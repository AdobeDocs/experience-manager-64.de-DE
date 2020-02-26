---
title: Konfiguration der Videowiedergabe und Problembehebung
seo-title: Beheben von Videoproblemen
description: null
seo-description: Auf dieser Seite erfahren Sie, wie Sie Videoprobleme beheben. Wenn Sie ein Video zu DAM hochladen und zu Ihrem Kanal hinzufügen, kann möglicherweise das Problem auftreten, dass das Video im Screens-Player nicht wiedergegeben wird. In diesem Abschnitt werden das Debugging und die Problembehebung für die Videowiedergabe in Ihrem Kanal erläutert.
uuid: 825b2440-5626-40d5-8c93-7689c24474d4
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: troubleshoot
discoiquuid: 65ecc6f1-ba0e-443f-85a1-ac19f9a52c2c
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Konfiguration der Videowiedergabe und Problembehebung{#video-playback-configuration-and-troubleshooting}

Wenn Sie ein Video zu DAM hochladen und zu Ihrem Kanal hinzufügen, kann möglicherweise das Problem auftreten, dass das Video im Screens-Player nicht wiedergegeben wird.

In den folgenden Abschnitten werden das Debugging und die Problembehebung für die Videowiedergabe in Ihrem Kanal beschrieben.

## DAM-Ausgaben     {#dam-renditions}

Wenn Sie das Video in den Kanal hochgeladen haben, sollte AEM damit beginnen, einige Ausgaben dafür zu erzeugen. Sie können Ihre Videos unter „Assets“ anzeigen.

So zeigen Sie das Video an:

1. Navigate to your video, for example [http://localhost:4502/assets.html/content/dam/we-retail/en/videos](http://localhost:4502/assets.html/content/dam/we-retail/en/videos).
1. Klicken Sie auf das Video. Erweitern Sie das obere linke Menü und klicken Sie auf **Ausgaben**.

Es sollten unterschiedliche Ausgaben vorliegen (ein MP4- oder M4V-Video).

Wenn keine Ausgabe verfügbar ist, überprüfen Sie, ob ffmpeg im Betriebssystem installiert ist, unter dem AEM ausgeführt wird.

>[!CAUTION]
>
>Wenn keine Ausgabe verfügbar ist, überprüfen Sie, ob ffmpeg im Betriebssystem installiert ist, unter dem AEM ausgeführt wird.
>
>Klicken Sie [hier](https://evermeet.cx/ffmpeg/), um ffmpeg zu installieren.

## Video-Assets {#video-assets}

Wenn unter dem Video kein Quellattribut angezeigt wird, wurde das Video möglicherweise nicht transkodiert. Wenn das Video ordnungsgemäß transkodiert wurde, wird es im Dashboard angezeigt (siehe nachfolgende Abbildung).

Vergewissern Sie sich, dass ffmpeg installiert ist, und prüfen Sie die Videoprofile.

![chlimage_1-2](assets/chlimage_1-2.png)

### Prüfen des Videoprofils {#checking-video-profile}

1. Navigate to the [Video Profile](http://localhost:4502/etc/dam/video.html) and click **Upload Test Video**.

   ![chlimage_1-3](assets/chlimage_1-3.png)

1. Laden Sie ein Testvideo hoch und klicken Sie auf **OK **um mit der Transkodierung zu beginnen.

   Falls die Transkodierung fehlschlägt, erweitern Sie die ffmpeg-Ausgabe, um die Fehler in der Konsolenausgabe von ffmpeg zu verstehen.

   ![chlimage_1-4](assets/chlimage_1-4.png)

   Wenn das Video erfolgreich transkodiert wurde, können Sie die transkodierte Datei herunterladen.

   ![chlimage_1-5](assets/chlimage_1-5.png)

   >[!NOTE]
   >
   >Stellen Sie sicher, dass Sie lange genug warten, bis das Video transkodiert wurde (es sollte das Tag „neu“ aufweisen statt „in Bearbeitung“), bevor Sie es zu einem Kanal hinzufügen.

### Testen des Profils mit einer Videokomponente     {#checking-profile-with-a-video-component}

Prüfen Sie die Liste der Profile über die Design-Seite, wenn die Videokomponente nicht korrekt konfiguriert ist.

1. Navigieren Sie zu Ihrem Kanal. Wählen Sie dort den Modus **Design** aus.

   ![chlimage_1-6](assets/chlimage_1-6.png)

1. Wählen Sie das Video aus und öffnen Sie das Dialogfeld **Bearbeiten**. Öffnen Sie die Registerkarte **Profile**.

   Wählen Sie unterschiedliche Profile aus. (Es sollte wenigstens das Profil „Hohe Qualität H.264“ vorhanden sein.)

   ![chlimage_1-7](assets/chlimage_1-7.png)

### Prüfen des Videos im Web-Player {#checking-the-video-in-the-web-player}

Mit dem [Web-Player](http://localhost:4502/content/mobileapps/cq-screens-player/firmware.html/content/screens/we-retail/locations/demo/flagship/single/device0)  können Sie die Wiedergabe in Browsern (Chrome und Safari) testen. Chrome wird auf Android-Geräten genutzt, Safari ist der Browser unter OSX und iOS.

Wenn das Video in Safari nicht läuft, funktioniert es auch nicht bei den OSX- und iOS-Playern. Das liegt wahrscheinlich an einem Kodierungsfehler. Das Video muss also neu kodiert werden.

Führen Sie die folgenden Schritte durch, um mit einem DAM-Workflow FullHD-Ausgaben zu erstellen:

1. Navigate to the [workflow model admin](http://localhost:4502/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models).
1. Wählen Sie das Modell **Screens – Asset aktualisieren** aus.
1. Klicken Sie in der Aktionsleiste auf **Workflow starten**, um das Dialogfeld **Workflow ausführen** zu öffnen.

1. Wählen Sie das Video-Asset in der **Nutzlast** aus.
1. Klicken Sie auf **Ausführen**.

>[!NOTE]
>
>Warten Sie eine Weile, während die Ausgaben erstellt werden. Laden Sie nach einigen Sekunden/Minuten (je nach Videogröße) den Web-Player in Safari neu.

#### Problembehebung für das Flag „Autoplay-Richtlinie“ {#troubleshooting-autoplay-policy-flag}

Falls der AEM Screens-Player das Video zwar abruft, aber nicht anzeigt, müssen Sie eine Problembehebung für das Flag „Autoplay-Richtlinie“ durchführen.

Führen Sie folgende Schritte aus, um das Problem mit dem Flag „Autoplay-Richtlinie“ von Google zu beheben:

1. Navigieren Sie zu ***chrome://flags/#autoplay-policy***
1. Die **Autoplay-Richtlinie** muss von **Standard** in **Keine Benutzergeste erforderlich** geändert werden

1. Starten Sie den Webbrowser neu und aktualisieren Sie den Player

>[!NOTE]
>
>To learn more about the best practices for good user experiences with the new autoplay policies in Chrome, please see documentation for [Autoplay Policy Changes.](https://developers.google.com/web/updates/2017/09/autoplay-policy-changes#webaudio)

### Synchronisieren von Videos über mehrere Player hinweg {#syncing-video-across-multiple-players}

Um Videos synchron auf mehreren Geräten wiederzugeben, sollten Sie die absolute Strategie für die Sequenz nutzen, zu der das Video gehört.

#### Voraussetzungen {#requirements}

* zwei oder mehr identische Player
* im Idealfall ähnliche Hardware
* identische Netzwerktopologie (die Player sind mit einem NTP-Server verbunden, der ihre internen Systemuhren synchronisiert)

#### Einrichten der absoluten Strategie {#setting-up-the-absolute-strategy}

Die absolute Strategie:

* berechnet eine Ankerzeit (Mitternacht des aktuellen Tages)
* berechnet die Dauer der Sequenz (Summe der Dauer aller Elemente)
* berechnet zu jedem beliebigen Zeitpunkt mit der Formel „verbleibende_Sequenzzeit = (aktuelle_Zeit - Ankerzeit) % Sequenzdauer“, welches Element aktuell und als nächstes wiedergegeben werden soll

Führen Sie die folgenden Schritte durch, um eine absolute Strategie einzurichten:

1. Navigieren Sie zu Ihrem Kanalautor und wählen Sie die Sequenzkomponenten wie in der nachfolgenden Abbildung gezeigt aus.
1. Öffnen Sie das Konfigurations-Dialogfeld.
1. Bearbeiten Sie die **Strategie** und fügen Sie „absolut“ hinzu.

![chlimage_1-8](assets/chlimage_1-8.png)

>[!NOTE]
>
>Die Betriebssysteme der Player müssen über dieselbe Uhr verfügen.

**Synchronisieren der Uhren unter OS X** Gehen Sie wie folgt vor, um die Uhren unter OS X zu synchronisieren:

1. Öffnen Sie in jedem OS X-Feld die Einstellungen für **Datum und Uhrzeit**.
1. Aktivieren Sie „Datum und Uhrzeit automatisch festlegen“.
1. Kopieren Sie den Wert 0.pool.ntp.org, 1.pool.ntp.org, 2.pool.ntp.org, 3.pool.ntp.org, time.apple.com in das Dropdown-Feld. Sie können auch einfach den Befehl *sudo ntpdate -u -v 0.pool.ntp.org* ausführen.
1. Starten Sie alle Player (mind. zwei).

Es kann eine Weile dauern, bis die Player eine neue synchronisierte Sequenz beginnen.

