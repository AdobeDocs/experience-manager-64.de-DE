---
title: Arbeiten mit Inhaltsfragmenten
seo-title: Working with Content Fragments
description: Erfahren Sie, wie Sie mit Inhaltsfragmenten seitenunabhängige Inhalte entwerfen, erstellen, kuratieren und verwenden können.
seo-description: Learn how Content Fragments allow you to design, create, curate and use page-independent content.
uuid: aa5acda2-4c20-4fe7-929d-6c065b252cf2
contentOwner: AEM Docs
topic-tags: content-fragments
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
discoiquuid: 22ae0d3a-083f-40e4-bf4a-7a755ae9e312
exl-id: e2804707-7b75-4fae-937e-9e258481878f
feature: Content Fragments
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2020'
ht-degree: 85%

---

# Arbeiten mit Inhaltsfragmenten {#working-with-content-fragments}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

>[!CAUTION]
>
>Einige Inhaltsfragmentfunktionen erfordern die Anwendung von [AEM 6.4 Service Pack 2 (6.4.2.0 oder höher)](/help/release-notes/sp-release-notes.md).

Adobe Experience Manager (AEM)-Inhaltsfragmente ermöglichen Ihnen das Entwerfen, Erstellen, Kuratieren und [seitenunabhängige Inhalte veröffentlichen](/help/sites-authoring/content-fragments.md). Außerdem können Sie Inhalte zur Verwendung an mehreren Orten/über mehrere Kanäle hinweg vorbereiten.

Mit der Sling Model (JSON)-Exportfunktion der AEM-Kernkomponenten können Inhaltsfragmente auch im JSON-Format bereitgestellt werden. Diese Form der Bereitstellung:

* bietet Ihnen die Möglichkeit, mithilfe der Komponente zu bestimmen, welche Fragmentelemente bereitgestellt werden sollen
* ermöglicht durch das Hinzufügen mehrerer Inhaltsfragment-Kernkomponenten auf der für die API-Bereitstellung verwendeten Seite eine Bereitstellung in größerem Umfang

Hier und auf den folgenden Seiten werden die Aufgaben zum Erstellen, Konfigurieren und Pflegen von Inhaltsfragmenten beschrieben: 

* [Verwalten von Inhaltsfragmenten](content-fragments-managing.md)            – Erstellen Sie Ihre Inhaltsfragmente; anschließend können Sie sie bearbeiten, veröffentlichen und Verweise erstellen

* [Inhaltsfragmentmodelle](content-fragments-models.md) – Aktivieren, Erstellen und Definieren Ihrer Modelle

* [Varianten – Erstellen von Inhaltsfragmenten](content-fragments-variations.md) – Erstellen Sie das Inhaltsfragment und erstellen Sie Varianten der Vorlage

* [Markdown](content-fragments-markdown.md) – Verwendung der Markdown-Syntax für Ihr Fragment

* [Verwenden verknüpfter Inhalte](content-fragments-assoc-content.md) – Hinzufügen verknüpfter Inhalte

* [Metadaten – Fragmenteigenschaften](content-fragments-metadata.md) – Anzeigen und Bearbeiten der Fragmenteigenschaften

>[!NOTE]
>
>Diese Seiten sollten in Verbindung mit dem Thema [Seitenbearbeitung mit Inhaltsfragmenten](/help/sites-authoring/content-fragments.md) gelesen werden. 

Die Anzahl der Kommunikationskanäle nimmt jährlich zu. Typischerweise beziehen sich Kanäle auf den Bereitstellungsmechanismus, und zwar wie folgt:

* Physische Kanäle, z. B. Desktop, Mobilgerät
* Bereitstellung in einem physischen Kanal, z. B. als „Produktdetailseite“ oder „Produktkategorieseite“ für Desktops bzw. als „mobiles Internet“ oder „Mobile App“ für mobile Geräte

Wahrscheinlich möchten Sie jedoch nicht dieselben Inhalte für alle Kanäle verwenden. Daher müssen Sie Ihre Inhalte je nach Kanal optimieren.

Inhaltsfragmente ermöglichen Ihnen Folgendes:

* Erwägen, wie sich Zielgruppen effizient kanalübergreifend erreichen lassen
* Kanalneutrale redaktionelle Inhalte erstellen und verwalten
* Inhaltspools für mehrere Kanäle erstellen
* Inhaltsvarianten für bestimmte Kanäle entwerfen
* Bilder durch Einfügen von Assets (Fragmente mit gemischten Medien) zu Texten hinzufügen

