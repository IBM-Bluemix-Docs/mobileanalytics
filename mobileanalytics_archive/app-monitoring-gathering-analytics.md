---

copyright:
  years: 2015, 2016

---

# Gathering usage analytics
{: #usage-analytics}
Last updated: 29 March 2016*
{: .last-updated}

You can configure the {{site.data.keyword.mobileanalytics_short}} Client SDK to record usage analytics and send the recorded data to the {{site.data.keyword.mobileanalytics_short}} service.

**Note:** Make sure that you set up the [{{site.data.keyword.mobileanalytics_short}} Client SDK](sdk.html) before you use the logging framework.


Use the following APIs to start recording and sending usage analytics:

  * Android
<!--// Initialize the Analytics SDK:-->
<!--MFPAnalytics.init(Application app, String applicationName, String clientApiKey, DeviceEvent... contexts)-->

    ```Java
      // Disable recording of usage analytics (for example, to save disk space)
      MFPAnalytics.disable();

      // Enable recording of usage analytics
      MFPAnalytics.enable();

      // Log a custom analytics event for custom charts, which is represented by a JSON object:
      JSONObject eventJSONObject = new JSONObject();

      eventJSONObject.put("customProperty" , "propertyValue");

      MFPAnalytics.log(eventJSONObject);

      // Send recorded usage analytics to the Mobile Analytics Service
      MFPAnalytics.send();
      ```

  * iOS - Swift

      ```Swift
        // Disable recording of usage analytics (for example, to save disk space)
        Analytics.enabled = false

        // Enable recording of usage analytics
        Analytics.enabled = true

        // Log a custom analytics event for custom charts
        let eventObject = ["customProperty": "propertyValue"]
        Analytics.log(eventObject)

        // Send recorded usage analytics to the {{site.data.keyword.mobileanalytics_short}} Service
        Analytics.send()
        ```

<!--Removing Cordova for experimental-->
<!--### Cordova-->
<!--{: #usage-analytics-cordova}-->

<!--```JavaScript-->
<!--// Enable usage analytics recording-->
<!--MFPAnalytics.enable();-->

<!--// Send recorded usage analytics to the {{site.data.keyword.mobileanalytics_short}} Service-->
<!--MFPAnalytics.send();-->
<!--```-->
<!--**Note:** When you are developing Cordova applications, use the native API to enable application lifecycle event recording.-->

## Tracking users
{: trackingusers}
You can track how many users are actively using your application by passing the user name of the active user to MFPAnalytics.

  * Android

  Add the following code when the user logs in:
  ```Java
    MFPAnalytics.setUserIdentity("username");
    ```

  Add the following code when the user logs out:  
  ```Java
    MFPAnalytics.clearUserIdentity();
    ```

  * iOS - Swift

    Add the following code when the user logs in:
    ```Swift
      Analytics.userIdentity = "username"
      ```

    Add the following code when the user logs out:  
    ```Swift
      Analytics.userIdentity = nil
      ```



## Next steps
{: #next-steps}

* Launch the MobileFirst Analytics Console to view usage analytics:
  * [Create custom charts](custom_charts/c_op_analytics_custom_charts.html)
  * [Create alerts](alerts/c_op_analytics_alerts.html)
  * Troubleshoot your apps with [app crash](app_crash/c_op_analytics_crashes.html) data

# rellinks

## SDK
* [Android SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-core){: new_window}  
* [iOS SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-core){: new_window}
