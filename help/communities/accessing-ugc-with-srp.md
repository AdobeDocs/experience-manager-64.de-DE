---
title: Zugriff auf UGC mit SRP
seo-title: Zugriff auf UGC mit SRP
description: Wenn eine Site für die Verwendung von ASRP oder MSRP konfiguriert ist, wird die tatsächliche UGC nicht im AEM-Node Store (JCR) gespeichert
seo-description: Wenn eine Site für die Verwendung von ASRP oder MSRP konfiguriert ist, wird die tatsächliche UGC nicht im AEM-Node Store (JCR) gespeichert
uuid: 5f9f8c9b-4c6a-45b0-96ff-14934380eba7
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: ee786a5c-b985-4d78-9063-6c79ae5e13e6
translation-type: tm+mt
source-git-commit: 565604feff7fa365a1c6b52b62a0b0eb681bb192

---


# Zugriff auf UGC mit SRP {#accessing-ugc-with-srp}

## Informationen zu SRP {#about-srp}

Alle Komponenten und Funktionen von AEM Communities basieren auf dem [Social-Komponenten-Framework (SCF)](scf.md), das die SocialResourceProvider-API aufruft, um auf alle benutzergenerierten Inhalte zuzugreifen.

Bevor eine Community-Site erstellt wird, muss der [Speicher-Ressourcenanbieter (SRP)](working-with-srp.md) so konfiguriert sein, dass eine Implementierung ausgewählt wird, die mit der zugrunde liegenden [Topologie](topologies.md)übereinstimmt. Die SRP-Implementierungen basieren auf drei Speicheroptionen:

1. [ASRP](asrp.md) - On-Demand-Speicher von Adobe
2. [MSRP](msrp.md) - MongoDB
3. [JSRP](jsrp.md) - JCR

## Über UGC-Speicher {#about-ugc-storage}

Wichtig beim Speichern von UGC ist, dass, wenn eine Site für die Verwendung von ASRP oder MSRP konfiguriert ist, die eigentliche UGC nicht im AEM- [Node Store](../../help/sites-deploying/data-store-config.md) (JCR) gespeichert wird.

Es gibt zwar Knoten in JCR, die den UGC zur Bereitstellung nützlicher Metadaten schatten, diese Knoten sind jedoch nicht mit dem tatsächlichen UGC zu verwechseln.

Siehe Übersicht über den [Storage Resource Provider.](srp.md)

## Best Practice {#best-practice}

Bei der Entwicklung benutzerdefinierter Komponenten sollten Entwickler darauf achten, dass sie unabhängig von der aktuell gewählten Topologie kodieren, um in Zukunft flexibel zu einer neuen Topologie zu wechseln.

### Angenommen, JCR ist nicht verfügbar {#assume-jcr-not-available}

JCR-spezifische Methoden sollten vermieden werden.

Zu verwendende Methoden:

* Sling API (Sling Resource)
   * Gehen Sie nicht davon aus, dass JCR-Knoten vorhanden sind

* OSGi-Ereignisse
   * Gehen Sie nicht davon aus, dass JCR-Ereignisse vorhanden sind

* [Social Resource Utilities](socialutils.md#socialresourceutilities-package)
* [SCF Utilities](socialutils.md#scfutilities-package)

Methoden zur Vermeidung:

* Knoten-API
* JCR-Ereignisse
* Workflow-Starter (die JCR-Ereignisse verwenden)

### Suchsammlungen verwenden {#use-search-collections}

Verschiedene SRPs können unterschiedliche native Abfragesprachen haben. Es wird empfohlen, Methoden aus dem [Paket com.adobe.cq.social.ugc.api](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/ugc/api/package-summary.html) zu verwenden, um die entsprechende Abfragesprache aufzurufen.

For more information, see [Search Essentials](search-implementation.md).

## Ressourcen {#resources}

* [Community Content Storage](working-with-srp.md) - Diskussion der verfügbaren SRP-Optionen für einen gemeinsamen UGC-Speicher
* [Übersicht über](srp.md) den Speicherressourcen-Provider - Einführung und Übersicht über die Repository-Nutzung
* [SRP und UGC Essentials](srp-and-ugc.md) - SRP-Dienstprogrammmethoden und Beispiele
* [Essentials](search-implementation.md) suchen - wesentliche Informationen für die Suche nach UGC
* [SocialUtils Refactoring](socialutils.md) - Zuordnen veralteter Dienstprogrammmethoden zu aktuellen SRP-Dienstprogrammmethoden
