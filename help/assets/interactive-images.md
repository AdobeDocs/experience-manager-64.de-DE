---
title: Interaktive Bilder
seo-title: Interactive Images
description: Erfahren Sie, wie Sie mit interaktiven Bildern in dynamischen Medien arbeiten.
seo-description: Learn how to work with interactive images in dynamic media
uuid: e8f79bc1-fccb-48d0-aca1-7f319c595fe9
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: d630499d-740d-4979-8a34-9e3fcc3b5a23
exl-id: 4d3299e2-269b-4a41-a979-c884c707666d
feature: Interactive Images
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '4283'
ht-degree: 64%

---

# Interaktive Bilder {#interactive-images}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Sie können aus statischen Bildern ganz einfach ansprechende Erlebnisse für Kunden machen, indem Sie Hotspots mit Shopping-Funktion auf ein Bild ziehen und dort ablegen. Hotspots mit Shopping-Funktion kombinieren zusätzliche Informationen über ein Produkt oder eine Dienstleistung mit einer direkten POS-Funktion, wie „In den Einkaufswagen legen“ oder „Kaufen“. Kunden können auf diese Hotspots tippen und direkt mit dem Produkt oder Service verknüpft werden, sie zu einem Warenkorb hinzufügen oder mit einer Webseite verknüpft werden. Direkte Erlebnisse wie diese erhöhen die Kundeninteraktion und die Konversion auf Ihrer Website.

Die folgende Abbildung zeigt ein Banner mit Shopping-Funktion mit einem Schnellansichts-Popup. Benutzer können die Schnellansicht aktivieren, indem sie auf den Kreis oder „Hotspot“ des Modells tippen.

![chlimage_1-368](assets/chlimage_1-368.png)

Zeigen Sie die interaktiven Bilder in Aktion auf der oben gezeigten Webseite an, indem Sie Folgendes aufrufen:

[https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion-QVzoom/index2-shoppable.html?lang=de](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion-QVzoom/index2-shoppable.html?lang=de)

## Sehen Sie sich an, wie interaktive Bildbanner erstellt werden {#watch-how-interactive-image-banners-are-created}

