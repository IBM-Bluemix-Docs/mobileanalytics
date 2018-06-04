---

copyright:
 years: 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Prérequis
{: #prerequisites}
Dernière mise à jour : 18 janvier 2018
{: .last-updated}


## Création d'une instance de service Mobile Analytics
{: #prerequisites_1}

1. Dans le [Catalogue IBM Cloud](https://console.ng.bluemix.net/catalog/), cliquez sur **Mobile** > **Mobile Analytics**. 
2. Indiquez un nom de service. 
3. Cliquez sur **Créer**. 
4. Choisissez de vous connecter à d'autres applications existantes ou laissez le service non lié.


Vous pouvez choisir de créer un service lié ou un service non lié. Les services liés sont connectés à d'autres applications IBM Cloud, alors que les services non liés sont autonomes et ne sont pas connectés à d'autres applications.  

## Initialisation de votre application
{: #prerequisites_app}

[Importez](/docs/services/mobileanalytics/available-client-sdk.html) et installez les logiciels [SDK du client](/docs/services/mobileanalytics/install-client-sdk.html) {{site.data.keyword.mobileanalytics_short}}. Si vous le souhaitez, vous pouvez utiliser l'[API REST![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://mobile-analytics-dashboard.{DomainName}/analytics-service/){:new_window} de {{site.data.keyword.mobileanalytics_short}}. 


###Importez les logiciels SDK du client

Importez les logiciels SDK du client et initialisez-les avec le fragment de code suivant pour enregistrer les analyses de l'utilisation :

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
		
		
L'étape suivante consiste à [instrumenter votre application](app-instrument.html). 


