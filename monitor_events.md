---

copyright:
  years: 2019
lastupdated: "2019-05-25"

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


# Monitoring events
{: #monitor_events}

After you provision an instance of the {{site.data.keyword.at_full_notm}} service in the {{site.data.keyword.cloud_notm}}, you can monitor events through the {{site.data.keyword.at_full_notm}} web UI.
{:shortdesc}

You view and manage events in the web UI. The default view is the one that is named **Everything**. As soon as you open the web UI, this is the view that you see.

You can create custom views to analyze data. 
* To create a custom view, you must apply a search query that defines what events to display through the view. [Learn more](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-views).
* You can attach alerts to a custom view. [Learn more](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-alerts).
* You can export data from a custom view. [Learn more](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-export).
* You can rename, and add or modify the description of a view. [Learn more](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-views#views_step5).
* You can apply a line template to a view to customize how the data is displayed. [Learn more](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-views#views_step4).



## View a subset of the events
{: #view_events_step2}

You can select the events that are displayed through a view by applying a timestamp, a search query, or both.

* You can apply a search query, and save it as a custom view. [Learn more](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-views).
* You can apply a timestamp to jump to a specific time within your retention period. Different [service plans](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-service_plan) have different retention periods.

When you apply a search query, you can save that view for reuse later. However, timestamps are not saved.
{: note}

## Viewing events
{: #mon_view_events}



Complete the following steps to view events:

1. Check that your user ID has permissions to launch the web UI and view events. 

    The following table lists the minimum policies that a user must have to be able to launch the {{site.data.keyword.at_full_notm}} web UI, and view, search, and filter events:

    <table>
      <caption>Table 1. IAM policies</caption>
      <tr>
        <th>Role</th>
        <th>Permission granted</th>
      </tr>
      <tr>
        <td>Platform role: `Viewer`</td>
        <td>Allows the user to view the list of service instances in the *Observability* dashboard.</td>
      </tr>
      <tr>
        <td>Service role: `Reader`</td>
        <td>Allows the user to launch the web UI, and view, search, and filter events in the web UI.</td>
      </tr>
    </table>

    For more information on how to configure these policies for a user, see [Granting user permissions to a user or service ID](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-iam_view_events#iam_view_events).

2. [Go to the web UI](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-launch#launch).

3. Click the **Views** icon ![Configuration icon](images/views.png).

4. Select **Everything** or a view. You can view events through the view that you have selected.




## Jump to timeframe
{: #view_events_stepx}


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




