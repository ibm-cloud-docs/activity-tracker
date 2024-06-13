---

copyright:
  years: 2019, 2023
lastupdated: "2022-05-23"

keywords:

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}

# Working with ingestion keys
{: #ingestion_key}

The ingestion key is a security key that you must use to forward auditing events to your {{site.data.keyword.at_short}} instance in {{site.data.keyword.cloud}}. The ingestion key is created automatically when you provision an instance. Alternatively, you can also obtain the ingestion key by creating a service ID for the instance.
{: shortdesc}



* To work with ingestion keys through the {{site.data.keyword.at_short}} Web UI, you must have an IAM policy with platform role **Viewer** and service role **Manager** for the {{site.data.keyword.at_short}} service.
* To work with ingestion keys through the {{site.data.keyword.cloud_notm}} UI, you must have an IAM policy with platform role **Editor** and service role **Manager** for the {{site.data.keyword.at_short}} service.



## Getting the ingestion key through the {{site.data.keyword.at_short}} web UI
{: #log_analysis_ui}
{: ui}

To get the ingestion key for an {{site.data.keyword.at_short}} instance by using the {{site.data.keyword.at_short}} web UI, complete the following steps:

1. [Go to the Activity Tracker web UI.](/docs/activity-tracker?topic=activity-tracker-launch).

2. Click the **Settings** icon ![Settings icon](/images/admin.png) &gt; **Organization** &gt; **API keys**.

    You can see the ingestion keys that are enabled.

3. Copy the ingestion key displayed in the **API keys** section.


## Getting the ingestion key through the CLI
{: #ingestion_key_cli}
{: cli}

To get the ingestion key for a auditing instance through the command line, complete the following steps:

1. [Pre-requisite] [Install the {{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cli-install-ibmcloud-cli).

2. Log in to the {{site.data.keyword.cloud_notm}} region where the auditing instance is by running the following command: [ibmcloud login](/docs/cli?topic=cli-ibmcloud_cli#ibmcloud_login).

3. Set the resource group where the auditing instance by running the following command: [ibmcloud target](/docs/cli?topic=cli-ibmcloud_cli#ibmcloud_target)

    By default, the `default` resource group is set.

4. Get the instance name by running the following command: [ibmcloud resource service-instances](/docs/cli?topic=cli-ibmcloud_commands_resource#ibmcloud_resource_service_instances)

    ```text
    ibmcloud resource service-instances
    ```
    {: pre}

5. Get the name of the key that is associated with the auditing instance by running the [ibmcloud resource service-keys](/docs/cli?topic=cli-ibmcloud_commands_resource#ibmcloud_resource_service_keys) command:

    ```text
    ibmcloud resource service-keys --instance-name INSTANCE_NAME
    ```
    {: pre}

    where INSTANCE_NAME is the name of the instance that you obtained in the previous step.

6. Get the ingestion key by running the [ibmcloud resource service-key](/docs/cli?topic=cli-ibmcloud_commands_resource#ibmcloud_resource_service_key) command:

    ```text
    ibmcloud resource service-key APIKEY_NAME
    ```
    {: pre}

    where APIKEY_NAME is the name of the API key.

    The output from this command includes the field **ingestion key** that contains the ingestion key for the instance.


## Getting the ingestion key through the API
{: #ingestion_key_api}
{: api}

To get the ingestion key for a auditing instance through the API, complete the following steps:

1. Generate an [{{site.data.keyword.cloud_notm}} API key](/docs/account?topic=account-userapikey&interface=api#create_user_key).

2. Get an access token. For more information, see [Generating an {{site.data.keyword.cloud_notm}} access token by using an API key](/docs/account?topic=account-iamtoken_from_apikey&interface=api).

    You need an IAM access token to authenticate in {{site.data.keyword.cloud_notm}}.

    To generate an IAM access token, run the following command:

    ```text
    curl -X POST 'https://iam.cloud.ibm.com/identity/token' -H 'Content-Type: application/x-www-form-urlencoded' -d 'grant_type=urn:ibm:params:oauth:grant-type:apikey&apikey=<MY_APIKEY>'
    ```
    {: pre}

    Replace `<MY_APIKEY>` with your API key from the previous step.

    The access token is only valid for 1 hour. The `access_token` includes the string "Bearer" followed by the IAM token.
    {: important}

3. Get the name and GUID of the service instance if you do not already have it.

    To get the list of resource instances, run the following:

    ```text
    curl -X GET   https://resource-controller.cloud.ibm.com/v2/resource_instances   -H "Authorization: Bearer <ACCESS_TOKEN>"
    ```
    {: pre}

    Where `<ACCESS_TOKEN>` is the IAM access token obtained in the prior step.

    Look for the returned `guid` field to get the instance GUID.

4. Get the ingestion key by running the following cURL command:

    ```shell
    curl -X POST  https://resource-controller.cloud.ibm.com/v2/resource_keys   -H "Authorization: Bearer <ACCESS_TOKEN>"   -H 'Content-Type: application/json'  -d '{"name": "<RESOURCE_KEY_NAME>", "source": "<INSTANCE_GUID>"}'
    ```
    {: pre}

    Where

    - `<ACCESS_TOKEN>` is the IAM access token obtained in a prior step.

    - `<INSTANCE_GUID>` is the instance GUID obtained in the prior step.

    - `<RESOURCE_KEY_NAME>` is the name that you give the resource key associated to the instance.

    The result will include a section with the following information:

    ```json
    "credentials": {
        "apikey": "xxxxxxxxxxxx",
        "iam_apikey_description": "Auto-generated for key xxxxxxxx",
        "iam_apikey_name": "<RESOURCE_KEY_NAME>",
        "iam_serviceid_crn": ".....",
        "ingestion_key": "xxxxxxx",
        "service_key": "xxxxxxxxxx"
    }
    ```
    {: codeblock}

    The `ingestion_key` value is the ingestion key.



## Resetting the ingestion key through the UI
{: #reset}
{: ui}

If the ingestion key is compromised, or you have a policy to renew it after a number of days, you can generate a new key and delete the old one.

To renew the ingestion key for an {{site.data.keyword.at_short}} instance by using the {{site.data.keyword.at_short}} Web UI, complete the following steps:

1. [Launch the {{site.data.keyword.at_short}} web UI](/docs/log-analysis?topic=log-analysis-view_logs#view_logs_step2).

2. Click the **Settings** icon ![Settings icon](/images/admin.png) &gt; **Organization**.

3. Select **API keys**.

    You can see the ingestion keys that are enabled.

4. Select **Generate Ingestion Key**.

    A new key is added to the list.

5. Delete the old ingestion key. Click **X** next to the ingestion key to be deleted.

## Resetting the ingestion key using the CLI
{: #reset_cli}
{: cli}

You can only reset the ingestion key using the [web UI.](/docs/activity-tracker?topic=activity-tracker-ingestion_key&interface=ui#reset)

## Resetting the ingestion key using the API
{: #reset_api}
{: api}

You can only reset the ingestion key using the [web UI.](/docs/activity-tracker?topic=activity-tracker-ingestion_key&interface=ui#reset)
