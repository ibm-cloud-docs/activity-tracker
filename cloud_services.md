---

copyright:
  years: 2019, 2024
lastupdated: "2024-02-06"

keywords:

subcollection: activity-tracker


---

{{site.data.keyword.attribute-definition-list}}



# IBM Cloud services that generate {{site.data.keyword.at_short}} events
{: #cloud_services}

{{site.data.keyword.cloud_notm}} services that use {{site.data.keyword.at_short}} to monitor user-initiated activities that change the state of any of the following services in the {{site.data.keyword.cloud_notm}}.
{: shortdesc}

{{site.data.keyword.at_short}} hosted event search routes location-based auditing events to an {{site.data.keyword.at_short}} instance in the region where they are generated and routes global auditing events to the {{site.data.keyword.at_short}} instance that is provisioned in Frankfurt.
{: important}


## Analytics services
{: #analytics}

The following table lists analytics services that send auditing events:

| Service     | CRN service name | {{site.data.keyword.at_short}} hosted event search offering | Events |
|-------------|--------------|------------------|--------|
| [{{site.data.keyword.iae_full}}](/docs/AnalyticsEngine?topic=AnalyticsEngine-getting-started) | `ibmanalyticsengine` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") |  [Location-based events](/docs/AnalyticsEngine?topic=AnalyticsEngine-at_events-serverless) |
| [{{site.data.keyword.sqlquery_full}}](/docs/sql-query?topic=sql-query-overview#overview) | `sql-query` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/sql-query?topic=sql-query-activitytracker#activitytracker) |
| [{{site.data.keyword.PA_SaaS_full}}](/docs/planning-analytics?topic=planning-analytics-about) | `planning-analytics` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/planning-analytics?topic=planning-analytics-at_events) |
| [{{site.data.keyword.dv_short}}](/docs/data-virtualization?topic=data-virtualization-getting-started) | `data-virtualization` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](https://dataplatform.cloud.ibm.com/docs/content/wsj/admin/at-events.html?context=cpdaas&audience=wdp#dv){: exernal} |
{: caption="Table 1. List of analytics services" caption-side="top"}

## Classic services
{: #classic}

The following table lists services that send auditing events:

| Service     | CRN service name | {{site.data.keyword.at_short}} hosted event search offering | Events |
|-------------|--------------|------------------|--------|
| [{{site.data.keyword.BluVirtServers_full}} (Classic)](/docs/virtual-servers?topic=virtual-servers-about-virtual-servers#about-virtual-servers)| `audit-log` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/virtual-servers?topic=virtual-servers-at_events#at_events) |
| [{{site.data.keyword.baremetal_long}} (Classic)](/docs/bare-metal?topic=bare-metal-about-bm#about-bm) | `audit-log` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/bare-metal?topic=bare-metal-bm-at-events#bm-at-events) |
{: caption="Table 2. List of classic services" caption-side="top"}



## Compute serverless services
{: #serverless}

The following table lists serverless compute services that send auditing events:

| Service     | CRN service name | {{site.data.keyword.at_short}} hosted event search offering | Events |
|-------------|--------------|------------------|--------|
| [{{site.data.keyword.codeenginefull}}](/docs/codeengine?topic=codeengine-getting-started)| `codeengine`  | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/codeengine?topic=codeengine-at_events) |
{: caption="Table 3. List of serverless compute services" caption-side="top"}



## Container services
{: #container}

The following table lists container platform services that send auditing events:

| Service     | CRN service name | {{site.data.keyword.at_short}} hosted event search offering | Events |
|-------------|--------------|------------------|--------|
| [{{site.data.keyword.registrylong}}](/docs/Registry?topic=Registry-getting-started) | `container-registry` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/Registry?topic=Registry-at_events) |
| [{{site.data.keyword.containerlong}}](/docs/containers?topic=containers-getting-started) | `containers-kubernetes` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") |  [Location-based events](/docs/containers?topic=containers-at_events) |
| [{{site.data.keyword.openshiftlong}}](/docs/openshift?topic=openshift-getting-started) | `openshift` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/openshift?topic=openshift-at_events) |
| [{{site.data.keyword.satellitelong}}](/docs/satellite?topic=satellite-getting-started) | `satellite` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/satellite?topic=satellite-at_events) |
{: caption="Table 4. Container events" caption-side="top"}


## Database services
{: #database}

The following table lists database services that send auditing events:

| Service     | CRN service name | {{site.data.keyword.at_short}} hosted event search offering | Events |
|-------------|--------------|------------------|--------|
| [{{site.data.keyword.cloudantfull}}](/docs/Cloudant?topic=Cloudant-getting-started-with-cloudant) | `cloudantnosqldb`  | ![Checkmark](/images/checkmark-icon.svg "Checkmark")| [Location-based events](/docs/Cloudant?topic=Cloudant-at_events) |
| [{{site.data.keyword.databases-for-enterprisedb_full}}](/docs/databases-for-enterprisedb?topic=databases-for-enterprisedb-getting-started) | `databases-for-enterprisedb-group` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/databases-for-enterprisedb?topic=databases-for-enterprisedb-activity-tracker) |
| [{{site.data.keyword.databases-for-postgresql_full}}](/docs/databases-for-postgresql?topic=databases-for-postgresql-getting-started) | `databases-for-postgresql` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/databases-for-postgresql?topic=databases-for-postgresql-activity-tracker) |
| [{{site.data.keyword.databases-for-redis_full_notm}}](/docs/databases-for-redis?topic=databases-for-redis-getting-started) | `databases-for-redis-group` | ![Checkmark](/images/checkmark-icon.svg "Checkmark")| [Location-based events](/docs/databases-for-redis?topic=databases-for-redis-activity-tracker) |
| [{{site.data.keyword.databases-for-etcd_full_notm}}](/docs/databases-for-etcd?topic=databases-for-etcd-getting-started) | `databases-for-etcd-group` | ![Checkmark](/images/checkmark-icon.svg "Checkmark")| [Location-based events](/docs/databases-for-etcd?topic=databases-for-etcd-activity-tracker) |
| [{{site.data.keyword.databases-for-elasticsearch_full_notm}}](/docs/databases-for-elasticsearch?topic=databases-for-elasticsearch-getting-started) | `databases-for-elasticsearch-group` | ![Checkmark](/images/checkmark-icon.svg "Checkmark")|  [Location-based events](/docs/cloud-databases?topic=cloud-databases-activity-tracker) |
| [{{site.data.keyword.messages-for-rabbitmq_full}}](/docs/messages-for-rabbitmq?topic=messages-for-rabbitmq-getting-started)  | `messages-for-rabbitmq-group` | ![Checkmark](/images/checkmark-icon.svg "Checkmark")| [Location-based events](/docs/messages-for-rabbitmq?topic=messages-for-rabbitmq-activity-tracker) |
| [{{site.data.keyword.databases-for-mongodb_full_notm}}](/docs/databases-for-mongodb) | `databases-for-mongodb-group` | ![Checkmark](/images/checkmark-icon.svg "Checkmark")| [Location-based events](/docs/databases-for-mongodb?topic=databases-for-mongodb-activity-tracker) |
| [{{site.data.keyword.databases-for-mysql_full}}](/docs/databases-for-mysql) | `databases-for-mysql-group` | ![Checkmark](/images/checkmark-icon.svg "Checkmark")|  [Location-based events](/docs/databases-for-mysql?topic=databases-for-mysql-activity-tracker) |
| [{{site.data.keyword.Db2_on_Cloud_long}}](/docs/Db2onCloud?topic=Db2onCloud-about) | `db2oncloud` | ![Checkmark](/images/checkmark-icon.svg "Checkmark")| [Location-based events](/docs/Db2onCloud?topic=Db2onCloud-auditing) |
| [{{site.data.keyword.dashdblong_notm}}](/docs/Db2whc?topic=Db2whc-getting-started) | `dashdb` | `[*]` | [Global events](/docs/activity-tracker?topic=activity-tracker-at_events_dashdb) |
{: caption="Table 5. List of database services" caption-side="top"}

`[*]` - Events provided by the BSS service.

## Developer tools
{: #devops}

The following table lists developer tools and DevOps services that send auditing events:

| Service     | CRN service name | {{site.data.keyword.at_short}} hosted event search offering | Events |
|-------------|--------------|------------------|--------|
| [{{site.data.keyword.bplong}}](/docs/schematics?topic=schematics-getting-started)  | `schematics` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/schematics?topic=schematics-at_events) |
| [Apps](/docs/apps?topic=apps-getting-started) | `developer-experience` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | Location-based events |
| [{{site.data.keyword.cloud-shell_full}}](/docs/cloud-shell?topic=cloud-shell-getting-started) | `cloudshell` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/cloud-shell?topic=cloud-shell-at_events) |
| [{{site.data.keyword.en_full}}](/docs/event-notifications?topic=event-notifications-getting-started) | `event-notifications`|![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/event-notifications?topic=event-notifications-en-at_events)|
| [{{site.data.keyword.appconfig_full}}](/docs/app-configuration?topic=app-configuration-getting-started) | `apprapp`|![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/app-configuration?topic=app-configuration-ac-at_events)|
{: caption="Table 6. List of developer tools services" caption-side="top"}


The following table lists {{site.data.keyword.contdelivery_full}} services that send auditing events:

| Service     | CRN service name | {{site.data.keyword.at_short}} hosted event search offering | Events |
|-------------|--------------|------------------|--------|
| [{{site.data.keyword.contdelivery_full}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-getting-started) | `continuous-delivery` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-at-events) |
| [Toolchain](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd_about) | `toolchain` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-at-events#toolchain-events) |
{: caption="Table 7. List of developer tools services" caption-side="top"}



## Integration services
{: #integration}

The following table lists integration services that send auditing events:

| Service     | CRN service name | {{site.data.keyword.at_short}} hosted event search offering | Events |
|-------------|--------------|------------------|--------|
| [{{site.data.keyword.messagehub_full}}](/docs/EventStreams?topic=EventStreams-getting-started)| `event-streams` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/EventStreams?topic=EventStreams-at_events) |
| [MQ on IBM Cloud](/docs/mqcloud?topic=mqcloud-getting_started) |`mqcloud` |![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/mqcloud?topic=mqcloud-at_events) |
|[{{site.data.keyword.apiconnect_long}}](/docs/apiconnect?topic=apiconnect-getting-started)| `apiconnect` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/apiconnect?topic=apiconnect-at_events) |
{: caption="Table 8. List of integration Cloud services" caption-side="top"}



