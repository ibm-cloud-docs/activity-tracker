---

copyright:
  years: 2019, 2021
lastupdated: "2021-10-21"

keywords: IBM Cloud, Activity Tracker, usage

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}


# Controlling data usage
{: #control_usage}


In {{site.data.keyword.at_full}}, you can control the data that is collected and available for analysis through an auditing instance. You can define exclusion rules in the UI that apply to data collected in that instance. You can define an alert that is triggered when the data usage threshold that you define for that auditing instance is reached.
{: shortdesc}

This information applies only if you use an {{site.data.keyword.at_full}} [hosted event search offering](/docs/activity-tracker?topic=activity-tracker-service_plan).
{: important}

## Controlling data by using exclusion rules
{: #control_usage_rule}

You can configure exclusion rules through the UI to stop events from counting against your data usage quota and from being stored for long term storage.

Events that are excluded do not count towards your data usage quota. Also, events that match the exclusion rule are not archived.
{: note}

When you exclude events through an exclusion rule, you can choose to **Preserve these lines for live-tail and alerting**. When you check this option, log lines that match the exclusion rule are shown through the live tail and you can set up an alert for that data. These lines show as `(not retained)`.

[Learn more](/docs/activity-tracker?topic=activity-tracker-exclusion_rules).

​


## Configuring an alert to notify when a data threshold is reached
{: #control_usage_alert}

In a {{site.data.keyword.at_full_notm}} instance, you can define an alert to notify when the data usage in the instance reaches the data usage threshold that you set for the instance.

[Learn more](/docs/activity-tracker?topic=activity-tracker-control_usage_alert).


