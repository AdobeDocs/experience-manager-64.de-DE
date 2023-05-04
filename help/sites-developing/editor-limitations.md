---
title: Editor-Einschränkungen
seo-title: Editor Limitations
description: Der Editor in der Touch-optimierten Benutzeroberfläche nutzt Überlagerungen, um mit Inhalten zu interagieren, die in einem iframe enthalten sind. Diese Interaktion verursacht einige Einschränkungen für die Verwendung des Editors sowie für Entwickler.
seo-description: The editor in the touch-enabled UI makes use of overlays to interact with content confined in an iframe. This interaction creates some limitations in both usage of the editor and also for developers.
uuid: ff524530-3f3a-4c5b-9f94-4aa9aeb9d461
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: introduction
discoiquuid: d748decb-a614-4c9e-a502-d6176b720f1a
exl-id: ce860880-5954-4f72-8ec6-60209c1ec659
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 61%

---

# Editor-Einschränkungen{#editor-limitations}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Der Editor in der Touch-optimierten Benutzeroberfläche nutzt Überlagerungen, um mit Inhalten zu interagieren, die in einem iframe enthalten sind. Diese Interaktion verursacht einige Einschränkungen für die Verwendung des Editors sowie für Entwickler. Diese Seite fasst diese Einschränkungen zusammen und bietet nach Möglichkeit Lösungen oder Umgehungen.

## Funktionale Einschränkungen {#functional-limitations}

Autoren sehen sich bei der Arbeit mit dem Editor zur Bearbeitung von Seiten möglicherweise mit den folgenden funktionalen Einschränkungen konfrontiert.

### Links nicht aktiv {#links-not-active}

Beim [Bearbeiten einer Seite](/help/sites-authoring/editing-content.md) sind Links nicht aktiv.

* [Wechseln Sie in den Modus **Vorschau**](/help/sites-authoring/editing-content.md#preview-mode), um anhand der Links in den Inhalten zu navigieren.

### Strukturseiten {#structure-pages}

Seiten dürfen nicht `structure` genannt werden. Seiten mit dem Namen `structure` können im Seiteneditor nicht bearbeitet werden.

## CSS-Einschränkungen {#css-limitations}

Entwickler sehen sich hinsichtlich der Interaktionen des Editors mit CSS möglicherweise mit den folgenden Einschränkungen konfrontiert.

### Absolut positionierte Elemente {#absolutely-positioned-elements}

Absolut positionierte Elemente können Probleme bei der Position ihrer Überlagerung verursachen.

* Stellen Sie in diesem Fall sicher, dass die Dimensionen des absolut positionierten Elements korrekt sind, da der Editor eine Überlagerung mit exakt denselben Dimensionen erstellt.

### vh-Einheiten {#vh-units}

`vh`-Einheiten werden nicht unterstützt, da die iframe-Höhe von AEM automatisch angepasst werden muss.

### Feste Hintergrundbilder {#fixed-background-images}

Feste Hintergrundbilder werden beim Scrollen möglicherweise nicht als fest angezeigt, da sie in einen iframe eingebettet sind.

* Wird in der Kopfzeile **Seite als veröffentlicht anzeigen** ausgewählt, wird die Seite korrekt angezeigt.

### 100 % Höhe {#height}

100 % Höhe wird im Hauptteilelement einer Seite nicht unterstützt.

* Dieses Problem kann umgangen werden, um einen Vollbildhauptteil zu implementieren, indem das Hauptteilelement wie folgt gestreckt wird:

```xml
body {
    position: absolute;
    top: 0;
    bottom: 0;
    right: 0;
    left: 0;
}
```

### Ausblenden des Seitenrands {#margin-collapsing}

Probleme beim Ausblenden des Seitenrands treten auf, wenn das erste untergeordnete Element des Hauptteilelements einen Seitenrand aufweist.

* Die Lösung besteht darin, auf Ebene des Hauptteilelements einen Clearfix wie folgt einzufügen:

```xml
body:before, body:after{
    content: ' ';
    display: table;
}
```
