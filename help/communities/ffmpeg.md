---
title: FFmpeg für Communities
seo-title: FFmpeg für Communities
description: Installieren und Konfigurieren von FFmpeg für Communities
seo-description: Installieren und Konfigurieren von FFmpeg für Communities
uuid: ef2f821c-70e9-4889-a8d7-a93b10a1d428
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 739ec991-552b-42cd-85cd-984d1c9fe8fd
role: Administrator
exl-id: 9ed54ee3-3509-4a43-a710-90f4543ccaf3
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 1%

---

# FFmpeg für Communities {#ffmpeg-for-communities}

## Überblick {#overview}

FFmpeg ist eine Lösung zum Konvertieren und Streaming von Audio und Video und wird bei der Installation für die ordnungsgemäße Transkodierung von [Video-Assets](../../help/sites-authoring/default-components-foundation.md#video) sowie für die Aktivierungsfunktion von AEM Communities verwendet.

FFmpeg wird in der Autorenumgebung verwendet, um Metadaten für hochgeladene Aktivierungsressourcen abzurufen und eine Miniaturansicht zu generieren, die bei der Auflistung der Aktivierungsressource angezeigt wird.

## Installieren von FFmpeg {#installing-ffmpeg}

FFmpeg sollte auf den Servern installiert sein, auf denen die AEM *author* -Instanz(en) gehostet wird.

1. Gehen Sie zu [https://www.ffmpeg.org](https://www.ffmpeg.org/)
1. Laden Sie die neueste Version von FFmpeg für Ihre spezifische Umgebung herunter (Macintosh, Windows oder Linux).

   * Es ist wichtig, FFmpeg aufgrund von Sicherheitslücken in älteren Versionen auf dem neuesten Stand zu halten

1. Installieren Sie FFmpeg anhand der Anweisungen für das Betriebssystem.

1. Stellen Sie sicher, dass die ausführbare FFmpeg-Datei in Ihrem Systempfad festgelegt ist.

   Sie sollten in der Lage sein, FFmpeg aus einem beliebigen Verzeichnis in Ihrem System auszuführen.

   * Beispiel: `ffmpeg -version`

## FFmpeg Transcoding Service {#configure-ffmpeg-transcoding-service} konfigurieren

Wenn FFmpeg installiert ist, werden gemäß der Workflow-Definition DAM Update Asset standardmäßig mehrere Ausgabedarstellungen konfiguriert (Transkodierungen).

Da die Transkodierungen CPU-intensiv sind, wird empfohlen, die Liste der Zielausgabeformate zu ändern. In den meisten Fällen ist eine Transkodierung nicht erforderlich.

So ändern Sie den Workflow &quot;DAM-Update-Asset&quot;und deaktivieren Sie in diesem Beispiel die Transkodierung:

* Bei der Autoreninstanz mit Administratorrechten anmelden
* Über die globale Navigation: **[!UICONTROL Tools > Workflow > Modelle]**
* Suchen Sie **[!UICONTROL DAM Update Asset]**
* Doppelklicken Sie auf , um den Workflow zur Bearbeitung in der klassischen Benutzeroberfläche zu öffnen.

   Ergebnisort: [http://localhost:4502/cf#/etc/workflow/models/dam/update_asset.html](http://localhost:4502/cf#/etc/workflow/models/dam/update_asset.html)

* Doppelklicken Sie auf den Schritt **[!UICONTROL FFmpeg-Transkodierung]** , um auf das Dialogfeld Schritt-Eigenschaften zuzugreifen.
* Auf der Registerkarte **[!UICONTROL Process]** :

   * **[!UICONTROL Argumente]**: Löschen Sie alle Einträge, um die Transkodierung von Standardwerten zu deaktivieren:  `profile:firefoxhq,profile:hq,profile:flv,profile:iehq`

![chlimage_1-372](assets/chlimage_1-372.png)

* Wählen Sie **[!UICONTROL OK]** aus, um das Dialogfeld `Step Properties` zu schließen.

* Wählen Sie **[!UICONTROL Save]** aus, um den Workflow `DAM Update Asset` zu speichern.

   (obere linke Ecke)
