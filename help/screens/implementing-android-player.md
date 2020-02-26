---
title: Implementieren des Android-Players
seo-title: Implementieren des Android-Players
description: 'Auf dieser Seite erfahren Sie mehr über die Implementierung von Android Watchdog, einer Lösung zur Wiederherstellung des Players nach Abstürzen. '
seo-description: 'Auf dieser Seite erfahren Sie mehr über die Implementierung von Android Watchdog, einer Lösung zur Wiederherstellung des Players nach Abstürzen. '
uuid: 37527a6a-dcc5-4256-abeb-e1f95ff80be4
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: administering
discoiquuid: e6ec1641-4323-4c79-b932-b857feb1df21
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939

---


# Implementieren des Android-Players {#implementing-android-player}

Ein ***Watchdog*** ist eine Lösung zur Wiederherstellung des Players nach Abstürzen. Eine Anwendung muss sich selbst beim Watchdog-Dienst registrieren und dann regelmäßig Nachrichten zur Bestätigung ihrer Aktivität an den Dienst senden. Falls der Watchdog-Dienst innerhalb der geforderten Zeit keine Keep-Alive-Nachricht erhält, versucht der Dienst das Gerät neu zu starten, um eine saubere Wiederherstellung durchzuführen (bei ausreichenden Rechten) oder die Anwendung neu zu starten.

## Implementieren von Android Watchdog {#implementing-android-watchdog}

Aufgrund der Architektur von Android erfordert der Neustart des Geräts, dass die Anwendung über Systemrechte verfügt. Hierzu müssen Sie die apk mithilfe der Signierungsschlüssel des Herstellers signieren. Andernfalls startet Watchdog die Player-Anwendung neu und nicht das Gerät.

### Signieren von Android-apks mithilfe von Herstellerschlüsseln      {#signage-of-android-apks-using-manufacturer-keys}

To access some of the privileged APIs of Android such as *PowerManager* or *HDMIControlServices*, you need to sign the android apk using the manufacturer&#39;s keys.

>[!CAUTION]
>
>Voraussetzungen:
>
>Die Android SDK sollte installiert sein, bevor Sie die folgenden Schritte durchführen.

Gehen Sie wie folgt vor, um die Android-apk mithilfe von Herstellerschlüsseln zu signieren:

1. Laden Sie die apk von Google Play oder von der Seite [AEM Screens-Player-Downloads](https://download.macromedia.com/screens/) herunter
1. Rufen Sie die Plattformschlüssel des Herstellers ab, um eine *pk8*- und eine *pem*-Datei zu erhalten

1. Suchen Sie nach dem apksigner-Tool in Android SDK mithilfe von find ~/Library/Android/sdk/build-tools -name &quot;apksigner&quot;
1. &lt;Pfad> /apksigner sign --key platform.pk8 --cert platform.x509.pem aemscreensplayer.apk
1. Suchen Sie den Pfad zum Zipalign-Tool in Android SDK
1. &lt;Pfad> /zipalign -fv 4 aemscreensplayer.apk aemscreensaligned.apk
1. Installieren Sie ***aemscreensaligned.apk*** mithilfe von adb install auf dem Gerät

## Implementierung von Android Watchdog {#android-watchdog-implementation}

Der Android Watchdog-übergreifende Dienst wird mithilfe von *AlarmManager* als Cordova-Plug-in implementiert.

Das folgende Diagramm zeigt die Implementierung des Watchdog-Diensts:

![chlimage_1-43](assets/chlimage_1-43.png)

**1. Initialisierung** Zum Zeitpunkt der Initialisierung des Cordova-Plug-ins werden die Berechtigungen geprüft, um zu ermitteln, ob wir über Systemrechte und damit über die Berechtigung zum Neustart verfügen. Sind diese beiden Kriterien erfüllt, wird ein Pending-Intent für den Neustart erstellt. Andernfalls wird ein Pending-Intent für den Neustart der Anwendung (basierend auf ihrer Startaktivität) erstellt.

**2. Keep-Alive-Timer** Ein Keep-Alive-Timer wird verwendet, um alle 15 Sekunden ein Ereignis auszulösen. In diesem Fall müssen Sie den vorhandenen Pending-Intent abbrechen (um die App neu zu starten) und einen neuen Pending-Intent für dieselben 60 Sekunden in der Zukunft registrieren (also im Grunde den Neustart verschieben).

>[!NOTE]
>
>In Android wird der *AlarmManager* für die Registrierung von *pendingIntents* verwendet, die auch dann noch ausgeführt werden können, wenn die App abgestürzt ist und die Alarmbereitstellung von API 19 (Kitkat) ungenau ist. Behalten Sie etwas Abstand zwischen dem Intervall des Timers und dem *AlarmManager*-Alarm *pendingIntent* bei.

**3. Anwendungsabsturz** Im Fall eines Absturzes wird der pendingIntent für den Neustart, der beim AlarmManager registriert ist, nicht mehr zurückgesetzt. Daher führt er (je nach den zum Zeitpunkt der Initialisierung des Cordova-Plug-ins verfügbaren Berechtigungen) einen Neustart der App durch.
