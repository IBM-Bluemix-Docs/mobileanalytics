---

copyright:
  years: 2015, 2017
lastupdated: "2017-01-13"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

#Installa l'SDK
{: #mobileanalytics_sdk}

## Installa le SDK client {{site.data.keyword.mobileanalytics_short}} 

Le SDK client {{site.data.keyword.mobileanalytics_short}}
sono attualmente disponibili per Android, iOS, WatchOS, Cordova e Web.
{: shortdesc}

## Installazione dell'SDK client Android
{: #install-sdk-android}

[![Maven Central](https://maven-badges.herokuapp.com/maven-central/com.ibm.mobilefirstplatform.clientsdk.android/analytics/badge.svg)](https://maven-badges.herokuapp.com/maven-central/com.ibm.mobilefirstplatform.clientsdk.android/analytics)

L'SDK client {{site.data.keyword.mobileanalytics_short}} viene distribuito con Gradle, un gestore dipendenze per i progetti Android. Gradle scarica automaticamente le risorse dai repository e le rende disponibili alla tua applicazione Android.

1. Crea un progetto [Android Studio ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://developer.android.com/sdk/index.html){: new_window} o apri un progetto esistente.

2. Apri il file `build.gradle` che si trova nel tuo **modulo dell'applicazione**.

  **Suggerimento**: il tuo progetto Android potrebbe avere due file `build.gradle`: uno per il progetto e uno per il modulo dell'applicazione. Accertati di utilizzare il file del **modulo dell'applicazione**.

3. Trova la sezione `Dependencies` del file `build.gradle` e aggiungi una dipendenza di compilazione per l'SDK client {{site.data.keyword.mobileanalytics_short}}. La tua istruzione relativa ai repository dovrebbe essere simile a questo esempio di codice:

	```
      dependencies {
        compile 'com.ibm.mobilefirstplatform.clientsdk.android:analytics:1.+'
        compile 'com.google.android.gms:play-services-location:10.0.1'
    	// altre dipendenze  
      }
  	```
  	{: codeblock}
	
	La prima dipendenza è per l'SDK client del servizio Mobile Analytics e la seconda per la registrazione dell'ubicazione lato client. La seconda dipendenza è necessaria solo se abiliti la raccolta dell'ubicazione lato client.
    	

4. Sincronizza il tuo progetto con Gradle facendo clic su **Tools &gt; Android &gt; Sync Project with Gradle Files**.

5. Apri il file `AndroidManifest.xml` del tuo progetto Android. Puoi trovare questo file in **app > manifests**. Aggiungi l'autorizzazione di accesso internet e all'ubicazione nell'elemento `<manifest>`:

	```
	 <uses-permission android:name="android.permission.INTERNET" />
	 <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION"/>
	 <uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION"/>
	```
   Se stai utilizzando una versione SDK maggiore di >= 1.2  devi inserire questa parte nell'elemento `<application>` del file `AndroidManifest.xml`.
   	
    ```
	 <activity
            android:name="com.ibm.mobilefirstplatform.clientsdk.android.ui.UIActivity"
            android:label="@string/app_name"
            android:launchMode="singleTask">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
	```
   	{: codeblock}
   

Hai ora installato l'SDK client Android. Successivamente, [importa e inizializza](sdk.html#initalize-ma-sdk) l'SDK client Analytics.   

## Installazione dell'SDK Swift
{: #installing-sdk-ios}

![Compatibile con CocoaPods](https://img.shields.io/cocoapods/v/BMSAnalytics.svg)

L'SDK {{site.data.keyword.mobileanalytics_full}} ti consente di strumentare la tua applicazione mobile. L'SDK Swift è disponibile per iOS e watchOS.

### Prima di cominciare
{: #before-you-begin-ios notoc}

Accertati di avere impostato correttamente Xcode. Per informazioni su come impostare il tuo ambiente di sviluppo iOS, visita il [sito Web Apple Developer ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://developer.apple.com/support/xcode/){: new_window}. Leggi le informazioni sui [requisiti Xcode ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-analytics/tree/development#requirements){: new_window} per Client SDK Swift Analytics.

#### Abilita l'API di ubicazione 
Per abilitare l'API di ubicazione in modo che funzioni correttamente, devi aggiungere una proprietà nel file Info.plist nella cartella del progetto della tua applicazione ossia  `Privacy - Location Usage Description`  e come valore aggiunto, fornisci una giustificazione appropriata per l'aggiunta dell'API di ubicazione come ad esempio "The app requires location service to be enabled" o qualcosa di simile.

L'SDK {{site.data.keyword.mobileanalytics_short}} viene distribuito con [CocoaPods ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://cocoapods.org/){: new_window} e [Carthage ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://github.com/Carthage/Carthage#getting-started){: new_window}, che sono dei gestori delle dipendenze per i progetti Cocoa. CocoaPods e Carthage scaricano automaticamente le risorse dai repository e le rendono disponibili alla tua applicazione. Seleziona CocoaPods o Carthage:

#### CocoaPods
{: #cocoapods notoc}

1. Segui le istruzioni [{{site.data.keyword.Bluemix_notm}} Mobile Services Swift SDK ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-analytics/tree/development#cocoapods){: new_window} su GitHub per installare `BMSAnalytics` utilizzando Cocoapods e aggiungerlo al tuo Podfile. 
	
2. Dopo aver installato l'SDK client iOS, [importa e inizializza](sdk.html#initalize-ma-sdk) l'SDK client Analytics.   

#### Carthage
{: #carthage notoc}

Se non stai utilizzando CocoaPods, puoi aggiungere i framework al tuo progetto utilizzando [Carthage ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://github.com/Carthage/Carthage#if-youre-building-for-ios-tvos-or-watchos){: new_window}.

1. Segui le [istruzioni di installazione Carthage ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-analytics/tree/development#carthage){: new_window} in GitHub per installare `BMSAnalytics`.

2. Dopo aver installato l'SDK client iOS, [importa e inizializza](sdk.html#initalize-ma-sdk) l'SDK client Analytics.


## Installazione del plugin Cordova
{: #installing-sdk-cordova}

Il plug-in Cordova {{site.data.keyword.mobileanalytics_full}} ti consente di strumentare la tua applicazione mobile. 

1. Crea un progetto [Cordova ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://cordova.apache.org/#getstarted){: new_window} o apri un progetto esistente.

2. Aggiungi le piattaforme Android e iOS alla tua applicazione Cordova. Esegui uno o entrambi i seguenti comandi dalla riga di comando. Al momento, è supportata la CLI Cordova V6.3.0 o precedente:
   
   Android:

	 ```
	 cordova platform add android@5.2.2
	 ```
	 {: codeblock}
	
   iOS:
   	
	```
	cordova platform add ios
	```
   {: codeblock}
	
3. Se hai aggiunto la piattaforma Android, devi aggiungere il livello API minimo supportato al file `config.xml` della tua applicazione Cordova. Apri il file `config.xml` e aggiungi la seguente riga all'elemento `<platform name="android">`:

	```
	<platform name="android">  
  	 <preference name="android-minSdkVersion" value="15"/>
  	<preference name="android-targetSdkVersion" value="23"/>
  	 <!-- add minimum and target Android API level declaration -->
  	</platform>
	```
   {: codeblock}

 Il valore *minSdkVersion* deve essere alla versione `15` o superiore. Fai riferimento alla [Android Platform Guide ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://cordova.apache.org/docs/en/latest/guide/platforms/android/){: new_window} per restare aggiornato sulla *targetSdkVersion* supportata per l'SDK Android.

4. Se hai aggiunto il sistema operativo iOS, aggiorna l'elemento `<platform name="ios">` con una dichiarazione di destinazione:

	```
	<platform name="ios">
    <preference name="deployment-target" value="8.0"/>
     <!-- add deployment target declaration -->
  	</platform>
	```
	{: codeblock}

5. Aggiungi il plugin `bms-core`.
 	
	 ```
	 cordova plugin add bms-core
	 ```
	 {: codeblock}

6. Verifica che il plug-in sia stato installato correttamente eseguendo il seguente comando:
	
	```
	cordova plugin list
	```
	{: codeblock}
	
7. [Configure your Android and iOS environment ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.npmjs.com/package/bms-core#4-configuring-your-platform){: new_window}.

8. Hai ora installato il plug-in Cordova e configurato i tuoi ambienti. Successivamente, [importa e inizializza](sdk.html#initalize-ma-sdk) l'SDK client Analytics.

#### Abilitazione del servizio di ubicazione prima della versione del plugin cordova bms-core (>2.4.+).
9. Per l'applicazione Cordova-ios per abilitare l'API di ubicazione in modo che funzioni correttamente, devi aggiungere una proprietà nel file Info.plist nella cartella del progetto della tua applicazione ossia  `Privacy - Location Usage Description`  e come valore aggiunto, fornisci una giustificazione appropriata per l'aggiunta dell'API di ubicazione come ad esempio "The app requires location service to be enabled" o qualcosa di simile.

10. Per l'applicazione Cordova-android per abilitare l'API di ubicazione in modo che funzioni correttamente inserisci quanto segue nel file AndroidManifest.xml dell'applicazione.
	```
	 <uses-permission android:name="android.permission.INTERNET" />
	 <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION"/>
	 <uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION"/>
	```
	{: codeblock}
	
   Dopodiché devi inserire la seguente parte nell'elemento `<application>` del file `AndroidManifest.xml`.
   	```
	 <activity
            android:name="com.ibm.mobilefirstplatform.clientsdk.android.ui.UIActivity"
            android:label="@string/app_name"
            android:launchMode="singleTask">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
	```
	{: codeblock}

## Installazione del plugin Web
{: #web-sdk-cordova}

L'SDK {{site.data.keyword.mobileanalytics_full}} ti abilita a instrumentare la tua applicazione web.

1. Assicurati di avere un server web e un browser configurati (ad es. Chrome, Firefox) .
2. Crea una nuova applicazione web o utilizzane una esistente e inserisci questo [WebSDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-web-analytics/) all'interno del tuo progetto in modo che sia accessibile dal codice dell'applicazione.
3. Aggiungi il plugin web aggiungendo questo script nel file `index.html` dell'applicazione web:
	
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
	  ```
	{: codeblock}




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
