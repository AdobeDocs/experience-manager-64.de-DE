---
title: Clientlibs für Communities-Komponenten
seo-title: Clientlibs für Communities-Komponenten
description: Clientseitige Bibliotheken für Communities
seo-description: Clientseitige Bibliotheken für Communities
uuid: 0a62f629-e6af-4269-862e-0595824c329f
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 7d423dff-8710-4f43-ad55-8863169946e2
translation-type: tm+mt
source-git-commit: 59d40b5bddc42a4ac057ef600243f396aefc926b
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 2%

---


# clipplibs für Communities-Komponenten {#clientlibs-for-communities-components}

## Einführung {#introduction}

In diesem Abschnitt der Dokumentation wird beschrieben, wie clientseitige Bibliotheken (clientlibs) zu einer Seite für Communities-Komponenten hinzugefügt werden.

Grundlegende Informationen finden Sie unter:

* [Verwenden clientseitiger ](../../help/sites-developing/clientlibs.md) Bibliotheken, die Nutzungsdetails sowie Debuggingwerkzeuge bereitstellen
* [clipplibs für ](client-customize.md#clientlibs) SCF, das nützliche Informationen zum Anpassen von SCF-Komponenten bereitstellt
* [Blog: AEM Client-Bibliotheken, erklärt durch Beispiel](https://blogs.adobe.com/experiencedelivers/experience-management/clientlibs-explained-example/)

## Warum clientlibs erforderlich ist {#why-clientlibs-are-required}

Clientlibs sind für das ordnungsgemäße Funktionieren (JavaScript) und die Formatierung (CSS) einer Komponente erforderlich.

Wenn für eine Funktion eine [Community-Funktion](functions.md) vorhanden ist, werden alle erforderlichen Komponenten und Konfigurationen, einschließlich der erforderlichen clientlibs, auf der Community-Site vorhanden sein. Nur wenn Autoren zusätzliche Komponenten zur Verfügung stehen sollen, müssen zusätzliche clientlibs hinzugefügt werden.

Wenn die erforderlichen clientlibs fehlen, kann das Hinzufügen einer Communities-Komponente zu einer Seite](author-communities.md) zu JavaScript-Fehlern und zu einem unerwarteten Erscheinungsbild führen.[

### Beispiel: Platzierte Reviews ohne clientlibs {#example-placed-reviews-without-clientlibs}

![chlimage_1-244](assets/chlimage_1-244.png)

### Beispiel: Platzierte Reviews mit clientlibs {#example-placed-reviews-with-clientlibs}

![chlimage_1-245](assets/chlimage_1-245.png)

## Identifizieren erforderlicher Clientlibs {#identifying-required-clientlibs}

Die wesentlichen Funktionsinformationen für Entwickler identifizieren die erforderlichen clientlibs.

Darüber hinaus können Sie von einer AEM Instanz aus im [Community-Komponentenleitfaden](components-guide.md) auf eine Auflistung der für eine Komponente erforderlichen clientlib-Kategorien zugreifen.

Beispiel: Am oberen Rand der Seite [Reviews](http://localhost:4502/content/community-components/en/reviews.html) sind die erforderlichen clientlibs aufgelistet

* cq.ckeditor
* cq.social.hbs.reviews

![chlimage_1-246](assets/chlimage_1-246.png)

## Erforderliche Clientlibs {#adding-required-clientlibs} hinzufügen

Wenn Sie einer Seite eine Communities-Komponente hinzufügen möchten, müssen Sie die erforderlichen clientlibs für die Komponente hinzufügen, falls diese noch nicht vorhanden ist.

Verwenden Sie [CRXDE|Lite](#using-crxde-lite), um eine vorhandene clientlibslist für eine Community-Site-Seite zu ändern.

So fügen Sie mithilfe von [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md) eine clientlib für eine Community-Site hinzu:

* Gehen Sie zu [https://&lt;server>:&lt;port>/crx/de](http://localhost:4502/crx/de)
* Suchen Sie den Knoten `clientlibslist` für die Seite, auf der Sie die Komponente hinzufügen möchten

   * `/content/sites/sample/en/page/jcr:content/clientlibslist`

* Bei Auswahl des Knotens `clientlibslist`

   * Suchen Sie die Eigenschaft String[] `scg:requiredClientLibs`
   * Wählen Sie die zugehörige `Value`, um auf das Dialogfeld &quot;String-Array&quot;zuzugreifen

      * Bei Bedarf scrollen
      * Wählen Sie `+` aus, um eine neue Client-Bibliothek einzugeben.

         * Wiederholen, um weitere Client-Bibliotheken hinzuzufügen
      * Wählen Sie **[!UICONTROL OK]** aus
   * Wählen Sie **[!UICONTROL Alle speichern]**



>[!NOTE]
>
>Wenn die Site keine Community-Site ist, muss die Existenz oder der Speicherort der Client-Bibliotheken, die für die Site verwendet werden, ermittelt werden.

Mithilfe des Beispiels [Erste Schritte mit AEM Communities](getting-started.md), bei dem `site-name` *engagement* lautet, wird die clientliblist wie folgt angezeigt, wenn die Komponente &quot;reviews&quot;hinzugefügt wird:

![chlimage_1-247](assets/chlimage_1-247.png)

