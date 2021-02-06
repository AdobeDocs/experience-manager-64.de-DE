---
title: Unterstützung von Camera Raw
description: Erfahren Sie, wie Sie Camera Raw Support in Adobe Experience Manager Assets aktivieren.
contentOwner: AG
translation-type: tm+mt
source-git-commit: dea673f8999656a5c5364f74f45eba41dd17b947
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 45%

---


# Verwenden Sie Camera Raw, um Bilder zu verarbeiten {#camera-raw-support}

Sie können die Camera Raw unterstützte Verarbeitung von Rohdateiformaten wie CR2, NEF und RAF aktivieren und die Bilder im JPEG-Format wiedergeben. Die Funktion wird in Adobe Experience Manager Assets mit dem unter Softwareverteilung verfügbaren Camera Raw-Paket](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/aem630/product/assets/aem-assets-cameraraw-pkg) unterstützt.[

>[!NOTE]
>
>Die Funktion unterstützt nur JPEG-Darstellungen. Es wird unter Windows 64 Bit, Mac OS und RHEL 7.x unterstützt.

Gehen Sie wie folgt vor, um Camera Raw Support in Adobe Experience Manager Assets zu aktivieren:

1. Laden Sie das [Camera Raw-Paket](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/aem630/product/assets/aem-assets-cameraraw-pkg) aus der Softwareverteilung herunter.

1. Greife Sie auf `https://[aem_server]:[port]/workflow` zu. Öffnen Sie den Workflow **[!UICONTROL DAM Update Asset]**.

1. Öffnen Sie den Schritt **[!UICONTROL Prozessminiaturen]**.

1. Geben Sie auf der Registerkarte **[!UICONTROL Miniaturansichten]** die folgende Konfiguration ein:

   * **[!UICONTROL Miniaturansichten]**:  `140:100:false, 48:48:false, 319:319:false`
   * **[!UICONTROL MIME-Typen überspringen]**: `skip:image/dng, skip:image/x-raw-(.*)`

   ![CHlimage](assets/chlimage_1-334.png)

1. Geben Sie auf der Registerkarte **[!UICONTROL Web-aktiviertes Bild]** im Feld **[!UICONTROL Liste]** überspringen `audio/mpeg, video/(.*), image/dng, image/x-raw-(.*)` an.

   ![CHlimage](assets/chlimage_1-335.png)

1. Fügen Sie im Seitenbedienfeld den Schritt **[!UICONTROL Camera Raw/DNG-Handler]** unter dem Schritt **[!UICONTROL Erstellung der Miniaturansicht]** hinzu.

1. Fügen Sie im Schritt **[!UICONTROL Camera Raw/DNG Handler]** die folgende Konfiguration in der Registerkarte **[!UICONTROL Argumente]** hinzu:

   * **[!UICONTROL Mime-Typen]**:  `image/dng` und  `image/x-raw-(.*)`
   * **[!UICONTROL Befehl]**:

      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.web.1280.1280.jpeg 1280 1280`
      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.319.319.jpeg 319 319`
      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.140.100.jpeg 140 100`
      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.48.48.jpeg 48 48`

   ![chlimage_1-336](assets/chlimage_1-336.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**.

>[!NOTE]
>
>Stellen Sie sicher, dass die oben aufgeführte Konfiguration mit der Konfiguration **** Beispiel-DAM-Update-Asset mit Schritt für Camera RAW- und DNG-Handling übereinstimmt.

Nun können Sie Camera Raw-Dateien in AEM Assets importieren. Nachdem Sie das Camera Raw-Paket installiert und den erforderlichen Arbeitsablauf konfiguriert haben, wird die Option **[!UICONTROL Bildanpassung]** in der Liste der Seitenfenster angezeigt.

![chlimage_1-337](assets/chlimage_1-337.png)

*Abbildung: Optionen im Seitenbereich*

![chlimage_1-338](assets/chlimage_1-338.png)

*Abbildung: Verwenden Sie diese Option, um Ihre Bilder leichter zu bearbeiten*

Nach Speichern der Änderungen in einem Camera Raw-Bild wird die neue Darstellung `AdjustedPreview.jpg` für das Bild erstellt. Für andere Bildtypen als Camera Raw werden die Änderungen in allen Darstellungen übernommen.

## Best Practices, bekannte Probleme und Einschränkungen {#best-practices}

Für die Funktionalität gelten folgende Einschränkungen:

* Die Funktion unterstützt nur JPEG-Darstellungen. Sie wird unter 64-Bit Windows, macOS und RHEL 7.x unterstützt.
* Metadaten-Writeback wird für RAW- und DNG-Formate nicht unterstützt.
* Für die Camera Raw-Bibliothek gelten Beschränkungen bei der gleichzeitig verarbeiteten Gesamtanzahl von Pixel. Derzeit kann eine Datei maximal 65000 Pixel auf der langen Seite oder 512 MP verarbeitet werden, je nachdem, welches Kriterium zuerst erfüllt wird.
