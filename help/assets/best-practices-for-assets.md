---
title: Best Practices zur Verwaltung von Assets mit AEM
description: Identifizieren Sie die Best Practices, die die Systemstabilität und Leistung bei Belastung verbessern, und halten Sie diese ein, je nach AEM Assets-Bereitstellung und den zum Erfassen und Verarbeiten von Assets verwendeten Funktionen.
contentOwner: AG
feature: Asset-Verwaltung
role: Architekt, Administrator
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '655'
ht-degree: 51%

---


# Bewährte Verfahren für AEM Assets {#best-practices-for-assets}

Adobe Experience Manager (AEM) Assets ist wichtig für die Bereitstellung von erstklassigen digitalen Marketingerlebnissen, die durch Erhöhung der Inhaltsgeschwindigkeit zum Erreichen von Geschäftszielen beitragen. Wenn Sie mit einer großen Zahl von Assets innerhalb von AEM arbeiten oder regelmäßig zahlreiche Assets wie etwa Videos und dynamische Medien hochladen, ist die Optimierung Ihres Digital Asset Management-Erlebnisses von großer Wichtigkeit für die Systemeffizienz.

Je nachdem, wie Sie AEM Assets für Ihr Unternehmen positioniert haben und welche Funktionen Sie für die Asset-Erfassung, Ausgabegenerierung und Metadatenextraktion verwenden, erhöht die Erkennung und Befolgung von Best Practices in verschiedenen Bereichen deutlich die Systemstabilität und Belastbarkeit.

Nachdem Sie die folgenden Handbücher gelesen haben, verfügen Sie über das Wissen und die Werkzeuge für die Entwicklung und Verwaltung eines Enterprise Asset Management-Systems, das Ihre Anforderungen erfüllt.

* [Leitfaden zur ](performance-tuning-guidelines.md)
Leistungsoptimierung für AssetsEnthält eine Reihe von Best Practices, die an jedem Punkt in Ihrer Implementierung befolgt werden können, auch wenn Sie live gehen, um sicherzustellen, dass Sie das Beste aus Ihrem System herausholen.
* [Asset-Größenanpassung ](assets-sizing-guide.md)
AnleitungBei der Erstellung von Schätzungen für eine Asset-Implementierung ist sicherzustellen, dass ausreichende Ressourcen in Bezug auf Asset-Datenspeicherung, CPU, Speicher, IO und Netzwerkdurchsatz verfügbar sind. Damit diese Elemente dimensioniert werden können, müssen Sie wissen, wie viele Elemente in das System geladen werden. Dieses Handbuch enthält Best Practices, mithilfe derer effiziente Metriken für die Schätzung von Infrastruktur und Ressourcen ermittelt werden können, die für die Bereitstellung von AEM Assets sowie eines Dimensionierungs-Tools erforderlich sind.
* [Migrationshandbuch für Assets ](assets-migration-guide.md)
Wenn Sie Assets aus Ihrem Legacy-System nach AEM Assets migrieren möchten, müssen Sie den Migrationsprozess in verschiedenen Schritten optimieren. Das Migrationshandbuch enthält Best Practices für die Aufgaben, die Sie durchführen müssen, um die Assets in mehreren Phasen in AEM zu laden. Dazu gehören das Anwenden von Metadaten, das Generieren von Darstellungen und das Aktivieren der Assets zur Veröffentlichung der Bereitstellung.
* [Überlegungen zum Netzwerk ](assets-network-considerations.md)
Bei der Handhabung AEM Bereitstellung ist ein Verständnis der Netzwerktopologie wichtig, um die Netzwerkleistung zu verstehen, Checkpoints zu identifizieren und die erwartete Benutzererfahrung zu beschreiben. Das Dokument über Netzwerkaspekte in Verbindung mit Assets enthält Überlegungen zum Netzwerk bezüglich der Entwicklung für die AEM Assets-Bereitstellung.
* [Asset Monitoring ](assets-monitoring-best-practices.md)
GuideNach der Bereitstellung Ihrer AEM sollten Sie bestimmte Aufgaben und das System im Allgemeinen überwachen, um die Systemintegrität und -effizienz sicherzustellen. Die Anleitung zur Überwachung umfasst Best Practices zur Überwachung verschiedener Aspekte Ihres Systems.
* (Veraltet) [Leitfaden zum Abladen von Assets](assets-offloading-best-practices.md)
Die Handhabung großer Dateien und das Workflows in AEM Assets können erhebliche CPU-, Speicher- und I/O-Ressourcen beanspruchen. Das Abladen dieser Aufgaben kann CPU-, Speicher- und I/O-Fixkosten verringern. Die Anleitung zur Abladung in Assets enthält empfohlene Einsatzmöglichkeiten und Best Practices für die Abladung in Assets.
* [Best ](https://helpx.adobe.com/de/experience-manager/desktop-app/aem-desktop-app-best-practices.html)
Practices für AEM Desktop-AppDie AEM-Desktop-App verbindet Ihre DAM-Lösung (Digital Asset Management) mit Ihrem Desktop, damit Sie die in der AEM Web-Benutzeroberfläche verfügbaren Dateien direkt auf dem Desktop öffnen können. Der unkomplizierte Workflow der AEM Desktop App wird anhand auf Desktop-Betriebssystemen gängigen Technologien zur Netzwerkfreigabe ermöglicht. In diesem Leitfaden werden die zentralen Funktionen und empfohlenen Anwendungsgebiete des AEM-Desktop-Programms erläutert.
* [Best ](aem-cc-integration-best-practices.md)
Practices zur Integration von AEM und Creative CloudSie können Ihre AEM auf verschiedene Weise in Creative Cloud integrieren. Das Einhalten einiger Best Practices für die Optimierung Ihrer Workflows zur Integration und Asset-Übertragung trägt zum Erzielen der maximalen Effizienz bei. Das vorliegende Handbuch enthält Best Practices für die Integration von AEM Assets mit Adobe Creative Cloud.
* (Veraltet) [Best Practices für die Weitergabe in den Creative Cloud-Ordner ](aem-cc-folder-sharing-best-practices.md)
Sie können AEM so konfigurieren, dass Benutzer in DAM Ordner für Creative Cloud-(CC-)Benutzer freigeben können, sodass sie im Creative Cloud Assets-Dienst als freigegebene Ordner verfügbar sind. Die Funktion kann verwendet werden, um Dateien zwischen Kreativteams und DAM-Benutzern auszutauschen. Dieses Handbuch enthält Best Practices, um die Freigabe von Ordnern aus AEM in Creative Cloud wirksam einzusetzen.