## Network services
{: #network}

The following table lists network services that send auditing events:

| Service     | CRN service name | {{site.data.keyword.at_short}} hosted event search offering | Events |
|-------------|--------------|------------------|--------|
| [{{site.data.keyword.BluDirectLink}} solution](/docs/dl?topic=dl-get-started-with-ibm-cloud-dl) | `directlink.dedicated` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Global events](/docs/dl?topic=dl-at_events) |
| [{{site.data.keyword.tg_full}}](/docs/transit-gateway?topic=transit-gateway-getting-started) | `transit` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Global events](/docs/transit-gateway?topic=transit-gateway-at_events) |
| [{{site.data.keyword.dns_full}}](/docs/dns-svcs?topic=dns-svcs-getting-started) | `dns-svcs` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Global events](/docs/dns-svcs?topic=dns-svcs-at_events) |
| [{{site.data.keyword.cis_full}} (CIS)](/docs/cis?topic=cis-getting-started)| `internet-svcs` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Global events](/docs/cis?topic=cis-at_events) |
| [Content Delivery Network](/docs/CDN#getting-started) | `cdn-powered-by-akamai` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Global events](/docs/CDN?topic=CDN-at_events)|
{: caption="Table 9. List of network services" caption-side="top"}

## Observability services
{: #observability}

The following table lists observability services that send auditing events:

| Service     | CRN service name | {{site.data.keyword.at_short}} hosted event search offering | Events |
|-------------|--------------|------------------|--------|
| [{{site.data.keyword.at_full}} hosted event search offering](/docs/activity-tracker?topic=activity-tracker-getting-started) | `logdnaat` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/activity-tracker?topic=activity-tracker-at_events) |
| [{{site.data.keyword.atracker_full}}](/docs/activity-tracker?topic=activity-tracker-getting-started) | `atracker` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/activity-tracker?topic=activity-tracker). |
| [{{site.data.keyword.la_full}}](/docs/log-analysis?topic=log-analysis-getting-started#getting-started) | `logdna` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/log-analysis?topic=log-analysis-at_events) |
| [{{site.data.keyword.mon_full}}](/docs/monitoring?topic=monitoring-getting-started) | `sysdig-monitor` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/monitoring?topic=monitoring-at_events) |
| [{{site.data.keyword.metrics_router_full_notm}}](/docs/metrics-router?topic=metrics-router-getting-started) | `metrics-router` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/monitoring?topic=monitoring-at_events) |
{: caption="Table 10. List of observability services" caption-side="top"}


