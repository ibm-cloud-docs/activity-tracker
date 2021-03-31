---

copyright:
  years: 2019, 2021
lastupdated: "2021-03-29"

keywords: IBM Cloud, Activity Tracker, IAM events

subcollection: Activity-Tracker-with-LogDNA

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
{:external: target="_blank" .external}



# Auditing events for DB2 Warehouse
{: #at_events_dashdb}

As a security officer, auditor, or manager, you can use the {{site.data.keyword.at_full_notm}} service to track how users and applications interact with the {{site.data.keyword.dashdblong}} service in {{site.data.keyword.cloud_notm}}. 
{:shortdesc}

You can provision an instance of {{site.data.keyword.dashdblong}} through the [{{site.data.keyword.Bluemix_notm}} catalog](https://cloud.ibm.com/catalog/db2-warehouse){: external}. [Learn more](/docs/account?topic=account-iamoverview).


The {{site.data.keyword.at_full_notm}} service records user-initiated activities that change the state of a service in {{site.data.keyword.cloud_notm}}. To get started monitoring your user's actions, see [{{site.data.keyword.at_full_notm}}](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-getting-started#getting-started). An initiator can be a user, a service, or an application.


## Platform events
{: #at_events_dashdb_platform}

The following table lists the actions that generate an event:

| Action                                   | Description |
|------------------------------------------|---------|
| `dashdb.instance.create`           | An event is generated when you provision a service instance. |
| `dashdb.instance.update`           | An event is generated when you rename a service instance or when you change the service plan. |
| `dashdb.instance.delete`           | An event is generated when a service instance is deleted. |
| `dashdb.instance.schedule_reclaim` | An event is generated when a service instance is pending_reclamation. |
| `dashdb.instance.restore`          | An event is generated when a service instance is restored. |
{: caption="Table 1. Actions that generate platform events" caption-side="top"}  
 
The following table lists the actions that generate an event for managing service credentials that are associated to a service instance:

| Action                         | Description |
|--------------------------------|---------|
| `service_name.key.create` | An event is generated when an API key is created for a service instance through the *Service credentials* section of the service instance UI. |
| `service_name.key.delete` | An event is generated when an API key that is associated with a service instance is deleted from the *Service credentials* section of the service instance UI. |
{: caption="Table 2. Actions that generate service credentials events" caption-side="top"} 


## Viewing events
{: #at_events_iam_ui}

Events are available in the **Frankfurt (eu-de)** region. 

To view these events, you must [provision an instance](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-provision#provision) of the {{site.data.keyword.at_full_notm}} service in the **Frankfurt (eu-de)** region. Then, you must [open the {{site.data.keyword.at_full_notm}} UI](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-launch#launch_cloud_ui). 
