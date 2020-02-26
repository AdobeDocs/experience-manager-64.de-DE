---
title: Textüberlagerung
seo-title: Textüberlagerung
description: Textüberlagerung ist eine Funktion in AEM Screens, mit der Sie in einem Sequenzkanal für ein überzeugendes Erlebnis sorgen können, indem Sie einen Titel oder eine Beschreibung auf einem Bild einfügen. Auf dieser Seite erfahren Sie mehr.
seo-description: Textüberlagerung ist eine Funktion in AEM Screens, mit der Sie in einem Sequenzkanal für ein überzeugendes Erlebnis sorgen können, indem Sie einen Titel oder eine Beschreibung auf einem Bild einfügen. Auf dieser Seite erfahren Sie mehr.
uuid: 944477e8-0025-4cc7-aa61-6b72f4a245fd
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: b6fdb5a0-5601-4443-a3f4-85cc90c49914
noindex: true
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Textüberlagerung{#text-overlay}

In diesem Abschnitt werden folgende Themen behandelt:

* **Überblick**
* **Verwenden von Textüberlagerung**
* **Voraussetzungen**
* **Verstehen der Eigenschaften von Textüberlagerung**

>[!CAUTION]
>
>Die Funktion **Textüberlagerung** ist nur verfügbar, wenn Sie AEM 6.3 Feature Pack 5 oder AEM 6.4 Feature Pack 3 installiert haben.

## Überblick {#overview}

Textüberlagerung ist eine Funktion in AEM Screens, mit der Sie in einem Sequenzkanal für ein überzeugendes Erlebnis sorgen können, indem Sie einen Titel oder eine Beschreibung auf einem Bild einfügen.

Informationen zum Erstellen einer eigenen benutzerdefinierten Komponente finden Sie unter **Erweitern einer AEM Screens-Komponente**.

In diesem Abschnitt wird nur gezeigt, wie die Poster-Komponente in einem AEM Screens-Projekt als Textüberlagerung in einem Ihrer Sequenz-Kanäle genutzt werden kann.

## Verwenden von Textüberlagerung {#using-text-overlay}

Im folgenden Abschnitt wird die Verwendung von Textüberlagerung in AEM Screens-Projekten beschrieben.

### Voraussetzungen {#prerequisites}

Bevor Sie mit der Implementierung der Funktion beginnen, stellen Sie sicher, dass Sie als Voraussetzung ein Projekt eingerichtet haben. Beispiel:

* Erstellen Sie ein AEM Screens-Projekt (in diesem Beispiel **TextOverlayDemo**)

* Erstellen Sie einen Kanal als **TextSample** im Ordner **Kanäle**

* Fügen Sie Inhalte zu Ihrem Kanal **TextSample** hinzu

Die folgende Abbildung zeigt das Projekt **TextOverlayDemo** mit dem Kanal **TextSample** im Ordner **Kanäle**.

![screen_shot_2018-12-16at75908pm](assets/screen_shot_2018-12-16at75908pm.png)

1. Navigieren Sie zu **TextOverlayDemo** > **Kanäle** > **TextSample** und klicken Sie in der Aktionsleiste auf **Bearbeiten**, um den Editor zu öffnen.

   ![screen_shot_2018-12-16at80017pm](assets/screen_shot_2018-12-16at80017pm.png)

1. Wählen Sie das Bild aus und klicken Sie auf **Konfigurieren** (Schraubenschlüsselsymbol), um das Dialogfeld „Eigenschaften“ zu öffnen.

   ![screen_shot_2018-12-16at80221pm](assets/screen_shot_2018-12-16at80221pm.png)

1. Wählen Sie in der Navigationsleiste des Dialogfelds die Option **Textüberlagerung**, wie in der folgenden Abbildung dargestellt.

   ![screen_shot_2018-12-16at80424pm](assets/screen_shot_2018-12-16at80424pm.png)

### Verstehen der Eigenschaften von Textüberlagerung {#understanding-text-overlay-properties}

Mithilfe der Eigenschaften für Textüberlagerung können Sie einer beliebigen Komponente in einem Screens-Projekt Text hinzufügen. Im folgenden Abschnitt erhalten Sie eine Übersicht über die Eigenschaften, die in der Textüberlagerung verfügbar sind:

![text](assets/text.gif)

Sie können dem Textfeld einen Text hinzufügen und typografische Hervorhebungen wie Fett, Kursiv, Unterstrichen usw. anwenden.

**Farbvariante** Mit dieser Option kann der Text entweder dunkel (Text in schwarzer Farbe) oder hell (Text in weißer Farbe) dargestellt werden.

**Größe und Anordnung** Mit dieser Option kann der Benutzer den Text horizontal oder vertikal ausrichten oder zusätzlich präzise Tools für die Textausrichtung verwenden.

>[!NOTE]
>
>Für einen richtigen Einsatz der Tools müssen Sie die gewünschte Position in Pixel mit „px“ als Suffix angeben (z. B. „200px“). Das Ergebnis dieses Ausdrucks ist 200 Pixel vom Anfangspunkt entfernt.

