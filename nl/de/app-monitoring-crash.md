---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-06"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Anwendungsabstürze überwachen
{: #monitor-app-crash}

Sie können Informationen zu Anwendungsabstürzen in der {{site.data.keyword.mobileanalytics_short}}-Konsole anzeigen, um Ihre Anwendungen besser überwachen und entsprechende Fehler beheben zu können.

## Überwachung von Anwendungsabstürzen
{: #app-crash notoc}

Auf der Seite mit den Abstürzen sehen Sie in der Tabelle mit der Absturzübersicht die folgenden Datenspalten:

* Application: Any application (Anwendung: Jede Anwendung)
* Crashes: total number of crashes for that app (Abstürze: Gesamtzahl der Abstürze für diese App)
* Total Uses: total number of times a user opens and closes that app (Gesamte Verwendungen: Die Angabe, wie oft diese App geöffnet und geschlossen wurde)
* Crash Rate: percentage of crashes per use (Absturzrate: Der Prozentsatz der Abstürze pro Verwendung)

In der Tabelle für Abstürze werden umgehend Informationen zu Ihren Anwendungsabstürzen angezeigt. <!--In the **Overview** page of the **Dashboard** section,--> Das Balkendiagramm für Abstürze zeigt ein Histogramm der Abstürze im zeitlichen Verlauf an.

Sie können Absturzdaten auf zwei Arten anzeigen:

1. Absturzrate anzeigen: Die Absturzrate im zeitlichen Verlauf
2. Gesamtsumme der Abstürze anzeigen: Gesamte Abstürze im zeitlichen Verlauf

## Fehlerbehebung für App-Abstürze
{: #app-crash-troubleshooting notoc}

Die Seite **Fehlerbehebung** im <!-- **Applications** section of the --> {{site.data.keyword.mobileanalytics_short}}-Konsole bietet eine differenzierte Ansicht der App-Abstürze; hierfür wird die Tabelle mit der Zusammenfassung der Abstürze verwendet.

Die Tabelle für die Absturzzusammenfassung kann sortiert werden und besteht aus den folgenden Datenspalten:

* Crashes (Abstürze)
* Devices (Geräte)
* Last Crash (Letzter Absturz)
* Anwendung
* OS (Betriebssystem)
* Message(Nachricht)

Sie können auf das Plussymbol (+) neben einem beliebigen Eintrag klicken, um die Tabelle für Absturzdetails mit den folgenden Spalten anzuzeigen:

* Time Crashed (Absturzzeit)
* Application Version (Anwendungsversion)
* OS Version (Version des Betriebssystems)
* Device Model (Gerätemodell)
* Device ID (Geräte-ID)
* Download: link to download the logs that led up to the crash (Download: Link zum Herunterladen der Protokolle führte zum Absturz)

Sie können einen Eintrag in der Tabelle für Absturzdetails erweitern, um weitere Details, u. a. einen Stack-Trace, anzuzeigen.

**Hinweis:** Die Daten für die Tabelle mit der Absturzzusammenfassung werden durch Abfragen der App-Protokolle mit schwerwiegenden Fehlern gefüllt. Wenn Ihre Anwendung keine Anwendungsprotokolle mit schwerwiegenden Fehlern erfasst, sind keine Daten verfügbar.
