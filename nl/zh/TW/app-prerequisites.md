---

copyright:
 years: 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 必要條件
{: #prerequisites}
前次更新：2018 年 1 月 18 日
{: .last-updated}


## 建立 Mobile Analytics 服務實例
{: #prerequisites_1}

1. 在 [IBM Cloud 型錄](https://console.ng.bluemix.net/catalog/)中，按一下 **Mobile** > **Mobile Analytics**。
2. 提供服務名稱。
3. 按一下**建立**。
4. 選擇連接至其他現有應用程式，或讓它維持不連結。


您可以選擇建立連結服務，或是取消連結服務。連結服務已連接至其他 IBM Cloud 應用程式，但取消連結服務為獨立式，且未連接至其他應用程式。 

## 起始設定應用程式
{: #prerequisites_app}

[匯入](/docs/services/mobileanalytics/available-client-sdk.html)及安裝 {{site.data.keyword.mobileanalytics_short}} [Client SDK](/docs/services/mobileanalytics/install-client-sdk.html)。您可以選擇性地使用 {{site.data.keyword.mobileanalytics_short}} [REST API ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://mobile-analytics-dashboard.{DomainName}/analytics-service/){:new_window}。


###匯入 Client SDK

匯入 Client SDK，並使用下列程式碼 Snippet 起始設定它們，以記錄用量分析：

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
		
		
下一步是[檢測應用程式](app-instrument.html)。


