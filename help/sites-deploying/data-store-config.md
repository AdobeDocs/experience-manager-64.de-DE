---
title: Konfigurieren von Knotenspeichern und Datenspeichern in AEM 6
seo-title: Configuring node stores and data stores in AEM 6
description: Erfahren Sie, wie Sie Knotenspeicher und Datenspeicher konfigurieren und wie Sie die automatische Datenspeicherbereinigung durchführen.
seo-description: Learn how to configure node stores and data stores and how to perform data store garbage collection.
uuid: b6bb43c7-23e9-428a-b977-6d4e246e714e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: deploying
discoiquuid: d4636434-98a6-4cf7-bb92-4338da17c893
legacypath: /deploy/platform/data-store-config
feature: Configuring
exl-id: 89b8e8a7-103b-472e-8c29-3b6e5b7273b1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3442'
ht-degree: 67%

---

# Konfigurieren von Knotenspeichern und Datenspeichern in AEM 6 {#configuring-node-stores-and-data-stores-in-aem}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Einführung {#introduction}

In Adobe Experience Manager (AEM) können Binärdaten unabhängig von den Inhaltsknoten gespeichert werden. Die Binärdaten werden in einem Datenspeicher gespeichert, während Inhaltsknoten in einem Knotenspeicher gespeichert werden.

Sowohl Datenspeicher als auch Knotenspeicher können mit der OSGi-Konfiguration konfiguriert werden. Jede OSGi-Konfiguration wird mithilfe einer beständigen Kennung (PID) referenziert.

## Konfigurationsschritte {#configuration-steps}

Führen Sie die folgenden Schritte aus, um sowohl den Knotenspeicher als auch den Datenspeicher zu konfigurieren:

1. Kopieren Sie die AEM Schnellstart-JAR-Datei in den Installationsordner.
1. Erstellen Sie einen Ordner `crx-quickstart/install` im Installationsverzeichnis.
1. Konfigurieren Sie zunächst den Knotenspeicher, indem Sie eine Konfigurationsdatei mit dem Namen der zu verwendenden Knotenspeicher-Option im Verzeichnis `crx-quickstart/install` erstellen.

   Der Knotenspeicher „Dokument“ (die Basis der AEM-MongoMK-Implementierung) nutzt etwa die Datei `org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService.config`.

