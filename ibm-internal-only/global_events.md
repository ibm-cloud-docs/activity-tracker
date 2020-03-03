---

copyright:
  years: 2019, 2020
lastupdated: "2020-03-01"

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

**This page is under construction.**

## What's Changing
{: #global_changing}

Several services have Activity Tracker events that are global, i.e. they do not belong in a specific region. These services include IAM, BSS, and Ghost. In addition, a subset of COS events are global.
Up to now, all global events have been stored in the `eu-de` (Frankfurt) location by convention.
However, customers require the ability to save their global events in the location of their choice.
In fact, some customers require that global events should not leave the location where they are generated.

LogDNA is now laying the groundwork to allow customers to select the location where their global events will be saved.
Events originating from the selected location will be stored in that location without ever leaving it.
The first customers to use this feature will be hardcoded, but a configuration UI will be added later and the feature will be generally available.

To make it possible for LogDNA to identify and route the global events, we need IBM services to stop sending global events to eu-de and start sending global events to a unique global endpoint.

Global Activity Tracker events have previously been sent to the `eu-de` supertenant ingestion endpoint, in Frankfurt. This endpoint received not only global AT events, but also Frankfurt operational logs, platform logs, and regional Frankfurt AT events. But now, global AT events will be sent to a `global` endpoint. Any service that sends global AT events must send those events to the global endpoint. The service will still send its other Frankfurt logs (and events, if applicable) to the normal `eu-de` endpoint.

**Coming soon: global routing diagram, additional explanation**

## Sending Global Events
{: #global_sending}

These instructions assume your global service uses the Kubernetes `logdna-agent`.

To send AT events to the global endpoint, you will run two instances of `logdna-agent` - one for logs and one for global AT events. To deploy the two agents, you will use a modified yaml file for each one. Here are reference yaml files, for your convenience:
1. The [yaml for the logging agent](https://github.ibm.com/rbertram/scratch/blob/master/logdna-doc-files/logdna-agent-v2-st-private.yaml)
2. The [yaml for the AT agent](https://github.ibm.com/rbertram/scratch/blob/master/logdna-doc-files/logdna-at-agent-v2-st-private.yaml)

These yaml files are derived from http://assets.eu-de.logging.cloud.ibm.com/clients/logdna-agent-v2-st-private.yaml downloaded on 2020/03/02. In case you are working from a different original yaml file, here are the changes you need to make to it:

1. Make a copy of the logging yaml for the AT agent.
2. The **logging** agent will pick up all of the usual logs. But we want it to no longer pick up the AT events, so we add a `LOGDNA_EXCLUDE` to the logging yaml in the `env` section:
  ```
         - name: LOGDNA_EXCLUDE
           value: /var/log/at**
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

That's it.

