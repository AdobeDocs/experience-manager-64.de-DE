---
title: Zeitplanung auf der Asset-Ebene
seo-title: Zeitplanung auf der Asset-Ebene
description: 'Auf dieser Seite erfahren Sie, wie Sie ein bestimmtes Asset in einem Kanal für einen geplanten Zeitraum in der lokalen Zeitzone des Players aktivieren können. '
seo-description: 'Auf dieser Seite erfahren Sie, wie Sie ein bestimmtes Asset in einem Kanal für einen geplanten Zeitraum in der lokalen Zeitzone des Players aktivieren können. '
uuid: b79d521b-19d4-47c8-a41a-148d7bbf6ac9
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: authoring
discoiquuid: da25cdc7-c814-493e-8d8e-b6191fee2831
noindex: true
translation-type: tm+mt
source-git-commit: 4b2c0f3a1ef8759eb3182b93cffa09c4afc23b6a

---


# Zeitplanung auf der Asset-Ebene {#asset-level-scheduling}

In diesem Abschnitt wird die Zeitplanung auf der Asset-Ebene für die in Kanälen verwendeten Assets beschrieben.

In diesem Abschnitt werden die folgenden Themen behandelt:

* Überblick
* Zeitplanung auf der Asset-Ebene
* Umgang mit sich wiederholenden Assets
* Multi-Asset-Zeitplanung

>[!CAUTION]
>
>Diese AEM Screens-Funktion ist nur verfügbar, wenn Sie AEM 6.3 Feature Pack 3 oder AEM 6.4 Screens Feature Pack 1 installiert haben.
>
>Wenden Sie sich an den Adobe-Support, um Zugriff auf dieses Feature Pack zu erhalten. Wenn Sie die entsprechenden Berechtigungen erhalten haben, können Sie es von Package Share herunterladen.

## Überblick {#overview}

Mit der ***Zeitplanung auf der Asset-Ebene*** können Sie ein bestimmtes Asset in einem Kanal für einen geplanten Zeitraum in der lokalen Zeitzone des Players aktivieren. Diese Funktion ist für Bilder, Videos, Übergänge, Seiten und eingebettete Kanäle (dynamisch oder statisch) verfügbar.

*Beispielsweise* soll eine Sonderaktion nur montags und mittwochs während der Happy Hour (14.00 bis 17.00 Uhr) angezeigt werden.

Mit der Funktion können Sie nicht nur Start- und Enddatum sowie -zeit, sondern auch ein Wiederholungsmuster angeben.

## Zeitplanung auf der Asset-Ebene {#using-asset-level-scheduling}

Die Zeitplanung auf der Asset-Ebene erfolgt durch Konfiguration der Registerkarte **Aktivierung** beim Zugriff auf die Eigenschaften eines Assets.

Gehen Sie wie folgt vor, um die Zeitplanung auf der Asset-Ebene durchzuführen:

1. Wählen Sie einen beliebigen Kanal aus und klicken Sie in der Aktionsleiste auf **Bearbeiten**, um im Kanal Inhalte hinzuzufügen oder zu bearbeiten.

   ![screen_shot_2018-04-23at111422am](assets/screen_shot_2018-04-23at111422am.png)

   >[!NOTE]
   >
   >Detaillierte Informationen zum
   >
   >* Erstellen eines Projekts finden Sie unter [Erstellen eines neuen Projekts](creating-a-screens-project.md).
   >* Erstellen von Inhalten und Hinzufügen zu einem Kanal finden Sie unter [Verwalten von Kanälen](managing-channels.md).


1. Klicken Sie auf **Bearbeiten**, um den Kanaleditor zu öffnen und ein Asset auszuwählen, das Sie zeitlich planen möchten.

   ![screen_shot_2018-04-24at90434pm](assets/screen_shot_2018-04-24at90434pm.png)

1. Wählen Sie das Asset aus und klicken Sie oben links auf das Symbol **Konfigurieren**, um die Eigenschaften des Bilds zu öffnen.

   Klicken Sie auf die Registerkarte **Aktivierung**.

   ![screen_shot_2018-04-23at112348am](assets/screen_shot_2018-04-23at112348am.png)

1. You can specify the date from the date picker from the **Active from** and **Active until** fields.

   If you select the** Active from** and **Active until** date and time, the asset will display and loop only between that start date/time and end date/time respectively.

   ![screen_shot_2018-04-23at113545am](assets/screen_shot_2018-04-23at113545am.png)

