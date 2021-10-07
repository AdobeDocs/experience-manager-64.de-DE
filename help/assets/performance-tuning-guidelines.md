---
title: Handbuch zur Leistungsoptimierung von Assets
description: Schlüsselbereiche für  [!DNL Experience Manager] configuration, changes to hardware, software, and network components to remove bottlenecks and optimize the performance of [!DNL Experience Manager] Assets.
contentOwner: AG
feature: Asset Management
role: Architect,Admin
exl-id: 6c1bff46-f9e0-4638-9374-a9e820d30534
source-git-commit: 63a4304a1a10f868261eadce74a81148026390b6
workflow-type: tm+mt
source-wordcount: '3151'
ht-degree: 67%

---

# Handbuch zur Leistungsoptimierung von Assets {#assets-performance-tuning-guide}

Ein Adobe Experience Manager Assets-Setup enthält eine Reihe von Hardware-, Software- und Netzwerkkomponenten. Je nach Ihrem Bereitstellungsszenario benötigen Sie möglicherweise bestimmte Konfigurationsänderungen an den Hardware-, Software- und Netzwerkkomponenten, um Leistungsengpässe zu vermeiden.

Darüber hinaus hilft Ihnen die Identifizierung und Einhaltung bestimmter Richtlinien zur Hardware- und Softwareoptimierung dabei, eine solide Grundlage zu schaffen, die es Ihrer [!DNL Experience Manager]-Assets-Implementierung ermöglicht, Erwartungen hinsichtlich Leistung, Skalierbarkeit und Zuverlässigkeit zu erfüllen.

Eine ungenügende Leistung in [!DNL Experience Manager] Assets kann sich auf die Benutzererfahrung im Hinblick auf interaktive Leistung, Asset-Verarbeitung, Download-Geschwindigkeit und andere Bereiche auswirken.

Daher gehört die Leistungsoptimierung zu den grundlegenden Aufgaben, bevor Sie Zielmetriken für Ihre Projekte erstellen.

In den folgenden Schlüsselbereichen sollten Sie besonders darauf achten, dass Leistungsprobleme erkannt und behoben werden, bevor sie sich auf das Benutzererlebnis auswirken.

## Plattform {#platform}

Während [!DNL Experience Manager] auf einer Reihe von Plattformen unterstützt wird, hat Adobe die beste Unterstützung für native Tools unter Linux und Windows gefunden, was zu einer optimalen Leistung und Vereinfachung der Implementierung beiträgt. Idealerweise sollten Sie ein 64-Bit-Betriebssystem bereitstellen, um die hohen Speicheranforderungen einer [!DNL Experience Manager] Assets-Bereitstellung zu erfüllen. Wie bei jeder [!DNL Experience Manager]-Implementierung sollten Sie TarMK möglichst implementieren. TarMK kann zwar nicht über eine einzelne Autoreninstanz skaliert werden, erzielt jedoch erfahrungsgemäß eine bessere Leistung als MongoMK. Sie können TarMK-Ablade-Instanzen hinzufügen, um die Verarbeitungsleistung Ihrer [!DNL Experience Manager] Assets-Implementierung zu erhöhen.

### Temporärer Ordner   {#temp-folder}

Nutzen Sie einen Hochleistungsspeicher für das temporäre Java-Verzeichnis, um das Hochladen der Assets zu beschleunigen. Unter Linux und Windows können Sie beispielsweise ein RAM- oder SSD-Laufwerk verwenden. In Cloud-basierten Umgebungen kann ein äquivalenter Hochgeschwindigkeitsspeicher verwendet werden. In Amazon EC2 kann beispielsweise ein [temporäres Laufwerk](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/InstanceStorage.html) für den temporären Ordner verwendet werden.

Bei einer großen Speicherkapazität des Servers kann ein RAM-Laufwerk konfiguriert werden. Führen Sie unter Linux die folgenden Befehle aus, um ein RAM-Laufwerk von 8 GB zu erstellen:

```shell
mkfs -q /dev/ram1 800000
 mkdir -p /mnt/aem-tmp
 mount /dev/ram1 /mnt/aem-tmp
 df -H | grep aem-tmp
```

Unter Windows müssen Sie den Treiber eines Drittanbieters nutzen, um ein RAM-Laufwerk zu erstellen, oder einen Hochleistungsspeicher wie SSD verwenden.

Sobald das temporäre Hochleistungs-Volume bereit ist, stellen Sie den JVM-Parameter Djava.io.tmpdir ein. Sie können beispielsweise den JVM-Parameter unter der Variablen „CQ_JVM_OPTS“ im Skript „bin/start“ von AEM einfügen:

`-Djava.io.tmpdir=/mnt/aem-tmp`

## Java-Konfiguration {#java-configuration}

### Java-Version {#java-version}

Da Oracle seit April 2015 keine Updates für Java 7 mehr veröffentlicht, empfiehlt Adobe die Bereitstellung von [!DNL Experience Manager] Assets unter Java 8. Damit wurde in einigen Fällen eine bessere Leistung erzielt.

