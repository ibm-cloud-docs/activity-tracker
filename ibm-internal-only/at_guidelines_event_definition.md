---

copyright:
  years: 2019, 2020
lastupdated: "2020-05-11"

keywords: IBM Cloud, LogDNA, Activity Tracker, event definition

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


# Adoption guidelines: AT event fields
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
            "address": "169.62.30.22",
            "addressType": "IPv4"
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
        "reasonType": "OK",
        "reasonForFailure": "xxxxxx"
    },
    "resourceGroupId": "crn:v1:bluemix:public:resource-controller:global:a/7131c65c6ad70bdc209bb564997a5f1c::resource-group:89094792-aa7c-48de-a1a0-7cbac484f072",
    "severity": "warning",
    "eventTime": "2019-11-03T21:40:53.94+0000",

    // The rest of the fields are not part of CADF spec:
    "message": "IAM Access Groups: add member Test Group",
    "logSourceCRN": "crn:v1:bluemix:public:iam-groups:global:a/7131c65c6ad70bdc209bb564997a5f1c:::",
    "saveServiceCopy": true,

    "observer": {
        "name": "ActivityTracker"
    },

    // requestData is required for events that modify resources in the IBM Cloud and to add info that clarifies the action on an audit
    "requestData": {
        // This object is defined by the service
        "updateType": "xxxx",
        "initialValue": "xxxxx",
        "newValue": "xxxxxx",
        "requestId": "xxxxxxxxx-xxxx-xxxx-xxxxxxxxxxx"
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
    "dataEvent": false,

    // id is optional - use it to correlate events within your service
    "id": "916faca9-4644-41ce-9e7c-b40a04738a16",

    // Unique ID that is used to correlate events across multiple services in IBM Cloud
    "correlationId": "xxxxxxxxxxxxxx"

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

To engage the AT team to review your service's AT event prior to One Cloud badging, you must open an issue in the following git repo: [AT repo](https://github.ibm.com/activity-tracker/customer-issues/issues). Select the issue type `AT review`.
{: important}




## Required event fields provided by the service to comply with AT guidelines
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

    Valid actions are: `add`, `bulkdelete`, `create`, `read`, `update`,`delete`, `backup`, `build`, `capture`, `configure`, `deploy`, `disable`, `enable`, `get`, `import`, `inspect`, `list`, `monitor`, `pull`, `push`, `restore`, `start`, `stop`, `undeploy`, `receive`, `reimport`, `remove`, `send`, `set`, `set-on`, `set-off`, `authenticate`, `read`, `renew`, `revoke`, `allow`, `deny`, `evaluate`, `notify`, `rotate`, `ack-delete`, `ack-restore`, `ack-disable`, `ack-enable`, `ack-rotate`, `edit`, `publish`, `authorize`
, `publish`    Not valid actions are: `info`, `unknown`

    More values will be added as needed.

**Use a dot `.` to separate the 3 parts that define the action field (serviceName, objectType, action).**
{: important}

**Use a dash `–` to separate complex objectTypes to make it more readable to the users.**
{: important}

**Use the action type `create` when you create a new resource in your service instance. Use the action type `add` when you add an existing resource to your service instance.**
{: important}

**Use the action type `read` for events that report a viewing request on 1 resource (Get).** 
{: important}

**Use the action type `list` for events that report a user's request to view all resources for a type of a resource in your service.**
{: important}


### compliance (JSON)
{: #compliance}

Add this JSON object to the Activity Tracker event **if your service is integrated with the IBM Cloud Configuration Governance service.** The IBM Cloud Configuration Governance enables you to define, manage, enforce, and monitor the configuration rules of your IBM Cloud resources.
{: note}

The following data must be defined for each event:

| Field                               | Type             | Description |
|-------------------------------------|------------------|-------------|
| `isComplaint`                       | `boolean`        | Defines the status of the action and flags out governance issues. </br>Set to `true` when the action is compliant with governance policies.  </br>Valid values are: `true`, `false`  |
| `complianceTraceId`                 | `string`         | Defines the unique ID that a user can use to get details of the governance policy, and the rules that are included in that policy and apply to the action. |
| `disallow`                          | `boolean`        | Defines whether the action is permitted or not. </br>When this field is set to `true`, the action must be rejected with a RC = 403. </br>Valid values are: `true`, `false`   |
| `notify`                            | `boolean`        | Defines whether a notification is requested.   </br>Valid values are: `true`, `false` |
| `channel`                           | `string`         | Defines the notification channels that a user has configured.    |
{: caption="Table 1. Compliance fields" caption-side="top"}


There are different scenarios that you should consider:

| Scenario      | `isCompliant` | `enforcementAction - disallow` | AT  field: resource.resourceCode | AT field: severity |
|---------------|---------------|--------------------------------|----------------------------------|--------------------|
| Compliant and allowed | `true`    | `true`    | Set per the AT guidance | Set per the AT guidance |
| Not compliant but action allowed | `false`       | `true`     | Set per the AT guidance | Set per the AT guidance |
| Not compliant and action not allowed | `false`       | `false`     | `RC = 403`    | `critical` |
{: caption="Table 1b. Compliance fields by scenario" caption-side="top"}


**Service Provider**: To obtain the information that you can use to set these fields, you must query the IBM Cloud Configuration Governance service. For more information, see [Config-Management APIs](https://pages.github.ibm.com/project-fortress/gov-config-apidoc/#/).

**Customers**: Users can use the `complianceTraceId` to get a static report, which is appropriate for audits and forensic analysis.

The JSON structure for this field should map the following one:

```
"compliance": {
    "isCompliant": false,
    "complianceTraceId": "801d5387-45f7-457e-920a-6d1696d2bf0b",
    "enforcementActions": {
      "disallow": true,
      "notify": true
    },
    "notificationDetails": {
      "channel": ""
  }
```
{: codeblock}



### correlationId (string)
{: #correlationId}

Use this field to specify the unique GUID that a user can use to correlate events across multiple services in IBM Cloud.
{: note}

For example, there are specific use cases where the field must be set:
* [Integration with Key Protect (KP)](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-at_use_cases#kp-hyperwarp)


### dataEvent (boolean)
{: #dataEvent}

This field specifies the type of event, whether it is a management event or a data event.
{: note}

* For a `management event`, set this field to **false**.
* For a `data event`, set this field to **true**.

[Learn more](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-ibm_faq#types-of-events).




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
* For actions (events) that are published to Hyperwarp by an IBM Cloud service, and subscribed by an IBM Cloud service, set this value as follows:

    Publisher service: Set this field to the IBMid or service ID that requests the action: **access_token.iam_id**. 

    Subscriber service:  Set this field with the service ID value in the `publisher` field

* For actions between services, set this field to the **crnToken.iam_id** field value that is available in the CRN token.


| Who is the initiator                       | Value                                                                   | Example          |
|--------------------------------------------|-------------------------------------------------------------------------|------------------|
| `Certificate`                              | `access_token.iam_id`                                                   | `CertificateId-769b5c65-0165-4c89-847d-9660b1632e14` |
| `User in the user's account with an IBMID where the action is requested` | `access_token.iam_id`                     | `IBMid-xxxxxxxx` | 
| `ServiceID in the user's account where the action is requested`          | `access_token.iam_id`                     | `iam-ServiceId-769b5c65-0165-4c89-847d-9660b1632e14` |
| `ServiceID not defined in the customer account and owned by a service`   | `access_token.iam_id`                     | `iam-ServiceId-769b5c65-0165-4c89-847d-9660b1632e14` |
| `Action triggered via Hyperwarp`           | Publisher service: `access_token.iam_id`  </br>Subscriber service: `publisher`  | `iam-ServiceId-769b5c65-0165-4c89-847d-9660b1632e14` |
| `Watson service - initiator is a user`     | `bluemix-subject`                                                       | `IBMid-xxxxxxxx` |
| `Watson service - initiator is a service ID` | `bluemix-subject`                                                     | `iam-ServiceId-769b5c65-0165-4c89-847d-9660b1632e14` |
| `No initiator - Action triggered by own service` `(1)`  | Leave empty                                                    | `` | 
| `IBM Cloud service service to service request`      | `crnToken.iam_id`            | `crn-crn:v1:bluemix:public:cloud-object-storage:global:a/xxxxxxxx:69002255-e226-424e-b6c7-23c887fdb8bf::` |
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

* For actions between services, set this field to **IBM**. 

| Who is the initiator                                                                 | Value                                   | Example          |
|--------------------------------------------------------------------------------------|-----------------------------------------|------------------|
| `User is a member in the customer account where the action is requested`             | `access_token.sub`                      | `joe@ibm.com`    | 
| `ServiceID in the user's account where the action is requested`                      | `access_token.sub`                      | `ServiceId-769b5c65-0165-4c89-847d-9660b1632e14` |
| `ServiceID not defined in the customer account and owned by a service`               | Set this field to the value in the  **Display Name** column in the [global catalog](https://globalcatalog.cloud.ibm.com/search?q=) for your service. In the catalog, some services include IBM Cloud nad others do not. To make sure it is clear that it is an IBM owned ID, add `IBM Cloud` to the name if your full legal name includes it.  If not sure, contact the AT team in slack. | `IBM Cloud Certificate Manager` |
| `Certificate`                                                                        | `access_token.sub`                      | `CertificateId-769b5c65-0165-4c89-847d-9660b1632e14` |
| `Action triggered via Hyperwarp`                                                     | `event_properties.publisher_name`       | `iam-ServiceId-769b5c65-0165-4c89-847d-9660b1632e14` |
| `Watson service - initiator is a user`                                               | `bluemix-iamid`                         | `IBMid-xxxxxxxx` |
| `Watson service - initiator is a service ID`                                         | `bluemix-iamid`                         | `iam-ServiceId-769b5c65-0165-4c89-847d-9660b1632e14` |
| `No initiator - Action triggered by own service` `(1)`                               | `IBM`                                   | `IBM`            |
| `IBM Cloud service (service to service request)`                                     |  `crnToken.sub` | `crn-crn:v1:bluemix:public:cloud-object-storage:global:a/xxxxxxxx:69002255-e226-424e-b6c7-23c887fdb8bf::` |
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
| `Registered IAM UI or service to service request` `(2)`                              | `service/security/clientid`             |
{: caption="Table 4. Guidance setting initiator.tyepURI" caption-side="top"}

`(1)` The action does not have an initiator because the event that is generated reports an action on a customer resource and this action is executed by the service as a scheduled job.

`(2)` For example, when Cloud Console logs in users with IAM, they need a client id / secret. In this case, the Token Service will set this value for the initiator.typeURI field in the AT event.
    


### initiator.credential.type (string)
{: #initiator.credential.type}

This field defines the type of credential that is used by the initiator to run the action.
{: note}

Valid values are: `token`, `user`, `apikey`, `certificate`, `public-access`

Guidance setting the value of this field:

| Value of `access_token.grant_type` in IAM token                 | Value of `initiator.credential.type` in AT event |
|-----------------------------------------------------------------|--------------------------------------------------|
| `urn:ibm:params:oauth:grant-type:apikey`                        | `apikey`                                         |
| `urn:ibm:params:oauth:grant-type:delegated-refresh-token`       | `token`                                          |
| `urn:ibm:params:oauth:grant-type:passcode`                      | `user`                                           |
| `authorization_code`                                            | `user`                                           |
| `password`                                                      | `user`                                           |
{: caption="Table 5. Guidance setting credential type" caption-side="top"}


### initiator.host.addressType (string)
{: #initiator.host.addresstype}

This field provides information about the type of IP address where the request came from. 
{: note}

Valid values are `IPv4` and `IPv6`.

The default value is `IPv4`


### initiator.host.address (string)
{: #initiator.host.address}

This field provides information about the IP address where the request came from. 
{: note}

Set this field to the originating IP address. 

The format for IPv4 addresses is:

```
xxx.xxx.xxx.xxx
```
{: codeblock}

The format for IPv6 addresses is: (The format is still under review)

```
2001:db8:: 2001:db8:ffff:ffff:ffff:ffff:ffff:ffff
```
{: codeblock}

**For services that run on Kubernetes:**

For services running on Kubernetes on VPC (available 2Q 2020) source IP preservation will not work until 2H 2020. 
{: note}

Services running Kubernetes on classic should update to [v2 loadbalancer](https://cloud.ibm.com/docs/containers?topic=containers-loadbalancer-v2) when enabling source IP preservation.  v1 of load balancer may cause outages with IP preservation enabled during rolling updates to the load balancer and should NOT be used without careful consideration.  While the v2 load balancer is publicly listed as beta it is approved for production use and is only beta due to a manual SL step that is required.  See [docs](https://cloud.ibm.com/docs/containers?topic=containers-loadbalancer-about) for differences between v1 and v2.
{: important}

To be able to get the originating IP address, complete the following steps to enable IP preservation to all enabled public or private ALBs:
1. Enable source IP preservation. [Learn more](/docs/containers?topic=containers-ingress-settings#preserve_source_ip).
2. Obtain the IP from the `x-forwarded-for` property in the header. 

Refer to [docs](https://cloud.ibm.com/docs/containers?topic=containers-loadbalancer-v2) for details on the following steps: 
1. Check which version of load balancers are in use 
2. Create an upgrade and test schedule for migration from v1 to v2 load balancers 
3. Upgrade to v2 loadbalancers 
4. Scale out v2 loadbalancers for high availability across zones 
5. Obtain the IP from the `x-forwarded-for` property in the header


`Services running Kubernetes on classic should update to v2 loadbalancer when enabling source IP preservation.`
{: important}

V1 of the load balancer may cause outages with IP preservation enabled during rolling updates to the load balancer and should **NOT** be used without careful consideration.
While the v2 load balancer is publicly listed as beta it is approved for production use and is only beta due to a manual SL step that is required. 
Services in classic infrastructure can swap to v2.  There is a script you can use that will delete your v1 LBs and replace them with v2. There will be a few seconds downtime if you do that. 

If you are running your cluster in an MZR (multiple zones), the LB won't work across zones unless you create a customer ticket to allow capacity aggregation. [Learn more](/docs/containers?topic=containers-loadbalancer-v2#ipvs_provision).

For questions implementing the solution, ask in the slack channel `#armada-users`.


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

**There is a 16k max field limit in LogDNA. Anything bigger than 16k is truncated and lost when the event is consumed by LogDNA.**
{: important}

* Must be formatted as JSON.  Not stringified JSON, as was required by legacy AT
* Must include information that is required to clarify the action. For example, an event with action create might require information on the Software verison. An update event requires information on the initial value and final value. There may be cases where data is sensitive or too long, in this situation, add information about the type of update
* Must be added as value pairs of information.
* Must be formatted in camel case style.

When you add fields, notice that the maximum size of an AT event is 16K.
{: important}

Some fields:
* [Optional] `serviceInstanceId`: Set to the service instance ID (not the CRN value)
* [Optional] `accountID`: Set to the account ID 
* [Optional] `resourceType`: Type of resource
* [Optional] `requestId`: The value of this field includes a UUID that can be used to identify a request in IBM Cloud. Customers should include this value in a support ticket.
* [`Required for update action`] `updateType`: Indicate if it is a name change, description change, or other type Valid values are: `Name changed`, `Description changed`, and others (the services may have their own set of values and might vary per service)
* [`Required for update action`] `initialValue`: Add the original value of the resource that is updated
    
    When the data is PII or sensitive data, consider adding a reference ID so the user can easily identify it. Notice that you should not include in this field data that is sensitive or PII. 

    When the data is a script or file, consider adding the object name and version.

    If you cannot reference by ID, version, or any other way data that is either too big in size or includes sensitive data, do not include this field. Document in your topic the reason why this information is not included so customers are aware as to why is not available.

* [`Required for update action`] `newValue`: Add the new value requested in the action

    When the data is PII or sensitive data, consider adding a reference ID so the user can easily identify it. Notice that you should not include in this field data that is sensitive or PII. 

    When the data is a script or file, consider adding the object name and version.

    If you cannot reference by ID, version, or any other way data that is either too big in size or includes sensitive data, do not include this field. Document in your topic the reason why this information is not included so customers are aware as to why is not available.

* [`Required for Watson services`] `platformSource`: Add the UI catalog name of your service, for example, `Watson Discovery` This helps users identify your events quickly by your service, since the platform_source value is shared across all Watson services.
* [Optional] `customizationId`
* [Optional] `environmentId`



**For update actions where only 1 change** is reported through the event, you can add the fields required as follows:

```
"requestData": {
        // updateType, initialValue, newValue are REQUIRED when the action of the event is UPDATE or the event reports on a change to the object
        "updateType": "xxxx",
        "initialValue": "xxxxx",
        "newValue": "xxxxxx"
    },
```
{: codeblock}

**For update actions where a small number of changes** are reported through the event, you can add the fields as follows:

```
"requestData": {
        // updateType, initialValue, newValue are REQUIRED when the action of the event is UPDATE or the event reports on a change to the object
        "update": [{"updateType": "xxxx",
        "initialValue": "xxxxx",
        "newValue": "xxxxxx"}]
    },
```
{: codeblock}

**For update actions where a large number of changes** are reported through the event, consider the following approach:
1. Create 1 Activity Tracker event (parent event) that reports the main update action and include in requestData information about the number of changes that are affected by that user request. Set the field `totalNumberChanges`. Set also the `id` field. The `id` field is used to correlate this event with the individual events that report detailed information on each change.

    ```
    "id": "xxxxxx",
    "requestData": {
        "totalNumberChanges": xx,
    },
    ```
    {: codeblock}

2. Generate 1 Activity Tracker event per change. Set the `id` field to the value set in the parent event. Add in requestData the required fields for updates:

    ```
    "id": "xxxxx",
    "requestData": {
        // updateType, initialValue, newValue are REQUIRED when the action of the event is UPDATE or the event reports on a change to the object
        "updateType": "xxxx",
        "initialValue": "xxxxx",
        "newValue": "xxxxxx"
    },
    ```
    {: codeblock}




### responseData (JSON)
{: #responseData}
 
Add any information here that will enhance the user experience going through ther audit trail of your service events. 
{: note}

**There is a 16k max field limit in LogDNA. Anything bigger than 16k is truncated and lost when the event is consumed by LogDNA.**
{: important}

* Must be formatted as JSON.  Not stringified JSON, as was required by legacy AT
* Must include information that is required to clarify the action.
* Must be added as value pairs of information.
* Must be formatted in camel case style.

When you add fields, notice that the maximum size of an AT event is 16K.
{: important}

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

### reason.reasonForFailure (string)
{: #reason.reasonForFailure}

This field provides additional information as to why the action has failed.
{: note}

### resourceGroupId (string)
{: #resourceGroupId}

Set to the resource group CRN. 
{: note}

For example, 

```
crn:v1:bluemix:public:resource-controller:global:a/59bcbfa6ea2f006b4ed7094c1a08dcdd:resource-group:59bcbfa6ea2f006b4ed7094c1a08dcdd
```
{: screen}

See [Resource Group API](https://cloud.ibm.com/apidocs/resource-controller/resource-manager#get-a-resource-group).  

### saveServiceCopy (boolean)
{: #saveServiceCopy}

This field is used to control whether the IBM service gets a copy of the event or not.
{: note} 

The default value is *true* but the field must be set explicitly. 

* To save a copy of the event in your ATS ( in your service's account), set this field to **true**.
* If you do not want a copy of the events saved in your ATS, set this field to **false**. 



### severity (string)
{: #severity}

This field defines the **level of threat** an action may have on the Cloud. This field allows a user to filter events by severity so that they can monitor the serious things that are happening in their account, and hide what is more likely to be background noise.
{: note}

Valid values are: `normal`, `warning`, and `critical`

The value of the severity field is intended to be the same, regardless of the outcome (success or failure). The severity field indicates the inherent `threat level` of the action, that is, how much damage it could do if the request completes successfully as a mistake or a malicious action. The word `severity` is often associated with an error, but CADF slant is slightly different. 


* Set to **normal** for routine actions in the Cloud. 

    For example: starting an instance,  refreshing a token, etc  

* Set to **warning**  when an action fails, or when a Cloud resource is updated or its metadata is modified. 

    For example: updating the version of a worker node, renaming a certificate, renaming a service instance, etc  

* Set to **critical** when the action affects security in the Cloud like changing credentials of a user, deleting data, unauthorized access to work with a Cloud resource.  

    For example: adding or removing proviledges to a user, deleting a security key, deleting logs, running an action against a resource where the user does not have permissions to work with, etc.

For example, if the action is:
* `read`: Set this value to `normal`
* `list`: Set this value to `normal`
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

* If the action requested is on a user, set this field to the user IBMid value. Notice that users do not belong exclusively to an account and cannot be defined by using a crn.

* **Exception:** Users are not unique to an account. They cannot be defined with a CRN. IAM and BSS actions where the target is a user that is a member of an account, the target.id does not have a crn formatted value.
{: note}

#### Information on how to set the target.id for services that on-boarded with the resource-controller
{: #logSourceCRN-1}

When an instance is provisioned by a user, the request calls the service’s broker via [IBM Cloud Open Service Broker API ![External link icon](../icons/launch-glyph.svg "External link icon")](https://test.cloud.ibm.com/apidocs/resource-controller/ibm-cloud-osb-api#create-provision-a-service-instance){: new_window}. The response includes the instance’s CRN.

When a user makes a call to one of your service's API endpoints, the user must pass the CRN as part of the call (can be a header, request Path, depends on your API), which you can then use to populate `target.id` and `logSourceCRN`.


### target.name (string)
{: #target.name}

Set this value to the human readable name of the cloud resource on which the action is executed.
{: note}

The value is a human readable name of the service, service instance or service sub-resource that matches the CRN specified on the field target.id 	
 
* When the action requested is on the instance of your service ( for example, a user requests to rename an instance), the name of the service should match the name as indicated under the `Name` column in the resource list. 

    If you cannot provide the name of the instance because getting that information can impact performance and a re-architecture of your service, leave this field empty.

* If the action requested is on a certificate, set the value to the name of the certificate that a user could see in the Cloud UI.

* If you have resources that do not have a name, you can set this value to  `<resource-type>-<ID of the resource modified>`, for example, `model-xxxxx` or leave empty.

* When the action is **list**, and the target is the account or an instance, set `target.name` to the name of the account or the service instance if you have it. If you cannot get it, leave it empty.




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

Use this field to correlate AT events within your service.
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
* The `dataEvent` flag is supported. `true` indicates a data event. `dataEvent` defaults to `false`, but events should specify `false` explicitly. Refer [here](https://test.cloud.ibm.com/docs/Activity-Tracker-with-LogDNA/ibm-internal-only?topic=Activity-Tracker-with-LogDNA-ibm_event_fields#optional) for more info.
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
| `correlationId`                    |                                                   |                 | March 2020 - added this new field to guidelines  (use this field to correlate across multiple services in the IBM Cloud - [Required for integration use cases](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-at_use_cases)  | 
| `compliance`                       | ![Checkmark icon](../../icons/checkmark-icon.svg) | July 2020       | Required only for services that integrate with the Governance service | 
| `dataEvent`                        | ![Checkmark icon](../../icons/checkmark-icon.svg) |  December 2019  | December 2019 - added this new field to guidelines    |
| `eventTime`                        | ![Checkmark icon](../../icons/checkmark-icon.svg) |  January 2019   |                                 | 
| `id`                               |                                                   |                 |                                 | 
| `logSourceCRN` `[*]`               | ![Checkmark icon](../../icons/checkmark-icon.svg) |  June 2019      | June 2019 - when changes to migrate to LogDNA were requested                                 |
| `message` `[*]`                    | ![Checkmark icon](../../icons/checkmark-icon.svg) |  June 2019      |                                 |
| `initiator.id`                     | ![Checkmark icon](../../icons/checkmark-icon.svg) |  January 2019   |                                 |
| `initiator.name`                   | ![Checkmark icon](../../icons/checkmark-icon.svg) |  January 2019   |                                 | 
| `initiator.typeURI`                | ![Checkmark icon](../../icons/checkmark-icon.svg) |  January 2019   |                                 |
| `initiator.credential.type`        | ![Checkmark icon](../../icons/checkmark-icon.svg) |  January 2019   |                                 |
| `initiator.host.address`           | ![Checkmark icon](../../icons/checkmark-icon.svg) |  January 2019   |                                 |
| `initiator.host.addressType`       | ![Checkmark icon](../../icons/checkmark-icon.svg) |  June 2020      |  Includedd to support IPv6 addresses |
| `observer.name`                    | ![Checkmark icon](../../icons/checkmark-icon.svg) |  December 2019  |                                 |
| `outcome`                          | ![Checkmark icon](../../icons/checkmark-icon.svg) |  January 2019   |                                 |
| `reason.reasonCode`                | ![Checkmark icon](../../icons/checkmark-icon.svg) |  January 2019   |  December 2019 - check 403 is being generated to report on unauthorized access to run an action |
| `reason.reasonType`                | ![Checkmark icon](../../icons/checkmark-icon.svg) |  December 2019  |  December 2019 - check that it is populated for failure events </br>January 2020 - required for all outcomes |
| `reason.reasonForFailure`           | ![Checkmark icon](../../icons/checkmark-icon.svg) |  September 2020     |  This field was initially part of requestData and location inherited from legacy. For consistency, has been moved to this new section of CADF.</br>January 2021 - required for all outcomes |
| `resourceGroupId`                  | ![Checkmark icon](../../icons/checkmark-icon.svg)  | September 2020 | This fie;d is included to support the AIM enhancements and integartion of AT with the CLoud platform. |
| `requestData`  `[*]`               | ![Checkmark icon](../../icons/checkmark-icon.svg) |  January 2019   |  December 2019 - update events must include information about the update (3 new subfields added to add consistency in the user experience) and should be JSON formatted </br>May 2020:  2 fields (resourceGroupId and reasonForFailure) have changed from optional to required |
| `responseData` `[*]`               |                                                   |  January 2019   |  December 2019 - Check that is JSON formatted |
| `saveServiceCopy`  `[*]`           | ![Checkmark icon](../../icons/checkmark-icon.svg) |  June 2019      |  June 2019 - when changes to migrate to LogDNA were requested |
| `severity`                         | ![Checkmark icon](../../icons/checkmark-icon.svg) |  January 2019   |                                 |
| `target.id`                        | ![Checkmark icon](../../icons/checkmark-icon.svg) |  January 2019   |                                 |
| `target.name`                      | ![Checkmark icon](../../icons/checkmark-icon.svg) |  January 2019   |                                 |
| `target.typeURI`                   | ![Checkmark icon](../../icons/checkmark-icon.svg) |  January 2019   |                                 |
| `target.host.address`              |                                                   |                 |                                 | 
| `tags`                             |                                                   |                 |                                 | 
{: caption="Table 4. Change control for list of event fields in an AT event" caption-side="top"}

`[*]` These fields are extensions of the CADF specification.

**Changes to guidelines** - Implementation change control:

| Detail                             | Required                                          | Date             |
|------------------------------------|---------------------------------------------------|-----------------|
| `Services do not need to change the UI to enable data events.` | ![Checkmark icon](../../icons/checkmark-icon.svg) | SH meeting `24/1/2020` |
| `reasonForFailure` and `resourceGroupId` are changed from optional to required.        | ![Checkmark icon](../../icons/checkmark-icon.svg) | SH meeting `14/5/2020` |
{: caption="Table 5. Change control for implementation changes" caption-side="top"}

A service has 3 months, from the date listed on the table, to implement changes and be compliant with AT guidelines.
{: important}


