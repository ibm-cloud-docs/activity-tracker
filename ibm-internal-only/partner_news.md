---

copyright:
  years: 2018
lastupdated: "2019-01-07"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# LogDNA News for Activity Tracker
{: #ibm_partner}

Activity Tracker(AT) and Log Analysis services are being moved to our partner [LogDNA](https://docs.logdna.com/docs). This page describes the transition for existing AT services to flow events to LogDNA. During the transition, events must flow to the current AT and LogDNA.
{:shortdesc}


## What Stays the Same
{: #same}


* The format of payload section in the event remains unchanged.
* Events flowing to the current AT will continue to work during the transition without any change to the events. So business as usual for customers.
* Services on Armada will continue to write AT events to disk. The fluentd plug-in will process the events and send them to the current AT.
* Non-Armada services please see the section [below](/docs/services/Activity-Tracker-with-LogDNA/ibm-internal-only/partner_news.html#ingestion).


## What Changes (Minor Changes)
{: #change}

Minor changes are required to send events to LogDNA. 

* two new fields will be added to each event. 
* one field has a format change in each event
* an additional plug-in to send events to logDNA

The three sections below provide a high level view of the new/modified fields and plug-in. Detailed information on the fields can be found [here](/docs/services/Activity-Tracker-with-LogDNA/ibm-internal-only/event_definition.html#new).

**Two new fields**

Two new fields will be added at the root level of the event structure. These are used by LogDNA to route the events. 

* **logSourceCRN** - This CRN is used to route the message to the service instance that generated the event. If this field is not present, the event will not be routed to the customer.
* **saveServiceCopy** - Used to indicate if the service wants to save a copy of their event. If this field is not supplied, the event will be saved for the service. 

**One modified format for a field**

The LogDNA UI will use the existing **message** field in the payload object as summary of the log line. This will enhance the customer experience when looking at events. The message field should follow the format defined [here](/docs/services/Activity-Tracker-with-LogDNA/ibm-internal-only/event_definition.html#new). This will allow us to present to the customer a consistent, easy to read summary of the event from all the services using AT.

**High-level view of updated event object**

```
JSON 
{
  'payload': {'message': <new_msg_format>, /* existing CADF fields */},
  'meta': {<meta>},
  'logSourceCRN': <crn_of_serviceInstance>, 
  'saveServiceCopy: true
}
```
{: codeblock}


**Additional plug-in to send events to LogDNA**

* Services on Armada will install the [LogDNA Kubernetes Agent](https://docs.logdna.com/docs/kubernetes).
* Super simple install. LogDNA will provide you the exact two commands you need to run.
* In the future the install and updates will be managed by Armada.


## Demo
{: #demo}

During a recent AT stakeholder meeting, we demonstrated LogDNA, the new/modified fields, and how our AT events  will be displayed in LogDNA.

See [this video](https://ibm.webex.com/ibm/lsr.php?RCID=4f9bf0967f2d4fb08debeaf118c57bc0) (password Qud4zPyc) for the demo.


## Approximate Timeline
{: #timeline}

### Phase 1: Now
{: #phase1}

* LogDNA working on code changes and getting into the IBM Cloud
* Services can prepare their events to support LogDNA

Service steps for Phase 1:

* Armada based services can update their events with the two new and one modified fields.
* See detailed documentation on the fields [here](/docs/services/Activity-Tracker-with-LogDNA/ibm-internal-only/event_definition.html#new).

### Phase 2: Now
{: #phase2}

* LogDNA will be available inside the IBM Cloud. Look for an announcement in our slack channel **activity-tracker-user** and stakeholder meeting.
* Optimized AT user experience provisioning for services running in Armada/Kubernetes. Traditional provisioning from the catalog will also be available.
* AT events can now be sent to the legacy AT and LogDNA. At this time only service records will be appear in LogDNA.

Service steps for Phase 2:

* Update event with new and modified fields if you have not already done this.
* Provision LogDNA, getting your service's ingestion key
* Install [LogDNA Kubernetes agent](https://docs.logdna.com/docs/kubernetes), using your service's ingestion key.
* Verify your service events show up in legacy AT and in LogDNA. **NOTE**: The event summary log line will not contain your message in this phase. This will be available in Phase 3


### Phase 3: Activate an AT account for your service - ET end of January
{: #phase3}

* LogDNA will have full AT functionality in the IBM Cloud.
* AT events in LogDNA can now be saved for your service and the customer. This means an IBM Cloud customer can provision a LogDNA instance, specifically for receiving AT events from services they are using.
* The message field will now show up in the log line summary.

Service steps for Phase 3:

* Services can now verify AT events sent to account and customer. 
* Services **must** continue to send events to the legacy AT. 

### Phase 4: Service stop sending event to legacy AT
{: #phase4}

* All services are sending to both legacy AT and LogDNA.
* Services can now stop sending events to legacy AT

Service steps for Phase 4:

* Services must verify that all events sent to the legacy AT show up in LogDNA.
* Removal of fluentd plugin to stop events being sent to legacy AT



## Ingestion by LogDNA
{: #ingestion}

We expect most services using AT will be hosted in Armada. These services are following our container based strategy, [write to service](/docs/services/Activity-Tracker-with-LogDNA/ibm-internal-only/kube.html#ibm_kube). This strategy writes AT events to a file in /var/log/at and a fluentd plug-in reads the events and sends them to the legacy Activity Tracker. For sending events to LogDNA, we will continue with this strategy. The LogDNA Kubernetes agent will read from the same directory and forward the events to LogDNA. 

This architecture has the following advantages:

1. Easy to install & configure. Only requires two simple `kubectl` commands.
1. Smooth transition. The Kube agent runs alongside fluentd to send to old AT and new AT at once.
1. Persist data in an outage. AT events are less likely to be lost on disk than in memory.
1. Supports operational logs at the same time. This includes the service's normal logs and super tenant logs.
1. Armada will eventually handle the Kube agent's lifecycle. Services will be responsible for install/update initially, but not long-term.

<a name="otherapproach"></a>
If your service **must** do something different:

* LogDNA has good ingestion options (agents, libraries, API), but...
* Your service is responsible to deliver all of the advantages listed above. 
