---
title: Handbuch zur Assets-Dimensionierung
description: 'Best Practices zur Bestimmung effizienter Metriken zur Abschätzung der für die Bereitstellung von AEM Assets erforderlichen Infrastruktur und Ressourcen. '
uuid: f847c07d-2a38-427a-9c38-8cdca3a1210c
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 82c1725e-a092-42e2-a43b-72f2af3a8e04
feature: Asset Management
role: Architect,Administrator
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '1862'
ht-degree: 88%

---


# Handbuch zur Assets-Dimensionierung {#assets-sizing-guide}

Beim Dimensionieren der Umgebung für eine Adobe Experience Manager (AEM) Assets-Implementierung gilt es sicherzustellen, dass hinsichtlich Festplatte, CPU, Arbeitsspeicher, I/O und Netzwerkdurchsatz genügend Ressourcen verfügbar sind. Zur Dimensionierung dieser Ressourcen muss bekannt sein, wie viele Assets in das System geladen werden. Wenn keine bessere Metrik verfügbar ist, können Sie die Größe der vorhandenen Bibliothek durch das Alter der Bibliothek dividieren, um die Rate zu ermitteln, mit der Assets erstellt werden.

## Festplatte {#disk}

### Datenspeicher {#datastore}

Ein häufiger Fehler bei der Dimensionierung des erforderlichen Festplattenspeichers für eine Assets-Implementierung besteht darin, die Berechnungen auf der Größe der in das System aufzunehmenden Rohbilder basieren zu lassen. Standardmäßig erstellt AEM zum Rendering der AEM-Benutzeroberflächenelemente drei Wiedergaben zusätzlich zum Originalbild. In vorherigen Implementierungen haben sich diese Wiedergaben als doppelt so groß wie die aufgenommenen Assets herausgestellt. 

Die meisten Benutzer definieren benutzerdefinierte Wiedergaben neben den standardmäßig verfügbaren Wiedergaben. Zusätzlich zu den Wiedergaben können Sie mit AEM Assets Unter-Assets aus gängigen Dateitypen wie InDesign und Illustrator extrahieren.

Schließlich sorgen die AEM-Versionierungsfunktionen dafür, dass Duplikate der Assets im Versionsverlauf gespeichert werden. Sie können die Versionen so konfigurieren, dass Bereinigungen häufig durchgeführt werden. Jedoch entscheiden sich viele Benutzer für eine längere Aufbewahrung der Versionen im System, wodurch zusätzlicher Speicherplatz belegt wird.

Angesichts dieser Faktoren benötigen Sie eine Methodik für eine ausreichend genaue Berechnung des Speicherplatzes, um Benutzer-Assets aufbewahren zu können.

1. Bestimmen Sie die Größe und die Anzahl der Assets, die in das System geladen werden.
1. Beschaffen Sie sich eine repräsentative Stichprobe der Assets, die in AEM hochgeladen werden sollen. Wenn Sie beispielsweise PSD-, JPG-, AI- und PDF-Dateien in das System laden möchten, benötigen Sie mehrere Beispielbilder für jedes Dateiformat. Außerdem sollten diese Stichproben repräsentativ für die verschiedenen Dateigrößen und die Komplexität der Bilder sein.
1. Definieren Sie die zu verwendenden Wiedergaben.
1. Erstellen Sie die Wiedergaben in AEM mit ImageMagick oder den Creative Cloud-Anwendungen von Adobe. Erstellen Sie neben den von den Benutzern angegebenen Wiedergaben sofort einsetzbare Standardwiedergaben. Für Benutzer, die Dynamic Media Classic implementieren, können Sie die IC-Binärdatei verwenden, um die PTIFF-Darstellungen zu generieren, die in AEM gespeichert werden sollen.
1. Wenn Sie die Verwendung von Unter-Assets beabsichtigen, generieren Sie diese für die entsprechenden Dateitypen. Informationen zum Generieren von Unter-Asset-Seiten aus InDesign-Dateien oder PNG-/PDF-Dateien aus Illustrator-Ebenen finden Sie in der entsprechenden Onlinedokumentation.
1. Vergleichen Sie die Größe der Ausgabebilder, Wiedergaben und Unter-Assets mit den Originalbildern. So können Sie den erwarteten Wachstumsfaktor beim Laden des Systems generieren. Wenn Sie z. B. Wiedergaben und Unter-Assets mit einer kombinierten Größe von 3 GB nach der Verarbeitung von 1 GB an Assets erzeugen, lautet der Wiedergabe-Wachstumsfaktor 3.
1. Ermitteln Sie, wie lange die einzelnen Asset-Versionen maximal im System aufbewahrt werden sollen.
1. Ermitteln Sie, wie oft vorhandene Assets im System geändert werden. Wenn AEM als Collaboration-Hub in kreativen Workflows dient, gibt es viele Änderungen. Wenn nur fertiggestellte Assets in das System hochgeladen werden, ist diese Zahl wesentlich niedriger.
1. Ermitteln Sie, wie viele Assets jeden Monat in das System geladen werden. Wenn Sie sich nicht sicher sind, bestimmen Sie die Anzahl der aktuell verfügbaren Assets und dividieren Sie diese Zahl durch das Alter des ältesten Assets, um einen ungefähren Wert zu berechnen. 

