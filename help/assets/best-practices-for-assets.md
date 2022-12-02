---
title: Best Practices zum Verwalten von Assets mithilfe von AEM
description: Ermitteln und Einhalten der Best Practices, die die Systemstabilität und -leistung unter Belastung verbessern, je nach [!DNL Experience Manager] Assets-Bereitstellung und Funktionen zur Erfassung und Verarbeitung von Assets.
contentOwner: AG
feature: Asset Management
role: Architect,Admin
exl-id: e2ab924b-53cb-4011-8c0a-9e8e59dd2f16
source-git-commit: d750c852b6367d753d18be57c8910bf5671fd5e8
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 25%

---

# Best Practices für [!DNL Experience Manager] Assets {#best-practices-for-assets}

Adobe Experience Manager Assets ist ein wichtiger Bestandteil der Bereitstellung hochwertiger digitaler Marketingerlebnisse, die durch die Beschleunigung Ihrer Content-Geschwindigkeit zur Erreichung von Geschäftszielen beitragen. Wenn Sie mit einer großen Anzahl von Assets in [!DNL Assets] Sie können regelmäßig/regelmäßig zahlreiche Assets, einschließlich Videos und dynamische Medien, hochladen. Die Optimierung Ihres Digital Asset Management-Erlebnisses ist für die Systemeffizienz von entscheidender Bedeutung.

Je nachdem, wie Sie sich positioniert haben [!DNL Assets] für Ihr Unternehmen und die Funktionen, die Sie für die Asset-Erfassung, Ausgabegenerierung und Metadatenextraktion verwenden, verbessert die Identifizierung und Einhaltung von Best Practices in verschiedenen Bereichen erheblich die Systemstabilität und Leistung bei Belastung.

Nachdem Sie die folgenden Handbücher gelesen haben, verfügen Sie über das Wissen und die Werkzeuge für die Entwicklung und Verwaltung eines Enterprise Asset Management-Systems, das Ihre Anforderungen erfüllt.

* [Handbuch zur Leistungsoptimierung von Assets](performance-tuning-guidelines.md)
Enthält eine Reihe von Best Practices, die Sie an jedem beliebigen Punkt in Ihrer Implementierung auch nach der Live-Schaltung anwenden können, um sicherzustellen, dass Sie Ihr System optimal nutzen.
* [Handbuch zur Dimensionierung von Assets](assets-sizing-guide.md)
Bei der Erstellung von Schätzungen für eine Assets-Implementierung ist es wichtig sicherzustellen, dass ausreichend Ressourcen für Asset-Speicher, CPU, Speicher, I/O und Netzwerkdurchsatz verfügbar sind. Damit diese Elemente dimensioniert werden können, müssen Sie wissen, wie viele Elemente in das System geladen werden. Dieses Handbuch enthält Best Practices, mit denen Sie effiziente Metriken zur Schätzung der für die Bereitstellung erforderlichen Infrastruktur und Ressourcen ermitteln können [!DNL Experience Manager] Assets sowie ein Dimensionierungswerkzeug.
* [Handbuch zur Asset-Migration](assets-migration-guide.md)
Wenn Sie Assets aus Ihrem alten System in [!DNL Experience Manager] Bei Assets sind mehrere Schritte zu beachten, um den Migrationsprozess zu optimieren. Das Migrationshandbuch enthält Best Practices für die Aufgaben, die Sie durchführen müssen, um die Assets in mehreren Phasen in [!DNL Experience Manager] zu laden. Dazu gehören das Anwenden von Metadaten, das Generieren von Ausgabedarstellungen und das Aktivieren der Assets für die Veröffentlichungsbereitstellung.
* [Überlegungen zum Assets-Netzwerk](assets-network-considerations.md)
Bei der Handhabung von [!DNL Experience Manager] -Implementierung müssen Sie die Netzwerktopologie verstehen, um die Netzwerkleistung zu verstehen, Engpässe zu identifizieren und das erwartete Benutzererlebnis zu beschreiben. Das Dokument zu Netzwerküberlegungen für Assets erläutert Netzwerküberlegungen bei der Erstellung Ihrer [!DNL Experience Manager] Asset-Bereitstellung.
* [Handbuch zur Asset-Überwachung](assets-monitoring-best-practices.md)
Nach [!DNL Experience Manager] -Implementierung bereitgestellt ist, sollten Sie bestimmte Aufgaben und das System im Allgemeinen überwachen, um die Systemintegrität und Effizienz der Vorgänge sicherzustellen. Die Anleitung zur Überwachung umfasst Best Practices zur Überwachung verschiedener Aspekte Ihres Systems.
* (Veraltet) [Handbuch zur Asset-Abladung](assets-offloading-best-practices.md)
Umgang mit großen Dateien und laufende Workflows in [!DNL Experience Manager] Assets können erhebliche CPU-, Speicher- und I/O-Ressourcen beanspruchen. Das Abladen dieser Aufgaben kann CPU-, Speicher- und I/O-Fixkosten verringern. Die Anleitung zur Abladung in Assets enthält empfohlene Einsatzmöglichkeiten und Best Practices für die Abladung in Assets.
* [[!DNL Experience Manager] Best Practices für das Desktop-Programm](https://helpx.adobe.com/de/experience-manager/desktop-app/aem-desktop-app-best-practices.html)
   [!DNL Experience Manager] Das -Desktop-Programm verknüpft Ihre Digital Asset Management (DAM)-Lösung mit Ihrem Desktop, damit Sie die Dateien öffnen können, die in der [!DNL Experience Manager] Web-Benutzeroberfläche direkt auf dem Desktop. [!DNL Experience Manager] Der benutzerfreundliche Workflow des Desktop-Programms wird mithilfe der Netzwerkfreigabetechnologie aktiviert, die von Desktop-Betriebssystemen bereitgestellt wird. In diesem Leitfaden werden die zentralen Funktionen und empfohlenen Anwendungsgebiete der [!DNL Experience Manager]-Desktop-App erläutert.
* [[!DNL Experience Manager] Best Practices für die Creative Cloud-Integration](aem-cc-integration-best-practices.md)
Sie können Ihre [!DNL Experience Manager] -Implementierung mit Creative Cloud auf verschiedene Arten. Das Einhalten einiger Best Practices für die Optimierung Ihrer Workflows zur Integration und Asset-Übertragung trägt zum Erzielen der maximalen Effizienz bei. Dieses Handbuch enthält Best Practices zur Integration von [!DNL Experience Manager] Assets mit Adobe Creative Cloud.
* (Veraltet) [[!DNL Experience Manager] Best Practices für die Ordnerfreigabe in Creative Cloud](aem-cc-folder-sharing-best-practices.md)
Sie können [!DNL Experience Manager] , damit Benutzer in DAM Ordner für Creative Cloud-Benutzer freigeben können, damit sie als freigegebene Ordner im Creative Cloud Assets-Dienst verfügbar sind. Die Funktion kann verwendet werden, um Dateien zwischen Kreativteams und DAM-Benutzern auszutauschen. In diesem Handbuch werden Best Practices für die Nutzung der [!DNL Experience Manager] zur Ordnerfreigabe in Creative Cloud.
