---

copyright:
  years: 2019, 2022
lastupdated: "2022-05-16"

keywords: IBM Cloud, Activity Tracker, security, auditing, troubleshooting

subcollection: activity-tracker

content-type: troubleshoot

---

{{site.data.keyword.attribute-definition-list}}

# Are you getting an "invalid_value" error when creating a route?
{: #troubleshoot-13}
{: troubleshoot}
{: support}

When creating a route, the following message is returned: `Your request has failed because rules per route limit 4 is reached.`.
{: shortdesc}


This information applies only if you use {{site.data.keyword.atracker_full_notm}} Event Routing.
{: important}


Your request fails with an error message and a code of `invalid_value`.
{: tsSymptoms}

You are trying to create a new route and you already have 4 routes configured in your account.
{: tsCauses}

Only 4 routes are supported in an account across all regions.  If you need to create a new route, [delete an existing route](/docs/activity-tracker?topic=activity-tracker-route_v2&interface=api#route-delete-api) and retry the request.
{: tsResolve}


