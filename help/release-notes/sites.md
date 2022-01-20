---
title: Versionshinweise zu AEM Sites
seo-title: AEM Sites
description: Spezifische Versionshinweise für Adobe Experience Manager 6.4 Sites
seo-description: Release notes specific to Adobe Experience Manager 6.4 Sites.
uuid: 593928ec-5d1a-4a88-bd73-897421c5984a
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 40225441-7cfe-4395-ac71-60504b42e764
exl-id: 19ec5c00-eae5-4e7f-9dc5-c7a88b06fd2a
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1010'
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

### Seiteneditor {#page-editor}

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

* Verbesserte Benutzerfreundlichkeit des AEM Inhaltsfragment-Editors

   * Übersicht zum Anzeigen aller Elemente
   * Bearbeiten im Vollbildmodus für einzelne Elemente
   * Verbesserte Funktionen zur Rich-Text-Bearbeitung (Aufzählungen, nummerierte Listen, Einrückungen, Hyperlinks, Tabellen, Suchen und Ersetzen, Rechtschreibprüfung)

* Zusätzliche verbesserte Ausgabeoptionen für AEM-Inhaltsfragmente

   * Neue Inhaltsfragment-Komponente als Teil der Kernkomponenten. [Siehe Code auf GitHub.](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/tree/master/extension/contentfragment/content/src/content/jcr_root/apps/core/wcm/extension/components/contentfragment/v1/contentfragment)
   * Unterstützung von Content Services mit JSON-Ausgabe über Sling Model Exporter

### Experience Fragments {#experience-fragments}

* Erlebnisfragment-Bausteine eingeführt, um die Wiederverwendung von Inhalten zwischen den Varianten von Erlebnisfragmenten zu vereinfachen, indem Komponenten gruppiert und einfache Verweise innerhalb von Varianten ermöglicht werden.
* Möglichkeit zum Hinzufügen von Erlebnisfragmenten zu Übersetzungsprojekten über die Verweisleiste hinzugefügt.
* Es wurde die Möglichkeit hinzugefügt, Workflows mit Experience Fragments über die Timeline-Leiste zu starten.
* Die Referenzleiste zeigt jetzt an, wo ein Experience Fragment in AEM verwendet wird
* Die Konfiguration von Vorlagenspeicherorten ermöglicht es Autoren jetzt, auf globaler oder Ordnerebene zu definieren, welche Experience Fragment-Vorlagen verwendet werden dürfen
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
* Aktualisierungen der intelligenten Übersetzung erkennen jetzt neue Seiten, die zu einem Übergeordneten Zweig der Sprache hinzugefügt wurden.
* Übersetzungsstatusberichte in der Sites-Admin-Listenansicht eingeführt.

### Verwaltung mehrerer Websites {#multi-site-management-msm}

* Verbesserte Skalierbarkeit der Verwaltung mehrerer Websites durch Verwendung eines Oak-basierten Index statt des speicherinternen Index (LiveCopyIndex)

### Launches {#launches}

* Verbesserte Leistung von Launches, die eine große Site-Struktur enthalten sowie wenn viele Launches aktiv sind
* Verbesserte automatische Promotion und Veröffentlichung von Launches mit mehreren Stammseiten
* Fehlerkorrektur - Die responsive Gerätevorschau funktioniert jetzt mit Seiten, die im Kontext eines Launches bearbeitet werden.

### Content-Targeting und Simulation {#content-targeting-simulation}

* Unterstützung von Ordnern zum Organisieren von Segmenten basierend auf Site/Kontext (CQ-94620)
* Der standardmäßige Speicherort für Segmente wurde in „/conf“ verschoben, um standort- bzw. kontextspezifische Segmentlisten zu erhalten.

### AEM und Adobe Target  {#aem-amp-adobe-target-nbsp}

* AEM-Erlebnisfragmente mit Adobe Target integriert. Durch das Synchronisieren von Erlebnisfragmenten mit Target werden Angebote in Adobe Target erstellt, die mit dem Visual Experience Composer von Target verwendet werden können, um sie in jedes für Target aktivierte Erlebnis zu integrieren.
* Adobe Target mbox.js , Version 63 ist jetzt enthalten. Adobe empfiehlt, die Implementierung auf „at.js“ umzustellen.
* „at.js“ Version 1.2.2 ist nun integriert. Adobe empfiehlt die Verwendung von Dynamic Tag Management (DTM) oder [Adobe Experience Platform Launch](https://www.adobe.com/de/enterprise/cloud-platform/launch.html) , um at.js in der Site bereitzustellen.

### AEM und Adobe Analytics {#aem-amp-adobe-analytics}

* s_code.js H.27.5 ist jetzt enthalten. Adobe empfiehlt, die Implementierung auf AppMeasurement.js umzustellen
* AppMeasurement.js 1.8.0 ist jetzt enthalten. Adobe empfiehlt die Verwendung von Dynamic Tag Management (DTM) oder [Adobe Experience Platform Launch](https://www.adobe.com/enterprise/cloud-platform/launch.html) , um AppMeasurement.js auf der Site bereitzustellen.

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
