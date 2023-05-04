---
title: AEM mit MongoDB
seo-title: AEM with MongoDB
description: Erfahren Sie mehr über die Aufgaben und Überlegungen, die für eine erfolgreiche AEM mit der MongoDB-Bereitstellung erforderlich sind.
seo-description: Learn about the tasks and considerations needed for a successful AEM with MongoDB deployment.
uuid: 51c463aa-d467-4857-8fff-e5f81d694145
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 3c59ec8f-b72f-48dd-bac8-9817005ae210
exl-id: 8397352a-51b0-4d03-a72d-19f7da58c07e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '6531'
ht-degree: 32%

---

# AEM mit MongoDB{#aem-with-mongodb}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Dieser Artikel soll das Wissen über Aufgaben und Überlegungen verbessern, die für eine erfolgreiche Bereitstellung von Adobe Experience Manager mit MongoDB erforderlich sind.

Weitere Informationen zur Bereitstellung finden Sie im Abschnitt [Bereitstellung und Wartung](/help/sites-deploying/deploy.md) Abschnitt der Dokumentation.

## Verwendung von MongoDB mit AEM {#when-to-use-mongodb-with-aem}

MongoDB wird normalerweise zur Unterstützung AEM Autorenbereitstellungen verwendet, wenn eines der folgenden Kriterien erfüllt ist:

* mehr als 1000 Unique Users pro Tag;
* mehr als 100 gleichzeitige Benutzer;
* Hohe Anzahl von Seitenbearbeitungen;
* Große Rollouts oder Aktivierungen.

Die oben genannten Kriterien gelten nur für die Autoreninstanzen und nicht für Veröffentlichungsinstanzen, die alle auf TarMK basieren sollten. Die Anzahl der Benutzer bezieht sich auf authentifizierte Benutzer, da Autoreninstanzen keinen nicht authentifizierten Zugriff zulassen.

Wenn die Kriterien nicht erfüllt sind, wird eine aktive/Standby-Bereitstellung von TarMK/TarMK empfohlen, um die Verfügbarkeit zu verbessern. Im Allgemeinen sollte MongoDB in Situationen berücksichtigt werden, in denen die Skalierungsanforderungen größer sind als mit einem einzelnen Hardwareelement möglich.

