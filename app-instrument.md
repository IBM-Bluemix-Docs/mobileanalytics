---

copyright:
 years: 2017, 2018, 2019

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Instrument your app
{: #Instrument-your-app}
Last updated: 19 February 2019
{: .last-updated}

##Initialize the {{site.data.keyword.mobileanalytics_short}} Client SDK 

Initialize the {{site.data.keyword.mobileanalytics_short}} Client SDK in your application code to record usage analytics and application sessions, using your [API Key](/docs/services/mobileanalytics/sdk.html#analytics-clientkey) value.	
	
- **Android**
	
```
		BMSClient.getInstance().initialize(getApplicationContext(), BMSClient.REGION_US_SOUTH); // You can change the region
		Analytics.init(getApplication(), "your_app_name_here", "your_api_key_here", hasUserContext, collectLocation, Analytics.DeviceEvent.ALL);
```
		{: codeblock}
	    
The **bluemixRegion** parameter specifies which {{site.data.keyword.Bluemix_notm}} deployment you are using, for example, `BMSClient.REGION_US_SOUTH` and `BMSClient.REGION_UK`. 
	    
	    
Set the value for `hasUserContext` to **true** or **false**. If false (default value), each device is counted as an active user.
		
Set the value for `collectLocation` to **true** or **false**. If true the device location data will be sent as part of the Appsession log. 

- **iOS**
	  
Initialize the Client SDK inside your application code to record usage analytics and application sessions, using your [API Key](/docs/services/mobileanalytics/sdk.html#analytics-clientkey) value.
		
```Swift
		BMSClient.sharedInstance.initialize(bluemixRegion: BMSClient.Region.usSouth) // You can change the region
		Analytics.initialize(appName: "your_app_name_here", apiKey: "your_api_key_here", hasUserContext: false, collectLocation: true, deviceEvents: deviceEvents: .lifecycle, .network)
```
		{: codeblock}
				
The **bluemixRegion** parameter specifies which IBM Cloud deployment you are using, for example, `BMSClient.Region.usSouth` or `BMSClient.Region.unitedKingdom`.
		
	 
Set the value for `hasUserContext` to **true** or **false**. If false (default value), each device is counted as an active user.
		
Set the value for `collectLocation` to **true** or **false**. If true the device location data will be sent as part of the Appsession log. 
	
- **Cordova**
		
Initialize the Client SDK inside your application code to record usage analytics and application sessions, using your [API Key](/docs/services/mobileanalytics/sdk.html#analytics-clientkey) value.
		
```
		var appName = "your_app_name_here";
		var apiKey = "your_api_key_here";
		BMSClient.initialize(BMSClient.REGION_US_SOUTH); // You can change the region
		BMSAnalytics.initialize(appName, apiKey, hasUserContext, collectLocation, [BMSAnalytics.ALL])
```
		{: codeblock}
		
The **bluemixRegion** parameter specifies which IBM Cloud deployment you are using, for example, `BMSClient.REGION_US_SOUTH` or `BMSClient.REGION_UK`.
		
Set the value for `hasUserContext` to **true** or **false**. If false (default value), each device is counted as an active user.
		
Set the value for `collectLocation` to **true** or **false**. If true the device location data will be sent as part of the Appsession log.
    
- **Web**
		
Initialize the Client SDK inside your application code to record usage analytics and application sessions, using your [API Key](/docs/services/mobileanalytics/sdk.html#analytics-clientkey) value.
		
```
		var appName = "your_app_name_here";
		var apiKey = "your_api_key_here";
		BMSAnalytics.Client.initialize(BMSAnalytics.Client.REGION_US_SOUTH);
		BMSAnalytics.initialize(appName,apiKey,hasUserContext,BMSAnalytics.DeviceEvents.ALL,instanceId);
``` 
		{: codeblock}

The `bluemixRegion` parameter specifies which {{site.data.keyword.Bluemix_notm}} deployment you are using. Set the value for `hasUserContext` to `true` or `false`. If false (default value), each device is counted as an active user.Set the `instanceId` to your service instanceId, its a alphanumeric string which you get from the browser url for your service instance after the string "...mobile-analytics_Prod/"  and upto "/". 

**Note** : The name that you select for your application (`your_app_name_here`) displays in the {{site.data.keyword.mobileanalytics_short}} console as the application name. The application name is used as a filter to search for application logs in the dashboard. When you use the same application name across platforms (for example, Android and iOS), you can see all logs from that application under the same name, regardless of which platform the logs were sent from.

##Send App Data to the {{site.data.keyword.mobileanalytics_short}} service

Send recorded usage analytics to the {{site.data.keyword.mobileanalytics_short}} service. A simple way to test your analytics is to run the following code when your application starts:


- **Android**
	
Use the `Analytics.send()` method to send analytics data to the server. You can place the `Analytics.send()` method anywhere in the `onCreate` method of the main activity in your Android application, or in a location that works best for your project. 
	
You can insert `Analytics.send()` anywhere.
	
- **iOS**
	
Use the `Analytics.send` method to send analytics data to the server. You can place the `Analytics.send` method anywhere in the `application(_:didFinishLaunchingWithOptions:)` method of your application delegate, or in a location that works best for your project. 
	
- **Cordova**
		
Use the `BMSAnalytics.send` method to send analytics data to the server. Place the `BMSAnalytics.send` method in a location that works best for your project.
		
- **Web**
		
Use the `BMSAnalytics.send` method to send analytics data to the server. Place the `BMSAnalytics.send` method in a location that works best for your project. 
		



Go through the [Instrumenting your application](/docs/services/mobileanalytics/sdk.html) topic to learn about additional {{site.data.keyword.mobileanalytics_short}} capabilities, such as [logging](/docs/services/mobileanalytics/sdk.html#app-monitoring-logger), [network requests](/docs/services/mobileanalytics/sdk.html#network-requests), [location logging](/docs/services/mobileanalytics/sdk.html#location-logging) and [crash analytics](/docs/services/mobileanalytics/sdk.html#report-crash-analytics).


Your next step is to **Compile and run the application on your emulator or device**.