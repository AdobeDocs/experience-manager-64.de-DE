---
title: Erstellen der Konfiguration von Artikelexporten
seo-title: Creating Article Export Configuration
description: Auf dieser Seite erfahren Sie mehr über den Export von Inhalten aus Adobe Experience Manager (AEM) zum Hochladen in AEM Mobile.
seo-description: Follow this page to learn about exporting content from Adobe Experience Manager (AEM) for upload to AEM Mobile.
uuid: 089bc15b-669e-4623-bdbb-fd9abf46e098
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
topic-tags: developing-on-demand-services-app
discoiquuid: bc681589-5d46-44cd-888d-b0722a2fd006
exl-id: d6e8412d-09d4-4cac-a691-71703ebaa374
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 8%

---

# Erstellen der Konfiguration von Artikelexporten{#creating-article-export-configuration}

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

Die folgenden Ressourcen beschreiben den Export von Inhalten aus Adobe Experience Manager (AEM) zum Hochladen in AEM Mobile.

Artikel enthalten Inhalte, die exportiert und hochgeladen werden müssen. Ein Teil dieses Inhalts kann zwischen Artikeln freigegeben werden.

Verwendung [ContentSync](/help/mobile/mobile-ondemand-contentsync.md) , um den Inhalt zu sammeln und eine ***Freigegebene Ressourcen*** Paket.

Die Konfiguration von ContentSync unter **&lt;dps-exporttemplate>/dps-article>** sollte so konfiguriert werden, dass alle Inhalte und Artikel exportiert werden, die für das statische Rendering der Eigenschaften auf dem Gerät erforderlich sind.

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
1. Navigieren Sie zu diesem Pfad [/etc/contentsync/templates/dps-we-unlimited-app/dps-article](http://localhost:4502/crx/de/index.jsp#/etc/contentsync/templates/dps-we-unlimited-app/dps-article), um die gemeinsamen Beispielressourcen anzuzeigen.

   Sie können alle Eigenschaften anzeigen, die für die Erstellung Ihrer freigegebenen Ressourcen erforderlich sind, wie in der folgenden Abbildung dargestellt:

   ![chlimage_1-134](assets/chlimage_1-134.png)

>[!NOTE]
>
>Artikel sollten hochgeladen oder nach AEM Mobile On-demand Services exportiert werden, wenn sich der Artikelinhalt ändert.
