---
title: AEM Foundation und Repository
seo-title: AEM Foundation & Repository
description: Spezifische Versionshinweise zur Plattform und zum Repository von Adobe Experience Manager 6.3
seo-description: Release notes specific to Adobe Experience Manager 6.3 AEM Platform and Repository.
uuid: 147b38d0-cf87-467c-a52d-3399d4af7e6e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: e5dd9d0d-6d67-4430-aeb3-2be91356f624
exl-id: 6f131247-d35e-4298-958f-35b94ff08c58
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '719'
ht-degree: 83%

---

# AEM Foundation und Repository {#aem-foundation-repository}

## Liste der Änderungen {#list-of-changes}

### Repository {#repository}

* Oak Segment Tar MicroKernel

   * Schneller Komprimierungsmodus (Fragmentkomprimierung) für Online-Revisionsbereinigung
   * Verbesserte Schreibraten
   * Statistiken zu Segmentvorgängen werden über JMXBean zur Verfügung gestellt
   * Geschätzte Dauer der Offline-Revisionsbereinigung

* Oak Mongo MicroKernel

   * Fortlaufende Revisionsbereinigung für MongoMK ersetzt geplante Revisionsbereinigung.

* Verbesserte Effizienz bei der Revisionsbereinigung von Dokument-Knotenspeichern.
* Siehe [Apache Jackrabbit Oak Jira v 1.8.0](https://archive.apache.org/dist/jackrabbit/oak/1.8.0/RELEASE-NOTES.txt), [Apache Jackrabbit Oak Jira v. 1.8.1](https://archive.apache.org/dist/jackrabbit/oak/1.8.1/RELEASE-NOTES.txt) und [Apache Jackrabbit Oak Jira v. 1.8.2](https://archive.apache.org/dist/jackrabbit/oak/1.8.2/RELEASE-NOTES.txt) für einen vollständigen Überblick über behobene Probleme.

>[!CAUTION]
>
>* Aufgrund der neuen Version von Oak Segment Tar, die mit AEM 6.3 eingeführt wurde, ist eine Repository-Migration erforderlich. Dieser Schritt ist obligatorisch, wenn Sie eine Aktualisierung von einer älteren TarMK-Version durchführen oder von einem anderen Persistenztyp zum neuen Segment-TAR-Format wechseln möchten. Weitere Informationen zu den Vorteilen des neuen Segment-TAR-Formats finden Sie unter [Migration auf Oak-Segment-TAR – Häufig gestellte Fragen (FAQ)](/help/sites-deploying/revision-cleanup.md#migrating-to-oak-segment-tar).

>


### Suche und Indizierung {#search-amp-indexing}

* Erweiterte Unterstützung für Indizierungsvorgänge über oak-run (CLI):

   * Indexkonsistenzüberprüfung
   * Indizierungsstatistiken
   * Import und Export von Indexkonfigurationen
   * Neuindizierung

* Verringertes Repository-Wachstum im Zusammenhang mit Lucene für eine verbesserte Gesamtleistung des Systems
* Synchrone Lucene-Eigenschaftenindizes [(weitere Informationen)](https://wiki.apache.org/jackrabbit/Synchronous%20Lucene%20Property%20Indexes)
* Explain Query im Index-Manager unterstützt jetzt die AEM QueryBuilder-Syntax
* Index-Manager stellt jetzt Index-Metriken bereit: Größe, letzte Aktualisierung und Konsistenzüberprüfung

### Benutzeroberfläche {#user-interface}

* Die Benutzeroberfläche wurde verbessert, um sie effizienter und benutzerfreundlicher zu gestalten.
* Neue Inhaltsstrukturleiste zur schnellen Navigation in Hierarchien. In Verbindung mit der Listenansicht sind damit wieder dieselben Interaktionen wie in der klassischen Benutzeroberfläche möglich.
* Verbesserte Funktion zum Scrollen in der Karten- und Listenansicht großer Ordner.
* Verbesserte Interaktion mit den Suchergebnissen – über die Schaltfläche „Zurück“ lässt sich das vorherige Suchergebnis wieder aufrufen.
* Zusätzliche Tastenkombinationen für die gängigsten Aktionen, etwa das Öffnen einer bestimmten Leiste, das Bearbeiten, Verschieben und Löschen von Elementen oder das Öffnen von Eigenschaften.
* Möglichkeit zum Deaktivieren von Tastaturbefehlen (diese können unter „Voreinstellungen“ aktiviert bzw. deaktiviert werden).
* Keine weitere Anzeige von Zeitstempeln in der gesamten Benutzeroberfläche nach sieben Tagen (als Standardeinstellung in den Voreinstellungen festgelegt).

>[!CAUTION]
>
>* Adobe plant keine weiteren Verbesserungen an der klassischen Benutzeroberfläche. In AEM 6.4 ist die klassische Benutzeroberfläche integriert und Kunden, die ein Upgrade auf diese Version durchführen, können diese wie gehabt verwenden. Beachten Sie, dass die klassische Benutzeroberfläche weiterhin vollständig unterstützt wird, obwohl sie veraltet ist. [Mehr dazu](/help/sites-deploying/ui-recommendations.md).

>


### Inhaltsverteilung {#content-distribution}

* Verbesserte Replikationsleistung zur Unterstützung der Veröffentlichung großer Asset-Volumina
* Unterstützung der OAuth 2.0-Authentifizierung im Verteilertransport
* Verbesserte Leistung bei VLT-Paketen

### Überwachung {#monitoring}

* Eine neue Systemübersicht, die eine Momentaufnahme aller leistungsbezogenen Systemzustände und Aktivitäten bietet
* Neue Konsistenzprüfungen:

   * Erkennung großer Lucene-Indizes
   * Status der asynchronen Indizierung
   * Große Lucene-Indizes
   * Abfrageleistung
   * Abfrage-Ausnahmelimits
   * Synchronisierte Uhren
   * Systemwartung – Revisionsbereinigung
   * Systemwartung – DataStore GC
   * Systemwartung – Continuous Revision GC

* Benutzer können nun den Umfang von status.zip-Downloads festlegen.

### Wartung {#maintenance}

* Aktives Löschen von Lucene-Binärdateien mithilfe einer Wartungsaufgabe
* Die RevisionGC-Wartungsaufgabe für MongoDB ist jetzt zugunsten der fortlaufenden Revisionsbereinigung deaktiviert. Weitere Informationen dazu finden Sie im obenstehenden Abschnitt „Repository“.
* Versionsbereinigungskonfiguration ermöglicht das Vorhalten einer minimalen Anzahl von Versionen.
* Versionsbereinigung stoppt bei Ende eines Wartungsfensters. Sie kann auch manuell gestartet und gestoppt werden und wird beim nächsten Start inkrementell fortgesetzt.

### Aktualisierung {#upgrade}

* Abwärtskompatibilität: Durch die Abwärtskompatibilität von Version 6.4 bleibt Ihr benutzerdefinierter Code in den meisten Fällen kompatibel. Außerdem verringert sich dadurch der mit dem Upgrade verbundene Aufwand.
* Analyse der Upgrade-Komplexität: Ein neues Mustererkennungstool analysiert die Komplexität von Upgrades.
* Nachhaltige Upgrades: Die eingeführte API-Oberfläche und Inhaltsklassifizierung erleichtert Ihnen die Umsetzung von Best Practices für effiziente und nahtlose Upgrades auf die nächste Version während Ihres gesamten Entwicklungszyklus.
* Repository-Neustrukturierung: Erhebliche Umstrukturierung (in erster Linie /etc) zur Erleichterung von Upgrades und zur Förderung der Best Practices bei der Implementierung. [Weitere Informationen.](/help/sites-deploying/repository-restructuring.md)
* Siehe [Upgrade-Dokumentation](/help/sites-deploying/upgrade.md) Weitere Informationen zu diesen Funktionen.

### Cloud Services {#cloud-services}

* Viele Cloud Services können jetzt über die Touch-optimierte Benutzeroberfläche konfiguriert werden. die restlichen Daten können auf der Karte Legacy Cloud Services konfiguriert werden.
* Sites- und Asset-Ordner können mit Cloud Services konfiguriert werden, die kontextabhängig geladen werden.

### Sicherheit {#security}

* Verbesserte und vereinfachte Benutzeroberfläche zur Benutzererstellung mit Unterstützung für mehrere Benutzerprofile.
* Verbesserte Leistung bei umfangreichen Gruppenmitgliedschaften für Benutzer.

### Projekte und Workflows {#projects-and-workflows}

* Workflow-Editor der Touch-optimierten Benutzeroberfläche zur effizienteren Verwaltung von Workflow-Modellen.
* Unterstützung für die Bereinigung von Projektaufgaben in Wartungsaufgaben.
