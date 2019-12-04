---

copyright:
  years: 2019
lastupdated: "2019-09-27"

keywords: IBM Cloud, LogDNA, Activity Tracker, cloud foundry

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
{:important: .important}
{:note: .note}

 
# Monitoring your LogDNA instance archives
{: #monitor_archiving}

 {{site.data.keyword.at_full_notm}} 
{:shortdesc}



1. get the service ID that you are using to archive into COS

2. create a view with the following query:

```
ServiceId-9066eabb-ad5b-4ed0-86c7-74bf235ae4bf AND action:iam-identity.serviceid-apikey.login
```
{: codeblock}

you get an event for every archive file that is uploaded into your COS bucket




