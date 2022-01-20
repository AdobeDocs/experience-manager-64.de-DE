---
title: Einrichten von MongoDB für Demo
seo-title: How to Setup MongoDB for Demo
description: Einrichten von MSRP für eine Autoreninstanz und eine Veröffentlichungsinstanz
seo-description: How to setup MSRP for one author instance and one publish instance
uuid: d2035a9e-f05c-4f90-949d-7cdae9646750
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 0b126218-b142-4d33-a28c-a91ab4fe99ac
role: Admin
exl-id: e32fc619-6226-48c6-bbd7-1910963d1036
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '825'
ht-degree: 2%

---

# Einrichten von MongoDB für Demo {#how-to-setup-mongodb-for-demo}

## Einführung {#introduction}

In diesem Tutorial wird beschrieben, wie Sie [MSRP](msrp.md) für *ein Autor* Instanz und *eine Veröffentlichung* -Instanz.

Bei dieser Konfiguration ist der Community-Inhalt sowohl in der Autoren- als auch in der Veröffentlichungsumgebung verfügbar, ohne dass benutzergenerierte Inhalte weitergeleitet oder umgekehrt repliziert werden müssen.

Diese Konfiguration eignet sich für *Nicht-Produktion* Umgebungen, z. B. für Entwicklung und/oder Demonstration.

**A *production* -Umgebung:**

* Ausführen von MongoDB mit einem Replikatsatz
* SolrCloud verwenden
* Mehrere Herausgeberinstanzen enthalten

## MongoDB {#mongodb}

### MongoDB installieren {#install-mongodb}

