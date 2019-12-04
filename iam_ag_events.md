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

# Managing access groups
{: #iam_ag_events}

{{site.data.keyword.cloud_notm}} services that are organized in a resource group in your account are managed by using {{site.data.keyword.iamlong}} (IAM). You can monitor IAM actions in your account with the {{site.data.keyword.at_full_notm}} service.
{:shortdesc}






## Events that are generated when you manage access groups
{: #iam_users_events_1}

| Working with access groups                                             | Service     | Actions                                        |
|:-----------------------------------------------------------------------|:------------|:-----------------------------------------------|
| `Create an access group`                                               | `IAM`       | `iam-groups.group.create` |
| `Add a user to a group or add service ID to a group`                   | `IAM`       | `iam-groups.group.read` </br>`iam-groups.member.add` |
| `Remove an access group`                                               | `IAM`       | `iam-groups.group.delete` </br>`iam-groups iam-groups.members.delete` </br>`iam-groups iam-groups.rules.delete` |
| `Rename an access group`                                               | `IAM`       | `iam-groups.group.read` </br>`iam-groups.group.update` |



## Events that are generated when you manage access groups and policies

| Working with policies and access groups                                | Service     | Actions                                        |
|:-----------------------------------------------------------------------|:------------|:-----------------------------------------------|
| `Add a policy by assigning access to resources`                        | `IAM`       | `iam-groups.group.read` </br>`iam-am.policy.create` |
| `Add a policy by assigning access within a resource group to a resource group` | `IAM`       |  `iam-groups.group.read` </br>`iam-am.policy.create` |
| `Add a policy by assigning access within a resource group to a resource group and to a service in the resource group` | `IAM` | `iam-groups.group.read` </br>`iam-am.policy.create` for the resource group permissions </br></br>`iam-am.policy.create` for the service permissions within the resource group |
| `Add a policy by assigning access to account management services`      | `IAM`       | `iam-groups.group.read` </br>`iam-am.policy.create` |
| `Modify a policy for an access group`                                  | `IAM`       | `iam-groups.group.read` </br>`iam-am.policy.update` |
| `Delete a policy`                                                      | `IAM`       | `iam-groups.group.read` </br>`iam-am.policy.delete` |
