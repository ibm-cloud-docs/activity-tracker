---

copyright:
  years: 2019
lastupdated: "2019-06-03"

keywords: IBM Cloud, LogDNA, Activity Tracker, provision instance

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

# Provisioning an instance
{: #provision}

Before you can monitor and manage event data with {{site.data.keyword.at_full_notm}}, you must provision an instance of the service in {{site.data.keyword.cloud_notm}}.
{:shortdesc}

To provision an {{site.data.keyword.at_full_notm}} instance in a Public Cloud region, consider the following information:
* You must select the service plan that is associated with the instance, the region where your logs are collected, and the plan that determines the retention period for your logs. You can choose from 7, 14, or 30-day retention periods. Alternatively, {{site.data.keyword.at_full_notm}} offers a `Lite` plan that you can use to view your events as they pass through the system. You can view events by using event tailing. You can also design filters to prepare for upgrading to a longer retention period plan. This plan has a 0-day retention period.
* Your user ID must have permisisons to provision a service in a resource group. [Learn more](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-iam#groups).


You can only provision 1 instance of the service per {{site.data.keyword.cloud_notm}} region.
{: important}

## Provisioning an instance through the Observability dashboard
{: #provision_ui}

To provision an instance from the Observability dashboard in the {{site.data.keyword.cloud_notm}}, complete the following steps:

1. [Log in to your {{site.data.keyword.cloud_notm}} account ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/login){:new_window}.

	After you log in with your user ID and password, the {{site.data.keyword.cloud_notm}} UI opens.

2. Go to the menu icon ![menu icon](../../icons/icon_hamburger.svg). Then, select **Observability** to access the *Observability* dashboard.

3. Select **Activity Tracker**, then click **Create instance**. 

4. Enter a name for the service instance.

5. Select the [location](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-regions) where you plan to provision the instance. 

6. Select a resource group. 

    By default, the **Default** resource group is set.

    **Note:** If you are not able to select a resource group, check that you have editing permissions on the resource group where you want to provision the instance.

7. Select the `Lite` service plan. 

    By default, the lite plan is set.

8. Click **Create**.

After you provision an instance, the *Activity Tracker* dashboard opens. 

Next, go to the web UI to view the events in your account. [Learn more](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-view_events).



## Provisioning an instance through the catalog
{: #provision_catalog}

To provision an instance of {{site.data.keyword.at_full_notm}} through the {{site.data.keyword.cloud_notm}} catalog, complete the following steps:

1. [Log in to your {{site.data.keyword.cloud_notm}} account ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/login){:new_window}.

	After you log in with your user ID and password, the {{site.data.keyword.cloud_notm}} UI opens.

2. Click **Catalog**. The list of the services that are available in {{site.data.keyword.cloud_notm}} opens.

3. To filter the list of services that is displayed, select the **Developer Tools** category.

4. Click the **{{site.data.keyword.at_full_notm}}** tile. 

5. Enter a name for the service instance.

6. Select the location where you plan to provision the instance. 

    To get the latest list of locations that are available for the {{site.data.keyword.at_full_notm}} service, see [Locations](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-regions).

7. Select a resource group. 

    By default, the **Default** resource group is set.

    **Note:** If you are not able to select a resource group, check that you have editing permissions on the resource group where you want to provision the instance.

8. Select the `Lite` service plan. 

    By default, the lite plan is set.

9. Click **Create**.

After you provision an instance, the *Activity Tracker* dashboard opens. 

Next, go to the web UI to manage events in your account. [Learn more](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-launch#launch).


## Provisioning an instance through the CLI
{: #provision_cli}

To provision an instance of {{site.data.keyword.at_full_notm}} through the command line, complete the following steps:

1. [Pre-requisite] Installation of the {{site.data.keyword.cloud_notm}} CLI. [Learn more](/docs/cli?topic=cloud-cli-ibmcloud-cli#ibmcloud-cli).

   If the CLI is installed, continue with the next step.

2. Log in to the location in the {{site.data.keyword.cloud_notm}} where you want to provision the instance. Run the following command: [`ibmcloud login`](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login)

    To get the latest list of locations that are available for the {{site.data.keyword.at_full_notm}} service, see [Locations](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-regions).

3. Set the resource group where you want to provision the instance. Run the following command: [`ibmcloud target`](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target)

    By default, the `default` resource group is set.

4. Create the instance. Run the [`ibmcloud resource service-instance-create`](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_commands_resource#ibmcloud_resource_service_instance_create) command:

    ```
    ibmcloud resource service-instance-create NAME logdnaat SERVICE_PLAN_NAME LOCATION
    ```
    {: codeblock}

    Where

    * NAME is the name of the instance

    * The value *logdnaat* is the name of the {{site.data.keyword.at_full_notm}} service in the {{site.data.keyword.cloud_notm}}

    * SERVICE_PLAN_NAME is the type of plan. Valid values are *lite*, *7-days*, *14-days*, *30-days*
    
    * LOCATION is the region where the LogDNA instance is created. To get the latest list of locations that are available for the {{site.data.keyword.at_full_notm}} service, see [Locations](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-regions).

    
For example, to provision an instance with the 7 days retention plan, run the following command:

```
ibmcloud resource service-instance-create logdna-instance-01 logdnaat 7-day us-south
```
{: codeblock}



