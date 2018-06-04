---

copyright:
 years: 2018

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# SDKs für Mobile Analytics
{: #install-sdk}
Letzte Aktualisierung: 18. Januar 2018
{: .last-updated}

Die {{site.data.keyword.mobileanalytics_short}}-Client-SDKs sind derzeit für Android, iOS, Cordova und Web verfügbar. Unten sind die Links zu plattformspezifischen SDKs aufgeführt.

Lesen Sie dieses [Dokument](install-client-sdk.html), um detaillierte Informationen zur Installation und zu den technischen Konzepten zu erhalten.

{: shortdesc}

## SDKs für Android

   Installation des [Android-Client-SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-analytics)


## SDKs für iOS

   Installation des [iOS-Client-SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-analytics)

   
## SDKs für Cordova

   Installation des [Cordova-Client-SDK](https://www.npmjs.com/package/bms-core)
   
## SDKs für Web

   Installation des [Web-Client-SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-web-analytics/)
   
**Hinweis**: Bei Web-SDKs müssen Sie Ihre Mobile Analytics-Serviceinstanz so konfigurieren, dass sie einen App-Server zulässt. Geben Sie die URL Ihres App-Servers über die REST-API für die Servicekonfiguration und mittels der Swagger-Benutzerschnittstelle an. Die Methoden POST, GET, PUT und DELETE werden für CRUD-Operationen der Servicekonfiguration angegeben, die eine Liste der zulässigen ULRs darstellt. Zum Abrufen oder Löschen (GET/DELETE) von Konfigurationen Ihrer Serviceinstanz verwenden Sie Ihren API-Schlüssel. Um die Servicekonfiguration zu erstellen und zu aktualisieren, verwenden Sie die Methoden POST und PUT mit zulässigen URLs, die als Hauptteil aufgelistet sind {"allowedUrls":["http://abc.com","https://www.xyz.com"]}. Wenn Sie von einem Browser in demselben System wie dem des Web-Servers zugreifen, geben Sie "http://localhost" als zulässige URL an.
