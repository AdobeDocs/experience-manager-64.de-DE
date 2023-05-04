---
title: Erstellen einer Beispielseite
seo-title: Create a Sample Page
description: Erstellen einer Beispiel-Community-Site
seo-description: Create a Sample community site
uuid: 04a8f027-b7d8-493a-a9bd-5c4a6715d754
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
content-type: reference
topic-tags: developing
discoiquuid: a03145f7-6697-4797-b73e-6f8d241ce469
exl-id: 00ac29fb-cc8f-4dd9-a261-839a4bf664c2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 5%

---

# Erstellen einer Beispielseite {#create-a-sample-page}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Ab AEM 6.1 Communities ist es am einfachsten, eine Beispielseite zu erstellen, indem eine einfache Community-Site erstellt wird, die aus einer Page-Funktion besteht.

Dies umfasst eine parsys-Komponente, mit der Sie [Komponenten für die Bearbeitung aktivieren](basics.md#accessing-communities-components).

Eine weitere Möglichkeit zur Erforschung von Beispielkomponenten besteht darin, die Funktionen zu verwenden, die im Abschnitt [Handbuch zu Community-Komponenten](components-guide.md).

## Community-Site erstellen {#create-a-community-site}

Dies ähnelt dem Erstellen einer neuen Site, die unter [Erste Schritte mit AEM Communities](getting-started.md).

Der Hauptunterschied besteht darin, dass dieses Tutorial eine neue Community-Site-Vorlage erstellt, die nur die [Seitenfunktion](functions.md#page-function) um eine einfache Community-Site zu erstellen, die frei von anderen Funktionen ist (außer den vorab verkabelten Funktionen, die für alle Community-Sites grundlegend sind).

### Neue Site-Vorlage erstellen {#create-new-site-template}

Erstellen Sie zunächst eine einfache [Community-Site-Vorlage](sites.md).

Wählen Sie in der globalen Navigation auf der Autoreninstanz die Option **[!UICONTROL Tools > Communities > Site-Vorlagen]**.

![chlimage_1-82](assets/chlimage_1-82.png)

* Klicken Sie auf `Create button`
* GRUNDLEGENDE INFORMATIONEN

   * `Name`: Einzelseitenvorlage
   * `Description`: Eine Vorlage, die aus einer einzelnen Seitenfunktion besteht.
   * Wählen Sie `Enabled` aus.

![chlimage_1-83](assets/chlimage_1-83.png)

* STRUKTUR

   * Ziehen Sie eine `Page` -Funktion zum Vorlagen-Builder
   * Geben Sie für Details zur Konfigurationsfunktion ein.

      * `Title`: Einzelseite
      * `URL`: Seite

![chlimage_1-84](assets/chlimage_1-84.png)

* Auswählen **`Save`** für die Konfiguration
* Auswählen **`Save`** für die Site-Vorlage

### Neue Community-Site erstellen {#create-new-community-site}

Erstellen Sie nun eine neue Community-Site basierend auf der einfachen Site-Vorlage.

Wählen Sie nach der Erstellung der Site-Vorlage in der globalen Navigation die Option **[!UICONTROL Communities > Sites]**.

![chlimage_1-85](assets/chlimage_1-85.png)

* Auswählen **`Create`** icon

* Schritt `1 - Site Template`

   * `Title`: Einfache Community-Site
   * `Description`: Eine Community-Site, die aus einer einzelnen Seite zum Experimentieren besteht.
   * `Community Site Root: (leave blank)`
   * `Community Site Base Language: English`
   * `Name`: sample

      * url = http://localhost:4502/content/sites/sample
   * `Template`: Auswählen `Single Page Template`


![chlimage_1-86](assets/chlimage_1-86.png)

* Klicken Sie auf `Next`
* Schritt `2 - Design`

   * Entwurf auswählen

* Klicken Sie auf `Next`
* Klicken Sie auf `Next`

   (Alle Standardeinstellungen akzeptieren)

* Klicken Sie auf `Create`

![chlimage_1-87](assets/chlimage_1-87.png)

## Veröffentlichen der Site {#publish-the-site}

![chlimage_1-88](assets/chlimage_1-88.png)

Aus dem [Community-Sites-Konsole](sites-console.md)Wählen Sie das Veröffentlichungssymbol aus, um die Site zu veröffentlichen. Standardmäßig ist dies &quot;http://localhost:4503&quot;.

## Öffnen Sie die Site im Autorenmodus im Bearbeitungsmodus. {#open-the-site-on-author-in-edit-mode}

![chlimage_1-89](assets/chlimage_1-89.png)

Wählen Sie das Symbol zum Öffnen der Site aus, um die Site im Bearbeitungsmodus anzuzeigen.

Die URL lautet [http://localhost:4502/editor.html/content/sites/sample/en.html](http://localhost:4502/editor.html/content/sites/sample/en.html)

![chlimage_1-90](assets/chlimage_1-90.png)

Auf der einfachen Startseite können Sie sehen, was über die Community-Funktionen und -Vorlagen vorab verkabelt ist, und mit dem Hinzufügen und Konfigurieren von Community-Komponenten spielen.

## Site zur Veröffentlichung anzeigen {#view-site-on-publish}

Öffnen Sie nach dem Veröffentlichen der Seite die Seite auf der [Veröffentlichungsinstanz](http://localhost:4503/content/sites/sample/en.html) , um mit den Funktionen als anonymer Site-Besucher, angemeldeter Mitglied oder Administrator zu experimentieren. Der in der Autorenumgebung angezeigte Link Administration wird in der Veröffentlichungsumgebung nur angezeigt, wenn sich ein Administrator anmeldet.
