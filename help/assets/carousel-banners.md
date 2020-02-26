---
title: Karussellbanner
seo-title: Karussellbanner
description: Informationen zum Arbeiten mit Karussellbannern in dynamischen Medien
seo-description: Informationen zum Arbeiten mit Karussellbannern in dynamischen Medien
uuid: 6d6de9ac-a6e1-4f07-a610-cc84e26bf76b
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 4b532cd3-1561-4b5c-8b4b-420c278926f0
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939

---


# Karussellbanner {#carousel-banners}

Mit Karussellbannern können Marketingexperten die Konversionsrate steigern, indem sie auf einfache Art Drehbanner mit Promo-Inhalten erstellen, die auf beliebigen Bildschirmen bereitgestellt werden können.

Das Erstellen und Ändern von Inhalten auf Werbebannern kann zeitaufwendig sein und Ihre Fähigkeit beeinträchtigen, neue Inhalte schnell zu veröffentlichen oder zielgerichteter zu gestalten. Karussell-Banner ermöglichen es Ihnen, sich schnell drehende Banner zu erstellen oder zu ändern, Interaktivität wie Hotspots, Verknüpfungen zu Produktdetails oder zugehörigen Ressourcen hinzuzufügen und sie auf jedem Bildschirm bereitzustellen - damit Sie neue Werbeinhalte schneller auf den Markt bringen können.

Karussellbanner sind Banner, die durch die Bezeichnung **CAROUSELSET** gekennzeichnet sind:

![chlimage_1-438](assets/chlimage_1-438.png)

Auf Ihrer Website kann ein Karussellbanner wie folgt aussehen:

![chlimage_1-439](assets/chlimage_1-439.png)

Hier können Sie durch die Bilder navigieren (durch Klicken auf die Zahlen). Zusätzlich drehen sich die Folien automatisch basierend auf einem Intervall, das Sie anpassen können. Bilder, die Sie im Karussellbanner einfügen, unterstützen sowohl Hotspots als auch Imagemaps, in denen Benutzer auf einen Hyperlink tippen oder klicken oder auf ein Schnellansichtsfenster zugreifen können.

In diesem Beispiel hat der Benutzer auf eine Imagemap geklickt oder getippt und das Schnellansichtsfenster für Handschuhe aufgerufen:

![chlimage_1-440](assets/chlimage_1-440.png)

## Video zur Erstellung von Karussellbannern {#watch-how-carousel-banners-are-created}

