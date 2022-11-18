---

copyright:
  years: 2019, 2022
lastupdated: "2022-06-22"

keywords: 

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}
 

# Using the Track Access template
{: #templates-track-access}

Use the {{site.data.keyword.at_full_notm}} Track Access template to gain insight on your {{site.data.keyword.cloud_notm}} access requests. Monitor login requests, unauthorize access, and denied requests.
{: shortdesc}


## Overview
{: #templates-track-access-ov}

The {{site.data.keyword.at_short}} track access template includes the following artifacts:
- Parsing templates to pull additional information from the data to enhance searchability and simplify customization such as `region`, `RC` and `accountID`.
- Views and screens that allow you to monitor activity in your account.

This template uses global events that are available through the Frankfurt region. In {{site.data.keyword.at_short}}, you can monitor global events through the instance in Frankfurt (EU-DE). Deploy this template in the Frankfurt region to monitor activity.


## Deploying the track access templates
{: #templates-track-access-deploy}

Complete the following steps to deploy the track access template objects in 1 {{site.data.keyword.at_short}} instance:

### Step 1. Launch the template library
{: #templates-track-access-step1}

The {{site.data.keyword.at_short}} hosted event search offering template library offers multiple tiles that group predefined views, dashboards, and screens by area. One of them is the **Track Archiving** template.

Complete the following steps to launch the {{site.data.keyword.at_short}} template library:

1. [Log in to your {{site.data.keyword.cloud_notm}} account](https://cloud.ibm.com/login){: external}.

	After you log in with your user ID and password, the {{site.data.keyword.cloud_notm}} dashboard opens.

2. Click the **Menu** icon ![Menu icon](../icons/icon_hamburger.svg) &gt; **Observability**.

3. Select **Activity Tracker**.

    The list of {{site.data.keyword.at_short}} instances is displayed.

    There is 1 instance per region.
    {: important}

4. Select the {{site.data.keyword.at_short}} instance in the region where you want to deploy the template. Then, click **Open Dashboard**.

### Step 2. Install the template
{: #templates-track-access-step2}

Complete the following steps to deploy the **Track Access** template:

1. From the {{site.data.keyword.at_short}} instance UI, click the **Settings** icon ![Settings icon](/images/config.png) &gt; **Template Library**.  The tiles show the available template libraries.  

2. In the Template library section, select the **Track Access** tile.

3. Choose the views and screen resources that you want to deploy. Make sure you select the parsing templates.

4. Click **Apply template**.  

    If you do not select one or more options within the template library, all options will be deployed.
    {: note}

    What you deploy appear under the appropriate sections of the UI.  For example if you deploy a screen, it will deploy under **Screens**.

5. Refresh your browser to see the template objects.


After you deploy the template, it may take a while for the parsing templates to be enabled. The new indexed fields that are included with the parsing templates are needed for the template to filter and display data.
{: important}

## Template objects
{: #templates-track-access-objects}

### Predefined views
{: #templates-track-access-views}

Use these views to gain insight on your {{site.data.keyword.cloud_notm}} access requests.
{: note}


| View name | Description |
|-----------|-------------|
| `[CBR] [Report] Allowed access requests` | Use this view to evaluate whether this access flow is supposed to be allowed, or whether you need to update your rule to deny access so that your resources are protected. |
| `[CBR] [Report] Blocked access requests report` | Use this view to evaluate whether this access flow is supposed to be denied, or whether you need to update your rule to allow access so that your workflows don't break. |
| `[CBR] Blocked access requests` | Use this view to find access flows that have been denied and blocked.|
| `[Login] [TP] Compute resources login sessions`     | Use this view to monitor trusted profile logins for compute resources. |
| `[Login] [TP] Federated users login sessions` | Use this view to monitor trusted profile (TP) logins for federated users. |
| `[Login] Service ID API Key logins` | Use this view to monitor logins with service ID API keys. |
| `[Login] User API Key logins` | Use this view to monitor logins with user API keys. |
{: caption="Table 1. Predefined views" caption-side="bottom"}

For more information, see [Monitoring login sessions for trusted profiles](/docs/account?topic=account-trusted-profile-monitor&interface=ui) and [Monitoring context-based restrictions](/docs/account?topic=account-cbr-monitor&interface=ui).


### Predefined screens
{: #templates-track-access-screens}


The following table outlines the predefined screens that you can use to gain insight on your {{site.data.keyword.cloud_notm}} access requests. 

| Screen name | Description |
|-------------|-------------|
| `Activity Summary` | View statistics and gain insight on your {{site.data.keyword.cloud_notm}} requests. |
| `Login and Requests Status`  | View statistics about login, unauthorize access, and denied requests. |
{: caption="Table 2. Predefined screens" caption-side="bottom"}






