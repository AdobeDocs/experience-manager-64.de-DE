---
title: Ändern des Farbschemas der Benutzeroberfläche
seo-title: Changing the color scheme of the interface
description: So ändern Sie das Farbschema der Benutzeroberfläche von AEM Forms Workspace selektiv.
seo-description: How to modify the color scheme of AEM Forms workspace user interface portions selectively.
uuid: 32c32f7a-8271-4d2c-8a1f-ad5ab3c90b83
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 18dab82a-badf-4c32-83a2-cd5cb04cae89
exl-id: efbb9a9e-0ddf-49f2-bcb8-14cd0c6de5ee
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 47%

---

# Ändern des Farbschemas der Benutzeroberfläche {#changing-the-color-scheme-of-the-interface}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Sie können das Farbschema von Bereichen der Benutzeroberfläche von AEM Forms Workspace Ihren Anforderungen entsprechend ändern. Im Folgenden finden Sie einige Beispiele für repräsentative Anpassungen des Farbschemas. Zusätzlich zu den in diesem Artikel besprochenen Schritten finden Sie mehr unter [Generische Schritte für die Anpassung des AEM Forms-Arbeitsbereichs](/help/forms/using/generic-steps-html-workspace-customization.md).

## Navigationsleiste oben {#top-navigation-bar}

### Hintergrundbild verwenden {#using-background-image}

So aktualisieren Sie die Navigationsleiste am oberen Rand von AEM Forms Workspace.

1. Erstellen Sie ein Hintergrundbild, um die Farbe zu aktualisieren. Benennen Sie die Datei mit newBackground.jpg.
1. Laden Sie die Hintergrundbilddatei mithilfe eines WebDAV-Clients in den Ordner /apps/ws/images hoch.

   >[!NOTE]
   >
   >Weitere Informationen zum WebDAV-Zugriff finden Sie unter [https://dev.day.com/docs/en/crx/current/how_to/webdav_access.html](https://docs.adobe.com/docs/de/crx/current/how_to/webdav_access.html).

1. Referenzieren Sie das neue Hintergrundbild in /apps/ws/css/newStyle.css , indem Sie folgenden Stil hinzufügen.

   ```css
   #header {
       background:#292929 url(../images/newBackground.jpg) repeat-x;
   }
   ```

### Verwenden der Farbeigenschaft in CSS {#using-color-property-in-css}

1. Fügen Sie den folgenden Stil in newStyle.css unter /apps/ws/css hinzu

   ```css
   #header {
   background : none;
   background-color: gray;
   }
   ```

## Kategoriekomponente {#category-component}

Die Komponente Kategorie zeigt die verschiedenen Kategorien Ihrer Aufgaben im linken Bereich an. Um die Farbe zu ändern, definieren Sie die Hintergrundfarbe im `.category`-Element der CSS-Datei.

## Task-Komponente {#task-component}

Aufgaben werden im mittleren Fenster, der TaskList-Komponente, angezeigt. Um die Farbe zu ändern, ändern Sie den Stil, der mit .task-Auswahl im Stylesheet verknüpft ist.
