---
title: Suchfunktion
seo-title: Suchfunktion
description: Hinzufügen und Konfigurieren der Suche zu einer Communities-Site
seo-description: Hinzufügen und Konfigurieren der Suche zu einer Communities-Site
uuid: ca633456-911f-447f-881e-653533125d5f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 3acac082-efbe-4995-b374-851cb9aaf62d
exl-id: 15d8bd59-397e-4bd3-b0a2-b6893c015798
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 29%

---

# Suchfunktion {#search-feature}

Die Suchfunktion kann für zahlreiche andere Funktionen wie beispielsweise Foren eingesetzt werden und bietet somit die Möglichkeit, bestimmte Inhalte aufzufinden.

Beim Hinzufügen der Möglichkeit, Beiträge von Community-Mitgliedern zu durchsuchen, die als benutzergenerierte Inhalte (UGC) bezeichnet werden, gibt es zwei Komponenten: [ `Search`](#search-features) und [ `Search Results`](#search-results)

Die Seite, die die Komponente `Search Results` enthält, unterstützt sowohl die Suche als auch die Anzeige der Ergebnisse.

Die Seite, die die Komponente `Search`enthält, bietet einen Ort zum Starten einer Suche mit Ergebnissen, die auf der Seite `Search Results` angezeigt werden.

Die Suchfunktion kann gemeinsam mit anderen Funktionen verwendet werden, sodass Site-Besucher und Mitglieder in der Lage sind, Inhalte einzusehen.

## Suche {#search-features}

### Hinzufügen einer Suche zu einer Seite {#add-search-to-a-page}

Um eine Komponente `Search` im Autorenmodus zu einer Seite hinzuzufügen, suchen Sie im Komponenten-Browser nach `Communities / Search` und ziehen Sie sie an die gewünschte Stelle auf einer Seite. Für die Verwendung von `Search` ist eine zweite Seite für `Search Results.` erforderlich.

Die erforderlichen Informationen finden Sie unter [Grundlagen der Communities-Komponenten](basics.md).

Wenn die erforderliche clientseitige Bibliothek `cq.social.hbs.search` eingeschlossen ist, wird die Komponente `Search` so angezeigt.

![chlimage_1-373](assets/chlimage_1-373.png)

### Konfigurieren der hinzugefügten Suche {#configure-the-added-search}

Wählen Sie die platzierte Komponente `Search` aus, um auf das Symbol `Configure` zuzugreifen, mit dem das Bearbeitungsdialogfeld geöffnet wird.

![chlimage_1-374](assets/chlimage_1-374.png)

Geben Sie auf der Registerkarte **[!UICONTROL Sucheinstellungen]** an, welche Pfade gesucht werden sollen, wenn ein Besucher eine Abfrage eingibt.

![chlimage_1-375](assets/chlimage_1-375.png)

* **[!UICONTROL Suchpfade]** Durch Hinzufügen von Suchpfaden mithilfe der Schaltfläche „Element hinzufügen“ wird die Elementsuche eingeschränkt. Um beispielsweise die Suche auf ein bestimmtes Forum zu beschränken, wählen Sie eine Forumskomponente aus, die auf einer Seite platziert wird:

   * `/content/community-components/en/forum/jcr:content/content/forum`

* **[!UICONTROL Result]**
PageDie Ergebnisse werden auf einer separaten Seite angezeigt, die mithilfe des Browsers angegeben wird, um eine Seite auszuwählen, die die 
`Search Results` component.

## Search Results {#search-results}

### Hinzufügen von Suchergebnissen zu einer Seite {#add-search-results-to-a-page}

Um eine Komponente `Search Results` im Autorenmodus zu einer Seite hinzuzufügen, suchen Sie mit dem Komponenten-Browser nach

* `Communities / Search Results`

und ziehen Sie die Komponente an die gewünschte Stelle auf der Seite. Im Gegensatz zur Komponente „Suche“ wird hier keine zweite Seite benötigt, da die Suchergebnisse auf der gleichen Seite angezeigt werden können.

Wenn Sie die Suche an einer anderen Stelle auf der Website verwenden, kann diese eine Seite mit `Search Results` so konfiguriert werden, dass sie `Result Page` für alle Instanzen von `Search` ist.

Die erforderlichen Informationen finden Sie unter [Grundlagen der Communities-Komponenten](basics.md).

Wenn die erforderliche clientseitige Bibliothek `cq.social.hbs.search` eingeschlossen ist, wird die Komponente `Search Result` so angezeigt:

![chlimage_1-376](assets/chlimage_1-376.png)

### Konfigurieren hinzugefügter Suchergebnisse {#configure-the-added-search-result}

Wählen Sie die platzierte Komponente `Search Results` aus, um auf das Symbol `Configure` zuzugreifen, mit dem das Bearbeitungsdialogfeld geöffnet wird.

![chlimage_1-377](assets/chlimage_1-377.png)

Auf der Registerkarte **[!UICONTROL Suchergebniseinstellungen]** können Sie angeben, welche Pfade bei der Suche berücksichtigt werden, wenn ein Besucher eine Abfrage eingibt.

![chlimage_1-378](assets/chlimage_1-378.png)

* **[!UICONTROL Suchergebnisse pro]**
SeiteDefinieren Sie die Anzahl der Themen/Beiträge, die pro Seite angezeigt werden. Der Standardwert ist 10.

* **[!UICONTROL Suchpfade]** Durch Hinzufügen von Suchpfaden mithilfe der Schaltfläche „Element hinzufügen“ wird die Elementsuche eingeschränkt.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Seite [Suchgrundlagen](search-implementation.md) für Entwickler.
