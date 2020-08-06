---
title: Anzeigen von 3D-Assets
seo-title: Anzeigen von 3D-Assets
description: In diesem Abschnitt erhalten Sie Informationen zum interaktiven 3D-Viewer, der in AEM auf der Seite „Asset-Details“ verfügbar ist. Sie lernen, wie 3D-Assets im Viewer angezeigt werden.
seo-description: In diesem Abschnitt erhalten Sie Informationen zum interaktiven 3D-Viewer, der in AEM auf der Seite „Asset-Details“ verfügbar ist. Sie lernen, wie 3D-Assets im Viewer angezeigt werden.
uuid: 7d8133ac-3110-4979-8e19-e65090e791be
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 65040923-a8a8-4e27-82c0-67a04348e238
translation-type: tm+mt
source-git-commit: 5acb16b1734331767554261bbcf9640947f2e23f
workflow-type: tm+mt
source-wordcount: '1755'
ht-degree: 65%

---


# Anzeigen von 3D-Assets {#viewing-d-assets}

In diesem Dokument wird beschrieben, wie Sie 3D-Assets in den Asset-Details anzeigen können. Außerdem wird beschrieben, wie Sie Assets anzeigen können, die sich in der 3D-Komponente in Sites befinden.

## Anzeigen von 3D-Assets in der Asset-Detailseite {#viewing-d-assets-in-the-asset-details-page}

Der interaktive 3D-Viewer ist auf der Seite „Asset-Details“ in AEM verfügbar. Der Viewer bietet unter anderem eine Reihe interaktiver Kamera-Steuerelemente, mit denen Sie die Kamera um das 3D-Asset drehen sowie Zoom- und Schwenkvorgänge durchführen können.

![chlimage_1-139](assets/chlimage_1-139.png)

Neben den Standardbühnen können Sie in AEM 3D auch Bühnen verwenden, die in einer Drittanbieteranwendung erstellt und in AEM hochgeladen wurden.

Siehe [Informationen zu Bühnen in AEM 3D](about-the-use-of-stages-in-aem-3d.md).

>[!NOTE]
>
>Um ein 3D-Asset anzuzeigen, muss der Browser Ihres Geräts oder Desktops WebGL-fähig sein. Außerdem muss die zugrunde liegende Grafikhardware über ausreichend Kapazität und Speicherplatz verfügen, um Modelle der gewünschten Größe und Komplexität rendern zu können. Bestimmte Vorschaufunktionen, etwa Schlagschatten, sind nicht in allen Browsern umsetzbar.

### Leistungsaspekte bei der Anzeige von 3D-Assets {#performance-considerations-when-you-view-d-assets}

Wie schnell ein 3D-Asset auf der Seite „Asset-Details“ geöffnet wird, hängt u. a. von den folgenden Faktoren abhängt:

* Bandbreite und Latenz zum Server.
* Modellgröße (Anzahl der Flächen).
* Anzahl und Größe der Maps.
* Komplexität der Bühnendatei. Beispielsweise die Größe des IBL-Bildes.

Wenn Sie die Kamera interaktiv bearbeiten, muss darüber hinaus die Kapazität des Client-Computers – etwa Workstation, Notebook oder Mobilgerät mit Touch-Funktion – berücksichtigt werden. Ein relativ leistungsfähiges System mit guten Grafikfähigkeiten unterstützt eine weichere, angenehmere interaktive 3D-Anzeige.

**So zeigen Sie 3D-Assets an**:

1. Laden Sie 3D-Assets in AEM hoch.

   Siehe [Informationen zum Hochladen und Verarbeiten von 3D-Assets in AEM](upload-processing-3d-assets.md).

