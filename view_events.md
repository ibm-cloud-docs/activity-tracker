---

copyright:
  years: 2019, 2020
lastupdated: "2020-04-27"

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
{: #view_events}

After you provision an instance of the {{site.data.keyword.at_full_notm}} service in the {{site.data.keyword.cloud_notm}}, you can view events through the {{site.data.keyword.at_full_notm}} web UI. You view events in your local time.
{:shortdesc}


## View events
{: #view_events_step1}

Complete the following steps to view events:

1. Check that your user ID has permissions to launch the web UI and view events. 

    The following table lists the minimum roles that a user must have to be able to launch the {{site.data.keyword.at_full_notm}} web UI, and view, search, and filter events:

    <table>
      <caption>Table 1. IAM roles</caption>
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

    For more information on how to configure policies for a user, see [Granting user permissions to a user or service ID](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-iam_view_events#iam_view_events).

2. [Go to the web UI](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-launch#launch).

3. Click the **Views** icon ![Configuration icon](images/views.png).

4. Select **Everything** to see all the events, or a view. 

You can view events through the view that you have selected.



## View a subset of the events by applying a search query
{: #view_events_step2}

You can select the events that are displayed through a view by applying a search query. You can save that view for reuse later. [Learn more](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-views#views_step2).

 


## View a subset of the events by applying a timeframe
{: #view_events_step3}

You can select the events that are displayed through a view by applying a timeframe.

You can apply a timestamp by specifying an absolute time, a relative time, or a time range.

Complete the following steps to jump to a specific time:
1. [Go to the web UI](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-launch#launch).
2. Click the **Views** icon ![Configuration icon](images/views.png).
3. Select **Everything** or a view.
4. Enter a time query. Choose any of the following options:

    * Enter an abosute time to jump to a point in time in your events such as `May 20 7:00pm`.
    
    * Enter a relative time such as `2 days ago`, `today at 12am`, or `an hour ago`.

    * Enter a time range such as `yesterday 10am to yesterday 11am`, `last fri 4:30pm to 11/12 1 AM`, `last wed 4:30pm to 23/05 1 AM`, or `May 20 10am to May 22 10am`. Make sure to include `to` to separate the initial timestamp from the end timestamp.

5. Click **ENTER**.

    You might get the error message: `Your request is taking longer than expected, try refreshing your browser in a bit as we try to catch up. Retry.` You might get this error when the timeframe that you have specified does not have any events available to show. Change the time query, and retry.



## View an event in context
{: #view_events_step4}

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
{: #view_events_step5}


Complete the following steps to copy an event to the clipboard: 

1. In the web UI, click the **Views** icon ![Configuration icon](images/views.png "Configuration icon").
2. Select **Everything** or a custom view.
3. Identify a line that you want to explore.
4. Expand the event line. 

    Information about line identifiers, tags, and labels is displayed.

5. Click **Copy to clipboard** to copy the event to the clipboard.

When you finish exploring the event, click **Close** to close the line.




