---

copyright:
  years: 2019
lastupdated: "2019-12-04"

keywords: IBM Cloud, LogDNA, Activity Tracker, service instance events

subcollection: logdnaat

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

Multifactor authentication (MFA) adds an extra layer of security to your account by requiring all users to authenticate by using an additional authentication method beyond an ID and password. This is also commonly known as two-factor authentication (2FA). When you change MFA settings at the account level or for users in your account, you get {{site.data.keyword.at_full_notm}} events to monitor these actions.
{:shortdesc}





| Working with services                   | Service     | Actions                                        |
|:----------------------------------------|:------------|:-----------------------------------------------|
| `Provision an instance`                 | `BSS`       | '<serviceName>.instance.create` |
| `Delete an instance`                    | `BSS`       | `<serviceName>.instance.delete` </br>`iam-am.policy.delete` (3 events of these type) |
| `Delete an instance with a tag`         | `BSS`       | `<serviceName>.instance.delete` | 
| `Rename an instance`                    | `BSS`       |  `<serviceName>.instance.update` |
| `Add a tag to an instance`              | `BSS`       | `global-search-tagging.tag.attach-tag` | 