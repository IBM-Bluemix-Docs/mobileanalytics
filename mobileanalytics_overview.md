---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-08"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# About {{site.data.keyword.mobileanalytics_short}}  
{: aboutmobileanalytics}

{: shortdesc}
The {{site.data.keyword.mobileanalytics_full}} service provides key application usage and performance insights for mobile application developers and application owners. By using {{site.data.keyword.mobileanalytics_short}} application owners and developers can understand what is happening on the user side, and they can use this insight to build better applications that are hyper-relevant to users and that stand out in the veritable sea of mobile applications. 

{: #overview}  
The service includes the {{site.data.keyword.mobileanalytics_short}} Console where developers and application owners can monitor mobile application performance, see usage statistics, and search device logs.  {{site.data.keyword.mobileanalytics_short}}  provides client SDKs for iOS 8+ (Swift only) and Android 4+.

With the {{site.data.keyword.mobileanalytics_short}} service you can:

<dl>
	<dt>Gain immediate insight</dt>
		<dd>See performance and usage metrics in real time.</dd>
	<dt>Implement in minutes</dt>
		<dd>Create a service instance in {{site.data.keyword.Bluemix}}, add the SDK to your project, paste two lines of code into your application and you are ready to collect dozens of pre-defined metrics.</dd>
	<dt>Collect any data you want</dt>
		<dd>Instrument apps with custom events, discover how users are interacting with your app, track purchases, and monitor app activity.  
</dd>
<dt>See metrics for all of your applications at-a-glance</dt>
	<dd>The {{site.data.keyword.mobileanalytics_short}} console offers <!-- both --> ready-made <!--and custom--> charts, without the need to write queries.</dd>
<dt>Focus on what is important to you</dt>
	<dd>Filter metrics by time, adapter, application, application version, OS, OS version, or device model.</dd>
<dt>Rapidly discover issues</dt>
	<dd>Monitor crash status. Set alert triggers on critical metrics and route alerts to any REST endpoint. </dd>
<dt>Troubleshoot to root cause</dt>
	<dd>Use custom logging in your application and automatically upload the logs and search them from the console. Drill down on crash events to see stack traces. </dd>
</dl>
 

## Using metrics and events
{: #usingmetrics}

With **pre-defined metrics** you can answer questions like:

* How many new users do I have?  
* How many people are actively using my application?  
* How frequently are people using my application? 
* What time of day are people using my application?  
* What device models do my users prefer? 
* When should I deprecate support for legacy operating systems? 
* Which applications are experiencing performance issues?  

By adding your own **custom events** you can answer questions like: 

* What features are used most and least?  
* Where are users entering and leaving my app?  
* What activities are users viewing most?  
* Are users completing workflows in the app (for example, conversion funnels)?   

Client-side logs and usage data are gathered automatically and sent to the Mobile Analytics service on demand. Developers and administrators can use the {{site.data.keyword.mobileanalytics_short}} service dashboard to view data that is gathered by the client SDK.

## Data visualization
{: data-visualization notoc}

All data that is collected by the analytics service can be visualized through the {{site.data.keyword.mobileanalytics_short}} dashboard which is accessible from your {{site.data.keyword.Bluemix_notm}} dashboard by clicking your IBM {{site.data.keyword.mobileanalytics_short}} service tile instance. <!--You can also create custom charts, based on data that is collected by the analytics service in the dashboard.--> In addition to an at-a-glance view of your mobile analytics, the analytics feature includes the capability to perform a raw search against client logs, captured client crash data, and any extra data that you explicitly provide through client API function calls that feed into the {{site.data.keyword.mobileanalytics_short}} service. 

# Related Links
{: #rellinks notoc}

## SDK
{: #sdk notoc}
<!-- Links to SDK download and SDK Developer Guide -->
* [Android SDK ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-core){: new_window} 
* [iOS SDK ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-core){: new_window}

