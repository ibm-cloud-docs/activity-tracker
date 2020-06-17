---

copyright:
  years: 2019, 2020
lastupdated: "2020-01-08"

keywords: IBM Cloud, LogDNA, Activity Tracker, IAM events

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


# Managing events from log in actions in an account
{: #iam_manage_login}

As a security officer, auditor, or manager, you can use the {{site.data.keyword.at_full_notm}} service to track how users, applications, and services interact with your account. The {{site.data.keyword.iamlong}} (IAM) service in {{site.data.keyword.cloud_notm}} generates events that you can use to monitor log in activity to your account. This tutorial explains the different log in options to {{site.data.keyword.cloud_notm}} and what happens from an IAM and an {{site.data.keyword.at_full_notm}} perspective. You can also find out how to define views and dashboards to monitor these actions in your account.
{:shortdesc}

To work in the {{site.data.keyword.cloud_notm}}, a user, an application, or a service must log in to {{site.data.keyword.cloud_notm}}. The user, application, or service needs valid credentials to access an account and run actions on services in that account.

As a user, you can log in to the {{site.data.keyword.cloud_notm}} in any of the following ways:
* Log in through the {{site.data.keyword.cloud_notm}} UI
* Log in from the command-line interface (CLI) by using an API key
* Log in from the command-line interface (CLI) by using a one-time passcode
* Log in from the command-line interface (CLI) by using a user ID and password

As a service, you log in to the {{site.data.keyword.cloud_notm}} by using an API key that is associated to a service ID.

If you are a new user of the {{site.data.keyword.cloud_notm}}, [you must request an IBMid ![External link icon](../../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/login){:new_window}. When you register to work in the {{site.data.keyword.cloud_notm}}, you get an IBMid, and an account is created and associated to your IBMid. 

Once you have registered to {{site.data.keyword.cloud_notm}}, you can be invited to be a member in other accounts in {{site.data.keyword.cloud_notm}}. When you are invited to work in an account that is different from the default account that is associated with your IBMid, an event with action **user-management.user.create** is generated and available in the  account where you are invited to work. Users in the account with permissions to monitor Activity Tracker events can monitor these events through the {{site.data.keyword.at_full_notm}} instance in Frankfurt.

For a user to log in successfully to your account, consider the following information:
1. First, the credentials of the user or service are validated in {{site.data.keyword.cloud_notm}}.
2. If the credentials are validated and the user or service is authorized to work in the {{site.data.keyword.cloud_notm}}, a token is issued by the IAM Identity service.

    Depending on the way that the user logs in, an account might be pre-selected, the account might be embedded in the API key, or the user might have to select one account after the credentials are validated. Therefore, the token might include account details or not. 

3. [User log in request only] If account information is not included, the user must select or switch account. 

An Activity Tracker event is generated and available in your account after the credentials are validated in the {{site.data.keyword.cloud_notm}}, and account details are available.

As owner or person responsible of the account access management, you can expect an event in your account in any of the following scenarios:
* User logs in from the UI: You get a log in event after the user's log in credentials (IBMid) are validated in {{site.data.keyword.cloud_notm}} and the user switches to work with your account.
* User logs in from the CLI by using a user ID and password, or a one-time passcode: You get a log in event after the user's log in credentials (IBMid) are validated in {{site.data.keyword.cloud_notm}} and the user selects your account.
* User logs in from the CLI by using an API key: You get a log in event after the user's log in credentials (IBMid) are validated in {{site.data.keyword.cloud_notm}}. The account details are included in the key.
* Service logs in by using a service ID: You get a log in event after the credentials (API key of a service ID) are validated in {{site.data.keyword.cloud_notm}}. The account details are included in the API key.


**You only get Activity Tracker events for successful log in requests to your account.**
{: important}



## User logs in through the {{site.data.keyword.cloud_notm}} UI
{: #iam_manage_login_ui}

For a user to log in successfully to your account through the {{site.data.keyword.cloud_notm}} UI, consider the following information:

1. To initiate the log in requets, the user must launch the [{{site.data.keyword.cloud_notm}} UI ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/login){:new_window}.

2. After the user enters the IBMid credentials into the browser, the data is forwarded to the IAM Identity Service.

3. If the credentials are validated and the user is authenticated to work in the pre-selected account, the IAM Identity Service returns an access token and a refresh token. These tokens are bounded to the default account and include information to allow the user to choose other accounts where the user is a member. 

    By default, an account is pre-selected. This account is the one that is associated to the IBMid of the user. 

4. At this point in the process, the IAM Identity Service generates an Activity Tracker event with action **iam-identity.user-refreshtoken.login**. This event is available in the user's default account, that is the account where the user is account owner.

5. Next, the user switches account and selects a different account.

    An account is preselected by the UI during login. When the dashboard shows up you are logged in to an account, you have a dropdown to switch accounts. Selecting a different account generates additional access and refresh token events.

6. The IAM Identity Service checks the current tokens. If the user is authorized to work in the new account, the IAM Identity Service returns a new access token and a new refresh token that are bound to the new account.

7. At this point in the process, the IAM Identity Service generates an Activity Tracker event with action **iam-identity.user-refreshtoken.login**. This event is available in the new account.



## User requests to run an action in the {{site.data.keyword.cloud_notm}} UI
{: #iam_manage_login_action_ui}

In this scenario, a user is already logged in successfully to your account and runs an action on a service in your account. 

* If the user's access and refresh tokens have expired, the user needs to log in through the {{site.data.keyword.cloud_notm}} UI to continue working through the UI. An Activity Tracker event with action **iam-identity.user-refreshtoken.login** is generated.

* When the user runs an action through the {{site.data.keyword.cloud_notm}} UI, a cookie is generated. At this point in the process, an Activity Tracker event with action **iam-identity.user-identitycookie.login** is generated in the account. 




## User logs in from the CLI by using an API key
{: #iam_manage_login_cli_key}

For a user to log in successfully to your account from the CLI by using an API key, consider the following information:

1. [Pre-requisite] Installation of the {{site.data.keyword.cloud_notm}} CLI. [Learn more](/docs/cli?topic=cloud-cli-ibmcloud-cli#ibmcloud-cli).

   If the CLI is installed, continue with the next step.

2. Log in to the {{site.data.keyword.cloud_notm}} by using an API key. Run the following command: [`ibmcloud login --apikey`](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login). The API key is forwarded to the IAM Identity Service.

    Notice that the API key includes information about the account.

3. After the credentials are validated and the API key is authenticated to work in the account, the IAM Identity Service generates an Activity Tracker event with action **iam-identity.user-apikey.login**. This event is available in the account that is associated with the API key.



## User logs in from the CLI by using a one-time passcode.
{: #iam_manage_login_cli_passcode}

For a user to log in successfully to your account from the CLI by using a one-time passcode, consider the following information:


1. [Pre-requisite] Installation of the {{site.data.keyword.cloud_notm}} CLI. [Learn more](/docs/cli?topic=cloud-cli-ibmcloud-cli#ibmcloud-cli).

   If the CLI is installed, continue with the next step.

2. Log in to the {{site.data.keyword.cloud_notm}} by using a one-time passcode. Run the following command: [`ibmcloud login --sso`](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login)

3. After the credentials are validated and the user is authenticated, a token is returned.

    The token has the information to allow the user to choose an account where he is a member or owner.

    Notice that the token does not include information about the account.

4. Next, the user selects an account. An access token and a refresh token are generated and returned to the user. These tokens are bound to the selected account. The tokens contain an identity, an account, and some rights.

5. At this point in the process, the IAM Identity Service generates an Activity Tracker event with action **iam-identity.user-refreshtoken.login**.





## User logs in from the CLI by using a user ID and password
{: #iam_manage_login_cli_pwd}

For a user to log in successfully to your account from the CLI by using a user ID and password, consider the following information:

1. [Pre-requisite] Installation of the {{site.data.keyword.cloud_notm}} CLI. [Learn more](/docs/cli?topic=cloud-cli-ibmcloud-cli#ibmcloud-cli).

   If the CLI is installed, continue with the next step.

2. Log in to the {{site.data.keyword.cloud_notm}} by using an API key. Run the following command: [`ibmcloud login –u USER –p password`](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login). The API key is forwarded to the IAM Identity Service.

    Notice that the API key includes information about the account.

3. After the credentials are validated and the user is authenticated, a token is returned.
    
    The token has the information to allow the user to choose an account where he is a member or owner.

    Notice that the token does not include information about the account.

4. Next, the user selects an account. An access token and a refresh token are generated and returned to the user. These tokens are bound to the selected account. The tokens contain an identity, an account, and some rights.

5. At this point in the process, the IAM Identity Service generates an Activity Tracker event with action **iam-identity.user-refreshtoken.login**.



## A service or application logs in by using a service ID
{: #iam_manage_loginiam_manage_login_svc_id}

A service ID identifies a service or application similar to how a user ID identifies a user. These are IDs that can be used by applications to authenticate with an {{site.data.keyword.cloud_notm}} service. Policies can be assigned to each service ID to control the level of access that is allowed by an application that uses the service ID, and an API key can be created to enable the authentication.

For a service or application to log in successfully to your account by using an API key that is associated with a service ID, consider the following information:

1. Your service or application uses the API key that is associated with the service ID to authenticate in the {{site.data.keyword.cloud_notm}}.

    Notice that the API key includes information about the account.

2. After the credentials are validated and the API key is authenticated to work in the account, the IAM Identity Service generates an Activity Tracker event with action **iam-identity.serviceid-apikey.login**. This event is available in the account that is associated with the API key.



## Summary
{: #iam_manage_login_summ}

The following table shows the IAM event that is generated in each of the log in cases:

| Type     | Action                                   | Description |
|----------|------------------------------------------|-----------------------------|
| Service  | `iam-identity.serviceid-apikey.login`    | An event is generated when a service logs in to the {{site.data.keyword.cloud_notm}} by using an API key that is associated with a service ID. |  
| User     | `iam-identity.user-apikey.login`         | An event is generated when a user logs in to the {{site.data.keyword.cloud_notm}} by using an API key. |  
| User     | `iam-identity.user-identitycookie.login` | This is an event that is generated when a user requests an identity cookie to run an action. |
| User     | `iam-identity.user-refreshtoken.login`   | This is an event that is generated when a user logs in to the IBM Cloud , or when an initiator that has already logged in to the {{site.data.keyword.cloud_notm}} requests a new refresh token to run an action. |
{: caption="Table 1. User login actions" caption-side="top"} 


[Learn more about analyzing IAM events](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-at_events_iam#at_events_iam_analyze).

