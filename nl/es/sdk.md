---

copyright:
  years: 2015, 2017
lastupdated: "2018-01-18"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Preparar la aplicación
{: #mobileanalytics_sdk}

## Prepare la aplicación para que utilice los SDK de cliente de {{site.data.keyword.mobileanalytics_short}}

Los SDK de {{site.data.keyword.mobileanalytics_full}} le permiten preparar su aplicación para móvil.
{: shortdesc}

{{site.data.keyword.mobileanalytics_short}} le permite recopilar las siguientes categorías de datos, cada una de las cuales requiere un nivel de preparación distinto:


- Datos predefinidos: esta categoría incluye información genérica de uso y de los dispositivos que se aplica a todas las aplicaciones. En esta categoría se encuentran los metadatos de dispositivo (sistema operativo y modelo de dispositivo) y los datos de uso (usuarios activos y sesiones de aplicaciones), que indican el volumen, la frecuencia o el tiempo de uso de una aplicación. Los datos predefinidos se recopilan automáticamente una vez inicializado el SDK de {{site.data.keyword.mobileanalytics_short}} en la aplicación.

- Mensajes de registro de aplicaciones: esta categoría permite que los desarrolladores añadan líneas de código a la aplicación que registran mensajes personalizados para ayudar al desarrollo y a la depuración. El desarrollador asigna un nivel de gravedad/detalle a todos los mensajes de registro y puede filtrarlos según el nivel asignado o bien conservar el espacio de almacenamiento configurando la aplicación para que ignore los mensajes que estén a un nivel inferior a un determinado nivel de registro. Para recopilar los datos de registro de la aplicación, debe inicializar el SDK de {{site.data.keyword.mobileanalytics_short}} en la aplicación y añadir una línea de código para cada mensaje de registro.

- Sucesos personalizados: Esta categoría incluye datos que define usted mismo y que son específicos de la app. Estos datos representan sucesos que se producen en la app, como las vistas de páginas, las pulsaciones de botones o las compras dentro de la app. Además de inicializar el SDK de {{site.data.keyword.mobileanalytics_short}} en la app, debe añadir una línea de código para cada suceso personalizado que desee seguir. 

En este momento, los SDK están disponibles para Android, iOS, WatchOS, Cordova y Web.

## Identificación del valor de la clave de API de Credenciales de servicio
{: #analytics-clientkey}

Identifique el valor **Clave de API** antes de configurar el SDK de cliente. La clave de API es necesaria para inicializar el SDK de cliente.

1. Abra el panel de control del servicio {{site.data.keyword.mobileanalytics_short}}.
1. Expanda **Ver credenciales** para revelar el valor de la Clave de API. Necesitará el valor de la Clave de API al inicializar el SDK de cliente de {{site.data.keyword.mobileanalytics_short}}.


## Inicialización de la aplicación para recopilar análisis
{: #initalize-ma-sdk}

Inicialice la aplicación para habilitar el envío de registros al servicio {{site.data.keyword.mobileanalytics_short}}.

1. Importe el SDK de cliente.
	- Android
	
		Añada las siguientes sentencias `import` al principio del archivo del proyecto:
		
		```
		import com.ibm.mobilefirstplatform.clientsdk.android.core.api.*;
import com.ibm.mobilefirstplatform.clientsdk.android.analytics.api.*;
import com.ibm.mobilefirstplatform.clientsdk.android.logger.api.*;
		```
		{: codeblock}
  
	- iOS
		
		El SDK de Swift está disponible para iOS y watchOS.	Importe las infraestructuras `BMSCore` y `BMSAnalytics`; para ello, añada las siguientes sentencias `import` al inicio del archivo del proyecto `AppDelegate.swift`:
	
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
			
		Añada el plugin web mediante la adición del SDK proporcionado como script a index.html:
	
		```Html
		<script src="/path/to/bms-clientsdk-web-analytics/bmsanalytics.js"></script>
		```
		{: codeblock} 	 	

	 	O bien añada el plugin Web mediante el cargador de módulos requirejs: 
	
	 	```Javascript
	 	require.config({
	    'paths': {
	        'bmsanalytics': '/path/to/bms-clientsdk-web-analytics/bmsanalytics'
	    	}
		});
		require(['bmsanalytics'], function(BMSAnalytics) {
		 BMSAnalytics.send();
		}
		``` 	
		{: codeblock}  

2. Inicialice el SDK de cliente de {{site.data.keyword.mobileanalytics_short}} en la aplicación.

	- Android
		
		Inicialice el SDK de cliente de {{site.data.keyword.mobileanalytics_short}} en su aplicación Android; para ello, añada el código de inicialización al método `onCreate` de la actividad principal de la aplicación Android, o bien en una ubicación que sea más adecuada para su proyecto.
	
		```Java
		BMSClient.getInstance().initialize(getApplicationContext(), BMSClient.REGION_US_SOUTH); // Asegúrese de apuntar a su región
		```
		{: codeblock}
	
		Debe inicializar `BMSClient` con el parámetro **bluemixRegion**. En el inicializador, el valor **bluemixRegion** especifica el despliegue de {{site.data.keyword.Bluemix_notm}} que está utilizando, por ejemplo `BMSClient.REGION_US_SOUTH` y `BMSClient.REGION_UK`. 
	    <!-- , or `BMSClient.REGION_SYDNEY`.--> 
    
	- iOS
	    
		Primero inicialice la clase `BMSClient` con el siguiente código. Coloque el código de inicialización en el método `application(_:didFinishLaunchingWithOptions:)` de la aplicación delegada o en una ubicación que sea más adecuada para su proyecto.
		
		```Swift
		BMSClient.sharedInstance.initialize(bluemixRegion: BMSClient.Region.usSouth) // Asegúrese de apuntar a su región
		```
		{: codeblock}
	
		Debe inicializar `BMSClient` con el parámetro **bluemixRegion**. En el inicializador, el valor **bluemixRegion** especifica el despliegue de {{site.data.keyword.Bluemix_notm}} que está utilizando, por ejemplo `BMSClient.Region.usSouth` o `BMSClient.Region.unitedKingdom`.
	    <!-- , or `BMSClient.Region.Sydney`. -->
    
	- Cordova
	  
		Inicialice **BMSClient** y **BMSAnalytics**. También necesitará el valor [**Clave de API**](#analytics-clientkey).
	
		```Javascript
		BMSClient.initialize(BMSClient.REGION_US_SOUTH); //Asegúrese de apuntar a su región	
		```
		{: codeblock}
		
		Para utilizar el SDK de cliente de {{site.data.keyword.mobileanalytics_short}}, debe inicializar `BMSClient` con el parámetro **bluemixRegion**. En el inicializador, el valor **bluemixRegion** especifica el despliegue de {{site.data.keyword.Bluemix_notm}} que está utilizando, por ejemplo `BMSClient.REGION_US_SOUTH` o `BMSClient.REGION_UK`.
	    <!-- , or `BMSClient.REGION_SYDNEY`. -->
    
	- Web

	    Inicialice el SDK de cliente dentro del código de la aplicación para registrar el análisis de uso y las sesiones de aplicación utilizando el valor de clave de API.
	    ```javascript
	    BMSAnalytics.Client.initialize(BMSAnalytics.Client.REGION_US_SOUTH);
	    ```
	    {: codeblock}
		
		Para utilizar el SDK de cliente de {{site.data.keyword.mobileanalytics_short}}, debe inicializar `BMSAnalytics.Client` con el parámetro **bluemixRegion**. En el inicializador, el valor **bluemixRegion** especifica el despliegue de {{site.data.keyword.Bluemix_notm}} que está utilizando, por ejemplo `BMSAnalytics.Client..REGION_UK` o `BMSAnalytics.Client..REGION_US_SOUTH`.
	    <!-- , or `BMSClient.REGION_SYDNEY`. -->
    
3. Inicialice Analytics utilizando el objeto de la aplicación y asignándole el nombre de su aplicación. 

	El nombre que seleccione para la aplicación (`your_app_name_here`) se muestra en la consola de {{site.data.keyword.mobileanalytics_short}} como nombre de la aplicación. El nombre de la aplicación se utiliza como filtro para buscar registros de aplicaciones en el panel de control. Si utiliza el mismo nombre de aplicación en varias plataformas (por ejemplo, en Android e iOS), podrá ver todos los registros de esa aplicación con el mismo nombre, independientemente de la plataforma desde la que se han enviado los registros.

	También necesita el valor [Clave de API](#analytics-clientkey).

- Android
		
	```Java
	// En este código de ejemplo, Analytics está configurado para registrar sucesos de ciclo de vida.
		Analytics.init(getApplication(), "your_app_name_here", apiKey, hasUserContext, collectLocation, Analytics.DeviceEvent.ALL);
	```
    {: codeblock}
		
	**Nota:** Establezca el valor para `hasUserContext` en **true** o **false**. Si es false (valor predeterminado), cada dispositivo se cuenta como un usuario activo. El método [`Analytics.setUserIdentity("username")`](sdk.html#android-tracking-users), que le permite realizar el seguimiento del número de usuarios por dispositivo que están utilizando de forma activa la aplicación, no funcionará cuando `hasUserContext` sea false. Si es true, cada uso de [`Analytics.setUserIdentity("username")`](sdk.html#android-tracking-users) cuenta como un usuario activo. No hay ninguna identidad de usuario predeterminado cuando `hasUserContext` es true y, por lo tanto, debe establecerse para rellenar los gráficos del usuario activo.
	El método `Analytics.logLocation()`, que permite a la app enviar la ubicación del dispositivo, funcionará si `collectLocation` tiene el valor true. 
		
		
	
- iOS
		
	```Swift
		Analytics.initialize(appName: "your_app_name_here", apiKey: "your_api_key_here", hasUserContext: false, collectLocation: true, deviceEvents: .lifecycle, .network)
	```
    {: codeblock}
 	
- watchOS
		 	
	```Swift
		Analytics.initialize(appName: "your_app_name_here", apiKey: "your_api_key_here",collectLocation: true, deviceEvents: .network)
	```
    {: codeblock}
	 	
    Un parámetro `deviceEvents` opcional recopila de forma automática las analíticas de los eventos de nivel de dispositivo.
		
    Establezca el valor para `hasUserContext` en **true** o **false**. Si es false (valor predeterminado), cada dispositivo se cuenta como un usuario activo. El método [`Analytics.userIdentity = "username"`](sdk.html#ios-tracking-users), que le permite realizar el seguimiento del número de usuarios por dispositivo que están utilizando de forma activa la aplicación, no funcionará cuando `hasUserContext` sea false. Si `hasUserContext` tiene el valor true, cada uso de [`Analytics.userIdentity = "username"`](sdk.html#ios-tracking-users) cuenta como un usuario activo. No hay ninguna identidad de usuario predeterminado cuando `hasUserContext` es true y, por lo tanto, debe establecerse para rellenar los gráficos del usuario activo.
    El método `Analytics.logLocation()`, que permite a la app enviar la ubicación del dispositivo, funcionará si `collectLocation` tiene el valor true. 

- watchOS
	
    Puede registrar los sucesos del dispositivo en WatchOS mediante los métodos `Analytics.recordApplicationDidBecomeActive()` y `Analytics.recordApplicationWillResignActive()`.
	  
    Añada la siguiente línea al método `applicationDidBecomeActive()` de la clase ExtensionDelegate:
	 
	```Javascript
		Analytics.recordApplicationDidBecomeActive()
	```
    {: codeblock}
	
    Añada la siguiente línea al método `applicationWillResignActive()` de la clase ExtensionDelegate:
	 
	```Javascript
		Analytics.recordApplicationWillResignActive()
	```
    {: codeblock}	
		
- Cordova
		
	```Javascript
	Analytics.initialize(appName, apiKey,  hasUserContext, collectLocation, [BMSAnalytics.ALL])
	```
    {: codeblock}	
		
    Establezca el valor para `hasUserContext` en **true** o **false**. Si es false (valor predeterminado), cada dispositivo se cuenta como un usuario activo. El método `Analytics.setUserIdentity("username")`, que le permite realizar el seguimiento del número de usuarios por dispositivo que están utilizando de forma activa la aplicación, no funcionará cuando `hasUserContext` sea false. Si es true, cada uso de `Analytics.setUserIdentity("username")`(sdk.html#android-tracking-users) cuenta como un usuario activo. No hay ninguna identidad de usuario predeterminado cuando `hasUserContext` es true y, por lo tanto, debe establecerse para rellenar los gráficos del usuario activo.
    El método `Analytics.logLocation()`, que permite a la app enviar la ubicación del dispositivo, funcionará si `collectLocation` tiene el valor true. 
	
- Web
		
	```Java		
		// En este código de ejemplo, Analytics está configurado para que registro todos los sucesos.
		BMSAnalytics.initialize(appName, apiKey, hasUserContext, BMSAnalytics.DeviceEvent.ALL);
	```
    {: codeblock}
		
    Establezca el valor para `hasUserContext` en **true** o **false**. Si es false (valor predeterminado), cada dispositivo se cuenta como un usuario activo. El método [`BMSAnalytics.setUserIdentity("username")`](sdk.html#web-tracking-users), que le permite realizar el seguimiento del número de usuarios por dispositivo que están utilizando de forma activa la aplicación, no funcionará cuando `hasUserContext` sea false. Si es true, cada uso de [`BMSAnalytics.setUserIdentity("username")`](sdk.html#web-tracking-users) cuenta como un usuario activo. No hay ninguna identidad de usuario predeterminado cuando `hasUserContext` es true y, por lo tanto, debe establecerse para rellenar los gráficos del usuario activo.	

4. Ya ha inicializado la aplicación para recopilar analíticas. A continuación puede [enviar datos analíticos](sdk.html#app-monitoring-gathering-analytics) al servicio {{site.data.keyword.mobileanalytics_short}}.


## Recopilación de analíticas de uso
{: #app-monitoring-gathering-analytics}

Puede configurar el SDK de cliente de {{site.data.keyword.mobileanalytics_short}} para que registre analíticas de uso y envíe los datos registrados al servicio {{site.data.keyword.mobileanalytics_short}}.

Utilice las siguientes API para empezar a registrar y enviar analíticas de uso:

- Android
	
	```
	// Inhabilitar el registro de las analíticas de uso (por ejemplo, para ahorrar espacio de disco)
// El registro está habilitado de forma predeterminada
Analytics.disable();
	// Habilitar el registro de las analíticas de uso
	Analytics.enable();
	// Enviar las analíticas de uso registradas a Mobile Analytics Service
	Analytics.send(new ResponseListener() {
	            @Override
            public void onSuccess(Response response) {
	                // Gestionar aquí el resultado correcto del envío de Analytics.
            }
	            @Override
            public void onFailure(Response response, Throwable throwable, JSONObject jsonObject) {
	                // Gestionar aquí el resultado erróneo del envío de Analytics.
            }
	        });
	```
	{: codeblock}
		
	Análisis de uso de ejemplo para el registro de un suceso:
		
	```
	// Registrar un suceso de analíticas personalizado
	JSONObject eventJSONObject = new JSONObject();
	eventJSONObject.put("customProperty" , "propertyValue");
	Analytics.log(eventJSONObject);
	```
	{: codeblock}


- iOS (Swift)

	```
	// Inhabilitar el registro de las analíticas de uso (por ejemplo, para ahorrar espacio de disco)
	// El registro está habilitado de forma predeterminada
	Analytics.isEnabled = false
	// Habilitar el registro de las analíticas de uso
	Analytics.isEnabled = true
	// Enviar las analíticas de uso registradas a Mobile Analytics Service
	Analytics.send(completionHandler: { (response: Response?, error: Error?) in
	    if let response = response {
	        // Gestionar aquí el resultado correcto del envío de Analytics.
            }
	    if let error = error {
	        // Gestionar aquí el resultado erróneo del envío de Analytics.
            }
	})
	```
	{: codeblock}
	
	Análisis de uso de ejemplo para el registro de un suceso:
	
	```Swift
	// Registrar un suceso de analíticas personalizado
	let eventObject = ["customProperty": "propertyValue"]
	Analytics.log(metadata: eventObject)
	```
	{: codeblock}

- Cordova

	```JavaScript
	// Habilitar el registro de analíticas de uso
	BMSAnalytics.enable();
	// Inhabilitar el registro de analíticas de uso
	BMSAnalytics.disable();
	// Enviar las analíticas de uso registradas al servicio {{site.data.keyword.mobileanalytics_short}}
	BMSAnalytics.send(
		function(response) {
			console.log('success: ' + response);
		},
	function (err) {
			console.log('fail: ' + err);
		});
	```
	{: codeblock}
	
	Análisis de uso de ejemplo para el registro de un suceso:
	
	```JavaScript
	// Registrar un suceso de analíticas personalizado
	var eventObject = {"customProperty": "propertyValue"}
	BMSAnalytics.log(eventObject)
	```
	{: codeblock}

	Cuando desarrolle aplicaciones Cordova, utilice la API nativa para habilitar el registro de sucesos del ciclo de vida de la aplicación.
 
- Web
		
	```
	// Inhabilitar el registro de las analíticas de uso (por ejemplo, para ahorrar espacio de disco)
	// El registro está habilitado de forma predeterminada
	BMSAnalytics.disable();
	// Habilitar el registro de las analíticas de uso
	BMSAnalytics.enable();
	// Enviar las analíticas de uso registradas a Mobile Analytics Service
	BMSAnalytics.send().then(function(result) {
         	//Gestionar aquí el resultado correcto
        }, function(err) {
                //Gestionar aquí el resultado erróneo
        });;
	```
	{: codeblock}
		
	Análisis de uso de ejemplo para el registro de un suceso:
		
	```JavaScript
	// Registrar un suceso de analíticas personalizado
	var eventObject = {"customProperty": "propertyValue"}
	BMSAnalytics.log(eventObject)
	```
	{: codeblock}
  
## Habilitación, configuración y uso del registrador

El SDK de cliente de {{site.data.keyword.mobileanalytics_full}} proporciona una infraestructura de registro que se parece a otras infraestructuras de registro con las que puede estar familiarizado, como `java.util.logging` o `log4j`. La infraestructura de registro admite varias instancias del registrador por paquete, distintos niveles de registro, la captura de seguimientos de pilas del bloqueo de una aplicación, etc.

También puede configurar los datos registrados para almacenarlos en el dispositivo en el que se ejecuta la aplicación y enviar posteriormente estos registros del dispositivo al servicio {{site.data.keyword.mobileanalytics_short}}.

<!-- Initialization has to happen first to be able to collect logs and send them to the {{site.data.keyword.mobileanalytics_short}} service. -->

La infraestructura de registro del SDK de cliente de {{site.data.keyword.mobileanalytics_short}} admite los siguientes niveles de registro, que aparecen ordenados de menos a más detallados, con directrices de uso recomendado:

  * `FATAL`: se usa para bloqueos irrecuperables. El nivel `FATAL` está reservado para errores de registro irrecuperables que ven los usuarios como un bloqueo de aplicación
  * `ERROR`: se usa para excepciones o errores de protocolo de red no esperados
  * `WARN`: se usa para registrar advertencias de uso que no se consideran errores críticos, como el uso de API en desuso o en caso de una respuesta de red lenta
  * `INFO`: se usa para registrar eventos de inicialización y otros datos que podrían ser importantes, pero no urgentes
  * `DEBUG`: se usa para notificar sentencias de depuración para que los desarrolladores puedan resolver defectos de la aplicación


### Caso de ejemplo de nivel de registro
{: #log-level-scenario notoc}

Si el nivel de registro está configurado en `FATAL`, el registrador captura las excepciones no capturadas, pero no captura ningún registro que conduzca al evento de bloqueo. Puede establecer un nivel de registro más detallado para garantizar que también se capturen los registros que puedan conducir a una entrada de registro `FATAL`, como `WARN` y `ERROR`.

Cuando el nivel de registro es `DEBUG`, también obtiene registros del SDK de cliente de Mobile Analytics, que se incluye cuando se envían los registros.

<!-- **Note:** Find full Logger API references for each platform at [SDKs, samples, API reference](sdks-samples-apis.html). The Logger API is part of the--> <!--{{site.data.keyword.mobileanalytics_short}} Client SDK Core. -->


### Ejemplo de uso del registrador
{: #sample-logger-usage notoc}

**Nota:** Asegúrese de que ha preparado la aplicación para que utilice el SDK de cliente de {{site.data.keyword.mobileanalytics_short}} antes de utilizar la infraestructura de registro.
 
En los siguientes fragmentos de código se muestra un ejemplo de uso del registrador:

- Android
	
	```
	// Configurar el registrador de modo que guarde los registros en el dispositivo
	// para que luego se puedan enviar al servicio Mobile Analytics
	// Inhabilitado de forma predeterminada; establézcalo en true para habilitar
	Logger.storeLogs(true);
	// Cambiar el nivel mínimo de registro (opcional)
	// El valor predeterminado es Logger.LEVEL.DEBUG
	Logger.setLogLevel(Logger.LEVEL.INFO);
	// Crear dos instancias del registrador
	// Puede crear varias instancias de registro para organizar sus registros
	Logger logger1 = Logger.getLogger("logger1");
	Logger logger2 = Logger.getLogger("logger2");
	// Registrar los mensajes con distintos niveles
	// Mensaje de depuración para la característica 1
	// Mensaje de información para la característica 2
	logger1.debug("debug message");
	//el mensaje logger1.debug no se registra porque logLevelFilter está establecido en Info
	logger2.info("info message");
	// Enviar los registros al servicio Mobile Analytics
	Logger.send(new ResponseListener() {
		@Override
		public void onSuccess(Response response) {
			// Gestionar aquí el envío correcto del registrador.
		}
		@Override
		public void onFailure(Response response, Throwable throwable, JSONObject jsonObject) {
			// Gestionar aquí el envío anómalo del registrador.
		}
	});        
	```
	{: codeblock}


- iOS (Swift)
	
	```
	// Configurar el registrador de modo que guarde los registros en el dispositivo
	// para que luego se puedan enviar al servicio Mobile Analytics
	// Inhabilitado de forma predeterminado; establézcalo en true para habilitar
	Logger.isLogStorageEnabled = true
	// Cambiar el nivel mínimo de registro (opcional)
	// El valor predeterminado es LogLevel.debug
	Logger.logLevelFilter = LogLevel.info
	// Crear dos instancias del registrador
	// Puede crear varias instancias de registro para organizar sus registros
	let logger1 = Logger.logger(name: "feature1Logger")
	let logger2 = Logger.logger(name: "feature2Logger")
	// Registrar mensajes con distintos niveles
	logger1.debug(message: "debug message for feature 1") 
	// El mensaje logger1.debug no se registra porque
	// logLevelFilter está establecido en info
	logger2.info(message: "info message for feature 2")
	// Enviar registros al servicio Mobile Analytics
	Logger.send(completionHandler: { (response: Response?, error: Error?) in
	        if let response = response {
	        logger.debug(message: "Status code: \(response.statusCode)")
	        logger.debug(message: "Response: \(response.responseText)")
	    }
	    if let error = error {
	        logger.error(message: "Error: \(error)")
	    }
	})
	```
	{: codeblock}

	**Sugerencia:** Por motivos de privacidad, puede inhabilitar la salida del registrador para las aplicaciones compiladas en modo de publicación. De forma predeterminada, la clase Logger imprime registros en la consola de Xcode. En la configuración de compilación del destino, añada un indicador `-D RELEASE_BUILD` a la sección **Otros indicadores Swift** de la configuración de compilación de la versión.
    

- Cordova

	```
	// Habilitar registros permanentes
	BMSLogger.storeLogs(true);
	// Establecer el nivel mínimo de registro que se debe imprimir y ser permanente
	BMSLogger.setLogLevel(BMSLogger.INFO);
	var logger1 = BMSLogger.getLogger("logger1");
	var logger2 = BMSLogger.getLogger("logger2");   
	// Registrar mensajes con distintos niveles
	logger1.debug ("debug message");
	logger2.info ("info message");
	// Enviar registros permanentes al servicio {{site.data.keyword.mobileanalytics_short}}
	BMSLogger.send();
	BMSAnalytics.send();
	```
	{: codeblock}

- Web

	```
	// Habilitar registros permanentes
	BMSAnalytics.Logger.storeLogs(true);
	// Establecer el nivel mínimo de registro que se debe imprimir y ser permanente   
	// niveles de registro en nivel de detalle descendente trace,debug,log,info,warn,error,fatal,analytics  
	BMSAnalytics.Logger.setLogLevel('error');
	// Registrar mensajes con distintos niveles
	BMSAnalytics.Logger.debug ("debug message");
	BMSAnalytics.Logger.info ("info message");
	// Enviar registros permanentes al servicio {{site.data.keyword.mobileanalytics_short}}
	BMSAnalytics.Logger.send();
	BMSAnalytics.send().then(function(result) {
		//Gestionar aquí el resultado correcto
        }, function(err) {
         	//Gestionar aquí el resultado erróneo
	 });;
	```
	{: codeblock}

<!--## Enabling the {{site.data.keyword.mobileanalytics_short}} Client SDK internal logs
{: #enable-logger-sdklogs notoc}

The {{site.data.keyword.mobileanalytics_short}} Client SDK provides a better development experience by not unnecessarily increasing the console output with its internal debug messages. Therefore, by default, internal log messages that are produced by the {{site.data.keyword.mobileanalytics_short}} SDK with the DEBUG level are not printed. You can enable printing of all internal log messages of the {{site.data.keyword.mobileanalytics_short}} Client SDK with the following API:

- Android
	```
	Logger.setSDKDebugLoggingEnabled(true);
	```
	{: codeblock}

- iOS - Swift
	```
	Logger.sdkDebugLoggingEnabled = true
	```
	{: codeblock}
-->

## Registro de datos de ubicación 
{: #location-logging}

La ubicación del dispositivo móvil se puede registrar desde la app mediante esta api suministrada.
```
Analytics.logLocation();
 
``` 
Esta api permite a la app para enviar su ubicación como latitud y longitud al servidor entre appsession. Además de estas llamadas explícitas a la api location-logging, el sdk envía la ubicación de dispositivo para cada sesión de la app, tanto para el contexto inicial de AppSession como para el contexto de conmutación de usuario de AppSession (es decir, cuando se cambia de usuario en una sesión de la app). La api de ubicación debe estar habilitada en la inicialización de sdk, tal como se ha mencionado anteriormente.

**Nota:** Para llamar a esta api de registro de ubicación, establezca el parámetro `collectLocation` en true en la inicialización del sdk tal como se muestra a continuación.
```
Analytics.initialize(appName, apiKey,  hasUserContext, collectLocation, [BMSAnalytics.ALL])
		
```





## Cómo realizar una solicitud de red
{: #network-requests}

Puede configurar el SDK de cliente de {{site.data.keyword.mobileanalytics_short}} para [realizar una solicitud de red](/docs/mobile/sdk_network_request.html). Asegúrese de haber inicializado `BMSClient` y `BMSAnalytics` y de haber importado los SDK de cliente.

<!--
#### Android
{: #android-network-requests notoc}

**Note:** This code snippet assumes that you have [imported the Client SDKs](#android-import).

```
public void makeGetCall(){
    Thread thread = new Thread(new Runnable() {
        @Override
        public void run() {
            try  {
                Request request = new Request("http://httpbin.org/get", "GET");
                    request.send(null, null);
            } catch (Exception e) {
                // Handle failure here.
            }
        }
    });
    thread.start();
}
```
	{: codeblock}

-->

<!-- 
#### Swift 3.0
{: #ios-network-requests notoc}

 ```Swift
 	// Make a network request
	let customResourceURL = "<your resource URL>"
	let request = Request(url: customResourceURL, method: HttpMethod.GET)

	let callBack:BMSCompletionHandler = {(response: Response?, error: Error?) in
   	if error == nil {
       	    print ("response:\(response?.responseText), no error")
    	  } else {
       	    print ("error: \(error)")
    	}
	}
	request.send(completionHandler: callBack)
 ```
	{: codeblock}
 
 -->

<!-- Commenting out bmsurlsession
```
// Make a network request
let urlSession = BMSURLSession(configuration: .default, delegate: nil, delegateQueue: nil)
var request = URLRequest(url: URL(string: "http://httpbin.org/get")!)
request.httpMethod = "GET"
request.allHTTPHeaderFields = ["foo":"bar"]

urlSession.dataTask(with: request) { (data: Data?, response: URLResponse?, error: Error?) in
    if let httpResponse = response as? HTTPURLResponse {
        logger.info(message: "Status code: \(httpResponse.statusCode)")
    }
    if data != nil, let responseString = String(data: data!, encoding: .utf8) {
        logger.info(message: "Response data: \(responseString)")
    }
    if let error = error {
        logger.error(message: "Error: \(error)")
    }
}.resume()
```
	{: codeblock}
-->

<!--
#### Swift 2.2
{: ios-swift22-network-requests}

```Swift
 	// Make a network request
	let customResourceURL = "<your resource URL>"
	let request = Request(url: customResourceURL, method: HttpMethod.GET)

	let callBack:BMSCompletionHandler = {(response: Response?, error: NSError?) in
   	if error == nil {
       	    print ("response:\(response?.responseText), no error")
    	  } else {
       	    print ("error: \(error)")
    	}
	}
	request.send(completionHandler: callBack)
 ```
	{: codeblock}
-->
<!--
```
// Make a network request
let urlSession = BMSURLSession(configuration: .defaultSessionConfiguration(), delegate: nil, delegateQueue: nil)
let request = NSMutableURLRequest(URL: NSURL(string: "http://httpbin.org/get")!)
request.HTTPMethod = "GET"
request.allHTTPHeaderFields = ["foo":"bar"]

urlSession.dataTaskWithRequest(request) { (data: NSData?, response: NSURLResponse?, error: NSError?) in
    if let httpResponse = response as? NSHTTPURLResponse {
        logger.info(message: "Status code: \(httpResponse.statusCode)")
    }
    if data != nil, let responseString = NSString(data: data!, encoding: NSUTF8StringEncoding) {
        logger.info(message: "Response data: \(responseString)")
    }
    if let error = error {
        logger.error(message: "Error: \(error)")
    }
}.resume()
```
	{: codeblock}
-->
<!--
#### Cordova
{: #cordova-network-requests notoc}

```
var success = function(data){
     console.log("success", data);
 }
 var failure = function(error)
     {console.log("failure", error);
 }
 var request = new BMSRequest("<your application route>", BMSRequest.GET);
 request.send(success, failure);
```
	{: codeblock}

-->


## Notificar analíticas de bloqueo
{: #report-crash-analytics}

Puede ver [datos de bloqueo de aplicación](app-monitoring.html#monitor-app-crash) enviando información de analíticas y de registro a {{site.data.keyword.mobileanalytics_short}}.

El método `Analytics.send()` rellena las tablas **Visión general de bloqueos** y **Bloqueos** en la página **Bloqueos**. Los gráficos de esta sección se habilitan utilizando el proceso de inicialización y de envío para su análisis; no es necesaria ninguna configuración especial.

El método `Logger.send()` rellena las tablas **Resumen de bloqueos** y **Detalles de bloqueo** en la página **Resolución de problemas**. Debe habilitar la aplicación para almacenar y enviar registros para rellenar los gráficos de esta sección, añadiendo una sentencia adicional en el código de la aplicación:


- Android

	`Logger.storeLogs(true);`
	<!-- * `Logger.setLogLevel(Logger.LEVEL.FATAL); // or greater` -->
	
	Consulte el [ejemplo de uso del registrador](sdk.html##sample-logger-usage) de Android.


- iOS

	`Logger.isLogStorageEnabled = true`
	<!-- * `Logger.logLevelFilter = LogLevel.Fatal // or greater` -->
	
	Consulte el [ejemplo de uso del registrador](sdk.html##sample-logger-usage) de iOS.


- Cordova

	 `BMSLogger.storeLogs(true);`
	<!-- * `Logger.logLevelFilter = LogLevel.Fatal // or greater` -->

	Consulte el [ejemplo de uso del registrador](sdk.html##sample-logger-usage) de Cordova.

- Web

	`BMSAnalytics.Logger.storeLogs(true);`

## Seguimiento de usuarios activos
{: #trackingusers}

Si la aplicación reconoce usuarios exclusivos en un dispositivo, puede realizar un seguimiento del número de usuarios que están utilizando de forma activa la aplicación; para ello pase el nombre del usuario a {{site.data.keyword.mobileanalytics_short}}. 

Habilite el seguimiento de usuarios inicializando {{site.data.keyword.mobileanalytics_short}} con `hasUserContext=true`. De lo contrario, {{site.data.keyword.mobileanalytics_short}} solamente captura un usuario por dispositivo. 


- Android

	Añada el siguiente código para rastrear cuando el usuario inicie la sesión:
	
	```
	Analytics.setUserIdentity("username");
	```
	{: codeblock}
	
	<!--Add the following code for when the user logs out:
	
	```
	Analytics.clearUserIdentity();
	```
	{: codeblock}
	-->

- iOS (Swift)

	Añada el siguiente código para rastrear cuando el usuario inicie la sesión:
	
	```
	Analytics.userIdentity = "username"
	```
	{: codeblock}
	
	<!--
	Add the following code for when the user logs out:
	
	```
	Analytics.userIdentity = nil
	```
	{: codeblock}
	-->


- Cordova
	
	Añada el siguiente código para rastrear cuando el usuario inicie la sesión:
	
	```
	BMSAnalytics.setUserIdentity("username");
	```
	{: codeblock}

- Web

	Añada el siguiente código para rastrear cuando el usuario inicie la sesión:
	
	```
	BMSAnalytics.setUserIdentity("username");
	```
	{: codeblock}

## Análisis de comentarios integrados en la app
{: #In-App}

El análisis de comentarios integrados en la app permite que **users and testers** proporcionen comentarios importantes a los propietarios de las apps. Los **propietarios de las apps** reciben comentarios en tiempo real de sus usuarios sobre el uso de la app. Los **desarrolladores** implementan cambios en función de los detalles obtenidos en tiempo real.

Invoque la siguiente API para preparar la app para móviles para que entre en modalidad de comentarios. 

- Android

    ```
    ImageButton feedback =(ImageButton)findViewById(R.id.Feedback);
        feedback.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Analytics.triggerFeedbackMode();
            }
        });
    ```	
	{: codeblock}
	
<!--## Configuring MobileFirst Platform Foundation servers to use the {{site.data.keyword.mobileanalytics_short}} service (optional)
{: #configmfp notoc}
  If you are using MobileFirst Platform Foundation Server V7 and higher, you can configure it to use the {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.mobileanalytics_short}} service to store analytics and logged data. 
  
  Configure MobileFirst Platform V7.0, V7.1, and V8.0 Beta servers to send analytics data to the {{site.data.keyword.mobileanalytics_short}} service on {{site.data.keyword.Bluemix_notm}}.

  1. Visit the dashboard for the {{site.data.keyword.mobileanalytics_short}} service where you want to send analytics data and note the browser URL for the dashboard.
  2. Determine the value for reporting analytics, as follows:
  	1. Get the {{site.data.keyword.mobileanalytics_short}} service route from the dashboard URL. The {{site.data.keyword.mobileanalytics_short}} service route is the part of the URL before ``/analytics/console/dashboard``.  

  		For example, if the dashboard URL is: `http://mobile-analytics-dashboard.ng.bluemix.net/analytics/console/dashboard?instanceId=12345abcde`
      {: screen}

  		then the Analytics Service Route is
      `http://mobile-analytics-dashboard.ng.bluemix.net`
      {: screen}

  	2. Get the [Client API Key](#analytics-clientkey) value from the Analytics dashboard.

  	You will use the {{site.data.keyword.mobileanalytics_short}} service route and API Key to construct a URL to report analytics data, depending on the version of your MobileFirst Platform server. -->

<!--  3. Copy the URL for your {{site.data.keyword.mobileanalytics_short}} service dashboard. Include the `instanceId` query parameter, for example:
      `http://mobile-analytics-dashboard.ng.bluemix.net/analytics/console/dashboard?instanceId=1212345abcde`
      {: screen}

  4. Configure the values for the MobileFirst Platform server JNDI properties, as follows:-->

<!--    ### MobileFirst Platform V7.0
    {: #mfp70 notoc}

        The format of the `wl.analytics.url` JNDI property is: `<Analytics Service Route>/analytics-service/rest/data?tenant=<Client API Key>`
        {: screen}

        The `wl.analytics.console.url` JNDI property is the Analytics service dashboard URL.

        #### Example of MobileFirst Platform V7.0 JNDI property values
        {: #example-mfp70-jndi-values notoc}

        For a MobileFirst Platform project named `Myproj7000`, based on the examples in steps 2 and 3, replace the current JNDI property values in the `server.xml` file with:
        ```
        <jndiEntry jndiName="MyProj7000/wl.analytics.url" value='"http://mobile-analytics-dashboard.ng.bluemix.net/analytics-service/rest/data?tenant=12345abcde"'/>
        ```
        {: screen}
        ```
        <jndiEntry jndiName="MyProj7000/wl.analytics.console.url" value='"http://mobile-analytics-dashboard.ng.bluemix.net/analytics/console/dashboard?instanceId=12345abcde"'/>
        ```
        {: screen}

    ### MobileFirst Platform V7.1
    {: #mfp71 notoc}

      The format of the `wl.analytics.url` JNDI property is: `<Analytics Service Route>/analytics-service/rest/v2/<Client API Key>`
      {: screen}

      #### Example of MobileFirst Platform JNDI V7.1 property values
      {: #example-mfp71-jndi-values notoc}

      For a MobileFirst Platform project named `MyProj7101`, replace the current JNDI property values in the `server.xml` file with:
      ```
      <jndiEntry jndiName="MyProj7101/wl.analytics.url" value='"http://mobile-analytics-dashboard.ng.bluemix.net/analytics-service/rest/v2/data?tenant=12345abcde"'/>
      ```
      {: screen}
      ```
      <jndiEntry jndiName="MyProj7101/wl.analytics.console.url" value='"http://mobile-analytics-dashboard.ng.bluemix.net/analytics/console/dashboard?instanceId=12345abcde"'/>
      ```
      {: screen}

      ### MobileFirst Platform V8.0
      {: #mfp80 notoc}

      The format of the `mfp.analytics.url` JNDI property is:
      `<Analytics Service Route>/analytics-service/rest/v2/<Client API Key>`  

    #### Example MobileFirst Platform V8.0 Beta JNDI property values
      {: example-mfp80b-jndi-values}

      For a MobileFirst Platform project named `mfp`, which is the default, replace the current JNDI property values in the `server.xml` file with:
      ```
      <jndiEntry jndiName="mfp/mfp.analytics.url" value='"http://mobile-analytics-dashboard.ng.bluemix.net/analytics-service/rest/data?tenant=12345abcde"'/>
      ```
      {: screen}
      ```
      <jndiEntry jndiName="mfp/mfp.analytics.console.url" value='"http://mobile-analytics-dashboard.ng.bluemix.net/analytics/console/dashboard?instanceId=12345abcde"'/>
      ```
      {: screen}
-->
<!-- #### Ignored events and event retention
{: #ignored-events notoc}
The {{site.data.keyword.mobileanalytics_short}} service saves the following data for ignored events and event retention:
  
<dl>	
<dt>Ignored events</dt>
	<dd>`ANALYTICS_SDK_CFG_IGNORE_AppPushAction: true`
		  `ANALYTICS_SDK_CFG_IGNORE_ServerLog: true`
		  `ANALYTICS_SDK_CFG_IGNORE_NetworkTransaction: true`
		  `ANALYTICS_SDK_CFG_IGNORE_NetworkTransactionSummarizedHourly: true`
		  `ANALYTICS_SDK_CFG_IGNORE_PushNotification: true`
		  `ANALYTICS_SDK_CFG_IGNORE_PushSubscription: true`</dd>
</dt>
<dt>Event retention</dd>
<dd>
`ANALYTICS_TTL_AlertNotification: 14d`<br>
`ANALYTICS_TTL_CustomData: 7d`<br>
`ANALYTICS_TTL_Device: 90d`<br>
`ANALYTICS_TTL_AppLog: 3d`<br>
`ANALYTICS_TTL_AppSession: 7d`
</dd>
</dt>
</dl>
  
-->


## Qué hacer a continuación
{: #what-to-do-next notoc}

Ahora puede ir a la consola de {{site.data.keyword.mobileanalytics_short}} para ver analíticas de uso, como dispositivos nuevos y total de dispositivos que utilizan su aplicación. También puede supervisar la aplicación <!--[creating custom charts](app-monitoring.html#custom-charts),-->[definiendo alertas](app-monitoring.html#alerts) y [supervisando bloqueos de la app](app-monitoring.html#monitor-app-crash).


# Enlaces relacionados
{: #rellinks notoc}

## Referencia de API
{: #api notoc}

* [API REST ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://mobile-analytics-dashboard.{DomainName}/analytics-service/){:new_window}
