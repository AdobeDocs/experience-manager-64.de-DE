---
title: SPA-Modell-Routing
seo-title: SPA Model Routing
description: Bei Single Page Applications in AEM ist die App für das Routing verantwortlich. In diesem Dokument werden der Routing-Mechanismus, der Vertrag und die verfügbaren Optionen beschrieben.
seo-description: For single page applications in AEM, the app is responsible for the routing. This document describes the routing mechanism, the contract, and options available.
uuid: 93b4f85a-a240-42d4-95e2-e8b790df7723
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: spa
content-type: reference
discoiquuid: d9f1e24e-51a9-4f28-b2cd-2e97aed63a24
exl-id: 865f524d-6b54-43c8-9b28-86a766e010a1
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 88%

---

# SPA-Modell-Routing{#spa-model-routing}

Bei Single Page Applications in AEM ist die App für das Routing verantwortlich. In diesem Dokument werden der Routing-Mechanismus, der Vertrag und die verfügbaren Optionen beschrieben.

>[!NOTE]
>
>Für die Funktion &quot;Single Page Application (SPA) Editor&quot;ist AEM Service Pack 2 (oder höher) 6.4 erforderlich.
>
>Der SPA Editor ist die empfohlene Lösung für Projekte, die SPA Framework-basiertes Client-seitiges Rendering erfordern (z. B. React oder Angular).

## Projekt-Routing {#project-routing}

Die App ist für das Routing verantwortlich und wird dann von den Frontend-Entwicklern des Projekts implementiert. In diesem Dokument wird das Routing für das vom AEM-Server zurückgegebene Modell beschrieben. Die Datenstruktur des Seitenmodells legt die URL der zugrunde liegenden Ressource offen. Das Frontend-Projekt kann eine benutzerdefinierte Bibliothek oder die Bibliothek eines Drittanbieters verwenden, die Routing-Funktionen bereitstellt. Sobald eine Route ein Modellfragment erwartet, kann die `PageModelManager.getData()`-Funktion aufgerufen werden. Wenn sich eine Modellroute geändert hat, muss ein Ereignis ausgelöst werden, um überwachende Bibliotheken wie den Seiteneditor zu warnen.

## Architektur {#architecture}

Eine ausführliche Beschreibung finden Sie im Abschnitt [PageModelManager](/help/sites-developing/spa-blueprint.md#pagemodelmanager) im SPA-Blueprint-Dokument.

## ModelRouter {#modelrouter}

`ModelRouter` – sofern aktiviert – kapselt die HTML5 History-API-Funktionen `pushState` und `replaceState`, um sicherzustellen, dass ein bestimmtes Modellfragment vorab abgerufen und zugänglich ist. Anschließend benachrichtigt er die registrierte Frontend-Komponente, dass das Modell geändert wurde.

## Vergleich von manuellem und automatischem Routing {#manual-vs-automatic-model-routing}

`ModelRouter` automatisiert das Abrufen von Modellfragmenten. Aber wie jedes automatisierte Tool ist es mit Einschränkungen verbunden. Bei Bedarf kann `ModelRouter` deaktiviert oder so konfiguriert werden, dass Pfade mit Meta-Eigenschaften ignoriert werden (siehe Abschnitt „Meta-Eigenschaften“ im Dokument [SPA-Seitenkomponente](/help/sites-developing/spa-page-component.md)). Frontend-Entwickler können dann ihre eigene Modell-Routing-Schicht implementieren, indem sie `PageModelManager` auffordern, ein bestimmtes Modellfragment mithilfe der `getData()`-Funktion zu laden.

>[!NOTE]
>
>Derzeit veranschaulicht das Beispiel-React-Projekt &quot;We.Retail Journal&quot;den automatisierten Ansatz, während das Angular-Projekt das manuelle Projekt veranschaulicht. Ein halbautomatisierter Ansatz wäre auch ein gültiger Anwendungsfall.

>[!CAUTION]
>
>Die aktuelle Version von `ModelRouter` unterstützt nur die Verwendung von URLs, die auf den tatsächlichen Ressourcenpfad der Einstiegspunkte des Sling-Modells verweisen. Die Verwendung von Vanity-URLs oder Aliasnamen wird nicht unterstützt.

## Routing-Vertrag {#routing-contract}

Die aktuelle Implementierung basiert auf der Annahme, dass das SPA-Projekt die HTML5 History-API für das Routing zu den verschiedenen Anwendungsseiten verwendet.

### Konfiguration {#configuration}

`ModelRouter` unterstützt das Konzept des Modell-Routings, da es auf `pushState`- und `replaceState`-Aufrufe wartet, um Modellfragmente vorab abzurufen. Intern triggert es den `PageModelManager`, das Modell zu laden, das einer bestimmten URL entspricht, und löst ein `cq-pagemodel-route-changed`-Ereignis aus, das andere Module überwachen können.

Standardmäßig ist dieses Verhalten automatisch aktiviert. Um es zu deaktivieren, sollte die SPA die folgende Meta-Eigenschaft rendern:

```
<meta property="cq:pagemodel_router" content="disable"\>
```

Beachten Sie, das jede Route der SPA einer vorhandenen Seite in AEM entsprechen sollte (z. B. `/content/mysite/mypage"`), da der `PageModelManager` automatisch versucht, das entsprechende Seitenmodell zu laden, wenn die Route ausgewählt wird. Bei Bedarf kann die SPA jedoch auch eine Blockierungsliste mit Routen definieren, die der `PageModelManager` ignorieren soll:

```
<meta property="cq:pagemodel_route_filters" content="route/not/found,^(.*)(?:exclude/path)(.*)"/>
```
