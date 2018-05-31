---

copyright:
 years: 2018

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# SDK per Mobile Analytics
{: #install-sdk}
Ultimo aggiornamento: 18 gennaio 2018
{: .last-updated}

Le SDK client {{site.data.keyword.mobileanalytics_short}} sono attualmente disponibili per Android, iOS, Cordova e Web. I seguenti sono i link alle SDK specifiche per piattaforma.

Fai riferimento al [documento](install-client-sdk.html) per informazioni dettagliate sull'installazione e sui concetti tecnici.

{: shortdesc}

## SDK per Android

   Installazione di [Android Client SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-analytics)


## SDK per iOS

   Installazione di [iOS Client SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-analytics)

   
## SDK per Cordova

   Installazione di [Cordova Client SDK](https://www.npmjs.com/package/bms-core)
   
## SDK per Web

   Installazione di [Web Client SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-web-analytics/)
   
**Nota** : per l'SDK Web, devi configurare la tua istanza del servizio Mobile Analytics per consentire un server dell'applicazione. Fornisci l'URL del tuo server dell'applicazione tramite l'API REST di configurazione del servizio attraverso la IU Swagger. I metodi POST, GET, PUT e DELETE vengono forniti per le operazioni CRUD della configurazione del servizio che è un elenco di URL consentiti. Per le configurazioni GET e DELETE della tua istanza del servizio, utilizza la chiave API. Per creare e aggiornare la configurazione del servizio, utilizza i metodi POST e PUT con gli URL consentiti elencati come corpo {"allowedUrls":["http://abc.com","https://www.xyz.com"]}. Se stai accedendo da un browser nello stesso sistema del server web, fornisci "http://localhost" come URL consentito.
