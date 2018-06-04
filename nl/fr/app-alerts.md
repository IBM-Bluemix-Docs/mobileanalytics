---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-06"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Définition d'alertes
{: #alerts}

## Définition d'alertes avec Mobile Analytics 

Vous pouvez définir des seuils dans les définitions d'alerte dans la console {{site.data.keyword.mobileanalytics_short}} pour un meilleur contrôle
de vos activités.

Vous pouvez configurer des seuils qui, s'ils sont dépassés, déclenchent des alertes et entraînent l'envoi de notifications au moniteur de la console
{{site.data.keyword.mobileanalytics_short}}. Les alertes déclenchées peuvent être visualisées dans la console ou gérées par un webhook
personnalisé. <!-- This feature provides a proactive means of detecting app log errors, server log errors, extended periods of network latency, and authentication failures.--> Cette fonction permet de détecter de façon proactive les erreurs dans les journaux d'application, ainsi que les erreurs dans les journaux serveur signalant
des pannes d'application. La mise en place d'alertes et de seuils réactifs vous évite d'avoir à parcourir vos données et à définir des seuils avec un niveau de granularité élevé.

## Création d'une définition d'alerte pour les journaux d'application
{: #alert-def-client-logs notoc}

Vous pouvez créer une définition d'alerte qui repose sur des journaux d'application.

Dans cet exemple, vous utilisez des données de journal d'application pour créer une définition d'alerte. L'alerte surveille tous les journaux
d'application qui
ont été reçus au cours des 5 dernières minutes, et procède à une vérification toutes les 5 minutes, jusqu'à ce que la définition d'alerte soit
désactivée ou supprimée. Une alerte est déclenchée pour chaque périphérique qui a envoyé au moins 3 journaux d'erreurs d'application avec le même nom et la même version
d'application.

1. Dans la console {{site.data.keyword.mobileanalytics_short}}, cliquez sur **Définitions** pour accéder à la page Définitions
d'alerte.
2. Cliquez sur **Créer une alerte** pour créer une alerte.
3. Indiquez les valeurs suivantes :
	* Nom de l'alerte : Alerte pour les journaux d'application
	* Message : Alerte de message d'erreur
	* Fréquence des requêtes : 5 minutes
	* Type d'événement : Journaux d'application
		* Propriété : Niveau de journalisation
			* Valeur : Erreur
			* Seuil
				* Type de seuil : Total pour instance d'application

					**Remarque** : si vous choisissez l'option Moyenne pour application, la moyenne de journaux d'application est calculée en
fonction du nombre de
périphériques. Par exemple, si vous possédez deux périphériques et que l'un d'eux envoie six journaux d'application tandis que l'autre en envoie trois, la
moyenne est de
4,5 journaux d'application.
				* Opérateur : Est supérieur ou égal à 3
	<!-- insert alert definition tab image? -->

4. Cliquez sur **Suivant** et indiquez la valeur suivante :
	* Méthode : Console Analytics uniquement

		**Remarque** : Choisissez l'option Console Analytics et publication sur le réseau si vous souhaitez envoyer
également un message POST avec un contenu JSON à votre URL personnalisée. Les zones suivantes sont disponibles lorsque vous choisissez cette option :
		* Adresse URL de publication sur le réseau
        * En-têtes
        * Type d'authentification
5. Cliquez sur **Sauvegarder**.

Vous avez créé une définition d'alerte qui déclenche une alerte toutes les 5 minutes si le nombre de journaux d'erreurs d'application est supérieur ou
égal
à 3.

## Création d'une définition d'alerte pour les pannes d'application
{: #alert-def-app-crash notoc}

Vous pouvez créer une définition d'alerte basée sur les pannes d'application.

Dans cet exemple, vous utilisez des données de panne d'application pour créer une définition d'alerte. L'alerte surveille toutes les pannes d'application qui se sont produites au cours des 2 dernières minutes, et continue la vérification toutes les 2 minutes, jusqu'à ce que la définition d'alerte soit désactivée ou supprimée. Une alerte est déclenchée pour chaque application qui est tombée en panne au moins 5 fois. Pour plus d'informations sur les pannes d'application, voir [Pannes d'application](#app_crash).

1. Dans la console {{site.data.keyword.mobileanalytics_short}}, cliquez sur **Définitions** pour afficher la page
Définitions d'alertes.
2. Cliquez sur **Créer une alerte**.
3. Indiquez les valeurs suivantes :
	* Nom d'alerte : Alerte pour les pannes d'application
	* Message : Alerte de panne d'application
	* Fréquence des requêtes : Pannes d'application
		* Fréquence des requêtes : 2 minutes
	* Type d'événement : Pannes d'application
		* Nom d'application : N'importe quelle application
		* Version d'application : N'importe quelle version
    * Seuil
      * Type de seuil : Nombre de pannes
      * Opérateur : Est supérieur ou égal à 5
4. Cliquez sur l'onglet **Méthode de distribution** et indiquez la valeur suivante :
  * Méthode : Console Analytics uniquement

    **Remarque** : Choisissez l'option **Console Analytics et publication sur le réseau** si vous souhaitez envoyer également un message POST avec un contenu JSON à votre URL personnalisée. Les zones suivantes sont disponibles lorsque vous choisissez cette option :
      * Adresse URL de publication sur le réseau (obligatoire)
      * En-têtes (facultative)
      * Type d'authentification (obligatoire)
5. Cliquez sur **Sauvegarder**.

## Gestion des définitions d'alerte
{: #managing-alert-definitions notoc}

Dans cet exemple, vous gérez vos définitions d'alerte à partir de la page Gestion des alertes.

1. Dans la console {{site.data.keyword.mobileanalytics_short}}, cliquez sur **Journaux**. Cette action ouvre la page
Journaux des alertes.
2. Facultatif : Sélectionnez ou désélectionnez la case à cocher située sous la colonne **Activé** pour activer ou désactiver une définition d'alerte donnée.
3. Facultatif : Cliquez sur l'icône **Dupliquer** si vous souhaitez créer une copie d'une définition d'alerte et modifier certaines valeurs.
4. Facultatif : Cliquez sur l'icône **Crayon** si vous souhaitez éditer une définition d'alerte.
5. Facultatif : Cliquez sur l'icône **Corbeille** si vous souhaitez supprimer une définition d'alerte.

## Affichage des détails d'alerte
{: #viewing-alert-details notoc}

Dans cet exemple, vous affichez les détails de vos alertes déclenchées à partir de la page Journal des alertes.

1. Dans la console {{site.data.keyword.mobileanalytics_short}}, cliquez sur **Journaux**. Cette action permet d'afficher la page Journal des alertes.
2. Cliquez sur l'icône **+** pour n'importe laquelle des alertes. Cette action permet d'afficher les sections **Définition d'alerte** et **Instances d'alerte**.

    **Remarque** : Si la définition d'alerte correspondante n'a pas été supprimée ou modifiée, vous pouvez l'éditer en cliquant sur **Editer une alerte**. Sinon, le bouton **Editer une alerte** n'est pas disponible et le message suivant s'affiche :

    `Depuis, cette définition d'alerte a été modifiée ou supprimée. `

3. Facultatif : Sélectionnez une alerte et cliquez sur l'icône **Corbeille** pour la supprimer.

