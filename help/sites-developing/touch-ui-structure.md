---
title: Struktur der Touch-optimierten Benutzeroberfläche von AEM
seo-title: Structure of the AEM Touch-Enabled UI
description: Die Touch-optimierte Benutzeroberfläche, die in AEM implementiert ist, basiert auf mehreren Prinzipien und besteht aus mehreren Schlüsselelementen
seo-description: The touch-optimized UI, as implemented in AEM, has several underlying principles and is made up of several key elements
uuid: 9a255238-1adc-4a40-9c37-30cb53ffb26c
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 55dba890-4847-4986-b272-33480bc1d573
exl-id: 9eeb3203-e27a-4960-a4ec-58dd9dd098a2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '897'
ht-degree: 62%

---

# Struktur der Touch-optimierten Benutzeroberfläche von AEM{#structure-of-the-aem-touch-enabled-ui}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Die Touch-optimierte Benutzeroberfläche von AEM basiert auf bestimmten Prinzipien und besteht aus mehreren Schlüsselelementen:

## Konsolen {#consoles}

### Grundlegendes Layout und Größenanpassung {#basic-layout-and-resizing}

Die Benutzeroberfläche ist für Mobilgeräte sowie Desktop-Computer geeignet. Adobe hat sich dagegen entschieden, zwei verschiedene Layouts zu entwickeln, und verwendet stattdessen ein Layout, das mit allen Bildschirmen und Geräten kompatibel ist.

Alle Module verwenden dasselbe Basis-Layout. In AEM sieht es wie folgt aus:

![chlimage_1-142](assets/chlimage_1-142.png)

Das Layout ermöglicht eine schnelle und einfache Bedienung und passt sich an die Größe des verwendeten Bildschirms oder Fensters an.

Wenn beispielsweise die Auflösung unter 1.024 px liegt (z. B. bei einem Mobilgerät), wird die Anzeige entsprechend angepasst:

![chlimage_1-143](assets/chlimage_1-143.png)

### Kopfzeilenleiste {#header-bar}

![chlimage_1-144](assets/chlimage_1-144.png)

Die Kopfzeilenleiste zeigt globale Elemente, z. B.:

* das Logo und das spezifische Produkt/die spezifische Lösung, das/die Sie derzeit verwenden; AEM bildet dies auch einen Link zur globalen Navigation
* Suchen
* Symbol für den Zugriff auf die Hilferessourcen
* Symbol für Zugriff auf andere Lösungen
* Anzeige (und Zugriff) aller Warnungen oder Posteingangselemente, die auf Sie warten
* Benutzersymbol mit einem Link zum Profil-Management

### Symbolleiste {#toolbar}

Die Symbolleiste zeigt abhängig vom Kontext Tools an, die die Ansicht oder Elemente der Seite steuern. Die Symbolleiste ist produktspezifisch, es gibt jedoch einige gemeinsame Elemente.

Sie zeigt stets die aktuell möglichen Aktionen an:

![chlimage_1-145](assets/chlimage_1-145.png)

Die möglichen Aktionen hängen auch davon ab, ob eine Ressource ausgewählt ist:

![chlimage_1-146](assets/chlimage_1-146.png)

### Linke Leiste {#left-rail}

Die linke Leiste kann nach Bedarf geöffnet oder ausgeblendet werden. Sie zeigt Folgendes an:

* **Zeitleiste**
* **Verweise**
* **Filter**

Der Standardwert ist **Nur Inhalt** (Leiste ausgeblendet).

![chlimage_1-147](assets/chlimage_1-147.png)

## Bearbeiten von Seiten {#page-authoring}

Beim Bearbeiten von Seiten gibt es folgende strukturelle Bereiche.

### Inhalts-Frame {#content-frame}

Der Seiteninhalt wird im Inhalts-Frame gerendert. Der Inhalts-Frame ist vollständig unabhängig vom Editor - um sicherzustellen, dass keine Konflikte aufgrund von CSS oder JavaScript auftreten.

Der Inhalts-Frame wird im rechten Bereich des Fensters unter der Symbolleiste angezeigt.

![chlimage_1-148](assets/chlimage_1-148.png)

### Editor-Frame {#editor-frame}

Der Editor-Frame enthält die Bearbeitungsfunktionen.

Der Editor-Frame ist ein Container (abstrakt) für alle *Seitenbearbeitungselemente*. Er wird über dem Inhalts-Frame angezeigt und enthält:

* die obere Symbolleiste
* Seitenbereich
* alle Überlagerungen
* alle anderen Seitenbearbeitungselemente; z. B. die Komponenten-Symbolleiste