## Platform services
{: #platform_core_integrated}

The following table lists platform services that send auditing events:

| Service     | CRN service name | {{site.data.keyword.at_short}} hosted event search offering | Events |
|-------------|--------------|------------------|--------|
| [Billing](/docs/account?topic=account-account-services&interface=ui#billing-acct-mgmt ) | `billing` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Global events](/docs/activity-tracker?topic=activity-tracker-at_events_acc_mgt#at_events_acc_mgt_account) |
| [User management](/docs/account?topic=account-iamuserinv) | `user-management` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Global events](/docs/activity-tracker?topic=activity-tracker-at_events_acc_mgt#at_events_acc_mgt_users) |
| [Provisioning](/docs/account?topic=account-manage_resource) | `provisioning` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Global events](/docs/activity-tracker?topic=activity-tracker-at_events_rc#at_events_rc) |
| [{{site.data.keyword.iamlong}}](/docs/account?topic=account-iamoverview)   | `iam-identity`   \n `iam-groups`   \n `iam-am` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Global events](/docs/activity-tracker?topic=activity-tracker-at_events_iam) |
| [{{site.data.keyword.compliance_full}}](/docs/security-compliance?topic=security-compliance-getting-started) | `compliance`  \n `security-advisor` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Global events](/docs/security-compliance?topic=security-compliance-at_events) |
| [Global Search Service](/docs/account?topic=account-tag) | `global-search-tagging` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Global events](/docs/activity-tracker?topic=activity-tracker-at_events_acc_mgt#at_events_acc_mgt_resources) |
| [Catalog Management](/docs/account?topic=account-filter-account) | `globalcatalog-collection` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Global events](/docs/activity-tracker?topic=activity-tracker-at_events_acc_mgt#at_events_catalog_management) |
| [Software instances](/docs/account?topic=account-sw-instance-details) | `globalcatalog-instance` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Global events](/docs/activity-tracker?topic=activity-tracker-at_events_acc_mgt#at_events_sw_instance) |
| [Context-based restrictions](/docs/account?topic=account-context-restrictions-whatis) | `context-based-restrections` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Global events](/docs/activity-tracker?topic=activity-tracker-events_context_based#restriction_rules_events) |
| [Projects](/docs/secure-enterprise?topic=secure-enterprise-understanding-projects) | `project` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Global events](/docs/secure-enterprise?topic=secure-enterprise-at_events) |
{: caption="Table 11. List of platform services" caption-side="top"}

