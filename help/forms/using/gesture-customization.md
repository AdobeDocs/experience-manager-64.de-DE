---
title: Gestenanpassung
seo-title: Gesture customization
description: Anpassen der Gesten in Ihrer AEM Forms-App
seo-description: Customize the gestures on your AEM Forms app
uuid: 117e0e21-66bd-42f1-879c-6c1443991974
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 747d13d3-e7cc-4aa1-bcc8-4b57157e71ed
exl-id: 238410e0-1623-49dc-b2fc-b5b2d5fb362b
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 45%

---

# Gestenanpassung {#gesture-customization}

Sie können die Gesten der AEM Forms-App anpassen, um eine unterschiedliche Methode zur Interaktion mit der App bereitzustellen. Beispielsweise können Sie neue Gesten zum Öffnen oder Schließen einer Aufgabe bzw. eines Startpunkts hinzufügen.

## So passen Sie Gesten in der AEM Forms-App an {#to-customize-gestures-in-aem-forms-app}

In der AEM Forms-App wird durch das Wischen nach links eine neue Aufgabe bzw. ein neuer Startpunkt geöffnet, während beim Wischen nach rechts nichts passiert. Im folgenden Beispiel werden Schritte zum Öffnen einer neuen Aufgabe oder eines neuen Startpunkts zum Ausführen der Wischgesten nach rechts in der AEM Forms-App beschrieben.

1. Öffnen Sie Ihr Projekt.

   * Öffnen Sie für iOS `Capture.xcodeproj` in Xcode
   * In Android öffnen Sie das Android-Projekt in Eclipse.
   * Für Windows öffnen Sie `MWSWindows.sln` in Visual Studio.

1. Navigieren Sie zum Ordner &quot;views&quot;und öffnen Sie die `task.js` Datei zur Bearbeitung.

   * Navigieren Sie in Xcode zum **Capture > www > wsmobile > js > runtime > views** Ordner.
   * Navigieren Sie in Eclipse zum **assets > www > wsmobile > js > runtime > views** Ordner.
   * Navigieren Sie in Visual Studio zum **MWSWindows > www > wsmobile > js > runtime > views** Ordner.

   >[!NOTE]
   >
   >Die Datei „task.js“ enthält die Backbone-Ansicht, die mit allen Aufgaben oder Startpunkten in der Aufgaben- oder Startpunktliste verknüpft ist.

1. Suchen Sie in der Datei `task.js` nach der Ereigniseigenschaft der Ansicht.

   Die Ereigniseigenschaft ist eine Zuordnung mit jedem Eintrag im folgenden Format:

   `"EventName Selector": "Function"`

   Beim Trigger eines JavaScript-Ereignisses mit dem Namen `EventName`auf einem HTML-Element, das von `Selector`, die `Function`aufgerufen wird.

1. Suchen

   * &quot;Tippen Sie auf .taskContentArea&quot;: &quot;onTaskClick&quot;,

      &quot;Tippen Sie auf .taskOpenArea&quot;: &quot;onTaskClick&quot;,

      &quot;Tippen Sie auf .task-content&quot;: &quot;onTaskClick&quot;,

      &quot;Tippen Sie auf .last_empty_div : &quot;onTaskClick&quot;,
   und ersetzen Sie diese durch

   * &quot;swipe .taskContentArea&quot; : &quot;onTaskClick&quot;,

      &quot;swipe .taskOpenArea&quot; : &quot;onTaskClick&quot;,

      &quot;swipe .task-content&quot;: &quot;onTaskClick&quot;,

      &quot;swipe .last_empty_div&quot;: &quot;onTaskClick&quot;,


1. Speichern und schließen Sie die Datei `task.js`.
1. Erstellen Sie die AEM Forms-App und führen Sie sie aus. Jetzt können Sie eine Aufgabe mit einem Wischen nach links und rechts öffnen.

Auf ähnliche Weise können Sie Änderungen in anderen Ansichten für verschiedene Kombinationen von Gesten, HTML-Elementen und Funktionen vornehmen.
