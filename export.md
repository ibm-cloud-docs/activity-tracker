---

copyright:
  years: 2019
lastupdated: "2019-04-04"

keywords: IBM Cloud, LogDNA, Activity Tracker, export

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

 
# Exporting events
{: #export}

You can export data in JSONL format from an {{site.data.keyword.at_full_notm}} instance into a local file. You can export logs programmatically or from the IBM Log Analysis Web UI. 
{:shortdesc}

Consider the following information when you export log data:
* You export a set of event entries. To define the set of data that you want to export, you can apply filter and searches. You can also specify the time range. 
* From the web UI, when you export events, you get an email that is sent to your email address, with a link to a compressed file that includes the data. To get the data, you must click the link and download the compressed file.
* When you export events programmatically, you can choose to send an email or to stream events in to your terminal.
* The compressed file that contains the data that you want to export is available for a maximum of 48 hours. 
* The maximum number of lines that you can export is 10,000.



## Prerequisites
{: #export_prereqs}

Before you start, check that your user ID has permissions to launch the web UI and view events. Then, [go to the web UI](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-launch#launch).

**Note:** You must be an administrator of the {{site.data.keyword.at_full_notm}} service, an administrator of the {{site.data.keyword.at_full_notm}} instance, or have account IAM permissions to manage policies.

The following table lists the minimum policies that a user must have to be able to launch the {{site.data.keyword.at_full_notm}} web UI, and view, search, and filter events:

| Role                      | Permission granted            |
|---------------------------|-------------------------------|  
| Platform role: `Viewer`     | Allows the user to view the list of service instances in the Observability dashboard. |
| Service role: `Reader`      | Allows the user to launch the web UI and view events in the web UI.  |
{: caption="Table 1. IAM policies" caption-side="top"} 

For more information on how to configure these policies for a user, see [Granting user permissions to a user or service ID](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-iam_view_events#iam_view_events).

**You must have a paid service plan** for the {{site.data.keyword.at_full_notm}} service. [Learn more](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-service_plan#service_plan). 



## Step 1. Go to the web UI
{: #export_step1}

[Go to the web UI](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-launch#launch).


## Step 2. Create a view
{: #export_step2}

[Create a view](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-views.md#views.md).


## Step 3. Export data
{: #export_step3}

Choose one of the following options to export events:

### Option 1. Exporting events from the web UI
{: #export_ui}

Complete the following steps to export data:

1. Click the **Views** icon ![Configuration icon](images/views.png).
2. Select **Everything** or a view.
3. Apply a time frame, filters and search criteria until you see the entries that you want to export.
4. Click **Unsaved View** if you are starting from the **Everything** view. Click your view name if you selected a view in the previous step.
5. Select **Export lines**. A new window opens.
6. Check the time range. If you need to change it, click the predefined time range in the *Change the Time Range for export* field.
7. Select **Prefer newer lines** or **Prefer older lines** in case the export request exceeds the line limit.
8. Check your email. You receive an email from **LogDNA** with a link to download your exported lines.


### Option 2. Exporting events programmatically by using the API
{: #export_api}

Complete the following steps to export events programmatically:

1. Generate a Service Key. 

    **Note:** You must have **manager** role for the {{site.data.keyword.at_full_notm}} instance or service to complete this step.

    1. Launch the {{site.data.keyword.at_full_notm}} web UI. For more information, see [Go to to the {{site.data.keyword.at_full_notm}} web UI](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-launch#launch_step2).

    2. Select the **Configuration** icon ![Configuration icon](images/admin.png). Then, select **Organization**. 

    3. Select **API keys**.

        You can see the service keys that are created. 

    4. Click **Generate Service Key**.

        A new key is added to the list. Copy this key.

2. Export events. Run the following cURL command:

    ```
    curl "ENDPOINT/v1/export?QUERY_PARAMETERS" -u SERVICE_KEY:
    ```
    {: codeblock}

    Where 

    * ENDPOINT represents the entry point to the service. Each region has a different URL. [Learn more](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-endpoints#endpoints).
    * QUERY_PARAMETERS are parameters that define the filtering criteria that is applied to the export request.
    * SERVICE_KEY is the service key that you created in the previous step.

The following table lists the query parameters that you can set:

| Query parameter | Type       | Status     | Description |
|-----------|------------|------------|-------------|
| `from`      | `int32`      | Required   | Start time. Set as UNIX timestamp in seconds or milliseconds. |
| `to`        | `int32`      | Required   | End time. Set as UNIX timestamp in seconds or milliseconds.    |
| `size`      | `string`     | Optional   | Number of log lines to include in the export.  | 
| `hosts`     | `string`     | Optional   | Comma-separated list of hosts. |
| `apps`      | `string`     | Optional   | Comma-separated list of applications. |
| `levels`    | `string`     | Optional   | Comma-separated list of log levels. |
| `query`     | `string`     | Optional   | Search query. For more information, see [Search Logs](/docs/services/Log-Analysis-with-LogDNA?topic=LogDNA-view_logs#view_logs_step6). |
| `prefer`    | `string`     | Optional   | Defines the log lines that you want to export. Valid values are `head`, first log lines, and `tail`, last log lines. If not specified, defaults to tail.  |
| `email`     | `string`     | Optional   | Specifies the email with the downloadable link of your export. By default, the log lines are streamed.|
| `emailSubject` | `string`     | Optional   | Use to set the subject of the email. </br>Use `%20` to represent a space. For example, a sample value is `Export%20logs`. |
{: caption="Query parameters" caption-side="top"} 

For example, to stream events into the terminal, you can run the following command:

```
curl "https://api.us-south.logging.cloud.ibm.com/v1/export?to=$(date +%s)000&from=$(($(date +%s)-86400))000" -u e08c0c759663491880b0d61712346789:
```
{: codeblock}

To send an email with the link to download the events that are specified on the export, you can run the following command:

```
curl "https://api.us-south.logging.cloud.ibm.com/v1/export?to=$(date +%s)000&from=$(($(date +%s)-86400))000&email=joe@ibm.com" -u e08c0c759663491880b0d61712346789:
```
{: codeblock}


To send an email with a custom subject, you can run the following command:

```
curl "https://api.us-south.logging.cloud.ibm.com/v1/export?to=$(date +%s)000&from=$(($(date +%s)-86400))000&email=joe@ibm.com&emailSubject=Export%20test" -u e08c0c759663491880b0d61712346789:
```
{: codeblock}

