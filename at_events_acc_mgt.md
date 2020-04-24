---

copyright:
  years: 2019, 2020
lastupdated: "2020-04-01"

keywords: IBM Cloud, LogDNA, Activity Tracker, account events, catalog, tags

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

As a security officer, auditor, or manager, you can use the {{site.data.keyword.at_full_notm}} service to track how users and applications interact with an {{site.data.keyword.cloud}} account. 
{:shortdesc}

The {{site.data.keyword.at_full_notm}} service records user-initiated activities that change the state of a service in {{site.data.keyword.cloud_notm}}. To get started, see [{{site.data.keyword.at_full_notm}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started). 



## Events for managing accounts
{: #at_events_acc_mgt_account}

The following table lists the actions that generate an event:

| Action                               | Description |
|--------------------------------------|-------------|
| `billing.account.create`             | An event is generated when you create an account after the account ID is assigned to the account. |
| `billing.account.update`             | An event is generated when you update information about the account.  |
| `billing.account.active`             | An event is generated when you verify the account, that is, an event is generated when the account becomes active. |
| `billing.account.subscription.create` | An event is generated when you create a <a href="/docs/account?topic=account-accounts#subscription-account">Subscription account</a>. |
{: caption="Table 1. Actions that generate account management events" caption-side="top"} 

## Events for managing catalogs
{: #at_events_catalog_management}

The following table lists the actions that generate an event:

| Action                                           | Description                                                           | 
|--------------------------------------------------|-----------------------------------------------------------------------|
| globalcatalog-collection.instance.update         | An event is generated when you update a catalog.          |
| globalcatalog-collection.instance.read           | An event is generated when you view a catalog.            | 
| globalcatalog-collection.instances.list           | An event is generated when you get a list of the catalogs in an account.           | 
| globalcatalog-collection.offerings.list         |  An event is generated when you get a list of the products in a catalog.          |
| globalcatalog-collection.offering.create         | An event is generated when you create a product.          |
| globalcatalog-collection.offering.update         | An event is generated when you update a product.          |
| globalcatalog-collection.offering.delete         | An event is generated when you delete a product.          |
| globalcatalog-collection.offering.read           | An event is generated when you view a product in a catalog.            |
| globalcatalog-collection.account-settings.update | An event is generated when you update the account settings. |
| globalcatalog-collection.account-settings.read   | An event is generated when you view the account settings.   | 
{: caption="Table 2. Actions that generate catalog management events" caption-side="top"}

`unavailable` indicates when an update is made, but specific details about the update aren't included. 
{: important}

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
| `global-search-tagging.tag.attach`              | An event is generated when you associate a tag to a resource. |
| `global-search-tagging.tag.detach`              | An event is generated when you remove a tag from a resource.  |
| `global-search-tagging.tag.update`              | An event is generated when you update a tag that is attached to a resource.  |
| `global-search-tagging.tag.delete`              | An event is generated when you delete a tag in your account.  |
| `global-search-tagging.tags.delete`             | An event is generated when you delete all the tags that are not attached to resources in your account.  |
{: caption="Table 4. Actions that generate events" caption-side="top"} 


## Events for managing users
{: #at_events_acc_mgt_users}

The following table lists the actions that generate an event:

| Action                               | Description |
|--------------------------------------|-------------|
| `user-management.user.create`        | An event is generated when you send an invitation to a user to join an account. |
| `user-management.user.active`        | An event is generated when you activate the user in the account. When the user verifies the email address, the event is generated. |
| `user-management.user.delete`        | An event is generated when you remove a user from the account. |
| `user-management.user-setting.update` | An event is generated when you update the user's login configuration settings: User one-time passcode authentication, Require MFA security questions at login, User-managed login or Setting up security questions |
{: caption="Table 5. Actions that generate events" caption-side="top"} 


## Where to look for the events
{: #at_events_acc_mgt_ui}

Events are available in the **Frankfurt (eu-de)** region. 

To view these events, you must [provision an instance](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-provision#provision) of the {{site.data.keyword.at_full_notm}} service in the **Frankfurt (eu-de)** region. Then, you must [open the {{site.data.keyword.at_full_notm}} UI](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-launch#launch_step2). 





