---
title: Erstellen und Verwalten von Anzeigen
seo-title: Verwalten von Anzeigen
description: Folgen Sie dieser Seite, um sich zu informieren, wie eine neue Anzeige bzw. eine neue Gerätekonfiguration erstellt wird. Außerdem können Sie sich über das Anzeigen-Dashboard informieren.
seo-description: Folgen Sie dieser Seite, um sich zu informieren, wie eine neue Anzeige bzw. eine neue Gerätekonfiguration erstellt wird. Außerdem können Sie sich über das Anzeigen-Dashboard informieren.
uuid: dfde0740-5c8b-4e6c-bc83-bf8fbb31a16a
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: authoring
discoiquuid: f8e2e7a3-f3a1-4c35-b055-166752c3fb86
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Erstellen und Verwalten von Anzeigen{#creating-and-managing-displays}

Eine Anzeige ist eine virtuelle Gruppierung von Bildschirmen, die normalerweise nebeneinander angeordnet sind. Die Installation einer Anzeige ist in der Regel permanent. Dies ist das Objekt, mit dem Inhaltsautoren arbeiten und das sie immer als logische und nicht als physische Anzeige bezeichnen.

Nachdem Sie einen Standort erstellt haben, müssen Sie eine neue Anzeige für Ihren Standort erstellen.

Auf dieser Seite wird gezeigt, wie Anzeigen für Screens erstellt und verwaltet werden.

**Voraussetzungen**:

* [Konfigurieren und Bereitstellen von Screens](configuring-screens-introduction.md)
* [Erstellen und Verwalten von Screens-Projekten](creating-a-screens-project.md)
* [Erstellen und Verwalten von Kanälen](managing-channels.md)
* [Erstellen und Verwalten von Standorten](managing-locations.md)

## Erstellen einer neuen Anzeige {#creating-a-new-display}

>[!NOTE]
>
>Sie müssen einen Standort erstellen, bevor Sie eine Anzeige erstellen können. Weitere Informationen zum Erstellen eines Standorts finden Sie unter [Erstellen und Verwalten von Standorten](managing-locations.md).

Um eine neue Anzeige an Ihrem Standort zu erstellen, gehen Sie wie folgt vor:

1. Navigieren Sie zum entsprechenden Ort, z. B. (http://localhost:4502/screens.html/content/screens/TestProject).
1. Wählen Sie Ihren Standortordner aus und tippen/klicken Sie neben dem Pluszeichen in der Aktionsleiste auf **Erstellen**. Ein Assistent wird geöffnet.
1. Wählen Sie im Assistenten **Erstellen** die Option **Anzeige** aus und klicken Sie auf **Weiter**.

1. Geben Sie **Name** und **Titel** für Ihren Anzeigeort ein.

1. Wählen Sie auf der Registerkarte **Anzeige** die Details für das Layout aus. Wählen Sie die gewünschte **Auflösung** (z. B. **Full HD**) aus. Außerdem können Sie die Anzahl der Geräte horizontal und vertikal festlegen.

1. Klicken Sie auf **Erstellen**.

Die Anzeige (*StoreDisplay*) wird erstellt und dem Standort (*SanJose*) hinzugefügt.

![display](assets/display.gif)

Nachdem Sie die Anzeige positioniert haben, besteht der nächste Schritt darin, für die Anzeige eine Gerätekonfiguration zu erstellen. Folgen Sie dem nachstehenden Abschnitt, um eine neue Gerätekonfiguration zu erstellen.

>[!NOTE]
>
>**Der nächste Schritt**:
>
>Wenn Sie eine Anzeige für einen Ort erstellen, müssen Sie Ihrer Anzeige einen Kanal zuweisen, um den Inhalt verwenden zu können.
>
>Weitere Informationen zum Zuweisen eines Kanals zur Anzeige finden Sie unter [Zuweisen von Kanälen](channel-assignment.md).

## Erstellen einer neuen Gerätekonfiguration {#creating-a-new-device-config}

Eine Gerätekonfiguration fungiert als Platzhalter für ein digitales Beschilderungsgerät, das noch nicht installiert ist.

Gehen Sie wie folgt vor, um eine neue Gerätekonfiguration zu erstellen:

1. Navigieren Sie zur entsprechenden Anzeige, z. B. http://localhost:4502/screens.html/content/screens/TestProject/locations/newlocation
1. Wählen Sie Ihren Anzeigenordner aus und tippen/klicken Sie in der Aktionsleiste auf **Dashboard anzeigen**.
1. Tippen/klicken Sie in der oberen rechten Ecke des Bedienfelds **Geräte** auf **+ Gerätekonfiguration hinzufügen**.

1. Wählen Sie **Gerätekonfiguration** als die erforderliche Vorlage aus und tippen/klicken Sie auf **Weiter**.

1. Geben Sie die entsprechenden Eigenschaften ein und tippen/klicken Sie auf **Erstellen**.

Die Gerätekonfiguration wird erstellt und der aktuellen Anzeige hinzugefügt. (In der folgenden Demonstration ist *DeviceConfig* die neue Gerätekonfiguration.)

![deviceconfig](assets/deviceconfig.gif)

Nach der Erstellung der Gerätekonfiguration für Ihre Anzeige am Standort besteht der nächste Schritt darin, Ihrer Anzeige einen Kanal zuzuweisen.

>[!NOTE]
>
>Nach der Erstellung der Gerätekonfiguration für Ihre Anzeige am Standort besteht der nächste Schritt darin, Ihrer Anzeige einen Kanal zuzuweisen.
>
>Wie in der folgenden Abbildung gezeigt, wird die Gerätekonfiguration im Bedienfeld **GERÄTE** als nicht zugewiesen angezeigt, wenn der Gerätekonfiguration kein Kanal zugewiesen ist.
>
>Sie sollten Vorkenntnisse im Erstellen und Verwalten von Kanälen haben. Weitere Informationen finden Sie unter [Erstellen und Verwalten von Kanälen](managing-channels.md).

![chlimage_1-9](assets/chlimage_1-9.png)

## Anzeigen-Dashboard {#display-dashboard}

Das Anzeigen-Dashboard bietet verschiedene Bedienfelder zum Verwalten von Anzeigegeräten und Gerätekonfigurationen für Ihr Gerät.

![screen_shot_2018-08-23at42810pm](assets/screen_shot_2018-08-23at42810pm.png)

>[!NOTE]
>
>Sie können die Dashboard-Listen auswählen und Massenaktionen für Elemente auslösen, statt jedes einzelne Element durchzugehen.
>
>Beispielsweise zeigt die folgende Abbildung, wie Sie mehrere Kanäle im Anzeigen-Dashboard auswählen können.

![cqdoc9456](assets/cqdoc9456.gif)

### Bedienfeld „Anzeigeinformationen“ {#display-information-panel}

Im Bedienfeld **ANZEIGEINFORMATIONEN** werden die Anzeigeeigenschaften angezeigt.

Klicken Sie in der oberen rechten Ecke im Bedienfeld „ANZEIGEINFORMATIONEN“ auf (**...**), um die Eigenschaften der Anzeige anzuzeigen und die Anzeige in der Vorschau zu betrachten.

![chlimage_1-10](assets/chlimage_1-10.png)

#### Anzeigen von Eigenschaften {#viewing-properties}

Klicken Sie auf **Eigenschaften**, um die Eigenschaften Ihrer Anzeige anzuzeigen oder zu ändern.

Außerdem können Sie den Ereignis-Timer-Wert für Ihren interaktiven Kanal auf der Registerkarte **Anzeige** in der Eigenschaft „Leerlauf-Zeitüberschreitung“ einstellen. Der Standardwert ist auf *300 Sekunden* eingestellt.

Use **CRXDE Lite**, to access the [***idleTimeout ***](http://localhost:4502/crx/de/index.jsp#/content/screens/we-retail/locations/demo/flagship/single/jcr%3Acontent/channels)property.

![chlimage_1-1](assets/chlimage_1-1.gif)

### Bedienfeld „Zugewiesene Kanäle“ {#assigned-channels-panel}

Das Bedienfeld **ZUGEWIESENE KANÄLE** zeigt die zugewiesenen Kanäle des Geräts an.

![chlimage_1-11](assets/chlimage_1-11.png)

### Bedienfeld „Geräte“ {#devices-panel}

Das Bedienfeld **GERÄTE** bietet Informationen zu den Gerätekonfigurationen.

Klicken Sie in der oberen rechten Ecke des Bedienfelds „GERÄTE“ auf (**...**), um Gerätekonfigurationen hinzuzufügen und Geräte zu aktualisieren.

![chlimage_1-12](assets/chlimage_1-12.png)

Außerdem können Sie auf die Gerätekonfiguration klicken, um Eigenschaften anzuzeigen, ein Gerät zuzuweisen oder ein Gerät komplett zu löschen.

![chlimage_1-13](assets/chlimage_1-13.png)

#### Die nächsten Schritte {#the-next-steps}

Nachdem Sie eine Anzeige für Ihren Standort erstellt haben, müssen Sie Ihrer Anzeige einen Kanal zuweisen.

Weitere Informationen finden Sie unter [Zuweisen von Kanälen](channel-assignment.md).
