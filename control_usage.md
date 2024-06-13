---

copyright:
  years: 2019, 2024
lastupdated: "2024-05-24"

keywords:

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}


# Controlling data usage
{: #control_usage}


In {{site.data.keyword.at_full}}, you can control the data that is collected and available for analysis through an auditing instance. You can define exclusion rules in the UI that apply to data collected in that instance. You can define an alert that is triggered when the data usage threshold that you define for that auditing instance is reached.
{: shortdesc}


{{../log-analysis/_include-segments/deprecation_notice.md}}

## Controlling data by using exclusion rules
{: #control_usage_1}

You can configure exclusion rules through the UI to stop events from counting against your data usage quota and from being stored for long term storage.

Events that are excluded do not count towards your data usage quota. Also, events that match the exclusion rule are not archived.
{: note}

When you exclude events through an exclusion rule, you can choose to **Preserve these lines for live-tail and alerting**. When you check this option, log lines that match the exclusion rule are shown through the live tail and you can set up an alert for that data. These lines show as `(not retained)`.

[Learn more](/docs/activity-tracker?topic=activity-tracker-exclusion_rules).



## Configuring the usage alert
{: #control_usage_2}

In {{site.data.keyword.at_full}}, you can define an alert to notify when the data usage in the instance reaches the data usage threshold that you set for the instance.

[Learn more](/docs/activity-tracker?topic=activity-tracker-control_usage_alert).


## Configuring an ingestion alert
{: #control_usage_3}

In {{site.data.keyword.at_full}}, you can define an alert to notify when the data collected reaches a threshold within a period of time that you can customize.

[Learn more](/docs/activity-tracker?topic=activity-tracker-control_usage_instance).

## Analyzing event data trends
{: #control_usage_4}

In {{site.data.keyword.at_full}}, you can query your auditing instance by using the *Usage API* and identify trends over a period of time.

You can analyze event data trends to assess the growth or decline of auditing data over time for services running in your account. You can monitor data trends to identify patterns and make predictions of how services are used in the account.

When you use the *Usage* API, consider the following information:
- Analyze 3 or more months worth of auditing data to identify patterns and trends.
- You can use the API to monitor the number of lines that are collected per service over a period of time.
- You can use the API to find out the top services that are driving the main load of data in a region.
- If you have exclusion rules defined, these lines are not included in the usage data response. The API reports number of lines that are ingested and not excluded via exclusion rules.

You can query data usage for up to 6 months.
{: note}

[Learn more](/docs/activity-tracker?topic=activity-tracker-control_usage_api).
