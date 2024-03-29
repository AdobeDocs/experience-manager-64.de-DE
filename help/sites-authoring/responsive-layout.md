---
title: Responsives Layout
seo-title: Responsive Layout
description: AEM ermöglicht Ihnen die Erstellung eines responsiven Layouts für Ihre Seiten
seo-description: AEM allows you to realize a responsive layout for your pages
uuid: 4db45d78-9fca-4251-b504-ae3481fd9a8b
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 668d1a8a-c757-4c9f-833f-e5dada4d0384
exl-id: 788bb439-fb8a-4ab9-b367-cea6a17c0c43
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1821'
ht-degree: 60%

---

# Responsives Layout{#responsive-layout}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

AEM ermöglicht Ihnen ein responsives Layout für Ihre Seiten mithilfe der **Layout-Container** -Komponente.

Dies bietet ein Absatzsystem, mit dem Sie Komponenten in einem responsiven Raster positionieren können. Dieses Raster kann das Layout entsprechend der Geräte-/Fenstergröße und dem Format neu anordnen. Die Komponente wird zusammen mit dem [**Layout**-Modus](/help/sites-authoring/responsive-layout.md#defining-layouts-layout-mode) verwendet, in dem Sie Ihr responsives Layout geräteabhängig erstellen und bearbeiten können.

Der Layout-Container:

* Bietet horizontale Ausrichtung am Raster sowie die Möglichkeit, Komponenten nebeneinander im Raster zu platzieren und zu definieren, wann sie reduziert/umfließen sollen.
* Verwendet vordefinierte Breakpoints (z. B. für Smartphone, Tablet usw.) , damit Sie das erforderliche Verhalten von Inhalten für zugehörige Geräte/Ausrichtungen definieren können.

   * Sie können beispielsweise die Komponentengröße anpassen oder festlegen, ob die Komponente auf bestimmten Geräten angezeigt werden soll.

* Kann verschachtelt werden, um die Spaltensteuerung zuzulassen.

Der Benutzer kann dann sehen, wie der Inhalt mithilfe des Emulators für bestimmte Geräte gerendert wird.

>[!CAUTION]
>
>Obwohl die Layout-Container-Komponente in der klassischen Benutzeroberfläche verfügbar ist, ist ihre vollständige Funktionalität nur in der Touch-optimierten Benutzeroberfläche verfügbar und wird unterstützt.

Das responsive Layout für Ihre Seiten wird von AEM mithilfe einer Kombination von Mechanismen ermöglicht:

* [**Layout-Container-Komponente**](#adding-a-layout-container-and-its-content-edit-mode)

   Diese Komponente ist im [Komponenten-Browser](/help/sites-authoring/author-environment-tools.md#components-browser) verfügbar. Sie bietet ein Raster-Absatzsystem, mit dem Sie Komponenten in einem responsiven Raster hinzufügen und positionieren können. Dieses kann auf Ihrer Seite auch als Standardabsatzsystem festgelegt werden.

* [**Layout-Modus**](/help/sites-authoring/responsive-layout.md#defining-layouts-layout-mode)

   Sobald der Layout-Container auf der Seite positioniert ist, können Sie im **Layout**-Modus Inhalte im responsiven Raster positionieren.

* [**Emulator**](#selecting-a-device-to-emulate)
Hiermit können Sie responsive Websites erstellen und bearbeiten, deren Layout durch eine interaktive Größenanpassung der Komponenten an die Größe des Geräts oder Fensters angepasst wird. Der Benutzer kann sich dann mit dem Emulator ansehen, wie der Inhalt für bestimmte Geräte gerendert wird.

Mit diesen responsiven Rastermechanismen können Sie:

* Verwenden Sie Haltepunkte, um verschiedene Inhaltslayouts basierend auf der Gerätebreite (bezogen auf Gerätetyp und Ausrichtung) zu definieren.
* Verwendung derselben Breakpoints und Inhaltslayouts, um sicherzustellen, dass Ihr Inhalt an die Größe des Browser-Fensters auf dem Desktop angepasst wird.
* Mit der horizontalen Ausrichtung am Raster können Sie Komponenten im Raster platzieren, die Größe anpassen und definieren, wann ein Reduzieren/Umfließen daneben oder drüber/darunter erfolgen soll.
* Ausblenden von Komponenten für bestimmte Gerätelayouts.
* Realisieren einer Spaltensteuerung.

Je nach Projekt kann der Layout-Container als standardmäßiges Absatzsystem für Ihre Seiten oder als Komponente verwendet werden, die über den Komponenten-Browser zu Ihrer Seite hinzugefügt werden kann (oder beides).

>[!NOTE]
>
>Adobe stellt eine [GitHub-Dokumentation](https://adobe-marketing-cloud.github.io/aem-responsivegrid/) zum responsiven Layout als Referenz bereit. Diese kann Frontend-Entwicklern zur Verfügung gestellt werden, damit sie das AEM-Raster außerhalb von AEM verwenden können, um beispielsweise statische HTML-Modelle für künftige AEM Sites zu erstellen.

>[!NOTE]
>
>Die Verwendung des obigen Mechanismus wird durch die Konfiguration der Vorlage aktiviert. Weitere Informationen finden Sie unter [Konfigurieren des responsiven Layouts](/help/sites-administering/configuring-responsive-layout.md).

## Layout-Definitionen, Geräteemulation und Breakpoints {#layout-definitions-device-emulation-and-breakpoints}

Wenn Sie den Inhalt Ihrer Website erstellen, möchten Sie sicherstellen, dass Ihr Inhalt auf dem für die Anzeige verwendeten Gerät angemessen angezeigt wird.

Mit AEM können Sie Layouts definieren, die von der Breite des Geräts abhängen:

* Mit dem Emulator können Sie diese Layouts auf einer Reihe von Geräten emulieren. Abgesehen vom Gerätetyp kann sich auch die durch die Option **Gerät drehen** ausgewählte Ausrichtung auf den ausgewählten Breakpoint auswirken, da sich die Breite ändert.
* Breakpoints sind Punkte, die die Layout-Definitionen trennen.

   * Sie definieren die maximale Breite (in Pixel) der Geräte, die ein bestimmtes Layout verwenden.
   * Breakpoints gelten in der Regel für eine Auswahl an Geräten und hängen von der Breite der Displays ab.
   * Ein Breakpoint reicht nach links bis zum nächsten Breakpoint.
   * Sie können den Breakpoint nicht spezifisch auswählen - durch die Auswahl eines Geräts und einer Ausrichtung wird der entsprechende Breakpoint automatisch ausgewählt.

Das Gerät **Desktop**, das keine bestimmte Breite aufweist und sich auf den Standard-Breakpoint bezieht (d. h. auf alles über dem letzten konfigurierten Breakpoint).

>[!NOTE]
>
>Es wäre möglich, Breakpoints für jedes einzelne Gerät zu definieren. Dies würde jedoch den Aufwand für die Layout-Definition und die Wartung deutlich erhöhen.

Wenn Sie den Emulator verwenden, wählen Sie ein bestimmtes Gerät für die Emulation und Layoutdefinition aus und der zugehörige Breakpoint wird ebenfalls hervorgehoben. Alle von Ihnen vorgenommenen Layoutänderungen gelten für andere Geräte, für die der Breakpoint gilt, d. h. alle Geräte, die links neben der aktiven Breakpoint-Markierung, aber vor der nächsten Breakpoint-Markierung positioniert sind.

Wenn Sie beispielsweise das Gerät auswählen **iPhone 6 Plus** (definiert mit einer Breite von 540 Pixel) für Emulation und Layout, der Breakpoint **Telefon** (definiert als 768 Pixel) wird ebenfalls aktiviert. Alle Layoutänderungen, die Sie für die **iPhone 6** auf andere Geräte im Rahmen der **Telefon** Breakpoint, z. B. **iPhone 5** (definiert als 320 Pixel).

![screen_shot_2018-03-23at084058](assets/screen_shot_2018-03-23at084058.png)

## Auswahl eines zu emulierenden Geräts {#selecting-a-device-to-emulate}

1. Öffnen Sie die gewünschte Seite zur Bearbeitung. Beispiel:

   `http://localhost:4502/editor.html/content/we-retail/us/en/experience.html`

1. Wählen Sie in der oberen Symbolleiste das Symbol **Emulator** aus:

   ![](do-not-localize/screen_shot_2018-03-23at084256.png)

1. Die Emulator-Symbolleiste wird geöffnet.

   ![screen_shot_2018-03-23at084551](assets/screen_shot_2018-03-23at084551.png)

   In der Emulator-Symbolleiste werden zusätzliche Layout-Optionen angezeigt:

   * **Gerät drehen** - Ermöglicht das Drehen eines Geräts von der vertikalen (Hochformat-) Ausrichtung in die horizontale (Querformat-) Ausrichtung und umgekehrt.

   ![](do-not-localize/screen_shot_2018-03-23at084612.png) ![](do-not-localize/screen_shot_2018-03-23at084637.png)

   * **Gerät auswählen** – Ermöglicht es Ihnen, ein bestimmtes Gerät anzugeben, das aus einer Liste emuliert werden soll (Einzelheiten dazu werden im nächsten Schritt beschrieben).

   ![](do-not-localize/screen_shot_2018-03-23at084743.png)

1. Um ein bestimmtes zu emulierendes Gerät auszuwählen, haben Sie folgende Möglichkeiten:

   * Verwenden Sie das Symbol Gerät auswählen und wählen Sie aus einer Dropdown-Auswahl aus.
   * Tippen/klicken Sie auf der Emulator-Symbolleiste auf das Gerätezeichen.

   ![screen_shot_2018-03-23at084818](assets/screen_shot_2018-03-23at084818.png)

1. Nachdem Sie ein bestimmtes Gerät ausgewählt haben, sind folgende Möglichkeiten verfügbar:

   * Sie können die aktive Markierung für das ausgewählte Gerät anzeigen, z. B. **iPad**.
   * Sie können die aktive Markierung für den entsprechenden [Breakpoint](/help/sites-authoring/responsive-layout.md#layout-definitions-device-emulation-and-breakpoints) anzeigen, z. B. **Tablet**.

   ![screen_shot_2018-03-23at084932](assets/screen_shot_2018-03-23at084932.png)

   * Die gepunktete blaue Linie stellt den *Falz* für das ausgewählte Gerät dar (in diesem Fall ein **iPhone 6**).

   ![screen_shot_2018-03-23at084947](assets/screen_shot_2018-03-23at084947.png)

   * Die Kante kann auch als Seitenzeilenumbruch betrachtet werden (nicht zu verwechseln mit der [Breakpoints](/help/sites-authoring/responsive-layout.md#layout-definitions-device-emulation-and-breakpoints)) für den Inhalt. Diese wird angezeigt, um zu veranschaulichen, welchen Teil des Inhalts der Benutzer vor dem Scrollen auf dem Gerät sehen wird.
   * Die Linie für die Kante wird nicht angezeigt, wenn die Höhe des zu emulierenden Geräts größer als die Bildschirmgröße ist.
   * Der Falz wird aus Komfortgründen für Autoren, aber nicht auf der veröffentlichten Seite angezeigt.



## Hinzufügen eines Layout-Containers und seiner Inhalte (Bearbeitungsmodus) {#adding-a-layout-container-and-its-content-edit-mode}

Ein **Layout-Container** ist ein Absatzsystem mit folgenden Eigenschaften:

* Enthält andere Komponenten.
* Definiert das Layout.
* Reagiert auf Änderungen.

>[!NOTE]
>
>Falls er noch nicht verfügbar ist, muss der **Layout-Container** explizit [für ein Absatzsystem/eine Seite aktiviert werden](/help/sites-administering/configuring-responsive-layout.md) (z. B. über den [**Design**-Modus](/help/sites-authoring/default-components-designmode.md)).

1. Der **Layout-Container** ist als Standardkomponente im [Komponentenbrowser](/help/sites-authoring/author-environment-tools.md#components-browser) verfügbar. Von hier können Sie ihn an die gewünschte Position auf der Seite ziehen, nach der der Platzhalter **Komponenten hierher ziehen** angezeigt wird.
1. Anschließend können Sie dem Layout-Container Komponenten hinzufügen. Diese Komponenten enthalten den tatsächlichen Inhalt:

   ![screen_shot_2018-03-23at085500](assets/screen_shot_2018-03-23at085500.png)

## Auswählen und Bearbeiten eines Layout-Containers (Bearbeitungsmodus) {#selecting-and-taking-action-on-a-layout-container-edit-mode}

Einen Layout-Container können Sie wie andere Komponenten im **Bearbeitungsmodus** auswählen und anschließend bearbeiten (ausschneiden, kopieren, löschen):

>[!CAUTION]
>
>Da ein Layout-Container ein Absatzsystem ist, werden beim Löschen der Komponente sowohl das Layout-Raster als auch alle Komponenten (und deren Inhalt) gelöscht, die sich im Container befinden.

1. Wenn Sie den Mauszeiger über den Rasterplatzhalter bewegen oder darauf tippen, wird das Aktionsmenü angezeigt.

   ![screen_shot_2018-03-23at085357](assets/screen_shot_2018-03-23at085357.png)

   Wählen Sie daraufhin die Option **Übergeordnetes Element** aus.

   ![](do-not-localize/screen_shot_2018-03-23at085417.png)

1. Wenn die Layout-Komponente verschachtelt ist, wählen Sie die **Übergeordnet** bietet eine Dropdown-Auswahl, über die Sie den verschachtelten Layout-Container oder dessen übergeordnete Elemente auswählen können.

   Wenn Sie den Mauszeiger über die Namen der Container in der Dropdown-Liste bewegen, werden ihre Umrisse auf der Seite angezeigt.

   * Der am wenigsten verschachtelte Layout-Container wird schwarz dargestellt.
   * Der nächstniedrigste verschachtelte Layout-Container ist dunkelgrau.
   * Jeder aufeinander folgende Behälter ist in einen helleren Schatten grau gehalten.

   ![screen_shot_2018-03-23at085636](assets/screen_shot_2018-03-23at085636.png)

1. Dadurch wird das gesamte Raster mit den Inhalten markiert. Die Aktionssymbolleiste wird angezeigt, über die Sie eine Aktion auswählen können, z. B. **Löschen**.

   ![screen_shot_2018-03-23at085724](assets/screen_shot_2018-03-23at085724.png)

## Definieren von Layouts (Layout-Modus) {#defining-layouts-layout-mode}

>[!NOTE]
>
>Sie können für jeden [Breakpoint](#layout-definitions-device-emulation-and-breakpoints) (der durch den emulierten Gerätetyp und die Ausrichtung bestimmt wird) ein eigenes Layout definieren.

Das Layout eines mit dem Layout-Container implementierten responsiven Rasters muss im **Layout**-Modus konfiguriert werden.

Der **Layout**-Modus kann auf zwei Arten aktiviert werden.

* Durch Verwenden des [Modusmenüs in der Symbolleiste](/help/sites-authoring/author-environment-tools.md#page-modes) und Auswählen des **Layout**-Modus

   * Wählen Sie den **Layout**-Modus so aus, wie Sie den Modus **Bearbeiten** oder **Targeting** auswählen.
   * Der **Layout**-Modus wird zunächst automatisch beibehalten. Sie können den **Layout**-Modus nur beenden, indem Sie über die Modusauswahl einen anderen Modus auswählen.

* Wann [Bearbeiten einer einzelnen Komponente.](/help/sites-authoring/editing-content.md#edit-component-layout)

   * Durch Verwendung der Variablen **Layout** im Schnellaktionsmenü der Komponente können Sie zu **Layout** -Modus.
   * **Layout** -Modus bleibt beim Bearbeiten der Komponente bestehen und wird auf **Bearbeiten** Modus, sobald der Fokus auf eine andere Komponente wechselt.

Im Layout-Modus können Sie verschiedene Aktionen für ein Raster ausführen:

* Ändern Sie die Größe der Inhaltskomponenten mithilfe der blauen Punkte. Die Größenanpassung erfolgt immer am Raster. Bei der Größenanpassung wird das Hintergrundraster angezeigt, um die Ausrichtung zu erleichtern:

   ![screen_shot_2018-03-23at090140](assets/screen_shot_2018-03-23at090140.png)

   >[!NOTE]
   >
   >Wenn Sie die Größe von Komponenten wie **Bildern** ändern, bleiben die Proportionen und Seitenverhältnisse erhalten.

* Wenn Sie auf eine Inhaltskomponente klicken/tippen, bietet Ihnen die Symbolleiste folgende Möglichkeiten:

   * **Übergeordnetes Element**

      Ermöglicht die Auswahl der gesamten Layout-Container-Komponente, um diese insgesamt zu bearbeiten.

   * **In neue Zeile verschieben**

      Die Komponente wird abhängig von dem innerhalb des Rasters verfügbaren Platz in eine neue Zeile verschoben.

   * **Komponente ausblenden**

      Die Komponente wird unsichtbar (sie kann über die Symbolleiste des Layout-Containers wiederhergestellt werden).
   ![screen_shot_2018-03-23at090246](assets/screen_shot_2018-03-23at090246.png)

* Im **Layout**-Modus können Sie auf **Komponenten hierher ziehen** tippen/klicken, um die gesamte Komponente auszuwählen. Dadurch wird die Symbolleiste für diesen Modus angezeigt.

   Die Symbolleiste bietet je nach Status der Layout-Komponente und der zugehörigen Komponenten unterschiedliche Optionen. Beispiel:

   * **Übergeordnetes Element**: Wählt die übergeordnete Komponente aus.

   ![](do-not-localize/screen_shot_2018-03-23at090823.png)

   * **Verborgene Komponenten einblenden**: Ermöglicht das Einblenden aller oder einzelner Komponenten. Die Zahl gibt an, wie viele verborgene Komponenten es jeweils gibt. Der Zähler zeigt an, wie viele Komponenten ausgeblendet sind.

   ![](do-not-localize/screen_shot_2018-03-23at091007.png)

   * **Breakpoint-Layout zurücksetzen**: Ermöglicht die Rückkehr zum Standard-Layout. Dies bedeutet, dass kein benutzerdefiniertes Layout vorgegeben wird.

   ![](do-not-localize/screen_shot_2018-03-23at091013.png)

   * **In neue Zeile verschieben**: Verschiebt die Komponente um eine Position nach oben, wenn der Leerraum dies erlaubt.

   ![screen_shot_2018-03-23at090829](assets/screen_shot_2018-03-23at090829.png)

   * **Komponente ausblenden**: Blendet die aktuelle Komponente aus.

   ![](do-not-localize/screen_shot_2018-03-23at090834.png)

   >[!NOTE]
   >
   >Im obigen Beispiel sind die Aktionen zum Verschieben und Ausblenden verfügbar, weil dieser Layout-Container in einem übergeordneten Layout-Container verschachtelt ist.

   * **Komponenten einblenden**
Wählen Sie die übergeordneten Komponenten aus, um die Aktionssymbolleiste mit der 
Option **Ausgeblendete Komponenten anzeigen** anzuzeigen. In diesem Beispiel gibt es zwei ausgeblendete Komponenten.
   ![screen_shot_2018-03-23at091200](assets/screen_shot_2018-03-23at091200.png)

   Bei Auswahl der Option **Ausgeblendete Komponenten anzeigen** werden die jeweils ausgeblendeten Komponenten in Blau an ihren ursprünglichen Positionen angezeigt.

   ![screen_shot_2018-03-23at091224](assets/screen_shot_2018-03-23at091224.png)

   Bei Auswahl der Option **Alle wiederherstellen** werden alle ausgeblendeten Komponenten eingeblendet.
