---

copyright:
  years: 2019, 2022
lastupdated: "2022-05-09"

keywords: IBM Cloud, Activity Tracker, about, auditing

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}
 

# About {{site.data.keyword.atracker_short}}
{: #about}

Use the {{site.data.keyword.atracker_short}} service to capture a record of your {{site.data.keyword.cloud_notm}} activities and monitor the activity of your {{site.data.keyword.cloud_notm}} account. You can use this service to investigate abnormal activity and critical actions, and comply with regulatory audit requirements. The events that are collected comply with the Cloud Auditing Data Federation (CADF) standard.
{: shortdesc}

Compliance with internal policies and industry regulations is a key requirement in any organization's strategy, regardless of where applications run: on-premises, in a hybrid cloud, or in a public cloud. The {{site.data.keyword.at_full_notm}} service provides the framework and functionality to monitor API calls to services on the {{site.data.keyword.cloud_notm}} and produces the evidence to comply with corporate policies and market industry-specific regulations.

When you work in a cloud environment, such as the {{site.data.keyword.cloud_notm}}, you must plan the cloud strategy for auditing and monitoring workloads and data in accordance with your internal policies and with industry and country-based compliance requirements. You can use the information that is registered through the {{site.data.keyword.at_full_notm}} service to identify security incidents, detect unauthorized access, and comply with regulatory and internal auditing requirements.

* {{site.data.keyword.at_full_notm}} supports high-level security governance for your IT resources in the cloud.
* {{site.data.keyword.at_full_notm}} provides a solution for administrators to capture, store, view, search, and monitor API activity in a single place. It also offers a notification feature to alert you by using any of the supported notification channels.
* {{site.data.keyword.at_full_notm}} provides capabilities to export events that you can then use to generate an audit trail report. These reports might be required so that your organization complies with internal regulations and external industry and country regulations.

The {{site.data.keyword.cloud_notm}} platform combines platform as a service (PaaS) with infrastructure as a service (IaaS) to provide an integrated experience. In addition, it offers a common and unified solution to monitor these services in any {{site.data.keyword.cloud_notm}} account. Services generate auditing events automatically in the {{site.data.keyword.cloud_notm}} platform. These events comply with the Cloud Auditing Data Federation (CADF) standard. You can monitor the activity of your {{site.data.keyword.cloud_notm}} account through these events. Furthermore, you can analyze the information provided in each event through continuous security audits; you can investigate abnormal activity and critical actions; and you can use them to comply with regulatory audit requirements in your organization and in the industry. {{site.data.keyword.cloud_notm}} administrators can configure an {{site.data.keyword.cloud_notm}} account to collect auditing events automatically for most enabled-services. However, some services might require an upgrade of the service plan, a configuration setting, or both, for you to be able to collect and analyze them due to the high volumes of data that they generate. [Learn more about enabling Activity Tracker events](/docs/activity-tracker?topic=activity-tracker-events-opt-in).

For information on the services sending events to {{site.data.keyword.atracker_short}}, see [{{site.data.keyword.cloud_notm}} services that generate {{site.data.keyword.atracker_short}} events](/docs/activity-tracker?topic=activity-tracker-cloud_services).

## CADF standard
{: #cadf_standard}

The CADF standard defines a full event model that includes the information that is needed to certify, manage, and audit security of applications and services in cloud environments. The CADF event model includes the following components:
-	Action: The action is the operation or activity that an initiator performs, attempts to perform, or is waiting to complete.
-	Initiator: The initiator is the resource that makes an API call and generates a CADF event. The event that is triggered depends on the action that is requested by the API call.
-	Observer: The observer is the resource that creates and stores a CADF record from information available in a CADF event
-	Outcome: The outcome is the status of the action against the target.
-	Target: The target is the resource against which the action is performed, attempted to perform, or is pending to complete.

## Selecting your {{site.data.keyword.at_full_notm}} offering
{: #select_offering}

Depending on your compliance and organizational requirements, you can choose {{site.data.keyword.atracker_full_notm}}  or an {{site.data.keyword.at_full_notm}} hosted event search offering.
- Application environments seeking to maintain Financial Services (FS) validation status on {{site.data.keyword.cloud_notm}} should use {{site.data.keyword.atracker_full_notm}} . 
- Application environments seeking compliance with PCI, SOC2, Privacy Shield and HIPAA should use an {{site.data.keyword.at_full_notm}} hosted event search offering.

[![Getting started with Event Routing](/images/getting_started_routing.svg)](/docs/activity-tracker?topic=activity-tracker-getting-started-routing) [![Getting started with hosted event and search offerings](/images/getting_started_event.svg)](/docs/activity-tracker?topic=activity-tracker-getting-started-search)

##  Financial Services Validated status
{: #about-fs}

If you're the account owner, you can enable your {{site.data.keyword.cloud}} account to be Financial Services Validated, which means your account stores and manages regulated financial services information. Services that are designated as {{site.data.keyword.cloud_notm}} for Financial Services Validated leverage the industry’s highest levels of encryption certification, provides preventive and compensatory controls for financial services regulatory workloads, multi-architecture support and proactive, and automated security. For more information on how to enable your account, see [Enabling your account to use Finantial Services Validated products](/docs/account?topic=account-enabling-fs-validated).

The {{site.data.keyword.cloud_notm}} for Financial Services Validated designation is available for services that are operating in the Dallas (us-south), Washington DC (us-east), Frankfurt (eu-de), and London (eu-gb) [multizone regions](#x9774820){: term}. 

Use {{site.data.keyword.atracker_short}} to manage auditing events in your account while maintaining Financial Services Validated status.
{: tip}




## PCI, SOC2, Privacy Shield and HIPAA compliance
{: #about-cp}

{{site.data.keyword.at_short}} offers ready to run event search offerings that you can use to expedite your time to greater insights. You can choose to retain your events for 7, 14, or 30 days. In addition, a 30 day HIPAA compliant offering is also available. For more information on these offerings, see [Service plans](/docs/activity-tracker?topic=activity-tracker-service_plan).

Use {{site.data.keyword.atracker_short}} hosted event search offerings to manage auditing events through the UI.
{: tip}

## Features
{: ##about-features}

* Simplify compliance sign-off tasks

    Boost audit tasks on your {{site.data.keyword.cloud_notm}} account by automatically collecting events that report on actions to resources in your account. Analyze and get notified on the events that report out of compliance actions. 

    {{site.data.keyword.atracker_short}} is Financial Services Validated.

    {{site.data.keyword.atracker_short}} hosted event search offerings is certified for PCI, SOC2, Privacy Shield and HIPAA compliance.

* Adhere to standards

   Events comply with the Cloud Auditing Data Federation (CADF) standard. 
   
   For {{site.data.keyword.atracker_short}} hosted event search offerings, you can use simple to use keyword-based search to search across your events instead of using custom query languages. Apply the same keyword search to instantly build time series graphs.

* Accelerate detection of security incidents

    For {{site.data.keyword.atracker_short}} hosted event search offerings, get alert notifications of important events and errors when things are out of compliance. Create custom views and get notified immediately. Configure multi-channel alert notifications based on pattern matching to a variety of direct integrations such as email, Slack, PagerDuty, {{site.data.keyword.cloud_notm}} Monitoring, or your own custom webhooks.

* Improve visibility on actions in your {{site.data.keyword.cloud_notm}} account

    Improve the visibility into user and resource activity in your account by easily identifying the initiator who requested an action, the object on which the action was requested, and the time when the action took place. 

    For {{site.data.keyword.atracker_short}} hosted event search offerings, search by using simple keywords to quickly and intuitively gain insight. Use time series graphs to analyze and compare data. Use of dashboards to visualize and monitor common patterns and event trends.

* Share filtered datasets with other analytic tools

    For {{site.data.keyword.atracker_short}} hosted event search offerings, use the export API to share filtered datasets with other analytic tools. Stream live tail events to a centralize location for additional analysis across other areas of your business by using other analytic tools. Filter out events so you only stream the ones that are of most interest to you. 

    For {{site.data.keyword.atracker_short}}, you can download event data that you can then analyze by using other analytic tools.





