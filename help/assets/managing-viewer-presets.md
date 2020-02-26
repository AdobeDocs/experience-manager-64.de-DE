---
title: Verwalten von Viewer-Vorgaben für dynamische Medien
seo-title: Verwalten von Viewer-Vorgaben für dynamische Medien
description: Erstellen und Verwalten von Viewer-Vorgaben für dynamische Medien
seo-description: Erstellen und Verwalten von Viewer-Vorgaben für dynamische Medien
uuid: 31ef7a4e-2053-43b5-ac6c-cdc4b30c3914
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: e78bb08a-a923-4399-b3f7-13aa4b7994d5
legacypath: /content/docs/en/aem/6-0/administer/integration/dynamic-media/viewer-presets
translation-type: tm+mt
source-git-commit: 211d6f13eba0000bbab92e0bd014420f5ca88e4d

---


# Managing Dynamic Media viewer presets {#managing-viewer-presets}

Eine Viewer-Vorgabe für dynamische Medien ist eine Sammlung von Einstellungen, mit denen festgelegt wird, wie Benutzer Rich-Media-Assets auf ihren Computerbildschirmen und Mobilgeräten anzeigen. Administratoren können Viewer-Vorgaben erstellen. Einstellungen sind für eine Vielzahl an Viewer-Konfigurationsoptionen verfügbar. Sie können beispielsweise die Viewer-Anzeigegröße oder das Zoomverhalten ändern.

For instructions on creating and customizing your own HTML5 viewer presets, see the *Adobe Scene7 HTML5 Viewer SDK*. Das SDK ist auf dem im SDK eingebetteten IS-Veröffentlichungsserver verfügbar. Jede Bibliotheksversion verfügt über eine eigene SDK-Dokumentation.

