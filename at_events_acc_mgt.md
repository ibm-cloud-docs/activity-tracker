---

copyright:
  years: 2019
lastupdated: "2019-07-04"

keywords: IBM Cloud, LogDNA, Activity Tracker, account events

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

# Account management events  
{: #at_events_acc_mgt}

As a security officer, auditor, or manager, you can use the {{site.data.keyword.at_full_notm}} service to track how users and applications interact with the {{site.data.keyword.cloud_notm}} account. 
{:shortdesc}

The {{site.data.keyword.at_full_notm}} service records user-initiated activities that change the state of a service in {{site.data.keyword.cloud_notm}}. To get started, see [{{site.data.keyword.at_full_notm}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started). 



## Events for managing accounts
{: #at_events_acc_mgt_account}

The following table lists the actions that generate an event:

| Action                               | Description |
|--------------------------------------|-------------|
| `billing.account.create`             | An event is generated when you provision an account after the account ID is assigned to the account. |
| `billing.account.update`             | An event is generated when you update information about the account.  |
| `billing.account.active`             | An event is generated when you verify the account, that is, an event is generated when the account becomes active. |
| `billing.account.subscription.create` | An event is generated when you create a <a href="/docs/account?topic=account-accounts#subscription-account">Subscription account</a>. |
{: caption="Table 1. Actions that generate events" caption-side="top"} 




## Events for managing users
{: #at_events_acc_mgt_users}

The following table lists the actions that generate an event:

| Action                               | Description |
|--------------------------------------|-------------|
| `user-management.user.create`        | An event is generated when you send an invitation to a user to join an account. |
| `user-management.user.active`        | An event is generated when you activate the user in the account. When the user verifies the email address, the event is generated. |
| `user-management.user.delete`        | An event is generated when you remove a user from the account. |
| `user-management.user-setting.update` | An event is generated when you update the user's login configuration settings: *User one-time passcode authentication*, *Require MFA security questions at login*, *User-managed login* or *Setting up security questions* |
{: caption="Table 2. Actions that generate events" caption-side="top"} 



## Events for managing organizations
{: #at_events_acc_mgt_org}

The following table lists the actions that generate an event:

| Action                               | Description |
|--------------------------------------|-------------|
| `billing.account.org.create`         | An event is generated when you add an organization to the account. |
{: caption="Table 3. Actions that generate events" caption-side="top"} 


## Events for managing tags
{: #at_events_acc_mgt_resources}

The following table lists the actions that generate an event:

| Action                                          | Description |
|-------------------------------------------------|-------------|
| `global-search-tagging.tag.attach-tag`          | An event is generated when you add a tag to a resource. |
| `global-search-tagging.tag.detach-tag`          | An event is generated when you remove a tag from a resource.  |
{: caption="Table 4. Actions that generate events" caption-side="top"} 


## Where to look for the events
{: #at_events_acc_mgt_ui}

Events are available in the **Frankfurt (eu-de)** region. 

To view these events, you must [provision an instance](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-provision#provision) of the {{site.data.keyword.at_full_notm}} service in the **Frankfurt (eu-de)** region. Then, you must [open the {{site.data.keyword.at_full_notm}} UI](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-launch#launch_step2). 


## Analyzing events
{: #at_events_acc_mgt_analyze}

### MFA user log in settings
{: #user_login_settings_events} 

An account owner or an administrator with permissions to manage users can modify the login settings of other users in the account. [Learn more](/docs/account?topic=account-login-settings). For example, they can modify the following settings:
* **User-managed login**: Allows the user to set a password expiration, turn on security questions for login, and define allowed IP addresses for {{site.data.keyword.cloud_notm}} login and classic infrastructure APIs.
* **Require MFA security questions at login**: Prompts the user for a security question at log in. To enable this setting, the user must set up answers to three security questions in their profile. 
* **User one-time passcode authentication**: Prompts the user for a one-time passcode at log in. To enable this setting, the user must set up a password expiration time in their profile.
* **This user has no external authentication set up**: Sets an external authentication provider.

When the account owner or an administrator with permissions to manage users sets on or off any of these settings for a user in the account, you get an event with action **user-management.user-setting.update**.

When a user that is logged in to your account [sets on security questions](/docs/account?topic=account-login-settings#security-questions), you get an event with action **user-management.user-setting.update** for each question. 

When a user that is logged in to your account [sets on or off a password expiration](/docs/account?topic=account-login-settings#password-expiration), you get an event with action **user-management.user-setting.update**.

If the a user has the **User-managed login** setting enabled, the user can also set on the **Require MFA security questions at login** through the *Access IAM* dashboard or through their profile. This request generates an event with action **user-management.user-setting.update**. 

For any of these events, requestData includes more information that can help you monitor these types of actions in your account:
* **iam_id** informs about the user in your account that has a login setting updated.
* **2FA** defines whether MFA is set on or off for the user. When it is set to false, MFA is not set for that user. Valid values are *true* and *false*.
* **security_questions_required** defines whether the user is required to set security questions to log in to the account. Valid values are *true* and *false*.
* **security_questions_setup** defines whether the user has defined the security questions in his profile. Valid values are *true* and *false*.






