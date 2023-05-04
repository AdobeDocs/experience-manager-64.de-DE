---
title: Handbuch zur Assets-Dimensionierung
description: Best Practices zur Bestimmung effizienter Metriken zur Schätzung der für die Bereitstellung erforderlichen Infrastruktur und Ressourcen [!DNL Experience Manager] Assets.
uuid: f847c07d-2a38-427a-9c38-8cdca3a1210c
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 82c1725e-a092-42e2-a43b-72f2af3a8e04
feature: Asset Management
role: Architect,Admin
exl-id: 6115e5e8-9cf5-417c-91b3-0c0c9c278b5b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1876'
ht-degree: 29%

---

# Handbuch zur Assets-Dimensionierung {#assets-sizing-guide}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Bei der Dimensionierung der Umgebung für eine Adobe Experience Manager Assets-Implementierung ist es wichtig sicherzustellen, dass ausreichend Ressourcen zur Verfügung stehen, d. h. Festplatten-, CPU-, Speicher-, I/O- und Netzwerkdurchsatz. Die Größe vieler dieser Ressourcen erfordert ein Verständnis davon, wie viele Assets in das System geladen werden. Wenn keine bessere Metrik verfügbar ist, können Sie die Größe der vorhandenen Bibliothek durch das Alter der Bibliothek dividieren, um die Rate zu ermitteln, mit der Assets erstellt werden.

## Festplatte {#disk}

### DataStore {#datastore}

Ein häufiger Fehler bei der Dimensionierung des erforderlichen Festplattenspeichers für eine Assets-Implementierung besteht darin, die Berechnungen auf der Größe der Rohbilder zu basieren, die in das System aufgenommen werden sollen. Standardmäßig [!DNL Experience Manager] erstellt drei Ausgabeformate zusätzlich zum Originalbild zur Verwendung beim Rendern der [!DNL Experience Manager] Benutzeroberflächen-Elemente. In früheren Implementierungen wurde festgestellt, dass diese Ausgabedarstellungen die doppelte Größe der aufgenommenen Assets annehmen.

Die meisten Benutzer definieren benutzerdefinierte Ausgabeformate zusätzlich zu den vordefinierten Ausgabeformaten. Zusätzlich zu den Ausgabeformaten können Sie mit Assets Unter-Assets aus gängigen Dateitypen wie InDesign und Illustrator extrahieren.

Schließlich speichern AEM Versionierungsfunktionen Duplikate der Assets im Versionsverlauf. Sie können die Versionen so konfigurieren, dass Bereinigungen häufig durchgeführt werden. Viele Benutzer entscheiden sich jedoch dafür, die Versionen lange im System zu behalten, was zusätzlichen Speicherplatz beansprucht.

In Anbetracht dieser Faktoren benötigen Sie eine Methode zur Berechnung eines akzeptabel präzisen Speicherplatzes zum Speichern von Benutzer-Assets.

1. Bestimmen Sie die Größe und Anzahl der Assets, die in das System geladen werden.
1. Rufen Sie ein repräsentatives Beispiel der Assets ab, die in AEM hochgeladen werden sollen. Wenn Sie beispielsweise PSD-, JPG-, AI- und PDF-Dateien in das System laden möchten, benötigen Sie mehrere Beispielbilder für jedes Dateiformat. Darüber hinaus sollten diese Muster für die verschiedenen Dateigrößen und Komplexität von Bildern repräsentativ sein.
1. Definieren Sie die zu verwendenden Ausgabedarstellungen.
1. Erstellen Sie die Ausgabedarstellungen in [!DNL Experience Manager] mit ImageMagick oder den Creative Cloud-Applikationen der Adobe. Erstellen Sie neben den von den Benutzern angegebenen Ausgabedarstellungen sofort einsetzbare Standard-Ausgabedarstellungen. Für Benutzer, die Dynamic Media Classic implementieren, können Sie die IC-Binärdatei verwenden, um die PTIFF-Ausgabeformate zu generieren, die in AEM gespeichert werden sollen.
1. Wenn Sie die Verwendung von Unter-Assets beabsichtigen, generieren Sie diese für die entsprechenden Dateitypen. Informationen zum Generieren von Unter-Asset-Seiten aus InDesign-Dateien oder PNG/PDF-Dateien aus Illustrator-Ebenen finden Sie in der Online-Dokumentation .
1. Vergleichen Sie die Größe der Ausgabebilder, Ausgabedarstellungen und Unter-Assets mit den Originalbildern. So können Sie den erwarteten Wachstumsfaktor beim Laden des Systems generieren. Wenn Sie z. B. Ausgabedarstellungen und Unter-Assets mit einer kombinierten Größe von 3 GB nach der Verarbeitung von 1 GB an Assets erzeugen, lautet der Ausgabedarstellungs-Wachstumsfaktor 3.
1. Legen Sie die maximale Zeit fest, für die Asset-Versionen im System gepflegt werden sollen.
1. Bestimmen Sie, wie oft vorhandene Assets im System geändert werden. Wenn [!DNL Experience Manager] als Collaboration-Hub in kreativen Workflows dient, gibt es viele Änderungen. Wenn nur fertige Assets in das System hochgeladen werden, ist diese Zahl viel niedriger.
1. Bestimmen Sie, wie viele Assets jeden Monat in das System geladen werden. Wenn Sie sich nicht sicher sind, ermitteln Sie die Anzahl der derzeit verfügbaren Assets und teilen Sie die Zahl durch das Alter des ältesten Assets, um eine ungefähre Zahl zu berechnen.

