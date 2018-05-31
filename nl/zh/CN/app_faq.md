---

copyright:
  years: 2015, 2017
lastupdated: "2018-02-19"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}


# 常见问题 
{: #faq}


1. **什么是 {{site.data.keyword.mobileanalytics_full}}？**
	
	{{site.data.keyword.mobileanalytics_full}} 是一种服务，可以提供实时和历史信息，帮助您了解移动应用程序的执行和使用情况。使用 {{site.data.keyword.mobileanalytics_short}}，应用程序开发人员和应用程序所有者可以通过监视活动用户、会话、移动平台和应用程序崩溃的趋势，依据数据来制定决策。您还可以针对所选度量值设置警报，一旦触发警报，立即将消息发送至 REST 端点，包括推送服务或内部消息传递服务。


2. **使用 {{site.data.keyword.mobileanalytics_short}} for {{site.data.keyword.Bluemix_notm}} 可以做什么？**

	作为移动应用程序产品经理，您可以查看有多少人使用您的应用程序（用户度量值），以及具体的使用时间（会话度量值）。这些信息以时间序列的形式呈现给您并且实时更新，让您能够看到您对应用程序的更改有怎样的效果。您可以进行过滤以查看特定的应用程序版本或操作系统，以制定淘汰决策和划分优先级的决策。 
	
	作为移动应用程序市场营销人员，您可以使用用户和会话度量值，通过观察各项指标随时间变化的情况并将其与事件日期相关联，来监视参与情况、管理顾客流失率，并评估移动应用程序市场营销活动的效果。
	
	作为移动应用程序开发人员，您可以使用崩溃度量值来提早发现并解决移动应用程序性能问题，使其不至于影响用户使用或应用程序声誉。您既可以监视来自分析控制台的崩溃计数和崩溃比率，也可以优先处理受影响用户数量最多的问题。您可以设置在崩溃数超过给定阈值时是发送通知警报还是自动执行操作；也可以通过向下钻取崩溃实例以查看设备日志和应用程序堆栈跟踪来进行故障诊断。
	
	使用 {{site.data.keyword.mobileanalytics_short}} 可确保不共享任何个人信息。

3. **使用 Mobile Analytics 需要有数据分析技能吗？**

	不需要，{{site.data.keyword.mobileanalytics_short}} 为业务利益相关方和应用程序开发人员提供了即取即用的分析控制台。无需任何查询技能。

4. **我能在自己的分析数据上执行定制查询吗？**

    {{site.data.keyword.mobileanalytics_short}} 不允许定制查询，但未来考虑要实现此功能。
	
5. **如何将我的应用程序连接到 {{site.data.keyword.mobileanalytics_short}}？**

    [下载开放式源代码 SDK for iOS 或 Android](install-client-sdk.html)，也可以将 {{site.data.keyword.mobileanalytics_short}} [REST API](https://mobile-analytics-dashboard.{DomainName}/analytics-service/) 用于其他平台。 

6. **Mobile Analytics 在哪些 IBM Cloud 区域中可用？**

    当前，Mobile Analytics 在美国南部和英国可用。此产品未来计划在其他地区上市，但具体时间表尚未确定。

7. **此服务成本是多少？**

    每个月收集的前 1 亿个事件是免费的，此后，每 1 百万个事件需要支付 $1。
	
8. **什么是事件？**

    当前报告的事件包括应用程序会话开始、应用程序会话结束（包括应用程序崩溃）、警报通知和日志条目。
	
9. **我如何估算该服务每月开销为多少？**

    因为定价取决于每个客户端账户发送给服务的事件数，所以估算定价意味着估算事件。  
	
	您所需支付的价格是您已连接到 {{site.data.keyword.mobileanalytics_short}} 的所有应用程序的事件总数。对于给定的应用程序，事件数取决于您在应用程序中实施的检测程度、用户数量以及用户活跃程度。 
	
	使用以下公式估算使用情况：每个应用程序每个月的事件数 = (每日用户数) x (每日每个用户的会话数) x (每月天数) x (每个会话的事件数)
	
	每会话事件数可以为 2 到几百个不等，取决于开发人员为应用程序配置的网络调用、定制分析、日志捕获和警报定义。


9. **分析数据可以保留多长时间？**

    数据保留时间不少于 30 天。
	
10. **数据显示在 {{site.data.keyword.mobileanalytics_short}} 控制台中需要花多长时间？**

    数据在 {{site.data.keyword.mobileanalytics_short}} Console 中几乎是实时的，也就是说，在实际事件发生后几秒之内，数据就会显示出来。
	
11. **{{site.data.keyword.mobileanalytics_full}} 与 MobileFirst Platform Foundation 中的移动分析有什么差别？**

    在这两种控制台中，用户和会话非常相似，但 MobileFirst Platform Foundation 随附的分析中还包含其他度量值和设置，客户机可以使用这些功能来管理自己的内部部署分析集群。此外，MobileFirst Platform Foundation 分析控制台将度量值零散提供给适配器和适配器程序，而在 {{site.data.keyword.mobileanalytics_short}} 服务中，这些度量值集成到网络请求图表和表中。
	
12. **我在内部部署中使用 MobileFirst Platform Foundation 来开发应用程序，但不想托管自己的分析集群。我可以改为使用 {{site.data.keyword.mobileanalytics_full}} 吗？**

    可以。您有两个选项：如果要使用 MobileFirst Platform Foundation 7.x 或 8.0，并且您的应用程序受 MobileFirst Platform SDK 检测，那么您可以配置 MobileFirst 服务器使其将分析数据报告给 {{site.data.keyword.mobileanalytics_short}} for {{site.data.keyword.Bluemix_notm}}。请阅读[配置 Mobile Analytics 和 Mobile Foundation IBM Cloud 服务 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://mobilefirstplatform.ibmcloud.com/blog/2016/07/11/analytics-bm-service/){: new_window} 博客帖子以了解详细信息。或者，您也可以使用 {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.mobileanalytics_short}} SDK 来检测您的应用程序，并直接报告给 {{site.data.keyword.mobileanalytics_short}} 服务。
