---
title: Anpassen der Aufgabendetailseite
seo-title: Customizing the task details page
description: Gehen Sie wie folgt vor, um die Aufgabendetailseite in AEM Forms Workspace anzupassen, um die Standardinformationen zu einer Aufgabe zu ändern.
seo-description: How-to customize the task details page in AEM Forms workspace to modify the default information displayed about a task.
uuid: d85fae55-8e66-4595-8560-5485622b6841
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 16e57cf6-aaa1-406d-a6ad-71ec60b15386
exl-id: de97e6f7-25bf-462b-b67d-0d3fbd86a321
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 35%

---

# Anpassen der Aufgabendetailseite {#customizing-the-task-details-page}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Die Aufgabendetailseite enthält Informationen zu einer Aufgabe und ihren Prozessen. Sie können jedoch die Aufgabendetailseite anpassen, um Informationen hinzuzufügen oder zu löschen.

Sie können der Aufgabendetailseite die folgenden Informationen hinzufügen:

* Im JSON-Objekt einer Aufgabe verfügbare Informationen (Abschnitt &quot;Aufgabe&quot;unter [AEM Forms Workspace JSON-Objektbeschreibung](/help/forms/using/html-workspace-json-object-description.md))
* Informationen, die im JSON-Objekt einer Prozessinstanz verfügbar sind (Abschnitt &quot;Prozessinstanz&quot;unter [AEM Forms Workspace JSON-Objektbeschreibung](/help/forms/using/html-workspace-json-object-description.md))

So passen Sie die Aufgabendetailseite an:

1. Folgen [Generische Schritte zur Anpassung von AEM Forms Workspace.](/help/forms/using/generic-steps-html-workspace-customization.md)
1. Wenn Sie zusätzliche Informationen anzeigen möchten, fügen Sie der Datei `translation.json` entsprechende Schlüssel-Wert-Paare an der Stelle `todo`-Block > `details`-Block > `app`-Block > [ `required`-Block] hinzu.

   Der [ `required`-Block] verweist auf verfügbare Blöcke, wie den task-Block für Aufgabeninformationen, den process-Block für Prozessinformationen und den currentpendingtask-Block für Informationen zu ausstehenden Aufgaben.

   Um beispielsweise Informationen zur Routenauswahl erforderlich auf der Aufgabendetailseite hinzuzufügen, können Sie das folgende Schlüssel-Wert-Paar zum Aufgabenblock hinzufügen:

   ```
   "todo" : {
       .
       .
       .
       "details" : {
           .
           .
           "task" : {
               .
               .
               "RouteSelectionRequired" : "Route Selection Required"
           }
       }
   }
   ```

   >[!NOTE]
   >
   >Fügen Sie entsprechende Schlüssel-Wert-Paare für alle unterstützten Sprachen hinzu.

1. Kopieren Sie `/libs/ws/js/runtime/templates/taskdetails.html` nach `/apps/ws/js/runtime/templates/taskdetails.html`.

   Fügen Sie die neuen Informationen zu `/apps/ws/js/runtime/templates/taskdetails.html` hinzu. Beispiel:

   ```css
   <div class="detailsContainer">
       .
       .
       <ul>
           .
           .
           <li>
               <label for="routeSelectionRequired" title="<%= $.t('todo.details.task.RouteSelectionRequired')%>"><%= $.t('todo.details.task.RouteSelectionRequired')%></label>
               <div>
                   <span id="routeSelectionRequired"><%= isRouteSelectionRequired != null ? isRouteSelectionRequired : ''%></span>
               </div>
           </li>
           .
           .
       </ul>
   </div>
   ```

1. Öffnen Sie /apps/ws/js/registry.js zur Bearbeitung.

   Suchen und ersetzen Sie `text!/lc/libs/ws/js/runtime/templates/taskdetails.html` durch `text!/lc/apps/ws/js/runtime/templates/taskdetails.html`.

>[!NOTE]
>
>Um die Aufgabendetailseite mit Aufgaben anzupassen, die auf der Registerkarte &quot;Startprozess&quot;in AEM Forms Workspace erstellt wurden, fügen Sie die neuen Informationen zu `/apps/ws/js/runtime/templates/startprocess.html`.
>
>Um neue Stile für die auf der Detailseite hinzugefügten Informationen hinzuzufügen, ändern Sie die CSS-Datei entsprechend dem Abschnitt *Änderungen der Benutzeroberfläche* in [Anpassung von Workspace](/help/forms/using/changing-locale-user-interface.md).
