---
title: Komponenten, Funktionen und Funktionsgrundlagen
seo-title: Component, Function and Feature Essentials
description: Funktionsweise von Community-Sites, -Vorlagen und -Gruppen
seo-description: How community sites, templates, and groups function
uuid: 6edfca2d-fe5b-4261-b033-51dc2f9dbfd7
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 2d308756-79d1-4d69-b51c-d4b6e692a137
exl-id: bde29d3a-8bc8-4c30-b764-a2fa1ac34069
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 19%

---

# Komponenten, Funktionen und Funktionsgrundlagen {#component-function-and-feature-essentials}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

AEM Communities-Funktionen erfordern, dass Besucher der Site Mitglieder werden und sich bei der [Community-Site](overview.md#communitiessites) vor dem Posten von Inhalten. Daher [Community-Site-Vorlagen](sites.md), von der aus eine Community-Site [created](sites-console.md), die so konzipiert sind, dass sie eine Anmeldefunktion sowie Benutzerprofile, Messaging, Suche, Moderation und Übersetzung enthalten.

Auf einer Community-Site werden Mitglieder unterstützt, die Community-Gruppen erstellen, wenn die [Community-Gruppen-Funktion](functions.md#groups-function) ist in der ausgewählten Community-Site-Vorlage enthalten.

Im Folgenden finden Sie Links zu wichtigen Informationen zu Communities-Komponenten, -Funktionen und -Funktionen.

## Basiskomponenten {#base-components}

* [Kommentare](essentials-comments.md)
* [Bewertungen](reviews-basics.md)
* [Tally](tally.md)

   * [Likes](essentials-liking.md)
   * [Bewertung](rating-basics.md)
   * [Abstimmung](essentials-voting.md)
   * *Umfrage (nicht mehr verfügbar)*

## Komponenten mit Funktionen {#components-with-functions}

* [Aktivitäts-Streams](essentials-activities.md)
* [Zuweisungen](essentials-assignments.md)
* [Blog](blog-developer-basics.md) ( `Journal`)

* [Kalender](calendar-basics-for-developers.md)
* [Katalog](catalog-developer-essentials.md)
* [Präsentierter Inhalt](essentials-featured.md)
* [Dateibibliothek](essentials-file-library.md)
* [Forum](essentials-forum.md)
* [Gruppen](essentials-groups.md)
* [Ideen](ideation.md)
* [Leaderboard](leaderboard.md)
* [Fragen und Antworten](qna-essentials.md) `(QnA)`

## Funktionen {#features}

* [Client-Bibliotheken](clientlibs.md)
* [Community-Sites](sites-for-developers.md)
* [Komponenten-OSGi-Ereignisse](events.md)
* [Komponenten-Sideloading](sideloading.md)
* [Messaging](essentials-messaging.md)
* [Rich-Text-Editor](rte.md)
* [Scoring und Abzeichen](configure-scoring.md)
* [Suchen](search-implementation.md)
* [Soziales Diagramm](essentials-socialgraph.md)
* [Storage Resource Provider](srp-and-ugc.md) `(SRP)`

* [Tagging](tag.md)

## Javadocs {#javadocs}

Die [Online-Javadocs](../../help/sites-developing/reference-materials.md) spiegeln die in AEM Version 6.3 verfügbaren APIs wider.\
Communities-APIs befinden sich in `com.adobe.cq.social.*` Packages.

Für jeden [Feature Pack](deploy-communities.md#latestfeaturepack), wird eine JavaScript-JAR bereitgestellt. Weitere Informationen finden Sie unter [Verwenden von Maven für Communities](maven.md#javadocs).

## Zusätzliche Informationen {#additional-information}

* [Social Component Framework (SCF)](scf.md)

   * [Clientseitige Anpassungen](client-customize.md)
   * [Serverseitige Anpassungen](server-customize.md)
   * [Übersicht über den Speicheranbieter](srp.md)

* [Codierungsrichtlinien ](code-guide.md)
* [Tutorials](tutorials.md)
* [Fehlerbehebung](troubleshooting.md)