1. From AEM, on the **[!UICONTROL Navigation]** page, tap **[!UICONTROL Assets]**.
1. Tippen Sie oben rechts auf der Seite in der Dropdown-Liste **[!UICONTROL Ansicht]** auf **[!UICONTROL Kartenansicht]**.
1. Navigieren Sie zu einem 3D-Asset, das Sie anzeigen möchten.
1. Tippen Sie auf die Karte des 3D-Assets, um das Asset auf der Seite „Asset-Details“ zu öffnen.
1. Führen Sie einen der folgenden Schritte aus:

   * Testen Sie mit der Palette der Kamerasteuerung in der rechten unteren Ecke der Seite „Asset-Details“ verschiedene Ansichten des Assets.

      Der Zoomfaktor und die Perspektive eines 3D-Assets lassen sich auch auf Eingabegeräten ohne Touchfunktion oder Mausrad ändern, beispielsweise mit der klassischen Apple-Maustaste. You accomplish the action by pressing and holding down the `SHIFT`key while depressing the mouse button and dragging up or down.

      Wenn Sie ein Touchpad auf einem typischen Notebook verwenden, lässt sich das Zoom- oder Perspektiveverhalten mit zwei Fingern häufig schwer steuern. In such cases, you can press and hold down `SHIFT`during the action. Dadurch wird die Geschwindigkeit der Pinch-Geste reduziert und es ist einfacher, den exakten Zoomfaktor oder die exakte Perspektive einzustellen. Alternately, you can use a one finger drag up or down while the `SHIFT`key is pressed to affect zoom or perspective behaviors.
   <table> 
    <tbody> 
      <tr> 
      <td><strong>Name der Camera Control</strong><br /> </td> 
      <td><strong>Beschreibung</strong></td> 
      </tr> 
      <tr> 
      <td><p>Zoom</p> <p> oder</p> <p>Persp</p> </td> 
      <td><p>Tippen oder klicken Sie auf , um zwischen den Modi "Zoom"und "Perspektive"zu wechseln.</p> <p>Oder halten Sie die <code>ALT/OPTION</code> Taste während der Aktion gedrückt, um vorübergehend in den Perspektivmodus<br /> zu wechseln. Lassen Sie die Taste los, um in den Zoom-Modus zurückzukehren.</p> 
      <ul> 
      <li><strong>Zoom</strong>-Dolly-Ein- und Auszoomen-Verhalten, das die Kamera näher oder weiter weg von dem Asset<br /> bewegt, das Sie sehen. Zoom ist das Standardverhalten für das Mausrad (falls verfügbar), für Pinch-Gesten mit zwei Fingern auf Mobilgeräten oder dann, wenn Sie bei gedrückter Umschalttaste mit der linken Maustaste nach oben oder unten ziehen.</li> 
      <li><strong>Perspektive</strong>-Ändert die Brennweite (auch als "Ansicht-Feld"bezeichnet) der Kamera, wobei die relative Größe des Assets in der Ansicht beibehalten wird. Perspektive ist ein alternatives Verhalten für das Mausrad (falls verfügbar), für Pinch-Gesten mit zwei Fingern auf Mobilgeräten oder dann, wenn Sie bei gedrückter Umschalttaste mit der linken Maustaste nach oben oder unten ziehen.</li> 
      </ul> </td> 
      </tr> 
      <tr> 
      <td><p>Orbit</p> <p> oder</p> <p>Schwenken</p> </td> 
      <td><p>Tippen oder klicken Sie auf , um zwischen dem Umlaufmodus und dem Schwenken zu wechseln.</p> <p>Oder halten Sie während der Aktion die <code>ALT/OPTION</code> Taste gedrückt, um vorübergehend in den Schwenk-Modus zu wechseln. Lassen Sie die Taste los, um in den Orbit-Modus zurückzukehren.</p> 
      <ul> 
      <li><strong>Orbit</strong>: Verschiebt die Betrachtungskamera auf eine Kugel, die auf einem Punkt der Zielgruppe zentriert ist, der sich in der Mitte des 3D-Assets befindet, ist standardmäßig eingestellt. Orbit ist das Standardverhalten beim Ziehen mit der linken Maustaste oder dem Ziehen mit Touch auf Mobilgeräten.</li> 
      <li><strong>Schwenken</strong>-Verschiebt die Kamera in der Betrachtungsebene. Der Zielpunkt wird entsprechend verschoben, sodass die Kamera in nachfolgenden Orbit-Vorgängen um einen neuen Zielpunkt bewegt wird. Schwenken ist ein alternatives Verhalten für das Ziehen mit der linken Maustaste und das Ziehen mit einem Touch.</li> 
      </ul> </td> 
      </tr> 
      <tr> 
      <td><p>Untersuchen</p> <p> oder</p> <p>Target</p> </td> 
      <td><p>Tippen oder klicken Sie auf , um zwischen dem Prüfungs- und dem Zielgruppe-Modus zu wechseln.</p> 
      <ul> 
      <li><strong>Überprüfen Sie</strong>, ob Sie auf tippen oder klicken, um in den Zielgruppe-Modus zu wechseln.</li> 
      <li><strong>Zielgruppe</strong>-Tippen oder klicken Sie auf einen Punkt an einer beliebigen Stelle des 3D-Assets, um die Ansicht auf diesem Teil des Assets zu zentrieren.<br /> Der neue Zielpunkt wird für Drehungsaktionen verwendet.</li> 
      </ul> </td> 
      </tr> 
      <tr> 
      <td>Zurücksetzen</td> 
      <td>Tippen oder klicken Sie auf , um die Zielgruppe der Ansicht in der Mitte des Modells wiederherzustellen. Reset also moves the camera<br /> closer or further away to show the asset in its entirety and at a reasonable viewing size.</td> 
      </tr> 
    </tbody> 
    </table>

   * Near the upper-right corner of the asset details page, tap the **[!UICONTROL Stage Selector]** icon. Wählen Sie eine Bühne mit dem Hintergrund und der Beleuchtung, die Sie auf das 3D-Asset anwenden möchten.

   ![chlimage_1-140](assets/chlimage_1-140.png)

   Die Stufen liefern den Hintergrund, die Grundebene und die Beleuchtung, in der das 3D-Umgebung angezeigt wird.

   Siehe [Informationen zu Bühnen in AEM 3D](about-the-use-of-stages-in-aem-3d.md).

   * Near the upper-right corner of the asset details page, tap the **[!UICONTROL Camera Selector]** icon, then select a camera view that you want to apply to the 3D asset.

   ![chlimage_1-141](assets/chlimage_1-141.png)

   In Bühnen werden häufig vordefinierte Kameras bereitgestellt. Sie können die aktuelle Kamera erneut auswählen, um die vordefinierten Einstellungen wiederherzustellen.

   Siehe [Informationen zu Bühnen in AEM 3D](about-the-use-of-stages-in-aem-3d.md).

