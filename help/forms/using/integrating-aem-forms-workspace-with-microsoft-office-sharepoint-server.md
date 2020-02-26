---
title: Integrieren von AEM Forms Workspace in Microsoft Office SharePoint Server
seo-title: Integrieren von AEM Forms Workspace in Microsoft Office SharePoint Server
description: 'Sie können AEM Forms Workspace in Microsoft Office SharePoint Server integrieren. '
seo-description: 'Sie können AEM Forms Workspace in Microsoft Office SharePoint Server integrieren. '
uuid: d43396d4-117f-47ea-91e4-10ee96107bc8
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: 1bada670-3e0e-40f4-b9be-8b090df910be
translation-type: tm+mt
source-git-commit: 8cbfa421443e62c0483756e9d5812bc987a9f91d

---


# Integrieren von AEM Forms Workspace in Microsoft Office SharePoint Server {#integrating-aem-forms-workspace-with-microsoft-office-sharepoint-server}

**- Voraussetzungen**

**Vorausgesetztes Wissen** Bevor Sie AEM Forms Workspace zu SharePoint Server hinzufügen können, müssen Sie Zugriff auf SharePoint Server mit den entsprechenden Berechtigungen haben. Außerdem müssen Sie die URL kennen, um auf Workspace zugreifen zu können. In den folgenden Schritten wird davon ausgegangen, dass Sie mit SharePoint Server vertraut sind. Weitere Informationen zu Webparts in SharePoint Server Webparte finden Sie unter „Webparts in Windows SharePoint-Diensten“.

**Benutzerebene** Erste Schritte

Sie können AEM Forms Workspace als Webpart in Microsoft Office SharePoint Server (z. B. Microsoft Office SharePoint Server 2007) verwenden. Benutzer können auf AEM-Formular Workspace zugreifen, indem sie mithilfe eines Webbrowsers eine Verbindung zu Ihrem SharePoint Server herstellen und so eine einheitliche Plattform erhalten. In diesem Artikel lernen Sie die grundlegenden Schritte, um AEM Forms Workspace als Webpart in Microsoft Office SharePoint Server anzuzeigen. Sie können die Schritte ausführen, die in diesem Artikel beschrieben werden, um eine einheitliche Plattform zu bieten, damit Benutzer, die eine Verbindung mit dem SharePoint Server herstellen, auf AEM Forms Workspace vom gleichen Port aus zugreifen können.

>[!NOTE]
>
>Die Schritte, die in diesem Artikel aufgeführt sind, gelten für Microsoft SharePoint Server 2007. Sie können auch HTML Workspace mit anderen unterstützten Versionen von Microsoft SharePoint konfigurieren.

## Integrieren von AEM Forms Workspace in Microsoft Office SharePoint Server 2007 {#integrate-aem-forms-workspace-with-microsoft-office-sharepoint-server}

Gehen Sie zur Integration von AEM Forms Workspace in einen Webpart wie folgt vor:

1. In a web browser, navigate to the SharePoint site such as, https://*[myMOSSserver]:*44299/default.aspx where *[myMOSSserver]* is the name or the IP address of the Sharepoint server.

   >[!NOTE]
   >
   >44299 ist die Standardportnummer für den SharePoint Server. Die Portnummer hängt von Ihrer Installation des SharePoint Server ab.

1. Klicken Sie in der rechten oberen Ecke der Webseite auf **Site-Aktionen** und wählen Sie **Seite bearbeiten**.
1. Klicken Sie auf die Schaltfläche **Webpart hinzufügen.**
1. Wählen Sie im Webseitendialogfeld „Webparts hinzufügen“ unter „Sonstiges“ **Seiten-Viewer-Webpart** hinzu und klicken Sie dann auf **Hinzufügen**.
1. Im Feld „Seiten-Viewer-Webpart“ klicken Sie auf **Bearbeiten** und wählen Sie **Freigegebenen Webpart ändern**.

   >[!NOTE]
   >
   >Das Feld „Seiten-Viewer-Webpart“ wird unter der Schaltfläche **Webpart hinzufügen** angezeigt, auf die Sie in Schritt 3 geklickt haben, wie in der folgenden Abbildung gezeigt (Abbildung 1):

   ![Feld „Seiten-Viewer-Webpart“ in Microsoft Office SharePoint Server.](assets/page-viewer-web-part-box-in-microsoft-office-sharepoint-server.png)

   **** Abbildung: *Das Feld &quot;Seiten-Viewer-Webpart&quot;im Microsoft Office SharePoint-Server.*

1. Führen Sie auf der Seite „Seiten-Viewer“ folgende Aufgaben durch:

   1. In the Link box, type the URL of AEM Forms Workspace, such as https://*[AEM_forms_Server]:*8080/lc/ws where *[AEM_forms_Server]* represents the IP or Name of AEM forms server.
   1. Klicken Sie auf **Erscheinungsbild** und ändern Sie die Höhe, die Breite und den Titel, damit Sie die gesamte Workspace-Benutzeroberfläche sehen können. Beispielsweise können Sie die Breite und Höhe auf 15 cm bzw. 28 cm festlegen.
   1. Klicken Sie auf **Link testen**. Ein neues Webbrowserfenster mit Workspace wird angezeigt.
   1. (Optional) Klicken Sie auf **Layout** und ändern Sie das Layout von Workspace im Webpart.
   1. (Optional) Klicken Sie auf **Erweitert** und ändern Sie andere Einstellungen wie die Beschreibung und ob Workspace im Webpart minimiert werden oder geschlossen werden kann.

      Klicken Sie auf **Übernehmen**.

1. Klicken Sie auf **Bearbeitungsmodus beenden** und vergewissern Sie sich, dass Sie auf Workspace zugreifen können.

Nachdem Sie die oben beschriebenen Schritte durchgeführt haben, sieht Ihre SharePoint-Site ähnlich wie in der folgenden Abbildung gezeigt aus (Abbildung 2):

![AEM Forms Workspace in Microsoft Office SharePoint Server integriert](assets/aem-forms-workspace.jpg)

**** Abbildung: In Microsoft Office SharePoint Server integrierte *AEM Forms Workspace*

