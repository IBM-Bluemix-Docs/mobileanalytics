---

copyright:
  years: 2016, 2017
lastupdated: "2017-07-14"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 시작하기 튜토리얼

{: #gettingstartedtemplate}

{{site.data.keyword.mobileanalytics_full}}는 개발자, IT 관리자, 비즈니스 이해 당사자에게 모바일 앱의 성능 및 사용 실태에 대한 인사이트를 제공합니다. {{site.data.keyword.mobileanalytics_short}}를 사용하면 다음을 수행할 수 있습니다.

* 데스크 탑이나 태블릿에서 사용자의 모든 애플리케이션의 성능과 사용량을 모니터합니다. 
* 상태동향과 이상 항목을 빠르게 식별하고 문제를 해결하기 위해 세부적으로 분석하며 핵심 메트릭이 중요 임계값을 초과할 때 경보를 트리거합니다. 
{: shortdesc}

{{site.data.keyword.mobileanalytics_short}} 서비스를 빨리 시작하고 실행하려면 다음 단계를 수행하십시오.

1. {{site.data.keyword.mobileanalytics_short}} 서비스의 <!--[create an instance](https://console.{DomainName}/docs/services/reqnsi.html#req_instance)--> 인스턴스를 작성한 후에는 {{site.data.keyword.Bluemix}} 대시보드의 **서비스** 섹션에서 타일을 클릭하여 {{site.data.keyword.mobileanalytics_short}} 콘솔에 액세스할 수 있습니다. **데모 모드** 옵션은 보기 및 차트에서 *데모 데이터*를 표시하는 {{site.data.keyword.mobileanalytics_short}} 콘솔에서 사용할 수 있습니다.
데모 모드는 서비스가 인스턴스화된 후 처음 실행되는 경우 콘솔의 기본 모드입니다. 고유 애플리케이션 및 분석 데이터를 서비스에 채운 후 데모 모드를 토글 *해제*하여 애플리케이션의 데이터를 여러 차트에서 볼 수 있습니다. {{site.data.keyword.mobileanalytics_short}} 콘솔은 데모 모드에서 읽기 전용이므로 새 경보 정의를 작성할 수 없습니다.

2. {{site.data.keyword.mobileanalytics_short}} [클라이언트 SDK](/docs/services/mobileanalytics/install-client-sdk.html)를 설치하십시오. 선택적으로 {{site.data.keyword.mobileanalytics_short}} [REST API ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://mobile-analytics-dashboard.{DomainName}/analytics-service/){:new_window}를 사용할 수 있습니다.
	
	- 웹 앱 서비스 구성
	
		웹 SDK의 경우 앱 서버를 허용하도록 서비스 인스턴스를 구성하려면, Swagger UI를 통한 서비스 구성 REST API를 통해 앱 서버의 URL을 제공해야 합니다. 허용되는 URL 목록인 서비스 구성의 CRUD 오퍼레이션을 위해 POST, GET, PUT 및 DELETE 메소드가 제공됩니다. 서비스 인스턴스의 구성을 GET 및 DELETE하려면, 사용자 API 키를 사용하십시오. 서비스 구성을 작성하고 업데이트하려면, 본문 {"allowedUrls":["http://abc.com","https://www.xyz.com"]} 처럼 나열된 허용되는 URL과 함께 POST 및 PUT 메소드를 사용하십시오. 웹 서버와 동일한 시스템에 있는 브라우저에서 액세스하는 경우 허용되는 URL로 "http://localhost" 를 제공하십시오. 

3. 클라이언트 SDK를 가져와서 다음 코드 스니펫을 사용하여 초기화하여 사용 분석을 기록하십시오.

	- Android
	
		다음 `import` 문을 프로젝트 파일의 시작 부분에 추가하십시오.
		
		```
		import com.ibm.mobilefirstplatform.clientsdk.android.core.api.*;
		import com.ibm.mobilefirstplatform.clientsdk.android.analytics.api.*;
		import com.ibm.mobilefirstplatform.clientsdk.android.logger.api.*;
		```
		{: codeblock}

	- iOS

		Swift SDK는 iOS 및 watchOS에 대해 사용 가능합니다.
		
		다음 `import` 문을 `AppDelegate.swift` 프로젝트 파일의 시작 부분에 추가하여 `BMSCore` 프레임워크와 `BMSAnalytics` 프레임워크를 가져오십시오.
	
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
	
		다음 스크립트를 웹 앱의 `index.html` 파일에 추가하여 웹 플러그인을 추가하십시오.
	
		```Html
		<script src="bms-clientsdk-web-analytics/bmsanalytics.js"></script>
		```
		{: codeblock}

		또는 모듈 로더 requirejs를 사용하여 추가하십시오. 참조 API로 사용된 이름은 사용된 인수 이름(`BMSAnalytics`)과 동일합니다. 
	
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
		
4. 애플리케이션 코드의 {{site.data.keyword.mobileanalytics_short}} 클라이언트 SDK를 초기화하여 사용 분석 및 애플리케이션 세션을 기록하십시오([API 키](/docs/services/mobileanalytics/sdk.html#analytics-clientkey) 값 사용).
	
	- Android
	
		```
		BMSClient.getInstance().initialize(getApplicationContext(), BMSClient.REGION_US_SOUTH); // You can change the region
		Analytics.init(getApplication(), "your_app_name_here", "your_api_key_here", hasUserContext, collectLocation, Analytics.DeviceEvent.ALL);
		```
		{: codeblock}
	    
		**bluemixRegion** 매개변수는 사용자가 사용 중인 {{site.data.keyword.Bluemix_notm}} 배치를 지정합니다(예: `BMSClient.REGION_US_SOUTH` 및 `BMSClient.REGION_UK`).
	    <!-- , or `BMSClient.Region.Sydney`.-->
	    
		`hasUserContext`에 대한 값을 **true** 또는 **false**로 설정하십시오. false(기본값)인 경우 각 디바이스는 활성 사용자로 계수됩니다.
		
		`collectLocation`에 대한 값을 **true** 또는 **false**로 설정하십시오. true인 경우에는 디바이스 위치 데이터가 Appsession 로그의 일부로 전송됩니다.

- iOS
	  
		애플리케이션 코드 내의 클라이언트 SDK를 초기화하여 사용 분석 및 애플리케이션 세션을 기록하십시오([API 키](/docs/services/mobileanalytics/sdk.html#analytics-clientkey) 값 사용).
		
		```Swift
		BMSClient.sharedInstance.initialize(bluemixRegion: BMSClient.Region.usSouth) // You can change the region
		Analytics.initialize(appName: "your_app_name_here", apiKey: "your_api_key_here", hasUserContext: false, collectLocation: true, deviceEvents: deviceEvents: .lifecycle, .network)
		```
		{: codeblock}
				
		**bluemixRegion** 매개변수는 사용 중인 IBM Cloud 배치를 지정합니다(예: `BMSClient.Region.usSouth` 또는 `BMSClient.Region.unitedKingdom`).
		<!-- , or `BMSClient.REGION_SYDNEY`. -->
	 
		`hasUserContext`에 대한 값을 **true** 또는 **false**로 설정하십시오. false(기본값)인 경우 각 디바이스는 활성 사용자로 계수됩니다.
		
		`collectLocation`에 대한 값을 **true** 또는 **false**로 설정하십시오. true인 경우에는 디바이스 위치 데이터가 Appsession 로그의 일부로 전송됩니다.

 - Cordova
		
		애플리케이션 코드 내의 클라이언트 SDK를 초기화하여 사용 분석 및 애플리케이션 세션을 기록하십시오([API 키](/docs/services/mobileanalytics/sdk.html#analytics-clientkey) 값 사용).
		
		```
		var appName = "your_app_name_here";
		var apiKey = "your_api_key_here";
		BMSClient.initialize(BMSClient.REGION_US_SOUTH); // You can change the region
		BMSAnalytics.initialize(appName, apiKey, hasUserContext, collectLocation, [BMSAnalytics.ALL])
		```
		{: codeblock}
		
		**bluemixRegion** 매개변수는 사용 중인 IBM Cloud 배치를 지정합니다(예: `BMSClient.REGION_US_SOUTH` 또는 `BMSClient.REGION_UK`).
		<!-- , or `BMSClient.REGION_SYDNEY`. -->
		`hasUserContext`에 대한 값을 **true** 또는 **false**로 설정하십시오. false(기본값)인 경우 각 디바이스는 활성 사용자로 계수됩니다.
		
		`collectLocation`에 대한 값을 **true** 또는 **false**로 설정하십시오. true인 경우에는 디바이스 위치 데이터가 Appsession 로그의 일부로 전송됩니다.

 - 웹
		
		애플리케이션 코드 내의 클라이언트 SDK를 초기화하여 사용 분석 및 애플리케이션 세션을 기록하십시오([API 키](/docs/services/mobileanalytics/sdk.html#analytics-clientkey) 값 사용).
		
		```
		var appName = "your_app_name_here";
		var apiKey = "your_api_key_here";
		BMSAnalytics.Client.initialize(BMSAnalytics.Client.REGION_US_SOUTH);
		BMSAnalytics.initialize(appName,apiKey,hasUserContext,BMSAnalytics.DeviceEvents.ALL,instanceId);
		``` 
		{: codeblock}

		`bluemixRegion` 매개변수는 사용 중인 {{site.data.keyword.Bluemix_notm}} 배치를 지정합니다(예: `BMSAnalytics.Client.REGION_US_SOUTH` 및 `BMSAnalytics.Client.REGION_UK`). `hasUserContext`의 값을 `true` 또는 `false`로 설정하십시오. false(기본값)인 경우 각 디바이스는 활성 사용자로 계산됩니다. `instanceId`를 서비스 instanceId로 설정하십시오. 해당 영숫자 문자열은 문자열 "...mobile-analytics_Prod/" 이후에서 "/"까지 서비스 인스턴스에 대한 브라우저 URL에서 가져옵니다.

		애플리케이션(`your_app_name_here`)에 사용하도록 선택한 이름이 {{site.data.keyword.mobileanalytics_short}} 콘솔에 애플리케이션 이름으로 표시된다는 점을 참고하십시오. 애플리케이션 이름은 대시보드에서 애플리케이션 로그를 검색하는 필터로 사용됩니다. 플랫폼(예: Android 및 iOS)에 걸쳐 동일한 애플리케이션 이름을 사용하는 경우, 로그가 전송된 플랫폼에 상관없이 동일한 이름 아래에서 애플리케이션의 모든 로그를 볼 수 있습니다.

5. 기록된 사용 분석을 {{site.data.keyword.mobileanalytics_short}} 서비스로 전송하십시오. 분석을 테스트할 간단한 방법은 애플리케이션을 시작할 때 다음 코드를 실행하는 것입니다.

	- Android
	
		분석 데이터를 서버에 전송하려면 `Analytics.send()` 메소드를 사용하십시오. `Analytics.send()` 메소드를 Android 애플리케이션에서 기본 활동의 `onCreate` 메소드에 또는 프로젝트에 적합한 위치에 배치할 수 있습니다.
	
		`Analytics.send()`를 위치에 상관없이 삽입할 수 있습니다.
	
	- iOS
	
		`Analytics.send` 메소드를 사용하여 분석 데이터를 서버에 전송하십시오. `Analytics.send` 메소드를 애플리케이션 위임의 `application(_:didFinishLaunchingWithOptions:)` 메소드에 또는 프로젝트에 가장 적합한 위치에 배치할 수 있습니다.
	
	- Cordova
		
		`BMSAnalytics.send` 메소드를 사용하여 분석 데이터를 서버로 전송하십시오. `BMSAnalytics.send` 메소드를 프로젝트에 가장 적합한 위치에 배치하십시오.
		
	- 웹
		
		`BMSAnalytics.send` 메소드를 사용하여 분석 데이터를 서버로 전송하십시오. `BMSAnalytics.send` 메소드를 프로젝트에 가장 적합한 위치에 배치하십시오.
		
	6. [애플리케이션 인스트루먼트](/docs/services/mobileanalytics/sdk.html) 주제를 조사하여 추가적인 {{site.data.keyword.mobileanalytics_short}} 기능(예: [로깅](/docs/services/mobileanalytics/sdk.html#app-monitoring-logger), [네트워크 요청](/docs/services/mobileanalytics/sdk.html#network-requests), [위치 로깅](/docs/services/mobileanalytics/sdk.html#location-logging) 및 [충돌 분석](/docs/services/mobileanalytics/sdk.html#report-crash-analytics))에 대해 자세히 알아보십시오.
	
7. 에뮬레이터 또는 디바이스에서 애플리케이션을 컴파하고 실행하십시오.

8. {{site.data.keyword.mobileanalytics_short}} 콘솔로 이동하여 애플리케이션에 대한 사용 분석을 확인하십시오. 또한 <!--[사용자 정의 차트 작성](app-monitoring.html#custom-charts),-->[경보 설정](/docs/services/mobileanalytics/app-monitoring.html#alerts) 및 [앱 충돌 모니터링](/docs/services/mobileanalytics/app-monitoring.html#monitor-app-crash)을 통해 애플리케이션을 모니터할 수 있습니다.

# 관련 링크
{: #rellinks notoc}

## SDK
{: #sdk notoc}
* [Android SDK ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-analytics){: new_window}
* [iOS SDK ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-analytics){: new_window}
* [Cordova 플러그인 코어 SDK ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.npmjs.com/package/bms-core){: new_window}
* [웹 SDK ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-web-analytics/){: new_window}
## API 참조
{: #api notoc}
* [REST API ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://mobile-analytics-dashboard.{DomainName}/analytics-service/){:new_window}