1. Bearbeiten Sie die Datei und legen Sie die Konfigurationsoptionen fest.
1. Erstellen Sie eine Konfigurationsdatei mit der PID des Datenspeichers, den Sie verwenden möchten. Bearbeiten Sie die Datei, um die Konfigurationsoptionen festzulegen.

   >[!NOTE]
   >
   >Weitere Informationen zu Konfigurationsoptionen finden Sie unter [Knotenspeicher-Konfigurationen](#node-store-configurations) und [Datenspeicher-Konfigurationen](#data-store-configurations).

1. Starten Sie AEM.

## Knotenspeicherkonfigurationen {#node-store-configurations}

>[!CAUTION]
>
>Neuere Versionen von Oak verwenden ein neues Benennungsschema und -format für OSGi-Konfigurationsdateien. Das neue Namensschema erfordert, dass die Konfigurationsdatei **.config** und das neue Format erfordert die Eingabe von Werten und ist [hier dokumentiert](https://sling.apache.org/documentation/development/slingstart.html#default-configuration-format).
>
>Wenn Sie von einer älteren Oak-Version aktualisieren, stellen Sie sicher, dass Sie zunächst den Ordner `crx-quickstart/install` sichern. Stellen Sie nach dem Upgrade den Inhalt des Ordners in der aktualisierten Installation wieder her und ändern Sie die Erweiterung der Konfigurationsdateien von **.cfg** zu **.config**.
>
>Falls Sie diesen Artikel lesen, um ein Upgrade von einem **AEM 5.x** installieren, konsultieren Sie die [Upgrade](https://docs.adobe.com/content/docs/de/aem/6-0/deploy/upgrade.html) Dokumentation zuerst.

### Segmentknotenspeicher {#segment-node-store}

Der Segmentknotenspeicher ist die Grundlage für die TarMK-Implementierung der Adobe in AEM6. Zur Konfiguration wird die PID `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService` verwendet.

>[!CAUTION]
>
>Die PID für den Segment-Knotenspeicher hat sich von `org.apache.jackrabbit.oak.plugins.segment.SegmentNodeStoreService in previous versions` in AEM 6 zu `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService` in AEM 6.3 geändert. Stellen Sie sicher, dass Sie die erforderlichen Konfigurationsanpassungen vornehmen, um diese Änderung widerzuspiegeln.

Sie können die folgenden Optionen konfigurieren:

* `repository.home`: Pfad zum Repository-Stammverzeichnis, in dem Repository-bezogene Daten gespeichert werden. Standardmäßig werden Segmentdateien im Verzeichnis `crx-quickstart/segmentstore` gespeichert.

* `tarmk.size`: Maximale Größe eines Segments in MB. Der standardmäßige Maximalwert lautet 256 MB.
* `customBlobStore`: Boolescher Wert, der angibt, dass ein benutzerdefinierter Datenspeicher verwendet wird. Der Standardwert ist „true“ für AEM 6.3 und höhere Versionen. Vor AEM 6.3 war die Standardeinstellung „false“.

Es folgt eine Beispieldatei für `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config`:

```shell
#Path to repo
repository.home="crx-quickstart/repository"

#Max segment size
tarmk.size=I"256"

#Custom data store
customBlobStore=B"true"
```

### Knotenspeicher &quot;Dokument&quot; {#document-node-store}

Der Knotenspeicher &quot;document&quot;bildet die Grundlage AEM MongoMK-Implementierung. Sie verwendet die `org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService` **PID**. Folgende Konfigurationsoptionen sind verfügbar:

* `mongouri`: Die für die Verbindung zur Mongo-Datenbank erforderliche [MongoURI](https://docs.mongodb.org/manual/reference/connection-string/). Standard: `mongodb://localhost:27017`

* `db`: Name der Mongo-Datenbank. Der Standardwert ist **Oak** . Neue AEM 6 werden jedoch verwendet **aem-author** als standardmäßigen Datenbanknamen.

* `cache`: Cache-Größe in MB. Dieser Wert verteilt sich auf die verschiedenen in DocumentNodeStore verwendeten Caches. Standard: `256`.

* `changesSize`: Größe (in MB) der begrenzten Sammlung, die in Mongo zum Caching unterschiedlicher Ausgaben verwendet wird. Der Standardwert lautet `256`.

* `customBlobStore`: Boolescher Wert, der angibt, dass ein benutzerdefinierter Datenspeicher verwendet wird. Der Standardwert lautet `false`.

Es folgt eine Beispieldatei für `org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService.config`:

```shell
#Mongo server details
mongouri="mongodb://localhost:27017"

#Name of Mongo database to use
db="aem-author"

#Store binaries in custom BlobStore
customBlobStore=B"false"
```

## Datenspeicherkonfigurationen {#data-store-configurations}

Muss eine große Anzahl von Binärdateien verarbeitet werden, wird empfohlen, statt der Standard-Knotenspeicher einen externen Datenspeicher zu verwenden, um die Leistung zu maximieren.

Wenn beispielsweise für Ihr Projekt eine große Anzahl von Medien-Assets erforderlich ist, wird durch die Speicherung dieser Assets im Datei- oder S3-Datenspeicher der Zugriff auf sie schneller erfolgt, als direkt in einer MongoDB zu speichern.

Der Dateidatenspeicher bietet eine bessere Leistung als MongoDB. Die Sicherungs- und Wiederherstellungsvorgänge von Mongo sind bei einer großen Anzahl von Assets ebenfalls langsamer.

Details zu den verschiedenen Datenspeichern und Konfigurationen werden nachfolgend beschrieben.

>[!NOTE]
>
>Um benutzerdefinierte Datenspeicher verwenden zu können, müssen Sie `customBlobStore` in `true` der entsprechenden Knotenspeicher-Konfigurationsdatei ([Knotenspeicher „Segment“](/help/sites-deploying/data-store-config.md#segment-node-store) oder [Knotenspeicher „Dokument“](/help/sites-deploying/data-store-config.md#document-node-store)) auf einstellen.

### Dateidatenspeicher {#file-data-store}

Dies ist die Implementierung von [FileDataStore](https://jackrabbit.apache.org/api/2.8/org/apache/jackrabbit/core/data/FileDataStore.html) vorhanden in Jackrabbit 2. Es bietet eine Möglichkeit, die Binärdaten als normale Dateien im Dateisystem zu speichern. Verwendet wird dabei die PID `org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore`.

Die folgenden Konfigurationsoptionen sind verfügbar:

* `repository.home`: Pfad zum Repository-Stammverzeichnis, in dem diverse Repository-bezogene Daten gespeichert werden. Standardmäßig werden Binärdateien im Verzeichnis `crx-quickstart/repository/datastore` gespeichert..

* `path`: Pfad zum Verzeichnis, unter dem Dateien gespeichert werden. Sofern angegeben, hat dieser Wert Vorrang gegenüber `repository.home`..

* `minRecordLength`: Mindestgröße in Byte einer im Datenspeicher abgelegten Datei. Binärinhalte, die unterhalb dieses Werts liegen, werden als Inline-Elemente dargestellt.

>[!NOTE]
>
>Wenn Sie einen NAS verwenden, um freigegebene Dateidatenspeicher zu speichern, stellen Sie sicher, dass Sie nur leistungsstarke Geräte verwenden, um Leistungsprobleme zu vermeiden.

## Amazon S3-Datenspeicher {#amazon-s-data-store}

AEM kann so konfiguriert werden, dass Daten im Simple Storage Service (S3) von Amazon gespeichert werden. Zur Konfiguration wird die PID `org.apache.jackrabbit.oak.plugins.blob.datastore.S3DataStore.config` verwendet.

Zur Aktivierung der S3-Datenspeicherfunktionalität muss ein Feature Pack mit dem S3-Datenspeicher-Connector heruntergeladen und installiert werden. Gehen Sie zum [Adobe-Repository](https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/) und laden Sie die neueste Version der 1.8.x-Versionen des Feature Packs herunter (z. B. com.adobe.granite.oak.s3connector-1.8.0.zip). Darüber hinaus müssen Sie auch das neueste AEM Service Pack herunterladen und installieren, wie im Abschnitt [AEM 6.4 Service Pack - Versionshinweise](https://experienceleague.adobe.com/docs/experience-manager-64/release-notes/release-notes.html?lang=de) Seite.

>[!NOTE]
>
>Bei Verwendung von AEM 6.4 mit TarMK werden die Binärdateien standardmäßig im `FileDataStore`. Um TarMK mit dem S3-Datenspeicher nutzen zu können, müssen Sie AEM mithilfe des `crx3tar-nofds`-Ausführungsmodus starten, z. B.:

```shell
java -jar aem6.4.jar -r crx3tar-nofds
```

Nach dem Download können Sie den S3-Connector wie folgt installieren und konfigurieren:

1. Extrahieren Sie den Inhalt der ZIP-Datei des Feature Packs in einen temporären Ordner.

1. Wechseln Sie zum temporären Ordner und navigieren Sie zum folgenden Speicherort:

   ```xml
   jcr_root/libs/system/install
   ```

   Kopieren Sie alle Inhalte vom oben genannten Speicherort nach `<aem-install>/crx-quickstart/install.`

1. Wenn AEM bereits für Tar- oder MongoDB-Speicher konfiguriert ist, entfernen Sie etwaig vorhandene Konfigurationsdateien aus dem Ordner `aem-install/crx-quickstart/install`, bevor Sie fortfahren. Die folgenden Dateien müssen entfernt werden:

   * `For MongoMK: org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService.config`
   * `For TarMK: org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config`

1. Kehren Sie zum temporären Verzeichnis mit dem extrahierten Feature Pack zurück und kopieren Sie den Inhalt des folgenden Ordners:

   * `jcr_root/libs/system/config`

   in

   * `<aem-install>/crx-quickstart/install`

   Stellen Sie sicher, dass Sie nur die für die aktuelle Konfiguration benötigten Konfigurationsdateien kopieren. Kopieren Sie sowohl bei einem dedizierten Datenspeicher als auch bei einem freigegebenen Datenspeicher die Datei `org.apache.jackrabbit.oak.plugins.blob.datastore.S3DataStore.config`.

   >[!NOTE]
   >
   >Führen Sie bei einer Clustereinrichtung die oben genannten Schritte für alle Knoten des Clusters einzeln durch. Stellen Sie außerdem sicher, dass Sie dieselben S3-Einstellungen für alle Knoten verwenden.

1. Bearbeiten Sie die Datei und fügen Sie die für Ihr Setup erforderlichen Konfigurationsoptionen hinzu.
1. Starten Sie AEM.

### Aktualisieren auf eine neue Version des 1.8.x S3-Connectors {#upgrading-to-a-new-version-of-the-x-s-connector}

Wenn Sie auf eine neue Version des 1.8.x S3-Connectors aktualisieren müssen (z. B. von 1.8.0 auf 1.8.1), führen Sie die folgenden Schritte aus:

1. Halten Sie die AEM-Instanz an.

1. Navigieren Sie im AEM-Installationsordner zu `<aem-install>/crx-quickstart/install/15` und sichern Sie die dort vorhandenen Inhalte.
1. Löschen Sie nach der Sicherung die alte Version des S3-Connectors und die entsprechenden abhängigen Elemente, indem Sie die JAR-Dateien aus dem Ordner `<aem-install>/crx-quickstart/install/15` entfernen, z. B.:

   * **oak-blob-cloud-1.6.1.jar**
   * **aws-java-sdk-osgi-1.10.76.jar**

   >[!NOTE]
   >
   >Die oben aufgeführten Dateinamen dienen nur zu Veranschaulichungszwecken und sind nicht endgültig.

1. Laden Sie die neueste Version des Feature Packs 1.8.x aus dem [Adobe-Repository](https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/) herunter.
1. Entpacken Sie den Inhalt in einen anderen Ordner und navigieren Sie dann zu `jcr_root/libs/system/install/15`.
1. Kopieren Sie die JAR-Dateien nach **&lt;aem-install>**/crx-quickstart/install/15 im AEM-Installationsverzeichnis.
1. Starten Sie AEM und überprüfen Sie die Funktionsweise des Connectors.

Sie können die Konfigurationsdatei mit den folgenden Optionen verwenden:

* accessKey: Der AWS-Zugriffsschlüssel.
* secretKey: Der geheime AWS-Zugriffsschlüssel. **Hinweis:** Wenn die `accessKey` oder `secretKey` nicht angegeben ist, wird die [IAM-Rolle](https://docs.aws.amazon.com/sdk-for-java/v1/developer-guide/java-dg-roles.html) wird für die Authentifizierung verwendet.
* s3Bucket: Der Name des Buckets.
* s3Region: Die Region des Buckets.
* path: Der Pfad des Datenspeichers. Der Standardwert lautet **&lt;AEM install folder>/repository/datastore**.
* minRecordLength: Die Mindestgröße eines Objekts, das im Datenspeicher gespeichert werden soll. Der Minimal-/Standardwert lautet **16 KB.**
* maxCachedBinarySize: Binärdateien, die kleiner als oder gleich diesem Wert sind, werden im Speichercache gespeichert. Die Größe wird in Byte angegeben. Der Standardwert lautet **17408** (17 KB).

* cacheSize: Die Größe des Cache. Der Wert wird in Byte angegeben. Der Standardwert lautet **64 GB**.
* secret: Darf nur bei einer nicht binären Replikation für freigegebene Datenspeicher verwendet werden.
* stagingSplitPercentage: Der Prozentsatz der Cachegröße, der zum Staging asynchroner Uploads konfiguriert ist. Der Standardwert lautet **10**.
* uploadThreads: Die Anzahl der Uploadthreads für asynchrone Uploads. Der Standardwert lautet **10**.
* stagingPurgeInterval: Das Intervall in Sekunden zum endgültigen Löschen abgeschlossener Uploads aus dem Staging-Cache. Der Standardwert lautet **300** Sekunden (5 Minuten).
* stagingRetryInterval: Das Wiederholungsintervall in Sekunden für fehlgeschlagene Uploads. Der Standardwert ist **600** Sekunden (10 Minuten).

### Bucket-Regionsoptionen {#bucket-region-options}

<table> 
 <tbody> 
  <tr> 
   <td>USA, Standard</td> 
   <td><code>us-standard</code></td> 
  </tr> 
  <tr> 
   <td>USA, Westen</td> 
   <td><code>us-west-2</code></td> 
  </tr> 
  <tr> 
   <td>USA, Westen (Nordkalifornien)</td> 
   <td><code>us-west-1</code></td> 
  </tr> 
  <tr> 
   <td>EU (Irland)<br /> </td> 
   <td><code>EU</code></td> 
  </tr> 
  <tr> 
   <td>Asien/Pazifik (Singapur)<br /> </td> 
   <td><code>ap-southeast-1</code></td> 
  </tr> 
  <tr> 
   <td>Asien/Pazifik (Sydney)<br /> </td> 
   <td><code>ap-southeast-2</code></td> 
  </tr> 
  <tr> 
   <td>Asien/Pazifik (Tokio)</td> 
   <td><code>ap-northeast-1</code></td> 
  </tr> 
  <tr> 
   <td>Südamerika (Sao Paolo)<br /> </td> 
   <td><code>sa-east-1</code></td> 
  </tr> 
 </tbody> 
</table>

**Datenspeicher-Caching**

>[!NOTE]
>
>Die Datenspeicher-Implementierungen von `S3DataStore`, `CachingFileDataStore` und `AzureDataStore` unterstützen das Caching lokaler Dateisysteme. Die `CachingFileDataStore`-Implementierung ist nützlich, wenn sich der Datenspeicher auf NFS (Network File System) befindet.

Beim Aktualisieren von einer älteren Cache-Implementierung (vor Oak 1.6) gibt es einen Unterschied in der Struktur des Cache-Verzeichnisses des lokalen Dateisystems. In der alten Cachestruktur wurden sowohl die heruntergeladenen als auch die hochgeladenen Dateien direkt unter den Cachepfad gesetzt. In der neuen Struktur werden Downloads und Uploads voneinander getrennt und in zwei Verzeichnissen namens `upload` und `download` unter dem Cachepfad gespeichert. Der Upgradeprozess sollte nahtlos sein und etwaige ausstehende Uploads sollten zum Hochladen geplant werden; etwaige zuvor heruntergeladene Dateien werden bei Initialisierung im Cache abgelegt.

Sie können den Cache auch offline upgraden, indem Sie den Befehl `datastorecacheupgrade` von oak-run ausführen. Weitere Einzelheiten zum Ausführen des Befehls finden Sie in der [Readme](https://svn.apache.org/repos/asf/jackrabbit/oak/trunk/oak-run/README.md)-Datei für das oak-run-Modul.

Der Cache hat eine Größenbeschränkung und kann mithilfe des cacheSize-Parameters konfiguriert werden.

**Downloads**

Der lokale Cache wird auf die Datei-/Blob-Anforderung geprüft, bevor ein Zugriff auf den Datenspeicher erfolgt. Wenn der Cache das konfigurierte Limit (siehe `cacheSize`-Parameter) überschreitet, während dem Cache eine Datei hinzugefügt wird, werden einige der Dateien entfernt, um Speicher freizugeben.

**Asynchrone Uploads**

Der Cache unterstützt asynchrone Uploads in den DataStore. Die Dateien werden lokal im Cache (im Dateisystem) bereitgestellt und ein asynchroner Auftrag startet das Hochladen der Datei. Die Anzahl der asynchronen Uploads ist durch die Größe des Staging-Cache begrenzt. Die Größe des Staging-Cache wird mithilfe des `stagingSplitPercentage`-Parameters konfiguriert. Dieser Parameter definiert den Prozentsatz der Cachegröße, der für den Staging-Cache verwendet werden soll. Außerdem wird der Prozentsatz des für Downloads verfügbaren Caches berechnet als **(100 - `stagingSplitPercentage`) &amp;ast;`cacheSize`**.

Asynchrone Uploads verlaufen in mehreren Threads und die Anzahl der Threads wird mithilfe des `uploadThreads`-Parameters konfiguriert.

Die Dateien werden nach Abschluss der Uploads in den Haupt-Download-Cache verschoben. Wenn die Größe des Staging-Cache die Grenze überschreitet, werden die Dateien synchron in den DataStore hochgeladen, bis die vorherigen asynchronen Uploads abgeschlossen sind und wieder Speicherplatz im Staging-Cache verfügbar ist. Die hochgeladenen Dateien werden aus dem Staging-Bereich durch einen periodischen Auftrag entfernt, dessen Intervall durch den `stagingPurgeInterval`-Parameter konfiguriert ist.

Fehlgeschlagene Uploads (etwa aufgrund von Netzwerkstörungen) werden in eine Warteschlange gestellt und regelmäßig wiederholt. Das Wiederholungsintervall wird mithilfe des `stagingRetryInterval parameter` konfiguriert.

### Konfiguration der Binärdatei-losen Replikation mit Amazon S3 {#configuring-binaryless-replication-with-amazon-s}

Um die Binärdatei-lose Replikation mit S3 zu konfigurieren, sind die folgenden Schritte erforderlich:

1. Installieren Sie die Autoren- und Veröffentlichungsinstanzen und stellen Sie sicher, dass sie ordnungsgemäß gestartet wurden.
1. Wechseln Sie zu den Einstellungen des Replikationsagenten, indem Sie eine Seite öffnen, um *http://localhost:4502/etc/replication/agents.author/publish.html*.
1. Wählen Sie im Abschnitt **Einstellungen** die Schaltfläche **Bearbeiten**.
1. Ändern Sie die Option für den **Serialisierungs** typ in **Nicht binär**.

1. Fügen Sie den Parameter `binaryless` = `true` dem Transport-URI hinzu. Nach dieser Änderung sollte der URI ungefähr wie folgt aussehen:

   *http://localhost:4503/bin/receive?sling:authRequestLogin=1&amp;binaryless=true*

1. Starten Sie alle Autoren- und Veröffentlichungsinstanzen neu, damit die Änderungen wirksam werden.

### Erstellen eines Clusters mit S3 und MongoDB {#creating-a-cluster-using-s-and-mongodb}

1. Entpacken Sie den CQ-Schnellstart mit dem folgenden Befehl:

   `java -jar cq-quickstart.jar -unpack`

1. Nachdem AEM entpackt wurde, erstellen Sie einen Ordner im Installationsverzeichnis *crx-quickstart*/*install*.

1. Erstellen Sie diese beiden Dateien im Ordner `crx-quickstart`:

   * *org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService*.*config*
   * *org.apache.jackrabbit.oak.plugins.blob.datastore.S3DataStore*.*config*

   Nachdem die Dateien erstellt wurden, fügen Sie die Konfigurationsoptionen nach Bedarf hinzu.

1. Installieren Sie die beiden Pakete, die für den S3-Datenspeicher erforderlich sind, wie oben beschrieben.
1. Stellen Sie sicher, dass MongoDB installiert ist und eine `mongod`-Instanz ausgeführt wird.
1. Starten Sie AEM mit dem folgenden Befehl:

   `java -Xmx1024m -XX:MaxPermSize=256M -jar cq-quickstart.jar -r crx3,crx3mongo`

1. Wiederholen Sie die Schritte 1 bis 4 für die zweite AEM.
1. Starten Sie die zweite AEM.

#### Konfigurieren eines freigegebenen Datenspeichers {#configuring-a-shared-data-store}

1. Erstellen Sie zunächst die Konfigurationsdatei für den Datenspeicher auf allen Instanzen, die zum Freigeben des Datenspeichers erforderlich sind:

   * Wenn Sie einen `FileDataStore` verwenden, erstellen Sie eine Datei mit dem Namen `org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config` und legen Sie diese im Ordner `<aem-install>/crx-quickstart/install` ab.
   * Wird S3 als Datenspeicher verwendet, erstellen Sie eine Datei mit dem Namen `rg.apache.jackrabbit.oak.plugins.blob.datastore.S3DataStore.config` im Ordner `<aem-install>/crx-quickstart/install`, wie oben erläutert.

1. Ändern Sie die Konfigurationsdateien des Datenspeichers in jeder Instanz so, dass sie auf denselben Datenspeicher verweisen. Weitere Informationen finden Sie unter [diesem Artikel](/help/sites-deploying/data-store-config.md#data-store-configurations).
1. Wenn die Instanz von einem vorhandenen Server geklont wurde, müssen Sie die `clusterId` der neuen Instanz mit dem neuesten oak-run-Tool entfernen, während das Repository offline ist. Hierzu muss der folgende Befehl ausgeführt werden:

   ```xml
   java -jar oak-run.jar resetclusterid < repository path | Mongo URI >
   ```

   >[!NOTE]
   >
   >Wenn ein Knotenspeicher „Segment“ konfiguriert ist, muss der Repositorypfad angegeben werden. Standardmäßig lautet der Pfad `<aem-install-folder>/crx-quickstart/repository/segmentstore.`. Ist ein Knotenspeicher „Dokument“ konfiguriert, können Sie einen [URI im Format einer Mongo-Verbindungszeichenfolge](https://docs.mongodb.org/manual/reference/connection-string/) verwenden.

   >[!NOTE]
   >
   >Das oak-run-Tool kann über diese Adresse heruntergeladen werden:
   >
   >[https://mvnrepository.com/artifact/org.apache.jackrabbit/oak-run/](https://mvnrepository.com/artifact/org.apache.jackrabbit/oak-run/)
   >
   >Denken Sie daran, dass abhängig von der Oak-Version in der AEM-Installation verschiedene Toolversionen verwenden werden müssen. Bitte überprüfen Sie die nachstehende Liste der Versionsvoraussetzungen , bevor Sie das Tool verwenden:
   >
   >* Setzen Sie für die Oak-Versionen **1.2.x** das oak-run-Tool der Version **1.2.12 oder höher** ein.
   >* Für **neuere** Oak-Versionen verwenden Sie die oak-run-Version, die dem Oak-Core der AEM-Installation entspricht.


1. Validieren Sie abschließend die Konfiguration. Dazu müssen Sie nach einer eindeutigen Datei suchen, die dem Datenspeicher von jedem Repository hinzugefügt wird, das ihn weitergibt. Das Format der Dateien ist `repository-[UUID]`, wobei die UUID für eine eindeutige Kennung jedes Repositorys steht.

   Daher sollte eine ordnungsgemäße Konfiguration so viele eindeutige Dateien enthalten wie Repositorys, die den Datenspeicher gemeinsam nutzen.

   Die Dateien werden je nach Datenspeicher unterschiedlich gespeichert:

   * Für den `FileDataStore` werden die Dateien unter dem Stammverzeichnis des Datenspeicherordners erstellt.
   * Für den `S3DataStore` werden die Dateien im konfigurierten S3-Bucket unter dem `META`-Ordner erstellt.

## Azure-Datenspeicher {#azure-data-store}

AEM können so konfiguriert werden, dass Daten im Azure-Speicherdienst von Microsoft gespeichert werden. Zur Konfiguration wird die PID `org.apache.jackrabbit.oak.plugins.blob.datastore.AzureDataStore.config` verwendet.

Zur Aktivierung der Azure-Datenspeicherfunktionalität muss ein Feature Pack mit dem Azure-Datenspeicher-Connector heruntergeladen und installiert werden. Gehen Sie zum [Adobe-Repository](https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.azureblobconnector/) und laden Sie die neueste Version der 1.6.x-Versionen des Feature Packs herunter (z. B. com.adobe.granite.oak.azureblobconnector-1.6.3.zip).

>[!NOTE]
>
>Bei Verwendung von AEM 6.4 mit TarMK werden die Binärdateien standardmäßig im FileDataStore gespeichert. Um TarMK mit dem Azure-Datenspeicher nutzen zu können, müssen Sie AEM mithilfe des `crx3tar-nofds`-Ausführungsmodus starten, z. B.:

```shell
java -jar aem6.4.jar -r crx3tar-nofds
```

Nach dem Download können Sie den Azure-Connector wie folgt installieren und konfigurieren:

1. Extrahieren Sie den Inhalt der ZIP-Datei des Feature Packs in einen temporären Ordner.

1. Gehen Sie zum temporären Ordner und kopieren Sie den Inhalt von `jcr_root/libs/system/install` in den Ordner `<aem-install>crx-quickstart/install`.
1. Wenn AEM bereits für Tar- oder MongoDB-Speicher konfiguriert ist, entfernen Sie etwaig vorhandene Konfigurationsdateien aus dem Ordner `/crx-quickstart/install`, bevor Sie fortfahren. Die folgenden Dateien müssen entfernt werden:

   FürMongoMK:

   `org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService.config`

   Für TarMK:

   `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config`

1. Kehren Sie zu dem temporären Verzeichnis mit dem extrahierten Feature Pack zurück und kopieren Sie den Inhalt von `jcr_root/libs/system/config` in den Ordner `<aem-install>/crx-quickstart/install`.
1. Bearbeiten Sie die Konfigurationsdatei und fügen Sie die für Ihr Setup erforderlichen Konfigurationsoptionen hinzu.
1. Starten Sie AEM.

Sie können die Konfigurationsdatei mit den folgenden Optionen verwenden:

* azureSas=&quot;&quot;: In der Connector-Version 1.6.3 wurde Unterstützung für Azure Shared Access Signature (SAS) hinzugefügt. **Wenn in der Konfigurationsdatei sowohl SAS als auch Speicheranmeldeinformationen vorhanden sind, hat SAS Priorität.** Weitere Informationen zu SAS finden Sie in der [offiziellen Dokumentation](https://docs.microsoft.com/de-de/azure/storage/common/storage-dotnet-shared-access-signature-part-1). Stellen Sie sicher, dass &#39;=&#39; wie folgt mit Escapezeichen versehen ist &#39;\=&#39;.

* azureBlobEndpoint=&quot;&quot;: Der Azure-Blob-Endpunkt, z. B. https://&lt;Speicherkonto>.blob.core.windows.net.
* accessKey=&quot;&quot;: Der Speicherkontoname. Weitere Informationen zu den von Microsoft Azure-Anmeldeinformationen für die Authentifizierung finden Sie in der [offiziellen Dokumentation](https://azure.microsoft.com/de-de/documentation/articles/storage-create-storage-account).

* secretKey=&quot;&quot;: Der Speicherzugriffsschlüssel. Stellen Sie sicher, dass &#39;=&#39; wie folgt mit Escapezeichen versehen ist &#39;\=&#39;.
* container=&quot;&quot;: Der Name des Microsoft Azure Blob Storage-Containers. Der Container ist eine Gruppierung einer Gruppe von Blobs. Weitere Informationen finden Sie im Abschnitt [amtliche Dokumentation](https://msdn.microsoft.com/de-DE/library/dd135715.aspx).
* maxConnections=&quot;&quot;: Die gleichzeitige Anzahl gleichzeitiger Anfragen pro Vorgang. Der Standardwert lautet 1.
* maxErrorRetry=&quot;&quot;: Die Anzahl der Wiederholungen pro Anfrage. Der Standardwert lautet 3.
* socketTimeout=&quot;&quot;: Das Zeitüberschreitungsintervall, in Millisekunden, für die Anfrage. Der Standardwert lautet 5 Minuten.

Neben den oben aufgeführten Einstellungen können auch die folgenden Einstellungen konfiguriert werden:

* path: Der Pfad des Datenspeichers. Standard: `<aem-install>/repository/datastore.`
* RecordLength: Die Mindestgröße eines Objekts, das im Datenspeicher gespeichert werden soll. Der Standardwert lautet 16 KB.
* maxCachedBinarySize: Binärdateien, die kleiner als oder gleich diesem Wert sind, werden im Speichercache gespeichert. Die Größe wird in Byte angegeben. Der Standardwert lautet 17408 (17 KB).
* cacheSize: Die Größe des Cache. Der Wert wird in Byte angegeben. Der Standardwert lautet 64 GB.
* secret: Darf nur bei einer nicht binären Replikation für freigegebene Datenspeicher verwendet werden.
* stagingSplitPercentage: Der Prozentsatz der Cachegröße, der zum Staging asynchroner Uploads konfiguriert ist. Der Standardwert lautet 10.
* uploadThreads: Die Anzahl der Uploadthreads für asynchrone Uploads. Der Standardwert lautet 10.
* stagingPurgeInterval: Das Intervall in Sekunden zum endgültigen Löschen abgeschlossener Uploads aus dem Staging-Cache. Der Standardwert lautet 300 Sekunden (5 Minuten).
* stagingRetryInterval: Das Wiederholungsintervall in Sekunden für fehlgeschlagene Uploads. Der Standardwert lautet 600 Sekunden (10 Minuten).

>[!NOTE]
>
>Alle Einstellungen sollten in Anführungszeichen gesetzt werden, z. B.:

```shell
accessKey="ASDASDERFAERAER"
secretKey="28932hfjlkwdo8fufsdfas\=\="
```

## Automatische Datenspeicherbereinigung {#data-store-garbage-collection}

Im Rahmen der automatischen Datenspeicherbereinigung werden nicht verwendete Dateien aus dem Datenspeicher entfernt. Dabei wird wertvoller Festplattenspeicher freigegeben.

Sie können die automatische Datenspeicherbereinigung wie folgt ausführen:

1. Rufen Sie die JMX-Konsole unter der folgenden Adresse auf: *https://&lt;Server-Adresse:Port>/system/console/jmx*
1. Suchen nach **RepositoryManagement.** Sobald Sie das MBean &quot;Repository Manager&quot;gefunden haben, klicken Sie darauf, um die verfügbaren Optionen aufzurufen.
1. Scrollen Sie zum Ende der Seite und klicken Sie auf die Schaltfläche **startDataStoreGC(boolean markOnly)** Link.
1. Geben Sie im folgenden Dialogfeld für den Parameter `false` den Wert `markOnly` ein und klicken Sie auf **Invoke**:

   ![chlimage_1-122](assets/chlimage_1-122.png)

   >[!NOTE]
   >
   >Der Parameter `markOnly` gibt an, ob die Sweeping-Phase der automatischen Bereinigung ausgeführt wird oder nicht.

## Datenspeicherbereinigung für einen freigegebenen Datenspeicher {#data-store-garbage-collection-for-a-shared-data-store}

>[!NOTE]
>
>Wenn Sie die automatische Bereinigung für einen eingerichteten Cluster- oder freigegebenen Speicher (mit Mongo oder Segment-Tar) durchführen, werden im Protokoll möglicherweise Warnungen angezeigt, wonach bestimmte Blob-IDs nicht gelöscht werden können. Dies geschieht, weil während einer vorherigen automatischen Bereinigung gelöschte Blob-IDs fälschlicherweise erneut von anderen Cluster- oder Freigabeknoten referenziert werden, denen die Informationen zu den ID-Löschungen fehlen. Daher wird bei der automatischen Bereinigung eine Warnung protokolliert, wenn versucht wird, eine bereits im vorherigen Durchgang gelöschte ID zu entfernen. Dieses Verhalten hat keine Auswirkungen auf die Leistung oder Funktionalität.

In neueren AEM-Versionen kann die automatische Datenspeicherbereinigung auch in einem Datenspeicher durchgeführt werden, der von mehreren Repositorys genutzt wird. Für eine automatische Datenspeicherbereinigung in einem freigegebenen Datenspeicher führen Sie die folgenden Schritte aus:

1. Stellen Sie sicher, dass alle für die Datenspeicherbereinigung konfigurierten Wartungsaufgaben auf allen Repository-Instanzen, die den Datenspeicher gemeinsam nutzen, deaktiviert sind.
1. Führen Sie die unter [Binäre Speicherbereinigung](/help/sites-deploying/data-store-config.md#data-store-garbage-collection) einzeln auf **all** Repository-Instanzen, die den Datenspeicher gemeinsam nutzen. Achten Sie jedoch darauf, den Wert `true` für den Parameter `markOnly` einzugeben, bevor Sie auf die Schaltfläche „Invoke“ klicken:

   ![chlimage_1-123](assets/chlimage_1-123.png)

1. Führen Sie nach Abschluss des obigen Verfahrens auf allen Instanzen die Datenspeicherbereinigung erneut aus. **any** der Instanzen:

   1. Wechseln Sie zur JMX-Konsole und wählen Sie das MBean Repository Manager aus.
   1. Klicken Sie auf **Klicken Sie auf startDataStoreGC(boolean markOnly)** Link.
   1. Geben Sie im folgenden Dialogfeld für den Parameter `false` erneut den Wert `markOnly` ein.
   Hierdurch werden alle in der zuvor verwendeten Markierungsphase gefundenen Dateien ausgeblendet und die restlichen nicht verwendeten Dateien werden aus dem Datenspeicher gelöscht.
