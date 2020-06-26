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


# NEW AT Adoption guidelines - please check
{: #at_new_guideline_guideline}

This page shows changes and enhancements to the AT guidelines that services should implement. All services should update AT events to reflect these new guidelines.
{:shortdesc}


## initiator host address supported types
{: #at_new_guideline_1}

[issue](https://github.ibm.com/activity-tracker/customer-issues/issues/624)

Guideline enhancement: 

Both fields are required:

1. `initiator.host.address` = IPv4 or IPv6 formatted IP address

2. `initiator.host.addressType` = `IPv4` / `IPv6`   The default value is `IPv4`. Services should start adding this field. 


## reasonForFailure
{: #at_new_guideline_2}

Currently, and to add consistency with services that adopted this value early, `reasonForFailure` is located in requestData. Services should move `requestData.reasonForFailure` to `reason.reasonForFailure`. Please, notify customers with 30 day warning.

Services who are still implementing this field, please add to `reason.reasonForFailure`.



## resourceGroupId
{: #at_new_guideline_3}

Currently, `resourceGroupId` is located in requestData and set to the CRN value. Services who have not yet implemented `resourceGroupId`, should make it a top level field. 
Please, notify customers with 30 day notice before making the change.

New services must add this field at the top level.