### JVM-Parameter   {#jvm-parameters}

Legen Sie die folgenden JVM-Parameter fest:

* `-XX:+UseConcMarkSweepGC`
* `-Doak.queryLimitInMemory`=500000
* `-Doak.queryLimitReads`=100000
* `-Dupdate.limit`=250000
* `-Doak.fastQuerySize`=true

## Datenspeicher- und Arbeitsspeicherkonfiguration {#data-store-and-memory-configuration}

### Dateidatenspeicherkonfiguration {#file-data-store-configuration}

Die Trennung des Datenspeichers vom Segmentspeicher wird für alle Benutzer von [!DNL Experience Manager] Assets empfohlen. Außerdem kann die Leistung durch die Konfiguration der Parameter `maxCachedBinarySize` und `cacheSizeInMB` maximiert werden. Stellen Sie `maxCachedBinarySize` auf die kleinste im Cache unterstützte Dateigröße ein. Geben Sie die Größe des Arbeitsspeicher-Cache für den Datenspeicher in `cacheSizeInMB` ein. Adobe empfiehlt, diesen Wert auf 2–10 Prozent der gesamten Heap-Größe einzustellen. Mithilfe von Last-/Leistungstests lässt sich die ideale Einstellung herausfinden.

### Konfigurieren der Maximalgröße des gepufferten Bilder-Caches   {#configure-the-maximum-size-of-the-buffered-image-cache}

Verringern Sie beim Hochladen großer Mengen an Assets in Adobe Experience Manager zur Berücksichtigung unerwarteter Spitzen bei der Speichernutzung und zur Verhinderung von JVM-Fehlern mit OutOfMemoryErrors die konfigurierte Maximalgröße des gepufferten Bilder-Caches. Betrachten wir ein Beispiel mit einem System, das über eine maximale Heap-Größe (-`Xmx`param) von 5 GB verfügt und bei dem der Oak-Blob-Cache auf 1 GB und der Dokumenten-Cache auf 2 GB eingestellt ist. In diesem Fall würde der gepufferte Cache das Maximum von 1,25 GB Speicher in Anspruch nehmen, wodurch nur 0,75 GB Speicher für unerwartete Spitzen verblieben.

Konfigurieren Sie die Größe des gepufferten Cache in der OSGi-Webkonsole. Legen Sie bei `https://host:port/system/console/configMgr/com.day.cq.dam.core.impl.cache.CQBufferedImageCache` die Eigenschaft `cq.dam.image.cache.max.memory` in Byte fest. 1073741824 entspricht beispielsweise 1 GB (1024 x 1024 x 1024 = 1 GB).

