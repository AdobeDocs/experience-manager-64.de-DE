---
title: Anzeigen zusätzlicher Daten in der Aufgabenliste
seo-title: Displaying additional data in ToDo list
description: Gehen Sie wie folgt vor, um die Anzeige der Aufgabenliste von LiveCycle AEM Forms Workspace anzupassen und neben dem Standard weitere Informationen anzuzeigen.
seo-description: How-to customize the display of the To-do list of LiveCycle AEM Forms workspace to show more information besides the default.
uuid: 4c678d9c-7794-4b62-8705-d62c7780c13f
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: b74a0933-2b96-4a88-9995-6fb21df141aa
exl-id: 42d8472d-0eab-4cf9-a7c3-bf2775ee6bec
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 32%

---

# Anzeigen zusätzlicher Daten in der Aufgabenliste {#displaying-additional-data-in-todo-list}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Standardmäßig zeigt die Aufgabenliste von AEM Forms Workspace den Anzeigenamen und die Beschreibung der Aufgabe an. Sie können jedoch weitere Informationen wie Erstellungsdatum und Termin hinzufügen. Sie können auch Symbole hinzufügen und den Stil der Anzeige ändern.

![Abbildung der Registerkarte „Aufgaben“ von HTML Workspace mit der Standardkonfiguration](assets/html-todo-list.png)

In diesem Artikel werden die Schritte zum Hinzufügen von Informationen beschrieben, die für jede Aufgabe in der ToDo-Liste angezeigt werden sollen.

## Was kann hinzugefügt werden? {#what-can-be-added}

Sie können die verfügbaren Informationen der Datei in `task.json` hinzufügen, die vom Server gesendet wurde. Die Informationen können als normaler Text hinzugefügt werden oder Sie können Stile verwenden, um die Informationen zu formatieren.

Weitere Informationen zur JSON-Objektbeschreibung finden Sie unter [this](/help/forms/using/html-workspace-json-object-description.md) Artikel.

## Anzeigen von Informationen zu einer Aufgabe {#displaying-information-on-a-task}

1. Befolgen Sie die [generischen Schritte zur Anpassung von AEM Forms Workspace](/help/forms/using/generic-steps-html-workspace-customization.md).
1. Um zusätzliche Information für eine Aufgabe anzuzeigen, müssen die entsprechenden Schlüssel-Wert-Paare innerhalb des Aufgabenblocks von `translation.json` hinzugefügt werden.

   Ändern Sie zum Beispiel `/apps/ws/locales/en-US/translation.json` für Englisch:

   ```
   "task" : {
           "reminder" : {
               "value" : "Reminder",
               "tooltip" : "This is reminder __reminderCount__, for this task."
           },
           "deadlined" : {
               "value" : "Deadlined",
               "tooltip" : "This task has deadlined"
           },
           "save" : {
               "message" : "Task has been saved successfully"
           },
           "status" : {
               "deadlined" : "Deadlined",
               "created" : "Created",
               "assignedsaved" : "Draft from assigned task",
               "terminated" : "Terminated",
               "assigned" : "Assigned",
               "unknown" : "Unknown",
               "createdsaved" : "Draft from created task",
               "completed" : "Completed"
           },
           "draft" : {
               "value" : "Saved",
               "tooltip" : "This task is marked as a draft"
           },
           "escalated" : {
               "value" : "Escalated",
               "tooltip" : "This task has been escalated"
           },
           "forward" : {
               "value" : "Forwarded",
               "tooltip" : "This task was forwarded"
           },
           "priority" : {
               "highest" : "Highest priority",
               "normal" : "Normal priority",
               "high" : "High priority",
               "low" : "Low priority",
               "lowest" : "Lowest priority"
           },
           "claimed" : {
               "value" : "Claimed",
               "tooltip" : "This task has been claimed"
           },
           "locked" : {
               "value" : "Locked",
               "tooltip" : "This task is locked"
           },
           "consulted" : {
               "value" : "Consulted",
               "tooltip" : "This task has been consulted"
           },
           "returned" : {
               "value" : "Returned",
               "tooltip" : "This task was returned back"
           },
           "multiplesubmitbuttons" : {
               "message" : "The form associated with this task has multiple submit buttons so the Workspace Complete button will be disabled. Click the appropriate button on the form to submit it."
           },
           "nosubmitbutton" : {
               "message" : "The form associated with this task does not appear to have submit buttons. You may need to upgrade your Adobe Reader version to 9.1 or greater and enable the Reader Submit option in your process."
           },
           "icon" : {
               "tooltip" : "open the task __taskName__"
           }
       }
   ```

   >[!NOTE]
   >
   >Fügen Sie entsprechende Schlüssel-Wert-Paare für alle unterstützten Sprachen hinzu.

1. Fügen Sie beispielsweise Informationen innerhalb des Aufgabenblocks hinzu:

   ```
   "stepname" : {
               "value" : "Step Name",
               "tooltip" : "This task belongs to __stepName__ step"
   }
   ```

## Definieren von CSS für die neue Eigenschaft {#defining-css-for-the-new-property}

1. Sie können einen Stil auf die Informationen (Eigenschaft) anwenden, die einer Aufgabe hinzugefügt werden. Dazu müssen Sie Stilinformationen für die neue Eigenschaft hinzufügen, die `/apps/ws/css/newStyle.css` hinzugefügt wurde.

   Fügen Sie beispielsweise hinzu:

   ```css
   .task .taskProperties .stepname{
       width: 25px;
       background: url(../images/stepname.png) no-repeat; /*-------- Or just reuse background image / image-sprite defined .task .taskProperties span of style.css---------------------*/
       background-position: 0px 0px; /*-------- Dummy values, need to be configured as per user background image / image-sprite ---------------------*/
   }
   ```

## Eintrag in der HTML-Vorlage hinzufügen {#adding-entry-in-the-html-template}

Schließlich müssen Sie für jede Eigenschaft, die Sie der Aufgabe hinzufügen möchten, einen Eintrag in das Dev-Paket aufnehmen. Informationen zum Erstellen eines Workflows finden Sie unter Erstellen von AEM Forms Workspace-Code .

1. Kopieren `task.html`:

   * von: `/libs/ws/js/runtime/templates/`
   * in: `/apps/ws/js/runtime/templates/`

1. Fügen Sie `/apps/ws/js/runtime/templates/task.html` die neuen Informationen hinzu.

   Fügen Sie beispielsweise Folgendes unter `div class="taskProperties"` hinzu:

   ```
   <span class="stepname" alt="<%= $.t('task.stepname.value')%>" title = '<%= $.t("task.stepname.tooltip",{stepName:stepName})%>'/>
   ```
