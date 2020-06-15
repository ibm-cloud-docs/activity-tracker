---

copyright:
  years: 2019, 2020
lastupdated: "2020-01-08"

keywords: IBM Cloud, LogDNA, Activity Tracker

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


# Documenting logs sent to Log Analysis with LogDNA
{: #ibm_docs_la}

Information about logs that customers can monitor must be documented. 
{:shortdesc}

Service teams are expected to provide the following documentation:

1. Publish the logs they expose to customers.

    **Topic title:** Logging for servicename

    **Location:**: Add your topic in the **Observability** topic group in the **How to** nav group* section  

    **Template:** [Sample](https://github.ibm.com/Bluemix/docs/blob/staging/developing/content-kit/at-events-docs-template.md)

    **Service Framework requirement:** [ONECLOUD: ARCH001oc.3 Internal and External Logging with LogDNA](/docs/service-framework?topic=service-framework-one-cloud-requirements#onecloud-arch001oc-3-internal-and-external-logging-with-logdna)

    **Sample:** [](/docs/Cloudant?topic=Cloudant-log-analysis-integration)

2. Create a PR against the [AT Cloud Services page](https://github.ibm.com/cloud-docs/Activity-Tracker-with-LogDNA/blob/draft/cloud_services.md) to provide a link to your documentation page ( from step 1 ).
3. Create a PR against the [AT Cloud Services Locations page](https://github.ibm.com/cloud-docs/Activity-Tracker-with-LogDNA/blob/draft/cloud_services_locations.md) to indicate which production environments are currently supported.

Once you have a PR in place for 2 and 3, please contact [Marisa](mailto:lopezdsr@uk.ibm.com) (slack:@Marisa) to review and merge the changes.
{: note }


**Contacts for queries:**
* For any documentation queries, contact Marisa (lopezdsr@uk.ibm.com) in slack.
* For CADF compliance queries, contact Brendan Hayes (brendan.hayes@us.ibm.com) in slack.


## Sections in the Auditing topic for services whose logs are available as platform logs

The topic should include the following sections:

```md
## Platform logs overview


## Enabling platform logs

### Enabling platform logs from the serviceName dashboard

### Enabling platform logs from the Logging dashboard



## Viewing logs

### Launching the LogDNA web UI from the serviceName dashboard

### Launching the LogDNA web UI from the Observability page



## Pre-defined fields per log type

Add subsections for different log record types.


## Analyzing logs for serviceName


Include information about the search queries customers can run to detect problems in your service.

Include information on indexed fields and how are they useful when monitoring logs for your service


```
{: codeblock}


## Sections in the Auditing topic for services that require to configure an agent to collect and forward logs

The topic should include the following sections:

```md
## Platform logs overview


## Configuring a LogDNA agent to collect logs




## Viewing logs

### Launching the LogDNA web UI from the serviceName dashboard

### Launching the LogDNA web UI from the Observability page



## Pre-defined fields per log type

Add subsections for different log record types.


## Analyzing logs for serviceName


Include information about the search queries customers can run to detect problems in your service.

Include information on indexed fields and how are they useful when monitoring logs for your service


```
{: codeblock}



