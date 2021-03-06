---
title: RDBMS-Unterstützung in AEM 6.4
seo-title: RDBMS Support in AEM 6.4
description: Erfahren Sie mehr über die Unterstützung der RDBMS-Persistenz in AEM 6.4 sowie die verfügbaren Konfigurationsoptionen.
seo-description: Learn about the relational database persistence support in AEM 6.4 and the available configuration options.
uuid: 599d3e61-99eb-4a1c-868b-52b20a615500
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: deploying
discoiquuid: 56a984a5-4b7f-4a95-8a17-95d2d355bfed
feature: Configuring
exl-id: 89523bb4-e4c4-469c-802b-6fe27c816a2e
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 73%

---

# RDBMS-Unterstützung in AEM 6.4{#rdbms-support-in-aem}

## Übersicht {#overview}

Die Unterstützung für RDBMS-Persistenz in AEM wird mithilfe des Document-Mikrokernels implementiert. Der Document-Mikrokernel bildet die Grundlage, die auch für die Implementierung der MongoDB-Persistenz verwendet wird.

Er umfasst eine Java-API, die auf der Mongo-Java-API basiert. Eine BlobStore-API wird ebenfalls implementiert. BLOB-Objekte werden standardmäßig in der Datenbank gespeichert.

Weitere Informationen zu den Implementierungsdetails finden Sie in der Dokumentation zu [RDBDocumentStore](https://jackrabbit.apache.org/oak/docs/apidocs/org/apache/jackrabbit/oak/plugins/document/rdb/RDBDocumentStore.html) und [RDBBlobStore](https://jackrabbit.apache.org/oak/docs/apidocs/org/apache/jackrabbit/oak/plugins/document/rdb/RDBBlobStore.html).

>[!NOTE]
>
>Unterstützung für **PostgreSQL 9.4** wird ebenfalls bereitgestellt, jedoch nur zu Demozwecken. Sie ist nicht für Produktionsumgebungen verfügbar.

## Unterstützte Datenbanken {#supported-databases}

Weitere Informationen zur Unterstützung relationaler Datenbanken in AEM finden Sie auf der [Seite mit den technischen Anforderungen](/help/sites-deploying/technical-requirements.md). 

## Konfigurationsschritte {#configuration-steps}

Das Repository wird durch Konfigurieren des OSGi-Dienstes `DocumentNodeStoreService` erstellt. Es muss erweitert werden, um neben der MongoDB-Persistenz auch die RDBMS-Persistenz zu unterstützen.

Um diese nutzen zu können, muss eine Datenquelle mithilfe von AEM konfiguriert werden. Dies geschieht über die Datei `org.apache.sling.datasource.DataSourceFactory.config`. Die JDBC-Treiber für die jeweilige Datenbank müssen separat als OSGi-Bundles in der lokalen Konfiguration bereitgestellt werden.

Weitere Informationen über die Schritte zum Erstellen von OSGi-Bundles für JDBC-Treiber finden Sie in dieser [Dokumentation](https://wiki.eclipse.org/Create_and_Export_MySQL_JDBC_driver_bundle) auf der Apache Sling-Website.

>[!NOTE]
>
>Einige der SQL-Treiber sind bereits als OSGi-Bundles gepackt.
>
>Wenn dies der Fall ist, kopieren Sie einfach die JAR-Datei in install-path/crx-quickstart/install/9.

Wenn die Bundles erstellt wurden, befolgen Sie die nachfolgenden Schritte zum Konfigurieren der RDB-Persistenz in AEM:

1. Stellen Sie sicher, dass der Datenbank-Daemon gestartet ist und eine aktive Datenbank für die Verwendung mit AEM vorhanden ist.
1. Kopieren Sie die AEM 6.3-JAR-Datei in das Installationsverzeichnis.
1. Erstellen Sie einen Ordner mit dem Namen `crx-quickstart\install` im Installationsverzeichnis.
1. Konfigurieren Sie den Document-Knotenspeicher, indem Sie eine Konfigurationsdatei mit dem folgenden Namen im Verzeichnis `crx-quickstart\install` erstellen:

   * `org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService.config`

1. Erstellen Sie eine weitere Konfigurationsdatei mit dem folgenden Namen im Ordner `crx-quickstart\install`, um die Datenquelle und die JDBC-Parameter zu konfigurieren:

   * `org.apache.sling.datasource.DataSourceFactory-oak.config`
   >[!NOTE]
   >
   >Detaillierte Informationen zur Datenquellenkonfiguration für die einzelnen unterstützten Datenbanken finden Sie unter [Konfigurationsoptionen für die Datenquelle](/help/sites-deploying/rdbms-support-in-aem.md#data-source-configuration-options).

1. Bereiten Sie dann die JDBC-OSGi-Bundles für die Verwendung mit AEM vor:

   1. Laden Sie das ZIP-Archiv von https://dev.mysql.com/downloads/connector/j/ herunter.
      * Version muss >= 5.1.38 sein.
   1. Extrahieren Sie die `mysql-connector-java-version-bin.jar` (Bundle) aus dem Archiv
   1. Verwenden Sie die Web-Konsole, um das Bundle zu installieren und zu starten:
      * Navigieren Sie zu *http://serveraddress:serverport/system/console/bundles*
      * Auswählen **Installieren/Aktualisieren**
      * Navigieren Sie zum Paket, das aus dem heruntergeladenen ZIP-Archiv extrahiert wurde.
      * Vergewissern Sie sich, dass **JDBC-Treiber der oracle Corporation für MySQLcom.mysql.jdbc** aktiv ist, und starten Sie es.

1. Beginnen Sie AEM schließlich mit der `crx3` und `crx3rdb` runmodes:

   ```java
   java -jar quickstart.jar -r crx3,crx3rdb
   ```

## Konfigurationsoptionen für die Datenquelle {#data-source-configuration-options}

Die OSGi-Konfiguration `org.apache.sling.datasource.DataSourceFactory-oak.config` dient zum Konfigurieren der erforderlichen Parameter für die Kommunikation zwischen AEM und der Datenbank-Persistenz-Schicht.

Folgende Konfigurationsoptionen sind verfügbar:

* `datasource.name:` Der Name der Datenquelle. Der Standardwert lautet `oak`.

* `url:` Die URL-Zeichenfolge der Datenbank, die mit JDBC verwendet werden muss. Jeder Datenbanktyp hat ein eigenes Format für die URL-Zeichenfolge. Weitere Informationen finden Sie nachfolgend unter [URL-Zeichenfolgenformate](/help/sites-deploying/rdbms-support-in-aem.md#url-string-formats).

* `driverClassName:` Der Name der JDBC-Treiberklasse. Dieser variiert je nach der zu verwendenden Datenbank und dem Treiber, der für die Verbindung mit derselben benötigt wird. Nachfolgend finden Sie die Klassennamen aller von AEM unterstützten Datenbanken:

   * `org.postgresql.Driver` für PostgreSQL;
   * `com.ibm.db2.jcc.DB2Driver` für DB2;
   * `oracle.jdbc.OracleDriver` für Oracle;
   * `com.mysql.jdbc.Driver` für MySQL und MariaDB (experimentell)
   * c`om.microsoft.sqlserver.jdbc.SQLServerDriver` für Microsoft SQL Server (experimentell)

* `username:` Der Benutzername, unter dem die Datenbank ausgeführt wird.

* `password:` Das Datenbankkennwort.

### URL-Zeichenfolgenformate {#url-string-formats}

Je nach dem zu verwendenden Datenbanktyp wird ein unterschiedliches URL-Zeichenfolgenformat in der Datenquellenkonfiguration verwendet. Nachfolgend finden Sie eine Liste der Formate für die derzeit von AEM unterstützten Datenbanken:

* `jdbc:postgresql:databasename` für PostgreSQL;

* `jdbc:db2://localhost:port/databasename` für DB2;
* `jdbc:oracle:thin:localhost:port:SID` für Oracle;
* `jdbc:mysql://localhost:3306/databasename` für MySQL und MariaDB (experimentell)

* `jdbc:sqlserver://localhost:1453;databaseName=name` für Microsoft SQL Server (experimentell).

## Bekannte Einschränkungen {#known-limitations}

Obwohl die RDBMS-Persistenz die gleichzeitige Verwendung mehrerer AEM-Instanzen mit einer einzigen Datenbank unterstützt, trifft dies nicht auf gleichzeitige Installationen zu.

Um dieses Problem zu umgehen, führen Sie zuerst die Installation mit nur einer Instanz aus und fügen Sie dann nach Abschluss derselben weitere hinzu.
