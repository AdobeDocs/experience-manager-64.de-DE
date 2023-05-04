---
title: Erstellen der Exportkonfiguration für freigegebene Ressourcen
seo-title: Creating Shared Resources Export Configuration
description: Auf dieser Seite erfahren Sie, wie Sie freigegebene Ressourcen aus Adobe Experience Manager (AEM) zum Hochladen in AEM Mobile exportieren.
seo-description: Follow this page to learn about exporting shared resources from Adobe Experience Manager (AEM) for upload to AEM Mobile.
uuid: 99b8ff94-8135-4643-a15b-aa6fb91f5401
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
topic-tags: developing-on-demand-services-app
discoiquuid: 1edf6c76-ccb1-40b6-bdf6-924f1461cd28
exl-id: 92ee8c25-9f11-4743-a8e6-1f4986d09a6a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 8%

---

# Erstellen der Exportkonfiguration für freigegebene Ressourcen{#creating-shared-resources-export-configuration}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes Client-seitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

>[!CAUTION]
>
>**Voraussetzung**:
>
>Bevor Sie mehr über das Erstellen und Ändern freigegebener Ressourcen erfahren, lesen Sie [Inhaltssynchronisierung](/help/mobile/mobile-ondemand-contentsync.md) um die grundlegenden Konzepte zu verstehen.

AEM Mobile-Benutzer verwenden die Inhaltssynchronisierung, um Live-Inhalte für die Verwendung in mobilen Apps in statische Inhalte zu exportieren. Dieser Export erfolgt beim Hochladen von Inhalten in Mobile On-Demand Services von AEM Mobile.

Die Eigenschaft ***dps-exportTemplate*** definiert den Pfad zu den Exportkonfigurationen der App. Legen Sie diese Eigenschaft fest, um freigegebene Ressourcen zu erstellen und zu ändern.

In den folgenden Ressourcen wird der Export von freigegebenen Ressourcen aus Adobe Experience Manager (AEM) zum Hochladen in AEM Mobile beschrieben.

Freigegebene HTML-Ressourcen ermöglichen es Artikeln, HTML-Ressourcen freizugeben, die andernfalls für alle Artikel dupliziert werden müssen, und können Symbole, Schriftarten, JavaScript und CSS enthalten.

Die Konfiguration zur Inhaltssynchronisierung finden Sie unter **&lt;dps-exporttemplate>/dps-HTMLResources>** sollte so konfiguriert werden, dass alle Inhalte und Artikel exportiert werden, die für das statische Rendering der Eigenschaften auf dem Gerät erforderlich sind.

>[!CAUTION]
>
>Sie können die folgenden Schritte ausführen, um Beispiel für freigegebene Ressourcen anzuzeigen, nur wenn Sie über Folgendes verfügen:
>
>* den Beispielinhalt installiert hat
>* AEM
>* kein konfigurierter benutzerdefinierter Kontext oder ein anderer Port
>


Informationen zum Anzeigen einer gemeinsam genutzten Beispielressource finden Sie in den folgenden Schritten:

1. Öffnen Sie die CRXDE Lite auf Ihrem AEM.
1. Navigieren Sie zu diesem Pfad *[/etc/contentsync/templates/dps-we-unlimited-app/dps-HTMLResources](http://localhost:4502/crx/de/index.jsp#/etc/contentsync/templates/dps-we-unlimited-app/dps-HTMLResources)*, um die gemeinsamen Beispielressourcen anzuzeigen.

   Sie können alle Eigenschaften anzeigen, die für die Erstellung Ihrer freigegebenen Ressourcen erforderlich sind, wie in der folgenden Abbildung dargestellt:

   ![chlimage_1-145](assets/chlimage_1-145.png)

>[!NOTE]
>
>Freigegebene Ressourcen sollten hochgeladen oder nach AEM Mobile On-demand Services exportiert werden, wenn sich eine der freigegebenen Ressourcen ändert.
