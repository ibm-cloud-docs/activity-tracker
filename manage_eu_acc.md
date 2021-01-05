---

copyright:
  years: 2019, 2021
lastupdated: "2021-01-05"

keywords: IBM Cloud, LogDNA, {{site.data.keyword.at_short}}, EU-supported

subcollection: Activity-Tracker-with-LogDNA

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}
{:important: .important}
{:note: .note}

# Managing events for an EU-supported account
{: #manage_eu_acc}

Across every industry, organizations require tighter controls and visibility into where their data is stored and processed in the {{site.data.keyword.cloud_notm}}. To manage events that are generated in your **EU-supported account** by using the {{site.data.keyword.at_full_notm}} service, consider the following information:
{:shortdesc}

* You must provision 1 {{site.data.keyword.at_full_notm}} instance in the `EU-DE (Frankfurt)` location. (You can only have 1 instance per region.)
* [You must enable your account to be EU-supported](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-manage_eu_acc#manage_eu_acc_step1), so support is handled by team members in the European Union. 
* To monitor activity from {{site.data.keyword.cloud_notm}} services and Cloud Foundry (CF) resources, you must provision these resources in the Frankfurt location.
    
    The {{site.data.keyword.cos_full_notm}} (COS) service is a global service. When you provision this service, the instance is not bound to a specific location, but COS resources such as buckets are location-bound. As soon as you provision a COS instance, you get [global events](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-event_types#event_types_global) automatically through the Frankfurt {{site.data.keyword.at_full_notm}} instance. You can also enable management and data events on a bucket to go to the Frankfurt {{site.data.keyword.at_full_notm}} instance. **When you enable all events to go to the Frankfurt instance, the global, management, and data events are hosted from the same {{site.data.keyword.at_full_notm}} instance in Frankfurt.**

* You must **restrict access to users** to see and manage events in the {{site.data.keyword.at_short}} instance provisioned in Frankfurt.  
* You must ensure that you **archive to an EU-Supported {{site.data.keyword.cos_full_notm}} (COS) bucket**. 



## Step 1. Set on the EU-Supported flag in your account
{: #manage_eu_acc_step1}

You must enable your account to be `EU-supported` so that logging instances in Frankfurt are supported by EU members. 

Consider the following information when you turn on the `EU-supported` flag in your account:
* Support is handled by team members in the European Union (EU). 
* In the event that your issue requires non-EU expert assistance, it will be reviewed and approval given prior to any non-EU intervention.
* You can filter and identify the {{site.data.keyword.cloud_notm}} Catalog services that are EU-supported. 


## Step 2. Provision the {{site.data.keyword.at_full_notm}} instance in Frankfurt 
{: #manage_eu_acc_step2}

You can provision 1 {{site.data.keyword.at_full_notm}} instance per [location](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-regions). However, only the instance that is provisioned in the `EU-DE (Frankfurt)` location is EU-Supported when you set on the EU-supported flag in your account.
{: important}

For more information on how to provision an instance, see [Provisioning an instance](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-provision).



## Step 3. Working with global services in the {{site.data.keyword.cloud_notm}}
{: #manage_eu_acc_step3}

[Global events](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-event_types#event_types_global) report on activity in your account that relate to data and resources that are generally synchronized across all regions. The common theme for global events is a single, synchronized location where account administrators can monitor certain types of activity across the Cloud. The services that users interact with are integrated into the core of the global {{site.data.keyword.cloud_notm}} experience. The global domain is set for **Frankfurt**. Global events are captured and made available through the {{site.data.keyword.at_full_notm}} instance that is configured in Frankfurt.



### {{site.data.keyword.cos_full_notm}} (COS)
{: #step3-cos}

{{site.data.keyword.cos_full_notm}} (COS) is a global service. Global actions on COS resources such as create a bucket in your account are automatically collected and forwarded to the {{site.data.keyword.at_short}} instance in Frankfurt. [Learn more about COS global events.](/docs/services/cloud-object-storage?topic=cloud-object-storage-at-events#at-actions-global)

COS can also generate management and data events. These events are optional. To learn more about these type of events, go to step 4.




## Step 4. Working with {{site.data.keyword.cloud_notm}} services and CF apps
{: #manage_eu_acc_step4}

To monitor activity from {{site.data.keyword.cloud_notm}} services and Cloud Foundry (CF) resources, you must provision these resources in the **Frankfurt** EU-supported location in the {{site.data.keyword.cloud_notm}}.

Check the list of {{site.data.keyword.cloud_notm}} resources that automatically collect events and forward them to the {{site.data.keyword.at_full_notm}} service. See [Cloud services](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-cloud_services).



### {{site.data.keyword.cos_full_notm}} (COS)
{: #step4-cos}


COS can also generate [management](/docs/services/cloud-object-storage?topic=cloud-object-storage-at-events#at-actions-mngt) and [data](/docs/services/cloud-object-storage?topic=cloud-object-storage-at-events#at-actions-data) events. These events are optional and location-based.

To monitor management events from actions on {{site.data.keyword.cos_full_notm}} (COS) buckets, you must create buckets in [(COS) EU-supported locations](/docs/services/cloud-object-storage?topic=cloud-object-storage-endpoints#endpoints-eu-managed) and you must configure the bucket to forward events to the {{site.data.keyword.at_short}} instance in Frankfurt. If you also want to monitor data events, you must configure the bucket to enable data events.


In summary, you must configure each bucket to enable collection and forwarding of bucket events to an {{site.data.keyword.at_short}} instance. Therefore, to keep all events in an EU-supported location, you must configure your buckets to collect and forward events to the {{site.data.keyword.at_short}} instance in the Frankfurt location.





## Step 5. Restrict user access to view and manage events
{: #manage_eu_acc_step5}

{{site.data.keyword.iamlong}} (IAM) enables you to securely authenticate users and control access to all cloud resources consistently in the {{site.data.keyword.cloud_notm}}.

**Every user that accesses the {{site.data.keyword.at_full_notm}} service in your account must be assigned an access policy with an IAM user role defined.** The policy determines what actions the user can perform within the context of the service or instance you select. The allowable actions are customized and defined as operations that are allowed to be performed on the service. The actions are then mapped to IAM user roles. [Learn more about the IAM user roles for the {{site.data.keyword.at_full_notm}}](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-iam#service).

You might have users across different geographies. However, to comply with EU law, only EU personnel can see and access log data from your EU-supported infrastructure, apps, and services. To restrict access to users, you can configure an access group, and define policies that restrict access to those users to the Frankfurt instance only.

### Grant permissions to users to manage the instance
{: #manage_eu_acc_step5-1}

To grant administrator permissions to users, complete the following steps:
1. Create an access group, then add users to it. For example, create an access group named `logdna-at-eu-sec-admins`. [Learn more](/docs/account?topic=account-groups#create_ag).
2. [Assign administrator access to a group](/docs/account?topic=account-groups#access_ag) by configuring policies.

    For example, add a policy where you select the {{site.data.keyword.at_short}} instance in Frankfurt only. Select the platform role **administrator**, or if you want to remove permissions to manage users, choose the platform role **editor**. Select the service role **manager**. [Learn more](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-iam_manage_events).


### Grant permissions to users to view events
{: #manage_eu_acc_step5-2}

To grant viewer permissions to users, complete the following steps:
1. Create an access group, then add users to it. For example, create an access group named `logdna-at-eu-users`. [Learn more](/docs/account?topic=account-groups#create_ag).
2. [Assign access to a group](/docs/account?topic=account-groups#access_ag) by configuring policies.

    For example, add a policy where you select the {{site.data.keyword.at_short}} instance in Frankfurt only. Select the platform role **viewer** to grant users permissions to view events. Select the service role **reader**. [Learn more](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-iam_view_events).


## Step 6. Exporting logs
{: #manage_eu_acc_step6}

In an {{site.data.keyword.at_full_notm}} instance, you can configure and control whether users can export data. [Learn more](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-export_config).

Users can export data through the LogDNA web UI or by using the *Export* LogDNA API:

* Users can export data to a local file or to a terminal by using the LogDNA export API and a service key. [Learn more](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-export_api).

    * Users with **manager** permissions to administer the Frankfurt {{site.data.keyword.at_short}} instance can create and view service keys. 

    * Users with **manager** or **Standard-Member** permissions to work with the Frankfurt {{site.data.keyword.at_short}} instance can view active service keys, and therefore, can export data locally.

    * Users with **user** permissions to work with the Frankfurt {{site.data.keyword.at_short}} instance cannot see service keys. Therefore, these users cannot use the export API to download data.

    * Service keys are only used to export data from a LogDNA instance by using the Export API. 
        

* Users can request the export of data through the LogDNA web UI. [Learn more](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-export).


## Step 7. Archiving logs
{: #manage_eu_acc_step7}

When you archive logs from the Frankfurt LogDNA instance to a {{site.data.keyword.cos_full_notm}} (COS) bucket, consider the following information:
* When you provision an instance of the COS service, this instance is a global one in your account. It is not region-bound.
* You must configure a bucket that complies with the EU-supported and GDPR regulations. For the list of COS EU-supported endpoints, see [EU-supported endpoints](/docs/services/cloud-object-storage?topic=cloud-object-storage-endpoints#endpoints-eu-managed).

    For example, consider the following scenarios:

    * For a bucket with **single site** resiliency, you can create the bucket in Amsterdam or Milan.

    * For a bucket with **regional** resiliency, you can create the bucket in the `EU-DE` location to keep the data in Frankfurt.

    * For a bucket with **cross region** resiliency, you can create the bucket in the `eu-geo` location. Data is kept within the EU geography across datacenters that are located in Milan, Amsterdam, and Frankfurt.

* You must restrict user access to manage archived log files in these buckets.  
* Users are responsible for downloading files to EU-supported locations.

To learn how to configure archiving for your LogDNA instance, see [Archiving logs](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-archiving).



## Step 8. Querying archived events with SQL Query service
{: #manage_eu_acc_step8}


{{site.data.keyword.sqlquery_short}} provides a serverless, no-ETL solution to easily query data stored in COS. [Learn more](/docs/services/sql-query?topic=sql-query-overview).

You can use this service to analyze data from archived files in COS. 

Once you have SQL Query running on IBM Cloud, you can immediately start querying your data using the SQL Query user interface, programmatically by using either the REST API or the Python `ibmcloudsql` library, or write a serverless function by using {{site.data.keyword.openwhisk_short}}.

When you query events, consider the following information:
* You must provision an instance of the {{site.data.keyword.sqlquery_short}} service in Frankfurt.
* You must restrict user access to work with that instance. Users need the platform **viewer** role to launch the UI, and the service **writer** role to run queries.
* When you open the UI, the {{site.data.keyword.sqlquery_short}} service automatically generates a unique COS bucket that will store all of the results as CSV files from your SQL queries. To make sure that you are using an EU-supported bucket, create one. You can specify your custom bucket to store results. 




