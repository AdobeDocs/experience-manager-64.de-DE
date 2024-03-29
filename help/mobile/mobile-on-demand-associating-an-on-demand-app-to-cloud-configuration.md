---
title: Cloud-Konfiguration
seo-title: Cloud Configuration
description: Durch die Verknüpfung einer On-Demand-App mit einer Cloud-Konfiguration kann Adobe Experience Manager (AEM) direkt mit einem von Mobile On-Demand gehosteten Projekt kommunizieren, indem eine Zwei-Wege-Verknüpfung erstellt wird. Auf dieser Seite erfahren Sie mehr.
seo-description: Associating an On-Demand App to a Cloud Configuration allows Adobe Experience Manager (AEM) to communicate directly with a Mobile On-Demand hosted project by establishing a two way link. Follow this page to learn more.
uuid: f377f2af-864b-43df-9d42-4a5fd6cd70d5
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
topic-tags: authoring-on-demand-services-app
discoiquuid: d0d29b99-53d4-4b0d-947b-39d91b381de7
exl-id: eff852b0-99cd-4242-bac8-992ee10401e2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 10%

---

# Cloud-Konfiguration{#cloud-configuration}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes Client-seitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Durch die Verknüpfung einer On-Demand-App mit einer Cloud-Konfiguration kann Adobe Experience Manager (AEM) direkt mit einem von Mobile On-Demand gehosteten Projekt kommunizieren, indem eine Zwei-Wege-Verknüpfung erstellt wird. Wenn Sie Ihre App mit einem On-Demand-Projekt für Mobilgeräte verknüpfen, können Sie Inhalte wie Artikel, Banner und Sammlungen in AEM erstellen, diese Inhalte aber auch für mobile On-Demand bereitstellen.

Von dort aus ist es möglich, Inhalte zu veröffentlichen, in der Vorschau anzuzeigen und zu verwalten. Sie können auch vorhandene mobile On-Demand-Inhalte in AEM importieren und die Inhaltsbearbeitung durchführen.

## Einrichten der Cloud-Konfiguration {#setting-up-cloud-configuration}

>[!CAUTION]
>
>Bevor Sie mit der Konfiguration der Cloud-Konfiguration für Ihre On-Demand-App beginnen, müssen Sie mit der Bereitstellung und Konfiguration des AEM Mobile On-demand Services-Clients für AEM Mobile vertraut sein.
>
>Weitere Informationen finden Sie unter [Einrichten von AEM Mobile On-demand Services](/help/mobile/aem-mobile-setup.md) im Abschnitt &quot;Administration&quot;.

Um Mobile On-Demand-Cloud Services zu konfigurieren, klicken Sie oben rechts im **Verbindung verwalten** -Kachel aus Ihrem App-Dashboard aus.

Sie sollten mit dem App-Dashboard und den verfügbaren Kacheln vertraut sein. Siehe [AEM Mobile Application Dashboard](/help/mobile/mobile-apps-ondemand-application-dashboard.md) für weitere Details.

### Einrichten von Link zur Cloud-Konfiguration {#setting-up-link-to-cloud-configuration}

>[!CAUTION]
>
>Stellen Sie sicher, dass Sie über einen On-Demand-Client und eine Cloud-Konfiguration verfügen.
>
>Weitere Informationen finden Sie unter [Einrichten von AEM Mobile On-demand Services](/help/mobile/aem-mobile-setup.md) im Abschnitt &quot;Administration&quot;.

Die folgenden Schritte beschreiben die Einrichtung eines Links zur Cloud-Konfiguration:

1. Von **Mobile** auswählen **Apps** und dann Ihre Mobile On-Demand-App aus dem Katalog.
1. Klicken Sie auf das Zahnradsymbol auf **Verbindung verwalten** Kachel.

   ![chlimage_1-65](assets/chlimage_1-65.png)

1. Geben Sie die bereits vorhandene Konfiguration ein oder erstellen Sie eine neue, indem Sie die **Konfigurationstitel**, **Geräte-ID** und **Geräte-Token**.

   ![chlimage_1-66](assets/chlimage_1-66.png)

1. Einmal **Geräte-ID** und **Geräte-Token** überprüft wurden, wählen Sie Ihr On-Demand-Projekt aus der Liste aus.

   Klicken Sie auf **Senden**.

   ![chlimage_1-67](assets/chlimage_1-67.png)

   Die **Verbindung verwalten** -Kachel zeigt Ihre Cloud-Konfiguration an.

   ![chlimage_1-68](assets/chlimage_1-68.png)

   >[!CAUTION]
   >
   >Wenn Sie beim Wechsel des Projekts im Dashboard versuchen, das Projekt zu ändern, mit dem diese App verknüpft ist, erhalten Sie eine Warnung zu Problemen mit der Inhaltsintegrität, wie in der folgenden Abbildung dargestellt:

   ![chlimage_1-69](assets/chlimage_1-69.png)

### Die nächsten Schritte {#the-next-steps}

Nachdem Sie die Cloud-Konfiguration für Ihre App konfiguriert haben, finden Sie weitere Informationen zum Verwalten von Inhalten in den folgenden Ressourcen:

* [Verwalten von Artikeln](/help/mobile/mobile-on-demand-managing-articles.md)
* [Verwalten von Bannern](/help/mobile/mobile-on-demand-managing-banners.md)
* [Verwalten von Sammlungen](/help/mobile/mobile-on-demand-managing-collections.md)
* [Hochladen freigegebener Ressourcen](/help/mobile/mobile-on-demand-shared-resources.md)
* [Veröffentlichen/Veröffentlichung des Inhalts rückgängig machen](/help/mobile/mobile-on-demand-publishing-unpublishing.md)
* [Vorschau mit Preflight](/help/mobile/aem-mobile-manage-ondemand-services.md)
