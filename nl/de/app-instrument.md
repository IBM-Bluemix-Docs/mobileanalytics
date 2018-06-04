---

copyright:
 years: 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# App instrumentieren
{: #Instrument}
Letzte Aktualisierung: 18. Januar 2018
{: .last-updated}

##{{site.data.keyword.mobileanalytics_short}}-Client-SDK initialisieren 

Initialisieren Sie das {{site.data.keyword.mobileanalytics_short}}-Client-SDK in Ihrem Anwendungscode, um Nutzungsanalysedaten und Anwendungssitzungen aufzuzeichnen. Verwenden Sie hierzu Ihren [API-Schlüsselwert](/docs/services/mobileanalytics/sdk.html#analytics-clientkey).	
	
- **Android**
	
```
		BMSClient.getInstance().initialize(getApplicationContext(), BMSClient.REGION_US_SOUTH); // Sie können die Region ändern
		Analytics.init(getApplication(), "your_app_name_here", "your_api_key_here", hasUserContext, collectLocation, Analytics.DeviceEvent.ALL);
```
		{: codeblock}
	    
Der Parameter **bluemixRegion** gibt an, welche {{site.data.keyword.Bluemix_notm}}-Bereitstellung Sie verwenden, z. B. `BMSClient.REGION_US_SOUTH` und `BMSClient.REGION_UK`. 
	    
	    
Setzen Sie den Wert für `hasUserContext` auf **true** oder **false**. Bei 'false' (Standardwert) wird jedes Gerät als aktiver Benutzer gezählt.
		
Setzen Sie den Wert für `collectLocation` auf **true** oder **false**. Bei 'true' werden die Daten für die Geräteposition als Teil des App-Sitzungsprotokolls gesendet. 

- **iOS**
	  
Initialisieren Sie das Client-SDK im Anwendungscode, um Nutzungsanalysedaten und Anwendungssitzungen aufzuzeichnen. Verwenden Sie hierzu Ihren [API-Schlüsselwert](/docs/services/mobileanalytics/sdk.html#analytics-clientkey).
		
```Swift
		BMSClient.sharedInstance.initialize(bluemixRegion: BMSClient.Region.usSouth) // Sie können die Region ändern
		Analytics.initialize(appName: "your_app_name_here", apiKey: "your_api_key_here", hasUserContext: false, collectLocation: true, deviceEvents: deviceEvents: .lifecycle, .network)
```
		{: codeblock}
				
Der Parameter **bluemixRegion** gibt an, welche IBM Cloud-Bereitstellung Sie verwenden, z. B. `BMSClient.Region.usSouth` oder `BMSClient.Region.unitedKingdom`.
		
	 
Setzen Sie den Wert für `hasUserContext` auf **true** oder **false**. Bei 'false' (Standardwert) wird jedes Gerät als aktiver Benutzer gezählt.
		
Setzen Sie den Wert für `collectLocation` auf **true** oder **false**. Bei 'true' werden die Daten für die Geräteposition als Teil des App-Sitzungsprotokolls gesendet. 
	
- **Cordova**
		
Initialisieren Sie das Client-SDK im Anwendungscode, um Nutzungsanalysedaten und Anwendungssitzungen aufzuzeichnen. Verwenden Sie hierzu Ihren [API-Schlüsselwert](/docs/services/mobileanalytics/sdk.html#analytics-clientkey).
		
```
		var appName = "your_app_name_here";
		var apiKey = "your_api_key_here";
		BMSClient.initialize(BMSClient.REGION_US_SOUTH); // Sie können die Region ändern
		BMSAnalytics.initialize(appName, apiKey, hasUserContext, collectLocation, [BMSAnalytics.ALL])
```
		{: codeblock}
		
Der Parameter **bluemixRegion** gibt an, welche IBM Cloud-Bereitstellung Sie verwenden, z. B. `BMSClient.REGION_US_SOUTH` oder `BMSClient.REGION_UK`.
		
Setzen Sie den Wert für `hasUserContext` auf **true** oder **false**. Bei 'false' (Standardwert) wird jedes Gerät als aktiver Benutzer gezählt.
		
Setzen Sie den Wert für `collectLocation` auf **true** oder **false**. Bei 'true' werden die Daten für die Geräteposition als Teil des App-Sitzungsprotokolls gesendet.
    
- **Web**
		
Initialisieren Sie das Client-SDK im Anwendungscode, um Nutzungsanalysedaten und Anwendungssitzungen aufzuzeichnen. Verwenden Sie hierzu Ihren [API-Schlüsselwert](/docs/services/mobileanalytics/sdk.html#analytics-clientkey).
		
```
		var appName = "your_app_name_here";
		var apiKey = "your_api_key_here";
		BMSAnalytics.Client.initialize(BMSAnalytics.Client.REGION_US_SOUTH);
		BMSAnalytics.initialize(appName,apiKey,hasUserContext,BMSAnalytics.DeviceEvents.ALL,instanceId);
``` 
		{: codeblock}

Der Parameter `bluemixRegion` gibt an, welche {{site.data.keyword.Bluemix_notm}}-Bereitstellung Sie verwenden. Setzen Sie den Wert für `hasUserContext` auf `true` oder `false`. Bei 'false' (Standardwert) wird jedes Gerät als aktiver Benutzer gezählt. Setzen Sie die `Instanz-ID` auf die ID Ihrer Serviceinstanz. Dies ist eine alphanumerische Zeichenfolge, die Sie nach der Zeichenfolge "...mobile-analytics_Prod/"  und bis zu "/" von der Browser-URL für Ihre Serviceinstanz abrufen. 

**Anmerkung**: Der Name, den Sie für Ihre Anwendung auswählen (`your_app_name_here`), wird in der {{site.data.keyword.mobileanalytics_short}}-Konsole als Anwendungsname angezeigt. Der Anwendungsname wird als Filter für die Suche nach Anwendungsprotokollen im Dashboard verwendet. Wenn Sie plattformübergreifend (zum Beispiel für Android und iOS) denselben Anwendungsnamen verwenden, können Sie unter einem Namen unabhängig von der Plattform, von der die Protokolle stammen, alle Protokolle zu dieser Anwendung anzeigen.

##App-Daten an den {{site.data.keyword.mobileanalytics_short}}-Service senden

Senden Sie die aufgezeichneten Nutzungsanalysedaten an den {{site.data.keyword.mobileanalytics_short}}-Service. Eine einfache Möglichkeit zum Testen der Analyse ist das Ausführen des folgenden Codes, wenn die Anwendung gestartet wird:


- **Android**
	
Verwenden Sie die Methode `Analytics.send()` zum Senden von Analysedaten an den Server. Sie können die Methode `Analytics.send()` an beliebiger Position in der Methode `onCreate` der Hauptaktivität in Ihrer Android-Anwendung oder an einer Position anordnen, die für Ihr Projekt am besten geeignet ist. 
	
`Analytics.send()` kann an beliebiger Position eingefügt werden.
	
- **iOS**
	
Verwenden Sie die Methode `Analytics.send` zum Senden der Analysedaten an den Server. Sie können die Methode `Analytics.send` an beliebiger Position in der Methode `application(_:didFinishLaunchingWithOptions:)` Ihres Anwendungsdelegierten oder an einer Position anordnen, die für Ihr Projekt am besten geeignet ist. 
	
- **Cordova**
		
Verwenden Sie die Methode `BMSAnalytics.send` zum Senden der Analysedaten an den Server. Legen Sie die Methode `BMSAnalytics.send` an einer Position ab, die sich am besten für Ihr Projekt eignet.
		
- **Web**
		
Verwenden Sie die Methode `BMSAnalytics.send` zum Senden der Analysedaten an den Server. Legen Sie die Methode `BMSAnalytics.send` an einer Position ab, die sich am besten für Ihr Projekt eignet. 
		



Lesen Sie den Abschnitt [Anwendung instrumentieren](/docs/services/mobileanalytics/sdk.html), um mehr über zusätzliche {{site.data.keyword.mobileanalytics_short}}-Funktionen, wie [Protokollierung](/docs/services/mobileanalytics/sdk.html#app-monitoring-logger), [Netzanforderungen](/docs/services/mobileanalytics/sdk.html#network-requests), [Positionsprotokollierung](/docs/services/mobileanalytics/sdk.html#location-logging) und [Absturzanalysen](/docs/services/mobileanalytics/sdk.html#report-crash-analytics) zu erfahren.


Ihr nächster Schritt ist das **Kompilieren und Ausführen der Anwendung im Emulator oder auf einem Gerät**.
