---

copyright:
  years: 2019, 2024
lastupdated: "2024-06-19"

keywords:

subcollection: activity-tracker


---

{{site.data.keyword.attribute-definition-list}}

# IBM Cloud services that generate {{site.data.keyword.at_short}} events by location
{: #cloud_services_locations}

List of locations where {{site.data.keyword.cloud}} services are enabled to send events to {{site.data.keyword.at_full_notm}}:
{: shortdesc}


{{../log-analysis/_include-segments/deprecation_notice.md}}

## Analytics services
{: #cloud_services_locations_analytics}

| Service                            | `Dallas (us-south)` | `Washington (us-east)`  |`Toronto (ca-tor)` | `Sao Paulo (br-sao)` |
|------------------------------------|---------------------|-------------------------|-------------------|----------------------|
| {{site.data.keyword.iae_full}}               | ![Checkmark icon](images/checkmark-icon.svg) |                                      |
| {{site.data.keyword.sqlquery_full}}          | ![Checkmark icon](images/checkmark-icon.svg) |                                      |
| {{site.data.keyword.PA_SaaS_full}}           |  | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.dv_short}}               | ![Checkmark icon](images/checkmark-icon.svg) |
| Data Product Hub | ![Checkmark icon](images/checkmark-icon.svg) | | | |
{: caption="Analytics services integration in Americas locations" caption-side="top"}
{: #analytics-table-1}
{: tab-title="Americas"}
{: tab-group="analytics"}
{: class="simple-tab-table"}
{: row-headers}

| Service        | `Tokyo (jp-tok)`    |`Sydney (au-syd)` | `Osaka (jp-osa)` | `Chennai (in-che)` |
|----------------|---------------------|------------------|------------------|------------------|
| {{site.data.keyword.iae_full}}               | ![Checkmark icon](images/checkmark-icon.svg) |  |
| {{site.data.keyword.sqlquery_full}}          | |  |
| {{site.data.keyword.PA_SaaS_full}}          | |  |
| {{site.data.keyword.dv_short}}               | ![Checkmark icon](images/checkmark-icon.svg)   |  |
| Data Product Hub | | | | |
{: caption="Analytics services integration in AP locations" caption-side="top"}
{: #analytics-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="analytics"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                        |`Frankfurt (eu-de)`  | `London (eu-gb)` | `Madrid (eu-es)` |
|------------------------------------------------|---------------------|------------------|------------------|
| {{site.data.keyword.iae_full}}               | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) |   |
| {{site.data.keyword.sqlquery_full}}          | ![Checkmark icon](images/checkmark-icon.svg) |                                 |    |
| {{site.data.keyword.PA_SaaS_full}}          | |  |    |
| {{site.data.keyword.dv_short}}               | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) |    |
| Data Product Hub | | | |
{: caption="Analytics services integration in Europe locations" caption-side="top"}
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
{: caption="Compute VMware services integration in Americas locations" caption-side="top"}
{: #cs-vm-table-1}
{: tab-title="Americas"}
{: tab-group="cs-vm"}
{: class="simple-tab-table"}
{: row-headers}

| Service        | `Tokyo (jp-tok)`    |`Sydney (au-syd)` | `Osaka (jp-osa)` | `Chennai (in-che)` |
|----------------|---------------------|------------------|------------------|------------------|
| VMware Solutions Shared                            |  |  |
| KMIP for VMware                                | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
{: caption="Compute VMware services integration in Asia Pacific locations" caption-side="top"}
{: #cs-vm-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="cs-vm"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                                       |`Frankfurt (eu-de)`  | `London (eu-gb)` | `Madrid (eu-es)` |
|---------------------------------------------------------------|-------------------|----------------|-----------|
| VMware Solutions Shared                             | ![Checkmark icon](images/checkmark-icon.svg) |  |    |
| KMIP for VMware                                | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg)  |    |
{: caption="Compute VMware services integration in Europe locations" caption-side="top"}
{: #cs-vm-table-3}
{: tab-title="Europe"}
{: tab-group="cs-vm"}
{: class="simple-tab-table"}
{: row-headers}


## Classic services
{: #cloud_services_locations_classic}

| Service                            | `Dallas (us-south)` | `Washington (us-east)`  |`Toronto (ca-tor)` | `Sao Paulo (br-sao)` |
|------------------------------------|---------------------|-------------------------|-------------------|----------------------|
| {{site.data.keyword.baremetal_long}}           | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
{: caption="Compute infrastructure services integration in Americas locations" caption-side="top"}
{: #cs-infra-table-1}
{: tab-title="Americas"}
{: tab-group="cs-infra"}
{: class="simple-tab-table"}
{: row-headers}

| Service        | `Tokyo (jp-tok)`    |`Sydney (au-syd)` | `Osaka (jp-osa)` | `Chennai (in-che)` |
|----------------|---------------------|------------------|------------------|------------------|
| {{site.data.keyword.baremetal_long}}           | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
{: caption="Compute infrastructure services integration in AP locations" caption-side="top"}
{: #cs-infra-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="cs-infra"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                                       |`Frankfurt (eu-de)`  | `London (eu-gb)` | `Madrid (eu-es)` |
|---------------------------------------------------------------|---------------------|------------------|--------|
| {{site.data.keyword.baremetal_long}}           |  ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |    |
{: caption="Compute infrastructure services integration in Europe locations" caption-side="top"}
{: #cs-infra-table-3}
{: tab-title="Europe"}
{: tab-group="cs-infra"}
{: class="simple-tab-table"}
{: row-headers}

## Compute serverless services
{: #cloud_services_locations_serverless}

| Service                            | `Dallas (us-south)` | `Washington (us-east)`  |`Toronto (ca-tor)` | `Sao Paulo (br-sao)` |
|------------------------------------|---------------------|-------------------------|-------------------|----------------------|
| {{site.data.keyword.codeengineshort}}          | ![Checkmark icon](images/checkmark-icon.svg) | |
{: caption="Compute serverless services integration in Americas locations" caption-side="top"}
{: #cs-comp-table-1}
{: tab-title="Americas"}
{: tab-group="cs-comp"}
{: class="simple-tab-table"}
{: row-headers}

| Service        | `Tokyo (jp-tok)`    |`Sydney (au-syd)` | `Osaka (jp-osa)` | `Chennai (in-che)` |
|----------------|---------------------|------------------|------------------|------------------|
| {{site.data.keyword.codeengineshort}}          | ![Checkmark icon](images/checkmark-icon.svg) |   |
{: caption="Compute serverless services integration in AP locations" caption-side="top"}
{: #cs-comp-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="cs-comp"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                                       |`Frankfurt (eu-de)`  | `London (eu-gb)` | `Madrid (eu-es)` |
|---------------------------------------------------------------|---------------------|------------------|---------|
| {{site.data.keyword.codeengineshort}}          | ![Checkmark icon](images/checkmark-icon.svg) | |    |
{: caption="Compute serverless services integration in Europe locations" caption-side="top"}
{: #cs-comp-table-3}
{: tab-title="Europe"}
{: tab-group="cs-comp"}
{: class="simple-tab-table"}
{: row-headers}



## Container services
{: #cloud_services_locations_container}

{{site.data.keyword.registrylong_notm}}
:   You can track how users and applications interact with the {{site.data.keyword.registrylong_notm}} service. For information about the locations where the automatic collection of {{site.data.keyword.registryshort_notm}} service events is enabled, see [Auditing events for {{site.data.keyword.registrylong_notm}}](/docs/Registry?topic=Registry-at_events#at_events_locations).

{{site.data.keyword.containerlong_notm}}
:   For {{site.data.keyword.containerlong_notm}}, see [Viewing your cluster events](/docs/containers?topic=containers-at_events#at-ui).

{{site.data.keyword.satellitelong_notm}}
:   For {{site.data.keyword.satellitelong_notm}}, see [Viewing events for {{site.data.keyword.satelliteshort}}](/docs/satellite?topic=satellite-at_events#at_ui).

{{site.data.keyword.openshiftlong_notm}}
:   For {{site.data.keyword.openshiftlong_notm}}, see [Viewing your cluster events](/docs/openshift?topic=openshift-at_events#at-ui).

## Observability services
{: #cloud_services_locations_observability}

| Service                            | `Dallas (us-south)` | `Washington (us-east)`  |`Toronto (ca-tor)` | `Sao Paulo (br-sao)` |
|------------------------------------|---------------------|-------------------------|-------------------|----------------------|
| {{site.data.keyword.at_full_notm}} hosted event search offering | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg)| ![Checkmark icon](images/checkmark-icon.svg)| ![Checkmark icon](images/checkmark-icon.svg)|
| {{site.data.keyword.atracker_full_notm}}  | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg)|
| {{site.data.keyword.la_full_notm}}       | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg)| ![Checkmark icon](images/checkmark-icon.svg)| ![Checkmark icon](images/checkmark-icon.svg)|
| {{site.data.keyword.mon_full_notm}}      | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg)| ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.metrics_router_full_notm}} | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg)| | |
{: caption="Observability services in America's locations" caption-side="top"}
{: #cs-observability-table-1}
{: tab-title="America"}
{: tab-group="cs-observability"}
{: class="simple-tab-table"}
{: row-headers}

| Service        | `Tokyo (jp-tok)`    |`Sydney (au-syd)` |  `Osaka (jp-osa)` | `Chennai (in-che)` |
|----------------|---------------------|------------------|------------------|------------------|
| {{site.data.keyword.at_full_notm}} hosted event search offering | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.atracker_full_notm}}  | | | | |
| {{site.data.keyword.la_full_notm}}  | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.mon_full_notm}}      | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg)| ![Checkmark icon](images/checkmark-icon.svg) | |  |
| {{site.data.keyword.metrics_router_full_notm}} | | | | |
{: caption="Observability services in AP locations" caption-side="top"}
{: #cs-observability-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="cs-observability"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                                       |`Frankfurt (eu-de)`  | `London (eu-gb)` | `Madrid (eu-es)` |
|---------------------------------------------|---------------------|------------------|-----------|
| {{site.data.keyword.at_full_notm}}     | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |  ![Checkmark icon](images/checkmark-icon.svg)  |
| {{site.data.keyword.atracker_full_notm}}  | | |  ![Checkmark icon](images/checkmark-icon.svg)  |
| {{site.data.keyword.la_full_notm}}     | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |  ![Checkmark icon](images/checkmark-icon.svg)  |
| {{site.data.keyword.mon_full_notm}}      | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg)|  ![Checkmark icon](images/checkmark-icon.svg)  |
| {{site.data.keyword.metrics_router_full_notm}} | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg)|  ![Checkmark icon](images/checkmark-icon.svg)  |
{: caption="Observability services in Europe locations" caption-side="top"}
{: #cs-observability-table-3}
{: tab-title="Europe"}
{: tab-group="cs-observability"}
{: class="simple-tab-table"}
{: row-headers}

## Platform services
{: #cloud_services_locations_core_integrated}


| Global service                                  | Location |
|-------------------------------------------------|---------------------|
| Billing | `Events are available through the Activity Tracker Frankfurt (eu-de) instance` |
| User management | `Events are available through the Activity Tracker Frankfurt (eu-de) instance` |
| Provisioning | `Events are available through the Activity Tracker Frankfurt (eu-de) instance` |
| {{site.data.keyword.iamlong}}    | `Events are available through the Activity Tracker Frankfurt (eu-de) instance` |
| {{site.data.keyword.compliance_short}}   | `Events are available through the Activity Tracker Frankfurt (eu-de) instance` |
| Global Search Service | `Events are available through the Activity Tracker Frankfurt (eu-de) instance` |
| Catalog Management | `Events are available through the Activity Tracker Frankfurt (eu-de) instance` |
| Trusted profiles | `Events are available through the Activity Tracker Frankfurt (eu-de) instance` |
| Context-based restrictions | `Events are available through the Activity Tracker Frankfurt (eu-de) instance` |
| Projects | `Events are available through the Activity Tracker Frankfurt (eu-de) instance` |
{: caption="Integrated security services integration in America locations" caption-side="top"}




## Database services
{: #cloud_services_locations_database}

The following tables list the locations where automatic collection of database service logs is enabled. You can monitor logs through the instance that is available in the same location as your database resources, if you enable 1 instance in this location to host service platform logs. For locations where you can provision a service instance but the {{site.data.keyword.at_full_notm}} service is not available, specific detail about the location where you can monitor those logs is provided in each case.

| Service                            | `Dallas (us-south)` | `Washington (us-east)`  |`Toronto (ca-tor)` | `Sao Paulo (br-sao)` |
|------------------------------------|---------------------|-------------------------|-------------------|----------------------|
| {{site.data.keyword.cloudant_short_notm}}                       | ![Checkmark icon](images/checkmark-icon.svg)               | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.databases-for-mongodb_full_notm}}           | ![Checkmark icon](images/checkmark-icon.svg)               | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.databases-for-mysql_full}}           | ![Checkmark icon](images/checkmark-icon.svg)               | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.databases-for-enterprisedb_full_notm}}      | ![Checkmark icon](images/checkmark-icon.svg)               | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.databases-for-elasticsearch_full_notm}}     | ![Checkmark icon](images/checkmark-icon.svg)               | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.databases-for-etcd_full_notm}}              | ![Checkmark icon](images/checkmark-icon.svg)               | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.databases-for-postgresql_full_notm}}        | ![Checkmark icon](images/checkmark-icon.svg)`               | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.messages-for-rabbitmq_full_notm}}           | ![Checkmark icon](images/checkmark-icon.svg)               | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.databases-for-redis_full_notm}}             | ![Checkmark icon](images/checkmark-icon.svg)               | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.Db2_on_Cloud_long}}| ![Checkmark icon](images/checkmark-icon.svg)               | ![Checkmark icon](images/checkmark-icon.svg) |
{: caption="Database services integration in America locations" caption-side="top"}
{: #cs-dbs-table-1}
{: tab-title="America"}
{: tab-group="cs_dbs"}
{: class="simple-tab-table"}
{: row-headers}

| Service    | `Tokyo (jp-tok)`   |`Sydney (au-syd)` | `Chennai 01 (che01)`     |
|------------|--------------------|------------------|--------------------------|
| {{site.data.keyword.cloudant_short_notm}}                       | ![Checkmark icon](images/checkmark-icon.svg) |![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg)| ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.databases-for-mongodb_full_notm}}           | ![Checkmark icon](images/checkmark-icon.svg) |![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.databases-for-mysql_full}}           | ![Checkmark icon](images/checkmark-icon.svg) |![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.databases-for-enterprisedb_full_notm}}      | ![Checkmark icon](images/checkmark-icon.svg) |![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.databases-for-elasticsearch_full_notm}}     | ![Checkmark icon](images/checkmark-icon.svg) |![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.databases-for-etcd_full_notm}}              | ![Checkmark icon](images/checkmark-icon.svg) |![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.databases-for-postgresql_full_notm}}        | ![Checkmark icon](images/checkmark-icon.svg) |![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.messages-for-rabbitmq_full_notm}}           | ![Checkmark icon](images/checkmark-icon.svg) |![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.databases-for-redis_full_notm}}            | ![Checkmark icon](images/checkmark-icon.svg) |![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.Db2_on_Cloud_long}} | ![Checkmark icon](images/checkmark-icon.svg) |![Checkmark icon](images/checkmark-icon.svg) | |
{: caption="Database services integration in AP locations" caption-side="top"}
{: #cs-dbs-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="cs_dbs"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                                       |`Frankfurt (eu-de)`  | `London (eu-gb)` | `Madrid (eu-es)` |
|---------------------------------------------------------------|---------------------|------------------|----------|
| {{site.data.keyword.cloudant_short_notm}}                     | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |  ![Checkmark icon](images/checkmark-icon.svg)   |
| {{site.data.keyword.databases-for-mongodb_full_notm}}           | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg)            |  ![Checkmark icon](images/checkmark-icon.svg)  |
| {{site.data.keyword.databases-for-mysql_full}}           | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg)            |  ![Checkmark icon](images/checkmark-icon.svg)  |
| {{site.data.keyword.databases-for-enterprisedb_full_notm}}      | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg)            |  ![Checkmark icon](images/checkmark-icon.svg)  |
| {{site.data.keyword.databases-for-elasticsearch_full_notm}}   | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg)            |  ![Checkmark icon](images/checkmark-icon.svg)  |
| {{site.data.keyword.databases-for-etcd_full_notm}}            | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg)            |  ![Checkmark icon](images/checkmark-icon.svg)  |
| {{site.data.keyword.databases-for-postgresql_full_notm}}      | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg)            |  ![Checkmark icon](images/checkmark-icon.svg)  |
| {{site.data.keyword.messages-for-rabbitmq_full_notm}}         | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg)            |  ![Checkmark icon](images/checkmark-icon.svg)  |
| {{site.data.keyword.databases-for-redis_full_notm}}           | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg)            |  ![Checkmark icon](images/checkmark-icon.svg)  |
| {{site.data.keyword.Db2_on_Cloud_long}} | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |                        |    |
{: caption="Database services integration in Europe locations" caption-side="top"}
{: #cs-dbs-table-3}
{: tab-title="Europe"}
{: tab-group="cs_dbs"}
{: class="simple-tab-table"}
{: row-headers}


## Developer tools
{: #cloud_services_locations_devops}

The Apps service sends global events. These events are available through the Frankfurt instance.


| Service                            | `Dallas (us-south)` | `Washington (us-east)`  |`Toronto (ca-tor)` | `Sao Paulo (br-sao)` |
|------------------------------------|---------------------|-------------------------|-------------------|----------------------|
| {{site.data.keyword.apigw_full}}               | ![Checkmark icon](images/checkmark-icon.svg)   | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.cloud-shell_notm}}         | ![Checkmark icon](images/checkmark-icon.svg)   |                     |
| {{site.data.keyword.contdelivery_full}}        | ![Checkmark icon](images/checkmark-icon.svg)   | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg)   | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.bplong}}                   |  ![Checkmark icon](images/checkmark-icon.svg)  | `Events are available through the Dallas instance`  |
| {{site.data.keyword.en_full}}         | ![Checkmark icon](images/checkmark-icon.svg)   |                     |
| {{site.data.keyword.appconfig_full}}         | ![Checkmark icon](images/checkmark-icon.svg)   |   ![Checkmark icon](images/checkmark-icon.svg) |
{: caption="Developer tools services integration in America's locations" caption-side="top"}
{: #cs-dev-tools-table-1}
{: tab-title="America"}
{: tab-group="cs-dev_tools"}
{: class="simple-tab-table"}
{: row-headers}

| Service        | `Tokyo (jp-tok)`    |`Sydney (au-syd)` | `Osaka (jp-osa)` | `Chennai (in-che)` |
|----------------|---------------------|------------------|------------------|--------------------|
| {{site.data.keyword.apigw_full}}               | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |  | |
| {{site.data.keyword.cloud-shell_notm}}        | ![Checkmark icon](images/checkmark-icon.svg) |  |  | |
| {{site.data.keyword.contdelivery_full}}        | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |  |
| {{site.data.keyword.bplong}}                   |   |   |   | |
| {{site.data.keyword.en_full}}                   |   | ![Checkmark icon](images/checkmark-icon.svg)   |  | |
| {{site.data.keyword.appconfig_full}}                   |   | ![Checkmark icon](images/checkmark-icon.svg)   |  | |
{: caption="Developer tools services integration in AP locations" caption-side="top"}
{: #cs-dev-tools-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="cs-dev_tools"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                                       |`Frankfurt (eu-de)`  | `London (eu-gb)` | `Madrid (eu-es)` |
|---------------------------------------------------------------|---------------------|------------------|----------|
| {{site.data.keyword.apigw_full}}               | ![Checkmark icon](images/checkmark-icon.svg)   | ![Checkmark icon](images/checkmark-icon.svg) |    |
| {{site.data.keyword.cloud-shell_notm}}        | ![Checkmark icon](images/checkmark-icon.svg)   |                     |    |
| {{site.data.keyword.contdelivery_full}}        | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg)                    |    |
| {{site.data.keyword.bplong}}                   | ![Checkmark icon](images/checkmark-icon.svg) | `Events are available through the Frankfurt instance` |  `Events are available through the Frankfurt instance`  |
| {{site.data.keyword.en_full}}                  | | ![Checkmark icon](images/checkmark-icon.svg)  |  ![Checkmark icon](images/checkmark-icon.svg)  |
| {{site.data.keyword.appconfig_full}}                  | | ![Checkmark icon](images/checkmark-icon.svg)  |    |
{: caption="Developer tools services integration in Europe locations" caption-side="top"}
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
{: caption="Integration services integration in America's locations" caption-side="top"}
{: #cs_integration-table-1}
{: tab-title="America"}
{: tab-group="cs_integration"}
{: class="simple-tab-table"}
{: row-headers}

| Service        | `Tokyo (jp-tok)`    |`Sydney (au-syd)` | `Osaka (jp-osa)` | `Chennai (in-che)` |
|----------------|---------------------|------------------|------------------|--------------------|
| {{site.data.keyword.messagehub}}               | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) | |
| MQ on IBM Cloud                                |                  | ![Checkmark icon](images/checkmark-icon.svg)  | | |
{: caption="Integration services integration in AP locations" caption-side="top"}
{: #cs_integration-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="cs_integration"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                                       |`Frankfurt (eu-de)`  | `London (eu-gb)` | `Madrid (eu-es)` |
|---------------------------------------------------------------|---------------------|------------------|----------|
| {{site.data.keyword.messagehub}}               | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |  ![Checkmark icon](images/checkmark-icon.svg)  |
| MQ on IBM Cloud                                | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |    |
{: caption="Integration services integration in Europe locations" caption-side="top"}
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
{: caption="Network services that are global" caption-side="top"}



## Security services
{: #cloud_services_locations_security}

The following tables list the locations where automatic collection of security service logs is enabled. You can monitor logs through the instance that is available in the same location as your security resources, if you enable 1 instance in this location to host service platform logs. For locations where you can provision a service instance but the {{site.data.keyword.at_full_notm}} service is not available, specific detail about the location where you can monitor those logs is provided in each case.


| Service                            | `Dallas (us-south)` | `Washington (us-east)`  |`Toronto (ca-tor)` | `Sao Paulo (br-sao)` |
|------------------------------------|---------------------|-------------------------|-------------------|----------------------|
| {{site.data.keyword.appid_full}}                                | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.keymanagementservicelong}}                  | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}} | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.security-advisor_long}}                     | ![Checkmark icon](images/checkmark-icon.svg) |    |
| {{site.data.keyword.secrets-manager_full}}  | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
{: caption="Security services integration in America's locations" caption-side="top"}
{: #cs-sec-table-1}
{: tab-title="America"}
{: tab-group="cs_sec"}
{: class="simple-tab-table"}
{: row-headers}

| Service     | `Tokyo (jp-tok)`   | `Sydney (au-syd)`   | `Osaka (jp-osa)` |
|-------------|--------------------|---------------------|-------------------|
| {{site.data.keyword.appid_full}}                                | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg)  |
| {{site.data.keyword.keymanagementservicelong}}                  | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}} |   ![Checkmark icon](images/checkmark-icon.svg)   | ![Checkmark icon](images/checkmark-icon.svg) | |
| {{site.data.keyword.security-advisor_long}}                     |      |     |   |
| {{site.data.keyword.secrets-manager_full}}       | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
{: caption="Security services integration in AP locations" caption-side="top"}
{: #cs-sec-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="cs_sec"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                                       |`Frankfurt (eu-de)`                                 | `London (eu-gb)` | `Madrid (eu-es)` |
|---------------------------------------------------------------|----------------------------------------------------|------------------|---------------|
| {{site.data.keyword.appid_full}}                              | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) |    |
| {{site.data.keyword.keymanagementservicelong}}                | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) |  ![Checkmark icon](images/checkmark-icon.svg)  |
| {{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}} | ![Checkmark icon](images/checkmark-icon.svg) |  ![Checkmark icon](images/checkmark-icon.svg)  |  ![Checkmark icon](images/checkmark-icon.svg)  |
| {{site.data.keyword.security-advisor_long}}                     |   | ![Checkmark icon](images/checkmark-icon.svg) |    |
| {{site.data.keyword.secrets-manager_full}}  | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
{: caption="Security services integration in Europe locations" caption-side="top"}
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
{: caption="Storage services integration in America locations" caption-side="top"}
{: #cs-storage-table-1}
{: tab-title="America"}
{: tab-group="cs-storage"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                        | `Tokyo (jp-tok)` |`Sydney (au-syd)`           |
|------------------------------------------------|------------------|----------------------------|
| {{site.data.keyword.cos_full_notm}}  `[*]`        | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
{: caption="Storage services integration in AP locations" caption-side="top"}
{: #cs-storage-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="cs-storage"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                                       |`Frankfurt (eu-de)`  | `London (eu-gb)` | `Madrid (eu-es)` |
|---------------------------------------------------------------|---------------------|------------------|---------|
| {{site.data.keyword.cos_full_notm}}  `[*]`        | ![Checkmark icon](images/checkmark-icon.svg) |  ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg)  |
{: caption="Storage services integration in Europe locations" caption-side="top"}
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


## VPC infrastructure services
{: #cloud_services_locations_vpc_infrastructure}

| Service                            | `Dallas (us-south)` | `Washington (us-east)`  |`Toronto (ca-tor)` | `Sao Paulo (br-sao)` |
|------------------------------------|---------------------|-------------------------|-------------------|----------------------|
| VPC                      | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg)   | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg)   |
| Load Balancer                          | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg)   |
| VPN                                    | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg)   |
| Client VPN                             | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg)   |
{: caption="VPC events in America's locations" caption-side="top"}
{: #cs-vpc-table-1}
{: tab-title="America"}
{: tab-group="cs_vpc"}
{: class="simple-tab-table"}
{: row-headers}

| Service     | `Tokyo (jp-tok)`   |`Sydney (au-syd)`    | `Osaka (jp-osa)` |
|-------------|--------------------|---------------------|-------------------|
| VPC                   | ![Checkmark icon](images/checkmark-icon.svg)   | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| Load Balancer                          | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| VPN                                    | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| Client VPN                             | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
{: caption="VPC events in AP locations" caption-side="top"}
{: #cs-vpc-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="cs_vpc"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                                       |`Frankfurt (eu-de)`  | `London (eu-gb)` | `Madrid (eu-es)` |
|---------------------------------------------------------------|---------------------|------------------|-----------|
| VPC                      | ![Checkmark icon](images/checkmark-icon.svg)   | ![Checkmark icon](images/checkmark-icon.svg) |  ![Checkmark icon](images/checkmark-icon.svg)  |
| Load Balancer                          | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) |    |
| VPN                                    | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) |    |
| Client VPN                             | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) |   |
{: caption="VPC events in Europe locations" caption-side="top"}
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
| {{site.data.keyword.pm_full}}          | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.nlushort}}          | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.texttospeechshort}} | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.speechtotextshort}} | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
{: caption="Watson AI services integration in America locations" caption-side="top"}
{: #cs-watsonai-table-1}
{: tab-title="America"}
{: tab-group="cs-watsonai"}
{: class="simple-tab-table"}
{: row-headers}

| Service | `Tokyo (jp-tok)` | `Sydney (au-syd)` |
|---------|------------------|-------------------|
| {{site.data.keyword.conversationshort}} | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.discoveryfull}}     | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.DSX_short}}         | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| Watson Knowledge Catalog                | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.knowledgestudioshort}} | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.pm_full}}           | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.nlushort}}          | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.texttospeechshort}} | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| {{site.data.keyword.speechtotextshort}} | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
{: caption="Watson AI services integration in AP locations" caption-side="top"}
{: #cs-watsonai-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="cs-watsonai"}
{: class="simple-tab-table"}
{: row-headers}

| Service |`Frankfurt (eu-de)` | `London (eu-gb)` | `Madrid (eu-es)` |
|---------|--------------------|------------------|------------------|
| {{site.data.keyword.conversationshort}} | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |    |
| {{site.data.keyword.discoveryfull}}     | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |    |
| {{site.data.keyword.DSX_short}}         | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |    |
| Watson Knowledge Catalog                | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |    |
| {{site.data.keyword.knowledgestudioshort}} | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |    |
| {{site.data.keyword.pm_full}}           | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |    |
| {{site.data.keyword.nlushort}}          | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |    |
| {{site.data.keyword.texttospeechshort}}      | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |    |
| {{site.data.keyword.speechtotextshort}}      | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |    |
{: caption="Watson AI services integration in Europe locations" caption-side="top"}
{: #cs-watsonai-table-3}
{: tab-title="Europe"}
{: tab-group="cs-watsonai"}
{: class="simple-tab-table"}
{: row-headers}






## Power IaaS services
{: #cloud_services_locations_power-iaas}

| Service                            | `Dallas (us-south)` | `Washington (us-east)`  |`Toronto (ca-tor)` | `Sao Paulo (br-sao)` |
|------------------------------------|---------------------|-------------------------|-------------------|----------------------|
| {{site.data.keyword.powerSys_notm}}                                 | ![Checkmark icon](images/checkmark-icon.svg)  | `Events are available through the Activity Tracker Dallas (us-south) instance.` |
| SSHKeys                                | ![Checkmark icon](images/checkmark-icon.svg)  | `Events are available through the Activity Tracker Dallas (us-south) instance.` |
{: caption="Power IaaS events in Americas locations" caption-side="top"}
{: #cs-power-iaas-table-1}
{: tab-title="Americas"}
{: tab-group="cs_power-iaas"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                                         | `Tokyo (jp-tok)` |`Sydney (au-syd)`           |
|-----------------------------------------------------------------|------------------|----------------------------|
| {{site.data.keyword.powerSys_notm}}                                 | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) |
| SSHKeys                                | ![Checkmark icon](images/checkmark-icon.svg)  | ![Checkmark icon](images/checkmark-icon.svg) |
{: caption="Power IaaS events in AP locations" caption-side="top"}
{: #cs-power-iaas-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="cs_power-iaas"}
{: class="simple-tab-table"}
{: row-headers}

| Service                                                       |`Frankfurt (eu-de)`  | `London (eu-gb)` | `Madrid (eu-es)` |
|---------------------------------------------------------------|---------------------|------------------|-------------|
| {{site.data.keyword.powerSys_notm}}                                 | ![Checkmark icon](images/checkmark-icon.svg)  | `Events are available through the Activity Tracker Frankfurt (eu-de) instance.` |    |
| SSHKeys                                | ![Checkmark icon](images/checkmark-icon.svg)  | `Events are available through the Activity Tracker Frankfurt (eu-de) instance.` |    |
{: caption="Power IaaS events in Europe locations" caption-side="top"}
{: #cs-power-iaas-table-3}
{: tab-title="Europe"}
{: tab-group="cs_power-iaas"}
{: class="simple-tab-table"}
{: row-headers}
