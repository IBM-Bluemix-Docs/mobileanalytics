---

copyright:
 years: 2018

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 用于 Mobile Analytics 的 SDK
{: #install-sdk}
上次更新时间：2018 年 1 月 18 日
{: .last-updated}

目前，Android、iOS、Cordova 和 Web 可以使用 {{site.data.keyword.mobileanalytics_short}} 客户端 SDK。下面是特定于平台的 SDK 的链接。

请参阅[文档](install-client-sdk.html)，以获取有关安装和技术概念的详细信息。

{: shortdesc}

## 用于 Android 的 SDK

   安装 [Android 客户端 SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-analytics)


## 用于 iOS 的 SDK

   安装 [iOS 客户端 SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-analytics)

   
## 用于 Cordova 的 SDK

   安装 [Cordova 客户端 SDK](https://www.npmjs.com/package/bms-core)
   
## 用于 Web 的 SDK

   安装 [Web 客户端 SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-web-analytics/)
   
**注**：对于 Web SDK，您需要将 Mobile Analytics 服务实例配置为允许应用程序服务器。在 Swagger UI 中通过服务配置 REST API 来提供应用程序服务器的 URL。为服务配置（即允许的 URL 列表）的 CRUD 操作提供 POST、GET、PUT 和 DELETE 方法。要执行服务实例的 GET 和 DELETE 配置，请使用 API 密钥。要创建和更新服务配置，请使用 POST 和 PUT 方法，并将允许的 URL 列为主体 {"allowedUrls":["http://abc.com","https://www.xyz.com"]}。如果在与 Web 服务器的系统相同的系统中通过浏览器进行访问，请提供“http://localhost”作为允许的 URL。
