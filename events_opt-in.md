---

copyright:
  years: 2019, 2020
lastupdated: "2020-11-12"

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

In {{site.data.keyword.at_full_notm}} (AT), events are collected automatically for most enabled-AT services. However, some services might require an upgrade of the service plan, a configuration setting, or both, for you to be able to collect and analyze them.
{:shortdesc}




## Management events
{: #events_opt-in_mgt}

The following table lists the services that require additional steps for you to be able to monitor [management events](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-event_types#event_types_management) that they generate:

| Service                            | Upgrade plan                       | Configure the service              | More info |
|------------------------------------|------------------------------------|------------------------------------|-----------|
| [Watson services](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-cloud_services#watson_ai) `[*]`  | ![Checkmark icon](../icons/checkmark-icon.svg) |  |   |
{: caption="Table 1. {{site.data.keyword.cloud_notm}} services that require opt-in actions for management events" caption-side="top"}

`[*]` You might need to upgrade to a paid plan to enable collection of Watson Activity Tracker events in your account. See [Details per Watson service](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-cloud_services#watson_ai) to check requirements by service.


## Data events
{: #events_opt-in_data}

The following table lists the services that require additional steps for you to be able to monitor [data events](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-event_types#event_types_data) that they generate:

| Service                            | Upgrade plan                       | Configure the service              | More info |
|------------------------------------|------------------------------------|------------------------------------|-----------|
| {{site.data.keyword.appid_full}}   | ![Checkmark icon](../icons/checkmark-icon.svg) | ![Checkmark icon](../icons/checkmark-icon.svg)   | [Monitoring runtime activity](/docs/appid?topic=appid-at-events#at-monitor-runtime-activity)   |
| {{site.data.keyword.cos_full}}     |  | ![Checkmark icon](../icons/checkmark-icon.svg) | [Enable activity tracking](/docs/cloud-object-storage?topic=cloud-object-storage-at#at-console-enable) |
| {{site.data.keyword.cloudantfull}} |  | ![Checkmark icon](../icons/checkmark-icon.svg) | [Configuring data events for an IBM Cloudant instance](/docs/Cloudant?topic=Cloudant-at_events#at_event_configure) | ![Checkmark icon](../icons/checkmark-icon.svg) | ![Checkmark icon](../icons/checkmark-icon.svg) | [How to enable message audit events](/docs/EventStreams?topic=EventStreams-at_events#enable-message-events) |
| {{site.data.keyword.messagehub_full}} | 
| [Watson services](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-cloud_services#watson_ai)    | ![Checkmark icon](../icons/checkmark-icon.svg) |  |   |
{: caption="Table 2. {{site.data.keyword.cloud_notm}} services that require opt-in actions for data events" caption-side="top"}


## Details per Watson service
{: #events_opt-in_watson}

The following table lists the Watson services and related information about additional steps that you might need to be able to monitor events:

| Service Name | Paid plan required | Other configuration required | 
| -- | -- | -- |
| {{site.data.keyword.cncfull}} | Yes | No |  
| {{site.data.keyword.conversationfull}} | Yes </br>Premium Plan only feature | No |  
| {{site.data.keyword.discoveryfull}} | Yes | No |  
| {{site.data.keyword.knowledgestudiofull}} | Yes | No |  
| {{site.data.keyword.languagetranslatorfull}} | Yes | No |  
| {{site.data.keyword.nlclassifierfull}} | Yes | No |  
| {{site.data.keyword.nlufull}} | Yes | No |  
| {{site.data.keyword.speechtotextfull}} | Yes | No |  
| {{site.data.keyword.texttospeechfull}} | Yes | No |  
| {{site.data.keyword.visualrecognitionfull}} | Yes | No |  
| {{site.data.keyword.iva_full}} | No | No |
{: caption="Table 3. Watson services that require opt-in actions for data events" caption-side="top"}


