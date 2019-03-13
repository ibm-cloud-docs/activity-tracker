---

copyright:
  years: 2019
lastupdated: "2019-03-19"

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

 
# Exporting events to local file
{: #export}

You can export data in JSONL format from an {{site.data.keyword.at_full_notm}} instance into a local file. You can export logs programmatically or from the IBM Log Analysis Web UI. 
{:shortdesc}

Consider the following information when you export log data:
* You export a set of event entries. To define the set of data that you want to export, you can apply filter and searches. You can also specify the time range. 
* From the web UI, when you export events, you get an email that is sent to your email address, with a link to a compressed file that includes the data. To get the data, you must click the link and download the compressed file.
* When you export events programmatically, you can choose to send an email or to stream events in to your terminal.
* The compressed file that contains the data that you want to export is available for a maximum of 48 hours. 
* The maximum number of lines that you can export is 10,000.



## Exporting events from the web UI
{: #ui}

Complete the following steps to export data:

1. Click the **Views** icon ![Configuration icon](images/views.png).
2. Select **Everything** or a view.
3. Apply a time frame, filters and search criteria until you see the entries that you want to export.
4. Click **Unsaved View** if you are starting from the **Everything** view. Click your view name if you selected a view in the previous step.
5. Select **Export lines**. A new window opens.
6. Check the time range. If you need to change it, click the predefined time range in the *Change the Time Range for export* field.
7. Select **Prefer newer lines** or **Prefer older lines** in case the export request exceeds the line limit.
8. Check your email. You receive an email from **LogDNA** with a link to download your exported lines.


## Exporting logs programmatically by using the API
{: #api}

Complete the following steps to export events programmatically:

1. Generate a Service Key. 

    **Note:** You must have **manager** role for the {{site.data.keyword.at_full_notm}} instance or service to complete this step.

    1. Launch the {{site.data.keyword.at_full_notm}} web UI. For more information, see [Go to to the {{site.data.keyword.at_full_notm}} web UI]().

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

    * ENDPOINT represents the entry point to the service. Each region has a different URL.
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
curl "https://api.us-south.logging.cloud.ibm.com/v1/export?to=$(date +%s)000&from=$(($(date +%s)-86400))000&levels=info" -u e08c0c759663491880b0d61712346789:
```
{: screen}

To send an email with the link to download the events that are specified on the export, you can run the following command:

```
curl "https://api.us-south.logging.cloud.ibm.com/v1/export?to=$(date +%s)000&from=$(($(date +%s)-86400))000&levels=info&email=joe@ibm.com" -u e08c0c759663491880b0d61712346789:
```
{: screen}


To send an email with a custom subject, you can run the following command:

```
curl "https://api.us-south.logging.cloud.ibm.com/v1/export?to=$(date +%s)000&from=$(($(date +%s)-86400))000&levels=info&email=lopezdsr@uk.ibm.com&emailSubject=Export%20test" -u e08c0c759663491880b0d61712346789:
```
{: screen}

