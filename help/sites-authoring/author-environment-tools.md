---
title: Autorenumgebung und Tools
seo-title: Authoring Environment and Tools
description: Die Autorenumgebung von AEM bietet verschiedene Mechanismen für das Organisieren und Bearbeiten von Inhalten
seo-description: The authoring environment of AEM provides various mechanisms for organizing and editing your content
uuid: 2fe17bbf-f431-49bc-9d27-7a95f1f76252
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 4f6a525d-d291-426f-be22-d2ef92c57156
exl-id: 5bb5f984-f741-4185-acb0-ffcf7e116875
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2160'
ht-degree: 83%

---

# Autorenumgebung und Tools{#authoring-the-environment-and-tools}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Die Autorenumgebung von AEM bietet verschiedene Mechanismen für das Organisieren und Bearbeiten von Inhalten. Die verfügbaren Tools können über verschiedene Konsolen und Seiteneditoren aufgerufen werden.

## Verwalten Ihrer Site {#managing-your-site}

Die **Sites** Mit der Konsole können Sie auf Ihrer Website navigieren und diese verwalten. Verwenden Sie dazu die Kopfzeilenleiste, Symbolleiste, Aktionssymbole (für die ausgewählte Ressource zutreffend), Breadcrumbs und ggf. sekundäre Leisten (z. B. Timeline und Verweise).

Beispiel: Kartenansicht:

![chlimage_1-290](assets/chlimage_1-290.png)

## Bearbeiten des Seiteninhalts {#editing-page-content}

Sie können eine Seite mit dem Seiteneditor bearbeiten. Beispiel:

`http://localhost:4502/editor.html/content/we-retail/us/en/equipment.html`

![screen_shot_2018-03-22at141536](assets/screen_shot_2018-03-22at141536.png)

>[!NOTE]
>
>Wenn Sie eine Seite zum ersten Mal zur Bearbeitung öffnen, werden Sie in einer Bildschirmpräsentation durch die Funktionen geführt.
>
>Sie können diese Tour überspringen und jederzeit wiederholen, indem Sie sie im Menü **Seiteninformationen** auswählen.

## Aufrufen der Hilfe   {#accessing-help}

Wenn Sie eine Seite bearbeiten, können Sie folgendermaßen auf die **Hilfe** zugreifen:

