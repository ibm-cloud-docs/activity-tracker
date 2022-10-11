---

copyright:
  years: 2022
lastupdated: "2022-05-24"

keywords: IBM Cloud, Activity Tracker, security, auditing, target, logdna

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}


# Managing {{site.data.keyword.atracker_full_notm}} hosted event search targets by using the V2 API 
{: #target_v2_at}

You can manage {{site.data.keyword.atracker_full}} hosted event search targets in your account by using the {{site.data.keyword.atracker_full_notm}} CLI or the {{site.data.keyword.atracker_full_notm}} REST API. A target is a resource where you can collect auditing events.
{: shortdesc}

This information applies only if you use {{site.data.keyword.atracker_full}}.
{: important}

The version of the API running in your account can be determined by running the [`ibmcloud atracker init version` command.](/docs/activity-tracker?topic=activity-tracker-v2api)
{: note}

## Understanding how targets work in your account
{: #target_v2at_behavior}

Note the following information about targets:

* You can define up to 16 targets in each account. Each account can have up to 2 default targets.

* The target defines where auditing events are collected. The [route](/docs/activity-tracker?topic=activity-tracker-route_v2) defines what auditing events are collected in a target.

* A target can be either an {{site.data.keyword.cos_full_notm}} (COS) bucket or the {{site.data.keyword.atracker_full_notm}} hosted event search offering.

* Targets are created within a region but are visible across regions. That is, all targets can be accessed by any {{site.data.keyword.atracker_full}} API endpoint.

The following table outlines valid target types:

| Target                                      | Type                     |
|---------------------------------------------|--------------------------|
| {{site.data.keyword.cos_full_notm}} (COS) | `cloud_object_storage`   |
| {{site.data.keyword.atracker_full_notm}} hosted event search offering | `logdna`   |
{: caption="Table 1. List of targets" caption-side="top"}

For information on creating an {{site.data.keyword.cos_full_notm}} (COS) target, see [managing COS targets by using the V2 API](/docs/activity-tracker?topic=activity-tracker-target_v2_cos).

## IAM Access
{: #target_v2_iam_access_at}

Users must have the following [{{site.data.keyword.atracker_full}} IAM roles](/docs/account?topic=account-assign-access-resources) to work with targets. Users with regional IAM scope will be limited to access targets in their authorized region.

| Role | Minimum scope | Minimum required roles | Action
| -------------- | -------------- | -------- | -------------- |
| `atracker.target.read` | Region | `Administrator`  \n `Editor`  \n `Viewer`  \n `Operator` | Read (view) information about a target |
| `atracker.target.create` | Region | `Administrator`  \n `Editor` | Create a target |
| `atracker.target.update` | Region | `Administrator`  \n `Editor` | Update a target |
| `atracker.target.delete` | Region | `Administrator`  \n `Editor` | Delete a target |
| `atracker.target.list` | Account | `Administrator`  \n `Editor`  \n `Viewer`  \n `Operator` | List all targets |
{: caption="Table 1. Required IAM roles}




## CLI prerequisites
{: #target_prereqs_at}
{: cli}

Before you use the CLI to manage targets, complete the following steps:

1. [Install the {{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cli-install-ibmcloud-cli).

2. [Install the {{site.data.keyword.atracker_full_notm}} CLI](/docs/activity-tracker?topic=activity-tracker-activity-tracking-cli#activity-tracking-cli-prereq).

3. Log in to the region in the {{site.data.keyword.cloud_notm}} where the instance is running. Run the following command: [ibmcloud login](/docs/cli?topic=cli-ibmcloud_cli#ibmcloud_login)


## Creating an {{site.data.keyword.atracker_full_notm}} hosted event search offering target using the CLI
{: #target-create-cli-at}
{: cli}

Use this command to create an {{site.data.keyword.atracker_full_notm}} hosted event search offering target to be used to configure a destination for activity events.

```sh
ibmcloud atracker target create --name TARGET_NAME --type TARGET_TYPE ( [--file LOGDNA_ENDPOINT_DEFINITION_JSON_FILE] | ( [--target-crn LOGDNA_TARGET_CRN] [--ingestion-key LOGDNA_INGESTION_KEY] ) ) [--region REGION] [--output FORMAT]
```
{: pre}

### Command options
{: #target-create-options-at}

`--region REGION` | `-r REGION`
:   Name of the region, for example, `us-south` or `eu-gb`. If not specified, the region logged into, or targeted, will be used.

`--name TARGET_NAME`
:   The name to be given to the target.

    Do not include any personal identifying information (PII) in any resource names.
    {: important}

`--type TARGET_TYPE`
:   Set the `TARGET_TYPE` to `logdna` for an IBM Cloud Activity Tracker hosted event search offering target.

`--file @LOGDNA_ENDPOINT_DEFINITION_JSON_FILE`
:   A file containing an endpoint definition in the following format:

    ```json
    {
      "target_crn": "yyyyy",
      "ingestion_key": "xxxxxx"
    }
    ```
    {: codeblock}

`--target-crn LOGDNA_TARGET_CRN`
:   The CRN of the {{site.data.keyword.atracker_full_notm}} hosted event search offering instance.

`--ingestion-key LOGDNA_INGESTION_KEY`
:   `LOGDNA_INGESTION_KEY` is the ingestion key that will be used to gain access to the {{site.data.keyword.atracker_full_notm}} instance.

`--output FORMAT`
:   Currently support format is JSON. If specified, output will be returned in JSON format.  If `JSON` is not specified, output will be returned in a tabular format.

`help` | `--help` | `-h`
:   List options available for the command.

### Example
{: #target-create-example-at}

The following is an example using the **`ibmcloud atracker target create --name eu-de-logdna-target --type logdna --target-crn "crn:v1:bluemix:public:logdna:eu-de:a/11111111111111111111111111111111:22222222-2222-2222-2222-222222222222::" --ingestion-key xxxxxx`** command.

This example shows an example successful target creation.
{: note}

```text
OK
Target
Name:                eu-de-logdna-target
ID:                  cccccccc-cccc-cccc-cccc-cccccccccccc
CRN:                 crn:v1:bluemix:public:atracker:eu-de:a/11111111111111111111111111111111::target:cccccccc-cccc-cccc-cccc-cccccccccccc
Type:                logdna
LogDNA Target CRN:   crn:v1:bluemix:public:logdna:eu-de:a/11111111111111111111111111111111:22222222-2222-2222-2222-222222222222::
CreatedAt:           2022-05-06T18:59:26.760Z
UpdatedAt:           2022-05-06T18:59:26.760Z
```
{: screen}


## Updating an {{site.data.keyword.atracker_full_notm}} hosted event search offering target using the CLI
{: #target-update-cli-at}
{: cli}

Use this command to update an {{site.data.keyword.atracker_full_notm}} hosted event search offering target to be used to configure a destination for activity events.

```sh
ibmcloud atracker target update --target TARGET [--name TARGET_NAME] ( --file @LOGDNA_ENDPOINT_DEFINITION_JSON_FILE ) | (--target-crn LOGDNA_TARGET_CRN --ingestion-key LOGDNA_INGESTION_KEY )  [--region REGION] [--output FORMAT]
```
{: pre}

### Command options
{: #target-update-options-at}

`--target TARGET`
:   The ID or current target name.

`--region REGION` | `-r REGION`
:   Name of the region, for example, `us-south` or `eu-gb`. If not specified, the region logged into, or targeted, will be used.

`--name TARGET_NAME`
:   The name to be given to the target.

    Do not include any personal identifying information (PII) in any resource names.
    {: important}

`--file @LOGDNA_ENDPOINT_DEFINITION_JSON_FILE`
:   A file containing an endpoint definition in the following format:

    ```json
    {
      "target_crn": "yyyyy",
      "ingestion_key": "xxxxxx"
    }
    ```
    {: codeblock}

`--target-crn LOGDNA_TARGET_CRN`
:   The CRN of the {{site.data.keyword.atracker_full_notm}} hosted event search offering instance.

`--ingestion-key LOGDNA_INGESTION_KEY`
:   `LOGDNA_INGESTION_KEY` is the ingestion key for the {{site.data.keyword.atracker_full_notm}} instance.

`--output FORMAT`
:   Currently support format is JSON. If specified, output will be returned in JSON format.  If `JSON` is not specified, output will be returned in a tabular format.

`help` | `--help` | `-h`
:   List options available for the command.

### Example
{: #target-update-example-at}

The following is an example using the **`ibmcloud atracker target update --name eu-de-logdna-target --target-crn "crn:v1:bluemix:public:logdna:eu-de:a/11111111111111111111111111111111:22222222-2222-2222-2222-222222222222::" --ingestion-key xxxxxx`** command.

This example shows an example successful target update.
{: note}

```text
OK
Target
Name:                eu-de-logdna-target
ID:                  cccccccc-cccc-cccc-cccc-cccccccccccc
CRN:                 crn:v1:bluemix:public:atracker:eu-de:a/11111111111111111111111111111111::target:cccccccc-cccc-cccc-cccc-cccccccccccc
Type:                logdna
LogDNA Target CRN:   crn:v1:bluemix:public:logdna:eu-de:a/11111111111111111111111111111111:22222222-2222-2222-2222-222222222222::
CreatedAt:           2022-05-06T18:59:26.760Z
UpdatedAt:           2022-05-06T19:16:50.090Z
```
{: screen}

## Deleting a target using the CLI
{: #target-delete-cli-at}
{: cli}

Use this command to delete a target.

```sh
ibmcloud atracker target rm --target TARGET [--force]
```
{: pre}

### Command options
{: #target-rm-options-at}

`--target TARGET`
:   The ID or name of the target.

`--force` | `-f`
:   Will delete the target without providing the user with any additional prompt.

`help` | `--help` | `-h`
:   List options available for the command.

### Example
{: #target-rm-example-at}

The following is an example using the **`ibmcloud atracker target rm --target xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx`** command.

```text
Are you sure you want to remove the target with target ID xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx? [y/N]>y
OK
Target with target ID xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx was successfully removed.
```
{: screen}

The following is an example using the **`ibmcloud atracker target rm --target xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx -force`** command.

This example shows a failed command where the specified target could not be found.
{: note}

```text
Are you sure you want to remove the Target bearing Target ID 33333333-3333-3333-3333-333333333333? [y/N]> y
FAILED
Something went wrong. Error:
 Status Code:  404
 Incident ID:  67a33257-d5a4-46ec-94d9-14eb70e94f3d
 Code:         not_found
 Message:      The target id specified in `target_id` field is not found.
```
{: screen}

## Validating a target using the CLI
{: #target-validate-cli-at}
{: cli}

Use this command to validate that a target is correctly configured for an {{site.data.keyword.atracker_full_notm}} region.

```sh
ibmcloud atracker target validate --target TARGET [--region REGION] [--output FORMAT]
```
{: pre}

### Command options
{: #target-validate-options-at}

`--target TARGET`
:   The ID or name of the target.

`--region REGION` | `-r REGION`
:   Name of the region, for example, `us-south` or `eu-gb`. If not specified, the region logged into, or targeted, will be used.

`--output FORMAT`
:   Currently support format is JSON. If specified, output will be returned in JSON format.  If `JSON` is not specified, output will be returned in a tabular format.

`help` | `--help` | `-h`
:   List options available for the command.

### Example
{: #target-validate-example-at}

The following is an example using the **`ibmcloud atracker target validate --target new-target-name`** command.

This example shows a successfully validated {{site.data.keyword.atracker_full_notm}} hosted event search target.
{: note}

```text
TBD
```
{: screen}

## Getting information about a target using the CLI
{: #target-get-cli-at}
{: cli}

Use this command to get information about a target for an {{site.data.keyword.atracker_full_notm}} region.

```sh
ibmcloud atracker target get --target TARGET [--output FORMAT]
```
{: pre}

### Command options
{: #target-get-options-at}

`--target TARGET`
:   The ID or name of the target.

`--output FORMAT`
:   Currently support format is JSON. If specified, output will be returned in JSON format.  If `JSON` is not specified, output will be returned in a tabular format.

`help` | `--help` | `-h`
:   List options available for the command.

### Example
{: #target-get-example-at}

The following is an example using the **`ibmcloud atracker target get --target new-target-name`** command showing an {{site.data.keyword.atracker_full_notm}} hosted event search target.

```text
OK
Target
Name:                new-target-name
ID:                  cccccccc-cccc-cccc-cccc-cccccccccccc
CRN:                 crn:v1:bluemix:public:atracker:eu-de:a/11111111111111111111111111111111::target:cccccccc-cccc-cccc-cccc-cccccccccccc
Type:                logdna
LogDNA Target CRN:   crn:v1:bluemix:public:logdna:eu-de:a/11111111111111111111111111111111:22222222-2222-2222-2222-222222222222::
CreatedAt:           2022-05-06T18:59:26.760Z
UpdatedAt:           2022-05-06T19:16:50.090Z
```
{: screen}

## Listing all targets in a region
{: #target-list-cli-at}
{: cli}

Use this command to list the configured targets for an {{site.data.keyword.atracker_full_notm}} region.

```sh
ibmcloud atracker target ls [--output FORMAT]
```
{: pre}

### Command options
{: #target-options-at}

`--output FORMAT`
:   Currently support format is JSON. If specified, output will be returned in JSON format.  If `JSON` is not specified, output will be returned in a tabular format.

`help` | `--help` | `-h`
:   List options available for the command.

### Example
{: #target-example-at}

The following is an example using the **`ibmcloud atracker target ls`** command.

```text
Name                       ID                                     Region     Type                     Created
test-eu-de-target           xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx   eu-de   logdna     2022-02-26T06:53:13.466Z
```
{: screen}


## API targets and actions
{: #target-actions-api-at}
{: api}

The following table lists the actions that you can run to manage targets:

| Action                     | REST API Method  | API_URL                                          |
|----------------------------|------------------|--------------------------------------------------|
| Create a target            | `POST`           | `<ENDPOINT>/api/v2/targets`              |
| Update a target            | `PUT`            | `<ENDPOINT>/api/v2/targets/<TARGET_ID>`  |
| Delete a target            | `DELETE`         | `<ENDPOINT>/api/v2/targets/<TARGET_ID>`  |
| Read a target              | `GET`            | `<ENDPOINT>/api/v2/targets/<TARGET_ID>`  |
| List all targets           | `GET`            | `<ENDPOINT>/api/v2/targets`             |
| Validate a target          | `POST`           | `<ENDPOINT>/api/v2/targets/{id}/validate` |
{: caption="Table 2. Target actions by using the {{site.data.keyword.atracker_full_notm}} REST API" caption-side="top"}

You can use private and public endpoints to manage targets. For more information about the list of `ENDPOINTS` that are available, see [Endpoints](/docs/activity-tracker?topic=activity-tracker-endpoints).

* You can manage targets from the private network using an API endpoint with the following format: `https://private.REGION.atracker.cloud.ibm.com`
* You can manage targets from the public network using an API endpoint with the following format: `https://REGION.atracker.cloud.ibm.com`

* You can disable the public endpoints by updating the account settings. For more information, see [Configuring target and region settings](/docs/activity-tracker?topic=activity-tracker-settings).

For more information about the REST API, see [Targets](https://{DomainName}/apidocs/atracker/atracker-v2#create-target){: external}.
{: note}


## API prerequisites
{: #target-prereqs-api-at}
{: api}

To make API calls to manage targets, complete the following steps:
1. Get an IAM access token. For more information, see [Retrieving IAM access tokens](/docs/activity-tracker?topic=activity-tracker-retrieve-iam-token).
2. Identify the API endpoint in the region where you plan to configure or manage a target. For more information, see [Endpoints](/docs/activity-tracker?topic=activity-tracker-endpoints#endpoints_api).





## Creating a {{site.data.keyword.atracker_full_notm}} hosted event search offering target using the API
{: #target-create-api-at-at}
{: api}

You can use the following cURL command to create an {{site.data.keyword.atracker_full_notm}} hosted event search offering target:

```shell
curl -X POST <ENDPOINT>/api/v2/targets
  -H "Authorization: Bearer IAM_TOKEN"
  -H 'content-type: application/json'
  -d '{
       "name": "TARGET_NAME",
       "target_type": "TARGET_TYPE",
       "logdna_endpoint": {
         "target_crn": "TARGET_CRN",
         "ingestion_key": "TARGET_KEY"
        }
      }
```
{: codeblock}

Where

- `<ENDPOINT>` is the API endpoint in the region where you plan to configure or manage a target. For more information, see [Endpoints](/docs/activity-tracker?topic=activity-tracker-endpoints#endpoints_api).
- `TARGET_NAME` is the name of the target. The maximum length of the name is 256 characters.

    Do not include any personal identifying information (PII) in any resource names.
    {: important}

- `TARGET_TYPE` is the type of the target. The valid type is `logdna`.
- `logdna_endpoint` includes information about the target. This includes the CRN of the {{site.data.keyword.atracker_full_notm}} hosted event search offering instance and the ingestion key of the instance.

    `TARGET_CRN` indicates the [CRN](/docs/account?topic=account-crn) of the {{site.data.keyword.atracker_full_notm}} instance.

    `TARGET_KEY` is the ingestion key for the {{site.data.keyword.atracker_full_notm}} instance.


For example, you can use the following cURL request to create a target in Dallas:

```shell
curl -X POST https://private.us-south.atracker.cloud.ibm.com/api/v2/targets -H "Authorization:  $ACCESS_TOKEN" -H "content-type: application/json" -d '{
     "name": "a-target-us-south",
       "target_type": "logdna",
         "logdna_endpoint": {
           "target_crn": "crn:v1:staging:public:logdna:us-south:a/11111111111111111111111111111111:22222222-2222-2222-2222-222222222222::",
           "ingestion_key": "xxxxxxxxxxxxxxxxxx"
    }
  }'
```
{: screen}

In the response, you get information about the target such as the `id`, that indicates the GUID of the target, and the `crn`, that indicates the CRN of the target.




## Updating an {{site.data.keyword.atracker_full_notm}} hosted event search offering target
{: #target-update-at-api-at}
{: api}

When you update an {{site.data.keyword.atracker_full_notm}} hosted event search offering target, you must include the target information in the data section of the request.
- You must pass all fields.
- Update the fields that need to be changed.

You can use the following cURL command to update an {{site.data.keyword.atracker_full_notm}} hosted event search offering target:

```shell
curl -X PUT <ENDPOINT>/api/v2/targets
  -H "Authorization: Bearer IAM_TOKEN"
  -H 'content-type: application/json'
  -d '{
       "name": "TARGET_NAME",
       "target_type": "TARGET_TYPE",
       "logdna_endpoint": {
         "target_crn": "TARGET_CRN",
         "ingestion_key": "TARGET_KEY"
        }
      }'
```
{: codeblock}

Where

- `<ENDPOINT>` is the API endpoint in the region where you plan to configure or manage a target. For more information, see [Endpoints](/docs/activity-tracker?topic=activity-tracker-endpoints#endpoints_api).
- `TARGET_NAME` is the name of the target. The maximum length of the name is 256 characters.

    Do not include any personal identifying information (PII) in any resource names.
    {: important}

- `TARGET_TYPE` is the type of the target. The valid type is `logdna`.
- `logdna_endpoint` includes information about the target. This includes the CRN of the {{site.data.keyword.atracker_full_notm}} hosted event search offering instance and the ingestion key of the instance.

    `TARGET_CRN` indicates the [CRN](/docs/account?topic=account-crn) of the {{site.data.keyword.atracker_full_notm}} instance.

    `TARGET_KEY` is the ingestion key for the {{site.data.keyword.atracker_full_notm}} instance.


For example, you can use the following cURL request to update a target in Dallas:

```shell
curl -X PUT https://private.us-south.atracker.cloud.ibm.com/api/v2/targets -H "Authorization:  $ACCESS_TOKEN" -H "content-type: application/json" -d '{
     "name": "a-target-us-south",
       "target_type": "logdna",
         "logdna_endpoint": {
           "target_crn": "crn:v1:staging:public:logdna:us-south:a/11111111111111111111111111111111:22222222-2222-2222-2222-222222222222::",
           "ingestion_key": "xxxxxxxxxxxxxxxxxx"
    }
  }'
```
{: screen}


## Deleting a target using the API
{: #target-delete-api-at}
{: api}

You can use the following cURL command to delete a target:

```text
curl -X DELETE <ENDPOINT>/api/v2/targets/TARGET_ID -H "Authorization: $ACCESS_TOKEN" -H "content-type: application/json"
```
{: codeblock}

Where

- `<ENDPOINT>` is the API endpoint in the region where you plan to configure or manage a target. For more information, see [Endpoints](/docs/activity-tracker?topic=activity-tracker-endpoints#endpoints_api).
- `TARGET_ID` is the ID of the target.


## Validating a target using the API
{: #target-validate-api-at}
{: api}

You can use the following cURL command to validate a target by checking the credentials to write to the target.

```shell
curl -X POST <ENDPOINT>/api/v2/targets/TARGET_ID/validate -H "Authorization: $ACCESS_TOKEN" -H "content-type: application/json"
```
{: codeblock}

Where

- `<ENDPOINT>` is the API endpoint in the region where you plan to configure or manage a target. For more information, see [Endpoints](/docs/activity-tracker?topic=activity-tracker-endpoints#endpoints_api).
- `TARGET_ID` is the ID of the target.

For example, you can use the following cURL request to validate a target in US-South:

```shell
curl -X POST https://private.us-south.atracker.cloud.ibm.com/api/v2/targets/<TARGET_ID>/validate   -H "Authorization: $ACCESS_TOKEN" -H "content-type: application/json"
```
{: screen}

In the response, you get information in the section `cos_write_status`, for example:

```json
"write_status": {
    "status": "success"
  },
```
{: screen}


## Viewing a target using the API
{: #target-view-api-at}
{: api}

You can use the following cURL command to view the configuration details of 1 target:

```shell
curl -X GET <ENDPOINT>/api/v2/targets/TARGET_ID -H "Authorization: $ACCESS_TOKEN" -H "content-type: application/json"
```
{: codeblock}

Where

- `<ENDPOINT>` is the API endpoint in the region where you plan to configure or manage a target. For more information, see [Endpoints](/docs/activity-tracker?topic=activity-tracker-endpoints#endpoints_api).
- `TARGET_ID` is the ID of the target.


For example, you can run the following cURL request to get information about a target with the ID `00000000-0000-0000-0000-000000000000`:

```shell
curl -X GET https://private.us-south.atracker.cloud.ibm.com/api/v2/targets/00000000-0000-0000-0000-000000000000 -H "Authorization: $ACCESS_TOKEN" -H "content-type: application/json"
```
{: screen}

Results will show if the target is a [COS (`"target_type": "cloud_object_storage"`)](/docs/activity-tracker?topic=activity-tracker-target_v2_cos) target or an {{site.data.keyword.atracker_full_notm}} hosted event search offering (`"target_type": "logdna"`) target.

## Listing all targets using the API
{: #target-list-targets-at}
{: api}

You can use the following cURL command to view all targets:

```shell
curl -X GET <ENDPOINT>/api/v2/targets -H "Authorization: $ACCESS_TOKEN" -H "content-type: application/json"
```
{: codeblock}

Where

- `<ENDPOINT>` is the API endpoint in the region where you plan to configure or manage a target. For more information, see [Endpoints](/docs/activity-tracker?topic=activity-tracker-endpoints#endpoints_api).


For example, you can run the following cURL request to get information about the targets that are defined in Dallas:

```shell
curl -X GET https://private.us-south.atracker.cloud.ibm.com/api/v2/targets -H "Authorization: $ACCESS_TOKEN" -H "content-type: application/json"
```
{: screen}

Results will show if the target is COS (`"target_type": "cloud_object_storage"`) or an {{site.data.keyword.atracker_full_notm}} hosted event search offering (`"target_type": "logdna"`).


## HTTP response codes
{: #target-rc-api-at}
{: api}

When you use the {{site.data.keyword.atracker_full_notm}} REST API, you can get standard HTTP response codes to indicate whether a method completed successfully.

- A 200 response always indicates success.
- A 4xx response indicates a failure.
- A 5xx response usually indicates an internal system error.

See the following table for some HTTP response codes:

| Status code | Status | Description |
|-------------|--------|-------------|
| `200` |	OK | The request was successful. |
| `201` |	OK | The request was successful. A resource is created. |
| `400` | Bad Request |	The request was unsuccessful. You might be missing a parameter that is required. |
| `401` |	Unauthorized | The IAM token that is used in the API request is invalid or expired. |
| `403` |	Forbidden | The operation is forbidden due to insufficient permissions. |
| `404` | Not Found |	The requested resource doesn't exist or is already deleted. |
| `429` |	Too Many Requests |	Too many requests hit the API too quickly. |
| `500` |	Internal Server Error |	Something went wrong in {{site.data.keyword.atracker_full_notm}} processing. |
{: caption="Table 3. List of HTTP response codes" caption-side="top"}

