---

copyright:
 years: 2018

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# SDKs for Mobile Analytics
{: #install-sdk}
Last updated: 18 January 2018
{: .last-updated}

The {{site.data.keyword.mobileanalytics_short}} Client SDKs are currently available for Android, iOS, Cordova and Web. Below are the links to  platform specific SDKs.

Refer the [document](install-client-sdk.html) for detailed information on installation and technical concepts.

{: shortdesc}

## SDK for Android

   Installing the [Android Client SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-analytics)


## SDK for iOS

   Installing the [iOS Client SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-analytics)

   
## SDK for Cordova

   Installing the [Cordova Client SDK](https://www.npmjs.com/package/bms-core)
   
## SDK for Web

   Installing the [Web Client SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-web-analytics/)
   
**Note** : For Web SDK, you need to configure your Mobile Analutics service instance to allow an app server. Provide the URL of your app server through the Service Confiuration REST API through Swagger UI. POST, GET, PUT and DELETE methods are provided for CRUD operations of the service configuration which is a list of allowed URL's. To GET and DELETE configurations of your service instance, use your API key. To create and update the service configuration, use POST and PUT methods with allowed URLs listed as body {"allowedUrls":["http://abc.com","https://www.xyz.com"]}. If you are accessing from a browser in the same system as that of the web server, provide "http://localhost" as the allowed URL.