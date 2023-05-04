---
title: Erweitern der Kommentarkomponente
seo-title: Extend Comments Component
description: Erweitern Sie die Komponente Kommentare , um ihr Erscheinungsbild oder Verhalten für bestimmte Verwendungen zu ändern.
seo-description: Extend the Comments component to alter its appearance or behavior for specific uses
uuid: 6f439097-b1d0-4e7d-afcf-01d8f43aa866
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: a07a4690-0e47-4a76-84cb-96abdc70b835
exl-id: f6722953-ff71-4fba-b76e-1d566f71f6d5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 3%

---

# Erweitern der Kommentarkomponente {#extend-comments-component}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Die Absicht von [Erweiterung](client-customize.md#extensions) Eine Standardkomponente besteht darin, das Erscheinungsbild oder Verhalten einer Komponente für bestimmte Verwendungen zu ändern.

Der Pfad zur Komponente ist eindeutig und verweist auf die Standardkomponente als Superressourcentyp. Das Risiko ist geringer, da der Umfang im Vergleich zum globalen Umfang einer Komponentenüberlagerung begrenzt ist.

>[!NOTE]
>
>Erweitern einer [überlagert](client-customize.md#overlays) -Komponente wird nicht unterstützt.

## Beispiel {#example}

Angenommen, die Kopfzeile für die Kommentarkomponente muss auf einer Site der AEM-Instanz mit einem alternativen Erscheinungsbild angezeigt werden, während sie auf einer anderen Site mit der Standardanzeige angezeigt wird. Statt den Standardkommentar zu überlagern, wodurch die Kommentarkomponente für alle Instanzen geändert wird, ist eine bessere Lösung sicherzustellen, dass mehrere Kommentarkomponenten für die Verwendung auf verschiedenen Sites verfügbar sind.

Um diese Lösung zu implementieren, erstellen Sie eine neue Komponente, die die vorhandene Komponente erweitert (überschreibt) und das Handlebars-Skript ändert. Der Bereich der Site, der die neuen Kommentare verwendet, kann den erweiterten Bereich verwenden, während die Sites, die das standardmäßige Erscheinungsbild verwenden, davon nicht betroffen sind.

Die Kommentarkomponente ist tatsächlich eine von zwei Komponenten, die das Kommentarsystem enthalten. Daher müssen zwei Komponenten erweitert werden: *Kommentare* und *comment*. Das zu bearbeitende Skript befindet sich im Abschnitt *Kommentar *Komponente `header.hbs` -Datei, während die übergeordnete *Kommentare* -Komponente (das Kommentarsystem) ist, was ein Autor der Seite tatsächlich hinzufügt.

Um Kommentare zu erweitern, müssen Sie:

1. [Erstellen der Komponenten](extend-create-components.md)
1. [Hinzufügen von Kommentaren zur Beispielseite](extend-sample-page.md)
1. [Erscheinungsbild ändern](extend-alter-appearance.md)
