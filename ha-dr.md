---

copyright:
  years: 2018, 2020
lastupdated: "2020-11-20"

keywords: IBM Cloud, LogDNA, Activity Tracker, auditing, disaster recovery, ha, high availability, redundancy

subcollection: Activity-Tracker-with-LogDNA



---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:tip: .tip}
{:note: .note}
{:important: .important}

# High availability and disaster recovery
{: #ha-dr}

{{site.data.keyword.at_full_notm}} is a highly available, multi-tenant, regional service. In this topic, you can learn more about {{site.data.keyword.at_full_notm}}'s availability and disaster recovery strategies.
{: shortdesc}



## Availability zones
{: #ha-dr_locations}

An availability zone is a logically and physically isolated location within an {{site.data.keyword.cloud_notm}} region where your data is processed and hosted. 
* An availability zone has independent power, cooling, and network infrastructures that are isolated from other zones to strengthen fault tolerance by avoiding single points of failure between zones.
* An availability zone offers high bandwidth and low inter-zone latency within a region.

A region (location) is a geographically and physically separate group of one or more availability zones with independent electrical and network infrastructures isolated from other regions. 
* Regions are designed to remove shared single points of failure with other regions and guarantee low inter-zone latency within the region.
* Each region has 3 different data centers (DC) for redundancy.

The following table lists the high-availability (HA) status for the regions (locations) where the {{site.data.keyword.at_full_notm}} service is available:

| Geography             | Region                   | EU-Supported | HA Status |
|-----------------------|--------------------------|--------------|-----------|
| `Asia Pacific`        | `Tokyo (jp-tok)`         | `N/A`        | `MZR`     |
| `Asia Pacific`        | `Seoul (kr-seo)`         | `N/A`        | `SZR`     |
| `Asia Pacific`        | `Sydney (au-syd)`        | `N/A`        | `MZR`     |
| `Europe`              | `Frankfurt (eu-de) (*)`  | `YES`        | `MZR`     |
| `Europe`              | `London (eu-gb)`         | `NO`         | `MZR`     |
| `North America`       | `Dallas (us-south)`      | `N/A`        | `MZR`     |
| `North America`       | `Washington (us-east)`   | `N/A`        | `MZR`     |
{: caption="Table 1. List of locations where the service is available" caption-side="top"}


Where
* A *geography* is a geographic area or larger political body that contains one or more regions.
* A *region* is a defined geographic territory. 

    A region could be a specific postal code area, a town, a city, a state, a group of states, or even a group of countries. 

    A region contains [multiple availability zones](https://www.ibm.com/cloud/data-centers/) to meet local access, low latency, and security requirements for the region.

* `N/A` means feature that is not applicable to that geography.
* `MZR` means multi-zone region. [Learn more](/docs/overview?topic=overview-locations#mzr-table).

 

## Availability of a auditing instance
{: #ha-dr-region}

When you provision an auditing instance, you select the MZR (location) where the instance is created. The region determines where the auditing data is processed and the data is hosted. 

A multizone region (MZR) consist of 3 or more availability zones that are independent from each other to ensure that single failure events affect only a single zone.

By default, each auditing instance consist of 3 zones, one primary zone and two secondary zones: 
* Each zone is located in a different data center in the region.
* The data in your primary zone is automatically replicated to the secondary zones with low latency. You don't need to do anything to enable the replication. 
* When the primary zone fails, a secondary zone is elected as the primary to prevent your service instance from being affected. 
* If 2 zones fail at the same time, the service is down.

The MZR architecture offers automatic failover between 2 zones, and high availability for a auditing instance withing a region.

Notice that only 1 region, Seoul, is a SZR.


## Disaster recovery (DR) of the auditing service in a region
{: #dr}

Disaster recovery is about surviving a catastrophic failure or loss of availability in a single location. 

{{site.data.keyword.at_full_notm}} follows {{site.data.keyword.cloud_notm}} requirements for [planning and recovering from disaster events](/docs/overview?topic=overview-zero-downtime#disaster-recovery).

If a regional disaster occurs, consider the following information:
* Data and the auditing metadata such as dashboards, alerts, views, screens, templates are backed up every 24 hours. In the event of an un-recoverable disaster, up to 24 hours of data and metadata changes to the auditing instance in the failure region can be lost.
* The estimated recovery time for rebuilding the regional site and restoring the service at another location is 24 hours.
* Due to the large volume of data, older data might not be available at the time the service is restored, as this process requires additional time to recover data from the backups.  
* When the auditing instance in the DR region is available in the new location, you will be able to use it while the data is restored into the newly constructed region.








