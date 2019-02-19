---

copyright:
  years: 2015, 2017, 2019
lastupdated: "2019-02-19"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Monitoring application crashes
{: #monitor-app-crash}

You can view information about your application crashes in the {{site.data.keyword.mobileanalytics_short}} console to better monitor and troubleshoot your applications.

## Application crash monitoring
{: #app-crash notoc}

On the **Crashes** page, The **Crash Overview** table shows the following data columns:

* Application: application name
* Crashes: total number of crashes for that app
* Total Uses: total number of times a user opens and closes that app
* Crash Rate: percentage of crashes per use

You can quickly see information about your application crashes the **Crashes** table. <!--In the **Overview** page of the **Dashboard** section,--> The **Crashes** bar graph shows a histogram of crashes over time.

You can display crash data in two ways:

1. Display crash rate: crash rate over time
2. Display total crashes: total crashes over time

## App crash troubleshooting
{: #app-crash-troubleshooting notoc}

The **Troubleshooting** page in the <!-- **Applications** section of the --> {{site.data.keyword.mobileanalytics_short}} console offers a granular view of your app crashes, using the **Crash Summary** table.

The **Crash Summary** table is sortable and includes the following data columns:

* Crashes
* Devices
* Last Crash
* Application
* OS
* Message

Click the + icon next to any entry to display the **Crash Details** table, which includes the following columns:

* Time Crashed
* Application Version
* OS Version
* Device Model
* Device ID
* Download: link to download the logs that led up to the crash

Expand any entry in the **Crash Details** table to get more details, including a stacktrace.

**Note**: The data for the **Crash Summary** table is populated by querying the fatal level app logs. If your application does not collect fatal application logs, no data is available.
