---
title: Erstellen und Konfigurieren von Anwendungen
seo-title: Application Create and Configuration Actions
description: Das Erstellen einer App ist häufig der erste Schritt zur Erstellung und Verwaltung von AEM Mobile-On-Demand-Inhalten. Auf dieser Seite erfahren Sie mehr.
seo-description: Creating an app is often the first step towards creating and managing AEM Mobile On-Demand content. Follow this page to learn more.
uuid: f6b41d9a-d896-479e-9f6c-e91a88f3e74d
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
topic-tags: authoring-on-demand-services-app
discoiquuid: ccafd49a-5c8a-44eb-9b0c-37070560bb52
exl-id: 42fa3026-ea37-40e7-8932-147fb3db2784
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 8%

---

# Erstellen und Konfigurieren von Anwendungen{#application-create-and-configuration-actions}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes Client-seitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

## Erstellen einer On-Demand-Anwendung {#creating-an-on-demand-application}

Das Erstellen einer App ist häufig der erste Schritt zur Erstellung und Verwaltung von AEM Mobile-On-Demand-Inhalten. Sie wird häufig auf AEM Administrator-Ebene durchgeführt. Es stellt eine Inhaltshierarchie dar, die auf Mobilgeräten angezeigt werden kann und die zur Anzeige von durch Autoren erstellten Inhalten wie Artikeln, Bildern, Sammlungen usw. bereit ist.

Die Details Ihrer App können im Dashboard oder im AEM Mobile Control Center eingesehen werden.

>[!NOTE]
>
>Das Dashboard ist eine Reihe nützlicher Kacheln, die einen Überblick über den App-Inhalt, die Metadaten und den AEM Mobile On-Demand-Verbindungsstatus bieten.
>
>Siehe [AEM Mobile Application Dashboard](/help/mobile/mobile-apps-ondemand-application-dashboard.md) für Details.

**So erstellen Sie eine On-Demand-App:**

1. Auswählen **Mobile** über die Seitenleiste aus.
1. Auswählen **Apps** aus der Navigation.
1. Klicken **Erstellen** und wählen Sie **App** aus der Dropdown-Liste aus.
1. Wählen Sie die Vorlage Mobile App aus und klicken Sie auf **Nächste**.
1. Geben Sie App-Eigenschaften ein, z. B. **Titel**, **Name**, **Beschreibung**.
1. Klicken Sie auf **Weiter**.
1. Wenn bekannt, geben Sie Details zur Cloud-Konfiguration ein, klicken Sie andernfalls auf **Erstellen**.
1. Klicken **Fertig** , um Ihre neue AEM Mobile-App im Katalog anzuzeigen.

![chlimage_1](assets/chlimage_1.gif)

>[!NOTE]
>
>Auf diese Weise können Sie eine App-Instanz in AEM erstellen.

## Verwenden von App-Vorlagen {#using-app-templates}

App-Vorlagen bieten eine einfache Möglichkeit, vorhandene, von Entwicklern erstellte Designs zu nutzen, die für die Erstellung neuer Apps in AEM verwendet werden.

Was ist eine App-Vorlage? Stellen Sie sich dies als Sammlung von Seitenvorlagen und Komponenten vor, die eine Grundlinie oder Grundlage einer App darstellen.
Wenn Sie eine neue App basierend auf der Vorlage einer anderen App erstellen, erhalten Sie eine App mit einem Startpunkt, der für die App steht, aus der sie erstellt wurde.

Sie müssen über eine vorhandene Vorlage für mobile Apps (oder eine installierte App, die über eine App-Vorlage verfügt) verfügen, um diese Funktion nutzen zu können.

### Der nächste Schritt {#the-next-step}

Nachdem Sie eine On-Demand-App über das Anwendungs-Dashboard erstellt haben, besteht der nächste Schritt darin, Ihre App mit der Cloud-Konfiguration zu verknüpfen.

Siehe [Verknüpfen Ihrer App mit der Cloud-Konfiguration](/help/mobile/mobile-on-demand-associating-an-on-demand-app-to-cloud-configuration.md) für weitere Details.

### Erste Schritte {#getting-ahead}

Sobald Sie mit dem Erstellen einer On-Demand-Anwendung und dem Verknüpfen dieser App mit einer Cloud-Konfiguration vertraut sind, finden Sie weitere Informationen unter [Content Management-Aktionen](/help/mobile/mobile-apps-ondemand-manage-content-ondemand.md).

**Content Management-Aktionen** umfasst die Erstellung und Verwaltung folgender Inhalte:

* [Verwalten von Artikeln](/help/mobile/mobile-on-demand-managing-articles.md)
* [Verwalten von Bannern](/help/mobile/mobile-on-demand-managing-banners.md)
* [Verwalten von Sammlungen](/help/mobile/mobile-on-demand-managing-collections.md)
* [Hochladen freigegebener Ressourcen](/help/mobile/mobile-on-demand-shared-resources.md)
* [Veröffentlichung von Inhalt rückgängig machen](/help/mobile/mobile-on-demand-publishing-unpublishing.md)

Informationen zu den Rollen und Zuständigkeiten von Administratoren und Entwicklern finden Sie in den folgenden Ressourcen:

* [Entwickeln von AEM für AEM Mobile On-demand Services](/help/mobile/aem-mobile-on-demand.md)
* [Verwalten von Inhalten zur Verwendung von AEM Mobile On-demand Services](/help/mobile/aem-mobile.md)
