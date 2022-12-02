---
title: Überlegungen zum Assets-Netzwerk
description: Erläutert Netzwerküberlegungen beim Entwurf eines [!DNL Experience Manager] Assets-Bereitstellung.
contentOwner: AG
feature: Developer Tools
role: Architect,Admin
exl-id: f8f9d86f-a5e3-46ac-8d96-c2e44eac9c93
source-git-commit: cc6de21180c9fff74f7d64067db82f0c11ac9333
workflow-type: tm+mt
source-wordcount: '999'
ht-degree: 88%

---

# Überlegungen zum Assets-Netzwerk {#assets-network-considerations}

Das Verständnis Ihres Netzwerks ist ebenso wichtig wie das Verständnis von Adobe Experience Manager Assets. Das Netzwerk kann Uploads, Downloads und Benutzererlebnisse beeinflussen. Eine grafische Darstellung Ihrer Netzwerktopologie hilft bei der Erkennung von Engpässen und unzureichend optimierten Bereichen im Netzwerk, die Sie beseitigen bzw. korrigieren müssen, um die Netzwerkleistung und das Benutzererlebnis zu verbessern.

Stellen Sie sicher, dass Sie Folgendes in Ihre Netzwerkgrafik einbeziehen:

* Möglichkeit der Verbindung des Client-Geräts (z. B. Computer, Mobilgerät oder Tablet) mit dem Netzwerk
* Topologie des Unternehmensnetzwerks
* Uplink zum Internet vom Unternehmensnetzwerk und von der [!DNL Experience Manager]-Umgebung
* Topologie der [!DNL Experience Manager]-Umgebung
* Definition gleichzeitiger Verbraucher und Verbraucherinnen der [!DNL Experience Manager]-Netzwerkschnittstelle
* Definierte Workflows der [!DNL Experience Manager] instance

## Möglichkeit der Verbindung des Client-Geräts mit dem Unternehmensnetzwerk {#connectivity-from-the-client-device-to-the-corporate-network}

Beginnen Sie, indem Sie die Verbindungsmöglichkeit zwischen den einzelnen Client-Geräten und dem Unternehmensnetzwerk grafisch darstellen. In dieser Phase ermitteln Sie gemeinsam genutzte Ressourcen wie WLAN-Verbindungen, bei denen mehrere Benutzer Zugriff auf denselben Punkt oder Ethernet-Switch haben, wodurch sie Assets hoch- bzw. herunterladen können.

![chlimage_1-353](assets/chlimage_1-353.png)

Client-Geräte stellen auf verschiedene Arten eine Verbindung mit einem Unternehmensnetzwerk her, z. B. über freigegebenes WLAN, Ethernet mit gemeinsam genutztem Switch und VPN. Das Erkennen und Verstehen von Engpässen in diesem Netzwerk ist für die Planung von Assets und die Netzwerkmodifizierung unerlässlich.

Oben links im Diagramm sind drei Geräte dargestellt, die gemeinsam einen 48 MBit/s schnellen WLAN-Zugangspunkt nutzen. Wenn alle Geräte gleichzeitig hochladen, wird die WLAN-Netzbandbreite von den Geräten gemeinsam genutzt. Im Vergleich zu einem System als Ganzes kann ein Benutzer auf einen Engpass stoßen, der daraus resultiert, dass die drei Clients diesen Kanal gemeinsam nutzen.

Es ist eine Herausforderung, die wahre Geschwindigkeit eines WLAN-Netzes zu messen, weil ein langsames Gerät die Leistung anderer Clients am Zugangspunkt beeinträchtigen kann. Wenn Sie beabsichtigen, WLAN für Asset-Interaktionen zu verwenden, führen Sie einen Geschwindigkeitstest mit mehreren Clients gleichzeitig durch, um die Leistung zu bewerten.

Unten links im Diagramm sind zwei Geräte dargestellt, die mit dem Unternehmensnetzwerk über unabhängige Kanäle verbunden sind. Daher kann jedes Gerät eine Mindestgeschwindigkeit von 10 MBit/s und 100 MBit/s nutzen.

Der rechts gezeigte Computer hat einen begrenzten Upstream zum Unternehmensnetzwerk über eine VPN-Verbindung mit einer Geschwindigkeit von 1 MBit/s. Das Benutzererlebnis bei der 1 MBit/s schnellen Verbindung unterscheidet sich erheblich vom Benutzererlebnis bei der 1 GBit/s schnellen Verbindung. Je nach Größe der Assets, mit denen Benutzer interagieren, kann ihr VPN-Uplink für die Aufgabe nicht ausreichend sein.

## Topologie des Unternehmensnetzwerks  {#topology-of-the-corporate-network}

![chlimage_1-354](assets/chlimage_1-354.png)

Das Diagramm zeigt höhere Uplink-Geschwindigkeiten innerhalb des Unternehmensnetzwerks, als im Allgemeinen üblich sind. Diese Leitungen sind freigegebene Ressourcen. Wenn erwartet wird, dass ein freigegebener Switch die Vorgänge von 50 Clients abwickelt, kann es möglicherweise zu einem Engpass kommen. Im anfangs gezeigten Diagramm nutzen nur zwei Computer die betreffende Verbindung.

## Uplink zum Internet vom Unternehmensnetzwerk und von der [!DNL Experience Manager]-Umgebung {#uplink-to-the-internet-from-the-corporate-network-and-aem-environment}

![chlimage_1-355](assets/chlimage_1-355.png)