* MongoDB herunterladen von [https://www.mongodb.org/](https://www.mongodb.org/)

   * Wahl des Betriebssystems:

      * Linux
      * Mac 10.8
      * Windows 7
   * Wahl der Version:

      * Verwenden Sie mindestens Version 2.6


* Grundkonfiguration

   * Befolgen Sie die MongoDB-Installationsanweisungen
   * Konfigurieren für mongod

      * Keine Konfiguration von Mongos oder Freigabe erforderlich
   * Der installierte MongoDB-Ordner wird als &lt;mongo-install>
   * Der definierte Datenordnerpfad wird als &lt;mongo-dbpath>


* MongoDB kann auf demselben Host ausgeführt werden wie AEM oder remote ausgeführt werden

### MongoDB starten {#start-mongodb}

* &lt;mongo-install>/bin/mongod —dbpath &lt;mongo-dbpath>

Dadurch wird ein MongoDB-Server mit dem Standardanschluss 27017 gestartet.

* Erhöhen Sie für Mac ulimit mit dem Startarg &#39;ulimit -n 2048&#39;.

>[!NOTE]
>
>Wenn MongoDB gestartet wird *after* AEM **Neustart** all **AEM** Instanzen ordnungsgemäß mit MongoDB verbunden werden.

### Demoproduktionsoption: MongoDB-Replikat-Set einrichten {#demo-production-option-setup-mongodb-replica-set}

Die folgenden Befehle sind ein Beispiel für die Einrichtung einer Replikatgruppe mit 3 Knoten auf localhost:

* bin/mongod —port 27017 —dbpath data —replSet rs0&amp;
* bin/mongo

   * cfg = {&quot;_id&quot;: &quot;rs0&quot;,&quot;version&quot;: 1, &quot;Mitglieder&quot;: [{&quot;_id&quot;: 0,&quot;host&quot;: &quot;127.0.0.1:27017&quot;}]}
   * rs.initiate(cfg)

* bin/mongod —port 27018 —dbpath data1 —replSet rs0&amp;
* bin/mongod —port 27019 —dbpath data2 —replSet rs0&amp;
* bin/mongo

   * rs.add(&quot;127.0.0.1:27018&quot;)
   * rs.add(&quot;127.0.0.1:27019&quot;)
   * rs.status()

## Solr {#solr}

### Installieren von Solr {#install-solr}

* Solr herunterladen von [Apache Lucene](https://archive.apache.org/dist/lucene/solr/):

   * Für jedes Betriebssystem geeignet
   * Version 4.10 oder Version 5 verwenden
   * Solr erfordert Java 1.7 oder höher

* Grundkonfiguration

   * Folgen Sie dem Solr-Setup &quot;example&quot;.
   * Es ist kein Dienst erforderlich
   * Der installierte Solr-Ordner wird als &lt;solr-install>

### Solr für AEM Communities konfigurieren {#configure-solr-for-aem-communities}

Um eine Solr-Sammlung für MSRP für Demos zu konfigurieren, müssen zwei Entscheidungen getroffen werden (unter den Links zur Hauptdokumentation finden Sie weitere Informationen):

1. Führen Sie Solr eigenständig aus oder [SolrCloud-Modus](msrp.md#solrcloudmode)
1. Installieren [standard](msrp.md#installingstandardmls) oder [advanced](msrp.md#installingadvancedmls) mehrsprachige Suche (MLS)

### Eigenständiger Solr {#standalone-solr}

Die Methode zum Ausführen von Solr kann je nach Version und Art der Installation unterschiedlich sein. Die [Solr-Referenzhandbuch](https://archive.apache.org/dist/lucene/solr/ref-guide/) ist die maßgebliche Dokumentation.

Zur Vereinfachung und zur Verwendung von Version 4.10 als Beispiel starten Sie Solr im eigenständigen Modus:

* cd bis &lt;solrinstall>/example
* java -jar start.jar

Dadurch wird ein Solr-HTTP-Server mit dem Standardanschluss 8983 gestartet. Sie können zur Solr-Konsole navigieren, um eine Solr-Konsole zum Testen zu erhalten.

* Standard-Solr-Konsole: [http://localhost:8983/solr/](http://localhost:8983/solr/)

>[!NOTE]
>
>Wenn die Solr-Konsole nicht verfügbar ist, überprüfen Sie die Protokolle unter &lt;solrinstall>/example/logs. Überprüfen Sie, ob SOLR versucht, an einen bestimmten Hostnamen zu binden, der nicht aufgelöst werden kann (z. B. &quot;user-macbook-pro&quot;).
Falls ja, aktualisieren Sie die Datei etc/hosts mit einem neuen Eintrag für diesen Hostnamen (z.B. 127.0.0.1 user-macbook-pro) und Solr wird ordnungsgemäß gestartet.

### SolrCloud {#solrcloud}

Um ein sehr einfaches SolrCloud-Setup (nicht die Produktion) auszuführen, starten Sie solr mit:

* java -Dbootstrap_confdir=./solr/collection1/conf -Dbootstrap_conf=true -DzkRun -jar start.jar

## MongoDB als allgemeinen Store identifizieren {#identify-mongodb-as-common-store}

Starten Sie bei Bedarf die Autoren- und Veröffentlichungsinstanzen AEM.

Wenn AEM vor dem Start von MongoDB ausgeführt wurde, müssen die AEM Instanzen neu gestartet werden.

Befolgen Sie die Anweisungen auf der Hauptseite der Dokumentation: [MSRP - MongoDB Common Store](msrp.md)

## Testen {#test}

Um den gemeinsamen MongoDB-Speicher zu testen und zu überprüfen, posten Sie einen Kommentar in der Veröffentlichungsinstanz, zeigen Sie ihn in der Autoreninstanz an und zeigen Sie die UGC in MongoDB und Solr an:

1. Navigieren Sie in der Veröffentlichungsinstanz zum [Handbuch zu Community-Komponenten](http://localhost:4503/content/community-components/en/comments.html) und wählen Sie die Komponente Kommentare aus.
1. Melden Sie sich an, um einen Kommentar zu posten:
1. Geben Sie Text in das Textfeld für Kommentare ein und klicken Sie auf **[!UICONTROL Post]**

   ![chlimage_1-191](assets/chlimage_1-191.png)

1. Sehen Sie sich einfach den Kommentar zum [Autoreninstanz](http://localhost:4502/content/community-components/en/comments.html) (Wahrscheinlich noch als Administrator/Administrator angemeldet).

   ![chlimage_1-192](assets/chlimage_1-192.png)

   Hinweis: , während es JCR-Knoten unter der *asipath* auf der Autoreninstanz, sind diese für das SCF-Framework bestimmt. Die tatsächliche UGC befindet sich nicht in JCR, sondern in der MongoDB.

1. Anzeigen der benutzergenerierten Inhalte in mongodb **[!UICONTROL Communities > Sammlungen > Inhalt]**

   ![chlimage_1-193](assets/chlimage_1-193.png)

1. Zeigen Sie den benutzergenerierten Inhalt in Solr an:

   * Navigieren Sie zum Solr-Dashboard: [http://localhost:8983/solr/](http://localhost:8983/solr/)
   * Benutzer `core selector` auswählen `collection1`
   * Wählen Sie nun eine der folgenden Optionen aus `Query`
   * Wählen Sie nun eine der folgenden Optionen aus `Execute Query`

   ![chlimage_1-194](assets/chlimage_1-194.png)

## Fehlerbehebung {#troubleshooting}

### Kein UGC wird angezeigt {#no-ugc-appears}

1. Stellen Sie sicher, dass MongoDB ordnungsgemäß installiert und ausgeführt wird.

1. Stellen Sie sicher, dass MSRP als Standardanbieter konfiguriert wurde:

   * Rufen Sie auf allen Autoren- und Veröffentlichungsinstanzen AEM erneut die [Speicherkonfigurationskonsole](srp-config.md)

   oder überprüfen Sie das AEM Repository:

   * Wenn in JCR [/etc/socialconfig](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/)

      * Enthält keine [srpc](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc) Knoten bedeutet, dass der Speicheranbieter JSRP ist.
      * Wenn der Knoten srpc vorhanden ist und den Knoten enthält [defaultconfiguration](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc/defaultconfiguration), sollten die Eigenschaften der Standardkonfiguration MSRP als Standardanbieter definieren


1. Stellen Sie sicher, dass AEM nach Auswahl von MSRP neu gestartet wurde.