Diese Inhaltsfragmente können dann zusammengestellt werden, um Erlebnisse über verschiedene Kanäle bereitzustellen.

## Inhaltsfragmente und Content Services {#content-fragments-and-content-services}

Mit den AEM Content Services können die Beschreibung und Bereitstellung von Inhalten in/über AEM über einen Fokus auf Web-Seiten hinweg generalisiert werden.

Sie ermöglichen die Bereitstellung von Inhalten in Kanälen, die keine traditionellen AEM-Web-Seiten sind, und nutzen standardisierte Methoden, die von allen Clients genutzt werden können. Diese Kanäle können Folgendes sein:

* Single Page Applications (SPA)
* native Mobile Apps
* weitere AEM-externe Kanäle und Touchpoints

Die Bereitstellung erfolgt im JSON-Format.

AEM-Inhaltsfragmente können zur Beschreibung und Verwaltung strukturierter Inhalte verwendet werden. Strukturierter Inhalt wird in Modellen definiert, die eine Vielzahl von Inhaltstypen enthalten können, darunter Text, numerische Daten, boolesche Ausdrücke, Datum und Uhrzeit und mehr.

Zusammen mit der JSON-Exportfunktion der AEM-Kernkomponenten kann dieser strukturierte Inhalt dann zur Bereitstellung von AEM-Inhalten auf anderen Kanälen als AEM-Seiten verwendet werden.

