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


# Documenting Activity Tracker events
{: #ibm_docs}

Information about AT events that customers can monitor must be documented. 
{:shortdesc}

Service teams are expected to provide the following documentation:

1. Publish the events they expose to customers.

    **Topic title:** Auditing events for servicename

    **Location:**: Add your topic in the **Enhancing security** topic group in the **How to** nav group* section  

    **Template:** [Sample](https://github.ibm.com/Bluemix/docs/blob/staging/developing/content-kit/at-events-docs-template.md)

    **Service Framework requirement:** [ONECLOUD: ARCH001oc.1 Customer Audit Logs via Activity Tracker with LogDNA](/docs/service-framework?topic=service-framework-one-cloud-requirements#onecloud-arch001oc-1-customer-audit-logs-via-activity-tracker-with-logdna)

2. Create a PR against the [AT Cloud Services page](https://github.ibm.com/cloud-docs/Activity-Tracker-with-LogDNA/blob/draft/cloud_services.md) to provide a link to your documentation page ( from step 1 ).
3. Create a PR against the [AT Cloud Services Locations page](https://github.ibm.com/cloud-docs/Activity-Tracker-with-LogDNA/blob/draft/cloud_services_locations.md) to indicate which production environments are currently supported.

Once you have a PR in place for 2 and 3, please contact [Marisa](mailto:lopezdsr@uk.ibm.com) (slack:@Marisa) to review and merge the changes.
{: note }


**Contacts for queries:**
* For any documentation and CADF compliance queries, contact Marisa (lopezdsr@uk.ibm.com) in slack.
* For SF queries, contact Brendan Hayes (brendan.hayes@us.ibm.com) in slack.


## Sections in the Auditing topic

The topic should include the following sections:

```md
## List of management events

You can classify by sub-resource/ sub-component type or other classification that can help the customer identify actions.

## List of data events

You can classify by sub-resource type or other classification that can help the customer identify actions.

## Enabling events

Some services requore a paid plan or additional configuration to enable events. Add any information on how to allow the customer to enable collection of events. 

### Enabling events through the UI

### Enabling events by using the command line

### Enabling events by using an API call

add example of cURL command including any headers like authorization headers that might be required.

## Viewing events


Add link to the section where your service is listed in the topic [Cloud services by location](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-cloud_services_locations).

## Analyzing events

Add information on custom fields that are included in requestData and responseData fields and that can help users understand your events.
```
{: codeblock}




