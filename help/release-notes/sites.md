---
title: Versionshinweise zu AEM Sites
seo-title: AEM Sites
description: Spezifische Versionshinweise für Adobe Experience Manager 6.4 Sites.
seo-description: Release notes specific to Adobe Experience Manager 6.4 Sites.
uuid: 593928ec-5d1a-4a88-bd73-897421c5984a
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 40225441-7cfe-4395-ac71-60504b42e764
exl-id: 19ec5c00-eae5-4e7f-9dc5-c7a88b06fd2a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1046'
ht-degree: 9%

---

# Versionshinweise zu AEM Sites {#aem-sites-release-notes}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Sites {#sites}

Detaillierte Informationen zu AEM Sites 6.4-Verbesserungen finden Sie unter:

### Site-Verwaltung {#site-administration}

* Neue Leiste &quot;Inhaltsstruktur&quot;, um schnell in einer Site-Hierarchie zu navigieren. In Kombination mit der Listenansicht wird dadurch das Interaktionsmodell der klassischen Benutzeroberfläche zum Durchsuchen einer Site wiederhergestellt.
* Verbessertes Scrollen in der Karten- und Listenansicht großer Ordner.
* Verbesserte Interaktion mit den Suchergebnissen - die Schaltfläche &quot;Zurück&quot;stellt das vorherige Suchergebnis wieder her.
* Zusätzliche Tastaturbefehle für die gängigsten Aktionen, z. B. das Öffnen einer bestimmten Leiste, das Bearbeiten, Verschieben und Löschen von Seiten oder das Öffnen von Eigenschaften.
* Möglichkeit, Tastaturbefehle zu deaktivieren (in den Voreinstellungen aktivieren/deaktivieren).
* Stoppen Sie die Anzeige von Zeitstempeln in der gesamten Benutzeroberfläche relativ nach 7 Tagen (standardmäßig in den Voreinstellungen festgelegt).

### Seiteneditor {#page-editor}

* Die Geräteliste für die responsive Site-Vorschau wurde aktualisiert, jetzt einschließlich Apple iPhone 8, 8 Plus und X und Samsung S7
* Der Standardspeicherort für Informationen zum Vorlagendesign wurde aus /etc/design verschoben, um Site-spezifische Einstellungen in /conf zu unterstützen. Kunden, die ein Upgrade von früheren AEM durchführen, können weiterhin /etc/design verwenden.

### Komponenten- und Vorlagenentwicklung {#component-amp-template-development}

