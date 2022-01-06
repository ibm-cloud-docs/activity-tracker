---

copyright:
  years: 2019, 2022
lastupdated: "2021-11-17"

keywords: IBM Cloud, Activity Tracker, api

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}

# Managing views and alerts programmatically
{: #config-api}

You can use the *Configuration REST API* to manage programmatically views and alerts.
{: shortdesc}

This information applies only if you use an {{site.data.keyword.at_full}} [hosted event search offering](/docs/activity-tracker?topic=activity-tracker-service_plan).
{: important}


- You can use the **POST** method to create a view, or create a view and attach an alert to it.
- You can use the **GET** method to get all existing views and alerts.
- You can use the **PUT** method to modify an existing view, and alerts that are attached to views.
- You can use the **DELETE** method to delete a view and associated alerts.

Before you run any automated tasks, consider doing a back up of your account configuration resources. You can use the back up to restore the resources, to the state before any change is applied, if you encounter problems. See [Export the configuration of resources in an auditing instance](/docs/activity-tracker?topic=activity-tracker-reuse_resource_definitions#rrd_export_config).
{: tip}


## Before you begin
{: #config-api-work}

### Creating views
{: #config-api-work-create-views}

When you create a view, consider the following information:
- You can create a view with no alerts. 
- You can create a view with 1 or more notification channels. Valid alert notification channels that are supported by the *Configuration* API are: email, webhook, or PagerDuty.
- The response to an API request to create a view includes the ID of the view.
- The `name` body parameter, that defines the name of the view, is always required.
- A category must exist before you create a view. The request fails if a category is not valid or is not specified.
- You can define body parameters to refine the data that is displayed through the view. You must specify 1 or more of the following body parameters: query, apps, levels, hosts, or tags.

When you create a PagerDuty notification channel, consider the following information:
- You must manually configure the integration with PagerDuty. 
- You must provide the PagerDuty API key. 

After you create a view, check the view in the UI. 
1. Refresh the browser to see the view listed in the *Views* section. 
2. Select the view to display it.
3. Check the data that is available through the view is the one that you expect.

    - If you do not see any data, check that data is being generated for the auditing events that you are planning to monitor through this view. For example, you can check the **Everything** view and look for events. 

    - If data is being generated, and you still cannot see any data, check the body parameter values that you have defined for the view. One of them might be set to the wrong value and the search criteria does not find any matching events. 

If you try to create a view without defining a category, you get the following error message:

```text
{"details":[{"message":"\"category[0]\" is not allowed to be empty","key":"category[0]"}],"error":"\"category[0]\" is not allowed to be empty","code":"BadRequest","status":"error"}
```
{: screen}

If you try to create a view without a valid category, you get the following error message:

```text
{"error":"Invalid category name(s): CATEGORYNAME","code":"BadRequest","status":"error"}
```
{: screen}

If you try to define a view and you do not define any of the following body parameters, query, hosts, apps, levels, tags, you can get the following error:

```text
{"details":[{"message":"\"value\" must contain at least one of [query, hosts, apps, levels, tags]","key":"value"}],"error":"\"value\" must contain at least one of [query, hosts, apps, levels, tags]","code":"BadRequest","status":"error"}
```
{: screen}

### Getting views
{: #config-api-work-get-views}

When you retrieve all the views and alerts for the instance using the GET method, consider the following information:

* The GET method will return all configured views and associated alerts for the instance.
* The data returned can be imported into a different instance to create the same views and alerts in that instance.

   If presets are defined, importing the data received from the GET method will fail.
   {: note


### Modifying views
{: #config-api-work-modify-views}

When you modify a view, consider the following information:
- You must specify the name and the view ID of the view. 
- If you are viewing a view in the UI, the view is not refreshed automatically after you run an API request to modify the view. To refresh the view in the UI, you must navigate to the `Everything` view and back to the view.

An API request to modify a view replaces the existing view definition and associated alerts with your request body data. Any properties that are not specified in your PUT request will be removed.
{: important}

If the `viewid` that you are trying to modify does not exist, a response similar to the following will be returned: 

```text
{"error":"Nothing to configure","code":"BadRequest","status":"error"}
```
{: screen}

### Deleting views
{: #config-api-work-delete-views}

When you delete a view, consider the following information:
- You must specify the ID of the view that you plan to delete.
- You delete the view and all the alerts that are configured for the view.


## API methods
{: #config-api-methods}

The following table outlines the actions that you can run to manage views and alerts programmatically:

| Action                                                                  | Request  | URL                                  |
| ------------------------------------------------------------------------|----------|--------------------------------------|
| Create a view and attach an alert to a view.                            | `POST`   | `<ENDPOINT>/v1/config/view`          |
| Get all configured views and alerts                            | `GET`   | `<ENDPOINT>/v1/config/view`          |
| Modify an existing view and the alerts that are attached to the view.   | `PUT`    | `<ENDPOINT>/v1/config/view/<VIEWID>` |
| Delete a view and its associated alerts.                                | `DELETE` | `<ENDPOINT>/v1/config/view/<VIEWID>` |
{: caption="Table 1. Configuration API endpoints" caption-side="top"}

Where `<VIEWID>` represents the ID of a view.

## Endpoint URL
{: #config-api-endpoint}

Depending on [your account settings](/docs/account?topic=account-service-endpoints-overview), you can use public or private endpoints to manage views and alerts programmatically. For information about endpoints per region, see [API endpoints](/docs/activity-tracker?topic=activity-tracker-endpoints#endpoints_api).


## Authentication
{: #config-api-authentication}

When you manage views and alerts programmatically, you must use a service key. Authorization to the Configuration API is enforced by using a service key.
{: note} 

A service key is a unique code that is passed in an API request to identify the calling application or user. The service key is specific to an auditing instance. For more information on how to generate a service key, see [Managing service keys](/docs/activity-tracker?topic=activity-tracker-service_keys).

Use of the Configuration REST API is done by adding a valid service key to the HTTP Authorization request header. You must pass the service key as a header parameter (`-H`) of your requests.

For example, in a cURL request, you must set the `content-type` header as follows:

```text
-H 'servicekey: <SERVICE_KEY>'
```
{: codeblock}


## Additional headers 
{: #config-api-headers}

Some additional headers might be required to make successful requests to the API. Those additional headers are:

### content-type
{: #config-api-headers-content-type}

Define the `Content-Type` header to make successful requests to the API. The `content-type` header specifies that the request body is in JSON format.
{: note}

You must pass the `content-type` in the header parameter (`-H`) of your requests.

For example, in a cURL request, you must set the `content-type` header as follows:

```text
-H 'content-type: application/json'
```
{: codeblock}



## Body parameters
{: #config-api-parm}

The following fields are body parameters that you can set in API request:

### name (string)
{: #config-api-parm-name}

Specifies the name of the view.

The following table indicates when the `name` parameter is required:

| Action                                                                | Request  | Field required                       |
| ----------------------------------------------------------------------|----------|--------------------------------------|
| Create a view and attach an alert to a view.                          | `POST`   | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating required")|
| Modify an existing view and the alerts that are attached to the view. | `PUT`    | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating required")|
| Get all configured views and alerts                            | `GET`   | |
| Delete a view and its associated alerts.                              | `DELETE` |  |
{: caption="Table 2. Required status per method" caption-side="top"}


### query (string)
{: #config-api-parm-query}

Specifies the search query that is applied to the view.

Check the query in the UI to validate that the data that is displayed through the view matches the data entry that you plan to monitor through that view.
{: tip}

### hosts (array of strings)
{: #config-api-parm-hosts}

Specifies the list of services from which you want to view data.

In the UI, the value that is set for **Source** in the **Line identifiers** section corresponds to the hosts value of the service that generates that auditing event.

For example, to enter multiple hosts, you must separate the hosts with a comma:

```text
"hosts": ["is", "event-streams"]
```
{: codeblock}



### apps (array of strings)
{: #config-api-parm-apps}

Specifies the service instance ID that generates the auditing event.

For example, to enter multiple apps, you must separate the apps with a comma:

```text
"apps": ["apps1", "apps2"]
```
{: codeblock}

Notice that the apps value for global auditing events is the CRN of the account where the event is generated.


### channels (array of objects)
{: #config-api-parm-channels}

Specifies the notification channels and trigger conditions that are associated with a view.
- You can configure 1 or more channels per view.
- You can configure any of the following channels through the *Configuration* API: email, webhook, PagerDuty.

```json
"channels": [
    {
      "integration": "email",
      "emails": ["LIST OF EMAILS"],    // array of strings (emails) that are comma-separated
      "triggerlimit": 15,
      "triggerinterval": "5m",
      "immediate": true,
      "terminal": true,
      "operator": "presence",
      "timezone": "TIMEZONE"
    },
    {
      "integration": "webhook",
      "url": "WEBHOOK_URL",
      "triggerlimit": 25,
      "triggerinterval": "30",
      "operator": "presence",
      "immediate": true,
      "terminal": true,
      "method": "post",
      "headers": {
        "X-MY-HEADER": "My Header Value"
      },
      "bodyTemplate": {
        "my_log_lines": "{{ lines }}"
      }
    },
    {
      "integration": "pagerduty",
      "key": "PAGERDUTY_KEY",
      "triggerlimit": 150,
      "triggerinterval": "15m",
      "operator": "absence",
      "immediate": false,
      "terminal": true
    }
  ]
```
{: codeblock}

### category (array of strings)
{: #config-api-parm-category}

Specifies the classification of views. 
- You can include a view in 1 or more categories.

For example, to associate a view to a category named `My category`, you can set it as follows:

```json
"category": ["My category"],
```
{: codeblock}



## Examples of using the Configuration API
{: #config-api-samples}

The following are examples of how to use the Configuration API.

A category must exist before you create a view. In these examples, replace `<MY_CATEGORY>` with your category. 
{: note}

In these examples, `<SERVICE_KEY>` is the [service key](/docs/activity-tracker?topic=activity-tracker-service_keys) for your {{site.data.keyword.at_full_notm}} instance. 

### Creating a view
{: #config-api-create-view}

The following sample creates a view.

```text
curl https://api.us-south.logging.cloud.ibm.com/v1/config/view \
  -H 'content-type: application/json' \
  -H 'servicekey: <SERVICE_KEY>' \
  -d '{
  "name": "My RC 200",
  "query": "reason.reasonCode:200",
  "hosts": ["ibm-cloud-databases-prod"],
  "category": ["<MY_CATEGORY>"]
}'
```
{: pre}

A response similar to the following will be returned:

```text
{"name":"My RC 200","query":"reason.reasonCode:200","hosts":["ibm-cloud-databases-prod"],"category":["89610d13a7"],"viewid":"VIEWID"}
```
{: screen}




### Creating a view and attaching an alert
{: #config-api-create-view-alert}

The following sample creates a view and associates an email alert with the view.

```text
curl https://api.eu-de.logging.cloud.ibm.com/v1/config/view \
        -H 'content-type: application/json' \
        -H 'servicekey: <SERVICE_KEY>' \
        -d '{
        "name": "My RC 200",
        "query": "reason.reasonCode:200",
        "hosts": ["ibm-cloud-databases-prod"],
        "category": ["TEST"],
      "channels": [
        {
          "integration": "email",
          "emails": ["myemail@ibm.com"],   
          "triggerlimit": 15,
          "triggerinterval": "5m",
          "immediate": true,
          "terminal": true,
          "operator": "presence",
          "timezone": "Europe/London"
        }
      ]
    }'
```
{: pre}

A response similar to the following will be returned:

```text
{"name":"My RC 200","query":"reason.reasonCode:200","hosts":["ibm-cloud-databases-prod"],"category":["89610d13a7"],"channels":[{"integration":"email","emails":"myemail@ibm.com","triggerlimit":15,"triggerinterval":300,"immediate":true,"terminal":true,"operator":"presence","timezone":"Europe/London","alertid":"<ALERTID>"}],"viewid":"VIEWID"}
```
{: screen}

### Get all configured views and alerts
{: #config-api-get}

The following sample gets all configured views and alerts for the instance.

```text
curl --request GET  https://api.eu-de.logging.cloud.ibm.com/v1/config/view  -H "content-type: application/json"  -H "servicekey: <SERVICE_KEY>"  
```
{: pre}

A response similar to the following will be returned:

```text
[{"viewid":"cf1a53da31","name":"(_platform:xxx create) OR (_platform:xxx delete)","query":"(_platform:xxx .create) OR (_platform:xxx .delete)","category":["Instance"],"account":"xxxxxxxxx"},{"viewid":"de6de89f6c","name":"[All] Logins","query":"reason.reasonCode:200 _platform:iam-identity (action login)","category":["Login"],"account":"xxxxxxxx"},{"viewid":"dfd136707e","name":"[All] Events","category":["COS"],"account":"xxxxxxxx","hosts":["cloud-object-storage"]}]
```
{: screen}

### Modifying a view by adding an alert
{: #api-configuration-mod-view-alert}

The following modifies a view by adding an alert.

```text
curl --request PUT \
  --url https://api.us-south.logging.cloud.ibm.com/v1/config/view/<VIEWID> \
  --header 'Content-Type: application/json' \
  -H 'servicekey: <SERVICE_KEY>'  \
-d '{
  "name": "My RC 200",
  "query": "reason.reasonCode:200",
  "hosts": ["ibm-cloud-databases-prod"],
  "category": ["<CATEGORY"],
  "channels": [
    {
      "integration": "email",
      "emails": ["myemail@ibm.com"],
      "triggerlimit": 15,
      "triggerinterval": "5m",
      "immediate": true,
      "terminal": true,
      "operator": "presence",
      "timezone": "Europe/London"
 }
  ]
}'
```
{: pre}

A response similar to the following is returned:

```text
{"name":"My RC 200","query":"reason.reasonCode:200","hosts":["ibm-cloud-databases-prod"],"category":["89610d13a7"],"channels":[{"integration":"email","emails":"myemail@ibm.com","triggerlimit":15,"triggerinterval":300,"immediate":true,"terminal":true,"operator":"presence","timezone":"Europe/London","alertid":"<ALERTID>"}],"viewid":"<VIEWID>"}
```
{: screen}



### Deleting a view
{: #api-configuration-del-view}

The following sample deletes a view.

```text
curl --request DELETE \
  --url https://api.us-south.logging.cloud.ibm.com/v1/config/view/<VIEWID> \
  -H 'content-type: application/json' \
  -H 'servicekey: <SERVICE_KEY>'  \
```  
{: pre}

The following response will be returned when the view is successfully deleted:

```text
{"deleted":true}
```
{: screen}


