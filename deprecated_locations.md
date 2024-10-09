---

copyright:
  years: 2019, 2024
lastupdated: "2024-05-24"

keywords:

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}

# Deprecated locations
{: #deprecated-locations}

Over time support for the {{site.data.keyword.at_full}} service might be deprecated in some regions. This topic documents the CIDR blocks and endpoints for deprecated regions.
{: shortdesc}


{{../log-analysis/_include-segments/deprecation_notice.md}}

## Deprecated regions
{: #deprecated-regions}

The following regions are deprecated for {{site.data.keyword.at_full_notm}} and should no longer be used:

* Seoul

## Deprecated CIDR blocks
{: #deprecated-cidr}

The following are the CIDR blocks for deprecated regions.

### Public CIDR blocks
{: #dep-cidr-public}

#### Seoul
{: #cidr_public_gen2_7}

| Region   | CIDR block |
|----------|------------|
| Seoul    | 169.56.86.240/28 |
| Seoul    | 169.56.111.128/27 |
{: caption="Seoul public CIDR blocks" caption-side="top"}

### Private CIDR blocks
{: #dep-cidr-private}

#### Seoul
{: #cidr_private_gen2_18}

| Region | CIDR block |
|--------|------------|
| Seoul	    | 10.178.139.64/26 |
{: caption="Seoul private CIDR blocks" caption-side="top"}

## Deprecated endpoints
{: #deprecated-endpoints}

The following are endpoints for deprecated regions.

### Public API endpoints
{: #endpoints_api-at-public}

The following table shows the deprecated public API endpoints:

| Location                 | Region                   |  Public Endpoint                                   |
|--------------------------|--------------------------|----------------------------------------------------|
| `Asia Pacific`           | `Seoul (kr-seo)`         | `https://api.kr-seo.logging.cloud.ibm.com`         |    |
{: caption="Deprecated public API endpoints" caption-side="top"}

### Private API endpoints
{: #endpoints_api-at-private}

The following table shows the deprecated private API endpoints:

| Location                 | Region                   |  Public Endpoint                                   |
|--------------------------|--------------------------|----------------------------------------------------|
| `Asia Pacific`           | `Seoul (kr-seo)`         | `https://api.private.kr-seo.logging.cloud.ibm.com`         |
{: caption="Deprecated private API endpoints" caption-side="top"}


### UI endpoints
{: #endpoints_api-at-ui}

The following table shows the deprecated UI endpoints:

| Location                 | Region                   |  Public Endpoint                                   |
|--------------------------|--------------------------|----------------------------------------------------|
| `Asia Pacific`           | `Seoul (kr-seo)`         | `https://app.kr-seo.logging.cloud.ibm.com`         |
{: caption="Deprecated UI endpoints" caption-side="top"}
