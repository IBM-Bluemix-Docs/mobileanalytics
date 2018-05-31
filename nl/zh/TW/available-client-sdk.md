---

copyright:
 years: 2018

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Mobile Analytics 的 SDK
{: #install-sdk}
前次更新：2018 年 1 月 18 日
{: .last-updated}

{{site.data.keyword.mobileanalytics_short}} Client SDK 目前適用於 Android、iOS、Cordova 及 Web。下面是平台特定 SDK 的鏈結。

如需安裝及技術概念的詳細資訊，請參照[文件](install-client-sdk.html)。

{: shortdesc}

## Android SDK

   安裝 [Android Client SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-analytics)


## iOS SDK

   安裝 [iOS Client SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-analytics)

   
## Cordova SDK

   安裝 [Cordova Client SDK](https://www.npmjs.com/package/bms-core)
   
## Web SDK

   安裝 [Web Client SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-web-analytics/)
   
**附註**：對於 Web SDK，您需要配置 Mobile Analytics 服務實例，以容許應用程式伺服器。透過使用 Swagger 使用者介面的「服務配置 REST API」，提供應用程式伺服器的 URL。POST、GET、PUT 及 DELETE 方法是針對服務配置的 CRUD 作業所提供，而這是容許的 URL 清單。若要 GET（取得）及 DELETE（刪除）您服務實例的配置，請使用 API 金鑰。若要建立及更新服務配置，請使用 POST 及 PUT 方法並將容許的 URL 列為內文 {"allowedUrls":["http://abc.com","https://www.xyz.com"]}。如果您在與 Web 伺服器之系統相同的系統中從瀏覽器進行存取，請提供 "http://localhost" 作為容許的 URL。
