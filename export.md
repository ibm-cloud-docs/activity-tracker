---

copyright:
  years: 2019, 2020
lastupdated: "2020-06-24"

keywords: IBM Cloud, LogDNA, Activity Tracker, export

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

 
# Exporting events through the LogDNA web UI
{: #export}

You can export data in JSONL format from an {{site.data.keyword.at_full_notm}} instance graphically through the web UI. 
{:shortdesc}


## Prerequisites
{: #export_prereqs}

* [Learn more about exporting events](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-monitor_events#mon_export).

* **You must have a paid service plan** for the {{site.data.keyword.at_full_notm}} service. [Learn more](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-service_plan#service_plan). 

* Check that your user ID has permissions to launch the web UI, view or manage service keys, and view events. [Learn more](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-iam_view_events#iam_view_events).

* Check that the LogDNA instance has the export feature enabled.

## Exporting events from a custom view
{: #export_ui_view}

You can create a custom view and then export data for a period of time.

Complete the following steps to export data through the LogDNA web UI:

1. [Launch the LogDNA web UI](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-launch#launch).
2. Click the **Views** icon ![Configuration icon](images/views.png).
3. Select a view.
4. Select the view name. 
5. Select **Export lines**. A new window opens.
6. Check the time range. If you need to change it, click the predefined time range in the *Change the Time Range for export* field.
7. Select **Prefer newer lines** or **Prefer older lines** in case the export request exceeds the line limit.
8. Check your email. You should receive an email from **LogDNA** with a link to download your exported lines.


## Exporting events from a search
{: #export_ui_search}

You can export data from a custom search.

Complete the following steps to export data through the LogDNA web UI:

1. [Launch the LogDNA web UI](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-launch#launch).
2. Click the **Views** icon ![Configuration icon](images/views.png).
3. Select **Everything**.
4. Apply filters and search criteria until you see the entries that you want to export.
4. Click **Unsaved View**.
5. Select **Export lines**. A new window opens.
6. Check the time range. If you need to change it, click the predefined time range in the *Change the Time Range for export* field.
7. Select **Prefer newer lines** or **Prefer older lines** in case the export request exceeds the line limit.
8. Check your email. You receive an email from **LogDNA** with a link to download your exported lines.


