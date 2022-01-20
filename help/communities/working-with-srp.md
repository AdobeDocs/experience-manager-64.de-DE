---
title: SRP - Community-Inhaltsspeicherung
seo-title: SRP - Community Content Storage
description: Ab AEM Communities 6.1 werden benutzergenerierte Inhalte in einem einzigen, gemeinsamen Speicher gespeichert, der von einem Speicherressourcenanbieter (SRP) bereitgestellt wird
seo-description: As of AEM Communities 6.1, user generated content (UGC) is stored in a single, common store provided by a storage resource provider (SRP)
uuid: 651af1d7-70e8-4b56-8c01-871cb397678e
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: e975e026-e815-4445-be3e-b1237ed3f6b2
role: Admin
exl-id: 4ff530ae-c676-4259-86f2-a3881843b642
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '896'
ht-degree: 0%

---

# SRP - Community-Inhaltsspeicherung {#srp-community-content-storage}

## Einführung {#introduction}

Ab AEM Communities 6.1 werden benutzergenerierte Inhalte (UGC) in einem einzigen, gemeinsamen Speicher gespeichert, der von einem Speicherressourcenanbieter (SRP) bereitgestellt wird. Es gibt verschiedene SRP-Optionen, aus denen Sie wählen können, z. B. ASRP, MSRP und JSRP.

Im Gegensatz zu früheren Versionen gibt es keine Reverse/Forward-Replikation von UGC über AEM Instanzen hinweg. Stattdessen ermöglicht das SRP die direkte Zugänglichkeit von UGC für CRUD-Vorgänge (Create, Read, Update, Delete, Erstellen, Aktualisieren und Löschen) in allen Autoren- und Veröffentlichungsinstanzen, mit Ausnahme von JSRP.

