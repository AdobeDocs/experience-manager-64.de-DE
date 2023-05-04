---
title: eCommerce
seo-title: eCommerce
description: AEM eCommerce hilft Marketing-Experten bei der Bereitstellung von markenspezifischen, personalisierten Einkaufserlebnissen über Web-, mobile und soziale Touchpoints hinweg.
seo-description: AEM eCommerce helps marketers deliver branded, personalized shopping experiences across web, mobile, and social touchpoints.
uuid: 14af7a3a-7211-4a56-aeef-1603128d5d8a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: e-commerce
content-type: reference
discoiquuid: 68799110-8183-40fe-be4f-2a7c7a7b3018
feature: Commerce Integration Framework
exl-id: 3c046e16-5f54-4a16-aa5b-256b679808fa
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '792'
ht-degree: 41%

---

# eCommerce{#ecommerce}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

* [Konzepte](/help/sites-administering/concepts.md)
* [Verwaltung (generisch)](/help/sites-administering/generic.md)
* [SAP Commerce Cloud](/help/sites-administering/sap-commerce-cloud.md)
* [Salesforce-Commerce Cloud](https://github.com/adobe/commerce-salesforce)
* [Magento](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/integrations.html#!AdobeDocs/commerce-cif-documentation/master/integrations/02-AEM-Magento.md)

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

eCommerce übernimmt zusammen mit dem Produktdatenmanagement (PIM) die Aktivitäten einer Website, die sich auf den Verkauf von Produkten über einen Online-Store konzentriert:

* Erstellung, Lebensdauer und Veralterung eines Produkts
* Preisverwaltung
* Transaktionsmanagement
* Verwaltung von kompletten Katalogen
* Live- und zentralisierte Speicherdatensätze
* Webschnittstellen

AEM eCommerce hilft Marketing-Experten bei der Bereitstellung von markenspezifischen, personalisierten Einkaufserlebnissen über Web-, mobile und soziale Touchpoints hinweg. Die AEM Authoring-Umgebung ermöglicht es Ihnen, Seiten und Komponenten basierend auf dem Zielgruppen-Besucherkontext und Merchandising-Strategien anzupassen. Beispiel:

* Produktseiten
* Warenkorbkomponenten
* Auschecken von Komponenten

Die Implementierung ermöglicht den Echtzeitzugriff auf Produktinformationen. Dies kann verwendet werden, um Folgendes zu erzwingen:

* Integrität der Produktinformationen
* Preise
* Lagerbestand
* Variationen im Status eines Warenkorbs

>[!NOTE]
>
>Um das Integrationsframework mit externen eCommerce-Anbietern zu nutzen, müssen Sie zunächst die benötigten Pakete installieren. Weitere Informationen finden Sie unter [Bereitstellen von eCommerce](/help/sites-deploying/ecommerce.md).
>
>Weitere Informationen zu erweiterten eCommerce-Funktionen finden Sie unter [Entwicklung von eCommerce](/help/sites-developing/ecommerce.md).

## Hauptfunktionen {#main-features}

AEM eCommerce bietet:

* Eine Reihe von **AEM-Komponenten, die vorkonfiguriert sind** und zeigen, was bei Ihrem Projekt möglich ist:

   * Produktanzeige
   * Warenkorb
   * Auschecken
   * Vor Kurzem aufgerufene Produkte
   * Gutscheine
   * und andere

   ![chlimage_1-150](assets/chlimage_1-150.png)

   >[!NOTE]
   >
   >Mit dem von AEM bereitgestellten Integrations-Framework können Sie auch zusätzliche AEM für Commerce-Funktionen erstellen, unabhängig von Ihrer spezifischen eCommerce-Engine.

* **Suche** - entweder:

   * AEM
   * die Suche nach dem eCommerce-System
   * eine Suche von Drittanbietern
   * oder eine Kombination aus diesen Suchmöglichkeiten

   ![chlimage_1-151](assets/chlimage_1-151.png)

* Nutzt die AEM-Funktion zur **Darstellung Ihrer Inhalte auf mehreren Kanälen**, ob im Browserfenster oder auf einem Mobilgerät. So stehen die Inhalte in dem Format bereit, das Ihre Besucher benötigen.

   ![chlimage_1-152](assets/chlimage_1-152.png)

* Funktion zur **Entwicklung Ihrer eigenen Integrationsimplementierung basierend auf dem [AEM eCommerce-Framework](#the-framework)**.

   Die beiden derzeit verfügbaren Implementierungen basieren auf derselben Basis - zusätzlich zur allgemeinen API (dem Framework). Die Implementierung einer neuen Integration umfasst nur die Implementierung der Funktionen, die für Ihre Integration erforderlich sind. Frontendkomponenten können von jeder neuen Implementierung genutzt werden, da sie Schnittstellen verwenden (und somit unabhängig von der Implementierung sind).

* Möglichkeit zur Entwicklung **erlebnisgesteuerter Handel basierend auf Kundendaten und Aktivitäten**. Auf diese Weise können Sie viele Szenarien umsetzen:

   * Beispielsweise können Sie einen Nachlass auf die Versandkosten anbieten, wenn der Gesamtbetrag der Bestellung einen bestimmten Wert überschreitet.
   * Eine andere Möglichkeit bietet Ihnen die Bereitstellung saisonaler Angebote, die Profildaten verwenden (z. B. Standort). Diese können dann hervorgehoben werden, je nach anderen Faktoren, falls erforderlich.

   Im folgenden Beispiel wird ein Teaser angezeigt, da der Inhalt des Warenkorbs weniger als 75 USD beträgt:

   ![chlimage_1-153](assets/chlimage_1-153.png)

   Dies kann geändert werden, wenn der Inhalt des Warenkorbs 75 USD überschreitet:

   ![chlimage_1-154](assets/chlimage_1-154.png)

* Und andere Funktionen wie:

   * Inhalte des Warenkorbs werden sitzungsübergreifend beibehalten
   * Vollständiger Bestellverlauf
   * Express-Katalogaktualisierung

## Der Rahmen {#the-framework}

Die [Konzepte](/help/sites-administering/concepts.md) -Abschnitt behandelt das Framework detaillierter, bietet jedoch im Folgenden eine allgemeine Hochgeschwindigkeits-Ansicht des Frameworks:

### Was? {#what}

* Das Integrations-Framework stellt die API, eine Reihe von Komponenten zur Veranschaulichung der Funktionalität und mehrere Erweiterungen bereit, um Beispiele für Verbindungsmethoden bereitzustellen.
* Das Framework stellt die für eine Projektimplementierung benötigte grundlegende Struktur bereit.
* Das Framework ist erweiterbar.
* Das Framework stellt keine vorkonfigurierte, sofort verwendbare Website bereit. Ein gewisses Maß an Entwicklungsarbeit ist immer erforderlich, um das Framework an Ihre Vorgaben anzupassen.

### Vorteile {#why}

* Bereitstellung der grundlegenden Mechanismen, die für die rasche Realisierung einer angepassten eCommerce-Site erforderlich sind.
* Tp bietet die Flexibilität, die für die Entwicklung einer echten eCommerce-Site erforderlich ist.
* Veranschaulichen Sie Best Practices.
