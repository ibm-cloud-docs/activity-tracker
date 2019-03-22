---

copyright:
  years: 2019
lastupdated: "2019-03-06"

keywords: IBM Cloud, LogDNA, Activity Tracker, enable super tenancy

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

# Enabling Super Tenancy and Activity Tracker
{: #enable_st}

## Overview
{: #overview}
Follow the steps on this page to enable Super Tenancy and Activity Tracker on your service. See [here](https://test.cloud.ibm.com/docs/services/Activity-Tracker-with-LogDNA/ibm-internal-only?topic=logdnaat-understand_st#understand_st) for architecture and other enablement considerations.

If you are enabling Activity Tracker, you must first enable Super Tenancy because AT is now a layer on top of ST. So first complete the Super Tenancy steps on this page, and then continue through the Activity Tracker steps.

1. [Provision a Super Tenant Sender](/docs/services/Activity-Tracker-with-LogDNA/ibm-internal-only/enable-ST.html#provision)
2. [Get the STS ingestion key](/docs/services/Activity-Tracker-with-LogDNA/ibm-internal-only/enable-ST.html#ingestion_key)
3. [Install LogDNA Agent on Kubernetes](/docs/services/Activity-Tracker-with-LogDNA/ibm-internal-only/enable-ST.html#kube_agent)
4. [Test your service's Super Tenancy](/docs/services/Activity-Tracker-with-LogDNA/ibm-internal-only/enable-ST.html#test) <br/><br/>Continue only if you are setting up Activity Tracker...
5. [Provision an Activity Tracker Sender](/docs/services/Activity-Tracker-with-LogDNA/ibm-internal-only/enable-ST.html#provision-at)
6. [Test your service's Activity Tracking](/docs/services/Activity-Tracker-with-LogDNA/ibm-internal-only/enable-ST.html#test-at)

<br/>
When you complete these steps, your service can use Super Tenancy and (if applicable) Activity Tracker. To use Super Tenancy, your service must write super tenant log lines in JSON, using the `logSourceCRN` field and (optionally) the `saveServiceCopy`. Otherwise, they will be handled as normal log lines. Similarly, to use Activity Tracking, your service must write Activity Tracker events using the `logSourceCRN` field and (optionally) the `saveServiceCopy` field. Otherwise, they will only be saved in your service's Activity Tracker instance. Read about the format of AT events [here](/docs/services/Activity-Tracker-with-LogDNA/ibm-internal-only/event_definition.html#ibm_event_fields), and the specific changes for LogDNA [here](/docs/services/Activity-Tracker-with-LogDNA/ibm-internal-only/partner_news.html#ibm_partner).

## Before you start
{: #before}

- Request a "provision key" for super tenancy by opening an issue [here](https://github.ibm.com/activity-tracker/customer-issues/issues/new?template=logdna_provision_key.md). This key is for _provisioning_ an ST or AT Sender, so that only service owners can do it. You will only use this key for the `service-instance-create` commands in the ST and AT instructions, and then you won't need it again.
- Have the IBM Cloud command line installed.
- Be logged into your service's account in production.

Even if you are running your service in staging, you should provision LogDNA in production. You can test your service's code in staging by writing to a LogDNA instance in production. While it is possible to use LogDNA in staging, it is not recommended due to whitelists and other complications that are caused by billing considerations.


## 1. Provision a Super Tenant Sender
{: #provision-st}

A Super Tenant Sender (STS) is a LogDNA instance that is configured to detect and handle super tenant log lines. This means it can save a copy of your service's log line to a customer's logging instance. You will need to create the STSender LogDNA instance from the command line in order to pass in the required parameters.

Create your STSender with the following command:

```
ibmcloud resource service-instance-create myService-STS logdna 7-day us-south \
    -p '{"service_supertenant": "name-of-your-service" , "provision_key": "123"}'
```
{: codeblock}

Where:  
* `myService-STS` is whatever you call your service, with STS ("super tenant sender") appended by convention.
* `7-day` is the plan, which could also be `lite`, `14-day` or `30-day`, your choice.
* `name-of-your-service` is the CRN service-name of your service.
* `provision_key` - see instructions above for obtaining this key.

## 2. Get the STSender ingestion key
{: #ingestion_key}

To send log lines to the STSender, you need its ingestion key. This key is used for sending logs to LogDNA, so your service will use it all the time. (It is different from the provision key, which was used in the previous step.)
1. Log into the IBM Cloud Console, using the same id as when you created the STSender above.
1. Open the hamburger menu on the top left.
1. Select Observability.
1. Select Logging. 
1. You should see your new STSender; it is just a LogDNA instance. Click the three-dot menu on the right-hand side, and select "View Key". Copy your ingestion key.

![Observability/Logging](images/getServiceKey.png)

(If the UI is not working for step 5, instead click "View LogDNA". Inside LogDNA, click the gear on the left, click "Organization", and click "API Keys".)

## 3. Install LogDNA Agent on Kubernetes
{: #kube_agent}

If your service is not running on Kubernetes, refer [here](https://test.cloud.ibm.com/docs/services/Activity-Tracker-with-LogDNA/ibm-internal-only?topic=logdnaat-understand_st#not_kube). Otherwise, install the logdna-agent on Kube by the following steps. These steps assume a clean install rather than an upgrade.

1. Using the STSender ingestion key that you got above:<br/> `kubectl create secret generic logdna-agent-key --from-literal=logdna-agent-key=<INGESTION KEY>`
2. Download <a href="images/logdna-agentv2-ds-us-south.yaml" download>logdna-agentv2-ds-us-south.yaml</a> and install it:<br/>`kubectl create -f logdna-agentv2-ds-us-south.yaml`<br/>Notes:
  * This installs v2 of the agent, which is required.
  * It sets `LDAPIHOST` and `LDLOGHOST` for `us-south`. Change it if you are deploying in other regions.
  * It sets `LDLOGPATH` to use the supertenant endpoint rather than the normal ingestion endpoint.
  * The v2 agent has a minor bug which you should keep in mind while testing ST and AT. If you create a new log file as you are writing to it, the initial write may not be sent until the next write occurs. So a test like `echo "wait for it" >>newFile.log` might require a second line to be written before the first one is sent. LogDNA is fixing this bug.

If your service is already sending data to the old Activity Tracker via fluentd, leave it alone. The fluentd design should continue to send AT data to the old AT until it is shut down.

## 4. Test your service's Super Tenancy
{: #test-st}

First, ensure that the STSender is receiving the logs from your service. In the diagram above, this is the green line that goes straight across from "My Service" to "Logs".

1. In Observability > Logging, click "View LogDNA" for your STSender.
2. You should see the log lines that your service writes to `stdout` or to files in `/var/log`.

Now test super tenancy. In the diagram, this is the green line that runs from MyService-STS to the customer's logging instance.

1. Switch to a different account for testing as a customer. (It is possible to use the same account for this test, but it makes the test less comprehensive.)
2. Provision an instance of your service from the ibmcloud catalog. (This is "MyServiceInstance" in the diagram.)
3. Get the CRN of your service instance. Run the command `ibmcloud resource service-instance MyServiceInstance` (but use the name of your own service instance), and save the CRN.
4. Provision an instance of "Log Analysis with LogDNA" in the same account. Do this in the IBM Cloud console, not the CLI. Let us call it "Customer-Logging_Instance" **Temporary work-around: instead of console, use this CLI: `ibmcloud resource service-instance-create Customer-Logging-Instance logdna 7-day us-south -p '{"default_receiver": true}'`**
5. Switch back to your service's account.
6. Write a line to a log file in your service's cluster (e.g. `/var/log/test.log`) that looks like this: <br>`
{"message":"This test log statement should be in STS and in Customer-Logging_Instance","saveServiceCopy":true,"logSourceCRN":"PUT YOUR SERVICE INSTANCE CRN HERE"}`. 
  * Your `logSourceCRN` must use an account id for the location--not a space id. So the CRN location will start with `a/`.
  * To write to a log file in your cluster, use `kubectl exec -it logdna-agent-name -- /bin/bash`. (Use `kubectl get pods` to get the actual name for `logdna-agent-name`.) Then `echo LOG-LINE-CONTENT >/var/log/test.log`.
7. Look in your STSender LogDNA again, and verify that the line came through. Click on the left of the line to expand it.
8. Now go back to the customer account where your service instance is provisioned, and look at that LogDNA instance. You should also see the line there.
9. As a further test, add `"saveServiceCopy":false` to the line, and verify that it *only* is saved for the customer, and not in your service's STSender.

Continue to the next step only if you are setting up Activity Tracker. Otherwise stop here.

## 5. Provision an Activity Tracker Sender
{: #provision-at}

Like the logging STS, an Activity Tracker Sender (ATS) is a LogDNA instance that is configured to detect and handle super tenant log lines. However, the ATSender super tenant log lines are AT events.

First, get the CRN of your logging STSender so you can link your ATSender to it. Using your own STSender name instead of "myService_STS", type:

```
ibmcloud resource service-instance "myService-STS"
```
{: codeblock}

Copy the CRN from the above output, and use it as an input parameter when creating the ATSender.

```
ibmcloud resource service-instance-create myService-ATS logdnaat 14-day us-south \
    -p '{"service_supertenant": "myservice" , "associated_logging_crn": "YOUR_STS_CRN", "provision_key": "123"}'
```
{: codeblock}

Where:  
* `myService-ATS` is whatever you call your service, with ATS ("Activity Tracker sender") appended by convention.
* `7-day` is the plan, which could also be `lite`, `14-day` or `30-day`, your choice.
* `myservice` is the CRN service-name of your service.
* `provision_key` - see [Super Tenant instructions](/docs/services/Activity-Tracker-with-LogDNA/ibm-internal-only/enable-ST.html#before) for how to obtain this key.

Notice that the service is `logdnaat` instead of `logdna`. The `associated_logging_crn` parameter links the STSender and ATSender together.

In the Observabilty view, click "Activity Tracker" and see your new ATSender.

![AT in Observability](images/myService-ATS.png)

## 6. Test your service's Activity Tracking
{: #test-at}

First, ensure that the ATSender is receiving the events from your service. In the diagram above, this is the red line that goes down to MyService-ATS.

1. In Observability > Activity Tracker, click "View LogDNA" for your ATSender.
2. You should see the events that your service writes to files in `/var/log/at` or `/var/log/at-no-rotate`. (Refer [here](https://test.cloud.ibm.com/docs/services/Activity-Tracker-with-LogDNA/ibm-internal-only?topic=logdnaat-ibm_kube#ibm_kube) for explanation of `at-no-rotate`; search for "at-no-rotate".)
3. If your service is not writing events yet (i.e. it is using AT for the first time), then write the following sample line in a sample AT log file (e.g. `/var/log/at/test.log`). Refer to the ST test instructions for how to write to your cluster's logs.

```
{"severity":"normal","reason":{"reasonCode":201},"initiator":{"credential":{"type":"token"},"name":"LOPEZDSR@uk.ibm.com","host":{"address":"138.177.90.26"},"id":"IBMid-060000JMG2","typeURI":"service/security/account/user"},"target":{"typeURI":"resource-controller/instance","host":{"address":"kub:prod-ams03:resource-controller-76693b7b88-lzlbx"},"id":"crn:v1:bluemix:public:kms:us-south:a/81de6380e6222019c6567c9c8de6dece:e3215e30-d27b-4533-857b-b27b7c5943b0::"},"eventTime":"2018-09-24T12:14:11Z","action":"kms.instance.create","outcome":"success","message":"Key Protect: create instance"}
```
{: codeblock}

This line should appear in your ATSender. Note that the `message` field is displayed as a summary of the line. To see the CADF fields, you click on the left of the line to open it.

Now test super tenancy. In the diagram, this is the red line that runs from MyService-ATS to the customer's AT instance.

1. Switch to the same account that you used for testing as a customer with super tenancy. You already have an instance of your service provisioned from the ibmcoud catalog. You already have the CRN of your service instance.
4. Provision an instance of "Activity Tracker with LogDNA" in the same account. Do this in the IBM Cloud console, not the CLI. Let us call it "Customer-AT_Instance" **Temporary work-around: instead of console, use this CLI: `ibmcloud resource service-instance-create Customer-AT-Instance logdnaat 7-day us-south -p '{"default_receiver": true}'`**
5. Switch back to your service's account.
6. Write the sample line above to an AT log file in your service's cluster (e.g. `/var/log/at/test.log`). However, this time add to the beginning of the JSON:  `"logSourceCRN":"PUT YOUR SERVICE INSTANCE CRN HERE"`. Remember that `logSourceCRN` must use an account id for the location, not a space id.
7. Look in your STS LogDNA again, and verify that the event came through.
8. Now go back to the customer account where your service instance is provisioned, and look at that AT instance. You should also see the event there.
9. As a further test, add `"saveServiceCopy":false` to the line, and verify that it *only* is saved for the customer, and not in your service's ATSender.
