---

copyright:
  years: 2016, 2017
lastupdated: "2017-07-14"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Tutoriel de mise en route

{: #gettingstartedtemplate}

{{site.data.keyword.mobileanalytics_full}} fournit aux développeurs, aux administrateurs informatiques et aux parties prenantes des informations relatives aux performances et à l'utilisation de leurs applications mobiles. {{site.data.keyword.mobileanalytics_short}} vous permet :

* De surveiller les performances et l'utilisation de toutes vos applications depuis votre bureau ou votre tablette. 
* D'identifier rapidement les tendances et les anomalies, d'accéder aux détails pour résoudre les problèmes et de déclencher des alertes lorsque des mesures clés dépassent des seuils critiques. 
{: shortdesc}

Pour que le service {{site.data.keyword.mobileanalytics_short}} soit rapidement opérationnel, procédez comme suit :

1. Après avoir créé une instance
<!--[create an instance](https://console.{DomainName}/docs/services/reqnsi.html#req_instance)-->du service
{{site.data.keyword.mobileanalytics_short}}, vous pouvez accéder à la console de {{site.data.keyword.mobileanalytics_short}}
en cliquant sur votre vignette dans la section **Services** du tableau de bord {{site.data.keyword.Bluemix}}. Une option **Mode démonstration** est disponible dans la console {{site.data.keyword.mobileanalytics_short}}, qui permet d'afficher les vues et les graphiques avec des *données de démonstration*. Le mode démonstration est le mode par défaut de la console lorsqu'elle est lancée pour la première fois après l'instanciation du service. Lorsque vous disposez de vos propres applications et données d'analyse alimentées dans le service, vous pouvez *désactiver* le mode démonstration pour afficher les données de vos applications dans les différents graphiques. La console {{site.data.keyword.mobileanalytics_short}} est accessible en lecture seule lorsque le mode démonstration est activé et vous ne pouvez donc pas créer de nouvelles définitions d'alerte.

2. Installez les [logiciels SDK du client](/docs/services/mobileanalytics/install-client-sdk.html) {{site.data.keyword.mobileanalytics_short}}. Si vous le souhaitez, vous pouvez utiliser l'[API REST![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://mobile-analytics-dashboard.{DomainName}/analytics-service/){:new_window} de {{site.data.keyword.mobileanalytics_short}}. 
	
	- Configuration de service de l'application Web
	
		Pour le logiciel SDK Web, afin de configurer votre instance de service pour qu'elle autorise un serveur d'applications, vous devez indiquer l'URL de votre serveur d'applications via l'API REST de configuration de service de l'interface utilisateur Swagger. Les méthodes POST, GET, PUT et DELETE sont fournies pour les opérations CRUD de la configuration de service qui est une liste des URL autorisées. Pour obtenir (GET) et supprimer (DELETE) les configurations de votre instance de service, utilisez votre clé d'API. Pour créer et mettre à jour la configuration de service, utilisez les méthodes POST et PUT avec les URL autorisées répertoriées comme corps {"allowedUrls":["http://abc.com","https://www.xyz.com"]}. Si vous y accédez à partir d'un navigateur dans le même système que celui du serveur Web, indiquez "http://localhost" comme URL autorisée. 

3. Importez les logiciels SDK client et initialisez-les avec le fragment de code suivant pour enregistrer les analyses de l'utilisation :

	- Android
	
		Ajoutez les instructions `import` suivantes au début de votre fichier de projet :
		
		```
		import com.ibm.mobilefirstplatform.clientsdk.android.core.api.*;
import com.ibm.mobilefirstplatform.clientsdk.android.analytics.api.*;
import com.ibm.mobilefirstplatform.clientsdk.android.logger.api.*;
		```
		{: codeblock}

	- iOS

		Le logiciel SDK de Swift est disponible pour iOS et watchOS.
		
		Importez les infrastructures `BMSCore` et `BMSAnalytics` en ajoutant les instructions `import` suivantes au début de votre fichier de projet `AppDelegate.swift` :
	
		```Swift
		import BMSCore
		import BMSAnalytics
	```
		{: codeblock}
   
	- Cordova
			
		Ajoutez le plug-in Cordova en exécutant la commande suivante depuis le répertoire racine de votre application Cordova :
	
		```Javascript
		cordova plugin add bms-core
	```
		{: codeblock}
   
	- Web
	
		Ajoutez le plug-in Web en ajoutant ce script dans le fichier `index.html` de l'application Web :
	
		```Html
		<script src="bms-clientsdk-web-analytics/bmsanalytics.js"></script>
		```
		{: codeblock}

		Ou en utilisant le chargeur de module requirejs. Le nom utilisé comme API de référence est identique au nom de l'argument (`BMSAnalytics`) utilisé.  
	
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
		
4. Initialisez le logiciel SDK client {{site.data.keyword.mobileanalytics_short}} dans votre code d'application pour enregistrer les analyses de
l'utilisation et les sessions d'application, en utilisant la valeur de votre [Clé d'API](/docs/services/mobileanalytics/sdk.html#analytics-clientkey).	
	
	- Android
	
		```
		BMSClient.getInstance().initialize(getApplicationContext(), BMSClient.REGION_US_SOUTH); // You can change the region
		Analytics.init(getApplication(), "your_app_name_here", "your_api_key_here", hasUserContext, collectLocation, Analytics.DeviceEvent.ALL);
```
		{: codeblock}
	    
		Le paramètre **bluemixRegion** spécifie le déploiement {{site.data.keyword.Bluemix_notm}} que vous utilisez, par exemple, `BMSClient.REGION_US_SOUTH` et `BMSClient.REGION_UK`.  
	    <!-- , or `BMSClient.Region.Sydney`.-->
	    
		Définissez la valeur **true** ou **false** pour `hasUserContext`. Si la valeur est false
(valeur par défaut), chaque périphérique est comptabilisé comme un utilisateur actif.
		
		Définissez la valeur **true** ou **false** pour `collectLocation`. Si la valeur est true, les données d'emplacement de périphérique seront envoyées dans le cadre du journal Appsession.  

	- iOS
	  
		Initialisez le logiciel SDK du client dans votre code d'application pour enregistrer les analyses d'utilisation et les sessions d'application
avec votre valeur de [clé d'API](/docs/services/mobileanalytics/sdk.html#analytics-clientkey).
		
		```Swift
		BMSClient.sharedInstance.initialize(bluemixRegion: BMSClient.Region.usSouth) // You can change the region
		Analytics.initialize(appName: "your_app_name_here", apiKey: "your_api_key_here", hasUserContext: false, collectLocation: true, deviceEvents: deviceEvents: .lifecycle, .network)
		```
		{: codeblock}
				
		Le paramètre **bluemixRegion** spécifie le déploiement IBM Cloud que vous utilisez, par exemple `BMSClient.Region.usSouth` ou `BMSClient.Region.unitedKingdom`.
		<!-- , or `BMSClient.REGION_SYDNEY`. -->
	 
		Définissez la valeur **true** ou **false** pour `hasUserContext`. Si la valeur est false
(valeur par défaut), chaque périphérique est comptabilisé comme un utilisateur actif.
		
		Définissez la valeur **true** ou **false** pour `collectLocation`. Si la valeur est true, les données d'emplacement de périphérique seront envoyées dans le cadre du journal Appsession.  
	
	- Cordova
		
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
		<!-- , or `BMSClient.REGION_SYDNEY`. -->
		Définissez la valeur **true** ou **false** pour `hasUserContext`. Si la valeur est false
(valeur par défaut), chaque périphérique est comptabilisé comme un utilisateur actif.
		
		Définissez la valeur **true** ou **false** pour `collectLocation`. Si la valeur est true, les données d'emplacement de périphérique seront envoyées dans le cadre du journal Appsession. 
    
	- Web
		
		Initialisez le logiciel SDK du client dans votre code d'application pour enregistrer les analyses d'utilisation et les sessions d'application
avec votre valeur de [clé d'API](/docs/services/mobileanalytics/sdk.html#analytics-clientkey).
		
		```
		var appName = "your_app_name_here";
		var apiKey = "your_api_key_here";
		BMSAnalytics.Client.initialize(BMSAnalytics.Client.REGION_US_SOUTH);
		BMSAnalytics.initialize(appName,apiKey,hasUserContext,BMSAnalytics.DeviceEvents.ALL,instanceId);
``` 
		{: codeblock}

		Le paramètre `bluemixRegion` spécifie le déploiement {{site.data.keyword.Bluemix_notm}} que vous utilisez, par exemple, `BMSAnalytics.Client.REGION_US_SOUTH` et `BMSAnalytics.Client.REGION_UK`. Définissez la valeur `true` ou `false` pour `hasUserContext`. Si le paramètre est défini sur false (valeur par défaut), chaque périphérique est comptabilisé en tant qu'utilisateur actif. Affectez l'ID d'instance de votre service au paramètre `instanceId`. Il s'agit d'une chaîne alphanumérique que vous obtenez à partir de l'URL de navigateur de votre instance de service entre les chaînes "...mobile-analytics_Prod/"  et "/". 

		Notez que le nom que vous sélectionnez pour votre application (`your_app_name_here`) s'affiche dans la console {{site.data.keyword.mobileanalytics_short}} comme nom d'application. Le nom d'application est utilisé pour filtrer la recherche des journaux d'application dans votre tableau de bord. Lorsque vous utilisez le même nom d'application sur plusieurs plateformes (par exemple, Android et iOS), tous les journaux issus de cette application s'affichent sous le même nom, quelle que soit la plateforme à partir de laquelle ils ont été envoyés.

5. Envoyez des analyses d'utilisation enregistrées au service {{site.data.keyword.mobileanalytics_short}}. Une méthode simple pour tester votre analyse consiste à exécuter le code suivant au démarrage de l'application :

	- Android
	
		Utilisez la méthode `Analytics.send()` pour envoyer des données d'analyse au serveur. Vous pouvez placer la méthode `Analytics.send()` n'importe où dans la méthode `onCreate` de l'activité principale de votre application Android ou à l'emplacement le plus approprié pour votre projet. 
	
		Vous pouvez insérer `Analytics.send()` n'importe où.
	
	- iOS
	
		Utilisez la méthode `Analytics.send` pour envoyer des données d'analyse au serveur. Vous pouvez placer la méthode `Analytics.send` n'importe où dans la méthode `application(_:didFinishLaunchingWithOptions:)` de votre délégué d'application ou à l'emplacement le plus approprié pour votre projet. 
	
	- Cordova
		
		Utilisez la méthode `BMSAnalytics.send` pour envoyer des données d'analyse au serveur. Placez la méthode `BMSAnalytics.send` dans le meilleur emplacement pour votre projet.
		
	- Web
		
		Utilisez la méthode `BMSAnalytics.send` pour envoyer des données d'analyse au serveur. Placez la méthode `BMSAnalytics.send` dans le meilleur emplacement pour votre projet. 
		
6. Lisez la rubrique [Instrumentation de votre application](/docs/services/mobileanalytics/sdk.html) pour connaître les fonctionnalités {{site.data.keyword.mobileanalytics_short}} supplémentaires, telles que la [consignation ](/docs/services/mobileanalytics/sdk.html#app-monitoring-logger), les [demandes de réseau](/docs/services/mobileanalytics/sdk.html#network-requests), [la consignation des emplacements](/docs/services/mobileanalytics/sdk.html#location-logging) et l'[analyse des pannes](/docs/services/mobileanalytics/sdk.html#report-crash-analytics).
	
7. Compilez et exécutez l'application sur votre émulateur ou périphérique.

8. Accédez à la console {{site.data.keyword.mobileanalytics_short}} pour voir l'analyse de l'utilisation de votre application. Vous pouvez également surveiller votre application en <!--[creating custom charts](app-monitoring.html#custom-charts),-->[définissant des alertes](/docs/services/mobileanalytics/app-monitoring.html#alerts) et en [surveillant les pannes de l'application](/docs/services/mobileanalytics/app-monitoring.html#monitor-app-crash). 

# Liens connexes
{: #rellinks notoc}

## Logiciel SDK
{: #sdk notoc}
* [Logiciel SDK Android ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-analytics){: new_window}  
* [Logiciel SDK iOS ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-analytics){: new_window}
* [Logiciel SDK du plug-in Core Cordova ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.npmjs.com/package/bms-core){: new_window}
* [Logiciel SDK Web ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-web-analytics/){: new_window}
## Référence d'API
{: #api notoc}
* [API REST ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://mobile-analytics-dashboard.{DomainName}/analytics-service/){:new_window}
