---

copyright:
  years: 2019, 2023
lastupdated: "2022-11-02"

keywords:

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}

# Removing an instance
{: #remove}

You can remove an instance of the {{site.data.keyword.at_full_notm}} service from the {{site.data.keyword.cloud_notm}} UI or through the command line.
{: shortdesc}

## Considerations if you are using archiving
{: #remove_archiving}

If you are using [archiving](/docs/activity-tracker?topic=activity-tracker-archiving-ov), make sure all archiving has completed and that you have stopped archiving before you remove your instance. Removing an instance while archiving is still active can result in archive records being lost.

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

1. [Pre-requisite] Install the {{site.data.keyword.cloud_notm}} CLI.

   For more information, see [Installing the {{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cli-install-ibmcloud-cli).

2. Log in to {{site.data.keyword.cloud_notm}}. Run the following command: [ibmcloud login](/docs/cli?topic=cli-ibmcloud_cli#ibmcloud_login)

3. Get information about the instance that you plan to delete.

    ```text
    ibmcloud resource service-instance INSTANCE-NAME --output JSON
    ```
    {: codeblock}

4. Remove any service key associated with the instance.

    Find the service keys that are associated with an instance:

    ```text
    ibmcloud resource service-keys --instance-id INSTANCE-GUID
    ```
    {: codeblock}

    Run the following command to delete 1 service key. You must delete all.

    ```text
    ibmcloud resource service-key-delete SERVICE-KEY-NAME
    ```
    {: codeblock}

5. Remove the instance. Run the [ibmcloud resource service-instance-delete](/docs/cli?topic=cli-ibmcloud_commands_resource#ibmcloud_resource_service_instance_delete) command:

    ```text
    ibmcloud resource service-instance-delete NAME
    ```
    {: codeblock}

    Where NAME is the name of the instance.

    For example, to remove an instance, run the following command:

    ```text
    ibmcloud resource service-instance-delete logging-instance-01
    ```
    {: codeblock}



For example, to remove an instance, run the following command:

```text
ibmcloud resource service-instance-delete logdna-instance-01
```
{: codeblock}

Next, remove permissions that are granted to users to work with the instance that you deleted.
