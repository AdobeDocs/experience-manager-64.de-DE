---
title: Rotationssets
seo-title: Rotationssets
description: Erfahren Sie, wie Sie in dynamischen Medien mit Rotationssets arbeiten können.
seo-description: Erfahren Sie, wie Sie in dynamischen Medien mit Rotationssets arbeiten können.
uuid: a80a0491-6500-463a-83c4-ff4b90a88182
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: afacb3ad-e4ad-4d06-a898-f3f2da8bbb64
translation-type: tm+mt
source-git-commit: 7cb0f63f0cd83e6e40ed51b2fd300f010278aa56
workflow-type: tm+mt
source-wordcount: '1838'
ht-degree: 69%

---


# Rotationssets {#spin-sets}

Ein Rotationsset simuliert das Drehen eines Gegenstands zur genaueren Untersuchung. Mit Rotationssets können Artikel aus jedem Winkel betrachtet werden, um die wesentlichen visuellen Details von allen Seiten sehen zu können.

Ein Rotationsset simuliert die 360-Grad-Anzeige. Dynamic Media bietet Rotationssets mit einer Achse, in denen ein Artikel gedreht werden kann. Darüber hinaus können Benutzer alle Ansichten mit nur wenigen Mausklicks frei zoomen und schwenken. So können Benutzer einen Artikel aus einem bestimmten Blickwinkel genauer untersuchen.

Rotationssets werden durch ein Banner mit dem Wort **[!UICONTROL SPINSET]** gekennzeichnet. Darüber hinaus wird bei veröffentlichten Rotationssets das Veröffentlichungsdatum (durch das **[!UICONTROL Welt]**-Symbol gekennzeichnet) zusammen mit dem Datum der letzten Änderung (durch das **[!UICONTROL Bleistift]**-Symbol gekennzeichnet) im Banner angezeigt.

![chlimage_1-380](assets/chlimage_1-380.png)

>[!NOTE]
>
>Weitere Informationen zur Assets-Benutzeroberfläche finden Sie unter [Verwalten von Assets mit der Touch-Benutzeroberfläche](managing-assets-touch-ui.md).

## Schnellstart: Rotationssets   {#quick-start-spin-sets}

Gehen Sie wie folgt vor, um sich schnell mit Rotationssets vertraut zu machen:

