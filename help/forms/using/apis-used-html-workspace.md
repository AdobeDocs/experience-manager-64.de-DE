---
title: APIs im AEM Forms-arbeitsbereich
seo-title: APIs used in AEM Forms workspace
description: Öffentliche Java- und JavaScript-APIs und Methoden von LiveCycle AEM Forms Workspace zur Anpassung und Automatisierung.
seo-description: Public Java and JavaScript APIs and methods of LiveCycle AEM Forms workspace, exposed for customization and automation.
uuid: 9602990e-8ac7-42eb-b507-50b3594055ba
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 4a73a973-fccf-466b-b4a0-47652a14a080
exl-id: 1d74fdb9-c118-45f7-93c6-116cacb2f1c4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1033'
ht-degree: 4%

---

# APIs im AEM Forms-arbeitsbereich {#apis-used-in-aem-forms-workspace}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Die folgenden APIs werden in AEM Forms Workspace verwendet.

<table> 
 <tbody>
  <tr>
   <td><strong>JavaScript-Methode</strong></td> 
   <td><strong>Service-Name</strong></td> 
   <td><strong>API-Name</strong></td> 
   <td><strong>Kommentare</strong></td> 
  </tr>
  <tr>
   <td>getGroups</td> 
   <td>ProcessManagementUserProxyService</td> 
   <td>getGroups</td> 
   <td>Sucht nach Gruppen. Gibt eine Liste aller Gruppen zurück, wenn nichts angegeben ist. Andernfalls werden Gruppen mit dem angegebenen Namen zurückgegeben.</td> 
  </tr>
  <tr>
   <td>getUsersAndGroups</td> 
   <td>ProcessManagementUserProxyService</td> 
   <td>getUsersAndGroups</td> 
   <td>Sucht Benutzer und Gruppen. Wenn nichts angegeben ist, wird eine Liste aller Benutzer und Gruppen zurückgegeben. Andernfalls werden Benutzer und Gruppen mit dem angegebenen Namen zurückgegeben.</td> 
  </tr>
  <tr>
   <td>prepareForSubmit</td> 
   <td>ProcessManagementDocumentHandlingService</td> 
   <td>prepareForSubmit</td> 
   <td>Sie wird aufgerufen, bevor das Formular über DocumentSubmitServlet gesendet wird. Legt die Aufgaben-ID in einer Sitzungsvariablen fest (zusammen mit der Ablaufzeit), die beim tatsächlichen Senden abgerufen wird.</td> 
  </tr>
  <tr>
   <td>submitTask</td> 
   <td>ProcessManagementDocumentHandlingService</td> 
   <td>absenden</td> 
   <td>Sendet das Dokumentobjekt, das mit einer Aufgabe verknüpft ist (und der Sendeprozess wiederum).</td> 
  </tr>
  <tr>
   <td>getRootEndpointCategories</td> 
   <td>ProcessManagementStartpointService</td> 
   <td>getRootEndpointCategories</td> 
   <td>Ruft alle Stammkategorien ab, die auf dem Server vorhanden sind.</td> 
  </tr>
  <tr>
   <td>getDirectChildCategories</td> 
   <td>ProcessManagementStartpointService</td> 
   <td>getDirectChildCategories2</td> 
   <td>Ruft alle direkten untergeordneten Elemente für eine Kategorie ab.</td> 
  </tr>
  <tr>
   <td>getAllStartpoints</td> 
   <td>ProcessManagementStartpointService</td> 
   <td>getAllStartpoints</td> 
   <td>Ruft alle Startpunkte ab, die auf dem Server unter allen Kategorien vorhanden sind.</td> 
  </tr>
  <tr>
   <td>invokeStartpoint</td> 
   <td>ProcessManagementStartpointService</td> 
   <td>invokeStartpoint</td> 
   <td>Dadurch wird ein Startpunkt aufgerufen und eine neue Aufgabe erstellt, die einem Startpunkt entspricht</td> 
  </tr>
  <tr>
   <td>getAllTasks</td> 
   <td>ProcessManagementTaskService</td> 
   <td>getAllActionableTasks</td> 
   <td>Ruft alle Aufgaben ab, die für den angemeldeten Benutzer erstellt und weitergeleitet, gespeichert, zugewiesen, zugewiesen und gespeichert werden.</td> 
  </tr>
  <tr>
   <td>getTask</td> 
   <td>ProcessManagementTaskService</td> 
   <td>getTask</td> 
   <td>Ruft eine bestimmte Aufgabe ab.</td> 
  </tr>
  <tr>
   <td>renderTask</td> 
   <td>ProcessManagementTaskService</td> 
   <td>render</td> 
   <td>Gibt eine Aufgabe wieder und gibt bei Bedarf Informationen zurück, die zum Rendern von Formularen erforderlich sind, z. B. Formular-URL, Formulartyp, Daten-URL usw.</td> 
  </tr>
  <tr>
   <td>submitWithPriorData</td> 
   <td>ProcessManagementTaskService</td> 
   <td>submitWithPriorData</td> 
   <td>Es wird das Ergebnis der Senden-API von TaskManager mithilfe des Ergebnisschlüssels zurückgegeben.</td> 
  </tr>
  <tr>
   <td>submitWithData</td> 
   <td>ProcessManagementTaskService</td> 
   <td>submitWithData</td> 
   <td>Sendet die mit der Aufgabe verknüpften Formulardaten (übergeben als Zeichenfolge) mithilfe der Senden-API von TaskManager. Sie wird für Flex-Formulare verwendet, die nicht die Senden-API von TaskManager aufrufen.</td> 
  </tr>
  <tr>
   <td>Speichern</td> 
   <td>ProcessManagementTaskService</td> 
   <td>Speichern</td> 
   <td>Speichert eine Aufgabe auf dem Server.</td> 
  </tr>
  <tr>
   <td>complete</td> 
   <td>ProcessManagementTaskService</td> 
   <td>complete</td> 
   <td>Er schließt eine Aufgabe ab und die Aufgabe wird gemäß dem Prozessentwurf an den nächsten Schritt übergeben.</td> 
  </tr>
  <tr>
   <td>getAttachment</td> 
   <td>ProcessManagementTaskService</td> 
   <td>getAttachment</td> 
   <td>Gibt die URL einer Anlage zurück, in der eine Anlage verfügbar ist.</td> 
  </tr>
  <tr>
   <td>getAllAttachments</td> 
   <td>ProcessManagementTaskService</td> 
   <td>getAllActionableAttachments</td> 
   <td>Ruft alle Anlagen und Notizen für eine Aufgabe ab.</td> 
  </tr>
  <tr>
   <td>Netzwerkfreigabe,</td> 
   <td>ProcessManagementTaskService</td> 
   <td>Netzwerkfreigabe,</td> 
   <td>Teilt eine Aufgabe mit einem anderen Benutzer. Ein anderer Benutzer kann die Aufgabe anfordern und wird Eigentümer der Aufgabe.</td> 
  </tr>
  <tr>
   <td>Vorwärts</td> 
   <td>ProcessManagementTaskService</td> 
   <td>Vorwärts</td> 
   <td>Leitet eine Aufgabe an einen anderen Benutzer weiter.</td> 
  </tr>
  <tr>
   <td>konsultieren</td> 
   <td>ProcessManagementTaskService</td> 
   <td>konsultieren</td> 
   <td>Er prüft eine Aufgabe mit einem anderen Benutzer.</td> 
  </tr>
  <tr>
   <td>claim</td> 
   <td>ProcessManagementTaskService</td> 
   <td>claim</td> 
   <td>Fordert eine Aufgabe an, die in der freigegebenen Warteschlange verfügbar ist.</td> 
  </tr>
  <tr>
   <td>unlock</td> 
   <td>ProcessManagementTaskService</td> 
   <td>unlock</td> 
   <td>Entsperrt eine Aufgabe.</td> 
  </tr>
  <tr>
   <td>lock</td> 
   <td>ProcessManagementTaskService</td> 
   <td>lock</td> 
   <td>Sperrt eine Aufgabe und die Aufgabe kann von einem anderen Benutzer nicht angefordert werden, wenn sie freigegeben wird.</td> 
  </tr>
  <tr>
   <td>Ablehnen der Bedingungen</td> 
   <td>ProcessManagementTaskService</td> 
   <td>Ablehnen der Bedingungen</td> 
   <td>Gibt die Aufgabe an den vorherigen Eigentümer der Aufgabe zurück.</td> 
  </tr>
  <tr>
   <td>Abbruch</td> 
   <td>ProcessManagementTaskService</td> 
   <td>Abbruch</td> 
   <td>Löscht eine Aufgabe.</td> 
  </tr>
  <tr>
   <td>setVisibility</td> 
   <td>ProcessManagementTaskService</td> 
   <td>setVisibility</td> 
   <td>Er legt die Sichtbarkeit einer Aufgabe fest. Wenn die Sichtbarkeit auf "false"gesetzt ist, ist die Aufgabe für den Benutzer danach nicht mehr sichtbar.</td> 
  </tr>
  <tr>
   <td>getUsers</td> 
   <td>ProcessManagementUserProxyService</td> 
   <td>getUsers</td> 
   <td>Sie wird für die Suche nach Benutzern verwendet. Gibt alle Benutzer zurück, wenn kein Name angegeben ist. Andernfalls werden Benutzer mit dem angegebenen Namen zurückgegeben.</td> 
  </tr>
  <tr>
   <td>getUsersInGroup</td> 
   <td>ProcessManagementUserProxyService</td> 
   <td>getUsersInGroupByName</td> 
   <td>Es werden alle Benutzer einer Gruppe zurückgegeben.</td> 
  </tr>
  <tr>
   <td>grantQueueAccess</td> 
   <td>ProcessManagementQueueService</td> 
   <td>grantQueueAccess</td> 
   <td>Gewährt dem angegebenen Benutzer Zugriff auf die Warteschlange des angemeldeten Benutzers. Im Grunde wird eine eigene Warteschlange für einen anderen Benutzer freigegeben.</td> 
  </tr>
  <tr>
   <td>requestQueueAccess</td> 
   <td>ProcessManagementQueueService</td> 
   <td>requestQueueAccess</td> 
   <td>Es stellt Zugriffsanfragen für die Warteschlange des angegebenen Benutzers für den angemeldeten Benutzer. Wenn der Benutzer die Anforderung genehmigt, wird die Warteschlange des Benutzers für den angemeldeten Benutzer freigegeben.</td> 
  </tr>
  <tr>
   <td>getGrantedUsers</td> 
   <td>ProcessManagementQueueService</td> 
   <td>getGrantedUsers</td> 
   <td>Gibt alle Benutzer zurück, die Zugriff auf die Warteschlange des angemeldeten Benutzers haben.</td> 
  </tr>
  <tr>
   <td>getUsersForAccessibleQueues</td> 
   <td>ProcessManagementQueueService</td> 
   <td>getUsersForAccessibleQueues</td> 
   <td>Gibt alle Benutzer zurück, deren Warteschlange für einen Benutzer zugänglich ist.</td> 
  </tr>
  <tr>
   <td>cancelQueueAccess</td> 
   <td>ProcessManagementQueueService</td> 
   <td>cancelQueueAccess</td> 
   <td>Entfernt einen Benutzer aus der Liste der Benutzer, die Zugriff auf die Warteschlange des angemeldeten Benutzers haben.</td> 
  </tr>
  <tr>
   <td>removeQueueAccess</td> 
   <td>ProcessManagementQueueService</td> 
   <td>removeQueueAccess</td> 
   <td>Entfernt einen Benutzer aus der Liste der Benutzer, deren Warteschlange für den angemeldeten Benutzer zugänglich ist.</td> 
  </tr>
  <tr>
   <td>getAllQueues<br /> </td> 
   <td>ProcessManagementQueueService<br /> </td> 
   <td>getAllQueues<br /> </td> 
   <td>Ruft alle Warteschlangen (eigene, freigegebene und Gruppenwarteschlangen) ab, auf die der angemeldete Benutzer zugreifen kann.<br /> </td> 
  </tr>
  <tr>
   <td>getOutOfOfficeSettings</td> 
   <td>ProcessManagementOutOfOfficeService</td> 
   <td>getOutOfOfficeSettings</td> 
   <td>Die Abwesenheitseinstellungen eines Benutzers werden angezeigt.</td> 
  </tr>
  <tr>
   <td>saveOutOfOfficeSettingsJson</td> 
   <td>ProcessManagementOutOfOfficeService</td> 
   <td>saveOutOfOfficeSettingsJson</td> 
   <td>Speichert Abwesenheitseinstellungen eines Benutzers.</td> 
  </tr>
  <tr>
   <td>getAllProcesses</td> 
   <td>ProcessManagementProcessService</td> 
   <td>getAllProcesses</td> 
   <td>Es wird eine Liste aller Prozesse zurückgegeben.</td> 
  </tr>
  <tr>
   <td>getParticipatedProcesses</td> 
   <td>ProcessManagementProcessService</td> 
   <td>getParticipatedProcesses</td> 
   <td>Gibt eine Liste aller Prozessnamen zurück, die vom angemeldeten Benutzer verwendet wurden.</td> 
  </tr>
  <tr>
   <td>getProcessInstance<br /> </td> 
   <td>ProcessManagementProcessService<br /> </td> 
   <td>getProcessInstance<br /> </td> 
   <td>Ruft Details einer Prozessinstanz ab.<br /> </td> 
  </tr>
  <tr>
   <td>getProcessInstances</td> 
   <td>ProcessManagementQueryService</td> 
   <td>getProcessInstances</td> 
   <td>Ruft alle Prozessinstanzen für einen Prozess ab.</td> 
  </tr>
  <tr>
   <td>getPendingTasksForProcessInstance</td> 
   <td>ProcessManagementQueryService</td> 
   <td>getPendingTasksForProcessInstance</td> 
   <td>Ruft ausstehende Aufgaben für eine Prozessinstanz ab.</td> 
  </tr>
  <tr>
   <td>getTasksForProcessInstance</td> 
   <td>ProcessManagementQueryService</td> 
   <td>getTasksForProcessInstance</td> 
   <td>Ruft alle Aufgaben für eine Prozessinstanz ab.</td> 
  </tr>
  <tr>
   <td>getAllSearchTemplates</td> 
   <td>ProcessManagementQueryService</td> 
   <td>getAllSearchTemplates</td> 
   <td>Es wird eine Liste aller Suchvorlagen zurückgegeben.</td> 
  </tr>
  <tr>
   <td>getTemplate</td> 
   <td>ProcessManagementQueryService</td> 
   <td>getTemplate</td> 
   <td>Es werden Inhalte für eine Suchvorlage zurückgegeben.</td> 
  </tr>
  <tr>
   <td>findTasksJson<br /> </td> 
   <td>ProcessManagementQueryService</td> 
   <td>findTasksJson</td> 
   <td>Es werden alle Aufgaben gesucht und zurückgegeben, die alle Bedingungen einer Suchvorlage erfüllen.</td> 
  </tr>
  <tr>
   <td>getAssignmentsForTask</td> 
   <td>ProcessManagementTaskService</td> 
   <td>getAssignmentsForTask</td> 
   <td>Ruft alle Zuweisungen für eine Aufgabe ab. Beispiel:- Wenn ein Benutzer eine Aufgabe an einen anderen Benutzer weiterleitet oder sie mit ihm bespricht, ist dies eine Zuweisung für eine Aufgabe.</td> 
  </tr>
  <tr>
   <td>deleteAttachment </td> 
   <td>TaskManagerService</td> 
   <td>deleteAttachment</td> 
   <td>Löscht eine Anlage.</td> 
  </tr>
  <tr>
   <td>initialize</td> 
   <td>ProcessManagementClientSessionService</td> 
   <td>initialize</td> 
   <td>Bei Bedarf wird die Bestätigung erneuert. Authentifiziert den Benutzer. Legt Sitzungsparameter für Server-/Client-Informationen fest. Gibt Benutzerinformationen und Abrufintervall zurück.</td> 
  </tr>
  <tr>
   <td>getTasksForDirectReports</td> 
   <td>ProcessManagementTeamTasksService</td> 
   <td>getTasksForDirectReports</td> 
   <td>Es werden alle Aufgaben der direkten Berichte des angemeldeten Managers zurückgegeben.</td> 
  </tr>
  <tr>
   <td>getTaskOfDirectReport<br /> </td> 
   <td>ProcessManagementTeamTasksService</td> 
   <td>getDirectReportTask</td> 
   <td>Es wird die Aufgabe des angegebenen direkten Berichts des angemeldeten Managers zurückgegeben.</td> 
  </tr>
  <tr>
   <td>forwardTaskOfDirectReport</td> 
   <td>ProcessManagementTeamTasksService</td> 
   <td>forwardTaskOfDirectReport</td> 
   <td>Leitet eine Aufgabe eines direkt unterstellten Mitarbeiters an einen anderen Benutzer weiter.</td> 
  </tr>
  <tr>
   <td>rejectTaskOfDirectReport</td> 
   <td>ProcessManagementTeamTasksService</td> 
   <td>rejectTaskOfDirectReport</td> 
   <td>Gibt eine Aufgabe eines direkt unterstellten Mitarbeiters an den vorherigen Benutzer zurück.</td> 
  </tr>
  <tr>
   <td>getProperty</td> 
   <td>WorkspacePropertyService</td> 
   <td>getProperty</td> 
   <td>Ruft eine Workspace-Eigenschaft für einen Benutzer ab.</td> 
  </tr>
  <tr>
   <td>removeProperty</td> 
   <td>WorkspacePropertyService</td> 
   <td>Löschen Sie</td> 
   <td>Entfernt eine Workspace-Eigenschaft für einen Benutzer.</td> 
  </tr>
  <tr>
   <td>getProperties</td> 
   <td>WorkspacePropertyService</td> 
   <td>getPropertiesAsMap</td> 
   <td>Es werden alle Workspace-Eigenschaften für einen Benutzer zurückgegeben.</td> 
  </tr>
  <tr>
   <td>setProperty</td> 
   <td>WorkspacePropertyService</td> 
   <td>setProperty</td> 
   <td>Legt eine Workspace-Eigenschaft für einen Benutzer fest.</td> 
  </tr>
  <tr>
   <td>getCurrentUserImageUrl</td> 
   <td>ProcessManagementClientSessionService</td> 
   <td>getCurrentUserImageUrl</td> 
   <td>Ruft die Bild-URL des Benutzers für den angemeldeten Benutzer ab.</td> 
  </tr>
  <tr>
   <td>getUserImageUrl</td> 
   <td>ProcessManagementClientSessionService</td> 
   <td>getUserImageUrl</td> 
   <td>Ruft die Bild-URL des Benutzers für den angegebenen Benutzer ab.</td> 
  </tr>
  <tr>
   <td>uploadNote</td> 
   <td>ProcessManagementDocumentHandlingService</td> 
   <td>uploadNote</td> 
   <td>Er lädt eine Notiz für eine Aufgabe auf den Server hoch.</td> 
  </tr>
  <tr>
   <td>uploadRMAToServer (es wird auch direkt von der HTML-Vorlage aufgerufen)<br /> </td> 
   <td>ProcessManagementDocumentHandlingService</td> 
   <td>uploadAttachment</td> 
   <td>Er lädt eine Anlage für eine Aufgabe auf den Server hoch.</td> 
  </tr>
  <tr>
   <td>getImageURL (es wird auch direkt von der HTML-Vorlage aufgerufen)</td> 
   <td>ProcessManagementDocumentHandlingService</td> 
   <td>getImage</td> 
   <td>Ruft Bild für einen Prozess ab.</td> 
  </tr>
 </tbody>
</table>
