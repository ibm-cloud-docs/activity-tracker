---

copyright:
  years: 2019
lastupdated: "2019-09-27"

keywords: IBM Cloud, LogDNA, Activity Tracker, scenarios

subcollection: logdnaat

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

 
# Trails of events for global actions
{: #trail_global_actions}

 {{site.data.keyword.at_full_notm}} 
{:shortdesc}


| Managing users                                                          | Service           | Actions                                        |
|:------------------------------------------------------------------------|:------------------|:-----------------------------------------------|
| `Invite a user to an account`                                           | `BSS`             | `user-management.user.create` |
| `Remove a user from an account`                                         | `IAM`  </br>`BSS` | `iam-am.policy.delete` </br>`user-management.user.delete` |
| `Invite a user to an account and add user to one or more access groups` | `IAM`  </br>`BSS` | `user-management.user.create` </br>`iam-groups.member.add` one entry per access group selected in the action | 



| Working with access groups                                             | Service     | Actions                                        |
|:-----------------------------------------------------------------------|:------------|:-----------------------------------------------|
| `Create an access group`                                               | `IAM`       | `iam-groups.group.create` |
| `Add a user to a group or add service ID to a group`                   | `IAM`       | `iam-groups.group.read` </br>`iam-groups.member.add` |
| `Remove an access group`                                               | `IAM`       | `iam-groups.group.delete` </br>`iam-groups iam-groups.members.delete` </br>`iam-groups iam-groups.rules.delete` |
| `Rename an access group`                                               | `IAM`       | `iam-groups.group.read` </br>`iam-groups.group.update` |


| Working with policies and access groups                                | Service     | Actions                                        |
|:-----------------------------------------------------------------------|:------------|:-----------------------------------------------|
| `Add a policy by assigning access to resources`                        | `IAM`       | `iam-groups.group.read` </br>`iam-am.policy.create` |
| `Add a policy by assigning access within a resource group to a resource group` | `IAM`       |  `iam-groups.group.read` </br>`iam-am.policy.create` |
| `Add a policy by assigning access within a resource group to a resource group and to a service in the resource group` | `IAM` | `iam-groups.group.read` </br>`iam-am.policy.create` for the resource group permissions </br></br>`iam-am.policy.create` for the service permissions within the resource group |
| `Add a policy by assigning access to account management services`      | `IAM`       | `iam-groups.group.read` </br>`iam-am.policy.create` |
| `Modify a policy for an access group`                                  | `IAM`       | `iam-groups.group.read` </br>`iam-am.policy.update` |
| `Delete a policy`                                                      | `IAM`       | `iam-groups.group.read` </br>`iam-am.policy.delete` |

| Working with policies and users                                        | Service     | Actions                                        |
|:-----------------------------------------------------------------------|:------------|:-----------------------------------------------|
| `Add a policy for a user by assigning access to resources`             | `IAM`       | `iam-am.policy.create  `   |
| `Add a policy by assigning access within a resource group to a resource group` | `IAM`  | `iam-am.policy.create` |
| `Add a policy by assigning access within a resource group to a resource group and to a service in the resource group` | `IAM` | </br>`iam-am.policy.create` for the resource group permissions </br></br>`iam-am.policy.create` for the service permissions within the resource group |
| `Modify a policy for a user`                                           | `IAM`       | `iam-am.policy.update` |
| `Delete a policy for a user`                                           | `IAM`       | `iam-am.policy.update` |



| Working with service IDs            | Service     | Actions                                        |
|:------------------------------------|:------------|:-----------------------------------------------|
| `Create a service ID`               | `IAM`       | `iam-identity.account-serviceid.create` |
| `Delete a service ID`               | `IAM`       | `iam-identity.account-serviceid.delete` | 
| `Lock a service ID`                 |  `IAM`       |`iam-identity.account-serviceid.update` |
| `Unlock a service ID`               |  `IAM`       |`iam-identity.account-serviceid.update` |
| `Rename a service ID`               |  `IAM`       |`iam-identity.account-serviceid.update` |
| `Change the service ID description` |  `IAM`       |`iam-identity.account-serviceid.update` |
| `Create an API key for a servie ID` |  `IAM`       |`iam-identity.serviceid-apikey.create` </br>`iam-am.policy.create`|

| Working with API keys                   | Service     | Actions                                        |
|:----------------------------------------|:------------|:-----------------------------------------------|
| `Create an IBM Cloud API key`           | `IAM`       | `iam-identity.user-apikey.create` |
| `Lock an API key`                       | `IAM`       |`iam-identity.user-apikey.update` |
| `Unlock an API key`                     | `IAM`       | `iam-identity.user-apikey.update` |
| `Change the description of an API key`  | `IAM`       | `iam-identity.user-apikey.update`  |
| `Rename an API key`                     | `IAM`       |`iam-identity.user-apikey.update` |
| `Delete an API key`                     | `IAM`       |`iam-identity.user-apikey.delete` |


| Working with API keys                   | Service     | Actions                                        |
|:----------------------------------------|:------------|:-----------------------------------------------|
| `Provision an instance`                 | `BSS`       | '<serviceName>.instance.create` |
| `Delete an instance`                    | `BSS`       | `<serviceName>.instance.delete` </br>`iam-am.policy.delete` (3 events of these type) |
| `Delete an instance with a tag`         | `BSS`       | `<serviceName>.instance.delete` | 
| `Rename an instance`                    | `BSS`       |  `<serviceName>.instance.update` |
| `Add a tag to an instance`              | `BSS`       | `global-search-tagging.tag.attach-tag` | 



| Working with CF                         | Service         | Actions                                        |
|:----------------------------------------|:----------------|:-----------------------------------------------|
| `Assign an organization`                | `Cloud Foundry` | `audit.user.organization_user_add` </br>`audit.user.space_auditor_add` |
| `Attach a tag to a CF service`          | `GST`           |`global-search-tagging.tag.attach-tag` |
| `Rename a service instance`             | `Cloud Foundry` | `audit.service_instance.update` |
| `Delete a servifce instance`            | `Cloud Foundry` | `audit.service_instance.delete` |





















| Managing account settings                                              | Service     | Actions                                        |
|:-----------------------------------------------------------------------|:------------|:-----------------------------------------------|
| 




Delete a service ID should trigger the cleanup of policies and apikeys

Download or copy of an API key does not generate an event

Changes of description do not trigger an action




7/Nov/2019:09:48:38 BSS user-management.user.create 
27/Nov/2019:09:48:52 iam-groups iam-groups.member.add 
27/Nov/2019:09:48:52 iam-groups iam-groups.member.add  

7/Nov/2019:09:53:03 iam-groups iam-groups.group.delete 
27/Nov/2019:09:53:03 iam-groups iam-groups.members.delete 
27/Nov/2019:09:53:03 iam-groups iam-groups.rules.delete 
27/Nov/2019:09:53:12 iam-groups iam-groups.group.delete 
27/Nov/2019:09:53:13 iam-groups iam-groups.members.delete 
27/Nov/2019:09:53:13 iam-groups iam-groups.members.delete 
27/Nov/2019:09:53:13 iam-groups iam-groups.rules.delete  


Add a policy by assigning access within a resource group and grant permissions on RG and a service in the RG:

IAM Access Groups: read group test2 
27/Nov/2019:10:30:11 iam-am IAM Access Management: create policy  
27/Nov/2019:10:30:11 iam-am IAM Access Management: create polic



## Managing users
{: #trail_global_actions_users}

### Invite a user to an account
{: #trail_global_actions_users_1}

1. action = user-management.user.create

```
{
    "eventTime": "2019-11-26T23:59:27.00+0000",
    "action": "user-management.user.create",
    "initiator": {
        "id": "IBMid-060000JMJ2",
        "typeURI": "User",
        "host": {
            "agent": "",
            "address": " 10.45.116.217"
        },
        "credential": {
            "type": "token"
        },
        "name": ""
    },
    "target": {
        "id": "crn:v1:bluemix:public:user-management:global:a/81de6380e6232019c6567c9c8de6dece:::",
        "typeURI": "account-management",
        "name": "",
        "host": {
            "address": "accounts.cloud.ibm.com"
        }
    },
    "reason": {
        "reasonCode": 200,
        "reasonType": ""
    },
    "outcome": "pending",
    "severity": "normal",
    "meta": {
        "serviceProviderName": "bss-at-sender-prod-ng",
        "serviceProviderRegion": "ng",
        "serviceProviderProjectId": "00ca5480-ac12-45d7-89af-b0acde8dc6cb",
        "userAccountIds": [
            "81de6380e6232019c6567c9c8de6dece"
        ],
        "userSpaceId": "",
        "userSpaceRegion": ""
    },
    "logSourceCRN": "crn:v1:bluemix:public:user-management:global:a/81de6380e6232019c6567c9c8de6dece:::",
    "saveServiceCopy": true
}
```
{: screen}


### Invite a user to an account and add to 2 access groups

```
27/Nov/2019:09:48:16 iam-identity iam-identity.user-apikey.login  STATUS:success 
27/Nov/2019:09:48:38 BSS user-management.user.create  STATUS:pending 
27/Nov/2019:09:48:52 iam-groups iam-groups.member.add  STATUS:success 
27/Nov/2019:09:48:52 iam-groups iam-groups.member.add  STATUS:success  
```

### Delete a user
{: #trail_global_actions_users_2}


Two events are generated:
* delete policy   iam-am.policy.delete
* delete user     user-management.user.delete

```
26/Nov/2019:17:40:30 iam-am IAM Access Management: delete policy xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx 

{
    "outcome": "success",
    "eventTime": "2019-11-26T17:40:30.634+0000",
    "action": "iam-am.policy.delete",
    "initiator": {
        "id": "iam-ServiceId-41fced36-37cf-47bf-826f-4602d3c035fa",
        "name": "ServiceId-41fced36-37cf-47bf-826f-4602d3c035fa",
        "typeURI": "/service/security/account/user",
        "credential": {
            "type": "token"
        }
    },
    "target": {
        "id": "crn:v1:bluemix:public:iam-am::a/81de6380e6232019c6567c9c8de6dece::policy:0f514810-d3f8-47b8-96d8-9e2ef484aee2",
        "name": "policy-guid",
        "typeURI": "iam-am/policy"
    },
    "reason": {
        "reasonCode": 204
    },
    "requestData": {
        "url": "https://iam.cloud.ibm.com/v1/policies/0f514810-d3f8-47b8-96d8-9e2ef484aee2",
        "api_name": "deletePolicyByIdV1",
        "method": "DELETE",
        "body": {}
    },
    "responseData": {
        "status": "204 No Content",
        "elapsed_time": "146.717ms",
        "transaction_id": "ef8bfd306f334020a0bd77d90127853f",
        "response_body": ""
    },
    "message": "IAM Access Management: delete policy 0f514810-d3f8-47b8-96d8-9e2ef484aee2",
    "meta": {
        "serviceProviderName": "iam-am",
        "serviceProviderRegion": "ng",
        "serviceProviderProjectId": "53c0f9a6-c07e-4ac0-b933-7327b6ca3c84",
        "userAccountIds": [
            "81de6380e6232019c6567c9c8de6dece"
        ]
    },
    "logSourceCRN": "crn:v1:bluemix:public:iam-am::a/81

```
{: screen}

```
26/Nov/2019:17:40:34 BSS: delete user xxxxx

{
    "eventTime": "2019-11-26T17:40:34.00+0000",
    "action": "user-management.user.delete",
    "initiator": {
        "id": "IBMid-060000JMJ2",
        "typeURI": "User",
        "host": {
            "agent": "",
            "address": " 10.113.15.79"
        },
        "credential": {
            "type": "token"
        },
        "name": ""
    },
    "target": {
        "id": "crn:v1:bluemix:public:user-management:global:a/81de6380e6232019c6567c9c8de6dece:::",
        "typeURI": "account-management",
        "name": "",
        "host": {
            "address": "accounts.cloud.ibm.com"
        }
    },
    "reason": {
        "reasonCode": 200,
        "reasonType": ""
    },
    "outcome": "success",
    "severity": "normal",
    "meta": {
        "serviceProviderName": "bss-at-sender-prod-ng",
        "serviceProviderRegion": "ng",
        "serviceProviderProjectId": "00ca5480-ac12-45d7-89af-b0acde8dc6cb",
        "userAccountIds": [
            "81de6380e6232019c6567c9c8de6dece"
        ],
        "userSpaceId": "",
        "userSpaceRegion": ""
    },
    "logSourceCRN": "crn:v1:bluemix:public:user-management:global:a/81de6380e6232019c6567c9c8de6dece:::",
    "saveServiceCopy": true
}de6380e6232019c6567c9c8de6dece: : :",
    "saveServiceCopy": true
}
```
{: screen}


## Create an access group

action: iam-groups.group.create


```
27/Nov/2019:00:03:01 iam-groups IAM Access Groups: create group Sample-access-group  

{
    "id": "a2d5e7b5-e2be-4795-9c68-0650cfedf462",
    "eventTime": "2019-11-27T00:03:01.8+0000",
    "action": "iam-groups.group.create",
    "outcome": "success",
    "message": "IAM Access Groups: create group Sample-access-group",
    "initiator": {
        "id": "IBMid-060000JMJ2",
        "typeURI": "service/security/account/user",
        "name": "LOPEZDSR@uk.ibm.com",
        "host": {
            "address": "158.177.175.87"
        },
        "credential": {
            "type": "token"
        }
    },
    "target": {
        "id": "crn:v1:bluemix:public:iam-groups:global:a/81de6380e6232019c6567c9c8de6dece::groups:AccessGroupId-6453e55b-8636-4884-85df-0c8d5b485d31",
        "typeURI": "iam-groups/group",
        "name": "Sample-access-group"
    },
    "reason": {
        "reasonCode": 201
    },
    "severity": "normal",
    "requestData": "{\"name\":\"Sample-access-group\",\"description\":\"\"}",
    "responseData": "{\"id\":\"AccessGroupId-6453e55b-8636-4884-85df-0c8d5b485d31\",\"name\":\"Sample-access-group\",\"description\":\"\",\"account_id\":\"81de6380e6232019c6567c9c8de6dece\",\"created_at\":\"2019-11-27T00:03:01Z\",\"created_by_id\":\"IBMid-060000JMJ2\",\"last_modified_at\":\"2019-11-27T00:03:01Z\",\"last_modified_by_id\":\"IBMid-060000JMJ2\"}",
    "logSourceCRN": "crn:v1:bluemix:public:iam-groups:global:a/81de6380e6232019c6567c9c8de6dece:::",
    "saveServiceCopy": true
}
```
{: screen}


## Add a user to an access group

27/Nov/2019:00:05:11 iam-groups IAM Access Groups: read group Sample-access-group 
27/Nov/2019:00:05:17 iam-groups IAM Access Groups: add member Sample-access-group  
  

{"id":"68716553-6be1-4ddd-b162-0c7a1a6ac416","eventTime":"2019-11-27T00:05:11.79+0000","action":"iam-groups.group.read","outcome":"success","message":"IAM Access Groups: read group Sample-access-group","initiator":{"id":"IBMid-060000JMJ2","typeURI":"service/security/account/user","name":"LOPEZDSR@uk.ibm.com","host":{"address":"158.177.175.87"},"credential":{"type":"token"}},"target":{"id":"crn:v1:bluemix:public:iam-groups:global:a/81de6380e6232019c6567c9c8de6dece::groups:AccessGroupId-6453e55b-8636-4884-85df-0c8d5b485d31","typeURI":"iam-groups/group","name":"Sample-access-group"},"reason":{"reasonCode":200},"severity":"normal","responseData":"{\"id\":\"AccessGroupId-6453e55b-8636-4884-85df-0c8d5b485d31\",\"name\":\"Sample-access-group\",\"description\":\"\",\"account_id\":\"81de6380e6232019c6567c9c8de6dece\",\"created_at\":\"2019-11-27T00:03:01Z\",\"created_by_id\":\"IBMid-060000JMJ2\",\"last_modified_at\":\"2019-11-27T00:03:01Z\",\"last_modified_by_id\":\"IBMid-060000JMJ2\"}","logSourceCRN":"crn:v1:bluemix:public:iam-groups:global:a/81de6380e6232019c6567c9c8de6dece:::","saveServiceCopy":true}

{"id":"3847d7b5-99a7-4364-bf54-7129fdb481dc","eventTime":"2019-11-27T00:05:17.92+0000","action":"iam-groups.member.add","outcome":"success","message":"IAM Access Groups: add member Sample-access-group","initiator":{"id":"IBMid-060000JMJ2","typeURI":"service/security/account/user","name":"LOPEZDSR@uk.ibm.com","host":{"address":"158.177.175.83"},"credential":{"type":"token"}},"target":{"id":"crn:v1:bluemix:public:iam-groups:global:a/81de6380e6232019c6567c9c8de6dece::groups:AccessGroupId-6453e55b-8636-4884-85df-0c8d5b485d31","typeURI":"iam-groups/member","name":"Sample-access-group"},"reason":{"reasonCode":200},"severity":"warning","requestData":"{\"iam_id\":\"IBMid-310000D73E\",\"type\":\"user\"}","responseData":"{\"iam_id\":\"IBMid-310000D73E\",\"type\":\"user\",\"created_at\":\"2019-11-27T00:05:17Z\",\"created_by_id\":\"IBMid-060000JMJ2\",\"status_code\":200}","logSourceCRN":"crn:v1:bluemix:public:iam-groups:global:a/81de6380e6232019c6567c9c8de6dece:::","saveServiceCopy":true}


Access group with 1 user:

7/Nov/2019:09:53:03 iam-groups IAM Access Groups: delete group test 
27/Nov/2019:09:53:03 iam-groups IAM Access Groups: delete members 
27/Nov/2019:09:53:03 iam-groups IAM Access Groups: delete rules -failure 

Access group with 2 users:

27/Nov/2019:09:53:12 iam-groups IAM Access Groups: delete group Sample-access-group 
27/Nov/2019:09:53:13 iam-groups IAM Access Groups: delete members 
27/Nov/2019:09:53:13 iam-groups IAM Access Groups: delete members 
27/Nov/2019:09:53:13 iam-groups IAM Access Groups: delete rules -failure  

