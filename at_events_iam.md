---

copyright:
  years: 2019
lastupdated: "2019-09-12"

keywords: IBM Cloud, LogDNA, Activity Tracker, IAM events

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


# IAM events
{: #at_events_iam}

As a security officer, auditor, or manager, you can use the {{site.data.keyword.at_full_notm}} service to track how users and applications interact with the {{site.data.keyword.iamlong}} (IAM) service in {{site.data.keyword.cloud_notm}}. 
{:shortdesc}

IAM enables you to securely authenticate users for both platform services and control access to resources consistently across {{site.data.keyword.cloud_notm}}. [Learn more](/docs/iam?topic=iam-iamoverview).


The {{site.data.keyword.at_full_notm}} service records user-initiated activities that change the state of a service in {{site.data.keyword.cloud_notm}}. To get started monitoring your user's actions, see [{{site.data.keyword.at_full_notm}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started). An initiator can be a user, a service, or an application.


## Access groups events
{: #at_events_iam_access}

The following table lists the actions that generate an event:

| Action                      | Description |
|-----------------------------|---------|
| `iam-groups.group.create`   | An event is generated when an initiator creates an access group. | 
| `iam-groups.group.read`     | An event is generated when an initiator looks at information that is related with access groups. |
| `iam-groups.group.update`   | An event is generated when an initiator updates a group name or a description. |
| `iam-groups.group.delete`   | An event is generated when an initiator deletes an access group. |
| `iam-groups.member.add`     | An event is generated when an initiator adds a member to an access group. |
| `iam-groups.member.delete`  | An event is generated when an initiator removes a member from an access group. |
| `iam-groups.member.read`    | An event is generated when an initiator checks a member's membership. |
| `iam-groups.rule.read`      | An event is generated when an initiator views a rule in an access group. |
| `iam-groups.rule.create`    | An event is generated when an initiator adds a rule to an access group. |
| `iam-groups.rule.update`    | An event is generated when an initiator modifies the rule name. |
| `iam-groups.rule.delete`    | An event is generated when an initiator deletes a rule from an access group. |
| `iam-groups.member.federated-login` | An event is generated when an initiator logs in to the account and gains federated membership to an access group. |
{: caption="Table 1. Manage access groups actions" caption-side="top"} 



## Policy events
{: #at_events_iam_policies}

The following table lists the actions that generate an event:

| Action                 | Description |
|------------------------|---------|
| `iam-am.policy.create` | An event is generated when an initiator adds a policy to a user or access group. |
| `iam-am.policy.delete` | An event is generated when an initiator modifies permissions to a policy of a user or access group.|
| `iam-am.policy.update` | An event is generated when an initiator deletes a policy that is assigned to a user or access group. |
{: caption="Table 5. Managing policy actions" caption-side="top"} 



## Service ID events
{: #at_events_iam_serviceids}

The following table lists the actions that generate an event:

| Action | Description |
|----------|---------|
| `iam-identity.account-serviceid.create` | An event is generated when an initiator creates a service ID.  | 
| `iam-identity.account-serviceid.update` | An event is generated when an initiator renames a service ID or modifies its description. | 
| `iam-identity.account-serviceid.delete` | An event is generated when an initiator deletes a service ID. | 
{: caption="Table 2. Working with service IDs actions" caption-side="top"} 


## API key events
{: #at_events_iam_apikeys}

The following table lists the actions that generate an event:

| Action | Description |
|----------|---------|
| `iam-identity.user-apikey.create`      | An event is generated when an initiator creates an API key. | 
| `iam-identity.user-apikey.update`      | An event is generated when an initiator renames an API key or modifies its description. |  
| `iam-identity.user-apikey.delete`      | An event is generated when an initiator deletes an API key. |  
| `iam-identity.serviceid-apikey.create` | An event is generated when an initiator creates an API key for a service ID. |  
| `iam-identity.serviceid-apikey.delete` | An event is generated when an initiator deletes an API key for a service ID. |  
| `iam-identity.serviceid-apikey.update` | An event is generated when an initiator renames an API key for a service ID or modifies its description. |
{: caption="Table 3. Working with API keys actions" caption-side="top"} 


## Login events
{: #at_events_iam_login}

The following table lists the actions that generate an event:

| Action                                   | Description |
|------------------------------------------|---------|
| `iam-identity.user-apikey.login`         | An event is generated when a user logs in to the {{site.data.keyword.cloud_notm}} by using an API key. |  
| `iam-identity.serviceid-apikey.login`    | An event is generated when an initiator logs in to the {{site.data.keyword.cloud_notm}} by using an API key that is associated with a service ID. |  
| `iam-identity.user-identitycookie.login` | This is an event that is generated when an initiator requests an identity cookie to run an action. |
| `iam-identity.user-refreshtoken.login`   | This is an event that is generated when the initiator logs in to the IBM Cloud , or when an initiator that has already logged in to the IBM Cloud requests a new refresh token to run an action. |
{: caption="Table 4. User login actions" caption-side="top"} 

## License and entitlement events
{: #at_events_iam_entitlement}

The following table lists the actions that generate an event:

| Action                                   | Description |
|------------------------------------------|---------|
| `entitlement.entitlement.create`         | An event is generated when an initiator binds a license to an account. |  
| `entitlement.entitlement.delete`    | An event is generated when an initiator deletes an entitlment. |  
| `entitlement.entitlement.update`   | An event is generated when an initiator updates an entilement. |
| `entitlement.entitlement.check`   | An event is generated when an initiator has used an entitlement to pull an image from the goverend IBM Container Registry. |
{: caption="Table 5. User entitlement actions" caption-side="top"} 

## Viewing events
{: #at_events_iam_ui}

Events are available in the **Frankfurt (eu-de)** region. 

To view these events, you must [provision an instance](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-provision#provision) of the {{site.data.keyword.at_full_notm}} service in the **Frankfurt (eu-de)** region. Then, you must [open the {{site.data.keyword.at_full_notm}} UI](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-launch#launch_step2). 


## Analyzing events
{: #at_events_iam_analyze}

### Login events
{: #an_login_events} 

In the {{site.data.keyword.cloud_notm}}, an administrator, or a user that has the correct access in your account, has different options to manage a user's login settings. For example, an administrator can order external authentication options, enable a one-time passcode to be used during login, enable the use of security questions at login, or set a password expiration time period. [Learn more](/docs/iam?topic=iam-loginsettings). 

* A user can log in by using a user ID and password.
* A federated user that uses a corporate or enterprise single sign-on ID can log in to {{site.data.keyword.cloud_notm}} from the command-line interface (CLI) by using either a one-time passcode or an API key. [Learn more](/docs/iam?topic=iam-federated_id). 
* A user can log in by using an API key.  

The following fields include extra information:
* The `initiator.name` includes information about the user that logs in to the account.
* The `X-Global-Transaction-Id` includes an ID that you can use when you open a support ticket if you need to get more information.


**Log in from the {{site.data.keyword.cloud_notm}} UI**

When a user logs in from the {{site.data.keyword.cloud_notm}} UI, you get an event in the account with action `iam-identity.user-refreshtoken.login`.

The following field includes extra information:
* In requestData, the `client_id` field is set to **HOP55v1CCT**. This value indicates a UI request.


**Log in with a federated ID from the {{site.data.keyword.cloud_notm}} CLI by using a one-time passcode or an API key**

When a user [logs in from the {{site.data.keyword.cloud_notm}} CLI by using a one-time passcode](/docs/iam?topic=iam-federated_id#onetime_passcode), you get an event in the account with action `iam-identity.user-refreshtoken.login`.

When a user [logs in from the {{site.data.keyword.cloud_notm}} CLI by using an API key](/docs/iam?topic=iam-federated_id#api_key), you get an event in the account with action `iam-identity.user-apikey.login`.

The following field includes extra information:
* In requestData, the `client_id` field is set to **bx**. This value indicates a CLI request.



**Failed log in actions**

When a user logs in to the {{site.data.keyword.cloud_notm}}, the user ID (IBMid) and credentiasls are validated first. At this point, the user has not selected an account. Notice that a user can belong to multiple accounts. 

After the user ID is authenticated successfully in the {{site.data.keyword.cloud_notm}}, the user can choose an account. It is at this point in the process that an account is associated to the log in request, and an event with action `iam-identity.user-refreshtoken.login`, or `iam-identity.user-apikey.login` is generated in your account.

In Activity Tracker, you can see events that are associated to your account. Failed log in actions do not generate an event that you can monitor in your account.


### Delete an access group
{: #an_del_ag}

When you delete an access group, the event that is triggered has an `action` field set to `iam-groups.group.delete`.

When an access group is deleted, consider the following information:
* Other actions are automatically triggered to clean up other resources that are associated with the group. Some actions that are triggered report events that are related to deletion of members in an access group, deletion of policies, and deletion of dynamic rules. 
* The initiator of these actions is an {{site.data.keyword.IBM_notm}} service ID.


When the access group that is deleted does not have members, policies, and rules assigned, the events that are generated for any of these resources report an outcome of`failure` with a `404` outcome code. The following sample shows the events that are generated when an access group that does not have members, policies or dynamic rules assigned is deleted:

```
Apr 29 14:11:22 IAM Access Groups: delete group test5
Apr 29 14:11:24 IAM Access Groups: delete members -failure
Apr 29 14:11:24 IAM Access Groups: delete rules -failure
Apr 29 14:11:24 IAM Access Management: delete policy -failure
```
{: screen}



### Update an account service ID
{: #an_update_acc_scvid}

A service ID identifies a service or application similar to how a user ID identifies a user. [Learn more](/docs/iam?topic=iam-serviceids).

When an action to update a service ID is requested, you get an event in the account with action `iam-identity.account-serviceid.update`.

The following fields include extra information:
* The `initiator.name` field includes information about who has requested to update the service ID.
* The `target.name` field includes information about the service ID that is changed.
* The `initiator.host.agent` field indicates if the request comes from the UI or the CLI. When the field is set to **NotSet**, the request originates in the UI. When the field is set to **IBM Cloud CLI...**, the request originates in the command-line. 

**Lock and unlock a service ID**

The following field includes extra information:
* In requestData, the `lock` field is set to **true** when the service ID is locked, and to **false** when it is unlocked.


**Add or modify a description**

When a request to change a description generates an event, the following fields include information that can help you determine this action:
* In requestData, the `lock` field is set to **false**.
* In requestData, the `prev_instance_name` field and the `instance_name` field are set to the same value.

**Change the name of a service ID**

The following fields include extra information:
* In requestData, the `lock` field is set to **false**.
* In requestData, the `instance_name` field includes the new name of the API key. 
* In requestData, the `prev_instance_name` field includes the name of the API key before it was changed.



### Update a user API key or a service ID API key
{: #an_update_apikey}

When an action to update an API key is requested, you get an event in the account with one of the following actions:
* To update a user API key, the action is `iam-identity.user-apikey.update`.
* To update a service ID API key, the action is `iam-identity.account-serviceid.update`.

The following fields include extra information:
* The `initiator.name` field includes information about who has requested to update the API key. 
* The `target.name` field includes information about the API key that is changed.
* The `initiator.host.agent` field indicates if the request comes from the UI or the CLI. When the field is set to **NotSet**, the request originates in the UI. When the field is set to **IBM Cloud CLI...**, the request originates in the command-line. 


**Lock and unlock a service ID**

The following field includes extra information:
* In requestData, the `lock` field is set to **true** when the API key is locked, and to **false** when it is unlocked.


**Add or modify a description**

When a request to change a description generates an event, the following fields include information that can help you determine this action:
* In requestData, the `lock` field is set to **false**.
* In requestData, the `prev_instance_name` field and the `instance_name` field are set to the same value.

**Change the name of a service ID**

The following fields include extra information:
* In requestData, the `lock` field is set to **false**.
* In requestData, the `instance_name` field includes the new name of the API key. 
* In requestData, the `prev_instance_name` field includes the name of the API key before it was changed.

## Analyzing events that fail
{: #at_events_iam_analyze_fail}

### Initiator not authorized. Request to update an API key or service ID fails
{: #an_fail_not_authorized}

For example, when a user logs into your account using an API key, the user is authenticated to access your account. However, this API key may not have permissions to run actions to modify API keys or service IDs in the account. When this happens, you get one of the following messages:
* **IAM Identity Service: update user-apikey APIKeyName -failure**
* **IAM Identity Service: update account-serviceid ServiceIDName -failure**

To look for information about the user that has requested a change to an API key or to a service ID, look at the initiator fields in the event.

When a user does not have permissions to run this action in your account, you get a failure event:
* The `initiator.name` field is empty. This information is not available at the time the event is generated.
* The user ID has been authenticated in your {{site.data.keyword.cloud_notm}} account.
* The action targets your account.
* The user ID is not authorized to run this action in your account.

To find out the user who has tried to modify an API key or a service ID, complete the following steps:
1. Copy the value of the `initiator.id`. This field includes the ID of the user that is trying to run this action in your account. 
2. Get the email address that is associated with the user. To complete this step, you must have administrator permissions in the account. Run the following command:

    ```
    ibmcloud iam users --output json | grep -A 1 InitiatorID 
    ```
    {: codeblock}

    Where InitiatorID is the value of the field `initiator.id`, and has the format IBMid-XXXXXXXXXX.
    
    The output of this command returns 2 fields. The `ibmUniqueId` field shows the ID of the user that matched the event `initiator.name` field. The `email` field shows the email address associated with that ID.

To get the API key on which the action has been requested and failed, see the field `prev_instance_name` in requestData.


### Resource is locked. Request to update Service ID or API key fails
{: #an_fail_locked}

When a service ID or an API key are locked, you cannot change any of its attributes. The event that is generated has an `outcome` of **failure**.

Depending on the resource type, you can get any of the following messages:
* Service ID: The message that you get says **IAM Identity Service: update account-serviceid ServiceIDName -failure** where *ServiceIDName* is the name of the service ID.
* User API key: The message that you get says **IAM Identity Service: update user-apikey APIkeyName -failure** where *APIkeyName* is the name of the API key.
* Account API key: The message that you get says **IAM Identity Service: update account-apikey APIkeyName -failure** where *APIkeyName* is the name of the API key.

In the event, the `lock` field in requestData is set to **true**. This is the reason why this action fails. To successfully change an attribute of a service ID, the `lock` field must be set to **false**.

Notice that the field `severity` is set to **critical**. Someone is trying to modify a service ID that is locked in the account.



