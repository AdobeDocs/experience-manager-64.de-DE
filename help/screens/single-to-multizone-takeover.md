---
title: Einzel- bis Mehrzonenübernahme
seo-title: Einzige Zone zur Übernahme durch Multizone
description: 'Folgen Sie dieser Seite, um mehr über die Einzel-/Mehrzonenübernahme in einem AEM Screens-Projekt zu erfahren.  '
seo-description: 'Folgen Sie dieser Seite, um mehr über die Einzel-/Mehrzonenübernahme in einem AEM Screens-Projekt zu erfahren.    '
translation-type: tm+mt
source-git-commit: 4b2c0f3a1ef8759eb3182b93cffa09c4afc23b6a

---


# Einzel- bis Mehrzonenübernahme {#single-zoneto-multizone}

## Nutzungsszenario – Beschreibung {#use-case-description}

In diesem Abschnitt wird ein Verwendungsfallbeispiel beschrieben, in dem hervorgehoben wird, wie ein Kanal mit einem Mehrzonenlayout eingerichtet wird, der mit einem Einzonenlayoutkanal wechselt. Jeder Kanal verfügt über sequenzierende Bild-/Video-Assets.

### Voraussetzungen {#preconditions}

Bevor Sie mit diesem Nutzungsszenario beginnen, sollten Sie sich mit den folgenden Themen vertraut machen:

* **[Erstellen und Verwalten von Kanälen](/help/screens/managing-channels.md)**
* **[Erstellen und Verwalten von Standorten](/help/screens/managing-locations.md)**
* **[Erstellen und Verwalten von Zeitplänen](/help/screens/managing-schedules.md)**
* **[Geräteregistrierung](/help/screens/device-registration.md)**

### Hauptakteure {#primary-actors}

Autoren von Inhalten

## Einrichten des Projekts {#setting-up-the-project}

Gehen Sie wie folgt vor, um ein Projekt einzurichten:

1. Create an AEM Screens Project named as **ZonesDemo**, as shown below.

   >[!NOTE]
   >
   >To learn more about creating and managing projects in AEM Screens, refer to [Creating a Project](/help/screens/creating-a-screens-project.md).

   ![screen_shot_2019-02-21at35809pm](assets/SZtoMZ1.png)

1. **Erstellen eines Sequenzkanals mit einem Bild**

   1. Wählen Sie den Ordner **Kanäle** aus und klicken Sie in der Aktionsleiste auf **Erstellen**, um den Assistenten zum Erstellen eines Kanals zu öffnen.
   1. Select **Sequence Channel** from the wizard and create the channel titled as **FullScreenOne**.

      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ2.png)
   1. Wählen Sie den Kanal aus und klicken Sie in der Aktionsleiste auf &quot; **Bearbeiten** &quot;, um den Editor zu öffnen und ein Bild auf diesen Kanal zu ziehen, wie unten dargestellt.
      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ3.png)

1. **Erstellen eines 2X2-Kanals mit vier Bildern**

   1. Wählen Sie den Ordner **Kanäle** aus und klicken Sie in der Aktionsleiste auf **Erstellen**, um den Assistenten zum Erstellen eines Kanals zu öffnen.

   1. Select **2X2 Split Screen Channel** template from the wizard and create the channel titled as **TwobyTwoChannel**.

      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ4.png)
   1. Wählen Sie den Kanal aus und klicken Sie in der Aktionsleiste auf &quot; **Bearbeiten** &quot;, um den Editor zu öffnen und vier Bilder (vier verschiedene Bereiche) wie unten dargestellt zu diesem Kanal zu ziehen.
      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ5.png)

1. **Erstellen eines 1X2-Split-Screen-Kanals mit zwei Bildern**

   1. Wählen Sie den Ordner **Kanäle** aus und klicken Sie in der Aktionsleiste auf **Erstellen**, um den Assistenten zum Erstellen eines Kanals zu öffnen.

   1. Select **1X2 Split Screen Channel** template from the wizard and create the channel titled as **OnebyTwoChannel**.

      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ6.png)
   1. Wählen Sie den Kanal aus und klicken Sie in der Aktionsleiste auf &quot; **Bearbeiten** &quot;, um den Editor zu öffnen und zwei Bilder (zwei verschiedene Bereiche) wie unten dargestellt zu diesem Kanal zu ziehen.
      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ7.png)

1. **Erstellen eines Kanals mit einem Vollbildvideo**

   1. Wählen Sie den Ordner **Kanäle** aus und klicken Sie in der Aktionsleiste auf **Erstellen**, um den Assistenten zum Erstellen eines Kanals zu öffnen.

   1. Select **Sequence Channel** template from the wizard and create the channel titled as **FullScreensVideo**.

      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ8.png)
   1. Wählen Sie den Kanal aus und klicken Sie in der Aktionsleiste auf &quot; **Bearbeiten** &quot;, um den Editor zu öffnen, ziehen Sie die Videokomponente auf den Kanal und fügen Sie dann das gewünschte Video hinzu, wie unten dargestellt.
      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ9.png)

## Einrichten des Übernahmekanals zum Übergang von einer Einzel- zu einer Mehrzone {#takeover-channel-setup}

1. **Bearbeiten des Einzonenkanals für die Übernahme mehrerer Zonen**

   1. Wählen Sie den in Schritt 1 erstellten Kanal (**FullScreenOne)** aus.
   1. Klicken Sie in der Aktionsleiste auf **Bearbeiten**, um den Editor zu öffnen. Ziehen Sie zwei Kanalkomponenten und eine Videokomponente in den Editor.
   ![screen_shot_2019-02-21at40516pm](assets/SZtoMZ10.png)

1. **Ausfüllen der zu FullScreenOne hinzugefügten Komponenten**

   1. Wählen Sie die erste Kanalkomponente aus dem Editor von **FullScreenOne** und klicken Sie auf **Konfigurieren** , um auf den in den vorherigen Schritten erstellten Kanal zu zeigen. Fügen Sie den Pfad zum Kanal im **Kanalpfad** zu den Kanalkomponenten hinzu und ziehen Sie das Video per Drag &amp; Drop in die Videokomponente, wie unten dargestellt.
   ![screen_shot_2019-02-21at40516pm](assets/SZ_MZvideo1.gif)

1. **Einstellen der Zeitdauer für die Kanäle während des Übergangs**

   >[!NOTE]
   >
   >Standardmäßig werden die Assets alle 8 Sekunden aktualisiert. Wenn Sie jedoch möchten, dass die Assets nach einer bestimmten Zeitdauer übergehen, führen Sie den folgenden Schritt aus.

   1. Wählen Sie die zweite Kanalkomponente im Editor von **FullScreenOne** aus und klicken Sie auf **Einstellungen** , um die Zeitdauer für diesen Kanal zu konfigurieren. Richten Sie die Zeitdauer für Kanal 2 wie unten dargestellt ein.
In diesem Beispiel wird die Zeit auf 3 Sekunden eingestellt.
   ![screen_shot_2019-02-21at40516pm](assets/SZ_MZvideo2.gif)

## Vorschau des Ergebnisses {#previewing-result}

Sie können im Editor auf &quot; **Vorschau** &quot;klicken und prüfen, wie die Assets von einer Einzel- zur Multizone wechseln.

![](assets/SZ_MZvideo3.gif)
