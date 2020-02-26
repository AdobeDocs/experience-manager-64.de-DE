---
title: Verwalten von Video-Assets
description: Erfahren Sie, wie Sie Video-Assets hochladen und veröffentlichen, eine Vorschau der entsprechenden Assets anzeigen und Anmerkungen hinzufügen können.
uuid: 56a8c221-409f-4605-97b1-a054dd2abfab
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: f341fae1-dda3-4917-b6db-ad02fec63702
translation-type: tm+mt
source-git-commit: 9ced187ddc9bb2d12922fcc734b20ef9767d8fbf

---


# Verwalten von Video-Assets {#managing-video-assets}

Lernen Sie, wie Sie die Video-Assets in Adobe Experience Manager (AEM) Assets verwalten und bearbeiten. Wenn Sie eine Lizenz für die Nutzung von Dynamic Media besitzen, sehen Sie sich die [Dynamic Media-Videodokumentation](video.md) an.

## Upload and preview video assets {#uploading-and-previewing-video-assets}

AEM Assets generiert Vorschauen für Video-Assets mit der Erweiterung MP4.  Wenn das Format des Assets nicht MP4 ist, installieren Sie das FFmpeg-Paket, um eine Vorschau zu generieren.  FFmpeg erstellt Videodarstellungen vom Typ OGG und MP4. Sie können eine Vorschau dieser Wiedergaben in der Benutzeroberfläche von AEM Assets anzeigen.

