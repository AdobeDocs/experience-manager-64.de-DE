---
title: Zugreifen auf UGC mit SRP
seo-title: Accessing UGC with SRP
description: Wenn eine Site für die Verwendung von ASRP oder MSRP konfiguriert ist, wird die tatsächliche UGC nicht in AEM Knotenspeicher (JCR) gespeichert
seo-description: When a site is configured to use ASRP or MSRP, the actual UGC is not be stored in AEM's node store (JCR)
uuid: 5f9f8c9b-4c6a-45b0-96ff-14934380eba7
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: ee786a5c-b985-4d78-9063-6c79ae5e13e6
exl-id: 3a16a771-e1c5-4ae4-9fc6-17a47064db54
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# Zugreifen auf UGC mit SRP {#accessing-ugc-with-srp}

## Über SRP {#about-srp}

Alle AEM Communities-Komponenten und -Funktionen basieren auf dem [Social Component Framework (SCF)](scf.md), der die SocialResourceProvider-API aufruft, um auf alle benutzergenerierten Inhalte zuzugreifen.

Bevor eine Community-Site erstellt wird, muss die [Storage Resource Provider (SRP)](working-with-srp.md) muss so konfiguriert sein, dass eine Implementierung ausgewählt wird, die mit der zugrunde liegenden [Topologie](topologies.md). Die SRP-Implementierungen basieren auf drei Speicheroptionen:

1. [ASRP](asrp.md) - Adobe der On-Demand-Speicherung
2. [MSRP](msrp.md) - MongoDB
3. [JSRP](jsrp.md) - JCR

## Über UGC-Speicher {#about-ugc-storage}

Wichtig ist, dass Sie über die Speicherung von UGC wissen, dass die tatsächliche UGC nicht in gespeichert wird, wenn eine Site für die Verwendung von ASRP oder MSRP konfiguriert istAEM [Knotenspeicher](../../help/sites-deploying/data-store-config.md) (JCR).

Es kann zwar Knoten in JCR geben, die die UGC daran erinnern, nützliche Metadaten bereitzustellen, diese Knoten sind jedoch nicht mit der tatsächlichen UGC zu verwechseln.

Siehe [Übersicht über den Speicheranbieter.](srp.md)

## Best Practice {#best-practice}

Bei der Entwicklung benutzerdefinierter Komponenten sollten Entwickler darauf achten, unabhängig von der aktuell ausgewählten Topologie zu programmieren, und so flexibel bleiben, um in Zukunft zu einer neuen Topologie zu wechseln.

### Angenommen, JCR ist nicht verfügbar {#assume-jcr-not-available}

JCR-spezifische Methoden sollten vermieden werden.

Zu verwendende Methoden:

* Sling-API (Sling-Ressource)
   * Es wird nicht davon ausgegangen, dass JCR-Knoten vorhanden sind

* OSGi-Ereignisse
   * Angenommen, es gibt JCR-Ereignisse

* [Social Resource Utilities](socialutils.md#socialresourceutilities-package)
* [SCF Utilities](socialutils.md#scfutilities-package)

Methoden zur Vermeidung von:

* Knoten-API
* JCR-Ereignisse
* Workflow-Starter (die JCR-Ereignisse verwenden)

### Verwenden von Suchkollektionen {#use-search-collections}

Verschiedene SRPs können unterschiedliche native Abfragesprachen haben. Es wird empfohlen, Methoden aus dem [com.adobe.cq.social.ugc.api](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/ugc/api/package-summary.html) -Paket, um die entsprechende Abfragesprache aufzurufen.

Weitere Informationen finden Sie unter [Suchgrundlagen](search-implementation.md).

## Ressourcen {#resources}

* [Community-Inhaltsspeicherung](working-with-srp.md) - beschreibt die verfügbaren SRP-Optionen für einen UGC Common Store
* [Übersicht über den Speicheranbieter](srp.md) - Einführung und Übersicht über die Repository-Nutzung
* [Grundlagen zu SRP und UGC](srp-and-ugc.md) - SRP-Anwendungsmethoden und -Beispiele
* [Suchgrundlagen](search-implementation.md) - wesentliche Informationen für die Suche nach UGC
* [SocialUtils-Refaktorierung](socialutils.md) - Zuordnung veralteter Methoden von Dienstprogrammen zu aktuellen Methoden des SRP-Dienstprogramms