Mit den Schritten 1–9 können Sie Folgendes ermitteln:

* Rohgröße der zu ladenden Assets
* Anzahl der zu ladenden Assets
* Wiedergabe-Wachstumsfaktor
* Anzahl der Asset-Änderungen pro Monat
* Anzahl der Monate für die Aufbewahrung von Asset-Versionen
* Anzahl der neu geladenen Assets pro Monat
* Wachstumsjahre, für die Speicher reserviert werden muss

Sie können diese Zahlen in der Tabelle zur Netzwerkdimensionierung angeben, um den Gesamtspeicherbedarf für den Datenspeicher zu ermitteln. Zudem lässt sich so nützlicherweise feststellen, wie sich die Aufbewahrung von Asset-Versionen oder die Änderung von Assets in AEM auf das Festplattenwachstum auswirkt. 

Die in das Tool aufgefüllten Beispieldaten zeigen, wie wichtig die Ausführung der genannten Schritte ist. Wenn Sie den Datenspeicher allein basierend auf dem Ladevorgang der Rohbilder (1 TB) bemessen, ist eine Unterbewertung der Repositorygröße um dem Faktor 15 möglich.

[Datei laden](assets/disk_sizing_tool.xlsx)

### Freigegebene Datenspeicher {#shared-datastores}

Bei großen Datenspeichern können Sie einen freigegebenen Datenspeicher entweder über einen freigegebenen Dateidatastore auf einem angeschlossenen Laufwerk oder über einen S3-Datenspeicher implementieren. In diesem Fall müssen einzelne Instanzen keine Kopie der Binärdateien aufbewahren. Außerdem unterstützt ein freigegebener Datenspeicher Binaryless-Replikationen und reduziert die Bandbreite zum Replizieren von Assets in Veröffentlichungsumgebungen oder Abladeinstanzen.

#### Anwendungsfälle {#use-cases}

Der Datenspeicher kann gemeinsam von primärer und Standby-Autoreninstanz genutzt werden, um den zeitlichen Aufwand zum Aktualisieren der Standby-Instanz mit Änderungen der primären Instanz zu minimieren. Adobe empfiehlt die gemeinsame Nutzung des Datenspeichers zwischen primärer Autoreninstanz und Ablade-Autoreninstanzen, um Mehraufwand bei der Workflow-Abladung zu reduzieren. Sie können den Datenspeicher zudem zwischen Autor- und Veröffentlichungsinstanzen freigeben, um den Traffic während der Replikation zu minimieren.

#### Nachteile  {#drawbacks}

Aufgrund gewisser Fallstricke wird die Freigabe eines Datenspeichers nicht in allen Fällen empfohlen.

#### Single Point of Failure  {#single-point-of-failure}

Mit einem freigegebenen Datenspeicher entsteht ein Single Point of Failure in einer Infrastruktur. Stellen Sie sich ein Szenario vor, bei dem Ihr System eine Autoreninstanz und zwei Veröffentlichungsinstanzen aufweist, jeweils mit einem eigenen Datenspeicher. Stürzt einer der Datenspeicher ab, können die beiden anderen nach wie vor ausgeführt werden. Wenn der Datenspeicher jedoch gemeinsam genutzt wird, kann der Ausfall einer einzigen Festplatte die gesamte Infrastruktur zum Erliegen bringen. Stellen Sie daher sicher, dass Sie eine Sicherung des freigegebenen Datenspeichers aufbewahren, über die Sie den Datenspeicher schnell wiederherstellen können.

Den AWS S3-Dienst für freigegebene Datenspeicher bereitzustellen, wird vorgezogen, weil hierdurch die Wahrscheinlichkeit eines Ausfalls gegenüber normalen Festplattenarchitekturen deutlich reduziert wird.

