---

copyright:
  years: 2015, 2017
lastupdated: "2018-02-19"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}


# Häufig gestellte Fragen (FAQs) 
{: #faq}


1. **Was ist {{site.data.keyword.mobileanalytics_full}}?**
	
	{{site.data.keyword.mobileanalytics_full}} ist ein Service, der Echtzeit- und Langzeitinformationen zur Leistung und Nutzung Ihrer mobilen Anwendungen liefert. Mithilfe von {{site.data.keyword.mobileanalytics_short}} können Anwendungsentwickler und -besitzer datengestützte Entscheidungen treffen, indem sie Trends bei aktiven Benutzern, Sitzungen, mobile Plattformen und App-Abstürze überwachen. Sie können auch Alerts zu ausgewählten Metriken einstellen, die nach ihrer Auslösung Nachrichten an jeden REST-Endpunkt senden, einschließlich eines Push-Service oder Ihrer internen Nachrichtenservices.


2. **Welche Möglichkeiten habe ich mit {{site.data.keyword.mobileanalytics_short}} for {{site.data.keyword.Bluemix_notm}}?**

	Als Produktmanager für mobile Anwendungen können Sie sehen, wie viele Personen Ihre Anwendung nutzen (Benutzermetriken) und wann sie sie nutzen (Sitzungsmetriken). Diese Informationen werden in Form einer Zeitreihe dargestellt und in Echtzeit aktualisiert, sodass Sie sehen können, wie sich Ihre Änderungen an der Anwendung auswirken. Sie können nach bestimmten Anwendungsversionen oder Betriebssystemen filtern, um fundierte Entscheidungen über die Einstellung der Unterstützung oder Priorisierung treffen zu können. 
	
	Als Anbieter mobiler Anwendungen können Sie Benutzer- und Sitzungsmetriken zur Überwachung von Kundenprojekten, zum Umgang mit der Abwanderung von Kunden und zur Auswertung der Effektivität von Marketingmaßnahmen im Bereich mobiler Apps nutzen, indem Sie Änderungen im Zeitverlauf beobachten und diese mit Ihren Ereignisdaten in Korrelation setzen.
	
	Als Entwickler mobiler Anwendungen können Sie anhand von Absturzmetriken Leistungsprobleme mobiler Apps aufspüren und beheben, bevor sich Benutzer darüber ärgern müssen und die Reputation der App Schaden nimmt. Sie können die Absturzanzahl und die Absturzrate an der Analysekonsole überwachen und die Bearbeitung derjenigen Abstürzen priorisieren, die die größte Benutzeranzahl betreffen. Sie können Alerts so einstellen, dass diese Benachrichtigungen senden oder automatisierte Abläufe auslösen, wenn Abstürze einen definierten Schwellenwert überschreiten. Außerdem können Sie Fehler beheben, indem Sie Absturzinstanzen eingehend untersuchen und sich Einheitenprotokolle und Anwendungsstack-Traces ansehen.
	
	Achten Sie darauf, mit {{site.data.keyword.mobileanalytics_short}} keine personenbezogenen Daten freizugeben.

3. **Muss ich mich mit der Datenanalyse auskennen, um Mobile Analytics verwenden zu können?**

	Nein, {{site.data.keyword.mobileanalytics_short}} bietet eine gebrauchsfertige Analysekonsole für Verantwortliche und Anwendungsentwickler. Spezialkenntnisse über Abfragen sind nicht erforderlich.

4. **Kann ich angepasste Abfragen anhand meiner Analysedaten durchführen?**

    {{site.data.keyword.mobileanalytics_short}} ermöglicht keine angepassten Abfragen. Für die Zukunft wird dieses Feature jedoch erwogen.
	
5. **Wie verbinde ich meine Anwendung mit {{site.data.keyword.mobileanalytics_short}}?**

    [Laden Sie unser Open-Source-SDK für iOS oder Android herunter](install-client-sdk.html), oder verwenden Sie die {{site.data.keyword.mobileanalytics_short}}-[REST-API](https://mobile-analytics-dashboard.{DomainName}/analytics-service/) für andere Plattformen. 

6. **In welchen IBM Cloud-Regionen ist Mobile Analytics verfügbar?**

    Derzeitig ist Mobile Analytics in den USA (Süden) und im Vereinigtes Königreich verfügbar. Eine Verfügbarkeit in weiteren Regionen ist in Planung, der Zeitrahmen ist jedoch noch nicht festgelegt.

7. **Wie viel kostet dieser Service?**

    Die ersten 100 Millionen Ereignisse, die jeden Monat erfasst werden, sind kostenlos. Danach kosten Ereignisse 1 $ pro einer Millionen Ereignisse.
	
8. **Was ist ein Ereignis?**

    Zu derzeitig gemeldeten Ereignissen zählen der Start der Anwendungssitzung, das Ende der Anwendungssitzung (einschließlich Anwendungsabsturz), Alertbenachrichtigungen und Protokolleinträge.
	
9. **Wie kann die voraussichtlichen Kosten pro Monat für den Service ermitteln?**

    Da die Preisbestimmung von der Anzahl der Ereignisse abhängt, die pro Clientkonto an den Service gesendet werden, wird durch die Anzahl der Ereignisse der Preis bestimmt.  
	
	Der berechnete Preis ist die Summe aller Ereignisse aus allen Anwendungen, die mit {{site.data.keyword.mobileanalytics_short}} verbunden sind. Für eine bestimmte Anwendung hängt die Anzahl der Ereignisse vom Grad der Instrumentierung, die im Rahmen der Anwendung implementiert wurde, der Anzahl der Benutzer und dem Aktivitätsgrad der Benutzer ab. 
	
	Verwenden Sie dieses Format zur Kostenschätzung: Ereignisse pro Monat pro App = (Benutzer pro Tag)(Sitzungen pro Benutzer pro Tag)(Tage pro Monat)(Ereignisse pro Sitzung)
	
	Pro Sitzungen können zwischen zwei und mehrere Hundert Ereignisse auftreten. Dies hängt davon ab, welche Netzaufrufe, angepassten Analysen, Protokollerfassungen und Alertdefinitionen der Entwickler für die Anwendung konfiguriert hat.

9. **Wie lange werden meine Analysedaten aufbewahrt?**

    Die Daten werden mindestens 30 Tage lang aufbewahrt.
	
10. **Wie lange dauert es, bis Daten in der {{site.data.keyword.mobileanalytics_short}}-Konsole angezeigt werden?**

    Daten werden in der {{site.data.keyword.mobileanalytics_short}}-Konsole nahezu in Echtzeit angezeigt, d. h. innerhalb weniger Sekunden nach dem tatsächlichen Ereignis.
	
11. **Worin liegt der Unterschied zwischen {{site.data.keyword.mobileanalytics_full}} und der mobilen Analyse in MobileFirst Platform Foundation?**

    Benutzer und Sitzungen unterscheiden sich bei beiden Konsolen kaum. Die Analysedaten von MobileFirst Platform Foundation enthalten allerdings zusätzliche Metriken und Einstellungen, die es Kunden ermöglichen, ihre eigenen Analysecluster lokal zu verwalten. Außerdem werden in der Analysekonsole von MobileFirst Platform Foundation Metriken für Adapter und Adapterprozeduren aufgegliedert, während beim {{site.data.keyword.mobileanalytics_short}}-Service diese Metriken in Netzanforderungsdiagramme und -tabellen integriert sind.
	
12. **Ich verwende MobileFirst Platform Foundation lokal zur Entwicklung meiner Apps, möchte aber nicht meinen eigenen Analysecluster hosten. Kann ich stattdessen {{site.data.keyword.mobileanalytics_full}} verwenden?**

    Ja. Sie haben mehrere Optionen zur Auswahl: Wenn Sie MobileFirst Platform Foundation 7.x oder 8.0 verwenden und Ihre Apps mit MobileFirst Platform-SDKs instrumentiert sind, können Sie Ihren Worklight Server so konfigurieren, dass er Analysedaten an {{site.data.keyword.mobileanalytics_short}} for {{site.data.keyword.Bluemix_notm}} meldet. Im Blogbeitrag [Configuring Mobile Analytics and Mobile Foundation IBM Cloud services ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://mobilefirstplatform.ibmcloud.com/blog/2016/07/11/analytics-bm-service/){: new_window} finden Sie weitere Details. Alternativ können Sie Ihre Apps auch mit dem {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.mobileanalytics_short}}-SDK instrumentieren und Daten direkt an den {{site.data.keyword.mobileanalytics_short}}-Service melden.
