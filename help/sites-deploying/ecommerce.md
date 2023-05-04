---
title: E-Commerce-Übersicht
seo-title: eCommerce Overview
description: AEM generische eCommerce ist als Teil der Standardinstallation verfügbar und bietet Ihnen die volle Funktionalität des eCommerce-Frameworks.
seo-description: AEM generic eCommerce is available as part of the standard installation and provides you with the full functionality of the eCommerce framework.
uuid: 7be42b1e-f1d6-4891-96f8-0133b3a299a1
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: e-commerce
content-type: reference
discoiquuid: cb043066-aefc-4b68-b302-2b5dd710a786
feature: Commerce Integration Framework
exl-id: d84cd0ec-4586-45c1-a07a-a4d50fcbb629
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 59%

---

# E-Commerce-Übersicht{#ecommerce-overview}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Der generische AEM-E-Commerce ist als Teil einer Standardinstallation verfügbar und bietet Ihnen alle Funktionen des E-Commerce-Frameworks.

Adobe bietet zwei Versionen des Commerce-Integrations-Frameworks:

|  | CIF On-Premise | CIF Cloud |
|-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------|
| Unterstützte AEM-Versionen | AEM On-Premise oder AMS 6.x | AEM AMS 6.4 und 6.5 |
| Back-End | - AEM, Java <br>- Monolithische Integration, voreingestellte Zuordnung (Vorlage)<br>- JCR-Repository | - Magento <br>- Java und JavaScript <br>- Keine Commerce-Daten im JCR-Repository gespeichert |
| Frontend | Server-seitig gerenderte Seiten AEM | Gemischte Seitenanwendung (Hybrid-Rendering) |
| Produktkatalog | - Produktimport-Tool, Editor, Zwischenspeicherung in AEM <br>- Standardkataloge mit AEM- oder Proxy-Seiten | - Kein Produktimport <br>- Generische Vorlagen <br>- On-Demand-Daten über Connector |
| Skalierbarkeit | - Unterstützt bis zu mehrere Millionen Produkte (je nach Anwendungsfall) <br>- Zwischenspeicherung im Dispatcher | - Keine Volumenbegrenzung <br>- Zwischenspeicherung im Dispatcher oder im CDN |
| Standardisiertes Datenmodell | Nein | Ja, Magento GraphQL-Schema |
| Verfügbarkeit | Ja:<br>- SAP-Commerce Cloud (Erweiterung aktualisiert, um AEM 6.4 und Hybris 5 zu unterstützen (Standard) und Kompatibilität mit Hybris 4 zu gewährleisten) <br>- Salesforce-Commerce Cloud (Open-Source-Connector zur Unterstützung von AEM 6.4) | Ja, über Open Source von GitHub. <br> Magento Commerce (unterstützt Magento 2.3.2 (Standard) und kompatibel mit Magento 2.3.1). |
| Verwendungsbereiche | Eingeschränkte Anwendungsfälle: wenn kleine, statische Kataloge importiert werden müssen | Bevorzugte Lösung in den meisten Anwendungsfällen |


## Bereitstellen anderer Implementierungen {#deploying-other-implementations}

* [SAP Commerce Cloud](/help/sites-deploying/sap-commerce-cloud.md)
* [Salesforce-Commerce Cloud](https://github.com/adobe/commerce-salesforce)
* [Magento](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/integrations.html#!AdobeDocs/commerce-cif-documentation/master/integrations/02-AEM-Magento.md)

>[!NOTE]
>
>Weitere Informationen zu den Konzepten und zur Verwaltung von eCommerce-Implementierungen finden Sie unter [Verwaltung von eCommerce](/help/sites-administering/ecommerce.md).
>
>Weitere Informationen zu erweiterten E-Commerce-Funktionen finden Sie unter [Entwicklung von E-Commerce](/help/sites-developing/ecommerce.md).
