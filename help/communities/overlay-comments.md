---
title: Komponente "Überlagerungskommentare"
seo-title: Komponente "Überlagerungskommentare"
description: Übersicht über die Komponente "Overlay Comments"
seo-description: Übersicht über die Komponente "Overlay Comments"
uuid: 634240e2-99bb-4107-89f5-c66d53e2515d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 4849da13-518c-40c8-b80e-1b2264d7f8f5
translation-type: tm+mt
source-git-commit: 8f169bb9b015ae94b9160d3ebbbd1abf85610465
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 0%

---


# Komponente &quot;Überlagerungskommentare&quot; {#overlay-comments-component}

Die Absicht, eine Standardkomponente zu [überlagern](client-customize.md#overlays) , besteht darin, das Erscheinungsbild oder Verhalten einer Komponente global für alle relativen Verweise auf die Komponente zu ändern. Es beruht auf der Natur von sling, um in den Ordner /apps aufzulösen, bevor Sie im Ordner /libs suchen. Daher ist der Pfad zur Komponente identisch mit dem Pfad zur Standardkomponente, es sei denn, er befindet sich im Ordner &quot;/apps&quot;und nicht im Ordner &quot;/libs&quot;.

## Beispiel {#example}

Angenommen, Sie möchten die Kommentarfunktion so ändern, dass sie mit dem Design Ihrer Website übereinstimmt, indem Sie die Kommentarkopfzeile ändern, sodass der Avatar für keinen Kommentar mehr angezeigt wird. Die Lösungen zum Ausblenden des Avatars verwenden entweder CSS oder überlagern, wie hier beschrieben, die Datei header.jsp im Anwendungsordner, damit der HTML-Code, der den Avatar enthält, nie an den Client gesendet wird.

Um Kommentare zu überlagern, müssen Sie:

1. [Kommentarseite](overlay-create-comments-page.md)
1. [Nodes erstellen](overlay-create-nodes.md)
1. [Erscheinungsbild ändern](overlay-alter-appearance.md)

