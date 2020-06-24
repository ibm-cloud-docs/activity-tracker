---

copyright:
  years: 2019, 2020
lastupdated: "2020-06-24"

keywords: IBM Cloud, LogDNA, Activity Tracker, new use cases

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


# New WIP Adoption guidelines
{: #at_new}

This page shows use cases where services need to be aligned when sending events to AT that are being worked on:
{:shortdesc}


## initiator.host.address (review guidelines)
{: #at_new_1}

* Provides information about the address where the request came from. 
* Formatted as IPv4

Currently, most services suppport IPv4, but IPv6 is also supported by some services.

CIS supports IPv4 and IPv6. Most services have IPv6 turned off, but when the proxy-mode in CIS  is enabled, IPv6 addresses are accepted. (This can be turned off via CLI).



Proposal: (Complete within the next 6 months)

initiator.host.address = IPv4 or IPv6 formatted IP address
initiator.host.addressType = IPv4 / IPv6   The default value is `IPv4`. However, services should start adding this field. 


## reasonForFailure
{: #at_new_2}

Currently, and to add consistency with services that adopted this value early, `reasonForFailure` is located in requestData. 

Proposal: (Complete within the next 6 months)
The proposal is to move `requestData.reasonForFailure` to `reason.reasonForFailure`. 

As services transition, 30 days notice needs to be given to users per the notification guidelines so customers can fix their queries and resources.


## resourceGroupId
{: #at_new_3}

Currently, `resourceGroupId` is located in requestData and set to the CRN value.

Proposal: (Complete within the next 6 months)
The proposal is to move `requestData.resourceGroupId` to a top level field: `resourceGroupId`. 

Services who have not yet implemented `resourceGroupId`, should make it a top level field. 

Services who already implement it: As services transition, 30 days notice needs to be given to users per the notification guidelines so customers can fix their queries and resources.



## Provider that is authorized by a service requests an action on the customer's account
{: #at_new_4}

There are services like DirectLink and Transit Gateway that allow customers to run actions in their account directly by using the service API/UI, and by using the provider's API.

![Pattern 2](images/pattern2.png "Pattern 2")

* Providers are registered with the IBM Cloud service.
* Providers use a service ID that is also registered with the IBM Cloud service. 
* When a provoder makes the request, the customer needs to accept the request.


### Customer creates a gateway directly

The following actions would be expected:

1. `dl.provider-gateway.request`
2. `dl.gateway.create`
3. `dl.gateway-create-request.approve` or `dl.gateway-create-request.reject`



| Field                       | `dl.provider-gateway.request` | `dl.gateway.create` |`dl.gateway-create-request.approve` | `dl.gateway-create-request.reject` |
|-----------------------------|-------------------------------|---------------------|------------------------------------|-----------------------|
| `eventTime`                 | `YYYY-MM-DDTHH:mm:ss.SS+0000` | `YYYY-MM-DDTHH:mm:ss.SS+0000`| `YYYY-MM-DDTHH:mm:ss.SS+0000` | `YYYY-MM-DDTHH:mm:ss.SS+0000` |
| `initiator.name`            | `Provider's name`             | `IBM`               | `user` or `service ID` in customer's account | `user` or `service ID` in customer's account |
| `initiator.id`              | `Provider's service ID`       | Leave empty         | IBMid or serviceID  | IBMid or serviceID  | 
| `initiator.typeURI`         | `service/security/account/serviceid` | `service/security/account/service` | `service/security/account/user` or `service/security/account/serviceid` | `service/security/account/user` or `service/security/account/serviceid` | 
| `initiator.credential.type` | Check guidelines | Leave empty | Check guidelines | Check guidelines | |
| `initiator.host.address`    | provider's IP address | Leave empty | User's IP address | User's IP address |
| `target.name`               | Key name |
| `target.id`                 | Key CRN |
| `target.typeURI`            | `dl/gateway/request` | `dl/gateway` | `dl/gateway/request` | `dl/gateway/request` |
| `requestData / `responseData`    | Add information on request |  Add information on request | Add information on request | Add information on request |
| `dataEvent`                 | `false` | `false` | `false` | `false` |
| `logSourceCRN`              | Per User's account | Per User's account | Per User's account | Per User's account |
| `saveServiceCopy`           | `true` | `true` | `true` | `true` |
{: caption="Register- success" caption-side="top"}













