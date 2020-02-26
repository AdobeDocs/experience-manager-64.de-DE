---
title: Integration von AEM 3D mit Autodesk Maya
seo-title: Integration von AEM 3D mit Autodesk Maya
description: Sie können AEM 3D optional mit Autodesk® Maya® integrieren, um die Unterstützung für native Maya-Dateien (.MA und .MB) zu aktivieren und 3D-Assets in AEM mit jedem verfügbaren Maya-Renderer zu rendern.
seo-description: Sie können AEM 3D optional mit Autodesk® Maya® integrieren, um die Unterstützung für native Maya-Dateien (.MA und .MB) zu aktivieren und 3D-Assets in AEM mit jedem verfügbaren Maya-Renderer zu rendern.
uuid: 07ff17b6-bdfc-4617-8b16-42aaf5c73fc7
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 3d063268-17d7-4db6-8028-682537645377
translation-type: tm+mt
source-git-commit: e2bb2f17035e16864b1dc54f5768a99429a3dd9f

---


# Integration von AEM 3D mit Autodesk Maya {#integrating-aem-d-with-autodesk-maya}

>[!NOTE]
>
>Diese Aufgabe ist optional und nur unter Windows verfügbar.

You can optionally integrate AEM 3D with Autodesk® Maya® software to enable support for native Maya files (`.MA` and `.MB`) and to let you render 3D assets in AEM with any available Maya renderer.

*Diese Integration gilt nur* für Windows.

Bei der Integration von Autodesk Maya müssen Sie Autodesk Maya installieren und konfigurieren, den Pfad zum Ordner mit den Maya-Programmdateien hinzufügen, Maya für Aufnahme und Rendering aktivieren und die Integration testen.

See [Advanced configuration settings](advanced-config-3d.md).

Siehe auch [Integration von AEM 3D mit AutoDesk 3ds Max](integrating-aem-3d-with-autodesk-3ds-max.md).

**So integrieren Sie Autodesk Maya in AEM 3D**:

1. Installieren Sie die Autodesk Maya 2016-Software auf denselben Servern, auf denen AEM gehostet wird.

   Vergewissern Sie sich nach der Installation, dass Sie Maya öffnen sowie verwenden können und keine Lizenzprobleme auftreten.

   >[!NOTE]
   >
   >AEM verwendet nur das Befehlszeilen-Rendering-Tool von Maya (`render.exe`). Mit einer einzelnen Maya-Netzwerklizenz können bis zu fünf Server gleichzeitig Maya-Inhalte verarbeiten oder rendern.

1. Aktivieren Sie in Maya das Autodesk FBX® Plug-In.
1. Installieren Sie das MentalRay-Render-Plug-in oder einen anderen gewünschten Renderer.

   Nach der Installation sollten Sie sicherstellen, dass MentalRay in Maya verfügbar ist.

