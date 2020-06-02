---

copyright:
  years: 2019, 2020
lastupdated: "2020-04-08"

keywords: IBM Cloud, LogDNA, Activity Tracker, CF events

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

# Cloud Foundry events  
{: #at_events_cf}

As a security officer, auditor, or manager, you can use the {{site.data.keyword.at_full_notm}} service to track how users and applications interact with the {{site.data.keyword.cloud_notm}} services. 
{:shortdesc}

The {{site.data.keyword.at_full_notm}} service records user-initiated activities that change the state of a service in {{site.data.keyword.cloud_notm}}. To get started monitoring your user's actions, see [{{site.data.keyword.at_full_notm}}](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-getting-started#getting-started). 


## Events for managing user permissions
{: #cf_user}

The following table lists the actions that generate an event:

| Action                                   | Description |
|------------------------------------------|---------|
| `service_name.instance.create`           | An event is generated when you provision a service instance. |
| `service_name.instance.update`           | An event is generated when you rename a service instance or when you change the service plan. |
| `service_name.instance.delete`           | An event is generated when a service instance is deleted. |
| `service_name.instance.schedule_reclaim` | An event is generated when a service instance is pending_reclamation. |
| `service_name.instance.restore`          | An event is generated when a service instance is restored. |
{: caption="Table 1. Actions that generate events" caption-side="top"} 
 

Add/remove user to an org and space does not include the target.name with the human readable name of the user that is being added or removed:
Cloudfoundry does only provide the guid of the "changed" user (actee) but the field actee_name (which is normally forwarded to target.name) is always empty for these events:

    audit.user.space_auditor_add
    audit.user.space_auditor_remove
    audit.user.space_manager_add
    audit.user.space_manager_remove
    audit.user.space_developer_add
    audit.user.space_developer_remove
    audit.user.organization_auditor_add
    audit.user.organization_auditor_remove
    audit.user.organization_billing_manager_add
    audit.user.organization_billing_manager_remove
    audit.user.organization_manager_add
    audit.user.organization_manager_remove
    audit.user.organization_user_add
    audit.user.organization_user_remove




    Some fields do not follow AT guidance like:

    target.id which is not a fully defined crn
    CF does not know the concept of CRNs. In order to make that happen, we would need to compute the CRN based on the ID we have and the type of event, its a different id and a different format for the CRN.
    Severity field does not contain values per the guidelines
    According to the internal activity tracker documentation the severity field should contain the values : "Normal", "Warning" and "Crititcal". CF does not provide these informations. Right now the field contains the hardcoded value "INFO"

    Create a service instance is missing information on the organization:
    Cloudfoundry does provide org and space guid in the events table. Eventforwarder reads given information and has it available but does not forward the given information. It would be super easy to add the values in the meta-data in at-events








-	Renaming a service instance is missing the original name
Update information on old value is not included. Only the new value is included.
o	 
o	State reports if the application has been stopped or started. When it is restarted, you get 2 events, one reporting the stop, and the other one reporting the start.
o	Name reports the new name of the CF app. The CF app ID does not change.To get the CF app GUID:
ibmcloud cf app GetStartedJava-demo –guid
If you search by target.id:5feaa322-0a48-4a64-ba41-236f861e489c, you can get all the activity in the account for that CF app
 

-	Some events like audit.user.space_add_auditor are missing information on the target.name.







## Where to look for the events
{: #cf_ui}

Events are available in the **Frankfurt (eu-de)** region. 

To view these events, you must [provision an instance](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-provision#provision) of the {{site.data.keyword.at_full_notm}} service in the **Frankfurt (eu-de)** region. Then, you must [open the {{site.data.keyword.at_full_notm}} UI](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-launch#launch_step2). 



## Analyzing events
{: #cf_analyze}

**Action: service_name.instance.delete**

When a service instance is deleted, consider the following information:
* Other actions are automatically triggered to clean up IAM permissions. These actions remove policies that are configured for users and service IDs in the account to work with the service instance. 
* The initiator of these actions is an {{site.data.keyword.IBM_notm}} service ID.


When the service instance that is deleted does not have IAM policies configured for users and service IDs, the events that are automatically generated for any of these resources report an outcome of`failure` with a `404` outcome code. The following sample shows the events that are generated when a service instance that does not have policies configured in the account is deleted:

```
Apr 30 09:04:16 cloudcerts: delete instance Certificate Manager-v1
Apr 30 09:41:20 IAM Access Management: delete policy -failure
Apr 30 09:41:20 IAM Access Management: delete policy -failure
```
{: screen}
