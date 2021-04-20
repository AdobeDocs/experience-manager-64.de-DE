---
title: JSRP - JCR Datenspeicherung Resource Provider
seo-title: JSRP - JCR Datenspeicherung Resource Provider
description: JSRP eignet sich im Allgemeinen am besten für Demonstrations- oder Entwicklungs-Umgebung einer Instanz im Veröffentlichungsmodus und einer Instanz im Autorenmodus
seo-description: JSRP eignet sich im Allgemeinen am besten für Demonstrations- oder Entwicklungs-Umgebung einer Instanz im Veröffentlichungsmodus und einer Instanz im Autorenmodus
uuid: 358a43c1-4137-4300-8443-c0d7166968ad
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: f5316a73-84e2-4a18-98c1-a384eeaa77cf
role: Administrator
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 2%

---


# JSRP - JCR Datenspeicherung Resource Provider {#jsrp-jcr-storage-resource-provider}

## Über JSRP {#about-jsrp}

Wenn AEM Communities JSRP als Standardoption für die Datenspeicherung verwendet, werden Community-Inhalte in JCR gespeichert und benutzerdefinierte Inhalte (UGC) können nur von der Autor- oder Veröffentlichungsinstanz aufgerufen werden, in der sie veröffentlicht wurden.

Aufgrund der einfachen Bereitstellung ist JSRP im Allgemeinen am besten für Demonstrations- oder Entwicklungs-Umgebung einer Veröffentlichungsinstanz und einer Autoreninstanz geeignet.

Siehe auch [Eigenschaften der SRP-Optionen](working-with-srp.md#characteristics-of-srp-options) und [Empfohlene Topologien](topologies.md).

## Konfiguration {#configuration}

### JSRP {#select-jsrp}

Standardmäßig ist JSRP die Datenspeicherung-Option für UGC.

Die [Datenspeicherung Configuration Console](srp-config.md) ermöglicht die Auswahl der Standardkonfiguration der Datenspeicherung, die die zu verwendende Implementierung von SRP identifiziert.

In der Umgebung &quot;author&quot;zur Datenspeicherung Configuration Console

* Aus globaler Navigation: **[!UICONTROL Tools > Communities > Datenspeicherung Configuration]**

![chlimage_1-234](assets/chlimage_1-234.png)

* Wählen Sie **[!UICONTROL JCR Datenspeicherung Resource Provider (JSRP)]**
* Klicken Sie auf **[!UICONTROL Übermitteln]**

### Veröffentlichen der Konfiguration {#publishing-the-configuration}

Während JSRP die Standardkonfiguration ist, stellen Sie sicher, dass die gleiche Konfiguration in der Umgebung &quot;Veröffentlichen&quot;festgelegt ist:

* Beim Autor:

   * Aus globaler Navigation: **[!UICONTROL Tools > Bereitstellung > Replikation]**
   * Wählen Sie **[!UICONTROL Baum aktivieren]**
   * **[!UICONTROL Startpfad]**:

      * Gehen Sie zu `/conf/global/settings/community/srpc/`
   * Wählen Sie **[!UICONTROL Aktivieren]**


## Verwalten von Benutzerdaten {#managing-user-data}

Informationen zu *Benutzergruppen*, *Benutzergruppen* und *die häufig in die Umgebung &quot;Veröffentlichen&quot;eingegeben wurden, finden Sie unter*

* [Benutzersynchronisierung](sync.md)
* [Verwalten von Benutzern und Benutzergruppen](users.md)

## Fehlerbehebung {#troubleshooting}

### UGC in JCR {#ugc-not-visible-in-jcr} nicht sichtbar

Vergewissern Sie sich, dass JSRP als Standardanbieter konfiguriert wurde, indem Sie die Konfigurationsoption der Datenspeicherung überprüfen. Standardmäßig ist der Datenspeicherung Resource Provider JSRP.

Rufen Sie auf allen Instanzen im Autorenmodus und AEM Veröffentlichungsmodus erneut die Datenspeicherung Configuration Console auf oder überprüfen Sie das AEM Repository:

* in JCR, wenn [/conf/global/settings/community](http://localhost:4502/crx/de/index.jsp#/conf/global/settings/community)

   * Enthält keinen Knoten [srpc](http://localhost:4502/crx/de/index.jsp#/conf/global/settings/community/srpc), d. h., der Anbieter der Datenspeicherung ist JSRP
   * Wenn der Knoten srpc vorhanden ist und den Knoten [defaultConfiguration](http://localhost:4502/crx/de/index.jsp#/conf/global/settings/community/srpc/defaultconfiguration) enthält, sollten die Eigenschaften der Standardkonfiguration JSRP als Standardanbieter definieren

### UGC auf Autoreninstanz {#ugc-not-visible-on-author-instance} nicht sichtbar

Das ist kein Fehler. Charakteristisch für JSRP ist, dass in der Umgebung &quot;Veröffentlichen&quot;eingegebene Community-Inhalte nur in der Umgebung &quot;Veröffentlichen&quot;sichtbar sind.

### UGC in Veröffentlichungsinstanz {#ugc-not-visible-on-publish-instance} nicht sichtbar

Wenn eine einzelne Veröffentlichungsinstanz oder ein Veröffentlichungscluster bereitgestellt ist, befolgen Sie die Anweisungen für [UGC nicht sichtbar in JCR](#ugc-not-visible-in-jcr).

Wenn eine Veröffentlichungsfarm bereitgestellt wird, ist ein Merkmal von JSRP, dass Community-Inhalte nur auf der Veröffentlichungsinstanz sichtbar sind, auf der sie veröffentlicht wurden.

Damit UGC von jeder Veröffentlichungsinstanz aus sichtbar sein kann, ist ein Veröffentlichungscluster erforderlich.
