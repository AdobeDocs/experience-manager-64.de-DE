---
title: Anpassungsfähige Formulare in externe Web-Seiten einbetten
seo-title: Embed adaptive form in external web page
description: Erfahren Sie, wie Sie ein adaptives Formular in eine externe Webseite einbetten
seo-description: Learn how to embed an adaptive form in an external HTML web page
uuid: c612ca3b-62f7-4021-939b-e0c05dbbf0d7
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: author
discoiquuid: b99c7b93-ba05-42ee-9ca8-0079e15d8602
feature: Adaptive Forms
exl-id: 84a46197-9933-4b94-a8e3-e7baf9c644b1
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1034'
ht-degree: 65%

---

# Anpassungsfähige Formulare in externe Web-Seiten einbetten{#embed-adaptive-form-in-external-web-page}

Erfahren Sie, wie Sie ein adaptives Formular in eine externe Webseite einbetten

Sie können [Adaptives Formular in AEM Sites einbetten](/help/forms/using/embed-adaptive-form-aem-sites.md) Seite oder einer Webseite, die außerhalb von AEM gehostet wird. Das eingebettete adaptive Formular ist voll funktionsfähig und Benutzer können es ausfüllen und senden, ohne die Seite zu verlassen. Es hilft Benutzern, im Kontext anderer Elemente auf der Webseite zu bleiben und gleichzeitig mit dem Formular zu interagieren.

## Voraussetzungen {#prerequisites}

Führen Sie folgende Schritte aus, bevor Sie ein adaptives Formular in eine externe Webseite einbetten::

