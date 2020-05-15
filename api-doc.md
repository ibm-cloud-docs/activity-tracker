---

copyright:
  years: 2019, 2020
lastupdated: "2020-01-08"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:generic: .ph data-hd-programlang='generic'}
{:java: .ph data-hd-programlang='java'}
{:ruby: .ph data-hd-programlang='ruby'}
{:c#: .ph data-hd-programlang='c#'}
{:objectc: .ph data-hd-programlang='Objective C'}
{:python: .ph data-hd-programlang='python'}
{:node: .ph data-hd-programlang='node'}
{:php: .ph data-hd-programlang='PHP'}
{:swift: .ph data-hd-programlang='swift'}
{:curl: .ph data-hd-programlang='curl'}
{:node: .ph data-hd-programlang='node'}
{:middle: .ph data-hd-position='middle'}
{:right: .ph data-hd-position='right'}


# Introduction

You can use the {{site.data.keyword.at_full}} service to monitor the activity of your {{site.data.keyword.cloud_notm}} account, investigate for abnormal activity and critical actions, and comply with regulatory audit requirements. In addition, you can be alerted on actions as they happen. The events that are collected comply with the Cloud Auditing Data Federation (CADF) standard. For details about using the {{site.data.keyword.at_full}} service, see the {{site.data.keyword.cloud_notm}} [docs](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-getting-started).

The {{site.data.keyword.at_full}} service provides a REST API that you can use to export events in JSONL format. For more information on how to use the API, see [Exporting events programmatically by using the API](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-export#export_api).

Consider the following information when you work with the API:
* You must have a **paid service plan** for the {{site.data.keyword.at_full_notm}} service. [Learn more](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-service_plan#service_plan). 
* You need a **service key**. The {{site.data.keyword.at_full}} administrator can generate one. The service key is different per location, that is, you need a service key per endpoint.
* You must use the **endpoint** for the location where the data that you want to export is available. Each location (region) has a different URL. To get the list of available endpoints, see [Endpoints](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-endpoints#endpoints).
* You must specify the version of the API.
* API requests are limited to 100 requests per second.
* 10,000 lines per batch are returned. 
* 500,000 log lines are the maximum lines that are returned per API request. 

For example, to stream events into the terminal, you can run the following command:

## Curl example
{: curl}
{: right}

```
curl "ENDPOINT/v1/export?QUERY_PARAMETERS" -u SERVICE_KEY:
```
{: codeblock}


### API endpoint 

Each location (region) has a different endpoint. To get the list of available endpoints, see [Endpoints](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-endpoints#endpoints)

For example, for us-south, the endpoint is the following:

```
https://api.us-south.logging.cloud.ibm.com/

```
{: codeblock}


# Error handling

This API uses standard HTTP response codes to indicate whether a method completed successfully. A `200` response indicates success. A `400` type response indicates a failure, and a `500` type response indicates an internal system error.

| HTTP Error Code | Description           | Recovery                                                                    |
|-----------------|-----------------------|-----------------------------------------------------------------------------|
| `200`           | Success               | The request was successful.                                                 |
| `400`           | Bad Request           | The input parameters in the request body are either incomplete or in the wrong format. Be sure to include all required parameters in your request. |
| `401`           | Unauthorized          | You are not authorized to make this request. Log in to {{site.data.keyword.cloud_notm}} and try again. If this error persists, contact the account owner to check your permissions. |
| `403`           | Forbidden             | The supplied authentication is not authorized to access XXXXXX.      |
| `404`           | Not Found             | The requested resource could not be found.                                  |
| `408`           | Request Timeout       | The connection to the server timed out. Wait a few minutes, then try again. |
| `409`           | Conflict              | The entity is already in the requested state.                               |
| `500`           | Internal Server Error | IBM Cloud Activity Tracker with LogDNA is currently unavailable. Your request could not be processed. Wait a few minutes and try again. |

# Authentication

This API is protected with HTTP Basic authentication. The Basic authentication credentials are in the `AUTH` property in your `~/.wskprops` file, delimited by a colon.

In the following cURL example, authentication is passed by using the `-u` flag:
`curl "https://api.us-south.logging.cloud.ibm.com/v1/export?to=$(date +%s)000&from=$(($(date +%s)-86400))000" -u INSERT_SERVICE_KEY:`.



# Versioning

API requests require a version parameter that is represented in the URL: `https://ENDPOINT/v1/`

You must send the version parameter with every API request.




# Pagination


Pagination is a ubiquitous method for handling large datasets and responses in the browser-based Web. When exporting event lines through the export API, you need to implement pagination into your script in order to request lines (in succession) greater than your plans API limit (Per each request).

implementing API pagination to export data - add info



# Sorting

**Optional**
**Purpose**: Does your API provide custom sorting? If so, provide details to clarify how sorting is handled. 


# Filtering

**Optional**
**Purpose**: Does your API support filtering? For example, do you support the use of pre-defined tags? If so, provide details to clarify how your API handles filtering. 


