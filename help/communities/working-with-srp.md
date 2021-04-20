---
title: SRP - Community Content Datenspeicherung
seo-title: SRP - Community Content Datenspeicherung
description: Ab AEM Communities 6.1 werden benutzergenerierte Inhalte (UGC) in einem gemeinsamen Speicher gespeichert, der von einem Datenspeicherung Resource Provider (SRP) bereitgestellt wird
seo-description: Ab AEM Communities 6.1 werden benutzergenerierte Inhalte (UGC) in einem gemeinsamen Speicher gespeichert, der von einem Datenspeicherung Resource Provider (SRP) bereitgestellt wird
uuid: 651af1d7-70e8-4b56-8c01-871cb397678e
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: e975e026-e815-4445-be3e-b1237ed3f6b2
role: Administrator
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '923'
ht-degree: 0%

---


# SRP - Community Content Datenspeicherung {#srp-community-content-storage}

## Einführung {#introduction}

Ab AEM Communities 6.1 werden benutzergenerierte Inhalte (UGC) in einem gemeinsamen Speicher gespeichert, der von einem Datenspeicherung Resource Provider (SRP) bereitgestellt wird. Es stehen verschiedene SRP-Optionen zur Auswahl, z. B. ASRP, MSRP und JSRP.

Im Gegensatz zu früheren Versionen gibt es keine Reverse/Forward-Replizierung von UGC über AEM Instanzen hinweg. Stattdessen macht der SRP UGC-Vorgänge für das Erstellen, Lesen, Aktualisieren und Löschen (CRUD) von allen Autoren- und Veröffentlichungsinstanzen mit Ausnahme von JSRP direkt zugänglich.

