---
title: Handbuch zur Leistungsoptimierung von Assets
description: Wichtige Schwerpunktbereiche [!DNL Experience Manager] Konfiguration, Änderungen an Hardware-, Software- und Netzwerkkomponenten, um Engpässe zu beseitigen und die Leistung von [!DNL Experience Manager] Assets.
contentOwner: AG
feature: Asset Management
role: Architect,Admin
exl-id: 6c1bff46-f9e0-4638-9374-a9e820d30534
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3203'
ht-degree: 43%

---

# Handbuch zur Leistungsoptimierung von Assets {#assets-performance-tuning-guide}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Ein Adobe Experience Manager Assets-Setup enthält eine Reihe von Hardware-, Software- und Netzwerkkomponenten. Je nach Ihrem Bereitstellungsszenario benötigen Sie möglicherweise bestimmte Konfigurationsänderungen an den Hardware-, Software- und Netzwerkkomponenten, um Leistungsengpässe zu vermeiden.

Darüber hinaus hilft die Identifizierung und Einhaltung bestimmter Richtlinien zur Hardware- und Softwareoptimierung dabei, eine solide Grundlage zu schaffen, die Ihre [!DNL Experience Manager] Assets-Bereitstellung, um Erwartungen hinsichtlich Leistung, Skalierbarkeit und Zuverlässigkeit zu erfüllen.

Schlechte Leistung in [!DNL Experience Manager] Assets können sich auf die Benutzererfahrung im Hinblick auf interaktive Leistung, Asset-Verarbeitung, Download-Geschwindigkeit und andere Bereiche auswirken.

Daher gehört die Leistungsoptimierung zu den grundlegenden Aufgaben, bevor Sie Zielmetriken für Ihre Projekte erstellen.

In den folgenden Schlüsselbereichen sollten Sie besonders darauf achten, dass Leistungsprobleme erkannt und behoben werden, bevor sie sich auf das Benutzererlebnis auswirken.

## Plattform {#platform}

while [!DNL Experience Manager] wird auf einer Reihe von Plattformen unterstützt, hat Adobe die größte Unterstützung für native Tools unter Linux und Windows gefunden, was zu einer optimalen Leistung und Vereinfachung der Implementierung beiträgt. Idealerweise sollten Sie ein 64-Bit-Betriebssystem bereitstellen, um die hohen Speicheranforderungen eines [!DNL Experience Manager] Assets-Bereitstellung. Wie bei allen [!DNL Experience Manager] -Implementierung sollten Sie TarMK so weit wie möglich implementieren. TarMK kann zwar nicht über eine einzelne Autoreninstanz skaliert werden, erzielt jedoch erfahrungsgemäß eine bessere Leistung als MongoMK. Sie können TarMK-Ablade-Instanzen hinzufügen, um die Verarbeitungsleistung Ihres Workflows zu erhöhen. [!DNL Experience Manager] Assets-Bereitstellung.

### Temporärer Ordner  {#temp-folder}

Nutzen Sie einen Hochleistungsspeicher für das temporäre Java-Verzeichnis, um das Hochladen der Assets zu beschleunigen. Unter Linux und Windows können Sie beispielsweise ein RAM- oder SSD-Laufwerk verwenden. In Cloud-basierten Umgebungen kann ein äquivalenter Hochgeschwindigkeitsspeicher verwendet werden. In Amazon EC2 beispielsweise wird eine [Kurzfahrwerk](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/InstanceStorage.html) -Laufwerk kann für den temporären Ordner verwendet werden.

Bei einer großen Speicherkapazität des Servers kann ein RAM-Laufwerk konfiguriert werden. Führen Sie unter Linux die folgenden Befehle aus, um ein RAM-Laufwerk von 8 GB zu erstellen:

```shell
mkfs -q /dev/ram1 800000
 mkdir -p /mnt/aem-tmp
 mount /dev/ram1 /mnt/aem-tmp
 df -H | grep aem-tmp
```

Unter Windows OS müssten Sie einen Treiber eines Drittanbieters verwenden, um ein RAM-Laufwerk zu erstellen oder einfach Hochleistungsspeicher wie SSD zu verwenden.