Die Durchführung der Schritte 1 bis 9 hilft Ihnen bei der Ermittlung folgender Punkte:

* Rohgröße der zu ladenden Assets
* Anzahl der zu ladenden Assets
* Ausgabedarstellungs-Wachstumsfaktor
* Anzahl der Asset-Änderungen pro Monat
* Anzahl der Monate für die Aufbewahrung von Asset-Versionen
* Anzahl der neu geladenen Assets pro Monat
* Wachstumsjahre, für die Speicherplatz reserviert werden soll

Sie können diese Zahlen in der Tabelle zur Netzwerkdimensionierung angeben, um den Gesamtspeicherbedarf für den Datenspeicher zu ermitteln. Zudem lässt sich so nützlicherweise feststellen, wie sich die Aufbewahrung von Asset-Versionen oder die Änderung von Assets in [!DNL Experience Manager] auf das Festplattenwachstum auswirkt.

Die in das Tool aufgefüllten Beispieldaten zeigen, wie wichtig die Ausführung der genannten Schritte ist. Wenn Sie den Datenspeicher allein basierend auf dem Ladevorgang der Rohbilder (1 TB) bemessen, ist eine Unterbewertung der Repository-Größe um den Faktor 15 möglich.

[Datei abrufen](assets/disk_sizing_tool.xlsx)

### Freigegebene Datenspeicher {#shared-datastores}

Für große Datenspeicher können Sie einen freigegebenen Datenspeicher implementieren, und zwar entweder über einen gemeinsam genutzten Dateidatenspeicher auf einem Netzlaufwerk oder über einen S3-Datenspeicher. In diesem Fall müssen einzelne Instanzen keine Kopie der Binärdateien aufbewahren. Darüber hinaus erleichtert ein freigegebener Datenspeicher die Binärdatei-lose Replikation und reduziert die Bandbreite, die zum Replizieren von Assets in Veröffentlichungsumgebungen oder Abladeinstanzen verwendet wird.

#### Anwendungsfälle {#use-cases}

Der Datenspeicher kann gemeinsam von primärer und Standby-Autoreninstanz genutzt werden, um den zeitlichen Aufwand zum Aktualisieren der Standby-Instanz mit Änderungen der primären Instanz zu minimieren. Adobe empfiehlt die Freigabe des Datenspeichers zwischen einer primären Autoreninstanz und Offload-Autoreninstanzen, um den Overhead bei der Workflow-Abladung zu reduzieren. Sie können den Datenspeicher auch zwischen der Autoren- und der Veröffentlichungsinstanz freigeben, um den Traffic während der Replikation zu minimieren.

#### Nachteile {#drawbacks}

Aufgrund einiger Fallstricke wird die Freigabe eines Datenspeichers nicht in allen Fällen empfohlen.

#### Single Point of Failure {#single-point-of-failure}

Ein freigegebener Datenspeicher führt einen einzelnen Fehlerpunkt in einer Infrastruktur ein. Stellen Sie sich ein Szenario vor, in dem Ihr System über eine Autoren- und zwei Veröffentlichungsinstanzen mit jeweils einem eigenen Datenspeicher verfügt. Wenn einer von ihnen abstürzt, können die beiden anderen weiterhin ausgeführt werden. Wenn der Datenspeicher jedoch freigegeben wird, kann ein einzelner Datenträgerfehler die gesamte Infrastruktur beeinträchtigen. Stellen Sie daher sicher, dass Sie eine Sicherung des freigegebenen Datenspeichers aufbewahren, aus dem Sie den Datenspeicher schnell wiederherstellen können.

Die Bereitstellung des AWS S3-Diensts für freigegebene Datenspeicher wird bevorzugt, da dadurch die Wahrscheinlichkeit eines Fehlschlagens im Vergleich zu normalen Festplattenarchitekturen erheblich verringert wird.

