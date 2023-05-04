---
title: Verwalten von Video-Assets
description: Erfahren Sie, wie Sie Video-Assets hochladen, in der Vorschau anzeigen, kommentieren und veröffentlichen.
uuid: 56a8c221-409f-4605-97b1-a054dd2abfab
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: f341fae1-dda3-4917-b6db-ad02fec63702
feature: Asset Management,Video
role: User
exl-id: eb652414-5b10-45af-a8b6-f1de649994c5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '823'
ht-degree: 41%

---

# Verwalten von Video-Assets    {#managing-video-assets}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Erfahren Sie, wie Sie die Video-Assets in Adobe Experience Manager Assets verwalten und bearbeiten. Wenn Sie für die Verwendung von Dynamic Media lizenziert sind, lesen Sie auch den Abschnitt [Dynamic Media-Videodokumentation](video.md).

## Hochladen und Anzeigen der Vorschau von Video-Assets {#uploading-and-previewing-video-assets}

[!DNL Experience Manager] Assets generiert eine Vorschau für Video-Assets mit der Erweiterung MP4. Wenn das Format des Assets nicht MP4 lautet, installieren Sie das FFmpeg-Pack, um die Vorschau zu generieren. FFmpeg erstellt Video-Ausgabedarstellungen vom Typ OGG und MP4. Sie können eine Vorschau dieser Ausgabedarstellungen im [!DNL Experience Manager] Assets-Benutzeroberfläche.