1. Tippen Sie oben rechts auf der Seite auf **[!UICONTROL Speichern]**.
1. Führen Sie einen der folgenden Schritte aus:

   * Rendern Sie das 3D-Asset.

      Weitere Informationen finden Sie unter [Rendern von 3D-Assets](rendering-3d-assets.md).

   * Tippen Sie in der linken oberen Ecke der Seite auf **[!UICONTROL Schließen]**, um zur Seite „Assets“ zurückzukehren.

## Anzeigen von 3D-Assets in der Sites-3D-Komponente {#viewing-d-assets-in-the-sites-d-component}

>[!NOTE]
>
>Dieser Abschnitt gilt nur für den klassischen WebGL-Viewer, der für andere 3D-Asset-Typen als Adobe Dimension verwendet wird.

Abhängig vom Gerätetyp gibt es verschiedene Möglichkeiten, auf die 3D-Komponentenfunktionen zuzugreifen.

Weitere Informationen finden Sie in den folgenden Themen:

* [Touchscreen-Geräte](#touchscreen-devices)
* [Touchpad-Geräte](#touchpad-devices)
* [Maus- und Trackball-Geräte](#mouse-and-trackball-devices)

Siehe auch [Anzeigen einer Vorschau für eine Webseite mit einer 3D-Komponente](using-the-3d-sites-component.md#previewing-a-web-page-that-has-a-d-component).

![screen_shot_2017-12-11at145654](assets/screen_shot_2017-12-11at145654.png)

### Touchscreen-Geräte {#touchscreen-devices}

So arbeiten Sie auf Touchscreen-Geräten mit 3D-Komponenten:

1. Ziehen Sie mit einem Finger oder wischen Sie, um den Blickwinkel („Kamera“) um das Objekt herumzuschwenken („drehen“). Sie können das Objekt aus einer beliebigen Richtung anzeigen.

1. Führen Sie mit zwei Fingern eine Pinch-Geste aus, um die Kamera näher an das Objekt oder weiter weg zu bewegen. Diese Aktion ähnelt dem Zoom und bietet Ihnen die Möglichkeit, Details des Objekts zu betrachten. Alternativ können Sie die Symbole „+“ bzw. „-“ drücken und halten, um die Kamera auf das Objekt zu- oder davon wegzubewegen.

1. Ziehen Sie mit zwei Fingern, um einen Bildschwenk mit der Kamera auszuführen. Mit dieser Aktion wird die Kamera seitlich versetzt, sodass Sie sich im eingezoomten Modus verschiedene Teile des Objekts ansehen können. Alternatively, tap the **[!UICONTROL Orbit/Pan Toggle]** button to toggle to Pan mode, then use a one-finger drag to pan the camera. Tap the **[!UICONTROL Orbit/Pan Toggle]** button to revert to **[!UICONTROL Orbit]** mode.

1. Tippen Sie auf **[!UICONTROL Viewer zurücksetzen]**, um die Kamera zurückzusetzen. Mit dieser Aktion wird das Objekt erneut in der Vollansicht angezeigt und die automatische Drehung fortgesetzt, sofern sie aktiviert ist.

1. Tippen Sie auf **[!UICONTROL Vollbild]**, um in den Vollbildmodus zu wechseln (sofern vom Gerät unterstützt). Tippen Sie erneut auf **[!UICONTROL Vollbild]**, um mit dem 3D-Viewer in den Seiteneinbettungsmodus zurückzukehren.

### Touchpad-Geräte {#touchpad-devices}

So arbeiten Sie auf Touchpad-Geräten mit 3D-Komponenten:

1. Ziehen Sie mit einem Finger, während Sie die Touchpad-Taste (links) gedrückt halten, um den Blickwinkel („Kamera“) um das Objekt zu schwenken („drehen“) Sie können das Objekt aus einer beliebigen Richtung anzeigen.

1. Ziehen Sie mit zwei Fingern nach unten bzw. nach oben (Touchpad-Tasten oben), um die Kamera auf das Objekt zu- bzw. davon wegzubewegen. Diese Aktion ähnelt dem Zoom und ermöglicht es Ihnen, Details des Objekts zu betrachten. Alternatively, click and hold the **[!UICONTROL Zoom In]** or **[!UICONTROL Zoom Out]** buttons to move the camera closer or farther away from the object.

1. Use a one-finger drag while holding the **ALT/option** key and the (left) touchpad button to pan the camera. Mit dieser Aktion wird die Kamera seitlich versetzt, sodass Sie sich im eingezoomten Modus verschiedene Teile des Objekts ansehen können. Alternatively, click the **[!UICONTROL Orbit/Pan Toggle]** button to toggle to **[!UICONTROL Pan]** mode, then use a one-finger drag while holding the (left) button to pan the camera. Click the **[!UICONTROL Orbit/Pan Toggle]** button again to revert to **[!UICONTROL Orbit]** mode.

1. Click **[!UICONTROL Reset Viewer]** to reset the camera. Mit dieser Aktion wird das Objekt erneut in der Vollansicht angezeigt und die automatische Drehung fortgesetzt, sofern sie aktiviert ist.

1. Click **[!UICONTROL Full Screen]** to enter full-screen mode. Use the **Escape** key on your keyboard or click **[!UICONTROL Full Screen]** again to restore the 3D viewer to page-embedded mode.

### Maus- und Trackball-Geräte {#mouse-and-trackball-devices}

So arbeiten Sie auf Maus- und Trackball-Geräten mit 3D-Komponenten:

1. Ziehen Sie mit einem Finger, während Sie die linke Maustaste gedrückt halten, um den Blickwinkel („Kamera“) um das Objekt zu schwenken („drehen“). Sie können das Objekt aus einer beliebigen Richtung anzeigen.

1. Nutzen Sie das Mausrad, um die Kamera näher an das Objekt oder weiter weg zu bewegen. Dies ähnelt dem Zoom und bietet Ihnen die Möglichkeit, Details des Objekts zu betrachten. Alternatively, click and hold the **[!UICONTROL Zoom In]** or **[!UICONTROL Zoom Out]** buttons to move the camera closer or farther away from the object.

1. Drag while holding the **ALT/option** key and the left mouse button to pan the camera. Dadurch wird die Kamera seitlich versetzt und ermöglicht es Ihnen, sich im eingezoomten Modus verschiedene Teile des Objekts anzusehen. Alternatively, click the **[!UICONTROL Orbit/Pan Toggle]** button to toggle to **[!UICONTROL Pan]** mode, then drag while holding the left mouse button to pan the camera. Click the **[!UICONTROL Orbit/Pan Toggle]** again to revert to **[!UICONTROL Orbit]** mode.
1. Click **[!UICONTROL Reset Viewer]** to reset the camera. Mit dieser Aktion wird das Objekt erneut in der Vollansicht angezeigt und die automatische Drehung fortgesetzt, sofern sie aktiviert ist.
1. Click **[!UICONTROL Full Screen]** to enter full-screen mode. Use the **[!UICONTROL Escape]** key on your keyboard or click **[!UICONTROL Full Screen]** again to restore the 3D viewer to page-embedded mode.