>[!NOTE]
>
>**Inhaltsfragmente** und **[Experience Fragments](/help/sites-authoring/experience-fragments.md)** sind unterschiedliche Funktionen in AEM:
>
>* **Inhaltsfragmente** sind redaktionelle Inhalte, in erster Linie Text und zugehörige Bilder. Sie sind reine Inhalte ohne Design und Layout.
>* **Experience Fragments** sind vollständig gestaltete Inhalte und stellen Teile von Web-Seiten dar.
>
>Experience Fragments können Inhalte in Form von Inhaltsfragmenten enthalten, aber nicht umgekehrt.
>
>Weitere Details finden Sie in den [Informationen zu Inhaltsfragmenten und Experience Fragments in AEM](https://helpx.adobe.com/de/experience-manager/kt/platform-repository/using/content-fragments-experience-fragments-article-understand.html).

>[!CAUTION]
>
>Inhaltsfragmente sind nicht in der klassischen Benutzeroberfläche verfügbar.
>
>Die Inhaltsfragment-Komponente ist im Sidekick der klassischen Benutzeroberfläche sichtbar, weitere Funktionen sind jedoch nicht verfügbar.

>[!NOTE]
>
>AEM unterstützt auch die Übersetzung von Fragmentinhalten. Siehe [Erstellen von Übersetzungsprojekten für Inhaltsfragmente](creating-translation-projects-for-content-fragments.md) für weitere Informationen.

## Arten von Inhaltsfragmenten {#types-of-content-fragment}

Es gibt folgende Arten von Inhaltsfragmenten:

* Einfache Fragmente

   * Sie haben keine vordefinierte Struktur. Sie enthalten lediglich Text und Bilder.
   * Diese basieren auf der Vorlage für einfache Fragmente.

* Fragmente mit strukturiertem Inhalt

   * Sie basieren auf einem [Inhaltsfragmentmodell](content-fragments-models.md), das eine Struktur für das daraus entstehende Fragment vordefiniert.
   * Diese können außerdem verwendet werden, um Content Services über den JSON Exporter bereitzustellen.

## Inhaltstyp {#content-type}

Inhaltsfragmente werden:

* als **Assets** gespeichert:

   * Inhaltsfragmente (und deren Varianten) können in der Konsole **Assets** erstellt und verwaltet werden.
   * Im Inhaltsfragment-Editor erstellt und bearbeitet.

* im [Seiteneditor anhand der Komponente Inhaltsfragment verwendet](/help/sites-authoring/content-fragments.md) (Verweiskomponente):

   * Die Komponente **Inhaltsfragment** steht für Seitenautoren zur Verfügung. Sie ermöglicht das Erstellen von Verweisen für sowie das Bereitstellen des erforderlichen Inhaltsfragments im HTML- oder JSON-Format.

Inhaltsfragmente sind eine Inhaltsstruktur mit folgenden Eigenschaften:

* Sie weisen kein Layout oder Design auf (gewisse Textformatierung ist im Rich-Text-Modus möglich).
* Enthalten mindestens einen [Bestandteil](#constituent-parts-of-a-content-fragment).
* Kann Bilder [enthalten oder mit Bildern verbunden sein](#fragments-with-visual-assets).
* Bei Referenzierung auf einer Seite können [Übergangsinhalte](#in-between-content-when-page-authoring-with-content-fragments) verwendet werden.

* Sie sind unabhängig vom Bereitstellungsmechanismus (d. h. Seite, Kanal).

### Fragmente mit visuellen Assets {#fragments-with-visual-assets}

Um Autoren eine bessere Kontrolle über eigene Inhalte zu ermöglichen, können Bilder zu einem Inhaltsfragment hinzugefügt und/oder darin integriert werden.

Assets können auf verschiedene Weise mit einem Inhaltsfragment verwendet werden – mit jeweiligen Vorteilen:

* In ein Fragment **eingefügte Assets** (Fragmente mit gemischten Medien)

   * sind ein integraler Bestandteil des Fragments (siehe [Bestandteile von Inhaltsfragmenten](#constituent-parts-of-a-content-fragment));
   * definieren die Position des Assets;
   * Weitere Informationen finden Sie unter [Einfügen von Assets in Fragmente](content-fragments-variations.md#inserting-assets-into-your-fragment) im Fragment-Editor.

   >[!NOTE]
   >
   >Die in das Inhaltsfragment eingefügten visuellen Assets werden mit dem vorangehenden Absatz verbunden. Beim Hinzufügen des Fragments zu einer Seite werden diese Assets in Beziehung zu diesem Absatz verschoben, wenn Übergangsinhalte hinzugefügt werden.

* **Zugehörige Inhalte**

   * sind zwar mit einem Fragment verbunden, stellen aber keinen festen Bestandteil des Fragments dar (siehe [Bestandteile von Inhaltsfragmenten](#constituent-parts-of-a-content-fragment));
   * ermöglichen eine gewisse Flexibilität bei der Positionierung;
   * sind problemlos verfügbar (als Übergangsinhalte), wenn das Fragment auf einer Seite verwendet wird;
   * weitere Informationen finden Sie unter [Zugehörige Inhalte](content-fragments-assoc-content.md).

* Im Seiten-Editor verfügbare Assets im **Asset-Browser**

   * bieten vollständige Flexibilität bei der Asset-Auswahl;
   * ermöglichen eine gewisse Flexibilität bei der Positionierung;
   * liefern nicht die Möglichkeit, für ein bestimmtes Fragment genehmigt zu werden;
   * weitere Informationen finden Sie unter [Assets-Browser](/help/sites-authoring/author-environment-tools.md#assets-browser).

### Bestandteile von Inhaltsfragmenten {#constituent-parts-of-a-content-fragment}

Inhaltsfragment-Assets setzen sich aus folgenden Teilen zusammen (entweder direkt oder indirekt):

* **Fragmentelementen**

   * Elemente korrelieren mit den Datenfeldern, die Inhalte enthalten.
   * Bei Fragmenten mit strukturiertem Inhalt verwenden Sie ein Inhaltsmodell, um das Inhaltsfragment zu erstellen. Die im Modell angegebenen Elemente (Felder) definieren die Struktur des Fragments. Bei diesen Elementen (Feldern) gibt es verschiedene Datentypen.
   * Für einfache Fragmente:

      * Der Inhalt befindet sich in einem (oder mehreren) mehrzeiligen Textfeld(ern) oder Element(en).
      * Die Elemente werden in der Fragmentvorlage definiert (sie können beim Bearbeiten des Fragments nicht definiert werden; siehe [Inhaltsfragmentvorlagen](/help/sites-developing/content-fragment-templates.md)).

* **Fragmentabsätze**

   * Textblöcke, die:

      * durch vertikale Abstände (Zeilenschaltung) getrennt sind 
      * sich in mehrzeiligen Textelementen befinden, entweder in einfachen oder in strukturierten Fragmenten
   * In den Modi [Rich Text](content-fragments-variations.md#rich-text) und [Markdown](content-fragments-variations.md#markdown) kann ein Absatz als Kopfzeile formatiert werden. In diesem Fall gehören dieser und der folgende Absatz als eine Einheit zusammen.
   * Ermöglichen die Inhaltssteuerung während der Seitenbearbeitung


* **In ein Fragment eingefügte Assets (Fragmente mit gemischten Medien)**

   * Assets (Bilder), die in das eigentliche Fragment eingefügt und als interne Inhalte eines Fragments verwendet werden;
   * sind in das Absatzsystem des Fragments eingebettet;
   * können formatiert werden, wenn das [Fragment auf einer Seite verwendet/referenziert wird](/help/sites-authoring/content-fragments.md);
   * können nur über den Fragment-Editor einem Fragment hinzugefügt, daraus gelöscht oder darin verschoben werden; diese Aktionen können nicht im Seiten-Editor durchgeführt werden;
   * können nur durch das [Rich-Text-Format im Fragment-Editor](content-fragments-variations.md#inserting-assets-into-your-fragment) einem Fragment hinzugefügt, daraus gelöscht oder darin verschoben werden;
   * können nur zu mehrzeiligen Textelementen hinzugefügt werden (beliebiger Fragmenttyp);
   * werden mit dem vorangehenden Text (Absatz) verbunden;

   >[!CAUTION]
   >
   >Kann (versehentlich) aus einem Fragment entfernt werden, indem auf das Nur Text -Format umgestellt wird.

   >[!NOTE]
   >
   >Assets können auch als [zusätzlicher (Übergangs) Inhalt](/help/sites-authoring/content-fragments.md#using-associated-content) hinzugefügt werden, wenn ein Fragment auf einer Seite verwendet wird (bei Nutzung von zugehörigen Inhalten oder Assets aus dem Assets-Browser).

* **Zugehörige Inhalte**

   * Hierbei handelt es sich um externen Inhalt für das Fragment, der jedoch von redaktioneller Relevanz ist. In der Regel sind dies Bilder, Videos oder andere Fragmente.
   * Die einzelnen Assets innerhalb der Sammlung können mit dem Fragment im Seiten-Editor verwendet werden, wenn es einer Seite hinzugefügt wird. Zugehörige Inhalte sind also optional, abhängig von den Anforderungen des jeweiligen Kanals.
   * Die Assets sind [mit Fragmenten über Sammlungen verknüpft](content-fragments-assoc-content.md). Mithilfe verknüpfter Sammlungen kann der Autor entscheiden, welche Assets beim Bearbeiten einer Seite verwendet werden sollen.

      * Sammlungen können Fragmenten über Vorlagen, als Standardinhalt oder von Autoren während der Fragmenterstellung zugeordnet werden.
      * [Asset (DAM)-Sammlungen](managing-collections-touch-ui.md) sind die Basis für die zugehörigen Inhalte von Fragmenten.
   * Sie können auch das eigentliche Fragment zu einer Sammlung hinzufügen und so die Nachverfolgung unterstützen.


* **Fragmentmetadaten**

   * Verwendung der [Assets-Metadatenschemata](metadata.md)
   * Tag-Erstellung möglich:

      * Beim Erstellen und Bearbeiten des Fragments
      * Oder später:

         * Durch Anzeigen/Bearbeiten der **Fragmenteigenschaften** über die Konsole
         * Durch Bearbeiten der **Metadaten** im Fragment-Editor

   >[!CAUTION]
   >
   >Profile für die Metadatenverarbeitung sind nicht für Inhaltsfragmente geeignet.

* **Vorlage**

   * Integraler Bestandteil des Fragments:

      * Jedes Inhaltsfragment hat eine Vorlageninstanz.
      * Die Vorlage kann gelöscht werden.
   * Auf die primäre Vorlage kann über den Fragment-Editor unter **[Varianten](content-fragments-variations.md)** zugegriffen werden.
   * Die Vorlage ist keine Variante an sich, sondern die Grundlage aller Varianten.


* **Varianten**

   * Ausgabedarstellungen von Fragmenttext, eigens zu redaktionellen Zwecken. Diese können mit einem Kanal verbunden sein, doch ist dies nicht obligatorisch; auch für lokale Ad-hoc-Änderungen geeignet;
   * werden als Kopien vom **Master** erstellt, können dann aber nach Bedarf bearbeitet werden; gewöhnlich kommt es zu einer Inhaltsüberlappung zwischen den Varianten;
   * Kann während der Fragmentbearbeitung definiert oder in Fragmentvorlagen vordefiniert werden.
   * werden im Fragment gespeichert, um die Streuung von Inhaltskopien zu vermeiden;
   * können mit der Vorlage [synchronisiert](content-fragments-variations.md#synchronizing-with-master) werden, wenn der Vorlageninhalt aktualisiert wurde;
   * können [zusammengefasst](content-fragments-variations.md#summarizing-text) werden, um Text schnell auf eine vordefinierte Länge zu kürzen;
   * sind auf der Registerkarte [Varianten](content-fragments-variations.md) des Fragment-Editors verfügbar.

### Übergangsinhalte bei der Seitenerstellung mit Inhaltsfragmenten {#in-between-content-when-page-authoring-with-content-fragments}

Übergangsinhalte:

* Sind für die Verwendung im [Seiteneditor bei der Arbeit mit Inhaltsfragmenten](/help/sites-authoring/content-fragments.md) verfügbar.
* Hierbei handelt es sich um [zusätzlichen Inhalt, der im Fluss eines Fragments hinzugefügt wird](/help/sites-authoring/content-fragments.md#adding-in-between-content), sobald dieses auf einer Seite verwendet/referenziert wird.
* Übergangsinhalte können zu jedem beliebigen Fragment hinzugefügt werden, in dem nur ein Element sichtbar ist.
* Zugehörige Inhalte sowie Assets und/oder Komponenten des entsprechenden Browsers können eingesetzt werden.

>[!CAUTION]
>
>Bei Zwischeninhalten handelt es sich um Seiteninhalte. Sie werden nicht im Inhaltsfragment gespeichert.

### Voraussetzungen für Fragmente {#required-by-fragments}

Zum Erstellen, Bearbeiten und Verwenden von Inhaltsfragmenten ist zudem Folgendes erforderlich: 

* **Inhaltsmodelle**

   * sind [aktiviert und anschließend mithilfe der Tools erstellt werden](content-fragments-models.md).
   * Erforderlich für [Erstellen eines strukturierten Fragments](content-fragments-managing.md#creating-content-fragments).
   * Definiert die Struktur eines Fragments (Titel, Inhaltselemente, Tag-Definitionen).
   * Inhaltsmodelldefinitionen erfordern einen Titel und ein Datenelement. Alle weiteren Elemente sind optional. Das Modell definiert einen minimalen Umfang des Fragments und ggf. Standardinhalt. Autoren können die definierte Struktur ändern, wenn sie den Fragmentinhalt erstellen.

* **Fragmentvorlage**

   * Erforderlich für [Erstellen eines einfachen Fragments](content-fragments-managing.md#creating-content-fragments).
   * Normalerweise [während der Projektdurchführung entwickelt wurde](/help/sites-developing/content-fragment-templates.md); kann beim Authoring nicht erstellt werden.
   * Definiert die grundlegenden Eigenschaften eines einfachen Fragments (Titel, Anzahl der Textelemente, Tag-Definitionen).
   * Vorlagendefinitionen erfordern einen Titel und ein Textelement. alles andere ist optional. Die Vorlage definiert einen minimalen Umfang des Fragments und ggf. den Standardinhalt. Autoren können zu einem späteren Zeitpunkt die Definition eines Fragments über die Angaben in der Vorlage hinaus erweitern.

* **Inhaltsfragment-Komponente**

   * Hilft bei der Bereitstellung des Fragments im HTML- und/oder JSON-Format.
   * Erforderlich zum [Referenzieren des Fragments auf einer Seite](/help/sites-authoring/content-fragments.md).
   * Zuständig für das Layout und die Bereitstellung eines Fragments, d. h. Kanäle.
   * Fragmente benötigen eine oder mehrere dedizierte Komponenten zur Definition des Layouts sowie zur Bereitstellung einiger oder aller Elemente/Varianten und zugehörigen Inhalte.
   * Durch Ziehen eines Fragments auf eine Seite während der Bearbeitung wird die erforderliche Komponente automatisch zugewiesen.

## Anwendungsbeispiel {#example-usage}

Ein Fragment samt seinen Elementen und Varianten kann zur Erstellung von kohärentem Inhalt für verschiedene Kanäle verwendet werden. Beim Entwurf eines Fragments muss berücksichtigt werden, welche Elemente wo verwendet werden.

### We.Retail-Beispiel {#we-retail-sample}

Ein Beispielfragment ist zu finden unter:

[http://localhost:4502/assets.html/content/dam/we-retail/en/experiences/arctic-surfing-in-lofoten](http://localhost:4502/assets.html/content/dam/we-retail/en/experiences/arctic-surfing-in-lofoten ) 
