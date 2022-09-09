---

copyright:
  years: 2019, 2022
lastupdated: "2022-05-23"

keywords: IBM Cloud, Activity Tracker, events, global, regional, data, management

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}


# Collecting events
{: #events_collect}

In {{site.data.keyword.at_full}}, events are collected automatically for most {{site.data.keyword.atracker_short}}-enabled services. However, some services might require an upgrade of the service plan, a configuration setting, or both, for you to be able to collect and analyze their events.
{: shortdesc}

To collect and monitor activity in your account, you must configure the {{site.data.keyword.atracker_short}} service in your account by using any of the following methods:

- You can [configure {{site.data.keyword.atracker_short}}](/docs/activity-tracker?topic=activity-tracker-getting-started-routing-2) to manage auditing events in your account while maintaining Financial Services Validated status.

    The target resource must be an {{site.data.keyword.cos_full}} bucket that is available in the same account where the auditing events are generated.

    You can also use a bucket that is available in a different account from where auditing events are generated.

    You must follow and comply with the Financial Services Validated requirements for buckets to maintain Financial Services Validated status.
    {: important}

- You can [configure the {{site.data.keyword.atracker_short}} hosted event search offering](/docs/activity-tracker?topic=activity-tracker-getting-started-search) to manage auditing events through the UI, or if you need PCI, SOC2, Privacy Shield or HIPAA compliance.

- You can configure {{site.data.keyword.atracker_short}} to define the {{site.data.keyword.atracker_short}} hosted event search instances where auditing events are routed.

    The {{site.data.keyword.atracker_short}} hosted event search instances can be located in the same account where auditing events are generated or in a different account.


In {{site.data.keyword.atracker_short}}, you can differentiate events by scope as global or location-based events, and by operational impact as either management or data events.

- The scope is determined from where an event is collected.

- Collection of management events is automatic for {{site.data.keyword.atracker_short}}-enabled services, except for Watson services which require a paid plan.

- Collection of data events is also automatic with the exception of some services where you must opt-in to collect those events. To opt-in, you might need to configure the service, upgrade the service plan, or both. For more information, see [Data events](/docs/activity-tracker?topic=activity-tracker-event_types#event_types_data).


{{site.data.keyword.atracker_short}} hosted event search routes location-based auditing events to an {{site.data.keyword.atracker_short}} instance in the region where they are generated and routes global auditing events to the {{site.data.keyword.atracker_short}} instance that is provisioned in Frankfurt.

{{site.data.keyword.atracker_short}} routes events based on the location that is specified in the `logSourceCRN` field included in the event. You can define a target, the resource where events are routed to, in any {{site.data.keyword.atracker_short}} supported region. However, the target resource can be located in any region where that type of target is supported, in the same account or in a different account. You can define rules to determine where auditing events are to be routed by configuring 1 or more routes in the account. You can define rules for managing global events and location-based events that are generated in regions where {{site.data.keyword.atracker_short}} is supported. 


## Collecting global events
{: #events_collect_global}

You can choose 1 of the following options to collect [global events](/docs/activity-tracker?topic=activity-tracker-event_types#event_types_global) in your account:

1. Configure {{site.data.keyword.atracker_short}}: You can choose the region where events are collected. [Learn more](/docs/activity-tracker?topic=activity-tracker-getting-started-routing-2#getting-started-routing-step6).

2. Configure {{site.data.keyword.at_short}} hosted event search: Global events are available through the {{site.data.keyword.atracker_short}} instance in Frankfurt. To collect and view global events, you must provision an instance of the {{site.data.keyword.at_short}} service in Frankfurt. [Learn more](/docs/activity-tracker?topic=activity-tracker-monitor_events).

3. While global events default to Frankfurt when you configure {{site.data.keyword.at_short}} hosted event search to manage auditing events, you can configure {{site.data.keyword.atracker_short}}  to manage routing of global events to the instance of your choice.  

    Routing can be to an {{site.data.keyword.at_short}} hosted event search instance so that you can monitor events through the UI or to an {{site.data.keyword.cos_full_notm}} bucket for archival purposes. [Learn more](/docs/activity-tracker?topic=activity-tracker-getting-started-target-1).

    Routing can be done to an instance within the account that generates the auditing events, or to an instance in another {{site.data.keyword.cloud_notm}} account.


## Collecting location-based events
{: #events_collect_location}

You can choose 1 of the following options to collect [location-based events](/docs/activity-tracker?topic=activity-tracker-event_types#event_types_location) in your account:

1. Configure {{site.data.keyword.atracker_short}}: You can choose the region where location-based events are collected. [Learn more](/docs/activity-tracker?topic=activity-tracker-atracker-resources).

2. Configure {{site.data.keyword.at_short}} hosted event search: Location-based events are available through the {{site.data.keyword.at_short}} instance that is available in the same region as the service. [Learn more](/docs/activity-tracker?topic=activity-tracker-monitor_events).

3. Configure {{site.data.keyword.atracker_short}} to manage routing of location-based events to the instance of your choice.  

    Routing can be to an {{site.data.keyword.at_short}} hosted event search instance to monitor events using the UI or to an {{site.data.keyword.cos_full_notm}} bucket for archival purposes. [Learn more](/docs/activity-tracker?topic=activity-tracker-getting-started-target-1).

    Routing can be done to an instance within the account, or to an instance in another {{site.data.keyword.cloud_notm}} account.

    Routing of location-based events from a given region is only supported for the regions where {{site.data.keyword.atracker_short}} is supported. For more information about supported regions, see [Locations](/docs/activity-tracker?topic=activity-tracker-regions&interface=cli#regions-atracker).


The following are exceptions for location-based events:

* The {{site.data.keyword.at_full_notm}} service might not be available in a region where a service is provisioned. [Learn more about supported locations](/docs/activity-tracker?topic=activity-tracker-regions).

    Check the [Cloud services by location](/docs/activity-tracker?topic=activity-tracker-cloud_services_locations) documentation to find out if the service generates {{site.data.keyword.atracker_short}} events in that region, and if it does, where the events are available for analysis.

* The service might not generate {{site.data.keyword.atracker_short}} events in the region where you have provisioned your {{site.data.keyword.atracker_short}} instance.

    Check the [Cloud services by location](/docs/activity-tracker?topic=activity-tracker-cloud_services_locations) documentation to confirm if events are available in that region.




