---

copyright:
  years: 2019, 2021
lastupdated: "2021-01-05"

keywords: IBM Cloud, Activity Tracker, export

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
{:external: target="_blank" .external}

 
# Exporting events through the UI
{: #export}

You can export data in JSONL format from an {{site.data.keyword.at_full_notm}} instance graphically through the web UI. 
{:shortdesc}

Consider the following information when you export events:
* You can export a set of log entries. To define the set of data that you want to export, you can apply filter and searches. You can also specify the time range. 
* From the Web UI, when you export logs, you get an email that is sent to your email address, with a link to a compressed file that includes the data. To get the data, you must click the link and download the compressed file.
* The compressed log file that contains the data that you want to export is available for a maximum of 12 hours. 
* When you export logs, you have a limit of lines that you can export in a request. You can specify to export older lines or newer lines in case you reach the limit in the time range that you specify for the export. 


## Prerequisites
{: #export_prereqs}

* **You must have a paid service plan** for the {{site.data.keyword.at_full_notm}} service. [Learn more](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-service_plan#service_plan). 

* Check that your user ID has permissions to launch the web UI, view or manage service keys, and view events. [Learn more](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-iam_view_events#iam_view_events).

* Check that the logging instance has the export feature enabled. [Learn more](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-export_config).

## Exporting events from a custom view
{: #export_ui_view}

You can create a custom view and then export data for a period of time.

Complete the following steps to export data through the UI:

1. [Launch the UI](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-launch#launch).
2. Click the **Views** icon ![Views icon](images/views.png "Views icon").
3. Select a view.
4. Select the view name. 
5. Select **Export lines**. A new window opens.
6. Check the time range. If you need to change it, click the predefined time range in the *Change the Time Range for export* field.
7. Select **Prefer newer lines** or **Prefer older lines** in case the export request exceeds the line limit.
8. Check your email. You should receive an email with a link to download your exported lines.


## Exporting events from a search
{: #export_ui_search}

You can export data from a custom search.

Complete the following steps to export data through the UI:

1. [Launch the UI](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-launch#launch).
2. Click the **Views** icon ![Views icon](images/views.png "Views icon").
3. Select **Everything**.
4. Apply filters and search criteria until you see the entries that you want to export.
4. Click **Unsaved View**.
5. Select **Export lines**. A new window opens.
6. Check the time range. If you need to change it, click the predefined time range in the *Change the Time Range for export* field.
7. Select **Prefer newer lines** or **Prefer older lines** in case the export request exceeds the line limit.
8. Check your email. You receive an email with a link to download your exported lines.


