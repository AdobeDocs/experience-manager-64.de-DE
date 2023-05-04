---
title: Ändern der Schriftart auf der Benutzeroberfläche
seo-title: Changing the font on the interface
description: So ändern Sie die Schriftarten in der Benutzeroberfläche selektiv.
seo-description: How to change the fonts on the user interface selectively.
uuid: d079f656-76f8-4908-9989-dde79e215eb2
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 487e3966-443a-408e-b5af-899fcba6fca6
exl-id: bd7ec9d6-b1d2-4f01-8cef-05e5e1eceda1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 39%

---

# Ändern der Schriftart auf der Benutzeroberfläche {#changing-the-font-on-the-interface}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Sie können die in AEM Forms Workspace angezeigte Schriftart ändern. Schriftarten, die in einem bestimmten Bereich der Benutzeroberfläche verwendet werden, werden im entsprechenden Abschnitt des Stylesheets definiert. Sie können die Schriftarten in der Benutzeroberfläche selektiv ändern.

Führen Sie die Anweisungen unter [Generische Schritte zur Anpassung von AEM Forms Workspace](/help/forms/using/generic-steps-html-workspace-customization.md) aus. Befolgen Sie bei Bedarf außerdem die Schritte zum Anpassen von CSS, HTML oder beidem.

1. Ändern Sie die Schriftfamilie in einem vorhandenen Stil oder fügen Sie sie hinzu.
1. Ändern oder fügen Sie die Schriftfamilie inline für das HTML-Element hinzu.
1. Fügen Sie einen Stil hinzu und verwenden Sie ihn für das HTML-Element.

Um beispielsweise die Schriftart für den Anker-Text in der Navigationsleiste oben in Courier New zu ändern, führen Sie die folgenden Schritte aus:

1. Melden Sie sich bei CRXDE Lite an, indem Sie auf `https://[server]:[port]/lc/crx/de/index.jsp` zugreifen.
1. Führen Sie einen der folgenden Schritte aus:

   1. Um die Schriftfamilie in einem vorhandenen Stil zu ändern, fügen Sie Folgendes in der Datei newStyle.css unter /apps/ws/css hinzu.

      ```css
      #topnav a {
         font-family: "Courier New";
      }
      ```

   1. Um die Schriftfamilie für das HTML-Element inline hinzuzufügen, kopieren Sie die Datei `/libs/ws/js/runtime/templates/appnavigation.html` nach`/apps/ws/js/runtime/templates/appnavigation.html`.

      aktualisieren Sie die Datei „/apps/ws/js/runtime/templates/appnavigation.html“ wie folgt:

      ```
      <li class="process"><a href="#" title="<%= $.t('index.header.topnav.startprocess.detail')%>" style="font-family:Courier New;" ><%= $.t('index.header.topnav.startprocess.name')%></a></li>
      <li class="todo"><a href="#/todo" title="<%= $.t('index.header.topnav.todo.detail')%>" style="font-family:Courier New;" ><%= $.t('index.header.topnav.todo.name')%></a></li>
      <li class="track"><a href="#/tracking" title="<%= $.t('index.header.topnav.tracking.detail')%>" style="font-family:Courier New;" ><%= $.t('index.header.topnav.tracking.name')%></a></li>
      <li class="preference"><a href="#/preferences" title="<%= $.t('index.header.topnav.preferences.detail')%>" style="font-family:Courier New;" ><%= $.t('index.header.topnav.preferences.name')%></a></li>
      ```

      Öffnen Sie die Datei „/apps/ws/js/registry.js“ zur Bearbeitung und ersetzen Sie `text!/lc/libs/ws/js/runtime/templates/appnavigation.html` durch `text!/lc/apps/ws/js/runtime/templates/appnavigation.html`.

   1. Um einen Stil hinzuzufügen, der die Schriftfamilie definiert, fügen Sie Folgendes in der Datei newStyle.css unter /apps/ws/css hinzu.

      ```css
      .myNewFontStyle a {
         font-family: "Courier New";
      }
      ```

      Um die Schriftfamilie für das HTML-Element inline hinzuzufügen, fügen Sie Folgendes in der Datei &quot;appnavigation.html&quot;unter /apps/ws/js/runtime/templates hinzu.

      ```css
      <div id="topnav" class="myNewFontStyle">
          <ul>
              <li class="process"><a href="#" title="<%= $.t('index.header.topnav.startprocess.detail')%>" ><%= $.t('index.header.topnav.startprocess.name')%></a></li>
              <li class="todo"><a href="#/todo" title="<%= $.t('index.header.topnav.todo.detail')%>"><%= $.t('index.header.topnav.todo.name')%></a></li>
              <li class="track"><a href="#/tracking" title="<%= $.t('index.header.topnav.tracking.detail')%>" ><%= $.t('index.header.topnav.tracking.name')%></a></li>
              <li class="preference"><a href="#/preferences" title="<%= $.t('index.header.topnav.preferences.detail')%>" ><%= $.t('index.header.topnav.preferences.name')%></a></li>
          </ul>
      </div>
      ```

1. Starten Sie den Arbeitsbereich neu und löschen Sie den Browsercache, damit die Änderungen sichtbar sind.

![change_font_before](assets/change_font_before.png)
**Abbildung:** *Obere Navigationsleiste vor Schriftartanpassung*

![change_font_after](assets/change_font_after.png)
**Abbildung:** *Obere Navigationsleiste nach der Schriftartanpassung auf der ersten Registerkarte*
