---
title: Gruppenvorlagen
seo-title: Group Templates
description: Zugriff auf die Konsole Gruppenvorlagen
seo-description: How to access the Group Templates console
uuid: a3c6dfe6-f973-4dcf-9c66-ea52cbe56630
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 9a862756-58e8-47c0-a4b4-5d4aaac021e4
role: Admin
exl-id: ac399a66-0f3b-4f95-969e-a4109c260d1d
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 2%

---

# Gruppenvorlagen {#group-templates}

Die Gruppenvorlagen-Konsole ähnelt der [Site-Vorlagen](sites.md) Konsole. Beide sind Blueprints für eine Reihe vorab verkabelter Seiten und Funktionen, die eine Community-Site bilden. Der Unterschied besteht darin, dass eine Site-Vorlage für die Hauptgemeinde und eine Gruppenvorlage für eine Community-Gruppe, eine Unter-Community, die in der Hauptgemeinde verschachtelt ist, bestimmt wird.

Eine Community-Gruppe wird in eine Site-Vorlage integriert, indem die Variable [Gruppenfunktion](functions.md#groups-function) (die nicht die erste und auch nicht die einzige Funktion in der Vorlage sein darf).

Als Communitys [Feature Pack 1](deploy-communities.md#latestfeaturepack)können Gruppen verschachtelt werden, indem die Funktion Gruppen in eine Gruppenvorlage eingefügt wird.

Im Moment, in dem die Aktion durchgeführt wird, um eine neue Community-Gruppe zu erstellen, wird die Vorlage (Struktur) der Gruppe ausgewählt. Die Auswahl hängt davon ab, wie die Funktion Gruppen konfiguriert wurde, als sie der Site- oder Gruppenvorlage hinzugefügt wurde.

>[!NOTE]
>
>Die Konsolen für die Erstellung von [Community-Sites](sites-console.md), [Community-Site-Vorlagen](sites.md), [Community-Gruppenvorlagen](tools-groups.md) und [Community-Funktionen](functions.md) sind nur zur Verwendung in der Autorenumgebung vorgesehen.

## Gruppenvorlagen-Konsole {#group-templates-console}

In der Autorenumgebung, um die Gruppenvorlagen-Konsole zu erreichen

* Über die globale Navigation: **[!UICONTROL Tools > Communities > Gruppenvorlagen]**

Diese Konsole zeigt die Vorlagen an, aus denen ein [Community-Site](sites-console.md) kann erstellt werden und die Erstellung neuer Gruppenvorlagen ermöglicht.

![groupstemplate](assets/groupstemplate.png)

## Gruppenvorlage erstellen {#create-goup-template}

Um mit der Erstellung einer neuen Gruppenvorlage zu beginnen, wählen Sie **[!UICONTROL Erstellen]**

Dadurch wird der Site-Editor-Bereich angezeigt, der drei Unterbereiche enthält:

### Grundlegende Informationen {#basic-info}

![chlimage_1-96](assets/chlimage_1-96.png)

Im Bedienfeld &quot;Grundlegende Informationen&quot;werden ein Name, eine Beschreibung und die Frage, ob die Vorlage aktiviert oder deaktiviert ist, konfiguriert:

* **[!UICONTROL Neuer Name der Gruppenvorlage]**
Vorlagenname-ID

* **[!UICONTROL Beschreibung]**
Vorlagenbeschreibung

* **[!UICONTROL Deaktiviert/Aktiviert]**
Ein Umschalter, der steuert, ob die Vorlage referenzierbar ist

### Miniaturansicht {#thumbnail}

![chlimage_1-97](assets/chlimage_1-97.png)

(Optional) Wählen Sie das Symbol Bild hochladen aus, um eine Miniaturansicht zusammen mit dem Namen und der Beschreibung für Ersteller von Community-Sites anzuzeigen.

### Struktur {#structure}

>[!CAUTION]
>
>Wenn Sie mit AEM 6.1 Communities FP4 oder früher arbeiten, fügen Sie einer Gruppenvorlage keine Gruppenfunktion hinzu.
>
>Die Funktion für verschachtelte Gruppen ist ab Communities verfügbar [FP1](communities.md#latestfeaturepack).
>
>Es ist immer noch nicht zulässig, eine Gruppenfunktion als erste oder einzige Funktion in einer Vorlage hinzuzufügen.

![grptemplateeditor](assets/grptemplateeditor.png)

Um Community-Funktionen hinzuzufügen, ziehen Sie von der rechten Seite nach links in die Reihenfolge, in der die Links zum Site-Menü angezeigt werden sollen. Stile werden während der Erstellung der Site auf die Vorlage angewendet.

Wenn Sie beispielsweise ein Forum wünschen, ziehen Sie die Forumsfunktion aus der Bibliothek und legen Sie sie unter dem Vorlagen-Builder ab. Dadurch wird das Dialogfeld für die Forenkonfiguration geöffnet. Siehe [Funktionskonsole](functions.md) für Informationen zu den Konfigurationsdialogfeldern.

Ziehen Sie weiterhin alle anderen Community-Funktionen, die basierend auf dieser Vorlage für eine Unter-Community-Site (Gruppe) gewünscht werden, in den Arbeitsbereich.

![dragfeatures](assets/dragfunctions.png)

Nachdem alle gewünschten Funktionen im Vorlagenerstellungsbereich abgelegt und konfiguriert wurden, wählen Sie **[!UICONTROL Speichern]** in der oberen rechten Ecke.

## Gruppenvorlage bearbeiten {#edit-group-template}

Beim Anzeigen von Community-Gruppen in der Hauptseite [Gruppenvorlagen-Konsole](#group-templates-console)können Sie eine vorhandene Gruppenvorlage zur Bearbeitung auswählen.

Die Bearbeitung einer Gruppenvorlage hat keine Auswirkungen auf Community-Sites, die bereits aus der Vorlage erstellt wurden. Es ist möglich, [Bearbeiten einer Community-Site](sites-console.md#modify-structure)-Struktur.

Dieser Prozess stellt dieselben Bedienfelder wie [Erstellen einer Gruppenvorlage](#create-goup-template).
