---
title: Bildsets
seo-title: Bildsets
description: 'Erfahren Sie, wie Sie in dynamischen Medien mit Bildsets arbeiten können. '
seo-description: 'Erfahren Sie, wie Sie in dynamischen Medien mit Bildsets arbeiten können. '
uuid: 16008278-f59f-4fa8-90e9-19c78f132439
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: e00e7cc9-b777-4f9e-906d-824bcb2bbd41
translation-type: tm+mt
source-git-commit: e269c0cf002f4b2db5454c315d35f4101b652540

---


# Bildsets {#image-sets}

Über Bildsets erhalten Benutzer ein integriertes Anzeigeerlebnis, bei dem sie unterschiedliche Ansichten eines Elements durch Klicken auf eine Miniaturansicht anzeigen können. Mit Bildsets können Sie alternative Ansichten eines Elements darstellen. Dabei enthält der Viewer Zoomtools, mit denen Bilder genauer betrachtet werden können.

Bildsets werden durch ein Banner mit dem Wort **[!UICONTROL BILDSET]** gekennzeichnet. Wenn das Bildset veröffentlicht wird, wird das durch das Symbol **[!UICONTROL Welt]** angegebene Veröffentlichungsdatum zusammen mit dem Datum der letzten Änderung auf dem Banner angezeigt, was durch das Symbol **[!UICONTROL Stift]** angegeben wird.

![chlimage_1-339](assets/chlimage_1-339.png)

Innerhalb des Bildsatzes können Sie auch Muster erstellen, indem Sie einen Bildsatz erstellen und Miniaturansichten hinzufügen.

Dies ist besonders nützlich, wenn Sie einen Artikel in einer anderen Farbe, einem anderen Muster oder mit anderer Endverarbeitung darstellen möchten. Um ein Bildset mit Farbmustern zu erstellen, benötigen Sie ein Bild für alle Farben, Muster oder Endverarbeitungen, die den Benutzern dargestellt werden sollen. Außerdem benötigen Sie eine Farb-, Muster- oder Endverarbeitungsvorlage für alle Farben, Muster oder Endverarbeitungen.

Beispiel: Sie möchten Bilder von Kappen darstellen, deren Schirme unterschiedliche Farben aufweisen: rot, grün und blau. In diesem Fall benötigen Sie drei Aufnahmen der gleichen Kappe. Sie brauchen eine Aufnahme mit einem roten Schirm, eine mit einem grünen Schirm und eine mit einem blauen Schirm. Außerdem brauchen Sie ein rotes, grünes und blaues Farbmuster. Die Farbmuster dienen als Miniaturansichten, auf die Benutzer im Musterset-Viewer klicken, um die Kappe mit rotem, grünem oder blauem Schirm anzuzeigen.

>[!NOTE]
>
>Weitere Informationen zur Assets-Benutzeroberfläche finden Sie unter [Verwalten von Assets mit der Touch-Benutzeroberfläche](managing-assets-touch-ui.md).

## Schnellstart: Bildsets {#quick-start-image-sets}

So schaffen Sie einen schnellen Einstieg:

1. [Laden Sie die Masterbilder für mehrere Ansichten hoch.](#uploading-assets-in-image-sets)

   Laden Sie zunächst die Bilder für die Bildsets hoch. Berücksichtigen Sie den Zoom bei der Auswahl von Bildern, da Benutzer Bilder im Bildset-Viewer einzoomen können. Achten Sie darauf, dass die längste Seite der Bilder mindestens 2000 Pixel hat, um optimale Zoomdetails zu erzielen. Mit dynamischen Medien können Bilder mit einer Auflösung von jeweils bis zu 25 Megapixeln gerendert werden. Sie können beispielsweise ein Bild mit 5000 x 5000 Megapixeln oder eine beliebige andere Größenkombination mit bis zu 25 Megapixeln verwenden.

   AEM Assets unterstützt zahlreiche Bilddateiformate, empfohlen werden aber verlustfreie TIFF-, PNG- und EPS-Bilder.

1. [Erstellen Sie Bildsets.](#creating-image-sets)

   In Bildsets klicken Benutzer im Bildset-Viewer auf Miniaturansichten.

   To create an Image Set in Assets, tap **[!UICONTROL Create > Image Sets]**. Then, add images and tap **[!UICONTROL Save]**.

   Sie können Bildsets auch automatisch über [Stapelsatzvorgaben](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets) erstellen.

   **Wichtig** — Stapelsätze werden im Rahmen der Asset-Erfassung vom IPS (Image Production System) erstellt und stehen nur im Modus &quot;Dynamische Medien - Scene7&quot;zur Verfügung.

   See [Preparing Image Set assets for upload and Uploading your files](#uploading-assets-in-image-sets).

   Siehe [Arbeiten mit Selektoren](working-with-selectors.md). 

1. Add [Image Set Viewer presets](managing-viewer-presets.md), as needed.

   Administrators can create or modify Image **[!UICONTROL Set Viewer Presets]**. To see your image set with a viewer preset, select the image set, and in the left-rail drop-down menu, select **[!UICONTROL Viewers]**.

   See **[!UICONTROL Tools > Assets > Viewer Presets]** to create or edit viewer presets.

1. (Optional) [Viewing Image Sets](image-sets.md#viewing-image-sets) that were created using batch set presets.
1. [Zeigen Sie Bildsets in einer Vorschau an.](previewing-assets.md)

   Wählen Sie das Bildset aus, um dessen Vorschau anzuzeigen. Tippen Sie auf die Miniaturansicht-Symbole, um den Bildsatz im ausgewählten Viewer zu überprüfen. You can choose different viewers from the **[!UICONTROL Viewers]** menu, available from the left rail drop-down menu.

1. [Veröffentlichen Sie Bildsets.](publishing-dynamicmedia-assets.md)

   Beim Veröffentlichen eines Bildsets wird die URL- und Einbettungszeichenfolge aktiviert. In addition, you must [publish any custom viewer preset](managing-viewer-presets.md) that you have created. Standardmäßig vorhandene Viewer-Vorgaben wurden bereits veröffentlicht.

1. [Verknüpfen Sie URLs mit einer Webanwendung](linking-urls-to-yourwebapplication.md) oder [betten Sie den Video- oder Bild-Viewer ein](embed-code.md).

   AEM Assets erstellt URL-Aufrufe für Bildsets und aktiviert diese, nachdem Sie die Bildsets veröffentlicht haben. Sie können diese URLs während der Asset-Vorschau kopieren. Sie können sie alternativ in Ihre Website einbetten.

   Wählen Sie das Bildset und dann im Dropdown-Menü links die Option **[!UICONTROL Viewer]**.

   Siehe [Verknüpfen eines Bildsets mit einer Webseite](linking-urls-to-yourwebapplication.md) und [Einbetten des Video- oder Bild-Viewers](embed-code.md).

To edit Image Sets, see [editing Image Sets.](#editing-image-sets) Darüber hinaus können Sie [Bildsatzeigenschaften](managing-assets-touch-ui.md#editing-properties)Ansicht und bearbeiten.

Wenn Sie beim Erstellen von Sets Probleme haben, lesen Sie den Abschnitt zu Bildern und Sets unter [Problembehandlung in Dynamic Media – Scene7-Modus](troubleshoot-dms7.md#images-and-sets).

## Uploading assets in Image Sets {#uploading-assets-in-image-sets}

Laden Sie zunächst die Bilder für die Bildsets hoch. Berücksichtigen Sie den Zoom bei der Auswahl von Bildern, da Benutzer Bilder im Bildset-Viewer einzoomen können. Achten Sie darauf, dass die längste Seite der Bilder mindestens 2000 Pixel hat. Bildsets unterstützen zahlreiche Bilddateiformate, empfohlen werden aber verlustfreie TIFF-, PNG- und EPS-Bilder.

Sie laden Bilder für Bildsets genauso wie [alle anderen Assets in Assets](managing-assets-touch-ui.md#uploading-assets) hoch.

### Vorbereiten von Bildset-Assets auf das Hochladen {#preparing-image-set-assets-for-upload}

Bevor Sie Bildsets erstellen, achten Sie darauf, dass die Bilder die richtige Größe und das richtige Format aufweisen.

Um ein Bildset mit mehreren Ansichten zu erstellen, benötigen Sie Bilder, die einen Artikel aus unterschiedlichen Blickwinkeln zeigen oder unterschiedliche Aspekte desselben Artikels darstellen. Ziel ist es, die wichtigen Merkmale eines Artikels so hervorzuheben, dass Benutzer einen umfassen Einblick in das Aussehen oder die Funktion des Gegenstands erhalten.

Stellen Sie sicher, dass die Bilder in Bildsets mindestens 2000 Pixel in der größten Abmessung aufweisen, da Benutzer sie einzoomen können. Assets unterstützt zahlreiche Bilddateiformate, empfohlen werden aber verlustfreie TIFF-, PNG- und EPS-Bilder.

>[!NOTE]
>
>Wenn Sie außerdem Miniaturansichten verwenden, um Produktmuster anzuzeigen, müssen Sie Folgendes ausführen:
>
>Sie benötigen Vignetten oder unterschiedliche Aufnahmen desselben Bildes, in denen dieses in verschiedenen Farben, Mustern oder Endverarbeitungen dargestellt wird. Außerdem benötigen Sie Miniaturansichtsdateien, die den verschiedenen Farben, Mustern oder Endverarbeitungen entsprechen. Um beispielsweise Miniaturansichten in einem Bildset zu präsentieren, die eine Jacke in Schwarz, Braun und Grün anzeigen, benötigen Sie:
>
>* eine schwarze, braune und grüne Aufnahme der Jacke,
>* eine schwarze, braune und grüne Miniaturansicht
>



## Erstellen von Bildsets {#creating-image-sets}

Sie können Bildsätze über die Benutzeroberfläche oder über die API erstellen. In diesem Abschnitt wird das Erstellen von Bildsätzen in der Benutzeroberfläche beschrieben.

>[!NOTE]
>
>Sie können Bildsets auch automatisch über [Stapelsatzvorgaben](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets) erstellen.

**Wichtig:** Stapelsätze werden vom IPS (Image Production System) im Rahmen der Asset-Aufnahme erstellt und sind nur im Scene7-Modus von Dynamic Media verfügbar.

Assets, die Sie Ihrem Set hinzufügen, werden automatisch in alphanumerischer Reihenfolge hinzugefügt.  Sie können die Assets manuell neu anordnen oder sortieren, nachdem sie hinzugefügt wurden. 

>[!NOTE]
>
>Image sets are not supported for assets with `,` (comma) in the file name.

**So erstellen Sie ein Bildset**:

1. In **Assets**, navigate to where you want to create an image set, tap **[!UICONTROL Create]**, and select **[!UICONTROL Image Set]**. Sie können das Set auch aus einem Ordner erstellen, der Ihre Assets enthält.

   ![chlimage_1-340](assets/chlimage_1-340.png)

1. On the Image Set Editor page, in the **[!UICONTROL Title]** field, enter a name for the Image Set. Der Name wird im Banner über dem Bildset angezeigt. Geben Sie optional eine Beschreibung ein.

   ![chlimage_1-341](assets/chlimage_1-341.png)

   >[!NOTE]
   >
   >Beim Erstellen des Bildsets können Sie die Miniaturansicht des Bildsets ändern oder zulassen, dass AEM die Miniaturansicht anhand der Assets im Bildset automatisch auswählt. To select a thumbnail, tap **[!UICONTROL Change thumbnail]** and select any image (you can navigate to other folders to find images as well). Wenn Sie eine Miniaturansicht ausgewählt haben und dann entscheiden, dass AEM eine aus dem Bildset generieren soll, wählen Sie **[!UICONTROL Wechseln zu Automatische Miniaturansicht]**.

1. Nehmen Sie eine der folgenden Aktionen vor:

   * Near the upper-left corner of the **[!UICONTROL Image Set Editor]** page, tap **[!UICONTROL Add Asset]**.
   * Near the middle of the **[!UICONTROL Image Set Editor]** page, tap **[!UICONTROL Tap to open Asset Selector]**.
   Tippen Sie auf , um Assets auszuwählen, die Sie in Ihren Bildsatz aufnehmen möchten. Die ausgewählten Assets sind mit einem Häkchen versehen. Wenn Sie die Assets ausgewählt haben, tippen Sie auf **[!UICONTROL Auswählen]**.

   Mit der Asset-Auswahl können Sie nach Assets suchen, indem Sie einen Suchbegriff eingeben und auf **[!UICONTROL Zurück]** tippen. Sie können auch Filter anwenden, um Ihre Suchergebnisse genauer abzustimmen. Sie können nach Pfad, Sammlung, Dateityp und Tag filtern. Wählen Sie den Filter aus und tippen Sie dann in der Symbolleiste auf das Symbol **[!UICONTROL Filter]**. Change the view by tapping the **[!UICONTROL View]** icon and selecting **[!UICONTROL Column View]**, **[!UICONTROL Card View]**, or **[!UICONTROL List View]**.

   Siehe [Arbeiten mit Selektoren](working-with-selectors.md). 

   ![chlimage_1-342](assets/chlimage_1-342.png)

1. Assets, die Sie Ihrem Set hinzufügen, werden automatisch in alphanumerischer Reihenfolge hinzugefügt.  Sie können die Assets nach dem Hinzufügen manuell neu anordnen oder sortieren.

   If necessary, drag an asset&#39;s **[!UICONTROL Reorder]** icon to the right of the asset&#39;s file name to re-order images up or down the set list.

   ![spin_set_assets](assets/spin_set_assets.png)

   If you want to change a thumbnail or swatch, tap the **[!UICONTROL Thumbnail]** icon next to the image and navigate to the thumbnail or swatch you want. When done selecting all the images tap **[!UICONTROL Save]**.

1. (Optional) Führen Sie einen der folgenden Schritte aus:

   * To delete an image, select the image, then tap **[!UICONTROL Delete Asset]**.
   * Wenn Sie eine Vorgabe anwenden möchten, tippen Sie oben rechts auf **[!UICONTROL Vorgabe]**. Wählen Sie anschließend eine Vorgabe aus, um sie auf alle Elemente gleichzeitig anzuwenden.

1. Tippen Sie auf **[!UICONTROL Speichern]**. Das neu erstellte Bildset wird in dem Ordner angezeigt, in dem es erstellt wurde.

## Anzeigen von Bildsets  {#viewing-image-sets}

Sie können Bildsätze entweder in der Benutzeroberfläche oder automatisch über [Stapelsatzvorgaben](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets) erstellen.

**Wichtig** — Stapelsätze werden vom IPS- [Bildproduktionssystem] als Teil der Asset-Erfassung erstellt und stehen nur im Modus &quot;Dynamische Medien - Scene7&quot;zur Verfügung.)

However, sets created using batch set presets, do *not* appear in the user interface. Sie können diese Sets auf drei verschiedene Arten anzeigen. (Diese Methoden sind auch verfügbar, wenn Sie die Bildsets in der Benutzeroberfläche erstellt haben.)

* Beim Öffnen der Eigenschaften eines einzelnen Assets. Die Eigenschaften zeigen an, zu welchen Sets das ausgewählte Asset gehört (unter **[!UICONTROL Mitglied von Sets]**).  Tippen Sie auf den Namen des Sets, um den gesamten Satz anzuzeigen.

   ![chlimage_1-343](assets/chlimage_1-343.png)

* Aus einem Mitgliederbild eines Sets. Select the **[!UICONTROL Sets]** menu to display the sets that the asset is a member of.

   ![chlimage_1-344](assets/chlimage_1-344.png)

* From search, you can select **[!UICONTROL Filters]**, then expand **[!UICONTROL Dynamic Media]** and select **[!UICONTROL Sets]**.

   Die Suche gibt als Ergebnis Sets zurück, die in der Benutzeroberfläche manuell oder mit Stapelsatzvorgaben automatisch erstellt wurden.  Im Gegensatz zu AEM-Suchen, die mit dem Suchkriterium „Enthält“ durchgeführt werden, wird die Suchabfrage für automatisierte Sets mithilfe des Suchkriteriums „Beginnt mit“ durchgeführt. Setting the filter to **[!UICONTROL Sets]** is the only way to search automated sets.

   ![chlimage_1-345](assets/chlimage_1-345.png)

>[!NOTE]
>
>Sets können über die Benutzeroberfläche angezeigt werden, wie unter [Bearbeiten von Bildsets](#editing-image-sets) beschrieben. 

## Bearbeiten von Bildsets {#editing-image-sets}

Sie können mehrere Bearbeitungsaufgaben für Bildsets ausführen, z. B. die folgenden:

* Fügen Sie dem Bildset Bilder hinzu.
* Ordnen Sie Bilder im Bildset neu an.
* Löschen Sie Assets im Bildset.
* Wenden Sie Viewer-Vorgaben an. 
* Löschen Sie das Bildset.

**So bearbeiten Sie Bildsets**:

1. Führen Sie einen der folgenden Schritte aus:

   * Zeigen Sie mit der Maus auf ein Bildset-Asset und tippen Sie auf **[!UICONTROL Bearbeiten]** (Bleistiftsymbol).
   * Zeigen Sie mit der Maus auf ein Bildset-Asset und tippen Sie auf **[!UICONTROL Auswählen]** (Häkchensymbol) und dann auf **[!UICONTROL Bearbeiten]** in der Symbolleiste.
   * Tippen Sie auf ein Bildset-Asset und dann auf **[!UICONTROL Bearbeiten]** (Bleistiftsymbol) in der Symbolleiste.

1. Führen Sie eine der folgenden Aktionen aus, um die Bilder im Bildset zu bearbeiten:

   * Ziehen Sie ein Bild, wenn Sie ein Asset an einer neuen Position anordnen möchten (zum Verschieben von Elementen wählen Sie das Symbol zum Neuanordnen).
   * Um Elemente in auf- oder absteigender Reihenfolge zu sortieren, tippen Sie auf die Spaltenüberschrift.
   * To add an asset or update an existing asset, tap the **[!UICONTROL Add Asset]**. Navigieren Sie zu einem Asset, wählen Sie es aus und tippen Sie oben rechts auf **[!UICONTROL Auswählen.]**
   >[!NOTE]
   >Wenn Sie das in AEM als Miniaturansicht verwendete Bild löschen und durch ein anderes ersetzen, wird das Original-Asset weiterhin angezeigt.

   * To delete an asset, select it, then tap **[!UICONTROL Delete Asset]**.
   * Um eine Vorgabe anzuwenden, tippen Sie oben rechts auf der Seite auf **[!UICONTROL Vorgabe]** und wählen Sie eine Viewer-Vorgabe aus.
   * Um eine Miniaturansicht hinzuzufügen oder zu ändern, wählen Sie die Miniaturansicht rechts neben dem Asset. Navigieren Sie zur neuen Miniaturansicht oder zum neuen Farbmuster-Asset, wählen Sie es aus und tippen Sie dann auf **[!UICONTROL Auswählen]**.
   * Um ein ganzes Bildset zu löschen, navigieren Sie zum Bildset, wählen Sie es aus und klicken Sie auf **[!UICONTROL Löschen]**.
   >[!NOTE]
   >
   >Sie können die Bilder in einem Bildset bearbeiten, indem Sie zu dem Set navigieren, in der linken Leiste auf **[!UICONTROL Setmitglieder]** tippen und dann auf das Stiftsymbol eines Assets, um das Bearbeitungsfenster zu öffnen.****

1. Tippen Sie auf **[!UICONTROL Speichern]**, wenn Sie die Bearbeitung abgeschlossen haben.

## Anzeigen von Bildsets in einer Vorschau {#previewing-image-sets}

Weitere Informationen finden Sie im Abschnitt [Asset-Vorschau](previewing-assets.md).

## Veröffentlichen von Bildsets {#publishing-image-sets}

Siehe [Veröffentlichen von Assets](publishing-dynamicmedia-assets.md).
