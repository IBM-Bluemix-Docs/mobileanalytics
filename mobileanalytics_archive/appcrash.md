---

copyright:
  years: 2015, 2016

---

# App crashes
{: #monitor-app-crash}
Last updated: 6 April 2016*
{: .last-updated}

You can view information about your app crashes in the MobileFirst Analytics Console to better monitor and troubleshoot your apps.
{: #shortdesc}

Learn more about monitoring and troubleshooting your app crashes.

## App crash monitoring
{: #app-crash}

You can quickly see information about your app crashes in the **Dashboard** section of the IBM MobileFirst™ Analytics Console.

In the **Overview** page of the **Dashboard** section, the **Crashes** bar graph shows a histogram of crashes over time.

You can display data in two ways:

1. Display crash rate: crash rate over time
2. Display total crashes: total crashes over time


## App crash troubleshooting
{: #app-crash-troubleshooting}

You can view the **Crashes** page in the **Applications** section of the IBM MobileFirst Analytics Console to better administer your apps.

The **Crash Overview** table shows the following data columns:

* App: app name
* Crashes: total number of crashes for that app
* Total Uses: total number of times a user opens and closes that app
* Crash Rate: percentage of crashes per use

The **Crash Summary** table is sortable and includes the following data columns:

* Crashes
* Devices
* Last Crash
* App
* OS
* Message

You can click on the + icon next to any entry to display the **Crash Details** table, which includes the following columns:

* Time Crashed
* App Version
* OS Version
* Device Model
* Device ID
* Download: link to download the logs that led up to the crash

You can expand any entry in the **Crash Details** table to get more details, including a stacktrace.

**Note**: The data for the **Crash Summary** table is populated by querying the fatal level client logs. If your app does not collect fatal client logs, no data is available.
