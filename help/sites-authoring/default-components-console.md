---
title: Komponentenkonsole
seo-title: Components Console
description: Komponentenkonsole
seo-description: null
uuid: 308b7fa1-9525-43f3-8c15-1076485b3f8c
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 8774c38a-abd2-4dc2-868e-d6760c96f3f6
exl-id: fa583a06-e75c-41de-a977-7e459ab8bca9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 53%

---

# Komponentenkonsole{#components-console}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Mit der Komponentenkonsole können Sie alle für Ihre Instanz definierten Komponenten durchsuchen und wichtige Informationen zu den einzelnen Komponenten anzeigen.

Der Zugriff erfolgt über **Instrumente** -> **Allgemein** -> **Komponenten**. In der Konsole sind Karten- und Listenansicht verfügbar. Da es keine Baumstruktur für Komponenten gibt, ist die Spaltenansicht nicht verfügbar.

![chlimage_1-301](assets/chlimage_1-301.png)

>[!NOTE]
>
>In der Komponentenkonsole werden alle im System vorhandenen Komponenten angezeigt. Im [Komponenten-Browser](/help/sites-authoring/author-environment-tools.md#components-browser) werden Komponenten angezeigt, die Autoren zur Verfügung stehen, und alle Komponentengruppen verborgen, die mit einem Punkt beginnen (`.`).

## Suchen {#search-features}

Mit dem Symbol **Nur Inhalt** (oben links) können Sie den **Suchbereich** öffnen, um die Komponenten zu durchsuchen und/oder zu filtern:

![chlimage_1-302](assets/chlimage_1-302.png)

## Komponentendetails {#component-details}

Um Details zu einer bestimmten Komponente anzuzeigen, tippen/klicken Sie auf die gewünschte Ressource. Drei Registerkarten bieten:

* **Eigenschaften**

   ![screen_shot_2018-03-27at165847](assets/screen_shot_2018-03-27at165847.png)

   In der Registerkarte „Eigenschaften“ haben Sie folgende Möglichkeiten:

   * Ansehen der allgemeinen Eigenschaften der Komponente
   * Anzeigen der [Symbol oder Abkürzung wurde definiert](/help/sites-developing/components-basics.md#component-icon-in-touch-ui) für die Komponente.

      * Durch Klicken auf die Quelle des Symbols gelangen Sie zu dieser Komponente.
   * Anzeigen der **Ressourcentyp** und **Resource Super Type** (sofern definiert) für die Komponente.

      * Wenn Sie auf den Ressourcen-Supertyp klicken, gelangen Sie zu dieser Komponente.
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

   Wenn der Entwickler [Dokumentation für die Komponente](/help/sites-developing/developing-components.md#documenting-your-component), wird sie im **Dokumentation** Registerkarte. Ist keine Dokumentation verfügbar, wird die Registerkarte **Dokumentation** nicht angezeigt.

   ![chlimage_1-305](assets/chlimage_1-305.png)