For example, the following table lists core security actions that send events to {{site.data.keyword.at_full_notm}}:

| Service     | {{site.data.keyword.at_short}} hosted event search offering | Events |
|-------------|------------------|--------|
| [Managing access groups](/docs/account?topic=account-groups#groups) | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Events that are generated when you manage access groups](/docs/activity-tracker?topic=activity-tracker-at_events_iam#at_events_iam_access) |
| [Managing policies](/docs/account?topic=account-userroles#userroles) | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Events that are generated when you manage IAM policies](/docs/activity-tracker?topic=activity-tracker-at_events_iam#at_events_iam_policies) |
| [Log in to the {{site.data.keyword.cloud_notm}}](/docs/account?topic=account-iamoverview#iamoverview)| ![Checkmark](/images/checkmark-icon.svg "Checkmark") |  [Events that are generated when a user or app logs in to the {{site.data.keyword.cloud_notm}}](/docs/activity-tracker?topic=activity-tracker-at_events_iam#at_events_iam_login) |
| [Managing platform API keys](/docs/account?topic=account-manapikey#manapikey) |![Checkmark](/images/checkmark-icon.svg "Checkmark")  | [Events that are generated when you manage Platform API keys](/docs/activity-tracker?topic=activity-tracker-at_events_iam#at_events_iam_apikeys) |
| [Managing service IDs](/docs/account?topic=account-serviceids#serviceids) | ![Checkmark](/images/checkmark-icon.svg "Checkmark") |[Events that are generated when you manage service IDs](/docs/activity-tracker?topic=activity-tracker-at_events_iam#at_events_iam_serviceids) |
{: caption="Table 12. List of core security platform services" caption-side="top"}

## Security services
{: #security}

The following table lists security Cloud services that send auditing events:


| Service     | CRN service name | {{site.data.keyword.at_short}} hosted event search offering | Events |
|-------------|--------------|------------------|--------|
| [{{site.data.keyword.appid_full}}](/docs/appid?topic=appid-getting-started) | `appid` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/appid?topic=appid-at-events)   |
| [{{site.data.keyword.keymanagementservicelong}}](/docs/key-protect?topic=key-protect-getting-started-tutorial#getting-started-tutorial) | `kms` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/key-protect?topic=key-protect-at-events) |
| [{{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}}](/docs/hs-crypto?topic=hs-crypto-get-started) | `hs-crypto` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/hs-crypto?topic=hs-crypto-at-events) |
| [{{site.data.keyword.secrets-manager_full}}](/docs/secrets-manager?topic=secrets-manager-getting-started) | `secrets-manager` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/secrets-manager?topic=secrets-manager-at-events) |
{: caption="Table 13. List of security services" caption-side="top"}



## Storage services
{: #storage}


The following table lists storage services that send auditing events:

| Service     | CRN service name | {{site.data.keyword.at_short}} hosted event search offering | Events |
|-------------|--------------|------------------|--------|
| [{{site.data.keyword.cos_full}}](/docs/cloud-object-storage?topic=cloud-object-storage-getting-started-cloud-object-storage)| `cloud-object-storage` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Global and location-based events `[*]`](/docs/cloud-object-storage?topic=cloud-object-storage-at-events) |
{: caption="Table 14. List of storage events" caption-side="top"}


`[*]` {{site.data.keyword.cos_full_notm}} (COS) generates global, and location-based events.
* By default, bucket management events such as the creation of a bucket are collected automatically.
* Collection of data events in your account is optional. You must configure each bucket to enable data events by selecting the option **Track data events**.



## VMware Solutions
{: #vmware_solutions}

With {{site.data.keyword.vmwaresolutions_full_notm}}, you can quickly and seamlessly integrate or migrate your on-premises VMware workloads to the {{site.data.keyword.cloud_notm}} by using the scalable, secure, and high-performance {{site.data.keyword.cloud_notm}} infrastructure and the industry-leading VMware hybrid virtualization technology. You can easily deploy your VMware virtual environments and manage the infrastructure resources on {{site.data.keyword.cloud_notm}}. At the same time, you can still use your familiar native VMware product console to manage the VMware workloads. [Learn more](https://www.ibm.com/products/vmware){: external}.

The following table lists VMware solution services that send auditing events:

| Service     | CRN service name | {{site.data.keyword.at_short}} hosted event search offering | Events |
|-------------|--------------|------------------|--------|
| [{{site.data.keyword.vmwaresolutions_short}}](/docs/vmwaresolutions?topic=vmwaresolutions-vc_vcenterserveroverview)   | `vmware-solutions` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Global events](/docs/vmwaresolutions?topic=vmwaresolutions-at-events#at-events) |
| [{{site.data.keyword.cloud}} for VMware® Solutions Shared](/docs/vmwaresolutions?topic=vmwaresolutions-shared_overview)      | `vmware-solutions` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/vmwaresolutions?topic=vmwaresolutions-at-events#at-events-instance-mgmt) |
| [KMIP for VMware](/docs/vmwaresolutions?topic=vmwaresolutions-kmip_standalone_considerations) | `vmware-solutions` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/vmwaresolutions?topic=vmwaresolutions-at-events#at-events-kmip) |
{: caption="Table 15. List of VMware solution services" caption-side="top"}




## VPC services
{: #vpc_services}

You can provision a Virtual Private Cloud (VPC) in the {{site.data.keyword.cloud_notm}} to run an isolated environment within the public cloud. VPC gives you the security of a private cloud, with the agility and ease of a public cloud. See [{{site.data.keyword.vpc_full}} Gen 2](/docs/vpc?topic=vpc-getting-started).


The following table lists VPC infrastructure services that send auditing events:

| Service     | Service name | {{site.data.keyword.at_short}} hosted event search offering |  Events |
|-------------|--------------|------------------|--------|
| [VPC](/docs/vpc?topic=vpc-getting-started) | `is` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/vpc?topic=vpc-at-events) |
| [Load Balancer](/docs/vpc?topic=vpc-load-balancers)| `is.load-balancer` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/vpc?topic=vpc-at-events#events-load-balancers) |
| [VPN](/docs/vpc?topic=vpc-using-vpn)| `is.vpn` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/vpc?topic=vpc-at-events#at-events) |
| [Client VPN](/docs/vpc?topic=vpc-vpn-client-to-site-overview)| `is.vpn-server` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/vpc?topic=vpc-at-events#events-vpn-server) |
{: caption="Table 16. List of VPC infrastructure services (generation 2)" caption-side="top"}

## Watson AI
{: #watson_ai}

The following table lists Watson AI services that send auditing events:

| Service     | CRN service name | {{site.data.keyword.at_short}} hosted event search offering | Events |
|-------------|--------------|------------------|--------|
| [{{site.data.keyword.conversationfull}}](/docs/watson-assistant?topic=watson-assistant-getting-started) | `conversation`  | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/watson-assistant?topic=watson-assistant-admin-auditing) |
| [{{site.data.keyword.discoveryfull}}](/docs/discovery-data?topic=discovery-data-getting-started) | `discovery` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/discovery-data?topic=discovery-data-at_events)  |
| [{{site.data.keyword.DSX_full}}](https://dataplatform.cloud.ibm.com/docs/content/svc-welcome/wsl.html?context=cpdaas) | `data-science-experience`  | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](https://dataplatform.cloud.ibm.com/docs/content/wsj/admin/at-events.html?context=cpdaas#ws) |
| [IBM Watson&trade; Knowledge Catalog](https://dataplatform.cloud.ibm.com/docs/content/svc-welcome/wkc.html?context=cpdaas) | `datacatalog` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](https://dataplatform.cloud.ibm.com/docs/content/wsj/admin/at-events.html?context=cpdaas#wkc) |
| [{{site.data.keyword.knowledgestudiofull}}](/docs/watson-knowledge-studio) | `knowledge-studio` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-activity-tracker-events) |
| [{{site.data.keyword.languagetranslatorfull}}](/docs/language-translator?topic=language-translator-about) | `language-translator` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/language-translator?topic=language-translator-at_events) |
| [{{site.data.keyword.pm_full}}](https://dataplatform.cloud.ibm.com/docs/content/wsj/analyze-data/ml-overview.html) | `pm-20` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](https://dataplatform.cloud.ibm.com/docs/content/wsj/admin/at-events.html?context=cpdaas#wml) |
| [{{site.data.keyword.nlufull}}](/docs/natural-language-understanding) | `natural-language-understanding` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/natural-language-understanding?topic=natural-language-understanding-at_events) |
| [{{site.data.keyword.speechtotextfull}}](/docs/speech-to-text?topic=speech-to-text-gettingStarted) | `speech-to-text` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/speech-to-text?topic=speech-to-text-at-events) |
| [{{site.data.keyword.texttospeechfull}}](/docs/text-to-speech?topic=text-to-speech-gettingStarted) | `text-to-speech` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/text-to-speech?topic=text-to-speech-at-events) |
{: caption="Table 17. List of Watson AI services" caption-side="top"}


## Power IaaS services
{: #power_iaas_services}

Power Systems Virtual Server (PowerVS) projects deliver flexible compute capacity for Power Systems workloads. Integrated with the {{site.data.keyword.cloud_notm}} platform for on-demand provisioning, this offering provides a secure and scalable server virtualization environment that is built upon the advanced RAS features and leading performance of the Power Systems™ platform. See [{{site.data.keyword.powerSysFull}}](/docs/power-iaas?topic=power-iaas-getting-started).


The following table lists Power IaaS infrastructure services that send auditing events:

| Service     | Service name | {{site.data.keyword.at_short}} hosted event search offering |  Events |
|-------------|--------------|------------------|--------|
| [{{site.data.keyword.powerSys_notm}}](/docs/power-iaas?topic=power-iaas-getting-started) | `power-iaas` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/power-iaas?topic=power-iaas-at-events) |
| [SSHKeys](/docs/power-iaas?topic=power-iaas-create-vm) | `pcloud.ssh-key` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/power-iaas?topic=power-iaas-at-events#at-actions-ssh) |
{: caption="Table 18. List of Power Systems Virtual Server infrastructure services" caption-side="top"}

## Cloud Pak
{: #cloud_pak}


The following table lists Cloud Pak services that send auditing events:

| Service     | Service name | {{site.data.keyword.at_short}} hosted event search offering |  Events |
|-------------|--------------|------------------|--------|
| [{{site.data.keyword.cpd_short}}](https://www.ibm.com/docs/en/cloud-paks/cp-data/4.8.x){: external} | `cp4d` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [List of events](https://www.ibm.com/docs/en/cloud-paks/cp-data/4.8.x?topic=data-services-that-support-audit-logging){: external} |
| [{{site.data.keyword.cpd_short}} as a Service](https://dataplatform.cloud.ibm.com/docs/content/wsj/getting-started/welcome-main.html?context=cpdaas&audience=wdp){: external} | `cpdaas` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [List of events](https://dataplatform.cloud.ibm.com/docs/content/wsj/admin/at-events.html?context=cpdaas&audience=wdp){: external} |
{: caption="Table 19. List of {{site.data.keyword.cpd_full_notm}} services" caption-side="top"}
