---

copyright:
  years: 2019
lastupdated: "2019-01-16"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}

# Enabling Super Tenancy
{: #enable_st}

**Super Tenancy on LogDNA is not working yet**, but expected soon. This document is a preview of how services will onboard once it is working.

## Background
{: #background}

LogDNA supports two related capabilities: Super Tenancy and Activity Tracking.

* *Super Tenancy* (ST) is a capability of logging. A "super tenant" can store log lines to other tenants as well as itself. As a super tenant, your service will still have its own instance of Log Analysis with LogDNA for saving its operational log lines. But it also has the ability to save its log lines in the LogDNA instances of your customers.

* *Activity Tracker with LogDNA* (AT) is a special LogDNA instance that allows your customers to see their activities on your service. Your service will have its own instance of AT for saving its AT log lines, which are called *events*. But since AT is a super tenant, your service can also save its events in the AT instances of your customers.

This page tells how to enable Super Tenancy. If you are enabling Activity Tracker, you must first enable Super Tenancy because AT is now a layer on top of ST. So first complete the instructions on this page, and then follow the link for step 5 to set up Activity Tracker.

## Overview
{: #overview}

An IBM service must complete the following steps to begin using super tenancy (ST).

1. [Provision a Super Tenant Sender](/docs/services/Activity-Tracker-with-LogDNA/ibm-internal-only/enable-ST.html#provision)
2. [Get the STS ingestion key](/docs/services/Activity-Tracker-with-LogDNA/ibm-internal-only/enable-ST.html#ingestion_key)
3. [Install LogDNA Agent on Kubernetes](/docs/services/Activity-Tracker-with-LogDNA/ibm-internal-only/enable-ST.html#kube_agent)
4. [Test your service's Super Tenancy](/docs/services/Activity-Tracker-with-LogDNA/ibm-internal-only/enable-ST.html#test)
5. [Set up Activity Tracker](/docs/services/Activity-Tracker-with-LogDNA/ibm-internal-only/enable-AT.html#enable_at) if applicable
6. [Other Considerations](/docs/services/Activity-Tracker-with-LogDNA/ibm-internal-only/enable-ST.html#considerations)
    * [Root Access on Kubernetes](/docs/services/Activity-Tracker-with-LogDNA/ibm-internal-only/enable-ST.html#kube_root)
    * [Not on Kubernetes?](/docs/services/Activity-Tracker-with-LogDNA/ibm-internal-only/enable-ST.html#not_kube)
    * [Precautions](docs/services/Activity-Tracker-with-LogDNA/ibm-internal-only/enable-ST.html#precautions)
    * [Continuous Automated Tests](/docs/services/Activity-Tracker-with-LogDNA/ibm-internal-only/enable-ST.html#automated_tests)

In addition to the above, your service must write super tenant log lines in JSON, using the `logSourceCRN` field and (optionally) the `saveServiceCopy` field as described in step 4. Otherwise, they will be handled as normal log lines. 

## Before you start
{: #before}

- Get a "provision key" from LogDNA. **TODO: give the IBM contact.** **NOTE: The provision key is not required on staging yet; just leave it out of the commands until it is required.**
- Have the IBM Cloud command line installed.
- Be logged into your service's account, or a test account in staging if you are just trying it out. 

These instructions assume you are working in staging, e.g. `test.cloud.ibm.com`. For production, adjust the endpoints accordingly.

## 1. Provision a Super Tenant Sender
{: #provision}

A Super Tenant Sender (STS) is a LogDNA instance that is configured to detect and handle super tenant log lines. This means it can save a copy of your service's log line to a customer's logging instance. You will need to create the STS LogDNA instance from the command line in order to pass in the required parameters.

Create your STS with the following command:

```
ibmcloud resource service-instance-create myService-STS logdna 7-day us-south \
    -p '{"service_supertenant": "name-of-your-service" , "provision_key": "123"}'
```
{: codeblock}

Where:  
* `myService-STS` is whatever you call your service, with STS ("super tenant sender") appended by convention.
* `7-day` is the plan, which could also be `lite`, `14-day` or `30-day`, your choice.
* `name-of-your-service` is the CRN service-name of your service.
* `provision_key` is a key IBM gets from LogDNA which expires frequently. Get this key from ___. **TODO: say who.** You will only use this key for the `service-instance-create` commands in the ST and AT instructions.

## 2. Get the STS ingestion key
{: #ingestion_key}

To send log lines to the STS, you need its ingestion key.
1. Log into the IBM Cloud Console.
1. Open the hamburger menu on the top left.
1. Select Observability.
1. Select Logging. 
1. You should see your new STS; it is just a LogDNA instance. You can click "View ingestion key" to copy its ingestion key.

![Observability/Logging](images/STS-STR.png)

(If the "View ingestion key" UI is not working, as an alternative click "View LogDNA". Inside LogDNA, click the gear on the left, click "Organization", and click "API Keys".)

## 3. Install LogDNA Agent on Kubernetes
{: #kube_agent}

If your service is running on Kubernetes, then follow [these instructions](https://docs.logdna.com/docs/kubernetes) to install the Kubernetes agent, while observing the following:

- The LogDNA Agent version must be 1.5.6 or later. If you are already running an older version, be sure to update it.
- Use your service's STS ingestion key.
- Download the `logdna-agent-ds.yaml` file before using it. Edit it to add to `spec.template.spec.containers.env` the following:

```
        - name: LDLOGPATH
          value: /supertenant/logs/ingest
```
{: codeblock}

When the agent is deployed, it will send your service's logs to LogDNA from `stdout` and `/var/log/*`. However, it has these new features:

* Whenever a JSON log line contains the `logSourceCRN` field, LogDNA will save a copy of the line to the logging instance in the account indicated in `logSourceCRN`.
* Whenever a JSON log line contains the `saveServiceCopy` field set to `false`, then it will not save a copy to your service's STS.

These features are illustrated by the green lines in the following diagram:

![ST complete](images/ST-instructions.png)

The customer's perspective is in yellow at the bottom. Customers save their own log lines in their LogDNA instance (Customer Logging Instance), and the service's super tenant lines are also saved there.

If your service was already using LogDNA before enabling Super Tenancy, then the new STS has replaced your service's old LogDNA instance. The old LogDNA instance will no longer receive logs from the Kubernetes cluster. You can keep it around while its existing logs are retained, and then delete it.

## 4. Test your service's Super Tenancy
{: #test}

First, ensure that the STS is receiving the logs from your service. In the diagram above, this is the green line that goes straight across from "My Service" to "Logs".

1. In Observability > Logging, click "View LogDNA" for your STS.
2. You should see the log lines that your service writes to `stdout` or to files in `/var/log`.

Now test super tenancy. In the diagram, this is the green line that runs from MyService-STS to the customer's logging instance.

1. Switch to a different account for testing as a customer.
2. Provision an instance of your service from the ibmcloud catalog. (This is "MyServiceInstance" in the diagram.)
3. Get the CRN of your service instance. Run the command `ibmcloud resource service-instance MyServiceInstance` (but use the name of your own service instance), and save the CRN.
4. Provision an instance of "Log Analysis with LogDNA" in the same account. Do this in the IBM Cloud console, not the CLI. Let us call it "Customer-Logging_Instance" **Temporary work-around: instead of console, use this CLI: `ibmcloud resource service-instance-create Customer-Logging-Instance logdna 7-day us-south -p '{"default_receiver": true}'`**
5. Switch back to your service's account.
6. Write a line to a log file in your service's cluster (e.g. `/var/log/test.log`) that looks like this: <br>`
{"message":"This test log statement should be in STS and in Customer-Logging_Instance","saveServiceCopy":true,"logSourceCRN":"PUT YOUR SERVICE INSTANCE CRN HERE"}`
7. Look in your STS LogDNA again, and verify that the line came through. Click on the left of the line to expand it.
8. Now go back to the customer account where your service instance is provisioned, and look at that LogDNA instance. You should also see the line there.
9. As a further test, add `"saveServiceCopy":false` to the line, and verify that it *only* is saved for the customer, and not in your service's STS.

## 5. Set up Activity Tracker
{: #setup}

Follow [these instructions](/docs/services/Activity-Tracker-with-LogDNA/ibm-internal-only/enable-AT.html#enable_at) to add Activity Tracker to your service.

## 6. Other Considerations
{: #considerations}

These considerations relate to both ST and AT. If you are only using ST or only using AT, you can ignore the content that doesn't apply.

### Root Access on Kubernetes
{: #root_access}

For a service using Activity Tracker on Kubernetes, the best practice is for the service to write the AT events to a host-mounted volume on the worker node. The service writes to a log file in `/var/log/at`, and an agent reads the events and sends them to AT. In the case of an outage in nearly any part of the system, the AT events will be preserved in the log file and processed when the outage is resolved. This design works for the legacy AT with a fluentd output plugin, and the LogDNA AT with the LogDNA agent.

Unfortunately, this solution requires writing as root to `/var/log/at`, since Kubernetes creates the mount path on the worker as root. To avoid writing as root, create an initContainer that runs as root to change the permissions of the directory. See https://pages.github.ibm.com/activity-tracker/getting-start/kube/#init-containers for more details on setting up an init container to do this.

Another alternative is for the service to call the AT API to send the AT events. LogDNA has an ingestion API, as does the legacy AT service. However, there is a requirement for the service to persist the AT events in the case of any lengthy outage. Therefore, the service should not call the API directly from its code, relying on a memory buffer to queue the events. The service would need to save the events persistently while they are waiting to be sent to AT, which leads back to the same problem.

AT considered the option of sending through `stdout` along with the normal log lines. There are several problems with this, one of which is that the container logs are not persisted past the destruction of the container.

### Not on Kubernetes?
{: #not_kube}

The ST/AT design is optimized for Kubernetes. If you are one of the few unlucky engineers with a service that is not on Kubernetes, then consider the following remedies.

1. Migrate your service to Kubernetes.

2. If you can't do #1 right now, then create a way for your service to use the [LogDNA agent](https://docs.logdna.com/docs/logdna-agent) to get the same advantages. Apart from Kubernetes, the LogDNA agent will still read from log files and support ST/AT in the same way. 
    - Be sure to use `/var/log/at` for your AT logs.
    - When setting up your agent, observe the Kubernetes notes above regarding version, ingestion key, and `LDLOGPATH`.

3. As a last resort, you can use the [LogDNA ingestion API](https://docs.logdna.com/v1.0/reference#api).
    - LogDNA has code libraries in most common languages for using the API. See [here](https://docs.logdna.com/docs), under "Code Libraries" on the left.
        - Be cautious about the libs that are "unofficial". They are not supported by LogDNA.
        - If using one of these libs, consider isolating it in a separate process, similar to how the agent works, reading from a persisted buffer.
    - One pitfall is that you must manage the persistence of your logs and events. If you store your logs and events in memory, the data will be lost if your program crashes or LogDNA is not accessible for a period of time. This limitation is overcome in the agent approach because it stores the logs and events in a disk based file. The LogDNA agent will automatically send the saved data when conditions get corrected.
    - If using the API, you can send AT events directly to your ATS instead of going through the STS. 
        - To send AT events through the STS via API, you have to fake out the file path by adding `"app":"/var/log/at" to each event. You avoid this by sending directly to the ATS.
        - You will need to get the ATS ingestion key from inside the LogDNA UI, since it is not available on the IBM Cloud Console.
        - If you are only using AT, and sending events directly to the ATS, the STS must still be provisioned, and the ATS must be linked to it. This is a design limitation of LogDNA. **TODO: confirm this is still the case.**

### Precautions
{: #precautions}

Now your service has the power to write log lines to any account in its region. With great power comes great responsibility...
- Your service's STS ingestion key is an important secret, so be sure your service manages it accordingly. For example, don't hard-code it.
- If you think your service's STS ingestion key may have been compromised, then generate a new key in LogDNA, replace the old one with the new, and invalidate the old one ASAP. **TODO: Specific Kube instructions, e.g. whether to restart pods.**
- Do not send super tenant log lines unless you need to. **Most services do not need to send super tenant log lines.** If your service does not use super tenancy and only needs Activity Tracker, then ensure it never has a `logSourceCRN` field in logging. The `logSourceCRN` field triggers super tenant behavior.
- If your service sends log lines to customers via super tenancy, then the service's documentation should explain those lines **when you start sending them** or earlier.
- If your service is sending so many log lines, or such large log lines, that customers may be concerned about the cost, then add an option to control them. (However, note that the ST/AT service will be adding controls for this in the future.)
- Develop AT events privately (in staging or ATS only), and review with Marisa/Architect Board before sending in production. Malformed events can break AT event consumers like QRadar, Security Advisor, and custom tools by IBM customers such as Caterpillar. Use the [event linter](https://github.ibm.com/activity-tracker/helloATv2#at-event-linter) to help ensure valid events.

### Continuous Automated Tests
{: #automated_tests}

If your service stops storing ST lines or AT events successfully, it should trigger a PagerDuty incident for your service. Here are some guidelines for setting up an automated test for this. The guidelines are written with AT in mind, but also apply to ST.

The automated test should cover the complete path that an AT event takes. Even though your automated test could use the ingestion API, it is better for the test data to come from your log files in `/var/log/at`.

The black-box approach is to create a test program that exercises your service:

1. The test program runs in its own "test account". In the test account, there is an instance of your service provisioned for the test program to use.
1. As the test runs, it exercises your service in some simple ways, causing your service to generate AT events--say, every minute.
1. In the test account, an Activity Tracker Receiver LogDNA instance is provisioned.
1. Your test program *could* test for AT events in the ATR using the [LogDNA export API](https://docs.logdna.com/v1.0/reference#api). However, LogDNA is soon adding "absence detection" and "anomaly detection" alerting. You will be able to trigger your PagerDuty from inside LogDNA if the events fail to show up. This is less work for you, and avoids pages resulting from LogDNA problems. **TODO: check the ETA for this feature**
1. The page occurs if events fail to appear after, say, 10 minutes. Adjust the interval based on experience with latency.

If you are already running a test program similar to the above, then you may only need to add steps 3 and 4.

This is a general design for generating AT events from outside your service, and then evaluating the events outside your service. Consider expanding this test to include more AT events and scenarios, so that you get more value out of the test.
