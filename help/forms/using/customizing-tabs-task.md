---
title: Anpassen von Registerkarten für eine Aufgabe
seo-title: Customizing tabs for a task
description: Gehen Sie wie folgt vor, um die Namen der Registerkarten für Ihre Aufgaben in LiveCycle AEM Forms Workspace anzupassen.
seo-description: How-to customize the names of the tabs for your tasks, in LiveCycle AEM Forms workspace.
uuid: 77eabb63-f8ea-4ec0-8a41-b51c65cdecc0
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: ac0a281f-f589-4a70-9bc7-1a23e054b02f
exl-id: 42671435-e0f0-41db-af83-182b01742954
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '101'
ht-degree: 100%

---

# Anpassen von Registerkarten für eine Aufgabe {#customizing-tabs-for-a-task}

Sie können benutzerdefinierte Registerkartennamen für die `Start Process`-Komponente in der Uber-Ansicht von `Start Process` und für die `Task Details`-Komponente in der Uber-Ansicht von `ToDo` festlegen.

1. Befolgen Sie die [generischen Schritte zur Anpassung von AEM Forms Workspace](/help/forms/using/generic-steps-html-workspace-customization.md).
1. Ändern Sie den Wert von `tabname` in der Datei `translation.json`.

   Ändern Sie zum Beispiel für Englisch folgende Änderungen an „`/apps/ws/locales/en-US/translation.json`/“ vor.

   * Für Aufgaben, die im Startprozess initiiert werden, verwenden Sie folgenden Code-Ausschnitt aus dem Block `"startprocess" : {}`.

   ```
   "tabname" : {
               "form" : "Application",
               "details" : "Overview",
               "attachments" : "Attachments",
               "notes" : "Helper Notes"
           }
   ```

   * Für Aufgaben in „Aufgaben“ verwenden Sie folgenden Code-Ausschnitt aus dem Block `"todo" : {}`.

   ```
   "tabname" : {
               "summary" : "Bird's-eye view",
               "history" : "Past",
               "form" : "Form",
               "details" : "Overview",
               "attachments" : "Attachments",
               "notes" : "Notes"
   }
   ```

   >[!NOTE]
   >
   >Fügen Sie das entsprechende Schlüssel-Wert-Paar für alle unterstützten Sprachen hinzu.
