---

copyright:
  years: 2019, 2021
lastupdated: "2021-10-21"

keywords: IBM Cloud, Activity Tracker, usage

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}


# Configuring an alert to notify when a data threshold is reached
{: #control_usage_alert}


In {{site.data.keyword.at_full}}, you can define an alert to notify when the data usage in the instance reaches the data usage threshold that you set for the instance.
{: shortdesc}

This information applies only if you use an {{site.data.keyword.at_full}} [hosted event search offering](/docs/activity-tracker?topic=activity-tracker-service_plan).
{: important}



## Prereqs
{: #control_usage_alert_prereqs}

You must have the service role **manager** to configure data threshold alerts.


## Configure an alert
{: #control_usage_alert_configure}

Complete the following steps to configure an alert that informs you when you reach a specific data volume in the instance:

1. [Launch the {{site.data.keyword.at_full_notm}} web UI](/docs/services/activity-tracker?topic=activity-tracker-launch).

2. Select the **Settings** icon ![Configuration icon](images/admin.png "Admin icon"). Then select **Usage**.

    In the **Dashboard** section, you can see your data usage.

3. Define a **Usage Alert** to set the **Usage Limit** threshold for data usage in the instance. When the usage reaches the percentage of the threshold you selected, the email recipient will be notified. 

4. In the **Add recipient** section, enter one or more emails where the notification will be sent.



