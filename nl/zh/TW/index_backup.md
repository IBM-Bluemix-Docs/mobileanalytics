---

copyright:
  years: 2016, 2017
lastupdated: "2017-07-14"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 入門指導教學

{: #gettingstartedtemplate}

{{site.data.keyword.mobileanalytics_full}} 可提供開發人員、IT 管理者及商業利害關係人，對其行動應用程式的效能及其使用情形的見解。{{site.data.keyword.mobileanalytics_short}} 可讓您：

* 從桌面或平板電腦監視所有應用程式的效能及使用情形。 
* 快速識別趨勢和異常、往下探查以解決這些問題，以及在重要度量值超過重大臨界值時觸發警示。
{: shortdesc}

若要快速開始進行 {{site.data.keyword.mobileanalytics_short}} 服務，請遵循下列步驟：

1. 為 {{site.data.keyword.mobileanalytics_short}} 服務建立實例<!--[create an instance](https://console.{DomainName}/docs/services/reqnsi.html#req_instance)-->之後，可以在「{{site.data.keyword.Bluemix}} 儀表板」的**服務**區段中按一下您的磚，以存取「{{site.data.keyword.mobileanalytics_short}} 主控台」。{{site.data.keyword.mobileanalytics_short}} 主控台中提供**展示模式**選項，視圖及圖表可以藉此顯示*展示資料*。展示模式是主控台在服務實例化之後初次啟動時的預設模式。當您將自己的應用程式及分析資料移入服務之後，便可以*關閉* 展示模式，以在不同圖表中檢視您的應用程式資料。處於展示模式時，{{site.data.keyword.mobileanalytics_short}} 主控台是唯讀的，因此您無法建立新的警示定義。

2. 安裝 {{site.data.keyword.mobileanalytics_short}} [Client SDK](/docs/services/mobileanalytics/install-client-sdk.html)。您可以選擇性地使用 {{site.data.keyword.mobileanalytics_short}} [REST API ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://mobile-analytics-dashboard.{DomainName}/analytics-service/){:new_window}。
	
	- Web 應用程式服務配置
	
		對於 Web SDK，若要配置服務實例以容許應用程式伺服器，您需要透過使用 Swagger 使用者介面的「服務配置 REST API」，提供應用程式伺服器的 URL。POST、GET、PUT 及 DELETE 方法是針對服務配置的 CRUD 作業所提供，而這是容許的 URL 清單。若要 GET（取得）及 DELETE（刪除）您服務實例的配置，請使用 API 金鑰。若要建立及更新服務配置，請使用 POST 及 PUT 方法並將容許的 URL 列為內文 {"allowedUrls":["http://abc.com","https://www.xyz.com"]}。如果您在與 Web 伺服器之系統相同的系統中從瀏覽器進行存取，請提供 "http://localhost" 作為容許的 URL。

3. 匯入 Client SDK，並使用下列程式碼 Snippet 起始設定它們，以記錄用量分析：

	- Android
	
		將下列 `import` 陳述式新增至專案檔開頭處：
		
		```
		import com.ibm.mobilefirstplatform.clientsdk.android.core.api.*;
	import com.ibm.mobilefirstplatform.clientsdk.android.analytics.api.*;
	import com.ibm.mobilefirstplatform.clientsdk.android.logger.api.*;
  	```
		{: codeblock}

	- iOS

		Swift SDK 適用於 iOS 及 watchOS。
		
		將下列 `import` 陳述式新增至 `AppDelegate.swift` 專案檔開頭處，以匯入 `BMSCore` 和 `BMSAnalytics` 架構：
	
		```Swift
		import BMSCore
		import BMSAnalytics
		```
		{: codeblock}
   
	- Cordova
			
		從您的 Cordova 應用程式根目錄，執行下列指令以新增 Cordova 外掛程式：
	
		```Javascript
		cordova plugin add bms-core
		```
		{: codeblock}
   
	- Web
	
		在 Web 應用程式的 `index.html` 檔案中新增此 Script，以新增 Web 外掛程式：
	
		```Html
		<script src="bms-clientsdk-web-analytics/bmsanalytics.js"></script>
		```
		{: codeblock}

		或者，使用模組載入器 requirejs。作為參照 API 使用的名稱會與使用的引數名稱 (`BMSAnalytics`) 相同。 
	
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
		
4. 使用 [API 金鑰](/docs/services/mobileanalytics/sdk.html#analytics-clientkey)值，以在應用程式碼內起始設定 {{site.data.keyword.mobileanalytics_short}} Client SDK，來記錄用量分析及應用程式階段作業。	
	
	- Android
	
		```
		BMSClient.getInstance().initialize(getApplicationContext(), BMSClient.REGION_US_SOUTH); // You can change the region
		Analytics.init(getApplication(), "your_app_name_here", "your_api_key_here", hasUserContext, collectLocation, Analytics.DeviceEvent.ALL);
		```
		{: codeblock}
	    
		**bluemixRegion** 參數指定您所使用的 {{site.data.keyword.Bluemix_notm}} 部署（例如，`BMSClient.REGION_US_SOUTH` 及 `BMSClient.REGION_UK`）。 
	    <!-- , or `BMSClient.Region.Sydney`.-->
	    
		將 `hasUserContext` 的值設為 **true** 或 **false**。如果是 false（預設值），每一台裝置都會計算為一個作用中使用者。
		
		將 `collectLocation` 的值設為 **true** 或 **false**。如果是 true，則會將裝置位置資料視為 Appsession 日誌的一部分傳送。 

	- iOS
	  
		使用 [API 金鑰](/docs/services/mobileanalytics/sdk.html#analytics-clientkey)值，以在應用程式碼內起始設定 Client SDK，來記錄用量分析及應用程式階段作業。
		
		```Swift
		BMSClient.sharedInstance.initialize(bluemixRegion: BMSClient.Region.usSouth) // You can change the region
		Analytics.initialize(appName: "your_app_name_here", apiKey: "your_api_key_here", hasUserContext: false, collectLocation: true, deviceEvents: deviceEvents: .lifecycle, .network)
		```
		{: codeblock}
				
		**bluemixRegion** 參數指定您所使用的 IBM Cloud 部署（例如，`BMSClient.Region.usSouth` 或 `BMSClient.Region.unitedKingdom`）。
		<!-- , or `BMSClient.REGION_SYDNEY`. -->
	 
		將 `hasUserContext` 的值設為 **true** 或 **false**。如果是 false（預設值），每一台裝置都會計算為一個作用中使用者。
		
		將 `collectLocation` 的值設為 **true** 或 **false**。如果是 true，則會將裝置位置資料視為 Appsession 日誌的一部分傳送。 
	
	- Cordova
		
		使用 [API 金鑰](/docs/services/mobileanalytics/sdk.html#analytics-clientkey)值，以在應用程式碼內起始設定 Client SDK，來記錄用量分析及應用程式階段作業。
		
		```
		var appName = "your_app_name_here";
		var apiKey = "your_api_key_here";
		BMSClient.initialize(BMSClient.REGION_US_SOUTH); // You can change the region
		BMSAnalytics.initialize(appName, apiKey, hasUserContext, collectLocation, [BMSAnalytics.ALL])
		```
		{: codeblock}
		
		**bluemixRegion** 參數指定您所使用的 IBM Cloud 部署（例如，`BMSClient.REGION_US_SOUTH` 或 `BMSClient.REGION_UK`）。
		<!-- , or `BMSClient.REGION_SYDNEY`. -->
		將 `hasUserContext` 的值設為 **true** 或 **false**。如果是 false（預設值），每一台裝置都會計算為一個作用中使用者。
		
		將 `collectLocation` 的值設為 **true** 或 **false**。如果是 true，則會將裝置位置資料視為 Appsession 日誌的一部分傳送。
    
	- Web
		
		使用 [API 金鑰](/docs/services/mobileanalytics/sdk.html#analytics-clientkey)值，以在應用程式碼內起始設定 Client SDK，來記錄用量分析及應用程式階段作業。
		
		```
		var appName = "your_app_name_here";
		var apiKey = "your_api_key_here";
		BMSAnalytics.Client.initialize(BMSAnalytics.Client.REGION_US_SOUTH);
		BMSAnalytics.initialize(appName,apiKey,hasUserContext,BMSAnalytics.DeviceEvents.ALL,instanceId);
		``` 
		{: codeblock}

		`bluemixRegion` 參數指定您所使用的 {{site.data.keyword.Bluemix_notm}} 部署（例如，`BMSAnalytics.Client.REGION_US_SOUTH` 及 `BMSAnalytics.Client.REGION_UK`）。將 `hasUserContext` 的值設為 `true` 或 `false`。如果是 false（預設值），每一台裝置都會計算為一個作用中使用者。請將 `instanceId` 設為服務 instanceId，這是從服務實例的瀏覽器 URL 取得的英數字串，放在字串 "...mobile-analytics_Prod/" 及 upto "/" 後面。 

		請注意，您為應用程式所選取的名稱 (`your_app_name_here`) 會在 {{site.data.keyword.mobileanalytics_short}} 主控台中顯示為應用程式名稱。應用程式名稱是用來作為過濾器，以在儀表板中搜尋應用程式日誌。當您跨平台（例如，Android 及 iOS）使用相同的應用程式名稱時，不論是從哪個平台傳送日誌，都可以看到同名應用程式的所有日誌。

5. 將記錄的用量分析傳送至 {{site.data.keyword.mobileanalytics_short}} 服務。簡單的測試分析方式是在應用程式啟動時執行下列程式碼：

	- Android
	
		使用 `Analytics.send()` 方法，將分析資料傳送至伺服器。您可以將 `Analytics.send()` 方法放在 Android 應用程式中主要活動之 `onCreate` 方法的任意位置，或放在最適合您專案的位置。 
	
		您可以在任意位置插入 `Analytics.send()`。
	
	- iOS
	
		使用 `Analytics.send` 方法，將分析資料傳送至伺服器。您可以將 `Analytics.send` 方法放在應用程式委派的 `application(_:didFinishLaunchingWithOptions:)` 方法的任意位置，或放在最適合您專案的位置。 
	
	- Cordova
		
		使用 `BMSAnalytics.send` 方法，將分析資料傳送至伺服器。將 `BMSAnalytics.send` 方法放在最適合您專案的位置中。
		
	- Web
		
		使用 `BMSAnalytics.send` 方法，將分析資料傳送至伺服器。將 `BMSAnalytics.send` 方法放在最適合您專案的位置中。 
		
6. 瀏覽[檢測應用程式](/docs/services/mobileanalytics/sdk.html)主題，以瞭解其他 {{site.data.keyword.mobileanalytics_short}} 功能（例如[記載](/docs/services/mobileanalytics/sdk.html#app-monitoring-logger)、[網路要求](/docs/services/mobileanalytics/sdk.html#network-requests)、[位置記載](/docs/services/mobileanalytics/sdk.html#location-logging)及[損毀分析](/docs/services/mobileanalytics/sdk.html#report-crash-analytics)）。
	
7. 在模擬器或裝置上編譯並執行應用程式。

8. 移至 {{site.data.keyword.mobileanalytics_short}} 主控台，以查看應用程式的用量分析。您也可以<!--[creating custom charts](app-monitoring.html#custom-charts),-->[設定警示](/docs/services/mobileanalytics/app-monitoring.html#alerts)及[監視應用程式損毀](/docs/services/mobileanalytics/app-monitoring.html#monitor-app-crash)來監視應用程式。

# 相關鏈結
{: #rellinks notoc}

## SDK
{: #sdk notoc}
* [Android SDK ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-analytics){: new_window}  
* [iOS SDK ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-analytics){: new_window}
* [Cordova 外掛程式核心 SDK ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.npmjs.com/package/bms-core){: new_window}
* [Web SDK ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-web-analytics/){: new_window}
## API 參考資料
{: #api notoc}
* [REST API ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://mobile-analytics-dashboard.{DomainName}/analytics-service/){:new_window}
