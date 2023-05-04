---
title: AEM Foundation und Repository
seo-title: AEM Foundation & Repository
description: Spezifische Versionshinweise für Adobe Experience Manager 6.3 AEM Platform und Repository.
seo-description: Release notes specific to Adobe Experience Manager 6.3 AEM Platform and Repository.
uuid: 147b38d0-cf87-467c-a52d-3399d4af7e6e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: e5dd9d0d-6d67-4430-aeb3-2be91356f624
exl-id: 6f131247-d35e-4298-958f-35b94ff08c58
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 12%

---

# AEM Foundation und Repository {#aem-foundation-repository}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Liste der Änderungen {#list-of-changes}

### Repository {#repository}

* Oak Segment Tar MicroKernel

   * Schneller Komprimierungsmodus (Tail-Komprimierung) für die Online-Revisionsbereinigung
   * Verbesserte Schreibraten
   * Statistiken zu Segmentvorgängen werden über JMXBean verfügbar gemacht
   * Schätzung der Dauer für die Offline-Revisionsbereinigung

* Oak Mongo-Mikrokernel

   * Die kontinuierliche Revisionsbereinigung für MongoMK ersetzt die geplante Bereinigung

* Verbesserte Effizienz bei der Revisionsbereinigung von Dokument-Knotenspeichern
* Siehe [Apache Jackrabbit Oak Jira v 1.8.0](https://archive.apache.org/dist/jackrabbit/oak/1.8.0/RELEASE-NOTES.txt), [Apache Jackrabbit Oak Jira v. 1.8.1](https://archive.apache.org/dist/jackrabbit/oak/1.8.1/RELEASE-NOTES.txt) und [Apache Jackrabbit Oak Jira v. 1.8.2](https://archive.apache.org/dist/jackrabbit/oak/1.8.2/RELEASE-NOTES.txt) für einen vollständigen Überblick über behobene Probleme.

>[!CAUTION]
>
>* Aufgrund der neuen Version von Oak Segment Tar, die mit AEM 6.3 eingeführt wurde, ist eine Repository-Migration erforderlich. Dieser Schritt ist obligatorisch, wenn Sie eine Aktualisierung von einer älteren TarMK-Version durchführen oder von einem anderen Persistenztyp zum neuen Segment-TAR-Format wechseln möchten. Weitere Informationen zu den Vorteilen des neuen Segment-TAR finden Sie unter [Häufig gestellte Fragen zur Migration zu Oak Segment Tar](/help/sites-deploying/revision-cleanup.md#migrating-to-oak-segment-tar).
>


### Suche und Indizierung {#search-amp-indexing}

* Erweiterte Unterstützung für Indizierungsvorgänge über oak-run (CLI):

   * Indexkonsistenzprüfung
   * Indizierungsstatistiken
   * Im/Export der Indexkonfiguration
   * Neuindizierung

* Verringertes Repository-Wachstum im Zusammenhang mit Lucene für eine insgesamt verbesserte Systemleistung
* Synchrone Lucene-Eigenschaftenindizes [(Weitere Infos)](https://wiki.apache.org/jackrabbit/Synchronous%20Lucene%20Property%20Indexes)
* Explain Query in Index Manager unterstützt jetzt AEM QueryBuilder-Syntax
* Der Index-Manager zeigt jetzt Indexmetriken an: Größe, letzte Aktualisierung und Konsistenzprüfung

### Benutzeroberfläche {#user-interface}

* An der Benutzeroberfläche wurden verschiedene Verbesserungen vorgenommen, um sie produktiver und benutzerfreundlicher zu gestalten.
* Neue Leiste &quot;Inhaltsstruktur&quot;, um schnell in einer Hierarchie zu navigieren. In Kombination mit der Listenansicht wird dadurch das Interaktionsmodell der klassischen Benutzeroberfläche wiederhergestellt.
* Verbessertes Scrollen in der Karten- und Listenansicht großer Ordner.
* Verbesserte Interaktion mit den Suchergebnissen - die Schaltfläche &quot;Zurück&quot;stellt das vorherige Suchergebnis wieder her.
* Zusätzliche Tastaturbefehle für die gängigsten Aktionen, wie das Öffnen einer bestimmten Leiste, das Bearbeiten, Verschieben und Löschen von Elementen oder das Öffnen von Eigenschaften.
* Möglichkeit, Tastaturbefehle zu deaktivieren (in den Voreinstellungen aktivieren/deaktivieren).
* Stoppen Sie die Anzeige von Zeitstempeln in der gesamten Benutzeroberfläche relativ nach 7 Tagen (standardmäßig in den Voreinstellungen festgelegt).

>[!CAUTION]
>
>* Adobe plant keine weiteren Verbesserungen an der klassischen Benutzeroberfläche. AEM Version 6.4 enthält die klassische Benutzeroberfläche, und Kunden, die ein Upgrade von früheren Versionen durchführen, können diese weiterhin unverändert verwenden. Beachten Sie, dass die klassische Benutzeroberfläche weiterhin vollständig unterstützt wird, obwohl sie veraltet ist. [Mehr dazu](/help/sites-deploying/ui-recommendations.md).
>


### Inhaltsverteilung {#content-distribution}

* Verbesserte Replikationsleistung zur Unterstützung von Asset-Veröffentlichungen mit großen Volumen
* Unterstützung der OAuth 2.0-Authentifizierung im Verteilungstransport
* Verbesserte Leistung für VLT-Pakete

### Monitoring {#monitoring}

* Eine neue Systemübersicht bietet eine Momentaufnahme aller leistungsbezogenen Systemstatus- und -aktivitäten
* Neue Konsistenzprüfungen:

   * Große Lucene-Indizes erkennen
   * Status der asynchronen Indizierung
   * Große Lucene-Indizes
   * Abfrageleistung
   * Abfrage-Ausnahmelimits
   * Synchronisierte Uhren
   * Systemwartung - Revisionsbereinigung
   * Systemwartung - DataStore GC
   * Systemwartung - Kontinuierliche Revision GC

* Der Benutzer kann jetzt den Umfang des status.zip-Downloads definieren

### Wartung {#maintenance}

* Aktives Löschen von Lucene-Binärdateien mithilfe einer Wartungsaufgabe
* Die RevisionGC-Wartungsaufgabe für MongoDB ist jetzt zugunsten der kontinuierlichen Revisionsbereinigung deaktiviert. Weitere Informationen finden Sie im Abschnitt &quot;Repository&quot;oben.
* Die Konfiguration der Versionsbereinigung ermöglicht die Beibehaltung einer Mindestanzahl von Versionen
* Die Versionsbereinigung hält am Ende eines Wartungsfensters an. Es kann auch manuell gestartet und gestoppt werden und wird beim nächsten Start schrittweise fortgesetzt.

### Aktualisierung {#upgrade}

* Abwärtskompatibilität: Abwärtskompatible Funktionen in Version 6.4 helfen Ihnen, Ihren benutzerdefinierten Code in den meisten Fällen kompatibel zu halten und reduzieren den Upgrade-Aufwand.
* Bewertung der Upgrade-Komplexität: Neues Musterdetektor-Tool zur Beurteilung der Komplexität Ihrer Upgrades.
* Nachhaltige Aktualisierungen: Die API-Oberfläche und die Inhaltsklassifizierung wurden eingeführt, damit Sie die Best Practices für eine effiziente und nahtlose Aktualisierung auf die nächste Version während Ihres Entwicklungszyklus einfach befolgen können.
* Repository-Neustrukturierung: Erhebliche Umstrukturierung (in erster Linie /etc) zur Erleichterung von Upgrades und zur Förderung der Best Practices bei der Implementierung. [Weitere Informationen.](/help/sites-deploying/repository-restructuring.md)
* Siehe [Upgrade-Dokumentation](/help/sites-deploying/upgrade.md) Weitere Informationen zu diesen Funktionen.

### Cloud Services {#cloud-services}

* Viele Cloud Services können jetzt über die Touch-optimierte Benutzeroberfläche konfiguriert werden. die restlichen Daten können auf der Karte Legacy Cloud Services konfiguriert werden.
* Sites- und Asset-Ordner können mit Cloud Services konfiguriert werden, die kontextabhängig geladen werden.

### Sicherheit {#security}

* Verbesserte und vereinfachte Benutzeroberfläche zur Benutzererstellung mit Unterstützung für mehrere Benutzerprofile.
* Verbesserte Leistung bei großen Gruppenmitgliedschaften für Benutzer.

### Projekte und Workflows {#projects-and-workflows}

* Tippen Sie auf den UI-basierten Workflow-Editor, um Workflow-Modelle auf rationellere Weise zu verwalten.
* Unterstützung für die Bereinigung von Projektaufgaben bei Wartungsaufgaben.
