---

copyright:
  years: 2019, 2022
lastupdated: "2021-08-09"

keywords: IBM Cloud, Activity Tracker, logging, web UI, observability

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}


# Changing the service plan of an instance
{: #upgrade}

When you provision an instance of the {{site.data.keyword.at_full_notm}} service, you must choose a service plan. Different plans offer different features. You can change the service plan at any time.
{: shortdesc}

This information applies only if you use an {{site.data.keyword.at_full}} [hosted event search offering](/docs/activity-tracker?topic=activity-tracker-service_plan).
{: important}

[Learn more about service plans](/docs/activity-tracker?topic=activity-tracker-service_plan).

## Changing the service plan through the Observability dashboard
{: #upgrade_ui}

To change the service plan of an instance from the Observability dashboard in the {{site.data.keyword.cloud_notm}}, complete the following steps:

1. Log in to your [{{site.data.keyword.cloud_notm}} account](https://cloud.ibm.com/login){: external}.

   After you log in with your user ID and password, the {{site.data.keyword.cloud_notm}} UI opens.

2. Go to the menu icon ![menu icon](../icons/icon_hamburger.svg) and select **Observability** to access the *Observability* dashboard.

3. Select **Activity Tracker**.

4. Click the **Actions** icon ![Actions icon](../icons/action-menu-icon.svg) for the instance you want to change and select **Edit plan**. 

5. Select a service plan. 

6. Click **Save**.

## Changing the service plan through the CLI
{: #upgrade_cli}

Complete the following steps to change the service plan:

1. Install the {{site.data.keyword.cloud_notm}} CLI. [Learn more](/docs/cli?topic=cli-getting-started).

2. Log in to the location in the {{site.data.keyword.cloud_notm}} where the instance is provisioned. Run the following command: [ibmcloud login](/docs/cli?topic=cli-ibmcloud_cli#ibmcloud_login)

   To get the latest list of locations that are available for the {{site.data.keyword.at_full_notm}} service, see [Locations](/docs/services/activity-tracker?topic=activity-tracker-regions).

3. Set the resource group where the instance is available. Run the following command: [ibmcloud target](/docs/cli?topic=cli-ibmcloud_cli#ibmcloud_target)

   By default, the `default` resource group is set.

4. Get the current service plan ID.

   To get the current service plan of an instance, you can run the following command and check the value of the **resource_plan_id** field:

   ```text
   ibmcloud resource service-instance INSTANCE_NAME --output JSON
   ```
   {: codeblock}

5. Change the service plan. Run the [ibmcloud resource service-instance-update](/docs/cli?topic=cli-ibmcloud_commands_resource#ibmcloud_resource_service_instance_create) command:

   ```text
   ibmcloud resource service-instance-update NAME --service-plan-id RESOURCE_PLAN_ID
   ```
   {: codeblock}

   Where

   * `NAME` is the name of the instance

   * `service-plan-id` indicates the type of plan.

   * `RESOURCE_PLAN_ID` is the ID of the plan that you want to set. To get the service plan IDs, see [Service plans](/docs/activity-tracker?topic=activity-tracker-service_plan).
    

For example, to change the service plan of an instance to the 7 days retention plan, run the following command:

```text
ibmcloud resource service-instance-update logdna-instance-01 9aae7491-5cb6-43eb-9b7a-3e0456c781f0
```
{: codeblock}

