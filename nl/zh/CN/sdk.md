---

copyright:
  years: 2015, 2017
lastupdated: "2018-01-18"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 检测应用程序
{: #mobileanalytics_sdk}

## 检测应用程序以使用 {{site.data.keyword.mobileanalytics_short}} 客户端 SDK

使用 {{site.data.keyword.mobileanalytics_full}} SDK，您可以检测移动应用程序。
{: shortdesc}

使用 {{site.data.keyword.mobileanalytics_short}}，您可以收集以下类别的数据，每一种需要不同程度的检测：


- 预定义的数据：这种类别包含适用于所有应用程序的通用使用情况和设备信息。在这种类别中存在设备元数据（操作系统和设备模型）和使用情况数据（活动用户和应用程序会话），可指示应用程序使用的数量、频率和持续时间。当您在应用程序中初始化 {{site.data.keyword.mobileanalytics_short}} SDK 之后，会自动收集预定义的数据。

- 应用程序日志消息：这种类别使得开发人员可以在整个应用程序中添加记录定制消息的代码行，以协助开发和调试。开发人员会为每一则日志消息分配严重性/详细程度级别，这样就可以根据所分配的级别对消息进行过滤，或者通过将应用程序配置为忽略低于给定日志级别的消息来保留存储空间。要收集应用程序日志数据，您必须在应用程序内初始化 {{site.data.keyword.mobileanalytics_short}} SDK，并对每一则日志消息，添加一行代码。

- 定制事件 - 这种类别包含您自行定义且特定于您应用程序的数据。此数据代表您应用程序中发生的事件，如查看页面、点击按钮或应用程序内采购。除了在您的应用程序中初始化 {{site.data.keyword.mobileanalytics_short}} SDK 之外，您还必须对要跟踪的每一个定制事件，添加一行代码。 

目前，Android、iOS、WatchOS、Cordova 和 Web 可以使用 SDK。

## 识别服务凭证 API 密钥值
{: #analytics-clientkey}

在设置客户端 SDK 之前，先识别您的 **API 密钥**值。初始化客户端 SDK 时，需要 API 密钥。

1. 打开 {{site.data.keyword.mobileanalytics_short}} 服务仪表板。
1. 展开**查看凭证**以显示 API 密钥值。当您初始化 {{site.data.keyword.mobileanalytics_short}} 客户端 SDK 时，将需要 API 密钥值。


## 初始化应用程序以收集分析
{: #initalize-ma-sdk}

初始化应用程序以启用发送日志到 {{site.data.keyword.mobileanalytics_short}} 服务。

1. 导入客户端 SDK。
	- Android
	
		将以下 `import` 语句添加到项目文件的开头：
		
		```
		  import com.ibm.mobilefirstplatform.clientsdk.android.core.api.*;
import com.ibm.mobilefirstplatform.clientsdk.android.analytics.api.*;
import com.ibm.mobilefirstplatform.clientsdk.android.logger.api.*;
  ```
		{: codeblock}
  
	- iOS
		
		iOS 和 watchOS 可以使用 Swift SDK。通过将以下 `import` 语句添加到 `AppDelegate.swift` 项目文件的开头，导入 `BMSCore` 和 `BMSAnalytics` 框架：
	
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
			
		通过将作为脚本提供的 SDK 添加到 index.html 来添加 Web 插件：
	
		```Html
		<script src="/path/to/bms-clientsdk-web-analytics/bmsanalytics.js"></script>
		```
		{: codeblock} 	 	

	 	或者，使用模块装入程序 requirejs 添加 Web 插件： 
	
	 	```Javascript
	 	require.config({
	    'paths': {
	        'bmsanalytics': '/path/to/bms-clientsdk-web-analytics/bmsanalytics'
	    	}
		});
		require(['bmsanalytics'], function(BMSAnalytics) {
		 BMSAnalytics.send(); 
		}
		``` 	
		{: codeblock}  

2. 初始化您应用程序中的 {{site.data.keyword.mobileanalytics_short}} 客户端 SDK。

	- Android
		
		通过在 Android 应用程序主要活动的 `onCreate` 方法中，或者在适合您项目的位置，添加初始化代码，以在 Android 应用程序中初始化 {{site.data.keyword.mobileanalytics_short}} 客户端 SDK。
	
		```Java
		BMSClient.getInstance().initialize(getApplicationContext(), BMSClient.REGION_US_SOUTH); // Make sure that you point to your region
		```
		{: codeblock}
	
		您必须使用 **bluemixRegion** 参数，初始化 `BMSClient`。在初始化程序中，**bluemixRegion** 值指定您使用的是哪一个 {{site.data.keyword.Bluemix_notm}} 部署，例如 `BMSClient.REGION_US_SOUTH` 和 `BMSClient.REGION_UK`。 
	    <!-- , or `BMSClient.REGION_SYDNEY`.--> 
    
	- iOS
	    
		先使用以下代码，初始化 `BMSClient` 类。将初始化代码置于应用程序代表的 `application(_:didFinishLaunchingWithOptions:)` 方法中，或者置于适合您项目的位置。
		
		```Swift
		BMSClient.sharedInstance.initialize(bluemixRegion: BMSClient.Region.usSouth) // 确保指向您的区域
		```
		{: codeblock}
	
		您必须使用 **bluemixRegion** 参数，初始化 `BMSClient`。在初始化程序中，**bluemixRegion** 值指定您使用的是哪一个 {{site.data.keyword.Bluemix_notm}} 部署，例如 `BMSClient.Region.usSouth` 或 `BMSClient.Region.unitedKingdom`。
	    <!-- , or `BMSClient.Region.Sydney`. -->
    
	- Cordova
	  
		初始化 **BMSClient** 和 **BMSAnalytics**。您将需要 [**API 密钥**](#analytics-clientkey)值。
	
		```Javascript
		BMSClient.initialize(BMSClient.REGION_US_SOUTH); // 确保指向您的区域	
		```
		{: codeblock}
		
		要使用 {{site.data.keyword.mobileanalytics_short}} 客户端 SDK，您必须使用 **bluemixRegion** 参数，初始化 `BMSClient`。在初始化程序中，**bluemixRegion** 值指定您使用的是哪一个 {{site.data.keyword.Bluemix_notm}} 部署，例如 `BMSClient.REGION_US_SOUTH` 或 `BMSClient.REGION_UK`。
	    <!-- , or `BMSClient.REGION_SYDNEY`. -->
    
	- Web

	    使用 API 密钥值在应用程序代码内部初始化客户端 SDK，以记录使用情况分析和应用程序会话。
	    ```javascript
	    BMSAnalytics.Client.initialize(BMSAnalytics.Client.REGION_US_SOUTH);
	    ```
	    {: codeblock}
		
		要使用 {{site.data.keyword.mobileanalytics_short}} 客户端 SDK，您必须使用 **bluemixRegion** 参数来初始化 `BMSAnalytics.Client`。在初始化程序中，**bluemixRegion** 值指定您使用的是哪一个 {{site.data.keyword.Bluemix_notm}} 部署，例如 `BMSAnalytics.Client..REGION_UK` 或 `BMSAnalytics.Client..REGION_US_SOUTH`。
	    <!-- , or `BMSClient.REGION_SYDNEY`. -->
    
3. 使用应用程序对象并为其提供应用程序名称，来初始化 Analytics。 

	您针对应用程序选择的名称 (`your_app_name_here`) 会在 {{site.data.keyword.mobileanalytics_short}} Console 中显示为应用程序名称。应用程序名称用作过滤器，在仪表板中搜索应用程序日志。当您跨平台（例如 Android 和 iOS）使用相同的应用程序名称时，您可以在相同的名称下，查看该应用程序的所有日志，而无论日志发自哪个平台。

	您还需要 [API 密钥](#analytics-clientkey)值。

- Android
		
	```Java
		// 在此代码示例中，Analytics 配置为记录生命周期事件。
		Analytics.init(getApplication(), "your_app_name_here", apiKey, hasUserContext, collectLocation, Analytics.DeviceEvent.ALL);
	```
    {: codeblock}
		
	**注**：将 `hasUserContext` 的值设置为 **true** 或 **false**。如果是 false（缺省值），那么在计数时，每个设备都会被计为活动用户。通过 [`Analytics.setUserIdentity("username")`](sdk.html#android-tracking-users) 方法，您可以跟踪当前使用应用程序的每个装置的用户数，但是当 `hasUserContext` 为 false 时无法使用。如果是 true，那么每次使用 [`Analytics.setUserIdentity("username")`](sdk.html#android-tracking-users) 都会在计数时被计为活动用户。当 `hasUserContext` 为 true 时，没有缺省用户身份，因此必须设置该身份以填充活动用户图表。如果 `collectLocation` 设置为 true，`Analytics.logLocation()` 方法将生效，用于支持应用程序发送设备位置。 
		
		
	
- iOS
		
	```Swift 
		Analytics.initialize(appName: "your_app_name_here", apiKey: "your_api_key_here", hasUserContext: false, collectLocation: true, deviceEvents: .lifecycle, .network)
	```
    {: codeblock}
 	
- watchOS
		 	
	```Swift
		Analytics.initialize(appName: "your_app_name_here", apiKey: "your_api_key_here",collectLocation: true, deviceEvents: .network)
	```
    {: codeblock}
	 	
    可选 `deviceEvents` 参数会自动收集设备级别事件的分析。
		
    将 `hasUserContext` 的值设置为 **true** 或 **false**。如果是 false（缺省值），那么在计数时，每个设备都会被计为活动用户。通过 [`Analytics.userIdentity = "username"`](sdk.html#ios-tracking-users) 方法，您可以跟踪当前使用应用程序的每个装置的用户数，但是当 `hasUserContext` 为 false 时无法使用。如果 `hasUserContext` 为 true，那么每次使用 [`Analytics.userIdentity="username"`](sdk.html#ios-tracking-users) 都会在计数时被计为活动用户。当 `hasUserContext` 为 true 时，没有缺省用户身份，因此必须设置该身份以填充活动用户图表。如果 `collectLocation` 设置为 true，`Analytics.logLocation()` 方法将生效，用于支持应用程序发送设备位置。 

- watchOS
	
    您可以使用 `Analytics.recordApplicationDidBecomeActive()` 和 `Analytics.recordApplicationWillResignActive()` 方法，来记录 WatchOS 上的设备事件。
	  
    将下列一行添加到 ExtensionDelegate 类的 `applicationDidBecomeActive()` 方法中：
	 
	```Javascript
		Analytics.recordApplicationDidBecomeActive()
	```
    {: codeblock}
	
    将下列一行添加到 ExtensionDelegate 类的 `applicationWillResignActive()` 方法中：
	 
	```Javascript
		Analytics.recordApplicationWillResignActive()
	```
    {: codeblock}	
		
- Cordova
		
	```Javascript
	Analytics.initialize(appName, apiKey,  hasUserContext, collectLocation, [BMSAnalytics.ALL])
	```
    {: codeblock}	
		
    将 `hasUserContext` 的值设置为 **true** 或 **false**。如果是 false（缺省值），那么在计数时，每个设备都会被计为活动用户。通过 `Analytics.setUserIdentity("username")` 方法，您可以跟踪当前使用应用程序的每个装置的用户数，但是当 `hasUserContext` 为 false 时无法使用。如果是 true，那么每次使用 `Analytics.setUserIdentity("username")` (sdk.html#android-tracking-users) 都会在计数时被计为活动用户。当 `hasUserContext` 为 true 时，没有缺省用户身份，因此必须设置该身份以填充活动用户图表。如果 `collectLocation` 设置为 true，`Analytics.logLocation()` 方法将生效，用于支持应用程序发送设备位置。 
	
- Web
		
	```Java
		// 在此代码示例中，Analytics 配置为记录所有事件。
		BMSAnalytics.initialize(appName, apiKey, hasUserContext, BMSAnalytics.DeviceEvent.ALL);
	```
    {: codeblock}
		
    将 `hasUserContext` 的值设置为 **true** 或 **false**。如果是 false（缺省值），那么在计数时，每个设备都会被计为活动用户。`hasUserContext` 为 false 时，[`BMSAnalytics.setUserIdentity("username")`](sdk.html#web-tracking-users) 方法不会生效，即不支持跟踪当前使用应用程序的每个设备的用户数。如果为 true，那么每次使用 [`BMSAnalytics.setUserIdentity("username")`](sdk.html#web-tracking-users) 都会在计数时被计为活动用户。当 `hasUserContext` 为 true 时，没有缺省用户身份，因此必须设置该身份以填充活动用户图表。	

4. 您现在已经初始化应用程序以收集分析。接下来，您可以[发送分析数据](sdk.html#app-monitoring-gathering-analytics)至 {{site.data.keyword.mobileanalytics_short}} 服务。


## 收集使用情况分析
{: #app-monitoring-gathering-analytics}

您可以配置 {{site.data.keyword.mobileanalytics_short}} 客户端 SDK，以记录使用情况分析，并将记录的数据发送到 {{site.data.keyword.mobileanalytics_short}} 服务。

使用下列 API，开始记录和发送使用情况分析：

- Android
	
	```
	// 禁用记录使用情况分析（例如，为了节省磁盘空间）
	// 缺省情况下会启用记录
	Analytics.disable();
	// 启用记录使用情况分析
	Analytics.enable();
	// 将记录的使用情况分析发送到 Mobile Analytics 服务
	Analytics.send(new ResponseListener() {
	            @Override
            public void onSuccess(Response response) {
                // Handle Analytics send success here.
            }

            @Override
            public void onFailure(Response response, Throwable throwable, JSONObject jsonObject) {
                // Handle Analytics send failure here.
            }
        });
	```
	{: codeblock}
		
	记录事件的使用情况分析示例：
		
	```
	// 记录定制分析事件
	JSONObject eventJSONObject = new JSONObject();
	eventJSONObject.put("customProperty" , "propertyValue");
	Analytics.log(eventJSONObject);
	```
	{: codeblock}


- iOS (Swift)

	```
	// 禁用记录使用情况分析（例如，为了节省磁盘空间）
	// 缺省情况下会启用记录
	Analytics.isEnabled = false
	// 启用记录使用情况分析
	Analytics.isEnabled = true
	// 将记录的使用情况分析发送到 Mobile Analytics 服务
	Analytics.send(completionHandler: { (response: Response?, error: Error?) in
	    if let response = response {
	        // Handle Analytics send success here.
            }

            if let error = error {
        // Handle Analytics send failure here.
            }
        })
	```
	{: codeblock}
	
	记录事件的使用情况分析示例：
	
	```Swift
	// 记录定制分析事件
	let eventObject = ["customProperty": "propertyValue"]
	Analytics.log(metadata: eventObject)
	```
	{: codeblock}

- Cordova

	```JavaScript
	// 启用使用情况分析记录
	BMSAnalytics.enable();
	// 禁用使用情况分析记录
	BMSAnalytics.disable();
	// 将记录的使用情况分析发送到 {{site.data.keyword.mobileanalytics_short}} 服务
	BMSAnalytics.send(
		function(response) {
			console.log('success: ' + response);
		},
	function (err) {
		console.log('fail: ' + err);
		});
  ```
	{: codeblock}
	
	记录事件的使用情况分析示例：
	
	```JavaScript
	// 记录定制分析事件
	var eventObject = {"customProperty": "propertyValue"}
	BMSAnalytics.log(eventObject)
	```
	{: codeblock}

	开发 Cordova 应用程序时，请使用本机 API 来启用应用程序生命周期事件记录。
 
- Web
		
	```
	// 禁用记录使用情况分析（例如，为了节省磁盘空间）
	// 缺省情况下会启用记录
	BBMSAnalytics.disable();
	// 启用记录使用情况分析
	BMSAnalytics.enable();
	// 将记录的使用情况分析发送到 Mobile Analytics 服务
	BMSAnalytics.send().then(function(result) {
         	// 在此句柄成功
        }, function(err) {
                // 在此句柄失败
        });;
	```
	{: codeblock}
		
	记录事件的使用情况分析示例：
		
	```JavaScript
	// 记录定制分析事件
	var eventObject = {"customProperty": "propertyValue"}
	BMSAnalytics.log(eventObject)
	```
	{: codeblock}
  
## 启用、配置和使用记录器

{{site.data.keyword.mobileanalytics_full}} 客户端 SDK 提供了一种日志记录框架，与您可能熟悉的其他日志框架（如 `java.util.logging` 或 `log4j`）类似。此日志记录框架支持每个数据包多个记录器实例，支持不同的日志级别，支持捕获对应用程序崩溃的堆栈跟踪，等等。

您还可以将记录的数据配置为存储在应用程序运行所在的设备上，并在以后将这些设备日志发送到 {{site.data.keyword.mobileanalytics_short}} 服务。

<!-- Initialization has to happen first to be able to collect logs and send them to the {{site.data.keyword.mobileanalytics_short}} service. -->

{{site.data.keyword.mobileanalytics_short}} 客户端 SDK 日志记录框架支持以下日志级别，按详细程度从低到高的顺序与其建议的使用准则一起列出：

  * `FATAL` - 用于不可恢复的崩溃或挂起。`FATAL` 级别保留用于记录不可恢复的错误，这些错误对于用户显示为应用程序崩溃
  * `ERROR` - 用于意外异常或意外网络协议错误
  * `WARN` - 用于记录不视为严重错误的使用情况警告，例如使用了不推荐的 API 或网络响应速度慢
  * `INFO` - 用于报告初始化事件以及其他可能重要但不紧急的数据
  * `DEBUG` - 用于报告调试语句，以帮助开发者解决应用程序缺陷


### 日志级别方案
{: #log-level-scenario notoc}

当记录器级别配置为 `FATAL` 时，记录器会捕获未捕获的异常，但是不会捕获导致崩溃事件的任何日志。您可以设置更详细的记录器级别，以确保同时捕获可能导致 `FATAL` 记录器条目的日志，如 `WARN` 和 `ERROR`。

记录器级别设置为 `DEBUG` 时，您还可以获取 Mobile Analytics 客户端 SDK 记录，在您发送日志时该记录也包含在内。

<!-- **Note:** Find full Logger API references for each platform at [SDKs, samples, API reference](sdks-samples-apis.html). The Logger API is part of the--> <!--{{site.data.keyword.mobileanalytics_short}} Client SDK Core. -->


### 记录器使用情况示例
{: #sample-logger-usage notoc}

**注**：在使用此日志记录框架之前，请确保已检测应用程序，可使用 {{site.data.keyword.mobileanalytics_short}} 客户端 SDK。
 
以下代码片段显示了样本记录器用法：

- Android
	
	```
	// 将记录器配置为将日志保存到设备，以便日后
	// 可以将日志发送到 Mobile Analytics 服务
	// 缺省情况下会禁用；设置为 true 以启用
	Logger.storeLogs(true);
	// 更改最低日志级别（可选）
	// 缺省设置为 Logger.LEVEL.DEBUG
	Logger.setLogLevel(Logger.LEVEL.INFO);
	// 创建两个记录器实例
	// 可以创建多个日志实例来组织日志
	Logger logger1 = Logger.getLogger("logger1");
	Logger logger2 = Logger.getLogger("logger2");
	// 具有不同级别的日志消息
	// 功能 1 的调试消息
	// 功能 2 的调试消息
	logger1.debug("debug message");
	// 未记录 logger1.debug 消息，因为 logLevelFilter 设置为 Info
	logger2.info("info message");
	// 将日志发送到 Mobile Analytics 服务
	Logger.send(new ResponseListener() {
		@Override
            public void onSuccess(Response response) {
                // Handle Logger send success here.
                    }

                    @Override
            public void onFailure(Response response, Throwable throwable, JSONObject jsonObject) {
                // Handle Logger send failure here.
                    }
                });        
	```
	{: codeblock}


- iOS (Swift)
	
	```
	// 将记录器配置为将日志保存到设备，以便日后
	// 可以将日志发送到 Mobile Analytics 服务
	// 缺省情况下会禁用；设置为 true 以启用
	Logger.isLogStorageEnabled = true
	// 更改最低日志级别（可选）
	// 缺省设置为 LogLevel.debug
	Logger.logLevelFilter = LogLevel.info
	// 创建两个记录器实例
	// 可以创建多个日志实例来组织日志
	let logger1 = Logger.logger(name: "feature1Logger")
	let logger2 = Logger.logger(name: "feature2Logger")
	// 具有不同级别的日志消息
	logger1.debug(message: "debug message for feature 1")
	// The logger1.debug message is not logged because the 
// logLevelFilter is set to info
logger2.info(message: "info message for feature 2")

// Send logs to the Mobile Analytics Service
Logger.send(completionHandler: { (response: Response?, error: Error?) in
	        if let response = response {
	        logger.debug(message: "Status code: \(response.statusCode)")
        logger.debug(message: "Response: \(response.responseText)")
    }
    if let error = error {
        logger.error(message: "Error: \(error)")
	    }
	})
	```
	{: codeblock}

	**提示**：出于隐私考虑，您可以对在发布方式下构建的应用程序，禁用记录器输出。缺省情况下，记录器类会将日志打印到 Xcode 控制台。在目标的构建设置中，将 `-D RELEASE_BUILD` 标记添加到发布构建配置的**其他 Swift 标记**部分。
    

- Cordova

	```
	// 启用持久存储日志
	BMSLogger.storeLogs(true);
	// 设置要打印和持久存储的最低日志级别
	BMSLogger.setLogLevel(BMSLogger.INFO);
	var logger1 = BMSLogger.getLogger("logger1");
	var logger2 = BMSLogger.getLogger("logger2");   
	// 具有不同级别的日志消息
	logger1.debug ("debug message");
	logger2.info ("info message");
	// 将持久存储的日志发送到 {{site.data.keyword.mobileanalytics_short}} 服务
	BMSLogger.send();
	BMSAnalytics.send();
	```
	{: codeblock}

- Web

	```
	// 启用持久存储日志
	BMSAnalytics.Logger.storeLogs(true);
	// 设置要打印和持久存储的最低日志级别   
	// 按降序详细级别列出的日志级别：trace,debug,log,info,warn,error,fatal,analytics  
	BMSAnalytics.Logger.setLogLevel('error');
	// 具有不同级别的日志消息
	BMSAnalytics.Logger.debug ("debug message");
	BMSAnalytics.Logger.info ("info message");
	// 将持久存储的日志发送到 {{site.data.keyword.mobileanalytics_short}} 服务
	BMSAnalytics.Logger.send();
	BMSAnalytics.send().then(function(result) {
		// 在此句柄成功
        }, function(err) {
         	// 在此句柄失败
	 });;
	```
	{: codeblock}

<!--## Enabling the {{site.data.keyword.mobileanalytics_short}} Client SDK internal logs
{: #enable-logger-sdklogs notoc}

The {{site.data.keyword.mobileanalytics_short}} Client SDK provides a better development experience by not unnecessarily increasing the console output with its internal debug messages. Therefore, by default, internal log messages that are produced by the {{site.data.keyword.mobileanalytics_short}} SDK with the DEBUG level are not printed. You can enable printing of all internal log messages of the {{site.data.keyword.mobileanalytics_short}} Client SDK with the following API:

- Android
	```
	Logger.setSDKDebugLoggingEnabled(true);
	```
	{: codeblock}

- iOS - Swift
	```
	Logger.sdkDebugLoggingEnabled = true
	```
	{: codeblock}
-->

## 位置数据日志记录 
{: #location-logging}

移动设备的位置可能会在应用程序中通过提供的此 API 进行日志记录。
```
Analytics.logLocation();
 
``` 
此 API 支持应用程序在 Appsession 之间将其位置作为纬度和经度发送到服务器。除了对位置日志记录 API SDK 的显式调用会发送每个 App-Session 的设备位置外，还会发送初始 AppSession 上下文和 userswitch AppSession（即在应用程序会话之间切换用户）上下文的设备位置。位置 API 需要在前面提到的 SDK 初始化中启用。


**注**：要调用此位置日志记录 API，请在 SDK 初始化中将 `collectLocation` 参数设置为 true，如下所示。
```
Analytics.initialize(appName, apiKey,  hasUserContext, collectLocation, [BMSAnalytics.ALL])
		
```





## 发起网络请求
{: #network-requests}

您可以配置 {{site.data.keyword.mobileanalytics_short}} 客户端 SDK 以[发起网络请求](/docs/mobile/sdk_network_request.html)。确保已经初始化 `BMSClient` 和 `BMSAnalytics`，并已导入客户端 SDK。

<!--
#### Android
{: #android-network-requests notoc}

**Note:** This code snippet assumes that you have [imported the Client SDKs](#android-import).

```
public void makeGetCall(){
    Thread thread = new Thread(new Runnable() {
        @Override
        public void run() {
            try  {
                Request request = new Request("http://httpbin.org/get", "GET");
                    request.send(null, null);
            } catch (Exception e) {
                // Handle failure here.
            }
        }
    });
    thread.start();
}
```
	{: codeblock}

-->

<!-- 
#### Swift 3.0
{: #ios-network-requests notoc}

 ```Swift
 	// Make a network request
	let customResourceURL = "<your resource URL>"
	let request = Request(url: customResourceURL, method: HttpMethod.GET)

	let callBack:BMSCompletionHandler = {(response: Response?, error: Error?) in
   	if error == nil {
       	    print ("response:\(response?.responseText), no error")
    	  } else {
       	    print ("error: \(error)")
    	}
	}
	request.send(completionHandler: callBack)
 ```
	{: codeblock}
 
 -->

<!-- Commenting out bmsurlsession
```
// Make a network request
let urlSession = BMSURLSession(configuration: .default, delegate: nil, delegateQueue: nil)
var request = URLRequest(url: URL(string: "http://httpbin.org/get")!)
request.httpMethod = "GET"
request.allHTTPHeaderFields = ["foo":"bar"]

urlSession.dataTask(with: request) { (data: Data?, response: URLResponse?, error: Error?) in
    if let httpResponse = response as? HTTPURLResponse {
        logger.info(message: "Status code: \(httpResponse.statusCode)")
    }
    if data != nil, let responseString = String(data: data!, encoding: .utf8) {
        logger.info(message: "Response data: \(responseString)")
    }
    if let error = error {
        logger.error(message: "Error: \(error)")
    }
}.resume()
```
	{: codeblock}
-->

<!--
#### Swift 2.2
{: ios-swift22-network-requests}

```Swift
 	// Make a network request
	let customResourceURL = "<your resource URL>"
	let request = Request(url: customResourceURL, method: HttpMethod.GET)

	let callBack:BMSCompletionHandler = {(response: Response?, error: NSError?) in
   	if error == nil {
       	    print ("response:\(response?.responseText), no error")
    	  } else {
       	    print ("error: \(error)")
    	}
	}
	request.send(completionHandler: callBack)
 ```
	{: codeblock}
-->
<!--
```
// Make a network request
let urlSession = BMSURLSession(configuration: .defaultSessionConfiguration(), delegate: nil, delegateQueue: nil)
let request = NSMutableURLRequest(URL: NSURL(string: "http://httpbin.org/get")!)
request.HTTPMethod = "GET"
request.allHTTPHeaderFields = ["foo":"bar"]

urlSession.dataTaskWithRequest(request) { (data: NSData?, response: NSURLResponse?, error: NSError?) in
    if let httpResponse = response as? NSHTTPURLResponse {
        logger.info(message: "Status code: \(httpResponse.statusCode)")
    }
    if data != nil, let responseString = NSString(data: data!, encoding: NSUTF8StringEncoding) {
        logger.info(message: "Response data: \(responseString)")
    }
    if let error = error {
        logger.error(message: "Error: \(error)")
    }
}.resume()
```
	{: codeblock}
-->
<!--
#### Cordova
{: #cordova-network-requests notoc}

```
var success = function(data){
     console.log("success", data);
 }
 var failure = function(error)
     {console.log("failure", error);
 }
 var request = new BMSRequest("<your application route>", BMSRequest.GET);
 request.send(success, failure);
```
	{: codeblock}

-->


## 报告崩溃分析
{: #report-crash-analytics}

您可以通过将分析和日志信息发送到 {{site.data.keyword.mobileanalytics_short}} 来查看[应用程序崩溃数据](app-monitoring.html#monitor-app-crash)。

`Analytics.send()` 方法会在**崩溃**页面填充**崩溃概述**和**崩溃**表。本部分的图表通过初始化和发送过程启用以供分析之用；无需任何特殊配置。

`Logger.send()` 方法会在**故障诊断**页面填充**崩溃摘要**和**崩溃详细信息**表。您必须使您的应用程序能够储存和发送日志，才能通过在应用程序代码中添加额外的语句，来填充本部分的图表。


- Android

	`Logger.storeLogs(true);`
	<!-- * `Logger.setLogLevel(Logger.LEVEL.FATAL); // or greater` -->
	
	查看 Android [样本记录器用法](sdk.html##sample-logger-usage)。


- iOS

	`Logger.isLogStorageEnabled = true`
	<!-- * `Logger.logLevelFilter = LogLevel.Fatal // or greater` -->
	
	查看 iOS [样本记录器用法](sdk.html##sample-logger-usage)。


- Cordova

	 `BMSLogger.storeLogs(true);`
	<!-- * `Logger.logLevelFilter = LogLevel.Fatal // or greater` -->

	查看 Cordova [样本记录器用法](sdk.html##sample-logger-usage)。

- Web

	`BMSAnalytics.Logger.storeLogs(true);`

## 跟踪活动用户
{: #trackingusers}

如果您的应用程序可以识别设备上的非重复用户，那么通过将活动用户的用户名传递到 {{site.data.keyword.mobileanalytics_short}} ，您可以选择跟踪有多少用户正在积极使用您的应用程序。 

通过使用 `hasUserContext=true` 初始化 {{site.data.keyword.mobileanalytics_short}} 来启用用户跟踪。否则，{{site.data.keyword.mobileanalytics_short}} 仅会从每个设备捕获一个用户。 


- Android

	添加下列代码，以在用户登录时进行跟踪：
	
	```
	Analytics.setUserIdentity("username");
```
	{: codeblock}
	
	<!--Add the following code for when the user logs out:
	
	```
	Analytics.clearUserIdentity();
	```
	{: codeblock}
	-->

- iOS (Swift)

	添加下列代码，以在用户登录时进行跟踪：
	
	```
	Analytics.userIdentity = "username"
```
	{: codeblock}
	
	<!--
	Add the following code for when the user logs out:
	
	```
	Analytics.userIdentity = nil
	```
	{: codeblock}
	-->


- Cordova
	
	添加下列代码，以在用户登录时进行跟踪：
	
	```
	BMSAnalytics.setUserIdentity("username");
```
	{: codeblock}

- Web

	添加下列代码，以在用户登录时进行跟踪：
	
	```
	BMSAnalytics.setUserIdentity("username");
```
	{: codeblock}

## 应用程序内反馈分析
{: #In-App}

应用程序内反馈分析支持**用户和测试者**向应用程序所有者提供丰富的上下文反馈。**应用程序所有者**从其用户那里获取基于应用程序使用情况的实时反馈。**开发者**根据实时洞察来实施更改。

调用以下 API 来检测移动应用程序，以进入反馈方式。 

- Android

    ```
    ImageButton feedback =(ImageButton)findViewById(R.id.Feedback);
        feedback.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Analytics.triggerFeedbackMode();
            }
        });
    ```	
	{: codeblock}
	
<!--## Configuring MobileFirst Platform Foundation servers to use the {{site.data.keyword.mobileanalytics_short}} service (optional)
{: #configmfp notoc}
  If you are using MobileFirst Platform Foundation Server V7 and higher, you can configure it to use the {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.mobileanalytics_short}} service to store analytics and logged data. 
  
  Configure MobileFirst Platform V7.0, V7.1, and V8.0 Beta servers to send analytics data to the {{site.data.keyword.mobileanalytics_short}} service on {{site.data.keyword.Bluemix_notm}}.

  1. Visit the dashboard for the {{site.data.keyword.mobileanalytics_short}} service where you want to send analytics data and note the browser URL for the dashboard.
  2. Determine the value for reporting analytics, as follows:
  	1. Get the {{site.data.keyword.mobileanalytics_short}} service route from the dashboard URL. The {{site.data.keyword.mobileanalytics_short}} service route is the part of the URL before ``/analytics/console/dashboard``.  

  		For example, if the dashboard URL is: `http://mobile-analytics-dashboard.ng.bluemix.net/analytics/console/dashboard?instanceId=12345abcde`
      {: screen}

  		then the Analytics Service Route is
      `http://mobile-analytics-dashboard.ng.bluemix.net`
      {: screen}

  	2. Get the [Client API Key](#analytics-clientkey) value from the Analytics dashboard.

  	You will use the {{site.data.keyword.mobileanalytics_short}} service route and API Key to construct a URL to report analytics data, depending on the version of your MobileFirst Platform server. -->

<!--  3. Copy the URL for your {{site.data.keyword.mobileanalytics_short}} service dashboard. Include the `instanceId` query parameter, for example:
      `http://mobile-analytics-dashboard.ng.bluemix.net/analytics/console/dashboard?instanceId=1212345abcde`
      {: screen}

  4. Configure the values for the MobileFirst Platform server JNDI properties, as follows:-->

<!--    ### MobileFirst Platform V7.0
    {: #mfp70 notoc}

        The format of the `wl.analytics.url` JNDI property is: `<Analytics Service Route>/analytics-service/rest/data?tenant=<Client API Key>`
        {: screen}

        The `wl.analytics.console.url` JNDI property is the Analytics service dashboard URL.

        #### Example of MobileFirst Platform V7.0 JNDI property values
        {: #example-mfp70-jndi-values notoc}

        For a MobileFirst Platform project named `Myproj7000`, based on the examples in steps 2 and 3, replace the current JNDI property values in the `server.xml` file with:
        ```
        <jndiEntry jndiName="MyProj7000/wl.analytics.url" value='"http://mobile-analytics-dashboard.ng.bluemix.net/analytics-service/rest/data?tenant=12345abcde"'/>
        ```
        {: screen}
        ```
        <jndiEntry jndiName="MyProj7000/wl.analytics.console.url" value='"http://mobile-analytics-dashboard.ng.bluemix.net/analytics/console/dashboard?instanceId=12345abcde"'/>
        ```
        {: screen}

    ### MobileFirst Platform V7.1
    {: #mfp71 notoc}

      The format of the `wl.analytics.url` JNDI property is: `<Analytics Service Route>/analytics-service/rest/v2/<Client API Key>`
      {: screen}

      #### Example of MobileFirst Platform JNDI V7.1 property values
      {: #example-mfp71-jndi-values notoc}

      For a MobileFirst Platform project named `MyProj7101`, replace the current JNDI property values in the `server.xml` file with:
      ```
      <jndiEntry jndiName="MyProj7101/wl.analytics.url" value='"http://mobile-analytics-dashboard.ng.bluemix.net/analytics-service/rest/v2/data?tenant=12345abcde"'/>
      ```
      {: screen}
      ```
      <jndiEntry jndiName="MyProj7101/wl.analytics.console.url" value='"http://mobile-analytics-dashboard.ng.bluemix.net/analytics/console/dashboard?instanceId=12345abcde"'/>
      ```
      {: screen}

      ### MobileFirst Platform V8.0
      {: #mfp80 notoc}

      The format of the `mfp.analytics.url` JNDI property is:
      `<Analytics Service Route>/analytics-service/rest/v2/<Client API Key>`  

    #### Example MobileFirst Platform V8.0 Beta JNDI property values
      {: example-mfp80b-jndi-values}

      For a MobileFirst Platform project named `mfp`, which is the default, replace the current JNDI property values in the `server.xml` file with:
      ```
      <jndiEntry jndiName="mfp/mfp.analytics.url" value='"http://mobile-analytics-dashboard.ng.bluemix.net/analytics-service/rest/data?tenant=12345abcde"'/>
      ```
      {: screen}
      ```
      <jndiEntry jndiName="mfp/mfp.analytics.console.url" value='"http://mobile-analytics-dashboard.ng.bluemix.net/analytics/console/dashboard?instanceId=12345abcde"'/>
      ```
      {: screen}
-->
<!-- #### Ignored events and event retention
{: #ignored-events notoc}
The {{site.data.keyword.mobileanalytics_short}} service saves the following data for ignored events and event retention:
  
<dl>	
<dt>Ignored events</dt>
	<dd>`ANALYTICS_SDK_CFG_IGNORE_AppPushAction: true`
		  `ANALYTICS_SDK_CFG_IGNORE_ServerLog: true`
		  `ANALYTICS_SDK_CFG_IGNORE_NetworkTransaction: true`
		  `ANALYTICS_SDK_CFG_IGNORE_NetworkTransactionSummarizedHourly: true`
		  `ANALYTICS_SDK_CFG_IGNORE_PushNotification: true`
		  `ANALYTICS_SDK_CFG_IGNORE_PushSubscription: true`</dd>
</dt>
<dt>Event retention</dd>
<dd>
`ANALYTICS_TTL_AlertNotification: 14d`<br>
`ANALYTICS_TTL_CustomData: 7d`<br>
`ANALYTICS_TTL_Device: 90d`<br>
`ANALYTICS_TTL_AppLog: 3d`<br>
`ANALYTICS_TTL_AppSession: 7d`
</dd>
</dt>
</dl>
  
-->


## 后续操作
{: #what-to-do-next notoc}

您现在可以转到 {{site.data.keyword.mobileanalytics_short}} Console，以查看使用情况分析，如使用应用程序的新设备和设备总数。您还可以通过<!--[creating custom charts](app-monitoring.html#custom-charts),-->[设置警报](app-monitoring.html#alerts)和[监视应用程序崩溃](app-monitoring.html#monitor-app-crash)来监视应用程序。


# 相关链接
{: #rellinks notoc}

## API 参考
{: #api notoc}

* [REST API ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://mobile-analytics-dashboard.{DomainName}/analytics-service/){:new_window}
