---
title: Vordefinierte Berichte in Process Reporting
seo-title: Vordefinierte Berichte in Process Reporting
description: Abfrage von AEM Forms on JEE-Prozessdaten zum Erstellen von Berichten über Prozesse mit langer Laufzeit, Prozessdauer und Workflow-Volumen
seo-description: Abfrage von AEM Forms on JEE-Prozessdaten zum Erstellen von Berichten über Prozesse mit langer Laufzeit, Prozessdauer und Workflow-Volumen
uuid: ba3a1809-270e-4c94-ade4-d2f6af86d860
content-type: reference
topic-tags: process-reporting
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 6320c632-c7ec-4e56-9d12-cd27e3e9306e
translation-type: tm+mt
source-git-commit: ec74a1c3b1d3686a1f5216e06dfc33dc1dccfb2f

---


# Vordefinierte Berichte in Process Reporting {#pre-defined-reports-in-process-reporting}

Die AEM Forms Process Reporting enthält die folgenden *vordefinierten* Berichte:

* **[Lange laufende Prozesse](/help/forms/using/process-reporting/pre-defined-reports-in-process-reporting.md#p-long-running-processes-p)**: Ein Bericht zu allen AEM Forms-Prozessen, deren Abschluss mehr als eine bestimmte Zeit dauerte

* **[Prozessdauer-Diagramm](/help/forms/using/process-reporting/pre-defined-reports-in-process-reporting.md#p-process-duration-report-br-p)**: Ein Bericht eines angegebenen AEM Forms-Prozesses nach Dauer

* **[Arbeitsablaufvolumen](/help/forms/using/process-reporting/pre-defined-reports-in-process-reporting.md#p-workflow-volume-report-p)**: Ein Bericht der ausgeführten und abgeschlossenen Instanzen des angegebenen Prozesses nach Datum

## Lange laufende Prozesse {#long-running-processes}

Der Bericht &quot;Dauerhaft ausgeführte Prozesse&quot;zeigt die AEM Forms-Prozesse an, deren Abschluss mehr als eine bestimmte Zeit in Anspruch genommen hat.

### So führen Sie einen Bericht über einen langwierigen Prozess aus {#to-execute-a-long-running-process-report-br}

1. Um die Liste der vordefinierten Berichte in der Prozessberichterstellung anzuzeigen, klicken Sie in der Strukturansicht der **Prozessberichterstellung** auf den Knoten **Berichte** .
1. Klicken Sie auf die Berichtsknoten **für langfristige** Prozesse.

   ![long_running_node](assets/long_running_node.png)

   Wenn Sie einen Bericht auswählen, wird das Bedienfeld &quot; **Berichtsparameter** &quot;rechts neben der Baumansicht angezeigt.

   ![Berichtsparameter für lange Prozesse](assets/report_parameters_panel.png)

   Parameter:

   * **Dauer**(*obligatorisch*): Geben Sie eine Dauer und eine Zeiteinheit an. Zeigt alle AEM Forms-Prozesse an, die länger als die angegebene Dauer ausgeführt wurden.
   * **Gestartet nach** (*optional*): Wählen Sie ein Datum aus. Filtern Sie den Bericht, um Prozessinstanzen anzuzeigen, die nach dem angegebenen Datum gestartet wurden.
   * **Vorher** gestartet (*optional*): Wählen Sie ein Datum aus. Filtern Sie den Bericht, um Prozessinstanzen anzuzeigen, die vor dem angegebenen Datum gestartet wurden.

1. Klicken Sie auf **Los** , um den Bericht auszuführen.

   Der Bericht wird im Bereich **Bericht **rechts neben dem Fenster **Prozessberichterstellung** angezeigt.

   ![long_running_processes](assets/long_running_processes.png)

   Verwenden Sie die Optionen in der oberen rechten Ecke des Bereichs **Bericht **s, um die folgenden Vorgänge für den Bericht auszuführen.

   * **Aktualisieren**: Aktualisiert den Bericht mit den neuesten Daten im Speicher
   * **Legendenfarbe**&#x200B;ändern: Auswählen und Ändern der Farbe der Berichtslegende
   * **In CSV** exportieren: Daten aus dem Bericht exportieren und in eine kommagetrennte Datei herunterladen

## Prozessdauerbericht {#process-duration-report-br}

Der Bericht &quot;Prozessdauer&quot;zeigt die Anzahl der Instanzen eines Formularprozesses nach Anzahl der Tage an, die jede Instanz ausgeführt hat.

### So führen Sie einen Bericht zur Prozessdauer aus {#to-execute-a-process-duration-report-br}

1. Um die vordefinierten Berichte in der Prozessberichterstellung anzuzeigen, klicken Sie in der Strukturansicht der **Prozessberichterstellung** auf den Knoten **Berichte** .
1. Klicken Sie auf den Berichtsknoten **Prozessdauer** .

   ![process_duration_node](assets/process_duration_node.png)

   Wenn Sie einen Bericht auswählen, wird das Bedienfeld &quot; **Berichtsparameter** &quot;rechts neben der Baumansicht angezeigt.

   ![Berichtsparameter für lange Prozesse](assets/process_duration_params.png)

   Parameter:

   * **Wählen Sie Process** (*mandatory*): Wählen Sie einen AEM Forms-Prozess.

1. Klicken Sie auf **Los** , um den Bericht auszuführen.

   Der Bericht wird im Bereich &quot; **Bericht** &quot;rechts neben dem Fenster &quot;Prozessberichterstellung&quot;angezeigt.

   ![process_duration_report](assets/process_duration_report.png)

   Verwenden Sie die Optionen in der oberen rechten Ecke des **Berichtbedienfelds** , um die folgenden Vorgänge für den Bericht auszuführen.

   * **Aktualisieren**: Aktualisiert den Bericht mit den neuesten Daten im Speicher
   * **Legendenfarbe**&#x200B;ändern: Auswählen und Ändern der Farbe der Berichtslegende
   * **In CSV** exportieren: Daten aus dem Bericht exportieren und in eine kommagetrennte Datei herunterladen

## Workflow-Volumenbericht {#workflow-volume-report}

Der Bericht &quot;Workflow-Volumen&quot;zeigt die Anzahl der derzeit ausgeführten und abgeschlossenen Instanzen eines AEM Forms-Prozesses nach Kalendertag an.

### So führen Sie einen Workflow-Volumenbericht aus {#to-execute-a-workflow-volume-report-br}

1. Um die vordefinierten Berichte in der Prozessberichterstellung anzuzeigen, klicken Sie in der Strukturansicht der **Prozessberichterstellung** auf den Knoten **Berichte** .
1. Klicken Sie auf den Berichtsknoten **Workflow-Volumen** .

   ![workflow_volume_node](assets/workflow_volume_node.png)

   Wenn Sie einen Bericht auswählen, wird das Bedienfeld &quot; **Berichtsparameter** &quot;rechts neben der Baumansicht angezeigt.

   ![Berichtsparameter für lange Prozesse](assets/workflow_volume_params.png)

   Parameter:

   * **Prozess** auswählen (*obligatorisch*): Wählen Sie einen AEM Forms-Prozess.
   * **Gestartet nach** (*optional*): Wählen Sie ein Datum aus. Filtert den Bericht, um Prozessinstanzen anzuzeigen, die nach dem angegebenen Datum gestartet wurden.
   * **Vorher** gestartet (*optional*): Wählen Sie ein Datum aus. Filtert den Bericht, um Prozessinstanzen anzuzeigen, die vor dem angegebenen Datum gestartet wurden.

1. Klicken Sie auf **Los** , um den Bericht auszuführen.

   Der Bericht wird im Bereich **Bericht** rechts neben dem Fenster **Prozessberichterstellung** angezeigt.

   ![workflow_volume_report](assets/workflow_volume_report.png)

   Verwenden Sie die Optionen in der oberen rechten Ecke des **Berichtbedienfelds** , um die folgenden Vorgänge für den Bericht auszuführen.

   * **Aktualisieren**: Aktualisiert den Bericht mit den neuesten Daten im Speicher
   * **Legendenfarbe**&#x200B;ändern: Auswählen und Ändern der Farbe der Berichtslegende
   * **In CSV** exportieren: Daten aus dem Bericht exportieren und in eine kommagetrennte Datei herunterladen

[Support kontaktieren](https://www.adobe.com/account/sign-in.supportportal.html)
