---

copyright:
  years: 2015, 2017
lastupdated: "2018-02-19"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}


# 자주 묻는 질문(FAQ) 
{: #faq}


1. **{{site.data.keyword.mobileanalytics_full}} 개념**
	
	{{site.data.keyword.mobileanalytics_full}}는 모바일 애플리케이션의 성능과 사용 실태에 대한 실시간 통찰 및 히스토리 기반 인사이트를 제공하는 서비스입니다. {{site.data.keyword.mobileanalytics_short}}를 사용하면 애플리케이션 개발자와 애플리케이션 소유자는 활성 사용자, 세션, 모바일 플랫폼, 애플리케이션 충돌의 상태동향을 모니터하여 데이터 중심의 의사결정을 내릴 수 있습니다. 사용자는 푸시 서비스 또는 내부 메시징 서비스를 포함하여, 한 번 트리거되면 모든 REST 엔드포인트에 메시지를 전송하는 선택된 메트릭에 경보를 설정할 수 있습니다.


2. **What can I do with {{site.data.keyword.mobileanalytics_short}} for {{site.data.keyword.Bluemix_notm}}로 어떤 작업을 할 수 있습니까?**

	모바일 애플리케이션 제품 관리자는 얼마나 많은 사용자가 본인의 애플리케이션을 사용하는지(사용자 메트릭)와 그러한 사용자가 언제 애플리케이션을 사용하는지(세션 메트릭)를 확인할 수 있습니다. 이 정보는 시계열로 제공되고 실시간으로 업데이트되므로 애플리케이션에 대한 변경사항이 미치는 영향을 볼 수 있습니다. 특정 애플리케이션 버전 또는 운영 체제를 표시하도록 필터링하여 지원중단 및 우선순위에 관한 결정을 내릴 수 있습니다. 
	
	모바일 애플리케이션 마케팅 담당자는 사용자 및 세션 메트릭을 사용하여 시간 경과에 따른 변화를 관찰하고 이벤트 날짜와 연관시킴으로써 고객 참여를 모니터하고 고객 이탈을 관리하며 모바일 애플리케이션 마케팅 노력의 효율성을 평가할 수 있습니다.
	
	모바일 애플리케이션 개발자는 모바일 애플리케이션 성능 문제로 인해 사용자가 불편을 겪고 애플리케이션의 평판에 피해가 가기 전에 충돌 메트릭을 사용하여 그러한 문제를 발견하고 해결할 수 있습니다. Analytics 콘솔에서 충돌 개수 및 충돌 비율을 모두 모니터할 수 있으며 가장 많은 사용자에게 영향을 주는 충돌에 우선순위를 지정할 수 있습니다. 충돌이 주어진 임계값을 초과할 때 자동화된 조치를 취하거나 알림을 보내도록 경보를 설정할 수 있으며, 충돌 인스턴스에서 드릴 다운하여 디바이스 로그와 애플리케이션 스택 추적을 확인함으로써 문제를 해결할 수 있습니다.
	
	{{site.data.keyword.mobileanalytics_short}}를 사용하여 개인 정보를 공유하지 않아야 합니다.

3. **Mobile Analytics를 사용하려면 데이터 분석가 스킬이 필요합니까?**

	아니오, {{site.data.keyword.mobileanalytics_short}}는 비즈니스 이해 당사자와 애플리케이션 개발자를 위한 바로 사용이 가능한 Analytics 콘솔을 제공합니다. 조회 스킬도 필요하지 않습니다.

4. **분석 데이터에서 사용자 정의 조회를 실행할 수 있습니까?**

    {{site.data.keyword.mobileanalytics_short}}에서 사용자 정의 조회를 할 수 없지만 향후 이 기능을 사용할 수 있도록 검토 중입니다.
	
5. **내 애플리케이션을 {{site.data.keyword.mobileanalytics_short}}에 어떻게 연결합니까?**

    [iOS 또는 Android용 오픈 소스 SDK를 다운로드](install-client-sdk.html)하거나 기타 플랫폼용 {{site.data.keyword.mobileanalytics_short}} [REST API](https://mobile-analytics-dashboard.{DomainName}/analytics-service/)를 사용하십시오. 

6. **어느 IBM Cloud 지역에서 Mobile Analytics를 사용할 수 있습니까?**

    현재 Mobile Analytics는 미국 남부와 영국에서 사용할 수 있습니다. 다른 지역에서도 제공할 계획이지만 아직 시기가 정해지지 않았습니다.

7. **이 서비스의 요금은 얼마입니까?**

    매달 수집되는 처음 1억 개의 이벤트는 무료이므로 이벤트 가격은 백만 개당 1달러입니다.
	
8. **이벤트란 무엇입니까?**

    현재 보고되는 이벤트에는 애플리케이션 세션 시작, 애플리케이션 세션 종료(애플리케이션 충돌 포함), 경보 알림 및 로그 입력이 있습니다.
	
9. **월별 서비스 비용을 어떻게 산정할 수 있습니까?**

    클라이언트 계정별로 서비스에 전송되는 이벤트 수에 따라 가격이 책정되므로 가격 산정은 이벤트 수의 산정을 의미합니다.  
	
	청구되는 가격은 {{site.data.keyword.mobileanalytics_short}}에 연결한 모든 애플리케이션의 이벤트 합계입니다. 하나의 애플리케이션의 경우, 이벤트 수는 애플리케이션 내에서 구현한 인스트루먼테이션 등급, 사용자 수 및 사용자의 적극성 정도에 따라 달라집니다. 
	
	사용량을 산정하려면 다음 공식을 사용하십시오. 앱당 월별 이벤트 수 = (일별 사용자 수)(일별 사용자당 세션 수)(월별 일 수)(세션당 이벤트 수)

	
	세션당 이벤트 수는 개발자가 애플리케이션에 구성한 경보 정의, 로그 캡처, 사용자 정의 분석 및 네트워크 호출 대상에 따라 2개에서 수백 개까지 매우 광범위할 수 있습니다.

9. **얼마나 오랫동안 분석 데이터를 유지할 수 있습니까?**

    데이터는 30일 이상 보관됩니다.
	
10. **데이터를 {{site.data.keyword.mobileanalytics_short}} 콘솔에 표시하는 데 시간이 얼마나 걸립니까?**

    {{site.data.keyword.mobileanalytics_short}} 콘솔의 데이터는 거의 실시간이며 이는 데이터가 실제 이벤트 발생 후 몇 초 내에 표시됨을 의미합니다.
	
11. **{{site.data.keyword.mobileanalytics_full}}와 MobileFirst Platform Foundation에서 발견되는 Mobile Analytics 간의 차이점은 무엇입니까?**

    두 콘솔에서 사용자 및 세션은 매우 유사하지만 MobileFirst Platform Foundation에서 제공하는 분석은 클라이언트가 자체 분석 클러스터를 온프레미스로 관리할 수 있는 추가 메트릭 및 설정을 포함합니다. 또한 MobileFirst Platform Foundation 분석 콘솔에서는 어댑터와 어댑터 프로시저에 대한 메트릭을 세분화할 수 있는 반면, {{site.data.keyword.mobileanalytics_short}} 서비스에서는 이러한 메트릭이 네트워크 요청 차트와 테이블로 통합됩니다.
	
12. **내 앱을 개발하는 데 MobileFirst Platform Foundation 온프레미스를 사용 중이지만 내 고유 분석 클러스터를 호스팅할 의향이 없습니다. 대신 {{site.data.keyword.mobileanalytics_full}}를 사용할 수 있습니까?**

    예. 다음과 같은 몇 개의 옵션이 있습니다. MobileFirst Platform Foundation 7.x 또는 8.0을 사용하고 앱이 MobileFirst Platform SDK로 인스트루먼트된 경우에는 {{site.data.keyword.mobileanalytics_short}} for {{site.data.keyword.Bluemix_notm}}에 분석 데이터를 보고하도록 MobileFirst 서버를 구성할 수 있습니다. 세부사항은 [Mobile Analytics 및 Mobile Foundation IBM Cloud 서비스 구성 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://mobilefirstplatform.ibmcloud.com/blog/2016/07/11/analytics-bm-service/){: new_window} 블로그 게시물을 읽어보십시오. 또는, {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.mobileanalytics_short}} SDK를 사용하여 앱을 인스트루먼트하고 보고서를 {{site.data.keyword.mobileanalytics_short}} 서비스에 직접 보고할 수 있습니다.
