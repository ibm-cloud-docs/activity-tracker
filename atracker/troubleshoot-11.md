---

copyright:
  years: 2019, 2022
lastupdated: "2022-05-13"

keywords: IBM Cloud, Activity Tracker, security, auditing, troubleshooting

subcollection: activity-tracker

content-type: troubleshoot

---

{{site.data.keyword.attribute-definition-list}}

# Are you getting a "setting limit" error when creating a target?
{: #troubleshoot-11}
{: troubleshoot}
{: support}

When creating a default target, the following message is returned: `Your request has failed because default_targets per setting limit 2 is reached.`.
{: shortdesc}


This information applies only if you use {{site.data.keyword.atracker_full_notm}} Event Routing.
{: important}


Your request fails with an error message and a code of `invalid_value`.
{: tsSymptoms}

You are trying to create or update your settings and specified more than two default target values (`--default-targets`) on the request.
{: tsCauses}

[Only two default target values are supported.](/docs/activity-tracker?topic=activity-tracker-settings) Retry your request specifying only two default targets for `--default-targets`.
{: tsResolve}


