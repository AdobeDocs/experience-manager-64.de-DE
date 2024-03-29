---
title: JSRP - JCR Storage Resource Provider
seo-title: JSRP - JCR Storage Resource Provider
description: JSRP ist im Allgemeinen am besten für Demonstrations- oder Entwicklungsumgebungen in einer Veröffentlichungsinstanz und einer Autoreninstanz geeignet
seo-description: JSRP is generally best suited for demonstration or development environments of one publish instance and one author instance
uuid: 358a43c1-4137-4300-8443-c0d7166968ad
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: f5316a73-84e2-4a18-98c1-a384eeaa77cf
role: Admin
exl-id: 73c59497-43fe-4e15-afda-e3cf5264696e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 3%

---

# JSRP - JCR Storage Resource Provider {#jsrp-jcr-storage-resource-provider}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Über JSRP {#about-jsrp}

Wenn AEM Communities JSRP als Speicheroption (Standard) verwendet, werden Community-Inhalte in JCR gespeichert und benutzergenerierte Inhalte (UGC) können nur von der Autoren- oder Veröffentlichungsinstanz aufgerufen werden, in der sie veröffentlicht wurden.

Aufgrund der Einfachheit der Implementierung ist JSRP im Allgemeinen am besten für Demonstrations- oder Entwicklungsumgebungen einer Veröffentlichungsinstanz und einer Autoreninstanz geeignet.

Siehe auch [Eigenschaften der SRP-Optionen](working-with-srp.md#characteristics-of-srp-options) und [Empfohlene Topologien](topologies.md).

## Konfiguration {#configuration}

### JSRP auswählen {#select-jsrp}

Standardmäßig ist JSRP die Speicheroption für UGC.

Die [Speicherkonfigurationskonsole](srp-config.md) ermöglicht die Auswahl der standardmäßigen Speicherkonfiguration, die angibt, welche SRP-Implementierung verwendet werden soll.

Um in der Autorenumgebung auf die Speicherkonfigurationskonsole zuzugreifen

* Über die globale Navigation: **[!UICONTROL Tools > Communities > Speicherkonfiguration]**

![chlimage_1-234](assets/chlimage_1-234.png)

* Auswählen **[!UICONTROL JCR Storage Resource Provider (JSRP)]**
* Klicken Sie auf **[!UICONTROL Übermitteln]**

### Veröffentlichen der Konfiguration {#publishing-the-configuration}

Während JSRP die Standardkonfiguration ist, um sicherzustellen, dass die identische Konfiguration in der Veröffentlichungsumgebung festgelegt ist:

* Bei Autor:

   * Über die globale Navigation: **[!UICONTROL Tools > Bereitstellung > Replikation]**
   * Auswählen **[!UICONTROL Baum aktivieren]**
   * **[!UICONTROL Startpfad]**:

      * Navigieren Sie zu `/conf/global/settings/community/srpc/`
   * Auswählen **[!UICONTROL Aktivieren]**


## Verwalten von Benutzerdaten {#managing-user-data}

Informationen über *Benutzer*, *Benutzerprofile* und *Benutzergruppen*, häufig in die Veröffentlichungsumgebung eingegeben, Besuch

* [Benutzersynchronisierung](sync.md)
* [Verwalten von Benutzern und Benutzergruppen](users.md)

## Fehlerbehebung {#troubleshooting}

### UGC nicht in JCR sichtbar {#ugc-not-visible-in-jcr}

Stellen Sie sicher, dass JSRP als Standardanbieter konfiguriert wurde, indem Sie die Konfiguration der Speicheroption aktivieren. Standardmäßig ist der Speicher-Ressourcenanbieter JSRP.

Rufen Sie auf allen Autoren- und Veröffentlichungsinstanzen AEM die Konsole Speicherkonfiguration erneut auf oder überprüfen Sie das AEM Repository:

* in JCR, wenn [/conf/global/settings/community](http://localhost:4502/crx/de/index.jsp#/conf/global/settings/community)

   * Enthält keine [srpc](http://localhost:4502/crx/de/index.jsp#/conf/global/settings/community/srpc) Knoten bedeutet, dass der Speicheranbieter JSRP ist.
   * Wenn der Knoten srpc vorhanden ist und den Knoten enthält [defaultconfiguration](http://localhost:4502/crx/de/index.jsp#/conf/global/settings/community/srpc/defaultconfiguration), sollten die Eigenschaften der Standardkonfiguration JSRP als Standardanbieter definieren

### UGC in Autoreninstanz nicht sichtbar {#ugc-not-visible-on-author-instance}

Das ist kein Fehler. Ein Merkmal von JSRP ist, dass in der Veröffentlichungsumgebung eingegebene Community-Inhalte nur in der Veröffentlichungsumgebung sichtbar sind.

### UGC in Veröffentlichungsinstanz nicht sichtbar {#ugc-not-visible-on-publish-instance}

Wenn eine einzelne Veröffentlichungsinstanz oder ein Veröffentlichungscluster bereitgestellt wird, befolgen Sie die Anweisungen für [UGC nicht in JCR sichtbar](#ugc-not-visible-in-jcr).

Wenn eine Veröffentlichungsfarm bereitgestellt wird, ist ein Merkmal von JSRP, dass Community-Inhalte nur auf der Veröffentlichungsinstanz sichtbar sind, auf der sie veröffentlicht wurde.

Damit UGC in jeder Veröffentlichungsinstanz sichtbar ist, ist ein Veröffentlichungscluster erforderlich.
