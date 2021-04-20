---
title: Unterstützung neuer Gebietsschemata zum Lokalisieren von adaptiven Formularen
seo-title: Unterstützung neuer Gebietsschemata zum Lokalisieren von adaptiven Formularen
description: Mit AEM Forms können Sie neue Gebietsschemata zum Lokalisieren von adaptiven Formularen hinzufügen. Die unterstützten Gebietsschemata sind standardmäßig Englisch, Französisch, Deutsch und Japanisch.
seo-description: Mit AEM Forms können Sie neue Gebietsschemata zum Lokalisieren von adaptiven Formularen hinzufügen. Die unterstützten Gebietsschemata sind standardmäßig Englisch, Französisch, Deutsch und Japanisch.
uuid: d4cee51b-c555-4544-9ae9-4aa8d38b2b17
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: e78f539a-109c-444c-8e52-be2260c3509f
feature: Adaptive Forms
role: Administrator
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 66%

---


# Unterstützung neuer Gebietsschemata zum Lokalisieren von adaptiven Formularen {#supporting-new-locales-for-adaptive-forms-localization}

## Informationen zu Gebietsschemawörterbüchern {#about-locale-dictionaries}

Die Lokalisierung von adaptiven Formularen beruht auf zwei Arten von Gebietsschemawörterbüchern:

**Formularspezifisches** WörterbuchEnthält Zeichenfolgen, die in adaptiven Formularen verwendet werden. Beispielsweise Beschriftungen, Feldnamen, Fehlermeldungen, Hilfebeschreibungen usw. Es wird als Satz von XLIFF-Dateien für jedes Gebietsschema verwaltet und Sie können darauf unter https://`<host>`:`<port>`/libs/cq/i18n/translator.html zugreifen.

**Globale** WörterbücherEs gibt zwei globale Wörterbücher, die als JSON-Objekte verwaltet werden, in AEM Client-Bibliothek. Diese Wörterbücher enthalten Standardfehlermeldungen, Monatsnamen, Währungssymbole, Datums- und Uhrzeitmuster usw. Sie können diese Wörterbücher in CRXDe Lite finden Sie unter /libs/fd/xfaforms/clientlibs/I18N. Diese Speicherorte enthalten für jedes Gebietsschema separate Ordner. Da globale Wörterbücher in der Regel nicht oft aktualisiert werden, können Browser separate JavaScript-Dateien für jedes Gebietsschema im Cache zwischenspeichern und die Beanspruchung der Netzwerkbandbreite reduzieren, wenn auf demselben Server auf verschiedene adaptive Formulare zugegriffen wird.

### Funktionsweise der Lokalisierung von adaptiven Formularen {#how-localization-of-adaptive-form-works}

Wenn ein adaptives Formular wiedergegeben wird, identifiziert es das angeforderte Gebietsschema, indem es folgende Parameter in der angegebenen Reihenfolge durchsucht:

* Abfrageparameter `afAcceptLang`

   Um das Browser-Gebietsschema der Benutzer zu überschreiben, können Sie den Anforderungsparameter `afAcceptLang` übergeben, um das Gebietsschema zu erzwingen. Beispielsweise erzwingt die folgende URL die Wiedergabe des Formulars im japanischen Gebietsschema:

   `https://[*server*]:[*port*]/<*contextPath*>/<*formFolder*>/<*formName*>.html?wcmmode=disabled&afAcceptLang=ja`

* Das für den Benutzer festgelegte Browser-Gebietsschema, das in der Abfrage mit dem `Accept-Language`-Header angegeben ist.

* Die in AEM angegebene Spracheinstellung des Benutzers.

Sobald das Gebietsschema definiert ist, wählt das adaptive Formular das formularspezifische Wörterbuch aus. Wenn das formularspezifische Wörterbuch für das angeforderte Gebietsschema nicht gefunden wird, wird das englische Wörterbuch (en) verwendet.

Wenn keine Client-Bibliothek für das angeforderte Gebietsschema vorhanden ist, wird nach einer Client-Bibliothek für den im Gebietsschema vorhandenen Sprachcode gesucht. Beispiel: Wenn das angeforderte Gebietsschema `en_ZA` (Südafrikanisches Englisch) lautet und die Client-Bibliothek für `en_ZA` nicht vorhanden ist, verwendet das adaptive Formular die Client-Bibliothek für `en` (Englisch), sofern vorhanden. Wenn jedoch keine der Sprachen vorhanden ist, verwendet das adaptive Formular das Wörterbuch für das Gebietsschema `en`.

## Lokalisierungsunterstützung für nicht unterstützte Gebietsschemata hinzufügen {#add-localization-support-for-non-supported-locales}

