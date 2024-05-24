---

copyright:
  years: 2019, 2024
lastupdated: "2024-05-24"

keywords:

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}


# Service IP changes
{: #service-ip-changes}

Due to maintenance, {{site.data.keyword.at_full}} makes changes periodically to service IPs in some regions. You might need to take action to continue using the service.
{: shortdesc}

<!-- Common deprecation statement -->
{{../log-analysis/_include-segments/deprecation_notice.md}}

Endpoints and regions that are not listed are unchanged.
{: note}

If you are using private endpoints, there are no user-required tasks. Private endpoints have not changed.
{: important}

## After 26 September 2023
{: #endpoint-changes-26Sep2023}

The following endpoints will be changing after 26 September 2023. 

### Madrid (eu-es)
{: #092ß623_eues}

This is a newly opened region.
{: note}

* `api.eu-es.logging.cloud.ibm.com`
* `api.private.eu-es.logging.cloud.ibm.com`
* `logs.eu-es.logging.cloud.ibm.com`
* `logs.private.eu-es.logging.cloud.ibm.com`
* `app.eu-es.logging.cloud.ibm.com`
* `syslog-a.eu-es.logging.cloud.ibm.com`
* `syslog-a.private.eu-es.logging.cloud.ibm.com`
* `syslog-u.eu-es.logging.cloud.ibm.com`
* `syslog-u.private.eu-es.logging.cloud.ibm.com`

## 28 May 2021 changes
{: #service-ip-changes-28May2021}

The following changes were made:

### London (eu-gb)
{: #service-ip-changes-london}

| London IP addresses                                    | Original IP addresses                                      | New IP addresses |
|----------------------------------------------------|-----------------------------------------------------------|-------------------------------------------|
| `api.eu-gb.logging.cloud.ibm.com`                  | 158.176.135.132   \n 158.175.82.238   \n 141.125.78.213   | 158.175.113.20   \n 158.176.163.154   \n 141.125.140.100 |
| `api.private.eu-gb.logging.cloud.ibm.com`          | 166.9.36.2   \n 166.9.38.4   \n 166.9.34.2                | No change |
{: caption="Table 1. IP changes in EU-GB" caption-side="top"}

### Dallas (us-south)
{: #service-ip-changes-dallas}

| Dallas IP addresses                                     | Original IP addresses                                      | New IP addresses  |
|-------------------------------------------------------|-----------------------------------------------------------|-------------------------------------------|
| `api.us-south.logging.cloud.ibm.com`                  | 169.47.224.74   \n 169.60.166.44   \n 169.48.237.109      | 169.61.197.85   \n 50.22.153.156   \n 67.228.211.4 |
| `api.private.us-south.logging.cloud.ibm.com`          | 166.9.16.11   \n 166.9.12.12   \n 166.9.14.2              | No change |
{: caption="Table 2. IP changes in  US-South" caption-side="top"}




### Frankfurt (eu-de)
{: #service-ip-changes-frankfurt}

| Frankfurt IP addresses                                 | Original IP addresses                                      | New IP addresses  |
|----------------------------------------------------|-----------------------------------------------------------|-------------------------------------------|
| `api.eu-de.logging.cloud.ibm.com`                  | 149.81.86.66   \n 161.156.89.12   \n 158.177.129.34       | 158.177.157.69   \n 161.156.6.180   \n 149.81.108.27 |
| `api.private.eu-de.logging.cloud.ibm.com`          | 166.9.32.7   \n 166.9.28.2                                | No change |
{: caption="Table 3. IP changes in EU-DE" caption-side="top"}



## User-required tasks
{: #service-ip-changes-tasks}

If you are using public endpoints, you must complete the following tasks:

### Reconfigure your firewalls to the new IPs
{: #service-ip-changes-tasks-1}

If you have firewalls set up on the public or private network in your {{site.data.keyword.cloud_notm}} infrastructure account, you need to allow traffic to and from the {{site.data.keyword.at_full_notm}} service. You must allow traffic on TCP port 443 and TCP port 80 in your firewall for the API endpoints and the ingestion endpoints. Check that valid IPs are configured per region where you operate. For a list of valid IPs, see [IP changes by region](/docs/activity-tracker?topic=activity-tracker-service-ip-changes#service-ip-changes-ips).

### Reconfigure applications and services
{: #service-ip-changes-tasks-2}

If you have applications and services that restrict connectivity to specific IPs and communicate with the {{site.data.keyword.at_short}} service, make sure the new IPs are configured to avoid interruption of the logging service.
