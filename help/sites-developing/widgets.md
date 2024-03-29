---
title: Verwenden und Erweitern von Widgets (klassische Benutzeroberfläche)
seo-title: Using and Extending Widgets (Classic UI)
description: AEM webbasierte Oberfläche verwendet AJAX und andere moderne Browsertechnologien, um die WYSIWYG-Bearbeitung und -Formatierung von Inhalten durch Autoren direkt auf der Webseite zu ermöglichen
seo-description: AEM's web-based interface uses AJAX and other modern browser technologies to enable WYSIWYG editing and formatting of content by authors right on the web page
uuid: e8dfa140-dab7-4e08-a790-d703adf86d6f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: components
content-type: reference
discoiquuid: 508f4fab-dd87-4306-83ae-12e544b8b723
exl-id: c747bfda-e82a-4b2d-a4af-5792bfe82576
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '5187'
ht-degree: 74%

---

# Verwenden und Erweitern von Widgets (klassische Benutzeroberfläche){#using-and-extending-widgets-classic-ui}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Die webbasierte Oberfläche von Adobe Experience Manager nutzt AJAX und andere moderne Browsertechnologien, um WYSIWYG-Bearbeitung und -Formatierung von Inhalten durch Autoren direkt auf der Webseite zu ermöglichen.