Im Folgenden finden Sie die [Merkmale der einzelnen SRP-Optionen](#characteristics-of-srp-options), die für den Entscheidungsprozess bei der Auswahl des geeigneten SRP von entscheidender Bedeutung ist, und [zugrunde liegende Implementierung](topologies.md).

Weitere Informationen zur Verwendung von SRP für UGC finden Sie unter [Übersicht über den Speicheranbieter](srp.md).

>[!NOTE]
>
>SRP gilt nur für Community-Inhalte. Sie hat keine Auswirkungen darauf, wo Site-Inhalte gespeichert werden ([Knotenspeicher](../../help/sites-deploying/data-store-config.md)) und betrifft nicht die sichere Handhabung von Benutzerregistrierung, Benutzerprofilen und Benutzergruppen zwischen AEM Instanzen (siehe auch [Verwalten von Benutzerdaten](#managing-user-data)).

>[!CAUTION]
>
>Ab AEM 6.1 [UGC wird nie repliziert](#ugc-never-replicated).
>
>Wenn die Bereitstellung keinen gemeinsamen Speicher enthält, z. B. die Standardeinstellung [JSRP](topologies.md#jsrp) -Topologie, wird UGC nur in der AEM- oder Autoreninstanz angezeigt, in der sie eingegeben wurde. Nur wenn die Topologie einen Veröffentlichungs-Cluster enthält, ist der UGC in jeder Veröffentlichungsinstanz sichtbar.

## Eigenschaften der SRP-Optionen {#characteristics-of-srp-options}

[ASRP - Adobe Storage Resource Provider](asrp.md)\
Mit dieser Option wird der benutzergenerierte Inhalt remote in einem von Adobe gehosteten und verwalteten Cloud-Service persistiert. Es erfordert eine zusätzliche Lizenz und die Zusammenarbeit mit einem Kundenbetreuer, um das Konto für diese spezifische Lizenz bereitzustellen.

* Erfordert einen zugehörigen Cloud-Service, der von Adobe bereitgestellt und unterstützt wird, um Community-Inhalte zu speichern
* Erfordert die Auswahl eines Rechenzentrums in einem bestimmten geografischen Gebiet (USA, EMEA, APAC)
* Erfordert den gesamten programmatischen Zugriff auf UGC über die SRP-API
* Geeignet für TarMK-Veröffentlichungsfarm
* Geeignet, wenn nicht beabsichtigt ist, in lokale Lagerhaltung zu investieren

>[!NOTE]
>
>Das Hochladen von Anhängen zu Beiträgen (oder Kommentaren) in ASRP ist auf 50 MB beschränkt.

[MSRP - MongoDB Storage Resource Provider](msrp.md)\
Mit dieser Option wird der benutzergenerierte Inhalt direkt in einer lokalen MongoDB-Instanz beibehalten.

* Erfordert eine lokale lizenzierte Installation von MongoDB zum Speichern von Community-Inhalten
* Erfordert eine lokale Installation von Apache Solr
* Erfordert den gesamten programmatischen Zugriff auf UGC über die SRP-API
* Geeignet für eine vorhandene TarMK-Veröffentlichungsfarm
* Geeignet für einen MongoMK- oder RdbMK-Cluster
* Geeignet für die Erwartung großer Mengen von Community-Inhalten

[DSRP - Resource Provider für relationale Datenbankspeicher](dsrp.md)\
Mit dieser Option wird der benutzergenerierte Inhalt direkt in einer lokalen MySQL-Datenbankinstanz beibehalten.

* Erfordert eine lokale Installation von MySQL zum Speichern von Community-Inhalten
* Erfordert eine lokale Installation von Apache Solr
* Erfordert den gesamten programmatischen Zugriff auf UGC über die SRP-API
* Geeignet für eine vorhandene TarMK-Veröffentlichungsfarm
* Geeignet für einen MongoMK- oder RdbMK-Cluster
* Geeignet für die Erwartung großer Mengen von Community-Inhalten

[JSRP - JCR Storage Resource Provider](jsrp.md)\
Mit der Standardoption gibt es keinen gemeinsamen Speicher. Der UGC wird nur im selben JCR-Repository beibehalten wie die AEM Instanz, in der er eingegeben wurde.

* Speichert Community-Inhalte im JCR-Repository der AEM Autoren- oder Veröffentlichungsinstanz, in der sie veröffentlicht wurde
* Erfordert den gesamten programmatischen Zugriff auf UGC über die SRP-API
* Erfordert einen Veröffentlichungscluster, wenn mehr als eine Veröffentlichungsinstanz bereitgestellt wird (es gibt keinen Replikationsmechanismus zwischen Veröffentlichungsinstanzen in einer TarMK-Farm)
* Die Moderation wird nur in der Veröffentlichungsumgebung durchgeführt (es gibt keinen Rückwärts-/Vorwärts-Replikationsmechanismus zwischen Autor und Veröffentlichung)
* Allgemein am besten für Entwicklung, Demonstrationen und Schulung

## Konfigurieren von SRP {#configuring-srp}

Die Angabe der standardmäßigen Speicheroption, die auf der zugrunde liegenden Bereitstellung basiert, erfolgt über das [Speicherkonfigurationskonsole](srp-config.md).

Informationen zur Konfiguration der einzelnen Optionen finden Sie unter:

* [ASRP - Adobe Storage Resource Provider](asrp.md)
* [MSRP - MongoDB Storage Resource Provider](msrp.md)
* [DSRP - Resource Provider für relationale Datenbankspeicher](dsrp.md)
* [JSRP - JCR Storage Resource Provider](jsrp.md)

Wenn keine Speicheroption aktiv ausgewählt ist, ist JSRP standardmäßig aktiviert.

## Zusätzliche Informationen {#additional-information}

### Nie replizierte benutzergenerische Inhalte {#ugc-never-replicated}

In der Autorenumgebung erstellt ein Autor Seiteninhalte und repliziert sie in der Veröffentlichungsumgebung. Wenn eine Seite eine interaktive AEM Communities-Funktion enthält, z. B. Kommentare, Rezensionen, Foren, Blog oder Fragen und Antworten, führt die Interaktion von Mitgliedern (die bei Site-Besuchern angemeldet sind) mit einer Veröffentlichungsinstanz dazu, dass benutzergenerierte Inhalte (UGC) in die Veröffentlichungsumgebung eingegeben werden.

Zuvor wurde dieser Community-Inhalt rückwärts auf Autoreninstanzen repliziert und von der Autoreninstanz auf Veröffentlichungsinstanzen repliziert. Es war problematisch, die Konsistenz zwischen AEM Instanzen mit der Rückwärts- und Vorwärtsreplikation zu wahren.

Ab AEM Communities 6.1 entfällt die Notwendigkeit der Replikation von benutzergenerierten Inhalten durch die Verwendung von freigegebenem Speicher für benutzergenerierte Inhalte (wie oben beschrieben).

Während Site-Inhalte repliziert werden, werden benutzergenerierte Inhalte nie repliziert.

### Verwalten von Benutzerdaten {#managing-user-data}

Auch die Kommunen sind von Interesse [*Benutzer*, *Benutzergruppen* und *Benutzerprofile*](users.md). Diese benutzerbezogenen Daten, die in der Veröffentlichungsumgebung erstellt und aktualisiert werden, müssen anderen Veröffentlichungsinstanzen zur Verfügung gestellt werden, wenn die Topologie eine [Veröffentlichungsfarm](../../help/sites-deploying/recommended-deploys.md#tarmk-farm).

Ab AEM Communities 6.1 werden benutzerbezogene Daten mithilfe der Sling-Verteilung anstatt der Replikation synchronisiert. Weitere Informationen finden Sie unter [Benutzersynchronisierung](sync.md).

### Upgrade auf AEM Communities 6.2 {#upgrading-to-aem-communities}

Wenn bei der Aktualisierung auf AEM Communities 6.3 bereits vorhandene benutzergenerierte Inhalte beibehalten werden müssen, sollten Schritte unternommen werden, je nachdem, ob die AEM 5.6.1 oder AEM 6.0 Community die On-Demand-Adobe oder die On-Premise-Speicherung von benutzergenerierten Inhalten verwendet hat.

Weitere Informationen finden Sie unter [Upgrade auf AEM Communities 6.3](upgrade.md).
