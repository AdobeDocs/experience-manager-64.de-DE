---
title: Integrieren von AEM Forms Workspace in Microsoft Office SharePoint Server
seo-title: Integrating AEM forms workspace with Microsoft Office SharePoint Server
description: Sie können AEM forms Workspace mit Microsoft Office SharePoint Server integrieren.
seo-description: You can integrate AEM forms workspace with Microsoft Office SharePoint Server.
uuid: d43396d4-117f-47ea-91e4-10ee96107bc8
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: 1bada670-3e0e-40f4-b9be-8b090df910be
exl-id: 43149456-8ff8-4ce1-9c51-1d950f60ff5d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 20%

---

# Integrieren von AEM Forms Workspace in Microsoft Office SharePoint Server {#integrating-aem-forms-workspace-with-microsoft-office-sharepoint-server}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

**- Voraussetzungen**

**Vorausgesetztes Wissen** 
Bevor Sie AEM Forms Workspace zu SharePoint Server hinzufügen können, benötigen Sie Zugriff auf SharePoint Server mit den entsprechenden Berechtigungen. Außerdem müssen Sie die URL für den Zugriff auf Workspace kennen. Bei den folgenden Schritten wird davon ausgegangen, dass Sie mit dem SharePoint-Server vertraut sind. Weitere Informationen zu Webparts in SharePoint Server finden Sie unter Webparts in Windows SharePoint Services.

**Benutzerebene** Erste Schritte

Sie können AEM Forms Workspace als Webpart in Microsoft Office SharePoint Server (z. B. Microsoft Office SharePoint Server 2007) verwenden. Benutzer können auf AEM Forms Workspace zugreifen, indem sie mithilfe eines Webbrowsers eine Verbindung zu Ihrem SharePoint Server herstellen und so eine einheitliche Plattform erhalten. In diesem Artikel lernen Sie die grundlegenden Schritte zum Anzeigen von AEM Forms Workspace als Webpart in Microsoft Office SharePoint Server kennen. Sie können die in diesem Artikel beschriebenen Schritte ausführen, um ein einheitliches Erlebnis zu bieten, sodass Benutzer, die eine Verbindung zu Ihrem SharePoint-Server herstellen, von demselben Port aus auf AEM Forms Workspace zugreifen können.

>[!NOTE]
>
>Die in diesem Artikel aufgeführten Schritte sind spezifisch für Microsoft SharePoint Server 2007. Sie können auch HTML Workspace mit anderen unterstützten Versionen von Microsoft SharePoint konfigurieren.

## Integrieren von AEM Forms Workspace mit Microsoft Office SharePoint Server 2007 {#integrate-aem-forms-workspace-with-microsoft-office-sharepoint-server}

Führen Sie die folgenden Schritte aus, um AEM Forms Workspace in einen Webpart zu integrieren:

1. Navigieren Sie in einem Webbrowser zur SharePoint-Site, z. B. https://*[myMOSSserver]:*44299/default.aspx wobei *[myMOSSserver]* ist der Name oder die IP-Adresse des Sharepoint Server.

   >[!NOTE]
   >
   >44299 ist die Standardportnummer für den SharePoint-Server. Die Portnummer hängt von Ihrer Installation des SharePoint-Servers ab.

1. Klicken Sie oben rechts auf der Webseite auf **Site-Aktionen** und wählen Sie **Seite bearbeiten**.
1. Klicken Sie auf die Schaltfläche **Webpart hinzufügen.**
1. Wählen Sie im Dialogfeld Webparts hinzufügen - Web-Seite unter Verschiedenes die Option **Seiten-Viewer-Webpart** und klicken Sie anschließend auf **Hinzufügen**.
1. Klicken Sie im Feld &quot;Seiten-Viewer-Webpart&quot;auf **edit** und wählen Sie **Freigegebenen Webpart ändern**.

   >[!NOTE]
   >
   >Das Feld &quot;Seiten-Viewer-Webpart&quot;wird unter dem **Webpart hinzufügen** -Schaltfläche, auf die Sie in Schritt 3 geklickt haben, wie in der folgenden Abbildung dargestellt (Abbildung 1):

   ![Feld „Seiten-Viewer-Webpart“ in Microsoft Office SharePoint Server.](assets/page-viewer-web-part-box-in-microsoft-office-sharepoint-server.png)

   **Abbildung:** *Das Feld &quot;Seiten-Viewer-Webpart&quot;im Microsoft Office SharePoint-Server.*

1. Führen Sie auf der Seite &quot;Seiten-Viewer&quot;die folgenden Aufgaben aus:

   1. Geben Sie in das Feld Link die URL von AEM Forms Workspace ein, z. B. https://*[AEM_forms_Server]:*8080/lc/ws, wobei *[AEM_forms_Server]* steht für die IP-Adresse oder den Namen AEM Formularservers.
   1. Klicken **Erscheinungsbild** und ändern Sie Höhe, Breite und Titel, sodass Sie die gesamte Workspace-Benutzeroberfläche sehen können. Sie können beispielsweise Höhe und Breite auf 6 Zoll bzw. 11 Zoll festlegen.
   1. Klicken **Testlink**. Es wird ein neues Webbrowser-Fenster mit Workspace angezeigt.
   1. (Optional) Klicken Sie auf **Layout** und ändern Sie das Layout von Workspace im Webpart.
   1. (Optional) Klicken Sie auf **Erweitert** und ändern Sie andere Einstellungen, z. B. die Beschreibung und ob Workspace im Webpart minimiert oder geschlossen werden kann.

      Klicken Sie auf **Übernehmen**.

1. Klicken **Bearbeitungsmodus beenden** und überprüfen Sie, dass Sie auf Workspace zugreifen können.

Nachdem Sie die oben genannten Schritte ausgeführt haben, sieht Ihre SharePoint-Site in etwa wie in der folgenden Abbildung dargestellt aus (Abbildung 2):

![AEM Forms Workspace in Microsoft Office SharePoint Server integriert](assets/aem-forms-workspace.jpg)

**Abbildung:** *AEM Forms Workspace ist mit Microsoft Office SharePoint Server integriert*
