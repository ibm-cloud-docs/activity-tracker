---

copyright:
  years: 2019, 2020
lastupdated: "2019-01-08"

keywords: IBM Cloud, LogDNA, Activity Tracker, web UI, browser

subcollection: Activity-Tracker-with-LogDNA

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
{:external: target="_blank" .external}

# Launching the LogDNA web UI directly from a browser
{: #launch_browser}

After you provision an instance of the {{site.data.keyword.at_full_notm}} service in the {{site.data.keyword.cloud_notm}}, you can view, monitor, and manage events through the {{site.data.keyword.at_full_notm}} web UI.
{:shortdesc}





## Launching the LogDNA web UI directly from a browser
{: #launch_step3}

You can launch the LogDNA web UI directly from a browser

Looking more at the above, finally. Are you aware that LogDNA has an ibm-oauth (I think) way to login from an url?
https://app.us-south.logging.cloud.ibm.com/ext/ibm-sso/ed79138c92
will log me into my LogDNA account:
https://app.us-south.logging.cloud.ibm.com/ed79138c92/logs/view
Not asking me to SSO again with w3id, if I already have.
Furthermore, you can pass in query parameters to initialize the view that comes up. Like:
https://app.us-south.logging.cloud.ibm.com/ext/ibm-sso/4a7b5dca04?tags=mytag,myothertag
Which would filter by those two tags.  The parameters include:
q (search box)
t (timeframe)
levels=info,debug,warn,error,n%2Fa
apps=crn...
hosts
tags



https://app.us-south.logging.cloud.ibm.com/9bd0f9b063/logs/view?t=timestamp%3A1593583439648&a=1593583439648.1231378191822954515