Adobe Experience Manager (AEM) verwendet die [ExtJS](https://www.sencha.com/) Widgets-Bibliothek, die die hochoptimierten Elemente der Benutzeroberfläche bereitstellt, die in allen wichtigen Browsern funktionieren und die Erstellung von Benutzeroberflächen-Erlebnissen auf Desktopebene ermöglichen.

Diese Widgets sind in AEM enthalten und können nicht nur von AEM selbst verwendet werden, sondern auch von jeder Website verwendet werden, die mit AEM erstellt wurde.

Eine vollständige Übersicht aller verfügbaren Widgets in AEM finden Sie in der [Widget-API-Dokumentation](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html) oder der [Liste der bestehenden X-Typen](/help/sites-developing/xtypes.md). Darüber hinaus zeigen zahlreiche Beispiele auf der Website von [Sencha](https://www.sencha.com/products/extjs/examples/), dem Eigentümer des Frameworks, wie das ExtJS-Framework zu verwenden ist.

Auf dieser Seite erhalten Sie einige Einblicke in die Verwendung und Erweiterung von Widgets. Zuerst wird beschrieben, wie [Client-seitiger Code in eine Seite eingefügt wird](#including-the-client-sided-code-in-a-page). Anschließend werden einige Beispielkomponenten beschrieben, die erstellt wurden, um einige grundlegende Verwendungen und Erweiterungen zu veranschaulichen. Diese Komponenten stehen als das Paket **Verwenden von ExtJS Widgets** auf **Package Share** zur Verfügung.

Das Paket enthält Beispiele für:

* [Grundlegende Dialogfelder](#basic-dialogs) mit vordefinierten Widgets erstellt.
* [Dynamische Dialogfelder](#dynamic-dialogs) wurde mit vordefinierten Widgets und benutzerdefinierter JavaScript-Logik erstellt.
* Dialogfelder basierend auf [benutzerdefinierte Widgets](#custom-widgets).
* A [Baumbereich](#tree-overview) Anzeigen einer JCR-Struktur unter einem bestimmten Pfad.
* A [Rasterbedienfeld](#grid-overview) Anzeige von Daten in Tabellenformat.

>[!NOTE]
>
>Die klassische Benutzeroberfläche von Adobe Experience Manager baut auf [ExtJS 3.4.0](https://extjs.cachefly.net/ext-3.4.0/docs/) auf.

>[!NOTE]
>
>Auf dieser Seite wird die Verwendung von Widgets in der klassischen Benutzeroberfläche beschrieben. Adobe empfiehlt, die moderne [Touch-optimierte Benutzeroberfläche](/help/sites-developing/touch-ui-concepts.md) zu verwenden, die auf [Coral-Benutzeroberfläche](/help/sites-developing/touch-ui-concepts.md#coral-ui) und [Granite-Benutzeroberfläche](/help/sites-developing/touch-ui-concepts.md#granite-ui-foundation-components) basiert.

## Einbauen von Client-seitigem Code in eine Seite {#including-the-client-sided-code-in-a-page}

Client-seitiger JavaScript- und Stylesheet-Code sollte in einer Client-Bibliothek platziert werden.

Erstellen Sie eine Client-Bibliothek wie folgt:

1. Erstellen Sie einen Knoten unterhalb von `/apps/<project>` mit den folgenden Eigenschaften:

   ```
       name="clientlib"
       jcr:mixinTypes="[mix:lockable]"
       jcr:primaryType="cq:ClientLibraryFolder" 
       sling:resourceType="widgets/clientlib" 
       categories="[<category-name>]" 
       dependencies="[cq.widgets]"
   ```

   >[!NOTE]
   >
   >Hinweis: `<category-name>` ist der Name der benutzerdefinierten Bibliothek (z. B. &quot;cq.extjstraining&quot;) und wird verwendet, um die Bibliothek auf der Seite einzuschließen.

1. Erstellen Sie unterhalb von `clientlib` die Ordner `css` und `js` (nt:folder).

1. Erstellen Sie unterhalb von `clientlib` die Dateien `css.txt` und `js.txt` (nt:files). Diese TXT-Dateien listen die Dateien auf, die in der Bibliothek enthalten sind.

1. Bearbeiten Sie die Datei `js.txt`: Sie muss mit „`#base=js`“ beginnen, worauf eine Liste der Dateien folgen soll, die vom CQ-Client-Bibliotheksdienst zusammengefasst werden sollen, z. B.:

   ```
   #base=js
    components.js
    exercises.js
    CustomWidget.js
    CustomBrowseField.js
    InsertTextPlugin.js
   ```

1. Bearbeiten Sie die Datei `css.txt`: Sie muss mit „`#base=css`“ beginnen, worauf eine Liste der Dateien folgen soll, die vom CQ-Client-Bibliotheksdienst zusammengefasst werden sollen, z. B.:

   ```
   #base=css
    components.css
   ```

1. Platzieren Sie die JavaScript-Dateien, die der Bibliothek angehören, unterhalb des Ordners `js`.

1. Platzieren Sie die Dateien `.css` und die von den css-Dateien verwendeten Ressourcen (z. B. `my_icon.png`) unter dem Ordner `css`.

>[!NOTE]
>
>Die oben beschriebene Verarbeitung von Stylesheets ist optional.

Fügen Sie die Client-Bibliothek wie folgt in die Seitenkomponenten-JSP ein:

* um sowohl JavaScript-Code als auch Stylesheets einzuschließen:

   `<ui:includeClientLib categories="<category-name1>, <category-name2>, ..."/>`

   where `<category-nameX>` ist der Name der clientseitigen Bibliothek.

* um nur JavaScript-Code einschließen:

   `<ui:includeClientLib js="<category-name>"/>`

Weitere Informationen finden Sie in der Beschreibung des [&lt;ui:includeclientlib>](/help/sites-developing/taglib.md#amp-lt-ui-includeclientlib) -Tag.

In einigen Fällen sollte eine Client-Bibliothek nur im Autorenmodus verfügbar sein und im Veröffentlichungsmodus ausgeschlossen werden. Dies lässt sich wie folgt erreichen:

```xml
    if (WCMMode.fromRequest(request) != WCMMode.DISABLED) {
        %><ui:includeClientLib categories="cq.collab.blog"/><%
    }
```

### Erste Schritte mit den Beispielen {#getting-started-with-the-samples}

Zum Durchführen der Übungen auf dieser Seite installieren Sie das Paket **Verwenden von ExtJS Widgets** auf einer lokalen AEM-Instanz und erstellen eine Beispielseite, auf der auch Komponenten eingefügt werden. Gehen Sie dazu wie folgt vor:

1. Laden Sie in Ihrer AEM-Instanz das Paket **Verwenden von ExtJS Widgets (v01)** von Package Share herunter und installieren Sie es. Dabei wird im Repository unter `extjstraining` das Projekt `/apps` erstellt.

1. Schließen Sie die Client-Bibliothek, die die Skripte (js) und das Stylesheet (css) enthält, im Head-Tag der Geometrixx-Seiten-JSP ein, da Sie die Beispielkomponenten auf einer neuen Seite des **Geometrixx** Verzweigung:

   in **CRXDE Lite** Datei öffnen `/apps/geometrixx/components/page/headlibs.jsp` und fügen Sie die `cq.extjstraining` der vorhandenen Kategorie `<ui:includeClientLib>` Tag wie folgt:

   `%><ui:includeClientLib categories="apps.geometrixx-main, cq.extjstraining"/><%`

1. Erstellen Sie eine neue Seite in der **Geometrixx**-Verzweigung unter `/content/geometrixx/en/products` und nennen Sie sie **Verwenden von ExtJS Widgets**.

1. Wechseln Sie in den Designmodus und fügen Sie alle Komponenten der Gruppe **Verwenden von ExtJS Widgets** dem Design von Geometrixx hinzu.
1. Wechseln Sie zurück in den Bearbeitungsmodus: Die Komponenten der Gruppe **Verwenden von ExtJS Widgets** stehen im Sidekick zur Verfügung.

>[!NOTE]
>
>Die Beispiele auf dieser Seite basieren auf dem Geometrixx-Beispielinhalt, der nicht mehr im Lieferumfang von AEM enthalten ist, da er durch We.Retail ersetzt wurde. Im Dokument [We.Retail-Referenzimplementierung](/help/sites-developing/we-retail.md#we-retail-geometrixx) finden Sie Informationen zum Herunterladen und Installieren von Geometrixx.

### Grundlegende Dialogfelder {#basic-dialogs}

Dialogfelder werden normalerweise zur Bearbeitung von Inhalten verwendet, können aber auch nur Informationen anzeigen. Eine einfache Möglichkeit, ein vollständiges Dialogfeld anzuzeigen, besteht darin, auf seine Darstellung im JSON-Format zuzugreifen. Verweisen Sie dazu Ihren Browser auf:

`http://localhost:4502/<path-to-dialog>.-1.json`

Die erste Komponente der Gruppe **Verwenden von ExtJS Widgets** im Sidekick wird mit **1. Dialog Allgemein** bezeichnet und umfasst vier grundlegende Dialogfelder, die mit standardmäßigen Widgets und ohne modifizierte JavaScript-Logik erstellt wurden. Die Dialogfelder werden unter `/apps/extjstraining/components/dialogbasics` gespeichert. Die grundlegenden Dialogfelder sind:

* das Dialogfeld „“ (Knoten `full`full): Es zeigt ein Fenster mit drei Registerkarten mit jeweils zwei Textfeldern an.

* das Dialogfeld „Single Panel“ (Knoten `singlepanel`): Es zeigt ein Fenster mit einer Registerkarte mit zwei Textfeldern an.
* das Dialogfeld „Multi Panel“ (Knoten `multipanel`): Es zeigt dasselbe an wie das Dialogfeld „Full“, ist aber anders aufgebaut.
* das Dialogfeld „“ (Knoten `design`design): Es zeigt ein Fenster mit zwei Registerkarten an. Die erste Registerkarte besitzt ein Textfeld, ein Dropdown-Menü und einen ausblendbaren Textbereich. Die zweite Registerkarte verfügt über einen Feldsatz mit vier Textfeldern und einen ausblendbaren Feldsatz mit zwei Textfeldern.

Fügen Sie die Komponente **1. Dialog Allgemein** der Beispielseite hinzu:

1. Fügen Sie die Komponente **1. Dialog Basics** zur Beispielseite aus der Registerkarte **Verwenden von ExtJS Widgets** im **Sidekick** hinzu.

1. Die Komponente zeigt einen Titel, einen Text und eine **EIGENSCHAFTEN** link: Klicken Sie auf den Link, um die Eigenschaften des im Repository gespeicherten Absatzes anzuzeigen. Klicken Sie erneut auf den Link, um die Eigenschaften auszublenden.

Die Komponente wird wie im Folgenden dargestellt:

![chlimage_1-135](assets/chlimage_1-135.png)

#### Beispiel 1: Vollständiger Dialog {#example-full-dialog}

Die **Voll** zeigt ein Fenster mit drei Registerkarten an, von denen jede Registerkarte zwei Textfelder enthält. Es ist das Standarddialogfeld der Komponente **Dialog Allgemein**. Die Eigenschaften sind:

* Wird von einem Knoten definiert: node type = `cq:Dialog`, xtype = [`dialog`](/help/sites-developing/xtypes.md#dialog).

* Zeigt drei Registerkarten (node type = `cq:Panel`).
* Jede Registerkarte weist zwei Textfelder auf (node type = `cq:Widget`, xtype = [`textfield`](/help/sites-developing/xtypes.md#textfield)).

* Wird durch den Knoten definiert:

   `/apps/extjstraining/components/dialogbasics/full`

* Wird im JSON-Format gerendert, indem Folgendes angefragt wird:

   `http://localhost:4502/apps/extjstraining/components/dialogbasics/full.-1.json`

Das Dialogfeld wird wie im Folgenden dargestellt:

![screen_shot_2012-01-31at45411pm](assets/screen_shot_2012-01-31at45411pm.png)

#### Beispiel 2: Dialogfeld &quot;Single Panel&quot; {#example-single-panel-dialog}

Die **Einzelnes Bedienfeld** zeigt ein Fenster mit einer Registerkarte mit zwei Textfeldern an. Die Eigenschaften sind:

* Zeigt eine Registerkarte (node type = `cq:Dialog`, xtype = [`panel`](/help/sites-developing/xtypes.md#panel))

* Die Registerkarte weist zwei Textfelder auf (node type = `cq:Widget`, xtype = [`textfield`](/help/sites-developing/xtypes.md#textfield))

* Wird durch den Knoten definiert:

   `/apps/extjstraining/components/dialogbasics/singlepanel`

* Wird im JSON-Format gerendert, indem Folgendes angefragt wird:

   `http://localhost:4502/apps/extjstraining/components/dialogbasics/singlepanel.-1.json`

* Ein Vorteil gegenüber dem **Vollständiger Dialog** ist, dass weniger Konfiguration erforderlich ist.
* Empfohlene Verwendung: für einfache Dialogfelder, die Informationen anzeigen oder nur wenige Felder haben.

So verwenden Sie das Dialogfeld &quot;Single Panel&quot;:

1. Ersetzen Sie das Dialogfeld der **Dialoggrundlagen** -Komponente mit **Einzelnes Bedienfeld** dialog:

   1. Löschen Sie in **CRXDE Lite** den Knoten: `/apps/extjstraining/components/dialogbasics/dialog`
   1. Klicken Sie auf **Alle speichern**, um die Änderungen zu speichern.
   1. Kopieren Sie den Knoten: `/apps/extjstraining/components/dialogbasics/singlepanel`
   1. Fügen Sie den kopierten Knoten ein unter: `/apps/extjstraining/components/dialogbasics`
   1. Wählen Sie den Knoten `/apps/extjstraining/components/dialogbasics/Copy of singlepanel` aus und benennen Sie ihn um zu `dialog`.

1. Bearbeiten Sie die Komponente: Das Dialogfeld wird wie im Folgenden dargestellt:

![screen_shot_2012-01-31at45952pm](assets/screen_shot_2012-01-31at45952pm.png)

#### Beispiel 3: Dialogfeld „Multi-Panel“ {#example-multi-panel-dialog}

Das Dialogfeld **Multi-Panel** zeigt dasselbe wie das Dialogfeld **Full**, ist aber anders aufgebaut. Die Eigenschaften sind:

* Wird von einem Knoten definiert (node type = `cq:Dialog`, xtype = [`tabpanel`](/help/sites-developing/xtypes.md#tabpanel)).

* Zeigt drei Registerkarten (node type = `cq:Panel`).
* Jede Registerkarte weist zwei Textfelder auf (node type = `cq:Widget`, xtype = [`textfield`](/help/sites-developing/xtypes.md#textfield)).

* Wird durch den Knoten definiert:

   `/apps/extjstraining/components/dialogbasics/multipanel`

* Wird im JSON-Format gerendert, indem Folgendes angefragt wird:

   `http://localhost:4502/apps/extjstraining/components/dialogbasics/multipanel.-1.json`

* Ein Vorteil gegenüber dem Dialogfeld **Full** besteht in der vereinfachten Struktur.

* Empfohlene Verwendung: für Dialogfelder mit mehreren Registerkarten.

Das Dialogfeld „Multi-Panel“ verwenden Sie wie folgt:

1. Ersetzen Sie das Dialogfeld der **Dialoggrundlagen** -Komponente mit **Multi-Panel** dialog:

   Führen Sie die Schritte aus, die für die [Beispiel 2: Dialogfeld &quot;Single Panel&quot;](#example-single-panel-dialog)

1. Bearbeiten Sie die Komponente: Das Dialogfeld wird wie im Folgenden dargestellt:

![screen_shot_2012-01-31at50119pm](assets/screen_shot_2012-01-31at50119pm.png)

#### Beispiel 4: Rich-Dialogfeld {#example-rich-dialog}

Die **Rich** zeigt ein Fenster mit zwei Registerkarten an. Die erste Registerkarte weist ein Textfeld auf, ein Dropdown-Menü und einen ausblendbaren Textbereich. Die zweite Registerkarte verfügt über einen Feldsatz mit vier Textfeldern und einen ausblendbaren Feldsatz mit zwei Textfeldern. Die Eigenschaften sind:

* Wird von einem Knoten definiert (node type = `cq:Dialog`, xtype = [`dialog`](/help/sites-developing/xtypes.md#dialog)).

* Zeigt zwei Registerkarten (node type = `cq:Panel`).
* Die erste Registerkarte verfügt über ein [`dialogfieldset`](/help/sites-developing/xtypes.md#dialogfieldset)-Widget mit einem [`textfield`](/help/sites-developing/xtypes.md#textfield)- und einem [`selection`](/help/sites-developing/xtypes.md#selection)-Widget mit drei Optionen sowie ein ausblendbares [`dialogfieldset`](/help/sites-developing/xtypes.md#dialogfieldset) mit einem [`textarea`](/help/sites-developing/xtypes.md#textarea)-Widget.

* Die zweite Registerkarte verfügt über ein [`dialogfieldset`](/help/sites-developing/xtypes.md#dialogfieldset)-Widget mit vier [`textfield`](/help/sites-developing/xtypes.md#textfield)-Widgets und ein ausblendbares `dialogfieldset` mit zwei [`textfield`](/help/sites-developing/xtypes.md#textfield)-Widgets.

* Wird durch den Knoten definiert:

   `/apps/extjstraining/components/dialogbasics/rich`

* Wird im JSON-Format gerendert, indem Folgendes angefragt wird:

   `http://localhost:4502/apps/extjstraining/components/dialogbasics/rich.-1.json`

So verwenden Sie das Dialogfeld **Rich**:

1. Ersetzen Sie das Dialogfeld der **Dialoggrundlagen** -Komponente mit **Rich** dialog:

   Führen Sie die Schritte aus, die für die [Beispiel 2: Dialogfeld &quot;Single Panel&quot;](#example-single-panel-dialog)

1. Bearbeiten Sie die Komponente: Das Dialogfeld wird wie im Folgenden dargestellt:

![screen_shot_2012-01-31at50429pm](assets/screen_shot_2012-01-31at50429pm.png) ![screen_shot_2012-01-31at50519pm](assets/screen_shot_2012-01-31at50519pm.png)

### Dynamische Dialogfelder {#dynamic-dialogs}

Die zweite Komponente der Gruppe **Verwenden von ExtJS Widgets** im Sidekick heißt **2. Dynamische Dialogfelder** und umfasst drei dynamische Dialogfelder, die mit standardmäßigen Widgets und **modifizierter JavaScript-Logik** erstellt wurden. Die Dialogfelder werden unter `/apps/extjstraining/components/dynamicdialogs` gespeichert. Die dynamischen Dialogfelder sind:

* das Dialogfeld „Registerkarten wechseln“ (Knoten `switchtabs`): Es zeigt ein Fenster mit zwei Registerkarten. Die erste Registerkarte verfügt über eine Optionsfeldauswahl mit drei Optionen: Wenn eine Option ausgewählt ist, wird eine Registerkarte angezeigt, die sich auf die Option bezieht. Die zweite Registerkarte enthält zwei Textfelder.
* das Dialogfeld „Beliebig“ (Knoten `arbitrary`): Es zeigt ein Fenster mit einer Registerkarte an. Die Registerkarte verfügt über ein Feld, in das Sie Assets ziehen oder hochladen können, und ein Feld, das Informationen über die Seite, die es umfasst, und das Asset (falls auf eines verwiesen wird) anzeigt.
* das Dialogfeld „Felder umschalten“ (Knoten `togglefield`): Es zeigt ein Fenster mit einer Registerkarte. Die Registerkarte verfügt über ein Kontrollkästchen: Ist es aktiviert, wird ein Feldsatz mit zwei Textfeldern angezeigt.

Fügen Sie die Komponente **2. Dynamische Dialogfelder** wie folgt der Beispielseite hinzu:

1. Fügen Sie die Komponente **2. Dynamische Dialogfelder** der Beispielseite aus der Registerkarte **Verwenden von ExtJS Widgets** im **Sidekick** hinzu.

1. Die Komponente zeigt einen Titel, etwas Text und einen Link **EIGENSCHAFTEN**: Klicken Sie, um die Eigenschaften des im Repository gespeicherten Absatzes anzuzeigen. Klicken Sie erneut, um die Eigenschaften zu verbergen.

Die Komponente wird wie im Folgenden dargestellt:

![chlimage_1-136](assets/chlimage_1-136.png)

#### Beispiel 1: Dialogfeld &quot;Switch Tabs&quot; {#example-switch-tabs-dialog}

Die **Switch Tabs** zeigt ein Fenster mit zwei Registerkarten an. Die erste Registerkarte verfügt über eine Optionsfeldauswahl mit drei Optionen: Wenn eine Option ausgewählt ist, wird eine Registerkarte angezeigt, die sich auf die Option bezieht. Die zweite Registerkarte enthält zwei Textfelder.

Die wichtigsten Merkmale sind:

* Wird von einem Knoten definiert (node type = `cq:Dialog`, xtype = [`dialog`](/help/sites-developing/xtypes.md#dialog)).

* Zeigt zwei Registerkarten (node type = `cq:Panel`): eine Auswahlregisterkarte und eine zweite Registerkarte, die von der Auswahl auf der ersten Registerkarte abhängt (drei Optionen).
* Weist drei optionale Registerkarten (node type = `cq:Panel`) mit jeweils zwei Textfeldern (node type = `cq:Widget`, xtype = [`textfield`](/help/sites-developing/xtypes.md#textfield)) auf. Es wird jeweils nur eine optionale Registerkarte angezeigt.

* Wird definiert durch den Knoten `switchtabs` unter:

   `/apps/extjstraining/components/dynamicdialogs/switchtabs`

* Wird im JSON-Format gerendert, indem Folgendes angefragt wird:

   `http://localhost:4502/apps/extjstraining/components/dynamicdialogs/switchtabs.-1.json`

Die Logik wird wie folgt durch Ereignis-Listener und JavaScript-Code implementiert:

* Der Dialogfeldknoten hat einen „`beforeshow`“-Listener, der alle optionalen Registerkarten ausblendet, bevor das Dialogfeld angezeigt wird:

   `beforeshow="function(dialog){Ejst.x2.manageTabs(dialog.items.get(0));}"`

   `dialog.items.get(0)` ruft die Registerkarte ab, die das Auswahlfeld und die 3 optionalen Bedienfelder enthält.

* Das Objekt `Ejst.x2` wird definiert in der Datei `exercises.js` unter:

   `/apps/extjstraining/clientlib/js/exercises.js`

* In der Methode `Ejst.x2.manageTabs()` werden alle optionalen Registerkarten ausgeblendet, weil der Wert von `index` „-1“ ist (i umfasst den Bereich von 1 bis 3).

* Die Auswahlregisterkarte weist zwei Listener auf: Einer zeigt die ausgewählte Registerkarte, wenn das ausgewählte Dialogfeld geladen wird (Ereignis „`loadcontent`“), und einer zeigt die ausgewählte Registerkarte, wenn die Auswahl geändert wird (Ereignis „`selectionchanged`“):

   `loadcontent="function(field,rec,path){Ejst.x2.showTab(field);}"`

   `selectionchanged="function(field,value){Ejst.x2.showTab(field);}"`

* In der Methode `Ejst.x2.showTab()`:

   ruft `field.findParentByType('tabpanel')` das Registerkartenbedienfeld ab, das alle Registerkarten enthält (`field` stellt das Auswahl-Widget dar).

   ruft `field.getValue()` den Wert der Auswahl ab, z. B. tab2.

   zeigt `Ejst.x2.manageTabs()` die ausgewählte Registerkarte an.

* Jede optionale Registerkarte verfügt über einen Listener, der die Registerkarte beim Ereignis „`render`“ ausblendet:

   `render="function(tab){Ejst.x2.hideTab(tab);}"`

* In der Methode `Ejst.x2.hideTab()`:

   ist `tabPanel` das Registerkartenbedienfeld, das alle Registerkarten enthält.

   ist `index` der Index der optionalen Registerkarte.

   blendet `tabPanel.hideTabStripItem(index)` die Registerkarte aus.

Dies wird wie folgt angezeigt:

![screen_shot_2012-02-01at114745am](assets/screen_shot_2012-02-01at114745am.png)

#### Beispiel 2: Dialogfeld „Arbitrary“ {#example-arbitrary-dialog}

Sehr oft zeigt ein Dialogfeld Inhalte aus der zugrunde liegenden Komponente an. Das hier beschriebene Dialogfeld **Arbitrary** zeigt Inhalte aus einer anderen Komponente an.

Die **Arbitrary** zeigt ein Fenster mit einer Registerkarte an. Die Registerkarte verfügt über zwei Felder: ein Asset zum Ablegen oder Hochladen und eines zum Anzeigen von Informationen über die übergeordnete Seite und über das Asset, wenn auf eines verwiesen wurde.

Die wichtigsten Merkmale sind:

* Wird von einem Knoten definiert (node type = `cq:Dialog`, xtype = [`dialog`](/help/sites-developing/xtypes.md#dialog)).

* Zeigt ein tabpanel-Widget (node type = `cq:Widget`, xtype = [`tabpanel`](/help/sites-developing/xtypes.md#tabpanel)) mit einem Bedienfeld (node type = `cq:Panel`)

* Das Bedienfeld verfügt über ein smartfile-Widget (Knotentyp = `cq:Widget`, xtype = [`smartfile`](/help/sites-developing/xtypes.md#smartfile)) und ein ownerdraw-Widget (Knotentyp = `cq:Widget`, xtype = [`ownerdraw`](/help/sites-developing/xtypes.md#ownerdraw))

* Wird definiert durch den Knoten `arbitrary` unter:

   `/apps/extjstraining/components/dynamicdialogs/arbitrary`

* Wird im JSON-Format gerendert, indem Folgendes angefragt wird:

   `http://localhost:4502/apps/extjstraining/components/dynamicdialogs/arbitrary.-1.json`

Die Logik wird wie folgt durch Ereignis-Listener und JavaScript-Code implementiert:

* Das ownerdraw-Widget verfügt über einen „`loadcontent`“-Listener, der Informationen über die Seite zeigt, die die Komponente und das Asset enthält, auf die vom smartfile-Widget verwiesen wird, wenn der Inhalt geladen wird:

   `loadcontent="function(field,rec,path){Ejst.x2.showInfo(field,rec,path);}"`

   `field` wird mit dem ownerdraw-Objekt festgelegt

   `path` wird mit dem Inhalts-Pfad der Komponente festgelegt (z. B.: /content/geometrixx/de/products/triangle/ui-tutorial/jcr:content/par/dynamicdialogs)

* Das Objekt `Ejst.x2` wird definiert in der Datei `exercises.js` unter:

   `/apps/extjstraining/clientlib/js/exercises.js`

* In der Methode `Ejst.x2.showInfo()`:

   ist `pagePath` der Pfad der Seite, die die Komponente enthält.

   stellt `pageInfo` die Seiteneigenschaften im JSON-Format dar.

   ist `reference` der Pfad des referenzierten Assets.

   stellt `metadata` die Metadaten des Assets im JSON-Format dar.

   zeigt `ownerdraw.getEl().update(html);` die erstellte HTML im Dialogfeld an.

So verwenden Sie das Dialogfeld **Arbitrary**:

1. Ersetzen Sie das Dialogfeld der **Dynamisches Dialogfeld** -Komponente mit **Arbitrary** dialog:

   Führen Sie die Schritte aus, die für die [Beispiel 2: Dialogfeld &quot;Single Panel&quot;](#example-single-panel-dialog)

1. Bearbeiten Sie die Komponente: Das Dialogfeld wird wie im Folgenden dargestellt:

![screen_shot_2012-02-01at115300am](assets/screen_shot_2012-02-01at115300am.png)

#### Beispiel 3: Dialogfeld &quot;Felder ein/aus&quot; {#example-toggle-fields-dialog}

Die **Umschalten zwischen Feldern** zeigt ein Fenster mit einer Registerkarte an. Die Registerkarte verfügt über ein Kontrollkästchen: Ist es aktiviert, wird ein Feldsatz mit zwei Textfeldern angezeigt.

Die wichtigsten Merkmale sind:

* Wird von einem Knoten definiert (node type = `cq:Dialog`, xtype = [`dialog`](/help/sites-developing/xtypes.md#dialog)).

* Zeigt ein tabpanel-Widget (node type = `cq:Widget`, xtype = [`tabpanel`](/help/sites-developing/xtypes.md#textpanel)) mit einem Bedienfeld (node type = `cq:Panel`).

* Das Bedienfeld weist ein -/checkbox-Widget (node type = `cq:Widget`, xtype = [`selection`](/help/sites-developing/xtypes.md#selection)selection, type = [`checkbox`](/help/sites-developing/xtypes.md#checkbox)) und ein ausblendbares (und standardmäßig ausgeblendetes) dialogfieldset-Widget (node type = `cq:Widget`, xtype = [`dialogfieldset`](/help/sites-developing/xtypes.md#dialogfieldset)) mit zwei textfield-Widgets (node type = `cq:Widget`, xtype = [`textfield`](/help/sites-developing/xtypes.md#textfield)) auf.

* Wird definiert durch den Knoten `togglefields` unter:

   `/apps/extjstraining/components/dynamicdialogs/togglefields`

* Wird im JSON-Format gerendert, indem Folgendes angefragt wird:

   `http://localhost:4502/apps/extjstraining/components/dynamicdialogs/togglefields.-1.json`

Die Logik wird wie folgt durch Ereignis-Listener und JavaScript-Code implementiert:

* Die Auswahlregisterkarte weist zwei Listener auf: Einer zeigt die Dialogfeldgruppe, wenn das ausgewählte Dialogfeld geladen wird (Ereignis „`loadcontent`“), und einer zeigt das die Dialogfeldgruppe, wenn die Auswahl geändert wird (Ereignis „`selectionchanged`“):

   `loadcontent="function(field,rec,path){Ejst.x2.toggleFieldSet(field);}"`

   `selectionchanged="function(field,value){Ejst.x2.toggleFieldSet(field);}"`

* Das Objekt `Ejst.x2` wird definiert in der Datei `exercises.js` unter:

   `/apps/extjstraining/clientlib/js/exercises.js`

* In der Methode `Ejst.x2.toggleFieldSet()`:

   * ist `box` das Auswahlobjekt.
   * ist `panel` das Bedienfeld, das das selection- und das dialogfieldset-Widget enthält.
   * ist `fieldSet` das dialogfieldset-Objekt.
   * `show` ist der Wert der Auswahl (true oder false)
   * basierend auf &quot; `show`&quot; das dialogfieldset angezeigt wird oder nicht

So verwenden Sie das Dialogfeld **Felder umschalten**:

1. Ersetzen Sie das Dialogfeld der **Dynamisches Dialogfeld** -Komponente mit **Umschalten zwischen Feldern** dialog:

   Führen Sie die Schritte aus, die für die [Beispiel 2: Dialogfeld &quot;Single Panel&quot;](#example-single-panel-dialog)

1. Bearbeiten Sie die Komponente: Das Dialogfeld wird wie im Folgenden dargestellt:

![screen_shot_2012-02-01at115518am](assets/screen_shot_2012-02-01at115518am.png)

### Benutzerdefinierte Widgets {#custom-widgets}

Die im Lieferumfang von AEM enthaltenen vordefinierten Widgets sollten die meisten Anwendungsfälle abdecken. Trotzdem kann es passieren, dass ein benutzerdefiniertes Widget erstellt werden muss, um eine projektspezifische Anforderung zu erfüllen. Benutzerdefinierte Widgets können durch Erweiterung vorhandener Widgets erstellt werden. Das Paket **Verwenden von ExtJS Widgets** enthält drei Dialogfelder, die drei verschiedene benutzerdefinierte Widgets verwenden, um die ersten Schritte mit der Anpassung zu vereinfachen:

* Das Dialogfeld „Multi Field“ (Knoten `multifield`) zeigt ein Fenster mit einer Registerkarte. Die Registerkarte verfügt über ein benutzerdefiniertes multifield-Widget mit zwei Feldern: Ein Dropdown-Menü mit zwei Optionen und ein Textfeld. Da es auf dem im Lieferumfang enthaltenen `multifield`-Widget (mit nur einem Textfeld) basiert, verfügt es über alle Funktionen des `multifield`-Widgets.

* Das Dialogfeld „Tree Browse“ (`treebrowse`-Knoten) zeigt ein Fenster mit einer Registerkarte, die ein Pfadbrowser-Widget enthält: Wenn Sie auf den Pfeil klicken, wird ein Fenster geöffnet, in dem Sie eine Hierarchie durchsuchen und ein Element auswählen können. Der Pfad des Elements wird dann dem Pfadfeld hinzugefügt und wird beibehalten, wenn das Dialogfeld geschlossen wird.
* Ein Dialogfeld, das auf dem Rich-Text-Editor-Plug-in basiert (Knoten `rteplugin`) und dem Rich-Text-Editor eine benutzerdefinierte Schaltfläche hinzufügt, mit der benutzerdefinierter Text in den Haupttext eingefügt werden kann. Es besteht aus einem `richtext`-Widget (RTE) und einer benutzerdefinierten Funktion, die durch den RTE-Plug-in-Mechanismus hinzugefügt wird.

Die benutzerdefinierten Widgets und das Plug-in sind in der Komponente **3. Benutzerdefinierte Widgets** des Pakets **Verwenden von ExtJS Widgets** enthalten. So fügen Sie diese Komponente zur Beispielseite hinzu:

1. Fügen Sie die Komponente **3. Benutzerdefinierte Widgets** zur Beispielseite aus der Registerkarte **Verwenden von ExtJS-Widgets** im **Sidekick** hinzu.

1. Die Komponente zeigt einen Titel, etwas Text und, wenn Sie auf den Link **EIGENSCHAFTEN** klicken, die Eigenschaften des im Repository gespeicherten Absatzes an. Durch erneutes Klicken werden die Eigenschaften verborgen.

   Die Komponente wird wie im Folgenden dargestellt:

![chlimage_1-137](assets/chlimage_1-137.png)

#### Beispiel 1: Benutzerdefiniertes Multifield-Widget {#example-custom-multifield-widget}

Die **Benutzerdefiniertes Multifield** Widget-basiertes Dialogfeld zeigt ein Fenster mit einer Registerkarte an. Die Registerkarte verfügt über ein benutzerdefiniertes multifield -Widget, das im Gegensatz zum Standard mit einem Feld zwei Felder aufweist: ein Dropdown-Menü mit zwei Optionen und einem Textfeld.

Das auf dem **Custom Multifield**-Widget basierende Dialogfeld:

* Wird von einem Knoten definiert (node type = `cq:Dialog`, xtype = [`dialog`](/help/sites-developing/xtypes.md#dialog)).

* Zeigt ein tabpanel-Widget (node type = `cq:Widget`, xtype = [`tabpanel`](/help/sites-developing/xtypes.md#tabpanel)) mit einem Bedienfeld (node type = `cq:Widget`, xtype = [`panel`](/help/sites-developing/xtypes.md#panel)).

* Das Bedienfeld weist ein `multifield`-Widget (node type = `cq:Widget`, xtype = [`multifield`](/help/sites-developing/xtypes.md#multifield)) auf.

* Das `multifield`-Widget verfügt über eine fieldconfig (Knotentyp = `nt:unstructured`, xtype = `ejstcustom`, optionsProvider = `Ejst.x3.provideOptions`), die auf dem benutzerdefinierten xtype „`ejstcustom`“ basiert:

   * „`fieldconfig`“ ist eine Konfigurationsoption des [`CQ.form.MultiField`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.MultiField)-Objekts.
   * „`optionsProvider`“ ist eine Konfiguration des `ejstcustom`-Widgets. Sie wird mit der `Ejst.x3.provideOptions`-Methode festgelegt, die definiert ist in `exercises.js` unter:

      `/apps/extjstraining/clientlib/js/exercises.js`

      und gibt 2 Optionen zurück.

* Wird definiert durch den Knoten `multifield` unter:

   `/apps/extjstraining/components/customwidgets/multifield`

* Wird im JSON-Format gerendert, indem Folgendes angefragt wird:

   `http://localhost:4502/apps/extjstraining/components/customwidgets/multifield.-1.json`

Das benutzerdefinierte Multifield-Widget (xtype = `ejstcustom`):

* Ist ein JavaScript-Objekt namens `Ejst.CustomWidget`.

* Wird definiert in der JavaScript-Datei `CustomWidget.js` unter:

   `/apps/extjstraining/clientlib/js/CustomWidget.js`

* Erweitert das Widget [`CQ.form.CompositeField`.](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.CompositeField)

* Weist drei Felder auf: `hiddenField` (Textfeld), `allowField` (Kombinationsfeld) und `otherField` (Textfeld)

* Überschreibt `CQ.Ext.Component#initComponent`, um die drei Felder hinzuzufügen:

   * `allowField` ist ein [CQ.form.Selection](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.Selection)-Objekt vom Typ „select“. „optionsProvider“ ist eine Konfiguration des Auswahl-Objekts, das mit der optionsProvider-Konfiguration des im Dialogfeld definierten CustomWidget instanziert wird.
   * `otherField` ist ein [CQ.Ext.form.TextField](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TextField)-Objekt.

* Überschreibt die Methoden `setValue`, `getValue` und `getRawValue` von [CQ.form.CompositeField](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.CompositeField), um den Wert von CustomWidget festzulegen und mit dem folgenden Format abzurufen:

   `<allowField value>/<otherField value>, e.g.: 'Bla1/hello'`.

* Registriert sich selbst als xtype „`ejstcustom`“:

   `CQ.Ext.reg('ejstcustom', Ejst.CustomWidget);`

Das auf dem **Custom Multifield**-Widget basierende Dialogfeld wird wie folgt angezeigt:

![screen_shot_2012-02-01at115840am](assets/screen_shot_2012-02-01at115840am.png)

#### Beispiel 2: Benutzerdefiniertes Treebrowse-Widget {#example-custom-treebrowse-widget}

Die benutzerdefinierte **Treebrowse** Widget-basiertes Dialogfeld zeigt ein Fenster mit einer Registerkarte, die ein benutzerdefiniertes Pfadbrowser-Widget enthält: Wenn Sie auf den Pfeil klicken, öffnet sich ein Fenster, in dem Sie eine Hierarchie durchsuchen und ein Element auswählen können. Der Pfad des Elements wird dann dem Pfadfeld hinzugefügt und wird beibehalten, wenn das Dialogfeld geschlossen wird.

Das benutzerdefinierte treebrowse-Dialogfeld:

* Wird von einem Knoten definiert (node type = `cq:Dialog`, xtype = [`dialog`](/help/sites-developing/xtypes.md#dialog)).

* Zeigt ein tabpanel-Widget (node type = `cq:Widget`, xtype = [`tabpanel`](/help/sites-developing/xtypes.md#tabpanel)) mit einem Bedienfeld (node type = `cq:Widget`, xtype = [`panel`](/help/sites-developing/xtypes.md#panel)).

* Das Bedienfeld weist ein benutzerdefiniertes Widget (node type = `cq:Widget`, xtype = `ejstbrowse`) auf.

* Wird definiert durch den Knoten `treebrowse` unter:

   `/apps/extjstraining/components/customwidgets/treebrowse`

* Wird im JSON-Format gerendert, indem Folgendes angefragt wird:

   `http://localhost:4502/apps/extjstraining/components/customwidgets/treebrowse.-1.json`

Das benutzerdefinierte treebrowse-Widgets (xtype = `ejstbrowse`):

* Ist ein JavaScript-Objekt namens `Ejst.CustomWidget`.
* Wird definiert in der JavaScript-Datei `CustomBrowseField.js` unter:

   `/apps/extjstraining/clientlib/js/CustomBrowseField.js`

* Erweitert [`CQ.Ext.form.TriggerField`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TriggerField).
* Definiert ein Fenster zum Durchsuchen namens `browseWindow`.

* Überschreibt [`CQ.Ext.form.TriggerField`, um das Fenster zum Durchsuchen anzuzeigen, wenn auf den Pfeil geklickt wird.](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TriggerField#onTriggerClick)
* Definiert ein [`CQ.Ext.tree.TreePanel`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.tree.TreePanel)-Objekt:

   * Es ruft Daten ab, indem es das Servlet aufruft, das unter `/bin/wcm/siteadmin/tree.json` registriert ist.
   * Sein Stamm ist „`apps/extjstraining`“.

* Definiert ein `window`-Objekt ([`CQ.Ext.Window`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Window)):

   * Basierend auf dem vordefinierten Bedienfeld.
   * Weist eine **OK**-Schaltfläche auf, die den Wert des ausgewählten Pfads festlegt und das Bedienfeld ausblendet.

* Das Fenster wird unterhalb des Feldes **Pfad** verankert.
* Der ausgewählte Pfad wird bei einem `show`-Ereignis vom Durchsuchfeld an das Fenster weitergegeben.

* Registriert sich selbst als xtype „`ejstbrowse`“:

   `CQ.Ext.reg('ejstbrowse', Ejst.CustomBrowseField);`

So verwenden Sie das auf dem Wideget **Benutzerdefiniertes Durchsuchen der Baumstruktur** basierende Dialogfeld:

1. Ersetzen Sie das Dialogfeld der **Benutzerdefinierte Widgets** -Komponente mit **Custom Treebrowse** dialog:

   Führen Sie die Schritte aus, die für die [Beispiel 2: Dialogfeld &quot;Single Panel&quot;](#example-single-panel-dialog)

1. Bearbeiten Sie die Komponente: Das Dialogfeld wird wie im Folgenden dargestellt:

![screen_shot_2012-02-01at120104pm](assets/screen_shot_2012-02-01at120104pm.png)

#### Beispiel 3: Rich-Text-Editor (RTE)-Plug-in {#example-rich-text-editor-rte-plug-in}

Die **Rich-Text-Editor (RTE)-Plug-in** basiertes Dialogfeld ist ein Dialogfeld, das auf dem Rich-Text-Editor basiert und über eine benutzerdefinierte Schaltfläche verfügt, um benutzerdefinierten Text in eckigen Klammern einzufügen. Der benutzerdefinierte Text kann auch anhand einer Server-seitigen Logik geparst werden (in diesem Beispiel nicht implementiert), um beispielsweise Text hinzuzufügen, der am jeweiligen Pfad definiert ist:

Das auf dem **RTE-Plug-in** basierende Dialogfeld:

* Wird definiert durch den Knoten „rteplugin“ unter:

   `/apps/extjstraining/components/customwidgets/rteplugin`

* Wird im JSON-Format gerendert, indem Folgendes angefragt wird:

   `http://localhost:4502/apps/extjstraining/components/customwidgets/rteplugin.-1.json`

* Der Knoten `rtePlugins` verfügt über einen untergeordneten Knoten `inserttext` (node type = `nt:unstructured`) der nach dem Plug-in benannt ist. Er weist eine Eigenschaft mit der Bezeichnung `features` auf, die definiert, welche der Plug-in-Funktionen für den RTE verfügbar sind.

Das RTE-Plug-in:

* Ist ein JavaScript-Objekt namens `Ejst.InsertTextPlugin`.

* Wird definiert in der JavaScript-Datei `InsertTextPlugin.js` unter:

   `/apps/extjstraining/clientlib/js/InsertTextPlugin.js`

* Erweitert das [`CQ.form.rte.plugins.Plugin`-Objekt.](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.Plugin)
* Die folgenden Methoden definieren das [`CQ.form.rte.plugins.Plugin`-Objekt und werden im implementierenden Plug-in überschrieben:](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.Plugin)

   * `getFeatures()` gibt ein Array aller Funktionen zurück, die vom Plug-in bereitgestellt werden.
   * `initializeUI()` fügt die neue Schaltfläche der RTE-Symbolleiste hinzu.
   * `notifyPluginConfig()` zeigt Titel und Text an, wenn auf die Schaltfläche gezeigt wird.
   * `execute()` wird aufgerufen, wenn auf die Schaltfläche geklickt wird, und führt die Plug-in-Aktion durch: Sie zeigt ein Fenster an, in dem Text definiert wird, der eingeschlossen werden soll.

* `insertText()` fügt einen Text anhand des entsprechenden Dialogfeldobjekts `Ejst.InsertTextPlugin.Dialog` ein (siehe unten).

* `executeInsertText()` wird von der Methode `apply()` des Dialogfelds aufgerufen, die ausgelöst wird, wenn auf die Schaltfläche **OK** geklickt wird.

* Registriert sich selbst als „`inserttext`“-Plug-in:

   `CQ.form.rte.plugins.PluginRegistry.register("inserttext", Ejst.InsertTextPlugin);`

* Das `Ejst.InsertTextPlugin.Dialog`-Objekt definiert das Dialogfeld, das geöffnet wird, wenn auf die Plug-in-Schaltfläche geklickt wird. Das Dialogfeld besteht aus einem Bedienfeld, einem Formular, einem Textfeld und zwei Schaltflächen (**OK** und **Abbrechen**).

So verwenden Sie das auf dem **Rich-Text-Editor (RTE)-Plug-in** basierende Dialogfeld:

1. Ersetzen Sie das Dialogfeld der **Benutzerdefinierte Widgets** -Komponente mit **Rich-Text-Editor (RTE)-Plug-in** basiertes Dialogfeld:

   Führen Sie die Schritte aus, die für die [Beispiel 2: Dialogfeld &quot;Single Panel&quot;](#example-single-panel-dialog)

1. Bearbeiten Sie die Komponente.
1. Klicken Sie auf das letzte Symbol auf der rechten Seite (das mit den vier Pfeilen). Geben Sie einen Pfad ein und klicken Sie auf **OK**:

   Der Pfad wird in eckigen Klammern (`[]`).

1. Klicken **OK** , um den Rich-Text-Editor zu schließen.

Die **Rich-Text-Editor (RTE)-Plug-in** Das basierte Dialogfeld wird wie folgt angezeigt:

![screen_shot_2012-02-01at120254pm](assets/screen_shot_2012-02-01at120254pm.png)

>[!NOTE]
>
>Dieses Beispiel zeigt nur die Implementierung des Client-seitigen Teils der Logik: Die Platzhalter (*[Text]*) müssen dann explizit Server-seitig geparst werden (z. B. in der Komponenten-JSP).

### Tree Overview {#tree-overview}

Das im Lieferumfang enthaltene [`CQ.Ext.tree.TreePanel`-Objekt bietet eine baumstrukturierte Benutzeroberflächendarstellung baumstrukturierter Daten. ](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.tree.TreePanel) Die im Paket **Verwenden von ExtJS Widgets** enthaltene Komponente „Übersicht über die Baumstruktur“ zeigt die Verwendung des Objekts `TreePanel` zur Anzeige einer JCR-Baumstruktur unterhalb eines gegebenen Pfads. Das Fenster selbst kann an- bzw. abgedockt werden. In diesem Beispiel wird die Fensterlogik in die Komponenten-JSP zwischen &lt;script>&lt;/script>-Tags eingebunden.

Fügen Sie die Komponente **Tree Overview** wie folgt der Beispielseite hinzu:

1. Fügen Sie die Komponente **4. Übersicht über die Baumstruktur** der Beispielseite aus der Registerkarte **Verwenden von ExtJS Widgets** im **Sidekick** hinzu.

1. Die Komponente zeigt:

   * einen Titel mit etwas Text
   * a **EIGENSCHAFTEN** link: Klicken Sie auf , um die Eigenschaften des im Repository gespeicherten Absatzes anzuzeigen. Klicken Sie erneut, um die Eigenschaften zu verbergen.
   * ein unverankertes Fenster mit einer Baumstruktur des Repositorys, das erweitert werden kann.

Die Komponente wird wie im Folgenden dargestellt:

![screen_shot_2012-02-01at120639pm](assets/screen_shot_2012-02-01at120639pm.png)

Die Komponente „Tree Overview“:

* Wird definiert unter:

   `/apps/extjstraining/components/treeoverview`

* Sein Dialogfeld ermöglicht es, die Größe des Fensters festzulegen und das Fenster anzudocken/zu lösen (siehe Details unten).

Die Komponenten-JSP:

* Ruft die Breite, Höhe und angedockten Eigenschaften aus dem Repository ab.
* Zeigt Text zum Datenformat der Baumübersicht an.
* Bettet die Fensterlogik zwischen JavaScript-Tags in die Komponenten-JSP ein.
* Wird definiert unter:

   `apps/extjstraining/components/treeoverview/content.jsp`

Der in die Komponenten-JSP eingebettete JavaScript-Code:

* Definiert ein `tree`-Objekt, indem versucht wird, ein Baumstrukturfenster von der Seite abzurufen.

* Wenn das Fenster, das die Baumstruktur anzeigt, nicht vorhanden ist, wird `treePanel` ([CQ.Ext.tree.TreePanel](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.tree.TreePanel)) erstellt:

   * `treePanel` enthält die Daten, anhand derer das Fenster erstellt wird.
   * Die Daten werden durch den Aufruf des Servlets abgerufen, das registriert ist unter:
      `/bin/wcm/siteadmin/tree.json`

* Der `beforeload`-Listener stellt sicher, dass der gewählte Knoten geladen wird.
* Das `root`-Objekt legt den Pfad `apps/extjstraining` als Stamm der Baumstruktur fest.
* `tree` ([`CQ.Ext.Window`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Window)) wird basierend auf der vordefinierten `treePanel`und wird angezeigt mit:

   `tree.show();`

* Wenn das Fenster bereits vorhanden ist, wird es anhand der aus dem Repository abgerufenen Breite, Höhe und angedockten Eigenschaften angezeigt.

Das Komponentendialogfeld:

* Zeigt eine Registerkarte mit zwei Feldern zum Festlegen der Größe (Breite und Höhe) des Fensters des Baumstrukturüberblicks und ein Feld zum An-/Abdocken des Fensters.
* Wird von einem Knoten definiert (node type = `cq:Dialog`, xtype = [`panel`](/help/sites-developing/xtypes.md#panel)).

* Das Bedienfeld weist ein sizefield-Widget (node type = `cq:Widget`, xtype = [`sizefield`](/help/sites-developing/xtypes.md#sizefield)) und ein selection-Widget (node type = `cq:Widget`, xtype = [`selection`](/help/sites-developing/xtypes.md#selection), type = `radio`) mit zwei Optionen (true/false) auf.

* Wird definiert durch den dialog-Knoten unter:

   `/apps/extjstraining/components/treeoverview/dialog`

* Wird im JSON-Format gerendert, indem Folgendes angefragt wird:

   `http://localhost:4502/apps/extjstraining/components/treeoverview/dialog.-1.json`

* Wird wie folgt angezeigt:

![screen_shot_2012-02-01at120745pm](assets/screen_shot_2012-02-01at120745pm.png)

### Rasterübersicht {#grid-overview}

Ein Rasterbedienfeld stellt Daten in tabellarischer Form von Zeilen und Spalten dar. Er umfasst Folgendes:

* Store: das Modell, das die Datendatensätze enthält (Zeilen)
* Spaltenmodell: das Spaltendesign
* Ansicht: fasst die Benutzeroberfläche zusammen
* Auswahlmodell: das Auswahlverhalten

Die im Paket **Verwenden von ExtJS Widgets** enthaltene Komponente „Raster-Übersicht“ zeigt, wie Daten in einem tabellarischen Format angezeigt werden:

* Das Beispiel 1 verwendet statische Daten.
* Das Beispiel 2 verwendet aus dem Repository abgerufene Daten.

Fügen Sie die Komponente „Raster-Übersicht“ wie folgt der Beispielseite hinzu:

1. Fügen Sie die Komponente **5. Raster-Übersicht** der Beispielseite aus der Registerkarte **Verwenden von ExtJS Widgets** im **Sidekick** hinzu.

1. Die Komponente zeigt:

   * einen Titel und etwas Text.
   * a **EIGENSCHAFTEN** link: Klicken Sie auf , um die Eigenschaften des im Repository gespeicherten Absatzes anzuzeigen. Klicken Sie erneut, um die Eigenschaften zu verbergen.
   * ein unverankertes Fenster mit Daten im Tabellenformat.

Die Komponente wird wie im Folgenden dargestellt:

![screen_shot_2012-02-01at121109pm](assets/screen_shot_2012-02-01at121109pm.png)

#### Beispiel 1: Standardraster {#example-default-grid}

In der vordefinierten Version **Rasterübersicht** -Komponente zeigt ein Fenster mit statischen Daten im Tabellenformat an. In diesem Beispiel wird die Logik auf zwei Arten in die Komponenten-JSP eingebettet:

* Die generische Logik wird definiert zwischen &lt;script>&lt;/script> tags
* Die spezifische Logik ist in einer separaten JS-Datei verfügbar und in der JSP mit verknüpft. Diese Einrichtung ermöglicht es, einfach zwischen den beiden Logiken (statisch/dynamisch) umzuschalten, indem die gewünschten &lt;script>-Tags kommentiert werden.

Die Komponente „Grid Overview“:

* Wird definiert unter:

   `/apps/extjstraining/components/gridoverview`

* Sein Dialogfeld ermöglicht es, die Größe des Fensters festzulegen und das Fenster anzudocken/zu lösen.

Die Komponenten-JSP:

* Ruft die Breite, Höhe und angedockten Eigenschaften aus dem Repository ab.
* Zeigt Text als Einführung zum Datenformat des Rasterüberblicks an.
* Verweist auf JavaScript-Code, der das GridPanel-Objekt definiert:

   `<script type="text/javascript" src="/apps/extjstraining/components/gridoverview/defaultgrid.js"></script>`

   `defaultgrid.js` definiert einige statische Daten als Grundlage für das GridPanel-Objekt.

* Bettet zwischen JavaScript-Tags JavaScript-Code ein, der das Window-Objekt definiert, das das GridPanel-Objekt verbraucht.
* Wird definiert unter:

   `apps/extjstraining/components/gridoverview/content.jsp`

Der in die Komponenten-JSP eingebettete JavaScript-Code:

* Definiert das `grid`-Objekt, indem versucht wird, die Fensterkomponente von folgender Seite abzurufen:

   `var grid = CQ.Ext.getCmp("<%= node.getName() %>-grid");`

* Wenn `grid` nicht vorhanden ist, wird ein [CQ.Ext.grid.GridPanel](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GridPanel)-Objekt (`gridPanel`) definiert, indem die Methode `getGridPanel()` aufgerufen wird (siehe unten). Diese Methode wird in `defaultgrid.js` definiert.

* `grid` ist ein [`CQ.Ext.Window`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Window)-Objekt, das auf dem vordefinierten GridPanel basiert, und wird angezeigt als: `grid.show();`

* Wenn `grid` bereits vorhanden ist, wird sie basierend auf den vom Repository abgerufenen Eigenschaften für Breite, Höhe und angedockte Elemente angezeigt.

Die JavaScript-Datei (`defaultgrid.js`), auf die in der Komponenten-JSP verwiesen wird, definiert die `getGridPanel()`-Methode, die von dem Skript aufgerufen wird, das in der JSP eingebettet ist, und gibt ein [`CQ.Ext.grid.GridPanel`-Objekt zurück, das auf statischen Daten basiert. ](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GridPanel) Die Logik lautet wie folgt:

* `myData` ist ein Array statischer Daten, formatiert als Tabelle mit fünf Spalten und vier Zeilen.
* `store` ist ein `CQ.Ext.data.Store`-Objekt, das `myData` verbraucht.

* `store` wird in den Speicher geladen:

   `store.load();`

* `gridPanel` ist ein [`CQ.Ext.grid.GridPanel`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GridPanel), das `store` verbraucht:

   * Die Spaltenbreiten werden ständig neu proportioniert:

      `forceFit: true`

   * Nur eine Zeile kann jeweils ausgewählt werden:

      `singleSelect:true`

#### Beispiel 2: Verweissuchraster {#example-reference-search-grid}

Bei der Installation des Pakets zeigt die Datei `content.jsp` der Komponente **Raster-Übersicht** ein Raster an, das auf statischen Daten basiert. Es ist möglich, die Komponente zu ändern, um ein Raster mit den folgenden Eigenschaften anzuzeigen:

* Hat drei Spalten.
* basiert auf Daten, die vom Repository durch Aufruf eines Servlets abgerufen werden.
* Die Zellen der letzten Spalte können bearbeitet werden. Der Wert wird in einer `test`-Eigenschaft unterhalb des Knotens gespeichert, der anhand des in der ersten Spalte angezeigten Pfades definiert wird.

Wie im vorherigen Abschnitt erläutert, erhält das Fensterobjekt seine [`CQ.Ext.grid.GridPanel`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GridPanel) -Objekt durch Aufruf der `getGridPanel()` -Methode, die in der `defaultgrid.js` Datei unter `/apps/extjstraining/components/gridoverview/defaultgrid.js`. Die **Rasterübersicht** -Komponente bietet eine andere Implementierung für die `getGridPanel()` -Methode, definiert in der `referencesearch.js` Datei unter `/apps/extjstraining/components/gridoverview/referencesearch.js`. Durch Wechseln der JS-Datei, auf die in der Komponenten-JSP verwiesen wird, basiert das Raster auf aus dem Repository abgerufenen Daten.

Wechseln Sie die JS-Datei, auf die in der Komponenten-JSP verwiesen wird:

1. Kommentieren Sie in **CRXDE Lite** in der Datei `content.jsp` der Komponente die Zeile, die die Datei `defaultgrid.js` enthält, sodass sie wie folgt aussieht:

   `<!-- script type="text/javascript" src="/apps/extjstraining/components/gridoverview/defaultgrid.js"></script-->`

1. Entfernen Sie den Kommentar aus der Zeile, die die Datei `referencesearch.js` enthält, sodass sie wie folgt aussieht:

   `<script type="text/javascript" src="/apps/extjstraining/components/gridoverview/referencesearch.js"></script>`

1. Speichern Sie die Änderungen.
1. Aktualisieren Sie die Beispielseite.

Die Komponente wird wie im Folgenden dargestellt:

![screen_shot_2012-02-01at121429pm](assets/screen_shot_2012-02-01at121429pm.png)

Der JavaScript-Code, auf den in der Komponenten-JSP (`referencesearch.js`) verwiesen wird, definiert die Methode `getGridPanel()`, die von der Komponenten-JSP aufgerufen werden, und gibt ein [`CQ.Ext.grid.GridPanel`-Objekt zurück, das auf Daten basiert, die dynamisch aus dem Repository abgerufen werden. ](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GridPanel) Die Logik in `referencesearch.js` definiert dynamische Daten als Basis für das GridPanel:

* `reader` ist ein [`CQ.Ext.data.JsonReader`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.JsonReader)-Objekt, das die Servlet-Antwort im JSON-Format für drei Spalten liest.

* `cm` ist ein [`CQ.Ext.grid.ColumnModel`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.ColumnModel)-Objekt für drei Spalten.

   Die „Test“-Spaltenzellen können bearbeitet werden, da sie mit einem Editor definiert werden:

   `editor: new `[`CQ.Ext.form.TextField`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TextField)`({})`

* die Spalten sind sortierbar:

   `cm.defaultSortable = true;`

* `store` ist [`CQ.Ext.data.GroupingStore`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.GroupingStore)-Objekt:

   * Es ruft seine Daten ab, indem es das unter „`/bin/querybuilder.json`“ registrierte Servlet mit einigen Parametern zum Filtern der Abfrage aufruft.
   * Es basiert auf dem vorher definierten `reader`.
   * Die Tabelle wird anhand der Spalte „**jcr:path**“ in aufsteigender Reihenfolge definiert.

* `gridPanel` ist ein [`CQ.Ext.grid.EditorGridPanel`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.EditorGridPanel)-Objekt, das bearbeitet werden kann:

   * Es basiert auf dem vordefinierten `store` und auf dem Spaltenmodell `cm`.
   * Nur eine Zeile kann jeweils ausgewählt werden:

      `sm: new `[`CQ.Ext.grid.RowSelectionModel`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.RowSelectionModel)`({singleSelect:true})`

   * Der `afteredit`-Listener stellt sicher, dass nach der Bearbeitung einer Zelle in der „**Test**“-Spalte Folgendes passiert:

      * Die Eigenschaft „`test`“ des Knotens an dem durch die Spalte „**jcr:path**“ definierten Pfad wird im Repository mit dem Wert der Zelle festgelegt.
      * Wenn der POST erfolgreich ist, wird der Wert dem `store`-Objekt hinzugefügt, andernfalls wird er abgelehnt.
