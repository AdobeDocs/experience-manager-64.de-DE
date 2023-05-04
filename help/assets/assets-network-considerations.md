---
title: Überlegungen zum Assets-Netzwerk
description: Erläutert Netzwerküberlegungen beim Entwurf eines [!DNL Experience Manager] Assets-Bereitstellung.
contentOwner: AG
feature: Developer Tools
role: Architect,Admin
exl-id: f8f9d86f-a5e3-46ac-8d96-c2e44eac9c93
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1035'
ht-degree: 32%

---

# Überlegungen zum Assets-Netzwerk {#assets-network-considerations}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Das Verständnis Ihres Netzwerks ist ebenso wichtig wie das Verständnis von Adobe Experience Manager Assets. Das Netzwerk kann sich auf das Upload-, Download- und Benutzererlebnis auswirken. Die Abbildung Ihrer Netzwerktopologie hilft dabei, Engpässe und unteroptimierte Bereiche im Netzwerk zu identifizieren, die Sie beheben müssen, um die Netzwerkleistung und das Benutzererlebnis zu verbessern.

Stellen Sie sicher, dass Sie Folgendes in Ihr Netzwerkdiagramm aufnehmen:

* Verbindung vom Client-Gerät (z. B. Computer, Mobilgerät und Tablet) zum Netzwerk
* Topologie des Unternehmensnetzwerks
* Uplink zum Internet vom Unternehmensnetzwerk und von der [!DNL Experience Manager]-Umgebung
* Topologie der [!DNL Experience Manager]-Umgebung
* Definition gleichzeitiger Verbraucher und Verbraucherinnen der [!DNL Experience Manager]-Netzwerkschnittstelle
* Definierte Workflows der [!DNL Experience Manager] instance

## Möglichkeit der Verbindung des Client-Geräts mit dem Unternehmensnetzwerk {#connectivity-from-the-client-device-to-the-corporate-network}

Erstellen Sie zunächst eine Grafik der Verbindung zwischen den einzelnen Client-Geräten und dem Unternehmensnetzwerk. Identifizieren Sie in dieser Phase freigegebene Ressourcen, z. B. WLAN-Verbindungen, bei denen mehrere Benutzer auf denselben Punkt oder Ethernet-Switch zugreifen, um Assets hochzuladen und herunterzuladen.

![chlimage_1-353](assets/chlimage_1-353.png)

Client-Geräte stellen auf verschiedene Arten eine Verbindung mit einem Unternehmensnetzwerk her, z. B. über freigegebenes WLAN, Ethernet mit gemeinsam genutztem Switch und VPN. Das Ermitteln und Verstehen von Engpässen in diesem Netzwerk ist für die Planung von Assets und die Änderung des Netzwerks wichtig.

Oben links im Diagramm werden drei Geräte als WiFi-Zugangspunkt mit 48 MBit/s dargestellt. Wenn alle Geräte gleichzeitig hochgeladen werden, wird die WiFi-Netzwerkbandbreite von den Geräten gemeinsam genutzt. Im Vergleich zu einem System als Ganzes kann ein Benutzer auf einen Engpass stoßen, der daraus resultiert, dass die drei Clients diesen Kanal gemeinsam nutzen.

Es ist eine Herausforderung, die wahre Geschwindigkeit eines WLAN-Netzwerks zu messen, da ein langsames Gerät andere Clients auf den Zugangspunkt beeinflussen kann. Wenn Sie für Asset-Interaktionen WLAN verwenden möchten, führen Sie einen Geschwindigkeitstest von mehreren Clients gleichzeitig durch, um den Durchsatz zu ermitteln.

Unten links im Diagramm sind zwei Geräte dargestellt, die über unabhängige Kanäle mit dem Unternehmensnetzwerk verbunden sind. Daher kann jedes Gerät eine Mindestgeschwindigkeit von 10 Mbit/s und 100 Mbit/s nutzen.

Der rechts angezeigte Computer verfügt über eine begrenzte Upstream-Funktionalität über einen VPN mit einer Geschwindigkeit von 1 MBit/s. Das Benutzererlebnis bei der 1 MBit/s schnellen Verbindung unterscheidet sich erheblich vom Benutzererlebnis bei der 1 GBit/s schnellen Verbindung. Je nach Größe der Assets, mit denen Benutzer interagieren, kann ihr VPN-Uplink für die Aufgabe unzureichend sein.

## Topologie des Unternehmensnetzwerks  {#topology-of-the-corporate-network}

![chlimage_1-354](assets/chlimage_1-354.png)

Das Diagramm zeigt höhere Uplink-Geschwindigkeiten innerhalb des Unternehmensnetzwerks, als im Allgemeinen üblich sind. Diese Pipe sind gemeinsame Ressourcen. Wenn erwartet wird, dass der gemeinsam genutzte Switch 50 Clients verarbeitet, kann dies ein Engpass sein. Im anfangs gezeigten Diagramm nutzen nur zwei Computer die betreffende Verbindung.

## Uplink zum Internet vom Unternehmensnetzwerk und von der [!DNL Experience Manager]-Umgebung {#uplink-to-the-internet-from-the-corporate-network-and-aem-environment}

![chlimage_1-355](assets/chlimage_1-355.png)

