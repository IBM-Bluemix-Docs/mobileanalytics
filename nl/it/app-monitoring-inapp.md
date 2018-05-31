---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-06"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Analisi del feedback all'interno dell'applicazione 
{: #In-App}

## Analisi del feedback all'interno dell'applicazione con Mobile Analytics

Con questa funzione di {{site.data.keyword.mobileanalytics_short}} -

- **Gli utenti e i tester** possono registrare ed inviare i report sui bug e il feedback 'All'interno dell'applicazione', poiché eseguono ed utilizzano l'applicazione
- **I proprietari dell'applicazione** hanno una percezione più profonda dell'esperienza utente dell'applicazione con questo feedback utente ricco di contesto
- **Gli sviluppatori** invece ricevono contesti dell'applicazione accurati per diagnosticare e correggere bug / carenze della funzione


## Abilitazione del feedback all'interno dell'applicazione

Completa la seguente procedura per abilitare la tua applicazione mobile ad acquisire il feedback utente all'interno dell'applicazione

**Instrumenta la tua applicazione:**

 - Instrumenta la tua applicazione mobile per entrare nella modalità di feedback. Richiama l'API  `Analytics.triggerFeedbackMode();` per richiamare la modalità di feedback. Per ulteriori informazioni [fai riferimento alla documentazione](/docs/services/mobileanalytics/sdk.html)
 - L'API può essere richiamata per qualsiasi evento dell'applicazione come pulsanti, azioni del menu o movimenti 
 
**Ricevi il feedback all'interno dell'applicazione**

 - I tester e gli utenti finali della tua applicazione possono passare alla modalità di feedback attivando l'azione dell'applicazione che hai strumentato per questo nel passo precedente
 - Dall'interno della modalità di feedback, può essere raccolto il feedback contestuale insieme a una schermata e inviati al servizio {{site.data.keyword.mobileanalytics_short}} 

![acquisisci e invia](images/in_app_capture.png)

**Analizza il feedback all'interno dell'applicazione e agisci di conseguenza**

 - Il servizio {{site.data.keyword.mobileanalytics_short}} riceve e consolida il feedback contestuale inviato dalle applicazioni mobili.
 - Accedi alla console del servizio Mobile Analytics e seleziona l'opzione **User Feedback** nel pannello di navigazione di sinistra della console del servizio {{site.data.keyword.mobileanalytics_short}} per visualizzare i feedback

![Feedback](images/in_app_user_feedback.png)
 
 - Un proprietario dell'applicazione può controllare il feedback, aggiungere commenti e contrassegnarlo con uno **stato di revisione**.  I commenti potrebbero generalmente essere azioni pianificate come link a problemi Git creati per lavorare sul feedback o potrebbero essere motivazioni del perché non è necessaria alcuna azione sul feedback.   
 - Lo stato di revisione può essere utilizzato per gestire in modo efficiente il feedback, categorizzandoli in uno dei vari stati

![Revisione Feedback](images/in_app_review_feedback.png) 

**Nota:**

 - La funzione è abilitata solo per gli utenti che hanno scelto il `Piano avanzato`. Seleziona **Piano** nella console del servizio {{site.data.keyword.mobileanalytics_short}} per l'[upgrade](https://console-tok02-red.cdn.s-bluemix.net/docs/account/change-plan.html#changing) .

 - Al momento, questa funzione è supportata solo su Android.








