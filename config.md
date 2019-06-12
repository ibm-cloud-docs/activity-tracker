---

copyright:
  years: 2019
lastupdated: "2019-05-25"

keywords: IBM Cloud, LogDNA, Activity Tracker, config, ui

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


# Configuring how event lines are displayed in a view
{: #config}

Through the {{site.data.keyword.at_full_notm}} web UI, you can apply search queries to define the events that are displayed through a custom view. Then, you can attach an alert to that view to be notified when a condition occurs. You can attach one or more alerts to a view. You can define multiple notification channels for an alert. You can mute alerts. You can detach alerts from a view.
{:shortdesc}

## Configure the timestamp to show UTC 

## Configure the background color





## Step 4. Customize how event lines are displayed through a view
{: #views_step4}

There are different options to customize how you see data in a view:
* You can modify the properties of a view., You can rename a view, add or modify its description, and apply a specific line format.
* You can change the `log format` in the *USER PREFERENCES* section.
* You can apply a line template from the *Tools* section. Notice that this overrides any other line configuration. If you select **Persist these settings**, all views in the UI will show data per the line format that is specified in this section.
* You can apply color to terms or strings by setting **Highlight Terms** in the **Tools** section.



### Change the line format through the view properties page
{: #views_step4_1}

Complete the following steps to modify the format of an event line in a single view:

1. In your view, select **Edit View Properties**. The *Edit View Properties* page opens.

2. Enter a custom line format in the **Custom %LINE Template** section. The default is set to `{{line}}`.

    For more information about the line template guidelines, see [Guidelines](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-views#views_line).

3. Click **Save properties*.



### Change the line format through the user preferences section
{: #views_step4_2}

In the **USER PREFERENCES** section, you can modify the order of the data fields that are displayed per line.

Complete the following steps to modify the format of an event line:

1. In the web UI, click the **Configuration** icon ![Configuration icon](images/admin.png "Admin icon").
2. Select **USER PREFERENCES**. A new window opens.
3. Select **Log Format**.
4. Modify the *Line Format* section to match your requirements. Drag boxes.


### Change the line format through the line template in the tools section
{: #views_step4_3}

Complete the following steps to modify the format of an event line:

1. In the view, click the **Tools** icon ![Tools icon](images/tool.png "Tools icon").
2. In the **Line Template** field, enter your custom line format. For more information about the line template guidelines, see [Guidelines](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-views#views_line).
3. Optionally, click **Persist these settings** to apply the line format to all views.



### Highlight terms
{: #view_events_step4_4}

Complete the following steps to highlight terms in a view:

1. In the view, click the **Tools** icon ![Tools icon](images/tool.png "Tools icon").
2. In the **Line Template** field, enter a word or string in the **Highlight Terms** section.
3. Optionally, click **Persist these settings** to apply these setting to all views.





## Guidelines defining line templates
{: #views_line}

Consider the following guidelines that you must apply when you define a line template:
* Use mustache style `{{field.name}}` or bash style `${field.name}` variables to construct your template. 
* Use `{{line}}` or `$@` to reference the original line. 
* All other characters or strings are interpreted as text literal. 


For example, you can define a line template as `{{initiator.id}} -- {{action}} -- {{message}}` to see these fields for each event in a view.



