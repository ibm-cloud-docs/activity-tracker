---

copyright:
  years: 2019, 2024
lastupdated: "2024-05-24"

keywords:

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}

# Managing API keys (WIP)
{: #iam_apikeys_events}


{{site.data.keyword.cloud_notm}} services that are organized in a resource group in your account are managed by using {{site.data.keyword.iamlong}} (IAM). You can monitor IAM actions in your account with the {{site.data.keyword.at_full_notm}} service.
{: shortdesc}



{{../../log-analysis/_include-segments/deprecation_notice.md}}







## Events that are generated when you work with API keys
{: #iam_apikeys_events_generated}


| Working with API keys                   | Service     | Actions                                        |
|:----------------------------------------|:------------|:-----------------------------------------------|
| `Create an IBM Cloud API key`           | `IAM`       | `iam-identity.user-apikey.create` |
| `Lock an API key`                       | `IAM`       |`iam-identity.user-apikey.update` |
| `Unlock an API key`                     | `IAM`       | `iam-identity.user-apikey.update` |
| `Change the description of an API key`  | `IAM`       | `iam-identity.user-apikey.update`  |
| `Rename an API key`                     | `IAM`       |`iam-identity.user-apikey.update` |
| `Delete an API key`                     | `IAM`       |`iam-identity.user-apikey.delete` |
{: caption="Table 1. API key events" caption-side="top"}
