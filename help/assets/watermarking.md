---
title: Hinzufügen von Wasserzeichen zu digitalen Assets
description: Erfahren Sie, wie Sie die Funktion verwenden können, um Assets digitale Wasserzeichen hinzuzufügen.
contentOwner: AG
feature: Asset Management
role: User,Admin
exl-id: ed01143c-b516-44f8-aceb-ad2e3f0106b2
source-git-commit: 1e3cd6ce3138113721183439f7cfb9daed6e0e58
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 77%

---

# Versehen von digitalen Assets mit Wasserzeichen {#watermarking}

[!DNL Adobe Experience Manager Assets] ermöglicht das Hinzufügen eines digitalen Wasserzeichens zu Assets, mit dem Benutzer die Authentizität und das Urheberrecht der Assets überprüfen können. [!DNL Experience Manager Assets] unterstützt die Verwendung von Text als Wasserzeichen auf PNG- und JPEG-Dateien.

Mit Adobe Experience Manager Assets können Sie Bildern ein digitales Wasserzeichen hinzufügen, mit dem Benutzer die Authentizität und das Urheberrecht der Assets überprüfen können. [!DNL Experience Manager] Assets unterstützt die Verwendung von Text als Wasserzeichen auf PNG- und JPEG-Dateien.

Um Wasserzeichen auf Assets anwenden zu können, fügen Sie den Schritt „Wasserzeichen“ im Workflow [!UICONTROL DAM-Update-Asset] hinzu.

1. Öffnen Sie die [!DNL Experience Manager]-Benutzeroberfläche und navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]**.
1. Wählen Sie auf der Seite der Workflow-Modelle den Workflow **[!UICONTROL DAM-Update-Asset]** aus und klicken Sie auf **[!UICONTROL Bearbeiten]**.

1. Ziehen Sie aus dem seitlichen Bedienfeld die **[!UICONTROL Wasserzeichen hinzufügen]** und fügen Sie ihn dem [!UICONTROL DAM-Update-Asset] Arbeitsablauf.

   ![Ziehen Sie den Schritt &quot;Wasserzeichen hinzufügen&quot;in den Workflow &quot;DAM-Update-Asset&quot;](assets/add_watermark_step_aem_assets.png)

   >[!NOTE]
   >
   >Ordnen Sie den Schritt [!UICONTROL Wasserzeichen hinzufügen] an beliebiger Stelle vor dem Schritt [!UICONTROL Miniaturansichten verarbeiten] ein.

1. Öffnen Sie den Schritt **[!UICONTROL Wasserzeichen hinzufügen]**, um seine Eigenschaften anzuzeigen.
1. Geben Sie auf die Registerkarte **[!UICONTROL Argumente]** gültige Werte in den verschiedenen Feldern an: „Text“, „Schriftart“, „Farbe“, „Position“, „Ausrichtung“ usw. Um die Änderungen zu bestätigen, klicken Sie auf **[!UICONTROL Fertig]**.

   ![Bereitstellen der Argumente im Schritt „Wasserzeichen hinzufügen“ in Assets](assets/arguments_add_watermark_aem_assets.png)

1. Speichern Sie den Workflow **[!UICONTROL DAM-Update-Asset]** mit dem Schritt „Wasserzeichen“.
1. Laden Sie über die [!DNL Experience Manager]-Benutzeroberfläche ein Beispiel-Asset hoch. Das Wasserzeichen wird mit der Schriftgröße, Farbe usw. an der Position angezeigt, die Sie in den oben genannten Schritten konfiguriert haben.

Wenn Sie PDF-Dokumente programmgesteuert oder mit dynamischen Informationen mit Wasserzeichen versehen möchten, sollten Sie [[!DNL Experience Manager]  Document Services](/help/forms/using/overview-aem-document-services.md) nutzen.

## Tipps und Einschränkungen {#tips-limitations}

* Es werden nur textbasierte Wasserzeichen unterstützt. Bilder werden nicht als Wasserzeichen verwendet, auch wenn Sie beim Erstellen des Prozesses [!UICONTROL Wasserzeichen hinzufügen] Bilder hochladen können.
* Nur PNG- und JPEG-Dateien können mit Wasserzeichen versehen werden. Andere Asset-Formate werden nicht mit Wasserzeichen versehen.