#### Erhöhte Komplexität {#increased-complexity}

Freigegebene Datenspeicher erhöhen auch die Komplexität von Vorgängen, wie z. B. der Speicherbereinigung. Normalerweise kann die Speicherbereinigung für einen eigenständigen Datenspeicher mit einem Klick initiiert werden. Freigegebene Datenspeicher erfordern jedoch zusätzlich zur Ausführung der tatsächlichen Sammlung auf einem einzelnen Knoten auch die Aktion zum Durchsuchen von Markierungen für jedes Element, das den Datenspeicher verwendet.

Im AWS-Betrieb können, wenn statt eines RAID-Arrays mit EBS-Volumes ein zentraler Speicherort (über S3) implementiert wird, die Komplexität und die Betriebsrisiken auf dem System deutlich kompensiert werden.

#### Leistungsaspekte {#performance-concerns}

Bei einem freigegebenen Datenspeicher müssen die Binärdateien auf einem Laufwerk gespeichert werden, das an ein Netzwerk angebunden und für alle Instanzen freigegeben ist. Da der Zugriff auf diese Binärdateien über ein Netzwerk erfolgt, wird die Systemleistung beeinträchtigt. Eine schnelle Netzwerkverbindung zu einem schnellen Festplattenarray kann diesen Effekt teilweise auffangen. Dies ist jedoch eine teure Angelegenheit. Im Falle von AWS-Vorgängen liegen alle Festplatten remote vor, sodass eine Netzwerkanbindung erforderlich ist. Bei temporären Volumes gehen Daten verloren, wenn die Instanz gestartet oder angehalten wird.

#### Latenz {#latency}

Die Latenz in S3-Implementierungen wird durch die Schreibthreads im Hintergrund eingeführt. Sicherungsverfahren müssen diese Latenz und alle Abladevorgänge berücksichtigen. Das S3-Asset ist in S3 möglicherweise nicht vorhanden, wenn ein Abladeauftrag gestartet wird. Darüber hinaus können Lucene-Indizes beim Erstellen einer Sicherung unvollständig bleiben. Dies gilt für alle zeitkritischen Dateien, die in den S3-Datenspeicher geschrieben und von einer anderen Instanz aus aufgerufen werden.

### Knotenspeicher/Dokumentenspeicher {#node-store-document-store}

Aufgrund der Ressourcen, die von den folgenden Benutzern benötigt werden, ist es schwierig, präzise Größenangaben für einen NodeStore oder DocumentStore zu erhalten:

* Asset-Metadaten
* Asset-Versionen
* Auditprotokolle
* Archivierte und aktive Workflows

Da die Binärdateien im Datenspeicher gespeichert werden, belegt jede Binärdatei etwas Platz. Die meisten Repositorys sind kleiner als 100 GB. Es kann jedoch größere Repositorys mit einer Größe von bis zu 1 TB geben. Um eine Offline-Komprimierung durchzuführen, benötigen Sie ausreichend freien Speicherplatz auf dem Volume, um das komprimierte Repository neben der vorab komprimierten Version neu zu schreiben. Eine geeignete Faustregel: Dimensionieren Sie die Festplatte so, dass sie 1,5-mal so groß ist wie die erwartete Repository-Größe.

Setzen Sie für das Repository SSDs oder Festplatten mit einem IOPS-Level von mehr als 3000 ein. Damit im Zuge der IOPS keine Leistungsengpässe entstehen, überwachen Sie die CPU-I/O-Wartelevel auf frühe Problemanzeichen.

[Datei laden](assets/aem_environment_sizingtool.xlsx)

## Netzwerk {#network}

Für [!DNL Assets] gibt es eine Reihe von Anwendungsbeispielen, in denen die Netzwerkleistung eine größere Bedeutung hat als bei vielen anderen unserer [!DNL Experience Manager]-Projekte. Eine Kundin oder ein Kunde kann zwar über einen schnellen Server verfügen, aber wenn die Netzwerkverbindung nicht für die Auslastung durch die Benutzenden ausreicht, die Assets hochladen und aus dem System herunterladen, scheint der Server nach wie vor langsam zu sein. Es gibt eine gute Methode, um den Schokoladpunkt in der Netzverbindung eines Benutzers zu [!DNL Experience Manager] at [[!DNL Experience Manager]  Asset-Überlegungen für Benutzererlebnisse, Instanzgröße, Workflow-Auswertung und Netzwerktopologie](assets-network-considerations.md).

## WebDAV {#webdav}

