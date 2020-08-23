---
title: Integration von AEM 3D mit Autodesk 3ds Max
seo-title: Integration von AEM 3D mit AutoDesk 3ds Max.
description: Sie können optional AEM 3D mit der Autodesk 3ds Max Software integrieren, um die Unterstützung für native 3ds Max-Dateien (.MAX) zu aktivieren. Das Rendering mittels 3ds Max wird derzeit nicht unterstützt.
seo-description: Sie können optional AEM 3D mit der Autodesk 3ds Max Software integrieren, um die Unterstützung für native 3ds Max-Dateien (.MAX) zu aktivieren. Das Rendering mittels 3ds Max wird derzeit nicht unterstützt.
uuid: 6c160ad3-6b6f-43f5-9e97-5b5d962a8d1a
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
topic-tags: 3D
discoiquuid: 0d7fefc0-6923-4ac3-9e90-335c08fa56f0
translation-type: tm+mt
source-git-commit: b698a1348df3ec2ab455c236422784d10cbcf7c2
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 8%

---


# Integration von AEM 3D mit Autodesk 3ds Max {#integrating-aem-d-with-autodesk-ds-max}

>[!NOTE]
>
>Diese Aufgabe ist optional und nur unter Windows verfügbar.

Sie können optional AEM 3D mit der Autodesk 3ds Max Software integrieren, um die Unterstützung für native 3ds Max-Dateien (.MAX) zu aktivieren. Das Rendering mittels 3ds Max wird derzeit nicht unterstützt.

See [Advanced configuration settings](advanced-config-3d.md).

Siehe auch [Integration von AEM 3D mit AutoDesk Maya](integrate-maya-with-3d.md).

**So integrieren Sie AEM 3D mit Autodesk 3ds Max**:

1. Installieren Sie die Autodesk 3ds Max-Software auf denselben Servern, auf denen AEM Author-Knoten installiert sind.

   Vergewissern Sie sich nach der Installation, dass Sie Maya öffnen sowie verwenden können und keine Lizenzprobleme auftreten.

   >[!NOTE]
   >
   >Um Probleme mit verweigertem Zugriff zu vermeiden, installieren Sie 3ds Max mit demselben Admin-Benutzerkonto wie AEM.

1. Klicken Sie in 3ds Max auf **[!UICONTROL Anpassen > Plug-in-Manager]**.

   Suchen Sie `FBXMAX.DLU` und überprüfen Sie, ob der **[!UICONTROL Status]** **[!UICONTROL geladen]** ist.

   Schließen Sie die **[!UICONTROL Dialogfelder &quot;Plug-In Manager]** &quot;und &quot;3ds Max&quot;.

1. Aktualisieren Sie das Konvertierungsskript.

   AEM verwendet ein Befehlszeilenskript, um das Befehlszeilendienstprogramm 3ds Max aufzurufen `3dsmaxcmd.exe`. Sie müssen dieses Skript bearbeiten, wenn Sie eine andere Version als 3ds Max 2016 installiert haben, oder wenn Sie 3ds Max an einem nicht standardmäßigen Speicherort installiert haben oder wenn Sie AEM auf einer anderen Partition oder einem anderen Laufwerk installiert haben.

   1. Öffnen Sie die CRXDE Lite und navigieren Sie zu `/libs/settings/dam/v3D/scripts/max`.
   1. Klicken Sie mit der Dublette `export-fbx.bat` , um es zu öffnen.
   1. Bearbeiten Sie die erste Zeile des Skripts nach Bedarf, um den Speicherort des `3dsmaxcmd.exe` Dienstprogramms anzuzeigen. Wenn beispielsweise 3ds Max 2017 verwendet wird und AEM auf einem anderen Festplattenlaufwerk installiert ist:

   ![image2018-6-22_13-35-8](assets/image2018-6-22_13-35-8.png)

1. Near the upper-left corner of the CRXDE Lite page, tap **[!UICONTROL Save All]**.

   Near the upper-left corner of the CRXDE Lite page, tap **[!UICONTROL Save All]**.

1. Entfernen Sie den Arbeitsordner (nur erforderlich, wenn zuvor versucht wurde, eine .MAX-Datei zu erfassen).

   1. Navigieren Sie in CRXDE Lite zu `/libs/settings/dam/v3D/Paths/maxWorkPath`. Der Standardwert dieser Einstellung ist `./MaxWork`relativ zum AEM Installationsstammordner.
   1. Melden Sie sich beim Server selbst an und verwenden Sie den DateiExplorer, um zum AEM Installationsstammordner zu navigieren.
   1. Löschen Sie den **[!UICONTROL Ordner &quot;MaxWork]** &quot;einschließlich des gesamten Inhalts, falls vorhanden.

      Der Ordner wird automatisch neu erstellt, wenn eine .MAX-Datei das nächste Mal aufgenommen wird.

1. Aktivieren Sie &quot;3ds Max&quot;für die Erfassung, indem Sie folgende Schritte ausführen:

   1. Navigieren Sie in der CRXDE Lite zu `/libs/settings/dam/v3D/assetTypes/max` und setzen Sie die **[!UICONTROL Enabled]** -Eigenschaft auf true:

   ![image2018-6-22_13-50-50](assets/image2018-6-22_13-50-50.png)

1. Near the upper-left corner of the CRXDE Lite page, tap **[!UICONTROL Save All]**.

## Testing the integration of AEM 3D with Autodesk 3ds Max {#testing-the-integration-of-aem-d-with-autodesk-ds-max}

1. Open AEM Assets, then upload the `.max` file located in `sample-3D-content/models` to the **[!UICONTROL test3d]** folder.

   Beachten Sie, dass sample-3D-content.zip zuvor zum Überprüfen der grundlegenden 3D-Funktionen heruntergeladen wurde.

1. Return to the **[!UICONTROL Card]** view and observe the message banners shown on the uploaded assets.

   Das Banner Konvertierungsformat wird angezeigt, während 3ds Max das native Format 3ds Max in .FBX konvertiert.

1. Nach Abschluss der Verarbeitung öffnen Sie `logo-sphere.max` die **[!UICONTROL Detail]** -Ansicht.

   Das Erlebnis der Vorschau ist dasselbe wie bei `logo_sphere.fbx`.

