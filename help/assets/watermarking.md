---
title: Hinzufügen von Wasserzeichen zu digitalen Assets
description: Erfahren Sie, wie Sie die Funktion verwenden können, um Assets digitale Wasserzeichen hinzuzufügen.
contentOwner: AG
feature: Asset Management
role: Business Practitioner,Administrator
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 36%

---


# Markieren Sie Ihre digitalen Assets {#watermarking}

[!DNL Adobe Experience Manager Assets] ermöglicht es Ihnen, Assets ein digitales Wasserzeichen hinzuzufügen, mit dem Benutzer die Authentizität und das Urheberrecht der Assets überprüfen können. [!DNL Experience Manager Assets] unterstützt die Verwendung von Text als Wasserzeichen auf PNG- und JPEG-Dateien.

Mit Adobe Experience Manager (AEM) Assets können Sie Bildern ein digitales Wasserzeichen hinzufügen, mit dem Benutzer die Authentizität und das Urheberrecht der Assets überprüfen können. AEM Assets unterstützt die Verwendung von Text als Wasserzeichen auf PNG- und JPEG-Dateien.

Um Wasserzeichen auf Assets anwenden zu können, fügen Sie den Wasserzeichenschritt im Arbeitsablauf [!UICONTROL DAM-Aktualisierung des Assets] hinzu.

1. Rufen Sie die [!DNL Experience Manager]-Benutzeroberfläche auf und gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]**.
1. Wählen Sie auf der Seite der Workflow-Modelle den Workflow **[!UICONTROL DAM-Update-Asset]** aus und klicken Sie auf **[!UICONTROL Bearbeiten]**.

1. Ziehen Sie aus dem Seitenbedienfeld den Schritt **[!UICONTROL Hinzufügen Wasserzeichen]** und fügen Sie ihn dem Arbeitsablauf [!UICONTROL DAM-Update-Asset] hinzu.

   ![Ziehen Sie den Schritt zum Hinzufügen eines Wasserzeichens in den DAM-Workflow zum Aktualisieren von Assets](assets/add_watermark_step_aem_assets.png)

   >[!NOTE]
   >
   >Platzieren Sie den Schritt [!UICONTROL Hinzufügen Wasserzeichen] an einer beliebigen Stelle vor dem Schritt [!UICONTROL Prozessminiatur].

1. Öffnen Sie den Schritt **[!UICONTROL Wasserzeichen hinzufügen]**, um seine Eigenschaften anzuzeigen.
1. Geben Sie auf die Registerkarte **[!UICONTROL Argumente]** gültige Werte in den verschiedenen Feldern an: „Text“, „Schriftart“, „Farbe“, „Position“, „Ausrichtung“ usw. Um die Änderungen zu bestätigen, klicken Sie auf **[!UICONTROL Fertig]**.

   ![Bereitstellen der Argumente im Schritt „Wasserzeichen hinzufügen“ in Assets](assets/arguments_add_watermark_aem_assets.png)

1. Speichern Sie den Workflow **[!UICONTROL DAM-Update-Asset]** mit dem Schritt „Wasserzeichen“.
1. Laden Sie in der AEM Benutzeroberfläche ein Beispiel-Asset hoch. Das Wasserzeichen wird mit der Schriftgröße, der Farbe usw. an der Position angezeigt, die Sie in den oben genannten Schritten konfiguriert haben.

Um PDF-Dokumente programmgesteuert oder mit dynamischen Informationen zu versehen, sollten Sie das Angebot [AEM Dokument Services](/help/forms/using/overview-aem-document-services.md) verwenden.

## Tipps und Einschränkungen {#tips-limitations}

* Nur textbasierte Wasserzeichen werden unterstützt. Bilder werden nicht als Wasserzeichen verwendet, auch wenn Sie Bilder beim Erstellen des [!UICONTROL Hinzufügen Wasserzeichenprozesses] hochladen können.
* Es werden nur PNG- und JPEG-Dateien als Wasserzeichen unterstützt. Andere Asset-Formate sind nicht mit Wasserzeichen versehen.
