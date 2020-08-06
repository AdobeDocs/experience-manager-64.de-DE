---
title: Gruppenvorlagen
seo-title: Gruppenvorlagen
description: Zugriff auf die Konsole Gruppenvorlagen
seo-description: Zugriff auf die Konsole Gruppenvorlagen
uuid: a3c6dfe6-f973-4dcf-9c66-ea52cbe56630
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 9a862756-58e8-47c0-a4b4-5d4aaac021e4
translation-type: tm+mt
source-git-commit: 13d890d08a032fe4eef1dac793dcf2a3e682a52c
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 2%

---


# Gruppenvorlagen {#group-templates}

Die Konsole &quot;Gruppenvorlagen&quot;ist der Konsole &quot; [Site-Vorlagen](sites.md) &quot;sehr ähnlich. Beide sind Entwürfe für eine Reihe vorab verkabelter Seiten und Funktionen, die eine Community-Site bilden. Der Unterschied besteht darin, dass eine Site-Vorlage für die Haupt-Community und eine Gruppenvorlage für eine Community-Gruppe, eine Unter-Community, die innerhalb der Haupt-Community verschachtelt ist, bestimmt ist.

Eine Community-Gruppe wird in eine Site-Vorlage integriert, indem die Funktion [](functions.md#groups-function) Groups einbezogen wird (die nicht die erste und auch nicht die einzige Funktion in der Vorlage sein kann).

Ab Communities [Feature Pack 1](deploy-communities.md#latestfeaturepack)ist es möglich Gruppen zu verschachteln, indem die Funktion Groups in eine Gruppenvorlage einbezogen wird.

Im Moment, da die Aktion durchgeführt wird, um eine neue Community-Gruppe zu erstellen, wird die Vorlage (Struktur) der Gruppe ausgewählt. Die Auswahl hängt davon ab, wie die Funktion Gruppen konfiguriert wurde, wenn sie der Site- oder Gruppenvorlage hinzugefügt wurde.

>[!NOTE]
>
>Die Konsolen für die Erstellung von [Community-Sites](sites-console.md), [Community-Site-Vorlagen](sites.md), [Community-Gruppenvorlagen](tools-groups.md) und [Community-Funktionen](functions.md) sind nur zur Verwendung in der Autorendatei bestimmt.

## Gruppenvorlagen-Konsole {#group-templates-console}

In der Umgebung &quot;Autor&quot;zur Gruppenvorlagen-Konsole

* Aus globaler Navigation: **[!UICONTROL Werkzeuge > Communities > Gruppenvorlagen]**

Diese Konsole zeigt die Vorlagen an, aus denen eine [Community-Site](sites-console.md) erstellt werden kann, und ermöglicht die Erstellung neuer Gruppenvorlagen.

![groupstemplate](assets/groupstemplate.png)

## Gruppenvorlage erstellen {#create-goup-template}

Um eine neue Gruppenvorlage zu erstellen, wählen Sie **[!UICONTROL Erstellen]**

Dadurch wird der Site-Editor-Bereich angezeigt, der drei Unterbereiche enthält:

### Grundlegende Informationen {#basic-info}

![chlimage_1-96](assets/chlimage_1-96.png)

Im Bedienfeld &quot;Grundlegende Informationen&quot;werden ein Name, eine Beschreibung und die Konfiguration der Vorlage, ob sie aktiviert oder deaktiviert ist, wie folgt konfiguriert:

* **[!UICONTROL Name der neuen Gruppenvorlage]** Die Vorlagenname-ID

* **[!UICONTROL Beschreibung]** Die Vorlagenbeschreibung

* **[!UICONTROL Deaktiviert/Aktiviert]** Ein Umschalter, der steuert, ob die Vorlage referenzierbar ist

### Miniaturansicht       {#thumbnail}

![chlimage_1-97](assets/chlimage_1-97.png)

(Optional) Wählen Sie das Symbol Bild hochladen, um eine Miniaturansicht mit dem Namen und der Beschreibung für Ersteller von Community-Sites anzuzeigen.

### Struktur {#structure}

>[!CAUTION]
>
>Wenn Sie mit AEM 6.1 Communities FP4 oder früher arbeiten, sollten Sie einer Gruppenvorlage keine Gruppenfunktion hinzufügen.
>
>Die Funktion für verschachtelte Gruppen ist ab Communities [FP1](communities.md#latestfeaturepack)verfügbar.
>
>Es ist immer noch nicht zulässig, eine Funktion &quot;Gruppen&quot;als erste oder einzige Funktion in einer Vorlage hinzuzufügen.

![grptemplateeditor](assets/grptemplateeditor.png)

Um Community-Funktionen hinzuzufügen, ziehen Sie von der rechten Seite nach links in der Reihenfolge, in der die Sitemenü-Links angezeigt werden sollen. Stile werden während der Erstellung der Site auf die Vorlage angewendet.

Wenn Sie beispielsweise ein Forum wünschen, ziehen Sie die Forumsfunktion aus der Bibliothek und legen Sie sie unter dem Vorlagenaufbau ab. Dadurch wird der Dialog zur Forumkonfiguration geöffnet. Informationen zu den Konfigurationsdialogen finden Sie in der [Funktionskonsole](functions.md) .

Ziehen Sie weiterhin alle anderen Community-Funktionen, die basierend auf dieser Vorlage für eine Subcommunity-Site (Gruppe) gewünscht werden, und legen Sie sie ab.

![dragworks](assets/dragfunctions.png)

Nachdem alle gewünschten Funktionen in den Vorlagenaufbaubereich gezogen und konfiguriert wurden, wählen Sie oben rechts die Option **[!UICONTROL Speichern]** .

## Gruppenvorlage bearbeiten {#edit-group-template}

Bei der Anzeige von Community-Gruppen in der Haupt- [Gruppenvorlagenkonsole](#group-templates-console)ist es möglich, eine vorhandene Gruppenvorlage zur Bearbeitung auszuwählen.

Das Bearbeiten einer Gruppenvorlage hat keine Auswirkungen auf Community-Sites, die bereits aus der Vorlage erstellt wurden. Stattdessen können Sie die Struktur einer Community-Site [direkt](sites-console.md#modify-structure)bearbeiten.

Dieser Vorgang stellt dieselben Bereiche bereit wie das [Erstellen einer Gruppenvorlage](#create-goup-template).
