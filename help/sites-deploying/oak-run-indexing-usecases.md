---
title: Oak-run.jar – Indizierungsanwendungsfälle
seo-title: Oak-run.jar Indexing Use Cases
description: Erfahren Sie mehr über die verschiedenen Anwendungsfälle für die Indizierung mit dem Oak-run-Tool.
seo-description: Learn about the various user cases for performing indexing with the Oak-run tool.
uuid: 3c50080d-1e0d-4886-8d37-269f06881eb4
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: deploying
discoiquuid: 084075b8-826d-4f27-9342-35f33368f24f
noindex: true
exl-id: 62f1d3e6-b0d2-4d64-b62e-91836b573e8c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1411'
ht-degree: 58%

---

# Oak-run.jar – Indizierungsanwendungsfälle{#oak-run-jar-indexing-use-cases}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Oak-run unterstützt Indizierungen über die Befehlszeile, ohne dass diese über die JMX-Konsole von AEM ausgeführt werden müssen.

Die übergreifenden Vorteile bei der Verwendung des oak-run.jar-Befehls „index“ für die Verwaltung von Oak-Indizes:

1. Der Oak-run-Befehl „index“ bietet ein neues Indizierungs-Tool für AEM 6.4.
1. Oak-run verkürzt die Zeit bis zur Neuindizierung, wodurch die Neuindizierungszeiten bei größeren Repositorys reduziert werden.
1. Oak-run reduziert den Ressourcenverbrauch während der Neuindizierung in AEM, was zu einer insgesamt besseren Systemleistung führt.
1. Oak-run bietet Out-of-Band-Neuindizierung und unterstützt Situationen, in denen die Produktion verfügbar sein muss und keine Wartung oder Ausfallzeiten tolerieren kann, die andernfalls für die Neuindizierung erforderlich sind.

In den folgenden Abschnitten finden Sie Beispielbefehle. Der oak-run-Indexbefehl unterstützt alle NodeStore- und BlobStore-Setups. Die folgenden Beispiele beziehen sich auf Setups mit FileDataStore und SegmentNodeStore.

## Nutzungsszenario 1 - Prüfung der Indexkonsistenz {#usercase1indexconsistencycheck}

Dies ist ein Anwendungsfall im Zusammenhang mit Indexbeschädigung. In einigen Fällen war es nicht möglich festzustellen, welche Indizes beschädigt sind. Daher bietet Adobe Tools, die Folgendes ermöglichen:

1. Konsistenzprüfungen aller Indizes und Erstellung eines Berichts über die gültigen und ungültigen Indizes. 
1. Das Tool kann auch verwendet werden, wenn kein Zugriff auf AEM möglich ist. 
1. Die Verwendung ist einfach.

Eine Suche nach beschädigten Indizes kann mit dem Vorgang `--index-consistency-check` durchgeführt werden:

```shell
java -jar oak-run*.jar index --fds-path=/path/to/datastore  /path/to/segmentstore/ --index-consistency-check
```

Dieser generiert einen Bericht in der Datei `indexing-result/index-consistency-check-report.txt` Unten finden Sie einen Beispielbericht:

```
Valid indexes :
        - /content/oak:index/enablementResourceName
        - /oak:index/cqProjectLucene
        - /oak:index/cqTagLucene
        - /oak:index/lucene
        - /oak:index/ntBaseLucene
        - /oak:index/socialLucene
    Invalid indexes :
        - /oak:index/atDamIndex
        - /oak:index/atIndex
        - /oak:index/cqPageLucene
        - /oak:index/damAssetLucene
        - /oak:index/groups
        - /oak:index/slingeventJob
        - /oak:index/users
        - /oak:index/workflowDataLucene
    Ignored indexes as these are not of type lucene:
        - /oak:index/acPrincipalName
        - /oak:index/active
```

### Vorteile {#uc1benefits}

Diese Tools können jetzt vom Support und vom Systemadministrator verwendet werden, um schnell zu ermitteln, welche Indizes beschädigt sind, und sie dann neu indizieren.

