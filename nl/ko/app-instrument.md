---

copyright:
 years: 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 앱 인스트루먼트
{: #Instrument}
마지막 업데이트 날짜: 2018년 1월 18일
{: .last-updated}

##{{site.data.keyword.mobileanalytics_short}} 클라이언트 SDK 초기화 

애플리케이션 코드 내에서 {{site.data.keyword.mobileanalytics_short}} 클라이언트 SDK를 초기화하여 사용 분석과 애플리케이션 세션을 기록하십시오([API 키](/docs/services/mobileanalytics/sdk.html#analytics-clientkey) 값 사용).	
	
- **Android**
	
```
		BMSClient.getInstance().initialize(getApplicationContext(), BMSClient.REGION_US_SOUTH); // You can change the region
		Analytics.init(getApplication(), "your_app_name_here", "your_api_key_here", hasUserContext, collectLocation, Analytics.DeviceEvent.ALL);
```
		{: codeblock}
	    
**bluemixRegion** 매개변수는 사용 중인 {{site.data.keyword.Bluemix_notm}} 배치(예: `BMSClient.REGION_US_SOUTH`, `BMSClient.REGION_UK`)를 지정합니다. 
	    
	    
`hasUserContext`의 값을 **true** 또는 **false**로 설정하십시오. false(기본값)인 경우 각 디바이스는 활성 사용자로 계수됩니다.
		
`collectLocation`의 값을 **true** 또는 **false**로 설정하십시오. true인 경우에는 디바이스 위치 데이터가 Appsession 로그의 일부로 전송됩니다. 

- **iOS**
	  
애플리케이션 코드 내에서 클라이언트 SDK를 초기화하여 사용 분석과 애플리케이션 세션을 기록하십시오([API 키](/docs/services/mobileanalytics/sdk.html#analytics-clientkey) 값 사용).
		
```Swift
		BMSClient.sharedInstance.initialize(bluemixRegion: BMSClient.Region.usSouth) // You can change the region
		Analytics.initialize(appName: "your_app_name_here", apiKey: "your_api_key_here", hasUserContext: false, collectLocation: true, deviceEvents: deviceEvents: .lifecycle, .network)
```
		{: codeblock}
				
**bluemixRegion** 매개변수는 사용 중인 IBM Cloud 배치(예: `BMSClient.Region.usSouth` 또는 `BMSClient.Region.unitedKingdom`)를 지정합니다.
		
	 
`hasUserContext`의 값을 **true** 또는 **false**로 설정하십시오. false(기본값)인 경우 각 디바이스는 활성 사용자로 계수됩니다.
		
`collectLocation`의 값을 **true** 또는 **false**로 설정하십시오. true인 경우에는 디바이스 위치 데이터가 Appsession 로그의 일부로 전송됩니다. 
	
- **Cordova**
		
애플리케이션 코드 내에서 클라이언트 SDK를 초기화하여 사용 분석과 애플리케이션 세션을 기록하십시오([API 키](/docs/services/mobileanalytics/sdk.html#analytics-clientkey) 값 사용).
		
```
		var appName = "your_app_name_here";
		var apiKey = "your_api_key_here";
		BMSClient.initialize(BMSClient.REGION_US_SOUTH); // You can change the region
		BMSAnalytics.initialize(appName, apiKey, hasUserContext, collectLocation, [BMSAnalytics.ALL])
```
		{: codeblock}
		
**bluemixRegion** 매개변수는 사용 중인 IBM Cloud 배치(예: `BMSClient.REGION_US_SOUTH` 또는 `BMSClient.REGION_UK`)를 지정합니다.
		
`hasUserContext`의 값을 **true** 또는 **false**로 설정하십시오. false(기본값)인 경우 각 디바이스는 활성 사용자로 계수됩니다.
		
`collectLocation`의 값을 **true** 또는 **false**로 설정하십시오. true인 경우에는 디바이스 위치 데이터가 Appsession 로그의 일부로 전송됩니다.
    
- **웹**
		
애플리케이션 코드 내에서 클라이언트 SDK를 초기화하여 사용 분석과 애플리케이션 세션을 기록하십시오([API 키](/docs/services/mobileanalytics/sdk.html#analytics-clientkey) 값 사용).
		
```
		var appName = "your_app_name_here";
		var apiKey = "your_api_key_here";
		BMSAnalytics.Client.initialize(BMSAnalytics.Client.REGION_US_SOUTH);
		BMSAnalytics.initialize(appName,apiKey,hasUserContext,BMSAnalytics.DeviceEvents.ALL,instanceId);
``` 
		{: codeblock}

`bluemixRegion` 매개변수는 사용 중인 {{site.data.keyword.Bluemix_notm}} 배치를 지정합니다. `hasUserContext`의 값을 `true` 또는 `false`로 설정하십시오. false(기본값)인 경우 각 디바이스는 활성 사용자로 계산됩니다. `instanceId`를 사용자 서비스 instanceId로 설정하십시오. 문자열 "...mobile-analytics_Prod/" 이후에서 "/"까지 서비스 인스턴스에 대한 브라우저 URL에서 가져오는 영숫자 문자열입니다. 

**참고**: 애플리케이션에 대해 선택하는 이름(`your_app_name_here`)이 {{site.data.keyword.mobileanalytics_short}} 콘솔에 애플리케이션 이름으로 표시됩니다. 애플리케이션 이름은 대시보드에서 애플리케이션 로그를 검색하는 필터로 사용됩니다. 플랫폼(예: Android 및 iOS)에 걸쳐 동일한 애플리케이션 이름을 사용하는 경우, 로그가 전송된 플랫폼에 상관없이 동일한 이름 아래에서 애플리케이션의 모든 로그를 볼 수 있습니다.

##{{site.data.keyword.mobileanalytics_short}} 서비스로 앱 데이터 전송

기록된 사용 분석을 {{site.data.keyword.mobileanalytics_short}} 서비스로 전송하십시오. 분석을 테스트하는 간단한 방법은 애플리케이션이 시작될 때 다음 코드를 실행하는 것입니다.


- **Android**
	
`Analytics.send()` 메소드를 사용하여 분석 데이터를 서버에 전송하십시오. `Analytics.send()` 메소드를 Android 애플리케이션에서 기본 활동의 `onCreate` 메소드 또는 프로젝트에 가장 적합한 위치에 배치할 수 있습니다. 
	
`Analytics.send()`를 위치에 상관 없이 삽입할 수 있습니다.
	
- **iOS**
	
`Analytics.send` 메소드를 사용하여 분석 데이터를 서버에 전송하십시오. `Analytics.send` 메소드를 애플리케이션 위임의 `application(_:didFinishLaunchingWithOptions:)` 메소드 또는 프로젝트에 가장 적합한 위치에 배치할 수 있습니다. 
	
- **Cordova**
		
`BMSAnalytics.send` 메소드를 사용하여 분석 데이터를 서버에 전송하십시오. `BMSAnalytics.send` 메소드를 프로젝트에 가장 적합한 위치에 배치하십시오.
		
- **웹**
		
`BMSAnalytics.send` 메소드를 사용하여 분석 데이터를 서버에 전송하십시오. `BMSAnalytics.send` 메소드를 프로젝트에 가장 적합한 위치에 배치하십시오. 
		



[애플리케이션 인스트루먼트](/docs/services/mobileanalytics/sdk.html) 주제를 조사하여 추가적인 {{site.data.keyword.mobileanalytics_short}} 기능(예: [로깅](/docs/services/mobileanalytics/sdk.html#app-monitoring-logger), [네트워크 요청](/docs/services/mobileanalytics/sdk.html#network-requests), [위치 로깅](/docs/services/mobileanalytics/sdk.html#location-logging) 및 [충돌 분석](/docs/services/mobileanalytics/sdk.html#report-crash-analytics))에 대해 알아보십시오.


다음 단계는 **에뮬레이터 또는 디바이스에서 애플리케이션을 컴파일 및 실행**하는 것입니다.
