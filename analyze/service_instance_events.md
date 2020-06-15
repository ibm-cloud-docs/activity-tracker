---

copyright:
  years: 2019, 2020
lastupdated: "2019-01-08"

keywords: IBM Cloud, LogDNA, Activity Tracker, service instance events

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

# Managing service instances
{: #service_instance_events}

{{site.data.keyword.at_full_notm}} events 
{:shortdesc}



| Working with services                   | Service     | Actions                                        |
|:----------------------------------------|:------------|:-----------------------------------------------|
| `Provision an instance`                 | `BSS`       | `<serviceName>.instance.create` |
| `Delete an instance`                    | `BSS`       | `<serviceName>.instance.delete` </br>`iam-am.policy.delete` (3 events of these type) |
| `Delete an instance with a tag`         | `BSS`       | `<serviceName>.instance.delete` | 
| `Rename an instance`                    | `BSS`       | `<serviceName>.instance.update` |
| `Add a tag to an instance`              | `BSS`       | `global-search-tagging.tag.attach-tag` | 





```
6/Dec/2019:10:14:04 BSS IBM Cloud Activity Tracker with LogDNA: create instance at-logdna-tokyo 
```


```
6/Dec/2019:09:38:32 BSS IBM Log Analysis with LogDNA: create instance logdna-via-cli
6/Dec/2019:09:42:03 BSS IBM Log Analysis with LogDNA: create instance logdna-via-ui
6/Dec/2019:09:42:04 iam-am IAM Access Management: create policy 
6/Dec/2019:09:42:04 iam-identity IAM Identity Service: create account-serviceid logdna-via-ui-key-admin
6/Dec/2019:09:42:04 iam-identity IAM Identity Service: create serviceid-apikey logdna-via-ui-key-admin
6/Dec/2019:09:42:05 BSS logdna: create key logdna-via-ui-key-admin
6/Dec/2019:09:42:05 iam-am IAM Access Management: create policy 
```


```
6/Dec/2019:10:13:35 BSS IBM Cloud Activity Tracker with LogDNA: delete instance at-logdna-tokyo
6/Dec/2019:10:13:36 iam-am IAM Access Management: delete policy 
6/Dec/2019:10:13:36 iam-am IAM Access Management: delete policy 
6/Dec/2019:10:13:36 iam-am IAM Access Management: delete policy 
```

```
6/Dec/2019:10:26:39 iam-am IAM Access Management: create policy 
6/Dec/2019:10:26:39 iam-identity IAM Identity Service: create account-serviceid logdna-via-cli-key-admin
6/Dec/2019:10:26:39 iam-identity IAM Identity Service: create serviceid-apikey logdna-via-cli-key-admin
6/Dec/2019:10:26:39 iam-am IAM Access Management: create policy 
```





| Action                                          | Description |
|-------------------------------------------------|-------------|
| `global-search-tagging.tag.attach`              | An event is generated when you associate a tag to a resource. |
| `global-search-tagging.tag.detach`              | An event is generated when you remove a tag from a resource.  |
| `global-search-tagging.tag.update`              | An event is generated when you update a tag that is attached to a resource.  |
| `global-search-tagging.tag.delete`              | An event is generated when you delete a tag in your account.  |
| `global-search-tagging.tag.deleteall`           | An event is generated when you delete all the tags that are not attached to resources in your account.  |
{: caption="Table 4. Actions that generate events" caption-side="top"} 


