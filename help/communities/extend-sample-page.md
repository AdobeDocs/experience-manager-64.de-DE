---
title: Hinzufügen von Kommentaren zur Beispielseite
seo-title: Hinzufügen von Kommentaren zur Beispielseite
description: Hinzufügen benutzerdefinierter Kommentare zu einer Seite
seo-description: Hinzufügen benutzerdefinierter Kommentare zu einer Seite
uuid: 7dbaff4f-9986-435d-9379-7add676ea254
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 7185fb13-46a2-4fa3-aa21-a51e63cdb9be
exl-id: 96ef7e58-66c9-4985-973b-0c6fc7c39fd5
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# Kommentar zur Beispielseite hinzufügen {#add-comment-to-sample-page}

Nachdem die Komponenten für das benutzerdefinierte Kommentarsystem im Anwendungsverzeichnis (/apps) vorhanden sind, können Sie die erweiterte Komponente verwenden. Die Instanz des Kommentarsystems auf einer Website, auf die sich die Auswirkungen auswirken sollen, muss ihren resourceType als benutzerdefiniertes Kommentarsystem festlegen und alle erforderlichen Client-Bibliotheken einschließen.

## Erforderliche Clientlibs identifizieren {#identify-required-clientlibs}

Die Client-Bibliotheken, die für den Stil und die Funktionsweise der Standardkommentare erforderlich sind, sind auch für erweiterte Kommentare erforderlich.

Im [Community Components Guide](components-guide.md) werden die erforderlichen Client-Bibliotheken identifiziert. Navigieren Sie zum Komponentenleitfaden und zeigen Sie die Komponente Kommentare an, z. B.:

[http://localhost:4502/content/community-components/en/comments.html](http://localhost:4502/content/community-components/en/comments.html)

Beachten Sie die drei Client-Bibliotheken, die erforderlich sind, damit Kommentare gerendert und ordnungsgemäß funktioniert. Diese müssen eingeschlossen werden, wenn auf die erweiterten Kommentare verwiesen wird, sowie die Client-Bibliothek [erweiterter Kommentare](extend-create-components.md#create-a-client-library-folder) ( `apps.custom.comments`).

![chlimage_1-47](assets/chlimage_1-47.png)

## Hinzufügen benutzerdefinierter Kommentare zu einer Seite {#add-custom-comments-to-a-page}

Da es pro Seite nur ein Kommentarsystem geben kann, ist es einfacher, eine Beispielseite zu erstellen, wie im kurzen Tutorial [Erstellen einer Beispielseite](create-sample-page.md) beschrieben.

Wechseln Sie nach der Erstellung in den Designmodus und stellen Sie die benutzerdefinierte Komponentengruppe bereit, damit die Komponente `Alt Comments` zur Seite hinzugefügt werden kann.

Damit der Kommentar angezeigt und ordnungsgemäß funktioniert, müssen die Client-Bibliotheken für Kommentare zur Clientlibsliste für die Seite hinzugefügt werden (siehe [Clientlibs für Communities-Komponenten](clientlibs.md)).

### Kommentare zu Clientlibs auf Beispielseite {#comments-clientlibs-on-sample-page}

![Kommentare zu Clientlibs auf Beispielseite](assets/chlimage_1-48.png)

### Autor: Alt-Kommentar auf Beispielseite {#author-alt-comment-on-sample-page}

![Alt-Kommentar auf Beispielseite](assets/chlimage_1-49.png)

### Autor: Beispiel-Seiten-Kommentar-Knoten {#author-sample-page-comments-node}

Sie können den resourceType in CRXDE überprüfen, indem Sie die Eigenschaften des Kommentarknotens für die Beispielseite unter `/content/sites/sample/en/jcr:content/content/primary/comments` anzeigen.

![chlimage_1-50](assets/chlimage_1-50.png)

### Beispielseite für Veröffentlichungen {#publish-sample-page}

Nachdem die benutzerdefinierte Komponente zur Seite hinzugefügt wurde, ist es auch erforderlich, die Seite [zu veröffentlichen](sites-console.md#publishing-the-site).

### Veröffentlichen: Alt-Kommentar auf Beispielseite {#publish-alt-comment-on-sample-page}

Nach der Veröffentlichung des benutzerdefinierten Programms und der Beispielseite sollte es möglich sein, einen Kommentar einzugeben. Wenn Sie angemeldet sind, entweder mit einem [Demobenutzer](tutorials.md#demo-users) oder Administrator, sollte es möglich sein, einen Kommentar zu posten.

Hier aaron.mcdonald@mailinator.com posten Sie einen Kommentar:

![chlimage_1-51](assets/chlimage_1-51.png) ![chlimage_1-52](assets/chlimage_1-52.png)

Nachdem sich herausstellt, dass die erweiterte Komponente ordnungsgemäß mit dem standardmäßigen Erscheinungsbild funktioniert, ist es an der Zeit, das Erscheinungsbild zu ändern.
