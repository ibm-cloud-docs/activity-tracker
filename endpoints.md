---

copyright:
  years: 2019, 2022
lastupdated: "2022-03-22"

keywords: IBM Cloud, Activity Tracker, endpoints

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}

# Endpoints
{: #endpoints}

The following table lists the endpoints per region for the {{site.data.keyword.atracker_full}} service:
{: shortdesc}


## API endpoints for {{site.data.keyword.atracker_short}} Event Routing
{: #endpoints_api-atracker}

This information applies only to {{site.data.keyword.atracker_full_notm}} Event Routing.
{: important}

### Private API endpoints
{: #endpoints_api-atracker-private}

The following table shows the private API endpoints:

| Region                   | ATracker Private endpoint                         | Port         | IPs |
|--------------------------|---------------------------------------------------|--------------|-----|
| `Dallas (us-south)`      | `https://private.us-south.atracker.cloud.ibm.com` | `https/443`  | `166.9.58.136`   \n `166.9.51.140`   \n `166.9.48.211` |
| `Washington (us-east)`   | `https://private.us-east.atracker.cloud.ibm.com`  | `https/443`  | `166.9.24.96`   \n `166.9.22.84`   \n `166.9.20.212` |
| `Frankfurt (eu-de)`   | `https://private.eu-de.atracker.cloud.ibm.com`  | `https/443`  | `166.9.30.195`   \n `166.9.28.229`   \n `166.9.32.161` |
| `London (eu-gb)`   | `https://private.eu-gb.atracker.cloud.ibm.com`  | `https/443`  | `166.9.38.78`   \n `166.9.34.154`   \n `166.9.36.109` |
| `Sydney (au-syd)` | `https://private.au-syd.atracker.cloud.ibm.com` | `https/443` | `166.9.54.51`  \n `166.9.52.48`  \n `166.9.56.53` |
{: caption="Table 1. Lists of private API endpoints for interacting with {{site.data.keyword.atracker_full_notm}} Event Routing" caption-side="top"}

### Public API endpoints
{: #endpoints_api-atracker-public}

The following table shows the public API endpoints:

| Region                   | ATracker Public endpoint                         | Port         |
|--------------------------|---------------------------------------------------|--------------|
| `Dallas (us-south)`      | `https://us-south.atracker.cloud.ibm.com`         | `https/443`  |
| `Washington (us-east)`   | `https://us-east.atracker.cloud.ibm.com`          | `https/443`  |
| `Frankfurt (eu-de)`   | `https://eu-de.atracker.cloud.ibm.com`          | `https/443`  |
| `London (eu-gb)`   | `https://eu-gb.atracker.cloud.ibm.com`          | `https/443`  |
| `Sydney (au-syd)` | `https://au-syd.atracker.cloud.ibm.com` | `https/443`  |
{: caption="Table 2. Lists of public API endpoints for interacting with {{site.data.keyword.atracker_full_notm}} Event Routing" caption-side="top"}


## Endpoints for {{site.data.keyword.at_short}} hosted event search offerings
{: #endpoints_api-at}

This information applies only to {{site.data.keyword.at_full_notm}} hosted event search offerings.
{: important}

There are two types of Configuration API endpoints: public and private.

### Public API endpoints
{: #endpoints_api-at-public}

The following table shows the public API endpoints:

| Location                 | Region                   |  Public Endpoint                                   |
|--------------------------|--------------------------|----------------------------------------------------|
| `Asia Pacific`           | `Chennai (in-che)`       | `https://api.in-che.logging.cloud.ibm.com`         |
| `Asia Pacific`           | `Osaka (jp-osa)`         | `https://api.jp-osa.logging.cloud.ibm.com`         |
| `Asia Pacific`           | `Seoul (kr-seo)`         | `https://api.kr-seo.logging.cloud.ibm.com`         |
| `Asia Pacific`           | `Sydney (au-syd)`        | `https://api.au-syd.logging.cloud.ibm.com`         |
| `Asia Pacific`           | `Tokyo (jp-tok)`         | `https://api.jp-tok.logging.cloud.ibm.com`         |
| `North America`          | `Dallas (us-south)`      | `https://api.us-south.logging.cloud.ibm.com`       |
| `North America`          | `Washington DC (us-east)` | `https://api.us-east.logging.cloud.ibm.com`       |
| `North America`          | `Toronto (ca-tor)`       | `https://api.ca-tor.logging.cloud.ibm.com`       |
| `South America`          | `Sao Paulo (br-sao)`     | `https://api.br-sao.logging.cloud.ibm.com`       |
| `Europe`                 | `Frankfurt (eu-de)`      | `https://api.eu-de.logging.cloud.ibm.com`          |
| `Europe`                 | `London (eu-gb)`         | `https://api.eu-gb.logging.cloud.ibm.com`          |
{: caption="Table 1. Public API endpoints" caption-side="top"}

### Private API endpoints
{: #endpoints_api-at-private}

The following table shows the private API endpoints:

| Location                 | Region                   |  Public Endpoint                                   |
|--------------------------|--------------------------|----------------------------------------------------|
| `Asia Pacific`           | `Chennai (in-che)`       | `https://api.private.in-che.logging.cloud.ibm.com`       |
| `Asia Pacific`           | `Osaka (jp-osa)`         | `https://api.private.jp-osa.logging.cloud.ibm.com`         |
| `Asia Pacific`           | `Seoul (kr-seo)`         | `https://api.private.kr-seo.logging.cloud.ibm.com`         |
| `Asia Pacific`           | `Sydney (au-syd)`        | `https://api.private.au-syd.logging.cloud.ibm.com`         |
| `Asia Pacific`           | `Tokyo (jp-tok)`         | `https://api.private.jp-tok.logging.cloud.ibm.com`         |
| `North America`          | `Dallas (us-south)`      | `https://api.private.us-south.logging.cloud.ibm.com`       |
| `North America`          | `Washington DC (us-east)`   | `https://api.private.us-east.logging.cloud.ibm.com`         |
| `North America`          | `Toronto (ca-tor)`       | `https://api.private.ca-tor.logging.cloud.ibm.com`         |
| `South America`          | `Sao Paulo (br-sao)`     | `https://api.private.br-sao.logging.cloud.ibm.com`       |
| `Europe`                 | `Frankfurt (eu-de)`      | `https://api.private.eu-de.logging.cloud.ibm.com`          |
| `Europe`                 | `London (eu-gb)`         | `https://api.private.eu-gb.logging.cloud.ibm.com`          |
{: caption="Table 2. Private API endpoints" caption-side="top"}


### UI endpoints
{: #endpoints_api-at-ui}

The following table shows the UI endpoints:

| Location                 | Region                   |  Public Endpoint                                   |
|--------------------------|--------------------------|----------------------------------------------------|
| `Asia Pacific`           | `Chennai (in-che)`       | `https://app.in-che.logging.cloud.ibm.com`       |
| `Asia Pacific`           | `Osaka (jp-osa)`         | `https://app.jp-osa.logging.cloud.ibm.com`         |
| `Asia Pacific`           | `Seoul (kr-seo)`         | `https://app.kr-seo.logging.cloud.ibm.com`         |
| `Asia Pacific`           | `Sydney (au-syd)`        | `https://app.au-syd.logging.cloud.ibm.com`         |
| `Asia Pacific`           | `Tokyo (jp-tok)`         | `https://app.jp-tok.logging.cloud.ibm.com`         |
| `North America`          | `Dallas (us-south)`      | `https://app.us-south.logging.cloud.ibm.com`       |
| `North America`          | `Washington DC (us-east)`   | `https://app.us-east.logging.cloud.ibm.com`        |
| `North America`          | `Toronto (ca-tor)`       | `https://app.ca-tor.logging.cloud.ibm.com`        |
| `South America`          | `Sao Paulo (br-sao)`     | `https://app.br-sao.logging.cloud.ibm.com`       |
| `Europe`                 | `Frankfurt (eu-de)`      | `https://app.eu-de.logging.cloud.ibm.com`         |
| `Europe`                 | `London (eu-gb)`         | `https://app.eu-gb.logging.cloud.ibm.com`         |
{: caption="Table 3. Lists of UI endpoints" caption-side="top"}

