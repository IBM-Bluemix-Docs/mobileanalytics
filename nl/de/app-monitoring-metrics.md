---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-06"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Metriken und Ereignisse verwenden
{: #usingmetrics}

## Anwendungen mit Mobile Analytics überwachen

Von {{site.data.keyword.mobileanalytics_full}} werden Überwachungs- und Analysefunktionen für mobile Anwendungen bereitgestellt. Mit dem {{site.data.keyword.mobileanalytics_short}}-Client-SDK können Sie Anwendungsprotokolle aufzeichnen und Daten überwachen. Entwickler können steuern, wann diese Daten an den {{site.data.keyword.mobileanalytics_short}}-Service gesendet werden sollen. Wenn die Daten an {{site.data.keyword.mobileanalytics_short}} übergeben werden, können Sie über die {{site.data.keyword.mobileanalytics_short}}-Konsole Erkenntnisse aus Analysen zu mobilen Anwendungen, Geräten und Anwendungsprotokollen erhalten.
{: shortdesc}

##Vordefinierte Metriken

Mit **vordefinierten Metriken** können Sie Fragen wie die folgenden beantworten:

* Wie viele Benutzer sind neue Benutzer?  
* Von wie vielen Benutzern wird meine Anwendung derzeit aktiv verwendet?  
* Wie häufig verwenden die Benutzer meine Anwendung? 
* Zu welcher Tageszeit verwenden die Benutzer meine Anwendung?  
* Welches Gerätemodell bevorzugen meine Benutzer? 
* Ab wann sollte ich die Unterstützung für veraltete Betriebssysteme einstellen? 
* Bei welchen Anwendungen treten Leistungsprobleme auf?  

##Angepasste Ereignisse

Durch das Hinzufügen Ihrer eigenen **angepassten Ereignisse** können Sie Fragen wie die folgenden beantworten: 

* Welche Features werden am meisten, welche am wenigsten verwendet?  
* Wo treten Benutzer in meine App ein und wo verlassen Sie sie wieder?  
* Welche Aktivitäten zeigen Benutzer am meisten an?  
* Führen Benutzer in der App Workflows durch (z. B. Konversionstrichter)?   

Clientseitige Protokolle und Nutzungsdaten werden automatisch gesammelt und bei Bedarf an den Mobile Analytics-Service gesendet. Entwickler und Administratoren können das {{site.data.keyword.mobileanalytics_short}}-Service-Dashboard zum Anzeigen von Daten verwenden, die vom Client-SDK erfasst werden.

## Datenvisualisierung
{: data-visualization notoc}

Alle Daten, die vom Analyseservice erfasst werden, können über das {{site.data.keyword.mobileanalytics_short}}-Dashboard, auf das über Ihr {{site.data.keyword.Bluemix_notm}}-Dashboard durch Klicken auf die Kachel für Ihre IBM {{site.data.keyword.mobileanalytics_short}}-Serviceinstanz zugegriffen werden kann, visualisiert werden. <!--You can also create custom charts, based on data that is collected by the analytics service in the dashboard.--> Zusätzlich zu einer Übersicht Ihrer mobilen Analyse umfasst das Analysefeature die Funktion zum Durchführen einer unformatierten Suche für Clientprotokolle, für erfasste Daten zu einem Clientabsturz sowie beliebige zusätzliche Daten, die Sie explizit über Client-API-Funktionsaufrufe bereitstellen, die dem {{site.data.keyword.mobileanalytics_short}}-Service zugeführt werden. 

