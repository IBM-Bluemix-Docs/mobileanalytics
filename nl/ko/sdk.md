---

copyright:
  years: 2015, 2017
lastupdated: "2018-01-18"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 애플리케이션 인스트루먼테이션
{: #mobileanalytics_sdk}

## {{site.data.keyword.mobileanalytics_short}} 클라이언트 SDK를 사용하도록 애플리케이션 인스트루먼트

{{site.data.keyword.mobileanalytics_full}} SDK를 사용하면 모바일 애플리케이션을 인스트루먼트할 수 있습니다.
{: shortdesc}

{{site.data.keyword.mobileanalytics_short}}를 사용하면 다음 카테고리의 데이터를 수집할 수 있으며 각각 다른 정도의 인스트루먼테이션이 필요합니다.


- 사전 정의된 데이터 - 이 카테고리에는 모든 애플리케이션에 적용되는 일반 사용 정보와 디바이스 정보가 포함됩니다. 이 카테고리 내에는 볼륨, 빈도 또는 애플리케이션 사용 기간을 표시하는 디바이스 메타데이터(운영 체제 및 디바이스 모델)와 사용 데이터(활성 사용자 및 애플리케이션 세션)가 있습니다. 사전 정의된 데이터는 애플리케이션에서 {{site.data.keyword.mobileanalytics_short}} SDK를 초기화한 후 자동으로 수집됩니다.

- 애플리케이션 로그 메시지 - 개발자는 이 카테고리에서 개발과 디버깅을 지원하기 위해 사용자 정의 메시지를 로그하는 애플리케이션을 통해 코드의 행을 추가할 수 있습니다. 개발자는 각 로그 메시지에 심각도/상세도 레벨을 지정하고, 레벨을 지정하여 차후에 메시지를 필터링하거나 주어진 로그 레벨보다 낮은 레벨의 메시지를 무시하도록 애플리케이션을 구성하여 스토리지 영역을 유지할 수 있습니다. 애플리케이션 로그 데이터를 수집하려면 로그 메시지마다 한 행의 코드를 추가할 뿐 아니라 애플리케이션에서 {{site.data.keyword.mobileanalytics_short}} SDK를 초기화해야 합니다.

- 사용자 정의 이벤트 - 이 카테고리에는 자체적으로 정의하고 사용자 앱에 특정적인 데이터가 포함됩니다. 이 데이터는 페이지 보기, 단추 탭 또는 인앱(In-App) 구매 등과 같이 인앱(In-App)에서 발생하는 이벤트를 표시합니다. 사용자 앱에서 {{site.data.keyword.mobileanalytics_short}} SDK를 초기화하는 외에 추적하려는 각 사용자 정의 이벤트에 대한 코드의 행을 추가해야 합니다. 

현재 SDK는 Android, iOS, WatchOS, Cordova 및 웹에서 사용 가능합니다.

## 서비스 신임 정보 API 키 값 식별
{: #analytics-clientkey}

클라이언트 SDK를 설정하기 전에 **API 키** 값을 식별하십시오. API 키는 클라이언트 SDK를 초기화하는 데 필요합니다.

1. {{site.data.keyword.mobileanalytics_short}} 서비스 대시보드를 여십시오.
1. **신임 정보 보기**를 펼쳐 API 키 값을 표시하십시오. {{site.data.keyword.mobileanalytics_short}} 클라이언트 SDK를 초기화하는 경우 API 키 값이 필요합니다.


## 분석을 수집하기 위해 애플리케이션 초기화
{: #initalize-ma-sdk}

{{site.data.keyword.mobileanalytics_short}} 서비스로 로그를 전송할 수 있도록 애플리케이션을 초기화하십시오.

1. 클라이언트 SDK를 가져오십시오.
	- Android
	
		다음 `import` 문을 프로젝트 파일의 시작 부분에 추가하십시오.
		
		```
		import com.ibm.mobilefirstplatform.clientsdk.android.core.api.*;
		import com.ibm.mobilefirstplatform.clientsdk.android.analytics.api.*;
		import com.ibm.mobilefirstplatform.clientsdk.android.logger.api.*;
		```
		{: codeblock}
  
	- iOS
		
		Swift SDK는 iOS 및 watchOS에 대해 사용 가능합니다.	다음 `import` 문을 `AppDelegate.swift` 프로젝트 파일의 시작 부분에 추가하여 `BMSCore` 프레임워크와 `BMSAnalytics` 프레임워크를 가져오십시오.
	
		```Swift
		import BMSCore
		import BMSAnalytics
		```
		{: codeblock}  
   
	- Cordova
			
		Cordova 애플리케이션 루트 디렉토리에서 다음 명령을 실행하여 Cordova 플러그인을 추가하십시오.
	
		```Javascript
		cordova plugin add bms-core
		```
		{: codeblock}  

	- 웹
			
		스크립트로 제공된 SDK를 index.html에 추가하여 웹 플러그인을 추가하십시오.
	
		```Html
		<script src="/path/to/bms-clientsdk-web-analytics/bmsanalytics.js"></script>
		```
		{: codeblock} 	 	

	 	또는 모듈 로더 requirejs를 사용하여 웹 플러그인을 추가하십시오. 
	
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

2. 애플리케이션의 {{site.data.keyword.mobileanalytics_short}} 클라이언트 SDK를 초기화하십시오.

	- Android
		
		Android 애플리케이션에서 기본 활동의 `onCreate` 메소드에 또는 프로젝트에 가장 적합한 위치에 초기화 코드를 추가하여 Android 애플리케이션의 {{site.data.keyword.mobileanalytics_short}} 클라이언트 SDK를 초기화하십시오.
	
		```Java
		BMSClient.getInstance().initialize(getApplicationContext(), BMSClient.REGION_US_SOUTH); // Make sure that you point to your region
		```
		{: codeblock}
	
		**bluemixRegion** 매개변수를 사용하여 `BMSClient`를 초기화해야 합니다. 초기자(initializer)에서 **bluemixRegion** 값은 사용자가 사용 중인 {{site.data.keyword.Bluemix_notm}} 배치를 지정합니다(예: `BMSClient.REGION_US_SOUTH` 및 `BMSClient.REGION_UK`).
	    <!-- , or `BMSClient.REGION_SYDNEY`.--> 
    
	- iOS
	    
		먼저 다음 코드를 사용하여 `BMSClient` 클래스를 초기화하십시오. 애플리케이션 위임의 `application(_:didFinishLaunchingWithOptions:)` 메소드에 또는 프로젝트에 가장 적합한 위치에 초기화 코드를 넣으십시오.
		
		```Swift 
		BMSClient.sharedInstance.initialize(bluemixRegion: BMSClient.Region.usSouth) // Make sure that you point to your region
		```
		{: codeblock}
	
		**bluemixRegion** 매개변수를 사용하여 `BMSClient`를 초기화해야 합니다. 초기자(initializer)에서 **bluemixRegion** 값은 사용자가 사용 중인 {{site.data.keyword.Bluemix_notm}} 배치를 지정합니다(예: `BMSClient.Region.usSouth` 또는 `BMSClient.Region.unitedKingdom`).
	    <!-- , or `BMSClient.Region.Sydney`. -->
    
	- Cordova
	  
		**BMSClient** 및 **BMSAnalytics**를 초기화하십시오. [**API 키**](#analytics-clientkey) 값이 필요합니다.
	
		```Javascript
		BMSClient.initialize(BMSClient.REGION_US_SOUTH); //Make sure you point to your region	
		```
		{: codeblock}
		
		{{site.data.keyword.mobileanalytics_short}} 클라이언트 SDK를 사용하려면 **bluemixRegion** 매개변수를 사용하여 `BMSClient`를 초기화해야 합니다. 초기자(initializer)에서 **bluemixRegion** 값은 사용자가 사용 중인 {{site.data.keyword.Bluemix_notm}} 배치를 지정합니다(예: `BMSClient.REGION_US_SOUTH` 또는 `BMSClient.REGION_UK`).
	    <!-- , or `BMSClient.REGION_SYDNEY`. -->
    
	- Web

	    애플리케이션 코드 내에서 클라이언트 SDK를 초기화하여 사용 분석과 애플리케이션 세션을 기록하십시오(API 키 값 사용).
     ```javascript
	    BMSAnalytics.Client.initialize(BMSAnalytics.Client.REGION_US_SOUTH);
	    ```
	    {: codeblock}
		
		{{site.data.keyword.mobileanalytics_short}} 클라이언트 SDK를 사용하려면, **bluemixRegion** 매개변수를 사용하여 `BMSAnalytics.Client`를 초기화해야 합니다. 초기자(initializer)에서 **bluemixRegion** 값은 사용자가 사용 중인 {{site.data.keyword.Bluemix_notm}} 배치를 지정합니다(예: `BMSAnalytics.Client..REGION_UK` 또는 `BMSAnalytics.Client..REGION_US_SOUTH`).
	    <!-- , or `BMSClient.REGION_SYDNEY`. -->
    
3. 애플리케이션 오브젝트를 사용하고 애플리케이션의 이름을 제공하여 Analytics를 초기화하십시오.

	애플리케이션(`your_app_name_here`)에 사용하도록 선택한 이름이 {{site.data.keyword.mobileanalytics_short}} 콘솔에 애플리케이션 이름으로 표시됩니다. 애플리케이션 이름은 대시보드에서 애플리케이션 로그를 검색하는 필터로 사용됩니다. 플랫폼(예: Android 및 iOS)에 걸쳐 동일한 애플리케이션 이름을 사용하는 경우, 로그가 전송된 플랫폼에 상관없이 동일한 이름 아래에서 애플리케이션의 모든 로그를 볼 수 있습니다.

	[API 키](#analytics-clientkey) 값도 필요합니다.

- Android
		
	```Java
		// In this code example, Analytics is configured to record lifecycle events.
		Analytics.init(getApplication(), "your_app_name_here", apiKey, hasUserContext, collectLocation, Analytics.DeviceEvent.ALL);
	```
    {: codeblock}
		
	**참고:** `hasUserContext`에 대한 값을 **true** 또는 **false**로 설정하십시오. false(기본값)인 경우 각 디바이스는 활성 사용자로 계수됩니다. 디바이스별로 활발하게 애플리케이션을 사용 중인 사용자의 수를 추적할 수 있는 [`Analytics.setUserIdentity("username")`](sdk.html#android-tracking-users) 메소드는 `hasUserContext`가 false인 경우 작동하지 않습니다. true인 경우에는 [`Analytics.setUserIdentity("username")`](sdk.html#android-tracking-users)의 각 사용이 활성 사용자로 계산됩니다. `hasUserContext`가 true인 경우 기본 사용자 ID가 없으므로 활성 사용자 차트를 채우도록 설정되어야 합니다.
	앱이 디바이스 위치로 전송할 수 있는 `Analytics.logLocation()` 메소드는 `collectLocation`이 true로 설정된 경우 작동합니다.
		
		
	
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
	 	
    선택적 `deviceEvents` 매개변수는 디바이스 레벨 이벤트에 대한 분석을 자동으로 수집합니다.
		
    `hasUserContext`에 대한 값을 **true** 또는 **false**로 설정하십시오. false(기본값)인 경우 각 디바이스는 활성 사용자로 계수됩니다. 디바이스별로 활발하게 애플리케이션을 사용 중인 사용자의 수를 추적할 수 있는 [`Analytics.userIdentity = "username"`](sdk.html#ios-tracking-users) 메소드는 `hasUserContext`가 false인 경우 작동하지 않습니다. `hasUserContext`가 true인 경우에는 [`Analytics.userIdentity = "username"`](sdk.html#ios-tracking-users)의 각 사용이 활성 사용자로 계산됩니다. `hasUserContext`가 true인 경우 기본 사용자 ID가 없으므로 활성 사용자 차트를 채우도록 설정되어야 합니다.
   	앱이 디바이스 위치로 전송할 수 있는 `Analytics.logLocation()` 메소드는 `collectLocation`이 true로 설정된 경우 작동합니다.  		
	
- watchOS
	
    `Analytics.recordApplicationDidBecomeActive()` 및 `Analytics.recordApplicationWillResignActive()` 메소드를 사용하여 WatchOS의 디바이스 이벤트를 기록할 수 있습니다.
	
    ExtensionDelegate 클래스의 `applicationDidBecomeActive()` 메소드에 다음 행을 추가하십시오.
	
	```Javascript
		Analytics.recordApplicationDidBecomeActive()
	```
    {: codeblock}
	
    다음 행을 ExtensionDelegate 클래스의 `applicationWillResignActive()` 메소드에 추가하십시오.
	
	```Javascript
		Analytics.recordApplicationWillResignActive()
	```
    {: codeblock}	
		
- Cordova
		
	```Javascript
	Analytics.initialize(appName, apiKey,  hasUserContext, collectLocation, [BMSAnalytics.ALL])
	```
    {: codeblock}	
		
    `hasUserContext`에 대한 값을 **true** 또는 **false**로 설정하십시오. false(기본값)인 경우 각 디바이스는 활성 사용자로 계수됩니다. 디바이스별로 활발하게 애플리케이션을 사용 중인 사용자의 수를 추적할 수 있는 `Analytics.setUserIdentity("username")` 메소드는 `hasUserContext`가 false인 경우 작동하지 않습니다. true인 경우에는 `Analytics.setUserIdentity("username")`(sdk.html#android-tracking-users)의 각 사용이 활성 사용자로 계산됩니다. `hasUserContext`가 true인 경우 기본 사용자 ID가 없으므로 활성 사용자 차트를 채우도록 설정되어야 합니다.
   	앱이 디바이스 위치로 전송할 수 있는 `Analytics.logLocation()` 메소드는 `collectLocation`이 true로 설정된 경우 작동합니다.  		
	
- 웹
		
	```Java		
		// In this code example, Analytics is configured to record allevents.
		BMSAnalytics.initialize(appName, apiKey, hasUserContext, BMSAnalytics.DeviceEvent.ALL);
	```
    {: codeblock}
		
    `hasUserContext`에 대한 값을 **true** 또는 **false**로 설정하십시오. false(기본값)인 경우 각 디바이스는 활성 사용자로 계수됩니다. 디바이스별로 활발하게 애플리케이션을 사용 중인 사용자의 수를 추적할 수 있는 [`BMSAnalytics.setUserIdentity("username")`](sdk.html#web-tracking-users) 메소드는 `hasUserContext`가 false인 경우 작동하지 않습니다. true인 경우에는 [`BMSAnalytics.setUserIdentity("username")`](sdk.html#web-tracking-users)의 각 사용이 활성 사용자로 계산됩니다. `hasUserContext`가 true인 경우 기본 사용자 ID가 없으므로 활성 사용자 차트를 채우도록 설정되어야 합니다.

4. 이제 분석을 수집할 수 있도록 애플리케이션을 초기화했습니다. 다음에는 {{site.data.keyword.mobileanalytics_short}} 서비스로 [분석 데이터를 전송](sdk.html#app-monitoring-gathering-analytics)할 수 있습니다.


## 사용 분석 수집
{: #app-monitoring-gathering-analytics}

사용 분석을 기록하고 기록한 데이터를 {{site.data.keyword.mobileanalytics_short}} 서비스에 전송하도록 {{site.data.keyword.mobileanalytics_short}} 클라이언트 SDK를 구성할 수 있습니다.

다음 API를 사용하여 사용 분석 기록 및 전송을 시작하십시오.

- Android
	
	```
	// Disable recording of usage analytics (for example, to save disk space)
	// Recording is enabled by default
	Analytics.disable();
	// Enable recording of usage analytics
	Analytics.enable();
	// Send recorded usage analytics to the Mobile Analytics Service
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
		
	이벤트 로깅을 위한 샘플 사용법 분석:
		
	```
	// Log a custom analytics event
	JSONObject eventJSONObject = new JSONObject();
	eventJSONObject.put("customProperty" , "propertyValue");
	Analytics.log(eventJSONObject);
	```
	{: codeblock}


- iOS(Swift)

	```
	// Disable recording of usage analytics (for example, to save disk space)
	// Recording is enabled by default
	Analytics.isEnabled = false
	// Enable recording of usage analytics
	Analytics.isEnabled = true
	// Send recorded usage analytics to the Mobile Analytics Service
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
	
	이벤트 로깅을 위한 샘플 사용법 분석:
	
	```Swift
	// Log a custom analytics event
	let eventObject = ["customProperty": "propertyValue"]
	Analytics.log(metadata: eventObject)
	```
	{: codeblock}

- Cordova

	```JavaScript
	// Enable usage analytics recording
	BMSAnalytics.enable();
	// Disable usage analytics recording
	BMSAnalytics.disable();
	// Send recorded usage analytics to the {{site.data.keyword.mobileanalytics_short}} Service
	BMSAnalytics.send(
		function(response) {
			console.log('success: ' + response);
	},
	function (err) {
			console.log('fail: ' + err);
	});
	```
	{: codeblock}
	
	이벤트 로깅을 위한 샘플 사용법 분석:
	
	```JavaScript
	// Log a custom analytics event
	var eventObject = {"customProperty": "propertyValue"}
	BMSAnalytics.log(eventObject)
	```
	{: codeblock}

	Cordova 애플리케이션을 개발 중인 경우 기본 API를 사용하여 애플리케이션 라이프사이클 이벤트 레코딩을 사용으로 설정하십시오.

- 웹
		
	```
	// Disable recording of usage analytics (for example, to save disk space)
	// Recording is enabled by default
	BMSAnalytics.disable();
	// Enable recording of usage analytics
	BMSAnalytics.enable();
	// Send recorded usage analytics to the Mobile Analytics Service
	BMSAnalytics.send().then(function(result) {
         	//Handle Success here
        }, function(err) {
                //Handle Failure here
        });;
	```
	{: codeblock}
		
	이벤트 로깅을 위한 샘플 사용법 분석:
		
	```JavaScript
	// Log a custom analytics event
	var eventObject = {"customProperty": "propertyValue"}
	BMSAnalytics.log(eventObject)
	```
	{: codeblock}
  
## 로거 사용 설정, 구성 및 사용

{{site.data.keyword.mobileanalytics_full}} 클라이언트 SDK는 사용자가 익숙할 수 있는 기타 로깅 프레임워크(예: `java.util.logging` 또는 `log4j`)와 유사한 로깅 프레임워크를 제공합니다. 로깅 프레임워크는 다중 패키지별 로거 인스턴스, 다른 로그 레벨, 애플리케이션 충돌에 대한 스택 추적 캡처 등을 지원합니다.

또한 애플리케이션이 실행 중인 디바이스에 로깅된 데이터를 저장하고 나중에 해당 디바이스 로그를 {{site.data.keyword.mobileanalytics_short}} 서비스로 전송하도록 구성할 수 있습니다.

<!-- 초기화는 먼저 로그를 수집하고 {{site.data.keyword.mobileanalytics_short}} 서비스에 로그를 전송할 수 있도록 수행되어야 합니다. -->

{{site.data.keyword.mobileanalytics_short}} 클라이언트 SDK 로깅 프레임워크는 다음 로그 레벨을 지원합니다. 해당 로그 레벨은 가장 자세한 레벨부터 나열되며 권장되는 사용 가이드라인이 함께 제공됩니다.

  * `FATAL` - 복구 불가능한 충돌 또는 정지에 대해 사용됩니다. `FATAL` 레벨은 사용자에게 애플리케이션 충돌로 표시되는 복구 불가능한 오류를 로깅하기 위해 예약됩니다.
  * `ERROR` - 예상치 못한 예외 또는 예상치 못한 네트워크 프로토콜 오류에 대해 사용됩니다.
  * `WARN` - 더 이상 사용되지 않는 API의 사용 또는 느린 네트워크 응답과 같이 중요한 오류로 고려되지 않는 사용 경고를 기록하는 데 사용됩니다.
  * `INFO` - 중요하지만 긴급한 상황은 아닌 기타 데이터 및 초기화 이벤트를 보고하는 데 사용됩니다.
  * `DEBUG` - 개발자가 애플리케이션 결함을 해결하는 데 도움을 주는 디버그 명령문을 보고하는 데 사용됩니다.


### 로그 레벨 시나리오
{: #log-level-scenario notoc}

로거 레벨이 `FATAL`로 구성되어 있는 경우 로거는 미발견 예외를 캡처하지만 충돌 이벤트를 발생시키는 로그는 캡처하지 않습니다. `FATAL` 로거 항목을 발생시킬 수 있는 `WARN` 및 `ERROR` 로그도 캡처되도록 더 상세하게 로거 레벨을 설정할 수 있습니다.

로거 레벨이 `DEBUG`로 설정되는 경우에는 로그를 전송할 때 포함되는 Mobile Analytics 클라이언트 SDK 로그도 얻을 수 있습니다.

<!-- **참고:** [SDK, 샘플, API 참조](sdks-samples-apis.html)에서 각 플랫폼에 대한 전체 로거 API 참조를 검색하십시오. 로거 API는--> <!--{{site.data.keyword.mobileanalytics_short}} 클라이언트 SDK 코어의 일부입니다. -->


### 샘플 로거 사용
{: #sample-logger-usage notoc}

**참고:** 로깅 프레임워크를 사용하기 전에 {{site.data.keyword.mobileanalytics_short}} 클라이언트 SDK를 사용하도록 애플리케이션을 인스트루먼트했는지 확인하십시오.

다음은 샘플 로거 사용법을 표시하는 코드 스니펫입니다.

- Android
	
	```
	// Configure Logger to save logs to the device so that they 
	// can later be sent to the Mobile Analytics service
	// Disabled by default; set to true to enable
	Logger.storeLogs(true);
	// Change the minimum log level (optional)
	// The default setting is Logger.LEVEL.DEBUG
	Logger.setLogLevel(Logger.LEVEL.INFO);
	// Create two logger instances
	// You can create multiple log instances to organize your logs
	Logger logger1 = Logger.getLogger("logger1");
	Logger logger2 = Logger.getLogger("logger2");
	// Log messages with different levels
	// Debug message for feature 1
	// Info message for feature 2
	logger1.debug("debug message"); 
	//the logger1.debug message is not logged because the logLevelFilter is set to Info
	logger2.info("info message");
	// Send logs to the Mobile Analytics Service
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


- iOS(Swift)
	
	```
	// Configure Logger to save logs to the device so that they 
	// can later be sent to the Mobile Analytics service
	// Disabled by default; set to true to enable
	Logger.isLogStorageEnabled = true
	// Change the minimum log level (optional)
	// The default setting is LogLevel.debug
	Logger.logLevelFilter = LogLevel.info
	// Create two logger instances
	// You can create multiple log instances to organize your logs
	let logger1 = Logger.logger(name: "feature1Logger")
	let logger2 = Logger.logger(name: "feature2Logger")
	// Log messages with different levels
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

	**팁:** 개인정보 보호정책과 관련하여 릴리스 모드로 빌드된 애플리케이션의 로거 출력을 사용 안함으로 설정할 수 있습니다. 기본적으로 로거 클래스는 로그를 Xcode 콘솔에 인쇄합니다. 대상에 대한 빌드 설정에서 `-D RELEASE_BUILD` 플래그를 릴리스 빌드 구성의 **기타 Swift 플래그** 섹션에 추가하십시오.


- Cordova

	```
	// Enable persisting logs
	BMSLogger.storeLogs(true);
	// Set the minimum log level to be printed and persisted
	BMSLogger.setLogLevel(BMSLogger.INFO);
	var logger1 = BMSLogger.getLogger("logger1");
	var logger2 = BMSLogger.getLogger("logger2");   
	// Log messages with different levels
	logger1.debug ("debug message");
	logger2.info ("info message");
	// Send persisted logs to the {{site.data.keyword.mobileanalytics_short}} Service
	BMSLogger.send();
	BMSAnalytics.send();
	```
	{: codeblock}

- 웹

	```
	// Enable persisting logs
	BMSAnalytics.Logger.storeLogs(true);
	// Set the minimum log level to be printed and persisted   
	// log levels in descending verbose level trace,debug,log,info,warn,error,fatal,analytics  
	BMSAnalytics.Logger.setLogLevel('error');
	// Log messages with different levels
	BMSAnalytics.Logger.debug ("debug message");
	BMSAnalytics.Logger.info ("info message");
	// Send persisted logs to the {{site.data.keyword.mobileanalytics_short}} Service
	BMSAnalytics.Logger.send();
	BMSAnalytics.send().then(function(result) {
		//Handle Success here
        }, function(err) {
         	//Handle Failure here
	 });;
	```
	{: codeblock}

<!--## {{site.data.keyword.mobileanalytics_short}} 클라이언트 SDK 내부 로그 사용
{: #enable-logger-sdklogs notoc}

{{site.data.keyword.mobileanalytics_short}} 클라이언트 SDK는 해당 내부 디버그 메시지가 포함된 콘솔 출력을 불필요하게 증가시키지 않음으로써 더 나은 개발 환경을 제공합니다. 따라서 기본적으로, DEBUG 레벨의 {{site.data.keyword.mobileanalytics_short}} SDK에서 생성되는 내부 로그 메시지는 인쇄되지 않습니다. 다음 API를 사용하여 {{site.data.keyword.mobileanalytics_short}} 클라이언트 SDK의 모든 내부 로그 메시지를 인쇄하도록 설정할 수 있습니다.

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

## 위치 데이터 로깅
{: #location-logging}

모바일 디바이스의 위치는 제공된 이 API를 통해 앱에서 로깅될 수 있습니다.
```
Analytics.logLocation();
 
``` 
이 API를 통해 앱은 해당 위치를 위도, 경도 정보를 사용하여 앱 세션 간에 서버로 전송할 수 있습니다. 위치-로깅 API에 대한 이 명시적인 호출 외에 SDK는 초기 AppSession 컨텍스트 및 userswitch AppSession(즉, 앱 세션 간에 사용자 전환) 컨텍스트 둘 다에 대해 모든 앱 세션에 대한 디바이스 위치를 전송합니다. 위치 API는 앞서 언급한 대로 SDK의 초기화 중에 사용으로 설정되어야 합니다.

**참고:** 이 위치 로깅 API를 호출하려면, 아래 표시된 대로 `collectLocation` 매개변수를 SDK 초기화에서 true로 설정하십시오.
```
Analytics.initialize(appName, apiKey,  hasUserContext, collectLocation, [BMSAnalytics.ALL])
		
```





## 네트워크 요청 작성
{: #network-requests}

{{site.data.keyword.mobileanalytics_short}} 클라이언트 SDK를 [네트워크 요청을 작성](/docs/mobile/sdk_network_request.html)하도록 구성할 수 있습니다. 이미 `BMSClient` 및 `BMSAnalytics`를 초기화했고 클라이언트 SDK를 가져왔는지 확인하십시오.

<!--
#### Android
{: #android-network-requests notoc}

**참고:** 이 코드 스니펫은 [클라이언트 SDK 가져오기](#android-import)를 완료한 것으로 가정합니다.

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

<!-- bmsurlsession 주석 처리
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


## 충돌 분석 보고
{: #report-crash-analytics}

분석 및 로그 정보를 {{site.data.keyword.mobileanalytics_short}}에 전송하여 [애플리케이션 충돌 데이터](app-monitoring.html#monitor-app-crash)를 확인할 수 있습니다.

`Analytics.send()` 메소드는 **충돌** 페이지의 **충돌 개요** 및 **충돌** 테이블을 채웁니다. 초기화를 사용하고 분석을 수행할 프로세스를 전송하여 이 섹션의 차트를 사용할 수 있습니다. 특수 구성은 필요하지 않습니다.

`Logger.send()` 메소드는 **문제점 해결** 페이지의 **충돌 요약** 및 **충돌 세부사항** 테이블을 채웁니다. 애플리케이션 코드에 추가 명령문을 추가하여 애플리케이션이 이 섹션의 차트를 채울 로그를 저장하고 전송하도록 해야 합니다.


- Android

	`Logger.storeLogs(true);`
	<!-- * `Logger.setLogLevel(Logger.LEVEL.FATAL); // or greater` -->
	
	Android [샘플 로거 사용](sdk.html##sample-logger-usage)을 참조하십시오.


- iOS

	`Logger.isLogStorageEnabled = true`
	<!-- * `Logger.logLevelFilter = LogLevel.Fatal // or greater` -->
	
	iOS [샘플 로거 사용](sdk.html##sample-logger-usage)을 참조하십시오.


- Cordova

	 `BMSLogger.storeLogs(true);`
	<!-- * `Logger.logLevelFilter = LogLevel.Fatal // or greater` -->

	Cordova [샘플 로거 사용](sdk.html##sample-logger-usage)을 참조하십시오.

- 웹

	`BMSAnalytics.Logger.storeLogs(true);`

## 활성 사용자 추적
{: #trackingusers}

애플리케이션에서 디바이스의 고유 사용자를 인식할 수 있는 경우 활성 사용자의 사용자 이름을 {{site.data.keyword.mobileanalytics_short}}에 전달하여 애플리케이션을 활발하게 사용 중인 사용자의 수를 선택적으로 추적할 수 있습니다.

`hasUserContext=true`로 {{site.data.keyword.mobileanalytics_short}}를 초기화하여 사용자 추적을 사용으로 설정하십시오. 그렇지 않으면 {{site.data.keyword.mobileanalytics_short}}에서 디바이스당 한 명의 사용자만 캡처합니다. 


- Android

	다음 코드를 추가하여 사용자가 로그인하는 경우를 추적하십시오.
	
	```
	Analytics.setUserIdentity("username");
	```
	{: codeblock}
	
	<!--사용자가 로그아웃하는 경우에 대해 다음 코드를 추가하십시오.
	
	```
	Analytics.clearUserIdentity();
	```
	{: codeblock}
	-->

- iOS(Swift)

	다음 코드를 추가하여 사용자가 로그인하는 경우를 추적하십시오.
	
	```
	Analytics.userIdentity = "username"
	```
	{: codeblock}
	
	<!--
	사용자가 로그아웃하는 경우에 대해 다음 코드를 추가하십시오.
	
	```
	Analytics.userIdentity = nil
	```
	{: codeblock}
	-->


- Cordova
	
	다음 코드를 추가하여 사용자가 로그인하는 경우를 추적하십시오.
	
	```
	BMSAnalytics.setUserIdentity("username");
	```
	{: codeblock}

- 웹

	다음 코드를 추가하여 사용자가 로그인하는 경우를 추적하십시오.
	
	```
	BMSAnalytics.setUserIdentity("username");
	```
	{: codeblock}

## 인앱(In-App) 피드백 분석
{: #In-App}

인앱(In-App) 피드백 분석을 통해 **사용자 및 테스터**는 앱 소유자에게 풍부한 상황별 피드백을 제공할 수 있습니다. **앱 소유자**는 앱 사용을 기반으로 사용자로부터 실시간 피드백을 받습니다. **개발자**는 실시간 인사이트에 따라 변경사항을 구현합니다.

아래 API를 호출하여 모바일 앱을 피드백 모드가 되도록 인스트루먼트하십시오.

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
	
<!--## {{site.data.keyword.mobileanalytics_short}} 서비스를 사용하도록 MobileFirst Platform Foundation Server 구성(선택사항)
{: #configmfp notoc}
  MobileFirst Platform Foundation Server V7 이상을 사용 중인 경우 분석 및 로그된 데이터를 저장하는 데 {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.mobileanalytics_short}} 서비스를 사용하도록 구성할 수 있습니다.

  분석 데이터를 {{site.data.keyword.Bluemix_notm}}의 {{site.data.keyword.mobileanalytics_short}} 서비스에 전송하도록 MobileFirst Platform V7.0, V7.1 및 V8.0 베타 서버를 구성하십시오.

  1. 분석 데이터를 전송하려는 {{site.data.keyword.mobileanalytics_short}} 서비스에 대한 대시보드를 방문하고 대시보드에 대한 브라우저 URL을 기록해 두십시오.
  2. 다음과 같이 분석 보고에 대한 값을 결정하십시오.
  	1. 대시보드 URL에서 {{site.data.keyword.mobileanalytics_short}} 서비스 라우트를 가져오십시오. {{site.data.keyword.mobileanalytics_short}} 서비스 라우트는 ``/analytics/console/dashboard`` 앞의 URL의 일부입니다.

  		예를 들어, 대시보드 URL이 `http://mobile-analytics-dashboard.ng.bluemix.net/analytics/console/dashboard?instanceId=12345abcde`인 경우
      {: screen}

  		Analytics 서비스 라우트는
      `http://mobile-analytics-dashboard.ng.bluemix.net`입니다.
      {: screen}

  	2. Analytics 대시보드에서 [클라이언트 API 키](#analytics-clientkey) 값을 가져오십시오.

  	{{site.data.keyword.mobileanalytics_short}} 서비스 라우트 및 API 키를 사용하여 MobileFirst Platform 서버 버전에 따라 분석 데이터를 보고할 URL을 구성합니다. -->

<!--  3. {{site.data.keyword.mobileanalytics_short}} 서비스 대시보드에 대한 URL을 복사하십시오. `instanceId` 조회 매개변수를 포함시키십시오. 예를 들어,
      `http://mobile-analytics-dashboard.ng.bluemix.net/analytics/console/dashboard?instanceId=1212345abcde`
      {: screen}

  4. 다음과 같이 MobileFirst Platform 서버 JNDI 특성의 값을 구성하십시오.-->

<!--    ### MobileFirst Platform V7.0
    {: #mfp70 notoc}

        `wl.analytics.url` JNDI 특성의 형식은 `<Analytics Service Route>/analytics-service/rest/data?tenant=<Client API Key>`입니다.
        {: screen}

        `wl.analytics.console.url` JNDI 특성은 Analytics 서비스 대시보드 URL입니다.

        #### MobileFirst Platform V7.0 JNDI 특성 값 예제
        {: #example-mfp70-jndi-values notoc}

        2단계 및 3단계의 예제를 기반으로 `Myproj7000`이라는 이름의 MobileFirst Platform 프로젝트의 경우 `server.xml` 파일의 현재 JNDI 특성 값을 다음으로 대체하십시오.
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

      `wl.analytics.url` JNDI 특성의 형식은 `<Analytics Service Route>/analytics-service/rest/v2/<Client API Key>`입니다.
      {: screen}

      #### MobileFirst Platform JNDI V7.1 특성 값 예제
      {: #example-mfp71-jndi-values notoc}

      `MyProj7101`이라는 이름의 MobileFirst Platform 프로젝트의 경우 `server.xml` 파일의 현재 JNDI 특성 값을 다음으로 대체하십시오.
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

      `mfp.analytics.url` JNDI 특성의 형식은 다음과 같습니다.
      `<Analytics Service Route>/analytics-service/rest/v2/<Client API Key>`  

    #### MobileFirst Platform V8.0 베타 JNDI 특성 값 예제
      {: example-mfp80b-jndi-values}

      기본값인 `mfp`라는 이름의 MobileFirst Platform 프로젝트의 경우 `server.xml` 파일의 현재 JNDI 특성 값을 다음으로 대체하십시오.
      ```
      <jndiEntry jndiName="mfp/mfp.analytics.url" value='"http://mobile-analytics-dashboard.ng.bluemix.net/analytics-service/rest/data?tenant=12345abcde"'/>
      ```
      {: screen}
      ```
      <jndiEntry jndiName="mfp/mfp.analytics.console.url" value='"http://mobile-analytics-dashboard.ng.bluemix.net/analytics/console/dashboard?instanceId=12345abcde"'/>
      ```
      {: screen}
-->
<!-- #### 무시된 이벤트 및 이벤트 보존
{: #ignored-events notoc}
{{site.data.keyword.mobileanalytics_short}} 서비스는 무시된 이벤트 및 이벤트 보존을 위해 다음 데이터를 저장합니다.

<dl>	
<dt>무시된 이벤트</dt>
	<dd>`ANALYTICS_SDK_CFG_IGNORE_AppPushAction: true`
		  `ANALYTICS_SDK_CFG_IGNORE_ServerLog: true`
		  `ANALYTICS_SDK_CFG_IGNORE_NetworkTransaction: true`
		  `ANALYTICS_SDK_CFG_IGNORE_NetworkTransactionSummarizedHourly: true`
		  `ANALYTICS_SDK_CFG_IGNORE_PushNotification: true`
		  `ANALYTICS_SDK_CFG_IGNORE_PushSubscription: true`</dd>
</dt>
<dt>이벤트 보존</dd>
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


## 다음으로 수행할 작업
{: #what-to-do-next notoc}

이제 {{site.data.keyword.mobileanalytics_short}} 콘솔로 이동하여 애플리케이션을 사용하는 새 디바이스 및 전체 디바이스 등의 사용 분석을 볼 수 있습니다. 또한 <!--[사용자 정의 차트 작성](app-monitoring.html#custom-charts),-->[경보 설정](app-monitoring.html#alerts) 및 [앱 충돌 모니터링](app-monitoring.html#monitor-app-crash)을 통해 애플리케이션을 모니터할 수 있습니다.


# 관련 링크
{: #rellinks notoc}

## API 참조
{: #api notoc}

* [REST API ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://mobile-analytics-dashboard.{DomainName}/analytics-service/){:new_window}
