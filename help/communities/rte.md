---
title: Grundlagen zum Rich-Text-Editor
seo-title: Rich Text Editor Essentials
description: Übersicht über die Rich-Text-Editor-Funktion
seo-description: Rich text Editor feature overview
uuid: f96015cc-114b-431a-a5ba-dc195c2a0b83
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 0225a543-0fad-488b-8b0b-8b3512d44fbe
exl-id: d236a8d3-20ad-4568-a7c2-87d146aa0532
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 7%

---

# Grundlagen zum Rich-Text-Editor {#rich-text-editor-essentials}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Übersicht {#overview}

Ein Rich-Text-Editor (RTE) bietet die Möglichkeit, Text mit Markup einzugeben.

Bei Communities-Komponenten ähneln sie der [Rich-Text-Editor in der Autorenumgebung](../../help/sites-authoring/rich-text-editor.md), wirkt sich dies auf den in der Veröffentlichungsumgebung eingegebenen Text aus.

![chlimage_1-410](assets/chlimage_1-410.png)

## Aktivieren des Rich-Text-Editors {#enabling-rich-text-editor}

Communities-Komponenten, die benutzergenerierte Inhalte (UGC) zulassen, können aktiviert werden, um den RTE zuzulassen. Je nachdem, ob die Komponente zu einer Seite hinzugefügt oder in einer [function](functions.md), kann der RTE standardmäßig aktiviert sein oder nicht.

Wenn diese Option nicht aktiviert ist, geben Sie einfach ein. [Bearbeitungsmodus des Autors](sites-console.md#authoring-site-content), wählen Sie die zu bearbeitende Komponente aus und wählen Sie die `Rich Text Editor` aktivieren.

RTE ist für die folgenden Communities-Komponenten verfügbar:

* [Blog](blog-feature.md)
* [Kalender](calendar.md)
* [Kommentare](comments.md)
* [FileLibrary](file-library.md)
* [Forum](forum.md)
* [Messaging](configure-messaging.md)
* [Fragen und Antworten](working-with-qna.md)
* [Bewertungen](reviews.md)

## Anpassung {#customization}

Die Anpassung des Rich-Text-Editors ist möglich, da die Implementierung auf [CKEditor](https://www.ckeditor.com/).

Die aktuelle Konfiguration für Communities-Komponenten befindet sich im `cq.social.  scf   clientlib`im Repository unter

`/libs/clientlibs/social/commons/scf/ckrte.js`

Eine Änderung der clientlib cq.social.scf wird nicht empfohlen, da zukünftige Upgrades Änderungen überschreiben können.

### Beispielanpassung: Inline-Links {#example-customization-inline-links}

Aus Sicherheitsgründen sind die Hyperlink-Optionen nicht im Satz von Rich-Text-Symbolen enthalten, die Mitgliedern standardmäßig angezeigt werden. Die Fähigkeit, Unruhe zu stiften, ist groß, wenn href in UGC erlaubt sind.

So fügen Sie die Hyperlink-Optionen zur Symbolleiste hinzu:

* Hinzufügen einer Symbolleiste mit dem Namen `links`&quot;
   * `{ name: 'links', items: [ 'Link','Unlink','Anchor' ] }`
* Klicken Sie auf **[!UICONTROL Alle speichern]**

#### /libs/clientlibs/social/commons/scf/ckrte.js {#libs-clientlibs-social-commons-scf-ckrte-js}

```
CKRte.prototype.config = {
    toolbar: [
        { name: "basicstyles",
           items: ["Bold", "Italic", "Underline", "NumberedList", "BulletedList", "Outdent", "Indent", "JustifyLeft", "JustifyCenter", "JustifyRight", "JustifyBlock", "TextColor"]
        },
        { name: 'links', 
           items: [ 'Link','Unlink','Anchor' ] 
        }
    ],
    autoParagraph: false,
    autoUpdateElement: false,
    removePlugins: "elementspath",
    resize_enabled: false
};
```
