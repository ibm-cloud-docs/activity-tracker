---

copyright:
  years: 2019, 2022
lastupdated: "2022-05-13"

keywords: IBM Cloud, Activity Tracker, security, auditing, troubleshooting

subcollection: activity-tracker

content-type: troubleshoot

---

{{site.data.keyword.attribute-definition-list}}

# Are you getting an "access denied" error when trying to create a COS target?
{: #troubleshoot-06}
{: troubleshoot}
{: support} 

When creating an {{site.data.keyword.cos_full_notm}} target using service-to-service authorization, the message `Your request to test a target has failed because the target details are not valid. The service could not write to the Cloud Object Storage bucket that is configured. {'error_code':'403','error_message':'Access Denied'}` is returned.
{: shortdesc}


This information applies only if you use {{site.data.keyword.atracker_full_notm}} Event Routing.
{: important}


Your request fails with an error message that indicates access to the {{site.data.keyword.cos_full_notm}} bucket was denied.
{: tsSymptoms}

You define a bucket in an account but have not set up [service-to-service authorization](/docs/activity-tracker?topic=activity-tracker-target_v2_cos&interface=cli#cos_s2s) to that bucket.  Then you attempt to create an {{site.data.keyword.cos_full_notm}} target pointing to the bucket using service-to-service authorization (`--service-to-service-enabled TRUE`), instead of using the [COS bucket API key.](/docs/activity-tracker?topic=activity-tracker-target_v2_cos&interface=cli#cos_apikey).
{: tsCauses}

Either setup [service-to-service authorization to the bucket](/docs/activity-tracker?topic=activity-tracker-target_v2_cos&interface=cli#cos_s2s) and retry the target create request, or use the [COS bucket API key](/docs/activity-tracker?topic=activity-tracker-target_v2_cos&interface=cli#cos_apikey) on the create request.
{: tsResolve}


