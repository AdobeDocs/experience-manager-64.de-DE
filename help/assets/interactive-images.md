---
title: Interaktive Bilder
seo-title: Interaktive Bilder
description: Erfahren Sie, wie Sie mit interaktiven Bildern in dynamischen Medien arbeiten
seo-description: Erfahren Sie, wie Sie mit interaktiven Bildern in dynamischen Medien arbeiten
uuid: e8f79bc1-fccb-48d0-aca1-7f319c595fe9
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: d630499d-740d-4979-8a34-9e3fcc3b5a23
translation-type: tm+mt
source-git-commit: 43a28b0d9552cfde74850dfd1a1d63d04f7e4540

---


# Interaktive Bilder {#interactive-images}

Sie können statische Bilder ganz einfach ansprechende Erlebnisse für Kunden machen, indem Sie Hotspots auf ein Bild ziehen und dort ablegen. Shoppable-Hotspots kombinieren zusätzliche Informationen über ein Produkt oder eine Dienstleistung mit einer Direktverbindung, einem Point-of-Sale &quot;Hinzufügen in den Einkaufswagen&quot; oder der Funktion &quot;Kaufen&quot;. Kunden können auf diese Hotspots tippen und direkt mit dem Produkt oder Service verknüpft werden, sie einem Warenkorb hinzufügen oder mit einer Webseite verknüpft werden. Direkte Erlebnisse wie diese erhöhen das Kundenengagement und die Umrechnung auf Ihrer Website.

Die folgende Abbildung zeigt ein Banner mit Shopping-Funktion mit einem Schnellansichts-Popup. Benutzer können die Schnellansicht aktivieren, indem sie auf den Kreis oder „Hotspot“ des Modells tippen.

![chlimage_1-368](assets/chlimage_1-368.png)

Zeigen Sie die interaktiven Bilder in Aktion auf der oben gezeigten Webseite an, indem Sie Folgendes aufrufen:

