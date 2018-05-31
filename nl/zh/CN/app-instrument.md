---

copyright:
 years: 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 检测应用程序
{: #Instrument}
上次更新时间：2018 年 1 月 18 日
{: .last-updated}

##初始化 {{site.data.keyword.mobileanalytics_short}} 客户端 SDK 

使用 [API 密钥](/docs/services/mobileanalytics/sdk.html#analytics-clientkey)值在应用程序代码内部初始化 {{site.data.keyword.mobileanalytics_short}} 客户端 SDK，以记录使用情况分析和应用程序会话。	
	
- **Android**
	
```
		BMSClient.getInstance().initialize(getApplicationContext(), BMSClient.REGION_US_SOUTH); // 您可以更改区域
		Analytics.init(getApplication(), "your_app_name_here", "your_api_key_here", hasUserContext, collectLocation, Analytics.DeviceEvent.ALL);
```
		{: codeblock}
	    
**bluemixRegion** 参数指定您使用的是哪一个 {{site.data.keyword.Bluemix_notm}} 部署，例如 `BMSClient.REGION_US_SOUTH` 和 `BMSClient.REGION_UK`。 
	    
	    
将 `hasUserContext` 的值设置为 **true** 或 **false**。如果是 false（缺省值），那么在计数时，每个设备都会被计为活动用户。
		
将 `collectLocation` 的值设置为 **true** 或 **false**。如果为 true，那么设备位置数据将作为 Appsession 日志的一部分发送。 

- **iOS**
	  
使用 [API 密钥](/docs/services/mobileanalytics/sdk.html#analytics-clientkey)值在应用程序代码内部初始化客户端 SDK，以记录使用情况分析和应用程序会话。
		
```Swift
		BMSClient.sharedInstance.initialize(bluemixRegion: BMSClient.Region.usSouth) // 您可以更改区域
		Analytics.initialize(appName: "your_app_name_here", apiKey: "your_api_key_here", hasUserContext: false, collectLocation: true, deviceEvents: deviceEvents: .lifecycle, .network)
```
		{: codeblock}
				
**bluemixRegion** 参数指定您使用的是哪一个 IBM Cloud 部署，例如 `BMSClient.Region.usSouth` 或 `BMSClient.Region.unitedKingdom`。
		
	 
将 `hasUserContext` 的值设置为 **true** 或 **false**。如果是 false（缺省值），那么在计数时，每个设备都会被计为活动用户。
		
将 `collectLocation` 的值设置为 **true** 或 **false**。如果为 true，那么设备位置数据将作为 Appsession 日志的一部分发送。 
	
- **Cordova**
		
使用 [API 密钥](/docs/services/mobileanalytics/sdk.html#analytics-clientkey)值在应用程序代码内部初始化客户端 SDK，以记录使用情况分析和应用程序会话。
		
```
		var appName = "your_app_name_here";
		var apiKey = "your_api_key_here";
		BMSClient.initialize(BMSClient.REGION_US_SOUTH); // 您可以更改区域
		BMSAnalytics.initialize(appName, apiKey, hasUserContext, collectLocation, [BMSAnalytics.ALL])
```
		{: codeblock}
		
**bluemixRegion** 参数指定您使用的是哪一个 IBM Cloud 部署，例如 `BMSClient.REGION_US_SOUTH` 或 `BMSClient.REGION_UK`。
		
将 `hasUserContext` 的值设置为 **true** 或 **false**。如果是 false（缺省值），那么在计数时，每个设备都会被计为活动用户。
		
将 `collectLocation` 的值设置为 **true** 或 **false**。如果为 true，那么设备位置数据将作为 Appsession 日志的一部分发送。
    
- **Web**
		
使用 [API 密钥](/docs/services/mobileanalytics/sdk.html#analytics-clientkey)值在应用程序代码内部初始化客户端 SDK，以记录使用情况分析和应用程序会话。
		
```
		var appName = "your_app_name_here";
		var apiKey = "your_api_key_here";
		BMSAnalytics.Client.initialize(BMSAnalytics.Client.REGION_US_SOUTH);
		BMSAnalytics.initialize(appName,apiKey,hasUserContext,BMSAnalytics.DeviceEvents.ALL,instanceId);
``` 
		{: codeblock}

`bluemixRegion` 参数指定您使用的是哪一个 {{site.data.keyword.Bluemix_notm}} 部署。将 `hasUserContext` 的值设置为 `true` 或 `false`。如果是 false（缺省值），那么在计数时，每个设备都会被计为活动用户。将 `instanceId` 设置为您的服务 instanceId，这是从服务实例的浏览器 URL 中获得的字母数字字符串，即字符串“...mobile-analytics_Prod/”与“/”之间的内容。 

**注**：您针对应用程序选择的名称 (`your_app_name_here`) 会在 {{site.data.keyword.mobileanalytics_short}} 控制台中显示为应用程序名称。应用程序名称用作过滤器，在仪表板中搜索应用程序日志。当您跨平台（例如 Android 和 iOS）使用相同的应用程序名称时，您可以在相同的名称下，查看该应用程序的所有日志，而无论日志发自哪个平台。

##将应用程序数据发送到 {{site.data.keyword.mobileanalytics_short}} 服务

将记录的使用分析发送到 {{site.data.keyword.mobileanalytics_short}} 服务。一个简单的方法可测试您的分析，即在应用程序启动时，运行下列代码：


- **Android**
	
使用 `Analytics.send()` 方法，将分析数据发送到服务器。您可以在 Android 应用程序主要活动的 `onCreate` 方法的任何位置或最适合您项目的位置，放置 `Analytics.send()` 方法。 
	
您可以在任何位置插入 `Analytics.send()`。
	
- **iOS**
	
使用 `Analytics.send` 方法，将分析数据发送到服务器。您可以将 `Analytics.send` 方法置于应用程序代表的 `application(_:didFinishLaunchingWithOptions:)` 方法的任何位置，或者置于适合您项目的位置。 
	
- **Cordova**
		
使用 `BMSAnalytics.send` 方法，将分析数据发送到服务器。将 `BMSAnalytics.send` 方法置于最适合您的项目的位置。
		
- **Web**
		
使用 `BMSAnalytics.send` 方法，将分析数据发送到服务器。将 `BMSAnalytics.send` 方法置于最适合您的项目的位置。 
		



请浏览[检测应用程序](/docs/services/mobileanalytics/sdk.html)主题，以了解其他 {{site.data.keyword.mobileanalytics_short}} 功能，例如[日志记录](/docs/services/mobileanalytics/sdk.html#app-monitoring-logger)、[网络请求](/docs/services/mobileanalytics/sdk.html#network-requests)、[位置日志记录](/docs/services/mobileanalytics/sdk.html#location-logging)和[崩溃分析](/docs/services/mobileanalytics/sdk.html#report-crash-analytics)。


下一步是**在仿真器或设备上编译并运行应用程序**。
