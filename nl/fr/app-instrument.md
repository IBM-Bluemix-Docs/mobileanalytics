---

copyright:
 years: 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Instrumentation de votre application
{: #Instrument}
Dernière mise à jour : 18 janvier 2018
{: .last-updated}

##Initialisation du logiciel SDK du client {{site.data.keyword.mobileanalytics_short}} 

Initialisez le logiciel SDK du client {{site.data.keyword.mobileanalytics_short}} dans votre code d'application pour enregistrer les analyses de
l'utilisation et les sessions d'application, en utilisant la valeur de votre [Clé d'API](/docs/services/mobileanalytics/sdk.html#analytics-clientkey).	
	
- **Android**
	
```
		BMSClient.getInstance().initialize(getApplicationContext(), BMSClient.REGION_US_SOUTH); // You can change the region
		Analytics.init(getApplication(), "your_app_name_here", "your_api_key_here", hasUserContext, collectLocation, Analytics.DeviceEvent.ALL);
```
		{: codeblock}
	    
Le paramètre **bluemixRegion** spécifie le déploiement {{site.data.keyword.Bluemix_notm}} que vous utilisez, par exemple, `BMSClient.REGION_US_SOUTH` et `BMSClient.REGION_UK`.  
	    
	    
Définissez la valeur **true** ou **false** pour `hasUserContext`. Si la valeur est false
(valeur par défaut), chaque périphérique est comptabilisé comme un utilisateur actif.
		
Définissez la valeur **true** ou **false** pour `collectLocation`. Si la valeur est true, les données d'emplacement de périphérique seront envoyées dans le cadre du journal Appsession.  

- **iOS**
	  
Initialisez le logiciel SDK du client dans votre code d'application pour enregistrer les analyses d'utilisation et les sessions d'application
avec votre valeur de [clé d'API](/docs/services/mobileanalytics/sdk.html#analytics-clientkey).
		
```Swift
		BMSClient.sharedInstance.initialize(bluemixRegion: BMSClient.Region.usSouth) // You can change the region
		Analytics.initialize(appName: "your_app_name_here", apiKey: "your_api_key_here", hasUserContext: false, collectLocation: true, deviceEvents: deviceEvents: .lifecycle, .network)
```
		{: codeblock}
				
Le paramètre **bluemixRegion** spécifie le déploiement IBM Cloud que vous utilisez, par exemple `BMSClient.Region.usSouth` ou `BMSClient.Region.unitedKingdom`.
		
	 
Définissez la valeur **true** ou **false** pour `hasUserContext`. Si la valeur est false
(valeur par défaut), chaque périphérique est comptabilisé comme un utilisateur actif.
		
Définissez la valeur **true** ou **false** pour `collectLocation`. Si la valeur est true, les données d'emplacement de périphérique seront envoyées dans le cadre du journal Appsession.  
	
- **Cordova**
		
Initialisez le logiciel SDK du client dans votre code d'application pour enregistrer les analyses d'utilisation et les sessions d'application
avec votre valeur de [clé d'API](/docs/services/mobileanalytics/sdk.html#analytics-clientkey).
		
```
		var appName = "your_app_name_here";
		var apiKey = "your_api_key_here";
		BMSClient.initialize(BMSClient.REGION_US_SOUTH); // You can change the region
		BMSAnalytics.initialize(appName, apiKey, hasUserContext, collectLocation, [BMSAnalytics.ALL])
```
		{: codeblock}
		
Le paramètre **bluemixRegion** spécifie le déploiement IBM Cloud que vous utilisez, par exemple `BMSClient.REGION_US_SOUTH` ou `BMSClient.REGION_UK`.
		
Définissez la valeur **true** ou **false** pour `hasUserContext`. Si la valeur est false
(valeur par défaut), chaque périphérique est comptabilisé comme un utilisateur actif.
		
Définissez la valeur **true** ou **false** pour `collectLocation`. Si la valeur est true, les données d'emplacement de périphériques eront envoyées dans le cadre du journal Appsession. 
    
- **Web**
		
Initialisez le logiciel SDK du client dans votre code d'application pour enregistrer les analyses d'utilisation et les sessions d'application
avec votre valeur de [clé d'API](/docs/services/mobileanalytics/sdk.html#analytics-clientkey).
		
```
		var appName = "your_app_name_here";
		var apiKey = "your_api_key_here";
		BMSAnalytics.Client.initialize(BMSAnalytics.Client.REGION_US_SOUTH);
		BMSAnalytics.initialize(appName,apiKey,hasUserContext,BMSAnalytics.DeviceEvents.ALL,instanceId);
``` 
		{: codeblock}

Le paramètre `bluemixRegion` spécifie le déploiement {{site.data.keyword.Bluemix_notm}} que vous utilisez. Définissez la valeur `true` ou `false` pour `hasUserContext`. Si le paramètre est défini sur false (valeur par défaut), chaque périphérique est comptabilisé en tant qu'utilisateur actif. Affectez l'ID d'instance de votre service au paramètre `instanceId`. Il s'agit d'une chaîne alphanumérique que vous obtenez à partir de l'URL de navigateur de votre instance de service entre les chaînes "...mobile-analytics_Prod/"  et "/". 

**Remarque** : Le nom que vous sélectionnez pour votre application (`your_app_name_here`) s'affiche dans la console {{site.data.keyword.mobileanalytics_short}} comme nom d'application. Le nom d'application est utilisé pour filtrer la recherche des journaux d'application dans votre tableau de bord. Lorsque vous utilisez le même nom d'application sur plusieurs plateformes (par exemple, Android et iOS), tous les journaux issus de cette application s'affichent sous le même nom, quelle que soit la plateforme à partir de laquelle ils ont été envoyés.

##Envoi des données de l'application au service {{site.data.keyword.mobileanalytics_short}}

Envoyez des analyses d'utilisation enregistrées au service {{site.data.keyword.mobileanalytics_short}}. Une méthode simple pour tester votre analyse consiste à exécuter le code suivant au démarrage de l'application :


- **Android**
	
Utilisez la méthode `Analytics.send()` pour envoyer des données d'analyse au serveur. Vous pouvez placer la méthode `Analytics.send()` n'importe où dans la méthode `onCreate` de l'activité principale de votre application Android ou à l'emplacement le plus approprié pour votre projet. 
	
Vous pouvez insérer `Analytics.send()` n'importe où.
	
- **iOS**
	
Utilisez la méthode `Analytics.send` pour envoyer des données d'analyse au serveur. Vous pouvez placer la méthode `Analytics.send` n'importe où dans la méthode `application(_:didFinishLaunchingWithOptions:)` de votre délégué d'application ou à l'emplacement le plus approprié pour votre projet. 
	
- **Cordova**
		
Utilisez la méthode `BMSAnalytics.send` pour envoyer des données d'analyse au serveur. Placez la méthode `BMSAnalytics.send` dans le meilleur emplacement pour votre projet.
		
- **Web**
		
Utilisez la méthode `BMSAnalytics.send` pour envoyer des données d'analyse au serveur. Placez la méthode `BMSAnalytics.send` dans le meilleur emplacement pour votre projet. 
		



Lisez la rubrique [Instrumentation de votre application](/docs/services/mobileanalytics/sdk.html) pour connaître les fonctionnalités {{site.data.keyword.mobileanalytics_short}} supplémentaires, telles que la [consignation ](/docs/services/mobileanalytics/sdk.html#app-monitoring-logger), les [demandes de réseau](/docs/services/mobileanalytics/sdk.html#network-requests), [la consignation des emplacements](/docs/services/mobileanalytics/sdk.html#location-logging) et l'[analyse des pannes](/docs/services/mobileanalytics/sdk.html#report-crash-analytics).


L'étape suivante consiste à **compiler et exécuter l'application sur votre émulateur ou périphérique**.
