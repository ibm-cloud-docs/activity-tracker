---

copyright:
  years: 2019, 2024
lastupdated: "2024-05-24"

keywords:

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}

# Excluding ingestion data by using exclusion rules
{: #exclusion_rules}

In an {{site.data.keyword.at_full_notm}} instance, you can configure exclusion rules through the UI to stop events from counting against your data usage quota and from being stored for search.
{: shortdesc}


{{../log-analysis/_include-segments/deprecation_notice.md}}


## Prereqs
{: #exclusion_rules_prereqs}

You must have manager access to define exclusion rules.
{: note}


## Configuring an exclusion rule through the UI
{: #exclusion_rules_ui}

Complete the following steps to define an exclusion rule:

Verify that each exclusion rule that you add behaves as expected. Improper configured exclusion rules can result in storing data not intended for storage.
{: important}

1. [Launch the {{site.data.keyword.at_full_notm}} web UI](/docs/services/activity-tracker?topic=activity-tracker-launch).

2. Select the **Settings** icon ![Configuration icon](images/admin.png "Admin icon"). Then select **Usage** &gt; **Exclusion Rules**.

3. Select **Add Rule**. The **Create Rule** section opens.

4. Enter a name for the rule in the section **What is this rule for?**.

5. Enter the exclusion criteria. You can select 1 or more hosts, 1 or more apps, enter a query, or a combination of hosts, apps and query.

    For example, to exclude all the lines from a specific host, select that host and leave the apps and query fields blank. A host represents a service or resource.

    You can enter a query to define the exclusion rule, or to refine the exclusion rule when you specify a host, an app, or both.

6. Select **Preserve these lines for live-tail and alerting** to show through the live tail the log lines that are excluded. Notice that you can still use these log lines to set up an alert.

7. Click **Save**.

8. After you configure an exclusion rule, verify that the exclusion rule behaves as you expect.

    Check the query in a custom view by entering the search criteria in the search bar of the *Everything* view, and validating that the data that is displayed is the data that you want excluded.
    {: tip}
