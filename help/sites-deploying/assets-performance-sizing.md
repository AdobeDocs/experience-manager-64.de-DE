---
title: Handbuch zur Leistung von Assets
seo-title: Assets Performance Guide
description: Erfahren Sie, wie Sie die optimale Hardwaredimensionierung für ein neues Digital Asset Management (DAM)-Setup ermitteln und wie Sie Leistungsprobleme beheben können.
seo-description: Learn how to determine the optimal hardware sizing for a new Digital Asset Management (DAM) setup and how to troubleshoot performance issues
uuid: 8291c5b9-c543-41cf-8754-445826200930
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: configuring
discoiquuid: a79839e2-be39-418b-a3bd-f5457e555172
exl-id: 2c455a20-a2b9-4a80-8577-f1a1713710d6
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1258'
ht-degree: 36%

---

# Handbuch zur Leistung von Assets{#assets-performance-guide}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Digital Asset Management wird häufig dort angewendet, wo es auf Leistung ankommt. Das typische DAM-Setup enthält jedoch eine Reihe von Hardware- und Software-Komponenten, die sich auf die Leistung auswirken können. Dieses Dokument enthält Folgendes:

* Informationen für Systemadministratoren zur Bestimmung der optimalen Hardwaregröße für ein neues Digital Asset Management-Setup
* Informationen für Software-Entwickler, die zur Fehlerbehebung bei DAM-Instanzen mit Leistungsproblemen beitragen möchten

## Leistungsprobleme {#performance-issues}

Eine ungenügende Leistung im Digital Asset Management kann sich auf drei Arten auf das Benutzererlebnis auswirken: interaktive Leistung, Asset-Verarbeitung und Download-Geschwindigkeit. Um die Leistung zu verbessern, ist es wichtig, die beobachtete Leistung richtig zu messen und Zielmetriken zu erstellen.

**1. Interaktive Suche und interaktives Durchsuchen** Wenn Benutzer etwa nach Assets suchen oder den DAM Finder durchsuchen und dann langsame Antwortzeiten oder eine verzögerte Anzeige von Suchergebnissen beklagen, Dies ist ein interaktives Leistungsproblem.

Die interaktive Leistung wird anhand der Seitenreaktionszeit gemessen. Dies ist die Zeit, die vom Empfang der HTTP-Anfrage bis zum Schließen der HTTP-Antwort benötigt wird. Diese kann aus den Protokolldateien der Anfrage bestimmt werden. Die typische Zielleistung ist eine Seitenreaktionszeit von weniger als zwei Sekunden.

**2. Asset-Verarbeitung** Ein Problem mit der Asset-Verarbeitung liegt vor, wenn beim es beim Hochladen von Assets mehrere Minuten dauert, bis die Assets fertig konvertiert sind und in AEM DAM übernommen werden.

Die Leistung der Asset-Verarbeitung wird anhand der durchschnittlichen Fertigstellungszeit des Workflow-Prozesses gemessen. Dies ist die Zeit, die vom Aufrufen des Workflow-Prozesses zur Asset-Aktualisierung bis zu seinem Abschluss benötigt wird. Diese kann über die Benutzeroberfläche der Workflow-Berichte bestimmt werden. Die typische Sollleistung ist abhängig von Größe und Typ der verarbeiteten Assets sowie von der Anzahl der Ausgabedarstellungen. Mögliche Beispiele für Sollleistungen:

* unter zehn Sekunden für Bilder, die kleiner als 1280x1280 Pixel sind und Standardausgabeformate verwenden
* unter einer Minute für Bilder, die kleiner als 100 MB sind und Standardausgabeformate verwenden
* weniger als fünf Minuten für HD-Videoclips, die weniger als eine Minute betragen

**3. Download-Geschwindigkeiten** Ein Durchsatzproblem liegt vor, wenn ein Download von AEM DAM längere Zeit dauert und Miniaturansichten beim Browsen in DAM Admin oder DAM Finder nicht sofort angezeigt werden.

Die Durchsatzleistung wird anhand der Download-Rate in Kilobit pro Sekunde gemessen. Die typische Zielleistung beträgt 300 Kilobits pro Sekunde für 100 gleichzeitige Downloads.

