---
title: Häufig gestellte Fragen zu AEM Screens
seo-title: Häufig gestellte Fragen zu AEM Screens
description: Auf dieser Seite erhalten Sie Antworten auf häufig gestellte Fragen zu AEM Screens-Projekten.
seo-description: Auf dieser Seite erhalten Sie Antworten auf häufig gestellte Fragen zu AEM Screens-Projekten.
uuid: e394b1bd-1e63-4bd1-b669-923b2a298743
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
content-type: reference
topic-tags: troubleshoot
discoiquuid: 558a7c2f-b32e-428e-89f6-123d72ca1108
translation-type: tm+mt
source-git-commit: 9f505017b80fe54e228daea9b248fb0a7db93ca2

---


# Häufig gestellte Fragen zu AEM Screens {#aem-screens-faqs}

Im folgenden Abschnitt finden Sie Antworten auf verschiedene häufig gestellte Fragen zu AEM Screens-Projekten.

## Kanalverwaltung {#channel-management}

### What is the difference between an online and an offline channel? {#what-is-the-difference-between-an-online-and-an-offline-channel}

Ein ***Online-Kanal*** zeigt den aktualisierten Inhalt in der Echtzeitumgebung an, während ein ***Offline-Kanal*** den im Cache gespeicherten Inhalt wiedergibt.

### How do I make a channel online? {#how-do-i-make-a-channel-online}

Wählen Sie den Kanal aus und navigieren Sie in der Aktionsleiste zu den Kanaleigenschaften. Aktivieren Sie **Entwicklermodus (Kanal zwingen, online zu sein)** auf der Registerkarte **Kanal**, um den Kanal online zu schalten.

### What is the use of the Channel Role field? {#what-is-the-use-of-the-channel-role-field}

Die Kanalrolle ist eine Abstraktion des tatsächlichen Kanals, die ausgeführt wird, damit sich der Autor direkt auf das generische Erlebnis konzentrieren kann. Sie können sich die Rolle als eine Art Tag vorstellen, das den Kanal in seinem Kontext (Anzeige oder Zeitplan) eindeutig identifiziert.

### How does actual channel resolution happen? {#how-does-actual-channel-resolution-happen}

Bei *statischen Verweisen* folgt die Auflösung einfach dem angegebenen Pfad.

Bei *dynamischen Verweisen* erfolgt die Auflösung, sobald der Kanal der Anzeige zugewiesen wird (nicht dem Zeitplan). Der Anzeigepfad wird zum Kontext des Kanals und die Auflösung wird wie folgt durchgeführt (höchste zu niedrigster Priorität):

1. Die Anzeige hat einen untergeordneten Knoten, der mit dem Namen des referenzierten Kanals übereinstimmt
1. Die Anzeige verfügt über einen gleichrangigen Knoten, der mit dem Namen des referenzierten Kanals übereinstimmt
1. Der übergeordnete Standort der Anzeige hat einen untergeordneten Knoten, der mit dem Namen des referenzierten Kanals übereinstimmt
1. Der über-übergeordnete Standort der Anzeige hat einen untergeordneten Knoten, der mit dem Namen des referenzierten Kanals übereinstimmt

Und so weiter, bis Sie den Standortordner erreichen und dort anhalten (Sie können also nicht auf einen Kanal verweisen, der sich zum Beispiel im Kanalordner befindet, sondern nur auf Kanäle in der Unterstruktur der Standorte)

## Geräteregistrierung {#device-registration}

### Wenn ich Endpunkte wie z.B. Anfragen nach Geräten beim Einstieg und bei der Registrierung feststelle, kann ich eine große Anzahl von Geräten schreiben und diese Geräte registrieren. Ist es möglich, diese Anfragen zu schützen und fest mit dem WLAN einer Zweigstelle zu verknüpfen? {#if-i-discover-endpoints-such-as-requests-for-device-onboarding-and-registration-i-can-script-a-large-number-of-devices-and-register-these-devices-besides-locking-this-to-a-branch-wi-fi-is-it-possible-to-secure-these-requests}

Derzeit ist eine Registrierung nur in der Autoreninstanz möglich. Obwohl der Registrierungsdienst nicht authentifiziert ist, erstellt er in AEM nur ein ausstehendes Gerät, das jedoch weder registriert noch einer Anzeige zugewiesen wird.

Um ein Gerät zu registrieren (d. h. in AEM einen Benutzer für das Gerät zu erstellen), müssen Sie sich bei AEM authentifizieren und derzeit manuell den Registrierungsassistenten nutzen, um die Registrierung abzuschließen. Theoretisch kann ein böswilliger Benutzer mehrere ausstehende Geräte erstellen, ohne Anmeldung in AEM jedoch keines von ihnen registrieren.

### Is there a way to transform HTTP GET requests into HTTP POST with some form of authentication? {#is-there-a-way-to-transform-http-get-requests-into-http-post-with-some-form-of-authentication}

Die Registrierungsanfrage ist eine POST-Anfrage.

