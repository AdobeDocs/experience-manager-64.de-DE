---
title: Verwalten von Dynamic Media-Viewer-Vorgaben
seo-title: Managing Dynamic Media viewer presets
description: Erstellen und Verwalten von Dynamic Media-Viewer-Vorgaben
seo-description: How to create and manage Dynamic Media viewer presets
uuid: 31ef7a4e-2053-43b5-ac6c-cdc4b30c3914
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: e78bb08a-a923-4399-b3f7-13aa4b7994d5
legacypath: /content/docs/en/aem/6-0/administer/integration/dynamic-media/viewer-presets
exl-id: 53e53cb7-1854-44e9-9516-51bcc99378b4
feature: Viewer Presets
role: Admin,User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '4256'
ht-degree: 73%

---

# Verwalten von Dynamic Media-Viewer-Vorgaben {#managing-viewer-presets}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Eine Dynamic Media-Viewer-Vorgabe ist eine Sammlung von Einstellungen, die bestimmen, wie Benutzer Rich-Media-Assets auf ihren Computerbildschirmen und Mobilgeräten anzeigen. Administratoren können Viewer-Vorgaben erstellen. Einstellungen sind für eine Reihe von Viewer-Konfigurationsoptionen verfügbar. Sie können beispielsweise die Viewer-Anzeigegröße oder das Zoom-Verhalten ändern.

Anweisungen zum Erstellen und Anpassen Ihrer eigenen HTML5-Viewer-Vorgaben finden Sie in der Dokumentation zur *HTML5 Viewer SDK API* von Adobe Dynamic Media. Das SDK ist auf dem im SDK selbst eingebetteten IS-Veröffentlichungs-Server verfügbar. Jede Bibliotheksversion verfügt über eine eigene SDK-Dokumentation.

