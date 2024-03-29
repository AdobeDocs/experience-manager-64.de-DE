---
title: JSON-Exporter für Content Services
seo-title: JSON Exporter for Content Services
description: Mit den AEM Content Services können die Beschreibung und Bereitstellung von Inhalten in/über AEM über einen Fokus auf Web-Seiten hinweg generalisiert werden. Sie ermöglichen die Bereitstellung von Inhalten in Kanälen, die keine traditionellen AEM-Web-Seiten sind, und nutzen standardisierte Methoden, die von allen Clients genutzt werden können.
seo-description: AEM Content Services are designed to generalize the description and delivery of content in/from AEM beyond a focus on web pages. They provide the delivery of content to channels that are not traditional AEM web pages, using standardized methods that can be consumed by any client.
uuid: be6457b1-fa9c-4f3b-b219-01a4afc239e7
contentOwner: User
content-type: reference
topic-tags: components
products: SG_EXPERIENCEMANAGER/6.4/SITES
discoiquuid: 4c7e33ea-f2d3-4d69-b676-aeb50c610d70
exl-id: ead4306a-6337-4dae-8839-14fada0ae0e5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 76%

---

# JSON-Exporter für Content Services{#json-exporter-for-content-services}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Mit den AEM Content Services können die Beschreibung und Bereitstellung von Inhalten in/über AEM über einen Fokus auf Web-Seiten hinweg generalisiert werden.

Sie ermöglichen die Bereitstellung von Inhalten in Kanälen, die keine traditionellen AEM-Web-Seiten sind, und nutzen standardisierte Methoden, die von allen Clients genutzt werden können. Diese Kanäle können Folgendes sein:

* [Single Page Applications (SPA)](spa-walkthrough.md)
* native Mobile Apps
* weitere AEM-externe Kanäle und Touchpoints

Über Inhaltsfragmente, die strukturierte Inhalte verwenden, können Sie Content Services zur Verfügung stellen, indem Sie die Inhalte mit JSON Exporter auf einer (beliebigen) AEM-Seite im JSON-Datenmodellformat bereitstellen. Diese können dann von Ihren eigenen Anwendungen genutzt werden.

>[!NOTE]
>
>Die hier beschriebene Funktionalität ist für alle Kernkomponenten seit [Version 1.1.0 der Kernkomponenten](https://docs.adobe.com/content/docs/de/core-components/v1.html) verfügbar.

## JSON Exporter mit Inhaltsfragment-Kernkomponenten {#json-exporter-with-content-fragment-core-components}

Mit dem AEM JSON Exporter können Sie den Inhalt einer (y) AEM Seite im JSON-Datenmodellformat bereitstellen. Diese können dann von Ihren eigenen Anwendungen genutzt werden.

In AEM erfolgt die Bereitstellung mit dem `model`-Selektor und der `.json`-Erweiterung.

`.model.json`

1. Beispielsweise eine URL wie:

   ```shell
   http://localhost:4502/content/we-retail/language-masters/en.model.json
   ```

1. liefert Inhalte wie:

   ![chlimage_1-192](assets/chlimage_1-192.png)

Alternativ können Sie die Inhalte eines strukturierten Inhaltsfragments bereitstellen, indem Sie dieses spezifisch nachverfolgen.

Verwenden Sie dazu den vollständigen Pfad zum Fragment (über `jcr:content`); beispielsweise mit dem folgenden Suffix:

`.../jcr:content/root/responsivegrid/contentfragment.model.json`

Ihre Seite kann entweder ein einzelnes Inhaltsfragment oder mehrere Komponenten verschiedener Typen enthalten. Sie können auch Mechanismen wie Listenkomponenten verwenden, um automatisch nach relevanten Inhalten zu suchen.

* Beispielsweise eine URL wie:

   ```shell
   http://localhost:4502/content/we-retail/language-masters/en/manchester-airport/jcr:content/root/responsivegrid/contentfragment.model.json
   ```

* liefert Inhalte wie:

   ![chlimage_1-193](assets/chlimage_1-193.png)

   >[!NOTE]
   >
   >Sie können [Ihre eigenen Komponenten anpassen](/help/sites-developing/json-exporter-components.md), um auf diese Daten zuzugreifen und sie zu verwenden.

   >[!NOTE]
   >
   >Obwohl es sich nicht um eine Standardimplementierung handelt, werden [mehrere Selektoren unterstützt,](json-exporter-components.md#multiple-selectors) jedoch muss `model` der erste sein.

### Weiterführende Informationen {#further-information}

Siehe auch:

* Assets-HTTP-API

   * [Assets-HTTP-API](/help/assets/mac-api-assets.md)

* Sling-Modelle:

   * [Sling-Modelle - Verknüpfen einer Modellklasse mit einem Ressourcentyp seit 130](https://sling.apache.org/documentation/bundles/models.html#associating-a-model-class-with-a-resource-type-since-130)

* AEM mit JSON:

   * [Ermitteln von Seiteninformationen im JSON-Format](/help/sites-developing/pageinfo.md)

## Verwandte Dokumentation {#related-documentation}

Weitere Informationen finden Sie unter:

* Das [Thema „Inhaltsfragmente“ im Assets-Benutzerhandbuch](https://helpx.adobe.com/de/experience-manager/6-4/assets/user-guide.html?topic=/experience-manager/6-4/assets/morehelp/content-fragments.ug.js)

* [Inhaltsfragmentmodelle](/help/assets/content-fragments-models.md)
* [Bearbeitung mit Inhaltsfragmenten](/help/sites-authoring/content-fragments.md)
* [Aktivieren eines JSON-Exports für eine Komponente](/help/sites-developing/json-exporter-components.md)

* [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) und die [Inhaltsfragmentkomponente](https://helpx.adobe.com/de/experience-manager/core-components/using/content-fragment-component.html)
