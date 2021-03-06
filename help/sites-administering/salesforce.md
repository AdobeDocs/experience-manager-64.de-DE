---
title: Integration mit Salesforce
seo-title: Integrating with Salesforce
description: Erfahren Sie mehr über die Integration von AEM mit Salesforce.
seo-description: Learn about integrating AEM with Salesforce.
uuid: db3b25f3-b680-4054-a8db-4161d4c86201
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: b9752c60-eb26-4840-9163-a99537a58727
exl-id: 4c09699a-c7ae-48ee-9423-87ff35b1e9d9
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1496'
ht-degree: 83%

---

# Integration mit Salesforce{#integrating-with-salesforce}

Eine Integration von Salesforce mit AEM bietet Lead-Management-Funktionen und nutzt die von Salesforce direkt bereitgestellten, vorhandenen Funktionen. Sie können AEM so konfigurieren, dass Leads in Salesforce gepostet und Komponenten erstellt werden, welche direkt von Salesforce aus auf die Daten zugreifen.

Die bidirektionale und erweiterbare Integration zwischen AEM und Salesforce ermöglicht:

* Organisationen, Daten in vollem Umfang zu nutzen und zu aktualisieren, um so das Kundenerlebnis zu optimieren;
* die Involvierung der Marketingabteilung in Vertriebstätigkeiten;
* Organisationen, Daten automatisch an einen Salesforce-Datenspeicher zu übermitteln und von diesem zu empfangen.

Dieses Dokument beschäftigt sich mit den folgenden Themen:

* Wie Sie Salesforce-Cloud-Services konfigurieren (AEM zur Integration in Salesforce konfigurieren)
* Wie Sie Salesforce-Lead/Kontaktdaten in ClientContext und zur Personalisierung nutzen
* Wie Sie das Salesforce-Workflow-Modell zum Posten von AEM-Benutzern als Leads in Salesforce nutzen
* Wie Sie eine Komponente erstellen, die Daten aus Salesforce anzeigt

## Konfigurieren von AEM zur Integration mit Salesforce {#configuring-aem-to-integrate-with-salesforce}

Um AEM für die Integration mit Salesforce zu konfigurieren, müssen Sie zunächst eine Fernzugriffsanwendung in Salesforce konfigurieren. Konfigurieren Sie dann den Salesforce-Cloud-Service, um auf diese Fernzugriffsanwendung zu verweisen.

>[!NOTE]
>
>Sie können ein kostenloses Entwicklerkonto in Salesforce anlegen.

So konfigurieren Sie AEM für die Integration mit Salesforce:

1. Navigieren Sie in AEM zu **Cloud-Services**. Klicken Sie unter „Services von Dritten“ auf **Jetzt konfigurieren** in **Salesforce**.

   ![chlimage_1-84](assets/chlimage_1-84.png)

1. Erstellen Sie eine neue Konfiguration, wie beispielsweise **developer**.

   >[!NOTE]
   >
   >Die neue Konfiguration wird auf eine neue Seite umgeleitet: **http://localhost:4502/etc/cloudservices/salesforce/developer.html**. Dies ist genau der Wert, den Sie in der Rückruf-URL beim Erstellen der Fernzugriffsanwendung in Salesforce angeben müssen. Diese Werte müssen übereinstimmen.

