---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-06"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 메트릭 및 이벤트 사용
{: #usingmetrics}

## Mobile Analytics를 사용하여 애플리케이션 모니터링

{{site.data.keyword.mobileanalytics_full}}는 모바일 애플리케이션에 대한 모니터링 및 분석을 제공합니다. {{site.data.keyword.mobileanalytics_short}} 클라이언트 SDK를 사용하여 애플리케이션 로그와 모니터 데이터를 기록할 수 있습니다. 개발자는 이 데이터를 {{site.data.keyword.mobileanalytics_short}} 서비스에 전송할 시기를 제어할 수 있습니다. 데이터가 {{site.data.keyword.mobileanalytics_short}}에 전달될 때 {{site.data.keyword.mobileanalytics_short}} 콘솔을 사용하여 모바일 애플리케이션, 디바이스, 애플리케이션 로그에 대한 분석 인사이트를 얻을 수 있습니다.
{: shortdesc}

##사전 정의된 메트릭

**사전 정의된 메트릭**을 사용하여 다음과 같은 질문에 응답할 수 있습니다.

* 얼마나 많은 새 사용자가 있습니까?  
* 얼마나 많은 사용자가 내 애플리케이션을 적극적으로 사용하고 있습니까?  
* 사용자가 내 애플리케이션을 얼마나 자주 사용하고 있습니까? 
* 사용자가 하루 중 언제 내 애플리케이션을 사용합니까?  
* 내 사용자가 선호하는 디바이스 모델은 무엇입니까? 
* 레거시 운영 체제에 대한 지원을 중지해야 하는 시기는 언제입니까? 
* 어느 애플리케이션에 성능 문제가 있습니까?  

##사용자 정의 이벤트

자체 **사용자 정의 이벤트**를 추가함으로써 다음과 같은 질문에 응답할 수 있습니다. 

* 가장 많이 사용되는 기능과 가장 적게 사용되는 기능은 무엇입니까?  
* 사용자가 맵에 들어가고 맵을 나가는 위치는 어디입니까?  
* 사용자가 가장 많이 보는 활동은 무엇입니까?  
* 사용자가 앱에서 워크플로우를 완료합니까(예: 전환 퍼널)?   

클라이언트 측 로그 및 사용법 데이터는 자동으로 수집되며 Mobile Analytics 서비스에 On-Demand로 전송됩니다. 개발자 및 관리자는 클라이언트 SDK에 의해 수집된 데이터를 보기 위해 {{site.data.keyword.mobileanalytics_short}} 서비스 대시보드를 사용할 수 있습니다.

## 데이터 시각화
{: data-visualization notoc}

분석 서비스에 의해 수집된 모든 데이터는 IBM {{site.data.keyword.mobileanalytics_short}} 서비스 타일 인스턴스를 클릭하여 {{site.data.keyword.Bluemix_notm}} 대시보드로부터 액세스 가능한 {{site.data.keyword.mobileanalytics_short}} 대시보드를 통해 시각화될 수 있습니다. <!--You can also create custom charts, based on data that is collected by the analytics service in the dashboard.--> 모바일 분석 둘러보기 외에도 분석 기능에는 클라이언트 로그, 캡처된 클라이언트 충돌 데이터 및 {{site.data.keyword.mobileanalytics_short}} 서비스에 피드하는 클라이언트 API 기능 호출을 통해 명시적으로 제공하는 추가 데이터에 대한 원시 검색을 수행하는 기능이 포함됩니다. 

