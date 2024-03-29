---
title: Verbindung mit SQL-Datenbanken
seo-title: Connecting to SQL Databases
description: Greifen Sie auf eine externe SQL-Datenbank zu, damit Ihre AEM-Anwendungen mit den Daten interagieren können.
seo-description: Access an external SQL database to so that your AEM applications can interact with the data
uuid: 0af0ed08-9487-4c37-87ce-049c9b4c1ea2
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 11a11803-bce4-4099-9b50-92327608f37b
exl-id: 7f10451d-3acb-4298-82f3-07897f66e407
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '984'
ht-degree: 55%

---

# Verbinden mit SQL-Datenbanken{#connecting-to-sql-databases}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Greifen Sie auf eine externe SQL-Datenbank zu, damit Ihre CQ-Anwendungen mit den Daten interagieren können:

1. [Erstellen oder beziehen Sie ein OSGi-Bundle, das das JDBC-Treiberpaket exportiert](#bundling-the-jdbc-database-driver).
1. [JDBC-Datenquellen-Poolanbieter konfigurieren](#configuring-the-jdbc-connection-pool-service).
1. [Rufen Sie ein Datenquellenobjekt ab und erstellen Sie die Verbindung in Ihrem Code.](#connecting-to-the-database).

## Bundling des JDBC-Datenbanktreibers {#bundling-the-jdbc-database-driver}

Einige Datenbankanbieter stellen JDBC-Treiber in einem OSGi-Paket bereit, z. B. [MySQL](https://www.mysql.com/downloads/connector/j/). Wenn der JDBC-Treiber für Ihre Datenbank nicht als OSGi-Bundle verfügbar ist, rufen Sie die Treiber-JAR-Datei ab und verpacken Sie sie in einem OSGi-Paket. Das Bundle muss die Pakete exportieren, die für die Interaktion mit dem Datenbankserver erforderlich sind. Das Bundle muss außerdem die Pakete importieren, die es referenziert.

Im folgenden Beispiel wird die [Bundle-Plug-in für Maven](https://felix.apache.org/site/apache-felix-maven-bundle-plugin-bnd.html) um den HSQLDB-Treiber in ein OSGi-Bundle zu verpacken. Der POM weist das Plug-in an, die hsqldb.jar-Datei einzubetten, die als Abhängigkeit identifiziert wird. Alle org.hsqldb-Pakete werden exportiert.

Das Plug-in bestimmt automatisch, welche Pakete importiert werden sollen, und listet sie in der Datei MANIFEST.MF des Bundles auf. Wenn eines der Pakete nicht auf dem CQ-Server verfügbar ist, startet das Bundle nicht bei der Installation. Zwei mögliche Lösungen sind:

* Geben Sie im POM an, dass die Pakete optional sind. Verwenden Sie diese Lösung, wenn die JDBC-Verbindung nicht die Paketmitglieder benötigt. Verwenden Sie das Element Import-Package , um optionale Pakete anzugeben, wie im folgenden Beispiel gezeigt:

   `<Import-Package>org.jboss.*;resolution:=optional,*</Import-Package>`
* Schließen Sie die JAR-Dateien, die die Pakete enthalten, in ein OSGi-Bundle ein, das die Pakete exportiert, und stellen Sie das Bundle bereit. Verwenden Sie diese Lösung, wenn die Paketmitglieder während der Codeausführung erforderlich sind.

Kenntnisse des Quellcodes ermöglichen es Ihnen, zu entscheiden, welche Lösung verwendet werden soll. Sie können auch eine der Lösungen ausprobieren und Tests durchführen, um die Lösung zu validieren.

### POM, das hsqldb.jar gebündelt {#pom-that-bundles-hsqldb-jar}

```xml
<project xmlns="https://maven.apache.org/POM/4.0.0" 
  xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" 
  xsi:schemaLocation="https://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  
  <groupId>com.adobe.example.myapp</groupId>
  <artifactId>hsqldb-jdbc-driver-bundle</artifactId>
  <version>0.0.1-SNAPSHOT</version>
  <name>wrapper-bundle-hsqldb-driver</name>
  <url>www.adobe.com</url>
  <description>Exports the HSQL JDBC driver</description>
  <packaging>bundle</packaging>
  <properties>
    <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
  </properties>
  <build>
    <plugins>
      <plugin>
        <groupId>org.apache.felix</groupId> 
        <artifactId>maven-bundle-plugin</artifactId>
        <version>1.4.3</version> 
        <extensions>true</extensions> 
        <configuration> 
         <instructions> 
            <Embed-Dependency>*</Embed-Dependency>
            <_exportcontents>org.hsqldb.*</_exportcontents>
          </instructions>
        </configuration> 
      </plugin>
    </plugins>
  </build>
  <dependencies>
    <dependency>
      <groupId>hsqldb</groupId>
      <artifactId>hsqldb</artifactId>
      <version>2.2.9</version>
    </dependency>
  </dependencies>
</project>
```

Die folgenden Links öffnen die Download-Seiten für einige beliebte Datenbankprodukte:

* [Microsoft SQL Server](https://www.microsoft.com/de-de/download/details.aspx?displaylang=en&amp;id=11774)
* [Oracle](https://www.oracle.com/technetwork/database/features/jdbc/index-091264.html)
* [IBM DB2](https://www-01.ibm.com/support/docview.wss?uid=swg27007053)

### Konfigurieren des JDBC Connection Pool-Dienstes {#configuring-the-jdbc-connection-pool-service}

Fügen Sie eine Konfiguration für den JDBC Connections Pool-Dienst hinzu. Dieser Dienst verwendet den JDBC-Treiber, um Datenquellenobjekte zu erstellen. Ihr Anwendungs-Code verwendet diesen Dienst, um das Objekt abzurufen und eine Verbindung zur Datenbank herzustellen.

JDBC Connections Pool (`com.day.commons.datasource.jdbcpool.JdbcPoolService`) ist ein Factory Service. Wenn Sie Verbindungen benötigen, die andere Eigenschaften verwenden, z. B. schreibgeschützten oder Lese-/Schreibzugriff, erstellen Sie mehrere Konfigurationen.

Beim Arbeiten mit CQ gibt es mehrere Methoden zum Verwalten der Konfigurationseinstellungen für solche Dienste. see [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md) für ausführliche Informationen.

Die folgenden Eigenschaften sind bei der Konfiguration eines Pool-Verbindungsdienstes verfügbar. Die Eigenschaftsnamen werden so aufgelistet, wie sie in der Web-Konsole angezeigt werden. Der entsprechende Name für einen `sling:OsgiConfig`-Knoten wird in Klammern aufgeführt. Die angegebenen Beispielwerte gelten für einen HSQLDB-Server und eine Datenbank mit dem Alias `mydb`:

* JDBC Driver Class (`jdbc.driver.class`): Die zu verwendende Java-Klasse, die die java.sql.Driver-Schnittstelle implementiert. Beispiel: `org.hsqldb.jdbc.JDBCDriver`. Der Datentyp ist `String`.

* JDBC Connection URI (`jdbc.connection.uri`): Die URL der für die Verbindungsherstellung zu verwendenden Datenbank. Beispiel: `jdbc:hsqldb:hsql//10.36.79.223:9001/mydb`. Das Format der URL muss mit der getConnection-Methode der java.sql.DriverManager-Klasse verwendbar sein. Der Datentyp ist `String`.

* Username (`jdbc.username`): Der zur Authentifizierung beim Datenbankserver zu verwendende Benutzername. Der Datentyp ist `String`.

* Password (`jdbc.password`): Das für die Authentifizierung des Benutzers zu verwendende Kennwort. Der Datentyp ist `String`.

* Validation Query (`jdbc.validation.query`): Das SQL-Statement, mit dem die erfolgreiche Verbindung bestätigt werden soll, z. B. `select 1 from INFORMATION_SCHEMA.SYSTEM_USERS`. Der Datentyp ist `String`.

* Readonly By Default (default.readonly): Wählen Sie diese Option aus, wenn die Verbindung nur Lesezugriff gewähren soll. Der Datentyp ist `Boolean`.
* Autocommit By Default (`default.autocommit`): Wählen Sie diese Option aus, um für jeden SQL-Befehl, der an die Datenbank gesendet wird, eine separate Transaktion zu erstellen. Jede Transaktion wird automatisch übergeben. Wählen Sie diese Option nicht aus, wenn Sie Transaktionen in Ihrem Code explizit übergeben. Der Datentyp ist `Boolean`.

* Pool Size (`pool.size`): Die Anzahl der gleichzeitig möglichen Verbindung mit der Datenbank. Der Datentyp ist `Long`.

* Pool wait (`pool.max.wait.msec`): Der Zeitraum bis zur Zeitüberschreitung von Verbindungsanfragen. Der Datentyp ist `Long`.

* Datasource Name (`datasource.name`): Der Name dieser Datenquelle. Der Datentyp ist `String`.

* Additional Service Properties (`datasource.svc.properties`): Eine Gruppe von Name/Wert-Paaren, die Sie an die Verbindungs-URL anhängen möchten. Der Datentyp ist `String[]`.

Der JDBC Connections Pool-Dienst ist eine Factory. Wenn Sie also einen `sling:OsgiConfig`-Knoten verwenden, um den Verbindungsdienst zu konfigurieren, muss der Name des Knotens die Factory-Dienst-PID gefolgt von *`-alias`* enthalten. Der Alias, den Sie verwenden, muss unter allen Konfigurationsknoten für diese PID eindeutig sein. Ein Beispiel für einen Knotennamen ist `com.day.commons.datasource.jdbcpool.JdbcPoolService-myhsqldbpool`.

![chlimage_1-7](assets/chlimage_1-7.png)

### Verbindung zur Datenbank aufbauen {#connecting-to-the-database}

In Ihrem Java-Code verwenden Sie den DataSourcePool-Dienst, um ein `javax.sql.DataSource`-Objekt für die Konfiguration, die Sie erstellt haben, zu erhalten. Der DataSourcePool-Dienst stellt die Methode `getDataSource` bereit, die ein `DataSource`-Objekt für einen angegebenen Datenquellennamen zurückgibt. Verwenden Sie als Argument der Methode den Wert der Datenquellennamen-Eigenschaft (oder `datasource.name`), den Sie für die JDBC Connections Pool-Konfiguration angegeben haben.

Der folgende JSP-Beispielcode ruft eine Instanz der hsqldbds-Datenquelle ab, führt eine einfache SQL-Abfrage aus und zeigt die Anzahl der zurückgegebenen Ergebnisse an.

#### JSP, das eine Datenbanksuche durchführt {#jsp-that-performs-a-database-lookup}

```java
<%@include file="/libs/foundation/global.jsp"%><%
%><%@page session="false"%><%
%><%@ page import="com.day.commons.datasource.poolservice.DataSourcePool" %><%
%><%@ page import="javax.sql.DataSource" %><%
%><%@ page import="java.sql.Connection" %><%
%><%@ page import="java.sql.SQLException" %><%
%><%@ page import="java.sql.Statement" %><%
%><%@ page import="java.sql.ResultSet"%><%
%><html>
<cq:include script="head.jsp"/>
<body>
<%DataSourcePool dspService = sling.getService(DataSourcePool.class);
  try {
     DataSource ds = (DataSource) dspService.getDataSource("hsqldbds"); 
     if(ds != null) {
         %><p>Obtained the datasource!</p><%
         %><%final Connection connection = ds.getConnection();
          final Statement statement = connection.createStatement();
          final ResultSet resultSet = statement.executeQuery("SELECT * from INFORMATION_SCHEMA.SYSTEM_USERS"); 
          int r=0;
          while(resultSet.next()){
             r=r+1;
          } 
          resultSet.close();
          %><p>Number of results: <%=r%></p><%
      } 
   }catch (Exception e) {
        %><p>error! <%=e.getMessage()%></p><%
    } 
%></body>
</html>
```

>[!NOTE]
>
>Wenn die getDataSource-Methode eine Ausnahme ausgibt, da die Datenquelle nicht gefunden wird, stellen Sie sicher, dass die Konfiguration des Connections Pool-Diensts korrekt ist. Überprüfen Sie die Eigenschaftsnamen, Werte und Datentypen.

>[!NOTE]
>
>Informationen zum Einfügen eines DataSourcePool in ein OSGi-Bundle finden Sie unter [Einfügen eines DataSourcePool-Dienstes in ein Adobe Experience Manager OSGi-Bundle](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=de&amp;CID=RedirectAEMCommunityKautuk).
