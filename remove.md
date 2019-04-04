---

copyright:
  years: 2019
lastupdated: "2019-04-04"

keywords: IBM Cloud, LogDNA, Activity Tracker, delete instance

subcollection: logdnaat

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

# Removing an instance
{: #remove}

You can remove an instance of the {{site.data.keyword.at_full_notm}} service from the {{site.data.keyword.cloud_notm}} UI or through the command line.
{:shortdesc}



## Removing an instance through the {{site.data.keyword.cloud_notm}} UI
{: #remove_ui}

To remove an instance of {{site.data.keyword.at_full_notm}} by using the {{site.data.keyword.cloud_notm}} UI, complete the following steps:

1. [Log in to your {{site.data.keyword.cloud_notm}} account ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/login){:new_window}.

	After you log in with your user ID and password, the {{site.data.keyword.cloud_notm}} UI opens.

2. Go to the menu icon ![Menu icon](../../icons/icon_hamburger.svg) &gt; **Observability** to access the *Observability* Dashboard.

3. Select **Activity Tracker**. The list of instances is displayed.

4. Select the instance that you want to delete.

5. From the *Action* menu, select **Remove**.

Next, remove permissions that are granted to users to work with the instance that you deleted.

## Removing an instance through the CLI
{: #remove_cli}

To remove an instance of {{site.data.keyword.at_full_notm}} through the command line, complete the following steps:

1. [Pre-requisite] Installation of the {{site.data.keyword.cloud_notm}} CLI.

   For more information, see [Installing the {{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cloud-cli-ibmcloud-cli#ibmcloud-cli).

   If the CLI is installed, continue with the next step.

2. Log in to the region in the {{site.data.keyword.cloud_notm}} where you want to provision the instance. Run the following command: [`ibmcloud login`](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login)

3. Set the resource group where the instance is provisioned. Run the following command: [`ibmcloud target`](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target)

    By default, the *default* resource group is set.

4. Remove the instance. Run the [`ibmcloud resource service-instance-delete`](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_commands_resource#ibmcloud_resource_service_instance_delete) command:

    ```
    ibmcloud resource service-instance-delete NAME 
    ```
    {: codeblock}

    Where NAME is the name of the instance

    To list all the instances that are available in the resource group where you logged in, run the following command:

    ```
    ibmcloud resource service-instances
    ```
    {: codeblock}
    
    
For example, to remove an instance, run the following command:

```
ibmcloud resource service-instance-delete logdna-instance-01
```
{: codeblock}

Next, remove permissions that are granted to users to work with the instance that you deleted.


