---

copyright:
  years: 2019, 2022
lastupdated: "2021-08-09"

keywords: IBM Cloud, Activity Tracker, web UI, browser

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}

# Getting the UI URL
{: #get_web_url}

After you provision an instance of the {{site.data.keyword.at_full_notm}} service in the {{site.data.keyword.cloud_notm}}, you can view, monitor, and manage events through the {{site.data.keyword.at_full_notm}} web UI. You can launch the UI from the {{site.data.keyword.cloud_notm}} UI or directly from a browser.
{: shortdesc}


This information applies only if you use an {{site.data.keyword.at_full}} [hosted event search offering](/docs/activity-tracker?topic=activity-tracker-service_plan).
{: important}

To get the UI URL, complete the following steps from a terminal:

1. [Pre-requisite] Installation of the {{site.data.keyword.cloud_notm}} CLI. [Learn more](/docs/cli?topic=cli-getting-started).

2. Log in to the location in the {{site.data.keyword.cloud_notm}} where the instance is provisioned. Run the following command: [ibmcloud login](/docs/cli?topic=cli-ibmcloud_cli#ibmcloud_login)

3. Set the resource group where the instance is available. Run the following command: [ibmcloud target](/docs/cli?topic=cli-ibmcloud_cli#ibmcloud_target)

    By default, the `default` resource group is set.

4. Get the dashboard URL. Run the following command:

    ```text
    ic resource service-instance INSTANCE_NAME --output JSON | grep dashboard_url
    ```
    {: codeblock}
    
Where *INSTANCE_NAME* is the name of the instance.

To get the name of the instances that are available in a resource group, you can run `ibmcloud resource service-instances`.
{: tip}

