---

copyright:
  years: 2019
lastupdated: "2019-05-25"

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

Core platform services generate events that you can view through the **Frankfurt (eu-de)** {{site.data.keyword.at_full_notm}} web UI. To view these events, you must [provision an instance](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-provision#provision) of the {{site.data.keyword.at_full_notm}} service in the **Frankfurt (eu-de)** region.
{: note}

The following table lists core platform actions that send events to {{site.data.keyword.at_full_notm}} by the ***Reasource controller service**:

| Action                           | Description | {{site.data.keyword.at_full_notm}} events |
|----------------------------------|-------------|-------------------------------------------|
| [Managing an account](/docs/account?topic=account-accounts#accounts) | You can sign up for an {{site.data.keyword.IBM_notm}} account by using an existing IBMid, creating a new IBMid, or by using a federated ID. | [Events that are generated when you manage an account](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_acc_mgt#at_events_acc_mgt_account) |
| [Managing users](/docs/iam?topic=iam-iamuserinv#iamusermanage) | You can view and manage users across the account or organizations that you own or manage.  | [Events that are generated when you manage users ](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-at_events_acc_mgt#at_events_acc_mgt_users) |
| [Managing organizations](/docs/account?topic=account-orgsspacesusers#orgsspacesusers) | As an account owner, you can add and manage organizations to the account. | [Events that are generated when you manage organizations ](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_acc_mgt#at_events_acc_mgt_org) |
| [Provisioning and managing catalog {{site.data.keyword.iamshort}} (IAM) enabled services](/docs/overview?topic=overview-ui#catalogcreate) | You can provision a service instance, rename a service instance, change the plan of a service instance, and remove a service instance. | [Events that are generated when you interact with catalog services ](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-at_events_rc#at_events_rc) | 
| [Working with service aliases](/docs/resources?topic=resources-connect_app#what_is_alias) | An alias is a connection between your IAM-managed service within a resource group and an application within an org or a space. | [Events for managing aliases that are associated to a service instance](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-at_events_rc#rc_alias) | 
| [Working with service credentials](/docs/resources?topic=resources-service_credentials#service_credentials) | A service credential provides the necessary information to connect an application to a service instance. | [Events for managing service credentials that are associated to a service instance](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-at_events_rc#rc_keys) | 
| [Binding a service instance to an app](/docs/resources?topic=resources-s2s_binding#s2s_binding) | You can generate a Cloud Foundry (CF) instance, or alias, of a service instance with the same name in a space.  | [Events for binding and unbinding a service instance to an app](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-at_events_rc#rc_bind) |
{: caption="List of core platform actions" caption-side="top"} 



## Platform integrated security services
{: #platform_integrated_security}

Integrated security services generate events that you can view through the **Frankfurt (eu-de)** {{site.data.keyword.at_full_notm}} web UI. To view these events, you must [provision an instance](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-provision#provision) of the {{site.data.keyword.at_full_notm}} service in the **Frankfurt (eu-de)** region.
{: note}

The following table lists core security platform actions that send events to {{site.data.keyword.at_full_notm}}:

| Service               | Actions                                                     | Description | {{site.data.keyword.at_full_notm}} events |
|-----------------------|-------------------------------------------------------------|-------------|-------------|
| `IAM Access Groups`     | [Managing access groups](/docs/iam?topic=iam-groups#groups) | You can define access groups to organize a set of users and service IDs into a single entity that makes it easy for you to assign permissions. | [Events that are generated when you manage access groups](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-at_events_iam#at_events_iam_access) |
| `IAM Access management` | [Managing policies](/docs/iam?topic=iam-userroles#userroles) | You can use IAM to manage users and roles across the {{site.data.keyword.cloud_notm}} Platform and Infrastructure services. | [Events that are generated when you manage IAM policies](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-at_events_iam#at_events_iam_policies) |
| `IAM Identity service`  | [Log in to the {{site.data.keyword.cloud_notm}}](/docs/iam?topic=iam-iamoverview#iamoverview)| You can log into the {{site.data.keyword.cloud_notm}} by using a password, an API key, an authorization code, or a passcode. As a federated user, you can log in from the command-line interface (CLI) by using either a one-time passcode or an API key. | [Events that are generated when a user or app logs in to the {{site.data.keyword.cloud_notm}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-at_events_iam#at_events_iam_login) |
| `IAM Identity service`  | [Managing platform API keys](/docs/iam?topic=iam-manapikey#platform-api-keys) | You can define platform API keys in the {{site.data.keyword.IBM_notm}} Cloud that are associated with a user or a service ID. | [Events that are generated when you manage Platform API keys](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-at_events_iam#at_events_iam_apikeys) |
| `IAM Identity service`  | [Managing service IDs](/docs/iam?topic=iam-serviceids#serviceids) | You can define service IDs at the account level in the {{site.data.keyword.IBM_notm}} Cloud. | [Events that are generated when you manage service IDs](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-at_events_iam#at_events_iam_serviceids) |
{: caption="List of core security platform services" caption-side="top"} 



## Platform integration services
{: #integration}

The following table lists integration services that send events to {{site.data.keyword.cloudaccesstrailshort}}:

| Service     | Description | {{site.data.keyword.cloudaccesstrailshort}} events |
|-------------|-------------|-------------|
| [{{site.data.keyword.messagehub}}](/docs/services/EventStreams?topic=eventstreams-about#about)| {{site.data.keyword.messagehub}} is a high-throughput message bus that is built with Apache Kafka. It is optimized for event ingestion into {{site.data.keyword.IBM_notm}} and event stream distribution between your services and applications. | [Events that are generated by {{site.data.keyword.messagehub}} ](/docs/services/EventStreams?topic=eventstreams-at_events#at_events) |  
{: caption="List of integration Cloud services that send events to {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 



## Platform network services
{: #network}

The following table lists network services that send events to {{site.data.keyword.at_full_notm}}:

| Service     | Description | {{site.data.keyword.at_full_notm}} events |
|-------------|-------------|-------------|
| [IBM Cloud Internet Services (CIS)](/docs/infrastructure/cis?topic=cis-about-ibm-cloud-internet-services-cis#about-ibm-cloud-internet-services-cis)| IBM Cloud Internet Services (CIS) provides a fast, highly performant, reliable, and secure internet service. | [Events that are generated by IBM Cloud Internet Services](/docs/infrastructure/cis?topic=cis-at_events#at_events) |  
{: caption="List of network services" caption-side="top"} 



## Platform security services
{: #security}

The following table lists security Cloud services that send events to {{site.data.keyword.cloudaccesstrailshort}}:


| Service     | Description | {{site.data.keyword.at_full_notm}} events          |
|-------------|-------------|----------------------------------------------------|
| [{{site.data.keyword.cloudcerts_full_notm}}](/docs/services/certificate-manager?topic=certificate-manager-about-certificate-manager#about-certificate-manager) | You can use {{site.data.keyword.cloudcerts_short}} to manage the SSL certificates for your {{site.data.keyword.cloud_notm}}-based apps and services.  | [Events that are generated by the {{site.data.keyword.cloudcerts_short}} service](/docs/services/certificate-manager?topic=certificate-manager-at_events#at_events) |
{: caption="List of security Cloud services that send events to {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 


