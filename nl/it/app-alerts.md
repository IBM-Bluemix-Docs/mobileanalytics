---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-06"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Impostazione di avvisi
{: #alerts}

## Configurazione degli avvisi con Mobile Analytics 

Puoi impostare delle soglie nelle definizioni di avviso nella console {{site.data.keyword.mobileanalytics_short}} per monitorare meglio le tue attività.

Puoi configurare delle soglie che, se vengono superate, attivano degli avvisi di segnalazione al monitoraggio della console {{site.data.keyword.mobileanalytics_short}}. Gli avvisi attivati possono essere visualizzati sulla console oppure gli avvisi possono essere gestiti da webhook personalizzato. <!-- This feature provides a proactive means of detecting app log errors, server log errors, extended periods of network latency, and authentication failures.--> Questa funzione fornisce un modo proattivo per rilevare gli errori log applicazione, gli arresti anomali dell'applicazione e gli errori di log server. Delle soglie e degli avvisi reattivi ti evitano di dover esaminare accuratamente i tuoi dati e impostare delle soglie a un ampio spettro di granularità.

## Creazione di una definizione di avviso per i log applicazione
{: #alert-def-client-logs notoc}

Puoi creare una definizione di avviso basata sui log applicazione.

In questo esempio, utilizzi i dati di log applicazione per creare una definizione di avviso. L'avviso monitora tutti i log applicazione ricevuti negli ultimi 5 minuti e continua a controllare ogni 5 minuti, finché la definizione di avviso non viene disabilitata o eliminata. Un avviso viene attivato per ciascun dispositivo che ha inviato 3 o più log di errori applicazione con gli stessi nome applicazione e versione.

1. Nella console {{site.data.keyword.mobileanalytics_short}}, fai clic su **Definizioni** per andare alla pagina delle definizioni di avviso.
2. Fai clic su **Crea avviso** per creare un avviso.
3. Fornisci i seguenti valori:
	* Nome avviso: Avviso per i log applicazione
	* messaggio: Avviso di messaggio di errore
	* Frequenza query: 5 minuti
	* Tipo di evento: Log applicazione
		* Proprietà: Livello di log
			* Valore: Errore
			* Soglia
				* Tipo di soglia: Totale per l'istanza dell'applicazione

					**Nota**: se scegli l'opzione Media per applicazione, per i log applicazione viene calcolata la media in base al numero di dispositivi. Ad esempio, se hai due dispositivi, e un dispositivo invia sei log applicazione mentre l'altro ne invia tre, la media è 4,5 log applicazione.
				* Operatore: è maggiore di o uguale a 3
	<!-- insert alert definition tab image? -->

4. Fai clic su **Avanti** e fornisci il seguente valore:
	* Metodo: Solo console Analytics

		**Nota**: scegli l'opzione Console Analytics e POST di rete se desideri inviare anche un messaggio POST con un payload JSON al tuo URL personalizzato. Se scegli questa opzione, sono disponibili i seguenti campi:
		* URL POST di rete
        * Intestazioni
        * Tipo di autenticazione
5. Fai clic su **Salva**.

Hai creato una definizione di avviso per attivare un avviso alla fine di ogni intervallo di 5 minuti se il numero di log applicazione ha raggiunto la tua soglia di 3 o più log di errori.

## Creazione di una definizione di avviso per gli arresti anomali delle applicazioni
{: #alert-def-app-crash notoc}

Puoi creare una definizione di avviso basata sugli arresti anomali delle applicazioni.

In questo esempio, utilizzi i dati relativi agli arresti anomali delle applicazioni per creare una definizione di avviso. L'avviso monitora tutti gli arresti anomali di applicazioni negli ultimi 2 minuti e continua a controllare ogni 2 minuti finché la definizione di avviso non viene disabilitata o eliminata. Un avviso viene attivato per ogni applicazione per cui si è verificato un arresto anomalo 5 o più volte. Per ulteriori informazioni sugli arresti anomali delle applicazioni, vedi [Arresti anomali delle applicazioni](#app_crash).

1. Nella console {{site.data.keyword.mobileanalytics_short}}, fai clic su **Definizioni** per visualizzare la pagina delle definizioni dell'avviso.
2. Fai clic su **Crea avviso**.
3. Fornisci i seguenti valori:
	* Nome avviso: Avviso per arresti anomali delle applicazioni
	* Messaggio: Avviso di arresto anomalo dell'applicazione
	* Frequenza query: Arresti anomali dell'applicazione
		* Frequenza query: 2 minuti
	* Tipo di evento: Arresti anomali dell'applicazione
		* Nome applicazione: Qualsiasi applicazione
		* Versione applicazione: Qualsiasi versione
    * Soglia
      * Tipo di soglia: Conteggio arresti anomali
      * Operatore: è maggiore di o uguale a 5
4. Fai clic sulla scheda **Metodo di distribuzione** e fornisci il seguente valore:
  * Metodo: Solo console Analytics

    **Nota**: scegli l'opzione **Console Analytics e POST di rete** se desideri inviare anche un messaggio POST con un payload JSON al tuo URL personalizzato. Se scegli questa opzione, sono disponibili i seguenti campi:
      * URL POST di rete (obbligatorio)
      * Intestazioni (facoltativo)
      * Tipo di autenticazione (obbligatorio)
5. Fai clic su **Salva**.

## Gestione delle definizioni di avviso
{: #managing-alert-definitions notoc}

In questo esempio, gestisci le definizioni di avviso dalla pagina Gestione avvisi.

1. Nella console {{site.data.keyword.mobileanalytics_short}}, fai clic su **Log**. Questa azione apre la pagina Log avvisi.
2. Facoltativo: attiva/disattiva la casella di spunta sotto la colonna **Abilitato** per abilitare o disabilitare una specifica definizione di avviso.
3. Facoltativo: fai clic sull'icona **Duplica** se vuoi creare una copia di una definizione di avviso e modificare qualche valore.
4. Facoltativo: fai clic sull'icona che rappresenta una **matita** se vuoi modificare una definizione di avviso.
5. Facoltativo: fai clic sull'icona che rappresenta un **cestino** se vuoi eliminare una definizione di avviso.

## Visualizzazione di dettagli dell'avviso
{: #viewing-alert-details notoc}

In questo esempio, visualizzi i dettagli dei tuoi avvisi attivati dalla pagina Log avvisi.

1. Nella console {{site.data.keyword.mobileanalytics_short}}, fai clic su **Log**. Questa azione visualizza la pagina Log avvisi.
2. Fai clic sull'icona **+** per uno qualsiasi degli avvisi. Questa azione visualizza le sezioni **Definizione di avviso** e **Istanze avviso**.

    **Nota**: se la definizione di avviso corrispondente non era stata eliminata o modificata, puoi modificare la definizione di avviso
facendo clic su **Modifica avviso**. Altrimenti, il pulsante **Modifica avviso** non è disponibile e viene visualizzato il seguente messaggio:

    `This alert definition has since been modified or deleted.`

3. Facoltativo: seleziona un avviso e fai clic sull'icona che rappresenta un **cestino** per eliminare l'avviso.

