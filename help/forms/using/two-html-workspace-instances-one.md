---
title: Hosten von zwei AEM Forms Workspace-Instanzen auf einem Server
seo-title: Hosting two AEM Forms workspace instances on one server
description: Wie können LC-Adminstratoren HTML Workspace anpassen, um zwei Instanzen auf einem Server zu hosten, auf die über unterschiedliche URLs zugegriffen werden kann?
seo-description: How LC administrators can customize HTML WS to host two instances on a single server accessible via different URLs.
uuid: 0584f512-6b92-4418-b71c-93605cfa1927
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 1254a7c2-2c67-4661-803e-afd53e817916
exl-id: ef2ad8e1-5007-4587-97ca-cf21070be9a6
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 67%

---

# Hosten von zwei AEM Forms Workspace-Instanzen auf einem Server {#hosting-two-aem-forms-workspace-instances-on-one-server}

Die Standardinstallation und -einstellungen von AEM Forms lassen nur die Bereitstellung einer AEM Forms Workspace-Instanz auf dem Server zu. Möglicherweise müssen Sie jedoch zwei verschiedene Instanzen von AEM Forms Workspace auf einem AEM Forms-Server hosten. Sie können auf die beiden Instanzen über unterschiedliche URLs zugreifen.

AEM Forms-Administratoren passen Workspace an, um zwei unterschiedliche URLs zu erstellen und zwei Workspace-Instanzen auf demselben Server bereitzustellen. In diesem Anpassungsartikel gehen wir davon aus, dass die beiden Arbeitsbereiche unter `https://[server]:[port]/lc/ws` und `https://[server]:[port]:/lc/ws2`.

Führen Sie folgende Schritte aus, um AEM Forms Workspace zu konfigurieren.

1. Installieren Sie das Dev-Paket von AEM Forms Workspace auf dem Server. Anweisungen zum Erstellen finden Sie unter [Dev-Paket](/help/forms/using/introduction-customizing-html-workspace.md#p-crx-package-p).
1. Melden Sie sich bei CRXDE Lite als Administrator an, indem Sie auf `https://[server]:[port]/lc/crx/de/index.jsp`.
1. Kopieren Sie den Knoten „ws“ unter „/content“ und fügen Sie ihn unter „/content“ ein. Benennen Sie den Knoten in „ws2“ um. Klicken Sie auf **[!UICONTROL Alle speichern]**. Ändern Sie in den Eigenschaften dieses Knotens den Wert `sling:resourceType` in „ws2“. Klicken Sie auf **[!UICONTROL Alle speichern]**.

1. Kopieren Sie den Ordner „ws“ unter „/libs“ und fügen Sie ihn unter „/apps “ein. Benennen Sie den Ordner in „ws2“ um. Klicken Sie auf **[!UICONTROL Alle speichern]**.
1. In `GET.jsp` at `/apps/ws2`, nehmen Sie die folgenden Codeänderungen vor. Ersetzen Sie den Code

   ```
   <html lang="en">
   <head>
       <meta charset="utf-8">
       <title>Workspace Next</title>
       <meta http-equiv="refresh" content="0;URL='/lc/libs/ws/index.html'" /><html lang="en">
   <head>
       <meta charset="utf-8">
       <title>Workspace Next</title>
       <meta http-equiv="refresh" content="0;URL='/lc/libs/ws/index.html'" />
   ```

   durch den folgenden Code

   ```
   <html lang="en">
   <head>
       <meta charset="utf-8">
       <title>Workspace Next</title>
       <meta http-equiv="refresh" content="0;URL='/lc/apps/ws2/index.html'" />
   ```

1. In `registry.js` at `/apps/ws2/js`, ändern Sie den Pfad der Vorlagen, um auf Vorlagen zu verweisen unter `/apps/ws2/js/runtime/templates`. Ersetzen Sie den folgenden Code

   ```css
   "tasklist" : {
   "name": "tasklist",
   "path": "tasklistview",
   "model": "tasklist",
   "template": "text!/lc/libs/ws/js/runtime/templates/tasklist.html",
   "utility": "utility",
   "view": "taskview",
   "errorModel": null
   }
   ```

   durch den folgenden Code

   ```css
   "tasklist" : {
   "name": "tasklist",
   "path": "tasklistview",
   "model": "tasklist",
   "template": "text!/lc/apps/ws2/js/runtime/templates/tasklist.html",
   "utility": "utility",
   "view": "taskview",
   "errorModel": null
   }
   ```

1. In `userinfo.js` at `/apps/ws2/js/runtime/models` und `/apps/ws2/js/runtime/views`, Zeichenfolge ändern `/lc/content/ws` nach `lc/content/ws2`.

1. In `/apps/ws2/js/runtime/services/service.js`ändern Sie den Pfad in `getLocalizationData` -Funktion auf `/lc/apps/ws2/Locale.html`.

1. Siehe `pdf.html` Ändern Sie den Pfad von `pdf.html` in `/apps/ws2/js/runtime/views/forms/pdftaskform.js`.

1. Siehe `pdf.html` Ändern Sie die Pfade von `pdf.html` und `WsNextAdapter.swf` in `startprocess.html`, `taskdetails.html`und `processinstancehistory.html` at `/apps/ws2/js/runtime/templates`.

1. Kopieren `/etc/map/ws` Ordner und Einfügen unter `/etc/map`. Benennen Sie den neuen Ordner in „ws2“ um. Klicken Sie auf „Alle speichern“.

1. In den Eigenschaften von `ws2`, Wert ändern von `sling:redirect` nach `content/ws2`.

1. Wert ändern von `sling:match` nach `^[^/\||]/[^/\||]/ws2$`.
