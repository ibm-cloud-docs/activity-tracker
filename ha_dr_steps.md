---

copyright:
  years: 2019, 2022
lastupdated: "2022-08-18"

keywords: IBM Cloud, Activity Tracker, auditing, disaster recovery, ha, high availability, redundancy

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}

# Recovering from a regional disaster
{: #ha_dr_steps}

{{site.data.keyword.atracker_full_notm}} hosted event search is a highly available, multi-tenant, regional service. In this topic, you can learn more about {{site.data.keyword.atracker_short}}'s availability and disaster recovery strategies, what you need to plan for, and what you need to do if you need to recover from a regional disaster.
{: shortdesc}

## Prereqs
{: #ha_dr_steps_prereqs}

- Learn about your responsibilities in the event of a disaster. See [Disaster and recovery](/docs/activity-tracker?topic=activity-tracker-shared-responsibilities#disaster-recovery).
- Learn about disaster recovery (DR). See [Overview](#ha_dr_steps_ov).

## Planning for a DR scenario
{: #ha_dr_steps_plan}

The steps in this section assume that you have a list of all {{site.data.keyword.at_full_notm}} instances per resource group and region in the account; access reports for each instance; and a current export of the configuration resources per instance.
{: important}

Consider using access groups to manage permissions to work with auditing instances. In the event of a DR situation, you can quickly add permissions for users and service IDs per access group and accelerate recovery time.
{: tip}

- To get the access report for an instance, go to the Observability UI, and in the **Activity Tracker** section, select 1 instance. Select the 3 dots icon and click **Access report**. Then, save it in a version control tool.

    The report includes a list of users, access groups, and service IDs that have access to the selected resource. You must have the `Administrator` role on the selected resource to view the report.

    You can download the report as CSV or as JSON.

    Generate an access report everytime permissions to work with auditing instances change in the account.

    You can use terraform to manage IAM permissions. Consider keeping the terraform script up to date with details of all the IAM resources so that you can recover faster in the event of a DR. For more information on using terraform to provision a auditing instance, see [IBM Cloud Provider - Identity and Access Management (IAM)](https://registry.terraform.io/providers/IBM-Cloud/ibm/latest/docs).
    {: tip}

- To get the list of instances including all the details, you can run the following command:

    ```text
    ibmcloud resource service-instances --all-resource-groups --output JSON > instances.json
    ```
    {: pre}

    Get current details everytime a change or a new auditing instance is created in the account. Then, save the file you save (`instances.json`) in a version control tool.

     Once the export file is generated, do not modify it. Any change to that file will corrupt the file and you will not be able to import it. For more information, see [Export the configuration of resources in a auditing instance](/docs/activity-tracker?topic=activity-tracker-reuse_resource_definitions#rrd_export_config).

    You can use terraform to provision auditing instances. Consider keeping the terraform script up to date with details of all the instances so that you can recover faster in the event of a DR. For more information on using terraform to provision a auditing instance, see [Provisioning an instance by using Terraforms](/docs/activity-tracker?topic=activity-tracker-terraform-setup).
    {: tip}


## Steps to recover a regional disaster
{: #ha_dr_steps_region}


Complete the following steps to recover {{site.data.keyword.at_full_notm}} from a regional disaster:

1. Decide the region where you plan to recover activity. 

    It is best to choose the same recovery region that you choose for the rest of your services that are also impacted in the region that is down. 

    Why? Some of those services might generate location-based events. 

    Make sure that the region that you choose is a supported region for the {{site.data.keyword.at_full_notm}} service. For more information on supported regions, see [Locations](/docs/activity-tracker?topic=activity-tracker-regions).
    {: note}
    
2. Only 1 instance of {{site.data.keyword.at_full_notm}} is available per region. Provision 1 instance in the new region if you do not have one already.

    You can use a terraform script. Notice that you must edit the script and change the `region` where the instance is to be provisioned. For more information, see [Provisioning an instance by using Terraforms](/docs/activity-tracker?topic=activity-tracker-terraform-setup).

3. Grant permissions to users, service IDs, and access groups to work with the new auditing instance. Use the latest access report to map permissions for the new instance.

    Use the latest report to map permissions in the new region. You can also use your terraform script.

    If you use access groups, add new policies for the new instances. The users and service IDs within an access group will inherit those new policies.

    If you define permissions by users and service IDs, you must update permissions for each use and for each service ID.

4. Per instance, you must import the auditing configuration so any views, parsing templates, boards and screens are uploaded into the new instance. For more information, see [Import the configuration of resources into a auditing instance](/docs/activity-tracker?topic=activity-tracker-reuse_resource_definitions#import_config). 

5. If the region that goes down is Frankfurt, an additional step is required. Global events are sent to the Activity Tracker instance in Frankfurt. In the event of a DR for the Frankfurt region, you must configure global events through Activity Tracker Event Routing to be routed to the auditing instance that you have provisioned in the new region. 

    To learn how to configure global events to be routed to the new instance, see [Configuring Activity Tracker Event Routing in your account](/docs/atracker?topic=atracker-configure-atracker).



If you recover IBM Cloud services across different regions, these services will generate location-based events in the region where they are operational. To get a similar audit trail as in the region that went down, consider streaming events to 1 auditing instance so that you can group events for analysis. For more information, see [Configuring streaming to an Activity Tracker instance](/docs/activity-tracker?topic=activity-tracker-streaming-configure-l2l).
{: note}



## Overview
{: #ha_dr_steps_ov}

Disaster recovery is about surviving a catastrophic failure or loss of availability in a single location. 

{{site.data.keyword.at_short}} is a regional service, there is no automatic cross-regional failover or cross-regional disaster recovery. If all of the availability zones in a region fail, {{site.data.keyword.at_short}} becomes unavailable in that location. 

### Availability zones
{: #ha_dr_steps_locations}

The following table lists the high-availability (HA) status for the regions (locations) where the {{site.data.keyword.at_full_notm}} hosted event search service is available:

| Geography             | Region                   | EU-Supported | HA Status |
|-----------------------|--------------------------|--------------|-----------|
| `Asia Pacific`        | `Tokyo (jp-tok)`         | `N/A`        | `MZR`     |
| `Asia Pacific`        | `Osaka (jp-osa)`         | `N/A`        | `MZR`     |
| `Asia Pacific`        | `Seoul (kr-seo)`         | `N/A`        | `SZR`     |
| `Asia Pacific`        | `Chennai (in-che)`       | `N/A`        | `SZR`     |
| `Asia Pacific`        | `Sydney (au-syd)`        | `N/A`        | `MZR`     |
| `Europe`              | `Frankfurt (eu-de)`      | `YES`        | `MZR`     |
| `Europe`              | `London (eu-gb)`         | `NO`         | `MZR`     |
| `North America`       | `Dallas (us-south)`      | `N/A`        | `MZR`     |
| `North America`       | `Washington (us-east)`   | `N/A`        | `MZR`     |
| `North America`       | `Toronto (ca-tor)`       | `N/A`        | `MZR`     |
| `South America`     | `Sao Paulo (br-sao)`       | `N/A`        | `MZR` | 
{: caption="Table 1. List of locations where the service is available" caption-side="top"}


Where
* A *geography* is a geographic area or larger political body that contains one or more regions.
* A *region* is a defined geographic territory. 

    A region could be a specific postal code area, a town, a city, a state, a group of states, or even a group of countries. 

    A region contains [multiple availability zones](https://www.ibm.com/cloud/data-centers/) to meet local access, low latency, and security requirements for the region.

* `N/A` means feature that is not applicable to that geography.
* `MZR` means multi-zone region. [Learn more](/docs/overview?topic=overview-locations#mzr-table).
* `SZR` means single-zone region. [Learn more](/docs/overview?topic=overview-locations#szr-table).



### DR recovery time
{: #ha_dr_steps_recovery_time}

The following table indicates the estimated recovery times in the event of a DR situation:

| Recovery objective for DR | Estimated time |
|---------------------------|----------------|
| Maximum Tolerable Downtime (MTD) / Recovery Time Objective (RTO)  | Less than 24 hours |
| Recovery Point Objective (RPO) | Less than 4 hours |
{: caption="Table 4. Recovery objectives for DR" caption-side="top"}


### MZR
{: #ha_dr_steps_mzr}

A multizone region (MZR) consist of 3 or more availability zones that are independent from each other to ensure that single failure events affect only a single zone. By default, {{site.data.keyword.atracker_short}} hosted event search is deployed across 3 zones, one primary zone and two secondary zones: 
* Each zone is located in a different data center in the region.
* The data in your primary zone is automatically replicated to the secondary zones with low latency. You don't need to do anything to enable the replication. 
* The service is designed to withstand a single zone failure with no interruption.

The MZR architecture offers automatic failover between zones within the region, and high availability for a auditing instance withing a region.

### SZR
{: #ha_dr_steps_mzr}

The SZR architecture offers failover across 3 distinct systems within the single datacenter so that you get high availability from a system failure, but not from a datacenter failure.


### Data availability for {{site.data.keyword.at_short}} hosted event search offerings
{: #ha_dr_steps_data_availability}

When you provision an auditing instance, you select the location where the instance is created. The region determines where the auditing data is processed and the data is hosted. 

### Considerations
{: #ha_dr_steps_res}

{{site.data.keyword.atracker_full_notm}} hosted event search follows {{site.data.keyword.cloud_notm}} requirements for [planning and recovering from disaster events](/docs/overview?topic=overview-zero-downtime#disaster-recovery).
{: note}

When a regional disaster occurs, consider the following information:
* Data and the auditing metadata such as dashboards, alerts, views, screens, templates are backed up every 24 hours. In the event of an un-recoverable disaster, up to 24 hours of data and metadata changes to the auditing instance in the failure region can be lost.
* The estimated recovery time for rebuilding the regional site and restoring the service at another location is 24 hours.
* Due to the large volume of data, older data might not be available at the time the service is restored, as this process requires additional time to recover data from the backups.  
* When the auditing instance in the DR region is available in the new location, you will be able to use it while the data is restored into the newly constructed region.


