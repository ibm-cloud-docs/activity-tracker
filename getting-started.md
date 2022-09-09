---

copyright:
  years: 2019, 2022
lastupdated: "2022-05-16"

keywords: IBM Cloud, Activity Tracker, getting started, auditing

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}
 

# Getting started with {{site.data.keyword.atracker_full_notm}}
{: #getting-started}

Use the {{site.data.keyword.atracker_short}} service to capture a record of your {{site.data.keyword.cloud_notm}} activities and monitor the activity of your {{site.data.keyword.cloud_notm}} account. You can use this service to investigate abnormal activity and critical actions, and comply with regulatory audit requirements. The events that are collected comply with the Cloud Auditing Data Federation (CADF) standard.
{: shortdesc}

For more information about {{site.data.keyword.atracker_full_notm}}, see [About {{site.data.keyword.atracker_short}}](/docs/activity-tracker?topic=activity-tracker-about).

{{site.data.keyword.cloud_notm}} administrators can configure an {{site.data.keyword.cloud_notm}} account to collect auditing events automatically for most enabled-services. However, some services might require an upgrade of the service plan, a configuration setting, or both, for you to be able to collect and analyze auditing events due to the high volumes of data that they generate. [Learn more about enabling Activity Tracker events](/docs/activity-tracker?topic=activity-tracker-events-opt-in).

For information on the services that are sending events to {{site.data.keyword.atracker_short}}, see [{{site.data.keyword.cloud_notm}} services that generate {{site.data.keyword.atracker_short}} events](/docs/activity-tracker?topic=activity-tracker-cloud_services).

Depending on your compliance and organizational requirements, you can choose {{site.data.keyword.atracker_full_notm}}  or an {{site.data.keyword.at_full_notm}} hosted event search offering.
- Application environments seeking to maintain Financial Services (FS) validation status on {{site.data.keyword.cloud_notm}} should use {{site.data.keyword.atracker_full_notm}} . 
- Application environments seeking compliance with PCI, SOC2, Privacy Shield and HIPAA should use an {{site.data.keyword.at_full_notm}} hosted event search offering.

[![Getting started with Event Routing](/images/getting_started_routing.svg)](/docs/activity-tracker?topic=activity-tracker-getting-started-routing-2) [![Getting started with hosted event and search offerings](/images/getting_started_event.svg)](/docs/activity-tracker?topic=activity-tracker-getting-started-search)


