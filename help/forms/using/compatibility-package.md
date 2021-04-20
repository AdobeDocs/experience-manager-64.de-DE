---
title: Kompatibilitätspaket
seo-title: Kompatibilitätspaket
description: 'Die Installation des Kompatibilitätspakets auf AEM Forms 6.4 ermöglicht es Ihnen, die Correspondence Management-Assets aus AEM Forms 6.3 sowie veraltete Vorlagen und Seiten für adaptive Formulare zu verwenden. '
seo-description: Die Installation des Kompatibilitätspakets auf AEM Forms 6.4 ermöglicht es Ihnen, die Correspondence Management-Assets aus AEM Forms 6.3 sowie veraltete Vorlagen und Seiten für adaptive Formulare zu verwenden.
uuid: e50b1ff9-c357-422a-8da8-a791ff805317
contentOwner: gtalwar
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management, installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: 38a80992-2eda-4535-89af-0de34b1a9686
role: Administrator
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 91%

---


# Kompatibilitätspaket {#compatibility-package} installieren

Die Installation des Kompatibilitätspakets auf AEM Forms 6.4 ermöglicht es Ihnen, die Correspondence Management-Assets aus AEM Forms 6.3 sowie veraltete Vorlagen und Seiten für adaptive Formulare zu verwenden.

## Überblick {#overview}

Interaktive Kommunikation ist der standardmäßige und empfohlene Ansatz zum Erstellen von Kundenkommunikation in AEM Forms 6.4. Um die Briefe aus AEM 6.3 Forms und AEM 6.2 Forms weiterhin verwenden zu können, müssen Sie das [AEMFD-Kompatibilitätspaket](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-COMPAT) installieren.

Das AEMFD-Kompatibilitätspaket ermöglicht es Ihnen, die folgenden Assets aus AEM Forms 6.3 und 6.2 auf AEM Forms 6.4 zu verwenden:

* In AEM Forms 6.3 und 6.2 erstellte Dokumentfragmente
* Briefe
* Datenwörterbücher
* Veraltete Vorlagen und Seiten für adaptive Formulare

Weitere Informationen finden Sie unter [Elemente, die mit AEM Forms 6.4 kompatibel gemacht wurden, indem Sie das Kompatibilitätspaket](/help/forms/using/compatibility-package.md#assetsmadecompatible) installieren.

## Unterstützung für Assets aus AEM Forms 6.3 und 6.2 in AEM Forms 6.4 hinzufügen {#add-support-for-aem-forms-and-assets-in-aem-forms}

Gehen Sie nach der Aktualisierung wie folgt vor, um das AEM-Kompatibilitätspaket zu installieren und Ihre Assets mit Version 6.4 kompatibel zu machen:

Vergewissern Sie sich, dass [AEM Compatibility Package](/help/sites-deploying/backward-compatibility.md) vorinstalliert ist.

1. Installieren Sie das [Kompatibilitätspaket](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-COMPAT).

   Weitere Informationen zum Hochladen und Installieren des Pakets finden Sie unter [Arbeiten mit Paketen](/help/sites-administering/package-manager.md).

1. Nachdem die Protokolle stabilisiert sind, starten Sie den Server neu.
1. Verwenden Sie das Migrationsdienstprogramm, um Ihre Assets mit Version 6.4 kompatibel zu machen.

   Weitere Informationen finden Sie unter [Migrationsdienstprogramm](/help/forms/using/migration-utility.md).

## Durch Installation des Kompatibilitätspakets mit AEM Forms 6.4 kompatible Assets {#assetsmadecompatible}

Durch Installation des Kompatibilitätspakets können Sie die folgenden Assets und Vorlagen mit AEM Forms 6.4 kompatibel machen:

* Correspondence Management-Assets aus AEM 6.3 und früher

   * [Briefe](/help/forms/using/create-letter.md)
   * [Datenwörterbücher](/help/forms/using/data-dictionary.md)
   * Dokumentfragmente

* Veraltete Vorlagen für adaptive Formulare

   * /libs/fd/af/templates/blankTemplate2
   * /libs/fd/af/templates/simpleEnrollmentTemplate
   * /libs/fd/af/templates/simpleEnrollmentTemplate2
   * /libs/fd/af/templates/surveyTemplate
   * /libs/fd/af/templates/surveyTemplate2
   * /libs/fd/af/templates/tabbedEnrollmentTemplate
   * /libs/fd/af/templates/tabbedEnrollmentTemplate2
   * /libs/fd/afaddon/templates/advancedEnrollmentTemplate
   * /libs/fd/afaddon/templates/advancedEnrollmentTemplate2

* Veraltete Seiten für adaptive Formulare

   * /libs/fd/af/components/page/survey
   * /libs/fd/af/components/page/tabbedenrollment
   * /libs/fd/afaddon/components/page/advancedenrollment

