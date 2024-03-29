---
title: Zuordnung dynamischer Modelle zu Komponenten für SPAs
seo-title: Dynamic Model to Component Mapping for SPAs
description: In diesem Artikel wird beschrieben, wie die Zuordnung des dynamischen Modells zu Komponenten im JavaScript SPA SDK für AEM erfolgt.
seo-description: This article describes how the dynamic model to component mapping occurs in the Javascript SPA SDK for AEM.
uuid: 337b8d90-efd7-442e-9fac-66c33cc26212
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: spa
content-type: reference
discoiquuid: 8b4b0afc-8534-4010-8f34-cb10475a8e79
exl-id: 2bbbfbaa-b0a1-4f8a-9445-51325d80e368
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 89%

---

# Zuordnung dynamischer Modelle zu Komponenten für SPAs{#dynamic-model-to-component-mapping-for-spas}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

In diesem Dokument wird beschrieben, wie die Zuordnung des dynamischen Modells zu Komponenten im JavaScript SPA SDK für AEM erfolgt.

>[!NOTE]
>Für die Funktion &quot;Single Page Application (SPA) Editor&quot;ist AEM Service Pack 2 (oder höher) 6.4 erforderlich.
>
>Der SPA-Editor ist die empfohlene Lösung für Projekte, bei denen Client-seitiges Rendering auf Basis eines SPA-Frameworks (z. B. React oder Angular) erforderlich ist.

## ComponentMapping-Modul {#componentmapping-module}

Das `ComponentMapping`-Modul wird dem Frontend-Projekt als NPM-Paket bereitgestellt. Es speichert Frontend-Komponenten und bietet der Single Page Application die Möglichkeit, Frontend-Komponenten AEM-Ressourcentypen zuzuordnen. Dies ermöglicht beim Parsen des JSON-Modells des Programms eine dynamische Auflösung von Komponenten.

Alle im Modell vorhandenen Elemente enthalten ein Feld `:type`, das einen AEM-Ressourcentyp verfügbar macht. Bei der Implementierung kann sich die Frontend-Komponente mit dem Fragment des Modells, das sie von den zugrunde liegenden Bibliotheken erhalten hat, selbst rendern.

Weitere Informationen zum Parsen von Modellen und zum Zugriff der Frontend-Komponenten auf das Modell finden Sie im Dokument [SPA-Blueprint](/help/sites-developing/spa-blueprint.md).

Weitere Informationen finden Sie im npm-Paket: [https://www.npmjs.com/package/@adobe/aem-spa-component-mapping](https://www.npmjs.com/package/@adobe/aem-spa-component-mapping)

## Modellgesteuerte Single Page Application {#model-driven-single-page-application}

Single Page Applications, die das JavaScript SPA SDK für AEM nutzen, sind modellgesteuert:

1. Frontend-Komponenten registrieren sich im [Komponentenzuordnungs-Store](/help/sites-developing/spa-dynamic-model-to-component-mapping.md#componentmapping-module).
1. Anschließend durchläuft der [Container](/help/sites-developing/spa-blueprint.md#container), sobald ihm ein Modell vom [Modellanbieter](/help/sites-developing/spa-blueprint.md#the-model-provider) zur Verfügung gestellt wurde, seinen Modellinhalt ( `:items`).

1. Im Fall einer Seite erhalten die untergeordneten Elemente (`:children`) zunächst eine Komponentenklasse aus der [Komponentenzuordnung](/help/sites-developing/spa-blueprint.md#componentmapping) und instanziieren sie dann.

## App-Initialisierung {#app-initialization}

Jede Komponente wird um die Funktionen von [`ModelProvider`](/help/sites-developing/spa-blueprint.md#the-model-provider) erweitert. Die Initialisierung hat daher die folgende allgemeine Form:

1. Jeder Modellanbieter initialisiert sich selbst und wartet auf Änderungen, die an dem Modell vorgenommen wurden, das seiner inneren Komponente entspricht.
1. [`PageModelManager`](/help/sites-developing/spa-blueprint.md#pagemodelmanager) muss gemäß dem [Initialisierungsfluss](/help/sites-developing/spa-blueprint.md) initialisiert werden.

1. Nach dem Speichern gibt der Seitenmodell-Manager das vollständige Modell der App zurück.
1. Dieses Modell wird dann an die Frontend-Stamm-[Container](/help/sites-developing/spa-blueprint.md#container)-Komponente der App übergeben.
1. Teile des Modells werden schließlich auf jede einzelne untergeordnete Komponente übertragen.

![app_model_initialization](assets/app_model_initialization.png)
