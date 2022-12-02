---
title: Konfigurieren asynchroner Vorgänge in [!DNL Adobe Experience Manager].
description: Führen Sie einige ressourcenintensive Aufgaben asynchron aus, um die Leistung in [!DNL Experience Manager Assets].
contentOwner: AG
feature: Asset Management
role: User
exl-id: 0abdfe87-d932-41dd-b1e6-9f5fa5b924fe
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '628'
ht-degree: 23%

---

# Asynchrone Vorgänge {#asynchronous-operations}

Verringerung der negativen Auswirkungen auf die Leistung, [!DNL Adobe Experience Manger Assets] verarbeitet bestimmte langwierige und ressourcenintensive Asset-Vorgänge asynchron. Die asynchrone Verarbeitung umfasst die Aneinanderreihung mehrerer Aufgaben und schließlich deren serielle Ausführung, abhängig von der Verfügbarkeit von Systemressourcen. Zu diesen Vorgängen gehören u. a.:

* Löschen vieler Assets.
* Verschieben vieler Assets oder Assets mit vielen Verweisen.
* Exportieren und Importieren von Asset-Metadaten in großen Mengen.

Sie können den Status asynchroner Aufgaben über die **[!UICONTROL Status asynchroner Aufträge]** Seite.

>[!NOTE]
>
>Standardmäßig wird die [!DNL Assets] Aufgaben werden parallel ausgeführt. Wenn `N` die Anzahl der CPU-Kerne, `N/2` Aufgaben können standardmäßig parallel ausgeführt werden. Um benutzerdefinierte Einstellungen für die Aufgabenwarteschlange zu verwenden, ändern Sie die **[!UICONTROL Standardwarteschlange für asynchrone Vorgänge]** Konfiguration aus der [!UICONTROL Web-Konsole]. Weitere Informationen finden Sie unter [Warteschlangenkonfigurationen](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#queue-configurations).

## Überwachen des Status asynchroner Vorgänge {#monitoring-the-status-of-asynchronous-operations}

Immer [!DNL Assets] einen Vorgang asynchron verarbeitet, erhalten Sie eine Benachrichtigung in Ihrer [!DNL Experience Manager] [Posteingang](/help/sites-authoring/inbox.md) und per E-Mail. Um den Status der asynchronen Vorgänge detailliert anzuzeigen, navigieren Sie zur Seite **[!UICONTROL Status asynchroner Aufträge]**.

1. Im [!DNL Experience Manager] Oberflächenklick **[!UICONTROL Aktivitäten]** > **[!UICONTROL Aufträge]**.

1. Überprüfen Sie die Details für die Vorgänge auf der Seite **[!UICONTROL Status von asynchronen Aufträgen]**.

   ![Status und Details asynchroner Vorgänge](assets/job_status.png)

   Informationen zum Fortschritt eines Vorgangs finden Sie unter **[!UICONTROL Status]** Spalte. Abhängig vom Fortschritt wird eine der folgenden Statusmeldungen angezeigt:

   * **[!UICONTROL Aktiv]**: Der Vorgang wird verarbeitet.
   * **[!UICONTROL Erfolg]**: Der Vorgang wurde abgeschlossen.
   * **[!UICONTROL Fehler]******: Der Vorgang konnte nicht verarbeitet werden.
   * **[!UICONTROL Geplant]**: Die Verarbeitung des Vorgangs ist für einen späteren Zeitpunkt geplant.

1. Um einen aktiven Vorgang anzuhalten, wählen Sie ihn aus der Liste aus und klicken Sie auf **[!UICONTROL Anhalten]** ![Stopp-Symbol](assets/do-not-localize/stop_icon.svg) aus der Symbolleiste.

1. Um zusätzliche Details anzuzeigen, z. B. eine Beschreibung und Protokolle, wählen Sie den Vorgang aus und klicken Sie auf **[!UICONTROL Öffnen]** ![open_icon](assets/do-not-localize/edit_icon.svg) aus der Symbolleiste. Die Aufgabendetailseite wird angezeigt.

   ![Details einer Metadaten-Importaufgabe](assets/job_details.png)

1. Um den Vorgang aus der Liste zu löschen, wählen Sie die Option **[!UICONTROL Löschen]** in der Symbolleiste aus. Um die Details als CSV-Datei herunterzuladen, tippen/klicken Sie auf **[!UICONTROL Herunterladen]**.

   >[!NOTE]
   >
   >Sie können eine Aufgabe nicht löschen, wenn ihr Status aktiv oder in der Warteschlange ist.

## Bereinigen abgeschlossener Aufgaben {#purge-completed-tasks}

[!DNL Experience Manager Assets] führt täglich um 100 Stunden eine Bereinigungsaufgabe aus, um abgeschlossene asynchrone Aufgaben zu löschen, die älter als einen Tag sind.

<!-- TBD: Find out from the engineering team and mention the time zone of this 1:00 am task.
-->

Sie können den Zeitplan für die Bereinigungsaufgabe und die Dauer ändern, für die Details abgeschlossener Aufgaben beibehalten werden, bevor sie gelöscht werden. Sie können auch die maximale Anzahl abgeschlossener Aufgaben konfigurieren, für die die Details zu einem beliebigen Zeitpunkt beibehalten werden.

1. Im [!DNL Experience Manager] Oberflächenklick **[!UICONTROL Instrumente]** > **[!UICONTROL Aktivitäten]** > **[!UICONTROL Web-Konsole]**.
1. Öffnen Sie die **[!UICONTROL Geplante Bereinigung asynchroner Aufträge für Adobe CQ DAM]** Aufgabe.
1. Geben Sie den Schwellenwert für die Anzahl der Tage an, nach denen abgeschlossene Aufgaben gelöscht werden, sowie die maximale Anzahl von Aufgaben, für die Details im Verlauf beibehalten werden. Speichern Sie die Änderungen.

   ![Konfiguration zum Planen der Bereinigung asynchroner Aufgaben](assets/purge_job.png)

## Konfigurieren des Schwellenwerts für asynchrone Löschvorgänge {#configure-thresholds-for-asynchronous-delete-operations}

Wenn die Anzahl der zu löschenden Assets oder Ordner den festgelegten Schwellenwert überschreitet, wird der Löschvorgang asynchron ausgeführt.

1. Im [!DNL Experience Manager] Oberflächenklick **[!UICONTROL Instrumente]** > **[!UICONTROL Aktivitäten]** > **[!UICONTROL Web-Konsole]**.
1. Aus dem [!UICONTROL Web-Konsole], öffnen Sie die **[!UICONTROL Verarbeitung asynchroner Löschvorgänge]** Konfiguration.
1. Im **[!UICONTROL Schwellenwert für Assets]** Legen Sie die Schwellenwerte fest, mit denen Assets, Ordner oder Verweise asynchron gelöscht werden sollen. Speichern Sie die Änderungen.

   ![Legen Sie den Schwellenwert für die Aufgabe fest, Assets zu löschen](assets/delete_threshold.png)

## Konfigurieren des Schwellenwerts für asynchrone Verschiebevorgänge {#configure-thresholds-for-asynchronous-move-operations}

Wenn die Anzahl der zu verschiebenden Assets, Ordner oder Verweise den festgelegten Schwellenwert überschreitet, wird der Verschiebungsvorgang asynchron ausgeführt.

1. Im [!DNL Experience Manager] Benutzeroberfläche, klicken Sie auf **[!UICONTROL Instrumente]** > **[!UICONTROL Aktivitäten]** > **[!UICONTROL Web-Konsole]**.
1. Aus dem [!UICONTROL Web-Konsole], öffnen Sie die **[!UICONTROL Verarbeitung asynchroner Verschiebevorgänge]** Konfiguration.
1. Im **[!UICONTROL Schwellenwert für Assets/Verweise]** Legen Sie den Schwellenwert fest, um Assets, Ordner oder Verweise asynchron zu verschieben. Speichern Sie die Änderungen.

   ![Legen Sie den Schwellenwert für die Aufgabe fest, Assets zu verschieben](assets/move_threshold.png)

>[!MORELIKETHIS]
>
>* [Konfigurieren von E-Mail in Experience Manager](/help/sites-administering/notification.md)
>* [Importieren und Exportieren von Asset-Metadaten in großen Mengen](/help/assets/metadata-import-export.md).

