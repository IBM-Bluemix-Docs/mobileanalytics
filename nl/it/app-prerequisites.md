---

copyright:
 years: 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Prerequisiti
{: #prerequisites}
Ultimo aggiornamento: 18 gennaio 2018
{: .last-updated}


## Creazione di un'istanza del servizio Mobile Analytics 
{: #prerequisites_1}

1. Nel [Catalogo IBM Cloud](https://console.ng.bluemix.net/catalog/), fai clic su **Mobile** > **Mobile Analytics**.
2. Fornisci un nome al servizio.
3. Fai clic su **Crea**.
4. Scegli di collegare altre applicazioni esistenti o lascialo senza associazioni.


Puoi scegliere di creare un servizio associato o un sevizio senza associazioni. I servizi associati vengono collegati ad altre applicazioni IBM Cloud, mentre quelli senza associazioni sono autonomi e non collegati ad altre applicazioni. 

## Inizializzazione della tua applicazione
{: #prerequisites_app}

[Importa](/docs/services/mobileanalytics/available-client-sdk.html) e installa gli {{site.data.keyword.mobileanalytics_short}} [SDK client](/docs/services/mobileanalytics/install-client-sdk.html). Puoi facoltativamente utilizzare l'{{site.data.keyword.mobileanalytics_short}}API REST [ ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://mobile-analytics-dashboard.{DomainName}/analytics-service/){:new_window}.


###Importa le SDK client

Importa le SDK client e inizializzale con il seguente frammento di codice per registrare l'analisi dell'utilizzo:

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
		
		
Il tuo prossimo passo è [Instrumentare la tua applicazione](app-instrument.html) .