Sobald das Tempo-Volumen mit hoher Leistung bereit ist, legen Sie den JVM-Parameter -Djava.io.tmpdir fest. Sie können beispielsweise den JVM-Parameter unter der Variablen „CQ_JVM_OPTS“ im Skript „bin/start“ von AEM einfügen:

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

Es wird empfohlen, den Datenspeicher vom Segmentspeicher zu trennen. [!DNL Experience Manager] Assets-Benutzer. Außerdem kann die Leistung durch die Konfiguration der Parameter `maxCachedBinarySize` und `cacheSizeInMB` maximiert werden. Stellen Sie `maxCachedBinarySize` auf die kleinste im Cache unterstützte Dateigröße ein. Geben Sie die Größe des Arbeitsspeicher-Cache für den Datenspeicher in `cacheSizeInMB` ein. Adobe empfiehlt, diesen Wert zwischen 2 und 10 % der gesamten Heap-Größe festzulegen. Lasttests können jedoch bei der Ermittlung der optimalen Einstellung helfen.

### Konfigurieren der Maximalgröße des gepufferten Bilder-Caches   {#configure-the-maximum-size-of-the-buffered-image-cache}

Verringern Sie beim Hochladen großer Mengen an Assets in Adobe Experience Manager zur Berücksichtigung unerwarteter Spitzen bei der Speichernutzung und zur Verhinderung von JVM-Fehlern mit OutOfMemoryErrors die konfigurierte Maximalgröße des gepufferten Bilder-Caches. Betrachten wir ein Beispiel mit einem System, das über eine maximale Heap-Größe (-`Xmx`param) von 5 GB verfügt und bei dem der Oak-Blob-Cache auf 1 GB und der Dokumenten-Cache auf 2 GB eingestellt ist. In diesem Fall würde der gepufferte Cache maximal 1,25 GB und Arbeitsspeicher belassen, was bei unerwarteten Spitzen nur 0,75 GB Arbeitsspeicher belassen würde.

Konfigurieren Sie die gepufferte Cachegröße in der OSGi-Web-Konsole. Legen Sie bei `https://host:port/system/console/configMgr/com.day.cq.dam.core.impl.cache.CQBufferedImageCache` die Eigenschaft `cq.dam.image.cache.max.memory` in Byte fest. 1073741824 entspricht beispielsweise 1 GB (1024 x 1024 x 1024 = 1 GB).

