---

copyright:
  years: 2019, 2024
lastupdated: "2024-03-27"

keywords:

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}

# Controlling who can export events
{: #export_config}

For each {{site.data.keyword.at_full_notm}} instance, you can configure whether users can export data.
{: shortdesc}

<!-- Common deprecation statement -->
{{../log-analysis/_include-segments/deprecation_notice.md}}

When the export configuration setting is enabled, you can export data in JSONL format from an {{site.data.keyword.at_full_notm}} instance.

You can have 1 Activity Tracker instance per region in your account. Therefore, to stop users from exporting auditing events in the account, you must disable the export feature in each Activity Tracker instance that you have provisioned in your account.
{: important}

## Allowing users to export events
{: #export_config_allow}

Complete the following steps to allow users to export events from an {{site.data.keyword.at_full_notm}} instance:

1. [Launch the {{site.data.keyword.at_full_notm}} web UI](/docs/activity-tracker?topic=activity-tracker-launch#launch_cloud_ui).

2. Select the **Configuration** icon ![Configuration icon](images/admin.png).

3. Select **Organization** &gt; **General**.

4. Set-on the **Export Log Lines** setting to allow users to export events.



## Disable the export feature
{: #export_config_disable}

Complete the following steps to disable the export feature in an {{site.data.keyword.at_full_notm}} instance:

1. [Launch the {{site.data.keyword.at_full_notm}} web UI](/docs/activity-tracker?topic=activity-tracker-launch#launch_cloud_ui).

2. Select the **Configuration** icon ![Configuration icon](images/admin.png).

3. Select **Organization** &gt; **General**.

4. Set-off the **Export Log Lines** setting to prevent users from exporting events.
