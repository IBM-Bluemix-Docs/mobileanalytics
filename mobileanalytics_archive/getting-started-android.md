---

copyright:
  years: 2015, 2016

---
# Setting up the Android SDK
{: #getting-started-android}

The {{site.data.keyword.mobileanalytics_full}} SDK allows you to instrument your mobile application.

## Before you begin
{: #before-you-begin}
<!--You must have an instance of the {{site.data.keyword.mobileanalytics_short}} service. For more information, see --> <!-- [Getting started](app-monitoring-start.html). -->
Set up Android Studio. To learn how to set up your Android development environment, see [Google Developer Tools](http://developer.android.com/sdk/index.html).

## Identifying your Client Key value
{: #analytics-clientkey}

Before you set up the Client SDK, identify your **Client Key** value, as follows:
1. Open your {{site.data.keyword.mobileanalytics_short}} service dashboard.
2. Click the wrench icon to open the API Keys tab.
3. In the API Keys tab, note the Client Key value.


## Installing the {{site.data.keyword.mobileanalytics_short}} Client SDK
{: #install-ma-sdk}

The {{site.data.keyword.mobileanalytics_short}} Client SDK is distributed with Gradle, a dependency manager for Android projects. Gradle automatically downloads artifacts from repositories and makes them available to your Android application.

1. Create an Android Studio project or open an existing project.

1. Add the Maven central snapshot repository to your `build.gradle` file that is in your project. This file is not the `build.gradle` file in your application module.
	```
	allprojects {
    repositories {
        jcenter()
        maven {
            url 'https://oss.sonatype.org/content/repositories/snapshots/'
        }
    }
}
	```

1. Open the `build.gradle` file that is in your application module.
**Tip**: Your Android project might have two `build.gradle` files: one for the project and one for the application module. Use the application module file.

1. Find the **Dependencies** section of the `build.gradle` file. Add a compile dependency for the {{site.data.keyword.mobileanalytics_short}} Client SDK:

	```Gradle
	dependencies {
		compile group: 'com.ibm.mobilefirstplatform.clientsdk.android',    
        name:'analytics',
        version: '2.+',
        ext: 'aar',
        transitive: true
    	// other dependencies  
}
```

1. Synchronize your project with Gradle. Click **Tools &gt; Android &gt; Sync Project with Gradle Files**.

1. Open the `AndroidManifest.xml` file for your Android project. Add internet access permission under the `<manifest>` element:

	```XML
	<uses-permission android:name="android.permission.INTERNET" />
```

## Initializing the {{site.data.keyword.mobileanalytics_short}} Client SDK
{: #initalize-ma-sdk}

To use the {{site.data.keyword.mobileanalytics_short}} Client SDK, you must initialize the `BMSClient` with the **bluemixRegionSuffix** parameter. In the initializer, the **bluemixRegionSuffix** value specifies which Bluemix deployment you are using. You can set this value with a `BMSClient.REGION` static property. You can optionally pass the **applicationGUID** and **applicationRoute** values if you are using another Bluemix service that requires these values, otherwise you can pass empty strings.

1. Initialize the {{site.data.keyword.mobileanalytics_short}} Client SDK in your Android application. A common, though not mandatory, place to put the initialization code is in the `onCreate` method of the main activity in your Android application.

	```Java
	BMSClient.getInstance().initialize(getApplicationContext(),
					"your_applicationRoute", // You can pass an empty string if you do not have a value
					"your_applicationGUID", // You can pass an empty string if you do not have a value
					BMSClient.REGION_US_SOUTH); // Make sure you are pointing to your region
```

3. Initialize MFPAnalytics by using your Android application object and giving it your application’s name. You also need the [**Client Key**](#analytics-clientkey) value.

```Java
MFPAnalytics.init(getApplication(), "my_app", apiKey, MFPAnalytics.DeviceEvent.LIFECYCLE);
//In this code example, MFPAnalytics is configured to record lifecycle events.
```

**Tip:** The application name is used as a filter to search for client logs in the dashboard. By using the same application name across platforms (for example, Android and iOS), you can see all logs from that application under the same name, regardless of which platform the logs were sent from.

## Next steps
{: #next-steps}

Learn about [app monitoring](app-monitoring.html).
