---

copyright:
  years: 2019, 2023
lastupdated: "2022-08-16"

keywords:

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}


# Archiving events to {{site.data.keyword.cos_full_notm}}
{: #archiving-ov}

You can archive events from an {{site.data.keyword.at_full_notm}} instance into a bucket in an {{site.data.keyword.cos_full_notm}} (COS) instance.
{: shortdesc}



In {{site.data.keyword.at_short}}, by default archiving is not enabled. Data is available for search and analysis for the number of days that your service instance plan indicates. However, you might need to access the data longer for troubleshooting. You might also have to keep the data for longer for compliance, and for corporate or industry regulations. When you need access to data for longer than the number of search days, you must configure archiving.

You can only have 1 {{site.data.keyword.at_short}} instance per region. Each {{site.data.keyword.at_full_notm}} instance has its own archiving configuration.
{: important}

The following figure shows a high-level view of the different components that are involved when archiving events:

![High-level view archiving events](images/archive.png "High-level view archiving events"){: caption="Figure 1. High-level view archiving events" caption-side="bottom"}

The {{site.data.keyword.cos_full_notm}} instance is provisioned within the context of a resource group. The {{site.data.keyword.at_full_notm}} instance is also provisioned within the context of a resource group. Both instances can be grouped under the same resource group or in different ones.

{{site.data.keyword.at_full_notm}} uses a service ID to communicate with the {{site.data.keyword.cos_full_notm}} service.
* The service ID that you create for an {{site.data.keyword.cos_full_notm}} instance is used by {{site.data.keyword.at_full_notm}} to authenticate and access the {{site.data.keyword.cos_full_notm}} instance.
* You can assign specific access policies to the service ID that restrict permissions on the {{site.data.keyword.cos_full_notm}} instance. Restrict the service ID to only have writing permissions on the bucket where you plan to archive the events.
* You can also restrict the IP addresses that are allowed to manage the bucket.

You are responsible for configuring and managing the bucket and the data stored in it.
- If you configure archiving in an EU-managed location, you must configure a bucket that complies with the EU-managed and GDPR regulations.


After you configure archiving,consider the following information:
- Events are automatically archived in a compressed format **(.json.gz)**. Each event preserves its metadata.
- Events are archived within 24-48 hours after you save the configuration.
- Events are archived hourly.
- The first archive file is created when the archiving process runs and there is data.

You have a service plan of 30 days. You configured the instance 10 days ago. You enable archiving today. There will be no archive data for the first 10 days the instance was running.
{: note}

The archiving process generates multiple files. Each file includes events for the period of time indicated as part of its name. If there is no data, the archive file for that period is empty.



## Archived file format
{: #archiving-ov-format}

The archive directory format looks like this:

```text
year=<YYYY>/month=<MM>/day=<DD>/<accountID>.<YYYY>-<MM>-<DD>.<HHHH>.json.gz
```
{: codeblock}

Where

`YYYY` represents the year; `MM` represents the month; and `DD` represents the day.

`<accountID>` represents the auditing account ID, that is, the ID that is shown in the [web UI URL](/docs/activity-tracker?topic=activity-tracker-get_web_url).

`HHHH` represents hours in 24 format.

* The timestamp that is used to determine whether the event is included in an archive is the UTC timestamp.

Depending on your location, there might be events that you see in local time in your views on a specific day. However, you cannot find them in the archive file. You are most likely viewing events in local time and the archive process uses the UTC timestamp.
{: note}



## Configure archiving
{: ##archiving-ov-configure}

For information on how to configure archiving, see:
- [Configuring archiving through the UI](/docs/activity-tracker?topic=activity-tracker-archiving).
- [Configuring archiving by using the API](/docs/activity-tracker?topic=activity-tracker-archiving-manage-api#archivingapi-conf).

In addition, consider the following information:
- You must have the **manager** role to configure archiving in the {{site.data.keyword.at_full_notm}} instance. This role includes the **logdna.dashboard.manage** IAM action role that allows a user to perform admin tasks such as configure archiving.
- When you configure archiving, the {{site.data.keyword.at_short}} instance and the {{site.data.keyword.cos_full_notm}} (COS) instance must be provisioned in the same account.
- The credential that {{site.data.keyword.at_short}} uses to write data into a COS bucket must have **writer** role.



## Monitor archiving
{: #archiving-ov-monitor}

To monitor archiving, you can use the following services:

- {{site.data.keyword.mon_full_notm}} service:

    {{site.data.keyword.cos_full_notm}} is integrated with the {{site.data.keyword.mon_short}} service. {{site.data.keyword.mon_short}} provides a default template that you can customize to monitor the bucket that you configure to store data for long term.

    For more information, see [Monitoring archiving by using {{site.data.keyword.mon_full_notm}}](/docs/activity-tracker?topic=activity-tracker-archiving-monitor).

- {{site.data.keyword.at_full_notm}}:

    Archiving generates {{site.data.keyword.at_short}} events with the action **logdnaat.archiving.send** to notify of failures sending data to {{site.data.keyword.messagehub}}. There are different reasons for failure such as invalid credentials and topic deleted.

    For more information, see [Configuring an alert to monitor archiving](/docs/activity-tracker?topic=activity-tracker-archiving-at-monitor).




## Viewing archived events by using the SQL Query service
{: #archiving-ov-sqlquery}


{{site.data.keyword.sqlquery_short}} provides a serverless, no-ETL solution to easily query data stored in COS. [Learn more](/docs/sql-query?topic=sql-query-overview).

You can use this service to analyze data from archived files in COS.

Once you have SQL Query running on IBM Cloud, you can immediately start querying your data using the SQL Query user interface, programmatically by using either the REST API or the Python `ibmcloudsql` library, or write a serverless function by using {{site.data.keyword.openwhisk_short}}.

When you query events:
* You must provision an instance of the {{site.data.keyword.sqlquery_short}} service.
* You must restrict user access to work with that instance. Users need the platform **viewer** role to launch the UI, and the service **writer** role to run queries.
* When you open the UI, the {{site.data.keyword.sqlquery_short}} service automatically generates a unique COS bucket that will store all of the results as CSV files from your SQL queries. To make sure that you are using a custom bucket, create one. You can specify your custom bucket as the place to to store results.


## IAM permissions to configure archiving
{: #archiving-ov-iam}

To configure archiving, you need the following permissions:

### {{site.data.keyword.at_full_notm}} service
{: #archiving-ov-iam-at}

The following table lists the minimum roles that a user must have to be able to launch the {{site.data.keyword.at_full_notm}} web UI, and configure archiving through the UI or by using the API:

| Role                      | Permission granted            |
|---------------------------|-------------------------------|
| Platform role: `Viewer`     | Allows the user to view the list of service instances in the Observability dashboard. |
| Service role: `Manager`      | Allows the user to launch the web UI and configure archiving through the web UI or by using the API.  |
{: caption="Table 1. IAM roles" caption-side="top"}

For more information on how to configure policies for a user, see [Granting user permissions to a user or service ID](/docs/services/activity-tracker?topic=activity-tracker-iam_view_events#iam_view_events).


### {{site.data.keyword.cos_full_notm}} service
{: #archiving-ov-iam-cos}

The following table lists the roles that a user can have to complete the actions required to configure the {{site.data.keyword.cos_full_notm}} service:

| Service                    | Roles    | Action                                                                                        |
|----------------------------|-------------------|-----------------------------------------------------------------------------------------------|
| `Cloud Object Storage`     | Platform role: `Administrator`     | Allows the user to assign policies to users in the account to work with the {{site.data.keyword.cos_full_notm}} service. |
| `Cloud Object Storage`     |  Platform role: `Administrator`   \n  or \n Platform role:`Editor` | Allows the user to provision an instance of the {{site.data.keyword.cos_full_notm}} service.    |
| `Cloud Object Storage`     |  Platform role: `Administrator`   \n or \n  Platform role:`Editor` \n or   \n  Platform role: `Operator` | Allows the user to create a service ID.    |
| `Cloud Object Storage`     |  Service role: `writer` | Grants permissions to create, modify, and delete buckets. In addition, grants permissions to upload and download the objects in the bucket.   |
{: caption="Table 2. Roles and actions" caption-side="top"}

For more information on how to configure policies for a user, see [Grant IAM policies to a user to work with {{site.data.keyword.cos_full_notm}}D](/docs/activity-tracker?topic=activity-tracker-archiving#archiving_step1).

### Service ID
{: #archiving-ov-iam-cos-cred}

The service ID that you must create for an {{site.data.keyword.cos_full_notm}} instance is used by {{site.data.keyword.at_full_notm}} to authenticate and access the {{site.data.keyword.cos_full_notm}} instance. This service ID must have the **writer** role. This role grants permissions to upload archive files in the bucket.

When the service credential is rotated, make sure the [API Key is updated with the new API Key.](/docs/activity-tracker?topic=activity-tracker-archiving#archiving_step8)  Archiving will stop if the API Key is not updated.
{: important}

## {{site.data.keyword.at_short}} events
{: #archiving-ov-at-events}


The following {{site.data.keyword.at_short}} events are generated when you configure archiving:

| Action                                            | Description                |
|---------------------------------------------------|----------------------------|
| `logdnaat.account-archive-setting.configure` | This event is generated when an administrator configures archiving for an auditing instance. |
{: caption="Table 3. Archiving {{site.data.keyword.at_short}} events" caption-side="top"}
