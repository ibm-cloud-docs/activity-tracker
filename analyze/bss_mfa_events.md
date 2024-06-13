---

copyright:
  years: 2019, 2024
lastupdated: "2024-05-24"

keywords:

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}

# Managing multifactor authentication settings
{: #bss_mfa_events}



Multifactor authentication (MFA) adds an extra layer of security to your account by requiring all users to authenticate by using an additional authentication method beyond an ID and password. This is also commonly known as two-factor authentication (2FA). When you change MFA settings at the account level or for users in your account, you get {{site.data.keyword.at_full_notm}} events to monitor these actions.
{: shortdesc}


{{../../log-analysis/_include-segments/deprecation_notice.md}}

As an {{site.data.keyword.cloud_notm}} account owner or administrator for the billing service, you can choose to require multifactor authentication (MFA) for every user in the account or just users with non-federated IDs who do not use SSO. All users with an IBMid use a time-based one-time passcode (TOTP) MFA method, and any users with a different type of ID must be enabled to use the time-based one-time passcode authentication (TOTP), security questions, or an external authentication method separately. [Learn more](/docs/account?topic=account-enablemfa).

You can also configure MFA options such as security questions, using a time-based one-time passcode, and using an external authentication method. These types of MFA options are specific per account and are available only with former classic infrastructure accounts.

To monitor changes to MFA settings in your account, you can use the {{site.data.keyword.at_full_notm}} service.


## Events that are generated when you configure ID-based MFA
{: #mfa_events_id_based}

IBMid MFA for an account requires a time-based one-time passcode in addition to a standard IBMid and password during login. This type of MFA is enabled at the account level by the account owner or an administrator for the billing service. [Learn more](/docs/account?topic=account-types#id-based).

This type of MFA applies to all account resources.

To configure ID-based MFA for users that log in to your account, you must complete the following steps:
1. As the account owner or an administrator for the billing service, turn MFA on or off from the **Manage** &gt; **Access (IAM)** &gt; **Settings** page in the {{site.data.keyword.cloud_notm}} console. For more information, see [enable MFA for all users in your account](/docs/account?topic=account-enablemfa#enabling).
2. Each user in the account must [set up TOTP](/docs/account?topic=account-enablemfa#setupapp) to log in to your account.

You get the following events in your account when you set on MFA in the account:

* One event with action **billing.account-traits.update**.

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

* One event that reports whether MFA is enabled or disabled in the account.

    When MFA is enabled, you get an event with action **billing.account-mfa.set-on**.

    When MFA is disabled, you get an event with action **billing.account-mfa.set-off**.



## Account-based options
{: #mfa_events_acc_based}

You can configure MFA options such as security questions, using a time-based one-time passcode, and using an external authentication method. These types of MFA options are specific per account and are available only with former classic infrastructure accounts. For more information, see [Account-based MFA options](/docs/account?topic=account-types#account-based).

You can modify any of the following settings:

* **User-managed login**: Allows the user to set a password expiration, turn on security questions for login, and define allowed IP addresses for {{site.data.keyword.cloud_notm}} login and classic infrastructure APIs.
* **Require MFA security questions at login**: Prompts the user for a security question at log in. To enable this setting, the user must set up answers to three security questions in their profile.
* **User one-time passcode authentication**: Prompts the user for a one-time passcode at log in. To enable this setting, the user must set up a password expiration time in their profile.
* **This user has no external authentication set up**: Sets an external authentication provider.

In the events that are generated, `requestData` includes information that you can use to monitor these actions in your account:
* Field **iam_id**: The user in your account whose login setting is updated.
* Field **2FA**: Defines whether MFA is set on or off for the user. When it is set to false, MFA is not set for that user. Valid values are *true* and *false*.
* Field **security_questions_setup**: Defines whether the user has defined the security questions in his profile. Valid values are *true* and *false*.
* Field **self_manage**: Defines whether a user can configure his log in settings. This field is set to `true` to allow a user to set password expiration, turn on security questions for login, and define allowed IP addresses for log in to {{site.data.keyword.cloud_notm}} and from classic infrastructure API calls.

### Requiring security questions at login
{: #mfa_events_acc_1}

You can add an extra layer of security at login by requiring users to answer a security question.

You set this setting per user.

To be able to set on this setting, the user must set up answers to three security questions in their profile. [Leaern more](/docs/account?topic=account-types).

After the user has configured the 3 security questions, you can [set on the setting **Require MFA security questions at login**](/docs/account?topic=account-questions). This action generates an event with action **user-management.user-setting.update**.

The following is an example of the `requestData` field when the **Require MFA security questions at login:** property is enabled. Notice that the `requestData.security_questions_setup` field is set to `true`.

```json
"action": "user-management.user-setting.update",
"message": "User management service: update user settings",
"requestData": {
    "2FA": true,
    "iam_id": "IBMid-xxxxxx",
    "origin": "BSS",
    "security_questions_setup": true,
    "self_manage": false
 }
}
```
{: screen}



### Requiring a passcode at login
{: #mfa_events_acc_2}

You can add an extra layer of security at login by prompting a user for a one-time passcode.

You set this setting per user.

To be able to set this setting, the user must set up a password expiration in their profile. [Learn more](/docs/account?topic=account-types).

After the user has configured a password expiration, you can [set the **User one-time passcode authentication** setting](/docs/account?topic=account-totp). This action generates an event with action **user-management.user-setting.update**.

The following is an example of the `requestData` field when the **User one-time passcode authentication:** property is enabled. The `requestData.2FA` field is set to `true`.

```json
"action": "user-management.user-setting.update",
"message": "User management service: update user settings",
"requestData": {
    "2FA": true,
    "iam_id": "IBMid-xxxxx",
    "origin": "BSS",
    "security_questions_setup": true,
    "self_manage": false
 }
}
```
{: screen}



### User-managed login
{: #mfa_events_acc_3}

You can grant users permissions to configure MFA settings when they log in to your account. [Learn more](/docs/account?topic=account-types). You change the setting per user.

When you set the **User-managed login** setting on or off, an event is generated with action **user-management.user-setting.update**.

The following is an example of the `requestData` field when the **User-managed login:** property is disabled:

```json
"action": "user-management.user-setting.update",
 "message": "User management service: update user settings",
"requestData": {
    "iam_id": "IBMid-27000757DW",
    "origin": "BSS",
    "self_manage": false
}
```
{: screen}




A user that has the **User-managed login** setting enabled, can also set the **Require MFA security questions at login** on through the *Access IAM* dashboard or through their profile. This request generates an event with action **user-management.user-setting.update**.
{: note}
