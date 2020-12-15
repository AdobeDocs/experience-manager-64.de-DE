---
title: Bilder mit Wasserzeichen versehen
description: Verwenden Sie die Wasserzeichenfunktion, um Ihren PNG- UND JPEG-Bildern ein digitales Wasserzeichen hinzuzufügen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 04de28347ddf0082d2e224aa3853297cad3aacd8
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 41%

---


# Versehen Sie Assets mit Wasserzeichen {#watermarking}

Mit Adobe Experience Manager (AEM) Assets können Sie Bildern ein digitales Wasserzeichen hinzufügen, mit dem Benutzer die Authentizität und das Urheberrecht der Assets überprüfen können. AEM Assets unterstützt die Verwendung von Text als Wasserzeichen auf PNG- und JPEG-Dateien.

Um Wasserzeichen auf Assets anwenden zu können, fügen Sie den Schritt [!UICONTROL Wasserzeichen] im Arbeitsablauf [!UICONTROL DAM-Update-Asset] hinzu.

1. Tippen Sie auf das AEM Logo und gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]**.
1. Wählen Sie auf der Seite der Workflow-Modelle den Workflow **[!UICONTROL DAM-Update-Asset]** aus und klicken Sie auf **[!UICONTROL Bearbeiten]**.

1. Ziehen Sie aus dem Seitenbedienfeld den Schritt **[!UICONTROL Hinzufügen Wasserzeichen]** und fügen Sie ihn dem Arbeitsablauf [!UICONTROL DAM-Update-Asset] hinzu.

   ![Ziehen des Schritts „Wasserzeichen hinzufügen“ in den Workflow „DAM-Update-Asset“](assets/add_watermark_step_aem_assets.png)

   >[!NOTE]
   >
   >Platzieren Sie den Schritt [!UICONTROL Hinzufügen Wasserzeichen] an einer beliebigen Stelle vor dem Schritt [!UICONTROL Prozessminiatur].

1. Öffnen Sie den Schritt **[!UICONTROL Wasserzeichen hinzufügen]**, um seine Eigenschaften anzuzeigen.
1. Geben Sie auf die Registerkarte **[!UICONTROL Argumente]** gültige Werte in den verschiedenen Feldern an: „Text“, „Schriftart“, „Farbe“, „Position“, „Ausrichtung“ usw. Tippen oder klicken Sie auf das Symbol „Fertig“, um die Änderungen zu bestätigen.

   ![Bereitstellen der Argumente im Schritt „Wasserzeichen hinzufügen“ in Assets](assets/arguments_add_watermark_aem_assets.png)

1. Speichern Sie den Workflow **[!UICONTROL DAM-Update-Asset]** mit dem Schritt „Wasserzeichen“.
1. Laden Sie in der AEM Benutzeroberfläche ein Beispiel-Asset hoch. Das Wasserzeichen wird mit der Schriftgröße, der Farbe usw. an der Position angezeigt, die Sie in den oben genannten Schritten konfiguriert haben.

Um PDF-Dokumente programmgesteuert oder mit dynamischen Informationen zu versehen, sollten Sie das Angebot [AEM Dokument Services](/help/forms/using/overview-aem-document-services.md) verwenden.
