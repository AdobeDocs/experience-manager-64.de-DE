---
title: MySQL-Konfiguration für Aktivierungsfunktionen
seo-title: MySQL Configuration for Enablement Features
description: Verbinden des MySQL-Servers
seo-description: Connecting your MySQL server
uuid: e02d9404-de75-4fdb-896c-ea3f64f980a3
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 9222bc93-c231-4ac8-aa28-30d784a4ca3b
role: Admin
exl-id: 1dfb55c2-41cb-445f-9bf8-f12ab6b8e9d8
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '1091'
ht-degree: 5%

---

# MySQL-Konfiguration für Aktivierungsfunktionen {#mysql-configuration-for-enablement-features}

MySQL ist eine relationale Datenbank, die hauptsächlich für SCORM-Tracking- und Reporting-Daten für Aktivierungsressourcen verwendet wird. Dazu gehören Tabellen für andere Funktionen wie das Tracking von angehaltenen/wiederaufgenommenen Videos.

In diesen Anweisungen wird beschrieben, wie Sie eine Verbindung zum MySQL-Server herstellen, die Aktivierungsdatenbank einrichten und die Datenbank mit Anfangsdaten füllen.

## Voraussetzungen {#requirements}

Stellen Sie vor der Konfiguration der Aktivierungsfunktion von MySQL für Communities sicher, dass Sie

