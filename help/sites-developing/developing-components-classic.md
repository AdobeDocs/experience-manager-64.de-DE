---
title: Entwickeln von AEM-Komponenten (klassische Benutzeroberfläche)
seo-title: Developing AEM Components (Classic UI)
description: Die klassische Benutzeroberfläche nutzt ExtJS, um Widgets zu erstellen, die das Erscheinungsbild der Komponenten angeben. HTL ist nicht die empfohlene Skriptsprache für AEM.
seo-description: The classic UI uses ExtJS to create widgets that provide the look-and-feel of the components. HTL is not the recommended scripting language for AEM.
uuid: ed53d7c6-5996-4892-81a4-4ac30df85f04
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: components
content-type: reference
discoiquuid: c68f724f-f9b3-4018-8d3a-1680c53d73f8
legacypath: /content/docs/en/aem/6-2/develop/components/components-classic
exl-id: 725e4f82-7019-4365-9c01-b5d95ea2a8fa
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '2391'
ht-degree: 72%

---

# Entwickeln von AEM-Komponenten (klassische Benutzeroberfläche){#developing-aem-components-classic-ui}

Die klassische Benutzeroberfläche nutzt ExtJS, um Widgets zu erstellen, die das Erscheinungsbild der Komponenten angeben. Aufgrund der Struktur dieses Widgets gibt es einige Unterschiede zwischen der Interaktion von Komponenten mit der klassischen Benutzeroberfläche und mit der [Touch-optimierten Benutzeroberfläche](/help/sites-developing/developing-components.md).

>[!NOTE]
>
>Viele Aspekte der Komponentenentwicklung sind sowohl für die klassische als auch für die Touch-optimierte Benutzeroberfläche gleich. **lesen [AEM Komponenten - Grundlagen](/help/sites-developing/components-basics.md) before** Verwenden Sie diese Seite, die sich mit den Besonderheiten der klassischen Benutzeroberfläche befasst.

