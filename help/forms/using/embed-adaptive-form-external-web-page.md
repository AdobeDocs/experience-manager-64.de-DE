---
title: Anpassungsfähige Formulare in externe Webseiten einbetten
seo-title: Anpassungsfähige Formulare in externe Webseiten einbetten
description: Erfahren Sie, wie Sie ein adaptives Formular in eine externe Webseite einbetten
seo-description: Erfahren Sie, wie Sie ein adaptives Formular in eine externe HTML-Seite einbetten
uuid: c612ca3b-62f7-4021-939b-e0c05dbbf0d7
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: author
discoiquuid: b99c7b93-ba05-42ee-9ca8-0079e15d8602
translation-type: tm+mt
source-git-commit: 61c9abca40007271f1fba49d3d5e3136df91938d
workflow-type: tm+mt
source-wordcount: '1271'
ht-degree: 55%

---


# Anpassungsfähige Formulare in externe Webseiten einbetten{#embed-adaptive-form-in-external-web-page}

Erfahren Sie, wie Sie ein adaptives Formular in eine externe Webseite einbetten

You can [Embed adaptive form in AEM Sites](/help/forms/using/embed-adaptive-form-aem-sites.md) page or a web page hosted outside AEM. Das eingebettete adaptive Formular ist voll funktionsfähig und Benutzer können es ausfüllen und senden, ohne die Seite zu verlassen. Es hilft Benutzern, im Kontext anderer Elemente auf der Webseite zu bleiben und gleichzeitig mit dem Formular zu interagieren.

## Voraussetzungen {#prerequisites}

Führen Sie die folgenden Schritte aus, bevor Sie ein adaptives Formular in eine externe Website einbetten:

