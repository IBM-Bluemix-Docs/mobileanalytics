---

copyright:
  years: 2015, 2017, 2019
lastupdated: "2019-02-19"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

#Install the SDK
{: #install-the-sdk}

## Install the {{site.data.keyword.mobileanalytics_short}} Client SDKs

The {{site.data.keyword.mobileanalytics_short}}
Client SDKs are currently available for Android, iOS, WatchOS, Cordova and Web.
{: shortdesc}

## Installing the Android Client SDK
{: #install-sdk-android}

[![Maven Central](https://maven-badges.herokuapp.com/maven-central/com.ibm.mobilefirstplatform.clientsdk.android/analytics/badge.svg)](https://maven-badges.herokuapp.com/maven-central/com.ibm.mobilefirstplatform.clientsdk.android/analytics)

The {{site.data.keyword.mobileanalytics_short}} Client SDK is distributed with Gradle, a dependency manager for Android projects. Gradle automatically downloads artifacts from repositories and makes them available to your Android application.

1. Create an [Android Studio ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://developer.android.com/sdk/index.html){: new_window} project or open an existing project.

2. Open the `build.gradle` file that is in your **app module**.

  **Tip**: Your Android project might have two `build.gradle` files: one for the project and one for the app module. Make sure to use the **app module** file.

3. Find the `Dependencies` section of the `build.gradle` file and add a compile dependency for the {{site.data.keyword.mobileanalytics_short}} Client SDK. Your repositories statement should be similar to the following code example:

	```
      dependencies {
        compile 'com.ibm.mobilefirstplatform.clientsdk.android:analytics:1.+'
        compile 'com.google.android.gms:play-services-location:10.0.1'
    	// other dependencies  
      }
  	```
  	{: codeblock}
	
	The first dependency is for the Mobile Analytics Service clientsdk and the second one is for the client-side location logging. The second dependency is only required if you enable the client side location collection.
    	

4. Synchronize your project with Gradle by clicking **Tools &gt; Android &gt; Sync Project with Gradle Files**.

5. Open the `AndroidManifest.xml` file for your Android project. You can find this file in **app > manifests**. Add internet access and location access permission under the `<manifest>` element:

	```
	 <uses-permission android:name="android.permission.INTERNET" />
	 <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION"/>
	 <uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION"/>
	```
   If you're using sdk version greater than >= 1.2  then you need to put this below part under the `<application>` element of the `AndroidManifest.xml` file.
   	
    ```
	 <activity
            android:name="com.ibm.mobilefirstplatform.clientsdk.android.ui.UIActivity"
            android:label="@string/app_name"
            android:launchMode="singleTask">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
	```
   	{: codeblock}
   

You have now installed the Android Client SDK. Next, [import and initialize](/docs/services/mobileanalytics/sdk.html#initalize-ma-sdk) the Analytics Client SDK.   

## Installing the Swift SDK
{: #installing-sdk-ios}

![CocoaPods Compatible](https://img.shields.io/cocoapods/v/BMSAnalytics.svg)

The {{site.data.keyword.mobileanalytics_full}} SDK enables you to instrument your mobile application. The Swift SDK is available for iOS and watchOS.

### Before you begin
{: #before-you-begin-ios notoc}

Make sure that you correctly set up Xcode. To learn how to set up your iOS development environment, see the [Apple Developer website ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.apple.com/support/xcode/){: new_window}. Read about the [Xcode requirements ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-analytics/tree/development#requirements){: new_window} for Client SDK Swift Analytics.

#### Enable Location API 
To enable the location API correct working you need to add a property in Info.plist file in the project folder of your app i.e.  `Privacy - Location Usage Description`  and as value give proper justification to adding the location API as "The app requires location service to be enabled" or so .

The {{site.data.keyword.mobileanalytics_short}} SDK is distributed with [CocoaPods ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cocoapods.org/){: new_window} and [Carthage ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/Carthage/Carthage#getting-started){: new_window}, which are dependency managers for Cocoa projects. CocoaPods and Carthage automatically download artifacts from repositories and makes them available to your application. Select CocoaPods or Carthage:

#### CocoaPods
{: #cocoapods notoc}

1. Follow the [{{site.data.keyword.Bluemix_notm}} Mobile Services Swift SDK instructions ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-analytics/tree/development#cocoapods){: new_window} on GitHub to install `BMSAnalytics` using Cocoapods and add it to your Podfile. 
	
2. After you have installed the iOS Client SDK,  [import and initialize](/docs/services/mobileanalytics/sdk.html#initalize-ma-sdk) the Analytics Client SDK.   

#### Carthage
{: #carthage notoc}

If you are not using using CocoaPods, you can add frameworks to your project using [Carthage ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/Carthage/Carthage#if-youre-building-for-ios-tvos-or-watchos){: new_window}.

1. Follow the [Carthage installation instructions ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-analytics/tree/development#carthage){: new_window} on GitHub to install `BMSAnalytics`.

2. After you have installed the iOS Client SDK, [import and initialize](/docs/services/mobileanalytics/sdk.html#initalize-ma-sdk) the Analytics Client SDK.


## Installing the Cordova plugin
{: #installing-sdk-cordova}

The {{site.data.keyword.mobileanalytics_full}} Cordova plugin enables you to instrument your mobile application. 

1. Create a [Cordova ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://cordova.apache.org/#getstarted){: new_window} project or open an existing project.

2. Add Android and iOS platforms to your Cordova application. Run one or both of the following commands from the command line. Currently, Cordova-CLI V6.3.0 or earlier is supported:
   
   Android:

	 ```
	 cordova platform add android@5.2.2
	 ```
	 {: codeblock}
	
   iOS:
   	
	```
	cordova platform add ios
	```
   {: codeblock}
	
3. If you added the Android platform, you must add the minimum supported API level to the `config.xml` file of your Cordova application. Open the `config.xml` file and add the following line to the `<platform name="android">` element:

	```
	<platform name="android">  
  	 <preference name="android-minSdkVersion" value="15"/>
  	 <preference name="android-targetSdkVersion" value="23"/>
  	 <!-- add minimum and target Android API level declaration -->
  	</platform>
	```
   {: codeblock}

 The *minSdkVersion* value must be version `15` or higher. Refer to the [Android Platform Guide ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cordova.apache.org/docs/en/latest/guide/platforms/android/){: new_window} to stay current with the supported *targetSdkVersion* for the Android SDK.

4. If you added the iOS operating system, update the `<platform name="ios">` element with a target declaration:

	```
	<platform name="ios">
    <preference name="deployment-target" value="8.0"/>
     <!-- add deployment target declaration -->
  	</platform>
	```
	{: codeblock}

5. Add the `bms-core` plugin.
 	
	 ```
	 cordova plugin add bms-core
	 ```
	 {: codeblock}

6. Verify that the plugin installed successfully by running the following command:
	
	```
	cordova plugin list
	```
	{: codeblock}
	
7. [Configure your Android and iOS environment ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.npmjs.com/package/bms-core#4-configuring-your-platform){: new_window}.

8. You have now installed the Cordova plugin and configured your environments. Next, [import and initialize](/docs/services/mobileanalytics/sdk.html#initalize-ma-sdk) the Analytics Client SDK.

#### Location Service Enablement ahead of cordova bms-core plugin version (>2.4.+).
9. For Cordova-ios app to enable the location API correct working you need to add a property in Info.plist file in the project folder of your app i.e.  `Privacy - Location Usage Description`  and as value give proper justification to adding the location API as "The app requires location service to be enabled" or so .

10. For Cordova-android app to enable the location API correct working put the following  in app AndroidManifest.xml file. 
	```
	 <uses-permission android:name="android.permission.INTERNET" />
	 <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION"/>
	 <uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION"/>
	```
	{: codeblock}
	
   Then you need to put this below part under the `<application>` element of the `AndroidManifest.xml` file.
   	```
	 <activity
            android:name="com.ibm.mobilefirstplatform.clientsdk.android.ui.UIActivity"
            android:label="@string/app_name"
            android:launchMode="singleTask">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
	```
	{: codeblock}
	

## Installing the Web plugin
{: #web-sdk-cordova}

The {{site.data.keyword.mobileanalytics_full}} SDK enables you to instrument your web application.

1. Make sure that you have a web server and a browser setup (eg. Chrome, Firefox) .
2. Create a new web app or use a existing one and put this [WebSDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-web-analytics/) within you project to be accessed by the app code . 
3. Add the web plugin by either adding this script in the `index.html` file of web app:
	
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
	  ```
	{: codeblock}




## Related Links
{: #rellinks notoc}

### SDK
{: #sdk notoc}
* [Android SDK ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-analytics){: new_window}  
* [iOS SDK ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-analytics){: new_window}
* [Cordova Plugin Core SDK ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.npmjs.com/package/bms-core){: new_window}
* [Web SDK![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-web-analytics/){: new_window}

## API Reference
{: #api notoc}
* [REST API ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://mobile-analytics-dashboard.ng.bluemix.net/analytics-service/){:new_window}
