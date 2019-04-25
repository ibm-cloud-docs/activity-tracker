---

copyright:
  years: 2019
lastupdated: "2019-04-25"

keywords: IBM Cloud, LogDNA, Activity Tracker, services

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


# Cloud services
{: #cloud_services}

Use the {{site.data.keyword.at_full}} service to monitor user-initiated activities that change the state of any of the following services in the {{site.data.keyword.cloud_notm}}.
{:shortdesc}


## Platform core integrated services
{: #platform_core_integrated}

Core platform services generate events that you can view through the **us-south** {{site.data.keyword.at_full_notm}} web UI. To view these events, you must [provision an instance](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-provision#provision) of the {{site.data.keyword.at_full_notm}} service in the **US-South** region.
{: note}

The following table lists core platform services that send events to {{site.data.keyword.at_full_notm}}:

| Service     | Description | {{site.data.keyword.at_full_notm}} events |
|-------------|-------------|-------------------------------------------|
| [Managing an account](/docs/account?topic=account-accounts#accounts) | You can sign up for an {{site.data.keyword.IBM_notm}} account by using an existing IBMid, creating a new IBMid, or by using a federated ID. | [Events that are generated when you manage an account](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_acc_mgt#at_events_acc_mgt_account) |
| [Managing users](/docs/iam?topic=iam-iamuserinv#iamusermanage) | You can view and manage users across the account or organizations that you own or manage.  | [Events that are generated when you manage users ](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-at_events_acc_mgt#at_events_acc_mgt_users) |
| [Managing organizations](/docs/account?topic=account-orgsspacesusers#orgsspacesusers) | As an account owner, you can add and manage organizations to the account. | [Events that are generated when you manage organizations ](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_acc_mgt#at_events_acc_mgt_org) |
| [Provisioning and managing catalog services for resources that are managed by {{site.data.keyword.iamshort}} (IAM)](/docs/overview?topic=overview-ui#catalogcreate) | You can provision a service instance, rename a service instance, change the plan of a service instance, and remove a service instance. | [Events that are generated when you interact with catalog services ](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-at_events_rc#at_events_rc) | 
| [Working with service aliases](/docs/resources?topic=resources-connect_app#what_is_alias) | An alias is a connection between your IAM-managed service within a resource group and an application within an org or a space. | [Events for managing aliases that are associated to a service instance](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-at_events_rc#rc_alias) | 
| [Working with service credentials](/docs/resources?topic=resources-service_credentials#service_credentials) | A service credential provides the necessary information to connect an application to a service instance. | [Events for managing service credentials that are associated to a service instance](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-at_events_rc#rc_keys) | 
| [Binding a service instance to an app](/docs/resources?topic=resources-s2s_binding#s2s_binding) | You can generate a Cloud Foundry (CF) instance, or alias, of a service instance with the same name in a space.  | [Events for binding and unbinding a service instance to an app](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-at_events_rc#rc_bind) |
{: caption="List of core platform actions" caption-side="top"} 

You can generate a Cloud Foundry (CF) instance, or alias, of this service with the same name. 

## Platform integrated security services
{: #platform_integrated_security}

Integrated security services generate events that you can view through the **us-south** {{site.data.keyword.at_full_notm}} web UI. To view these events, you must [provision an instance](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-provision#provision) of the {{site.data.keyword.at_full_notm}} service in the **US-South** region.
{: note}

The following table lists core security platform services that send events to {{site.data.keyword.at_full_notm}}:

| Service     | Description | {{site.data.keyword.at_full_notm}} events |
|-------------|-------------|-------------|
| [Managing access groups](/docs/iam?topic=iam-groups#groups) | You can define access groups to organize a set of users and service IDs into a single entity that makes it easy for you to assign permissions. | [Events that are generated when you manage access groups](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-at_events_iam#at_events_iam_access) |
| [Managing policies](/docs/iam?topic=iam-userroles#userroles) | You can use IAM to manage users and roles across the {{site.data.keyword.cloud_notm}} Platform and Infrastructure services. | [Events that are generated when you manage IAM policies](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-at_events_iam#at_events_iam_policies) |
{: caption="List of core security platform services" caption-side="top"} 





## Platform security services
{: #security}

The following table lists security Cloud services that send events to {{site.data.keyword.cloudaccesstrailshort}}:


| Service     | Description | {{site.data.keyword.at_full_notm}} events          |
|-------------|-------------|----------------------------------------------------|
| [{{site.data.keyword.cloudcerts_full_notm}}](/docs/services/certificate-manager?topic=certificate-manager-about-certificate-manager#about-certificate-manager) | You can use {{site.data.keyword.cloudcerts_short}} to manage the SSL certificates for your {{site.data.keyword.cloud_notm}}-based apps and services.  | [Events that are generated by the {{site.data.keyword.cloudcerts_short}} service](/docs/services/certificate-manager?topic=certificate-manager-at_events#at_events) |
{: caption="List of security Cloud services that send events to {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 