Wenn Sie von [!DNL Experience Manager] 6.1 SP1 einen `sling:osgiConfig`-Knoten zum Konfigurieren dieser Eigenschaft verwenden, stellen Sie sicher, dass Sie den Datentyp auf &quot;Long&quot;einstellen. Weitere Details finden Sie unter [CQBufferedImageCache belegt beim Asset-Upload den Heap](https://helpx.adobe.com/de/experience-manager/kb/cqbufferedimagecache-consumes-heap-during-asset-uploads.html).

### Gemeinsame Datenspeicher   {#shared-data-stores}

Mit der Implementierung eines S3-Datenspeichers oder Shared File Datastore sparen Sie Speicherplatz auf der Festplatte und erhöhen den Netzwerkdurchsatz in großen Implementierungen. Weitere Informationen zu den Vor- und Nachteilen der Verwendung eines freigegebenen Datenspeichers finden Sie unter [Anleitung zur Dimensionierung von Assets](assets-sizing-guide.md).

### S3-Datenspeicher {#s-data-store}

Mit der folgenden Konfiguration des S3-Datenspeichers (`org.apache.jackrabbit.oak.plugins.blob.datastore.S3DataStore.cfg`) konnte Adobe binäre große Objekte (BLOBs) mit einer Größe von 12,8 TB von einem vorhandenen Dateidatenspeicher in einen S3-Datenspeicher am Standort eines Kunden extrahieren:

```conf
accessKey=<snip>
 secretKey=<snip>
 s3Bucket=<snip>
 s3Region=us-standard
 s3EndPoint=<a href="https://s3.amazonaws.com/">s3.amazonaws.com</a>
 connectionTimeout=120000
 socketTimeout=120000
 maxConnections=80
 writeThreads=60
 concurrentUploadsThreads=30
 asyncUploadLimit=30
 maxErrorRetry=1000
 path=/opt/author/crx-quickstart/repository/datastore
 s3RenameKeys=false
 s3Encryption=SSE_S3
 proactiveCaching=true
 uploadRetries=1000
 migrateFailuresCount=400
```

## Netzwerkoptimierung {#network-optimization}

Adobe empfiehlt die Aktivierung von HTTPS, da viele Unternehmen über Firewalls verfügen, die den HTTP-Verkehr überprüfen und sich dadurch negativ auf Uploads auswirken und Dateien beschädigen. Stellen Sie bei großen Datei-Uploads sicher, dass Benutzer über Kabelverbindungen zum Netzwerk verfügen, da ein WLAN-Netzwerk schnell überfordert ist. Richtlinien zur Ermittlung von Netzwerkengpässen finden Sie unter [Anleitung zur Dimensionierung von Assets](assets-sizing-guide.md). Informationen zur Beurteilung der Netzwerkleistung mit einer Analyse der Netzwerktopologie finden Sie unter [Überlegungen zum Assets-Netzwerk](assets-network-considerations.md).

In erster Linie hängt Ihre Netzwerkoptimierungsstrategie von der verfügbaren Bandbreite und der Belastung Ihrer [!DNL Experience Manager]-Instanz ab. Allgemeine Konfigurationsoptionen, einschließlich Firewalls oder Proxys, können zur Verbesserung der Netzwerkleistung beitragen. Die folgenden Aspekte sollten berücksichtigt werden:

* Stellen Sie je nach Instanztyp (klein, mittel, groß) sicher, dass Sie über ausreichend Netzwerkbandbreite für Ihre [!DNL Experience Manager]-Instanz verfügen. Eine angemessene Bandbreitenzuordnung ist besonders wichtig, wenn [!DNL Experience Manager] auf AWS gehostet wird.
* Wenn Ihre [!DNL Experience Manager]-Instanz auf AWS gehostet wird, können Sie von einer flexiblen Skalierungsrichtlinie profitieren. Vergrößern Sie die Instanz, wenn Benutzer eine hohe Belastung erwarten. Verkleinern Sie die Instanz, wenn nur eine mäßige/geringe Belastung erwartet wird.
* HTTPS: Die meisten Benutzer verwenden Firewalls zur Überwachung des HTTP-Verkehrs. Sie können den Prozess des Hochladens beeinträchtigen oder Dateien beim Hochladen beschädigen.
* Upload großer Dateien: Die Benutzer benötigen Kabelverbindungen zum Netzwerk (WLAN-Verbindungen sind schnell gesättigt).

## Workflows   {#workflows}

### Verlaufs-Workflows {#transient-workflows}

Stellen Sie den Workflow „DAM-Update-Asset“ nach Möglichkeit auf „Übergang“ ein. Die Einstellung trägt zu einer erheblichen Reduzierung des Overheads bei, der für die Verarbeitung der Workflows benötigt wird, da die Workflows in diesem Fall nicht die normalen Tracking- und Archivierungsprozesse durchlaufen.

>[!NOTE]
>
>Standardmäßig ist der Workflow DAM-Update-Asset in [!DNL Experience Manager] 6.3 auf Verlaufs gesetzt. In diesem Fall können Sie das folgende Verfahren überspringen.

1. Öffnen Sie `http://localhost:4502/miscadmin` in der [!DNL Experience Manager]-Instanz, die Sie konfigurieren möchten.

1. Erweitern Sie im Navigationsbaum **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]** > **[!UICONTROL dam]**.
1. Doppelklicken Sie auf **[!UICONTROL DAM-Update-Asset]**.
1. Wechseln Sie im unverankerten Tool-Fenster auf die Registerkarte **[!UICONTROL Seite]** und klicken Sie auf **[!UICONTROL Seiteneigenschaften]**.
1. Wählen Sie **[!UICONTROL Verlaufs-Workflow]**. Klicken Sie auf **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Einige Funktionen unterstützen keine Verlaufs-Workflows. Wenn diese Funktionen für Ihre [!DNL Experience Manager] Assets-Bereitstellung erforderlich sind, konfigurieren Sie keine Übergangs-Workflows.

   Wenn keine Verlaufs-Workflows verwendet werden können, führen Sie regelmäßig Workflow-Bereinigungen durch, um archivierte DAM-Update-Asset-Workflows zu löschen. So verhindern Sie eine Beeinträchtigung der Systemleistung.

   In der Regel sollten Sie Workflow-Bereinigungen auf wöchentlicher Basis durchführen. In ressourcenintensiven Szenarien wie z. B. einer umfangreichen Asset-Erfassung kann die Bereinigung auch häufiger ausgeführt werden.

   Um die Workflow-Bereinigung zu konfigurieren, fügen Sie in der OSGi-Konsole eine neue Adobe Granite-Workflow-Bereinigungskonfiguration hinzu. Konfigurieren und planen Sie im nächsten Schritt den Workflow als Teil des wöchentlichen Wartungsfensters.

   Dauert die Bereinigung zu lange, kommt es zu einem Timeout. Daher sollten Sie sicherstellen, dass die Bereinigungsaufträge abgeschlossen sind. So vermeiden Sie, dass Bereinigungs-Workflows aufgrund der hohen Zahl an Workflows nicht abgeschlossen werden können.

   Wenn Sie zahlreiche Nicht-Verlaufs-Workflows ausgeführt haben, die Workflow-Instanzknoten erstellen, können Sie das Tool [ACS AEM Commons Workflow Remover](https://adobe-consulting-services.github.io/acs-aem-commons/features/workflow-remover.html) auf Ad-hoc-Basis ausführen. Es entfernt redundante, abgeschlossene Workflow-Instanzen sofort, ohne dass Sie auf die Ausführung des Adobe Granite-Workflow-Bereinigungsplaners warten müssen.

### Maximal parallel ausführbare Aufträge   {#maximum-parallel-jobs}

Standardmäßig führt [!DNL Experience Manager] eine maximale Anzahl paralleler Aufträge aus, die der Anzahl der Prozessoren auf dem Server entspricht. Das Problem bei dieser Einstellung besteht darin, dass in Zeiten hoher Auslastung alle Prozessoren von DAM Update Asset-Workflows genutzt werden, was die Reaktionsfähigkeit der Benutzeroberfläche verlangsamt und verhindert, dass [!DNL Experience Manager] andere Prozesse ausführt, die die Serverleistung und -stabilität gewährleisten. Es hat sich bewährt, diese Einstellung so zu wählen, dass nur die Hälfte der auf dem Server verfügbaren Prozessoren verwendet wird:

1. Wechseln Sie auf [!DNL Experience Manager] Author zu [http://localhost:4502/system/console/slingevent](http://localhost:4702/system/console/slingevent).
1. Klicken Sie für jede für Ihre Implementierung relevante Workflow-Warteschlange, z. B. für die Granite-Warteschlange für Verlaufs-Workflows, auf „Bearbeiten“.
1. Ändern Sie den Wert der maximal parallel ausführbaren Aufträge und klicken Sie auf „Speichern“.

Diese Einstellung des Werts auf die Hälfte der verfügbaren Prozesse ist für den Anfang eine praktikable Lösung. Unter Umständen müssen Sie diese Zahl jedoch nach oben oder unten anpassen, um den maximalen Durchsatz zu erreichen, und auch an die spezifische Umgebung anpassen. Es gibt separate Warteschlangen für Verlaufs- und Nicht-Verlaufs-Workflows sowie für andere Prozesse wie beispielsweise externe Workflows. Sind mehrere Warteschlangen, die auf 50 % der Prozessoren gesetzt sind, gleichzeitig aktiv, kann es schnell zu einer Überlastung des Systems kommen. Welche Warteschlangen stark ausgelastet sind, hängt in hohem Maße von den Benutzerimplementierungen ab. Sie müssen daher sorgfältig und mit Bedacht konfiguriert werden, um maximale Effizienz zu erreichen, die nicht zu Lasten der Serverstabilität geht.

### Entladen {#offloading}

Bei umfangreichen Workflows oder ressourcenintensiven Workflows, z. B. bei der Videotranskodierung, können Sie die Workflows &quot;DAM-Update-Asset&quot;auf eine zweite Autoreninstanz übertragen. Das Problem mit der Abladung liegt häufig darin, dass die Auslastung, die durch Abladung der Workflow-Verarbeitung eingespart wird, durch die Kosten aufgewogen wird, die bei der Replikation von Inhalten zwischen den Instanzen anfallen.

Ab [!DNL Experience Manager] 6.2 und mit einem Feature Pack für [!DNL Experience Manager] 6.1 können Sie das Abladen mit binärloser Replikation durchführen. In diesem Modell verwenden die Autor-Instanzen einen gemeinsamen Datenspeicher und senden nur die Metadaten durch Vorwärtsreplikation hin und her. Diese Vorgehensweise funktioniert hervorragend mit einem gemeinsamen Dateispeicher. Mit S3-Datenspeichern können jedoch Probleme auftreten. Da im Hintergrund laufende Schreib-Threads zu Latenz führen können, kann es Assets geben, die vor Start des Abladungsauftrags nicht in den Datenspeicher geladen wurden.

### Konfiguration von DAM-Update-Asset {#dam-update-asset-configuration}

Der Workflow &quot;DAM-Update-Asset&quot;enthält eine vollständige Suite von Schritten, die für Aufgaben wie die Dynamic Media Classic-PTIFF-Generierung und InDesign Server-Integration konfiguriert sind. Die meisten Benutzer benötigen jedoch nicht alle diese Schritte. Adobe empfiehlt die Erstellung einer benutzerdefinierten Kopie des DAM-Update-Asset-Workflow-Modells, in der alle unnötigen Schritte entfernt wurden. Aktualisieren Sie dann die Launcher für DAM-Update-Asset so, dass sie auf das neue Modell zeigen.

>[!NOTE]
>
>Wenn Sie den Workflow „DAM-Update-Asset“ häufig ausführen, kann hierdurch die Größe Ihres Dateidatenspeichers deutlich ansteigen. Entsprechende Tests von Adobe haben gezeigt, dass die Datenspeichergröße um ca. 400 GB ansteigt, wenn innerhalb von 8 Stunden 5.500 Workflows ausgeführt werden.
>
>Hierbei handelt es sich um einen vorübergehenden Anstieg. Nach Ausführung der Aufgabe zur Speicherbereinigung weist der Datenspeicher wieder seine ursprüngliche Größe auf.
>
>In der Regel wird die Speicherbereinigung wöchentlich gemeinsam mit anderen geplanten Wartungsaufgaben ausgeführt.
>
>Wenn Sie nur über eingeschränkten Speicherplatz verfügen und den Workflow „DAM-Update-Asset“ häufig ausführen, sollten Sie die Speicherbereinigung öfter planen.

#### Ausgabegenerierung zur Laufzeit {#runtime-rendition-generation}

Kunden verwenden Bilder unterschiedlicher Größen und Formate auf ihrer Website oder zur Weiterleitung an die Geschäftspartner. Da jede Darstellung den Footprint der Assets im Repository vergrößert, empfiehlt Adobe die umsichtige Verwendung dieser Funktion. Um die Menge der Ressourcen zu reduzieren, die für die Verarbeitung und Speicherung von Bildern benötigt wird, können Sie die Bilder statt als Ausgabeformate bei der Erfassung auch zur Laufzeit generieren.

Viele Kunden der Website implementieren ein Bild-Servlet, das Bilder zum Zeitpunkt ihrer Anforderung skaliert und beschneidet und der Veröffentlichungsinstanz damit eine zusätzliche Belastung auferlegt. Wenn diese Bilder zwischengespeichert werden können, lässt sich dieses Problem abmildern.

Ein alternativer Ansatz besteht darin, die Dynamic Media Classic-Technologie zu verwenden, um die Bildbearbeitung vollständig abzugeben. Darüber hinaus können Sie Brand Portal bereitstellen, das nicht nur die Verantwortung für die Generierung von Ausgabedarstellungen von der [!DNL Experience Manager]-Infrastruktur übernimmt, sondern auch die gesamte Veröffentlichungsstufe.

#### ImageMagick {#imagemagick}

Wenn Sie den Workflow „DAM-Update-Asset“ so anpassen, dass Ausgabeformate mit ImageMagick generiert werden, empfiehlt Adobe die Bearbeitung der Datei policy.xml unter */etc/ImageMagick/*. Standardmäßig beansprucht ImageMagick den gesamten verfügbaren Speicherplatz auf dem Betriebssystem-Volume sowie den verfügbaren Arbeitsspeicher. Nehmen Sie die folgenden Konfigurationsänderungen im Abschnitt `policymap` von policy.xml vor, um diese Ressourcen zu beschränken.

```xml
<policymap>
  <!-- <policy domain="system" name="precision" value="6"/> -->
  <policy domain="resource" name="temporary-path" value="/ephemeral0/imagemagick_tmp"/>
  <policy domain="resource" name="memory" value="1000MiB"/>
  <policy domain="resource" name="map" value="1000MiB"/>
  <!-- <policy domain="resource" name="area" value="1gb"/> -->
  <policy domain="resource" name="disk" value="10000MiB"/>
  <!-- <policy domain="resource" name="file" value="768"/> -->
  <policy domain="resource" name="thread" value="1"/>
  <policy domain="resource" name="throttle" value="50"/>
  <!-- <policy domain="resource" name="time" value="3600"/> -->
</policymap>
```

Stellen Sie darüber hinaus in der Datei *configure.xml* (alternativ in der Umgebungsvariable `MAGIC_TEMPORARY_PATH`) den Pfad zum temporären Ordner von ImageMagick auf eine Festplattenpartition ein, die über ausreichend Speicherplatz und IOPS verfügt.

>[!CAUTION]
>
>Eine falsche Konfiguration kann den Server instabil machen, wenn ImageMagick sämtlichen verfügbaren Festplattenspeicher verwendet. Die zur Verarbeitung großer Dateien mit ImageMagick erforderlichen Richtlinienänderungen können sich auf die Leistung von [!DNL Experience Manager] auswirken. Weitere Informationen finden Sie unter [Installieren und Konfigurieren von ImageMagick](best-practices-for-imagemagick.md).

>[!NOTE]
>
>Die ImageMagick-Dateien `policy.xml` und `configure.xml` befinden sich unter `/usr/lib64/ImageMagick-*/config/` anstelle von `/etc/ImageMagick/`. Weitere Informationen zu den Speicherorten der Konfigurationsdatei finden Sie in der [ImageMagick-Dokumentation](https://www.imagemagick.org/script/resources.php) .

Wenn Sie [!DNL Experience Manager] in Adobe Managed Services (AMS) verwenden, wenden Sie sich an den Support von Adobe, wenn Sie eine Vielzahl großer PSD- oder PSB-Dateien verarbeiten möchten. Experience Manager verarbeiten möglicherweise keine sehr hochauflösenden PSB-Dateien mit mehr als 30000 x 23000 Pixel.

<!-- 

#### Sub-asset generation and page extraction {#sub-asset-generation-and-page-extraction}

During asset uploads, AEM's workflow creates a separate asset for each page in PDF and Office documents. Each of these pages is an asset by itself, which consumes additional disk space, requires versioning and additional workflow processing. If you do not require separate pages, disable Sub Asset Generation and Page Extraction.

To disable Sub Asset generation, do the following:

1. Open the **[!UICONTROL Workflow Console]** tool by going to */libs/cq/workflow/content/console.html*

1. Select the **[!UICONTROL Models]** tab
1. Double click the **[!UICONTROL DAM Update Asset]** workflow model
1. Delete **[!UICONTROL Process Sub Asset]** step from **[!UICONTROL DAM Update Asset]** workflow model.

1. Click on **[!UICONTROL Save]**

To disable Page Extraction:

1. Open the **[!UICONTROL Workflow Console]** tool by going to */libs/cq/workflow/content/console.html*

1. Select the **[!UICONTROL Launchers]** tab
1. Select a launcher that launches **[!UICONTROL DAM Parse Word Documents]** workflow model 
1. Click **[!UICONTROL Edit]**
1. Select **[!UICONTROL Disable]**
1. Click **[!UICONTROL OK]**
1. Repeat steps 3-6 for other launcher items that use **DAM Parse Word Documents **workflow model 

-->

<!--
# Sub-asset generation and page extraction {#sub-asset-generation-and-page-extraction}

During asset uploads, AEM's workflow creates a separate asset for each page in PDF and Office documents. Each of these pages is an asset by itself, which consumes additional disk space, requires versioning and additional workflow processing. If you do not require separate pages, disable Sub Asset Generation and Page Extraction.

To disable Sub Asset generation, do the following:

1. Open the **[!UICONTROL Workflow Console]** tool by going to */libs/cq/workflow/content/console.html*

1. Select the **[!UICONTROL Models]** tab
1. Double click the **[!UICONTROL DAM Update Asset]** workflow model
1. Delete **[!UICONTROL Process Sub Asset]** step from **[!UICONTROL DAM Update Asset]** workflow model.

1. Click on **[!UICONTROL Save]**

To disable Page Extraction:

1. Open the **[!UICONTROL Workflow Console]** tool by going to */libs/cq/workflow/content/console.html*

1. Select the **[!UICONTROL Launchers]** tab
1. Select a launcher that launches **[!UICONTROL DAM Parse Word Documents]** workflow model.
1. Click **[!UICONTROL Edit]**
1. Select **[!UICONTROL Disable]**
1. Click **[!UICONTROL OK]**
1. Repeat steps 3-6 for other launcher items that use **DAM Parse Word Documents** workflow model.
-->

### XMP-Writeback {#xmp-writeback}

XMP-Writeback aktualisiert das Original-Asset, sobald Metadaten in AEM geändert werden. Folgende Änderungen werden vorgenommen:

* Das Asset selbst wird geändert.
* Eine Version des Assets wird erstellt.
* DAM-Update-Asset wird für das Asset ausgeführt.

Die aufgeführten Ergebnisse beanspruchen umfangreiche Ressourcen. Daher empfiehlt Adobe, [XMP-Writeback zu deaktivieren](https://helpx.adobe.com/de/experience-manager/kb/disable-xmp-writeback.html), wenn es nicht benötigt wird.

Wenn Sie eine große Menge an Metadaten importieren, kann es zu ressourcenintensiven XMP-Writeback-Aktivitäten kommen, falls das Flag für laufende Workflows gesetzt ist. Planen Sie einen solchen Import während Zeiten geringer Servernutzung, damit die Leistung anderer Benutzer nicht beeinträchtigt wird.

## Replikation {#replication}

Wenn Sie Assets in einer große Menge an veröffentlichten Instanzen replizieren (beispielsweise in einer Sites-Implementierung), empfiehlt Adobe die Kettenreplikation. In diesem Fall wird die Autorinstanz in eine einzelne Veröffentlichungsinstanz repliziert, die wiederum in die anderen Veröffentlichungsinstanzen repliziert wird und so die Autorinstanz freihält.

### Konfiguration der Kettenreplikation   {#configure-chain-replication}

1. Wählen Sie die Veröffentlichungsinstanz, mit der Sie die Replikationen verketten möchten.
1. Fügen Sie dieser Veröffentlichungsinstanz Agenten hinzu, die auf die anderen Veröffentlichungsinstanzen verweisen.
1. Aktivieren Sie für jeden dieser Replikationsagenten **[!UICONTROL Auf Empfang]** auf der Registerkarte **[!UICONTROL Trigger]** .

>[!NOTE]
>
>Adobe rät von der automatischen Aktivierung von Assets ab. Falls jedoch notwendig, sollte dies der letzte Schritt in einem Workflow, normalerweise „DAM-Update-Asset“, sein.

## Durchsuchen von Indizes   {#search-indexes}

Vergewissern Sie sich, dass Sie die neuesten Service Packs und leistungsrelevanten Hotfixes implementiert haben, da sie häufig Aktualisierungen der Systemindizes enthalten. Informationen zu je nach der AEM-Version anwendbaren Indexoptimierungen finden Sie unter [Tipps zur Leistungsoptimierung | 6.x](https://helpx.adobe.com/de/experience-manager/kb/performance-tuning-tips.html).

Erstellen Sie eigene Indizes für Abfragen, die Sie häufig ausführen. Weitere Informationen finden Sie unter [Methoden zur Analyse von langsamen Abfragen](https://aemfaq.blogspot.com/2014/08/oak-query-log-file-analyzer-tool.html) und [Erstellen benutzerdefinierter Indizes](/help/sites-deploying/queries-and-indexing.md). Weitere Einblicke in Best Practices bezüglich Abfragen und Indizes finden Sie unter [Best Practices für Abfragen und Indizierung](/help/sites-deploying/best-practices-for-queries-and-indexing.md).

### Lucene-Indexkonfigurationen {#lucene-index-configurations}

Einige Optimierungen können an den Oak-Indexkonfigurationen vorgenommen werden, die dazu beitragen können, die Leistung von [!DNL Experience Manager] Assets zu verbessern:

LuceneIndexProvider-Konfiguration aktualisieren:

1. Navigieren Sie zu /system/console/configMgrorg.apache.jackrabbit.oak.plugins.index.lucene.LuceneIndexProviderService
1. Aktivieren Sie **[!UICONTROL CopyOnRead , CopyOnWrite und Prefetch Index Files]** in Versionen vor [!DNL Experience Manager] 6.2. Diese Werte sind standardmäßig in [!DNL Experience Manager] 6.2 und höheren Versionen aktiviert.

Indexkonfigurationen aktualisieren, um die Zeit für Neuindizierungen zu verbessern:

1. Öffnen Sie CRXDe /crx/de/index.jsp und melden Sie sich als Benutzer mit Administratorrechten an.
1. Navigieren Sie zu /oak:index/lucene
1. Fügen Sie eine String[]-Eigenschaft mit dem Namen **[!UICONTROL excludedPaths]** mit den Werten &quot;/var&quot;, &quot;/etc/workflow/instances&quot;und &quot;/etc/replication&quot;hinzu.
1. Navigieren Sie zu „/oak:index/damAssetLucene“.
1. Fügen Sie eine String[]-Eigenschaft mit dem Namen **[!UICONTROL includedPaths]** mit einem Wert &quot;/content/dam&quot; hinzu.
1. Speichern

(Nur AEM 6.1 und 6.2) Aktualisieren Sie den Index „ntBaseLucene“, um die Leistung des Assets beim Löschen und Verschieben zu verbessern:

1. Navigieren Sie zu */oak:index/ntBaseLucene/indexRules/nt:base/properties*.
1. Fügen Sie zwei nt:unstructured -Knoten **[!UICONTROL slingResource]** und **[!UICONTROL damResolvedPath]** unter */oak:index/ntBaseLucene/indexRules/nt:base/properties* hinzu.
1. Legen Sie die folgenden Eigenschaften für die Knoten fest (wobei die Eigenschaften &quot;ordered&quot;und &quot;propertyIndex&quot;vom Typ *Boolesch* sind:

   slingResource

   name=&quot;sling:resource&quot;

   ordered=false

   propertyIndex= true

   type=&quot;String&quot;

   damResolvedPath

   name=&quot;dam:resolvedPath&quot;

   ordered=false

   propertyIndex=true

   type=&quot;String&quot;

1. Legen Sie für den Knoten „/oak:index/ntBaseLucene“ die Eigenschaft `reindex=true` fest.
1. Klicken Sie auf **[!UICONTROL Alle speichern]**
1. Überwachen Sie error.log, um zu sehen, wann die Indizierung abgeschlossen ist:

   Neuindizierung abgeschlossen für Indizes: [/oak:index/ntBaseLucene]

1. Den Abschluss der Indizierung können Sie auch nachverfolgen, indem Sie „/oak:index/ntBaseLucene“ in CRXDe aktualisieren. Die Eigenschaft für die Neuindizierung würde auf „false“ zurückgesetzt werden.
1. Nachdem die Indizierung abgeschlossen ist, kehren Sie zu CRXDe zurück und legen Sie die Eigenschaft **[!UICONTROL type]** für diese beiden Indizes auf &quot;disabled&quot;fest.

   * */oak:index/slingResource*
   * */oak:index/damResolvedPath*

1. Klicken Sie auf **[!UICONTROL Alle speichern]**

Lucene-Text-Extraktion deaktivieren:

Wenn Ihre Benutzer nicht nach dem Inhalt von Assets suchen müssen, beispielsweise nach Texten, die in PDF-Dokumenten enthalten sind, können Sie diese Funktion deaktivieren und damit die Indexleistung verbessern.

1. Gehen Sie zum Paketmanager [!DNL Experience Manager] /crx/packmgr/index.jsp .
1. Laden Sie das folgende Paket herunter und installieren Sie es.

[Datei laden](assets/disable_indexingbinarytextextraction-10.zip)

### guessTotal {#guess-total}

Verwenden Sie beim Erstellen von Abfragen mit großen Ergebnismengen den Parameter `guessTotal`, um eine übermäßige Belastung des Arbeitsspeichers bei der Ausführung zu vermeiden.

## Bekannte Probleme {#known-issues}

### Große Dateien {#large-files}

Zwei bekannte Probleme beziehen sich auf große Dateien in AEM. Bei Dateien, die größer als 2 GB sind, kann eine kalte Standby-Synchronisierung zu einem Speicherengpass führen. In einigen Fällen wird die Ausführung der Standby-Synchronisierung verhindert. In anderen Fällen stürzt die primäre Instanz ab. Dieses Szenario gilt für alle Dateien in [!DNL Experience Manager], die größer als 2 GB sind, einschließlich Inhaltspaketen.

Entsprechend kann es bei Dateien, die in einem gemeinsamen S3-Datenspeicher eine Größe von 2 GB erreichen, einige Zeit dauern, bis die Datei vollständig aus dem Cache in das Dateisystem gespeichert werden kann. Wenn Sie die Binaryless-Replikation verwenden, kann es passieren, dass die binären Daten vor dem Abschluss der Replikation nicht dauerhaft gespeichert werden. Diese Situation kann besonders dann zu Problemen führen, wenn die Verfügbarkeit der Daten wichtig ist, etwa in Abladungsszenarios.

## Leistungstests {#performance-testing}

Legen Sie für jede [!DNL Experience Manager]-Implementierung ein Leistungstestsystem fest, das Engpässe schnell erkennen und beheben kann. Konzentrieren Sie sich dabei auf die folgenden Schlüsselaspekte.

### Netzwerktests   {#network-testing}

Führen Sie für alle Aspekte, die die für Kunden relevante Netzwerkleistung betreffen, die folgenden Aufgaben aus:

* Testen Sie die Netzwerkleistung im Netzwerk des Kunden.
* Testen Sie die Netzwerkleistung im Adobe-Netzwerk. Arbeiten Sie bei AMS-Kunden mit CSE, um Tests innerhalb des Adobe-Netzwerks durchzuführen.
* Testen Sie die Netzwerkleistung an anderen Zugriffspunkten.
* Testen Sie unter Verwendung eines Benchmark-Tools für Netzwerke.
* Testen Sie mit dem Dispatcher.

### [!DNL Experience Manager] Instanztests {#aem-instance-testing}

Um Latenz zu minimieren und einen hohen Durchsatz durch effiziente CPU-Auslastung und Lastverteilung zu erzielen, überwachen Sie regelmäßig die Leistung Ihrer [!DNL Experience Manager]-Instanz. Führen Sie insbesondere die folgenden Aufgaben aus:

* Ausführen von Belastungstests für die [!DNL Experience Manager]-Instanz
* Überwachen Sie die Upload-Leistung und die Reaktionsfähigkeit der Benutzeroberfläche.

## [!DNL Experience Manager] Checkliste für die Leistung von Assets {#aem-assets-performance-checklist}

* Aktivieren Sie HTTPS, um alle geschäftlichen HTTP-Traffic-Sniffer zu umgehen.
* Verwenden Sie eine Kabelverbindung, um umfangreiche Assets hochzuladen.
* Legen Sie optimale JVM-Parameter fest.
* Konfigurieren Sie einen Dateisystem-DataStore oder einen S3-Datenspeicher.
* Die Erstellung von Unter-Assets deaktivieren. Ist diese Option aktiviert, erstellt AEM Workflow für jede Seite eines mehrseitigen Assets ein separates Asset. Jede dieser Seiten ist ein einzelnes Asset, das zusätzlichen Speicherplatz beansprucht, Versionierung und zusätzliche Workflow-Verarbeitung erfordert. Wenn Sie keine separaten Seiten benötigen, deaktivieren Sie die Aktivitäten zum Generieren von Unter-Assets und zum Extrahieren von Seiten.
* Aktivieren Sie Übergangs-Workflows.
* Passen Sie die Granite-Workflow-Warteschlangen an, um gleichzeitige Aufträge zu begrenzen.
* Konfigurieren Sie ImageMagick, um den Ressourcenverbrauch zu begrenzen.
* Entfernen Sie unnötige Schritte aus dem Workflow &quot;DAM-Update-Asset&quot;.
* Konfigurieren Sie den Workflow und die Versionsbereinigung.
* Optimieren Sie die Lucene-Indexkonfiguration.
* Optimieren Sie die Indizes mit den neuesten Service Packs und Hotfixes. Wenden Sie sich an die Adobe-Kundenunterstützung , um weitere verfügbare Indexoptimierungen zu erhalten.
* Verwenden Sie `guessTotal`, um die Abfrageleistung zu optimieren.
* Wenn Sie [!DNL Experience Manager] so konfigurieren, dass Dateitypen aus dem Inhalt der Dateien erkannt werden (durch Konfiguration von [!UICONTROL Day CQ DAM Mime Type Service] in der [!UICONTROL [!DNL Experience Manager] Web Console]), laden Sie viele Dateien außerhalb der Spitzenzeiten stapelweise hoch, da der Vorgang ressourcenintensiv ist.
