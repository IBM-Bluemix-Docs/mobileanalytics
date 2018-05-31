---

copyright:
  years: 2016, 2017
lastupdated: "2017-07-14"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Esercitazione introduttiva

{: #gettingstartedtemplate}

{{site.data.keyword.mobileanalytics_full}} fornisce agli sviluppatori, agli amministratori IT e alle parti interessate di business informazioni approfondite su come stanno venendo eseguite le loro applicazioni e su come stanno venendo utilizzate. {{site.data.keyword.mobileanalytics_short}} ti consente di:

* Monitora le prestazioni e l'utilizzo di tutte le tue applicazioni dal tuo desktop o tablet. 
* Identifica velocemente gli andamenti e le anomalie, esegue il drilldown per risolvere i problemi e attiva gli avvisi quando le metriche chiave superano le soglie critiche. 
{: shortdesc}

Per essere operativi rapidamente con il servizio {{site.data.keyword.mobileanalytics_short}}, utilizza la seguente procedura:

1. Dopo che hai creato un'istanza <!--[create an instance](https://console.{DomainName}/docs/services/reqnsi.html#req_instance)-->del servizio {{site.data.keyword.mobileanalytics_short}}, puoi accedere alla console {{site.data.keyword.mobileanalytics_short}} facendo clic sul tuo tile nella sezione **Servizi** del dashboard {{site.data.keyword.Bluemix}}. Un'opzione **modalità demo** è disponibile nella console {{site.data.keyword.mobileanalytics_short}}, in cui le viste e i grafici visualizzano i *dati demo*. La modalità demo è la modalità predefinita della console all'avvio iniziale dopo aver istanziato il servizio. Quando disponi delle tue proprie applicazioni e i
dati di analisi hanno popolato il servizio, puoi *disattivare* la modalità demo per visualizzare i dati della tua applicazione
in grafici diversi. La console {{site.data.keyword.mobileanalytics_short}} è in sola lettura nella modalità demo, quindi non sarai in grado di creare nuove definizioni dell'avviso.

2. Installa gli [SDK client](/docs/services/mobileanalytics/install-client-sdk.html) {{site.data.keyword.mobileanalytics_short}}. Puoi facoltativamente utilizzare l'{{site.data.keyword.mobileanalytics_short}}API REST [ ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://mobile-analytics-dashboard.{DomainName}/analytics-service/){:new_window}.
	
	- Configurazione del servizio dell'applicazione web
	
		Per l'SDK Web, per configurare la tua istanza del servizio per consentire un server dell'applicazione, devi fornire l'URL del tuo server dell'applicazione tramite l'API REST di configurazione del servizio attraverso la IU Swagger. I metodi POST, GET, PUT e DELETE vengono forniti per le operazioni CRUD della configurazione del servizio che è un elenco di URL consentiti. Per le configurazioni GET e DELETE della tua istanza del servizio, utilizza la chiave API. Per creare e aggiornare la configurazione del servizio, utilizza i metodi POST e PUT con gli URL consentiti elencati come corpo {"allowedUrls":["http://abc.com","https://www.xyz.com"]}. Se stai accedendo da un browser nello stesso sistema del server web, fornisci "http://localhost" come URL consentito.

3. Importa le SDK client e inizializzale con il seguente frammento di codice per registrare l'analisi dell'utilizzo:

	- Android
	
		Aggiungi le seguenti istruzioni `import` all'inizio del tuo file del progetto:
		
		```
		import com.ibm.mobilefirstplatform.clientsdk.android.core.api.*;
import com.ibm.mobilefirstplatform.clientsdk.android.analytics.api.*;
import com.ibm.mobilefirstplatform.clientsdk.android.logger.api.*;
		```
		{: codeblock}

	- iOS

		L'SDK Swift è disponibile per iOS e watchOS.
		
		Importa i framework `BMSCore` e `BMSAnalytics` aggiungendo le seguenti istruzioni `import` all'inizio del tuo file di progetto `AppDelegate.swift`:
	
		```Swift
		import BMSCore
		import BMSAnalytics
		```
		{: codeblock}
   
	- Cordova
			
		Aggiungi il plugin Cordova eseguendo il seguente comando dalla directory root della tua applicazione Cordova:
	
		```Javascript
		cordova plugin add bms-core
		```
		{: codeblock}
   
	- Web
	
		Aggiungi il plugin web aggiungendo questo script nel file `index.html` dell'applicazione web:
	
		```Html
		<script src="bms-clientsdk-web-analytics/bmsanalytics.js"></script>
		```
		{: codeblock}

		O utilizzando il requirejs del programma di caricamento del modulo. Il nome utilizzato come riferimento API è lo stesso del nome dell'argomento (`BMSAnalytics`) utilizzato. 
	
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
		
4. Inizializza l'SDK client {{site.data.keyword.mobileanalytics_short}} nel tuo codice dell'applicazione per registrare l'analisi dell'utilizzo e le sessioni dell'applicazione, utilizzando il tuo valore [Chiave API](/docs/services/mobileanalytics/sdk.html#analytics-clientkey).	
	
	- Android
	
		```
		BMSClient.getInstance().initialize(getApplicationContext(), BMSClient.REGION_US_SOUTH); // Puoi modificare la regione
		Analytics.init(getApplication(), "your_app_name_here", "your_api_key_here", hasUserContext, collectLocation, Analytics.DeviceEvent.ALL);
		```
		{: codeblock}
	    
		Il parametro **bluemixRegion** specifica quale distribuzione {{site.data.keyword.Bluemix_notm}} stai utilizzando, ad esempio `BMSClient.REGION_US_SOUTH` e `BMSClient.REGION_UK`. 
	    <!-- , or `BMSClient.Region.Sydney`.-->
	    
		Imposta il valore per `hasUserContext` su **true** o **false**. Se false (valore predefinito), ogni dispositivo viene calcolato come un utente attivo.
		
		Imposta il valore per `collectLocation` su **true** o **false**. Se true, i dati di ubicazione del dispositivo saranno inviati come parte del log Appsession. 

	- iOS
	  
		Inizializza l'SDK client all'interno del tuo codice dell'applicazione per registrare l'analisi dell'utilizzo e le sessioni dell'applicazione, utilizzando il tuo valore [Chiave API](/docs/services/mobileanalytics/sdk.html#analytics-clientkey).
		
		```Swift
		BMSClient.sharedInstance.initialize(bluemixRegion: BMSClient.Region.usSouth) // Puoi modificare la regione
		Analytics.initialize(appName: "your_app_name_here", apiKey: "your_api_key_here", hasUserContext: false, collectLocation: true, deviceEvents: deviceEvents: .lifecycle, .network)
		```
		{: codeblock}
				
		Il parametro **bluemixRegion** specifica quale distribuzione IBM Cloud  stai utilizzando, ad esempio, `BMSClient.Region.usSouth` o `BMSClient.Region.unitedKingdom`.
		<!-- , or `BMSClient.REGION_SYDNEY`. -->
	 
		Imposta il valore per `hasUserContext` su **true** o **false**. Se false (valore predefinito), ogni dispositivo viene calcolato come un utente attivo.
		
		Imposta il valore per `collectLocation` su **true** o **false**. Se true, i dati di ubicazione del dispositivo saranno inviati come parte del log Appsession. 
	
	- Cordova
		
		Inizializza l'SDK client all'interno del tuo codice dell'applicazione per registrare l'analisi dell'utilizzo e le sessioni dell'applicazione, utilizzando il tuo valore [Chiave API](/docs/services/mobileanalytics/sdk.html#analytics-clientkey).
		
		```
		var appName = "your_app_name_here";
		var apiKey = "your_api_key_here";
		BMSClient.initialize(BMSClient.REGION_US_SOUTH); // Puoi modificare la regione
		BMSAnalytics.initialize(appName, apiKey, hasUserContext, collectLocation, [BMSAnalytics.ALL])
		```
		{: codeblock}
		
		Il parametro **bluemixRegion** specifica quale distribuzione IBM Cloud  stai utilizzando, ad esempio, `BMSClient.REGION_US_SOUTH` o `BMSClient.REGION_UK`.
		<!-- , or `BMSClient.REGION_SYDNEY`. -->
		Imposta il valore per `hasUserContext` su **true** o **false**. Se false (valore predefinito), ogni dispositivo viene calcolato come un utente attivo.
		
		Imposta il valore per `collectLocation` su **true** o **false**. Se true, i dati di ubicazione del dispositivo saranno inviati come parte del log Appsession.
    
	- Web
		
		Inizializza l'SDK client all'interno del tuo codice dell'applicazione per registrare l'analisi dell'utilizzo e le sessioni dell'applicazione, utilizzando il tuo valore [Chiave API](/docs/services/mobileanalytics/sdk.html#analytics-clientkey).
		
		```
		var appName = "your_app_name_here";
		var apiKey = "your_api_key_here";
		BMSAnalytics.Client.initialize(BMSAnalytics.Client.REGION_US_SOUTH);
		BMSAnalytics.initialize(appName,apiKey,hasUserContext,BMSAnalytics.DeviceEvents.ALL,instanceId);
		``` 
		{: codeblock}

		Il parametro `bluemixRegion` specifica quale distribuzione {{site.data.keyword.Bluemix_notm}} stai utilizzando, ad esempio `BMSAnalytics.Client.REGION_US_SOUTH` e `BMSAnalytics.Client.REGION_UK`.Imposta il valore per `hasUserContext` su `true` o `false`. Se false (valore predefinito), ogni dispositivo viene calcolato come un utente attivo.Imposta `instanceId` sul tuo instanceId del servizio, è una stringa alfanumerica che ottieni dall'URL del browser della tua istanza del servizio dopo la stringa "...mobile-analytics_Prod/"  e fino a "/". 

		Tieni presente che il nome che hai selezionato per la tua applicazione (`your_app_name_here`) visualizza la console {{site.data.keyword.mobileanalytics_short}} come il nome dell'applicazione. Il nome applicazione viene utilizzato come un filtro per cercare i log applicazione nel dashboard Quando utilizzi lo stesso nome applicazione su diverse piattaforme (ad esempio Android e iOS), puoi visualizzare tutti i log da tale applicazione sotto lo stesso nome, indipendentemente da quale sia la piattaforma dalla quale i log erano stati inviati.

5. Invia l'analisi di utilizzo registrata al servizio {{site.data.keyword.mobileanalytics_short}}. Un modo semplice per verificare la tua analisi consiste nell'eseguire il seguente codice quando viene avviata la tua applicazione:

	- Android
	
		Utilizza il metodo `Analytics.send()` per inviare i dati di analisi al server. Puoi inserire il metodo `Analytics.send()` ovunque nel metodo `onCreate` dell'attività principale nella tua applicazione Android o nell'ubicazione che ritieni più indicata per il tuo progetto. 
	
		Puoi inserire `Analytics.send()` ovunque.
	
	- iOS
	
		Utilizza il metodo `Analytics.send` per inviare i dati di analisi al server. Puoi inserire il metodo `Analytics.send` ovunque nel metodo `application(_:didFinishLaunchingWithOptions:)` del delegato della tua applicazione oppure in un'ubicazione che ritieni più adatta per il tuo progetto. 
	
	- Cordova
		
		Utilizza il metodo `BMSAnalytics.send` per inviare i dati di analisi al server. Inserisci il metodo `BMSAnalytics.send` in un'ubicazione che ritieni più adatta per il tuo progetto.
		
	- Web
		
		Utilizza il metodo `BMSAnalytics.send` per inviare i dati di analisi al server. Inserisci il metodo `BMSAnalytics.send` in un'ubicazione che ritieni più adatta per il tuo progetto. 
		
6. Completa l'argomento [Strumentazione della tua applicazione](/docs/services/mobileanalytics/sdk.html) per ulteriori informazioni sulle funzionalità {{site.data.keyword.mobileanalytics_short}}, come ad esempio [registrazione](/docs/services/mobileanalytics/sdk.html#app-monitoring-logger), [richieste di rete](/docs/services/mobileanalytics/sdk.html#network-requests), [registrazione dell'ubicazione](/docs/services/mobileanalytics/sdk.html#location-logging) e [analisi degli arresti anomali](/docs/services/mobileanalytics/sdk.html#report-crash-analytics).
	
7. Compila ed esegui l'applicazione sul tuo emulatore o sul tuo dispositivo.

8. Vai alla console {{site.data.keyword.mobileanalytics_short}} per visualizzare l'utilizzo delle analisi per la tua applicazione. Puoi inoltre monitorare la tua applicazione <!--[creating custom charts](app-monitoring.html#custom-charts),-->[configurando gli avvisi](/docs/services/mobileanalytics/app-monitoring.html#alerts) e [monitorando gli arresti anomali dell'applicazione](/docs/services/mobileanalytics/app-monitoring.html#monitor-app-crash).

# Link correlati
{: #rellinks notoc}

## SDK
{: #sdk notoc}
* [SDK Android ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-analytics){: new_window}  
* [SDK iOS ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-analytics){: new_window}
* [Cordova Plugin Core SDK ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.npmjs.com/package/bms-core){: new_window}
* [Web SDK ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-web-analytics/){: new_window}
## Guida di riferimento API 
{: #api notoc}
* [API REST ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://mobile-analytics-dashboard.{DomainName}/analytics-service/){:new_window}