AEM Forms unterstützt derzeit die lokale Anpassung von Inhalten für adaptive Formulare in den Gebietsschemata Englisch (en), Spanisch (es), Französisch (fr), Italienisch (es), Deutsch (de), Japanisch (ja), Portugiesisch-Brasilianisch (pt-BR, Chinesisch- (zh-CN), Chinesisch-Taiwan (zh-TW) und Koreanisch (ko-KR).

So fügen Sie Unterstützung für ein neues Gebietsschema während der Laufzeit adaptiver Formulare hinzu:

1. [Gebietsschema zum GuideLocalizationService-Dienst hinzufügen](/help/forms/using/supporting-new-language-localization.md#p-add-a-locale-to-the-guide-localization-service-br-p)

1. [XFA-Clientbibliothek für ein Gebietsschema hinzufügen](/help/forms/using/supporting-new-language-localization.md#p-add-xfa-client-library-for-a-locale-br-p)

1. [Clientbibliothek für adaptive Formulare für ein Gebietsschema hinzufügen](/help/forms/using/supporting-new-language-localization.md#p-add-adaptive-form-client-library-for-a-locale-br-p)
1. [Gebietsschema-Unterstützung für das Wörterbuch hinzufügen](/help/forms/using/supporting-new-language-localization.md#p-add-locale-support-for-the-dictionary-br-p)
1. [Starten Sie den Server neu](/help/forms/using/supporting-new-language-localization.md#p-restart-the-server-p)

### hinzufügen eines Gebietsschemas für den Guide Lokale Anpassung-Dienst {#add-a-locale-to-the-guide-localization-service-br}

1. Rufen Sie `https://[server]:[port]/system/console/configMgr` auf.
1. Klicken Sie, um die Komponente **Handbuch-Lokalisierungsdienst** zu bearbeiten.
1. Fügen Sie der Liste der unterstützen Gebietsschemata das gewünschte Gebietsschema hinzu.

![GuideLocalizationSevice](assets/configservice.png)

### XFA-Clientbibliothek für ein Gebietsschema hinzufügen {#add-xfa-client-library-for-a-locale-br}

Erstellen Sie einen Knoten des Typs `cq:ClientLibraryFolder` unter `etc/<folderHierarchy>` mit der Kategorie `xfaforms.I18N.<locale>` und fügen Sie der Client-Bibliothek die folgenden Dateien hinzu:

* **I18N.** jsdefinition  `xfalib.locale.Strings` für die  `<locale>` wie unter  `/etc/clientlibs/fd/xfaforms/I18N/ja/I18N` definiert.

* **js.txt**, die Folgendes enthält:

```
/libs/fd/xfaforms/clientlibs/I18N/Namespace.js
I18N.js
/etc/clientlibs/fd/xfaforms/I18N/LogMessages.js
```

### Clientbibliothek für adaptive Formulare für ein Gebietsschema hinzufügen {#add-adaptive-form-client-library-for-a-locale-br}

Erstellen Sie einen Knoten des Typs `cq:ClientLibraryFolder` unter `etc/<folderHierarchy>` mit der Kategorie `guides.I18N.<locale>` und den Abhängigkeiten `xfaforms.3rdparty`, `xfaforms.I18N.<locale>` und `guide.common`. &quot;

Fügen Sie der Clientbibliothek folgende Dateien hinzu:

* **i18n.** jsdefinition  `guidelib.i18n`, mit Mustern von &quot;calendarSymbols&quot;,  `datePatterns`,  `timePatterns`,  `dateTimeSymbols`,  `numberPatterns`,  `numberSymbols`,  `currencySymbols`für die XFA-Spezifikationen, die in der Spezifikation für denLocale-Satz beschrieben sind,  `typefaces`   `<locale>`   [ ](https://helpx.adobe.com/content/dam/de/Adobe/specs/xfa_spec_3_3.pdf)wie in der Beschreibung unter Spezifizierung für Gebietsschemasatz beschrieben. Sie können auch sehen, wie es für andere unterstützte Gebietsschemata in `/etc/clientlibs/fd/af/I18N/fr/javascript/i18n.js` definiert wird.

* **LogMessages.** jsdefinition  `guidelib.i18n.strings` und  `guidelib.i18n.LogMessages` für die  `<locale>` wie in  `/etc/clientlibs/fd/af/I18N/fr/javascript/LogMessages.js` definiert.

* **js.txt**, die Folgendes enthält:

```
i18n.js
LogMessages.js
```

### Gebietsschema-Unterstützung für das Wörterbuch hinzufügen {#add-locale-support-for-the-dictionary-br}

Führen Sie diesen Schritt nur dann aus, wenn das `<locale>`, das Sie hinzufügen, nicht unter `en`, `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja`, `ko-kr` steht.

1. Erstellen Sie einen `nt:unstructured`-Knoten `languages` unter `etc`, falls noch nicht vorhanden.

1. Fügen Sie dem Knoten eine Zeichenfolgeneigenschaft mit mehreren Eigenschaften, `languages`, hinzu, falls nicht bereits vorhanden.
1. hinzufügen die Standardgebietsschemawerte `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja`, `ko-kr`, falls noch nicht vorhanden.`<locale>`

1. hinzufügen Sie `<locale>` auf die Werte der `languages`-Eigenschaft von `/etc/languages`.

Das `<locale>` wird bei `https://[server]:[port]/libs/cq/i18n/translator.html` angezeigt.

### Starten Sie den Server neu {#restart-the-server}

Starten Sie den AEM-Server neu, damit das hinzugefügte Gebietsschema in Kraft tritt.

## Beispielbibliotheken zum Hinzufügen der Unterstützung für Spanisch {#sample-libraries-for-adding-support-for-spanish}

Client-Beispielbibliotheken zum Hinzufügen der Unterstützung für Spanisch

[Datei laden](assets/sample.zip)
