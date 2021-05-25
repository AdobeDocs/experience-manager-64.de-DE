---
title: Best Practices zum Verwalten von Assets mithilfe von AEM
description: Ermitteln und halten Sie die Best Practices ein, die die Systemstabilität und -leistung unter Last verbessern, je nach AEM Assets-Bereitstellung und Funktionen zur Erfassung und Verarbeitung von Assets.
contentOwner: AG
feature: Asset-Verwaltung
role: Architect,Administrator
exl-id: e2ab924b-53cb-4011-8c0a-9e8e59dd2f16
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '653'
ht-degree: 51%

---

# Best Practices für AEM Assets {#best-practices-for-assets}

Adobe Experience Manager (AEM) Assets ist wichtig für die Bereitstellung von erstklassigen digitalen Marketingerlebnissen, die durch Erhöhung der Inhaltsgeschwindigkeit zum Erreichen von Geschäftszielen beitragen. Wenn Sie mit einer großen Zahl von Assets innerhalb von AEM arbeiten oder regelmäßig zahlreiche Assets wie etwa Videos und dynamische Medien hochladen, ist die Optimierung Ihres Digital Asset Management-Erlebnisses von großer Wichtigkeit für die Systemeffizienz.

Je nachdem, wie Sie AEM Assets für Ihr Unternehmen positioniert haben und welche Funktionen Sie für die Asset-Erfassung, Ausgabegenerierung und Metadatenextraktion verwenden, erhöht die Erkennung und Befolgung von Best Practices in verschiedenen Bereichen deutlich die Systemstabilität und Belastbarkeit.

Nachdem Sie die folgenden Handbücher gelesen haben, verfügen Sie über das Wissen und die Werkzeuge für die Entwicklung und Verwaltung eines Enterprise Asset Management-Systems, das Ihre Anforderungen erfüllt.

* [Handbuch zur ](performance-tuning-guidelines.md)
Leistungsoptimierung von AssetsEnthält eine Reihe von Best Practices, die an jedem Punkt in Ihrer Implementierung auch nach der Live-Schaltung befolgt werden können, um sicherzustellen, dass Sie Ihr System optimal nutzen.
* [Handbuch zur Asset-Größenanpassung ](assets-sizing-guide.md)
Bei der Erstellung von Schätzungen für eine Assets-Implementierung ist es wichtig sicherzustellen, dass ausreichend Ressourcen zur Verfügung stehen, was Asset-Speicher, CPU, Speicher, I/O- und Netzwerkdurchsatz betrifft. Damit diese Elemente dimensioniert werden können, müssen Sie wissen, wie viele Elemente in das System geladen werden. Dieses Handbuch enthält Best Practices, mithilfe derer effiziente Metriken für die Schätzung von Infrastruktur und Ressourcen ermittelt werden können, die für die Bereitstellung von AEM Assets sowie eines Dimensionierungs-Tools erforderlich sind.
* [Handbuch ](assets-migration-guide.md)
zur Migration von AssetsWenn Sie Assets aus Ihrem alten System in AEM Assets migrieren möchten, müssen Sie den Migrationsprozess mit verschiedenen Schritten optimieren. Das Migrationshandbuch enthält Best Practices für die Aufgaben, die Sie durchführen müssen, um die Assets in mehreren Phasen in AEM zu laden. Dazu gehören das Anwenden von Metadaten, das Generieren von Ausgabedarstellungen und das Aktivieren der Assets für die Veröffentlichungsbereitstellung.
* [Überlegungen zum Assets-Netzwerk ](assets-network-considerations.md)
Bei der Handhabung AEM Bereitstellung ist ein Verständnis der Netzwerktopologie wichtig, um die Netzwerkleistung zu verstehen, Engpässe zu identifizieren und das erwartete Benutzererlebnis zu beschreiben. Das Dokument über Netzwerkaspekte in Verbindung mit Assets enthält Überlegungen zum Netzwerk bezüglich der Entwicklung für die AEM Assets-Bereitstellung.
* [](assets-monitoring-best-practices.md)
Handbuch zur Überwachung von AssetsNach der Bereitstellung Ihrer AEM sollten Sie bestimmte Aufgaben und das System im Allgemeinen überwachen, um die Systemintegrität und Effizienz der Vorgänge sicherzustellen. Die Anleitung zur Überwachung umfasst Best Practices zur Überwachung verschiedener Aspekte Ihres Systems.
* (Veraltet) [Handbuch zur Asset-Abladung](assets-offloading-best-practices.md)
Die Verarbeitung großer Dateien und die Ausführung von Workflows in AEM Assets können erhebliche CPU-, Speicher- und I/O-Ressourcen erfordern. Das Abladen dieser Aufgaben kann CPU-, Speicher- und I/O-Fixkosten verringern. Die Anleitung zur Abladung in Assets enthält empfohlene Einsatzmöglichkeiten und Best Practices für die Abladung in Assets.
* [AEM Best ](https://helpx.adobe.com/de/experience-manager/desktop-app/aem-desktop-app-best-practices.html)
Practices für das Desktop-ProgrammDas AEM-Desktop-Programm verbindet Ihre Digital Asset Management (DAM)-Lösung mit Ihrem Desktop, damit Sie die in der AEM Web-Benutzeroberfläche verfügbaren Dateien direkt auf dem Desktop öffnen können. Der unkomplizierte Workflow der AEM Desktop App wird anhand auf Desktop-Betriebssystemen gängigen Technologien zur Netzwerkfreigabe ermöglicht. In diesem Leitfaden werden die zentralen Funktionen und empfohlenen Anwendungsgebiete des AEM-Desktop-Programms erläutert.
* [Best ](aem-cc-integration-best-practices.md)
Practices für die Integration von AEM und Creative CloudenSie können Ihre AEM-Implementierung auf verschiedene Arten mit Creative Cloud integrieren. Das Einhalten einiger Best Practices für die Optimierung Ihrer Workflows zur Integration und Asset-Übertragung trägt zum Erzielen der maximalen Effizienz bei. Das vorliegende Handbuch enthält Best Practices für die Integration von AEM Assets mit Adobe Creative Cloud.
* (Veraltet) [Best Practices für die Ordnerfreigabe AEM Creative Cloud-Ordner](aem-cc-folder-sharing-best-practices.md)
Sie können AEM so konfigurieren, dass Benutzer in DAM Ordner für Creative Cloud-Benutzer (CC) freigeben können, damit sie als freigegebene Ordner im Creative Cloud Assets-Dienst verfügbar sind. Die Funktion kann verwendet werden, um Dateien zwischen Kreativteams und DAM-Benutzern auszutauschen. Dieses Handbuch enthält Best Practices, um die Freigabe von Ordnern aus AEM in Creative Cloud wirksam einzusetzen.
