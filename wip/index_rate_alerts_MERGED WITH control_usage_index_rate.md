---

copyright:
  years: 2022, 2023
lastupdated: "2022-09-22"

keywords:

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}


# Index rate alerts
{: #index_rate_alerts}

In {{site.data.keyword.at_full}}, you can use *index rate alerts* to monitor applications or sources for  data spikes that can affect storage costs.
{: shortdesc}



## What are index rate alerts?
{: #about_index_alerts}

Index rate alerts are calculated from the rate of indexing and ingestion of data for your account. In the console you can see the ratio of log lines ingested to those being stored. That is you can see how much data is being received and indexed.

Index rate alerts are triggered by thresholds you configure for your account. When one or both thresholds are exceeded an alert will be sent.

## Types of thresholds
{: #index_threshold_types}

There are two types of index alert thresholds:

Max line/s
:   The maximum number of lines indexed or stored expected per second.

Max z score
:   An exception to the expected flow rate based on the number of standard deviations from the regular baseline of the past 30 days.

## Considerations when using index rate alerts
{: #index_threshold_considerations}

The index rate is the average value of all index rates measured over the previous rolling hour. Log lines are indexed every five minutes to get the total number of lines indexed over an hour. The total number of lines is divided by 60 to get the average per minute. The result is divided by 60 again to get the average index rate per second for that hour.

If no log lines are ingested for over 60 minutes, you will see a *Check Later* message in the console instead of the index rate. After log lines resume, the *Check later* message is replaced with the index rate value.

Since measurements are taken every five minutes, the first measurement of ingested log lines for that five minutes will be averaged out for the full hour. Any time there is an interruption in ingestion, wait at least an hour before using the index rate value for analysis.



## Configuring index rate alerts using the API
{: #configure_index_alerts_api}
{: api}

You can configure index rates and what alerts are triggered using the [API.]({DomainName}/apidocs/activity-tracker#get-index-rate-alert){: external}

### Creating or updating an index rate alert
{: #create_index_rate_api}

Use the `PUT` REST API command to create or update your index rate alerts. If no index rate alert is configured, the first `PUT` will create the index rate alert.

Run the following command:

```text
curl -X PUT https://<ENDPOINT>/v1/config/index-rate -H 'content-type: application/json'   -H 'servicekey: <SERVICE_KEY>' -d '{"max_lines":<MAX_LINES>,"max_z_score":<MAX_Z_SCORE>,"enabled":<ENABLED>,"channels":<CHANNELS>,"threshold_alert":"<THRESHOLD_ALERT>","frequency":"<FREQUENCY>"}'
```
{: pre}

Where:

`ENDPOINT`
:   Is the [endpoint]/docs/activity-tracker?topic=activity-tracker-endpoints) for your {{site.data.keyword.at_full_notm}} instance.

`SERVICE_KEY`
:   Is the [service key](/docs/activity-tracker?topic=activity-tracker-service_keys) for your {{site.data.keyword.at_full_notm}} instance.

`MAX_LINES`
:   Is the number of lines required in order to trigger the alert.

`MAX_Z_SCORE`
:   Is the number of standard deviations above the 30 day average lines in order to trigger the alert.

`ENABLED`
:   Specify if the index rate configuration is enabled (`true`) or disabled (`false`).

`CHANNELS`
:   Can be `email` or `pagerduty`.  If `email` then specify a comma-separated list of email addresses.  For example, `{"email":["emailaddress@company.com"]}`.  If `pagerduty` specify the PagerDuty key.

`THRESHOLD_ALERT`
:   Is tetermines if you want alerts to be triggered if both the max lines and standard deviation have been triggered, or if one of the thresholds has been reached.  Valid values are `separate` and `both`.

`FREQUENCY`
:   Determines if recipients are notified once per hour, or once per day, (starting when the threshold is passed the first time) until the index rate drops below the thresholds. When the index rate drops below the thresholds, alerting stops.  Valid values are `hourly` and `daily`

### Getting the index rate alert configuration
{: #get_index_rate_api}

You can retrieve your index rate alert configuration by running the following:

```sh
curl -X GET https://<ENDPOINT>/v1/config/index-rate -H 'content-type: application/json'   -H 'servicekey: <SERVICE_KEY>'
```
{: pre}

Where:

`ENDPOINT`
:   Is the [endpoint]/docs/activity-tracker?topic=activity-tracker-endpoints) for your {{site.data.keyword.at_full_notm}} instance.

`SERVICE_KEY`
:   Is the [service key](/docs/activity-tracker?topic=activity-tracker-service_keys) for your {{site.data.keyword.at_full_notm}} instance.

Output similar to the following is returned:

```text
{"max_lines":1,"max_z_score":3,"enabled":true,"channels":{"email":["emailaddress@company.com"]},"threshold_alert":"both","frequency":"hourly"}
```
{: screen}

If no index rate alert is configured, the following is returned:

```text
{"error":"No Index Rate Alert found","code":"NotFound","status":"error"}
```
{: screen}

### Disabling an index rate alert
{: #delete_index_rate_api}

Use the `PUT` REST API command to disable your index rate alerts.  To disable your index rate alert configuration, run the following:

```text
curl -X PUT https://<ENDPOINT>/v1/config/index-rate -H 'content-type: application/json'   -H 'servicekey: <SERVICE_KEY>' -d '{"max_lines":0,"max_z_score":0,"enabled":true,"channels":{"email":[""]},"threshold_alert":"","frequency":""}'
```
{: pre}

Where:

`ENDPOINT`
:   Is the [endpoint]/docs/activity-tracker?topic=activity-tracker-endpoints) for your {{site.data.keyword.at_full_notm}} instance.

`SERVICE_KEY`
:   Is the [service key](/docs/activity-tracker?topic=activity-tracker-service_keys) for your {{site.data.keyword.at_full_notm}} instance.
