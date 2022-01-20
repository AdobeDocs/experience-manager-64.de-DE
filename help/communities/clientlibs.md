---
title: Clientlibs für Communities-Komponenten
seo-title: Clientlibs for Communities Components
description: Client-seitige Bibliotheken für Communities
seo-description: Client-side libraries for Communities
uuid: 0a62f629-e6af-4269-862e-0595824c329f
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 7d423dff-8710-4f43-ad55-8863169946e2
exl-id: 9b4ed16f-3c7c-478a-a897-9b4be086988b
source-git-commit: 9178c3a01e7f450d3794f41605fb3788231c88c0
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 3%

---

# Clientlibs für Communities-Komponenten {#clientlibs-for-communities-components}

## Einführung {#introduction}

In diesem Abschnitt der Dokumentation wird beschrieben, wie Sie clientseitige Bibliotheken (clientlibs) zu einer Seite für Communities-Komponenten hinzufügen.

Grundlegende Informationen finden Sie unter:

* [Verwenden Client-seitiger Bibliotheken](../../help/sites-developing/clientlibs.md) , das Nutzungsdetails sowie Debugging-Tools bereitstellt
* [Clientlibs für SCF](client-customize.md#clientlibs) , die nützliche Informationen beim Anpassen von SCF-Komponenten bietet

## Warum Clientlibs erforderlich sind {#why-clientlibs-are-required}

Clientlibs sind für die ordnungsgemäße Funktion (JavaScript) und Formatierung (CSS) einer Komponente erforderlich.

Wenn eine [Community-Funktion](functions.md) für eine Funktion sind alle erforderlichen Komponenten und Konfigurationen, einschließlich der erforderlichen clientlibs, auf der Community-Site vorhanden. Nur wenn Autoren zusätzliche Komponenten zur Verfügung stehen sollen, müssen zusätzliche Client-Bibliotheken hinzugefügt werden.

Wenn die erforderlichen clientlibs fehlen, [Hinzufügen einer Communities-Komponente zu einer Seite](author-communities.md) kann zu JavaScript-Fehlern sowie einem unerwarteten Erscheinungsbild führen.

### Beispiel: Platzierte Prüfungen ohne Clientlibs {#example-placed-reviews-without-clientlibs}

![chlimage_1-244](assets/chlimage_1-244.png)

### Beispiel: Platzierte Prüfungen mit Clientlibs {#example-placed-reviews-with-clientlibs}

![chlimage_1-245](assets/chlimage_1-245.png)

## Identifizieren erforderlicher Clientlibs {#identifying-required-clientlibs}

Die grundlegenden Funktionsinformationen für Entwickler identifizieren die erforderlichen Clientlibs.

Darüber hinaus navigieren Sie von einer AEM-Instanz zum [Handbuch zu Community-Komponenten](components-guide.md) bietet Zugriff auf eine Liste von clientlib-Kategorien, die für eine Komponente erforderlich sind.

Beispiel: ganz oben im [Überprüfungsseite](http://localhost:4502/content/community-components/en/reviews.html) die aufgelisteten erforderlichen clientlibs

* cq.ckeditor
* cq.social.hbs.reviews

![chlimage_1-246](assets/chlimage_1-246.png)

## Hinzufügen erforderlicher Clientlibs {#adding-required-clientlibs}

Wenn Sie eine Communities-Komponente zu einer Seite hinzufügen möchten, müssen Sie die erforderlichen Clientlibs für die Komponente hinzufügen, falls diese noch nicht vorhanden ist.

Verwendung [CRXDE|Lite](#using-crxde-lite) , um eine vorhandene Clientlibsliste für eine Community-Site-Seite zu ändern.

So fügen Sie eine Clientlib für eine Community-Site hinzu: [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Navigieren Sie zu [https://&lt;server>:&lt;port>/crx/de](http://localhost:4502/crx/de)
* Suchen Sie die `clientlibslist` Knoten für die Seite, auf der Sie die Komponente hinzufügen möchten

   * `/content/sites/sample/en/page/jcr:content/clientlibslist`

* Mit `clientlibslist` Knoten ausgewählt

   * Suchen Sie den String .[] property `scg:requiredClientLibs`
   * Auswahl der `Value` , um auf das Dialogfeld String-Array zuzugreifen

      * Scrollen Sie bei Bedarf nach unten
      * Auswählen `+` , um eine neue Client-Bibliothek aufzurufen

         * Wiederholen Sie diesen Vorgang, um weitere Client-Bibliotheken hinzuzufügen.
      * Klicken Sie auf **[!UICONTROL OK]**
   * Wählen Sie **[!UICONTROL Alle speichern]** aus



>[!NOTE]
>
>Wenn es sich bei der Site nicht um eine Community-Site handelt, müssen die Existenz oder der Speicherort der Client-Bibliotheken, die für die Site verwendet werden, ermittelt werden.

Verwenden der [Erste Schritte mit AEM Communities](getting-started.md) Beispiel, wobei `site-name` is *interagieren* festgelegt ist, wird die clientliblist so angezeigt, wenn die Reviews-Komponente hinzugefügt wird:

![chlimage_1-247](assets/chlimage_1-247.png)
