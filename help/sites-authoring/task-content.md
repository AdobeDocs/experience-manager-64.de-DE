---
title: Arbeiten mit Aufgaben
seo-title: Working with Tasks
description: Aufgaben stellen Arbeitselemente dar, die an Inhalten zu erledigen sind, und werden in Projekten verwendet, um den Grad der Vollständigkeit aktueller Aufgaben zu bestimmen.
seo-description: Tasks represent items of work to be done on content and are used in projects to determine the level of completeness of current tasks
uuid: df4efb3f-8298-4159-acfe-305ba6b46791
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: projects
content-type: reference
discoiquuid: 1b79d373-73f4-4228-b309-79e74d191f3e
exl-id: 6480a0ba-ff65-42af-a14f-ce9fdbb7945f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '605'
ht-degree: 47%

---

# Arbeiten mit Aufgaben{#working-with-tasks}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Bei Aufgaben handelt es sich um Arbeitsschritte, die auf Inhalt ausgeführt werden. Wenn Ihnen eine Aufgabe zugewiesen wird, wird diese in Ihrem Workflow-Posteingang angezeigt. Aufgabenelemente enthalten in der Spalte &quot;Typ&quot;den Wert &quot;task&quot;.

Aufgaben werden auch in Projekten verwendet, um den Grad der Vollständigkeit aktueller Aufgaben, einschließlich Workflow-Aufgaben, zu bestimmen.

## Verfolgen des Projektfortschritts {#tracking-project-progress}

Sie können den Projektfortschritt verfolgen, indem Sie sich die aktiven/abgeschlossenen Aufgaben in einem Projekt ansehen, das durch die **Aufgaben** Kachel. Der Projektfortschritt kann durch Folgendes bestimmt werden:

* **Aufgabenkachel:** Ein Gesamtfortschritt des Projekts wird in der Aufgabenkachel dargestellt, die auf der Seite „Projektdetails“ verfügbar ist.

* **Aufgabenliste:** Beim Klicken auf die Aufgabenkachel wird eine Liste von Aufgaben angezeigt. Diese Liste enthält detaillierte Informationen zu allen Aufgaben in Zusammenhang mit dem Projekt.

Beide listen Workflow-Aufgaben sowie Aufgaben auf, die Sie direkt in der **Aufgaben** Kachel.

### Aufgabenkachel {#task-tile}

Wenn ein Projekt verwandte Aufgaben hat, wird innerhalb des Projekts eine Aufgabenkachel angezeigt. Die Aufgabenkachel zeigt den aktuellen Status des Projekts an. Die Anzeige basiert auf den vorhandenen Aufgaben innerhalb des Workflows und beinhaltet keine Aufgaben, die in der Zukunft erzeugt werden, während der Workflow fortgesetzt wird. Die folgenden Informationen sind in der Aufgabenkachel sichtbar:

* Prozentsatz der abgeschlossenen Aufgaben
* Prozentsatz der aktiven Aufgaben
* Prozentsatz der überfälligen Aufgaben

![chlimage_1-98](assets/chlimage_1-98.png)

### Anzeigen oder Ändern von Aufgaben in einem Projekt {#viewing-or-modifying-the-tasks-in-a-project}

Zusätzlich zur Verfolgung des Fortschritts möchten Sie vielleicht auch Informationen über das Projekt anzeigen oder es ändern.

#### Aufgabenliste {#task-list}

Klicken Sie auf das Auslassungszeichen (...) in der Aufgabenkachel, um die Liste der Aufgaben anzuzeigen, die mit dem Projekt verbunden sind. Die Aufgaben werden durch übergeordnete Workflows aufgeteilt. Die Aufgabendetails werden zusammen mit Metadaten wie Fälligkeitsdatum, Verantwortlicher, Priorität und Status angezeigt.

![chlimage_1-99](assets/chlimage_1-99.png)

#### Aufgabendetails {#task-details}

Tippen/klicken Sie für weitere Informationen über eine bestimmte Aufgabe in der Aufgabenliste auf die Aufgabe und öffnen Sie „Aufgabendetails“.

![chlimage_1-100](assets/chlimage_1-100.png)

### Anzeigen und Ändern von Aufgabenkommentaren {#viewing-and-modifying-task-comments}

In Aufgabendetails können Sie Kommentare bearbeiten oder hinzufügen. Darüber hinaus sind alle Kommentare in einem Projekt im Bereich Kommentare sichtbar.

![chlimage_1-101](assets/chlimage_1-101.png)

### Hinzufügen von Aufgaben {#adding-tasks}

Sie können Projekten neue Aufgaben hinzufügen. Diese Aufgaben werden dann in der Kachel Aufgaben angezeigt und stehen im Benachrichtigungs-Posteingang zur Durchführung von Aktionen zur Verfügung.

So fügen Sie eine Aufgabe hinzu:

1. Tippen/Klicken Sie im Projekt in der Kachel **Aufgaben** auf das Plussymbol (+). Das Fenster **Aufgabe hinzufügen** wird geöffnet.
1. Geben Sie Informationen zur Aufgabe ein. Der Titel der Aufgabe und die Gruppe, der sie zugewiesen ist, sind obligatorisch. Zusätzliche Informationen wie der Inhaltspfad, die Beschreibung, die Aufgabenpriorität und das Fälligkeitsdatum sind optional. Darüber hinaus können Sie die **Erweitert** um den Namen der Aufgabe einzugeben, die zum Benennen der URL verwendet wird.

   ![chlimage_1-102](assets/chlimage_1-102.png)

1. Tippen oder klicken Sie auf **Erstellen**.

## Arbeiten mit Aufgaben im Posteingang {#working-with-tasks-in-the-inbox}

Eine andere Möglichkeit, auf Aufgaben zuzugreifen, bietet der Posteingang. Sie können den Inhalt aus dem Posteingang öffnen, um die erforderlichen Änderungen vorzunehmen. Wenn Sie fertig sind, ändern Sie den Aufgabenstatus in „Fertig gestellt“. Aufgaben werden auch in Ihrem Posteingang angezeigt, wenn sie einer Benutzergruppe zugewiesen werden, der Sie angehören. In diesem Fall kann jedes Mitglied der Gruppe die Arbeit durchführen und die Aufgabe abschließen.

![chlimage_1-103](assets/chlimage_1-103.png)

Um eine Aufgabe abzuschließen, wählen Sie die Aufgabe aus und klicken Sie auf **Fertig**. Fügen Sie Informationen zur Aufgabe hinzu und klicken Sie auf **Fertig**. Siehe [Ihr Posteingang](/help/sites-authoring/inbox.md) für weitere Informationen.

![chlimage_1-104](assets/chlimage_1-104.png)
