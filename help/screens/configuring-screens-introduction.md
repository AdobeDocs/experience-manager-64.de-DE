---
title: Konfigurieren und Bereitstellen von AEM Screens
seo-title: Konfigurieren und Bereitstellen von Screens
description: Der AEM Screens-Player ist für Android, Chrome OS, iOS und Windows verfügbar. Diese Seite beschreibt die Konfiguration und Bereitstellung von AEM Screens und fasst die Hardware-Auswahlrichtlinien für Player-Geräte zusammen.
seo-description: Der AEM Screens-Player ist für Android, Chrome OS, iOS und Windows verfügbar. Diese Seite beschreibt die Konfiguration und Bereitstellung von AEM Screens und fasst die Hardware-Auswahlrichtlinien für Player-Geräte zusammen.
uuid: 8ee5311f-b377-4035-af77-e1391a840745
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: administering
discoiquuid: a94d0891-d75f-482e-8d2a-e0cbf953a9de
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939

---


# Konfigurieren und Bereitstellen von AEM Screens{#configuring-and-deploying-aem-screens}

Diese Seite zeigt, wie Sie die Screens-Player auf Ihren Geräten installieren und konfigurieren, und behandelt die folgenden Themen:

* Installieren des AEM Screens-Players
* Server-Konfiguration
* Richtlinien zur Hardware-Auswahl für das Player-Gerät
* Die nächsten Schritte

## Installieren des AEM Screens-Players {#installing-aem-screens-player}

Der AEM Screens-Player ist für Android, Chrome OS, iOS und Windows verfügbar.