Von [!DNL Experience Manager] 6.1 SP1, wenn Sie eine `sling:osgiConfig` -Knoten für die Konfiguration dieser Eigenschaft verwenden, stellen Sie sicher, dass Sie den Datentyp auf &quot;Long&quot;einstellen. Weitere Informationen finden Sie unter [CQBufferedImageCache nutzt Heap während Asset-Uploads](https://helpx.adobe.com/de/experience-manager/kb/cqbufferedimagecache-consumes-heap-during-asset-uploads.html).

### Gemeinsame Datenspeicher   {#shared-data-stores}

Mit der Implementierung eines S3-Datenspeichers oder Shared File Datastore sparen Sie Speicherplatz auf der Festplatte und erhöhen den Netzwerkdurchsatz in großen Implementierungen. Weitere Informationen zu den Vor- und Nachteilen der Verwendung eines gemeinsamen Datenspeichers finden Sie unter [Anleitung zur Dimensionierung in Assets](assets-sizing-guide.md).

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

Adobe empfiehlt die Aktivierung von HTTPS, da viele Unternehmen über Firewalls verfügen, die den HTTP-Verkehr überprüfen und sich dadurch negativ auf Uploads auswirken und Dateien beschädigen. Stellen Sie bei großen Datei-Uploads sicher, dass Benutzer über Kabelverbindungen zum Netzwerk verfügen, da ein WLAN-Netzwerk schnell überfordert ist. Richtlinien zur Ermittlung von Netzwerkengpässen finden Sie unter [Anleitung zur Dimensionierung in Assets](assets-sizing-guide.md). Informationen zur Beurteilung der Netzwerkleistung mit einer Analyse der Netzwerktopologie finden Sie unter [Überlegungen zum Assets-Netzwerk](assets-network-considerations.md).

Welche Strategie der Netzwerkoptimierung Sie verwenden, hängt in erster Linie von der verfügbaren Bandbreite und der Last auf Ihrer [!DNL Experience Manager]-Instanz ab. Allgemeine Konfigurationsoptionen wie Firewalls oder Proxys können zur Verbesserung der Netzwerkleistung beitragen. Im Folgenden sind einige wichtige Punkte zu beachten:

* Stellen Sie je nach Instanztyp (klein, mittel, groß) sicher, dass Sie über ausreichend Netzwerkbandbreite für Ihre [!DNL Experience Manager] -Instanz. Dies ist besonders wichtig, wenn [!DNL Experience Manager] auf AWS gehostet wird.
* Wird Ihre [!DNL Experience Manager]-Instanz auf AWS gehostet, können Sie von einer flexiblen Skalierung profitieren. Vergrößern Sie die Instanz, wenn Benutzer eine hohe Belastung erwarten. Vergrößern Sie die Größe für mäßige/niedrige Auslastung.
* HTTPS: Die meisten Benutzer verfügen über Firewalls, die den HTTP-Traffic aufspüren. Dies kann sich negativ auf das Hochladen von Dateien auswirken oder Dateien während des Upload-Vorgangs beschädigen.
* Uploads großer Dateien: Stellen Sie sicher, dass Benutzer über Kabelverbindungen zum Netzwerk verfügen (WLAN-Verbindungen sind schnell gesättigt).

## Workflows {#workflows}

### Übergangs-Workflows {#transient-workflows}

Stellen Sie den Workflow DAM-Update-Asset nach Möglichkeit auf „Übergang“ ein. Die Einstellung trägt zu einer erheblichen Reduzierung des Overheads bei, der für die Verarbeitung der Workflows benötigt wird, da die Workflows in diesem Fall nicht die normalen Tracking- und Archivierungsprozesse durchlaufen.

>[!NOTE]
>
>Standardmäßig ist der Workflow DAM-Update-Asset auf Verlaufs in eingestellt [!DNL Experience Manager] 6.3. In diesem Fall können Sie das folgende Verfahren überspringen.

1. Öffnen `http://localhost:4502/miscadmin` auf [!DNL Experience Manager] -Instanz, die Sie konfigurieren möchten.

1. Erweitern Sie im Navigationsbaum **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]** > **[!UICONTROL dam]**.
1. Doppelklicken Sie auf **[!UICONTROL DAM-Update-Asset]**.
1. Wechseln Sie im unverankerten Tool-Fenster auf die Registerkarte **[!UICONTROL Seite]** und klicken Sie auf **[!UICONTROL Seiteneigenschaften]**.
1. Auswählen **[!UICONTROL Übergangs-Workflow]** Klicken **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Einige Funktionen unterstützen keine Übergangs-Workflows. Wenn [!DNL Experience Manager] Die Bereitstellung von Assets erfordert diese Funktionen, konfigurieren Sie keine Übergangs-Workflows.

   Wenn keine Übergangs-Workflows verwendet werden können, führen Sie regelmäßig Workflow-Bereinigungen durch, um archivierte DAM-Update-Asset-Workflows zu löschen. So verhindern Sie eine Beeinträchtigung der Systemleistung.

   Normalerweise sollten Sie die Bereinigungs-Workflows wöchentlich ausführen. In ressourcenintensiven Szenarien wie der umfangreichen Asset-Erfassung können Sie diese jedoch häufiger ausführen.

   Um die Workflow-Bereinigung zu konfigurieren, fügen Sie über die OSGi-Konsole eine neue Adobe Granite Workflow Purge-Konfiguration hinzu. Konfigurieren und planen Sie anschließend den Workflow als Teil des wöchentlichen Wartungsfensters.

   Wenn die Bereinigung zu lange läuft, wird die Zeit überschritten. Daher sollten Sie sicherstellen, dass Ihre Bereinigungsaufträge abgeschlossen sind, um zu vermeiden, dass Bereinigungs-Workflows aufgrund der hohen Anzahl an Workflows nicht abgeschlossen werden können.

   Wenn Sie zahlreiche Nicht-Verlaufs-Workflows ausgeführt haben, die Workflow-Instanzknoten erstellen, können Sie das Tool [ACS AEM Commons Workflow Remover](https://adobe-consulting-services.github.io/acs-aem-commons/features/workflow-remover.html) auf Ad-hoc-Basis ausführen. Es entfernt redundante, abgeschlossene Workflow-Instanzen sofort, ohne dass Sie auf die Ausführung des Adobe Granite-Workflow-Bereinigungsplaners warten müssen.

### Maximal parallel ausführbare Aufträge   {#maximum-parallel-jobs}

Standardmäßig kann [!DNL Experience Manager] maximal so viele Aufträge parallel ausführen wie Prozessoren auf dem Server vorhanden sind. In Zeiten hoher Auslastung ist diese Einstellung jedoch problematisch, da alle Prozessoren von den DAM-Update-Asset-Workflows beansprucht werden und dadurch die Reaktionsfähigkeit der Benutzeroberfläche verlangsamt wird und [!DNL Experience Manager] andere Prozesse zum Schutz von Serverleistung und -stabilität nicht ausführen kann. Es hat sich bewährt, diese Einstellung so zu wählen, dass nur die Hälfte der auf dem Server verfügbaren Prozessoren verwendet wird:

1. on [!DNL Experience Manager] Autor, gehen Sie zu [http://localhost:4502/system/console/slingevent](http://localhost:4702/system/console/slingevent).
1. Klicken Sie für jede für Ihre Implementierung relevante Workflow-Warteschlange, z. B. für die Ganite-Übergangs-Workflows-Warteschlange, auf Bearbeiten.
1. Ändern Sie den Wert Maximale Anzahl paralleler Aufträge und klicken Sie auf &quot;Speichern&quot;.

Das Festlegen einer Warteschlange auf die Hälfte der verfügbaren Prozessoren ist eine praktikable Lösung, mit der begonnen werden kann. Möglicherweise müssen Sie diese Zahl jedoch erhöhen oder verringern, um den maximalen Durchsatz zu erzielen und sie nach Umgebung zu verfeinern. Es gibt separate Warteschlangen für Übergangs- und Nicht-Übergangs-Workflows sowie für andere Prozesse wie beispielsweise externe Workflows. Wenn mehrere Warteschlangen, die auf 50 % der Prozessoren eingestellt sind, gleichzeitig aktiv sind, kann das System schnell überlastet werden. Die stark verwendeten Warteschlangen variieren je nach Benutzerimplementierung erheblich. Daher müssen Sie sie möglicherweise sorgfältig für maximale Effizienz konfigurieren, ohne die Serverstabilität zu beeinträchtigen.

### Entladen {#offloading}

Bei umfangreichen Workflows oder ressourcenintensiven Workflows, z. B. der Videotranskodierung, können Sie die Workflows &quot;DAM-Update-Asset&quot;an eine zweite Autoreninstanz abladen. Häufig besteht das Problem bei der Abladung darin, dass jede durch Abladen der Workflow-Verarbeitung eingesparte Last durch die Kosten der Replikation des Inhalts zwischen Instanzen umgekehrt ausgeglichen wird.

Als [!DNL Experience Manager] 6.2 und mit einem Feature Pack für [!DNL Experience Manager] 6.1, können Sie die Abladung mit der Binärdatei-losen Replikation durchführen. In diesem Modell verwenden die Autoreninstanzen einen gemeinsamen Datenspeicher und senden die Metadaten nur über die Vorwärtsreplikation hin und her. Dieser Ansatz funktioniert zwar gut mit einem freigegebenen Dateidatenspeicher, es kann jedoch Probleme mit einem S3-Datenspeicher geben. Da Hintergrundschreibungs-Threads Latenzzeiten verursachen können, kann es sein, dass ein Asset möglicherweise nicht in den Datenspeicher geschrieben wurde, bevor der Abladevorgang beginnt.

### Konfiguration von DAM-Update-Asset {#dam-update-asset-configuration}

Der Workflow &quot;DAM-Update-Asset&quot;enthält eine vollständige Suite von Schritten, die für Aufgaben wie die Dynamic Media Classic-PTIFF-Generierung und InDesign Server-Integration konfiguriert sind. Die meisten Benutzer benötigen jedoch nicht alle diese Schritte. Adobe empfiehlt die Erstellung einer benutzerdefinierten Kopie des DAM-Update-Asset-Workflow-Modells, in der alle unnötigen Schritte entfernt wurden. Ändern Sie dann die Launcher für DAM-Update-Asset so, dass sie auf das neue Modell zeigen.

>[!NOTE]
>
>Wenn Sie den Workflow DAM-Update-Asset häufig ausführen, kann hierdurch die Größe Ihres Dateidatenspeichers deutlich ansteigen. Die Ergebnisse eines von Adobe durchgeführten Experiments haben gezeigt, dass die Datenspeichergröße um ca. 400 GB erhöht werden kann, wenn innerhalb von 8 Stunden etwa 5.500 Workflows ausgeführt werden.
>
>Es handelt sich um eine vorübergehende Erhöhung, und der Datenspeicher wird nach Ausführung der Speicherbereinigungsaufgabe wieder in seiner ursprünglichen Größe angezeigt.
>
>In der Regel wird die Speicherbereinigung wöchentlich zusammen mit anderen geplanten Wartungsaufgaben ausgeführt.
>
>Wenn Sie nur über eingeschränkten Speicherplatz verfügen und den Workflow „DAM-Update-Asset“ häufig ausführen, sollten Sie die Speicherbereinigung öfter planen.

#### Ausgabegenerierung zur Laufzeit {#runtime-rendition-generation}

Kunden verwenden Bilder unterschiedlicher Größe und Formate auf ihrer Website oder zur Weitergabe an Geschäftspartner. Da jede Ausgabedarstellung den Platzbedarf des Assets im Repository erhöht, empfiehlt Adobe, diese Funktion umsichtig zu verwenden. Um die für die Verarbeitung und Speicherung von Bildern erforderliche Ressourcenmenge zu reduzieren, können Sie diese Bilder zur Laufzeit und nicht als Ausgabeformate während der Aufnahme generieren.

Viele Sites-Kunden implementieren ein Bildservlet, das die Größe von Bildern zum Zeitpunkt ihrer Anforderung ändert und zuschneidet. Dadurch wird die Veröffentlichungsinstanz zusätzlich geladen. Solange diese Bilder jedoch zwischengespeichert werden können, kann die Herausforderung abgemildert werden.

Ein alternativer Ansatz besteht darin, die Dynamic Media Classic-Technologie zu verwenden, um die Bildbearbeitung vollständig abzugeben. Darüber hinaus können Sie Brand Portal bereitstellen, das nicht nur die Verantwortung für die Generierung von Ausgabedarstellungen vom [!DNL Experience Manager] Infrastruktur, aber auch die gesamte Veröffentlichungsstufe.

#### ImageMagick {#imagemagick}

Wenn Sie den Workflow DAM Update Asset anpassen, um Ausgabedarstellungen mit ImageMagick zu generieren, empfiehlt Adobe, die Datei policy.xml unter */etc/ImageMagick/*. Standardmäßig beansprucht ImageMagick den gesamten verfügbaren Speicherplatz auf dem Betriebssystem-Volume sowie den verfügbaren Arbeitsspeicher. Nehmen Sie die folgenden Konfigurationsänderungen in der `policymap` -Abschnitt von policy.xml verwenden, um diese Ressourcen zu beschränken.

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

Legen Sie außerdem den Pfad des temporären Ordners von ImageMagick im *configure.xml* Datei (oder durch Festlegen der Umgebungsvariablen) `MAGIC_TEMPORARY_PATH`) auf eine Festplattenpartition mit genügend Speicherplatz und IOPS.

>[!CAUTION]
>
>Eine falsche Konfiguration kann den Server instabil machen, wenn ImageMagick sämtlichen verfügbaren Festplattenspeicher verwendet. Die Regeländerungen, die zum Verarbeiten großer Dateien mit ImageMagick erforderlich sind, können sich auf die Leistung von [!DNL Experience Manager] auswirken. Weitere Informationen finden Sie unter [Installieren und Konfigurieren von ImageMagick](best-practices-for-imagemagick.md).

>[!NOTE]
>
>ImageMagick `policy.xml` und `configure.xml` -Dateien finden Sie unter `/usr/lib64/ImageMagick-*/config/` anstelle von `/etc/ImageMagick/`. Siehe [ImageMagick-Dokumentation](https://www.imagemagick.org/script/resources.php) für Details zu den Speicherorten der Konfigurationsdatei.

Wenn Sie [!DNL Experience Manager] in Adobe Managed Services (AMS) verwenden, wenden Sie sich an den Adobe Support, wenn Sie viele große PSD- oder PSB-Dateien verarbeiten möchten. Experience Manager verarbeitet möglicherweise keine PSB-Dateien mit sehr hoher Auflösung, die mehr als 30000 x 23000 Pixel umfassen.

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

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).

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

XMP Writeback aktualisiert das Original-Asset, sobald Metadaten in AEM geändert werden, was zu Folgendem führt:

* Das Asset selbst wird geändert
* Eine Version des Assets wird erstellt
* DAM-Update-Asset wird für das Asset ausgeführt.

Die aufgeführten Ergebnisse beanspruchen umfangreiche Ressourcen. Daher empfiehlt die Adobe, [Deaktivieren XMP Writeback](https://helpx.adobe.com/de/experience-manager/kb/disable-xmp-writeback.html), wenn dies nicht erforderlich ist.

Das Importieren einer großen Menge an Metadaten kann zu ressourcenintensiven XMP Writeback-Aktivitäten führen, wenn das Flag &quot;Workflows ausführen&quot;aktiviert ist. Planen Sie einen solchen Import während der schlanken Server-Nutzung, damit die Leistung für andere Benutzer nicht beeinträchtigt wird.

## Replikation {#replication}

Beim Replizieren von Assets auf eine große Anzahl von Veröffentlichungsinstanzen, z. B. in einer Sites-Implementierung, empfiehlt Adobe die Verwendung der Kettenreplikation. In diesem Fall repliziert die Autoreninstanz auf eine einzelne Veröffentlichungsinstanz, die wiederum auf die anderen Veröffentlichungsinstanzen repliziert, wodurch die Autoreninstanz freigeschaltet wird.

### Konfiguration der Kettenreplikation   {#configure-chain-replication}

1. Wählen Sie die Veröffentlichungsinstanz, mit der Sie die Replikationen verketten möchten.
1. Fügen Sie in dieser Veröffentlichungsinstanz Replikationsagenten hinzu, die auf die anderen Veröffentlichungsinstanzen verweisen
1. Aktivieren Sie in jedem dieser Replikationsagenten die Option **[!UICONTROL Bei Erhalt]** auf **[!UICONTROL Trigger]** tab

>[!NOTE]
>
>Adobe rät von der automatischen Aktivierung von Assets ab. Bei Bedarf empfiehlt Adobe jedoch, dies als letzten Schritt in einem Workflow zu tun, normalerweise DAM Update Asset .

## Durchsuchen von Indizes   {#search-indexes}

Vergewissern Sie sich, dass Sie die neuesten Service Packs und leistungsrelevanten Hotfixes implementiert haben, da sie häufig Aktualisierungen der Systemindizes enthalten. Informationen zu je nach der AEM-Version anwendbaren Indexoptimierungen finden Sie unter [Tipps zur Leistungsoptimierung | 6.x](https://helpx.adobe.com/de/experience-manager/kb/performance-tuning-tips.html).

Erstellen Sie eigene Indizes für Abfragen, die Sie häufig ausführen. Weitere Informationen finden Sie unter [Methoden zur Analyse von langsamen Abfragen](https://aemfaq.blogspot.com/2014/08/oak-query-log-file-analyzer-tool.html) und [Erstellen benutzerdefinierter Indizes](/help/sites-deploying/queries-and-indexing.md). Weitere Einblicke in Best Practices bezüglich Abfragen und Indizes finden Sie unter [Best Practices für Abfragen und Indizierung](/help/sites-deploying/best-practices-for-queries-and-indexing.md).

### Lucene-Indexkonfigurationen {#lucene-index-configurations}

Einige Optimierungen können an den Oak-Indexkonfigurationen vorgenommen werden, die zur Verbesserung beitragen können [!DNL Experience Manager] Asset-Leistung:

Aktualisieren Sie die LuceneIndexProvider-Konfiguration:

1. Navigieren Sie zu /system/console/configMgrorg.apache.jackrabbit.oak.plugins.index.lucene.LuceneIndexProviderService
1. Aktivieren **[!UICONTROL CopyOnRead , CopyOnWrite und Prefetch Index Files]** in Versionen vor [!DNL Experience Manager] 6.2. Diese Werte sind standardmäßig in [!DNL Experience Manager] 6.2 und neuere Versionen.

Aktualisieren Sie Indexkonfigurationen, um die Neuindizierungszeit zu verbessern:

1. Öffnen Sie CRXDe /crx/de/index.jsp und melden Sie sich als Administrator an
1. Navigieren Sie zu /oak:index/lucene
1. Zeichenfolge hinzufügen[] Eigenschaft namens **[!UICONTROL excludedPaths]** mit den Werten &quot;/var&quot;, &quot;/etc/workflow/instances&quot;und &quot;/etc/replication&quot;
1. Navigieren Sie zu „/oak:index/damAssetLucene“.
1. Zeichenfolge hinzufügen[] Eigenschaft namens **[!UICONTROL includedPaths]** mit einem Wert &quot;/content/dam&quot;
1. Speichern

(Nur AEM 6.1 und 6.2) Aktualisieren Sie den Index „ntBaseLucene“, um die Leistung des Assets beim Löschen und Verschieben zu verbessern:

1. Navigieren Sie zu */oak:index/ntBaseLucene/indexRules/nt:base/properties*.
1. Fügen Sie zwei nt:unstrukturierte Knoten hinzu **[!UICONTROL slingResource]** und **[!UICONTROL damResolvedPath]** under */oak:index/ntBaseLucene/indexRules/nt:base/properties*
1. Legen Sie die folgenden Eigenschaften auf den Knoten fest (wobei die Eigenschaften &quot;ordered&quot;und &quot;propertyIndex&quot;vom Typ sind *Boolesch*:

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

1. Sie können auch sehen, dass die Indizierung abgeschlossen ist, indem Sie den Knoten /oak:index/ntBaseLucene in CRXDe aktualisieren, da die Eigenschaft für die Neuindizierung wieder auf &quot;false&quot;zurückgesetzt wird.
1. Nachdem die Indizierung abgeschlossen ist, kehren Sie zu CRXDe zurück und legen Sie die **[!UICONTROL type]** -Eigenschaft für diese beiden Indizes deaktiviert werden

   * */oak:index/slingResource*
   * */oak:index/damResolvedPath*

1. Klicken Sie auf **[!UICONTROL Alle speichern]**

Lucene-Textextraktion deaktivieren:

Wenn Ihre Benutzer nicht in der Lage sein müssen, den Inhalt von Assets zu durchsuchen, z. B. nach dem in PDF-Dokumenten enthaltenen Text, können Sie die Indexleistung verbessern, indem Sie diese Funktion deaktivieren.

1. Navigieren Sie zu [!DNL Experience Manager] Package Manager /crx/packmgr/index.jsp
1. Hochladen und Installieren des unten stehenden Pakets

[Datei abrufen](assets/disable_indexingbinarytextextraction-10.zip)

### guessTotal {#guess-total}

Verwenden Sie beim Erstellen von Abfragen mit großen Ergebnismengen den Parameter `guessTotal`, um eine übermäßige Belastung des Arbeitsspeichers bei der Ausführung zu vermeiden.

## Bekannte Probleme {#known-issues}

### Große Dateien {#large-files}

Zwei bekannte Probleme beziehen sich auf große Dateien in AEM. Wenn Dateien größer als 2 GB sind, kann es bei der Cold-Standby-Synchronisation zu Speicherausfällen kommen. In einigen Fällen verhindert dies die Ausführung der Standby-Synchronisation. In anderen Fällen führt dies zum Absturz der primären Instanz. Dieses Szenario gilt für alle Dateien in [!DNL Experience Manager], die größer als 2 GB sind, darunter auch Inhaltspakete.

Wenn Dateien bei Verwendung eines freigegebenen S3-Datenspeichers eine Größe von 2 GB erreichen, kann es auch einige Zeit dauern, bis die Datei vollständig aus dem Cache in das Dateisystem persistiert wird. Wenn Sie die Binaryless-Replikation verwenden, kann es passieren, dass die binären Daten vor dem Abschluss der Replikation nicht dauerhaft gespeichert werden. Diese Situation kann zu Problemen führen, insbesondere wenn die Verfügbarkeit von Daten wichtig ist, z. B. bei Abladeszenarien.

## Leistungstests {#performance-testing}

Erstellen Sie für jede [!DNL Experience Manager]-Implementierung einen Plan für Leistungstests, der Engpässe schnell identifizieren und beseitigen kann. Konzentrieren Sie sich dabei auf die folgenden Schlüsselaspekte.

### Netzwerktests   {#network-testing}

Führen Sie für alle vom Kunden angesprochenen Probleme mit der Netzwerkleistung die folgenden Aufgaben aus:

* Testen Sie die Netzwerkleistung innerhalb des Kundennetzwerks.
* Testen Sie die Netzwerkleistung im Adobe-Netzwerk. Arbeiten Sie bei AMS-Kunden mit CSE, um Tests innerhalb des Adobe-Netzwerks durchzuführen.
* Testen der Netzwerkleistung von einem anderen Access Point
* Verwenden eines Netzwerk-Benchmark-Tools
* Testen mit dem Dispatcher

### [!DNL Experience Manager] Instanztests {#aem-instance-testing}

Um Latenzzeiten zu minimieren und einen hohen Durchsatz durch effiziente CPU-Auslastung und Lastverteilung zu erzielen, überwachen Sie die Leistung Ihrer [!DNL Experience Manager] regelmäßig installiert werden. Führen Sie insbesondere die folgenden Aufgaben aus:

* Führen Sie Belastungstests für die [!DNL Experience Manager] instance
* Überwachen Sie die Upload-Leistung und die Reaktionsfähigkeit der Benutzeroberfläche

## [!DNL Experience Manager] Checkliste für die Leistung von Assets {#aem-assets-performance-checklist}

* Aktivieren Sie „HTTPS“, um alle vom Unternehmen installierten Sniffer für HTTP-Traffic zu umgehen.
* Verwenden Sie eine Kabelverbindung, um umfangreiche Assets hochzuladen.
* Legen Sie optimale JVM-Parameter fest.
* Konfigurieren Sie einen Dateisystem-DataStore oder einen S3-Datenspeicher.
* Deaktivieren Sie das Erzeugen von Unter-Assets. Ist diese Option aktiviert, erstellt der Workflow in AEM für jede Seite eines mehrseitigen Assets ein separates Asset. Jede dieser Seiten ist selbst Asset, das zusätzlichen Speicherplatz belegt sowie Versionierung und zusätzliche Workflow-Verarbeitung erfordert. Wenn Sie keine separaten Seiten benötigen, deaktivieren Sie das Erzeugen von Unter-Assets und die Seitenextraktion.
* Aktivieren Sie Übergangs-Workflows.
* Stimmen Sie die Granit-Workflow-Warteschlangen ab, um gleichzeitige Aufträge einzuschränken.
* Konfigurieren Sie ImageMagick, um den Ressourcenverbrauch zu begrenzen.
* Entfernen Sie unnötige Schritte aus dem DAM-Update-Asset-Workflow.
* Konfigurieren Sie Workflow- und Versionsbereinigung.
* Optimieren Sie die Lucene-Indexkonfiguration.
* Optimieren Sie die Indizes mit den neuesten Service Packs und Hotfixes. Fragen Sie den Adobe-Kunden-Support nach verfügbaren zusätzlichen Indexoptimierungen.
* Verwendung `guessTotal` , um die Abfrageleistung zu optimieren.
* Wenn Sie [!DNL Experience Manager] zur Erkennung von Dateitypen aus dem Inhalt der Dateien (durch Konfiguration [!UICONTROL Day CQ DAM Mime Type Service] im [!UICONTROL [!DNL Experience Manager] Web-Konsole]), laden Sie viele Dateien außerhalb der Spitzenzeiten stapelweise hoch, da der Vorgang ressourcenintensiv ist.
