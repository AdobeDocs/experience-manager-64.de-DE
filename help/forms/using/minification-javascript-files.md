---
title: Minimierung der JavaScript-Dateien
seo-title: Minification of the JavaScript files
description: Anweisungen zur Generierung von minimiertem Code nach AEM Forms Workspace-Anpassungen zur Optimierung der JS-Dateien für das Web.
seo-description: Instructions to generate minified code after AEM Forms workspace customizations to optimize the JS files for the web.
uuid: ad91e380-a988-4740-9534-e09657e0322a
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: c88a3013-5da2-4b09-9f29-ac1fb00822ec
exl-id: 8394151e-e9cf-4f68-97a3-ba1d1dd6a2d2
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 83%

---

# Minimierung der JavaScript-Dateien {#minification-of-the-javascript-files}

Durch die Minimierung werden die redundanten Zeichen im Quellcode, wie Leerzeichen, neue Zeile und Kommentare, entfernt. Dies verbessert die Leistung, da die Größe des Codes verringert wird. Minimierung wirkt sich nicht auf die Funktion aus, verringert jedoch die Lesbarkeit des Codes.

Um minimierten Code für semantische Änderungen zu generieren, führen Sie folgende Schritte aus.

1. Kopieren `client-html/src/main/webapp/js` von src-package im Dateisystem.

   >[!NOTE]
   >
   >Weitere Informationen finden Sie unter [Einführung zum Anpassen von AEM Forms Workspace](/help/forms/using/introduction-customizing-html-workspace.md) finden Sie weitere Informationen über die Pakete.

1. Pfade in aktualisieren `main.js` befindet sich unter client-html/src/main/webapp/js, für hinzugefügte/aktualisierte Modelle/Ansichten.

   Ändern Sie zum Beispiel nach Hinzufügen eines neuen Sharequeue-Modells mySharequeue:

   ```
   sharequeuemodel : pathprefix + 'runtime/models/sharequeue',
   
   To
   
   sharequeuemodel : pathprefix + 'runtime/myModels/mySharequeue',
   ```

1. Aktualisieren `registry-config.xml, located at client-html/src/main/webapp/js/resource_generator,` falls es eine Änderung/Hinzufügung des Alias in `main.js`.

   Ändern Sie zum Beispiel nach Hinzufügen eines neuen Sharequeue-Modells mySharequeue:

   ```xml
   <sharequeue
               name="sharequeue"
               path="runtime/models/sharequeue.js"
               service="service"/>
   
   To
   
   <sharequeue
               name="sharequeue"
               path="runtime/myModels/mySharequeue.js"
               service="service"/>
   ```

1. Führen Sie unter client-html/src/main/webapp/js/minifier folgenden Befehl aus:

   ```shell
   mvn clean install
   ```

   Es wird ein Ordner minified-files unter client-html/src/main/webapp/js mit minimierten Dateien main.js und registry.js generiert.

>[!NOTE]
>
>Die Minimierung funktioniert nur auf 64-Bit-JVM.

>[!NOTE]
>
>Wenn Sie minimieren, wirkt sich dies auf das Upgrade aus.
