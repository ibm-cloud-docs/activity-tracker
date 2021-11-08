---

copyright:
  years: 2019, 2021
lastupdated: "2021-08-09"

keywords: IBM Cloud, {{site.data.keyword.atracker_short}}, events, security, auditlog

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}

---

# Auditing events for {{site.data.keyword.atracker_short}}
{: #at_events}

As a security officer, auditor, or manager, you can use the {{site.data.keyword.atracker_short}} service to track how users and applications interact with the {{site.data.keyword.atracker_short}} service in {{site.data.keyword.cloud}}.
{: shortdesc}


{{site.data.keyword.atracker_short}} records user-initiated activities that change the state of a service in {{site.data.keyword.cloud_notm}}. You can use this service to investigate abnormal activity and critical actions and to comply with regulatory audit requirements. In addition, you can be alerted about actions as they happen. The events that are collected comply with the Cloud Auditing Data Federation (CADF) standard. For more information, see the [getting started tutorial for {{site.data.keyword.atracker_short}}](/docs/activity-tracker?topic=activity-tracker-getting-started).

{{site.data.keyword.atracker_short}} automatically generates events so that you can track activity on your service instance.


## Management events for {{site.data.keyword.atracker_short}} event routing
{: #at_events_mgt_atracker}

### Targets
{: #at_events_mgt_target}

The following table lists the auditing events that are generated when you manage targets:

| Action                                            | Description                |
|---------------------------------------------------|----------------------------|
| `atracker.target.create`       | This event is generated when an administrator creates a new Cloud Object Storage (COS) target with specified COS endpoint information and credentials.  |
| `atracker.target.list` | This event is generated when an administrator lists all Cloud Object Storage (COS) targets defined under a region. |
| `atracker.target.get` | This event is generated when an administrator retrieves a target and its details by specifying the ID of the target.|
| `atracker.target.update` | This event is generated when an administrator updates a target details by specifying the ID of the target. |
| `atracker.target.delete` | This event is generated when an administrator deletes a target by specifying the ID of the target. |
{: caption="Table 1. Events for account settings actions" caption-side="top"} 


### Routes
{: #at_events_mgt_route}

The following table lists the auditing events that are generated when you manage routes:

| Action                                            | Description                |
|---------------------------------------------------|----------------------------|
| `atracker.route.create` | This event is generated when an administrator creates a route with rules defined how to route auditing events to targets for a region. |
| `atracker.route.list` | This event is generated when an administrator lists routes defined under this region.  |
| `atracker.route.get` | This event is generated when an administrator retrieves a route and its details by specifying the ID of the route. |
| `atracker.route.update` | This event is generated when an administrator replaces a route details by specifying the ID of the route. You can also get this event when you validate a target by checking the credentials to write to the bucket. |
| `atracker.route.delete` | This event is generated when an administrator deletes a route by specifying the ID of the route. |
{: caption="Table 2. Events for account settings actions" caption-side="top"} 


### Endpoints
{: #at_events_mgt_endpoint}

The following table lists the auditing events that are generated when you manage endpoints:

| Action                                            | Description                |
|---------------------------------------------------|----------------------------|
| `atracker.endpoint.set` | This event is generated when an administrator configures the public endpoint availability in a region. |
| `atracker.endpoint.get` | This event is generated when an administrator gets information about the public and private endpoints that are enabled in a region.  |

{: caption="Table 3. Events for account settings actions" caption-side="top"} 


## Management events for {{site.data.keyword.at_short}} hosted event search offerings
{: #at_events_mgt_at}

### Account settings
{: #at_events_acc_settings}

| Action                                            | Description                |
|---------------------------------------------------|----------------------------|
| `logdnaat.account.update`       | This event is generated when an administrator turns on or off a feature for an auditing instance. |
{: caption="Table 4. Events for account settings actions" caption-side="top"} 

The following table lists custom fields that are included in these events:

| Custom fields                      | Valid values         | Description                |
|------------------------------------|----------------------|----------------------------|
| `requestData.owneremail`        | `xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx@logdna.ibm.com`  | Defines an {{site.data.keyword.atracker_short}} account. |
| `requestData.type`              | `meta.addrawline` | Defines an {{site.data.keyword.atracker_short}} administrative feature. |
| `requestData.value`            | `false`   \n `true`  | When is set to `true`, the feature specified in the field `requestData.type` is enabled.  |
| `responseData.logdnaId`            | Sample `3a941d8ert`  | Defines the {{site.data.keyword.atracker_short}} ID that is associated with the {{site.data.keyword.atracker_short}} instance. | 
{: caption="Table 2. Custom fields for account settings actions" caption-side="top"} 



### Archiving
{: #at_events_archive}


| Action                                            | Description                |
|---------------------------------------------------|----------------------------|
| `logdnaat.account-archive-setting.configure` | This event is generated when an administrator configures archiving for an auditing instance. |
{: caption="Table 5. Events for archiving actions" caption-side="top"} 


The following table lists custom fields that are included in these events:

| Custom fields                      | Valid values         | Description                |
|------------------------------------|----------------------|----------------------------|
| `requestData.feature`              | `archive`            | Defines a {{site.data.keyword.atracker_short}} administrative feature. |
| `requestData.isEnabled`            | `false`   \n `true`  | Defines if archiving of the auditing instance to a COS bucket is configured.   \n When is set to `true`, archiving is enabled.  |
| `requestData.provider`             | `ibm`                | Defines the Cloud provider where data is archived. |
| `responseData.logdnaId`            | Sample `3a941d8ert`  | Defines the {{site.data.keyword.atracker_short}} ID that is associated with the {{site.data.keyword.atracker_short}} instance. | 
{: caption="Table 6. Custom fields for archiving actions" caption-side="top"} 


### Exclusion rules
{: #at_events_exclusion_rules}

| Action                              | Description                |
|-------------------------------------|----------------------------|
| `logdnaat.exclusion-rule.create`      | This event is generated when an administrator creates an exclusion rule through the UI. |
| `logdnaat.exclusion-rule.update`      | This event is generated when an administrator updates an exclusion rule through the UI. |
| `logdnaat.exclusion-rule.delete`      | This event is generated when an administrator deletes an exclusion rule through the UI. |
{: caption="Table 7. Events for exclusion rules actions" caption-side="top"} 

The following table lists custom fields that are included in exclusion rule events:

| Custom fields                | Description          |
|------------------------------|----------------------|
| `feature`                    | Defines an {{site.data.keyword.atracker_short}} administrative feature.   \n Valid value is `exclusion-rule`. |
| `ruleId`                     | Defines the ID of the rule. |
| `isEnabled`                  | Defines when the exclusion rule is enabled.   \n Set to `true` when the rule is enabled. |
| `requestData.hosts`          | Defines 1 or more hosts whose data is excluded from search. |
| `requestData.apps`           | Defines 1 or more apps whose data is excluded from search.  |
| `requestData.query`          | Defines an advanced query to refine the data that is excluded from search. |
| `requestData.description`    | Description of the exclusion rule. |
| `requestData.indexonly`      | Defines whether the data is available to see through the UI.   \n Set to `true` when data is visible but not available for search. |
| `responseData.logdnaId`      | Defines the {{site.data.keyword.atracker_short}} ID that is associated with the {{site.data.keyword.atracker_short}} instance. | 
{: caption="Table 8. Custom fields for exclusion rules actions" caption-side="top"} 


### Ingestion keys
{: #at_events_ingestion_keys}

| Action                               | Description                |
|--------------------------------------|----------------------------|
| `logdnaat.ingestion-key.create`        | This event is generated when an administrator creates an ingestion key through the UI. |
| `logdnaat.ingestion-key.delete`        | This event is generated when an administrator deletes an ingestion key through the UI. |
{: caption="Table 9. Events for ingestion keys actions" caption-side="top"} 

The following table lists custom fields that are included in these events:

| Custom fields                      | Valid values         | Description                |
|------------------------------------|----------------------|----------------------------|
| `requestData.key`                  | Masked field         | Use this field to identify the ingestion key that is created. |
| `requestData.keyType`              | `ingestion`          | Defines the type of key that is configured. |
| `responseData.logdnaId`            | Sample `3a941d8ert`  | Defines the {{site.data.keyword.atracker_short}} ID that is associated with the {{site.data.keyword.atracker_short}} instance. | 
{: caption="Table 10. Custom fields for ingestion keys actions" caption-side="top"} 




### Service keys
{: #at_events_service_keys}

| Action                               | Description                |
|--------------------------------------|----------------------------|
| `logdnaat.service-key.create`          | This event is generated when an administrator creates a service key through the UI. |
| `logdnaat.service-key.delete`          | This event is generated when an administrator deletes a service key through the UI. |
{: caption="Table 11. Events for service keys actions" caption-side="top"} 

The following table lists custom fields that are included in these events:

| Custom fields                      | Valid values         | Description                |
|------------------------------------|----------------------|----------------------------|
| `requestData.key`                  | Masked field         | Use this field to identify the service key that is created to export data by using the {{site.data.keyword.atracker_short}}  export API. |
| `requestData.keyType`              | `service`            | Defines the type of key that is configured. |
| `responseData.logdnaId`            | Sample `3a941d8ert`  | Defines the {{site.data.keyword.atracker_short}} ID that is associated with the {{site.data.keyword.atracker_short}} instance. | 
{: caption="Table 12. Custom fields for service keys actions" caption-side="top"} 


### Streaming events
{: #at_events_streaming}


| Action | Description |
|--------|-------------|
| `logdnaat.streaming-configuration.validate`   | This event is generated when you configure the connection in {{site.data.keyword.at_short}} to {{site.data.keyword.messagehub}}. |
| `logdnaat.streaming-samples.send`             | This event is generated when sample data is sent to verify the connection. |
| `logdnaat.account-streaming-setting.configure`| This event is generated when you start streaming. |
| `logdnaat.streaming-configuration.deactivate` | This event is generated when you stop streaming. |
| `logdnaat.streaming-logs.send`              | This event is generated when there is a failure streaming data. |
| `logdnaat.exclusion-rule.create`            | This event is generated when an streaming exclusion rule is configured. |
| `logdnaat.exclusion-rule.delete`            | This event is generated when an streaming exclusion rule is deleted. |
{: caption="Table 13. Events for streaming actions" caption-side="top"} 



### Parsing templates
{: #at_events_parsing}

| Action                                | Description                |
|---------------------------------------|----------------------------|
| `logdnaat.parsing-template.create`      | This event is generated when an administrator creates a parsing template through the UI. |
| `logdnaat.parsing-template.update`      | This event is generated when an administrator updates a parsing template through the UI. |
| `logdnaat.parsing-template.delete`      | This event is generated when an administrator deletes a parsing template through the UI. |
{: caption="Table 14. Events for parsing templates actions" caption-side="top"} 

The following table lists custom fields that are included in these events:

| Custom fields                | Description          | 
|------------------------------|----------------------|
| `requestData.feature`        | Defines an {{site.data.keyword.atracker_short}} administrative feature.   \n Valid value is `custom-parsing`. |
| `requestData.isEnabled`      | Defines when the template is enabled.   \n Set to `true` when the template is enabled. |
| `requestData.name`           | Defines the name of the template.   \n This field is available for create actions.|
| `requestData.query`          | Defines the query that is configured to identify log lines where the custome parsing is applied. |
| `requestData.templateId`     | Defines the ID of the template.   \n This field is available for update actions. |
| `responseData.logdnaId`      | Defines the {{site.data.keyword.atracker_short}} ID that is associated with the {{site.data.keyword.atracker_short}} instance. | 
{: caption="Table 15. Custom fields for parsing templates actions" caption-side="top"} 


### Configuration 
{: #at_events_configuration}

| Action                              | Description                |
|-------------------------------------|----------------------------|
| `logdnaat.configuration.import`      | This event is generated when an administrator imports user-metadata such as views, and alerts through the UI. |
| `logdnaat.configuration.export`      | This event is generated when an administrator exports user-metadata such as views, and alerts through the UI. |
{: caption="Table 16. Events for user-metadata related actions" caption-side="top"} 

The following table lists custom fields that are included in these events:

| Custom fields                | Description          | 
|------------------------------|----------------------|
| `feature`                    | Defines an {{site.data.keyword.atracker_short}} administrative feature.   \n Valid value is `export-configuration`. |
| `requestData.configResources` | Defines the list of resources that a user chooses to export or import. |
| `responseData.logdnaId`      | Defines the {{site.data.keyword.atracker_short}} ID that is associated with the {{site.data.keyword.atracker_short}} instance. | 
{: caption="Table 14. Custom fields for user-metadata related actions" caption-side="top"} 



## Data events for {{site.data.keyword.at_short}} hosted event search offerings
{: #at_events_data-at}

### Views
{: #at_events_data_views}

| Action                    | Description                |
|---------------------------|----------------------------|
| `logdnaat.view.create`      | This event is generated when a view is created. |
| `logdnaat.view.update`      | This event is generated when a view is updated. This event is also generated when an alert is attached or dettached from a view. |
| `logdnaat.view.delete`      | This event is generated when a view is deleted. |
{: caption="Table 17. Events for views" caption-side="top"} 


The following table lists custom fields that are included in these events:

| Custom fields                | Description          | 
|------------------------------|----------------------|
| `requestData.name`    | Defines the name of the view. |
| `requestData.query`   | Defines the search query that is applied to filter data in the view. |
| `requestData.hosts`   | Defines the list of hosts that are selected and whose data is included in the view. |
| `requestData.apps`    | Defines the list of apps that are selected and whose data is included in the view. |
| `requestData.levels`  | Defines the list of levels that are selected and whose data is included in the view. |
| `requestData.category` | Defines the category where the view is included. |
| `requestData.viewId`   | Defines the view ID. |
| `requestData.description` | Describes the view. | 
| `requestData.customLine` | Describes how the information is displayed in the view. |
| `responseData.logdnaId`      | Defines the {{site.data.keyword.atracker_short}} ID that is associated with the {{site.data.keyword.atracker_short}} instance. | 
{: caption="Table 18. Custom fields for view actions" caption-side="top"} 



### Presets (alerts)
{: #at_events_data_alerts}

| Action                     | Description                |
|----------------------------|----------------------------|
| `logdnaat.alert.create`      | This event is generated when an alert is created as a preset. |
| `logdnaat.alert.update`      | This event is generated when an alert is updated. |
| `logdnaat.alert.delete`      | This event is generated when an alert is deleted. |
{: caption="Table 19. Events for alerts" caption-side="top"} 

The following table lists custom fields that are included in these events:

| Custom fields                | Description          | 
|------------------------------|----------------------|
| `requestData.alertId`   | Defines the preset ID. |
| `requestData.name`    | Defines the name of the preset. |
| `requestData.preset`  | Defines whether the alert is defined as a preset. |
| `requestData.channels` | List of channels that are configured in a preset. Each channel includes information about the notification method and the trigger conditions per method. |
| `responseData.logdnaId`      | Defines the {{site.data.keyword.atracker_short}} ID that is associated with the {{site.data.keyword.atracker_short}} instance. | 
{: caption="Table 20. Custom fields for view actions" caption-side="top"} 


### Dashboards
{: #at_events_data_boards}

| Action                        | Description                |
|-------------------------------|----------------------------|
| `logdnaat.board.create`         | This event is generated when a dashboard is created. |
| `logdnaat.board.delete`         | This event is generated when a dashboard is deleted. |
| `logdnaat.board-graph.update`   | This event is generated when a graph is added to a dashboard. |
{: caption="Table 21. Events for dashboards" caption-side="top"} 


The following table lists custom fields that are included in these events:

| Custom fields                | Description          | 
|------------------------------|----------------------|
| `requestData.boardId`         | Defines the ID of the dashboard. |
| `requestData.category`       | Defines the category where the board is included. |
| `requestData.title`          | Defines the name of the dashboard. |
| `requestData.graphId`        | Defines the ID of a graph that is added to a board. | 
| `responseData.logdnaId`      | Defines the {{site.data.keyword.atracker_short}} ID that is associated with the {{site.data.keyword.atracker_short}} instance. | 
{: caption="Table 22. Custom fields for boards" caption-side="top"} 





## Viewing events
{: #at_events_ui}


### Viewing events for {{site.data.keyword.atracker_short}} event routing
{: #at_events_ui_atracker}

Location based events are automatically forwarded to the {{site.data.keyword.atracker_short}} target that is available in the same location (region).

Global events are available in the location that you configure to collect global events in your account.

{{site.data.keyword.atracker_short}} can have only one target and route per location. To view events, you must access the target and download the object.


### Viewing events for {{site.data.keyword.at_short}} hosted event search offerings
{: #at_events_ui-at}

 
Events that are generated by an instance of the {{site.data.keyword.at_short}} service are automatically forwarded to the {{site.data.keyword.at_short}} service instance that is available in the same location. For more information, see [Cloud services locations](/docs/activity-tracker?topic=activity-tracker-cloud_services_locations).

{{site.data.keyword.at_short}} can have only one instance per location. To view events, you must access the web UI of the {{site.data.keyword.at_short}} service in the same location where your service instance is available. For more information, see [Launching the web UI through the IBM Cloud UI](/docs/activity-tracker?topic=activity-tracker-launch).



## Analyzing events
{: #at_events_analyzing}

{{site.data.keyword.at_short}} hosted event search offerings events only report success outcomes.

{{site.data.keyword.at_short}} hosted event search offerings events that report update actions do not include information about the delta of the change. 
