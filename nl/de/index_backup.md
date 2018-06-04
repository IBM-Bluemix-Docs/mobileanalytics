---

copyright:
  years: 2016, 2017
lastupdated: "2017-07-14"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Lernprogramm 'Einführung'

{: #gettingstartedtemplate}

{{site.data.keyword.mobileanalytics_full}} liefert Entwicklern, IT-Administratoren und Verantwortlichen Aufschlüsse über Leistung und Nutzungsweise ihrer mobilen Apps. Mit {{site.data.keyword.mobileanalytics_short}} haben Sie die folgenden Möglichkeiten:

* Überwachen Sie damit Leistung und Nutzung aller Ihrer Anwendungen vom Desktop oder Tablet aus. 
* So erkennen Sie schnell Trends und Anomalien, gelangen durch Drilldown zur Problemlösung und lösen Alerts aus, wenn Schlüsselmesswerte kritische Schwellenwerte überschreiten. 
{: shortdesc}

Führen Sie die folgenden Schritte aus, um den {{site.data.keyword.mobileanalytics_short}}-Service ohne zeitliche Verzögerung betriebsbereit zu machen:

1. Nachdem Sie eine Instanz <!--[create an instance](https://console.{DomainName}/docs/services/reqnsi.html#req_instance)-->des {{site.data.keyword.mobileanalytics_short}}-Service erstellt haben, können Sie auf die {{site.data.keyword.mobileanalytics_short}}-Konsole zugreifen, indem Sie auf die entsprechende Kachel im Abschnitt **Services** des {{site.data.keyword.Bluemix}}-Dashboards klicken. Eine Option **Demomodus** ist in der {{site.data.keyword.mobileanalytics_short}}-Konsole verfügbar und bewirkt, dass die Ansichten und Diagramme mit *Demodaten* gefüllt sind. Der Demomodus ist der Standardmodus der Konsole bei deren erstem Start, nachdem der Service instanziiert wurde. Wenn Sie den Service mit Ihren eigenen Anwendungen und Analysedaten gefüllt haben, können Sie den Demomodus *inaktivieren* und die Daten Ihrer Anwendungen in den anderen Diagrammen anzeigen. Die {{site.data.keyword.mobileanalytics_short}}-Konsole ist im Demomodusschreibgeschützt, weshalb Sie keine neuen Alertdefinitionen erstellen können.

2. Installieren Sie die {{site.data.keyword.mobileanalytics_short}} [Client-SDKs](/docs/services/mobileanalytics/install-client-sdk.html). Sie können optional die {{site.data.keyword.mobileanalytics_short}} [REST-API ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://mobile-analytics-dashboard.{DomainName}/analytics-service/){:new_window} verwenden.
	
	- Konfiguration des Web-App-Service
	
		Bei einer Web-SDK müssen Sie, um Ihre Serviceinstanz so zu konfigurieren, dass sie einen App-Server zulässt, die URL Ihres App-Servers mittels der REST-API für die Servicekonfiguration über die Swagger-Benutzerschnittstelle angeben. Die Methoden POST, GET, PUT und DELETE werden für CRUD-Operationen der Servicekonfiguration angegeben, die eine Liste der zulässigen ULRs darstellt. Zum Abrufen oder Löschen (GET/DELETE) von Konfigurationen Ihrer Serviceinstanz verwenden Sie Ihren API-Schlüssel. Um die Servicekonfiguration zu erstellen und zu aktualisieren, verwenden Sie die Methoden POST und PUT mit zulässigen URLs, die als Hauptteil aufgelistet sind {"allowedUrls":["http://abc.com","https://www.xyz.com"]}. Wenn Sie von einem Browser in demselben System wie dem des Web-Servers zugreifen, geben Sie "http://localhost" als zulässige URL an.

3. Importieren Sie die Client-SDKs und initialisieren Sie sie mit dem folgenden Codeausschnitt, um die Nutzungsanalysedaten aufzuzeichnen:

	- Android
	
		Fügen Sie die folgenden `import`-Anweisungen am Anfang Ihrer Projektdatei ein:
		
		```
		import com.ibm.mobilefirstplatform.clientsdk.android.core.api.*;
import com.ibm.mobilefirstplatform.clientsdk.android.analytics.api.*;
import com.ibm.mobilefirstplatform.clientsdk.android.logger.api.*;
		```
		{: codeblock}

	- iOS

		Das Swift-SDK ist für iOS und WatchOS verfügbar.
		
		Importieren Sie die Frameworks `BMSCore` und `BMSAnalytics` durch Hinzufügen der folgenden `import`-Anweisungen am Anfang der Projektdatei `AppDelegate.swift`:
	
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
	
		Fügen Sie das Web-Plug-in hinzu, indem Sie entweder dieses Script in der Datei `index.html` der Web-App hinzufügen:
	
		```Html
		<script src="bms-clientsdk-web-analytics/bmsanalytics.js"></script>
		```
		{: codeblock}

		Oder indem Sie den Modul-Loader RequireJS verwenden. Der als Referenz-API verwendete Name ist mit dem verwendeten Argumentnamen (`BMSAnalytics`) identisch. 
	
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
	
4. Initialisieren Sie das {{site.data.keyword.mobileanalytics_short}}-Client-SDK in Ihrem Anwendungscode, um Nutzungsanalysedaten und Anwendungssitzungen mit Ihrem [API-Schlüsselwert](/docs/services/mobileanalytics/sdk.html#analytics-clientkey) aufzuzeichnen.	
	
	- Android
	
		```
		BMSClient.getInstance().initialize(getApplicationContext(), BMSClient.REGION_US_SOUTH); // Sie können die Region ändern
		Analytics.init(getApplication(), "your_app_name_here", "your_api_key_here", hasUserContext, collectLocation, Analytics.DeviceEvent.ALL);
```
		{: codeblock}
	
		Der Parameter **bluemixRegion** gibt an, welche {{site.data.keyword.Bluemix_notm}}-Bereitstellung Sie verwenden, z. B. 'BMSClient.REGION_US_SOUTH' und 'BMSClient.REGION_UK'.
	    <!-- oder 'BMSClient.Region.Sydney'.-->
	
		Setzen Sie den Wert für 'hasUserContext' auf **true** oder **false**. Bei 'false' (Standardwert) wird jedes Gerät als aktiver Benutzer gezählt.
		
		Setzen Sie den Wert für 'collectLocation' auf **true** oder **false**. Bei 'true' werden die Daten für die Geräteposition als Teil des App-Sitzungsprotokolls gesendet.

	- iOS
	  
		Initialisieren Sie das Client-SDK in Ihrem Anwendungscode, um Nutzungsanalysedaten und Anwendungssitzungen aufzuzeichnen. Verwenden Sie hierzu Ihren [API-Schlüsselwert](/docs/services/mobileanalytics/sdk.html#analytics-clientkey).
		
		```Swift
		BMSClient.sharedInstance.initialize(bluemixRegion: BMSClient.Region.usSouth) // Sie können die Region ändern
		Analytics.initialize(appName: "your_app_name_here", apiKey: "your_api_key_here", hasUserContext: false, collectLocation: true, deviceEvents: deviceEvents: .lifecycle, .network)
		```
		{: codeblock}
	
		Der Parameter **bluemixRegion** gibt an, welche IBM Cloud-Bereitstellung Sie verwenden, z. B. 'BMSClient.Region.usSouth' oder 'BMSClient.Region.unitedKingdom'.
		<!-- oder 'BMSClient.REGION_SYDNEY'. -->
	
		Setzen Sie den Wert für 'hasUserContext' auf **true** oder **false**. Bei 'false' (Standardwert) wird jedes Gerät als aktiver Benutzer gezählt.
		
		Setzen Sie den Wert für 'collectLocation' auf **true** oder **false**. Bei 'true' werden die Daten für die Geräteposition als Teil des App-Sitzungsprotokolls gesendet.

	- Cordova
		
		Initialisieren Sie das Client-SDK in Ihrem Anwendungscode, um Nutzungsanalysedaten und Anwendungssitzungen aufzuzeichnen. Verwenden Sie hierzu Ihren [API-Schlüsselwert](/docs/services/mobileanalytics/sdk.html#analytics-clientkey).
		
		```
		var appName = "your_app_name_here";
		var apiKey = "your_api_key_here";
		BMSClient.initialize(BMSClient.REGION_US_SOUTH); // Sie können die Region ändern
		BMSAnalytics.initialize(appName, apiKey, hasUserContext, collectLocation, [BMSAnalytics.ALL])
```
		{: codeblock}
	
		Der Parameter **bluemixRegion** gibt an, welche IBM Cloud-Bereitstellung Sie verwenden, z. B. 'BMSClient.REGION_US_SOUTH' oder 'BMSClient.REGION_UK'.
		<!-- oder 'BMSClient.REGION_SYDNEY'. -->
		Setzen Sie den Wert für 'hasUserContext' auf **true** oder **false**. Bei 'false' (Standardwert) wird jedes Gerät als aktiver Benutzer gezählt.
		
		Setzen Sie den Wert für 'collectLocation' auf **true** oder **false**. Bei 'true' werden die Daten für die Geräteposition als Teil des App-Sitzungsprotokolls gesendet.

	- Web
		
		Initialisieren Sie das Client-SDK in Ihrem Anwendungscode, um Nutzungsanalysedaten und Anwendungssitzungen aufzuzeichnen. Verwenden Sie hierzu Ihren [API-Schlüsselwert](/docs/services/mobileanalytics/sdk.html#analytics-clientkey).
		
		```
		var appName = "your_app_name_here";
		var apiKey = "your_api_key_here";
		BMSAnalytics.Client.initialize(BMSAnalytics.Client.REGION_US_SOUTH);
		BMSAnalytics.initialize(appName,apiKey,hasUserContext,BMSAnalytics.DeviceEvents.ALL,instanceId);
``` 
		{: codeblock}

		Der Parameter 'bluemixRegion' gibt an, welche {{site.data.keyword.Bluemix_notm}}-Bereitstellung Sie verwenden, z. B. 'BMSAnalytics.Client.REGION_US_SOUTH' und 'BMSAnalytics.Client.REGION_UK'. Setzen Sie den Wert für 'hasUserContext' auf 'true' oder 'false'. Bei 'false' (Standardwert) wird jedes Gerät als aktiver Benutzer gezählt. Setzen Sie die Instanz-ID auf die ID Ihrer Serviceinstanz. Dies ist eine alphanumerische Zeichenfolge, die Sie nach der Zeichenfolge "...mobile-analytics_Prod/" und bis zu "/" von der Browser-URL für Ihre Serviceinstanz abrufen.

		Bitte beachten: Der Name, den Sie für Ihre Anwendung auswählen ('your_app_name_here'), wird in der {{site.data.keyword.mobileanalytics_short}}-Konsole als Anwendungsname angezeigt. Der Anwendungsname wird als Filter für die Suche nach Anwendungsprotokollen im Dashboard verwendet. Wenn Sie plattformübergreifend (zum Beispiel für Android und iOS) denselben Anwendungsnamen verwenden, können Sie unter einem Namen unabhängig von der Plattform, von der die Protokolle stammen, alle Protokolle zu dieser Anwendung anzeigen.

5. Senden Sie die aufgezeichneten Nutzungsanalysedaten an den {{site.data.keyword.mobileanalytics_short}}-Service. Eine einfache Möglichkeit zum Testen der Analyse ist das Ausführen des folgenden Codes, wenn die Anwendung gestartet wird:

	- Android
	
		Verwenden Sie die Methode 'Analytics.send()' zum Senden von Analysedaten an den Server. Sie können die Methode 'Analytics.send()' an beliebiger Position in der Methode 'onCreate' der Hauptaktivität in Ihrer Android-Anwendung oder an einer Position anordnen, die für Ihr Projekt am besten geeignet ist.
	
		'Analytics.send()' kann an beliebiger Position eingefügt werden.
	
	- iOS
	
		Verwenden Sie die Methode 'Analytics.send' zum Senden von Analysedaten an den Server. Sie können die Methode 'Analytics.send' an beliebiger Position in der Methode 'application(_:didFinishLaunchingWithOptions:)' Ihres Anwendungsdelegierten oder an einer Position anordnen, die für Ihr Projekt am besten geeignet ist.
	
	- Cordova
		
		Verwenden Sie die Methode 'BMSAnalytics.send' zum Senden von Analysedaten an den Server. Ordnen Sie die Methode 'BMSAnalytics.send' an einer beliebigen Position an, die sich am besten für Ihr Projekt eignet.
		
	- Web
		
		Verwenden Sie die Methode 'BMSAnalytics.send' zum Senden von Analysedaten an den Server. Ordnen Sie die Methode 'BMSAnalytics.send' an einer beliebigen Position an, die sich am besten für Ihr Projekt eignet.
		
6. Lesen Sie das Thema [Anwendung instrumentieren](/docs/services/mobileanalytics/sdk.html), um mehr über zusätzliche {{site.data.keyword.mobileanalytics_short}}-Funktionen wie z. B. [Protokollierung](/docs/services/mobileanalytics/sdk.html#app-monitoring-logger), [Netzanforderungen](/docs/services/mobileanalytics/sdk.html#network-requests), [Positionsprotokollierung](/docs/services/mobileanalytics/sdk.html#location-logging) oder [Absturzanalysen](/docs/services/mobileanalytics/sdk.html#report-crash-analytics) zu erfahren.
	
7. Kompilieren Sie die Anwendung und führen Sie sie im Emulator oder einem Gerät aus.

8. Wechseln Sie zur {{site.data.keyword.mobileanalytics_short}}-Konsole, um die Nutzungsanalysedaten für Ihre Anwendung anzuzeigen. Sie können Ihre Anwendung auch überwachen, indem Sie <!--[angepasste Diagramme erstellen](app-monitoring.html#custom-charts),-->[Alerts festlegen](/docs/services/mobileanalytics/app-monitoring.html#alerts) oder [App-Abstürze überwachen](/docs/services/mobileanalytics/app-monitoring.html#monitor-app-crash).

# Zugehörige Links
{: #rellinks notoc}

## SDK
{: #sdk notoc}
* [Android SDK ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-analytics){: new_window}
* [iOS-SDK ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-analytics){: new_window}
* [Cordova-Plug-in-Core-SDK ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.npmjs.com/package/bms-core){: new_window}
* [Web-SDK![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-web-analytics/){: new_window}
## API-Referenz
{: #api notoc}
* [REST-API ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://mobile-analytics-dashboard.{DomainName}/analytics-service/){:new_window}
