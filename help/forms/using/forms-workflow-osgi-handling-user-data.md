---
title: Formularzentrierte Workflows unter OSGi | Umgang mit Benutzerdaten
seo-title: Forms-centric workflows on OSGi | Handling user data
description: Forms-orientierte AEM-Workflows ermöglichen die Automatisierung von Forms-orientierten Geschäftsprozessen in der Praxis. Weitere Informationen zu Benutzerdaten und Datenspeichern. Erfahren Sie, wie Sie auf Benutzerdaten zugreifen und diese löschen können.
seo-description: Forms-centric AEM workflows enable you to automate real-world Forms-centric business processes. Dig deeper on user data and data stores. Learn how to access and delete user data.
uuid: 6eefbe84-6496-4bf8-b065-212aa50cd074
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 9f400560-8152-4d07-a946-e514e9b9cedf
role: Admin
exl-id: 65c13bc8-da82-4c4b-b014-341ce1b59b71
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1069'
ht-degree: 35%

---

# Formularzentrierte Workflows unter OSGi | Umgang mit Benutzerdaten {#forms-centric-workflows-on-osgi-handling-user-data}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Forms-orientierte AEM-Workflows ermöglichen die Automatisierung von Forms-orientierten Geschäftsprozessen in der Praxis. Workflows bestehen aus einer Reihe von Schritten, die in der im zugehörigen Workflow-Modell angegebenen Reihenfolge ausgeführt werden. Jeder Schritt führt eine bestimmte Aktion aus, z. B. das Zuweisen einer Aufgabe zu einem Benutzer oder das Senden einer E-Mail-Nachricht. Workflows können mit Assets im Repository, mit Benutzerkonten und mit Experience Manager-Diensten interagieren. Daher können Workflows komplexe Aktivitäten koordinieren, die einen beliebigen Aspekt des Experience Managers betreffen.

Ein formularzentrierter Workflow kann über eine der folgenden Methoden ausgelöst oder gestartet werden:

* Senden eines Programms aus dem AEM-Posteingang
* Senden einer Anwendung aus der AEM Forms-App
* Senden eines adaptiven Formulars
* Verwenden eines überwachten Ordners
* Senden einer interaktiven Kommunikation oder eines Briefes

Weitere Informationen über die formularzentrierten AEM-Workflows und -Funktionen finden Sie unter [Formularzentrierter Workflow auf OSGi](/help/forms/using/aem-forms-workflow.md).

## Benutzerdaten und Datenspeicher {#user-data-and-data-stores}

Wenn ein Workflow ausgelöst wird, wird automatisch eine Payload für die Workflow-Instanz generiert. Jeder Workflow-Instanz wird eine eindeutige Instanz-ID und eine zugeordnete Payload-ID zugewiesen. Die Payload enthält die Repository-Speicherorte für Benutzer- und Formulardaten, die mit einer Workflow-Instanz verknüpft sind. Darüber hinaus werden Entwürfe und historische Daten für eine Workflow-Instanz auch im AEM Repository gespeichert.

Die standardmäßigen Repository-Speicherorte, in denen sich Payload, Entwürfe und der Verlauf einer Workflow-Instanz befinden, lauten wie folgt:

>[!NOTE]
>
>Sie können verschiedene Speicherorte konfigurieren, um beim Erstellen eines Workflows oder einer Anwendung Payload-, Entwurfs- und Verlaufsdaten zu speichern. Überprüfen Sie den Workflow, um die Speicherorte anzugeben, an denen ein Workflow oder eine Anwendung Daten gespeichert hat.

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td>AEM 6.4 Forms</td> 
   <td>AEM 6.3 Forms</td> 
  </tr> 
  <tr> 
   <td><strong>Workflow-<br />Instanz</strong></td> 
   <td>/var/workflow/instances/[server_id]/&lt;date&gt;/[workflow-instance]/</td> 
   <td>/etc/workflow/instances/[server_id]/[date]/[workflow-instance]/</td> 
  </tr> 
  <tr> 
   <td><strong>Nutzlast</strong></td> 
   <td>/var/fd/dashboard/payload/[server_id]/[date]/<br /> [payload-id]/</td> 
   <td>/etc/fd/dashboard/payload/[server_id]/[date]/<br /> [payload-id]/</td> 
  </tr> 
  <tr> 
   <td><strong>Entwürfe</strong></td> 
   <td>/var/fd/dashboard/instances/[server_id]/<br /> [Datum]/[Workflow-Instanz]/draft/[Arbeitselement]/</td> 
   <td>/etc/fd/dashboard/instances/[server_id]/<br /> [Datum]/[Workflow-Instanz]/draft/[Arbeitselement]/</td> 
  </tr> 
  <tr> 
   <td><strong>Verlauf</strong></td> 
   <td>/var/fd/dashboard/instances/[server_id]/<br /> [Datum]/[Workflow-Instanz]/history/</td> 
   <td>/etc/fd/dashboard/instances/[server_id]/<br /> [Datum]/[Workflow-Instanz]/history/</td> 
  </tr> 
 </tbody> 