* Installieren [MySQL-Server](https://dev.mysql.com/downloads/mysql/) Community-Server, Version 5.6
   * Version 5.7 wird für SCORM nicht unterstützt
   * Kann derselbe Server wie AEM Autoreninstanz sein
* Installieren Sie auf allen AEM Instanzen den offiziellen [JDBC-Treiber für MySQL](deploy-communities.md#jdbc-driver-for-mysql)
* Installieren [MySQL Workbench](https://dev.mysql.com/downloads/tools/workbench/)
* Installieren Sie auf allen AEM die [SCORM-Paket](enablement.md#scorm)

## MySQL installieren {#installing-mysql}

MySQL sollte heruntergeladen und entsprechend den Anweisungen für das Zielbetriebssystem installiert werden.

### Tabellennamen mit Kleinbuchstaben {#lower-case-table-names}

Da bei SQL nicht zwischen Groß- und Kleinschreibung unterschieden wird, müssen bei Betriebssystemen, bei denen zwischen Groß- und Kleinschreibung unterschieden wird, alle Tabellennamen in Kleinbuchstaben geschrieben werden.

So geben Sie beispielsweise alle Tabellennamen mit Kleinbuchstaben unter Linux an:

* Datei bearbeiten `/etc/my.cnf`
* Im `[mysqld]` -Abschnitt, fügen Sie die folgende Zeile hinzu:
   `lower_case_table_names = 1`

### UTF8-Zeichensatz {#utf-character-set}

Um eine bessere mehrsprachige Unterstützung zu bieten, ist es erforderlich, den UTF8-Zeichensatz zu verwenden.

Ändern Sie MySQL so, dass UTF8 als Zeichensatz verwendet wird:
* mysql> SET NAMES &#39;utf8&#39;;

Ändern Sie die MySQL-Datenbank in UTF8:
* Datei bearbeiten `/etc/my.cnf`
* Im `[client]` -Abschnitt, fügen Sie die folgende Zeile hinzu:
   `default-character-set=utf8`
* Im `[mysqld]` -Abschnitt, fügen Sie die folgende Zeile hinzu:
   `character-set-server=utf8`

## Installieren von MySQL Workbench {#installing-mysql-workbench}

MySQL Workbench bietet eine Benutzeroberfläche zum Ausführen von SQL-Skripten, die das Schema und die Anfangsdaten installieren.

MySQL Workbench sollte heruntergeladen und entsprechend den Anweisungen für das Zielbetriebssystem installiert werden.

## Aktivierungsverbindung {#enablement-connection}

Wenn die MySQL Workbench zum ersten Mal gestartet wird, sofern sie nicht bereits für andere Zwecke verwendet wird, werden noch keine Verbindungen angezeigt:

![chlimage_1-327](assets/chlimage_1-327.png)

### Neue Verbindungseinstellungen {#new-connection-settings}

1. Wählen Sie rechts neben dem Symbol &quot;+&quot;das Symbol `MySQL Connections`.
1. Im Dialogfeld `Setup New Connection`Geben Sie Werte ein, die für Ihre Plattform zu Demonstrationszwecken geeignet sind, wobei sich die Autoreninstanz AEM MySQL auf demselben Server befindet:
   * Verbindungsname: `Enablement`
   * Verbindungsmethode: `Standard (TCP/IP)`
   * Hostname: `127.0.0.1`
   * Benutzername: `root`
   * Passwort: `no password by default`
   * Standardschema: `leave blank`
1. Auswählen `Test Connection` Überprüfen der Verbindung zum ausgeführten MySQL-Dienst

**Anmerkungen**:

* Der Standardanschluss ist `3306`
* Die `Connection Name` ausgewählt wird, wird als `datasource` name in [JDBC OSGi-Konfiguration](#configure-jdbc-connections)

#### Erfolgreiche Verbindung {#successful-connection}

![chlimage_1-328](assets/chlimage_1-328.png)

#### Neue Aktivierungsverbindung {#new-enablement-connection}

![chlimage_1-329](assets/chlimage_1-329.png)

## Datenbankeinrichtung {#database-setup}

Beachten Sie beim Öffnen der neuen Aktivierungsverbindung, dass es ein Testschema und standardmäßige Benutzerkonten gibt.

![chlimage_1-330](assets/chlimage_1-330.png)

### Abrufen von SQL-Skripten {#obtain-sql-scripts}

Die SQL-Skripte werden mithilfe der CRXDE Lite in der Autoreninstanz abgerufen. Die [SCORM-Paket](deploy-communities.md#scorm) muss installiert sein:

1. Zur CRXDE Lite navigieren
   * Beispiel: [http://localhost:4502/crx/de](http://localhost:4502/crx/de)
1. Erweitern Sie die `/libs/social/config/scorm/` Ordner
1. Download `database_scormengine.sql`
1. Download `database_scorm_integration.sql`

![chlimage_1-331](assets/chlimage_1-331.png)

Eine Methode zum Herunterladen des Schemas besteht darin,

* Wählen Sie die `jcr:content`Knoten für die SQL-Datei
* Beachten Sie den Wert für `jcr:data`-Eigenschaft ist ein Ansichtslink
* Klicken Sie auf den Ansichtslink, um die Daten in einer lokalen Datei zu speichern.

### SCORM-Datenbank erstellen {#create-scorm-database}

Die zu erstellende Aktivierungs-SCORM-Datenbank lautet:

* name: `ScormEngineDB`
* erstellt aus Skripten:
   * schema: `database_scormengine.sql`
   * data: `database_scorm_integration.sql`
Führen Sie die folgenden Schritte aus (
[open](#step-open-sql-file), [execute](#step-execute-sql-script)), um jede [SQL-Skript](#obtain-sql-scripts) . [Aktualisieren](#refresh) wenn nötig, um die Ergebnisse der Skriptausführung anzuzeigen.

Installieren Sie das Schema, bevor Sie die Daten installieren.

>[!CAUTION]
>
>Wenn der Datenbankname geändert wird, geben Sie ihn in
>
>* [JDBC-Konfiguration](#configure-jdbc-connections)
>* [SCORM-Konfiguration](#configure-scorm)

>


#### Schritt 1: SQL-Datei öffnen {#step-open-sql-file}

In der MySQL Workbench

* Über das Pulldown-Menü Datei
* Wählen Sie nun eine der folgenden Optionen aus `Open SQL Script ...`
* Wählen Sie in dieser Reihenfolge eine der folgenden Optionen aus:
   1. `database_scormengine.sql`
   1. `database_scorm_integration.sql`

![chlimage_1-332](assets/chlimage_1-332.png)

#### Schritt 2: SQL-Skript ausführen {#step-execute-sql-script}

Wählen Sie im Workbench-Fenster für die in Schritt 1 geöffnete Datei die `lightening (flash) icon` , um das Skript auszuführen.

Beachten Sie, dass die `database_scormengine.sql` -Skript zur Erstellung der SCORM-Datenbank benötigen, kann es eine Minute dauern.

![chlimage_1-333](assets/chlimage_1-333.png)

#### Aktualisieren {#refresh}

Nach Ausführung der Skripte muss die `SCHEMAS`Abschnitt `Navigator` um die neue Datenbank zu sehen. Verwenden Sie das Aktualisierungssymbol rechts neben &quot;SCHEMAS&quot;:

![chlimage_1-334](assets/chlimage_1-334.png)

#### Ergebnis: scormenginedb {#result-scormenginedb}

Nach der Installation und Aktualisierung von SCHEMAS wird die **`scormenginedb`** angezeigt.

![chlimage_1-335](assets/chlimage_1-335.png)

## JDBC-Verbindungen konfigurieren {#configure-jdbc-connections}

Die OSGi-Konfiguration für **Day Commons JDBC Connections Pool** konfiguriert den MySQL JDBC-Treiber.

Alle Veröffentlichungs- und AEM-Instanzen sollten auf denselben MySQL-Server verweisen.

Wenn MySQL auf einem Server ausgeführt wird, der sich von AEM unterscheidet, muss der Hostname des Servers anstelle von &quot;localhost&quot;im JDBC-Connector angegeben werden (der den [ScormEngine](#configurescormengineservice) config).

* In jeder AEM der Autoren- und Veröffentlichungsinstanz
* Mit Administratorrechten angemeldet
* Zugriff auf [Webkonsole](../../help/sites-deploying/configuring-osgi.md)
   * Beispiel: [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)
* Suchen Sie die `Day Commons JDBC Connections Pool`
* Wählen Sie die `+` Symbol zum Erstellen einer neuen Konfiguration

![chlimage_1-336](assets/chlimage_1-336.png)

* Geben Sie die folgenden Werte ein:
   * **[!UICONTROL JDBC-Treiberklasse]**: `com.mysql.jdbc.Driver`
   * **DBC-Verbindung URIJ**: `jdbc:mysql://localhost:3306/aem63reporting` den Server anstelle von localhost angeben, wenn der MySQL-Server nicht mit dem &#39;this&#39;-AEM Server übereinstimmt
   * **[!UICONTROL Benutzername]**: Stamm oder geben Sie den konfigurierten Benutzernamen für den MySQL-Server ein, falls nicht &quot;root&quot;
   * **[!UICONTROL Passwort]**: Löschen Sie dieses Feld, wenn kein Kennwort für MySQL festgelegt ist. Geben Sie andernfalls das konfigurierte Kennwort für den MySQL-Benutzernamen ein.
   * **[!UICONTROL Datenquellenname]**: Der für die [MySQL-Verbindung](#new-connection-settings), z. B. &quot;Aktivierung&quot;
* Wählen Sie **[!UICONTROL Speichern]** aus

## Scorm konfigurieren {#configure-scorm}

### AEM Communities ScormEngine-Dienst {#aem-communities-scormengine-service}

Die OSGi-Konfiguration für **AEM Communities ScormEngine-Dienst** konfiguriert SCORM für die Verwendung des MySQL-Servers durch eine Aktivierungs-Community.

Diese Konfiguration ist vorhanden, wenn die [SCORM-Paket](deploy-communities.md#scorm-package) installiert ist.

Alle Veröffentlichungs- und Autoreninstanzen verweisen auf denselben MySQL-Server.

Wenn MySQL auf einem Server ausgeführt wird, der sich von AEM unterscheidet, muss der Server-Hostname anstelle von &quot;localhost&quot;im ScormEngine-Dienst angegeben werden, der normalerweise aus dem [JDBC-Verbindung](#configure-jdbc-connections) config.

* In jeder AEM der Autoren- und Veröffentlichungsinstanz
* Mit Administratorrechten angemeldet
* Zugriff auf [Webkonsole](../../help/sites-deploying/configuring-osgi.md)
   * Beispiel: [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)
* Suchen Sie die `AEM Communities ScormEngine Service`
* Bearbeiten-Symbol auswählen
   ![chlimage_1-337](assets/chlimage_1-337.png)
* Stellen Sie sicher, dass die folgenden Parameterwerte mit dem [JDBC-Verbindung](#configurejdbcconnectionspool) config:
   * **[!UICONTROL JDBC-Verbindungs-URI]**: `jdbc:mysql://localhost:3306/ScormEngineDB` *ScormEngineDB* ist der standardmäßige Datenbankname in SQL-Skripten
   * **[!UICONTROL Benutzername]**: Stamm oder geben Sie den konfigurierten Benutzernamen für den MySQL-Server ein, falls nicht &quot;root&quot;
   * **[!UICONTROL Passwort]**: Löschen Sie dieses Feld, wenn kein Kennwort für MySQL festgelegt ist. Geben Sie andernfalls das konfigurierte Kennwort für den MySQL-Benutzernamen ein.
* Für den folgenden Parameter:
   * **[!UICONTROL Scorm-Benutzerkennwort]**: NICHT BEARBEITEN

      Nur zur internen Verwendung. Es ist für einen speziellen Dienstbenutzer bestimmt, der von AEM Communities zur Kommunikation mit der Scorm-Engine verwendet wird.
* Wählen Sie **[!UICONTROL Speichern]** aus

### Adobe Granite CSRF-Filter {#adobe-granite-csrf-filter}

Um sicherzustellen, dass Aktivierungskurse in allen Browsern ordnungsgemäß funktionieren, muss Mozilla als Benutzeragent hinzugefügt werden, der nicht vom CSRF-Filter überprüft wird.

* Bei jeder AEM-Instanz
* Mit Administratorrechten angemeldet
* Zugriff auf [Webkonsole](../../help/sites-deploying/configuring-osgi.md)
   * Beispiel: [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)
* Suchen `Adobe Granite CSRF Filter`
* Bearbeiten-Symbol auswählen
   ![chlimage_1-338](assets/chlimage_1-338.png)
* Wählen Sie die `[+]` Symbol zum Hinzufügen eines sicheren Benutzeragenten
* Geben Sie `Mozilla/*` ein
* Wählen Sie **[!UICONTROL Speichern]** aus
