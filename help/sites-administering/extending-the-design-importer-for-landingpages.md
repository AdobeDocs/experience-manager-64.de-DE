---
title: Erweitern und Konfigurieren des Design-Import-Tools für Landing-Pages
seo-title: Extending and Configuring the Design Importer for Landing Pages
description: Erfahren Sie, wie Sie den Design Importer für Landingpages konfigurieren.
seo-description: Learn how to configure the Design Importer for landing pages.
uuid: b2bfe831-bfaf-43f3-babc-687bf229dd44
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: f8991416-995b-4160-a705-d131e78089ee
exl-id: 4b37c866-30c3-45ff-b7a3-013b69598668
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3526'
ht-degree: 58%

---

# Erweitern und Konfigurieren des Design-Import-Tools für Landing-Pages{#extending-and-configuring-the-design-importer-for-landing-pages}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

In diesem Abschnitt wird beschrieben, wie Sie den Design Importer für Einstiegsseiten konfigurieren und bei Bedarf erweitern. Die Arbeit mit Landingpages nach dem Import wird im Abschnitt [Landingpages.](/help/sites-classic-ui-authoring/classic-personalization-campaigns-landingpage.md)

**Extrahieren der benutzerdefinierten Komponente durch den Design Importer**

Im Folgenden finden Sie die logischen Schritte, damit der Design Importer Ihre benutzerdefinierte Komponente erkennt

1. Erstellen eines Taghandlers

   * Ein Taghandler ist ein POJO, das HTML-Tags eines bestimmten Typs handelt. Welche HTML-Tags Ihr Taghandler handeln kann, wird über die OSGi-Eigenschaft „tagpattern.name“ in der TagHandlerFactory definiert. Im Grunde handelt es sich bei der OSGi-Eigenschaft um einen RegEx, der dem Eingabe-HTML-Tag entsprechen sollte, das Sie handeln möchten. Alle verschachtelten Tags würden zum Handling an den Taghandler übergeben werden. Wenn Sie sich beispielsweise für ein div registrieren, das eine verschachtelte &lt;p> -Tag &lt;p> -Tag auch an Ihren TagHandler gesendet werden und es liegt an Ihnen, wie Sie sich darum kümmern möchten.
   * Die Oberfläche des Taghandlers ähnelt der Oberfläche eines SAX-Inhaltshandlers. Sie erhält für jedes HTML-Tag SAX-Ereignisse. Als Tag-Handler-Anbieter müssen Sie bestimmte Lebenszyklusmethoden implementieren, die automatisch vom Design Importer-Framework aufgerufen werden.

1. Erstellen Sie die entsprechende TagHandlerFactory.

   * Bei der TagHandlerFactory handelt es sich um eine OSGi-Komponente (Singleton), die dafür verantwortlich ist, Instanzen des Taghandlers zu erzeugen.
   * Ihre Tag-Handler-Factory muss eine OSGi-Eigenschaft namens &quot;tagpattern.name&quot;verfügbar machen, deren Wert mit dem Eingabe-HTML-Tag übereinstimmt.
   * Wenn mehrere Taghandler mit dem Eingabe-HTML-Tag übereinstimmen, wird jener mit dem höheren Rang gewählt. Der Rang selbst wird in der OSGi-Eigenschaft **service.ranking** angegeben.
   * Die TagHandlerFactory ist eine OSGi-Komponente. Alle Verweise, die Sie für Ihren TagHandler bereitstellen möchten, müssen über diese Factory erfolgen.

1. Stellen Sie sicher, dass Ihre TagHandlerFactory einen höheren Rang hat, wenn Sie den Standard überschreiben möchten.

## Vorbereiten der HTML für den Import {#preparing-the-html-for-import}

Nachdem Sie eine Importtool-Seite erstellt haben, können Sie Ihre vollständige HTML-Landingpage importieren. Um Ihre HTML-Einstiegsseite zu importieren, müssen Sie den Inhalt zunächst zu einem Designpaket packen. Das Designpaket enthält Ihre HTML-Landingpage zusammen mit den referenzierten Assets (Bilder, CSS, Symbole, Skripte usw.).

Das folgende Spickzettel enthält ein Beispiel für die Vorbereitung Ihrer HTML für den Import:

Landingpage-Spickzettel

[Datei laden](assets/cheatsheet.zip)

### Zip-Datei-Layout und -Anforderungen {#zip-file-layout-and-requirements}

>[!NOTE]
>
>An dieser Stelle dürfen ZIP-Dateien nur eine HTML-Seite oder einen Seitenbereich enthalten.

Ein Beispiel für ein Zip-Layout:

* /index.html -> Landingpage-HTML-Datei
* /css -> zum Hinzufügen zur CSS-clientlib
* /img -> alle Bilder und Assets
* /js -> zum Hinzufügen zur JS-clientlib

