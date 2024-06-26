---
title: Komponenten-Sideloading
seo-title: Component Sideloading
description: Das Sideloading von Communities-Komponenten ist nützlich, wenn eine Webseite als einfache Einzelseitenanwendung konzipiert ist, die die Anzeige dynamisch ändert, je nachdem, was der Besucher der Site auswählt.
seo-description: Communities component sideloading is useful when a web page is designed as a simple, single page app that dynamically alters what is displayed depending on what is selected by the site visitor
uuid: 8c9a5fde-26a3-4610-bc14-f8b665059015
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: a9cb5294-e5ab-445b-b7c2-ffeecda91c50
exl-id: 12fdc503-29b6-4970-a883-c22162f7a9eb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 2%

---

# Komponenten-Sideloading {#component-sideloading}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Übersicht {#overview}

Das Sideloading von Communities-Komponenten ist nützlich, wenn eine Webseite als einfache Einzelseitenanwendung konzipiert ist, die die Anzeige dynamisch ändert, je nachdem, was der Besucher der Site ausgewählt hat.

Dies wird erreicht, wenn Communities-Komponenten nicht in der Seitenvorlage vorhanden sind, sondern nach der Auswahl eines Site-Besuchers dynamisch hinzugefügt werden.

Da das Social-Komponenten-Framework (SCF) über eine leichte Präsenz verfügt, werden nur SCF-Komponenten registriert, die zum Zeitpunkt des ersten Seitenladevorgangs vorhanden sind. Damit eine dynamisch hinzugefügte SCF-Komponente nach dem Laden der Seite registriert werden kann, muss SCF aufgerufen werden, um die Komponente zu &quot;sideload&quot;zu laden.

Wenn eine Seite für das Sideloaden von Communities-Komponenten entwickelt wurde, ist es möglich, die gesamte Seite zwischenzuspeichern.

Die Schritte zum dynamischen Hinzufügen von SCF-Komponenten sind:

1. [Komponente zum DOM hinzufügen](#dynamically-add-component-to-dom)

1. [Sideloaden der Komponente](#sideload-by-invoking-scf) Verwendung einer von zwei Methoden:

* [Dynamische Integration](#dynamic-inclusion)
   * Alle dynamisch hinzugefügten Komponenten verstärken
* [Dynamisches Laden](#dynamic-loading)
   * Eine bestimmte Komponente bei Bedarf hinzufügen

>[!NOTE]
>
>Sideloading [nicht vorhandene Ressourcen](scf.md#add-or-include-a-communities-component) wird nicht unterstützt.

## Dynamisches Hinzufügen einer Komponente zu DOM {#dynamically-add-component-to-dom}

Unabhängig davon, ob die Komponente dynamisch eingeschlossen oder dynamisch geladen wird, muss sie zuerst zum DOM hinzugefügt werden.

Beim Hinzufügen der SCF-Komponente ist das am häufigsten zu verwendende Tag das DIV-Tag. Es können jedoch auch andere Tags verwendet werden. Da SCF das DOM nur beim erstmaligen Laden der Seite überprüft, wird dieses Hinzufügen zum DOM nicht bemerkt, bis SCF explizit aufgerufen wird.

Welches Tag verwendet wird, mindestens muss das Element dem normalen SCF-Stammelementmuster entsprechen, indem es die beiden folgenden Attribute enthält:

* **data-component-id**
Der effektive Pfad zur hinzugefügten Komponente

* **data-scf-component**
Der resourceType der Komponente

Im Folgenden finden Sie ein Beispiel einer hinzugefügten Kommentarkomponente:

```xml
<div
    class="scf-commentsystem scf translation-commentsystem" 
    data-component-id="<%= currentPage.getPath()%>/jcr:content/content-left/comments"
    data-scf-component="social/commons/components/hbs/comments"
>
</div>
```

## Sideload durch Aufrufen von SCF {#sideload-by-invoking-scf}

### Dynamische Integration {#dynamic-inclusion}

Die dynamische Einbindung verwendet eine Bootstrap-Anfrage, die dazu führt, dass SCF das DOM prüft und alle auf der Seite vorhandenen SCF-Komponenten bootet.

Um SCF-Komponenten jederzeit nach dem Laden der Seite zu initialisieren, lösen Sie einfach ein JQuery-Ereignis wie folgt aus:

$(document).Trigger(SCF.events.BOOTSTRAP_REQUEST);

### Dynamisches Laden {#dynamic-loading}

Dynamisches Laden bietet Kontrolle über das Laden von SCF-Komponenten.

Anstatt alle im DOM gefundenen SCF-Komponenten per Bootstrapping durchzuführen, können Sie eine bestimmte SCF-Komponente angeben, die mit dieser JavaScript-Methode geladen werden soll:

SCF.addComponent(document.getElementById(*someId*);

Wo *someId* ist der Wert der **data-component-id** -Attribut.
