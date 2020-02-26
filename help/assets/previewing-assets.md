---
title: Anzeigen einer Vorschau von Dynamic Media-Assets
seo-title: Anzeigen einer Vorschau von Dynamic Media-Assets
description: Erfahren Sie, wie Sie eine Vorschau von Assets in dynamischen Medien anzeigen können
seo-description: Erfahren Sie, wie Sie eine Vorschau von Assets in dynamischen Medien anzeigen können
uuid: f0ff2fc4-a263-4dbe-ba46-b07077b49ae0
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 77296bff-8429-4240-af93-26076ae431ec
translation-type: tm+mt
source-git-commit: 8c6fdcea0def7720062edfc564c536f8d47e8402

---


# Anzeigen einer Vorschau von Dynamic Media-Assets {#previewing-assets}

You can use **[!UICONTROL Preview]** to see how a Dynamic Media digital asset looks when it is viewed by a customer in their own web browser. The default embedded, cross-device viewer that is assigned to the asset is used for the **[!UICONTROL Preview]**.

Ein Viewer ist eine Sammlung aus verschiedenen Einstellungen oder „Vorgaben“, wie die Viewer-Anzeigegröße, das Zoom-Verhalten, die Farbschemata, Rahmen, Schriftarten usw., die bestimmen, wie Rich-Media-Assets auf den Computerbildschirmen und Mobilgeräten der Benutzer angezeigt werden.

Neben der dedizierten Vorschaufunktion für Videos, Rotationssets und Bildsätze können Sie auch eine Vorschau eines Assets mit von Ihnen erstellten Viewer-Vorgaben anzeigen.Sie können auch Bildvorgaben verwenden, um eine Vorschau der Darstellungen von Bildern anzuzeigen.

* [Anwenden von Bildvorgaben](image-presets.md)
* [Anwenden von Viewer-Vorgaben](viewer-presets.md)

>[!NOTE]
>
>Wenn Sie sich auf einer Webseite (Sites) in AEM befinden, können Sie keine Asset-Vorschau im **[!UICONTROL Bearbeitungsmodus]** anzeigen. Sie müssen in den **[!UICONTROL Vorschaumodus]** wechseln, indem Sie in der oberen rechten Ecke auf **Vorschau** klicken.

**So zeigen Sie die Asset-Vorschau an**:

1. From **Adobe Experience Manager**, on the **[!UICONTROL Navigation]** page, tap **[!UICONTROL Asset]s **, then**[!UICONTROL Files ]**to access assets.
1. Near the upper-right corner of the page, from the **[!UICONTROL View]** drop-down list, tap **[!UICONTROL List View]**.
1. (Optional) Sortieren Sie in der Spalte **[!UICONTROL Typ]** die Assets nach dem Typ, den Sie in einer Vorschau anzeigen möchten.
1. Klicken Sie in der Spalte **[!UICONTROL Titel]** auf den Namen des Titels (nicht auf die Miniaturansicht) des Assets, das Sie in der Vorschau anzeigen möchten.
1. Führen Sie je nach ausgewähltem Asset eine der folgenden Aktionen aus:

<table> 
 <tbody>
  <tr>
   <td><strong>Asset-Typ, auf den Sie getippt haben</strong><br /> </td> 
   <td><strong>Asset-Vorschau in bestimmtem Ausgabeformat möglich?</strong></td> 
   <td><strong>Asset-Vorschau in bestimmtem Viewer möglich?</strong></td> 
  </tr>
  <tr>
   <td><p>Bild</p> </td> 
   <td>Ja</td> 
   <td>Ja</td> 
   <td><p><strong>Asset-Vorschau in bestimmtem Ausgabeformat</strong></p> 
    <ul> 
     <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdownliste angezeigt wird. Klicken Sie in der Liste auf <strong>Ausgabeformate</strong> und wählen Sie dann das Ausgabeformat, das Sie in einer Vorschau anzeigen möchten.</li> 
    </ul> <p><strong>Asset-Vorschau in bestimmtem Viewer</strong></p> 
    <ul> 
     <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdownliste angezeigt wird. Klicken Sie in der Liste auf <strong>Viewer</strong>. Wählen Sie dann einen Viewer aus, den Sie auf das Asset anwenden möchten.</li> 
    </ul> <p>Mit den Symbolen <strong>+</strong> und <strong>-</strong> können Sie den Zoom des gewählten Bildes erhöhen bzw. verkleinern. Klicken Sie auf <strong>Zurücksetzen</strong>, um den Originalzoom des Bildes wiederherzustellen.<br /> Mit einem Mobilgerät können Sie durch Doppeltippen auf das Bild in Schritten einzoomen. Wenn Sie den maximalen Zoom erreicht haben, doppeltippen Sie erneut auf das Bild, um den Zoomstatus zurückzusetzen. Streichen Sie mit dem Finger über das Bild, um es zu schwenken.</p> <p>To enable or disable viewer presets in the user interface, see <a href="/help/assets/managing-viewer-presets.md">Managing Viewer Presets</a>.<br /> </p> </td> 
  </tr>
  <tr>
   <td>Multimedia</td> 
   <td>Ja</td> 
   <td>Ja</td> 
   <td><p><strong>Asset-Vorschau in bestimmtem Ausgabeformat</strong></p> 
    <ul> 
     <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdownliste angezeigt wird. Klicken Sie in der Liste auf <strong>Ausgabeformate</strong> und wählen Sie dann das Ausgabeformat, das Sie in einer Vorschau anzeigen möchten.</li> 
    </ul> <p>Wenn Sie eine Videowiedergabe mit höherer Auflösung für die Vorschau auswählen, wird das Video möglicherweise abgeschnitten angezeigt. Das liegt daran, dass die Vorschau der Darstellung die exakte Auflösung zeigt, die Ihre Kunden sehen werden, und zwar im Kontext des eingebetteten Viewers, der für die Vorschau verwendet wird.</p> <p>Wenn Sie eine Vorschau eines adaptiven Videosets auf Asset-Ebene anzeigen, werden die Darstellungen in einem Wiedergabeerlebnis gruppiert. That is, the adaptive video is sized properly for viewing and played back using the best resolution in the context of your viewing device and connection speed.<br /> </p> <p><strong>Asset-Vorschau in bestimmtem Viewer</strong></p> 
    <ul> 
     <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdownliste angezeigt wird. Klicken Sie in der Liste auf <strong>Viewer</strong>. Wählen Sie dann einen Viewer aus, den Sie auf das Asset anwenden möchten.</li> 
    </ul> <p>To enable or disable viewer presets in the user interface, see <a href="/help/assets/managing-viewer-presets.md">Managing Viewer Presets</a>.</p> </td> 
  </tr>
  <tr>
   <td>Bildset</td> 
   <td>Nein</td> 
   <td>Ja</td> 
   <td><p><strong>Asset-Vorschau in bestimmtem Viewer</strong></p> 
    <ul> 
     <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdownliste angezeigt wird. Klicken Sie in der Liste auf <strong>Viewer</strong>. Wählen Sie dann einen Viewer aus, den Sie auf das Asset anwenden möchten.</li> 
    </ul> <p>Mit den Symbolen <strong>+</strong> und <strong>-</strong> können Sie den Zoom des gewählten Bildes erhöhen bzw. verkleinern. Klicken Sie auf <strong>Zurücksetzen</strong>, um den Originalzoom des Bildes wiederherzustellen.<br /> Mit einem Mobilgerät können Sie durch Doppeltippen auf das Bild in Schritten einzoomen. Wenn Sie den maximalen Zoom erreicht haben, doppeltippen Sie erneut auf das Bild, um den Zoomstatus zurückzusetzen. Streichen Sie mit dem Finger über das Bild, um es zu schwenken.</p> <p>To enable or disable viewer presets in the user interface, see <a href="/help/assets/managing-viewer-presets.md">Managing Viewer Presets</a>.</p> </td> 
  </tr>
  <tr>
   <td>Rotationsset</td> 
   <td>Nein</td> 
   <td>Ja</td> 
   <td><p><strong>Asset-Vorschau in bestimmtem Viewer</strong></p> 
    <ul> 
     <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdownliste angezeigt wird. Klicken Sie in der Liste auf <strong>Viewer</strong>. Wählen Sie dann einen Viewer aus, den Sie auf das Asset anwenden möchten.</li> 
    </ul> <p>Mit den Symbolen <strong>+</strong> und <strong>-</strong> können Sie den Zoom des gewählten Bildes erhöhen bzw. verkleinern. Klicken Sie auf <strong>Zurücksetzen</strong>, um den Originalzoom des Bildes wiederherzustellen.<br /> Mit einem Mobilgerät können Sie durch Doppeltippen auf das Bild in Schritten einzoomen. Wenn Sie den maximalen Zoom erreicht haben, doppeltippen Sie erneut auf das Bild, um den Zoomstatus zurückzusetzen. Streichen Sie mit dem Finger über das Bild, um es zu schwenken.</p> <p>To enable or disable viewer presets in the user interface, see <a href="/help/assets/managing-viewer-presets.md">Managing Viewer Presets</a>.</p> </td> 
  </tr>
  <tr>
   <td>Sets für gemischte Medien</td> 
   <td>Nein</td> 
   <td>Ja</td> 
   <td><p><strong>Asset-Vorschau in bestimmtem Viewer</strong></p> 
    <ul> 
     <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdownliste angezeigt wird. Klicken Sie in der Liste auf <strong>Viewer</strong>. Wählen Sie dann einen Viewer aus, den Sie auf das Asset anwenden möchten.</li> 
    </ul> <p>Mit den Symbolen <strong>+</strong> und <strong>-</strong> können Sie den Zoom des gewählten Bildes erhöhen bzw. verkleinern. Klicken Sie auf <strong>Zurücksetzen</strong>, um den Originalzoom des Bildes wiederherzustellen.<br /> Mit einem Mobilgerät können Sie durch Doppeltippen auf das Bild in Schritten einzoomen. Wenn Sie den maximalen Zoom erreicht haben, doppeltippen Sie erneut auf das Bild, um den Zoomstatus zurückzusetzen. Streichen Sie mit dem Finger über das Bild, um es zu schwenken.</p> <p>To enable or disable viewer presets in the user interface, see <a href="/help/assets/managing-viewer-presets.md">Managing Viewer Presets</a>.</p> </td> 
  </tr>
  <tr>
   <td>Karussell-Set</td> 
   <td>Nein</td> 
   <td>Ja</td> 
   <td><p><strong>Asset-Vorschau in bestimmtem Viewer</strong></p> 
    <ul> 
     <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdownliste angezeigt wird. Wählen Sie einen Viewer aus, den Sie auf das Asset anwenden möchten.</li> 
    </ul> <p>To enable or disable viewer presets in the user interface, see <a href="/help/assets/managing-viewer-presets.md">Managing Viewer Presets</a>.</p> </td> 
  </tr>
 </tbody>
</table>

