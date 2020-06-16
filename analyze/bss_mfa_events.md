---

copyright:
  years: 2019, 2020
lastupdated: "2020-06-15"

keywords: IBM Cloud, LogDNA, Activity Tracker, account events

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

# Managing multifactor authentication settings
{: #bss_mfa_events}

Multifactor authentication (MFA) adds an extra layer of security to your account by requiring all users to authenticate by using an additional authentication method beyond an ID and password. This is also commonly known as two-factor authentication (2FA). When you change MFA settings at the account level or for users in your account, you get {{site.data.keyword.at_full_notm}} events to monitor these actions.
{:shortdesc}

As an {{site.data.keyword.cloud_notm}} account owner or administrator for the billing service, you can choose to require multifactor authentication (MFA) for every user in the account or just users with non-federated IDs who do not use SSO. All users with an IBMid use a time-based one-time passcode (TOTP) MFA method, and any users with a different type of ID must be enabled to use the time-based one-time passcode authentication (TOTP), security questions, or an external authentication method separately. [Learn more](/docs/iam?topic=iam-enablemfa).

You can also configure MFA options such as security questions, using a time-based one-time passcode, and using an external authentication method. These types of MFA options are specific per account and are available only with former classic infrastructure accounts.

To monitor changes to MFA settings in your account, you can use the {{site.data.keyword.at_full_notm}} service. 


## Events that are generated when you configure ID-based MFA
{: #mfa_events_id_based}

IBMid MFA for an account requires a time-based one-time passcode in addition to a standard IBMid and password during login. This type of MFA is enabled at the account level by the account owner or an administrator for the billing service. [Learn more](/docs/iam?topic=iam-types#id-based).

This type of MFA applies to all account resources. 

To configure ID-based MFA for users that log in to your account, you must complete the following steps:
1. As the account owner or an administrator for the billing service, turn it on or off from the **Manage** &gt; **Access (IAM)** &gt; **Settings** page in the {{site.data.keyword.cloud_notm}} console. For more information, see [enable MFA for all users in the account](/docs/iam?topic=iam-enablemfa#enabling).
2. Each user in the account must [set up TOTP](/docs/iam?topic=iam-enablemfa#enabling) to log in to your account.

You get the following events in your account when you set on MFA in the account:

* An event with action **billing.account-traits.update**

    When you select **None** as the MFA option, MFA is not enabled in the account, and all users log in by using a standard ID and password. You get the following event:

    ```json
    "action": "billing.account-traits.update",
    "message": "Billing service: update account traits",
    "requestData": {
        "mfa": "",
        "origin": "BSS"
    }
    ```
    {: screen}

    When you select **Non-federated users only** as the MFA option, the account requires MFA for non-federated users only. You get the following event:

    ```json
    "action": "billing.account-traits.update",
    "message": "Billing service: update account traits",
    "requestData": {
        "mfa": "TOTP",
        "origin": "BSS"
    }
    ```
    {: screen}

    When you select **All users** as the MFA option, the account requires MFA for all users. You get the following event:

    ```json
    "action": "billing.account-traits.update",
    "message": "Billing service: update account traits",
    "requestData": {
        "mfa": "TOTP4ALL",
        "origin": "BSS"
    }
    ```
    {: screen}

* An event with action **billing.account-mfa.set-on** if an MFA option is set on. 

* An event per user when they set up the TOTP with action **user-management.user-setting.update**.

    ```
    Add info
    ```
    {: screen}



## Events that are generated when you disable MFA for all users in your account
{: #mfa_events_id_based_dis}

When you [disable MFA for all users in your account](/docs/iam?topic=iam-enablemfa#disablemfa), you get the following events:

```
Add info
```
{: screen}




## Account-based options
{: #mfa_events_acc_based}

You can configure MFA options such as security questions, using a time-based one-time passcode, and using an external authentication method. These types of MFA options are specific per account and are available only with former classic infrastructure accounts. For more information, see [Account-based MFA options](/docs/iam?topic=iam-types#account-based).

You can modify any of the following settings:

* **User-managed login**: Allows the user to set a password expiration, turn on security questions for login, and define allowed IP addresses for {{site.data.keyword.cloud_notm}} login and classic infrastructure APIs.
* **Require MFA security questions at login**: Prompts the user for a security question at log in. To enable this setting, the user must set up answers to three security questions in their profile. 
* **User one-time passcode authentication**: Prompts the user for a one-time passcode at log in. To enable this setting, the user must set up a password expiration time in their profile.
* **This user has no external authentication set up**: Sets an external authentication provider.


### Requiring a security question at login
{: #mfa_events_acc_1}

You can add an extra layer of security at login by requiring users to answer a security question. 

You set on this setting per user.

To be able to set on this setting, the user must set up answers to three security questions in their profile. When a user that is logged in to your account [sets on security questions](/docs/account?topic=account-login-settings#security-questions), you get an event with action **user-management.user-setting.update** for each question. 

```
ADD event
```
{: screen}


After the user has configured the 3 security questions, you can [set on the setting **Require MFA security questions at login**](/docs/iam?topic=iam-questions). This action generates an event with action **user-management.user-setting.update**. 

```
ADD event
```
{: screen}


### Requiring a passcode at login
{: #mfa_events_acc_2}

You can add an extra layer of security at login by prompting a user for a one-time passcode. 

You set on this setting per user.

To be able to set on this setting, the user must set up a password expiration in their profile. When a user that is logged in to your account [sets up a password expiration](/docs/account?topic=account-login-settings#password-expiration), you get an event with action **user-management.user-setting.update**


```
ADD event
```
{: screen}


After the user has configured a password expiration, you can [set on the setting **User one-time passcode authentication**](/docs/iam?topic=iam-totp).



### User-managed login
{: #mfa_events_acc_3}

You can grant users permissions to configure MFA settings when they log in to your account. [Learn more](/docs/iam?topic=iam-loginsettings). You change the setting per user.

When you set on or off the **User-managed login** setting, an event is generated with action **user-management.user-setting.update**.

```
ADD event
```
{: screen}


In the event, `requestData` includes more information that can help you monitor these actions in your account:
* **iam_id** informs about the user in your account that has a login setting updated.
* **2FA** defines whether MFA is set on or off for the user. When it is set to false, MFA is not set for that user. Valid values are *true* and *false*.
* **security_questions_required** defines whether the user is required to set security questions to log in to the account. Valid values are *true* and *false*.
* **security_questions_setup** defines whether the user has defined the security questions in his profile. Valid values are *true* and *false*.


Notice that a user that has the **User-managed login** setting enabled, can also set on the **Require MFA security questions at login** through the *Access IAM* dashboard or through their profile. This request generates an event with action **user-management.user-setting.update**. 




