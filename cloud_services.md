---

copyright:
  years: 2019, 2021
lastupdated: "2021-11-03"

keywords: IBM Cloud, {{site.data.keyword.atracker_short}} event routing, security, auditing, services, {{site.data.keyword.at_short}} hosted event search offering

subcollection: activity-tracker


---

{{site.data.keyword.attribute-definition-list}}



# Cloud services
{: #cloud_services}

Use {{site.data.keyword.atracker_short}} to monitor user-initiated activities that change the state of any of the following services in the {{site.data.keyword.cloud_notm}}.
{: shortdesc}

## Analytics services
{: #analytics}

The following table lists analytics services that send auditing events:

| Service     | CRN service name | {{site.data.keyword.at_short}} hosted event search offering | {{site.data.keyword.atracker_short}} event routing | Events |
|-------------|--------------|------------------|-------------------|--------|
| [{{site.data.keyword.iae_full}}](/docs/AnalyticsEngine?topic=AnalyticsEngine-getting-started) | `ibmanalyticsengine` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") |  | [Location-based events](/docs/AnalyticsEngine?topic=AnalyticsEngine-at_events) |
| [{{site.data.keyword.sqlquery_full}}](/docs/sql-query?topic=sql-query-overview#overview) | `sql-query` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") |  | [Location-based events](/docs/sql-query?topic=sql-query-activitytracker#activitytracker) |
| [{{site.data.keyword.dv_short}}](/docs/data-virtualization?topic=data-virtualization-about) | `data-virtualization` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") |  | [Location-based events](/docs/data-virtualization?topic=data-virtualization-activity-tracker) |
{: caption="Table 1. List of analytics services" caption-side="top"}

## Classic services
{: #classic}

The following table lists services that send auditing events:

| Service     | CRN service name | {{site.data.keyword.at_short}} hosted event search offering | {{site.data.keyword.atracker_short}} event routing | Events |
|-------------|--------------|------------------|-------------------|--------|
| [{{site.data.keyword.BluVirtServers_full}} (Classic)](/docs/vsi?topic=virtual-servers-about-virtual-servers#about-virtual-servers)| `audit-log` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") |  [Location-based events](/docs/vsi?topic=virtual-servers-at_events#at_events) |
| [{{site.data.keyword.baremetal_long}} (Classic)](/docs/bare-metal?topic=bare-metal-about-bm#about-bm) | `audit-log` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/bare-metal?topic=bare-metal-bm-at-events#bm-at-events) |




## Cloud Foundry applications
{: #platform_cfapps}

The events that are sent by Cloud Foundry applications to {{site.data.keyword.cloudaccesstrailshort}} are listed in the response area of the `GET /v2/events`, under the body section. The *Type* field lists all actions that generate an event. For more information, see the [Events API](https://apidocs.cloudfoundry.org/270/events/list_all_events.html){: external}.

## Compute serverless services
{: #serverless}

The following table lists serverless compute services that send auditing events:

| Service     | CRN service name | {{site.data.keyword.at_short}} hosted event search offering | {{site.data.keyword.atracker_short}} event routing | Events |
|-------------|--------------|------------------|-------------------|--------|
| [{{site.data.keyword.openwhisk}}](/docs/openwhisk?topic=openwhisk-getting-started) | `functions` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") |  | [Events](/docs/openwhisk?topic=openwhisk-at_events) |
| [{{site.data.keyword.codeenginefull}}](/docs/codeengine?topic=codeengine-getting-started)| `codeengine`  | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Events](/docs/codeengine?topic=codeengine-at_events) |
{: caption="Table 4. List of serverless compute services" caption-side="top"}



## Container services
{: #container}

The following table lists container platform services that send auditing events:

| Service     | CRN service name | {{site.data.keyword.at_short}} hosted event search offering | {{site.data.keyword.atracker_short}} event routing | Events |
|-------------|--------------|------------------|-------------------|--------|
| [{{site.data.keyword.registrylong}}](/docs/Registry?topic=Registry-getting-started) | `container-registry` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events `[*]`](/docs/Registry?topic=Registry-at_events) |
| [{{site.data.keyword.containerlong}}](/docs/containers?topic=containers-getting-started) | `containers-kubernetes` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based event](/docs/containers?topic=containers-at_events) |
| [{{site.data.keyword.openshiftlong}}](/docs/openshift?topic=openshift-getting-started) | `containers-kubernetes` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based event](/docs/openshift?topic=openshift-at_events) |
| [{{site.data.keyword.satellitelong}}](/docs/satellite?topic=satellite-getting-started) | `satellite` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/satellite?topic=satellite-at_events) |
{: caption="Table 3. Container events" caption-side="top"}

`[*]` {{site.data.keyword.registrylong_notm}} generates also global registry events that are available in the region that you configure to collect global auditing events in your account. 


## Database services
{: #database}

The following table lists database services that send auditing events:

| Service     | CRN service name | {{site.data.keyword.at_short}} hosted event search offering | {{site.data.keyword.atracker_short}} event routing | Events |
|-------------|--------------|------------------|-------------------|--------|
| [{{site.data.keyword.cloudantfull}}](/docs/Cloudant?topic=Cloudant-getting-started-with-cloudant) | `cloudantnosqldb`  | ![Checkmark](/images/checkmark-icon.svg "Checkmark")| ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/Cloudant?topic=Cloudant-at_events) |
| [{{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_mongodb_full}}](/docs/hyper-protect-dbaas-for-mongodb?topic=hyper-protect-dbaas-for-mongodb-gettingstarted) | `hyperp-dbaas-mongodb` | ![Checkmark](/images/checkmark-icon.svg "Checkmark")| ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/hyper-protect-dbaas-for-mongodb?topic=hyper-protect-dbaas-for-mongodb-activity-tracker-events) |
| [{{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-gettingstarted) | `hyperp-dbaas-postgresql`| ![Checkmark](/images/checkmark-icon.svg "Checkmark")| ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-activity-tracker-events) |
| [{{site.data.keyword.databases-for-enterprisedb_full}}](/docs/databases-for-enterprisedb?topic=databases-for-enterprisedb-getting-started) | `databases-for-enterprisedb-group` | ![Checkmark](/images/checkmark-icon.svg "Checkmark")|  | [Location-based events](/docs/databases-for-enterprisedb?topic=cloud-databases-activity-tracker) |
| [{{site.data.keyword.databases-for-cassandra_full}}](/docs/databases-for-cassandra?topic=databases-for-cassandra-getting-started) | `databases-for-cassandra-group` | ![Checkmark](/images/checkmark-icon.svg "Checkmark")|  | [Location-based events](/docs/databases-for-cassandra?topic=cloud-databases-activity-tracker) |
| [{{site.data.keyword.databases-for-postgresql_full}}](/docs/databases-for-postgresql?topic=databases-for-postgresql-getting-started) | `databases-for-postgresql` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | | [Location-based events](/docs/databases-for-postgresql?topic=cloud-databases-activity-tracker) | 
| [{{site.data.keyword.databases-for-redis_full_notm}}](/docs/databases-for-redis?topic=databases-for-redis-getting-started) | `databases-for-redis-group` | ![Checkmark](/images/checkmark-icon.svg "Checkmark")|    | [Location-based events](/docs/databases-for-redis?topic=cloud-databases-activity-tracker) |
| [{{site.data.keyword.databases-for-etcd_full_notm}}](/docs/databases-for-etcd?topic=databases-for-etcd-getting-started) | `databases-for-etcd-group` | ![Checkmark](/images/checkmark-icon.svg "Checkmark")|   | [Location-based events](/docs/databases-for-etcd?topic=cloud-databases-activity-tracker) |
| [{{site.data.keyword.databases-for-elasticsearch_full_notm}}](/docs/databases-for-elasticsearch?topic=databases-for-elasticsearch-getting-started) | `databases-for-elasticsearch-group` | ![Checkmark](/images/checkmark-icon.svg "Checkmark")|   | [Location-based events](/docs/databases-for-elasticsearch?topic=cloud-databases-activity-tracker) |
| [{{site.data.keyword.messages-for-rabbitmq_full}}](/docs/messages-for-rabbitmq?topic=messages-for-rabbitmq-getting-started)  | `messages-for-rabbitmq-group` | ![Checkmark](/images/checkmark-icon.svg "Checkmark")|     | [Location-based events](/docs/messages-for-rabbitmq?topic=cloud-databases-activity-tracker) |
| [{{site.data.keyword.Db2_on_Cloud_long}}](/docs/Db2onCloud?topic=Db2onCloud-about) | `db2oncloud` | ![Checkmark](/images/checkmark-icon.svg "Checkmark")|   | [Events](/docs/Db2onCloud?topic=Db2onCloud-activity-tracker) |
{: caption="Table 4. List of database services" caption-side="top"}



## Developer tools
{: #devops}

The following table lists developer tools and DevOps services that send auditing events:

| Service     | CRN service name | {{site.data.keyword.at_short}} hosted event search offering | {{site.data.keyword.atracker_short}} event routing | Events |
|-------------|--------------|------------------|-------------------|--------|
| [{{site.data.keyword.apigw_full}}](/docs/api-gateway?topic=api-gateway-getting-started) | `api-gateway` | ![Checkmark](/images/checkmark-icon.svg "Checkmark")| ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/api-gateway?topic=api-gateway-at_events) |
| [{{site.data.keyword.bplong}}](/docs/schematics?topic=schematics-getting-started)  | `schematics` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/schematics?topic=schematics-at_events) |
| [Apps](/docs/apps?topic=apps-getting-started) | `developer-experience` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/apps?topic=apps-at_events) |
| [{{site.data.keyword.cloud-shell_full}}](/docs/cloud-shell?topic=cloud-shell-getting-started) | `cloudshell` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") |  | [Events](/docs/cloud-shell?topic=cloud-shell-at_events) |
| [{{site.data.keyword.contdelivery_full}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-getting-started) | `continuous-delivery` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") |  | [Location-based events for {{site.data.keyword.contdelivery_short}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-at-events#cd-events) \n [Location-based events for toolchains](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-at-events#toolchain-events) \n [Location-based events for {{site.data.keyword.DRA_short}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-at-events#insights-events) \n [Location-based events for {{site.data.keyword.deliverypipeline}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-at-events#pipeline-events) \n [Location-based events for Eclipse Orion {{site.data.keyword.webide}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-at-events#webide-events)|
| [{{site.data.keyword.mobilepushfull}}](/docs/mobilepush?topic=mobilepush-getting-started) | `imfpush` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") |  | [Events](/docs/mobilepush?topic=mobilepush-at_events#at_actions) |
| [{{site.data.keyword.en_full}}](/docs/event-notifications?topic=event-notifications-getting-started) | `event-notifications`|![Checkmark](/images/checkmark-icon.svg "Checkmark") |  | [Events](/docs/event-notifications?topic=event-notifications-en-at_events)|
| [{{site.data.keyword.appconfig_full}}](/docs/app-configuration?topic=app-configuration-getting-started) | `apprapp`|![Checkmark](/images/checkmark-icon.svg "Checkmark") |  | [Location-based events](/docs/app-configuration?topic=app-configuration-ac-at_events)|
{: caption="Table 5. List of developer tools services" caption-side="top"}


## Integration services
{: #integration}

The following table lists integration services that send auditing events:

| Service     | CRN service name | {{site.data.keyword.at_short}} hosted event search offering | {{site.data.keyword.atracker_short}} event routing | Events |
|-------------|--------------|------------------|-------------------|--------|
| [{{site.data.keyword.messagehub_full}}](/docs/EventStreams?topic=EventStreams-getting_started)| `event-streams` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/EventStreams?topic=EventStreams-at_events) |
| [MQ on IBM Cloud](/docs/mqcloud?topic=mqcloud-mqoc_getting_started) |`mqcloud` |![Checkmark](/images/checkmark-icon.svg "Checkmark") | | [Location-based events](/docs/mqcloud?topic=mqcloud-at_events) |
{: caption="Table 6. List of integration Cloud services" caption-side="top"}



## Network services
{: #network}

The following table lists network services that send auditing events:

| Service     | CRN service name | {{site.data.keyword.at_short}} hosted event search offering | {{site.data.keyword.atracker_short}} event routing | Events |
|-------------|--------------|------------------|-------------------|--------|
| [{{site.data.keyword.BluDirectLink}} solution](/docs/dl?topic=dl-get-started-with-ibm-cloud-dl) | `directlink.dedicated` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Global events](/docs/dl?topic=dl-at_events) |
| [{{site.data.keyword.tg_full}}](/docs/transit-gateway?topic=transit-gateway-getting-started) | `transit` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Global events](/docs/transit-gateway?topic=transit-gateway-at_events) |
| [{{site.data.keyword.dns_full}}](/docs/dns-svcs?topic=dns-svcs-getting-started) | `dns-svcs` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Global events](/docs/dns-svcs?topic=dns-svcs-at_events) |
| [{{site.data.keyword.cis_full}} (CIS)](/docs/cis?topic=cis-getting-started)| `internet-svcs` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Global events](/docs/cis?topic=cis-at_events) |
| [Content Delivery Network](/docs/CDN#getting-started) | `cdn-powered-by-akamai` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | | [Events](/docs/CDN?topic=CDN-at_events)|
{: caption="Table 7. List of network services" caption-side="top"}

## Observabiliy services
{: observability}

The following table lists observability services that send auditing events:

| Service     | CRN service name | {{site.data.keyword.at_short}} hosted event search offering | {{site.data.keyword.atracker_short}} event routing | Events |
|-------------|--------------|------------------|-------------------|--------|
| [{{site.data.keyword.atracker_full}} event routing](/docs/activity-tracker?topic=activity-tracker-getting-started) | `atracker` |  | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/activity-tracker?topic=activity-tracker). |
| [{{site.data.keyword.at_full}} hosted event search offering](/docs/activity-tracker?topic=activity-tracker-getting-started) | `logdnaat` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") |  | [Location-based events](/docs/activity-tracker?topic=activity-tracker-at_events) |
| [{{site.data.keyword.la_full}}](/docs/log-analysis?topic=log-analysis-getting-started#getting-started) | `logdna` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") |  | [Location-based events](/docs/log-analysis?topic=log-analysis-at_events) |
| [{{site.data.keyword.mon_full}}](/docs/monitoring?topic=monitoring-getting-started) | `sysdig-monitor` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") |  | [Location-based events](/docs/monitoring?topic=monitoring-at_events) |
{: caption="Table 8. List of observability services" caption-side="top"} 


## Platform services
{: #platform_core_integrated}

The following table lists platform services that send auditing events:

| Service     | CRN service name | {{site.data.keyword.at_short}} hosted event search offering | {{site.data.keyword.atracker_short}} event routing | Events |
|-------------|--------------|------------------|-------------------|--------|
| [BSS - Account and billing](/docs/account?topic=account-accounts#accounts) | `billing` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Global events](/docs/activity-tracker?topic=activity-tracker-at_events_acc_mgt#at_events_acc_mgt_account) |
| [BSS - User management](/docs/account?topic=account-assign-access-resources) | `user-management` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Global events](/docs/activity-tracker?topic=activity-tracker-at_events_acc_mgt#at_events_acc_mgt_users) |
| [BSS - Provisioning](/docs/overview?topic=overview-ui#catalogcreate) | `provisioning` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Global events](/docs/activity-tracker?topic=activity-tracker-at_events_rc#at_events_rc) |
| [{{site.data.keyword.iamlong}}](/docs/account?topic=account-iamoverview)   | `iam-identity`   \n `iam-groups`   \n `iam-am`   \n `iam-trustedprofiles` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Global events](/docs/activity-tracker?topic=activity-tracker-at_events_iam) |
| [{{site.data.keyword.compliance_full}}](/docs/security-compliance?topic=security-compliance-getting-started) | `compliance` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Global events](/docs/security-compliance?topic=security-compliance-at_events) |
| [{{site.data.keyword.security-advisor_long}}](/docs/security-advisor?topic=security-advisor-getting-started) | `security-advisor` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Global events](/docs/security-compliance?topic=security-compliance-at_events#at_actions_insights) |
| [Global Search Service](/docs/account?topic=account-tag) | `global-search-tagging` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Global events](/docs/activity-tracker?topic=activity-tracker-at_events_acc_mgt#at_events_acc_mgt_resources) |
| [Catalog](/docs/account?topic=account-filter-account) | `globalcatalog-collection` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Global events](/docs/activity-tracker?topic=activity-tracker-at_events_acc_mgt#at_events_catalog_management) |
| [Software instances](/docs/account?topic=account-sw-instance-details) | `globalcatalog-instance` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Global events](/docs/activity-tracker?topic=activity-tracker-at_events_acc_mgt#at_events_sw_instance) |
{: caption="Table 9. List of platform services" caption-side="top"}

For example, the following table lists core security actions that send events to {{site.data.keyword.at_full_notm}}:

| Service     | {{site.data.keyword.at_short}} hosted event search offering | {{site.data.keyword.atracker_short}} event routing | Events |
|-------------|------------------|-------------------|--------|
| [Managing access groups](/docs/account?topic=account-groups#groups) | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Events that are generated when you manage access groups](/docs/activity-tracker?topic=activity-tracker-at_events_iam#at_events_iam_access) |
| [Managing policies](/docs/account?topic=account-userroles#userroles) | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Events that are generated when you manage IAM policies](/docs/activity-tracker?topic=activity-tracker-at_events_iam#at_events_iam_policies) |
| [Log in to the {{site.data.keyword.cloud_notm}}](/docs/account?topic=account-iamoverview#iamoverview)| ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Events that are generated when a user or app logs in to the {{site.data.keyword.cloud_notm}}](/docs/activity-tracker?topic=activity-tracker-at_events_iam#at_events_iam_login) |
| [Managing platform API keys](/docs/account?topic=account-manapikey#manapikey) |![Checkmark](/images/checkmark-icon.svg "Checkmark")  | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Events that are generated when you manage Platform API keys](/docs/activity-tracker?topic=activity-tracker-at_events_iam#at_events_iam_apikeys) |
| [Managing service IDs](/docs/account?topic=account-serviceids#serviceids) | ![Checkmark](/images/checkmark-icon.svg "Checkmark") |![Checkmark](/images/checkmark-icon.svg "Checkmark")  | [Events that are generated when you manage service IDs](/docs/activity-tracker?topic=activity-tracker-at_events_iam#at_events_iam_serviceids) |
{: caption="Table 10. List of core security platform services" caption-side="top"}

## Security services
{: #security}

The following table lists security Cloud services that send auditing events:


| Service     | CRN service name | {{site.data.keyword.at_short}} hosted event search offering | {{site.data.keyword.atracker_short}} event routing | Events |
|-------------|--------------|------------------|-------------------|--------|
| [{{site.data.keyword.appid_full}}](/docs/appid?topic=appid-getting-started) | `appid` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/appid?topic=appid-at-events)   |
| [{{site.data.keyword.keymanagementservicelong}}](/docs/key-protect?topic=key-protect-getting-started-tutorial#getting-started-tutorial) | `kms` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/key-protect?topic=key-protect-at-events) |
| [{{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}}](/docs/hs-crypto?topic=hs-crypto-get-started) | `hs-crypto` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/hs-crypto?topic=hs-crypto-at-events) |
| [{{site.data.keyword.secrets-manager_full}}](/docs/secrets-manager?topic=secrets-manager-getting-started) | `secrets-manager` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/secrets-manager?topic=secrets-manager-at-events) |
| [{{site.data.keyword.cloudcerts_full}}](/docs/certificate-manager?topic=certificate-manager-about-certificate-manager#about-certificate-manager) | `cloudcerts` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | | [Location-based events](/docs/certificate-manager?topic=certificate-manager-at_events#at_events) |
{: caption="Table 11. List of security services" caption-side="top"}



## Storage services
{: #storage}


The following table lists storage services that send auditing events:

| Service     | CRN service name | {{site.data.keyword.at_short}} hosted event search offering | {{site.data.keyword.atracker_short}} event routing | Events |
|-------------|--------------|------------------|-------------------|--------|
| [{{site.data.keyword.cos_full}}](/docs/cloud-object-storage?topic=cloud-object-storage-getting-started-cloud-object-storage)| `cloud-object-storage` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Global and location-based events `[*]`](/docs/cloud-object-storage?topic=cloud-object-storage-at-events) |
| [{{site.data.keyword.mdms_short}}](/docs/mass-data-migration?topic=mass-data-migration-getting-started-tutorial)| `mass-data-migration` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Events](/docs/mass-data-migration?topic=mass-data-migration-at-events) |
{: caption="Table 12. List of storage events" caption-side="top"}


`[*]` {{site.data.keyword.cos_full_notm}} (COS) generates global, and location-based events.
* By default, bucket management events such as the creation of a bucket are collected automatically.
* Collection of data events in your account is optional. You must configure each bucket to enable data events by selecting the option **Track data events**.
* {{site.data.keyword.mdms_short}} generates global events only, for each transition of the order state.


## VMware Solutions
{: #vmware_solutions}

With {{site.data.keyword.vmwaresolutions_full_notm}}, you can quickly and seamlessly integrate or migrate your on-premises VMware workloads to the {{site.data.keyword.cloud_notm}} by using the scalable, secure, and high-performance {{site.data.keyword.cloud_notm}} infrastructure and the industry-leading VMware hybrid virtualization technology. You can easily deploy your VMware virtual environments and manage the infrastructure resources on {{site.data.keyword.cloud_notm}}. At the same time, you can still use your familiar native VMware product console to manage the VMware workloads. [Learn more](https://www.ibm.com/cloud/vmware){: external}.

The following table lists VMware solution services that send auditing events:

| Service     | CRN service name | {{site.data.keyword.at_short}} hosted event search offering | {{site.data.keyword.atracker_short}} event routing | Events |
|-------------|--------------|------------------|-------------------|--------|
| [{{site.data.keyword.vmwaresolutions_short}}](/docs/vmwaresolutions?topic=vmwaresolutions-vc_vcenterserveroverview)   | `vmware-solutions` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Global events](/docs/vmwaresolutions?topic=vmwaresolutions-at-events#at-events) |
| [{{site.data.keyword.cloud}} for VMware® Solutions Shared](/docs/vmwaresolutions?topic=vmwaresolutions-shared_overview)      | `vmware-solutions` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/vmwaresolutions?topic=vmwaresolutions-at-events#at-events-instance-mgmt) |
| [KMIP for VMware](/docs/vmwaresolutions?topic=vmwaresolutions-kmip_standalone_considerations) | `vmware-solutions` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/vmwaresolutions?topic=vmwaresolutions-at-events#at-events-kmip) |
{: caption="Table 13. List of VMware solution services" caption-side="top"}




## VPC services
{: #vpc_services}

You can provision a Virtual Private Cloud (VPC) in the {{site.data.keyword.cloud_notm}} to run an isolated environment within the public cloud. VPC gives you the security of a private cloud, with the agility and ease of a public cloud. See [{{site.data.keyword.vpc_full}} Gen 2](/docs/vpc?topic=vpc-getting-started).


The following table lists VPC infrastructure services that send auditing events:

| Service     | Service name | {{site.data.keyword.at_short}} hosted event search offering | {{site.data.keyword.atracker_short}} event routing | Events |
|-------------|--------------|------------------|-------------------|--------|
| [Storage resources](/docs/vpc?topic=vpc-block-storage-about) | `is.volume` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/vpc?topic=vpc-at-events#events-storage) |
| [Compute resources](/docs/vpc?topic=vpc-about-advanced-virtual-servers) | `is.instance` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/vpc?topic=vpc-at-events#events-compute) |
| [Network resources](/docs/vpc?topic=vpc-about-networking-for-vpc) | `is.subnet` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/vpc?topic=vpc-at-events#events-network) |
| [Load Balancer](/docs/vpc?topic=vpc-load-balancers)| `is.load-balancer` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/vpc?topic=vpc-at-events#events-load-balancers) |
| [VPN](/docs/vpc?topic=vpc-using-vpn)| `is.vpn` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/vpc?topic=vpc-at-events#at-events) |
| [Images](/docs/vpc?topic=vpc-about-images) | `is.image` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/vpc?topic=vpc-at-events#events-images) |
{: caption="Table 14. List of VPC infrastructure services (generation 2)" caption-side="top"}

## Watson AI
{: #watson_ai}

The following table lists Watson AI services that send auditing events:

| Service     | CRN service name | {{site.data.keyword.at_short}} hosted event search offering | {{site.data.keyword.atracker_short}} event routing | Events |
|-------------|--------------|------------------|-------------------|--------|
| [{{site.data.keyword.conversationfull}}](/docs/assistant?topic=assistant-getting-started) | `conversation`  | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | | [Location-based events](/docs/assistant?topic=assistant-at-events) |
| [{{site.data.keyword.discoveryfull}}](/docs/discovery?topic=discovery-getting-started) | `discovery` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | | [Location-based events](/docs/discovery?topic=discovery-at_events)  |
| [{{site.data.keyword.cncfull}}](/docs/compare-comply?topic=compare-comply-about)  | `compare-comply` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | | [Location-based events](/docs/compare-comply?topic=compare-comply-at_events) |
| [{{site.data.keyword.DSX_full}}](https://dataplatform.cloud.ibm.com/docs/content/wsj/getting-started/overview-ws.html) | `data-science-experience`  | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | | [Location-based events](https://dataplatform.cloud.ibm.com/docs/content/wsj/admin/at-events.html#ws) |
| [IBM Watson&trade; Knowledge Catalog](https://dataplatform.cloud.ibm.com/docs/content/wsj/catalog/overview-wkc.html) | `datacatalog` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | | [Location-based events](https://dataplatform.cloud.ibm.com/docs/content/wsj/admin/at-events.html#wkc) |
| [{{site.data.keyword.knowledgestudiofull}}](/docs/watson-knowledge-studio) | `knowledge-studio` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | | [Location-based events](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-activity-tracker-events) |
| [{{site.data.keyword.languagetranslatorfull}}](/docs/language-translator?topic=language-translator-gettingstarted) | `language-translator` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | | [Location-based events](/docs/language-translator?topic=language-translator-at_events) |
| [{{site.data.keyword.pm_full}}](https://dataplatform.cloud.ibm.com/docs/content/wsj/analyze-data/ml-overview.html) | `pm-20` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | | [Location-based events](https://dataplatform.cloud.ibm.com/docs/content/wsj/admin/at-events.html#wml) |
| [{{site.data.keyword.nlclassifierfull}}](/docs/natural-language-classifier?topic=natural-language-classifier-natural-language-classifier) | `natural-language-classifier` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | | [Location-based events](/docs/natural-language-classifier?topic=natural-language-classifier-at_events) |
| [{{site.data.keyword.nlufull}}](/docs/natural-language-understanding) | `natural-language-understanding` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | | [Location-based events](/docs/natural-language-understanding?topic=natural-language-understanding-at_events) |
| [{{site.data.keyword.speechtotextfull}}](/docs/speech-to-text?topic=speech-to-text-gettingStarted) | `speech-to-text` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | | [Location-based events](/docs/speech-to-text?topic=speech-to-text-atEvents) |
| [{{site.data.keyword.texttospeechfull}}](/docs/text-to-speech?topic=text-to-speech-gettingStarted) | `text-to-speech` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | | [Location-based events](/docs/text-to-speech?topic=text-to-speech-atEvents) |
| [{{site.data.keyword.visualrecognitionfull}}](/docs/visual-recognition?topic=visual-recognition-index) | `watson-vision-combined` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | | [Location-based events](/docs/visual-recognition?topic=visual-recognition-at_events) |
| [{{site.data.keyword.wh-acd_full}}](/docs/wh-acd?topic=wh-acd-getting-started) | `wh-acd` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | | [Location-based events](/docs/wh-acd?topic=wh-acd-at_events) |
{: caption="Table 15. List of Watson AI services" caption-side="top"}

## Web and mobile services
{: #web}

The following table lists web and mobile services that send auditing events:

| Service     | CRN service name | {{site.data.keyword.at_short}} hosted event search offering | {{site.data.keyword.atracker_short}} event routing | Events |
|-------------|--------------|------------------|-------------------|--------|
| [{{site.data.keyword.mobilefoundation_long}}](/docs/mobilefoundation?topic=mobilefoundation-getting-started)| `mobile-foundation` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/mobilefoundation?topic=mobilefoundation-mfp_activity_tracker) |
{: caption="Table 16. List of web and mobile events" caption-side="top"}



## Power IaaS services
{: #power_iaas_services}

Power Systems Virtual Server (PowerVS) projects deliver flexible compute capacity for Power Systems workloads. Integrated with the {{site.data.keyword.cloud_notm}} platform for on-demand provisioning, this offering provides a secure and scalable server virtualization environment that is built upon the advanced RAS features and leading performance of the Power Systems™ platform. See [{{site.data.keyword.power-iaas_full}} Power-IaaS](/docs/power-iaas?topic=power-iaas).


The following table lists Power IaaS infrastructure services that send auditing events:

| Service     | Service name | {{site.data.keyword.at_short}} hosted event search offering | {{site.data.keyword.atracker_short}} event routing | Events |
|-------------|--------------|------------------|-------------------|--------|
| [Images](/docs/power-iaas?topic=power-iaas-deploy-custom-image) | `pcloud.images` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](docs/power-iaas?topic=power-iaas-at-events#at-actions-images) |
| [Networks](/docs/power-iaas?topic=power-iaas-connecting-networks) | `pcloud.networks` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/power-iaas?topic=power-iaas-at-events#at-actions-networks) |
| [PVM-Instance](/docs/power-iaas?topic=power-iaas-creating-power-virtual-server) | `pcloud.pvm-instance` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/power-iaas?topic=power-iaas-at-events#at-actions-servers) |
| [Volumes](/docs/power-iaas?topic=power-iaas-modifying-server#modifying-volume-network) | `pcloud.volumes` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/power-iaas?topic=power-iaas-at-events#at-actions-volumes) |
| [VPN](/docs/power-iaas?topic=power-iaas-vpn-connectivity) | `pcloud.vpn-connection` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/power-iaas?topic=power-iaas-at-events#at-vpn-connection) |
| [PlacementGroups](/docs/power-iaas?topic=power-iaas-placement-groups) | `pcloud.placement-groups` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/power-iaas?topic=power-iaas-at-events#at-placement-groups) |
| [CloudConnections](/docs/power-iaas?topic=power-iaas-cloud-connections) | `pcloud.cloud-connection` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/power-iaas?topic=power-iaas-at-events#at-cloud-connection) |
| [SAP](/docs/power-iaas?topic=power-iaas-about-virtual-server#support-SAPNetWeaver-or-SAPHANA) | `pcloud.sap` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/power-iaas?topic=power-iaas-at-events#at-sap) |
| [NetworkPorts](/docs/power-iaas?topic=power-iaas-configuring-subnet) | `pcloud.port` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/power-iaas?topic=power-iaas-at-events#at-network-ports) |
| [Tenant](/docs/power-iaas?topic=power-iaas-managing-resources-and-users) | `pcloud.tenant` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/power-iaas?topic=power-iaas-at-events#at-tenants) |
| [SSHKeys](https://test.cloud.ibm.com/docs/power-iaas?topic=power-iaas-create-vm) | `pcloud.ssh-key` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/power-iaas?topic=power-iaas-at-events#at-actions-ssh) |
| [IKE](https://test.cloud.ibm.com/docs/power-iaas?topic=power-iaas-ordering-direct-link-connect) | `pcloud.ike-policy` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/power-iaas?topic=power-iaas-at-events#at-actions-ssh) |
| [IPSec](https://test.cloud.ibm.com/docs/power-iaas?topic=power-iaas-ordering-direct-link-connect) | `pcloud.ipsec-policy` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/power-iaas?topic=power-iaas-at-events#at-actions-ssh) |
{: caption="Table 17. List of Power Iaas infrastructure services" caption-side="top"}