>[!NOTE]
>
>Weitere Informationen zur Größenanpassung von Autoreninstanzen und zur Definition gleichzeitiger Benutzer finden Sie in der [Richtlinien zur Hardware-Skalierung](/help/managing/hardware-sizing-guidelines.md#authors-working-in-parallel).

### Minimale MongoDB-Bereitstellung für AEM {#minimal-mongodb-deployment-for-aem}

Nachfolgend finden Sie eine minimale Bereitstellung für AEM auf MongoDB. Zur Vereinfachung wurden SSL-Terminierung und HTTP-Proxy-Komponenten verallgemeinert. Die Bereitstellung besteht aus einer einzigen MongoDB-Replikatgruppe mit einem primären Replikat und zwei sekundären Replikaten.

![chlimage_1-94](assets/chlimage_1-94.png)

Eine minimale Bereitstellung setzt voraus, dass 3 `mongod`-Instanzen als Replikatgruppe konfiguriert sind. Eine Instanz wird als primäres Replikat gewählt, die beiden anderen sind sekundäre Replikate; die Wahl wird von `mongod` verwaltet. Angebunden an jede Instanz ist eine lokale Festplatte. Damit der Cluster die Last bewältigen kann, wird ein Mindestdurchsatz von 12 MB/s mit mehr als 3.000 IOPS (I/O Operations per Second) empfohlen.

Die AEM-Autoren sind mit den `mongod`-Instanzen verbunden, wobei jeweils eine Verbindung zu allen drei `mongod`-Instanzen besteht. Schreibvorgänge werden an die primäre Instanz gesendet und Lesevorgänge können von jeder der Instanzen gelesen werden. Der Traffic wird basierend auf dem Laden durch einen Dispatcher an eine der aktiven AEM Autoreninstanzen verteilt. Der Oak-Datenspeicher ist ein `FileDataStore` und die MongoDB-Überwachung erfolgt je nach Bereitstellungsort über MMS oder MongoDB Ops Manager. Die Betriebssystemebene und die Protokollüberwachung werden von Lösungen von Drittanbietern wie Splunk oder Ganglia bereitgestellt.

In dieser Bereitstellung sind alle Komponenten für eine erfolgreiche Implementierung erforderlich. Jede fehlende Komponente lässt die Implementierung nicht funktionsfähig.

### Betriebssysteme {#operating-systems}

Eine Aufstellung der unterstützten Betriebssysteme für AEM 6 finden Sie auf der Seite [Technische Anforderungen](/help/sites-deploying/technical-requirements.md).

### Umgebungen {#environments}

Virtualisierte Umgebungen werden unterstützt, sofern eine gute Kommunikation zwischen den verschiedenen technischen Teams besteht, die das Projekt durchführen. Dazu gehören das Team, das AEM ausführt, das Team, dem das Betriebssystem gehört, und das Team, das die virtualisierte Infrastruktur verwaltet.

Es gibt spezifische Anforderungen an die I/O-Kapazität der MongoDB-Instanzen, die vom Team verwaltet werden müssen, das die virtualisierte Umgebung verwaltet. Wenn das Projekt eine Cloud-Implementierung wie Amazon Web Services nutzt, müssen die Instanzen mit ausreichender I/O-Kapazität und Konsistenz bereitgestellt werden, um die MongoDB-Instanzen zu unterstützen. Andernfalls werden die MongoDB-Prozesse und das Oak-Repository unzuverlässig und fehlerhaft ausgeführt.

In den virtualisierten Umgebungen erfordert MongoDB spezifische I/O- und VM-Konfigurationen, um sicherzustellen, dass die Speicher-Engine von MongoDB nicht durch VMWare-Richtlinien zur Ressourcenzuordnung beeinträchtigt wird. Durch eine erfolgreiche Implementierung wird sichergestellt, dass es keine Hindernisse zwischen den verschiedenen Teams gibt und alle sich für die erforderliche Leistung angemeldet haben.

## Hardwareaspekte {#hardware-considerations}

### Speicherung {#storage}

Um den Lese- und Schreibdurchsatz für eine optimale Leistung ohne vorzeitige horizontale Skalierung zu erreichen, benötigt MongoDB im Allgemeinen SSD-Speicher oder -Speicher mit einer SSD-gleichwertigen Leistung.

### RAM {#ram}

MongoDB-Versionen 2.6 und 3.0, die die MMAP-Speicher-Engine verwenden, erfordern, dass der Arbeitssatz der Datenbank und deren Indizes in RAM passen.

Unzureichender RAM führt zu einer deutlichen Leistungsminderung. Die Größe des Workflows und der Datenbank hängt stark von der Anwendung ab. Während einige Schätzungen vorgenommen werden können, ist die zuverlässigste Methode, die erforderliche RAM-Menge zu bestimmen, die Erstellung der AEM-Anwendung und die Belastungsprüfung.

Um den Lasttest zu unterstützen, kann das folgende Verhältnis zwischen Arbeitssatz und Gesamtdatenbankgröße angenommen werden:

* 1:10 für SSD-Speicher
* 1:3 für Festplattenspeicher

Dies bedeutet, dass im Falle von SSD-Bereitstellungen für eine 2 TB große Datenbank 200 GB RAM erforderlich sind.

Die gleichen Einschränkungen gelten für das WiredTiger-Speichermodul in MongoDB 3.0, aber die Korrelation zwischen Arbeitsset, RAM und Seitenfehlern ist nicht so stark, da WiredTiger die Speicherzuordnung nicht auf die gleiche Weise wie die MMAP-Speichermodul verwendet.

>[!NOTE]
>
>Adobe empfiehlt die Verwendung der WiredTiger-Speicher-Engine für AEM 6.1-Bereitstellungen, die MongoDB 3.0 verwenden.

### Datenspeicher {#data-store}

Aufgrund der Beschränkungen des MongoDB-Workingsets wird empfohlen, den Datenspeicher unabhängig von MongoDB zu verwalten. In den meisten Umgebungen sollte ein für alle AEM-Instanzen verfügbarer `FileDataStore` mit einem NAS verwendet werden. Wird Amazon Web Services genutzt, steht auch ein `S3 DataStore` zur Verfügung. Wenn der Datenspeicher aus irgendeinem Grund innerhalb von MongoDB verwaltet wird, sollte die Größe des Datenspeichers der gesamten Datenbankgröße hinzugefügt und die Berechnungen des Arbeitssatzes entsprechend angepasst werden. Dies kann bedeuten, dass deutlich mehr RAM bereitgestellt wird, um die Leistung ohne Seitenfehler zu halten.

## Überwachung {#monitoring}

Überwachung ist für eine erfolgreiche Umsetzung des Projekts von entscheidender Bedeutung. Mit ausreichend Wissen ist es zwar möglich, ohne Überwachung AEM MongoDB auszuführen, aber diese Kenntnisse werden normalerweise in Ingenieuren vermittelt, die für jeden Abschnitt der Implementierung spezialisiert sind.

Dazu gehören in der Regel ein F&amp;E-Techniker, der am Apache Oak Core arbeitet, und ein MongoDB-Spezialist.

Ohne Überwachung auf allen Ebenen ist eine detaillierte Kenntnis der Codebasis erforderlich, um Probleme zu diagnostizieren. Mit einer Überwachung und geeigneten Leitlinien zu den wichtigsten Statistiken können Implementierungsteams angemessen auf Anomalien reagieren.

Es ist zwar möglich, Befehlszeilen-Tools zu verwenden, um einen schnellen Überblick über den Betrieb eines Clusters zu erhalten, doch ist es fast unmöglich, dies in Echtzeit über viele Hosts durchzuführen. Befehlszeilenwerkzeuge geben nur selten historische Informationen nach einigen Minuten zurück und ermöglichen nie eine Kreuzkorrelation zwischen verschiedenen Metriktypen. Ein kurzer Zeitraum langsamer `mongod`-Hintergrundsynchronisierungen bedeutet zusätzlichen manuellen Aufwand, um I/O-Wartezeiten oder übermäßige Write-Level mit einer freigegebenen Speicherressource von einer scheinbar nicht verbundenen virtuellen Maschine in Beziehung zu setzen.

### MongoDB Cloud Manager {#mongodb-cloud-manager}

MongoDB Cloud Manager ist ein kostenloser Dienst von MongoDB, der die Überwachung und Verwaltung von MongoDB-Instanzen ermöglicht. Es bietet einen Überblick über die Leistung und den Zustand des MongoDB-Clusters in Echtzeit. Es verwaltet sowohl Cloud- als auch privat gehostete Instanzen, sofern die Instanz den Cloud Manager-Überwachungsserver erreichen kann.

Voraussetzung ist die Installation eines Agenten auf der MongoDB-Instanz, der mit dem Überwachungsserver verbunden ist. Es gibt drei Stufen des Erregers:

* Ein Automatisierungsagent, der alles auf dem MongoDB-Server vollständig automatisieren kann,
* Einen Überwachungsagenten, der die `mongod`-Instanz überwachen kann
* Ein Backup-Agent, der geplante Sicherungen der Daten durchführen kann.

Obwohl die Verwendung von Cloud Manager zur Wartungsautomatisierung eines MongoDB-Clusters viele der Routineaufgaben vereinfacht, ist dies nicht erforderlich und wird auch nicht für die Sicherung verwendet. Bei der Wahl von Cloud Manager zur Überwachung ist jedoch eine Überwachung erforderlich.

Weitere Informationen zu MongoDB Cloud Manager finden Sie in der [MongoDB-Dokumentation](https://docs.mongodb.com/).

### MongoDB Ops Manager {#mongodb-ops-manager}

MongoDB Ops Manager ist dieselbe Software wie MongoDB Cloud Manager. Nach der Registrierung kann Ops Manager lokal in einem privaten Rechenzentrum oder auf einem anderen Laptop oder Desktop-Computer heruntergeladen und installiert werden. Es verwendet eine lokale MongoDB-Datenbank, um Daten zu speichern und auf dieselbe Weise wie Cloud Manager mit den verwalteten Servern zu kommunizieren. Wenn Sie Sicherheitsrichtlinien haben, die einen Überwachungsagenten verbieten, sollte MongoDB Ops Manager verwendet werden.

### Betriebssystemüberwachung {#operating-system-monitoring}

Zum Ausführen eines AEM MongoDB-Clusters ist eine Überwachung auf Betriebssystemebene erforderlich.

Ganglia ist ein gutes Beispiel für ein solches System und liefert ein Bild über die Bandbreite und Details der benötigten Informationen, die über grundlegende Gesundheitsmetriken wie CPU, Lastdurchschnitt und freien Speicherplatz hinausgehen. Um Probleme zu diagnostizieren, sind niedrigere Informationen wie Entropy-Pool-Ebenen, CPU-I/O-Wartezeit, Sockets im FIN_WAIT2-Status erforderlich.

### Logaggregate {#log-aggregation}

Bei einem Cluster aus mehreren Servern ist die zentrale Protokollaggregation eine Voraussetzung für ein Produktionssystem. Software wie Splunk unterstützt die Protokollierung und ermöglicht es Teams, Verhaltensmuster der Anwendung zu analysieren, ohne die Protokolle manuell erfassen zu müssen.

## Checklisten {#checklists}

In diesem Abschnitt werden die verschiedenen Schritte beschrieben, die Sie unternehmen sollten, um sicherzustellen, dass Ihre AEM- und MongoDB-Bereitstellungen vor der Implementierung Ihres Projekts ordnungsgemäß eingerichtet sind.

### Netzwerk {#network}

1. Stellen Sie zunächst sicher, dass alle Hosts einen DNS-Eintrag haben.
1. Alle Hosts sollten durch ihren DNS-Eintrag von allen anderen routbaren Hosts aufgelöst werden können
1. Alle MongoDB-Hosts sind von allen anderen MongoDB-Hosts im selben Cluster routbar
1. MongoDB-Hosts können Pakete an MongoDB Cloud Manager und die anderen Überwachungsserver weiterleiten
1. AEM Server können Pakete an alle MongoDB-Server weiterleiten
1. Die Paketlatenz zwischen einem beliebigen AEM-Server und einem MongoDB-Server ist kleiner als zwei Millisekunden, ohne Paketverlust und mit einer Standardverteilung von einer Millisekunde oder weniger.
1. Stellen Sie sicher, dass zwischen einem AEM und einem MongoDB-Server nicht mehr als zwei Hopfen vorhanden sind.
1. Zwischen zwei MongoDB-Servern gibt es nicht mehr als zwei Hopfen
1. Es gibt keine Router, die höher sind als OSI Level 3 zwischen Kernservern (MongoDB oder AEM oder einer Kombination).
1. Wenn VLAN-Trunking oder eine Netzwerktunnelung verwendet wird, muss es den Paketlatenzprüfungen entsprechen.

### AEM {#aem-configuration}

#### Knotenspeicherkonfiguration {#node-store-configuration}

Die AEM Instanzen müssen für die Verwendung von AEM mit MongoMK konfiguriert werden. Die Grundlage der MongoMK-Implementierung in AEM ist der Document Node Store.

Weitere Informationen zum Konfigurieren von Knotenspeichern finden Sie unter [Konfigurieren von Knotenspeichern und Datenspeichern in AEM](/help/sites-deploying/data-store-config.md).

Nachfolgend finden Sie ein Beispiel für die Konfiguration des Knotenspeichers für eine minimale MongoDB-Bereitstellung:

```xml
# org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService.config

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
#MongoDB server details
mongodburi=mongodb://aem:aempassword@mongodbserver1.customer.com:27000,mongodbserver2.customer.com:27000
  
#Name of MongoDB database to use
db=aem
  
#Store binaries in custom BlobStore e.g. FileDataStore
customBlobStore=true
  
cache=2048
blobCacheSize=1024
```

Dabei gilt:

* `mongodburi`

   Der MongoDB-Server, zu dem AEM eine Verbindung herstellen muss. Verbindungen werden zu allen bekannten Mitgliedern des standardmäßigen Replikatsatzes hergestellt. Wenn MongoDB Cloud Manager verwendet wird, ist die Serversicherheit aktiviert. Folglich muss die Verbindungszeichenfolge einen geeigneten Benutzernamen und ein passendes Kennwort enthalten. Nicht-Enterprise-Versionen von MongoDB unterstützen nur die Authentifizierung von Benutzernamen und Passwörtern. Weitere Informationen zur Syntax der Verbindungszeichenfolge finden Sie im Abschnitt [Dokumentation](https://docs.mongodb.org/manual/reference/connection-string/).

* `db`

   Der Name der Datenbank. Der Standardwert für AEM lautet `aem-author`.

* `customBlobStore`

   Wenn Binärdateien im Zuge der Bereitstellung in der Datenbank gespeichert werden, werden sie Teil des Workingsets. Aus diesem Grund wird empfohlen, keine Binärdateien in MongoDB zu speichern und einen alternativen Datenspeicher wie einen `FileSystem` Datenspeicher auf einem NAS.

* `cache`

   Die Cachegröße in Megabyte. Dieser Wert ist verteilt über diverse Cache-Speicher im `DocumentNodeStore`. Die Standardgröße ist 256 MB. Die Oak-Leseleistung profitiert jedoch von einem größeren Cache.

* `blobCacheSize`

   Häufig verwendete Blobs können von AEM im Cache gespeichert werden. So wird vermieden, dass sie erneut aus dem Datenspeicher abgerufen werden. Dies wirkt sich stärker auf die Leistung aus, insbesondere beim Speichern von Blobs in der MongoDB-Datenbank. Alle dateisystembasierten Datenspeicher profitieren vom Datenträgercache auf Betriebssystemebene.

#### Datenspeicherkonfiguration {#data-store-configuration}

Der Datenspeicher dient zum Speichern von Dateien mit einer Größe, die größer als ein Schwellenwert ist. Unter diesem Schwellenwert werden Dateien als Eigenschaften im Knotenspeicher &quot;Dokument&quot;gespeichert. Wenn der `MongoBlobStore` verwendet wird, wird in MongoDB eine dedizierte Sammlung zum Speichern der Blobs erstellt. Diese Sammlung trägt zum Workingset der `mongod`-Instanz bei und setzt eine höhere RAM-Menge für die `mongod`-Instanz voraus, um Leistungsprobleme zu vermeiden. Daher wird für Konfigurationen empfohlen, in Produktionsbereitstellungen auf `MongoBlobStore` zu verzichten und einen `FileDataStore` einzusetzen, der von einem von allen AEM-Instanzen genutzten NAS gestützt wird. Da der Cache auf Betriebssystemebene eine effiziente Verwaltung von Dateien ermöglicht, sollte die Mindestgröße einer Datei auf der Festplatte auf einen Wert eingestellt werden, der der Blockgröße der Festplatte nahekommt. So kann das Dateisystem effizient verwendet werden und das Workingset der `mongod`-Instanz wird nicht durch eine große Anzahl kleiner Dokumente übermäßig belastet.

Es folgt ein Beispiel einer typischen Datenspeicherkonfiguration für eine minimale AEM-Bereitstellung mit MongoDB:

```xml
# org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
# The minimum size of an object that should be stored in this data store.

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
minRecordLength=4096
path=/datastore
maxCachedBinarySize=4096
cacheSizeInMB=128
```

Dabei gilt:

* `minRecordLength`

   Größe in Byte. Binärdateien, die kleiner oder gleich dieser Größe sind, werden mit dem Document Node Store gespeichert. Anstatt die Kennung des Blob zu speichern, wird der Inhalt der Binärdatei gespeichert. Bei Binärdateien, die größer sind als dieser Wert, wird die ID der Binärdatei als Eigenschaft des Dokuments in der Knotensammlung gespeichert und der Hauptteil der Binärdatei wird gespeichert im `FileDataStore` auf der Festplatte. 4096 Byte entspricht einer typischen Dateisystem-Blockgröße.

* `path`

   Der Pfad zum Stamm des Datenspeichers. Bei einer MongoMK-Bereitstellung muss es sich um ein freigegebenes Dateisystem handeln, das für alle AEM Instanzen verfügbar ist. Normalerweise wird ein NAS-Server (Network Attached Storage) verwendet. Bei Cloud-Implementierungen wie Amazon Web Services ist der `S3DataFileStore` ebenfalls verfügbar.

* `cacheSizeInMB`

   Die Gesamtgröße des Binärdatencache in Megabyte. Sie wird verwendet, um Binärdateien zwischenzuspeichern, die kleiner sind als die `maxCacheBinarySize` -Einstellung.

* `maxCachedBinarySize`

   Die maximale Größe in Byte der im Binärdatencache gespeicherten Binärdatei. Wenn ein dateisystembasierter Datenspeicher verwendet wird, wird die Verwendung hoher Werte für den Datenspeicher-Cache nicht empfohlen, da die Binärdateien bereits vom Betriebssystem zwischengespeichert werden.

#### Deaktivieren des Abfragehinweises {#disabling-the-query-hint}

Es wird empfohlen, den mit allen Abfragen gesendeten Abfragehinweis zu deaktivieren, indem Sie die Eigenschaft

`-Doak.mongo.disableIndexHint=true`

beim Start AEM. Auf diese Weise berechnet MongoDB basierend auf internen Statistiken den am besten geeigneten Index.

Wenn der Abfragehinweis nicht deaktiviert ist, hat eine Leistungsoptimierung von Indizes keine Auswirkungen auf die Leistung von AEM.

#### Persistenten Cache für MongoMK aktivieren {#enable-persistent-cache-for-mongomk}

Es wird empfohlen, eine persistente Cache-Konfiguration für MongoDB-Bereitstellungen zu aktivieren, um die Geschwindigkeit für Umgebungen mit hoher I/O-Leseleistung zu maximieren. Weitere Informationen finden Sie unter [Jackrabbit Oak-Dokumentation](https://jackrabbit.apache.org/oak/docs/nodestore/persistent-cache.html).

## MongoDB-Betriebssystemoptimierungen {#mongodb-operating-system-optimizations}

### Betriebssystemunterstützung {#operating-system-support}

MongoDB 2.6 verwendet eine Speichermodul-Engine, die für einige Aspekte der Verwaltung auf Betriebssystemebene zwischen RAM und Datenträger sensibilisiert ist. Die Abfrage- und Leseleistung der MongoDB-Instanz beruht darauf, langsame I/O-Vorgänge, die häufig als Seitenfehler bezeichnet werden, zu vermeiden oder zu beseitigen. Hierbei handelt es sich um Seitenfehler, die insbesondere den `mongod`-Prozess betreffen. Sie sollten nicht mit Seitenfehlern auf Betriebssystemebene verwechselt werden.

Für einen schnellen Betrieb sollte die MongoDB-Datenbank nur auf Daten zugreifen, die sich bereits im RAM befinden. Die Daten, auf die sie zugreifen muss, bestehen aus Indizes und Daten. Diese Sammlung von Indizes und Daten wird als Arbeitssatz bezeichnet. Wenn der Arbeitssatz größer als der verfügbare RAM ist, muss MongoDB diese Daten von einem Datenträger eintragen, der I/O-Kosten verursacht, und andere Daten, die bereits im Speicher sind, entfernen. Wenn die Entfernung dazu führt, dass Daten von der Festplatte neu geladen werden, werden Seitenfehler dominieren und die Leistung wird beeinträchtigt. Wenn der Arbeitssatz dynamisch und variabel ist, treten mehr Seitenfehler auf, um Vorgänge zu unterstützen.

MongoDB läuft auf einer Reihe von Betriebssystemen, einschließlich einer Vielzahl von Linux-Versionen, Windows und Mac OS. Siehe [https://docs.mongodb.com/manual/installation/#supported-platforms](https://docs.mongodb.com/manual/installation/#supported-platforms) für weitere Details. Je nach Wahl Ihres Betriebssystems bietet MongoDB verschiedene Empfehlungen auf Betriebssystemebene. Die Dokumentation finden Sie unter [https://docs.mongodb.com/manual/administration/production-checklist-operations/#operating-system-configuration](https://docs.mongodb.com/manual/administration/production-checklist-operations/#operating-system-configuration) und zusammengefasst hier aus Gründen der Bequemlichkeit.

#### Linux {#linux}

* Deaktivieren Sie transparente hugepages und defrag. Siehe [Transparent Huge Pages Settings](https://docs.mongodb.com/manual/tutorial/transparent-huge-pages/) für weitere Informationen.
* [Anpassen der readahead-Einstellungen](https://docs.mongodb.com/manual/administration/production-notes/#readahead) auf den Geräten, auf denen Ihre Datenbankdateien gespeichert werden, entsprechend Ihrem Anwendungsfall.

   * Wenn für die MMAPv1-Speicher-Engine der verfügbare Arbeitsspeicher größer ist und das Zugriffsmuster für Dokumente zufällig ist, sollten Sie erwägen, die Vorausplanung auf 32 oder 16 zu reduzieren. Bewerten Sie verschiedene Einstellungen, um einen optimalen Wert zu finden, der den residenten Speicher maximiert und die Anzahl der Seitenfehler verringert.
   * Legen Sie für die WiredTiger-Speicher-Engine readahead auf 0 fest, unabhängig vom Speichermedientyp (Spinnen, SSD usw.). Verwenden Sie im Allgemeinen die empfohlene readahead-Einstellung, es sei denn, Tests zeigen einen messbaren, wiederholbaren und zuverlässigen Nutzen in einem höheren readahead-Wert. [MongoDB Professional Support](https://docs.mongodb.com/manual/administration/production-notes/#readahead) kann Ratschläge und Anleitungen zu readahead-Konfigurationen ungleich null geben.

* Deaktivieren Sie das angepasste Tool, wenn Sie RHEL 7/CentOS 7 in einer virtuellen Umgebung ausführen.
* Wenn RHEL 7/CentOS 7 in einer virtuellen Umgebung ausgeführt wird, ruft das angepasste Tool automatisch ein aus dem Leistungsdurchsatz abgeleitetes Leistungsprofil auf, das die readahead-Einstellungen automatisch auf 4 MB festlegt. Dies kann sich negativ auf die Leistung auswirken.
* Verwenden Sie die Noop- oder Deadline-Scheduler für SSD-Laufwerke.
* Verwenden Sie den noop Disk Scheduler für virtualisierte Laufwerke in Gast-VMs.
* NUMA deaktivieren oder vm.zone_reclaim_mode auf 0 setzen und ausführen [mongod](https://docs.mongodb.com/manual/administration/production-notes/#readahead) Instanzen mit Knotenwechselschaltung. Siehe: [MongoDB und NUMA Hardware](https://docs.mongodb.com/manual/administration/production-notes/#readahead) für weitere Informationen.

* Passen Sie die ulimit -Werte auf Ihrer Hardware an Ihren Anwendungsfall an. Wenn mehrere [mongod](https://docs.mongodb.com/manual/reference/program/mongod/#bin.mongod) oder [mongos](https://docs.mongodb.com/manual/reference/program/mongos/#bin.mongos) -Instanzen unter demselben Benutzer ausgeführt werden, skalieren Sie die ulimit -Werte entsprechend. Siehe: [UNIX ulimit Settings](https://docs.mongodb.com/manual/reference/ulimit/) für weitere Informationen.

* Verwenden Sie noatime für die [dbPath](https://docs.mongodb.com/manual/reference/configuration-options/#storage.dbPath) Einhängepunkt.
* Konfigurieren Sie ausreichende Dateigriffe (fs.file-max), die Pid-Grenze des Kernels (kernel.pid_max) und die maximalen Threads pro Prozess (kernel.threads-max) für Ihre Implementierung. Für große Systeme bieten die folgenden Werte einen guten Ausgangspunkt:

   * fs.file-max -Wert 98000,
   * kernel.pid_max -Wert von 64000,
   * andkernel.threads-max -Wert von 64000

* Stellen Sie sicher, dass auf Ihrem System der Austauschraum konfiguriert ist. Weitere Informationen zur geeigneten Größe finden Sie in der Dokumentation Ihres Betriebssystems .
* Vergewissern Sie sich, dass der standardmäßige TCP-Keepalive des Systems korrekt eingestellt ist. Der Wert 300 bietet häufig eine bessere Leistung für Replikatsätze und freigegebene Cluster. Siehe: [Beeinflusst die TCP-Lebensdauer MongoDB-Bereitstellungen?](https://docs.mongodb.com/manual/faq/diagnostics/#faq-keepalive) in den häufig gestellten Fragen für weitere Informationen.

#### Windows {#windows}

* Erwägen Sie, Aktualisierungen der &quot;letzten Zugriffszeit&quot;von NTFS zu deaktivieren. Dies entspricht der Deaktivierung von atime auf Unix-ähnlichen Systemen.

### WiredTiger {#wiredtiger}

Ab MongoDB 3.2 ist die standardmäßige Speichermodul-Engine für MongoDB die WiredTiger-Speicher-Engine. Diese Engine bietet eine Reihe robuster und skalierbarer Funktionen, wodurch sie für allgemeine Datenbankarbeitslasten wesentlich besser geeignet ist. Die folgenden Abschnitte beschreiben diese Funktionen.

#### Parallelität auf Dokumentebene {#document-level-concurrency}

WiredTiger verwendet die Parallelitätssteuerung auf Dokumentebene für Schreibvorgänge. Dadurch können mehrere Clients verschiedene Dokumente einer Sammlung gleichzeitig ändern.

Für die meisten Lese- und Schreibvorgänge verwendet WiredTiger eine optimistische Parallelitätssteuerung. WiredTiger verwendet nur Intent-Sperren auf globaler, Datenbank- und Sammlungsebene. Wenn das Speicher-Engine Konflikte zwischen zwei Vorgängen erkennt, entsteht ein Schreibkonflikt, der dazu führt, dass MongoDB diesen Vorgang transparent neu durchführt. Einige globale Vorgänge, normalerweise kurzlebige Vorgänge mit mehreren Datenbanken, erfordern weiterhin eine globale &quot;Instanzweite&quot;Sperre.

Für einige andere Vorgänge wie das Ablegen einer Sammlung ist weiterhin eine exklusive Datenbanksperre erforderlich.

#### Schnappschüsse und Checkpoints {#snapshots-and-checkpoints}

WiredTiger verwendet die MultiVersion Concurrency Control (MVCC). Zu Beginn eines Vorgangs liefert WiredTiger einen Point-in-Time-Schnappschuss der Daten für die Transaktion. Ein Snapshot zeigt eine konsistente Ansicht der Arbeitsspeicherdaten.

Beim Schreiben auf die Festplatte schreibt WiredTiger alle in einem Snapshot enthaltenen Daten konsistent über alle Datendateien auf die Festplatte. Die jetzt [permanenten](https://docs.mongodb.com/manual/reference/glossary/#term-durable) Daten dienen als Checkpoint in den Datendateien. Der Checkpoint stellt sicher, dass die Datendateien bis einschließlich des letzten Checkpoints konsistent sind. d. h. Checkpoints können als Wiederherstellungspunkte dienen.

MongoDB konfiguriert WiredTiger so, dass Checkpoints (d. h. das Schreiben der Momentaufnahmen-Daten auf die Festplatte) in Intervallen von 60 Sekunden oder 2 Gigabyte Journaldaten erstellt werden.

Während des Schreibens eines neuen Checkpoints ist der vorherige Checkpoint weiterhin gültig. Selbst wenn MongoDB beim Schreiben eines neuen Checkpoints beendet oder auf einen Fehler stößt, kann MongoDB nach dem Neustart vom letzten gültigen Checkpoint abgerufen werden.

Der neue Checkpoint wird verfügbar und dauerhaft, wenn die Metadatentabelle von WiredTiger automatisch aktualisiert wird, um auf den neuen Checkpoint zu verweisen. Sobald der neue Checkpoint verfügbar ist, gibt WiredTiger Seiten von den alten Checkpoints frei.

Verwenden von WiredTiger, auch ohne [Journaling](https://docs.mongodb.com/manual/reference/glossary/#term-durable), kann MongoDB vom letzten Checkpoint abgerufen werden. Um jedoch Änderungen wiederherzustellen, die nach dem letzten Checkpoint vorgenommen wurden, führen Sie mit [Journaling](https://docs.mongodb.com/manual/core/wiredtiger/#storage-wiredtiger-journal).

#### Journal {#journal}

WiredTiger verwendet ein Write-Ahead-Transaktionsprotokoll in Kombination mit [Checkpoints](https://docs.mongodb.com/manual/core/wiredtiger/#storage-wiredtiger-checkpoints), um die Dauerhaftigkeit der Daten sicherzustellen.

Das WiredTiger-Journal behält alle Datenänderungen zwischen Checkpoints bei. Wenn MongoDB zwischen Checkpoints beendet wird, verwendet es das Journal, um alle seit dem letzten Checkpoint geänderten Daten wiederzugeben. Informationen zur Häufigkeit, mit der MongoDB die Journaldaten auf die Festplatte schreibt, finden Sie unter [Journalprozess](https://docs.mongodb.com/manual/core/journaling/#journal-process).

Das WiredTiger-Journal wird mithilfe der [snappy](https://docs.mongodb.com/manual/core/journaling/#journal-process) Komprimierungsbibliothek. Verwenden Sie zum Angeben eines alternativen Komprimierungsalgorithmus oder einer Komprimierung die [storage.wiredTiger.engineConfig.journalCompressor](https://docs.mongodb.com/manual/reference/configuration-options/#storage.wiredTiger.engineConfig.journalCompressor) -Einstellung.

Weitere Informationen finden Sie unter [Journaling with WiredTiger](https://docs.mongodb.com/manual/core/journaling/#journaling-wiredtiger).

>[!NOTE]
>
>Die minimale Protokolldatensatzgröße für WiredTiger beträgt 128 Byte. Wenn ein Protokolldatensatz 128 Byte oder kleiner ist, komprimiert WiredTiger diesen Datensatz nicht.
>
>Sie können das Journal deaktivieren, indem Sie für [storage.journal.enabled](https://docs.mongodb.com/manual/reference/configuration-options/#storage.journal.enabled) „false“ festlegen. So können Sie den Mehraufwand für die Pflege des Journals verringern.
>
>Für [standalone](https://docs.mongodb.com/manual/reference/glossary/#term-standalone) -Instanzen nicht verwenden, bedeutet dies, dass Sie einige Datenänderungen verlieren, wenn MongoDB unerwartet zwischen Checkpoints beendet wird. Für Mitglieder von [Replikatsätze](https://docs.mongodb.com/manual/reference/glossary/#term-replica-set)kann der Replikationsprozess ausreichende Dauerhaltbarkeitsgarantien bieten.

#### Komprimierung {#compression}

Mit WiredTiger unterstützt MongoDB die Komprimierung für alle Sammlungen und Indizes. Die Komprimierung minimiert den Speicherverbrauch auf Kosten zusätzlicher CPU.

WiredTiger nutzt standardmäßig die Blockkomprimierung der [snappy](https://docs.mongodb.com/manual/reference/glossary/#term-snappy)-Komprimierungsbibliothek für alle Sammlungen und die [Präfixkomprimierung](https://docs.mongodb.com/manual/reference/glossary/#term-prefix-compression) für alle Indizes.

Blockkomprimierung für Sammlungen mit [zlib](https://docs.mongodb.com/manual/reference/glossary/#term-zlib) ist auch verfügbar. Verwenden Sie zum Angeben eines alternativen Komprimierungsalgorithmus oder einer Komprimierung die [storage.wiredTiger.collectionConfig.blockCompressor](https://docs.mongodb.com/manual/reference/glossary/#term-zlib) -Einstellung.

Die [Präfixkomprimierung](https://docs.mongodb.com/manual/reference/glossary/#term-prefix-compression) für Indizes können Sie mit der Einstellung [storage.wiredTiger.indexConfig.prefixCompression](https://docs.mongodb.com/manual/reference/configuration-options/#storage.wiredTiger.indexConfig.prefixCompression) deaktivieren.

Die Komprimierungseinstellungen können während der Sammlung- und Indexerstellung auch pro Sammlung und Index konfiguriert werden. Siehe [Festlegen der Speicher-Engine-Optionen](https://docs.mongodb.com/manual/reference/method/db.createCollection/#create-collection-storage-engine-options) und [db.collection.createIndex() storageEngine](https://docs.mongodb.com/manual/reference/method/db.collection.createIndex/#createindex-options) -Option.

Bei den meisten Arbeitslasten stimmen die Standardkomprimierungseinstellungen über die Speichereffizienz und die Verarbeitungsanforderungen ab.

Das WiredTiger-Journal wird ebenfalls standardmäßig komprimiert. Informationen zur Journalkomprimierung finden Sie unter [Protokoll](https://docs.mongodb.com/manual/core/wiredtiger/#storage-wiredtiger-journal).

#### Speichernutzung {#memory-use}

Mit WiredTiger nutzt MongoDB sowohl den internen Cache von WiredTiger als auch den Dateisystemcache.

Ab Version 3.4 verwendet der interne Cache von WiredTiger standardmäßig den größeren von:

* 50 % RAM minus 1 GB oder
* 256 MB

WiredTiger verwendet standardmäßig die Snappy-Blockkomprimierung für alle Sammlungen und die Präfixkomprimierung für alle Indizes. Die Komprimierungsstandardwerte können global konfiguriert werden und können während der Sammlung- und Indexerstellung auch pro Sammlung und Index festgelegt werden.

Für Daten im internen Cache von WiredTiger werden unterschiedliche Darstellungen verwendet, verglichen mit dem On-Disk-Format:

* Die Daten im Dateisystem-Cache sind mit dem On-Disk-Format identisch, einschließlich der Vorteile einer Komprimierung für Datendateien. Der Dateisystemcache wird vom Betriebssystem verwendet, um die I/O der Festplatte zu reduzieren.

Indizes, die im internen Cache von WiredTiger geladen werden, weisen eine andere Datendarstellung auf als das On-Disk-Format, können aber dennoch die Indexpräfixkomprimierung nutzen, um die RAM-Nutzung zu reduzieren.

Die Indexpräfixkomprimierung dedupliziert allgemeine Präfixe aus indizierten Feldern.

Sammlungsdaten im internen Cache von WiredTiger sind unkomprimiert und verwenden eine andere Darstellung als das On-Disk-Format. Die Blockkomprimierung kann erhebliche Speichereinsparungen auf der Festplatte ermöglichen, doch müssen die Daten unkomprimiert werden, damit sie vom Server bearbeitet werden können.

Über den Dateisystemcache verwendet MongoDB automatisch alle freien Speicher, die nicht vom WiredTiger-Cache oder anderen Prozessen verwendet werden.

Informationen zum Anpassen der Größe des internen WiredTiger-Cache finden Sie unter [storage.wiredTiger.engineConfig.cacheSizeGB](https://docs.mongodb.com/manual/reference/configuration-options/#storage.wiredTiger.engineConfig.cacheSizeGB) und [—wiredTigerCacheSizeGB](https://docs.mongodb.com/manual/reference/program/mongod/#cmdoption-wiredtigercachesizegb). Vermeiden Sie es, die interne Cachegröße von WiredTiger über den Standardwert zu erhöhen.

### NUMA {#numa}

Mit NUMA (Non Uniform Memory Access) kann ein Kernel verwalten, wie Speicher den Prozessorkernen zugeordnet wird. Obwohl dies versucht, den Speicherzugriff für Kerne zu beschleunigen, um sicherzustellen, dass sie auf die erforderlichen Daten zugreifen können, stört NUMA die Einführung zusätzlicher Latenzzeiten durch MMAP, da Lesevorgänge nicht vorhergesagt werden können. Aus diesem Grund muss NUMA für den `mongod`-Prozess auf allen Betriebssystemen mit diesen Funktionen deaktiviert werden.

Im Wesentlichen ist in einer NUMA-Architektur Speicher mit CPUs verbunden und CPUs sind mit einem Bus verbunden. In einer SMP- oder UMA-Architektur ist der Speicher mit dem Bus verbunden und wird von den CPUs gemeinsam genutzt. Wenn ein Thread Speicher auf einer NUMA-CPU zuweist, wird er gemäß einer Richtlinie zugewiesen. Die Standardeinstellung besteht darin, Speicher zuzuweisen, der an die lokale CPU des Threads angehängt ist, es sei denn, es ist kein freier Speicher vorhanden. In diesem Fall wird Speicher von einer kostenlosen CPU zu höheren Kosten verwendet. Nach der Zuordnung bewegt sich der Speicher nicht zwischen den CPUs. Die Zuordnung wird von einer Richtlinie vorgenommen, die vom übergeordneten Thread übernommen wurde. Letztendlich ist dies der Thread, der den Prozess gestartet hat.

In vielen Datenbanken, in denen der Rechner als Multicore-Uniform-Speicherarchitektur angesehen wird, führt dies dazu, dass zunächst die anfängliche CPU aufgefüllt wird und später die sekundäre CPU. Dies gilt insbesondere dann, wenn Speicherpuffer über einen zentralen Thread zugeordnet werden. Zur Lösung muss die NUMA-Richtlinie des Haupt-Threads geändert werden, mit dem der `mongod`-Prozess gestartet wird.

Führen Sie dazu den folgenden Befehl aus:

```shell
numactl --interleaved=all <mongod> -f config
```

Diese Richtlinie ordnet Speicher in einem runden Rund-Rund-Rund-Rund-Rad über alle CPU-Knoten zu, wodurch eine gleichmäßige Verteilung über alle Knoten gewährleistet ist. Sie generiert nicht den höchsten Leistungszugriff auf den Speicher wie in Systemen mit mehreren CPU-Hardware. Ungefähr die Hälfte der Speichervorgänge erfolgt langsamer und über den Bus, aber `mongod` ist nicht auf eine optimale NUMA-Nutzung ausgelegt. Daher handelt es sich um einen vernünftigen Kompromiss.

### NUMA-Probleme {#numa-issues}

Wenn der `mongod`-Prozess über ein anderes Verzeichnis als `/etc/init.d` gestartet wird, ist davon auszugehen, dass der Start nicht mit der richtigen NUMA-Richtlinie erfolgt. Je nach Standardrichtlinie können Probleme entstehen. Dies liegt daran, dass die verschiedenen Linux Package Manager-Installer für MongoDB auch einen Dienst installieren, dessen Konfigurationsdateien sich in `/etc/init.d` befinden und die oben beschriebenen Schritte ausführen. Wenn Sie MongoDB direkt aus einem Archiv (`.tar.gz`.targz) installieren und ausführen, müssen Sie mongod unter dem Prozess `numactl` manuell ausführen.

>[!NOTE]
>
>Weitere Informationen zu den verfügbaren NUMA-Richtlinien finden Sie in der [numactl-Dokumentation](https://linux.die.net/man/8/numactl).

Das Verhalten des MongoDB-Prozesses variiert abhängig von der jeweiligen Zuordnungsrichtlinie:

* `-membind=<nodes>`

   Die Zuordnung erfolgt nur auf den aufgeführten Knoten. Mongod ordnet keinen Speicher auf aufgeführten Knoten zu und nutzt möglicherweise nicht sämtlichen verfügbaren Speicher.

* `-cpunodebind=<nodes>`

   Die Ausführung erfolgt nur auf den Knoten. Mongod wird nur auf den aufgeführten Knoten ausgeführt und nutzt nur den auf diesen Knoten verfügbaren Speicher.

* `-physcpubind=<nodes>`

   
Die Ausführung erfolgt nur auf den genannten CPUs (Kernen). Mongod wird nur auf den aufgeführten CPUs ausgeführt und nutzt nur den auf diesen CPUs verfügbaren Speicher.

* `--localalloc`

   Speicher wird immer auf dem aktuellen Knoten zugewiesen, aber es werden alle Knoten verwendet, auf denen der Thread ausgeführt wird. Wenn ein Thread die Zuordnung ausführt, wird nur der Speicher verwendet, der der CPU zur Verfügung steht.

* `--preferred=<node>`

   Zwar wird die Zuordnung zu einem bestimmten Knoten vorgezogen, es wird aber auf einen anderen Knoten zurückgegriffen, wenn der bevorzugte Knoten voll ist. Es kann eine relative Notation zum Definieren eines Knotens verwendet werden. Außerdem werden die Threads auf allen Knoten ausgeführt.

Einige der Richtlinien können einen geringeren Wert als die für den `mongod`-Prozess verfügbare RAM-Gesamtmenge zur Folge haben. Im Gegensatz zu MySQL vermeidet MongoDB aktiv das Paging auf Betriebssystemebene, sodass der `mongod`-Prozess ggf. weniger Speicher erhält als verfügbar angezeigt wird.

#### Tausch {#swapping}

Aufgrund der speicherintensiven Natur von Datenbanken muss der Austausch auf Betriebssystemebene deaktiviert werden. Der MongoDB-Prozess vermeidet Swapping per Design.

#### Remote-Dateisysteme {#remote-filesystems}

Remote-Dateisysteme wie NFS werden für die internen Datendateien von MongoDB (die Datenbankdateien des mongod-Prozesses) nicht empfohlen, weil sie zu viel Latenz verursachen. Dies ist nicht mit dem freigegebenen Dateisystem zu verwechseln, das zum Speichern von Oak-Blobs (FileDataStore) erforderlich ist. Dafür wird NFS empfohlen.

#### Read-Ahead {#read-ahead}

Read-Ahead (Vorauslesen) muss so angepasst werden, dass nicht benötigte Blöcke beim Paging einer Seite im Zusammenhang mit einem zufälligen Lesevorgang nicht von der Festplatte gelesen werden, was zu einem unnötigen Verbrauch von I/O-Brandbreite führt.

### Linux-Anforderungen {#linux-requirements}

#### Mindestkernversionen {#minimum-kernel-versions}

* **2.6.23** für `ext4`-Dateisysteme

* **2.6.25** für `xfs`-Dateisysteme

#### Empfohlene Einstellungen für Datenbankdiscs {#recommended-settings-for-database-disks}

**Deaktivieren von atime**

Es wird empfohlen, `atime` für die Festplatten mit den Datenbanken zu deaktivieren.

**NOOP-Festplatten-Scheduler festlegen**

Gehen Sie dazu wie folgt vor:

Überprüfen Sie zunächst die I/O-Planung, die derzeit festgelegt ist. Führen Sie dazu den folgenden Befehl aus:

```shell
cat /sys/block/sdg/queue/scheduler
```

Erhalten Sie `noop` als Antwort, sind keine weiteren Maßnahmen erforderlich.

Ist NOOP nicht als I/O-Scheduler eingerichtet, können Sie dies durch Ausführen von Folgendem ändern:

```shell
echo noop > /sys/block/sdg/queue/scheduler
```

**Anpassen des Read-Ahead-Werts**

Es wird empfohlen, einen Wert von 32 für die Festplatten zu verwenden, von denen MongoDB-Datenbanken ausgeführt werden. Das sind 16 Kilobytes. Sie können sie festlegen, indem Sie Folgendes ausführen:

```shell
sudo blockdev --setra <value> <device>
```

#### NTP aktivieren {#enable-ntp}

Vergewissern Sie sich, dass NTP auf dem Computer installiert ist, auf dem die MongoDB-Datenbanken gehostet werden. Beispielsweise können Sie NTP über Yum Package Manager auf einem CentOS-Rechner installieren:

```shell
sudo yum install ntp
```

Nachdem der NTP-Daemon installiert und erfolgreich gestartet wurde, können Sie die Drift-Datei auf den Zeitversatz Ihres Servers überprüfen.

#### Transparente große Seiten deaktivieren {#disable-transparent-huge-pages}

Red Hat Linux nutzt einen Speicherverwaltungsalgorithmus mit der Bezeichnung THP (Transparent Huge Pages). Es wird empfohlen, diesen zu deaktivieren, wenn Sie das Betriebssystem für Datenbank-Workloads einsetzen.

Eine Deaktivierung ist mithilfe der folgenden Vorgehensweise möglich:

1. Öffnen Sie die Datei `/etc/grub.conf` in einem beliebigen Texteditor.
1. Fügen Sie der Datei „grub.conf“ die folgende Zeile hinzu:

   ```xml
   transparent_hugepage=never
   ```

1. Überprüfen Sie abschließend, ob die Einstellung wirksam wurde, indem Sie Folgendes ausführen:

   ```shell
   cat /sys/kernel/mm/redhat_transparent_hugepage/enabled
   ```

   Wenn THP deaktiviert ist, sollte die Ausgabe des obigen Befehls wie folgt lauten:

   ```xml
   always madvise [never]
   ```

>[!NOTE]
>
>Weitere Informationen zu THP finden Sie in diesem [Artikel](https://access.redhat.com/solutions/46111).

#### Deaktivieren von NUMA {#disable-numa}

In den meisten Installationen mit NUMA-Aktivierung wird NUMA automatisch vom MongoDB-Daemon deaktiviert, sofern die Ausführung als Dienst über den Ordner `/etc/init.d` erfolgt.

Sollte dies nicht der Fall sein, können Sie NUMA prozessweise deaktivieren. Zum Deaktivieren führen Sie diese Befehle aus:

```shell
numactl --interleave=all <path_to_process>
```

`<path_to_process>` steht dabei für den Pfad zum mongod-Prozess.

Deaktivieren Sie dann den „zone_reclaim“-Modus, indem Sie Folgendes ausführen:

```shell
echo 0 > /proc/sys/vm/zone_reclaim_mode
```

#### Optimieren der ulimit-Einstellungen für den mongod-Prozess {#tweak-the-ulimit-settings-for-the-mongod-process}

Linux ermöglicht mit dem Befehl `ulimit` eine konfigurierbare Steuerung der Ressourcenzuweisung. Dies kann auf Benutzenden- oder Prozessbasis geschehen.

Es wird empfohlen, ulimit für den mongod -Prozess entsprechend der Variablen [MongoDB Empfohlene ulimit-Einstellungen](https://docs.mongodb.org/manual/reference/ulimit/#recommended-ulimit-settings).

#### Testen der MongoDB I/O-Leistung {#test-mongodb-i-o-performance}

MongoDB bietet ein Tool namens `mongoperf`, das zum Testen der I/O-Leistung entwickelt wurde. Sie sollten damit die Leistung aller MongoDB-Instanzen in Ihrer Infrastruktur testen.

Informationen zum Verwenden von `mongoperf` finden Sie in der [MongoDB-Dokumentation](https://docs.mongodb.org/manual/reference/program/mongoperf/).

>[!NOTE]
>
>`mongoperf` wurde als Indikator für die MongoDB-Leistung auf der Plattform, auf der MongoDB ausgeführt wird, entwickelt. Daher sollten die Ergebnisse nicht als definitiver Wert für die Leistung eines Produktionssystems angesehen werden.
>
>Um genauere Leistungsergebnisse zu erhalten, können Sie ergänzende Tests mit dem Linux-Tool `fio` durchführen.

**Testen der Leseleistung auf den virtuellen Maschinen einer Bereitstellung**

Wechseln Sie nach der Installation des Tools in das MongoDB-Datenbankverzeichnis, um die Tests durchzuführen. Starten Sie dann den ersten Test, indem Sie `mongoperf` mit der folgenden Konfiguration ausführen:

```shell
echo "{nThreads:32,fileSizeMB:1000,r:true}" | mongoperf
```

Die gewünschte Ausgabe sollte bis zu zwei Gigabyte pro Sekunde (2 GB/s) sowie 500.000 IOPS bei 32 Threads für alle MongoDB-Instanzen erreichen.

Führen Sie einen zweiten Test durch (dieses Mal mit den speicherzugeordneten Dateien), indem Sie den Parameter `mmf:true` festlegen:

```shell
echo "{nThreads:32,fileSizeMB:1000,r:true,mmf:true}" | mongoperf
```

Die Ausgabe des zweiten Tests sollte deutlich höher sein als die erste und die Leistung in Bezug auf die Speicherübertragung angeben.

>[!NOTE]
>
>Überprüfen Sie während der Tests die I/O-Nutzungsstatistik für die fraglichen virtuellen Maschinen in Ihrem zur Betriebssystemüberwachung eingesetzten System. Wenn für die I/O-Lesevorgänge ein Testergebnis von unter 100 % ausgegeben wird, liegt womöglich ein Problem bei der virtuellen Maschine vor.

**Testen der Schreibleistung der primären MongoDB-Instanz**

Überprüfen Sie als Nächstes die I/O-Schreibleistung der primären MongoDB-Instanz, indem Sie `mongoperf` mit denselben Einstellungen über das MongoDB-Datenbankverzeichnis ausführen:

```shell
echo "{nThreads:32,fileSizeMB:1000,w:true}" | mongoperf
```

Die gewünschte Ausgabe sollte 12 Megabyte pro Sekunde betragen und etwa 3000 IOPS erreichen, wobei die Anzahl der Threads nur geringfügig variiert.

## Schritte für virtualisierte Umgebungen {#steps-for-virtualised-environments}

### VMWare {#vmware}

Wenn Sie virtualisierte Umgebungen mithilfe von VMware ESX verwalten und bereitstellen, müssen Sie für MongoDB über die ESX-Konsole die folgenden Einstellungen vornehmen:

1. Deaktivieren Sie Memory-Ballooning.
1. Führen Sie eine Vorabzuweisung und Reservierung von Speicher für die virtuellen Maschinen durch, die die MongoDB-Datenbanken hosten sollen.
1. Weisen Sie dem `mongod`-Prozess über Storage I/O Control genügend I/O-Kapazität zu.
1. Garantieren Sie den MongoDB-Hostmaschinen CPU-Ressourcen, indem Sie die Option für die [CPU-Reservierung](https://pubs.vmware.com/vsphere-4-esx-vcenter/index.jsp?topic=/com.vmware.vsphere.vmadmin.doc_41/vsp_vm_guide/configuring_virtual_machines/t_allocate_cpu_resources.html) einstellen.

1. Ziehen Sie die Verwendung von Paravirtual-I/O-Treibern in Betracht. Weitere Informationen dazu finden Sie in diesem [Knowledgebase-Artikel](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&amp;cmd=displayKC&amp;externalId=1010398).

### Amazon Web Services {#amazon-web-services}

Die Dokumentation zum Einrichten von MongoDB mit Amazon Web Services finden Sie im folgenden Handbuch [MongoDB auf AWS](https://docs.aws.amazon.com/quickstart/latest/mongodb/welcome.html).

## Sichern von MongoDB vor der Bereitstellung {#securing-mongodb-before-deployment}

Siehe diesen Beitrag auf [Sichere Bereitstellung von MongoDB](https://blogs.adobe.com/security/2015/07/securely-deploying-mongodb-3-0.html) für Ratschläge zur Sicherung der Konfiguration Ihrer Datenbanken vor der Bereitstellung.

## Dispatcher {#dispatcher}

### Auswählen des Betriebssystems für den Dispatcher {#choosing-the-operating-system-for-the-dispatcher}

Damit Ihre MongoDB-Bereitstellung ordnungsgemäß bereitgestellt werden kann, muss das Betriebssystem, das den Dispatcher hostet, ausgeführt werden **Apache httpd Version 2.4 oder höher.**

Stellen Sie zudem sicher, dass alle Bibliotheken im Build auf dem aktuellen Stand sind, um Auswirkungen auf die Sicherheit zu minimieren.

### Dispatcher-Konfiguration {#dispatcher-configuration}

Eine typische Dispatcher-Konfiguration wird den Anforderungsdurchsatz einer einzelnen AEM zwischen zehnmal und zwanzig Mal erhöhen.

Da der Dispatcher hauptsächlich statusfrei ist, kann er mit Leichtigkeit horizontal skaliert werden. In einigen Implementierungen müssen Autoren vom Zugriff auf bestimmte Ressourcen ausgeschlossen sein. Daher wird ausdrücklich die Verwendung eines Dispatchers bei Autoreninstanzen empfohlen.

Wenn AEM ohne Dispatcher ausgeführt werden, müssen SSL-Terminierung und Lastenausgleich von einer anderen Anwendung durchgeführt werden. Dies ist erforderlich, da Sitzungen eine Affinität zu der AEM Instanz aufweisen müssen, auf der sie erstellt wurden. Dabei handelt es sich um ein Konzept, das als Sticky-Verbindungen bezeichnet wird. Hierdurch soll sichergestellt werden, dass Inhaltsaktualisierungen eine minimale Latenz aufweisen.

Weitere Informationen zur entsprechenden Konfiguration finden Sie in der [Dispatcherdokumentation](https://helpx.adobe.com/de/experience-manager/dispatcher/using/dispatcher.html).

### Zusätzliche Konfiguration {#additional-configuration}

#### Sticky-Verbindungen  {#sticky-connections}

Sticky-Verbindungen stellen sicher, dass personalisierte Seiten und Sitzungsdaten für einen Benutzer alle auf derselben Instanz von AEM erstellt werden. Diese Daten werden in der Instanz gespeichert, sodass nachfolgende Anforderungen desselben Benutzers an dieselbe Instanz zurückgegeben werden.

Es wird empfohlen, Sticky-Verbindungen für alle inneren Ebenen zu aktivieren, die Anforderungen an die AEM-Instanzen leiten, sodass nachfolgende Anforderungen dieselbe AEM erreichen. Dies trägt dazu bei, Latenzzeiten zu minimieren, die andernfalls auftreten, wenn Inhalt zwischen Instanzen aktualisiert wird.

#### Lange Ablaufzeit {#long-expires}

Standardmäßig enthält Inhalt, der von einem AEM Dispatcher gesendet wird, die Header Last-Modified und Etag , ohne Angabe des Ablaufs des Inhalts. Dadurch wird zwar sichergestellt, dass die Benutzeroberfläche immer die neueste Ressourcenversion erhält, doch bedeutet dies auch, dass der Browser einen GET-Vorgang durchführt, um zu überprüfen, ob sich die Ressource geändert hat. Dies kann zu mehreren Anfragen führen, auf die die HTTP-Antwort je nach Seitenladevorgang 304 (Nicht geändert) beträgt. Für Ressourcen, von denen bekannt ist, dass sie nicht ablaufen, wird der Inhalt zwischengespeichert, wenn Sie eine Expires-Kopfzeile festlegen und die Header Last-Modified und ETag entfernen, bis das Datum in der Kopfzeile Expires erreicht ist. Dadurch werden keine weiteren Aktualisierungsanfragen gestellt.

Die Verwendung dieser Methode bedeutet jedoch, dass es keine vernünftige Möglichkeit gibt, die Ressource im Browser ablaufen zu lassen, bevor der Expires-Header abläuft. Um dies zu vermeiden, kann der HtmlClientLibraryManager so konfiguriert werden, dass unveränderliche URLs für Client-Bibliotheken verwendet werden.

Diese URLs werden garantiert nicht geändert. Wenn sich der in der URL enthaltene Hauptteil der Ressource ändert, werden diese Änderungen automatisch in der URL widergespiegelt. So ist sichergestellt, dass der Browser die richtige Ressourcenversion anfordert.

Die Standardkonfiguration fügt dem HtmlClientLibraryManager einen Selektor hinzu. Da es sich um einen Selektor handelt, wird die Ressource im Dispatcher mit intaktem Selektor zwischengespeichert. Dieser Selektor kann auch verwendet werden, um das richtige Ablaufverhalten sicherzustellen. Der Standardselektor folgt dem Muster `lc-.*?-lc`. Die folgenden Apache httpd-Konfigurationsanweisungen stellen sicher, dass alle Anforderungen, die diesem Muster entsprechen, mit einer angemessenen Ablaufzeit verarbeitet werden.

```xml
Header set Expires "Tue, 20 Jan 2037 04:20:42 GMT" "expr=(%{REQUEST_STATUS} -eq 200) && (%{REQUEST_URI} =~ /.*lc-.*?-lc.*/)"
Header set Cache-Control "public, no-transform, max-age=267840000" "expr=(%{REQUEST_STATUS} -eq 200) && (%{REQUEST_URI} =~ /.*lc-.*?-lc.*/)"
Header unset ETag "expr=(%{REQUEST_STATUS} -eq 200) && (%{REQUEST_URI} =~ /.*lc-.*?-lc.*/)"
Header unset Last-Modified "expr=(%{REQUEST_STATUS} -eq 200) && (%{REQUEST_URI} =~ /.*lc-.*?-lc.*/)"
Header unset Pragma "expr=(%{REQUEST_STATUS} -eq 200) && (%{REQUEST_URI} =~ /.*lc-.*?-lc.*/)"
```

#### No Sniff {#no-sniff}

Wenn Inhalte ohne Content-Typ gesendet werden, versuchen viele Browser, den Inhaltstyp zu erraten, indem sie die ersten Byte des Inhalts lesen. Dies wird als &quot;Sniffing&quot;bezeichnet. Sniffing eröffnet eine Sicherheitslücke, da Benutzer, die in das Repository schreiben können, möglicherweise schädliche Inhalte ohne Inhaltstyp hochladen können.

Daher wird empfohlen, den Header `no-sniff` zu den Ressourcen hinzuzufügen, die vom Dispatcher abgewickelt werden. Der Dispatcher speichert jedoch keine Header zwischen. Das bedeutet, dass jeder Inhalt, der aus dem lokalen Dateisystem bereitgestellt wird, seinen Inhaltstyp durch seine Erweiterung bestimmt, anstatt den ursprünglichen Content-Type-Header vom AEM Herkunftsserver zu verwenden.

Kein Sniff kann sicher aktiviert werden, wenn bekannt ist, dass die Webanwendung keine zwischengespeicherten Ressourcen ohne Dateityp bereitstellt.

Sie können &quot;No Sniff&quot;einschließen:

```xml
Header set X-Content-Type-Options "nosniff"
```

Sie kann auch selektiv aktiviert werden:

```xml
RewriteCond %{REQUEST_URI} \.(?:js|jsonp)$ [OR]
RewriteCond %{QUERY_STRING} (callback|jsonp|cb)=\w+
RewriteRule .* - [E=jsonp_request:1]
Header set X-Content-Type-Options "nosniff"  env=jsonp_request
Header setifempty Content-Type application/javascript env=jsonp_request
```

#### Inhaltssicherheitsrichtlinie {#content-security-policy}

Die standardmäßigen Dispatcher-Einstellungen ermöglichen das Öffnen der Content Security Policy, auch als CSP bezeichnet. Hierdurch kann eine Seite Ressourcen von allen Domains gemäß den Standardrichtlinien der Browser-Sandbox laden.

Es ist wünschenswert, den Speicherort von Ressourcen einzuschränken, um zu vermeiden, dass Code von nicht vertrauenswürdigen oder nicht verifizierten ausländischen Servern in die JavaScript-Engine geladen wird.

CSP ermöglicht eine Feinabstimmung der Richtlinien. In einer komplexen Anwendung müssen CSP-Header jedoch mit Vorsicht entwickelt werden, da zu restriktive Richtlinien Teile der Benutzeroberfläche beschädigen können.

>[!NOTE]
>
>Weitere Informationen zur Funktionsweise finden Sie unter [OWASP-Seite für Content Security Policy](https://www.owasp.org/index.php/Content_Security_Policy).

### Größe {#sizing}

Weitere Informationen zur Größenanpassung finden Sie unter [Richtlinien zur Hardware-Skalierung](/help/managing/hardware-sizing-guidelines.md).

### MongoDB-Leistungsoptimierung {#mongodb-performance-optimization}

Allgemeine Informationen zur MongoDB-Leistung finden Sie unter [Analysieren der MongoDB-Leistung](https://docs.mongodb.org/manual/administration/analyzing-mongodb-performance/).

## Bekannte Einschränkungen {#known-limitations}

### Gleichzeitige Installationen {#concurrent-installations}

Die gleichzeitige Verwendung mehrerer AEM Instanzen mit einer einzigen Datenbank wird von MongoMK unterstützt, gleichzeitige Installationen jedoch nicht.

Um dieses Problem zu umgehen, führen Sie zuerst die Installation mit nur einer Instanz aus und fügen Sie dann nach deren Abschluss weitere hinzu.

### Länge des Seitennamens {#page-name-length}

Wenn AEM auf einer MongoMK-Persistenz-Manager-Bereitstellung ausgeführt wird, sind [Seitennamen auf 150 Zeichen beschränkt](/help/sites-authoring/managing-pages.md#page-name-restrictions-and-best-practices).

>[!NOTE]
>
>Weitere Informationen zu den bekannten Einschränkungen und Schwellenwerten von MongoDB [finden Sie in der MongoDB-Dokumentation](https://docs.mongodb.com/manual/reference/limits/).
