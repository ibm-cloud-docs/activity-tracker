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


# Testing and validating integration of your service with AT 
{: #at_validate}

Each service is responsible for continuously validating that they send all of the Activity Tracker events for the actions that are documented in the service's Activity Tracker topic in IBM Cloud Docs.
{:shortdesc}

To generate your service's events, you may rely on continuous tests that the service is already running in production, or test each event manually. You must verify each event in an Activity Tracker instance (not the service's own internal AT Sender instance).
{: important}



## Step 1. Keep AT events documentation up to date

As you release new AT events for your service, add them to the AT documentation topic that must be available in the following location:

* **Topic title:** Auditing events for servicename
* **Location:**: **Enhancing security** topic group in the **How to** nav group* section of your services documentation


Make sure that all the actions that are listed in the topic published to customers is accurate.
{: important}

## Step 2. Keep information where AT events are available up to date

As you integrate with AT in a region, update the location table so customers can easily find out where to look for your events.

You must update your AT topic.

Also, make sure that you keep the information up to date in the global AT topic: [Cloud services by location](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-cloud_services_locations)

## Step 3. Keep information about how to enable AT events up to date

AT events are automatically collected. However there are some services that require a special service plan, or configuration to enable them.

If your service requores extra user work, check that you have clearly documented in your AT topic whether your service requires a special plan to receive the AT events in the account, whether they are collected automatically, or whether they need to be enabled (and how). 

Also, make sure that you keep the information up to date in the global AT topic: [Enabling Activity Tracker events](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-events_opt-in)

## Step 4. Define absence alerts to monitor when your service has a problem on individual actions

Services are responsible for monitoring that their logs and Activity Tracker events are being received by LogDNA.
{: note}

To identify quickly a problem where AT events might not be getting to the user or you might not be generating the events, consider the following information:

For each [ATS instance](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-enable_st#ATS), define absence alerts that allow you to identify quickly when your service is not generating an action. Make sure to monitor all actions.
{: important}

For each [ATR instance](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-enable_st#ATR), define absence alerts that allow you to detect when a user is not receiving your service's AT events.
{: important}

If your service generates logs that are available as platform logs, follow the same advise.
{: tip}


The alerts that you define can use the AT events from continuous tests that the service is already running in production.
{: note}


For information on how to define alerts, see [Alert if your service's logs or events are not flowing into LogDNA](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-enable_st#alert).

