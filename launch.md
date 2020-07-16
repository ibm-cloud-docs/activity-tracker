---

copyright:
  years: 2019, 2020
lastupdated: "2019-01-08"

keywords: IBM Cloud, LogDNA, Activity Tracker, web UI, browser

subcollection: Activity-Tracker-with-LogDNA

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

# Navigating to the LogDNA web UI
{: #launch}

After you provision an instance of the {{site.data.keyword.at_full_notm}} service in the {{site.data.keyword.cloud_notm}}, you can view, monitor, and manage events through the {{site.data.keyword.at_full_notm}} web UI. You can launch the LogDNA web UI from the {{site.data.keyword.cloud_notm}} UI or directly from a browser.
{:shortdesc}


## Granting IAM policies to a user to view data 
{: #launch_iam}

**Note:** You must be an administrator of the {{site.data.keyword.at_full_notm}} service, an administrator of an {{site.data.keyword.at_full_notm}} instance, or have account IAM permissions to grant other users policies.

The following table lists the minimum policy that a user must have to be able to launch the web UI, and view data through the {{site.data.keyword.at_full_notm}} web UI:

| Role                      | Permission granted       |
|---------------------------|---------------------|
| Platform role: `Viewer`   | Allows the user to view the list of service instances in the Observability dashboard. |
| Service role: `Reader`    | Allows the user to view events through the web UI. | 
{: caption="Table 1. IAM policies" caption-side="top"} 

For more information, see [Granting user permissions to a user or service ID](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-iam_view_events#iam_view_events).


## Launching the LogDNA web UI through the {{site.data.keyword.cloud_notm}} UI
{: #launch_cloud_ui}

You can launch the LogDNA web UI within the context of an {{site.data.keyword.at_full_notm}} instance, from the {{site.data.keyword.cloud_notm}} UI. 

Complete the following steps to launch the web UI:

1. [Log in to your {{site.data.keyword.cloud_notm}} account](https://cloud.ibm.com/login){: external}.

	After you log in with your user ID and password, the {{site.data.keyword.cloud_notm}} dashboard opens.

2. Click the **Menu** icon ![Menu icon](../icons/icon_hamburger.svg) &gt; **Observability**. 

3. Select **Activity Tracker**. 

    The list of {{site.data.keyword.at_full_notm}} instances is displayed.

    There is 1 instance per region.
    {: important}

4. Select the instance in the region where you want to view events. Then, click **View LogDNA**.

The {{site.data.keyword.at_full_notm}} web UI opens and shows the **Everything** view. Through this view, you can see the events in your account for the region that you have selected.


## Launching the LogDNA web UI from a browser
{: #launch_browser}


You can launch the LogDNA web UI directly from a browser. 


Looking more at the above, finally. Are you aware that LogDNA has an ibm-oauth (I think) way to login from an url?
https://app.us-south.logging.cloud.ibm.com/ext/ibm-sso/ed79138c92
will log me into my LogDNA account:
https://app.us-south.logging.cloud.ibm.com/ed79138c92/logs/view
Not asking me to SSO again with w3id, if I already have.
Furthermore, you can pass in query parameters to initialize the view that comes up. Like:
https://app.us-south.logging.cloud.ibm.com/ext/ibm-sso/4a7b5dca04?tags=mytag,myothertag
Which would filter by those two tags.  The parameters include:
q (search box)
t (timeframe)
levels=info,debug,warn,error,n%2Fa
apps=crn...
hosts
tags




## Getting the LogDNA web UI URL
{: #launch_get_url}

To get the LogDNA web UI URL, complete the following steps from a terminal:

1. [Pre-requisite] Installation of the {{site.data.keyword.cloud_notm}} CLI. [Learn more](/docs/cli?topic=cli-getting-started).

2. Log in to the location in the {{site.data.keyword.cloud_notm}} where the instance is provisioned. Run the following command: [ibmcloud login](/docs/cli?topic=cli-ibmcloud_cli#ibmcloud_login)

3. Set the resource group where the instance is available. Run the following command: [ibmcloud target](/docs/cli?topic=cli-ibmcloud_cli#ibmcloud_target)

    By default, the `default` resource group is set.

4. Get the dashboard URL. Run the following command:

    ```
    ic resource service-instance at-london --output JSON | grep dashboard_url
    ```
    {: codeblock}
    
