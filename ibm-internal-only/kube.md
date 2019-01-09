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


# Write by service (IBM Cloud Container Service)
{: #ibm_kube}


{:shortdesc}


| Pattern                                  | Scenario                                 | Sample App                               |
| ---------------------------------------- | ---------------------------------------- | ---------------------------------------- |
| <img src="images/AT_write_directv3.png" alt="Write by Service (IBM Cloud Container Service) pattern"  height="300" width="450" /> | You have a service in the IBM Cloud that you must [register with AT](#step2) in order to collect activity data. <br> <br> Use the <b><i>Write by Service (Kube)</i></b> pattern to [write activity data](#step3) for that service into the IBM Cloud Activity Tracker (AT) service. <br> <br> Use AT to understand how this cloud service is being used by end users. [Display and analyze the activity data](../read/) that is stored for the service in AT. | |

By using this pattern, you write activity data to /var/log/at/**/*.log in your container. The cluster's [fluentd](https://www.fluentd.org/) service forwards those events to AT. Fluentd is configured to pick up events from a file located in `/var/log/at/` in your service container.


## Overview
{: #ov}

To display and analyze the usage of a Cloud service that an application interacts with, you must complete the following steps for the service:

1. [Register the service with Activity Tracker.](#step1)
2. [Enable Activity Tracker event-forwarding on your Cluster](#step2)
3. [Send events to Activity Tracker.](#step3)

Then, you and your users can [view and analyze the Cloud service activity](../read/).


## Step 1: Register the service with Activity Tracker
{: #step1}

**NOTE: First, register your service in staging. Once it is tested and compliant with AT adoption guidelines and CADF field formats, register your service for production.**


Register the service with Activity Tracker by
opening an issue [here](https://github.ibm.com/activity-tracker/customer-issues/issues/new).

The issue needs to include the following:

1. The [CRN](https://github.ibm.com/ibmcloud/builders-guide/blob/master/specifications/crn/CRN.md) service-name of the service.
You can look it up [here](http://resource-catalog.bluemix.net/search) in the Name column.
The Name column gives the service-name segment of CRN; this is the programatic name from the Catalog.
2. The Cloud Foundry space ID (service_provider_project_id) that you want the service's events forwarded to. (service_provider_account_id) is the guid of the account of this space <br><br>
This space is only for your team to use internally, and your service does not have to run in the space or in Cloud Foundry.
The service's user's account IDs or space IDs will be specified in the actual events being sent, so that AT will know how to get the events to your users.
3. The Activity Tracker endpoint
to register the service against.<br><br>
The following tables list the endpoints available for Activity Tracker per environment and region. You must register for each region individually that you want to use.

**Stage1**

| Environment   | Endpoint                                          |
| ------------- | ------------------------------------------------- |
| Dallas        | https://activity-tracker.stage1.ng.bluemix.net    |
| London        | https://activity-tracker.stage1.eu-gb.bluemix.net |
| Frankfurt     |                not available                      |
| Sydney        |                not available                      |

**Production**

| Environment          | Endpoint                                         |
| -------------------- | ------------------------------------------------ |
| Dallas               | https://activity-tracker.ng.bluemix.net          |
| London               | https://activity-tracker.eu-gb.bluemix.net       |
| Frankfurt            | https://activity-tracker.eu-de.bluemix.net       |
| Sydney               | https://activity-tracker.au-syd.bluemix.net      |


Make sure to request a **service token** for your service (not an IAM token). You will use this when you
enable Activity Tracker on your cluster in the next step.

Wait for the confirmation from the team that the service has been registered before you proceed to the next step.


## Step 2: Enable Activity Tracker event-forwarding on your Cluster
{: #step2}

In order to add Activity Tracker support to your cluster, you'll need to:

2a. Create an `ENCODED_SERVICES` string<br>
2b. Add a Secret to your cluster<br>
2c. Add a ConfigMap to your cluster<br>
2d. Restart the fluentd pods<br>

These instructions require:

* Familiarity with Kubernetes
* A Kubernetes cluster for your service, in IBM Cloud (Armada). These instructions will not work on a free trial account.
* An admin role for your cluster. Be sure to get the admin cluster-config for running kubectl: `bx cs cluster-config CLUSTER_NAME --admin`

These instructions involve creating several local files
which `kubectl` uses to update your cluster.
If you want copies of the files that are already created,
clone [this repo](https://github.ibm.com/activity-tracker/helloATv2).

### 2a: Encode AT account info
{: #step2a}

Copy the following line into a text editor, creating a file called `encodedServices.sh`:

```
echo '{"services":[{"service_name":"YOUR_SERVICE_NAME","auth_token_value":"YOUR_SERVICE_TOKEN","project_id": "YOUR_SERVICE_SPACE_ID"}]}' | base64
```
{: codeblock}


Replace the following values in this line:

1. Replace `YOUR_SERVICE_NAME` and `YOUR_SERVICE_SPACE_ID` with the information you registered to AT.
2. Replace `YOUR_SERVICE_TOKEN` with token you got back from AT when you registered.
3. If you run multiple services on one cluster, add the other service entries to the services array.

The above information pertains to the region that the cluster is in. Other regions require other clusters, each with a different AT registration.

Once you have your service JSON ready, encode it by running
the script at a command prompt.
The command's output is your `ENCODED_SERVICES` string, to be used below.

### 2b: Add a Secret to your cluster
{: #step2b}

Now that the account info is encoded,
you need to make it available to Armada as a "secret".
Create a file called `at_secret.yaml` and copy in the following:

```
yaml
apiVersion: v1
data:
  ACTIVITY_TRACKER_URL: ENCODED_SERVICES
kind: Secret
metadata:
  name: activity-tracker-secrets
  namespace: kube-system
type: Opaque
```
{: codeblock}

Replace the following values in this file:

1. `ACTIVITY_TRACKER_URL` - the Activity Tracker URL that you registered your service against above, **without** the leading `https://`.  This will be something
like `activity-tracker.ng.bluemix.net`.
2. `ENCODED_SERVICES` - this is an encoded JSON string you created above, containing your service-name,
service space ID, and service token.
3. The name `activity-tracker-secrets` should **not** be changed.

Add the secret to your cluster by running `kubectl create -f at_secret.yaml`. This will create the Activity Tracker secret in the `kube-system` namespace.
If you get an error saying the secret already exists then you can delete the existing one by running `kubectl -n kube-system delete secret activity-tracker-secrets`
 and run the `kubectl create` command again. 


### 2c: Add a ConfigMap to your cluster
{: #step2c}

A ConfigMap will tell fluentd what files to read,
and where to send the data.
Create a file called `at_config.yaml` and copy in the following:

```
yaml
apiVersion: v1
data:
  logging-activity-tracker.conf: |
    <worker 0>
      <source>
        @type tailinodes
        path /var/log/at/**/*.log*
        exclude_path /var/log/at/**/*.gz
        pos_file /mnt/ibm-kube-fluentd-persist/fluentd-at.pos
        time_format %Y-%m-%dT%H:%M:%S
        tag kubernetes.at.*
        format json
        read_from_head true
        read_lines_limit 100
        rotate_wait 43200 # set to 12 hours in case AT gets behind in reading events
        follow_inodes true
      </source>
      <match kubernetes.at.**>
        @type ibmactivitytracker
        <buffer>
            @type file
            overflow_action block
            flush_interval 10s
            retry_max_times 10
            total_limit_size 800m
            chunk_limit_size 500k
            flush_at_shutdown true
            path /mnt/ibm-kube-fluentd-persist/fluentd-at-buffer.buf
        </buffer>
        targetHost ACTIVITY_TRACKER_URL
        service_region ACTIVITY_TRACKER_REGION
        ibm_plugin_log_level warn
        secrets_path /mnt/activity-tracker/secrets
        retry_wait 1s
        max_retry_wait 10s
        disable_retry_limit true
      </match>
    </worker>
kind: ConfigMap
metadata:
  name: at-fluentd-config
  namespace: kube-system
```
{: codeblock}

Replace the following values in this file:

1. `ACTIVITY_TRACKER_URL` - the Activity Tracker URL that you registered your service against above, **without** the leading `https://`.  This will be something like `activity-tracker.ng.bluemix.net`.

2. `ACTIVITY_TRACKER_REGION` - the Activity Tracker region that you want to send your events to and
it also has to be the one that you registered your service against. This will be something
like `ng`.

Add the ConfigMap to your cluster by running `kubectl create -f at_config.yaml`. This will create the Activity Tracker ConfigMap in the `kube-system` namespace where fluentd requires it.

**Special note on log rotation**

The following configuration will handle log rotation of any files written to the `var/log/at` directory. Rotation is done
daily and rotated logs are kept for three days. If you want your service to handle log rotation because you want to be 
able to keep the handle to your file open or you're using a logger that handles log rotation then you'll want to update
the path to be `/var/log/at-no-rotate`.

### 2d: Restart the fluentd pods
{: #step2d}

You must restart each fluentd pod for it to pick up the new configuration
and begin sending your events to AT.
Save the following script in a file (such as `restartFluentd.sh`), `chmod +x` the file, and run it.

```
kubectl -n kube-system delete pods -l app=ibm-kube-fluentd
sleep 30
kubectl -n kube-system get pods -l app=ibm-kube-fluentd
```
{: codeblock}

The fluentd pods will be printed out at the end. Verify that they are all in `Running` state.

Now the fluentd pods are watching the `/var/log/at` directory,
waiting to process any events that the other pods write there.


## Step 3: Send events to Activity Tracker
{: #step3}

Now that Activity Tracker is enabled on your cluster,
you must enable your service to send events.
The service must write its events into log files in `/var/log/at/*.log`,
because that is where fluentd will look for them on the worker nodes.
Fluentd will include any `*.log` file in any subdirectory of `/var/log/at`. 
If you want to handle log rotation for your files then write the logs to 
`/var/log/at-no-rotate` instead.

For this to work, you must map your event log file to `/var/log/at` or `/var/log/at-no-rotate`.
To do this, mount a volume in your service's deployment descriptor,
as the following sample shows.

**Note:** Kubernetes creates the mount directory as the root user.
If your service is not running as root, then you will either need to change the
user in your image ([using the `USER` directive][user-directive]) or [use an
`initContainer`](#init-containers) to change the permissions.

[user-directive]: https://docs.docker.com/engine/reference/builder/#user

**Sample deployment descriptor**

The following sample deploys a test service called `at-noisy`which sends a sample event every 30 seconds.
Other than the deployment descriptor, no additional code is needed.
The `at-noisy` service consists of one line of bash: the "while true..." line in the file below.

Use this simple sample to verify that you can successfully send events and
view them in the Activity Tracker console.

Save this text to a file called `at_noisy.yaml`.

```
yaml
apiVersion: extensions/v1beta1
kind: Deployment
metadata:
  name: at-noisy
spec:
  replicas: 1
  selector:
    matchLabels:
      app: at-noisy
  template:
    metadata:
      name: at-noisy
      labels:
        app: at-noisy
    spec:
      containers:
      - name: at-noisy
        image: ubuntu:16.04
        args:
        - sh
        - -c
        - "while true; do echo '{\"meta\":{\"serviceProviderName\":\"YOUR_SERVICE_NAME\",\"serviceProviderRegion\":\"YOUR_SERVICE_SPACE_REGION\",\"serviceProviderProjectId\":\"YOUR_SERVICE_SPACE_ID\",\"userAccountIds\":[\"USER_ACCOUNT_ID\"],\"userSpaceId\":\"USER_SPACE_ID\",\"userSpaceRegion\":\"USER_SPACE_REGION\"},\"payload\":{\"initiator\":{\"id\":\"rbertram@us.ibm.com\",\"typeURI\":\"security/account/user\",\"credential\":{\"type\":\"user\"}},\"target\":{\"id\":\"crn:v1:bluemix:public:containers-kuberentes:dal09:a/4324327284:6e4c93cdf28e47f6abecb7e97e65056d::\",\"typeURI\":\"containers-kubernetes/worker\"},\"action\":\"containers-kubernetes.worker.create\",\"outcome\":\"success\",\"reason\":{\"reasonCode\":200},\"severity\":\"normal\",\"eventTime\":\"2017-10-19 19:07:50.32 +0000 UTC\"}}' >> /var/log/at/noisy_events.log; sleep 30; done"
        imagePullPolicy: "Always"
        volumeMounts:
          - mountPath: /var/log/at
            name: at-events
      volumes:
        - name: at-events
          hostPath:
            path: /var/log/at # or /var/log/at-no-rotate if you are handling log rotation
```
{: codeblock}

## The test service: `at-noisy`
{: #test_svc}

Every 30 seconds, the "while true..." line writes an event to `/var/log/at/noisy_events.log`.
The name of the file is a constant in this simple example,
but in a real service, each log file from each pod should
have a unique name, since the volume is shared by all pods.
**TODO: add sample code to helloATv2 for pod-unique names.**

Each event uses the following JSON object,
copied from above:

```
javascript
  {
    meta: {
      serviceProviderName: "YOUR_SERVICE_NAME",
      serviceProviderRegion: "YOUR_SERVICE_SPACE_REGION",
      serviceProviderProjectId: "YOUR_SERVICE_SPACE_ID",
      userAccountIds: ["USER_ACCOUNT_ID"],
      userSpaceId: "USER_SPACE_ID",
      userSpaceRegion: "USER_SPACE_REGION"
    },
    payload: {
        initiator: {
          id: "rbertram@us.ibm.com",
          typeURI: "security/account/user",
          credential: {
            type: "user"
          }
        },
        target: {
          id: "crn:v1:bluemix:public:containers-kuberentes:dal09:a/4324327284:6e4c93cdf28e47f6abecb7e97e65056d::",
          typeURI: "containers-kubernetes/worker"
        },
        action: "containers-kubernetes.worker.create",
        outcome: "success",
        reason: {
          reasonCode: 200
        },
        severity: "normal",
        eventTime: "2017-10-19 19:07:50.32 +0000 UTC"
      }
  }
```
{: codeblock}


There are two parts to the structure: `meta` and `payload`.

* `meta` tells Activity Tracker where to send the event, as explained below.
* `payload` contains the CADF fields. CADF is explained [here](../../#cadf), and the fields are described in detail [here](../event/).
  This sample event shows rbertram creating a Kube worker node.

The `meta` structure tells AT where to save two copies of each event: one for the service, and one for the user.
Before you deploy `at-noisy`, you must replace the placeholders in `meta` with your own values.

1. For the service copy of the event (your copy), replace the `YOUR_SERVICE_*` placeholders
  with the values that you registered to AT.
2. For the user's copy of the event, you will normally do **one** of these options:
  <br>a. Provide `USER_ACCOUNT_ID` to send to the user's account, and omit `userSpaceId` and `userSpaceRegion`.
  (Only give one account id, even though it is an array.)
  <br>b. Provide `USER_SPACE_ID` and `USER_SPACE_REGION` to send to the user's space, and omit `userAccountIds`.<br>
  For the test, specify either (a) an account or (b) a space, so that you can look to see if it is working.

## Try out the test service
{: #try}

Deploy `at-noisy` by running `kubectl create -f at_noisy.yaml`.

Go to Activity Tracker UI, and verify that the events are coming through in the accounts and spaces you specified.

1. In IBM console, navigate to each space.
  (If you gave an account for the user, pick any space in the account.)
2. If Activity Tracker is not already provisioned, then provision it.
3. Open AT to the Manage tab.
4. If you are looking for events at the account level,
  switch the dropdown at the top from "space" to "account".
  You must be the Account Owner to see the account events.

When you are finished with this test, remove the `at-noisy` service
by running `kubectl delete -f at_noisy.yaml`.


## helloAT revisited
{: #helloat}

Try the [Kube version of helloAT](https://github.ibm.com/activity-tracker/helloATv2).

Back by popular demand, this is an update to the hello-world NodeJS application that sends events to AT. The original helloAT used protobuf to call the AT API. This simplified version just writes to a file, and lets Armada (fluentd) do the heavy lifting.

## Debugging Tips
{: #debug}

If you don't see your events in Activity Tracker or Kibana you can do the following to figure out what's going on:

1. Check the fluentd logs for any errors. Fluentd runs as a daemonset so you'll need to find the fluentd pod that's running on the
same worker node as your application. To find out what node your application is on run `kubectl -n YOUR_NAMESPACE describe pod
YOUR_POD_NAME`. Towards the top it will list what node the pod is running on. Run the command `kubectl describe node NODE_IP` to 
see the list of pods running on that node. Find ibm-kube-fluentd in that list then run `kubectl -n kube-system logs FLUENTD_POD > pod.log`
 to fetch the logs. Look toward the end of the logs to see if there are any obvious configuration issues. 
 * If you see something
 like `service token does not exist for service xxx` then that means it can't find the service token in the encoded secret you created
 * If you see `Error contacting AT with code 401 and message Unauthorized` this means the token you're using isn't valid. Make sure you've specified
 the correct activity tracker endpoint that you used when registering your service. 
2. Verify that fluentd can see your events. Exec into the fluentd pod `kubectl -n kube-system exec -it FLUENTD_POD /bin/sh` 
then run `cd /var/log/at` then 'ls -l' to verify that your event logs files are there. View the event files to make sure 
your events are in there. 
3. If you don't see any obvious issues in the logs then you can change the fluentd activity tracker pluging logging level. 
If you set it to debug then fluentd will print out each event that it processes and will also print out the response code 
it gets back after sending an event to activity tracker. To update the debug level run `kubectl -n kube-system edit at-fluentd-config`
and change `ibm_plugin_log_level` to `debug`. Restart the fluentd pods to pick up the changes and follow the directions in step
1 to view the logs.

NOTE: If the kubectl edit command fails with the error `the server doesn't have a resource type "at-fluentd-config`, try the following: `kubectl -n kube-system edit cm at-fluentd-config`


## Init Containers
{: #init-containers}

Since Kubernetes mount host paths as root, you may need to change the file
permissions so your service can write logs there. One such method is to run
an `initContainer` that changes the file permissions.

If your service name is `helloAT` then you could add this to your pod spec:

```
yaml
  initContainers:
    - name: fix-permissions
      image: alpine:3.6
      command:
        - sh
        - -c
        - 'mkdir -p /var/log/at/helloAT; chmod -R a+rwx /var/log/at/helloAT'
      volumeMounts:
        - name: at-events
          mountPath: /var/log/at
      securityContext:
        runAsUser: 0
```
{: codeblock}

This will add write permissions on the `/var/log/at/helloAT` directory for all users.

## Using protobuf to create JSON string events for writing to a logfile
{: #protobuf}

Services should write JSON content directly to file, and not convert to/from protobuf in the process. This avoids unnecessary work and overhead, and avoids existing bugs in Trail.java conversion to JSON.
