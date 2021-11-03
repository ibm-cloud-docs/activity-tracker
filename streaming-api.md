---

copyright:
  years: 2019, 2021
lastupdated: "2021-08-09"

keywords: IBM Cloud, Activity Tracker, streaming

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}

# Managing streaming by using the API
{: #streaming-manage}



Using the streaming API


Dallas Service key: 183f001b42fc49af85bc46e02fd17e06
London:  9fc834458c084cd5873a498bd25efed3
Frankfurt: 74dd4143fc044ad68ab37b0766de6d23

## Get details of the streaming configuration

Use this method to get an existing streaming configuration.
{: note}

```shell
curl --request GET https://api.us-south.logging.cloud.ibm.com/v1/config/stream  
 -H "content-type: application/json"  
 -H "servicekey: <SERVICE_KEY>"  
```

curl --request GET https://api.us-south.logging.cloud.ibm.com/v1/config/stream  -H "content-type: application/json"  -H "servicekey: 183f001b42fc49af85bc46e02fd17e06"  

curl --request GET https://api.eu-de.logging.cloud.ibm.com/v1/config/stream  -H "content-type: application/json"  -H "servicekey: 74dd4143fc044ad68ab37b0766de6d23"  
curl --request GET https://api.eu-gb.logging.cloud.ibm.com/v1/config/stream  -H "content-type: application/json"  -H "servicekey: 9fc834458c084cd5873a498bd25efed3"  

response

```
{"status":"active","topic":"at-dallas-topic","user":"token","brokers":["kafka-0.mh-msngbffdzhflbqpyrcvr-4c201a12d7add7c99d2b22e361c6f175-0000.eu-de.containers.appdomain.cloud:9093","kafka-1.mh-msngbffdzhflbqpyrcvr-4c201a12d7add7c99d2b22e361c6f175-0000.eu-de.containers.appdomain.cloud:9093","kafka-2.mh-msngbffdzhflbqpyrcvr-4c201a12d7add7c99d2b22e361c6f175-0000.eu-de.containers.appdomain.cloud:9093"]}
```

## Configure streaming

Use this method to create a streaming configuration.
{: note}

```shell
curl --request POST https://api.eu-gb.logging.cloud.ibm.com/v1/config/stream  
 -H "content-type: application/json"  
 -H "servicekey: <SERVICE_KEY>"  
 -d '{"brokers":["broker-1.kafka.svc00.env.eventstreams.cloud.ibm.com:9093"],"topic":"topic","user":"token","password":"SASL_PASSWORD"}' 
 ```

curl --request POST https://api.eu-gb.logging.cloud.ibm.com/v1/config/stream -H "content-type: application/json" -H "servicekey: 9fc834458c084cd5873a498bd25efed3" -d '{"brokers":["kafka-0.mh-msngbffdzhflbqpyrcvr-4c201a12d7add7c99d2b22e361c6f175-0000.eu-de.containers.appdomain.cloud:9093","kafka-1.mh-msngbffdzhflbqpyrcvr-4c201a12d7add7c99d2b22e361c6f175-0000.eu-de.containers.appdomain.cloud:9093","kafka-2.mh-msngbffdzhflbqpyrcvr-4c201a12d7add7c99d2b22e361c6f175-0000.eu-de.containers.appdomain.cloud:9093"],"topic":"at-dallas-topic","user":"token","password":"wckJ6WcAb_1-pjm5oGNGAZ05yq4C11krxrD4Vf_Z6qHf"}' 

{"status":"active","brokers":["kafka-0.mh-msngbffdzhflbqpyrcvr-4c201a12d7add7c99d2b22e361c6f175-0000.eu-de.containers.appdomain.cloud:9093","kafka-1.mh-msngbffdzhflbqpyrcvr-4c201a12d7add7c99d2b22e361c6f175-0000.eu-de.containers.appdomain.cloud:9093","kafka-2.mh-msngbffdzhflbqpyrcvr-4c201a12d7add7c99d2b22e361c6f175-0000.eu-de.containers.appdomain.cloud:9093"],"topic":"at-dallas-topic","user":"token"}

## Update the streaming configuration


Use this method to update an existing streaming configuration.
{: note}

```shell
curl --request PUT https://api.us-south.logging.cloud.ibm.com/v1/config/stream  
 -H "content-type: application/json"  
 -H "servicekey: <SERVICE_KEY>"  
 -d '{"brokers":["broker-1.kafka.svc00.env.eventstreams.cloud.ibm.com:9093"],"topic":"topic","user":"token","password":"SASL_PASSWORD"}' 
```



curl --request PUT https://api.eu-gb.logging.cloud.ibm.com/v1/config/stream -H "content-type: application/json" -H "servicekey: 9fc834458c084cd5873a498bd25efed3" -d '{"brokers":["kafka-0.mh-msngbffdzhflbqpyrcvr-4c201a12d7add7c99d2b22e361c6f175-0000.eu-de.containers.appdomain.cloud:9093","kafka-1.mh-msngbffdzhflbqpyrcvr-4c201a12d7add7c99d2b22e361c6f175-0000.eu-de.containers.appdomain.cloud:9093","kafka-2.mh-msngbffdzhflbqpyrcvr-4c201a12d7add7c99d2b22e361c6f175-0000.eu-de.containers.appdomain.cloud:9093"],"topic":"topic","user":"token","password":"wckJ6WcAb_1-pjm5oGNGAZ05yq4C11krxrD4Vf_Z6qHf","status":"inactive"}' 

error when the saervice Key is not valid - Check the service key for the instance in the region that the user is targetting:
{"error":"Service Key Validation Error: Invalid or deactivated servicekey","status":"error","code":"NotAuthorized"}

response:
{"code":"EINVAL","details":[{"message":"\"status\" is not allowed","key":"status"}]}


curl --request PUT https://api.us-south.logging.cloud.ibm.com/v1/config/stream -H "content-type: application/json" -H "servicekey: 9fc834458c084cd5873a498bd25efed3" -d '{"brokers":["kafka-0.mh-msngbffdzhflbqpyrcvr-4c201a12d7add7c99d2b22e361c6f175-0000.eu-de.containers.appdomain.cloud:9093","kafka-1.mh-msngbffdzhflbqpyrcvr-4c201a12d7add7c99d2b22e361c6f175-0000.eu-de.containers.appdomain.cloud:9093","kafka-2.mh-msngbffdzhflbqpyrcvr-4c201a12d7add7c99d2b22e361c6f175-0000.eu-de.containers.appdomain.cloud:9093"],"topic":"topic","user":"token","password":"wckJ6WcAb_1-pjm5oGNGAZ05yq4C11krxrD4Vf_Z6qHf"}' 

{"error":"Service Key Validation Error: Invalid or deactivated servicekey","status":"error","code":"NotAuthorized"}


## Delete the streaming configuration

Use this method to delete the streaming config.
{: note}

```shell
curl --request DELETE https://api.us-south.logging.cloud.ibm.com/v1/config/stream  
 -H "content-type: application/json"  
 -H "servicekey: <SERVICE_KEY>"  
```

curl --request DELETE https://api.eu-gb.logging.cloud.ibm.com/v1/config/stream  -H "content-type: application/json"  -H "servicekey: 9fc834458c084cd5873a498bd25efed3"  

{"deleted":true}


## Add a streaming exclusion rule

Use this method to create a streaming exclusion rule.
{: note}


```shell
curl --request POST https://api.us-south.logging.cloud.ibm.com/v1/config/stream/exclusions  
 -H "content-type: application/json"  
 -H "servicekey: <SERVICE_KEY>"  
 -d '{"title": "Exclude Example", "query": "example", "active": true}' 
```

curl --request POST https://api.eu-gb.logging.cloud.ibm.com/v1/config/stream/exclusions  -H "content-type: application/json"  -H "servicekey: 9fc834458c084cd5873a498bd25efed3" -d '{"title": "Exclude Rule 1", "query": "host:sysdig-monitor (action read)", "active": true}' 

{"hosts":[],"apps":[],"title":"Exclude Rule 1","query":"host:sysdig-monitor (action read)","active":true,"id":"3ee3baf108"}


## List streaming exclusion rules

Use this method to list existing streaming exclusion rules
curl --request GET https://api.us-south.logging.cloud.ibm.com/v1/config/stream/exclusions  
 -H "content-type: application/json"  
 -H "servicekey: <SERVICE_KEY>"  
```shell

curl --request GET https://api.eu-gb.logging.cloud.ibm.com/v1/config/stream/exclusions -H "content-type: application/json"  -H "servicekey: 9fc834458c084cd5873a498bd25efed3"  
 ```

[{"hosts":[],"apps":[],"title":"Exclude Rule 1","query":"host:sysdig-monitor (action read)","active":true,"id":"3ee3baf108"}]