>[!NOTE]
>
>Auch wenn die HTML Template Language (HTL) und JSP beide für die Entwicklung von Komponenten für die klassische Benutzeroberfläche verwendet werden können, ist auf dieser Seite nur die Entwicklung mit JSP abgebildet. Dies liegt einzig an der Historie der Verwendung von JSP für die klassische Benutzeroberfläche.
>
>HTL ist jetzt die empfohlene Skriptsprache für AEM. Siehe [HTL](https://helpx.adobe.com/de/experience-manager/htl/user-guide.html) und [Entwickeln AEM Komponenten](/help/sites-developing/developing-components.md) , um Methoden zu vergleichen.

## Struktur {#structure}

Die grundlegende Struktur einer Komponente wird auf der Seite behandelt [AEM Komponenten - Grundlagen](/help/sites-developing/components-basics.md#structure), das sowohl die Touch-optimierte als auch die klassische Benutzeroberfläche anwendet. Auch wenn Sie die Einstellungen für die Touch-optimierte Benutzeroberfläche in Ihrer neuen Komponente nicht verwenden müssen, ist es möglicherweise hilfreich, diese beim Vererben aus vorhandenen Komponenten zu beachten.

## JSP-Skripte {#jsp-scripts}

JSP-Skripte oder -Servlets können verwendet werden, um Komponenten zu rendern. Gemäß den Anforderungsverarbeitungsregeln von Sling lautet der Name für das Standardskript:

`<*componentname*>.jsp`

## global.jsp {#global-jsp}

Die JSP-Skriptdatei `global.jsp` wird verwendet, um allen JSP-Skriptdateien, die zum Rendern einer Komponente verwendet werden, schnellen Zugriff auf bestimmte Objekte (d. h. Zugriff auf Inhalte) bereitzustellen.

Daher muss `global.jsp` in jedem JSP-Skript enthalten sein, das Komponenten rendert, bei dem mindestens ein in `global.jsp` bereitgestelltes Objekt verwendet wird.

Der Speicherort der standardmäßigen `global.jsp` ist:

`/libs/foundation/global.jsp`

>[!NOTE]
>
>Der Pfad `/libs/wcm/global.jsp`, die von den Versionen CQ 5.3 und früher verwendet wurde, ist nun veraltet.

### Funktion von global.jsp, verwendeten APIs und Taglibs {#function-of-global-jsp-used-apis-and-taglibs}

Im Folgenden sind die wichtigsten Objekte aufgelistet, die die standardmäßige `global.jsp` bereitstellt:

Zusammenfassung:

* `<cq:defineObjects />`

   * `slingRequest` - Das umschlossene Anforderungsobjekt ( `SlingHttpServletRequest`).
   * `slingResponse` - Das umschlossene Antwortobjekt ( `SlingHttpServletResponse`).
   * `resource` - das Sling-Ressourcenobjekt ( `slingRequest.getResource();`).
   * `resourceResolver` - Das Sling Resource Resolver-Objekt ( `slingRequest.getResoucreResolver();`).
   * `currentNode` – der aufgelöste JCR-Knoten für die Anforderung.
   * `log` - Die Standardprotokollierung ().
   * `sling` - Der Sling-Skript-Helfer.
   * `properties` - Eigenschaften der adressierten Ressource ( `resource.adaptTo(ValueMap.class);`).
   * `pageProperties` – die Eigenschaften der Seite der betreffenden Ressource.
   * `pageManager` - Der Seitenmanager für den Zugriff auf AEM Inhaltsseiten ( `resourceResolver.adaptTo(PageManager.class);`).
   * `component` – das Komponentenobjekt der aktuellen AEM-Komponente.
   * `designer` - Das Designerobjekt zum Abrufen von Designinformationen ( `resourceResolver.adaptTo(Designer.class);`).
   * `currentDesign` – das Design der betreffenden Ressource.
   * `currentStyle` – der Stil der betreffenden Ressource.

### Zugreifen auf Inhalte {#accessing-content}

Es gibt drei Methoden für den Zugriff auf Inhalte in AEM WCM:

* Über das Eigenschaftenobjekt, das in `global.jsp`:

   Das properties -Objekt ist eine Instanz einer ValueMap (siehe [Sling-API](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/ValueMap.html)) und enthält alle Eigenschaften der aktuellen Ressource.

   Beispiel: `String pageTitle = properties.get("jcr:title", "no title");` wird im Rendering-Skript einer Seitenkomponente verwendet.

   Beispiel: `String paragraphTitle = properties.get("jcr:title", "no title");` wird im Rendering-Skript einer Standard-Absatzkomponente verwendet.

* Über die `currentPage` -Objekt eingeführt in `global.jsp`:

   Die `currentPage` -Objekt ist eine Instanz einer Seite (siehe [AEM API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/Page.mhtml)). Die Seitenklasse bietet verschiedene Methoden, um auf Inhalte zuzugreifen.

   Beispiel: `String pageTitle = currentPage.getTitle();`

* Via `currentNode` -Objekt eingeführt in `global.jsp`:

   Die `currentNode` -Objekt ist eine Instanz eines Knotens (siehe [JCR-API](https://jackrabbit.apache.org/api/2.16/org/apache/jackrabbit/standalone/cli/core/CurrentNode.html)). Auf die Eigenschaften eines Knotens kann über die `getProperty()` -Methode.

   Beispiel: `String pageTitle = currentNode.getProperty("jcr:title");`

## JSP-Tag-Bibliotheken {#jsp-tag-libraries}

Die Tag-Bibliotheken von CQ und Sling verleihen Ihnen Zugriff auf spezifische Funktionen für die Verwendung im JSP-Skript der Vorlagen und Komponenten.

Weitere Informationen finden Sie im Dokument . [Tag-Bibliotheken](/help/sites-developing/taglib.md).

## Verwendung clientseitiger HTML-Bibliotheken {#using-client-side-html-libraries}

Moderne Websites beruhen in hohem Maße auf der clientseitigen Verarbeitung durch einen komplexen JavaScript- und CSS-Code. Die Organisation und Optimierung der Bereitstellung dieses Codes kann äußerst kompliziert sein.

Um dieses Problem zu beheben, bietet AEM **Clientseitige Bibliotheksordner**, mit dem Sie Ihren clientseitigen Code im Repository speichern, in Kategorien organisieren und definieren können, wann und wie jede Codekategorie dem Client bereitgestellt werden soll. Das clientseitige Bibliotheksystem übernimmt dann das Herstellen der richtigen Links auf der endgültigen Webseite, um den korrekten Code zu laden.

Siehe Dokument . [Verwenden Client-seitiger HTML-Bibliotheken](/help/sites-developing/clientlibs.md) für weitere Informationen.

## Dialogfeld {#dialog}

Ihre Komponente benötigt ein Dialogfeld für Autoren, um Inhalte hinzuzufügen und zu konfigurieren.

Siehe [AEM Komponenten - Grundlagen](/help/sites-developing/components-basics.md#dialogs) für weitere Informationen.

## Konfigurieren des Bearbeitungsverhaltens {#configuring-the-edit-behavior}

Sie können das Bearbeitungsverhalten einer Komponente konfigurieren. Hierzu zählen Attribute, wie für die Komponente verfügbare Aktionen, Eigenschaften des Editors für die Bearbeitung im Kontext und die Listener, die im Zusammenhang mit den Ereignissen der Komponente stehen. Die Konfiguration ist für die Touch-optimierte und die klassische Benutzeroberfläche dieselbe, auch wenn bestimmte, spezifische Unterschiede bestehen.

Die [Bearbeitungsverhalten einer Komponente konfiguriert ist](/help/sites-developing/components-basics.md#edit-behavior) durch Hinzufügen eines `cq:editConfig` Knoten des Typs `cq:EditConfig` unterhalb des Komponentenknotens (vom Typ `cq:Component`) und durch Hinzufügen bestimmter Eigenschaften und untergeordneter Knoten.

## Verwenden und Erweitern von ExtJS-Widgets {#using-and-extending-extjs-widgets}

Weitere Details finden Sie unter [Verwenden und Erweitern von ExtJS-Widgets](/help/sites-developing/widgets.md).

## Verwenden von xtypes für ExtJS-Widgets {#using-xtypes-for-extjs-widgets}

Weitere Details finden Sie unter [Verwenden von xtypes](/help/sites-developing/xtypes.md).

## Entwickeln neuer Komponenten {#developing-new-components}

Dieser Abschnitt beschreibt, wie Sie Ihre eigenen Komponenten erstellen und diese dem Absatzsystem hinzufügen.

Eine schnelle Möglichkeit für den Einstieg ist das Kopieren einer vorhandenen Komponente und das anschließende Vornehmen der gewünschten Änderungen.

Ein Beispiel für die Entwicklung einer Komponente wird detailliert unter [Erweitern der Text- und Bildkomponente – ein Beispiel](#extending-the-text-and-image-component-an-example) beschrieben.

### Entwickeln einer neuen Komponente (vorhandene Komponente anpassen) {#develop-a-new-component-adapt-existing-component}

Um neue Komponenten für AEM basierend auf einer vorhandenen Komponente zu entwickeln, können Sie die Komponente kopieren, eine JavaScript-Datei für die neue Komponente erstellen und sie an einem Ort speichern, auf den AEM zugreifen kann (siehe auch [Anpassen von Komponenten und anderen Elementen](/help/sites-developing/dev-guidelines-bestpractices.md#customizing-components-and-other-elements)):

1. Verwenden Sie CRXDE Lite und erstellen Sie einen neuen Komponentenordner unter:

   / `apps/<myProject>/components/<myComponent>`

   Erstellen Sie die Knotenstruktur wie in den Bibliotheken neu und kopieren Sie dann die Definition einer vorhandenen Komponente, wie etwa die Textkomponente. Um beispielsweise die Textkomponente anzupassen, kopieren Sie diese

   * von `/libs/foundation/components/text`
   * in `/apps/myProject/components/text`

1. Ändern Sie die `jcr:title` , um den neuen Namen widerzuspiegeln.
1. Öffnen Sie den neuen Komponentenordner und nehmen Sie die erforderlichen Änderungen vor. Löschen Sie zudem alle irrelevanten Informationen im Ordner.

   Sie können Änderungen vornehmen, wie etwa:

   * Hinzufügen eines neuen Felds im Dialogfeld

      * `cq:dialog` - Dialogfeld für die Touch-optimierte Benutzeroberfläche
      * `dialog` – Dialogfeld für die klassische Benutzeroberfläche
   * ersetzt die `.jsp` Datei (nennen Sie sie nach Ihrer neuen Komponente)
   * oder vollständiges Überarbeiten der gesamten Komponente, falls gewünscht

   Wenn Sie beispielsweise eine Kopie der Standardtext-Komponente erstellen, können Sie dem Dialogfeld ein zusätzliches Feld hinzufügen und dann die `.jsp` , um die dort vorgenommenen Eingaben zu verarbeiten.

   >[!NOTE]
   >
   >Eine Komponente für:
   >
   >* Die Touch-optimierte Benutzeroberfläche verwendet [Granite](https://helpx.adobe.com/de/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/index.html)-Komponenten
   >* Die klassische Benutzeroberfläche verwendet [ExtJS-Widgets](https://helpx.adobe.com/de/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html)


   >[!NOTE]
   >
   >Ein Dialogfeld, das für die klassische Benutzeroberfläche definiert ist, funktioniert auf der Touch-optimierten Benutzeroberfläche.
   >
   >Ein Dialogfeld, das für die Touch-optimierte Benutzeroberfläche definiert ist, funktioniert auf der klassischen Benutzeroberfläche nicht.
   >
   >Abhängig von Ihrer Instanz und der Autorenumgebung können Sie beide Arten eines Dialogfelds für Ihre Komponente definieren.

1. Einer der folgenden Knoten muss vorhanden und ordnungsgemäß initialisiert sein, damit die neue Komponente angezeigt wird:

   * `cq:dialog` - Dialogfeld für die Touch-optimierte Benutzeroberfläche
   * `dialog` – Dialogfeld für die klassische Benutzeroberfläche
   * `cq:editConfig` – Verhalten von Komponenten in der Bearbeitungsumgebung (z. B Ziehen und Ablegen)
   * `design_dialog` - Dialogfeld für den Designmodus (nur klassische Benutzeroberfläche)

1. Aktivieren Sie die neue Komponente in Ihrem Absatzsystem anhand folgender Optionen:

   * Verwenden der CRXDE Lite zum Hinzufügen des Werts `<path-to-component>` (z. B. `/apps/geometrixx/components/myComponent`) zu den Eigenschaftskomponenten des Knotens `/etc/designs/geometrixx/jcr:content/contentpage/par`
   * Beachten der Anweisungen in [Hinzufügen neuer Komponenten zu Absatzsystemen](#adding-a-new-component-to-the-paragraph-system-design-mode)

1. Öffnen Sie in AEM WCM auf Ihrer Website eine Seite und fügen Sie einen neuen Absatz vom gerade erstellten Typ ein, um zu gewährleisten, dass die Komponente ordnungsgemäß funktioniert.

>[!NOTE]
>
>Um Zeitstatistiken für das Laden von Seiten anzuzeigen, können Sie Strg-Umschalt-U verwenden - mit `?debugClientLibs=true` in der URL festgelegt.

### Hinzufügen einer neuen Komponente zum Absatzsystem (Designmodus) {#adding-a-new-component-to-the-paragraph-system-design-mode}

Nach dem Entwickeln der Komponente fügen Sie sie dem Absatzsystem hinzu. Autoren können dadurch die Komponente auswählen und verwenden, wenn sie eine Seite bearbeiten.

1. Greifen Sie auf eine Seite in Ihrer Authoring-Umgebung zu, die beispielsweise das Absatzsystem verwendet `<contentPath>/Test.html`.
1. Wechseln Sie auf eine der folgenden Arten zum Designmodus:

   * adding `?wcmmode=design` zum Ende der URL und erneuter Zugriff, z. B.:

      `<contextPath>/ Test.html?wcmmode=design`

   * Klicken auf „Design“ im Sidekick

   Sie befinden sich jetzt im Designmodus und können das Absatzsystem bearbeiten.

1. Klicken Sie auf „Bearbeiten“.

   Eine Liste von Komponenten, die zum Absatzsystem gehören, wird angezeigt. Ihre neue Komponente ist jetzt auch aufgeführt.

   Die Komponenten können aktiviert (oder deaktiviert) werden, um zu bestimmen, welche dem Verfasser beim Bearbeiten einer Seite angeboten werden.

1. Aktivieren Sie Ihre Komponente, kehren Sie dann wieder in den normalen Bearbeitungsmodus zurück, um zu bestätigen, dass sie zur Nutzung verfügbar ist.

### Erweitern der Text- und der Bildkomponente – ein Beispiel {#extending-the-text-and-image-component-an-example}

Dieser Abschnitt bietet ein Beispiel dazu, wie die weithin verwendete, standardmäßige Text- und Bildkomponente um eine konfigurierbare Bildplatzierungsfunktion erweitert wird.

Die Erweiterung der Text- und Bildkomponente ermöglicht Editoren die Nutzung sämtlicher vorhandener Funktionen der Komponente sowie zusätzlich die Möglichkeit, die Platzierung des Bilds festzulegen:

* Auf der linken Seite des Texts (aktuelles Verhalten und der neue Standard)
* Sowie auf der rechten Seite

Nach der Erweiterung dieser Komponente können Sie die Bildplatzierung über das Dialogfeld der Komponente konfigurieren.

Die folgenden Techniken werden in dieser Übung erläutert:

* Kopieren des vorhandenen Komponentenknotens und Ändern seiner Metadaten
* Ändern des Dialogfelds der Komponente, einschließlich der Vererbung von Widgets aus den übergeordneten Dialogfeldern
* Ändern des Skripts der Komponente, um die neue Funktion zu implementieren

>[!NOTE]
>
>Dieses Beispiel ist auf die klassische Benutzeroberfläche ausgerichtet.

>[!NOTE]
>
>Dieses Beispiel beruht auf dem Geometrixx-Beispielinhalt, der nicht mehr im Lieferumfang von AEM enthalten ist und durch We.Retail ersetzt wird. Siehe Dokument . [We.Retail-Referenzimplementierung](/help/sites-developing/we-retail.md#we-retail-geometrixx) für Informationen zum Herunterladen und Installieren von Geometrixx.

#### Erweitern der vorhandenen textimage-Komponente {#extending-the-existing-textimage-component}

Um die neue Komponente zu erstellen, verwenden wir die standardmäßige textimage-Komponente als Grundlage und ändern sie. Wir speichern die neue Komponente in der Geometrixx-AEM WCM-Beispielanwendung.

1. Kopieren Sie die standardmäßige textimage-Komponente aus `/libs/foundation/components/textimage` in den Komponentenordner der Geometrixx, `/apps/geometrixx/components`, wobei textimage als Zielknotenname verwendet wird. (Kopieren Sie die Komponente, indem Sie zur Komponente navigieren, mit der rechten Maustaste klicken, „Kopieren“ auswählen und zum Zielverzeichnis navigieren.)

   ![chlimage_1-59](assets/chlimage_1-59.png)

1. Um dieses Beispiel einfach zu halten, navigieren Sie zu der Komponente, die Sie kopiert haben, und löschen alle Unterknoten des neuen textimage-Knotens mit Ausnahme der folgenden:

   * Dialogdefinition: `textimage/dialog`
   * Komponentenskript: `textimage/textimage.jsp`
   * Bearbeitungskonfigurationsknoten (erlaubt Drag &amp; Drop von Assets): `textimage/cq:editConfig`

   >[!NOTE]
   >
   >Die Dialogfelddefinition hängt von der Benutzeroberfläche ab:
   >
   >* Touch-optimierte Benutzeroberfläche: `textimage/cq:dialog`
   >* Klassische Benutzeroberfläche: `textimage/dialog`


1. Bearbeiten Sie die Komponentenmetadaten:

   * Komponentenname

      * Satz `jcr:description` nach `Text Image Component (Extended)`
      * Satz `jcr:title` nach `Text Image (Extended)`
   * Gruppe, in der die Komponente im Sidekick aufgelistet ist (unverändert lassen)

      * Urlaub `componentGroup` auf `General`
   * Übergeordnete Komponente für die neue Komponente (die standardmäßige textimage-Komponente)

      * Satz `sling:resourceSuperType` nach `foundation/components/textimage`

   Nach diesem Schritt sieht der Komponentenknoten wie folgt aus:

   ![chlimage_1-60](assets/chlimage_1-60.png)

1. Ändern Sie die `sling:resourceType` -Eigenschaft des Konfigurationsknotens &quot;edit&quot;des Bildes (Eigenschaft: `textimage/cq:editConfig/cq:dropTargets/image/parameters/sling:resourceType`) zu `geometrixx/components/textimage.`

   Auf diese Weise wird beim Ablegen eines Bilds in der Komponente auf der Seite die `sling:resourceType`-Eigenschaft der erweiterten textimage-Komponente auf `geometrixx/components/textimage.` festgelegt.

1. Ändern Sie das Dialogfeld „Komponente“, damit es die neue Option enthält. Die neue Komponente erbt die Teile des Dialogfelds, die dem Original entsprechen. Wir erweitern zusätzlich lediglich die Registerkarte **Erweitert** und fügen eine Dropdown-Liste **Bildposition** mit den Optionen **Links** und **Rechts** hinzu:

   * Lassen Sie die `textimage/dialog`Eigenschaften unverändert.

   Beachten Sie, dass `textimage/dialog/items` vier Unterknoten aufweist, tab1 bis tab4, die den vier Registerkarten des textimage-Dialogfelds entsprechen.

   * Für die ersten beiden Registerkarten (tab1 und tab2):

      * Ändern Sie xtype in cqinclude (um von der Standardkomponente zu erben).
      * Hinzufügen einer Pfadeigenschaft mit Werten `/libs/foundation/components/textimage/dialog/items/tab1.infinity.json`und `/libs/foundation/components/textimage/dialog/items/tab2.infinity.json`zurück.
      * Entfernen Sie alle anderen Eigenschaften oder Unterknoten.
   * Für tab3:

      * Lassen Sie die Funktionen und Unterknoten unverändert.
      * Hinzufügen einer neuen Felddefinition zu `tab3/items`, Knotenposition des Typs `cq:Widget`
      * Legen Sie die folgenden Eigenschaften (vom Typ &quot;String&quot;) für die neue `tab3/items/position`node:

         * `name`: `./imagePosition`
         * `xtype`: `selection`
         * `fieldLabel`: `Image Position`
         * `type`: `select`
      * Unterknoten hinzufügen `position/options` des Typs `cq:WidgetCollection` , um die beiden Optionen für die Bildplatzierung darzustellen, und erstellen Sie darunter zwei Knoten, o1 und o2 des Typs `nt:unstructured`.
      * Für Knoten `position/options/o1` Legen Sie die Eigenschaften fest: `text` nach `Left` und `value` nach `left.`
      * Für Knoten `position/options/o2` Legen Sie die Eigenschaften fest: `text` nach `Right` und `value` nach `right`.
   * Löschen Sie tab4.

   Die Bildposition wird im Inhalt als `imagePosition`-Eigenschaft des Knotens beibehalten, der für den Absatz `textimage` steht. Nach diesen Schritten sieht das Komponentendialogfeld folgendermaßen aus:

   ![chlimage_1-61](assets/chlimage_1-61.png)

1. Erweitern Sie das Komponentenskript `textimage.jsp` um eine zusätzliche Bearbeitungsmöglichkeit des neuen Parameters:

   ```xml
   Image image = new Image(resource, "image");
   
   if (image.hasContent() || WCMMode.fromRequest(request) == WCMMode.EDIT) {
        image.loadStyleData(currentStyle);
   ```

   Wir ersetzen das hervorgehobene Code-Fragment *%>&lt;div class=&quot;image&quot;>&lt;%* durch einen neuen Code, der einen benutzerdefinierten Stil für dieses Tag generiert.

   ```xml
   // todo: add new CSS class for the 'right image' instead of using 
   // the style attribute 
   String style="";
        if (properties.get("imagePosition", "left").equals("right")) { 
             style = "style=\"float:right\""; 
        } 
        %><div <%= style %> class="image"><%
   ```

1. Speichern Sie die Komponente im Repository. Die Komponente kann jetzt getestet werden.

#### Testen der neuen Komponente {#checking-the-new-component}

Nach der Entwicklung der Komponente können Sie sie dem Absatzsystem hinzufügen. Damit können Autoren die Komponente auswählen und verwenden, wenn sie eine Seite bearbeiten. Mit diesen Schritten können Sie die Komponente testen.

1. Öffnen Sie eine Seite in Geometrixx, wie etwa „Englisch/Unternehmen“.
1. Wechseln Sie in den Designmodus, indem Sie im Sidekick auf „Design“ klicken.
1. Bearbeiten Sie das Absatzsystemdesign, indem Sie in der Mitte der Seite im Absatzsystem auf die Schaltfläche „Bearbeiten“ klicken. Eine Liste der Komponenten, die im Absatzsystem platziert werden können, wird angezeigt und sollte Ihre neu entwickelte Komponente „Textbild (erweitert)“ enthalten. Aktivieren Sie diese für das Absatzsystem, indem Sie sie auswählen und auf „OK“ klicken.
1. Wechseln Sie zurück zum Bearbeitungsmodus.
1. Fügen Sie dem Absatzsystem den Absatz „Text-Bild (erweitert)“ hinzu und initialisieren Sie Text und Bild mit Beispielinhalten. Speichern Sie die Änderungen.
1. Öffnen Sie das Dialogfeld des Text- und Bildabsatzes, ändern Sie die Bildposition auf der Registerkarte „Erweitert“ in „Rechts“ und klicken Sie auf „OK“, um die Änderungen zu speichern.
1. Der Absatz wird mit dem Bild auf der rechten Seite wiedergegeben.
1. Die Komponente ist jetzt einsatzbereit.

Die Komponente speichert den Inhalt in einem Absatz auf der Unternehmensseite.

### Upload-Funktion der image-Komponente deaktivieren {#disable-upload-capability-of-the-image-component}

Um diese Funktion zu deaktivieren, verwenden wir die standardmäßige Bildkomponente als Grundlage und ändern sie. Wir speichern die neue Komponente in der Geometrixx-Beispielanwendung.

1. Kopieren Sie die standardmäßige Bildkomponente aus `/libs/foundation/components/image` in den Komponentenordner der Geometrixx, `/apps/geometrixx/components`, wobei image als Zielknotenname verwendet wird.

   ![chlimage_1-62](assets/chlimage_1-62.png)

1. Bearbeiten Sie die Komponentenmetadaten:

   * Satz **jcr:title** nach `Image (Extended)`

1. Navigieren Sie zu `/apps/geometrixx/components/image/dialog/items/image`.
1. Neue Eigenschaft hinzufügen:

   * **Name**: `allowUpload`
   * **Typ**: `String`
   * **Wert**: `false`

   ![chlimage_1-63](assets/chlimage_1-63.png)

1. Klicken Sie auf **Alle speichern**. Die Komponente kann jetzt getestet werden.
1. Öffnen Sie eine Seite in Geometrixx, wie etwa „Englisch/Unternehmen“.
1. Wechseln Sie in den Designmodus und aktivieren Sie „Bild (erweitert)“.
1. Wechseln Sie zurück zum Bearbeitungsmodus und fügen Sie diese Option dem Absatzsystem hinzu. Auf den nächsten Bildern sehen Sie die Unterschiede zwischen der ursprünglichen image-Komponente und der, die Sie soeben erstellt haben.

   Ursprüngliche image-Komponente:

   ![chlimage_1-64](assets/chlimage_1-64.png)

   Ihre neue image-Komponente:

   ![chlimage_1-65](assets/chlimage_1-65.png)

1. Die Komponente ist jetzt einsatzbereit.
