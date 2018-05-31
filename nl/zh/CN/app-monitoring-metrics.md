---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-06"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 使用度量和事件
{: #usingmetrics}

## 使用 Mobile Analytics 监视应用程序

{{site.data.keyword.mobileanalytics_full}} 可监视和分析移动应用程序。您可以使用 {{site.data.keyword.mobileanalytics_short}} 客户端 SDK 来记录应用程序日志并监视数据。开发者可以控制何时将这些数据发送到 {{site.data.keyword.mobileanalytics_short}} 服务。数据传递到 {{site.data.keyword.mobileanalytics_short}} 后，可以使用 {{site.data.keyword.mobileanalytics_short}} 控制台，来获取有关移动应用程序、设备和应用程序日志的分析洞察。
{: shortdesc}

##预定义的度量值

使用**预定义度量**，可以回答如下问题：

* 我有多少位新用户？  
* 有多少人正在积极地使用我的应用程序？  
* 人们使用我的应用程序有多频繁？ 
* 人们在一天中的什么时间使用我的应用程序？  
* 我的用户最喜欢用的是什么设备模型？ 
* 我应该何时淘汰对旧操作系统的支持？ 
* 哪些应用程序有性能问题？  

##定制事件

通过添加自己的**定制事件**，可以回答如下问题： 

* 哪些功能最常用，哪些不常用？  
* 用户在哪里进入我的应用程序，又在哪里离开？  
* 用户查看最多的活动是哪些？  
* 用户在应用程序中完成工作流（例如，转换漏斗）了吗？   

客户端日志和使用情况数据会自动收集，并根据需要发送到 Mobile Analytics 服务。开发者和管理员可使用 {{site.data.keyword.mobileanalytics_short}} 服务仪表板查看客户端 SDK 收集的数据。

## 数据可视化
{: data-visualization notoc}

分析服务收集的所有数据均可显示在 {{site.data.keyword.mobileanalytics_short}} 仪表板中，该仪表板可从 {{site.data.keyword.Bluemix_notm}} 仪表板访问，通过单击 IBM {{site.data.keyword.mobileanalytics_short}} 服务磁贴实例即可。<!--You can also create custom charts, based on data that is collected by the analytics service in the dashboard.-->除了简明的移动分析视图之外，分析功能还包括对如下数据执行原始搜索的功能：客户端日志、捕获的客户端崩溃数据以及您通过调用客户端 API 函数订阅到 {{site.data.keyword.mobileanalytics_short}} 服务而明确提供的任何其他数据。 

