---

copyright:
 years: 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 전제조건
{: #prerequisites}
마지막 업데이트 날짜: 2018년 1월 18일
{: .last-updated}


## Mobile Analytics 서비스 인스턴스 작성
{: #prerequisites_1}

1. [IBM Cloud 카탈로그](https://console.ng.bluemix.net/catalog/)에서 **모바일** > **Mobile Analytics**를 클릭하십시오.
2. 서비스 이름을 제공하십시오.
3. **작성**을 클릭하십시오.
4. 기존의 다른 앱에 연결하거나 바인딩되지 않은 상태를 유지하도록 선택하십시오.


바인딩된 서비스 또는 바인딩되지 않은 서비스를 작성할지 선택할 수 있습니다. 바인딩된 서비스는 다른 IBM Cloud 앱에 연결되는 반면, 바인딩되지 않은 서비스는 독립형이며 다른 앱에 연결되지 않습니다.  

## 앱 초기화
{: #prerequisites_app}

{{site.data.keyword.mobileanalytics_short}} [클라이언트 SDK](/docs/services/mobileanalytics/install-client-sdk.html)를 [가져오기](/docs/services/mobileanalytics/available-client-sdk.html)하여 설치하십시오. 선택적으로 {{site.data.keyword.mobileanalytics_short}} [REST API ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://mobile-analytics-dashboard.{DomainName}/analytics-service/){:new_window}를 사용할 수 있습니다.


###클라이언트 SDK 가져오기

클라이언트 SDK를 가져와서 다음 코드 스니펫을 사용하여 초기화하여 사용 분석을 기록하십시오.

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
		
		
다음 단계는 [앱 인스트루먼트](app-instrument.html)입니다.


