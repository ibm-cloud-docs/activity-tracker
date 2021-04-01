---

copyright:
  years: 2019, 2021
lastupdated: "2021-03-28"

keywords: IBM Cloud, Activity Tracker, users events

subcollection: activity-tracker

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

# Managing service IDs
{: #iam_serviceids_events}

{{site.data.keyword.cloud_notm}} services that are organized in a resource group in your account are managed by using {{site.data.keyword.iamlong}} (IAM). You can monitor IAM actions in your account with the {{site.data.keyword.at_full_notm}} service.
{:shortdesc}



| Working with service IDs            | Service     | Actions                                        |
|:------------------------------------|:------------|:-----------------------------------------------|
| `Create a service ID`               | `IAM`       | `iam-identity.account-serviceid.create` |
| `Delete a service ID`               | `IAM`       | `iam-identity.account-serviceid.delete` | 
| `Lock a service ID`                 |  `IAM`       |`iam-identity.account-serviceid.update` |
| `Unlock a service ID`               |  `IAM`       |`iam-identity.account-serviceid.update` |
| `Rename a service ID`               |  `IAM`       |`iam-identity.account-serviceid.update` |
| `Change the service ID description` |  `IAM`       |`iam-identity.account-serviceid.update` |
| `Create an API key for a service ID` |  `IAM`       |`iam-identity.serviceid-apikey.create` </br>`iam-am.policy.create`|
{: caption="Table 1. Actions generated when working with service IDs" caption-side="top"} 




## Events that are generated when you work with policies and service IDs
{: #iam_serviceids_events_policies}

| Working with policies and users                                                 | Actions                                        |
|:--------------------------------------------------------------------------------|:-----------------------------------------------|
| `Add a policy by assigning access to resources`                                 | `iam-am.policy.create  `   |
| `Add a policy by assigning access within a resource group to a resource group`  | `iam-am.policy.create` |
| `Add a policy by assigning access within a resource group to a resource group and to a service in the resource group` | `iam-am.policy.create` for the resource group permissions </br></br>`iam-am.policy.create` for the service permissions within the resource group |
| `Modify a policy`                                                               | `iam-am.policy.update` |
| `Delete a policy`                                                               | `iam-am.policy.update` |
{: caption="Table 2. Actions generated when you assign a policy to a service ID" caption-side="top"} 


### Add a policy by assigning access to resources
{: #iam_serviceids_events_policies_1}


### Add a policy by assigning access within a resource group to a resource group
{: #iam_serviceids_events_policies_2}


### Modify a policy
{: #iam_serviceids_events_policies_3}


### Delete a policy
{: #iam_serviceids_events_policies_5}