Es wird empfohlen, die Geräte-ID aus der Sitzung abzurufen, anstatt sie als Parameter zu übernehmen. Dadurch werden die Server-Protokolle, der Browsercache usw. bereinigt. Es handelt sich dabei derzeit nicht um ein Sicherheitsproblem. Beachten Sie, dass GET semantisch verwendet wird, wenn keine Statusänderung auf dem Server erfolgt, und POST zum Einsatz kommt, wenn eine Statusänderung erfolgt.

### Gibt es eine Möglichkeit, eine Geräteregistrierungsanforderung abzulehnen?

Sie können Registrierungsanfragen nicht ablehnen. Stattdessen sollten Registrierungsanfragen nach einem Time-out ablaufen, das sich in der Adobe Experience Manager-Web-Konsole einrichten lässt.

Standardmäßig ist dieser Wert auf einen Tag festgelegt und wird in einem Arbeitsspeicher-Cache gespeichert.

## Geräteüberwachung und Statusberichte {#device-monitoring-and-health-reports}

### How do I troubleshoot, if my AEM Screens player shows blank screen? {#how-do-i-troubleshoot-if-my-aem-screens-player-shows-blank-screen}

Prüfen Sie folgende Möglichkeiten, um Probleme mit einem leeren Bildschirm zu beheben:

* AEM kann die Offline-Inhalte nicht im Push-Verfahren übertragen
* Der Kanal weist keinen Inhalt auf
* Keines der Assets soll gerade angezeigt werden

### What do I do if AEM Screens player cannot register and its state is displayed as Failure? {#what-do-i-do-if-aem-screens-player-cannot-register-and-its-state-is-displayed-as-failure}

Sie müssen die Option „Apache Sling Referrer Filter Allow Empty“ aktivieren. Dies ist erforderlich, um eine optimale Funktionsweise des Steuerungsprotokolls zwischen dem AEM Screens-Player und dem AEM Screens-Server zu ermöglichen.

1. Navigieren Sie zur **Konfiguration der Adobe Experience Manager-Web-Konsole**.
1. Aktivieren Sie die Option „allow.empty“.
1. Klicken Sie auf **Speichern**.

### How to troubleshoot if while registering an AEM Screens player, device shows FAILURE and the console logs display ENAME_NOT_FOUND error? {#how-to-troubleshoot-if-while-registering-an-aem-screens-player-device-shows-failure-and-the-console-logs-display-ename-not-found-error}

Das Problem kann auftreten, wenn der Player das DNS des AEM Screens-Servers nicht finden kann. Sie können versuchen, eine Verbindung über die IP-Adresse herzustellen. Um die IP des Servers abzurufen, verwenden Sie *arp &lt;Server-DNS-Name>*.

### Empfiehlt AMS die Implementierung eines Android-Watchdog auf allen Geräten? Ist das Watchdog-Plug-in (Cordova) Teil des APK? {#does-ams-recommend-implementing-an-android-watchdog-on-all-devices-is-the-watchdog-cordova-plugin-included-as-part-of-the-apk}

Ein plattformübergreifender Android-Watchdog, der reine Android-APIs nutzt, ist bereits Bestandteil des APK. Es ist keine zusätzliche Software erforderlich, aber je nach verwendetem Gerät müssen Sie das APK neu signieren, um Systemberechtigungen für einen vollständigen Betriebszyklus zu erhalten (Powermanager-API). Falls es nicht mit den Herstellerschlüsseln neu signiert wird, wird das APK beendet und die Anwendung neu gestartet, jedoch ohne Betriebszyklus.

Weitere Informationen zur Implementierung des Android-Players finden Sie unter [**Implementieren des Android-Players **](implementing-android-player.md).

### What third-party remote monitoring and alerting tools (software) does Adobe/AMS recommend for monitoring each device?  {#what-third-party-remote-monitoring-and-alerting-tools-software-does-adobe-ams-recommend-for-monitoring-each-device}

Je nachdem, welches Ergebnis Sie von der Überwachung und den Warnmeldungen wünschen, benachrichtigt Sie der AEM Screens-Benachrichtigungsdienst, wenn ein Gerät länger nicht mehr gepingt hat. Geeignete Tools von Drittanbietern hängen vom jeweiligen Betriebssystem, seinen Funktionen und den spezifischen Anforderungen des Kunden ab.

Wenn Sie weitere Informationen dazu benötigen, wie Sie Geräteaktivität überwachen können, konsultieren Sie [**AEM Screens-Benachrichtigungsdienst **](screens-notifications-service.md).

### Sind die Geräte mit Smart Sync unter Verwendung der Topologie des Veröffentlichungsgeräts für Snapshots und Herzschlagfunktionen weiterhin direkt mit der Autoreninstanz verbunden?

Nein, die Geräte sind nicht direkt mit dem Autor verbunden. Sie melden die Instanzen im Veröffentlichungsmodus und der Autor fragt die Instanzen im Veröffentlichungsmodus nach Updates ab.

## AEM Screens-Player {#aem-screens-player}

### How to Install ChromeOS player as Chrome Browser Plugin? {#how-to-install-chromeos-player-as-chrome-browser-plugin}

