---
title: Verwenden von Seitenverfolgung und Einbettungs-Code in Web-Seiten
description: Erfahren Sie mehr über das Einbinden der Seitenverfolgung und das Einbetten von JavaScript-Codes in Ihren Website-Code, damit Adobe Analytics Nutzungsdaten zu Assets erfassen kann.
contentOwner: AG
feature: Asset Reports
role: Architect,Admin
exl-id: b0154c9c-a671-43fb-8733-274a35307a34
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 72%

---

# Verwenden von Seitenverfolgung und Einbettungs-Code in Web-Seiten {#using-page-tracker-and-embed-code-in-web-pages}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Seitenverfolgung ist ein JavaScript-Code, den Sie in den Code von Drittanbieter-Websites einfügen, damit Adobe Analytics Nutzungsdaten zu Adobe Experience Manager-Assets auf diesen Websites erfassen kann.

Um Ereignisse wie Klicks usw. zu erfassen, die Asset-spezifisch sind, beziehen Sie auch den Einbettungs-Code in den Code der Websites von Drittanbietern ein.

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

Sie fügen den Seitenverfolgungs-Code in der Kopfzeile des Website-Codes hinzu. Das folgende Code-Beispiel zeigt den Seitenverfolgungs-Code, der in einer Beispiel-Web-Seite enthalten ist:

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
