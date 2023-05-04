---
title: Migrieren von Assets in Adobe Experience Manager Assets in großen Mengen
description: So bringen Sie Assets in AEM, wenden Metadaten an, generieren Ausgabedarstellungen und aktivieren sie für Veröffentlichungsinstanzen.
contentOwner: AG
feature: Migration,Renditions,Asset Management
role: Architect,Admin
exl-id: 31da9f3d-460a-4b71-9ba0-7487f1b159cb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1808'
ht-degree: 29%

---

# Handbuch zur Assets-Migration {#assets-migration-guide}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Bei der Migration von Assets in AEM sind mehrere Schritte zu beachten. Das Extrahieren von Assets und Metadaten aus ihrer aktuellen Startseite fällt nicht in den Geltungsbereich dieses Dokuments, da es bei den Implementierungen sehr unterschiedlich ist. Stattdessen wird in diesem Dokument beschrieben, wie Sie diese Assets in AEM einbinden, ihre Metadaten anwenden, Ausgabedarstellungen generieren und die Assets aktivieren oder veröffentlichen.

## Voraussetzungen {#prerequisites}

Bevor Sie einen der unten beschriebenen Schritte durchführen, lesen und implementieren Sie die Anleitungen unter [Tipps zur Leistungsoptimierung von Assets](performance-tuning-guidelines.md). Viele Schritte wie die Konfiguration der maximalen Anzahl gleichzeitiger Aufträge verbessern die Stabilität und Leistung des Servers unter Last. Andere Schritte, wie die Konfiguration des Dateidatenspeichers, sind nach dem Laden des Systems mit Assets schwierig durchzuführen.