**4. Faktoren, die die Leistung der Asset-Verarbeitung beeinflussen**

Um schätzen zu können, welche Hardware Sie zur Verarbeitung von Assets benötigen, müssen die folgenden Aspekte berücksichtigt werden:

* Die Auflösung der Bilder in Pixel
* Der AEM Prozess zugewiesene Heap

Die Anzahl der Pixel im Bild bestimmt die Verarbeitungszeit – je höher die Pixelzahl, desto länger dauert die Verarbeitung.\
Der Bildtyp, die Komprimierungsrate oder die entsprechende Dateigröße beim Speichern des Bildes wirken sich nicht wesentlich auf die Gesamtleistung aus.

Heap wurde als der wichtigste Begrenzungsfaktor identifiziert. Sobald das Asset den verfügbaren freien Speicher überschreitet, nimmt die Verarbeitungsleistung rapide ab.

Im Falle großer Mengen können DAM-Prozesse sehr gut parallel durchgeführt werden. Stapelweises Hochladen von Assets und Multicore-Prozessoren senken den absoluten Zeitaufwand pro Asset erheblich.

**5. Schätzen der Hardwareanforderungen für die Asset-Verarbeitung**

Eine umfassende Verarbeitung digitaler Assets erfordert optimierte Hardware-Ressourcen. Die wichtigsten Faktoren sind die Bildgröße und der maximale Durchsatz verarbeiteter Bilder.

Weisen Sie mindestens 16 GB Heap zu und konfigurieren Sie den Workflow DAM-Update-Asset so, dass Rohbilder mit dem [Camera Raw-Paket](/help/assets/camera-raw.md) aufgenommen werden.

## Grundlegendes zum System {#understanding-the-system}

Ein typisches DAM-Setup besteht aus Endbenutzern, die über einen Lastenausgleich auf DAM zugreifen. Die DAM-Instanz kann Teil eines Clustersetup sein, bei dem jede DAM-Instanz in einem Java Virtual Machine-Prozess auf einem physischen Computer oder einer virtuellen Maschine ausgeführt wird. Der DAM-Speicher wird entweder von einem RAID-Datenträger bei Einzelcomputer-Setups oder von einem verwalteten Netzwerk-angehängten Speicher bei Clustereinstellungen bereitgestellt.

In der folgenden Legende werden die möglichen Leistungseinbußen bei einigen Lösungen beschrieben.

**Netzwerkverbindung zum Endbenutzer** Eine langsame Netzwerkverbindung kann Durchsatzprobleme verursachen, in seltenen Fällen auch Latenzprobleme. Manchmal hat der Benutzer eine langsame Verbindung vom ISP, insbesondere in Intranets. Dies ist ein Zeichen für eine falsche Netzwerktopologie.

**Temporäres Dateisystem** Ein langsames lokales Dateisystem kann zu Problemen mit der interaktiven Leistung führen. Dies gilt insbesondere für Suchvorgänge, da Suchindizes auf der lokalen Festplatte gespeichert werden. Darüber hinaus können Probleme bei der Asset-Verarbeitung auftreten, sofern der Befehlszeilenprozess verwendet wird.

**AEM-DAM Produktsuche** Probleme mit der interaktiven Leistung, die häufig bei Suchvorgängen auftreten, sind auf eine hohe CPU-Auslastung aufgrund einer zu großen Anzahl gleichzeitiger Benutzender oder andere CPU-intensive Prozesse in derselben Instanz zurückzuführen. Die Umstellung von virtuellen Maschinen auf dedizierte Maschinen und die Sicherstellung, dass keine anderen Dienste auf dem Computer ausgeführt werden, kann dazu beitragen, die Leistung zu verbessern. Wenn aufgrund der Asset-Verarbeitung und vieler gleichzeitiger Benutzer eine hohe CPU-Last verursacht wird, empfiehlt Day das Hinzufügen zusätzlicher Clusterknoten.

