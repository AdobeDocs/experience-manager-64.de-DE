---
title: Auf Gerätefunktionen zugreifen
seo-title: Access Device Features
description: Auf dieser Seite erfahren Sie, wie Sie AEM Komponenten erstellen, die auf Gerätefunktionen zugreifen. Das AEM PhoneGap Kitchen Sink Github-Repository bietet Entwicklern eine funktionale AEM App, die die Verwendung einer Reihe von Cordova-Core-APIs veranschaulicht.
seo-description: Follow this page to learn about building AEM components that access device features. The AEM PhoneGap Kitchen Sink Github repository provides developers with a functional AEM app that illustrates the use of a number of core Cordova APIs.
uuid: 1996f017-21d3-4d90-9f55-95c626bc4c60
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
discoiquuid: 0019e367-8edc-4a23-bfa4-5beda266ace6
exl-id: 7f3a5081-9640-49ce-a8e7-8061fc080ec1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 13%

---

# Auf Gerätefunktionen zugreifen{#access-device-features}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes Client-seitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

## Erstellen AEM Komponenten, die auf Gerätefunktionen zugreifen {#building-aem-components-that-access-device-features}

Die [AEM PhoneGap Kitchen Sink](https://github.com/blefebvre/aem-phonegap-kitchen-sink) Das GitHub-Repository bietet Entwicklern eine funktionale AEM App, die die Verwendung einer Reihe von Cordova-Core-APIs veranschaulicht. Wenn die App über die PhoneGap-CLI auf iOS oder Android ausgeführt wird, wird sie auf der folgenden Seite geöffnet, auf der sie einen Link zu den einzelnen Geräte-APIs enthält, die sie demonstriert:

![chlimage_1-107](assets/chlimage_1-107.png)

Der Quellcode für jede dieser Geräte-API-Komponenten lautet [verfügbar auf Github](https://github.com/blefebvre/aem-phonegap-kitchen-sink/tree/master/content/src/main/content/jcr_root/apps/brucelefebvre/kitchen-sink/components).

Weitere Informationen zur Verwendung der einzelnen APIs erhalten Sie im Abschnitt [Dokumentation zum Cordova-Plug-in](https://docs.phonegap.com/en/4.0.0/cordova_plugins_pluginapis.md.html).

## Die nächsten Schritte {#the-next-steps}

Siehe [App-Leistung mit Adobe Mobile Analytics verfolgen](/help/mobile/phonegap-intro-to-app-analytics.md).