Pfad: `<scene7_domain>/s7sdk/<library_version>/docs/jsdocs/index.html`.\
Beispielsweise das 3.10-SDK: [https://s7d1.scene7.com/s7sdk/3.10/docs/jsdoc/index.html](https://s7d1.scene7.com/s7sdk/3.10/docs/jsdoc/index.html)

Siehe auch das [Adobe Dynamic Media Viewers-Referenzhandbuch](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/homeviewers.html?lang=de).

In diesem Abschnitt wird beschrieben, wie Viewer-Vorgaben erstellt, bearbeitet und verwaltet werden. Sie können jederzeit bei der Vorschau eines Assets eine Viewer-Vorgabe darauf anwenden. Siehe [Anwenden von Viewer-Vorgaben](viewer-presets.md).

>[!NOTE]
>
>Denken Sie daran, dass die Bearbeitung von *vordefinierten, standardmäßig vorhandenen Viewer-Vorgaben* als Szenario nicht unterstützt wird. Wenn Sie versuchen, eine standardmäßig vorhandene Viewer-Vorgabe zu bearbeiten, werden Sie aufgefordert, die Viewer-Vorgabe unter einem neuen Namen zu speichern.

## Möglichkeit des Zugriffs auf die Tastatur im Viewer {#keyboard-accessibility-for-viewers}

Alle standardmäßigen Viewer unterstützen den Zugriff auf die Tastatur.

Weitere Informationen finden Sie unter [Tastaturzugriff und Navigation](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/c-keyboard-accessibility.html?lang=de).

## Verwalten von Dynamic Media-Viewer-Vorgaben {#managing-presets}

Sie können Viewer-Vorgaben in AEM hinzufügen, bearbeiten, löschen, veröffentlichen, Veröffentlichung rückgängig machen und eine Vorschau davon anzeigen, indem Sie auf **[!UICONTROL Tools > Assets > Viewer-Vorgaben]**.

![tools-assets](assets/tools-assets.png)

>[!NOTE]
>
>Standardmäßig zeigt das System 15 Viewer-Vorgaben, wenn Sie in einer Detailansicht eines Assets „Viewer“ auswählen. Sie können diese Grenze erhöhen. Siehe [Erhöhen der Anzahl angezeigter Viewer-Vorgaben](#increasing-the-number-of-viewer-presets-that-display).

## Viewer-Unterstützung für Web-Seiten mit responsivem Design {#viewer-support-for-responsive-designed-web-pages}

Unterschiedliche Web-Seiten haben unterschiedliche Anforderungen. Mitunter möchten Sie vielleicht, dass eine Web-Seite über einen Link verfügt, der den HTML5-Viewer in einem separaten Browser-Fenster öffnet. In anderen Fällen kann es aber auch erforderlich sein, den HTML5-Viewer direkt auf der Host-Seite einzubetten. In letzterem Fall kann die Web-Seite ein statisches Layout aufweisen. Oder es kann *responsiv* und werden auf verschiedenen Geräten oder für unterschiedliche Browser-Fenstergrößen unterschiedlich angezeigt. Um all diese Anforderungen zu berücksichtigen, unterstützen sämtliche vordefinierten, standardmäßig vorhandenen HTML5-Viewer, die mit Dynamic Media bereitgestellt werden, sowohl statische als auch responsive Web-Seiten.

Weitere Informationen zum Einbetten responsiver Viewer auf Web-Seiten finden Sie unter [Bibliothek responsiver Bilder](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/responsive-static-image-library/c-about-responsive-static-image-library.html?lang=de) in der *Image Serving-API-Hilfe*.

>[!NOTE]
>
>Sie müssen zunächst alle standardmäßig vorhandenen Viewer veröffentlichen, um sie verwenden zu können.\
>Siehe [Veröffentlichen von Viewer-Vorgaben](#publishing-viewer-presets).

## Systemkompatibilität von Viewer-Vorgaben  {#viewer-preset-system-compatibility}

Alle standardmäßig vorhandenen Viewer-Vorgaben, die mit Dynamic Media bereitgestellt werden, sind mit den folgenden Systemen vollständig kompatibel:

* Desktops
* Apple iPhones
* Apple iPads
* Android-Smartphones
* Android-Tablets
* Für Videos wird zusätzliche Unterstützung für die MP4-Wiedergabe bereitgestellt für [BlackBerry](https://developer.blackberry.com/devzone/develop/supported_media/bb_media_support_at_a_glance.html#kba1328730952678) und [Windows Phone 8](https://msdn.microsoft.com/library/windows/apps/ff462087%28v=vs.105%29.aspx).

### Rich-Media-Typen für Viewer-Vorgaben {#rich-media-types-for-viewer-presets}

Administratoren können bei der Erstellung von Viewer-Vorgaben die folgenden Rich-Media-Typen hinzufügen und anpassen.

| Rich-Media-Typen | Beschreibung |
|:---|:---|
| **Karussellset** | Hotspots, Imagemaps oder beide werden zu einer Serie von mindestens zwei Bildern hinzugefügt. Kunden können einen Bildschwenk nach links oder rechts durchführen und dann auf einen Hotspot auf einem Bild klicken, um zusätzliche Details aufzurufen oder direkt über eine Kategorie-, Start- oder Landingpage einer Website zu kaufen. |
| **Flyout-Zoom** | Zeigt ein zweites Bild des gezoomten Bereichs neben dem Originalbild an. Es gibt dazu keine Steuerelemente, sondern die Auswahl muss über den Bereich verschoben werden, der angezeigt werden soll. |
|  | Beachten Sie bei der Bestimmung der vollständigen Bandbreitennutzung für diesen Viewer, dass sowohl das Hauptbild als auch das Flyout-Bild im Viewer angezeigt werden. Die Größe des Hauptbilds (Stage-Breite und -Höhe) und der Zoom-Faktor bestimmen die Größe des Flyout-Bildes. Damit die Flyout-Datei nicht zu groß wird, sollten Sie diese beiden Werte ausgleichen: Wenn Sie eine große Hauptbildgröße haben, senken Sie den Wert des Zoom-Faktors. (Die Flyout-Breite und Flyout-Höhe bestimmen die Größe des Flyout-Fensters, jedoch nicht die Größe des Flyout-Bildes, das für den Viewer bereitgestellt wird.) |
|  | Wenn die Größe des Hauptbilds beispielsweise 350 x 350 Pixel bei einem Zoom-Faktor von 3 beträgt, misst das resultierende Flyout-Bild 1050 x 1050 Pixel. Wenn die Größe des Hauptbilds 300 x 300 Pixel bei einem Zoomfaktor von 4 beträgt, umfasst das Flyout-Bild 1200 x 1200 Pixel. Je nach JPEG-Qualitätseinstellung (empfohlene Einstellungen sind zwischen 80 und 90) können Sie die Dateigröße erheblich verringern. Je nach Größe des Hauptbilds werden Zoom-Faktoren von 2,5 bis 4 empfohlen. |
| **Inline-Zoom** | Zeigt ein Bild des gezoomten Bereichs im Original-Viewer an. Es stehen keinerlei Steuerelemente zur Verfügung. Benutzer verschieben vielmehr die Auswahl über den Bereich, der angezeigt werden soll. |
| **Bildset** | Im Bildset-Viewer können Benutzer unterschiedliche Ansichten oder Farbvariationen eines Elements sehen, indem sie auf eine Miniaturansicht klicken. Dieser Viewer bietet auch Zoomtools, mit denen Bilder genauer untersucht werden können. |
| **Interaktives Bild** | Hotspots werden zu Teilmengen eines Bildes hinzugefügt, auf die ein Kunde anschließend klicken kann, um zusätzliche Informationen zu erhalten oder den Kauf direkt über die Kategorie einer Website, über die Startseite oder Landingpages vorzunehmen. |
| **Interaktives Video** | Miniaturansichten werden Zeitleistensegmenten in einem Video hinzugefügt, auf die ein Kunde anschließend klicken kann, um zusätzliche Informationen zu erhalten oder den Kauf direkt über die Kategorie einer Website, über die Startseite oder Landingpages vorzunehmen. |
| **Gemischte Medien** | Zeigt unterschiedliche Medientypen in einem Viewer an. Dort können Sie Rotationssets, Bildsets, Bilder und Videos aufnehmen. |
| **Panoramabild** | Die Viewer für Panoramabilder und PanoramaVR rendern kugelförmige Panoramabilder, um ein 360°-Zuschauererlebnis eines Raums, einer Eigenschaft, eines Standorts oder einer Landschaft zu erzielen. |
|  | Damit ein hochgeladenes Bild als Kugelpanorama gilt, muss es entweder eine oder beide der folgenden Eigenschaften aufweisen: <ul><li>Ein Seitenverhältnis von 2:1.</li><li>Mit den Keywords equirechteckig, kugelförmig und panorama oder kugelförmig und panoramisch getaggt. Weitere Informationen finden Sie unter [Verwenden von Tags](../sites-authoring/tags.md).</li></ul> |
|  | Sowohl das Kriterium für das Seitenverhältnis als auch das für die Keywords gelten für Panorama-Assets für die Asset-Detailseite und die WCM-Komponente für „Panoramamedien“. |
|  | Wichtig: Dieser Viewer ist nur im Scene7-Modus von Dynamic Media verfügbar. |
| **Rotationsset** | Stellt mehrere Ansichten eines Bildes bereit, sodass Benutzer den Gegenstand drehen können, um ihn von allen Seiten zu betrachten. |
| **Video** | Gibt Videos mit progressivem oder adaptivem Bit-Rate-Streaming wieder. Beim adaptiven Bit-Rate-Streaming wird automatisch eine Geräte- und Bandbreitenerkennung durchgeführt, um das richtige Video in der richtigen Qualität und im richtigen Format bereitzustellen. |
| **Vertikaler Zoom** | Mit dem Viewer für vertikalen Zoom können Sie das Anzeigeerlebnis von Produktbildern maximieren, um Ihrem Publikum die bestmögliche Darstellung eines Produkts zu bieten. Die vertikale Position von Farbfeldern bewirkt Folgendes: <ul><li>Stellt sicher, dass die Farbfelder über der Kante liegen. Bei horizontalen Farbfeldern waren die Farbfelder je nach Bildschirmgröße des Benutzers auf dem Desktop  erst sichtbar, wenn der Benutzer einen Bildlauf auf der Seite nach unten ausgeführt hat. Durch die vertikale Platzierung der Farbfelder im Viewer wird sichergestellt, dass sie unabhängig von der Bildschirmgröße der Benutzenden sichtbar sind.</li><li>Maximiert die Größe des Hauptbilds. Bei horizontalen Farbfeldern muss Platz auf der Seite eingeplant werden, um sicherzustellen, dass sie sichtbar sind. Durch diese Positionierung wird die Größe des Hauptbilds verringert. Bei einem vertikalen Farbfeld-Layout ist das Einplanen dieses Bereichs jedoch nicht erforderlich. Daher können Sie die Größe des Hauptbilds maximieren.</li></ul> |
| **Zoom** | Ermöglicht Benutzern das Vergrößern des Bereichs durch Klicken darauf. Benutzer können auf Steuerelemente klicken, um ein- und auszuzoomen und das Bild auf die Standardgröße zurückzusetzen. |

## Liste der standardmäßig vorhandenen Viewer-Vorgaben {#list-of-out-of-the-box-viewer-presets}

In der folgenden Tabelle sind alle vordefinierten, standardmäßig vorhandenen Viewer-Vorgaben aufgeführt, die in Dynamic Media enthalten sind.

Siehe auch [Live-Demos](https://landing.adobe.com/en/na/dynamic-media/ctir-2755/live-demos.html).

Informationen zu unterstützten Webbrowsern und Betriebssystemversionen für Viewer finden Sie in den Viewer-Versionshinweisen.

Siehe *Versionshinweise zu Viewers* im Inhaltsverzeichnis der [Viewer-Referenzhandbuch](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/homeviewers.html?lang=de).

>[!NOTE]
>
>Alle standardmäßig vorhandenen Viewer-Vorgaben in Dynamic Media sind bereits aktiviert. Sie müssen sie allerdings noch veröffentlichen.\
>Siehe [Veröffentlichen von Viewer-Vorgaben](#publishing-viewer-presets).
>
>Alle neuen Viewer-Vorgaben, die Sie erstellen und hinzufügen, müssen beide aktiviert sein *und* veröffentlicht.\
>Siehe [Aktivieren oder Deaktivieren von Viewer-Vorgaben](#activating-or-deactivating-viewer-presets) und [Veröffentlichen von Viewer-Vorgaben](#publishing-viewer-presets).

| Viewer-Vorgabentitel | Typ | CSS-Dateiname |
|:---|:---|:---|
| Carousel_Dotted_dark | Carousel_Set | html5_carouselviewer_dotted_dark.css |
| Carousel_Dotted_light | Carousel_Set | html5_carouselviewer_dotted_light.css |
| Carousel_Numeric_dark | Carousel_Set | html5_carouselviewer_numeric_dark.css |
| Carousel_Numeric_light | Carousel_Set | html5_carouselviewer_numeric_light.css |
| Flyout | Flyout_Zoom | html5_flyoutviewer.css |
| ImageSet_dark | Bildset | html5_zoomviewer_dark.css |
| ImageSet_light | Bildset | html5_zoomviewer_light.css |
| InlineMixedMedia_dark | Mixed_Media | html5_inlinemixedmediaviewer_dark.css |
| InlineMixedMedia_light | Mixed_Media | html5_inlinemixedmediaviewer_light.css |
| InlineZoom | Flyout_Zoom | html5_inlinezoomviewer.css |
| MixedMedia_dark | Mixed_Media | html5_mixedmediaviewer_dark.css |
| MixedMedia_light | Mixed_Media | html5_mixedmediaviewer_light.css |
| PanoramicImage | Panoramic_image | html5_panoramicimage.css |
| PanoramicImageVR | Panoramic_image | html5_panoramicimage.css |
| Shoppable_Banner | Interactive_Image | html5_interactiveimage.css |
| Shoppable_Video_dark | Interactive_Video | html5_interactivevideoviewer_dark.css |
| Shoppable_Video_light | Interactive_Video | html5_interactivevideovewer_light.css |
| SpinSet_dark | Spin_Set | html5_spinviewer_dark.css |
| SpinSet_light | Spin_Set | html5_spinviewer_light.css |
| Video (einschließlich Unterstützung für Untertitel) | Video  | html5_videoviewer.css |
| Video_social (einschließlich Unterstützung für Untertitel und soziale Medien) | Video  | html5_videoviewersocial.css |
| Zoom_dark | Zoom | html5_basiczoomviewer_dark.css |
| Zoom_light | Zoom | html5_basiczoomviewer_light.css |
| ZoomVertical_dark | Vertical_Zoom | html5_zoomverticalviewer_dark.css |
| ZoomVertical_light | Vertical_Zoom | html5_zoomverticalviewer_light.css |

### Matrix unterstützter Mobile-Viewer-Gesten {#supported-mobile-viewers-gestures-matrix}

In der folgenden Tabelle werden die Mobile Viewer-Gesten aufgeführt, die auf iOS-, Android 2.x- und Android 3.x-Geräten unterstützt werden.

| Geste | Flyout-Zoom | Zoom | Drehung |
|---|---|---|---|
| **Ziehen** | Schwenkt | Schwenkt | Schwenkt |
| **Tippen** | Blendet Flyout-Fenster ein | Blendet die Benutzeroberfläche ein oder aus | Blendet die Benutzeroberfläche ein oder aus |
| **Doppeltippen** | Trifft nicht zu | Zoomt ein oder setzt zurück | Zoomt ein oder setzt zurück |
| **Aufziehen** | Trifft nicht zu | Zoomt ein (nur iOS und Android 3x) | Zoomt ein (nur iOS und Android 3x) |
| **Zuziehen** | Trifft nicht zu | Zoomt aus (nur iOS und Android 3x) | Zoomt aus (nur iOS und Android 3x) |
| **Streichen** | Scrollt Farbfeldleiste | Scrollt Bilder | Dreht |
| **Schnippen** | Scrollt Farbfeldleiste | Scrollt Bilder | Dreht |

## Erhöhen der Anzahl angezeigter Dynamic Media-Viewer-Vorgaben {#increasing-the-number-of-viewer-presets-that-display}

AEM zeigt verschiedene Viewer-Vorgaben an, wenn Sie ein Asset unter **[!UICONTROL Detailansicht > Viewer]** anzeigen. Sie können die Anzahl der angezeigten Viewer erhöhen oder verringern.

**So erhöhen Sie die Anzahl der angezeigten Dynamic Media-Viewer-Vorgaben**:

1. Navigieren Sie zu **[!UICONTROL CRXDE Lite]** ([http://localhost:4502/crx/de](http://localhost:4502/crx/de)).
1. Navigieren Sie zum Knoten mit der Viewer-Vorgabenliste unter `/libs/dam/gui/coral/content/commons/sidepanels/viewerpresets/viewerpresetslist`

   ![chlimage_1-221](assets/chlimage_1-221.png)

1. Ändern Sie für die Eigenschaft **[!UICONTROL limit]** den **[!UICONTROL Wert]**, für den standardmäßig 15 festgelegt ist, in einen höheren Wert.
1. Navigieren Sie zur Datenquelle der Viewer-Vorgabe unter `/libs/dam/gui/coral/content/commons/sidepanels/viewerpresets/viewerpresetslist/datasource`

   ![chlimage_1-222](assets/chlimage_1-222.png)

1. Im **[!UICONTROL limit]** -Eigenschaft, ändern Sie die Zahl in die gewünschte Zahl, z. B. `{empty requestPathInfo.selectors[1] ? "20" : requestPathInfo.selectors[1]}`
1. Tippen Sie auf **[!UICONTROL Alle speichern]**.

## Erstellen einer neuen Dynamic Media-Viewer-Vorgabe {#creating-a-new-viewer-preset}

Durch Erstellen von Viewer-Vorgaben können Sie verschiedene Einstellungen anwenden, um Assets anzuzeigen und mit diesen zu interagieren. Sie müssen jedoch keine neuen Viewer-Vorgaben erstellen. Wenn Sie dies bevorzugen, können Sie auch die bereits standardmäßig in AEM Assets verfügbaren Viewer-Vorgaben verwenden.

Wenn Sie eine neue Viewer-Vorgabe erstellen möchten, wird nach deren Speicherung der Viewer-Status auf der Seite „Viewer-Vorgaben“ automatisch aktiviert (auf **Ein** gesetzt). **** Dieser Status bedeutet, dass er im **[!UICONTROL Dynamic Media]** und **[!UICONTROL Interaktive Medien]** und jedes Mal, wenn Sie eine Vorschau eines Bildes oder Videos anzeigen.

Bestimmte Viewer-Vorgaben weisen exklusive Einstellungen auf, die die Nutzung und das Gesamtverhalten des Viewers beeinflussen können. Je nach der von Ihnen erstellten Viewer-Vorgabe sollten Sie diese besonderen Hinweise berücksichtigen.

Siehe [Besondere Hinweise zum Erstellen von Vorgaben für interaktive Viewer](#special-considerations-for-creating-an-interactive-viewer-preset).

Siehe [Besondere Hinweise zum Erstellen von Viewer-Vorgaben für Karussellbanner](#special-considerations-for-creating-a-carousel-banner-viewer-preset).

**So erstellen Sie eine neue Dynamic Media-Viewer-Vorgabe**:

1. Tippen Sie in der linken oberen Ecke von AEM auf das AEM-Logo und tippen Sie dann in der linken Leiste auf **[!UICONTROL Tools > Assets > Viewer-Vorgaben]**.

   ![Viewer-Vorgaben](assets/viewerpresets.png)

1. Im **[!UICONTROL Viewer-Vorgaben]** Seite, tippen Sie in der Symbolleiste auf **[!UICONTROL Erstellen]**.
1. Geben Sie im Dialogfeld **[!UICONTROL Neue Viewer-Vorgabe]** in das Feld **[!UICONTROL Vorgabename]** den Namen der neuen Vorgabe ein. Achten Sie darauf, einen Namen zu wählen, der nach dem Tippen nicht mehr bearbeitet werden kann. **[!UICONTROL Erstellen]**.

   Wenn Sie die Vorgabe später in diesen Schritten speichern, wird der Name auf der Seite &quot;Viewer-Vorgaben&quot;unter der **[!UICONTROL Vorgabentitel]** Spaltenüberschrift.

1. Im **[!UICONTROL Rich-Media-Typ]** Dropdown-Menü den Typ der zu erstellenden Viewer-Vorgabe auswählen und dann oben rechts auf der Seite auf tippen. **[!UICONTROL Erstellen]**.

   Siehe [Rich-Media-Typen für Viewer-Vorgaben](#rich-media-types-for-viewer-presets).

1. Im **Viewer-Vorgabe bearbeiten** Seite, tippen Sie auf **[!UICONTROL Erscheinungsbild]** Registerkarte.
1. Führen Sie einen der folgenden Schritte aus:

   * Wählen Sie aus dem Pulldown-Menü **[!UICONTROL Ausgewählter Typ]** eine Komponente aus, deren visuelles Design angepasst werden soll. Alternativ können Sie auf ein beliebiges visuelles Element im Viewer tippen, um es zur Konfiguration auszuwählen.

      Der Visual Editor zeigt Ihnen, wie sich eine bestimmte Eigenschaft auf einen Stil auswirkt. Legen Sie eine beliebige Eigenschaft fest bzw. passen Sie diese an, um sofort anhand des Beispiels auf der linken Seite des Editors zu sehen, wie sich dies auf den Viewer auswirkt.

      Die CSS-Stileigenschaften für jeden Viewer-Vorgabetyp werden im Abschnitt &quot;Anpassen von *&lt;viewer_name>* Hilfethema &quot;Viewer&quot;im [Viewer-Referenzhandbuch](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/homeviewers.html?lang=de).

      Wenn Sie z. B. eine Viewer-Vorgabe vom Typ `Mixed_Media` erstellen, finden Sie im Thema zum [Anpassen von Viewern für gemischte Medien](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/mixed-media/customing-mixed-media/c-html5-mixedmedia-viewer-customizingviewer.html?lang=de) eine Aufstellung und Beschreibung jeder Eigenschaft.

   * Wenn Stileinstellungen in einer separaten CSS-Datei definiert sind, können Sie die CSS-Datei in AEM Assets hochladen. Tippen Sie auf **[!UICONTROL CSS importieren]** unter dem Pulldown-Menü **[!UICONTROL Ausgewählter Typ]** (ggf. müssen Sie hierzu einen Bildlauf im Visual Editor durchführen), um nach der hochgeladenen CSS-Datei zu suchen und diese mit der Viewer-Vorgabe zu verknüpfen.

      Beim Importieren einer CSS-Datei überprüft der Visual Editor, ob CSS die korrekten Viewer-Markierungen verwendet. Wenn Sie etwa einen Zoom-Viewer erstellen, müssen alle CSS-Regeln, die Sie importieren, mit dem zugehörigen Viewer-Klassennamen `.s7mixedmediaviewer` (definiert in einem übergeordneten Viewer-Element) festgelegt werden.

      Sie können beliebige, selbst definierte CSS-Dateien importieren, solange diese die CSS-Markierungen für den jeweiligen Viewer ordnungsgemäß definieren. (CSS-Markierungen werden im Hilfethema „Anpassen des *&lt;Viewer-Name>*-Viewers“ im [Viewers-Referenzhandbuch](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/homeviewers.html?lang=de) erläutert. Wenn Sie beispielsweise mehr über CSS-Markierungen für den Zoom-Viewer erfahren möchten, lesen Sie den Abschnitt [Anpassen des Zoom-Viewers](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/zoom/customizing-zoom/c-html5-20-zoom-viewer-customizingviewer.html?lang=de).) Es ist jedoch möglich, dass der Visual Editor nicht alle CSS-Werte versteht. In diesem Fall versucht der Visual Editor, die Fehler zu überschreiben, damit CSS nach wie vor verwendet werden kann.
   >[!NOTE]
   >
   >Wenn Sie CSS lieber direkt im Rohformat bearbeiten möchten, tippen Sie im Pulldown-Menü „Ausgewählter Typ“ auf **[!UICONTROL CSS ein-/ausblenden]** (Sie müssen ggf. im Visual Editor nach oben blättern, um diese Option anzuzeigen).****
   >
   >Wenn Sie eine Eigenschaft direkt in CSS ändern, können Sie wie im Visual Editor sofort sehen, wie sich dies auf das Viewer-Beispiel auswirkt. Außerdem wird zur gleichen Zeit genau diese Eigenschaft automatisch im Visual Editor aktualisiert. Daher können Sie entweder den CSS-Editor, den Visual Editor oder beide abwechselnd verwenden.

   >[!NOTE]
   >
   >Für Schaltflächengrafiken wählen Sie das 2x-Bild aus und laden Sie Grafiken mit hoher Auflösung hoch. Beim Arbeiten mit interaktiven Bildern und Bannern mit Einkaufsfunktion können Sie auch aus verschiedenen standardmäßig vorhandenen Hotspot-Schaltflächen wählen.

1. (Optional) Oben im **[!UICONTROL Viewer-Vorgabe bearbeiten]** Seite, tippen Sie auf **[!UICONTROL Desktop]**, **[!UICONTROL Tablette]** oder **[!UICONTROL Telefon]** um visuelle Stile für verschiedene Geräte- und Bildschirmtypen eindeutig zu definieren.
1. Im **[!UICONTROL Viewer-Vorgabe bearbeiten]** Seite, tippen Sie auf **Verhalten** Registerkarte. Sie können auch auf ein beliebiges visuelles Element im Viewer tippen oder klicken, um es zum Konfigurieren auszuwählen.
1. Wählen Sie im Pulldown-Menü **[!UICONTROL Ausgewählter Typ]** eine Komponente aus, deren Verhalten Sie ändern möchten.

   Viele Komponenten im Visual Editor sind mit einer detaillierten Beschreibung verknüpft. Diese Beschreibungen werden in blauen Feldern angezeigt, wenn Sie eine Komponente zum Anzeigen der mit ihr verknüpften Parameter einblenden.

   Einige Viewer-Typen verfügen über Komponenten, mit denen Sie Befehle zum Image Serving in einem **IS-Befehl**-Textfeld angeben können. Eine Liste der verfügbaren Befehle finden Sie in der [Image Serving API-Referenz](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/c-is-home.html?lang=de).

   >[!NOTE]
   >
   >**Bei Nutzung eines Touch-Geräts, etwa eines Smartphones oder Tablets:**
   >
   >Nachdem Sie einen Wert in das Textfeld eingegeben haben, tippen Sie an einer anderen Stelle in der Benutzeroberfläche, um die Änderung zu senden und die virtuelle Tastatur zu schließen. Wenn Sie auf **[!UICONTROL Eingabe]**, keine Aktion erfolgt.

1. Tippen Sie oben rechts auf **[!UICONTROL Speichern]**.
1. Veröffentlichen Sie die neue Viewer-Vorgabe. Sie müssen die Vorgabe veröffentlichen, um sie auf Ihrer Website verwenden zu können.

   Siehe [Veröffentlichen von Viewer-Vorgaben](#publishing-viewer-presets).

## Besondere Hinweise zum Erstellen von Viewer-Vorgaben für interaktive Videos {#special-considerations-for-creating-an-interactive-viewer-preset}

**Über Anzeigemodi für Bildminiaturansichten im Anzeigefeld**

Wenn Sie eine Viewer-Vorgabe für interaktive Videos erstellen oder bearbeiten, können Sie entscheiden, **[!UICONTROL Anzeigemodus]** Einstellung, die bei Auswahl von `InteractiveSwatches` von **[!UICONTROL Ausgewählte Komponente]** Pulldown-Menü unter **[!UICONTROL Verhalten]** Registerkarte. Der von Ihnen gewählte Anzeigemodus beeinflusst, wie und wann Miniaturansichten während der Videowiedergabe angezeigt werden. Sie können entweder den Anzeigemodus `segment` (Standard) oder den Anzeigemodus `continuous` auswählen.

| Anzeigemodus | Beschreibung |
|---|---|
| [!UICONTROL Segment] | [!UICONTROL Segment] ist der Standardanzeigemodus für die standardmäßig vorhandenen Viewer-Vorgaben für interaktive Videos Shoppable_Video_light und Shoppable_Video_dark sowie alle Viewer-Vorgaben für interaktive Videos, die Sie selbst erstellen. |
|  | Wenn einem Videosegment weniger Miniaturansichten als sichtbare Spots im Anzeigefeld zugewiesen sind, werden in diesem Modus Miniaturansichten von den nächsten oder vorhergehenden Untersegmenten nicht herangezogen, um leere Spots im Feld aufzufüllen. So bleibt die Anzeige von einem bestimmten Videosegment zugewiesenen Mustern erhalten. |
| [!UICONTROL Kontinuierlich] | In [!UICONTROL Kontinuierlich] Anzeigemodus: Wenn die Anzahl der Miniaturansichten in einem Segment kleiner ist als die Anzahl, die im Bedienfeld sichtbar ist, schließt der Viewer in den Fällen, in denen die letzte Miniaturansicht angezeigt wird, automatisch die Anzeige von Miniaturansichten aus dem nächsten oder vorherigen Segment ein. |

**Informationen zum automatischen Bildlauf im Viewer für interaktive Videos**

Das automatische Bildlaufverhalten von Miniaturen der Viewer-Funktionen für interaktive Videos erfolgt unabhängig vom gewählten Anzeigemodus.

Wenn Sie eine interaktive Video-Viewer-Vorgabe erstellen oder bearbeiten, greifen Sie auf **[!UICONTROL Auto-Bildlauf]** von **[!UICONTROL Verhalten]** Registerkarte. Tippen Sie auf der Registerkarte „Verhalten“ im Dropdown-Menü **[!UICONTROL Ausgewählte Komponenten]** auf **[!UICONTROL InteractiveSwatches]**. Die **[!UICONTROL Auto-Bildlauf]** wird unter dem Textfeld IS-Befehl aufgeführt.

Wenn Sie in der Viewer-Vorgabe bei der Videowiedergabe durch den Benutzer die Option **[!UICONTROL Automatischer Bildlauf]** deaktivieren (das Kontrollkästchen abwählen), wird im Feld während der gesamten Videodauer nur das erste Miniaturbild angezeigt. Allerdings kann der Benutzer ggf. mithilfe der Pfeilsymbole nach oben und nach unten einen manuellen Bildlauf durch die Miniaturen durchführen.

Wenn Sie während der Videowiedergabe die Option **[!UICONTROL Automatischer Bildlauf]** in der Viewer-Vorgabe aktivieren (auswählen), werden die Miniaturbilder, die einem Videosegment zugewiesen sind, zu Beginn eines Segments in die Ansicht verschoben. Es gibt jedoch Fälle, in denen bestimmte Miniaturen innerhalb eines Segments doppelt so lange angezeigt werden wie andere Miniaturen vor oder nach dem Segment. Dieses Verhalten tritt auf, weil die Anzahl der Miniaturen in einem Segment größer ist als die Zahl, die im Bedienfeld sichtbar ist, und diese nicht gleichmäßig teilbar ist.

Gehen wir zu Illustrationszwecken von einem 30 Sekunden langen Videosegment aus. Insgesamt gibt es neun Miniaturansichten, die im Laufe dieser 30 Sekunden angezeigt werden. Die Größe Ihres Browsers wird dergestalt geändert, dass vier verfügbare Miniaturpositionen im Anzeigefeld vorliegen. Das 30-sekündige Videozeitsegment ist in drei Untersegmente unterteilt. In der folgenden Tabelle wird aufgeschlüsselt, welche Miniaturansichten für ein bestimmtes Zeituntersegment angezeigt werden:

| **Video-Untersegment** | **Zeit des Untersegments in Sekunden** | **Im Feld sichtbare Miniaturen** |
|---|---|---|
| 1 | 0–10 | 1, 2, 3, 4 |
| 2 | 10-20 | 4, 5, 6, 7 |
| 3 | 20-30 | 6, 7, 8, 9 |

Das Videountersegment 3 wird nicht über die Miniaturansichten hinweg erweitert, die ihm zugewiesen sind. Beachten Sie, dass die Miniaturen 4, 6 und 7 im Anzeigefeld doppelt so lang sichtbar sind wie die anderen.

Die durch den Viewer zum Bestimmen der Anzahl der im seitlichen Bedienfeld angezeigten Miniaturen verwendete Logik basiert wie folgt auf der Anzahl der verfügbaren Positionen:

* Anzahl der Untersegmente = Aufrundung auf das nächste Untersegment (Anzahl der Miniaturansichten: Anzahl der sichtbaren Spots im Miniaturansichtsfeld, auf Grundlage der Browser-Fenstergröße)


   Unter Verwendung des Beispiels in der obigen Tabelle ergibt 9 Miniaturansichten: 4 Slots = 2,25, was die Viewer-Logik auf 3 Untersegmente aufrundet.

* Anzahl der Miniaturen = Aufrundung auf die nächste Miniaturansicht (Anzahl der Miniaturansichten: Anzahl der Videountersegmente)


   Unter Verwendung des Beispiels in der obigen Tabelle ergibt 9 Miniaturansichten: 3 Videountersegmente = 3 Miniaturansichten.

* Dauer des Untersegments = gesamte Videodauer: Anzahl der Videountersegmente


   Unter Verwendung des Beispiels in der obigen Tabelle ergibt 30 Sekunden: 3 Segmente = 10 Sekunden anhaltende Anzeige jedes Segments.

### Besondere Hinweise zum Erstellen einer Viewer-Vorgabe für Karussellbanner {#special-considerations-for-creating-a-carousel-banner-viewer-preset}

Beim Erstellen von Viewer-Vorgaben für Karussellbanner kann der Stil von Hotspots wie folgt geändert werden:

|  | **Beschreibung** | **Aktionen** |
|---|---|---|
| **Hotspot-Symbol** | Ändern des für Hotspots verwendeten Symbols | Um das Bild des Hotspot-Symbols zu ändern, tippen Sie auf der Registerkarte **[!UICONTROL Erscheinungsbild]** in **[!UICONTROL Ausgewählte Komponente]** auf **[!UICONTROL ImageMapEffect]**. Wählen Sie unter **[!UICONTROL Symbol]** die Option **[!UICONTROL Hintergrund]** und navigieren Sie im Feld **[!UICONTROL Bild]** zum gewünschten Hintergrundbild. |

## Aktivieren oder Deaktivieren von Dynamic Media-Viewer-Vorgaben {#activating-or-deactivating-viewer-presets}

Welche Viewer-Vorgaben in der Benutzeroberfläche verfügbar sind, hängt davon ab, welche im Autorenmodus aktiv sind. Standardmäßig ist eine Viewer-Vorgabe *on* nach der Erstellung. Wenn Sie die Vorgabe deaktivieren, wird sie nicht im Autorenmodus angezeigt. Wenn die Vorgabe veröffentlicht wurde. Es wird immer veröffentlicht, unabhängig davon, ob es ein- oder ausgeschaltet ist. Sie können Viewer-Vorgaben deaktivieren, wenn die Liste zu schwierig wird oder wenn keine Viewer-Vorgabe zur Verfügung gestellt werden soll.

**So aktivieren oder deaktivieren Sie Dynamic Media-Viewer-Vorgaben**:

1. Tippen Sie in der linken oberen Ecke von AEM auf das AEM-Logo und tippen Sie dann in der linken Leiste auf **[!UICONTROL Tools > Assets > Viewer-Vorgaben]**.
1. Im **[!UICONTROL Viewer-Vorgabe]** Seite, unter der **[!UICONTROL state]** -Spaltenüberschrift tippen Sie auf den Umschalter, um eine Viewer-Vorgabe zu aktivieren oder zu deaktivieren.

   Bei aktivierten Viewer-Vorgaben wird die Umschaltfläche rechts in einem blauen Feld angezeigt; bei deaktivierten Viewer-Vorgaben wird die Umschaltfläche links in einem hellgrauen Feld angezeigt.

## Veröffentlichen von Dynamic Media-Viewer-Vorgaben {#publishing-viewer-presets}

Aktivieren (oder Drehen) *on*) bedeutet der Status einer Viewer-Vorgabe, dass sie in der Dynamic Media-Komponente, der interaktiven Medienkomponente und immer dann sichtbar ist, wenn Sie ein Asset anzeigen.

Um jedoch ein Asset mit einer Viewer-Vorgabe bereitzustellen, muss die Viewer-Vorgabe auch veröffentlicht werden. Alle Viewer-Vorgaben müssen aktiviert *und* veröffentlicht werden, um die URL oder den Einbettungs-Code für ein Asset zu beziehen. Sie müssen alle im Lieferumfang von Dynamic Media enthaltenen sofort einsetzbaren Viewer-Voreinstellungen aktivieren und veröffentlichen. Benutzerdefinierte Viewer-Voreinstellungen, die Sie erstellen und hinzufügen, werden automatisch aktiviert, müssen aber auch veröffentlicht werden.

Siehe [Aktivieren oder Deaktivieren von Viewer-Vorgaben](#activating-or-deactivating-viewer-presets).

Weitere Informationen finden Sie unter [Vorschau von Assets](previewing-assets.md).

**So veröffentlichen Sie Dynamic Media-Viewer-Vorgaben**:

1. Tippen Sie in der linken oberen Ecke von AEM auf das AEM-Logo und tippen Sie dann in der linken Leiste auf **[!UICONTROL Tools > Assets > Viewer-Vorgaben]**.
1. Wählen Sie eine oder mehrere Viewer-Vorgaben zum Veröffentlichen aus.
1. Tippen Sie in der Symbolleiste auf **[!UICONTROL Veröffentlichen]** Symbol.

## Sortieren von Dynamic Media-Viewer-Vorgaben {#sorting-viewer-presets}

**So sortieren Sie Dynamic Media-Viewer-Vorgaben**:

1. Tippen Sie in der linken oberen Ecke von AEM auf das AEM-Logo und tippen Sie dann in der linken Leiste auf **Tools** (Hammersymbol) **[!UICONTROL > Assets > Viewer-Vorgaben]**.
1. Klicken Sie auf **[!UICONTROL Vorgabentitel]**, **[!UICONTROL Typ]**, **[!UICONTROL Veröffentlicht]** oder **[!UICONTROL Status]**, um nach dieser Spaltenüberschrift zu sortieren. Klicken Sie beispielsweise auf **[!UICONTROL Typ]**, um die Viewer-Vorgabentypen in alphabetischer oder in umgekehrt alphabetischer Reihenfolge zu sortieren.

## Bearbeiten von Dynamic Media-Viewer-Vorgaben {#editing-viewer-presets}

Denken Sie daran, dass die Bearbeitung von *vordefinierten, standardmäßig vorhandenen Viewer-Vorgaben* als Szenario nicht unterstützt wird. Wenn Sie eine standardmäßig vorhandene Viewer-Vorgabe bearbeiten, werden Sie aufgefordert, die Viewer-Vorgabe unter einem neuen Namen zu speichern.

**So bearbeiten Sie Dynamic Media-Viewer-Vorgaben**:

1. Tippen Sie in der linken oberen Ecke von AEM auf das AEM-Logo und tippen Sie dann in der linken Leiste auf **[!UICONTROL Tools > Assets > Viewer-Vorgaben]**.
1. Wählen Sie eine Vorgabe aus, indem Sie das Kontrollkästchen links neben dem Viewer-Vorgabentitel aktivieren.
1. Tippen Sie in der Symbolleiste auf **[!UICONTROL Bearbeiten]**.
1. Im **[!UICONTROL Viewer-Vorgabe bearbeiten]** -Seite nehmen Sie die Änderungen an der Viewer-Vorgabe vor.
1. Führen Sie einen der folgenden Schritte aus:

   * Tippen Sie auf **[!UICONTROL Speichern]**, um Ihre Änderungen zu speichern und zur Seite „Viewer-Vorgabe“ zurückzukehren.****
   * Tippen Sie auf **[!UICONTROL Abbrechen]**, um alle von Ihnen vorgenommenen Änderungen rückgängig zu machen und zur Seite „Viewer-Vorgaben“ zurückzukehren.****

## Löschen benutzerdefinierter Dynamic Media-Viewer-Vorgaben {#deleting-custom-viewer-presets}

Sie können Viewer-Vorgaben löschen, die Sie erstellt und Dynamic Media hinzugefügt haben.

**So löschen Sie benutzerdefinierte Dynamic Media-Viewer-Vorgaben**:

1. Tippen Sie in der linken oberen Ecke von AEM auf das AEM-Logo und tippen Sie dann in der linken Leiste auf **[!UICONTROL Tools > Assets > Viewer-Vorgaben]**.
1. Im **[!UICONTROL Viewer-Vorgaben]** Seite, überprüfen Sie eine **[!UICONTROL Vorgabentitel]** und tippen Sie dann auf **[!UICONTROL Papierkorb]** Symbol.
1. Tippen Sie auf **[!UICONTROL Löschen]**.

## Anwenden von Dynamic Media-Viewer-Vorgaben auf ein Asset {#applying-a-viewer-preset-to-an-asset}

Wenn Sie das Asset und den ausgewählten Viewer bereits veröffentlicht haben, werden nach Auswahl einer Viewer-Vorgabe die Schaltflächen **[!UICONTROL URL]** und **[!UICONTROL Einbetten]** angezeigt.

**So wenden Sie eine Dynamic Media-Viewer-Vorgabe auf ein Asset an**:

1. Öffnen Sie das Asset, tippen Sie in der Nähe des oberen linken Bereichs der Seite auf das Dropdown-Menü und wählen Sie **[!UICONTROL Viewer]** aus.

   >[!NOTE]
   >
   >Wenn Sie das Asset und den ausgewählten Viewer bereits veröffentlicht haben, werden nach Auswahl einer Viewer-Vorgabe die Schaltflächen **[!UICONTROL URL]** und **[!UICONTROL Einbetten]** angezeigt.

1. Wählen Sie im linken Bereich eine Viewer-Vorgabe aus, um sie auf das Asset anzuwenden.

   Sie können die [URL kopieren, um sie für andere Benutzer freizugeben](linking-urls-to-yourwebapplication.md).

## Bereitstellen von Assets mit Dynamic Media-Viewer-Vorgaben {#delivering-assets-with-viewer-presets}

Informationen zum Abrufen der URLs für Viewer-Vorgaben finden Sie unter [Verknüpfen von URLs mit Ihrer Web-Anwendung](linking-urls-to-yourwebapplication.md). Informationen hierzu finden Sie unter [Einbetten des Video-Viewers auf einer Web-Seite](embed-code.md).

Wenn Sie AEM als WCM verwenden, können Sie Assets mithilfe der Viewer-Vorgaben direkt auf der Seite hinzufügen. Siehe [Hinzufügen von Dynamic Media-Assets zu Seiten](adding-dynamic-media-assets-to-pages.md).