1. Navigieren Sie im Ordner &quot;Digitale Assets&quot;oder in den Unterordnern zu dem Speicherort, an dem Sie digitale Assets hinzufügen möchten.
1. Um Assets hochzuladen, klicken oder tippen Sie in der Symbolleiste auf **[!UICONTROL Erstellen]** und wählen Sie dann **[!UICONTROL Dateien]** aus. Alternativ können Sie sie direkt in den Assets-Bereich ziehen. See [Uploading assets](managing-assets-touch-ui.md#uploading-assets) for details around the upload operation.
1. To preview a video in the Card view, tap the **[!UICONTROL Play]** button on the video asset.

   ![chlimage_1-201](assets/chlimage_1-201.png)

   You can pause or play video in the **[!UICONTROL Card]** view only. The Play/Pause button is not available in the **[!UICONTROL List]** view.

1. Tippen Sie auf das Symbol **[!UICONTROL Bearbeiten]** auf der Karte, um eine Vorschau des Videos in der **[!UICONTROL Detailansicht]** anzuzeigen.

   Das Video wird im systemeigenen Videoplayer des Browsers wiedergegeben. Sie können das Video wiedergeben und anhalten, die Lautstärke regeln und in den Vollbildmodus wechseln.

   ![chlimage_1-202](assets/chlimage_1-202.png)

## Configuration to upload assets that are larger than 2 GB {#configuration-to-upload-video-assets-that-are-larger-than-gb}

Standardmäßig können Sie mit den AEM-Assets keine Assets hochladen, die aufgrund einer Dateigrößenbeschränkung größer als 2 GB sind. However, you can overwrite this limit by going into CRXDE Lite and creating a node under the `/apps` directory. Der Knoten muss denselben Knotennamen, dieselbe Verzeichnisstruktur und vergleichbare Knoteneigenschaften im Hinblick auf die Reihenfolge aufweisen.

Zusätzlich zur AEM Assets-Konfiguration ändern Sie die folgenden Konfigurationen, um große Assets hochzuladen:

* Erhöhen Sie die Ablaufzeit des Tokens. Siehe [!UICONTROL Adobe Granite CSRF Servlet] in Web Console unter `https://[aem_server]:[port]/system/console/configMgr`. Weitere Informationen finden Sie unter [CSRF-Schutz](/help/sites-developing/csrf-protection.md).
* Erhöhen Sie die `receiveTimeout` in der Dispatcher-Konfiguration. Weitere Informationen finden Sie unter [Experience Manager Dispatcher-Konfiguration](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#renders-options).

>[!NOTE]
>
>Die AEM Classic-Benutzeroberfläche unterliegt keiner Beschränkung der Dateigröße von zwei Gigabyte. Außerdem werden End-to-End-Workflows für große Videos nicht vollständig unterstützt.

To configure a higher file size limit, perform the following steps in the `/apps` directory.

1. Tippen Sie in AEM auf **[!UICONTROL Werkzeuge > Allgemein > CRXDE Lite]**.
1. In the **[!UICONTROL CRXDE Lite]** page, in the directory window on the left, navigate to `/libs/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload`. To see the directory window, touch `>>` icon.
1. From the toolbar, tap **[!UICONTROL Overlay Node]**. Alternativ können Sie im Kontextmenü die Option **[!UICONTROL Überlagerungsknoten]** auswählen.
1. Tippen Sie im Dialogfeld **[!UICONTROL Überlagerungsknoten]** auf **[!UICONTROL OK]**.

   ![chlimage_1-203](assets/chlimage_1-203.png)

1. Aktualisieren Sie die Browser-Ansicht. Der Überlagerungsknoten `/jcr_root/apps/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload` ist ausgewählt.
1. In the **[!UICONTROL Properties]** tab, enter the appropriate value in bytes to increase the size limit to the desired size. Geben Sie beispielsweise den folgenden Wert ein, um die maximale Größe auf 30 GB zu erhöhen:

   `{sizeLimit : "32212254720"}`

1. From the toolbar, tap **[!UICONTROL Save All]**.
1. Tippen Sie in AEM auf **[!UICONTROL Werkzeuge > Vorgänge > Web Console]**.
1. On the **[!UICONTROL Adobe Experience Manager Web Console Bundles]** page, under the **[!UICONTROL Name]** column of the table, locate and tap **[!UICONTROL Adobe Granite Workflow External Process Job Handler]**.
1. In the **[!UICONTROL Adobe Granite Workflow External Process Job Handler]** page, set the seconds for both **[!UICONTROL Default Timeout]** and **[!UICONTROL Max Timeout]** fields to `18000` (five hours).
1. Tippen Sie auf **[!UICONTROL Speichern]**.
1. Tippen Sie in AEM auf **[!UICONTROL Tools > Workflow > Modelle]**.
1. On the **[!UICONTROL Workflow Models]** page, select **[!UICONTROL Dynamic Media Encode Video]**, then tap **[!UICONTROL Edit]**.
1. On the **[!UICONTROL Workflow]** page, double-tap the **[!UICONTROL Dynamic Media Video Service Process]** component.
1. Erweitern Sie im Dialogfeld **[!UICONTROL Schritteigenschaften]** unter der Registerkarte **[!UICONTROL Allgemein]** die Option **[!UICONTROL Erweiterte Einstellungen]**.
1. Geben Sie im Feld **[!UICONTROL Timeout]** den Wert `18000` an und tippen Sie dann auf **[!UICONTROL OK]**, um zur Workflow-Seite **[!UICONTROL Videokodierung mit dynamischen Medien]** zurückzukehren.
1. Near the top of the page, below the **[!UICONTROL Dynamic Media Encode Video]** page title, tap **[!UICONTROL Save]**.

## Veröffentlichen von Video-Assets {#publishing-video-assets}

Nach dem Veröffentlichen Ihrer Video-Assets können diese über eine URL auf einer Webseite eingebunden oder eingebettet werden. Siehe [Veröffentlichen von Assets](publishing-dynamicmedia-assets.md).

## Video-Assets kommentieren {#annotating-video-assets}

1. From the Assets console, tap the **[!UICONTROL Edit]** icon on the asset card to display the asset details page.
1. Tap the **[!UICONTROL Preview]** icon to play the video.
1. To annotate the video, tap the **[!UICONTROL Annotate]** button. Eine Anmerkung wird an diesem speziellen Zeitpunkt (Frame) im Video hinzugefügt.

   Beim Hinzufügen von Anmerkungen können Sie auf der Arbeitsfläche zeichnen und einen Kommentar zur Zeichnung aufnehmen. Kommentare werden automatisch in Adobe Experience Manager-Assets gespeichert.

   ![chlimage_1-204](assets/chlimage_1-204.png)

   To exit the annotation wizard, tap **[!UICONTROL Close]**.

1. To jump to a specific point in the video, specify the time in seconds in the text field and click **[!UICONTROL Jump]**. Um beispielsweise die ersten Sekunden des Videos zu überspringen, geben Sie `20`10 in das Textfeld ein.

   ![chlimage_1-205](assets/chlimage_1-205.png)

1. Klicken Sie auf eine Anmerkung, um sie in der Zeitleiste anzuzeigen. Tap **[!UICONTROL Delete]** to remove the annotation from the timeline.

   ![chlimage_1-206](assets/chlimage_1-206.png)
