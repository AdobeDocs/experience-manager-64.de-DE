---
title: Architektonischer Überblick zur Autoren- und Veröffentlichungsinstanz
seo-title: Architektonischer Überblick zur Autoren- und Veröffentlichungsinstanz
description: Die AEM Screens-Architektur ähnelt einer traditionellen AEM Sites-Architektur. Inhalte werden in einer AEM-Autoreninstanz erstellt und dann vorwärts an mehrere Veröffentlichungsinstanzen repliziert. Auf dieser Seite erfahren Sie mehr über die Architektur der Autoren- und Veröffentlichungsinstanz.
seo-description: Die AEM Screens-Architektur ähnelt einer traditionellen AEM Sites-Architektur. Inhalte werden in einer AEM-Autoreninstanz erstellt und dann vorwärts an mehrere Veröffentlichungsinstanzen repliziert. Auf dieser Seite erfahren Sie mehr über die Architektur der Autoren- und Veröffentlichungsinstanz.
uuid: f5c848fb-c230-4fb1-8760-e42c643fc405
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
content-type: reference
topic-tags: administering
discoiquuid: e650e33b-198f-41bf-a912-3d76f635b557
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Architektonischer Überblick zur Autoren- und Veröffentlichungsinstanz{#author-and-publish-architectural-overview}

Auf dieser Seite werden folgende Themen vorgestellt:

* **Einführung in Veröffentlichungs-Server**
* **Architektonischer Überblick**
* **Registrierungsverfahren**

## Voraussetzungen {#prerequisites}

Bevor Sie mit Autoren- und Veröffentlichungs-Servern beginnen, sollten Sie mit folgenden Themen vertraut sein:

* **AEM-Topologie**
* **Erstellen und Verwalten von AEM Screens-Projekten**
* **Verfahren zur Geräteregistrierung**

>[!NOTE]
>
>Diese AEM Screens-Funktion ist nur verfügbar, wenn Sie das Feature Pack 2 für AEM 6.4 Screens installiert haben. Wenden Sie sich an den Adobe-Support, um Zugriff auf dieses Feature Pack zu erhalten. Wenn Sie die entsprechenden Berechtigungen erhalten haben, können Sie es von Package Share herunterladen.

## Einführung {#introduction}

Die AEM Screens-Architektur ähnelt einer traditionellen AEM Sites-Architektur. Inhalte werden in einer AEM-Autoreninstanz erstellt und dann vorwärts an mehrere Veröffentlichungsinstanzen repliziert. AEM Screens-Geräte können jetzt per Load-Balancer mit einer AEM-Veröffentlichungs-Farm verbunden werden. Es lassen sich zur weiteren Skalierung der Veröffentlichungs-Farm mehrere AEM-Veröffentlichungsinstanzen hinzufügen.

*Beispielsweise* gibt ein Autor von AEM Screens-Inhalten im Authoring-System einen Befehl für ein bestimmtes Gerät aus, das für die Interaktion mit einer Veröffentlichungs-Farm oder einem Autor von AEM Screens-Inhalten konfiguriert ist, der Informationen über Geräte abruft, die für die Interaktion mit Veröffentlichungs-Farmen konfiguriert sind.

Das folgende Diagramm veranschaulicht die Autoren- und Veröffentlichungsumgebungen.

![screen_shot_2019-03-04at30236pm](assets/screen_shot_2019-03-04at30236pm.png)

## Architektonisches Design {#architectural-design}

Es gibt fünf architektonische Komponenten, die diese Lösung unterstützen:

* ****** Replizieren von Inhalten von der Autoren- zur Veröffentlichungsinstanz für die Anzeige auf Geräten
* ***Rückwärtsreplizieren*** binärer Inhalte von der Veröffentlichungs- (von Geräten empfangen) zur Autoreninstanz
* ***Senden*** von Befehlen von der Autoren- zur Veröffentlichungsinstanz über bestimmte REST-APIs
* ***Messaging*** zwischen Veröffentlichungsinstanzen zur Synchronisierung von aktualisierten Geräteinformationen und Befehlen
* ***Abruf*** durch den Autor von Veröffentlichungsinstanzen zum Abrufen von Geräteinformationen über bestimmte REST-APIs

### Replikation (Weiterleitung) von Inhalten und Konfigurationen {#replication-forward-of-content-and-configurations}

Mit den standardmäßigen Replikationsagenten werden Kanalinhalte von Bildschirmen, Standortkonfigurationen und Gerätekonfigurationen repliziert. So können Autoren den Inhalt eines Kanals aktualisieren und optional eine Art Genehmigungs-Workflow durchlaufen, bevor Kanalaktualisierungen veröffentlicht werden. Für jede Veröffentlichungsinstanz in der Veröffentlichungs-Farm muss ein Replikationsagent eingerichtet werden.

Das folgende Diagramm veranschaulicht das Replikationsverfahren:

![screen_shot_2019-03-04at33935pm](assets/screen_shot_2019-03-04at33935pm.png)

>[!NOTE]
>
>Für jede Veröffentlichungsinstanz in der Veröffentlichungs-Farm muss ein Replikationsagent eingerichtet werden.

### Screens-Replikationsagenten und -Befehle {#screens-replication-agents-and-commands}

Benutzerdefinierte Screens-spezifische Replikationsagenten werden erstellt, um Befehle von der Autoreninstanz an das AEM Screens-Gerät zu senden. Die AEM-Veröffentlichungsinstanzen dienen als Vermittler, um diese Befehle an das Gerät weiterzuleiten.

Auf diese Weise können Autoren das Gerät weiter verwalten, z. B. Geräteaktualisierungen senden und Screenshots der Authoring-Umgebung erstellen. Die AEM Screens-Replikationsagenten verfügen über eine benutzerdefinierte Transportkonfiguration, wie standardmäßige Replikationsagenten.

### Messaging zwischen Veröffentlichungsinstanzen {#messaging-between-publish-instances}

In vielen Fällen soll ein Befehl an ein Gerät nur einmal gesendet werden. In einer Veröffentlichungsarchitektur mit Load-Balancing ist jedoch nicht bekannt, mit welcher Veröffentlichungsinstanz das Gerät eine Verbindung herstellt.

Daher sendet die Autoreninstanz die Nachricht an alle Veröffentlichungsinstanzen. Es soll jedoch nur eine einzige Nachricht an das Gerät weitergeleitet werden. Um eine korrekte Benachrichtigung sicherzustellen, muss zwischen den Veröffentlichungsinstanzen kommuniziert werden. Dies wird mit *Apache ActiveMQ Artemis erreicht. *Jede Veröffentlichungsinstanz wird mit dem Oak-basierten Sling-Erkennungsdienst in einer locker gekoppelten Topologie platziert; ActiveMQ wird so konfiguriert, dass jede Veröffentlichungsinstanz kommunizieren und eine einzelne Nachrichtenwarteschlange erstellen kann. Das Screens-Gerät fragt über den Load-Balancer die Veröffentlichungs-Farm ab und übernimmt den Befehl an der Spitze der Warteschlange.

### Rückwärtsreplikation {#reverse-replication}

In vielen Fällen wird nach einem Befehl eine bestimmte Antwort vom Screens-Gerät erwartet, die an die Autoreninstanz weitergeleitet wird. Dafür wird AEM-***Rückwärtsreplikation*** verwendet.

* Erstellen Sie für jede Veröffentlichungsinstanz einen Agenten für Rückwärtsreplikation, ähnlich wie bei den standardmäßigen Replikationsagenten und den Screens-Replikationsagenten.
* Eine Workflow-Starter-Konfiguration überwacht die in der Veröffentlichungsinstanz geänderten Knoten und löst dann einen Workflow aus, um die Antwort des Geräts im Ausgang der Veröffentlichungsinstanz zu platzieren.
* Eine Rückwärtsreplikation wird in diesem Kontext nur für binäre Daten (wie Protokolldateien und Screenshots) verwendet, die von den Geräten bereitgestellt werden. Nicht-binäre Daten werden per Abruf abgerufen.
* Bei einer von der AEM-Autoreninstanz abgerufenen Rückwärtsreplikation wird die Antwort abgerufen und in der Autoreninstanz gespeichert.

### Abrufen von Veröffentlichungsinstanzen {#polling-of-publish-instances}

Die Autoreninstanz muss die Geräte abfragen können, um einen Takt zu erhalten und den Integritätsstatus eines verbundenen Geräts zu kennen.

Geräte pingen den Load-Balancer und werden an eine Veröffentlichungsinstanz weitergeleitet. Der Status des Geräts wird dann von der Veröffentlichungsinstanz über eine Publish-API veröffentlicht, die für alle aktiven Geräte unter **api/screens-dcc/devices/stati** und für einzelne Geräte unter **api/screens-dcc/devices/&lt;Geräte-ID>/status.json** bereitgestellt wird.

Die Autoreninstanz fragt alle Veröffentlichungsinstanzen ab und führt die Antworten zum Gerätestatus in einem Status zusammen. The scheduled job that polls on author is *com.adobe.cq.screens.impl.jobs.DistributedDevicesStatiUpdateJob* and can be configured based on a cron expression.

## Registrierung {#registration}

Der Ursprung der Registrierung liegt weiterhin in der AEM-Autoreninstanz. Das AEM Screens-Gerät verweist auf die Autoreninstanz und die Registrierung ist abgeschlossen.

Nachdem ein Gerät in der Authoring-Umgebung registriert wurde, werden die Gerätekonfiguration und die Kanal-/Zeitplanzuweisungen an die AEM-Veröffentlichungsinstanzen repliziert. Anschließend wird die Konfiguration des AEM Screens-Geräts aktualisiert, um auf den Load-Balancer vor der AEM-Veröffentlichungs-Farm zu verweisen. Es soll sich dabei um eine einmalige Einrichtung handeln. Nachdem das Screens-Gerät erfolgreich eine Verbindung zur Publishing-Umgebung hergestellt hat, kann es weiter Befehle aus der Authoring-Umgebung erhalten, ohne dass es jemals direkt mit der Authoring-Umgebung verbunden werden muss.

![screen_shot_2019-02-25at15218pm](assets/screen_shot_2019-02-25at15218pm.png)

### Die nächsten Schritte {#the-next-steps}

Nachdem Sie sich mit dem architektonischen Design der Autoren- und Veröffentlichungsinstanz in AEM Screens vertraut gemacht haben, finden Sie weitere Informationen unter [**Konfigurieren von Autoren- und Veröffentlichungsinstanz für AEM Screens **](author-and-publish.md).