Wenn Sie die [!DNL Experience Manager] -Desktop-Programm verwenden, werden Netzwerkprobleme aufgrund von Ineffizienzen im WebDAV-Protokoll schwieriger.

Um diese Ineffizienzen zu veranschaulichen, testete Adobe die Systemleistung mit WebDAV unter OS X. Eine InDesign-Datei mit 3,5 MB wurde geöffnet, bearbeitet und die Änderungen wurden gespeichert. Folgende Bemerkungen wurden gemacht:

* Insgesamt wurden rund 100 HTTP-Anfragen generiert, um den Vorgang abzuschließen.
* Die Datei wurde viermal über HTTP hochgeladen
* Die Datei wurde einmal über HTTP heruntergeladen
* Der gesamte Vorgang dauerte 42 Sekunden
* Insgesamt wurden 18 MB Daten übertragen

Bei der Analyse der durchschnittlichen Speicherzeit für Dateien über WebDAV wurde festgestellt, dass die Leistung drastisch zunimmt, da die Bandbreite bis zum Niveau von 5-10 MBit/s zunimmt. Daher empfiehlt Adobe, dass jeder Benutzer, der gleichzeitig auf das System zugreift, mindestens eine Upload-Geschwindigkeit von 10 MBit/s und eine Bandbreite von 5 bis 10 MBit/s aufweist.

Weitere Informationen finden Sie unter [Fehlerbehebung [!DNL Experience Manager] Desktop-Programm](https://helpx.adobe.com/experience-manager/kb/troubleshooting-companion-app.html).

## Beschränkungen {#limitations}

Bei der Größenanpassung einer Implementierung müssen die Systembeschränkungen beachtet werden. Wenn die vorgeschlagene Implementierung diese Einschränkungen überschreitet, wenden Sie kreative Strategien an, z. B. das Partitionieren der Assets über mehrere Assets-Implementierungen hinweg.

Die Dateigröße ist nicht der einzige Faktor, der zu OOM-Problemen (Out of Memory) beiträgt. Es hängt auch von den Abmessungen des Bildes ab. Sie können OOM-Probleme vermeiden, indem Sie beim Start der AEM eine höhere Heap-Größe festlegen.

Außerdem können Sie die Eigenschaft für die Schwellenwertgröße der `com.day.cq.dam.commons.handler.StandardImageHandler`-Komponente in Configuration Manager so bearbeiten, dass eine temporäre Zwischendatei größer als null verwendet wird.

## Maximale Anzahl von Assets {#maximum-number-of-assets}

<!-- Currently, Adobe has not tested the system for loading greater than 8 million assets. There are limitations both on the number of documents that can exist in an Oak repository and the number of files that can exist in a datastore.

While the limit for the number of nodes in a repository has not been determined, assuming each asset generates roughly 30 nodes, putting the 8 million asset test at 240 million nodes from the assets alone. This does not include audit logs, archived workflows, or versions. -->

Die Anzahl der Dateien, die in einem Datenspeicher vorhanden sein können, kann aufgrund von Dateisystembeschränkungen auf 2,1 Milliarden begrenzt sein. Es ist wahrscheinlich, dass das Repository aufgrund einer großen Anzahl von Knoten Probleme hat, lange bevor das Datenspeicherlimit erreicht wurde.

Wenn die Ausgabedarstellungen falsch generiert werden, verwenden Sie die Camera Raw Bibliothek. In diesem Fall sollte die längste Seite des Bildes jedoch nicht größer als 65.000 Pixel sein. Außerdem sollte das Bild nicht mehr als 512 MP (512 &amp;ast) enthalten. 1024 &amp;ast; 1024 Pixel)&quot;. *Die Größe des Assets ist unerheblich*.

Es ist schwierig, die Größe der standardmäßig unterstützten TIFF-Datei (OOTB) mit einem bestimmten Heap für [!DNL Experience Manager] weil zusätzliche Faktoren wie die Pixelgröße die Verarbeitung beeinflussen. Es ist möglich, dass [!DNL Experience Manager] kann eine Datei mit einer Größe von 255 MB OOTB verarbeiten, kann jedoch keine Dateigröße von 18 MB verarbeiten, da letztere eine ungewöhnlich höhere Anzahl von Pixeln im Vergleich zu ersteren aufweist.

## Größe von Assets {#size-of-assets}

Standardmäßig [!DNL Experience Manager] ermöglicht das Hochladen von Assets mit Dateigrößen von bis zu 2 GBs. Informationen zum Hochladen sehr großer Assets in AEM finden Sie unter [Konfiguration zum Hochladen sehr großer Assets](managing-video-assets.md#configuration-to-upload-video-assets-that-are-larger-than-gb).
