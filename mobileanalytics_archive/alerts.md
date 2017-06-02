---

copyright:
  years: 2015, 2016

---

# Setting alerts
{: #alerts}
Last updated: 5 April 2016*
{: .last-updated}

You can set thresholds in alert definitions in the MobileFirst Analytics Console to better monitor your activities.
{: #shortdesc}

You can configure thresholds, which if exceeded, trigger alerts to notify the MobileFirst Analytics Console monitor. The triggered alerts can be visualized on the console, or the alerts can be handled by a custom webhook. This feature provides a proactive means of detecting client log errors, server log errors, extended periods of network latency, and authentication failures. Reactive thresholds and alerts keep you from having to sift through your data and set thresholds at a wide spectrum of granularity.

## Creating an alert definition for client logs
{: #alert-def-client-logs}

You can create an alert definition that is based on client logs.

In this example, you use client log data to create an alert definition. The alert monitors all client logs that were received in the last 5 minutes, and continues to check every 5 minutes, until the alert definition is disabled or deleted. An alert is triggered for each device that sent 3 or more client error logs with the same app name and version.

1. In the MobileFirst Analytics Console, click the bell icon to go to the **Alert Log** page.
2. Go to the **Alert Management** page and click Create **Alert**.
3. Provide the following values:
	* Alert Name: Alert for client logs
	* Message: Error Message Alert
	* Query Frequency: 5 minutes
	* Event Type: Client Logs
		* Property: Log Level
			* Value: Error
			* Threshold
				* Threshold Type: Total for Application Instance

					Note: If you choose the Average for Application option, the client logs are averaged by the number of devices. For example, if you have two devices, 					and one device sends six client logs while the other device sends three client logs, the average is 4.5 client logs.
				* Operator: is greater than or equals 3
	<!-- insert alert definition tab image? -->

4. Click **Next** or the **Distribution Method** tab, and provide the following value:
	* Method: Analytics Console Only

		Note: Choose the Analytics Console and Network Post option if you want to additionally send a POST message with a JSON payload to your customized URL. The following fields are available if you choose this option:
		* Network Post URL
        * Headers
        * Authentication Type
5. Click **Save**.

You created an alert definition to trigger an alert at the end of each 5 minute interval if the number of client logs reached your threshold of 3 or more error logs.

## Creating an alert definition for app crashes
{: #alert-def-app-crash}

You can create an alert definition based on app crashes.

In this example, you use app crash data to create an alert definition. The alert monitors all app crashes in the last 2 minutes, and continues to check every 2 minutes, until the alert definition is disabled or deleted. An alert is triggered for each app that crashed 5 or more times. For more information about app crashes, see [App crashes](app_crash/c_op_analytics_crashes.html).

1. In the MobileFirst Analytics Console, click the **Alerts** icon. This action brings up the Alert Log page.
2. Click the **Alert Management** tab and click **Create Alert**.
3. Provide the following values:
	* Alert Name: Alert for App Crashes
	* Message: App Crash Alert
	* Query Frequency: Application Crashes
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

## Managing Alert definitions
{: #managing-alert-definitions}

In this example, you manage your alert definitions from the Alert Management page.

1. In the MobileFirst Analytics Console, click the **Alerts** icon. This action opens the Alert Log page.
2. Click the **Alerts Management** tab.
3. Optional: Toggle the check-box under the **Enabled** column to enable or disable a specific alert definition.
4. Optional: Click the **Duplicate** icon if you want to create a copy of an alert definition and change some values.
5. Optional: Click the **Pencil** icon if you want to edit an alert definition.
6. Optional: Click the **Trash** icon if you want to delete an alert definition.

## Viewing alert details
{: #viewing-alert-details}

In this example, you view the details of your triggered alerts from the Alert Log page.

1. In the MobileFirst Analytics Console, click the **Alerts** icon. This action brings up the Alert Log page.
2. Click the **+** icon for any of the alerts. This action displays the **Alert Definition** and **Alert Instances** sections.

    **Note**: If the corresponding alert definition was not deleted or modified, you can edit the alert definition by clicking **Edit Alert**. Otherwise, the **Edit Alert** button is unavailable and the following message displays:

    `This alert definition has since been modified or deleted.`

3. Optional: Select an alert and click the **Trash** icon to delete the alert.
