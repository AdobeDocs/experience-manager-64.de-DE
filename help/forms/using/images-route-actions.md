---
title: In Route-Aktionen verwendete Bilder anpassen
seo-title: Customize images used in route actions
description: Vorgehensweise zum Anpassen von Bildern, die in Route-Aktionen in LiveCycle AEM Forms Workspace verwendet werden.
seo-description: How-to customize the images used in route actions in LiveCycle AEM Forms workspace.
uuid: 42608376-587e-4b57-a9d5-8f9ebd981426
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 10158c13-47b4-43e3-ac47-690f3cbab158
exl-id: 7b1f60e7-c8fa-43b6-bef4-88b42e7bbc36
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 100%

---

# In Route-Aktionen verwendete Bilder anpassen {#customize-images-used-in-route-actions}

Um die in Route-Aktionen verwendeten Bilder anzupassen, führen Sie die Schritte in [Generische Schritte zur Anpassung](/help/forms/using/generic-steps-html-workspace-customization.md) und anschließend die Schritte in diesem Artikel durch.

## Bilder für Route-Aktionen {#images-for-route-actions}

1. Fügen Sie in CSS am folgenden Speicherort die Stile hinzu, die die Bilder für die neuen Route-Aktionen definieren:

   `/apps/ws/css/newStyle.css`

   Ein Beispiel: Fügen Sie einen neuen Stil mit dem Namen `myStyle1` wie unten gezeigt hinzu und laden Sie die Grafikdatei `myStyleIcon1.png` mithilfe eines WebDAV-Clients in den Ordner `/apps/ws/image` hoch.

   >[!NOTE]
   >
   >Weitere Informationen zum Zugriff über WebDAV finden Sie unter [https://dev.day.com/docs/en/crx/current/how_to/webdav_access.html](https://docs.adobe.com/docs/de/crx/current/how_to/webdav_access.html).

   >[!NOTE]
   >
   >Verwenden Sie den Route-Aktionsnamen auch als den Stilnamen.

   ```css
   .myStyle1{
   
           background-image: url('../images/myStyleIcon1.png');
   
       }
   ```

## Popup bei Tasklist-Aufgabenaktion {#task-list-task-action-popup}

1. Erstellen Sie ein Tasklisten-Aktionspopup siehe [Erstellen von AEM Forms Workspace-Code](introduction-customizing-html-workspace.md#building-html-workspace-code). Dazu muss ein Dev-Paket verwendet werden.

1. Kopieren Sie `/libs/ws/js/runtime/templates/task.html` nach `/apps/ws/js/runtime/templates/task.html`.

1. Wenn der Name des CSS-Stils mit dem Namen der vom Server kommenden Route-Aktion übereinstimmt, ändern Sie den folgenden Code in `/apps/ws/js/runtime/templates/task.html`:

   ```
   <%if(routeList == null){%>
               <li>
                   <a href="javascript:void(0);" title="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0])%>" value="<%= availableCommands.directCommands[0]%>" data-action="route"><%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0])%></a>
               </li>
               <%}else{%>
               <%for(var i = 0; i<availableCommands.directCommands.length; i++){%>
               <li>
                   <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route"><%= availableCommands.directCommands[i]%></a>
               </li>
               <%}%>
               <%}%>
   
   To
   
   <%if(routeList == null){%>
               <li class="<%= availableCommands.directCommands[0]%>" alt="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0]+'.value')%>">
                   <a href="javascript:void(0);" title="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0])%>" value="<%= availableCommands.directCommands[0]%>" data-action="route"><%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0])%></a>
               </li>
               <%}else{%>
               <%for(var i = 0; i<availableCommands.directCommands.length; i++){%>
               <li class="<%= availableCommands.directCommands[i]%>" alt="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[i]+'.value')%>">
                   <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route"><%= availableCommands.directCommands[i]%></a>
               </li>
               <%}%>
               <%}%>
   ```

1. Wenn der Name des CSS-Stils nicht mit dem Namen der vom Server kommenden Route-Aktion übereinstimmt, ändern Sie den folgenden Code in `/apps/ws/js/runtime/templates/task.html`. Er fügt einen Stapel der `if-else`-Servlet-Bedingungen hinzu, um den Stil dem Route-Aktionsnamen zuzuordnen.

```
<%if(routeList == null){%>
            <li>
                <a href="javascript:void(0);" title="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0])%>" value="<%= availableCommands.directCommands[0]%>" data-action="route"><%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0])%></a>
            </li>
            <%}else{%>
            <%for(var i = 0; i<availableCommands.directCommands.length; i++){%>
            <li>
                <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route"><%= availableCommands.directCommands[i]%></a>
            </li>
            <%}%>
            <%}%>
 
To
 
<%if(routeList == null){%>
            <li class="<%= availableCommands.directCommands[0]%>" alt="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0]+'.value')%>">
                <a href="javascript:void(0);" title="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0])%>" value="<%= availableCommands.directCommands[0]%>" data-action="route"><%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0])%></a>
            </li>
            <%}else{%>
            <%for(var i = 0; i<availableCommands.directCommands.length; i++){%>
                <%if(availableCommands.directCommands[i].equals("myAction1")){%>
                     <li class="myStyle1" alt="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[i]+'.value')%>">
                         <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route"><%= availableCommands.directCommands[i]%></a>
                     </li>
                <%}else if(availableCommands.directCommands[i].equals("myAction2")){%>
                     <li class="myStyle2" alt="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[i]+'.value')%>">
                         <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route"><%= availableCommands.directCommands[i]%></a>
                     </li>
                <%}%>
            <%}%>
            <%}%>
```

## Popup bei Aufgabendetails-Aufgabenaktion {#task-details-task-action-popup}

1. Kopieren Sie `/libs/ws/js/runtime/templates/taskdetails.html` nach `/apps/ws/js/runtime/templates/taskdetails.html`.

1. Wenn der Name des CSS-Stils mit dem Namen der vom Server kommenden Route-Aktion übereinstimmt, ändern Sie den folgenden Code in `/apps/ws/js/runtime/templates/taskdetails.html`:

   ```
   <%for (var i = 0; i < availableCommands.directCommands.length; i++) {%>
                           <li class="routeAction">
                               <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route"><%= availableCommands.directCommands[i]%></a>
                           </li>
                       <%}%>
   
   To
   
   <%for (var i = 0; i < availableCommands.directCommands.length; i++) {%>
                           <li class="routeAction">
                               <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route">
                               <i class="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route"/>
                               </a>
                           </li>
                       <%}%>
   ```

1. Wenn der Name des CSS-Stils nicht mit dem Namen der vom Server kommenden Route-Aktion übereinstimmt, ändern Sie den folgenden Code in `/apps/ws/js/runtime/templates/taskdetails.html`. Er fügt einen Stapel der `if-else`-Servlet-Bedingungen hinzu, um den Stil dem Route-Aktionsnamen zuzuordnen.

   ```
   <%for (var i = 0; i < availableCommands.directCommands.length; i++) {%>
                           <li class="routeAction">
                               <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route"><%= availableCommands.directCommands[i]%></a>
                           </li>
                       <%}%>
   
   To
   
   <%for (var i = 0; i < availableCommands.directCommands.length; i++) {%>
                   <%if(availableCommands.directCommands[i].equals("myAction1")){%>
                       <li class="routeAction">
                               <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route">
                               <i class="myStyle1" value="<%= availableCommands.directCommands[i]%>" data-action="route"/>
                               </a>
                           </li>
                   <%}else if(availableCommands.directCommands[i].equals("myAction2")){%>
                       <li class="routeAction">
                               <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route">
                               <i class="myStyle2" value="<%= availableCommands.directCommands[i]%>" data-action="route"/>
                               </a>
                           </li>
                   <%}%>
               <%}%>
   ```

1. Öffnen Sie `/apps/ws/js/registry.js` zur Bearbeitung und suchen Sie den folgenden Text:\
   `"text!/lc/libs/ws/js/runtime/templates/taskdetails.html"`

1. Ersetzen Sie den Text durch Folgendes:\
   `"text!/lc/apps/ws/js/runtime/templates/taskdetails.html"`
