---
title: Best Practices zur Verwaltung von Assets mit AEM
description: Identifizieren Sie die Best Practices, die die Systemstabilität und Leistung bei Belastung verbessern, und halten Sie diese ein, je nach AEM Assets-Bereitstellung und den zum Erfassen und Verarbeiten von Assets verwendeten Funktionen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0e0e2aa693c30c8e1ef1033b936b82d83e5b348e
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 51%

---


# Best practices for AEM Assets {#best-practices-for-assets}

Adobe Experience Manager (AEM) Assets ist wichtig für die Bereitstellung von erstklassigen digitalen Marketingerlebnissen, die durch Erhöhung der Inhaltsgeschwindigkeit zum Erreichen von Geschäftszielen beitragen. Wenn Sie mit einer großen Zahl von Assets innerhalb von AEM arbeiten oder regelmäßig zahlreiche Assets wie etwa Videos und dynamische Medien hochladen, ist die Optimierung Ihres Digital Asset Management-Erlebnisses von großer Wichtigkeit für die Systemeffizienz.

Je nachdem, wie Sie AEM Assets für Ihr Unternehmen positioniert haben und welche Funktionen Sie für die Asset-Erfassung, Ausgabegenerierung und Metadatenextraktion verwenden, erhöht die Erkennung und Befolgung von Best Practices in verschiedenen Bereichen deutlich die Systemstabilität und Belastbarkeit.

Nachdem Sie die folgenden Handbücher gelesen haben, verfügen Sie über das Wissen und die Werkzeuge für die Entwicklung und Verwaltung eines Enterprise Asset Management-Systems, das Ihre Anforderungen erfüllt.

* [Leitfaden](performance-tuning-guidelines.md)zur Leistungsoptimierung von AssetsEnthält eine Reihe von Best Practices, die an jedem Punkt in Ihrer Implementierung befolgt werden können, auch wenn Sie live gehen, um sicherzustellen, dass Sie das Beste aus Ihrem System herausholen.
* [Asset-Größenanpassung](assets-sizing-guide.md)Bei der Erstellung von Schätzungen für eine Asset-Implementierung ist es wichtig sicherzustellen, dass ausreichende Ressourcen für Asset-Datenspeicherung, CPU, Speicher, IO und Netzwerkdurchsatz verfügbar sind. Damit diese Elemente dimensioniert werden können, müssen Sie wissen, wie viele Elemente in das System geladen werden. Dieses Handbuch enthält Best Practices, mithilfe derer effiziente Metriken für die Schätzung von Infrastruktur und Ressourcen ermittelt werden können, die für die Bereitstellung von AEM Assets sowie eines Dimensionierungs-Tools erforderlich sind.
* [Handbuch](assets-migration-guide.md)zur Asset-Migration Wenn Sie Assets aus Ihrem Legacy-System nach AEM Assets migrieren möchten, sollten Sie den Migrationsprozess in mehrfacher Hinsicht optimieren. Das Migrationshandbuch enthält Best Practices für die Aufgaben, die Sie durchführen müssen, um die Assets in mehreren Phasen in AEM zu laden. Dazu gehören das Anwenden von Metadaten, das Generieren von Darstellungen und das Aktivieren der Assets zur Veröffentlichung der Bereitstellung.
* [Aspekte des Netzwerks Beim](assets-network-considerations.md)Umgang mit AEM Bereitstellung ist es wichtig, die Netzwerktopologie zu verstehen, um die Netzwerkleistung zu verstehen, Checkpoints zu identifizieren und die erwartete Benutzererfahrung zu beschreiben. Das Dokument über Netzwerkaspekte in Verbindung mit Assets enthält Überlegungen zum Netzwerk bezüglich der Entwicklung für die AEM Assets-Bereitstellung.
* [Asset-Überwachungshandbuch](assets-monitoring-best-practices.md)Nach der Bereitstellung der AEM sollten Sie bestimmte Aufgaben und das System im Allgemeinen überwachen, um die Systemintegrität und -effizienz der Vorgänge sicherzustellen. Die Anleitung zur Überwachung umfasst Best Practices zur Überwachung verschiedener Aspekte Ihres Systems.
* (Deprecated) [Assets offloading guide](assets-offloading-best-practices.md)
Handling large files and running workflows in AEM Assets can consume considerable CPU, memory, and I/O resources. Das Abladen dieser Aufgaben kann CPU-, Speicher- und I/O-Fixkosten verringern. Die Anleitung zur Abladung in Assets enthält empfohlene Einsatzmöglichkeiten und Best Practices für die Abladung in Assets.
* [AEM Best Practices](https://helpx.adobe.com/de/experience-manager/desktop-app/aem-desktop-app-best-practices.html)AEM Desktop-App verknüpft Ihre DAM-Lösung (Digital Asset Management) mit Ihrem Desktop, sodass Sie die in der AEM Web-Benutzeroberfläche verfügbaren Dateien direkt auf dem Desktop öffnen können. Der unkomplizierte Workflow der AEM Desktop App wird anhand auf Desktop-Betriebssystemen gängigen Technologien zur Netzwerkfreigabe ermöglicht. In diesem Leitfaden werden die zentralen Funktionen und empfohlenen Anwendungsgebiete des AEM-Desktop-Programms erläutert.
* [Best Practices](aem-cc-integration-best-practices.md)für die Integration von AEM und Creative Clouden Sie können Ihre AEM-Bereitstellung auf verschiedene Weise in Creative Cloud integrieren. Das Einhalten einiger Best Practices für die Optimierung Ihrer Workflows zur Integration und Asset-Übertragung trägt zum Erzielen der maximalen Effizienz bei. Das vorliegende Handbuch enthält Best Practices für die Integration von AEM Assets mit Adobe Creative Cloud.
* (Deprecated) [AEM to Creative Cloud folder sharing best practices](aem-cc-folder-sharing-best-practices.md)
You can configure AEM to allow users in DAM to share folders with Creative Cloud (CC) users, so they are available as shared folders in the Creative Cloud Assets service. Die Funktion kann verwendet werden, um Dateien zwischen Kreativteams und DAM-Benutzern auszutauschen. Dieses Handbuch enthält Best Practices, um die Freigabe von Ordnern aus AEM in Creative Cloud wirksam einzusetzen.
