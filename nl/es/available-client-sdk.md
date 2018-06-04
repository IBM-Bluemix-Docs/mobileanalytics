---

copyright:
 years: 2018

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# SDK para Mobile Analytics
{: #install-sdk}
Última actualización: 18 de enero de 2018
{: .last-updated}

Los SDK de cliente de {{site.data.keyword.mobileanalytics_short}} están disponibles
actualmente para Android, iOS, Cordova y Web. A continuación encontrará los enlaces con los SDK específicos de cada plataforma.

Consulte el [documento](install-client-sdk.html) para obtener información detallada sobre la instalación y los conceptos técnicos.

{: shortdesc}

## SDK para Android

   Instalación del [SDK de cliente de Android](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-analytics)


## SDK para iOS

   Instalación del [SDK de cliente de iOS](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-analytics)

   
## SDK para Cordova

   Instalación del [SDK de cliente de Cordova](https://www.npmjs.com/package/bms-core)
   
## SDK para web

   Instalación del [SDK de cliente de Web](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-web-analytics/)
   
**Nota** : para el SDK para Web, debe configurar la instancia del servicio Mobile Analytics de modo que permita un servidor de apps. Especifique el URL del servidor de apps mediante la API REST de configuración del servicio disponible en la IU de Swagger. Se proporcionan los métodos POST, GET, PUT y DELETE para las operaciones CRUD de la configuración del servicio, que es una lista de los URL permitidos. Para obtener (GET) y suprimir (DELETE) configuraciones de la instancia del servicio, utilice su clave de API. Para crear y actualizar la configuración del servicio, utilice los métodos POST y PUT con los URL permitidos que se muestran en el cuerpo {"allowedUrls":["http://abc.com","https://www.xyz.com"]}. Si accede desde un navegador que está en el mismo sistema que el del servidor web, especifique "http://localhost" como URL permitido.
