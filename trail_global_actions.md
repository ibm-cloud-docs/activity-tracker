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


| Managing users                                                         | Service     | Actions                                        |
|:-----------------------------------------------------------------------|:------------|:-----------------------------------------------|
| `Invite a user to an account`                                          | `BSS`       | `user-management.user.create` |
| `Remove a user from an account`                                        | `IAM`  </br>`BSS` | `iam-am.policy.delete` </br>`user-management.user.delete` |
| `Invite a user to an account and add user to one or more access groups` | `IAM`  </br>`BSS`| `user-management.user.create` </br>`iam-groups.member.add` one entry per access group selected in the action | 
| `Create an access group`                                                | `IAM`      | `iam-groups.group.create` |
| `Add a user to a group or add service ID to a group`                   | `IAM`      | `iam-groups.group.read` </br>`iam-groups.member.add` |
| `Remove an access group`       | `IAM`       | `iam-groups.group.delete` </br>`iam-groups iam-groups.members.delete` </br>`iam-groups iam-groups.rules.delete` |
| `Add a policy by assigning access to resources` | `IAM`| `iam-groups.group.read` </br>`iam-am.policy.create` |
| `Add a policy by assigning access within a resource group` | `IAM` |  `iam-groups.group.read` </br>`iam-am.policy.create` |
| `Add a policy by assigning access within a resource group to the resource group and to a service in the resource group` | `IAM` | `iam-groups.group.read` </br>`iam-am.policy.create` for the resource group permissions </br></br>`iam-am.policy.create` for the service permissions within the resource group |
| `Add a policy by assigning access to account management services` | `iam-groups.group.read` </br>`iam-am.policy.create` |
| `Rename an access group` | `IAM` | `iam-groups.group.read` </br>`iam-groups.group.update` |

