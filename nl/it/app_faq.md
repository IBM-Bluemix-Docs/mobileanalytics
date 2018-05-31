---

copyright:
  years: 2015, 2017
lastupdated: "2018-02-19"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}


# Domande frequenti (FAQ)  
{: #faq}


1. **Che cos'è {{site.data.keyword.mobileanalytics_full}}?**
	
	{{site.data.keyword.mobileanalytics_full}} è un servizio che fornisce informazioni approfondite cronologiche e in tempo reale su come stanno venendo eseguite ed utilizzate le tue applicazioni. Utilizzando {{site.data.keyword.mobileanalytics_short}}, i proprietari e gli sviluppatori dell'applicazione possono prendere decisioni di indirizzamento dati monitorando gli andamenti degli utenti attivi, delle sessioni, delle piattaforme mobili e degli arresti anomali dell'applicazione. Puoi anche impostare gli avvisi su metriche selezionate che, una volta attivati, inviano messaggi a tutti gli endpoint REST, inclusi il servizio di push o i tuoi servizi di messaggistica interni.


2. **Come posso utilizzare {{site.data.keyword.mobileanalytics_short}} per {{site.data.keyword.Bluemix_notm}}?**

	Come responsabile del prodotto dell'applicazione mobile, puoi visualizzare quante persone utilizzano la tua applicazione (metriche utente) e quando la stanno utilizzando (metriche sessione). Queste informazioni sono presentate come serie temporali e sono aggiornate in tempo reale in modo che puoi notare l'effetto delle modifiche che effettui per la tua applicazione. Puoi impostare un filtro per visualizzare versioni o sistemi operativi dell'applicazione specifici e prendere decisioni di assegnazione della priorità o di deprecazione. 
	
	Come venditore dell'applicazione mobile, puoi utilizzare le metriche sessione e utente per monitorare il coinvolgimento, gestire la variazione e valutare l'efficacia dell'impatto di marketing dell'applicazione mobile osservando le modifiche nel tempo e correlandole ai tuoi dati evento.
	
	Come sviluppatore dell'applicazione mobile, puoi utilizzare le metriche degli arresti anomali per rilevare e risolvere problemi nelle prestazioni dell'applicazione mobile prima che frustino l'utente e danneggino la reputazione dell'applicazione. Puoi monitorare il numero e la frequenza degli arresti anomali dalla console di analisi e puoi dare priorità agli arresti anomali che coinvolgono molti utenti. Puoi impostare gli avvisi per inviare notifiche o per effettuare azioni automatizzate quando gli arresti anomali superano una soglia fornita e puoi risolvere i problemi eseguendo il drilldown delle istanze con arresti anomali per visualizzare i log del dispositivo e le tracce di stack dell'applicazione.
	
	Assicurati di non condividere alcuna informazione personale utilizzando {{site.data.keyword.mobileanalytics_short}}.

3. **Ho bisogno di una analista dei dati per utilizzare Mobile Analytics?**

	No, {{site.data.keyword.mobileanalytics_short}} offre una console di analisi pronta per l'utilizzo per le parti interessate di business e per gli sviluppatori dell'applicazione. Non è richiesta alcuna competenza di query.

4. **Posso eseguire query personalizzate sui miei dati di analisi?**

    {{site.data.keyword.mobileanalytics_short}} non consente query personalizzate ma sarà preso in considerazione per il futuro.
	
5. **Come posso collegare la mia applicazione a {{site.data.keyword.mobileanalytics_short}}?**

    [Scarica la nostra SDK open source per iOS o Android](install-client-sdk.html), o utilizza la {{site.data.keyword.mobileanalytics_short}} [API REST](https://mobile-analytics-dashboard.{DomainName}/analytics-service/) per altre piattaforme. 

6. **In quali regioni IBM Cloud è disponibile Mobile Analytics?**

    Al momento, Mobile Analytics è disponibile negli Stati Uniti - Sud e nel Regno Unito. La disponibilità in altre regioni è stata pianificata ma il periodo non è ancora stato determinato.

7. **Quanto costa questo servizio?**

    I primi 100 milioni di eventi raccolti ogni mese sono gratuiti e quindi, il costo degli eventi è $1 per milioni di eventi.
	
8. **Cosa è un evento?**

    Al momento gli eventi riportati includono l'avvio e la fine della sessione dell'applicazione (incluso l'arresto anomalo dell'applicazione), le notifiche di avviso e le voci di log.
	
9. **Come posso stimare quanto il servizio costerà al mese?**

    Poiché il prezzo dipende dal numero di eventi inviati al servizio per account del client, la stima del prezzo equivale alla stima degli eventi.  
	
	Il prezzo che viene addebitato è la somma degli eventi da tutte le applicazioni che hai collegato a {{site.data.keyword.mobileanalytics_short}}. Per un'applicazione specificata, il numero di eventi dipende dal grado di strumentazione che hai implementato nell'applicazione, dal numero di utenti e da quanto sono attivi gli utenti. 
	
	Utilizza questa formula per stimare l'utilizzo:eventi per mese per applicazione = (utenti al giorno)(sessioni per utente al giorno)(giorni del mese)(eventi per sessione)
	
	Gli eventi per sessione possono variare ampiamente da 2 a diverse centinaia, a seconda di quante chiamate di rete, analisi personalizzate, acquisizioni log e definizioni dell'avviso lo sviluppatore ha configurato nell'applicazione.

9. **Per quanto tempo sono conservati i miei dati?**

    I dati sono conservati almeno per 30 giorni.
	
10. **Quanto ci impiegano i dati ad essere visualizzati nella console {{site.data.keyword.mobileanalytics_short}}?**

    I dati nella console {{site.data.keyword.mobileanalytics_short}} sono quasi in tempo reale, il che significa che i dati vengono visualizzati pochi secondi dopo gli eventi effettivi.
	
11. **Quale è la differenza tra {{site.data.keyword.mobileanalytics_full}} e le analisi mobili di MobileFirst Platform Foundation?**

    Le metriche sessione e utente sono molto simili in queste due console, ma le analisi che provengono da MobileFirst Platform Foundation contengono ulteriori metriche e impostazioni che consentono ai client di gestire il proprio cluster di analisi in locale. Inoltre, la console di analisi MobileFirst Platform Foundation interrompe le metriche per gli adattatori e le procedure dell'adattatore, mentre nel servizio {{site.data.keyword.mobileanalytics_short}}, queste metriche sono integrate nelle tabelle e nei grafici della richiesta di rete.
	
12. **Sto utilizzando MobileFirst Platform Foundation in locale per sviluppare le mie applicazioni ma non voglio ospitare il mio cluster di analisi. Posso invece utilizzare {{site.data.keyword.mobileanalytics_full}}?**

    Sì. Disponi di un paio di opzioni: Se stai utilizzando MobileFirst Platform Foundation 7.x o 8.0 e le tue applicazioni sono instrumentate con le SDK MobileFirst Platform, puoi configurare il tuo server MobileFirst per notificare i dati di analisi a {{site.data.keyword.mobileanalytics_short}} per {{site.data.keyword.Bluemix_notm}}. Leggi il post del blog [Configuring Mobile Analytics and Mobile Foundation IBM Cloud services ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://mobilefirstplatform.ibmcloud.com/blog/2016/07/11/analytics-bm-service/){: new_window} per i dettagli. In alternativa, puoi instrumentare le tue applicazioni ad utilizzare la SDK {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.mobileanalytics_short}} ed inviare notifiche direttamente al servizio {{site.data.keyword.mobileanalytics_short}}.
