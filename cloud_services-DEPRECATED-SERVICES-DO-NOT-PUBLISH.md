---

copyright:
  years: 2019, 2023
lastupdated: "2022-10-07"

keywords: IBM Cloud, {{site.data.keyword.atracker_short}}, security, auditing, services, {{site.data.keyword.at_short}} hosted event search offering

subcollection: activity-tracker


---

{{site.data.keyword.attribute-definition-list}}



# Cloud services - DEPRECATED SERVICES
{: #cloud_services}

Use {{site.data.keyword.atracker_short}} to monitor user-initiated activities that change the state of any of the following services in the {{site.data.keyword.cloud_notm}}.
{: shortdesc}

## Analytics services
{: #analytics}

The following table lists analytics services that send auditing events:

| Service     | CRN service name | {{site.data.keyword.at_short}} hosted event search offering | {{site.data.keyword.atracker_short}} | Events |
|-------------|--------------|------------------|-------------------|--------|
| | | | | |
{: caption="Table 1. List of analytics services" caption-side="top"}

## Classic services
{: #classic}

The following table lists services that send auditing events:

| Service     | CRN service name | {{site.data.keyword.at_short}} hosted event search offering | {{site.data.keyword.atracker_short}} | Events |
|-------------|--------------|------------------|-------------------|--------|
| | | | | |
{: caption="Table 2. List of classic services" caption-side="top"}



## Cloud Foundry applications
{: #platform_cfapps}

The events that are sent by Cloud Foundry applications to {{site.data.keyword.cloudaccesstrailshort}} are listed in the response area of the `GET /v2/events`, under the body section. The *Type* field lists all actions that generate an event. For more information, see the [Events API](https://apidocs.cloudfoundry.org/270/events/list_all_events.html){: external}.

## Compute serverless services
{: #serverless}

The following table lists serverless compute services that send auditing events:

| Service     | CRN service name | {{site.data.keyword.at_short}} hosted event search offering | {{site.data.keyword.atracker_short}} | Events |
|-------------|--------------|------------------|-------------------|--------|
| | | | | |
{: caption="Table 3. List of serverless compute services" caption-side="top"}



## Container services
{: #container}

The following table lists container platform services that send auditing events:

| Service     | CRN service name | {{site.data.keyword.at_short}} hosted event search offering | {{site.data.keyword.atracker_short}} | Events |
|-------------|--------------|------------------|-------------------|--------|
| | | | | |
{: caption="Table 4. Container events" caption-side="top"}

`[*]` {{site.data.keyword.registrylong_notm}} generates also global registry events that are available in the region that you configure to collect global auditing events in your account.


## Database services
{: #database}

The following table lists database services that send auditing events:

| Service     | CRN service name | {{site.data.keyword.at_short}} hosted event search offering | {{site.data.keyword.atracker_short}} | Events |
|-------------|--------------|------------------|-------------------|--------|
| | | | | |
{: caption="Table 5. List of database services" caption-side="top"}

`[*]` - Events provided by the BSS service.

## Developer tools
{: #devops}

The following table lists developer tools and DevOps services that send auditing events:

| Service     | CRN service name | {{site.data.keyword.at_short}} hosted event search offering | {{site.data.keyword.atracker_short}} | Events |
|-------------|--------------|------------------|-------------------|--------|
| [{{site.data.keyword.mobilepushfull}}](/docs/mobilepush?topic=mobilepush-getting-started) | `imfpush` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") |  | [Location-based events](/docs/mobilepush?topic=mobilepush-at_events#at_actions) |
{: caption="Table 6. List of developer tools services" caption-side="top"}


The following table lists {{site.data.keyword.contdelivery_full}} services that send auditing events:

| Service     | CRN service name | {{site.data.keyword.at_short}} hosted event search offering | {{site.data.keyword.atracker_short}} | Events |
|-------------|--------------|------------------|-------------------|--------|
| | | | | |
{: caption="Table 7. List of developer tools services" caption-side="top"}



## Integration services
{: #integration}

The following table lists integration services that send auditing events:

| Service     | CRN service name | {{site.data.keyword.at_short}} hosted event search offering | {{site.data.keyword.atracker_short}} | Events |
|-------------|--------------|------------------|-------------------|--------|
| | | | | |
{: caption="Table 8. List of integration Cloud services" caption-side="top"}



## Network services
{: #network}

The following table lists network services that send auditing events:

| Service     | CRN service name | {{site.data.keyword.at_short}} hosted event search offering | {{site.data.keyword.atracker_short}} | Events |
|-------------|--------------|------------------|-------------------|--------|
| | | | | |
{: caption="Table 9. List of network services" caption-side="top"}

## Observability services
{: #observability}

The following table lists observability services that send auditing events:

| Service     | CRN service name | {{site.data.keyword.at_short}} hosted event search offering | {{site.data.keyword.atracker_short}} | Events |
|-------------|--------------|------------------|-------------------|--------|
| | | | | |
{: caption="Table 10. List of observability services" caption-side="top"}


## Platform services
{: #platform_core_integrated}

The following table lists platform services that send auditing events:

| Service     | CRN service name | {{site.data.keyword.at_short}} hosted event search offering | {{site.data.keyword.atracker_short}} | Events |
|-------------|--------------|------------------|-------------------|--------|
| | | | | |
{: caption="Table 11. List of platform services" caption-side="top"}

For example, the following table lists core security actions that send events to {{site.data.keyword.at_full_notm}}:

| Service     | {{site.data.keyword.at_short}} hosted event search offering | {{site.data.keyword.atracker_short}} | Events |
|-------------|------------------|-------------------|--------|
| | | | | |
{: caption="Table 12. List of core security platform services" caption-side="top"}

## Security services
{: #security}

The following table lists security Cloud services that send auditing events:


| Service     | CRN service name | {{site.data.keyword.at_short}} hosted event search offering | {{site.data.keyword.atracker_short}} | Events |
|-------------|--------------|------------------|-------------------|--------|
| | | | | |
{: caption="Table 13. List of security services" caption-side="top"}



## Storage services
{: #storage}


The following table lists storage services that send auditing events:

| Service     | CRN service name | {{site.data.keyword.at_short}} hosted event search offering | {{site.data.keyword.atracker_short}} | Events |
|-------------|--------------|------------------|-------------------|--------|
| | | | | |
{: caption="Table 14. List of storage events" caption-side="top"}


`[*]` {{site.data.keyword.cos_full_notm}} (COS) generates global, and location-based events.
* By default, bucket management events such as the creation of a bucket are collected automatically.
* Collection of data events in your account is optional. You must configure each bucket to enable data events by selecting the option **Track data events**.
* {{site.data.keyword.mdms_short}} generates global events only, for each transition of the order state.


## VMware Solutions
{: #vmware_solutions}

With {{site.data.keyword.vmwaresolutions_full_notm}}, you can quickly and seamlessly integrate or migrate your on-premises VMware workloads to the {{site.data.keyword.cloud_notm}} by using the scalable, secure, and high-performance {{site.data.keyword.cloud_notm}} infrastructure and the industry-leading VMware hybrid virtualization technology. You can easily deploy your VMware virtual environments and manage the infrastructure resources on {{site.data.keyword.cloud_notm}}. At the same time, you can still use your familiar native VMware product console to manage the VMware workloads. [Learn more](https://www.ibm.com/products/vmware){: external}.

The following table lists VMware solution services that send auditing events:

| Service     | CRN service name | {{site.data.keyword.at_short}} hosted event search offering | {{site.data.keyword.atracker_short}} | Events |
|-------------|--------------|------------------|-------------------|--------|
| | | | | |
{: caption="Table 15. List of VMware solution services" caption-side="top"}




## VPC services
{: #vpc_services}

You can provision a Virtual Private Cloud (VPC) in the {{site.data.keyword.cloud_notm}} to run an isolated environment within the public cloud. VPC gives you the security of a private cloud, with the agility and ease of a public cloud. See [{{site.data.keyword.vpc_full}} Gen 2](/docs/vpc?topic=vpc-getting-started).


The following table lists VPC infrastructure services that send auditing events:

| Service     | Service name | {{site.data.keyword.at_short}} hosted event search offering | {{site.data.keyword.atracker_short}} | Events |
|-------------|--------------|------------------|-------------------|--------|
| | | | | |
{: caption="Table 16. List of VPC infrastructure services (generation 2)" caption-side="top"}

## Watson AI
{: #watson_ai}

The following table lists Watson AI services that send auditing events:

| Service     | CRN service name | {{site.data.keyword.at_short}} hosted event search offering | {{site.data.keyword.atracker_short}} | Events |
|-------------|--------------|------------------|-------------------|--------|
| [{{site.data.keyword.cncfull}}](/docs/compare-comply?topic=compare-comply-about)  | `compare-comply` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/compare-comply?topic=compare-comply-at_events) |
| [{{site.data.keyword.nlclassifierfull}}](/docs/natural-language-classifier?topic=natural-language-classifier-natural-language-classifier) | `natural-language-classifier` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/natural-language-classifier?topic=natural-language-classifier-at_events) |
| [{{site.data.keyword.visualrecognitionfull}}](/docs/visual-recognition?topic=visual-recognition-index) | `watson-vision-combined` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | [Location-based events](/docs/visual-recognition?topic=visual-recognition-at_events) |
| [{{site.data.keyword.wh-acd_full}}](/docs/wh-acd?topic=wh-acd-getting-started) | `wh-acd` | ![Checkmark](/images/checkmark-icon.svg "Checkmark") | | [Location-based events](/docs/wh-acd?topic=wh-acd-at_events) |
{: caption="Table 17. List of Watson AI services" caption-side="top"}

## Web and mobile services
{: #web}

The following table lists web and mobile services that send auditing events:

| Service     | CRN service name | {{site.data.keyword.at_short}} hosted event search offering | {{site.data.keyword.atracker_short}} | Events |
|-------------|--------------|------------------|-------------------|--------|
| | | | | |
{: caption="Table 17. List of web and mobile events" caption-side="top"}



## Power IaaS services
{: #power_iaas_services}

Power Systems Virtual Server (PowerVS) projects deliver flexible compute capacity for Power Systems workloads. Integrated with the {{site.data.keyword.cloud_notm}} platform for on-demand provisioning, this offering provides a secure and scalable server virtualization environment that is built upon the advanced RAS features and leading performance of the Power Systems™ platform. See [{{site.data.keyword.powerSysFull}}](/docs/power-iaas?topic=power-iaas-getting-started).


The following table lists Power IaaS infrastructure services that send auditing events:

| Service     | Service name | {{site.data.keyword.at_short}} hosted event search offering | {{site.data.keyword.atracker_short}} | Events |
|-------------|--------------|------------------|-------------------|--------|
| | | | | |
{: caption="Table 18. List of Power Systems Virtual Server infrastructure services" caption-side="top"}