#### Höhere Komplexität  {#increased-complexity}

Freigegebene Datenspeicher erhöhen ebenfalls die Komplexität solcher Vorgänge, etwa der automatischen Speicherbereinigung. Normalerweise kann die automatische Speicherbereinigung für einen Standalone-Datenspeicher mit einem einzigen Klick initiiert werden. Allerdings setzen freigegebene Datenspeicher zusätzlich zu der auf jedem Knoten tatsächlich durchgeführten Bereinigung Mark-Sweep-Vorgänge auf jedem Mitglied voraus, das den Datenspeicher nutzt.

Bei AWS-Vorgängen können, wenn statt des Aufbaus eines RAID-Arrays von EBS-Volumes ein zentraler Speicherort (über S3) implementiert wird, die Komplexität und die Betriebsrisiken auf dem System deutlich kompensiert werden.

#### Leistungsprobleme  {#performance-concerns}

Bei einem freigegebenen Datenspeicher müssen die Binärdateien auf einem Laufwerk gespeichert werden, das an ein Netzwerk angebunden und für alle Instanzen freigegeben ist. Da der Zugriff auf diese Binärdateien über ein Netzwerk erfolgt, wird die Systemleistung beeinträchtigt. Eine schnelle Netzwerkverbindung zu einem schnellen Festplattenarray kann diesen Effekt teilweise auffangen. Dies ist jedoch eine teure Angelegenheit. Im Falle von AWS-Vorgängen liegen alle Festplatten remote vor, sodass eine Netzwerkanbindung erforderlich ist. Auf flüchtigen Volumes gehen Daten beim Starten und Stoppen von Instanzen verloren.

#### Latenz  {#latency}

Latenz in S3-Implementierungen ist auf die im Hintergrund durchgeführten Schreibthreads zurückzuführen. Für Sicherungsvorgänge müssen diese Latenz und etwaige Abladevorgänge berücksichtigt werden. Das S3-Asset ist beim Start eines Abladeauftrags unter Umständen nicht in S3 vorhanden. Außerdem bleiben Lucene-Indizes möglicherweise unvollständig, wenn eine Sicherung durchgeführt wird. Dies gilt für alle zeitempfindlichen Dateien, die in einen S3-Datenspeicher geschrieben werden und auf die von einer anderen Instanz zugegriffen wird.

### Knotenspeicher/Dokumentspeicher  {#node-store-document-store}

Es ist schwierig, genaue Dimensionierungszahlen für einen Knotenspeicher oder Dokumentspeicher zu ermitteln, da Ressourcen durch Folgendes verbraucht werden:

* Asset-Metadaten
* Asset-Versionen
* Auditprotokolle
* Archivierte und aktive Workflows

Binärdateien in einem Datenspeicher aufzubewahren bedeutet, dass entsprechender Speicherplatz belegt wird. Die meisten Repositorys sind zwar kleiner als 100 GB, aber es sind auch größere Repositorys mit bis zu 1 TB möglich. Zusätzlich zur Offlinekomprimierung muss genügend freier Speicher auf dem Volume vorhanden sein, damit das komprimierte Repository neben der vorab komprimierten Version neu geschrieben werden kann. Eine geeignete Faustregel: Dimensionieren Sie die Festplatte so, dass sie 1,5-mal so groß ist wie die erwartete Repositorygröße.

Verwenden Sie für das Repository SSDs oder Festplatten mit einem IOPS-Level über 3000. Damit im Zuge der IOPS keine Leistungsengpässe entstehen, überwachen Sie die CPU-I/O-Wartelevel auf frühe Problemanzeichen.

[Datei laden](assets/aem_environment_sizingtool.xlsx)

## Netzwerk {#network}

Für AEM Assets gibt es eine Reihe von Anwendungsbeispielen, in denen die Netzwerkleistung eine größere Bedeutung hat als bei vielen anderen unserer AEM-Projekte. Ein Kunde kann über einen schnellen Server verfügen. Wenn die Netzwerkverbindung jedoch nicht groß genug ist, um die Belastung der Benutzer zu unterstützen, die Assets vom System hochladen und herunterladen, dann scheint sie immer noch langsam zu sein. Es gibt eine gute Methode zur Bestimmung des Choke-Punkts in der Netzwerkverbindung eines Benutzers mit AEM unter [AEM Asset-Überlegungen für Benutzererfahrung, Instanzgrößenänderung, Workflow-Auswertung und Netzwerktopologie](assets-network-considerations.md).

## WebDAV {#webdav}

