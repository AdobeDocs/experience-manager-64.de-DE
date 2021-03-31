---
title: Optimierte Sortierung von Assets in AEM
description: Erfahren Sie, wie AEM Assets mit der serverseitigen Sortierung Ordner-Assets oder Suchanfragen in einem Durchgang sortiert, anstatt sie in Batches auf Clientseite zu verarbeiten.
contentOwner: AG
feature: Suchen
role: Geschäftspraktiker
translation-type: tm+mt
source-git-commit: 4acf159ae1b9923a9c93fa15faa38c7f4bc9f759
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 93%

---


# Optimierte Sortierung von Assets in AEM {#enhanced-sorting-of-assets-in-aem}

Erfahren Sie, wie AEM Assets mit der serverseitigen Sortierung Ordner-Assets oder Suchanfragen in einem Durchgang sortiert, anstatt sie in Batches auf Clientseite zu verarbeiten.

Die Suchfunktion von Adobe Experience Manager (AEM) Assets wurde verbessert, um eine große Anzahl von Assets in der Ordnerlistenansicht und auf Suchergebnisseiten effizient zu sortieren.  Timeline-Einträge können ebenfalls sortiert werden. 

AEM Assets setzt auf eine serverseitige Sortierung, um alle Assets (unabhängig von ihrer Größe) in einem Ordner oder in einer Suchabfrage in einem Schritt und nicht stapelweise auf Clientseite zu sortieren.  Auf diese Weise können per Prefetch abgerufene Ergebnisse schnell in der Benutzeroberfläche angezeigt werden. Der Sortiervorgang wird hierdurch responsiver und schneller. 

## Sortieren von Assets in der Listenansicht {#sorting-assets-in-list-view}

Mit AEM Assets können Sie Ordner-Assets basierend auf den folgenden Feldern sortieren: 

* Gebietsschema
* Status
* Typ
* Größe
* Bewertung
* Änderungsdatum 
* Veröffentlichungsdatum 
* Nutzung
* Klicks
* Impressionen
* Ausgecheckt

1. Navigieren Sie zu einem Ordner, der eine große Anzahl von Assets enthält. 
1. Klicken/tippen Sie auf das Layoutsymbol und wechseln Sie in die Listenansicht.

   ![chlimage_1-394](assets/chlimage_1-394.png)

1. Klicken/tippen Sie auf das Sortiersymbol neben einer beliebigen Spaltenüberschrift in der Asset-Liste.

   ![chlimage_1-395](assets/chlimage_1-395.png)

   Die Liste der Assets wird auf Basis der Feldwerte sortiert. 

   ![chlimage_1-396](assets/chlimage_1-396.png)

>[!NOTE]
>
>Um die Werte in den Spalten `Name` oder `Title`zu sortieren, überlagern Sie `/libs/dam/gui/content/commons/availablecolumns` und ändern Sie den Wert von `sortable` in `True`.

## Sortieren von Assets in Suchergebnissen {#sorting-assets-in-search-results}

Sie können die Suchergebnisse basierend auf den folgenden Feldern sortieren: 

* Titel
* Status
* Typ
* Größe
* Änderungsdatum 
* Veröffentlichungsdatum 

1. Suchen Sie anhand der gewünschten Kriterien über das OmniSearch-Feld nach Assets. 

   ![chlimage_1-397](assets/chlimage_1-397.png)

1. Klicken/tippen Sie auf das Layoutsymbol und wechseln Sie in die Listenansicht. Wenn die Suchergebnisse bereits in der Listenansicht angezeigt werden, können Sie diesen Schritt überspringen. 
1. Klicken/tippen Sie auf das Sortiersymbol neben einer beliebigen Spaltenüberschrift in der Asset-Liste. Die Liste der Assets wird auf Basis der Feldwerte sortiert. 

   ![chlimage_1-398](assets/chlimage_1-398.png)

## Sortieren von Assets in der Timeline {#sorting-assets-in-timeline}

Mit AEM Assets können Sie Timeline-Einträge chronologisch sortieren, wie z. B. Anmerkungen, Versionen, Workflows und Aktivitäten. 

1. Wählen Sie über die Assets-Benutzeroberfläche ein Asset aus, für das die Timeline angezeigt werden soll. 
1. Klicken/tippen Sie auf das GlobalNav-Symbol und wählen Sie **[!UICONTROL Timeline]** aus.

   ![chlimage_1-399](assets/chlimage_1-399.png)

1. Wählen Sie in der Timeline einen Eintrag in der Liste aus.  Wählen Sie beispielsweise **[!UICONTROL Kommentare]** aus, um die Liste der Anmerkungen anzuzeigen, die mit dem Asset verknüpft sind.

   ![chlimage_1-400](assets/chlimage_1-400.png)

1. Klicken/tippen Sie auf das **[!UICONTROL Sortiersymbol]** neben der Bezeichnung **[!UICONTROL Datum]**. Abhängig von Ihrer Auswahl werden die Anmerkungen chronologisch in der Reihenfolge aufgeführt, in der sie dem Asset hinzugefügt wurden. 

   ![chlimage_1-401](assets/chlimage_1-401.png)