![chlimage_1-149](assets/chlimage_1-149.png)

### Seitenbereich {#side-panel}

Der Seitenbereich enthält standardmäßig zwei Registerkarten, in denen Sie Assets und Komponenten auswählen und von dort auf die Seite ziehen können.

Der Seitenbereich ist standardmäßig ausgeblendet. Wenn diese Option ausgewählt ist, wird sie entweder auf der linken Seite angezeigt oder über das gesamte Fenster eingeblendet (wenn die Fenstergröße unter einer Breite von 1024 Pixel liegt). z. B. auf einem Mobilgerät).

![chlimage_1-150](assets/chlimage_1-150.png)

### Seitenbereich – Assets {#side-panel-assets}

Auf der Registerkarte Assets können Sie aus dem Asset-Bereich auswählen. Sie können auch nach einem bestimmten Begriff filtern oder eine Gruppe auswählen.

![chlimage_1-151](assets/chlimage_1-151.png)

### Seitenbereich – Asset-Gruppen {#side-panel-asset-groups}

Auf der Registerkarte „Assets“ gibt es eine Dropdown-Liste zum Auswählen bestimmter Asset-Gruppen.

![chlimage_1-152](assets/chlimage_1-152.png)

### Seitenbereich – Komponenten {#side-panel-components}

Auf der Registerkarte Komponenten können Sie aus dem Komponentenbereich auswählen. Sie können auch nach einem bestimmten Begriff filtern oder eine Gruppe auswählen.

![chlimage_1-153](assets/chlimage_1-153.png)

### Überlagerungen {#overlays}

Diese überlagern den Inhalts-Frame und werden von [Ebenen](#layer) genutzt, um die (vollständig transparente) Interaktion mit Komponenten und ihrem Inhalt zu ermöglichen.

Die Überlagerungen befinden sich im Editor-Frame (neben allen anderen Seitenbearbeitungselementen); sie überlagern jedoch die entsprechenden Elemente im Inhalts-Frame.

![chlimage_1-154](assets/chlimage_1-154.png)

### Ebene {#layer}

Eine Ebene ist eine unabhängige Funktionsgruppe, die Sie aktivieren können, um Folgendes auszuführen:

* eine andere Ansicht der Seite aufrufen
* ermöglichen die Bearbeitung und/oder Interaktion mit einer Seite

Anders als spezifische Aktionen zu einzelnen Komponenten bieten die Ebenen komplexe Funktionen für die gesamte Seite.

AEM enthält mehrere bereits für die Seitenbearbeitung implementierte Ebenen. , z. B. Bearbeiten, Vorschau, Anmerkungen.

>[!NOTE]
>
>Ebenen sind ein leistungsstarkes Konzept, das die Ansicht des Benutzers und die Interaktion mit dem Seiteninhalt beeinflusst. Wenn Sie eigene Ebenen entwickeln, müssen Sie sicherstellen, dass die Ebene beim Verlassen bereinigt wird.

### Ebenenschalter {#layer-switcher}

Mit dem Ebenenschalter können Sie die Ebene auswählen, die Sie verwenden möchten. Wenn er geschlossen ist, zeigt er die aktuell verwendete Ebene an.

Der Ebenenschalter ist ein Dropdown-Menü in der Symbolleiste (am oberen Rand des Fensters im Editor-Frame).

![chlimage_1-155](assets/chlimage_1-155.png)

### Komponentensymbolleiste {#component-toolbar}

Jede Instanz einer Komponente zeigt ihre Symbolleiste an, wenn Sie darauf klicken (entweder einmal oder mit einem langsamen Doppelklick). Die Symbolleiste enthält die spezifischen Aktionen (z. B. Kopieren, Einfügen, Öffnen-Editor), die für die Komponenteninstanz (bearbeitbar) auf der Seite verfügbar sind.

Je nach verfügbarem Platz werden die Komponenten-Symbolleisten in der oberen oder unteren rechten Ecke der entsprechenden Komponente platziert.

![chlimage_1-156](assets/chlimage_1-156.png)

## Weiterführende Informationen {#further-information}

Weitere Informationen zu den Konzepten der Touch-optimierten Benutzeroberfläche finden Sie im Artikel [Konzepte der Touch-optimierten Benutzeroberfläche von AEM](/help/sites-developing/touch-ui-concepts.md).

Weitere technische Informationen finden Sie im [JS-Dokumentationssatz](https://helpx.adobe.com/de/experience-manager/6-4/sites/developing/using/reference-materials/jsdoc/ui-touch/editor-core/index.html) für den Touch-optimierten Seiteneditor.