1. Navigieren Sie im Ordner &quot;Digitale Assets&quot;oder in den Unterordnern zu dem Speicherort, an dem Sie digitale Assets hinzufügen möchten.
1. Um das Asset hochzuladen, klicken oder tippen Sie auf **[!UICONTROL Erstellen]** Wählen Sie in der Symbolleiste und anschließend **[!UICONTROL Dateien]**. Alternativ können Sie sie direkt im Asset-Bereich ablegen. Weitere Informationen zum Hochladen finden Sie unter [Hochladen von Assets](managing-assets-touch-ui.md#uploading-assets).
1. Rufen Sie die Vorschau eines Videos in der Kartenansicht auf, indem Sie auf die Schaltfläche **[!UICONTROL Wiedergabe]** im Video-Asset tippen.

   ![chlimage_1-201](assets/chlimage_1-201.png)

   Sie können Videos im **[!UICONTROL Karte]** nur anzeigen. Die Schaltfläche Wiedergabe/Pause ist nicht im **[!UICONTROL Liste]** anzeigen.

1. Tippen Sie auf **[!UICONTROL Bearbeiten]** auf der Karte angezeigt, um eine Vorschau des Videos im **[!UICONTROL Details]** anzeigen.

   Das Video wird im systemeigenen Video-Player des Browsers wiedergegeben. Sie können das Video wiedergeben und anhalten, die Lautstärke regeln und in den Vollbildmodus wechseln.

   ![chlimage_1-202](assets/chlimage_1-202.png)

## Konfiguration zum Hochladen von Assets, die größer als 2 GB sind {#configuration-to-upload-video-assets-that-are-larger-than-gb}

Standardmäßig wird die [!DNL Experience Manager] Mit Assets können Sie keine Assets hochladen, die aufgrund einer Dateigrößenbeschränkung größer als 2 GB sind. Sie können diese Beschränkung aber umgehen, indem Sie CRXDE Lite aufrufen und im Verzeichnis `/apps` einen Knoten erstellen. Der Knoten muss denselben Knotennamen, dieselbe Verzeichnisstruktur und vergleichbare Knoteneigenschaften im Hinblick auf die Reihenfolge aufweisen.

Zusätzlich zu [!DNL Experience Manager] Ändern Sie die folgenden Konfigurationen, um große Assets hochzuladen:

* Erhöhen Sie die Ablaufzeit des Tokens. Siehe [!UICONTROL Adobe Granite CSRF Servlet] in der Web-Konsole unter `https://[aem_server]:[port]/system/console/configMgr`. Weitere Informationen finden Sie unter [CSRF-Schutz](/help/sites-developing/csrf-protection.md).
* Erhöhen Sie `receiveTimeout` in der Dispatcher-Konfiguration. Weitere Informationen finden Sie unter [Experience Manager Dispatcher-Konfiguration](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=de#renders-options).

>[!NOTE]
>
>Die [!DNL Experience Manager] Die klassische Benutzeroberfläche hat keine Dateigrößenbeschränkung von zwei Gigabyte. Außerdem werden End-to-End-Workflows für große Videos nicht vollständig unterstützt.

Um eine höhere Dateigrößenbeschränkung zu konfigurieren, führen Sie die folgenden Schritte im Verzeichnis `/apps` aus.

1. Tippen Sie in AEM auf **[!UICONTROL Tools > Allgemein > CRXDE Lite]**.
1. Im **[!UICONTROL CRXDE Lite]** Seite, navigieren Sie im Verzeichnisfenster auf der linken Seite zu `/libs/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload`. Um das Verzeichnisfenster anzuzeigen, tippen Sie auf `>>` Symbol.
1. Tippen Sie in der Symbolleiste auf **[!UICONTROL Überlagerungsknoten]**. Wählen Sie alternativ **[!UICONTROL Überlagerungsknoten]** aus dem Kontextmenü aus.
1. Tippen Sie im Dialogfeld **[!UICONTROL Überlagerungsknoten]** auf **[!UICONTROL OK]**.

   ![chlimage_1-203](assets/chlimage_1-203.png)

1. Aktualisieren Sie die Browser-Ansicht. Der Überlagerungsknoten `/apps/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload` ist ausgewählt.
1. Geben Sie auf der Registerkarte **[!UICONTROL Eigenschaften]** den gewünschten Wert in Byte ein, um die maximale Größe festzulegen. Geben Sie beispielsweise `32212254720` -Wert, um die Größenbeschränkung auf 30 GB zu erhöhen.

1. Tippen Sie in der Symbolleiste auf **[!UICONTROL Alle speichern]**.
1. Tippen Sie in AEM auf **[!UICONTROL Tools > Vorgänge > Web-Konsole]**.
1. Im **[!UICONTROL Adobe Experience Manager Web Console Bundles]** Seite, unter der **[!UICONTROL Name]** Spalte der Tabelle, suchen Sie nach und tippen Sie auf **[!UICONTROL Adobe Granite Workflow External Process Job Handler]**.
1. Im **[!UICONTROL Adobe Granite Workflow External Process Job Handler]** Seite, legen Sie die Sekunden für **[!UICONTROL Standard-Timeout]** und **[!UICONTROL Max. Timeout]** Felder zu `18000` (fünf Stunden).
1. Tippen Sie auf **[!UICONTROL Speichern]**.
1. Tippen Sie in AEM auf **[!UICONTROL Tools > Workflow > Modelle]**.
1. Im **[!UICONTROL Workflow-Modelle]** Seite, wählen Sie **[!UICONTROL Dynamic Media-Kodierungsvideo]** und tippen Sie dann auf **[!UICONTROL Bearbeiten]**.
1. Im **[!UICONTROL Workflow]** Seite, doppeltippen Sie auf die **[!UICONTROL Dynamic Media Video Service-Prozess]** -Komponente.
1. Erweitern Sie im Dialogfeld **[!UICONTROL Schritteigenschaften]** auf der Registerkarte **[!UICONTROL Allgemein]** die Option **[!UICONTROL Erweiterte Einstellungen]**.
1. Geben Sie im Feld **[!UICONTROL Timeout]** den Wert `18000` an und tippen Sie dann auf **[!UICONTROL OK]**, um zur Workflow-Seite **[!UICONTROL Dynamic Media-Videokodierung]** zurückzukehren.
1. Oben auf der Seite unter dem **[!UICONTROL Dynamic Media-Kodierungsvideo]** Seitentitel, tippen Sie auf **[!UICONTROL Speichern]**.

## Veröffentlichen von Video-Assets {#publishing-video-assets}

Nach dem Veröffentlichen Ihrer Video-Assets können diese über eine URL auf einer Web-Seite eingebunden oder eingebettet werden. Siehe [Veröffentlichen von Assets](publishing-dynamicmedia-assets.md).

## Hinzufügen von Anmerkungen zu Video-Assets {#annotating-video-assets}

1. Tippen Sie in der Konsole &quot;Assets&quot;auf die **[!UICONTROL Bearbeiten]** auf der Asset-Karte, um die Seite mit den Asset-Details anzuzeigen.
1. Tippen Sie auf **[!UICONTROL Vorschau]** Symbol, um das Video wiederzugeben.
1. Um das Video zu kommentieren, tippen Sie auf **[!UICONTROL Anmerken]** Schaltfläche. Zu dem bestimmten Zeitpunkt (Frame) im Video wird eine Anmerkung hinzugefügt.

   Beim Anmerken können Sie auf der Arbeitsfläche zeichnen und einen Kommentar zur Zeichnung hinzufügen. Kommentare werden automatisch in Adobe Experience Manager Assets gespeichert.

   ![chlimage_1-204](assets/chlimage_1-204.png)

   Tippen Sie zum Beenden des Anmerkungsassistenten auf **[!UICONTROL Schließen]**.

1. Um zu einem bestimmten Punkt im Video zu springen, geben Sie die Zeit in Sekunden in das Textfeld ein und klicken Sie auf **[!UICONTROL Sprung]**. Um beispielsweise die ersten 20 Sekunden des Videos zu überspringen, geben Sie `20` im Textfeld.

   ![chlimage_1-205](assets/chlimage_1-205.png)

1. Klicken Sie auf eine Anmerkung, um sie in der Timeline anzuzeigen. Tippen **[!UICONTROL Löschen]** , um die Anmerkung aus der Timeline zu entfernen.

   ![chlimage_1-206](assets/chlimage_1-206.png)