* Projektarchetyp 13+, siehe [Github für Versionshinweise](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype/releases).
* HTL Version 1.3.1, siehe [Versionshinweise zu GitHub](https://github.com/Adobe-Marketing-Cloud/htl-spec/releases/tag/1.3.1).
* Kernkomponenten 2.0.4+, siehe [Versionshinweise zu Github](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/releases).
* Stilsystem

   * Es wurde ein völlig neues Konzept hinzugefügt, um Komponenten CSS-Klassen zuzuweisen und es Benutzern im Seiteneditor zu ermöglichen, über die Benutzeroberfläche aus einer Untergruppe von Stilen auszuwählen
   * Es wurde die Möglichkeit hinzugefügt, den HTML-Elementnamen zu definieren, der um die Komponente gerendert wird, z. B. &lt;main>, &lt;aside>

* Rastersystem für Layout-Container, siehe [GitHub](https://github.com/Adobe-Marketing-Cloud/aem-responsivegrid).
* Vorlagen-Editor und Richtlinien:

   * Richtlinien unterstützen jetzt Stilsystemkonfigurationen pro Komponente, pro Container und pro Vorlage.
   * Verbesserte Unterstützung für das Definieren des Layouts in Vorlagen für bearbeitbare Komponenten

* Referenz-Website We.Retail 3.0, siehe [Versionshinweise zu GitHub](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/releases).

>[!CAUTION]
>
>AEM umfasst Version 1.12.4 der jQuery-Bibliothek, um für größtmögliche Kompatibilität mit vorhandenem benutzerdefinierten Code zu sorgen. Adobe hat Änderungen vorgenommen, um bekannte Sicherheitsprobleme zu beheben.

### Inhaltsfragmente und Editor {#content-fragments-amp-editor}

* Neu: Strukturierte Inhaltsmodelle als Grundlage für Inhaltsfragmente

   * Benutzeroberfläche des Modell-Editors
   * Vorkonfigurierte Datenelemente für Inhaltsfragmentmodelle (einzeiliger Text, mehrzeiliger Text, Zahl, boolescher Wert, Datum und Uhrzeit, Auflistung, Inhaltsreferenz, Tags)

* Verbesserte Benutzerfreundlichkeit des AEM Inhaltsfragment-Editors

   * Übersicht über alle Elemente anzeigen
   * Bearbeitung im Vollbildmodus für einzelne Elemente
   * Verbesserte Rich-Text-Bearbeitungsfunktionen (Listen mit Aufzählungszeichen, nummerierte Listen, Einzug, Hyperlinks, Tabellen, Suchen und Ersetzen, Rechtschreibprüfung)

* Erweiterte Ausgabeoptionen für AEM Inhaltsfragmente hinzugefügt

   * Neue Inhaltsfragment-Komponente als Teil der Kernkomponenten. [Siehe Code auf GitHub.](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/tree/master/extension/contentfragment/content/src/content/jcr_root/apps/core/wcm/extension/components/contentfragment/v1/contentfragment)
   * Content Services-Unterstützung mit JSON-Ausgabe über Sling Model Exporter

### Experience Fragments  {#experience-fragments}

* Es wurden Experience Fragment-Bausteine eingeführt, um die Wiederverwendung von Inhalten zwischen Experience Fragments-Varianten durch Gruppieren von Komponenten und einfache Referenzierung innerhalb von Varianten zu erleichtern.
* Es wurde die Möglichkeit hinzugefügt, Experience Fragments über die Referenzleiste zu Übersetzungsprojekten hinzuzufügen.
* Es wurde die Möglichkeit hinzugefügt, Workflows mit Experience Fragments über die Timeline-Leiste zu starten.
* Die Referenzleiste zeigt jetzt an, wo ein Experience Fragment in AEM verwendet wird
* Die Konfiguration von Vorlagenspeicherorten ermöglicht es Autoren jetzt, auf globaler oder Ordnerebene zu definieren, welche Experience Fragment-Vorlagen verwendet werden dürfen
* Die Facettensuche unterstützt jetzt erweiterte Filter, z. B. veröffentlichte/nicht veröffentlichte, nach Social Media und Adobe Target exportierte
* Single-Social-Media-Anmeldung beim Exportieren von Experience Fragments in Pinterest oder Facebook hinzugefügt
* Integrierte AEM Experience Fragments mit Adobe Target. Beim Synchronisieren von Experience Fragments mit Target werden Angebote in Adobe Target erstellt, die mit dem Visual Experience Composer von Target verwendet werden können, um sie in ein beliebiges für Target aktiviertes Erlebnis einzubetten.

### Übersetzung {#translation}

* Die Benutzerfreundlichkeit AEM Übersetzungsprojekte wurde verbessert:

   * Unterstützung mehrerer Zielsprachen in einem Projekt
   * Option zum automatischen Weiterleiten und Löschen von Übersetzungsstarts
   * Option zur Planung der wiederholten Ausführung von Übersetzungsprojekten (täglich, wöchentlich, monatlich, jährlich)
   * Verbesserte Kacheln für Übersetzungsprojekte mit detaillierteren Statusinformationen

* Umgekehrtes Translation Memory-Update wurde eingeführt, um Translation Memorys in Übersetzungsmanagementsystemen von Drittanbietern nach lokalen Inhaltsbearbeitungen in AEM zu aktualisieren
* Übersetzungs-Workflows unterstützen jetzt gruppierte Sprachstämme
* Möglichkeit hinzugefügt, Sprachstämmen beliebige Namen zuzuweisen und JCR-Eigenschaft für die Zuordnung zum ISO-Code zu verwenden
* Aktualisierungen der intelligenten Übersetzung erkennen jetzt neue Seiten, die zu einem Übergeordneten Zweig der Sprache hinzugefügt wurden.
* In der Sites Admin-Listenansicht wurde ein Übersetzungsstatusbericht eingeführt.

### Multi-Site-Management (MSM) {#multi-site-management-msm}

* Verbesserte MSM-Skalierbarkeit durch Verwendung eines Oak-basierten Index im Vergleich zum Arbeitsspeicher (LiveCopyIndex)

### Launches {#launches}

* Verbesserte Leistung bei Launches, die einen großen Site-Baum enthalten und bei denen viele Launches aktiv sind
* Verbesserte automatische Promotion und Veröffentlichung von Launches mit mehreren Stammseiten.
* Fehlerkorrektur - Die responsive Gerätevorschau funktioniert jetzt mit Seiten, die im Kontext eines Launches bearbeitet werden.

### Content-Targeting und -Simulation {#content-targeting-simulation}

* Unterstützung von Ordnern zum Organisieren von Segmenten basierend auf Site/Kontext (CQ-94620)
* Der Standardspeicherort für Segmente wurde nach /conf verschoben, um Site-/kontextspezifische Segmentlisten zu erhalten.

### AEM und Adobe Target  {#aem-amp-adobe-target-nbsp}

* Integrierte AEM Experience Fragments mit Adobe Target. Beim Synchronisieren von Experience Fragments mit Target werden Angebote in Adobe Target erstellt, die mit dem Visual Experience Composer von Target verwendet werden können, um sie in ein beliebiges für Target aktiviertes Erlebnis einzubetten.
* Adobe Target mbox.js , Version 63 ist jetzt enthalten. Adobe empfiehlt, die Implementierung auf at.js umzustellen.
* at.js , Version 1.2.2 ist jetzt enthalten. Adobe empfiehlt die Verwendung von Dynamic Tag Management (DTM) oder [Adobe Experience Platform Launch](https://www.adobe.com/enterprise/cloud-platform/launch.html) , um at.js in der Site bereitzustellen.

### AEM und Adobe Analytics {#aem-amp-adobe-analytics}

* s_code.js H.27.5 ist jetzt enthalten. Adobe empfiehlt, die Implementierung auf AppMeasurement.js umzustellen
* AppMeasurement.js 1.8.0 ist jetzt enthalten. Adobe empfiehlt die Verwendung von Dynamic Tag Management (DTM) oder [Adobe Experience Platform Launch](https://www.adobe.com/enterprise/cloud-platform/launch.html) , um AppMeasurement.js auf der Site bereitzustellen.

## Communities-Add-on {#communities-add-on}

Siehe [Communities-Versionshinweise](/help/release-notes/communities-release-notes.md)

## Screens-Add-on {#screens-add-on}

* Zusätzliche Unterstützung für Screens-Player für die Verbindung mit AEM Veröffentlichungsservern für Befehls- und Steuerungsaktionen sowie für Kanaldownloads (anstatt direkt für AEM Autor).
* Neue Möglichkeit zur Gruppierung von Kanalzuweisungen in Zeitplänen
* Kanalzuweisungen haben jetzt Start- und Enddatum.
* Geräte-Dashboard zeigt jetzt Player-Shell und Firmware-Version an
* Geräte-Dashboard-Liste zeigt den Verbindungsstatus des Players an
* Google Chrome OS-Unterstützung für AEM Screens Player hinzugefügt
* Microsoft Windows 10 für AEM Screens Player hinzugefügt