Sehen Sie sich eine exemplarische Vorgehensweise (10 Minuten und 33 Sekunden) zur [Erstellung von Karussellbannern](https://s7d5.scene7.com/s7viewers/html5/VideoViewer.html?videoserverurl=https://s7d5.scene7.com/is/content/&emailurl=https://s7d5.scene7.com/s7/emailFriend&serverUrl=https://s7d5.scene7.com/is/image/&config=Scene7SharedAssets/Universal_HTML5_Video_social&contenturl=https://s7d5.scene7.com/skins/&asset=S7tutorials/InteractiveCarouselBanner) an. Sie erfahren außerdem, wie eine Vorschau auf Karussellbannern angezeigt wird und wie diese bearbeitet und bereitgestellt werden.

>[!NOTE]
>
>Benutzer, die keine Administratoren sind, müssen der Gruppe **dam-users** hinzugefügt werden, damit sie Karussellbanner erstellen oder bearbeiten können. Sollten Sie Schwierigkeiten beim Erstellen oder Bearbeiten haben, wenden Sie sich an den Systemadministrator, der Sie der Gruppe **dam-users** hinzufügen kann.

## Schnellstart: Karussellbanner {#quick-start-carousel-banners}

So schaffen Sie einen schnellen Einstieg:

1. [Identifizieren Sie Hotspot- und Imagemap-Variablen](#identifying-hotspot-and-image-map-variables) (nur für Kunden, die AEM Assets + Dynamic Media verwenden).

   Ermitteln Sie zunächst die von der vorhandenen Schnellansichtsimplementierung verwendeten dynamischen Variablen, damit Sie die Hotspots und Imagemap-Daten beim Erstellen von Karussellbannern in AEM Assets korrekt eingeben können.

   >[!NOTE]
   >
   >Wenn Sie AEM Sites- oder eCommerce-Kunde sind, können Sie die integrierte Funktion verwenden, um zu den Produktseiten zu navigieren und die vorhandenen SKUs im Produktkatalog zu suchen. Sie müssen keine Hotspot- oder Imagemap-Variablen manuell eingeben. Weitere Informationen finden Sie unter [Einrichten von eCommerce](/help/sites-administering/generic.md).
   >
   >Wenn Sie AEM Assets und dynamische Medien verwenden, geben Sie Daten für Hotspots und Imagemaps manuell ein und fügen Sie dann die veröffentlichte URL oder den Einbettungscode in Ihrem Drittanbietersystem für Web Content Management ein.

1.  Optional: [Erstellen Sie bei Bedarf eine Viewer-Voreinstellung für das Karussellset](managing-viewer-presets.md).

   Wenn Sie ein Administrator sind, können Sie das Verhalten und das Erscheinungsbild des Karussells anpassen, indem Sie eine eigene Karussell-Viewer-Vorgabe erstellen. Der größten Vorteile besteht darin, dass diese benutzerdefinierte Viewer-Vorgabe für mehrere Karussells wiederverwendet werden kann. Benutzer haben jedoch auch die Möglichkeit, das Verhalten und das Erscheinungsbild des Karussells direkt bei der Erstellung anzupassen. Dies ist der bevorzugte Ansatz, wenn Sie ein sehr spezifisches Design für ein bestimmtes Karussell wünschen.

1. [Laden Sie ein Bildbanner hoch](#uploading-image-banners).

   Laden Sie Bildbanner hoch, die interaktiv sein sollen.

1. [Erstellen Sie ein Karussell-Set](#creating-carousel-sets).

   In Karussell-Sets navigieren Benutzer durch Bannerbilder und tippen auf Hotspots oder Imagemaps, um auf relevante Inhalte zuzugreifen.

   Um ein Karussellset in Assets zu erstellen, tippen Sie auf **[!UICONTROL Erstellen]** und wählen Sie dann **[!UICONTROL Karussellsets]**. Fügen Sie Folien Assets hinzu und tippen Sie auf **[!UICONTROL Speichern]**. Sie können das Erscheinungsbild und Verhalten des Karussells auch direkt im Editor bearbeiten.

1. [Fügen Sie Hotspots oder Imagemaps in einem Bildbanner hinzu.](#adding-hotspots-or-image-maps-to-an-image-banner)

   Fügen Sie einem Bild-Banner einen oder mehrere Hotspots oder Imagemaps hinzu und verknüpfen Sie die einzelnen Hotspots oder Imagemaps mit einer Aktion wie einem Link, einer QuickView oder einem Erlebnisfragment. Nachdem Sie Hotspots oder Imagemaps hinzugefügt haben, schließen Sie diese Aufgabe ab, indem Sie das Karussell-Set veröffentlichen. Durch das Veröffentlichen wird der Einbettungscode erstellt, den Sie kopieren und auf die Einstiegsseite Ihrer Website anwenden können.

   Siehe [(Optional) Anzeigen einer Vorschau für Karussellbanner](#optional-previewing-carousel-banners) – Optional. Bei Bedarf können Sie eine Darstellung des Karussell-Sets anzeigen und dessen Interaktivität testen.

1. [Veröffentlichen Sie Karussellbanner.](#publishing-carousel-banners) 

   Sie veröffentlichen ein Karussell-Set wie jedes andere Asset. In Assets, navigate to the Carousel Set and select it and tap or tap **[!UICONTROL Publish]**. Durch Veröffentlichen eines Karussell-Sets wird die URL und die Einbettungszeichenfolge aktiviert.

1. Führen Sie einen der folgenden Schritte aus:

   * [Fügen Sie Ihrer Webseite ein Karussellbanner hinzu.](#adding-a-carousel-banner-to-your-website-page) Sie können die kopierte Karussellbanner-URL oder den Einbettungscode auf der Website hinzufügen.

      * [Integrieren Sie das Karussellbanner in eine Schnellansicht.](#integrating-the-carousel-banner-with-an-existing-quickview) Wenn Sie ein Drittanbietersystem für Web Content Management verwenden, müssen Sie das neue Karussellbanner in der vorhandenen Schnellansichtsimplementierung auf Ihrer Website integrieren.
   * [Fügen Sie Ihrer Website in AEM ein Karussellbanner hinzu.](adding-dynamic-media-assets-to-pages.md) Wenn Sie AEM Sites-Kunde sind, können Sie das Karussell-Set der Seite in AEM direkt hinzufügen, indem Sie die interaktive Medienkomponente verwenden.


If you need to edit Carousel Sets, see [editing Carousel Sets](#editing-carousel-sets). In addition, you can view and edit [Carousel Set properties](/help/assets/managing-assets-touch-ui.md#editing-properties).

## Ermitteln von Hotspot- und Imagemap-Variablen {#identifying-hotspot-and-image-map-variables}

Ermitteln Sie zunächst die von der vorhandenen Schnellansichtsimplementierung verwendeten dynamische Variablen, damit Sie die Hotspots oder Imagemap-Daten beim Erstellen von Karussell-Sets in AEM Assets korrekt eingeben können.

Beim Hinzufügen von Hotspots oder Imagemaps zu einem Bannerbild in AEM Assets müssen Sie jedem Hotspot und jeder Imagemap eine SKU und optional zusätzliche Variablen zuweisen. Mithilfe dieser Variablen werden Hotspots oder Imagemaps später Schnellansichtsinhalte zugeordnet.

>[!NOTE]
>
>Wenn Sie AEM Sites- und/oder AEM eCommerce-Kunde sind, können Sie diesen Schritt überspringen. Sie müssen keine Hotspot- oder Imagemap-Variablen manuell ermitteln. Sie können die Integration mit eCommerce für die Produktintegration verwenden. Weitere Informationen finden Sie unter [Einrichten von eCommerce](/help/sites-administering/generic.md). Darüber hinaus können Sie die interaktive Komponente verwenden und in Ihre Webseite einfügen.
>
>Wenn Sie AEM Assets- oder Medien-Kunde sind, veröffentlichen Sie den URL- oder Einbettungscode, integrieren Sie ihn dann in Ihrem Drittanbieter-Content Management System und ermitteln Sie Hotspots und Imagemaps manuell.

Es ist wichtig, die Anzahl und den Typ der Variablen, denen Hotspot- oder Imagemap-Daten zugewiesen werden sollen, korrekt zu ermitteln. Jeder Hotspot bzw. jede Imagemap, der/die einem Bannerbild hinzugefügt wird, muss genügend Informationen enthalten, um das Produkt im vorhandenen Backend-System eindeutig zu identifizieren. Gleichzeitig sollten Hotspots oder Imagemaps nicht mehr Daten enthalten als unbedingt notwendig. Dies würde die Dateneingabe unnötig erschweren und bei der Verwaltung von Hotspots und Imagemaps könnten leichter Fehler auftreten.

Es gibt verschiedene Möglichkeiten, den für Hotspot- oder Imagemap-Daten zu verwendenden Variablensatz zu ermitteln,

Manchmal ist es ausreichend, IT-Experten zu konsultieren, die für die vorhandene Schnellansichtsimplementierung verantwortlich sind. Diese kennen wahrscheinlich den Mindestsatz an Daten, die erforderlich sind, um die Schnellansicht im System zu ermitteln. In den meisten Fällen ist es jedoch auch möglich, einfach das vorhandene Verhalten des Front-End-Codes zu analysieren.

Der Großteil der Schnellansichtsimplementierungen verwendet das folgende Modell:

* Benutzer aktiviert ein Benutzeroberflächenelement auf der Website. For example, clicking a **[!UICONTROL Quick View]** button.
* Die Website sendet eine Ajax-Anforderung an das Back-End, um bei Bedarf die Schnellansichtsdaten oder -inhalte zu laden.
* Die Schnellansichtsdaten werden in den Inhalt übersetzt, um für das Rendern auf der Webseite vorbereitet zu werden.
* Schließlich zeigt der Front-End-Code diesen Inhalt visuell auf dem Bildschirm an.

Dann werden unterschiedliche Bereiche der vorhandenen Website besucht, auf denen die Schnellansichtsfunktion implementiert wird, die Schnellansicht wird ausgelöst und die Ajax-URL, die durch die Webseite zum Laden der Schnellansichtsdaten oder -inhalte gesendet wurde, wird erfasst.

Normalerweise müssen Sie keine speziellen Debugging-Tools verwenden. Moderne Webbrowser verfügen über Web-Inspektoren, die dafür ausreichend sind. Die folgenden Webbrowser beispielsweise umfassen Web-Inspektoren:

* To see all outgoing HTTP requests in Google Chrome, press F12 (Windows) or Command-Option-I (Mac) to open the Developer Tools panel, and then tap the **[!UICONTROL Network]** tab.
* In Firefox können Sie das Firebug-Plug-in aktivieren, indem Sie F12 (Windows) bzw. Befehlstaste + Wahltaste + I (Mac) drücken und die Registerkarte „Netz“ öffnen, oder Sie öffnen die Registerkarte „Netzwerk“ im integrierten Inspektor-Tool.

Wenn die Netzwerküberwachung im Browser aktiviert ist, lösen Sie die Schnellansicht auf der Seite aus.

Suchen Sie nun die Schnellansichts-Ajax-URL im Netzwerkprotokoll und kopieren Sie die aufgezeichnete URL für die zukünftige Analyse. In den meisten Fällen werden beim Auslösen der Schnellansicht zahlreiche Anforderungen an den Server gesendet. Normalerweise ist die Schnellansichts-Ajax-URL die erste in der Liste. It has either a complex query string portion or path, and its response MIME type is either `text/html`, `text/xml`, or `text/javascript`.

Während dieses Vorgangs müssen Sie verschiedene Bereiche der Website mit verschiedenen Produktkategorien und -typen besuchen. Grund dafür ist, dass Schnellansichts-URLs möglicherweise Teile aufweisen, die für eine bestimmte Website-Kategorie häufig vorkommen, sich aber nur ändern, wenn Sie einen anderen Bereich der Website besuchen.

Im einfachsten Fall ist der einzige variable Teil der Schnellansichts-URL die Produkt-SKU. In diesem Fall ist der SKU-Wert der einzige Datenteil, den Sie benötigen, um dem Bannerbild Hotspots oder Imagemaps hinzuzufügen.

In komplexen Fällen hat die Schnellansichts-URL allerdings mehrere verschiedene Elemente zusätzlich zur SKU, wie Kategorie-ID, Farbcode, Größencode usw. In diesen Fällen ist jedes Element eine separate Variable in der Hotspot- oder Imagemap-Datendefinition innerhalb der Karussellbanner-Funktion.

Im Folgenden finden Sie einige Beispiele für Schnellansichts-URLs und die resultierenden Hotspot- oder Imagemap-Variablen:

<table> 
 <tbody> 
  <tr> 
   <td>Einzelne SKU, befindet sich in der Abfragezeichenfolge.</td> 
   <td><p>Die aufgezeichneten Schnellansichts-URLs enthalten Folgendes:</p> 
    <ul> 
     <li><p><code>https://server/json?productId=866558&amp;source=100</code></p> </li> 
     <li><p><code>https://server/json?productId=1196184&amp;source=100</code></p> </li> 
     <li><p><code>https://server/json?productId=1081492&amp;source=100</code></p> </li> 
     <li><p><code>https://server/json?productId=1898294&amp;source=100</code></p> </li> 
    </ul> <p>The only variable part in the URL is the value of the <code>productId=</code> query string parameter, and it is clearly a SKU value. Daher benötigen unsere Hotspots oder Imagemaps nur SKU-Felder, die mit Werten wie <code>866558,</code> <code>1196184,</code> <code>1081492,</code> <code>1898294.</code></p> </td> 
  </tr> 
  <tr> 
   <td>Einzelne SKU, befindet sich am URL-Pfad.</td> 
   <td><p>Die aufgezeichneten Schnellansichts-URLs enthalten Folgendes:</p> 
    <ul> 
     <li><p><code>https://server/product/6422350843</code></p> </li> 
     <li><p><code>https://server/product/1607745002</code></p> </li> 
     <li><p><code>https://server/product/0086724882</code></p> </li> 
    </ul> <p>The variable part is in the last portion of the path, and it becomes the SKU value of the hotspots/image maps:<strong><code>6422350843</code>, <code>1607745002,</code> </strong><code>0086724882.</code></p> </td> 
  </tr> 
  <tr> 
   <td>SKU und Kategorie-ID in der Abfragezeichenfolge.</td> 
   <td><p>Die aufgezeichneten Schnellansichts-URLs enthalten Folgendes:</p> 
    <ul> 
     <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=305466</code></p> </li> 
     <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=310181</code></p> </li> 
     <li><p><code>https://server/quickView/product/?category=1740148&amp;prodId=308706</code></p> </li> 
    </ul> <p>In diesem Fall liegen zwei abweichende Teile in der URL vor. The SKU is stored in the <code>prodId</code> parameter and the category ID is stored in the <code>category=</code>parameter.</p> <p>Bei den Hotspot- oder Imagemap-Definitionen selbst handelt es sich um Paare. Also einen SKU-Wert und eine zuätzliche Variable mit dem Namen <code>categoryId</code>. Die resultierenden Paare lauten wie folgt:</p> 
    <ul> 
     <li><p>SKU is <strong><code>305466</code></strong> and <code>categoryId</code> is <code>1100004</code>.</p> </li> 
     <li><p>SKU is <strong><code>310181</code></strong> and <code>categoryId</code> is <strong><code>1100004</code></strong>.</p> </li> 
     <li><p>SKU is <strong><code>308706</code></strong> and <code>categoryId</code> is <strong><code>1740148</code></strong>.</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## Hochladen von Bildbannern {#uploading-image-banners}

If you have already uploaded the images that you want to use, advance to the next step, [Creating Carousel Sets](#creating-carousel-sets). Beachten Sie, dass die im Karussell verwendeten Bilder nach dem Aktivieren von dynamischen Medien hochgeladen werden müssen.

Informationen zum Hochladen von Bildbannern finden Sie unter [Hochladen von Assets](managing-assets-touch-ui.md).

## Erstellen von Karussell-Sets {#creating-carousel-sets}

>[!NOTE]
>
>Benutzer, die keine Administratoren sind, müssen der Gruppe **[!UICONTROL dam-users]** hinzugefügt werden, damit sie Karussellbanner erstellen oder bearbeiten können. Sollten Sie Schwierigkeiten beim Erstellen oder Bearbeiten haben, wenden Sie sich an den Systemadministrator, der Sie der Gruppe **dam-users** hinzufügen kann.

**So erstellen Sie ein Karussell-Set**:

1. In Assets, navigate to the folder where you want to create the Carousel Set and tap **[!UICONTROL Create > Carousel Set]**.
1. On the **[!UICONTROL Carousel Banner Editor]** page, tap **[!UICONTROL Tap to open Asset Selector]** to select the image for your first slide.

   On the **[!UICONTROL Carousel Banner Editor]** page, do either one of the following:

   * Tippen Sie oben links auf **[!UICONTROL Folie hinzufügen]**.
   * Tippen Sie in der Mitte der Seite auf **[!UICONTROL Tippen, um den Asset-Wähler zu öffnen]**.
   Tippen Sie zur Auswahl von Assets, die Sie in das Karussellset aufnehmen möchten. Die ausgewählten Assets sind mit einem Häkchen versehen. Wenn Sie die Assets ausgewählt haben, tippen Sie auf **[!UICONTROL Auswählen]**.

   Mit der Asset-Auswahl können Sie nach Assets suchen, indem Sie einen Suchbegriff eingeben und auf **[!UICONTROL Zurück]** tippen. Sie können auch Filter anwenden, um Ihre Suchergebnisse genauer abzustimmen. Sie können nach Pfad, Sammlung, Dateityp und Tag filtern. Wählen Sie den Filter aus und tippen Sie dann in der Symbolleiste auf das Symbol **[!UICONTROL Filter]**. Change the view by tapping the **[!UICONTROL View]** icon and selecting **[!UICONTROL Column View]**, **[!UICONTROL Card View]**, or **[!UICONTROL List View]**.

   Weitere Informationen finden Sie unter [Arbeiten mit Selektoren](working-with-selectors.md).

1. Fügen Sie weitere Folien hinzu, bis Sie alle gewünschten Bilder für das Karussell-Set ausgewählt haben.
1. (Optional) Führen Sie einen der folgenden Schritte aus:

   * Ziehen Sie bei Bedarf die Folios, um die Bilder in der Setliste neu anzuordnen.
   * Um ein Bild zu löschen, wählen Sie es aus und tippen Sie in der Symbolleiste auf **[!UICONTROL Folie löschen]**. 
   * Um eine Vorgabe anzuwenden, tippen Sie oben rechts auf die Dropdownliste mit den Vorgaben. Wählen Sie anschließend eine Vorgabe aus, um sie auf das ganze Set anzuwenden.
   To delete a slide, tap the slide, and tap **[!UICONTROL Delete Slide]** in the toolbar. Um eine Folie zu verschieben, tippen Sie auf das Symbol zur Neuanordnung und halten und bewegen Sie das Element an die gewünschte Position.

1. Nachdem Sie die Bilder in den Folien hinzugefügt haben, können Sie einen Hotspot, eine Imagemap oder beides in die Bilder einfügen. See [adding hotspots or image maps](#adding-hotspots-or-image-maps-to-an-image-banner).
1. Sie können das visuelle Design und das Verhalten von Karussell-Sets ändern, indem Sie auf die Registerkarten „Verhalten“ und „Darstellung“ tippen oder klicken und Anpassungen am Aussehen des Karussellbanners oder am Verhalten bestimmter Komponenten vornehmen. Weitere Informationen zum Verwenden des Viewer-Editors finden Sie unter [Verwalten von Viewer-Vorgaben](viewer-presets.md).

   >[!NOTE]
   >
   >Für Karussellbanner sollten Sie folgende Elemente anpassen:
   >* Dauer der Anzeige eines Bildes Standardmäßig wird jedes Bild für 9 Sekunden angezeigt.
   >* Animation. Standardmäßig sind alle Folienübergänge Überblendungen. Sie können einen anderen Übergang auswählen.
   >* Stil der Schaltflächen Benutzer können die Banner durchlaufen, indem sie auf die jeweiligen Punkte oder Zahlen tippen. Sie können ändern, wo die Set-Indikatoren angezeigt werden (und ob es sich um einen numerischen oder Punktstil handelt). Sie können auch ihre Größe bestimmen.
   >* Ändern des Markierungsstils einer Imagemap oder des Symbols für Hotspots.
   >* Wählen Sie vor dem Bearbeiten einer Viewer-Vorgabe das Format aus, auf dem die Vorgabe basieren soll. Wenn Sie diese Auswahl nicht treffen, wenn Sie mit dem Bearbeiten der Viewer-Vorgabe beginnen, werden alle Ihre Änderungen verworfen, wenn Sie eine andere Vorgabe festlegen. .


   Sie können in einer Vorschau anzeigen, wie das Karussellbanner aussehen wird. Siehe [(Optional) Anzeigen einer Vorschau für Karussellbanner](#optional-previewing-carousel-banners).

1. Tap **[!UICONTROL Save]** when finished.

## Adding hotspots or image maps to an Image Banner {#adding-hotspots-or-image-maps-to-an-image-banner}

Sie können einem Banner Hotspots oder Imagemaps mithilfe des Karussell-Set-Editors hinzufügen.

Beim Hinzufügen von Hotspots oder Imagemaps können Sie sie als eine Schnellansichts-Popup-Anzeige, als einen Hyperlink oder als Experience Fragment definieren.

Weitere Informationen finden Sie unter [Experience Fragments](/help/sites-authoring/experience-fragments.md).

>[!NOTE]
>
>Beachten Sie, dass die Social-Media-Freigabe-Werkzeuge im Karussell-Banner nicht unterstützt werden, wenn Sie den Viewer in ein Erlebnisfragment einbetten. Um dies zu umgehen, können Sie Viewer-Vorgaben verwenden oder erstellen, die keine Social Media Sharing-Werkzeuge haben. Mit diesen Viewer-Vorgaben können Sie sie erfolgreich in Erlebnisfragmente einbetten.

Vergessen Sie nicht, Ihre Arbeit zu speichern, wenn Sie einem Bild Hotspots oder Imagemaps hinzufügen. **[!UICONTROL Die Optionen &quot;Rückgängig]** &quot;und &quot; **[!UICONTROL Wiederholen]** &quot;in der oberen rechten Ecke der Seite werden während der aktuellen Erstellungssitzung/Bearbeitungssitzung unterstützt.

When you finish creating your carousel banner, you can optionally use **[!UICONTROL Preview]** to see a representation of how your carousel banner will appear to customers.

Siehe [(Optional) Anzeigen einer Vorschau für Karussellbanner](#optional-previewing-carousel-banners).

>[!NOTE]
>
>Wenn Sie einem [interaktiven Bild](interactive-images.md) oder einem Bild für ein Karussellbanner Hotspots hinzufügen, werden die Hotspot-Informationen immer am selben Metadatenspeicherort gespeichert, der relativ zum Speicherort des Bildes ist, unabhängig davon, ob es sich um ein interaktives Bild oder um ein Karussellbanner handelt. Das bedeutet, dass Sie dasselbe Bild zusammen mit den definierten Hotspot-Daten in beiden Viewern einfach wiederverwenden können.

>  Beachten Sie jedoch, dass Karussellbanner Imagemaps auf Bildern unterstützen, die auch Hotspots enthalten können. Bei interaktiven Bildern wird dies dagegen nicht unterstützt. Dies sollten Sie beachten, wenn Sie ein interaktives Bild oder ein Karussellbanner mit demselben Bild erstellen möchten. Stattdessen sollten Sie separate Kopien desselben Bildes verwenden, um interaktive Bilder und Karussellbilder zu erstellen.

>[!NOTE]
>
>Wenn Sie interaktive Bilder mit Hotspots bearbeiten, um das Bild zu beschneiden, werden die Hotspots entfernt.

**So fügen Sie einem Bildbanner Hotspots hinzu**:

1. Navigieren Sie in Assets zu dem Karussell-Set, das interaktiv sein soll.
1. Select the carousel set and tap **[!UICONTROL Edit]**.
1. Wählen Sie im Karussell-Viewer-Editor die Folie aus, die Sie interaktiv gestalten möchten.
1. Tippen Sie links oben auf der Seite auf **[!UICONTROL Hotspot]** oder **[!UICONTROL Image Map]**.
1. Führen Sie einen der folgenden Schritte aus:

   * Hotspots: Tippen Sie auf dem Bild auf eine Stelle, an der der Hotspot angezeigt werden soll.
   * Für Imagemaps: Tippen Sie im Bild auf und ziehen Sie dann von oben links nach unten rechts, um den Imagemap-Bereich zu erstellen. Sie können die Größe der Imagemap anpassen, indem Sie an den Ecken ziehen.
   Ziehen Sie den Hotspot oder die Imagemap ggf. an eine neue Position. Fügen Sie weitere Hotspots oder Imagemaps nach Bedarf hinzu.

   Um einen Hotspot oder eine Image Map zu löschen, tippen Sie auf die Registerkarte **[!UICONTROL Aktionen]**. Wählen Sie unter der Überschrift **[!UICONTROL Maps und Hotspots]** aus dem Dropdownmenü **[!UICONTROL Ausgewählter Typ]** den Namen des Hotspots oder der Landkarte aus, den/die Sie entfernen möchten. Tippen Sie auf das Symbol **[!UICONTROL Papierkorb]** neben dem Menü und dann auf **[!UICONTROL Löschen]**.

1. Geben Sie im Textfeld „Name“ den Namen des Hotspots oder der Imagemap ein. Dieser Name wird auch in der Dropdownliste **[!UICONTROL Karten und Hotspots]** angezeigt. Wenn Sie einen Namen angeben, können Sie den Hotspot oder die Imagemap leicht identifizieren, wenn Sie in Zukunft Änderungen daran vornehmen möchten.
1. Führen Sie einen der folgenden Schritte auf der Registerkarte **[!UICONTROL Aktion]** aus:

   * Tippen Sie auf **[!UICONTROL Schnellansicht]**.

      * If you are an AEM Sites and Ecommerce customer, tap the **[!UICONTROL Product Picker]** icon (magnifying glass) to open the **[!UICONTROL Select Product]** page. Tap the product you want to use, then tap the check mark in the upper-right corner of the page to return to the **[!UICONTROL Carousel Banner Editor]**.
      * Wenn Sie kein AEM-Sites- oder E-Commerce-Kunde sind

         * See [Identifying hotspot variables](#identifying-hotspot-and-image-map-variables) as you may want to define these variables.
         * Geben Sie dann manuell den SKU-Wert ein. In the **[!UICONTROL SKU Value]** text field, type the product&#39;s SKU (Stock Keeping Unit), which is a unique identifier for each distinct product or service that you offer. Der eingegebene SKU-Wert füllt automatisch den variablen Teil der Vorlage für die Schnellansicht, sodass das System den getippten Hotspot mit einer bestimmten SKU-Schnellansicht verknüpfen kann.
         * (Optional) If there are other variables within the quick view that you need to use to further identify a product, tap **[!UICONTROL Add Generic Variable]**. In the text field, specify an additional variable. Beispielsweise ist `category=Mens` eine hinzugefügte Variable.
         * Weitere Informationen finden Sie unter [Arbeiten mit Selektoren](working-with-selectors.md).
   * Tippen Sie auf **[!UICONTROL Hyperlink]**.

      * If you are an AEM Sites customer, tap the **[!UICONTROL Site Selector]** icon (folder) to navigate to a URL.

         >[!NOTE]
         >Die URL-basierte Verlinkungsmethode ist nicht möglich, wenn Ihr interaktiver Inhalt über Links mit relativen URLs verfügt, insbesondere über Links zu Seiten in AEM Sites.

      * If you are a standalone customer, in the **[!UICONTROL HREF]** text field, specify the full URL path to a linked web page.

         Vergessen Sie nicht anzugeben, ob der Link auf einer neuen Browser-Registerkarte (empfohlener Standard) oder auf derselben Registerkarte geöffnet werden soll.

         Weitere Informationen finden Sie unter [Arbeiten mit Selektoren](working-with-selectors.md).
   * Tippen Sie auf **[!UICONTROL Experience Fragment]**.

      * If you are an AEM Sites customer, tap the **[!UICONTROL Search]** icon (magnifying glass) to open the Experience Fragment page. Tap the Experience Fragment you want to use, then tap **[!UICONTROL Select]** in the upper-right corner of the page to return to the Hotspot management page.

         Weitere Informationen finden Sie unter [Experience Fragments](/help/sites-authoring/experience-fragments.md).

         **Hinweis**:Beachten Sie, dass die Social-Media-Freigabe-Werkzeuge im Karussell-Banner nicht unterstützt werden, wenn Sie den Viewer in ein Erlebnisfragment einbetten. Um dies zu umgehen, können Sie Viewer-Vorgaben verwenden oder erstellen, die keine Social Media Sharing-Werkzeuge haben. Mit diesen Viewer-Vorgaben können Sie sie erfolgreich in Erlebnisfragmente einbetten.

      * Legen Sie die Breite und Höhe des Experience Fragments fest, so wie es im Banner angezeigt werden soll.
   ![experience_fragment-carouselbanner](assets/experience_fragment-carouselbanner.png)

   Sie können in einer Vorschau anzeigen, wie das Karussellbanner aussehen wird. Siehe [(Optional) Anzeigen einer Vorschau für Karussellbanner](#optional-previewing-carousel-banners).

1. Tippen Sie auf **[!UICONTROL Speichern]**.
1. Veröffentlichen Sie das Karussell-Set. Durch das Veröffentlichen wird der Einbettungscode oder die URL erstellt, den/die Sie auf der Webseite verwenden können. Wenn Sie ein AEM Sites-Kunde sind, können Sie Ihrer Webseite das Karussell-Set direkt hinzufügen.

   Informationen hierzu finden Sie unter [Veröffentlichen von Assets](publishing-dynamicmedia-assets.md).

   Siehe [Hinzufügen eines Karussell-Sets zur Einstiegsseite Ihrer Website](#adding-a-carousel-banner-to-your-website-page).

## Bearbeiten von Karussell-Sets {#editing-carousel-sets}

>[!NOTE]
>
>Benutzer, die keine Administratoren sind, müssen der Gruppe **[!UICONTROL dam-users]** hinzugefügt werden, damit sie Karussellbanner erstellen oder bearbeiten können. Sollten Sie Schwierigkeiten beim Erstellen oder Bearbeiten haben, wenden Sie sich an den Systemadministrator, der Sie der Gruppe **[!UICONTROL dam-users]** hinzufügen kann.

Sie können mehrere Bearbeitungsaufgaben für Karussell-Sets ausführen, z. B.:

* einem Karussell-Set Folien hinzufügen. See also [Working with Selectors](working-with-selectors.md).
* die Anordnung der Folien im Karussell-Set ändern.
* Assets im Karussell-Set löschen
* Viewer-Vorgaben anwenden.
* das Karussell-Set löschen.
* Hotspots und Imagemaps hinzufügen oder bearbeiten. See also [Working with Selectors](working-with-selectors.md).

Achten Sie darauf, dass beim Bearbeiten interaktiver Bilder mit Hotspots und beim Beschneiden des Bildes die Hotspots entfernt werden.

**So bearbeiten Sie ein Karussell-Set**:

1. Führen Sie einen der folgenden Schritte aus:

   * Bewegen Sie den Mauszeiger über ein Karussell-Asset und tippen Sie auf **[!UICONTROL Bearbeiten]** (Stiftsymbol).
   * Bewegen Sie den Mauszeiger über ein Karussell-Asset, wählen Sie **[!UICONTROL Tippen]** (Kontrollkästchensymbol) und dann **[!UICONTROL Bearbeiten]** in der Symbolleiste.
   * Tippen Sie auf ein Karussell-Asset und dann links oben auf der Seite auf **[!UICONTROL Bearbeiten]** (Bleistiftsymbol).

1. Um das Karussell-Set zu bearbeiten, führen Sie einen der folgenden Schritte aus:

   * To add a slide, tap the **[!UICONTROL Add Slide]** icon then navigate to the asset you want to add to that slide and tap the checkmark.
   * Um die Folien neu anzuordnen, ziehen Sie eine Folie an eine neue Position (wählen Sie das Symbol für die Neuanordnung aus, um Elemente zu verschieben).
   * To add a hotspot or image map, tap the hotspot or image map icons and see [adding hotspots and image maps](#adding-hotspots-or-image-maps-to-an-image-banner).
   * Um das Erscheinungsbild und das Verhalten des Karussell-Sets zu bearbeiten, tippen Sie auf die Registerkarte **[!UICONTROL Erscheinungsbild]** oder **[!UICONTROL Verhalten]** und legen Sie dann die gewünschten Optionen fest.
   * Um Hotspots oder Imagemaps zu bearbeiten, wählen Sie auf der entsprechenden Folie einen Hotspot oder eine Imagemap aus und nehmen Sie die erforderlichen Änderungen auf der Registerkarte **[!UICONTROL Aktionen]** vor.
   * Um eine Folie zu löschen, wählen Sie sie aus und tippen Sie in der Symbolleiste auf **[!UICONTROL Folie löschen]**.
   * Um eine Vorgabe anzuwenden, tippen Sie oben rechts auf der Seite auf die Dropdownliste der Vorgaben und wählen Sie eine Viewer-Vorgabe aus.
   * Um ein ganzes Karussell-Set zu löschen, navigieren Sie zum Karussell-Set, wählen Sie es aus und tippen Sie auf **[!UICONTROL Löschen]**.

## (Optional) Previewing Carousel Banners {#optional-previewing-carousel-banners}

You can use **[!UICONTROL Preview]** to see what your carousel banner will look like to customers and to test the carousel banners hotspots and image maps to ensure they are behaving as expected.

Wenn das Karussellbanner Ihren Vorstellungen entspricht, können Sie es veröffentlichen.

* Siehe [Einbetten des Video- oder Bild-Viewers auf einer Webseite](embed-code.md).
* Siehe [Verknüpfen von URLs mit einer Webanwendung.](linking-urls-to-yourwebapplication.md). Beachten Sie, dass die URL-basierte Verlinkungsmethode nicht möglich ist, wenn Ihr interaktiver Inhalt über Links mit relativen URLs verfügt, insbesondere über Links zu Seiten in AEM Sites.
* Siehe [Hinzufügen von Assets mit dynamischen Medien zu Seiten.](adding-dynamic-media-assets-to-pages.md)

Um eine Vorschau für ein Karussellbanner anzuzeigen, verwenden Sie entweder den Karussell-Editor (bevorzugte Methode) oder die **[!UICONTROL Viewer]**-Liste.

**So erstellen Sie eine Vorschau von Karussellbannern**:

1. In **[!UICONTROL Assets]** navigieren Sie zu einem vorhandenen Karussellbanner, das Sie erstellt haben, und tippen Sie darauf, um das Banner zu öffnen.
1. Tippen Sie auf **[!UICONTROL Bearbeiten]**.
1. Wählen Sie in der Liste der Viewer-Vorgaben in der rechten Ecke der Symbolleiste einen Viewer, um das Karussellbanner auszuwählen.

   ![experience_fragment-carouselbanner-viewerdropdown](assets/experience_fragment-carouselbanner-viewerdropdown.png)

1. Tippen Sie auf **[!UICONTROL Vorschau]**.
1. Tippen Sie auf die Hotspots oder Imagemaps im Bild, um die zugehörigen Aktionen zu testen.

**So zeigen Sie eine Vorschau für Karussellbanner über die Viewer-Liste an**:

1. In **[!UICONTROL Assets]** navigieren Sie zu einem vorhandenen Karussellbanner, das Sie erstellt haben, und tippen Sie darauf, um das Banner zu öffnen.
1. Near the upper-left corner of the **[!UICONTROL Preview]** page, tap the **[!UICONTROL Content]** icon.
1. In the **[!UICONTROL Viewers]** list in the panel on the left side of the page, tap the name of the carousel banner viewer preset you want to use.
1. Tippen Sie auf die Hotspots oder Imagemaps im Bild, um die zugehörigen Aktionen zu testen.

## Veröffentlichen von Karussellbannern {#publishing-carousel-banners}

Sie müssen das Karussell veröffentlichen, um es zu verwenden. Durch Veröffentlichen eines Karussell-Sets werden die URL und der Einbettungscode aktiviert. Außerdem wird das Karussell in der Cloud für dynamische Medien veröffentlicht, die in ein CDN für skalierbare und leistungsfähige Bereitstellung integriert ist.

Wenn Sie ein vorhandenes interaktives Bild mit Hotspots für Ihr Karussellbanner verwenden, müssen Sie das interaktive Bild separat veröffentlichen, nachdem Sie das Karussellbanner veröffentlicht haben.

Wenn Sie ein bereits vorhandenes und veröffentlichtes interaktives Bild ändern, das Sie in einem Karussellbanner verwenden, müssen Sie das interaktive Bild veröffentlichen, bevor die Änderungen im Karussellbanner sichtbar werden.

Unter [Veröffentlichen von Assets mit dynamischen Medien](publishing-dynamicmedia-assets.md) finden sie Informationen zum Veröffentlichen von Karussellbannern.

## Hinzufügen eines Karussellbanners zu Ihrer Website {#adding-a-carousel-banner-to-your-website-page}

Nachdem Sie Bannerbilder hochgeladen haben, um ein Karussell zu erstellen, Hotspots und/oder Imagemaps zum Banner hinzugefügt und das Karussell-Set veröffentlicht haben, können Sie es jetzt Ihrer vorhandenen Webseite hinzufügen.

Wenn Sie AEM Sites-Kunde sind, können Sie das Karussellbanner Ihrer Seite direkt hinzufügen, indem Sie die interaktive Medienkomponente auf Ihre Seite ziehen. See [Adding Dynamic Media Assets to Pages.](adding-dynamic-media-assets-to-pages.md)

Wenn Sie jedoch nur AEM Assets verwenden, können Sie das Karussellbanner manuell der Einstiegsseite Ihrer Website hinzufügen, wie im folgenden Abschnitt beschrieben.

1. Kopieren Sie den Einbettungscode des veröffentlichten Karussell-Sets.

   Siehe [Einbetten des Video- oder Bild-Viewers auf einer Webseite](embed-code.md).

1. Fügen Sie den Einbettungscode, den Sie aus AEM Assets kopiert haben, auf Ihrer Webseite ein.

   Der kopierte Einbettungscode ist responsiv und sollte sich automatisch an den Einbettungsbereich der Seite anpassen.

## Integrating the Carousel Banner with an existing Quickview {#integrating-the-carousel-banner-with-an-existing-quickview}

Diese Aufgabe gilt nur, wenn Sie ein eigenständiger AEM Assets-Kunde sind.

Der letzte Schritt in diesem Prozess ist die Integration des Karussellbanners in eine vorhandene Schnellansichtsimplementierung auf Ihrer Website. Jede Schnellansichtsimplementierung ist einzigartig. Daher ist ein spezifischer Ansatz erforderlich, wofür höchstwahrscheinlich die Unterstützung eines Front-End-IT-Mitarbeiters nötig ist.

Die vorhandene Schnellansichtsimplementierung stellt normalerweise eine Kette von untereinander verknüpften Aktionen dar, die auf der Webseite in der folgenden Reihenfolge stattfinden:

1. Ein Benutzer löst ein Element auf der Benutzeroberfläche Ihrer Website aus.
1. Der Front-End-Code ruft anhand des in Schritt 1 ausgelösten Benutzeroberflächenelements eine Schnellansichts-URL auf.
1. Der Front-End-Code sendet mithilfe der in Schritt 2 abgerufenen URL eine Ajax-Anforderung.
1. Die Back-End-Logik gibt dem Front-End-Code die entsprechenden Schnellansichtsdaten oder -inhalte zurück.
1. Der Front-End-Code lädt die Schnellansichtsdaten oder -inhalte.
1. Optional wandelt der Front-End-Code die geladenen Schnellansichtsdaten in eine HTML-Darstellung um.
1. Der Front-End-Code zeigt ein modales Dialogfeld an und rendert den HTML-Inhalt auf dem Bildschirm für den Endbenutzer.

Diese Aufrufe stellen möglicherweise keine unabhängigen öffentlichen API-Aufrufe dar, die durch die Webseitenlogik in einem beliebigen Schritt aufgerufen werden können. Vielmehr handelt es sich um einen verketteten Aufruf, in dem der jeweils nächste Schritte in der letzten Phase (Callback) des vorherigen Schritts ausgeblendet ist.

Sobald das interaktive Karussellbanner Schritt 1 und teilweise Schritt 2 ersetzt, sofern ein Benutzer auf einen Hotspot oder eine Imagemap im Karussellbanner klickt, wird eine solche Benutzerinteraktion durch den Viewer verarbeitet. Der Viewer gibt ein Ereignis an die Webseite zurück, das die gesamten Hotspot- oder Imagemap-Daten enthält, die zuvor hinzugefügt wurden.

In einem solchen Ereignishandler nimmt der Front-End-Code Folgendes vor:

* Er lauscht am Ereignis, das durch das Karussellbanner ausgegeben wird.
* Er erstellt eine Schnellansichts-URL anhand der Hotspot- oder Imagemap-Daten.
* Er löst den Schnellansichts-Ladevorgang vom Back-End aus und rendert die Schnellansicht auf dem Bildschirm, um sie anzuzeigen.

Der von AEM Assets zurückgegebene Einbettungscode verfügt über einen einsatzbereiten Ereignishandler, der auskommentiert ist.

Daher ist es nur erforderlich, die Auskommentierung des Codes aufzuheben und den Platzhalter-Handlertext durch den Code zu ersetzen, der für die bestimmte Webseite spezifisch ist.

Der Prozess der Erstellung der Schnellansichts-URL ist im Prinzip das Gegenteil des Prozesses, der verwendet wird, um die zuvor erläuterten Hotspot-und Imagemap-Variablen zu ermitteln.

Siehe [Ermitteln von Hotspot- und Imagemap-Variablen](#identifying-hotspot-and-image-map-variables).

Der letzte Schritt besteht darin, die Schnellansichts-URL auszulösen, und für das Aktivieren des Schnellansichtsbereichs ist höchstwahrscheinlich die Unterstützung einer Front-End-IT-Person aus Ihrer IT-Abteilung erforderlich. Sie verfügt am ehesten über das entsprechende Fachwissen, um die Schnellansichtsimplementierung aus dem entsprechenden Schritt entsprechend auszulösen, um über eine einsatzbereite Schnellansichts-URL zu verfügen.

## Verwenden von Schnellansichten zum Erstellen von benutzerdefinierten Popups {#using-quickviews-to-create-custom-pop-ups}

Siehe [Popups mithilfe von benutzerspezifischen Schnellansichten erstellen](custom-pop-ups.md).
