---

copyright:
 years: 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Instrumenta la tua applicazione 
{: #Instrument}
Ultimo aggiornamento: 18 gennaio 2018
{: .last-updated}

##Inizializza l'SDK client {{site.data.keyword.mobileanalytics_short}}  

Inizializza l'SDK client {{site.data.keyword.mobileanalytics_short}} nel tuo codice dell'applicazione per registrare l'analisi dell'utilizzo e le sessioni dell'applicazione, utilizzando il tuo valore [Chiave API](/docs/services/mobileanalytics/sdk.html#analytics-clientkey).	
	
- **Android**
	
```
		BMSClient.getInstance().initialize(getApplicationContext(), BMSClient.REGION_US_SOUTH); // Puoi modificare la regione
		Analytics.init(getApplication(), "your_app_name_here", "your_api_key_here", hasUserContext, collectLocation, Analytics.DeviceEvent.ALL);
```
		{: codeblock}
	    
Il parametro **bluemixRegion** specifica quale distribuzione {{site.data.keyword.Bluemix_notm}} stai utilizzando, ad esempio `BMSClient.REGION_US_SOUTH` e `BMSClient.REGION_UK`. 
	    
	    
Imposta il valore per `hasUserContext` su **true** o **false**. Se false (valore predefinito), ogni dispositivo viene calcolato come un utente attivo.
		
Imposta il valore per `collectLocation` su **true** o **false**. Se true, i dati di ubicazione del dispositivo saranno inviati come parte del log Appsession. 

- **iOS**
	  
Inizializza l'SDK client all'interno del tuo codice dell'applicazione per registrare l'analisi dell'utilizzo e le sessioni dell'applicazione, utilizzando il tuo valore [Chiave API](/docs/services/mobileanalytics/sdk.html#analytics-clientkey).
		
```Swift
		BMSClient.sharedInstance.initialize(bluemixRegion: BMSClient.Region.usSouth) // Puoi modificare la regione
		Analytics.initialize(appName: "your_app_name_here", apiKey: "your_api_key_here", hasUserContext: false, collectLocation: true, deviceEvents: deviceEvents: .lifecycle, .network)
```
		{: codeblock}
				
Il parametro **bluemixRegion** specifica quale distribuzione IBM Cloud  stai utilizzando, ad esempio, `BMSClient.Region.usSouth` o `BMSClient.Region.unitedKingdom`.
		
	 
Imposta il valore per `hasUserContext` su **true** o **false**. Se false (valore predefinito), ogni dispositivo viene calcolato come un utente attivo.
		
Imposta il valore per `collectLocation` su **true** o **false**. Se true, i dati di ubicazione del dispositivo saranno inviati come parte del log Appsession. 
	
- **Cordova**
		
Inizializza l'SDK client all'interno del tuo codice dell'applicazione per registrare l'analisi dell'utilizzo e le sessioni dell'applicazione, utilizzando il tuo valore [Chiave API](/docs/services/mobileanalytics/sdk.html#analytics-clientkey).
		
```
		var appName = "your_app_name_here";
		var apiKey = "your_api_key_here";
		BMSClient.initialize(BMSClient.REGION_US_SOUTH); // Puoi modificare la regione
		BMSAnalytics.initialize(appName, apiKey, hasUserContext, collectLocation, [BMSAnalytics.ALL])
```
		{: codeblock}
		
Il parametro **bluemixRegion** specifica quale distribuzione IBM Cloud  stai utilizzando, ad esempio, `BMSClient.REGION_US_SOUTH` o `BMSClient.REGION_UK`.
		
Imposta il valore per `hasUserContext` su **true** o **false**. Se false (valore predefinito), ogni dispositivo viene calcolato come un utente attivo.
		
Imposta il valore per `collectLocation` su **true** o **false**. Se true, i dati di ubicazione del dispositivo saranno inviati come parte del log Appsession.
    
- **Web**
		
Inizializza l'SDK client all'interno del tuo codice dell'applicazione per registrare l'analisi dell'utilizzo e le sessioni dell'applicazione, utilizzando il tuo valore [Chiave API](/docs/services/mobileanalytics/sdk.html#analytics-clientkey).
		
```
		var appName = "your_app_name_here";
		var apiKey = "your_api_key_here";
		BMSAnalytics.Client.initialize(BMSAnalytics.Client.REGION_US_SOUTH);
		BMSAnalytics.initialize(appName,apiKey,hasUserContext,BMSAnalytics.DeviceEvents.ALL,instanceId);
``` 
		{: codeblock}

Il parametro `bluemixRegion` specifica quale distribuzione {{site.data.keyword.Bluemix_notm}} stai utilizzando. Imposta il valore per `hasUserContext` su `true` o `false`. Se false (valore predefinito), ogni dispositivo viene calcolato come un utente attivo.Imposta `instanceId` sul tuo instanceId del servizio, è una stringa alfanumerica che ottieni dall'URL del browser della tua istanza del servizio dopo la stringa "...mobile-analytics_Prod/"  e fino a "/". 

**Nota**: il nome che hai selezionato per la tua applicazione (`your_app_name_here`) visualizza la console {{site.data.keyword.mobileanalytics_short}} come il nome dell'applicazione. Il nome applicazione viene utilizzato come un filtro per cercare i log applicazione nel dashboard Quando utilizzi lo stesso nome applicazione su diverse piattaforme (ad esempio Android e iOS), puoi visualizzare tutti i log da tale applicazione sotto lo stesso nome, indipendentemente da quale sia la piattaforma dalla quale i log erano stati inviati.

##Invia i dati dell'applicazione al servizio {{site.data.keyword.mobileanalytics_short}} 

Invia l'analisi di utilizzo registrata al servizio {{site.data.keyword.mobileanalytics_short}}. Un modo semplice per verificare la tua analisi consiste nell'eseguire il seguente codice quando viene avviata la tua applicazione:


- **Android**
	
Utilizza il metodo `Analytics.send()` per inviare i dati di analisi al server. Puoi inserire il metodo `Analytics.send()` ovunque nel metodo `onCreate` dell'attività principale nella tua applicazione Android o nell'ubicazione che ritieni più indicata per il tuo progetto. 
	
Puoi inserire `Analytics.send()` ovunque.
	
- **iOS**
	
Utilizza il metodo `Analytics.send` per inviare i dati di analisi al server. Puoi inserire il metodo `Analytics.send` ovunque nel metodo `application(_:didFinishLaunchingWithOptions:)` del delegato della tua applicazione oppure in un'ubicazione che ritieni più adatta per il tuo progetto. 
	
- **Cordova**
		
Utilizza il metodo `BMSAnalytics.send` per inviare i dati di analisi al server. Inserisci il metodo `BMSAnalytics.send` in un'ubicazione che ritieni più adatta per il tuo progetto.
		
- **Web**
		
Utilizza il metodo `BMSAnalytics.send` per inviare i dati di analisi al server. Inserisci il metodo `BMSAnalytics.send` in un'ubicazione che ritieni più adatta per il tuo progetto. 
		



Completa l'argomento [Strumentazione della tua applicazione](/docs/services/mobileanalytics/sdk.html) per ulteriori informazioni sulle funzionalità {{site.data.keyword.mobileanalytics_short}}, come ad esempio [registrazione](/docs/services/mobileanalytics/sdk.html#app-monitoring-logger), [richieste di rete](/docs/services/mobileanalytics/sdk.html#network-requests), [registrazione dell'ubicazione](/docs/services/mobileanalytics/sdk.html#location-logging) e [analisi degli arresti anomali](/docs/services/mobileanalytics/sdk.html#report-crash-analytics).


Il tuo prossimo passo è **Compila ed esegui l'applicazione sul tuo emulatore o sul tuo dispositivo**.
