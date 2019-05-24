---

copyright:
  years: 2019
lastupdated: "2019-05-25"

keywords: IBM Cloud, LogDNA, Activity Tracker, manage events

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


# Managing events in your account
{: #manage_events}

As an administrator of the {{site.data.keyword.at_full_notm}} service in the {{site.data.keyword.cloud_notm}}, you must provision an instance of the service in each location that you plan to monitor. You must define the account guidelines to manage events in the account.
{:shortdesc}


## Provisioning an instance of the service per location
{: #manage_events_provision}

To collect and monitor activity in your account, you must provision the {site.data.keyword.at_full_notm}} service in your account. 

There is 1 instance of the {{site.data.keyword.at_full_notm}} service per location. Therefore, to monitor activity in your account, you might need to provision multiple {{site.data.keyword.at_full_notm}} instances. 

* In the {{site.data.keyword.cloud_notm}}, you can click the **Menu** icon ![Menu icon](../icons/icon_hamburger.svg) > **Observability** > **Activity Tracker** to see the dashboard where all the instances that are provisioned in the account are listed. 
* If you want to monitor [global events](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-monitor_events#mon_def_global), you must configure an instance in Frankfurt. 
{: tip}

[Learn more about provisioning the service](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-provision).

To get the list of locations where the service is available in the {{site.data.keyword.cloud_notm}}, see [Locations](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-regions).

As soon as an instance is available, events are collected and available for monitoring through the web UI of the service in that location.



## Archiving events
{: #manage_events_archive}

You can archive events from an {{site.data.keyword.at_full_notm}} instance into a bucket in an {{site.data.keyword.cos_full_notm}} (COS) instance. [Learn more](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-archiving).

* Events are automatically archived once a day in a compressed format **(.json.gz)**. Each line preserves its metadata.
* Events are archived within 24-48 hours after you save the configuration. 

Each {{site.data.keyword.at_full_notm}} instance has its own archiving configuration.
{: important}

The following figure shows a high-level view of the different components that are integrated when archiving events:

![High-level view archiving events](images/archive.png "High-level view archiving events")

The {{site.data.keyword.cos_full_notm}} instance is provisioned within the context of a resource group. The {{site.data.keyword.at_full_notm}} instance is also provisioned within the context of a resource group. Both instances can be grouped under the same resource group or in different ones. 

{{site.data.keyword.at_full_notm}} uses a service ID to communicate with the {{site.data.keyword.cos_full_notm}} service.
* The service ID that you create for an {{site.data.keyword.cos_full_notm}} instance is used by the {{site.data.keyword.at_full_notm}} to authenticate and access the {{site.data.keyword.cos_full_notm}} instance. 
* You can assign specific access policies to the service ID that restrict permissions on the {{site.data.keyword.cos_full_notm}} instance. Restrict the service ID to only have writing permissions on the bucket where you plan to archive the events.


## Classifying events by using categories
{: #manage_events_category}

You can define categories through the **Categories** section in the web UI. 

You can define categories to group views. You can define a different set of categories to group dashboards.

Use categories to group resources so users can easily find them. 






