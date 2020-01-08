---

copyright:
  years: 2019, 2020
lastupdated: "2019-01-08"

keywords: IBM Cloud, LogDNA, Activity Tracker, support

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
{:important: .important}
{:note: .note}

# Support Cases
{: #support_cases}

This page tells how your service can get support from LogDNA for a problem with *Log Analysis with LogDNA* or *Activity Tracker with LogDNA*. Support is provided via IBM Cloud Support. To get started, open a case by following the steps below. 

Support is supplemented by the Slack channel *ibm-guest-logdna-help*. However, incidents should be reported by opening cases.

## To open a case on LogDNA
{: #open_case}

1. Log into your team's IBM Cloud account.
	- Services generally have one IBM Cloud account that all team members use for opening cases.
	- This account will be the one that has Advanced or Premium support, if your service pays for it.
	- This account must be an internal paid account to get even Basic support.
1. On the IBM Cloud console, click "Support" at the top.
1. Click "Create a case" on the right.
1. Select "Technical".
1. Category: select "Developer Tools and Runtimes."
1. Offering: usually have to leave it blank. You are usually using a different account for support than where the LogDNA instance is.
1. Severity: Select the appropriate Severity.
    - See [below](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-support_cases#severity) for guidance on selecting the appropriate severity.
    - If you do not see a place to set the Severity, then you do not have Advanced or Premium support. Your cases will have severity 4 only. See [this section](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-support_cases#adv-prem) below.
    - If your team does have Adv/Prem support and you still can't set the severity, then consider whether you are logged into the right account for it. See [this section](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-support_cases#adv-prem) below.
1. Subject: Mention "LogDNA" in the subject. This is important, so the support team will quickly see they need to route the case to LogDNA.
1. Fill out the rest of the form. Include this information:
    - Account Information, Environment, Region (URL included)<br>- You can get all three (account, environment, and region) by copying the URL from the LogDNA UI.<br>- Response to tickets is often delayed because this vital information is missing.
    - Problem statement (Expected behavior)
    - Result of the problem (Actual behavior)
    - Any configuration information inclusive of that problem (Patterns, how to replicate issue)
    - Known changes that occurred on the client-side since the problem started
    - Any other information (please include screenshots, video)
1. Submit.

### To follow up in Slack

After you have opened a case, you may wish to refer to it in the Slack channel *ibm-guest-logdna-help*.
To do this, you need the Third Party Ticket number (TPT), since LogDNA support has no visibility into ServiceNow.
To get the TPT, someone with appropriate ServiceNow access should:

1. Log into ServiceNow.
2. Open the case.
3. Scroll down to the "Related Links" section.
4. Select the "Third Party Case tickets" tab.
5. You sould see a row in the table, starting with something like "TPT0000123". 

That is the TPT number that LogDNA support will recognize. If you don't see it, then you may not have appropriate access or the ticket may not have been opened in LogDNA's system yet.

## Advanced/Premium Support
{: #adv-prem}

Your service must have *Advanced Support* or *Premium Support* to open cases with severity of 1, 2, or 3, or to escalate cases. If you only have *Basic Support* (the free level), then you can only open cases with severity 4. See [here](https://cloud.ibm.com/docs/get-support?topic=get-support-support-plans) for an explanation of support levels. 

#### To see if you have Advanced Support:

1. Log into your team's IBM Cloud account.
	- Services generally have one IBM Cloud account that all team members use for opening cases.
	- This account will be the one that has Advanced or Premium support, if your service pays for it.
	- This account must be an internal paid account to get even Basic support.
2. Click "Support" at the top.
3. On the right, the "Plan" section will show your support plan. If it is "basic" support, you need to upgrade to at least "advanced."


If you do not have Advanced (or Premium) support, see [here](https://ibm.ent.box.com/v/cldsup-internal) for instructions on how to order it.

## LogDNA Severities
{: #severity}

Set the severity based on the following. Do not assign a higher severity than appropriate, as it will only lead to delays.

Notice that LogDNA considers some problems more severe when multiple customers are experiencing them. Unless you know otherwise, you can assign the severity on the assumption that other users are having the same problem you are.

| Sev | Definition | Examples |
| --- | --- | --- |
| 1 | Urgent - Critical business impact/Service Down | <ul><li>Ingestion has stopped from ALL Sources on multiple customers<li>No logs are showing up in the console<li>Web App unreachable for multiple customers for significant period of time<li>Customers unable to login to web console to see logs <li>Archive data missing for more than 72 hours</ul> |
| 2 | High - Significant business impact | <ul><li>Indexing delay for more than 20 mins. Indexing refers to the time between a line is ingested and when itʼs available for search. By default, our indexing process updates every 15s after live tail latency. <li>Alert did not triggering for multiple customers <li>Ingestion (live-tail) latency for more than 15 mins <li>Logs are showing up in live-tail but with delay which affects Alerts. By default, live-tail latency is 30 sec or less.</ul>
| 3 | Normal - Minor business impact | <ul><li>Unable to export logs <li>Exclusion Rule issues Log lines that matches the exclusion rule still showing up in the console for search <li>Parsing issue Logs are not displayed properly in the console <li>Alert did not trigger due to customer configuration issue</ul> |
| 4 | Low - Minimal business impact: An inquiry or non-technical request | <ul><li>New Feature Request from the customer <li>Documentation updates <li>Update outdated documentation <li>Change billing information <li>How-to questions <li>Add new members <li>Create alerts, custom views, etc.</ul> |

