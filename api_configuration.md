---

copyright:
  years: 2019, 2020
lastupdated: "2020-11-12"

keywords: IBM Cloud, LogDNA, Activity Tracker, CF events

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

# Managing views programmatically
{: #api_configuration}

You can use the *Configuration REST API* to programmatically manage views and alerts. 
{:shortdesc}

- You can use the **POST** method to create a view, or create a view and attach an alert to it.
- You can use the **PUT** method to modify an existing view, and alerts that are attached to views.
- You can use the **DELETE** method to delete a view and associated alerts.


## Configuration API endpoints
{: #api_configuration-endpoints}

### Public API endpoints
{: #api_configuration-endpoints-public}

The following table shows the API endpoints:

| Region                   |  Public Endpoint                                   |
|--------------------------|----------------------------------------------------|
| `Chennai (in-che)`       | `https://api.in-che.logging.cloud.ibm.com/v1/config/view`       |
| `Dallas (us-south)`      | `https://api.us-south.logging.cloud.ibm.com/v1/config/view`       |
| `Frankfurt (eu-de)`      | `https://api.eu-de.logging.cloud.ibm.com/v1/config/view`          |
| `London (eu-gb)`         | `https://api.eu-gb.logging.cloud.ibm.com/v1/config/view`          |
| `Tokyo (jp-tok)`         | `https://api.jp-tok.logging.cloud.ibm.com/v1/config/view`         |
| `Seoul (kr-seo)`         | `https://api.kr-seo.logging.cloud.ibm.com/v1/config/view`         |
| `Sydney (au-syd)`        | `https://api.au-syd.logging.cloud.ibm.com/v1/config/view`         |
| `Washington (us-east)`   | `https://api.us-east.logging.cloud.ibm.com/v1/config/view`         |
{: caption="Table 1. Lists of public API endpoints" caption-side="top"}

### Private API endpoints
{: #api_configuration-endpoints-private}

The following table shows the API endpoints:

| Region                   |  Private Endpoint                                   |
|--------------------------|----------------------------------------------------|
| `Chennai (in-che)`       | `https://api.private.in-che.logging.cloud.ibm.com/v1/config/view`       |
| `Dallas (us-south)`      | `https://api.private.us-south.logging.cloud.ibm.com/v1/config/view`       |
| `Frankfurt (eu-de)`      | `https://api.private.eu-de.logging.cloud.ibm.com/v1/config/view`          |
| `London (eu-gb)`         | `https://api.private.eu-gb.logging.cloud.ibm.com/v1/config/view`          |
| `Tokyo (jp-tok)`         | `https://api.private.jp-tok.logging.cloud.ibm.com/v1/config/view`         |
| `Seoul (kr-seo)`         | `https://api.private.kr-seo.logging.cloud.ibm.com/v1/config/view`         |
| `Sydney (au-syd)`        | `https://api.private.au-syd.logging.cloud.ibm.com/v1/config/view`         |
| `Washington (us-east)`   | `https://api.private.us-east.logging.cloud.ibm.com/v1/config/view`         |
{: caption="Table 2. Lists of private API endpoints" caption-side="top"}



## Creating a view
{: #api_configuration-create-view}

- A category must exist. 


```
curl https://api.us-south.logging.cloud.ibm.com/v1/config/view \
  -H 'content-type: application/json' \
  -H 'servicekey: 183f001b42fc49af85bc46e02fd17e06' \
  -d '{
  "name": "My RC 200",
  "query": "reason.reasonCode:200",
  "hosts": ["ibm-cloud-databases-prod"],
  "apps": ["N/A"],
  "levels": ["normal"],
  "tags": ["N/A"],
  "category": ["IBM"]
}'
```
{: codeblock}

response

```
{"name":"My RC 200","query":"reason.reasonCode:200","hosts":["ibm-cloud-databases-prod"],"apps":["N/A"],"levels":["normal"],"tags":["N/A"],"category":[],"viewid":"35e815837a"}
```

{"name":"My RC 200","query":"reason.reasonCode:200","hosts":["ibm-cloud-databases-prod"],"apps":["N/A"],"levels":["normal"],"tags":["N/A"],"category":["89610d13a7"],"viewid":"3c3de90460"}


Delete

curl --request DELETE \
  --url https://api.us-south.logging.cloud.ibm.com/v1/config/view/35e815837a \
  -H 'content-type: application/json' \
  -H 'servicekey: 183f001b42fc49af85bc46e02fd17e06'  \
  


Response

```
{"deleted":true}
```

Modify a view

curl --request PUT \
  --url https://api.us-south.logging.cloud.ibm.com/v1/config/view/3c3de90460 \
  --header 'Content-Type: application/json' \
  -H 'servicekey: 183f001b42fc49af85bc46e02fd17e06' 


If the view ID does not exist

```
{"error":"Nothing to configure","code":"BadRequest","status":"error"}
```





curl --request PUT \
  --url https://api.us-south.logging.cloud.ibm.com/v1/config/view/3c3de90460 \
  --header 'Content-Type: application/json' \
  -H 'servicekey: 183f001b42fc49af85bc46e02fd17e06'  \
-d '{
  "name": "My RC 200",
  "query": "reason.reasonCode:200",
  "hosts": ["ibm-cloud-databases-prod"],
  "apps": ["N/A"],
  "levels": ["normal"],
  "tags": ["N/A"],
  "category": ["IBM"],
  "channels": [
    {
      "integration": "email",
      "emails": ["your_email@email.test"],
      "triggerlimit": 15,
      "triggerinterval": "5m",
      "immediate": true,
      "terminal": true,
      "operator": "presence",
      "timezone": "America/Los_Angeles"
    {
      "integration": "webhook",
      "url": "YOUR_WEBHOOK_URL_HERE",
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
      "key": "YOUR_PD_KEY_HERE",
      "triggerlimit": 150,
      "triggerinterval": "15m",
      "operator": "absence",
      "immediate": false,
      "terminal": true
    }
  ]
}'


When the apps is left empty
```
{"details":[{"message":"\"apps[0]\" is not allowed to be empty","key":"apps[0]"}],"error":"\"apps[0]\" is not allowed to be empty","code":"BadRequest","status":"error"}
```





Sample:

```
curl https://api.us-south.logging.cloud.ibm.com/v1/config/view \
  -H 'content-type: application/json' \
  -H 'servicekey: xxxxxxxxxxxxx' \
  -d '{
  "name": "My View from API",
  "query": "logType:stderr",
  "hosts": ["ibm-cloud-databases-prod"],
  "apps": ["crn:v1:bluemix:public:databases-for-redis:us-south:a/xxxxxxxxxxxx:xxxxxxx::"],
  "levels": ["info"],
  "tags": ["script"],
  "category": ["ICD"]
}'
```
{: screen}


## Creating a view and attach an alert
{: #api_configuration-create-view-alert}


## Modifying a view by changing the search query
{: #api_configuration-mod-view-query}



## Modifying a view by adding an alert
{: #api_configuration-mod-view-alert}


## Deleting a view
{: #api_configuration-del-view}


When using the POST method, the name parameter is always required, in order to define the name of the new View.
When using PUT you must specify the name and viewid.
For DELETE you must specify the viewid parameter, in order to affect the correct View.
Authentication
The LogDNA Configuration API uses a service key in the Header to provide authentication. HTTP Headers are the part of the API request and response that contain the meta-data associated with the API request and response.

NOTE: You can pass the service key in the header parameter (-H) of your requests, as shown in the Example below. Alternatively, you can pass service key in the username element (-u) of the request and leave the password value as blank/empty.




view ID  ec2e986718



{"name":"My View from API","query":"logType:stderr","hosts":["ibm-cloud-databases-prod"],"apps":["crn:v1:bluemix:public:databases-for-redis:us-south:a/81de6380e6232019c6567c9c8de6dece:f3374b92-f10d-46c1-bb7d-9bb8012bf9da::"],"levels":["info"],"tags":["script"],"category":["6a544ff358"],"viewid":"67e76d6cd2"}



{"details":[{"message":"\"levels[0]\" is not allowed to be empty","key":"levels[0]"},{"message":"\"tags[0]\" is not allowed to be empty","key":"tags[0]"}],"error":"\"levels[0]\" is not allowed to be empty. \"tags[0]\" is not allowed to be empt



curl https://api.us-south.logging.cloud.ibm.com/v1/config/view \
  -H 'content-type: application/json' \
  -H 'servicekey: 45475372efad48c5abf77dbc72b7c8e0' \
  -d '{
  "name": "My View from API",
  "query": "logType:stderr",
  "hosts": ["ibm-cloud-databases-prod"],
  "apps": ["crn:v1:bluemix:public:databases-for-redis:us-south:a/81de6380e6232019c6567c9c8de6dece:f3374b92-f10d-46c1-bb7d-9bb8012bf9da::"],
  "levels": ["N/A"],
  "tags": ["script"],
  "category": ["New category"]
}'

{"name":"My View from API","query":"logType:stderr","hosts":["ibm-cloud-databases-prod"],"apps":["crn:v1:bluemix:public:databases-for-redis:us-south:a/81de6380e6232019c6567c9c8de6dece:f3374b92-f10d-46c1-bb7d-9bb8012bf9da::"],"levels":["info"],"tags":["script"],"category":[],"viewid":"f7b46891df"}


curl https://api.us-south.logging.cloud.ibm.com/v1/config/view \
  -H 'content-type: application/json' \
  -H 'servicekey: 45475372efad48c5abf77dbc72b7c8e0' \
  -d '{
  "name": "My View from API",
  "query": "logType:stderr",
  "hosts": ["ibm-cloud-databases-prod"],
  "apps": ["crn:v1:bluemix:public:databases-for-redis:us-south:a/81de6380e6232019c6567c9c8de6dece:f3374b92-f10d-46c1-bb7d-9bb8012bf9da::"],
  "levels": ["N/A"],
  "tags": ["N/A"],
  "category": ["New category"]
}'



curl --request DELETE \
  --url https://api.us-south.logging.cloud.ibm.com/v1/config/view/867434d7ac \
  -H 'servicekey: 183f001b42fc49af85bc46e02fd17e06' \
  --header 'Content-Type: application/json'
















curl https://api.us-south.logging.cloud.ibm.com/v1/config/view \
  -H 'content-type: application/json' \
  -H 'servicekey: 45475372efad48c5abf77dbc72b7c8e0' \
  -d '{
  "name": "My View from API",
  "hosts": ["ibm-cloud-databases-prod"],
  "category": ["IBM"]
}'

{"name":"My View from API","hosts":["ibm-cloud-databases-prod"],"category":[],"viewid":"c05fc3ce22"}



curl --request PUT \
  --url https://api.logdna.com/v1/config/view/viewid/c05fc3ce22 \
  --header 'Content-Type: application/json'

curl --request POST \
  --url https://api.us-south.logging.cloud.ibm.com/v1/config/view/c05fc3ce22 \
  --header 'Content-Type: application/json'\
  -H 'servicekey: 45475372efad48c5abf77dbc72b7c8e0' \
  -d '{
  "name": "My View from API 1",
  "hosts": ["ibm-cloud-databases-prod"],
  "category": ["IBM"]
}'

curl -I https://api.us-south.logging.cloud.ibm.com/v1/config/view/c05fc3ce22  \
  -H 'content-type: application/json' \
  -H 'servicekey: 45475372efad48c5abf77dbc72b7c8e0' \
  -d '{
  "name": "My View from API 1",
  "hosts": ["ibm-cloud-databases-prod"],
  "category": ["IBM"]
}'


curl https://api.logdna.com/v1/config/view \
  -H 'content-type: application/json' \
  -H 'servicekey: YOUR_SERVICE_KEY' \
  -d '{
  "name": "My View With Alerts",
  "query": "response:500",
  "hosts": ["host1", "host2"],
  "apps": ["apps1", "apps2"],
  "levels": ["error"],
  "tags": ["prod"],
  "category": ["My Service"],
  "channels": [
    {
      "integration": "email",
      "emails": ["your_email@email.test"],
      "triggerlimit": 15,
      "triggerinterval": "5m",
      "immediate": true,
      "terminal": true,
      "operator": "presence",
      "timezone": "America/Los_Angeles"
    {
      "integration": "webhook",
      "url": "YOUR_WEBHOOK_URL_HERE",
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
      "key": "YOUR_PD_KEY_HERE",
      "triggerlimit": 150,
      "triggerinterval": "15m",
      "operator": "absence",
      "immediate": false,
      "terminal": true
    }
  ]
}'




| Task                                                                                        | Description     |
|---------------------------------------------------------------------------------------------|-----------------|
| [Copy a group](/docs/services/Monitoring-with-Sysdig/groups.html#copy_group)     | Copy a group to other teams. |
| [Create a group](/docs/services/Monitoring-with-Sysdig/groups.html#create_group) | Create a new group. |
| [Delete a group](/docs/services/Monitoring-with-Sysdig/groups.html#delete_group) | Delete a group. |
| [Rename a group](/docs/services/Monitoring-with-Sysdig/groups.html#rename_group) | Rename a group. |
| [Share a group](/docs/services/Monitoring-with-Sysdig/groups.html#share_group)   | Share a group with other members in the team. |
{: caption="Table 3. Tasks grouping labels" caption-side="top"} 


