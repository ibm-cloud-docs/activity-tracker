---

copyright:
  years:  2022, 2023
lastupdated: "2022-05-04"

keywords: IBM Cloud, Activity Tracker, terraform

subcollection: activity-tracker


---

{{site.data.keyword.attribute-definition-list}}



# Terraform changes required after migrating to the V2 API (WIP)
{: #terraform-migrate}

After you have migrated to the {{site.data.keyword.atracker_full}} V2 API you will need to make changes to your **LogDNA Terraform provider** configuration.
{: shortdesc}

These instructions assume you have an {{site.data.keyword.atracker_full}} instance that you have provisioned using Terraform prior to the availability of the {{site.data.keyword.atracker_full}} V2 API.

Once you have [migrated to the V2 API](/docs/activity-tracker?topic=activity-tracker-migrate-resources) you will need to follow these instructions to update your Terraform configuration.
