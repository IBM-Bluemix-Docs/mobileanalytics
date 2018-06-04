---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-06"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Surveillance de pannes d'application
{: #monitor-app-crash}

Vous pouvez consulter des informations sur les pannes de votre application dans la console
{{site.data.keyword.mobileanalytics_short}} pour mieux surveiller vos applications et résoudre leurs incidents.

## Surveillance des pannes d'application
{: #app-crash notoc}

Sur la page **Pannes**, le tableau **Présentation des pannes** affiche les colonnes de données suivantes :

* Application : Nom d'application
* Pannes : Nombre total de pannes pour cette application
* Nombre total d'utilisations : Nombre total de fois qu'un utilisateur ouvre et ferme cette application
* Taux de pannes : Pourcentage de pannes par utilisation

Vous pouvez afficher rapidement des informations sur les pannes d'application dans le tableau **Crashes**. <!--In the **Overview** page of the **Dashboard** section,--> Le diagramme à barres
**Crashes** affiche un histogramme des pannes au fil du temps.

Vous pouvez afficher les données de panne de deux façons :

1. Afficher le taux de pannes : taux de pannes au fil du temps
2. Afficher le nombre total de pannes : nombre total de pannes au fil du temps

## Traitement des incidents liés aux pannes d'application
{: #app-crash-troubleshooting notoc}

La page **Traitement des incidents** dans la console <!-- **Applications** section of the -->
{{site.data.keyword.mobileanalytics_short}} offre une vue granulaire des pannes de votre application grâce au tableau **Récapitulatif des pannes**.

Le tableau **Récapitulatif des pannes** inclut les colonnes de données suivantes et peut être trié :

* Pannes
* Périphériques
* Dernière panne
* Application
* Système d'exploitation
* Message

Cliquez sur l'icône + située en regard de n'importe quelle entrée pour afficher le tableau **Détails des pannes**, qui inclut les colonnes suivantes :

* Heure de la panne
* Version de l'application
* Version du système d'exploitation
* Modèle de périphérique
* ID du périphérique
* Télécharger : lien permettant de télécharger les journaux qui ont conduit à la panne

Développez n'importe quelle entrée du tableau **Détails des pannes** pour obtenir plus de détails, y compris une trace de pile.

**Remarque** : vous remplissez le tableau **Récapitulatif des pannes** en exécutant une requête
sur les journaux d'application de niveau Fatal. Si votre application ne collecte pas de journaux d'application de niveau Fatal, aucune donnée n'est disponible.
