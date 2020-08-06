---
title: Einrichten einer IBL-Bühne mit Autodesk Maya und Mental Ray
seo-title: Einrichten einer IBL-Bühne mit Autodesk Maya und Mental Ray
description: Anleitungen zur Einrichtung einer IBL-Bühne mit Autodesk Maya und Mental Ray
seo-description: Anleitungen zur Einrichtung einer IBL-Bühne mit Autodesk Maya und Mental Ray
uuid: 353ff561-0d30-4d62-8cad-68890c883c92
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 752e521f-198f-425a-abfa-051993f9c694
translation-type: tm+mt
source-git-commit: 4b05b24a91ba9c31a19a5a96fb481d2ffc4c9bfc
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 80%

---


# Einrichten einer IBL-Bühne mit Autodesk Maya und Mental Ray {#setting-up-an-ibl-stage-with-autodesk-maya-and-mental-ray}

1. Erstellen Sie in Maya eine neue, leere Szene.

1. Erstellen Sie eine (vorübergehende) Referenz auf ein repräsentatives Modell. Auf diese Weise können Sie die Beleuchtung einfacher ermitteln, Kameras einrichten und den Renderer konfigurieren.
1. Richten Sie eine bildbasierte Beleuchtung ein.

   1. In **[!UICONTROL Render Settings]**, select **[!UICONTROL Render Render Using: mental ray]**, and open the Scene tab.
   1. Open the **[!UICONTROL Render Environment]** accordion and click **[!UICONTROL Render Create Image Based Lighting**.
   1. Click the box icon that has a right arrow on the left side of the box to select the IBL node `mentalRayIblShape1`, then exit **[!UICONTROL Render Settings]**.
   1. In the **[!UICONTROL Attribute Editor]**, select the transform node `mentalRayIbl1`, then rename the transform node to `AdobeIbl`.
   1. Legen Sie die Skalierung des Knotens fest. Machen Sie dabei den Umgebungsbereich erheblich größer als das größte 3D-Objekt, das mit dieser Bühne gezeigt werden soll (z. B. `10000,10000,10000`).
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

   Configure the **[!UICONTROL Render Settings]** with the following suggestions.

   * **[!UICONTROL Häufige]** Registerkarte

      Deselect the **[!UICONTROL Alpha channel (mask)]** check box for all **[!UICONTROL Renderable Cameras]**.

   * **[!UICONTROL Registerkarte „Quality“]**

      * **Overall quality** – `0.5` oder weniger
      * **Indirekter Diffuse-Modus** - `Final Gather`
      * ``**Filter Size** - `2.0`, `2.0`
   * Rendern Sie die Szene mit den typischen Bildgrößen, die Sie gewohnt sind. Verfeinern Sie gegebenenfalls die Licht- und/oder Rendereinstellung, um die gewünschten Ergebnisse zu erzielen.

      Beachten Sie, dass das Rendern mit Mental Ray und bildbasierter Beleuchtung sehr langsam und rechenintensiv ist. Adobe empfiehlt die Einrichtung der niedrigsten Qualitätseinstellungen, mit denen noch die gewünschte Renderqualität erzielt werden kann.


1. Entfernen Sie die Referenz, die Sie in Schritt 2 erstellt haben.

1. Speichern Sie die Szene und beenden Sie Autodesk Maya.

1. Laden Sie die Szene und das IBL-PTIFF-Bild in AEM hoch und warten Sie, bis der Ladevorgang abgeschlossen ist.

   Siehe [Hochladen von Assets](managing-assets-touch-ui.md#uploading-assets).

1. Lösen Sie eventuelle Dateiabhängigkeiten auf.

   Siehe [Auflösen von Dateiabhängigkeiten](resolve-file-dependencies.md).

   Es kann vorkommen, dass AEM 3D das in der Bühne konfigurierte IBL-Bild nicht erkennen kann. In solchen Fällen müssen Sie die fehlenden Abhängigkeiten manuell auflösen. Sie können dasselbe zuvor hochgeladene IBL-PTIFF-Bild jeder der fehlenden Abhängigkeiten zuordnen. Alternativ können Sie verschiedene Bilder zuweisen, um die IBL-Effekte weiter zu steuern. Tippen Sie nach dem Auflösen der Abhängigkeiten auf **[!UICONTROL Speichern]**, um die Neuverarbeitung einzuleiten. 

1. Öffnen Sie die Asset-Eigenschaften in AEM. Set **[!UICONTROL Title]** to a suitable string that will appear in the **[!UICONTROL Stage Selector]** drop-down list. Prüfen Sie, ob **[!UICONTROL Klasse]** auf **[!UICONTROL 3D-Bühne]** eingestellt ist. Speichern und beenden Sie.

1. Öffnen Sie ein 3D-Asset, wählen Sie eine neue Bühnendatei und prüfen Sie, ob sie wie erwartet in der Vorschau angezeigt und gerendert wird.

