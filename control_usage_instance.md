---

copyright:
  years: 2019, 2024
lastupdated: "2024-05-17"

keywords:

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}


# Configuring an alert (WIP)
{: #control_usage_instance}

make a tutorial
{: note}

In {{site.data.keyword.at_full}}, you can define an alert to notify when a condition, that is defined by the filtering criteria of a custom view, reaches a theshold that the user configures. The user can choose from absence or presence alert types.
{: shortdesc}

<!-- Common deprecation statement -->
{{../log-analysis/_include-segments/deprecation_notice.md}}



## Prereqs
{: #control_usage_instance_prereqs}

The following table lists the minimum policies that a user must have to be able to launch the {{site.data.keyword.at_full_notm}} Web UI, view events, and define an alert:

| Service                               | Role                      | Permission granted            |
|---------------------------------------|---------------------------|-------------------------------|
| `{{site.data.keyword.at_full_notm}}` | Platform role: Viewer     | Allows the user to view the list of service instances in the Observability Logging dashboard. |
| `{{site.data.keyword.at_full_notm}}` | Service role: Manager or Standard-member      | Allows the user to launch the Web UI and create alerts.  |
{: caption="Table 1. IAM policies" caption-side="top"}


## Step 1. Configure a view
{: #control_usage_instance_step1}

Complete the following steps to configure a view that displays all the data that is collected through the instance:

1. [Go to the web UI](/docs/services/activity-tracker?topic=activity-tracker-launch#launch).

2. Click the **Views** icon ![Views icon](images/views.png "Views icon").

3. Select **Everything** to see all the events, or a view.

4. In the search bar, enter the following query: `hosts:*`

5. Save the view.


## Step 2. Configure a presence alert
{: #control_usage_instance_step2}

Complete the following steps to configure an alert that informs you when you reach a specific data volume in the instance:

1. In the web UI, click the **Views** icon ![Views icon](images/views.png "Views icon").
2. Click the view name. Then, select **Attach an alert**.
3. Select **View-specific alert**.
4. Select the type of alert (Slack, Email, Webhook, or PagerDuty).  If you selected the wrong alert type and you want to change it, click **Delete Alert Channel**.
5. Configure when you want the alert to be sent.

    Select **Presence** alert.

    Indicate the criteria when an alert should be sent. Indicate the number of lines that you want to set as your threshold. For example, when 100000 lines matching in the view are logged in an hour.  A graph will help you determine the number of event lines matching your specified criteria.

    Select the triggering condition so that the alert is sent at the end of the selected period or immediately when the number of lines are logged.

    Optionally you can specify a **Custom schedule** with alerting limited to a specified timezone, days of the week, or timeframe. To configure a **Custom schedule**:

    Select **on** for **Custom schedule**.

    Select the Timezone for the event entries.

    Select the days of the week when alerts should be generated.

    Optionally specify a time range for the selected days. A graph will help you determine the number of event entries for the timezone and time range.

6. Depending on the type of alert you will also need to configure additional settings, for example:

    **Slack**:  Specify your **Webhook** URL and the desired **Message color**.

    **Email**: Specify the **Recipients** of the email and a **Timezone**. The timezone defines the timestamp value of each event that is included in the email. To see UTC timestamps, you can select **(GMT +00:00) UTC**.

    **PagerDuty**: Specify the **Service**.  If required, you will be prompted to connect to PagerDuty.

    **Webhook**: Specify the **Method & URL**, and the **Headers** and **Body** of the `JSON` used to interact with your webhook.  You can use **Validate JSON** to make sure your `JSON` is correct before creating the alert.

7. You can click **Test** to test that your alert configuration is correct.

    ![Test option](images/alert_test.png "Example event showing Test option")

8. Click **Save Alert**.

9. If you want to create an additional alert channel, click **+** and follow the prior steps to create additional channels.  You can create different channel types, for example, an email and a Slack channel.  Or, you can create multiple channels of the same type with different alert criteria.

Alerts will be generated based on your configuration.