>[!NOTE]
>
>Die folgenden Tools zur Asset-Migration sind nicht Teil von Adobe Experience Manager. Der Adobe-Support unterstützt diese Tools nicht.
>
>* ACS [!DNL Experience Manager] Tools-Tag-Maker
>* ACS [!DNL Experience Manager] Tools CSV Asset Importer
>* Bulk Workflow Manager von ACS Commons
>* ACS Commons Fast Action Manager
>* Synthetischer Workflow
>
>Hierbei handelt es sich um eine Open-Source-Software. Sie wird mit der [Apache v2-Lizenz](https://adobe-consulting-services.github.io/pages/license.html) abgedeckt. Um eine Frage zu stellen oder ein Problem zu melden, besuchen Sie die [GitHub-Probleme für ACS [!DNL Experience Manager] Instrumente](https://github.com/Adobe-Consulting-Services/acs-aem-commons/issues) und [ACS [!DNL Experience Manager] Commons](https://github.com/Adobe-Consulting-Services/acs-aem-tools/issues).

## Migrieren nach [!DNL Experience Manager] {#migrate-to-aem}

Die Migration von Assets nach [!DNL Experience Manager] erfolgt in mehreren Schritten und sollte als stufenweises Verfahren angesehen werden. Die Migrationsphasen lauten wie folgt:

1. Deaktivieren von Workflows.
1. Laden von Tags.
1. Aufnehmen von Assets.
1. Verarbeiten von Ausgabedarstellungen.
1. Aktivieren von Assets.
1. Aktivieren von Workflows.

![chlimage_1-223](assets/chlimage_1-223.png)

### Deaktivieren von Workflows {#disable-workflows}

Deaktivieren Sie vor Beginn einer Migration die Starter für die `DAM Update Asset` Arbeitsablauf. Am besten nehmen Sie alle Assets in das System auf und führen dann die Workflows in Batches aus. Wenn Sie bereits aktiv sind, während die Migration stattfindet, können Sie diese Aktivitäten so planen, dass sie außerhalb der Arbeitszeiten ausgeführt werden.

### Laden von Tags {#load-tags}

Womöglich verfügen Sie bereits über eine Tag-Taxonomie für Ihre Bilder. Tools wie der CSV Asset Importer und die Metadatenprofilfunktionalität können dabei helfen, die Anwendung von Tags auf Assets zu automatisieren. Fügen Sie vor diesem die Tags in Experience Manager hinzu. Die [ACS [!DNL Experience Manager] Tools-Tag-Maker](https://adobe-consulting-services.github.io/acs-aem-tools/features/tag-maker/index.html) können Sie Tags mithilfe einer in das System geladenen Microsoft Excel-Tabelle ausfüllen.

### Aufnehmen von Assets {#ingest-assets}

Leistung und Stabilität sind bei der Aufnahme von Assets in das System von großer Bedeutung. Stellen Sie beim Laden einer Vielzahl von Daten in Experience Manager sicher, dass das System gut funktioniert. Dadurch wurde die zum Hinzufügen der Daten erforderliche Zeit minimiert und das System kann nicht überlastet werden. Dies verhindert Systemabstürze, insbesondere bei Systemen, die bereits in Produktion sind.

Es gibt zwei Ansätze zum Laden der Assets in das System: einen Push-basierten Ansatz mit HTTP oder einem Pull-basierten Ansatz unter Verwendung der JCR-APIs.

#### Push über HTTP {#push-through-http}

Das Managed Services-Team von Adobe lädt Daten mit einem Tool namens Glutton in Kundenumgebungen. Glutton ist eine kleine Java-Anwendung, die alle Assets aus einem Ordner in ein anderes Verzeichnis in einem [!DNL Experience Manager] -Instanz. Statt Glutton können Sie auch Tools wie Perl-Skripts zum Posten der Assets in das Repository verwenden.

Der Push-basierte Ansatz mit HTTP hat zwei wesentliche Nachteile:

1. Senden Sie die Assets über HTTP an den Server. Dies erfordert einen gewissen Mehraufwand und ist zeitaufwendig, wodurch die Dauer der Migration verlängert wird.
1. Wenn Sie über Tags und benutzerdefinierte Metadaten verfügen, die auf die Assets angewendet werden müssen, erfordert dieser Ansatz einen zweiten benutzerdefinierten Prozess, den Sie ausführen müssen, um diese Metadaten nach dem Import auf die Assets anzuwenden.

Der andere Ansatz bei der Aufnahme von Assets besteht darin, Assets aus dem lokalen Dateisystem abzurufen. Wenn Sie jedoch kein externes Laufwerk oder keine Netzwerkfreigabe auf den Server bereitstellen können, um einen Pull-basierten Ansatz durchzuführen, ist die Veröffentlichung der Assets über HTTP die beste Option.

#### Abrufen aus dem lokalen Dateisystem {#pull-from-the-local-file-system}

Die [ACS [!DNL Experience Manager] Tools CSV Asset Importer](https://adobe-consulting-services.github.io/acs-aem-tools/features/csv-asset-importer/index.html) Ruft Assets aus dem Dateisystem und Asset-Metadaten aus einer CSV-Datei für den Asset-Import ab. Die [!DNL Experience Manager] Die Asset Manager-API wird verwendet, um die Assets in das System zu importieren und die konfigurierten Metadateneigenschaften anzuwenden. Idealerweise werden Assets über eine Netzwerkdateibereitstellung oder über ein externes Laufwerk auf dem Server bereitgestellt.

Wenn Assets nicht über ein Netzwerk übertragen werden, verbessert sich die Gesamtleistung erheblich. Diese Methode ist normalerweise die effizienteste Methode zum Laden von Assets in das Repository. Darüber hinaus können Sie alle Assets und Metadaten in einem einzigen Schritt importieren, da das Tool die Metadatenerfassung unterstützt. Es ist kein anderer Schritt erforderlich, um die Metadaten anzuwenden, z. B. mit einem separaten Tool.

### Verarbeiten von Ausgabedarstellungen {#process-renditions}

Nachdem Sie die Assets in das System geladen haben, müssen Sie sie über den Workflow DAM-Update-Asset verarbeiten, um Metadaten zu extrahieren und Ausgabedarstellungen zu generieren. Vor diesem Schritt müssen Sie den Workflow DAM-Update-Asset duplizieren und an Ihre Anforderungen anpassen. Einige Schritte im Standard-Workflow sind für Sie möglicherweise nicht erforderlich, z. B. die Dynamic Media Classic-PTIFF-Generierung oder die InDesign-Serverintegration.

Nachdem Sie den Workflow entsprechend Ihren Anforderungen konfiguriert haben, haben Sie zwei Möglichkeiten, ihn auszuführen:

1. Die einfachste Herangehensweise bietet [Bulk Workflow Manager von ACS Commons](https://adobe-consulting-services.github.io/acs-aem-commons/features/bulk-workflow-manager.html). Mit diesem Tool können Sie eine Abfrage ausführen und die Ergebnisse der Abfrage mithilfe eines Workflows verarbeiten. Es gibt auch Optionen zum Festlegen von Stapelgrößen.
1. Sie können [Fast Action Manager von ACS Commons](https://adobe-consulting-services.github.io/acs-aem-commons/features/fast-action-manager.html) zusammen mit [Synthetic Workflows](https://adobe-consulting-services.github.io/acs-aem-commons/features/synthetic-workflow.html) verwenden. Dieser Ansatz erfordert zwar viel mehr Mitwirkung, Sie können jedoch den Verwaltungsaufwand für die [!DNL Experience Manager]-Workflow-Engine verringern und gleichzeitig die Verwendung von Server-Ressourcen optimieren. Darüber hinaus steigert der Fast Action Manager die Leistung durch die dynamische Überwachung der Serverressourcen und die Einschränkung der Systemlast. Beispielskripte wurden auf der Seite mit den ACS Commons-Funktionen bereitgestellt.

### Aktivieren von Assets {#activate-assets}

Bei Bereitstellungen mit einer Veröffentlichungsstufe müssen Sie die Assets in der Veröffentlichungsfarm aktivieren. Adobe empfiehlt zwar, mehr als eine Veröffentlichungsinstanz auszuführen, es ist jedoch am effizientesten, alle Assets in einer Veröffentlichungsinstanz zu replizieren und diese Instanz dann zu klonen. Wenn Sie eine große Anzahl von Assets aktivieren, müssen Sie nach dem Auslösen einer Strukturaktivierung möglicherweise eingreifen. Der Grund: Beim Auslösen von Aktivierungen werden Elemente der Sling-Auftrags-/Even-Warteschlange hinzugefügt. Nachdem die Größe dieser Warteschlange etwa 40.000 Elemente überschreitet, verlangsamt sich die Verarbeitung drastisch. Wenn die Größe dieser Warteschlange 100.000 Elemente überschreitet, leidet die Systemstabilität.

Um dieses Problem zu umgehen, können Sie die [Fast Action Manager](https://adobe-consulting-services.github.io/acs-aem-commons/features/fast-action-manager.html) zur Verwaltung der Asset-Replikation. Dies funktioniert ohne die Sling-Warteschlangen, wodurch der Overhead verringert und gleichzeitig die Arbeitslast reduziert wird, um zu verhindern, dass der Server überlastet wird. Ein Beispiel für die Verwendung von FAM zur Verwaltung der Replikation finden Sie auf der Dokumentationsseite der Funktion.

Zu weiteren Optionen zum Übertragen von Assets in die Veröffentlichungsfarm gehören u. a. [vlt-rcp](https://jackrabbit.apache.org/filevault/rcp.html) und [oak-run](https://github.com/apache/jackrabbit-oak/tree/trunk/oak-run), die als Tools mit Jackrabbit bereitgestellt werden. Eine andere Möglichkeit ist zudem [Grabbit](https://github.com/TWCable/grabbit), ein Open-Source-Tool für Ihre [!DNL Experience Manager]-Infrastruktur, das schneller sein soll als vlt.

Bei jedem dieser Ansätze besteht der Nachteil darin, dass die Assets in der Autoreninstanz nicht als aktiviert angezeigt werden. Um die Kennzeichnung dieser Assets mit dem korrekten Aktivierungsstatus zu verarbeiten, müssen Sie auch ein Skript ausführen, um die Assets als aktiviert zu markieren.

>[!NOTE]
>
>Adobe unterstützt Grabbit nicht.

### Klonen der Veröffentlichungsinstanz {#clone-publish}

Nachdem die Assets aktiviert wurden, können Sie Ihre Veröffentlichungsinstanz klonen, um so viele Kopien zu erstellen, wie für die Bereitstellung erforderlich sind. Das Klonen eines Servers ist relativ einfach, es gibt jedoch einige wichtige Schritte, die Sie sich merken müssen. So klonen Sie die Veröffentlichung:

1. Sichern Sie die Quellinstanz und den Datenspeicher.
1. Stellen Sie die Sicherung der Instanz und des Datenspeichers am Zielspeicherort wieder her. Die folgenden Schritte beziehen sich alle auf diese neue Instanz.
1. Führen Sie eine Dateisystemsuche unter durch. `crx-quickstart/launchpad/felix` für `sling.id`. Löschen Sie diese Datei.
1. Suchen und löschen Sie etwaig vorhandene `repository-XXX`-Dateien im Stammverzeichnis.
1. Bearbeiten Sie `crx-quickstart/install/org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config` und `crx-quickstart/launchpad/config/org/apache/jackrabbit/oak/plugins/blob/datastore/FileDataStore.config`, um auf den Speicherort des Datenspeichers in der neuen Umgebung zu zeigen.
1. Starten Sie die Umgebung.
1. Aktualisieren Sie die Konfiguration von Replikationsagenten auf der/den Autoreninstanz(en), um auf die richtigen Veröffentlichungsinstanzen zu verweisen, oder die Dispatcher-Flush-Agenten auf der neuen Instanz, um auf die richtigen Dispatcher für die neue Umgebung zu verweisen.

### Aktivieren von Workflows {#enable-workflows}

Nach abgeschlossener Migration sollten die Starter für die Workflows „DAM-Update-Asset“ neu aktiviert werden, um die Ausgabegenerierung und Metadatenextraktion für die laufende, tagtägliche Systemnutzung zu unterstützen.

## Migrieren von Assets über [!DNL Experience Manager] Bereitstellungen {#migrate-between-aem-instances}

Obwohl es nicht so häufig vorkommt, müssen Sie manchmal große Datenmengen von einem [!DNL Experience Manager] Instanz an eine andere Instanz; Wenn Sie beispielsweise eine [!DNL Experience Manager] Aktualisierung, Aktualisierung Ihrer Hardware oder Migration zu einem neuen Rechenzentrum, beispielsweise mit einer AMS-Migration.

In diesem Fall sind die Assets schon mit Metadaten aufgefüllt und Ausgabedarstellungen sind bereits generiert. Sie können sich einfach darauf konzentrieren, Assets von einer Instanz in eine andere zu verschieben. Bei der Migration zwischen [!DNL Experience Manager] -Instanzen führen Sie die folgenden Schritte aus:

1. Workflows deaktivieren: Da Sie Ausgabedarstellungen zusammen mit unseren Assets migrieren, möchten Sie die Workflow-Starter für DAM Update Asset deaktivieren.

1. Tags migrieren: Da bereits Tags in der Quelle geladen wurden [!DNL Experience Manager] -Instanz können Sie sie in einem Inhaltspaket erstellen und das Paket auf der Zielinstanz installieren.

1. Migrieren von Assets: Es werden zwei Tools zum Verschieben von Assets von einem [!DNL Experience Manager] Instanz zu einer anderen Instanz:

   * **Vault Remote Copy** oder `vlt rcp`ermöglicht Ihnen die Verwendung von vlt in einem Netzwerk. Nach Angabe eines Quell- und Zielverzeichnisses lädt vlt alle Repository-Daten von einer Instanz herunter und lädt diese in die andere Instanz. Die Dokumentation zum vlt rcp-Tool finden Sie unter [https://jackrabbit.apache.org/filevault/rcp.html](https://jackrabbit.apache.org/filevault/rcp.html)
   * **Grabbit** ist ein Open-Source-Tool zur Inhaltssynchronisierung, das von Time Warner Cable für die eigene [!DNL Experience Manager]-Implementierung entwickelt wurde. Da es kontinuierliche Datenströme verwendet, weist es im Vergleich zu vlt rcp eine geringere Latenz auf und beansprucht eine Geschwindigkeitsverbesserung von zwei- bis zehnmal schneller als vlt rcp. Grabbit unterstützt auch nur die Synchronisierung von Delta-Inhalten, wodurch Änderungen synchronisiert werden können, nachdem ein erster Migrationsdurchgang abgeschlossen wurde.

1. Aktivieren von Assets: Befolgen Sie die Anweisungen für [Aktivieren von Assets](#activate-assets) dokumentiert für die Erstmigration nach AEM.

1. Klonen der Veröffentlichungsinstanz: Wie bei einer neuen Migration ist es effizienter, eine einzelne Veröffentlichungsinstanz zu laden und zu klonen, als Inhalt auf beiden Knoten zu aktivieren. Siehe [Klonen von Veröffentlichungsinstanzen](#clone-publish).

1. Aktivieren von Workflows: Nachdem Sie die Migration abgeschlossen haben, aktivieren Sie die Starter für die DAM Update Asset-Workflows erneut, um die Ausgabegenerierung und Metadatenextraktion für die laufende, tagtägliche Systemnutzung zu unterstützen.
