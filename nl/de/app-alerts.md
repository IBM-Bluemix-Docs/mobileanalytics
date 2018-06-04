---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-06"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Alerts einstellen
{: #alerts}

## Alerts mit Mobile Analytics festlegen 

Sie können Schwellenwerte in Alertdefinitionen in der {{site.data.keyword.mobileanalytics_short}}-Konsole einstellen, um die Aktivitäten besser zu überwachen.

Sie können Schwellenwerte so konfigurieren, dass bei ihrem Überschreiten Alerts ausgelöst werden, über die die {{site.data.keyword.mobileanalytics_short}}-Konsolenüberwachung benachrichtigt wird. Die ausgelösten Alerts können in der Konsole dargestellt oder von einem angepassten Web-Hook verarbeitet werden.<!-- This feature provides a proactive means of detecting app log errors, server log errors, extended periods of network latency, and authentication failures.--> Diese Funktion ist eine proaktive Möglichkeit, um Anwendungsprotokollfehler und Serverprotokollfehler zu Anwendungsabstürzen zu erkennen. Bei Verwendung von reaktiven Schwellenwerten und Alerts ist es nicht erforderlich, Daten zu untersuchen und für ein breites Spektrum an Granularität Schwellenwerte festzulegen.

## Alertdefinition für Anwendungsprotokolle erstellen
{: #alert-def-client-logs notoc}

Sie können eine Alertdefinition erstellen, die auf Anwendungsprotokollen basiert.

Im folgenden Beispiel wird aus den Daten eines Anwendungsprotokolls eine Alertdefinition erstellt. Vom Alert werden alle Anwendungsprotokolle überwacht, die in den letzten fünf Minuten empfangen wurden; in Abständen von fünf Minuten werden sie vom Alert weiter überprüft, bis die Alertdefinition inaktiviert oder gelöscht wird. Ein Alert wird für jedes Gerät ausgelöst, von dem mindestens drei Anwendungsfehlerprotokolle mit demselben Anwendungsnamen und derselben Version gesendet wurden.

1. Klicken Sie in der {{site.data.keyword.mobileanalytics_short}}-Konsole auf **Definitionen**, um die Seite mit den Alertdefinitionen zu öffnen.
2. Klicken Sie auf **Alert erstellen**, um einen Alert zu erstellen.
3. Geben Sie die folgenden Werte an:
	* Alert Name: Alert for app logs (Alert-Name: Alert für App-Protokolle)
	* Message: Error Message Alert (Nachricht: Alert für Fehlernachricht)
	* Query Frequency: 5 minutes (Abfragehäufigkeit: 5 Minuten)
	* Event Type: App Logs (Ereignistyp: App-Protokolle)
		* Property: Log Level (Eigenschaft: Protokollebene)
			* Value: Error (Wert: Fehler)
			* Threshold (Schwellenwert)
				* Threshold Type: Total for Application Instance (Schwellenwerttyp: Gesamtwert für Anwendungsinstanz)

					**Hinweis**: Wenn Sie die Option für den Anwendungsdurchschnitt auswählen, wird aus den App-Protokollen und der Anzahl der Geräte ein Durchschnittswert berechnet. Beispiel: Wenn Sie über zwei Geräte verfügen und von einem Gerät sechs App-Protokolle gesendet werden, vom anderen Gerät dagegen nur drei Protokolle, beträgt der Durchschnitt 4,5 Protokolle.
				* Operator: is greater than or equals 3 (Operator: Größer gleich 3)(
	<!-- insert alert definition tab image? -->

4. Klicken Sie auf **Weiter** und geben Sie den folgenden Wert an:
	* Method: Analytics Console Only (Methode: Nur Analytics-Konsole)

		**Hinweis**: Wählen Sie die Option für Analytics-Konsole und Network Post aus, wenn Sie zusätzlich eine POST-Nachricht mit einer JSON-Nutzlast an die angepasste URL senden wollen. Wenn Sie diese Option auswählen, sind die folgenden Felder verfügbar:
		* Network Post URL (Network Post-URL)
        * Header (Header)
        * Authentication Type (Authentifizierungstyp)
5. Klicken Sie auf **Speichern**.

Sie haben eine Alertdefinition für einen Alert erstellt, der nach Ablauf eines Intervalls von fünf Minuten ausgelöst wird, wenn die Anzahl der App-Protokolle den Schwellenwert von 3 Fehlerprotokollen erreicht oder überschreitet.

## Alertdefinition für Anwendungsabstürze erstellen
{: #alert-def-app-crash notoc}

Sie können eine Alertdefinition erstellen, die auf Anwendungsabstürzen basiert.

Im folgenden Beispiel wird aus den Daten eines Anwendungsabsturzes eine Alertdefinition erstellt. Vom Alert werden alle Anwendungsabstürze überwacht, die in den letzten zwei Minuten empfangen wurden; in Abständen von zwei Minuten werden sie vom Alert weiter überprüft, bis die Alertdefinition inaktiviert oder gelöscht wird. Ein Alert wird für jede Anwendung ausgelöst, die mindestens fünf Mal abgestürzt ist. Weitere Informationen zu Anwendungsabstürzen finden Sie unter [Anwendungsabstürze](#app_crash).

1. Klicken Sie in der {{site.data.keyword.mobileanalytics_short}}-Konsole auf **Definitionen**, um die Seite mit den Alertdefinitionen anzuzeigen.
2. Klicken Sie auf **Alert erstellen**.
3. Geben Sie die folgenden Werte an:
	* Alert Name: Alert for Application Crashes (Alert-Name: Alert für Anwendungsabstürze)
	* Message: App Crash Alert (Nachricht: App-Absturz-Alert)
	* Query Frequency: Application Crashes (Abfragehäufigkeit: Anwendungsabstürze)
		* Query Frequency: 2 minutes (Abfragehäufigkeit: 2 Minuten)
	* Event Type: Application Crashes (Ereignistyp: Anwendungsabstürze)
		* Application Name: Any application (Anwendungsname: Jede Anwendung)
		* Application Version: Any version (Anwendungsversion: Jede Version)
    * Threshold (Schwellenwert)
      * Threshold Type: Crash Count (Schwellenwerttyp: Absturzanzahl)
      * Operator: is greater than or equals 5 (Operator: Größer gleich 5)
4. Klicken Sie auf die Registerkarte **Verteilungsmethode** und geben Sie den folgenden Wert an:
  * Method: Analytics Console Only (Methode: Nur Analytics-Konsole)

    **Hinweis:** Wählen Sie die Option für Analytics-Konsole und Network Post aus, wenn Sie zusätzlich eine POST-Nachricht mit JSON-vernetzen an die angepasste URL senden möchten. Wenn Sie diese Option auswählen, sind die folgenden Felder verfügbar:
      * Network Post URL (required) (Network Post-URL (erforderlich))
      * Headers (optional) (Header (optional))
      * Authentication Type (required) (Authentifizierung (erforderlich))
5. Klicken Sie auf **Speichern**.

## Alertdefinitionen verwalten
{: #managing-alert-definitions notoc}

Im folgenden Beispiel verwalten Sie Alertdefinitionen auf der Seite 'Alert-Management'.

1. Klicken Sie in der {{site.data.keyword.mobileanalytics_short}}-Konsole auf **Protokolle**. Daraufhin wird die Seite für Alertprotokolle geöffnet.
2. Optional: Schalten Sie das Kontrollkästchen unter der Spalte **Enabled** (Aktiviert) ein bzw. aus, um eine bestimmte Alertdefinition zu aktivieren bzw. zu inaktivieren.
3. Optional: Klicken Sie auf das Symbol zum Duplizieren, wenn Sie eine Kopie einer Alertdefinition erstellen und einige Werte verändern möchten.
4. Optional: Klicken Sie auf das Stiftsymbol, wenn Sie eine Alertdefinition bearbeiten möchten.
5. Optional: Klicken Sie auf das Papierkorbsymbol, wenn Sie eine Alertdefinition löschen möchten.

## Alertdetails anzeigen
{: #viewing-alert-details notoc}

Im folgenden Beispiel zeigen Sie die Details ausgelöster Alerts auf der Seite für Alertprotokolle an.

1. Klicken Sie in der {{site.data.keyword.mobileanalytics_short}}-Konsole auf **Protokolle**. Daraufhin wird die Seite für Alertprotokolle angezeigt.
2. Klicken Sie auf das Symbol **+** für einen beliebigen Alert. Daraufhin werden die Abschnitte mit den Alertdefinitionen und den Alert-Instanzen angezeigt.

    **Hinweis:** Wenn die entsprechende Alertdefinition nicht gelöscht oder geändert wurde, können Sie die Alertdefinition durch Klicken auf die Schaltfläche zum Bearbeiten von Alerts bearbeiten. Andernfalls ist die Schaltfläche zum Bearbeiten von Alerts nicht verfügbar und die folgende Nachricht wird angezeigt:

    `This alert definition has since been modified or deleted.`

3. Optional: Wählen Sie einen Alert aus und klicken Sie auf das Papierkorbsymbol, um den Alert zu löschen.

