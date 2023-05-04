---
title: FFmpeg für Communities
seo-title: FFmpeg for Communities
description: Installieren und Konfigurieren von FFmpeg für Communities
seo-description: How to install and configure FFmpeg for Communities
uuid: ef2f821c-70e9-4889-a8d7-a93b10a1d428
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 739ec991-552b-42cd-85cd-984d1c9fe8fd
role: Admin
exl-id: 9ed54ee3-3509-4a43-a710-90f4543ccaf3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 3%

---

# FFmpeg für Communities {#ffmpeg-for-communities}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Übersicht {#overview}

FFmpeg ist eine Lösung für das Konvertieren und Streaming von Audio und Video und wird, falls installiert, für die ordnungsgemäße Transkodierung von [Video-Assets](../../help/sites-authoring/default-components-foundation.md#video) sowie für die Aktivierungsfunktion von AEM Communities.

FFmpeg wird in der Autorenumgebung verwendet, um Metadaten für hochgeladene Aktivierungsressourcen abzurufen und eine Miniaturansicht zu generieren, die bei der Auflistung der Aktivierungsressource angezeigt werden soll.

## Installieren von FFmpeg {#installing-ffmpeg}

FFmpeg sollte auf den Servern installiert sein, auf denen das AEM gehostet wird *author* Instanz(en).

1. Navigieren Sie zu [https://www.ffmpeg.org](https://www.ffmpeg.org/)
1. Laden Sie die neueste Version von FFmpeg für Ihre spezifische Umgebung herunter (Macintosh, Windows oder Linux).

   * Es ist wichtig, FFmpeg aufgrund von Sicherheitslücken in älteren Versionen auf dem neuesten Stand zu halten

1. Installieren Sie FFmpeg anhand der Anweisungen für das Betriebssystem.

1. Stellen Sie sicher, dass die ausführbare FFmpeg-Datei in Ihrem Systempfad festgelegt ist.

   Sie sollten in der Lage sein, FFmpeg aus einem beliebigen Verzeichnis in Ihrem System auszuführen.

   * Beispiel: `ffmpeg -version`

## FFmpeg Transcoding Service konfigurieren {#configure-ffmpeg-transcoding-service}

Wenn FFmpeg installiert ist, werden gemäß der Workflow-Definition DAM Update Asset standardmäßig mehrere Ausgabedarstellungen konfiguriert (Transkodierungen).

Da die Transkodierungen CPU-intensiv sind, wird empfohlen, die Liste der Zielausgabeformate zu ändern. In den meisten Fällen ist eine Transkodierung nicht erforderlich.

So ändern Sie den Workflow &quot;DAM-Update-Asset&quot;und deaktivieren Sie in diesem Beispiel die Transkodierung:

* Bei der Autoreninstanz mit Administratorrechten anmelden
* Über die globale Navigation: **[!UICONTROL Tools > Workflow > Modelle]**
* Suchen **[!UICONTROL DAM-Update-Asset]**
* Doppelklicken Sie auf , um den Workflow zur Bearbeitung in der klassischen Benutzeroberfläche zu öffnen.

   Ergebnisort: [http://localhost:4502/cf#/etc/workflow/models/dam/update_asset.html](http://localhost:4502/cf#/etc/workflow/models/dam/update_asset.html)

* Doppelklicken Sie auf die **[!UICONTROL FFmpeg-Transkodierung]** Schritt zum Aufrufen des Dialogfelds &quot;Schritt-Eigenschaften&quot;
* Unter dem **[!UICONTROL Prozess]** tab:

   * **[!UICONTROL Werbemittel]**: Löschen Sie alle Einträge, um die Transkodierung von Standardwerten zu deaktivieren: `profile:firefoxhq,profile:hq,profile:flv,profile:iehq`

![chlimage_1-372](assets/chlimage_1-372.png)

* Auswählen **[!UICONTROL OK]** zum Schließen der `Step Properties` dialog

* Auswählen **[!UICONTROL Speichern]** , um `DAM Update Asset` Workflow

   (obere linke Ecke)