1. Melden Sie sich bei Ihrem Salesforce-Konto an (oder erstellen Sie eines bei [https://developer.force.com](https://developer.force.com).
1. Navigieren Sie in Salesforce zu **Erstellen** > **Apps** um **Connected Apps** (in früheren Versionen von Salesforce war der Workflow **Bereitstellen** > **Remote Access**).
1. Klicken Sie auf **Neu**, um AEM mit Salesforce zu verbinden.

   ![chlimage_1-85](assets/chlimage_1-85.png)

1. Geben Sie die entsprechenden Daten in die Felder **Name der verbundenen App**, **API-Name** und **E-Mail-Adresse des Kontakts** ein. Wählen Sie das Kontrollkästchen **OAuth-Einstellungen aktivieren** und geben Sie die **Rückruf-URL** ein. Fügen Sie dann einen OAuth-Umfang hinzu (beispielsweise vollständigen Zugriff). Die Callback-URL sieht in etwa so aus: `http://localhost:4502/etc/cloudservices/salesforce/developer.html`

   Ändern Sie den Servernamen/die Portnummer und die Seitennummer, sodass sie Ihrer Konfiguration entsprechen.

   ![chlimage_1-86](assets/chlimage_1-86.png)

1. Klicken Sie auf **Speichern**, um die Salesforce-Konfiguration zu speichern. Salesforce erstellt einen **Verbraucherschlüssel** und ein **Kundengeheimnis**, die Sie für die AEM-Konfiguration benötigen.

   ![chlimage_1-87](assets/chlimage_1-87.png)

   >[!NOTE]
   >
   >Unter Umständen müssen Sie einige Minuten (bis zu 15 Minuten) warten, bis die Fernzugriffsanwendung in Salesforce aktiviert wird.

1. Navigieren Sie in AEM zu **Cloud-Services** und dann zu der Salesforce-Konfiguration, die Sie zuvor erstellt haben (beispielsweise **developer**). Klicken Sie auf **Bearbeiten** und geben Sie den Kundenschlüssel und das Kundengeheimnis von salesforce.com ein.

   ![chlimage_1-23](assets/chlimage_1-23.jpeg)

   | Login-URL | Dies ist der Salesforce-Autorisierungsendpunkt. Der Wert ist bereits ausgefüllt und kann in den meisten Fällen verwendet werden. |
   |---|---|
   | Kundenschlüssel | Geben Sie den Wert ein, der von der Seite zur Registrierung von Remote-Zugriffsanwendungen in salesforce.com erhalten wurde. |
   | Kundengeheimnis | Geben Sie den Wert ein, der von der Seite zur Registrierung von Remote-Zugriffsanwendungen in salesforce.com erhalten wurde. |

1. Klicken Sie zum Verbinden auf **Mit Salesforce verbinden**. Salesforce verlangt, dass Sie Ihrer Konfiguration erlauben, sich mit Salesforce zu verbinden.

   ![chlimage_1-88](assets/chlimage_1-88.png)

   In AEM wird ein Bestätigungsdialogfeld mit der Meldung geöffnet, dass die Verbindung hergestellt wurde.

1. Navigieren Sie zur Stammseite Ihrer Website und klicken Sie auf **Seiteneigenschaften**. Wählen Sie anschließend **Cloud Services** und hinzufügen **Salesforce** und wählen Sie die richtige Konfiguration aus (z. B. **Entwickler**).

   ![chlimage_1-89](assets/chlimage_1-89.png)

   Jetzt können Sie das Workflow-Modell verwenden, um Leads an Salesforce zu posten und Komponenten zu erstellen, welche auf die Daten aus Salesforce zugreifen.

## Exportieren von AEM-Benutzern als Salesforce-Leads {#exporting-aem-users-as-salesforce-leads}

Wenn Sie einen AEM-Benutzer als Salesforce-Lead exportieren möchten, müssen Sie den Workflow so konfigurieren, dass Leads an Salesforce gepostet werden.

So exportieren Sie AEM-Benutzer als Salesforce-Leads:

1. Navigieren Sie zum Salesforce-Workflow unter `http://localhost:4502/workflow` durch Rechtsklick auf den Workflow **Salesforce.com Export** und klicken **Starten**.

   ![chlimage_1-90](assets/chlimage_1-90.png)

1. Wählen Sie den AEM-Benutzer, den Sie als Lead erstellen möchten, als **Payload** für diesen Workflow (Startseite -> Benutzer). Stellen Sie sicher, dass Sie den Profilknoten des Benutzers auswählen, da er Informationen, wie **givenName**, **familyName** usw. enthält, die den Feldern **FirstName** und **LastName** des Salesforce-Leads zugeordnet sind.

   ![chlimage_1-91](assets/chlimage_1-91.png)

   >[!NOTE]
   >
   >Vor Beginn dieses Workflows gibt es bestimmte Pflichtfelder, die ein Lead-Knoten in AEM vor der Veröffentlichung an Salesforce aufweisen muss. Diese **givenName**, **familyName**, **Firma** und **email**. Eine vollständige Liste der Zuordnung zwischen AEM Benutzer und Salesforce-Lead finden Sie unter [Zuordnen der Konfiguration zwischen AEM Benutzer und Slaesforce-Lead.](#mapping-configuration-between-aem-user-and-salesforce-lead)

1. Klicken Sie auf **OK**. Die Benutzerinformationen werden nach salesforce.com exportiert. Sie können dies unter salesforce.com überprüfen.

   >[!NOTE]
   >
   >Die Fehlerprotokolle zeigen Ihnen, ob ein Lead importiert wurde. Überprüfen Sie das Fehlerprotokoll auf weitere Informationen.

### Konfigurieren des Salesforce.com-Export-Workflows {#configuring-the-salesforce-com-export-workflow}

Möglicherweise müssen Sie den Salesforce.com-Export-Workflow so konfigurieren, dass er der korrekten Salesforce.com-Konfiguration entspricht, oder Sie müssen unter Umständen andere Änderungen vornehmen.

So konfigurieren SIe den Salesforce.com-Export-Workflow:

1. Navigieren Sie zu `http://localhost:4502/cf#/etc/workflow/models/salesforce-com-export.html.`

   ![chlimage_1-24](assets/chlimage_1-24.jpeg)

1. Öffnen Sie den Schritt Salesforce.com Export und wählen Sie die **Argumente** und wählen Sie die richtige Konfiguration aus und klicken Sie auf **OK**. Aktivieren Sie zudem das Kontrollkästchen, wenn Sie möchten, dass der Workflow einen Lead, der in Salesforce gelöscht wurde, neu erstellt.

   ![chlimage_1-92](assets/chlimage_1-92.png)

1. Klicken Sie auf **Speichern**, um Ihre Änderungen zu speichern.

   ![chlimage_1-93](assets/chlimage_1-93.png)

### Zuordnen der Konfiguration zwischen AEM-Benutzer und Salesforce Lead {#mapping-configuration-between-aem-user-and-salesforce-lead}

Um die aktuelle Zuordnungskonfiguration zwischen einem AEM Benutzer und einem Salesforce-Lead anzuzeigen oder zu bearbeiten, öffnen Sie Configuration Manager: `https://<hostname>:<port>/system/console/configMgr` und suchen Sie nach **Salesforce-Lead-Zuordnungskonfiguration**.

1. Öffnen Sie Configuration Manager durch Klicken auf **Web-Konsole** oder direkt zu `https://<hostname>:<port>/system/console/configMgr.`
1. Suchen Sie nach **Salesforce-Lead-Zuordnungskonfiguration**.

   ![chlimage_1-94](assets/chlimage_1-94.png)

1. Ändern Sie die Zuordnungen nach Bedarf. Die Standardzuordnung folgt dem Muster** aemUserAttribute=sfLeadAttribute**. Klicken Sie auf **Speichern**, um Ihre Änderungen zu speichern.

## Konfigurieren des Salesforce ClientContext-Speichers {#configuring-salesforce-client-context-store}

Der Salesforce-ClientContext-Speicher zeigt neben den Informationen zum derzeit angemeldeten Benutzer, die bereits in AEM verfügbar sind, zusätzliche Informationen an. Er ruft diese zusätzlichen Informationen gemäß der Benutzerverbindung zu Salesforce aus Salesforce ab.

Dazu müssen Sie Folgendes konfigurieren:

1. Verknüpfen Sie einen AEM-Benutzer über die Salesforce Connect-Komponente mit einer Salesforce-ID.
1. Geben Sie die Salesforce-Profildaten auf der ClientContext-Seite ein, um die Eigenschaften, die Sie sehen möchten, zu konfigurieren.
1. (Optional) Erstellen Sie ein Segment, welches Daten aus dem Salesforce-ClientContext-Speicher nutzt.

### Verknüpfen eines AEM-Benutzers mit einer Salesforce-ID {#linking-an-aem-user-with-a-salesforce-id}

Sie müssen einen AEM-Benutzer einer Salesforce-ID zuordnen, um sie in ClientContext zu laden. In einem praxisnahen Szenario würden Sie die Verknüpfung basierend auf den bekannten Benutzerdaten mit einer Validierung erstellen. Zur Veranschaulichung nutzen Sie in diesem Verfahren die **Salesforce Connect**-Komponente.

1. Navigieren Sie zu einer Website in AEM, melden Sie sich an und ziehen Sie die **Salesforce Connect-Komponente** per Drag-and-Drop aus dem Sidekick.

   >[!NOTE]
   >
   >Wenn die **Salesforce Connect**-Komponente nicht verfügbar ist, wechseln Sie zur **Design**-Ansicht. Wählen Sie sie aus, um sie in der Ansicht **Bearbeiten** verfügbar zu machen.

   ![chlimage_1-25](assets/chlimage_1-25.jpeg)

   Wenn Sie die Komponente auf die Seite ziehen, zeigt diese **Verknüpfung zu Salesforce=Aus** an.

   ![chlimage_1-95](assets/chlimage_1-95.png)

   >[!NOTE]
   >
   >Diese Komponente dient nur der Veranschaulichung. In praxisnahen Szenarien gäbe es einen weiteren Prozess zum Verknüpfen/Abgleichen von Benutzern mit Leads.

1. Nachdem Sie die Komponente auf die Seite gezogen haben, öffnen Sie sie zum Konfigurieren. Wählen Sie die Konfiguration, den Kontakttyp und den Salesforce-Lead oder -Kontakt. Klicken Sie auf **OK**.

   ![chlimage_1-96](assets/chlimage_1-96.png)

   AEM verknüpft den Benutzer mit dem Salesforce-Kontakt oder -Lead.

   ![chlimage_1-97](assets/chlimage_1-97.png)

### Hinzufügen von Salesforce-Daten zu ClientContext {#adding-salesforce-data-to-client-context}

Sie können Benutzerdaten aus Salesforce in ClientContext laden, um sie für die Personalisierung zu verwenden:

1. Öffnen Sie den Client-Kontext, den Sie erweitern möchten, indem Sie dort z. B. navigieren. `http://localhost:4502/etc/clientcontext/default/content.html.`

   ![chlimage_1-26](assets/chlimage_1-26.jpeg)

1. Ziehen Sie die Salesforce-Profildaten-Komponente auf den ClientContext.****

   ![chlimage_1-27](assets/chlimage_1-27.jpeg)

1. Doppelklicken Sie auf die Komponente, um diese zu öffnen. Wählen Sie **Element hinzufügen** und dann eine Eigenschaft aus der Dropdown-Liste aus. Fügen Sie beliebig viele Eigenschaften hinzu und wählen Sie **OK** aus.

   ![chlimage_1-98](assets/chlimage_1-98.png)

1. Jetzt können Sie die Salesforce-spezifischen Eigenschaften aus Salesforce in ClientContext sehen.

   ![chlimage_1-99](assets/chlimage_1-99.png)

### Erstellen eines Segments mithilfe der Daten aus dem Salesforce-ClientContext-Speicher {#building-a-segment-using-data-from-salesforce-client-context-store}

Sie können ein Segment erstellen, das Daten aus dem Salesforce-ClientContext-Speicher verwendet. Gehen Sie hierfür wie folgt vor:

1. Navigieren Sie in AEM zur Segmentierung, indem Sie entweder **Instrumente** > **Segmentierung** oder [http://localhost:4502/miscadmin#/etc/segmentation](http://localhost:4502/miscadmin#/etc/segmentation).
1. Erstellen oder aktualisieren Sie ein Segment, um Daten aus Salesforce zu übernehmen. Weitere Informationen erhalten Sie unter [Segmentierung](/help/sites-administering/campaign-segmentation.md).

## Suchen von Leads {#searching-leads}

Im Lieferumfang von AEM ist eine Muster-Suchkomponente enthalten, die gemäß den angegebenen Kriterien in Salesforce nach Leads sucht. Diese Komponente zeigt Ihnen, wie Sie die Salesforce-REST-API nutzen, um nach Salesforce-Objekten zu suchen. Sie müssen eine Seite mit einer Salesforce-Konfiguration verknüpfen, um ein Abrufen bei salesforce.com auszulösen.

>[!NOTE]
>
>Dies ist eine Beispielkomponente, die Ihnen zeigt, wie die Salesforce-REST-API zur Abfrage von Salesforce-Objekten verwendet wird. Verwenden Sie sie als Beispiel, um komplexere Komponenten gemäß Ihren Anforderungen zu erstellen.

So verwenden Sie diese Komponente:

1. Navigieren Sie zu der Seite, auf der Sie diese Konfiguration verwenden möchten. Öffnen Sie die Seiteneigenschaften und wählen Sie **Cloud-Services.** Klicken Sie auf **Services hinzufügen**. Wählen Sie dann **Salesforce** und die entsprechende Konfiguration aus und klicken Sie auf **OK**.

   ![chlimage_1-28](assets/chlimage_1-28.jpeg)

1. Ziehen Sie die Salesforce-Suchkomponente auf die Seite (sofern sie aktiviert wurde. Zum Aktivieren wechseln Sie in den Designmodus und fügen sie dem entsprechenden Bereich hinzu).

   ![chlimage_1-29](assets/chlimage_1-29.jpeg)

1. Öffnen Sie die Suchkomponente und legen Sie die Suchparameter fest. Klicken Sie dann auf **OK**.

   ![chlimage_1-100](assets/chlimage_1-100.png)

1. AEM zeigt die in Ihrer Suchkomponente aufgeführten Leads an, die den angegebenen Kriterien entsprechen.

   ![chlimage_1-101](assets/chlimage_1-101.png)
