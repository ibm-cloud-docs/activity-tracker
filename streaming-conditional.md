---

copyright:
  years: 2019, 2022
lastupdated: "2022-02-04"

keywords: 

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}

# Configuring conditional streaming
{: #streaming-conditional}

In an {{site.data.keyword.at_full}} instance, you can configure streaming exclusion rules through the UI to filter what data is streamed.
{: shortdesc}

You must have manager access for {{site.data.keyword.at_short}} to define exclusion rules.  See [Configure streaming](/docs/activity-tracker?topic=activity-tracker-streaming#streaming-1) for more information on roles required for streaming.
{: note}

Complete the following steps to define an exclusion rule:

Verify that each exclusion rule that you add behaves as expected. Improper configured exclusion rules can result in storing data not intended for storage.
{: important}

1. [Launch the {{site.data.keyword.at_full_notm}} web UI](/docs/services/activity-tracker?topic=activity-tracker-launch).

2. Select the **Settings** icon ![Configuration icon](images/admin.png "Admin icon"). Then select **Streaming** &gt; **Exclusion Rules**. 

3. Select **Add Rule**. The **Create Rule** section opens.

4. Enter a name for the rule in the section **What is this rule for?**.

5. Enter the exclusion criteria by adding a query. For more information on how to build a query, see [Select the set of events to display through a view by applying a search query](/docs/activity-tracker?topic=activity-tracker-views#views_step2).

6. Click **Save**.

7. After you configure an exclusion rule, verify that the exclusion rule behaves as you expect.

    Check the query in a custom view by entering the search criteria in the search bar of the *Everything* view, and validating that the data that is displayed is the data that you want excluded.
    {: tip} 





