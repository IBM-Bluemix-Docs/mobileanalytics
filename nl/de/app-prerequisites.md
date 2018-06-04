---

copyright:
 years: 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Voraussetzungen
{: #prerequisites}
Letzte Aktualisierung: 18. Januar 2018
{: .last-updated}


## Mobile Analytics-Serviceinstanz erstellen
{: #prerequisites_1}

1. Klicken Sie im [IBM Cloud-Katalog](https://console.ng.bluemix.net/catalog/) auf **Mobile** > **Mobile Analytics**.
2. Geben Sie einen Servicenamen an.
3. Klicken Sie auf **Erstellen**.
4. Wählen Sie eine Verbindung zu anderen vorhandenen Apps oder lassen Sie den Service nicht gebunden.


Sie können einen gebundenen oder nicht gebundenen Service erstellen. Gebundene Services werden mit anderen IBM Cloud-Apps verbunden, nicht gebundene Services sind eigenständig und nicht mit anderen Apps verbunden. 

## App initialisieren
{: #prerequisites_app}

[Importieren](/docs/services/mobileanalytics/available-client-sdk.html) und installieren Sie die {{site.data.keyword.mobileanalytics_short}} [Client-SDKs](/docs/services/mobileanalytics/install-client-sdk.html). Sie können optional die {{site.data.keyword.mobileanalytics_short}} [REST-API ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://mobile-analytics-dashboard.{DomainName}/analytics-service/){:new_window} verwenden.


###Client-SDKs importieren

Importieren Sie die Client-SDKs und initialisieren Sie sie mit dem folgenden Codeausschnitt, um die Nutzungsanalysedaten aufzuzeichnen:

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
		
		
Ihr nächster Schritt ist das [Instrumentieren Ihrer App](app-instrument.html).


