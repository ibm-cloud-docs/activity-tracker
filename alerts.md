---

copyright:
  years: 2019, 2020
lastupdated: "2020-01-08"

keywords: IBM Cloud, LogDNA, Activity Tracker, alerts, events

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


# Managing alerts
{: #alerts}

Through the {{site.data.keyword.at_full_notm}} web UI, you can apply search queries to define the events that are displayed through a custom view. Then, you can attach an alert to that view to be notified when a condition occurs. You can attach one or more alerts to a view. You can define multiple notification channels for an alert. You can mute alerts. You can detach alerts from a view.
{:shortdesc}


## Configure an alert
{: alerts_config}

### Prerequisites
{: #alerts_prereqs}

* [Learn more about alerts](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-monitor_events#mon_alerts).

* **You must have a paid service plan** for the {{site.data.keyword.at_full_notm}} service. [Learn more](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-service_plan#service_plan).

* Check that your user ID has permissions to launch the web UI and view events. The following table lists the minimum roles that a user must have to be able to launch the {{site.data.keyword.at_full_notm}} web UI, and view, search, and filter events:

| Role                      | Permission granted            |
|---------------------------|-------------------------------|  
| Platform role: `Viewer`     | Allows the user to view the list of service instances in the Observability dashboard. |
| Service role: `Reader`      | Allows the user to launch the web UI and view events in the web UI.  |
{: caption="Table 1. IAM roles" caption-side="top"} 

For more information on how to configure policies for a user, see [Granting user permissions to a user or service ID](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-iam_view_events#iam_view_events).

 


### Step 1. Go to the web UI
{: #alerts_step1}

[Go to the web UI](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-launch#launch).


### Step 2. Create a view
{: #alerts_step2}

[Create a view](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-views).


### Step 3. Configure an alert
{: #alerts_step3}

Choose one of the following options to attach an alert to a view:

#### Option 1. Configure an alert by using a preset
{: #alerts_step3_preset}

Complete the following steps to attach a preset to a view:

1. In the web UI, click the **Views** icon ![Views icon](images/views.png).
2. Click the view name to which you want to attach an alert. Then, select **Attach an alert**.
3. Enable or disable the ability of a user to [mute an alert](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-monitor_events#mon_alerts_mute). By default, it is enabled. This step only applies if you are configuring an email notification channel.
4. Choose a preset to reuse an alert definition. 
5. Click **Save alert**. 



#### Option 2. Configure a view-specific alert
{: #alerts_step3_view}

Complete the following steps to attach an alert to a view:

1. In the web UI, click the **Views** icon ![Views icon](images/views.png).
2. Click the view name. Then, select **Attach an alert**.
3. Enable or disable the ability of a user to [mute an alert](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-monitor_events#mon_alerts_mute). By default, it is enabled. This step only applies if you are configuring an email notification channel.
4. Choose **view-specific alert**.
5. Choose a notification channel. 
6. Select the type of alert. Choose the **Presence alert** type to notify when the number of events that show in a view is more than what you expect. Choose the **Absence alert** type to notify when the number of events that show in a view is less than what you expect, or none. 
7. Define the threshold conditions.

    1. Select a time frequency. For example, 12 hours.

    2. Enter the number of event lines after which you want the alert to trigger.

    3. Select whether you want both conditions to be checked or just one.

8. Add the details for the notification channel that you have chosen.

    For example, for the email notification channel, add one or more recipients, and optionally a time zone. The time zone defines the timestamp value of each event that is included in the email. To see UTC timestamps, you can select **(GMT +00:00) UTC**.

9. Click **Save alert**.


## Configure a preset (alert template)
{: #alerts_preset_config}

To reuse an alert configuration with different views, a service administrator can configure an **alert preset**.
{: note}

Complete the following steps to configure a preset:

1. In the web UI, select the **Settings** icon ![Settings icon](images/admin.png "Admin icon").
2. Select **Alerts**.
3. Select **Add a preset alert**.
4. Choose a notification channel. For the list of supported channels, see [Alert notification channels](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-channels).
5. Select the type of alert. Choose the **Presence alert** type to notify when the number of events that show in a view is more than what you expect. Choose the **Absence alert** type to notify when the number of events that show in a view is less than what you expect, or none. 
5. Choose a notification channel. For the list of supported channels, see [Alert notification channels](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-channels).
6. Define the threshold conditions.

    1. Select a time frequency. For example, 12 hours.

    2. Enter the number of event lines after which you want the alert to trigger.

    3. Select whether you want both conditions to be checked or just one.

7. Add the details for the notification channel that you have chosen.

    For example, for the email notification channel, add one or more recipients, and optionally a time zone.

8. Click **Save alert**.


## Delete a preset
{: #alerts_delete_preset}

You can manage presets through the *Alerts* dashboard.

Complete the following steps to delete a preset from the *Alerts** dashboard:

1. In the web UI, select the **Settings** icon ![Settings icon](images/admin.png "Admin icon").
2. Select **Alerts**.
3. Hover the mouse over the *edit* button of the preset that you want to delete. The *delete* option shows.
4. Select **Delete**.
5. Confirm that you want to delete the preset by clicking **Delete**.

When you delete a preset, any alerts that are defined by using this preset are automatically deleted.
{: note}

## Detach a view-specific alert
{: #alerts_delete_view}

Complete the following steps to detach an alert from the *Alerts** dashboard:

1. In the web UI, select the **Settings** icon ![Settings icon](images/admin.png "Admin icon").
2. Select **Alerts**.
3. Hover the mouse over the *edit* button of the alert that you want to delete. The *detach* option shows.
4. Select **Detach**.
5. Confirm that you want to delete the alert by clicking **Detach**.



## Mute an alert
{: #alerts_mute}

This section applies to email alerts.
{: note}

After you configure an alert on a view and receive a notification email from `LogDNA Alerts`, complete the following steps to mute the alert a period of time:

1. Go to the email account where you receive email notifications.

2. Open a notification email for a view that you want to mute. 

    Look for emails that are sent by `LogDNA Alerts`. The subject includes the name of the view.

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

    From this page, you can select **unmute** to enable notifications on the view. You can also select **manage** to go to the *Alerts* dashboard in the web UI.


## Unmute a muted alert
{: #alerts_manage_mute}

You can manage alerts through the *Alerts* dashboard.

1. Launch the *Alerts* dashboard.

    In the web UI, select the **Settings** icon ![Settings icon](images/admin.png "Admin icon").

    Select **Alerts**.

    You can see the list of alerts that are muted. Each entry informs about the view where notifications are muted, the user who requested the action, and the UTC time when notifications will be enabled. 

2. Select an alert that you want to unmute.

3. Click **Unmute**.






