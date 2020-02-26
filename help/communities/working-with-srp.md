---
title: SRP - Gemeinschaftlicher Inhaltsspeicher
seo-title: SRP - Gemeinschaftlicher Inhaltsspeicher
description: Ab AEM Communities 6.1 werden benutzergenerierte Inhalte (UGC) in einem einzigen gemeinsamen Speicher gespeichert, der von einem Speicherressourcenanbieter (SRP) bereitgestellt wird
seo-description: Ab AEM Communities 6.1 werden benutzergenerierte Inhalte (UGC) in einem einzigen gemeinsamen Speicher gespeichert, der von einem Speicherressourcenanbieter (SRP) bereitgestellt wird
uuid: 651af1d7-70e8-4b56-8c01-871cb397678e
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: e975e026-e815-4445-be3e-b1237ed3f6b2
translation-type: tm+mt
source-git-commit: 8f169bb9b015ae94b9160d3ebbbd1abf85610465

---


# SRP - Gemeinschaftlicher Inhaltsspeicher {#srp-community-content-storage}

## Einführung {#introduction}

Ab AEM Communities 6.1 werden benutzergenerierte Inhalte (UGC) in einem einzigen, von einem Speicherressourcenanbieter (SRP) bereitgestellten gemeinsamen Speicher gespeichert. Es stehen verschiedene SRP-Optionen zur Auswahl, z. B. ASRP, MSRP und JSRP.

Im Gegensatz zu früheren Versionen gibt es keine Reverse/Forward-Replizierung von UGC in AEM-Instanzen. Stattdessen macht der SRP UGC-Vorgänge für das Erstellen, Lesen, Aktualisieren und Löschen (CRUD) von allen Autoren- und Veröffentlichungsinstanzen mit Ausnahme von JSRP direkt zugänglich.

