---

copyright:
  years: 2018
lastupdated: "2018-11-15"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# Getting started with {{site.data.keyword.at_full_notm}}
{: #getting-started}

Use {{site.data.keyword.at_full}} to add log management capabilities to your {{site.data.keyword.Bluemix}} architecture. {{site.data.keyword.at_full_notm}} is operated by LogDNA in partnership with {{site.data.keyword.IBM_notm}}.
{:shortdesc}


## Step 1: Before you begin
{: #prereqs}

* Read about {{site.data.keyword.at_full_notm}}. For more information, see [About {{site.data.keyword.at_full_notm}}](/docs/services/Activity-Tracker-with-LogDNA/overview.html#about).
* Check the regions where the service is available. For more information, see [Regions](/docs/services/Activity-Tracker-with-LogDNA/overview.html#regions).
* Get a user ID that is a member or an owner of an {{site.data.keyword.Bluemix_notm}} account. 

    To get an {{site.data.keyword.Bluemix_notm}} user ID, go to: [Registration ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/registration/){:new_window}.



## Step 2: Get started
{: #getstarted}

Choose a cloud resource for which you want to manage logs. Then, configure this log source so that you can monitor its logs through the {{site.data.keyword.at_full_notm}} service.

The following table lists cloud resources that you can configure to store and manage logs by using the {{site.data.keyword.at_full_notm}} service. Complete the tutorial for a resource to get started working with the {{site.data.keyword.loganalysisshort}} service:

<table>
  <caption>Tutorials to get started working with the {{site.data.keyword.at_full_notm}} service </caption>
  <tr>
    <th>Resource</th>
    <th>Tutorial</th>
    <th>Environment</th>
    <th>Scenario</th>
  </tr>
  <tr>
    <td>Containers running on the {{site.data.keyword.containershort}}</td>
    <td>[Managing Kubernetes cluster logs with {{site.data.keyword.at_full_notm}}](/docs/services/Activity-Tracker-with-LogDNA/tutorials/kube.html#kube)</td>
    <td>{{site.data.keyword.Bluemix_notm}} Public </td>
    <td>![{{site.data.keyword.containershort}} and the {{site.data.keyword.at_full_notm}}](images/kube.png "{{site.data.keyword.containershort}} and the {{site.data.keyword.at_full_notm}}")</td>
  </tr>
  <tr>
    <td>Linux Ubuntu/Debian</td>
    <td>[Managing Linux Ubuntu logs with {{site.data.keyword.at_full_notm}}](/docs/services/Activity-Tracker-with-LogDNA/tutorials/ubuntu.html#ubuntu)</td>
    <td>On premisses</td>
    <td>![Ubuntu server and the {{site.data.keyword.at_full_notm}}](images/ubuntu.png "Ubuntu server and the {{site.data.keyword.at_full_notm}}")</td>
  </tr>
</table>



## Step 3: Upgrade the plan
{: #upgrade}

Enable additional logging features.

Upgrade the {{site.data.keyword.at_full_notm}} service plan to a paid plan to be able to [filter logs](/docs/services/Activity-Tracker-with-LogDNA/view_logs.html#step5), [search logs](/docs/services/Activity-Tracker-with-LogDNA/view_logs.html#step6), [define views](/docs/services/Activity-Tracker-with-LogDNA/view_logs.html#step7), and [configure alerts](https://docs.logdna.com/docs/alerts). . For more information about {{site.data.keyword.at_full_notm}} service plans, see [Pricing plans](/docs/services/Activity-Tracker-with-LogDNA/overview.html#pricing_plans).

## Step 4: Manage user access with IAM
{: #iam}

Identify the IAM policies that a user needs to work with the {{site.data.keyword.at_full_notm}} service.

To learn more about IAM integration with the {{site.data.keyword.at_full_notm}} service, see [Managing user access with IAM](/docs/services/Activity-Tracker-with-LogDNA/iam.html#iam).

For example, learn how to grant permissions to a user to work with the {{site.data.keyword.at_full_notm}} service:

| User role in the {{site.data.keyword.Bluemix_notm}} | For more information                     |
|-----------------------------------------------------|------------------------------------------|
| Account owner                                       | [Granting permissions to a user to become an administrator of the service in the {{site.data.keyword.Bluemix_notm}} account](/docs/services/Activity-Tracker-with-LogDNA/work_iam.html#admin_account) |
| Platform service administrator in the account       | [Granting permissions to a user to become an administrator of the service in the {{site.data.keyword.Bluemix_notm}} account](/docs/services/Activity-Tracker-with-LogDNA/work_iam.html#admin_account) |
| Platform service administrator in a resource group  | [Granting permissions to a user to become an administrator of the service within a resource group](/docs/services/Activity-Tracker-with-LogDNA/work_iam.html#admin_rg) |
| Platform Devops operator in the account           | [Granting permissions to a Devops user to manage the service in the {{site.data.keyword.Bluemix_notm}} account](/docs/services/Activity-Tracker-with-LogDNA/work_iam.html#devops_account) |
| Platform Devops operator in a resource group        | [Granting permissions to a Devops user to manage the service within a resource group](/docs/services/Activity-Tracker-with-LogDNA/work_iam.html#devops_rg) |
| Service administrator in LogDNA                     | [Granting permissions to manage logs and configure alerts in LogDNA](/docs/services/Activity-Tracker-with-LogDNA/work_iam.html#admin_user_logdna)              |
| User / developer                                    | [Granting permissions to a user to view and manage logs in LogDNA](/docs/services/Activity-Tracker-with-LogDNA/work_iam.html#user_logdna)               |
{: caption="Table 2. Cloud roles in the {{site.data.keyword.Bluemix_notm}}" caption-side="top"}


