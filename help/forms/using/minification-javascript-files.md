---
title: Minimierung der JavaScript-Dateien
seo-title: Minification of the JavaScript files
description: Anleitung zum Generieren von minimiertem Code nach AEM Forms Workspace-Anpassungen zur Optimierung der JS-Dateien für das Web.
seo-description: Instructions to generate minified code after AEM Forms workspace customizations to optimize the JS files for the web.
uuid: ad91e380-a988-4740-9534-e09657e0322a
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: c88a3013-5da2-4b09-9f29-ac1fb00822ec
exl-id: 8394151e-e9cf-4f68-97a3-ba1d1dd6a2d2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 37%

---

# Minimierung der JavaScript-Dateien {#minification-of-the-javascript-files}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Durch die Minimierung werden die redundanten Zeichen, wie Leerzeichen, neue Zeile und Kommentare, aus dem Quellcode entfernt. Dies verbessert die Leistung, indem die Größe des Codes verringert wird. Die Minimierung wirkt sich nicht auf die Funktionalität aus, verringert jedoch die Lesbarkeit des Codes.

Gehen Sie wie folgt vor, um minimierten Code für semantische Änderungen zu generieren.

1. Kopieren Sie `client-html/src/main/webapp/js` von „src-package“ nach „filesystem“.

   >[!NOTE]
   >
   >Weitere Informationen finden Sie unter [Einführung zum Anpassen von AEM Forms Workspace](/help/forms/using/introduction-customizing-html-workspace.md) finden Sie weitere Informationen über die Pakete.

1. Aktualisieren Sie die Pfade in `main.js`, die sich unter client-html/src/main/webapp/js befinden, für hinzugefügte bzw. aktualisierte Modelle oder Ansichten.

   Ändern Sie zum Beispiel nach Hinzufügen eines neuen Sharequeue-Modells mySharequeue:

   ```
   sharequeuemodel : pathprefix + 'runtime/models/sharequeue',
   
   To
   
   sharequeuemodel : pathprefix + 'runtime/myModels/mySharequeue',
   ```

1. Aktualisieren Sie `registry-config.xml, located at client-html/src/main/webapp/js/resource_generator,`, falls es eine Änderung/Hinzufügung des Alias in `main.js` gibt.

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

1. Führen Sie unter client-html/src/main/webapp/js/minifier den Befehl aus:

   ```shell
   mvn clean install
   ```

   Es wird ein Ordner minified-files unter client-html/src/main/webapp/js mit minimiertem main.js und registry.js generiert.

>[!NOTE]
>
>Die Minimierung funktioniert nur auf 64-Bit-JVM.

>[!NOTE]
>
>Wenn Sie die Aktualisierung verkleinern, wirkt sich dies auf die Aktualisierung aus.