## Anwendungsfall 2: Indexstatistiken {#usecase2indexstatistics}

Für die Diagnose einiger Fälle rund um die Adobe der Abfrageleistung waren häufig eine vorhandene Indexdefinition und indexbezogene Statistiken aus der Kundeneinrichtung erforderlich. Bisher wurden diese Informationen über mehrere Ressourcen verteilt. Um die Fehlerbehebung zu vereinfachen, hat Adobe Tools erstellt, die Folgendes ermöglichen:

1. Dump aller im System vorhandener Indexdefinitionen in einer einzigen JSON-Datei. 

1. Dump wichtiger Statistiken aus vorhandenen Indizes. 

1. Dump von Indexinhalten für Offline-Analysen. 

1. Kann auch verwendet werden, wenn kein Zugriff auf AEM möglich ist. 

Die obigen Vorgänge können jetzt mit den folgenden Indexbefehlen ausgeführt werden:

* `--index-info` – Sammelt verschiedene indexbezogene Statistiken und gibt deren Speicherinhalt aus

* `--index-definitions` – Sammelt Indexdefinitionen und gibt deren Speicherinhalt aus

* `--index-dump` – Gibt den Speicherinhalt von Indexinhalten aus

Unten sehen Sie ein Beispiel dafür, wie der Befehl in der Praxis arbeitet:

```shell
java -jar oak-run*.jar index --fds-path=/path/to/datastore  /path/to/segmentstore/ --index-info --index-definitions --index-dump
```

Die Berichte werden in `indexing-result/index-info.txt` und `indexing-result/index-definitions.json` erstellt.

Außerdem werden dieselben Details über die Web-Konsole bereitgestellt und wären Teil der ZIP-Datei für die Konfigurationsablage. Sie können unter folgendem Pfad darauf zugreifen:

`https://serverhost:serverport/system/console/status-oak-index-defn`

### Vorteile {#uc2benefits}

Diese Tools ermöglichen die schnelle Erfassung aller erforderlichen Details im Zusammenhang mit Indizierungs- oder Abfrageproblemen und verkürzen die Zeit, die mit dem Extrahieren dieser Informationen verbracht wird.

## Anwendungsfall 3: Neuindizierung {#usecase3reindexing}

