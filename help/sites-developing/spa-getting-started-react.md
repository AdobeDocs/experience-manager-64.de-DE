---
title: Erste Schritte mit SPAs in AEM – React
seo-title: Getting Started with SPAs in AEM - React
description: Dieser Artikel beschreibt eine Beispiel-SPA, erläutert, wie sie zusammengestellt wird, und ermöglicht es Ihnen, unter Verwendung des React-Frameworks schnell mit Ihrer eigenen SPA zu arbeiten.
seo-description: This article presents a sample SPA application, explains how it is put together, and allows you to get up-and-running with your own SPA quickly using the React framework.
uuid: e863fdc7-6c8e-49c5-9513-d3ed88196f07
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: spa
content-type: reference
discoiquuid: 0843ceff-2607-4733-8383-681820e513d1
exl-id: 43376dfd-9cef-46f5-af14-21e379fbb79a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1214'
ht-degree: 92%

---

# Erste Schritte mit SPAs in AEM – React {#getting-started-with-spas-in-aem-react}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Single Page Applications (SPAs) können ansprechende Erlebnisse für Website-Benutzer bieten. Entwickler möchten Sites mit SPA Frameworks erstellen können und Autoren möchten Inhalte in AEM für eine Site, die mit SPA Frameworks erstellt wurde, nahtlos bearbeiten.

Die SPA Authoring-Funktion bietet eine umfassende Lösung zur Unterstützung von SPA in AEM. Dieser Artikel beschreibt eine vereinfachte SPA-Anwendung im React-Framework, erläutert, wie sie zusammengestellt wird, und ermöglicht es Ihnen, rasch mit Ihrer eigenen SPA zu arbeiten.

>[!NOTE]
>
>Dieser Artikel basiert auf dem React-Framework. Das entsprechende Dokument für das Angular-Framework finden Sie unter [Erste Schritte mit SPAs in AEM – Angular](/help/sites-developing/spa-getting-started-angular.md).

>[!NOTE]
>Für die Funktion &quot;Single Page Application (SPA) Editor&quot;ist AEM Service Pack 2 (oder höher) 6.4 erforderlich.
>
>Der SPA-Editor ist die empfohlene Lösung für Projekte, bei denen Client-seitiges Rendering auf Basis eines SPA-Frameworks (z. B. React oder Angular) erforderlich ist.

## Einführung {#introduction}

Dieser Artikel fasst die grundlegenden Funktionen einer einfachen SPA und die Grundlagen zusammen, die Sie für deren Nutzung benötigen.

Weitere Details zur Funktionsweise von SPAs in AEM finden Sie in den folgenden Dokumenten:

* [SPA-Einführung und exemplarische Vorgehensweise](/help/sites-developing/spa-walkthrough.md)

* [Einführung in die SPA-Erstellung](/help/sites-developing/spa-overview.md)

* [SPA-Blueprint](/help/sites-developing/spa-blueprint.md)

>[!NOTE]
>
>Um Inhalt in einer SPA zu erstellen, muss der Inhalt in AEM gespeichert und durch das Inhaltsmodell verfügbar gemacht werden.
>
>Eine SPA, die außerhalb von AEM entwickelt wurde, wird nicht autorisiert, wenn der Content-Modell-Vertrag nicht eingehalten wird.

Dieses Dokument beschreibt die Struktur einer vereinfachten SPA, die mithilfe des React-Frameworks erstellt wurde, und veranschaulicht, wie sie funktioniert, damit Sie dieses Wissen auf Ihre eigene SPA anwenden können.

## Abhängigkeiten, Konfiguration und Aufbau {#dependencies-configuration-and-building}

Zusätzlich zur erwarteten React-Abhängigkeit kann die Beispiel-SPA zusätzliche Bibliotheken nutzen, um die Erstellung der SPA effizienter zu gestalten.

### Abhängigkeiten {#dependencies}

Die `package.json`-Datei definiert die Anforderungen des übergeordneten SPA-Pakets. Die minimalen AEM-Abhängigkeiten für eine funktionierende SPA sind hier aufgelistet.

```
  "dependencies": {
    "@adobe/aem-react-editable-components": "~1.0.4",
    "@adobe/aem-spa-component-mapping": "~1.0.5",
    "@adobe/aem-spa-page-model-manager": "~1.0.3"
  }
```

Da dieses Beispiel auf dem React-Framework basiert, gibt es zwei reaktionsspezifische Abhängigkeiten, die in der Datei `package.json` obligatorisch sind:

```
react
 react-dom
```

Der `aem-clientlib-generator` wird genutzt, um die Erstellung von Client-Bibliotheken als Teil des Build-Prozesses automatisch zu gestalten.

`"aem-clientlib-generator": "^1.4.1",`

