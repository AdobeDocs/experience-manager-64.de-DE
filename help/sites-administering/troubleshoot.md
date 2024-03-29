---
title: Beheben von Fehlern in AEM
seo-title: Troubleshooting AEM
description: Erfahren Sie mehr über die Fehlerbehebung bei AEM.
seo-description: Learn about troubleshooting issues with AEM.
uuid: d68e9ead-8aa6-4108-9f1e-85d7cd7a370f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 1bc19f9a-fa3f-43e3-813e-23ab0b708d43
exl-id: 34b509d5-4e80-4229-b155-40004856e87e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 55%

---

# Beheben von Fehlern in AEM{#troubleshooting-aem}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Im folgenden Abschnitt werden einige Probleme behandelt, auf die Sie bei der Verwendung von AEM stoßen können, sowie Empfehlungen zur Fehlerbehebung.

>[!NOTE]
>
>Wenn Sie Probleme beim Authoring in AEM beheben, finden Sie weitere Informationen unter [Fehlerbehebung für Autoren.](/help/sites-authoring/troubleshooting.md)

>[!NOTE]
>
>Bei Problemen sollten Sie auch die Liste der [Bekannte Probleme](/help/release-notes/known-issues.md) für Ihre Instanz (Release- und Service Packs).

## Fehlerbehebungsszenarien für Administratoren {#troubleshooting-scenarios-for-administrators}

Die folgende Tabelle bietet einen Überblick über Probleme, die Administratoren möglicherweise beheben müssen:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Rolle(en)</strong></td> 
   <td><strong>Problem </strong></td> 
  </tr> 
  <tr> 
   <td>Systemadmin</td> 
   <td><p>Beim Doppelklicken auf die JAR-Datei für den Schnellstart passiert entweder gar nichts oder die Datei wird mit einem anderen Programm (z. B. der Archivverwaltung) geöffnet</p> </td> 
  </tr> 
  <tr> 
   <td><p>Systemadmin</p> </td> 
   <td><p>Über CRX ausgeführte Anwendung erzeugt Fehler wegen unzureichendem Arbeitsspeicher</p> </td> 
  </tr> 
  <tr> 
   <td><p>Systemadmin</p> </td> 
   <td><p>Der AEM-Willkommensbildschirm wird nach einem Doppelklick auf den AEM-CM-Schnellstart nicht im Browser angezeigt</p> </td> 
  </tr> 
  <tr> 
   <td><p>Systemadmin</p> <p>Admin-Benutzer</p> </td> 
   <td><p>Erstellen von Thread-Speicherauszügen</p> </td> 
  </tr> 
  <tr> 
   <td><p>Systemadmin</p> <p>Admin-Benutzer</p> </td> 
   <td><p>Überprüfung auf nicht beendete JCR-Sitzungen</p> </td> 
  </tr> 
 </tbody> 
</table>

## Installationsprobleme {#installation-issues}

Siehe [Häufige Installationsprobleme](/help/sites-deploying/troubleshooting.md#common-installation-issues) für Informationen zu den folgenden Fehlerbehebungsszenarien:

* Ein Doppelklick auf die Schnellstart-JAR-Datei hat keine Auswirkungen oder die JAR-Datei mit einem anderen Programm (z. B. Archivmanager).
* Bei Anwendungen, die auf CRX ausgeführt werden, treten Fehler wegen zu wenig Arbeitsspeicher auf.
* Der AEM Begrüßungsbildschirm wird nach einem Doppelklick auf AEM Schnellstart nicht im Browser angezeigt.

## Methoden zur Fehlerbehebung in der Analyse {#methods-for-troubleshooting-analysis}

### Erstellen von Thread-Speicherauszügen {#making-a-thread-dump}

Ein Thread-Speicherauszug ist eine Liste aller Java-Threads, die derzeit aktiv sind. Wenn AEM nicht richtig reagiert, kann der Thread-Speicherauszug helfen, Deadlocks oder andere Probleme zu identifizieren.

### Verwenden der Sling-Thread-Dumper {#using-sling-thread-dumper}

1. Öffnen Sie die **AEM-Web-Konsole**; zum Beispiel unter `http://localhost:4502/system/console/`.

1. Wählen Sie auf der Registerkarte **Status** die Option **Threads** aus.

![screen_shot_2012-02-13at43925pm](assets/screen_shot_2012-02-13at43925pm.png)

### Verwenden von jstack (Befehlszeile) {#using-jstack-command-line}

1. Suchen Sie die PID (Prozess-ID) der AEM Java-Instanz.

   Sie können beispielsweise `ps -ef` oder `jps` verwenden.

1. Ausführen:

   `jstack <pid>`

1. Daraufhin wird der Thread-Speicherauszug angezeigt.

>[!NOTE]
>
>Sie können die Thread-Speicherauszüge an eine Protokolldatei anhängen, indem Sie die `>>`-Ausgabeumleitung verwenden:
>
>`jstack <pid> >> /path/to/logfile.log`

Weitere Informationen dazu finden Sie in der Dokumentation [Erstellen von Thread-Speicherauszügen von einem JVM](https://helpx.adobe.com/de/cq/kb/TakeThreadDump.html).

### Überprüfen auf nicht beendete JCR-Sitzungen {#checking-for-unclosed-jcr-sessions}

Wenn Funktionen für AEM WCM entwickelt werden, können JCR-Sitzungen geöffnet werden (vergleichbar mit dem Öffnen einer Datenbankverbindung). Wenn die geöffneten Sitzungen nie geschlossen werden, kann Ihr System folgende Symptome aufweisen:

* Das System wird langsamer.
* Es befinden sich viele „CacheManager: resizeAll“-Einträge in der Protokolldatei. Die folgende Zahl (size=&lt;x>) gibt die Anzahl an Caches an; jede Sitzung öffnet mehrere Caches.
* Gelegentlich reicht der Speicherplatz des Systems nicht aus (nach einigen Stunden, Tagen oder Wochen – je nach Schweregrad).

Informationen zum Analysieren nicht geschlossener Sitzungen und zum Ermitteln, welcher Code eine Sitzung nicht schließt, finden Sie im Knowledge Base-Artikel . [Nicht geschlossene Sitzungen analysieren](https://helpx.adobe.com/crx/kb/AnalyzeUnclosedSessions.html).

### Verwenden der Adobe Experience Manager-Web-Konsole {#using-the-adobe-experience-manager-web-console}

Der Status der OSGi-Pakete kann auch frühzeitig auf mögliche Probleme hinweisen.

1. Öffnen Sie die **AEM-Web-Konsole**; zum Beispiel unter `http://localhost:4502/system/console/`.

1. Wählen auf der Registerkarte **OSGi** die Option **Pakete** aus.

1. Überprüfen Sie Folgendes:

   * den Status der Pakete. Falls Status wie „Inaktiv“ oder „Nicht erfüllt“ angezeigt werden, versuchen Sie, das Paket zu stoppen und neu zu starten. Wenn das Problem weiterhin besteht, müssen Sie möglicherweise weitere Untersuchungen mit anderen Methoden durchführen.
   * ob Pakete mit fehlenden Abhängigkeiten vorliegen. Dies können Sie herausfinden, indem Sie auf den einzelnen Paket-Namen klicken, bei dem es sich um einen Link handelt (im folgenden Beispiel sind keine Probleme aufgetreten):

![screen_shot_2012-02-13at44706pm](assets/screen_shot_2012-02-13at44706pm.png)