1. Fügen Sie den Pfad zur ausführbaren Maya-Datei zur Windows-PATH-Umgebungsvariable hinzu.

   For example, on Windows Server 2012, tap **[!UICONTROL Start > Control Panel > System and Security > System > Advanced System Settings > Environment Variables**. Append the full path to the `Maya2016\bin` folder to the `Path`system variable.

   ![chlimage_1-53](assets/chlimage_1-53.png)

1. Um Maya für die Erfassung und Wiedergabe zu aktivieren, öffnen Sie **[!UICONTROL CRXDE Lite]** , navigieren Sie zu `/libs/settings/dam/v3D/assetTypes/maya` und legen Sie die **[!UICONTROL Enabled]** -Eigenschaft auf `true`fest.

   ![image2018-6-22_12-42-7](assets/image2018-6-22_12-42-7.png)

1. To enable the JT (Siemens PLM Open CAD) file format, navigate to `/libs/settings/dam/v3D/assetTypes/jt` and set the **[!UICONTROL Enabled]** property to `true`.
1. Aktivieren Sie Maya in AEM Maya als Renderer. Navigieren Sie dazu zu **[!UICONTROL Tools > Allgemein > CRXDE Lite]**.
1. From the **[!UICONTROL CRXDE Lite]** page, in the left panel, navigate to the following:

   `/libs/settings/dam/v3D/renderers/maya`

   ![image2018-6-22_12-46-18](assets/image2018-6-22_12-46-18.png)

1. Setzen Sie die Eigenschaft **[!UICONTROL Aktiviert]** auf `true`.

1. Near the upper-left corner of the **[!UICONTROL CRXDE Lite]** page, tap **[!UICONTROL Save All]**.

   Maya ist nun als Renderer aktiviert.

## Testen der Integration von AEM 3D in Autodesk Maya {#testing-the-integration-of-aem-d-with-autodesk-maya}

1. Open AEM Assets, then upload the `.MA` files located in `sample-3D-content/models` to the `test3d` folder.

   Beachten Sie, dass `sample-3D-content.zip` zuvor zum Überprüfen der grundlegenden 3D-Funktionen heruntergeladen wurde.

1. Return to the **[!UICONTROL Card** view and observe the message banners shown on the uploaded assets.

   The Converting Format banner is displayed while Maya is converting the native `.MA` format to `.FBX`.

1. Nachdem die Verarbeitung abgeschlossen ist, öffnen Sie das `logo-sphere.ma` Asset und wählen Sie die `stage-helipad.ma` Bühne aus.

   Das Vorschaufenster ist dasselbe wie mit `logo_sphere.fbx` und `stage-helipad.fbx`.

1. Near the upper-left corner of the page, tap or click the drop-down list and then select **[!UICONTROL CRender]**.

   ![chlimage_1-54](assets/chlimage_1-54.png)

1. In the **[!UICONTROL Renderer]** drop-down list, select **[!UICONTROL Autodesk Maya]**, then tap **[!UICONTROL Start Render]**.
1. Near the upper-right corner of the page, tap or click **[!UICONTROL Close]** to return to the **[!UICONTROL Card]** view.

   Beobachten Sie das Meldungsbanner auf dem Bild-Asset, das gerendert wird (`logo-sphere`sofern kein anderer Bildname angegeben wurde). Ein Fortschrittsbalken auf dem Banner zeigt den Rendering-Fortschritt.

   >[!NOTE]
   >
   >Das Rendern ist sehr CPU-intensiv und kann einige Minuten dauern

1. Nachdem das Rendern abgeschlossen ist, öffnen Sie das gerenderte Bild-Asset.

   Check that the rendered image reasonably matches the image that you were viewing at the time you clicked **[!UICONTROL Render Now]**.

## Aktivieren zusätzlicher von Maya unterstützter Formate {#enabling-additional-formats-supported-by-maya}

(Optional) Maya unterstützt eine Reihe von 3D-Eingabeformaten, von denen jedes aktiviert werden kann, damit AEM den Dateityp erkennt. Wenn diese Option aktiviert ist, sendet AEM die Datei an Maya, um sie in ein Zwischenformat zu konvertieren, das direkt von AEM aufgenommen werden kann.

Je nach Format kann die Unterstützung für Funktionen eingeschränkt sein (z. B. werden Materialien nicht weitergegeben) und Qualität/Treue kann eingeschränkt sein (z. B. umgekehrte Gesichter). Adobe unterstützt nur den allgemeinen Mechanismus, jedoch keine bestimmte Formatkonversion.

See [Supported Data Import Formats | Maya](https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2016/ENU/Maya/files/GUID-69BC066D-D4D8-4B12-900C-CF42E798A5D6-htm.html) for information about the formats supported by Maya.

**So aktivieren Sie weitere von AEM** unterstützte Formate:

1. Navigieren Sie mit **[!UICONTROL CRXDE Lite]** zu `/libs/settings/dam/v3D/assetTypes`.
1. Make a copy of the **[!UICONTROL jt]** node. Right-click on the **[!UICONTROL jt]** node and select **[!UICONTROL Copy]**, then right-click the **[!UICONTROL assetTypes]** folder and select **[!UICONTROL Paste]**. Dadurch sollte ein neuer Knoten erstellt werden `/apps/cq-scene7-v3D/config/assetTypes/Copy of jt`.
1. Benennen Sie den neuen Knoten um. Wählen Sie hierbei einen Namen, der den hinzuzufügenden Dateityp beschreibt. Sie können das Dateisuffix oder eine beliebige andere eindeutige ID verwenden.

1. Set the **[!UICONTROL Enabled]** property of the new node to `true`.

1. Set the **[!UICONTROL Extension]** property of the new note to the file suffix/extension of the format being added.
1. Set the **[!UICONTROL MimeType]** property to an appropriate value. `application/x-` gefolgt vom Wert der **[!UICONTROL Extension]** -Eigenschaft sollte für die meisten Dateitypen funktionieren.
1. Make certain that the **[!UICONTROL Conversion]** property is set to `fbx` and **[!UICONTROL IngestRegime]** to `Maya`.
1. Click **[!UICONTROL Save All]** near the top left of the page.

Im folgenden Screenshot wird ein hinzugefügtes Dateiformat veranschaulicht, wobei COLLADA DAE als Beispiel verwendet wird:

![image2018-6-22_12-50-39](assets/image2018-6-22_12-50-39.png)

