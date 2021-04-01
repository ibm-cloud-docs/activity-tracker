---

copyright:
  years: 2019, 2021
lastupdated: "2021-01-05"

keywords: IBM Cloud, Activity Tracker, web UI, browser

subcollection: activity-tracker

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

# Navigating to the UI
{: #launch}

After you provision an instance of the {{site.data.keyword.at_full_notm}} service in the {{site.data.keyword.cloud_notm}}, you can view, monitor, and manage events through the {{site.data.keyword.at_full_notm}} web UI. You can launch the UI from the {{site.data.keyword.cloud_notm}} UI or directly from a browser.
{:shortdesc}



## Granting IAM policies to a user to launch the web UI
{: #launch_iam}

**Note:** You must be an administrator of the {{site.data.keyword.at_full_notm}} service, an administrator of an {{site.data.keyword.at_full_notm}} instance, or have account IAM permissions to grant other users policies.

The following table lists the minimum policy that a user must have to be able to launch the web UI, and view data through the {{site.data.keyword.at_full_notm}} web UI:

| Role                      | Permission granted       |
|---------------------------|---------------------|
| Platform role: `Viewer`   | Allows the user to view the list of service instances in the Observability dashboard. |
| Service role: `Reader`    | Allows the user to view events through the web UI. | 
{: caption="Table 1. IAM policies" caption-side="top"} 

For more information, see [Granting user permissions to a user or service ID](/docs/services/activity-tracker?topic=activity-tracker-iam_view_events#iam_view_events).


## Launching the UI through the {{site.data.keyword.cloud_notm}} UI
{: #launch_cloud_ui}

You can launch the UI within the context of an {{site.data.keyword.at_full_notm}} instance, from the {{site.data.keyword.cloud_notm}} UI. 

Complete the following steps to launch the web UI:

1. [Log in to your {{site.data.keyword.cloud_notm}} account](https://cloud.ibm.com/login){: external}.

	After you log in with your user ID and password, the {{site.data.keyword.cloud_notm}} dashboard opens.

2. Click the **Menu** icon ![Menu icon](../icons/icon_hamburger.svg) &gt; **Observability**. 

3. Select **Activity Tracker**. 

    The list of {{site.data.keyword.at_full_notm}} instances is displayed.

    There is 1 instance per region.
    {: important}

4. Select the instance in the region where you want to view events. Then, click **View {{site.data.keyword.at_full_notm}}**.

The {{site.data.keyword.at_full_notm}} web UI opens and shows the **Everything** view. Through this view, you can see the events in your account for the region that you have selected.


## Launching the UI from a browser
{: #launch_browser}

You can launch the UI directly from a browser. 

Complete the following steps:

1. [Get the UI URL](/docs/activity-tracker?topic=activity-tracker-get_web_url).

    For example, a UI looks like `https://app.eu-gb.logging.cloud.ibm.com/ext/ibm-sso/xxxxxxxxxx`.

    You can also copy the UI URL that you get when you launch the UI through the {{site.data.keyword.cloud_notm}} UI. For example, a UI looks like `https://app.eu-gb.logging.cloud.ibm.com/xxxxxxxxxx/logs/view`.

2. Enter the dashboard URL in a browser and log in to {{site.data.keyword.cloud_notm}}.

    Notice that when you enter the following URL `https://app.eu-de.logging.cloud.ibm.com/xxxxxxxx`, you get a `404 page not found` error.

    Valid formats are `https://<ENDPOINT>/ext/ibm-sso/xxxxxxxxxx` or `https://<ENDPOINT>/xxxxxxxxxx/logs/view`

3. [Optional] You can also pass query parameters to refine the view that is displayed.

    ```
    https://<ENDPOINT>/ext/ibm-sso/WEB_UI_ID?q=<QUERY>&hosts=<HOSTS>&apps=<APPS>&levels=<LEVELS>&t=<TIMEFRAME>
    ```
    {: codeblock}

    Where

    * `<ENDPOINT>` represents the dashboard URL in the region where the instance is available. See [UI endpoints](/docs/activity-tracker?topic=activity-tracker-endpoints#endpoints_logdna_ui).

    * `<QUERY>` represents the search query that is applied for the view, for example, `q=table%3Amangle%20reason%3A%27refresh%20timer%27`. 

        Use `%3A` to represent a colon (`:`).

        Use `%20` to represent a space.

        Use `%27` to represent a quote (`'`).

    * `<HOSTS>` represents the list of services for which data is included in the view. Notice that these are values that you select in the *Sources* section of the UI. Multiple hosts are separated by commas, for example,  `hosts=logging-agent-trkq9,logging-agent-trkq7`.

    * `<APPS>` represents the list of apps for which data is included in the view. Multiple apps are separated by commas.

    * `<LEVELS>` represents the list of levels for which data is included in the view. Multiple levels are separated by commas, for example, `levels=normal,critical`.

    * `<TIMEFRAME>` represents the timeframe that you apply to the data that is displayed through the view. For example, look at the following samples:
    
        When you specify a timeframe of `July 12`, the value is `t=July%2012`. 
        
        When you specify a timeframe of `July 12, 2020`, the value is `t=July%2012%2C%202020`. 

        When you specify a timeframe of `July 12, 2020 to July 15,2020`, the value is `t=July%2012%2C%202020%20to%20July%2015%2C2020`.