* die [**Seiteninformationen**](/help/sites-authoring/editing-page-properties.md#page-properties) Selektor; Hier werden die Einführungsfolien angezeigt (wie beim ersten Zugriff auf den Editor gezeigt).
* die [Konfiguration](/help/sites-authoring/editing-content.md#edit-configure-copy-cut-delete-paste) Dialogfeld für bestimmte Komponenten (mithilfe des Symbols ? Symbol in der Symbolleiste des Dialogfelds); zeigt kontextsensitive Hilfe an.

In den Konsolen stehen weitere [Hilferessourcen zur Verfügung](/help/sites-authoring/basic-handling.md#accessing-help).

## Komponenten-Browser {#components-browser}

Der Komponenten-Browser enthält alle Komponenten, die zur Verwendung auf der aktuellen Seite verfügbar sind. Sie können diese an die gewünschte Position ziehen und dann bearbeiten, um Inhalte hinzuzufügen.

Der Komponenten-Browser befindet sich auf einer Registerkarte im seitlichen Bedienfeld (zusammen mit dem [Asset-Browser](/help/sites-authoring/author-environment-tools.md#assets-browser) und der [Inhaltsstruktur](/help/sites-authoring/author-environment-tools.md#content-tree)). Um das Bedienfeld zu öffnen (oder zu schließen), verwenden Sie das Symbol links oben in der Symbolleiste:

![](do-not-localize/screen_shot_2018-03-22at141659.png)

Wenn Sie das Bedienfeld öffnen, wird es von der linken Seite aus eingeblendet. Wählen Sie hier ggf. die Registerkarte **Komponenten**. Wenn diese geöffnet ist, können Sie alle für die Seite verfügbaren Komponenten durchsuchen.

Das tatsächliche Aussehen und die Nutzung hängen vom verwendeten Gerätetyp ab:

>[!NOTE]
>
>Ein Mobilgerät wird erkannt, wenn die Breite weniger als 1024 Pixel beträgt. Dies kann auch bei einem kleinen Desktop-Fenster der Fall sein.

* **Mobilgerät (z. B. iPad)**

   Der Komponenten-Browser deckt die bearbeitete Seite vollständig ab.

   Um Ihrer Seite Komponenten hinzuzufügen, berühren und halten Sie die gewünschte Komponente und verschieben Sie sie nach rechts - der Komponenten-Browser wird geschlossen und die Seite wird erneut angezeigt - wo Sie die Komponente platzieren können.

   ![screen_shot_2018-03-22at141752](assets/screen_shot_2018-03-22at141752.png)

* **Desktop-Gerät**

   Der Komponenten-Browser wird auf der linken Seite des Fensters geöffnet.

   Um der Seite eine Komponente hinzuzufügen, klicken Sie auf die gewünschte Komponente und ziehen Sie sie an die gewünschte Position.

   ![screen_shot_2018-03-22at141808](assets/screen_shot_2018-03-22at141808.png)

   Komponenten werden wie folgt dargestellt:

   * Komponentenname
   * Komponentengruppe (in grau)
   * Symbol oder Abkürzung

      * Die Symbole für die Standardkomponenten sind monochrom dargestellt.
      * Abkürzungen sind immer die ersten beiden Zeichen des Komponentennamen.

   In der oberen Symbolleiste des Komponenten-Browsers haben Sie folgende Möglichkeiten:

   * Komponenten nach Namen filtern
   * mittels Dropdown-Auswahl die Anzeige auf eine bestimmte Gruppe begrenzen

   Für eine detailliertere Beschreibung der Komponente können Sie im Browser Komponenten auf das Informationssymbol neben der Komponente tippen/klicken (falls verfügbar).

   ![screen_shot_2018-03-22at141929](assets/screen_shot_2018-03-22at141929.png)

   Weiterführende Informationen zu den verfügbaren Komponenten finden Sie unter [Komponenten-Konsole](/help/sites-authoring/default-components-console.md).

## Asset-Browser {#assets-browser}

Der Asset-Browser enthält alle Assets, die auf Ihrer aktuellen Seite direkt verwendet werden können.

Der Asset-Browser befindet sich auf einer Registerkarte im seitlichen Bedienfeld (zusammen mit dem [Komponenten-Browser](/help/sites-authoring/author-environment-tools.md#components-browser) und der [Inhaltsstruktur](/help/sites-authoring/author-environment-tools.md#content-tree)). Um das Bedienfeld zu öffnen (oder zu schließen), verwenden Sie das Symbol links oben in der Symbolleiste:

![](do-not-localize/screen_shot_2018-03-22at141659-1.png)

Wenn Sie das Bedienfeld öffnen, wird es von der linken Seite aus eingeblendet. Wählen Sie hier ggf. die Registerkarte **Assets**.

![](do-not-localize/screen_shot_2018-03-22at142035.png)

Wenn der Asset-Browser geöffnet ist, können Sie alle für die Seite verfügbaren Assets durchsuchen. Bei Bedarf können Sie die Liste durch Scrollen unendlich erweitern.

![chlimage_1-291](assets/chlimage_1-291.png)

Um ein Asset zu der Seite hinzuzufügen, wählen Sie es aus und ziehen Sie es an die gewünschte Position. Dabei kann es sich um Folgendes handeln:

* Eine vorhandene Komponente des entsprechenden Typs.

   * Sie können beispielsweise ein Asset des Typs „Bild“ auf eine Bildkomponente ziehen.

* Ein [Platzhalter](/help/sites-authoring/editing-content.md#component-placeholder) im Absatzsystem zum Erstellen einer neuen Komponente des entsprechenden Typs.

   * Sie können beispielsweise ein Asset des Typs &quot;Bild&quot;auf das Absatzsystem ziehen, um eine Bildkomponente zu erstellen.

>[!NOTE]
>
>Dies ist für spezielle Assets und Komponententypen verfügbar. Weitere Einzelheiten finden Sie unter [Einfügen einer Komponente mit dem Asset-Browser](/help/sites-authoring/editing-content.md#inserting-a-component-using-the-assets-browser).

In der Symbolleiste des Asset-Browsers können Sie Assets nach folgenden Kriterien filtern:

* Name
* Pfad
* Asset-Typ, z. B. Bilder, Manuskripte, Dokumente, Videos, Seiten, Absätze oder Produkte
* Asset-Merkmale, z. B. Ausrichtung (Hochformat, Querformat, quadratisch) und Stil (farbig, monochrom, Graustufen)

   * Nur für bestimmte Asset-Typen verfügbar

Das tatsächliche Aussehen und die Nutzung hängen vom verwendeten Gerätetyp ab:

>[!NOTE]
>
>Ein Mobilgerät wird erkannt, wenn die Breite geringer als 1.024 Pixel ist, d. h. auch bei einem kleinen Desktop-Fenster.

* **Mobilgerät wie iPad**

   Der Asset-Browser deckt die gesamte bearbeitete Seite ab.

   Um der Seite ein Asset hinzuzufügen, berühren und halten Sie das gewünschte Asset und verschieben Sie es nach rechts. Der Asset-Browser wird geschlossen und die Seite wird erneut angezeigt. Jetzt können Sie das Asset der gewünschten Komponente hinzufügen.

   ![screen_shot_2018-03-22at142223](assets/screen_shot_2018-03-22at142223.png)

* **Desktop-Gerät**

   Der Asset-Browser wird auf der linken Seite des Fensters geöffnet.

   Um ein Asset zu Ihrer Seite hinzuzufügen, klicken Sie auf das gewünschte Asset und ziehen Sie es auf die benötigte Komponente oder Stelle.

   ![screen_shot_2018-03-22at142337](assets/screen_shot_2018-03-22at142337.png)

Wenn Sie eine Änderung an einem der Assets vornehmen möchten, können Sie den [Asset-Editor](/help/assets/managing-assets-touch-ui.md) auch direkt über den Browser starten. Klicken Sie dazu einfach auf das Bearbeitungssymbol neben dem Asset-Namen.

![](do-not-localize/screen_shot_2018-03-22at142448.png)

## Inhaltsstruktur {#content-tree}

Die **Inhaltsstruktur** bietet einen Überblick über alle auf der Seite verwendeten Komponenten in einer hierarchischen Darstellung, sodass Sie direkt feststellen können, wie die Seite aufgebaut ist.

Die Inhaltsstruktur befindet sich auf einer Registerkarte im seitlichen Bedienfeld (zusammen mit dem Asset-Browser). Um das Bedienfeld zu öffnen (oder zu schließen), verwenden Sie das Symbol links oben in der Symbolleiste:

![](do-not-localize/screen_shot_2018-03-22at142042.png)

Wenn Sie das Bedienfeld öffnen, wird es von der linken Seite aus eingeblendet. Wählen Sie ggf. die Registerkarte **Inhaltsstruktur**. Mit dieser Strukturansicht Ihrer Seite oder Vorlage können Sie leicht nachvollziehen, wie die darauf verwendeten Komponenten hierarchisch strukturiert sind. Auf einer komplexer gestalteten Seite können Sie so zudem einfacher zwischen Komponenten auf der Seite wechseln.

![screen_shot_2018-03-22at142526](assets/screen_shot_2018-03-22at142526.png)

Eine Seite kann problemlos aus vielen Komponenten desselben Typs bestehen. Daher wird in der Komponentenstruktur nach dem Namen des Komponententyps (in Schwarz) beschreibender Text (grau) angezeigt. Der Text für diese Beschreibung wird aus den allgemeinen Eigenschaften der Komponente (z. B. Titel oder Text) entnommen.

Die Komponententypen werden in der für die Benutzeroberfläche ausgewählten Sprache angezeigt, die Beschreibung dagegen in der Sprache, die für die Seite verwendet wird.

Durch Klicken auf den Richtungspfeil neben einer Komponente wird die entsprechende Ebene ein- bzw. ausgeblendet.

![screen_shot_2018-03-22at142559](assets/screen_shot_2018-03-22at142559.png)

Durch Klicken auf die Komponente wird diese im Seiteneditor markiert.

![screen_shot_2018-03-22at142647](assets/screen_shot_2018-03-22at142647.png)

Wenn Sie in der Struktur auf eine Komponente klicken, die bearbeitbar ist, wird rechts neben ihrem Namen ein Schraubenschlüssel-Symbol angezeigt. Durch Klicken auf dieses Symbol können Sie das Dialogfeld für die Bearbeitung der Komponente direkt aufrufen.

![](do-not-localize/screen_shot_2018-03-22at142725.png)

>[!NOTE]
>
>Beim Bearbeiten einer Seite auf einem Mobilgerät ist die Inhaltsstruktur nicht verfügbar (wenn die Browser-Breite weniger als 1.024 Pixel beträgt).

## Fragmente: Browser für zugehörige Inhalte {#fragments-associated-content-browser}

Wenn Ihre Seite Inhaltsfragmente enthält, haben Sie auch Zugriff auf den [Browser für zugehörige Inhalte](/help/sites-authoring/content-fragments.md#using-associated-content).

## Verweise {#references}

**Verweise** zeigen Verbindungen zur ausgewählten Seite an:

* Blueprints
* Launches
* Live Copies
* Sprachkopien
* Verwendung der Referenzkomponente
* Verweise auf Produktseiten (auf der Konsole „E-Commerce - Produkte“)

Öffnen Sie die gewünschte Konsole, navigieren Sie zur gewünschten Ressource und öffnen Sie **Verweise** wie folgt:

![screen_shot_2018-03-22at153653](assets/screen_shot_2018-03-22at153653.png)

[Wählen Sie die gewünschte Ressource aus](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources), um eine Liste der Verweistypen anzuzeigen, die für diese Ressource relevant sind:

![screen_shot_2018-03-22at153731](assets/screen_shot_2018-03-22at153731.png)

Wählen Sie den gewünschten Verweistyp, um weitere Informationen anzuzeigen: In bestimmten Situationen sind weitere Aktionen verfügbar, wenn Sie einen bestimmten Verweis auswählen:

* Instanzen der Referenzkomponente (z. B. Navigieren zur referenzierenden/referenzierten Seite)
* [Verweise auf Produktseiten](/help/sites-administering/generic.md#showing-product-references) (verfügbar in der Konsole „E-Commerce - Produkte“)
* [Launches](/help/sites-authoring/launches.md)
* [Live Copies](/help/sites-administering/msm.md) zeigt die Pfade aller Live Copies an, die auf der gewählten Ressource basieren.
* [Blueprint](/help/sites-administering/msm-best-practices.md)
* [Sprachkopien](/help/sites-administering/tc-manage.md#creating-translation-projects-using-the-references-panel)

Sie können beispielsweise einen beschädigten Verweis innerhalb einer Verweiskomponente reparieren:

![chlimage_1-292](assets/chlimage_1-292.png)

## Ereignisse: Zeitleiste {#events-timeline}

Bei bestimmten Ressourcen (z. B. Seiten aus der **Sites-Konsole** oder Assets aus der **Asset-Konsole**) kann die [Zeitleiste dazu verwendet werden, die zuletzt durchgeführten Aktivitäten für ausgewählte Elemente anzuzeigen](/help/sites-authoring/basic-handling.md#timeline).

Öffnen Sie die gewünschte Konsole, navigieren Sie zur gewünschten Ressource und öffnen Sie die **Zeitleiste** wie folgt:

![screen_shot_2018-03-22at153952](assets/screen_shot_2018-03-22at153952.png)

[Wählen Sie die gewünschte Ressource ](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources)und danach entweder **Alle anzeigen** oder **Aktivitäten** aus, um die mit den ausgewählten Ressourcen zuletzt ausgeführten Aktionen aufzulisten:

![screen_shot_2018-03-22at154130](assets/screen_shot_2018-03-22at154130.png)

## Seiteninformationen {#page-information}

Mit „Seiteninformationen“ (Equalizer-Symbol) öffnen Sie ein Menü, das auch Details zur letzten Bearbeitung und zur letzten Aktivierung enthält. Je nach den Eigenschaften der Seite (und ihrer Site) stehen mehr oder weniger Optionen zur Verfügung:

![screen_shot_2018-03-22at154210](assets/screen_shot_2018-03-22at154210.png)

* [Eigenschaften öffnen](/help/sites-authoring/editing-page-properties.md)
* [Seiten-Rollout](/help/sites-administering/msm.md#msm-from-the-ui)
* [Workflow starten](/help/sites-authoring/workflows-applying.md#starting-a-workflow-from-the-page-editor)
* [Sperren einer Seite](/help/sites-authoring/editing-content.md#locking-a-page)
* [Seite veröffentlichen](/help/sites-authoring/publishing-pages.md#publishing-pages)
* [Veröffentlichen einer Seite aufheben](/help/sites-authoring/publishing-pages.md#unpublishing-pages)
* [Als veröffentlicht anzeigen](/help/sites-authoring/editing-content.md#view-as-published)
* [In Admin anzeigen](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources)
* [Hilfe](/help/sites-authoring/basic-handling.md#accessing-help)

Beispiel: **Seiteninformationen** verfügt außerdem über die folgenden Optionen:

* [Launch bewerben](/help/sites-authoring/launches-promoting.md) wenn es sich bei der Seite um einen Launch handelt.
* [Vorlage bearbeiten](/help/sites-authoring/templates.md) wenn die Seite auf einer [bearbeitbare Vorlage](/help/sites-authoring/templates.md#editable-and-static-templates)

* [In klassischer Benutzeroberfläche öffnen](/help/sites-authoring/select-ui.md#switching-to-classic-ui-when-editing-a-page), wenn diese Option [von einer bzw. einem Admin aktiviert](/help/sites-administering/enable-classic-ui-editor.md) wurde.

Darüber hinaus können über die **Seiteninformationen** ggf. auch Analysen und Empfehlungen aufgerufen werden.

## Seitenmodi {#page-modes}

Für die Bearbeitung von Seiten stehen verschiedene Modi zur Verfügung, über die jeweils unterschiedliche Aktionen durchgeführt werden können:

* [Bearbeiten:](/help/sites-authoring/editing-content.md) Der Modus zum Bearbeiten des Seiteninhalts.
* [Layout](/help/sites-authoring/responsive-layout.md): Ermöglicht es Ihnen, Ihr responsives Layout gerätespezifisch zu erstellen und zu bearbeiten (wenn die Seite auf einem Layout-Container basiert).

* [Strukturvorlage:](/help/sites-authoring/scaffolding.md) Hilft Ihnen bei der Erstellung einer großen Anzahl von Seiten, die unterschiedliche Inhalte, aber eine einheitliche Struktur aufweisen sollen.
* [Entwickler:](/help/sites-developing/developer-mode.md) Ermöglicht die Durchführung verschiedener Aktionen (Berechtigungen erforderlich), zu denen die Untersuchung der technischen Details einer Seite und von deren Komponenten gehört.

* [Design](/help/sites-authoring/default-components-designmode.md) - ermöglicht es Ihnen, Komponenten für die Verwendung auf einer Seite zu aktivieren bzw. zu deaktivieren und das Design der Komponente zu konfigurieren (wenn die Seite auf einer [statische Vorlage](/help/sites-authoring/templates.md#editable-and-static-templates)).

* [Zielsetzung:](/help/sites-authoring/content-targeting-touch.md) Steigerung der Inhaltsrelevanz durch Zielsetzung und Messung über alle Kanäle hinweg.
* [Activity Map:](/help/sites-authoring/pa-using.md) Zeigt Analytics-Daten für die Seite an.

* [Timewarp](/help/sites-authoring/working-with-page-versions.md#timewarp): Ermöglicht es, eine Seite in dem Zustand anzuzeigen, den sie zu einem früheren Zeitpunkt aufgewiesen hat.
* [Live Copy-Status:](/help/sites-authoring/editing-content.md#live-copy-status) Für einen schnellen Überblick über den Live Copy-Status und darüber, welche Komponenten übernommen oder nicht übernommen wurden.
* [Vorschau](/help/sites-authoring/editing-content.md#previewing-pages): Dient zur Anzeige der Darstellung der Seite in der Veröffentlichungsumgebung oder zur Navigation anhand der Links im Inhalt.

* [Anmerken](/help/sites-authoring/annotations.md): In diesem Modus können Sie Anmerkungen auf der Seite hinzufügen oder anzeigen.

Sie können darauf über das Symbol oben rechts im Bildschirm zugreifen. Das Symbol ändert sich je nach verwendetem Modus:

![chlimage_1-293](assets/chlimage_1-293.png)

>[!NOTE]
>
>* Abhängig von den Merkmalen der Seite sind einige Modi ggf. nicht verfügbar.
>* Für den Zugriff auf einige Modi sind die entsprechenden Berechtigungen erforderlich.
>* Aus Platzgründen steht der Entwicklermodus auf Mobilgeräten nicht zur Verfügung.
>* Mit dem [Tastaturbefehl](/help/sites-authoring/page-authoring-keyboard-shortcuts.md) `Ctrl-Shift-M` (Strg+Umschalt+M) können Sie zwischen der **Vorschau** und dem aktuell ausgewählten Modus (z. B. **Bearbeiten**, **Layout** usw.) wechseln.
>


## Pfadauswahl {#path-selection}

Oft muss bei der Bearbeitung einer Seite eine andere Ressource ausgewählt werden (z. B. zum Definieren eines Links zu einer anderen Seite/Ressource oder zum Auswählen eines Bilds). Zur Vereinfachung der Pfadauswahl werden Eingaben in den [Pfad-Feldern](/help/sites-authoring/author-environment-tools.md#path-fields) automatisch ausgefüllt. Ergänzend dazu stehen zudem leistungsstarke Auswahlfunktionen im [Pfad-Browser](/help/sites-authoring/author-environment-tools.md#path-browser) zur Verfügung.

### Pfadfelder {#path-fields}

Im vorliegenden Beispiel wird zur Verdeutlichung die Bildkomponente verwendet. Weitere Informationen zur Verwendung und Bearbeitung von Komponenten finden Sie unter [Komponenten für die Seitenbearbeitung](/help/sites-authoring/default-components.md).

Pfadfelder verfügen jetzt über automatische Vervollständigungs- und Vorausschau-Funktionen, um die Suche nach einer Ressource zu vereinfachen. Beginnen Sie einfach mit der Eingabe in das Pfadfeld und die AEM bietet Ihnen passende Pfade während der Eingabe.

![screen_shot_2018-03-22at154403](assets/screen_shot_2018-03-22at154403.png)

Durch Klicken auf die Schaltfläche **Auswahl-Dialogfeld öffnen** im Pfadfeld wird das Dialogfeld [Pfad-Browser](/help/sites-authoring/author-environment-tools.md#path-browser) geöffnet, in dem Optionen für eine präzisere Auswahl zur Verfügung stehen.

![](do-not-localize/screen_shot_2018-03-22at154427.png)

### Pfad-Browser {#path-browser}

Der Pfad-Browser ist wie die [Spaltenansicht](/help/sites-authoring/basic-handling.md#column-view) der Sites-Konsole aufgebaut und ermöglicht eine präzisere Auswahl der Ressourcen.

![screen_shot_2018-03-22at154521](assets/screen_shot_2018-03-22at154521.png)

Sobald eine Ressource ausgewählt wird, wird die Schaltfläche **Auswählen** oben rechts im Dialogfeld aktiviert. Klicken/tippen Sie darauf, um die Auswahl zu bestätigen, oder heben Sie die Auswahl über **Abbrechen** auf.

Wenn der Kontext die Auswahl mehrerer Ressourcen zulässt, wird bei Auswahl einer Ressource auch die Schaltfläche Auswählen aktiviert, aber auch die Anzahl der ausgewählten Ressourcen wird oben rechts im Fenster angezeigt. Klicken Sie auf das X neben der Zahl, um die Auswahl für alle aufzuheben.

![chlimage_1-294](assets/chlimage_1-294.png)

Mit den Breadcrumbs können Sie schnell in die Ressourcenhierarchie springen.

![chlimage_1-295](assets/chlimage_1-295.png)

Darüber hinaus können Sie auch jederzeit das Suchfeld oben im Dialogfeld verwenden.

![chlimage_1-296](assets/chlimage_1-296.png)

Klicken Sie im Suchfeld auf X, wenn Sie die Suche löschen möchten.

Sie können Ihre Suche auch eingrenzen, indem Sie die Filteroptionen einblenden und die Ergebnisse nach Pfad filtern.

![chlimage_1-297](assets/chlimage_1-297.png)

## Tastaturbefehle {#keyboard-shortcuts}

Für die Bedienung stehen verschiedene [Tastaturbefehle](/help/sites-authoring/page-authoring-keyboard-shortcuts.md) zur Verfügung.
