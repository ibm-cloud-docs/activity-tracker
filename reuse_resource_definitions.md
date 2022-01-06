---

copyright:
  years: 2019, 2022
lastupdated: "2021-08-09"

keywords: IBM Cloud, Activity Tracker, reuse

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}

# Reusing definitions of resources
{: #reuse_resource_definitions}

To avoid recreating definitions of views, boards, parsing templates, and exclusion rules, you can export these resources from a {{site.data.keyword.at_full}} instance as a JSON file. Then, you can import the definitions into other auditing instances.
{: shortdesc}

This information applies only if you use an {{site.data.keyword.at_full}} [hosted event search offering](/docs/activity-tracker?topic=activity-tracker-service_plan).
{: important}

## Export the configuration of resources
{: #rrd_export_config}

Complete the following steps to export the configuration of your resources:

1. [Launch the {{site.data.keyword.at_full_notm}} web UI](/docs/services/activity-tracker?topic=activity-tracker-launch).

2. Select the **Settings** icon ![Configuration icon](images/admin.png "Admin icon"). Then select **Organization**. 

3. Select **Export Config**.

4. In the *Export configuration* section, select the types of resources that you want to export.

    Notice that options are disabled if you do not have definitions of this type of resource in your auditing instance. 

    You can export views and alerts, boards, screens, parsing templates, and exclusion rules. 

5. Click **Export** to save the file.


## Import the configuration of resources into an auditing instance
{: #import_config}


Complete the following steps to import the configuration of your resources:

1. [Launch the {{site.data.keyword.at_full_notm}} web UI](/docs/services/activity-tracker?topic=activity-tracker-launch).

2. Select the **Settings** icon ![Configuration icon](images/admin.png "Admin icon"). Then select **Organization**. 

3. Select **Import Config**.

4. In the *Import configuration* section, drop the JSON config file that inclides the resource definitions, or click to upload a file.

5. Choose **Add to existing configuration** or **Replace existing configuration**.

    When you choose the **add** option, you add assets to the exisiting ones.

    When you choose the **replace** option, you remove all assets, and new ones are created.

6. Click **Import**.


