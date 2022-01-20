---
title: Designanpassung
seo-title: Theme Customization
description: Anpassen des Themas an Ihre AEM Forms-App.
seo-description: How to customize the theme of your AEM Forms app.
uuid: 36632e67-1cc6-416d-ae80-d84bbabab4bd
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: c72f608e-052a-4bf9-b7bc-ddf57483af35
exl-id: fb1e0bec-c943-4468-920d-8ef360a01365
source-git-commit: 2208d23985ebd913b6aa9dee3bf16ce7529a8fa6
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 56%

---

# Designanpassung {#theme-customization}

Sie können den HTML-Code und die CSS-Datei anpassen, um der AEM Forms-App ein unverwechselbares, organisationsspezifisches Erscheinungsbild zu geben. Sie können beispielsweise die Hintergrundfarbe und die Höhe von Aufgaben bzw. Startpunkten ändern. Folgendes Beispiel enthält hierzu Anweisungen:

* Anweisungen statt Beschreibungen anzeigen
* Anzahl der Anzeigewege
* Farbverlauf Hintergrundfarbe

## Schritte {#steps}

1. Öffnen Sie Ihr Projekt.

   * Öffnen Sie für iOS `Capture.xcodeproj` in Xcode
   * In Android öffnen Sie das Android-Projekt in Eclipse.
   * Für Windows öffnen Sie `MWSWindows.sln` in Visual Studio.

1. Navigieren Sie zum Ordner „templates“.

   * Navigieren Sie in Xcode zum **Capture > www > wsmobile > js > runtime > templates** Ordner.
   * Navigieren Sie in Eclipse zum **assets > www > wsmobile > js > runtime > templates** Ordner.
   * Navigieren Sie in Visual Studio zum **MWSWindows > www > wsmobile > js > runtime > templates** Ordner.

1. Öffnen Sie die `template.html` Datei zur Bearbeitung.
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

   * Navigieren Sie in Xcode zu **Capture > www > wsmobile > css**.
   * Navigieren Sie in Eclipse zu **assets > www > wsmobile > css**.
   * Navigieren Sie in Visual Studio zu **MWSWindows > www > wsmobile > css**.

1. Öffnen Sie die `_style.css` Datei zur Bearbeitung.
1. Für Hintergrundbilder ändern Sie `#323232` nach `#fff`.
1. Speichern und schließen Sie die Änderungen `_style.css` -Datei.
1. Öffnen Sie die AEM Forms-App.

   Die AEM Forms-App zeigt jetzt Anweisungen anstelle einer Beschreibung an.
