---

copyright:
  years: 2019
lastupdated: "2019-05-25"

keywords: IBM Cloud, LogDNA, Activity Tracker, view events

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


# Monitoring events
{: #monitor_events}

After you provision an instance of the {{site.data.keyword.at_full_notm}} service in the {{site.data.keyword.cloud_notm}}, you can monitor events through the {{site.data.keyword.at_full_notm}} web UI.
{:shortdesc}

You can select the events that are displayed through a view by applying a timestamp, a search query, or both.

* You can apply a search query, and save it as a custom view. 
* You can apply a timestamp to jump to a specific time in your event log. 

You can only monitor events within your retention period. Different [service plans](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-service_plan) have different retention periods.
{: important}

When you apply a search query, you can save that view for reuse later. However, timestamps are not saved.
{: note}

## Monitoring events through the default view
{: #mon_def_view}

The default view is named **Everything**. As soon as you open the web UI, this is the view that you see.

[Learn more](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-view_events#view_events_step1).


## Monitoring events through custom views
{: #mon_cus_view}

You can create custom views to analyze data. 

To create a custom view, you must apply a search query that defines what events to display through the view. [Learn more](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-view_events#view_events_step2).

You can attach alerts to a custom view. [Learn more](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-alerts).

You can export data from a custom view. [Learn more](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-export).

You can rename, and add or modify the description of a view. [Learn more](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-views#views_step5).

You can apply a line template to a view to customize how the data is displayed. [Learn more](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-views#views_step4).

You can organize views by grouping them in **categories*.


## Monitoring events by applying a timeframe
{: #mon_time_view}

You can select the events that are displayed through a view by applying a timeframe.

You can apply a timestamp by specifying an absolute time, a relative time, or a time range.

* An abosute time specifies a precise point in time in your event log, such as `May 20 7:00pm`.
    
* A relative time specifies a timeframe that is not precise, such as `2 days ago`, `today at 12am`, or `an hour ago`.

* A time range specified an interval of time, such as `yesterday 10am to yesterday 11am`, `last fri 4:30pm to 11/12 1 AM`, `last wed 4:30pm to 23/05 1 AM`, or `May 20 10am to May 22 10am`. 

[Learn more](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-view_events#view_events_step3).


## Configuring alerts
{: #mon_alerts}

Through the {{site.data.keyword.at_full_notm}} web UI, you can apply search queries to define the events that are displayed through a custom view. Then, you can attach an alert to that view to be notified when a condition occurs. A bell icon is displayed with the view to indicate that this view has an alert attached to it.

* You can attach one alert per view. [Learn more](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-alerts#alerts_delete_view).
* You can configure conditions that are based on the number of event lines that meet the search query in the view, on a time frequency, or both.
* You can define multiple notification channels for an alert. For information about the supported channels, see [Alert notification channels](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-channels).
* You can define a **preset**. A preset is an alert template that you can attach to any number of views. You can use presets to define templates that users can reuse when they attach an alert to a view. [Learn more](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-alerts#alerts_step3).
* You can mute alerts. 
* You can detach an alert from a view. [Learn more](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-alerts#alerts_delete_view).

### Alert types
{: #mon_alerts_types}

You can configure the following types of alerts:

* **Presence alert**: You can use this type of alert to notify when the number of events that show in a view is more than what you expect. 
* **Absence alert**: You can use this type of alert to notify when the number of events that show in a view is less than what you expect, or none. 

For example, you might have a view that shows events that report the deletion of service instances in your account. You are not expecting the deletion of service instances. You can configure a *presence alert** that triggers an alert when 1 or more events show in the view.

The absence alert is enabled after an event is shown in the view.
{: note}


### Alert conditions
{: #mon_alerts_conditions}

You can configure any of the following conditions for an alert:

* **Time frequency**: You set this condition to specify how often to trigger an alert. Valid values are: 30 seconds, 1 minute, 5 minutes, 15 minutes, 30 minutes, 1 hour, 6 hours, 12 hours, 24 hours
* **Event lines counter**: You set this condition to specify the number of event lines that match the view's filtering and search criteria. When the number of event lines is reached, an alert is triggered.

You can decide whether both conditions are checked or only one. If both conditions are set, an alert is triggered when any of the thresholds is reached. 

If you set the *Event lines counter* to be the only condition that triggers an alert, notice that the time frequency that is set when you configure the condition determines the time that it takes for the alert condition to be reset after the alert is triggered.
{: note}

For example, you can configure an alert that is triggered after 30 seconds, or when a 100 event lines that match the view's filtering and search criteria are collected.












