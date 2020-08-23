---
title: Panoramabilder
seo-title: Panoramabilder
description: Erfahren Sie mehr über das Arbeiten mit interaktiven Bildern in Dynamic Media.
seo-description: Erfahren Sie mehr über das Arbeiten mit interaktiven Bildern in Dynamic Media.
uuid: dfd7a55c-7bcc-4d62-8c3a-a73726881103
contentOwner: Rick Brough
topic-tags: dynamic-media
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
discoiquuid: fc285b25-2bce-493c-87bc-5f1a8a26eb42
translation-type: tm+mt
source-git-commit: b698a1348df3ec2ab455c236422784d10cbcf7c2
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 44%

---


# Panoramabilder {#panoramic-images}

In diesem Abschnitt wird beschrieben, wie Sie mit dem Viewer für Panoramabilder Kugelpanoramen für ein immersives 360°-Betrachtungserlebnis eines Zimmers, einer Immobilie, eines Ortes oder einer Landschaft ausgeben können.

Informationen hierzu finden Sie in [Verwalten von Viewer-Vorgaben](managing-viewer-presets.md).

![panoramic-image2](assets/panoramic-image2.png)

## Hochladen von Assets für die Verwendung mit dem Viewer für Panoramabilder {#uploading-assets-for-use-with-the-panoramic-image-viewer}

Damit hochgeladene Assets als Kreispanoramen gelten und mit dem Viewer für Panoramabilder verwendet werden können, muss mindestens eine der beiden folgenden Eigenschaften zutreffen:

* Ein Seitenverhältnis von 2.

   You can override the default aspect ratio setting of 2 in **[!UICONTROL CRXDE Lite]** at the following:

   `/conf/global/settings/cloudconfigs/dmscene7/jcr:content`

* Mit den Keywords `equirectangular` oder `spherical` und `panorama` oder `spherical` und `panoramic` als Tags versehen. Weitere Informationen finden Sie unter [Verwenden von Tags](/help/sites-authoring/tags.md).

Both the aspect ratio and keyword criteria apply to panoramic assets for the asset details page and the **[!UICONTROL Panoramic Media]** component.

Weitere Informationen über den Upload von Assets für die Verwendung mit dem Viewer für Panoramabilder finden Sie unter [Hochladen von Assets](managing-assets-touch-ui.md#uploading-assets).

## Configuring Dynamic Media Classic {#configuring-dynamic-media-classic-scene}

Damit der Panorama-Bild-Viewer in AEM ordnungsgemäß funktioniert, müssen Sie die Viewer-Vorgaben für Panoramabilder mit den für Dynamic Media Classic und Dynamic Media Classic spezifischen Metadaten synchronisieren, damit die Viewer-Vorgaben in der JCR-Datei aktualisiert werden. Konfigurieren Sie dazu Dynamic Media Classic wie folgt:

1. [Melden Sie sich für jedes Firmen-Konto bei Ihrer Instanz von Dynamic Media Classic](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html) an.

1. Klicken Sie oben rechts auf der Seite auf **[!UICONTROL Einstellungen > Anwendungseinstellungen > Veröffentlichungseinrichtung > Image-Server]**.
1. On the **[!UICONTROL Image Server Publish]** page, from the **[!UICONTROL Publish Context]** drop-down menu near the top, select **[!UICONTROL Image Serving]**.

1. On the same **[!UICONTROL Image Server Publish]** page, locate the heading **[!UICONTROL Request Attributes]**.
1. Under the **[!UICONTROL Request Attributes]** heading, locate **[!UICONTROL Reply Image Size Limit]**. Then, in the associated **[!UICONTROL Width]** and **[!UICONTROL Height]** fields, increase the maximum allowable image size for panoramic images.

   Der Wert von Dynamic Media Classic ist auf 25.000.000 Pixel begrenzt. Die maximal zulässige Größe für Bilder mit einem Seitenverhältnis von 2:1 beträgt 7000 x 3500. In der Regel ist für Desktopbildschirme jedoch eine Größe von 4096 x 2048 Pixel ausreichend.

   >[!NOTE]
   >
   >Es werden nur Bilder innerhalb der zulässigen Maximalgröße unterstützt. Anfragen zu Bildern oberhalb der Obergrenze geben einen „403“-Fehler zurück.

1. Under the **[Request Attributes]** heading, do the following:

   * Set **[!UICONTROL Request Obfuscation Mode]** to **[!UICONTROL Disabled]**.
   * Set **[!UICONTROL Request Locking Mode]** to **[!UICONTROL Disabled]**.

   These settings are necessary for using the **[!UICONTROL Panoramic Media]** component in AEM.

1. At the bottom of the **[!UICONTROL Image Server Publish]** page, on the left side, tap **[!UICONTROL Save]**.

1. In the lower-right corner, tap **[!UICONTROL Close]**.

### Troubleshooting the Panoramic Media component {#troubleshooting-the-panoramic-media-wcm-component}

If you dropped an image into the **[!UICONTROL Panoramic Media]** component in your WCM and the component placeholder collapsed, you may want to troubleshoot the following:

* Wenn Ihnen ein 403-Fehler (Forbidden) angezeigt wird, liegt es möglicherweise daran, dass die angefragte Bildgröße den Grenzwert überschreitet. Überprüfen Sie die Einstellungen für *Maximale Größe des Antwortbildes* in [Konfigurieren von Dynamic Media Classic (Scene7)](#configuring-dynamic-media-classic-scene).

* For an *Invalid lock* on the asset or *Parsing error* displayed on the page, check **[!UICONTROL Request Obfuscation Mode]** and **[!UICONTROL Request Locking Mode]** to ensure they are disabled.
* For a tainted canvas error, setup a **[!UICONTROL Rule Set Definition File Path and Invalidate CTN]** for the previous requests for the image asset.
* Wenn die Bildqualität infolge einer Bildanforderung mit einer Größe, die den unterstützten Bereich überschreitet, sehr gering wird, stellen Sie sicher, dass die Einstellung **[!UICONTROL JPEG-Codierungsattribute > Qualität]** nicht leer ist. Eine typische Einstellung für das Feld **[!UICONTROL Qualität]** ist `95`. You can find the setting on the **[!UICONTROL Image Server Publish]** page. To access the page, see [Configuring Dynamic Media Classic](#configuring-dynamic-media-classic-scene).

## Anzeigen einer Vorschau für Panoramabilder {#previewing-panoramic-images}

Weitere Informationen finden Sie im Abschnitt [Asset-Vorschau](previewing-assets.md).

## Veröffentlichen von Panoramabildern   {#publishing-panoramic-images}

Siehe [Veröffentlichen von Assets](publishing-dynamicmedia-assets.md).
