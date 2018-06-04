---

copyright:
 years: 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Preparación de la app
{: #Instrument}
Última actualización: 18 de enero de 2018
{: .last-updated}

##Inicialice el SDK de cliente de {{site.data.keyword.mobileanalytics_short}} 

Inicialice el SDK de cliente de {{site.data.keyword.mobileanalytics_short}} del código de la aplicación para registrar el análisis de uso y las sesiones de aplicación utilizando el valor de [clave de API](/docs/services/mobileanalytics/sdk.html#analytics-clientkey).	
	
- **Android**
	
```
		BMSClient.getInstance().initialize(getApplicationContext(), BMSClient.REGION_US_SOUTH); // Puede cambiar la región
		Analytics.init(getApplication(), "your_app_name_here", "your_api_key_here", hasUserContext, collectLocation, Analytics.DeviceEvent.ALL);
```
		{: codeblock}
	    
El parámetro **bluemixRegion** especifica qué despliegue de {{site.data.keyword.Bluemix_notm}} está utilizando, por ejemplo, `BMSClient.REGION_US_SOUTH` y `BMSClient.REGION_UK`. 
	    
	    
Establezca el valor para `hasUserContext` en **true** o **false**. Si es false (valor predeterminado), cada dispositivo se cuenta como un usuario activo.
		
Establezca el valor de `collectLocation` en **true** o **false**. Si tiene el valor true, los datos de ubicación del dispositivo se enviarán como parte del registro de Appsession. 

- **iOS**
	  
Inicialice el SDK de cliente dentro del código de la aplicación para registrar el análisis de uso y las sesiones de aplicación utilizando el valor de [clave de API](/docs/services/mobileanalytics/sdk.html#analytics-clientkey).
		
```Swift
		BMSClient.sharedInstance.initialize(bluemixRegion: BMSClient.Region.usSouth) // Puede cambiar la región
		Analytics.initialize(appName: "your_app_name_here", apiKey: "your_api_key_here", hasUserContext: false, collectLocation: true, deviceEvents: deviceEvents: .lifecycle, .network)
```
		{: codeblock}
				
El parámetro **bluemixRegion** especifica el despliegue de IBM Cloud que está utilizando, por ejemplo `BMSClient.Region.usSouth` o `BMSClient.Region.unitedKingdom`.
		
	 
Establezca el valor para `hasUserContext` en **true** o **false**. Si es false (valor predeterminado), cada dispositivo se cuenta como un usuario activo.
		
Establezca el valor de `collectLocation` en **true** o **false**. Si tiene el valor true, los datos de ubicación del dispositivo se enviarán como parte del registro de Appsession. 
	
- **Cordova**
		
Inicialice el SDK de cliente dentro del código de la aplicación para registrar el análisis de uso y las sesiones de aplicación utilizando el valor de [clave de API](/docs/services/mobileanalytics/sdk.html#analytics-clientkey).
		
```
		var appName = "your_app_name_here";
		var apiKey = "your_api_key_here";
		BMSClient.initialize(BMSClient.REGION_US_SOUTH); // Puede cambiar la región
		BMSAnalytics.initialize(appName, apiKey, hasUserContext, collectLocation, [BMSAnalytics.ALL])
```
		{: codeblock}
		
El parámetro **bluemixRegion** especifica el despliegue de IBM Cloud que está utilizando, por ejemplo `BMSClient.REGION_US_SOUTH` o `BMSClient.REGION_UK`.
		
Establezca el valor para `hasUserContext` en **true** o **false**. Si es false (valor predeterminado), cada dispositivo se cuenta como un usuario activo.
		
Establezca el valor de `collectLocation` en **true** o **false**. Si tiene el valor true, los datos de ubicación del dispositivo se enviarán como parte del registro de Appsession.
    
- **Web**
		
Inicialice el SDK de cliente dentro del código de la aplicación para registrar el análisis de uso y las sesiones de aplicación utilizando el valor de [clave de API](/docs/services/mobileanalytics/sdk.html#analytics-clientkey).
		
```
		var appName = "your_app_name_here";
		var apiKey = "your_api_key_here";
		BMSAnalytics.Client.initialize(BMSAnalytics.Client.REGION_US_SOUTH);
		BMSAnalytics.initialize(appName,apiKey,hasUserContext,BMSAnalytics.DeviceEvents.ALL,instanceId);
``` 
		{: codeblock}

El parámetro `bluemixRegion` especifica el despliegue de {{site.data.keyword.Bluemix_notm}} que está utilizando. Establezca el valor para `hasUserContext` en `true` o `false`. Si tiene el valor false (valor predeterminado), cada dispositivo se cuenta como un usuario activo. Establezca el valor de `instanceId` en su instanceId de servicio; es una serie alfanumérica que encontrará en el url del navegador correspondiente a su instancia de servicio tras la serie "...mobile-analytics_Prod/"  y hasta "/". 

**Nota**: el nombre que seleccione para la aplicación (`your_app_name_here`) se mostrará en la consola de {{site.data.keyword.mobileanalytics_short}} como el nombre de la aplicación. El nombre de la aplicación se utiliza como filtro para buscar registros de aplicaciones en el panel de control. Si utiliza el mismo nombre de aplicación en varias plataformas (por ejemplo, en Android e iOS), podrá ver todos los registros de esa aplicación con el mismo nombre, independientemente de la plataforma desde la que se han enviado los registros.

##Enviar datos de la app al servicio {{site.data.keyword.mobileanalytics_short}}

Envíe las analíticas de uso registradas al servicio {{site.data.keyword.mobileanalytics_short}}. Una manera fácil de probar las analíticas consiste en ejecutar el siguiente código en el momento de iniciar la aplicación:


- **Android**
	
Utilice el método `Analytics.send()` para enviar datos analíticos al servidor. Puede colocar el método `Analytics.send()` en cualquier lugar del método `onCreate` de la actividad principal de la aplicación de Android, o en una ubicación que sea más adecuada para su proyecto. 
	
Puede insertar `Analytics.send()` en cualquier lugar.
	
- **iOS**
	
Utilice el método `Analytics.send` para enviar datos analíticos al servidor. Puede colocar el método `Analytics.send` en cualquier lugar del método `application(_:didFinishLaunchingWithOptions:)` de la aplicación delegada o en una ubicación que sea más adecuada para su proyecto. 
	
- **Cordova**
		
Utilice el método `BMSAnalytics.send` para enviar datos analíticos al servidor. Coloque el método `BMSAnalytics.send` en la ubicación que mejor se ajuste a su proyecto.
		
- **Web**
		
Utilice el método `BMSAnalytics.send` para enviar datos analíticos al servidor. Coloque el método `BMSAnalytics.send` en la ubicación que mejor se ajuste a su proyecto. 
		



Consulte el tema [Preparación de la aplicación](/docs/services/mobileanalytics/sdk.html) para ver más información sobre las funciones de {{site.data.keyword.mobileanalytics_short}}, como por ejemplo [registro](/docs/services/mobileanalytics/sdk.html#app-monitoring-logger), [solicitudes de red](/docs/services/mobileanalytics/sdk.html#network-requests), [registro de ubicación](/docs/services/mobileanalytics/sdk.html#location-logging) y [analítica de bloqueo](/docs/services/mobileanalytics/sdk.html#report-crash-analytics).


El siguiente paso es **Compilar y ejecutar la aplicación en el emulador o dispositivo**.
