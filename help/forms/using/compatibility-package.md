---
title: Kompatibilitätspaket
seo-title: Compatibility Package
description: Durch die Installation des Kompatibilitätspakets auf AEM Forms 6.4 können Sie die Correspondence Management-Assets aus AEM Forms 6.3 und veraltete Vorlagen und Seiten für adaptive Formulare verwenden
seo-description: Installing the Compatibility package on AEM Forms 6.4 allows you to use the Correspondence Management assets from AEM Forms 6.3 and deprecated adaptive forms templates and pages
uuid: e50b1ff9-c357-422a-8da8-a791ff805317
contentOwner: gtalwar
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management, installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: 38a80992-2eda-4535-89af-0de34b1a9686
role: Admin
exl-id: 0bfa0e65-c4cd-4c37-b42b-bff1b777a7be
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 35%

---

# Kompatibilitätspaket installieren {#compatibility-package}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Durch die Installation des Kompatibilitätspakets auf AEM Forms 6.4 können Sie die Correspondence Management-Assets aus AEM Forms 6.3 und veraltete Vorlagen und Seiten für adaptive Formulare verwenden

## Übersicht {#overview}

Interaktive Kommunikation ist der standardmäßige und empfohlene Ansatz zur Erstellung von Kundenkommunikation in AEM Forms 6.4. Um die Briefe aus AEM 6.3 Forms und AEM 6.2 Forms weiterhin verwenden zu können, müssen Sie die [AEMFD-Kompatibilitätspaket](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de).

Mit dem AEMFD-Kompatibilitätspaket können Sie die folgenden Assets aus AEM Forms 6.3 und 6.2 in AEM Forms 6.4 verwenden:

* Dokumentfragmente, die in AEM Forms 6.3 und 6.2 erstellt wurden
* Briefe
* Datenwörterbücher
* Veraltete Vorlagen und Seiten für adaptive Formulare

Weitere Informationen finden Sie unter [Durch Installation des Kompatibilitätspakets mit AEM Forms 6.4 kompatible Assets](/help/forms/using/compatibility-package.md#assetsmadecompatible).

## Unterstützung für AEM Forms 6.3- und 6.2-Assets in AEM Forms 6.4 hinzugefügt {#add-support-for-aem-forms-and-assets-in-aem-forms}

Gehen Sie nach der Aktualisierung wie folgt vor, um das AEM-Kompatibilitätspaket zu installieren und Ihre Assets mit Version 6.4 kompatibel zu machen:

Stellen Sie sicher, dass das [AEM-Kompatibilitätspaket](/help/sites-deploying/backward-compatibility.md) vorinstalliert ist.

1. Installieren Sie die [Kompatibilitätspaket](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de).

   Weitere Informationen zum Hochladen und Installieren des Pakets finden Sie unter [Arbeiten mit Paketen](/help/sites-administering/package-manager.md).

1. Nachdem die Protokolle stabilisiert wurden, starten Sie den Server neu.
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

* Veraltete Seiten für adaptive Formulare:

   * /libs/fd/af/components/page/survey
   * /libs/fd/af/components/page/tabbedenrollment
   * /libs/fd/afaddon/components/page/advancedenrollment
