---
title: Integration mit Adobe Analytics
seo-title: Integrating with Adobe Analytics
description: Erfahren Sie, wie Sie AEM in Adobe Analytics integrieren.
seo-description: Learn how to integrate AEM with Adobe Analytics.
uuid: 8329d891-1897-46f6-80ee-40244b079c0e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 0089394f-0107-49eb-ad73-52e9cabe71b1
exl-id: ca11bfcd-06d1-4ca9-9069-afa91d8a6610
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 75%

---

# Integration mit Adobe Analytics{#integrating-with-adobe-analytics}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Die Integration von Adobe Analytics und AEM ermöglicht es Ihnen, Web-Seiten-Aktivität zu erfassen:

* Eine Adobe Analytics-Konfiguration ermöglicht AEM die Authentifizierung mit Adobe Analytics.
* Ein Framework identifiziert die Daten, die an die Adobe Analytics-Report Suite übermittelt werden.

Die Daten umfassen Seiten- und Benutzerdaten, z. B.:

* Daten, die von AEM-Komponenten erfasst werden
* Link-Klicks
* Videonutzungsdaten
* die Anzahl von Seitenbesuchen aus Adobe Analytics

Die folgenden Seiten helfen Ihnen beim Konfigurieren der Integration:

* [Herstellen einer Verbindung mit Adobe Analytics und Erstellen von Frameworks](/help/sites-administering/adobeanalytics-connect.md)
* [Konfigurieren des Linktrackings für Adobe Analytics](/help/sites-administering/adobeanalytics-link.md)
* [Zuordnen von Komponentendaten zu Adobe Analytics-Eigenschaften](/help/sites-administering/adobeanalytics-mapping.md)
* [Konfigurieren von Videotracking für Adobe Analytics](/help/sites-administering/adobeanalytics-video.md)

Der [Opt-in-Assistent](/help/sites-administering/opt-in.md) erleichtert die Durchführung der Integration.

>[!NOTE]
>
>Siehe auch den Artikel: [Integrieren von AEM mit Adobe Target und Adobe Analytics mithilfe von DTM](https://helpx.adobe.com/de/experience-manager/using/integrate-digital-marketing-solutions.html).

## Weiterführende Informationen {#further-information}

Siehe:

* [Erweitern der Adobe Analytics-Integration](/help/sites-developing/extending-analytics.md), um Informationen zur Entwicklung von Komponenten zu erhalten, die Benutzerdaten erfassen, und zur Anpassung des Adobe Analytics-Frameworks.
* den Knowledgebase-Artikel [Adobe Analytics-Integration – Problembehebung](https://helpx.adobe.com/de/experience-manager/kb/sitecatalystintegrationtroubleshooting.html), um Information zur Behebung von Problemen mit der Adobe Analytics-Integration zu erhalten.

>[!NOTE]
>
>Wenn Sie Adobe Analytics mit einer benutzerdefinierten Proxykonfiguration verwenden, müssen Sie zwei OSGi-Pakete[ (z. B. mit der Web Console) ](/help/sites-deploying/configuring-osgi.md)konfigurieren, die für die **Apache HTTP Client**-Proxykonfigurationen erforderlich sind. Beide sind erforderlich, da einige Funktionen von AEM die 3.x-APIs verwenden, während andere die 4.x-APIs verwenden. Konfigurieren:
>
>* **Day Commons HTTP Client 3.1** zum Konfigurieren der 3.x-API;\
   >  Beispiel: [http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
>
>* **Apache HTTP Components Proxy Configuration** zum Konfigurieren der 4.x-API;
>
>  Beispiel: [http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)