</table>

## Zugreifen auf und Löschen von Benutzerdaten {#access-and-delete-user-data}

Sie können Benutzerdaten aus einer Workflow-Instanz im Repository aufrufen und löschen. Um dies zu erreichen, müssen Sie die Instanz-ID der Workflow-Instanz kennen, die dem Benutzer zugeordnet ist. Sie können die Instanz-ID einer Workflow-Instanz mithilfe des Benutzernamens des Benutzers finden, der die Workflow-Instanz initiiert hat oder der der aktuelle Bearbeiter der Workflow-Instanz ist.

In den folgenden Szenarien können Sie jedoch keine mehrdeutigen Ergebnisse erkennen, wenn Sie Workflows identifizieren, die mit einem Initiator verknüpft sind:

* **Workflow, der durch einen überwachten Ordner ausgelöst wird**: Eine Workflow-Instanz kann nicht mit ihrem Initiator identifiziert werden, wenn der Workflow durch einen überwachten Ordner ausgelöst wird. In diesem Fall werden die Benutzerinformationen in den gespeicherten Daten kodiert.
* **Workflow, der von der Veröffentlichungs-AEM-Instanz initiiert wurde**: Alle Workflow-Instanzen werden mithilfe eines Dienstbenutzers erstellt, wenn adaptive Formulare, interaktive Kommunikation oder Briefe aus AEM Veröffentlichungsinstanz gesendet werden. In diesen Fällen wird der Benutzername des angemeldeten Benutzers nicht in den Workflow-Instanzdaten erfasst.

### Zugreifen auf Benutzerdaten {#access}

Führen Sie die folgenden Schritte aus, um Benutzerdaten für eine Workflow-Instanz zu identifizieren und darauf zuzugreifen:

1. Navigieren Sie in der AEM-Author-Instanz zu `https://[server]:[port]/crx/de` und anschließend zu **[!UICONTROL Tools > Abfrage]**.

   Auswählen **[!UICONTROL SQL2]** von **[!UICONTROL Typ]** Dropdown-Liste.

1. Führen Sie je nach den verfügbaren Informationen eine der folgenden Abfragen aus:

   * Führen Sie Folgendes aus, wenn der Workflow-Initiator bekannt ist:

   `SELECT &ast; FROM [cq:Workflow] AS s WHERE ISDESCENDANTNODE([path-to-workflow-instances]) and s.[initiator]='*initiator-ID*'`

   * Führen Sie Folgendes aus, wenn der Benutzer, dessen Daten Sie finden, der aktuelle Workflow-Bearbeiter ist:

   `SELECT &ast; FROM [cq:WorkItem] AS s WHERE ISDESCENDANTNODE([path-to-workflow-instances]) and s.[assignee]='*assignee-id*'`

   Die Abfrage gibt den Speicherort aller Workflow-Instanzen für den angegebenen Workflow-Initiator oder den aktuellen Workflow-Empfänger zurück.

   Die folgende Abfrage gibt z. B. den Pfad zweier Workflow-Instanzen vom Knoten `/var/workflow/instances` zurück, deren Workflow-Initiator `srose` ist.

   ![workflow-instance](assets/workflow-instance.png)

1. Navigieren Sie zu einem Workflow-Instanzpfad, der von der Abfrage zurückgegeben wird. Die Statuseigenschaft zeigt den aktuellen Status der Workflow-Instanz an.

   ![status](assets/status.png)

1. Navigieren Sie im Workflow-Instanzknoten zu `data/payload/`. Die Eigenschaft `path` speichert den Pfad zur Nutzlast für die Workflow-Instanz. Sie können zu dem Pfad navigieren, um auf Daten zuzugreifen, die in der Nutzlast gespeichert sind.

   ![payload-path](assets/payload-path.png)

