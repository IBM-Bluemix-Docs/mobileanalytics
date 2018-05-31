---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-06"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 인앱(In-App) 피드백 분석
{: #In-App}

## Mobile Analytics를 사용하여 인앱(In-App) 피드백 분석

{{site.data.keyword.mobileanalytics_short}}의 이 기능을 사용하여 다음을 수행할 수 있습니다.

- **사용자 및 테스터**는 애플리케이션을 실행하고 사용할 때 피드백 및 버그 보고서 '인앱(In-App)'을 기록하고 전송할 수 있습니다.
- **앱 소유자**는 이러한 상황별 풍부한 사용자 피드백을 통해 더 정확한 애플리케이션 사용자의 경험을 얻을 수 있습니다.
- 한편 **개발자**는 버그/기능 부족을 진단하고 수정하기 위한 정확한 애플리케이션 컨텍스트를 수신합니다.


## 인앱(In-App) 피드백

인앱(In-App) 사용자 피드백을 캡처하도록 모바일 애플리케이션을 사용으로 설정하려면 다음 단계를 완료하십시오.

**앱 인스트루먼트:**

 - 모바일 앱을 피드백 모드가 되도록 인스트루먼트하십시오. API `Analytics.triggerFeedbackMode();`를 호출하여 피드백 모드를 호출하십시오. 자세한 정보는 [문서를 참조](/docs/services/mobileanalytics/sdk.html)하십시오.
 - 단추, 메뉴 조치 또는 제스처와 같은 모든 애플리케이션 이벤트에서 API를 호출할 수 있습니다. 
 
**인앱(In-App) 피드백 받기**

 - 앱의 일반 사용자 및 테스터는 이전 페이지에서 이에 대해 인스트루먼트된 애플리케이션 조치를 트리거하여 피드백 모드로 전환할 수 있습니다.
 - 피드백 모드 내에서 스크린샷이 포함된 풍부한 상황별 피드백을 수집할 수 있으며 {{site.data.keyword.mobileanalytics_short}} 서비스로 전송할 수 있습니다.

![캡처 및 전송](images/in_app_capture.png)

**인앱(In-App) 피드백 분석 및 관련 조치**

 - {{site.data.keyword.mobileanalytics_short}} 서비스는 모바일 애플리케이션에서 전송된 풍부한 상황별 피드백을 수신하고 통합합니다. 
 - 피드백을 보려면 Mobile Analytics 서비스 콘솔에 로그온하여 {{site.data.keyword.mobileanalytics_short}} 서비스의 왼쪽 탐색 분할창에서 **사용자 피드백** 옵션을 선택하십시오. 

![피드백](images/in_app_user_feedback.png)
 
 - 앱 소유자는 피드백을 검토하고, 주석을 추가한 후 피드백에 **검토 상태**라는 태그를 지정할 수 있습니다. 일반적으로 주석은 피드백에 대해 작업하기 위해 작성된 Git 이슈에 대한 링크와 같은 조치 계획이거나 피드백에 대해 조치가 필요하지 않은 경우 그 이유에 대한 설명일 수 있습니다.    
 - 검토 상태는 다양한 상태 중 하나로 피드백을 분류하여 효율적으로 관리하는 데 사용할 수 있습니다.

![피드백 검토](images/in_app_review_feedback.png) 

**참고:**

 - 기능은 `고급 플랜`을 선택한 사용자에 대해서만 사용으로 설정됩니다. [업그레이드](https://console-tok02-red.cdn.s-bluemix.net/docs/account/change-plan.html#changing)하려면 {{site.data.keyword.mobileanalytics_short}} 서비스 콘솔에서 **플랜**을 선택하십시오.

 - 현재 이 기능은 Android에서만 지원됩니다.








