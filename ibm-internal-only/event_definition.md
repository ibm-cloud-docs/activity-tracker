---

copyright:
  years: 2019
lastupdated: "2019-03-06"

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


# Event fields
{: #ibm_event_fields}


{:shortdesc}


## Introduction
{: #intro}

This page defines all of the fields used by an Activity Tracker event. Events in Activity Tracker are expressed in JSON.

The schema of an Activity Tracker event is based on [the CADF standard](http://www.dmtf.org/sites/default/files/standards/documents/DSP0262_1.0.0.pdf) (Cloud Auditing Data Federation). This is an open model for events that is suitable for auditing.

The CADF event model requires 5 components. For Activity Tracker, these translate into:

1. observer: always Activity Tracker
2. initiator: an end user, or an internal (IBM) or external service
3. action: the activity that the initiator is performing, such as calling a REST API
4. target: the IBM service that the action is performed against
5. outcome: the result of the action; "success" or "failure"

Following is a sample event, to use as an example. Each of the fields is explained in the rest of this page.

```js
{
    // REQUIRED FIELDS:

    "initiator": {
        "id": "IBMid-120000QUJ0",
        "name": "rbertram@us.ibm.com",
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
        "reasonCode": 200
        // reasonType is optional here
    },
    "severity": "warning",
    "eventTime": "2019-11-03T21:40:53.94+0000",

    // Three required fields are not part of CADF spec:
    "message": "IAM Access Groups: add member Test Group",
    "logSourceCRN": "crn:v1:bluemix:public:iam-groups:global:a/7131c65c6ad70bdc209bb564997a5f1c:::",
    "saveServiceCopy": true,

    // REMAINING FIELDS ARE OPTIONAL

    "id": "916faca9-4644-41ce-9e7c-b40a04738a16",
    "observer": {
        "name": "Activity Tacker",
        "id": "ActivityTracker"
    },

    // The rest of the optional fields are not part of CADF spec:
    "requestData": {
        // This object is defined by the service
        "iam_id": "IBMid-550000HRWG",
        "type": "user"
    },
    "responseData": {
        // This object is defined by the service
        "iam_id": "IBMid-550000HRWG",
        "type": "user",
        "created_at": "2019-11-03T21:40:53Z",
        "created_by_id": "IBMid-120000QUJ0",
        "status_code": 200
    },
    "dataEvent": false

}
```

## Required event fields provided by the service to comply with CADF
{: #mandatory}

The following table list the mandatory fields:

<table>
  <caption>Mandatory fields</caption>
  <tr>
    <th>Field Name</th>
	  <th>Description</th>
	  <th>Value</th>
  </tr>
  <tr>
    <td>initiator.id</td>
	  <td>ID of the initiator of the action. </br>There are different types of initiators: IBMID, serviceID. </br>The initiator is a user with an IBMID or a service ID in the customer account. Set this value to the **access_token.iam_id** field. </br>The initiator of an action in the customer account is an IBM service ID. This action is run on behalf of the customer as a result a customer's request. Set the initiator.id to the **access_token.iam_id** field. </br>**Note: It is strongly recommended to also set the <i>initiator.name</i> field.**</td>
	  <td>Example of an IBMID:  <b>IBMid-060000JGT2</b> </br>Example of a service ID: <b>iam-ServiceId-769b5c65-0165-4c89-847d-9660b1632e14</b> </br>Example of a certificate: <b>CertificateId-769b5c65-0165-4c89-847d-9660b1632e14</b></td>
  </tr>
  <tr>
    <td>initiator.name</td>
	  <td>Username of the user that initiated the action.  </br>The initiator is a user with an IBMID or a service ID in the customer account. Set this value to the <b>access_token.sub</b> field. </br>The initiator of an action in the customer account is an IBM service ID. This action is run on behalf of the customer as a result a customer's request. Set the initiator.id to the `Catalog name of the service` who owns the service ID that is used. </td>
	  <td>For example: for IBMID, set the value to <i>lopezdsr@uk.ibm.com</i> </br>For a service ID initiator.id, set the value to <i>ServiceId-769b5c65-0165-4c89-847d-9660b1632e14</i>.</td>
  </tr>
  <tr>
    <td>initiator.typeURI</td>
	  <td>The type of the source of the event. </br>Set to <b>service/security/clientid</b> to indicate that the initiator is an registered IAM UI or service </br>For example, when Cloud Console logs in users with IAM, they need a client id / secret. In this case, the Token Service will set this value for the initiator.typeURI field in the AT event.</br>Set to <b>service/security/account/user</b> to indicate that the initiator is a user </br>For example, a user with an IBMid runs an action to create a certificate. </br>Set to <b>service/security/account/serviceid</b> to indicate that the initiator is a serviceID (a service or an app) </br>For example, an app or a service call an API to trigger an action on a cloud resource. </br>Set to <b>service/security/client/certificateid</b> to indicate that the initiator runs an action by using a certificate.</td>
	  <td><b>service/security/clientid</b> </br><b>service/security/account/user</b> </br><b>service/security/account/serviceid</b></td>
  </tr>
  <tr>
    <td>initiator.credential.type</td>
	  <td>Set to type of initiator ID credential. </td>
	  <td>token, user, apikey, certificate</td>
  </tr>
  <tr>
    <td>initiator.host.address</td>
	  <td>This field provides information about the address where the request came from. </br>Set this field to the originating IP address. </br>For Kubernetes: By default, the source IP address of the client request is not preserved.  When a client request to your app is sent to your cluster, the request is routed to a pod for the load balancer service that exposes the ALB. </br>If no app pod exists on the same worker node as the load balancer service pod, the load balancer forwards the request to an app pod on a different worker node. The source IP address of the package is changed to the public IP address of the worker node where the app pod is running. </br>This setting can be automated in various ways.  It is the services' responsibility how they want to automate it. The way depends on how you deploy your environment. E.g. yaml, helm chart, terraform, etc </br>For a Helm Chart, you can add the following line: `kubectl get svc -n kube-system | awk '/^public.*alb/{print $1}' | while read alb; do kubectl patch svc $alb -n kube-system -p '{"spec":{"externalTrafficPolicy":"Local"}}'; done`</td>
	  <td>For example: 154.197.90.34</td>
  </tr>
  <tr>
    <td>target.id</td>
	  <td>Set this value to the CRN of the cloud resource on which the action is executed. A cloud resource can be a service, a service instance, or a service sub-resource (such as a user API key, a certificate, etc). </br>Guidance: Set this value to the resource CRN when the action is executed on a specific resource. If the action is executed on a service, set the field to the service's crn value.</td>
	  <td>For example, if the action requested is on a certificate, set the value to the CRN of the certificate. </br>If the action affects a service instance, like provision a service, set the value to the CRN of the instance. </br>CRN that identifies a whole service instance should use the format: <b>crn:v1:{cname}:{ctype}:{service-name}:{location}:a/{IBM-account}:{service-instance}::</b> </br></br>CRN that identifies a specific resource belonging to a service instance should use the format: <b>crn:v1:{cname}:{ctype}:{service-name}:{location}:a/{IBM-account}:{service-instance}:{resource-type}:{resource}</b> </br></br>For instance, when you deploy a cluster, the target would be <i>crn:v1:bluemix:public:containers-kubernetes:dal09:a/4324327284:6e4c93cdf28e47f6abecb7e97e65056d::</i> but when you add a worker to that cluster, the target value would be <i>crn:v1:bluemix:public:containers-kubernetes:dal09:a/4324327284:6e4c93cdf28e47f6abecb7e97e65056d:worker:myworkerhostname</i>
    </td>
  </tr>
  <tr>
    <td>target.name</td>
	  <td>Set this value to the name of the cloud resource on which the action is executed. </br>The value is a human readable name of the service, service instance or service sub-resource that matches the CRN specified on the field <i>target.id</i> </td>
	  <td>For example, if the action requested is on a certificate, set the value to the name of the certificate that a user coould see in the Cloud UI. </br>If the action affects a service instance, like provision a service, set the value to the name of the service instance as listed under the field Name on the Cloud dashboard. </br>For services that are registered into the IBM Cloud Catalog, the service name MUST correspond to one of the services registered to the Cloud Platform Global Catalog service. It is the "name" property returned by the Cloud Platform Global Catalog service API GET https://resource-catalog.bluemix.net/api/v1/{id} for the corresponding resource instance. 
  </tr>
  <tr>
    <td>target.typeURI</td>
	  <td>The type of the target of the event. </br></br>This field does not include action information. </br></br> This field starts with the serviceName. The serviceName is the name of the service as indicated in the crn. </br>Use forward slash <b>/</b> to separate complex objectTypes to make it more readable to the users.
</td>
	  <td>For example: </br>iam/audit/apikey/userapikey  </br>ibm-key-protect/secret  </br>cloud-object-storage/bucket/cors</td>
  </tr>
  <tr>
    <td>action</td>
	  <td>This field indicates the action that triggers an event. The format of this field is <b>serviceName.objectType.action</b> where servicename is the name of the service as indicated in the crn. </br></br>The most common values are: <i>create</i>, <i>update</i>, <i>delete</i>. <br></br>Use a dot <b>.</b> to separate the 3 parts that define the action field (serviceName, objectType, action). </br></br>Use a dash <b>–</b> to separate complex objectTypes to make it more readable to the users. </br></br>Valid action values are: create, read, update, delete, backup, capture, configure, deploy, disable, enable, monitor, restore, start, stop, undeploy, receive, send, authenticate, renew, revoke, allow, deny, evaluate, notify, unknown </br></br>More values will be added as needed. </td>
    <td>For example: </br>containers-kubernetes.worker.create  </br>iam-identity.user-apikey.create  </br>cloud-object-storage.bucket-acl.create   </br>cloud-object-storage.bucket.update   </td>
  </tr>
  <tr>
    <td>outcome</td>
	  <td>This field indicates the result of the action. </br></br>Valid values are: <b>success</b>, <b>pending</b>, <b>failure</b>, <b>unknown</b></td>
	  <td><b>success</b> </br><b>pending</b> </br><b>failure</b> </br><b>unknown</b></td>
  </tr>
  <tr>
    <td>reason.reasonCode</td>
	  <td>This is a numeric field (the others are strings). <br>Use the values that are defined in https://www.iana.org/assignments/http-status-codes/http-status-codes.xml </br>If your actions are not REST API calls, set to 200 for success outcome and 500 for failure. Add in responseData information about the failure cause.</td>
	  <td>For example: 200</td>
  </tr>
  <tr>
    <td>severity</td>
	  <td>This field defines the level of threat an action may have on the Cloud. </br></br>Valid values are: </br><b>normal</b>: Use this value for routine actions in the Cloud. For example: starting an instance,  refreshing a token, etc  </br><b>warning</b>: Use this value when a Cloud resource is updated or its metadata is modified. For example: updating the version of a worker node, renaming a certificate, renaming a service instance, etc  </br><b>critical</b>: Use this value when the action affects security in the Cloud like changing credentials of a user, deleting data, unauthorized access to work with a Cloud resource.  For example: adding or removing proviledges to a user, deleting a security key, deleting logs, running an action against a resource where the user does not have permissions to work with, etc.</td>
	  <td><b>normal</b> </br><b>warning</b> </br><b>critical</b> </td>
  </tr>
  <tr>
    <td>eventTime</td>
	  <td>Indicates the timestamp when the event was created. </br>The date is represented as Universal Time Coordinated (UTC). </br></br>ISO 8601 date and time must be followed by Z or +0000 to indicate that a time is defined as Universal Time (UTC). For AT, use +0000   </br></br>The letter 'T' in the date/time syntax must always be upper case.  </br></br>For readability and consistency in the UI, the format of this field is: <b>YYYY-MM-DDTHH:mm:ss.SS+0000</b></td>
	  <td>For example: 2017-10-19T19:07:50.32+0000</td>
  </tr>
</table>

## Optional event fields provided by the service to comply with CADF
{: #optional}

**Optional fields:**

<table>
  <caption>Optional fields</caption>
  <tr>
    <th width="20%">Field Name</th>
	  <th width="30%">Description</th>
	  <th width="30%">Value</th>
  </tr>
  <tr>
    <td>id</td>
	  <td>You can use this field to correlate events.</td>
	  <td></td>
  </tr>
  <tr>
    <td>target.host.address</td>
	  <td>IP Address or URL of the target service. </td>
	  <td></td>
  </tr>
  <tr>
    <td>reason.reasonType</td>
	  <td>Information about the reasonCode when one is provided through the reason.reasonCode field. </br>Use the description associated to the reasonCode (value) defined in https://www.iana.org/assignments/http-status-codes/http-status-codes.xml </td>
	  <td>For example, for a reason.reasonCode = 200, set reasonType to <b>OK</b></td>
  </tr>
  <tr>
    <td>requestData<br>responseData</td>
	  <td>These two fields are not part of CADF, but are provided for services to use for custom JSON. </br>Add any information here that will enhance the user experience going through ther audit trail of your service events.  </br>Add value pairs of information. Although this is a string field, add the information as JSON. </br>Some fields: </br>{"ResourceGroupID":"CRN of the resource group"} </br>{"ReasonForFailure":"Additional information about why the request failed"} </td>
	  <td>Notice that for update events (this field is required), you should add details of original version and final version of the change.</td>
  </tr>
  <tr>
    <td>tags</td>
	  <td>These field is an array of strings.</td>
	  <td></td>
  </tr>
  <tr>
	<td>dataEvent</td>
	<td>True if this event is a "data event" rather than a "management event". See [here](/docs/services/Activity-Tracker-with-LogDNA/ibm-internal-only?topic=logdnaat-ibm_faq#types-of-events) for an explanation. The default is `false`, so that an event is a management event unless it has `dataEvent:true`. <br/><br/>This field is not part of CADF. This field can only be provided to Activity Tracker with LogDNA; legacy AT will not parse it.</td>
	<td>`true`<br/>`false` (default)</td>
  </tr>
</table>



## Event fields for new architecture 
{: #new}

Activity Tracker with LogDNA relies on three new fields: `logSourceCRN`, `saveServiceCopy`, and `message`.

<table>
  <caption>Required fields for new architecture</caption>
  <tr>
    <th width="20%">Field Name</th>
	  <th width="30%">Description</th>
	  <th width="30%">Value</th>
  </tr>
  <tr>
    <td>logSourceCRN</td>
	  <td>Set to the CRN of the service instance that generates the event. (CRN of the service instance in the customer's account.)  </br></br>This field determines where a copy of the event is saved for the user. </br></br>If you leave out logSourceCRN, it only saves the event to your account, not to the user's account. </br></br>If you leave out logSourceCRN AND set saveServiceCopy:false, then the event is not saved at all.</td>
	  <td>For example: crn:v1:bluemix:public:kms:eu-	gb:a/8131c65c6ad70bdc209bb564997a5f1c	:8424aaea-ddcf-4dfe-ae90-
	1a4b89e07b86::</td>
  </tr>
  <tr>
    <td>saveServiceCopy</td>
	  <td>This field is used to control whether the IBM service gets a copy of the event or not. </br></br>Defaults to <b>true</b>. </br></br>If set to <b>true</b>,  the event is saved to the service's account.  </br></br>If set to <b>false</b>, then event is not saved to the service's account.</td>
	  <td><b>true</b> </br><b>false</b></td>
  </tr>
  <tr>
    <td>message</td>
	  <td>Message that is associated with the event. </br></br>The format of this field is: <b>serviceName: action objectType target.name [custom data per service][outcome]</b> </br></br>where <b>ServiceName</b> is the UI name of the service as shown in the catalog.  </br></br> <b>action</b> matches the action component as described in the CADF <i>action</i> field of the event. Must be in lowercase. </br></br><b>objectType</b> matches the objectType component as described in the CADF <i>action</i> field of the event. Must be in lowercase. </br></br><b>target.name</b> matches the value of the CADF field <i>target.name</i>. If a name is not available, leave it out. </br></br><b>[custom data per service]</b> has the format: <b>[for resourceType resourceID][custom information]</b> </br>You can add information from data that is available through the AT fields requestData and responseData lowercase. </br>When the action applies to a sub resource component, for example, a policy for a user, or a worker for a cluster, the section [for resourceType resourceID]  should be included. </br>* <b>resourceType</b> defines type of resource, for example, cluster, access group, serviceID, etc. </br>* <b>resourceID</b> specifies the ID of the resource type to which the action applies. </br>The section <b>[custom information]</b> should include any relevant information that you consider important to the user for your event. </br></br><b>[outcome]</b> is set when the <i>outcome</i> field reports an action that is not <i>success</i>. The format is <b>-outcome</b> where outcome matches the outcome value as described in the CADF <i>outcome</i> field of the event. </td>
	  <td>For example: </br>IAM Identity Service: delete user-apikey KeyProtectTest -failure  </br>Key Protect: list secrets </br>IAM Identity Service: login user-apikey containers-kubernetes-key</td>
  </tr>
</table>


## Reserved fields for Activity Tracker
{: #reserved}

<table>
  <caption>Reserved fields (reserved for Activity Tracker)</caption>
  <tr>
    <th width="20%">Field Name</th>
	<th width="30%">Description</th>
	<th width="30%">Value</th>
  </tr>
  <tr>
    <td>eventType</td>
	  <td>This value is set to activity for Activity Tracker. (Other CADF values are "monitor" and "control".</td>
	   <td>activity</td>
  </tr>
  <tr>
    <td>typeURI</td>
  	<td>This value must be set to: `http://schemas.dmtf.org/cloud/audit/1.0/event`</td>
	  <td>http://schemas.dmtf.org/cloud/audit/1.0/event</td>
  </tr>
  <tr>
    <td>type</td>
	  <td>This field must be set to ActivityTracker.</td>
	  <td>ActivityTracker</td>
  </tr>
  <tr>
    <td>observer.name</td>
	  <td>This field must be set to ActivityTracker.</td>
	  <td></td>
  </tr>
  <tr>
    <td>observer.id</td>
	  <td>This field must be set to the CRN of the AT instance that the event is sent to.</td>
	  <td>ActivityTracker</td>
  </tr>
  <tr>
    <td>observer.typeURI</td>
	  <td>This field must be set to security/edge/activity-tracker.</td>
	  <td>security/edge/activity-tracker</td>
  </tr>
</table>


