---

copyright:
  years: 2019, 2024
lastupdated: "2024-03-27"

keywords:

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}


# Collecting events
{: #events_collect}

In {{site.data.keyword.at_full}}, events are collected automatically for most {{site.data.keyword.at_short}}-enabled services. However, some services might require an upgrade of the service plan, a configuration setting, or both, for you to be able to collect and analyze their events.
{: shortdesc}

<!-- Common deprecation statement -->
{{../log-analysis/_include-segments/deprecation_notice.md}}

{{site.data.keyword.at_short}} routes location-based auditing events to an {{site.data.keyword.at_short}} instance in the region where they are generated and routes global auditing events to the {{site.data.keyword.at_short}} instance that is provisioned in Frankfurt.
{: note}

To collect and monitor activity in your account, you must configure the {{site.data.keyword.at_short}} service in your account.

In {{site.data.keyword.at_short}}, you can differentiate events by scope as global or location-based events, and by operational impact as either management or data events.

- The scope is determined from where an event is collected.

- Collection of management events is automatic for {{site.data.keyword.at_short}}-enabled services, except for Watson services which require a paid plan.

- Collection of data events is also automatic with the exception of some services where you must opt-in to collect those events. To opt-in, you might need to configure the service, upgrade the service plan, or both. For more information, see [Data events](/docs/activity-tracker?topic=activity-tracker-event_types#event_types_data).



## Collecting global events
{: #events_collect_global}

[Global events](/docs/activity-tracker?topic=activity-tracker-event_types#event_types_global) are available through the {{site.data.keyword.at_short}} instance in Frankfurt.

To collect and view global events, you must provision an instance of the {{site.data.keyword.at_short}} service in Frankfurt. [Learn more](/docs/activity-tracker?topic=activity-tracker-monitor_events).



## Collecting location-based events
{: #events_collect_location}

Location-based events are available through the {{site.data.keyword.at_short}} instance that is available in the same region as the service. [Learn more](/docs/activity-tracker?topic=activity-tracker-monitor_events).