Um einen **AEM Screens-Player** herunterzuladen, rufen Sie die Seite [**AEM 6.4 Player-Downloads **](https://download.macromedia.com/screens/)auf.

>[!NOTE]
>
>Nachdem Sie den aktuellen Player (*.exe*) heruntergeladen haben, führen Sie die Schritte im Player aus, um die Ad-hoc-Installation abzuschließen:
>
>1. Halten Sie die linke obere Ecke gedrückt, um den Admin-Bereich zu öffnen.
>1. Navigieren Sie im linken Aktionsmenü zu **Konfiguration**, geben Sie die Standortadresse der AEM-Instanz unter **Server** ein und klicken Sie auf **Speichern**.
   >
   >
1. Klicken Sie im linken Aktionsmenü auf den Link **Registrierung** und führen Sie die folgenden Schritte aus, um die Geräteregistrierung abzuschließen.
>



### Zusätzliche Ressourcen {#additional-resources}

In den folgenden Themen finden Sie ausführliche Informationen:

* Um Android-Player herunterzuladen, gehen Sie zu **Google Play**. To learn about implementing Android Watchdog, please refer to **[Implementing Android player](implementing-android-player.md)**.

* To implement Chrome OS Player, please refer to [Chrome Management Console](implementing-chrome-os-player.md) for more information.
* To configure AEM Screens Windows player, please refer to [Implementing Windows Player](implementing-windows-player.md).

## Server-Konfiguration {#server-configuration}

>[!NOTE]
>
>**Wichtig**:
>
>Der AEM Screens-Player verwendet kein Site-übergreifendes Anforderungsfälschungs-Token (CSRF-Token). Um einen AEM-Server für den Einsatz von AEM Screens zu konfigurieren, müssen Sie daher den Referrer-Filter überspringen, indem Sie leere Referrer zulassen.

### Voraussetzungen {#prerequisites}

Die folgenden wichtigen Punkte bieten Hilfestellung beim Konfigurieren von AEM-Servern für die Nutzung von AEM Screens:

#### Zulassen von leeren Referrer-Anforderungen {#allow-empty-referrer-requests}

Führen Sie die nachfolgenden Schritte aus, um den Apache Sling Referrer-Filter „Allow Empty“ zu aktivieren. Dies ist erforderlich, um eine optimale Funktionsweise des Steuerungsprotokolls zwischen dem AEM Screens-Player und dem AEM Screens-Server zu ermöglichen.

1. Navigieren Sie zur Konfiguration der Adobe Experience Manager-Web-Konsole über AEM-Instanz > Hammersymbol > **Vorgänge** > **Web-Konsole**.

   ![screen_shot_2019-02-11at15405pm](assets/screen_shot_2019-02-11at15405pm.png)

1. Die **Konfiguration der Adobe Experience Manager-Web-Konsole** wird geöffnet. Suchen Sie nach „sling referrer“.

   Um nach der Eigenschaft „sling referrer“ zu suchen, drücken Sie **Befehl+F** für **Mac** und **Strg+F** für **Windows**.

   ![screen_shot_2019-02-11at15629pm](assets/screen_shot_2019-02-11at15629pm.png)

1. Markieren Sie die Option **Leere erlauben**, wie in der folgenden Abbildung dargestellt.

   ![screen_shot_2018-12-04at22911pm](assets/screen_shot_2018-12-04at22911pm.png)

1. Klicken Sie auf **Speichern**, um den Apache Sling Referrer-Filter „Leere erlauben“ zu aktivieren.

#### Aktivieren der Touch-Benutzeroberfläche für AEM Screens {#enable-touch-ui-for-aem-screens}

AEM Screens erfordert die TOUCH-Benutzeroberfläche und funktioniert nicht mit der KLASSISCHEN Benutzeroberfläche von Adobe Experience Manager (AEM).

1. Navigieren Sie zu *&lt;IhreAutoreninstanz>/system/console/configMgr/com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl*
1. Stellen Sie sicher, dass der **standardmäßige Authoring-Oberflächenmodus** auf **TOUCH** gesetzt ist, wie in der folgenden Abbildung gezeigt.

Alternatively, you can also perform the same setting using*&lt;yourAuthorInstance> *->* tools (hammer icon)* -> **Operations** ->**Web Console** and search for **WCM Authoring UI Mode Service**.

![screen_shot_2018-12-04at22425pm](assets/screen_shot_2018-12-04at22425pm.png)

>[!NOTE]
>
>Sie können die klassische Benutzeroberfläche jederzeit mithilfe der Benutzereinstellungen für bestimmte Benutzer aktivieren.

#### AEM im NOSAMPLECONTENT-Ausführungsmodus {#aem-in-nosamplecontent-runmode}

Beim Ausführen von AEM in einer Produktionsumgebung wird der Ausführungsmodus **NOSAMPLECONTENT** verwendet. Remove the *X-Frame-Options=SAMEORIGIN* header (in the additional response header section) from

[http://localhost:4502/system/console/configMgr/org.apache.sling.engine.impl.SlingMainServlet](http://localhost:4502/system/console/configMgr/org.apache.sling.engine.impl.SlingMainServlet)

Dies ist erforderlich, damit der AEM Screens-Player Online-Kanäle wiedergeben kann.

#### Kennworteinschränkungen {#password-restrictions}

Mit den neuesten Änderungen an ***DeviceServiceImpl*** müssen Sie die Kennworteinschränkungen nicht entfernen.

Sie können ***DeviceServiceImpl*** über den unten stehenden Link konfigurieren, um die Kennworteinschränkungen zu aktivieren, während Sie das Kennwort für die Screens-Gerätebenutzer erstellen:

[http://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.impl.DeviceService](http://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.impl.DeviceService)

Gehen Sie wie folgt vor, um ***DeviceServiceImpl*** zu konfigurieren:

1. Navigieren Sie zur **Konfiguration der Adobe Experience Manager-Web-Konsole** über AEM-Instanz > Hammersymbol > **Vorgänge** > **Web-Konsole**.

1. Die **Konfiguration der Adobe Experience Manager-Web-Konsole** wird geöffnet. Suchen Sie nach „deviceservice“. Um nach der Eigenschaft zu suchen, drücken Sie **Befehl+F** für **Mac** und **Strg+F** für **Windows**.

![screen_shot_2019-02-21at24951pm](assets/screen_shot_2019-02-21at24951pm.png)

#### Dispatcher-Konfiguration {#dispatcher-configuration}

Für **Dispatcher **fügen Sie Clientheader zu jeder Datei hinzu. Lassen Sie die folgenden Header zu:

* &quot;X-Requested-With&quot;
* &quot;X-SET-HEARTBEAT&quot;
* &quot;X-REQUEST-COMMAND&quot;

#### Java-Kodierung {#java-encoding}

Stellen Sie die ***Java-Kodierung*** auf Unicode ein. *Dfile.encoding=Cp1252* funktioniert beispielsweise nicht.

>[!NOTE]
>
>**Empfehlung:**
>
>Für AEM Screens Server in Produktionsumgebungen wird HTTPS empfohlen.

## Richtlinien zur Hardware-Auswahl für das Player-Gerät {#hardware-selection-guidelines-for-player-device}

Der folgende Abschnitt enthält Richtlinien zur Hardware-Auswahl für ein Screens-Projekt:

* Beziehen Sie für PC-Player und Anzeige-Panels oder Projektoren stets Komponenten von ***Handels-*** oder ***Industrie***-Qualität.

* Arbeiten Sie immer mit Anbietern, die den Markt für digitale Beschilderung bedienen.
* Berücksichtigen Sie stets Umgebungsfaktoren wie Umgebungstemperatur und relative Luftfeuchtigkeit.
* Überprüfen Sie stets Strombedarf und Stromkonditionierung.
* Prüfen Sie sorgfältig die für die Anwendung erforderlichen Leistungsanforderungen und E/A-Anschlüsse.

In der folgenden Tabelle sind die Hardware-Konfigurationen mit typischen Anwendungsbeispielen für ein AEM Screens-Projekt zusammengefasst:

<table> 
 <tbody> 
  <tr> 
   <td>Player-Konfiguration</td> 
   <td>Prozessor</td> 
   <td>Arbeitsspeicher</td> 
   <td>Speicher-SSD</td> 
   <td>GPU</td> 
   <td>Anzeige</td> 
   <td>E/A</td> 
   <td>Typische Anwendungsbeispiele</td> 
  </tr> 
  <tr> 
   <td>Einfach</td> 
   <td>Dual Core-, i3- oder Quad-Core Intel® Atom-Prozessor der Einstiegsklasse</td> 
   <td><p>4 GB Arbeitsspeicher</p> <p>2 MB Cache</p> </td> 
   <td><p>•ChromeOS 32 GB</p> <p>•Windows 128 GB</p> </td> 
   <td>OnBoard</td> 
   <td>1920 x 1080</td> 
   <td>DVI,<br /> Ethernet/Wireless,<br /> 2x USB</td> 
   <td> 
    <ul> 
     <li>Standardschleife im Vollbildmodus <br /> </li> 
     <li>Tagesaufteilung</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Standard</td> 
   <td>Intel® Core i5-Prozessor (Quad-Core)</td> 
   <td><p>8GB Arbeitsspeicher</p> <p>4MB Cache</p> </td> 
   <td>128 GB</td> 
   <td>OnBoard</td> 
   <td>3840 x 2160 (4 K)</td> 
   <td>DVI, HDMI<br /> Ethernet/Wireless,<br /> 2x USB</td> 
   <td> 
    <ul> 
     <li>Dynamischer Inhalt aus einer Quelle </li> 
     <li>Einfach interaktiv</li> 
     <li> 1-3 Bereichs-Layouts</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Erweitert</td> 
   <td>Intel® Core i7-Prozessor, Quad-Core mit Hyperthreading</td> 
   <td><p>16GB Arbeitsspeicher</p> <p>8MB Cache</p> </td> 
   <td>256 GB</td> 
   <td>Diskrete GPU</td> 
   <td>3840 x 2160 (4 K)</td> 
   <td>DVI, HDMI<br /> Ethernet/Wireless,<br /> 4xUSB</td> 
   <td> 
    <ul> 
     <li>4 oder mehr Inhaltsbereiche, gleichzeitige Videowiedergabe</li> 
     <li> Interaktiv auf mehreren Seiten</li> 
     <li>Datenauslöser aus mehreren Quellen</li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## Die nächsten Schritte {#the-next-steps}

Nachdem Sie den Screens Player installiert und konfiguriert haben, führen Sie die folgenden Schritte aus, um zu beginnen:

1. [Erstellen und Verwalten von Screens-Projekten](creating-a-screens-project.md)
1. [Erstellen und Verwalten von Kanälen](managing-channels.md)
1. [Erstellen und Verwalten von Standorten](managing-locations.md)
1. [Erstellen und Verwalten von Anzeigen](managing-displays.md)
1. [Zuweisen von Kanälen](channel-assignment.md)
1. [Geräte verwalten](managing-devices.md)
1. [Registrieren von Geräten](device-registration.md)
1. [Zuweisen von Geräten](managing-devices.md)
1. [Erstellen und Verwalten von Zeitplänen](managing-schedules.md)
1. [AEM Screens-Player](working-with-screens-player.md)
1. [Fehlerbehebung beim Device Control Center](monitoring-screens.md)

