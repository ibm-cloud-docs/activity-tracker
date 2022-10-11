---

copyright:
  years: 2019, 2022
lastupdated: "2022-05-13"

keywords: IBM Cloud, Activity Tracker, security, auditing, troubleshooting

subcollection: activity-tracker

content-type: troubleshoot

---

{{site.data.keyword.attribute-definition-list}}

# Are you getting a "target_limit_reached" error when creating a target?
{: #troubleshoot-12}
{: troubleshoot}
{: support}

When creating a target, the following message is returned: `You have reached the limit of targets that you can define in your account. Remove unused targets, then try again.`.
{: shortdesc}


This information applies only if you use {{site.data.keyword.atracker_full_notm}} .
{: important}


Your request fails with an error message and a code of `target_limit_reached`.
{: tsSymptoms}

You are trying to create a new target and you already have 16 targets configured in your account.
{: tsCauses}

Only 16 targets are supported in an account across all regions. If you need to create a new target, delete an existing [COS target](/docs/activity-tracker?topic=activity-tracker-target_v2_cos&interface=api#target-delete-api-cos) or an existing [LogDNA target](/docs/activity-tracker?topic=activity-tracker-target_v2_at&interface=api#target-delete-api-at) that is no longer needed and retry the request.
{: tsResolve}


