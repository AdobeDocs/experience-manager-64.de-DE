---
title: Migrieren von Assets zu Adobe Experience Manager-Assets als Massen
description: So können Sie Assets in AEM importieren, Metadaten anwenden, Darstellungen generieren und sie für Veröffentlichungsinstanzen aktivieren.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 976d037d701eb7cc61a62e14e554675961d6179c

---


# Assets migration guide {#assets-migration-guide}

Beim Migrieren von Assets nach AEM sind verschiedene Schritte zu berücksichtigen. Das Extrahieren von Assets und Metadaten aus ihrem aktuellen Stammordner fällt nicht in den Anwendungsbereich dieses Dokuments, da es von Implementierung zu Implementierung sehr unterschiedlich ist. Stattdessen wird in diesem Dokument beschrieben, wie diese Assets in AEM importiert, ihre Metadaten angewendet, Darstellungen generiert und die Assets aktiviert oder veröffentlicht werden.

## Voraussetzungen {#prerequisites}

Before performing any of the steps described below, review and implement the guidance in [Assets performance tuning tips](performance-tuning-guidelines.md). Viele Schritte, z. B. die Konfiguration der maximalen Anzahl gleichzeitiger Aufträge, verbessern die Stabilität und Leistung des Servers unter Belastung. Andere Schritte wie die Konfiguration des Dateispeichers sind nach dem Laden des Systems mit Assets schwierig durchzuführen.

