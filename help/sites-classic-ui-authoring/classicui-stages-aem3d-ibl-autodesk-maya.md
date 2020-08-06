---
title: Einrichten einer IBL-Bühne mit Autodesk Maya und Mental Ray
seo-title: Einrichten einer IBL-Bühne mit Autodesk Maya und Mental Ray
description: Erfahren Sie, wie Sie mit Autodesk Maya und Mental Ray eine IBL-Bühne einrichten.
seo-description: Erfahren Sie, wie Sie mit Autodesk Maya und Mental Ray eine IBL-Bühne einrichten.
uuid: 99878112-74c1-4a52-a7c2-c39927ce0e2a
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 00f7ed25-276b-42c2-ae4c-11de357a9ec6
translation-type: tm+mt
source-git-commit: e0ce860380a28a9dcaa6f8ce94ad278cdbe49fad
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 85%

---


# Einrichten einer IBL-Bühne mit Autodesk Maya und Mental Ray{#setting-up-an-ibl-stage-with-autodesk-maya-and-mental-ray}

1. Erstellen Sie in Maya eine neue, leere Szene.

1. Erstellen Sie eine (vorübergehende) Referenz auf ein repräsentatives Modell. Auf diese Weise können Sie die Beleuchtung einfacher ermitteln, Kameras einrichten und den Renderer konfigurieren.
1. Richten Sie eine bildbasierte Beleuchtung ein.

   1. Wählen Sie in den Rendereinstellungen die Option **[!UICONTROL Render Using: mental ray]** und öffnen Sie die Registerkarte „Scene“.****
   1. Open the **[!UICONTROL Environment]** accordion, then click **[!UICONTROL Create Image Based Lighting]**.
   1. Klicken Sie auf das Feldsymbol mit dem rechten Pfeil auf der linken Seite des Feldes und wählen Sie den IBL-Knoten `mentalRayIblShape1`[!UICONTROL . Beenden Sie dann die Rendereinstellungen].
   1. In the **[!UICONTROL Attribute Editor]**, select the transform node `mentalRayIbl1`, then rename the transform node to `AdobeIbl`.

   1. Set the [!UICONTROL Scale] of the node to make the environment sphere significantly larger than the largest 3D object to be shown with this stage (for example, `10000,10000,10000`).
   1. Wählen Sie den Knoten `AdobeIblShape` aus und konfigurieren Sie ihn wie folgt:

      * **[!UICONTROL Mapping]** – Spherical
      * **[!UICONTROL Type]** – Image File
      * **[!UICONTROL Emit Light]** – true
   1. Hängen Sie das gewünschte 32-Bit-TIFF-Bild an den Knoten `AdobeIbl` an.


1. Richten Sie die Ausgangsebene ein.

   * Erstellen Sie eine geeignete Ebene, die als neue Ausgangsebene verwendet werden soll. Passen Sie die Größe der Ebene so an, dass sie in den IBL-Bereich passt und durch den Koordinatenursprung verläuft.
   * Hängen Sie ein Material für **[!UICONTROL Hintergrund verwenden]** an die Bodenfläche an, nennen Sie dieses `AdobeUseBackground` und hängen Sie es an das Bodenflächenobjekt an.

1. (Optional) Erstellen und konfigurieren Sie Kameras.

   Die Kamera muss zur Mitte der Szene hin gerichtet sein, wo das Asset eingefügt wird. Die Kamera muss auf „renderbar“ eingestellt sein.

1. Richten Sie das Rendern mit Mental Ray ein.

   Configure the [!UICONTROL Render Settings] with the following suggestions.

   * **[!UICONTROL Häufige]** Registerkarte

      Deselect the **[!UICONTROL Alpha channel (mask)]** check box for all Renderable Cameras.

   * **[!UICONTROL Registerkarte „Quality“]**

      * **[!UICONTROL Overall quality]** – `0.5` oder weniger
      * **[!UICONTROL Indirekter Diffuse-Modus]** - `Final Gather`
      * **[!UICONTROL Filtergröße]** - `2.0`, `2.0`
   * Rendern Sie die Szene mit den typischen Bildgrößen, die Sie gewohnt sind. Verfeinern Sie gegebenenfalls die Licht- und/oder Rendereinstellung, um die gewünschten Ergebnisse zu erzielen.

      Beachten Sie, dass das Rendern mit Mental Ray und bildbasierter Beleuchtung sehr langsam und rechenintensiv ist. Adobe empfiehlt die Einrichtung der niedrigsten Qualitätseinstellungen, mit denen noch die gewünschte Renderqualität erzielt werden kann.


1. Entfernen Sie die Referenz, die Sie in Schritt 2 erstellt haben.

1. Speichern Sie die Szene und beenden Sie Autodesk Maya.

1. Laden Sie die Szene und das IBL-PTIFF-Bild in AEM hoch und warten Sie, bis der Ladevorgang abgeschlossen ist.

   Siehe [Hochladen von Assets](/help/assets/managing-assets-touch-ui.md#uploading-assets).

1. Lösen Sie eventuelle Dateiabhängigkeiten auf.

   Siehe [Auflösen von Dateiabhängigkeiten](/help/sites-classic-ui-authoring/classicui-upload-proc-3d-resolve-dependencies.md).

   Es kann vorkommen, dass AEM 3D das in der Bühne konfigurierte IBL-Bild nicht erkennen kann. In solchen Fällen müssen Sie die fehlenden Abhängigkeiten manuell auflösen. Sie können dasselbe zuvor hochgeladene IBL-PTIFF-Bild jeder der fehlenden Abhängigkeiten zuordnen. Alternativ können Sie verschiedene Bilder zuweisen, um die IBL-Effekte weiter zu steuern. Tippen Sie nach dem Auflösen der Abhängigkeiten auf **Speichern**, um die Neuverarbeitung einzuleiten. 

1. Öffnen Sie die Asset-Eigenschaften in AEM. Stellen Sie den Titel auf eine geeignete Zeichenfolge ein. Er wird in der Dropdown-Liste für die Auswahl der Bühne angezeigt. Prüfen Sie, ob **[!UICONTROL Klasse]** auf **[!UICONTROL 3D-Bühne]** eingestellt ist. Speichern und beenden Sie.

1. Öffnen Sie ein 3D-Asset, wählen Sie eine neue Bühnendatei und prüfen Sie, ob sie wie erwartet in der Vorschau angezeigt und gerendert wird.

