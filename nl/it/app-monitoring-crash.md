---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-06"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Monitoraggio degli arresti anomali delle applicazioni
{: #monitor-app-crash}

Puoi visualizzare le informazioni sugli arresti anomali delle tue applicazioni nella console {{site.data.keyword.mobileanalytics_short}} per monitorare meglio e risolvere più facilmente i problemi delle tue applicazioni.

## Monitoraggio degli arresti anomali delle applicazioni
{: #app-crash notoc}

Nella pagina **Arresti anomali**, la tabella **Panoramica arresti anomali** mostra le seguenti colonne di dati:

* Applicazione: il nome dell'applicazione
* Arresti anomali: il numero totale di arresti anomali per l'applicazione
* Totale utilizzi: il numero di volte per cui un utente apre e chiude l'applicazione
* Frequenza di arresti anomali: percentuale di arresti anomali per utilizzo

Puoi visualizzare rapidamente le informazioni sugli arresti anomali delle tue applicazioni nella tabella **Arresti anomali**. <!--In the **Overview** page of the **Dashboard** section,--> Il grafico a barre **Arresti anomali** visualizza un istogramma degli arresti anomali nel tempo.

Puoi visualizzare i dati relativi agli arresti anomali in due modi:

1. Visualizza frequenza arresti anomali: frequenza degli arresti anomali nel tempo
2. Visualizza totale arresti anomali: totale arresti anomali nel tempo

## Risoluzione dei problemi di arresto anomalo delle applicazioni
{: #app-crash-troubleshooting notoc}

La pagina **Risoluzione dei problemi** nella console <!-- **Applications** section of the --> {{site.data.keyword.mobileanalytics_short}} offre una vista granulare degli arresti anomali della tua applicazione, utilizzando la tabella **Riepilogo arresti anomali**.

La tabella **Riepilogo arresti anomali** è ordinabile e include le seguenti colonne di dati:

* Arresti anomali
* Dispositivi
* Ultimo arresto anomalo
* Applicazione
* Sistema operativo
* Messaggio

Fai clic sull'icona + accanto a qualsiasi voce per visualizzare la tabella **Dettagli dell'arresto anomalo**, che include le seguenti colonne:

* Data/ora arresto anomalo
* Versione applicazione
* Versione sistema operativo
* Modello dispositivo
* ID dispositivo
* Download: link per scaricare i log che portavano all'arresto anomalo

Espandi qualsiasi voce nella tabella **Dettagli dell'arresto anomalo** per ottenere ulteriori dettagli, compresa una traccia di stack.

**Nota:**: i dati per la tabella **Riepilogo dell'arresto anomalo** viene compilata eseguendo delle query dei log applicazione a livello di errore irreversibile. Se la tua applicazione non raccoglie i log applicazione a livello di errore irreversibile, non è disponibile alcun dato.