[https://marketing.adobe.com/resources/help/de_DE/dm/shoppable-banner/we-fashion-QVzoom/index2-shoppable.html](https://marketing.adobe.com/resources/help/de_DE/dm/shoppable-banner/we-fashion-QVzoom/index2-shoppable.html)

## Schauen Sie sich an, wie interaktive Bildbanner erstellt werden {#watch-how-interactive-image-banners-are-created}

Hier erhalten Sie eine Einführung (10 Min., 33 Sek.) in die [Erstellung interaktiver Bildbanner](https://s7d5.scene7.com/s7viewers/html5/VideoViewer.html?videoserverurl=https://s7d5.scene7.com/is/content/&amp;emailurl=https://s7d5.scene7.com/s7/emailFriend&amp;serverUrl=https://s7d5.scene7.com/is/image/&amp;config=Scene7SharedAssets/Universal_HTML5_Video_social&amp;contenturl=https://s7d5.scene7.com/skins/&amp;asset=S7tutorials/InteractiveCarouselBanner). Außerdem erfahren Sie, wie Sie interaktive Bildbanner in der Vorschau betrachten, bearbeiten und bereitstellen können.

## Schnellstart: Interaktive Bilder {#quick-start-interactive-images}

Die folgende schrittweise Workflow-Beschreibung soll Ihnen den schnellen Einstieg in die Arbeit mit interaktiven Bildern in AEM Assets ermöglichen.

Suchen Sie nach der Überschrift **Beispiele** in einigen der Schnellstartaufgaben. Hier finden Sie ein kurzes Tutorial, das auf der folgenden Beispielwebseite basiert, der noch keine interaktiven Bilder hinzugefügt wurden:

[https://marketing.adobe.com/resources/help/de_DE/dm/shoppable-banner/we-fashion/landing-0.html](https://marketing.adobe.com/resources/help/de_DE/dm/shoppable-banner/we-fashion/landing-0.html)

Das Tutorial veranschaulicht die Schritte zur Integration von interaktiven Bildern auf Ihrer eigenen Website.

**Arbeitsablauf** für interaktive Bilder:

1. **(Optional) Ermitteln von Hotspot-Variablen**: Wenn Sie lediglich AEM Assets und Dynamic Media verwenden, ermitteln Sie zunächst die dynamischen Variablen, die in Ihrer vorhandenen Schnellansichtsimplementierung verwendet werden, damit Sie bei der Erstellung des interaktiven Bildes Hotspot-Daten eingeben können. Siehe [(Optional) Ermitteln von Hotspot-Variablen](#optional-identifying-hotspot-variables).

   Wenn Sie jedoch AEM Sites, AEM eCommerce oder beides verwenden, ist dieser Schritt nicht erforderlich.

   Siehe [eCommerce-Konzepte in AEM Assets](/help/sites-administering/concepts.md).

1. **(Optional) Erstellen einer Viewer-Vorgabe für interaktive Bilder**: Passen Sie das Grafikbild an, das zur Darstellung von Hotspots verwendet wird. Die Erstellung Ihrer eigenen Viewer-Vorgabe für interaktive Bilder ist nicht erforderlich, wenn Sie stattdessen die standardmäßig bereitgestellte Viewer-Vorgabe für interaktive Bilder namens `Shoppable_Banner` (Banner mit Shopping-Funktion) verwenden möchten.

   Siehe [(Optional) Erstellen einer Viewer-Vorgabe für interaktive Bilder](managing-viewer-presets.md#creating-a-new-viewer-preset).

1. **Hochladen eines Bildbanners** - Hochladen von Bildbannern, die interaktiv sein sollen.

   Siehe [Hochladen eines Bildbanners](#uploading-an-image-banner).

1. **Hinzufügen von Hotspots zu einem Bild-Banner** - Hinzufügen einem oder mehreren Hotspots zu einem Bild-Banner und Verknüpfen jedes dieser Hotspots mit einer Aktion wie einem Hyperlink, einer QuickView oder einem Erlebnisfragment. Nachdem Sie Hotspots hinzugefügt haben, schließen Sie diese Aufgabe ab, indem Sie das interaktive Bild veröffentlichen.

   * Siehe [Hinzufügen von Hotspots zu einem Bildbanner](#adding-hotspots-to-an-image-banner).
   *  Siehe [(Optional) Anzeigen einer Vorschau für interaktive Bilder](#optional-previewing-interactive-images). Bei Bedarf können Sie eine Darstellung des Banners mit Shopping-Funktion anzeigen und dessen Interaktivität testen.
   * Weitere Informationen zum Veröffentlichen von interaktiven Bild-Assets finden Sie unter [Veröffentlichen von Assets](publishing-dynamicmedia-assets.md).

1. **Hinzufügen eines interaktiven Bildes zu Ihrer Website oder zu Ihrer Website in AEM**

   * Wenn Sie AEM-Sites, AEM eCommerce oder beides verwenden, können Sie das interaktive Bild direkt zu einer Webseite in AEM hinzufügen, indem Sie die Komponente Interaktive Medien auf die Seite ziehen. Siehe [Hinzufügen von Assets mit dynamischen Medien zu Seiten](adding-dynamic-media-assets-to-pages.md). 
   * Wenn Sie lediglich AEM Assets und Dynamic Media verwenden, müssen Sie den Einbettungscode auf Ihrer Website kopieren und in Ihre vorhandene Schnellansicht integrieren. Siehe [Integrieren eines interaktiven Bildes auf Ihrer Website](#integrating-an-interactive-image-with-your-website).
   * Wenn Sie einen Drittanbieter-WCM (Web Content Manager) verwenden, müssen Sie das neue interaktive Video in die vorhandene Schnellansichtsimplementierung integrieren, die auf Ihrer Website verwendet wird. Siehe [Integrieren eines interaktiven Bildes in einer Schnellansicht](#integrating-an-interactive-image-with-an-existing-quickview).

## (Optional) Identifying hotspot variables {#optional-identifying-hotspot-variables}

>[!NOTE]
>
>Diese Aufgabe ist nur erforderlich, wenn Folgendes zutrifft:
>
>* Sie möchten das Bild durch Auslösen von Schnellansichten in ein interaktives Bild umwandeln.
>* Ihre AEM-Implementierung verwendet *kein* eCommerce-Integrations-Framework, um Produktdaten aus einer eCommerce-Lösung wie IBM Websphere Commerce, Elastic Path, hybris oder Intershop in AEM abzurufen. Siehe [eCommerce-Konzepte in AEM Assets](/help/sites-administering/concepts.md).
>
>
Wenn Ihre AEM-Implementierung eCommerce verwendet, können Sie diese Aufgabe überspringen und zur nächsten Aufgabe übergehen.

Ermitteln Sie zunächst die dynamischen Variablen, die von Ihrer vorhandenen Schnellansichtsimplementierung verwendet werden, damit Sie Hotspot-Daten eingeben können, um das interaktive Bild zu erstellen.

Wenn Sie Hotspots zu einem Bannerbild in AEM Assets hinzufügen, müssen Sie eine SKU (Stock Keeping Unit; Lagereinheit; einen eindeutigen Bezeichner für jedes einzelne Produkt oder jeden Dienst, das bzw. den Sie als Angebot verwenden, und optional zusätzliche Variablen für jeden Hotspot. Anhand dieser Hotspot-Variablen werden Hotspots später mit Schnellansichtsinhalten abgeglichen.

Sie müssen die Anzahl und den Typ der Variablen für die Verknüpfung mit Hotspot-Daten korrekt identifizieren. Jeder dem Bannerbild hinzugefügte Hotspot muss ausreichend Informationen enthalten, um das Produkt im vorhandenen Back-End-System eindeutig zu identifizieren.

Sie können ein Set aus Variablen für Hotspot-Daten auf mehrere Arten ermitteln.

Manchmal ist es ausreichend, IT-Experten zu konsultieren, die für die vorhandene Schnellansichtsimplementierung verantwortlich sind. Diese kennen wahrscheinlich den Mindestsatz an Daten, der zum Ermitteln der Schnellansicht im System erforderlich ist. In den meisten Fällen ist es jedoch auch möglich, einfach das vorhandene Verhalten des Front-End-Codes zu analysieren.

Die meisten Schnellansichtsimplementierungen verwenden das folgende Modell:

* Benutzer aktiviert ein Benutzeroberflächenelement auf der Website. For example, clicking a **[!UICONTROL Quickview]** button.
* Die Website sendet eine Ajax-Anforderung an das Back-End, um bei Bedarf die Schnellansichtsdaten oder -inhalte zu laden.
* Die Schnellansichtsdaten werden in den Inhalt übersetzt, um für das Rendern auf der Webseite vorbereitet zu werden.
* Schließlich zeigt der Front-End-Code diesen Inhalt visuell auf dem Bildschirm an.

Dann werden unterschiedliche Bereiche der vorhandenen Website besucht, auf denen die Schnellansichtsfunktion implementiert wird, die Schnellansicht wird ausgelöst und die Ajax-URL, die durch die Webseite zum Laden der Schnellansichtsdaten oder -inhalte gesendet wurde, wird erfasst.

Normalerweise müssen Sie keine speziellen Debugging-Tools verwenden. Moderne Webbrowser verfügen über Web-Inspektoren, die dafür ausreichend sind. Die folgenden Webbrowser beispielsweise umfassen Web-Inspektoren:

* To see all outgoing HTTP requests in Google Chrome, press F12 to open the **[!UICONTROL Developer Tools]** panel, and then click the **[!UICONTROL Network]** tab.

   On a Mac, press **[!UICONTROL Command+Option+I]** to open the **[!UICONTROL Developer Tools]** panel, then click the Network tab.

* In Firefox, you can either activate the Firebug plug-in by pressing F12 and use its Net tab, or you can use the built-in **[!UICONTROL Inspector]** tool and its **[!UICONTROL Network]** tab.

   On a Mac, press **[!UICONTROL Command+Option+I]** to open the **[!UICONTROL Developer Tools]** panel, then click the **[!UICONTROL Inspector]** tab.

Wenn die Netzwerküberwachung im Browser aktiviert ist, lösen Sie die Schnellansicht auf der Seite aus.

Suchen Sie nun die Schnellansichts-Ajax-URL im Netzwerkprotokoll und kopieren Sie die aufgezeichnete URL für die zukünftige Analyse. In den meisten Fällen werden beim Auslösen der Schnellansicht zahlreiche Anforderungen an den Server gesendet. In der Regel ist die Schnellansichts-Ajax-URL die erste URL in der Liste. It has either a complex query string portion or path, and its response MIME type is either `text/html`, `text/xml`, or `text/javascript`.

Während dieses Vorgangs müssen Sie verschiedene Bereiche der Website mit verschiedenen Produktkategorien und -typen besuchen. Grund dafür ist, dass Schnellansichts-URLs möglicherweise Teile aufweisen, die für eine bestimmte Website-Kategorie häufig vorkommen, sich aber nur ändern, wenn Sie einen anderen Bereich der Website besuchen.

Im einfachsten Fall ist der einzige variable Teil der Schnellansichts-URL die Produkt-SKU. In diesem Fall ist der SKU-Wert das einzige Datenteil, das Sie benötigen, um dem Bannerbild Hotspots hinzuzufügen.

In komplexen Fällen hat die Schnellansichts-URL allerdings mehrere verschiedene Elemente zusätzlich zur SKU, wie Kategorie-ID, Farbcode, Größencode usw. In diesen Fällen ist jedes Element eine separate Variable in der Hotspot-Datendefinition der Funktion für interaktive Bilder mit Shopping-Funktion in AEM Assets.

Im Folgenden finden Sie einige Beispiele für Schnellansichts-URLs und die resultierenden Hotspot-Variablen:

<table> 
     <tbody> 
      <tr> 
       <td><p>Einzelne SKU, befindet sich in der Abfragezeichenfolge.</p> </td> 
       <td><p>Die aufgezeichneten Schnellansichts-URLs enthalten Folgendes:</p> 
        <ul> 
         <li><p><code>https://server/json?productId=866558&amp;source=100</code></p> </li> 
         <li><p><code>https://server/json?productId=1196184&amp;source=100</code></p> </li> 
         <li><p><code>https://server/json?productId=1081492&amp;source=100</code></p> </li> 
         <li><p><code>https://server/json?productId=1898294&amp;source=100</code></p> </li> 
        </ul> <p>Der einzige variable Teil der URL ist der Wert des Abfrageparameters productId= und es ist offensichtlich ein SKU-Wert. Therefore, our hotspots only need SKU fields populated with values like <strong><code>866558</code></strong>, <strong><code>1196184</code></strong>, <strong><code>1081492</code></strong>, <strong><code>1898294</code></strong>.</p> </td> 
      </tr> 
      <tr> 
       <td><p>Einzelne SKU, befindet sich am URL-Pfad.</p> </td> 
       <td><p>Die aufgezeichneten Schnellansichts-URLs enthalten Folgendes:</p> 
        <ul> 
         <li><p><code>https://server/product/6422350843</code></p> </li> 
         <li><p><code>https://server/product/1607745002</code></p> </li> 
         <li><p><code>https://server/product/0086724882</code></p> </li> 
        </ul> <p>Der variable Teil befindet sich im letzten Abschnitt des Pfads und wird zum SKU-Wert der Hotspots: <strong><code>6422350843</code></strong>, <strong><code>1607745002</code></strong>, <strong><code>0086724882</code></strong>.</p> </td> 
      </tr> 
      <tr> 
       <td><p>SKU und Kategorie-ID in der Abfragezeichenfolge.</p> </td> 
       <td><p>Die aufgezeichneten Schnellansichts-URLs enthalten Folgendes:</p> 
        <ul> 
         <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=305466</code></p> </li> 
         <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=310181</code></p> </li> 
         <li><p><code>https://server/quickView/product/?category=1740148&amp;prodId=308706</code></p> </li> 
        </ul> <p>In diesem Fall liegen zwei abweichende Teile in der URL vor. Die SKU wird im <code>prodId</code> Parameter und in der Kategorien-ID gespeichert</p><p><code>categoryId</code></p><ul><li><p><code>305466</code><code>categoryId</code><code>1100004</code></p></li><li><p><code>310181</code><code>categoryId</code><code>1100004</code></p></li><li><p><code>308706</code><code>categoryId</code><code>1740148</code></p></li></ul><p></p></td></tr></tbody></table></td></tr><tr></tr></table>

**Beispiel**

Sie können den in den drei oben genannten Beispielen verwendeten Ansatz auch auf die Demo-Webseite anwenden:

[https://marketing.adobe.com/resources/help/de_DE/dm/shoppable-banner/we-fashion/landing-0.html](https://marketing.adobe.com/resources/help/de_DE/dm/shoppable-banner/we-fashion/landing-0.html)

The demo web page has several product thumbnails, each having a Quickview button labeled **[!UICONTROL See More]**. Klicken Sie bei aktiviertem Debugging-Tool des Webbrowsers auf jede Schaltfläche und notieren Sie sich die aufgezeichneten Schnellansichts-URLs. Nachdem Sie alle vier Produktschnellansichten auf der Seite aktiviert haben, verfügen Sie über die folgende Liste mit den an das Back-End gesendeten Schnellansichtsanforderungen:

* `/datafeed/Men-Windbreaker.json`
* `/datafeed/Men-SimpleHenley.json`
* `/datafeed/Men-CamoPullover.json`
* `/datafeed/Women-QuiltedDownJacket.json`

Wenn Sie diese Serveraufrufe betrachten, sehen Sie, dass nur der Anforderungspfad produktspezifische Informationen enthält. Beachten Sie außerdem, dass die Abfragezeichenfolge überhaupt nicht verwendet wird und zwei unterschiedliche Typen von Datenteilen beteiligt sind:

* Der erste Typ ist „Männer“ oder „Frauen“. Dies kann als „Produktkategorie“ bezeichnet werden.
* Der zweite Typ ist der Produktname, wie beispielsweise „CamoPullover“. Sie können davon ausgehen, dass dies die Produkt-SKU ist.

Mit diesen Informationen hat die gesamte Schnellansichts-URL das folgende Muster:

`/datafeed/$categoryId$-$SKU$.json`

Auf Grundlage einer solchen Analyse würden Sie `categoryId` und `SKU` für Hotspots verwenden.

Jetzt können Sie ein Bildbanner hochladen und diesem Hotspots mit der Funktion für interaktive Bilder mit Shopping-Funktion in AEM Assets hinzufügen.

## (Optional) Erstellen einer Viewer-Vorgabe für interaktive Bilder {#optional-creating-an-interactive-image-viewer-preset}

You can choose to use the default, out-of-the-box Interactive Image viewer preset called **[!UICONTROL Shoppable_Banner]** that comes with AEM Assets. Sie können auch eigene benutzerdefinierte Viewer-Vorgaben für die Verwendung mit interaktiven Bildern erstellen.

Wenn Sie eine benutzerdefinierte Viewer-Vorgabe für interaktive Bilder erstellen, können Sie das Aussehen von Hotspots auf dem Bild-Banner festlegen. Bei der Erstellung der Viewer-Vorgabe können Sie eine Hotspot-Grafik aus einer Galerie mit vordefinierten Bildern verwenden.

After you save the viewer preset, it is automatically activated (turned on) on the **[!UICONTROL Viewer Preset]** list page in AEM Assets. Diese Funktion bedeutet, dass sie in der Komponente Interaktive Medien und bei jeder Ansicht eines Assets sichtbar ist. However, to *deliver* an interactive banner with this viewer preset, you must *publish* your viewer preset as well (this is true for custom or out-of-box viewer presets).

**So erstellen Sie eine Viewer-Vorgabe für interaktive Bilder**:

1. Tippen Sie links in der Leiste auf **[!UICONTROL Tools > Assets > Viewer-Vorgaben]**.
1. Tippen Sie in der Nähe der rechten oberen Ecke der Seite auf **[!UICONTROL Erstellen]**.
1. In the **[!UICONTROL New Viewer Preset]** dialog box, type a name to describe the interactive banner viewer preset.

   This is the title that will appear in the **[!UICONTROL Viewer Preset]** list page after you save.
1. In the **[!UICONTROL Rich Media Type]** pull-down menu, select **[!UICONTROL Interactive Image]**.
1. Tippen Sie auf **Erstellen**.
1. On the **[!UICONTROL Edit Viewer Preset]** page, tap the **[!UICONTROL Appearance]** tab.
1. Führen Sie einen der folgenden Schritte aus:

   * To upload your own hotspot image that you want to use on images, tap the **[!UICONTROL Asset Picker]** icon. In the **[!UICONTROL Select Content]** page, navigate to the hotspot image you want to use, select it, and then tap the **[!UICONTROL Check Mark]** icon in the upper-right corner.
   * To select a predefined hotspot image, tap the **[!UICONTROL Hotspot Gallery]** icon. On the hotspot gallery pallette, tap the hotspot image you want to use.

1. Tippen Sie in der Nähe der oberen rechten Ecke auf **[!UICONTROL Speichern]**.

   Stellen Sie sicher, die neue Viewer-Vorgabe zu veröffentlichen.

   Informationen finden Sie unter [Veröffentlichen der von Ihnen hinzugefügten Viewer-Vorgaben](managing-viewer-presets.md#publishing-viewer-presets).

   Sie sind nun bereit, einen Bildbanner hochzuladen.

## Hochladen eines Bildbanners {#uploading-an-image-banner}

If you have already uploaded the images that you want to use, advance to the next step, [Adding hotspots to an image banner](#adding-hotspots-to-an-image-banner).

**So laden Sie einen Imagebanner hoch**:

1. Laden Sie Bildbanner hoch, die interaktiv sein sollen.

   Informationen hierzu finden Sie unter [Hochladen von Assets](managing-assets-touch-ui.md#uploading-assets).

   Sie können jetzt dem Bildbanner Hotspots hinzuzufügen. Anweisungen dazu finden Sie in der folgenden Aufgabe.

## Hinzufügen von Hotspots zu einem Bildbanner {#adding-hotspots-to-an-image-banner}

You can add hotspots to an image banner using the editor on the **[!UICONTROL Hotspot Management]** page.

Beim Hinzufügen von Hotspots können Sie sie als eine Schnellansichts-Popup-Anzeige, als einen Hyperlink oder als Experience Fragment definieren.

Weitere Informationen finden Sie unter [Experience Fragments](/help/sites-authoring/experience-fragments.md).

>[!NOTE]
>
>Beachten Sie, dass die Werkzeuge zum Freigeben von sozialen Medien in interaktiven Bildern nicht unterstützt werden, wenn Sie den Viewer in ein Erlebnisfragment einbetten. Um dies zu umgehen, können Sie Viewer-Vorgaben verwenden oder erstellen, für die keine Social Media-Sharing-Werkzeuge zur Verfügung stehen. Mit diesen Viewer-Vorgaben können Sie sie erfolgreich in Erlebnisfragmente einbetten.

**[!UICONTROL Die Optionen &quot;Rückgängig]** &quot;und &quot; **[!UICONTROL Wiederholen]** &quot;in der oberen rechten Ecke der Seite werden während der aktuellen Erstellungssitzung/Bearbeitungssitzung unterstützt.

When you finish creating your interactive image, you can use **[!UICONTROL Preview]** to see a representation of how your interactive image will appear to customers.

Siehe [(Optional) Anzeigen einer Vorschau für interaktive Bilder](#optional-previewing-interactive-images).

>[!NOTE]
>
>Wenn Sie Hotspots einem interaktiven Bild oder einem Bild für ein Karussellbanner hinzufügen, werden die Hotspot-Informationen immer am selben Metadatenspeicherort gespeichert, der relativ zum Speicherort des Bildes ist, unabhängig davon, ob es sich um ein interaktives Bild oder um ein Karussellbanner handelt. Das bedeutet, dass Sie dasselbe Bild zusammen mit den definierten Hotspot-Daten in beiden Viewern einfach wiederverwenden können.

>  Beachten Sie jedoch, dass Karussellbanner Imagemaps auf Bildern unterstützen, die auch Hotspots enthalten können. Bei interaktiven Bildern wird dies dagegen nicht unterstützt. Dies sollten Sie beachten, wenn Sie ein interaktives Bild oder ein Karussellbanner mit demselben Bild erstellen möchten. Stattdessen sollten Sie separate Kopien desselben Bildes verwenden, um interaktive Bilder und Karussellbilder zu erstellen.
>
>Weitere Informationen finden Sie unter [Karussellbanner](carousel-banners.md).

>[!NOTE]
>
>Wenn Sie interaktive Bilder mit Hotspots bearbeiten, um das Bild zu beschneiden, werden die Hotspots entfernt.

**So fügen Sie einem Bildbanner Hotspots hinzu**:

1. Navigieren Sie in der Ansicht „Assets“ zu dem Bildbanner, das interaktiv sein soll.
1. Führen Sie einen der folgenden Schritte aus:

   * Hover on the image, then tap **[!UICONTROL Select** (checkmark icon). On the toolbar, tap **[!UICONTROL Edit**.
   * Bewegen Sie den Mauszeiger über dem Bild und tippen Sie dann auf **[!UICONTROL Mehr Aktionen]** (Ellipsensymbol) > **[!UICONTROL Bearbeiten]**.
   * Tap the image to open it in the **[!UICONTROL Detail View]** page. On the toolbar, tap **[!UICONTROL Edit**.

1. Near the upper-left corner of the page, tap **[!UICONTROL Add Hotspot]** (finger tap icon) to open the **[!UICONTROL Hotspot Management]** page.
1. Tippen Sie in der Nähe der rechten oberen Ecke der Seite auf **[!UICONTROL Hotspot]**.
1. a. Near the upper-left corner of the **Hotspot Management** page, tap **[!UICONTROL Hotspot]**.
b. Tippen Sie im Bild auf eine Stelle, an der der Hotspot angezeigt werden soll. Ziehen Sie bei Bedarf den Hotspot, um seine Position anzupassen.
c. Hinzufügen Sie nach Bedarf weitere Hotspots, indem Sie die Schritte a und b wiederholen.
d. (Optional) Um einen Hotspot zu löschen, wählen Sie ihn im Bild aus und tippen Sie dann unter der Überschrift &quot; **[!UICONTROL Hotspots]** &quot;auf &quot; **[!UICONTROL Löschen]** &quot;(das Symbol &quot;Müll kann&quot;).

1. In the **[!UICONTROL Name]** text field, type the name of the hotspot. This name also appears in the **[!UICONTROL Selected Hotspot]** drop-down list.
1. Führen Sie einen der folgenden Schritte aus:

   * Tippen Sie auf **[!UICONTROL Schnellansicht]**.

      * If you are an AEM Sites or eCommerce customer, tap the **[!UICONTROL Product Picker]** icon (magnifying glass) to open the **[!UICONTROL Select Product]** page. Tap the product you want to use, then tap **[!UICONTROL Select]** in the upper-right corner of the page to return to the **[!UICONTROL Hotspot Management]** page.
      * If you are *not* an AEM Sites or eCommerce customer

         * See [Identifying hotspot variables](#optional-identifying-hotspot-variables); you will need to define these variables.
         * Geben Sie dann manuell den SKU-Wert ein. In the **[!UICONTROL SKU Value]** text field, type the product&#39;s SKU (Stock Keeping Unit), which is a unique identifier for each distinct product or service that you offer. Der eingegebene SKU-Wert füllt automatisch den variablen Teil der QuickView-Vorlage, damit das System den getippten Hotspot mit der QuickView einer bestimmten SKU verknüpfen kann.
         * (Optional) If there are other variables within the Quickview that you need to use to further identify a product, tap **[!UICONTROL Add Generic Variable]**. Geben Sie im Textfeld eine zusätzliche Variable an. Beispielsweise ist `category=Mens` eine hinzugefügte Variable.
   * Tippen Sie auf **Hyperlink**.

      * If you are an AEM Sites customer, tap the **[!UICONTROL Site Selector]** icon (folder) to navigate to a URL. Beachten Sie, dass die URL-basierte Verlinkungsmethode nicht möglich ist, wenn Ihr interaktiver Inhalt über Links mit relativen URLs verfügt, insbesondere über Links zu Seiten in AEM Sites.
      * If you are a standalone customer, in the **[!UICONTROL HREF]** text field, specify the full URL path to a linked web page.
      Vergessen Sie nicht anzugeben, ob der Link auf einer neuen Browser-Registerkarte (empfohlener Standard) oder auf derselben Registerkarte geöffnet werden soll.

      Weitere Informationen finden Sie unter [Arbeiten mit Selektoren](working-with-selectors.md).

   * Tippen Sie auf **Experience Fragment**.

      * If you are an AEM Sites customer, tap the **[!UICONTROL Search]** icon (magnifying glass) to open the **[!UICONTROL Experience Fragment]** page. Tap the Experience Fragment you want to use, then tap **[!UICONTROL Select]** in the upper-right corner of the page to return to the Hotspot management page.

         Weitere Informationen finden Sie unter [Experience Fragments](/help/sites-authoring/experience-fragments.md).
         >[!NOTE]
         >Beachten Sie, dass die Werkzeuge zum Freigeben von sozialen Medien in interaktiven Bildern nicht unterstützt werden, wenn Sie den Viewer in ein Erlebnisfragment einbetten. Um dies zu umgehen, können Sie Viewer-Vorgaben verwenden oder erstellen, für die keine Social Media-Sharing-Werkzeuge zur Verfügung stehen. Mit diesen Viewer-Vorgaben können Sie sie erfolgreich in Erlebnisfragmente einbetten.

      * Legen Sie die Breite und Höhe des Experience Fragments fest, so wie es im Banner angezeigt werden soll.



1. Tippen Sie auf **[!UICONTROL Speichern]**, um Ihre Änderungen zu speichern, und kehren Sie zur Seite „Durchsuchen“ zurück.****
1. Veröffentlichen Sie das interaktive Bild. Durch eine Veröffentlichung kann das Banner über die Cloud bereitgestellt werden. Außerdem wird ein Einbettungscode zur Integration auf der Website von Dritten generiert. 

   Informationen hierzu finden Sie unter [Veröffentlichen von Assets](managing-assets-touch-ui.md#publishing-assets).

   Nachdem Sie Hotspots hinzugefügt und das interaktive Bild veröffentlicht haben, können Sie es jetzt einer vorhandenen Website hinzufügen.

   Siehe [Integrieren eines interaktiven Bildes auf Ihrer Website](#integrating-an-interactive-image-with-your-website).

   >[!NOTE]
   >
   >Wenn Sie interaktive Bilder mit Hotspots bearbeiten, um das Bild zu beschneiden, werden die Hotspots entfernt.

### (Optional) Anzeigen einer Vorschau für interaktive Bilder {#optional-previewing-interactive-images}

Sie können Vorschau verwenden, um eine Darstellung des Erscheinungsbilds Ihres interaktiven Bilds anzuzeigen und die Hotspots des Bildes zu testen, um sicherzustellen, dass sie sich wie erwartet verhalten.

Wenn das interaktive Bild Ihren Vorstellungen entspricht, können Sie es veröffentlichen.\
Siehe [Einbetten des Video- oder Bild-Viewers auf einer Webseite](embed-code.md).\
Siehe [Verknüpfen von URLs mit einer Webanwendung.](linking-urls-to-yourwebapplication.md). Beachten Sie, dass die URL-basierte Verlinkungsmethode nicht möglich ist, wenn Ihr interaktiver Inhalt über Links mit relativen URLs verfügt, insbesondere über Links zu Seiten in AEM Sites.\
See [Adding Dynamic Media Assets to Pages.](adding-dynamic-media-assets-to-pages.md)

**So zeigen Sie eine Vorschau für interaktive Bilder an**:

1. Navigieren Sie in der Ansicht „Assets“ zu einem vorhandenen interaktiven Bild, das Sie erstellt haben, um es in der Vorschau zu öffnen.
1. Near the upper-left corner of the Preview page, in the **[!UICONTROL Content]** drop-down list, tap **[!UICONTROL Viewers]**.
1. In the **[!UICONTROL Viewers]** list, tap **[!UICONTROL Shoppable_Banner]** or the name of the interactive image viewer preset you have created.
1. Tippen Sie auf Hotspots auf dem Bild, um die zugehörigen Aktionen zu testen.

## Veröffentlichen von interaktiven Bild-Assets {#publishing-interactive-image-assets}

Weitere Informationen zum Veröffentlichen von interaktiven Bild-Assets finden Sie unter [Veröffentlichen von Assets](publishing-dynamicmedia-assets.md).

## Integrieren eines interaktiven Bildes auf Ihrer Website {#integrating-an-interactive-image-with-your-website}

Nachdem Sie ein Bannerbild hochgeladen, Hotspots hinzugefügt und das interaktive Bild veröffentlicht haben, können Sie es jetzt auf Ihrer Webseite hinzufügen.

Wenn Sie AEM Sites-Kunde sind, können Sie das interaktive Bild hinzufügen, indem Sie die interaktive Medienkomponente auf Ihre Seite ziehen. See [Adding Dynamic Media Assets to Pages.](adding-dynamic-media-assets-to-pages.md)

Wenn Sie ein nur AEM Assets verwenden, können Sie das interaktive Bild Ihrer Website manuell hinzufügen, wie in diesem Abschnitt beschrieben.

1. Kopieren Sie den Einbettungscode des veröffentlichten interaktiven Bildes.

   Siehe [Einbetten des Video- oder Bild-Viewers auf einer Webseite](embed-code.md).

1. Fügen Sie den kopierten Einbettungscode auf dem gewünschten Bereich innerhalb der Webseite hinzu.

   Der kopierte Einbettungscode ist für eine responsive Umgebung ausgelegt, sodass die Anpassung an den zugewiesenen Bereich automatisch erfolgen sollte.

**Beispiel**

Verwenden der Demowebsite als ein Beispiel:

[https://marketing.adobe.com/resources/help/de_DE/dm/shoppable-banner/we-fashion/landing-0.html](https://marketing.adobe.com/resources/help/de_DE/dm/shoppable-banner/we-fashion/landing-0.html)

Beachten Sie, dass es sich beim Bild der drei Männer um ein statisches `IMG`-Tag handelt:

```xml
<img class="img-responsive" width="100%" title="Hero Image 2" alt="Hero Image 2" src="images/shoppable-banner.jpg">
```

Die Integration ist so einfach wie das Entfernen des `IMG`-Tags und dessen entsprechende Ersetzung durch den kopierten Integrationscode aus AEM Assets. Sie können das Ergebnis in der folgenden URL anzeigen, die ein interaktives Bild mit Shopping-Funktion auf der Seite mit drei Kreis-Hotspots anzeigt:

[https://marketing.adobe.com/resources/help/de_DE/dm/shoppable-banner/we-fashion/landing-1.html](https://marketing.adobe.com/resources/help/de_DE/dm/shoppable-banner/we-fashion/landing-1.html)

>[!NOTE]
>
>Zurzeit dienen die Hotspots auf dem interaktiven Bild mit Shopping-Funktion auf der Demowebsite nur zu Anzeigezwecken. Sie sind zurzeit noch nicht in den Schnellansicht integriert.

To apply a crop to a shoppable interactive image for a responsive environment, you can include the Interactive Image configuration attribute `ZoomView.iscommand` to the path—where `ZoomView` is the component to call and `iscommand` is the crop image serving command that you apply.

Informationen hierzu finden Sie im Thema über das Konfigurationsattribut [ZoomView.iscommand](https://marketing.adobe.com/resources/help/de_DE/s7/viewers_ref/r_html5_aem_interactive_image_config_attrib_zoomview_iscommand.html).

Informationen finden Sie unter [Image-Serving-Befehl](https://marketing.adobe.com/resources/help/de_DE/s7/is_ir_api/is_api/http_ref/r_crop.html).

Jetzt können Sie das interaktive Bild in eine vorhandene Schnellansicht auf Ihrer Website integrieren.

## Integrieren eines interaktiven Bildes in einer Schnellansicht {#integrating-an-interactive-image-with-an-existing-quickview}

>[!NOTE]
>
>Diese Aufgabe ist nur relevant, wenn Sie die Standalone-Version von AEM Assets verwenden.

Der letzte Schritt in diesem Prozess ist die Integration des interaktiven Bildes in eine vorhandene Schnellansichtsimplementierung auf Ihrer Website. Es gibt keine Lösung für die Integration, die für alle Fälle funktioniert. Jede Schnellansichtsimplementierung ist einzigartig. Daher ist ein spezifischer Ansatz erforderlich, wofür höchstwahrscheinlich die Unterstützung eines Front-End-IT-Mitarbeiters nötig ist.

Die vorhandene Schnellansichtsimplementierung stellt normalerweise eine Kette von untereinander verknüpften Aktionen dar, die auf der Webseite in der folgenden Reihenfolge stattfinden:

1. Ein Benutzer löst ein Element auf der Benutzeroberfläche Ihrer Website aus.
1. Der Front-End-Code ruft anhand des in Schritt 1 ausgelösten Benutzeroberflächenelements eine Schnellansichts-URL auf.
1. Der Front-End-Code sendet mithilfe der in Schritt 2 abgerufenen URL eine Ajax-Anforderung.
1. Die Back-End-Logik gibt dem Front-End-Code die entsprechenden Schnellansichtsdaten oder -inhalte zurück.
1. Der Front-End-Code lädt die Schnellansichtsdaten oder -inhalte.
1. Optional wandelt der Front-End-Code die geladenen Schnellansichtsdaten in eine HTML-Darstellung um.
1. Der Front-End-Code zeigt ein modales Dialogfeld an und rendert den HTML-Inhalt auf dem Bildschirm für den Endbenutzer.

Diese Aufrufe stellen möglicherweise keine unabhängigen öffentlichen API-Aufrufe dar, die durch die Webseitenlogik in einem beliebigen Schritt aufgerufen werden können. Vielmehr handelt es sich um einen verketteten Aufruf, in dem der jeweils nächste Schritte in der letzten Phase (Callback) des vorherigen Schritts ausgeblendet ist.

Gleichzeitig, wenn das interaktive Bild mit Shopping-Funktion Schritt 1 und teilweise Schritt 2 ersetzt, sofern ein Benutzer auf einen Hotspot auf dem Bild mit Shopping-Funktion klickt, wird eine derartige Benutzerinteraktion durch den Viewer verarbeitet. Der Viewer gibt der Webseite ein Ereignis zurück, das alle zuvor zu AEM Assets hinzugefügten Hotspot-Daten aufweist.

In einem solchen Ereignishandler nimmt der Front-End-Code Folgendes vor:

* Er lauscht am Ereignis, das durch das interaktive Bild mit Shopping-Funktion ausgegeben wurde.
* Er erstellt anhand der Hotspot-Daten eine Schnellansichts-URL.
* Er löst den Schnellansichts-Ladevorgang vom Back-End aus und rendert die Schnellansicht auf dem Bildschirm, um sie anzuzeigen.

Der von AEM Assets zurückgegebene Einbettungscode verfügt über einen einsatzbereiten Ereignishandler, der auskommentiert ist, wie im folgenden hervorgehobenen Codefragment zu sehen ist:

```xml
        var s7interactiveimageviewer = new s7viewers.InteractiveImage({
            "containerId" : "s7interactiveimage_div",
            "params" : { 
                "serverurl" : "https://aodmarketingna.assetsadobe.com/is/image",
                "contenturl" : "https://aodmarketingna.assetsadobe.com/", 
                "config" : "/etc/dam/presets/viewer/Shoppable_Media",
                "asset" : "/content/dam/mac/aodmarketingna/shoppable-banner/shoppable-banner.jpg" }
        })
        /* // Example of interactive image event for Quickview.
             s7interactiveimageviewer.setHandlers({ 
                "quickViewActivate": function(inData) {
                    var sku=inData.sku; //SKU for product ID
                    //To pass other parameter from the hotspot, you will need to add custom parameter during the hotspot setup as parameterName=value
                    loadQuickView(sku); //Replace this call with your Quickview plugin
                    //Please refer to your Quickviewer plugin for the Quickview call
                 }, 
             });
        */
        s7interactiveimageviewer.init();
```

Daher ist es nur erforderlich, die Auskommentierung des Codes aufzuheben und den Platzhalter-Handlertext durch den Code zu ersetzen, der für die bestimmte Webseite spezifisch ist.

Der Prozess der Erstellung der Schnellansichts-URL ist im Prinzip das Gegenteil des Prozesses, der verwendet wird, um die zuvor erläuterten Hotspot-Variablen zu ermitteln.

Informationen hierzu finden Sie unter [Ermitteln von Hotspot-Variablen](#optional-identifying-hotspot-variables).

Unter Verwendung der vorherigen Schnellansichts-URL-Beispiele können Sie in den folgenden Beispielen sehen, wie die Schnellansichts-URL in jedem Fall erstellt wird:

<table> 
 <tbody> 
  <tr> 
   <td><p>Einzelne SKU, befindet sich in der Abfragezeichenfolge.</p> </td> 
   <td><code class="code">s7interactiveimageviewer.setHandlers({
      "quickViewActivate": function(inData) {
      var quickViewUrl = "https://server/json?productId=" + inData.sku + "&amp;amp;source=100";
      },
      });</code></td> 
  </tr> 
  <tr> 
   <td><p>Einzelne SKU, befindet sich am URL-Pfad.</p> </td> 
   <td><code class="code">s7interactiveimageviewer.setHandlers({
      "quickViewActivate": function(inData) {
      var quickViewUrl = "https://server/product/" + inData.sku;
      },
      });</code></td> 
  </tr> 
  <tr> 
   <td><p>SKU und Kategorie-ID in der Abfragezeichenfolge.</p> </td> 
   <td><code class="code">s7interactiveimageviewer.setHandlers({
      "quickViewActivate": function(inData) {
      var quickViewUrl = "https://server/quickView/product/?category=" + inData.categoryId + "&amp;amp;prodId=" + inData.sku;
      },
      });</code></td> 
  </tr> 
 </tbody> 
</table>

Der letzte Schritt besteht darin, die Schnellansichts-URL auszulösen, und für das Aktivieren des Schnellansichtsbereichs ist höchstwahrscheinlich die Unterstützung eines Front-End-IT-Mitarbeiters aus Ihrer IT-Abteilung erforderlich. Er verfügt am ehesten über das entsprechende Fachwissen, um die Schnellansichtsimplementierung aus dem entsprechenden Schritt entsprechend auszulösen, um über eine einsatzbereite Schnellansichts-URL zu verfügen.

Sie können sehen, wie diese Schritte auf die Demo-Website angewendet werden, sodass ein interaktives Bild mit Shopping-Funktion mit dem Schnellansichtscode voll integriert wird. Die Struktur der Schnellansichts-URL wurde bereits wie folgt ermittelt:

```xml
/datafeed/$categoryId$-$SKU$.json
```

Um diese URL innerhalb der Handlers `quickViewActivate` zu rekonstruieren, können Sie die Felder `categoryId` und `SKU` verwenden, die im Objekt `inData` verfügbar sind, das durch den Code des Viewers an den Handler übergeben wird:

```xml
var sku=inData.sku;
var categoryId=inData.categoryId;
var quickViewUrl = "datafeed/" + categoryId + "-" + sku + ".json";
```

The demo website is triggering the Quickview dialog box using a simple `loadQuickView()` function call. Diese Funktion akzeptiert als einziges Argument die Schnellansichtsdaten-URL. Der letzte Schritt bei der Integration des interaktiven Bildes mit Shopping-Funktion besteht darin, die folgende Codezeile dem `quickViewActivate`-Handler hinzuzufügen:

```xml
loadQuickView(quickViewUrl);
```

Im Folgenden finden Sie den vollständigen Quellcode:

```xml
 var s7interactiveimageviewer = new s7viewers.InteractiveImage({
  "containerId" : "s7interactiveimage_div",
  "params" : { 
   "serverurl" : "https://aodmarketingna.assetsadobe.com/is/image",
   "contenturl" : "https://aodmarketingna.assetsadobe.com/", 
   "config" : "/etc/dam/presets/viewer/Shoppable_Media",
   "asset" : "/content/dam/mac/aodmarketingna/shoppable-banner/shoppable-banner.jpg" }
 })
   s7interactiveimageviewer.setHandlers({ 
   "quickViewActivate": function(inData) {
     var sku=inData.sku;
     var categoryId=inData.categoryId;
    var quickViewUrl = "datafeed/" + categoryId + "-" + sku + ".json";
    loadQuickView(quickViewUrl);
    }, 
   });
 s7interactiveimageviewer.init();
```

Die endgültige Demowebsite mit dem vollständig integrierten interaktiven Bild hat folgendes Aussehen:

[https://marketing.adobe.com/resources/help/de_DE/dm/shoppable-banner/we-fashion/landing-3.html](https://marketing.adobe.com/resources/help/de_DE/dm/shoppable-banner/we-fashion/landing-3.html)

## Verwenden von Schnellansichten zum Erstellen von benutzerdefinierten Popups {#using-quickviews-to-create-custom-pop-ups}

Siehe [Popups mithilfe von benutzerspezifischen Schnellansichten erstellen](custom-pop-ups.md).
