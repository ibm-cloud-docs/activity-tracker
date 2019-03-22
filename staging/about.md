---

copyright:
  years: 2019
lastupdated: "2019-03-19"

keywords: IBM Cloud, LogDNA, Activity Tracker, overview

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





# Collecting events
{: #ov_collect}

The {{site.data.keyword.at_full_notm}} service captures activity data that is related to API calls and other actions that are made to selected cloud services in the {{site.data.keyword.cloud_notm}}. 

* Events are collected automatically. 
* Events that are collected in {{site.data.keyword.at_full_notm}} comply with the Cloud Auditing Data Federation (CADF) standard. The CADF standard defines a full event model that includes the information that is needed to certify, manage, and audit security of applications in cloud environments.
* {{site.data.keyword.at_full_notm}} stores and groups events by domain. There is an account domain per region, and a space domain per Cloud Foundry space. 

The CADF event model includes the following components:

<table>
  <caption>Table 1. Components that are available in a CADF event model</caption>
  <tr>
    <th>Component</th>
	<th>Description</th>
  </tr>
  <tr>
    <td>Action</td>
	<td>The action is the operation or activity that an initiator performs, attempts to perform, or is waiting to complete.</td>
  </tr>
  <tr>
    <td>Initiator</td>
	<td>The initiator is the resource that makes an API call and generates a CADF event. The event that is triggered depends on the action that is requested by the API call.</td>
  </tr>
  <tr>
    <td>Observer</td>
	<td>The observer is the resource that creates and stores a CADF record from information available in a CADF event.</td>
  </tr>
  <tr>
    <td>Outcome</td>
	<td>The outcome is the status of the action against the target.</td>
  </tr>
  <tr>
    <td>Target</td>
	<td>The target is the resource against which the action is performed, attempted to perform, or is pending to complete.</td>
  </tr>
</table>


Consider the following information when you work with the {{site.data.keyword.at_full_notm}} log in the {{site.data.keyword.IBM_notm}} public cloud:

* You can store only audit records for API calls made to resources that run in the {{site.data.keyword.IBM_notm}} public cloud.
* Only {{site.data.keyword.IBM_notm}} public cloud storage is used to collect events.
* Information is stored for 3 days. After that, the information is deleted on a first-in, first-out (FIFO) method.
* CADF events of type *Activity* are supported by the {{site.data.keyword.at_full_notm}} service.


## Provisioning Activity Tracker
{: #ov_provision}

To view events that are available through an account domain, you must provision the {{site.data.keyword.cloudaccesstrailshort}} service in a Cloud Foundry space in the region where you want to monitor API activity. Only the **account owner** can see account events.

To view events that are available through a space domain, you must provision the {{site.data.keyword.cloudaccesstrailshort}} service in the space  where you want to monitor API activity.

To learn how to provision the {{site.data.keyword.cloudaccesstrailshort}} service, see [Provisioning the {{site.data.keyword.cloudaccesstrailshort}} service](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-provision#provision).



## Analyzing activity logs
{: #ov_analyze}

You can analyze activity logs through the {{site.data.keyword.cloudaccesstrailshort}} UI in the {{site.data.keyword.cloud_notm}}, or by using Kibana, an open source tool. You can monitor events that are available in a specific space or at the account level.

You can search, analyze, and monitor activity logs for the last 24 hours through the {{site.data.keyword.cloudaccesstrailshort}} UI in the {{site.data.keyword.cloud_notm}}. For more information, see [Navigating to the {{site.data.keyword.cloudaccesstrailshort}} UI](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-launch_at_ui#launch_at_ui).

You can search, analyze, and monitor activity logs for the last 3 days through Kibana by using the {{site.data.keyword.cloudaccesstrailshort}} Kibana dashboard, or by creating your own custom dashboards. * **Note:** This feature is available for **Premium** plan users.

* For more information on how to launch Kibana, see [Navigating to the Kibana dashboard](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-launch_kibana#launch_kibana). 
* For a list of fields that you can use to analyze events in Kibana, see [{{site.data.keyword.cloudaccesstrailshort}} event fields](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-at_event#at_event)



## Pricing plans
{: #ov_pricing_plans}

Different pricing plans are available that you can choose for an {{site.data.keyword.la_full_notm}} instance. Each plan defines the number of days that data is retained for search, the number of users allowed to manage the data, and the LogDNA features that are enabled.

| Plan                     | 
|--------------------------|
| `30 days log search`  |
| `14 days log search`  |
| `7-day log search`   |
| `Lite`                  |
{: caption="Table 1. List of service plans" caption-side="top"} 

{{site.data.keyword.la_full_notm}} offers a `Lite` plan that you can use to view your logs as they pass through the system. You can view logs by using log tailing. You can also design filters to prepare for upgrading to a longer retention period plan. This plan has a 0-day retention period.

The following tables outline the different features that are included in each service plan:

| Feature                          | `30 day log search` plan | `14 days log search` plan    | `7 days log search plan     | `Lite` plan | 
|----------------------------------|-------------------------|-------------------------------|-----------------------------|--------------|
| `Logs are stored and searchable` | Yes - for 30 days       | Yes - for 14 days             | Yes - for 7 days            | No           |
| `Live streaming tail`            | Yes                     | Yes                           | Yes                         | Yes          |
| `Archiving`                      | Yes                     | Yes                           | Yes                         | No           |
| `Multi-channel Alerting`         | Yes                     | Yes                           | Yes                         | No           | 
{: caption="Table 2. List of features available for each service plan" caption-side="top"} 



## Regions
{: #ov_regions}

Logging with {{site.data.keyword.la_full_notm}} is available in the following regions:

| Region                | Location  |
|-----------------------|-----------|
| **US South**          | Dallas    |
| **EU-DE**             | Frankfurt | 
{: caption="Table 3. List of regions where the service is available" caption-side="top"} 

Currently, the **Frankfurt** location is **not** EU-managed. For more information, see [Enabling the EU Supported setting](/docs/account?topic=account-eu-hipaa-supported#bill_eusupported).
{: important}






## Security
{: #activity_tracker_ov_security}

Consider the following information about security when you work with the {{site.data.keyword.cloudaccesstrailshort}} service:

* IBM services that generate {{site.data.keyword.cloudaccesstrailshort}} events follow the {{site.data.keyword.IBM_notm}} Cloud security policy. For more information, see [Trust the security and privacy of IBM Cloud ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/cloud-computing/learn-more/why-ibm-cloud/security/){: new_window}.
* The {{site.data.keyword.cloudaccesstrailshort}} service captures user-initiated actions that change the state of Cloud services. The information does not provide direct access to databases or applications.
* Only authorized users can view and monitor {{site.data.keyword.cloudaccesstrailshort}} event logs. Each user is identified by their unique ID in the {{site.data.keyword.cloud_notm}}.



