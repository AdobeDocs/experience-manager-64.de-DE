---
title: Einrichten eines Referrer-Filters, um leere zu erlauben
seo-title: Einrichten eines Referrer-Filters, um leere zu erlauben
description: Folgen Sie dieser Seite, um mehr über den Werber-Filter zu erfahren. Damit der AEM Mobile Application Viewer Apps in Ihrer Autoreninstanz Ansicht haben kann, müssen Sie den HTML-Werber-Filter auf "Leer zulassen"einstellen.
seo-description: Folgen Sie dieser Seite, um mehr über den Werber-Filter zu erfahren. Damit der AEM Mobile Application Viewer Apps in Ihrer Autoreninstanz Ansicht haben kann, müssen Sie den HTML-Werber-Filter auf "Leer zulassen"einstellen.
uuid: 4fb0f95c-ac8f-4a14-8c46-6616d9d4f380
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
topic-tags: administering-adobe-phonegap-enterprise
discoiquuid: 8fb7d088-94bf-4799-98b3-8fa58eef83df
translation-type: tm+mt
source-git-commit: 64090e3c7cf722f44968467c51291a11aeeec237
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 47%

---


# Einrichten eines Referrer-Filters, um leere zu erlauben{#setting-your-referrer-filter-to-allow-empty}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Damit der AEM Mobile Application Viewer Apps in Ihrer Autoreninstanz Ansicht haben kann, müssen Sie den HTML-Werber-Filter auf &quot;Leer zulassen&quot;einstellen.

Wenn Sie nicht beabsichtigen, den Anwendungs-Viewer zu verwenden, um Anwendungen im Entwicklungs- und Bereitstellungsstatus zu überprüfen, müssen Sie die Standardeinstellung des Referrer-Filters nicht ändern.

Within your running Author instance of AEM, navigate to: [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr) and search for &#39;Apache Sling Referrer Filter&#39;. Klicken Sie, um den Referrer-Filter bearbeiten, und aktivieren Sie das Kontrollkästchen „leere erlauben“ (siehe folgende Abbildung). Klicken Sie anschließend auf die Schaltfläche „Speichern“ und schließen Sie die Browserseite.

![Referrer-Filtereinstellungen](assets/chlimage_1-106.png)
