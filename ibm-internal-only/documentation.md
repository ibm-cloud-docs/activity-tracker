---

copyright:
  years: 2019, 2020
lastupdated: "2020-01-08"

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

This topic should include the following information:
* Link to the [Getting started](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started-with-cla#getting-started-with-cla).
* List of actions and a brief description.
* Any information that might be useful to the user related to each event.
* Information on where to find the events in the customer account.

See [AT events template](https://github.ibm.com/Bluemix/docs/blob/staging/developing/content-kit/at-events-docs-template.md) and [Creating the Activity Tracker reference topic](/docs/developing/writing/markdown?topic=writing-atref).

After you create the topic, complete the following steps:

1. Add the topic to the `Reference` section of your service documentation. 
2. Add your service information to [Cloud services](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-cloud_services)
3. Add your service information to [Cloud services locations](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-cloud_services_locations)
4. Submit a PR. Then, notify the Activity Tracker docs owner to merge your PR. Slack handle: **@Marisa** or email: lopezdsr@uk.ibm.com. 



## Where will the information be available?
{: #docs_3}

Specific event information for a service is provided through a reference topic that is owned and maintained by your service.

General overview services information about the events that services send to AT will be available through the following URL: 
* [Cloud services](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-cloud_services)
* [Cloud services locations](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-cloud_services_locations)


