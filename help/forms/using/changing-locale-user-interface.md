---
title: Ändern des Gebietsschemas der Benutzeroberfläche von AEM Forms Workspace
seo-title: Changing the locale of AEM Forms workspace user interface
description: So ändern Sie den AEM Forms-Arbeitsbereich, um Text, ausgeblendete Kategorien, Warteschlangen und Prozesse sowie die Datumsauswahl auf der Benutzeroberfläche zu lokalisieren.
seo-description: How to modify the AEM Forms workspace to localize text, collapsed categories, queues, and processes, and the date picker on the interface.
uuid: f8e7d399-98d9-4655-b51f-0346a5713f06
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: e4ca8188-fb9a-44bf-8437-a98abaa7521a
exl-id: 9968f399-454b-4cb2-b6af-2c16428ca7b4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '593'
ht-degree: 59%

---

# Ändern des Gebietsschemas der Benutzeroberfläche von AEM Forms Workspace {#changing-the-locale-of-aem-forms-workspace-user-interface}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

AEM Forms Workspace unterstützt standardmäßig die Sprachen Englisch, Französisch, Deutsch und Japanisch. Darüber hinaus besteht die Möglichkeit, die AEM Forms Workspace-Benutzeroberfläche in einer beliebigen anderen Sprache zu lokalisieren.

So lokalisieren Sie die AEM Forms Workspace-Benutzeroberfläche in einer Sprache Ihrer Wahl:

* Lokalisieren Sie den Text des AEM Forms-Arbeitsbereichs.
* Lokalisieren von ausgeblendeten Kategorien, Warteschlangen und Prozessen
* Datumsauswahl lokalisieren

Bevor Sie die obengenannten Schritte ausführen, achten Sie darauf, die hier aufgeführten Schritte durchzuführen: [Generische Schritte zur Anpassung von AEM Forms Workspace](/help/forms/using/generic-steps-html-workspace-customization.md).

>[!NOTE]
>
>Informationen zum Ändern der Sprache des Anmeldebildschirms von AEM Forms Workspace finden Sie unter [Neuen Anmeldebildschirm erstellen](/help/forms/using/creating-new-login-screen.md).

## Lokalisieren von Text {#localizing-text}

Führen Sie die folgenden Schritte aus, um Unterstützung für eine Sprache *Neu* und den Browser-Gebietsschema-Code *nw* hinzuzufügen.

1. Melden Sie sich bei CRXDE Lite an.

   Die Standard-URL von CRXDE Lite lautet `https://[server]:[port]/lc/crx/de/index.jsp`.

1. Navigieren Sie zum Speicherort `apps/ws/locales` und erstellen Sie einen neuen Ordner `nw.`
1. Kopieren Sie die Datei `translation.json` vom Speicherort `/apps/ws/locales/en-US` zum Speicherort `/apps/ws/locales/nw`.
1. Navigieren Sie zu `/apps/ws/locales/nw` und öffnen Sie `translation.json` zur Bearbeitung. Nehmen Sie gebietsschemaspezifische Änderungen an der Datei translation.json vor.

   Die folgenden Beispiele enthalten die Datei translation.json für die englischen und französischen Gebietsschemata von AEM Forms Workspace.

   ![translation_json_in_en](assets/translation_json_in_en.png) ![translation_json_in_fr](assets/translation_json_in_fr.png)

## Lokalisieren von ausgeblendeten Kategorien, Warteschlangen und Prozessen {#localizing-collapsed-categories-queues-and-processes}

