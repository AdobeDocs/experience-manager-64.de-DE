---
title: Anzeigen von Informationen in der Aufgabenzusammenfassung
seo-title: Displaying information in the Task Summary pane
description: In AEM Forms Workspace kann ein Bereich "Aufgabenzusammenfassung"konfiguriert werden, um die Aufgabe zusammenzufassen oder eine beliebige andere Webseite anzuzeigen.
seo-description: In AEM Forms workspace, a Task Summary pane can be configured to summarize the task or display any other web page.
uuid: 2fcc3d9f-0ec2-4250-8dc1-9746fd72ea60
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 90d0f584-b598-4b21-85d7-31da5f13d404
exl-id: cb9de2d7-04ad-4221-8db7-403464c9888b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 41%

---

# Anzeigen von Informationen in der Aufgabenzusammenfassung {#displaying-information-in-the-task-summary-pane}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Wenn Sie eine Aufgabe in AEM Forms Workspace öffnen, kann ein Bereich &quot;Aufgabenzusammenfassung&quot;eine Zusammenfassung der Aufgabe anzeigen. Diese zusätzlichen und relevanten Informationen für eine Aufgabe bieten dem Endbenutzer von AEM Forms Workspace einen Mehrwert.

AEM Forms Workspace gibt Ihnen die Möglichkeit, eine Web-Seite zu wählen, die in der Aufgabenzusammenfassung angezeigt werden soll. Es kann ein Vorgang erstellt werden, um eine Aufgabenzusammenfassung mithilfe von Workbench anzuzeigen.

1. Erstellen Sie einen Prozess &quot;Assign Task&quot;in Workbench. Weitere Informationen zum Vorgang &quot;Assign Task&quot;finden Sie unter Dienstreferenz-Thema unter [Workbench-Hilfe](https://help.adobe.com/de_DE/AEMForms/6.1/WorkbenchHelp/).

   >[!NOTE]
   >
   >Wenn eine TaskSummary-URL vorhanden ist, wird die Ansicht &quot;Task Summary&quot;standardmäßig anstelle der Ansicht &quot;Form&quot;geöffnet. In diesem Fall wird das Formular nicht im maximierten Modus geöffnet, selbst wenn ein Benutzer die Option &quot;Formular im maximierten Modus öffnen&quot;in &quot;Aufgabe zuweisen&quot;aktiviert hat.

1. Konfigurieren Sie das Feld &quot;Aufgabenzusammenfassungs-URL&quot;. Sie können einen Literalwert, eine Vorlage, eine Variable oder einen XPath-Ausdruck angeben.
1. Nachfolgend finden Sie ein Beispiel für die Anzeige der Informationen auf der Seite &quot;Aufgabenzusammenfassung&quot;.

   * Melden Sie sich bei der CRXDE Lite-Umgebung unter `https://[server]:[port]/lc/crx/de` an.
   * `Create a node`**SampleSummary** ` under `/content` with type `nt:unstructured`. In the properties of this node, add `sling:resourceType` of type String and value `SampleSummary`. In the Access Control List of this node, add an entry for `PERM_WORKSPACE_USER` allowing `jcr:read` privileges.`
   * `Create a folder`**SampleSummary** unter `/apps`. Fügen Sie in der Zugriffssteuerungsliste von `/apps/SampleSummary` einen Eintrag für `PERM_WORKSPACE_USER` hinzu, wobei die Berechtigungen `jcr:readprivileges` zugelassen werden.
   * `Create a file `html.esp` at `/apps/SampleSummary`. For example, add the following lines in `html.esp`.`

   ```
   <html>
       <body>
           <h1>Sample Summary</h1>
           <br/>
           <p>Hello Sir!
               <br/>
               This is sample summary page for this task.
           </p>
       </body>
   </html>
   ```

   * Legen Sie im Schritt „Aufgabe zuweisen“ den Wert der Aufgabenzusammenfassungs-URL auf `/lc/content/SampleSummary.html` fest.
   * Wenn die Aufgabe, die mit diesem Schritt „Aufgabe zuweisen“ verknüpft ist, in AEM Forms Workspace geöffnet wird, wird `html.esp` in `/apps/SampleSummary` in der Aufgabenzusammenfassung gerendert.
