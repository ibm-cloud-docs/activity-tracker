---

copyright:
  years: 2019, 2024
lastupdated: "2024-05-24"

keywords:

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}

# Monitoring streaming to an {{site.data.keyword.at_short}} instance (WIP)
{: #streaming-monitor-l2l}

missimng data on failures and samples
{: important}

You can use {{site.data.keyword.at_full_notm}} to monitor streaming of data from your {{site.data.keyword.at_short}} instance to a destination {{site.data.keyword.at_short}} instance.
{: shortdesc}


{{../../log-analysis/_include-segments/deprecation_notice.md}}


## Monitoring streaming by using {{site.data.keyword.at_full_notm}}
{: #streaming-monitor-2}

Streaming generates {{site.data.keyword.at_short}} events with the action **logdna.streaming-logs.send** to notify about failures when data is streamed  to {{site.data.keyword.messagehub}}.
