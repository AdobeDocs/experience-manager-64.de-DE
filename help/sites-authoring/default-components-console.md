---
title: Komponentenkonsole
seo-title: Komponentenkonsole
description: Komponentenkonsole
seo-description: 'null'
uuid: 308b7fa1-9525-43f3-8c15-1076485b3f8c
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 8774c38a-abd2-4dc2-868e-d6760c96f3f6
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 95%

---


# Komponentenkonsole{#components-console}

Die Komponentenkonsole ermöglicht es Ihnen, alle Komponenten zu durchsuchen, die für Ihre Instanz definiert sind, und wichtige Informationen für jede Komponente anzuzeigen. 

Sie können von **Tools** -> **Allgemein** -> **Komponenten** aus aufgerufen werden. In der Konsole sind Karten- und Listenansicht verfügbar. Da es keine Baumstruktur für Komponenten gibt, ist die Spaltenansicht nicht verfügbar.

![chlimage_1-301](assets/chlimage_1-301.png)

>[!NOTE]
>
>In der Komponentenkonsole werden alle im System vorhandenen Komponenten angezeigt. Im [Komponenten-Browser](/help/sites-authoring/author-environment-tools.md#components-browser) werden Komponenten angezeigt, die Autoren zur Verfügung stehen, und alle Komponentengruppen verborgen, die mit einem Punkt beginnen (`.`).

## Suche {#search-features}

Mit dem Symbol **Nur Inhalt** (oben links) können Sie den **Suchbereich** öffnen, um die Komponenten zu durchsuchen und/oder zu filtern: 

![chlimage_1-302](assets/chlimage_1-302.png)

## Komponentendetails {#component-details}

Um weitere Einzelheiten zu einer bestimmten Komponente anzuzeigen, tippen/klicken Sie auf die gewünschte Ressource. Die drei Registerkarten bieten:

* **Eigenschaften**

   ![screen_shot_2018-03-27at165847](assets/screen_shot_2018-03-27at165847.png)

   In der Registerkarte „Eigenschaften“ haben Sie folgende Möglichkeiten:

   * Ansehen der allgemeinen Eigenschaften der Komponente
   * Ansehen, wie das [Symbol oder die Abkürzung für die Komponente definiert wurde](/help/sites-developing/components-basics.md#component-icon-in-touch-ui)

      * Durch Klicken auf die Symbolquelle gelangen Sie zu dieser Komponente.
   * Ansehen des **Ressourcentyps** und des **Ressourcen-Supertyps** (sofern definiert) für die Komponente

      * Durch Klicken auf den Ressourcen-Supertyp gelangen Sie zu dieser Komponente.
   >[!NOTE]
   >
   >Da `/apps` zur Laufzeit nicht bearbeitet werden kann, ist die Komponentenkonsole schreibgeschützt.

* **Richtlinien**

   ![chlimage_1-303](assets/chlimage_1-303.png)

* **Live-Nutzung**

   ![chlimage_1-304](assets/chlimage_1-304.png)

   >[!CAUTION]
   >
   >Aufgrund der Art der Informationen, die für diese Ansicht erfasst werden, kann es eine Weile dauern, bis sie zusammengestellt/angezeigt wird. 

* **Dokumentation**

   Etwaige vom Entwickler [für eine Komponente bereitgestellte Dokumentation](/help/sites-developing/developing-components.md#documenting-your-component) wird auf der Registerkarte **Dokumentation** angezeigt. Ist keine Dokumentation verfügbar, wird die Registerkarte **Dokumentation** nicht angezeigt.

   ![chlimage_1-305](assets/chlimage_1-305.png)

