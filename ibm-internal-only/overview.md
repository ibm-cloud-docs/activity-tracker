---

copyright:
  years: 2018
lastupdated: "2018-11-29"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# Overview
{: #ibm_ov}

Access Trail provides logging and monitoring functions for API calls
to Bluemix services. You can use Access Trail to monitor for abnormal
activity, and comply with regulatory audit requirements.
{:shortdesc}


You can set the level of detail that is displayed in the logs, and
then search, view, and export the log output. The information that is
stored complies with the Cloud Auditing Data Federation (CADF)
standard.

Access Trail events are stored in the Logging service (Logmet).

**Note:** Logmet is an Alchemy cloud service that allows you to
monitor logs & metrics produced by your application. You forward your
logs and/or metrics to Logmet, and they will be available to search
and visualize. For more information, see
[Logmet Service](https://pages.github.ibm.com/alchemy-logmet).

The scope of the Access Trail service is a space in a Bluemix
organization.

You can visualize and analyze events for a space in Bluemix in a
Kibana dashboard. Access Trail provides a default Kibana dashboard
that you can access through the Bluemix UI or through a web
browser. The following table lists the URLs that you can launch from a
web browser and are supported by the Access Trail service:

| Location          | Logging service (Logmet) Url                            |
|-------------------|---------------------------------------|
| Dallas Stage1     | https://logmet.stage1.ng.bluemix.net |
| Dallas Production | https://logmet.ng.bluemix.net        |
| London Production | https://logmet.eu-gb.bluemix.net     |

**Note:** You log in to Logmet with your Bluemix ID.

## Access Trail users

An upstream service provider can integrate with Access Trail in 2 ways:

* Sending the API logs to Access Trail by using the Access Trail REST API
* Having the upstream service proxied by Access Trail 

Access Trail has two types of users:

1. [Upstream service providers (internal users)](#upstream-service-providers)
2. [End users (Bluemix users)](#end-users)


### Upstream Service Providers

There are two ways for an upstream service to work with Access Trail:

1. Integration: The upstream service integrates with the Access Trail
   Service.
   
2. Distribution: The upstream service sends events to the Access Trail
   service.

Both ways store Access Trail Events in the Logging service (Logmet).

**Note:** Logmet is an Alchemy cloud service that allows you to
monitor logs & metrics produced by your application. You forward your
logs and/or metrics to Logmet, and they will be available to search
and visualize. For more information, see
[Logging Service](https://pages.github.ibm.com/alchemy-logging).

When the upstream service integrates with Access Trail, the following
features are also available:

1. Metrics for the upstream service, such as request/response time,
   and requests per minute.

    These metrics are collected and stored in the Logging service
    (Logmet).
   
2. Support for rate limits.

    Rate limit of the API is described per user access token. If a
    method allows for 5 requests per rate limit window, then it allows
    5 requests per window per access token.

3. Request/response header transform


### End Users 

End users are Bluemix users.

Bluemix users can:

1. Provision the Access Trail service in a space of a BLuemix
   organization.
2. Enable or disable logging for a space of a Bluemix organization.
2. Visualize and analyse events in the default Kibana dashboard that
   the Access Trail service provides.
3. Customize Kibana dashboards to analyze events.
