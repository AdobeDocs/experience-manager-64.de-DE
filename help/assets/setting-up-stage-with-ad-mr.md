---
title: Einrichten einer Standardbühne mit Autodesk Maya und Mental Ray
seo-title: Einrichten einer Standardbühne mit Autodesk Maya und Mental Ray
description: Anleitung zur Einrichtung einer Standardbühne mit Autodesk Maya und Mental Ray
seo-description: Anleitung zur Einrichtung einer Standardbühne mit Autodesk Maya und Mental Ray
uuid: 3895fda6-29ae-46f5-b2bc-abc989808648
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: da8fc33b-84ae-4ead-87bb-5a7870a38b1f
translation-type: tm+mt
source-git-commit: 4b05b24a91ba9c31a19a5a96fb481d2ffc4c9bfc
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 91%

---


# Einrichten einer Standardbühne mit Autodesk Maya und Mental Ray {#setting-up-a-standard-stage-with-autodesk-maya-and-mental-ray}

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

   Konfigurieren Sie die Rendereinstellungen. Orientieren Sie sich dabei an den folgenden Vorschlägen:

   * **** Commontab

      Deaktivieren Sie das Kontrollkästchen **[!UICONTROL Alpha-Kanal (maske)]** für alle renderbaren Kameras.

   * **[!UICONTROL Registerkarte „Quality“]**

      * **[!UICONTROL Allgemeine]** `- 0.5` Qualität oder weniger
      * **[!UICONTROL Indirekter Diffuse-Modus]**  -  `Final Gather`
      * **[!UICONTROL Filtergröße]** -  `2.0`,  `2.0`
   * Rendern Sie die Szene mit den typischen Bildgrößen, die Sie gewohnt sind. Verfeinern Sie gegebenenfalls die Licht- und/oder Rendereinstellung, um die gewünschten Ergebnisse zu erzielen.

      Beachten Sie, dass das Rendern mit Mental Ray und bildbasierter Beleuchtung sehr langsam und rechenintensiv ist. Adobe empfiehlt die Einrichtung der niedrigsten Qualitätseinstellungen, mit denen noch die gewünschte Renderqualität erzielt werden kann.


1. Entfernen Sie die Referenz, die Sie in Schritt 2 erstellt haben.

1. Speichern Sie die Szene und beenden Sie Autodesk Maya.
1. Laden Sie die Szene in AEM hoch und warten Sie, bis der Ladevorgang abgeschlossen ist.

   Informationen hierzu finden Sie unter [Hochladen von Assets](managing-assets-touch-ui.md#uploading-assets).

   Wenn Autodesk® Maya® nicht auf dem AEM-Server konfiguriert ist, exportieren Sie eine FBX von Maya und laden Sie sie in AEM hoch.

1. Öffnen Sie die Asset-Eigenschaften in AEM. Stellen Sie **[!UICONTROL title]** auf eine geeignete Zeichenfolge ein, die in der Dropdown-Liste **[!UICONTROL Stage Selector]** angezeigt wird. Prüfen Sie, ob **[!UICONTROL Klasse]** auf **[!UICONTROL 3D-Bühne]** eingestellt ist. Speichern und beenden Sie.
1. Öffnen Sie ein 3D-Asset, wählen Sie eine neue Bühnendatei und prüfen Sie, ob sie wie erwartet in der Vorschau angezeigt und gerendert wird.

