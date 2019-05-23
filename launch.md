---

copyright:
  years: 2019
lastupdated: "2019-04-04"

keywords: IBM Cloud, LogDNA, Activity Tracker, web UI, browser

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

# Navigating to the web UI
{: #launch}

After you provision an instance of the {{site.data.keyword.at_full_notm}} service in the {{site.data.keyword.cloud_notm}}, you can view, monitor, and manage events through the {{site.data.keyword.at_full_notm}} web UI.
{:shortdesc}


## Step 1. Granting IAM policies to a user to view data 
{: #step1}

**Note:** You must be an administrator of the {{site.data.keyword.at_full_notm}} service, an administrator of an {{site.data.keyword.at_full_notm}} instance, or have account IAM permissions to grant other users policies.

The following table lists the minimum policy that a user must have to be able to launch the web UI, and view data through the {{site.data.keyword.at_full_notm}} web UI:

| Role                      | Permission granted       |
|---------------------------|---------------------|
| Platform role: `Viewer`   | Allows the user to view the list of service instances in the Observability dashboard. |
| Service role: `Reader`    | Allows the user to view events through the web UI. | 
{: caption="Table 1. IAM policies" caption-side="top"} 

For more information, see [Granting user permissions to a user or service ID](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-iam_view_events#iam_view_events).


## Step 2. Launching the web UI through the {{site.data.keyword.cloud_notm}} UI
{: #launch_step2}

You launch the web UI within the context of an {{site.data.keyword.at_full_notm}} instance, from the {{site.data.keyword.cloud_notm}} UI. 

Complete the following steps to launch the web UI:

1. [Log in to your {{site.data.keyword.cloud_notm}} account ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/login){:new_window}.

	After you log in with your user ID and password, the {{site.data.keyword.cloud_notm}} dashboard opens.

2. Click the **Menu** icon ![Menu icon](../icons/icon_hamburger.svg) > **Observability**. 

3. Select **Activity Tracker**. 

    The list of {{site.data.keyword.at_full_notm}} instances is displayed.

    There is 1 instance per region.
    {: important}

4. Select the instance in the region where you want to view events. Then, click **View LogDNA**.

The {{site.data.keyword.at_full_notm}} web UI opens and shows the **Everything** view. Through this view, you can see the events in your account for the region that you have selected.



## Getting the web UI URL from the {{site.data.keyword.cloud_notm}}
{: #launch_get}

To get the web UI URL, complete the following steps from a terminal:

1. Set the resource group where the {{site.data.keyword.at_full_notm}} instance is provisioned.

    ```
    export logdna_rg_name=<Resource_Group_Name_Where_LogDNA_Instance_Is_Created>
    ```
    {: codeblock}

2. Set the {{site.data.keyword.at_full_notm}} instance name.

    ```
    export logdna_instance_name=<Your_LogDNA_Instance_Name>
    ```
    {: codeblock}

3. Set the endpoint.

    ```
    export rc_endpoint=resource-controller.cloud.ibm.com
    ```
    {: codeblock}

4. Set the IAM token.

    ```
    export iam_token=$(ibmcloud iam oauth-tokens | grep IAM | grep -oP  "eyJ.*")
    ```
    {: codeblock}

    **Note:** If you are working on a MacOS terminal, the command is as follows: `export iam_token=$(ibmcloud iam oauth-tokens | grep IAM | grep -o  "eyJ.*")`

5. Set the resource group ID.

    ```
    export resource_group_id=$(ibmcloud resource groups | grep "^$logdna_rg_name" | awk '{print $2}')
    ```
    {: codeblock}

6. Set the web UI URL in a variable.

    ```
    export dashboard_url=$(curl -H "Accept: application/json" -H "Authorization: Bearer $iam_token" "https://$rc_endpoint/v1/resource_instances?resource_group_id=$resource_group_id&type=service_instance" | jq ".resources[] | select(.name==\"$logdna_instance_name\") | .dashboard_url")
    ```
    {: codeblock}

7. Get the web UI URL.

    ```
    echo $dashboard_url
    ```
    {: codeblock}

    

