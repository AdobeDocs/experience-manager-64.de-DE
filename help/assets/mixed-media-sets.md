---
title: Gemischte Mediensets
seo-title: Gemischte Mediensets
description: In diesem Abschnitt erfahren Sie, wie Sie gemischte Mediensets in Dynamic Media verwenden.
seo-description: In diesem Abschnitt erfahren Sie, wie Sie gemischte Mediensets in Dynamic Media verwenden.
uuid: e37fa648-74e2-42e3-8611-8509c92ec00d
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 599c316e-b6a7-4a28-bc4b-75d48409bde0
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939

---


# Gemischte Mediensets {#mixed-media-sets}

Mit gemischten Mediensets können Sie eine Mischung aus Bildern, Bildsets, Rotationssets und Videos in einer Präsentation bereitstellen.

Gemischte Mediensets sind durch ein Banner mit dem Wort **[!UICONTROL MixedMediaSet]** gekennzeichnet. Wenn das gemischte Medienset veröffentlicht wird, wird das durch das Symbol **[!UICONTROL Welt]** angegebene Veröffentlichungsdatum zusammen mit dem Datum der letzten Änderung auf dem Banner angezeigt, was durch das Symbol **[!UICONTROL Stift]** angegeben wird.

![chlimage_1-348](assets/chlimage_1-348.png)

>[!NOTE]
>
>Weitere Informationen zur Assets-Benutzeroberfläche finden Sie unter [Verwalten von Assets mit der Touch-Benutzeroberfläche](managing-assets-touch-ui.md).

## Schnellstartanleitungen: Gemischte Mediensets {#quick-start-mixed-media-sets}

Führen Sie die folgenden Schritte aus, um den schnellen Einstieg in die Arbeit mit gemischten Mediensets zu schaffen:

1. [Laden Sie die Assets hoch.](#uploading-assets)

   Laden Sie zunächst die Bilder und Videos für Ihre gemischten Mediensets hoch. Erstellen Sie bei Bedarf [Bildsets](image-sets.md) und [Rotationssets](spin-sets.md). Da Benutzer Bilder im Viewer für gemischte Mediensets zoomen können, sollten Sie beim Auswählen von Bildern auch das Zoomen berücksichtigen. Achten Sie darauf, dass die längste Seite der Bilder mindestens 2000 Pixel hat.

1. [Erstellen Sie gemischte Mediensets.](#creating-mixed-media-sets)

   Um ein gemischtes Medienset zu erstellen, tippen Sie auf der Seite &quot; **[!UICONTROL Assets]** &quot;auf **[!UICONTROL Erstellen > Gemischtes Medienset]** und geben Sie dann einen Namen für das Set ein. Wählen Sie die Assets und dann die Reihenfolge aus, in der die Bilder angezeigt werden.

   Siehe [Arbeiten mit Selektoren](working-with-selectors.md). 

1. Set up [Mixed Media Viewer presets](managing-viewer-presets.md), as needed.

   Administratoren können Viewer-Voreinstellungen für gemischte Mediensets erstellen oder ändern. Um Ihre gemischten Medien mit einer Viewer-Voreinstellung anzuzeigen, wählen Sie das gemischte Medienset aus und wählen Sie im Dropdownmenü links die Option **[!UICONTROL Viewer]**.

   See **[!UICONTROL Tools > Assets > Viewer Presets]** to create or edit viewer presets.

   See [Adding and editing viewer presets.](managing-viewer-presets.md)

1. [Zeigen Sie eine Vorschau der gemischten Mediensets an.](#previewing-mixed-media-sets)

   Wenn Sie das gemischte Medienset auswählen, können Sie eine Vorschau davon anzeigen. Klicken Sie auf die Miniaturansichtssymbole, um das gemischte Medienset im gewählten Viewer zu untersuchen. You can choose different Viewers from the **[!UICONTROL Viewers]** menu, available from the left rail drop-down menu.

1. [Veröffentlichen Sie gemischte Mediensets.](#publishing-mixed-media-sets)

   Beim Veröffentlichen eines gemischten Mediensets wird die URL- und Integrationszeichenfolge aktiviert. In addition, you must [publish the viewer preset](managing-viewer-presets.md#publishing-viewer-presets).

1. [Verknüpfen Sie URLs mit einer Webanwendung](linking-urls-to-yourwebapplication.md) oder [betten Sie den Video- oder Bild-Viewer ein](embed-code.md).

   AEM Assets erstellt URL-Aufrufe für gemischte Mediensets und aktiviert diese nach deren Veröffentlichung. Sie können diese URLs während der Asset-Vorschau kopieren. Alternativ dazu können Sie sie in Ihre Website einbetten.

   Select the Mixed Media Set, then in the left rail drop-down menu, select **[!UICONTROL Viewers]**.

   Siehe [Verknüpfen eines gemischten Mediensets mit einer Webseite](linking-urls-to-yourwebapplication.md) und [Einbetten des Video- oder Bild-Viewers](embed-code.md).

Bei Bedarf können Sie die [gemischten Mediensets](#editing-mixed-media-sets) bearbeiten. In addition, you can view and modify [Mixed Media Set properties](managing-assets-touch-ui.md#editing-properties).

>[!NOTE]
>
>If you have issues creating sets, see [Troubleshooting Dynamic Media - Scene7 mode](troubleshoot-dms7.md).

## Hochladen von Assets {#uploading-assets}

Laden Sie zunächst die Bilder und Videos für Ihre gemischten Mediensets hoch. Berücksichtigen Sie den Zoom bei der Auswahl von Bildern, da Benutzer Bilder im Viewer für das gemischte Medienset einzoomen können. Achten Sie darauf, dass die längste Seite der Bilder mindestens 2000 Pixel hat.

Wenn Sie außerdem Rotationssets oder Bildsets zum Set für gemischte Medien hinzufügen möchten, müssen Sie auch diese erstellen.

## Erstellen von gemischten Mediensets {#creating-mixed-media-sets}

Sie können Ihrem gemischten Medienset Bilder, Bildsets, Rotationssets und Videos hinzufügen. Achten Sie darauf, dass die Dateien, Bildsets und Rotationssets veröffentlicht werden können, bevor Sie diese dem gemischten Medienset hinzufügen.

Assets, die Sie Ihrem Set hinzufügen, werden automatisch in alphanumerischer Reihenfolge hinzugefügt. Sie können die Assets manuell neu anordnen oder sortieren, nachdem sie hinzugefügt wurden. 

**So erstellen Sie ein gemischtes Medienset**:

1. Navigieren Sie in „Assets“ zu der Stelle, an der Sie ein gemischtes Medienset erstellen möchten, klicken Sie auf **Erstellen** und wählen Sie **[!UICONTROL Gemischtes Medienset]**. Sie können das Set auch aus einem Ordner erstellen, der Ihre Assets enthält.

   ![chlimage_1-349](assets/chlimage_1-349.png)

1. In the **[!UICONTROL Mixed Media Set Editor]** page, in **[!UICONTROL Title]**, enter a name for the Mixed Media Set. Der Name wird im Banner über dem Set für gemischte Medien angezeigt. Geben Sie optional eine Beschreibung ein.

   ![chlimage_1-350](assets/chlimage_1-350.png)

   >[!NOTE]
   >
   >Beim Erstellen des gemischten Mediensets können Sie die Miniaturansicht des gemischten Mediensets ändern oder zulassen, dass AEM die Miniaturansicht basierend auf den Assets im gemischten Mediensatz automatisch auswählt. To select a thumbnail, click **[!UICONTROL Change thumbnail]** and select any image (you can navigate to other folders to find images as well). If you have selected a thumbnail and then decide that you want AEM to generate one from the mixed media set, select **[!UICONTROL Switch to Automatic thumbnail]**.

1. Tap the **[!UICONTROL Asset Selector]** to select assets that you want to include in your Mixed Media Set. Select them and tap **[!UICONTROL Select]**.

   With the **[!UICONTROL Asset Selector]**, you can search for assets by typing in a keyword and tapping **[!UICONTROL Return]**. Sie können auch Filter anwenden, um Ihre Suchergebnisse genauer abzustimmen. Sie können nach Pfad, Sammlung, Dateityp und Tag filtern. Wählen Sie den Filter aus und tippen Sie dann in der Symbolleiste auf das Symbol **[!UICONTROL Filter]**. Change the view by selecting the View icon and selecting **[!UICONTROL List]**, **[!UICONTROL Column]**, or **[!UICONTROL Card]** view.

   Siehe [Arbeiten mit Selektoren](working-with-selectors.md).

   ![chlimage_1-351](assets/chlimage_1-351.png)

1. Ordnen Sie die Bilder neu an, indem Sie sie in der Liste nach Bedarf nach oben oder unten ziehen. (Sie müssen dazu das Symbol für die Neuanordnung wählen.)

   ![chlimage_1-352](assets/chlimage_1-352.png)

   If you want to add thumbnails, click the **[!UICONTROL +]** icon next to the image and navigate to the thumbnail you want. Wenn Sie alle Miniaturbilder ausgewählt haben, tippen Sie auf **[!UICONTROL Speichern]**.

   >[!NOTE]
   >
   >If you want to add assets, tap **[!UICONTROL Add Asset]**.

1. To delete an asset, select the corresponding check box and tap **[!UICONTROL Delete Asset]**.
1. To apply a preset, tap **[!UICONTROL Preset]** in the upper right corner and select a preset to apply to the assets.
1. Klicken Sie auf **[!UICONTROL Speichern]**. Das neu erstellte Set für gemischte Medien wird in dem Ordner angezeigt, in dem es erstellt wurde.

## Bearbeiten von Sets für gemischte Medien {#editing-mixed-media-sets}

Sie können direkt auf der Benutzeroberfläche eine Vielzahl an Bearbeitungsaufgaben für Assets in gemischten Mediensets ausführen, [genauso wie bei allen anderen Assets in Assets](managing-assets-touch-ui.md). Sie können außerdem die folgenden Aktionen in gemischten Mediensets ausführen:

* Fügen Sie dem gemischten Medienset Assets hinzu.
* Ordnen Sie Assets im gemischten Medienset neu an.
* Löschen Sie Assets im gemischten Medienset.
* Wenden Sie Viewer-Vorgaben an.
* Ändern Sie die Standardminiatur.

**So bearbeiten Sie gemischte Mediensets**:

1. Führen Sie einen der folgenden Schritte aus:

   * Bewegen Sie den Mauszeiger über ein Asset in einem gemischten Medienset und tippen Sie auf **[!UICONTROL Bearbeiten]** (Stiftsymbol).
   * Bewegen Sie den Mauszeiger über ein Asset in einem gemischten Medienset und tippen Sie auf **[!UICONTROL Auswählen]** (Häkchensymbol) und dann auf **[!UICONTROL Bearbeiten]** in der Symbolleiste.
   * Tippen Sie auf ein Asset in einem gemischten Medienset und dann auf **[!UICONTROL Bearbeiten]** (Bleistiftsymbol) in der Symbolleiste.

1. Führen Sie im Editor für gemischte Mediensets einen der folgenden Schritte aus:

   * Um Assets neu anzuordnen, tippen Sie im linken Bereich auf **[!UICONTROL Assets]** (Bildsymbol) und ziehen Sie das Asset an eine neue Position.
   * Um Assets hinzuzufügen, tippen Sie in der Symbolleiste auf **[!UICONTROL Asset hinzufügen]**. Navigieren Sie zu den Assets. Bewegen Sie bei jedem Asset, das Sie hinzufügen möchten, den Mauszeiger über dem Bild des Assets (nicht über dem Namen des Assets) und tippen Sie auf das Häkchensymbol. Tippen Sie oben rechts auf **[!UICONTROL Auswählen]**.
   * Um ein Asset zu löschen, tippen Sie im linken Bereich auf **[!UICONTROL Assets]** (Bildsymbol) und wählen Sie das Asset aus. Tippen Sie in der Symbolleiste auf **[!UICONTROL Asset löschen]**.
   * Um Assets anhand des Namens in aufsteigender oder absteigender Reihenfolge zu sortieren, tippen Sie im linken Bereich auf **[!UICONTROL Assets]** (Bildsymbol). Klicken Sie rechts neben der Überschrift **[!UICONTROL Assets]** auf das Caret-Zeichen nach oben oder unten.
   >[!NOTE]
   >
   >* To delete an entire Mixed Media Set, from any viewing mode (such as **[!UICONTROL Card]** view or **[!UICONTROL Column]** view) navigate to the Mixed Media Set. Bewegen Sie den Zeiger über das Asset und tippen Sie auf das Häkchen, um es auszuwählen. Press **[!UICONTROL Backspace]** on the keyboard, or tap **[!UICONTROL More]** (three dots) on the toolbar, then tap **[!UICONTROL Delete]**.
   >* You can edit the assets in a Mixed Media Set by navigating to the set, tapping **[!UICONTROL Set Members]** in the left rail, and then tapping the **[!UICONTROL Pencil]** icon on an individual asset to open the editing window.


1. Tap **[!UICONTROL Save** when you are done editing.

   >[!NOTE]
   >
   >* Um die Assets in einem gemischten Medienset zu bearbeiten, navigieren Sie zum gemischten Medienset. Tap (do not select) the set to open it in the AEM **[!UICONTROL Set Preview]** page. In the left rail, tap the down caret to open the drop-down list, then tap **[!UICONTROL Set Members]**. In the **[!UICONTROL Set Members]** page, hover on an asset, then tap **[!UICONTROL Edit]** (pencil icon) to open the editing page.
   >* To delete an entire Mixed Media Set - From any viewing mode (such as **[!UICONTROL Card]** view or **[!UICONTROL Column]** view), navigate to the Mixed Media Set. Bewegen Sie den Mauszeiger über das Set und tippen Sie auf **[!UICONTROL Auswählen]** (Häkchensymbol). Drücken Sie die **[!UICONTROL Rücktaste]** oder tippen Sie auf **[!UICONTROL Mehr]** und dann auf **[!UICONTROL Löschen]**.


## Vorschau von gemischten Mediensets {#previewing-mixed-media-sets}

Weitere Informationen zum Aufrufen einer Vorschau von Sets für gemischte Medien finden Sie in [Asset-Vorschau](previewing-assets.md).

## Veröffentlichen von Sets für gemischte Medien {#publishing-mixed-media-sets}

Weitere Informationen zum Veröffentlichen von Sets für gemischte Medien finden Sie in [Veröffentlichen von Assets](publishing-dynamicmedia-assets.md).

>[!NOTE]
>
>Wenn das gemischte Medienset beim ersten Veröffentlichen nicht vollständig im Bereitstellungsdienst landet, müssen Sie den gemischten Mediensatz möglicherweise ein zweites Mal veröffentlichen.

