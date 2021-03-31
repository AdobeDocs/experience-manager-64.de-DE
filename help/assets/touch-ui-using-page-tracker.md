---
title: Verwenden von Seitenverfolgung und Einbettungs-Code in Web-Seiten
description: Erfahren Sie mehr über das Miteinbeziehen der Seitenverfolgung und das Einbetten von JavaScript-Codes in Ihren Website-Code, damit Adobe Analytics Nutzungsdaten zu Assets erfassen kann.
contentOwner: AG
feature: 'Asset-Berichte '
role: Architekt, Administrator
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 98%

---


# Verwenden von Seitenverfolgung und Einbettungs-Code in Web-Seiten {#using-page-tracker-and-embed-code-in-web-pages}

Die Seitenverfolgung ist Teil des JavaScript-Codes, den Sie in Code von Websites von Drittanbietern einbeziehen, um es Adobe Analytics zu ermöglichen, die Erfassung von Nutzungsdaten rund um Adobe Experience Manager (AEM) Assets auf diesen Websites zu aktivieren.

Um Ereignisse wie Klicks usw. zu erfassen, die Asset-spezifisch sind, beziehen Sie auch den Einbettungscode in den Code der Websites von Drittanbietern ein.

Der folgende Beispiel-Code veranschaulicht, wie eine Web-Seite aussieht, die sowohl den Seitenverfolgungs-Code als auch Einbettungs-Code enthält:

```
<!DOCTYPE html>
<html>
    <head>
            <script type="text/javascript" src="http://localhost:4502/xxxx/etc.clientlibs/dam/clientlibs/sitecatalyst/appmeasurement.js"></script>
            <script type="text/javascript" src="http://localhost:4502/xxxx/etc.clientlibs/dam/clientlibs/foundation/assetinsights/pagetracker.js"></script>
            <script type="text/javascript">
                                assetAnalytics.attrTrackable = 'trackable';
                assetAnalytics.defaultTrackable = false;
                assetAnalytics.attrAssetID = 'aem-asset-id';
                assetAnalytics.assetImpressionPollInterval = 200; // interval in milliseconds
                assetAnalytics.charsLimitForGET = 2000; // bytes
                assetAnalytics.dispatcher.init("assetstesting","xxxx","xxx","list1","eVar3","event8","event7");
            </script>

    </head>

    <body>

                                <img
            src="https://10.41.52.147:4502/xxxx/content/dam/test/abc.jpg"
            data-aem-asset-id="aaid:a386f2cd78234becb66bd11575f9452d"
            data-trackable=true
            onload=assetAnalytics.core.assetLoaded(this)>

        <a
            href="https://www.adobe.com"

            onclick="assetAnalytics.core.assetClicked(this);return false">
                <img
                    src="http://localhost/xxxx/content/dam/test/xyz.jpg"
                    data-aem-asset-id="aaid:7fa01fce0ebe40268cd6dcf07e2d9cb1"
                    data-trackable=true
                    onload=assetAnalytics.core.assetLoaded(this)>
        </a>

    </body>
</html>
```

## Hinzufügen von Seitenverfolgungs-Code {#adding-page-tracker-code}

Sie fügen den Seitenverfolgungs-Code in der Kopfzeile des Website-Codes hinzu. Das folgende Codebeispiel zeigt den Seitenverfolgungscode, der in einer Beispielwebseite enthalten ist:

```xml
 <head>
            <script type="text/javascript" src="http://localhost:4502/xxxx/etc.clientlibs/dam/clientlibs/sitecatalyst/appmeasurement.js"></script>
            <script type="text/javascript" src="http://localhost:4502/xxxx/etc.clientlibs/dam/clientlibs/foundation/assetinsights/pagetracker.js"></script>
            <script type="text/javascript">
                                assetAnalytics.attrTrackable = 'trackable';
                assetAnalytics.defaultTrackable = false;
                assetAnalytics.attrAssetID = 'aem-asset-id';
                assetAnalytics.assetImpressionPollInterval = 200; // interval in millis
                assetAnalytics.charsLimitForGET = 2000; // bytes
                assetAnalytics.dispatcher.init("assetstesting","abc.net","bee","list1","eVar3","event8","event7");
            </script>
 </head>
```

## Hinzufügen von Einbettungs-Code   {#adding-embed-code}

Sie können Einbettungs-Code im Hauptteil des Website-Codes hinzufügen. Das folgende Code-Beispiel zeigt den Einbettungs-Code, der in einer Web-Seite enthalten ist:

```xml
<body>

      <img
            src="http://localhost:4502/xxxx/content/dam/test/xyz.jpg"
            data-aem-asset-id="aaid:a386f2cd78234becb66bd11575f9452d"
            data-trackable=true
            onload=assetAnalytics.core.assetLoaded(this)>

        <a
            href="https://www.adobe.com"

            onclick="assetAnalytics.core.assetClicked(this);return false">
           <img
                    src="http://localhost:4502/xxxx/content/dam/test/xyz.jpg"
                    data-aem-asset-id="aaid:7fa01fce0ebe40268cd6dcf07e2d9cb1"
                    data-trackable=true
                    onload=assetAnalytics.core.assetLoaded(this)>
        </a>

    </body>
```
