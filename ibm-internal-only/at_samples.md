---

copyright:
  years: 2019, 2020
lastupdated: "2020-03-11"

keywords: IBM Cloud, LogDNA, Activity Tracker, event definition

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


# AT samples
{: #at_samples}

This page shows samples of different AT type of actions:
{:shortdesc}

## List resources
{: #list}

Sample when a user lists resources that are available in a service instance, for example, see all certificates in Certificate Manager:





## CRUD actions with success outcome
{: #crud_success}

### Read action
{: #read}

```
{
    "id": "91a138d5-50b2-4b98-8ec6-cfb6becec3cf",
    "eventTime": "2020-03-11T09:28:35.15+0000",
    "action": "iam-groups.group.read",
    "outcome": "success",
    "message": "IAM Access Groups: read group at-logdna-admin",
    "initiator": {
        "id": "IBMid-xxxxxxxx",
        "typeURI": "service/security/account/user",
        "name": "xxxxx@uk.ibm.com",
        "host": {
            "address": "xxx.xxx.xxx.xxx"
        },
        "credential": {
            "type": "token"
        }
    },
    "target": {
        "id": "crn:v1:bluemix:public:iam-groups:global:a/xxxxxxxxxxxxxxxxxxxxxxx::groups:AccessGroupId-b56e5cd7-903f-4d6a-8f26-7f29b8f201a1",
        "typeURI": "iam-groups/group",
        "name": "at-logdna-admin"
    },
    "observer": {
        "name": "ActivityTracker"
    },
    "reason": {
        "reasonCode": 200
    },
    "severity": "normal",
    "responseData": "{\"id\":\"AccessGroupId-b56e5cd7-903f-4d6a-8f26-7f29b8f201a1\",\"name\":\"at-logdna-admin\",\"description\":\"\",\"account_id\":\"xxxxxxxxxxxxxxxxxxxxxxx\",\"created_at\":\"2019-03-25T12:57:19Z\",\"created_by_id\":\"IBMid-xxxxxxxx\",\"last_modified_at\":\"2019-03-25T12:57:19Z\",\"last_modified_by_id\":\"IBMid-xxxxxxxxx\"}",
    "logSourceCRN": "crn:v1:bluemix:public:iam-groups:global:a/xxxxxxxxxxxxxxxxxxxxxxx:::",
    "saveServiceCopy": true,
    "dataEvent": true
}
```
{: screen}


### Create action
{: #create}

```
{
    "logSourceCRN": "crn:v1:bluemix:public:cloud-object-storage:global:a/xxxxxxxxxxxxxxxxxxxxxxx:69002255-e226-424e-b6c7-23c887fdb8bf::",
    "dataEvent": "true",
    "saveServiceCopy": true,
    "initiator": {
        "id": "iam-ServiceId-2a456728-0cfc-4ece-a061-26d7be298645",
        "name": "ServiceId-2a456728-0cfc-4ece-a061-26d7be298645",
        "typeURI": "service/security/account/service-id",
        "host": {
            "address": "10.123.77.122",
            "agent": "ibm-cos-sdk-nodejs/1.4.3 linux/v10.15.3 callback"
        }
    },
    "target": {
        "name": "3a941d8f1f.2020-03-07.70.json.gz",
        "id": "crn:v1:bluemix:public:cloud-object-storage:global:a/xxxxxxxxxxxxxxxxxxxxxxx:69002255-e226-424e-b6c7-23c887fdb8bf:bucket:at-frankfurt",
        "typeURI": "cloud-object-storage/object",
        "host": {
            "address": "at-frankfurt.s3.private.eu-de.cloud-object-storage.appdomain.cloud"
        }
    },
    "action": "cloud-object-storage.object.create",
    "outcome": "success",
    "reason": {
        "reasonCode": "200",
        "reasonType": "OK"
    },
    "severity": "normal",
    "eventTime": "2020-03-08T12:22:01+00:00",
    "responseData": {
        "serviceInstanceId": "69002255-e226-424e-b6c7-23c887fdb8bf",
        "bucketLocation": "eu-de",
        "requestId": "9aa6b5a9-fc03-42bb-9794-2a1241696545",
        "objectLengthInBytes": "22319",
        "objectLifecycle": {}
    },
    "message": "Cloud Object Storage: create object 3a941d8f1f.2020-03-07.70.json.gz in bucket at-frankfurt"
}
```
{: screen}



### Update action
{: #update}

```

```
{: screen}


### Delete action
{: #delete}

```

```
{: screen}

## CRUD actions with success failure
{: #crud_success}

### Read action
{: #read-fail}

```

```
{: screen}

### Create action
{: #create-fail}

```

```
{: screen}


### Update action
{: #update-fail}

```

```
{: screen}



### Delete action
{: #delete-fail}

```

```
{: screen}