>[!NOTE]
>
>Die folgenden Tools zur Asset-Migration sind nicht Teil von Adobe Experience Manager. Die Adobe-Kundenunterstützung unterstützt diese Tools nicht.
>
>* Tag Maker von ACS AEM-Tools
>* CSV Asset Importer von ACS AEM-Tools
>* Bulk Workflow Manager von ACS Commons
>* Fast Action Manager von ACS Commons
>* Synthetic Workflow
>
>
Hierbei handelt es sich um eine Open-Source-Software. Sie wird mit der [Apache v2-Lizenz](https://adobe-consulting-services.github.io/pages/license.html) abgedeckt. Um eine Frage zu stellen oder ein Problem zu melden, besuchen Sie den Bereich für die entsprechenden [GitHub-Probleme für ACS AEM-Tools](https://github.com/Adobe-Consulting-Services/acs-aem-commons/issues) und [ACS AEM Commons](https://github.com/Adobe-Consulting-Services/acs-aem-tools/issues).

## Zu AEM migrieren {#migrate-to-aem}

Die Migration von Assets nach AEM setzt die Ausführung verschiedener Schritte voraus und sollte als stufenweises Verfahren angesehen werden. Die Migrationsphasen lauten wie folgt:

1. Workflows deaktivieren
1. Tags laden
1. Assets aufnehmen
1. Wiedergaben verarbeiten
1. Assets aktivieren
1. Workflows aktivieren

![chlimage_1-223](assets/chlimage_1-223.png)

### Disable workflows {#disable-workflows}

Deaktivieren Sie vor dem Beginn einer Migration die Starter für den `DAM Update Asset` Workflow. Am besten erfassen Sie alle Assets in das System und führen Sie dann die Workflows in Stapeln aus. Wenn Sie während der Migration bereits live sind, können Sie planen, dass diese Aktivitäten außerhalb der Arbeitszeit ausgeführt werden.

### Load tags {#load-tags}

Womöglich verfügen Sie bereits über eine Tag-Taxonomie für Ihre Bilder. Mit Tools wie dem CSV Asset Importer und den Metadaten-Profilen können Sie die Anwendung von Tags auf Assets automatisieren. Fügen Sie zuvor die Tags in Experience Manager hinzu. The [ACS AEM Tools Tag Maker](https://adobe-consulting-services.github.io/acs-aem-tools/features/tag-maker/index.html) feature lets you populate tags by using a Microsoft Excel spreadsheet that is loaded into the system.

### Ingest assets {#ingest-assets}

Leistung und Stabilität sind wichtige Faktoren bei der Aufnahme von Assets in das System. Stellen Sie beim Laden einer Menge Daten in Experience Manager sicher, dass das System gut funktioniert. Auf diese Weise konnte die zum Hinzufügen der Daten erforderliche Zeit minimiert und ein Überladen des Systems vermieden werden. Dadurch wird ein Systemabsturz verhindert, insbesondere bei Systemen, die bereits in Produktion sind.

Es gibt zwei Herangehensweisen zum Laden von Assets in das System: ein Push-basierter Ansatz mit HTTP oder ein Pull-basierter Ansatz mit JCR-APIs.

#### Push through HTTP {#push-through-http}

Das Managed Services-Team von Adobe lädt Daten mit einem Tool namens Glutton in Kundenumgebungen. Glutton ist eine kleine Java-Anwendung, die alle Assets von einem Verzeichnis in ein anderes Verzeichnis einer AEM-Instanz lädt. Statt Glutton können Sie auch Tools wie Perl-Skripts zum Posten der Assets in das Repository verwenden.

Der Ansatz, HTTPS zu durchdrücken, hat zwei Hauptvorteile:

1. Übertragen Sie die Assets über HTTP an den Server. Dies ist mit einem gewissen (zeitlichen) Mehraufwand verbunden, sodass die Migration länger dauert.
1. Wenn Tags und benutzerdefinierte Metadaten auf die Assets angewendet werden müssen, erfordert dieser Ansatz einen zweiten benutzerdefinierten Prozess, der zum Anwenden dieser Metadaten auf die Assets durchgeführt werden muss (nach dem Asset-Import).

Der andere Ansatz zur Aufnahme von Assets sieht einen Pull der Assets aus dem lokalen Dateisystem vor. Kann jedoch kein externes Laufwerk bzw. keine Netzwerkfreigabe an den Server angebunden werden, um den Pull-basierten Ansatz durchzuführen, sollten die Assets am besten über HTTP gepostet werden.

#### Ziehen Sie aus dem lokalen Dateisystem {#pull-from-the-local-file-system}

The [ACS AEM Tools CSV Asset Importer](https://adobe-consulting-services.github.io/acs-aem-tools/features/csv-asset-importer/index.html) pulls assets from the file system and asset metadata from a CSV file for the asset import. Die AEM Asset Manager-API dient zum Importieren der Assets in das System und zum Anwenden der konfigurierten Metadateneigenschaften. Im Idealfall werden die Assets über eine Netzwerkdateibereitstellung oder über ein externes Laufwerk auf dem Server bereitgestellt.

Wenn Assets nicht über ein Netzwerk übertragen werden, verbessert sich die Gesamtleistung erheblich. Diese Methode ist in der Regel die effizienteste Methode, um Assets in das Repository zu laden. Außerdem können Sie alle Assets und Metadaten in einem Schritt importieren, da das Tool die Metadaten-Erfassung unterstützt. Es ist kein weiterer Schritt erforderlich, um die Metadaten anzuwenden, z. B. mithilfe eines separaten Tools.

### Process renditions {#process-renditions}

Nachdem Sie die Assets in das System geladen haben, müssen Sie sie über den Workflow „DAM-Update-Asset“ verarbeiten, um Metadaten zu extrahieren und Wiedergaben zu generieren. Vor diesem Schritt müssen Sie den DAM-Update-Asset-Workflow duplizieren und an Ihre Anforderungen anpassen. Einige Schritte im Standardarbeitsablauf sind für Sie möglicherweise nicht erforderlich, wie z. B. die Scene7 PTIFF-Generierung oder die InDesign-Serverintegration.

Nachdem Sie den Workflow Ihren Anforderungen entsprechend konfiguriert haben, haben Sie zwei Optionen, um ihn auszuführen:

1. The simplest approach is [ACS Commons’ Bulk Workflow Manager](https://adobe-consulting-services.github.io/acs-aem-commons/features/bulk-workflow-manager.html). Mit diesem Tool können Sie eine Abfrage ausführen und die Ergebnisse der Abfrage durch einen Workflow verarbeiten. Darüber hinaus gibt es auch Optionen zum Festlegen von Stapelgrößen.
1. Sie können den [ACS Commons Fast Action Manager](https://adobe-consulting-services.github.io/acs-aem-commons/features/fast-action-manager.html) gemeinsam mit [Synthetischen Workflows](https://adobe-consulting-services.github.io/acs-aem-commons/features/synthetic-workflow.html) verwenden. Dieser Ansatz erfordert zwar viel mehr Mitwirkung, Sie können jedoch den Verwaltungsaufwand für die AEM-Workflow-Engine verringern und gleichzeitig die Verwendung von Serverressourcen optimieren. Darüber hinaus steigert der Fast Action Manager die Leistung durch die dynamische Überwachung der Serverressourcen und die Einschränkung der Systemlast. Beispielskripte wurden auf der Seite mit den ACS Commons-Funktionen bereitgestellt.

### Activate assets {#activate-assets}

Bei Bereitstellungen mit einer Veröffentlichungsstufe müssen Sie die Assets für die Veröffentlichungsfarm aktivieren. Zwar empfiehlt Adobe die Ausführung von mehr als einer Veröffentlichungsinstanz, dennoch ist es am effizientesten, alle Assets in einer Veröffentlichungsinstanz zu replizieren und dann diese Instanz zu klonen. Wird eine große Anzahl von Assets nach Auslösen einer Strukturaktivierung aktiviert, müssen Sie ggf. eingreifen. Deshalb: Beim Auslösen von Aktivierungen werden Elemente zu den Sling-Aufträgen/Ereignisschlangen hinzugefügt. Bei einer Warteschlangengröße von mehr als ca. 40.000 Elementen wird die Verarbeitung deutlich langsamer. Wenn die Größe dieser Warteschlange die Zahl von 100.000 Elementen übersteigt, wird die Systemstabilität beeinträchtigt.

Um hier Abhilfe zu schaffen, können Sie [Fast Action Manager](https://adobe-consulting-services.github.io/acs-aem-commons/features/fast-action-manager.html) für die Asset-Verwaltung einsetzen. Dies funktioniert ohne Sling-Warteschlangen und sorgt für weniger Mehraufwand, während der Workload gedrosselt wird, um eine Überlastung des Servers zu vermeiden. Ein Beispiel für die Verwendung von FAM zur Replikationsverwaltung finden Sie auf der Dokumentationsseite für die Funktion.

Weitere Optionen zum Abrufen von Assets in die Veröffentlichungsfarm sind die Verwendung von [vlt-rcp](https://jackrabbit.apache.org/filevault/rcp.html) oder [oak-run](https://github.com/apache/jackrabbit-oak/tree/trunk/oak-run), die als Werkzeuge im Rahmen von Jackrabbit bereitgestellt werden. Eine andere Möglichkeit ist die Verwendung eines Open-Source-Werkzeugs für Ihre AEM-Infrastruktur namens [Grabbit](https://github.com/TWCable/grabbit), das angeblich schneller ist als vlt.

Jeder dieser Ansätze ist dahingehend eingeschränkt, dass die Assets in der Autoreninstanz nicht als aktiviert angezeigt werden. Um diese Assets mit dem korrekten Aktivierungsstatus zu kennzeichnen, müssen Sie ein Skript ausführen, damit die Assets als aktiviert markiert werden.

>[!NOTE]
>
>Adobe bietet weder Wartung noch Unterstützung für Grabbit.

### Clone Publish {#clone-publish}

Nach Aktivierung der Assets können Sie Ihre Veröffentlichungsinstanz klonen, um die zur Bereitstellung benötigte Anzahl an Kopien zu erstellen. Einen Server zu klonen, ist ein relativ unkomplizierter Vorgang. Dabei müssen jedoch einige wichtige Schritte berücksichtigt werden. So klonen Sie eine Veröffentlichungsinstanz:

1. Sichern Sie die Quellinstanz und den Datenspeicher.
1. Stellen Sie die Sicherung der Instanz und des Datenspeichers am Zielspeicherort wieder her. Die folgenden Schritte beziehen sich allesamt auf diese neue Instanz.
1. Führen Sie eine Dateisystemsuche unter `crx-quickstart/launchpad/felix` nach durch `sling.id`. Löschen Sie diese Datei.
1. Suchen und löschen Sie etwaig vorhandene `repository-XXX`-Dateien im Stammverzeichnis.
1. Bearbeiten `crx-quickstart/install/org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config` und `crx-quickstart/launchpad/config/org/apache/jackrabbit/oak/plugins/blob/datastore/FileDataStore.config` bis zum Speicherort des Datenspeichers auf der neuen Umgebung.
1. Starten Sie die Umgebung.
1. Aktualisieren Sie die Konfiguration aller Replikationsagenten auf Autorseite so, dass auf die korrekten Veröffentlichungsinstanzen verwiesen wird, bzw. die Agenten „Dispatcher leeren“ der neuen Instanz so, dass auf die korrekten Dispatcher für die neue Umgebung verwiesen wird.

### Enable workflows {#enable-workflows}

Nach abgeschlossener Migration sollten die Starter für die Workflows „DAM-Update-Asset“ neu aktiviert werden, um die Wiedergabegenerierung und Metadatenextraktion für die laufende, tagtägliche Systemnutzung zu unterstützen.

## Assets über AEM-Bereitstellungen migrieren {#migrate-between-aem-instances}

Wenn es auch nicht so häufig vorkommt, müssen dennoch manchmal große Datenmengen zwischen AEM-Instanzen migriert werden, etwa wenn Sie ein AEM- bzw. Hardwareupgrade durchführen oder auf ein neues Rechenzentrum migrieren, wie bei der AMS-Migration.

In diesem Fall sind die Assets schon mit Metadaten aufgefüllt und Wiedergaben sind bereits generiert. Sie können sich einfach darauf konzentrieren, Assets zwischen Instanzen zu verschieben. Führen Sie beim Migrieren zwischen AEM-Instanzen die folgenden Schritte aus:

1. Workflows deaktivieren: Da Sie Darstellungen zusammen mit unseren Assets migrieren, sollten Sie die Workflow-Starter für DAM Update Asset deaktivieren.

1. Tags migrieren: Da Sie bereits Tags in der AEM-Quellinstanz geladen haben, können Sie sie in einem Inhaltspaket erstellen und das Zielgruppe auf der Instanz installieren.

1. Assets migrieren: Es gibt zwei Tools, die zum Verschieben von Assets von einer AEM-Instanz in eine andere empfohlen werden:

   * **Vault Remote Copy** oder `vlt rcp`ermöglicht die Verwendung von VLT in einem Netzwerk. Nach Angabe eines Quell- und Zielverzeichnisses lädt vlt alle Repositorydaten von einer Instanz herunter und lädt diese in die andere Instanz. Vlt rcp is documented at [https://jackrabbit.apache.org/filevault/rcp.html](https://jackrabbit.apache.org/filevault/rcp.html)
   * **Grabbit** ist ein Open-Source-Tool zur Inhaltssynchronisierung, das von Time Warner Cable für die eigene AEM-Implementierung entwickelt wurde. Durch die Nutzung kontinuierlicher Datenströme weist das Tool im Vergleich zu vlt rcp eine geringere Latenz auf. Darüber hinaus soll es zwei- bis zehnmal schneller sein als vlt rcp. Grabbit unterstützt zudem die alleinige Synchronisierung von Delta-Inhalten, sodass Änderungen nach erfolgreich abgeschlossener Erstmigration synchronisiert werden.

1. Activate assets: Follow the instructions for [activating assets](#activate-assets) documented for the initial migration to AEM.

1. Veröffentlichung klonen: Wie bei einer neuen Migration ist das Laden einer einzelnen Veröffentlichungsinstanz und das Klonen effizienter als das Aktivieren des Inhalts auf beiden Knoten. Siehe [Klonen von Veröffentlichungsinstanzen](#clone-publish).

1. Aktivieren von Workflows: Nachdem Sie die Migration abgeschlossen haben, aktivieren Sie die Starter für das DAM Update Asset Workflows, um die Generierung von Darstellungen und die Metadaten-Extraktion für die laufende Systemverwendung zu unterstützen.
