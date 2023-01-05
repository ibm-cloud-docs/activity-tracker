---

copyright:
  years: 2019, 2023
lastupdated: "2023-01-05"

keywords: Observability

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}


# Getting started with {{site.data.keyword.at_full_notm}}
{: #getting-started}

Use the {{site.data.keyword.at_full}} service to capture a record of your {{site.data.keyword.cloud_notm}} activities and monitor the activity of your {{site.data.keyword.cloud_notm}} account. You can use this service to investigate abnormal activity and critical actions, and comply with regulatory audit requirements. In addition, you can be alerted on actions as they happen. The events that are collected comply with the Cloud Auditing Data Federation (CADF) standard.
{: shortdesc}

For more information about {{site.data.keyword.atracker_full_notm}}, see [About {{site.data.keyword.atracker_short}}](/docs/atracker?topic=atracker-about).

## About {{site.data.keyword.at_full}}
{: #gs_ov}

Compliance with internal policies and industry regulations is a key requirement in any organization's strategy, regardless of where applications run: on-premises, in a hybrid cloud, or in a public cloud. The {{site.data.keyword.at_full_notm}} service provides the framework and functionality to monitor API calls to services on the {{site.data.keyword.cloud_notm}} and produces the evidence to comply with corporate policies and market industry-specific regulations.

![The {{site.data.keyword.at_full_notm}} service](images/atov.png "The {{site.data.keyword.at_full_notm}} service"){: caption="Figure 1. Activity Tracker hosted event search flow" caption-side="bottom"}

When you work in a cloud environment, such as the {{site.data.keyword.cloud_notm}}, you must plan the cloud strategy for auditing and monitoring workloads and data in accordance with your internal policies and with industry and country-based compliance requirements. You can use the information that is registered through the {{site.data.keyword.at_full_notm}} service to identify security incidents, detect unauthorized access, and comply with regulatory and internal auditing requirements.

* {{site.data.keyword.at_full_notm}} supports high-level security governance for your IT resources in the cloud.
* {{site.data.keyword.at_full_notm}} provides a solution for administrators to capture, store, view, search, and monitor API activity in a single place. It also offers a notification feature to alert you by using any of the supported notification channels.
* {{site.data.keyword.at_full_notm}} provides capabilities to export events that you can then use to generate an audit trail report. These reports might be required so that your organization complies with internal regulations and external industry and country regulations.

{{site.data.keyword.at_full_notm}} collects and stores audit records for API calls made to resources that run in the {{site.data.keyword.cloud_notm}}. You can archive these events on {{site.data.keyword.cloud_notm}} for long-term storage.
{: note}

{{site.data.keyword.cloud_notm}} administrators can configure an {{site.data.keyword.cloud_notm}} account to collect auditing events automatically for most enabled-services. However, some services might require an upgrade of the service plan, a configuration setting, or both, for you to be able to collect and analyze auditing events due to the high volumes of data that they generate. [Learn more about enabling Activity Tracker events](/docs/activity-tracker?topic=activity-tracker-events-opt-in).

For information on the services that are sending events to {{site.data.keyword.at_short}}, see [{{site.data.keyword.cloud_notm}} services that generate {{site.data.keyword.at_short}} events](/docs/activity-tracker?topic=activity-tracker-cloud_services).

Depending on your compliance and organizational requirements, you can choose {{site.data.keyword.atracker_full_notm}} or an {{site.data.keyword.at_full_notm}} hosted event search offering.
- Application environments seeking to maintain Financial Services (FS) validation status on {{site.data.keyword.cloud_notm}} should use {{site.data.keyword.atracker_full_notm}} .
- Application environments seeking compliance with PCI, SOC2, Privacy Shield and HIPAA should use an {{site.data.keyword.at_full_notm}} hosted event search offering.

[![Getting started with Event Routing](/images/getting_started_routing.svg)](/docs/atracker?topic=atracker-getting-started) [![Getting started with hosted event and search offerings](/images/getting_started_event.svg)](/docs/activity-tracker?topic=activity-tracker-getting-started-search)

## Security
{: #gs_ov_security}

Consider the following information about security when you work with the {{site.data.keyword.at_full_notm}} service:

* IBM services that generate {{site.data.keyword.at_full_notm}} events follow the {{site.data.keyword.IBM_notm}} Cloud security policy. For more information, see [Trust the security and privacy of IBM Cloud](https://www.ibm.com/cloud/security){: external}.
* The {{site.data.keyword.at_full_notm}} service captures user-initiated actions that change the state of {{site.data.keyword.IBM_notm}} Cloud services. The information does not provide direct access to databases or applications.
* Only authorized users can view and monitor {{site.data.keyword.at_full_notm}} event logs. Each user is identified by their unique ID in the {{site.data.keyword.cloud_notm}}.
* You can only provision 1 instance of the service per {{site.data.keyword.cloud_notm}} location (region).


## Getting started
{: #gs_objectives}

Complete this tutorial to learn how to provision an {{site.data.keyword.at_full_notm}}  service in the {{site.data.keyword.cloud_notm}}. Find out what common data is available in each event and how it can help you monitor your {{site.data.keyword.cloud_notm}} environment. Learn to navigate in the web UI.


## Prerequisites
{: #gs_prereq}

* You need a user ID that is a member, or an owner of, an {{site.data.keyword.cloud_notm}} account. To get an {{site.data.keyword.cloud_notm}} user ID, go to: [Create an account](https://cloud.ibm.com/login){: external}.

* If you prefer to work with the command line, you must install the {{site.data.keyword.cloud_notm}} CLI. For more information, see [Installing the {{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cli-install-ibmcloud-cli).

* To complete the steps to manage access to the service, your user ID needs **administrator platform permissions** to manage the {{site.data.keyword.at_full_notm}} service. Contact the account owner. The account owner can grant another user access to the account for the purposes of managing user access, and managing account resources. [Learn more](/docs/account?topic=account-userroles).


## Provision an instance of the {{site.data.keyword.at_full_notm}} service
{: #gs_step1}

Complete the following steps to provision an instance:

1. Log in to your [{{site.data.keyword.cloud_notm}} account](https://cloud.ibm.com/login){: external}.

   After you log in with your user ID and password, the {{site.data.keyword.cloud_notm}} UI opens.

2. Go to the menu icon ![Menu icon](../icons/icon_hamburger.svg) and select **Observability** to access the *Observability* dashboard.

3. Select **Activity Tracker**, then click **Create**.

4. Enter a name for the service instance.

5. Select the **Frankfurt** location.

   For more information about the regions where the service is available, see [Regions](/docs/services/activity-tracker?topic=activity-tracker-regions).

6. Select a resource group.

   By default, the **default** resource group is set.

   **Note:** If you are not able to select a resource group, check that you have editing permissions on the resource group where you want to provision the instance.

7. Select the `Lite` service plan.

   By default, the lite plan is set.

8. Click **Create**.

   After you provision an instance, the *Activity Tracker* dashboard, that is located in the *Observability* section of the {{site.data.keyword.cloud_notm}} UI, opens.


## Manage access to the service
{: #gs_step2}

**Every user that accesses the {{site.data.keyword.at_full_notm}} service in your account must be assigned an access policy with an IAM user role defined.** The policy determines what actions the user can perform within the context of the service or instance you select. The allowable actions are customized and defined as operations that are allowed to be performed on the service. The actions are then mapped to IAM user roles. [Learn more](/docs/services/activity-tracker?topic=activity-tracker-iam).
{: important}

To grant a user management permissions to work with the {{site.data.keyword.at_full_notm}} service within the context of a resource group, complete the following steps:


### Create an access group
{: #gs_step2_1}

Complete the following steps to create an access group:
1. From the menu bar, click **Manage** &gt; **Access (IAM)**, and select **Access Groups**.
2. Click **Create**.
3. Enter a name and optional description for your group, and click **Create**.

### Add permissions to manage events
{: #gs_step2_2}

After you set up your group, you must assign a common access policy to the group. Any policy that you set for an access group applies to all entities, users and service IDs, within the group.

When you define the policy, you need to select a platform role and a service role:
* Platform management roles cover a range of actions, including the ability to create and delete instances, manage aliases, bindings, and credentials, and manage access. The platform roles are administrator, editor, operator, viewer. Platform management roles also apply to account management services that enable users to invite users, manage service IDs, access policies, catalog entries, and track billing and usage depending on their assigned role on an account management service.
* Service access roles define a user or service’s ability to perform actions on a service instance. The service access roles are manager, writer, and reader.

To manage the {{site.data.keyword.at_full_notm}} service, a user needs the following roles:
* Platform role: **Administrator**.
* Service role: **Manager**.


Complete the following steps to assign a policy through the UI:

1. From the menu bar, click **Manage** &gt; **Access (IAM)**.
2. Select **Access Groups**.
3. Select the name of the group that you want to assign access to.
4. Click **Access policies** &gt; **Assign access**.
5. Select **IAM services**.
6. For the field *What type of access do you want to assign?*, select **{{site.data.keyword.at_full_notm}}**.
7. For the *in* field, select the resource group.
8. Select the platform role **Administrator**.
9. Select the service role **Manager**.
10. Click **Add**. Then, select **Assign**.


### Add the user to the group
{: #gs_step2_3}

Complete the following steps to add the user to the access group:
1. Click **Add users** on the **Users** tab.
2. Select the user that you want to add from the list, and click **Add to group**.


## Generate {{site.data.keyword.at_full_notm}} events
{: #gs_step3}
{: step}

If you have a pay-as-you-go account, you can use {{site.data.keyword.keymanagementservicelong}} to create an event. If you don't have a pay-as-you-go account, provisioning any of the available lite services triggers an event.


1. From the [{{site.data.keyword.cloud_notm}} catalog](https://cloud.ibm.com/catalog){: external}, select the category **Security**.

2. Select the {{site.data.keyword.keymanagementserviceshort}} service.

3. (Optional) [Provision an instance of the {{site.data.keyword.keymanagementserviceshort}} service](/docs/key-protect?topic=key-protect-getting-started-tutorial#getting-started-tutorial).

## Launch the web UI
{: #gs_step4}

Complete the following steps to launch the web UI:

1. [Log in to your {{site.data.keyword.cloud_notm}} account](https://cloud.ibm.com/login){: external}.

	After you log in with your user ID and password, the {{site.data.keyword.cloud_notm}} dashboard opens.

2. In the navigation menu, select **Observability**.

3. Select **Activity Tracker**.

    The list of instances that are available on {{site.data.keyword.cloud_notm}} is displayed.

4. Select the instance that is located in **Frankfurt**. Then, click **Open Dashboard**.

    Global events, such as provisioning a service, are available through the global domain instance that is located in Frankfurt.

The web UI opens.


## View events
{: #gs_step5}


The {{site.data.keyword.at_full_notm}} service captures activity data that is related to API calls and other actions that are made to selected cloud services in the {{site.data.keyword.cloud_notm}}.

* Events are collected automatically.
* Events that are collected in {{site.data.keyword.at_full_notm}} comply with the **Cloud Auditing Data Federation (CADF) standard**. The CADF standard defines a full event model that includes the information that is needed to certify, manage, and audit security of applications in cloud environments.
* {{site.data.keyword.at_full_notm}} stores and groups events by location.
* Events that report on global {{site.data.keyword.cloud_notm}} account actions, are collected and stored in **Frankfurt (EU-DE)**.
* The service plan that you select for your {{site.data.keyword.at_full_notm}} instance sets the number of days that events are available for search through the web UI.

When the web UI opens, the **EVERYTHING** view is displayed. You can see events through this view.

You can also define custom views to view a set of events by applying a timestamp, a search query, or both. [Learn more](/docs/services/activity-tracker?topic=activity-tracker-views).


## Learn about the structure of an event
{: #gs_step6}

Events comply with the **Cloud Auditing Data Federation (CADF) standard**. The CADF standard defines a full event model that includes the information that is needed to certify, manage, and audit security of applications in cloud environments.

The CADF event model includes the following components:

| Component | Description |
|------------|----------------------------|
| `Action`   | The action is the operation or activity that an initiator performs, attempts to perform, or is waiting to complete. |
| `Initiator`| The initiator is the resource that makes an API call and generates a CADF event. The event that is triggered depends on the action that is requested by the API call. |
| `Observer` | The observer is the resource that creates and stores a CADF record from information available in a CADF event. |
| `Outcome`  | The outcome is the status of the action against the target. |
| `Target`   | The target is the resource against which the action is performed, attempted to perform, or is pending to complete. |
{: caption="Table 1. Components that are available in a CADF event model" caption-side="top"}

[Learn more](/docs/services/activity-tracker?topic=activity-tracker-event#event).



## Next steps
{: #gs_next_steps}

1. [Define custom views](/docs/services/activity-tracker?topic=activity-tracker-views).

2. Upgrade the {{site.data.keyword.at_full_notm}} service plan to a paid plan to be able to [search events by applying a query](/docs/services/activity-tracker?topic=activity-tracker-views#views_step2) and [configure alerts](/docs/services/activity-tracker?topic=activity-tracker-alerts).

   For more information about {{site.data.keyword.at_full_notm}} service plans, see [Service plans](/docs/services/activity-tracker?topic=activity-tracker-service_plan#service_plan).