Im Folgenden finden Sie die [Eigenschaften jeder SRP-Option](#characteristics-of-srp-options), die für den Entscheidungsprozess bei der Auswahl des entsprechenden SRP und [zugrunde liegenden Bereitstellung](topologies.md) entscheidende Informationen sind.

Weitere Informationen zur Verwendung von SRP für UGC finden Sie unter [Übersicht über den Ressourcenanbieter der Datenspeicherung](srp.md).

>[!NOTE]
>
>SRP gilt nur für Community-Inhalte. Sie hat keine Auswirkungen auf die Speicherorte von Site-Inhalten ([node store](../../help/sites-deploying/data-store-config.md)) und hat keine Auswirkungen auf die sichere Verarbeitung von Benutzerregistrierung, Profilen und Benutzergruppen zwischen AEM Instanzen (siehe auch [Verwalten von Benutzerdaten](#managing-user-data)).

>[!CAUTION]
>
>Ab AEM 6.1 wird [UGC nie repliziert](#ugc-never-replicated).
>
>Wenn die Bereitstellung keinen gemeinsamen Speicher enthält, z. B. die Standardtopologie [JSRP](topologies.md#jsrp), ist UGC nur in der AEM- oder Autoreninstanz sichtbar, in der sie eingegeben wurde. Nur wenn die Topologie einen Veröffentlichungscluster enthält, ist das UGC in jeder Veröffentlichungsinstanz sichtbar.

## Merkmale der SRP-Optionen {#characteristics-of-srp-options}

[ASRP - Adobe Datenspeicherung Resource Provider](asrp.md)\
Bei dieser Option wird der UGC remote in einem Cloud-Dienst, der von der Adobe gehostet und verwaltet wird, beibehalten. Es erfordert eine zusätzliche Lizenz und arbeitet mit einem Kundenbetreuer zusammen, um das Konto für diese spezifische Lizenz bereitzustellen.

* Erfordert einen verknüpften Cloud-Dienst, der von der Adobe bereitgestellt und unterstützt wird, um Community-Inhalte zu speichern
* Erfordert die Auswahl eines Datenzentrums in einer bestimmten geografischen Region (USA, EMEA, APAC)
* Erfordert den programmatischen Zugriff auf UGC über die SRP API
* Geeignet für TarMK-Veröffentlichungsfarm
* Geeignet, wenn keine Absicht besteht, in lokale Datenspeicherung zu investieren

>[!NOTE]
>
>Das Hochladen von Anlagen zu Beiträgen (oder Kommentaren) in ASRP ist auf 50 MB beschränkt.

[MSRP - MongoDB Datenspeicherung Resource Provider](msrp.md)\
Mit dieser Option wird der UGC direkt in einer lokalen MongoDB-Instanz beibehalten.

* Erfordert eine lokale lizenzierte Installation von MongoDB zum Speichern von Community-Inhalten
* Erfordert eine lokale Installation von Apache Solr
* Erfordert den programmatischen Zugriff auf UGC über die SRP API
* Geeignet für einen vorhandenen TarMK-Veröffentlichungsbetrieb
* Eignet sich für einen MongoMK- oder RdbMK-Cluster
* Geeignet für große Mengen von Community-Inhalten

[DSRP - Ressourcenanbieter für relationale Datenspeicherung](dsrp.md)\
Mit dieser Option wird der UGC direkt in einer lokalen MySQL-Datenbankinstanz beibehalten.

* Zum Speichern von Community-Inhalten ist eine lokale Installation von MySQL erforderlich
* Erfordert eine lokale Installation von Apache Solr
* Erfordert den programmatischen Zugriff auf UGC über die SRP API
* Geeignet für einen vorhandenen TarMK-Veröffentlichungsbetrieb
* Eignet sich für einen MongoMK- oder RdbMK-Cluster
* Geeignet für große Mengen von Community-Inhalten

[JSRP - JCR Datenspeicherung Resource Provider](jsrp.md)\
Bei der Standardoption gibt es keinen gemeinsamen Speicher. Die UGC wird nur im selben JCR-Repository wie die AEM Instanz, in der sie eingegeben wurde, beibehalten.

* Speichert Community-Inhalte im JCR-Repository der AEM Autoren- oder Veröffentlichungsinstanz, in der sie veröffentlicht wurden
* Erfordert den programmatischen Zugriff auf UGC über die SRP API
* Erfordert ein Veröffentlichungscluster, wenn mehr als eine Instanz im Veröffentlichungsmodus bereitgestellt wird (es gibt keinen Replizierungsmechanismus zwischen Veröffentlichungsinstanzen in einer TarMK-Farm)
* Die Moderation wird nur in der Umgebung &quot;Veröffentlichen&quot;durchgeführt (zwischen Autor und Veröffentlichung gibt es keinen Rückwärtsreplikationsmechanismus)
* Im Allgemeinen am besten für Entwicklung, Demonstrationen und Ausbildung

## Konfigurieren von SRP {#configuring-srp}

Die Standardoption für die Datenspeicherung wird basierend auf der zugrunde liegenden Bereitstellung über die [Datenspeicherung Configuration Console](srp-config.md) festgelegt.

Konfigurationsdetails zu den einzelnen Optionen finden Sie unter:

* [ASRP - Adobe Datenspeicherung Resource Provider](asrp.md)
* [MSRP - MongoDB Datenspeicherung Resource Provider](msrp.md)
* [DSRP - Ressourcenanbieter für relationale Datenspeicherung](dsrp.md)
* [JSRP - JCR Datenspeicherung Resource Provider](jsrp.md)

Wenn keine Option &quot;Datenspeicherung&quot;aktiv ausgewählt ist, ist JSRP standardmäßig aktiviert.

## Zusätzliche Informationen {#additional-information}

### UGC nie repliziert {#ugc-never-replicated}

In der Umgebung &quot;Autor&quot;erstellt ein Autor Seiteninhalte und repliziert sie in der Umgebung &quot;Veröffentlichen&quot;. Wenn eine Seite eine interaktive AEM Communities-Funktion wie Kommentare, Rezensionen, Foren, Blog oder QnA enthält, führt die Interaktion (bei Site-Besuchern angemeldet) mit einer Veröffentlichungsinstanz dazu, dass benutzergenerierte Inhalte (UGC) in die Umgebung &quot;Veröffentlichen&quot;eingegeben werden.

Bisher wurde dieser Community-Inhalt umgekehrt in Autoreninstanzen repliziert und vom Autor in Veröffentlichungsinstanzen repliziert. Es war problematisch, die Konsistenz zwischen AEM Instanzen mit der umgekehrten und weiterleitenden Replizierung aufrechtzuerhalten.

Ab AEM Communities 6.1 entfällt die Notwendigkeit für die Replikation von UGC durch die Verwendung von freigegebener Datenspeicherung für UGC, wie oben beschrieben.

Obwohl Site-Inhalte repliziert werden, wird UGC nie repliziert.

### Verwalten von Benutzerdaten {#managing-user-data}

Für Communities sind außerdem [*user*, *user groups* und *user Profils*](users.md) von Interesse. Wenn diese benutzerbezogenen Daten in der Umgebung &quot;Veröffentlichen&quot;erstellt und aktualisiert werden, müssen sie anderen Instanzen im Veröffentlichungsmodus zur Verfügung gestellt werden, wenn die Topologie eine [Veröffentlichungsfarm](../../help/sites-deploying/recommended-deploys.md#tarmk-farm) ist.

Ab AEM Communities 6.1 werden benutzerbezogene Daten mit der Sling-Distribution und nicht mit der Replikation synchronisiert. Weitere Informationen finden Sie unter [Benutzersynchronisierung](sync.md).

### Upgrade auf AEM Communities 6.2 {#upgrading-to-aem-communities}

Wenn bei der Aktualisierung auf AEM Communities 6.3 bereits vorhandene UGC beibehalten werden müssen, sollten Schritte unternommen werden, je nachdem, ob die AEM 5.6.1- oder AEM 6.0-Community die On-Demand-Datenspeicherung der Adobe oder die lokale Datenspeicherung von UGC verwendet hat.

Weitere Informationen finden Sie unter [Upgrade auf AEM Communities 6.3](upgrade.md).
