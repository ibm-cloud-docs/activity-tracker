---

copyright:
  years: 2019, 2021
lastupdated: "2021-03-01"

keywords: IBM Cloud, Activity Tracker, usage

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


# Controlling data usage
{: #control_usage}

In {{site.data.keyword.at_full}}, you can control the data that is collected and available for analysis through a logging instance. You can define exclusion rules in the UI that apply to data collected in that instance. You can define an alert that is triggered when the data usage threshold that you define for that logging instance is reached.
{:shortdesc}



## Controlling data by using exclusion rules
{: #control_usage_rule}

You can configure exclusion rules through the UI to stop events from counting against your data usage quota and from being stored for search.

Events that are excluded do not count towards your data usage quota. Also, events that match the exclusion rule are not archived.
{: note}

When you exclude events through an exclusion rule, you can choose to **Preserve these lines for live-tail and alerting**. When you check this option, log lines that match the exclusion rule are shown through the live tail and you can set up an alert for that data.

[Learn more](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-exclusion_rules).

​


## Configuring an alert to notify when a data threshold is reached
{: #control_usage_alert}

In a {{site.data.keyword.at_full_notm}} instance, you can define an alert to notify when the data usage in the instance reaches the data usage threshold that you set for the instance.

Complete the following steps to configure an alert that informs you when you reach a specific data volume in the instance.

You must have manager access to configure data threshold alerts.
{: note}

1. [Launch the {{site.data.keyword.at_full_notm}} web UI](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-launch).

2. Select the **Settings** icon ![Configuration icon](images/admin.png "Admin icon"). Then select **Usage**.

    In the **Dashboard** section, you can see your data usage.

3. Define a **Usage Alert** to set the **Usage Limit** threshold for data usage in the instance. When the usage reaches the percentage of the threshold you selected, the email recipient will be notified. 

4. In the **Add recipient** section, enter one or more emails where the notification will be sent.