Je nach [Szenario](https://jackrabbit.apache.org/oak/docs/query/indexing.html#reindexing) ist es in einigen Fällen notwendig, eine Neuindizierung durchzuführen. Zurzeit erfolgt die Neuindizierung, indem das Flag `reindex` im Indexdefinitionsknoten über CRXDE oder die Benutzeroberfläche des Index-Managers auf `true` gesetzt wird. Nachdem das Flag gesetzt wurde, erfolgt die Neuindizierung asynchron.

Einige Hinweise zur Neuindizierung:

* Die Neuindizierung verläuft in `DocumentNodeStore`-Setups weitaus langsamer als in `SegmentNodeStore`-Setups, in denen der gesamte Inhalt lokal gespeichert ist. 

* Während der Neuindizierung wird zurzeit der asynchrone Indexer blockiert, weshalb alle anderen asynchronen Indizes veralten, weil sie während der Indizierung nicht mehr aktualisiert werden. Wenn das System verwendet wird, kann es aus diesem Grund passieren, dass Benutzer keine aktuellen Ergebnisse sehen. 
* Bei der Neuindizierung muss das gesamte Repository durchlaufen werden, was eine hohe Verarbeitungslast für das AEM-Setup bedeuten und sich negativ auf die Benutzerfreundlichkeit auswirken kann.
* Für eine `DocumentNodeStore`-Installation, in der die Neuindizierung sehr lange dauern kann, muss die Indizierung komplett neu gestartet werden, falls die Verbindung zur Mongo-Datenbank während des Vorgangs unterbrochen wird.

* In einigen Fällen kann die Neuindizierung aufgrund der Textextraktion lange dauern. Dies ist hauptsächlich für Setups mit vielen PDF-Dateien spezifisch, bei denen sich die für die Textextraktion aufgewendete Zeit auf die Indizierungszeit auswirken kann.

Um diese Ziele zu erreichen, unterstützt das Oak-run-Index-Tool verschiedene Neuindizierungsmodi, die bei Bedarf verwendet werden können. Der oak-run-Indexbefehl bietet folgende Vorteile:

* **Out-of-Band-Neuindizierung** – Die Oak-run-Neuindizierung kann getrennt von einem ausgeführten AEM-Setup ausgeführt werden. Dies minimiert die Auswirkungen auf die verwendete AEM-Instanz. 

* **Out-of-Lane-Neuindizierung** – Die Neuindizierung hat keine Auswirkungen auf Indizierungsvorgänge. Dies bedeutet, dass der asynchrone Indexer andere Indizes weiterhin indizieren kann. 

* **Vereinfachte Neuindizierung für DocumentNodeStore-Installationen** – Für `DocumentNodeStore`-Installationen kann die Neuindizierung mit einem einzigen Befehl ausgeführt werden, der sicherstellt, dass die Neuindizierung auf die optimalste Weise erfolgt.

* **Unterstützt die Aktualisierung der Indexdefinitionen und das Erstellen neuer Indexdefinitionen** 

### Neuindizierung – DocumentNodeStore {#reindexdocumentnodestore}

Für `DocumentNodeStore`-Installationen kann die Neuindizierung über einen einzelnen Oak-run-Befehl ausgeführt werden:

```shell
java -jar oak-run*.jar index --reindex --index-paths=/oak:index/lucene --read-write --fds-path=/path/to/datastore mongodb://server:port/aem
```

Dies bietet die folgenden Vorteile

* Minimale Auswirkung auf AEM Instanzen. Die meisten Lesevorgänge können von Sekundärservern ausgeführt werden und ausgeführte AEM-Caches sind nicht von all den für die Neuindizierung erforderlichen Durchläufen betroffen. 
* Benutzer können über die Option `--index-definitions-file` auch eine JSON-Datei oder einen neuen oder aktualisierten Index bereitstellen.

### Neuindizierung – SegmentNodeStore {#reindexsegmentnodestore}

Für `SegmentNodeStore`-Installationen kann die Neuindizierung auf eine der folgenden Weisen durchgeführt werden:

#### Online-Neuindizierung – SegmentNodeStore {#onlinereindexsegmentnodestore}

Das übliche Verfahren, bei dem das Flag `reindex` gesetzt wird.

#### Online-Neuindizierung – SegmentNodeStore – Die AEM-Instanz wird ausgeführt {#onlinereindexsegmentnodestoretheaeminstanceisrunning}

In `SegmentNodeStore`-Installationen kann nur ein Prozess im Lese-/Schreibmodus auf Segmentdateien zugreifen. Daher erfordern einige Vorgänge der Oak-run-Indizierung zusätzliche manuelle Schritte.

Dies würde Folgendes umfassen:

1. Schritttext
1. Verbinden Sie `oak-run` mit dem von AEM verwendeten Repository im schreibgeschützten Modus und führen Sie die Neuindizierung durch. Beispiel: 

   ```shell
   java -jar oak-run-1.7.6.jar index --fds-path=/Users/dhasler/dev/cq/quickstart/target/crx-quickstart/repository/datastore/ --checkpoint 26b7da38-a699-45b2-82fb-73aa2f9af0e2 --reindex --index-paths=/oak:index/lucene /Users/dhasler/dev/cq/quickstart/target/crx-quickstart/repository/segmentstore/
   ```

1. Importieren Sie nach dem Ausführen des obigen Befehls die erstellten Indexdateien mit dem Vorgang `IndexerMBean#importIndex` aus dem Pfad, unter dem Oak-run die Indexdateien gespeichert hat.

In diesem Szenario müssen Sie den AEM-Server nicht stoppen oder eine neue Instanz bereitstellen. Da die Indizierung jedoch das Durchlaufen des gesamten Repositorys beinhaltet, würde sich die I/O-Belastung der Installation erhöhen und die Laufzeitleistung negativ beeinflussen.

#### Online-Neuindizierung - SegmentNodeStore - Die AEM Instanz ist beendet. {#onlinereindexsegmentnodestoreaeminstanceisdown}

Für `SegmentNodeStore`-Installationen kann die Neuindizierung über einen einzigen Oak-run-Befehl ausgeführt werden: Die AEM-Instanz muss jedoch heruntergefahren werden.

Sie können die Neuindizierung des Triggers mit dem folgenden Befehl durchführen:

```shell
java -jar oak-run*.jar index --reindex --index-paths=/oak:index/lucene --read-write --fds-path=/path/to/datastore  /path/to/segmentstore/ 
```

Der Unterschied zwischen diesem und dem oben erläuterten Ansatz besteht darin, dass die Erstellung von Checkpoints und der Import von Indizes automatisch erfolgen. Der Nachteil ist, dass AEM während des Prozesses ausfallen muss.

#### Out-Band-Neuindizierung - SegmentNodeStore {#outofbandreindexsegmentnodestore}

In diesem Anwendungsfall können Sie eine Neuindizierung an einem geklonten Setup durchführen, um die Auswirkungen auf die laufende AEM zu minimieren:

1. Erstellen Sie einen Checkpoint über einen JMX-Vorgang. Hierzu können Sie in der [JMX-Konsole](/help/sites-administering/jmx-console.md) nach `CheckpointManager` suchen. Klicken Sie anschließend auf den Vorgang **createCheckpoint (long p1)** und verwenden Sie einen hohen Ablaufwert in Sekunden (z. B. **2592000**).
1. Kopieren Sie den Ordner `crx-quickstart` auf einen neuen Computer.
1. Führen Sie die Neuindizierung über den Oak-run-Befehl „index“ durch. 

1. Kopieren Sie die generierten Indexdateien auf den AEM-Server. 

1. Importieren Sie die Indexdateien über JMX. 

In diesem Szenario wird davon ausgegangen, dass der Zugriff auf den Datenspeicher in einer anderen Instanz möglich ist. Dies ist nicht möglich, wenn `FileDataStore` in einer Cloud-basierten Speicherlösung wie EBS platziert ist. Dies schließt das Szenario aus, in dem auch `FileDataStore` geklont wird. Wenn die Indexdefinition keine Volltextindizierung durchführt, ist kein Zugriff auf den `DataStore` erforderlich.

## Anwendungsfall 4 – Aktualisieren der Indexdefinitionen {#usecase4updatingindexdefinitions}

Zurzeit können Sie Änderungen der Indexdefinitionen über das Paket [ACS Ensure Index](https://adobe-consulting-services.github.io/acs-aem-commons/features/ensure-oak-index/index.html) versenden. Dies ermöglicht den Versand der Indexdefinitionen über das Inhaltspaket, das später neu indiziert werden muss, indem das Flag `reindex` auf `true` gesetzt wird.

Dies funktioniert bei kleineren Installationen, bei denen die Neuindizierung nicht lange dauert. Bei sehr großen Repositorys erfolgt die Neuindizierung jedoch in einer deutlich größeren Zeit. Für solche Fälle können wir jetzt das Oak-Run-Index-Tool verwenden.

Oak-run unterstützt jetzt die Bereitstellung von Indexdefinitionen im JSON-Format und die Erstellung von Index im Out-of-Band-Modus, bei dem keine Änderungen an einer Live-Instanz vorgenommen werden.

Der Prozess, den Sie für diesen Anwendungsfall beachten müssen, ist:

1. Ein Entwickler aktualisiert die Indexdefinitionen in einer lokalen Instanz und generiert dann mit der Option `--index-definitions` eine JSON-Indexdefinitionsdatei.

1. Die aktualisierte JSON-Datei erhält die bzw. der Systemadmin. 
1. Die bzw. der Systemadmin verfolgt den Out-of-Band-Ansatz und bereitet den Index in einer anderen Installation vor. 
1. Sobald dies abgeschlossen ist, werden die erstellten Indexdateien in eine laufende AEM-Installation importiert.