Im Folgenden sind die [Merkmale jeder einzelnen SRP-Option](#characteristics-of-srp-options)aufgeführt, die für den Entscheidungsprozess bei der Auswahl des geeigneten SRP und der [zugrunde liegenden Bereitstellung](topologies.md)von entscheidender Bedeutung ist.

Weitere Informationen zur Verwendung von SRP für UGC finden Sie unter Übersicht über den [Speicherressourcen-Provider](srp.md).

>[!NOTE]
>
>SRP gilt nur für Community-Inhalte. Sie hat keine Auswirkungen auf den Speicherort des Site-Inhalts ([Knotenspeicher](../../help/sites-deploying/data-store-config.md)) und hat keine Auswirkungen auf die sichere Verarbeitung von Benutzerregistrierung, Benutzerprofilen und Benutzergruppen zwischen AEM-Instanzen (siehe auch [Verwalten von Benutzerdaten](#managing-user-data)).

>[!CAUTION]
>
>Ab AEM 6.1 wird [UGC nie repliziert](#ugc-never-replicated).
>
>Wenn die Bereitstellung keinen gemeinsamen Store enthält, z. B. die standardmäßige [JSRP](topologies.md#jsrp) -Topologie, ist UGC nur auf der AEM-Veröffentlichungs- oder Autoreninstanz sichtbar, auf der sie eingegeben wurde. Nur wenn die Topologie einen Veröffentlichungscluster enthält, ist das UGC in jeder Veröffentlichungsinstanz sichtbar.

## Merkmale der SRP-Optionen {#characteristics-of-srp-options}

[ASRP - Adobe Storage Resource Provider](asrp.md)\
Mit dieser Option wird der UGC remote in einem Cloud-Dienst, der von Adobe gehostet und verwaltet wird, beibehalten. Es erfordert eine zusätzliche Lizenz und arbeitet mit einem Kundenbetreuer zusammen, um das Konto für diese spezifische Lizenz bereitzustellen.

* Erfordert einen verknüpften Cloud-Dienst, der von Adobe bereitgestellt und unterstützt wird, um Community-Inhalte zu speichern
* Erfordert die Auswahl eines Datenzentrums in einer bestimmten geografischen Region (USA, EMEA, APAC)
* Erfordert den programmatischen Zugriff auf UGC über die SRP API
* Geeignet für TarMK Veröffentlichungsfarm
* Geeignet, wenn keine Absicht besteht, in lokale Speicher zu investieren

>[!NOTE]
>
>Das Hochladen von Anlagen zu Beiträgen (oder Kommentaren) in ASRP ist auf 50 MB beschränkt.

[MSRP - MongoDB Storage Resource Provider](msrp.md)\
Mit dieser Option wird der UGC direkt in einer lokalen MongoDB-Instanz beibehalten.

* Erfordert eine lokale lizenzierte Installation von MongoDB zum Speichern von Community-Inhalten
* Erfordert eine lokale Installation von Apache Solr
* Erfordert den programmatischen Zugriff auf UGC über die SRP API
* Geeignet für einen vorhandenen TarMK-Veröffentlichungsbetrieb
* Geeignet für einen MongoMK- oder RdbMK-Cluster
* Geeignet für große Mengen von Community-Inhalten

[DSRP - Ressourcenanbieter für den relationalen Datenbankspeicher](dsrp.md)\
Mit dieser Option wird der UGC direkt in einer lokalen MySQL-Datenbankinstanz beibehalten.

* Zum Speichern von Community-Inhalten ist eine lokale Installation von MySQL erforderlich
* Erfordert eine lokale Installation von Apache Solr
* Erfordert den programmatischen Zugriff auf UGC über die SRP API
* Geeignet für einen vorhandenen TarMK-Veröffentlichungsbetrieb
* Geeignet für einen MongoMK- oder RdbMK-Cluster
* Geeignet für große Mengen von Community-Inhalten

[JSRP - JCR Storage Resource Provider](jsrp.md)\
Bei der Standardoption gibt es keinen gemeinsamen Speicher. Der UGC wird nur im selben JCR-Repository wie die AEM-Instanz, in der er eingegeben wurde, beibehalten.

* Speichert Community-Inhalte im JCR-Repository der AEM-Autoren- oder Veröffentlichungsinstanz, in der sie veröffentlicht wurden
* Erfordert den programmatischen Zugriff auf UGC über die SRP API
* Erfordert ein Veröffentlichungscluster, wenn mehr als eine Instanz im Veröffentlichungsmodus bereitgestellt wird (es gibt keinen Replizierungsmechanismus zwischen Veröffentlichungsinstanzen in einer TarMK-Farm)
* Die Moderation wird nur in der Veröffentlichungsumgebung durchgeführt (zwischen Autor und Veröffentlichung gibt es keinen Rückwärtsreplikationsmechanismus)
* Im Allgemeinen am besten für Entwicklung, Demonstrationen und Ausbildung

## Konfigurieren von SRP {#configuring-srp}

Die Standardspeicheroption wird basierend auf der zugrunde liegenden Bereitstellung über die [Speicherkonfigurationskonsole](srp-config.md)festgelegt.

Konfigurationsdetails zu den einzelnen Optionen finden Sie unter:

* [ASRP - Adobe Storage Resource Provider](asrp.md)
* [MSRP - MongoDB Storage Resource Provider](msrp.md)
* [DSRP - Ressourcenanbieter für den relationalen Datenbankspeicher](dsrp.md)
* [JSRP - JCR Storage Resource Provider](jsrp.md)

Wenn keine Speicheroption aktiv ausgewählt ist, ist JSRP standardmäßig aktiviert.

## Zusätzliche Informationen {#additional-information}

### UGC nie repliziert {#ugc-never-replicated}

In der Autorenumgebung erstellt ein Autor Seiteninhalte und repliziert sie in der Veröffentlichungsumgebung. Wenn eine Seite eine interaktive AEM Communities-Funktion wie Kommentare, Rezensionen, Forum, Blog oder QnA enthält, führt die Interaktion von Mitgliedern (die bei Site-Besuchern angemeldet sind) mit einer Veröffentlichungsinstanz dazu, dass benutzergenerierte Inhalte (UGC) in die Veröffentlichungsumgebung eingegeben werden.

Bisher wurde dieser Community-Inhalt umgekehrt in Autoreninstanzen repliziert und vom Autor in Veröffentlichungsinstanzen repliziert. Es war problematisch, die Konsistenz zwischen AEM-Instanzen mit der umgekehrten und weiterleitenden Replizierung aufrechtzuerhalten.

Ab AEM Communities 6.1 wurde die Notwendigkeit für die Replikation von UGC durch die Verwendung von freigegebenem Speicher für UGC wie oben beschrieben beseitigt.

Obwohl Site-Inhalte repliziert werden, wird UGC nie repliziert.

### Verwalten von Benutzerdaten {#managing-user-data}

Von Interesse sind auch [*Benutzer *,* Benutzergruppen *und* Benutzerprofile *](users.md). Wenn diese benutzerbezogenen Daten in der Veröffentlichungsumgebung erstellt und aktualisiert werden, müssen sie anderen Instanzen im Veröffentlichungsmodus zur Verfügung gestellt werden, wenn die Topologie eine[Veröffentlichungsfarm](../../help/sites-deploying/recommended-deploys.md#tarmk-farm)ist.

Ab AEM Communities 6.1 werden benutzerbezogene Daten mit der Sling-Distribution und nicht mit der Replikation synchronisiert. Weitere Informationen finden Sie unter [Benutzersynchronisierung](sync.md).

### Upgrading to AEM Communities 6.2 {#upgrading-to-aem-communities}

Wenn bei der Aktualisierung auf AEM Communities 6.3 bereits vorhandene UGC beibehalten werden müssen, sollten Schritte unternommen werden, je nachdem, ob die AEM 5.6.1- oder AEM 6.0-Community Adobe-On-Demand-Speicher oder lokalen Speicher von UGC verwendet hat.

Weitere Informationen finden Sie unter [Aktualisieren auf AEM Communities 6.3](upgrade.md).
