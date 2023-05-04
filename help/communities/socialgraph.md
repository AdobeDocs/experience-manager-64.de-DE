---
title: Social-Diagramm verwenden
seo-title: Using Social Graph
description: Hinzufügen einer folgenden Komponente zu einer Seite
seo-description: Adding a Following component to a page
uuid: 8be6334b-e6c9-40bc-90a8-750b98419470
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 0ce57ab1-e4c6-4c38-963d-556eef8757f2
exl-id: ab829d28-278d-4139-af16-edcc24b3d56b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 5%

---

# Social-Diagramm verwenden {#using-social-graph}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Einführung {#introduction}

Die Fähigkeit eines Community-Mitglieds zu folgen [activities](activities.md) und werden durch zwei Komponenten festgelegt: `Follow`und `Following`.

Die `Follow`-Komponente muss mit einer anderen Ressource verknüpft sein, und diese Zuordnung ist bereits für Community-Mitglieder und -Funktionen eingerichtet.

Die `Following`-Komponente werden lediglich die Mitglieder aufgelistet, die dem aktuellen Mitglied folgen oder dem aktuellen Mitglied folgen. Dieses soziale Diagramm der Beziehungen zwischen Mitgliedern ist in dem Benutzerprofil enthalten, das für eine [Community-Site](overview.md#communitiessites).

## Folgendes zu einer Seite hinzufügen {#adding-following-to-a-page}

Wenn Sie eine `Following`Komponente auf einer Seite im Autorenmodus zu finden, die Komponente `Communities / Following` und ziehen Sie sie an die gewünschte Stelle auf einer Seite, auf der das Social-Diagramm erscheinen soll.

Die erforderlichen Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](basics.md).

Wenn die [erforderliche clientseitige Bibliotheken](essentials-socialgraph.md#essentials-for-client-side) eingeschlossen sind, wird die `Following` wird angezeigt:

![chlimage_1-447](assets/chlimage_1-447.png)

## Konfigurieren der folgenden {#configuring-following}

Derzeit ist es erforderlich, die -Eigenschaft festzulegen, um zu bestimmen, ob die Komponente die `follows`Beziehung oder `following`Beziehung.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie unter [Grundlagen zum Social-Diagramm](essentials-socialgraph.md) für Entwickler.
