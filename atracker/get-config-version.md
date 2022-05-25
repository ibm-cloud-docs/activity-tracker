---

copyright:
  years: 2019, 2022
lastupdated: "2022-05-16"

keywords: IBM Cloud, Activity Tracker, Event Routing
subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}


# Determining your {{site.data.keyword.atracker_full_notm}} Event Routing configuration version
{: #get-config-version}

To collect auditing events in your {{site.data.keyword.cloud_notm}} account, you can configure {{site.data.keyword.atracker_short}} Event Routing by using the {{site.data.keyword.atracker_short}} Event Routing API or the {{site.data.keyword.atracker_short}} Event Routing CLI. You can have a V1 configuration or a V2 configuration.
{: shortdesc}

This information applies only if you use {{site.data.keyword.atracker_short}} Event Routing.
{: important}



## IAM permissions 
{: #get-config-version-iam}

Users must have the following [IAM roles](/docs/account?topic=account-assign-access-resources) to manage the {{site.data.keyword.atracker_short}} Event Routing account settings. 

| Role                      | Minimum scope  | Minimum required roles | Action         |
| ------------------------- | -------------- | ---------------------- | -------------- |
| `atracker.setting.get`    | Account        | `Administrator`  \n `Editor`  \n `Viewer`  \n `Operator` | Get setting information |
| `atracker.setting.update` | Account        | `Administrator`| Update settings |
{: caption="Table 1. Required IAM roles to manage the {{site.data.keyword.atracker_short}} Event Routing account settings." caption-side="top"}



## Determining your CLI version
{: #get-config-version-cli-version}

To use the V2 configuration you must have the V2 API and CLI installed.

If you are unsure if your CLI environment is running the V2 configuration, run the following command:

```text
ibmcloud atracker setting get
```
{: pre}

If the command indicates that `setting` is not a valid command, then you do not have the V2 CLI installed. 

Install the V2 CLI by running the following command:

```text
ibmcloud plugin install atracker
```
{: pre}

Update the V2 CLI by running the following command:

```text
ibmcloud plugin update atracker
```
{: pre}

## Determining if you have V1 routes and targets
{: #get-config-version-conf-version}

Once you have upgraded to the V2 CLI you can run the following command to check the configuration version running in your {{site.data.keyword.atracker_full}} Event Routing deployment.

```text
ibmcloud atracker setting get
```
{: pre}

If the response shows your deployment is running V1, you will need to [migrate your route and target configuration to a V2 configuration.](/docs/activity-tracker?topic=activity-tracker-migrate-resources)


## Next steps
{: #get-config-version-v2-next-steps}

If [step 1](#cli_version) and [step 2](#conf_version) show you have a V2 configuration, or you have completed the migration in step 2, if needed, you are ready to create and manage your {{site.data.keyword.atracker_full}} Event Routing instance using the V2 configuration.

If you have a V1 configuration, migrate to a V2 configuration. For more information, see [Migrating the {{site.data.keyword.atracker_short}} Event Routing account configuration from V1 to V2](/docs/activity-tracker?topic=activity-tracker-migration&interface=cli). 


