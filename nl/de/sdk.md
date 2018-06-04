---

copyright:
  years: 2015, 2017
lastupdated: "2018-01-18"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Anwendung instrumentieren
{: #mobileanalytics_sdk}

## Anwendung zur Verwendung mit den {{site.data.keyword.mobileanalytics_short}}-Client-SDKs instrumentieren

Mit den {{site.data.keyword.mobileanalytics_full}}-SDKs können Sie die mobile Anwendung instrumentieren.
{: shortdesc}

{{site.data.keyword.mobileanalytics_short}} ermöglicht das Erfassen der folgenden Datenkategorien, von denen jede einen unterschiedlichen Umfang an Instrumentierung erfordert:


- Vordefinierte Daten - Diese Kategorie umfasst Informationen zur allgemeinen Nutzung und zum Gerät, die auf alle Anwendungen zutreffen. Diese Kategorie setzt sich aus Gerätemetadaten (Betriebssystem und Gerätemodell) und Nutzungsdaten (aktive Benutzer und Anwendungssitzungen) zusammen, aus denen das Volumen, die Häufigkeit oder die Dauer der Anwendungsnutzung hervorgehen. Vordefinierte Daten werden nach der Initialisierung des {{site.data.keyword.mobileanalytics_short}}-SDKs in Ihrer Anwendung automatisch erfasst.

- Anwendungsprotokollnachrichten - Diese Kategorie ermöglicht dem Entwickler das Hinzufügen von Codezeilen in der ganzen Anwendung, die zur Erleichterung der Entwicklung und Fehlerbehebung benutzerdefinierte Nachrichten protokollieren. Der Entwickler weist jeder Protokollnachricht eine Ebene für den Schweregrad bzw. die Ausführlichkeit zu und kann die Nachrichten danach anhand der zugewiesenen Ebene filtern; alternativ kann er die Anwendung so konfigurieren, dass Nachrichten auf einer niedrigeren Ebene einer bestimmten Protokollebene ignoriert werden, um Speicherplatz zu sparen. Wenn Sie Anwendungsprotokolldaten erfassen möchten, müssen Sie das {{site.data.keyword.mobileanalytics_short}}-SDK innerhalb Ihrer Anwendung initialisieren und für jede Protokollnachricht eine Codezeile hinzufügen.

- Angepasste Ereignisse - Diese Kategorie umfasst Daten, die Sie selbst definieren und die für Ihre App spezifisch sind. Diese Daten stellen Ereignisse in Ihrer App dar, z. B. Seitenansichten, Schaltflächenantipper oder App-interne Käufe. Zusätzlich zur Initialisierung des {{site.data.keyword.mobileanalytics_short}}-SDK in Ihrer App müssen Sie für jedes angepasste Ereignis, das Sie verfolgen möchten, eine Codezeile hinzufügen. 

Derzeit sind SDKs für Android, iOS, WatchOS, Cordova und Web verfügbar.

## API-Schlüsselwert für Serviceberechtigungsnachweise angeben
{: #analytics-clientkey}

Geben Sie Ihren **API-Schlüsselwert** an, bevor Sie das Client-SDK konfigurieren. Der API-Schlüssel ist für die Initialisierung des Client-SDK erforderlich.

1. Öffnen Sie das Dashboard für den {{site.data.keyword.mobileanalytics_short}}-Service.
1. Erweitern Sie **Berechtigungsnachweise anzeigen**, um Ihren API-Schlüsselwert sichtbar zu machen. Den API-Schlüsselwert benötigen Sie für die Initialisierung des {{site.data.keyword.mobileanalytics_short}}-Client-SDK.


## Anwendung zum Erfassen von Analysedaten initialisieren
{: #initalize-ma-sdk}

Initialisieren Sie die Anwendung, damit Protokolle an den {{site.data.keyword.mobileanalytics_short}}-Service gesendet werden können.

1. Importieren Sie das Client-SDK.
	- Android
	
		Fügen Sie die folgenden `import`-Anweisungen am Anfang Ihrer Projektdatei ein:
		
		```
		import com.ibm.mobilefirstplatform.clientsdk.android.core.api.*;
import com.ibm.mobilefirstplatform.clientsdk.android.analytics.api.*;
import com.ibm.mobilefirstplatform.clientsdk.android.logger.api.*;
		```
		{: codeblock}
  
	- iOS
		
		Das Swift-SDK ist für iOS und WatchOS verfügbar.	Importieren Sie die Frameworks `BMSCore` und `BMSAnalytics` durch Hinzufügen der folgenden `import`-Anweisungen am Anfang der Projektdatei `AppDelegate.swift`:
	
		```Swift
		import BMSCore
		import BMSAnalytics
		```
		{: codeblock}  
   
	- Cordova
			
		Fügen Sie das Cordova-Plug-in hinzu, indem Sie den folgenden Befehl im Stammverzeichnis der Cordova-Anwendung ausführen:
	
		```Javascript
		cordova plugin add bms-core
		```
		{: codeblock}  

	- Web
			
		Fügen Sie das Web-Plug-in hinzu, indem Sie entweder das als Script bereitgestellte SDK zur Datei 'index.html' hinzufügen:
	
		```Html
		<script src="/path/to/bms-clientsdk-web-analytics/bmsanalytics.js"></script>
		```
		{: codeblock} 	 	

	 	Oder indem Sie das Web-Plug-in mithilfe des Modul-Loaders RequireJS hinzufügen: 
	
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

2. Initialisieren Sie das {{site.data.keyword.mobileanalytics_short}}-Client-SDK in Ihrer Anwendung.

	- Android
	
		Initialisieren Sie das {{site.data.keyword.mobileanalytics_short}}-Client-SDK in Ihrer Android-Anwendung durch Hinzufügen des Initialisierungscodes in der Methode 'onCreate' der Hauptaktivität in Ihrer Android-Anwendung oder an einer Position, die für Ihr Projekt am besten geeignet ist.
	
		```Java
		BMSClient.getInstance().initialize(getApplicationContext(), BMSClient.REGION_US_SOUTH); // Sicherstellen, dass auf eigene Region verwiesen wird
		```
		{: codeblock}
	
		Sie müssen 'BMSClient' mit dem Parameter **bluemixRegion** initialisieren. Im Initialisierungsoperator gibt der Wert **bluemixRegion** an, welche {{site.data.keyword.Bluemix_notm}}-Bereitstellung Sie verwenden, z. B. 'BMSClient.REGION_US_SOUTH' und 'BMSClient.REGION_UK'.
	    <!-- oder 'BMSClient.REGION_SYDNEY'.-->

	- iOS
	
		Initialisieren Sie zuerst mithilfe des nachfolgenden Codes die Klasse 'BMSClient'. Ordnen Sie den Initialisierungscode in der Methode 'application(_:didFinishLaunchingWithOptions:)' Ihres Anwendungsdelegierten oder an einer Position an, die sich für Ihr Projekt am besten eignet.
		
		```Swift
		BMSClient.sharedInstance.initialize(bluemixRegion: BMSClient.Region.usSouth) // Sicherstellen, dass auf eigene Region verwiesen wird
		```
		{: codeblock}
	
		Sie müssen 'BMSClient' mit dem Parameter **bluemixRegion** initialisieren. Im Initialisierungsoperator gibt der Wert **bluemixRegion** an, welche {{site.data.keyword.Bluemix_notm}}-Bereitstellung Sie verwenden, z. B. 'BMSClient.Region.usSouth' oder 'BMSClient.Region.unitedKingdom'.
	    <!-- oder 'BMSClient.Region.Sydney'. -->

	- Cordova
	
		Initialisieren Sie **BMSClient** und **BMSAnalytics**. Dazu benötigen Sie Ihren [**API-Schlüsselwert**](#analytics-clientkey).
	
		```Javascript
		BMSClient.initialize(BMSClient.REGION_US_SOUTH); //Sicherstellen, dass auf eigene Region verwiesen wird	
		```
		{: codeblock}
	
		Zum Verwenden des {{site.data.keyword.mobileanalytics_short}}-Client-SDK müssen Sie 'BMSClient' mit dem Parameter **bluemixRegion** initialisieren. Im Initialisierungsoperator gibt der Wert **bluemixRegion** an, welche {{site.data.keyword.Bluemix_notm}}-Bereitstellung Sie verwenden, z. B. 'BMSClient.REGION_US_SOUTH' oder 'BMSClient.REGION_UK'.
	    <!-- oder 'BMSClient.REGION_SYDNEY'. -->

	- Web

	    Initialisieren Sie das Client-SDK im Anwendungscode, um Nutzungsanalysedaten und Anwendungssitzungen aufzuzeichnen. Verwenden Sie hierzu Ihren API-Schlüsselwert.
	    ```javascript
	    BMSAnalytics.Client.initialize(BMSAnalytics.Client.REGION_US_SOUTH);
	    ```
	    {: codeblock}
	
		Zum Verwenden des {{site.data.keyword.mobileanalytics_short}}-Client-SDK müssen Sie 'BMSAnalytics.Client' mit dem Parameter **bluemixRegion** initialisieren. Im Initialisierungsoperator gibt der Wert **bluemixRegion** an, welche {{site.data.keyword.Bluemix_notm}}-Bereitstellung Sie verwenden, z. B. 'BMSAnalytics.Client..REGION_UK' oder 'BMSAnalytics.Client..REGION_US_SOUTH'.
	    <!-- oder 'BMSClient.REGION_SYDNEY'. -->

3. Initialisieren Sie Analytics mithilfe des Anwendungsobjekts und legen Sie dafür den Namen der Anwendung fest.

	Der Name, den Sie für Ihre Anwendung auswählen ('your_app_name_here'), wird in der {{site.data.keyword.mobileanalytics_short}}-Konsole als Anwendungsname angezeigt. Der Anwendungsname wird als Filter für die Suche nach Anwendungsprotokollen im Dashboard verwendet. Wenn Sie plattformübergreifend (zum Beispiel für Android und iOS) denselben Anwendungsnamen verwenden, können Sie unter einem Namen unabhängig von der Plattform, von der die Protokolle stammen, alle Protokolle zu dieser Anwendung anzeigen.

	Außerdem benötigen Sie den [API-Schlüsselwert](#analytics-clientkey).

- Android
		
	```Java
		// In diesem Codebeispiel ist Analytics für die Aufzeichnung von Lebenszyklusereignissen konfiguriert.
		Analytics.init(getApplication(), "your_app_name_here", apiKey, hasUserContext, collectLocation, Analytics.DeviceEvent.ALL);
	```
    {: codeblock}
		
	*Hinweis:** Setzen Sie den Wert für 'hasUserContext' auf **true** oder **false**. Bei 'false' (Standardwert) wird jedes Gerät als aktiver Benutzer gezählt. Die Methode [`Analytics.setUserIdentity("username")`](sdk.html#android-tracking-users), mit der Sie die Anzahl der Benutzer pro Gerät verfolgen können, die Ihre Anwendung aktiv nutzen, funktioniert nicht, wenn der Wert für 'hasUserContext' 'false' ist. Bei 'true' wird jede Verwendung von [`Analytics.setUserIdentity("username")`](sdk.html#android-tracking-users) als ein aktiver Benutzer gezählt. Wenn 'hasUserContext' auf 'true' gesetzt ist, gibt es keine Standardbenutzer-ID. Daher muss diese festgelegt werden, damit die Diagramme für aktive Benutzer gefüllt werden. Die Methode 'Analytics.logLocation()', die die App dafür aktiviert, die Geräteposition zu senden, funktioniert, wenn 'collectLocation' auf 'true' gesetzt ist.
		
		
	
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
	 	
    Mit dem optionalen Parameter 'deviceEvents' können automatisch Analysedaten für gerätespezifische Ereignisse erfasst werden.
		
    Setzen Sie den Wert für 'hasUserContext' auf **true** oder **false**. Bei 'false' (Standardwert) wird jedes Gerät als aktiver Benutzer gezählt. Die Methode [`Analytics.userIdentity = "username"`](sdk.html#ios-tracking-users), mit der Sie die Anzahl der Benutzer pro Gerät verfolgen können, die Ihre Anwendung aktiv nutzen, funktioniert nicht, wenn der Wert für 'hasUserContext' 'false' ist. Wenn 'hasUserContext' auf 'true' gesetzt ist, wird jede Verwendung von [`Analytics.userIdentity = "username"`](sdk.html#ios-tracking-users) als ein aktiver Benutzer gezählt. Wenn 'hasUserContext' auf 'true' gesetzt ist, gibt es keine Standardbenutzer-ID. Daher muss diese festgelegt werden, damit die Diagramme für aktive Benutzer gefüllt werden. Die Methode 'Analytics.logLocation()', die die App dafür aktiviert, die Geräteposition zu senden, funktioniert, wenn 'collectLocation' auf 'true' gesetzt ist.

- watchOS
	
    Unter WatchOS können Sie Geräteereignisse mit den Methoden 'Analytics.recordApplicationDidBecomeActive()' und 'Analytics.recordApplicationWillResignActive() aufzeichnen.
	
    Fügen Sie die folgende Zeile zur Methode 'applicationDidBecomeActive()' der Klasse 'ExtensionDelegate' hinzu:
	
	```Javascript
		Analytics.recordApplicationDidBecomeActive()
	```
    {: codeblock}
	
    Fügen Sie die folgende Zeile zur Methode 'applicationWillResignActive()' der Klasse 'ExtensionDelegate' hinzu:
	
	```Javascript
		Analytics.recordApplicationWillResignActive()
	```
    {: codeblock}	
		
- Cordova
		
	```Javascript
	Analytics.initialize(appName, apiKey,  hasUserContext, collectLocation, [BMSAnalytics.ALL])
	```
    {: codeblock}	
		
    Setzen Sie den Wert für 'hasUserContext' auf **true** oder **false**. Bei 'false' (Standardwert) wird jedes Gerät als aktiver Benutzer gezählt. Die Methode 'Analytics.setUserIdentity("username")', mit der Sie die Anzahl der Benutzer pro Gerät verfolgen können, die Ihre Anwendung aktiv nutzen, funktioniert nicht, wenn der Wert für 'hasUserContext' 'false' ist. Bei 'true' wird jede Verwendung von 'Analytics.setUserIdentity("username")'(sdk.html#android-tracking-users) als ein aktiver Benutzer gezählt. Wenn 'hasUserContext' auf 'true' gesetzt ist, gibt es keine Standardbenutzer-ID. Daher muss diese festgelegt werden, damit die Diagramme für aktive Benutzer gefüllt werden. Die Methode 'Analytics.logLocation()', die die App dafür aktiviert, die Geräteposition zu senden, funktioniert, wenn 'collectLocation' auf 'true' gesetzt ist.

- Web
		
	```Java		
		// In diesem Codebeispiel ist Analytics für die Aufzeichnung von 'allevents' konfiguriert.
		BMSAnalytics.initialize(appName, apiKey, hasUserContext, BMSAnalytics.DeviceEvent.ALL);
	```
    {: codeblock}
		
    Setzen Sie den Wert für 'hasUserContext' auf **true** oder **false**. Bei 'false' (Standardwert) wird jedes Gerät als aktiver Benutzer gezählt. Die Methode [`BMSAnalytics.setUserIdentity("username")`](sdk.html#web-tracking-users), mit der Sie die Anzahl der Benutzer pro Gerät verfolgen können, die Ihre Anwendung aktiv nutzen, funktioniert nicht, wenn der Wert für 'hasUserContext' 'false' ist. Bei 'true' wird jede Verwendung von [`BMSAnalytics.setUserIdentity("username")`](sdk.html#web-tracking-users) als ein aktiver Benutzer gezählt. Wenn 'hasUserContext' auf 'true' gesetzt ist, gibt es keine Standardbenutzer-ID. Daher muss diese festgelegt werden, damit die Diagramme für aktive Benutzer gefüllt werden.	

4. Sie haben die Anwendung nun für die Erfassung von Analysedaten initialisiert. Als nächstes können Sie an den {{site.data.keyword.mobileanalytics_short}}-Service [Analysedaten senden](sdk.html#app-monitoring-gathering-analytics).


## Nutzungsanalysedaten sammeln
{: #app-monitoring-gathering-analytics}

Sie können das {{site.data.keyword.mobileanalytics_short}}-Client-SDK für die Aufzeichnung von Nutzungsanalysedaten und zum Senden der aufgezeichneten Daten an den {{site.data.keyword.mobileanalytics_short}}-Service konfigurieren.

Verwenden Sie die folgende API zum Starten einer Aufzeichnung und zum Senden der Nutzungsanalysedaten:

- Android
	
	```
	// Aufzeichnung der Nutzungsanalysedaten inaktivieren (z. B. zum Sparen von Speicherplatz)
	// Aufzeichnung ist standardmäßig aktiviert
	Analytics.disable();
	// Aufzeichnung von Nutzungsanalysedaten aktivieren
	Analytics.enable();
	// Aufgezeichnete Nutzungsanalysedaten an den Mobile Analytics-Service senden
	Analytics.send(new ResponseListener() {
	            @Override
                    public void onSuccess(Response response) {
	                // Sendeerfolg für Analytics hier bearbeiten.
    }
	            @Override
                    public void onFailure(Response response, Throwable throwable, JSONObject jsonObject) {
	                // Sendefehler für Analytics hier bearbeiten.
            }
	        });
	```
	{: codeblock}
		
	Beispiel für Nutzungsanalyse zur Protokollierung eines Ereignisses:
		
	```
	// Angepasstes Analyseereignis protokollieren
	JSONObject eventJSONObject = new JSONObject();
	eventJSONObject.put("customProperty" , "propertyValue");
	Analytics.log(eventJSONObject);
	```
	{: codeblock}


- iOS (Swift)

	```
	// Aufzeichnung der Nutzungsanalysedaten inaktivieren (z. B. zum Sparen von Speicherplatz)
	// Aufzeichnung ist standardmäßig aktiviert
	Analytics.isEnabled = false
	// Aufzeichnung von Nutzungsanalysedaten aktivieren
	Analytics.isEnabled = true
	// Aufgezeichnete Nutzungsanalysedaten an den Mobile Analytics-Service senden
	Analytics.send(completionHandler: { (response: Response?, error: Error?) in
	    if let response = response {
	        // Sendeerfolg für Analytics hier bearbeiten.
    }
	    if let error = error {
	        // Sendefehler für Analytics hier bearbeiten.
            }
	})
	```
	{: codeblock}
	
	Beispiel für Nutzungsanalyse zur Protokollierung eines Ereignisses:
	
	```Swift
	// Angepasstes Analyseereignis protokollieren
	let eventObject = ["customProperty": "propertyValue"]
	Analytics.log(metadata: eventObject)
	```
	{: codeblock}

- Cordova

	```JavaScript
	// Aufzeichnung von Nutzungsanalysedaten aktivieren
	BMSAnalytics.enable();
	// Aufzeichnung von Nutzungsanalysedaten inaktivieren
	BMSAnalytics.disable();
	// Aufgezeichnete Nutzungsanalysedaten an den {{site.data.keyword.mobileanalytics_short}}-Service senden
	BMSAnalytics.send(
		function(response) {
			console.log('success: ' + response);
		},
	function (err) {
			console.log('fail: ' + err);
		});
	```
	{: codeblock}
	
	Beispiel für Nutzungsanalyse zur Protokollierung eines Ereignisses:
	
	```JavaScript
	// Angepasstes Analyseereignis protokollieren
	var eventObject = {"customProperty": "propertyValue"}
	BMSAnalytics.log(eventObject)
	```
	{: codeblock}

	Verwenden Sie bei der Entwicklung von Cordova-Anwendungen die native API zum Aktivieren der Aufzeichnung von Anwendungslebenszyklusereignissen.

- Web
		
	```
	// Aufzeichnung der Nutzungsanalysedaten inaktivieren (z. B. zum Sparen von Speicherplatz)
	// Aufzeichnung ist standardmäßig aktiviert
	BMSAnalytics.disable();
	// Aufzeichnung von Nutzungsanalysedaten aktivieren
	BMSAnalytics.enable();
	// Aufgezeichnete Nutzungsanalysedaten an den Mobile Analytics-Service senden
	BMSAnalytics.send().then(function(result) {
         	//Erfolg hier behandeln
        }, function(err) {
                //Fehler hier behandeln
        });;
	```
	{: codeblock}
		
	Beispiel für Nutzungsanalyse zur Protokollierung eines Ereignisses:
		
	```JavaScript
	// Angepasstes Analyseereignis protokollieren
	var eventObject = {"customProperty": "propertyValue"}
	BMSAnalytics.log(eventObject)
	```
	{: codeblock}

## Protokollfunktion aktivieren, konfigurieren und verwenden

Vom {{site.data.keyword.mobileanalytics_full}}-Client-SDK wird ein Protokollierungsframework bereitgestellt, das anderen Protokollierungsframeworks ähnelt, mit denen Sie unter Umständen vertraut sind, zum Beispiel 'java.util.logging' oder 'log4j'. Vom Protokollierungsframework werden mehrere paketweise arbeitende Protokollfunktionen, unterschiedliche Protokollebenen, die Erfassung von Stack-Traces für einen Anwendungsabsturz, etc bereitgestellt.

Sie können auch konfigurieren, dass die protokollierten Daten auf dem Gerät gespeichert werden sollen, auf dem die Anwendung ausgeführt wird und dass diese Geräteprotokolle zu einem späteren Zeitpunkt an den {{site.data.keyword.mobileanalytics_short}}-Service gesendet werden sollen.

<!-- Die Initialisierung muss erfolgt sein, bevor Protokolle gesammelt und an den {{site.data.keyword.mobileanalytics_short}}-Service gesendet werden können. -->

Vom Protokollierungsframework des {{site.data.keyword.mobileanalytics_short}}-Client-SDK werden die folgenden Protokollebenen (aufgelistet von der am wenigsten ausführlichen bis zur ausführlichsten Ebene) unterstützt, für die die nachfolgenden Verwendungsrichtlinien empfohlen werden:

  * `FATAL` - Für nicht behebbare Abstürze oder Blockierungen. Die Ebene 'FATAL' ist für die Protokollierung nicht behebbarer Fehler, die Benutzern als Anwendungsabstürze angezeigt werden, reserviert
  * `ERROR` - Für unerwartete Ausnahmen oder unerwartete Netzprotokollfehler
  * `WARN` - Zur Protokollierung von Nutzungswarnungen, die nicht als kritische Fehler gelten, z. B. die Verwendung veralteter APIs oder eine langsame Netzantwort
  * `INFO` - Zum Berichten von Initialisierungsereignissen und anderen Daten, die wichtig sein können, aber nicht dringend
  * `DEBUG` - Zum Berichten von Debuganweisungen als Unterstützung für Entwickler beim Lösen von Anwendungsfehlern


### Protokollebenen-Szenario
{: #log-level-scenario notoc}

Wenn die Protokollebene mit 'FATAL' konfiguriert ist, erfasst die Protokollfunktion nicht abgefangene Ausnahmebedingungen, aber keine Protokolle, die Aufschluss über den Vorlauf vor dem Absturzereignis liefern. Sie können eine ausführlichere Protokollebene festlegen, um sicherzustellen, dass auch Protokolle erfasst werden, die zum Eintrag 'FATAL' der Protokollfunktion führen, zum Beispiel 'WARN' und 'ERROR'.

Wenn die Protokollierungsstufe auf 'DEBUG' gesetzt ist, erhalten Sie zudem Protokolle des Mobile Analytics-Client-SDK, die im Sendeumfang der Protokolle enthalten sind.

<!-- **Hinweis:** Die vollständigen API-Referenzen zur Protokollfunktion für jede Plattform finden Sie unter [SDKs, Beispiele, API-Referenz](sdks-samples-apis.html). Die API der Protokollfunktion ist Teil des--> <!--{{site.data.keyword.mobileanalytics_short}}-Client-SDK-Cores. -->


### Verwendung der Beispielprotokollfunktion
{: #sample-logger-usage notoc}

**Hinweis:** Stellen Sie sicher, dass Sie die Anwendung zur Verwendung des {{site.data.keyword.mobileanalytics_short}}-Client-SDK instrumentiert haben, bevor Sie das Protokollierungsframework verwenden.

An den folgenden Codeausschnitten wird die Verwendung der Beispielprotokollfunktion veranschaulicht:

- Android
	
	```
	// Konfigurieren Sie die Protokollfunktion zur Speicherung von Protokollen im Gerät, sodass sie
	// später an den Mobile Analytics-Service gesendet werden können
	// Standardmäßig inaktiviert; zum Aktivieren auf 'true' setzen
	Logger.storeLogs(true);
	// Mindestprotokollebene ändern (optional)
	// Standardeinstellung ist Logger.LEVEL.DEBUG
	Logger.setLogLevel(Logger.LEVEL.INFO);
	// Zwei Instanzen der Protokollfunktion erstellen
	// Sie können mehrere Protokollinstanzen erstellen, um Ihre Protokolle zu organisieren
	Logger logger1 = Logger.getLogger("logger1");
	Logger logger2 = Logger.getLogger("logger2");
	// Protokollnachrichten mit unterschiedlichen Ebenen
	// Debugnachricht für Feature 1
	// Informationsnachricht für Feature 2
	logger1.debug("debug message");
	//logger1.debug-Nachricht wird nicht protokolliert, weil logLevelFilter auf 'Info' gesetzt ist
	logger2.info("info message");
	// Protokolle an Mobile Analytics-Service senden
	Logger.send(new ResponseListener() {
		@Override
                    public void onSuccess(Response response) {
			// Sendeerfolg für Logger hier bearbeiten.
                    }
		@Override
                    public void onFailure(Response response, Throwable throwable, JSONObject jsonObject) {
			// Sendefehler für Logger hier bearbeiten.
                    }
	});        
	```
	{: codeblock}


- iOS (Swift)
	
	```
	// Konfigurieren Sie die Protokollfunktion zur Speicherung von Protokollen im Gerät, sodass sie
	// später an den Mobile Analytics-Service gesendet werden können
	// Standardmäßig inaktiviert; zum Aktivieren auf 'true' setzen
	Logger.isLogStorageEnabled = true
	// Mindestprotokollebene ändern (optional)
	// Standardeinstellung ist LogLevel.debug
	Logger.logLevelFilter = LogLevel.info
	// Zwei Instanzen der Protokollfunktion erstellen
	// Sie können mehrere Protokollinstanzen erstellen, um Ihre Protokolle zu organisieren
	let logger1 = Logger.logger(name: "feature1Logger")
	let logger2 = Logger.logger(name: "feature2Logger")
	// Protokollnachrichten mit unterschiedlichen Ebenen
	logger1.debug(message: "debug message for feature 1")
	// Die Nachricht logger1.debug wird nicht protokolliert, weil für
// logLevelFilter der Wert info eingestellt ist
logger2.info(message: "info message for feature 2")
	// Protokolle an den Mobile Analytics-Service senden
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

	**Tipp:** Aus Datenschutzgründen können Sie die Ausgabe der Protokollfunktion für Anwendungen inaktivieren, die im Releasemodus erstellt werden. Von der Protokollfunktionsklasse werden Protokolle standardmäßig in der Xcode-Konsole gedruckt. Fügen Sie in den Erstellungseinstellungen für das Ziel das Flag '-D RELEASE_BUILD' zum Abschnitt mit den weiteren Swift-Flags der Buildkonfiguration des Release hinzu.


- Cordova

	```
	// Persistente Protokolle aktivieren
	BMSLogger.storeLogs(true);
	// Mindestprotokollebene für Druck und Definition als persistent festlegen
	BMSLogger.setLogLevel(BMSLogger.INFO);
	var logger1 = BMSLogger.getLogger("logger1");
	var logger2 = BMSLogger.getLogger("logger2");
	// Protokollnachrichten mit unterschiedlichen Ebenen
	logger1.debug ("debug message");
	logger2.info ("info message");
	// Als persistent definierte Protokolle an den {{site.data.keyword.mobileanalytics_short}}-Service senden
	BMSLogger.send();
	BMSAnalytics.send();
	```
	{: codeblock}

- Web

	```
	// Als persistent definierte Protokolle aktivieren
	BMSAnalytics.Logger.storeLogs(true);
	// Mindestprotokollebene für Druck und Definition als persistent festlegen
	// Protokollebenen in absteigender Ausführlichkeit: trace,debug,log,info,warn,error,fatal,analytics
	BMSAnalytics.Logger.setLogLevel('error');
	// Protokollnachrichten mit unterschiedlichen Ebenen
	BMSAnalytics.Logger.debug ("debug message");
	BMSAnalytics.Logger.info ("info message");
	// Als persistent definierte Protokolle an den {{site.data.keyword.mobileanalytics_short}}-Service senden
	BMSAnalytics.Logger.send();
	BMSAnalytics.send().then(function(result) {
		//Erfolg hier behandeln
        }, function(err) {
         	//Fehler hier behandeln
	 });;
	```
	{: codeblock}

<!--## Interne Protokolle des {{site.data.keyword.mobileanalytics_short}}-Client-SDK aktivieren
{: #enable-logger-sdklogs notoc}

Das {{site.data.keyword.mobileanalytics_short}}-Client-SDK bietet eine bessere Entwicklererfahrung, da es die Konsolenausgabe nicht unnötig mit seinen internen Debugnachrichten belastet. Daher werden interne Protokollnachrichten, die vom {{site.data.keyword.mobileanalytics_short}}-SDK mit der Ebene DEBUG generiert werden, standardmäßig nicht ausgegeben. Sie können die Ausgabe aller internen Protokollnachrichten des {{site.data.keyword.mobileanalytics_short}}-Client-SDK mit der folgenden API aktivieren:

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

## Protokollierung von Positionsdaten
{: #location-logging}

Über diese bereitgestellte API kann die Position des mobilen Geräts aus der App protokolliert werden.
```
Analytics.logLocation();
 
``` 
Diese API ermöglicht der App das Senden ihrer Position zwischen App-Sitzungen als Breiten- und Längengrad an den Server. Anders als diese expliziten Aufrufe an die API für Positionsprotokollierung sendet das SDK die Geräteposition für jede App-Sitzung, sowohl für anfänglichen App-Sitzungskontext als auch für den Kontext von 'userswitch'-App-Sitzungen (d. h. Wechsel des Benutzers zwischen einer App-Sitzung). Wie bereits erwähnt, muss die Positions-API bei der Initialisierung des SDK aktiviert werden.

**Hinweis:**  Um diese Positionsprotokollierung aufzurufen, setzen Sie den Parameter 'collectLocation' wie unten gezeigt bei der SDK-Initialisierung auf 'true'.
```
Analytics.initialize(appName, apiKey,  hasUserContext, collectLocation, [BMSAnalytics.ALL])
		
```





## Netzanforderung stellen
{: #network-requests}

Sie können das {{site.data.keyword.mobileanalytics_short}}-Client-SDK für das [Stellen von Netzanforderungen](/docs/mobile/sdk_network_request.html) konfigurieren. Stellen Sie sicher, dass Sie 'BMSClient' und 'BMSAnalytics' bereits initialisiert und die Client-SDKs importiert haben.

<!--
#### Android
{: #android-network-requests notoc}

**Hinweis:** Bei diesem Codeausschnitt wird davon ausgegangen, dass Sie [die Client-SDKs importiert](#android-import) haben.

```
public void makeGetCall(){
    Thread thread = new Thread(new Runnable() {
        @Override
        public void run() {
            try  {
                Request request = new Request("http://httpbin.org/get", "GET");
                    request.send(null, null);
            } catch (Exception e) {
                // Fehler hier bearbeiten.
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
 	// Netzanforderung stellen
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
// Netzanforderung stellen
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
 	// Netzanforderung stellen
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
// Netzanforderung stellen
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


## Absturzanalysen berichten
{: #report-crash-analytics}

Die [Daten eines Anwendungsabsturzes](app-monitoring.html#monitor-app-crash) können Sie einsehen, indem Sie Analyse- und Protokolldaten an {{site.data.keyword.mobileanalytics_short}} senden.

Die Methode 'Analytics.send()' belegt die Tabelle mit der Absturzübersicht und die Tabelle **Crashes** (Abstürze) auf der Seite **Crashes** (Abstürze). Die Diagramme in diesem Abschnitt werden unter Verwendung der Initialisierung und des Sendevorgangs für Analysedaten aktiviert; eine spezielle Konfiguration ist nicht notwendig.

Die Methode 'Logger.send()' belegt die Tabellen für die Absturzzusammenfassung und für Absturzdetails auf der Seite **Fehlerbehebung**. Zum Füllen der Diagramme in diesem Abschnitt müssen Sie Ihre Anwendung für das Speichern und Senden von Protokollen aktivieren. Dies geschieht durch Hinzufügen einer zusätzlichen Anweisung in Ihrem Anwendungscode:


- Android

	`Logger.storeLogs(true);`
	<!-- * `Logger.setLogLevel(Logger.LEVEL.FATAL); // oder höher` -->
	
	Siehe [Verwendung der Beispielprotokollfunktion](sdk.html##sample-logger-usage) für Android.


- iOS
		
	`Logger.isLogStorageEnabled = true`
	<!-- * `Logger.logLevelFilter = LogLevel.Fatal // oder höher` -->
	
	Siehe [Verwendung der Beispielprotokollfunktion](sdk.html##sample-logger-usage) für iOS.


- Cordova

	 `BMSLogger.storeLogs(true);`
	<!-- * `Logger.logLevelFilter = LogLevel.Fatal // oder höher` -->
	
	Siehe [Verwendung der Beispielprotokollfunktion](sdk.html##sample-logger-usage) für Cordova.

- Web

	`BMSAnalytics.Logger.storeLogs(true);`

## Aktive Benutzer verfolgen
{: #trackingusers}

Wenn Ihre Anwendung eindeutige Benutzer für ein Gerät erkennen kann, können Sie optional verfolgen, wie viele Benutzer die Anwendung aktiv nutzen, indem Sie den Benutzernamen des aktiven Benutzers an {{site.data.keyword.mobileanalytics_short}} übergeben.

Aktivieren Sie die Benutzerverfolgung, indem Sie {{site.data.keyword.mobileanalytics_short}} mit 'hasUserContext=true' initialisieren. Andernfalls erfasst {{site.data.keyword.mobileanalytics_short}} nur einen Benutzer pro Gerät. 


- Android

	Fügen Sie den folgenden Code hinzu, um zu verfolgen, wann sich der Benutzer anmeldet:
	
	```
	Analytics.setUserIdentity("username");
	```
	{: codeblock}
	
	<!--Fügen Sie folgenden Code hinzu für den Fall, dass sich der Benutzer abmeldet:
	
	```
	Analytics.clearUserIdentity();
	```
	{: codeblock}
	-->

- iOS (Swift)

	Fügen Sie den folgenden Code hinzu, um zu verfolgen, wann sich der Benutzer anmeldet:
	
	```
	Analytics.userIdentity = "username"
	```
	{: codeblock}
	
	<!--
	Fügen Sie folgenden Code hinzu für den Fall, dass sich der Benutzer abmeldet:
	
	```
	Analytics.userIdentity = nil
	```
	{: codeblock}
	-->


- Cordova
		
	Fügen Sie den folgenden Code hinzu, um zu verfolgen, wann sich der Benutzer anmeldet:
	
	```
	BMSAnalytics.setUserIdentity("username");
	```
	{: codeblock}

- Web

	Fügen Sie den folgenden Code hinzu, um zu verfolgen, wann sich der Benutzer anmeldet:
	
	```
	BMSAnalytics.setUserIdentity("username");
	```
	{: codeblock}

## App-interne Feedbackanalyse
{: #In-App}

Die App-interne Feedbackanalyse ermöglicht es **Benutzern und Testern**, kontextreiches Feedback für App-Eigner bereitzustellen. **App-Eigner** erhalten Echtzeitfeedback von ihren Benutzern auf Grundlage der App-Nutzung. **Entwickler** implementieren Änderungen auf Basis der Echtzeitinformationen.

Rufen Sie die unten stehende API auf, um Ihre mobile App für den Feedbackmodus zu instrumentieren.

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
	
<!--## MobileFirst Platform Foundation-Server für die Verwendung des {{site.data.keyword.mobileanalytics_short}}-Service konfigurieren (optional)
{: #configmfp notoc}
  Wenn Sie MobileFirst Platform Foundation Server V7 oder höher verwenden, können Sie es für die Verwendung des {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.mobileanalytics_short}}-Service konfigurieren, sodass Analyse- und Protokolldaten gespeichert werden.

  Konfigurieren Sie die Beta-Server von MobileFirst Platform Version 7.0, Version 7.1 und Version 8.0, sodass Analysedaten an den {{site.data.keyword.mobileanalytics_short}}-Service auf {{site.data.keyword.Bluemix_notm}} gesendet werden.

  1. Rufen Sie das Dashboard für den {{site.data.keyword.mobileanalytics_short}}-Service auf, an den die Analysedaten gesendet werden sollen, und vermerken Sie die Browser-URL für das Dashboard.
  2. Bestimmen Sie den Wert für das Berichten der Analysedaten wie folgt:
  	1. Rufen Sie die {{site.data.keyword.mobileanalytics_short}}-Serviceroute von der Dashboard-URL auf. Die {{site.data.keyword.mobileanalytics_short}}-Serviceroute ist der Teil der URL vor ``/analytics/console/dashboard``.

  		Beispiel: Wenn die Dashboard-URL lautet: `http://mobile-analytics-dashboard.ng.bluemix.net/analytics/console/dashboard?instanceId=12345abcde`
      {: screen}

  		dann ist die Route des Analyseservice
      `http://mobile-analytics-dashboard.ng.bluemix.net`
      {: screen}

  	2. Rufen Sie den [Client-API-Schlüsselwert](#analytics-clientkey) vom Analysedashboard ab.

  	Sie werden die {{site.data.keyword.mobileanalytics_short}}-Serviceroute und den API-Schlüssel zum Erstellen einer URL für das Berichten der Analysedaten verwenden, abhängig von der Version Ihres ersten MobileFirst Platform-Servers. -->

<!--  3. Kopieren Sie die URL für Ihr {{site.data.keyword.mobileanalytics_short}}-Servicedashboard. Schließen Sie den Abfrageparameter `instanceId` ein, z. B.:
      `http://mobile-analytics-dashboard.ng.bluemix.net/analytics/console/dashboard?instanceId=1212345abcde`
      {: screen}

  4. Konfigurieren Sie die Werte für die JNDI-Eigenschaften des MobileFirst-Plaftform-Servers wie folgt:-->

<!--    ### MobileFirst Platform V7.0
    {: #mfp70 notoc}

        Das Format der JNDI-Eigenschaft `wl.analytics.url` ist: `<Analyseserviceroute>/analytics-service/rest/data?tenant=<Client-API-Schlüssel>`
        {: screen}

        Die JNDI-Eigenschaft `wl.analytics.console.url` ist die Dashboard-URL des Analyseservice.

        #### Beispiel für JNDI-Eigenschaftswerte von MobileFirst Platform V7.0
        {: #example-mfp70-jndi-values notoc}

        Für ein MobileFirst-Plattform-Projekt mit dem Namen `Myproj7000` ersetzen Sie anhand der Beispiele in den Schritten 2 und 3 die aktuellen JNDI-Eigenschaftswerte in der Datei `server.xml` durch:
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

      Das Format der JNDI-Eigenschaft `wl.analytics.url` ist: `<Analyseserviceroute>/analytics-service/rest/v2/<Client-API-Schlüssel>`
      {: screen}

      #### Beispiel für JNDI-Eigenschaftswerte von MobileFirst Platform V7.1
      {: #example-mfp71-jndi-values notoc}

      Für ein MobileFirst-Plattform-Projekt mit dem Namen `MyProj7101` ersetzen Sie die aktuellen JNDI-Eigenschaftswerte in der Datei `server.xml` durch:
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

      Das Format der JNDI-Eigenschaft `mfp.analytics.url` ist:
      `<Analyseserviceroute>/analytics-service/rest/v2/<Client-API-Schlüssel>`

    #### Beispiel für JNDI-Eigenschaftswerte von MobileFirst Platform V8.0
      {: example-mfp80b-jndi-values}

       Für ein MobileFirst-Plattform-Projekt mit dem Standardnamen `mfp` ersetzen Sie die aktuellen JNDI-Eigenschaftswerte in der Datei `server.xml` durch:
      ```
      <jndiEntry jndiName="mfp/mfp.analytics.url" value='"http://mobile-analytics-dashboard.ng.bluemix.net/analytics-service/rest/data?tenant=12345abcde"'/>
      ```
      {: screen}
      ```
      <jndiEntry jndiName="mfp/mfp.analytics.console.url" value='"http://mobile-analytics-dashboard.ng.bluemix.net/analytics/console/dashboard?instanceId=12345abcde"'/>
      ```
      {: screen}
-->
<!-- #### Ignorierte Ereignisse und Ereignisaufbewahrung
{: #ignored-events notoc}
Der {{site.data.keyword.mobileanalytics_short}}-Service speichert die folgenden Daten zu ignorierten Ereignissen und zur Ereignisaufbewahrung:

<dl>	
<dt>Ignorierte Ereignisse</dt>
	<dd>`ANALYTICS_SDK_CFG_IGNORE_AppPushAction: true`
		  `ANALYTICS_SDK_CFG_IGNORE_ServerLog: true`
		  `ANALYTICS_SDK_CFG_IGNORE_NetworkTransaction: true`
		  `ANALYTICS_SDK_CFG_IGNORE_NetworkTransactionSummarizedHourly: true`
		  `ANALYTICS_SDK_CFG_IGNORE_PushNotification: true`
		  `ANALYTICS_SDK_CFG_IGNORE_PushSubscription: true`</dd>
</dt>
<dt>Ereignisaufbewahrung</dd>
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


## Nächste Schritte
{: #what-to-do-next notoc}

Sie können jetzt die {{site.data.keyword.mobileanalytics_short}}-Konsole aufrufen, um Nutzungsanalysedaten, z. B. neue Geräte und die Gesamtzahl der Geräte, die Ihre Anwendung nutzen, anzuzeigen. Sie können Ihre Anwendung auch überwachen, indem Sie <!--[angepasste Diagramme erstellen](app-monitoring.html#custom-charts),-->[Alerts festlegen](app-monitoring.html#alerts) und [App-Abstürze überwachen](app-monitoring.html#monitor-app-crash).


# Zugehörige Links
{: #rellinks notoc}

## API-Referenz
{: #api notoc}

* [REST-API ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://mobile-analytics-dashboard.{DomainName}/analytics-service/){:new_window}
