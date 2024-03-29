---
title: Hosten von zwei AEM Forms Workspace-Instanzen auf einem Server
seo-title: Hosting two AEM Forms workspace instances on one server
description: Wie LC-Administratoren HTML WS anpassen können, um zwei Instanzen auf einem Server zu hosten, auf den über verschiedene URLs zugegriffen werden kann.
seo-description: How LC administrators can customize HTML WS to host two instances on a single server accessible via different URLs.
uuid: 0584f512-6b92-4418-b71c-93605cfa1927
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 1254a7c2-2c67-4661-803e-afd53e817916
exl-id: ef2ad8e1-5007-4587-97ca-cf21070be9a6
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 68%

---

# Hosten von zwei AEM Forms Workspace-Instanzen auf einem Server {#hosting-two-aem-forms-workspace-instances-on-one-server}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Die Standardinstallation und -einstellungen von AEM Forms lassen nur die Bereitstellung einer AEM Forms Workspace-Instanz auf dem Server zu. Möglicherweise müssen Sie jedoch zwei verschiedene Instanzen von AEM Forms Workspace auf einem AEM Forms-Server hosten. Auf die beiden Instanzen kann über verschiedene URLs zugegriffen werden.

AEM Forms-Administratoren passen Workspace an, um zwei unterschiedliche URLs zu erstellen und zwei Workspace-Instanzen auf demselben Server bereitzustellen. In diesem Artikel zum Thema benutzerdefinierte Anpassung gehen wir davon aus, dass die beiden Arbeitsbereiche unter `https://[server]:[port]/lc/ws` und `https://[server]:[port]:/lc/ws2` bereitstehen.

Führen Sie diese Schritte aus, um AEM Forms Workspace zu konfigurieren.

1. Installieren Sie das Dev-Paket von AEM Forms Workspace auf dem Server. Siehe [dev-Paket](/help/forms/using/introduction-customizing-html-workspace.md#p-crx-package-p), um Anweisungen zur Erstellung zu erhalten.
1. Melden Sie sich bei CRXDE Lite als Administrator an, indem Sie auf `https://[server]:[port]/lc/crx/de/index.jsp` zugreifen.
1. Kopieren Sie den Knoten unter /content und fügen Sie ihn unter /content ein. Benennen Sie den Knoten in &quot;ws2&quot;um. Klicken Sie auf **[!UICONTROL Alle speichern]**. Ändern Sie in den Eigenschaften dieses Knotens den Wert `sling:resourceType` in „ws2“. Klicken Sie auf **[!UICONTROL Alle speichern]**.

1. Kopieren Sie die Ordner aus /libs und fügen Sie sie unter /apps ein. Benennen Sie den Ordner in &quot;ws2&quot;um. Klicken Sie auf **[!UICONTROL Alle speichern]**.
1. Ändern Sie den Code in der Datei `GET.jsp` in der Zeile `/apps/ws2` folgendermaßen. Ersetzen Sie den Code

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

1. Ändern Sie in der Datei `registry.js` in der Zeile `/apps/ws2/js` den Pfad zu den Vorlagen so, dass dieser auf die Vorlagen unter `/apps/ws2/js/runtime/templates` verweist. Ersetzen Sie den folgenden Code

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

1. Ändern Sie in der Datei `userinfo.js` in der Zeile `/apps/ws2/js/runtime/models` und `/apps/ws2/js/runtime/views` den Zeichenfolgenwert von `/lc/content/ws` auf `lc/content/ws2`.

1. Ändern Sie in der Datei `/apps/ws2/js/runtime/services/service.js` den Pfad in der `getLocalizationData`-Funktion so, dass dieser auf `/lc/apps/ws2/Locale.html` verweist.

1. Um auf `pdf.html` des neuen Arbeitsbereich zu verweisen, ändern Sie den Pfad von `pdf.html` auf `/apps/ws2/js/runtime/views/forms/pdftaskform.js`.

1. Um auf `pdf.html` des neuen Arbeitsbereichs zu verweisen, ändern Sie die Pfade von `pdf.html` und `WsNextAdapter.swf` auf `startprocess.html`, `taskdetails.html` und `processinstancehistory.html` in der Zeile `/apps/ws2/js/runtime/templates`.

1. Kopieren Sie den Ordner `/etc/map/ws` und fügen Sie ihn unter `/etc/map` ein. Benennen Sie den neuen Ordner in &quot;ws2&quot;um. Klicken Sie auf Alle speichern.

1. Ändern Sie in den Eigenschaften von `ws2` den Wert von `sling:redirect` auf `content/ws2`.

1. Ändern Sie den Wert von `sling:match` auf `^[^/\||]/[^/\||]/ws2$`.
