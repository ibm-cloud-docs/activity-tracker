---

copyright:
  years: 2019, 2022
lastupdated: "2022-02-11"

keywords: IBM Cloud, Activity Tracker, config, ui

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}


# Customizing the web UI
{: #config}

You can configure your web UI to work with UTC timestamps, change the log line format, change the background color and more.
{: shortdesc}

This information applies only if you use an {{site.data.keyword.at_full}} [hosted event search offering](/docs/activity-tracker?topic=activity-tracker-service_plan).
{: important}


## Configure UTC timestamps 
{: #config_utc}

By default, the web UI is configured to use local timestamps in views and searches.

To display timestamps in UTC and do timeframe searches relative to UTC instead of local time, complete the following steps:

1. In the web UI, click the **User preferences** icon &gt; **User preferences**.
2. Select **Viewer options**.
3. Click **Show time as UTC** to enable UTC timestamps.



## Configure the background color
{: #config_color}

Complete the following steps:

1. In the web UI, click the **User preferences** icon &gt; **User preferences**.
2. Select **Viewer style**.
3. Choose the default contrast. 

    Choose *Light mode* to have a light background. 
    
    Choose *Dark mode** to have a black background.

4. Select the desired theme, text size, and line height.

5. Click **Done** to save your changes.



## Configure the log line format
{: #config_line_format}

Complete the following steps to display a log line that includes the timestamp and message of an event:

1. In the web UI, click the **User preferences** icon &gt; **User preferences**.
2. Select **Log format**.

    By default, the log format is configured in the following way:
    
    ```text
    %time('MMM D HH:mm:ss') %source %app %level %line
    ```
    {: screen}

3. To remove items from the format, drag and drop the items.  For example, to remove source, app, and level drag them out.

    The log line changes to the following format:

    ```text
    %time('MMM D HH:mm:ss') %line
    ```
    {: screen}