Im Entwicklermodus kann der Chrome OS-Player als Chrome-Browser-Plug-in installiert werden, ohne dass ein echtes Chrome-Player-Gerät erforderlich ist. Gehen Sie zur Installation wie folgt vor:

1. Klicken Sie [hier](https://download.macromedia.com/screens/), um den neuesten Chrome-Player herunterzuladen.
1. Entpacken Sie die Datei und speichern Sie sie auf der Festplatte.
1. Öffnen Sie den Chrome-Browser, klicken Sie oben rechts auf das Menü mit den 3 Punkten und wählen Sie **Weitere Tools** > **Erweiterungen** aus oder navigieren Sie direkt zu ***chrome://extensions***.
1. Aktivieren Sie oben rechts den **Entwicklermodus**.
1. Klicken Sie oben links auf „Entpackte Erweiterung laden“ und laden Sie den entpackten Chrome-Player.
1. Überprüfen Sie, ob in der Liste der Erweiterungen das Plug-in **AEM Screens Chrome Player** aufgeführt wird.
1. Öffnen Sie eine neue Registerkarte und klicken Sie oben links auf das Symbol **Apps** oder navigieren Sie direkt zu ***chrome://apps***.
1. Klicken Sie auf das Plug-in **AEM Screens**, um den Chrome-Player zu starten. Standardmäßig wird der Player im Vollbildmodus gestartet. Drücken Sie **Esc**, um den Vollbildmodus zu beenden.

### How to troubleshoot if Screens player is unable to authenticate through publish instance with custom error handler? {#how-to-troubleshoot-if-screens-player-is-unable-to-authenticate-through-publish-instance-with-custom-error-handler}

Wenn der AEM Screens-Player beim Starten einen 404-Fehler erhält, stellt er eine Anfrage an ***/content/screens/svc.ping.json***. Der Player initiiert eine Authentifizierungsanforderung, um sich bei der Veröffentlichungsinstanz zu authentifizieren. Wenn es in der Veröffentlichungsinstanz einen benutzerdefinierten Fehler-Handler gibt, sorgen Sie dafür, dass Sie in ***/content/screens/svc.ping.json*** den 404-Status-Code für einen anonymen Benutzer zurückgeben.

### Wie kann der Gerätebildschirm in einem Android Player aktiviert bleiben?

Führen Sie folgende Schritte durch, um „Stay Awake“ in einem beliebigen Android-Player zu aktivieren:

1. Navigate to Android player settings -> **About**
1. Tippen Sie 7-mal auf die Build-Nummer, um Entwickleroptionen in den Einstellungen zu aktivieren.
1. Navigieren Sie zu den **Entwickleroptionen**.
1. Aktivieren Sie **Stay Awake**.

### Wenn eine Aktualisierung von AEM gesendet wird und der Player offline ist, gibt es einen Wiederholungsmechanismus, der prüft, ob das Gerät wieder online ist, um den aktualisierten Inhalt bereitzustellen? Wie lange versucht es auch?

Beim nächsten Ping vom Gerät, das eingeht, wird eine letzte Bearbeitungszeit angezeigt, die neuer ist als die, die es hat, und dieser neue Inhalt wird heruntergeladen.
Es wird ewig versuchen, bis ein Ping erfolgreich ist.

### Verwenden von Assets {#using-assets}

### Wie können Videos in einem AEM Screens-Kanal verwendet werden, der größer als 2 GB ist? {#how-to-use-videos-in-an-aem-screens-channel-larger-than-gb}

Standardmäßig können Sie mit der AEM Assets Touch-Benutzeroberfläche keine Assets hochladen, die aufgrund einer Dateigrößenbeschränkung in einem AEM Screens-Kanal größer als 2 GB sind. Sie können diese Beschränkung aber umgehen, indem Sie CRXDE Lite aufrufen und im Verzeichnis /apps  einen Knoten erstellen.

Detaillierte Informationen zum Konfigurieren einer höheren Dateigrößenbeschränkung (z. B. 30 GB) im */Apps* -Ordner finden Sie unter *Konfiguration zum Hochladen von Video-Assets, die größer als 2 GB* sind, unter [Verwalten von Video-Assets](/help/assets/managing-video-assets.md).

### Allgemeine Tipps zur Problembehebung {#general-troubleshooting}

### Wie kann ich Livefyre deaktivieren, um Fehler bei A/P-Bildschirmen zu vermeiden?

So deaktivieren Sie Livefyre, um Protokollfehler zu vermeiden:

**Deaktivieren des Livefyre-Bundles:**

1. Navigieren Sie zu `http://<host>:<port>/system/console/bundles`
1. Search for the AEM Livefyre bundle:  *com.adobe.cq.social.cq-social-livefyre*
1. Klicken Sie auf **Anhalten**.

**Deaktivieren des Livefyre-Pollers:**

1. Navigieren Sie in CRXDE Lite zu */etc/importing/polling/livefyre-oller/jcr:content*
1. Fügen Sie eine neue aktivierte Eigenschaft vom Typ Boolesch hinzu
1. Setzen Sie die **aktivierte Eigenschaft** auf **false**
