---
title: Clientlibs für Communities-Komponenten
seo-title: Clientlibs für Communities-Komponenten
description: Client-seitige Bibliotheken für Communities
seo-description: Client-seitige Bibliotheken für Communities
uuid: 0a62f629-e6af-4269-862e-0595824c329f
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 7d423dff-8710-4f43-ad55-8863169946e2
exl-id: 9b4ed16f-3c7c-478a-a897-9b4be086988b
source-git-commit: 9178c3a01e7f450d3794f41605fb3788231c88c0
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 2%

---

# Clientlibs für Communities-Komponenten {#clientlibs-for-communities-components}

## Einführung {#introduction}

In diesem Abschnitt der Dokumentation wird beschrieben, wie Sie clientseitige Bibliotheken (clientlibs) zu einer Seite für Communities-Komponenten hinzufügen.

Grundlegende Informationen finden Sie unter:

* [Verwendung clientseitiger ](../../help/sites-developing/clientlibs.md) Bibliotheken, die Nutzungsdetails sowie Debugging-Tools bereitstellt
* [Clientlibs für ](client-customize.md#clientlibs) SCF, die nützliche Informationen beim Anpassen von SCF-Komponenten bereitstellen

## Warum Clientlibs erforderlich sind {#why-clientlibs-are-required}

Clientlibs sind für die ordnungsgemäße Funktion (JavaScript) und Formatierung (CSS) einer Komponente erforderlich.

Wenn für eine Funktion eine [Community-Funktion](functions.md) vorhanden ist, sind alle erforderlichen Komponenten und Konfigurationen, einschließlich der erforderlichen clientlibs, auf der Community-Site vorhanden. Nur wenn Autoren zusätzliche Komponenten zur Verfügung stehen sollen, müssen zusätzliche Client-Bibliotheken hinzugefügt werden.

Wenn die erforderlichen clientlibs fehlen, kann das Hinzufügen einer Communities-Komponente zu einer Seite](author-communities.md) zu JavaScript-Fehlern sowie zu einem unerwarteten Erscheinungsbild führen.[

### Beispiel: Platzierte Prüfungen ohne Clientlibs {#example-placed-reviews-without-clientlibs}

![chlimage_1-244](assets/chlimage_1-244.png)

### Beispiel: Platzierte Prüfungen mit Clientlibs {#example-placed-reviews-with-clientlibs}

![chlimage_1-245](assets/chlimage_1-245.png)

## Identifizieren erforderlicher Clientlibs {#identifying-required-clientlibs}

Die grundlegenden Funktionsinformationen für Entwickler identifizieren die erforderlichen Clientlibs.

Darüber hinaus bietet das Navigieren von einer AEM-Instanz zum [Community Components Guide](components-guide.md) Zugriff auf eine Liste von clientlib-Kategorien, die für eine Komponente erforderlich sind.

Am Anfang der [Seite &quot;Bewertungen&quot;](http://localhost:4502/content/community-components/en/reviews.html) sind die erforderlichen clientlibs aufgeführt.

* cq.ckeditor
* cq.social.hbs.reviews

![chlimage_1-246](assets/chlimage_1-246.png)

## Hinzufügen erforderlicher Clientlibs {#adding-required-clientlibs}

Wenn Sie eine Communities-Komponente zu einer Seite hinzufügen möchten, müssen Sie die erforderlichen Clientlibs für die Komponente hinzufügen, falls diese noch nicht vorhanden ist.

Verwenden Sie [CRXDE|Lite](#using-crxde-lite), um eine vorhandene Clientlibslist für eine Community-Site-Seite zu ändern.

So fügen Sie eine clientlib für eine Community-Site mit [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md) hinzu:

* Navigieren Sie zu [https://&lt;server>:&lt;port>/crx/de](http://localhost:4502/crx/de)
* Suchen Sie den Knoten `clientlibslist` für die Seite, auf der Sie die Komponente hinzufügen möchten

   * `/content/sites/sample/en/page/jcr:content/clientlibslist`

* Mit dem ausgewählten Knoten `clientlibslist`

   * Suchen Sie die Eigenschaft String[] `scg:requiredClientLibs` .
   * Wählen Sie die zugehörige `Value` aus, um auf das Dialogfeld &quot;String-Array&quot;zuzugreifen

      * Scrollen Sie bei Bedarf nach unten
      * Wählen Sie `+` aus, um eine neue Client-Bibliothek einzugeben.

         * Wiederholen Sie diesen Vorgang, um weitere Client-Bibliotheken hinzuzufügen.
      * Wählen Sie **[!UICONTROL OK]** aus
   * Wählen Sie **[!UICONTROL Alle speichern]**



>[!NOTE]
>
>Wenn es sich bei der Site nicht um eine Community-Site handelt, müssen die Existenz oder der Speicherort der Client-Bibliotheken, die für die Site verwendet werden, ermittelt werden.

Unter Verwendung des Beispiels [Erste Schritte mit AEM Communities](getting-started.md), in dem `site-name` *engage* ist, würde die clientliblist so angezeigt, wenn die Überprüfungskomponente hinzugefügt wird:

![chlimage_1-247](assets/chlimage_1-247.png)
