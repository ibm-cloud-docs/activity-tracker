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


# Event fields
{: #ibm_event_fields}

This page defines all of the fields used by an Activity Tracker event. Events in Activity Tracker are expressed in JSON.
{:shortdesc}


Join the AT team in the stakeholders meeting that is run fortnightly on Fridays. [Subscribe and enroll to the meeting](https://ec.yourlearning.ibm.com/w3/subscription/series/10008720). The presentations and recordings of these sessions are available in the box folder [Recordings and ppts](https://ibm.box.com/s/47sqtlhgg21ck3nsuz9ib4kwbgupjlrd).
{: important}


## Introduction
{: #intro}

The schema of an Activity Tracker (AT) event is based on [the CADF standard](http://www.dmtf.org/sites/default/files/standards/documents/DSP0262_1.0.0.pdf) (Cloud Auditing Data Federation). This is an open model for events that is suitable for auditing.

The CADF event model requires 5 components. For Activity Tracker, these translate into:

1. `observer`: always Activity Tracker
2. `initiator`: an end user, or an internal (IBM) or external service
3. `action`: the activity that the initiator is performing, such as calling a REST API
4. `target`: the IBM service that the action is performed against
5. `outcome`: the result of the action; "success" or "failure"

<img src="images/CADF-event.png" alt="CADF event model"  height="200" width="300"  />

Following is a sample event that includes the fields that are required. You can use it as an example of a CADF event. Each of the fields is explained in the rest of this page.


```js
{
    // REQUIRED FIELDS:

    "initiator": {
        "id": "IBMid-xxxxxxxxxx",
        "name": "xxxxm@us.ibm.com",
        "typeURI": "service/security/account/user",
        "credential": {
            "type": "token"
        },
        "host": {
            "address": "169.62.30.22"
        }
    },
    "target": {
        "id": "crn:v1:bluemix:public:iam-groups:global:a/7131c65c6ad70bdc209bb564997a5f1c::groups:AccessGroupId-89094792-aa7c-48de-a1a0-7cbac484f072",
        "name": "Test Group",
        "typeURI": "iam-groups/member"
        // host.address is optional here
    },
    "action": "iam-groups.member.add",
    "outcome": "success",
    "reason": {
        "reasonCode": 200,
        "reasonType": "OK"
    },
    "severity": "warning",
    "eventTime": "2019-11-03T21:40:53.94+0000",

    // The rest of the fields are not part of CADF spec:
    "message": "IAM Access Groups: add member Test Group",
    "logSourceCRN": "crn:v1:bluemix:public:iam-groups:global:a/7131c65c6ad70bdc209bb564997a5f1c:::",
    "saveServiceCopy": true,

    // id is optional
    "id": "916faca9-4644-41ce-9e7c-b40a04738a16",

    "observer": {
        "name": "ActivityTracker"
    },

    // requestData is required for events that modify resources in the IBM Cloud and to add info that clarifies the action on an audit
    "requestData": {
        // This object is defined by the service
        // ResourceGroupID is optional
        "resourceGroupId": "xxxx",
        // updateType, initialValue, newValue are REQUIRED when the action of the event is UPDATE or the event reports on a change to the object
        "updateType": "xxxx",
        "initialValue": "xxxxx",
        "newValue": "xxxxxx",
        "reasonForFailure": "xxxxxx",
        "platformSource" : "Watson xxxxx"
    },

    // responseData is optional
    "responseData": {
        // This object is defined by the service
        "iamId": "IBMid-550000HRWG",
        "type": "user",
        "createdAt": "2019-11-03T21:40:53Z",
        "createdById": "IBMid-120000QUJ0",
        "statusCode": 200
    },
    "dataEvent": false

}
```
{: codeblock}


## Checking an AT event
{: #validate}

You must check the **formatting of each of its fields**, the **platform_service** name, and also the **quality of the data**.
{: note}

To validate the formatting, you can use the [Activity Tracker linter tool ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.ibm.com/Yuqian-Chen/event-linter-web/blob/master/README.md){:new_window}. **Notice that this tool is offered and supported on a best-effort basis.** You can also use this tool through the following URL [AT linter tool ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://eventlinter.mybluemix.net/){:new_window}.

* If your event action is being reported as not valid, check the list of actions in the code. If it is not listed there, notify the AT team at the `AT Office hours & Stakeholders meeting`.
* Validate that the initiator IP address is not an IBM IP.

To check the quality of the data, verify that the data provided by the event includes the information required for auditing your service. For example, if you update the name of a resource, indicate the old name and the new name. Use the requestData and responseData fields to include additonal information.

To check the **platform_service** name, check the service name displayed that is displayed in the IBM section for your events. It should be set to the name of your service. 

To engage the AT tema to review your service's AT event prior to One Cloud badging, you must open an issue in the following git repo: [AT repo](https://github.ibm.com/activity-tracker/customer-issues/issues). Select the issue type `AT review`.
{: important}




## Event fields provided by the service to comply with AT guidelines
{: #mandatory}


### action (string)
{: #action}

This field indicates the action that triggers an event. 
{: note}

To identify the actions that a service should enable to generate an AT event, you can check the IAM actions that users can perform, the user actions that incur on resource changes in your service, etc. Then, define the list of actions. IAM and AT actions should match.
{: tip}

The format of this field is the following:

```
serviceName.objectType.action
```
{: codeblock}

Where 

* `servicename` is the name of the service as indicated under the **Name** column in the [global catalog](https://globalcatalog.cloud.ibm.com/search?q=).

    [Learn more about CRNs](https://github.ibm.com/ibmcloud/builders-guide/blob/master/specifications/crn/CRN.md)

* `objectType` describes the resource or resource attribute on which the action is requested. 

    For example, in COS, a user can create a bucket. The action triggered would be cloud-object-storage.bucket.create where `objectType = bucket`  However, if the action is to creata the ACL of the bucket, the action would be `cloud-object-storage.bucket-acl.create` where `objectType = bucket-acl`

* `action` defines the task requested by the user.  

    Valid actions are: `add`, `bulkdelete`, `create`, `read`, `update`,`delete`, `backup`, `build`, `capture`, `configure`, `deploy`, `disable`, `enable`, `get`, `import`, `inspect`, `list`, `monitor`, `pull`, `push`, `restore`, `start`, `stop`, `undeploy`, `receive`, `reimport`, `remove`, `send`, `set`, `set-on`, `set-off`, `authenticate`, `read`, `renew`, `revoke`, `allow`, `deny`, `evaluate`, `notify`, `rotate`

    Not valid actions are: `info`, `unknown`

    More values will be added as needed.

**Use a dot `.` to separate the 3 parts that define the action field (serviceName, objectType, action).**
{: important}

**Use a dash `–` to separate complex objectTypes to make it more readable to the users.**
{: important}

The following table shows some actions and sample events:

| Action      | Sample     |
|-------------|------------|
| `add`       | `containers-kubernetes.usersubnet.add` |
| `allow`     | |
| `attach`    | `global-search-tagging.tag.attach`  |
| `authenticate` | |
| `backup`    | |
| `capture`   | |
| `configure` | |
| `connect`   | `mobile-foundation.server-db.connect` |
| `create`    | `containers-kubernetes.alb.create` |
| `delete`    | `cloudcerts.certificate.delete` |
| `deny`      | |
| `deploy`    | |
| `detach`    | `global-search-tagging.tag.detach`  |
| `disable`   | |
| `enable`    | |
| `evaluate`  | |
| `export`    | `toolchain.pipeline-job-execution.export`|
| `import`    | `cloudcerts.certificate.import` |
| `inspect`   | `container-registry.image.inspect`   |
| `list`      | `cloudcerts.certificates.list` </br>`container-registry.image.list` |
| `monitor`   | |
| `notify`    | |
| `pull`      | `container-registry.image.pull` |
| `push`      | `container-registry.image.push` |
| `read`      | `cloudcerts.certificates.read` </br> `kms.policies.read`|
| `receive`   | |
| `reimport`  | `cloudcerts.certificate.reimport` |
| `remove`    | |
| `renew`     | |
| `restore`   | `<service_id>.backup.restore` |
| `revoke`    | |
| `rewrap`    | `kms.secrets.rewrap`  |
| `scale`     | `<service_id>.resources.scale`       |
| `search`    | `cloudcerts.certificates-metadata.search` |
| `send`      | |
| `set-on`    | |
| `set-off`   | |
| `start`     | |
| `stop`      | |
| `test`      | `cloudcerts.notification-channel.test` |
| `undeploy`  | |
| `update`    | `containers-kubernetes.logging-config.update` |
{: caption="Table 1. Actions and samples" caption-side="top"}


### dataEvent (boolean)
{: #dataEvent}

This field specifies the type of event, whether it is a management event or a data event.
{: note}

* For a `management event`, set this field to **false**.
* For a `data event`, set this field to **true**.

[Learn more](/docs/Activity-Tracker-with-LogDNA?topic=logdnaat-ibm_faq#types-of-events).




### eventTime (string)
{: #eventTime}

This field indicates the timestamp when the event was created. 
{: note}

The LogDNA timestamp is set from eventTime.
{: important}
  
The date is represented as Universal Time Coordinated (UTC). 

The format of this field is: 

```
YYYY-MM-DDTHH:mm:ss.SS+0000
```
{: codeblock}
  
* The letter `T` in the date time syntax must always be upper case.  
  
For example: 2017-10-19T19:07:50.32+0000
  
For example, some java sample code to generate the eventTime: This code is provided as-is and is not supported nor maintained by the AT team.

```java
import java.time.ZonedDateTime;
import java.time.format.DateTimeFormatter;

public class EventTime {        
    public static void main(String[] args) {        
        System.out.println(getCurrentATEventDateFormat());    
        }    
    public static String getCurrentATEventDateFormat() {        
        ZonedDateTime date = ZonedDateTime.now();        
        DateTimeFormatter formatter = DateTimeFormatter.ofPattern("yyyy-MM-dd'T'HH:mm:ss.SSZ");        
        return date.format(formatter);    
        }
    }
```
{: codeblock}



### initiator.id (string)
{: #initiator.id}

ID of the initiator of the action. 
{: note}

* When the request includes an IAM  token, set this value to the **access_token.iam_id** field value that is available in the IAM token that your service gets to run the action.
* For Watson services that get the initiator information through the Watson Gateway header, set this value to the **x-watson-userinfo** &gt; **bluemix-subject**.
* For actions (events)) that are published to Hyperwarp by an IBM Cloud service, and subscribed by an IBM Cloud service, set this value as follows:

    Publisher service: Set this field to the user or service ID that requests the action: **access_token.iam_id**. 

    Subscriber service:  Set this field to the **publisher**.


| Who is the initiator                       | Value                                                                   | Example          |
|--------------------------------------------|-------------------------------------------------------------------------|------------------|
| `Certificate`                              | `access_token.iam_id`                                                   | `CertificateId-769b5c65-0165-4c89-847d-9660b1632e14` |
| `User in the user's account with an IBMID where the action is requested` | `access_token.iam_id`                     | `IBMid-xxxxxxxx` | 
| `ServiceID in the user's account where the action is requested`          | `access_token.iam_id`                     | `iam-ServiceId-769b5c65-0165-4c89-847d-9660b1632e14` |
| `ServiceID not defined in the customer account and owned by a service`   | `access_token.iam_id`                     | `iam-ServiceId-769b5c65-0165-4c89-847d-9660b1632e14` |
| `Action triggered via Hyperwarp`           | Publisher service: `access_token.iam_id`  </br>Subscriber service: `publisher`  | `iam-ServiceId-769b5c65-0165-4c89-847d-9660b1632e14` |
| `Watson service - initiator is a user`     | `bluemix-subject`                                                       | `IBMid-xxxxxxxx` |
| `Watson service - initiator is a service ID` | `bluemix-subject`                                                     | `iam-ServiceId-769b5c65-0165-4c89-847d-9660b1632e14` |
| `No initiator - Action triggered by service` `(1)`  | Leave empty                                                    | `` | 
{: caption="Table 2. Guidance setting initiator.id" caption-side="top"}

`(1)` The action does not have an initiator because the event that is generated reports an action on a customer resource and this action is executed by the service as a scheduled job.

### initiator.name (string)
{: #initiator.name}
 
Username of the user that initiated the action.
{: note}

* When the request includes an IAM  token, set this value to the **access_token.sub** field value that is available in the IAM token that your service gets to run the action.
* For Watson services that get the initiator information through the Watson Gateway header, set this value to the **x-watson-userinfo** &gt; **bluemix-iamid**.
* For actions (events)) that are published to Hyperwarp by an IBM Cloud service, and subscribed by an IBM Cloud service, set this value as follows:

    Publisher service: Set this field to the user or service ID that requests the action: **access_token.sub**. 

    Subscriber service:  Set this field to the **event_properties.publisher_name**.


| Who is the initiator                                                                 | Value                                   | Example          |
|--------------------------------------------------------------------------------------|-----------------------------------------|------------------|
| `User is a member in the customer account where the action is requested`             | `access_token.sub`                      | `joe@ibm.com`    | 
| `ServiceID in the user's account where the action is requested`                      | `access_token.sub`                      | `ServiceId-769b5c65-0165-4c89-847d-9660b1632e14` |
| `ServiceID not defined in the customer account and owned by a service`               | Set this field to the value in the  **Display Name** column in the [global catalog](https://globalcatalog.cloud.ibm.com/search?q=) for your service. In the catalog, some services include IBM Cloud nad others do not. To make sure it is clear that it is an IBM owned ID, add `IBM Cloud` to the name if your full legal name includes it.  If not sure, contact the AT team in slack. | `IBM Cloud Certificate Manager` |
| `Certificate`                                                                        | `access_token.sub`                      | `CertificateId-769b5c65-0165-4c89-847d-9660b1632e14` |
| `Action triggered via Hyperwarp`                                                     | `event_properties.publisher_name`       | `iam-ServiceId-769b5c65-0165-4c89-847d-9660b1632e14` |
| `Watson service - initiator is a user`                                               | `bluemix-iamid`                         | `IBMid-xxxxxxxx` |
| `Watson service - initiator is a service ID`                                         | `bluemix-iamid`                         | `iam-ServiceId-769b5c65-0165-4c89-847d-9660b1632e14` |
| `No initiator - Action triggered by service` `(1)`                                   | `IBM`                                   | `IBM`            |
{: caption="Table 3. Guidance setting initiator.name" caption-side="top"}

`(1)` The action does not have an initiator because the event that is generated reports an action on a customer resource and this action is executed by the service as a scheduled job.

 


### initiator.typeURI (string)
{: #initiator.typeURI}

This field defines the type of the source of the event.
{: note}

Valid values are: `service/security/account/user`, `service/security/account/serviceid`, `service/security/client/certificateid`, `service/security/clientid`

| Who is the initiator                                                                 | Value                                   | 
|--------------------------------------------------------------------------------------|-----------------------------------------|
| `User is a member in the customer account where the action is requested`             | `service/security/account/user`         | 
| `ServiceID in the user's account where the action is requested`                      | `service/security/account/serviceid`    | 
| `ServiceID not defined in the customer account and owned by a service`               | `service/security/account/serviceid`    |
| `Certificate`                                                                        | `service/security/client/certificateid` | 
| `Action triggered via Hyperwarp`                                                     | `service/security/account/serviceid`    |
| `Watson service - initiator is a user`                                               | `service/security/account/user`         |
| `Watson service - initiator is a service ID`                                         | `service/security/account/serviceid`    |
| `No initiator - Action triggered by service` `(1)`                                   | `service/security/account/service`      |
| `Registered IAM UI or service` `(2)`                                                 | `service/security/clientid`             |
{: caption="Table 4. Guidance setting initiator.tyepURI" caption-side="top"}

`(1)` The action does not have an initiator because the event that is generated reports an action on a customer resource and this action is executed by the service as a scheduled job.

`(2)` For example, when Cloud Console logs in users with IAM, they need a client id / secret. In this case, the Token Service will set this value for the initiator.typeURI field in the AT event.
    


### initiator.credential.type (string)
{: #initiator.credential.type}

This field defines the type of credential that is used by the initiator to run the action.
{: note}

Valid values are: `token`, `user`, `apikey`, `certificate`

Guidance setting the value of this field:

| Value of `access_token.grant_type` in IAM token                 | Value of `initiator.credential.type` in AT event |
|-----------------------------------------------------------------|--------------------------------------------------|
| `urn:ibm:params:oauth:grant-type:apikey`                        | `apikey`                                         |
| `urn:ibm:params:oauth:grant-type:delegated-refresh-token`       | `token`                                          |
| `urn:ibm:params:oauth:grant-type:passcode`                      | `user`                                           |
| `authorization_code`                                            | `user`                                           |
| `password`                                                      | `user`                                           |
{: caption="Table 5. Guidance setting credential type" caption-side="top"}


### initiator.host.address (string)
{: #initiator.host.address}

This field provides information about the address where the request came from. 
{: note}

Set this field to the originating IP address. 

The format of this field is:

```
xxx.xxx.xxx.xxx
```
{: codeblock}

**For services that run on Kubernetes:**

By default, the source IP address of the client request is not preserved. When a client request to your app is sent to your cluster, the request is routed to a pod for the load balancer (LB) service that exposes the ALB. If no app pod exists on the same worker node as the load balancer service pod, the load balancer forwards the request to an app pod on a different worker node. The source IP address of the package is changed to the public IP address of the worker node where the app pod is running. 

To preserve the source IP, you must change the LB service configuration to have the **externalTrafficPolicy** set to `Local` instead of `Cluster`. 
* The change to the LB service is only needed when an ALB is created or enabled, and only if the LB service has `"externalTrafficPolicy":"Cluster"`.  
* If it is already set with `"externalTrafficPolicy":"Local"`, then the change is not required. 
* There is no need to do this each time a user updates their deployment, or microservice.
* If you create or enable any additional ALBs for your service, you must enable source IP preservation for the ALBs.

To be able to get the originating IP address, complete the following steps to enable IP preservation to all enabled public or private ALBs:  they'll need to first enable source IP preservation and then have code to actually fetch that off of a header
1. Enable source IP preservation. [Learn more](/docs/containers?topic=containers-ingress-settings#preserve_source_ip).
2. Obtain the IP from the `x-forwarded-for` property in the header. 


 
### logSourceCRN  (string)
{: #logSourceCRN}

This field determines where a copy of the event is saved for the user. 
{: note}

This field must be set to the CRN of the service instance that generates the event. The information in the CRN indicates the user's account ID and the instance ID of your service in the user's account.

The format of this field is the following:

```
crn:version:cname:ctype:service-name:location:scope:service-instance::
```
{: codeblock}

Where:
* `service-name` is as defined in the `action` field.
* `location` must be set to the region or datacenter where the event occurred. The location can only be set to **global** if the action does not pertain to a specific location, for example, IAM actions. Events that have location set to *global* go to the *global endpoint* that is currently in Frankfurt.
* `scope` must be set to the user's account. It must start with "a/", followed by the cloud account ID. LogDNA does not support the CloudFoundry values of `scope` ("o/" for the org or "s/" for the space).
* `service-instance` must be set to the ID of the instance in the user's account.

If you leave out logSourceCRN, it only saves the event to your account, not to the user's account. 
{: important}

If you leave out logSourceCRN AND set saveServiceCopy:false, then the event is not saved at all.
{: important}

#### Information on how to set the logSourceCRN for services that on-boarded with the resource-controller
{: #logSourceCRN-1}

When an instance is provisioned by a user, the request calls the service’s broker via [IBM Cloud Open Service Broker API ![External link icon](../icons/launch-glyph.svg "External link icon")](https://test.cloud.ibm.com/apidocs/resource-controller/ibm-cloud-osb-api#create-provision-a-service-instance){: new_window}. The response includes the instance’s CRN.

When a user makes a call to one of your service's API endpoints, the user must pass the CRN as part of the call (can be a header, request Path, depends on your API), which you can then use to populate `target.id` and `logSourceCRN`.





### message (string)
{: #message}

Message that is associated with the event. 
{: note}

The format of this field is: 

```
serviceName: action objectType target.name [custom data per service][outcome]
```
{: codeblock}

Where 

* `servicename` is the name of the service as indicated under the **Display Name** column in the [global catalog](https://globalcatalog.cloud.ibm.com/search?q=).  
* `action` matches the action component as described in the CADF *action* field of the event. Must be in lowercase. 
* `objectType` matches the objectType component as described in the CADF *action* field of the event. Must be in lowercase. 
* `target.name` matches the value of the CADF field *target.name*. If a name is not available, leave it out. 
* `[custom data per service]` has the format: 

    ```
    [for resourceType resourceID][custom information]
    ```
    {: codeblock}
    
    You can add information from data that is available through the AT fields requestData and responseData lowercase. 
    
    When the action applies to a sub resource component, for example, a policy for a user, or a worker for a cluster, the section [for resourceType resourceID] should be included. 
    
    `resourceType` defines the type of resource, for example, cluster, access group, serviceID, etc. 
    
    `resourceID` specifies the ID of the resource type to which the action applies. 
    
    The section `[custom information]` should include any relevant information that you consider important to the user for your event. 

* `outcome` is set when the `outcome` field reports an action that is NOT `success`. 

    The format is 
    
    ```
    -outcome
    ```
    {: codeblock}
    
    Where `outcome` matches the outcome value as described in the CADF *outcome* field of the event. Valid values in message are `failure` and `warning`.


For example: 

```
IAM Identity Service: delete user-apikey KeyProtectTest -failure  
Key Protect: list secrets 
IAM Identity Service: login user-apikey containers-kubernetes-key
```
{: codeblock}


  
### requestData (JSON)
{: #requestData}

Add any information here that will enhance the user experience going through ther audit trail of your service events.  
{: note}

* Must be formatted as JSON.  Not stringified JSON, as was required by legacy AT
* Must include information that is required to clarify the action. For example, an event with action create might require information on the Software verison. An update event requires information on the initial value and final value. There may be cases where data is sensitive or too long, in this situation, add information about the type of update
* Must be added as value pairs of information.
* Must be formatted in camel case style.

Some fields:
* [Optional] `resourceGroupId`: Set to the CRN of the resource group
* [`Required for update action`] `updateType`: Indicate if it is a name change, description change, or other type Valid values are: `Name changed`, `Description changed`, and others (the services may have their own set of values and might vary per service)
* [`Required for update action`] `initialValue`: Add the original value of the resource that is updated
* [`Required for update action`] `newValue`: Add the new value requested in the action
* [`Required for Watson services`] `platformSource`: Add the UI catalog name of your service, for example, `Watson Discovery` This helps users identify your events quickly by your service, since the platform_source value is shared across all Watson services.
* [Optional] `customizationId`
* [Optional] `environmentId`
* [Optional] `reasonForFailure`:  Include additional info as to why the action has failed.


### responseData (JSON)
{: #responseData}
 
Add any information here that will enhance the user experience going through ther audit trail of your service events. 
{: note}

* Must be formatted as JSON.  Not stringified JSON, as was required by legacy AT
* Must include information that is required to clarify the action.
* Must be added as value pairs of information.
* Must be formatted in camel case style.

Some fields:
* [Optional] `targetAddress.type`: Set to the type of endpoint. Valid values are: `public` and `private`, in lowercase.


### observer.name (string)
{: #observer.name}

This field must be set to the fixed value **ActivityTracker**.
{: note}




### outcome (string)
{: #outcome}

This field indicates the result of the action.
{: note}

Valid values are: `success`, `pending`, `failure`, `unknown`

Make sure that all values are in lowercase.
{: tip}
 
#### Use case 1: Someone calls an API to delete a resource that does not exist (RC 404)
{: #case1}

If someone calls an api to delete a resource that doesn't exist, the event will report `404 not found error` and the outcome will be `failure`.

In this situation, you must set the following fields:
* `reason.reasonType = resource not found`
* `outcome = failure` because the action cannot be completed since the object does not exist.
* `reason.reasonCode = 404`
* `target.id =` CRN of the object that was requested to be deleted
* `target.name` might be left empty if you do not have the human readable name of the object to be deleted.

#### Use case 2: Someone calls an API and does not have the authorization to execute that action (RC 403)
{: #case2}

If someone calls an api to delete a resource, and they do not have the authorization to execute the task, the event will report `403 forbidden` and the outcome will be `failure`.

In this situation, you must set the following fields:
* `reason.reasonType = forbidden - not authorized`
* `outcome = failure` 
* `reason.reasonCode = 403`
* `target.id =` CRN of the object on which the action was requested
* `target.name` name of the object




### reason.reasonCode (numeric)
{: #reason.reasonCode}

This field returns the HTTP response code of the action requested.
{: note}

Use the values that are defined in [HTTP response codes](https://www.iana.org/assignments/http-status-codes/http-status-codes.xml).

If your actions are not REST API calls, set to 200 for success outcome and 500 for failure. Add in `reason.reasonType` information about the failure cause.

### reason.reasonType (string)
{: #reason.reasonType}

This field provides additional information about the result of the action requested. 
{: note}

This field is REQUIRED for all events. 

When the outcome is failure, you can also add additional information in the field `requestData.reasonForFailure`.
{: tip}


To set this field, you can use the description associated to the reasonCode (value) defined in [HTTP response codes](https://www.iana.org/assignments/http-status-codes/http-status-codes.xml). For example, for a reason.reasonCode = 200, set reasonType to **OK**.

You can also set it to any message or information that you might have available in your service when you receive a specific reasonCode and outcome.


### saveServiceCopy (boolean)
{: #saveServiceCopy}

This field is used to control whether the IBM service gets a copy of the event or not.
{: note} 

The default value is *true* but the field must be set explicitly. 

* To save a copy of the event in your ATS ( in your service's account), set this field to **true**.
* If you do not want a copy of the events saved in your ATS, set this field to **false**. 



### severity (string)
{: #severity}

This field defines the level of threat an action may have on the Cloud.
{: note}

Valid values are: `normal`, `warning`, and `critical`

* Set to **normal** for routine actions in the Cloud. 

    For example: starting an instance,  refreshing a token, etc  

* Set to **warning**  when an action fails, or when a Cloud resource is updated or its metadata is modified. 

    For example: updating the version of a worker node, renaming a certificate, renaming a service instance, etc  

* Set to **critical** when the action affects security in the Cloud like changing credentials of a user, deleting data, unauthorized access to work with a Cloud resource.  

    For example: adding or removing proviledges to a user, deleting a security key, deleting logs, running an action against a resource where the user does not have permissions to work with, etc.

For example, if the action is:
* `create`: Set the value to `normal` 
* `update`: Set the value to `warning`
* `delete`: Set the value to `critical`


For the deletion of low level data resources that are not critical, like objects in a bucket in COS, which is a routine action for that service, severity for deleting an object should be set to normal as this is `routine action in the cloud`, and the severity for deleting a bucket should be set to critical.

When the reasonCode for an API call is any of the following values, you can apply a a second set of criteria to determine the value of severity.  The following list outlines the reasonCodes and expected severity values:

| reasonCode | description                   | severity       |
|------------|-------------------------------|----------------|
| `400`      | `Bad Request`                 | `warning`      |
| `401`      | `Unauthorized`                | `critical`     |
| `403`      | `Forbidden`                   | `critical`     |
| `409`      | `Conflict`                    | `warning`      |
| `424`      | `Failed Dependency`           | `warning `     |
| `500`      | `Internal Server Error`       | `warning`      |
| `502`      | `Bad Gateway`                 | `warning`      |
| `503`      | `Service Unavailable`         | `critical`     |
| `504`      | `Gateway Timeout`             | `warning`      |
| `505`      | `HTTP Version Not Supported`  | `warning`      |
| `507`      | `Insufficient Storage`        | `critical`     |
{: caption="Table 3. Severity value for some reason codes" caption-side="top"}




### target.id (string)
{: #target.id}

This value informs about the cloud resource on which the action is executed. Must be set to the CRN of the resource.
{: note}

[CRN guidelines](https://github.ibm.com/ibmcloud/builders-guide/blob/master/specifications/crn/CRN.md)

A cloud resource can be a service, a service instance, or a service sub-resource (such as a user API key, a certificate, etc). Set this value to the resource CRN when the action is executed on a specific resource. For example:

* If the action is executed on a service, set the field to the service's crn value. 

    ```
    crn:v1:{cname}:{ctype}:{service-name}:{location}:a/{IBM-account}:{service-instance}::
    ```
    {: coddeblock}

* If the action requested is on a resource type, set the value to the CRN of the resource type. 

    ```
    crn:v1:{cname}:{ctype}:{service-name}:{location}:a/{IBM-account}:{service-instance}:{resource-type}:{resource}
    ```
    {: codeblock}

    For example, if the action requested is on a certificate, set the value to the CRN of the certificate. 

    ```
    crn:v1:{cname}:{ctype}:{service-name}:{location}:a/{IBM-account}:{service-instance}:certificate:<ID of the certificate>
    ```
    {: codeblock}


#### Information on how to set the target.id for services that on-boarded with the resource-controller
{: #logSourceCRN-1}

When an instance is provisioned by a user, the request calls the service’s broker via [IBM Cloud Open Service Broker API ![External link icon](../icons/launch-glyph.svg "External link icon")](https://test.cloud.ibm.com/apidocs/resource-controller/ibm-cloud-osb-api#create-provision-a-service-instance){: new_window}. The response includes the instance’s CRN.

When a user makes a call to one of your service's API endpoints, the user must pass the CRN as part of the call (can be a header, request Path, depends on your API), which you can then use to populate `target.id` and `logSourceCRN`.


### target.name (string)
{: #target.name}

Set this value to the human readable name of the cloud resource on which the action is executed.
{: note}

The value is a human readable name of the service, service instance or service sub-resource that matches the CRN specified on the field target.id 	

For example, 
* When the action requested is on the instance of your service ( rename an instance), the name of the service must match the name as indicated under the **Display Name** column in the [global catalog](https://globalcatalog.cloud.ibm.com/search?q=).
* If the action requested is on a certificate, set the value to the name of the certificate that a user could see in the Cloud UI.
* If you have resources that do not have a name, set this value to  `<resource-type>-<ID of the resource modified>` For example, `model-xxxxx`

### target.typeURI (string)
{: #target.typeURI}

This field defines the type of the target of the event. 
{: note}

This field does not include action information. 

The format of this field is: 

```
serviceName/objectType/attribute
```
{: codeblock}

Where

* `servicename` is the name of the service as indicated under the **Name** column in the [global catalog](https://globalcatalog.cloud.ibm.com/search?q=).
* `objectType` is the resource on which the action is run.


This field does not include action information.

Use forward slash `/` to separate complex objectTypes to make it more readable to the users. For example, `cloud-object-storage/bucket/cors`

For example, check out the following samples:

| action                                            | target.typeURI                                  |
|---------------------------------------------------|-------------------------------------------------|
| cloudcerts.certificate.import                     | cloudcerts/certificate                          |
| container-registry.namespace.create               | container-registry/namespace                    |
| kms.secrets.read                                  | kms/secrets                                     |
| mqcloud.queue-manager.update                      | mqcloud/queue-manager                           |
| cloud-object-storage.instance.create              | cloud-object-storage/instance                   |
| cloud-object-storage.object-multipart.create      | cloud-object-storage/object/multipart           |
{: caption="Table 4. target.typeURI examples" caption-side="top"}


## Optional event fields provided by the service to comply with CADF
{: #optional}


### id (string)
{: #id}

Use this field to correlate events.
{: note}

This field is optional.


### target.host.address (string)
{: #target.host.address}

Use this field to set the IP Address or URL of the target service.
{: note}

### tags (array of strings)
{: #tags}

Use this field to attach tags to an event.
{: note}



## Reserved CADF fields
{: #reserved}

These are reserved fields for Activity Tracker that might be used in the future.

Do not set these fields.
{: important}

### eventType (string)
{: #eventType}

Set this field to **activity** for Activity Tracker. (Other CADF values are "monitor" and "control".
{: note}


### typeURI (string)
{: #typeURI}

This field would be set to: `http://schemas.dmtf.org/cloud/audit/1.0/event`.

### type (string)
{: #type}

This field would be set to `ActivityTracker`.
{: note}

### observer.id (string)
{: #observer.id}

This field would be set to the CRN of the AT instance that the event is sent to.

### observer.typeURI (string)
{: #observer.typeURI}

This field would be set to `security/edge/activity-tracker`.




## Differences in legacy and LogDNA Activity Tracker events
{: #legacy_vs_new_at}

The legacy Activity Tracker service was deprecated in October 2019.
It is replaced by Activity Tracker with LogDNA, which supports a number of improvements in the format of the events.

The events that worked on legacy Activity will continue to work on the new Activity Tracker with LogDNA.
However, services should consider the following improvements:

* `requestData`/`responseData` can be any JSON object, not just stringified JSON. A JSON object is now preferred over stringified JSON, for better parsing and searching. All events should include `requestData` and `responseData`, even if empty.
* The `dataEvent` flag is supported. `true` indicates a data event. `dataEvent` defaults to `false`, but events should specify `false` explicitly. Refer [here](https://test.cloud.ibm.com/docs/Activity-Tracker-with-LogDNA/ibm-internal-only?topic=logdnaat-ibm_event_fields#optional) for more info.
* The `observer` fields are no longer discouraged, and `observer.name` should be set to "ActivityTracker". `observer.name` may be used in the future to support sending events to AT via stdout.
* Events should have the CADF fields at the top level, and no longer encapsulate the CADF fields in the `payload` structure. When an event does have `payload`, LogDNA removes it and promotes its internal fields to the top level.
* The `meta` object is now ignored. Services should remove it.
* The following fields were used by legacy AT, but should now be removed:
   * `attachments`
   * `requestHeader`, `requestBody`, `responseHeader`, `responseBody`
   * `latencies`

## Change control
{: #change}

The following table outlines when the AT guidelines change to adapt to new requirements:

| Field                              | Required                                          | Field required  | Guideline changes               |
|------------------------------------|---------------------------------------------------|-----------------|---------------------------------|
| `action`                           | ![Checkmark icon](../../icons/checkmark-icon.svg) |  January 2019   |                                 | 
| `dataEvent`                        |                                                   |  December 2019  |                                 |
| `eventTime`                        | ![Checkmark icon](../../icons/checkmark-icon.svg) |  January 2019   |                                 | 
| `id`                               |                                                   |                 |                                 | 
| `logSourceCRN` `[*]`               | ![Checkmark icon](../../icons/checkmark-icon.svg) |  June 2019      | June 2019 - when changes to migrate to LogDNA were requested                                 |
| `message` `[*]`                    | ![Checkmark icon](../../icons/checkmark-icon.svg) |  June 2019      |                                 |
| `initiator.id`                     | ![Checkmark icon](../../icons/checkmark-icon.svg) |  January 2019   |                                 |
| `initiator.name`                   | ![Checkmark icon](../../icons/checkmark-icon.svg) |  January 2019   |                                 | 
| `initiator.typeURI`                | ![Checkmark icon](../../icons/checkmark-icon.svg) |  January 2019   |                                 |
| `initiator.credential.type`        | ![Checkmark icon](../../icons/checkmark-icon.svg) |  January 2019   |                                 |
| `initiator.host.address`           | ![Checkmark icon](../../icons/checkmark-icon.svg) |  January 2019   |                                 |
| `observer.name`                    | ![Checkmark icon](../../icons/checkmark-icon.svg) |  December 2019  |                                 |
| `outcome`                          | ![Checkmark icon](../../icons/checkmark-icon.svg) |  January 2019   |                                 |
| `reason.reasonCode`                | ![Checkmark icon](../../icons/checkmark-icon.svg) |  January 2019   |  December 2019 - check 403 is being generated to report on unauthorized access to run an action |
| `reason.reasonType`                | ![Checkmark icon](../../icons/checkmark-icon.svg) |  December 2019  |  December 2019 - check that it is populated for failure events </br>January 2020 - required for all outcomes |
| `requestData`  `[*]`               | ![Checkmark icon](../../icons/checkmark-icon.svg) |  January 2019   |  December 2019 - check and request that update events all include information about the update (3 new subfields added to add consistency in the user experience) |
| `responseData` `[*]`               |                                                   |                                                   |
| `saveServiceCopy`  `[*]`           | ![Checkmark icon](../../icons/checkmark-icon.svg) |  June 2019      |  June 2019 - when changes to migrate to LogDNA were requested |
| `severity`                         | ![Checkmark icon](../../icons/checkmark-icon.svg) |  January 2019   |                                 |
| `target.id`                        | ![Checkmark icon](../../icons/checkmark-icon.svg) |  January 2019   |                                 |
| `target.name`                      | ![Checkmark icon](../../icons/checkmark-icon.svg) |  January 2019   |                                 |
| `target.typeURI`                   | ![Checkmark icon](../../icons/checkmark-icon.svg) |  January 2019   |                                 |
| `target.host.address`              |                                                   |                 |                                 | 
| `tags`                             |                                                   |                 |                                 | 
{: caption="Table 4. Change control for list of event fields in an AT event" caption-side="top"}

`[*]` These fields are extensions of the CADF specification.

Implementation change control:

| Detail                             | Required                                          | Proposed        | Agreed                          |
|------------------------------------|---------------------------------------------------|-----------------|---------------------------------|
| `Services do not need to change the UI to enable data events.` | ![Checkmark icon](../../icons/checkmark-icon.svg) | SH meeting `17/1/2020` | SH meeting `24/1/2020` |
{: caption="Table 5. Change control for implementation changes" caption-side="top"}
