---

copyright:
  years: 2019, 2024
lastupdated: "2024-03-27"

keywords:

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}


# Monitoring activity through the UI
{: #monitor_events}


You can monitor activity in your account through the {{site.data.keyword.at_full_notm}} web UI by using views, dashboards, and screens. You can also export sets of events to analyze them in a different context. You can be notified if specific events are generated in your account.
{: shortdesc}

<!-- Common deprecation statement -->
{{../log-analysis/_include-segments/deprecation_notice.md}}


There is 1 instance of the {{site.data.keyword.at_full_notm}} service per location. Therefore, to monitor activity in your account, you might need to view and analyze events through different {{site.data.keyword.at_full_notm}} instances.

In the {{site.data.keyword.cloud_notm}}, you can click the **Menu** icon ![Menu icon](../icons/icon_hamburger.svg) &gt; **Observability** &gt; **Activity Tracker** to see the dashboard where all the instances that are provisioned in the account are listed.
{: tip}

To view events, [launch the web UI](/docs/activity-tracker?topic=activity-tracker-launch) in the location where events are available. Then, you can work with views to monitor those events. You view events in your local time.

You can select the events that are displayed through a view by applying a timestamp, a search query, or both.

* You can apply a search query, and save it as a custom view.
* You can apply a timestamp to jump to a specific time in your event log.

When you apply a search query, you can save that view for reuse later. However, timestamps are not saved.

Instances might have different service plans, and consequently different data retention periods that determine the number of days that you have data available for search though the web UI. You can only monitor events within your retention period. Different [service plans](/docs/activity-tracker?topic=activity-tracker-service_plan) have different retention periods.


## Monitoring global and location-based events
{: #mon_def_event_type}

Events can be classified as global or location-based. The type of event determines where you monitor events. [Learn more](/docs/activity-tracker?topic=activity-tracker-event_types).

Global events are captured and made available through the {{site.data.keyword.at_full_notm}} instance that is configured in Frankfurt (eu-de).

Location-based events are captured and made available through the {{site.data.keyword.at_full_notm}} instance that is configured in the same location where the service is available.


## Monitoring events through the default view
{: #mon_def_view}

The default view is named **EVERYTHING**.

As soon as you open the web UI in a location, this is the view that you see.

All events in your instance are displayed through this view.

To learn how to view events through this view, see [Viewing events](/docs/activity-tracker?topic=activity-tracker-view_events#view_events_step1).

## Monitoring events through custom views
{: #mon_cus_view}

You might want to monitor a set of events in your account. To anayze a subset of events, you can create custom views.

You create a custom view by applying a search query that defines what events to display through the view. [Learn more](/docs/activity-tracker?topic=activity-tracker-view_events#view_events_step2).

You can also do any of the following tasks:

* [Attach an alert](/docs/activity-tracker?topic=activity-tracker-alerts) to a custom view.
* [Export data](/docs/activity-tracker?topic=activity-tracker-export) from a custom view.
* [Rename, and add or modify the description of a view.](/docs/activity-tracker?topic=activity-tracker-views#views_step5)
* [Apply a line template](/docs/activity-tracker?topic=activity-tracker-views#views_step4) to a view to customize how the data is displayed.
* Organize views by grouping them into **categories**.


## Monitoring events by applying a timeframe
{: #mon_time_view}

You might want to see events within a specific timeframe.

You can select the events that are displayed through a view by [applying a timeframe](/docs/activity-tracker?topic=activity-tracker-view_events#view_events_step3).

You can apply a timestamp by specifying an absolute time, a relative time, or a time range.

* An abosute time specifies a precise point in time in your event log, such as `May 20 7:00pm`.

* A relative time specifies a timeframe that is not precise, such as `2 days ago`.

* A time range specified an interval of time, such as `yesterday 10am to yesterday 11am`.



## Configuring alerts
{: #mon_alerts}

There are scenarios where you might want to be notified if specific events are generated in your account. For example, you might want to be notified if the number of actions that fail goes over a specified threshold.

Through the {{site.data.keyword.at_full_notm}} web UI, you can apply search queries to define the events that are displayed through a custom view. Then, you can attach an alert to that view to be notified when a condition occurs. A bell icon is displayed with the view to indicate that this view has an alert attached to it.

When you configure alerts:

* You can [attach one alert](/docs/activity-tracker?topic=activity-tracker-alerts) per custom view. There are 2 types of alerts: presence alert and absence alert.

* You can configure conditions that are based on the number of event lines that meet the search query in the view, on a time frequency, or both. The time frequency that is specified as part of the condition defines the reset time of an alert after it is triggered.

* You can define multiple notification channels for an alert. For information about the supported channels, see [Alert notification channels](/docs/activity-tracker?topic=activity-tracker-channels).

* You can [define **presets**](/docs/activity-tracker?topic=activity-tracker-alerts#alerts_step3). A preset is an alert template that users can attach to any number of views. Service administrators define presets. Notice that when you delete a preset, any alerts that are defined by using this preset are automatically deleted.

* You can enable or disable the feature on alerts that allows a user to mute an alert for a period of time. This feature only applies to email notification channels.

* You can [detach an alert](/docs/activity-tracker?topic=activity-tracker-alerts#alerts_delete_view) from a view.

* The timestamp that you see in a notification is set to UTC. For email notifications, you can set the **Timezone** to define a different timestamp value such as local time.




### Presence alert
{: #mon_alerts_presence}

Configure a presence alert to notify when the number of events that show in a view is more than what you expect.

For example, you might have a view that shows events that report the deletion of service instances in your account. You are not expecting the deletion of service instances. You can configure a *presence alert* that triggers an alert when 1 or more events show in the view.


### Absence alert
{: #mon_alerts_absences}

Configure an absence alert to notify when the number of events that show in a view is less than what you expect, or none.

An absence alert is triggered when the view that has an absence alert attached to it is active. A view is active when the view receives events within the last 24 hours.
{: important}

For example, you might have a view that does not get any events for 2 days. Therefore, this view is not active. You have an absence alert attached to this view that is configured to send a notification after 30 minutes. Because the view is not active, the absence alert is muted and you do not get notifications. To make the view active and get notifications for the absence condition, events need to start flowing into the view.


### Alert conditions
{: #mon_alerts_conditions}

You can configure any of the following conditions for an alert:

* **Time frequency**: You set this condition to specify how often to trigger an alert. Valid values are: 30 seconds, 1 minute, 5 minutes, 15 minutes, 30 minutes, 1 hour, 6 hours, 12 hours, 24 hours
* **Event lines counter**: You set this condition to specify the number of event lines that match the view's filtering and search criteria. When the number of event lines is reached, an alert is triggered.

You can decide whether both conditions are checked or only one. If both conditions are set, an alert is triggered when any of the thresholds is reached.

If you set the *Event lines counter* to be the only condition that triggers an alert, the time frequency that is set when you configure the condition determines the time that it takes for the alert condition to be reset after the alert is triggered.
{: note}

For example, you can configure an alert that is triggered after 30 seconds, or when a 100 event lines that match the view's filtering and search criteria are collected.


### Mute alert notifications
{: #mon_alerts_mute}

By default, the feature that controls the ability of a user to mute notifications is enabled when you configure an alert on a custom view. The **Muteable** feature applies to email notifications only.

When the **mutable** feature is enabled on an alert, a user can pause notifications for a period of time. A user can choose to mute an alert for a period of 1 hour, 6 hours, 12 hours, or 1 day.






## Exporting events
{: #mon_export}

You might need access to a set of events outside the web UI to investigate an issue in more detail.

You can export data in JSONL format from an {{site.data.keyword.at_full_notm}} instance into a local file.

You can export events through a view in the web UI, or programmatically by using a REST API.

Consider the following information when you export log data:
* You can export a set of event entries. To define the set of data that you want to export, you can apply filter and searches. You can also specify the time range.
* From the Web UI, when you export events, you get an email that is sent to your email address, with a link to a compressed file that includes the data. To get the data, you must click the link and download the compressed file.
* When you export events programmatically, you can choose to send an email or to write events into your terminal.
* The compressed log file that contains the data that you want to export is available for a maximum of 12 hours.
* When you export events, you have a limit of lines that you can export in a request. You can specify to export older lines or newer lines in case you reach the limit in the time range that you specify for the export. The maximum number of lines that you can export through the UI is `10.000` lines. The maximum number of lines that you can export per API request is `500.000` lines.


### Exporting events by using the REST API
{: #mon_export_api}

You can export events programmatically by using the Export REST API. [Learn more](/docs/activity-tracker?topic=activity-tracker-export_api).

When you export events programmatically:

* You can choose to send an email or to stream events into your terminal.
* You must use a service key to pass the credentials that must be used when you make an export REST API call.

    You must have **manager** role for the {{site.data.keyword.at_full_notm}} instance or service to view and generate service keys in the web UI.


### Exporting events through a view in the web UI
{: #mon_export_ui}

You can export events through a view in the web UI.

In the web UI, you can select a view that displays the data that you want to export. For this view, you must choose the task to **Export Lines**. You must specify a time range, and whether to export newer lines or older lines. Then, you can request the export.

After you submit a request, you get an email that is sent to your email address, with a link to a compressed file that includes the data.
* To get the data, you must click the link and download the compressed file.
* The compressed file that contains the data that you want to export is available for a maximum of 48 hours.

[Learn more about exporting events through the web UI](/docs/activity-tracker?topic=activity-tracker-export).
