---

copyright:
  years: 2019, 2020
lastupdated: "2020-01-08"

keywords: IBM Cloud, LogDNA, Activity Tracker, usage

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


# Controlling data usage
{: #control_usage}

In {{site.data.keyword.at_full}}, you can control the data that is collected and available for analysis through a LogDNA instance. You can define exclusion rules in the UI that apply to data collected in that instance. You can define an alert that is triggered when the data usage threshold that you define for that LogDNA instance is reached.
{:shortdesc}



## Controlling data by using exclusion rules
{: #control_usage_rule}

You can configure exclusion rules through the LogDNA web UI to stop events from counting against your data usage quota and from being stored for search.

Events that are excluded do not count towards your data usage quota. Also, events that match the exclusion rule are not archived.
{: note}

When you exclude events through an exclusion rule, you can choose to **Preserve these lines for live-tail and alerting**. When you check this option, log lines that match the exclusion rule are shown through the live tail and you can set up an alert for that data.

[Learn more](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-exclusion).

​


## Configuring an alert to notify when a data threshold is reached
{: #control_usage_alert}

In a {{site.data.keyword.at_full_notm}} instance, you can define an alert to notify when the data usage in the instance reaches the data usage threshold that you set for the instance.

Complete the following steps to configure an alert that informs you when you reach a specific data volume in the instance:

1. [Launch the {{site.data.keyword.at_full_notm}} web UI](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-launch).

2. Select the **Settings** icon ![Configuration icon](images/admin.png "Admin icon"). Then select **Usage**.

    In the **Dashboard** section, you can see your data usage.

3. Define a **Usage Alert** to set the threshold for data usage in the instance. When the threshold is reached, you are notified. Enter a value to set the data usage threshold.

4. In the **Add recipient** section, enter one or more emails where the notification will be sent.



