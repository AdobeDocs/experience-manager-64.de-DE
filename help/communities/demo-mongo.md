---
title: Setup von MongoDB für Demo
seo-title: Setup von MongoDB für Demo
description: Einrichten von MSRP für eine Autoreninstanz und eine Veröffentlichungsinstanz
seo-description: Einrichten von MSRP für eine Autoreninstanz und eine Veröffentlichungsinstanz
uuid: d2035a9e-f05c-4f90-949d-7cdae9646750
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 0b126218-b142-4d33-a28c-a91ab4fe99ac
role: 'Administrator  '
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '844'
ht-degree: 2%

---


# Setup von MongoDB für Demo {#how-to-setup-mongodb-for-demo}

## Einführung {#introduction}

In diesem Lernprogramm wird beschrieben, wie [MSRP](msrp.md) für *eine Autorinstanz* und *eine Instanz im Veröffentlichungsmodus* eingerichtet wird.

Bei diesem Setup ist der Zugriff auf den Community-Inhalt sowohl von Autoren- als auch von Veröffentlichungsinhalten möglich, ohne dass benutzergenerierte Inhalte weitergeleitet oder umgekehrt repliziert werden müssen.

Diese Konfiguration eignet sich für *Nicht-Produktion*-Umgebung, z. B. für Entwicklungs- und/oder Demonstrationszwecke.

**Eine  ** Produktionsumgebung sollte**

* Ausführen von MongoDB mit einem Replikationssatz
* SolrCloud verwenden
* Mehrere Herausgeberinstanzen enthalten

## MongoDB {#mongodb}

### MongoDB {#install-mongodb} installieren

