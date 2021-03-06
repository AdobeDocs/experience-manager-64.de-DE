---
title: Testen von Inhaltsfragmenten in We.Retail
seo-title: Trying out Content Fragments in We.Retail
description: Testen von Inhaltsfragmenten in We.Retail
seo-description: null
uuid: 66daddfe-8e98-47b6-8499-db055887ac17
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: d1326737-f378-46d0-9916-61ead4d31639
exl-id: d93bec03-c651-4329-b220-4ac1ea189de1
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 79%

---

# Testen von Inhaltsfragmenten in We.Retail{#trying-out-content-fragments-in-we-retail}

Inhaltsfragmente ermöglichen es Ihnen, kanalneutrale Inhalte zusammen mit (möglicherweise kanalspezifischen) Varianten zu erstellen. **We.Retail** (wie in einer vordefinierten Instanz von AEM verfügbar) stellt das Fragment bereit **Arktisches Surfen in Lofoten** als Grundmuster. Dies verdeutlicht:

* Content Fragments für Adobe Experience Manager (AEM) werden [als seitenunabhängige Assets erstellt und verwaltet](/help/assets/content-fragments.md). Sie ermöglichen es Ihnen, kanalneutrale Inhalte zusammen mit (möglicherweise kanalspezifischen) Varianten zu erstellen.

   * Siehe [Suchen nach Inhaltsfragment-Assets in We.Retail](#where-to-find-content-fragments-in-we-retail)

* Sie können [diese Fragmente und ihre Varianten bei der Erstellung Ihrer Inhaltsseiten](/help/sites-authoring/content-fragments.md) verwenden.

   * Siehe [wo Inhaltsfragmente in We.Retail verwendet werden](#where-content-fragments-are-used-in-we-retail)

Die vollständige Dokumentation zum Erstellen, Verwalten, Nutzen und Entwickeln von Inhaltsfragmenten:

* Siehe [Weitere Informationen](#further-information)

>[!NOTE]
>
>**Inhaltsfragmente** und **[Experience Fragments](/help/sites-authoring/experience-fragments.md)** sind unterschiedliche Funktionen in AEM:
>
>* **Inhaltsfragmente** sind redaktionelle Inhalte, vor allem Text und zugehörige Bilder. Dabei handelt es sich um reinen Inhalt ohne Design und Layout.
>* **Experience Fragments** sind vollständig gestaltete Inhalte und stellen Teile von Web-Seiten dar.

>
>Experience Fragments können Inhalte in Form von Inhaltsfragmenten enthalten, aber nicht umgekehrt.

## Suche nach Inhaltsfragment-Assets in We.Retail {#where-to-find-content-fragments-in-we-retail}

Es gibt mehrere Beispielinhaltsfragmente in We.Retail. über navigieren **Assets**, **Dateien**, **We.Retail**, **englisch**, **Erlebnisse**.

Diese enthalten **Arktisches Surfen in Lofoten**, ein Fragment zusammen mit dazu gehörenden visuellen Assets:

* Navigieren über **Assets**, **Dateien**, **We.Retail**, **englisch**, **Erlebnisse**, **Artisches Surfen in Lofoten**:

   * [http://localhost:4502/assets.html/content/dam/we-retail/en/experiences/arctic-surfing-in-lofoten](http://localhost:4502/assets.html/content/dam/we-retail/en/experiences/arctic-surfing-in-lofoten ) 

![cf-44](assets/cf-44.png)

Sie können das Fragment **Arktisches Surfen in Lofoten** auswählen und bearbeiten:

* [http://localhost:4502/editor.html/content/dam/we-retail/en/experiences/arctic-surfing-in-lofoten/arctic-surfing-in-lofoten](http://localhost:4502/editor.html/content/dam/we-retail/en/experiences/arctic-surfing-in-lofoten/arctic-surfing-in-lofoten)

Hier können Sie Ihr Fragment anhand der Registerkarten (linkes Bedienfeld) [bearbeiten und verwalten](/help/assets/content-fragments.md):

![](do-not-localize/cf-45-aa.png) ![](do-not-localize/cf-45-a.png)

* **[Variationen](/help/assets/content-fragments-variations.md)** einschließlich [Markdown](/help/assets/content-fragments-markdown.md)

* **[Zugehörige Inhalte](/help/assets/content-fragments-assoc-content.md)**
* **[Metadaten](/help/assets/content-fragments-metadata.md)**

![cf-46](assets/cf-46.png)

## Verwendung von Inhaltsfragmenten in We.Retail {#where-content-fragments-are-used-in-we-retail}

Unter folgendem Link finden Sie mehrere Beispiele zum Veranschaulichen der [Seitenerstellung mit einem Inhaltsfragment](/help/sites-authoring/content-fragments.md):

* [http://localhost:4502/sites.html/content/we-retail/language-masters/en/experience](http://localhost:4502/sites.html/content/we-retail/language-masters/en/experience)

Beispiel: die **Arktisches Surfen in Lofoten** Inhaltsfragment wird auf der Seite Sites referenziert:

* Navigieren über **Sites**, **We.Retail**, **Sprach-Master**, **englisch**, **Erlebnis**. Öffnen Sie dann **Arktisches Surfen in Lofoten** zur Bearbeitung:

   * [http://localhost:4502/editor.html/content/we-retail/language-masters/en/experience/arctic-surfing-in-lofoten.html](http://localhost:4502/editor.html/content/we-retail/language-masters/en/experience/arctic-surfing-in-lofoten.html)

![cf-53](assets/cf-53.png)

## Weiterführende Informationen {#further-information}

Weitere Informationen finden Sie unter:

* [Arbeiten mit Inhaltsfragmenten](/help/assets/content-fragments.md)

   * Hier erfahren Sie, wie Sie Ihre Inhaltsfragment-Assets erstellen, bearbeiten und verwalten.

* [Seitenbearbeitung mit Inhaltsfragmenten](/help/sites-authoring/content-fragments.md)

   * Verwenden Sie Ihr Inhaltsfragment beim Erstellen einer Seite.

* [Entwickeln von AEM-Komponenten für Inhaltsfragmente](/help/sites-developing/components-content-fragments.md)

   * Ein Überblick über die Komponenten für Inhaltsfragmente.

* [Entwickeln und Erweitern von Inhaltsfragmenten](/help/sites-developing/customizing-content-fragments.md)

   * Informationen, mit deren Hilfe Sie Inhaltsfragmente entwickeln und erweitern können.