1. [Laden Sie die Bilder für mehrere Ansichten hoch.](#uploading-assets-for-spin-sets)

   Sie benötigen mindestens 8 bis 12 Aufnahmen eines Artikels für ein eindimensionales Rotationsset und 16 bis 24 Aufnahmen für ein zweidimensionales Rotationsset. Die Aufnahmen müssen in regelmäßigen Abständen gemacht werden, um den Eindruck zu erwecken, dass der Artikel gedreht wird. Beispiel: Wenn ein eindimensionales Rotationsset 12 Aufnahmen umfasst, drehen Sie den Artikel für jede Aufnahme um 30 Grad (360/12).

1. [Erstellen Sie Rotationssets.](#creating-spin-sets)

   Um ein Rotationsset zu erstellen, wählen Sie &quot; **[!UICONTROL Erstellen&quot;> &quot;Rotationsset]** &quot;und geben Sie dem Set einen Namen, wählen Sie die Assets aus und sortieren Sie dann die Bilder in der Reihenfolge, in der sie angezeigt werden.

   Siehe [Arbeiten mit Selektoren](working-with-selectors.md).

   >[!NOTE]
   >
   >You can also create Spin Sets automatically through [batch set presets](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets).
   *Stapelsätze werden vom IPS (Image Production System) im Rahmen der Asset-Erfassung erstellt und sind nur im Dynamischen Media - Scene7-Modus* verfügbar.

1. Richten Sie [Rotationsset-Viewer-Vorgaben](managing-viewer-presets.md) nach Bedarf ein.

   Administratoren können Rotationsset-Viewer-Vorgaben erstellen oder ändern. To see your Spin Set with a Viewer preset, select the Spin Set, and in the left-rail drop-down menu, select **[!UICONTROL Viewers]**.

   Um Viewer-Vorgaben zu erstellen oder zu bearbeiten, wählen Sie **[!UICONTROL Tools > Assets > Viewer-Vorgaben]**.

   Siehe [Hinzufügen und Bearbeiten von Viewer-Vorgaben.](managing-viewer-presets.md)

1. [Zeigen Sie Rotationssets an](#viewing-spin-sets).

   Es gibt drei verschiedene Arten, über Stapelsatzvorgaben erstellte Sätze anzuzeigen und darauf zuzugreifen. (In der Benutzeroberfläche werden *keine* mit Stapelsatzvorgaben erstellten Sets angezeigt.)

1. [Zeigen Sie eine Vorschau der Rotationssets an.](previewing-assets.md)

   Wählen Sie das Rotationsset aus, um dessen Vorschau anzuzeigen. Drehen Sie das Rotationsset. Sie können verschiedene Viewer aus dem Menü **[!UICONTROL Viewer]** wählen, das Sie links in der Leiste über die Dropdown-Liste aufrufen können.

1. [Veröffentlichen Sie Rotationssets.](publishing-dynamicmedia-assets.md)

   Beim Veröffentlichen eines Rotationssets wird die Reihenfolge aktiviert, in der Bilder in einem Rotationsset angezeigt werden. Achten Sie darauf, sie so anzuordnen, dass die Rotation eine gleichmäßige 360-Grad-Ansicht ergibt.**[!UICONTROL URL]** und **[!UICONTROL Einbettungszeichenfolge]** . Außerdem müssen Sie [die Viewer-Vorgabe veröffentlichen](managing-viewer-presets.md).

1. [Verknüpfen Sie URLs mit einer Web-Anwendung](linking-urls-to-yourwebapplication.md) oder [betten Sie den Video- oder Bild-Viewer ein](embed-code.md).

   AEM Assets erstellt URL-Aufrufe für Rotationssets und aktiviert sie, nachdem Sie die Rotationssets veröffentlicht haben. Sie können diese URLs kopieren, wenn Sie Assets Vorschau haben. Alternativ können Sie sie auch in Ihre Website einbetten.

   Wählen Sie dazu das Rotationsset aus und klicken Sie dann im Dropdown-Menü in der linken Seitenleiste auf **[!UICONTROL Viewer]**.

   Siehe [Verknüpfen von Rotationssets mit Web-Seiten](linking-urls-to-yourwebapplication.md) und [Einbetten des Video- oder Bild-Viewers](embed-code.md).

Bei Bedarf können Sie [Rotationssets bearbeiten](#editing-spin-sets). In addition, you can view and edit [Spin Set properties](managing-assets-touch-ui.md#editing-properties).

## Hochladen von Assets für Rotationssets {#uploading-assets-for-spin-sets}

Sie benötigen mindestens 8 bis 12 Aufnahmen eines Artikels für ein eindimensionales Rotationsset und 16 bis 24 Aufnahmen für ein zweidimensionales Rotationsset. Die Aufnahmen müssen in regelmäßigen Abständen gemacht werden, um den Eindruck zu erwecken, dass der Artikel gedreht wird. Beispiel: Wenn ein eindimensionales Rotationsset 12 Aufnahmen umfasst, drehen Sie den Artikel für jede Aufnahme um 30 Grad (360/12).

Bilder für Rotationssets können Sie [genauso wie alle anderen Assets in AEM Assets hochladen](managing-assets-touch-ui.md).

### Richtlinien für die Aufnahme von Rotationsset-Bildern {#guidelines-for-shooting-spin-set-images}

Im Folgenden finden Sie einige Best Practices für Rotationsset-Bilder. Im Allgemeinen gilt: Je mehr Bilder ein Rotationsset enthält, desto besser gelingt der Bildrotationseffekt. Wenn Sie aber zahlreiche Bilder in das Set aufnehmen, dauert es auch länger, bis die Bilder geladen werden. AEM empfiehlt die folgenden Richtlinien für die Aufnahme von Bildern für Rotationssets.

* Verwenden Sie mindestens 8 bis 12 Bilder für ein eindimensionales Rotationsset und 16 bis 24 Bilder für ein zweidimensionales Rotationsset. Mindestens 8 Bilder sind erforderlich, um die Drehung um 360 Grad zu ermöglichen. Eindimensionale Rotationssets werden häufiger verwendet, da zweidimensionale Rotationssets sehr aufwendig zu erstellen sind.
* Verwenden Sie ein verlustfreies Format: TIFF und PNG werden empfohlen.
* Maskieren Sie alle Bilder so, dass der Artikel vor einem rein weißen oder kontrastreichen Hintergrund erscheint. Fügen Sie optional Schatten hinzu.
* Stellen Sie sicher, dass die Produktdetails gut beleuchtet und fokussiert sind.
* Denken Sie z. B. an Rotationsbilder für Bekleidung an einer Schaufensterpuppe oder einem Modell. Die Schaufensterpuppe ist häufig entweder komplett maskiert (eine Schaufensterpuppe aus Glas) oder es wird eine stilisierte Schaufensterpuppe im Bild gezeigt. Sie können ein modellbezogenes Rotationsset erstellen, indem Sie die Anzahl der Winkel definieren. Markieren Sie jeden Winkel mit Klebeband auf dem Boden, um dem Modell anzugeben, einen Schritt zu machen und in die Richtung der jeweiligen Aufnahme zu schauen.

## Erstellen von Rotationssets   {#creating-spin-sets}

Die Reihenfolge der Bilder in einem Rotationsset ist wichtig. Achten Sie darauf, sie so anzuordnen, dass die Rotation eine gleichmäßige 360-Grad-Ansicht ergibt.

>[!NOTE]
>
>Sie können Rotationssets auch automatisch über [Stapelsatzvorgaben](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets) erstellen.
Stapelsätze werden vom IPS (Image Production System) im Rahmen der Asset-Erfassung erstellt und sind nur im Modus &quot;Dynamische Medien - Scene7&quot;verfügbar.
>
>Siehe „Erstellen von Stapelsatzvorgaben zum automatischen Erzeugen von Bild- und Rotationssets“ in [Konfigurieren von Dynamic Media – Scene7-Modus](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets).

**So erstellen Sie Rotationssets:**

1. In Assets, navigate to where you want to create a spin set, tap **[!UICONTROL Create]**, and select **[!UICONTROL Spin Set]**. Sie können das Set auch in einem Ordner erstellen, der die gewünschten Assets enthält.

   ![chlimage_1-381](assets/chlimage_1-381.png)

1. On the **[!UICONTROL Spin Set Editor]** page, in the **[!UICONTROL Title]** field, enter a name for the Spin Set. Der Name wird im Banner über dem Rotationsset angezeigt. Geben Sie optional eine Beschreibung ein.

   ![chlimage_1-382](assets/chlimage_1-382.png)

   Beim Erstellen des Rotationssets können Sie die Miniaturansicht des Rotationssets ändern oder zulassen, dass AEM die Miniaturansicht automatisch anhand der Assets im Rotationsset auswählen. To select a thumbnail, tap **[!UICONTROL Change thumbnail]**. Select any image (you can navigate to other folders to find images as well). Wenn Sie eine Miniaturansicht ausgewählt haben und möchten, dass AEM eine Miniaturansicht aus dem Rotationsset generiert, wählen Sie **[!UICONTROL Zu automatischer Miniatur wechseln]** aus.

1. Nehmen Sie eine der folgenden Aktionen vor:

   * Near the upper-left corner of the **[!UICONTROL Spin Set Editor]** page, tap **[!UICONTROL Add Asset]**.
   * Near the middle of the **[!UICONTROL Spin Set Editor]** page, tap **[!UICONTROL Tap to open Asset Selector]**.

   Tippen Sie, um die gewünschten Assets für das Rotationsset auszuwählen. Die ausgewählten Assets sind mit einem Häkchen versehen. Wenn Sie die Assets ausgewählt haben, tippen Sie auf **[!UICONTROL Auswählen]**.

   Mit dem Asset-Selektor können Sie nach Assets suchen, indem Sie ein Keyword eingeben und auf **[!UICONTROL Eingabe]** tippen. Sie können auch Filter anwenden, um Ihre Suchergebnisse genauer abzustimmen. Sie können nach Pfad, Sammlung, Dateityp und Tag filtern. Wählen Sie den Filter und tippen Sie in der Symbolleiste auf das Symbol **[!UICONTROL Filter]**. Um die Ansicht zu ändern, tippen Sie oben rechts auf der Seite auf das Symbol &quot; **[!UICONTROL Ansicht]** &quot;und dann auf &quot;Ansicht **[!UICONTROL der]** Spalte&quot;, &quot;Ansicht **[!UICONTROL der]** Karte&quot;oder &quot;Ansicht **[!UICONTROL der]** Liste&quot;.

   Siehe [Arbeiten mit Selektoren](working-with-selectors.md).

   ![chlimage_1-383](assets/chlimage_1-383.png)

1. Assets, die Sie Ihrem Set hinzufügen, werden automatisch in alphanumerischer Reihenfolge hinzugefügt.  Sie können die Assets nach dem Hinzufügen manuell neu anordnen oder sortieren. If necessary, drag an asset&#39;s **[!UICONTROL Reorder]** icon to the right of the asset&#39;s file name to re-order images up or down the set list.

   ![spin_set_assets6-4](assets/spin_set_assets6-4.png)

1. (Optional) Führen Sie einen der folgenden Schritte aus:

   * To delete an image, select the image, then tap **[!UICONTROL Delete Asset]**.
   * Wenn Sie eine Vorgabe anwenden möchten, tippen Sie oben rechts auf **[!UICONTROL Vorgabe]**. Wählen Sie anschließend eine Vorgabe aus, um sie auf alle Elemente gleichzeitig anzuwenden.

1. Tippen Sie auf **[!UICONTROL Speichern]**. Das neu erstellte Rotationsset wird in dem Ordner angezeigt, in dem Sie es erstellt haben.

## Anzeigen von Rotationssets   {#viewing-spin-sets}

Sie können Rotationssets in der Benutzeroberfläche oder automatisch über [Stapelsatzvorgaben](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets) erstellen. Mit Stapelsatzvorgaben erstellte Sets werden jedoch *nicht* in der Benutzeroberfläche angezeigt. Es gibt drei verschiedene Arten, auf über Stapelsatzvorgaben erstellte Sätze zuzugreifen. (Diese Methoden sind auch dann verfügbar, wenn Sie die Rotationssets in der Benutzeroberfläche erstellt haben).

Sets können auch über die Benutzeroberfläche angezeigt werden, wie unter [Bearbeiten von Rotationssets](#editing-spin-sets) beschrieben.

**So zeigen Sie Rotationssets an:**

1. Beim Öffnen der Eigenschaften eines einzelnen Assets. Die Eigenschaften zeigen an, zu welchen Sets das ausgewählte Asset gehört (unter **[!UICONTROL Mitglied von Sets]**).  Tippen Sie auf den Namen des Sets, um den gesamten Satz anzuzeigen.

   ![chlimage_1-384](assets/chlimage_1-384.png)

1. Von einem zugehörigen Bild eines beliebigen Sets. Wählen Sie das Menü **[!UICONTROL Sets]** aus, um die Sets anzuzeigen, denen das Asset angehört.

   ![chlimage_1-385](assets/chlimage_1-385.png)

1. From search, you can select **[!UICONTROL Filters]**, then expand **[!UICONTROL Dynamic Media]** and select **[!UICONTROL Sets]**.

   Die Suche gibt Übereinstimmungssätze zurück, die manuell in der Benutzeroberfläche erstellt oder automatisch mithilfe von Stapelsatzvorgaben erstellt wurden. For automated sets, the search query is conducted using **[!UICONTROL Starts with]** search criteria which is different from AEM search which is based on using **[!UICONTROL Contains]** search criteria. Automatisierte Sets können nur durchsucht werden, wenn der Filter auf **[!UICONTROL Sets]** eingestellt ist.

   ![chlimage_1-386](assets/chlimage_1-386.png)

## Bearbeiten von Rotationssets {#editing-spin-sets}

Sie können mehrere Bearbeitungsaufgaben für Rotationssets ausführen, z. B. die folgenden:

* Fügen Sie dem Rotationsset Bilder hinzu.
* Ordnen Sie Bilder im Rotationsset neu an.
* Löschen Sie Assets im Rotationsset.
* Wenden Sie Viewer-Vorgaben an.
* Löschen Sie das Rotationsset.

**So bearbeiten Sie ein Rotationsset:**

1. Führen Sie einen der folgenden Schritte aus:

   * Zeigen Sie mit der Maus auf ein Rotationsset-Asset und tippen Sie auf **[!UICONTROL Bearbeiten]** (Bleistiftsymbol).
   * Zeigen Sie mit der Maus auf ein Rotationsset-Asset und tippen Sie auf **[!UICONTROL Auswählen]** (Häkchensymbol) und dann auf **[!UICONTROL Bearbeiten]** in der Symbolleiste.
   * Tippen Sie auf ein Rotationsset-Asset und dann auf **[!UICONTROL Bearbeiten]** (Bleistiftsymbol) in der Symbolleiste.

1. Führen Sie zum Bearbeiten des Rotationssets einen der folgenden Schritte aus:

   * Ziehen Sie ein Bild, wenn Sie es an einer neuen Position anordnen möchten (zum Verschieben von Elementen wählen Sie das Symbol zum Neuanordnen).
   * Um Elemente in auf- oder absteigender Reihenfolge zu sortieren, tippen Sie auf die Spaltenüberschrift.
   * To add an asset or update an existing asset, tap **[!UICONTROL Add Asset]**. Navigieren Sie zu einem Element, wählen Sie es aus und tippen Sie oben rechts auf **[!UICONTROL Auswählen]**.
Wenn Sie das in AEM als Miniaturansicht verwendete Bild löschen und durch ein anderes ersetzen, wird das Original-Asset weiterhin angezeigt.
   * To delete an asset, select it and tap **[!UICONTROL Delete Asset]**.
   * To apply a preset, tap the **[!UICONTROL Preset]** icon and select a preset.
   * Navigieren Sie zum Löschen eines ganzen Rotationssets zu diesem Rotationsset, wählen Sie es aus und wählen Sie **[!UICONTROL Löschen]**.

      >[!NOTE]
      >* You can edit the images in a Spin Set by navigating to the set, tap **[!UICONTROL Set Members]** in the left rail, and then tap the **[!UICONTROL Edit]** (pencil icon) on an individual asset to open the editing window.


1. Klicken Sie auf **[!UICONTROL Speichern]**, wenn Sie fertig mit der Bearbeitung sind.

## Anzeigen der Vorschau von Rotationssets   {#previewing-spin-sets}

Weitere Informationen finden Sie im Abschnitt [Asset-Vorschau](previewing-assets.md).

## Veröffentlichen von Rotationssets   {#publishing-spin-sets}

Siehe [Veröffentlichen von Assets](publishing-dynamicmedia-assets.md).
