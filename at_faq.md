---

copyright:
  years: 2019, 2021
lastupdated: "2021-08-09"

keywords: IBM Cloud, {{site.data.keyword.at_short}}, faq

subcollection: activity-tracker

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

# FAQs
{: #at_faq}

Frequently asked questions about {{site.data.keyword.atracker_short}}.
{: shortdesc}


## Where can I find the list of Cloud services that generate {{site.data.keyword.atracker_short}} events?
{: #faq_1}
{: faq}

You can find information about the services that generate audit events and send those to {{site.data.keyword.atracker_short}} in the following documentation topic: [Cloud services](/docs/activity-tracker?topic=activity-tracker-cloud_services).

## Where can I find the actions that a service generates?
{: #faq_2}
{: faq}

You can link to the list of events that each service generates from the following documentation topic: [Cloud services](/docs/activity-tracker?topic=activity-tracker-cloud_services).

## Where can I find the events that a service generates?
{: #faq_3}
{: faq}

In {{site.data.keyword.atracker_short}}, you can differentiate events by scope as [global events](/docs/activity-tracker?topic=activity-tracker-event_types#event_types_global) or [location-based events](/docs/activity-tracker?topic=activity-tracker-event_types#event_types_location), and by operational impact as management or data events. 

First, you need to check if you need to configure your service, upgrade your plan, or both to be able to collect {{site.data.keyword.at_short}} events.

* Management events are collected automatically for most services except Watson services that require a paid plan.

    If you are looking for Watson {{site.data.keyword.atracker_short}} events, check your plan and make sure you have a service plan that includes them.

* Data events are collected automatically for most services except the following ones:

    AppID requires a paid plan and you opting in.

    Cloud Object Storage requires that you enable them by bucket.

    Cloudant Database requires that you enable them per service instance.

Then, you need to determine the location of the events based on scope.

For {{site.data.keyword.at_short}} event viewing, global events are available through the {{site.data.keyword.at_short}} instance in Frankfurt. Therefore, to view global events, you must provision an instance of the {{site.data.keyword.at_full_notm}} service in Frankfurt.

For {{site.data.keyword.atracker_short}} event routing, global events are collected in the region that you configure. Therefore, to find those events, you must find the route that is configured in 1 region of your account to collect global events. 

For location-based events, you need to check the following scenarios to determine the {{site.data.keyword.atracker_short}} instance where the events are available for analysis:

* Scenario 1: The service is provisioned in a location where the {{site.data.keyword.atracker_short}} service is available.

    1. Identify the location where your service is provisioned. 
    
    2. Check whether the {{site.data.keyword.atracker_short}} service is available in that region. See [Locations](/docs/activity-tracker?topic=activity-tracker-regions).

    3. For {{site.data.keyword.at_short}} event viewing, check that you have an {{site.data.keyword.atracker_short}} instance provisioned in the same location where your service is provisioned. For {{site.data.keyword.atracker_short}} event routing, check that you have a target and  aroute defines in that region.,

* Scenario 2: The service is provisioned in a location where the {{site.data.keyword.at_full_notm}} service is not available.

    1. Identify the location where your service is provisioned. 
        
    2. Check the [Cloud services locations](/docs/activity-tracker?topic=activity-tracker-regions) to identify the {{site.data.keyword.atracker_short}} instance where events are available.




## How do I access and query data that has been archived for long term storage in COS?
{: #faq_4}
{: faq}

This information applies only to {{site.data.keyword.at_short}} event viewing.
{: important}

To access data, you can download the archived file locally.

To query the data, you can also use a service like SQL Query to query your COS archives and get information based on queries that you define. [Learn more](/docs/activity-tracker?topic=activity-tracker-sqlquery).


## Can I import archived data back into the UI?
{: #faq_5}
{: faq}

This information applies only to {{site.data.keyword.at_short}} event viewing.
{: important}

You cannot import archived data into the UI. 

## How do I configure archiving for my instance?
{: #faq_6}
{: faq}

This information applies only to {{site.data.keyword.at_short}} event viewing.
{: important}

To configure archiving see [Archiving events to IBM Cloud Object Storage](/docs/activity-tracker?topic=activity-tracker-archiving).

## I get an error when I try to provision an {{site.data.keyword.at_short}} instance
{: #faq_7}
{: faq}

This information applies only to {{site.data.keyword.at_short}} event viewing.
{: important}

You can only have 1 instance of the {{site.data.keyword.at_full_notm}} service per region. 

When an auditing instance already exists in a region, you get a message when you try to provision an auditing instance a second time. 

Most likely, your account administrator has already provisioned the auditing instances and has not given you permisisons to see work with them. 

To see auditing instances, you must have IAM platform permissions for the {{site.data.keyword.at_full_notm}} service. 

Therefore, if you cannot see any Auditing instances when you [launch the {{site.data.keyword.at_short}} observability dashboard](/docs/activity-tracker?topic=activity-tracker-launch), check that you have permissions to at least view them. You need at least the **viewer** platform role to see the auditing instances. To learn more about IAM permissions, see [Managing access with IAM](/docs/activity-tracker?topic=activity-tracker-iam). 

## How do I create an API key?
{: #faq_8}
{: faq}

Complete the following steps:

1. Log in to {{site.data.keyword.cloud_notm}} with the [{{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cli-getting-started).

    ```sh
    ibmcloud login
    ```
    {: pre}

    If the login fails, run the `ibmcloud login --sso` command to try again. The `--sso` parameter is required when you log in with a federated ID. If this option is used, go to the link listed in the CLI output to generate a one-time passcode.
    {: note}

2. Create a [service ID](/docs/iam?topic=iam-serviceids) for your application.

    ```sh
    ibmcloud iam service-id-create <SERVICE_ID_NAME> [-d, --description DESCRIPTION]
    ```
    {: pre}

3. [Assign an access policy](/docs/iam?topic=iam-serviceidpolicy) for the service ID.

    You can assign access permissions for your service ID [by using the {{site.data.keyword.cloud_notm}} console](/docs/iam?topic=iam-serviceidpolicy#access_new).
    
    To learn how roles map to specific actions, see [Managing IAM access for {{site.data.keyword.atracker_full_notm}}](/docs/activity-tracker?topic=activity-tracker-iam).
    {: tip}

4. Create a [service ID API key](/docs/iam?topic=iam-serviceidapikeys).

    ```sh
    ibmcloud iam service-api-key-create <API_KEY_NAME> <SERVICE_ID_NAME> [-d, --description DESCRIPTION] [--file FILE_NAME]
    ```
    {: pre}

    Replace `SERVICE_ID_NAME` with the service ID name. 
    
    Save your API key by downloading it to a secure location.


## Can I choose the region where global events are collected?
{: #faq_9}
{: faq}

This information applies only to {{site.data.keyword.atracker_short}} event routing.
{: important}

Yes, you can choose the location where global events are collected. 

To configure a region, add 1 route in the region where you want to collect the global events, and set the property `receive_global_events` to `true`. [Learn more](/docs/activity-tracker?topic=activity-tracker-route#route_behaviour).



## I cannot find auditing events in my account. Where can I find them?
{: #faq_10}
{: faq}

In {{site.data.keyword.cloud_notm}}, auditing events are generated automatically with the exception of some services that require additional configuration or a specific service plan. For more information about these services, see [Enabling Activity Tracker events](/docs/activity-tracker?topic=activity-tracker-events_opt-in).

There are 2 ways by which you can access the auditing events in your account:
- Option 1: You can see auditing events through {{site.data.keyword.at_full_notm}} event viewing. This is the default option. For more information, see [Getting started tutorial](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-getting-st).
- Option 2: You can configure {{site.data.keyword.atracker_full_notm}} event routing per region in your account. For more information, see [Getting started tutorial](/docs/activity-tracker?topic=activity-tracker-getting-started).

In a region, you can manage auditing events in {{site.data.keyword.atracker_full_notm}} or in {{site.data.keyword.at_full_notm}}. Both options are not allowed in parallel per region. If a route is not defined in a region, by default, {{site.data.keyword.at_full_notm}} is the service that you can use to monitor auditing events.
{: important}




