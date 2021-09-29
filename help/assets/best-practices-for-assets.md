---
title: Best Practices zum Verwalten von Assets mithilfe von AEM
description: Ermitteln und halten Sie die Best Practices ein, die die Systemstabilität und -leistung unter Last verbessern, je nach [!DNL Experience Manager] Assets-Bereitstellung und Funktionen, die zum Erfassen und Verarbeiten von Assets verwendet werden.
contentOwner: AG
feature: Asset Management
role: Architect,Admin
exl-id: e2ab924b-53cb-4011-8c0a-9e8e59dd2f16
source-git-commit: de5632ff0ee87a4ded88e792b57e818baf4c01a3
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 20%

---

# Best Practices für [!DNL Experience Manager] Assets {#best-practices-for-assets}

Adobe Experience Manager Assets ist ein wichtiger Bestandteil der Bereitstellung hochwertiger digitaler Marketingerlebnisse, die durch die Beschleunigung Ihrer Content-Geschwindigkeit zur Erreichung von Geschäftszielen beitragen. Wenn Sie mit einer großen Anzahl von Assets in [!DNL Assets] arbeiten oder regelmäßig/regelmäßig zahlreiche Assets hochladen, einschließlich Videos und Dynamic Media, ist die Optimierung Ihres Digital Asset Management-Erlebnisses für die Systemeffizienz von entscheidender Bedeutung.

Je nachdem, wie Sie [!DNL Assets] für Ihr Unternehmen positioniert haben und welche Funktionen Sie für die Asset-Erfassung, Ausgabegenerierung und Metadatenextraktion verwenden, verbessert die Identifizierung und Einhaltung der Best Practices in verschiedenen Bereichen erheblich die Systemstabilität und die Leistung bei Belastung.

Nachdem Sie die folgenden Handbücher gelesen haben, verfügen Sie über das Wissen und die Werkzeuge für die Entwicklung und Verwaltung eines Enterprise Asset Management-Systems, das Ihre Anforderungen erfüllt.

* [Handbuch zur ](performance-tuning-guidelines.md)
Leistungsoptimierung von AssetsEnthält eine Reihe von Best Practices, die an jedem Punkt in Ihrer Implementierung auch nach der Live-Schaltung befolgt werden können, um sicherzustellen, dass Sie Ihr System optimal nutzen.
* [Handbuch zur Asset-Größenanpassung ](assets-sizing-guide.md)
Bei der Erstellung von Schätzungen für eine Assets-Implementierung ist es wichtig sicherzustellen, dass ausreichend Ressourcen zur Verfügung stehen, was Asset-Speicher, CPU, Speicher, I/O- und Netzwerkdurchsatz betrifft. Damit diese Elemente dimensioniert werden können, müssen Sie wissen, wie viele Elemente in das System geladen werden. Dieses Handbuch enthält Best Practices, mit denen Sie effiziente Metriken für die Schätzung der Infrastruktur und der Ressourcen ermitteln können, die für die Bereitstellung von [!DNL Experience Manager] Assets erforderlich sind, sowie ein Dimensionierungs-Tool.
* [Handbuch ](assets-migration-guide.md)
zur Migration von AssetsWenn Sie Assets aus Ihrem alten System in  [!DNL Experience Manager] Assets migrieren möchten, sind verschiedene Schritte zu beachten, um den Migrationsprozess zu optimieren. Das Migrationshandbuch enthält Best Practices für die Aufgaben, die Sie ausführen, um die Assets schrittweise in [!DNL Experience Manager] zu übertragen. Dazu gehören das Anwenden von Metadaten, das Generieren von Ausgabedarstellungen und das Aktivieren der Assets für die Veröffentlichungsbereitstellung.
* [Überlegungen zum Assets-Netzwerk ](assets-network-considerations.md)
Bei der  [!DNL Experience Manager] Bereitstellung ist ein Verständnis der Netzwerktopologie wichtig, um die Netzwerkleistung zu verstehen, Engpässe zu ermitteln und das erwartete Benutzererlebnis zu beschreiben. Das Dokument zu Netzwerküberlegungen für Assets erläutert Netzwerküberlegungen bei der Erstellung Ihrer [!DNL Experience Manager] Asset-Bereitstellung.
* [Überwachungshandbuch zu Assets ](assets-monitoring-best-practices.md)
Nach der Bereitstellung Ihrer  [!DNL Experience Manager] Bereitstellung sollten Sie bestimmte Aufgaben und das System im Allgemeinen überwachen, um die Systemintegrität und Effizienz der Vorgänge sicherzustellen. Die Anleitung zur Überwachung umfasst Best Practices zur Überwachung verschiedener Aspekte Ihres Systems.
* (Veraltet) [Handbuch zur Asset-Abladung](assets-offloading-best-practices.md)
Die Verarbeitung großer Dateien und die Ausführung von Workflows in [!DNL Experience Manager] Assets können erhebliche CPU-, Speicher- und I/O-Ressourcen beanspruchen. Das Abladen dieser Aufgaben kann CPU-, Speicher- und I/O-Fixkosten verringern. Die Anleitung zur Abladung in Assets enthält empfohlene Einsatzmöglichkeiten und Best Practices für die Abladung in Assets.
* [[!DNL Experience Manager] Best Practices für das Desktop-Programm](https://helpx.adobe.com/de/experience-manager/desktop-app/aem-desktop-app-best-practices.html)
   [!DNL Experience Manager] Das -Desktop-Programm verknüpft Ihre DAM-Lösung (Digital Asset Management) mit Ihrem Desktop, damit Sie die in der  [!DNL Experience Manager] Web-Benutzeroberfläche verfügbaren Dateien direkt auf dem Desktop öffnen können. [!DNL Experience Manager] Der benutzerfreundliche Workflow des Desktop-Programms wird mithilfe der Netzwerkfreigabetechnologie aktiviert, die von Desktop-Betriebssystemen bereitgestellt wird. In diesem Handbuch werden die wichtigsten Funktionen und empfohlenen Verwendungen des [!DNL Experience Manager]-Desktop-Programms erläutert.
* [[!DNL Experience Manager] Best ](aem-cc-integration-best-practices.md)
Practices für die Integration von Creative CloudenSie können Ihre  [!DNL Experience Manager] Implementierung auf verschiedene Arten mit Creative Cloud integrieren. Das Einhalten einiger Best Practices für die Optimierung Ihrer Workflows zur Integration und Asset-Übertragung trägt zum Erzielen der maximalen Effizienz bei. Dieses Handbuch enthält Best Practices zur Integration von [!DNL Experience Manager] Assets mit Adobe Creative Cloud.
* (Veraltet) [[!DNL Experience Manager] Best Practices für die Ordnerfreigabe in Creative Cloud](aem-cc-folder-sharing-best-practices.md)
Sie können [!DNL Experience Manager] so konfigurieren, dass Benutzer in DAM Ordner für Creative Cloud-Benutzer (CC) freigeben können, damit sie als freigegebene Ordner im Creative Cloud Assets-Dienst verfügbar sind. Die Funktion kann verwendet werden, um Dateien zwischen Kreativteams und DAM-Benutzern auszutauschen. In diesem Handbuch werden Best Practices für die Nutzung der Funktion [!DNL Experience Manager] zur Ordnerfreigabe in Creative Cloud erläutert.
