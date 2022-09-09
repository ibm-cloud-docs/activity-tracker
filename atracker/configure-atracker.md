---

copyright:
  years: 2019, 2022
lastupdated: "2022-05-16"

keywords: IBM Cloud, Activity Tracker, Event Routing
subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}


# Configuring {{site.data.keyword.atracker_short}} in your account
{: #configure-atracker}

To collect auditing events in your {{site.data.keyword.cloud}} account, you can configure {{site.data.keyword.atracker_short}} by using the {{site.data.keyword.atracker_short}} API, the {{site.data.keyword.atracker_short}} CLI and Terraform scripts.
{: shortdesc}

This information applies only if you use {{site.data.keyword.atracker_short}}.
{: important}


The {{site.data.keyword.atracker_full}} feature has been enhanced and a new API version 2 is available. To use the new V2 features and configurations, your existing {{site.data.keyword.atracker_short}} V1 account configuration must be migrated to an {{site.data.keyword.atracker_short}} V2 account configuration.
{: note}

If you configured {{site.data.keyword.atracker_full}} prior to 16 May 2022, you will need to migrate your configuration to the new version V2. The {{site.data.keyword.atracker_full}} API version 1 is deprecated. For more information, see [Migrating the {{site.data.keyword.atracker_short}} account configuration from V1 to V2](/docs/activity-tracker?topic=activity-tracker-migration&interface=cli).



## Prerequisites
{: #configure-atracker-prereqs}

- Plan your account configuration. For more information, see [Planning your account configuration settings](/docs/activity-tracker?topic=activity-tracker-atracker-resources-planning).
- Learn about the API V2 enhancements. For more information, see [the {{site.data.keyword.atracker_short}} API](https://{DomainName}/apidocs/atracker/atracker-v2){: external}.

## IAM permissions 
{: #configure-atracker-iam}

Users must have the following [IAM roles](/docs/account?topic=account-assign-access-resources) to manage the {{site.data.keyword.atracker_short}} account settings. 

| Role                      | Minimum scope  | Minimum required roles | Action         |
| ------------------------- | -------------- | ---------------------- | -------------- |
| `atracker.setting.get`    | Account        | `Administrator`  \n `Editor`  \n `Viewer`  \n `Operator` | Get setting information |
| `atracker.setting.update` | Account        | `Administrator`| Update settings |
{: caption="Table 1. Required IAM roles to manage the {{site.data.keyword.atracker_short}} account settings." caption-side="top"}

Users must have the following [IAM roles](/docs/account?topic=account-assign-access-resources) to migrate the account's {{site.data.keyword.atracker_short}} configuration. 

| Role                      | Minimum scope  | Minimum required roles | Action         |
| ------------------------- | -------------- | ---------------------- | -------------- |
| `atracker.migration.post` | Account        | `Administrator`        | Start the migration of {{site.data.keyword.atracker_short}} resources in the account. | 
| `atracker.migration.get`  | Account        | `Administrator`  \n `Editor`  \n `Viewer`  \n `Operator` | Get the status of {{site.data.keyword.atracker_short}} resources that are being migrated from V1 to V2. |
{: caption="Table 2. Required IAM roles to migrate the {{site.data.keyword.atracker_short}} account configuration." caption-side="top"}



## Step 1. Configure the CLI V2 in your local system
{: #configure-atracker-step1}
{: cli}

Install the latest {{site.data.keyword.atracker_short}} CLI V2 plugin in your local system. See [Installing the {{site.data.keyword.atracker_short}} CLI](/docs/activity-tracker?topic=activity-tracker-atracker-cli-config&interface=cli).

Next, log in to the {{site.data.keyword.cloud_notm}}. Run the following command: [ibmcloud login](/docs/cli?topic=cli-ibmcloud_cli#ibmcloud_login)



## Step 2. Configure the account global settings
{: #configure-atracker-step2}
{: cli}

When you configure {{site.data.keyword.atracker_short}} in your account, you can configure the account settings such as the metadata location, type of endpoints allowed to manage the configuration, locations where targets can be defined, and default targets for collecting auditing events in regions that yiu have not explicitly configured.

You can configure the {{site.data.keyword.atracker_short}} account settings in your account by using the {{site.data.keyword.atracker_short}} CLI V2 or {{site.data.keyword.atracker_short}} REST API V2. For more information, see [Configuring {{site.data.keyword.atracker_short}} account settings](/docs/activity-tracker?topic=activity-tracker-settings&interface=cli).

Set these settings to define where and how auditing events are collected, routed, and managed in your account.
{: note}

### Define the metadata location
{: #configure-atracker-step2-1}

The metadata location is the region where all your {{site.data.keyword.atracker_short}} resource definitions are stored.

When you set the metadata location, check any compliance or industry regulations that apply to data location.
{: tip}

Run the following command to set the metadata location:

```pre
ibmcloud atracker setting update --metadata-region-primary <REGION>
```
{: codeblock}

Where `<REGION>` you can set the region to any of the supported locations where {{site.data.keyword.atracker_short}} is available.


### Define the type of endpoints allowed
{: #configure-atracker-step2-2}

You can use public endpoints, private endpoints or both to manage the {{site.data.keyword.atracker_short}} account configuration.

Configure private endpoints only when you require to be Financial Services Validated.
{: tip}

Run the following command to set the account to only use private endpoints:

```pre
ibmcloud atracker setting update --private-api-endpoint-only TRUE
```
{: codeblock}

For more information, see [Enforcing private endpoints to configure {{site.data.keyword.atracker_short}} resources](/docs/activity-tracker?topic=activity-tracker-getting-started-mng-endpoints&interface=cli).



## Step 3. Configure the account targets
{: #configure-atracker-step3}
{: cli}

A target defines where auditing events are collected.

Note the following information about targets:

* You can define up to 16 targets in each account. Each account can have up to 2 default targets.

* A target can be either an {{site.data.keyword.cos_full_notm}} (COS) bucket or the {{site.data.keyword.atracker_full_notm}} hosted event search offering.

* Targets are created within a region but are visible across regions. That is, all targets can be accessed by any {{site.data.keyword.atracker_full}} API endpoint.

* You can define targets in the same account where events are generated or in a different account.

* When you define a Cloud Object Storage target, you can use an API key or a service to service authentication to upload events.

* You can manage targets in your account by using the {{site.data.keyword.atracker_short}} CLI, and programmatically by using the {{site.data.keyword.atracker_short}} REST API and Terraform scripts.

The following table outlines valid target types:

| Target                                      | Type                     |
|---------------------------------------------|--------------------------|
| {{site.data.keyword.cos_full_notm}} (COS) | `cloud_object_storage`   |
| {{site.data.keyword.atracker_full_notm}} hosted event search offering | `logdna`   |
{: caption="Table 1. List of targets" caption-side="top"}

For more information, see [Managing COS targets by using the V2 API](/docs/activity-tracker?topic=activity-tracker-target_v2_cos&interface=cli) and [Managing IBM Cloud Activity Tracker hosted event search targets by using the V2 API](/docs/activity-tracker?topic=activity-tracker-target_v2_at&interface=cli).

Check out these tutorials:
- [Configuring a Cloud Object Storage target in the account that generates the auditing events by using a service ID](/docs/activity-tracker?topic=activity-tracker-getting-started-target-1&interface=cli).
- [Configuring a Cloud Object Storage target in a different account from the one that generates the auditing events by using service to service authorization](/docs/activity-tracker?topic=activity-tracker-getting-started-target-2&interface=cli).
- [Configuring a logdna target in the account to manage global events](/docs/activity-tracker?topic=activity-tracker-getting-started-target-1).

## Step 4. Define the default target for the account 
{: #configure-atracker-step4}
{: cli}

You can define up to 2 default targets in the account. 
- Each target collects auditing events that are not explicitly managed in the account's routing rules.
- Each target must be defined in the account before you can configure it as default in the account.

Define 1 default target per account. Consider defining a second default target per account when you want to collect the data in a backup location or account.
{: tip}

Run the following command to define a default target:

```pre
ibmcloud atracker setting update --default-targets TARGETS
```
{: codeblock}



## Step 5. Configure the account routes
{: #configure-atracker-step5}
{: cli}

A route defines the rules that indicate what auditing events are collected in a region and where to store them.

* Routes are global under an account and are evaluated in all regions where {{site.data.keyword.atracker_short}} is deployed.

* Routes may be accessed from any regional {{site.data.keyword.atracker_full}} API endpoint.

* You can define up to 4 routes for an account.

* By default, the account has 0 routes configured.

* You can configure up to 4 rules for each route. A routing rule indicates the locations and associated targets where auditing events are routed.

* You can configure up to 8 locations for each rule.

* You can configure up to 3 targets (`target_ids`) for each rule.

* Routes are processed independently.  If you have multiple routes with rules that match the same event, that event will be sent to multiple targets.

* Rules are processed in order.  The first matching rule (for example,  `location`) an event matches will be used to process the event.  Once an event has been processed it will not be processed by a subsequent rule within that route's definition. If you want to specify a default rule for all events that were not processed by other rules you would specify the rule (`"locations" : ["*"]`) as the final rule in your `rules` definition for the `route`.

* If an event doesn't match any rule and no default target is configured, the event will be dropped and not routed to any target.

* Any update to a `rules` configuration must include all `location` rules.  An update will discard the existing rule set and replace it with the specified configuration.

* You can manage routes in your account by using the {{site.data.keyword.atracker_short}} CLI, and programmatically by using the {{site.data.keyword.atracker_short}} REST API and Terraform scripts.

After you configure a route, it might take up to 1 hour for the configuration to be enabled.
{: note}


For more information, see [Managing routes using the V2 API](/docs/activity-tracker?topic=activity-tracker-route_v2&interface=cli).

