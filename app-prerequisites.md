---

copyright:
 years: 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Prerequisites
{: #prerequisites}
Last updated: 18 January 2018
{: .last-updated}


## Creating a Mobile Analytics service instance
{: #prerequisites_1}

1. In the [IBM Cloud Catalog](https://console.ng.bluemix.net/catalog/), click **Mobile** > **Mobile Analytics**.
2. Provide a Service name.
3. Click **Create**.
4. Choose to connect to other existing apps, or leave it unbound.


You can choose to create either a bound service or an unbound service. Bound services are connected to other IBM Cloud apps, while unbound services are standalone and not connected to other apps. 

## Initializing your app
{: #prerequisites_app}

Import and install the {{site.data.keyword.mobileanalytics_short}} Client SDKs. You can optionally use the {{site.data.keyword.mobileanalytics_short}} [REST API ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://mobile-analytics-dashboard.{DomainName}/analytics-service/){:new_window}.


###Import the Client SDKs

[Import the Client SDKs](/docs/services/mobileanalytics/available-client-sdk.html) and [initialize](/docs/services/mobileanalytics/install-client-sdk.html) them with the following code snippet to record usage analytics:

- **Android**
	
    Add the following `import` statements to the beginning of your project file:
		
	```
		import com.ibm.mobilefirstplatform.clientsdk.android.core.api.*;
		import com.ibm.mobilefirstplatform.clientsdk.android.analytics.api.*;
		import com.ibm.mobilefirstplatform.clientsdk.android.logger.api.*;
	```
    {: codeblock}

- **iOS**

    The Swift SDK is available for iOS and watchOS.
		
    Import the `BMSCore` and `BMSAnalytics` frameworks by adding the following `import` statements to the beginning of your `AppDelegate.swift` project file:
	
	```Swift
		import BMSCore
		import BMSAnalytics
	```
    {: codeblock}
   
- **Cordova**
			
    Add the Cordova plugin by running the following command from your Cordova application root directory:
	
	```Javascript
		cordova plugin add bms-core
	```
    {: codeblock}
   
- **Web**
	
    Add the web plugin by either adding this script in the `index.html` file of web app:
	
	```Html
		<script src="bms-clientsdk-web-analytics/bmsanalytics.js"></script>
	```
    {: codeblock}

    Or by using module loader requirejs. The name used as reference API is same as the argument name (`BMSAnalytics`) used. 
	
	 ```Javascript
	 	require.config({
	    'paths': {
	        'bmsanalytics': 'bms-clientsdk-web-analytics/bmsanalytics'
	    	}
		});
			require(['bmsanalytics'], function(BMSAnalytics) {
		    BMSAnalytics.send();
		}
	```
    {: codeblock}
		
		
Your next step is to [Instrument your app](app-instrument.html) .


