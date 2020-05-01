---

copyright:
  years: 2019, 2020
lastupdated: "2020-03-03"

keywords: IBM Cloud, LogDNA, Activity Tracker, global events

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

# Global Events in Activity Tracker
{: #global_events}

## What's Changing
{: #global_changing}

Several services have Activity Tracker events that are global, i.e. they do not belong in a specific region. These services include IAM, BSS, and Ghost. In addition, a subset of COS events are global.
Up to now, all global events have been stored in the `eu-de` (Frankfurt) location by convention.
However, customers require the ability to save their global events in the location of their choice.
In fact, some customers require that global events should not leave the location where they are generated.

**Kaiser Permanente is requiring that their global events be stored only in Dallas, starting at the end of March 2020.**
Therefore, LogDNA is now laying the groundwork to allow customers to select the location where their global events will be saved.
Events originating from the selected location will be stored in that location without ever leaving it.
The first customers to use this feature, starting with Kaiser Permanente, will be hardcoded. But a configuration UI will be added later and the feature will be generally available.

To make it possible for LogDNA to identify and route the global events, we need IBM services to stop sending global events to eu-de and start sending global events to a unique global endpoint.

Global Activity Tracker events have previously been sent to the `eu-de` supertenant ingestion endpoint, in Frankfurt. This endpoint received not only global AT events, but also Frankfurt operational logs, platform logs, and regional Frankfurt AT events. But now, global AT events will be sent to a `global` endpoint. Any service that sends global AT events must send those events to the global endpoint. The service will still send its other Frankfurt logs (and events, if applicable) to the normal `eu-de` endpoint.

**Coming soon: global routing diagram, additional explanation**

## Sending Global Events
{: #global_sending}

The global endpoint, using `global` as the location instead of `eu-de`, is now available. If you send global events to this endpoint today, they will go to `eu-de` just as they did before, so you will see no change. However, by the end of March, the global events for Kaiser Permanente's accounts will be sent to their AT instances in Dallas. (Your service's copy will still be in your ATS in `eu-de`. You don't need to move your STS/ATS or set up new ones.)

### Sending with the Agent
{: #sending_agent}

These instructions assume your global service uses the Kubernetes `logdna-agent`.

To send AT events to the global endpoint, you will run two instances of `logdna-agent` - one for logs and one for global AT events. To deploy the two agents, you will use a modified yaml file for each one. Here are reference yaml files, for your convenience:
1. The [yaml for the logging agent](https://github.ibm.com/rbertram/scratch/blob/master/logdna-doc-files/logdna-agent-v2-st-private.yaml)
2. The [yaml for the AT agent](https://github.ibm.com/rbertram/scratch/blob/master/logdna-doc-files/logdna-at-agent-v2-st-private.yaml)

These yaml files are derived from http://assets.eu-de.logging.cloud.ibm.com/clients/logdna-agent-v2-st-private.yaml downloaded on 2020/03/02. In case you are working from a different original yaml file, here are the changes you need to make to it:

1. Make a copy of the logging yaml for the AT agent.
2. The **logging** agent will pick up all of the usual logs. But we want it to no longer pick up the AT events, so we add a `LOGDNA_EXCLUDE` to the logging yaml in the `env` section:
  ```
         - name: LOGDNA_EXCLUDE
           value: /var/log/at/**
  ```
3. Conversely, the **Activity Tracker** agent needs to only pick up the AT events and ignore the logs, so we make these changes to the AT yaml:
  ```
        volumeMounts:
        - name: varlogat
          mountPath: /var/log/at
  ...
      volumes:
      - name: varlogat
        hostPath:
          path: /var/log/at
  ```
4. The **Activity Tracker** agent also needs to avoid naming conflicts with the logging agent, so we change its name in `metadata` & `containers`:
  ```
  metadata:
    name: logdna-agent-activity-tracker
  ...
        containers:
        - name: logdna-agent-activity-tracker
  ```
5. And finally, for AT, change "eu-de" to "global" to send to the new endpoint.
  ```
        - name: LDAPIHOST
          value: api.private.global.logging.cloud.ibm.com
        - name: LDLOGHOST
          value: logs.private.global.logging.cloud.ibm.com
  ```
  Most services should use the private global endpoints. To use the public global endpoints instead, set the values to `api.global.logging.cloud.ibm.com` and `logs.global.logging.cloud.ibm.com`.
  
One more thing: If your current yaml uses any custom tags in `LOGDNA_TAGS`, be sure to copy them into both of the new yaml files.

That's it. Here's a [comparison of the two files](https://github.ibm.com/rbertram/scratch/blob/master/logdna-doc-files/yaml-compare.png).


### Sending to the Ingestion API
{: #sending_api}

If your code is sending data directly to LogDNA via the [ingestion API](https://docs.logdna.com/reference#api), then you'll need to make your code send logs and AT events to separate endpoints.

1. Logs go to `logs.private.eu-de.logging.cloud.ibm.com/supertenant/logs/ingest`. Replace `eu-de` with whatever location your code is logging in. AT regional events also go to this endpoint.
2. AT global events go to `logs.private.global.logging.cloud.ibm.com/supertenant/logs/ingest`.

## Super Tenant Sender (STS) in Dallas
{: #sts_dallas}

Your service will need an STS in Dallas (`us-south`), even if you don't use it for anything. LogDNA needs it for storing a Dallas copy of the ingestion key. It will use the STS to authenticate your AT events before storing them in the users' Dallas AT instances.

1. Does your service already have an STS in Dallas? If yes, skip to 2.

    Otherwise, create an STS in your service's account in the `us-south` region. The instructions are [here](/docs/services/Activity-Tracker-with-LogDNA/ibm-internal-only?topic=logdnaat-enable_st#STS), sub-step 2 only ("Provision your service's Logging Super Tenant Sender (STS)"). 
    - Use a 7-day plan, or whatever plan you want. No data will be saved in this STS unless you save it yourself.
    - Specify `us-south` in the command.
    - Use the same `name-of-your-service` as you did in `eu-de`. This is your CRN service name.
    - Use the latest ingestion key (last rotated in mid-April).
    
2. Get the LogDNA UI URL of your Dallas STS, and slack it to Randy Bertram.

That's all! When LogDNA enables global routing, a copy of your `eu-de` ingestion key will magically appear in the API keys of your `us-south` STS. Information on how to rotate the shared ingestion key will be available soon.
