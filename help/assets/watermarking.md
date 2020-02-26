---
title: Bilder mit Wasserzeichen versehen
description: Verwenden Sie die Wasserzeichenfunktion, um Ihren PNG- UND JPEG-Bildern ein digitales Wasserzeichen hinzuzufügen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0e0e2aa693c30c8e1ef1033b936b82d83e5b348e

---


# Wasserzeichen für Assets {#watermarking}

Mit Adobe Experience Manager (AEM) Assets können Sie Bildern ein digitales Wasserzeichen hinzufügen, mit dem Benutzer die Authentizität und das Urheberrecht der Assets überprüfen können. AEM Assets unterstützt die Verwendung von Text als Wasserzeichen auf PNG- und JPEG-Dateien.

To be able to apply watermark on assets, add the [!UICONTROL Watermark] step in the [!UICONTROL DAM Update Asset] workflow.

1. Tap the AEM logo, and go to **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
1. From the Workflow Models page, select the **[!UICONTROL DAM Update Asset]** workflow and click **[!UICONTROL Edit]**.

1. From the side panel, drag the **[!UICONTROL Add Watermark]** step and add it to the [!UICONTROL DAM Update Asset] workflow.

   ![Ziehen des Schritts „Wasserzeichen hinzufügen“ in den Workflow „DAM-Update-Asset“](assets/add_watermark_step_aem_assets.png)

   >[!NOTE]
   >
   >Place the [!UICONTROL Add Watermark] step anywhere before the [!UICONTROL Process Thumbnail] step.

1. Öffnen Sie den Schritt **[!UICONTROL Wasserzeichen hinzufügen]**, um seine Eigenschaften anzuzeigen.
1. Geben Sie auf die Registerkarte **[!UICONTROL Argumente]** gültige Werte in den verschiedenen Feldern an: „Text“, „Schriftart“, „Farbe“, „Position“, „Ausrichtung“ usw. Tippen oder klicken Sie auf das Symbol „Fertig“, um die Änderungen zu bestätigen.

   ![Bereitstellen der Argumente im Schritt „Wasserzeichen hinzufügen“ in Assets](assets/arguments_add_watermark_aem_assets.png)

1. Speichern Sie den **[!UICONTROL DAM Update Asset]**-Workflow beim Wasserzeichenschritt.
1. Laden Sie in der AEM-Benutzeroberfläche ein Beispiel-Asset hoch. Das Wasserzeichen wird mit der Schriftgröße, der Farbe usw. an der Position angezeigt, die Sie in den oben genannten Schritten konfiguriert haben.
