---

copyright:
 years: 2018

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Mobile Analytics용 SDK
{: #install-sdk}
마지막 업데이트 날짜: 2018년 1월 18일
{: .last-updated}

{{site.data.keyword.mobileanalytics_short}} 클라이언트 SDK는 현재 Android, iOS, Cordova 및 웹에 대해 사용 가능합니다. 다음은 플랫폼 특정 SDK에 대한 링크입니다. 

설치 및 기술적 개념에 대한 세부사항은 [문서](install-client-sdk.html)를 참조하십시오.

{: shortdesc}

## Adroid용 SDK

   [Android 클라이언트 SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-analytics) 설치


## iOS용 SDK

   [iOS 클라이언트 SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-analytics) 설치

   
## Cordova용 SDK

   [Cordova 클라이언트 SDK](https://www.npmjs.com/package/bms-core) 설치
   
## 웹용 SDK

   [웹 클라이언트 SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-web-analytics/)
   
**참고**: 웹 SDK의 경우 앱 서버를 허용하도록 Mobile Analytics 서비스 인스턴스를 구성해야 합니다. Swagger UI를 통한 서비스 구성 REST API를 통해 앱 서버의 URL을 제공하십시오. 허용되는 URL 목록인 서비스 구성의 CRUD 오퍼레이션을 위해 POST, GET, PUT 및 DELETE 메소드가 제공됩니다. 서비스 인스턴스의 구성을 GET 및 DELETE하려면, 사용자 API 키를 사용하십시오. 서비스 구성을 작성하고 업데이트하려면, 본문 {"allowedUrls":["http://abc.com","https://www.xyz.com"]} 처럼 나열된 허용되는 URL을 사용하여 POST 및 PUT 메소드를 사용하십시오. 웹 서버와 동일한 시스템에 있는 브라우저에서 액세스하는 경우 허용되는 URL로 "http://localhost" 를 제공하십시오. 
