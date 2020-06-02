---

copyright:
  years: 2019, 2020
lastupdated: "2020-05-20"

keywords: IBM Cloud, LogDNA, Activity Tracker, account events, catalog, tags

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

# Account management events  
{: #at_events_acc_mgt}

As a security officer, auditor, or manager, you can use the {{site.data.keyword.at_full_notm}} service to track how users and applications interact with an {{site.data.keyword.cloud}} account. 
{:shortdesc}

The {{site.data.keyword.at_full_notm}} service records user-initiated activities that change the state of a service in {{site.data.keyword.cloud_notm}}. To get started, see [{{site.data.keyword.at_full_notm}}](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-getting-started#getting-started). 



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

The following tables list the actions that generate an event:

### Events for managing catalogs
{: #at_events_catalog_1}

| Action                                           | Description                                                           | 
|--------------------------------------------------|-----------------------------------------------------------------------|
| `globalcatalog-collection.instance.read`           | An event is generated when you view a catalog.            | 
| `globalcatalog-collection.instance.update`         | An event is generated when you update a catalog.          |
| `globalcatalog-collection.instances.list`           | An event is generated when you get a list of the catalogs in an account.           | 
{: caption="Table 2. Actions that generate catalog management events" caption-side="top"}

### Events for managing products in a catalog
{: #at_events_catalog_2}

| Action                                           | Description                                                           | 
|--------------------------------------------------|-----------------------------------------------------------------------|
| `globalcatalog-collection.offerings.list`         |  An event is generated when you get a list of the products in a catalog.          |
| `globalcatalog-collection.offering.read`           | An event is generated when you view a product in a catalog.            |
| `globalcatalog-collection.offering.create`         | An event is generated when you create a product.          |
| `globalcatalog-collection.offering.update`         | An event is generated when you update a product.          |
| `globalcatalog-collection.offering.delete`         | An event is generated when you delete a product.          |
{: caption="Table 3. Actions that generate product catalog management events" caption-side="top"}

### Events for managing account settings that are related to catalogs
{: #at_events_catalog_3}

| Action                                           | Description                                                           | 
|--------------------------------------------------|-----------------------------------------------------------------------|
| `globalcatalog-collection.account-settings.read`   | An event is generated when you view the account settings.   | 
| `globalcatalog-collection.account-settings.update` | An event is generated when you update the account settings. |
{: caption="Table 4. Actions that generate account settings management events" caption-side="top"}

### Events for managing enterprise account settings that are related to catalogs
{: #at_events_catalog_4}

| Action                                           | Description                                                           | 
|--------------------------------------------------|-----------------------------------------------------------------------|
| `globalcatalog-collection.enterprise-settings.read` | An event is generated when you view the enterprise settings. |
| `globalcatalog-collection.enterprise-settings.update` | An event is generated when you update the enterprise settings. |
| `globalcatalog-collection.enterprise-settings.list` | An event is generated when you get a list of the enterprises in an account and their corresponding settings. | 
{: caption="Table 5. Actions that generate enterprise account settings management events" caption-side="top"}

### Events for managing license and entitlement events
{: #at_events_catalog_entitlement}

The following table lists the actions that generate an event:

| Action                                 | Description |
|----------------------------------------|---------|
| `entitlement.entitlement.create`       | An event is generated when an initiator binds a license to an account. |  
| `entitlement.entitlement.delete`       | An event is generated when an initiator deletes an entitlement. |  
| `entitlement.entitlement.delete_purge` | An event is generated when an initiator purges an entitlement. |
| `entitlement.entitlement.update`       | An event is generated when an initiator updates an entitlement. |
| `entitlement.entitlement.check`        | An event is generated when an initiator uses an entitlement to pull an image from the governed IBM Container Registry. |
| `entitlement.entitlement.invalidate`   | An event is generated when an entitlement's license is not valid anymore. |
{: caption="Table 6. User entitlement actions" caption-side="top"}

## Events for managing organizations
{: #at_events_acc_mgt_org}

The following table lists the actions that generate an event:

| Action                               | Description |
|--------------------------------------|-------------|
| `billing.account.org.create`         | An event is generated when you add an organization to the account. |
{: caption="Table 7. Actions that generate events" caption-side="top"} 


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
{: caption="Table 8. Actions that generate events" caption-side="top"} 


## Events for managing users
{: #at_events_acc_mgt_users}

The following table lists the actions that generate an event:

| Action                               | Description |
|--------------------------------------|-------------|
| `user-management.user.create`        | An event is generated when you send an invitation to a user to join an account. |
| `user-management.user.active`        | An event is generated when you activate the user in the account. When the user verifies the email address, the event is generated. |
| `user-management.user.delete`        | An event is generated when you remove a user from the account. |
| `user-management.user-setting.update` | An event is generated when you update the user's login configuration settings: User one-time passcode authentication, Require MFA security questions at login, User-managed login or Setting up security questions |
{: caption="Table 9. Actions that generate events" caption-side="top"} 


## Where to look for the events
{: #at_events_acc_mgt_ui}

Events are available in the **Frankfurt (eu-de)** region. 

To view these events, you must [provision an instance](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-provision#provision) of the {{site.data.keyword.at_full_notm}} service in the **Frankfurt (eu-de)** region. Then, you must [open the {{site.data.keyword.at_full_notm}} UI](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-launch#launch_step2). 


## Analyzing events
{: #at_events_analyze}

### Catalog events
{: #at_events_analyze_1}

You can find the value `unavailable` in catalog events. This value indicates when an update is made, but specific details about the update aren't included. 
{: important}


