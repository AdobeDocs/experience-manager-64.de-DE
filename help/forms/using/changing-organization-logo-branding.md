---
title: Ändern des Organisationslogos für das Branding
seo-title: Changing the organization logo for branding
description: Um AEM Forms Workspace mit Marke zu versehen, stellen Sie das Logo Ihres Unternehmens bereit, indem Sie das Standardlogo anpassen.
seo-description: To brand AEM Forms workspace provide the logo of your organization by customizing the default logo.
uuid: f0c340ee-2e54-4bb0-9c30-383cc1bbadb8
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 2c651302-f4ef-4211-b897-f5942ed0ffb1
exl-id: 890e98af-0491-4b59-9a9b-6c245db54f0f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 50%

---

# Ändern des Organisationslogos für das Branding {#changing-the-organization-logo-for-branding}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Das Unternehmenslogo wird in der linken oberen Ecke des AEM Forms Workspace-Fensters angezeigt. Um das Logo zu aktualisieren, folgen Sie dem [Allgemeine Schritte zur Anpassung von AEM Forms Workspace](/help/forms/using/generic-steps-html-workspace-customization.md#generic-steps-for-html-workspace-customization) und dann die folgenden Schritte.

1. Erstellen Sie ein Logo und benennen Sie die Datei als `NewWorkspace.png` Platzieren Sie die Bilddatei mithilfe eines WebDAV-Clients im Ordner /apps/ws/images .

   >[!NOTE]
   >
   >Die empfohlene Größe des Logobilds beträgt 218 px × 20 px.

   >[!NOTE]
   >
   >Weitere Informationen zum WebDAV-Zugriff finden Sie unter [https://dev.day.com/docs/en/crx/current/how_to/webdav_access.html](https://docs.adobe.com/docs/de/crx/current/how_to/webdav_access.html).

1. Erstellen Sie einen Verweis auf das neue Logo im Stylesheet bei „/apps/ws/css/newStyle.css“, indem Sie folgenden Stil hinzufügen.

   ```css
   #logo {
   
          background: url(../images/NewWorkspace.png) no-repeat 14px 11px; 
         }
   ```
