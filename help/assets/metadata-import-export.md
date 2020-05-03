---
title: Massenimport und -export von Metadaten
description: Dieser Artikel beschreibt, wie Sie Metadaten in Batches importieren und exportieren können.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 254a9dec248255f8f76db3531c65b54fb4ebff0c

---


# Bulk metadata import and export {#bulk-metadata-import-and-export}

Mit AEM Assets können Sie Asset-Metadaten mithilfe einer CSV-Datei in Massen importieren. Sie können für die kürzlich hochgeladenen Assets oder die vorhandenen Assets eine Massenaktualisierung durchführen, indem Sie eine CSV-Datei importieren. Außerdem können Sie Asset-Metadaten von Drittanbietersystemen mithilfe des CSV-Formats in Batches aufnehmen.

## Importieren von Metadaten   {#import-metadata}

Der Metadatenimport ist asynchron und beeinträchtigt nicht die Systemleistung. Die gleichzeitige Aktualisierung der Metadaten für mehrere Assets kann aufgrund der XMP-Writeback-Aktivität ressourcenintensiv sein, wenn das Flag für die Arbeitsabläufe gesetzt ist. Planen Sie einen solchen Import während der schlanken Servernutzung, um Leistungseinbußen für andere Benutzer zu vermeiden.

>[!NOTE]
>
>Um Metadaten in benutzerdefinierte Namespaces zu importieren, registrieren Sie zunächst die Namespaces.

Gehen Sie wie folgt vor, um Metadaten stapelweise zu importieren:

1. Navigieren Sie zur Benutzeroberfläche „Assets“ und tippen/klicken Sie in der Symbolleiste auf **[!UICONTROL Erstellen]**.
1. Wählen Sie aus dem Menü **[!UICONTROL Metadaten]** aus.
1. On the **[!UICONTROL Metadata Import]** page, tap/click the **[!UICONTROL Select File]**.  Wählen Sie die CSV-Datei mit den Metadaten aus.
1. Stellen Sie sicher, dass die CSV-Datei die folgenden Parameter enthält:

   | Metadaten-Importparameter | Beschreibung |
   |:---|:---|
   | [!UICONTROL Batch-Größe] | Anzahl der Assets in einem Batch, für die Metadaten importiert werden sollen. Der Standardwert ist 50. Der Wert darf maximal 100 betragen. |
   | [!UICONTROL Feldtrennzeichen] | Default value is `,` – a comma. Sie können jedoch ein beliebiges anderes Zeichen eingeben. |
   | [!UICONTROL Mehrfachtrennzeichen] | Trennzeichen für Metadatenwerte. Default value is `|` – a pipe. |
   | [!UICONTROL Workflows starten] | Lautet standardmäßig „False“. When set to true and default Launcher settings are in effect for the `DAM Metadata WriteBack Workflow` (that writes metadata to the binary XMP data). Die Aktivierung der Workflows hat Auswirkungen auf die Leistung des Systems. |
   | [!UICONTROL Asset-Pfad-Spaltenname] | Definiert den Namen der Spalte in der CSV-Datei, die die Assets enthält. |

1. Tippen oder klicken Sie in der Symbolleiste auf **[!UICONTROL Importieren]**. Nachdem die Metadaten importiert wurden, wird eine Benachrichtigung an Ihren Benachrichtigungs-Posteingang gesendet. Navigieren Sie zur Asset-Eigenschaftsseite und überprüfen Sie, ob die Metadatenwerte richtig in die entsprechenden Assets importiert wurden.

Um beim Importieren von Metadaten Datum und Zeitstempel hinzuzufügen, verwenden Sie das `YYYY-MM-DDThh:mm:ss.fff-00:00` Format für Datum und Uhrzeit. Datum und Uhrzeit werden durch `T`, `hh` Stunden im 24-Stunden-Format, `fff` Nanosekunden und Zeitzonenversatz getrennt `-00:00` angegeben. Zum Beispiel `2020-03-26T11:26:00.000-07:00` ist der 26. März 2020 um 11:26:00 Uhr PST-Zeit.

>[!CAUTION]
>
>Stimmt das Datumsformat nicht überein, `YYYY-MM-DDThh:mm:ss.fff-00:00`werden die Datumswerte nicht eingestellt. Die Datumsformate der exportierten Metadaten-CSV-Datei haben das Format `YYYY-MM-DDThh:mm:ss-00:00`. Wenn Sie es importieren möchten, konvertieren Sie es in das akzeptable Format, indem Sie den von `fff`Ihnen angegebenen Nanosekunden-Wert hinzufügen.

## Exportieren von Metadaten {#export-metadata}

Einige Anwendungsfälle für den Massenexport von Metadaten:

* Importieren Sie die Metadaten in ein Drittanbietersystem, wenn Sie Assets migrieren.
* Geben Sie Asset-Metadaten für ein breiteres Projektteam frei.
* Testen oder prüfen Sie die Metadaten auf Ihre Konformität.
* Externalisieren Sie die Metadaten für eine separate Lokalisierung.

Sie können Metadaten für mehrere Assets in ein CSV-Format exportieren. Die Metadaten werden asynchron exportiert, sodass der Export die Systemleistung nicht beeinträchtigt. Wenn Sie Metadaten exportieren, durchsucht AEM die Eigenschaften des Asset-Knotens `jcr:content/metadata` und der untergeordneten Knoten und exportiert die Metadateneigenschaften in eine CSV-Datei.

Gehen Sie wie folgt vor, um Metadaten mehrerer Assets stapelweise zu exportieren:

1. Wählen Sie einen Asset-Ordner aus, der Assets enthält, für die Sie Metadaten exportieren möchten. Wählen Sie in der Symbolleiste **[!UICONTROL Metadaten exportieren]** aus.

1. In the [!UICONTROL Metadata Export] dialog, specify a name for the CSV file. Um Metadaten von Assets in Unterordnern zu exportieren, wählen Sie **[!UICONTROL Assets in Unterordnern einschließen]**.

   ![export_metadata_page](assets/export_metadata_page.png)

1. Wählen Sie die gewünschten Optionen aus. Geben Sie einen Dateinamen und ggf. ein Datum an.
1. In the **[!UICONTROL Properties to be exported]**, specify whether you want to export all or specific properties. If you choose **[!UICONTROL Selective]** properties to be exported, add the desired properties.

1. Tippen oder klicken Sie in der Symbolleiste auf **[!UICONTROL Exportieren]**. Sie erhalten eine Meldung, die bestätigt, dass die Metadaten exportiert wurden. Schließen Sie die Meldung.

1. Öffnen Sie die Posteingangsbenachrichtigung für den Exportauftrag. Wählen Sie den Auftrag aus und klicken Sie in der Symbolleiste auf **[!UICONTROL Öffnen]**. Um die CSV-Datei mit den Metadaten herunterzuladen, tippen/klicken Sie in der Symbolleiste auf **[!UICONTROL CSV-Download]**. Klicken Sie auf **[!UICONTROL Schließen]**.

   ![csv_download](assets/csv_download.png)