Weitere Details dazu können [hier auf GitHub](https://github.com/wcm-io-frontend/aem-clientlib-generator) gefunden werden.

>[!CAUTION]
>
>`aem-clientlib-generator` muss mindestens Version 1.4.1 sein.

Der `aem-clientlib-generator` wird in der Datei `clientlib.config.js` wie folgt konfiguriert.

```
module.exports = {
    // default working directory (can be changed per 'cwd' in every asset option)
    context: __dirname,

    // path to the clientlib root folder (output)
    clientLibRoot: "./../content/jcr_root/apps/my-react-app/clientlibs",

    libs: {
        name: "my-react-app",
        allowProxy: true,
        categories: ["my-react-app"],
        embed: ["my-react-app.responsivegrid"],
        jsProcessor: ["min:gcc"],
        serializationFormat: "xml",
        assets: {
            js: [
                "dist/**/*.js"
            ],
            css: [
                "dist/**/*.css"
            ]
        }
    }
};
```

### Erstellung {#building}

Bei der Erstellung der App wird neben dem aem-clientlib-generator zur automatischen Client-Bibliothekserstellung auch [Webpack](https://webpack.js.org/) für die Übertragung verwendet. Daher ähnelt der Build-Befehl:

`"build": "webpack && clientlib --verbose"`

Sobald das Paket erstellt wurde, kann es in eine AEM-Instanz hochgeladen werden.

### AEM-Projektarchetyp {#aem-project-archetype}

Für jedes AEM-Projekt sollte der [AEM-Projektarchetyp](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de) genutzt werden, der SPA-Projekte mithilfe von React oder Angular unterstützt und das SPA-SDK verwendet.

## Anwendungsstruktur {#application-structure}

Wenn Sie die Abhängigkeiten einbeziehen und Ihre App wie beschrieben erstellen, erhalten Sie ein funktionierendes SPA-Paket, das Sie in Ihre AEM-Instanz hochladen können.

Im nächsten Abschnitt dieses Dokuments erfahren Sie, wie die SPA in AEM strukturiert ist, welche wichtigen Dateien die Anwendung steuern und wie sie zusammenarbeiten.

Eine vereinfachte Bildkomponente wird als Beispiel verwendet, aber alle Komponenten der Anwendung basieren auf dem gleichen Konzept.

### index.js {#index-js}

Der Einstiegspunkt in die SPA ist natürlich die hier gezeigte Datei `index.js`, die sich auf den wichtigen Inhalt konzentriert.

```javascript
import ReactDOM from 'react-dom';
import App from './App';
import { ModelManager, Constants } from "@adobe/aem-spa-page-model-manager";

...

ModelManager.initialize().then((pageModel) => {
ReactDOM.render(
    <App cqChildren={pageModel[Constants.CHILDREN_PROP]} cqItems={pageModel[Constants.ITEMS_PROP]} cqItemsOrder={pageModel[Constants.ITEMS_ORDER_PROP]} cqPath={ModelManager.rootPath} locationPathname={ window.location.pathname }/>
, document.getElementById('page'));

});
```

Die Hauptfunktion von `index.js` ist die Verwendung der Funktion `ReactDOM.render`, um zu bestimmen, wo im DOM die Anwendung injiziert werden soll.

Dies ist eine Standardnutzung dieser Funktion, die nicht nur für diese Beispielanwendung gilt.

#### Statische Instanziierung {#static-instantiation}

Wenn die Komponente mit der Komponentenvorlage (z. B. JSX) statisch instanziiert wird, muss der Wert vom Modell an die Eigenschaften der Komponente übergeben werden.

### App.js {#app-js}

Beim Rendern der Anwendung ruft `index.js` `App.js` auf, die hier in einer vereinfachten Version angezeigt wird, um die Erläuterung auf den wesentlichen Inhalt zu reduzieren.

```
import {Page, withModel } from '@adobe/aem-react-editable-components';

...

class App extends Page {
...
}

export default withModel(App);
```

`App.js` dient hauptsächlich dazu, die Root-Komponenten einzuschließen, aus denen die Anwendung besteht. Der Einstiegspunkt für jede Anwendung ist die Seite.

### Page.js {#page-js}

Durch Rendern der Seite ruft `App.js` das hier aufgelistete `Page.js` in einer vereinfachten Version auf.

```
import {Page, MapTo, withComponentMappingContext } from "@adobe/aem-react-editable-components";

...

class AppPage extends Page {
...
}

MapTo('my-react-app/components/structure/page')(withComponentMappingContext(AppPage));
```

In diesem Beispiel erweitert die `AppPage`-Klasse `Page`. Darin sind die inneren Inhaltsmethoden enthalten, die dann verwendet werden können.

Der `Page` nimmt die JSON-Repräsentation des Seitenmodells auf und verarbeitet den Inhalt, um jedes Element der Seite zu umhüllen/dekorieren. Weitere Details zum `Page` finden Sie im Dokument [SPA-Blueprint](/help/sites-developing/spa-blueprint.md).

### Image.js {#image-js}

Mit der gerenderten Seite können die Komponenten wie `Image.js` wie hier dargestellt gerendert werden.

```
import React, {Component} from 'react';
import {MapTo} from '@adobe/aem-react-editable-components';

require('./Image.css');

const ImageEditConfig = {

    emptyLabel: 'Image',

    isEmpty: function() {
        return !this.props || !this.props.src || this.props.src.trim().length < 1;
    }
};

class Image extends Component {

    render() {
        return (<img src={this.props.src}>);
    }
}

MapTo('my-react-app/components/content/image')(Image, ImageEditConfig);
```

Die zentrale Idee von SPAs in AEM besteht darin, SPA-Komponenten auf AEM-Komponenten abzubilden und die Komponente zu aktualisieren, wenn der Inhalt geändert wird (und umgekehrt). Eine Zusammenfassung dieses Kommunikationsmodells finden Sie im Dokument [SPA-Editor – Überblick](/help/sites-developing/spa-overview.md).

`MapTo('my-react-app/components/content/image')(Image, ImageEditConfig);`

Die `MapTo`-Methode ordnet die SPA-Komponente der AEM-Komponente zu. Sie unterstützt die Verwendung einer einzelnen Zeichenfolge oder eines Arrays von Zeichenfolgen.

`ImageEditConfig` ist ein Konfigurationsobjekt, das dazu beiträgt, die Authoring-Funktionen einer Komponente zu aktivieren, indem die erforderlichen Metadaten bereitgestellt werden, damit der Editor Platzhalter generieren kann

Wenn kein Inhalt vorhanden ist, werden Etiketten als Platzhalter bereitgestellt, um den leeren Inhalt darzustellen.

#### Dynamisch übergebene Eigenschaften {#dynamically-passed-properties}

Die vom Modell stammenden Daten werden als Eigenschaften der Komponente dynamisch übergeben.

## Exportieren bearbeitbarer Inhalte {#exporting-editable-content}

Sie können eine Komponente exportieren und bearbeitbar halten.

```
import React, { Component } from 'react';
import { MapTo } from '@adobe/aem-react-editable-components';

...

const EditConfig = {...}

class PageClass extends Component {...};

...

export default MapTo('my-react-app/react/components/structure/page')(PageClass, EditConfig);
```

Die Funktion `MapTo` gibt eine `Component` zurück, die das Ergebnis einer Komposition ist, die die bereitgestellte `PageClass` mit den Klassennamen und Attributen erweitert, die das Authoring ermöglichen. Diese Komponente kann exportiert werden, um später im Markup Ihrer Anwendung instanziiert zu werden.

Beim Exportieren mithilfe der Funktionen `MapTo` oder `withModel` wird die Komponente `Page` mit einer `ModelProvider`-Komponente umschlossen, die Standardkomponenten Zugriff auf die neueste Version des Seitenmodells oder eine genaue Position in diesem Seitenmodell bietet.

Weitere Informationen finden Sie im Dokument [SPA-Blueprint](/help/sites-developing/spa-blueprint.md).

>[!NOTE]
>
>Standardmäßig erhalten Sie das gesamte Modell der Komponente, wenn Sie die Funktion `withModel` verwenden.

## Freigeben von Informationen zwischen SPA-Komponenten {#sharing-information-between-spa-components}

Regelmäßig müssen Komponenten in einer SPA Daten austauschen. Es gibt mehrere empfohlene Methoden, um dies zu erreichen, wie im Folgenden in der Reihenfolge zunehmender Komplexität aufgeführt.

* **Option 1:** Zentralisieren Sie die Logik und senden Sie sie an die erforderlichen Komponenten, z. B. mithilfe von React Context.
* **Option 2:** Geben Sie Komponentenstatus mithilfe einer Statusbibliothek wie Redux frei.
* **Option 3:** Nutzen Sie die Objekthierarchie durch Anpassen und Erweitern der Container-Komponente.


## Nächste Schritte {#next-steps}

Eine schrittweise Anleitung zum Erstellen einer eigenen SPA finden Sie unter [Erste Schritte mit dem AEM-SPA-Editor – WKND-Events-Tutorial](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/spa-editor/spa-editor-framework-feature-video-use.html?lang=de).

Weitere Informationen dazu, wie Sie sich für die Entwicklung von SPAs für AEM organisieren können, finden Sie im Artikel [Entwickeln von SPAs für AEM](/help/sites-developing/spa-architecture.md).

Weitere Informationen zum dynamischen Modell für die Komponentenzuordnung und dazu, wie es mit SPAs in AEM funktioniert, finden Sie im Artikel [Dynamisches Modell für die Komponentenzuordnung bei SPAs](/help/sites-developing/spa-dynamic-model-to-component-mapping.md).

Wenn Sie SPAs in AEM für ein anderes Framework als React oder Angular implementieren oder einfach nur tief in die Funktionsweise des SPA-SDK für AEM eintauchen möchten, lesen Sie den Artikel [SPA Blueprint](/help/sites-developing/spa-blueprint.md).
