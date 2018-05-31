---

copyright:
 years: 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 檢測應用程式
{: #Instrument}
前次更新：2018 年 1 月 18 日
{: .last-updated}

##起始設定 {{site.data.keyword.mobileanalytics_short}} Client SDK 

使用 [API 金鑰](/docs/services/mobileanalytics/sdk.html#analytics-clientkey)值，以在應用程式碼內起始設定 {{site.data.keyword.mobileanalytics_short}} Client SDK，來記錄用量分析及應用程式階段作業。	
	
- **Android**
	
```
		BMSClient.getInstance().initialize(getApplicationContext(), BMSClient.REGION_US_SOUTH); // You can change the region
		Analytics.init(getApplication(), "your_app_name_here", "your_api_key_here", hasUserContext, collectLocation, Analytics.DeviceEvent.ALL);
```
		{: codeblock}
	    
**bluemixRegion** 參數指定您所使用的 {{site.data.keyword.Bluemix_notm}} 部署（例如，`BMSClient.REGION_US_SOUTH` 及 `BMSClient.REGION_UK`）。 
	    
	    
將 `hasUserContext` 的值設為 **true** 或 **false**。如果是 false（預設值），每一台裝置都會計算為一個作用中使用者。
		
將 `collectLocation` 的值設為 **true** 或 **false**。如果是 true，則會將裝置位置資料視為 Appsession 日誌的一部分傳送。 

- **iOS**
	  
使用 [API 金鑰](/docs/services/mobileanalytics/sdk.html#analytics-clientkey)值，以在應用程式碼內起始設定 Client SDK，來記錄用量分析及應用程式階段作業。
		
```Swift
		BMSClient.sharedInstance.initialize(bluemixRegion: BMSClient.Region.usSouth) // You can change the region
		Analytics.initialize(appName: "your_app_name_here", apiKey: "your_api_key_here", hasUserContext: false, collectLocation: true, deviceEvents: deviceEvents: .lifecycle, .network)
```
		{: codeblock}
				
**bluemixRegion** 參數指定您所使用的 IBM Cloud 部署（例如，`BMSClient.Region.usSouth` 或 `BMSClient.Region.unitedKingdom`）。
		
	 
將 `hasUserContext` 的值設為 **true** 或 **false**。如果是 false（預設值），每一台裝置都會計算為一個作用中使用者。
		
將 `collectLocation` 的值設為 **true** 或 **false**。如果是 true，則會將裝置位置資料視為 Appsession 日誌的一部分傳送。 
	
- **Cordova**
		
使用 [API 金鑰](/docs/services/mobileanalytics/sdk.html#analytics-clientkey)值，以在應用程式碼內起始設定 Client SDK，來記錄用量分析及應用程式階段作業。
		
```
		var appName = "your_app_name_here";
		var apiKey = "your_api_key_here";
		BMSClient.initialize(BMSClient.REGION_US_SOUTH); // You can change the region
		BMSAnalytics.initialize(appName, apiKey, hasUserContext, collectLocation, [BMSAnalytics.ALL])
```
		{: codeblock}
		
**bluemixRegion** 參數指定您所使用的 IBM Cloud 部署（例如，`BMSClient.REGION_US_SOUTH` 或 `BMSClient.REGION_UK`）。
		
將 `hasUserContext` 的值設為 **true** 或 **false**。如果是 false（預設值），每一台裝置都會計算為一個作用中使用者。
		
將 `collectLocation` 的值設為 **true** 或 **false**。如果是 true，則會將裝置位置資料視為 Appsession 日誌的一部分傳送。
    
- **Web**
		
使用 [API 金鑰](/docs/services/mobileanalytics/sdk.html#analytics-clientkey)值，以在應用程式碼內起始設定 Client SDK，來記錄用量分析及應用程式階段作業。
		
```
		var appName = "your_app_name_here";
		var apiKey = "your_api_key_here";
		BMSAnalytics.Client.initialize(BMSAnalytics.Client.REGION_US_SOUTH);
		BMSAnalytics.initialize(appName,apiKey,hasUserContext,BMSAnalytics.DeviceEvents.ALL,instanceId);
``` 
		{: codeblock}

`bluemixRegion` 參數指定您所使用的 {{site.data.keyword.Bluemix_notm}} 部署。將 `hasUserContext` 的值設為 `true` 或 `false`。如果是 false（預設值），每一台裝置都會計算為一個作用中使用者。請將 `instanceId` 設為服務 instanceId，這是從服務實例的瀏覽器 URL 取得的英數字串，放在字串 "...mobile-analytics_Prod/" 及 upto "/" 後面。 

**附註**：您為應用程式所選取的名稱 (`your_app_name_here`) 會在 {{site.data.keyword.mobileanalytics_short}} 主控台中顯示為應用程式名稱。應用程式名稱是用來作為過濾器，以在儀表板中搜尋應用程式日誌。當您跨平台（例如，Android 及 iOS）使用相同的應用程式名稱時，不論是從哪個平台傳送日誌，都可以看到同名應用程式的所有日誌。

##將應用程式資料傳送至 {{site.data.keyword.mobileanalytics_short}} 服務

將記錄的用量分析傳送至 {{site.data.keyword.mobileanalytics_short}} 服務。簡單的測試分析方式是在應用程式啟動時執行下列程式碼：


- **Android**
	
使用 `Analytics.send()` 方法，將分析資料傳送至伺服器。您可以將 `Analytics.send()` 方法放在 Android 應用程式中主要活動之 `onCreate` 方法的任意位置，或放在最適合您專案的位置。 
	
您可以在任意位置插入 `Analytics.send()`。
	
- **iOS**
	
使用 `Analytics.send` 方法，將分析資料傳送至伺服器。您可以將 `Analytics.send` 方法放在應用程式委派的 `application(_:didFinishLaunchingWithOptions:)` 方法的任意位置，或放在最適合您專案的位置。 
	
- **Cordova**
		
使用 `BMSAnalytics.send` 方法，將分析資料傳送至伺服器。將 `BMSAnalytics.send` 方法放在最適合您專案的位置中。
		
- **Web**
		
使用 `BMSAnalytics.send` 方法，將分析資料傳送至伺服器。將 `BMSAnalytics.send` 方法放在最適合您專案的位置中。 
		



瀏覽[檢測應用程式](/docs/services/mobileanalytics/sdk.html)主題，以瞭解其他 {{site.data.keyword.mobileanalytics_short}} 功能（例如[記載](/docs/services/mobileanalytics/sdk.html#app-monitoring-logger)、[網路要求](/docs/services/mobileanalytics/sdk.html#network-requests)、[位置記載](/docs/services/mobileanalytics/sdk.html#location-logging)及[損毀分析](/docs/services/mobileanalytics/sdk.html#report-crash-analytics)）。


下一步是**在模擬器或裝置上編譯並執行應用程式**。
