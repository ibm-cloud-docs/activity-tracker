---

copyright:
  years:  2018, 2020
lastupdated: "2020-03-25"

keywords: IBM Cloud, LogDNA, Activity Tracker, auditing, overview, personal data, data deletion, PHI, data, data security, _service-name_

subcollection: Activity-Tracker-with-LogDNA


---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}


# Securing your data
{: #mng-data}

To ensure that you can securely manage your data when you use {{site.data.keyword.at_full_notm}}, it is important to know exactly what data is stored and encrypted, and how you can delete any stored personal data.
{: shortdesc}


## How your data is collected in {{site.data.keyword.at_full_notm}}
{: #data-collection}

Data from [{{site.data.keyword.cloud_notm}} services and resources](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-cloud_services) is collected automatically and available for analysis through the web UI. 

{{site.data.keyword.at_full_notm}} collects management and data events from {{site.data.keyword.cloud_notm}} services and resources: 
* **Management Events** are generated when an API call changes the state of a Cloud resource. A resource might be an entire service instance or a resource managed by the service. 
* **Data Events** are generated when an API call reads or modifies a resource's data. 




## How your data is stored in {{site.data.keyword.at_full_notm}}
{: #data-storage}

{{site.data.keyword.at_full_notm}} collects and aggregates logs. 

### Data location
{: #data-storage_location}

Data is hosted on the {{site.data.keyword.cloud_notm}}. The {{site.data.keyword.at_full_notm}} service is operated by LogDNA.

Events can be classified as global or location-based. [Learn more](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-event_types).
* **Location-based events** maintain data locality to the services that run in that Cloud location.
* **Global events** are collected and made available through the {{site.data.keyword.at_full_notm}} instance that is configured in Frankfurt.


### Data encryption
{: #data-storage_encryption}

All the data that is hosted in a LogDNA instance is encrypted at rest using **AES 256**.

When an {{site.data.keyword.cloud_notm}} service sends data to a LogDNA instance, data is encrypted in transit over HTTPS.

When a user requests an export, the data is encrypted during transit, and is also encrypted at rest in {{site.data.keyword.cos_full_notm}} (COS).


## Data retention for search
{: #data_retention}

The service plan that you choose for an {{site.data.keyword.at_full_notm}} instance defines the number of days that data is stored and retained in LogDNA. 

For example, if you choose the *Lite* plan, data is not stored at all. However, if you choose the 7-day plan, data is stored for 7 days and you have access to it through the LogDNA Web UI.



## Data archives
{: #data_archives}

You can archive events from an {{site.data.keyword.at_full_notm}} instance into a bucket in an {{site.data.keyword.cos_full_notm}} (COS) instance. [Learn more](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-archiving).

When data is archived, data going from LogDNA to {{site.data.keyword.cos_full_notm}} (COS) is encrypted in transit over HTTPS.

You must configure archiving to a COS instance if you want to backup your events for long term storage.

You can use the {{site.data.keyword.sqlquery_short}} service to query data in archive files that are stored in an {{site.data.keyword.cos_short}} (COS) bucket in your account. You can run queries from the {{site.data.keyword.cloud_notm}} UI, or programmatically.

## Data exports
{: #data_exports}

You can export data in JSONL format locally, write data to your terminal, or request an email with a link to the data. [Learn more](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-export).

Consider the following information when you export log data:
* You export a set of event entries. To define the set of data that you want to export, you can apply filter and searches. You can also specify the time range. 
* From the Web UI, when you export events, you get an email that is sent to your email address, with a link to a compressed file that includes the data. To get the data, you must click the link and download the compressed file. Notice that the link expires automatically after 12 hours. The compressed file is hosted in {{site.data.keyword.cos_full_notm}} (COS).
* When you export events programmatically, you can choose to send an email, or to write to the terminal.
* When you export data, you have a limit of lines that you can export in a request. You can specify to export older lines or newer lines in case you reach the limit in the time range that you specify for the export.


## Deleting your data
{: #data-delete}

### Deleting events when an instance is deleted
{: #service-delete-logs}

When you delete a LogDNA instance, the instance is automatically deactivated, and ingestion of events is stopped. [Learn more](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-remove).

LogDNA deletes all events that are already ingested. Deletion is completed within 24 hours after receiving your request.

You are responsible for managing archived data. 

### Deleting user metadata when an instance is deleted
{: #service-delete-metadata}

When you delete a LogDNA instance, user metadata such as views, alerts, dashboards, screens, and templates, is never deleted. 

You must open a case through support to request the data to be deleted. For more information, see [Open a support ticket](/docs/get-support?topic=get-support-getting-customer-support#getting-customer-support).

You are responsible for deleting archived metadata. 

### Deleting metadata from an instance
{: #service-delete-metadata1}

You can delete metadata such as views, dashboards, screens, templates, and alerts at any time.


### Deleting a subset of the data from an instance
{: #service-delete-service}

Deletion of a subset of your data is not supported. 

For example, you cannot delete data for a specific service. You cannot delete data that match a particular query.

