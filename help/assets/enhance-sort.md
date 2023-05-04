---
title: Erweiterte Sortierung von Assets in AEM
description: Erfahren Sie mehr [!DNL Experience Manager] Assets stellt eine serverseitige Sortierung bereit, um Ordner-Assets oder Suchabfragen auf einmal zu sortieren, anstatt sie in Stapeln auf der Clientseite zu sortieren.
contentOwner: AG
feature: Search
role: User
exl-id: aa24ca68-d94e-4bd4-a5cc-113906650a2e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 6%

---

# Verbesserte Sortierung von Assets in [!DNL Experience Manager] {#enhanced-sorting-of-assets-in-aem}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Erfahren Sie mehr [!DNL Experience Manager] Assets stellt eine serverseitige Sortierung bereit, um Ordner-Assets oder Suchabfragen auf einmal zu sortieren, anstatt sie in Stapeln auf der Clientseite zu sortieren.

Die Suchfunktion von Adobe Experience Manager Assets wurde verbessert, um eine große Anzahl von Assets in der Ordnerlistenansicht und den Suchergebnisseiten effizient zu sortieren. Sie können auch Zeitleisten-Einträge sortieren.

[!DNL Experience Manager] Assets stellt eine Server-seitige Sortierung bereit, um den gesamten Satz von Assets (unabhängig davon, wie groß sie sind) in einem Ordner oder einer Suchabfrage auf einmal zu sortieren, anstatt sie in Stapeln auf Client-Seite zu sortieren. Auf diese Weise können bereits abgerufene Ergebnisse schnell auf der Benutzeroberfläche angezeigt werden, was den Sortiervorgang responsiver und schneller macht.

## Sortieren von Assets in der Listenansicht {#sorting-assets-in-list-view}

[!DNL Experience Manager] Mit Assets können Sie Ordner-Assets anhand der folgenden Felder sortieren:

* Gebietsschema
* Status
* Typ
* Größe
* Bewertung
* Datum geändert
* Veröffentlichungsdatum
* Verwendung
* Klicks
* Impressionen
* Ausgecheckt

1. Navigieren Sie zu einem Ordner, der eine große Anzahl von Assets enthält.
1. Klicken/tippen Sie auf das Symbol Layout und wechseln Sie zur Listenansicht.

   ![chlimage_1-394](assets/chlimage_1-394.png)

1. Klicken/tippen Sie auf das Symbol Sortieren neben einer Spaltenüberschrift in der Asset-Liste.

   ![chlimage_1-395](assets/chlimage_1-395.png)

   Die Liste der Assets wird anhand der Feldwerte sortiert.

   ![chlimage_1-396](assets/chlimage_1-396.png)

>[!NOTE]
>
>So sortieren Sie die Werte im `Name` oder `Title`Spalten, Überlagerung `/libs/dam/gui/content/commons/availablecolumns` und ändern Sie den Wert von `sortable` nach `True`.

## Sortieren von Assets in Suchergebnissen {#sorting-assets-in-search-results}

Sie können Suchergebnisse anhand der folgenden Felder sortieren:

* Titel
* Status
* Typ
* Größe
* Datum geändert
* Veröffentlichungsdatum

1. Suchen Sie im OmniSearch-Feld basierend auf den gewünschten Kriterien nach Assets.

   ![chlimage_1-397](assets/chlimage_1-397.png)

1. Klicken/tippen Sie auf das Symbol Layout und wechseln Sie zur Listenansicht. Wenn die Suchergebnisse bereits in der Listenansicht angezeigt werden, überspringen Sie diesen Schritt.
1. Klicken/tippen Sie auf das Symbol Sortieren neben einer Spaltenüberschrift in der Asset-Liste. Die Liste der Assets wird anhand der Feldwerte sortiert.

   ![chlimage_1-398](assets/chlimage_1-398.png)

## Sortieren von Assets in der Timeline {#sorting-assets-in-timeline}

[!DNL Assets] ermöglicht die chronologische Sortierung von Zeitleisten-Einträgen, z. B. Anmerkungen, Versionen, Workflows und Aktivitäten.

1. Wählen Sie in der Assets-Benutzeroberfläche ein Asset aus, für das Sie die Timeline anzeigen möchten.
1. Klicken/tippen Sie auf das GlobalNav-Symbol und wählen Sie **[!UICONTROL Timeline]**.

   ![chlimage_1-399](assets/chlimage_1-399.png)

1. Wählen Sie in der Timeline einen Eintrag aus der Liste aus. Wählen Sie beispielsweise **[!UICONTROL Kommentare]** , um die Liste der mit dem Asset verknüpften Anmerkungen anzuzeigen.

   ![chlimage_1-400](assets/chlimage_1-400.png)

1. Klicken/tippen Sie auf **[!UICONTROL Sortieren]** neben dem **[!UICONTROL Datum]** Beschriftung. Je nach Auswahl werden die Anmerkungen in chronologischer/umgekehrter chronologischer Reihenfolge aufgeführt, in der sie zum Asset hinzugefügt wurden.

   ![chlimage_1-401](assets/chlimage_1-401.png)
