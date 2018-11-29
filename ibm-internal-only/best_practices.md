---

copyright:
  years: 2018
lastupdated: "2018-11-29"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# FAQ and Adoption guidelines
{: #ibm_faq}


{:shortdesc}


## How to send events to AT Using Armada and fluentd (strategic approach)



**Services on Armada must use this approach.**  

When your service runs on Armada containers, 

1. Send your events using the fluentd plugin built into containers. Sending events is a simple as writing the event to a file. 
2. Use an AT token versus an IAM token. 

Then, rely on the Write by Service (Kube) pattern to send the events to Activity Tracker.

For more information, see [Write by Service (IBM Cloud Container Service)](https://pages.github.ibm.com/activity-tracker/getting-start/kube/).



## How to send events to AT Using the API (Deprecated)

**Services that do not run on Armada will need to use the Activity Tracker API. In the future we will provide another alternative and remove this API.**

* Use **Version 3** of the Activity Tracker API. 

* Use an IAM token to send events to Activity Tracker.

* Use protobuf in v3 to send batches of up to 128 events quickly, rather than sending them individually.

For more information, see [Trail API](https://pages.github.ibm.com/activity-tracker/api-spec/v3/#/Trail_API).

## Types of events

There are two kinds of events in Activity Tracker:

* **Management Events**:  These are events that are generated when an API call changes the state of a Cloud resource. A resource might be an entire service instance or a resource managed internally by a service. A resource can be whatever the user experiences as a "thing" that they can create/update/delete, regardless of its internal implementation. For example, creating a policy for a user. 

* **Data Events**: These are events that are generated when an API call retrieves the data from a resource. There are an order-of-magnitude more data events than management events, so the user must opt in to start saving them. **NOTE: Data events are not currently supported in Activity Tracker, but will be in the future.**

## What events to define

* Only send events for customer initiated activities. These activities can be initiated by a physical person, by using an API key, or by using a token that is bound to a service.

* Send events for your service, not for the microservices inside your service. You must hide the service's internal implementation.

* A service in the IBM Cloud that starts sending audit events to Activity Tracker should generate an event for the following Cloud actions:

    * Create resources.
    * Update resources.
    * Delete resources.
    * Actions that involve access or retrieval of security data; for example, getting the details of a key in Key Protect.

* BSS or Cloud Foundry will generate these events for you:
    * Provisioning a service in the IBM Cloud.
    * Deprovisioning a service in the IBM Cloud.
    * Service plan changes.

## How many events/minute can my service send to AT?

Events are stored in the Log Analysis service. Depending on the events per minute, you might need to contact the AT team.

* 1 - 100 events/min requires no additional Log Analysis resource to be allocated.
* 101 - 250 events/min may require additional Log Analysis resources. Contact AT team.
* \> 250 events/min will require additional Log Analysis resources. Contact the AT team.



## Are there any mandatory fields in an event? 

**You must include all mandatory fields in every AT event.** Activity Tracker events comply with the industry standard CADF format. For more information about the mandatory fields you need to provide, see [Event Fields](https://pages.github.ibm.com/activity-tracker/getting-start/event/).

**target.id** is a mandatory field that must be set to the CRN of the resource on the IBM Cloud. When you define sets of events for a sub-resource in your service, use the same CRN for create, update, delete, and any other events that apply to that sub-resource.

There are some optional fields that are recommend to be set to enhance the user experience:

* **target.name**: Set this field to the human readable name of the cloud resource on which the action is being performed. This is the value a user would see on the Cloud UI or running a command.
* **initiator.name**: Set this field to the username that is associated with the IBMID or service ID that is used to initiate an action. 
* **requestData** and **responseData**: Set data in these field that provide useful information to the user. These fields must be set to valid JSON, where an object (like requestData) can contain one or more child elements. The child elements must be simple and not contain nested structures. For example, if you upgrade the version of an object, and only specify the mandatory fields, the user will not know what was the original version and the one that the object was upgraded to. 

## What event fields can be sent and be GDPR compliant?

AT events that you send to the AT service must comply with GDPR. 

The following mandatory fields have been exempted for auditing purposes and can be included in AT events:

* *initiator.id*
* *initiator.name*
* *initiator.host.address*
* *target.id*
* *target.name*

**It is your service’s responsibility to comply with GDPR. Do not include other customer data.**

If you are unsure about the information that you are sending, contact the GDPR SME responsible for your service. 

## Global domain

For global services in the IBM Cloud, use the <b>US South region</b> as the global account domain for Activity Tracker events.

For example, IAM and BSS send events that are not bound to a region. Those events are available to the user through the account domain in the US South region.



## How to set the AT domain where users can view events for your service

There are two service brokers a service can support:

* Cloud Foundry (CF) service broker:  Services are bound to a CF space.
* Resource controller (RC), which is the next-generation provisioning layer that manages the lifecycle of cloud resources. Services are bound to the account per region.

In AT, events can be hosted in a CF space domain or in the account domain. A Resource Group domain will be added in the future.

* **If you support a CF service broker, you can send either events at a space or account level.**
* **If you support a RC service broker, you can only send events at the account level (at this time).**

Use the following guidelines to decide where you should send your events:

* If your **service is managed by the CF service broker**: Send events to the **space domain** that is associated with the CF space where your service instance is running.

    * Set *userSpaceId* to the space ID of the customer
    * Set the *userAccountIds* to null.

* If your service is an **account level service**: Send events to the AT **account domain**.

    * Set the userSpaceId to null.
    * Set the userAccountIds to [user-account] (an array of one)

* If your **service is managed by the Resource Controller**: Send events to the AT **account domain**.

    * Set the userSpaceId to null.
    * Set the userAccountIds to [user-account] (an array of one)
    
    * In addition, consider using a field in `requestData` in the CADF payload to distinguish the Resource Group, such as `"resourceGroup": "default"`. This is a temporary work-around. **Note: Resource groups are not supported yet.** Resource Groups will be supported in the future.

In all cases:

* The `serviceProviderName`, `serviceProviderRegion`, and `serviceProviderProjectId` should be the same in the metadata as what you registered to AT. 
* The `userSpaceRegion` should match the serviceProviderRegion. AT currently only supports saving events in the region where the service is registered.

**Note:** If you are generating AT events in a region where AT is not deployed, you can send the events to a region where it is. You must register with AT in the target region, and use that information for sending the events. Consider GDPR and EU rules when transferring data. The users will have to look in the target region to see the data. This is a temporary work-around, and more regions will be supported in the future.




## What event fields can a user choose to generate useful reports?

**Cloud activity report for a resource**

* The field **target.id** contains the CRN of the cloud resource on which an action is executed. A user can use this field to obtain the activity trail for a specific cloud resource. 
* **Tip:** When you define your events, check that the create, update, delete, and other relevant actions that apply to a resource, all have the same value set for this field.

**Operational report**

* The field **outcome** contains the operation result. Users can search for failures to identify potential problems on specific cloud resources.
* **Tip**: Define events that report on failures, for example, a key could not be created, or a user could not execute action because it did not have permissions.

**Critical actions report**

* The field **severity** contains the information about the criticallity of the action on the Cloud. Users can search for critical events where permissions on users are changed, data is deleted, etc.



## Validating events

**You are responsible for verifying the correct format of each event before sending it to Activity Tracker.** The [AT event linter](https://github.ibm.com/activity-tracker/helloATv2/blob/master/README.md#at-event-linter) is a tool that validates a JSON event stored in a file. This is a great tool to use in your initial Activity Tracker development to ensure you are sending valid JSON to Activity Tracker. You can refer to the [events_schema.json](https://github.ibm.com/activity-tracker/helloATv2/blob/master/eventLinter/events_schema.json) for the validation rules.

**NOTE: First, Validate events for your service in staging. Once it is tested and compliant with AT adoption guidelines and CADF field formats, register your service for production and validate in production.**  WHY?  Customers and other services (such as SEIMs) are consuming AT events. Inconsistency in field formats and deviations of the AT event format causes parsing errors and customer unsatisfaction.

## Validating JSON

The [AT Event Linter](https://github.ibm.com/activity-tracker/helloATv2/blob/master/README.md#at-event-linter) is a tool that validates a JSON event stored in a file. 

This is a tool that you can use to ensure that you are sending valid JSON to Activity Tracker. 

* You can refer to the events_schema.json for the validation rules. 
* You can validate your AT event data using the Node.js and Go tools provided in the eventLinter folder.

For Node.js users:

1. Download the js file `at_event_linter.js` under the `eventLinter/node` folder
2. Run `npm install`
3. Rub `node at_event_linter.js <filename>` where filename points to the .json file holding your event data

For Go users:

1. Download the AT-event-linter executable under the `eventLinter/go` folder
2. Run `./AT-event-linter <filename>`


## Testing events

To test Activity Tracker, complete the following steps when your service forwards AT events to a space domain:

1. Create a new CF space, or use an existing space that is different from the one you service currently uses.
2. In that space, provision an instance of the Activity Tracker service and provision an instance of your service.
3. Within the context of the CF space, execute an action in your service that generates an AT event.
4. Launch the AT UI from the Cloud console. In the space domain view, verify that the event for the action you executed shows on the AT dashboard.

To test Activity Tracker, complete the following steps when your service forwards AT events to an account domain:

1. Create a new CF space, or use an existing space that is different from the one you service currently uses.
2. In that space, provision an instance of the Activity Tracker service.
3. Provision an instance of your service, if your service requires provisioning.
3. Execute an action in your service that generates an AT event.
4. Launch the AT UI from the Cloud console, select the account domain view, and verify that the event for the action you executed shows on the AT dashboard.

**Note:** To see account events, your user must have specific permissions. For more information, see [Viewing events](https://console.bluemix.net/docs/services/cloud-activity-tracker/how-to/manage-events-ui/viewing_events.html#view_acc_events).

## Documenting events


Information about AT events that customers can monitor must be documented. 

Your services technical writer must complete the following steps to document the Activity Tracker events that your service generates:

1. Create a topic that list all the Activity Tracker events. 
2. Add the topic to the Reference section of your service documentation. For example: [AT events](https://console.stage1.bluemix.net/docs/services/cloud-activity-tracker/reference/events.html#events)
3. Update the Activity Tracker documentation to include your service information.

For more information, see the section [Onboarding in Activity Tracker (AT)](https://console.stage1.bluemix.net/docs/developing/index.html)


For any documentation queries, contact Marisa (lopezdsr@uk.ibm.com) in slack.
For CADF compliance queries, contact Brendan Hayes (brendan.hayes@us.ibm.com) in slack.

Where will the information be available? 

Specific event information for a service is provided through a reference topic that is owned and maintained by the your service.

General overview services information about the events that services send to AT will be available through the following URLs: 

* Staging: https://console.stage1.bluemix.net/docs/services/cloud-activity-tracker/cloud_services.html#cloud_services

* Prod: https://console.bluemix.net/docs/services/cloud-activity-tracker/cloud_services.html#cloud_services
   
Your service is responsible for including the entry of your service in the list.