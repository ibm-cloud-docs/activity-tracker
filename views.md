---

copyright:
  years: 2019
lastupdated: "2019-04-04"

keywords: IBM Cloud, LogDNA, Activity Tracker, search, filter, events

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


# Creating custom views
{: #views.md}

Through the {{site.data.keyword.at_full_notm}} web UI, you can apply search and filtering criteria to define the events that are displayed through a custom view.
{:shortdesc}


## Prerequisites
{: #views_prereqs}

Before you start, check that your user ID has permissions to launch the web UI and view events. Then, [go to the web UI](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-launch#launch).

**Note:** You must be an administrator of the {{site.data.keyword.at_full_notm}} service, an administrator of the {{site.data.keyword.at_full_notm}} instance, or have account IAM permissions to manage policies.

The following table lists the minimum policies that a user must have to be able to launch the {{site.data.keyword.at_full_notm}} web UI, and view, search, and filter events:

| Role                      | Permission granted            |
|---------------------------|-------------------------------|  
| Platform role: `Viewer`     | Allows the user to view the list of service instances in the Observability dashboard. |
| Service role: `Reader`      | Allows the user to launch the web UI and view events in the web UI.  |
{: caption="Table 1. IAM policies" caption-side="top"} 

For more information on how to configure these policies for a user, see [Granting user permissions to a user or service ID](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-iam_view_events#iam_view_events).



## Step 1. Filter events
{: #views_step1}

You can filter events by source, application, and log level. 

* A source can be a host, a computer, a virtual machine, or a Heroku app.
* An application represents a log file, a program, or a container.
* Examples of log levels are: INFO, DEBUG, ERROR

Complete the following steps to filter logs:

1. In the web UI, click the **Views** icon ![Configuration icon](images/views.png "Configuration icon").
2. Select **Everything** or a view.
3. Expand **All Tags** to see the list of tags that are available. Then, choose the ones that you want.
4. Expand **All Sources** to see the list of sources that are available. Then, choose the ones that you want.
5. Expand **All Apps** to see the list of apps that are available. Then, choose the ones that you want.
6. Expand **All Levels** to see the list of levels that are available. Then, choose the ones that you want.

As you apply filters, notice that the name of the view changes to **Unsaved View**.

**Note:** In each section, you can group multiple options into a group. Group tags, sources, apps, and levels to reuse these groupings when you filter data in other custom views.

To create a group, select multiple values. Then, click **Save as group**. Enter a name for the group, and save it.


## Step 2. Search events
{: #views_step2}

When you search events, the search applies any filters and time queries that are configured in that view.

You can do simple searches (single term string search), compound search (multiple search terms and operators), field searches if the log line can be parsed, and others. For more information, see [How to Search Logs in LogDNA docs ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://docs.logdna.com/docs/search){:new_window}.

**Note:** AND and OR operators are case-sensitive and must be capitalized.

As you apply search criteria, notice that the name of the view changes to **Unsaved View**.



## Step 3. Create a custom view
{: #views_step3}

After you apply a time frame, filters and search criteria to the **Everything** view or to an existing custom view, complete the following steps to save the outcome as a custom view:

1. In the web UI, click **Unsaved View**.
2. Select **Save as new view / alert**. The *Create new view* page opens.
3. Enter a name for the view in the *Name* field.
4. Optionally, add a category. Enter a name and then click **Add this as new view category**.
5. Optionally, attach an alert. A new section is displayed for you to configure the alert.
6. Click **Save View**




