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




