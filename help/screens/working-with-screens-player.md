---
title: Arbeiten mit dem AEM Screens-Player
seo-title: Arbeiten mit dem AEM Screens-Player
description: Auf dieser Seite erhalten Sie Informationen zum AEM Screens-Player. Hier werden auch die Administrator-Benutzeroberfläche und der Kanalschalter erklärt.
seo-description: Auf dieser Seite erhalten Sie Informationen zum AEM Screens-Player. Hier werden auch die Administrator-Benutzeroberfläche und der Kanalschalter erklärt.
uuid: 93e113ea-fbef-4757-982b-b7dc52fc76a7
contentOwner: jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: authoring
discoiquuid: 4ad51b5e-c628-4440-9f2e-41d17cb10bc3
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Arbeiten mit dem AEM Screens-Player{#working-with-aem-screens-player}

Im AEM Screens-Player können Sie den Inhalt für einen Kanal und andere Einstellungen verwalten.

>[!NOTE]
>
>Drücken Sie ***Ctrl + Befehl + F***, um den Vollbildmodus für AEM Screens-Player unter OS X zu beenden.

Wenn Sie einen Kanal einer Anzeige zuweisen, wird im AEM Screens-Player der Inhalt angezeigt. Sie können die Einstellungen für den Player über die Voreinstellungen für die Administrator-Benutzeroberfläche (im Dashboard) oder im Player selbst konfigurieren.

## Verwenden des Geräte-Dashboards    {#using-the-device-dashboard}

Sie können die Voreinstellungen für Ihr Gerät im Geräte-Dashboard konfigurieren, auf das Sie über Ihre AEM-Autoreninstanz zugreifen können.

1. Navigieren Sie ausgehend von Ihrem Projekt zum Geräte-Dashboard, z. B. über ***Testprojekt*** > ***Geräte***.

   Wählen Sie in der Aktionsleiste die Optionen **Geräte** und **Geräte-Manager** aus.

   ![chlimage_1-66](assets/chlimage_1-66.png)

1. Klicken Sie auf das Gerät, um das Geräte-Dashboard zu öffnen.

   ![chlimage_1-67](assets/chlimage_1-67.png)

1. Überprüfen Sie das Fenster **VOREINSTELLUNGEN**. Sie können über diese beiden Optionen die **Administrator-Benutzeroberfläche** und den **Kanalschalter** für den Player aktivieren bzw. deaktivieren.

   ![chlimage_1-68](assets/chlimage_1-68.png)

### Die Administrator-Benutzeroberfläche {#the-admin-ui}

Durch die Aktivierung der **Administrator-Benutzeroberfläche** im Fenster „Voreinstellungen“ kann der Benutzer die Administratoreinstellungen vom Screens-Player aus öffnen. Wenn Sie diese Option im Geräte-Dashboard deaktivieren, kann der Benutzer die Administrator-Benutzeroberfläche nicht im Player öffnen.

Um die Administrator-Benutzeroberfläche vom Screens-Player aus zu öffnen, halten Sie die linke obere Ecke gedrückt, um das Menü „Admin“ auf Ihrem Touch-optimierten Player zu öffnen, oder verwenden Sie eine Maus. Nachdem die Registrierung abgeschlossen ist und die Kanäle geladen sind, werden Informationen angezeigt.

>[!NOTE]
>
>Sie können jetzt die Betriebszeit der App für den AEM Screens-Player aufrufen, um ihren Zustand zu überprüfen.

![chlimage_1-3](assets/chlimage_1-3.gif)

Wenn Sie im Seitenmenü die Option **Konfiguration** wählen, können Sie auch die Zurücksetzungsoptionen **Firmware**, **Voreinstellungen** oder **Auf Werkseinstellungen** auswählen.

Darüber hinaus können Sie in **Max. Anzahl der beizubehalt. Prot.dateien** die maximale Zahl der Protokolldateien festlegen, die für einen AEM Screens-Player bewahrt werden. Weitere Informationen dazu finden Sie im folgenden Screenshot.

>[!NOTE]
>
>Die Option **Firmware aktualisieren** funktioniert nur in Cordova, z. B. in Android-Playern.

![screen_shot_2018-10-15at101257am](assets/screen_shot_2018-10-15at101257am.png)

Sie können den Cache für Kanäle und Anwendungen über die Administrator-Benutzeroberfläche im AEM Screens-Player löschen.

Wählen Sie **Inhaltscache** in der Seitenleiste, um den Cache zu aktualisieren.

![screen_shot_2018-10-15at105717am](assets/screen_shot_2018-10-15at105717am.png)

### Der Kanalschalter {#the-channel-switcher}

Durch das Aktivieren der Option **Kanalschalter** im Fenster „Voreinstellungen“ kann der Benutzer die Kanalauswahl/-einstellungen vom Screens-Player aus öffnen.

Wenn Sie diese Option im Geräte-Dashboard deaktivieren, kann der Benutzer die Kanal-Voreinstellungen nicht vom Screens-Player aus steuern.

Sie können im Screens-Player die Einstellungen für Ihren Kanal wechseln und steuern.

Um den Kanalschalter vom Player aus aufzurufen, halten Sie die untere linke Ecke gedrückt, um den Kanalschalter zu öffnen. Dort können Sie Kanäle wechseln und auf sonstige Funktionen zugreifen.

![chlimage_1-69](assets/chlimage_1-69.png)

>[!NOTE]
>
>Sie können auch vom Screens-Player aus das Menü „Admin“ und den Kanalschalter für den Player aktivieren oder deaktivieren.
>
>(Siehe *Ändern der Voreinstellungen im AEM Screens-Player* wie im Abschnitt weiter unten beschrieben).

### Verwalten von Voreinstellungen im AEM Screens-Player   {#managing-preferences-from-the-aem-screens-player}

Sie können die Einstellungen für die Administrator-Benutzeroberfläche und den Kanalschalter auch im Player selbst ändern.

Führen Sie folgende Schritte aus, um die Voreinstellungen im Player zu ändern:

1. Halten Sie die linke obere Ecke im inaktiven Kanal gedrückt, um das Administratorfenster zu öffnen.
1. Navigieren Sie im linken Aktionsmenü zu **Konfiguration**.
1. Aktivieren bzw. deaktivieren Sie die Option „Konfiguration“ für die **Administrator-Benutzeroberfläche** oder den **Kanalschalter**.

![screen_shot_2018-10-15at101257am-1](assets/screen_shot_2018-10-15at101257am-1.png)

## Fehlerbehebung beim AEM Screens-Player {#troubleshooting-aem-screens-player}

Im Folgenden finden Sie empfohlene Maßnahmen bei Problemen mit dem AEM Screens-Player (Hard- und Software):

| **Probleme** | **Empfehlungen** |
|---|---|
| Speicher des Players ist voll | Löschen Sie unnötige Dateien. |
| Player hat keine Verbindung zum Netzwerk mehr | Verwenden Sie das Cat-5/Cat-6-Kabel. Bei einer WLAN-Verbindung müssen Sie den Abstand zwischen Router und Player verringern. |
| AEM Screens-Player ist abgestürzt | Es wird empfohlen, eine Watchdog-App zu verwenden, die sicherstellt, dass der AEM Screens-Player stets richtig ausgeführt wird. |
| Einstellungen für AEM Screens-Player nicht mehr vorhanden | Überprüfen Sie die Verbindung zum AEM-Server. |
| AEM Screens-Player startet nach einem Neustart des Players/Systems nicht automatisch | Überprüfen Sie den Startordner oder das Initialisierungsverfahren des Betriebssystems. |
| AEM Screens-Player zeigt falschen/alten Inhalt an | Überprüfen Sie die Netzwerkverbindung. |

### Updates für den AEM Screens-Player {#updates-for-aem-screens-player}

Für den AEM Screens-Player gibt es zwei Arten von Updates:

| **Methode** | **Details** | **Remote** | **Automatisiert** | **Ohne Ausfallzeit** |
|---|---|---|---|---|
| Firmware-Update | Wird per Remote-Befehl auf vorhandene installierte Player angewendet. Nach der Aktualisierung wird der Player mit dem vorhandenen Inhalt automatisch neu geladen. | Ja | Benutzerdefiniert | Fast – 1-3 Sekunden |
| Player-Shell-Aktualisierungen | Dabei handelt es sich um eine neue ausführbare Datei, die im Player bereitgestellt werden kann. Dazu müssen neue Binärdaten remote auf den Player kopiert, der aktuelle Player angehalten und die neue Version gestartet werden. Die vorab geladenen Pakete müssen möglicherweise erneut heruntergeladen werden. | Ja (über Remote-Shell) | Benutzerdefiniert | Nein |

