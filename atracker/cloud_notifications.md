---

copyright:
  years: 2022
lastupdated: "2022-03-22"

keywords: IBM Cloud, Activity Tracker, notifications, event routing

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}


# Enabling IBM Cloud notifications
{: #cloud_notifications}

{{site.data.keyword.cloud_notm}} users can choose to receive email notifications about {{site.data.keyword.cloud_notm}} platform-related items, such as announcements, billing and usage, additional notification preferences, and ordering. Users can also update their preferences to receive email notifications about resource-related items, such as incidents, maintenance, security bulletins, or resource activity on the Notification preferences page. These notifications are for only the resources in use.  You can use these notifications to be alerted when credential issues affect {{site.data.keyword.atracker_full}} event routing.
{: shortdesc}

This information applies only if you use {{site.data.keyword.atracker_full_notm}} event routing.
{: important}

## {{site.data.keyword.atracker_full_notm}} event routing notifications
{: #at_cloud_notifications}

{{site.data.keyword.cloud_notm}} notifications can alert you when {{site.data.keyword.atracker_full_notm}} users update their {{site.data.keyword.cos_full_notm}} (COS) API key without updating the COS API key associated with the target.  Not updating the credentials in both places will result in failures writing to the target.

When you create a target initially, and the API keys do not match, you will receive an error message.  Using {{site.data.keyword.cloud_notm}} notifications helps you know when the COS API key has been changed after {{site.data.keyword.atracker_full_notm}} starts sending events to COS.

If the API key is not updated in both {{site.data.keyword.atracker_full_notm}} and {{site.data.keyword.cos_full_notm}}, a notification similar to the following is sent:

```screen
Misconfigured Activity Tracker event routing target
```
{: codeblock}

Additional notifications include:

```screen
Activity Tracker event routing target started discarding events
```
{: codeblock}

This notification is sent when the limit of undelivered auditing events has been reached.

Once you have resolved the API key issue the following notification will be sent.

```screen
Activity Tracker event routing target is recovered.
```
{: codeblock}

## Configuring {{site.data.keyword.cloud_notm}} notifications
{: #config_cloud_notifications}

See [setting email preferences for notifications](/docs/account?topic=account-email-prefs) for more information on configuring {{site.data.keyword.cloud_notm}} notifications.


