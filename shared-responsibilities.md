---

copyright:
  years: 2018, 2020
lastupdated: "2020-11-12"

keywords: IBM Cloud, LogDNA, Activity Tracker, auditing, customer responsibilities, IBM responsibilities, terms and conditions

subcollection: Activity-Tracker-with-LogDNA


---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:codeblock: .codeblock}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:download: .download}
{:preview: .preview}

# Understanding your responsibilities when using {{site.data.keyword.at_full_notm}}
{: #shared-responsibilities}

Learn about the management responsibilities and terms and conditions that you have when you use {{site.data.keyword.at_full_notm}}. For a high-level view of the service types in {{site.data.keyword.cloud_notm}} and the breakdown of responsibilities between the customer and {{site.data.keyword.IBM_notm}} for each type, see [Shared responsibilities for {{site.data.keyword.cloud_notm}} offerings](/docs/overview?topic=overview-shared-responsibilities).
{:shortdesc}

Review the following sections for the specific responsibilities for you and for {{site.data.keyword.IBM_notm}} when you use {{site.data.keyword.at_full_notm}}. For the overall terms of use, see [{{site.data.keyword.cloud_notm}} Terms and Notices](/docs/overview/terms-of-use?topic=overview-terms).

  
## Incident and operations management
{: #incident-and-ops}


| Task              | {{site.data.keyword.IBM_notm}} Responsibilities | Your Responsibilities |
|-------------------|-------------------------------------------------|-----------------------|
| `Incident and operations management` | Maintain {{site.data.keyword.la_full_notm}} service instances and infrastructure workloads. | Maintain incident and operations management of your data. |
| `Monitor incidents`  | Provide notifications for planned maintenance, security bulletins, or unplanned outages. | Set preferences to [receive emails about platform notifications](/docs/overview?topic=overview-ui#email-prefsl). </br>Monitor the [IBM Cloud status page](https://{DomainName}/status?selected=announcement) for general announcements. |
| `Maintain {{site.data.keyword.cloud_notm}} high availability SLA`   | Provide Cloud Service across availability zones in a Multi-Zone Region (MZR). </br> Provide Cloud Service across hosts in a Single-Zone Region (SZR). </br>Provides replication, fail-over features, and infrastructure maintenance and updates. | Use the list of available regions to plan for and create new instances of the service. |
| `Archive events`  | Provide the ablity to archive to a client configured Cloud Object Storage (COS) location and archive data hourly or daily. | Configure Cloud Object Storage per your requirements. </br>[Enable archiving of the Activity Tracker instance.](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-archiving) |
| `Monitor events`  | [Participating Cloud services](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-cloud_services) publish relevant event data to their subscribing clients. {{site.data.keyword.at_full_notm}} provides clients with the ability to receive the events once the client configures their instance. | [Create an {{site.data.keyword.at_full_notm}} instance](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-provision) in each region where Cloud service subscriptions publish events to receive the published events. </br>Create an instance in Frankfurt to get global Activity Tracker events. </br>[Create views, dashboards, and screens to view and analyze the data.](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-monitor_events)|
{: caption="Table 1. Responsibilities for incident and operations" caption-side="top"}



## Change management
{: #change-management}


| Task                                                    | {{site.data.keyword.IBM_notm}} Responsibilities | Your Responsibilities |
|---------------------------------------------------------|-----------------------|--------|
| `Update the {{site.data.keyword.at_full_notm}} service` | Provide major, minor, and patch version updates for {{site.data.keyword.at_full_notm}} interfaces. </br>Document changes in the [LogDNA release notes](https://logdna.zendesk.com/hc/en-us/categories/360001626492-Release-Notes) | `N/A` | 
| `Track versions of custom views, dashboards, screens, parsing templates, and alerts`    | `N/A` | Use your own change management process to control versions of metadata resources such as views, dashboards, screens, parsing templates, and alerts`. </br>To learn how to export metadata, see [Export the configuration of resources in a LogDNA instance](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-reuse_resource_definitions#rrd_export_config). | 
{: caption="Table 2. Responsibilities for change management" caption-side="top"}


## Identity and access management
{: #iam-responsibilities}


| Task                           | {{site.data.keyword.IBM_notm}} Responsibilities | Your Responsibilities |
|--------------------------------|-------------------------------------------------|-----------------------|
| `Manage permissions`           |Provide the ability to restrict access to resouces. </br>{{site.data.keyword.IBM_notm}} is responsible for the security and compliance of {{site.data.keyword.la_full_notm}}. | Restrict access to resources by using Cloud IAM access policies by defining IAM policies to control which users within your account have access to the data.  </br>[Learn more about controlling access through IAM](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-iam).| 
{: caption="Table 3. Responsibilities for identity and access management" caption-side="top"}




## Security and regulation compliance
{: #security-compliance}


| Task                                       | {{site.data.keyword.IBM_notm}} Responsibilities | Your Responsibilities |
|--------------------------------------------|-------------------------------------------------|-----------------------|
| `Encrypt data`  | Operate the Cloud Service encrypting data in motion and at rest per compliance specifications. | Ensure encryption of archived data by configuring a COS bucket that has full control over the data encryption keys that are used. [{{site.data.keyword.cos_full}} provides several options to encrypt your data.](/docs/cloud-object-storage?topic=cloud-object-storage-encryption) |
| `Meet security and compliance objectives`  | Maintain controls that are commensurate to various industry compliance standards such as SOC2, PCI, HIPAA and Privacy Shield. | Set up and maintain security and regulation compliance for your apps and data.  This includes: </br>[Defining the account management strategy](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-adoption#adoption_account) </br>[Configuring the accounts settings for compliance](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-adoption#adoption_acc_settings) </br>[Define IAM Strategy](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-adoption#adoption_iam) </br>[Define the notification strategy](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-adoption#adoption_alerts) |
{: caption="Table 4. Responsibilities for security and regulation compliance" caption-side="top"}



## Disaster recovery
{: #disaster-recovery}


| Task                                                            | {{site.data.keyword.IBM_notm}} Responsibilities | Your Responsibilities |
|-----------------------------------------------------------------|-------------------------------------------------|-----------------------|
| `Restore the service` `[*]`      |Automatically recover and restart service components after any disaster event.  | `N/A` |
| `Backup the {{site.data.keyword.at_full_notm}} key resources that are provided by the service`        | Daily backup of the {{site.data.keyword.at_full_notm}} infrastructure and components. | `N/A` |
| `Backup the metadata of a LogDNA instance`                          | `N/A` | [Backup the metadata such as views, dashboards, screens, parsing templates, and alerts for each LogDNA instance.](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-reuse_resource_definitions#rrd_export_config) |
| `Restore the metadata of a LogDNA instance`                         | `N/A` | [Restore the metadata such as views, dashboards, screens, parsing templates, and alerts for each LogDNA instance.](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-reuse_resource_definitions#import_config) |
| `Backup of the data` | `N/A` | [Configure archiving to retain a backup copy of the data.](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-archiving) |
{: caption="Table 5. Responsibilities for disaster recovery" caption-side="top"}

`[*]` Recovered and restarted service components will not have customer data reloaded.
{: note}