## Umgang mit sich wiederholenden Assets {#handling-recurrence-in-assets}

Sie können eine Wiederholung von Assets Ihren Anforderungen entsprechend in bestimmten Intervallen auf Tages-, Wochen- oder Monatsbasis planen.

Angenommen, Sie möchten ein Bild nur freitags von 13.00 bis 22.00 Uhr anzeigen. Auf der Registerkarte „Aktivierung“ können Sie das gewünschte Wiederholungsintervall für Ihr Asset festlegen.

### Hinzufügen eines wiederkehrenden Ereignisses für Ihr Asset {#adding-a-recurring-event-for-your-asset}

1. Wählen Sie das Asset aus und klicken Sie auf das Symbol **Konfigurieren**, um das Dialogfeld „Eigenschaften“ zu öffnen.
1. Nach Eingabe von Startdatum/Startzeit und Enddatum/Endzeit können Sie einen Cron-Ausdruck oder eine natürliche Textversion verwenden, um Ihren Wiederholungsplan anzugeben.

   Sie können im Web nach einem kostenlosen Cron-Ausdrucksgenerator suchen und den Cron-Ausdruck dann kopieren und in den **Zeitplan** einfügen. Ihr Asset wird im jeweiligen Tages- und Uhrzeitintervall angezeigt.

   *Alternativ* können Sie anstelle des Cron-Ausdrucks auch die natürliche Textversion verwenden, z. B. *nach 6:00 Uhr und vor 18:00 Uhr am Freitag*, um Ihre Aufgabe durchzuführen. Geben Sie den Text in den **Zeitplan** ein, um das Asset anzuzeigen.

## Multi-Asset-Zeitplanung {#multi-asset-scheduling}

>[!CAUTION]
>
>Die Funktion **Multi-Asset-Zeitplanung** ist nur verfügbar, wenn Sie AEM 6.3 Feature Pack 5 oder AEM 6.4 Feature Pack 3 installiert haben.

Die ***Zeitplanung für mehrere Assets*** ermöglicht es dem Benutzer, mehrere Assets auszuwählen und einen Wiedergabezeitplan auf alle ausgewählten Assets anzuwenden.

### Voraussetzungen {#prerequisites}

Um die Multi-Asset-Zeitplanung zu verwenden, erstellen Sie ein AEM Screens-Projekt mit einem Sequenzkanal. Im folgenden Anwendungsbeispiel wird die Implementierung der Funktion veranschaulicht:

* Erstellen Sie ein AEM Screens-Projekt mit dem Titel **MultiAssetDemo**
* Erstellen Sie einen Kanal mit der Bezeichnung **MultiAssetChannel** und fügen Sie dem Kanal Inhalt hinzu, wie in der folgenden Abbildung dargestellt

![screen_shot_2018-12-21at70128am](assets/screen_shot_2018-12-21at70128am.png)

Gehen Sie wie folgt vor, um mehrere Assets auszuwählen und ihre Anzeige in einem AEM Screens-Projekt zu planen:

1. Wählen Sie **MultiAssetChannel** aus und klicken Sie in der Aktionsleiste auf **Bearbeiten**, um den Editor zu öffnen.

   ![screen_shot_2018-12-21at70313am](assets/screen_shot_2018-12-21at70313am.png)

1. Wählen Sie im Editor mehrere Assets aus und klicken Sie auf **Aktivierung bearbeiten** (Symbol oben links).

   ![screen_shot_2018-12-21at70550am](assets/screen_shot_2018-12-21at70550am.png)

1. Select the date and time in **Active from** and **Active until **from the **Component Activation** dialog box. Klicken Sie auf das Häkchen, nachdem Sie die Zeitpläne ausgewählt haben.

   ![screen_shot_2018-12-17at20337pm](assets/screen_shot_2018-12-17at20337pm.png)

1. Klicken Sie auf „Aktualisieren“, um die Assets zu überprüfen, auf die der Multi-Asset-Plan angewendet wird.

   >[!NOTE]
   >
   >Das Zeitplansymbol wird bei Assets, die über Multi-Asset-Zeitplanungen verfügen, oben rechts sichtbar.

   ![screen_shot_2018-12-21at70722am](assets/screen_shot_2018-12-21at70722am.png)