AEM Forms Workspace verwendet Bilder, um Kopfzeilen von Kategorien, Warteschlangen und Prozessen anzuzeigen. Sie benötigen das Entwicklungspaket um diese Kopfzeilen zu lokalisieren. Ausführliche Informationen zum Erstellen des Entwicklungspakets finden Sie unter [AEM Forms Workspace-Code erstellen.](introduction-customizing-html-workspace.md#building-html-workspace-code)

In den folgenden Schritten wird davon ausgegangen, dass es sich bei den neuen lokalisierten Bilddateien um *Categories_nw.png*, *Queue_nw.png* und *Processes_nw.png* handelt. Die empfohlene Breite der Bilder ist 19 px.

>[!NOTE]
>
>Den Browser-Sprachschema-Code Ihres Browsers finden. Öffnen Sie `https://[server]:[port]/lc/libs/ws/Locale.html`.

![collapsing_panels_image](assets/collapsing_panels_image.png)

Führen Sie die folgenden Schritte aus, um die Bilder zu lokalisieren:

1. Platzieren Sie die Bilddateien mithilfe eines WebDAV-Clients im */apps/ws/images* Ordner.
1. Navigieren Sie zu */apps/ws/css*. Öffnen Sie *newStyle.css* zur Bearbeitung und fügen Sie die folgenden Einträge hinzu:

   ```
   #categoryListBar .content.nw {
        background: #3e3e3e url(../images/Categories_nw.png) no-repeat 10px 10px;
    }
   
   #filterListBar .content.nw {
       background: #3e3e3e url(../images/Queues_nw.png) no-repeat 10px 10px;
   }
   
   #processNameListBar .content.nw {
       background: #3e3e3e url(../images/Processes_nw.png) no-repeat 10px 10px;
   }
   ```

1. Führen Sie alle semantischen Änderungen durch, die im Artikel [Anpassung von Workspace](/help/forms/using/introduction-customizing-html-workspace.md) aufgeführt sind.
1. Navigieren Sie zum *js/runtime/utility* und öffnen Sie die Datei &quot;usersession.js*&quot;zur Bearbeitung.
1. Suchen Sie den Code, der im ursprünglichen Codeblock aufgeführt ist und fügen Sie die folgende Bedingung hinzu: *lang !== &#39;nw&#39;* to the if statement:

   ```
   // Orignal code
   setLocale = function () {
           var lang = $.trim(i18n.lng());
           if (lang === null || lang === '' || (lang !== 'fr-FR' && lang !== 'de-DE' && lang !== 'ja-JP')) {
               window.lcWorkspace.locale = 'en-US';
           } else {
               window.lcWorkspace.locale = lang;
           }
       }
   ```

   ```
   //new code
    setLocale = function () {
           var lang = $.trim(i18n.lng());
           if (lang === null || lang === '' || (lang !== 'fr-FR' && lang !== 'de-DE' && lang !== 'ja-JP' && lang !== 'nw')) {
               window.lcWorkspace.locale = 'en-US';
           } else {
               window.lcWorkspace.locale = lang;
           }
       }
   ```

## Datumsauswahl lokalisieren {#localizing-date-picker}

Sie benötigen ein Entwicklungspaket, um die *datepicker *API zu lokalisieren. Ausführliche Informationen zum Erstellen des Entwicklungspakets finden Sie unter [AEM Forms Workspace-Code erstellen](introduction-customizing-html-workspace.md#building-html-workspace-code).

1. Laden Sie die [jQuery UI Package](https://jqueryui.com/download/all/), navigieren Sie zu *&lt;extracted jquery=&quot;&quot; ui=&quot;&quot; package=&quot;&quot;>*\jquery-ui-1.10.2.zip\jquery-ui-1.10.2\ui\i18n.
1. Kopieren Sie die Datei jquery.ui.datepicker-nw.js für Gebietsschema-Code jetzt in apps/ws/js/libs/jqueryui und nehmen Sie gebietsschemaspezifische Änderungen an der Datei vor.
1. Navigieren Sie zu `apps/ws/js` und öffnen Sie die Datei`jquery.ui.datepicker-nw.js` zur Bearbeitung.
1. Erstellen Sie in der Datei main.js einen Alias für `jquery.ui.datepicker-nw.js.`. Der Code zum Erstellen eines Alias für die Datei `jquery.ui.datepicker-nw.js` ist:

   ```
   jqueryuidatepickernw : pathprefix + 'libs/jqueryui/jquery.ui.datepicker-nw'
   ```

1. Verwenden Sie den Alias `jqueryuidatepickernw`, um die Datei `jquery.ui.datepicker-nw.js` in allen Dateien einzubinden, die die Datumsauswahl verwenden. Die Datumsauswahl wird in den folgenden Dateien verwendet:

   * `js/runtime/views/outofoffice.js`
   * `js/runtime/views/searchtemplatedetails.js`

   Der folgende Beispielcode zeigt, wie der Eintrag von jquery.ui.datepicker-nw.js hinzugefügt wird:

   ```
   //Original Code
   define([
       'jquery',
       'underscore',
       'backbone',
       'jqueryui',
       'jqueryuidatepickerja',
       'jqueryuidatepickerde',
       'jqueryuidatepickerfr',
       'slimscroll',
       'usersearchview',
       'logmanagerutil',
       'loggerutil'
   ], function ($, _, Backbone, jQueryUI, jQueryUIDatePickerJA, jQueryUIDatePickerDE, jQueryUIDatePickerFR, slimScroll, UserSearch, LogManager, Logger) {
   ```

   ```
   // Code with Date Picker alias for new language
   define([
       'jquery',
       'underscore',
       'backbone',
       'jqueryui',
       'jqueryuidatepickerja',
       'jqueryuidatepickerde',
       'jqueryuidatepickerfr',
       'jqueryuidatepickernw', // Date Picker alias
       'slimscroll',
       'usersearchview',
       'logmanagerutil',
       'loggerutil'
   ], function ($, _, Backbone, jQueryUI, jQueryUIDatePickerJA, jQueryUIDatePickerDE, jQueryUIDatePickerFR, jQueryUIDatePickerNW, slimScroll, UserSearch, LogManager, Logger) {
   ```

1. Ändern Sie in allen Dateien, die die Datepicker-API verwenden, die standardmäßigen API-Einstellungen für die Datumsauswahl. Die Datumsauswahl-API wird in den folgenden Dateien verwendet:

   * apps\ws\js\runtime\views\searchtemplatedetails.js
   * apps\ws\js\runtime\views\outofoffice.js

   Ändern Sie den folgenden Code, um das neue Gebietsschema hinzuzufügen:

   ```
   if (locale === 'ja-JP') {
      $.datepicker.setDefaults($.datepicker.regional.ja);
   } else if (locale === 'de-DE') {
      $.datepicker.setDefaults($.datepicker.regional.de);
   } else if (locale === 'fr-FR') {
      $.datepicker.setDefaults($.datepicker.regional.fr);
   } else {
      $.datepicker.setDefaults($.datepicker.regional['']);
   }
   ```

in

```
if (locale === 'ja-JP') {
    $.datepicker.setDefaults($.datepicker.regional.ja);
} else if (locale === 'de-DE') {
    $.datepicker.setDefaults($.datepicker.regional.de);
} else if (locale === 'fr-FR') {
    $.datepicker.setDefaults($.datepicker.regional.fr);
} else if (locale === 'nw') {
    $.datepicker.setDefaults($.datepicker.regional.nw);
} else {
    $.datepicker.setDefaults($.datepicker.regional['']);
}
```
