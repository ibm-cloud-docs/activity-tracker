---

copyright:
  years: 2022
lastupdated: "2022-05-16"

keywords: IBM Cloud, Activity Tracker, security, auditing, target, logdna

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}


# Planning for the {{site.data.keyword.atracker_short}} account configuration
{: #atracker-resources-planning}

You must plan and decide how the account's {{site.data.keyword.atracker_short}} configuration is managed and stored.
{: shortdesc}


This information applies only if you use {{site.data.keyword.atracker_full}}.
{: important}



## Metadata location
{: #atracker-resources-planning-1}

Decide the location in your {{site.data.keyword.cloud_notm}} account where the {{site.data.keyword.atracker_short}} account configuration metadata is stored. 

You can choose any of the supported locations where {{site.data.keyword.atracker_short}} is available. For more information, see [Locations](/docs/activity-tracker?topic=activity-tracker-regions&interface=cli).

Take into account any corporate or industry compliance requirements such as Financial Services Validated locations, or EU-managed regions.

## Endpoints allowed
{: #atracker-resources-planning-2}

Decide whether public endpoints, private endpoints, or both are allowed to manage the {{site.data.keyword.atracker_short}} account configuration. For more information, see [Enforcing private endpoints to configure {{site.data.keyword.atracker_short}} resources](/docs/activity-tracker?topic=activity-tracker-getting-started-mng-endpoints).


## Target locations
{: #atracker-resources-planning-3}

Define the locations where an account administrator can configure targets to collect auditing events. You can choose any of the supported locations where {{site.data.keyword.atracker_short}} is available. For more information, see [Locations](/docs/activity-tracker?topic=activity-tracker-regions&interface=cli).
    
Take into account any corporate or industry compliance requirements such as Financial Services Validated locations, or EU-managed regions.

The location of a target definition must be a supported location where {{site.data.keyword.atracker_short}} is available. The target can configure a resource in the same account where the events are located or in a different account. In addition, the resource can be located in any region where that type of resource is supported in {{site.data.keyword.cloud_notm}}.

## Default targets
{: #atracker-resources-planning-4}

Define 1 or more default targets in the account to define where auditing events that are not explicitly managed in the account's routing rules are collected.

If you define more than 1 default target, all default targets get a copy of an auditing event that does not have a clearly defined routing rule to indicate where to route events in the account. You can define up to 2 default targets per account.
{: note}

You must create the targets in the account before you can configure them in the account as default ones.


## Number and location of targets
{: #atracker-resources-planning-5}

Define the targets where you plan to collect auditing events based on your regulatory and corporate requirements.

- You can have 1 target per region to collect auditing events for that region. Use this option to reduce latency and network connectivity issues.

- You can have 1 target to collect auditing events across the entire account.

- You can define targets within the account or in a different account.

For more information, see [Targets](/docs/activity-tracker?topic=activity-tracker-atracker-resources#atracker-resources-targets).


## Routing rules in the account
{: #atracker-resources-planning-6}


Define the routing rules that indicate how to route events in your account.

- Routes are global. 

- You can define up to 4 routes per account.
    
- You can define 1 or more routes to configure how auditing events across all regions in your account are collected and stored in 1 or more targets.
    
- For each route that you define, you can configure 4 rules. These rules are applied top down. When a rule is identified for a region, any follow up rules withing that route definition that apply to that region are not considered.

 -To drop the collection of auditing events in 1 or more regions, you can configure a route for those regions with no targets defined.

For more information, see [Routes](/docs/activity-tracker?topic=activity-tracker-atracker-resources#atracker-resources-routes).

 
## Next
{: #atracker-resources-planning-next}

Next, [check samples of different scenarios](/docs/activity-tracker?topic=activity-tracker-atracker-scenarios). 


