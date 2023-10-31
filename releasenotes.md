---

copyright:
  years: 2019, 2023
lastupdated: "2023-10-31"

keywords:

subcollection: activity-tracker

content-type: release-note

---

{{site.data.keyword.attribute-definition-list}}



# Release notes for {{site.data.keyword.at_full_notm}} hosted event search
{: #activity-tracker-release-notes}

Use these release notes to learn about the latest updates to {{site.data.keyword.at_full}} hosted event search.
{: shortdesc}

## 31 October 2023
{: #activity-tracker-oct3123}
{: release-note}
 
Services now sending events to Madrid
:   Some services are now sending events to Madrid. See [services generating events by location](/docs/activity-tracker?topic=activity-tracker-cloud_services_locations) for the services sending events to Madrid.

## 26 September 2023
{: #activity-tracker-sep2623}
{: release-note}
 
Madrid region support
:   Madrid is now an online region for {{site.data.keyword.at_full}} hosted event search. Services can now be provisioned in Madrid and Madrid endpoints can be used. Platform metrics will continue flowing to the Frankfurt region.

## 24 July 2023
{: #activity-tracker-jul2423}
{: release-note}

CIDR block deprecated in Frankfurt
:   A CIDR block has been deprecated in Frankfurt. You should remove deprecated CIDR blocks from any configured allowlists. See [CIDR blocks](/docs/activity-tracker?topic=activity-tracker-cidr) for more information.

## 27 June 2023
{: #activity-tracker-jun2723}
{: release-note}

CIDR block deprecated in Frankfurt
:   A CIDR block has been deprecated in Frankfurt. You should remove deprecated CIDR blocks from any configured allowlists. See [CIDR blocks](/docs/activity-tracker?topic=activity-tracker-cidr) for more information.

## 8 June 2023
{: #activity-tracker-jun0823}
{: release-note}

CIDR blocks deprecated in London and Toronto
:   Some CIDR blocks have been deprecated in London and Toronto. You should remove deprecated CIDR blocks from any configured allowlists. See [CIDR blocks](/docs/activity-tracker?topic=activity-tracker-cidr) for more information.

## 25 April 2023
{: #activity-tracker-apr2523}
{: release-note}

New private CIDR blocks available for Toronto
:   New private CIDR blocks will be available on 10 May 2023 for Toronto. See [CIDR blocks](/docs/activity-tracker?topic=activity-tracker-cidr) for more information.

## 22 February 2023
{: #activity-tracker-feb2223}
{: release-note}

New CIDR blocks available
:   New CIDR blocks will be available on 9 March 2023. See [CIDR blocks](/docs/activity-tracker?topic=activity-tracker-cidr) for more information.

## 13 February 2023
{: #activity-tracker-feb1323}
{: release-note}

New API method to retrieve account usage totals
:   A [new method](/apidocs/activity-tracker#list-usage-v2) is available to get aggregate data usage information for an account during a specified time period.

## 10 January 2023
{: #activity-tracker-jan1023}
{: release-note}

Webhook alerts are enabled for Index Rate alerting.
:   For more information, see [Activate the index rate alert feature](/docs/activity-tracker?topic=activity-tracker-control_usage_index_rate&interface=ui#control_usage_index_rate_activate).

## 18 November 2022
{: #activity-tracker-nov1822}
{: release-note}

New documentation locations for {{site.data.keyword.atracker_short}} and {{site.data.keyword.at_short}} hosted event search
:   There are now two different locations for {{site.data.keyword.at_short}} documentation depending on your use case.

    * For {{site.data.keyword.atracker_short}}, see the [{{site.data.keyword.atracker_short}} documentation.](/docs/atracker)

    * For {{site.data.keyword.at_short}} hosted event search, see the [{{site.data.keyword.at_short}} hosted event search documentation.](/docs/activity-tracker?topic=activity-tracker-getting-started)

## 24 March 2022
{: #activity-tracker-mar2422}
{: release-note}

Ability to limit access to private endpoints only
:   You can limit access to an {{site.data.keyword.at_full}} instance to private endpoints only.    [Learn more](/docs/activity-tracker?topic=activity-tracker-private_endpoints_only).


## 31 January 2022
{: #activity-tracker-jan3122}
{: release-note}

Index rate analysis to alert on unexpected data volume spikes
:   You can configure index rates alerts in your {{site.data.keyword.at_short}} instance to monitor and be alerted of unexpected spikes in your data volumes. Use the index rate to analyze and predict costs associated with storage of searchable data.  [Learn more about index rate analysis](/docs/activity-tracker?topic=activity-tracker-control_usage_index_rate).

Managing and limiting data usage
:   In your {{site.data.keyword.at_short}} instance, you can use the usage quota settings to control how much data is stored so you can manage your data cost while still being able to view and retain the data you need.  [Learn more about usage quotas](/docs/activity-tracker?topic=activity-tracker-control_usage_quotas).

## 4 October 2021
{: #activity-tracker-oct0421}
{: release-note}

API for Archiving
:   Documentation of API changes supporting archiving is generally available.  [Learn more about the archiving API](/apidocs/activity-tracker#get-v1-config-archiving).

## 1 October 2021
{: #activity-tracker-sep3121}
{: release-note}

API for data streaming
:   Documentation of API changes supporting data streaming is generally available.  [Learn more about the streaming API](/apidocs/activity-tracker#post-v1-config-stream).

## 13 August 2021
{: #activity-tracker-aug1321}
{: release-note}

Data streaming support
:   Feature to stream data from an {{site.data.keyword.at_full_notm}} instance to other corporate tools such as Security Information and Event Management (SIEM) tools is generally available. [Learn more about streaming](/docs/activity-tracker?topic=activity-tracker-streaming).

## 2 July 2021
{: #activity-tracker-jul0221}
{: release-note}

Support to stream data is available in beta
:   New beta feature released in US-South and Frankfurt to stream data from an {{site.data.keyword.at_full_notm}} instance to other corporate tools such as Security Information and Event Management (SIEM) tools. [Learn more about streaming](/docs/activity-tracker?topic=activity-tracker-streaming).

## 31 March 2021
{: #activity-tracker-mar3121}
{: release-note}

New CLI support
:   New CLI added that can be used to list instances and export data from an instance. [Learn more about the CLI](/docs/cli?topic=log-analysis-cli-plugin-log-analysis-cli).

New API support
:   New API added that can be used to export data from an instance, and manage views and alerts. [Learn more about the API](https://cloud.ibm.com/apidocs/logdna?code=python#introduction){: external}.

## 31 January 2021
{: #activity-tracker-jan3121}
{: release-note}

Changes to archiving frequency
:   Hourly archiving in Chennai, Tokyo, Sydney, Seoul, London, Washington instead of daily archiving. [Learn more](/docs/activity-tracker?topic=activity-tracker-manage_events#manage_events_archive).

## 31 December 2020
{: #activity-tracker-dec3120}
{: release-note}

Addition of configuration support using an API
:   Configuration support using an API, in addition to configuration using the web UI. [Learn more](/docs/activity-tracker?topic=activity-tracker-config-api).

Terraform support
:   Support for Terraform to programmatically manage {{site.data.keyword.at_full_notm}} views and alerts and automate their deployment.

## 9 July 2020
{: #activity-tracker-jul0920}
{: release-note}

HIPPA service plans available
:   Added support for 30-day search plans for HIPAA workloads.

## 19 July 2019
{: #activity-tracker-jul1920}
{: release-note}

Enhanced data residency, compliance, and security
:   The following support is now available:

    * Services are available in London and Tokyo.
    * Services in Frankfurt are now available as EU-Managed.
    * Cloud Service endpoint support is available in all regions.

## 30 April 2019
{: #activity-tracker-apr3019}
{: release-note}

Introducing {{site.data.keyword.at_full_notm}}
:   Use the {{site.data.keyword.at_full_notm}} service to capture a record of your {{site.data.keyword.cloud_notm}} activities and monitor the activity of your {{site.data.keyword.cloud_notm}} account. You can use this service to investigate abnormal activity and critical actions, and comply with regulatory audit requirements. The events that are collected comply with the Cloud Auditing Data Federation (CADF) standard.
