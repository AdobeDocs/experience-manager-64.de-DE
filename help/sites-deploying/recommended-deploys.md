---
title: Empfohlene Bereitstellungen
seo-title: Recommended Deployments
description: In diesem Artikel werden die empfohlenen Topologien für AEM beschrieben.
seo-description: This article describes the recommended topologies for AEM.
uuid: 565117b1-4659-41e1-9f57-97dd048e306f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: deploying
discoiquuid: 5e903df9-6591-46e8-9251-45170c78aa21
exl-id: aa4ec854-e32b-4136-a6d4-a42deb2afb18
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1827'
ht-degree: 52%

---

# Empfohlene Bereitstellungen{#recommended-deployments}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

>[!NOTE]
>
>Diese Seite beschreibt empfohlene Topologien für AEM. Weitere Informationen zu Clustering-Funktionen und zum Konfigurieren derselben finden Sie in der [Apache Sling-Dokumentation zur Discovery-API](https://sling.apache.org/documentation/bundles/discovery-api-and-impl.html) (in englischer Sprache).

MicroKernels dienen in AEM 6.4 als Persistenzmanager. Die Auswahl eines Persistenzmanagers hängt vom Zweck Ihrer Instanz und dem Bereitstellungstyp ab, den Sie in Erwägung ziehen.

Die folgenden Beispiele geben Auskunft über die empfohlenen Verwendungszwecke in den gängigsten AEM.

## Bereitstellungsszenarien {#deployment-scenarios}

### Einzelne TarMK-Instanz {#single-tarmk-instance}

In diesem Szenario wird eine einzelne TarMK-Instanz auf einem einzelnen Server ausgeführt.

**Dies ist die Standardbereitstellung für Autoreninstanzen.**

![chlimage_1-15](assets/chlimage_1-15.png)

Die Vorteile:

* Einfach
* Einfache Wartung
* Gute Leistung

Die Nachteile:

* Nicht skalierbar über die Grenzen der Server-Kapazität
* Keine Failover-Kapazität

### TarMK Cold Standby {#tarmk-cold-standby}

Eine TarMK-Instanz fungiert als primäre Instanz. Das Repository von der primären Instanz wird in ein Standby-Failover-System repliziert.

Der Cold-Standby-Mechanismus kann auch als Sicherungsmechanismus verwendet werden, da das gesamte Repository ständig auf dem Failover-Server repliziert wird. Der Failover-Server wird im Cold-Standby-Modus ausgeführt, was bedeutet, dass nur der HttpReceiver der Instanz ausgeführt wird.

![chlimage_1-16](assets/chlimage_1-16.png)

Die Vorteile:

* Einfachheit
* Wartbarkeit
* Leistung
* Failover

Die Nachteile:

* Nicht skalierbar über die Grenzen der Server-Kapazität
* Ein Server ist meistens inaktiv
* Kein automatisches Failover. Sie muss extern erkannt werden, bevor das Failover-System mit der Verarbeitung von Anforderungen beginnen kann.

>[!NOTE]
>
>Weitere Informationen zum Konfigurieren von TarMK-Cold-Standby in AEM finden Sie in [diesem](/help/sites-deploying/tarmk-cold-standby.md) Artikel.

>[!NOTE]
>
>Für die Cold-Standby-Bereitstellung in diesem TarMK-Beispiel müssen die primäre und die Standby-Instanz separat lizenziert werden, da eine konstante Replikation auf dem Failover-Server stattfindet. Weitere Informationen zur Lizenzierung finden Sie in den [allgemeinen Lizenzbedingungen von Adobe](https://www.adobe.com/de/legal/terms/enterprise-licensing.html).

### TarMK-Farm {#tarmk-farm}

Mehrere Oak-Instanzen werden jeweils mit einer TarMK-Instanz ausgeführt. Die TarMK-Repositorys sind unabhängig und müssen synchronisiert werden.

Die Synchronisierung der Repositorys wird dadurch erreicht, dass der Autorenserver dieselben Inhalte auf allen Mitgliedern der Farm veröffentlicht. Weitere Informationen finden Sie unter [Replikation](/help/sites-deploying/replication.md).

Für AEM Communities werden benutzergenerierte Inhalte nie repliziert. Weitere Informationen zur Unterstützung von benutzergenerierten Inhalten in einer TarMK-Farm finden Sie unter [Faktoren für AEM Communities](#considerations-for-aem-communities).

**Dies ist das Standard-Bereitstellungsszenario für Veröffentlichungsumgebungen.**

![chlimage_1-17](assets/chlimage_1-17.png)

Die Vorteile:

* Leistung
* Skalierbarkeit des Lesezugriffs
* Failover

### Oak-Cluster mit MongoMK-Failover für hohe Verfügbarkeit in einem einzigen Rechenzentrum {#oak-cluster-with-mongomk-failover-for-high-availability-in-a-single-datacenter}

Dieser Ansatz bedeutet, dass mehrere Oak-Instanzen auf ein MongoDB-Replikat in einem einzigen Rechenzentrum zugreifen und so einen aktiv-aktiven Cluster für die AEM-Autorenumgebung erstellen. In MongoDB dienen Replikatgruppen dazu, bei Hardware- oder Netzwerkausfällen für hohe Verfügbarkeit und Redundanz zu sorgen.

![chlimage_1-18](assets/chlimage_1-18.png)

Die Vorteile:

* Möglichkeit zur horizontalen Skalierung mit neuen AEM Autoreninstanzen
* Hohe Verfügbarkeit, Redundanz und automatisiertes Failover der Datenschicht

Die Nachteile:

* In einigen Szenarien kann die Leistung geringer sein als bei TarMK

### Oak-Cluster mit MongoMK-Failover für mehrere Rechenzentren {#oak-cluster-with-mongomk-failover-across-multiple-datacenters}

Dieser Ansatz bedeutet, dass mehrere Oak-Instanzen auf ein MongoDB-Replikat in mehreren Rechenzentren zugreifen und so einen aktiv-aktiven Cluster für die AEM-Autorenumgebung erstellen. Bei mehreren Rechenzentren bietet die MongoDB-Replikation dieselbe hohe Verfügbarkeit und Redundanz sowie jetzt die Möglichkeit, Rechenzentrumsausfälle zu bewältigen.

![oakclustermongofailover2datacenters](assets/oakclustermongofailover2datacenters.png)

Die Vorteile:

* Möglichkeit zur horizontalen Skalierung mit neuen AEM Autoreninstanzen
* Hohe Verfügbarkeit, Redundanz und automatisiertes Failover der Datenschicht (einschließlich Ausfall des Rechenzentrums)

>[!NOTE]
>
>In der obigen Abbildung werden AEM-Server 3 und AEM-Server 4 mit einem inaktiven Status dargestellt, wobei von einer Netzwerklatenz zwischen den AEM-Servern im Rechenzentrum 2 und dem primären MongoDB-Knoten im Rechenzentrum 1 ausgegangen wird. Diese Latenz ist höher als die Anforderung, die [hier](/help/sites-deploying/aem-with-mongodb.md#checklists) dokumentiert ist. Wenn die maximale Latenzzeit mit den Anforderungen vereinbar ist, z. B. durch die Verwendung von Verfügbarkeitszonen, können auch die AEM-Server im Rechenzentrum 2 aktiv sein und einen aktiv-aktiven AEM-Cluster über mehrere Rechenzentren hinweg bilden.

>[!NOTE]
>
>Weitere Informationen zu den in diesem Abschnitt beschriebenen MongoDB-Architekturkonzepten finden Sie unter [MongoDB-Replikation](https://docs.mongodb.org/manual/replication/).

## Microkernel: welche {#microkernels-which-one-to-use}

Die grundlegende Regel, die bei der Auswahl zwischen den beiden verfügbaren Mikrokernels berücksichtigt werden muss, besteht darin, dass TarMK für die Leistung entwickelt wurde, während MongoMK für die Skalierbarkeit verwendet wird.

Sie können diese Entscheidungsmatrizen verwenden, um festzulegen, welcher Bereitstellungstyp für Ihre Anforderungen am besten geeignet ist.

Adobe empfiehlt dringend, TarMK als Standard-Persistenztechnologie zu verwenden, die von Kunden in allen Bereitstellungsszenarien verwendet wird, sowohl für die AEM-Autoren- als auch für die Veröffentlichungsinstanz, mit Ausnahme der unten beschriebenen Anwendungsfälle.

### Ausnahmen für die Auswahl AEM MongoMK gegenüber TarMK in Autoreninstanzen {#exceptions-for-choosing-aem-mongomk-over-tarmk-on-author-instances}

Der Hauptgrund dafür, warum anstatt des TarMK der MongoMK als Persistenz-Backend ausgewählt werden sollte, liegt in der horizontalen Skalierung der Instanzen. Das bedeutet, dass immer mindestens zwei aktive Autoreninstanzen ausgeführt werden und MongoDB als Persistenzspeichersystem verwendet wird. Die Notwendigkeit, mehr als eine Autoreninstanz auszuführen, resultiert im Allgemeinen aus der Tatsache, dass die CPU- und Speicherkapazität eines einzelnen Servers, der alle gleichzeitigen Authoring-Aktivitäten unterstützt, nicht mehr tragbar ist.

Es ist quasi unmöglich, vorherzusagen, wie das genau Parallelitätsmodell nach der Live-Schaltung einer neuen Site aussehen wird. Daher empfiehlt Adobe, bei der Beurteilung, ob MongoMK und zwei oder mehr aktive Autorknoten verwendet werden sollen, die folgenden Kriterien zu beachten:

1. Anzahl der benannten, verbundenen Benutzer an einem Tag: Tausende oder mehr.
1. Anzahl der gleichzeitigen Benutzer: Hunderte oder mehr.
1. Volumen der erfassten Assets pro Tag: Hunderttausende oder mehr.
1. Volumen der Seitenbearbeitungen pro Tag: Hunderttausende oder mehr (einschließlich automatisierte Aktualisierungen, z. B. über Multi-Site-Manager oder Newsfeed-Erfassungen)
1. Volumen der Suchvorgänge pro Tag: Zehntausende oder mehr.

>[!NOTE]
>
>Mithilfe von Tough Day kann die Leistung der Kundenanwendung im Kontext der implementierten Hardwarekonfiguration bewertet werden. Weitere Informationen zu diesem Tool finden Sie unter [here](/help/sites-developing/tough-day.md).

Eine minimale Bereitstellung mit MongoDB umfasst normalerweise die folgende Topologie:

* Eine MongoDB-Replikatgruppe mit einem primären und zwei sekundären Knoten, wobei alle MongoDB-Instanzen in einer Verfügbarkeitszone mit einer Latenz von unter 15 Millisekunden für jeden Knoten ausgeführt werden.
* Ein Cluster von Autoreninstanzen mit einem Leader-Knoten, einem Nicht-Leader-Knoten und beiden gleichzeitig aktiven Instanzen, wobei jede Autoreninstanz in jedem Rechenzentrum ausgeführt wird, in dem die primären und sekundären MongoDB-Instanzen ausgeführt werden.

Darüber hinaus wird dringend empfohlen, den Datenspeicher auf einem freigegebenen Dateisystem oder Amazon S3 so zu konfigurieren, dass die Assets oder Binärdateien nicht in MongoDB gespeichert werden. Dadurch wird eine optimale Leistung innerhalb der Implementierung sichergestellt.

Ein weiterer Vorteil, der sich durch die Bereitstellung einer MongoDB-Replikatgruppe mit einem Cluster von zwei oder mehr Autoreninstanzen ergibt, ist das automatisierte Wiederherstellungsszenario mit minimalen Ausfallzeiten bei einem Ausfall der Autoreninstanzen, MongoDB-Replikatgruppe oder des gesamten Rechenzentrums. Dennoch sollte die Wahl von MongoMK gegenüber TarMK nicht allein von der Wiederherstellungsanforderung bestimmt werden, da TarMK auch eine minimale Ausfallzeitlösung mit einem kontrollierten Failover-Mechanismus bereitstellen kann.

Wenn die oben genannten Kriterien während der ersten achtzehn Monate der Bereitstellung nicht erfüllt sein sollen, wird empfohlen, zunächst AEM mit TarMK bereitzustellen, dann Ihre Konfiguration zu einem späteren Zeitpunkt, wenn die oben genannten Kriterien zutreffen, neu zu bewerten und schließlich zu bestimmen, ob TarMK weiterhin verwendet oder zu MongoMK migriert werden soll.

### Ausnahmen für die Auswahl AEM MongoMK gegenüber TarMK auf Veröffentlichungsinstanzen {#exceptions-for-choosing-aem-mongomk-over-tarmk-on-publish-instances}

Die Bereitstellung von MongoMK für Veröffentlichungsinstanzen wird nicht empfohlen. Die Veröffentlichungsschicht der Bereitstellung wird fast immer als Farm mit unabhängigen Veröffentlichungsinstanzen bereitgestellt, auf denen TarMK ausgeführt wird und die durch das Replizieren von Inhalten von den Autoreninstanzen synchronisiert werden. Diese für Veröffentlichnungsinstanzen geeignete Shared-Nothing-Architektur ermöglicht die horizontale, lineare Skalierung der bereitgestellten Veröffentlichungsschicht. Die Farm-Topologie bietet auch den Vorteil, dass Aktualisierungen oder Aktualisierungen rollierend auf Veröffentlichungsinstanzen angewendet werden, sodass Änderungen an der Veröffentlichungsstufe keine Ausfallzeiten erfordern.

Dies gilt nicht für AEM Communities, das MongoMK-Cluster auf der Veröffentlichungsschicht verwendet, wenn mehr als ein Publisher vorhanden ist. Bei Auswahl von JSRP (siehe [Community-Inhaltsspeicher](/help/communities/working-with-srp.md)) ist ein MongoMK-Cluster angebracht, ebenso wie jedes Cluster auf Veröffentlichungsseite, unabhängig vom ausgewählten Mikrokernel (z. B. MongoDB oder RDB).

### Voraussetzungen und Empfehlungen für die Bereitstellung von AEM mit MongoMK {#prerequisites-and-recommendations-when-deploying-aem-with-mongomk}

Falls Sie eine MongoMK-Bereitstellung für AEM in Betracht ziehen, liegt eine Reihe von Voraussetzungen und Empfehlungen für AEM vor.

**Obligatorische Voraussetzungen für MongoDB-Bereitstellungen:**

1. Die MongoDB-Bereitstellungsarchitektur und -größe müssen mithilfe von Adobe Consulting oder MongoDB-Architekten, die mit AEM vertraut sind, Teil der Projektimplementierung sein.
1. MongoDB-Expertise muss im Partner- oder Kundenteam vorhanden sein, um Vertrauen in die Aufrechterhaltung und Pflege einer bestehenden oder neuen MongoDB-Umgebung zu haben.
1. Sie können die kommerzielle oder Open-Source-Version von MongoDB bereitstellen (AEM unterstützt beide), müssen jedoch einen MongoDB-Wartungs- und Supportvertrag direkt bei MongoDB Inc erwerben.
1. AEM- und MongoDB-Architekturen und -Infrastrukturen sollten von einer Adobe AEM Architekten klar definiert und validiert werden.
1. Sie müssen das Supportmodell für AEM Bereitstellungen überprüfen, die MongoDB enthalten.

**Dringende Empfehlungen für MongoDB-Bereitstellungen:**

* Lesen Sie den [Artikel](https://www.mongodb.com/lp/contact/mongodb-adobe-experience-manager) zu MongoDB für Adobe Experience Manager.
* Gehen Sie die Produktions[prüfliste](https://docs.mongodb.org/manual/administration/production-checklist/) für MongoDB durch.
* Nehmen Sie an einer Zertifizierungsschulung für MongoDB teil, die online [hier](https://university.mongodb.com/) verfügbar ist.

>[!NOTE]
>
>Bei allen weiteren Fragen zu diesen Richtlinien, Voraussetzungen und Empfehlungen wenden Sie sich bitte an [Adobe-Kundenunterstützung](https://helpx.adobe.com/de/marketing-cloud/contact-support.html).

### Überlegungen zu AEM Communities {#considerations-for-aem-communities}

Für Sites, die bereitstellen möchten [AEM Communities](/help/communities/overview.md)wird empfohlen, [Bereitstellung auswählen](/help/communities/working-with-srp.md) optimiert für die Verarbeitung von benutzergenerierten Inhalten, die von Community-Mitgliedern aus der Veröffentlichungsumgebung veröffentlicht werden.

Durch Verwendung von [gemeinsamer Speicher](/help/communities/working-with-srp.md), muss UGC nicht zwischen Autoren- und anderen Veröffentlichungsinstanzen repliziert werden, um eine einheitliche Ansicht der benutzergenerierten Inhalte zu erhalten.

Mit den nachfolgenden Entscheidungshilfen können Sie den optimalen Persistenztyp für Ihre Bereitstellung auswählen:

#### Auswahl des Bereitstellungstyps für Autoreninstanzen {#choosing-the-deployment-type-for-author-instances}

![chlimage_1-19](assets/chlimage_1-19.png)

#### Auswahl des Bereitstellungstyps für Veröffentlichungsinstanzen {#choosing-the-deployment-type-for-publish-instances}

![chlimage_1-20](assets/chlimage_1-20.png)

>[!NOTE]
>
>MongoDB ist eine Drittanbietersoftware und nicht im AEM-Lizenzierungspaket enthalten. Weitere Informationen finden Sie auf der Seite zur [MongoDB-Lizenzierungsrichtlinie](https://www.mongodb.org/about/licensing/).
>
>Um das Beste aus Ihrer AEM-Bereitstellung zu erhalten, empfiehlt Adobe die Lizenzierung der MongoDB Enterprise-Version, um professionellen Support zu erhalten.
>
>Die Lizenz umfasst eine standardmäßige Replikatgruppe. Diese besteht aus einer primären und zwei sekundären Instanzen, die für die Autoren- oder Veröffentlichungsbereitstellungen verwendet werden können.
>
>Wenn Sie sowohl Autor als auch Veröffentlichung auf MongoDB ausführen möchten, müssen zwei separate Lizenzen erworben werden.
>
>Weitere Informationen finden Sie auf der Seite für [MongoDB für Adobe Experience Manager](https://www.mongodb.com/lp/contact/mongodb-adobe-experience-manager).
