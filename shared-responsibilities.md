---

copyright:
  years: 2019, 2022
lastupdated: "2022-05-16"

keywords: 

subcollection: activity-tracker


---

{{site.data.keyword.attribute-definition-list}}

# Understanding your responsibilities when using {{site.data.keyword.at_full_notm}}
{: #shared-responsibilities}

Learn about the management responsibilities and terms and conditions that you have when you use {{site.data.keyword.at_full_notm}}. For a high-level view of the service types in {{site.data.keyword.cloud_notm}} and the breakdown of responsibilities between the customer and {{site.data.keyword.IBM_notm}} for each type, see [Shared responsibilities for {{site.data.keyword.cloud_notm}} offerings](/docs/overview?topic=overview-shared-responsibilities).
{: shortdesc}

Review the following sections for the specific responsibilities for you and for {{site.data.keyword.IBM_notm}} when you use {{site.data.keyword.at_full_notm}}. For the overall terms of use, see [{{site.data.keyword.cloud_notm}} Terms and Notices](/docs/overview/terms-of-use?topic=overview-terms).


## Incident and operations management
{: #incident-and-ops}

| Task              | {{site.data.keyword.IBM_notm}} Responsibilities | Your Responsibilities |
|-------------------|-------------------------------------------------|-----------------------|
| `Incident and operations management` | Maintain service instances and infrastructure workloads. | Maintain incident and operations management of your data. |
| `Monitor incidents`  | Provide notifications for planned maintenance, security bulletins, or unplanned outages. | Set preferences to [receive emails about platform notifications](/docs/overview?topic=overview-ui#email-prefsl).   \n Monitor the [IBM Cloud status page](https://{DomainName}/status?selected=announcement) for general announcements. |
| `Maintain {{site.data.keyword.cloud_notm}} high availability SLA for {{site.data.keyword.at_short}}`   | Provide {{site.data.keyword.at_short}} functionality across availability zones in a Multi-Zone Region (MZR).   \n  Provide {{site.data.keyword.at_short}} functionality across hosts in a Single-Zone Region (SZR).   \n Provide replication, fail-over features, and infrastructure maintenance and updates. | Keep your {{site.data.keyword.at_short}}  configuration in a version control system so that you can reconfigure a region if needed.   \n Comply with [Operational responsibilities when using {{site.data.keyword.cos_full_notm}}](/docs/cloud-object-storage?topic=cloud-object-storage-responsibilities#responsibilities-operational). |
| `Monitor events for {{site.data.keyword.at_short}}`  | [Participating Cloud services](/docs/activity-tracker?topic=activity-tracker-cloud_services) publish relevant event data to their subscribing clients. Clients have the ability to receive this data once their account is configured. | [Configure your account](/docs/activity-tracker?topic=activity-tracker-getting-started) in each region where Cloud service subscriptions publish events to receive the published events. |
| `Maintain {{site.data.keyword.cloud_notm}} high availability SLA for {{site.data.keyword.at_short}}`   | Provide Cloud Service across availability zones in a Multi-Zone Region (MZR).   \n  Provide Cloud Service across hosts in a Single-Zone Region (SZR).   \n Provides replication, fail-over features, and infrastructure maintenance and updates. | Use the list of available regions to plan for and create new instances of the service. |
| `Archive events for {{site.data.keyword.at_short}}`  | Provide the ability to archive to a client configured Cloud Object Storage (COS) location and archive data. | Configure Cloud Object Storage per your requirements.   \n [Enable archiving of the Activity Tracker instance.](/docs/activity-tracker?topic=activity-tracker-archiving) |
| `Monitor events for {{site.data.keyword.at_short}}`  | [Participating Cloud services](/docs/activity-tracker?topic=activity-tracker-cloud_services) publish relevant event data to their subscribing clients. {{site.data.keyword.at_full_notm}} provides clients with the ability to receive the events once the client configures their instance. | [Create an {{site.data.keyword.at_full_notm}} instance](/docs/activity-tracker?topic=activity-tracker-provision) in each region where Cloud service subscriptions publish events to receive the published events.   \n Create an instance in Frankfurt to get global Activity Tracker events.   \n [Create views, dashboards, and screens to view and analyze the data.](/docs/activity-tracker?topic=activity-tracker-monitor_events)|
| `Configuring exclusion rules for {{site.data.keyword.at_short}}` |  | Verify that each exclusion rule that you add behaves as expected. Improper configured exclusion rules can result in storing data not intended for storage. For more information on how to use exclusion rules, see [Excluding data by using exclusion rules](/docs/activity-tracker?topic=activity-tracker-exclusion_rules), [Configuring conditional streaming](/docs/activity-tracker?topic=activity-tracker-streaming-conditional) and [Configuring usage quota exclusion rules](/docs/activity-tracker?topic=activity-tracker-control_usage_quotas#rules_usage_quota). |
{: caption="Table 1. Responsibilities for incident and operations" caption-side="top"}


## Change management
{: #change-management}

| Task                                                    | {{site.data.keyword.IBM_notm}} Responsibilities | Your Responsibilities |
|---------------------------------------------------------|-----------------------|--------|
| `Updates to {{site.data.keyword.at_short}}` | Provide major, minor, and patch version updates for {{site.data.keyword.at_full_notm}} interfaces.   \n Document changes in the [Release notes](https://docs.mezmo.com/changelog){: external} | `N/A` | 
| `Track versions of custom views, dashboards, screens, parsing templates, and alerts for {{site.data.keyword.at_short}}`    | `N/A` | Use your own change management process to control versions of metadata resources such as views, dashboards, screens, parsing templates, and alerts`.   \n To learn how to export metadata, see [Export the configuration of resources in an auditing instance](/docs/activity-tracker?topic=activity-tracker-reuse_resource_definitions#rrd_export_config). | 
{: caption="Table 2. Responsibilities for change management" caption-side="top"}



## Identity and access management
{: #iam-responsibilities}


| Task                           | {{site.data.keyword.IBM_notm}} Responsibilities | Your Responsibilities |
|--------------------------------|-------------------------------------------------|-----------------------|
| `Manage permissions for {{site.data.keyword.at_short}}`           |Provide the ability to restrict access to resources.   \n {{site.data.keyword.IBM_notm}} is responsible for the security and compliance of {{site.data.keyword.at_full_notm}}. | Restrict access to resources by using Cloud IAM access policies by defining IAM policies to control which users within your account have access to the data.    \n [Learn more about controlling access through IAM](/docs/activity-tracker?topic=activity-tracker-iam).| 
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
| `Restore functionality for {{site.data.keyword.at_short}}` `[*]`  | Automatically recover and restart {{site.data.keyword.at_short}} components after any disaster event.    \n In case of a regional disaster, {{site.data.keyword.cloud_notm}} service teams, who are responsible for the operations of services that generate auditing events, will point their service to {{site.data.keyword.at_short}} endpoints in the alternate region within the same regulatory boundaries. | `N/A`|
| `Backup {{site.data.keyword.a_short}} components`   | Daily backup of the {{site.data.keyword.at_short}} infrastructure and components. | `N/A` |
| `Backup auditing events for {{site.data.keyword.at_short}}` | `N/A` | [Configure archiving to retain a backup copy of the data.](/docs/activity-tracker?topic=activity-tracker-archiving) |
| `Backup metadata for {{site.data.keyword.at_short}}` | Backup metadata that is used by the service. | [Backup the metadata such as views, dashboards, screens, parsing templates, and alerts for each auditing instance.](/docs/activity-tracker?topic=activity-tracker-reuse_resource_definitions#rrd_export_config) |
| `Restore metadata for {{site.data.keyword.at_short}}`   | Restore metadata that is used by the service.  | [Restore the metadata such as views, dashboards, screens, parsing templates, and alerts for each instance.](/docs/activity-tracker?topic=activity-tracker-reuse_resource_definitions#import_config) |
{: caption="Table 5. Responsibilities for disaster recovery" caption-side="top"}

`[*]` Recovered and restarted service components will not have customer data reloaded.
{: note}


To plan and prepare in the event of a DR scenario for {{site.data.keyword.at_short}}, see [Recovering from a disaster region](/docs/activity-tracker?topic=activity-tracker-ha_dr_steps).
{: important}

