---

copyright:
  years: 2019, 2024
lastupdated: "2024-05-24"

keywords:

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}

# Is streaming not working?
{: #troubleshoot-01}
{: troubleshoot}
{: support}

Streaming is failing because your {{site.data.keyword.at_short}} instance cannot connect to the {{site.data.keyword.messagehub}} Kafka broker.
{: shortdesc}


{{../log-analysis/_include-segments/deprecation_notice.md}}

You get the following error message: `Failed to connect to Kafka broker: KafkaJSSASLAuthenticationError: SASL PLAIN authentication failed: Authentication failed, invalid credentials`.
{: tsSymptoms}

The account has been configured to restrict access to configured IP address rules via IAM or the account limits the network locations that connections are accepted from.
{: tsCauses}


Configure the account by allowlisting the {{site.data.keyword.at_short}} CIDR blocks in the account. For more information, see [{{site.data.keyword.at_short}} CIDR blocks](/docs/activity-tracker?topic=activity-tracker-cidr). Follow the instructions in [{{site.data.keyword.messagehub}} - Restricting network access](/docs/EventStreams?topic=EventStreams-restrict_access).
{: tsResolve}
