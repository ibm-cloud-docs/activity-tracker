---

copyright:
  years: 2019, 2021
lastupdated: "2021-08-09"

keywords: IBM Cloud, Activity Tracker, auditing, customer responsibilities, IBM responsibilities, terms and conditions

subcollection: activity-tracker


---

{{site.data.keyword.attribute-definition-list}}

# Understanding your responsibilities when using {{site.data.keyword.atracker_full_notm}}
{: #shared-responsibilities}

Learn about the management responsibilities and terms and conditions that you have when you use {{site.data.keyword.atracker_full_notm}}. For a high-level view of the service types in {{site.data.keyword.cloud_notm}} and the breakdown of responsibilities between the customer and {{site.data.keyword.IBM_notm}} for each type, see [Shared responsibilities for {{site.data.keyword.cloud_notm}} offerings](/docs/overview?topic=overview-shared-responsibilities).
{: shortdesc}

Review the following sections for the specific responsibilities for you and for {{site.data.keyword.IBM_notm}} when you use {{site.data.keyword.atracker_full_notm}}. For the overall terms of use, see [{{site.data.keyword.cloud_notm}} Terms and Notices](/docs/overview/terms-of-use?topic=overview-terms).


## Incident and operations management
{: #incident-and-ops}

| Task              | {{site.data.keyword.IBM_notm}} Responsibilities | Your Responsibilities |
|-------------------|-------------------------------------------------|-----------------------|
| `Incident and operations management` | Maintain service instances and infrastructure workloads. | Maintain incident and operations management of your data. |
| `Monitor incidents`  | Provide notifications for planned maintenance, security bulletins, or unplanned outages. | Set preferences to [receive emails about platform notifications](/docs/overview?topic=overview-ui#email-prefsl).   \n Monitor the [IBM Cloud status page](https://{DomainName}/status?selected=announcement) for general announcements. |
| `Maintain {{site.data.keyword.cloud_notm}} high availability SLA for {{site.data.keyword.atracker_short}} event routing`   | Provide {{site.data.keyword.atracker_short}} functionality across availability zones in a Multi-Zone Region (MZR).   \n  Provide {{site.data.keyword.atracker_short}} functionality across hosts in a Single-Zone Region (SZR).   \n Provide replication, fail-over features, and infrastructure maintenance and updates. | Keep your {{site.data.keyword.atracker_short}}  configuration in a version control system so that you can reconfigure a region if needed.   \n Comply with [Operational responsibilities when using {{site.data.keyword.cos_full_notm}}](/docs/cloud-object-storage?topic=cloud-object-storage-responsibilities#responsibilities-operational). |
| `Monitor events for {{site.data.keyword.atracker_short}} event routing`  | [Participating Cloud services](/docs/activity-tracker?topic=activity-tracker-cloud_services) publish relevant event data to their subscribing clients. Clients have the ability to receive this data once their account is configured. | [Configure your account](/docs/activity-tracker?topic=activity-tracker-getting-started) in each region where Cloud service subscriptions publish events to receive the published events. |
| `Maintain {{site.data.keyword.cloud_notm}} high availability SLA for {{site.data.keyword.atracker_short}} hosted event search offerings`   | Provide Cloud Service across availability zones in a Multi-Zone Region (MZR).   \n  Provide Cloud Service across hosts in a Single-Zone Region (SZR).   \n Provides replication, fail-over features, and infrastructure maintenance and updates. | Use the list of available regions to plan for and create new instances of the service. |
| `Archive events for {{site.data.keyword.atracker_short}} hosted event search offerings`  | Provide the ablity to archive to a client configured Cloud Object Storage (COS) location and archive data. | Configure Cloud Object Storage per your requirements.   \n [Enable archiving of the Activity Tracker instance.](/docs/activity-tracker?topic=activity-tracker-archiving) |
| `Monitor events for {{site.data.keyword.atracker_short}} hosted event search offerings`  | [Participating Cloud services](/docs/activity-tracker?topic=activity-tracker-cloud_services) publish relevant event data to their subscribing clients. {{site.data.keyword.at_full_notm}} provides clients with the ability to receive the events once the client configures their instance. | [Create an {{site.data.keyword.at_full_notm}} instance](/docs/activity-tracker?topic=activity-tracker-provision) in each region where Cloud service subscriptions publish events to receive the published events.   \n Create an instance in Frankfurt to get global Activity Tracker events.   \n [Create views, dashboards, and screens to view and analyze the data.](/docs/activity-tracker?topic=activity-tracker-monitor_events)|
{: caption="Table 1. Responsibilities for incident and operations" caption-side="top"}



## Change management
{: #change-management}

| Task                                                    | {{site.data.keyword.IBM_notm}} Responsibilities | Your Responsibilities |
|---------------------------------------------------------|-----------------------|--------|
| `Updates to {{site.data.keyword.atracker_short}} event routing` | Provide major, minor, and patch version updates for {{site.data.keyword.atracker_short}} interfaces.   \n Document changes in the [IBM Cloud Support Center](https://cloud.ibm.com/unifiedsupport/supportcenter) | `N/A` | 
| `Updates to {{site.data.keyword.at_short}} hosted event search offerings` | Provide major, minor, and patch version updates for {{site.data.keyword.at_full_notm}} interfaces.   \n Document changes in the [Release notes](https://logdna.zendesk.com/hc/categories/360001626492-Release-Notes){: external} | `N/A` | 
| `Track versions of custom views, dashboards, screens, parsing templates, and alerts for {{site.data.keyword.at_short}} hosted event search offerings`    | `N/A` | Use your own change management process to control versions of metadata resources such as views, dashboards, screens, parsing templates, and alerts`.   \n To learn how to export metadata, see [Export the configuration of resources in an auditing instance](/docs/activity-tracker?topic=activity-tracker-reuse_resource_definitions#rrd_export_config). | 
{: caption="Table 2. Responsibilities for change management" caption-side="top"}



## Identity and access management
{: #iam-responsibilities}


| Task                           | {{site.data.keyword.IBM_notm}} Responsibilities | Your Responsibilities |
|--------------------------------|-------------------------------------------------|-----------------------|
| `Manage permissions for {{site.data.keyword.atracker_short}} event routing`           | Provide the ability to restrict access to resouces.   \n {{site.data.keyword.IBM_notm}} is responsible for the security and compliance of the {{site.data.keyword.atracker_short}} feature. | Restrict access to {{site.data.keyword.atracker_short}} and Cloud Object Storage resources by using Cloud IAM access policies. Define IAM policies to control which users within your account have access to manage the service and related resources in your account.    \n [Learn more about controlling access through IAM](/docs/activity-tracker?topic=activity-tracker-iam).|
| `Manage permissions for {{site.data.keyword.at_short}} hosted event search offerings`           |Provide the ability to restrict access to resouces.   \n {{site.data.keyword.IBM_notm}} is responsible for the security and compliance of {{site.data.keyword.at_full_notm}}. | Restrict access to resources by using Cloud IAM access policies by defining IAM policies to control which users within your account have access to the data.    \n [Learn more about controlling access through IAM](/docs/activity-tracker?topic=activity-tracker-iam).| 
| `Validate targets in each region for {{site.data.keyword.atracker_short}} event routing` | Provide the ability to check if the credentials that are used by the {{site.data.keyword.atracker_short}} service in a region are valid and allow uploading of objects to teh bucket.  | [Configure a target per region](/docs/activity-tracker?topic=activity-tracker-target#target-create) with valid credentials to upload object into the bucket. [Validate the credentials](/docs/activity-tracker?topic=activity-tracker-target#target-validate) that are used by {{site.data.keyword.atracker_short}} in each region to write auditing events in a COS bucket. | 
{: caption="Table 3. Responsibilities for identity and access management" caption-side="top"}



## Security and regulation compliance
{: #security-compliance}


| Task                                       | {{site.data.keyword.IBM_notm}} Responsibilities | Your Responsibilities |
|--------------------------------------------|-------------------------------------------------|-----------------------|
| `Encrypt data`  | Encrypt data in motion and at rest per compliance specifications. | Ensure encryption of archived data by configuring a COS bucket that has full control over the data encryption keys that are used. [{{site.data.keyword.cos_full}} provides several options to encrypt your data.](/docs/cloud-object-storage?topic=cloud-object-storage-encryption) |
| `Meet security and compliance objectives`  | Maintain controls that are commensurate to various industry compliance standards such as SOC2, PCI, HIPAA and Privacy Shield. | Set up and maintain security and regulation compliance for your apps and data.  This includes:   \n [Defining the account management strategy](/docs/activity-tracker?topic=activity-tracker-adoption#adoption_account)   \n [Configuring the accounts settings for compliance](/docs/activity-tracker?topic=activity-tracker-adoption#adoption_acc_settings)   \n [Define IAM Strategy](/docs/activity-tracker?topic=activity-tracker-adoption#adoption_iam)   \n [Define the notification strategy](/docs/activity-tracker?topic=activity-tracker-adoption#adoption_alerts) |
{: caption="Table 4. Responsibilities for security and regulation compliance" caption-side="top"}



## Disaster recovery
{: #disaster-recovery}


| Task                                                            | {{site.data.keyword.IBM_notm}} Responsibilities | Your Responsibilities |
|-----------------------------------------------------------------|-------------------------------------------------|-----------------------|
| `Restore functionality for {{site.data.keyword.atracker_short}} event routing`  | Automatically recover and restart {{site.data.keyword.atracker_short}} components after any disaster event.    \n In case of a regional disaster, {{site.data.keyword.cloud_notm}} service teams, who are responsible for the operations of services that generate auditing events, will repoint their service to {{site.data.keyword.atracker_short}} endpoints in the alternate region within the same regulatory boundaries. | [Complete the disaster recovery (DR) steps for {{site.data.keyword.atracker_short}} event routing](/docs/activity-tracker?topic=activity-tracker-ha_dr#dr-atracker). |
| `Restore functionality for {{site.data.keyword.at_short}} hosted event search offerings` `[*]`  | Automatically recover and restart {{site.data.keyword.atracker_short}} components after any disaster event.    \n In case of a regional disaster, {{site.data.keyword.cloud_notm}} service teams, who are responsible for the operations of services that generate auditing events, will repoint their service to {{site.data.keyword.atracker_short}} endpoints in the alternate region within the same regulatory boundaries. | `N/A`|
| `Backup {{site.data.keyword.atracker_short}} components`   | Daily backup of the {{site.data.keyword.atracker_short}} infrastructure and components. | `N/A` |
| `Backup auditing events for {{site.data.keyword.atracker_short}} hosted event search offerings` | `N/A` | [Configure archiving to retain a backup copy of the data.](/docs/activity-tracker?topic=activity-tracker-archiving) |
| `Backup metadata for {{site.data.keyword.atracker_short}} hosted event search offerings` | Backup metadata that is used by the service. | [Backup the metadata such as views, dashboards, screens, parsing templates, and alerts for each auditing instance.](/docs/activity-tracker?topic=activity-tracker-reuse_resource_definitions#rrd_export_config) |
| `Restore metadata for {{site.data.keyword.atracker_short}} hosted event search offerings`   | Restore metadata that is used by the service.  | [Restore the metadata such as views, dashboards, screens, parsing templates, and alerts for each instance.](/docs/activity-tracker?topic=activity-tracker-reuse_resource_definitions#import_config) |
{: caption="Table 5. Responsibilities for disaster recovery" caption-side="top"}

`[*]` Recovered and restarted service components will not have customer data reloaded.
{: note}



