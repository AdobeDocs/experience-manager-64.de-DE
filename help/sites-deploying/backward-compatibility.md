---
title: Abwärtskompatibilität in AEM 6.4
seo-title: Abwärtskompatibilität in AEM 6.4
description: Erfahren Sie, wie Sie Ihre Apps und Konfigurationen mit AEM 6.4 kompatibel machen.
seo-description: Erfahren Sie, wie Sie Ihre Apps und Konfigurationen mit AEM 6.4 kompatibel machen.
uuid: 2fa8525e-7f3b-4096-ac85-01c2c76bc9ac
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: upgrading
content-type: reference
discoiquuid: 5e76fe09-4d37-4c8c-8baf-97e75689bd26
feature: Upgrading
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 77%

---


# Abwärtskompatibilität in AEM 6.4{#backward-compatibility-in-aem}

## Überblick {#overview}

>[!NOTE]
>
>Eine Liste der Inhalts- und Konfigurationsänderungen, die nicht unter das Kompatibilitätspaket fallen, finden Sie unter [Repository-Umstrukturierung in AEM 6.4](/help/sites-deploying/repository-restructuring.md).

In AEM 6.4 wurden alle Funktionen mit Rückwärtskompatibilität entwickelt.

In den meisten Fällen sollten Kunden, die mit AEM 6.3 arbeiten, weder ihren Code noch ihre Anpassungen ändern müssen, wenn sie die Aktualisierung durchführen. Für AEM 6.1- und 6.2-Kunden gibt es keine zusätzlichen Änderungen, die sich während eines Upgrades auf 6.3 ändern würden.

Für die Ausnahmen, in denen Funktionen nicht abwärtskompatibel realisiert werden konnten, kann die Abwärtskompatibilität für Bundles und Inhalte erzielt werden, indem ein Kompatibilitätspaket für 6.3 installiert wird (im Folgenden finden Sie weitere Informationen und erfahren, wo Sie das Paket herunterladen können). Dieses Kompatibilitätspaket stellt die Kompatibilität für Anwendungen wieder her, die AEM 6.3 entsprechen.

Mit dem Kompatibilitätspaket können Sie AEM im Kompatibilitätsmodus ausführen und so die benutzerdefinierte Entwicklung für neue AEM-Funktionen zurückstellen:

>[!NOTE]
>
>Beachten Sie, dass das Kompatibilitätspaket nur eine Zwischenlösung ist, um die für die Kompatibilität mit AEM 6.4 erforderliche Entwicklung aufzuschieben. Es wird nur als letzte Option empfohlen, falls Sie Kompatibilitätsprobleme nicht direkt nach der Aktualisierung durch Eigenentwicklungen beheben können. Es wird dringend empfohlen, in den nativen Modus zu wechseln und das Kompatibilitätspaket zu deinstallieren, sobald Sie auf 6.4 basierende Eigenentwicklungen vornehmen, damit Sie den vollen Funktionsumfang von 6.4 nutzen können.

![screen_shot_2018-04-05at43339pm](assets/screen_shot_2018-04-05at43339pm.png)

Das Kompatibilitätspaket bietet zwei Modi: **Routing aktiviert** und **Routing deaktiviert**.

Damit kann AEM 6.4 in drei Modi ausgeführt werden:

**Nativer Modus:** 

Der native Modus eignet sich für Kunden, die alle neuen Funktionen von AEM 6.4 nutzen möchten und bereit sind, ihre Anpassungen durch Entwicklungsarbeiten an die neuen Funktionen anzupassen.

Dies bedeutet, dass Sie die Korrekturen in Ihrer Anwendung sofort nach der Aktualisierung durchführen müssen.

**Kompatibilitätsmodus: Kompatibilitätspaket mit aktiviertem Routing installiert** 

Der Kompatibilitätsmodus eignet sich für Kunden, die Schnittstellen angepasst haben, die nicht abwärtskompatibel sind. Damit kann AEM im Kompatibilitätsmodus ausgeführt und die für nicht mit Ihrem benutzerdefinierten Code kompatible neue AEM-Funktionen erforderliche Eigenentwicklung zurückgestellt werden.

**Legacy-Modus: Kompatibilitätspaket mit deaktiviertem Routing installiert** 

Der Legacy-Modus eignet sich für Kunden, die benutzerdefinierte Schnittstellen besitzen, die auf Legacy- oder veraltetem Code von AEM basieren, der in das Kompatibilitätspaket ausgelagert wurde.

![image2018-2-12_23-58-37](assets/image2018-2-12_23-58-37.png)

## Einrichtung {#how-to-set-up}

Das AEM 6.3-Kompatibilitätspaket kann mit Package Manager als Paket installiert werden. Sie können das [AEM 6.3 Kompatibilitätspaket von der Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/compatpack/aem-compat-cq64-to-cq63)-Site herunterladen.

Sobald das Kompatibilitätspaket installiert wurde, können Sie das Routing über einen Schalter in der OSGi-Konfiguration aktivieren oder deaktivieren:

![screen_shot_2017-11-27at122421pm](assets/screen_shot_2017-11-27at122421pm.png)

Sobald das Kompatibilitätspaket installiert und konfiguriert wurde, werden die Funktionen basierend auf dem ausgewählten Kompatibilitätsmodus verwendet.
