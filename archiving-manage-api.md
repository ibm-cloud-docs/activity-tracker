---

copyright:
  years: 2019, 2022
lastupdated: "2021-10-21"

keywords: IBM Cloud, Activity Tracker, archiving, API

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}

# Managing archiving by using the API
{: #archiving-manage-api}

You can archive events from an {{site.data.keyword.at_full_notm}} instance into a bucket in an {{site.data.keyword.cos_full_notm}} (COS) instance by using an API. 
{: shortdesc}

This information applies only if you use an {{site.data.keyword.at_full}} [hosted event search offering](/docs/activity-tracker?topic=activity-tracker-service_plan).
{: important}


## Prerequisites on the {{site.data.keyword.at_full_notm}} service
{: #archiving_prereqs}

* **You must have a paid service plan** for the {{site.data.keyword.at_full_notm}} service. [Learn more](/docs/services/activity-tracker?topic=activity-tracker-service_plan#service_plan). 

* Check that your user ID has permissions to manage archiving. The following table lists the minimum roles that a user must have to manage archiving by using the API:

| Role                      | Permission granted            |
|---------------------------|-------------------------------|  
| Platform role: `Viewer`     | Allows the user to view the list of service instances. |
| Service role: `Manager`      | Allows the user to manage archiving by using the API.  |
{: caption="Table 1. IAM roles" caption-side="top"} 

For more information on how to configure policies for a user, see [Granting user permissions to a user or service ID](/docs/services/activity-tracker?topic=activity-tracker-iam_view_events#iam_view_events).

You must have a bucket, and the details of the service credential that you must use to write data to the bucket. For more information, see [Create some buckets to store your data](/docs/cloud-object-storage?topic=cloud-object-storage-getting-started-cloud-object-storage).


## Get details of the archiving configuration
{: #archivingapi-get-conf}

Use [this method](https://{DomainName}/apidocs/activity-tracker#get-v1-config-archiving){: external} to get the details about an existing archiving configuration.

```text
curl -X GET https://<ENDPOINT>/v1/config/archiving  
 -H "content-type: application/json"  
 -H "servicekey: <SERVICE_KEY>"  
```
{: pre}

- Replace `<ENDPOINT>` with the API endpoint. To see the list of endpoints, see [Endpoints](/docs/activity-tracker?topic=activity-tracker-endpoints#endpoints_api-at).
- Replace the `<SERVICE_KEY>` with a valid service key for the instance where you plan to configure archiving. For more information, see [Service keys by using the API](/docs/activity-tracker?topic=activity-tracker-service_keys#service_keys_api).

For example, the following is a sample get request:

```text
curl -X GET https://api.us-south.logging.cloud.ibm.com/v1/config/archiving  
 -H "content-type: application/json"  
 -H "servicekey: xxxxxxxx"  
```
{: codeblock}

The response will be similar to the following:

```text
{"integration":"ibm","bucket":"archiving-demo","endpoint":"<COS_ENDPOINT>","apikey":"<API_KEY>","resourceinstanceid":"crn:v1:bluemix:public:cloud-object-storage:global:a/<CRN>:"}
```
{: screen}

## Delete the archiving configuration
{: #archivingapi-delete-conf}

Use [this method](https://{DomainName}/apidocs/activity-tracker#delete-v1-config-archiving){: external} to delete an existing archiving configuration.

```text
curl -X DELETE https://<ENDPOINT/v1/config/archiving  
 -H "content-type: application/json"  
 -H "servicekey: <SERVICE_KEY>"  
```
{: pre}

- Replace `<ENDPOINT>` with the API endpoint. To see the list of endpoints, see [Endpoints](/docs/activity-tracker?topic=activity-tracker-endpoints#endpoints_api-at).
- Replace the `<SERVICE_KEY>` with a valid service key for the instance where you plan to configure archiving. For more information, see [Service keys by using the API](/docs/activity-tracker?topic=activity-tracker-service_keys#service_keys_api).


The response will be similar to the following if the configuration is successfully deleted:

```text
{"deleted":true}
```
{: codeblock}

If an incorrect service key was specified, a response similar to the following will be returned: 

```text
{"error":"Service Key Validation Error: Invalid or deactivated servicekey","status":"error","code":"NotAuthorized"}
```
{: codeblock}

## Configure archiving
{: #archivingapi-conf}

Use [this method](https://{DomainName}/apidocs/activity-tracker#post-v1-config-archiving){: external} to create an archiving configuration.

```text
curl -X POST https://<ENDPOINT>/v1/config/archiving  
 -H "content-type: application/json"  
 -H "servicekey: <SERVICE_KEY>"  
 -d '{"integration": "ibm", "bucket": "<BUCKET>", "endpoint": "<COS_ENDPOINT>", "apikey": "<API_KEY>", "resourceinstanceid": "<ID>"}' 
 ```
{: pre}

- Replace `<ENDPOINT>` with the API endpoint. To see the list of endpoints, see [Endpoints](/docs/activity-tracker?topic=activity-tracker-endpoints#endpoints_api-at).
- Replace the `<SERVICE_KEY>` with a valid service key for the instance where you plan to configure archiving. For more information, see [Service keys by using the API](/docs/activity-tracker?topic=activity-tracker-service_keys#service_keys_api).
- Replace `<BUCKET>` with the name of your {{site.data.keyword.cos_full_notm}} bucket.
- Replace `<COS_ENDPOINT>` with your {{site.data.keyword.cos_full_notm}} endpoint associated with the bucket.
- Replace `<API_KEY>` with the API key required to authenticat with 
- Replace `<ID>` With the CRN of the {{site.data.keyword.cos_full_notm}} instance where the bucket is located.


The response will be similar to the following if the configuration is successfully configured:

 ```text
 {"status":"active","brokers":["kafka-0.mh-svc1-0000.eu-de.containers.appdomain.cloud:9093","kafka-1.mh-sv2.eu-de.containers.appdomain.cloud:9093","kafka-2.mh-sv3.eu-de.containers.appdomain.cloud:9093"],"topic":"at-london-topic","user":"token"}
 ```
 {: codeblock}

## Update the archiving configuration
{: #archivingapi-update-conf}

Use [this method](https://{DomainName}/apidocs/activity-tracker#put-v1-config-archiving){: external} to update an archiving configuration.

```text
curl -X PUT https://api.eu-gb.logging.cloud.ibm.com/v1/config/archiving 
 -H "content-type: application/json"  
 -H "servicekey: <SERVICE_KEY>"  
 -d '{"integration": "ibm", "bucket": "<BUCKET>", "endpoint": "<COS_ENDPOINT>", "apikey": "<API_KEY>", "resourceinstanceid": "<ID>"}' 
```
{: pre}

- Replace `<ENDPOINT>` with the API endpoint. To see the list of endpoints, see [Endpoints](/docs/activity-tracker?topic=activity-tracker-endpoints#endpoints_api-at).
- Replace the `<SERVICE_KEY>` with a valid service key for the instance where you plan to configure archiving. For more information, see [Service keys by using the API](/docs/activity-tracker?topic=activity-tracker-service_keys#service_keys_api).
- Replace `<BUCKET>` with the name of your {{site.data.keyword.cos_full_notm}} bucket.
- Replace `<COS_ENDPOINT>` with your {{site.data.keyword.cos_full_notm}} endpoint associated with the bucket.
- Replace `<API_KEY>` with the API key required to authenticat with 
- Replace `<ID>` With the CRN of the {{site.data.keyword.cos_full_notm}} instance where the bucket is located.

The response will be similar to the following if the configuration is successfully updated:

 ```text
{"status":"active","brokers":["kafka-0.mh-svc1-0000.eu-de.containers.appdomain.cloud:9093","kafka-1.mh-sv2.eu-de.containers.appdomain.cloud:9093","kafka-2.mh-sv3.eu-de.containers.appdomain.cloud:9093"],"topic":"at-london-topic","user":"token"}
 ```
 {: codeblock}

If archiving is not configured, the following will be returned when trying to do an update:

```text
{"error":"Archiving configuration does not exist","code":"NotFound","status":"error"}
```
{: codeblock}

## Check the status of an archiving configuration
{: #archivingapi-conf-status}

To check if archiving is enabled or disabled, you can use either the GET or PUT methods.

When archiving is not enabled, the following is returned when running the [GET method](#archivingapi-get-conf): 

```text
{"error":"Not found","code":"NotFound","status":"error"}
```
{: codeblock}

When archiving is not enabled, the following is returned when running the [PUT method](#archivingapi-update-conf): 

```text
{"error":"Archiving configuration does not exist","code":"NotFound","status":"error"}
```
{: codeblock}



