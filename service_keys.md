---

copyright:
  years: 2019, 2021
lastupdated: "2021-01-05"

keywords: IBM Cloud, LogDNA, Activity Tracker, export, api

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

 
# Managing service keys
{: #service_keys}

In an {{site.data.keyword.at_full_notm}} instance, you can create, delete, and view service keys through the LogDNA web UI.
{:shortdesc}

A service key is a unique code that is passed in an API request to identify the calling application or user. 

You must use a service key to complete any of the following tasks:
- Export data programmatically 
- Manage views and alerts programmatically by using the Configuration API or Terraform.

Only users that have **manager** role for the {{site.data.keyword.at_full_notm}} service, can manage service keys in an auditing instance.

You can only enable 20 service keys per auditing instance.



## Creating a service key
{: #service_keys_create}

You must have **manager** role for the {{site.data.keyword.at_full_notm}} service to complete this step.
{: important} 

You can only generate a service key through the LogDNA web UI.
{: important}
    
Complete the following steps to create a service key:

1. [Launch the {{site.data.keyword.at_full_notm}} web UI](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-launch#launch_cloud_ui).

2. Select the **Configuration** icon ![Configuration icon](images/admin.png). Then, select **Organization**. 

3. Select **API keys**.

    You can see the service keys that are created.   

4. Click **Generate Service Key**. A new key is added to the list. 



## Deleting a service key
{: #service_keys_delete}

You must have **manager** role for the {{site.data.keyword.at_full_notm}} service to complete this step.
{: important} 

You can only delete a service Key through the LogDNA web UI.
{: important}

Complete the following steps to delete a service key:

1. [Launch the {{site.data.keyword.at_full_notm}} web UI](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-launch#launch_cloud_ui).

2. Select the **Configuration** icon ![Configuration icon](images/admin.png). Then, select **Organization**. 

3. Select **API keys**.

    You can see the service keys that are created.   

4. Delete the key.


## Viewing a service key
{: #service_keys_view}

Only users that have the **manager** service role or the **standard-member** service role can view service keys.
{: important} 

For more information, see [service roles](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-iam#service).

Complete the following steps to view a service key:

1. [Launch the {{site.data.keyword.at_full_notm}} web UI](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-launch#launch_cloud_ui).

2. Select the **Configuration** icon ![Configuration icon](images/admin.png). Then, select **Organization**. 

3. Select **API keys**.

    If you have permissions, you can see the service keys that are available.   