Hier erhalten Sie eine Einführung (10 Min., 33 Sek.) in die [Erstellung interaktiver Bild-Banner](https://s7d5.scene7.com/s7viewers/html5/VideoViewer.html?videoserverurl=https://s7d5.scene7.com/is/content/&amp;emailurl=https://s7d5.scene7.com/s7/emailFriend&amp;serverUrl=https://s7d5.scene7.com/is/image/&amp;config=Scene7SharedAssets/Universal_HTML5_Video_social&amp;contenturl=https://s7d5.scene7.com/skins/&amp;asset=S7tutorials/InteractiveCarouselBanner). Außerdem erfahren Sie, wie Sie interaktive Bildbanner in der Vorschau anzeigen, bearbeiten und bereitstellen.

## Schnellstart: Interaktive Bilder {#quick-start-interactive-images}

Die folgende schrittweise Workflow-Beschreibung soll Ihnen dabei helfen, interaktive Bilder in AEM Assets einzurichten und schnell auszuführen.

Suchen Sie nach der Überschrift **Beispiele** in einigen der Schnellstartaufgaben. Es enthält ein kurzes Tutorial, das auf dem folgenden Webseitenbeispiel basiert, dem noch keine interaktiven Bilder hinzugefügt wurden:

[https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html?lang=de](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html?lang=de)

Das Tutorial veranschaulicht die Schritte zur Integration interaktiver Bilder auf Ihrer eigenen Website.

**Workflow für interaktive Bilder**:

1. **(Optional) Ermitteln von Hotspot-Variablen** - Wenn Sie AEM Assets und Dynamic Media eigenständig verwenden, ermitteln Sie zunächst die dynamischen Variablen, die in Ihrer vorhandenen Schnellansichtsimplementierung verwendet werden, damit Sie beim Erstellen des interaktiven Bildes Hotspot-Daten eingeben können. Siehe [(Optional) Ermitteln von Hotspot-Variablen](#optional-identifying-hotspot-variables).

   Wenn Sie jedoch AEM Sites, AEM eCommerce oder beides verwenden, ist dieser Schritt nicht erforderlich.

   Siehe [eCommerce-Konzepte in AEM Assets](/help/sites-administering/concepts.md).

1. **(Optional) Erstellen einer Viewer-Vorgabe für interaktive Bilder** - Passen Sie das Grafikbild an, das zur Darstellung von Hotspots verwendet wird. Die Erstellung Ihrer eigenen Viewer-Vorgabe für interaktive Bilder ist nicht erforderlich, wenn Sie stattdessen die standardmäßig bereitgestellte Viewer-Vorgabe für interaktive Bilder namens `Shoppable_Banner` (Banner mit Shopping-Funktion) verwenden möchten.

   Siehe [(Optional) Erstellen einer Viewer-Vorgabe für interaktive Bilder](managing-viewer-presets.md#creating-a-new-viewer-preset).

1. **Hochladen eines Bildbanners** - Laden Sie Bildbanner hoch, die interaktiv sein sollen.

   Siehe [Hochladen eines Bildbanners](#uploading-an-image-banner).

1. **Hinzufügen von Hotspots zu einem Bildbanner** - Fügen Sie einem Bildbanner einen oder mehrere Hotspots hinzu und weisen Sie jedem eine Aktion wie einen Hyperlink, eine Schnellansicht oder ein Experience Fragment zu. Nachdem Sie Hotspots hinzugefügt haben, schließen Sie diese Aufgabe ab, indem Sie das interaktive Bild veröffentlichen.

   * Siehe [Hinzufügen von Hotspots zu einem Bildbanner](#adding-hotspots-to-an-image-banner).
   * Siehe [(Optional) Anzeigen einer Vorschau für interaktive Bilder](#optional-previewing-interactive-images). Bei Bedarf können Sie eine Darstellung des Banners mit Shopping-Funktion anzeigen und dessen Interaktivität testen.
   * Weitere Informationen zum Veröffentlichen von interaktiven Bild-Assets finden Sie unter [Veröffentlichen von Assets](publishing-dynamicmedia-assets.md).

1. **Hinzufügen eines interaktiven Bildes zu Ihrer Website oder zu Ihrer Website in AEM**

   * Wenn Sie AEM Sites, AEM eCommerce oder beides verwenden, können Sie das interaktive Bild direkt zu einer Web-Seite in AEM hinzufügen, indem Sie die interaktive Medienkomponente auf die Seite ziehen. Siehe [Hinzufügen von Dynamic Media-Assets zu Seiten](adding-dynamic-media-assets-to-pages.md).
   * .
Wenn Sie lediglich AEM Assets und Dynamic Media verwenden, müssen Sie den Einbettungs-Code auf Ihrer Website kopieren und in Ihre vorhandene Schnellansicht integrieren. Siehe [Integrieren eines interaktiven Bildes auf Ihrer Website](#integrating-an-interactive-image-with-your-website).
   * Wenn Sie einen Drittanbieter-WCM (Web Content Manager) verwenden, müssen Sie das neue interaktive Video in die vorhandene Schnellansichtsimplementierung integrieren, die auf Ihrer Website verwendet wird. Siehe [Integrieren eines interaktiven Bildes in einer Schnellansicht](#integrating-an-interactive-image-with-an-existing-quickview).

## (Optional) Ermitteln von Hotspot-Variablen {#optional-identifying-hotspot-variables}

>[!NOTE]
>
>Diese Aufgabe ist nur erforderlich, wenn Folgendes zutrifft:
>
>* Sie möchten dem Bild Interaktivität hinzufügen, indem Sie Schnellansichten aktivieren.
>* Ihre AEM-Implementierung verwendet *kein* E-Commerce-Integrations-Framework, um Produktdaten aus einer E-Commerce-Lösung wie IBM Websphere Commerce, Elastic Path, hybris oder Intershop in AEM abzurufen. Siehe [eCommerce-Konzepte in AEM Assets](/help/sites-administering/concepts.md).
>
>Wenn Ihre AEM-Implementierung eCommerce nutzt, können Sie diese Aufgabe überspringen und mit der nächsten Aufgabe fortfahren.

Ermitteln Sie zunächst die dynamischen Variablen, die von Ihrer vorhandenen Schnellansichtsimplementierung verwendet werden, damit Sie Hotspot-Daten eingeben können, um das interaktive Bild zu erstellen.

Wenn Sie einem Bannerbild in AEM Assets Hotspots hinzufügen, müssen Sie eine SKU (Stock Keeping Unit: eindeutiger Bezeichner für die jeweiligen von Ihnen angebotenen Produkte oder Services) und optionale zusätzliche Variablen für jeden Hotspot zuweisen. Diese Hotspot-Variablen werden später verwendet, um Hotspots mit Schnellansichtsinhalten abzugleichen.

Es ist wichtig, die Anzahl und den Typ der Variablen, die mit Hotspot-Daten verknüpft werden sollen, ordnungsgemäß zu identifizieren. Jeder dem Bannerbild hinzugefügte Hotspot muss ausreichend Informationen enthalten, um das Produkt im vorhandenen Backend-System eindeutig zu identifizieren.

Sie können ein Set aus Variablen für Hotspot-Daten auf mehrere Arten ermitteln.

Manchmal ist es ausreichend, IT-Experten zu konsultieren, die für die vorhandene Schnellansichtsimplementierung verantwortlich sind. Diese kennen wahrscheinlich den Mindestsatz an Daten, der zum Ermitteln der Schnellansicht im System erforderlich ist. In den meisten Fällen ist es jedoch auch möglich, einfach das vorhandene Verhalten des Frontend-Codes zu analysieren.

Die meisten Schnellansichtsimplementierungen verwenden das folgende Paradigma:

* Benutzer aktiviert ein Benutzeroberflächenelement auf der Website. Beispiel: Klicken auf eine **[!UICONTROL Schnellansicht]** Schaltfläche.
* Die Website sendet eine Ajax-Anfrage an das Backend, um bei Bedarf die Schnellansichtsdaten oder -inhalte zu laden.
* Die Schnellansichtsdaten werden in den Inhalt übersetzt, um für das Rendern auf der Web-Seite vorbereitet zu werden.
* Schließlich zeigt der Frontend-Code diesen Inhalt visuell auf dem Bildschirm an.

Dann werden unterschiedliche Bereiche der vorhandenen Website besucht, auf denen die Schnellansichtsfunktion implementiert wird, die Schnellansicht wird ausgelöst und die Ajax-URL, die durch die Web-Seite zum Laden der Schnellansichtsdaten oder -inhalte gesendet wurde, wird erfasst.

Normalerweise müssen Sie keine speziellen Debugging-Tools verwenden. Moderne Webbrowser verfügen über Web-Inspektoren, die dafür ausreichend sind. Im Folgenden finden Sie einige Beispiele für Webbrowser, die Web-Inspektoren beinhalten:

* Drücken Sie F12, um alle ausgehenden HTTP-Anfragen in Google Chrome zu öffnen. **[!UICONTROL Entwicklertools]** und klicken Sie dann auf **[!UICONTROL Netzwerk]** Registerkarte.

   Drücken Sie auf einer Mac die **[!UICONTROL Befehl+Option+I]** , um **[!UICONTROL Entwicklertools]** und klicken Sie auf die Registerkarte &quot;Netzwerk&quot;.

* In Firefox können Sie entweder das Firebug-Plug-in aktivieren, indem Sie F12 drücken und die Registerkarte Netz verwenden, oder Sie können die integrierte **[!UICONTROL Inspektor]** -Tool und **[!UICONTROL Netzwerk]** Registerkarte.

   Drücken Sie auf einer Mac die **[!UICONTROL Befehl+Option+I]** , um **[!UICONTROL Entwicklertools]** und klicken Sie auf das **[!UICONTROL Inspektor]** Registerkarte.

Wenn die Netzwerküberwachung im Browser aktiviert ist, lösen Sie die Schnellansicht auf der Seite aus.

Suchen Sie nun die Schnellansichts-Ajax-URL im Netzwerkprotokoll und kopieren Sie die aufgezeichnete URL für die zukünftige Analyse. In den meisten Fällen werden beim Auslösen der Schnellansicht zahlreiche Anfragen an den Server gesendet. In der Regel ist die Schnellansichts-Ajax-URL die erste URL in der Liste. Sie weist einen Teil oder Pfad mit einer komplexen Abfragezeichenfolge auf und ihr MIME-Typ lautet entweder `text/xml`, `text/html` oder `text/javascript`.

Während dieses Prozesses ist es wichtig, verschiedene Bereiche Ihrer Website mit verschiedenen Produktkategorien und -typen zu besuchen. Der Grund dafür ist, dass Schnellansichts-URLs möglicherweise Teile aufweisen, die für eine bestimmte Website-Kategorie häufig vorkommen, sich aber nur ändern, wenn Sie einen anderen Bereich der Website besuchen.

Im einfachsten Fall ist der einzige variable Teil der Schnellansichts-URL die Produkt-SKU. In diesem Fall ist der SKU-Wert das einzige Datenelement, das Sie zum Hinzufügen von Hotspots zum Bannerbild benötigen.

In komplexen Fällen hat die Schnellansichts-URL allerdings mehrere verschiedene Elemente zusätzlich zur SKU, wie Kategorie-ID, Farb-Code, Größen-Code usw. In solchen Fällen ist jedes Element eine separate Variable in Ihrer Hotspot-Datendefinition in der Funktion für interaktive Bilder mit Shopping-Funktion in AEM Assets.

Sehen Sie sich die folgenden Beispiele für Schnellansichts-URLs und die resultierenden Hotspot-Variablen an:

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
        </ul> <p>Der einzige variable Teil der URL ist der Wert des Abfrageparameters „productId=“ und ist offensichtlich ein SKU-Wert. Daher müssen nur die SKU-Felder der Hotspots mit Werten wie <strong><code>866558</code></strong>, <strong><code>1196184</code></strong>, <strong><code>1081492</code></strong> oder <strong><code>1898294</code></strong> ausgefüllt werden.</p> </td> 
      </tr> 
      <tr> 
       <td><p>Einzelne SKU, befindet sich im URL-Pfad.</p> </td> 
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
        </ul> <p>In diesem Fall liegen zwei abweichende Teile in der URL vor. Die SKU wird im <code>prodId</code> und die Kategorie-ID</p><p><code>categoryId</code></p><ul><li><p><code>305466</code><code>categoryId</code><code>1100004</code></p></li><li><p><code>310181</code><code>categoryId</code><code>1100004</code></p></li><li><p><code>308706</code><code>categoryId</code><code>1740148</code></p></li></ul><p></p></td></tr></tbody></table></td></tr><tr></tr></table>

**Beispiel**

Sie können den in den drei oben genannten Beispielen verwendeten Ansatz auch auf die Demo-Web-Seite anwenden:

[https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html?lang=de](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html?lang=de)

Die Demo-Web-Seite enthält mehrere Produktminiaturansichten, von denen jede eine Schnellansichtsschaltfläche mit der Bezeichnung **[!UICONTROL Weitere Informationen]**. Klicken Sie bei aktiviertem Debugging-Tool des Webbrowsers auf jede Schaltfläche und notieren Sie sich die aufgezeichneten Schnellansichts-URLs. Nachdem Sie alle vier Produktschnellansichten auf der Seite aktiviert haben, verfügen Sie über die folgende Liste mit den an das Backend gesendeten Schnellansichtsanfragen:

* `/datafeed/Men-Windbreaker.json`
* `/datafeed/Men-SimpleHenley.json`
* `/datafeed/Men-CamoPullover.json`
* `/datafeed/Women-QuiltedDownJacket.json`

Wenn Sie diese Server-Aufrufe betrachten, sehen Sie, dass nur der Anfragepfad produktspezifische Informationen enthält. Beachten Sie außerdem, dass die Abfragezeichenfolge überhaupt nicht verwendet wird und zwei unterschiedliche Typen von Datenteilen beteiligt sind:

* Der erste Typ ist Männer oder Frauen. Dies kann als „Produktkategorie“ bezeichnet werden.
* Der zweite Typ ist der Produktname, z. B. CamoPullover. Sie können davon ausgehen, dass dies die Produkt-SKU ist.

Mit diesen Informationen hat die gesamte Schnellansichts-URL das folgende Muster:

`/datafeed/$categoryId$-$SKU$.json`

Auf Grundlage einer solchen Analyse würden Sie `categoryId` und `SKU` für Hotspots verwenden.

Jetzt können Sie ein Bildbanner hochladen und diesem Hotspots mit der Funktion für interaktive Bilder mit Shopping-Funktion in AEM Assets hinzufügen.

## (Optional) Erstellen einer Viewer-Vorgabe für interaktive Bilder {#optional-creating-an-interactive-image-viewer-preset}

Sie können die standardmäßige Viewer-Vorgabe für interaktive Bilder mit dem Namen **[!UICONTROL Shoppable_Banner]** , das mit AEM Assets geliefert wird. Sie können auch eine eigene benutzerdefinierte Viewer-Vorgabe für interaktive Bilder erstellen.

Wenn Sie eine benutzerdefinierte Viewer-Vorgabe für interaktive Bilder erstellen, können Sie das Erscheinungsbild von Hotspots auf dem Bildbanner bestimmen. Bei der Erstellung der Viewer-Vorgabe können Sie eine Hotspot-Grafik aus einer Galerie mit vordefinierten Bildern verwenden.

Nachdem Sie die Viewer-Vorgabe gespeichert haben, wird sie automatisch aktiviert (eingeschaltet) auf der **[!UICONTROL Viewer-Vorgabe]** Listenseite in AEM Assets. Diese Funktionalität bedeutet, dass sie in der interaktiven Medienkomponente sowie dann sichtbar ist, wenn Sie ein Asset anzeigen. Allerdings *liefern* ein interaktives Banner mit dieser Viewer-Vorgabe, müssen Sie *publish* auch Ihre Viewer-Vorgabe (dies gilt für benutzerdefinierte oder vordefinierte Viewer-Vorgaben).

**So erstellen Sie eine Viewer-Vorgabe für interaktive Bilder**:

1. Tippen Sie links in der Leiste auf **[!UICONTROL Tools > Assets > Viewer-Vorgaben]**.
1. Tippen Sie in der Nähe der rechten oberen Ecke der Seite auf **[!UICONTROL Erstellen]**.
1. Im **[!UICONTROL Neue Viewer-Vorgabe]** Geben Sie einen Namen ein, um die Viewer-Vorgabe für interaktive Banner zu beschreiben.

   Dies ist der Titel, der im **[!UICONTROL Viewer-Vorgabe]** Listenseite nach dem Speichern.
1. Im **[!UICONTROL Rich-Media-Typ]** Pulldown-Menü auswählen **[!UICONTROL Interaktives Bild]**.
1. Tippen Sie auf **Erstellen**.
1. Im **[!UICONTROL Viewer-Vorgabe bearbeiten]** Seite, tippen Sie auf **[!UICONTROL Erscheinungsbild]** Registerkarte.
1. Führen Sie einen der folgenden Schritte aus:

   * Um ein eigenes Hotspot-Bild hochzuladen, das Sie für Bilder verwenden möchten, tippen Sie auf das **[!UICONTROL Asset-Auswahl]** Symbol. Im **[!UICONTROL Inhalt auswählen]** , navigieren Sie zum gewünschten Hotspot-Bild, wählen Sie es aus und tippen Sie dann auf **[!UICONTROL Häkchen]** rechts oben.
   * Um ein vordefiniertes Hotspot-Bild auszuwählen, tippen Sie auf das **[!UICONTROL Hotspot-Galerie]** Symbol. Tippen Sie in der Palette der Hotspot-Galerie auf das Hotspot-Bild, das Sie verwenden möchten.

1. Tippen Sie oben rechts auf **[!UICONTROL Speichern]**.

   Veröffentlichen Sie die neue Viewer-Vorgabe.

   Siehe [Veröffentlichen von Viewer-Vorgaben, die Sie hinzugefügt haben](managing-viewer-presets.md#publishing-viewer-presets).

   Sie sind nun bereit, ein Bildbanner hochzuladen.

## Hochladen eines Bildbanners {#uploading-an-image-banner}

Wenn Sie die gewünschten Bilder bereits hochgeladen haben, fahren Sie mit dem nächsten Schritt fort: [Hinzufügen von Hotspots zu einem Bildbanner](#adding-hotspots-to-an-image-banner).

**So laden Sie ein Bildbanner hoch**:

1. Laden Sie Bildbanner hoch, die interaktiv sein sollen.

   Informationen hierzu finden Sie unter [Hochladen von Assets](managing-assets-touch-ui.md#uploading-assets).

   Sie können jetzt dem Bildbanner Hotspots hinzuzufügen. Anweisungen dazu finden Sie in der folgenden Aufgabe.

## Hinzufügen von Hotspots zu einem Bildbanner {#adding-hotspots-to-an-image-banner}

Sie können einem Bildbanner Hotspots hinzufügen, indem Sie den Editor im **[!UICONTROL Hotspot-Verwaltung]** Seite.

Beim Hinzufügen von Hotspots können Sie sie als Popup-Schnellansichtsanzeige, als Hyperlink oder als Experience Fragment definieren.

Weitere Informationen finden Sie unter [Experience Fragments](/help/sites-authoring/experience-fragments.md).

>[!NOTE]
>
>Beachten Sie, dass im interaktiven Bild die Tools zur Freigabe in Social Media nicht unterstützt werden, wenn Sie den Viewer in ein Experience Fragment einbetten. Um dies zu vermeiden, können Sie Viewer-Vorgaben verwenden oder erstellen, die keine Tools zur Freigabe in Social Media aufweisen. Mit diesen Viewer-Vorgaben können Sie sie erfolgreich in Experience Fragments einbetten.

**[!UICONTROL Die Optionen „Rückgängig“ und „Wiederholen“ in der Nähe der oberen rechten Ecke der Seite werden während der aktuellen Erstellungs-/Bearbeitungssitzung unterstützt.]******

Wenn Sie die Erstellung des interaktiven Bildes abgeschlossen haben, können Sie **[!UICONTROL Vorschau]** um eine Darstellung anzuzeigen, wie das interaktive Bild für Kunden angezeigt wird.

Siehe [(Optional) Anzeigen einer Vorschau für interaktive Bilder](#optional-previewing-interactive-images).

>[!NOTE]
>
>Wenn Sie einem Bild in einem interaktiven Bild oder einem Karussellbanner Hotspots hinzufügen, werden die Hotspot-Informationen unabhängig davon, ob es sich um ein interaktives Bild oder ein Karussellbanner handelt, am selben Metadatenspeicherort gespeichert, der relativ zum Speicherort des Bildes ist. Diese Funktion bedeutet, dass Sie dasselbe Bild zusammen mit den definierten Hotspot-Daten in beiden Viewern einfach wiederverwenden können.
>
>Beachten Sie jedoch, dass Karussellbanner Imagemaps auf Bildern unterstützen, die auch Hotspots enthalten können. Bei interaktiven Bildern wird dies dagegen nicht unterstützt. Beachten Sie dies, wenn Sie ein interaktives Bild oder ein Karussellbanner erstellen möchten, das dasselbe Bild verwendet. Sie können interaktive Bilder und Karussellbanner erstellen, indem Sie stattdessen separate Kopien desselben Bildes verwenden.
>
>Siehe auch [Karussellbanner](carousel-banners.md).

>[!NOTE]
>
>Wenn Sie interaktive Bilder mit Hotspots bearbeiten, um das Bild zu beschneiden, werden die Hotspots entfernt.

**So fügen Sie einem Bildbanner Hotspots hinzu**:

1. Navigieren Sie in der Ansicht &quot;Assets&quot;zum Bildbanner, das interaktiv sein soll.
1. Führen Sie einen der folgenden Schritte aus:

   * Bewegen Sie den Mauszeiger über das Bild und tippen Sie auf **[!UICONTROL Auswählen]** (Häkchensymbol). Tippen Sie in der Symbolleiste auf **[!UICONTROL Bearbeiten]**.
   * Bewegen Sie den Mauszeiger über das Bild und tippen Sie dann auf **[!UICONTROL Mehr Aktionen]** (Symbol mit drei Punkten) > **[!UICONTROL Bearbeiten]**.
   * Tippen Sie auf das Bild, um es im **[!UICONTROL Detailansicht]** Seite. Tippen Sie in der Symbolleiste auf **[!UICONTROL Bearbeiten]**.

1. Tippen Sie oben links auf der Seite auf **[!UICONTROL Hotspot hinzufügen]** (Fingertipp-Symbol), um den **[!UICONTROL Hotspot-Verwaltung]** Seite.
1. Tippen Sie oben links auf der Seite auf **[!UICONTROL Hotspot]**.
1. a. In der linken oberen Ecke des **Hotspot-Verwaltung** Seite, tippen Sie auf **[!UICONTROL Hotspot]**.
b. Tippen Sie im Bild auf eine Stelle, an der der Hotspot angezeigt werden soll. Ziehen Sie bei Bedarf den Hotspot, um seine Position anzupassen.
c. Fügen Sie bei Bedarf weitere Hotspots hinzu, indem Sie die Schritte a und b wiederholen. d. (Optional) Um einen Hotspot zu löschen, wählen Sie ihn auf dem Bild aus und tippen Sie dann auf **[!UICONTROL Löschen]** (Papierkorbsymbol) unter dem **[!UICONTROL Hotspots]** -Überschrift.

1. Im **[!UICONTROL Name]** Textfeld den Namen des Hotspots ein. Dieser Name wird auch im **[!UICONTROL Ausgewählter Hotspot]** Dropdown-Liste.
1. Führen Sie einen der folgenden Schritte aus:

   * Tippen Sie auf **[!UICONTROL Schnellansicht]**.

      * Wenn Sie AEM Sites- oder eCommerce-Kunde sind, tippen Sie auf das **[!UICONTROL Produktauswahl]** Symbol (Lupe), um die **[!UICONTROL Produkt auswählen]** Seite. Tippen Sie auf das Produkt, das Sie verwenden möchten, und dann auf **[!UICONTROL Auswählen]** in der oberen rechten Ecke der Seite, um zur **[!UICONTROL Hotspot-Verwaltung]** Seite.
      * Wenn Sie *kein* AEM Sites- oder eCommerce-Kunde sind, gehen Sie wie folgt vor:

         * Lesen Sie den Abschnitt [Ermitteln von Hotspot-Variablen](#optional-identifying-hotspot-variables). Diese Variablen müssen Sie definieren.
         * Geben Sie anschließend manuell den SKU-Wert ein. Im **[!UICONTROL SKU-Wert]** in das Textfeld die SKU (Stock Keeping Unit, Bestandseinheit) des Produkts ein. Hierbei handelt es sich um eine eindeutige Kennung für jedes von Ihnen angebotene Produkt oder jeden von Ihnen angebotenen Dienst. Der variable Teil der Schnellansichtsvorlage wird automatisch mit dem eingegebenen SKU-Wert ausgefüllt, sodass das System den Hotspot, auf den getippt wird, mit der Schnellansicht einer bestimmten SKU verbinden kann.
         * (Optional) Wenn andere Variablen in der Schnellansicht vorhanden sind, die Sie verwenden müssen, um ein Produkt weitergehend zu identifizieren, tippen Sie auf **[!UICONTROL Generische Variable hinzufügen]**. Geben Sie im Textfeld eine zusätzliche Variable an. Beispielsweise ist `category=Mens` eine hinzugefügte Variable.
   * Tippen Sie auf **Hyperlink**.

      * Wenn Sie AEM Sites-Kunde sind, tippen Sie auf die **[!UICONTROL Site-Selektor]** Symbol (Ordner), um zu einer URL zu navigieren. Beachten Sie, dass die URL-basierte Verknüpfungsmethode nicht möglich ist, wenn Ihr interaktiver Inhalt über Links mit relativen URLs verfügt, insbesondere über Links zu Seiten in AEM Sites.
      * Wenn Sie ein eigenständiger Kunde sind, finden Sie im **[!UICONTROL HREF]** Textfeld den vollständigen URL-Pfad zu einer verknüpften Webseite angeben.

      Vergessen Sie nicht anzugeben, ob der Link auf einer neuen Browser-Registerkarte (empfohlener Standard) oder auf derselben Registerkarte geöffnet werden soll.

      Weitere Informationen finden Sie unter [Arbeiten mit Selektoren](working-with-selectors.md).

   * Tippen Sie auf **Experience Fragment**.

      * Wenn Sie AEM Sites-Kunde sind, tippen Sie auf die **[!UICONTROL Suche]** Symbol (Lupe), um die **[!UICONTROL Experience Fragment]** Seite. Tippen Sie auf das Experience Fragment, das Sie verwenden möchten, und dann auf **[!UICONTROL Auswählen]** in der rechten oberen Ecke der Seite, um zur Seite &quot;Hotspot-Verwaltung&quot;zurückzukehren.

         Weitere Informationen finden Sie unter [Experience Fragments](/help/sites-authoring/experience-fragments.md).
         >[!NOTE]
         >Beachten Sie, dass im interaktiven Bild die Tools zur Freigabe in Social Media nicht unterstützt werden, wenn Sie den Viewer in ein Experience Fragment einbetten. Um dies zu vermeiden, können Sie Viewer-Vorgaben verwenden oder erstellen, die keine Tools zur Freigabe in Social Media aufweisen. Mit diesen Viewer-Vorgaben können Sie sie erfolgreich in Experience Fragments einbetten.

      * Legen Sie die Breite und Höhe des Experience Fragment fest, so wie es im Banner angezeigt werden soll.



1. Tippen **[!UICONTROL Speichern]** , um Ihre Arbeit zu speichern und zur **[!UICONTROL Durchsuchen]** Seite.
1. Veröffentlichen Sie das interaktive Bild. Durch eine Veröffentlichung kann das Banner über die Cloud bereitgestellt werden. Außerdem wird ein Einbettungs-Code zur Integration auf der Website von Dritten generiert.

   Siehe [Veröffentlichen von Assets](managing-assets-touch-ui.md#publishing-assets).

   Nachdem Sie Hotspots hinzugefügt und das interaktive Bild veröffentlicht haben, können Sie es jetzt einer vorhandenen Website hinzufügen.

   Siehe [Integrieren eines interaktiven Bildes auf Ihrer Website](#integrating-an-interactive-image-with-your-website).

   >[!NOTE]
   >
   >Wenn Sie interaktive Bilder mit Hotspots bearbeiten, um das Bild zu beschneiden, werden die Hotspots entfernt.

### (Optional) Anzeigen einer Vorschau für interaktive Bilder {#optional-previewing-interactive-images}

Mithilfe der Vorschau können Sie eine Darstellung des interaktiven Bildes aus der Perspektive der Kunden anzeigen und die Hotspots des Bildes testen, um sicherzustellen, dass sie sich wie erwartet verhalten.

Wenn das interaktive Bild Ihren Vorstellungen entspricht, können Sie es veröffentlichen.\
Siehe [Einbetten des Video- oder Bild-Viewers auf einer Web-Seite](embed-code.md).\
Siehe [Verknüpfen von URLs mit einer Web-Anwendung](linking-urls-to-yourwebapplication.md). Beachten Sie, dass die URL-basierte Verknüpfungsmethode nicht möglich ist, wenn Ihr interaktiver Inhalt über Links mit relativen URLs verfügt, insbesondere über Links zu Seiten in AEM Sites.\
Siehe [Hinzufügen von Dynamic Media-Assets zu Seiten](adding-dynamic-media-assets-to-pages.md).

**So zeigen Sie eine Vorschau für interaktive Bilder an**:

1. Navigieren Sie in der Ansicht „Assets“ zu einem vorhandenen interaktiven Bild, das Sie erstellt haben, um es in der Vorschau zu öffnen.
1. In der linken oberen Ecke der Seite &quot;Vorschau&quot;in der **[!UICONTROL Inhalt]** Dropdown-Liste, tippen Sie auf **[!UICONTROL Viewer]**.
1. Im **[!UICONTROL Viewer]** Liste, tippen Sie auf **[!UICONTROL Shoppable_Banner]** oder den Namen der von Ihnen erstellten Viewer-Vorgabe für interaktive Bilder.
1. Tippen Sie auf die Hotspots auf dem Bild, um ihre zugehörigen Aktionen zu testen.

## Veröffentlichen von interaktiven Bild-Assets {#publishing-interactive-image-assets}

Weitere Informationen zum Veröffentlichen von interaktiven Bild-Assets finden Sie unter [Veröffentlichen von Assets](publishing-dynamicmedia-assets.md).

## Integrieren eines interaktiven Bildes auf Ihrer Website {#integrating-an-interactive-image-with-your-website}

Nachdem Sie ein Bannerbild hochgeladen, Hotspots hinzugefügt und das interaktive Bild veröffentlicht haben, können Sie es jetzt auf Ihrer Website hinzufügen.

Wenn Sie AEM Sites-Kunde sind, können Sie das interaktive Bild hinzufügen, indem Sie die interaktive Medienkomponente auf Ihre Seite ziehen. Siehe [Hinzufügen von Dynamic Media-Assets zu Seiten](adding-dynamic-media-assets-to-pages.md).

Wenn Sie nur AEM Assets verwenden, können Sie das interaktive Bild Ihrer Website manuell hinzufügen, wie in diesem Abschnitt beschrieben.

1. Kopieren Sie den Einbettungs-Code des veröffentlichten interaktiven Bildes.

   Siehe [Einbetten des Video- oder Bild-Viewers auf einer Web-Seite](embed-code.md).

1. Fügen Sie den kopierten Einbettungs-Code auf dem gewünschten Bereich innerhalb der Web-Seite hinzu.

   Der kopierte Einbettungs-Code ist für eine responsive Umgebung ausgelegt, sodass die Anpassung an den zugewiesenen Bereich automatisch erfolgen sollte.

**Beispiel**

Verwenden der Demo-Website als ein Beispiel:

[https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html?lang=de](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html?lang=de)

Beachten Sie, dass das Bild der drei Männer ein statisches Bild ist `IMG` Tag:

```xml
<img class="img-responsive" width="100%" title="Hero Image 2" alt="Hero Image 2" src="images/shoppable-banner.jpg">
```

Die Integration ist so einfach wie das Entfernen des `IMG`-Tags und dessen entsprechende Ersetzung durch den kopierten Integrations-Code aus AEM Assets. Sie können das Ergebnis in der folgenden URL anzeigen, die ein interaktives Bild mit Shopping-Funktion auf der Seite mit drei Kreis-Hotspots anzeigt:

[https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-1.html?lang=de](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-1.html?lang=de)

>[!NOTE]
>
>Zurzeit dienen die Hotspots auf dem interaktiven Bild mit Shopping-Funktion auf der Demo-Website nur zu Anzeigezwecken. Sie sind zurzeit noch nicht in die Schnellansichten integriert.

Um einen Zuschnitt auf ein interaktives Bild mit Shopping-Funktion für eine responsive Umgebung anzuwenden, können Sie das Konfigurationsattribut für das interaktive Bild einbeziehen `ZoomView.iscommand` zum Pfad - wobei `ZoomView` die aufzurufende Komponente ist und `iscommand` ist der von Ihnen angewendete Image-Serving-Befehl.

Informationen hierzu finden Sie im Thema über das Konfigurationsattribut [ZoomView.iscommand](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/command-reference-configuration-attributes-interactive-images/r-html5-aem-interactive-image-config-attrib-zoomview-iscommand.html?lang=de).

Informationen finden Sie unter [Image-Serving-Befehl](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-crop.html?lang=de).

Jetzt können Sie das interaktive Bild in eine Schnellansicht auf Ihrer Website integrieren.

## Integrieren eines interaktiven Bildes in einer Schnellansicht  {#integrating-an-interactive-image-with-an-existing-quickview}

>[!NOTE]
>
>Diese Aufgabe ist nur relevant, wenn Sie die Standalone-Version von AEM Assets verwenden.

Der letzte Schritt in diesem Prozess ist die Integration des interaktiven Bildes in eine vorhandene Schnellansichtsimplementierung auf Ihrer Website. Es gibt keine Lösung für die Integration, die für alle Fälle funktioniert. Jede Schnellansichtsimplementierung ist einzigartig. Daher ist ein spezifischer Ansatz erforderlich, wofür höchstwahrscheinlich die Unterstützung eines Frontend-IT-Mitarbeiters nötig ist.

Die vorhandene Schnellansichtsimplementierung stellt normalerweise eine Kette von untereinander verknüpften Aktionen dar, die auf der Web-Seite in der folgenden Reihenfolge stattfinden:

1. Ein Benutzer löst ein Element auf der Benutzeroberfläche Ihrer Website aus.
1. Der Frontend-Code ruft anhand des in Schritt 1 ausgelösten Benutzeroberflächenelements eine Schnellansichts-URL auf.
1. Der Frontend-Code sendet mithilfe der in Schritt 2 abgerufenen URL eine Ajax-Anfrage.
1. Die Backend-Logik gibt dem Frontend-Code die entsprechenden Schnellansichtsdaten oder -inhalte zurück.
1. Der Frontend-Code lädt die Schnellansichtsdaten oder -inhalte.
1. Optional wandelt der Frontend-Code die geladenen Schnellansichtsdaten in eine HTML-Darstellung um.
1. Der Frontend-Code zeigt ein modales Dialogfeld an und rendert den HTML-Inhalt auf dem Bildschirm für den Endbenutzer.

Diese Aufrufe stellen möglicherweise keine unabhängigen öffentlichen API-Aufrufe dar, die durch die Web-Seitenlogik in einem beliebigen Schritt aufgerufen werden können. Vielmehr handelt es sich um einen verketteten Aufruf, in dem der jeweils nächste Schritte in der letzten Phase (Callback) des vorherigen Schritts ausgeblendet ist.

Während das interaktive Bild mit Shopping-Funktion Schritt 1 und teilweise Schritt 2 ersetzt, wenn ein Benutzer auf einen Hotspot innerhalb des Shop-fähigen Bildes klickt, wird diese Benutzerinteraktion vom Viewer verarbeitet. Der Viewer gibt der Web-Seite ein Ereignis zurück, das alle zuvor zu AEM Assets hinzugefügten Hotspot-Daten aufweist.

In einem solchen Ereignis-Handler nimmt der Frontend-Code Folgendes vor:

* Listet ein Ereignis auf, das vom interaktiven Bild mit Shopping-Funktion ausgegeben wird.
* Erstellt anhand der Hotspot-Daten eine Schnellansichts-URL.
* Er löst den Schnellansichts-Ladevorgang vom Backend aus und rendert die Schnellansicht auf dem Bildschirm, um sie anzuzeigen.

Der von AEM Assets zurückgegebene Einbettungs-Code verfügt über einen einsatzbereiten Ereignis-Handler, der auskommentiert ist, wie im folgenden hervorgehobenen Code-Fragment zu sehen ist:

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

Daher ist es nur erforderlich, die Auskommentierung des Codes aufzuheben und den Platzhalter-Handlertext durch den Code zu ersetzen, der für die bestimmte Web-Seite spezifisch ist.

Der Prozess der Erstellung der Schnellansichts-URL ist im Wesentlichen das Gegenteil des Prozesses, der zur Identifizierung der zuvor behandelten Hotspot-Variablen verwendet wird.

Informationen hierzu finden Sie unter [Ermitteln von Hotspot-Variablen](#optional-identifying-hotspot-variables).

Anhand unserer vorherigen Schnellansichts-URL-Beispiele können Sie in den folgenden Beispielen sehen, wie die Schnellansichts-URL in jedem Fall erstellt wird:

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
   <td><p>Einzelne SKU, befindet sich im URL-Pfad.</p> </td> 
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

Der letzte Schritt besteht darin, die Schnellansichts-URL auszulösen, und für das Aktivieren des Schnellansichtsbereichs ist höchstwahrscheinlich die Unterstützung eines Frontend-IT-Mitarbeiters aus Ihrer IT-Abteilung erforderlich. Diese Fachkraft verfügt am ehesten über das entsprechende Fachwissen, um mithilfe einer vordefinierten Schnellansichts-URL die Implementierung der Schnellansicht im entsprechenden Schritt auszulösen.

Sie können sehen, wie diese Schritte auf die Demo-Website angewendet werden, sodass ein interaktives Bild mit Shopping-Funktion mit dem Schnellansichts-Code voll integriert wird. Zuvor wurde die Struktur der Schnellansichts-URL wie folgt identifiziert:

```xml
/datafeed/$categoryId$-$SKU$.json
```

Um diese URL innerhalb der Handlers `quickViewActivate` zu rekonstruieren, können Sie die Felder `categoryId` und `SKU` verwenden, die im Objekt `inData` verfügbar sind, das durch den Code des Viewers an den Handler übergeben wird:

```xml
var sku=inData.sku;
var categoryId=inData.categoryId;
var quickViewUrl = "datafeed/" + categoryId + "-" + sku + ".json";
```

Auf der Demo-Website wird die Anzeige des Schnellansichtsdialogfelds durch einen einfachen `loadQuickView()`-Funktionsaufruf ausgelöst. Diese Funktion akzeptiert als einziges Argument die Schnellansichtsdaten-URL. Der letzte Schritt bei der Integration des interaktiven Bildes mit Shopping-Funktion besteht darin, dem `quickViewActivate`-Handler die folgende Code-Zeile hinzuzufügen:

```xml
loadQuickView(quickViewUrl);
```

Im Folgenden finden Sie den vollständigen Quell-Code:

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

Die endgültige Demowebsite mit dem vollständig integrierten interaktiven Bild sieht wie folgt aus:

[https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-3.html?lang=de](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-3.html?lang=de)

## Verwenden von Schnellansichten zum Erstellen benutzerdefinierter Popups {#using-quickviews-to-create-custom-pop-ups}

Siehe [Erstellen benutzerdefinierter Popups mithilfe von Schnellansichten](custom-pop-ups.md).
