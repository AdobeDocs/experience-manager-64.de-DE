---
title: Abwärtskompatibilität in AEM 6.4
seo-title: Backward Compatibility in AEM 6.4
description: Erfahren Sie, wie Sie Ihre Apps und Konfigurationen mit AEM 6.4 kompatibel machen.
seo-description: Learn how to keep your apps and configurations compatible with AEM 6.4
uuid: 2fa8525e-7f3b-4096-ac85-01c2c76bc9ac
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: upgrading
content-type: reference
discoiquuid: 5e76fe09-4d37-4c8c-8baf-97e75689bd26
feature: Upgrading
exl-id: 5798100a-e03a-43f8-9189-ae51c06e192b
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 76%

---

# Abwärtskompatibilität in AEM 6.4{#backward-compatibility-in-aem}

## Übersicht {#overview}

>[!NOTE]
>
>Eine Liste der Inhalts- und Konfigurationsänderungen, die nicht unter das Kompatibilitätspaket fallen, finden Sie unter [Repository-Neustrukturierung in AEM 6.4](/help/sites-deploying/repository-restructuring.md).

In AEM 6.4 wurden alle Funktionen mit Rückwärtskompatibilität entwickelt.

In den meisten Fällen sollten Kunden, die mit AEM 6.3 arbeiten, weder ihren Code noch ihre Anpassungen ändern müssen, wenn sie die Aktualisierung durchführen. Für Kunden von AEM 6.1 und 6.2 gibt es keine zusätzlichen Änderungen, die grundlegend sind, als dies bei einem Upgrade auf 6.3 der Fall wäre.

Für die Ausnahmen, in denen Funktionen nicht abwärtskompatibel realisiert werden konnten, kann die Abwärtskompatibilität für Bundles und Inhalte erzielt werden, indem ein Kompatibilitätspaket für 6.3 installiert wird (im Folgenden finden Sie weitere Informationen und erfahren, wo Sie das Paket herunterladen können). Dieses Kompatibilitätspaket stellt die Kompatibilität für Anwendungen wieder her, die mit AEM 6.3 kompatibel sind.

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

Das AEM 6.3-Kompatibilitätspaket kann mit Package Manager als Paket installiert werden. Sie können die [AEM 6.3-Kompatibilitätspaket von der Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/compatpack/aem-compat-cq64-to-cq63) Site.

Sobald das Kompatibilitätspaket installiert wurde, können Sie das Routing über einen Schalter in der OSGi-Konfiguration aktivieren oder deaktivieren:

![screen_shot_2017-11-27at122421pm](assets/screen_shot_2017-11-27at122421pm.png)

Sobald das Kompatibilitätspaket installiert und konfiguriert wurde, werden die Funktionen basierend auf dem ausgewählten Kompatibilitätsmodus verwendet.