Es ist wichtig, unbekannte Faktoren des Internets und der VPC-Verbindung zu berücksichtigen, da die Bandbreite im Internet durch Spitzenlasten oder umfangreiche Anbieterausfälle verringert werden kann. Im Allgemeinen ist eine Internetverbindung zuverlässig. Manchmal kann es allerdings zu Engpässen kommen.

Am Uplink von einem Unternehmensnetzwerk zum Internet können andere Dienste die Bandbreite nutzen. Es ist wichtig zu verstehen, wie viel Bandbreite zugewiesen oder priorisiert werden kann für [!DNL Assets]. Wenn beispielsweise eine 1 Gbit/s-Verbindung bereits zu 80 % genutzt wird, können Sie nur maximal 20 % der Bandbreite für [!DNL Experience Manager] Assets.

Unternehmens-Firewalls und Proxys können Bandbreite zudem auf vielfältige Weise anpassen. Diese Geräteart kann Bandbreite mithilfe der Dienstgüte, der Bandbreitenbeschränkungen pro Benutzer oder der Bitratenbeschränkungen pro Host priorisieren. Dies sind wichtige Engpässe, die zu untersuchen sind, da sie das Assets-Benutzererlebnis erheblich beeinträchtigen können.

In diesem Beispiel nutzt das Unternehmen einen 10 GBit/s schnellen Uplink. Dieser sollte für mehrere Clients ausreichen. Außerdem beschränkt die Firewall die Host-Geschwindigkeit auf 10 MBit/s. Diese Beschränkung kann möglicherweise den Traffic zu einem einzelnen Host bis auf 10 MBit/s drosseln, obwohl der Uplink zum Internet auf 10 GBit/s ausgelegt ist.

Dies ist der kleinste Engpass in Bezug auf Clients. Sie können jedoch die für die Firewall verantwortliche Netzwerkbetriebsgruppe kontaktieren, um festzustellen, ob eine Änderung oder ein Eintrag in die Zulassungsliste infrage kommt.

Aus den Beispieldiagrammen ist ersichtlich, dass sechs Geräte einen konzeptionellen, 10 MBit/s schnellen Kanal gemeinsam nutzen. Je nach Größe der genutzten Assets reicht dies möglicherweise aus, um die Erwartungen der Benutzer zu erfüllen.

## Topologie der [!DNL Experience Manager]-Umgebung {#topology-of-the-aem-environment}

![chlimage_1-356](assets/chlimage_1-356.png)

Das Entwerfen der Topologie der [!DNL Experience Manager]-Umgebung erfordert detaillierte Kenntnisse der Systemkonfiguration sowie der Art der Netzwerkverbindung innerhalb der Benutzerumgebung.

Das Beispielszenario umfasst eine Veröffentlichungsfarm mit fünf Servern, einen binären S3-Speicher und konfigurierte dynamische Medien.

Der Dispatcher teilt seine 100 MBit/s-Verbindung mit zwei Entitäten, der Außenwelt und der [!DNL Experience Manager] -Instanz. Für gleichzeitiges Hoch- und Herunterladen sollten Sie diesen Wert durch zwei teilen. Der zugeordnete externe Speicher verwendet eine separate Verbindung.

Die [!DNL Experience Manager] -Instanz teilt die 1 Gbit/s-Verbindung mit mehreren Diensten. Aus Sicht der Netzwerktopologie entspricht das der Nutzung eines einzelnen Kanals mit verschiedenen Diensten.

Überprüfen Sie das Netzwerk vom Client-Gerät zum [!DNL Experience Manager] Beispielsweise scheint der kleinste Engpass die Firewall-Drosselklappe von 10 Mbit für Unternehmen zu sein. Sie können diese Werte für die in der [Anleitung zur Dimensionierung in Assets](assets-sizing-guide.md) beschriebenen Größenberechnung verwenden, um das Benutzererlebnis zu bestimmen.

## Definierte Workflows der [!DNL Experience Manager] instance {#defined-workflows-of-the-aem-instance}

Bei Überlegungen zur Netzwerkleistung ist es möglicherweise wichtig, die Workflows und die im System stattfindenden Veröffentlichungen zu berücksichtigen. Außerdem beanspruchen S3 oder Speicher, der im Netzwerk zugeteilt ist und von Ihnen verwendet wird, und I/O-Anforderungen Netzwerkbandbreite. Daher wird die Leistung selbst in einem voll optimierten Netzwerk durch die Anzahl der Datenträger-I/O beschränkt.

Um Prozesse zu optimieren, die mit der Asset-Aufnahme zu tun haben (insbesondere, wenn eine große Anzahl von Assets hochgeladen wird), sind die Asset-Workflows zu untersuchen, um mehr über ihre Konfiguration zu erfahren.

Bei der Untersuchung der internen Workflow-Topologie sollten Sie Folgendes analysieren:

* Verfahren zum Schreiben eines Assets
* Workflows/Ereignisse, die ausgelöst werden, wenn Assets/Metadaten geändert werden
* Verfahren zum Lesen eines Assets

Es folgen einige Punkte, die zu berücksichtigen sind:

* Lesen von XMP-Metadaten/Writeback
* Automatische Aktivierung und Replikation
* Wasserzeichen  
* Unter-Asset-Aufnahme/Seitenextraktion
* Überlappende Workflows

Es folgt ein Kundenbeispiel für die Definition eines Asset-Workflows.

![chlimage_1-357](assets/chlimage_1-357.png)
