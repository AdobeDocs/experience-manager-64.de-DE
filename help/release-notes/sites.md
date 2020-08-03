---
title: Versionshinweise zu AEM Sites
seo-title: AEM Sites
description: Spezifische Versionshinweise für Adobe Experience Manager 6.4 Sites
seo-description: Spezifische Versionshinweise für Adobe Experience Manager 6.4 Sites
uuid: 593928ec-5d1a-4a88-bd73-897421c5984a
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 40225441-7cfe-4395-ac71-60504b42e764
translation-type: tm+mt
source-git-commit: f8ba597c62379ba413309303c2ad066ab7afce1e
workflow-type: tm+mt
source-wordcount: '1020'
ht-degree: 80%

---


# Versionshinweise zu AEM Sites {#aem-sites-release-notes}

## Sites {#sites}

Im Folgenden sind die mit AEM Sites 6.4 aufgeführten Verbesserungen aufgeführt:

### Site-Administration {#site-administration}

* Neue Inhaltsstrukturleiste zur schnellen Navigation in Site-Hierarchien. In Verbindung mit der Listenansicht steht damit wieder das Interaktionsmodell der klassischen Benutzeroberfläche zum Durchsuchen einer Site zur Verfügung.
* Verbesserte Funktion zum Scrollen in der Karten- und Listenansicht großer Ordner.
* Verbesserte Interaktion mit den Suchergebnissen – über die Schaltfläche „Zurück“ lässt sich das vorherige Suchergebnis wieder aufrufen.
* Zusätzliche Tastenkombinationen für die gängigsten Aktionen, etwa das Öffnen einer bestimmten Leiste, das Bearbeiten, Verschieben und Löschen von Seiten oder das Öffnen von Eigenschaften.
* Möglichkeit zum Deaktivieren von Tastaturbefehlen (diese können unter „Voreinstellungen“ aktiviert bzw. deaktiviert werden).
* Keine weitere Anzeige von Zeitstempeln in der gesamten Benutzeroberfläche nach sieben Tagen (als Standardeinstellung in den Voreinstellungen festgelegt).

### Seiten-Editor {#page-editor}

* Aktualisierte Geräteliste für eine responsive Site-Vorschau – umfasst nun auch Apple iPhone 8, 8 Plus und X und Samsung S7
* Der Standardspeicherort für Vorlagendesigninformationen wurde aus „/etc/design“ entfernt, um die spezifischen Einstellungen in „/conf“ zu unterstützen. Kunden, die ein Upgrade von früheren AEM-Versionen durchführen, können weiterhin „/etc/design“ verwenden.

### Komponenten- und Vorlagenentwicklung {#component-amp-template-development}

