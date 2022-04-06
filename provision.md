---

copyright:
  years: 2019, 2022
lastupdated: "2022-03-24"

keywords: IBM Cloud, Activity Tracker, provision instance

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}


# Provisioning an instance
{: #provision}

Before you can monitor and manage event data with {{site.data.keyword.at_full_notm}}, you must provision an instance of the service in {{site.data.keyword.cloud_notm}}.
{: shortdesc}

This information applies only if you use an {{site.data.keyword.at_full}} [hosted event search offering](/docs/activity-tracker?topic=activity-tracker-service_plan).
{: important}

To provision an {{site.data.keyword.at_full_notm}} instance in a Public Cloud region, consider the following information:
* You must select the service plan that is associated with the instance, the region where your events are collected, and the plan that determines the retention period for your events. You can choose from 7, 14, or 30-day retention periods. Alternatively, {{site.data.keyword.at_full_notm}} offers a `Lite` plan that you can use to view your events as they pass through the system. You can view events by using event tailing. You can also design filters to prepare for upgrading to a longer retention period plan. This plan has a 0-day retention period.
* Your user ID must have permissisons to provision a service in a resource group. [Learn more](/docs/services/activity-tracker?topic=activity-tracker-iam#groups).
* You must decide if you want your instance to be accessible through both public and private endpoints, or only private endpoints.


You can only provision 1 instance of the service per {{site.data.keyword.cloud_notm}} region.
{: important}

## Provisioning an instance through the Observability dashboard
{: #provision_ui}

To provision an instance from the Observability dashboard in the {{site.data.keyword.cloud_notm}}, complete the following steps:

1. [Log in to your {{site.data.keyword.cloud_notm}} account](https://cloud.ibm.com/login){: external}.

	After you log in with your user ID and password, the {{site.data.keyword.cloud_notm}} UI opens.

2. Go to the **Menu** icon ![Menu icon](../icons/icon_hamburger.svg). Then, select **Observability** to access the *Observability* dashboard.

3. Select **Activity Tracker**, then click **Create instance**. 

4. Enter a name for the service instance.

5. Select the [location](/docs/services/activity-tracker?topic=activity-tracker-regions) where you plan to provision the instance. 

6. Select a resource group. 

    By default, the **Default** resource group is set.

    **Note:** If you are not able to select a resource group, check that you have editing permissions on the resource group where you want to provision the instance.

7. Select the `Lite` service plan. 

    By default, the lite plan is set.

8. Click **Create**.

After you provision an instance, the *Activity Tracker* dashboard opens. 

Next, go to the web UI to view the events in your account. [Learn more](/docs/services/activity-tracker?topic=activity-tracker-view_events).


## Provisioning an instance through the catalog
{: #provision_catalog}

To provision an instance of {{site.data.keyword.at_full_notm}} through the {{site.data.keyword.cloud_notm}} catalog, complete the following steps:

1. [Log in to your {{site.data.keyword.cloud_notm}} account](https://cloud.ibm.com/login){: external}.

	After you log in with your user ID and password, the {{site.data.keyword.cloud_notm}} UI opens.

2. Click **Catalog**. The list of the services that are available in {{site.data.keyword.cloud_notm}} opens.

3. To filter the list of services that is displayed, select the **Logging and Monitoring** category.

4. Click the **{{site.data.keyword.at_full_notm}}** tile. 

5. Enter a name for the service instance.

6. Select the location where you plan to provision the instance. 

    To get the latest list of locations that are available for the {{site.data.keyword.at_full_notm}} service, see [Locations](/docs/services/activity-tracker?topic=activity-tracker-regions).

7. Select a resource group. 

    By default, the **Default** resource group is set.

    **Note:** If you are not able to select a resource group, check that you have editing permissions on the resource group where you want to provision the instance.

8. Select a service plan. 

    By default, the lite plan is set.

9. Click **Create**.

After you provision an instance, the *Activity Tracker* dashboard opens. 

Next, go to the web UI to manage events in your account. [Learn more](/docs/services/activity-tracker?topic=activity-tracker-launch#launch).

## Configuring your instance to be accessible to private endpoints only
{: #config_private_endpoints}

After provisioning your instance through the Observability dashboard or catalog, you can configure the instance to be accessibile by private endpoints only.

If you configure your instance to use private endpoints only, this will block the public endpoints. All API usage that may be in progress on the public endpoints will be blocked when the configuration change is made.
{: important}

Unless otherwise specified when provisioning an instance, the default is for the instance to be accessible by both public and private endpoints.
{: note}

1. [Log in to your {{site.data.keyword.cloud_notm}} account](https://cloud.ibm.com/login){: external}.

	After you log in with your user ID and password, the {{site.data.keyword.cloud_notm}} dashboard opens.

2. Click the **Menu** icon ![Menu icon](../icons/icon_hamburger.svg) &gt; **Observability**. 

3. Select **Activity Tracker**. 

    The list of {{site.data.keyword.at_full_notm}} instances is displayed.

    There is 1 instance per region.
    {: important}

4. Select the instance in the region where you want to view events. Then, click **Open Dashboard**.

5. Select the **settings** icon. 

6. Click **Organization** &gt; **General**.

7. For **Private endpoints only** select *on* to limit access to the instance to only [private endpoints](/docs/activity-tracker?topic=activity-tracker-endpoints).  Select *off* to allow the instance to be accessed by both [public and private endpoints](/docs/activity-tracker?topic=activity-tracker-endpoints).

## Provisioning an instance through the CLI
{: #provision_cli}

Complete the following steps:

### Step 1. Provision the instance
{: #provision_cli_1}

1. [Pre-requisite] Installation of the {{site.data.keyword.cloud_notm}} CLI. [Learn more](/docs/cli?topic=cli-install-ibmcloud-cli).

2. Log in to the location in the {{site.data.keyword.cloud_notm}} where you want to provision the instance. Run the following command: [ibmcloud login](/docs/cli?topic=cli-ibmcloud_cli#ibmcloud_login)

    To get the latest list of locations that are available for the {{site.data.keyword.at_full_notm}} service, see [Locations](/docs/services/activity-tracker?topic=activity-tracker-regions).

3. Set the resource group where you want to provision the instance. Run the following command: [ibmcloud target](/docs/cli?topic=cli-ibmcloud_cli#ibmcloud_target)

    By default, the `default` resource group is set.

4. Create the instance. Run the [ibmcloud resource service-instance-create](/docs/cli?topic=cli-ibmcloud_commands_resource#ibmcloud_resource_service_instance_create) command:

    ```text
    ibmcloud resource service-instance-create NAME logdnaat SERVICE_PLAN_NAME LOCATION -p '{"private_endpoints_only": PRIVATE_ENDPOINT}'
    ```
    {: codeblock}

    Where

    * `NAME` is the name of the instance

    * `SERVICE_PLAN_NAME` is the type of plan. Valid values are *lite*, *7-day*, *14-day*, *30-day*
    
    * `LOCATION` is the region where the auditing instance is created. To get the latest list of locations that are available for the {{site.data.keyword.at_full_notm}} service, see [Locations](/docs/services/activity-tracker?topic=activity-tracker-regions).

    * `PRIVATE_ENDPOINT` is either `true` or `false`.  If `true` only [private endpoints](/docs/activity-tracker?topic=activity-tracker-endpoints) can be used to access the instance.

       Unless otherwise specified when provisioning an instance, the default is for the instance to be accessible by both public and private endpoints.
       {: note}
    
    For example, to provision an instance with the 7 days retention plan that can be accessed only by private endpoints, run the following command:

    ```text
    ibmcloud resource service-instance-create my-instance logdnaat 7-day us-south -p '{"private_endpoints_only": true}'
    ```
    {: codeblock}

    To provision an instance with the 14 days retention plan that can be accessed only by both public and private endpoints, run one of the following commands:

    ```text
    ibmcloud resource service-instance-create my-instance logdnaat 14-day us-south -p '{"private_endpoints_only": false}'
    ```
    {: codeblock}

    or

    ```text
    ibmcloud resource service-instance-create my-instance logdnaat 14-day us-south    
    ```
    {: codeblock}

### Step 2. Create the credentials for your instance
{: #provision_cli_2}

Run the following command to create a service ID:

```text
ibmcloud resource service-key-create NAME ROLE_NAME --instance-name SERVICE_INSTANCE_NAME
```
{: pre}

Where 

* `SERVICE_INSTANCE_NAME` is the name of the instance that you provisioned in the previous step.
* `NAME` is the name of the service ID. Use the following format to name the key **<SERVICE_INSTANCE_NAME>-key-admin**
* `ROLE_NAME` is the permission that you grant this service ID. Set it to **Manager**.

 
For example, you can run the following command:

```text
ibmcloud resource service-key-create my-instance-key-admin Manager --instance-name my-instance
```
{: pre}

