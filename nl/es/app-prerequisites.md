---

copyright:
 years: 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Requisitos previos
{: #prerequisites}
Última actualización: 18 de enero de 2018
{: .last-updated}


## Creación de una instancia del servicio Mobile Analytics
{: #prerequisites_1}

1. En el [Catálogo de IBM Cloud](https://console.ng.bluemix.net/catalog/), pulse **Móvil** > **Mobile Analytics**.
2. Especifique un nombre de servicio.
3. Pulse **Crear**.
4. Elija entre conectar con otras apps existentes o dejarlo sin enlazar.


Puede elegir entre crear un servicio enlazado o un servicio no enlazado. Los servicios enlazados se conectan a otras apps de IBM Cloud, mientras que los servicios no enlazados son independientes y no están conectados a otras apps. 

## Inicialización de la app
{: #prerequisites_app}

[Importe](/docs/services/mobileanalytics/available-client-sdk.html) e instale los {{site.data.keyword.mobileanalytics_short}} [SDK de cliente](/docs/services/mobileanalytics/install-client-sdk.html). Si lo desea puede utilizar la {{site.data.keyword.mobileanalytics_short}} [API REST ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://mobile-analytics-dashboard.{DomainName}/analytics-service/){:new_window}.


###Importar los SDK de cliente

Importe los SDK de cliente e inicialícelos con el siguiente fragmento de código para registrar las analíticas de uso:

- Android
	
    Añada las siguientes sentencias `import` al principio del archivo del proyecto:
		
	```
		import com.ibm.mobilefirstplatform.clientsdk.android.core.api.*;
import com.ibm.mobilefirstplatform.clientsdk.android.analytics.api.*;
import com.ibm.mobilefirstplatform.clientsdk.android.logger.api.*;
	```
    {: codeblock}

- iOS

    El SDK de Swift está disponible para iOS y watchOS.
		
    Importe las infraestructuras `BMSCore` y `BMSAnalytics`; para ello, añada las siguientes sentencias `import` al inicio del archivo del proyecto `AppDelegate.swift`:
	
	```Swift
		import BMSCore
		import BMSAnalytics
	```
    {: codeblock}
   
- Cordova
			
    Añada el plugin de Cordova ejecutando el siguiente mandato desde el directorio raíz de la aplicación de Cordova:
	
	```Javascript
		cordova plugin add bms-core
	```
    {: codeblock}
   
- Web
	
    Añada el plugin de web; para ello añada este script al archivo `index.html` de la app web:
	
	```Html
		<script src="bms-clientsdk-web-analytics/bmsanalytics.js"></script>
	```
    {: codeblock}

    También puede utilizar el cargador de módulos requirejs. El nombre utilizado como API de referencia coincide con el nombre del argumento (`BMSAnalytics`) utilizado. 
	
	 ```Javascript
	 	require.config({
	    'paths': {
	        'bmsanalytics': 'bms-clientsdk-web-analytics/bmsanalytics'
	    	}
		});
			require(['bmsanalytics'], function(BMSAnalytics) {
		    BMSAnalytics.send();
		}
	```
    {: codeblock}
		
		
El siguiente paso es [Preparar la app](app-instrument.html).