Das Layout basiert auf dem Boilerplate-Layout für HTML5. Lesen Sie mehr unter [https://html5boilerplate.com/](https://html5boilerplate.com/).

>[!NOTE]
>
>Mindestens das Designpaket **must** enthält **index.html** -Datei auf der Stammebene. Wenn die zu importierende Landingpage auch eine mobile Version aufweist, muss die ZIP-Datei eine **mobile.index.html** zusammen mit **index.html** auf der Stammebene.

### Vorbereiten der HTML-Landingpage {#preparing-the-landing-page-html}

Um die HTML importieren zu können, müssen Sie der Landingpage-HTML ein Leinwand-div hinzufügen.

Das Arbeitsflächen-div ist ein HTML-**div** mit `id="cqcanvas"`, das in das HTML-`<body>`-Tag eingefügt werden muss und das den Inhalt für die Konvertierung umgeben muss.

Ein Beispielausschnitt der Landingpage-HTML nach dem Hinzufügen des Leinwand-div ist wie folgt:

```xml
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title></title>
  <meta name="description" content="">
</head>
<body>
 <div id="cqcanvas">
  <!-- HTML content intended for conversion -->
 </div>
</body>
</html>
```

### Vorbereiten des HTML auf das Einschließen bearbeitbarer AEM {#preparing-the-html-to-include-editable-aem-components}

Beim Import einer Landingpage haben Sie die Möglichkeit, die Seite unverändert zu importieren. Das bedeutet, dass Sie nach dem Import der Landingpage keines der importierten Elemente in AEM bearbeiten können (Sie können auf der Seite noch weitere AEM hinzufügen).

Bevor Sie die Einstiegsseite importieren, empfiehlt es sich, einige Teile der Einstiegsseite in bearbeitbare AEM-Komponenten zu konvertieren. Dadurch können Sie auch nach dem Import des Einstiegsseitendesigns Teile der Einstiegsseite schnell bearbeiten.

Sie tun dies, indem Sie in der zu importierenden HTML-Datei der entsprechenden Komponente die `data-cq-component` hinzufügen.

Im folgenden Abschnitt wird beschrieben, wie Sie Ihre HTML-Datei so bearbeiten, dass bestimmte Teile der Einstiegsseiten in andere bearbeitbare AEM-Komponenten konvertiert werden. Die Komponenten werden detailliert beschrieben unter [Einstiegsseiten-Komponenten](/help/sites-classic-ui-authoring/classic-personalization-campaigns-landingpage.md).

>[!NOTE]
>
>HTML-Markup zum Konvertieren von Teilen der Einstiegsseiten in AEM-Komponenten verfügt sowohl über eine lange als auch über eine kurze Tag-Deklarierung. Beide werden für jede Komponente beschrieben.

### Beschränkungen {#limitations}

Beachten Sie vor dem Import die folgenden Einschränkungen:

### Sämtliche Attribute wie „class“ oder „id“, die auf das     &amp;lt;body>-Tag angewendet werden, werden nicht beibehalten. {#any-attribute-like-class-or-id-applied-on-the-amp-lt-body-tag-is-not-preserved}

Wenn ein beliebiges Attribut wie „id“ oder „class“ auf das body-Tag angewendet wird, z. B. `<body id="container">`, bleibt dieses Attribut nach dem Import nicht erhalten. Das importierte Design darf also über keine Abhängigkeiten bei den Attributen verfügen, die auf das `<body>`-Tag angewendet werden.

### Verschieben einer Zip-Datei per Drag-and-Drop {#drag-and-drop-zip}

Ein Upload durch Verschieben einer Zip-Datei per Drag-and-Drop wird für Internet Explorer und Firefox-Versionen vor 3.6 nicht unterstützt. Um bei Verwendung dieser Browser ein Design hochzuladen, klicken Sie auf den Bereich der Dropdatei, um ein Dialogfeld zum Hochladen von Dateien zu öffnen und Ihr Design mithilfe dieses Dialogfelds hochzuladen.

Die Browser, die &quot;Drag &amp; Drop&quot;der Design-ZIP unterstützen, sind Chrome, Safari5.x, Firefox 4 und höher.

### Modernizr wird nicht unterstützt {#modernizr-is-not-supported}

`Modernizr.js` ist ein Javascript-basiertes Hilfsmittel, das native Browserfunktionen erkennt und ermittelt, ob sie für HTML5-Elemente geeignet sind. Bei Designs, die Modernizr für die verbesserte Unterstützung älterer Browserversionen verwenden, können Fehler in der Einstiegsseitenlösung auftreten. `Modernizr.js`-Skripts werden vom Design-Importer nicht unterstützt.

### Seiteneigenschaften werden beim Import des Designpakets nicht beibehalten {#page-properties-are-not-preserved-at-the-time-of-importing-design-package}

Jede Seiteneigenschaft (z. B. „Benutzerdefinierte Domain“, „HTTPS erzwingen“ usw.), die für eine (mit der Vorlage „Leere Startseite“ erstellte) Seite vor dem Import des Designpakets festgelegt wurde, geht verloren, nachdem das Design importiert wurde. Daher wird empfohlen, die Seiteneigenschaften nach dem Import des Designpakets festzulegen.

### Nur Markup für HTML angenommen {#html-only-markup-assumed}

Nach dem Importieren wird das Markup aus Sicherheitsgründen bereinigt, um den Import und die Veröffentlichung von ungültigem Markup zu verhindern. Dabei wird davon ausgegangen, dass das reine HTML-Markup und alle anderen Elementformen wie Inline-SVG oder Webkomponenten herausgefiltert werden.

### Text {#text}

HTML-Markup zum Einfügen einer text-Komponente (`foundation/components/text`) in das HTML im Designpaket:

```xml
<div data-cq-component="text"> <p>This is some editable text</p> </div>
```

Durch die Integration des oben genannten Markups in das HTML passiert Folgendes:

* Eine bearbeitbare AEM-text-Komponente (`sling:resourceType=foundation/components/text`) wird in der Landingpage erstellt, die nach dem Import des Designpakets erstellt wurde.
* Die Eigenschaft `text` der erstellten Komponente „text“ wird auf das im `div` eingeschlossene HTML gesetzt.

**Kurze Komponenten-Tag-Deklaration**:

```xml
<p data-cq-component="text">Text component shorthand</p>
```

**Text mit Liste**

So fügen Sie einen Text mit einer Liste hinzu:

* 1st
* 2nd

die im RTE-Editor bearbeitet werden können:

```xml
<div data-cq-component="text"><p>This is text with a list:</p><ul><li>1st</li><li>2nd</li></ul><p>It can be edited with the RTE editor</p></div>
```

**Text mit Farbe**

So fügen Sie einen Text mit Farbe (rosa) hinzu, der im RTE-Editor bearbeitet werden kann:

```xml
<div class="pink" data-cq-component="text"><p>This is pink text.</p><p>It can be edited with the RTE editor</p></div>
```

### Titel {#title}

HTML-Markup, um eine title-Komponente (`wcm/landingpage/components/title`) in das HTML im Designpaket einzufügen:

```xml
<div data-cq-component="title"> <h1>This is some editable title text</h1> </div>
```

Durch die Integration des oben genannten Markups in das HTML passiert Folgendes:

* Eine bearbeitbare AEM-title-Komponente (`sling:resourceType=wcm/landingpage/components/title`) wird in der Landingpage erstellt, die nach dem Import des Designpakets erstellt wurde.
* Stellt die Eigenschaft `jcr:title` der erstellten title-Komponente auf den Text ein, der im div in das Überschriften-Tag eingeschlossen ist.
* Stellt die Eigenschaft `type` des Überschriften-Tags ein, in diesem Fall `h1`.

Die title-Komponente unterstützt 7 Typen: `h1, h2, h3, h4, h5, h6` und `default`.

**Kurze Komponenten-Tag-Deklaration**:

```xml
<h1 data-cq-component="title">Title component shorthand</h1>
```

### Bild {#image}

HTML Markup zum Einfügen einer Bildkomponente (foundation/components/image) in die HTML innerhalb des Designpakets:

```xml
<div data-cq-component="image">
<img src="img/video1.png" alt="Video about Polar Brake Goggles in action" title="Polar Brake Goggles" width="300" height="200" />
</div>
```

Durch die Integration des oben genannten Markups in das HTML passiert Folgendes:

* Eine bearbeitbare AEM-image-Komponente (`sling:resourceType=foundation/components/image`) wird in der Landingpage erstellt, die nach dem Import des Designpakets erstellt wurde.
* Stellt die Eigenschaft `fileReference` der erstellten image-Komponente auf den Pfad ein, in den das im src-Attribut angegebene Bild importiert wird.
* Setzt die Eigenschaft `alt` auf den Wert des alt-Attributs im img-Tag.
* Setzt die Eigenschaft `title` auf den Wert des title-Attributs im img-Tag.
* Setzt die Eigenschaft `width` auf den Wert des width-Attributs im img-Tag.
* Setzt die Eigenschaft `height` auf den Wert des height-Attributs im img-Tag.

**Kurze Komponenten-Tag-Deklaration:**

```xml
<img data-cq-component="image" src="test.png" alt="Image component shorthand"/>
```

#### Absolute URL img src wird in der Bildkomponente &quot;Div&quot;nicht unterstützt {#absolute-url-img-src-not-supported-within-image-component-div}

Wenn ein `<img>`-Tag mit einer absoluten URL-src für die Komponenten-Konverstierung ausgewählt wird, wird ein entsprechender Ausnahmefehler **UnsupportedTagContentException** ausgegeben. So wird das folgende Beispiel nicht unterstützt:

`<div data-cq-component="image">`

`<img src="https://cdn.printfriendly.com/pf-button.gif" alt="Print Friendly and PDF"/>`

`</div>`

Andernfalls werden jedoch absolute URL-Bilder für img-Tags unterstützt, die nicht Teil des Bildkomponente-div sind.

### Aktionsaufruf-Komponenten {#call-to-action-components}

Sie können einen Teil der zu importierenden Landingpage als &quot;bearbeitbare Aktionsaufruf-Komponente&quot;markieren. Solche importierten Aktionsaufruf-Komponenten können nach dem Import der Landingpage bearbeitet werden. AEM enthält die folgenden CTA-Komponenten:

* Clickthrough-Link - Ermöglicht den Zusatz eines Textlinks, der den Besucher bei Klick zu einer Ziel-URL führt.
* Grafischer Link - Ermöglicht das Hinzufügen eines Bildes, das den Besucher durch Klicken auf eine Ziel-URL weiterleitet.

#### Click Through-Link {#click-through-link}

Diese CTA-Komponente kann dazu verwendet werden, der Landingpage einen Text-Link hinzuzufügen.

Unterstützte Eigenschaften

* Beschriftung mit fett-, kursiv- und unterstrichenen Optionen
* Target-URL, unterstützt Drittanbieter- und AEM-URL
* Seitenrendering-Optionen (gleiches Fenster, neues Fenster usw.)

HTML-Tag mit in der importierten Zip enthaltener Click Through-Komponente: Hier ordnet href der Ziel-URL zu, &quot;Produktdetails anzeigen&quot;wird der Beschriftung zugeordnet usw.

```xml
<div id="cqcanvas">
.
.
                <div data-cq-component="clickThroughLink">
        <a href="/content/we-retail/us/en/products/equipment/snow-sports/flying-snowboard.html">View Product Details  ></a>
  </div>
.
.
</div>
```

Diese Komponente kann in jeder eigenständigen Anwendung verwendet oder aus der ZIP-Datei importiert werden.

**Kurze Komponenten-Tag-Deklaration**:

```xml
<a href="/somelink.html" data-cq-component="clickThroughLink">Click Through Link shorthand</a>
```

#### Grafischer Link {#graphical-link}

Diese CTA-Komponente kann dazu verwendet werden, ein beliebiges grafisches Bild mit Link auf der Einstiegsseite hinzuzufügen. Beim Bild kann es sich um eine einfache Schaltfläche oder um ein grafisches Bild als Hintergrund handeln. Wenn der Benutzer auf das Bild klickt, wird er zur in den Komponenteneigenschaften angegebenen Ziel-URL weitergeleitet. Sie ist Teil der Gruppe &quot;Aktionsaufruf&quot;.

Unterstützte Eigenschaften

* Bild beschneiden, drehen
* Hover-Text, Beschreibung, Größe in px
* Target-URL, unterstützt Drittanbieter- und AEM-URL
* Seitenrendering-Optionen (gleiches Fenster, neues Fenster usw.)

HTML-Tag mit in der importierten Zip enthaltenem grafischen Link: Hier wird href der Ziel-URL zugeordnet, img src das Rendering-Bild, &quot;title&quot;wird als Hover-Text verwendet und so weiter.

```xml
<div id="cqcanvas">
  <div data-cq-component="clickThroughGraphicalLink"><a href="https://www.adobe.com/go/wem"><img src="img/call-to-action-button.png" title="Click Here to Learn More" /></a></div>
</div>
```

**Kurze Komponenten-Tag-Deklaration**:

```xml
<a href="/somelink.html" data-cq-component="clickThroughGraphicalLink"><img src="linkimage.png" alt="Click Through Graphical Link shorthand"/></a>
```

>[!NOTE]
>
>Um einen Link „clickthroughgraphical“ zu erstellen, müssen Sie ein Anchortag und das Bild-Tg in einem div mit dem Attribut `data-cq-component="clickthroughgraphicallink"` einschließen.
>
>Beispiel: `<div data-cq-component="clickthroughlink"> <a href="https://myURLhere/"><img src="image source here"></a> </div>`
>
>Andere Möglichkeiten, mit CSS ein Bild mit einem Anchortag zu verknüpfen werden nicht unterstützt. So funktioniert z. B. das folgende Markup nicht:
>
>`<div data-cq-component="clickthroughgraphicallink">`
>
>`<a class="hasBackground" href="https://myURLhere/"></a>`
>
>`</div>`
>
>mit einem verknüpften `css .hasbackground { background-image: pathtoimage }`

### Lead-Formular {#lead-form}

Ein Lead-Formular ist ein Formular, das dazu verwendet wird, die Informationen eines Besuchers/Leads zu sammeln. Diese Informationen können gespeichert und später dazu verwendet werden, anhand dieser Informationen effizientes Marketing durchzuführen. Die Informationen enthalten im Allgemeinen Titel, Namen, E-Mail, Geburtsdatum, Adresse, Interessen usw. Sie sind Teil der Gruppe „CTA-Lead-Formular“.

**Unterstützte Funktionen**

* Vordefinierte Lead-Felder (Vorname, Nachname, Adresse, Geburtsdatum, Geschlecht, Info, Benutzer-ID, E-Mail-ID, Sende-Schaltfläche) sind im Sidekick verfügbar. Platzieren Sie die erforderliche Komponente einfach per Drag-and-Drop in Ihrem Lead-Formular.
* Mithilfe dieser Komponenten kann der Autor ein eigenständiges Formular entwerfen. Diese Felder entsprechen den Lead-Formular-Feldern. In eigenständigen oder importierten Zip-Anwendungen kann der Benutzer mit den Formularfeldern „cq:form“ oder „cta lead“ weitere Felder hinzufügen und diese seinen Anforderungen entsprechend benennen und entwerfen.
* Ordnen Sie Formularfelder mithilfe spezifischer vordefinierter Namen für CTA-Lead-Formulare zu, z. B. „firstName“ für den Vornamen in einem Lead-Formular usw.
* Felder, die nicht dem Lead-Formular zugewiesen sind, werden cq:form-Komponenten zugewiesen: Text, Optionsschalter, Kontrollkästchen, Dropdown, Verborgen, Kennwort.
* Der Benutzer kann den Titel mithilfe des Tags &quot;label&quot;angeben und die Formatierung mithilfe des Stilattributs &quot;class&quot;bereitstellen (nur für CTA-Lead-Formular-Komponenten verfügbar).
* Die „Vielen Dank“-Seite und die Abonnement-Liste können als versteckter Parameter des Formulars (vorhanden in der Datei index.htm) bereitgestellt werden oder über die Bearbeitungsleiste von „Start des Lead-Formulars“ hinzugefügt oder bearbeitet werden:

   &lt;input type=&quot;hidden&quot; name=&quot;redirectUrl&quot; value=&quot;/content/we-retail/en/user/register/thank_you&quot;/>

   &lt;input type=&quot;hidden&quot; name=&quot;groupName&quot; value=&quot;leadForm&quot;/>

* Beschränkungen wie „Erforderlich“ können in jeder der Komponenten unter „Konfiguration bearbeiten“ angegeben werden.

HTML-Tag mit in der importierten Zip enthaltenem grafischen Link: Hier wird &quot;firstName&quot;dem Lead-Formular &quot;firstName&quot;usw. zugeordnet, mit Ausnahme von Kontrollkästchen - diese beiden Kontrollkästchen werden der Dropdown-Komponente cq:form zugeordnet.

```xml
<div id="cqcanvas">
   <div id="form_wrapper">
    <h2>NEWSLETTER SIGN UP</h2>
       <div data-cq-component="leadFormGeneration">
       <form method="post" action="#" onsubmit="return popupBox()">
       <label for="firstName" class="checkText">
        FIRST NAME
       </label><br />
       <input name="firstName" class="text pink" type="text" /><br />
       <label for="lastName" class="checkText">
        LAST NAME
       </label><br />
       <input name="lastName" class="text pink" type="text" /><br />
       <label for="emailId" class="checkText">
        EMAIL ADDRESS
       </label><br />
       <input name="emailId" class="text pink" type="text" /><br />

       <div class="checkboxes">
       <input type="checkbox" class="check" name="send_news" /> <label for="send_news" class="checkText">Send me the latest We.Retail news and announcements.</label><br />
       <input type="checkbox" class="check" name="send_offers" /> <label for="send_offers" class="checkText">Send me We.Retail deals and special offers.</label><br />
       </div>
       <input type="submit" name="submit" class="submit pink" value="Sign Up >" />
       </form>
     </div>
   </div>
```

### Parsys {#parsys}

Das AEM-parsys ist eine Container-Komponente, die andere AEM-Komponenten enthalten kann. Es ist möglich, in das importierte HTML eine parsys-Komponente einzufügen. Dadurch kann der Benutzer bearbeitbare AEM zur Landingpage hinzufügen/löschen, selbst wenn sie importiert wurde.

Das Absatzsystem bietet Benutzern die Möglichkeit, mithilfe des Sidekicks Komponenten hinzuzufügen.

HTML-Markup zum Einfügen einer parsys-Komponente (`foundation/components/parsys`) in das HTML im Designpaket:

```xml
<div data-cq-component="parsys">
   <div data-cq-component="title"><h2>ULTIMATE PROTECTION</h2></div>
        <div data-cq-component="title"><h3>ON SALE</h3></div>
</div>
```

Das Einschließen des obigen Markups in die HTML führt zu folgenden Aufgaben:

* Fügt eine AEM parsys-Komponente (foundation/components/parsys) in die Landingpage ein, die nach dem Import des Designpakets erstellt wurde.
* Startet den Sidekick mit Standardkomponenten. Neue Komponenten können zur Landingpage hinzugefügt werden, indem Komponenten aus dem Sidekick auf die parsys-Komponente gezogen werden.
* Zwei Titelkomponenten sind ebenfalls Teil des parsys.

### Ziel {#target}

Die target-Komponente zeigt den Inhalt eines Erlebnisses auf der Seite an. In einer Kampagne können viele Erlebnisse erstellt werden, und die Zielkomponente kann verschiedenen Benutzern, die die Seite besuchen, dynamisch Inhalte aus verschiedenen Erlebnissen anzeigen.

Das HTML-Markup zum Einfügen einer Zielkomponente und zum Erstellen verschiedener Erlebnisse in einer Kampagne:

```xml
<div data-cq-component="target">
 <section data-cq-component="experience" data-cq-experience="default">
  <p data-cq-component="text">Default content. Select this campaign in client context to view other experiences</p>
 </section>

 <section data-cq-component="experience" data-cq-segment="over-30">
  <p data-cq-component="text">Content for Over 30</p>
 </section>

 <section data-cq-component="experience" data-cq-segment="under-30">
  <p data-cq-component="text">Content for Under 30</p>
 </section>
</div>
```

## Zusätzliche Importoptionen {#additional-importing-options}

Neben der Angabe, ob importierte Komponenten bearbeitbar AEM sind, können Sie vor dem Import des Designpakets auch Folgendes konfigurieren:

* Festlegen von Seiteneigenschaften durch Extrahieren der in der importierten HTML definierten Metadaten.
* Gibt die Zeichensatzkodierung im HTML an.
* Überlagern der Importtool-Seitenvorlage.

### Festlegen von Seiteneigenschaften durch Extrahieren von in importierten HTML definierten Metadaten {#setting-page-properties-by-extracting-metadata-defined-in-imported-html}

Die folgenden im Kopf der importierten HTML deklarierten Metadaten werden vom Design Importer als Eigenschaft &quot;jcr:description&quot;extrahiert und beibehalten:

* &lt;meta name=&quot;description&quot; content=&quot;&quot;>

Das im HTML-Tag festgelegte Attribut lang wird vom Design Importer als Eigenschaft &quot;jcr:language&quot;extrahiert und beibehalten

* &lt;html lang=&quot;en&quot;>

### Festlegen der Zeichensatzkodierung im HTML-Code {#specifying-the-charset-encoding-in-the-html}

Der Design Importer liest die im importierten HTML festgelegte Kodierung. Die Kodierung kann wie folgt festgelegt werden:

`<meta charset="UTF-8">`

*ODER*

`<meta http-equiv="content-type" content="text/html;charset=utf-8">`

Wenn in der importierten HTML keine Kodierung angegeben ist, ist die vom Design Importer festgelegte Standardkodierung UTF-8.

### Vorlage überlagern {#overlaying-template}

Die Vorlage „Leere Einstiegsseite“ kann überlagert werden, indem eine neue erstellt wird unter: `/apps/<appName>/designimporter/templates/<templateName>`

Die Schritte zum Erstellen einer neuen Vorlage in AEM werden [hier](/help/sites-developing/templates.md) erläutert.

### Verweisen auf eine Komponente von der Landingpage {#referring-a-component-from-landing-page}

Angenommen, Sie verfügen über eine Komponente, auf die Sie in Ihrem HTML mit dem data-cq-component-Attribut verweisen möchten, sodass der Design Importer an dieser Stelle eine Komponente rendert. Sie möchten z. B. folgende table-Komponente referenzieren: (`resourceType = /libs/foundation/components/table`). Sie müssen das HTML wie folgt ergänzen:

`<div data-cq-component="/libs/foundation/components/table">foundation table</div>`

Der Pfad in der data-cq-component sollte der resourceType der Komponente sein.

### Best Practices {#best-practices}

Die Verwendung von CSS-Selektoren, die den folgenden ähneln, wird nicht für die Verwendung mit Elementen empfohlen, die beim Import zur Komponentenkonvertierung markiert sind.

| E > F | ein einem E-Element untergeordnetes F-Element | [Untergeordneter Kombinator](https://www.w3.org/TR/css3-selectors/#child-combinators) |
|---|---|---|
| E + F | ein F-Element, dem ein E-Element unmittelbar vorhergeht | [Angrenzender gleichrangiger Kombinator](https://www.w3.org/TR/css3-selectors/#adjacent-sibling-combinators) |
| E ~ F | ein F-Element, dem ein E-Element vorangestellt ist | [Allgemeiner gleichrangiger Kombinator](https://www.w3.org/TR/css3-selectors/#general-sibling-combinators) |
| E:root | ein E-Element, Stamm des Dokuments | [Strukturelle Pseudoklassen](https://www.w3.org/TR/css3-selectors/#structural-pseudos) |
| E:nth-child(n) | ein E-Element, das n. untergeordnete Element des übergeordneten Elements | [Strukturelle Pseudoklassen](https://www.w3.org/TR/css3-selectors/#structural-pseudos) |
| E:nth-last-child(n) | ein E-Element, das n. untergeordnete Element des übergeordneten Elements, das vom letzten Element gezählt wird | [Strukturelle Pseudoklassen](https://www.w3.org/TR/css3-selectors/#structural-pseudos) |
| E:nth-of-type(n) | ein E-Element, das n. gleichrangige Element seines Typs | [Strukturelle Pseudoklassen](https://www.w3.org/TR/css3-selectors/#structural-pseudos) |
| E:nth-last-of-type(n) | ein E-Element, das n. gleichrangige Element seines Typs, das vom letzten Element gezählt wird | [Strukturelle Pseudoklassen](https://www.w3.org/TR/css3-selectors/#structural-pseudos) |

Dies liegt daran, dass zusätzliche HTML-Elemente wie &lt;div> werden nach dem Import zum generierten HTML-Code hinzugefügt.

* Skripte, die sich auf eine ähnliche Struktur wie die oben stehende stützen, werden ebenfalls nicht zur Verwendung mit Elementen empfohlen, die zur Konvertierung in AEM Komponenten markiert sind.
* Die Verwendung von Stilen in den Markup-Tags für die Komponentenkonvertierung wie &lt;div data-cq-component=”&amp;ast;”> wird nicht empfohlen.
* Beim Designlayout sollten die Best Practices für das HTML5-Boilerplate befolgt werden. Lesen Sie mehr unter [https://html5boilerplate.com/](https://html5boilerplate.com/).

## Konfigurieren von OSGi-Modulen {#configuring-osgi-modules}

Folgende Komponenten geben Eigenschaften an, die über die OSGi-Konsole konfiguriert werden können:

* Landingpage Design Importer
* Builder für Landingpages
* Builder für mobile Landingpages
* Eintrags-Präprozessor für Landingpages

In der folgenden Tabelle werden die Eigenschaften kurz beschrieben:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Komponente</strong></td> 
   <td><strong>Eigenschaftsname</strong></td> 
   <td><strong>Beschreibung der Eigenschaft </strong></td> 
  </tr> 
  <tr> 
   <td>Landingpage Design Importer</td> 
   <td>Filter extrahieren</td> 
   <td>Die Liste der regulären Ausdrücke, die für das Filtern der Dateien beim Extrahieren verwendet werden. <br />Zip-Einträge, die einem der angegebenen Muster entsprechen, werden von der Extraktion ausgeschlossen.</td> 
  </tr> 
  <tr> 
   <td>Builder für Landingpages</td> 
   <td>Dateimuster</td> 
   <td>Der Builder für die Landingpage kann so konfiguriert werden, dass er HTML-Dateien verwaltet, die einem bestimmten im Dateimuster definierten regulären Ausdruck entsprechen.</td> 
  </tr> 
  <tr> 
   <td>Builder für mobile Landingpages</td> 
   <td>Dateimuster</td> 
   <td>Der Builder für die Landingpage kann so konfiguriert werden, dass er HTML-Dateien verwaltet, die einem bestimmten im Dateimuster definierten regulären Ausdruck entsprechen.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Gerätegruppen</td> 
   <td>Die Liste der Gerätegruppen, die unterstützt werden sollen.</td> 
  </tr> 
  <tr> 
   <td>Eintrags-Präprozessor für Landingpages</td> 
   <td>Suchmuster </td> 
   <td>Das Muster, nach dem im Inhalt der Einträge im Archiv gesucht wird. Dieser reguläre Ausdruck wird Zeile für Zeile mit dem Eintragsinhalt abgeglichen. Bei einer Übereinstimmung wird der übereinstimmende Text durch das angegebene Ersetzungsmuster ersetzt.<br /> <br /> Beachten Sie den unten stehenden Hinweis bezüglich aktuellen Beschränkungen für den Eintrags-Präprozessor für die Einstiegsseite.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Muster ersetzen</td> 
   <td>Das Muster, das die gefundenen Übereinstimmungen ersetzt. Sie können Gruppenreferenzen für reguläre Ausdrücke wie $1, $2 verwenden. Außerdem unterstützt dieses Muster Schlüsselwörter wie {designPath}, die während des Imports durch die aktuellen Werte ersetzt werden.</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>**Aktuelle Beschränkung des Eintrags-Präprozessors für Landingpages:**
>Wenn Sie Änderungen am Suchmuster vornehmen müssen, müssen Sie beim Öffnen des Felix Property Editor manuell umgekehrte Schrägstriche einfügen, um die regex-Metazeichen auszukommentieren. Wenn Sie umgekehrte Schrägstriche nicht manuell hinzufügen, wird der Regex als ungültig betrachtet und ersetzt nicht das ältere.
>
>Wenn die Standardkonfiguration beispielsweise
>
>`/\&ast *CQ_DESIGN_PATH *\*/ *(['"])`
>
>Und Sie müssen im Suchmuster `CQ_DESIGN_PATH` durch `VIPURL` ersetzen, dann sollte Ihr Suchmuster wie folgt aussehen:
>
>`/\* *VIPURL *\*/ *(['"])`

## Fehlerbehebung {#troubleshooting}

Beim Import des Designpakets können mehrere Fehler auftreten, die in diesem Abschnitt beschrieben werden.

### Initialisierung des Sidekicks mit relevanten Komponenten der Einstiegsseite {#initialization-of-sidekick-with-landing-page-relevant-components}

Wenn das Designpaket ein parsys-Komponenten-Markup enthält, werden nach dem Import im Sidekick für Einstiegsseiten relevante Komponenten angezeigt. Sie können neue Komponenten per Drag-and-Drop auf die parsys-Komponente in der Einstiegsseite ziehen. Sie können auch den Design-Modus aufrufen und dem Sidekick neue Komponenten hinzufügen.

### Während des Imports werden Fehlermeldungen angezeigt {#error-messages-displayed-during-import}

Wenn Fehler auftreten (z. B. wenn es sich beim importierten Paket nicht um eine gültige Zip-Datei handelt), importiert der Design Importer das Paket nicht und zeigt stattdessen oben auf der Seite über dem Drag-and-Drop-Feld eine Fehlermeldung an. Hier werden Beispiele für Fehlerszenarios aufgeführt. Wenn Sie den Fehler korrigiert haben, können Sie die aktualisierte Zip-Datei erneut in dieselbe leere Einstiegsseite importieren. Folgende Szenarien weisen Fehler auf:

* Das importierte Designpaket ist kein gültiges ZIP-Archiv.
* Das importierte Designpaket enthält auf der höchsten Ebene keine index.html.

### Nach dem Import werden Warnmeldungen angezeigt {#warnings-displayed-after-import}

Wenn Warnmeldungen angezeigt werden (z. B. „HTML verweist auf Bilder, die nicht im Paket enthalten sind“), importiert der Design Importer das Zip-Archiv, zeigt aber gleichzeitig im Ergebnisfenster eine Liste mit Fehlern/Warnungen an. Wenn Sie auf den Fehlerlink klicken, wird eine Liste mit Warnmeldungen angezeigt, die auf Fehler innerhalb des Designpakets verweisen. Unter anderem werden in folgenden Fällen vom Design Importer Warnmeldungen erzeugt und angezeigt:

* HTML verweist auf Bilder, die im Paket nicht vorhanden sind.
* HTML verweist auf Skripte, die im Paket nicht vorhanden sind.
* HTML verweist auf Stile, die im Paket nicht vorhanden sind.

### Wo werden die Dateien der ZIP-Datei in AEM gespeichert? {#where-are-the-files-of-the-zip-file-being-stored-in-aem}

Nach dem Import der Einstiegsseite werden die Dateien (Bilder, CSS, JS usw.) innerhalb des Designpakets an folgendem Speicherort in AEM gespeichert:

`/etc/designs/default/canvas/content/campaigns/<name of brand>/<name of campaign>/<name of landing page>`

Angenommen, die Einstiegsseite wird unter der Kampagne We.Retail erstellt und der Name der Einstiegsseite lautet **myBlankLandingPage**. In diesem Fall werden die Zip-Dateien in folgendem Verzeichnis gespeichert:

`/etc/designs/default/canvas/content/campaigns/geometrixx/myBlankLandingPage`

### Formatierung nicht beibehalten {#formatting-not-preserved}

Beachten Sie beim Erstellen Ihres CSS die folgenden Einschränkungen:

Wenn ein Text- und (bearbeitbares) Bild wie folgt aussehen:

```xml
<div class="box">
<p><div data-cq-component="image"><img src="assets/image.jpg" width="115"
height="116" /></div>Some Text </p>
</div>
```

mit einem wie folgt auf die Klasse `box` angewendeten CSS:

```xml
.box

{ width: 450px; padding:10px; border: 1px #C5DBE7 solid; margin: 0px auto 0 auto; background-image:url(assets/box.gif); background-repeat:repeat-x,y; font-family:Verdana, Arial, Helvetica, sans-serif; font-size:12px; color:#6D6D6D; }
```

wird `box img` im Design Importer verwendet. Die daraus resultierende Einstiegsseite wird ohne Formatierung angezeigt. Um dies zu umgehen, beachten Sie, dass AEM im CSS div-Tags hinzufügt, und schreiben Sie den Code entsprechend um. Andernfalls sind einige CSS-Regeln ungültig.

```xml
.box img

{ float:right; margin: 0 0 5px 5px; border: 1px #343434 solid; }
```

>[!NOTE]
>
>Außerdem sollten Designer beachten, dass nur Code innerhalb des **id=cqcanvas**-Tags vom Importer erkannt wird. Andernfalls bleibt das Design nicht erhalten.
