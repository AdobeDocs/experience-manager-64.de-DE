---
title: Best Practices für effizientes Übersetzen von Assets
description: Best Practices für die effiziente Verwaltung von Assets zur Synchronisation verschiedener übersetzter Versionen und zur Optimierung von Übersetzungs-Workflows.
contentOwner: AG
feature: Translation
role: User,Admin
exl-id: 15162b80-ddef-4ec0-9db6-36695c93ebb1
source-git-commit: de5632ff0ee87a4ded88e792b57e818baf4c01a3
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 89%

---

# Best Practices zur effizienten Übersetzung von Assets {#best-practices-for-translating-assets-efficiently}

Adobe Experience Manager Assets unterstützt mehrsprachige Workflows zum Übersetzen von Binärdateien, Metadaten und Tags für digitale Assets in mehrere Gebietsschemata und zum Verwalten der übersetzten Assets. Details finden Sie unter [Mehrsprachige Assets](multilingual-assets.md).

Um die Assets effizient zu verwalten und sicherzustellen, dass verschiedene übersetzte Versionen synchronisiert bleiben, erstellen Sie [Sprachkopien](preparing-assets-for-translation.md) der Assets, bevor Sie die Übersetzungsworkflows ausführen.

Die Sprachkopie eines Assets oder einer Gruppe von Assets ist ein gleichgeordnetes Sprachenelement (oder eine Version der oder des Assets in einer verwandten Sprache) mit einer ähnlichen Inhaltshierarchie.

Jede Sprachkopie ist ein unabhängiges Asset. Daher kann durch das Übertragen von Assets in mehrere Gebietsschemas die Größe des CRX-Repository deutlich zunehmen. Beispielsweise kann sich durch das Übersetzen von Assets mit einer Größe von insgesamt 10 GB in zwei Sprachen die Repositorygröße auf ca. 20 GB (10 GB für jede Sprache) erhöhen.

Asset-Binärdateien belegen im Vergleich zu Metadaten und Tags deutlich mehr Speicherplatz. Wenn das Übersetzen von Metadaten und Tags für Ihre Zwecke ausreicht, sollten Sie daher auf das Übersetzen der Binärdateien verzichten. Sie können die Originalkopie der Binärdateien im Repository zur Verknüpfung mit in verschiedene Gebietsschemas übertragenen Metadaten und Tags aufbewahren. Wenn Sie lediglich eine Einzelkopie statt mehrerer übersetzter Versionen beibehalten, wird hierdurch die Auswirkung auf die Repositorygröße minimiert.

Dateidatenspeicher und Amazon S3-Datenspeicher bieten eine Speicherinfrastruktur, die für diese Szenarien am besten geeignet ist. Diese Speicherrepositorys speichern eine Einzelkopie der Asset-Binärdateien (einschließlich Wiedergaben), die gemeinsam von Metadaten und Tags in mehreren Gebietsschemas genutzt werden kann. Daher wird die Repositorygröße nicht durch das Erstellen von Asset-Sprachkopien und Übersetzen von Metadaten und Tags beeinflusst.

Mittels gewisser Änderungen an Workflows und am Framework für die Übersetzungsintegration können Sie den Prozess weiter optimieren.

1. Führen Sie einen der folgenden Schritte aus:

   * [Richten Sie einen Dateidatenspeicher ein.](/help/sites-deploying/data-store-config.md)
   * [Richten Sie einen Amazon S3-Datenspeicher ein.](/help/sites-deploying/data-store-config.md)

1. Deaktivieren Sie den Workflow [DAM-Metadaten-Writeback](/help/sites-administering/workflow-offloader.md#disable-offloading).

   Wie der Name schon sagt, werden Metadaten im Rahmen des Workflows *DAM-Metadaten-Writeback* erneut in die Binärdatei geschrieben. Das sich die Metadaten nach der Übersetzung verändern, wird durch das Zurückschreiben dieser Metadaten in die Binärdatei eine andere Binärdatei für eine Sprachkopie generiert.

   >[!NOTE]
   >
   >Wird der Workflow *DAM-Metadaten-Writeback* deaktiviert, wird der XMP-Metadaten-Writeback-Prozess für Asset-Binärdateien ausgeschaltet. In der Folge werden zukünftige Metadatenänderungen nicht mehr innerhalb der Assets gespeichert. Schätzen Sie die Auswirkungen ein, bevor Sie diesen Workflow deaktivieren.

1. Aktivieren Sie den Workflow *Letztes Änderungsdatum des Sets*.

   Mit dem Workflow *DAM-Metadaten-Writeback* wird das Datum der letzten Änderung eines Assets konfiguriert. Da Sie diesen Workflow in Schritt 2 deaktivieren, [!DNL Experience Manager Assets] kann das Datum der letzten Änderung von Assets nicht mehr auf dem neuesten Stand halten. Aktivieren Sie daher den Workflow *Letztes Änderungsdatum des Sets*, um sicherzustellen, dass die Datumsangaben für die letzten Asset-Änderungen aktuell sind. Assets mit veralteten Datumsangaben für letzte Änderungen können Fehler verursachen.

1. [Konfigurieren Sie das Framework für die Übersetzungsintegration](/help/sites-administering/tc-tic.md), damit Asset-Binärdateien nicht mehr übersetzt werden. Deaktivieren Sie auf der Registerkarte „Assets“ die Option „Assets übersetzen“, um eine Übersetzung von Asset-Binärdateien auszuschließen. 
1. Übersetzen Sie Asset-Metadaten/-Tags mithilfe [mehrsprachiger Asset-Workflows](multilingual-assets.md).