* Laden Sie MongoDB von [https://www.mongodb.org/](https://www.mongodb.org/) herunter.

   * Wahl des Betriebssystems:

      * Linux
      * Mac 10.8
      * Windows 7
   * Wahl der Version:

      * Verwenden Sie mindestens Version 2.6


* Grundkonfiguration

   * Befolgen Sie die Installationsanweisungen für MongoDB
   * Konfigurieren für Mongod

      * Keine Konfiguration von Mongos oder Freigeben erforderlich
   * Der installierte MongoDB-Ordner wird als &lt;mongo-install> bezeichnet
   * Der definierte Datenordnerpfad wird als &lt;mongo-dbpath> bezeichnet


* MongoDB kann auf demselben Host wie AEM ausgeführt oder remote ausgeführt werden

### Beginn MongoDB {#start-mongodb}

* &lt;mongo-install>/bin/mongod —dbpath  &lt;mongo-dbpath>

Dadurch wird ein MongoDB-Server mit dem Standardanschluss 27017 Beginn.

* Für Mac sollten Sie ulimit mit dem Beginn arg &#39;ulimit -n 2048&#39; erhöhen.

>[!NOTE]
>
>Wenn MongoDB nach *AEM gestartet wird,**starten Sie**alle **AEM**-Instanzen neu, damit sie ordnungsgemäß eine Verbindung zu MongoDB herstellen.*

### Demoproduktionsoption: Setup MongoDB Replikat Set {#demo-production-option-setup-mongodb-replica-set}

Die folgenden Befehle sind ein Beispiel für die Einrichtung eines Replikationssatzes mit 3 Knoten auf localhost:

* bin/mongod —port 27017 —dbpath data —replSet rs0&amp;
* bin/mongo

   * cfg = {&quot;_id&quot;: &quot;rs0&quot;,&quot;version&quot;: 1, &quot;Mitglieder&quot;: [{&quot;_id&quot;: 0,&quot;Host&quot;: &quot;127.0.0.1:27017&quot;}]}
   * rs.initiate(cfg)

* bin/mongod —port 27018 —dbpath data1 —replSet rs0&amp;
* bin/mongod —port 27019 —dbpath data2 —replSet rs0&amp;
* bin/mongo

   * rs.add(&quot;127.0.0.1:27018&quot;)
   * rs.add(&quot;127.0.0.1:27019&quot;)
   * rs.status()

## Solr {#solr}

### Installieren von Solr {#install-solr}

* Laden Sie Solr von [Apache Lucene](https://archive.apache.org/dist/lucene/solr/) herunter:

   * Eignet sich für jedes Betriebssystem
   * Version 4.10 oder Version 5 verwenden
   * Solr erfordert Java 1.7 oder höher

* Grundkonfiguration

   * Führen Sie das Setup von &#39;example&#39; Solr aus
   * Es ist kein Dienst erforderlich
   * Der installierte Solr-Ordner wird als &lt;solr-install> bezeichnet

### Konfigurieren von Solr für AEM Communities {#configure-solr-for-aem-communities}

Um eine SOLR-Sammlung für MSRP für Demo zu konfigurieren, müssen zwei Entscheidungen getroffen werden (siehe die Links zur Hauptdokumentation):

1. Führen Sie Solr im eigenständigen oder [SolrCloud-Modus](msrp.md#solrcloudmode) aus
1. [standard](msrp.md#installingstandardmls) oder [advanced](msrp.md#installingadvancedmls) Mehrsprachige Suche (MLS) installieren

### Eigenständiger Solr {#standalone-solr}

Die Methode zum Ausführen von Solr kann je nach Version und Installationsart unterschiedlich sein. Die [Solr-Referenzhandbuch](https://archive.apache.org/dist/lucene/solr/ref-guide/) ist die maßgebliche Dokumentation.

Aus Gründen der Einfachheit ist Beginn Solr im eigenständigen Modus mit Version 4.10 als Beispiel zu verwenden:

* cd bis &lt;solrinstall>/example
* java -jar Beginn.jar

Dadurch wird ein Solr-HTTP-Server mit dem Standardanschluss 8983 Beginn. Sie können zur Solr-Konsole navigieren, um eine Solr-Konsole zum Testen zu erhalten.

* Standard-Solr-Konsole: [http://localhost:8983/solr/](http://localhost:8983/solr/)

>[!NOTE]
>
>Wenn Solr Console nicht verfügbar ist, überprüfen Sie die Protokolle unter &lt;solrinstall>/example/logs. Achten Sie darauf, ob SOLR versucht, sich an einen bestimmten Hostnamen zu binden, der nicht aufgelöst werden kann (z.B. &quot;user-macbook-pro&quot;).
Wenn ja, aktualisieren Sie die Datei etc/hosts mit einem neuen Eintrag für diesen Hostnamen (z.B. 127.0.0.1 user-macbook-pro) und Solr wird ordnungsgemäß Beginn.

### SolrCloud {#solrcloud}

Um eine sehr einfache (nicht produktive) solrCloud-Einrichtung auszuführen, führen Sie Beginn-Solr mit:

* java -Dbootstrap_condir=./solr/collection1/conf -Dbootstrap_conf=true -DzkRun -jar Beginn.jar

## Identifizieren Sie MongoDB als Common Store {#identify-mongodb-as-common-store}.

Starten Sie bei Bedarf die Instanz im Autorenmodus und veröffentlichen Sie AEM.

Wenn AEM vor dem Start von MongoDB ausgeführt wurde, müssen die AEM Instanzen neu gestartet werden.

Befolgen Sie die Anweisungen auf der Hauptseite der Dokumentation: [MSRP - MongoDB Common Store](msrp.md)

## Test {#test}

Um den MongoDB-Stammspeicher zu testen und zu überprüfen, veröffentlichen Sie einen Kommentar zur Veröffentlichungsinstanz und Ansicht auf der Autoreninstanz sowie die Ansicht des UGC in MongoDB und Solr:

1. Navigieren Sie auf der Seite &quot;Veröffentlichungsinstanz&quot;zur Seite [Community-Komponentenhandbuch](http://localhost:4503/content/community-components/en/comments.html) und wählen Sie die Komponente &quot;Kommentare&quot;aus.
1. Melden Sie sich an, um einen Kommentar zu posten:
1. Geben Sie Text in das Kommentartexteingabefeld ein und klicken Sie auf **[!UICONTROL Post]**

   ![chlimage_1-191](assets/chlimage_1-191.png)

1. Ansicht Sie einfach den Kommentar auf der [Autoreninstanz](http://localhost:4502/content/community-components/en/comments.html) (wahrscheinlich noch als Admin/Admin angemeldet).

   ![chlimage_1-192](assets/chlimage_1-192.png)

   Hinweis: während sich unter dem Autorenordner *asipath* JCR-Knoten befinden, gelten diese für das SCF-Framework. Die eigentliche UGC ist nicht in JCR, sondern in der MongoDB.

1. Ansicht des UGC in mongodb **[!UICONTROL Communities > Collections > Content]**

   ![chlimage_1-193](assets/chlimage_1-193.png)

1. Ansicht des UGC in Solr:

   * Zu Solr-Dashboard navigieren: [http://localhost:8983/solr/](http://localhost:8983/solr/)
   * Benutzer `core selector` zur Auswahl von `collection1`
   * Wählen Sie nun eine der folgenden Optionen aus `Query`
   * Wählen Sie nun eine der folgenden Optionen aus `Execute Query`

   ![chlimage_1-194](assets/chlimage_1-194.png)

## Fehlerbehebung {#troubleshooting}

### Kein UGC wird angezeigt {#no-ugc-appears}

1. Vergewissern Sie sich, dass MongoDB ordnungsgemäß installiert ist und ausgeführt wird.

1. Stellen Sie sicher, dass MSRP als Standardanbieter konfiguriert wurde:

   * Auf allen Instanzen im Autorenmodus und AEM Veröffentlichungsmodus erneut die Konfigurationskonsole [Datenspeicherung ](srp-config.md)

   oder überprüfen Sie das AEM Repository:

   * In JCR, wenn [/etc/socialconfig](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/)

      * Enthält keinen Knoten [srpc](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc), d. h., der Anbieter der Datenspeicherung ist JSRP
      * Wenn der Knoten srpc vorhanden ist und den Knoten [defaultConfiguration](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc/defaultconfiguration) enthält, sollten die Eigenschaften der Standardkonfiguration MSRP als Standardanbieter definieren


1. Stellen Sie sicher, dass AEM nach Auswahl von MSRP neu gestartet wurde.
