---

copyright:
  years: 2019, 2024
lastupdated: "2024-05-17"

keywords:

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}

# Managing groups by using the API
{: #groups-manage-api}

You can manage {{site.data.keyword.at_full_notm}} [groups](/docs/activity-tracker?topic=activity-tracker-group_data_access) by using an API.
{: shortdesc}

<!-- Common deprecation statement -->
{{../log-analysis/_include-segments/deprecation_notice.md}}


## Prerequisites on the {{site.data.keyword.at_full_notm}} service
{: #groups_prereqs}

* **You must have a paid service plan** for the {{site.data.keyword.at_full_notm}} service. [Learn more](/docs/services/activity-tracker?topic=activity-tracker-service_plan#service_plan).

* Check that your user ID has permissions to manage groups. The following table lists the minimum roles that a user must have to manage groups by using the API:

| Role                      | Permission granted            |
|---------------------------|-------------------------------|
| Platform role: `Viewer`     | Allows the user to view the list of service instances. |
| Service role: `Manager`      | Allows the user to manage groups by using the API.  |
{: caption="Table 1. IAM roles" caption-side="top"}

For more information on how to configure policies for a user, see [Granting user permissions to a user or service ID](/docs/services/activity-tracker?topic=activity-tracker-iam_view_events#iam_view_events).


## List the configured groups
{: #group-list-api}

Use [this method](https://{DomainName}/apidocs/activity-tracker#list-group){: external} to list existing groups.

```text
curl --request GET
 --url https://<ENDPOINT>/v1/config/groups
 -H "content-type: application/json"
 -H "servicekey: <SERVICE_KEY>"
```
{: pre}

- Replace `<ENDPOINT>` with the {{site.data.keyword.at_full_notm}} API endpoint. To see the list of endpoints, see [Endpoints](/docs/activity-tracker?topic=activity-tracker-endpoints#endpoints_api-at).
- Replace the `<SERVICE_KEY>` with a valid service key for the {{site.data.keyword.at_full_notm}} instance where you plan to configure groups. For more information, see [Service keys by using the API](/docs/activity-tracker?topic=activity-tracker-service_keys#service_keys_api).

For example, the following is a sample get request:

```text
curl --request GET https://api.eu-gb.logging.cloud.ibm.com/v1/config/groups
 -H "content-type: application/json"
 -H "servicekey: xxxxxxxx"
```
{: codeblock}

The response will be similar to the following:

```text
[{"name":"Test group","groupId":"xxxxxxxxxxx","accessScopes":["reasonCode:200"]}]
```
{: codeblock}


If no groups exist, the response will be:

```text
{"error":"Not Found","code":"ResponseError","status":"error"}
```
{: codeblock}

If an incorrect service key is supplied, the response will be:

```text
{"error":"Service Key Validation Error: Invalid or deactivated servicekey","status":"error","code":"NotAuthorized"}
```
{: codeblock}

## Create a new group
{: #group-create-api}

Use [this method](https://{DomainName}/apidocs/activity-tracker#create-group){: external} to create a new group.

```text
curl --request POST
 --url https://<ENDPOINT>/v1/config/groups
 -H "content-type: application/json"
 -H "servicekey: <SERVICE_KEY>"
 -d '{"name": "<NAME>","accessScopes": ["<SCOPE>"] }'
```
{: pre}

- Replace `<ENDPOINT>` with the {{site.data.keyword.at_full_notm}} API endpoint. To see the list of endpoints, see [Endpoints](/docs/activity-tracker?topic=activity-tracker-endpoints#endpoints_api-at).
- Replace the `<SERVICE_KEY>` with a valid service key for the {{site.data.keyword.at_full_notm}} instance where you plan to configure groups. For more information, see [Service keys by using the API](/docs/activity-tracker?topic=activity-tracker-service_keys#service_keys_api).
- Replace `<NAME>` with the name you want to give to the group.
- Replace `<SCOPE>` with a query specified as a JSON array. See [Defining service groups](/docs/activity-tracker?topic=activity-tracker-group_data_access#groups_data_access_groups) for example access scope search queries.

For example, for the following command:

```text
curl --request POST --url https://api.eu-gb.logging.cloud.ibm.com/v1/config/groups -H "content-type: application/json" -H "servicekey: <SERVICE_KEY>" -d '{"name": "My log group","accessScopes": ["reasonCode:200"] }'
```
{: codeblock}

The response will be similar to the following:

```text
{"name":"My log group","groupId":"xxxxxxxxxxxx","accessScopes":["reasonCode:200"]}
```
{: codeblock}


## Get group details
{: #group-details-api}

Use [this method](https://{DomainName}/apidocs/activity-tracker#read-group){: external} to get information about an existing group.

```text
curl --request GET
 --url https://<ENDPOINT>/v1/config/groups/<GROUP_ID>
 -H "content-type: application/json"
 -H "servicekey: <SERVICE_KEY>"
```
{: pre}

- Replace `<ENDPOINT>` with the {{site.data.keyword.at_full_notm}} API endpoint. To see the list of endpoints, see [Endpoints](/docs/activity-tracker?topic=activity-tracker-endpoints#endpoints_api-at).
- Replace the `<SERVICE_KEY>` with a valid service key for the {{site.data.keyword.at_full_notm}} instance where you plan to configure groups. For more information, see [Service keys by using the API](/docs/activity-tracker?topic=activity-tracker-service_keys#service_keys_api).
- Replace `<GROUP_ID>` with the `groupId` returned when [listing configured groups](#group-list-api).

The response will be similar to the following:

```text
[{"name":"Test group","groupId":"xxxxxxxxxxx","accessScopes":["reasonCode:200"]}]
```
{: codeblock}



## Delete a group
{: #group-delete-api}

Use [this method](https://{DomainName}/apidocs/activity-tracker#delete-group){: external} to delete a group.

```text
curl --request DELETE
 --url https://<ENDPOINT>/v1/config/groups/<GROUP_ID>
 -H "content-type: application/json"
 -H "servicekey: <SERVICE_KEY>"
```
{: pre}

- Replace `<ENDPOINT>` with the {{site.data.keyword.at_full_notm}} API endpoint. To see the list of endpoints, see [Endpoints](/docs/activity-tracker?topic=activity-tracker-endpoints#endpoints_api-at).
- Replace the `<SERVICE_KEY>` with a valid service key for the {{site.data.keyword.at_full_notm}} instance where you plan to configure groups. For more information, see [Service keys by using the API](/docs/activity-tracker?topic=activity-tracker-service_keys#service_keys_api).
- Replace `<GROUP_ID>` with the `groupId` returned when [listing configured groups](#group-list-api).

The response will be similar to the following:

```text
{"deleted":true}
```
{: codeblock}

If the `<GROUP_ID>` does not exist, the response will be similar to the following:

```text
{"groupId":"xxxxxxxxxx","error":"Not Found","code":"ResponseError","status":"error"}
```
{: codeblock}

## Update a group
{: #group-update-api}

Use [this method](https://{DomainName}/apidocs/activity-tracker#update-group){: external} to update a group.

```text
curl --request PATCH
 --url https://<ENDPOINT>/v1/config/groups/<GROUP_ID>
 -H "content-type: application/json"
 -H "servicekey: <SERVICE_KEY>"
 -d '{"name": "<NAME>","accessScopes": ["<SCOPE>"] }'
```
{: pre}

- Replace `<ENDPOINT>` with the {{site.data.keyword.at_full_notm}} API endpoint. To see the list of endpoints, see [Endpoints](/docs/activity-tracker?topic=activity-tracker-endpoints#endpoints_api-at).
- Replace the `<SERVICE_KEY>` with a valid service key for the {{site.data.keyword.at_full_notm}} instance where you plan to configure groups. For more information, see [Service keys by using the API](/docs/activity-tracker?topic=activity-tracker-service_keys#service_keys_api).
- Replace `<GROUP_ID>` with the `groupId` returned from [listing configured groups](#group-list-api).
- Replace `<NAME>` with the name you want to give to the group.
- Replace `<SCOPE>` with a query specified as a JSON array. See [Defining service groups](/docs/activity-tracker?topic=activity-tracker-group_data_access#groups_data_access_groups) for example access scope search queries.

```text
curl --request PATCH --url https://api.eu-gb.logging.cloud.ibm.com/v1/config/groups/xxxxxxxxxxxx -H "content-type: application/json" -H "servicekey: <SERVICE_KEY>" -d '{"name": "My log group2","accessScopes": ["reasonCode:200"] }'
```
{: codeblock}

The response will be similar to the following:

```text
{"name":"My log group2","groupId":"xxxxxxxxxxxx","accessScopes":["reasonCode:200"]}
```
{: codeblock}
