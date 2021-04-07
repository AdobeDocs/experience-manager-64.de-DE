---
title: Anzeigen von Dynamic Media-Assets in der Vorschau
seo-title: Anzeigen von Dynamic Media-Assets in der Vorschau
description: Erfahren Sie, wie Sie Assets in Dynamic Media in einer Vorschau anzeigen.
seo-description: Erfahren Sie, wie Sie Assets in Dynamic Media in einer Vorschau anzeigen.
uuid: f0ff2fc4-a263-4dbe-ba46-b07077b49ae0
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 77296bff-8429-4240-af93-26076ae431ec
exl-id: ec05569a-6449-4430-9b9f-7ab051f44970
feature: Asset-Verwaltung, Darstellungen
role: Business Practitioner
translation-type: tm+mt
source-git-commit: 13eb1d64677f6940332a2eeb4d3aba2915ac7bba
workflow-type: tm+mt
source-wordcount: '1031'
ht-degree: 90%

---

# Anzeigen von Dynamic Media-Assets in der Vorschau {#previewing-assets}

Sie können **[!UICONTROL Vorschau]** verwenden, um zu sehen, wie ein digitales Dynamic Media-Asset aussieht, wenn es von einem Kunden in seinem eigenen Webbrowser angezeigt wird. Der dem Asset zugeordnete standardmäßige, eingebettete, geräteübergreifende Viewer wird für die **[!UICONTROL Vorschau]** verwendet.

Ein Viewer ist eine Sammlung aus verschiedenen Einstellungen oder „Vorgaben“, wie die Viewer-Anzeigegröße, das Zoom-Verhalten, die Farbschemata, Rahmen, Schriftarten usw., die bestimmen, wie Rich-Media-Assets auf den Computerbildschirmen und Mobilgeräten der Benutzer angezeigt werden.

Neben der dedizierten Vorschau für Videos, Rotationssets und Bildsätze können Sie ein Asset auch mithilfe von von von Ihnen erstellten Viewer-Vorgaben Vorschauen durchführen. Sie können auch Bildvorgaben zur Vorschau von Bilddarstellungen verwenden.

* [Anwenden von Bildvorgaben](image-presets.md)
* [Anwenden von Viewer-Vorgaben](viewer-presets.md)

>[!NOTE]
>
>Wenn Sie sich auf einer Web-Seite (Sites) in AEM befinden, können Sie keine Asset-Vorschau im **[!UICONTROL Bearbeitungsmodus]** anzeigen. Sie müssen in den **[!UICONTROL Vorschaumodus]** wechseln, indem Sie in der oberen rechten Ecke auf **Vorschau** klicken.

**So zeigen Sie die Asset-Vorschau an**:

1. Tippen Sie auf der Seite **Adobe Experience Manager** auf **[!UICONTROL Navigation]** auf **[!UICONTROL Asset]s** und dann **[!UICONTROL Dateien]**, um auf Assets zuzugreifen.
1. Tippen Sie rechts oben auf der Seite in der Dropdown-Liste **[!UICONTROL Ansicht]** auf **[!UICONTROL Listenansicht]**.
1. (Optional) Sortieren Sie in der Spalte **[!UICONTROL Typ]** die Assets nach dem Typ, den Sie in einer Vorschau anzeigen möchten.
1. Klicken Sie in der Spalte **[!UICONTROL Titel]** auf den Namen des Titels (nicht auf die Miniaturansicht) des Assets, das Sie in der Vorschau anzeigen möchten.
1. Führen Sie je nach ausgewähltem Asset eine der folgenden Aktionen aus:

<table> 
 <tbody>
  <tr>
   <td><strong>Asset-Typ, auf den Sie getippt haben</strong><br /> </td> 
   <td><strong>Asset-Vorschau in bestimmter Ausgabedarstellung möglich?</strong></td> 
   <td><strong>Asset-Vorschau in bestimmtem Viewer möglich?</strong></td> 
  </tr>
  <tr>
   <td><p>Bild</p> </td> 
   <td>Ja</td> 
   <td>Ja</td> 
   <td><p><strong>Asset-Vorschau in bestimmter Ausgabedarstellung</strong></p> 
    <ul> 
     <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdown-Liste angezeigt wird. Klicken Sie in der Liste auf <strong>Ausgabedarstellungen</strong> und wählen Sie dann die Ausgabedarstellung, die Sie in einer Vorschau anzeigen möchten.</li> 
    </ul> <p><strong>Asset-Vorschau in bestimmtem Viewer</strong></p> 
    <ul> 
     <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdown-Liste angezeigt wird. Klicken Sie in der Liste auf <strong>Viewer</strong>. Wählen Sie dann einen Viewer aus, den Sie auf das Asset anwenden möchten.</li> 
    </ul> <p>Mit den Symbolen <strong>+</strong> und <strong>-</strong> können Sie den Zoom des gewählten Bildes erhöhen bzw. verkleinern. Klicken Sie auf <strong>Zurücksetzen</strong>, um den Original-Zoom des Bildes wiederherzustellen.<br /> Mit einem Mobilgerät können Sie durch Doppeltippen auf das Bild in Schritten einzoomen. Wenn Sie den maximalen Zoom erreicht haben, doppeltippen Sie erneut auf das Bild, um den Zoomstatus zurückzusetzen. Streichen Sie mit dem Finger über das Bild, um es zu schwenken.</p> <p>Informationen zum Aktivieren oder Deaktivieren von Viewer-Vorgaben in der Benutzeroberfläche finden Sie in <a href="/help/assets/managing-viewer-presets.md">Verwalten von Viewer-Vorgaben</a>.<br /> </p> </td> 
  </tr>
  <tr>
   <td>Multimedia</td> 
   <td>Ja</td> 
   <td>Ja</td> 
   <td><p><strong>Asset-Vorschau in bestimmter Ausgabedarstellung</strong></p> 
    <ul> 
     <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdown-Liste angezeigt wird. Klicken Sie in der Liste auf <strong>Ausgabedarstellungen</strong> und wählen Sie dann die Ausgabedarstellung, die Sie in einer Vorschau anzeigen möchten.</li> 
    </ul> <p>Wenn Sie eine Videoausgabedarstellung mit einer höheren Auflösung für die Vorschau auswählen, kann das Video abgeschnitten werden. Dies liegt daran, dass in der Vorschau der Ausgabedarstellung die genaue Auflösung angezeigt wird, die auch die Kunden sehen, und zwar im Kontext des eingebetteten Viewers, über den die Vorschau erfolgt.</p> <p>Wenn Sie die Vorschau eines adaptiven Videosets auf Asset-Ebene anzeigen, werden die Ausgabedarstellungen in ein Wiedergabeerlebnis zusammengefasst. Das heißt, das adaptive Video wird entsprechend für die Anzeige skaliert und mit der optimalen Auflösung im Kontext des Anzeigegeräts und der Verbindungsgeschwindigkeit wiedergegeben.<br /> </p> <p><strong>Vorschau eines Assets in einem bestimmten Viewer anzeigen</strong></p> 
    <ul> 
     <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdown-Liste angezeigt wird. Klicken Sie in der Liste auf <strong>Viewer</strong>. Wählen Sie dann einen Viewer aus, den Sie auf das Asset anwenden möchten.</li> 
    </ul> <p>Informationen zum Aktivieren oder Deaktivieren von Viewer-Vorgaben in der Benutzeroberfläche finden Sie in <a href="/help/assets/managing-viewer-presets.md">Verwalten von Viewer-Vorgaben</a>.</p> </td> 
  </tr>
  <tr>
   <td>Bildset</td> 
   <td>Nein</td> 
   <td>Ja</td> 
   <td><p><strong>Vorschau eines Assets in einem bestimmten Viewer anzeigen</strong></p> 
    <ul> 
     <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdown-Liste angezeigt wird. Klicken Sie in der Liste auf <strong>Viewer</strong>. Wählen Sie dann einen Viewer aus, den Sie auf das Asset anwenden möchten.</li> 
    </ul> <p>Mit den Symbolen <strong>+</strong> und <strong>-</strong> können Sie den Zoom des gewählten Bildes erhöhen bzw. verkleinern. Klicken Sie auf <strong>Zurücksetzen</strong>, um den Original-Zoom des Bildes wiederherzustellen.<br /> Mit einem Mobilgerät können Sie durch Doppeltippen auf das Bild in Schritten einzoomen. Wenn Sie den maximalen Zoom erreicht haben, doppeltippen Sie erneut auf das Bild, um den Zoomstatus zurückzusetzen. Streichen Sie mit dem Finger über das Bild, um es zu schwenken.</p> <p>Informationen zum Aktivieren oder Deaktivieren von Viewer-Vorgaben in der Benutzeroberfläche finden Sie in <a href="/help/assets/managing-viewer-presets.md">Verwalten von Viewer-Vorgaben</a>.</p> </td> 
  </tr>
  <tr>
   <td>Rotationsset</td> 
   <td>Nein</td> 
   <td>Ja</td> 
   <td><p><strong>Vorschau eines Assets in einem bestimmten Viewer anzeigen</strong></p> 
    <ul> 
     <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdown-Liste angezeigt wird. Klicken Sie in der Liste auf <strong>Viewer</strong>. Wählen Sie dann einen Viewer aus, den Sie auf das Asset anwenden möchten.</li> 
    </ul> <p>Mit den Symbolen <strong>+</strong> und <strong>-</strong> können Sie den Zoom des gewählten Bildes erhöhen bzw. verkleinern. Klicken Sie auf <strong>Zurücksetzen</strong>, um den Original-Zoom des Bildes wiederherzustellen.<br /> Mit einem Mobilgerät können Sie durch Doppeltippen auf das Bild in Schritten einzoomen. Wenn Sie den maximalen Zoom erreicht haben, doppeltippen Sie erneut auf das Bild, um den Zoomstatus zurückzusetzen. Streichen Sie mit dem Finger über das Bild, um es zu schwenken.</p> <p>Informationen zum Aktivieren oder Deaktivieren von Viewer-Vorgaben in der Benutzeroberfläche finden Sie in <a href="/help/assets/managing-viewer-presets.md">Verwalten von Viewer-Vorgaben</a>.</p> </td> 
  </tr>
  <tr>
   <td>Sets für gemischte Medien</td> 
   <td>Nein</td> 
   <td>Ja</td> 
   <td><p><strong>Vorschau eines Assets in einem bestimmten Viewer anzeigen</strong></p> 
    <ul> 
     <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdown-Liste angezeigt wird. Klicken Sie in der Liste auf <strong>Viewer</strong>. Wählen Sie dann einen Viewer aus, den Sie auf das Asset anwenden möchten.</li> 
    </ul> <p>Mit den Symbolen <strong>+</strong> und <strong>-</strong> können Sie den Zoom des gewählten Bildes erhöhen bzw. verkleinern. Klicken Sie auf <strong>Zurücksetzen</strong>, um den Original-Zoom des Bildes wiederherzustellen.<br /> Mit einem Mobilgerät können Sie durch Doppeltippen auf das Bild in Schritten einzoomen. Wenn Sie den maximalen Zoom erreicht haben, doppeltippen Sie erneut auf das Bild, um den Zoomstatus zurückzusetzen. Streichen Sie mit dem Finger über das Bild, um es zu schwenken.</p> <p>Informationen zum Aktivieren oder Deaktivieren von Viewer-Vorgaben in der Benutzeroberfläche finden Sie in <a href="/help/assets/managing-viewer-presets.md">Verwalten von Viewer-Vorgaben</a>.</p> </td> 
  </tr>
  <tr>
   <td>Karussellset</td> 
   <td>Nein</td> 
   <td>Ja</td> 
   <td><p><strong>Vorschau eines Assets in einem bestimmten Viewer anzeigen</strong></p> 
    <ul> 
     <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdown-Liste angezeigt wird. Wählen Sie einen Viewer aus, den Sie auf das Asset anwenden möchten.</li> 
    </ul> <p>Informationen zum Aktivieren oder Deaktivieren von Viewer-Vorgaben in der Benutzeroberfläche finden Sie in <a href="/help/assets/managing-viewer-presets.md">Verwalten von Viewer-Vorgaben</a>.</p> </td> 
  </tr>
 </tbody>
</table>
