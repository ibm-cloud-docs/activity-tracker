---

copyright:
  years: 2019
lastupdated: "2019-08-05"

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


# Managing log in actions in an account
{: #tutorial_iam_login}

As a security officer, auditor, or manager, you can use the {{site.data.keyword.at_full_notm}} service to track how users, applications, and services interact with your account. The {{site.data.keyword.iamlong}} (IAM) service in {{site.data.keyword.cloud_notm}} generates events that you can use to monitor log in activity to your account. This tutorial explains the different log in options to {{site.data.keyword.cloud_notm}} and what happens from an IAM and an {{site.data.keyword.at_full_notm}} perspective. You can also find out how to define views and dashboards to monitor these actions in your account.
{:shortdesc}

To work in the {{site.data.keyword.cloud_notm}}, a user, an application, or a service must log in to {{site.data.keyword.cloud_notm}}. The user, application, or service needs valid credentials to access an account and run actions on services in that account.

As a user, you can log in to the {{site.data.keyword.cloud_notm}} in any of the following ways:
* Log in through the {{site.data.keyword.cloud_notm}} UI
* Log in from the command-line interface (CLI) by using an API key
* Log in from the command-line interface (CLI) by using a one-time passcode
* Log in from the command-line interface (CLI) by using a user ID and password

As a service, you log in to the {{site.data.keyword.cloud_notm}} by using an API key that is associated to a service ID.

When a user registers in {{site.data.keyword.cloud_notm}}, the user requests an IBMid. An account is created and associated to the user's IBMid by default. 

A user that has an IBMid can be invited to be a member in other accounts in {{site.data.keyword.cloud_notm}}. When a user is invited to work in your account, an event with action **user-management.user.create** is generated and available in your account. You can monitor these events through the {{site.data.keyword.at_full_notm}} instance in Frankfurt.

For a user to log in successfully to your account, consider the following information:
1. First, the credentials of the user or service are validated in {{site.data.keyword.cloud_notm}}.
2. If the credentials are validated and the user or service is authorized to work in the {{site.data.keyword.cloud_notm}}, a token is issued by the IAM Identity service.

    Depending on the way that the user logs in where an account might be pre-selected, the account might be embedded in the API key, or the user might have to select one account after the credentials are validated, the token might include account details or not. 

3. [User log in request only] If account information is not included, the user must select or switch account. 

An Activity Tracker event is generated and available in your account after the credentials are validated in the {{site.data.keyword.cloud_notm}}, and account details are available.

As owner or person responsible of the account access management, you can expect an event in your account in any of the following scenarios:
* User logs in from the UI: You get a log in event after the user's log in credentials (IBMid) are validated in {{site.data.keyword.cloud_notm}} and the user switches to work with your account.
* User logs in from the CLI by using a user ID and password or a one-time passcode: You get a log in event after the user's log in credentials (IBMid) are validated in {{site.data.keyword.cloud_notm}} and the user selects your account.
* User logs in from the CLI by using an API key: You get a log in event after the user's log in credentials (IBMid) are validated in {{site.data.keyword.cloud_notm}}. The account details are included in the key.
* Service logs in by using a service ID: You get a log in event after the credentials (API key of a service ID) are validated in {{site.data.keyword.cloud_notm}}. The account details are included in the API key.


**You only get Activity Tracker events for successful log in requests to your account.**
{: important}



## Log in through the {{site.data.keyword.cloud_notm}} UI
{: #tutorial_iam_login_ui}


For a user to log in successfully to your account through the {{site.data.keyword.cloud_notm}} UI, consider the following information:

1. To initiate the log in requets, the user must launch the [{{site.data.keyword.cloud_notm}} UI ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/login){:new_window}.

2. After the user enters the IBMid credentials into the browser, the data is forwarded to the IAM Identity Service.

3. If the credentials are validated and the user is authenticated to work in the pre-selected account, the IAM Identity Service returns an access token and a refresh token. These tokens are bounded to the default account and include information to allow the user to choose other accounts where the user is a member. 

    By default, an account is pre-selected. This account is the one that is associated to the IBMid of the user. 

4. At this point in the process, the IAM Identity Service generates an Activity Tracker event with action **iam-identity.user-refreshtoken.login**. This event is available in the user's default account.

5. Next, the user switches account and selects a different account.

6. The IAM Identity Service checks the current tokens. If the user is authorized to work in the new account, the IAM Identity Service returns a new access token and a new refresh token that are bound to the new account.

7. At this point in the process, the IAM Identity Service generates an Activity Tracker event with action **iam-identity.user-refreshtoken.login**. This event is available in the new account.



## Run an action in the {{site.data.keyword.cloud_notm}} UI
{: #tutorial_iam_action_ui}

When a user runs an action in the {{site.data.keyword.cloud_notm}} UI, you might get one or more login events:

* If the access and refresh tokens are expired, the user needs to log in through the {{site.data.keyword.cloud_notm}} UI. An Activity Tracker event with action **iam-identity.user-refreshtoken.login** is generated.

8. Optional] User runs an action

9. Cookie is generated.

10. Activity Tracker event is generated in the account selected. by the user iam-identity.user-identitycookie.login


An account is preselected by the UI during login. When the dashboard shows up you are logged in to an account. You have a dropdown to switch accounts which would generate additional refreshtoken events if you switch to a different account

When you do a console login, the console ( 1 of the many microservices) gets the access and refresh token. As the console consists of multiple microservices (>20) not each microservice will do a complete login flow. Therefore an IdentityCookie is pass around and if one of the console microservices wants to do a rest call which requires a token they will exchange the identityCookie into a token (access/refresh). The exchange is much faster than a complete login flow and the identityCookie is much smaller than a IAM token. During this exchange the microservices can decide what kind of tokens they require. e.g. IAM token softlayer token, ... depending what kind of rest interfaces they have to call to full fill their work




### Log in from the CLI by using an API key
{: #tutorial_iam_login_cli_key}

Log in with IBMid through the CLI 
ibmcloud login –a cloud.ibm.com –apikey xxxx

1. User logs in with API key.
The API key includes account information

Validate credential in IBM Cloud
(Authenticate user in the IBM Cloud and authorize access to account)

Activity Tracker event is generated iam-identity.user-apikey.login


### Log in from the CLI by using a one-time passcode.
{: #tutorial_iam_login_cli_passcode}

Log in with IBMid through the CLI 
ibmcloud login –a cloud.ibm.com –sso


1. User logs in by providing a passcode. 

Validate IBMid in IBM Cloud
(Authenticate user in the IBM Cloud)
NO account is selected


2. Token is returned. 
The token has the information to allow the user to choose an account where he is a member or owner.

3. User selects an account

4. Access token and refresh token bound to the selected account are returned. 

5. Activity Tracker event is generated iam-identity.user-refreshtoken.login

The token does not contain any credentials. It contains an identity, account and some rights. The combination of the token together with the definitions in pep/pem provide the access rights a person has for a specific rest or service call



### Log in from the CLI by using a user ID and password
{: #tutorial_iam_login_cli_pwd}

Log in with IBMid through the CLI 
ibmcloud login –a cloud.ibm.com –u USER –p password

1. User logs in with IBMid credentials. The user provides credentials.

2. Token is returned without account information. This token has the credentials to allow the user do account selection

3. User selects an account

4. Access token and refresh token bound to the selected account are returned

5. Activity Tracker event is generated iam-identity.user-refreshtoken.login



## Summary
{: #tutorial_iam_login_summ}

The following table shows the IAM event that is generated in each of the log in cases:

| Type     | sAction                                   | Description |
|----------|------------------------------------------|-----------------------------|
| Service  | `iam-identity.serviceid-apikey.login`    | An event is generated when an initiator logs in to the {{site.data.keyword.cloud_notm}} by using an API key that is associated with a service ID. |  
| User     | `iam-identity.user-apikey.login`         | An event is generated when a user logs in to the {{site.data.keyword.cloud_notm}} by using an API key. |  
| User     | `iam-identity.user-identitycookie.login` | This is an event that is generated when an initiator requests an identity cookie to run an action. |
| User     | `iam-identity.user-refreshtoken.login`   | This is an event that is generated when the initiator logs in to the IBM Cloud , or when an initiator that has already logged in to the IBM Cloud requests a new refresh token to run an action. |
{: caption="Table 1. User login actions" caption-side="top"} 




