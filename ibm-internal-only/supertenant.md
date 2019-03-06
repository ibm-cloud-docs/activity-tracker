---

copyright:
  years: 2019
lastupdated: "2019-03-06"

keywords: IBM Cloud, LogDNA, Activity Tracker, super tenant

subcollection: logdnaat

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# LogDNA News for Super Tenants
{: #ibm_partner_supertenant}

All services are moving from Log Analysis to [LogDNA](https://docs.logdna.com/docs) for operational logs.
{:shortdesc}


These instructions are for services that currently send super tenant logs to Log Analysis. A *super tenant log* is a log line that is copied to a customer's logging instance. There are about 15 services that do this--Cloud Foundry, Armada, and Message Hub, to name a few. These instructions do NOT pertain to Activity Tracker. However, AT is based on Super Tenant architecture, so the JSON fields are the same, and services can use a single agent instance for both AT and Super Tenant logs.

The Super Tenant functionality will be available on LogDNA as early as October 2018. With LogDNA, the service will send super tenant logs via the same agent/library/API that it uses for normal operational logs. However, the service's account must be enabled for super tenancy. Super tenant log lines must be JSON, and will be distinguished by a special JSON field, `logSourceCRN`.

## Super Tenant Log Lines
{: #loglines}

A super tenant log line must be in JSON. (Other log lines do not have to be in JSON.) The format of a super tenant line is:

```javascript
{
   "logSourceCRN": "crn:v1:bluemix:public:cloud-object-storage:global:
       a/8131c65c6ad70bdc209bb564997a5f1c:8424aaea-ddcf-4dfe-ae90-1a4b89e07b86::", // REQUIRED
   "saveServiceCopy": true, // optional
   "message": "Summary of log line", // optional
   // Additional JSON fields for your existing log line content...
}
```
{: codeblock}

With the line in JSON, there are three special fields to be aware of:

1. The line **must** have a JSON field called `logSourceCRN`. This field gives the CRN of your service instance that is producing the log. 
  * The `logSourceCRN` field is what triggers the super tenant feature. 
  * LogDNA uses `logSourceCRN` to determine what LogDNA instance to save the customer's copy of the log line. 
  * The `logSourceCRN` must have the customer's account in the scope segment--not a Cloud Foundry space. The other CRN segments are used as normal; the instance segment (after the scope) should be provided if applicable.
2. Optionally, the log line can include the `saveServiceCopy` field. This field defaults to `true`, so that a copy of the line is saved in both the service's and customer's LogDNA instances.  If saveServiceCopy is `false`, then only the customer gets a copy.
3. For all JSON log lines, super tenant or otherwise, be aware that LogDNA uses the `message` field to show a human-readable summary of the log line. If no `message` field is given, then it shows the entire line. But if there is a `message` field, it only displays that field. The user sees the rest of the log line by clicking to expand it. 
  * This is a nice feature for your service to use, but don't use it by accident.
  * If your super tenant line is not already in JSON, one easy way to convert it is by putting the entire line in the `message` field. Then the entire line will show up in the LogDNA UI.

## Approximate Timeline
{: #timeline}

**Now**

You can convert your service's super tenant log lines to the above format, while still using Log Analysis.

LogDNA will be available inside the IBM Cloud. You can create a LogDNA account for your service, and begin sending its operational logs to LogDNA.
* If your service is running in Armada, use the [LogDNA Kubernetes agent](https://docs.logdna.com/docs/kubernetes), which is easy to set up and also works for AT.
* Otherwise, LogDNA offers many convenient methods of log ingestion--agents, libraries, and direct to API.  All of these will work for a super tenant account. Refer to [LogDNA docs](https://docs.logdna.com/docs) for details.
* Continue sending to Log Analysis at the same time--at least for your super tenant logs.


**End of January** 

LogDNA will add Super Tenant capability.
* Your service will then need a Super Tenant account (hopefully you can convert your existing LogDNA account, or else make a new one).
* As an implementation detail, the IP address of the ingestion API will be different for a super tenant account. But the normal ingestion behavior will work the same.
* Your service will use the same super tenant account to send operation logs, super tenant logs, and Activity Tracker events. If using a LogDNA agent, you will only need one agent for all three purposes.
* Super tenancy will begin to work. However, continue to send to both Log Analysis and LogDNA until LA support is ended for super tenant services.
* Additional tip: Provide a [LogDNA tag](https://docs.logdna.com/docs/ingestion#section-tags) for your human-readable service name, as seen in the catalog. The LogDNA doc shows how to do this for various ingestion methods, but it typically involves a simple agent configuration. *[Armada example to be provided.]* This will make your service more visible to customers, so they will see all you are doing for them. Otherwise, your service will not stand out as your log lines are mingled with all the other services.
