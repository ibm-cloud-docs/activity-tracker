---

copyright:
  years: 2019, 2022
lastupdated: "2022-05-25"

keywords: IBM Cloud, Activity Tracker, configuration, route, target, setting, backup, report

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}


# Creating a report of the {{site.data.keyword.atracker_short}} V2 configuration
{: #config_report_v2}

After configuring your {{site.data.keyword.atracker_full}} resources for your account, you should save a copy of your configuration for reference and backup purposes.
{: shortdesc}

This information applies only if you use {{site.data.keyword.atracker_full}}.
{: important}

## Prereqs
{: #config_report_v2_prereqs}

Before you use the CLI to save your {{site.data.keyword.atracker_full_notm}} resource data, you must do the following:

1. [Install the {{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cli-install-ibmcloud-cli).

2. [Install the {{site.data.keyword.atracker_full_notm}} CLI](/docs/activity-tracker?topic=activity-tracker-activity-tracking-cli#activity-tracking-cli-prereq).

3. Make sure your account is [running the V2 configuration.](/docs/activity-tracker?topic=activity-tracker-settings&interface=cli#settings-get-cli)  If you are running the V1 configuration [migrated to the {{site.data.keyword.atracker_full_notm}} V2 configuration](/docs/activity-tracker?topic=activity-tracker-migration).

4. Make sure you have configured your [settings](/docs/activity-tracker?topic=activity-tracker-settings), [routes](/docs/activity-tracker?topic=activity-tracker-route_v2), and [{{site.data.keyword.cos_full_notm}} targets](/docs/activity-tracker?topic=activity-tracker-target_v2_cos) or [{{site.data.keyword.atracker_full_notm}} hosted event search](/docs/activity-tracker?topic=activity-tracker-target_v2_at).


## Saving a copy of your account settings
{: #save_settings}

Run the following command to save a copy of your account settings to a file.

```text
ibmcloud atracker setting get --output JSON > ACCOUNT_settings.json
```
{: pre}

Where `ACCOUNT` is a unique indicator for your account.

## Saving a copy of your route configuration
{: #save_route}

Run the following command to save a copy of your route configuration to a file.

```text
ibmcloud atracker route ls --output JSON > ACCOUNT_routes.json
```
{: pre}

Where `ACCOUNT` is a unique indicator for your account.

## Saving a copy of your target configuration
{: #save_target}

Run the following command to save a copy of your target configuration to a file.

```text
ibmcloud atracker target ls --output JSON > ACCOUNT_targets.json
```
{: pre}

Where `ACCOUNT` is a unique indicator for your account.
