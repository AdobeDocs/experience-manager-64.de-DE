---
title: ASRP - Adobe Storage Resource Provider
seo-title: ASRP - Adobe Storage Resource Provider
description: Einrichten von AEM Communities zur Verwendung einer relationalen Datenbank als gemeinsamen Speicher
seo-description: Set up AEM Communities to use a relational database as its common store
uuid: 29826b44-633d-4586-8553-cd87ebe269a2
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 86349e4d-29ff-4baa-9fcd-c0ab1f0753e9
role: Admin
exl-id: 136c0913-c8b8-451d-bb28-3c3285c172a1
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '811'
ht-degree: 2%

---

# ASRP - Adobe Storage Resource Provider {#asrp-adobe-storage-resource-provider}

## Über ASRP {#about-asrp}

Wenn AEM Communities für die Verwendung von ASRP als gebräuchlicher Speicher konfiguriert ist, kann von allen Autoren- und Veröffentlichungsinstanzen auf benutzergenerierte Inhalte (UGC) zugegriffen werden, ohne dass eine Synchronisierung oder Replikation erforderlich ist.

Siehe auch [Eigenschaften der SRP-Optionen](working-with-srp.md#characteristics-of-srp-options) und [Empfohlene Topologien](topologies.md).

## Voraussetzungen {#requirements}

Für die Verwendung von ASRP ist eine zusätzliche Lizenz erforderlich.

Wenden Sie sich an Ihren Kundenbetreuer, um Ihre AEM Communities-Website für die Verwendung von ASRP für UGC zu konfigurieren:

* URL des Rechenzentrums (Adresse des ASRP-Endpunkts)
* Verbraucherschlüssel
* Geheimer Schlüssel
* Report Suite-ID(s)

Der Verbraucher- und der geheime Schlüssel werden für alle Report Suites eines Unternehmens freigegeben. Pro Mandant gibt es eine Report Suite.

## Konfiguration {#configuration}

### ASRP auswählen {#select-asrp}

Die [Speicherkonfigurationskonsole](srp-config.md) ermöglicht die Auswahl der standardmäßigen Speicherkonfiguration, die angibt, welche SRP-Implementierung verwendet werden soll.

**Beim Autor**:

* Über die globale Navigation: **[!UICONTROL Tools > Communities > Speicherkonfiguration]**

![chlimage_1-310](assets/chlimage_1-310.png)

* Auswählen **[!UICONTROL Adobe Storage Resource Provider (ASRP)]**
* Die folgenden Informationen stammen aus dem Bereitstellungsprozess

   * **[!UICONTROL Datenzentrum-URL]**

      Pulldown zur Auswahl des Produktionsdatencenters, das von Ihrem Kundenbetreuer identifiziert wird

   * **[!UICONTROL Standard-Berichtssuite]**

      Geben Sie den Namen der Standard-Report Suite ein

   * **[!UICONTROL Verbraucherschlüssel]**

      Consumer-Schlüssel eingeben

   * **[!UICONTROL Geheimnis]**

      Geheimschlüssel eingeben

* Klicken Sie auf **[!UICONTROL Übermitteln]**

Bereiten Sie die Veröffentlichungsinstanzen vor:

* [Replizieren des Kryptoschlüssels](#replicate-the-crypto-key)
* [Konfiguration replizieren](#publishing-the-configuration)

Testen Sie nach dem Senden der Konfiguration die Verbindung:

* Auswählen **[!UICONTROL Testkonfiguration]**
für jede Autoren- und Veröffentlichungsinstanz die Verbindung zum Rechenzentrum über die Konsole Speicherkonfiguration testen

* Stellen Sie abschließend sicher, dass die Site-URLs für Profildaten vom Data Center routbar sind durch [Externalisieren von Links](#externalize-links).

### Replizieren des Crypto-Schlüssels {#replicate-the-crypto-key}

Der Consumer Key und der Secret Key sind verschlüsselt. Damit die Schlüssel ordnungsgemäß verschlüsselt/entschlüsselt werden können, muss der primäre Granite-Crypto-Schlüssel auf allen AEM Instanzen gleich sein.

Befolgen Sie die Anweisungen unter [Replizieren des Crypto-Schlüssels](deploy-communities.md#replicate-the-crypto-key).

### Externe Links {#externalize-links}

Stellen Sie für korrekte Profil- und Profilbildlinks sicher, dass [Link Externalizer konfigurieren](../../help/sites-developing/externalizer.md).

Stellen Sie sicher, dass die Domänen URLs sind, die über die Data Center URL (ASRP-Endpunkt) routbar sind.

### Zeitsynchronisierung {#time-synchronization}

Damit die Authentifizierung mit dem ASRP-Endpunkt erfolgreich ist, müssen die Computer, auf denen Ihr gehosteter AEM Communities ausgeführt wird, zeitsynchronisiert sein, z. B. mit dem [Network Time Protocol (NTP)](https://www.ntp.org/).

### Veröffentlichen der Konfiguration {#publishing-the-configuration}

ASRP muss in allen Autoren- und Veröffentlichungsinstanzen als gemeinsamer Speicher identifiziert werden.

So stellen Sie die identische Konfiguration in der Veröffentlichungsumgebung zur Verfügung:

* **Beim Autor**:

   * Navigieren Sie vom Hauptmenü zu **[!UICONTROL Tools > Vorgänge > Replikation]**
   * Auswählen **[!UICONTROL Baum aktivieren]**
   * **[!UICONTROL Startpfad]**:

      * Navigieren Sie zu `/etc/socialconfig/srpc/`
   * Deaktivieren **[!UICONTROL Nur geändert]**
   * Auswählen **[!UICONTROL Aktivieren]**


## Upgrade von AEM 6.0 {#upgrading-from-aem}

>[!CAUTION]
>
>Wenn Sie ASRP auf einer veröffentlichten Community-Site aktivieren, werden alle bereits in gespeicherten UGCs [JCR](jsrp.md) wird nicht mehr angezeigt, da keine Synchronisierung der Daten zwischen On-Premise-Speicher und Cloud-Speicher erfolgt.

**`AEM Communities Extension`** wurde zuvor in AEM 6.0 Social Communities als Cloud Service eingeführt. Ab AEM 6.1 Communities ist keine Cloud-Konfiguration erforderlich. Wählen Sie einfach ASRP aus der [Speicherkonfigurationskonsole](srp-config.md).

Aufgrund der neuen Speicherstruktur ist es erforderlich, die [Upgrade](upgrade.md#adobe-cloud-storage) Anweisungen für die Aktualisierung von Social Communities auf Communities.

## Verwalten von Benutzerdaten {#managing-user-data}

Informationen über *Benutzer*, *Benutzerprofile* und *Benutzergruppen*, häufig in die Veröffentlichungsumgebung eingegeben, Besuch

* [Benutzersynchronisierung](sync.md)
* [Verwalten von Benutzern und Benutzergruppen](users.md)

## Fehlerbehebung {#troubleshooting}

### UGC verschwindet nach der Aktualisierung {#ugc-disappears-after-upgrade}

Wenn Sie von einer vorhandenen AEM 6.0 Social Community-Site aktualisieren, folgen Sie dem [Upgrade-Anweisungen](upgrade.md#adobe-cloud-storage), andernfalls wird UGC *Anzeige* verloren.

### Authentifizierungsfehler {#authentication-errors}

Wenn Authentifizierungsfehler für die Data Center-URL empfangen und die AEM error.log Meldungen zu veralteten Zeitstempeln enthält, überprüfen Sie, ob eine Zeitsynchronisierung stattfindet.

Es wird empfohlen, ein Tool wie das [Network Time Protocol (NTP)](https://www.ntp.org/) , um alle AEM Autoren- und Veröffentlichungsserver zu synchronisieren.

### Neue Inhalte werden nicht in Suchvorgängen angezeigt {#new-content-does-not-appear-in-searches}

Die Cloud-Speicher-Infrastruktur der Adobe verwendet *Konsistenz* , um die Skalierung und Leistungsziele zu erreichen. Aus diesem Grund sind neue Inhalte nicht sofort verfügbar und es kann mehrere Sekunden dauern, bis sie in den Suchergebnissen angezeigt werden.

Während das Intervall, das sich auf die Konsistenz auswirkt, überwacht wird, wenden Sie sich an Ihren Kundenbetreuer, wenn es länger als ein paar Sekunden dauert, bis neue Inhalte bei Suchvorgängen angezeigt werden.

### UGC in ASRP nicht sichtbar {#ugc-not-visible-in-asrp}

Stellen Sie sicher, dass ASRP als Standardanbieter konfiguriert wurde, indem Sie die Konfiguration der Speicheroption aktivieren. Standardmäßig ist der Speicherressourcenanbieter JSRP, nicht ASRP.

Rufen Sie auf allen Autoren- und Veröffentlichungsinstanzen AEM die Konsole Speicherkonfiguration erneut auf oder überprüfen Sie das AEM Repository:

* Wenn in JCR [/etc/socialconfig](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/)

   * Enthält keine [srpc](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc) Knoten bedeutet, dass der Speicheranbieter JSRP ist.
   * Wenn der Knoten srpc vorhanden ist und den Knoten enthält [defaultconfiguration](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc/defaultconfiguration), sollten die Eigenschaften der Standardkonfiguration ASRP als Standardanbieter definieren
