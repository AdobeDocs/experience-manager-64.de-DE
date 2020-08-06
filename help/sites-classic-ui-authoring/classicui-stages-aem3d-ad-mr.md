---
title: Einrichten einer Standardbühne mit Autodesk Maya und Mental Ray
seo-title: Einrichten einer Standardbühne mit Autodesk Maya und Mental Ray
description: Lernen Sie, wie Sie eine Standardbühne mit Autodesk Maya und Mental Ray einrichten.
seo-description: Lernen Sie, wie Sie eine Standardbühne mit Autodesk Maya und Mental Ray einrichten.
uuid: 05c4858b-6261-4de3-a87a-03dd6bc519a4
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: f30c4039-3bbf-4d02-a9b5-bda6ccce16b9
translation-type: tm+mt
source-git-commit: e0ce860380a28a9dcaa6f8ce94ad278cdbe49fad
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 88%

---


# Einrichten einer Standardbühne mit Autodesk Maya und Mental Ray{#setting-up-a-standard-stage-with-autodesk-maya-and-mental-ray}

1. Erstellen Sie in Maya eine neue, leere Szene.
1. Erstellen Sie eine (vorübergehende) Referenz auf ein repräsentatives Modell. Auf diese Weise können Sie die Beleuchtung einfacher ermitteln, Kameras einrichten und den Renderer konfigurieren.

1. Fügen Sie Lichtquellen wie gewohnt hinzu. AEM 3D unterstützt derzeit die folgenden Lichtarten:

   * Gerichtete Beleuchtung
   * Spotlichter
   * Punktlichter 

   Andere Lichtarten werden ignoriert oder in eine der oben genannten unterstützten Lichtarten konvertiert, wenn die Bühnendatei in AEM 3D geladen wird. Die konvertierten Lichtarten werden beim Anzeigen des Assets und beim Rendern mit dem integrierten Renderer Rapid Refine verwendet. Die ursprünglichen Lichtarten werden beim Rendern mit Maya verwendet.

1. Erstellen Sie, falls erforderlich, eine neue Ausgangsebene und wenden Sie ein geeignetes Material an.

   Adobe empfiehlt die Einrichtung der Ausgangsebene als einseitig. Dadurch wird sichergestellt, dass Sie das Asset in AEM 3D von unten sehen können, ohne dass es durch die Ausgangsebene verdeckt wird.

1. (Optional) Erstellen und konfigurieren Sie Kameras.

   Die Kamera muss zur Mitte der Szene hin gerichtet sein, wo das Asset eingefügt wird. Die Kamera muss auf „renderbar“ eingestellt sein.

1. Richten Sie das Rendern mit Mental Ray ein.

   Configure the **[!UICONTROL Render Settings]** with the following suggestions:

   * **[!UICONTROL Häufige]** Registerkarte

      Deselect the **[!UICONTROL Alpha channel (mask)]** check box for all [!UICONTROL Renderable Cameras].

   * **[!UICONTROL Registerkarte „Quality“]**

      * **[!UICONTROL Gesamtqualität]** `- 0.5` oder weniger
      * **[!UICONTROL Indirekter Diffuse-Modus]** - `Final Gather`
      * **[!UICONTROL Filtergröße]** - `2.0`, `2.0`
   * Rendern Sie die Szene mit den typischen Bildgrößen, die Sie gewohnt sind. If necessary, refine the lights, or [!UICONTROL Render settings], or do both to achieve the results you want.

      Beachten Sie, dass das Rendern mit Mental Ray und bildbasierter Beleuchtung sehr langsam und rechenintensiv ist. Adobe empfiehlt die Einrichtung der niedrigsten Qualitätseinstellungen, mit denen noch die gewünschte Renderqualität erzielt werden kann.


1. Entfernen Sie die Referenz, die Sie in Schritt 2 erstellt haben.
1. Speichern Sie die Szene und beenden Sie Autodesk Maya.
1. Laden Sie die Szene in AEM hoch und warten Sie, bis der Ladevorgang abgeschlossen ist.

   Siehe [Hochladen von Assets](/help/assets/managing-assets-touch-ui.md#uploading-assets).

   Wenn Autodesk® Maya® nicht auf dem AEM-Server konfiguriert ist, exportieren Sie eine FBX von Maya und laden Sie sie in AEM hoch.

1. Öffnen Sie die Asset-Eigenschaften in AEM. Stellen Sie den Titel auf eine geeignete Zeichenfolge ein. Er wird in der Dropdown-Liste für die Auswahl der Bühne angezeigt. Prüfen Sie, ob **[!UICONTROL Klasse]** auf **[!UICONTROL 3D-Bühne]** eingestellt ist. Speichern und beenden Sie.
1. Öffnen Sie ein 3D-Asset, wählen Sie eine neue Bühnendatei und prüfen Sie, ob sie wie erwartet in der Vorschau angezeigt und gerendert wird.

