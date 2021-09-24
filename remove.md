---

copyright:
  years: 2019, 2021
lastupdated: "2021-08-09"

keywords: IBM Cloud, Activity Tracker, delete instance

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}

# Removing an instance
{: #remove}

You can remove an instance of the {{site.data.keyword.at_full_notm}} service from the {{site.data.keyword.cloud_notm}} UI or through the command line.
{: shortdesc}

This information applies only if you use an {{site.data.keyword.at_full}} [hosted event search offering](/docs/activity-tracker?topic=activity-tracker-service_plan).
{: important}


## Removing an instance through the {{site.data.keyword.cloud_notm}} UI
{: #remove_ui}

To remove an instance of {{site.data.keyword.at_full_notm}} by using the {{site.data.keyword.cloud_notm}} UI, complete the following steps:

1. [Log in to your {{site.data.keyword.cloud_notm}} account](https://cloud.ibm.com/login){: external}.

	After you log in with your user ID and password, the {{site.data.keyword.cloud_notm}} UI opens.

2. Go to the menu icon ![Menu icon](../icons/icon_hamburger.svg) &gt; **Observability** to access the *Observability* Dashboard.

3. Select **Activity Tracker**. The list of instances is displayed.

4. Click the **Actions** icon ![Actions icon](../icons/action-menu-icon.svg) for the instance you want to delete and select **Delete**.

Next, remove permissions that are granted to users to work with the instance that you deleted.

## Removing an instance through the CLI
{: #remove_cli}

To remove an instance of {{site.data.keyword.at_full_notm}} through the command line, complete the following steps:

1. [Pre-requisite] Installation of the {{site.data.keyword.cloud_notm}} CLI.

   For more information, see [Installing the {{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cli-install-ibmcloud-cli).

2. Log in to the region in the {{site.data.keyword.cloud_notm}} where you want to provision the instance. Run the following command: [ibmcloud login](/docs/cli?topic=cli-ibmcloud_cli#ibmcloud_login)

3. Set the resource group where the instance is provisioned. Run the following command: [ibmcloud target](/docs/cli?topic=cli-ibmcloud_cli#ibmcloud_target)

    By default, the *default* resource group is set.

4. Remove the instance. Run the [ibmcloud resource service-instance-delete](/docs/cli?topic=cli-ibmcloud_commands_resource#ibmcloud_resource_service_instance_delete) command:

    ```text
    ibmcloud resource service-instance-delete NAME 
    ```
    {: codeblock}

    Where NAME is the name of the instance

    To list all the instances that are available in the resource group where you logged in, run the following command:

    ```text
    ibmcloud resource service-instances
    ```
    {: codeblock}
    
    
For example, to remove an instance, run the following command:

```text
ibmcloud resource service-instance-delete logdna-instance-01
```
{: codeblock}

Next, remove permissions that are granted to users to work with the instance that you deleted.