1. Navigieren Sie zu den Speicherorten für Entwürfe und Verlauf für die Workflow-Instanz.

   Beispiel:

   `/var/fd/dashboard/instances/server0/2018-04-09/_var_workflow_instances_server0_2018-04-09_basicmodel_54/draft/`

   `/var/fd/dashboard/instances/server0/2018-04-09/_var_workflow_instances_server0_2018-04-09_basicmodel_54/history/`

1. Wiederholen Sie die Schritte 3 bis 5 für alle Workflow-Instanzen, die von der Abfrage in Schritt 2 zurückgegeben wurden.

>[!NOTE]
>
>Das AEM Forms-Programm speichert auch Daten im Offline-Modus. Es ist möglich, dass Daten für eine Workflow-Instanz lokal auf einzelnen Geräten gespeichert und an den Forms-Server gesendet werden, wenn die App mit dem Server synchronisiert wird.

### Löschen von Benutzerdaten {#delete-user-data}

Sie müssen ein AEM Administrator sein, um Benutzerdaten aus Workflow-Instanzen zu löschen, indem Sie die folgenden Schritte ausführen:

1. Folgen Sie den Anweisungen in [Auf Benutzerdaten zugreifen](/help/forms/using/forms-workflow-osgi-handling-user-data.md#access) und beachten Sie Folgendes:

   * Pfade zu Workflow-Instanzen, die dem Benutzer zugeordnet sind
   * Status der Workflow-Instanzen
   * Pfade zu Payloads für die Workflow-Instanzen
   * Pfade zu Entwürfen und Verlauf für die Workflow-Instanzen

1. Führen Sie diesen Schritt für Workflow-Instanzen mit dem Status **RUNNING**, **SUSPENDED** oder **STALE** aus:

   1. Navigieren Sie zu `https://[server]:[port]/aem/start.html` und melden Sie sich als Administrator an.
   1. Navigieren Sie zu **[!UICONTROL Tools > Workflow > Instanzen]**.
   1. Wählen Sie relevante Workflow-Instanzen für den Benutzer aus und tippen Sie auf **[!UICONTROL Beenden]** , um laufende Instanzen zu beenden.

   Weitere Informationen zum Arbeiten mit Workflow-Instanzen finden Sie unter [Verwalten von Workflow-Instanzen](/help/sites-administering/workflows-administering.md).

1. Navigieren Sie zur CRXDE Lite-Konsole, navigieren Sie zum Payload-Pfad für eine Workflow-Instanz und löschen Sie die `payload` Knoten.
1. Navigieren Sie zum Entwurfspfad für eine Workflow-Instanz und löschen Sie den Knoten `draft`.
1. Navigieren Sie zu dem Verlaufspfad für eine Workflow-Instanz und löschen Sie den Knoten `history`.
1. Navigieren Sie zum Workflow-Instanzpfad für eine Workflow-Instanz und löschen Sie den Knoten `[workflow-instance-ID]` für den Workflow.

   >[!NOTE]
   >
   >Durch Löschen des Knotens der Workflow-Instanz wird die Workflow-Instanz für alle Workflow-Teilnehmer entfernt.

1. Wiederholen Sie die Schritte 2 bis 6 für alle Workflow-Instanzen, die für einen Benutzer identifiziert wurden.
1. Identifizieren und löschen Sie Offline-Entwurfs- und -Sendedaten aus dem AEM Forms-App-Postausgang von Workflow-Teilnehmern, um eine Übermittlung an den Server zu vermeiden.

Sie können APIs auch verwenden, um auf Knoten und Eigenschaften zuzugreifen und sie zu entfernen. Weitere Informationen finden Sie in den folgenden Dokumenten.

* [Anleitung für den programmgesteuerten Zugriff auf das AEM-JCR](/help/sites-developing/access-jcr.md)
* [Entfernen von Knoten und Eigenschaften](https://docs.adobe.com/docs/en/spec/jcr/2.0/10_Writing.html#10.9%20Removing%20Nodes%20and%20Properties)
* [API-Referenz](https://helpx.adobe.com/de/experience-manager/6-3/sites-developing/reference-materials/javadoc/overview-summary.html)
