---

copyright:
  years: 2019, 2020
lastupdated: "2020-03-11"

keywords: IBM Cloud, LogDNA, Activity Tracker, faq

subcollection: Activity-Tracker-with-LogDNA

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# Adoption guidelines: FAQ on AT events
{: #ibm_faq}

{:shortdesc}

## How to join the Stakeholders meeting and office hours

A stakeholders meeting runs fortnightly on Fridays. [Subscribe and enroll to the meeting](https://ec.yourlearning.ibm.com/w3/subscription/series/10008720)
{: important}

This meeting is an open invitation for Service Teams to learn more about what is happening with Activity Tracker, as well as get events reviewed.  Because Activity Tracker is required for One Cloud badging, and for Catalog Minimum (GA), there should be a plan for Activity Tracker by each Service team. This meeting is a good place to discuss your development of events, have questions answered, and evaluate your LogDNA entries in real time.

In the meeting, the following areas are covered:
* Activity Tracker news and updates 
* Upcoming Activity Tracker things to be aware of
* Event reviews
* Q&A time

The presentations and recordings of these sessions are available in the box folder [Recordings and ppts](https://ibm.box.com/s/47sqtlhgg21ck3nsuz9ib4kwbgupjlrd).


## How do I engage the AT team to review my AT events? 

To engage the AT tema to review your service's AT event prior to One Cloud badging, you must open an issue in the following git repo: [AT repo](https://github.ibm.com/activity-tracker/customer-issues/issues). Select the issue type `AT review`.
{: important}


## Types of events

A resource might be an entire service instance or a resource managed internally by a service. A resource can be whatever the user experiences as a "thing" that they can create/update/delete, regardless of its internal implementation. For example, creating a policy for a user. 

There are two kinds of events in Activity Tracker:

* **Management Events**:  These are events that are generated when an API call that changes the state of a Cloud resource reports activity on operational platform actions on a Cloud resource.

    Designated by the field: `dataEvent:false`.

* **Data Events**: These are events that are generated when an API call reads or modifies a resource's data. 

    Data events are stored with management events, but designated by the field: `dataEvent:true`. 
    
    There are an order-of-magnitude more data events than management events. 
    
    By default, all data events are collected. However, if your service generates high volumes of data events, you might choose to offer the users a way to opt out. Contact the AT team to work on a consistent UI.

## What events to define

Activity Tracker reports actions on the customer account. The actions can be initiated by a user, a service ID, or the IBM Cloud service.

    * A service should send events to report actions that report access, change, or management on resources in the IBM Cloud. These activities can be initiated by a physical person, by using an API key, or by using a token that is bound to a service.

    * A service should send events to report actions that the IBM Cloud service does in the customer account. These actions report access, change, or management on resources that is initiated by the service, for example, schedule a backup of a database that contains customer data. 

    * A service should send events for API calls that are made to the service and available externally. A service should not send events for the actions performed by microservices inside your service. **You must hide the service's internal implementation.**

A service should report `read`, `create`, `update`, and `delete` actions. 

    * Use the action `configure` to report update actions that report a toggle-type action (enable/disable or set-on/set-off).

    * AT events are not required for read operations that are triggered by an IBM Cloud service as part of their internal operations.

* A service in the IBM Cloud that starts sending audit events to Activity Tracker should generate an event for the following Cloud actions:

    * Access to resources (e.g. read action)
    * Create resources (e.g. create action)
    * Update resources (e.g. update action)
    * Delete resources (e.g. delete action)
    * Actions that involve access or retrieval of security data; for example, getting the details of a key in Key Protect, viewing metadata, listing resources.
    * Denied access (403), successful, and failed actions must ge reported for each AT event.

* The platform will generate these events for you:
    * Provisioning a service in the IBM Cloud.
    * Deprovisioning a service in the IBM Cloud.
    * Service plan changes.
    * Tagging of resources.


## What event fields can be sent and be GDPR compliant?

AT events that you send to the AT service must comply with GDPR. 

The following mandatory fields have been exempted for auditing purposes and can be included in AT events:

* *initiator.id*
* *initiator.name*
* *initiator.host.address*
* *target.id*
* *target.name*

AT customers do require the above information for “security/audit logging”. We discussed this topic in the [AT stakeholder meeting on 2018/09/21](https://ibm.webex.com/ibm/lsr.php?RCID=dd8e42624d974893bbd2de6c8160393a), with a couple of GDPR SMEs. The discussion starts at 7:30. The password is `3Mip3DWj`.

**It is your service’s responsibility to comply with GDPR. Do not include other customer data.**

If you are unsure about the information that you are sending, contact the GDPR SME responsible for your service. 

## What global domain should I use?

For global services in the IBM Cloud, use the <b>eu-de region</b> as the endpoint for global Activity Tracker events.



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

## Validating JSON: AT Event Linter tool

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




