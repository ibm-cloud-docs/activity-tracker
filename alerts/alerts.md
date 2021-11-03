---

copyright:
  years: 2019, 2021
lastupdated: "2021-08-09"

keywords: IBM Cloud, Activity Tracker, auditing, alerts

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}

 
# Working with alerts
{: #alerts}

You can configure alerts to notify about the activity in your {{site.data.keyword.cloud_notm}} account and changes in configuration in the account. 
{: shortdesc}

This information applies only if you use an {{site.data.keyword.at_full}} [hosted event search offering](/docs/activity-tracker?topic=activity-tracker-service_plan).
{: important}

A rule specifies the scope of the data that you want to monitor and be notified if certain conditions occur. Per alert rule, consider the following information:
- You can define 1 or more notification channels. 
- You can configure different alert types for each notification channel that you configure for an alert.
- You can configure different triggering conditions for each notification channel that you configure for an alert.
 
A rule is also the basis of a `view`. You can see the data that is included by any rule by using it as a view. The two are interchangeable. 

## Types of alerts
{: #alerts_types}

You can configure any of the following types of alerts for each notification channel that you configure for an alert:

### Presence alert
{: #alerts_presence}

You can configure a presence alert to notify when the number of events that show in a view is more than what you expect. 

For example, you might have a view that shows events that report payments that are rejected by your service. You can configure a *presence alert* that triggers an alert when 1 or more events show in the view.


### Absence alert
{: #alerts_absence}

Configure an absence alert to notify when the number of events that show in a view is less than what you expect, or none. 

An absence alert is triggered when the view that has an absence alert attached to it is active. A view is active when the view receives events within the last 24 hours.
{: important}

For example, you might have a view that does not get any events for 2 days. Therefore, this view is not active. You have an absence alert attached to this view that is configured to send a notification after 30 minutes. Because the view is not active, the absence alert is muted and you do not get notifications. To make the view active and get notifications for the absence condition, events need to start flowing into the view. 


## Alert conditions
{: #alerts_conditions}

You can configure any of the following triggering conditions for each notification channel that you configure for an alert:

* **Time frequency**: You set this condition to specify how often to trigger an alert. Valid values are: 30 seconds, 1 minute, 5 minutes, 15 minutes, 30 minutes, 1 hour, 6 hours, 12 hours, 24 hours
* **Event lines counter**: You set this condition to specify the number of event lines that match the view's filtering and search criteria. When the number of event lines is reached, an alert is triggered.

You can decide whether both conditions are checked or only one. If both conditions are set, an alert is triggered when any of the thresholds is reached. 

For example, you can configure an alert that is triggered after 30 seconds, or when a 100 event lines that match the view's filtering and search criteria are collected.


## Notification channels
{: #alerts_channels}

You can define 1 or more notification channels for an alert.

The following table lists the notification channels that you can configure when an alert is triggered:

| Channel           | Configuration details | 
|-------------------|-----------------------|
| `email`             | You can configure one or more email addresses. For more information, see [Integrating with email](/docs/activity-tracker?topic=activity-tracker-email). |
| `SMS`               | You can send an SMS to notify of an alert either through the PagerDuty channel or through the {{site.data.keyword.mon_full_notm}} channel. For more information, see [Integrating with SMS](/docs/activity-tracker?topic=activity-tracker-sms). |
| `Slack`             | You can configure a slack channel. |
| `Webhook`           | You can configure a web hook URL. |
| `PagerDuty`         | You can configure connection details to your PagerDuty system, and select a service. Use this channel when you require call times and escalation management processes. For more information, see [Integrating with PagerDuty](/docs/activity-tracker?topic=activity-tracker-pagerduty). |
| `{{site.data.keyword.mon_full_notm}}`         | You can configure the API key to connect to an {{site.data.keyword.mon_full_notm}} instance. |
{: caption="Notification channels" caption-side="top"} 


## Creating alerts
{: #alerts_create}

You can choose any of the following options to create an alert:
- Create a preset and attach the preset to the view
- Create a specific alert on a view.

You can configure alerts graphically through the {{site.data.keyword.at_short}} UI, or programmatically.
- For more information on how to configure an alert, see [Creating alerts through the UI](/docs/activity-tracker?topic=activity-tracker-create_alert_ui).
- For more information on how to create alerts programmatically, see [Managing views and alerts programmatically](/docs/activity-tracker?topic=activity-tracker-config-api).


## Deleting alerts
{: #alerts_delete}

You can delete alerts graphically through the {{site.data.keyword.at_short}} UI, or programmatically.
- For more information on how to delete an alert, see [Removing alerts through the UI](/docs/activity-tracker?topic=activity-tracker-remove_alert_ui).
- For more information on how to delete alerts programmatically, see [Managing views and alerts programmatically](/docs/activity-tracker?topic=activity-tracker-config-api#config-api-create-view-alert).


## Managing presets (alert templates)
{: #alerts_preset}

To reuse an alert configuration, a service administrator can configure an **alert preset** (alert template).
- For more information on how to create a preset, see [Create a preset](/docs/activity-tracker?topic=activity-tracker-preset_ui#preset_ui_create).
- For more information on how to delete a preset, see [Delete a preset](/docs/activity-tracker?topic=activity-tracker-preset_ui#preset_ui_delete).


## Muting alert notifications
{: #mon_alerts_mute}

By default, the feature that controls the ability of a user to mute notifications is enabled when you configure an alert on a custom view. The **Mutable** feature applies to email notifications only.

When the **mutable** feature is enabled on an alert, a user can pause notifications for a period of time. A user can choose to mute an alert for a period of 1 hour, 6 hours, 12 hours, or 1 day. 

For more information on how to mute an email alert, see [Muting an alert](/docs/activity-tracker?topic=activity-tracker-email#email_mute).

For more information on how to ummute an email alert, see [Unmuting a muted alert](/docs/activity-tracker?topic=activity-tracker-email#email_unmute).



