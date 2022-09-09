---

copyright:
  years: 2019, 2022
lastupdated: "2021-08-09"

keywords: IBM Cloud, {{site.data.keyword.at_short}}, EU-supported

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}

# Managing events for an EU-supported account
{: #manage_eu_acc}

Across every industry, organizations require tighter controls and visibility into where their data is stored and processed in the {{site.data.keyword.cloud_notm}}. To manage events that are generated in your **EU-supported account** by using the {{site.data.keyword.atracker_full_notm}} service, consider the following information:
{: shortdesc}

* [You must enable your account to be EU-supported](/docs/services/activity-tracker?topic=activity-tracker-manage_eu_acc#manage_eu_acc_step1), so support is handled by team members in the European Union. 
* You must **configure resources to collect global events in an EU-supported location.** For {{site.data.keyword.at_full_notm}} hosted event search offerings, you must provision 1 {{site.data.keyword.at_full_notm}} instance in the `EU-DE (Frankfurt)` location. (You can only have 1 instance per region.) For {{site.data.keyword.atracker_full_notm}} , you must configure the route that is defined in an EU-supported location to collect global events.
* You must **restrict access to users** to manage and view events.
* You must ensure that you configure **an EU-Supported {{site.data.keyword.cos_full_notm}} (COS) bucket**. 
* To monitor activity from {{site.data.keyword.cloud_notm}} services and Cloud Foundry (CF) resources, you must provision these resources in an EU location such as Frankfurt.
    
    For services that generate global events such as the {{site.data.keyword.cos_full_notm}} (COS) service, when you provision this service, the instance is not bound to a specific location, but COS resources such as buckets are location-bound. As soon as you provision a COS instance, you get [global events](/docs/activity-tracker?topic=activity-tracker-event_types#event_types_global) automatically. You can also enable management and data events per bucket. For {{site.data.keyword.at_full_notm}} hosted event search offerings, when you enable all events to go to the Frankfurt instance, the global, management, and data events are hosted from the same {{site.data.keyword.at_full_notm}} instance in Frankfurt. For {{site.data.keyword.atracker_full_notm}} , you must configure a location in your account to collect global events. If you need to collect all types of events, you should configure the location where your bucket is provisioned. [Learn more about COS global events.](/docs/services/cloud-object-storage?topic=cloud-object-storage-at-events#at-actions-global).



## Step 1. Set on the EU-Supported flag in your account
{: #manage_eu_acc_step1}

You must enable your account to be `EU-supported` so that auditing instances in Frankfurt are supported by EU members. 

Consider the following information when you turn on the `EU-supported` flag in your account:
* Support is handled by team members in the European Union (EU). 
* In the event that your issue requires non-EU expert assistance, it will be reviewed and approval given prior to any non-EU intervention.
* You can filter and identify the {{site.data.keyword.cloud_notm}} Catalog services that are EU-supported. 


## Step 2. Configure resources to collect global events in an EU-supported location
{: #manage_eu_acc_step2}

For {{site.data.keyword.at_full_notm}} hosted event search offerings, you can provision 1 {{site.data.keyword.at_full_notm}} instance per [location](/docs/services/activity-tracker?topic=activity-tracker-regions). However, only the instance that is provisioned in the `EU-DE (Frankfurt)` location is EU-Supported when you set on the EU-supported flag in your account. For more information on how to provision an instance, see [Provisioning an instance](/docs/services/activity-tracker?topic=activity-tracker-provision).


For {{site.data.keyword.atracker_full_notm}} , you must configure the route that is defined in an EU-supported location to collect global events. For more information on how to create a route, see [Define a route](/docs/activity-tracker?topic=activity-tracker-getting-started-routing&interface=cli#getting-started-routing-setp5).


## Step 3. Working with global services in the {{site.data.keyword.cloud_notm}}
{: #manage_eu_acc_step3}

[Global events](/docs/activity-tracker?topic=activity-tracker-event_types#event_types_global) report on activity in your account that relate to data and resources that are generally synchronized across all regions. The common theme for global events is a single, synchronized location where account administrators can monitor certain types of activity across the Cloud. The services that users interact with are integrated into the core of the global {{site.data.keyword.cloud_notm}} experience. 
- For {{site.data.keyword.at_full_notm}} hosted event search offerings, the global domain is set for **Frankfurt**. Global events are captured and made available through the {{site.data.keyword.at_full_notm}} instance that is configured in Frankfurt.
- For {{site.data.keyword.atracker_full_notm}} , you must configure the route in the **Frankfurt** location to collect global events in that region.

For example, to monitor management events from actions on {{site.data.keyword.cos_full_notm}} (COS) buckets, you must create buckets in [(COS) EU-supported locations](/docs/services/cloud-object-storage?topic=cloud-object-storage-endpoints#endpoints-eu-managed).

## Step 4. Working with {{site.data.keyword.cloud_notm}} services and CF apps
{: #manage_eu_acc_step4}

To monitor activity from {{site.data.keyword.cloud_notm}} services and Cloud Foundry (CF) resources, you must provision these resources in the **Frankfurt** EU-supported location in the {{site.data.keyword.cloud_notm}}. Check that the services support EU-supported locations. Notice that most services generate location-based events so the region where they are provisioned define where the auditing events are generated.

Check the list of {{site.data.keyword.cloud_notm}} resources that automatically collect events and forward them to the {{site.data.keyword.atracker_full_notm}} service. See [Cloud services](/docs/services/activity-tracker?topic=activity-tracker-cloud_services) and [Cloud services locations](/docs/activity-tracker?topic=activity-tracker-cloud_services_locations&interface=cli).



## Step 5. Restrict user access to view and manage events
{: #manage_eu_acc_step5}

{{site.data.keyword.iamlong}} (IAM) enables you to securely authenticate users and control access to all cloud resources consistently in the {{site.data.keyword.cloud_notm}}.

**Every user that accesses the {{site.data.keyword.at_full_notm}} service in your account must be assigned an access policy with an IAM user role defined.** The policy determines what actions the user can perform within the context of the service or instance you select. The allowable actions are customized and defined as operations that are allowed to be performed on the service. The actions are then mapped to IAM user roles. [Learn more about the IAM user roles for the {{site.data.keyword.at_full_notm}}](/docs/services/activity-tracker?topic=activity-tracker-iam#service).

You might have users across different geographies. However, to comply with EU law, only EU personnel can see and access log data from your EU-supported infrastructure, apps, and services. To restrict access to users, you can configure an access group, and define policies that restrict access to those users to the Frankfurt instance only.

For more information, see [Managing access with IAM](/docs/activity-tracker?topic=activity-tracker-iam).


## Step 6. Exporting logs
{: #manage_eu_acc_step6}

This information applies only if you use an {{site.data.keyword.at_full}} [hosted event search offering](/docs/activity-tracker?topic=activity-tracker-service_plan).
{: important}

In an {{site.data.keyword.at_full_notm}} instance, you can configure and control whether users can export data. [Learn more](/docs/activity-tracker?topic=activity-tracker-export_config).

Users can export data through the UI or by using the *Export* API:

* Users can export data to a local file or to a terminal by using the export API and a service key. [Learn more](/docs/activity-tracker?topic=activity-tracker-export_api).

    * Users with **manager** permissions to administer the Frankfurt {{site.data.keyword.at_short}} instance can create and view service keys. 

    * Users with **manager** or **Standard-Member** permissions to work with the Frankfurt {{site.data.keyword.at_short}} instance can view active service keys, and therefore, can export data locally.

    * Users with **user** permissions to work with the Frankfurt {{site.data.keyword.at_short}} instance cannot see service keys. Therefore, these users cannot use the export API to download data.

    * Service keys are only used to export data from an auditing instance by using the Export API. 
        

* Users can request the export of data through the UI. [Learn more](/docs/activity-tracker?topic=activity-tracker-export).


## Step 7. Archiving logs
{: #manage_eu_acc_step7}

This information applies only if you use an {{site.data.keyword.at_full}} [hosted event search offering](/docs/activity-tracker?topic=activity-tracker-service_plan).
{: important}

When you archive logs from the Frankfurt auditing instance to a {{site.data.keyword.cos_full_notm}} (COS) bucket, consider the following information:
* When you provision an instance of the COS service, this instance is a global one in your account. It is not region-bound.
* You must configure a bucket that complies with the EU-supported and GDPR regulations. For the list of COS EU-supported endpoints, see [EU-supported endpoints](/docs/services/cloud-object-storage?topic=cloud-object-storage-endpoints#endpoints-eu-managed).

    For example, consider the following scenarios:

    * For a bucket with **single site** resiliency, you can create the bucket in Amsterdam or Milan.

    * For a bucket with **regional** resiliency, you can create the bucket in the `EU-DE` location to keep the data in Frankfurt.

    * For a bucket with **cross region** resiliency, you can create the bucket in the `eu-geo` location. Data is kept within the EU geography across datacenters that are located in Milan, Amsterdam, and Frankfurt.

* You must restrict user access to manage archived log files in these buckets.  
* Users are responsible for downloading files to EU-supported locations.

To learn how to configure archiving for your auditing instance, see [Archiving logs](/docs/services/activity-tracker?topic=activity-tracker-archiving).



## Step 8. Querying archived events with SQL Query service
{: #manage_eu_acc_step8}

This information applies only if you use an {{site.data.keyword.at_full}} [hosted event search offering](/docs/activity-tracker?topic=activity-tracker-service_plan).
{: important}

{{site.data.keyword.sqlquery_short}} provides a serverless, no-ETL solution to easily query data stored in COS. [Learn more](/docs/services/sql-query?topic=sql-query-overview).

You can use this service to analyze data from archived files in COS. 

Once you have SQL Query running on IBM Cloud, you can immediately start querying your data using the SQL Query user interface, programmatically by using either the REST API or the Python `ibmcloudsql` library, or write a serverless function by using {{site.data.keyword.openwhisk_short}}.

When you query events, consider the following information:
* You must provision an instance of the {{site.data.keyword.sqlquery_short}} service in Frankfurt.
* You must restrict user access to work with that instance. Users need the platform **viewer** role to launch the UI, and the service **writer** role to run queries.
* When you open the UI, the {{site.data.keyword.sqlquery_short}} service automatically generates a unique COS bucket that will store all of the results as CSV files from your SQL queries. To make sure that you are using an EU-supported bucket, create one. You can specify your custom bucket to store results. 




