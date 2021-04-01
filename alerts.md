---

copyright:
  years: 2019, 2021
lastupdated: "2021-03-28"

keywords: IBM Cloud, Activity Tracker, alerts, events

subcollection: activity-tracker

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


# Managing alerts through the UI
{: #alerts}

Through the {{site.data.keyword.at_full_notm}} web UI, you can apply search queries to define the events that are displayed through a custom view. Then, you can attach an alert to that view to be notified when a condition occurs. You can attach one or more alerts to a view. You can define multiple notification channels for an alert. You can mute alerts. You can detach alerts from a view.
{:shortdesc}


## Configure an alert
{: alerts_config}

### Prerequisites
{: #alerts_prereqs}

* [Learn more about alerts](/docs/services/activity-tracker?topic=activity-tracker-monitor_events#mon_alerts).

* **You must have a paid service plan** for the {{site.data.keyword.at_full_notm}} service. [Learn more](/docs/services/activity-tracker?topic=activity-tracker-service_plan#service_plan).

* Check that your user ID has permissions to launch the web UI and view events. The following table lists the minimum roles that a user must have to be able to launch the {{site.data.keyword.at_full_notm}} web UI, and view, search, and filter events:

| Role                      | Permission granted            |
|---------------------------|-------------------------------|  
| Platform role: `Viewer`     | Allows the user to view the list of service instances in the Observability dashboard. |
| Service role: `Reader`      | Allows the user to launch the web UI and view events in the web UI.  |
{: caption="Table 1. IAM roles" caption-side="top"} 

For more information on how to configure policies for a user, see [Granting user permissions to a user or service ID](/docs/services/activity-tracker?topic=activity-tracker-iam_view_events#iam_view_events).

 


### Step 1. Go to the web UI
{: #alerts_step1}

[Go to the web UI](/docs/services/activity-tracker?topic=activity-tracker-launch#launch).


### Step 2. Create a view
{: #alerts_step2}

[Create a view](/docs/services/activity-tracker?topic=activity-tracker-views).


### Step 3. Configure an alert
{: #alerts_step3}

Choose one of the following options to attach an alert to a view.

You cannot attach an alert to the **EVERYTHING** view.
{: note}

#### Option 1. Configure an alert by using a preset
{: #alerts_step3_preset}

Complete the following steps to attach a preset to a view.

A preset is defined by a service administrator.
{: note}

1. In the web UI, click the **Views** icon ![Views icon](images/views.png "Views icon").
2. Click the view name to which you want to attach an alert. Then, select **Attach an alert**.
4. Choose a preset to reuse an alert definition. 
5. Click **Save Alert**. 

#### Option 2. Configure a view-specific alert
{: #alerts_step3_view}

Complete the following steps to attach an alert to a view:

1. In the web UI, click the **Views** icon ![Views icon](images/views.png "Views icon").
2. Click the view name. Then, select **Attach an alert**.
3. Select **View-specific alert**.
4. Select the type of alert (Slack, Email, Webhook, or PagerDuty).  If you selected the wrong alert type and you want to change it, click **Delete Alert Channel**.
5. Configure when you want the alter to be sent.
   1. Select if you want the alert to be sent when the condition exists (**Presence**) or does not exist (**Absence**).
   2. Indicate the logging criteria when an alert should be sent.  For example, when 100 lines matching in the view are logged in an hour.  A graph will help you determine the number of log lines matching your specified criteria.
   3. Select if the alert should be sent at the end of the selected period or immediately when the number of lines are logged.
   4. Optionally you can specify a **Custom schedule** with alerting limited to a specified timezone, days of the week, or timeframe. To configure a **Custom schedule**:
      1. Select **on** for **Custom schedule**.
      2. Select the Timezone for the log entries. 
      3. Select the days of the week when alerts should be generated.
      4. Optionally specify a time range for the selected days. A graph will help you determine the number of log entries for the timezone and time range.
   5. Depending on the type of alert you will also need to configure additional settings:

      **Slack**:  Specify your **Webhook** URL and the desired **Message color**.

      **Email**: Specify the **Recipients** of the email and a **Timezone**. The timezone defines the timestamp value of each event that is included in the email. To see UTC timestamps, you can select **(GMT +00:00) UTC**. 

      **PagerDuty**: Specify the **Service**.  If required, you will be prompted to connect to PagerDuty.

      **Webhook**: Specify the **Method & URL**, and the **Headers** and **Body** of the `JSON` used to interact with your webhook.  You can use **Validate JSON** to make sure your `JSON` is correct before creating the alert.

   6. You can click **Test** to test that your alert configuration is correct.

      ![Test option](images/alert_test.png "Example dialog showing Test option")

   7. Click **Save Alert**.

   8. If you want to create an additional alert channel, click **+** and follow the prior steps to create additional channels.  You can create different channel types, for example, an email and a Slack channel.  Or, you can create multiple channels of the same type with different alert criteria.

Alerts will be generated based on your configuration.

## Configure a preset (alert template)
{: #alerts_preset_config}

To reuse an alert configuration with different views, a service administrator can configure an **alert preset**.
{: note}

Complete the following steps to configure a preset:

1. In the web UI, select the **Settings** icon ![Settings icon](images/admin.png "Settings icon").
2. Select **ALERTS**.
3. Select **Add Preset**.
4. Specify a name for the preset.
5. Select the type of alert (Slack, Email, Webhook, or PagerDuty).  If you selected the wrong alert type and you want to change it, click **Delete Alert Channel**.
6. Configure the type of alert.
   1. Select if you want the alert to be sent when the condition exists (**Presence**) or does not exist (**Absence**).
   2. Indicate the logging criteria when an alert should be sent.  For example, when 100 lines matching in the view are logged in an hour.  A graph will help you determine the number of log lines matching your specified criteria.
   3. Select if the alert should be sent at the end of the selected period or immediately when the number of lines are logged.
   4. Optionally you can specify a **Custom schedule** with alerting limited to a specified timezone, days of the week, or timeframe. To configure a **Custom schedule**:
      1. Select **on** for **Custom schedule**.
      2. Select the Timezone for the log entries. 
      3. Select the days of the week when alerts should be generated.
      4. Optionally specify a time range for the selected days. A graph will help you determine the number of log entries for the timezone and time range.
   5. Depending on the type of alert you will also need to configure additional settings:

      **Slack**:  Specify your **Webhook** URL and the desired **Message color**.

      **Email**: Specify the **Recipients** of the email and a **Timezone**. The timezone defines the timestamp value of each event that is included in the email. To see UTC timestamps, you can select **(GMT +00:00) UTC**. 

      **PagerDuty**: Specify the **Service**.  If required, you will be prompted to connect to PagerDuty.

      **Webhook**: Specify the **Method & URL**, and the **Headers** and **Body** of the `JSON` used to interact with your webhook.  You can use **Validate JSON** to make sure your `JSON` is correct before creating the alert.

   6. You can click **Test** to test that your alert configuration is correct.

      ![Test option](images/alert_test.png "Example dialog showing Test option")

   7. Click **Save Alert**

   8. If you want to create an additional alert channel, click **+** and follow the prior steps to create additional channels.  You can create different channel types, for example, an email and a Slack channel.  Or, you can create multiple channels of the same type with different alert criteria.

Your preset can now be used by others to setup alerts.


## Delete a preset
{: #alerts_delete_preset}

You can manage presets through the **ALERTS** dashboard.

Complete the following steps to delete a preset from the **ALERTS** dashboard:

1. In the web UI, select the **Settings** icon ![Settings icon](images/admin.png "Settings icon").
2. Select **ALERTS**.
3. Hover the mouse over the **Edit**** button of the preset that you want to delete. The **Delete** option displays.
4. Click **Delete**.
5. Confirm that you want to delete the preset by clicking **Yes, delete**.

When you delete a preset, any alerts that are defined by using this preset are automatically deleted.
{: note}

## Detach a view-specific alert
{: #alerts_delete_view}

Complete the following steps to detach an alert from the **ALERTS** dashboard:

1. In the web UI, click the **Views** icon ![Views icon](images/views.png "Views icon").
2. Click the view name. Then, select **Detach alert**.
3. Confirm you want to remove the alert by clicking **Detach**.


## Mute an alert
{: #alerts_mute}

This section only applies to email alerts.
{: note}

After you configure an alert on a view and receive a notification email, complete the following steps to mute the alert a period of time:

1. Go to the email account where you receive email notifications.

2. Open a notification email for a view that you want to mute. 

    Look for emails that are sent by {{site.data.keyword.at_full_notm}}. The subject includes the name of the view.

    In the email, there is a section that includes the following text: 

    ```
     Mute these alerts for   [1 Hour] [6 Hours] [12 Hours] [1 Day]
    ```
    {: screen}

3. Choose a period of time.

    A window opens. The information provided indicates the view, the notification that is muted, and the time period that is muted for.

    For example, you can get a message that indicates the following:

    ```
    Email alerting for MyView has been muted for an hour.

    Unmute

    Alerting is scheduled to resume at Jun 14, 11:59am.

    Manage Alerts
    ```
    {: screen}

    From this page, you can select **Unmute** to enable notifications on the view. You can also select **Manage** to go to the **ALERTS** dashboard in the web UI.


## Unmute a muted alert
{: #alerts_manage_mute}

You can manage alerts through the **ALERTS** dashboard.

1. Launch the **ALERTS** dashboard.

    In the web UI, select the **Settings** icon ![Settings icon](images/admin.png "Admin icon").

    Select **ALERTS**.

    You can see the list of alerts that are muted. Each entry informs about the view where notifications are muted, the user who requested the action, and the UTC time when notifications will be enabled. 

2. Select an alert that you want to unmute.

3. Click **Unmute**.






