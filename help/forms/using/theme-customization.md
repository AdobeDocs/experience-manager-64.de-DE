---
title: Design-Anpassung
seo-title: Theme Customization
description: Anpassen des Designs Ihrer AEM Forms-App.
seo-description: How to customize the theme of your AEM Forms app.
uuid: 36632e67-1cc6-416d-ae80-d84bbabab4bd
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: c72f608e-052a-4bf9-b7bc-ddf57483af35
exl-id: fb1e0bec-c943-4468-920d-8ef360a01365
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 70%

---

# Design-Anpassung {#theme-customization}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Sie können den HTML-Code und die CSS-Datei anpassen, um der AEM Forms-App ein unverwechselbares, organisationsspezifisches Erscheinungsbild zu geben. Sie können beispielsweise die Hintergrundfarbe und die Höhe von Aufgaben oder Startpunkten ändern. Das folgende Beispiel enthält Anweisungen zum Ändern:

* Anweisungen statt Beschreibungen anzeigen
* Anzahl der Anzeigewege
* Farbverlauf mit Hintergrundfarbe

## Schritte {#steps}

1. Öffnen Sie Ihr Projekt.

   * In iOS öffnen Sie `Capture.xcodeproj` in Xcode
   * In Android öffnen Sie das Android-Projekt in Eclipse.
   * In Windows öffnen Sie `MWSWindows.sln` in Visual Studio.

1. Navigieren Sie zum Ordner „templates“.

   * In Xcode navigieren Sie zum Ordner **Capture > www > wsmobile > js > runtime > templates**.
   * In Eclipse navigieren Sie zum Ordner **assets > www > wsmobile > js > runtime > templates**.
   * In Visual Studio navigieren Sie zum Ordner **MWSWindows > www > wsmobile > js > runtime > templates**.

1. Öffnen Sie die Datei „`template.html`“, um sie zu bearbeiten.
1. Suchen Sie die folgende Zeichenfolge:

   ```
   <%if ( (task.description !== "") && (task.description !== null) && (typeof task.description !== null) && (typeof task.description !== 'undefined') ) {%>
                  <div class="description_details">
                    <%= task.description %>
                  </div>
                 <%} else 
   ```

   Ersetzen Sie sie durch `<%`.

1. Suchen Sie den folgenden Code in der Datei `template.html`:

   ```
   <ul id="task_menu_list">
                                   <li class="approve" title="<%= task.availableCommands.directCommands[0]%>" data-routename="<%= task.availableCommands.directCommands[0]%>">
                                       <%= task.availableCommands.directCommands[0]%>
                                   </li>
                                   <li class="reject last" title="<%= task.availableCommands.directCommands[1]%>" data-routename="<%= task.availableCommands.directCommands[1]%>">
                                       <%= task.availableCommands.directCommands[1]%>
                                   </li>
   ```

1. Geben Sie die folgende Zeile ein und speichern Sie die Datei.

   ```
   task.availableCommands.directCommands[1]%>">
   <%= task.availableCommands.directCommands[1]%>
   </li>
   ```

1. Navigieren Sie zum Ordner „css“.

   * In Xcode navigieren Sie zu **Capture > www > wsmobile > css**.
   * In Eclipse navigieren Sie zu **assets > www > wsmobile > css**.
   * In Visual Studio navigieren Sie zu **MWSWindows > www > wsmobile > css**.

1. Öffnen Sie die Datei „`_style.css`“, um sie zu bearbeiten.
1. Ändern Sie für das Hintergrundbild `#323232` auf `#fff`.
1. Speichern Sie die Änderungen und schließen Sie die Datei `_style.css`.
1. Öffnen Sie die AEM Forms-App.

   Das AEM Forms-Programm zeigt jetzt Anweisungen anstelle von Beschreibungen an.
