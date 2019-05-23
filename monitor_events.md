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
{: #monitor_events.md}

After you provision an instance of the {{site.data.keyword.at_full_notm}} service in the {{site.data.keyword.cloud_notm}}, you can monitor events through the {{site.data.keyword.at_full_notm}} web UI.
{:shortdesc}

* You view and manage events in the web UI.
* The default view is the **Everything** view. As soon as you open the web UI, this is the view that you see.
* You can create custom views.

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


## Customizing a view
{: #mon_customize}

To complete these steps, you need a custom view. If you do not have one, create one. [Learn more](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-views.md).
{: note}

There are different options to customize how you see data in a view.
* You can modify the properties of a view., You can rename a view, add or modify its description, and apply a specific line format.
* You can change the `log format` in the *USER PREFERENCES* section.
* You can apply a line template from the *Tools* section. Notice that this overrides any other line configuration. If you select **Persist these settings**, all views in the UI will show data per the line format that is specified in this section.
* You can apply color to terms or strings by setting ***Highlight Terms** in the **Tools** section.

Consider the following guidance on how to define line templates:
* Use mustache style `{{field.name}}` or bash style `${field.name}` variables to construct your template. 
* Use `{{line}}` or `$@` to reference the original line. 
* All other characters or strings are interpreted as text literal. 

### Edit view properties
{: #mon_cust_1}

Complete the following steps to modify the format of an event line in a single view:

1. In your view, select **Edit View Properties**. The *Edit View Properties* page opens.

    You can rename the view, add or modify the description of the view, and apply a custom line format.

2. Enter a new name in the **Rename View** section to rename the view.

3. Enter or modify the description in the **Description** section.

4. Enter a custom line format in the **Custom %LINE Template** section.

    The default is set to `{{line}}`.

5. Click **Save properties*.


### Customize the user preferences section
{: #mon_cust_2}

In the **USER PREFERENCES** section, you can modify the order of the data fields that are displayed per line.

Complete the following steps to modify the format of an event line:

1. In the web UI, click the **Configuration** icon ![Configuration icon](images/admin.png "Admin icon").
2. Select **USER PREFERENCES**. A new window opens.
3. Select **Log Format**.
4. Modify the *Line Format* section to match your requirements. Drag boxes.

### Customize the line template in the tools section
{: #mon_cust_3}

Complete the following steps to modify the format of an event line:

1. In the view, click the **Tools** icon ![Tools icon](images/tool.png "Tools icon").
2. In the **Line Template*** field, enter your custom line format.
3. Optionally, click **Persist these settings** to apply the line format to all views.


### Highlight terms
{: #view_events_step2_4}

Complete the following steps to highlight terms in a view:

1. In the view, click the **Tools** icon ![Tools icon](images/tool.png "Tools icon").
2. In the **Line Template*** field, enter a word or string in the ***Highlight Terms** section.
3. Optionally, click **Persist these settings** to apply these setting to all views.



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




