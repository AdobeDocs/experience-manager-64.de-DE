---
title: Anzeigen von Dynamic Media-Assets in der Vorschau
seo-title: Previewing Dynamic Media assets
description: Erfahren Sie, wie Sie Assets in Dynamic Media in einer Vorschau anzeigen.
seo-description: Learn how to preview assets in Dynamic Media
uuid: f0ff2fc4-a263-4dbe-ba46-b07077b49ae0
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 77296bff-8429-4240-af93-26076ae431ec
exl-id: ec05569a-6449-4430-9b9f-7ab051f44970
feature: Asset Management,Renditions
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1052'
ht-degree: 59%

---

# Anzeigen von Dynamic Media-Assets in der Vorschau {#previewing-assets}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Sie können **[!UICONTROL Vorschau]** um zu sehen, wie ein digitales Dynamic Media-Asset aussieht, wenn es von einem Kunden in seinem eigenen Webbrowser angezeigt wird. Der dem Asset zugewiesene standardmäßige eingebettete, geräteübergreifende Viewer wird für die **[!UICONTROL Vorschau]**.

Ein Viewer ist eine Sammlung verschiedener Einstellungen oder &quot;Vorgaben&quot;, z. B. die Viewer-Anzeigegröße, das Zoom-Verhalten, Farbschemata, Rahmen, Schriftarten usw., die bestimmen, wie Benutzer Rich-Media-Assets auf ihren Computerbildschirmen und Mobilgeräten anzeigen.

Sie können die dedizierte Vorschaufunktion für Videos, Rotationssets und Bildsets verwenden und außerdem mithilfe der von Ihnen erstellten Viewer-Vorgaben eine Vorschau eines Assets anzeigen. Alternativ dazu können Sie auch Bildvorgaben verwenden, um Ausgabedarstellungen von Bildern anzuzeigen.

* [Anwenden von Bildvorgaben](image-presets.md)
* [Anwenden von Viewer-Vorgaben](viewer-presets.md)

>[!NOTE]
>
>Wenn Sie sich auf einer Web-Seite (Sites) in AEM befinden, können Sie keine Asset-Vorschau im **[!UICONTROL Bearbeitungsmodus]** anzeigen. Sie müssen in den **[!UICONTROL Vorschaumodus]** wechseln, indem Sie in der oberen rechten Ecke auf **Vorschau** klicken.

**So zeigen Sie die Asset-Vorschau an**:

1. Von **Adobe Experience Manager** auf **[!UICONTROL Navigation]** Seite, tippen Sie auf **[!UICONTROL Asset]s**, dann **[!UICONTROL Dateien]** , um auf Assets zuzugreifen.
1. Tippen Sie rechts oben auf der Seite in der Dropdown-Liste **[!UICONTROL Ansicht]** auf **[!UICONTROL Listenansicht]**.
1. (Optional) Sortieren Sie in der Spalte **[!UICONTROL Typ]** die Assets nach dem Typ, den Sie in einer Vorschau anzeigen möchten.
1. Unter dem **[!UICONTROL Titel]** klicken Sie auf den Titel (nicht das Miniaturbild) des Assets, das Sie in der Vorschau anzeigen möchten.
1. Führen Sie je nach angeklicktem Asset-Typ einen der folgenden Schritte aus:

<table> 
 <tbody>
  <tr>
   <td><strong>Asset-Typ, auf den Sie tippt haben</strong><br /> </td> 
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
     <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdown-Liste angezeigt wird. Klicken <strong>Viewer</strong> Wählen Sie in der Liste einen Viewer aus, den Sie auf das Asset anwenden möchten.</li> 
    </ul> <p>Mit den Symbolen <strong>+</strong> und <strong>-</strong> können Sie den Zoom des gewählten Bildes erhöhen bzw. verkleinern. Klicken Sie auf <strong>Zurücksetzen</strong>, um den Original-Zoom des Bildes wiederherzustellen.<br /> Auf einem Mobilgerät können Sie durch Doppeltippen auf das Bild in Schritten einzoomen. Wenn Sie den maximalen Zoom erreichen, doppeltippen Sie erneut auf das Bild, um den Zoomstatus zurückzusetzen. Ziehen Sie über das Bild, um es zu schwenken.</p> <p>Informationen zum Aktivieren oder Deaktivieren von Viewer-Vorgaben in der Benutzeroberfläche finden Sie in <a href="/help/assets/managing-viewer-presets.md">Verwalten von Viewer-Vorgaben</a>.<br /> </p> </td> 
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
     <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdown-Liste angezeigt wird. Klicken <strong>Viewer</strong> Wählen Sie in der Liste einen Viewer aus, den Sie auf das Asset anwenden möchten.</li> 
    </ul> <p>Informationen zum Aktivieren oder Deaktivieren von Viewer-Vorgaben in der Benutzeroberfläche finden Sie in <a href="/help/assets/managing-viewer-presets.md">Verwalten von Viewer-Vorgaben</a>.</p> </td> 
  </tr>
  <tr>
   <td>Bildset</td> 
   <td>Nein</td> 
   <td>Ja</td> 
   <td><p><strong>Vorschau eines Assets in einem bestimmten Viewer anzeigen</strong></p> 
    <ul> 
     <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdown-Liste angezeigt wird. Klicken <strong>Viewer</strong> Wählen Sie in der Liste einen Viewer aus, den Sie auf das Asset anwenden möchten.</li> 
    </ul> <p>Mit den Symbolen <strong>+</strong> und <strong>-</strong> können Sie den Zoom des gewählten Bildes erhöhen bzw. verkleinern. Klicken Sie auf <strong>Zurücksetzen</strong>, um den Original-Zoom des Bildes wiederherzustellen.<br /> Auf einem Mobilgerät können Sie durch Doppeltippen auf das Bild in Schritten einzoomen. Wenn Sie den maximalen Zoom erreichen, doppeltippen Sie erneut auf das Bild, um den Zoomstatus zurückzusetzen. Ziehen Sie über das Bild, um es zu schwenken.</p> <p>Informationen zum Aktivieren oder Deaktivieren von Viewer-Vorgaben in der Benutzeroberfläche finden Sie in <a href="/help/assets/managing-viewer-presets.md">Verwalten von Viewer-Vorgaben</a>.</p> </td> 
  </tr>
  <tr>
   <td>Rotationsset</td> 
   <td>Nein</td> 
   <td>Ja</td> 
   <td><p><strong>Vorschau eines Assets in einem bestimmten Viewer anzeigen</strong></p> 
    <ul> 
     <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdown-Liste angezeigt wird. Klicken <strong>Viewer</strong> Wählen Sie in der Liste einen Viewer aus, den Sie auf das Asset anwenden möchten.</li> 
    </ul> <p>Mit den Symbolen <strong>+</strong> und <strong>-</strong> können Sie den Zoom des gewählten Bildes erhöhen bzw. verkleinern. Klicken Sie auf <strong>Zurücksetzen</strong>, um den Original-Zoom des Bildes wiederherzustellen.<br /> Auf einem Mobilgerät können Sie durch Doppeltippen auf das Bild in Schritten einzoomen. Wenn Sie den maximalen Zoom erreichen, doppeltippen Sie erneut auf das Bild, um den Zoomstatus zurückzusetzen. Ziehen Sie über das Bild, um es zu schwenken.</p> <p>Informationen zum Aktivieren oder Deaktivieren von Viewer-Vorgaben in der Benutzeroberfläche finden Sie in <a href="/help/assets/managing-viewer-presets.md">Verwalten von Viewer-Vorgaben</a>.</p> </td> 
  </tr>
  <tr>
   <td>gemischtes Medienset</td> 
   <td>Nein</td> 
   <td>Ja</td> 
   <td><p><strong>Vorschau eines Assets in einem bestimmten Viewer anzeigen</strong></p> 
    <ul> 
     <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdown-Liste angezeigt wird. Klicken <strong>Viewer</strong> Wählen Sie in der Liste einen Viewer aus, den Sie auf das Asset anwenden möchten.</li> 
    </ul> <p>Mit den Symbolen <strong>+</strong> und <strong>-</strong> können Sie den Zoom des gewählten Bildes erhöhen bzw. verkleinern. Klicken Sie auf <strong>Zurücksetzen</strong>, um den Original-Zoom des Bildes wiederherzustellen.<br /> Auf einem Mobilgerät können Sie durch Doppeltippen auf das Bild in Schritten einzoomen. Wenn Sie den maximalen Zoom erreichen, doppeltippen Sie erneut auf das Bild, um den Zoomstatus zurückzusetzen. Ziehen Sie über das Bild, um es zu schwenken.</p> <p>Informationen zum Aktivieren oder Deaktivieren von Viewer-Vorgaben in der Benutzeroberfläche finden Sie in <a href="/help/assets/managing-viewer-presets.md">Verwalten von Viewer-Vorgaben</a>.</p> </td> 
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
