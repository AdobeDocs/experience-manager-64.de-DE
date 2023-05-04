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
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1070'
ht-degree: 48%

---

# Anpassungsfähige Formulare in externe Web-Seiten einbetten{#embed-adaptive-form-in-external-web-page}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Erfahren Sie, wie Sie ein adaptives Formular in eine externe Webseite einbetten

Sie können [Adaptives Formular in AEM Sites einbetten](/help/forms/using/embed-adaptive-form-aem-sites.md) Seite oder einer Webseite, die außerhalb von AEM gehostet wird. Das eingebettete adaptive Formular ist voll funktionsfähig, und Benutzende können es ausfüllen und senden, ohne die Seite zu verlassen. Es hilft Benutzenden, im Kontext anderer Elemente auf der Web-Seite zu bleiben und gleichzeitig mit dem Formular zu interagieren.

## Voraussetzungen {#prerequisites}

Führen Sie die folgenden Schritte aus, bevor Sie ein adaptives Formular in eine externe Website einbetten:

* Veröffentlichen Sie das adaptive Formular in der AEM-Veröffentlichungsinstanz.
* Erstellen Sie auf Ihrer Website eine Webseite oder legen Sie sie fest, um das adaptive Formular zu hosten. Stellen Sie sicher, dass die Webseite [jQuery-Dateien von einem CDN lesen](https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js) kann oder eine lokale Kopie von jQuery eingebettet hat. jQuery ist erforderlich, um ein adaptives Formular zu rendern.
* Wenn AEM-Server und die Web-Seite sich in verschiedenen Domains befinden, führen Sie die im Abschnitt [Bereitstellung adaptiver Formulare auf einer Domain-übergreifenden Site durch AEM Forms](#cross-domain-sites) beschriebenen Schritte aus.
* [Reverse Proxy einrichten](#reveseproxy) um die Kommunikation zwischen einer externen Seite und dem AEM Forms-Server zu aktivieren.

## Adaptives Formular einbetten {#embed-adaptive-form}

Sie können ein adaptives Formular einbetten, indem Sie einige Zeilen JavaScript in die Web-Seite einfügen. Die API im Code sendet eine HTTP-Anforderung an den AEM-Server für adaptive Formularressourcen und fügt das adaptive Formular in den angegebenen Formularcontainer ein. Hier finden Sie einen Beispielcode zum Einbetten eines adaptiven Formulars in eine externe Seite. Verwenden Sie den Code nicht so, wie er sich in einer Produktionsumgebung befindet. Passen Sie den Code an Ihre Website an, z. B. die Verwendung eines iFrame für Websites, die ihre eigene Version von jQuery verwenden. Die Verwendung von iFrame hilft, Konflikte innerhalb von jQuery-Versionen zu vermeiden:


1. Betten Sie den folgenden Code in eine Webseite auf Ihrer Website ein:

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

   * Ersetzen Sie den Wert der Variablen `options.path` durch die Veröffentlichungs-URL des adaptiven Formulars. Wenn der AEM-Server in einem Kontextpfad ausgeführt wird, stellen Sie sicher, dass die URL diesen Pfad enthält. Beispielsweise befinden sich der obige Code und das adaptive Formular auf demselben AEM forms-Server, sodass das Beispiel den Kontextpfad des adaptiven Formulars /content/forms/af/locbasic.html verwendet.
   * Ersetzen Sie `options.dataRef` durch Attribute, die mit der URL übertragen werden sollen. Sie können die Variable dataref zum [Vorausfüllen eines adaptiven Formulars](/help/forms/using/prepopulate-adaptive-form-fields.md) verwenden.
   * Ersetzen `options.themePath` mit dem Pfad zu einem anderen Design als dem im adaptiven Formular konfigurierten Design. Alternativ können Sie den Designpfad mit dem Anfrageattribut angeben.
   * `CSS_Selector` ist der CSS-Selektor des Formularcontainers, in den das adaptive Formular eingebettet ist. Im obigen Beispiel ist die CSS-Klasse „.customafsection“ der CSS-Selektor.

Das adaptive Formular ist in die Webseite eingebettet. Beachten Sie Folgendes im eingebetteten adaptiven Formular:

* Kopf- und Fußzeile im ursprünglichen adaptiven Formular sind nicht im eingebetteten Formular enthalten.
* Entwürfe und übermittelte Formulare sind auf der entsprechenden Registerkarte im Forms Portal verfügbar.
* Die im ursprünglichen adaptiven Formular konfigurierte Sendeaktion wird im eingebetteten Formular beibehalten.
* Die Regeln für adaptive Formulare werden beibehalten und im eingebetteten Formular vollständig verwendet.
* Erlebnis-Targeting und im ursprünglichen adaptiven Formular konfigurierte A/B-Tests funktionieren im eingebetteten Formular nicht.
* Wenn Adobe Analytics im Originalformular konfiguriert ist, werden die Analysedaten auf dem Adobe Analytics-Server erfasst. Sie ist jedoch nicht im Forms-Analysebericht verfügbar.

## Reverse Proxy einrichten  {#reveseproxy}

Die externe Webseite, die das adaptive Formular einbettet, sendet Anforderungen an den AEM-Server, der sich normalerweise hinter der Firewall in einem privaten Netzwerk befindet. Um sicherzustellen, dass die Anfragen sicher an den AEM-Server weitergeleitet werden, wird empfohlen, einen Reverse-Proxy-Server einzurichten.

Sehen wir uns ein Beispiel an, wie Sie einen Apache 2.4 Reverse-Proxy-Server ohne Dispatcher einrichten können. In diesem Beispiel hosten Sie den AEM-Server mit dem Kontextpfad `/forms` und weisen `/forms` für den Reverse-Proxy zu. Dadurch wird sichergestellt, dass alle Anforderungen für `/forms` auf dem Apache-Server an die AEM-Instanz geleitet werden. Diese Topologie hilft dabei, die Anzahl der Regeln auf der Dispatcher-Ebene zu reduzieren, da alle Anforderungen mit dem Präfix `/forms` an den AEM-Server weitergeleitet werden.

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

   Ersetzen Sie in den Regeln `[AEM_Instance]` durch die Veröffentlichungs-URL des AEM-Servers.

Wenn Sie den AEM-Server nicht in einem Kontextpfad bereitstellen, lauten die Proxy-Regeln auf Apache-Ebene wie folgt:

```java
ProxyPass /content https://<AEM_Instance>/content
ProxyPass /etc https://<AEM_Instance>/etc
ProxyPass /etc.clientlibs https://<AEM_Instance>/etc.clientlibs
# CSRF Filter

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
ProxyPass /libs/granite/csrf/token.json https://<AEM_Instance>/libs/granite/csrf/token.json
  
ProxyPassReverse /etc https://<AEM_Instance>/etc
ProxyPassReverse /etc.clientlibs https://<AEM_Instance>/etc.clientlibs
# written for thank you page and other URL present in AF during redirect

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
ProxyPassReverse /content https://<AEM_Instance>/content
```

>[!NOTE]
>
>Wenn Sie eine andere Topologie einrichten, stellen Sie sicher, dass Sie die URLs für Senden, Vorausfüllen und andere Funktionen auf der Dispatcher-Ebene in die Positivliste eintragen.

## Best Practices {#best-practices}

Beachten Sie beim Einbetten eines adaptiven Formulars in eine Webseite die folgenden Best Practices:

* Stellen Sie sicher, dass die Stilregeln, die in der CSS der Webseite definiert sind, nicht mit dem CSS des Formularobjekts in Konflikt stehen. Um Konflikte zu vermeiden, können Sie das CSS der Webseite im Thema für adaptive Formulare mithilfe AEM Client-Bibliothek wiederverwenden. Informationen zur Verwendung der Client-Bibliothek in Designs für adaptive Formulare finden Sie unter [Designs in AEM Forms](/help/forms/using/themes.md).
* Stellen Sie sicher, dass der Formularcontainer auf der Webseite die gesamte Fensterbreite verwendet. Dadurch wird sichergestellt, dass die für Mobilgeräte konfigurierten CSS-Regeln ohne Änderungen funktionieren. Wenn der Formular-Container nicht die gesamte Fensterbreite benötigt, müssen Sie benutzerdefiniertes CSS schreiben, damit das Formular an verschiedene Mobilgeräte angepasst werden kann.
* Verwendung  [getData](https://helpx.adobe.com/experience-manager/6-4/forms/javascript-api/GuideBridge.html) API zum Abrufen der XML- oder JSON-Darstellung von Formulardaten im Client.
* Verwendung [unloadAdaptiveForm](https://helpx.adobe.com/experience-manager/6-4/forms/javascript-api/GuideBridge.html) API zum Entladen des adaptiven Formulars vom HTML-DOM.
* Richten Sie den Header „access-control-origin“ ein, wenn Sie eine Antwort vom AEM-Server senden.

## Bereitstellung adaptiver Formulare auf einer Domain-übergreifenden Site durch AEM Forms  {#cross-domain-sites}

1. Gehen Sie in der AEM-Veröffentlichungsinstanz zum Konfigurations-Manager der AEM-Web-Konsole unter `http://[server]:[port]/system/console/configMgr`.
1. Suchen und öffnen Sie die **Apache Sling Referrer** Filterkonfiguration.
1. Im **Zulässige Hosts** Geben Sie die Domäne an, in der sich die Webseite befindet. Dadurch kann der Host POST-Anforderungen an den AEM-Server senden. Sie können auch einen regulären Ausdruck verwenden, um eine Reihe von externen Anwendungs-Domains anzugeben.
