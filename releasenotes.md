---

copyright:
  years: 2019, 2022
lastupdated: "2022-05-24"

keywords: IBM Cloud, Activity Tracker, release notes, whats new

subcollection: activity-tracker

content-type: release-note

---

{{site.data.keyword.attribute-definition-list}}

 

# Release notes for {{site.data.keyword.atracker_full_notm}}
{: #activity-tracker-release-notes}

Use these release notes to learn about the latest updates to {{site.data.keyword.atracker_full}}.
{: shortdesc}

## 25 May 2022
{: #activity-tracker-may2522}
{: release-note}

New V2 API support for {{site.data.keyword.atracker_short}} Event Routing including the ability to configure service-to-service authorization for {{site.data.keyword.cos_full_notm}} targets. *({{site.data.keyword.atracker_short}} Event Routing offering)*
:   Highlights of this new support include:

    * You are now able to route your global events to any {{site.data.keyword.atracker_short}} hosted event search region even if {{site.data.keyword.atracker_short}} Event Routing is not present in the region.

    * The {{site.data.keyword.atracker_short}} Event Routing configuration has been moved to be a global configuration so that all route definitions apply to all regions where the feature is present.  This removes the requirement to configure {{site.data.keyword.atracker_short}} Event Routing in each region.  Routing based on location is still possible.

    * {{site.data.keyword.cos_full_notm}} targets support service-to-service authorizations which eliminates the need to manage keys for your {{site.data.keyword.cos_full_notm}} targets.

    * The `setting` feature allows the account to choose the location where the {{site.data.keyword.atracker_short}} Event Routing metadata for their account is stored.

    * The `setting` feature allows the account to choose one or more default targets for routing events.  This removes the requirement to individually define routes in each region if you want to have all events from all regions to flow to a specific target.

    * New `/api/v2` APIs have been introduced to replace the existing V1 APIs.

    * The V1 APIs are now deprecated and will be removed in a future release.

    * For existing {{site.data.keyword.atracker_short}} Event Routing users, you will need to follow a migration process to use the new V2 features.  For customers that have not yet configured a target using {{site.data.keyword.atracker_short}} Event Routing, you will default to V2 and will not require a migration.

{{site.data.keyword.atracker_short}} Event Routing available in Sydney (au-syd) *({{site.data.keyword.atracker_short}} Event Routing offering)*
:   {{site.data.keyword.atracker_short}} Event Routing is now available in the in Sydney (au-syd) region.  [Learn more](/docs/activity-tracker?topic=activity-tracker-regions#regions-atracker).

## 24 March 2022
{: #activity-tracker-mar2422}
{: release-note}

Ability to limit access to private endpoints only *({{site.data.keyword.at_short}} hosted event search offering)*
:   You can limit access to an {{site.data.keyword.at_full}} instance to private endpoints only.    [Learn more](/docs/activity-tracker?topic=activity-tracker-private_endpoints_only).

## 22 March 2022
{: #activity-tracker-mar2222}
{: release-note}

{{site.data.keyword.atracker_short}} Event Routing available in Frankfurt (eu-de) and London (eu-gb) *({{site.data.keyword.atracker_short}} Event Routing offering)*
:   {{site.data.keyword.atracker_short}} Event Routing is now available in the Frankfurt (eu-de) and London (eu-gb) regions.  [Learn more](/docs/activity-tracker?topic=activity-tracker-regions#regions-atracker).

## 31 January 2022
{: #activity-tracker-jan3122}
{: release-note}

Index rate analysis to alert on unexpected data volume spikes *({{site.data.keyword.at_short}} hosted event search offering)*
:   You can configure index rates alerts in your {{site.data.keyword.atracker_short}} instance to monitor and be alerted of unexpected spikes in your data volumes. Use the index rate to analyze and predict costs associated with storage of searchable data.  [Learn more about index rate analysis](/docs/activity-tracker?topic=activity-tracker-control_usage_index_rate).

Managing and limiting data usage *({{site.data.keyword.at_short}} hosted event search offering)*
:   In your {{site.data.keyword.atracker_short}} instance, you can use the usage quota settings to control how much data is stored so you can manage your data cost while still being able to view and retain the data you need.  [Learn more about usage quotas](/docs/activity-tracker?topic=activity-tracker-control_usage_quotas).

## 4 October 2021
{: #activity-tracker-oct0421}
{: release-note}

API for Archiving *({{site.data.keyword.at_short}} hosted event search offering)*
:   Documentation of API changes supporting archiving is generally available.  [Learn more about the archiving API](/apidocs/activity-tracker#get-v1-config-archiving).

## 1 October 2021
{: #activity-tracker-sep3121}
{: release-note}

API for data streaming *({{site.data.keyword.at_short}} hosted event search offering)*
:   Documentation of API changes supporting data streaming is generally available.  [Learn more about the streaming API](/apidocs/activity-tracker#post-v1-config-stream).

## 13 August 2021
{: #activity-tracker-aug1321}
{: release-note}

General availability of {{site.data.keyword.atracker_short}} Event Routing *({{site.data.keyword.atracker_short}} Event Routing offering)*
:   [Learn more about {{site.data.keyword.atracker_short}} Event Routing](/docs/activity-tracker?topic=activity-tracker-getting-started-routing).

Data streaming support *({{site.data.keyword.at_short}} hosted event search offering)*
:   Feature to stream data from an {{site.data.keyword.at_full_notm}} instance to other corporate tools such as Security Information and Event Management (SIEM) tools is generally available. [Learn more about streaming](/docs/activity-tracker?topic=activity-tracker-streaming).

## 2 July 2021
{: #activity-tracker-jul0221}
{: release-note}

Support to stream data is available in beta *({{site.data.keyword.at_short}} hosted event search offering)*
:   New beta feature released in US-South and Frankfurt to stream data from an {{site.data.keyword.at_full_notm}} instance to other corporate tools such as Security Information and Event Management (SIEM) tools. [Learn more about streaming](/docs/activity-tracker?topic=activity-tracker-streaming).

## 31 March 2021
{: #activity-tracker-mar3121}
{: release-note}

New CLI support *({{site.data.keyword.at_short}} hosted event search offering)*
:   New CLI added that can be used to list instances and export data from an instance. [Learn more about the CLI](/docs/cli?topic=log-analysis-cli-plugin-log-analysis-cli).

New API support *({{site.data.keyword.at_short}} hosted event search offering)*
:   New API added that can be used to export data from an instance, and manage views and alerts. [Learn more about the API](https://cloud.ibm.com/apidocs/logdna?code=python#introduction){: external}.

## 31 January 2021
{: #activity-tracker-jan3121}
{: release-note}

Changes to archiving frequency *({{site.data.keyword.at_short}} hosted event search offering)*
:   Hourly archiving in Chennai, Tokyo, Sydney, Seoul, London, Washington instead of daily archiving. [Learn more](/docs/activity-tracker?topic=activity-tracker-manage_events#manage_events_archive).

## 31 December 2020
{: #activity-tracker-dec3120}
{: release-note}

Addition of configuration support using an API *({{site.data.keyword.at_short}} hosted event search offering)*
:   Configuration support using an API, in addition to configuration using the web UI. [Learn more](/docs/activity-tracker?topic=activity-tracker-config-api).

Terraform support *({{site.data.keyword.at_short}} hosted event search offering)*
:   Support for Terraform to programmatically manage {{site.data.keyword.at_full_notm}} views and alerts and automate their deployment. 

## 9 July 2020
{: #activity-tracker-jul0920}
{: release-note}

HIPPA service plans available *({{site.data.keyword.at_short}} hosted event search offering)*
:   Added support for 30-day search plans for HIPAA workloads.

## 19 July 2019
{: #activity-tracker-jul1920}
{: release-note}

Enhanced data residency, compliance, and security *({{site.data.keyword.at_short}} hosted event search offering)*
:   The following support is now available:

    * Services are available in London and Tokyo.
    * Services in Frankfurt are now available as EU-Managed.
    * Cloud Service endpoint support is available in all regions.

## 30 April 2019
{: #activity-tracker-apr3019}
{: release-note}

Introducing {{site.data.keyword.at_full_notm}} *({{site.data.keyword.at_short}} hosted event search offering)*
:   Use the {{site.data.keyword.at_full_notm}} service to capture a record of your {{site.data.keyword.cloud_notm}} activities and monitor the activity of your {{site.data.keyword.cloud_notm}} account. You can use this service to investigate abnormal activity and critical actions, and comply with regulatory audit requirements. The events that are collected comply with the Cloud Auditing Data Federation (CADF) standard.


