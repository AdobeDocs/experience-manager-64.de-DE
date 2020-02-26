---
title: ASRP - Adobe Storage Resource Provider
seo-title: ASRP - Adobe Storage Resource Provider
description: Einrichten von AEM Communities zur Verwendung einer relationalen Datenbank als gemeinsamen Speicher
seo-description: Einrichten von AEM Communities zur Verwendung einer relationalen Datenbank als gemeinsamen Speicher
uuid: 29826b44-633d-4586-8553-cd87ebe269a2
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 86349e4d-29ff-4baa-9fcd-c0ab1f0753e9
translation-type: tm+mt
source-git-commit: 565604feff7fa365a1c6b52b62a0b0eb681bb192

---


# ASRP - Adobe Storage Resource Provider {#asrp-adobe-storage-resource-provider}

## Über ASRP {#about-asrp}

Wenn AEM Communities so konfiguriert ist, dass ASRP als gemeinsamer Speicher verwendet wird, können vom Benutzer generierte Inhalte (UGC) von allen Autor- und Veröffentlichungsinstanzen aus aufgerufen werden, ohne dass eine Synchronisierung oder Replikation erforderlich ist.

Siehe auch [Eigenschaften der SRP-Optionen](working-with-srp.md#characteristics-of-srp-options) und der [empfohlenen Topologien](topologies.md).

## Voraussetzungen {#requirements}

Für die Verwendung von ASRP ist eine zusätzliche Lizenz erforderlich.

Wenden Sie sich an Ihren Kundenbetreuer, um Ihre AEM Communities-Site für die Verwendung von ASRP für UGC zu konfigurieren.

* Datenzentrum-URL (Adresse des ASRP-Endpunkts)
* Verbraucherschlüssel
* Geheimer Schlüssel
* Report Suite-ID(s)

Die privaten und geheimen Schlüssel werden für alle Report Suites eines Unternehmens freigegeben. Pro Mandant gibt es eine Report Suite.

## Konfiguration{#configuration}

### ASRP auswählen {#select-asrp}

Die [Speicherkonfigurationskonsole](srp-config.md) ermöglicht die Auswahl der standardmäßigen Speicherkonfiguration, die festlegt, welche SRP-Implementierung verwendet werden soll.

**Beim Autor**:

* Aus globaler Navigation: **[!UICONTROL Werkzeuge > Communities > Speicherkonfiguration]**

![chlimage_1-310](assets/chlimage_1-310.png)

* Select **[!UICONTROL Adobe Storage Resource Provider (ASRP)]**
* Die folgenden Informationen stammen aus dem Bereitstellungsprozess

   * **[!UICONTROL Datenzentrum-URL]**

      Ziehen Sie den Cursor nach unten, um das Produktionsdatencenter auszuwählen, das von Ihrem Kundenbetreuer identifiziert wurde.

   * **[!UICONTROL Standard-Berichtssuite]**

      Geben Sie den Namen der Standard-Report Suite ein

   * **[!UICONTROL Verbraucherschlüssel]**

      Verbraucherschlüssel eingeben

   * **[!UICONTROL Geheimnis]**

      Geheimschlüssel eingeben

* Klicken Sie auf **[!UICONTROL Übermitteln]**

Vorbereiten der Veröffentlichungsinstanzen:

* [Kryptoschlüssel replizieren](#replicate-the-crypto-key)
* [Konfiguration replizieren](#publishing-the-configuration)

Nach dem Senden der Konfiguration die Verbindung testen:

* Wählen Sie **[!UICONTROL Testkonfiguration]** für jede Autoren- und Veröffentlichungsinstanz und testen Sie die Verbindung zum Rechenzentrum in der Speicherkonfigurationskonsole.

* Stellen Sie abschließend sicher, dass die Site-URLs für Profildaten vom Rechenzentrum routinemäßig über [externe Links](#externalize-links)abrufbar sind.

### Crypto-Schlüssel replizieren {#replicate-the-crypto-key}

Der Consumer Key und der Secret Key sind verschlüsselt. Damit die Schlüssel richtig verschlüsselt/entschlüsselt werden können, muss der Master-Granite-Crypto-Schlüssel auf allen AEM-Instanzen gleich sein.

Befolgen Sie die Anweisungen unter Crypto-Schlüssel [replizieren](deploy-communities.md#replicate-the-crypto-key).

### Links externalisieren {#externalize-links}

Für korrekte Profil- und Profilbild-Links müssen Sie den Link Externalizer ordnungsgemäß [konfigurieren](../../help/sites-developing/externalizer.md).

Stellen Sie sicher, dass es sich bei den Domänen um URLs handelt, die über die Data Center-URL (ASRP-Endpunkt) routingfähig sind.

### Zeitsynchronisierung {#time-synchronization}

Damit die Authentifizierung mit dem ASRP-Endpunkt erfolgreich ist, müssen die Computer, auf denen Ihre gehosteten AEM Communities ausgeführt werden, zeitsynchronisiert sein, z. B. mit dem [Network Time Protocol (NTP)](https://www.ntp.org/).

### Veröffentlichen der Konfiguration {#publishing-the-configuration}

ASRP muss in allen Autoren- und Veröffentlichungsinstanzen als gemeinsamer Speicher identifiziert werden.

So stellen Sie die identische Konfiguration in der Veröffentlichungsumgebung zur Verfügung:

* **Beim Autor**:

   * Navigieren Sie vom Hauptmenü zu **[!UICONTROL Tools > Vorgänge > Replikation]**
   * Baumstruktur **[!UICONTROL aktivieren]**
   * **[!UICONTROL Startpfad]**:

      * Navigieren zu `/etc/socialconfig/srpc/`
   * Deaktivieren **[!UICONTROL nur geändert]**
   * Aktivieren **[!UICONTROL auswählen]**


## Aktualisieren von AEM 6.0 {#upgrading-from-aem}

>[!CAUTION]
>
>Wenn Sie ASRP auf einer veröffentlichten Community-Site aktivieren, sind bereits in [JCR](jsrp.md) gespeicherte UGC nicht mehr sichtbar, da es keine Synchronisierung der Daten zwischen lokalen Speicher und Cloud-Speicherung gibt.

**`AEM Communities Extension`** wurde zuvor in AEM 6.0 Social Communities als Cloud-Dienst eingeführt. Ab AEM 6.1 Communities ist keine Cloud-Konfiguration erforderlich. Wählen Sie einfach ASRP aus der [Speicherkonfigurationskonsole](srp-config.md).

Aufgrund der neuen Speicherstruktur müssen Sie bei der Aktualisierung von Social Communities auf Communities die [Upgrade](upgrade.md#adobe-cloud-storage) -Anweisungen befolgen.

## Verwalten von Benutzerdaten {#managing-user-data}

Informationen zu *Benutzern*, *Benutzerprofilen* und *Benutzergruppen*, die häufig in der Veröffentlichungsumgebung eingegeben werden, finden Sie unter

* [Benutzersynchronisierung](sync.md)
* [Verwalten von Benutzern und Benutzergruppen](users.md)

## Fehlerbehebung {#troubleshooting}

### UGC wird nach der Aktualisierung ausgeblendet {#ugc-disappears-after-upgrade}

Wenn Sie ein Upgrade von einer vorhandenen AEM 6.0 Social Community-Site durchführen, befolgen Sie die [Upgrade-Anweisungen](upgrade.md#adobe-cloud-storage). Andernfalls *scheint* UGC verloren zu gehen.

### Authentifizierungsfehler {#authentication-errors}

Wenn beim Empfang von Authentifizierungsfehlern für die Data Center-URL die Datei &quot;AEM error.log&quot;Meldungen über statische Zeitstempel enthält, überprüfen Sie, ob eine Zeitsynchronisierung stattfindet.

Es wird empfohlen, ein Tool wie das [Network Time Protocol (NTP)](https://www.ntp.org/) zu verwenden, um alle AEM-Autor- und -Veröffentlichungsserver zeitlich zu synchronisieren.

### Neue Inhalte werden in Suchvorgängen nicht angezeigt {#new-content-does-not-appear-in-searches}

Die Adobe Cloud-Speicherinfrastruktur verwendet *letztendlich Konsistenz* , um die Skalierungs- und Leistungsziele zu erreichen. Aus diesem Grund sind neue Inhalte nicht sofort verfügbar und es kann einige Sekunden dauern, bis sie in den Suchergebnissen angezeigt werden.

Während das Intervall, das sich auf die spätere Konsistenz auswirkt, überwacht wird, wenden Sie sich an Ihren Kundenbetreuer, wenn es länger als ein paar Sekunden dauert, bis neue Inhalte in Suchvorgängen angezeigt werden.

### UGC in ASRP nicht sichtbar {#ugc-not-visible-in-asrp}

Vergewissern Sie sich, dass ASRP als Standardanbieter konfiguriert wurde, indem Sie die Konfiguration der Speicheroption überprüfen. Standardmäßig ist der Speicherressourcenanbieter JSRP, nicht ASRP.

Gehen Sie bei allen Autoren- und Veröffentlichungsinstanzen von AEM erneut zur Speicherkonfigurationskonsole oder überprüfen Sie das AEM-Repository:

* In JCR, if [/etc/socialconfig](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/)

   * Enthält keinen [srpc](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc) -Knoten, d. h. der Speicheranbieter ist JSRP
   * Wenn der Knoten srpc vorhanden ist und die Node- [Standardkonfiguration](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc/defaultconfiguration)enthält, sollten die Eigenschaften der Standardkonfiguration ASRP als Standardanbieter definieren

