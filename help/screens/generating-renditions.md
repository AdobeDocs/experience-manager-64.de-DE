---
title: Videoausgabeformate
seo-title: Videoausgabeformate
description: Auf dieser Seite erfahren Sie, wie Sie Full HD-Wiedergaben für Screens-Projekte generieren.
seo-description: Auf dieser Seite erfahren Sie, wie Sie Full HD-Wiedergaben für Screens-Projekte generieren.
uuid: 0a3b009e-8a97-4396-ad47-97077fe26cde
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: authoring
discoiquuid: 40a182fd-7772-4ef7-b4fd-29ef99390b4a
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Videoausgabeformate{#video-renditions}

Es ist möglich, manuelle und automatische Full HD-Ausgabeformate zu generieren. Im folgenden Abschnitt wird der Workflow zum Hinzufügen von Ausgabeformaten zu Assets beschrieben.

## Automatisches Generieren von Full HD-Ausgabeformaten            {#automatically-generating-full-hd-renditions}

>[!NOTE]
>
>Wenn keine optimale Wiedergabe der AEM Screens-Videoausgabeformate auf Ihrem Gerät möglich ist, setzen Sie sich mit dem Hardwareanbieter in Verbindung, um sich über die Spezifikationen für das Video zu informieren. Auf diese Weise erhalten Sie eine optimale Leistung auf dem Gerät und können Ihr eigenes Videoprofil mit entsprechenden FFMPEG-Parametern für die gewünschten Wiedergabeformate erstellen. Gehen Sie anschließend wie folgt vor, um Ihr eigenes Videoprofil der Profilliste hinzuzufügen.
>
>Darüber hinaus finden Sie Informationen zum Debuggen und zur Fehlerbehebung der Videowiedergabe unter [Fehlerbehebung beim Arbeiten mit Videos](/help/screens/troubleshoot-videos.md).

Gehen Sie wie folgt vor, um automatisch Full HD-Ausgabeformate zu generieren:

1. Wählen Sie den Adobe Experience Manager-Link (oben links) aus und klicken Sie auf das Hammersymbol, um Tools zum Auswählen von **Workflow** aufzurufen.

   Klicken Sie auf **Modelle**, um die Verwaltung der Workflow-Modelle aufzurufen.

   ![screen_shot_2018-02-01at123407pm](assets/screen_shot_2018-02-01at123407pm.png)

1. Wählen Sie das Modell „DAM-Update-Asset“ aus und klicken Sie in der Aktionsleiste auf „Bearbeiten“, um das Fenster „DAM-Update-Asset“ zu öffnen.

   ![step5_-_edit_thedamupdateassetmodel](assets/step5_-_edit_thedamupdateassetmodel.png)

1. Doppelklicken Sie auf den Schritt **FFmpeg-Transkodierung**.

   ![screen_shot_2018-02-01at124454pm](assets/screen_shot_2018-02-01at124454pm.png)

1. Wählen Sie die Registerkarte **Prozess** aus, um die Prozessargumente zu bearbeiten. Geben Sie in der Liste unter **Argumente** die Full HD-Profile wie folgt ein: ***profile:fullhd-bp,profile:fullhd-hp***. Klicken Sie dann auf **OK**.

   ![screen_shot_2018-02-02at103340am](assets/screen_shot_2018-02-02at103340am.png)

1. Klicken Sie oben links im Bildschirm „DAM-Update-Asset“ auf „Speichern“.

   ![screen_shot_2018-02-02at101830am](assets/screen_shot_2018-02-02at101830am.png)

1. Navigieren Sie zu **Assets** und laden Sie ein neues Video hoch. Klicken Sie auf das Video und öffnen Sie die Seitenleiste „Wiedergaben“. Dort sehen Sie zwei Full HD-Videos.

   ![step10_-_open_thevideoasset](assets/step10_-_open_thevideoasset.png)

1. Öffnen Sie über die Seitenleiste die Option **Wiedergaben**.

   ![step11_-_open_therenditionssiderail](assets/step11_-_open_therenditionssiderail.png)

1. Sie werden zwei neue Full HD-Wiedergaben bemerken.

   ![step12_-_2_new_renditionsareaddedtothevideo](assets/step12_-_2_new_renditionsareaddedtothevideo.png)

## Manuelles Generieren von Full HD-Wiedergaben {#manually-generating-full-hd-renditions}

Gehen Sie wie folgt vor, um manuell Full HD-Wiedergaben zu generieren:

1. Wählen Sie den Adobe Experience Manager-Link (oben links) aus und klicken Sie auf das Hammersymbol, um Tools zum Auswählen von **Workflow** aufzurufen.

   Klicken Sie auf **Modelle**, um die Verwaltung der Workflow-Modelle aufzurufen.

   ![screen_shot_2018-02-01at123407pm-1](assets/screen_shot_2018-02-01at123407pm-1.png)

1. Wählen Sie das Modell „Screens – Asset aktualisieren“ aus und klicken Sie auf **Workflow starten**, um das Dialogfeld **Workflow ausführen** zu öffnen.

   ![step5_-_start_a_newscreensupdateassetworkflow](assets/step5_-_start_a_newscreensupdateassetworkflow.png)

1. Wählen Sie das gewünschte Video unter **Nutzlast** aus und klicken Sie auf **Ausführen**.

   ![step6_-_select_thedesiredvideo](assets/step6_-_select_thedesiredvideo.png)

1. Navigieren Sie zu **Assets**, führen Sie einen Drilldown zum gewünschten Asset durch und klicken Sie darauf.

   ![step7_-_open_thevideoasset](assets/step7_-_open_thevideoasset.png)

1. Wenn Sie die Seitenleiste **Wiedergaben** öffnen, sehen Sie die neuen Full HD-Wiedergaben.

   ![step8_-_open_therenditionssiderail](assets/step8_-_open_therenditionssiderail.png)

