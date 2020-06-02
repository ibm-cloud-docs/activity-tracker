--

copyright:
  years: 2019, 2020
lastupdated: "2020-04-28"

keywords: IBM Cloud, LogDNA, Activity Tracker, provision instance

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

# Change the service plan of an instance
{: #upgrade}

When you provision an instance of the {{site.data.keyword.at_full_notm}} service, you must choose a service plan. Different plans offer different features. You can change the service plan at any time.
{:shortdesc}

[Learn more about service plans.](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-service_plan)

## Changing the service plan through the Observability dashboard
{: #upgrade_ui}

To change the service plan of an instance from the Observability dashboard in the {{site.data.keyword.cloud_notm}}, complete the following steps:

1. [Log in to your {{site.data.keyword.cloud_notm}} account ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/login){:new_window}.

	After you log in with your user ID and password, the {{site.data.keyword.cloud_notm}} UI opens.

2. Go to the menu icon ![menu icon](../../icons/icon_hamburger.svg). Then, select **Observability** to access the *Observability* dashboard.

3. Select **Activity Tracker**, then select **Edit plan**. 

4. Select a service plan. 

8. Click **Save**.






## Changing the service plan through the CLI
{: #upgrade_cli}

Complete the following steps to change the service plan:

1. [Pre-requisite] Installation of the {{site.data.keyword.cloud_notm}} CLI. [Learn more](/docs/cli?topic=cloud-cli-ibmcloud-cli#ibmcloud-cli).

   If the CLI is installed, continue with the next step.

2. Log in to the location in the {{site.data.keyword.cloud_notm}} where the instance is provisioned. Run the following command: [`ibmcloud login`](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login)

    To get the latest list of locations that are available for the {{site.data.keyword.at_full_notm}} service, see [Locations](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-regions).

3. Set the resource group where the instance is available. Run the following command: [`ibmcloud target`](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target)

    By default, the `default` resource group is set.

4. Change the service plan. Run the [`ibmcloud resource service-instance-update`](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_commands_resource#ibmcloud_resource_service_instance_create) command:

    ```
    ibmcloud resource service-instance-update NAME --service-plan-id SERVICE_PLAN_NAME
    ```
    {: codeblock}

    Where

    * NAME is the name of the instance

    * SERVICE_PLAN_NAME is the type of plan. Valid values are *lite*, *7-day*, *14-day*, *30-day*


    
For example, to change the service plan of an instance to the 7 days retention plan, run the following command:

```
ibmcloud resource service-instance-update logdna-instance-01 7-day
```
{: codeblock}