Pfad: `<scene7_domain>/s7sdk/<library_version>/docs/jsdocs/index.html`.\
For example, 3.5 SDK: [https://s7d1.scene7.com/s7sdk/3.5/docs/jsdoc/index.html](https://s7d1.scene7.com/s7sdk/3.5/docs/jsdoc/index.html)

Siehe auch das [Adobe-Viewer-Referenzhandbuch](https://marketing.adobe.com/resources/help/en_US/s7/viewers_ref/). 

In diesem Abschnitt wird beschrieben, wie Viewer-Vorgaben erstellt, bearbeitet und verwaltet werden.  Sie können jederzeit bei der Vorschau eines Assets eine Viewer-Vorgabe darauf anwenden.  Siehe [Anwenden von Viewer-Vorgaben](viewer-presets.md). 

>[!NOTE]
>
>Denken Sie daran, dass die Bearbeitung von *vordefinierten, standardmäßig vorhandenen Viewer-Vorgaben* als Szenario nicht unterstützt wird.  Wenn Sie versuchen, eine standardmäßig vorhandene Viewer-Vorgabe zu bearbeiten, werden Sie aufgefordert, die Viewer-Vorgabe unter einem neuen Namen zu speichern. 

## Möglichkeit des Zugriffs auf die Tastatur im Viewer {#keyboard-accessibility-for-viewers}

Alle standardmäßigen Viewer unterstützen den Zugriff auf die Tastatur.

Weitere Informationen finden Sie unter [ Tastaturzugriff und Navigation](https://marketing.adobe.com/resources/help/en_US/s7/viewers_ref/c_keyboard_accessibility.html).

## Managing Dynamic Media viewer presets {#managing-presets}

You can add, edit, delete, publish, unpublish, and preview viewer presets in AEM by tapping **[!UICONTROL Tools > Assets > Viewer Presets]**.

![tools-assets](assets/tools-assets.png)

>[!NOTE]
>
>Standardmäßig zeigt das System 15 Viewer-Vorgaben, wenn Sie in einer Detailansicht eines Assets „Viewer“ auswählen.  Sie können diese Grenze erhöhen. Siehe [Erhöhen der Anzahl angezeigter Viewer-Vorgaben](#increasing-the-number-of-viewer-presets-that-display). 

## Viewer-Unterstützung für Webseiten mit responsivem Design  {#viewer-support-for-responsive-designed-web-pages}

Unterschiedliche Webseiten haben unterschiedliche Anforderungen.  Mitunter möchten Sie vielleicht, dass eine Webseite über einen Link verfügt, der den HTML5-Viewer in einem separaten Browserfenster öffnet.  In anderen Fällen kann es aber auch erforderlich sein, den HTML5-Viewer direkt auf der Hostseite einzubetten. In letzterem Fall kann die Webseite ein statisches Layout aufweisen.  Or, it may be *responsive* and display differently on different devices or for different browser window sizes. Um all diese Anforderungen zu berücksichtigen, unterstützen sämtliche vordefinierten, standardmäßig vorhandenen HTML5-Viewer, die mit Dynamic Media bereitgestellt werden, sowohl statische als auch responsive Webseiten. 

Weitere Informationen zum Einbetten responsiver Viewer auf Webseiten finden Sie unter [Bibliothek responsiver Bilder](https://marketing.adobe.com/resources/help/en_US/s7/is_ir_api/is_api/c_about_responsive_static_image_library.html) in der *Scene7 Image Serving-API-Hilfe*.

>[!NOTE]
>
>Sie müssen zunächst alle standardmäßig vorhandenen Viewer veröffentlichen, um sie verwenden zu können. \
>Siehe [Veröffentlichen von Viewer-Vorgaben](#publishing-viewer-presets).

## Kompatibilität mit Viewer-Vorgaben {#viewer-preset-system-compatibility}

Alle standardmäßig vorhandenen Viewer-Vorgaben, die mit Dynamic Media bereitgestellt werden, sind mit den folgenden Systemen vollständig kompatibel: 

* Desktops 
* Apple iPhones 
* Apple iPads 
* Android-Smartphones 
* Android-Tablets 
* Videos: zusätzliche Unterstützung zur MP4-Wiedergabe für [Blackberry](https://developer.blackberry.com/devzone/develop/supported_media/bb_media_support_at_a_glance.html#kba1328730952678) und [Windows Phone](https://msdn.microsoft.com/library/windows/apps/ff462087%28v=vs.105%29.aspx) 

### Rich media types for viewer presets {#rich-media-types-for-viewer-presets}

Administratoren können die folgenden Rich-Media-Typen hinzufügen und anpassen, wenn sie Viewer-Vorgaben erstellen. 

| Rich-Media-Typen | Beschreibung |
|:---|:---|
| **Karussell-Set** | Hotspots, Imagemaps oder beide werden zu einer Reihe von mindestens zwei Bildern hinzugefügt. Ein Kunde kann die Bilder nach links oder rechts schwenken und dann auf einen Hotspot auf einem Bild klicken, um weitere Details zu erhalten oder direkt von einer Website-Kategorie, -Startseite oder -Einstiegsseite zu erwerben. |
| **Flyout-Zoom** | Zeigt ein zweites Bild des vergrößerten Bereichs neben dem Originalbild an. Dafür gibt es keine Steuerelemente. Benutzer verschieben die Auswahl auf den gewünschten Bereich. |
|  | Bei der Bestimmung der vollständigen Bandbreitenauslastung für diesen Viewer müssen Sie berücksichtigen, dass sowohl das Hauptbild als auch das Flyout-Bild im Viewer verarbeitet werden. Die Größe des Hauptbildes (Anzeigenbreite und -höhe) und der Zoomfaktor bestimmen die Größe des Flyout-Bildes. Sie müssen ein Gleichgewicht zwischen diesen beiden Werten schaffen, um zu verhindern, dass die Flyout-Datei zu groß wird: Wenn das Hauptbild sehr groß ist, reduzieren Sie den Zoomfaktor-Wert. (Die Flyout-Breite und Flyout-Höhe bestimmen die Größe des Flyout-Fensters, aber nicht die Größe des Flyout-Bildes, das im Viewer verarbeitet wird.) |
|  | Beispiel: Wenn das Hauptbild eine Größe von 350 x 350 Pixel und einen Zoomfaktor von 3 aufweist, hat das resultierende Flyout-Bild eine Größe von 1050 x 1050 Pixel. Wenn das Hauptbild eine Größe von 300 x 300 Pixel und einen Zoomfaktor von 4 aufweist, hat das Flyout-Bild eine Größe von 1200 x 1200 Pixel. Abhängig von der JPEG-Qualitätseinstellung (empfohlene Einstellungen liegen zwischen 80 und 90) können Sie die Dateigröße erheblich reduzieren. Als Zoomfaktor wird ein Wert zwischen 2,5 und 4 empfohlen, je nach Größe des Hauptbildes. |
| **Inline-Zoom** | Zeigt ein Bild des hereingezoomten Bereichs im ursprünglichen Viewer an. Es stehen keinerlei Steuerelemente zur Verfügung.  Benutzer verschieben vielmehr die Auswahl über den Bereich, der angezeigt werden soll.  |
| **Bildset** | Im Bildset-Viewer können Benutzer unterschiedliche Ansichten oder Farbvariationen eines Elements sehen, indem sie auf eine Miniaturansicht klicken. Dieser Viewer bietet auch Zoomtools, mit denen Bilder genauer untersucht werden können. |
| **Interaktives Bild** | Hotspots werden zu Bildteilen hinzugefügt, auf die ein Kunde klicken kann, um weitere Details zu erhalten oder direkt von den Kategorien-, Home- oder Einstiegsseiten einer Website zu erwerben. |
| **Interaktives Video** | Miniaturansichten werden zu Zeitschienensegmenten in einem Video hinzugefügt, auf das ein Kunde klicken kann, um weitere Details zu erhalten oder direkt von den Kategorien-, Home- oder Einstiegsseiten einer Website zu erwerben. |
| **Gemischte Medien** | Zeigt unterschiedliche Medientypen in einem Viewer an. Dort können Sie Rotationssets, Bildsets, Bilder und Videos aufnehmen. |
| **Panoramabild** | Die Viewer für Panoramabilder und PanoramicVR geben Kugelpanoramen wieder, um Benutzern ein 360°-Betrachtererlebnis eines Zimmers, einer Immobilie, eines Orts oder einer Landschaft zu bieten. |
|  | Damit ein hochgeladenes Bild als Kugelpanorama gilt, muss mindestens eine der beiden folgenden Eigenschaften zutreffen: <ul><li>Ein Seitenverhältnis von 2:1.</li><li>Mit den Keywords equirectangular oder spherical und panorama oder spherical und panoramic als Tags versehen. Weitere Informationen finden Sie unter [Verwenden von Tags](../sites-authoring/tags.md).</li></ul> |
|  | Die Kriterien für das Seitenverhältnis sowie die Keywords gelten für Panorama-Assets für die Asset-Detailseite und die WCM-Komponente „Panoramamedien“. |
|  | Wichtig: Dieser Viewer ist nur im Scene7-Modus von Dynamic Media verfügbar. |
| **Rotationsset** | Stellt mehrere Ansichten eines Bildes bereit, sodass Benutzer den Gegenstand drehen können, um ihn von allen Seiten zu betrachten. |
| **Video** | Wiedergeben von Videos unter Verwendung des progressiven oder adaptiven Bitraten-Streamings. Beim Streaming mit adaptiver Bitrate wird eine automatische Geräte- und Brandbreitenerkennung durchgeführt, um Videos mit der richtigen Qualität und im richtigen Format bereitzustellen. |
| **Vertikaler Zoom** | Mit dem Viewer für vertikalen Zoom können Sie das Betrachtererlebnis für Produktbilder optimieren, um Ihren Benutzern die bestmögliche Darstellung eines Produktes zu bieten. Die vertikale Positionierung von Farbfeldern: <ul><li>Stellt sicher, dass die Farbfelder über der Kante liegen. Bei horizontalen Farbfeldern waren die Muster je nach Bildschirmgröße des Benutzers  nicht sichtbar, bis der Benutzer einen Bildlauf nach unten durchführte. Wenn die Farbfelder vertikal im Viewer platziert werden, sind sie unabhängig von der Bildschirmgröße des Benutzers sichtbar.</li><li>Maximiert die Größe des Hauptbildes. Bei horizontalen Farbfeldern ist es erforderlich, Platz auf der Seite zu lassen, um sicherzustellen, dass sie sichtbar sind. Diese Positionierung verringerte die mögliche Größe des Hauptbildes. Bei einer vertikalen Farbfeld-Platzierung ist es jedoch nicht notwendig, diesen Platz freizulassen. Somit können Sie die Größe des Hauptbildes maximieren.</li></ul> |
| **Zoom** | Damit können Benutzer den Bereich durch Klicken ein- und auszoomen. Benutzer können auf Steuerelemente klicken, um ein- und auszuzoomen und das Bild auf seine Standardgröße zurückzusetzen. |

## List of out-of-the-box viewer presets {#list-of-out-of-the-box-viewer-presets}

In der folgenden Tabelle sind alle vordefinierten, sofort einsetzbaren Viewer-Vorgaben aufgeführt, die mit dynamischen Medien geliefert werden.

Siehe auch [Viewer-Referenzbibliotheksbeispiele](https://marketing.adobe.com/resources/help/en_US/s7/vlist/vlist.html) und [Live-Demos](https://landing.adobe.com/en/na/dynamic-media/ctir-2755/live-demos.html).

Informationen zu unterstützten Webbrowsern und Betriebssystemversionen für Viewer finden Sie in den Viewer-Versionshinweisen. 

See *Viewers release notes* in the table of contents of the [Viewers Reference Guide](https://marketing.adobe.com/resources/help/en_US/s7/viewers_ref/).

>[!NOTE]
>
>Alle standardmäßig vorhandenen Viewer-Vorgaben in Dynamic Media sind bereits aktiviert. Sie müssen sie allerdings noch veröffentlichen. \
>Siehe [Veröffentlichen von Viewer-Vorgaben](#publishing-viewer-presets).
>
>Any new viewer presets that you create and add must be both activated *and* published.\
> Siehe [Aktivieren oder Deaktivieren von Viewer-Vorgaben](#activating-or-deactivating-viewer-presets) und [Veröffentlichen von Viewer-Vorgaben](#publishing-viewer-presets). 

| Viewer-Vorgabentitel  | Typ | CSS-Dateiname |
|:---|:---|:---|
| Carousel_Dotted_dark | Carousel_Set | html5_carouselviewer_dotted_dark.css |
| Carousel_Dotted_light | Carousel_Set | html5_carouselviewer_dotted_light.css |
| Carousel_Numeric_dark | Carousel_Set | html5_carouselviewer_numeric_dark.css |
| Carousel_Numeric_light | Carousel_Set | html5_carouselviewer_numeric_light.css |
| Flyout | Flyout_Zoom | html5_flyoutviewer.css |
| ImageSet_dark | Bildset | html5_zoomviewer_dark.css |
| ImageSet_light | Bildset | html5_zoomviewer_light.css |
| InlineMixedMedia_dark | Mixed_Media | html5_inlinemixedmediaviewer_dark.css |
| InlineMixedMedia_light | Mixed_Media | html5_inlinemixedmediaviewer_light.css  |
| InlineZoom | Flyout_Zoom | html5_inlinezoomviewer.css |
| MixedMedia_dark | Mixed_Media | html5_mixedmediaviewer_dark.css |
| MixedMedia_light | Mixed_Media | html5_mixedmediaviewer_light.css |
| PanoramicImage | Panoramic_Image | html5_panoramicimage.css |
| PanoramicImageVR | Panoramic_Image | html5_panoramicimage.css |
| Shoppable_Banner | Interactive_Image | html5_interactiveimage.css |
| Shoppable_Video_dark | Interactive_Video | html5_interactivevideoviewer_dark.css |
| Shoppable_Video_light | Interactive_Video | html5_interactivevideovewer_light.css |
| SpinSet_dark | Spin_Set | html5_spinviewer_dark.css |
| SpinSet_light | Spin_Set | html5_spinviewer_light.css |
| Video (einschließlich Unterstützung für Untertitel) | Video | html5_videoviewer.css |
| Video_social (einschließlich Unterstützung für Untertitel und soziale Medien) | Video | html5_videoviewersocial.css |
| Zoom_dark | Zoom | html5_basiczoomviewer_dark.css |
| Zoom_light | Zoom | html5_basiczoomviewer_light.css |
| ZoomVertical_dark | Vertical_Zoom | html5_zoomverticalviewer_dark.css |
| ZoomVertical_light | Vertical_Zoom | html5_zoomverticalviewer_light.css |

### Matrix unterstützter Mobile Viewer-Gesten {#supported-mobile-viewers-gestures-matrix}

In der folgenden Tabelle werden die Mobile Viewer-Gesten benannt, die auf iOS-, Android 2.x- und Android 3.x-Geräten unterstützt werden. 

| Geste | Flyout-Zoom | Zoom | Drehung |
|---|---|---|---|
| **ziehen** | Schwenken | Schwenken | Schwenken |
| **Tippen Sie auf** | Blendet Flyout-Fenster ein | Blendet die Benutzeroberfläche ein oder aus | Blendet die Benutzeroberfläche ein oder aus |
| **Doppeltippen** | Gilt nicht | Vergrößern oder Zurücksetzen | Vergrößern oder Zurücksetzen |
| **Aufziehen** | Gilt nicht | Vergrößert (nur iOS und Android 3x) | Vergrößert (nur iOS und Android 3x) |
| **Schließen** | Gilt nicht | Verkleinert (nur iOS und Android 3x) | Verkleinert (nur iOS und Android 3x) |
| **Streichen** | Bildlaufleiste | Bildlauf | Rotationen |
| **Flick** | Bildlaufleiste | Bildlauf | Rotationen |

## Increasing the number of Dynamic Media viewer presets that display {#increasing-the-number-of-viewer-presets-that-display}

AEM zeigt verschiedene Viewer-Vorgaben an, wenn Sie ein Asset unter **[!UICONTROL Detailansicht > Viewer]** anzeigen. Sie können die Anzahl der angezeigten Viewer erhöhen oder verringern.

**So erhöhen Sie die Anzahl der angezeigten** Viewer-Vorgaben für dynamische Medien:

1. Navigate to **[!UICONTROL CRXDE Lite]** ([http://localhost:4502/crx/de](http://localhost:4502/crx/de)).
1. Navigieren Sie zum Knoten für die Viewer-Vorgabenliste unter `/libs/dam/gui/coral/content/commons/sidepanels/viewerpresets/viewerpresetslist`

   ![chlimage_1-221](assets/chlimage_1-221.png)

1. Ändern Sie in der **[!UICONTROL Grenzwert]**-Eigenschaft den **[!UICONTROL Wert]**, der standardmäßig auf 15 eingestellt ist, auf die gewünschte Zahl.
1. Navigieren Sie zur Datenquelle der Viewer-Vorgabe unter `/libs/dam/gui/coral/content/commons/sidepanels/viewerpresets/viewerpresetslist/datasource`

   ![chlimage_1-222](assets/chlimage_1-222.png)

1. In the **[!UICONTROL limit]** property, change the number to the desired number, for example `{empty requestPathInfo.selectors[1] ? "20" : requestPathInfo.selectors[1]}`
1. Tippen Sie auf **[!UICONTROL Alle speichern]**.

## Erstellen einer neuen Viewer-Vorgabe für dynamische Medien {#creating-a-new-viewer-preset}

Durch Erstellen von Viewer-Vorgaben können Sie verschiedene Einstellungen anwenden, um Assets anzuzeigen und mit diesen zu interagieren.  Sie müssen jedoch keine neuen Viewer-Vorgaben erstellen.  Wenn Sie dies bevorzugen, können Sie auch die bereits standardmäßig in AEM Assets verfügbaren Viewer-Vorgaben verwenden. 

If you choose to create a new viewer preset, after you save it, the viewer&#39;s state is automatically activated (set to **On**) in the **[!UICONTROL Viewer Presets]** page. This state means that it is visible in the **[!UICONTROL Dynamic Media]** component and the **[!UICONTROL Interactive Media]** component and whenever you preview an image or video.

Bestimmte Viewer-Vorgaben weisen exklusive Einstellungen auf, die die Nutzung und das Gesamtverhalten des Viewers beeinflussen können.  Je nach der von Ihnen erstellten Viewer-Vorgabe sollten Sie diese besonderen Hinweise berücksichtigen.  

Siehe [Besondere Hinweise zum Erstellen von Vorgaben für interaktive Viewer](#special-considerations-for-creating-an-interactive-viewer-preset).

Siehe [Besondere Hinweise zum Erstellen von Viewer-Vorgaben für Karussellbanner](#special-considerations-for-creating-a-carousel-banner-viewer-preset). 

**So erstellen Sie eine neue Viewer-Vorgabe** für dynamische Medien:

1. In the upper-left corner of AEM, tap the AEM logo, then in the left rail, tap **[!UICONTROL Tools > Assets > Viewer Presets]**.

   ![Viewer-Vorgaben](assets/viewerpresets.png)

1. On the **[!UICONTROL Viewer Presets]** page, on the toolbar, tap **[!UICONTROL Create]**.
1. Geben Sie im Dialogfeld **[!UICONTROL Neue Viewer-Vorgabe]** in das Feld **[!UICONTROL Vorgabename]** den Namen der neuen Vorgabe ein. Achten Sie darauf, einen geeigneten Namen festzulegen, da dieser nach dem Tippen auf **[!UICONTROL Erstellen]** nicht mehr geändert werden kann.

   When you save the preset later in these steps, the name appears on the Viewer Presets page under the **[!UICONTROL Preset Title]** column header.

1. On the **[!UICONTROL Rich Media Type]** drop-down menu, select the type of viewer preset you want to create, then in the upper-right corner of the page, tap **[!UICONTROL Create]**.

   Siehe [Rich-Media-Typen für Viewer-Vorgaben](#rich-media-types-for-viewer-presets).

1. On the **Edit Viewer Preset** page, tap the **[!UICONTROL Appearance]** tab.
1. Führen Sie einen der folgenden Schritte aus:

   * Wählen Sie aus dem Pulldown-Menü **[!UICONTROL Ausgewählter Typ]** eine Komponente aus, deren visuelles Design angepasst werden soll. Alternativ können Sie auf jedes visuelle Element im Viewer tippen, um es zur Konfiguration auszuwählen.

        Der Visual Editor zeigt Ihnen, wie sich eine bestimmte Eigenschaft auf einen Stil auswirkt.  Legen Sie eine beliebige Eigenschaft fest bzw. passen Sie diese an, um sofort anhand des Beispiels auf der linken Seite des Editors zu sehen, wie sich dies auf den Viewer auswirkt. 

      The CSS styling properties for each type of viewer preset are described in the any &quot;Customizing *&lt;viewer_name>* Viewer&quot; Help topic in the [Viewers Reference Guide](https://marketing.adobe.com/resources/help/en_US/s7/viewers_ref/).

      For example, if you are creating a viewer preset of the type `Mixed_Media`, see [Customizing Mixed Media Viewer](https://marketing.adobe.com/resources/help/en_US/s7/viewers_ref/c_html5_mixedmedia_viewer_customizingviewer.html) for a list and description of each property.

   * Wenn Stileinstellungen in einer separaten CSS-Datei definiert sind, können Sie die CSS-Datei in AEM Assets hochladen.  Tippen Sie unterhalb des Pulldown-Menüs „Ausgewählter Typ“ auf **[!UICONTROL CSS importieren]** (ggf. müssen Sie hierzu einen Bildlauf im Visual Editor durchführen), um nach der hochgeladenen CSS-Datei zu suchen und diese mit der Viewer-Vorgabe zu verknüpfen.****

        Beim Importieren einer CSS-Datei überprüft der Visual Editor, ob CSS die korrekten Viewer-Markierungen verwendet.  For example, if you are creating a Zoom viewer, all the CSS rules you import must be defined using its viewer class name `.s7mixedmediaviewer` defined on a parent viewer element.

      Sie können beliebige, handgefertigten CSS-Dateien importieren, solange diese die CSS-Markierungen für den jeweiligen Viewer ordnungsgemäß definieren. (CSS-Markierungen werden im Hilfethema *Anpassen des &lt;Viewer-Name>-Viewers* im [Viewer-Referenzhandbuch](https://marketing.adobe.com/resources/help/en_US/s7/viewers_ref/) erläutert. Wenn Sie beispielsweise mehr über CSS-Markierungen für den Zoom-Viewer erfahren möchten, lesen Sie den Abschnitt [Anpassen des Zoom-Viewers](https://marketing.adobe.com/resources/help/en_US/s7/viewers_ref/c_html5_20_zoom_viewer_customizingviewer.html).) Es ist jedoch möglich, dass der Visual Editor nicht alle CSS-Werte versteht.  In solchen Fällen versucht der Visual Editor, die Fehler zu überschreiben, damit das CSS weiterhin funktionieren kann.
   >[!NOTE]
   >
   >Wenn Sie CSS lieber direkt im Rohformat bearbeiten möchten, tippen Sie im Pulldownmenü „Ausgewählter Typ“ auf **[!UICONTROL CSS ein-/ausblenden]** (Sie müssen ggf. im Visual Editor nach oben blättern, um diese Option anzuzeigen).****
   >
   >Wenn Sie eine Eigenschaft direkt in CSS ändern, können Sie wie im Visual Editor sofort sehen, wie sich dies auf das Viewer-Beispiel auswirkt.  Außerdem wird zur gleichen Zeit genau diese Eigenschaft automatisch im Visual Editor aktualisiert.  Daher können Sie entweder den CSS-Editor, den Visual Editor oder beide abwechselnd verwenden. 

   >[!NOTE]
   >
   >Für Schaltflächengrafiken wählen Sie das 2x-Bild aus und laden Sie Grafiken mit hoher Auflösung hoch.  Beim Arbeiten mit interaktiven Bildern und Bannern mit Einkaufsfunktion können Sie auch aus verschiedenen standardmäßig vorhandenen Hotspot-Schaltflächen wählen. 

1. (Optional) Near the top of the **[!UICONTROL Edit Viewer Preset]** page, tap **[!UICONTROL Desktop]**, **[!UICONTROL Tablet]**, or **[!UICONTROL Phone]** to uniquely define visual styles for different device and screen types.
1. On the **[!UICONTROL Edit Viewer Preset]** page, tap the **Behavior** tab. Alternativ können Sie auf ein beliebiges visuelles Element im Viewer tippen/klicken, um es zur Konfiguration auszuwählen.
1. Wählen Sie im Pulldownmenü **[!UICONTROL Ausgewählter Typ]** eine Komponente aus, deren Verhalten Sie ändern möchten.

   Viele Komponenten im Visual Editor sind mit einer detaillierten Beschreibung verknüpft.  Diese Beschreibungen werden in blauen Feldern angezeigt, wenn Sie eine Komponente zum Anzeigen der mit ihr verknüpften Parameter einblenden. 

   Einige Viewer-Typen verfügen über Komponenten, mit denen Sie Befehle zum Image Serving in einem **IS-Befehl**-Textfeld angeben können. Eine Liste der verfügbaren Befehle finden Sie in der [Image Serving API-Referenz](https://marketing.adobe.com/resources/help/en_US/s7/is_ir_api/image_serving_api_ref.html).

   >[!NOTE]
   >
   >**Bei Nutzung eines Touchgeräts, etwa eines Telefons oder Tablets:** 
   >
   >Nachdem Sie einen Wert in das Textfeld eingegeben haben, tippen Sie auf eine andere Stelle in der Benutzeroberfläche, um die Änderung weiterzuleiten und die virtuelle Tastatur zu schließen. Wenn Sie auf die **[!UICONTROL Eingabetaste]** tippen, wird keine Aktion ausgeführt.

1. Tippen Sie in der Nähe der oberen rechten Ecke auf **[!UICONTROL Speichern]**.
1. Veröffentlichen Sie die neue Viewer-Vorgabe.  Sie müssen die Vorgabe veröffentlichen, um sie auf Ihrer Website verwenden zu können. 

   Siehe[ Veröffentlichen von Viewer-Vorgaben](#publishing-viewer-presets).

## Besondere Hinweise zum Erstellen von Viewer-Vorgaben für interaktive Videos  {#special-considerations-for-creating-an-interactive-viewer-preset}

**Wissenswertes über Anzeigemodi für Bildminiaturansichten im Anzeigefeld** 

When you create or edit an Interactive Video viewer preset, you have the choice of which **[!UICONTROL Display Mode]** setting to use when you select `InteractiveSwatches` from the **[!UICONTROL Selected Component]** pull-down menu under the **[!UICONTROL Behavior]** tab. Der von Ihnen gewählte Anzeigemodus beeinflusst, wie und wann Miniaturansichten während der Videowiedergabe angezeigt werden.  You can choose either a `segment`display mode (default) or a `continuous`display mode.

| Anzeigemodus | Beschreibung |
|---|---|
| [!UICONTROL Segment] | [!UICONTROL Das Segment] ist der Standardanzeigemodus für die standardmäßigen interaktiven Video-Viewer-Vorgaben Shoppable_Video_light und Shoppable_Video_dark sowie alle selbst erstellten interaktiven Video-Viewer-Vorgaben. |
|  | Wenn in diesem Modus einem Videosegment weniger Miniaturansichten zugewiesen sind als die Anzahl der sichtbaren Stellen im Anzeigebereich, werden Miniaturansichten der nächsten oder vorherigen Untersegmente nicht eingezogen, um leere Stellen im Bedienfeld zu füllen. So bleibt die Anzeige von einem bestimmten Videosegment zugewiesenen Mustern erhalten. |
| [!UICONTROL Kontinuierlich] | In [!UICONTROL Continuous] display mode, if the number of thumbnails in a segment is less than the number that are visible in the panel, the viewer automatically includes the display of thumbnails from the next segment, or the previous segment, in cases where the last thumbnail is displayed. |

**Wissenswertes über den automatischen Bildlauf im Viewer für interaktive Videos** 

Das automatische Bildlaufverhalten von Miniaturansichten der Viewer-Funktionen für interaktive Videos erfolgt unabhängig vom gewählten Anzeigemodus. 

When you create or edit an interactive video viewer preset, you access **[!UICONTROL Auto Scroll]** from the **[!UICONTROL Behavior]** tab. Tippen Sie auf der Registerkarte „Verhalten“ im Dropdownmenü **[!UICONTROL Ausgewählte Komponenten]** auf **[!UICONTROL InteractiveSwatches]**. The **[!UICONTROL Auto Scroll]** check box is listed below the IS Command text field.

Wenn Sie **[!UICONTROL Auto-Bildlauf]** in der Viewer-Voreinstellung deaktivieren (das Kontrollkästchen deaktivieren), wird während der Videowiedergabe durch Benutzer während der gesamten Länge des Videos nur die erste Miniaturansicht angezeigt. Benutzer können jedoch mithilfe der Pfeilsymbole manuell durch die Miniaturansichten nach oben und unten blättern.

Wenn Sie in der Viewer-Voreinstellung **[!UICONTROL Auto-Bildlauf]** aktivieren (auswählen), werden während der Videowiedergabe zu Beginn eines Segments Miniaturansichten angezeigt, die einem Videosegment zugewiesen sind. Es gibt jedoch Fälle, in denen bestimmte Miniaturansichten innerhalb eines Segments doppelt so lange angezeigt werden wie andere Miniaturansichten vor oder nach dem Segment. Dieses Verhalten tritt auf, weil die Anzahl der Miniaturansichten in einem Segment größer ist als die Zahl, die im Bedienfeld sichtbar ist, und diese nicht gleichmäßig teilbar ist.

Gehen wir zu Illustrationszwecken von einem 30 Sekunden langen Videosegment aus.  Insgesamt gibt es neun Miniaturansichten, die im Laufe dieser 30 Sekunden angezeigt werden.  Die Größe Ihres Browsers wird dergestalt geändert, dass vier verfügbare Miniaturpositionen im Anzeigefeld vorliegen.  Das 30-sekündige Videozeitsegment ist in drei Untersegmente unterteilt.  In der folgenden Tabelle wird aufgeschlüsselt, welche Miniaturansichten für ein bestimmtes Zeituntersegment angezeigt werden: 

| **Video-Untersegment** | **Zeit des Teilsegments in Sekunden** | **Im Feld sichtbare Miniaturen** |
|---|---|---|
| 1 | 0–10 | 1, 2, 3, 4 |
| 2 | 10-20 | 4, 5, 6, 7 |
| 3 | 20-30 | 6, 7, 8, 9 |

Das Videountersegment 3 wird nicht über die Miniaturansichten hinweg erweitert, die ihm zugewiesen sind.  Beachten Sie, dass die Miniaturansichten 4, 6 und 7 im Anzeigefeld doppelt so lang sichtbar sind wie die anderen.

Die durch den Viewer zum Bestimmen der Anzahl der im seitlichen Bedienfeld angezeigten Miniaturansichten verwendete Logik basiert wie folgt auf der Anzahl der verfügbaren Positionen:

* Anzahl der Untersegmente = Aufrundung auf das nächste Untersegment (Anzahl der Miniaturansichten : Anzahl der sichtbaren Spots im Miniaturansichtsfeld, auf Grundlage der Browserfenstergröße)

   Unter Verwendung des Beispiels in der obigen Tabelle ergibt 9 Miniaturansichten : 4 Slots = 2,25, was die Viewer-Logik auf 3 Untersegmente aufrundet.

* Anzahl der Miniaturen = Aufrundung auf die nächste Miniaturansicht (Anzahl der Miniaturansichten : Anzahl der Videountersegmente)

   Unter Verwendung des Beispiels in der obigen Tabelle ergibt 9 Miniaturansichten : 3 Videountersegmente = 3 Miniaturansichten.

* Dauer des Untersegments = gesamte Videodauer : Anzahl der Videountersegmente

   Unter Verwendung des Beispiels in der obigen Tabelle ergibt 30 Sekunden : 3 Segmente = 10 Sekunden anhaltende Anzeige jedes Segments.

### Special considerations for creating a Carousel Banner viewer preset {#special-considerations-for-creating-a-carousel-banner-viewer-preset}

Beim Erstellen von Viewer-Vorgaben für Karussellbanner kann der Stil von Hotspots wie folgt geändert werden: 

|  | **Beschreibung** | **Aktionen** |
|---|---|---|
| **Hotspot-Symbol** | Ändern des für Hotspot verwendeten Symbols | Um das Bild des Hotspot-Symbols zu ändern, tippen Sie auf der Registerkarte &quot; **[!UICONTROL Erscheinungsbild]** &quot;in der **[!UICONTROL ausgewählten Komponente]** auf **[!UICONTROL ImageMapEffect]**. Wählen Sie unter **[!UICONTROL Symbol]** die Option **[!UICONTROL Hintergrund]** und navigieren Sie im Feld **[!UICONTROL Bild]** zum gewünschten Hintergrundbild. |

## Aktivieren oder Deaktivieren von Viewer-Vorgaben für dynamische Medien {#activating-or-deactivating-viewer-presets}

Welche Viewer-Vorgaben in der Benutzeroberfläche verfügbar sind, hängt davon ab, welche Vorgaben im Autorenmodus aktiviert wurden. By default, a viewer preset is *On* after you create it. Wenn Sie die Vorgabe deaktivieren möchten, wird sie nicht im Autorenmodus angezeigt. Wenn die Vorgabe veröffentlicht wird. Sie wird immer veröffentlicht, unabhängig davon, ob sie aktiviert oder deaktiviert wurde. Sie können die Viewer-Vorgaben deaktivieren, wenn die Liste zu unleserlich wird oder wenn keine Viewer-Vorgabe zur Verfügung gestellt werden soll.

**So aktivieren oder deaktivieren Sie die Viewer-Vorgaben** für dynamische Medien:

1. In the upper-left corner of AEM, tap the AEM logo, then in the left rail, tap **[!UICONTROL Tools > Assets > Viewer Presets]**.
1. On the **[!UICONTROL Viewer Preset]** page, under the **[!UICONTROL State]** column header, tap the toggle to activate or deactivate a viewer preset.

   Bei aktivierten Viewer-Vorgaben wird die Umschaltfläche rechts in einem blauen Feld angezeigt; bei deaktivierten Viewer-Vorgaben wird die Umschaltfläche links in einem hellgrauen Feld angezeigt. 

## Publishing Dynamic Media viewer presets {#publishing-viewer-presets}

Activating (or turning *On*) the state of a viewer preset means that it is visible in the Dynamic Media component, the Interactive Media component, and whenever you view an asset.

Damit ein Asset mit einer Viewer-Vorgabe bereitgestellt werden kann, muss die Viewer-Vorgabe ebenfalls veröffentlicht werden. All viewer presets must be activated *and* published to obtain URL or embed code for an asset. Sie müssen alle im Lieferumfang von dynamischen Medien enthaltenen sofort einsetzbaren Viewer-Voreinstellungen aktivieren und veröffentlichen. Benutzerdefinierte Viewer-Voreinstellungen, die Sie erstellen und hinzufügen, werden automatisch aktiviert, müssen aber auch veröffentlicht werden.

Siehe [Aktivieren oder Deaktivieren von Viewer-Vorgaben](#activating-or-deactivating-viewer-presets). 

Siehe auch [Anzeigen von Assets in einer Vorschau](previewing-assets.md).

**So veröffentlichen Sie Viewer-Vorgaben** für dynamische Medien:

1. In the upper-left corner of AEM, tap the AEM logo, then in the left rail, tap **[!UICONTROL Tools > Assets > Viewer Presets]**.
1. Wählen Sie eine oder mehrere Viewer-Vorgaben zum Veröffentlichen aus. 
1. Tippen Sie auf der Symbolleiste auf das Symbol **[!UICONTROL Veröffentlichen]**.

## Sorting Dynamic Media viewer presets {#sorting-viewer-presets}

**So sortieren Sie Viewer-Vorgaben** für dynamische Medien:

1. Tippen Sie in der oberen linken Ecke von AEM auf das AEM-Logo und dann in der linken Leiste auf **Werkzeuge** (Hammersymbol) **[!UICONTROL > Assets > Viewer-Voreinstellungen]**.
1. Klicken Sie auf **[!UICONTROL Voreinstellungentitel]**, **[!UICONTROL Typ]**, **[!UICONTROL Veröffentlicht]** oder **[!UICONTROL Status]**, um nach dieser Spaltenüberschrift zu sortieren. Klicken Sie beispielsweise auf **[!UICONTROL Typ]**, um die Viewer-Voreinstellungstypen in alphabetischer oder umgekehrter alphabetischer Reihenfolge zu sortieren.

## Editing Dynamic Media viewer presets {#editing-viewer-presets}

Denken Sie daran, dass die Bearbeitung von *vordefinierten, standardmäßig vorhandenen Viewer-Vorgaben* als Szenario nicht unterstützt wird.  Wenn Sie eine standardmäßig vorhandene Viewer-Vorgabe bearbeiten, werden Sie aufgefordert, die Viewer-Vorgabe unter einem neuen Namen zu speichern. 

**So bearbeiten Sie Viewer-Vorgaben** für dynamische Medien:

1. In the upper-left corner of AEM, tap the AEM logo, then in the left rail, tap **[!UICONTROL Tools > Assets > Viewer Presets]**.
1. Wählen Sie eine Vorgabe aus, indem Sie das Kontrollkästchen links neben dem Viewer-Vorgabentitel aktivieren. 
1. Tippen Sie in der Symbolleiste auf **[!UICONTROL Bearbeiten]**.
1. Nehmen Sie auf der Seite **[!UICONTROL Viewer-Vorgabe bearbeiten]** die gewünschten Änderungen an der Viewer-Vorgabe vor. 
1. Führen Sie einen der folgenden Schritte aus:

   * Tap **[!UICONTROL Save]** to save your changes and return to the **[!UICONTROL Viewer Preset]** page.
   * Tap **[!UICONTROL Cancel]** to void any changes you made and return to the **[!UICONTROL Viewer Preset]** page.

## Löschen von benutzerdefinierten Viewer-Vorgaben für dynamische Medien {#deleting-custom-viewer-presets}

Sie können Viewer-Vorgaben löschen, die Sie Dynamic Media erstellt und hinzugefügt haben.

**So löschen Sie benutzerdefinierte Viewer-Vorgaben** für dynamische Medien:

1. In the upper-left corner of AEM, tap the AEM logo, then in the left rail, tap **[!UICONTROL Tools > Assets > Viewer Presets]**.
1. On the **[!UICONTROL Viewer Presets]** page, check a **[!UICONTROL Preset Title]**, and then tap the **[!UICONTROL Trash]** icon.
1. Tippen Sie auf **[!UICONTROL Löschen]**. 

## Applying a Dynamic Media viewer preset to an asset {#applying-a-viewer-preset-to-an-asset}

Wenn Sie das Asset und den ausgewählten Viewer bereits veröffentlicht haben, werden nach Auswahl einer Viewer-Voreinstellung die Schaltflächen **[!UICONTROL URL]** und **[!UICONTROL Einbetten]** angezeigt.

**So wenden Sie eine Viewer-Vorgabe für dynamische Medien auf ein Asset** an

1. Öffnen Sie das Asset, tippen Sie in der Nähe des oberen linken Bereichs der Seite auf das Dropdownmenü und wählen Sie **[!UICONTROL Viewer]** aus.

   >[!NOTE]
   >
   >Wenn Sie das Asset und den ausgewählten Viewer bereits veröffentlicht haben, werden nach Auswahl einer Viewer-Voreinstellung die Schaltflächen **[!UICONTROL URL]** und **[!UICONTROL Einbetten]** angezeigt.

1. Wählen Sie eine Viewer-Vorgabe im linken Bereich aus, um sie auf das Asset anzuwenden. 

   Sie können die [URL kopieren, um sie für andere Benutzer freizugeben](linking-urls-to-yourwebapplication.md). 

## Bereitstellen von Assets mit Viewer-Vorgaben für dynamische Medien {#delivering-assets-with-viewer-presets}

Informationen zum Abrufen der URLs für Viewer-Vorgaben finden Sie unter [Verknüpfen von URLs mit Ihrer Webanwendung](linking-urls-to-yourwebapplication.md). Informationen hierzu finden Sie unter [Einbetten des Video-Viewers auf einer Webseite](embed-code.md).

Wenn Sie AEM als WCM verwenden, können Sie Assets mithilfe der Viewer-Vorgaben direkt auf der Seite hinzufügen.  Siehe [Hinzufügen von Assets mit dynamischen Medien zu Seiten](adding-dynamic-media-assets-to-pages.md). 
