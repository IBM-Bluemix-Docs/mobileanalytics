---

copyright:
  years: 2015, 2017
lastupdated: "2018-02-19"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}


# Foire aux questions 
{: #faq}


1. **Présentation d'{{site.data.keyword.mobileanalytics_full}}**
	
	{{site.data.keyword.mobileanalytics_full}} est un service qui fournit des données d'historique et en temps réel. Ces dernières indiquent les performances de vos applications mobiles et comment les applications mobiles sont utilisées. Avec {{site.data.keyword.mobileanalytics_short}}, les développeurs et les propriétaires d'applications peuvent prendre des décisions en fonction des données en surveillant les tendances pour les utilisateurs actifs, les sessions, les plateformes mobiles et les pannes d'application. Vous pouvez aussi définir des alertes pour des mesures sélectionnées qui, une fois déclenchées, envoient des messages à un noeud final REST, comprenant un service push ou vos services de messagerie internes.


2. **Que puis-je faire avec {{site.data.keyword.mobileanalytics_short}} for {{site.data.keyword.Bluemix_notm}} ?**

	En tant que gestionnaire de produits pour application mobile, vous pouvez voir combien de personnes utilisent votre application (mesures d'utilisateurs) et à quel moment elles l'utilisent (mesures de sessions). Ces informations sont présentées sous forme de séries temporelles et mises à jour en temps réel pour que vous puissiez constater l'effet des modifications que vous apportez à votre application. Vous pouvez procéder à un filtrage pour afficher des versions d'application ou des systèmes d'exploitation spécifiques afin de prendre des décisions relatives à la dépréciation ou à la hiérarchisation. 
	
	En tant que spécialiste du marketing pour les applications mobiles, vous pouvez vous servir des mesures d'utilisateurs et de sessions pour surveiller l'engagement, gérer les résiliations et évaluer l'efficacité de l'effort de marketing pour vos applications mobiles en observant les changements au fil du temps et en établissant des corrélations avec vos dates d'événement.
	
	En tant que développeur d'applications mobiles, vous pouvez vous servir des mesures sur les pannes afin d'identifier et de résoudre les problèmes de performance des applications mobiles avant qu'ils ne gênent les utilisateurs et entachent la réputation de l'application. Vous pouvez surveiller le nombre de pannes et le taux de panne dans la console d'analyse et hiérarchiser les pannes affectant le plus d'utilisateurs. Vous pouvez définir des alertes pour envoyer des notifications ou effectuer des actions automatisées lorsque les pannes dépassent un seuil donné, et vous pouvez traiter les incidents en explorant les instances de panne afin d'afficher les journaux des périphériques et les traces de pile de l'application.
	
	Veillez à ne pas partager d'informations personnelles à l'aide de {{site.data.keyword.mobileanalytics_short}}.

3. **Dois-je avoir des compétences d'analyste de données pour utiliser Mobile Analytics ?**

	Non, {{site.data.keyword.mobileanalytics_short}} propose une console d'analyse prête à l'emploi conçue pour les parties prenantes et les développeurs d'applications. Aucune compétence dans le domaine des requêtes n'est nécessaire.

4. **Puis-je effectuer des requêtes personnalisées sur mes données d'analyse ?**

    {{site.data.keyword.mobileanalytics_short}} ne permet pas d'effectuer des requêtes personnalisées, mais cette fonction est envisagée pour une version future.
	
5. **Comment puis-je connecter mon application à {{site.data.keyword.mobileanalytics_short}} ?**

    [Téléchargez notre logiciel SDK open source pour iOS ou Android](install-client-sdk.html), ou utilisez l'[API REST](https://mobile-analytics-dashboard.{DomainName}/analytics-service/) de {{site.data.keyword.mobileanalytics_short}} pour les autres plateformes. 

6. **Dans quelles régions IBM Cloud Mobile Analytics est-il disponible ?**

    Actuellement, Mobile Analytics est disponible dans le Sud des Etats-Unis et au Royaume-Uni. Il sera disponible dans d'autres régions, mais le planning de mise à disposition n'a pas encore été défini.

7. **Combien coûte ce service ?**

    Les 100 premiers millions d'événements qui sont collectés chaque mois sont gratuits, ensuite les événements coûtent 1 $ par million d'événements.
	
8. **Qu'est-ce qu'un événement ?**

    Les événements actuellement signalés incluent le début de session d'application, la fin de session d'application (y compris le blocage d'application), les notifications d'alerte et les entrées de journal.
	
9. **Comment puis-je estimer le coût mensuel du service ?**

    Étant donné que le prix dépend du nombre d'événements envoyés au service par compte client, estimer les prix revient à estimer les événements.  
	
	Le prix facturé est la somme des événements de toutes les applications que vous avez connectées à {{site.data.keyword.mobileanalytics_short}}. Pour une application donnée, le nombre d'événements dépend du degré d'instrumentation que vous avez implémenté dans l'application, du nombre d'utilisateurs et de l'activité des utilisateurs. 
	
	Utilisez cette formule pour estimer l'utilisation : événements par mois par application = (utilisateurs par jour) (sessions par utilisateur par jour) (jours par mois) (événements par session)

	
	Les événements par session peuvent varier considérablement de 2 à plusieurs centaines, selon les appels réseau, les analyses personnalisées, les captures de journaux et les définitions d'alertes que le développeur a configurés dans l'application.

9. **Combien de temps mes données d'analyse sont-elles conservées ?**

    Les données sont conservées au moins 30 jours.
	
10. **Au bout de combien de temps les données s'affichent-elles dans la console {{site.data.keyword.mobileanalytics_short}} ?**

    Les données qui apparaissent dans la console {{site.data.keyword.mobileanalytics_short}} sont des données presque en temps réel, ce qui signifie qu'elles s'affichent quelques secondes à peine après les événements réels.
	
11. **Quelle est la différence entre {{site.data.keyword.mobileanalytics_full}} et l'analyse des applications mobiles disponible dans MobileFirst Platform Foundation ?**

    Les concepts d'utilisateur et de session sont très similaires dans ces deux consoles, mais l'analyse proposée par MobileFirst Platform Foundation contient des mesures et des paramètres supplémentaires qui permettent aux clients de gérer leur propre cluster d'analyse sur site. De plus, la console d'analyse MobileFirst Platform Foundation décompose les métriques des adaptateurs et des procédures de l'adaptateur, alors que dans le service {{site.data.keyword.mobileanalytics_short}}, ces métriques sont intégrées dans les graphiques et les tableaux de demandes de réseau.
	
12. **J'utilise MobileFirst Platform Foundation sur site pour développer mes applications, mais je ne veux pas héberger mon propre cluster d'analyse. Puis-je utiliser {{site.data.keyword.mobileanalytics_full}} à la place ?**

    Oui. Vous avez deux options : si vous utilisez MobileFirst Platform Foundation 7.x ou 8.0 et que vos applications sont instrumentées avec des logiciels SDK de MobileFirst Platform, vous pouvez configurer votre serveur MobileFirst afin d'afficher les données d'analyse dans {{site.data.keyword.mobileanalytics_short}} for {{site.data.keyword.Bluemix_notm}}. Lisez l'article de blogue [Configuring Mobile Analytics and Mobile Foundation IBM Cloud services ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://mobilefirstplatform.ibmcloud.com/blog/2016/07/11/analytics-bm-service/){: new_window} pour des détails. Vous pouvez aussi instrumenter vos applications avec le logiciel SDK de {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.mobileanalytics_short}} et afficher les données d'analyse directement dans le service {{site.data.keyword.mobileanalytics_short}}.
