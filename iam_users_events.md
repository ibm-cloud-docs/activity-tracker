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

# Managing users and permissions
{: #iam_users_events}

{{site.data.keyword.cloud_notm}} services that are organized in a resource group in your account are managed by using {{site.data.keyword.iamlong}} (IAM). You can monitor IAM actions in your account with the {{site.data.keyword.at_full_notm}} service.
{:shortdesc}

Account owners are automatically assigned the account administrator role for IAM. As the account administrator, you can assign and manage access for users, create resource groups, create access groups, view billing details and track usage, and create service instances. You provide access for users, service IDs, and access groups by creating policies that set a target for the subject of the policy to access and a role that defines what type of access that is allowed. [Learn more](/docs/iam?topic=iam-userroles).


## Events that are generated when you invite a user to your account
{: #iam_users_events_1}


### Invite a user to the account
{: #iam_users_events_1_1}

When you invite a user to your account, you get an event from the platform service **BSS** and action **user-management.user.create**.

```
8/Nov/2019:15:49:41 BSS User management service: create user
```
{: screen}

The field **target.name** includes information about the user that is being added.


### Invite a user to the account and add to one or more access groups
{: #iam_users_events_1_2}

When you invite a user, as part of the same request, you can also add this user to 1 or more access groups in your account. For each access group that you select, you get an event from the platform service **iam-groups** with action **iam-groups.member.add**.

```
8/Nov/2019:15:49:42 iam-groups IAM Access Groups: add member <Access group name>  
```
{: screen}

The field **requestData.iam_id** includes information about the user that is being added.

The field **target.name** includes information about the access group to which the user is added.

The **initiator** fields are set to an IBM owned service ID that is used to complete the clean process of the user in the account as a result of the action *user-management.user.add*.


### Invite a user to the account and assign additional access
{: #iam_users_events_1_3}

When you invite a user, you can also assign additional access to the following type of resources:

* *Cloud Foundry* to grant access to orgs and spaces that contain resources managed by Cloud Foundry. 

    You get one event to add the user to the organization with action **audit.user.organization_user_add**. 
    
    You get 1 or more events that report on the roles of that user in the organization, for example, you can get an event with action **audit.user.organization_auditor_add**.

    You get 1 or more events that report on the roles of that user in a space, for example, you can get an event with action **audit.user.space_auditor_add**.

    ```
    4/Dec/2019:15:49:22 cloud-foundry audit.user.organization_user_add 
    4/Dec/2019:15:49:22 cloud-foundry audit.user.organization_auditor_add 
    4/Dec/2019:15:49:24 cloud-foundry audit.user.space_auditor_add 
    ```
    {: screen}

* *IAM services* to grant access to IAM-enabled services.
 
    ```
    4/Dec/2019:15:49:44 iam-am IAM Access Management: create policy   
    ```
    {: screen}

    The **initiator** fields are set to an IBM owned service ID that is used to create the user's policy in the account as a result of the action *user-management.user.add**.

    In **requestData.body.subjects**, the value of the field **iam_ID** indicates the user for which this policy is created.

    In **requestData.body.roles**, you can see the roles that are granted to this user for the service specified in the value of the field **serviceName** that is available in **requestData.body.resources**.

* *Account management* to grant access to services like billing, user management, support center, and more.

    ```
    4/Dec/2019:15:49:44 iam-am IAM Access Management: create policy  
    ```
    {: screen}

    The **initiator** fields are set to an IBM owned service ID that is used to create the user's policy in the account as a result of the action *user-management.user.add**.

    In **requestData.body.subjects**, the value of the field **iam_ID** indicates the user for which this policy is created.

    In **requestData.body.roles**, you can see the roles that are granted to this user for the service specified in the value of the field **serviceName** that is available in **requestData.body.resources**.


## Events that are generated when you remove a user from the account
{: #iam_users_events_1}


When you remove a user from your account, an event from the platform service *BSS* with action **user-management.user.delete** is generated.

```
4/Dec/2019:19:22:31 BSS User management service: delete user  
```
{: screen}

The field **target.name** includes information about the user that is being removed.


* If the user belongs to 1 or more access groups, you get an event for each access group from which the user is removed. These events are generated by the platform service **iam-groups** with action **iam-groups.member.delete**.

    ```
    4/Dec/2019:19:22:32 iam-groups IAM Access Groups: delete members 
    ```
    {: screen}

    The field **responseData.member_id** includes information about the user that is being removed.

    The field **target.id** includes information about the access group from which the user is removed. You can run the command `ibmcloud iam access-groups` to list the access groups and corresponding ids in your account and identify the access group from which the user is being removed.

    The **initiator** fields are set to an IBM owned service ID that is used to complete the clean process of the user in the account as a result of the action *user-management.user.delete*.

* If the user has one or more policies assigned, you get an event for each policy that is deleted. These events are generated by the platform service **iam-am** with action **iam-am.policy.delete**.

    ```
    4/Dec/2019:19:22:22 iam-am IAM Access Management: delete policy 36419294-251b-4cde-ad0d-3752b5d73a87
    ```
    {: screen}

    The field **target.id** includes information about the policy that is being deleted.

    The **initiator** fields are set to an IBM owned service ID that is used to complete the clean process of the user in the account as a result of the action *user-management.user.delete*.
    
* If the user has permissions in a Cloud Foundry organization, you get events that are generated by the platform service **cloud-foundry**. 

    You get an event per role deleted in a space in the organization. For example to remove the auditor role of a user in a space, you get an event with action **audit.user.space_auditor_remove**.

    You get an event per role deleted in an organization. For example to remove the auditor role of a user in an organization, you get an event with action **audit.user.organization_auditor_remove**.

    You get an event to remove a user from the organization with action **audit.user.organization_user_remove**.

    You get an event to update the organization with action **audit.organization.update**.

    ```
    4/Dec/2019:19:22:28 cloud-foundry audit.user.space_auditor_remove 
    4/Dec/2019:19:22:28 cloud-foundry audit.organization.update 
    4/Dec/2019:19:22:28 cloud-foundry audit.user.organization_user_remove 
    4/Dec/2019:19:22:28 cloud-foundry audit.user.organization_auditor_remove
    ```
    {: screen}



| Managing users                                                          | Service           | Actions                                        |
|:------------------------------------------------------------------------|:------------------|:-----------------------------------------------|
| `Invite a user to an account`                                           | `BSS`             | `user-management.user.create` |
| `Remove a user from an account`                                         | `IAM`  </br>`BSS` | `iam-am.policy.delete` </br>`user-management.user.delete` |
| `Invite a user to an account and add user to one or more access groups` | `IAM`  </br>`BSS` | `user-management.user.create` </br>`iam-groups.member.add` one entry per access group selected in the action | 


## Events that are generated when you manage access groups

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


## Events that are generated when you work with policies and users


| Working with policies and users                                        | Service     | Actions                                        |
|:-----------------------------------------------------------------------|:------------|:-----------------------------------------------|
| `Add a policy for a user by assigning access to resources`             | `IAM`       | `iam-am.policy.create  `   |
| `Add a policy by assigning access within a resource group to a resource group` | `IAM`  | `iam-am.policy.create` |
| `Add a policy by assigning access within a resource group to a resource group and to a service in the resource group` | `IAM` | </br>`iam-am.policy.create` for the resource group permissions </br></br>`iam-am.policy.create` for the service permissions within the resource group |
| `Modify a policy for a user`                                           | `IAM`       | `iam-am.policy.update` |
| `Delete a policy for a user`                                           | `IAM`       | `iam-am.policy.update` |


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


## Events that are generated when you work with API keys



| Working with API keys                   | Service     | Actions                                        |
|:----------------------------------------|:------------|:-----------------------------------------------|
| `Create an IBM Cloud API key`           | `IAM`       | `iam-identity.user-apikey.create` |
| `Lock an API key`                       | `IAM`       |`iam-identity.user-apikey.update` |
| `Unlock an API key`                     | `IAM`       | `iam-identity.user-apikey.update` |
| `Change the description of an API key`  | `IAM`       | `iam-identity.user-apikey.update`  |
| `Rename an API key`                     | `IAM`       |`iam-identity.user-apikey.update` |
| `Delete an API key`                     | `IAM`       |`iam-identity.user-apikey.delete` |





