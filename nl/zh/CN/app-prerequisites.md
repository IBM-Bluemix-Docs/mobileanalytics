---

copyright:
 years: 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 先决条件
{: #prerequisites}
上次更新时间：2018 年 1 月 18 日
{: .last-updated}


## 创建 Mobile Analytics 服务实例
{: #prerequisites_1}

1. 在 [IBM Cloud 目录](https://console.ng.bluemix.net/catalog/)中，单击**移动** > **Mobile Analytics**。
2. 提供服务名称。
3. 单击**创建**。
4. 选择连接到其他现有应用程序，或将其保留为未绑定。


可以选择创建绑定服务或未绑定服务。绑定服务已连接到其他 IBM Cloud 应用程序，而未绑定服务则独立且未连接到其他应用程序。 

## 初始化应用程序
{: #prerequisites_app}

[导入](/docs/services/mobileanalytics/available-client-sdk.html)并安装{{site.data.keyword.mobileanalytics_short}}[客户端 SDK](/docs/services/mobileanalytics/install-client-sdk.html)。您可以选择使用 {{site.data.keyword.mobileanalytics_short}} [REST API ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://mobile-analytics-dashboard.{DomainName}/analytics-service/){:new_window}。


###导入客户端 SDK

导入客户端 SDK，并使用下列代码片段对它们进行初始化，以记录使用情况分析：

- Android
	
    将以下 `import` 语句添加到项目文件的开头：
		
	```
		  import com.ibm.mobilefirstplatform.clientsdk.android.core.api.*;
import com.ibm.mobilefirstplatform.clientsdk.android.analytics.api.*;
import com.ibm.mobilefirstplatform.clientsdk.android.logger.api.*;
  ```
    {: codeblock}

- iOS

    iOS 和 watchOS 可以使用 Swift SDK。
		
    通过将以下 `import` 语句添加到 `AppDelegate.swift` 项目文件的开头，导入 `BMSCore` 和 `BMSAnalytics` 框架：
	
	```Swift
		import BMSCore
		import BMSAnalytics
	```
    {: codeblock}
   
- Cordova
			
    从 Cordova 应用程序根目录运行以下命令来添加 Cordova 插件：
	
	```Javascript
		cordova plugin add bms-core
	```
    {: codeblock}
   
- Web
	
    通过在 Web 应用程序的 `index.html` 文件中添加以下脚本来添加 Web 插件：
	
	```Html
		<script src="bms-clientsdk-web-analytics/bmsanalytics.js"></script>
	```
    {: codeblock}

    或者，使用模块装入程序 requirejs 来添加 Web 插件。用作参考 API 的名称与所使用的自变量名称 (`BMSAnalytics`) 相同。 
	
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
		
		
下一步是[检测应用程序](app-instrument.html)。


