---

copyright:
 years: 2018

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# SDK pour Mobile Analytics
{: #install-sdk}
Dernière mise à jour : 18 janvier 2018
{: .last-updated}

Actuellement, les logiciels SDK du client {{site.data.keyword.mobileanalytics_short}} sont disponibles pour Android, iOS, Cordova et Web. Vous trouverez ci-dessous des liens vers les logiciels SDK spécifiques aux différentes plateformes. 

Pour obtenir des informations détaillées sur l'installation et les concepts techniques, consultez le [document](install-client-sdk.html). 

{: shortdesc}

## Logiciels SDK pour Android

   Installation du [logiciel SDK du client Android](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-analytics)


## Logiciels SDK pour iOS

   Installation du [logiciel SDK du client iOS](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-analytics)

   
## Logiciels SDK pour Cordova

   Installation du [logiciel SDK du client Cordova](https://www.npmjs.com/package/bms-core)
   
## Logiciels SDK pour Web

   Installation du [logiciel SDK du client Web](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-web-analytics/)
   
**Remarque** : Pour le logiciel SDK Web, vous devez configurer votre instance de service Mobile Analytics pour autoriser un serveur d'applications. Indiquez l'URL de votre serveur d'applications via l'API REST de configuration de service de l'interface utilisateur Swagger. Les méthodes POST, GET, PUT et DELETE sont fournies pour les opérations CRUD de la configuration de service qui est une liste des URL autorisées. Pour obtenir (GET) et supprimer (DELETE) les configurations de votre instance de service, utilisez votre clé d'API. Pour créer et mettre à jour la configuration de service, utilisez les méthodes POST et PUT avec les URL autorisées répertoriées comme corps {"allowedUrls":["http://abc.com","https://www.xyz.com"]}. Si vous y accédez à partir d'un navigateur dans le même système que celui du serveur Web, indiquez "http://localhost" comme URL autorisée. 
