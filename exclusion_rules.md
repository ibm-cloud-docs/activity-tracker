---

copyright:
  years: 2019, 2021
lastupdated: "2021-08-09"

keywords:  IBM, activity tracker

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}

# Excluding data by using exclusion rules in the web UI
{: #exclusion_rules}

In an {{site.data.keyword.at_full_notm}} instance, you can configure exclusion rules through the UI to stop events from counting against your data usage quota and from being stored for search.
{: shortdesc}

This information applies only if you use an {{site.data.keyword.at_full}} [hosted event search offering](/docs/activity-tracker?topic=activity-tracker-service_plan).
{: important}

Complete the following steps to define an exclusion rule:

You must have manager access to define exclusion rules.
{: note}

1. [Launch the {{site.data.keyword.at_full_notm}} web UI](/docs/services/activity-tracker?topic=activity-tracker-launch).

2. Select the **Settings** icon ![Configuration icon](images/admin.png "Admin icon"). Then select **Usage** &gt; **Exclusion Rules**. 

3. Select **Add Rule**. The **Create Rule** section opens.

4. Enter a name for the rule in the section **What is this rule for?**.

5. Enter the exclusion criteria. You can select 1 or more hosts, 1 or more apps, enter a query, or a combination of hosts, apps and query.

    For example, to exclude all the lines from a specific host, select that host and leave the apps and query fields blank. A host represents a service or resource.

    You can enter a query to define the exclusion rule, or to refine the exclusion rule when you specify a host, an app, or both.

6. Select **Preserve these lines for live-tail and alerting** to show through the live tail the log lines that are excluded. Notice that you can still use these log lines to set up an alert.

7. Click **Save**.


