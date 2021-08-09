---
 
copyright:
  years: 2019, 2021
lastupdated: "2021-08-09"

subcollection: atracker

keywords: IBM Cloud ATracker CLI, IBM Cloud ATracker command line, IBM Cloud ATracker terminal, IBM Cloud ATracker shell

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}


# {{site.data.keyword.atracker_full_notm}} event routing CLI
{: #activity-tracking-cli}

The {{site.data.keyword.cloud}} command-line interface (CLI) provides extra capabilities for service offerings. This information describes how you can use the CLI to interact with {{site.data.keyword.atracker_full}} event routing.
{: shortdesc} 

This information applies only if you use the {{site.data.keyword.atracker_full}} event routing.
{: important}

## Prerequisites
{: #activity-tracking-cli-prereq}

* Install the [{{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cli-getting-started).
* Install the CLI by running the following command:

   ```sh
   ibmcloud plugin install atracker
   ```
   {: pre}

You're notified on the command line when updates to the {{site.data.keyword.cloud_notm}} CLI and plug-ins are available. Be sure to keep your CLI up to date so that you can use the latest commands. You can view the current version of all installed plug-ins by running `ibmcloud plugin list`.
{: tip}

Whether the `atracker` API uses public or private endpoints depends on the CLI API connection setting.  Use the `ibmcloud api` command to determine which will be used.  If the `ibmcloud api` command returns `https://cloud.ibm.com`, then the `atracker` plug-in uses the public API.  If the `ibmcloud api` command returns `https://private.cloud.ibm.com`, then the `atracker` private API will be used. 
{: note}

## ibmcloud atracker endpoint api ls
{: #activity-tracking-endpoint-ls}

Use this command to list the {{site.data.keyword.atracker_full_notm}} service API endpoints.

```sh
ibmcloud atracker endpoint api ls [--output JSON]
```
{:pre}

### Command options 
{: #activity-tracking-endpoint-ls-options}

<dl>
<dt>--output JSON</dt>
<dd>If specified, output will be returned in JSON format.  If `JSON` is not specified, output will be returned in a tabular format.</dd> 
<dt>help | --help | -h</dt>
<dd>List options available for the command.</dd>
</dl>
  
### Example
{: #activity-tracking-endpoint-ls-example}

The following is an example using the **`ibmcloud atracker endpoint api ls`** command.

```
Listing the IBM Cloud Activity Tracking service API endpoints....
OK
Region     Public Endpoint                           Private Endpoint
eu-gb      https://eu-gb.atracker.cloud.ibm.com      https://private.eu-gb.atracker.cloud.ibm.com
eu-de      https://eu-de.atracker.cloud.ibm.com      https://private.eu-de.atracker.cloud.ibm.com
us-south   https://us-south.atracker.cloud.ibm.com   https://private.us-south.atracker.cloud.ibm.com
```
{: screen}

## ibmcloud atracker endpoint api get
{: #activity-tracking-endpoint-get}

Use this command to view detailed information about a region's {{site.data.keyword.atracker_full_notm}} service API endpoint.

```sh
ibmcloud atracker endpoint api get [--region <REGION>] [--output JSON]
```
{:pre}

### Command options 
{: #activity-tracking-endpoint-get-options}

<dl>
<dt>--region &lt;REGION&gt; | -r &lt;REGION&gt;</dt>
<dd>Name of the region, for example, `us-south` or `eu-gb`. If not specified, the region logged into, or targeted, will be used.</dd>
<dt>--output JSON</dt>
<dd>If specified, output will be returned in JSON format.  If `JSON` is not specified, output will be returned in a tabular format.</dd> 
<dt>help | --help | -h</dt>
<dd>List options available for the command.</dd>
</dl>
  
### Example
{: #activity-tracking-endpoint-get-example}

The following is an example using the **`ibmcloud atracker endpoint api get --region us-south`** command.

```
API endpoints for region us-south
Public URL:                         https://us-south.atracker.cloud.ibm.com
Public Enabled:                     true
Private URL:                        https://private.us-south.atracker.cloud.ibm.com
Private Enabled:                    true

```
{: screen}

## ibmcloud atracker endpoint api update
{: #activity-tracking-endpoint-update}

Use this command to update an {{site.data.keyword.atracker_full_notm}} service API endpoint.

```sh
ibmcloud atracker endpoint api update --public-enabled ( TRUE | FALSE ) [--region <REGION>] [--output JSON] [--force]
```
{:pre}

Before disabling a public endpoint (`--public-enabled FALSE`), make sure your account has access to the private endpoint.  You can do this by running the command `ibmcloud account show`.  If `VRF Enabled` is `true` and `Service Endpoint Enabled` is `true` then you have access to the private endpoint.  If you do not have access to the private endpoint, you will be unable to re-enable the public endpoint since private endpoint access is required to re-enable the public endpoint.
{: important}

### Command options 
{: #activity-tracking-endpoint-update-options}

<dl>
<dt>--public-enabled (TRUE | FALSE)</dt>
<dd>Specifies if the public endpoint is available or not.  If TRUE, the endpoint is enabled for use.</dd>
<dt>--region &lt;REGION&gt; | -r &lt;REGION&gt;</dt>
<dd>Name of the region, for example, `us-south` or `eu-gb`. If not specified, the region logged into, or targeted, will be used.</dd>
<dt>--output JSON</dt>
<dd>If specified, output will be returned in JSON format.  If `JSON` is not specified, output will be returned in a tabular format.</dd>
<dt>--force</dt>
<dd>The command will be run without prompting the user whether or not to continue with the command.</dd> 
<dt>help | --help | -h</dt>
<dd>List options available for the command.</dd>
</dl>
  
### Example
{: #activity-tracking-endpoint-update-example}

The following is an example using the **`ibmcloud atracker endpoint api update --public-enabled false`** command.

```
Are you sure you want to update the IBM Cloud Activity Tracking service endpoint settings for your account? [y/N]> y
OK
API endpoints for region us-south
Public URL:                         https://us-south.atracker.cloud.ibm.com
Public Enabled:                     false
Private URL:                        https://private.us-south.atracker.cloud.ibm.com
Private Enabled:                    true
```
{: screen}

## ibmcloud atracker target create
{: #activity-tracking-target-create}

Use this command to create an {{site.data.keyword.atracker_full_notm}} service target to be used to configure a destination for activity events.

```sh
 ibmcloud atracker target create --name <TARGET_NAME> --type <TARGET_TYPE> ( --file <COS_ENDPOINT_DEFINITION_JSON_FILE> |  --endpoint <COS_ENDPOINT> --bucket <COS_BUCKET> --target-crn <COS_TARGET_CRN> --api-key ( <COS_API_KEY> | <@COS_API_KEY_FILE> ) ) [--region <REGION>] [--output JSON]
```
{:pre}

### Command options 
{: #activity-tracking-target-create-options}

<dl>
<dt>--region &lt;REGION&gt; | -r &lt;REGION&gt;</dt>
<dd>Name of the region, for example, `us-south` or `eu-gb`. If not specified, the region logged into, or targeted, will be used.</dd>
<dt>--name &lt;TARGET_NAME&gt;</dt>
<dd>The name to be given to the target.</dd>
<dt>--type &lt;TARGET_TYPE&gt;</dt>
<dd>Only supported value for &lt;TARGET_TYPE&gt; is `cloud-object-storage`.</dd>
<dt>--file &lt;@COS_ENDPOINT_DEFINITION_JSON_FILE&gt;</dt>
<dd>A file containing an endpoint definition in the following format:
<code>
{
  "endpoint": "aaaaa", 
  "target_crn": "yyyyy",
  "bucket": "zzzzzz", 
  "api_key": "xxxxxx"
}
</code></dd>
<dt>--endpoint &lt;COS_ENDPOINT&gt;</dt>
<dd>The {{site.data.keyword.cos_full_notm}} endpoint to be associated with the {{site.data.keyword.cos_full_notm}} bucket.</dd>
<dt>--bucket &lt;BUCKET&gt;</dt>
<dd>The name of the {{site.data.keyword.cos_full_notm}} bucket to be associated with the target.</dd>
<dt>--target-crn &lt;COS_TARGET_CRN&gt;</dt>
<dd>The CRN of the {{site.data.keyword.cos_full_notm}} instance.</dd>
<dt>--api-key &lt;COS_API_KEY&gt; | &lt;@COS_API_KEY_FILE&gt;</dt>
<dd>Your [API key](/docs/account?topic=account-manapikey) value or a reference to the API Key file used when logging in.  For example, `ibmcloud login --apikey $KEYFILE`</dd>
<dt>--output JSON</dt>
<dd>If specified, output will be returned in JSON format.  If `JSON` is not specified, output will be returned in a tabular format.</dd> 
<dt>help | --help | -h</dt>
<dd>List options available for the command.</dd>
</dl>
  
### Example
{: #activity-tracking-target-create-example}

The following is an example using the **`ibmcloud atracker target create --name my-target --type cloud-object-storage --endpoint s3.us-west.cloud-object-storage.appdomain.cloud --bucket cloud-object-storage-my-cos --target-crn crn:v1:staging:public:cloud-object-storage:global:a/xxxxxxxxxx:xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxx:: --api-key yyyyyyyyyyyyyyyyyyyyyyyyyyyyy`** command.

This example shows an example successful target creation.
{: note}

```
Target
Name:               my-target
ID:                 000000000-00000000-0000-0000-00000000
CRN:                crn:v1:staging:public:atracker:us-south:a/xxxxxxxxxx:xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxx
Type:               cloud_object_storage
COS Endpoint:       s3.us-west.cloud-object-storage.appdomain.cloud
COS Target CRN:     crn:v1:staging:public:cloud-object-storage:global:a/xxxxxxxxxx:xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxx:
COS Bucket:         cloud-object-my-target
COS API Key:        REDACTED
COS Write Status:   success
Created:            2021-07-21T16:04:15.174Z
Updated:            2021-07-21T16:04:15.174Z
```
{: screen}

## ibmcloud atracker target ls
{: #activity-tracking-target-ls}

Use this command to list the configured targets for an {{site.data.keyword.atracker_full_notm}} region.

```sh
ibmcloud atracker target ls [--region <REGION>] [--output JSON]
```
{:pre}

### Command options 
{: #activity-tracking-target-options}

<dl>
<dt>--region &lt;REGION&gt; | -r &lt;REGION&gt;</dt>
<dd>Name of the region, for example, `us-south` or `eu-gb`. If not specified, the region logged into, or targeted, will be used.</dd>
<dt>--output JSON</dt>
<dd>If specified, output will be returned in JSON format.  If `JSON` is not specified, output will be returned in a tabular format.</dd> 
<dt>help | --help | -h</dt>
<dd>List options available for the command.</dd>
</dl>
  
### Example
{: #activity-tracking-target-example}

The following is an example using the **`ibmcloud atracker target ls`** command.

```
Name                       ID                                     Region     Type                     Created
target-01                  xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx   us-south    cloud_object_storage     2020-11-18T03:52:08.603Z
target-02                  xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx   us-south    cloud_object_storage     2020-11-18T03:52:01.592Z
target-02-backup           xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx   us-south   cloud_object_storage     2021-02-26T06:53:13.466Z
```
{: screen}



## ibmcloud atracker target update
{: #activity-tracking-target-update}

Use this command to update a target for an {{site.data.keyword.atracker_full_notm}} region.  Any specified value that is different from when the target was originally created will be updated to the value specified in the command.

```sh
ibmcloud atracker target update --target <TARGET> [--name <TARGET_NAME>] [ --file <COS_ENDPOINT_DEFINITION_JSON_FILE> |  [--endpoint <COS_ENDPOINT>] [--bucket <COS_BUCKET>] [--target-crn <COS_TARGET_CRN>] [--api-key ( <COS_API_KEY> | <@COS_API_KEY_FILE> )] ) ] [--region <REGION>] [--output JSON]
```
{:pre}

### Command options 
{: #activity-tracking-target-update-options}

<dl>
<dt>--target &lt;TARGET&gt;</dt>
<dd>The ID or current target name.</dd>
<dt>--region &lt;REGION&gt; | -r &lt;REGION&gt;</dt>
<dd>Name of the region, for example, `us-south` or `eu-gb`. If not specified, the region logged into, or targeted, will be used.</dd>
<dt>--name &lt;TARGET_NAME&gt;</dt>
<dd>The name to be given to the target.</dd>
<dt>--file &lt;@COS_ENDPOINT_DEFINITION_JSON_FILE&gt;</dt>
<dd>A file containing an endpoint definition in the following format:
<code>
{
  "endpoint": "aaaaa", 
  "target_crn": "yyyyy",
  "bucket": "zzzzzz", 
  "api_key": "xxxxxx"
}
</code></dd>
<dt>--endpoint &lt;COS_ENDPOINT&gt;</dt>
<dd>The {{site.data.keyword.cos_full_notm}} endpoint to be associated with the {{site.data.keyword.cos_full_notm}} bucket.</dd>
<dt>--bucket &lt;COS_BUCKET&gt;</dt>
<dd>The name of the {{site.data.keyword.cos_full_notm}} bucket to be associated with the target.</dd>
<dt>--target-crn &lt;COS_TARGET_CRN&gt;</dt>
<dd>The CRN of the {{site.data.keyword.cos_full_notm}} instance.</dd>
<dt>--api-key &lt;COS_API_KEY&gt; | &lt;@COS_API_KEY_FILE&gt;</dt>
<dd>Your [API key](/docs/account?topic=account-manapikey) value or a reference to the API Key file used when logging in.  For example, `ibmcloud login --apikey $KEYFILE`</dd>
<dt>--output JSON</dt>
<dd>If specified, output will be returned in JSON format.  If `JSON` is not specified, output will be returned in a tabular format.</dd> 
<dt>help | --help | -h</dt>
<dd>List options available for the command.</dd>
</dl>
  
### Example
{: #activity-tracking-target-update-example}

The following is an example using the **`ibmcloud atracker target update --target my-target --name new-target-name `** command.

```
Target
Name:               new-target-name
ID:                 xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
CRN:                crn:v1:staging:public:atracker:us-south:a/xxxxxxxxxx:xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxx
Type:               cloud_object_storage
COS Endpoint:       s3.us-west.cloud-object-storage.appdomain.cloud
COS Target CRN:     crn:v1:staging:public:cloud-object-storage:global:a/xxxxxxxxxx:xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxx:
COS Bucket:         cloud-object-my-target
COS API Key:        REDACTED
COS Write Status:   success
Created:            2021-07-21T16:04:15.174Z
Updated:            2021-07-21T17:49:56.452Z
```
{: screen}

## ibmcloud atracker target get
{: #activity-tracking-target-get}

Use this command to get information about a target for an {{site.data.keyword.atracker_full_notm}} region. 

```sh
ibmcloud atracker target get --target <TARGET> [--region <REGION>] [--output JSON]
```
{:pre}

### Command options 
{: #activity-tracking-target-get-options}

<dl>
<dt>--target &lt;TARGET&gt;</dt>
<dd>The ID or name of the target.</dd>
<dt>--region &lt;REGION&gt; | -r &lt;REGION&gt;</dt>
<dd>Name of the region, for example, `us-south` or `eu-gb`. If not specified, the region logged into, or targeted, will be used.</dd>
<dt>--output JSON</dt>
<dd>If specified, output will be returned in JSON format.  If `JSON` is not specified, output will be returned in a tabular format.</dd> 
<dt>help | --help | -h</dt>
<dd>List options available for the command.</dd>
</dl>
  
### Example
{: #activity-tracking-target-get-example}

The following is an example using the **`ibmcloud atracker target get --target new-target-name`** command.

```
Target
Name:               new-target-name
ID:                 xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
CRN:                crn:v1:staging:public:atracker:us-south:a/xxxxxxxxxx:xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxx
Type:               cloud_object_storage
COS Endpoint:       s3.us-west.cloud-object-storage.appdomain.cloud
COS Target CRN:     crn:v1:staging:public:cloud-object-storage:global:a/xxxxxxxxxx:xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxx:
COS Bucket:         cloud-object-my-target
COS API Key:        REDACTED
COS Write Status:   success
Created:            2021-07-21T16:04:15.174Z
Updated:            2021-07-21T17:49:56.452Z
```
{: screen}

## ibmcloud atracker target rm
{: #activity-tracking-target-rm}

Use this command to delete a target for an {{site.data.keyword.atracker_full_notm}} region. 

```sh
ibmcloud atracker target rm --target <TARGET> [--region <REGION>] [--force]
```
{:pre}

### Command options 
{: #activity-tracking-target-rm-options}

<dl>
<dt>--target &lt;TARGET&gt;</dt>
<dd>The ID or name of the target.</dd>
<dt>--region &lt;REGION&gt; | -r &lt;REGION&gt;</dt>
<dd>Name of the region, for example, `us-south` or `eu-gb`. If not specified, the region logged into, or targeted, will be used.</dd>
<dt>--force</dt>
<dd>Will delete the target without providing the user with any additional prompt.</dd>
<dt>help | --help | -h</dt>
<dd>List options available for the command.</dd>
</dl>
  
### Example
{: #activity-tracking-target-rm-example}

The following is an example using the **`ibmcloud atracker target rm --region us-east --target xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx`** command.

```
Are you sure you want to remove the target with target ID xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx? [y/N]>y
OK
Target with target ID xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx was successfully removed.
```
{: screen}

The following is an example using the **`ibmcloud atracker target rm --region us-east --target xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx -force`** command.

This example shows a failed command where the specified target could not be found.
{: note}

```
FAILED
Something went wrong. Error: Delete "https://us-east.atracker.cloud.ibm.com/api/v1/targets/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx": dial tcp: lookup us-east.atracker.cloud.ibm.com: no such host
```
{: screen}

## ibmcloud atracker target validate
{: #activity-tracking-target-validate}

Use this command to validate that a target is correctly configured for an {{site.data.keyword.atracker_full_notm}} region. 

```sh
ibmcloud atracker target validate --target <TARGET> [--region <REGION>] [--output JSON]
```
{:pre}

### Command options 
{: #activity-tracking-target-validate-options}

<dl>
<dt>--target &lt;TARGET&gt;</dt>
<dd>The ID or name of the target.</dd>
<dt>--region &lt;REGION&gt; | -r &lt;REGION&gt;</dt>
<dd>Name of the region, for example, `us-south` or `eu-gb`. If not specified, the region logged into, or targeted, will be used.</dd>
<dt>--output JSON</dt>
<dd>If specified, output will be returned in JSON format.  If `JSON` is not specified, output will be returned in a tabular format.</dd>
<dt>help | --help | -h</dt>
<dd>List options available for the command.</dd>
</dl>
  
### Example
{: #activity-tracking-target-validate-example}

The following is an example using the **`ibmcloud atracker target validate --target new-target-name`** command.

This example shows a successfully validated target.
{: note}

```
Target
Name:               new-target-name
ID:                 xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
CRN:                crn:v1:staging:public:atracker:us-south:a/xxxxxxxxxx:xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxx
Type:               cloud_object_storage
COS Endpoint:       s3.us-west.cloud-object-storage.appdomain.cloud
COS Target CRN:     crn:v1:staging:public:cloud-object-storage:global:a/xxxxxxxxxx:xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxx:
COS Bucket:         cloud-object-my-target
COS API Key:        REDACTED
COS Write Status:   success
Created:            2021-07-21T16:04:15.174Z
Updated:            2021-07-21T17:49:56.452Z
```
{: screen}

## ibmcloud atracker route create
{: #activity-tracking-route-create}

Use this command to create a new route for an {{site.data.keyword.atracker_full_notm}} target in a region. 

```sh
ibmcloud atracker route create --name <ROUTE_NAME> --target <TARGET> [--receive-global-events] [--region <REGION>] [--output JSON]
```
{:pre}

### Command options 
{: #activity-tracking-route-create-options}

<dl>
<dt>--target &lt;TARGET_ID&gt;</dt>
<dd>The ID or name of the target.</dd>
<dt>--region &lt;REGION&gt; | -r &lt;REGION&gt;</dt>
<dd>Name of the region, for example, `us-south` or `eu-gb`. If not specified, the region logged into, or targeted, will be used.</dd>
<dt>--name &lt;ROUTE_NAME&gt;</dt>
<dd>The name to be given to the route.</dd>
<dt>--receive-global-events</dt>
<dd>Specifies that the route will receive [global events](/docs/activity-tracker?topic=activity-tracker-event_types#event_types_global).  If not specified, global events will not be sent on the route</dd>
<dt>--output JSON</dt>
<dd>If specified, output will be returned in JSON format.  If `JSON` is not specified, output will be returned in a tabular format.</dd>
<dt>help | --help | -h</dt>
<dd>List options available for the command.</dd>
</dl>
  
### Example
{: #activity-tracking-route-create-example}

The following is an example using the **`ibmcloud atracker route create --name my_route --target xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx --receive-global-events`** command.

```
Route
Name:                    my_route
ID:                      xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
CRN:                     crn:v1:staging:public:atracker:us-south:a/xxxxxxxxxxxxxxxxxxxxxxxxxxxxx::route:xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
Receive Global Events:   true
Version:                 0
Rules:                   [*: [b1ea1ad9-71ac-493e-abb1-1261f9110b07]]
Created:                 2021-07-21T18:10:44.456Z
Updated:                 2021-07-21T18:10:44.456Z
```
{: screen}

## ibmcloud atracker route ls
{: #activity-tracking-route-ls}

Use this command to list all the configured routes for a specific {{site.data.keyword.atracker_full_notm}} region or all {{site.data.keyword.atracker_full_notm}} regions. 

```sh
ibmcloud atracker route ls [--region <REGION> | --all-regions ] [--output JSON]
```
{:pre}

### Command options 
{: #activity-tracking-route-ls-options}

<dl>
<dt>--region &lt;REGION&gt; | -r &lt;REGION&gt;</dt>
<dd>Name of the region, for example, `us-south` or `eu-gb`. If not specified, the region logged into, or targeted, will be used.</dd>
<dt>--all-regions</dt>
<dd>Specifies the routes for all regions should be listed.  This option cannot be specified if `--region` is specified.</dd>
<dt>--output JSON</dt>
<dd>If specified, output will be returned in JSON format.  If `JSON` is not specified, output will be returned in a tabular format.</dd> 
<dt>help | --help | -h</dt>
<dd>List options available for the command.</dd>
</dl>
  
### Example
{: #activity-tracking-route-ls-example}

The following is an example using the **`ibmcloud atracker route ls --region us-south`** command which returns the routes for all regions.

```
Name       ID                                     Region     Receive Global Events   Version   Created                    Updated
my_route   xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx   us-south   true                    0         2021-07-21T18:10:44.456Z   2021-07-21T18:10:44.456Z
```
{: screen}


## ibmcloud atracker route update
{: #activity-tracking-route-update}

Use this command to update a route for an {{site.data.keyword.atracker_full_notm}} target in a region.  Any specified value that is different from when the route was originally created will be updated to the value specified in the command.

```sh
ibmcloud atracker route update --route <ROUTE> [--name <ROUTE_NAME>] [--receive-global-events ( TRUE | FALSE )] [--target <TARGET>] [--region <REGION>] [--output JSON]
```
{:pre}

### Command options 
{: #activity-tracking-route-update-options}

<dl>
<dt>--route &lt;ROUTE&gt;</dt>
<dd>The name or ID of the route to be updated.</dd>
<dt>--target &lt;TARGET&gt;</dt>
<dd>The ID or name of the target.</dd>
<dt>--region &lt;REGION&gt; | -r &lt;REGION&gt;</dt>
<dd>Name of the region, for example, `us-south` or `eu-gb`. If not specified, the region logged into, or targeted, will be used.</dd>
<dt>--name &lt;ROUTE_NAME&gt;</dt>
<dd>The name to be given to the route.</dd>
<dt>--receive-global-events (TRUE | FALSE)</dt>
<dd>Specifies that the route will receive [global events](/docs/activity-tracker?topic=activity-tracker-event_types#event_types_global).  If not specified, global events will not be sent on the route</dd>
<dt>--output JSON</dt>
<dd>If specified, output will be returned in JSON format.  If `JSON` is not specified, output will be returned in a tabular format.</dd>
<dt>help | --help | -h</dt>
<dd>List options available for the command.</dd>
</dl>
  
### Example
{: #activity-tracking-route-update-example}

The following is an example using the **`ibmcloud atracker route update --route my_route --receive-global-events false`** command.

```
Route
Name:                    my_route
ID:                      xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
CRN:                     crn:v1:staging:public:atracker:us-south:a/xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx::route:xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
Receive Global Events:   false
Version:                 1
Rules:                   [*: [b1ea1ad9-71ac-493e-abb1-1261f9110b07]]
Created:                 2021-07-21T18:10:44.456Z
Updated:                 2021-07-21T18:33:48.898Z
```
{: screen}

## ibmcloud atracker route get
{: #activity-tracking-route-get}

Use this command to get information about a route for an {{site.data.keyword.atracker_full_notm}} region. 

```sh
ibmcloud atracker route get --route [ <ROUTE_ID> | <ROUTE_NAME> ] [--region <REGION>] [--output JSON]
```
{:pre}

### Command options 
{: #activity-tracking-route-get-options}

<dl>
<dt>--route &lt;ROUTE_ID&gt; | &lt;ROUTE_NAME&gt;</dt>
<dd>The route ID or name of the route.</dd>
<dt>--region &lt;REGION&gt; | -r &lt;REGION&gt;</dt>
<dd>Name of the region, for example, `us-south` or `eu-gb`. If not specified, the region logged into, or targeted, will be used.</dd>
<dt>--output JSON</dt>
<dd>If specified, output will be returned in JSON format.  If `JSON` is not specified, output will be returned in a tabular format.</dd> 
<dt>help | --help | -h</dt>
<dd>List options available for the command.</dd>
</dl>
  
### Example
{: #activity-tracking-route-get-example}

The following is an example using the **`ibmcloud atracker route get --route my_route --output json`** command.

```
{
  "id": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
  "name": "my_route",
  "crn": "crn:v1:staging:public:atracker:us-south:a/xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx::route:xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
  "version": 1,
  "receive_global_events": false,
  "rules": [
    {
      "target_ids": [
        "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
      ]
    }
  ],
  "created": "2021-07-21T18:10:44.456Z",
  "updated": "2021-07-21T18:33:48.898Z"
}
```
{: screen}


## ibmcloud atracker route rm
{: #activity-tracking-route-rm}

Use this command to delete a route for an {{site.data.keyword.atracker_full_notm}} region. 

```sh
ibmcloud atracker route rm --route <ROUTE> [--region <REGION>] [--force]
```
{:pre}

### Command options 
{: #activity-tracking-route-rm-options}

<dl>
<dt>--route &lt;ROUTE&gt;</dt>
<dd>The name or ID of the route to be deleted.</dd>
<dt>--region &lt;REGION&gt; | -r &lt;REGION&gt;</dt>
<dd>Name of the region, for example, `us-south` or `eu-gb`. If not specified, the region logged into, or targeted, will be used.</dd>
<dt>--force</dt>
<dd>Will delete the route without providing the user with any additional prompt.</dd>
<dt>help | --help | -h</dt>
<dd>List options available for the command.</dd>
</dl>
  
### Example
{: #activity-tracking-route-rm-example}

The following is an example using the **`ibmcloud atracker route rm --route my_route`** command.

```
Are you sure you want to remove the route with the route ID xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx [y/N]> y
OK
Route with route ID xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx was successfully removed.
```
{: screen}

The following is an example using the **`ibmcloud atracker route rm --route my_route --force`** command.

This example shows a failed command where the specified route could not be found.
{: note}

```
FAILED
Something went wrong. Error: No route found with route name - my_route.
```
{: screen}

## ibmcloud atracker config report
{: #activity-tracking-config-report}

Use this command to return a report about the {{site.data.keyword.atracker_full_notm}} service configuration which includes any issues in the configuration. 

```sh
ibmcloud atracker config report --output YAML 
```
{:pre}

### Command options 
{: #activity-tracking-config-report-options}

<dl>
<dt>--output YAML</dt>
<dd>Output will be returned in YAML format.  This option is required.</dd> 
<dt>help | --help | -h</dt>
<dd>List options available for the command.</dd>
</dl>
  
### Example
{: #activity-tracking-config-report-example}

The following is an example using the **`ibmcloud atracker config report`** command with a report containing configuration warnings.

```
OK
summary: 'The IBM Cloud Activity Tracking service configuration has detected some warnings. Review the warnings section for details. '
warnings:
- No route is defined to receive global events.
- No route is defined for the us-south region. All IBM Cloud Activity Tracking service events are forwarded to LogDNA for that region.
config-report:
- region: us-south
```
{: screen}




