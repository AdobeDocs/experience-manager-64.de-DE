---
title: Kanal-Layout-Editor
seo-title: Kanal-Layout-Editor
description: 'null'
seo-description: 'null'
page-status-flag: never-activated
uuid: 81490abc-58cf-4daa-93d6-d697f7495232
contentOwner: jsyal
discoiquuid: 10beb13e-d8b2-440e-b2b0-d9fc2dafdc26
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Kanal-Layout-Editor{#channel-layout-editor}

Mit dem ***Kanal-Layout-Editor*** können Sie Inhalte für mehrere Bereiche erstellen und verschiedene Assets wie Videos, Bilder und Text verwenden, die sich in einem einzigen Bildschirm kontextbezogen kombinieren lassen. Führen Sie Bilder, Videos und Texte zusammen und erschaffen Sie so ein intuitives und interaktives digitales Erlebnis. 

Abhängig von den Projektanforderungen sind ggf. mehrere Bereiche in einem Kanal erforderlich, die dann zusammen als Einheit bearbeitet werden. Beispiel: eine Produktsequenz mit entsprechendem Social-Media-Feed, die in drei separaten Bereichen in einem Kanal läuft.

## Überblick {#overview}

Beim Erstellen eines Kanals können Sie mithilfe verschiedener Vorlagen Bereiche in Ihrem Kanal erstellen. Sie können je nach Projektanforderungen ein Bild, ein Video oder einen eingebetteten Kanal hinzufügen, um Inhalte zu nutzen.

### Nutzungsszenario – Beschreibung {#use-case-description}

Im Rahmen des folgenden Nutzungsszenarios wird beschrieben, wie mehrere Bereiche für einen Kanal erstellt werden.

1. ***Erstellen eines Screens-Projekts***

   1. Wählen Sie den Adobe Experience Manager-Link (oben links) und dann **Screens** aus. Sie können auch direkt zu folgenden Themen gehen: http://localhost:4502/screens.html/content/screens.
   1. Klicken Sie auf **Erstellen**, um ein neues Screens-Projekt zu erstellen.
   1. Wählen Sie im Assistenten **Screens-Projekt erstellen** die Option **Screens** aus und klicken Sie auf **Weiter**.
   1. Geben Sie **Kanal-Layout-Projekt** als Titel ein und klicken Sie auf **Erstellen**.
   ![ch1](assets/ch1.gif)

1. ***Erstellen eines Kanals***

   1. Navigieren Sie zu **Kanal-Layout-Projekt**.
   1. Klicken Sie in der Aktionsleiste auf **Erstellen**. Ein Assistent wird geöffnet.
   1. Wählen Sie die Option **1x2-Splitscreen-Kanal** aus und klicken Sie auf **Weiter**.
   1. Geben Sie **Horizontal geteilt** als **Titel** ein und klicken Sie auf **Erstellen**.
   ![channelcreation](assets/channelcreation.gif)

1. ***Hinzufügen von Inhalten zum Kanal***

   1. Navigieren Sie zu dem von Ihnen erstellten Projekt **Kanal-Layout-Projekt** und wählen Sie den Kanal aus (**Geteilter Kanal**).
   1. Klicken Sie in der Aktionsleiste auf **Bearbeiten**. Daraufhin wird der Editor für **Geteilter Kanal** geöffnet.
   1. Klicken Sie auf der linken Seite der Aktionsleiste auf das Symbol zum Ein-/Ausblenden des seitlichen Bedienfelds, um die Assets und Komponenten zu öffnen. Wählen Sie die Ihrem Kanal hinzuzufügenden Komponenten per Drag-and-Drop aus.
   ![ch4](assets/ch4.gif)

   >[!NOTE]
   >
   >Als Beispiel werden die beiden folgenden Bilder dem Kanal im Editor hinzugefügt.

   ![screen_shot_2018-02-08at123635pm](assets/screen_shot_2018-02-08at123635pm.png)

1. ***Erstellen eines Standorts***

   1. Navigieren Sie zu dem Standortordner, in dem die Anzeige erstellt werden soll (**Kanal-Layout-Projekt** > **Standorte**).
   1. Klicken Sie in der Aktionsleiste auf **Erstellen**.
   1. Wählen Sie im Assistenten **Erstellen** die Option **Standort** aus und klicken Sie auf **Weiter**.
   1. Geben Sie **San Jose** als **Titel** für Ihren Standort ein.
   1. Klicken Sie auf **Erstellen**.
   ![ch5](assets/ch5.gif)

1. ***Erstellen einer neuen Anzeige***

   1. Navigieren Sie zum Standort, an dem die Anzeige erstellt werden soll (**Acme** > **Standorte** > **San Jose**) und wählen Sie **San Jose** aus.
   1. Klicken Sie in der Aktionsleiste auf **Erstellen**. Wählen Sie im Assistenten **Erstellen** die Option **Anzeige** aus und klicken Sie auf **Weiter**.
   1. Geben Sie **Geteilte Anzeige** als **Titel** für den Anzeigeort ein.
   1. Wählen Sie auf der Registerkarte **Anzeige** die Details für das Layout aus. Wählen Sie unter **Auflösung** die Option **Full HD** aus. Legen Sie für **Anzahl der Geräte horizontal** den Wert „1“ und für **Anzahl der Geräte vertikal** den Wert ****„1“ fest.
   1. Klicken Sie auf **Erstellen**.
   ![ch6](assets/ch6.gif)

1. ***Zuweisen von Kanälen***

   1. Navigieren Sie über **Kanal-Layout-Projekt** > **Standorte** > **San Jose** > **Geteilte Anzeige** zur Anzeige.
   1. Wählen Sie **Geteilte Anzeige** aus und tippen/klicken Sie in der Aktionsleiste auf **Kanal zuweisen**. Als Alternative:
   1. Klicken Sie auf **Dashboard** und wählen Sie oben rechts im Fenster **ZUGEWIESENE KANÄLE UND ZEITPLÄNE** die Option **+ Kanal zuweisen** aus. Daraufhin wird das Dialogfeld **Kanalzuweisung** geöffnet.
   1. Geben Sie **Geteilt** als **Kanalrolle** ein.
   1. Wählen Sie als Vorgehensweise für **Kanal referenzieren** die Option „Pfad“ aus. Wählen Sie im Kanal den Pfad des Kanalordners aus (**Kanal-Layout-Projekt** > **Kanäle** > **Horizontal geteilt**).
   1. Wählen Sie als **Priorität** für den Kanal **1** aus.
   1. Wählen Sie unter **Unterstützte Ereignisse** die Optionen **Erster Ladevorgang** und **Bildschirm bei Untätigkeit** aus.
   1. Klicken Sie auf **Speichern**.
   ![ch7](assets/ch7.gif)

1. ***Registrieren und Zuweisen des Geräts***

   1. Öffnen Sie ein separates Browser-Fenster. Wechseln Sie mithilfe des Webbrowsers zum Screens-Player oder starten Sie die AEM Screens-App.
   1. Wenn Sie das Gerät öffnen, können Sie sehen, dass das Gerät nicht registriert ist. Navigieren Sie im AEM-Dashboard zu **Kanal-Layout-Projekt** > **Geräte**.
   1. Klicken Sie in der Aktionsleiste auf **Geräte-Manager**.
   1. Klicken Sie auf **Geräteregistrierung**. Daraufhin werden die ausstehenden Geräte angezeigt. Wählen Sie das zu registrierende Gerät aus und klicken Sie auf **Gerät registrieren**.
   1. Sie müssen den Code validieren, indem Sie ihn über den Webbrowser oder den AEM Screens-Player überprüfen. Klicken Sie auf **Validieren**, um zum Bildschirm **Geräteregistrierung** zu wechseln.
   1. Geben Sie **NewD** als Titel ein und klicken Sie auf **Registrieren**. Daraufhin wird das Gerät registriert.
   1. Klicken Sie auf **Anzeige zuweisen**, um mit dem nächsten Schritt fortzufahren und das Gerät einer Anzeige zuzuweisen.
   1. Klicken Sie auf „Gerät zuweisen“ und wählen Sie /content/screens/Test_Project/Locations/TestLocation/TestDisplay als Anzeigepfad für Ihren Kanal aus. Klicken Sie auf **Zuweisen**.
   1. Klicken Sie auf **Beenden**, um den Vorgang abzuschließen. Das Gerät ist jetzt zugewiesen.
   ![ch8](assets/ch8.gif)

#### Anzeigen von Inhalten im AEM Screens-Player {#viewing-content-in-aem-screens-player}

Laden Sie den AEM Screens-Player oder verwenden Sie den Webbrowser. Sie werden feststellen, dass die Inhalte für den Kanal im Screens-Player angezeigt werden. Die Inhalte werden als 1x2-Splitscreen-Kanalvorlage angezeigt.

![](do-not-localize/screen_shot_2018-02-08at123648pm.png)

### Folgerung    {#inference}

Wenn Sie einen Kanal mithilfe der verfügbaren Vorlagen erstellen, können Sie Inhalte in verschiedenen Bereichen nutzen und dort anzeigen. Das Beispiel oben bezieht sich auf ein Nutzungsszenario für die 2x2-Vorlage.

Die folgenden Abbildungen zeigen das Layout, das mit verschiedenen Vorlagen erreicht werden kann.
