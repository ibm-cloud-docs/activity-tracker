---

copyright:
  years: 2019
lastupdated: "2019-03-26"

keywords: IBM Cloud, LogDNA, Activity Tracker, faq

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


# Documenting events
{: #ibm_docs}

Information about AT events that customers can monitor must be documented. 
{:shortdesc}

**Contacts for queries:**
* For any documentation queries, contact Marisa (lopezdsr@uk.ibm.com) in slack.
* For CADF compliance queries, contact Brendan Hayes (brendan.hayes@us.ibm.com) in slack.


## Who needs to document events that a service generated
{: #docs_0}

Your services technical writer must complete the following steps to document the Activity Tracker events that your service generates:



## What information should be documented
{: #docs_1}

You must create a topic that list all the Activity Tracker events. The name of the file should be: `at_events.md`. **All the events that are available in the Production environment must be documented.**

You can get the template, at [AT events template](https://github.ibm.com/Bluemix/docs/blob/staging/developing/content-kit/at-events-docs-template.md)

This topic should include the following information:
* Link to the [Getting started](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started-with-cla#getting-started-with-cla).
* List of actions and a brief description.
* Any information that mighrt be useful to the user related to each event.
* Information on where to find the events in the customer account.


You must add the topic to the Reference section of your service documentation. Use the template: [Template Activity Tracker events](/docs/services/Activity-Tracker-with-LogDNA/ibm-internal-only/at_events_acc_mgt.html#at_events)

You must update the [Activity Tracker documentation](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started-with-cla#getting-started-with-cla) to include your service information. The topic [Cloud services](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-cloud_services#cloud_services) 



## What documentation changes are required for AT with LogDNA
{: #docs_2}

When you on-board your service to {{site.data.keyword.at_full_notm}}, event's actions do not change.

You will need to update the topic [Cloud Services](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-cloud_services#cloud_services).

You will need to update the topic *at_events.md* to include the following information:

* Link to [Getting started with {{site.data.keyword.at_full_notm}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
* Information of where to find the events if the user is using the service {{site.data.keyword.at_full_notm}}.


## Where will the information be available?
{: #docs_3}

Specific event information for a service is provided through a reference topic that is owned and maintained by your service.

General overview services information about the events that services send to AT will be available through the following URL: 

* IBM Cloud Activity Tracker: [Cloud services](/docs/services/cloud-activity-tracker/cloud_services.html#cloud_services)
* {{site.data.keyword.at_full_notm}}: [Cloud Services](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-cloud_services#cloud_services)

