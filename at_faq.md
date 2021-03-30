---

copyright:
  years: 2019, 2021
lastupdated: "2021-01-05"

keywords: IBM Cloud, Activity Tracker, faq

subcollection: Activity-Tracker-with-LogDNA

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:download: .download}
{:faq: data-hd-content-type='faq'}
{:term: .term}
{:external: target="_blank" .external}

# Frequently asked questions (FAQs)
{: #at_faq}

Frequently asked questions about {{site.data.keyword.at_full}}.
{: shortdesc}

## Where can I find the list of Cloud services that generate Activity Tracker events?
{: #faq_1}
{: faq}

You can find information about the services that generate audit events and send those to Activity Tracker in the following documentation topic: [Cloud services](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-cloud_services).

## Where can I find the actions that a service generates?
{: #faq_2}
{: faq}

You can link to the list of events that each service generates from the following documentation topic: [Cloud services](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-cloud_services).

## Where can I find the events that a service generates?
{: #faq_3}
{: faq}

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




## How do I access and query data that has been archived for long term storage in COS?
{: #faq_4}
{: faq}

To access data, you can download the archived file locally.

To query the data, you can also use a service like SQL Query to query your COS archives and get information based on queries that you define. [Learn more](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-sqlquery).


## Can I import archived data back into the UI?
{: #faq_5}
{: faq}

You cannot import archived data into the UI. 

## How do I configure archiving for my instance?
{: #faq_6}
{: faq}

To configure archiving see [Archiving events to IBM Cloud Object Storage](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-archiving).

## I get an error when I try to provision an Activity Tracker instance
{: #faq_7}
{: faq}

You can only have 1 instance of the {{site.data.keyword.at_full_notm}} service per region. 


When an auditing instance already exists in a region, you get the following message when you try to provision it a second one: 

```
Service Broker returned error status code 400 when creating LogDNA-AT 
```
{: screen}


Most likely, your account administrator has already provisioned the auditing instances and has not given you permisisons to see work with them. 

To see auditing instances, you must have IAM platform permissions for the {{site.data.keyword.at_full_notm}} service. 

Therefore, if you cannot see any Auditing instances when you [launch the Activity Tracker observability dashboard](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-launch), check that you have permissions to at least view them. You need at least the **viewer** platform role to see the auditing instances. To learn more about IAM permissions, see [Managing access with IAM](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-iam). 