**AEM-DAM Workflow** Lang laufende Workflow-Prozesse während der Asset-Aufnahme führen zu Leistungsproblemen bei der Asset-Verarbeitung. Je nach Typ der verarbeiteten Assets kann dies auf eine Überauslastung der CPU hinweisen. Day empfiehlt, dass Sie die Anzahl der anderen Prozesse reduzieren, die auf dem System ausgeführt werden, und die Anzahl der verfügbaren CPUs erhöhen, indem Sie Clusterknoten hinzufügen.

**NAS Connectivity** Eine unzureichende Netzwerkkonnektivität zum NAS verursacht Probleme mit der interaktiven Leistung, weil der Zugriff auf neue Knoten während der Asset-Verarbeitung aufgrund der Netzwerklatenz verlangsamt wird. Darüber hinaus wirkt sich der langsame Netzwerkdurchsatz negativ auf den Durchsatz, aber auch auf die Leistung der Asset-Verarbeitung aus, da das Laden und Speichern von Ausgabedarstellungen verlangsamt wird.

Gründe für schlechte Latenz und Durchsatz in einem NAS sind normalerweise Netzwerktopologie oder NAS-Überauslastung durch andere Dienste.

**Network Attached Storage (NAS)** Überbeanspruchte NAS-Systeme können zu einer Vielzahl von Problemen führen:

* Geringer Festplattenspeicher ist ein häufig auftretendes Problem, das durch eine ordnungsgemäße Dimensionierung von DAM-Projekten verhindert werden kann.
* Eine hohe Festplattenlatenz führt zu langsamen Zugriffszeiten für CRX und kann Probleme mit der interaktiven Leistung verursachen.
* Ein geringer Datenträgerdurchsatz kann Leistungseinbußen für CQ5 DAM zur Folge haben.

## Leistungstests {#testing-for-performance}

Stellen Sie für jedes DAM-Projekt sicher, dass Sie ein Leistungstestsystem einrichten, das Engpässe schnell erkennen und beheben kann. Beachten Sie dazu die folgenden Checkpoints:

1. End-to-End-Leistungstests mit JMeter - Simulieren Sie eine Beispiel-Such- und Durchsuchsitzung, um interaktive Leistungsprobleme zu erkennen.
1. Durchsatz- und Latenztests mit JMeter - Die Ausführung auf einem Client-Computer stellt sicher, dass es keine topologiebezogenen Probleme gibt.
1. Standardisierte Asset-Verarbeitungstests : Erfassen Sie eine kleine Anzahl von Beispiel-Assets und messen Sie die Zeit. Dies sollte die Integration externer Workflows beinhalten.
1. Überwachen Sie die CPU-, Datenträger- und Speicherauslastung jedes Clusterknotens.
1. CRX-Diagnose für Lese-/Schreibleistung, um nicht mit der Verarbeitung zusammenhängende Probleme zu identifizieren.
1. Überwachen Sie die Netzwerklatenz und den Durchsatz vom DAM-Cluster zu Ihrem NAS.
1. Testen Sie nach Möglichkeit die Lese- und Schreibleistung sowie die Festplattenlatenz direkt auf dem NAS.

## Beheben von Engpässen {#tweaking-bottlenecks}

Die folgenden Leistungsverbesserungen wurden bisher in Projekten verwendet:

* Selektive Ausgabegenerierung: Generieren Sie nur die Ausgabedarstellungen, die Sie benötigen, indem Sie Bedingungen zum Asset-Verarbeitungs-Workflow hinzufügen, sodass kostspieligere Ausgabedarstellungen nur für ausgewählte Assets generiert werden.
* Freigegebener Datenspeicher zwischen Instanzen: Wenn wenig Speicherplatz auf der Festplatte zur Verfügung steht, kann dies die benötigte Festplattenspeicherkapazität erheblich reduzieren, was höhere Konfigurationsaufwand und den Verlust der automatischen Bereinigung des Datenspeichers verursacht.

## Weiterführende Literatur {#further-reading}

* [Analysieren von langsamen und blockierten Prozessen](https://helpx.adobe.com/de/experience-manager/kb/AnalyzeSlowAndBlockedProcesses.html)
