---

copyright:
 years: 2018

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Mobile Analytics 用の SDK
{: #install-sdk}
最終更新日: 2018 年 1 月 18 日
{: .last-updated}

{{site.data.keyword.mobileanalytics_short}} クライアント SDK は、現在 Android、iOS、Cordova、Web で使用できます。 プラットフォーム固有の SDK へのリンクを以下に示します。

インストールおよび技術的な概念について詳しくは、[資料](install-client-sdk.html)を参照してください。

{: shortdesc}

## Android 用の SDK

   [Android クライアント SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-analytics) のインストール


## iOS 用の SDK

   [iOS クライアント SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-analytics) のインストール

   
## Cordova 用の SDK

   [Cordova クライアント SDK](https://www.npmjs.com/package/bms-core) のインストール
   
## Web 用の SDK

   [Web クライアント SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-web-analytics/) のインストール
   
**注**: Web SDK の場合は、アプリ・サーバーを許可するように Mobile Analytics サービス・インスタンスを構成する必要があります。Swagger UI を介してサービス構成 REST API を使用し、アプリ・サーバーの URL を指定します。許可された URL のリストであるサービス構成の CRUD 操作用に POST、GET、PUT、および DELETE メソッドが提供されています。サービス・インスタンスの構成を GET および DELETE するには、API キーを使用します。サービス構成を作成および更新するには、POST メソッドおよび PUT メソッドを使用し、それに許可された URL を本文 {"allowedUrls": ["http://abc.com", "https://www.xyz.com"]} としてリストして指定します。Web サーバーと同じシステムのブラウザーからアクセスしている場合は、許可される URL として http://localhost を指定します。