* Veröffentlichen Sie das adaptive Formular in einer AEM-Veröffentlichungsinstanz.
* Erstellen Sie auf Ihrer Website eine Webseite oder legen Sie sie fest, um das adaptive Formular zu hosten. Stellen Sie sicher, dass die Webseite [jQuery-Dateien aus einem CDN lesen](https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js) oder eine lokale Kopie der jQuery eingebettet hat. jQuery ist erforderlich, um ein adaptives Formular zu rendern.
* Wenn sich AEM Server und die Webseite auf unterschiedlichen Domänen befinden, führen Sie die im Abschnitt aufgeführten Schritte aus. [AEM Forms aktivieren, um adaptive Formulare für eine domänenübergreifende Site bereitzustellen](#cross-domain-sites).
* [Reverse Proxy einrichten](#reveseproxy) um die Kommunikation zwischen einer externen Seite und dem AEM Forms-Server zu aktivieren.

## Adaptives Formular einbetten {#embed-adaptive-form}

Sie können ein adaptives Formular einbetten, indem Sie einige JavaScript-Zeilen in die Webseite einfügen. Die API im Code sendet eine HTTP-Anforderung an den AEM-Server für adaptive Formularressourcen und fügt das adaptive Formular in den angegebenen Formularcontainer ein. Hier finden Sie einen Beispielcode zum Einbetten eines adaptiven Formulars in eine externe Seite. Verwenden Sie den Code nicht so, wie er sich in einer Produktionsumgebung befindet. Passen Sie den Code an Ihre Website an, z. B. die Verwendung eines iFrame für Websites, die ihre eigene Version von jQuery verwenden. Die Verwendung von iFrame hilft, Konflikte innerhalb von jQuery-Versionen zu vermeiden:


1. Betten Sie den folgenden Code in eine Webseite in Ihrer Website ein:

   ```html
   <!doctype html>
   <html>
   <head>
    <title>This is the title of the webpage!</title>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
   </head>
   <body>
   <div class="customafsection"/>
   <p>This section is replaced with the adaptive form.</p>
   
    <script>
    var options = {path:"/content/forms/af/locbasic.html", dataRef:"", themepath:"", CSS_Selector:".customafsection"};
    alert(options.path);
    var loadAdaptiveForm = function(options){
    //alert(options.path);
    if(options.path) {
        // options.path refers to the publish URL of the adaptive form
        // For Example: http:myserver:4503/content/forms/af/ABC, where ABC is the adaptive form
        // Note: If AEM server is running on a context path, the adaptive form URL must contain the context path 
        var path = options.path;
        path += "/jcr:content/guideContainer.html";
        $.ajax({
            url  : path ,
            type : "GET",
            data : {
                // Set the wcmmode to be disabled
                wcmmode : "disabled"
                // Set the data reference, if any
               // "dataRef": options.dataRef
                // Specify a different theme for the form object
              //  "themeOverride" : options.themepath
            },
            async: false,
            success: function (data) {
                // If jquery is loaded, set the inner html of the container
                // If jquery is not loaded, use APIs provided by document to set the inner HTML but these APIs would not evaluate the script tag in HTML as per the HTML5 spec
                // For example: document.getElementById().innerHTML
                if(window.$ && options.CSS_Selector){
                    // HTML API of jquery extracts the tags, updates the DOM, and evaluates the code embedded in the script tag.
                    $(options.CSS_Selector).html(data);
                }
            },
            error: function (data) {
                // any error handler
            }
        });
    } else {
        if (typeof(console) !== "undefined") {
            console.log("Path of Adaptive Form not specified to loadAdaptiveForm");
        }
    }
    }(options);
   
    </script>
   </body>
   </html>
   ```

1. Im eingebetteten Code:

   * Wert der `options.path` mit dem Pfad der Veröffentlichungs-URL des adaptiven Formulars. Wenn der AEM-Server in einem Kontextpfad ausgeführt wird, stellen Sie sicher, dass die URL diesen Pfad enthält. Beispielsweise befinden sich der Code und das adaptive Formular im Beispiel oben auf demselben AEM Forms-Server, daher wird im Kontextpfad dieses Beispiels der Pfad /content/forms/af/locbasic.html für das adaptive Formular verwendet.
   * Ersetzen Sie `options.dataRef` durch Attribute, die mit der URL übertragen werden sollen. Sie können die dataref-Variable verwenden, um [Vorausfüllen eines adaptiven Formulars](/help/forms/using/prepopulate-adaptive-form-fields.md).
   * Ersetzen Sie `options.themePath` durch den Pfad zu einem anderen Design als dem im adaptiven Formular konfigurierten Design. Alternativ können Sie den Designpfad mit dem Anforderungsattribut angeben.
   * `CSS_Selector` ist der CSS-Selektor des Formularcontainers, in den das adaptive Formular eingebettet ist. Beispielsweise ist die CSS-Klasse .customafsection im obigen Beispiel der CSS-Selektor.

Das adaptive Formular wird in die Webseite eingebettet. Beobachten Sie Folgendes im eingebetteten adaptiven Formular:

* Die Kopf- und Fußzeile im adaptiven Originalformular werden nicht vom eingebetteten Formular übernommen.
* Entwürfe und übermittelte Formulare sind auf der entsprechenden Registerkarte im Forms Portal verfügbar.
* Die im adaptiven Originalformular konfigurierte Aktion wird im eingebetteten Formular beibehalten.
* Regeln für adaptive Formulare bleiben erhalten und sind im eingebetteten Formular voll funktionsfähig.
* Die im Originalformular konfigurierten Erlebnis-Targeting und A/B-Tests funktionieren im eingebetteten adaptiven Formular nicht.
* Wenn Adobe Analytics im ursprünglichen Formular konfiguriert ist, werden die Analysedaten im Adobe Analytics-Server erfasst. Sie sind jedoch nicht im Formularanalysebericht verfügbar.

## Reverse Proxy einrichten  {#reveseproxy}

Die externe Webseite, in die das adaptive Formular eingebettet wird, sendet Anforderungen an den AEM-Server, der sich in der Regel hinter der Firewall in einem privaten Netzwerk befindet. Um sicherzustellen, dass die Anforderungen sicher auf den AEM-Server geleitet werden, wird empfohlen, einen Reverse-Proxy-Server einzurichten.

Schauen wir uns ein Beispiel an, wie Sie einen Apache 2.4-Reverse-Proxy-Server ohne Dispatcher einrichten können. In diesem Beispiel hosten Sie den AEM-Server mit `/forms` Kontextpfad und Zuordnung `/forms` für den Reverse-Proxy. Dadurch wird sichergestellt, dass alle Anfragen an `/forms` auf dem Apache-Server werden zur AEM-Instanz weitergeleitet. Diese Topologie hilft dabei, die Anzahl der Regeln auf der Dispatcher-Ebene zu reduzieren, da alle Anforderungen mit dem Präfix `/forms` zum AEM Server weitergeleitet.

1. Öffnen Sie die Konfigurationsdatei `httpd.conf` und heben Sie den Kommentar für die folgenden Codezeilen auf. Alternativ können Sie die folgenden Codezeilen in die Datei einfügen.

   ```
   LoadModule proxy_html_module modules/mod_proxy_html.so 
    LoadModule proxy_http_module modules/mod_proxy_http.so
   ```

1. Richten Sie Proxy-Regeln ein, indem Sie die folgenden Codezeilen in der Konfigurationsdatei `httpd-proxy.conf` hinzufügen.

   ```
   ProxyPass /forms https://[AEM_Instance]/forms 
    ProxyPassReverse /forms https://[AEM_Instance]/forms
   ```

   Ersetzen `[AEM_Instance]` mit der Veröffentlichungs-URL des AEM-Servers in den Regeln.

Wenn Sie den AEM-Server nicht auf einem Kontextpfad bereitstellen, lauten die Proxy-Regeln auf der Apache-Ebene wie folgt:

```java
ProxyPass /content https://<AEM_Instance>/content
ProxyPass /etc https://<AEM_Instance>/etc
ProxyPass /etc.clientlibs https://<AEM_Instance>/etc.clientlibs
# CSRF Filter
ProxyPass /libs/granite/csrf/token.json https://<AEM_Instance>/libs/granite/csrf/token.json
  
ProxyPassReverse /etc https://<AEM_Instance>/etc
ProxyPassReverse /etc.clientlibs https://<AEM_Instance>/etc.clientlibs
# written for thank you page and other URL present in AF during redirect
ProxyPassReverse /content https://<AEM_Instance>/content
```

>[!NOTE]
>
>Wenn Sie eine andere Topologie einrichten, stellen Sie sicher, dass Sie die URLs zum Senden, Vorbefüllen und andere URLs zur Zulassungsliste auf der Dispatcher-Ebene hinzufügen.

## Best Practices {#best-practices}

Berücksichtigen Sie beim Einbetten eines adaptiven Formulars in eine Webseite die folgenden Richtlinien:

* Stellen Sie sicher, dass die Formatierungsregeln in den Webseite-CSS nicht mit den Formularobjekt-CSS in Konflikt stehen. Um dies zu vermeiden, können Sie die Webseite-CSS im Design für das adaptive Formular mithilfe der AEM-Clientbibliothek wiederverwenden. Weitere Informationen zur Verwendung der Client-Bibliothek in den Designs für adaptive Formulare finden Sie unter [Designs in AEM Forms](/help/forms/using/themes.md).
* Verwenden Sie für den Formularcontainer auf der Webseite die gesamte Fensterbreite. So wird sichergestellt, dass die für mobile Geräte konfigurierten CSS-Regeln ohne Änderungen funktionieren. Wenn der Formularcontainer nicht die gesamte Fensterbreite einnimmt, müssen Sie benutzerdefinierte CSS schreiben, damit sich das Formular an verschiedene mobile Geräte anpasst.
* Verwendung  [getData](https://helpx.adobe.com/de/experience-manager/6-4/forms/javascript-api/GuideBridge.html) API zum Abrufen der XML- oder JSON-Darstellung von Formulardaten im Client.
* Verwendung [unloadAdaptiveForm](https://helpx.adobe.com/experience-manager/6-4/forms/javascript-api/GuideBridge.html) API zum Entladen des adaptiven Formulars vom HTML-DOM.
* Richten Sie den Header access-control-origin ein, wenn Sie eine Antwort von AEM Server senden.

## Bereitstellung adaptiver Formulare auf einer domänenübergreifenden Site durch AEM Forms  {#cross-domain-sites}

1. Wechseln Sie in AEM Veröffentlichungsinstanz zu AEM Web Console Configuration Manager unter `http://[server]:[port]/system/console/configMgr`.
1. Suchen und öffnen Sie die **Apache Sling Referrer** Filterkonfiguration.
1. Geben Sie im Feld **Zulässige Hosts** die Domäne an, in der sich die Webseite befindet. Dadurch kann der Host POST-Anforderungen an den AEM-Server senden. Sie können auch einen regulären Ausdruck verwenden, um eine Reihe von externen Anwendungsdomänen anzugeben.
