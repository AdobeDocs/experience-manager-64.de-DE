---
title: Anpassen der Auflistung von Prozessinstanzen
seo-title: Customizing the listing of process instances
description: Gehen Sie wie folgt vor, um die Eigenschaften anzupassen, die in der Prozessinstanz in AEM Forms Workspace angezeigt werden.
seo-description: How-to customize the properties displayed in process instance in AEM Forms workspace.
uuid: 3b55d9b9-7f73-46dd-9eb6-42be218440a1
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 40d7d43f-ee0a-4e34-ae93-20c9c940f76b
exl-id: e7b8206c-bac2-48a6-b353-d06bc73b29f9
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 100%

---

# Anpassen der Auflistung von Prozessinstanzen {#customizing-the-listing-of-process-instances}

Die Prozessinstanzliste wird auf der Registerkarte „Verfolgung“ von AEM Forms Workspace angezeigt.

In der Prozessinstanzliste zeigt AEM Forms Workspace für jede Prozessinstanz einige Eigenschaften dieser Instanz. Die folgenden Eigenschaften sind für jede Prozessinstanz verfügbar. Diese Eigenschaften werden als Attribute im Prozessinstanz-Komponentenmodell gespeichert und sind in dessen Ansicht und Vorlage verfügbar.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Eigenschaft</strong></td> 
   <td><strong>Kommentare</strong></td> 
  </tr> 
  <tr> 
   <td>description</td> 
   <td>Beschreibung der Prozessinstanz</td> 
  </tr> 
  <tr> 
   <td>initiator</td> 
   <td>Name des Initiators der Prozessinstanz</td> 
  </tr> 
  <tr> 
   <td>initiatorId</td> 
   <td>ID des Initiators der Prozessinstanz</td> 
  </tr> 
  <tr> 
   <td>processCompleteTime</td> 
   <td>Zeitstempel zum Zeitpunkt, als der Vorgang abgeschlossen wurde.</td> 
  </tr> 
  <tr> 
   <td>processInstanceId</td> 
   <td>ID der Prozessinstanz</td> 
  </tr> 
  <tr> 
   <td>processInstanceStatus</td> 
   <td>0 = Initiiert<br />1 = Wird ausgeführt<br /> 2 = Abgeschlossen<br /> 3 = Wird abgeschlossen<br />4 = Beendet<br /> 5 = Wird beendet<br /> 6 = Ausgesetzt<br /> 7 = Wird ausgesetzt<br /> 8 = Aussetzen wird aufgehoben</td> 
  </tr> 
  <tr> 
   <td>processName</td> 
   <td>Der Name des Vorgangs</td> 
  </tr> 
  <tr> 
   <td>processStartTime</td> 
   <td>Zeitstempel zum Zeitpunkt, als der Prozess gestartet wurde.</td> 
  </tr> 
  <tr> 
   <td>processVariables</td> 
   <td>Array von Objekten aus Prozessvariablen Jedes Objekt einer Prozessvariable enthält <strong>name</strong> (den Namen der Prozessvariable), <strong>value</strong> (den Wert der Prozessvariable) und <strong>type</strong> (den Typ der Prozessvariable).</td> 
  </tr> 
 </tbody> 
</table>

**Beispiel:**

Um die Eigenschaft `description` der Prozessinstanz auf der Prozessinstanzkarte anzuzeigen, führen Sie die folgenden Schritte aus.

1. Befolgen Sie die [generischen Schritte zur Anpassung von AEM Forms Workspace](/help/forms/using/generic-steps-html-workspace-customization.md).
1. Gehen Sie folgendermaßen vor:

   1. Kopieren Sie /libs/ws/js/runtime/templates/processinstance.html nach /apps/ws/js/runtime/templates/, wenn es nicht existiert. Klicken Sie auf **Alle speichern**.
   1. Fügen Sie die Prozessbeschreibung div mit class = „processDescription“ in processinstance.html hinzu.

   ```
   <div class="processDescription" title="<%= description%>"><%= description%></div>
   ```

1. Gehen Sie folgendermaßen vor:

   1. Öffnen Sie /apps/ws/js/registry.js zur Bearbeitung.
   1. Suchen und Ersetzen `text!/lc/libs/ws/js/runtime/templates/processinstance.html`mit `text!/lc/`**apps**/ws/js/runtime/templates/processinstance.html

1. Die oben genannten Änderungen erfordern möglicherweise ein Update der CSS-Datei, indem Sie wie folgt einen Eintrag im Stylesheet /apps/ws/css/newStyle.css hinzufügen:

   ```css
   .processinstance .processDescription {
    <!--Dummy values, need to be configured by user as per requirement as well as user can add or delete any property depending upon requirement-->
       width : 250px;
       font-size : 11pt;
       padding : 2px;
   }
   ```
