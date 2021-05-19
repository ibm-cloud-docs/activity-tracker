---

copyright:
  years: 2019, 2021
lastupdated: "2021-04-06"

keywords: IBM Cloud, Activity Tracker, services

subcollection: activity-tracker


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
{:external: target="_blank" .external}



# Cloud services
{: #cloud_services}

Use the {{site.data.keyword.at_full}} service to monitor user-initiated activities that change the state of any of the following services in the {{site.data.keyword.cloud_notm}}.
{:shortdesc}

## Analytics services
{: #analytics}

The following table lists analytics services that send events to {{site.data.keyword.at_short}}:

| Service     | Description | Events      |
|-------------|-------------|-------------|
| [{{site.data.keyword.iae_full}}](/docs/AnalyticsEngine?topic=AnalyticsEngine-getting-started) | You can use the {{site.data.keyword.iae_full_notm}} service to develop and deploy analytics applications in Apache Hadoop and Apache Spark. | [Events](/docs/AnalyticsEngine?topic=AnalyticsEngine-at_events) |
| [{{site.data.keyword.sqlquery_full}}](/docs/sql-query?topic=sql-query-overview#overview) | You can use the {{site.data.keyword.sqlquery_short}} service to run SQL queries (that is, SELECT statements) to analyze, transform, or clean up rectangular data. | [Events](/docs/sql-query?topic=sql-query-activitytracker#activitytracker) |
{: caption="Table 1. List of analytics services" caption-side="top"}


## VMware solution services
{: #vmware_solutions}

With {{site.data.keyword.vmwaresolutions_full_notm}}, you can quickly and seamlessly integrate or migrate your on-premises VMware workloads to the {{site.data.keyword.cloud_notm}} by using the scalable, secure, and high-performance {{site.data.keyword.cloud_notm}} infrastructure and the industry-leading VMware hybrid virtualization technology. You can easily deploy your VMware virtual environments and manage the infrastructure resources on {{site.data.keyword.cloud_notm}}. At the same time, you can still use your familiar native VMware product console to manage the VMware workloads. [Learn more](https://www.ibm.com/cloud/vmware){: external}.

The following table lists VMware solution services that send events to {{site.data.keyword.at_full_notm}}:

| Service     | Description | Events    |
|-------------|-------------|-----------|
| {{site.data.keyword.vmwaresolutions_short}}   | Use {{site.data.keyword.vmwaresolutions_short}} to track how users and applications interact with Virtual Data Centers. | [Events](/docs/vmwaresolutions?topic=vmwaresolutions-at-events#at-events) |
| vCenter Server      | Use vCenter Server to manage user accounts, instances, clusters, and services in {{site.data.keyword.vmwaresolutions_short}}. | [Events](/docs/vmwaresolutions?topic=vmwaresolutions-at-events#at-events-instance-mgmt) |
| KMIP for VMware | KMIP for VMware works together with VMware native vSphere encryption and vSAN encryption to provide simplified storage encryption management together with the security and flexibility of {{site.data.keyword.keymanagementservicelong_notm}} or {{site.data.keyword.hscrypto}} customer-managed keys. | [Events](/docs/vmwaresolutions?topic=vmwaresolutions-at-events#at-events-kmip) |
{: caption="Table 2. List of VMware solution services" caption-side="top"}




## Infrastructure services
{: #infrastructure}

The following table lists infrastructure services that send events to {{site.data.keyword.cloudaccesstrailshort}}:

| Service     | Description | Events |
|-------------|-------------|-------------------|
| [{{site.data.keyword.BluVirtServers_full}} ](/docs/virtual-servers?topic=virtual-servers-about-virtual-servers#about-virtual-servers)| {{site.data.keyword.BluVirtServers}} are scalable virtual servers that are purchased with dedicated cores and memory allocations. They are a great option if you are looking for compute resources, that can be added in minutes, with access to features like image templates.  | [Events}](/docs/virtual-servers?topic=virtual-servers-at_events#at_events) |
| [{{site.data.keyword.baremetal_long}} ](/docs/bare-metal?topic=bare-metal-about-bm#about-bm) | {{site.data.keyword.baremetal_short}} are single-tenant physical servers that provide you performance and control with low-level access to the hardware resources. | [Events](/docs/bare-metal?topic=bare-metal-bm-at-events#bm-at-events) |
{: caption="Table 3. List of infrastructure services" caption-side="top"}


## Compute serverless services
{: #serverless}

The following table lists serverless compute services that send events to {{site.data.keyword.at_short}}:

| Service     | Description | Events |
|-------------|-------------|-------------------|
| [{{site.data.keyword.openwhisk}}](/docs/openwhisk?topic=openwhisk-getting-started) | {{site.data.keyword.openwhisk_short}} is a polyglot Functions-as-a-Service (FaaS) programming platform based on Apache OpenWhisk that you can use to write lightweight code called `actions`. | [Events](/docs/openwhisk?topic=openwhisk-at_events) |
| [{{site.data.keyword.codeenginefull}}](/docs/codeengine?topic=codeengine-getting-started)| Code Engine is a fully managed, serverless platform that runs your containerized workloads, including web apps, micro-services, event-driven functions, or batch jobs  | [Events](/docs/codeengine?topic=codeengine-at_events) |
{: caption="Table 4. List of serverless compute services" caption-side="top"}



## Cloud Foundry applications
{: #platform_cfapps}

The events that are sent by Cloud Foundry applications to {{site.data.keyword.cloudaccesstrailshort}} are listed in the response area of the `GET /v2/events`, under the body section. The *Type* field lists all actions that generate an event. For more information, see the [Events API](https://apidocs.cloudfoundry.org/270/events/list_all_events.html){: external}.



## Container services
{: #container}

The following table lists container platform services that send events to {{site.data.keyword.at_full_notm}}:

| Service     | Description | Events |
|-------------|-------------|-------------------|
| [{{site.data.keyword.registrylong}}](/docs/Registry?topic=Registry-getting-started) | You can use the {{site.data.keyword.registrylong_notm}} service to store and access private images in a highly available and scalable architecture. | [Events](/docs/Registry?topic=Registry-at_events) |
| [{{site.data.keyword.containerlong}}](/docs/containers?topic=containers-getting-started) | You can use the {{site.data.keyword.containerlong_notm}} service to deploy highly available apps in Docker containers that run in Kubernetes clusters. | [Events](/docs/containers?topic=containers-at_events) |
| [{{site.data.keyword.openshiftlong}}](/docs/openshift?topic=openshift-getting-started) | With {{site.data.keyword.openshiftlong}}, you can deploy apps on highly available clusters that come installed with the [Red Hat OpenShift on IBM Cloud Container Platform](https://docs.openshift.com/container-platform/4.2/welcome/index.html){: external} software installed on Red Hat Enterprise Linux. | [Events](/docs/openshift?topic=openshift-at_events) |
| [{{site.data.keyword.satellitelong}}](/docs/satellite?topic=satellite-getting-started) | With {{site.data.keyword.satellitelong_notm}}, you can bring your own compute infrastructure to run {{site.data.keyword.cloud_notm}} services and consistently deploy, manage, and control your app workloads. | [Events](/docs/satellite?topic=satellite-at_events) |
{: caption="Table 5. Container events" caption-side="top"}



## Logging and monitoring services
{: observability}

The following table lists observability services that send events to {{site.data.keyword.at_short}}:

| Service     | Service name | Description | Events |
|-------------|-------------|-------------|-------------------|
| [{{site.data.keyword.at_full}}](/docs/activity-tracker?topic=activity-tracker-getting-started) | `logdnaat` | {{site.data.keyword.at_full_notm}} monitors the activity of your {{site.data.keyword.cloud_notm}} account. | [Events](/docs/activity-tracker?topic=activity-tracker-at_events) |
| [{{site.data.keyword.la_full}}](/docs/log-analysis?topic=log-analysis-getting-started#getting-started) | `logdna` | {{site.data.keyword.la_full_notm}} adds log management capabilities to your {{site.data.keyword.cloud_notm}} architecture. | [Events](/docs/log-analysis?topic=log-analysis-at_events) |
| [{{site.data.keyword.mon_full}}](/docs/monitoring?topic=monitoring-getting-started) | `sysdig-monitor` | You can use the {{site.data.keyword.mon_full_notm}} service to gain operational visibility into the performance and health of your applications, services, and platforms. | [Events](/docs/monitoring?topic=monitoring-at_events) |
{: caption="Table 6. List of observability services" caption-side="top"} 



## Database services
{: #database}

The following table lists database services that send events to {{site.data.keyword.at_short}}:

| Service     | Description | Events |
|-------------|-------------|-------------------|
| [{{site.data.keyword.cloudantfull}}](/docs/Cloudant?topic=Cloudant-getting-started-with-cloudant)    | {{site.data.keyword.cloudant_short_notm}} is a document-oriented database as a service (DBaaS) It stores data as documents in JSON format. | [Events](/docs/Cloudant?topic=Cloudant-at_events) |
| [{{site.data.keyword.databases-for-mongodb_full}}](/docs/databases-for-mongodb?topic=databases-for-mongodb-getting-started) | MongoDB, a leading NoSQL database, is an open source document data store. | [Events](/docs/databases-for-mongodb?topic=cloud-databases-activity-tracker) |
| [{{site.data.keyword.databases-for-enterprisedb_full}}](/docs/databases-for-enterprisedb?topic=databases-for-enterprisedb-getting-started) | {{site.data.keyword.databases-for-enterprisedb}} is a database engine that optimizes the built-in features of PostgreSQL. | [Events](/docs/databases-for-enterprisedb?topic=cloud-databases-activity-tracker) |
| [{{site.data.keyword.databases-for-cassandra_full}}](/docs/databases-for-cassandra?topic=databases-for-cassandra-getting-started) | {{site.data.keyword.databases-for-cassandra_full}} is a scale-out NoSQL database that is built on Apache Cassandra. It’s designed to power real-time applications with high availability and massive scalability. | [Events](/docs/databases-for-cassandra?topic=cloud-databases-activity-tracker) |
| [{{site.data.keyword.databases-for-postgresql_full_notm}}](/docs/databases-for-postgresql?topic=databases-for-postgresql-getting-started) | {{site.data.keyword.databases-for-postgresql_full_notm}} is a managed PostgreSQL service that is hosted in the {{site.data.keyword.cloud_notm}} and integrated with other {{site.data.keyword.cloud_notm}} services. | [Events](/docs/databases-for-postgresql?topic=cloud-databases-activity-tracker) |
| [{{site.data.keyword.databases-for-redis_full_notm}}](/docs/databases-for-redis?topic=databases-for-redis-getting-started) | {{site.data.keyword.databases-for-redis_full_notm}} is a managed service that is hosted in the {{site.data.keyword.cloud_notm}} and integrated with other {{site.data.keyword.cloud_notm}} services.  | [Events](/docs/databases-for-redis?topic=cloud-databases-activity-tracker) |
| [{{site.data.keyword.databases-for-etcd_full_notm}}](/docs/databases-for-etcd?topic=databases-for-etcd-getting-started) | {{site.data.keyword.databases-for-etcd_full_notm}} is a managed etcd service that is hosted in the {{site.data.keyword.cloud_notm}} and integrated with other {{site.data.keyword.cloud_notm}} services. | [Events](/docs/databases-for-etcd?topic=cloud-databases-activity-tracker) |
| [{{site.data.keyword.databases-for-elasticsearch_full_notm}}](/docs/databases-for-elasticsearch?topic=databases-for-elasticsearch-getting-started) | {{site.data.keyword.databases-for-elasticsearch_full_notm}} is a managed Elasticsearch service that is hosted in the {{site.data.keyword.cloud_notm}} and integrated with other {{site.data.keyword.cloud_notm}} services. | [Events](/docs/databases-for-elasticsearch?topic=cloud-databases-activity-tracker) |
| [{{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_mongodb_full}}](/docs/hyper-protect-dbaas-for-mongodb?topic=hyper-protect-dbaas-for-mongodb-gettingstarted) | {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_mongodb_full}} is a managed highly secure MongoDB service that is hosted in the {{site.data.keyword.cloud_notm}} and integrated with other {{site.data.keyword.cloud_notm}} services. | [Events](/docs/hyper-protect-dbaas-for-mongodb?topic=hyper-protect-dbaas-for-mongodb-activity-tracker-events) |
| [{{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-gettingstarted) | {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} is a managed highly secure MongoDB service that is hosted in the {{site.data.keyword.cloud_notm}} and integrated with other {{site.data.keyword.cloud_notm}} services. | [Events](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-activity-tracker-events) |
| [{{site.data.keyword.messages-for-rabbitmq_full}}](/docs/messages-for-rabbitmq?topic=messages-for-rabbitmq-getting-started)  | {{site.data.keyword.messages-for-rabbitmq_full_notm}} is a managed RabbitMQ service that is hosted in the {{site.data.keyword.cloud_notm}} and integrated with other {{site.data.keyword.cloud_notm}} services.   | [Events](/docs/messages-for-rabbitmq?topic=cloud-databases-activity-tracker) |
| [{{site.data.keyword.Db2_on_Cloud_long}}](/docs/Db2onCloud?topic=Db2onCloud-about) | {{site.data.keyword.Db2_on_Cloud_long}} is a relational database that delivers fast query processing with enterprise-level performance and capabilities for online transactional processing (OLTP) | [Events](/docs/Db2onCloud?topic=Db2onCloud-activity-tracker) |
{: caption="Table 7. List of database services" caption-side="top"}



## Developer tools
{: #devops}

The following table lists developer tools and DevOps services that send events to {{site.data.keyword.at_short}}:

| Service     | Description | Events |
|-------------|-------------|-------------------|
| [{{site.data.keyword.apigw_full}}](/docs/api-gateway?topic=api-gateway-getting-started) | You can use {{site.data.keyword.apigw_short}} to manage APIs natively in {{site.data.keyword.cloud_notm}}. | [Events](/docs/api-gateway?topic=api-gateway-at_events) |
| [{{site.data.keyword.cloud-shell_full}}](/docs/cloud-shell?topic=cloud-shell-getting-started) | {{site.data.keyword.cloud-shell_notm}} is a cloud-based shell workspace that you can access through your browser. It's preconfigured with the full {{site.data.keyword.cloud_notm}} CLI and plug-ins and tools that you can use to manage apps, resources, and infrastructure. | [Events](/docs/cloud-shell?topic=cloud-shell-at_events) |
| [{{site.data.keyword.contdelivery_full}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-getting-started) | With {{site.data.keyword.contdelivery_short}}, you can build, test, and deliver applications by using DevOps practices and industry-leading tools. | [Events](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-at-events) |
| [{{site.data.keyword.mobilepushfull}}](/docs/mobilepush?topic=mobilepush-getting-started)| You can use the {{site.data.keyword.mobilepushshort}} service to send notifications to mobile devices and browsers. Notifications can be targeted to all application users or to a specific set of users and devices by using tags. For every message that you submit to the service, the intended audience receives a notification. | [Events](/docs/mobilepush?topic=mobilepush-at_events#at_actions) |
| [{{site.data.keyword.DRA_full}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-getting-started) | You can use {{site.data.keyword.DRA_short}} to provide comprehensive insights from popular continuous integration and continuous delivery tools to increase the speed, quality and control of your applications.  | [Events](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-at-events)|
| [{{site.data.keyword.bplong}}](/docs/schematics?topic=schematics-getting-started)  | With {{site.data.keyword.bplong_notm}}, you can enable Infrastructure as Code (IaC), and start automating the provisioning and management of your {{site.data.keyword.cloud_notm}} resources across environments. | [Events](/docs/schematics?topic=schematics-at_events) |
| [Apps](/docs/apps?topic=apps-getting-started) | Use this service to build enterprise-ready mobile and web applications in {{site.data.keyword.cloud_notm}} and take advantage of cloud extensions that are hosted by {{site.data.keyword.cloud_notm}}. | [Events](/docs/apps?topic=apps-at_events) |
{: caption="Table 8. List of developer tools services" caption-side="top"}




## Integration services
{: #integration}

The following table lists integration services that send events to {{site.data.keyword.at_short}}:

| Service     | Description | Events |
|-------------|-------------|-------------------|
| [{{site.data.keyword.messagehub_full}}](/docs/EventStreams?topic=EventStreams-getting_started)| {{site.data.keyword.messagehub}} is a high-throughput message bus that is built with Apache Kafka. It is optimized for event ingestion into {{site.data.keyword.IBM_notm}} and event stream distribution between your services and applications. | [Events](/docs/EventStreams?topic=EventStreams-at_events) |
| [MQ on IBM Cloud](/docs/mqcloud?topic=mqcloud-mqoc_getting_started) | MQ on IBM Cloud enables you to quickly and easily deploy queue managers in the cloud and connect your applications to them, for reliable data transfer between different parts of your enterprise application landscape. | [Events](/docs/mqcloud?topic=mqcloud-at_events) |
{: caption="Table 9. List of integration Cloud services" caption-side="top"}



## Network services
{: #network}

The following table lists network services that send events to {{site.data.keyword.at_short}}:

| Service     | Description | Events |
|-------------|-------------|-------------------|
| [{{site.data.keyword.BluDirectLink}} solution](/docs/dl?topic=dl-get-started-with-ibm-cloud-dl) | Use {{site.data.keyword.BluDirectLink}} to seamlessly connect your on-premises resources to your cloud resources. | [Events](/docs/dl?topic=dl-at_events) |
| [{{site.data.keyword.tg_full}}](/docs/transit-gateway?topic=transit-gateway-getting-started) | Use {{site.data.keyword.tg_full_notm}} to interconnect {{site.data.keyword.cloud_notm}} classic and Virtual Private Cloud (VPC) infrastructures worldwide, keeping traffic within the {{site.data.keyword.cloud_notm}} network. | [Events](/docs/transit-gateway?topic=transit-gateway-at_events) |
| [{{site.data.keyword.dns_full}}](/docs/dns-svcs?topic=dns-svcs-getting-started) | {{site.data.keyword.dns_short}} provides private DNS to Virtual Private Cloud (VPC) users.  | [Events](/docs/dns-svcs?topic=dns-svcs-at_events) |
| [{{site.data.keyword.cis_full}} (CIS)](/docs/cis?topic=cis-getting-started)| IBM Cloud Internet Services (CIS) provides a fast, highly performant, reliable, and secure internet service. | [Events](/docs/cis?topic=cis-at_events) |
| [Content Delivery Network](/docs/CDN#getting-started) | You can use IBM Cloud® Content Delivery Network (CDN) for various industry solutions, including media, entertainment, software, gaming, banking, and e-commerce, to meet the needs of your businesses.  | [Events](/docs/CDN?topic=CDN-at_events)|
{: caption="Table 10. List of network services" caption-side="top"}



## Platform services
{: #platform_core_integrated}


Core platform services generate events that you can view through the **Frankfurt (eu-de)** {{site.data.keyword.at_full_notm}} web UI. To view these events, you must [provision an instance](/docs/activity-tracker?topic=activity-tracker-provision#provision) of the {{site.data.keyword.at_full_notm}} service in the **Frankfurt (eu-de)** region.
{: note}


| Service                          | Service name  | Description | Events |
|----------------------------------|--------------|-------------|-------------------| 
| [BSS - Account and billing](/docs/account?topic=account-accounts#accounts) | `billing` | You can sign up for an {{site.data.keyword.IBM_notm}} account by using an existing IBMid, creating a new IBMid, or by using a federated ID. | [Events](/docs/activity-tracker?topic=activity-tracker-at_events_acc_mgt#at_events_acc_mgt_account) |
| [BSS - User management](/docs/account?topic=account-assign-access-resources) | `user-management` |  You can view and manage users across the account or organizations that you own or manage.  | [Events](/docs/activity-tracker?topic=activity-tracker-at_events_acc_mgt#at_events_acc_mgt_users) |
| [BSS - Provisioning](/docs/overview?topic=overview-ui#catalogcreate) | `provisioning` | You can create a service instance, rename a service instance, change the plan of a service instance, reclaim a service instance, restore a service instance and remove a service instance. | [Events](/docs/activity-tracker?topic=activity-tracker-at_events_rc#at_events_rc) |
| [{{site.data.keyword.iamlong}}](/docs/account?topic=account-iamoverview)   | `iam-identity` </br>`iam-groups` </br>`iam-am` | IAM enables you to securely authenticate users for platform services and control access to resources consistently across {{site.data.keyword.cloud_notm}}. | [Events](/docs/activity-tracker?topic=activity-tracker-at_events_iam) |
| [{{site.data.keyword.compliance_full}}](/docs/security-compliance?topic=security-compliance-getting-started) | `compliance` | You can use {{site.data.keyword.compliance_short}} to embed security checks into your every day workflows to help monitor for security and compliance. | [Events](/docs/security-compliance?topic=security-compliance-at_events) |
| [{{site.data.keyword.security-advisor_long}}](/docs/security-advisor?topic=security-advisor-getting-started) | `security-advisor` | You can use {{site.data.keyword.security-advisor_short}} to instantly view the security posture of your {site.data.keyword.cloud_notm}} services through a single, centralized dashboard. | [Events](/docs/security-compliance?topic=security-compliance-at_events#at_actions_insights) |
| [Global Search Service](/docs/account?topic=account-tag) | `global-search-tagging` | You can use this service to manage tags. A tag is a label that you assign to a resource for easy filtering of resources in your resource list. | [Events](/docs/activity-tracker?topic=activity-tracker-at_events_acc_mgt#at_events_acc_mgt_resources) |
| [Catalog](/docs/account?topic=account-filter-account) | `globalcatalog-collection` | You can create, organize, and manage catalogs | [Events](/docs/activity-tracker?topic=activity-tracker-at_events_acc_mgt#at_events_catalog_management) |
{: caption="Table 11. List of platform services" caption-side="top"}


For example, the following table lists core security actions that send events to {{site.data.keyword.at_full_notm}}:

| Actions     | Description | Events |
|-------------|-------------|-------------------|
| [Managing access groups](/docs/account?topic=account-groups#groups) | You can define access groups to organize a set of users and service IDs into a single entity that makes it easy for you to assign permissions. | [Events that are generated when you manage access groups](/docs/activity-tracker?topic=activity-tracker-at_events_iam#at_events_iam_access) |
| [Managing policies](/docs/account?topic=account-userroles#userroles) | You can use IAM to manage users and roles across the {{site.data.keyword.cloud_notm}} Platform and Infrastructure services. | [Events that are generated when you manage IAM policies](/docs/activity-tracker?topic=activity-tracker-at_events_iam#at_events_iam_policies) |
| [Log in to the {{site.data.keyword.cloud_notm}}](/docs/account?topic=account-iamoverview#iamoverview)| You can log into the {{site.data.keyword.cloud_notm}} by using a password, an API key, an authorization code, or a passcode. As a federated user, you can log in from the command-line interface (CLI) by using either a one-time passcode or an API key. | [Events that are generated when a user or app logs in to the {{site.data.keyword.cloud_notm}}](/docs/activity-tracker?topic=activity-tracker-at_events_iam#at_events_iam_login) |
| [Managing platform API keys](/docs/account?topic=account-manapikey#manapikey) | You can define platform API keys in the {{site.data.keyword.IBM_notm}} Cloud that are associated with a user or a service ID. | [Events that are generated when you manage Platform API keys](/docs/activity-tracker?topic=activity-tracker-at_events_iam#at_events_iam_apikeys) |
| [Managing service IDs](/docs/account?topic=account-serviceids#serviceids) | You can define service IDs at the account level in the {{site.data.keyword.IBM_notm}} Cloud. | [Events that are generated when you manage service IDs](/docs/activity-tracker?topic=activity-tracker-at_events_iam#at_events_iam_serviceids) |
{: caption="Table 12. List of core security platform services" caption-side="top"}


## Security services
{: #security}

The following table lists security Cloud services that send events to {{site.data.keyword.at_short}}:


| Service     | Description | Events |
|-------------|-------------|-------------------|
| [{{site.data.keyword.cloudcerts_full}}](/docs/certificate-manager?topic=certificate-manager-about-certificate-manager#about-certificate-manager) | You can use {{site.data.keyword.cloudcerts_short}} to manage the SSL certificates for your {{site.data.keyword.cloud_notm}}-based apps and services.  | [Events](/docs/certificate-manager?topic=certificate-manager-at_events#at_events) |
| [{{site.data.keyword.appid_full}}](/docs/appid?topic=appid-getting-started) | Use this service to secure resources and add authentication in your apps.  | [Events](/docs/appid?topic=appid-at-events)   |
| [{{site.data.keyword.keymanagementservicelong}}](/docs/key-protect?topic=key-protect-getting-started-tutorial#getting-started-tutorial) | You can use the {{site.data.keyword.keymanagementserviceshort}} service to provision encrypted keys for apps across the {{site.data.keyword.cloud_notm}}. | [Events](/docs/key-protect?topic=key-protect-at-events) |
| [{{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}}](/docs/hs-crypto?topic=hs-crypto-get-started) | You can use the {{site.data.keyword.hscrypto}} to control your cloud data encryption keys in cloud hardware security modules for apps across the {{site.data.keyword.cloud_notm}}. | [Events](/docs/hs-crypto?topic=hs-crypto-at-events) |
| [{{site.data.keyword.secrets-manager_full}}](/docs/secrets-manager?topic=secrets-manager-getting-started) | With {{site.data.keyword.secrets-manager_full_notm}}, you can create, lease, and centrally manage secrets that are used in {{site.data.keyword.cloud_notm}} services or your custom-built applications. | [Events](/docs/secrets-manager?topic=secrets-manager-at-events) |
{: caption="Table 13. List of security services" caption-side="top"}



## Storage services
{: #storage}


The following table lists storage services that send events to {{site.data.keyword.at_short}}:

| Service     | Description | Events |
|-------------|-------------|-------------------|
| [{{site.data.keyword.cos_full}}](/docs/cloud-object-storage?topic=cloud-object-storage-getting-started-cloud-object-storage)| You can use {{site.data.keyword.cos_full_notm}} to store unstructured data in the {{site.data.keyword.cloud_notm}}.  | [Events](/docs/cloud-object-storage?topic=cloud-object-storage-at-events) |
| [{{site.data.keyword.mdms_short}}](/docs/mass-data-migration?topic=mass-data-migration-getting-started-tutorial)| You can use {{site.data.keyword.mdms_short}} to upload data quickly to the {{site.data.keyword.cloud_notm}}.  | [Events](/docs/mass-data-migration?topic=mass-data-migration-at-events) |
{: caption="Table 14. List of storage events" caption-side="top"}


{{site.data.keyword.cos_full_notm}} (COS) generates global, management, and data events.
* By default, events that report on global actions such as the creation of a bucket are collected automatically. You can monitor these events through the {{site.data.keyword.at_short}} instance that is located in the Frankfurt location.
* Collection of management and data events in your account is optional.
* **You must configure each bucket to enable management events, or management and data events.** Notice that you cannot enable data events only for a bucket.

    * To monitor management events, you must configure a bucket and specify the {{site.data.keyword.at_short}} instance where those events will be available for monitoring.
    * To monitor data events, you must select the option **Track data events** when you associate a bucket with an {{site.data.keyword.at_short}} instance.

{{site.data.keyword.mdms_short}} generates global events only, for each transition of the order state.


## Web and mobile services
{: #web}

The following table lists web and mobile services that send events to {{site.data.keyword.at_short}}:

| Service     | Description | Events |
|-------------|-------------|-------------------|
| [{{site.data.keyword.mobilefoundation_long}}](/docs/mobilefoundation?topic=mobilefoundation-getting-started)| The {{site.data.keyword.mobilefoundation_short}} service is a scalable, secure mobile-access gateway that you can use to simplify integration with back-end and cloud services.  | [Events](/docs/mobilefoundation?topic=mobilefoundation-mfp_activity_tracker) |
{: caption="Table 15. List of web and mobile events" caption-side="top"}

## VPC infrastructure
{: #vpc_infrastructure}

You can provision a Virtual Private Cloud (VPC) in the {{site.data.keyword.cloud_notm}} to run an isolated environment within the public cloud. VPC gives you the security of a private cloud, with the agility and ease of a public cloud. For more information, see [{{site.data.keyword.vpc_full}}](/docs/vpc?topic=vpc-getting-started).

The following table lists VPC infrastructure services that send events to {{site.data.keyword.at_full_notm}}:

| Service     | Description |Events             |
|-------------|-------------|-------------------|
| [Storage resources](/docs/vpc?topic=vpc-block-storage-about) | Use this service to provide hypervisor-mounted, high-performance data storage for virtual server instances (instances) in your VPC. | [Events](/docs/vpc?topic=vpc-at-events#events-storage) |
| [Compute resources](/docs/vpc?topic=vpc-about-advanced-virtual-servers) | Use this service to provision scalable compute resources in the IBM Cloud. | [Events](/docs/vpc?topic=vpc-at-events#events-compute) |
| [Network resources](/docs/vpc?topic=vpc-about-networking-for-vpc) | Use this service to add network resources to your VPC infrastructure. | [Events](/docs/vpc?topic=vpc-at-events#events-network) |
| [Load Balancer](/docs/vpc?topic=vpc-load-balancers)| Use this service to distribute traffic among multiple server instances within the same region of your VPC.  | [Events](/docs/vpc?topic=vpc-at-events#events-load-balancers) |
| [VPN](/docs/vpc?topic=vpc-using-vpn)| Use this service to connect private networks in a secure fashion. You can use VPN to set up an IPsec site-to-site tunnel between your VPC and your on-premise private network or another VPC. | [Events](/docs/vpc?topic=vpc-at-events#at-events) |
| [Images](/docs/vpc?topic=vpc-about-images) | When you provision {{site.data.keyword.vsi_is_short}}, you can select from the supported stock images or a custom image that you import from {{site.data.keyword.cos_full_notm}}. | [Events](/docs/vpc?topic=vpc-at-events#events-images) |
{: caption="Table 16. List of VPC infrastructure services" caption-side="top"}

## Watson AI
{: #watson_ai}

The following table lists Watson AI services that send events to {{site.data.keyword.at_full_notm}}:

| Service     | Description | Events            |
|-------------|-------------|-------------------|
| [{{site.data.keyword.conversationfull}}](/docs/assistant?topic=assistant-getting-started) | Build your own branded assistant into any device, application, or channel. Your assistant connects to the customer engagement resources you already use to deliver an engaging, unified problem-solving experience to your customers. | [Events](/docs/assistant?topic=assistant-at-events) |
| [{{site.data.keyword.discoveryfull}}](/docs/discovery?topic=discovery-getting-started) | Build cognitive, cloud-based exploration applications that unlock actionable insights hidden in unstructured data — including your own proprietary data, as well as public and third-party data. | [Events](/docs/discovery?topic=discovery-at_events)  |
| [{{site.data.keyword.cncfull}}](/docs/compare-comply?topic=compare-comply-about)  | Extract data from contracts and governing documents to increase productivity, reduce costs and minimize exposure. | [Events](/docs/compare-comply?topic=compare-comply-at_events) |
| [{{site.data.keyword.DSX_full}}](https://dataplatform.cloud.ibm.com/docs/content/wsj/getting-started/overview-ws.html) | Provide a collaborative machine-learning platform for teams to explore, model and deploy AI-powered applications, using open-source tools. | [Events](https://dataplatform.cloud.ibm.com/docs/content/wsj/admin/at-events.html#ws) |
| [IBM Watson&trade; Knowledge Catalog](https://dataplatform.cloud.ibm.com/docs/content/wsj/catalog/overview-wkc.html) | Provides a secure enterprise catalog management platform that is supported by a policy framework. A catalog connects data and knowledge with the people who need to use it. The policy framework ensures that data access is compliant with your business rules. | [Events](https://dataplatform.cloud.ibm.com/docs/content/wsj/admin/at-events.html#wkc) |
| [{{site.data.keyword.knowledgestudiofull}}](/docs/watson-knowledge-studio) | Train custom models that identify entities and relationships unique to your industry in unstructured text. Build your models in a collaborative environment designed for both developers and domain experts, without needing to write code. Use the models in IBM Watson Discovery, IBM Watson Natural Language Understanding and IBM Watson Explorer. | [Events](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-activity-tracker-events) |
| [{{site.data.keyword.languagetranslatorfull}}](/docs/language-translator?topic=language-translator-gettingstarted) | {{site.data.keyword.languagetranslatorfull}} allows you to translate text programmatically from one language into another language.  | [Events](/docs/language-translator?topic=language-translator-at_events) |
| [{{site.data.keyword.pm_full}}](https://dataplatform.cloud.ibm.com/docs/content/wsj/analyze-data/ml-overview.html) | Integrated to work with Watson Studio, Watson Machine Learning empowers your cross-functional team to deploy, monitor and optimize models quickly and easily. | [Events](https://dataplatform.cloud.ibm.com/docs/content/wsj/admin/at-events.html#wml) |
| [{{site.data.keyword.nlclassifierfull}}](/docs/natural-language-classifier?topic=natural-language-classifier-natural-language-classifier) | Build custom text classification models and return matching classes for a sentence, phrase, or paragraph. | [Events](/docs/natural-language-classifier?topic=natural-language-classifier-at_events) |
| [{{site.data.keyword.nlufull}}](/docs/natural-language-understanding) | Analyze text to extract entities, relations, keywords, sentiment, semantic roles and more. | [Events](/docs/natural-language-understanding?topic=natural-language-understanding-at_events) |
| [{{site.data.keyword.speechtotextfull}}](/docs/speech-to-text?topic=speech-to-text-gettingStarted) | Transcribes audio to text to enable speech transcription capabilities for applications. | [Events](/docs/speech-to-text?topic=speech-to-text-atEvents) |
| [{{site.data.keyword.texttospeechfull}}](/docs/text-to-speech?topic=text-to-speech-gettingStarted) | Converts written text to natural-sounding speech to provide speech-synthesis capabilities for applications. | [Events](/docs/text-to-speech?topic=text-to-speech-atEvents) |
| [{{site.data.keyword.visualrecognitionfull}}](/docs/visual-recognition?topic=visual-recognition-index) | Uses deep learning algorithms to analyze images for scenes, objects, and other content. The response includes keywords that provide information about the content. | [Events](/docs/visual-recognition?topic=visual-recognition-at_events) |
| [{{site.data.keyword.wh-acd_full}}](/docs/wh-acd?topic=wh-acd-getting-started) | Finds medical concepts, medical codes, and contextual information in unstructured text. | [Events](/docs/wh-acd?topic=wh-acd-at_events) |
{: caption="Table 17. List of Watson AI services" caption-side="top"}


