---
title: Erweitern von ContextHub
seo-title: Extending ContextHub
description: Definieren Sie neue Typen von ContextHub-Stores und -Modulen, wenn die bereitgestellten Typen nicht Ihren Lösungsanforderungen entsprechen
seo-description: Define new types of ContextHub stores and modules when the ones provided do not meet your solution requirements
uuid: 1d80c01d-ec5d-4e76-849d-bec0e1c3941a
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 13a908ae-6965-4438-96d0-93516b500884
exl-id: 15b17bed-3422-43cf-b1af-91d9e0c5dfcb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '686'
ht-degree: 80%

---

# Erweitern von ContextHub{#extending-contexthub}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Definieren Sie neue Typen von ContextHub-Stores und -Modulen, wenn die bereitgestellten Typen nicht Ihren Lösungsanforderungen entsprechen.

## Erstellen benutzerdefinierter Store-Kandidaten {#creating-custom-store-candidates}

ContextHub-Stores werden aus registrierten Store-Kandidaten erstellt. Um einen benutzerdefinierten Store zu erstellen, müssen Sie einen Store-Kandidaten erstellen und registrieren.

Die JavaScript-Datei, die den Code enthält, der den Store-Kandidaten erstellt und registriert, muss in einer [Client-Bibliotheksordner](/help/sites-developing/clientlibs.md#creating-client-library-folders). Die Ordnerkategorie muss dem folgenden Muster entsprechen:

```xml
contexthub.store.[storeType]
```

Beim `[storeType]`-Teil der Kategorie handelt es sich um den `storeType`, mit dem der Store-Kandidat registriert wird. (Siehe [Registrieren von ContextHub-Store-Kandidaten](/help/sites-developing/ch-extend.md#registering-a-contexthub-store-candidate).) Beispielsweise muss für den Store-Typ `contexthub.mystore` die Kategorie des Client-Bibliotheksordners `contexthub.store.contexthub.mystore` lauten.

### Erstellen von ContextHub-Store-Kandidaten {#creating-a-contexthub-store-candidate}

Verwenden Sie zum Erstellen eines Store-Kandidaten die Funktion [`ContextHub.Utils.inheritance.inherit`](/help/sites-developing/contexthub-api.md#inherit-child-parent), um einen der grundlegenden Stores zu erweitern:

* [`ContextHub.Store.PersistedStore`](/help/sites-developing/contexthub-api.md#contexthub-store-persistedstore)
* [`ContextHub.Store.SessionStore`](/help/sites-developing/contexthub-api.md#contexthub-store-sessionstore)
* [`ContextHub.Store.JSONPStore`](/help/sites-developing/contexthub-api.md#contexthub-store-jsonpstore)
* [`ContextHub.Store.PersistedJSONPStore`](/help/sites-developing/contexthub-api.md#contexthub-store-persistedjsonpstore)

Beachten Sie, dass jeder grundlegende Store den Store [`ContextHub.Store.Core`](/help/sites-developing/contexthub-api.md#contexthub-store-core) erweitert.

Im folgenden Beispiel wird erst die einfachste Erweiterung des Store-Kandidaten `ContextHub.Store.PersistedStore` erstellt:

```
myStoreCandidate = function(){};
ContextHub.Utils.inheritance.inherit(myStoreCandidate,ContextHub.Store.PersistedStore);
```

In der Praxis werden mit Ihren benutzerdefinierten Store-Kandidaten wohl zusätzliche Funktionen definiert oder die ursprüngliche Konfiguration des Stores überschrieben. Mehrere [Beispiel-Store-Kandidaten](/help/sites-developing/ch-samplestores.md) werden im Repository unter `/libs/granite/contexthub/components/stores` installiert. Um von diesen Beispielen zu lernen, verwenden Sie CRXDE Lite, um die JavaScript-Dateien zu öffnen.

### Registrieren von ContextHub-Store-Kandidaten {#registering-a-contexthub-store-candidate}

Registrieren Sie einen Store-Kandidaten, um ihn mit dem ContextHub-Framework zu integrieren und Stores zu aktivieren, die auf Grundlage des Kandidaten erstellt werden sollen. Um einen Store-Kandidaten zu registrieren, verwenden Sie die Funktion [`registerStoreCandidate`](/help/sites-developing/contexthub-api.md#registerstorecandidate-store-storetype-priority-applies) der Klasse `ContextHub.Utils.storeCandidates`.

Wenn Sie einen Store-Kandidaten registrieren, geben Sie einen Namen für den Store-Typ an. Beim Erstellen eines Stores auf Grundlage des Kandidaten identifizieren Sie über den Store-Typ den zugrunde liegenden Kandidaten.

Geben Sie beim Registrieren eines Store-Kandidaten dessen Priorität an. Wird ein Store-Kandidat mit demselben Store-Typ wie ein bereits registrierter Store-Kandidat registriert, wird der Kandidat mit der höheren Priorität verwendet. Daher können Sie vorhandene Store-Kandidaten durch neue Implementierungen überschreiben.

```
ContextHub.Utils.storeCandidates.registerStoreCandidate(myStoreCandidate,
                                'contexthub.mystorecandidate', 0);
```

In den meisten Fällen ist nur ein Kandidat erforderlich und die Priorität kann auf `0` gesetzt werden. Wenn Sie Interesse daran haben, können Sie mehr über [erweiterte Registrierungen](/help/sites-developing/contexthub-api.md#registerstorecandidate-store-storetype-priority-applies) erfahren, die es ermöglichen, auf Basis der JavaScript-Bedingung (`applies`) und Kandidatenpriorität eine von mehreren Store-Implementierungen auszuwählen.

## Erstellen von Typen von ContextHub-Benutzeroberflächenmodulen {#creating-contexthub-ui-module-types}

Erstellen Sie benutzerdefinierte Typen eines Benutzeroberflächenmoduls, wenn die [mit ContextHub installierten Typen](/help/sites-developing/ch-samplemodules.md) nicht Ihren Anforderungen entsprechen. Erstellen Sie dazu einen neuen Benutzeroberflächenmodul-Renderer, indem Sie die `ContextHub.UI.BaseModuleRenderer`-Klasse erweitern und sie dann mit `ContextHub.UI` registrieren.

Erstellen Sie zum Erstellen eines Benutzeroberflächenmodul-Renderers ein `Class`-Objekt, das die Logik enthält, die das Benutzeroberflächenmodul rendert. Ihre Klasse muss mindestens die folgenden Aktionen durchführen:

* Erweitern der `ContextHub.UI.BaseModuleRenderer`-Klasse. Bei dieser Klasse handelt es sich um die Basisimplementierung für alle Benutzeroberflächenmodul-Renderer. Das `Class`-Objekt definiert eine Eigenschaft namens `extend`, mit der Sie diese Klasse als diejenige benennen, die erweitert wird.

* Bereitstellen einer Standardkonfiguration. Erstellen Sie eine Eigenschaft `defaultConfig`. Diese Eigenschaft ist ein Objekt, das die Eigenschaften enthält, die für das Benutzeroberflächenmodul [`contexthub.base`](/help/sites-developing/ch-samplemodules.md#contexthub-base-ui-module-type) definiert sind, sowie alle anderen Eigenschaften, die Sie benötigen.

Die Quelle für `ContextHub.UI.BaseModuleRenderer` befindet sich unter /libs/granite/contexthub/code/ui/container/js/ContextHub.UI.BaseModuleRenderer.js. Verwenden Sie zum Registrieren des Renderers die Methode [`registerRenderer`](/help/sites-developing/contexthub-api.md#registerrenderer-moduletype-renderer-dontrender) der `ContextHub.UI`-Klasse. Sie müssen einen Namen für den Modultyp angeben. Wenn Administratoren ein Benutzeroberflächenmodul auf Grundlage dieses Renderers erstellen, geben sie diesen Namen an.

Erstellen und registrieren Sie die Renderer-Klasse in einer selbstausführenden anonymen Funktion. Das folgende Beispiel basiert auf dem Quellcode für das Benutzeroberflächenmodul contexthub.browserinfo. Dieses Benutzeroberflächenmodul ist eine einfache Erweiterung der `ContextHub.UI.BaseModuleRenderer`-Klasse.

```xml
;(function() {

    var SurferinfoRenderer = new Class({
        extend: ContextHub.UI.BaseModuleRenderer,

        defaultConfig: {
            icon: 'coral-Icon--globe',
            title: 'Browser/OS Information',

            storeMapping: {
                surferinfo: 'surferinfo'
            },

            template:
                '<p>{{surferinfo.browser.family}} {{surferinfo.browser.version}}</p>' +
                '<p>{{surferinfo.os.name}} {{surferinfo.os.version}}</p>'
        }
    });

    ContextHub.UI.registerRenderer('contexthub.browserinfo', new SurferinfoRenderer());

}());
```

Die JavaScript-Datei mit dem Code zum Erstellen und Registrieren des Renderers muss in einem [Client-Bibliotheksordner](/help/sites-developing/clientlibs.md#creating-client-library-folders) enthalten sein. Die Ordnerkategorie muss dem folgenden Muster entsprechen:

```xml
contexthub.module.[moduleType]
```

Beim `[moduleType]`-Teil der Kategorie handelt es sich um den `moduleType`, mit dem der Renderer registriert wird. Beispielsweise muss für den `moduleType` von `contexthub.browserinfo` die Kategorie des Client-Bibliotheksordners `contexthub.module.contexthub.browserinfo` lauten.
