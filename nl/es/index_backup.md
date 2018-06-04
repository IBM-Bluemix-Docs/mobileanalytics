---

copyright:
  years: 2016, 2017
lastupdated: "2017-07-14"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Guía de aprendizaje de iniciación

{: #gettingstartedtemplate}

{{site.data.keyword.mobileanalytics_full}} proporciona a los desarrolladores, administradores de TI y a las partes interesadas del negocio información sobre el rendimiento de sus apps para móviles y cómo se utilizan. {{site.data.keyword.mobileanalytics_short}} le permite:

* Supervisar el rendimiento y el uso de todas las aplicaciones desde el escritorio o la tableta. 
* Identificar rápidamente tendencias y anomalías, obtener detalles para resolver problemas y desencadenar alertas cuando las métricas de claves atraviesan umbrales críticos. 
{: shortdesc}

Para que el servicio {{site.data.keyword.mobileanalytics_short}} esté activo y en ejecución rápidamente, siga estos pasos:

1. Después de crear una instancia <!--[create an instance](https://console.{DomainName}/docs/services/reqnsi.html#req_instance)-->del servicio {{site.data.keyword.mobileanalytics_short}}, puede acceder a la consola de {{site.data.keyword.mobileanalytics_short}} pulsando el mosaico en el panel de control de la sección **Servicios** de {{site.data.keyword.Bluemix}}. Dispone de una opción de **modalidad de demostración** en la consola de {{site.data.keyword.mobileanalytics_short}}, en la que las vistas y los gráficos muestran *datos de demostración*. La modalidad de demostración es la modalidad predeterminada de la consola cuando al iniciarse por primera vez tras crear la instancia del servicio. Cuando el servicio se rellene con sus propios datos analíticos y de aplicaciones, puede *desactivar* la modalidad de demostración para ver los datos de sus aplicaciones en distintos gráficos. La consola de {{site.data.keyword.mobileanalytics_short}} es de sólo lectura cuando se encuentre en modalidad de demostración, por lo que no podrá crear nuevas definiciones de alerta.

2. Instale los [SDK cliente](/docs/services/mobileanalytics/install-client-sdk.html) de {{site.data.keyword.mobileanalytics_short}}. Si lo desea puede utilizar la {{site.data.keyword.mobileanalytics_short}} [API REST ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://mobile-analytics-dashboard.{DomainName}/analytics-service/){:new_window}.
	
	- Configuración del servicio de app web
	
		Para el SDK Web, para configurar la instancia del servicio de modo que permita un servidor de app, debe suministrar el URL del servidor de app mediante la API REST de configuración del servicio disponible en la IU de Swagger. Se proporcionan los métodos POST, GET, PUT y DELETE para las operaciones CRUD de la configuración del servicio, que es una lista de los URL permitidos. Para obtener (GET) y suprimir (DELETE) configuraciones de la instancia del servicio, utilice su clave de API. Para crear y actualizar la configuración del servicio, utilice los métodos POST y PUT con los URL permitidos que se muestran en el cuerpo {"allowedUrls":["http://abc.com","https://www.xyz.com"]}. Si accede desde un navegador que está en el mismo sistema que el del servidor web, especifique "http://localhost" como URL permitido.

3. Importe los SDK de cliente e inicialícelos con el siguiente fragmento de código para registrar las analíticas de uso:

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
		
4. Inicialice el SDK de cliente de {{site.data.keyword.mobileanalytics_short}} del código de la aplicación para registrar el análisis de uso y las sesiones de aplicación utilizando el valor de [clave de API](/docs/services/mobileanalytics/sdk.html#analytics-clientkey).	
	
	- Android
	
		```
		BMSClient.getInstance().initialize(getApplicationContext(), BMSClient.REGION_US_SOUTH); // Puede cambiar la región
		Analytics.init(getApplication(), "your_app_name_here", "your_api_key_here", hasUserContext, collectLocation, Analytics.DeviceEvent.ALL);
		```
		{: codeblock}
	    
		El parámetro **bluemixRegion** especifica qué despliegue de {{site.data.keyword.Bluemix_notm}} está utilizando, por ejemplo, `BMSClient.REGION_US_SOUTH` y `BMSClient.REGION_UK`. 
	    <!-- , or `BMSClient.Region.Sydney`.-->
	    
		Establezca el valor para `hasUserContext` en **true** o **false**. Si es false (valor predeterminado), cada dispositivo se cuenta como un usuario activo.
		
		Establezca el valor de `collectLocation` en **true** o **false**. Si tiene el valor true, los datos de ubicación del dispositivo se enviarán como parte del registro de Appsession. 

	- iOS
	  
		Inicialice el SDK de cliente dentro del código de la aplicación para registrar el análisis de uso y las sesiones de aplicación utilizando el valor de [clave de API](/docs/services/mobileanalytics/sdk.html#analytics-clientkey).
		
		```Swift
		BMSClient.sharedInstance.initialize(bluemixRegion: BMSClient.Region.usSouth) // Puede cambiar la región
		Analytics.initialize(appName: "your_app_name_here", apiKey: "your_api_key_here", hasUserContext: false, collectLocation: true, deviceEvents: deviceEvents: .lifecycle, .network)
		```
		{: codeblock}
				
		El parámetro **bluemixRegion** especifica el despliegue de IBM Cloud que está utilizando, por ejemplo `BMSClient.Region.usSouth` o `BMSClient.Region.unitedKingdom`.
		<!-- , or `BMSClient.REGION_SYDNEY`. -->
	 
		Establezca el valor para `hasUserContext` en **true** o **false**. Si es false (valor predeterminado), cada dispositivo se cuenta como un usuario activo.
		
		Establezca el valor de `collectLocation` en **true** o **false**. Si tiene el valor true, los datos de ubicación del dispositivo se enviarán como parte del registro de Appsession. 
	
	- Cordova
		
		Inicialice el SDK de cliente dentro del código de la aplicación para registrar el análisis de uso y las sesiones de aplicación utilizando el valor de [clave de API](/docs/services/mobileanalytics/sdk.html#analytics-clientkey).
		
		```
		var appName = "your_app_name_here";
		var apiKey = "your_api_key_here";
		BMSClient.initialize(BMSClient.REGION_US_SOUTH); // Puede cambiar la región
		BMSAnalytics.initialize(appName, apiKey, hasUserContext, collectLocation, [BMSAnalytics.ALL])
		```
		{: codeblock}
		
		El parámetro **bluemixRegion** especifica el despliegue de IBM Cloud que está utilizando, por ejemplo `BMSClient.REGION_US_SOUTH` o `BMSClient.REGION_UK`.
		<!-- , or `BMSClient.REGION_SYDNEY`. -->
		Establezca el valor para `hasUserContext` en **true** o **false**. Si es false (valor predeterminado), cada dispositivo se cuenta como un usuario activo.
		
		Establezca el valor de `collectLocation` en **true** o **false**. Si tiene el valor true, los datos de ubicación del dispositivo se enviarán como parte del registro de Appsession.
    
	- Web
		
		Inicialice el SDK de cliente dentro del código de la aplicación para registrar el análisis de uso y las sesiones de aplicación utilizando el valor de [clave de API](/docs/services/mobileanalytics/sdk.html#analytics-clientkey).
		
		```
		var appName = "your_app_name_here";
		var apiKey = "your_api_key_here";
		BMSAnalytics.Client.initialize(BMSAnalytics.Client.REGION_US_SOUTH);
		BMSAnalytics.initialize(appName,apiKey,hasUserContext,BMSAnalytics.DeviceEvents.ALL,instanceId);
		``` 
		{: codeblock}

		El parámetro `bluemixRegion` especifica qué despliegue de {{site.data.keyword.Bluemix_notm}} está utilizando, por ejemplo, `BMSAnalytics.Client.REGION_US_SOUTH` y `BMSAnalytics.Client.REGION_UK`. Establezca el valor para `hasUserContext` en `true` o `false`. Si tiene el valor false (valor predeterminado), cada dispositivo se cuenta como un usuario activo. Establezca el valor de `instanceId` en su instanceId de servicio; es una serie alfanumérica que encontrará en el url del navegador correspondiente a su instancia de servicio tras la serie "...mobile-analytics_Prod/"  y hasta "/". 

		Tenga en cuenta que el nombre que seleccione para la aplicación (`your_app_name_here`) se muestra en la consola de {{site.data.keyword.mobileanalytics_short}} como nombre de la aplicación. El nombre de la aplicación se utiliza como filtro para buscar registros de aplicaciones en el panel de control. Si utiliza el mismo nombre de aplicación en varias plataformas (por ejemplo, en Android e iOS), podrá ver todos los registros de esa aplicación con el mismo nombre, independientemente de la plataforma desde la que se han enviado los registros.

5. Envíe las analíticas de uso registradas al servicio {{site.data.keyword.mobileanalytics_short}}. Una manera fácil de probar las analíticas consiste en ejecutar el siguiente código en el momento de iniciar la aplicación:

	- Android
	
		Utilice el método `Analytics.send()` para enviar datos analíticos al servidor. Puede colocar el método `Analytics.send()` en cualquier lugar del método `onCreate` de la actividad principal de la aplicación de Android, o en una ubicación que sea más adecuada para su proyecto. 
	
		Puede insertar `Analytics.send()` en cualquier lugar.
	
	- iOS
	
		Utilice el método `Analytics.send` para enviar datos analíticos al servidor. Puede colocar el método `Analytics.send` en cualquier lugar del método `application(_:didFinishLaunchingWithOptions:)` de la aplicación delegada o en una ubicación que sea más adecuada para su proyecto. 
	
	- Cordova
		
		Utilice el método `BMSAnalytics.send` para enviar datos analíticos al servidor. Coloque el método `BMSAnalytics.send` en la ubicación que mejor se ajuste a su proyecto.
		
	- Web
		
		Utilice el método `BMSAnalytics.send` para enviar datos analíticos al servidor. Coloque el método `BMSAnalytics.send` en la ubicación que mejor se ajuste a su proyecto. 
		
6. Consulte el tema [Preparación de la aplicación](/docs/services/mobileanalytics/sdk.html) para ver más información sobre las funciones de {{site.data.keyword.mobileanalytics_short}}, como por ejemplo [registro](/docs/services/mobileanalytics/sdk.html#app-monitoring-logger), [solicitudes de red](/docs/services/mobileanalytics/sdk.html#network-requests), [registro de ubicación](/docs/services/mobileanalytics/sdk.html#location-logging) y [analítica de bloqueo](/docs/services/mobileanalytics/sdk.html#report-crash-analytics).
	
7. Compile y ejecute la aplicación en el emulador o dispositivo.

8. Vaya a la consola de {{site.data.keyword.mobileanalytics_short}} para ver las analíticas de uso para su aplicación. También puede supervisar la aplicación <!--[creating custom charts](app-monitoring.html#custom-charts),-->[definiendo alertas](/docs/services/mobileanalytics/app-monitoring.html#alerts) y [supervisando bloqueos de la app](/docs/services/mobileanalytics/app-monitoring.html#monitor-app-crash).

# Enlaces relacionados
{: #rellinks notoc}

## SDK
{: #sdk notoc}
* [SDK de Android ![icono de enlace externo](../../icons/launch-glyph.svg "icono de enlace externo")](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-analytics){: new_window}  
* [SDK de iOS ![icono de enlace externo](../../icons/launch-glyph.svg "icono de enlace externo")](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-analytics){: new_window}
* [Cordova Plugin Core SDK ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.npmjs.com/package/bms-core){: new_window}
* [SDK Web ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-web-analytics/){: new_window}
## Referencia de API
{: #api notoc}
* [API REST ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://mobile-analytics-dashboard.{DomainName}/analytics-service/){:new_window}
