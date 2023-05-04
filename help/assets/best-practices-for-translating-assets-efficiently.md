---
title: Best Practices für die effiziente Übersetzung von Assets
description: Best Practices für die effiziente Verwaltung von Assets zur Synchronisation verschiedener übersetzter Versionen und zur Optimierung von Übersetzungs-Workflows.
contentOwner: AG
feature: Translation
role: User,Admin
exl-id: 15162b80-ddef-4ec0-9db6-36695c93ebb1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 24%

---

# Best Practices für das Übersetzen von Assets effizient {#best-practices-for-translating-assets-efficiently}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Adobe Experience Manager Assets unterstützt mehrsprachige Workflows zum Übersetzen von Binärdateien, Metadaten und Tags für digitale Assets in mehrere Gebietsschemata und zum Verwalten der übersetzten Assets. Details finden Sie unter [Mehrsprachige Assets](multilingual-assets.md).

Erstellen Sie für eine effiziente Verwaltung von Assets, um sicherzustellen, dass verschiedene übersetzte Versionen synchronisiert bleiben. [Sprachkopien](preparing-assets-for-translation.md) Assets vor dem Ausführen von Übersetzungs-Workflows.

Eine Sprachkopie eines Assets oder einer Gruppe von Assets ist ein gleichrangiges Sprachenlernen (oder eine Version der Assets in einer Fremdsprache) mit einer ähnlichen Inhaltshierarchie.

Jede Sprachkopie ist ein unabhängiges Asset. Daher kann durch das Übertragen von Assets in mehrere Gebietsschemata die Größe des CRX-Repository deutlich zunehmen. Wenn Sie beispielsweise Assets mit einer kombinierten Größe von 10 GB in zwei Sprachen übersetzen, kann die Repository-Größe um etwa 20 GB (10 GB für jede Sprache) erhöht werden.

Asset-Binärdateien belegen im Vergleich zu Metadaten und Tags deutlich mehr Speicherplatz. Wenn die Übersetzung von Metadaten und Tags nur Ihrem Zweck dient, lassen Sie die Übersetzung der Binärdateien weg. Sie können die Originalkopie der Binärdateien im Repository zur Verknüpfung mit in verschiedene Gebietsschemata übertragenen Metadaten und Tags aufbewahren. Durch die Pflege einer einzigen Kopie von Binärdateien anstelle mehrerer übersetzter Versionen werden die Auswirkungen auf die Repository-Größe minimiert.

Dateidatenspeicher und Amazon S3-Datenspeicher bieten eine Speicherinfrastruktur, die für diese Szenarien am besten geeignet ist. Diese Speicherrepositorys speichern eine Einzelkopie der Asset-Binärdateien (einschließlich Wiedergaben), die gemeinsam von Metadaten und Tags in mehreren Gebietsschemata genutzt werden kann. Daher wirkt sich das Erstellen von Asset-Sprachkopien und das Übersetzen von Metadaten und Tags nicht auf die Repository-Größe aus.

Sie können auch einige Konfigurationsänderungen an einigen Workflows und dem Framework für die Übersetzungsintegration vornehmen, um den Prozess weiter zu optimieren.

1. Führen Sie einen der folgenden Schritte aus:

   * [Richten Sie einen Dateidatenspeicher ein.](/help/sites-deploying/data-store-config.md)
   * [Richten Sie einen Amazon S3-Datenspeicher ein.](/help/sites-deploying/data-store-config.md)

1. Deaktivieren Sie die [DAM MetaData Writeback](/help/sites-administering/workflow-offloader.md#disable-offloading) Workflow

   Wie der Name schon sagt, wird die *DAM-Metadaten-Writeback* Workflow schreibt die Metadaten in die Binärdatei um. Da sich die Metadaten nach der Übersetzung ändern, wird beim Zurückschreiben in die Binärdatei eine andere Binärdatei für eine Sprachkopie generiert.

   >[!NOTE]
   >
   >Deaktivieren der *DAM MetaData Writeback* Workflow deaktiviert XMP Zurückschreiben von Metadaten in Asset-Binärdateien. Folglich werden zukünftige Metadatenänderungen nicht mehr in den Assets gespeichert. Bewerten Sie die Folgen, bevor Sie diesen Workflow deaktivieren.

1. Aktivieren Sie die *Datum der letzten Änderung festlegen* Arbeitsablauf.

   Die *DAM MetaData Writeback* Der Workflow konfiguriert das Datum der letzten Änderung für ein Asset. Da dieser Workflow in Schritt 2 deaktiviert wird, kann [!DNL Experience Manager Assets] das Datum der letzten Asset-Änderung nicht länger auf dem neuesten Stand halten. Aktivieren Sie daher die *Datum der letzten Änderung festlegen* Arbeitsablauf, um sicherzustellen, dass die letzten geänderten Daten der Assets aktuell sind. Assets mit veralteten Datumsangaben der letzten Änderung können Fehler verursachen.

1. [Konfigurieren des Framework für die Übersetzungsintegration](/help/sites-administering/tc-tic.md) , um die Übersetzung von Asset-Binärdateien zu beenden. Deaktivieren Sie die Option &quot;Assets übersetzen&quot;auf der Registerkarte &quot;Assets&quot;, um die Übersetzung von Asset-Binärdateien zu stoppen.
1. Übersetzen von Asset-Metadaten/Tags mithilfe von [Mehrsprachige Asset-Workflows](multilingual-assets.md).
