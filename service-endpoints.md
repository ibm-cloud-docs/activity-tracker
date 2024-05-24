---

copyright:
  years: 2019, 2024
lastupdated: "2024-05-24"

keywords:

subcollection: activity-tracker


---

{{site.data.keyword.attribute-definition-list}}


# Using service endpoints to privately connect to {{site.data.keyword.at_full_notm}}
{: #service-endpoints}

To ensure that you have enhanced control and security over your data when you use {{site.data.keyword.at_full}}, you have the option of using private routes to {{site.data.keyword.cloud}} service endpoints. Private routes are not accessible or reachable over the internet. By using the {{site.data.keyword.cloud_notm}} private service endpoints feature, you can protect your data from threats from the public network and logically extend your private network.
{: shortdesc}

<!-- Common deprecation statement -->
{{../log-analysis/_include-segments/deprecation_notice.md}}

You can use private and public endpoints to configure {{site.data.keyword.at_full}} resources in your account.

You can connect to {{site.data.keyword.at_full_notm}} over a private network by using {{site.data.keyword.cloud_notm}} private service endpoints.

- When using the classic infrastructure, you connect to resources in your account over the {{site.data.keyword.cloud_notm}} public network by default. You can enable virtual routing and forwarding (VRF) to move IP routing for your account and all of its resources into a separate routing table. If VRF is enabled, you can then enable {{site.data.keyword.cloud_notm}} service endpoints to connect directly to resources without using the public network. [Enabling VRF and service endpoints](/docs/account?topic=account-vrf-service-endpoint).

- Virtual Private Clouds (VPCs) are automatically enabled for virtual routing and forwarding (VRF). To enable service endpoints for your VPC, continue to [Enabling service endpoints](/docs/account?topic=account-vrf-service-endpoint#service-endpoint).

## Before you begin
{: #prereq-service-endpoint}

Check if the account is VRF enabled by running the following command:

```text
ibmcloud account show
```
{: pre}

To enable private endpoints, run the following command:

```text
ibmcloud account update --service-endpoint-enable true
```
{: pre}



## Setting up service endpoints for {{site.data.keyword.at_full_notm}}
{: #endpoint-setup}

By default, private and public endpoints are enabled. For more information about supported endpoints, see [Endpoints](/docs/activity-tracker?topic=activity-tracker-endpoints).


## Disabling public service endpoints for {{site.data.keyword.at_full_notm}}
{: #endpoint-disable}

You cannot disable private endpoints.

You can disable public endpoints per region in your account for {{site.data.keyword.at_full_notm}}:
- If public and private endpoints are enabled, you can disable a public endpoint by using private or public endpoints.
- If public endpoints have been disabled, you can only enable public endpoints by using the private endpoint.

For more information on how to disable a public endpoint, see [Disabling public endpoints](/docs/activity-tracker?topic=activity-tracker-endpoints_manage#endpoints-manage-disable-cli).


## Limitations using private endpoints
{: #network_endpoints_limitations}

The UI for {{site.data.keyword.at_full_notm}} is not currently supported on the CSE network.