Wird dazu noch die AEM Desktop App genutzt, verschärfen sich die Netzwerkprobleme aufgrund von Ineffizienzen im WebDAV-Protokoll weiter.

Um diese Ineffizienzen zu verdeutlichen, hat Adobe die Systemleistung mit WebDAV unter OS X getestet. Ein 3,5 MB große InDesign-Datei wurde geöffnet, bearbeitet und mit Änderungen gespeichert. Folgendes wurde beobachtet:

* Insgesamt wurden 100 HTTP-Anforderungen generiert, um den Vorgang abzuschließen.
* Die Datei wurde viermal über HTTP hochgeladen.
* Die Datei wurde einmal über HTTP heruntergeladen.
* Der gesamte Vorgang dauerte 42 Sekunden
* Insgesamt wurden 18 MB an Daten übertragen.

Beim Analysieren der durchschnittlichen Speicherzeit für Dateien über WebDAV wurde eine deutliche Leistungszunahme festgestellt, als sich die Brandbreite auf 5–10 MBit/s erhöht hatte. Daher empfiehlt Adobe, dass alle Benutzer, die gleichzeitig auf das System zugreifen, mindestens über eine Uploadgeschwindigkeit von 10 MBit/s und eine Bandbreite von 5–10 MBit/s verfügen sollten.

Weitere Informationen finden Sie unter [Fehlerbehebung AEM Desktop-App](https://helpx.adobe.com/de/experience-manager/kb/troubleshooting-companion-app.html).

## Beschränkungen {#limitations}

Beim Dimensionieren einer Implementierung ist es wichtig, Systembeschränkungen zu bedenken. Wenn die vorgeschlagene Implementierung über diese Beschränkungen hinausgeht, setzen Sie auf kreative Strategien wie die Partitionierung von Assets über mehrere Assets-Implementierungen hinweg.

Die Dateigröße ist nicht der einzige Faktor, der bei OOM-Problemen (Out of Memory, nicht genügend Arbeitsspeicher) eine Rolle spielt. Es kommt auch auf die Bildabmessungen an. Sie können OOM-Probleme durch eine höhere Heap-Größe beim Starten von AEM vermeiden.

Darüber hinaus können Sie die Eigenschaft &quot;Schwellenwert&quot;der Komponente `com.day.cq.dam.commons.handler.StandardImageHandler` in Configuration Manager bearbeiten, um eine temporäre Zwischendatei größer als null zu verwenden.

## Maximale Anzahl von Assets {#maximum-number-of-assets}

<!-- Currently, Adobe has not tested the system for loading greater than 8 million assets. There are limitations both on the number of documents that can exist in an Oak repository and the number of files that can exist in a datastore.

While the limit for the number of nodes in a repository has not been determined, assuming each asset generates roughly 30 nodes, putting the 8 million asset test at 240 million nodes from the assets alone. This does not include audit logs, archived workflows, or versions. -->

Die maximale Anzahl von Dateien in einem Datenspeicher kann sich aufgrund von Dateisystembeschränkungen auf 2,1 Milliarden belaufen. Wahrscheinlich trifft das Repository aufgrund der großen Anzahl von Knoten auf Probleme, lange bevor der Datenspeicher an seine Grenzen stößt.

Wurden die Wiedergaben nicht korrekt generiert, verwenden Sie die Camera Raw-Bibliothek. In diesem Fall sollte jedoch die längste Bildseite nicht größer sein als 65.000 Pixel. Darüber hinaus sollte das Bild maximal 512 MP (512 &amp;ast; 1024 &amp;ast; 1024 Pixel)&quot;. *Die Größe des Assets ist unerheblich*.

Die bei einem bestimmten Heap standardmäßig unterstützte TIFF-Dateigröße für AEM lässt sich nur schwer abschätzen, weil die Verarbeitung durch zusätzliche Faktoren wie die Pixelgröße beeinflusst wird. Es ist möglich, dass AEM eine 255 MB große Datei standardmäßig verarbeiten kann, aber eine 18 MB große Datei nicht, weil sich letztere gegenüber der ersteren eine ungewöhnlich hohe Anzahl an Pixel aufweist.

## Größe der Assets  {#size-of-assets}

Standardmäßig können Sie AEM Assets mit einer Dateigröße von bis zu 2 GB hochladen. Informationen zum Hochladen sehr großer Assets in AEM finden Sie unter [Konfiguration zum Hochladen sehr großer Assets](managing-video-assets.md#configuration-to-upload-video-assets-that-are-larger-than-gb).
