---
title: Abrufen von Aufgabenvariablen in der Zusammenfassungs-URL
seo-title: Getting Task Variables in Summary URL
description: Gehen Sie wie folgt vor, um die Informationen zu einer Aufgabe wiederzuverwenden und eine Zusammenfassungs-URL zu generieren, um eine Aufgabe zusammenzufassen oder zu beschreiben.
seo-description: How-to reuse the information about a task and generate a Summary URL to summarize or describe a task.
uuid: 9eab3a6a-a99a-40ae-b483-33ec7d21c5b6
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 6dc31bec-b02d-47db-a4f4-be8c14c5619e
exl-id: f80d006b-6970-4448-aa38-3ffec8b08c18
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 16%

---

# Abrufen von Aufgabenvariablen in der Zusammenfassungs-URL {#getting-task-variables-in-summary-url}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Auf der Zusammenfassungsseite werden aufgabenbezogene Informationen angezeigt. In diesem Artikel wird beschrieben, wie Sie aufgabenbezogene Informationen auf der Zusammenfassungsseite wiederverwenden können.

In dieser Beispielorchestrierung sendet ein Mitarbeiter ein Urlaubsantragsformular. Das Antragsformular wird dann zur Genehmigung an den Vorgesetzten des Mitarbeiters weitergeleitet.

1. Erstellen eines HTML-Renderers (html.esp) für resourceType **Employees/PtoApplication**.

   Der Renderer geht davon aus, dass die folgenden Eigenschaften für den Knoten festgelegt werden:

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

1. Ändern Sie die Orchestrierung, um die vier Eigenschaften aus den gesendeten Formulardaten zu extrahieren. Erstellen Sie anschließend einen Knoten des Typs CRX . **Employees/PtoApplication**, wobei die Eigenschaften ausgefüllt sind.

   1. Erstellen eines Prozesses **PTO-Zusammenfassung erstellen** und verwenden Sie dies als Teilprozess vor dem **Aufgabe zuweisen** -Operation in Ihrer Orchestrierung.
   1. Definieren Sie **employeeName**, **employeeID**, **ptoReason**, **totalDays** und **nodeName** als Eingabevariablen in dem neuen Prozess. Diese Variablen werden als gesendete Formulardaten übergeben.

      Definieren Sie außerdem eine Ausgabevariable **ptoNodePath**, die beim Festlegen der Zusammenfassungs-URL verwendet wird.

   1. Im **PTO-Zusammenfassung erstellen** -Prozess verwenden, verwenden Sie die **set value** Komponente zum Festlegen der Eingabedetails in einer **nodeProperty **(**nodeProps**) zuordnen.

      Die Schlüssel in dieser Zuordnung sollten mit den Schlüsseln übereinstimmen, die im vorherigen Schritt im HTML-Renderer definiert wurden.

      Fügen Sie außerdem eine **sling:resourceType** Schlüssel mit Wert **Employees/PtoApplication** in der Karte.

   1. Teilprozess verwenden **storeContent** von **ContentRepositoryConnector** im **PTO-Zusammenfassung erstellen** Prozess. Dieser Teilprozess erstellt einen CRX-Knoten.

      Es sind drei Eingabevariablen erforderlich:

      * **Ordnerpfad**: Der Pfad, in dem der neue CRX-Knoten erstellt wird. Legen Sie den Pfad als **/content**.
      * **Knotenname**: Weisen Sie diesem Feld die Eingabevariable nodeName zu. Dies ist eine eindeutige Knotennamen-Zeichenfolge.
      * **Knotentyp**: Definieren Sie den Typ als **nt:unstructured**. Die Ausgabe dieses Prozesses ist nodePath. Der nodePath ist der CRX-Pfad des neu erstellten Knotens. NodePath ist die endgültige Ausgabe der **PTO erstellen** Zusammenfassungsprozess.
   1. Übergeben Sie die gesendeten Formulardaten (**employeeName**, **employeeID**, **ptoReason** und **totalDays**) als Eingabe für den neuen Prozess **PTO-Zusammenfassung erstellen**. Nehmen Sie die Ausgabe als **ptoSummaryNodePath**.


1. Definieren Sie die Zusammenfassungs-URL als XPath-Ausdruck, der die Serverdetails zusammen mit **ptoSummaryNodePath**.

   XPath: `concat('https://[*server*]:[*port*]/lc',/process_data/@ptoSummaryNodePath,'.html')`.

Wenn Sie in AEM Forms Workspace eine Aufgabe öffnen, greift die Zusammenfassungs-URL auf den CRX-Knoten zu und der HTML-Renderer zeigt die Zusammenfassung an.

Das Zusammenfassungslayout kann geändert werden, ohne den Prozess zu ändern. Der HTML-Renderer zeigt die Zusammenfassung entsprechend an.
