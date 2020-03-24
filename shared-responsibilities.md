---

copyright:
  years: 2018, 2020
lastupdated: "2020-03-25"

keywords: IBM Cloud, LogDNA, Activity Tracker, auditing, customer responsibilities, IBM responsibilities, terms and conditions

subcollection: logdnaat


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

You and {{site.data.keyword.IBM_notm}} share responsibilities for the set up and maintenance of your {{site.data.keyword.at_full_notm}} service instance and infrastructure workloads. You are responsible for incident and operations management of your data.
{: note}

| Task              | {{site.data.keyword.IBM_notm}} Responsibilities | Your Responsibilities |
|-------------------|-------------------------------------------------|-----------------------|
| `Monitor incidents`  | Provide notifications for planned maintenance, security bulletins, or unplanned outages. | Set preferences to [receive emails about platform notifications](/docs/overview?topic=overview-ui#email-prefsl). </br>Monitor the [IBM Cloud status page](https://{DomainName}/status?selected=announcement) for general announcements. |
| `Maintain {{site.data.keyword.cloud_notm}} high availability SLA`  | Operate the {{site.data.keyword.contdelivery_short}} service in accordance with the {{site.data.keyword.cloud_notm}} Public [Service Level Agreements (SLAs)](/docs/overview/terms-of-use?topic=overview-slas). | `N/A` |
| `Provide high availability capabilities` | Provide capabilities, such as {{site.data.keyword.IBM_notm}}-owned infrastructure in multizone regions (MZR), to meet local access and low latency requirements for each supported region.  | Use the list of [available regions](/docs/Log-Analysis-with-LogDNA?topic=LogDNA-regions) to plan for and create new instances of the service. |
{: caption="Table 1. Responsibilities for incident and operations" caption-side="top"}



## Change management
{: #change-management}

You and {{site.data.keyword.IBM_notm}} share responsibilities for keeping {{site.data.keyword.at_full_notm}} service components at the latest version. 

{: note}

| Task                                                    | {{site.data.keyword.IBM_notm}} Responsibilities | Your Responsibilities |
|---------------------------------------------------------|-----------------------|--------|
| `Update the {{site.data.keyword.at_full_notm}} service` | Provide regular updates to the service with new features, fixes for defects, and security fixes. | `N/A` |
| `Track versions of custom views, dashboards, screens, parsing templates, and alerts`    | `N/A` | Use your own change management process to control versions of metadata resources such as views, dashboards, screens, parsing templates, and alerts`. | 
{: caption="Table 2. Responsibilities for change management" caption-side="top"}


## Identity and access management
{: #iam-responsibilities}

{{site.data.keyword.IBM_notm}} is responsible for the security and compliance of {{site.data.keyword.at_full_notm}}. You are responsible for defining the {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM) policies to control which users within your account have access to the auditing data.
{: note}

| Task                           | {{site.data.keyword.IBM_notm}} Responsibilities | Your Responsibilities |
|--------------------------------|-------------------------------------------------|-----------------------|
| `Manage platform permissions`  | Allow administrators to control access to manage resources in the {{site.data.keyword.cloud_notm}}. | Grant, revoke, and manage access to service instances by using IAM. | 
| `Manage service permissions`   | Allow administrators to control access to work with the {{site.data.keyword.at_full_notm}}. | Grant, revoke, and manage access to auditing features by using IAM. |
{: caption="Table 3. Responsibilities for identity and access management" caption-side="top"}

[Learn more about controlling access through IAM](/docs/Activity-Tracker-with-LogDNA?topic=logdnaat-iam).


## Security and regulation compliance
{: #security-compliance}

{{site.data.keyword.IBM_notm}} is responsible for the security and compliance of {{site.data.keyword.at_full_notm}}. You are responsible for ensuring that logs, that contain regulated data, are not provided to the {{site.data.keyword.at_full_notm}} service.
{: note}

| Task                                       | {{site.data.keyword.IBM_notm}} Responsibilities | Your Responsibilities |
|--------------------------------------------|-------------------------------------------------|-----------------------|
| `Meet security and compliance objectives`  | Maintain controls that are commensurate to supported industry compliance standards, such as SOC and ISO. | Ensure that sensitive data, PII data, or regulated data is not used to name resources. |
{: caption="Table 4. Responsibilities for security and regulation compliance" caption-side="top"}



## Disaster recovery
{: #disaster-recovery}

{{site.data.keyword.IBM_notm}} is responsible for the recovery of {{site.data.keyword.at_full_notm}} components in case of disaster. You are responsible for the recovery of the LogDNA agents running in your environment should they be impacted by a disaster, and the resources to manage data like views, dashboards, screens, parsing templates, and alerts`.
{: note}

| Task                                                            | {{site.data.keyword.IBM_notm}} Responsibilities | Your Responsibilities |
|-----------------------------------------------------------------|-------------------------------------------------|-----------------------|
| `Backup the {{site.data.keyword.at_full_notm}} service`        | Daily backup of the {{site.data.keyword.at_full_notm}} infrastructure and components. | `N/A` |
| `Recovery of the {{site.data.keyword.at_full_notm}} service`   | Re-establish the {{site.data.keyword.at_full_notm}} service after any disaster event. | `N/A` |
| `Backup data that is available for search`                     | Backup data in the region that the service operates in every 24 hrs. | Use access groups to manage permissions to work with the {{site.data.keyword.at_full_notm}}. |
| `Restore data that is available for search`                    | Restore auditing data after any disaster event.   | Add or modify policies to the access groups in your asccount that control permissions to work with the auditing service in the new location where the region is recovered. |
| `Backup the metadata of a LogDNA instance`                          | `N/A` | Backup the metadata such as views, dashboards, screens, parsing templates, and alerts for each LogDNA instance. |
| `Restore the metadata of a LogDNA instance`                         | `N/A` | Restore the metadata such as views, dashboards, screens, parsing templates, and alerts for each LogDNA instance. |
{: caption="Table 5. Responsibilities for disaster recovery" caption-side="top"}
