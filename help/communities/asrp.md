---
title: ASRP - Adobe Datenspeicherung Resource Provider
seo-title: ASRP - Adobe Datenspeicherung Resource Provider
description: AEM Communities für die Verwendung einer relationalen Datenbank als gemeinsamen Speicher einrichten
seo-description: AEM Communities für die Verwendung einer relationalen Datenbank als gemeinsamen Speicher einrichten
uuid: 29826b44-633d-4586-8553-cd87ebe269a2
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 86349e4d-29ff-4baa-9fcd-c0ab1f0753e9
role: 'Administrator  '
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '830'
ht-degree: 2%

---


# ASRP - Adobe Datenspeicherung Resource Provider {#asrp-adobe-storage-resource-provider}

## Über ASRP {#about-asrp}

Wenn AEM Communities so konfiguriert ist, dass ASRP als gemeinsamer Speicher verwendet wird, können vom Benutzer generierte Inhalte (UGC) von allen Autor- und Veröffentlichungsinstanzen aus aufgerufen werden, ohne dass eine Synchronisierung oder Replikation erforderlich ist.

Siehe auch [Eigenschaften der SRP-Optionen](working-with-srp.md#characteristics-of-srp-options) und [Empfohlene Topologien](topologies.md).

## Voraussetzungen {#requirements}

Für die Verwendung von ASRP ist eine zusätzliche Lizenz erforderlich.

Wenden Sie sich an Ihren Kundenbetreuer, um Ihre AEM Communities-Site für die Verwendung von ASRP für UGC zu konfigurieren.

* Datenzentrum-URL (Adresse des ASRP-Endpunkts)
* Verbraucherschlüssel
* Geheimer Schlüssel
* Report Suite-ID(s)

Die Verbraucher- und geheimen Schlüssel werden für alle Report Suites für eine Firma freigegeben. Pro Mandant gibt es eine Report Suite.

## Konfiguration {#configuration}

### ASRP {#select-asrp}

Die [Datenspeicherung Configuration Console](srp-config.md) ermöglicht die Auswahl der Standardkonfiguration der Datenspeicherung, die die zu verwendende Implementierung von SRP identifiziert.

**Beim Autor**:

* Aus globaler Navigation: **[!UICONTROL Tools > Communities > Datenspeicherung Configuration]**

![chlimage_1-310](assets/chlimage_1-310.png)

* Wählen Sie **[!UICONTROL Adobe Datenspeicherung Resource Provider (ASRP)]**
* Die folgenden Informationen stammen aus dem Bereitstellungsprozess

   * **[!UICONTROL Datenzentrum-URL]**

      Ziehen Sie den Cursor nach unten, um das Produktionsdatencenter auszuwählen, das von Ihrem Kundenbetreuer identifiziert wurde.

   * **[!UICONTROL Standard-Berichtssuite]**

      Geben Sie den Namen der Standard-Report Suite ein

   * **[!UICONTROL Verbraucherschlüssel]**

      Consumer key eingeben

   * **[!UICONTROL Geheimnis]**

      Geben Sie den geheimen Schlüssel ein

* Klicken Sie auf **[!UICONTROL Übermitteln]**

Vorbereiten der Veröffentlichungsinstanzen:

* [Kryptoschlüssel replizieren](#replicate-the-crypto-key)
* [Konfiguration replizieren](#publishing-the-configuration)

Nach dem Senden der Konfiguration die Verbindung testen:

* Wählen Sie **[!UICONTROL Testkonfiguration]**
für jede Instanz im Autorenmodus und jede Instanz im Veröffentlichungsmodus die Verbindung zum Rechenzentrum über die Datenspeicherung Configuration Console testen

* Stellen Sie abschließend sicher, dass die Site-URLs für Profil-Daten vom Rechenzentrum routinemäßig über [Externalisierungs-Links](#externalize-links) ausgeführt werden können.

### Crypto-Schlüssel {#replicate-the-crypto-key} replizieren

Die Consumer key und der Geheimschlüssel sind verschlüsselt. Damit die Schlüssel richtig verschlüsselt/entschlüsselt werden können, muss der primäre Granite Crypto-Schlüssel auf allen AEM Instanzen gleich sein.

Befolgen Sie die Anweisungen unter [Crypto-Schlüssel replizieren](deploy-communities.md#replicate-the-crypto-key).

### Externalisieren von Links {#externalize-links}

Stellen Sie für korrekte Profil- und Profil-Bildverknüpfungen sicher, dass Sie [Link Externalizer konfigurieren](../../help/sites-developing/externalizer.md) richtig konfigurieren.

Stellen Sie sicher, dass es sich bei den Domänen um URLs handelt, die über die Data Center-URL (ASRP-Endpunkt) routingfähig sind.

### Zeitsynchronisierung {#time-synchronization}

Damit die Authentifizierung mit dem ASRP-Endpunkt erfolgreich ist, müssen die Computer, auf denen das gehostete AEM Communities ausgeführt wird, zeitsynchronisiert sein, z. B. mit dem [Network Time Protocol (NTP)](https://www.ntp.org/).

### Veröffentlichen der Konfiguration {#publishing-the-configuration}

ASRP muss in allen Autoren- und Veröffentlichungsinstanzen als gemeinsamer Speicher identifiziert werden.

So stellen Sie die gleiche Konfiguration in der Umgebung &quot;Veröffentlichen&quot;zur Verfügung:

* **Beim Autor**:

   * Navigieren Sie vom Hauptmenü zu **[!UICONTROL Tools > Vorgänge > Replikation]**
   * Wählen Sie **[!UICONTROL Baum aktivieren]**
   * **[!UICONTROL Startpfad]**:

      * Gehen Sie zu `/etc/socialconfig/srpc/`
   * Deaktivieren Sie **[!UICONTROL Nur geändert]**
   * Wählen Sie **[!UICONTROL Aktivieren]**


## Aktualisieren von AEM 6.0 {#upgrading-from-aem}

>[!CAUTION]
>
>Wenn Sie ASRP auf einer veröffentlichten Community-Site aktivieren, sind bereits in [JCR](jsrp.md) gespeicherte UGC nicht mehr sichtbar, da keine Synchronisierung der Daten zwischen der lokalen Datenspeicherung und der Cloud-Datenspeicherung erfolgt.

**`AEM Communities Extension`** wurde zuvor in AEM 6.0 Social Communities als Cloud-Dienst eingeführt. Ab AEM 6.1 Communities ist keine Cloud-Konfiguration erforderlich. Wählen Sie einfach ASRP aus der [Datenspeicherung-Konfigurationskonsole](srp-config.md).

Aufgrund der neuen Datenspeicherung müssen Sie bei der Aktualisierung von Social Communities auf Communities die [upgrade](upgrade.md#adobe-cloud-storage)-Anweisungen befolgen.

## Verwalten von Benutzerdaten {#managing-user-data}

Informationen zu *Benutzergruppen*, *Benutzergruppen* und *die häufig in die Umgebung &quot;Veröffentlichen&quot;eingegeben wurden, finden Sie unter*

* [Benutzersynchronisierung](sync.md)
* [Verwalten von Benutzern und Benutzergruppen](users.md)

## Fehlerbehebung {#troubleshooting}

### UGC verschwindet nach der Aktualisierung {#ugc-disappears-after-upgrade}

Wenn Sie ein Upgrade von einer vorhandenen Social Community-Site AEM 6.0 durchführen, folgen Sie den [Upgrade-Anweisungen](upgrade.md#adobe-cloud-storage), andernfalls *erscheint*, um verloren zu gehen.

### Authentifizierungsfehler {#authentication-errors}

Wenn beim Empfang von Authentifizierungsfehlern für die Data Center-URL die Datei &quot;error.log&quot;Meldungen über statische Zeitstempel enthält, stellen Sie sicher, dass eine Synchronisierung durchgeführt wird.

Es wird empfohlen, ein Tool wie das [Network Time Protocol (NTP)](https://www.ntp.org/) zu verwenden, um alle AEM Autor- und Veröffentlichungsserver zeitlich zu synchronisieren.

### Neuer Inhalt wird nicht in Suchvorgängen {#new-content-does-not-appear-in-searches} angezeigt

Die Infrastruktur für die Adobe Cloud-Datenspeicherung verwendet *letztendlich Konsistenz*, um die Skalierungs- und Leistungsziele zu erreichen. Aus diesem Grund sind neue Inhalte nicht sofort verfügbar und es kann einige Sekunden dauern, bis sie in den Suchergebnissen angezeigt werden.

Während das Intervall, das sich auf die spätere Konsistenz auswirkt, überwacht wird, wenden Sie sich an Ihren Kundenbetreuer, wenn es länger als ein paar Sekunden dauert, bis neue Inhalte in Suchvorgängen angezeigt werden.

### UGC nicht sichtbar in ASRP {#ugc-not-visible-in-asrp}

Vergewissern Sie sich, dass ASRP als Standardanbieter konfiguriert wurde, indem Sie die Konfigurationsoption der Datenspeicherung überprüfen. Standardmäßig ist der Datenspeicherung Resource Provider JSRP, nicht ASRP.

Rufen Sie auf allen Instanzen im Autorenmodus und AEM Veröffentlichungsmodus erneut die Datenspeicherung Configuration Console auf oder überprüfen Sie das AEM Repository:

* In JCR, wenn [/etc/socialconfig](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/)

   * Enthält keinen Knoten [srpc](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc), d. h., der Anbieter der Datenspeicherung ist JSRP
   * Wenn der Knoten srpc vorhanden ist und den Knoten [defaultConfiguration](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc/defaultconfiguration) enthält, sollten die Eigenschaften der Standardkonfiguration ASRP als Standardanbieter definieren

