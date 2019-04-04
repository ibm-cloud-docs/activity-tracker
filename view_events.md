---

copyright:
  years: 2019
lastupdated: "2019-04-04"

keywords: IBM Cloud, LogDNA, Activity Tracker, view events

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


# Viewing events
{: #view_events.md}

After you provision an instance of the {{site.data.keyword.at_full_notm}} service in the {{site.data.keyword.cloud_notm}}, you can view events through the {{site.data.keyword.at_full_notm}} web UI.
{:shortdesc}


## Prerequisites
{: #view_events_prereqs}

Before you start, check that your user ID has permissions to launch the web UI and view events. 

**Note:** You must be an administrator of the {{site.data.keyword.at_full_notm}} service, an administrator of the {{site.data.keyword.at_full_notm}} instance, or have account IAM permissions to manage policies.

The following table lists the minimum policies that a user must have to be able to launch the {{site.data.keyword.at_full_notm}} web UI, and view events:

| Role                      | Permission granted            |
|---------------------------|-------------------------------|  
| Platform role: `Viewer`     | Allows the user to view the list of service instances in the Observability dashboard. |
| Service role: `Reader`      | Allows the user to launch the web UI and view events in the web UI.  |
{: caption="Table 1. IAM policies" caption-side="top"} 

For more information on how to configure these policies for a user, see [Granting user permissions to a user or service ID](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-iam_view_events#iam_view_events).


## View events through the web UI
{: #view_events_step1}

To launch the {{site.data.keyword.at_full_notm}} web UI, complete the following steps:

1. [Log in to your {{site.data.keyword.cloud_notm}} account ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/login){:new_window}.

	After you log in with your user ID and password, the {{site.data.keyword.cloud_notm}} *Dashboard* opens.

2. Go to the menu icon ![menu icon](../../icons/icon_hamburger.svg), and select **Observability**. 

3. Select **Activity Tracker**. 

    The list of {{site.data.keyword.at_full_notm}} instances is displayed.

    **Note:** There is 1 instance per region.

4. Select the instance in the region where you want to view events. Then, click **View LogDNA**.

The {{site.data.keyword.at_full_notm}} web UI opens and shows the **Everything** view. Through this view, you can see the events in your account for the region that you have selected.

**Note:** If you have a `Lite` plan, and you cannot see the events that you are looking for, you might need to upgrade to a paid plan to enable search capabilities on older events. The number of days that events are available for search depends on the plan that you choose. [Learn more](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-service_plan#service_plan).


## Customize your default view
{: #view_events_step2}

In the **USER PREFERENCES** section, you can modify the order of the data fields that are displayed per line.

Complete the following steps to modify the format of an event line:

1. In the web UI, click the **Configuration** icon ![Configuration icon](images/admin.png "Admin icon").
2. Select **USER PREFERENCES**. A new window opens.
3. Select **Log Format**.
4. Modify the *Line Format* section to match your requirements. Drag boxes.




## View an event in context
{: #view_events_step3}

At any time, you can view each event line in context.

Complete the following steps: 

1. In the web UI, click the **Views** icon ![Configuration icon](images/views.png "Configuration icon").
2. Select **Everything** or a custom view.
3. Identify a line that you want to explore.
4. Expand the event line. 

    Information about line identifiers, tags, and labels is displayed.

5. Click **View in Context** to see the event line in context of other entries from that host, app, or both.

When you finish exploring the event, click **Close** to close the line.




## Copy an event to the clipboard
{: #view_events_step4}


Complete the following steps to copy an event to the clipboard: 

1. In the web UI, click the **Views** icon ![Configuration icon](images/views.png "Configuration icon").
2. Select **Everything** or a custom view.
3. Identify a line that you want to explore.
4. Expand the event line. 

    Information about line identifiers, tags, and labels is displayed.

5. Click **Copy to clipboard** to copy the event to the clipboard.

When you finish exploring the event, click **Close** to close the line.




