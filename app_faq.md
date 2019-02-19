---

copyright:
  years: 2015, 2017, 2018, 2019
lastupdated: "2019-02-19"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}


# Frequently Asked Questions 
{: #faq}


1. **What is {{site.data.keyword.mobileanalytics_full}}?**
	
	{{site.data.keyword.mobileanalytics_full}} is a service that provides real time and historical insight into how your mobile applicaitons are performing and being used. Using {{site.data.keyword.mobileanalytics_short}}, application developers and application owners can make data driven decisions by monitoring trends in active users, sessions, mobile platforms, and application crashes. You can also set alerts on selected metrics that, once triggered, sends messages to any REST endpoint, including a push service or your internal messaging services.


2. **What can I do with {{site.data.keyword.mobileanalytics_short}} for {{site.data.keyword.Bluemix_notm}}?**

	As a Mobile Application Product Manager, you can see how many people use your application (user metrics) and when they are using it (session metrics). This information is presented as a time series and updated in real time so you can see the effect of changes you make to your application. You can filter to see specific application versions or operating systems to make deprecation and prioritization decisions. 
	
	As a Mobile Application Marketer, you can use user and session metrics to monitor engagement, manage churn, and evaluate the effectiveness of mobile application marketing efforts by observing changes over time and correlating to your event dates.
	
	As a Mobile Application Developer, you can use crash metrics to discover and resolve mobile application performance issues before they frustrate users and damage the reputation of the application. You can monitor both crash count and crash rate from the analytics console, and you can prioritize crashes affecting the most users. You can set alerts to send notifications or take automated actions when crashes exceed a given threshold, and you can troubleshoot by drilling down on crash instances to see device logs and application stack traces.
	
	Ensure that you do not share any personal information using {{site.data.keyword.mobileanalytics_short}}.

3. **Do I need data analyst skills to use Mobile Analytics?**

	No, {{site.data.keyword.mobileanalytics_short}} offers a ready-to-use analytics console for business stakeholders and application developers. No query skills are required.

4. **Can I perform custom queries on my analytics data?**

    {{site.data.keyword.mobileanalytics_short}} does not allow custom queries, but there is consideration for this feature for the future.
	
5. **How do I connect my application to {{site.data.keyword.mobileanalytics_short}}?**

    [Download our open-source SDK for iOS or Android](/docs/services/mobileanalytics/install-client-sdk.html), or use the {{site.data.keyword.mobileanalytics_short}} [REST API](https://mobile-analytics-dashboard.ng.bluemix.net/analytics-service/) for other platforms. 

6. **In what IBM Cloud regions is Mobile Analytics available?**

    Currently, Mobile Analytics is available in the United States - South and the United Kingdom. Availability in other regions is planned, but the timeframe is not yet determined.

7. **How much does this service cost?**

    The first 100 million events that are collected each month are free, and thereafter, events cost $1 per million events.
	
8. **What is an event?**

    Currently reported events include application session start, application session end (including application crash), alert notifications, and log entries.
	
9. **How can I estimate how much the service will cost per month?**

    Because pricing depends on the number of events that are sent to the service per client account, estimating pricing means estimating events.  
	
	The price you are charged is the sum of events from all applications that you have connected to {{site.data.keyword.mobileanalytics_short}}. For a given application, the number of events depends on the degree of instrumentation that you have implemented within the application, the number of users, and how active the users are. 
	
	Use this formula to estimate usage:events per month per app = (users per day)(sessions per user per day)(days per month)(events per session)
	
	Events per session can vary widely from 2 to several hundred, depending on what network calls, custom analytics, log captures, and alert definitions the developer has configured into the application.

9. **How long is my analytics data kept?**

    Data is kept for at least 30 days.
	
10. **How long does it take for data to display in the {{site.data.keyword.mobileanalytics_short}} console?**

    Data in the {{site.data.keyword.mobileanalytics_short}} console is near-real-time, meaning that the data displays within seconds of the actual events.
	
11. **What is the difference between {{site.data.keyword.mobileanalytics_full}} and the mobile analytics found in MobileFirst Platform Foundation?**

    User and session are very similar in these two consoles, but analytics that come with MobileFirst Platform Foundation contains additional metrics and settings that allow clients to manage their own analytics cluster on-premises. Also, the MobileFirst Platform Foundation analytics console breaks out metrics for adapters and adapter procedures, whereas in the {{site.data.keyword.mobileanalytics_short}} service, these metrics are integrated into network request charts and tables.
	
12. **I am using MobileFirst Platform Foundation on premises to develop my apps, but I don't want to host my own analytics cluster. Can I use {{site.data.keyword.mobileanalytics_full}} instead?**

    Yes. You have a couple of options: If you are using MobileFirst Platform Foundation 7.x or 8.0 and your apps are instrumented with MobileFirst Platform SDKs, you can configure your MobileFirst server to report analtyics data to {{site.data.keyword.mobileanalytics_short}} for {{site.data.keyword.Bluemix_notm}}. You can instrument your apps using the {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.mobileanalytics_short}} SDK and report directly to the {{site.data.keyword.mobileanalytics_short}} service.