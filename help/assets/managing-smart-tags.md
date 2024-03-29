---
title: Verwalten von Smart-Tags
description: Aktualisieren oder Entfernen ungenauer Smart-Tags zur Verbesserung der Relevanz von Tags
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
uuid: fd3eedf0-f222-45bf-aac7-90da6b7b7087
contentOwner: AG
discoiquuid: 3394b56a-3054-419b-9547-5740f8c35071
feature: Smart Tags,Tagging,Search
role: User
exl-id: 05f43e43-ac72-4ab1-a373-687c137d2bed
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 54%

---

# Verwalten von Smart-Tags {#managing-smart-tags}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Sie können Smart-Tags kuratieren, um ungenaue Tags zu entfernen, die möglicherweise Ihren Markenbildern zugewiesen wurden, sodass nur die relevantesten Tags angezeigt werden.

Mithilfe der Moderation von Smart-Tags können Sie Tag-basierte Suchen nach Bildern verfeinern, indem Sie sicherstellen, dass Ihr Bild nur in den Suchergebnissen für die relevantesten Tags angezeigt wird. Im Wesentlichen hilft es, die Wahrscheinlichkeit zu vermeiden, dass nicht verwandte Bilder in Suchergebnissen angezeigt werden.

Sie können einem Tag auch einen höheren Rang zuweisen, um seine Relevanz in Bezug auf ein Bild zu erhöhen. Je höher der Rang eines Tags für ein Bild, desto wahrscheinlicher ist bei einer Tag-basierten Suche die Aufnahme des Bildes in die Suchergebnisse.

1. Suchen Sie im OmniSearch-Feld nach Assets, die auf einem Tag basieren.
1. Prüfen Sie die Suchergebnisse auf Bilder, die Ihnen für Ihren Suchvorgang nicht relevant erscheinen.
1. Wählen Sie das Bild aus und klicken/tippen Sie dann auf das **[!UICONTROL Verwalten von Tags]** in der Symbolleiste.
1. Prüfen Sie die Tags auf der Seite **[!UICONTROL Tags verwalten]**. Wenn Sie nicht möchten, dass das Bild basierend auf einem bestimmten Tag durchsucht wird, wählen Sie das Tag aus und klicken/tippen Sie auf die **[!UICONTROL Löschen]** in der Symbolleiste. Klicken/tippen Sie alternativ auf (**[!UICONTROL X]**), das neben der Beschriftung angezeigt wird.
1. Um einem Tag einen höheren Rang zuzuweisen, wählen Sie das Tag aus und klicken/tippen Sie auf die **[!UICONTROL Bewerben]** in der Symbolleiste. Das höhergestufte Tag wird in den Abschnitt **[!UICONTROL Tags]** verschoben.
1. Klicken/tippen Sie auf **[!UICONTROL Speichern]** und dann Sie auf **[!UICONTROL OK]**, um das Dialogfeld „Erfolg“ zu schließen.
1. Navigieren Sie zur Eigenschaftenseite für das Bild. Beachten Sie, dass das beworbene Tag eine hohe Relevanz erhält und es aus diesem Grund höher in den Suchergebnissen angezeigt wird.

## Grundlegendes zu [!DNL Experience Manager]-Suchergebnissen mit Smart-Tags {#understand-search-results-with-smart-tags}

Die [!DNL Experience Manager]-Suche kombiniert die Suchbegriffe standardmäßig mit einer `AND`-Klausel. Dieses Standardverhalten ändert sich durch die Verwendung von Smart-Tags nicht. Durch die Verwendung von Smart-Tags wird eine zusätzliche `OR`-Klausel hinzugefügt. Damit wird jeder Suchbegriff aus den angewandten Smart-Tags gefunden. Suchen Sie beispielsweise nach `woman running`. Assets, die in den Metadaten nur das Keyword `woman`oder `running` aufweisen, werden standardmäßig nicht in den Suchergebnissen angezeigt. Ein Asset, das mit `woman` oder `running` die Verwendung von Smart-Tags wird in einer solchen Suchabfrage angezeigt. Die Suchergebnisse sind also eine Kombination aus

* Assets mit beiden Keywords, `woman` und `running` in den Metadaten.
* Assets, die über Smart-Tags mit einem der Keywords getaggt wurden.

Die Suchergebnisse, die in Metadatenfeldern alle Suchbegriffe aufweisen, werden zuerst angezeigt. Danach folgen die Suchergebnisse, die einem oder mehr Suchbegriffen in den Smart-Tags entsprechen. Im obigen Beispiel werden die Suchergebnisse ungefähr in dieser Reihenfolge angezeigt:

1. Treffer von `woman running` in den verschiedenen Metadatenfeldern.
1. Treffer von `woman running` in den Smart-Tags.
1. Treffer von `woman` oder `running` in Smart-Tags.