* Veröffentlichen Sie das adaptive Formular in einer AEM-Veröffentlichungsinstanz.
* Erstellen Sie auf Ihrer Website eine Webseite oder legen Sie sie fest, um das adaptive Formular zu hosten. Ensure that the webpage can [read jQuery files from a CDN](https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js) or has a local copy of the jQuery embeded. jQuery ist erforderlich, um ein adaptives Formular zu rendern.
* When AEM server and the web page are on different domains, perform the steps listed in sectiion, [enable AEM Forms to serve adaptive forms to a cross domain site](#cross-domain-sites).
* [Richten Sie den Reverse-Proxy](#reveseproxy) ein, um die Kommunikation zwischen der externen Seite und dem AEM Forms-Server zu aktivieren.

## Adaptives Formular einbetten {#embed-adaptive-form}

Sie können ein adaptives Formular einbetten, indem Sie einige Zeilen JavaScript in die Webseite einfügen. Die API im Code sendet eine HTTP-Anforderung an den AEM-Server für adaptive Formularressourcen und fügt das adaptive Formular in den angegebenen Formularcontainer ein. Im Folgenden finden Sie einen Beispielcode zum Einbetten eines adaptiven Formulars in eine externe Seite. Verwenden Sie den Code nicht so, wie er sich in einer Produktions-Umgebung befindet. Passen Sie den Code an Ihre Website an, wie z. B. die Verwendung eines iFrames für Websites, die eine eigene Version von jQuery verwenden. Die Verwendung von iFrame hilft, Konflikte innerhalb von jQuery-Versionen zu vermeiden:


1. Betten Sie den folgenden Code in eine Webseite in Ihrer Website ein:

   ```
   
   
<!doctype html>
<html>
  <head><meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
    <title>Dies ist der Titel der Webseite!</title>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
  </head>
  <body>
  <div class="customafsection"/>
    <p>Dieser Abschnitt wird durch das adaptive Formular ersetzt.</p>


    &lt;script>
    var options = {path:&quot;/content/forms/af/locbasic.html&quot;, dataRef:&quot;, theepath:&quot;, CSS_Selector:&quot;.customafsection&quot;};
    alert(options.path);
    var loadAdaptiveForm = function(options){
    //alert(options.path);
    if(options.path) {
    // options.path bezieht sich auf die Veröffentlichungs-URL des adaptiven Formulars
    // Beispiel: http:myserver:4503/content/forms/af/ABC, wobei ABC das adaptive Formular
    // Hinweis ist: Wenn der AEM-Server auf einem Kontextpfad ausgeführt wird, muss die URL des adaptiven Formulars den
    Pfad context pathvar path = options.path;
    path += &quot;/jcr:content/guideContainer.html&quot;;
    $.ajax({
    url : path,
    type : &quot;GET&quot;,
    Daten: {
    // Setzen Sie wcmmode auf
    disabledwcmmode : &quot;disabled&quot;
    // Legen Sie die Datenreferenz fest, falls vorhanden
    // &quot;dataRef&quot;: options.dataRef
    // Festlegen eines anderen Designs für das Formularobjekt
    // &quot;themeOverride&quot; : options.themepath
    },
    async: false,
    success: function (data) {
    // Wenn jquery geladen wird, stellen Sie den inneren HTML-Code des Containers
    // Wenn jquery nicht geladen wird, verwenden Sie APIs, die von Dokument bereitgestellt werden, um den inneren HTML-Code festzulegen, aber diese APIs werten das Skript-Tag nicht in HTML gemäß HTML5 spec
    // aus. Beispiel: Dokument.getElementById().
    innerHTMLif(window.$ &amp;&amp; options.CSS_Selector){
    // HTML-API von jquery extrahiert die Tags, aktualisiert das DOM und wertet den im script-Tag eingebetteten Code aus.
    $(options.CSS_Selector).html(data);
    }
    },
    error: function (data) {
    // any error handler
    }
    });
    } else {
    if (typeof(console) !== &quot;undefined&quot;) {
    console.log(&quot;Path of Adaptive Form not specified to loadAdaptiveForm&quot;);
    }
    }
    }(options);
    
    &lt;/script>
</body>
</html>
   ```

1. Im eingebetteten Code:

   * Change value of the `options.path` variable with the path of the publish URL of the adaptive form. Wenn der AEM-Server in einem Kontextpfad ausgeführt wird, stellen Sie sicher, dass die URL diesen Pfad enthält. Beispielsweise befinden sich der Code und das adaptive Formular im Beispiel oben auf demselben AEM Forms-Server, daher wird im Kontextpfad dieses Beispiels der Pfad /content/forms/af/locbasic.html für das adaptive Formular verwendet.
   * Ersetzen Sie `options.dataRef` durch Attribute, die mit der URL übertragen werden sollen. You can use the dataref variable to [prefill an adaptive form](/help/forms/using/prepopulate-adaptive-form-fields.md).
   * Ersetzen Sie `options.themePath` durch den Pfad zu einem anderen Design als dem im adaptiven Formular konfigurierten Design. Alternativ können Sie den Designpfad mit dem Anforderungsattribut angeben.
   * `CSS_Selector` ist der CSS-Selektor des Formularcontainers, in den das adaptive Formular eingebettet ist. Beispiel: Die CSS-Klasse &quot;.customafsection&quot;ist im obigen Beispiel der CSS-Selektor.

Das adaptive Formular wird in die Webseite eingebettet. Beobachten Sie Folgendes im eingebetteten adaptiven Formular:

* Die Kopf- und Fußzeile im adaptiven Originalformular werden nicht vom eingebetteten Formular übernommen.
* Entwürfe und übermittelte Formulare sind auf der entsprechenden Registerkarte im Forms Portal verfügbar.
* Die im adaptiven Originalformular konfigurierte Aktion wird im eingebetteten Formular beibehalten.
* Regeln für adaptive Formulare bleiben erhalten und sind im eingebetteten Formular voll funktionsfähig.
* Die im Originalformular konfigurierten Erlebnis-Targeting und A/B-Tests funktionieren im eingebetteten adaptiven Formular nicht.
* Wenn Adobe Analytics im ursprünglichen Formular konfiguriert ist, werden die Analysedaten im Adobe Analytics-Server erfasst. Sie sind jedoch nicht im Formularanalysebericht verfügbar.

## SSL Reverse Proxy  {#reveseproxy}

Die externe Webseite, in die das adaptive Formular eingebettet wird, sendet Anforderungen an den AEM-Server, der sich in der Regel hinter der Firewall in einem privaten Netzwerk befindet. Um sicherzustellen, dass die Anforderungen sicher auf den AEM-Server geleitet werden, wird empfohlen, einen Reverse-Proxy-Server einzurichten.

Schauen wir uns ein Beispiel an, wie Sie einen Apache 2.4-Reverse-Proxy-Server ohne Dispatcher einrichten können. In this example, you will host the AEM server with `/forms` context path and map `/forms` for the reverse proxy. It ensures that any request for `/forms` on Apache server are directed to the AEM instance. This topology helps reduces the number of rules at the dispatcher layer as all request prefixed with `/forms` route to the AEM server.

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

   Replace `[AEM_Instance`] with the AEM server publish URL in the rules.

Wenn Sie den AEM-Server nicht auf einem Kontextpfad bereitstellen, lauten die Proxyregeln auf der Apache-Ebene wie folgt:

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
>Wenn Sie eine andere Topologie einrichten, stellen Sie sicher, dass Sie die URLs für Senden, Vorausfüllen und andere Funktionen auf der Dispatcher-Ebene in die Positivliste eintragen.

## Best Practices {#best-practices}

Berücksichtigen Sie beim Einbetten eines adaptiven Formulars in eine Webseite die folgenden Richtlinien:

* Stellen Sie sicher, dass die Formatierungsregeln in den Webseite-CSS nicht mit den Formularobjekt-CSS in Konflikt stehen. Um dies zu vermeiden, können Sie die Webseite-CSS im Design für das adaptive Formular mithilfe der AEM-Clientbibliothek wiederverwenden. Weitere Informationen zur Verwendung der Client-Bibliothek in den Designs für adaptive Formulare finden Sie unter [Designs in AEM Forms](/help/forms/using/themes.md).
* Verwenden Sie für den Formularcontainer auf der Webseite die gesamte Fensterbreite. So wird sichergestellt, dass die für mobile Geräte konfigurierten CSS-Regeln ohne Änderungen funktionieren. Wenn der Formularcontainer nicht die gesamte Fensterbreite einnimmt, müssen Sie benutzerdefinierte CSS schreiben, damit sich das Formular an verschiedene mobile Geräte anpasst.
* Use  [getData](https://helpx.adobe.com/de/experience-manager/6-4/forms/javascript-api/GuideBridge.html) API to get the XML or JSON representation of form data in client.
* Use [unloadAdaptiveForm](https://helpx.adobe.com/de/experience-manager/6-4/forms/javascript-api/GuideBridge.html) API to unload the adaptive form from HTML DOM.
* Richten Sie die Kopfzeile &quot;access-control-Herkunft&quot;ein, wenn Sie eine Antwort vom AEM-Server senden.

## Bereitstellung adaptiver Formulare auf einer domänenübergreifenden Site durch AEM Forms  {#cross-domain-sites}

1. On AEM author instance, go to AEM Web Console Configuration Manager at `http://[server]:[port]/system/console/configMgr`.
1. Locate and open the **Apache Sling Referrer** Filter configuration.
1. Geben Sie im Feld **Zulässige Hosts** die Domäne an, in der sich die Webseite befindet. Dadurch kann der Host POST-Anforderungen an den AEM-Server senden. Sie können auch einen regulären Ausdruck verwenden, um eine Reihe von externen Anwendungsdomänen anzugeben.