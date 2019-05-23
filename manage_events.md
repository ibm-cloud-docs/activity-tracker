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

As an administrator of the {{site.data.keyword.at_full_notm}} service in the {{site.data.keyword.cloud_notm}}, you must provision an instance of the service in each location that you plan to monitor. You must define the account guidelines to manage events in the account, such as archiving guidelines.
{:shortdesc}


## Provision an instance of the service per location
{: #manage_events_provision}

You can provison 1 instance of the {{site.data.keyword.at_full_notm}} service per location. [Learn more](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-launch).

To get the list of locations where the service is available in the {{site.data.keyword.cloud_notm}}, see [Locations](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-regions).

As soon as an instance is available, events are collected and available for monitoring through the web UI of the service in that location.


## Export events
{: #manage_events_export}

You can export data in JSONL format from an {{site.data.keyword.at_full_notm}} instance into a local file. 

You can export logs programmatically by using the LogDNA REST API. [Learn more](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-export#export_api).
You can export logs through the web UI. [Learn more](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-export#export_ui).

Consider the following information when you export log data:
* You export a set of event entries. To define the set of data that you want to export, you can apply filter and searches. You can also specify the time range. 
* From the web UI, when you export events, you get an email that is sent to your email address, with a link to a compressed file that includes the data. To get the data, you must click the link and download the compressed file. The compressed file that contains the data that you want to export is available for a maximum of 48 hours. 
* When you export events programmatically, you can choose to send an email or to stream events in to your terminal.
* The maximum number of lines that you can export is 10,000.



## Archive events
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


## Classify events by using categories
{: #manage_events_category}

You can define categories through the **Categories** section in the web UI. 

You can define categories to group views. You can define a different set of categories to group dashboards.

Use categories to group resources so users can easily find them. 






