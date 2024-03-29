---
title: Unterstützung von Camera Raw
description: Erfahren Sie, wie Sie die Camera Raw Unterstützung in Adobe Experience Manager Assets aktivieren.
contentOwner: AG
feature: Developer Tools
role: Admin
exl-id: 637c57ae-55a6-4032-9821-b55839b3e567
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 49%

---

# Verwenden von Camera Raw zur Bildverarbeitung {#camera-raw-support}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Sie können die Camera Raw Unterstützung aktivieren, um Rohdateiformate wie CR2, NEF und RAF zu verarbeiten und die Bilder im JPEG-Format zu rendern. Die Funktion wird in Adobe Experience Manager Assets mit dem [Camera Raw Package](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/aem630/product/assets/aem-assets-cameraraw-pkg) über Softwareverteilung verfügbar.

>[!NOTE]
>
>Die Funktion unterstützt nur JPEG-Darstellungen. Sie wird unter Windows 64-Bit, macOS und RHEL 7.x unterstützt.

Gehen Sie wie folgt vor, um die Camera Raw Unterstützung in Adobe Experience Manager Assets zu aktivieren:

1. Laden Sie die [Camera Raw Package](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/aem630/product/assets/aem-assets-cameraraw-pkg) über die Softwareverteilung.

1. Greife Sie auf `https://[aem_server]:[port]/workflow` zu. Öffnen Sie den Workflow **[!UICONTROL DAM-Update-Asset]**.

1. Öffnen Sie die **[!UICONTROL Prozessminiaturansichten]** Schritt.

1. Legen Sie auf der Registerkarte **[!UICONTROL Miniaturansichten]** folgende Konfiguration fest:

   * **[!UICONTROL Miniaturansichten]**: `140:100:false, 48:48:false, 319:319:false`
   * **[!UICONTROL MIME-Typen überspringen]**: `skip:image/dng, skip:image/x-raw-(.*)`

   ![chlimage](assets/chlimage_1-334.png)

1. Geben Sie auf der Registerkarte **[!UICONTROL Webfähiges Bild]** im Feld **[!UICONTROL Liste überspringen]** `audio/mpeg, video/(.*), image/dng, image/x-raw-(.*)` an.

   ![chlimage](assets/chlimage_1-335.png)

1. Fügen Sie im seitlichen Bedienfeld die **[!UICONTROL Camera Raw/DNG Handler]** Schritt unter dem **[!UICONTROL Erstellung von Miniaturansichten]** Schritt.

1. Fügen Sie im Schritt **[!UICONTROL Camera Raw/DNG Handler]** auf der Registerkarte **[!UICONTROL Argumente]** die folgende Konfiguration hinzu:

   * **[!UICONTROL MIME-Typen]**: `image/dng` und `image/x-raw-(.*)`
   * **[!UICONTROL Befehl]**:

      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.web.1280.1280.jpeg 1280 1280`
      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.319.319.jpeg 319 319`
      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.140.100.jpeg 140 100`
      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.48.48.jpeg 48 48`

   ![chlimage_1-336](assets/chlimage_1-336.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**.

>[!NOTE]
>
>Stellen Sie sicher, dass die oben aufgeführte Konfiguration mit der Konfiguration **[!UICONTROL Beispiel-DAM-Update-Asset mit Schritt für Camera RAW- und DNG-Handling]** übereinstimmt.

Sie können jetzt Kamera-Rohdateien in [!DNL Experience Manager] Assets. Nach der Installation des Camera RAW-Pakets und der Konfiguration des erforderlichen Workflows wird die Option **[!UICONTROL Bildanpassung]** in der Liste der seitlichen Bedienfelder angezeigt.

![chlimage_1-337](assets/chlimage_1-337.png)

*Abbildung: Optionen im seitlichen Bedienfeld*

![chlimage_1-338](assets/chlimage_1-338.png)

*Abbildung: Verwenden Sie die Option, um Ihre Bilder geringfügig zu bearbeiten*

Nach dem Speichern der Änderungen in einem Camera Raw Bild, eine neue Ausgabedarstellung `AdjustedPreview.jpg` wird für das Bild generiert. Bei anderen Bildtypen außer Camera Raw werden die Änderungen in allen Ausgabedarstellungen übernommen.

## Best Practices, bekannte Probleme und Einschränkungen {#best-practices}

Die Funktionalität weist die folgenden Einschränkungen auf:

* Die Funktion unterstützt nur JPEG-Darstellungen. Es wird unter Windows 64 Bit, Mac OS und RHEL 7.x unterstützt.
* Metadaten-Writeback wird für RAW- und DNG-Formate nicht unterstützt.
* Die Camera Raw Bibliothek weist Einschränkungen hinsichtlich der Gesamtpixel auf, die gleichzeitig verarbeitet werden können. Derzeit kann sie eine maximale Größe von 65.000 Pixel auf der langen Seite einer Datei oder 512 MP verarbeiten, je nachdem, welches Kriterium zuerst erfüllt wird.
