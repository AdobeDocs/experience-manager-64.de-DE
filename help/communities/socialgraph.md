---
title: Verwenden von Sozialdiagrammen
seo-title: Verwenden von Sozialdiagrammen
description: Hinzufügen einer folgenden Komponente zu einer Seite
seo-description: Hinzufügen einer folgenden Komponente zu einer Seite
uuid: 8be6334b-e6c9-40bc-90a8-750b98419470
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 0ce57ab1-e4c6-4c38-963d-556eef8757f2
exl-id: ab829d28-278d-4139-af16-edcc24b3d56b
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 26%

---

# Verwenden von Sozialdiagrammen {#using-social-graph}

## Einführung {#introduction}

Die Möglichkeit, dass ein Community-Mitglied [Aktivitäten](activities.md) folgt und ihnen folgt, wird durch zwei Komponenten festgelegt: `Follow`und `Following`.

Die Komponente `Follow`muss mit einer anderen Ressource verknüpft sein, und diese Zuordnung ist bereits für Community-Mitglieder und -Funktionen eingerichtet.

Die Komponente `Following`listet einfach die Mitglieder auf, die dem aktuellen Mitglied folgen oder dem aktuellen Mitglied folgen. Dieses Sozialdiagramm der Mitgliederbeziehungen untereinander ist Teil des Benutzerprofils, das für eine [Community-Site](overview.md#communitiessites) bereitgestellt wird.

## Hinzufügen von Folgenden zu einer Seite {#adding-following-to-a-page}

Wenn Sie im Autorenmodus eine `Following`Komponente zu einer Seite hinzufügen möchten, suchen Sie die Komponente `Communities / Following` und ziehen Sie sie an die gewünschte Stelle auf einer Seite, auf der das Social-Diagramm angezeigt werden soll.

Die erforderlichen Informationen finden Sie unter [Grundlagen der Communities-Komponenten](basics.md).

Wenn die [erforderlichen clientseitigen Bibliotheken](essentials-socialgraph.md#essentials-for-client-side) eingeschlossen sind, wird die Komponente `Following` so angezeigt:

![chlimage_1-447](assets/chlimage_1-447.png)

## Konfigurieren von Folgenden {#configuring-following}

Derzeit muss die Eigenschaft festgelegt werden, um zu bestimmen, ob die Komponente die `follows`Beziehung oder die `following`Beziehung anzeigt.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Entwickler-Seite [Sozialdiagrammgrundlagen](essentials-socialgraph.md).
