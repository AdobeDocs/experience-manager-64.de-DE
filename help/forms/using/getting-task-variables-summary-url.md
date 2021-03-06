---
title: Aufrufen von Aufgabenvariablen in der Zusammenfassungs-URL
seo-title: Getting Task Variables in Summary URL
description: Gehen Sie wie folgt vor, um die Informationen zu einer Aufgabe erneut zu verwenden und eine Zusammenfassungs-URL für die Zusammenfassung oder Beschreibung einer Aufgabe zu generieren.
seo-description: How-to reuse the information about a task and generate a Summary URL to summarize or describe a task.
uuid: 9eab3a6a-a99a-40ae-b483-33ec7d21c5b6
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 6dc31bec-b02d-47db-a4f4-be8c14c5619e
exl-id: f80d006b-6970-4448-aa38-3ffec8b08c18
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 91%

---

# Aufrufen von Aufgabenvariablen in der Zusammenfassungs-URL {#getting-task-variables-in-summary-url}

Auf der Zusammenfassungsseite werden aufgabenbezogene Informationen angezeigt. Dieser Artikel beschreibt, wie Sie aufgabenbezogene Informationen auf der Zusammenfassungssseite wiederverwenden können.

In dieser Beispielorchestrierung reicht ein Mitarbeiter ein Urlaubsantragsformular ein. Das Antragsformular geht dann zur Genehmigung an den Manager des Mitarbeiters.

1. Erstellen Sie einen Beispiel-HTML-Renderer (html.esp) für resourseType **Employees/PtoApplication**.

   Der Renderer setzt voraus, dass die folgenden Eigenschaften für den Knoten festgelegt wurden:

   * ename
   * empid
   * reason
   * duration

   >[!NOTE]
   >
   >Dieser Renderer stellt die Übersichtsseitenvorlage dar.

   Der folgende Beispielcode für diesen Renderer ist enthalten in:

   `apps/Employees/PtoApplication/html.esp`

   ```
   <html>
     <body>
       <table>
       <tbody>
       <tr>
           <td>
               <h3>Employee Name: <%= currentNode.ename %></h3>
               <h3>Employee ID: <%= currentNode.eid %></h3>
               <h3>Leave duration: <%= currentNode.duration %> days</h3>
               <h3>Reason: <%= currentNode.reason %></h3>
           </td>
       </tr>
       </tbody>
       </table>
     </body>
   </html>
   ```

1. Ändern Sie die Orchestrierung, um die vier Eigenschaften aus den übermittelten Formulardaten zu extrahieren. Anschließend erstellen Sie in CRX einen Knoten vom Typ **Employees/PtoApplication**, für den die Eigenschaften ausgefüllt sind.

   1. Erstellen Sie einen Prozess **create PTO summary** und verwenden Sie diesen als Teilprozess vor dem **Assign Task**-Vorgang in der Orchestrierung.
   1. Definieren Sie **employeeName**, **employeeID**, **ptoReason**, **totalDays** und **nodeName** als Eingabevariablen in dem neuen Prozess. Diese Variablen werden als gesendete Formulardaten übergeben.

      Definieren Sie außerdem eine Ausgabevariable **ptoNodePath**, die beim Festlegen der Zusammenfassungs-URL verwendet wird.

   1. Im **PTO-Zusammenfassung erstellen** -Prozess verwenden, verwenden Sie die **set value** Komponente zum Festlegen der Eingabedetails in einer **nodeProperty **(**nodeProps**) zuordnen.

      Die Schlüssel in dieser Zuordnung müssen identisch mit den Schlüsseln sein, die in Ihrem HTML-Renderer im vorherigen Schritt definiert wurden.

      Fügen Sie in der Zuordnung außerdem einen Schlüssel **sling:resourceType** mit dem Wert **Employees/PtoApplication** hinzu.

   1. Verwenden Sie den Teilprozess **storeContent** aus dem **ContentRepositoryConnector**-Dienst im Prozess **create PTO summary**. Dieser Teilprozess erstellt einen CRX-Knoten.

      Er akzeptiert drei Eingabevariablen:

      * **Ordnerpfad**: Der Pfad, in dem der neue CRX-Knoten erstellt wird. Legen Sie den Pfad auf **/content** fest.
      * **Knotenname**: Weisen Sie diesem Feld die Eingabevariable nodeName zu. Dies ist eine eindeutige Knotennamen-Zeichenfolge.
      * **Knotentyp**: Definieren Sie den Typ als **nt:unstructured**. Die Ausgabe dieses Prozesses ist nodePath. NodePath ist der CRX-Pfad des neu erstellten Knotens. NodePath stellt die endgültige Ausgabe des Prozesses **create PTO summary** dar.
   1. Übergeben Sie die gesendeten Formulardaten (**employeeName**, **employeeID**, **ptoReason** und **totalDays**) als Eingabe für den neuen Prozess **create PTO summary**. Übernehmen Sie die Ausgabe als **ptoSummaryNodePath**.


1. Definieren Sie die Zusammenfassungs-URL als XPath-Ausdruck, der die Serverdetails zusammen mit **ptoSummaryNodePath** enthält.

   XPath: `concat('https://[*server*]:[*port*]/lc',/process_data/@ptoSummaryNodePath,'.html')`.

Wenn Sie in AEM Forms Workspace eine Aufgabe öffnen, greift die Zusammenfassungs-URL auf den CRX-Knoten zu und der HTML-Renderer zeigt die Zusammenfassung an.

Das Zusammenfassungs-Layout kann geändert werden, ohne den Prozess zu ändern. Der HTML-Renderer zeigt die Zusammenfassung entsprechend an.
