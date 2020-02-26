---
title: Verwalten von Smarttags
description: Aktualisieren oder entfernen Sie die ungenauen Smarttags, um die Relevanz von Tags zu verbessern
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
uuid: fd3eedf0-f222-45bf-aac7-90da6b7b7087
contentOwner: AG
discoiquuid: 3394b56a-3054-419b-9547-5740f8c35071
translation-type: tm+mt
source-git-commit: 7771cbb218d80247f65e92cbe7e8cdfd9720b75e

---


# Verwalten von Smart-Tags {#managing-smart-tags}

Sie können Smart-Tags kuratieren, um alle falschen Tags zu entfernen, die Ihren Markenbildern zugewiesen wurden, sodass nur die relevantesten Tags angezeigt werden.

Mithilfe der Moderation können Sie Tag-basierte Suchen nach Bildern verfeinern, indem Sie sicherstellen, dass Ihr Bild nur in den Suchergebnissen für die relevantesten Tags angezeigt wird. Im Grunde wird so ausgeschlossen, dass in den Suchergebnissen Bilder ohne Bezug angezeigt werden.

Darüber hinaus können Sie Tags einen höheren Rang zuweisen, um ihre Relevanz in Bezug auf ein Bild zu erhöhen. Je höher der Rang eines Tags für ein Bild, desto wahrscheinlicher ist bei einer Tag-basierten Suche die Aufnahme des Bildes in die Suchergebnisse.

1. Suchen Sie im OmniSearch-Feld nach Assets, die auf einem Tag basieren.
1. Prüfen Sie die Suchergebnisse auf Bilder, die Ihnen für Ihren Suchvorgang nicht relevant erscheinen.
1. Wählen Sie ein solches Bild aus und klicken/tippen Sie dann in der Symbolleiste auf das Symbol **[!UICONTROL Tags verwalten]**.
1. Prüfen Sie die Tags auf der Seite **[!UICONTROL Tags verwalten]**. Wenn Sie ein spezifisches Tag für ein Bild ausschließen möchten, wählen Sie das Tag aus und klicken/tippen Sie in der Symbolleiste auf das Symbol **[!UICONTROL Löschen]**. Klicken/tippen Sie alternativ auf das Symbol (**[!UICONTROL X]**), das neben der Beschriftung angezeigt wird.
1. Um dem Tag einen höheren Rang zuzuweisen, wählen Sie es aus und klicken/tippen Sie in der Symbolleiste auf das Symbol **[!UICONTROL Bewerben.]** Das höhergestufte Tag wird in den Abschnitt **[!UICONTROL Tags]** verschoben.
1. Klicken Sie auf **[!UICONTROL Speichern]** und dann auf **[!UICONTROL OK]**, um das Dialogfeld „Erfolg“ zu schließen.
1. Navigieren Sie zur Seite „Eigenschaften“ des betreffenden Bildes. Beachten Sie, dass das beworbene Tag eine hohe Relevanz erhält und es aus diesem Grund höher in den Suchergebnissen angezeigt wird.

## AEM-Suchergebnisse mit Smart-Tags {#understand-search-results-with-smart-tags}

By default, AEM search combines the search terms with an `AND` clause. Dieses Standardverhalten ändert sich durch die Verwendung von Smart-Tags nicht. Using smart tags adds an additional `OR` clause to find any of the search terms in the applies smart tags. For example, consider searching for `woman running`. Assets with just `woman` or just `running` keyword in the metadata do not appear in the search results by default. However, an asset tagged with either `woman` or `running` using smart taggs appears in such a search query. Die Suchergebnisse sind also eine Kombination aus

* Assets mit Suchbegriffen `woman` und `running` in den Metadaten.
* Assets, die über Smart-Tags mit einem der Schlüsselwörter getaggt wurden.

Die Suchergebnisse, die in Metadatenfeldern alle Suchbegriffe aufweisen, werden zuerst angezeigt. Danach folgen die Suchergebnisse, die einem oder mehr Suchbegriffen in den Smart-Tags entsprechen. Im obigen Beispiel werden die Suchergebnisse ungefähr in dieser Reihenfolge angezeigt:

1. matches of `woman running` in the various metadata fields.
1. Übereinstimmungen `woman running` in Smart-Tags.
1. matches of `woman` or of `running` in smart tags.
