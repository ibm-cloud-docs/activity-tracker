---

copyright:
  years: 2019, 2020
lastupdated: "2020-03-11"

keywords: IBM Cloud, LogDNA, Activity Tracker, events, global, regional, data, management

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
{:important: .important}
{:note: .note}


# Enabling Activity Tracker events
{: #events_opt-in}

In {{site.data.keyword.at_full_notm}}, you can differentiate events by scope as global or location-based events, and by operational impact as management or data events.
{:shortdesc}



## Analyzing events
{: #event_types_analyze}


You might need to configure your service, upgrade your plan, or both to be able to collect Activity Tracker events.

The following table lists the services that require additional steps for you to be able to monitor the events that they generate:

| Service                    | Upgrade plan                       | Configure the service              |
|----------------------------|------------------------------------|------------------------------------|
| {{site.data.keyword.appid_full}}  | 
| {{site.data.keyword.cos_full}}    |




In {{site.data.keyword.at_full_notm}}, you can differentiate events by scope as [global events](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-event_types#event_types_global) or [location-based events](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-event_types#event_types_location), and by operational impact as management or data events. 

First, you need to check if you need to configure your service, upgrade your plan, or both to be able to collect Activity Tracker events.

* Management events are collected automatically for most services except Watson services that require a paid plan.

    If you are looking for Watson Activity Tracker events, check your plan and make sure you have a service plan that includes them.

* Data events are collected automatically for most services except the following ones:

    AppID requires a paid plan and you opting in.

    Cloud Object Storage requires that you enable them by bucket.

    Cloudant Database requires that you enable them per service instance.

Then, you need to determine the location of the events based on scope.

Global events are available through the Activity Tracker instance in Frankfurt. Therefore, to view global events, you must provision an instance of the {{site.data.keyword.at_full_notm}} service in Frankfurt.

For location-based events, you need to check the following scenarios to determine the Activity Tracker instance where the events are available for analysis:

* Scenario 1: The service is provisioned in a location where the {{site.data.keyword.at_full_notm}} service is available.

    1. Identify the location where your service is provisioned. 
    
    2. Check whether the {{site.data.keyword.at_full_notm}} service is available in that region. See [Locations](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-regions).

    3. Check that you have an Activity Tracker instance provisioned in the same location where your service is provisioned.

    In this scenario, you can find the Activity Tracker events that the service generates through the Activity Tracker instance in that location.

* Scenario 2: The service is provisioned in a location where the {{site.data.keyword.at_full_notm}} service is not available.

    1. Identify the location where your service is provisioned. 
        
    2. Check the [Cloud services locations](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-regions) to identify the Activity Tracker instance where events are available.