Es ist wichtig, unbekannte Faktoren im Internet und in der VPC-Verbindung zu berücksichtigen, da die Bandbreite im Internet durch Spitzenlasten oder Ausfälle bei großen Anbietern beeinträchtigt werden kann. Im Allgemeinen ist die Internetverbindung zuverlässig. Manchmal kann es jedoch zu Engpässen kommen.

Am Uplink von einem Unternehmensnetzwerk zum Internet kann es andere Dienste geben, die die Bandbreite nutzen. Es ist wichtig zu verstehen, wie viel Bandbreite zugewiesen oder priorisiert werden kann für [!DNL Assets]. Wenn beispielsweise eine 1 Gbit/s-Verbindung bereits zu 80 % genutzt wird, können Sie nur maximal 20 % der Bandbreite für [!DNL Experience Manager] Assets.

Unternehmens-Firewalls und Proxys können Bandbreite zudem auf vielfältige Weise anpassen. Bei diesem Gerätetyp kann die Bandbreite anhand der Dienstqualität, der Bandbreitenbeschränkungen pro Benutzer oder der Bitratenbeschränkungen pro Host priorisiert werden. Dies sind wichtige Checkpoints, die untersucht werden müssen, da sie erhebliche Auswirkungen auf das Asset-Benutzererlebnis haben können.

In diesem Beispiel nutzt das Unternehmen einen 10 GBit/s schnellen Uplink. Dieser sollte für mehrere Clients ausreichen. Außerdem beschränkt die Firewall die Host-Geschwindigkeit auf 10 MBit/s. Durch diese Beschränkung kann der Traffic auf einen einzelnen Host auf 10 MBit/s drosseln, auch wenn der Uplink zum Internet bei 10 GBit/s liegt.

Dies ist der kleinste Client-orientierte Checkpoint. Sie können jedoch eine Änderung oder eine Zulassungsliste mit der für diese Firewall zuständigen Netzwerkbetriebsgruppe prüfen.

Aus den Beispieldiagrammen ist ersichtlich, dass sechs Geräte einen konzeptionellen, 10 MBit/s schnellen Kanal gemeinsam nutzen. Je nach Größe der verwendeten Assets ist dies möglicherweise nicht ausreichend, um die Erwartungen der Benutzer zu erfüllen.

## Topologie der [!DNL Experience Manager]-Umgebung {#topology-of-the-aem-environment}

![chlimage_1-356](assets/chlimage_1-356.png)

Das Entwerfen der Topologie der [!DNL Experience Manager]-Umgebung erfordert detaillierte Kenntnisse der Systemkonfiguration sowie der Art der Netzwerkverbindung innerhalb der Benutzerumgebung.

Das Beispielszenario umfasst eine Veröffentlichungsfarm mit fünf Servern, einen S3-Binärspeicher und konfigurierten dynamischen Medien.

Der Dispatcher teilt seine 100 MBit/s-Verbindung mit zwei Entitäten, der Außenwelt und der [!DNL Experience Manager] -Instanz. Bei gleichzeitigen Upload- und Download-Vorgängen sollte diese Zahl durch zwei dividiert werden. Der angeschlossene externe Speicher verwendet eine separate Verbindung.

Die [!DNL Experience Manager] -Instanz teilt die 1 Gbit/s-Verbindung mit mehreren Diensten. Aus Sicht der Netzwerktopologie entspricht das der Nutzung eines einzelnen Kanals mit verschiedenen Diensten.

Überprüfen Sie das Netzwerk vom Client-Gerät zum [!DNL Experience Manager] Beispielsweise scheint der kleinste Engpass die Firewall-Drosselklappe von 10 Mbit für Unternehmen zu sein. Sie können diese Werte für die in der [Anleitung zur Dimensionierung in Assets](assets-sizing-guide.md) beschriebenen Größenberechnung verwenden, um das Benutzererlebnis zu bestimmen.

## Definierte Workflows der [!DNL Experience Manager] instance {#defined-workflows-of-the-aem-instance}

Bei Überlegungen zur Netzwerkleistung ist es möglicherweise wichtig, die Workflows und die im System stattfindenden Veröffentlichungen zu berücksichtigen. Außerdem beanspruchen S3 oder Speicher, der im Netzwerk zugeteilt ist und von Ihnen verwendet wird, und I/O-Anforderungen Netzwerkbandbreite. Daher wird die Leistung selbst in einem voll optimierten Netzwerk durch die Anzahl der Datenträger-I/O beschränkt.

Zur Optimierung von Prozessen rund um die Asset-Erfassung (insbesondere beim Hochladen einer großen Anzahl von Assets) sollten Sie Asset-Workflows untersuchen und mehr über deren Konfiguration erfahren.

Bei der Auswertung der internen Workflow-Topologie sollten Sie Folgendes analysieren:

* Verfahren zum Schreiben eines Assets
* Workflows/Ereignisse, die beim Ändern von Assets/Metadaten Trigger werden
* Verfahren zum Lesen eines Assets

Es folgen einige Punkte, die zu berücksichtigen sind:

* XMP lesen/schreiben von Metadaten
* Automatische Aktivierung und Replikation
* Wasserzeichen  
* Aufnahme von Unter-Assets/Seitenextraktion
* Überlappende Workflows

Im Folgenden finden Sie ein Kundenbeispiel für die Definition eines Asset-Workflows.

![chlimage_1-357](assets/chlimage_1-357.png)
