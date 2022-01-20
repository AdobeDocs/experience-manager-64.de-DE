---
title: Vordefinierte Berichte in Prozessberichten
seo-title: Pre-defined reports in Process Reporting
description: Abfragen von AEM Forms on JEE-Prozessdaten zum Erstellen von Berichten zu langwierigen Prozessen, Prozessdauer und Workflow-Volumen
seo-description: Query for AEM Forms on JEE process data to create reports on long running processes, Process duration, and Workflow volume
uuid: ba3a1809-270e-4c94-ade4-d2f6af86d860
content-type: reference
topic-tags: process-reporting
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 6320c632-c7ec-4e56-9d12-cd27e3e9306e
exl-id: 21f5fb7e-53b3-485d-9b6a-813182f14781
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '698'
ht-degree: 0%

---

# Vordefinierte Berichte in Prozessberichten {#pre-defined-reports-in-process-reporting}

AEM Forms Process Reporting wird mit folgenden Komponenten bereitgestellt: *vorkonfiguriert* Berichte:

* **[Lange laufende Prozesse](/help/forms/using/process-reporting/pre-defined-reports-in-process-reporting.md#p-long-running-processes-p)**: Ein Bericht über alle AEM Forms-Prozesse, deren Abschluss länger als eine bestimmte Zeit dauerte

* **[Diagramm zur Prozessdauer](/help/forms/using/process-reporting/pre-defined-reports-in-process-reporting.md#p-process-duration-report-br-p)**: Ein Bericht eines bestimmten AEM Forms-Prozesses nach Dauer

* **[Workflow-Volumen](/help/forms/using/process-reporting/pre-defined-reports-in-process-reporting.md#p-workflow-volume-report-p)**: Ein Bericht der ausgeführten und abgeschlossenen Instanzen des angegebenen Prozesses nach Datum

## Lange laufende Prozesse {#long-running-processes}

Der Bericht &quot;Lange laufende Prozesse&quot;zeigt die AEM Forms-Prozesse an, deren Abschluss länger als eine bestimmte Zeit in Anspruch genommen hat.

### So führen Sie einen Bericht zu einem langwierigen Prozess aus {#to-execute-a-long-running-process-report-br}

1. Um die Liste der vordefinierten Berichte in der Prozessberichterstellung anzuzeigen, klicken Sie auf **Prozessberichterstellung** Baumansicht, klicken Sie auf die **Berichte** Knoten.
1. Klicken Sie auf **Lange laufende Prozesse** Berichtsknoten.

   ![long_running_node](assets/long_running_node.png)

   Wenn Sie einen Bericht auswählen, wird die **Berichtsparameter** wird rechts neben der Baumansicht angezeigt.

   ![Berichtsparameter für langlaufende Prozesse](assets/report_parameters_panel.png)

   Parameter:

   * **Dauer**(*mandatory*): Geben Sie eine Dauer und eine Zeiteinheit an. Zeigt alle AEM Forms-Prozesse an, die länger als die angegebene Dauer ausgeführt wurden.
   * **Started After** (*optional*): Wählen Sie ein Datum aus. Filtern Sie den Bericht, um Prozessinstanzen anzuzeigen, die nach dem angegebenen Datum gestartet wurden.
   * **Started Before** (*optional*): Wählen Sie ein Datum aus. Filtern Sie den Bericht, um Prozessinstanzen anzuzeigen, die vor dem angegebenen Datum gestartet wurden.

1. Klicken **Los** , um den Bericht auszuführen.

   Der Bericht wird im **Bericht** -Bedienfeld rechts neben dem **Prozessberichterstellung** Fenster.

   ![long_running_processes](assets/long_running_processes.png)

   Verwenden Sie die Optionen oben rechts im **Bericht** -Bedienfeld, um die folgenden Vorgänge für den Bericht auszuführen.

   * **Aktualisieren**: Aktualisiert den Bericht mit den neuesten Daten im Speicher
   * **Farbe der Legende ändern**: Auswählen und Ändern der Farbe der Berichtslegende
   * **Exportieren in CSV**: Daten aus dem Bericht exportieren und in eine kommagetrennte Datei herunterladen

## Bericht zur Prozessdauer {#process-duration-report-br}

Der Bericht &quot;Prozessdauer&quot;zeigt die Anzahl der Instanzen eines Forms-Prozesses nach Anzahl der Tage an, die jede Instanz ausgeführt wurde.

### So führen Sie einen Bericht zur Prozessdauer aus {#to-execute-a-process-duration-report-br}

1. So zeigen Sie die vordefinierten Berichte in der Prozessberichterstellung im **Prozessberichterstellung** Baumansicht, klicken Sie auf die **Berichte** Knoten.
1. Klicken Sie auf **Verarbeitungsdauer** Berichtsknoten.

   ![process_duration_node](assets/process_duration_node.png)

   Wenn Sie einen Bericht auswählen, wird die **Berichtsparameter** wird rechts neben der Baumansicht angezeigt.

   ![Berichtsparameter für langlaufende Prozesse](assets/process_duration_params.png)

   Parameter:

   * **Prozess auswählen** (*mandatory*): Wählen Sie einen AEM Forms-Prozess aus.

1. Klicken **Los** , um den Bericht auszuführen.

   Der Bericht wird im **Bericht** auf der rechten Seite des Fensters &quot;Process Reporting&quot;.

   ![process_duration_report](assets/process_duration_report.png)

   Verwenden Sie die Optionen oben rechts im **Bericht** -Bedienfeld, um die folgenden Vorgänge für den Bericht auszuführen.

   * **Aktualisieren**: Aktualisiert den Bericht mit den neuesten Daten im Speicher
   * **Farbe der Legende ändern**: Auswählen und Ändern der Farbe der Berichtslegende
   * **Exportieren in CSV**: Daten aus dem Bericht exportieren und in eine kommagetrennte Datei herunterladen

## Workflow-Volumenbericht {#workflow-volume-report}

Der Bericht &quot;Workflow-Volumen&quot;zeigt die Anzahl der derzeit ausgeführten und abgeschlossenen Instanzen eines AEM Forms-Prozesses nach Kalendertagen an.

### So führen Sie einen Workflow-Volumenbericht aus {#to-execute-a-workflow-volume-report-br}

1. So zeigen Sie die vordefinierten Berichte in der Prozessberichterstellung im **Prozessberichterstellung** Baumansicht, klicken Sie auf die **Berichte** Knoten.
1. Klicken Sie auf **Workflow-Volumen** Berichtsknoten.

   ![workflow_volumen_node](assets/workflow_volume_node.png)

   Wenn Sie einen Bericht auswählen, wird die **Berichtsparameter** wird rechts neben der Baumansicht angezeigt.

   ![Berichtsparameter für langlaufende Prozesse](assets/workflow_volume_params.png)

   Parameter:

   * **Prozess auswählen**(*mandatory*): Wählen Sie einen AEM Forms-Prozess aus.
   * **Started After** (*optional*): Wählen Sie ein Datum aus. Filtert den Bericht, um Prozessinstanzen anzuzeigen, die nach dem angegebenen Datum gestartet wurden.
   * **Started Before** (*optional*): Wählen Sie ein Datum aus. Filtert den Bericht, um Prozessinstanzen anzuzeigen, die vor dem angegebenen Datum gestartet wurden.

1. Klicken **Los** , um den Bericht auszuführen.

   Der Bericht wird im **Bericht** -Bedienfeld rechts neben dem **Prozessberichterstellung** Fenster.

   ![workflow_volumen_report](assets/workflow_volume_report.png)

   Verwenden Sie die Optionen oben rechts im **Bericht** -Bedienfeld, um die folgenden Vorgänge für den Bericht auszuführen.

   * **Aktualisieren**: Aktualisiert den Bericht mit den neuesten Daten im Speicher
   * **Farbe der Legende ändern**: Auswählen und Ändern der Farbe der Berichtslegende
   * **Exportieren in CSV**: Daten aus dem Bericht exportieren und in eine kommagetrennte Datei herunterladen
