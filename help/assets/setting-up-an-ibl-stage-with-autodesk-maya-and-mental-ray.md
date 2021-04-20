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
exl-id: ecb489e2-fd6f-4163-9739-5d7ff497d305
feature: 3D Assets
role: Administrator,Business Practitioner
translation-type: tm+mt
source-git-commit: 13eb1d64677f6940332a2eeb4d3aba2915ac7bba
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 80%

---

# Einrichten einer IBL-Bühne mit Autodesk Maya und Mental Ray {#setting-up-an-ibl-stage-with-autodesk-maya-and-mental-ray}

1. Erstellen Sie in Maya eine neue, leere Szene.

1. Erstellen Sie eine (vorübergehende) Referenz auf ein repräsentatives Modell. Auf diese Weise können Sie die Beleuchtung einfacher ermitteln, Kameras einrichten und den Renderer konfigurieren.
1. Richten Sie eine bildbasierte Beleuchtung ein.

   1. Wählen Sie unter **[!UICONTROL Rendereinstellungen]** **[!UICONTROL Rendereinstellungen mit: &quot;mental ray]**&quot;und öffnen Sie die Registerkarte &quot;Scene&quot;.
   1. Öffnen Sie das Akkordeon **[!UICONTROL Render-Umgebung]** und klicken Sie auf **[!UICONTROL Render Create Image Based Lighting]**.
   1. Klicken Sie auf das Feldsymbol mit dem Pfeil nach rechts auf der linken Seite des Felds, um den IBL-Knoten `mentalRayIblShape1` auszuwählen, und verlassen Sie dann **[!UICONTROL Rendereinstellungen]**.
   1. Wählen Sie im **[!UICONTROL Attribut-Editor]** den Transformationsknoten `mentalRayIbl1` und benennen Sie dann den Transformationsknoten in `AdobeIbl` um.
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

   Konfigurieren Sie die **[!UICONTROL Rendereinstellungen]** mit den folgenden Vorschlägen.

   * **** Commontab

      Deaktivieren Sie das Kontrollkästchen **[!UICONTROL Alpha-Kanal (maske)]** für alle **[!UICONTROL Renderbare Kameras]**.

   * **[!UICONTROL Registerkarte „Quality“]**

      * **Overall quality** – `0.5` oder weniger
      * **Indirekter Diffuse-Modus**  -  `Final Gather`
      * **Filtergröße** -  `2.0`,  `2.0`
   * Rendern Sie die Szene mit den typischen Bildgrößen, die Sie gewohnt sind. Verfeinern Sie gegebenenfalls die Licht- und/oder Rendereinstellung, um die gewünschten Ergebnisse zu erzielen.

      Beachten Sie, dass das Rendern mit Mental Ray und bildbasierter Beleuchtung sehr langsam und rechenintensiv ist. Adobe empfiehlt die Einrichtung der niedrigsten Qualitätseinstellungen, mit denen noch die gewünschte Renderqualität erzielt werden kann.


1. Entfernen Sie die Referenz, die Sie in Schritt 2 erstellt haben.

1. Speichern Sie die Szene und beenden Sie Autodesk Maya.

1. Laden Sie die Szene und das IBL-PTIFF-Bild in AEM hoch und warten Sie, bis der Ladevorgang abgeschlossen ist.

   Informationen hierzu finden Sie unter [Hochladen von Assets](managing-assets-touch-ui.md#uploading-assets).

1. Lösen Sie eventuelle Dateiabhängigkeiten auf.

   Siehe [Auflösen von Dateiabhängigkeiten](resolve-file-dependencies.md).

   Es kann vorkommen, dass AEM 3D das in der Bühne konfigurierte IBL-Bild nicht erkennen kann. In solchen Fällen müssen Sie die fehlenden Abhängigkeiten manuell auflösen. Sie können dasselbe zuvor hochgeladene IBL-PTIFF-Bild jeder der fehlenden Abhängigkeiten zuordnen. Alternativ können Sie verschiedene Bilder zuweisen, um die IBL-Effekte weiter zu steuern. Tippen Sie nach dem Auflösen der Abhängigkeiten auf **[!UICONTROL Speichern]**, um die Neuverarbeitung einzuleiten. 

1. Öffnen Sie die Asset-Eigenschaften in AEM. Stellen Sie **[!UICONTROL title]** auf eine geeignete Zeichenfolge ein, die in der Dropdown-Liste **[!UICONTROL Stage Selector]** angezeigt wird. Prüfen Sie, ob **[!UICONTROL Klasse]** auf **[!UICONTROL 3D-Bühne]** eingestellt ist. Speichern und beenden Sie.

1. Öffnen Sie ein 3D-Asset, wählen Sie eine neue Bühnendatei und prüfen Sie, ob sie wie erwartet in der Vorschau angezeigt und gerendert wird.
