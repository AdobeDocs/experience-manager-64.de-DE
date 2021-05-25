---
title: Überlagerungskommentkomponente
seo-title: Überlagerungskommentkomponente
description: Übersicht über die Komponente "Overlay Comments"
seo-description: Übersicht über die Komponente "Overlay Comments"
uuid: 634240e2-99bb-4107-89f5-c66d53e2515d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 4849da13-518c-40c8-b80e-1b2264d7f8f5
exl-id: 31528814-02bc-4978-87fa-5c8074b454ed
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 0%

---

# Komponente für Überlagerungskommentare {#overlay-comments-component}

Die Absicht von [Überlagern](client-customize.md#overlays) einer Standardkomponente besteht darin, das Erscheinungsbild oder Verhalten einer Komponente global zu ändern, und zwar für alle relativen Verweise auf die Komponente. Es verlässt sich auf die Art von Sling, um zum Ordner /apps zu gelangen, bevor eine Suche im Ordner /libs durchgeführt wird. Daher ist der Pfad zur Komponente mit dem Pfad zur Standardkomponente identisch, allerdings befindet er sich im Ordner /apps und nicht im Ordner /libs .

## Beispiel {#example}

Angenommen, Sie möchten die Kommentarfunktion so ändern, dass sie mit dem Design Ihrer Website übereinstimmt, indem Sie den Kommentar-Header so ändern, dass er den Avatar nicht mehr für Kommentare anzeigt. Die Lösungen zum Ausblenden des Avatars verwenden entweder CSS oder, wie hier beschrieben, überlagern die Datei &quot;header.jsp&quot;im Apps-Ordner, sodass der HTML-Code, der den Avatar enthält, nie an den Client gesendet wird.

Um Kommentare zu überlagern, müssen Sie:

1. [Kommentarseite](overlay-create-comments-page.md)
1. [Erstellen von Knoten](overlay-create-nodes.md)
1. [Erscheinungsbild ändern](overlay-alter-appearance.md)
