---

copyright:
  years: 2019, 2020
lastupdated: "2020-02-03"

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


# Cloud services by location
{: #cloud_services_locations}

List of locations where {{site.data.keyword.cloud}} services are enabled to send logs to {{site.data.keyword.at_full_notm}}. [Learn more about enabling service platform logs](/docs/services/Log-Analysis-with-LogDNA?topic=LogDNA-config_svc_logs).
{:shortdesc}


## Compute VMware solution services
{: #cloud_services_locations_vmware}

| Service                                        | `Dallas (us-south)` | `Washington (us-east)`               |
|------------------------------------------------|:-------------------:|:------------------------------------:|
| Management actions                             |                     |                                      |        
| KMIP for VMware                                |                     |                                      |  
{: caption="Compute VMware services integration in America's locations" caption-side="top"}
{: #cs_vm-table-1}
{: tab-title="America"}
{: tab-group="cs_vm"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                        | `Tokyo (jp-tok)` |`Sydney (au-syd)`           |
|------------------------------------------------|:----------------:|:--------------------------:|
| Management actions                             |                     |                                      |        
| KMIP for VMware                                |                     |                                      |  
{: caption="Compute VMware services integration in AP locations" caption-side="top"}
{: #cs_vm-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="cs_vm"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                                       |`Frankfurt (eu-de)`  | `London (eu-gb)` |
|---------------------------------------------------------------|:-------------------:|:----------------:|
| Management actions                             |                     |                                      |        
| KMIP for VMware                                |                     |                                      |  
{: caption="Compute VMware services integration in Europe locations" caption-side="top"}
{: #cs_vm-table-3}
{: tab-title="Europe"}
{: tab-group="cs_vm"}
{: class="simple-tab-table"}
{: row-headers}


## Compute infrastructure services
{: #cloud_services_locations_infrastructure}

| Service                                        | `Dallas (us-south)` | `Washington (us-east)`               |
|------------------------------------------------|:-------------------:|:------------------------------------:|
| {{site.data.keyword.BluVirtServers_short}}     |                     |                                      |        
| {{site.data.keyword.baremetal_long}}           |                     |                                      |  
{: caption="Compute infrastructure services integration in America's locations" caption-side="top"}
{: #cs_infra-table-1}
{: tab-title="America"}
{: tab-group="cs_infra"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                        | `Tokyo (jp-tok)` |`Sydney (au-syd)`           |
|------------------------------------------------|:----------------:|:--------------------------:|
| {{site.data.keyword.BluVirtServers_short}}     |                     |                                      |        
| {{site.data.keyword.baremetal_long}}           |                     |                                      |  
{: caption="Compute infrastructure services integration in AP locations" caption-side="top"}
{: #cs_infra-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="cs_infra"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                                       |`Frankfurt (eu-de)`  | `London (eu-gb)` |
|---------------------------------------------------------------|:-------------------:|:----------------:|
| {{site.data.keyword.BluVirtServers_short}}     |                     |                                      |        
| {{site.data.keyword.baremetal_long}}           |                     |                                      |  
{: caption="Compute infrastructure services integration in Europe locations" caption-side="top"}
{: #cs_infra-table-3}
{: tab-title="Europe"}
{: tab-group="cs_infra"}
{: class="simple-tab-table"}
{: row-headers}

## Compute serverless services
{: #cloud_services_locations_serverless}

| Service                                        | `Dallas (us-south)` | `Washington (us-east)`               |
|------------------------------------------------|:-------------------:|:------------------------------------:|
| {{site.data.keyword.openwhisk_short}}          |                     |                                      |          
{: caption="Compute serverless services integration in America's locations" caption-side="top"}
{: #cs_comp-table-1}
{: tab-title="America"}
{: tab-group="cs_comp"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                        | `Tokyo (jp-tok)` |`Sydney (au-syd)`           |
|------------------------------------------------|:----------------:|:--------------------------:|
| {{site.data.keyword.openwhisk_short}}          |                     |                                      |
{: caption="Compute serverless services integration in AP locations" caption-side="top"}
{: #cs_comp-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="cs_comp"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                                       |`Frankfurt (eu-de)`  | `London (eu-gb)` |
|---------------------------------------------------------------|:-------------------:|:----------------:|
| {{site.data.keyword.openwhisk_short}}          |                     |                                      |
{: caption="Compute serverless services integration in Europe locations" caption-side="top"}
{: #cs_comp-table-3}
{: tab-title="Europe"}
{: tab-group="cs_comp"}
{: class="simple-tab-table"}
{: row-headers}


## Compute: Cloud Foundry
{: #cloud_services_locations_cfapps}

The following table shows the locations where automatic collection of Cloud Foundry (CF) logs is enabled. You can monitor these logs through the {{site.data.keyword.at_full_notm}}  instance that is configured with the **service platform logs** in the same location where the CF resource is available.

| Service                                                       | `Dallas (us-south)` |
|---------------------------------------------------------------|:--------------------:|
| Cloud Foundry (CF)                                            | ![Checkmark icon](../../icons/checkmark-icon.svg)              |
{: caption="Cloud Foundry in America" caption-side="top"}
{: #cs-cfapps-table-1}
{: tab-title="America"}
{: tab-group="cs_cfapps"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                                       | `Tokyo (jp-tok)` |
|---------------------------------------------------------------|:----------------:|
| Cloud Foundry (CF)                                            | ![Checkmark icon](../../icons/checkmark-icon.svg)            |
{: caption="Cloud Foundry in Asia Pacific" caption-side="top"}
{: #cs-cfapps-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="cs_cfapps"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                                       | `Frankfurt (eu-de)` | `London (eu-gb)` |
|---------------------------------------------------------------|:-------------------:|:----------------:|
| Cloud Foundry (CF)                                            | ![Checkmark icon](../../icons/checkmark-icon.svg) | ![Checkmark icon](../../icons/checkmark-icon.svg)  |
{: caption="Cloud Foundry in Europe" caption-side="top"}
{: #cs-cfapps-table-3}
{: tab-title="Europe"}
{: tab-group="cs_cfapps"}
{: class="simple-tab-table"}
{: row-headers}



## Platform container services
{: #cloud_services_locations_container}

| Service                                        | `Dallas (us-south)` | `Washington (us-east)`               |
|------------------------------------------------|:-------------------:|:------------------------------------:|
| {{site.data.keyword.registrylong_notm}}        | ![Checkmark icon](../../icons/checkmark-icon.svg) | `No` |          
| {{site.data.keyword.containerlong_notm}}       |                     |                                      |
{: caption="Container services integration in America's locations" caption-side="top"}
{: #cs_container-table-1}
{: tab-title="America"}
{: tab-group="cs_container"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                        | `Tokyo (jp-tok)` |`Sydney (au-syd)`           |
|------------------------------------------------|:----------------:|:--------------------------:|
| {{site.data.keyword.registrylong_notm}}        | ![Checkmark icon](../../icons/checkmark-icon.svg) | `Events are available through the Activity Tracker Tokyo (jp-tok) instance` |          
| {{site.data.keyword.containerlong_notm}}       |                     |                                      |
{: caption="Container services integration in AP locations" caption-side="top"}
{: #cs_container-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="cs_container"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                                       |`Frankfurt (eu-de)`  | `London (eu-gb)` |
|---------------------------------------------------------------|:-------------------:|:----------------:|
| {{site.data.keyword.registrylong_notm}}        | ![Checkmark icon](../../icons/checkmark-icon.svg) | ![Checkmark icon](../../icons/checkmark-icon.svg) |          
| {{site.data.keyword.containerlong_notm}}       |                     |                                      |
{: caption="Container services integration in Europe locations" caption-side="top"}
{: #cs_container-table-3}
{: tab-title="Europe"}
{: tab-group="cs_container"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                                       | Global |
|---------------------------------------------------------------|:-------------------:|
| {{site.data.keyword.registrylong_notm}}        | `Events are available through the Activity Tracker Dallas (us-south) instance` |          
| {{site.data.keyword.containerlong_notm}}       |                     |
{: caption="Container services integration in Global" caption-side="top"}
{: #cs_container-table-3}
{: tab-title="Global"}
{: tab-group="cs_container"}
{: class="simple-tab-table"}
{: row-headers}


## Platform core integrated services
{: #cloud_services_locations_core_integrated}

| Service                                        | `Dallas (us-south)` | `Washington (us-east)`               |
|------------------------------------------------|:-------------------:|:------------------------------------:|
| Managing an account                            |                     |                                      |          
| Managing users                                 |                     |                                      |
| Managing organizations                         |                     |                                      |
| Provisioning and managing catalog {{site.data.keyword.iamshort}} (IAM) enabled services  |                     |                                      |
| Working with service aliases                   |                     |                                      |
| Working with service credentials               |                     |                                      |
| Binding a service instance to an app           |                     |                                      |
| Managing tags                                  |                     |                                      |
{: caption="Core integrated services integration in America's locations" caption-side="top"}
{: #cs_int_core-table-1}
{: tab-title="America"}
{: tab-group="cs_int_core"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                        | `Tokyo (jp-tok)` |`Sydney (au-syd)`           |
|------------------------------------------------|:----------------:|:--------------------------:|
| Managing an account                            |                     |                                      |          
| Managing users                                 |                     |                                      |
| Managing organizations                         |                     |                                      |
| Provisioning and managing catalog {{site.data.keyword.iamshort}} (IAM) enabled services  |                     |                                      |
| Working with service aliases                   |                     |                                      |
| Working with service credentials               |                     |                                      |
| Binding a service instance to an app           |                     |                                      |
| Managing tags                                  |                     |                                      |
{: caption="Core integrated services integration in AP locations" caption-side="top"}
{: #cs_int_core-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="cs_int_core"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                                       |`Frankfurt (eu-de)`  | `London (eu-gb)` |
|---------------------------------------------------------------|:-------------------:|:----------------:|
| Managing an account                            |                     |                                      |          
| Managing users                                 |                     |                                      |
| Managing organizations                         |                     |                                      |
| Provisioning and managing catalog {{site.data.keyword.iamshort}} (IAM) enabled services  |                     |                                      |
| Working with service aliases                   |                     |                                      |
| Working with service credentials               |                     |                                      |
| Binding a service instance to an app           |                     |                                      |
| Managing tags                                  |                     |                                      |
{: caption="Core integrated services integration in Europe locations" caption-side="top"}
{: #cs_int_core-table-3}
{: tab-title="Europe"}
{: tab-group="cs_int_core"}
{: class="simple-tab-table"}
{: row-headers}

## Platform: Database services
{: #cloud_services_locations_database}

The following tables list the locations where automatic collection of database service logs is enabled. You can monitor logs through the Log Analysis instance that is available in the same location as your database resources, if you enable 1 instance in this location to host service platform logs. For locations where you can provision a service instance but the {{site.data.keyword.at_full_notm}} service is not available, specific detail about the location where you can monitor those logs is provided in each case.

| Service                                                         | `Dallas (us-south)` | `Washington (us-east)`  |
|-----------------------------------------------------------------|:-------------------:|:-------------------:|
| {{site.data.keyword.cloudant_short_notm}}                       | ![Checkmark icon](../../icons/checkmark-icon.svg) `(beta)`        | `NO`                |
| {{site.data.keyword.databases-for-elasticsearch_full_notm}}     | ![Checkmark icon](../../icons/checkmark-icon.svg)               | `NO`                |
| {{site.data.keyword.databases-for-etcd_full_notm}}              | ![Checkmark icon](../../icons/checkmark-icon.svg)               | `NO`                |
| {{site.data.keyword.databases-for-mongodb_full_notm}}           | ![Checkmark icon](../../icons/checkmark-icon.svg)               | `NO`                |
| {{site.data.keyword.databases-for-postgresql_full_notm}}        | ![Checkmark icon](../../icons/checkmark-icon.svg)`               | `NO`                |
| {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_mongodb_full}}        | ![Checkmark icon](../../icons/checkmark-icon.svg)               | `NO`                |
| {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}        | ![Checkmark icon](../../icons/checkmark-icon.svg)               | `NO`                |
| {{site.data.keyword.messages-for-rabbitmq_full_notm}}           | ![Checkmark icon](../../icons/checkmark-icon.svg)               | `NO`                |
| {{site.data.keyword.databases-for-redis_full_notm}}             | ![Checkmark icon](../../icons/checkmark-icon.svg)               | `NO`                |
{: caption="Database services integration in America's locations" caption-side="top"}
{: #cs-dbs-table-1}
{: tab-title="America"}
{: tab-group="cs_dbs"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                                         | `Tokyo (jp-tok)`   |`Sydney (au-syd)` | `Seoul 01 (seo01)`       | `Chennai 01 (che01)`     |
|-----------------------------------------------------------------|:------------------:|:----------------:|:-------------------------|:-------------------------|
| {{site.data.keyword.cloudant_short_notm}}                       | `NO`               | `NO`             | `NO`                     | `NO`                     |
| {{site.data.keyword.databases-for-elasticsearch_full_notm}}     | ![Checkmark icon](../../icons/checkmark-icon.svg)   | `NO`             | `Events are available through the Log Analysis Tokyo instance` | `Events are available through the Log Analysis Tokyo instance` |
| {{site.data.keyword.databases-for-etcd_full_notm}}              | ![Checkmark icon](../../icons/checkmark-icon.svg)   | `NO`             | `Events are available through the Log Analysis Tokyo instance` | `Events are available through the Log Analysis Tokyo instance` |
| {{site.data.keyword.databases-for-mongodb_full_notm}}           | ![Checkmark icon](../../icons/checkmark-icon.svg)    | `NO`             | `Events are available through the Log Analysis Tokyo instance` | `Events are available through the Log Analysis Tokyo instance` |
| {{site.data.keyword.databases-for-postgresql_full_notm}}        | ![Checkmark icon](../../icons/checkmark-icon.svg)    | `NO`             | `Events are available through the Log Analysis Tokyo instance` | `Events are available through the Log Analysis Tokyo instance` |
| {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_mongodb_full}}          | `NO`               | `Events are available through the Log Analysis Dallas instance`             | `NO`                     | `NO`                     |
| {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}       | `NO`               | `Events are available through the Log Analysis Dallas instance`             | `NO`                     | `NO`                     |
| {{site.data.keyword.messages-for-rabbitmq_full_notm}}           | ![Checkmark icon](../../icons/checkmark-icon.svg)    | `NO`             | `Events are available through the Log Analysis Tokyo instance` | `Events are available through the Log Analysis Tokyo instance` |
| {{site.data.keyword.databases-for-redis_full_notm}}             | ![Checkmark icon](../../icons/checkmark-icon.svg)    | `NO`             | `Events are available through the Log Analysis Tokyo instance` | `Events are available through the Log Analysis Tokyo instance` |
{: caption="Database services integration in AP locations" caption-side="top"}
{: #cs-dbs-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="cs_dbs"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                                       |`Frankfurt (eu-de)`  | `London (eu-gb)` | `Oslo 01 (osl01)`         |
|---------------------------------------------------------------|:-------------------:|:----------------:|:-------------------------:|
| {{site.data.keyword.cloudant_short_notm}}                     | `NO`                | `NO`             | `NO`                      |
| {{site.data.keyword.databases-for-elasticsearch_full_notm}}   | `NO`                | ![Checkmark icon](../../icons/checkmark-icon.svg)            | `Events are available through the Log Analysis London instance` |
| {{site.data.keyword.databases-for-etcd_full_notm}}            | `NO`                | ![Checkmark icon](../../icons/checkmark-icon.svg)            | `Events are available through the Log Analysis London instance` |
| {{site.data.keyword.databases-for-mongodb_full_notm}}         | `NO`                | ![Checkmark icon](../../icons/checkmark-icon.svg)            | `Events are available through the Log Analysis London instance` |
| {{site.data.keyword.databases-for-postgresql_full_notm}}      | `NO`                | ![Checkmark icon](../../icons/checkmark-icon.svg)            | `Events are available through the Log Analysis London instance` |
| {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_mongodb_full}}        | ![Checkmark icon](../../icons/checkmark-icon.svg)                | `NO`             | `NO`  |
| {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}     | ![Checkmark icon](../../icons/checkmark-icon.svg)                | `NO`             | `NO`  |
| {{site.data.keyword.messages-for-rabbitmq_full_notm}}         | `NO`                | ![Checkmark icon](../../icons/checkmark-icon.svg)            | `Events are available through the Log Analysis London instance` |
| {{site.data.keyword.databases-for-redis_full_notm}}           | `NO`                | ![Checkmark icon](../../icons/checkmark-icon.svg)            | `Events are available through the Log Analysis London instance` |
{: caption="Database services integration in Europe locations" caption-side="top"}
{: #cs-dbs-table-3}
{: tab-title="Europe"}
{: tab-group="cs_dbs"}
{: class="simple-tab-table"}
{: row-headers}


## Platform developer tools
{: #cloud_services_locations_devops}

| Service                                        | `Dallas (us-south)` | `Washington (us-east)`               |
|------------------------------------------------|:-------------------:|:------------------------------------:|
| Managing access groups                         |                     |                                      |          
| Managing policies                              |                     |                                      |
| Log in to the {{site.data.keyword.cloud_notm}} |                     |                                      |
| Managing platform API keys                     |                     |                                      |
| Managing service IDs                           |                     |                                      |
{: caption="Developer tools services integration in America's locations" caption-side="top"}
{: #cs_dev-tools-table-1}
{: tab-title="America"}
{: tab-group="cs_dev_tools"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                        | `Tokyo (jp-tok)` |`Sydney (au-syd)`           |
|------------------------------------------------|:----------------:|:--------------------------:|
| Managing access groups                         |                     |                                      |          
| Managing policies                              |                     |                                      |
| Log in to the {{site.data.keyword.cloud_notm}} |                     |                                      |
| Managing platform API keys                     |                     |                                      |
| Managing service IDs                           |                     |                                      |
{: caption="Developer tools services integration in AP locations" caption-side="top"}
{: #cs_dev-tools-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="cs_dev_tools"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                                       |`Frankfurt (eu-de)`  | `London (eu-gb)` |
|---------------------------------------------------------------|:-------------------:|:----------------:|
| Managing access groups                         |                     |                                      |          
| Managing policies                              |                     |                                      |
| Log in to the {{site.data.keyword.cloud_notm}} |                     |                                      |
| Managing platform API keys                     |                     |                                      |
| Managing service IDs                           |                     |                                      |
{: caption="Developer tools services integration in Europe locations" caption-side="top"}
{: #cs_dev-tools-table-3}
{: tab-title="Europe"}
{: tab-group="cs_dev_tools"}
{: class="simple-tab-table"}
{: row-headers}




## Platform integrated security services
{: #cloud_services_locations_integrated_security}

| Service                                        | `Dallas (us-south)` | `Washington (us-east)`               |
|------------------------------------------------|:-------------------:|:------------------------------------:|
| Managing access groups                         |                     |                                      |          
| Managing policies                              |                     |                                      |
| Log in to the {{site.data.keyword.cloud_notm}} |                     |                                      |
| Managing platform API keys                     |                     |                                      |
| Managing service IDs                           |                     |                                      |
{: caption="Integrated security services integration in America's locations" caption-side="top"}
{: #cs_int_sec-table-1}
{: tab-title="America"}
{: tab-group="cs_int_sec"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                        | `Tokyo (jp-tok)` |`Sydney (au-syd)`           |
|------------------------------------------------|:----------------:|:--------------------------:|
| Managing access groups                         |                     |                                      |          
| Managing policies                              |                     |                                      |
| Log in to the {{site.data.keyword.cloud_notm}} |                     |                                      |
| Managing platform API keys                     |                     |                                      |
| Managing service IDs                           |                     |                                      |
{: caption="Integrated security services integration in AP locations" caption-side="top"}
{: #cs_int_sec-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="cs_int_sec"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                                       |`Frankfurt (eu-de)`  | `London (eu-gb)` |
|---------------------------------------------------------------|:-------------------:|:----------------:|
| Managing access groups                         |                     |                                      |          
| Managing policies                              |                     |                                      |
| Log in to the {{site.data.keyword.cloud_notm}} |                     |                                      |
| Managing platform API keys                     |                     |                                      |
| Managing service IDs                           |                     |                                      |
{: caption="Integrated security services integration in Europe locations" caption-side="top"}
{: #cs_int_sec-table-3}
{: tab-title="Europe"}
{: tab-group="cs_int_sec"}
{: class="simple-tab-table"}
{: row-headers}


## Platform integration services
{: #cloud_services_locations_integration}

| Service                                        | `Dallas (us-south)` | `Washington (us-east)`               |
|------------------------------------------------|:-------------------:|:------------------------------------:|
| {{site.data.keyword.messagehub}}               |                     |                                      |          
| MQ on IBM Cloud                                |                     |                                      |
{: caption="Integration services integration in America's locations" caption-side="top"}
{: #cs_integration-table-1}
{: tab-title="America"}
{: tab-group="cs_integration"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                        | `Tokyo (jp-tok)` |`Sydney (au-syd)`           |
|------------------------------------------------|:----------------:|:--------------------------:|
| {{site.data.keyword.messagehub}}               |                     |                                      |          
| MQ on IBM Cloud                                |                     |                                      |
{: caption="Integration services integration in AP locations" caption-side="top"}
{: #cs_integration-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="cs_integration"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                                       |`Frankfurt (eu-de)`  | `London (eu-gb)` |
|---------------------------------------------------------------|:-------------------:|:----------------:|
| {{site.data.keyword.messagehub}}               |                     |                                      |          
| MQ on IBM Cloud                                |                     |                                      |
{: caption="Integration services integration in Europe locations" caption-side="top"}
{: #cs_integration-table-3}
{: tab-title="Europe"}
{: tab-group="cs_integration"}
{: class="simple-tab-table"}
{: row-headers}

## Platform network services
{: #cloud_services_locations_network}

| Service                                        | `Dallas (us-south)` | `Washington (us-east)`               |
|------------------------------------------------|:-------------------:|:------------------------------------:|
| IBM Cloud Internet Services (CIS)              |                     |                                      |          
{: caption="Network services integration in America's locations" caption-side="top"}
{: #cs_network-table-1}
{: tab-title="America"}
{: tab-group="cs_network"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                        | `Tokyo (jp-tok)` |`Sydney (au-syd)`           |
|------------------------------------------------|:----------------:|:--------------------------:|
| IBM Cloud Internet Services (CIS)              |                     |                                      | 
{: caption="Network services integration in AP locations" caption-side="top"}
{: #cs_network-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="cs_network"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                                       |`Frankfurt (eu-de)`  | `London (eu-gb)` |
|---------------------------------------------------------------|:-------------------:|:----------------:|
| IBM Cloud Internet Services (CIS)              |                     |                                      | 
{: caption="Network services integration in Europe locations" caption-side="top"}
{: #cs_storage-table-3}
{: tab-title="Europe"}
{: tab-group="cs_network"}
{: class="simple-tab-table"}
{: row-headers}





## Platform: Security services
{: #cloud_services_locations_security}

The following tables list the locations where automatic collection of security service logs is enabled. You can monitor logs through the Log Analysis instance that is available in the same location as your security resources, if you enable 1 instance in this location to host service platform logs. For locations where you can provision a service instance but the {{site.data.keyword.at_full_notm}} service is not available, specific detail about the location where you can monitor those logs is provided in each case.


| Service                                                         | `Dallas (us-south)` | `Washington (us-east)`                |
|-----------------------------------------------------------------|:-------------------:|:-------------------------------------:|
| {{site.data.keyword.cloudcerts_full_notm}}                      | ![Checkmark icon](../../icons/checkmark-icon.svg)               | `NO`                                 |          
| {{site.data.keyword.keymanagementservicelong}}                  | ![Checkmark icon](../../icons/checkmark-icon.svg)               | `Events are available through the Log Analysis Dallas (us-south) instance` |
{: caption="Security services integration in America's locations" caption-side="top"}
{: #cs-sec-table-1}
{: tab-title="America"}
{: tab-group="cs_sec"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                                         | `Tokyo (jp-tok)` |`Sydney (au-syd)`           |
|-----------------------------------------------------------------|:----------------:|:--------------------------:|
| {{site.data.keyword.cloudcerts_full_notm}}                      | ![Checkmark icon](../../icons/checkmark-icon.svg)            | `NO`                       |
| {{site.data.keyword.keymanagementservicelong}}                  | ![Checkmark icon](../../icons/checkmark-icon.svg)            | `Events are available through the Log Analysis Tokyo instance`   |
{: caption="Security services integration in AP locations" caption-side="top"}
{: #cs-sec-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="cs_sec"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                                       |`Frankfurt (eu-de)`  | `London (eu-gb)` |
|---------------------------------------------------------------|:-------------------:|:----------------:|
| {{site.data.keyword.cloudcerts_full_notm}}                    | ![Checkmark icon](../../icons/checkmark-icon.svg)               | `NO`             |
| {{site.data.keyword.keymanagementservicelong}}                | ![Checkmark icon](../../icons/checkmark-icon.svg)               | `NO`             |
{: caption="Security services integration in Europe locations" caption-side="top"}
{: #cs-sec-table-3}
{: tab-title="Europe"}
{: tab-group="cs_sec"}
{: class="simple-tab-table"}
{: row-headers}


## Platform storage services
{: #cloud_services_locations_storage}

| Service                                        | `Dallas (us-south)` | `Washington (us-east)`               |
|------------------------------------------------|:-------------------:|:------------------------------------:|
| {{site.data.keyword.cos_full_notm}}            |                     |                                      |          
{: caption="Storage services integration in America's locations" caption-side="top"}
{: #cs_storage-table-1}
{: tab-title="America"}
{: tab-group="cs_storage"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                        | `Tokyo (jp-tok)` |`Sydney (au-syd)`           |
|------------------------------------------------|:----------------:|:--------------------------:|
| {{site.data.keyword.cos_full_notm}}            |                     |                                      |     
{: caption="Storage services integration in AP locations" caption-side="top"}
{: #cs_storage-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="cs_storage"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                                       |`Frankfurt (eu-de)`  | `London (eu-gb)` |
|---------------------------------------------------------------|:-------------------:|:----------------:|
| {{site.data.keyword.cos_full_notm}}            |                     |                                      |     
{: caption="Storage services integration in Europe locations" caption-side="top"}
{: #cs_storage-table-3}
{: tab-title="Europe"}
{: tab-group="cs_storage"}
{: class="simple-tab-table"}
{: row-headers}

## Platform web and mobile services
{: #cloud_services_locations_web}

| Service                                        | `Dallas (us-south)` | `Washington (us-east)`               |
|------------------------------------------------|:-------------------:|:------------------------------------:|
| {{site.data.keyword.mobilefoundation_short}}   |                     |                                      |          
{: caption="Web adn mobile services integration in America's locations" caption-side="top"}
{: #cs_web-table-1}
{: tab-title="America"}
{: tab-group="cs_web"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                        | `Tokyo (jp-tok)` |`Sydney (au-syd)`           |
|------------------------------------------------|:----------------:|:--------------------------:|
| {{site.data.keyword.mobilefoundation_short}}   |                     |                                      |           
{: caption="Web and mobile services integration in AP locations" caption-side="top"}
{: #cs_web-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="cs_web"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                                       |`Frankfurt (eu-de)`  | `London (eu-gb)` |
|---------------------------------------------------------------|:-------------------:|:----------------:|
| {{site.data.keyword.mobilefoundation_short}}   |                     |                                      |   
{: caption="Web and mobile services integration in Europe locations" caption-side="top"}
{: #cs_web-table-3}
{: tab-title="Europe"}
{: tab-group="cs_web"}
{: class="simple-tab-table"}
{: row-headers}

## VPC infrastructure services
{: #cloud_services_locations_vpc_infrastructure}

The following tables list the locations where automatic collection of security service logs is enabled. You can monitor logs through the Log Analysis instance that is available in the same location as your security resources, if you enable 1 instance in this location to host service platform logs. For locations where you can provision a service instance but the {{site.data.keyword.at_full_notm}} service is not available, specific detail about the location where you can monitor those logs is provided in each case.

| Service                                                         | `Dallas (us-south)` | `Washington (us-east)`               |
|-----------------------------------------------------------------|:-------------------:|:------------------------------------:|
| [{{site.data.keyword.block_storage_is_short}} - Storage resources](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-getting-started)| ![Checkmark icon](../../icons/checkmark-icon.svg)               | `NO`   |            
| [{{site.data.keyword.vsi_is_short}} - Compute resources](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-getting-started)|  ![Checkmark icon](../../icons/checkmark-icon.svg)  |  `NO` |
| [VPC Network resources](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-getting-started)|  ![Checkmark icon](../../icons/checkmark-icon.svg)  |  `NO` |
| [VPC Load Balancer](/docs/vpc-on-classic-network?topic=vpc-on-classic-network---using-load-balancers-in-ibm-cloud-vpc)| ![Checkmark icon](../../icons/checkmark-icon.svg)  |  `NO` |
| [VPC VPN](/docs/vpc-on-classic-network?topic=vpc-on-classic-network---using-vpn-with-your-vpc)| `Events are available through the Activity Tracker US-South instance` | `Events are available through the Activity Tracker US-South instance` |
{: caption="VPC events in America's locations" caption-side="top"}
{: #cs-vpc-table-1}
{: tab-title="America"}
{: tab-group="cs_vpc"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                                         | `Tokyo (jp-tok)` |`Sydney (au-syd)`           |
|-----------------------------------------------------------------|:----------------:|:--------------------------:|
| [{{site.data.keyword.block_storage_is_short}} - Storage resources](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-getting-started)| ![Checkmark icon](../../icons/checkmark-icon.svg)               | `Events are available through the Activity Tracker US-South instance` |            
| [{{site.data.keyword.vsi_is_short}} - Compute resources](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-getting-started)| ![Checkmark icon](../../icons/checkmark-icon.svg)               | `Events are available through the Activity Tracker US-South instance` |            
| [VPC Network resources](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-getting-started)| ![Checkmark icon](../../icons/checkmark-icon.svg)               | `Events are available through the Activity Tracker US-South instance` |            
| [VPC Load Balancer](/docs/vpc-on-classic-network?topic=vpc-on-classic-network---using-load-balancers-in-ibm-cloud-vpc)| `Events are available through the Activity Tracker US-South instance` | `Events are available through the Activity Tracker US-South instance` |
| [VPC VPN](/docs/vpc-on-classic-network?topic=vpc-on-classic-network---using-vpn-with-your-vpc)|  ![Checkmark icon](../../icons/checkmark-icon.svg)               | `Events are available through the Activity Tracker US-South instance` |            
{: caption="VPC events in AP locations" caption-side="top"}
{: #cs-vpc-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="cs_vpc"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                                       |`Frankfurt (eu-de)`  | `London (eu-gb)` |
|---------------------------------------------------------------|:-------------------:|:----------------:|
| [{{site.data.keyword.block_storage_is_short}} - Storage resources](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-getting-started)| ![Checkmark icon](../../icons/checkmark-icon.svg)               | `Events are available through the Activity Tracker EU-DE instance` |            
| [{{site.data.keyword.vsi_is_short}} - Compute resources](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-getting-started)|  ![Checkmark icon](../../icons/checkmark-icon.svg)               | `Events are available through the Activity Tracker EU-DE instance` |            
| [VPC Network resources](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-getting-started)|  ![Checkmark icon](../../icons/checkmark-icon.svg)               | `Events are available through the Activity Tracker EU-DE instance` |            
| [VPC Load Balancer](/docs/vpc-on-classic-network?topic=vpc-on-classic-network---using-load-balancers-in-ibm-cloud-vpc)| `Events are available through the Activity Tracker US-South instance` | `Events are available through the Activity Tracker US-South instance` |
| [VPC VPN](/docs/vpc-on-classic-network?topic=vpc-on-classic-network---using-vpn-with-your-vpc)|  ![Checkmark icon](../../icons/checkmark-icon.svg)               | `Events are available through the Activity Tracker EU-DE instance` |            
{: caption="VPC events in Europe locations" caption-side="top"}
{: #cs-vpc-table-3}
{: tab-title="Europe"}
{: tab-group="cs_vpc"}
{: class="simple-tab-table"}
{: row-headers}



## Watson AI
{: #cloud_services_locations_watson_ai}


| Service  | `Dallas (us-south)`  | `Washington (us-east)` |
|----------|:--------------------:|:----------------------:|
| {{site.data.keyword.conversationshort}} | ![Checkmark icon](../../icons/checkmark-icon.svg) | ![Checkmark icon](../../icons/checkmark-icon.svg) |
| {{site.data.keyword.discoveryfull}}    | ![Checkmark icon](../../icons/checkmark-icon.svg) | ![Checkmark icon](../../icons/checkmark-icon.svg) |
| {{site.data.keyword.cncfullnotm}}      |  |  |
| {{site.data.keyword.DSX_short}}        |  |  |
| Watson Knowledge Catalog               |  |  |
| {{site.data.keyword.knowledgestudioshort}} | ![Checkmark icon](../../icons/checkmark-icon.svg) | ![Checkmark icon](../../icons/checkmark-icon.svg) |
| {{site.data.keyword.pm_full}}          |  |  |
| {{site.data.keyword.nlclassifiershort}} |  |  |
| {{site.data.keyword.nlushort}}          | ![Checkmark icon](../../icons/checkmark-icon.svg) | ![Checkmark icon](../../icons/checkmark-icon.svg) |
| {{site.data.keyword.visualrecognitionshort}} |  |  | 
| {{site.data.keyword.texttospeechshort}} | ![Checkmark icon](../../icons/checkmark-icon.svg) | ![Checkmark icon](../../icons/checkmark-icon.svg) |
| {{site.data.keyword.speechtotextshort}} | ![Checkmark icon](../../icons/checkmark-icon.svg) | ![Checkmark icon](../../icons/checkmark-icon.svg) |
{: caption="Watson AI services integration in America's locations" caption-side="top"}
{: #cs_watsonai-table-1}
{: tab-title="America"}
{: tab-group="cs_watsonai"}
{: class="simple-tab-table"}
{: row-headers}

| Service | `Tokyo (jp-tok)` | `Sydney (au-syd)` |
|---------|:----------------:|:-----------------:|
| {{site.data.keyword.conversationshort}} | ![Checkmark icon](../../icons/checkmark-icon.svg) | ![Checkmark icon](../../icons/checkmark-icon.svg) |
| {{site.data.keyword.discoveryfull}}     | ![Checkmark icon](../../icons/checkmark-icon.svg) | ![Checkmark icon](../../icons/checkmark-icon.svg) |          
| {{site.data.keyword.cncfullnotm}}       |  |  |
| {{site.data.keyword.DSX_short}}         |  |  | 
| Watson Knowledge Catalog                |  |  |
| {{site.data.keyword.knowledgestudioshort}} | ![Checkmark icon](../../icons/checkmark-icon.svg) | ![Checkmark icon](../../icons/checkmark-icon.svg) |
| {{site.data.keyword.pm_full}}           |  |  | 
| {{site.data.keyword.nlclassifiershort}} |  |  |
| {{site.data.keyword.nlushort}}          | ![Checkmark icon](../../icons/checkmark-icon.svg) | ![Checkmark icon](../../icons/checkmark-icon.svg) |
| {{site.data.keyword.visualrecognitionshort}} |  |  | 
| {{site.data.keyword.texttospeechshort}} | ![Checkmark icon](../../icons/checkmark-icon.svg) | ![Checkmark icon](../../icons/checkmark-icon.svg) |
| {{site.data.keyword.speechtotextshort}} | ![Checkmark icon](../../icons/checkmark-icon.svg) | ![Checkmark icon](../../icons/checkmark-icon.svg) |
{: caption="Watson AI services integration in AP locations" caption-side="top"}
{: #cs_watsonai-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="cs_watsonai"}
{: class="simple-tab-table"}
{: row-headers}

| Service |`Frankfurt (eu-de)` | `London (eu-gb)` |
|---------|:------------------:|:----------------:|
| {{site.data.keyword.conversationshort}} | ![Checkmark icon](../../icons/checkmark-icon.svg) | ![Checkmark icon](../../icons/checkmark-icon.svg) |
| {{site.data.keyword.discoveryfull}}     | ![Checkmark icon](../../icons/checkmark-icon.svg) | ![Checkmark icon](../../icons/checkmark-icon.svg) |
| {{site.data.keyword.cncfullnotm}}       |  |  |
| {{site.data.keyword.DSX_short}}         |  |  | 
| Watson Knowledge Catalog                |  |  |
| {{site.data.keyword.knowledgestudioshort}} | ![Checkmark icon](../../icons/checkmark-icon.svg) | ![Checkmark icon](../../icons/checkmark-icon.svg) |
| {{site.data.keyword.pm_full}}           |  |  | 
| {{site.data.keyword.nlclassifiershort}} |  |  |
| {{site.data.keyword.nlushort}}          | ![Checkmark icon](../../icons/checkmark-icon.svg) | ![Checkmark icon](../../icons/checkmark-icon.svg) |
| {{site.data.keyword.visualrecognitionshort}} |  |  |
| {{site.data.keyword.texttospeechshort}}      | ![Checkmark icon](../../icons/checkmark-icon.svg) | ![Checkmark icon](../../icons/checkmark-icon.svg) |
| {{site.data.keyword.speechtotextshort}}      | ![Checkmark icon](../../icons/checkmark-icon.svg) | ![Checkmark icon](../../icons/checkmark-icon.svg) |
{: caption="Watson AI services integration in Europe locations" caption-side="top"}
{: #cs_watsonai-table-3}
{: tab-title="Europe"}
{: tab-group="cs_watsonai"}
{: class="simple-tab-table"}
{: row-headers}




