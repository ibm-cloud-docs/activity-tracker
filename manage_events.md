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

You can provison 1 instance of the {{site.data.keyword.at_full_notm}} service per location. To get the list of locations where the service is available in the {{site.data.keyword.cloud_notm}}, see [Locations](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-regions).


## Export events
{: #manage_events_export}

You can export data in JSONL format from an {{site.data.keyword.at_full_notm}} instance into a local file. You can export logs programmatically by using the LogDNA REST API.

Consider the following information when you export log data:
* You export a set of event entries. To define the set of data that you want to export, you can apply filter and searches. You can also specify the time range. 
* From the web UI, when you export events, you get an email that is sent to your email address, with a link to a compressed file that includes the data. To get the data, you must click the link and download the compressed file.
* When you export events programmatically, you can choose to send an email or to stream events in to your terminal.
* The compressed file that contains the data that you want to export is available for a maximum of 48 hours. 
* The maximum number of lines that you can export is 10,000.





## Hide events from views
{: #manage_events_hide}



## Archive events
{: #manage_events_archive}



## Classify events by using categories
{: #manage_events_category}








