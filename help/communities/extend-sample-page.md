---
title: hinzufügen auf Beispielseite
seo-title: hinzufügen auf Beispielseite
description: hinzufügen benutzerdefinierter Kommentare auf einer Seite
seo-description: hinzufügen benutzerdefinierter Kommentare auf einer Seite
uuid: 7dbaff4f-9986-435d-9379-7add676ea254
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 7185fb13-46a2-4fa3-aa21-a51e63cdb9be
translation-type: tm+mt
source-git-commit: 44c56ec5de6e9a832aaa52ab4a6c4978af7a9865
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---


# hinzufügen auf Beispielseite {#add-comment-to-sample-page}

Nachdem die Komponenten für das benutzerdefinierte Kommentarsystem im Anwendungsordner (/apps) vorhanden sind, ist es möglich, die erweiterte Komponente zu verwenden. Die Instanz des Kommentarsystems auf einer Website, die betroffen sein soll, muss ihren resourceType als benutzerdefiniertes Kommentarsystem festlegen und alle erforderlichen Client-Bibliotheken einschließen.

## Erforderliche Clientlibs {#identify-required-clientlibs} identifizieren

Die für den Stil und die Funktionsweise der Standardkommentare erforderlichen Client-Bibliotheken sind auch für erweiterte Kommentare erforderlich.

Das [Handbuch zu Community-Komponenten](components-guide.md) identifiziert die erforderlichen Client-Bibliotheken. Navigieren Sie zum Komponentenhandbuch und Ansicht der Kommentarkomponente, z. B.:

[http://localhost:4502/content/community-components/en/comments.html](http://localhost:4502/content/community-components/en/comments.html)

Beachten Sie die drei Clientbibliotheken, die für die ordnungsgemäße Wiedergabe und Funktionsweise von Kommentaren erforderlich sind. Diese müssen eingeschlossen werden, wenn auf erweiterte Kommentare verwiesen wird, sowie die Client-Bibliothek [extended Comments](extend-create-components.md#create-a-client-library-folder) ( `apps.custom.comments`).

![chlimage_1-47](assets/chlimage_1-47.png)

## hinzufügen benutzerspezifischer Kommentare auf einer Seite {#add-custom-comments-to-a-page}

Da pro Seite nur ein Kommentarsystem erstellt werden kann, ist es einfacher, eine Beispielseite zu erstellen, wie im kurzen Lernprogramm [Beispielseite erstellen](create-sample-page.md) beschrieben.

Nach der Erstellung wechseln Sie in den Designmodus und stellen Sie die benutzerspezifische Komponentengruppe bereit, damit die Komponente `Alt Comments` der Seite hinzugefügt werden kann.

Damit der Kommentar korrekt angezeigt und funktioniert, müssen die Client-Bibliotheken für Kommentare zur clientlibslist für die Seite hinzugefügt werden (siehe [clientlibs für Communities-Komponenten](clientlibs.md)).

### Kommentare clientlibs auf Beispielseite {#comments-clientlibs-on-sample-page}

![Kommentare zu Clientlibs auf der Beispielseite](assets/chlimage_1-48.png)

### Autor: Alt-Kommentar auf Beispielseite {#author-alt-comment-on-sample-page}

![Alt-Kommentar auf Beispielseite](assets/chlimage_1-49.png)

### Autor: Beispiel-Seiten-Kommentarknoten-Knoten {#author-sample-page-comments-node}

Sie können resourceType in CRXDE überprüfen, indem Sie die Eigenschaften des Knotens comments für die Beispielseite unter `/content/sites/sample/en/jcr:content/content/primary/comments` anzeigen.

![chlimage_1-50](assets/chlimage_1-50.png)

### Beispielseite {#publish-sample-page} veröffentlichen

Nachdem die benutzerdefinierte Komponente der Seite hinzugefügt wurde, muss auch [die Seite ](sites-console.md#publishing-the-site) (erneut) veröffentlicht werden.

### Veröffentlichen: Alt-Kommentar auf Beispielseite {#publish-alt-comment-on-sample-page}

Nach der Veröffentlichung der benutzerdefinierten Anwendung und der Beispielseite sollte es möglich sein, einen Kommentar einzugeben. Bei der Anmeldung, entweder mit einem [demo-Benutzer](tutorials.md#demo-users) oder mit einem Admin, sollte es möglich sein, einen Kommentar zu posten.

Hier finden Sie aaron.mcdonald@mailinator.com zum Posten eines Kommentars:

![chlimage_1-51](assets/chlimage_1-51.png) ![chlimage_1-52](assets/chlimage_1-52.png)

Nun, da es so aussieht, als ob die erweiterte Komponente mit dem Standardaussehen korrekt funktioniert, ist es an der Zeit, das Erscheinungsbild zu ändern.

