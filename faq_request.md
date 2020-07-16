---

copyright:
  years: 2019, 2020
lastupdated: "2020-07-16"

keywords: IBM Cloud, LogDNA, Activity Tracker, troubleshooting

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
{:external: target="_blank" .external}


# What can I do when my request fails to complete successfully due to a network transmission interruption?
{: #faq_request}

When LogDNA operations are affected by a network transmission interruption in {{site.data.keyword.cloud_notm}}, you may experience a delay viewing your data or processing a request. 
{:shortdesc}

## What triggers a network transmission interruption?
{: #faq_request_1}

LogDNA operations might be affected by a network transmission interruption in {{site.data.keyword.cloud_notm}}. This interruption might be caused by a spike of activity in the service, or by authentication (IAM) issues. LogDNA might also be affected by other interruptions that are transient in nature.

## What happens when there is a network transmission interruption?
{: #faq_request_2}

When an interruption happens, there are specific requests where LogDNA notifies via email of the status of the request. For other requests, you can configure alerts on custom views, for example to detect when data is delayed showing in your views due to a spike processing data in the service. 


## How can I get more information of the network transmission interruption?
{: #faq_request_3}

Check the status of the {{site.data.keyword.at_full}} service in the [support page](https://cloud.ibm.com/status?selected=status){: external}.

You can also use {{site.data.keyword.mon_full_notm}} to monitor the status of enabled-Sysdig services in {{site.data.keyword.cloud_notm}}. The monitoring service offers additonal information that can help troubleshoot network transmission interruption problems.

    * If you are interested in [{{site.data.keyword.messagehub}}](/docs/EventStreams?topic=EventStreams-getting_started), you can monitor your {{site.data.keyword.messagehub}} instance and analyze authentication failures or bandwidth problems. For example, when you exceed `17.7 MB per min` or `25GB per day` extracting data, LogDNA reports a network transmission interruption. 



## What can I do if I am notified or detect a network transmission interruption when extracting data from my LogDNA instance?
{: #faq_request_4}

Complete one or more of the following tasks to identify and manage data that was affected by the network transmission interruption:

For any task that you choose, apply a time range to indicate the timeframe when the service was interrupted.
{: important}

1. View data through the LogDNA web UI. [Learn more](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-view_events).

2. Export data through the LogDNA web UI. [Learn more](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-export).

3. Export data programmatically by using the **Export API**. [Learn more](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-export_api). 

4. If you enable archiving for the LogDNA instance that is affected by the network transmission interruption, query data that is archived in {{site.data.keyword.cos_full_notm}} (COS) by using the {{site.data.keyword.sqlquery_short}} service. [Learn more](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-sqlquery).









