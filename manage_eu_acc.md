---

copyright:
  years:  2018, 2019
lastupdated: "2019-08-05"

keywords: IBM Cloud, LogDNA, Activity Tracker, EU managed

subcollection: logdnaat

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

# Managing events for an EU-managed account
{: #manage_eu_acc}

Across every industry, organizations require tighter controls and visibility into where their data is stored and processed in the {{site.data.keyword.cloud_notm}}. If you are looking for guidance on how to monitor activity in an EU-managed account, check out this topic. 
{:shortdesc}

To manage events that are generated in your **EU-managed account** by using the {{site.data.keyword.at_full_notm}} service, consider the following information:
* You must provision 1 {{site.data.keyword.at_full_notm}} instance in the `EU-DE (Frankfurt)` location.
* Your account must be EU Supported enabled, so support is handled by team members in the European Union. 
* To monitor activity from {{site.data.keyword.cloud_notm}} services and Cloud Foundry (CF) resources, you must provision these resources in an EU managed location in the {{site.data.keyword.cloud_notm}}.
* Global actions on {{site.data.keyword.cos_full_notm}} (COS) resources in your account are automatically collected and forwarded to the Activity Tracker instance in Frankfurt.
* To monitor management events from actions on {{site.data.keyword.cos_full_notm}} (COS) buckets, you must create buckets in [(COS) EU managed locations](/docs/services/cloud-object-storage?topic=cloud-object-storage-endpoints#endpoints-eu-managed) and you must configure the bucket to forward events to the Activity Tracker instance in Frankfurt. If you also want to monitor data events, you must configure the bucket to enable data events.
* You must **restrict access to users** to see and manage events in the Activity Tracker instance provisioned in Frankfurt.  
* You must ensure that you **archive to an EU-Supported {{site.data.keyword.cos_full_notm}} (COS) bucket**. 



## Step 1. Set on the EU-Supported flag in your account
{: #manage_eu_acc_step1}

You must enable your account to be `EU-Supported` so that logging instances in Frankfurt are supported by EU members. 

Consider the following information when you turn on the `EU Supported` flag in your account:
* Support is handled by team members in the European Union (EU). 
* In the event that your issue requires non-EU expert assistance, it will be reviewed and approval given prior to any non-EU intervention.
* You can filter and identify the {{site.data.keyword.cloud_notm}} Catalog services that are EU-Supported. 


## Step 2. Provision the {{site.data.keyword.at_full_notm}} instance in Frankfurt 
{: #manage_eu_acc_step2}

You can provision 1 {{site.data.keyword.at_full_notm}} instance per [location](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-regions). However, only the instance that is provisioned in the `EU-DE (Frankfurt` location is EU-Supported when you set on the EU-Supported flag in your account.
{: important}

For more information on how to provision an instance, see [Provisioning an instance](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-provision).


## Step 3. Working with {{site.data.keyword.cloud_notm}} services and CF apps
{: #manage_eu_acc_step3}

To monitor activity from {{site.data.keyword.cloud_notm}} services and Cloud Foundry (CF) resources, you must provision these resources in an EU managed location in the {{site.data.keyword.cloud_notm}}.

Check out the list of {{site.data.keyword.cloud_notm}} resources that automatically collect events and forward them to the {{site.data.keyword.at_full_notm}} service. See [Cloud services](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-cloud_services).



## Step 4. Working with global services in the {{site.data.keyword.cloud_notm}}
{: #manage_eu_acc_step4}

Global events report on activity in your account that relate to data and resources that are generally synchronized across all regions. The common theme for global events is a single, synchronized location where account administrators can monitor certain types of activity across the Cloud. The services that users interact with are integrated into the core of the global {{site.data.keyword.cloud_notm}} experience. The global domain is set in **Frankfurt**. Global events are captured and made available through the {{site.data.keyword.at_full_notm}} instance that is configured in Frankfurt.

 


### {{site.data.keyword.cos_full_notm}} (COS)
{: #cos}


{{site.data.keyword.cos_full_notm}} (COS) is a global service. Global actions on COS resources in your account are automatically collected and forwarded to the Activity Tracker instance in Frankfurt.

COS can also generate management and data events. These events are optional.
* To monitor management events from actions on buckets, you must create buckets in [(COS) EU managed locations](/docs/services/cloud-object-storage?topic=cloud-object-storage-endpoints#endpoints-eu-managed) and you must configure the bucket to forward events to the Activity Tracker instance in Frankfurt. 
* If you also want to monitor data events, you must configure the bucket to enable data events.

In summary, you must configure each bucket to enable collection and forwarding of bucket events to an Activity Tracker instance. Therefore, to keep all events in an EU managed location, you must configure your buckets to collect and forward events to the ACtivity Tracker instance in the Frankfurt location.

Notice that to create a bucket, you need to have *editor* or *Manager* service role for the COS instance.



## Step 5. Restrict user access to view and manage events
{: #manage_eu_acc_step5}

{{site.data.keyword.iamlong}} (IAM) enables you to securely authenticate users and control access to all cloud resources consistently in the {{site.data.keyword.cloud_notm}}.

**Every user that accesses the {{site.data.keyword.at_full_notm}} service in your account must be assigned an access policy with an IAM user role defined.** The policy determines what actions the user can perform within the context of the service or instance you select. The allowable actions are customized and defined as operations that are allowed to be performed on the service. The actions are then mapped to IAM user roles. [Learn more about the IAM user roles for the {{site.data.keyword.at_full_notm}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-iam#service).

You might have users across different geographies. However, to comply with EU law, only EU personel can see and access log data from your EU-managed infrastructure, apps, and services. To restrict access to users, you can configure an access group, and define policies that restrict access to those users to the Frankfurt instance only.

### Grant permissions to users to manage the instance
{: #manage_eu_acc_step5-1}

To grant administrator permissions to users, complete the following steps:
1. Create an access group, then add users to it. For example, create an access group named `logdnaat-eu-admins`. [Learn more](/docs/iam?topic=iam-groups#create_ag).
2. [Assign administrator access to a group](/docs/iam?topic=iam-groups#access_ag) by configuring policies.

    For example, add a policy where you select the Activity Tracker instance in Frankfurt only. Select the platform role **administrator**. If you want to remove permissions to manage users, choose the platform role **editor**. Select the service role **manager**. [Learn more](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-iam_manage_events).


### Grant permissions to users to view events
{: #manage_eu_acc_step5-2}

To grant viewer permissions to users, complete the following steps:
1. Create an access group, then add users to it. For example, create an access group named `logdna-eu-users`. [Learn more](/docs/iam?topic=iam-groups#create_ag).
2. [Assign access to a group](/docs/iam?topic=iam-groups#access_ag) by configuring policies.

    For example, add a policy where you select the Activity Tracker instance in Frankfurt only. Select the platform role **viewer** to grant users permissions to view events. Select the service role **reader**. [Learn more](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-iam_view_events).


## Step 6. Exporting logs
{: #manage_eu_acc_step6}

To make the EU-DE (Frankfurt) location `EU-Supported`, the web UI export functionality is not available for the Activity Tracker instance that is provisioned in Frankfurt. In addition, you cannot use the API to export data to an email address. 

Users can export data to a local file or to a terminal by using the LogDNA export API and a service key. Only administrators can create and view service keys. Service keys are only used to export data from a LogDNA instance by using the Export API. [Learn more](/docs/services/Log-Analysis-with-LogDNA?topic=LogDNA-export#api).

Notice that users in the account that have permissions to view events through the LogDNA web UI can export data by using the API if they have an active service key. 


## Step 7. Archiving logs
{: #manage_eu_acc_step7}

When you archive logs from the Frankfurt LogDNA instance to a {{site.data.keyword.cos_full_notm}} (COS) bucket, consider the following information:
* When you provision an instance of the COS service, this instance is a global one in your account. It is not region bound.
* You must configure a bucket that complies with the EU-Supported and GDPR regulations. For the list of COS EU managed endpoints, see [EU managed endpoints](/docs/services/cloud-object-storage?topic=cloud-object-storage-endpoints#endpoints-eu-managed).

    For example, consider the following scenarios:

    * For a bucket with **single site** resiliency, you can create the bucket in Amsterdam or Milan.

    * For a bucket with **regional** resiliency, you can create the bucket in the `EU-DE` location to keep the data in Frankfurt.

    * For a bucket with **cross region** resiliency, you can create the bucket in the `eu-geo` location. Data is kept within the EU geography across datacenters that are located in Milan, Amsterdam, and Frankfurt.

* You must restrict user access to manage archived log files in these buckets.  
* Users are responsible for downloading files to EU-managed locations.

To learn how to configure archiving for your LogDNA instance, see [Archiving logs](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-archiving).



## Step 8. Querying archived logs with SQL Query service
{: #manage_eu_acc_step8}


{{site.data.keyword.sqlquery_short}} provides a serverless, no-ETL solution to easily query data stored in COS. [Learn more](/docs/services/sql-query?topic=sql-query-overview).

You can use this service to analyze data from archived files in COS. 

Once you have SQL Query running on IBM Cloud, you can immediately start querying your data using the SQL Query user interface, programmatically by using either the REST API or the Python `ibmcloudsql` library, or write a serverless function by using {{site.data.keyword.openwhisk_short}}.

When you query events, consider the following information:
* You must provision an instance of the {{site.data.keyword.sqlquery_short}} service in Frankfurt.
* You must restrict user access to work with that instance. Users need the platform **viewer** role to launch the UI, and the service **writer** role to run queries.
* When you open the UI, the {{site.data.keyword.sqlquery_short}} service automatically generates a unique COS bucket that will store all of the results as CSV files from your SQL queries. To make sure that you are using an EU-Supported bucket, create one. You can specify your custom bucket to store results in. 




