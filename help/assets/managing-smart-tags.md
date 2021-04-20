---
title: Verwalten von Smarttags
description: Aktualisieren oder entfernen Sie die ungenauen Smarttags, um die Relevanz von Tags zu verbessern
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
uuid: fd3eedf0-f222-45bf-aac7-90da6b7b7087
contentOwner: AG
discoiquuid: 3394b56a-3054-419b-9547-5740f8c35071
feature: Smart Tags,Tagging,Search
role: Business Practitioner
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 84%

---


# Verwalten von Smart-Tags {#managing-smart-tags}

Sie können Smart-Tags kuratieren, um alle falschen Tags zu entfernen, die Ihren Markenbildern zugewiesen wurden, sodass nur die relevantesten Tags angezeigt werden.

Mithilfe der Moderation von Smart-Tags können Sie Tag-basierte Suchen nach Bildern verfeinern, indem Sie sicherstellen, dass Ihr Bild nur in den Suchergebnissen für die relevantesten Tags angezeigt wird. Im Grunde wird so ausgeschlossen, dass in den Suchergebnissen Bilder ohne Bezug angezeigt werden.

Darüber hinaus können Sie Tags einen höheren Rang zuweisen, um ihre Relevanz in Bezug auf ein Bild zu erhöhen. Je höher der Rang eines Tags für ein Bild, desto wahrscheinlicher ist bei einer Tag-basierten Suche die Aufnahme des Bildes in die Suchergebnisse.

1. Suchen Sie im OmniSearch-Feld nach Assets, die auf einem Tag basieren.
1. Prüfen Sie die Suchergebnisse auf Bilder, die Ihnen für Ihren Suchvorgang nicht relevant erscheinen.
1. Wählen Sie ein solches Bild aus und klicken/tippen Sie dann in der Symbolleiste auf das Symbol **[!UICONTROL Tags verwalten]**.
1. Prüfen Sie die Tags auf der Seite **[!UICONTROL Tags verwalten]**. Wenn Sie ein spezifisches Tag für ein Bild ausschließen möchten, wählen Sie das Tag aus und klicken/tippen Sie in der Symbolleiste auf das Symbol **[!UICONTROL Löschen]**. Klicken/tippen Sie alternativ auf das Symbol (**[!UICONTROL X]**), das neben der Beschriftung angezeigt wird.
1. Um dem Tag einen höheren Rang zuzuweisen, wählen Sie es aus und klicken/tippen Sie in der Symbolleiste auf das Symbol **[!UICONTROL Bewerben.]** Das höhergestufte Tag wird in den Abschnitt **[!UICONTROL Tags]** verschoben.
1. Klicken/tippen Sie auf **[!UICONTROL Speichern]** und dann Sie auf **[!UICONTROL OK]**, um das Dialogfeld „Erfolg“ zu schließen.
1. Navigieren Sie zur Seite „Eigenschaften“ des betreffenden Bildes. Beachten Sie, dass das beworbene Tag eine hohe Relevanz erhält und es aus diesem Grund höher in den Suchergebnissen angezeigt wird.

## AEM-Suchergebnisse mit Smart-Tags  {#understand-search-results-with-smart-tags}

Die AEM-Suche kombiniert die Suchbegriffe standardmäßig mit einer `AND`-Klausel. Dieses Standardverhalten ändert sich durch die Verwendung von Smart-Tags nicht. Durch die Verwendung von Smart-Tags wird eine zusätzliche `OR`-Klausel hinzugefügt. Damit wird jeder Suchbegriff aus den angewandten Smart-Tags gefunden. Suchen Sie beispielsweise nach `woman running`. Assets, die in den Metadaten nur das Keyword `woman`oder `running` aufweisen, werden standardmäßig nicht in den Suchergebnissen angezeigt. Ein Asset, das entweder mit `woman` oder `running` mit intelligenten Tags getaggt wurde, wird in einer solchen Abfrage angezeigt. Die Suchergebnisse sind also eine Kombination aus

* Assets mit beiden Schlüsselwörtern `woman` und `running` in den Metadaten.
* Assets, die über Smart-Tags mit einem der Keywords getaggt wurden.

Die Suchergebnisse, die in Metadatenfeldern alle Suchbegriffe aufweisen, werden zuerst angezeigt. Danach folgen die Suchergebnisse, die einem oder mehr Suchbegriffen in den Smart-Tags entsprechen. Im obigen Beispiel werden die Suchergebnisse ungefähr in dieser Reihenfolge angezeigt:

1. Treffer von `woman running` in den verschiedenen Metadatenfeldern.
1. Treffer von `woman running` in den Smart-Tags.
1. Treffer von `woman` oder `running` in Smart-Tags.
