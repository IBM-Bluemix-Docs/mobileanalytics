---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-06"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Using metrics and events
{: #usingmetrics}

## Monitoring applications with Mobile Analytics

The {{site.data.keyword.mobileanalytics_full}} provides monitoring and analytics for your mobile applications. You can record application logs and monitor data with the {{site.data.keyword.mobileanalytics_short}} Client SDK. Developers can control when to send this data to the {{site.data.keyword.mobileanalytics_short}} Service. When data is delivered to {{site.data.keyword.mobileanalytics_short}}, you can use the {{site.data.keyword.mobileanalytics_short}} console to get analytics insights about your mobile applications, devices, and application logs.
{: shortdesc}

##Pre-Defined Metrics

With **pre-defined metrics** you can answer questions like:

* How many new users do I have?  
* How many people are actively using my application?  
* How frequently are people using my application? 
* What time of day are people using my application?  
* What device models do my users prefer? 
* When should I deprecate support for legacy operating systems? 
* Which applications are experiencing performance issues?  

##Custom Events

By adding your own **custom events** you can answer questions like: 

* What features are used most and least?  
* Where are users entering and leaving my app?  
* What activities are users viewing most?  
* Are users completing workflows in the app (for example, conversion funnels)?   

Client-side logs and usage data are gathered automatically and sent to the Mobile Analytics service on demand. Developers and administrators can use the {{site.data.keyword.mobileanalytics_short}} service dashboard to view data that is gathered by the client SDK.

## Data visualization
{: data-visualization notoc}

All data that is collected by the analytics service can be visualized through the {{site.data.keyword.mobileanalytics_short}} dashboard which is accessible from your {{site.data.keyword.Bluemix_notm}} dashboard by clicking your IBM {{site.data.keyword.mobileanalytics_short}} service tile instance. <!--You can also create custom charts, based on data that is collected by the analytics service in the dashboard.--> In addition to an at-a-glance view of your mobile analytics, the analytics feature includes the capability to perform a raw search against client logs, captured client crash data, and any extra data that you explicitly provide through client API function calls that feed into the {{site.data.keyword.mobileanalytics_short}} service. 

