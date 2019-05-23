---

copyright:
  years: 2019
lastupdated: "2019-05-25"

keywords: IBM Cloud, LogDNA, Activity Tracker, alerts, events

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


# Configuring alerts
{: #alerts}

Through the {{site.data.keyword.at_full_notm}} web UI, you can apply search queries to define the events that are displayed through a custom view. Then, you can attach an alert to that view to be notified when a condition occurs. You can attach one or more alerts to a view. You can define multiple notification channels for an alert. You can mute alerts. You can detach alerts from a view.
{:shortdesc}


## Prerequisites
{: #alerts_prereqs}

* [Learn more about alerts](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-monitor_events#mon_alerts).

* **You must have a paid service plan** for the {{site.data.keyword.at_full_notm}} service. [Learn more](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-service_plan#service_plan).

* Check that your user ID has permissions to launch the web UI and view events. The following table lists the minimum roles that a user must have to be able to launch the {{site.data.keyword.at_full_notm}} web UI, and view, search, and filter events:

| Role                      | Permission granted            |
|---------------------------|-------------------------------|  
| Platform role: `Viewer`     | Allows the user to view the list of service instances in the Observability dashboard. |
| Service role: `Reader`      | Allows the user to launch the web UI and view events in the web UI.  |
{: caption="Table 1. IAM roles" caption-side="top"} 

For more information on how to configure policies for a user, see [Granting user permissions to a user or service ID](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-iam_view_events#iam_view_events).

 


## Step 1. Go to the web UI
{: #alerts_step1}

[Go to the web UI](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-launch#launch).


## Step 2. Create a view
{: #alerts_step2}

[Create a view](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-views).



## Step 3. [Optional] Configure a preset (alert template)
{: #alerts_step3}

To reuse an alert configuration with different views, configure an **alert preset**.
{: note}

Complete the following steps to configure a preset:

1. In the web UI, select the **Configuration** icon ![Configuration icon](images/admin.png "Admin icon").
2. Select **Alerts**.
3. Select **Add a preset alert**.
4. Choose a notification channel. For the list of supported channels, see [Alert notification channels](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-channels).
5. Select the type of alert. Choose the **Presence alert** type to notify when the number of events that show in a view is more than what you expect. Choose the **Absence alert** type to notify when the number of events that show in a view is less than what you expect, or none. 
5. Choose a notification channel. For the list of supported channels, see [Alert notification channels](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-channels).
6. Define the threshold conditions.

    1. Select a time frequency. For example, 12 hours.

    2. Enter the number of event lines after which you want the alert to trigger.

    3. Select whether you want both conditions to be checked or just one.

7. Add the details for the notification channel that you have chosen.

    For example, for the email notification channel, add one or more recipients, and optionally a time zone.

8. Click **Save alert**.



## Step 4. Configure an alert
{: #alerts_step4}

Choose any of the following options to attach an alert to a view:

### Option 1. Configure an alert by using a preset
{: #alerts_step4_preset}

Complete the following steps to attach a preset to a view:

1. In the web UI, click the **Views** icon ![Configuration icon](images/views.png).
2. Click the view name to which you want to attach an alert. Then, select **Attach an alert**.
3. Choose a preset to reuse an alert definition. 
4. Click **Save alert**. 




### Option 2. Configure a view-specific alert
{: #alerts_step4_view}

Complete the following steps to attach an alert to a view:

1. In the web UI, click the **Views** icon ![Configuration icon](images/views.png).
2. Click the view name. Then, select **Attach an alert**.
3. Choose **view-specific alert**.
4. Choose a notification channel. 
5. Select the type of alert. Choose the **Presence alert** type to notify when the number of events that show in a view is more than what you expect. Choose the **Absence alert** type to notify when the number of events that show in a view is less than what you expect, or none. 
6. Define the threshold conditions.

    1. Select a time frequency. For example, 12 hours.

    2. Enter the number of event lines after which you want the alert to trigger.

    3. Select whether you want both conditions to be checked or just one.

7. Add the details for the notification channel that you have chosen.

    For example, for the email notification channel, add one or more recipients, and optionally a time zone.

8. Click **Save alert**.



## Delete a preset (alert template)
{: #alerts_delete_preset}

Complete the following steps to delete a preset:

1. In the web UI, select the **Configuration** icon ![Configuration icon](images/admin.png "Admin icon").
2. Select **Alerts**.
3. Hover the mouse over the *edit* button of the preset that you want to delete. The *delete* option shows.
4. Select **Delete**.
5. Confirm that you want to delete the preset. Click **Delete**.

## Detach a view-specific alert from a view
{: #alerts_delete_view}

Complete the following steps to detach a preset:

1. In the web UI, select the **Configuration** icon ![Configuration icon](images/admin.png "Admin icon").
2. Select **Alerts**.
3. Hover the mouse over the *edit* button of the alert that you want to delete. The *delete* option shows.
4. Select **Detach**.
5. Confirm that you want to delete the alert. Click **Detach**.