* Projekt-Archetype 13+, siehe [Versionshinweise von GitHub](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype/releases).
* HTL Version 1.3.1, siehe [Versionshinweise von GitHub](https://github.com/Adobe-Marketing-Cloud/htl-spec/releases/tag/1.3.1).
* Kernkomponenten 2.0.4+, siehe [Versionshinweise von GitHub](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/releases).
* Stilsystem

   * Neues Konzept, um Komponenten CSS-Klassen zuzuweisen und es den Benutzern im Seiten-Editor zu ermöglichen, über die Benutzeroberfläche eine Auswahl aus einem Teil der Stile zu treffen
   * Neue Möglichkeit, den um die Komponente gerenderten HTML-Elementnamen zu definieren, z. B. „&lt;main>“, „&lt;aside>“

* Rastersystem für Layout-Container, siehe [GitHub](https://github.com/Adobe-Marketing-Cloud/aem-responsivegrid).
* Vorlagen-Editor und Richtlinien

   * Richtlinien unterstützen nun Stilsystemkonfigurationen pro Komponente, pro Container und pro Vorlage.
   * Verbesserte Unterstützung für das Definieren von Layouts in Vorlagen für bearbeitbare Komponenten

* Referenz-Website We.Retail 3.0, siehe [Versionshinweise von GitHub](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/releases).

>[!CAUTION]
>
>AEM enthält Version 1.12.4 der jQuery-Bibliothek, um eine maximale Kompatibilität mit vorhandenem benutzerdefiniertem Code zu gewährleisten. Adobe hat Änderungen vorgenommen, um bekannte Sicherheitsprobleme zu beheben.

### Inhaltsfragmente und Editor {#content-fragments-amp-editor}

* Strukturierte Inhaltsmodelle als Grundlage für Inhaltsfragmente eingeführt

   * Modell-Editor-Benutzeroberfläche
   * Vorkonfigurierte Datenelemente für Inhaltsfragmentmodelle (einzeiliger Text, mehrzeiliger Text, Zahl, boolesch, Datum und Uhrzeit, Aufzählung, Inhaltsreferenz, Tags)

* Verbesserte Benutzerfreundlichkeit des Editors AEM Inhaltsfragment

   * Übersicht zum Anzeigen aller Elemente
   * Bearbeiten im Vollbildmodus für einzelne Elemente
   * Verbesserte Funktionen zur Rich-Text-Bearbeitung (Aufzählungen, nummerierte Listen, Einrückungen, Hyperlinks, Tabellen, Suchen und Ersetzen, Rechtschreibprüfung)

* Zusätzliche verbesserte Ausgabeoptionen für AEM-Inhaltsfragmente

   * Neue Inhaltsfragment-Komponente als Teil der Kernkomponenten. [Siehe Code auf GitHub.](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/tree/master/extension/contentfragment/content/src/content/jcr_root/apps/core/wcm/extension/components/contentfragment/v1/contentfragment)
   * Unterstützung von Content Services mit JSON-Ausgabe über Sling Model Exporter

### Experience Fragments {#experience-fragments}

* Erlebnisfragment-Bausteine eingeführt, um die Wiederverwendung von Inhalten zwischen den Varianten von Erlebnisfragmenten zu vereinfachen, indem Komponenten gruppiert und einfache Verweise innerhalb von Varianten ermöglicht werden.
* Möglichkeit zum Hinzufügen von Erlebnisfragmenten zu Übersetzungsprojekten über die Verweisleiste hinzugefügt.
* Die Möglichkeit zum Beginn von Workflows mit Erlebnisfragmenten über die Zeitschienenleiste wurde hinzugefügt
* Die Referenzleiste zeigt jetzt, wo ein Erlebnisfragment in AEM verwendet wird
* Die Konfiguration von Vorlagenspeicherorten ermöglicht es Autoren jetzt, auf globaler Ebene oder auf Ordnerebene zu definieren, welche Erlebnisfragment-Vorlagen verwendet werden dürfen
* Die Facettensuche unterstützt nun erweiterte Filterfunktionen, beispielsweise für veröffentlichte/nicht veröffentlichte oder in soziale Netzwerke und Adobe Target exportierte Elemente.
* Einmalige Anmeldung für soziale Netzwerke hinzugefügt, wenn Erlebnisfragmente nach Pinterest oder Facebook exportiert werden.
* AEM-Erlebnisfragmente mit Adobe Target integriert. Durch das Synchronisieren von Erlebnisfragmenten mit Target werden Angebote in Adobe Target erstellt, die mit dem Visual Experience Composer von Target verwendet werden können, um sie in jedes für Target aktivierte Erlebnis zu integrieren.

### Übersetzung {#translation}

* Verbesserte Benutzerfreundlichkeit von AEM-Übersetzungsprojekten:

   * Unterstützung für mehrere Zielsprachen in einem Projekt
   * Option zum automatischen Bewerben und Löschen von Übersetzungsstarts
   * Option zum Planen der wiederkehrenden Ausführung von Übersetzungsprojekten (täglich, wöchentlich, monatlich, jährlich)
   * Verbesserte Kacheln für Übersetzungsprojekte mit detaillierteren Statusinformationen

* Umgekehrte Translation-Memory-Aktualisierung eingeführt, um Translation Memorys in Übersetzungsmanagementsystemen von Drittanbietern nach der Bearbeitung von lokalen Inhalten in AEM zu aktualisieren.
* Übersetzungs-Workflows unterstützen gruppierte Sprachstämme.
* Möglichkeit hinzugefügt, Sprachstämmen beliebige Namen zuzuweisen und die Eigenschaft „jcr“ für die Zuordnung zum ISO-Code zu verwenden.
* Updates für intelligente Übersetzungen erkennen jetzt neue Seiten, die zu einer Übergeordnet-Verzweigung hinzugefügt wurden.
* Übersetzungsstatusberichte in der Sites-Admin-Listenansicht eingeführt.

### Verwaltung mehrerer Websites {#multi-site-management-msm}

* Verbesserte Skalierbarkeit der Verwaltung mehrerer Websites durch Verwendung eines Oak-basierten Index statt des speicherinternen Index (LiveCopyIndex)

### Launches {#launches}

* Verbesserte Leistung von Launches, die eine große Site-Struktur enthalten sowie wenn viele Launches aktiv sind
* Verbesserte automatische Promotion und Veröffentlichung von Launches mit mehreren Stammseiten
* Es wurde ein Fehler behoben, der verhinderte, dass die Vorschau des reaktionsfähigen Geräts mit Seiten funktionierte, die im Kontext eines Starts bearbeitet wurden.

### Content-Targeting und Simulation {#content-targeting-simulation}

* Unterstützungsordner zum Organisieren von Segmenten je nach Site/Kontext (CQ-94620)
* Der standardmäßige Speicherort für Segmente wurde in „/conf“ verschoben, um standort- bzw. kontextspezifische Segmentlisten zu erhalten.

### AEM und Adobe Target  {#aem-amp-adobe-target-nbsp}

* AEM-Erlebnisfragmente mit Adobe Target integriert. Durch das Synchronisieren von Erlebnisfragmenten mit Target werden Angebote in Adobe Target erstellt, die mit dem Visual Experience Composer von Target verwendet werden können, um sie in jedes für Target aktivierte Erlebnis zu integrieren.
* Adobe Target mbox.js Version 63 ist jetzt enthalten. Adobe empfiehlt, die Implementierung auf „at.js“ umzustellen.
* „at.js“ Version 1.2.2 ist nun integriert. Adobe recommends to use either Dynamic Tag Management (DTM) or [Adobe Experience Platform Launch](https://www.adobe.com/de/enterprise/cloud-platform/launch.html) to provision at.js into the site.

### AEM und Adobe Analytics {#aem-amp-adobe-analytics}

* s_code.js H.27.5 jetzt enthalten. Adobe empfiehlt den Umstieg auf AppMeasurement.js
* AppMeasurement.js 1.8.0 ist jetzt enthalten. Adobe recommends to use either Dynamic Tag Management (DTM) or [Adobe Experience Platform Launch](https://www.adobe.com/de/enterprise/cloud-platform/launch.html) to provision AppMeasurement.js into the site.

## Communities-Add-on {#communities-add-on}

Weitere Informationen hierzu finden Sie auf der [Seite mit Versionshinweisen für AEM Communities](/help/release-notes/communities-release-notes.md).

## Screens-Add-on {#screens-add-on}

* Unterstützung für Screens-Player zur Verbindung mit AEM-Veröffentlichungsservern für Befehle und Steuerungen sowie den Download von Kanälen hinzugefügt (anstelle eines direkten Downloads in die Autoreninstanz von AEM).
* Möglichkeit zum Gruppieren von Kanalzuweisungen in Zeitplänen hinzugefügt.
* Kanalzuweisungen verfügen nun über ein Start- und Enddatum.
* Geräte-Dashboard zeigt nun Player-Shell- und Firmware-Version.
* Geräte-Dashboard-Liste zeigt nun den Verbindungsstatus des Players.
* Google Chrome OS-Unterstützung für AEM Screens Player hinzugefügt
* Microsoft Windows 10 für AEM Screens Player hinzugefügt
