---

copyright:
  years: 2015, 2017, 2019
lastupdated: "2019-02-19"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Setting alerts
{: #setting-alerts}

## Setting alerts with Mobile Analytics 
{: #setting-alerts-with-mobile-analytics}

You can set thresholds in alert definitions in the {{site.data.keyword.mobileanalytics_short}} console to better monitor your activities.

You can configure thresholds, which if exceeded, trigger alerts to notify the {{site.data.keyword.mobileanalytics_short}} console monitor. The triggered alerts can be visualized on the console, or the alerts can be handled by a custom webhook. This feature provides a proactive means of detecting application log errors and application crashes server log errors. Reactive thresholds and alerts keep you from having to sift through your data and set thresholds at a wide spectrum of granularity.

## Creating an alert definition for application logs
{: #alert-def-client-logs notoc}

You can create an alert definition that is based on application logs.

In this example, you use application log data to create an alert definition. The alert monitors all application logs that were received in the last 5 minutes, and continues to check every 5 minutes, until the alert definition is disabled or deleted. An alert is triggered for each device that sent 3 or more application error logs with the same application name and version.

1. In the {{site.data.keyword.mobileanalytics_short}} console, click **Definitions** to go to the Alert Definitions page.
2. Click **Create Alert** to create an alert.
3. Provide the following values:
	* Alert Name: Alert for app logs
	* Message: Error Message Alert
	* Query Frequency: 5 minutes
	* Event Type: App Logs
		* Property: Log Level
			* Value: Error
			* Threshold
				* Threshold Type: Total for Application Instance

					**Note**: If you choose the Average for Application option, the app logs are averaged by the number of devices. For example, if you have two devices, and one device sends six app logs while the other device sends three app logs, the average is 4.5 app logs.
				* Operator: is greater than or equals 3
	<!-- insert alert definition tab image? -->

4. Click **Next** and provide the following value:
	* Method: Analytics Console Only

		**Note**: Choose the Analytics Console and Network Post option if you want to additionally send a POST message with a JSON payload to your customized URL. The following fields are available if you choose this option:
		* Network Post URL
        * Headers
        * Authentication Type
5. Click **Save**.

You created an alert definition to trigger an alert at the end of each 5 minute interval if the number of app logs reached your threshold of 3 or more error logs.

## Creating an alert definition for application crashes
{: #alert-def-app-crash notoc}

You can create an alert definition based on application crashes.

In this example, you use application crash data to create an alert definition. The alert monitors all application crashes in the last 2 minutes, and continues to check every 2 minutes, until the alert definition is disabled or deleted. An alert is triggered for each application that crashed 5 or more times. For more information about application crashes, see [Application crashes](/docs/services/mobileanalytics/app-monitoring-crash.html).

1. In the {{site.data.keyword.mobileanalytics_short}} console, click **Definitions** to display the Alerts Definitions page.
2. Click **Create Alert**.
3. Provide the following values:
	* Alert Name: Alert for Application Crashes
	* Message: App Crash Alert
	* Query Frequency: Application Crashes
		* Query Frequency: 2 minutes
	* Event Type: Application Crashes
		* Application Name: Any application
		* Application Version: Any version
    * Threshold
      * Threshold Type: Crash Count
      * Operator: is greater than or equals 5
4. Click the **Distribution Method** tab, and provide the following value:
  * Method: Analytics Console Only

    **Note**: Choose the **Analytics Console and Network Post** option if you want to additionally send a POST message with a JSON payload to your customized URL. The following fields are available if you choose this option:
      * Network Post URL (required)
      * Headers (optional)
      * Authentication Type (required)
5. Click **Save**.

## Managing alert definitions
{: #managing-alert-definitions notoc}

In this example, you manage your alert definitions from the Alert Management page.

1. In the {{site.data.keyword.mobileanalytics_short}} console, click **Logs**. This action opens the Alert Logs page.
2. Optional: Toggle the check-box under the **Enabled** column to enable or disable a specific alert definition.
3. Optional: Click the **Duplicate** icon if you want to create a copy of an alert definition and change some values.
4. Optional: Click the **Pencil** icon if you want to edit an alert definition.
5. Optional: Click the **Trash** icon if you want to delete an alert definition.

## Viewing alert details
{: #viewing-alert-details notoc}

In this example, you view the details of your triggered alerts from the Alert Log page.

1. In the {{site.data.keyword.mobileanalytics_short}} console, click **Logs**. This action brings up the Alert Log page.
2. Click the **+** icon for any of the alerts. This action displays the **Alert Definition** and **Alert Instances** sections.

    **Note**: If the corresponding alert definition was not deleted or modified, you can edit the alert definition by clicking **Edit Alert**. Otherwise, the **Edit Alert** button is unavailable and the following message displays:

    `This alert definition has since been modified or deleted.`

3. Optional: Select an alert and click the **Trash** icon to delete the alert.

