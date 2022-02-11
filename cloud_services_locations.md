---

copyright:
  years: 2019, 2022
lastupdated: "2022-02-11"

keywords: IBM Cloud,Activity Tracker, cloud services, services, locations, {{site.data.keyword.at_short}} hosted event search, {{site.data.keyword.atracker_short}} event routing,

subcollection: activity-tracker


---

{{site.data.keyword.attribute-definition-list}}

# IBM Cloud services that generate {{site.data.keyword.atracker_short}} events by location
{: #cloud_services_locations}

List of locations where {{site.data.keyword.cloud}} services are enabled to send events to {{site.data.keyword.at_full_notm}}:
{: shortdesc}


## Analytics services
{: #cloud_services_locations_analytics}

| Service                            | `Dallas (us-south)` | `Washington (us-east)`  |`Toronto (ca-tor)` | `Sao Paulo (br-sao)` |
|------------------------------------|---------------------|-------------------------|-------------------|----------------------|
| {{site.data.keyword.iae_full}}               | ![Checkmark icon](images/checkmark-icon.svg) |                                      |        
| {{site.data.keyword.sqlquery_full}}          | ![Checkmark icon](images/checkmark-icon.svg) |                                      |  
| {{site.data.keyword.dv_short}}               | ![Checkmark icon](images/checkmark-icon.svg) |                                      |  
{: caption="Table 1. Analytics services integration in Americas locations" caption-side="top"}
{: #analytics-table-1}
{: tab-title="Americas"}
{: tab-group="analytics"}
{: class="simple-tab-table"}
{: row-headers}

| Service        | `Tokyo (jp-tok)`    |`Sydney (au-syd)` | `Seoul (kr-seo)` | `Osaka (jp-osa)` | `Chennai (in-che)` |
|----------------|---------------------|------------------|------------------|------------------|--------------------|
| {{site.data.keyword.iae_full}}               | ![Checkmark icon](images/checkmark-icon.svg) |  |
| {{site.data.keyword.sqlquery_full}}          | |  |
| {{site.data.keyword.dv_short}}               | ![Checkmark icon](images/checkmark-icon.svg)   |  |  
{: caption="Table 1. Analytics services integration in AP locations" caption-side="top"}
{: #analytics-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="analytics"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                        |`Frankfurt (eu-de)`  | `London (eu-gb)` |
|------------------------------------------------|---------------------|------------------|
| {{site.data.keyword.iae_full}}               | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) |        
| {{site.data.keyword.sqlquery_full}}          | ![Checkmark icon](images/checkmark-icon.svg) |                                 |  
| {{site.data.keyword.dv_short}}               | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) |        
{: caption="Table 1. Analytics services integration in Europe locations" caption-side="top"}
{: #analytics-table-3}
{: tab-title="Europe"}
{: tab-group="analytics"}
{: class="simple-tab-table"}
{: row-headers}


## VMware solution services
{: #cloud_services_locations_vmware}

{{site.data.keyword.vmwaresolutions_short}} events are available through the Activity Tracker Frankfurt (eu-de) instance.

| Service                            | `Dallas (us-south)` | `Washington (us-east)`  |`Toronto (ca-tor)` | `Sao Paulo (br-sao)` |
|------------------------------------|---------------------|-------------------------|-------------------|----------------------|
| VMware Solutions Shared                        | ![Checkmark icon](images/checkmark-icon.svg) |  |    
| KMIP for VMware                                | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |  
{: caption="Table 2. Compute VMware services integration in Americas locations" caption-side="top"}
{: #cs-vm-table-1}
{: tab-title="Americas"}
{: tab-group="cs-vm"}
{: class="simple-tab-table"}
{: row-headers}

| Service        | `Tokyo (jp-tok)`    |`Sydney (au-syd)` | `Seoul (kr-seo)` | `Osaka (jp-osa)` | `Chennai (in-che)` |
|----------------|---------------------|------------------|------------------|------------------|--------------------|
| VMware Solutions Shared                            |  |  |   
| KMIP for VMware                                | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |  
{: caption="Table 2. Compute VMware services integration in Asia Pacific locations" caption-side="top"}
{: #cs-vm-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="cs-vm"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                                       |`Frankfurt (eu-de)`  | `London (eu-gb)` |
|---------------------------------------------------------------|-------------------|----------------|
| VMware Solutions Shared                             | ![Checkmark icon](images/checkmark-icon.svg) |  |   
| KMIP for VMware                                | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg)  |  
{: caption="Table 2. Compute VMware services integration in Europe locations" caption-side="top"}
{: #cs-vm-table-3}
{: tab-title="Europe"}
{: tab-group="cs-vm"}
{: class="simple-tab-table"}
{: row-headers}


## Classic services
{: #cloud_services_locations_classic}

| Service                            | `Dallas (us-south)` | `Washington (us-east)`  |`Toronto (ca-tor)` | `Sao Paulo (br-sao)` |
|------------------------------------|---------------------|-------------------------|-------------------|----------------------|
| {{site.data.keyword.BluVirtServers_full}}     | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |        
| {{site.data.keyword.baremetal_long}}           | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |   
{: caption="Table 3. Compute infrastructure services integration in Americas locations" caption-side="top"}
{: #cs-infra-table-1}
{: tab-title="Americas"}
{: tab-group="cs-infra"}
{: class="simple-tab-table"}
{: row-headers}

| Service        | `Tokyo (jp-tok)`    |`Sydney (au-syd)` | `Seoul (kr-seo)` | `Osaka (jp-osa)` | `Chennai (in-che)` |
|----------------|---------------------|------------------|------------------|------------------|--------------------|
| {{site.data.keyword.BluVirtServers_full}}     | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |        
| {{site.data.keyword.baremetal_long}}           | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |   
{: caption="Table 3. Compute infrastructure services integration in AP locations" caption-side="top"}
{: #cs-infra-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="cs-infra"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                                       |`Frankfurt (eu-de)`  | `London (eu-gb)` |
|---------------------------------------------------------------|---------------------|------------------|
| {{site.data.keyword.BluVirtServers_full}}     |  ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |       
| {{site.data.keyword.baremetal_long}}           |  ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |   
{: caption="Table 3. Compute infrastructure services integration in Europe locations" caption-side="top"}
{: #cs-infra-table-3}
{: tab-title="Europe"}
{: tab-group="cs-infra"}
{: class="simple-tab-table"}
{: row-headers}

## Compute serverless services
{: #cloud_services_locations_serverless}

| Service                            | `Dallas (us-south)` | `Washington (us-east)`  |`Toronto (ca-tor)` | `Sao Paulo (br-sao)` |
|------------------------------------|---------------------|-------------------------|-------------------|----------------------|
| {{site.data.keyword.openwhisk_short}}          | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |   
| {{site.data.keyword.codeengineshort}}          | ![Checkmark icon](images/checkmark-icon.svg) | |       
{: caption="Table 4. Compute serverless services integration in Americas locations" caption-side="top"}
{: #cs-comp-table-1}
{: tab-title="Americas"}
{: tab-group="cs-comp"}
{: class="simple-tab-table"}
{: row-headers}

| Service        | `Tokyo (jp-tok)`    |`Sydney (au-syd)` | `Seoul (kr-seo)` | `Osaka (jp-osa)` | `Chennai (in-che)` |
|----------------|---------------------|------------------|------------------|------------------|--------------------|
| {{site.data.keyword.openwhisk_short}}          | ![Checkmark icon](images/checkmark-icon.svg) |   |
| {{site.data.keyword.codeengineshort}}          | ![Checkmark icon](images/checkmark-icon.svg) |   |
{: caption="Table 4. Compute serverless services integration in AP locations" caption-side="top"}
{: #cs-comp-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="cs-comp"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                                       |`Frankfurt (eu-de)`  | `London (eu-gb)` |
|---------------------------------------------------------------|---------------------|------------------|
| {{site.data.keyword.openwhisk_short}}          | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.codeengineshort}}          | ![Checkmark icon](images/checkmark-icon.svg) | |
{: caption="Table 4. Compute serverless services integration in Europe locations" caption-side="top"}
{: #cs-comp-table-3}
{: tab-title="Europe"}
{: tab-group="cs-comp"}
{: class="simple-tab-table"}
{: row-headers}




## Cloud Foundry
{: #cloud_services_locations_cfapps}

The following table shows the locations where automatic collection of Cloud Foundry (CF) logs is enabled. You can monitor these logs through the {{site.data.keyword.at_full_notm}} instance that is configured with the **service platform logs** in the same location where the CF resource is available.

| Service                            | `Dallas (us-south)` | `Washington (us-east)`  |`Toronto (ca-tor)` | `Sao Paulo (br-sao)` |
|------------------------------------|---------------------|-------------------------|-------------------|----------------------|
| Cloud Foundry (CF)                                            | ![Checkmark icon](images/checkmark-icon.svg)              | ![Checkmark icon](images/checkmark-icon.svg)              |
{: caption="Table 5. Cloud Foundry in Americas" caption-side="top"}
{: #cs-cfapps-table-1}
{: tab-title="Americas"}
{: tab-group="cs_cfapps"}
{: class="simple-tab-table"}
{: row-headers}

| Service        | `Tokyo (jp-tok)`    |`Sydney (au-syd)` | `Seoul (kr-seo)` | `Osaka (jp-osa)` | `Chennai (in-che)` |
|----------------|---------------------|------------------|------------------|------------------|--------------------|
| Cloud Foundry (CF)                                  |          | ![Checkmark icon](images/checkmark-icon.svg)            |
{: caption="Table 5. Cloud Foundry in Asia Pacific" caption-side="top"}
{: #cs-cfapps-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="cs_cfapps"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                                       | `Frankfurt (eu-de)` | `London (eu-gb)` |
|---------------------------------------------------------------|---------------------|------------------|
| Cloud Foundry (CF)                                            | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg)  |
{: caption="Table 5. Cloud Foundry in Europe" caption-side="top"}
{: #cs-cfapps-table-3}
{: tab-title="Europe"}
{: tab-group="cs_cfapps"}
{: class="simple-tab-table"}
{: row-headers}


## Container services
{: #cloud_services_locations_container}

For {{site.data.keyword.containerlong_notm}}, see [Locations](/docs/containers?topic=containers-at_events#at-ui).

For {{site.data.keyword.openshiftlong_notm}}, see [Locations](/docs/openshift?topic=openshift-at_events#at-ui).

For {{site.data.keyword.satellitelong_notm}}, see [Locations](/docs/satellite?topic=satellite-at_events#at_ui).

You can track how users and applications interact with the {{site.data.keyword.registrylong_notm}} service. The following table lists the locations where the automatic collection of {{site.data.keyword.registryshort_notm}} service events is enabled. For more information, see [Auditing the events for {{site.data.keyword.registrylong_notm}}](/docs/Registry?topic=Registry-at_events).

| Service                                       | `Dallas (us-south)` | `Sao Paulo (br-sao)` | `Toronto (ca-tor)` | `Global` |
|-----------------------------------------------|---------------------|----------------------|--------------------|------------------------|
| {{site.data.keyword.registrylong_notm}}  | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) | `[*]` |         
{: caption="Table 6. Container services integration in Americas locations" caption-side="top"}
{: #cs-container-table-1}
{: tab-title="America"}
{: tab-group="cs-container"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                        |  `Osaka (jp-osa)`  | `Sydney (au-syd)`    | `Tokyo (jp-tok)`|
|------------------------------------------------|--------------------|----------------------|-----------------|
| {{site.data.keyword.registrylong_notm}}  `[*]` | ![Checkmark icon](images/checkmark-icon.svg) | `Events are available through the Activity Tracker Tokyo (jp-tok) instance.` | ![Checkmark icon](images/checkmark-icon.svg) |       
{: caption="Table 6. Container services integration in Asia Pacific locations" caption-side="top"}
{: #cs-container-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="cs-container"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                       |`Frankfurt (eu-de)`  | `London (eu-gb)` |
|-----------------------------------------------|---------------------|------------------|
| {{site.data.keyword.registrylong_notm}} `[*]` | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |          
{: caption="Table 6. Container services integration in Europe locations" caption-side="top"}
{: #cs-container-table-3}
{: tab-title="Europe"}
{: tab-group="cs-container"}
{: class="simple-tab-table"}
{: row-headers}

`[*]` {{site.data.keyword.registrylong_notm}} events from the global registry (`icr.io`) are available through the Activity Tracker `Dallas (us-south)` instance.  

## Observability services
{: #cloud_services_locations_observability}

| Service                            | `Dallas (us-south)` | `Washington (us-east)`  |`Toronto (ca-tor)` | `Sao Paulo (br-sao)` |
|------------------------------------|---------------------|-------------------------|-------------------|----------------------|
| {{site.data.keyword.at_full_notm}} hosted event search offering | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg)| ![Checkmark icon](images/checkmark-icon.svg)| ![Checkmark icon](images/checkmark-icon.svg)|
| {{site.data.keyword.at_full_notm}} event routing  | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg)|
| {{site.data.keyword.la_full_notm}}       | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg)| ![Checkmark icon](images/checkmark-icon.svg)| ![Checkmark icon](images/checkmark-icon.svg)|  
| {{site.data.keyword.mon_full_notm}}      | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg)| ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |     
{: caption="Table 7. Observability services in America's locations" caption-side="top"}
{: #cs-observability-table-1}
{: tab-title="America"}
{: tab-group="cs-observability"}
{: class="simple-tab-table"}
{: row-headers}

| Service        | `Tokyo (jp-tok)`    |`Sydney (au-syd)` | `Seoul (kr-seo)` | `Osaka (jp-osa)` | `Chennai (in-che)` |
|----------------|---------------------|------------------|------------------|------------------|--------------------|
| {{site.data.keyword.at_full_notm}} hosted event search offering | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |  
| {{site.data.keyword.at_full_notm}} event routing  | | | | | |
| {{site.data.keyword.la_full_notm}}  | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |    
| {{site.data.keyword.mon_full_notm}}      | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg)|  | ![Checkmark icon](images/checkmark-icon.svg) | |  | 
{: caption="Table 7. Observability services in AP locations" caption-side="top"}
{: #cs-observability-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="cs-observability"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                                       |`Frankfurt (eu-de)`  | `London (eu-gb)` |
|---------------------------------------------|---------------------|------------------|
| {{site.data.keyword.at_full_notm}}     | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.at_full_notm}} event routing  | | |
| {{site.data.keyword.la_full_notm}}     | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |     
| {{site.data.keyword.mon_full_notm}}      | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg)|        
{: caption="Table 7. Observability services in Europe locations" caption-side="top"}
{: #cs-observability-table-3}
{: tab-title="Europe"}
{: tab-group="cs-observability"}
{: class="simple-tab-table"}
{: row-headers}

## Platform services
{: #cloud_services_locations_core_integrated}


| Global service                                  | Location | 
|-------------------------------------------------|---------------------|
| BSS - Account and billing | `Events are available through the Activity Tracker Frankfurt (eu-de) instance` | 
| BSS - User management | `Events are available through the Activity Tracker Frankfurt (eu-de) instance` | 
| BSS - Provisioning | `Events are available through the Activity Tracker Frankfurt (eu-de) instance` | 
| {{site.data.keyword.iamlong}}    | `Events are available through the Activity Tracker Frankfurt (eu-de) instance` |        
| {{site.data.keyword.compliance_short}}   | `Events are available through the Activity Tracker Frankfurt (eu-de) instance` |    
| Global Search Service | `Events are available through the Activity Tracker Frankfurt (eu-de) instance` |  
| Catalog | `Events are available through the Activity Tracker Frankfurt (eu-de) instance` | 
| Trusted profiles | `Events are available through the Activity Tracker Frankfurt (eu-de) instance` | 
| Context-based restrictions | `Events are available through the Activity Tracker Frankfurt (eu-de) instance` | 
{: caption="Table 8. Integrated security services integration in America locations" caption-side="top"}




## Database services
{: #cloud_services_locations_database}

The following tables list the locations where automatic collection of database service logs is enabled. You can monitor logs through the instance that is available in the same location as your database resources, if you enable 1 instance in this location to host service platform logs. For locations where you can provision a service instance but the {{site.data.keyword.at_full_notm}} service is not available, specific detail about the location where you can monitor those logs is provided in each case.

| Service                            | `Dallas (us-south)` | `Washington (us-east)`  |`Toronto (ca-tor)` | `Sao Paulo (br-sao)` |
|------------------------------------|---------------------|-------------------------|-------------------|----------------------|
| {{site.data.keyword.cloudant_short_notm}}                       | ![Checkmark icon](images/checkmark-icon.svg)               | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.databases-for-mongodb_full_notm}}           | ![Checkmark icon](images/checkmark-icon.svg)               | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.databases-for-enterprisedb_full_notm}}      | ![Checkmark icon](images/checkmark-icon.svg)               | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.databases-for-cassandra_full_notm}}         | ![Checkmark icon](images/checkmark-icon.svg)               | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.databases-for-elasticsearch_full_notm}}     | ![Checkmark icon](images/checkmark-icon.svg)               | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.databases-for-etcd_full_notm}}              | ![Checkmark icon](images/checkmark-icon.svg)               | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.databases-for-postgresql_full_notm}}        | ![Checkmark icon](images/checkmark-icon.svg)`               | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_mongodb_full}}        | ![Checkmark icon](images/checkmark-icon.svg)               | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}        | ![Checkmark icon](images/checkmark-icon.svg)               | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.messages-for-rabbitmq_full_notm}}           | ![Checkmark icon](images/checkmark-icon.svg)               | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.databases-for-redis_full_notm}}             | ![Checkmark icon](images/checkmark-icon.svg)               | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.Db2_on_Cloud_long}}| ![Checkmark icon](images/checkmark-icon.svg)               | ![Checkmark icon](images/checkmark-icon.svg) |
{: caption="Table 9. Database services integration in America locations" caption-side="top"}
{: #cs-dbs-table-1}
{: tab-title="America"}
{: tab-group="cs_dbs"}
{: class="simple-tab-table"}
{: row-headers}

| Service    | `Tokyo (jp-tok)`   |`Sydney (au-syd)` | `Seoul 01 (seo01)`       | `Chennai 01 (che01)`     | `Seoul (kr-seo)` | 
|------------|--------------------|------------------|--------------------------|--------------------------|------------------|
| {{site.data.keyword.cloudant_short_notm}}                       | ![Checkmark icon](images/checkmark-icon.svg) |![Checkmark icon](images/checkmark-icon.svg) |   | ![Checkmark icon](images/checkmark-icon.svg)| ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.databases-for-mongodb_full_notm}}           | ![Checkmark icon](images/checkmark-icon.svg) |![Checkmark icon](images/checkmark-icon.svg) | `Events are available through the Tokyo instance` | ![Checkmark icon](images/checkmark-icon.svg) |               |
| {{site.data.keyword.databases-for-enterprisedb_full_notm}}      | ![Checkmark icon](images/checkmark-icon.svg) |![Checkmark icon](images/checkmark-icon.svg) | `Events are available through the Tokyo instance` | ![Checkmark icon](images/checkmark-icon.svg) |               |
| {{site.data.keyword.databases-for-cassandra_full_notm}}         | ![Checkmark icon](images/checkmark-icon.svg) |![Checkmark icon](images/checkmark-icon.svg) | `Events are available through the Tokyo instance` | ![Checkmark icon](images/checkmark-icon.svg) |               |
| {{site.data.keyword.databases-for-elasticsearch_full_notm}}     | ![Checkmark icon](images/checkmark-icon.svg) |![Checkmark icon](images/checkmark-icon.svg) | `Events are available through the Tokyo instance` | ![Checkmark icon](images/checkmark-icon.svg) |               |
| {{site.data.keyword.databases-for-etcd_full_notm}}              | ![Checkmark icon](images/checkmark-icon.svg) |![Checkmark icon](images/checkmark-icon.svg) | `Events are available through the Tokyo instance` | ![Checkmark icon](images/checkmark-icon.svg) |               |
| {{site.data.keyword.databases-for-postgresql_full_notm}}        | ![Checkmark icon](images/checkmark-icon.svg) |![Checkmark icon](images/checkmark-icon.svg) | `Events are available through the Tokyo instance` | ![Checkmark icon](images/checkmark-icon.svg) |               |
| {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_mongodb_full}}          |                 | `Events are available through the Dallas instance`             |                       |                       |               |
| {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}       |                 | `Events are available through the Dallas instance`             |                       |                       |               |
| {{site.data.keyword.messages-for-rabbitmq_full_notm}}           | ![Checkmark icon](images/checkmark-icon.svg) |![Checkmark icon](images/checkmark-icon.svg) | `Events are available through the Tokyo instance` | ![Checkmark icon](images/checkmark-icon.svg) |               |
| {{site.data.keyword.databases-for-redis_full_notm}}            | ![Checkmark icon](images/checkmark-icon.svg) |![Checkmark icon](images/checkmark-icon.svg) | `Events are available through the Tokyo instance` | ![Checkmark icon](images/checkmark-icon.svg) |               |
| {{site.data.keyword.Db2_on_Cloud_long}} | ![Checkmark icon](images/checkmark-icon.svg) |![Checkmark icon](images/checkmark-icon.svg) |   | | |
{: caption="Table 9. Database services integration in AP locations" caption-side="top"}
{: #cs-dbs-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="cs_dbs"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                                       |`Frankfurt (eu-de)`  | `London (eu-gb)` | `Oslo 01 (osl01)`         |
|---------------------------------------------------------------|---------------------|------------------|---------------------------|
| {{site.data.keyword.cloudant_short_notm}}                     | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |                        |
| {{site.data.keyword.databases-for-mongodb_full_notm}}           | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg)            | `Events are available through the London instance` |
| {{site.data.keyword.databases-for-enterprisedb_full_notm}}      | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg)            | `Events are available through the London instance` |
| {{site.data.keyword.databases-for-cassandra_full_notm}}         | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg)            | `Events are available through the London instance` |
| {{site.data.keyword.databases-for-elasticsearch_full_notm}}   | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg)            | `Events are available through the London instance` |
| {{site.data.keyword.databases-for-etcd_full_notm}}            | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg)            | `Events are available through the London instance` |
| {{site.data.keyword.databases-for-postgresql_full_notm}}      | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg)            | `Events are available through the London instance` |
| {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_mongodb_full}}        | ![Checkmark icon](images/checkmark-icon.svg)  |    |    |
| {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}     | ![Checkmark icon](images/checkmark-icon.svg)   |    |    |
| {{site.data.keyword.messages-for-rabbitmq_full_notm}}         | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg)            | `Events are available through the London instance` |
| {{site.data.keyword.databases-for-redis_full_notm}}           | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg)            | `Events are available through the London instance` |
| {{site.data.keyword.Db2_on_Cloud_long}} | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |                        |
{: caption="Table 9. Database services integration in Europe locations" caption-side="top"}
{: #cs-dbs-table-3}
{: tab-title="Europe"}
{: tab-group="cs_dbs"}
{: class="simple-tab-table"}
{: row-headers}


## Developer tools
{: #cloud_services_locations_devops}

The Apps service sends global events. These events are available through the Franfurt instance.


| Service                            | `Dallas (us-south)` | `Washington (us-east)`  |`Toronto (ca-tor)` | `Sao Paulo (br-sao)` |
|------------------------------------|---------------------|-------------------------|-------------------|----------------------|
| {{site.data.keyword.apigw_full}}               | ![Checkmark icon](images/checkmark-icon.svg)   | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.cloud-shell_notm}}         | ![Checkmark icon](images/checkmark-icon.svg)   |                     |   
| {{site.data.keyword.contdelivery_full}}        | ![Checkmark icon](images/checkmark-icon.svg)   | ![Checkmark icon](images/checkmark-icon.svg) |         
| {{site.data.keyword.mobilepush}}               | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.bplong}}                   |  ![Checkmark icon](images/checkmark-icon.svg)  | `Events are available through the Dallas instance`  |
| {{site.data.keyword.en_full}}         | ![Checkmark icon](images/checkmark-icon.svg)   |                     | 
| {{site.data.keyword.appconfig_full}}         | ![Checkmark icon](images/checkmark-icon.svg)   |                     | 
{: caption="Table 10. Developer tools services integration in America's locations" caption-side="top"}
{: #cs-dev-tools-table-1}
{: tab-title="America"}
{: tab-group="cs-dev_tools"}
{: class="simple-tab-table"}
{: row-headers}

| Service        | `Tokyo (jp-tok)`    |`Sydney (au-syd)` | `Seoul (kr-seo)` | `Osaka (jp-osa)` | `Chennai (in-che)` |
|----------------|---------------------|------------------|------------------|------------------|--------------------|
| {{site.data.keyword.apigw_full}}               | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) | | | |
| {{site.data.keyword.cloud-shell_notm}}        | ![Checkmark icon](images/checkmark-icon.svg) |  |  |  | |
| {{site.data.keyword.contdelivery_full}}        | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |  | ![Checkmark icon](images/checkmark-icon.svg) |  |
| {{site.data.keyword.mobilepush}}               | ![Checkmark icon](images/checkmark-icon.svg) |  | ![Checkmark icon](images/checkmark-icon.svg) | | |
| {{site.data.keyword.bplong}}                   |   |   |   | | |
| {{site.data.keyword.en_full}}                   |   | ![Checkmark icon](images/checkmark-icon.svg)   | |  | |
| {{site.data.keyword.appconfig_full}}                   |   | ![Checkmark icon](images/checkmark-icon.svg)   |  | | |
{: caption="Developer tools services integration in AP locations" caption-side="top"}
{: #cs-dev-tools-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="cs-dev_tools"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                                       |`Frankfurt (eu-de)`  | `London (eu-gb)` |
|---------------------------------------------------------------|---------------------|------------------|
| {{site.data.keyword.apigw_full}}               | ![Checkmark icon](images/checkmark-icon.svg)   | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.cloud-shell_notm}}        | ![Checkmark icon](images/checkmark-icon.svg)   |                     |  
| {{site.data.keyword.contdelivery_full}}        | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg)                    |   
| {{site.data.keyword.mobilepush}}               | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.bplong}}                   | ![Checkmark icon](images/checkmark-icon.svg) | `Events are available through the Frankfurt instance` | 
| {{site.data.keyword.en_full}}                  | | ![Checkmark icon](images/checkmark-icon.svg)  |   
| {{site.data.keyword.appconfig_full}}                  | | ![Checkmark icon](images/checkmark-icon.svg)  | 
{: caption="Table 10. Developer tools services integration in Europe locations" caption-side="top"}
{: #cs-dev-tools-table-3}
{: tab-title="Europe"}
{: tab-group="cs-dev_tools"}
{: class="simple-tab-table"}
{: row-headers}





## Integration services
{: #cloud_services_locations_integration}

| Service                            | `Dallas (us-south)` | `Washington (us-east)`  |`Toronto (ca-tor)` | `Sao Paulo (br-sao)` |
|------------------------------------|---------------------|-------------------------|-------------------|----------------------|
| {{site.data.keyword.messagehub}}               | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |          
| MQ on IBM Cloud                                | ![Checkmark icon](images/checkmark-icon.svg) |                                       |
{: caption="Table 11. Integration services integration in America's locations" caption-side="top"}
{: #cs_integration-table-1}
{: tab-title="America"}
{: tab-group="cs_integration"}
{: class="simple-tab-table"}
{: row-headers}

| Service        | `Tokyo (jp-tok)`    |`Sydney (au-syd)` | `Seoul (kr-seo)` | `Osaka (jp-osa)` | `Chennai (in-che)` |
|----------------|---------------------|------------------|------------------|------------------|--------------------|
| {{site.data.keyword.messagehub}}               | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |![Checkmark icon](images/checkmark-icon.svg) |
| MQ on IBM Cloud                                |                  | ![Checkmark icon](images/checkmark-icon.svg)  | | |
{: caption="Table 11. Integration services integration in AP locations" caption-side="top"}
{: #cs_integration-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="cs_integration"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                                       |`Frankfurt (eu-de)`  | `London (eu-gb)` |
|---------------------------------------------------------------|---------------------|------------------|
| {{site.data.keyword.messagehub}}               | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |          
| MQ on IBM Cloud                                | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
{: caption="Table 11. Integration services integration in Europe locations" caption-side="top"}
{: #cs_integration-table-3}
{: tab-title="Europe"}
{: tab-group="cs_integration"}
{: class="simple-tab-table"}
{: row-headers}




## Network services
{: #cloud_services_locations_network}

| Global service                                 | Location |
|------------------------------------------------|--------------------|
| {{site.data.keyword.dns_full}}                 | `Events are available through the Activity Tracker Frankfurt (eu-de) instance` |  
| {{site.data.keyword.BluDirectLink}}            | `Events are available through the Activity Tracker Frankfurt (eu-de) instance` |  
| {{site.data.keyword.cis_full}}  (CIS)          | `Events are available through the Activity Tracker Frankfurt (eu-de) instance` |  
| {{site.data.keyword.tg_full}}                  | `Events are available through the Activity Tracker Frankfurt (eu-de) instance` |
| Content Delivery Network (CDN)                 | `Events are available through the Activity Tracker Frankfurt (eu-de) instance` | 
| {{site.data.keyword.vpc_full}}                 | `Events are available through the Activity Tracker Dallas (us-south) instance` |
{: caption="Table 12. Network services that are global" caption-side="top"}



## Security services
{: #cloud_services_locations_security}

The following tables list the locations where automatic collection of security service logs is enabled. You can monitor logs through the instance that is available in the same location as your security resources, if you enable 1 instance in this location to host service platform logs. For locations where you can provision a service instance but the {{site.data.keyword.at_full_notm}} service is not available, specific detail about the location where you can monitor those logs is provided in each case.


| Service                            | `Dallas (us-south)` | `Washington (us-east)`  |`Toronto (ca-tor)` | `Sao Paulo (br-sao)` |
|------------------------------------|---------------------|-------------------------|-------------------|----------------------|
| {{site.data.keyword.cloudcerts_full_notm}}                      | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |  |
| {{site.data.keyword.appid_full}}                                | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |        
| {{site.data.keyword.keymanagementservicelong}}                  | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}} | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.security-advisor_long}}                     | ![Checkmark icon](images/checkmark-icon.svg) |    |   
| {{site.data.keyword.secrets-manager_full}}  | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) |
{: caption="Table 13. Security services integration in America's locations" caption-side="top"}
{: #cs-sec-table-1}
{: tab-title="America"}
{: tab-group="cs_sec"}
{: class="simple-tab-table"}
{: row-headers}

| Service     | `Tokyo (jp-tok)`   | `Sydney (au-syd)`   | `Osaka (jp-osa)` | 
|-------------|--------------------|---------------------|-------------------|
| {{site.data.keyword.cloudcerts_full_notm}}                      | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.appid_full}}                                | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) | |
| {{site.data.keyword.keymanagementservicelong}}                  | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) | 
| {{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}} |   ![Checkmark icon](images/checkmark-icon.svg)   | ![Checkmark icon](images/checkmark-icon.svg) | |
| {{site.data.keyword.security-advisor_long}}                     |      |     |   |
| {{site.data.keyword.secrets-manager_full}}       | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) | |
{: caption="Table 13. Security services integration in AP locations" caption-side="top"}
{: #cs-sec-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="cs_sec"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                                       |`Frankfurt (eu-de)`                                 | `London (eu-gb)` |
|---------------------------------------------------------------|----------------------------------------------------|------------------|
| {{site.data.keyword.cloudcerts_full_notm}}                    | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.appid_full}}                              | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) |   
| {{site.data.keyword.keymanagementservicelong}}                | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}} | ![Checkmark icon](images/checkmark-icon.svg) |  ![Checkmark icon](images/checkmark-icon.svg)  |
| {{site.data.keyword.security-advisor_long}}                     |   | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.secrets-manager_full}}  | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) |
{: caption="Table 13. Security services integration in Europe locations" caption-side="top"}
{: #cs-sec-table-3}
{: tab-title="Europe"}
{: tab-group="cs_sec"}
{: class="simple-tab-table"}
{: row-headers}


## Storage services
{: #cloud_services_locations_storage}

| Service                            | `Dallas (us-south)` | `Washington (us-east)`  |`Toronto (ca-tor)` | `Sao Paulo (br-sao)` |
|------------------------------------|---------------------|-------------------------|-------------------|----------------------|
| {{site.data.keyword.cos_full_notm}}  `[*]`          | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg)  |
| {{site.data.keyword.mdms_short}}            | ![Checkmark icon](images/checkmark-icon.svg)  |       |  
{: caption="Table 14. Storage services integration in America locations" caption-side="top"}
{: #cs-storage-table-1}
{: tab-title="America"}
{: tab-group="cs-storage"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                        | `Tokyo (jp-tok)` |`Sydney (au-syd)`           | `Seoul (kr-seo)` |
|------------------------------------------------|------------------|----------------------------|-------------------|
| {{site.data.keyword.cos_full_notm}}  `[*]`        | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) | `Events are available through the Activity Tracker Tokyo (jp-tok) instance` |
| {{site.data.keyword.mdms_short}}            |   |       |   |
{: caption="Table 14. Storage services integration in AP locations" caption-side="top"}
{: #cs-storage-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="cs-storage"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                                       |`Frankfurt (eu-de)`  | `London (eu-gb)` |
|---------------------------------------------------------------|---------------------|------------------|
| {{site.data.keyword.cos_full_notm}}  `[*]`        | ![Checkmark icon](images/checkmark-icon.svg) |  ![Checkmark icon](images/checkmark-icon.svg)  | 
| {{site.data.keyword.mdms_short}}            |   |       |  
{: caption="Table 14. Storage services integration in Europe locations" caption-side="top"}
{: #cs-storage-table-3}
{: tab-title="Europe"}
{: tab-group="cs-storage"}
{: class="simple-tab-table"}
{: row-headers}

`[*]` {{site.data.keyword.cos_full_notm}} (COS) generates global, management, and data events. 
* By default, events that report on global actions such as the creation of a bucket are collected automatically. You can monitor these events through the {{site.data.keyword.at_short}} instance that is located in the Frankfurt location.
* Collection of management and data events in your account is optional. 
* **You must configure each bucket to enable management events, or management and data events.** You cannot enable data events only for a bucket. 

    * To monitor management events, you must configure a bucket and specify the {{site.data.keyword.at_short}} instance where those events will be available for monitoring.
    * To monitor data events, you must select the option **Track data events** when you associate a bucket with an {{site.data.keyword.at_short}} instance. 


## Web and mobile services
{: #cloud_services_locations_web}

| Service                            | `Dallas (us-south)` | `Washington (us-east)`  |`Toronto (ca-tor)` | `Sao Paulo (br-sao)` |
|------------------------------------|---------------------|-------------------------|-------------------|----------------------|
| {{site.data.keyword.mobilefoundation_short}}   |![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |          
{: caption="Table 15. Web and mobile services integration in America locations" caption-side="top"}
{: #cs-web-table-1}
{: tab-title="America"}
{: tab-group="cs-web"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                        | `Tokyo (jp-tok)` |`Sydney (au-syd)`           |
|------------------------------------------------|------------------|----------------------------|
| {{site.data.keyword.mobilefoundation_short}}   |               | ![Checkmark icon](images/checkmark-icon.svg) |           
{: caption="Table 15. Web and mobile services integration in AP locations" caption-side="top"}
{: #cs-web-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="cs-web"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                                       |`Frankfurt (eu-de)`  | `London (eu-gb)` |
|---------------------------------------------------------------|---------------------|------------------|
| {{site.data.keyword.mobilefoundation_short}}   | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg)   |   
{: caption="Table 15. Web and mobile services integration in Europe locations" caption-side="top"}
{: #cs-web-table-3}
{: tab-title="Europe"}
{: tab-group="cs-web"}
{: class="simple-tab-table"}
{: row-headers}

## VPC infrastructure services
{: #cloud_services_locations_vpc_infrastructure}

| Service                            | `Dallas (us-south)` | `Washington (us-east)`  |`Toronto (ca-tor)` | `Sao Paulo (br-sao)` |
|------------------------------------|---------------------|-------------------------|-------------------|----------------------|
| Storage resources                      | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg)   | ![Checkmark icon](images/checkmark-icon.svg)  |  |       
| Compute resources                      | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg)  |  | 
| Network resources                      | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg)  |  | 
| Load Balancer                          | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg)  |  | 
| VPN                                    | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg)  |  | 
{: caption="Table 16. VPC events in America's locations" caption-side="top"}
{: #cs-vpc-table-1}
{: tab-title="America"}
{: tab-group="cs_vpc"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                                         | `Tokyo (jp-tok)` |`Sydney (au-syd)`           |
|-----------------------------------------------------------------|------------------|----------------------------|
| Storage resources                      | ![Checkmark icon](images/checkmark-icon.svg)   | ![Checkmark icon](images/checkmark-icon.svg) |            
| Compute resources                      | ![Checkmark icon](images/checkmark-icon.svg)   | ![Checkmark icon](images/checkmark-icon.svg) |            
| Network resources                      | ![Checkmark icon](images/checkmark-icon.svg)   | ![Checkmark icon](images/checkmark-icon.svg) |
| Load Balancer                          | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) |
| VPN                                    | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) |
{: caption="Table 16. VPC events in AP locations" caption-side="top"}
{: #cs-vpc-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="cs_vpc"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                                       |`Frankfurt (eu-de)`  | `London (eu-gb)` |
|---------------------------------------------------------------|---------------------|------------------|
| Storage resources                      | ![Checkmark icon](images/checkmark-icon.svg)   | ![Checkmark icon](images/checkmark-icon.svg) |            
| Compute resources                      | ![Checkmark icon](images/checkmark-icon.svg)               | ![Checkmark icon](images/checkmark-icon.svg) |            
| Network resources                      | ![Checkmark icon](images/checkmark-icon.svg)               | ![Checkmark icon](images/checkmark-icon.svg) |       
| Load Balancer                          | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) |
| VPN                                    | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) |            
{: caption="Table 16. VPC events in Europe locations" caption-side="top"}
{: #cs-vpc-table-3}
{: tab-title="Europe"}
{: tab-group="cs_vpc"}
{: class="simple-tab-table"}
{: row-headers}



## Watson AI
{: #cloud_services_locations_watson_ai}


| Service                            | `Dallas (us-south)` | `Washington (us-east)`  |`Toronto (ca-tor)` | `Sao Paulo (br-sao)` |
|------------------------------------|---------------------|-------------------------|-------------------|----------------------|
| {{site.data.keyword.conversationshort}} | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.discoveryfull}}    | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.DSX_short}}        | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| Watson Knowledge Catalog               | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.knowledgestudioshort}} | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.languagetranslatorfull}} | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.pm_full}}          | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.nlushort}}          | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.texttospeechshort}} | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.speechtotextshort}} | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.wh-acd_short}} | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
{: caption="Table 17. Watson AI services integration in America locations" caption-side="top"}
{: #cs-watsonai-table-1}
{: tab-title="America"}
{: tab-group="cs-watsonai"}
{: class="simple-tab-table"}
{: row-headers}

| Service | `Tokyo (jp-tok)` | `Sydney (au-syd)` |  `Seoul (kr-seo)` |
|---------|------------------|-------------------|---------------------|
| {{site.data.keyword.conversationshort}} | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.discoveryfull}}     | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |         
| {{site.data.keyword.DSX_short}}         | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| Watson Knowledge Catalog                | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.knowledgestudioshort}} | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.languagetranslatorfull}} | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.pm_full}}           | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.nlushort}}          | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.texttospeechshort}} | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.speechtotextshort}} | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.wh-acd_short}} |   |   |   |
{: caption="Table 17. Watson AI services integration in AP locations" caption-side="top"}
{: #cs-watsonai-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="cs-watsonai"}
{: class="simple-tab-table"}
{: row-headers}

| Service |`Frankfurt (eu-de)` | `London (eu-gb)` |
|---------|--------------------|------------------|
| {{site.data.keyword.conversationshort}} | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.discoveryfull}}     | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.DSX_short}}         | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| Watson Knowledge Catalog                | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.knowledgestudioshort}} | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.languagetranslatorfull}} |![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.pm_full}}           | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.nlushort}}          | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.texttospeechshort}}      | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.speechtotextshort}}      | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.wh-acd_short}} |   |   |
{: caption="Table 17. Watson AI services integration in Europe locations" caption-side="top"}
{: #cs-watsonai-table-3}
{: tab-title="Europe"}
{: tab-group="cs-watsonai"}
{: class="simple-tab-table"}
{: row-headers}






## Power IaaS services
{: #cloud_services_locations_power-iaas}

| Service                            | `Dallas (us-south)` | `Washington (us-east)`  |`Toronto (ca-tor)` | `Sao Paulo (br-sao)` |
|------------------------------------|---------------------|-------------------------|-------------------|----------------------|
| Images                                 | ![Checkmark icon](images/checkmark-icon.svg)  | `Events are available through the Activity Tracker Dallas (us-south) instance.` |            
| Networks                               | ![Checkmark icon](images/checkmark-icon.svg)  | `Events are available through the Activity Tracker Dallas (us-south) instance.` | 
| PVM-Instance                           | ![Checkmark icon](images/checkmark-icon.svg)  | `Events are available through the Activity Tracker Dallas (us-south) instance.` | 
| Volumes                                | ![Checkmark icon](images/checkmark-icon.svg)  | `Events are available through the Activity Tracker Dallas (us-south) instance.` | 
| VPN                                    | ![Checkmark icon](images/checkmark-icon.svg)  | `Events are available through the Activity Tracker Dallas (us-south) instance.` | 
| PlacementGroups                        | ![Checkmark icon](images/checkmark-icon.svg)  | `Events are available through the Activity Tracker Dallas (us-south) instance.` | 
| CloudConnections                       | ![Checkmark icon](images/checkmark-icon.svg)  | `Events are available through the Activity Tracker Dallas (us-south) instance.` | 
| SAP                                    | ![Checkmark icon](images/checkmark-icon.svg)  | `Events are available through the Activity Tracker Dallas (us-south) instance.` | 
| NetworkPorts                           | ![Checkmark icon](images/checkmark-icon.svg)  | `Events are available through the Activity Tracker Dallas (us-south) instance.` | 
| Tenant                                 | ![Checkmark icon](images/checkmark-icon.svg)  | `Events are available through the Activity Tracker Dallas (us-south) instance.` | 
| SSHKeys                                | ![Checkmark icon](images/checkmark-icon.svg)  | `Events are available through the Activity Tracker Dallas (us-south) instance.` | 
| IKE                                    | ![Checkmark icon](images/checkmark-icon.svg)  | `Events are available through the Activity Tracker Dallas (us-south) instance.` | 
| IPSec                                  | ![Checkmark icon](images/checkmark-icon.svg)  | `Events are available through the Activity Tracker Dallas (us-south) instance.` | 
{: caption="Table 18. Power IaaS events in Americas locations" caption-side="top"}
{: #cs-power-iaas-table-1}
{: tab-title="Americas"}
{: tab-group="cs_power-iaas"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                                         | `Tokyo (jp-tok)` |`Sydney (au-syd)`           |
|-----------------------------------------------------------------|------------------|----------------------------|
| Images                                 | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) |            
| Networks                               | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) |
| PVM-Instance                           | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) |
| Volumes                                | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) |
| VPN                                    | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) |
| PlacementGroups                        | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) |
| CloudConnections                       | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) |
| SAP                                    | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) |
| NetworkPorts                           | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) |
| Tenant                                 | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) |
| SSHKeys                                | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) |
| IKE                                    | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) |
| IPSec                                  | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) |
{: caption="Table 18. Power IaaS events in AP locations" caption-side="top"}
{: #cs-power-iaas-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="cs_power-iaas"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                                       |`Frankfurt (eu-de)`  | `London (eu-gb)` |
|---------------------------------------------------------------|---------------------|------------------|
| Images                                 | ![Checkmark icon](images/checkmark-icon.svg)  | `Events are available through the Activity Tracker Frankfurt (eu-de) instance.` |             
| Networks                               | ![Checkmark icon](images/checkmark-icon.svg)  | `Events are available through the Activity Tracker Frankfurt (eu-de) instance.` | 
| PVM-Instance                           | ![Checkmark icon](images/checkmark-icon.svg)  | `Events are available through the Activity Tracker Frankfurt (eu-de) instance.` | 
| Volumes                                | ![Checkmark icon](images/checkmark-icon.svg)  | `Events are available through the Activity Tracker Frankfurt (eu-de) instance.` | 
| VPN                                    | ![Checkmark icon](images/checkmark-icon.svg)  | `Events are available through the Activity Tracker Frankfurt (eu-de) instance.` | 
| PlacementGroups                        | ![Checkmark icon](images/checkmark-icon.svg)  | `Events are available through the Activity Tracker Frankfurt (eu-de) instance.` | 
| CloudConnections                       | ![Checkmark icon](images/checkmark-icon.svg)  | `Events are available through the Activity Tracker Frankfurt (eu-de) instance.` | 
| SAP                                    | ![Checkmark icon](images/checkmark-icon.svg)  | `Events are available through the Activity Tracker Frankfurt (eu-de) instance.` | 
| NetworkPorts                           | ![Checkmark icon](images/checkmark-icon.svg)  | `Events are available through the Activity Tracker Frankfurt (eu-de) instance.` | 
| Tenant                                 | ![Checkmark icon](images/checkmark-icon.svg)  | `Events are available through the Activity Tracker Frankfurt (eu-de) instance.` | 
| SSHKeys                                | ![Checkmark icon](images/checkmark-icon.svg)  | `Events are available through the Activity Tracker Frankfurt (eu-de) instance.` | 
| IKE                                    | ![Checkmark icon](images/checkmark-icon.svg)  | `Events are available through the Activity Tracker Frankfurt (eu-de) instance.` | 
| IPSec                                  | ![Checkmark icon](images/checkmark-icon.svg)  | `Events are available through the Activity Tracker Frankfurt (eu-de) instance.` |         
{: caption="Table 18. Power IaaS events in Europe locations" caption-side="top"}
{: #cs-power-iaas-table-3}
{: tab-title="Europe"}
{: tab-group="cs_power-iaas"}
{: class="simple-tab-table"}
{: row-headers}

