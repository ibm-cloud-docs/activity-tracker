---

copyright:
  years: 2019
lastupdated: "2019-12-04"

keywords: IBM Cloud, LogDNA, Activity Tracker, users events

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

# Managing service IDs
{: #iam_serviceIDs_events}

{{site.data.keyword.cloud_notm}} services that are organized in a resource group in your account are managed by using {{site.data.keyword.iamlong}} (IAM). You can monitor IAM actions in your account with the {{site.data.keyword.at_full_notm}} service.
{:shortdesc}





## Events that are generated when you work with service IDs

| Working with service IDs            | Service     | Actions                                        |
|:------------------------------------|:------------|:-----------------------------------------------|
| `Create a service ID`               | `IAM`       | `iam-identity.account-serviceid.create` |
| `Delete a service ID`               | `IAM`       | `iam-identity.account-serviceid.delete` | 
| `Lock a service ID`                 |  `IAM`       |`iam-identity.account-serviceid.update` |
| `Unlock a service ID`               |  `IAM`       |`iam-identity.account-serviceid.update` |
| `Rename a service ID`               |  `IAM`       |`iam-identity.account-serviceid.update` |
| `Change the service ID description` |  `IAM`       |`iam-identity.account-serviceid.update` |
| `Create an API key for a servie ID` |  `IAM`       |`iam-identity.serviceid-apikey.create` </br>`iam-am.policy.create`|





## Events that are generated when you work with policies and service IDs


| Working with policies and users                                        | Service     | Actions                                        |
|:-----------------------------------------------------------------------|:------------|:-----------------------------------------------|
| `Add a policy for a user by assigning access to resources`             | `IAM`       | `iam-am.policy.create  `   |
| `Add a policy by assigning access within a resource group to a resource group` | `IAM`  | `iam-am.policy.create` |
| `Add a policy by assigning access within a resource group to a resource group and to a service in the resource group` | `IAM` | </br>`iam-am.policy.create` for the resource group permissions </br></br>`iam-am.policy.create` for the service permissions within the resource group |
| `Modify a policy for a user`                                           | `IAM`       | `iam-am.policy.update` |
| `Delete a policy for a user`                                           | `IAM`       | `iam-am.policy.update` |




