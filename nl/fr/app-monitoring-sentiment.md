---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-06"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Analyse des sentiments
{: #sentimentanalysis}

## Analyse des sentiments avec Mobile Analytics

{{site.data.keyword.mobileanalytics_short}} vous permet de collecter et d'analyser les évaluations données à votre application par les utilisateurs. 

La fonction d'analyse des sentiments -

 - Rassemble toutes les données de vérification en les extrayant des flux de vérification publics.
 - Consolide les évaluations du magasin d'applications et après une analyse approfondie, attribue un score des sentiments à votre application.
 - Les modèles/variations du score des sentiments peuvent être visualisés à l'aide de graphiques.
 - Sélectionne des mots clés dans les commentaires en retour des utilisateurs, qui donnent un indice sur la tendance des évaluations.
 
## Configuration de l'analyse des sentiments

Pour activer l'analyse des sentiments sur votre application, procédez comme suit :

![Configuration des sentiments](images/configure_sentiment.png)

1. Sur la console {{site.data.keyword.mobileanalytics_short}}, sélectionnez l'onglet **Configurer**. 

2. Sélectionnez l'onglet **Analyse des sentiments**.

3. Cliquez sur le bouton **Ajouter**. Sélectionnez le **Nom de l'application** dans le menu déroulant. 

4. Sélectionnez la **Période d'analyse**. 

5. Cliquez sur la **Source** et déplacez-la vers **Sélectionné**.

6. Cliquez sur **Sauvegarder**.

Vous avez maintenant configuré votre application pour l'analyse des sentiments. 

![Sentiment](images/sentiment_analysis.png)

## Analyse des données de l'application

La quantité de données disponibles que vous pouvez afficher dépend des commentaires en retour de l'utilisateur qui ont été transmis à votre application. Les données statistiques peuvent être consultées uniquement si les utilisateurs ont ajouté des commentaires. 

 - Sur la console {{site.data.keyword.mobileanalytics_short}}, sélectionnez l'onglet **Analyse des sentiments** sous **DONNEES DE L'APPLICATION**. 

 - Sélectionnez la plage de dates, l'application et la plateforme. Sous les graphiques, vous trouverez les éléments suivants pour votre application -

**Score des sentiments** pour votre application, basé sur les commentaires de revue fournis par les utilisateurs 

![Score des sentiments](images/sentiment_score.png)

**Classification** du commentaire de revue basé sur les sentiments

![Commentaires de revue](images/sentiment_review.png)

Les **mots clés** qui apparaissent le plus souvent dans les commentaires de revue de votre application

![Mots clés](images/sentiment_keywords.png)


Il faut au moins 6 heures pour que les données de commentaires se reflètent dans la console {{site.data.keyword.mobileanalytics_short}} une fois qu'ils ont été soumis par l'utilisateur. 

**Remarque :**
 - La fonction est activée uniquement pour les utilisateurs qui ont opté pour le `plan Avancé`. Sélectionnez **Plan** dans la console de maintenance {{site.data.keyword.mobileanalytics_short}} pour effectuer une [mise à niveau](https://console-tok02-red.cdn.s-bluemix.net/docs/account/change-plan.html#changing). 
 - Actuellement, la fonction d'analyse des sentiments est disponible sur `IBM Cloud - Région : Sud des Etats-Unis` et s'applique sur la `plateforme iOS`.








































