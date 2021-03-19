---
title: MySQL-Konfiguration für Aktivierungsfunktionen
seo-title: MySQL-Konfiguration für Aktivierungsfunktionen
description: MySQL-Server anschließen
seo-description: MySQL-Server anschließen
uuid: e02d9404-de75-4fdb-896c-ea3f64f980a3
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 9222bc93-c231-4ac8-aa28-30d784a4ca3b
role: 'Administrator  '
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '1101'
ht-degree: 5%

---


# MySQL-Konfiguration für Aktivierungsfunktionen {#mysql-configuration-for-enablement-features}

MySQL ist eine relationale Datenbank, die in erster Linie für die SCORM-Verfolgung und die Berichte-Daten für die Aktivierungsressourcen verwendet wird. Es sind Tabellen für andere Funktionen wie das Verfolgen der Video-Pause/-Wiederaufnahme enthalten.

Diese Anweisungen beschreiben, wie eine Verbindung zum MySQL-Server hergestellt, die Aktivierungsdatenbank eingerichtet und die Datenbank mit den Ausgangsdaten gefüllt wird.

## Voraussetzungen {#requirements}

Bevor Sie die Funktion zur Aktivierung von MySQL für Communities konfigurieren, stellen Sie sicher, dass

* [MySQL Server](https://dev.mysql.com/downloads/mysql/) Community Server Version 5.6 installieren
   * Version 5.7 wird für SCORM nicht unterstützt
   * Kann derselbe Server AEM Autoreninstanz sein
* Installieren Sie auf allen AEM Instanzen den offiziellen [JDBC-Treiber für MySQL](deploy-communities.md#jdbc-driver-for-mysql)
* [MySQL-Workbench ](https://dev.mysql.com/downloads/tools/workbench/) installieren
* Installieren Sie auf allen AEM Instanzen das [SCORM-Paket](enablement.md#scorm)

## MySQL {#installing-mysql} installieren

MySQL sollte gemäß den Anweisungen für das Zielgruppe OS heruntergeladen und installiert werden.

### Tabellennamen in Kleinbuchstaben {#lower-case-table-names}

Da bei SQL nicht zwischen Groß- und Kleinschreibung unterschieden wird, müssen bei Betriebssystemen, bei denen die Groß-/Kleinschreibung beachtet wird, alle Tabellennamen in Kleinbuchstaben eingestellt werden.

So geben Sie beispielsweise alle Tabellennamen in Kleinbuchstaben unter Linux an:

* Datei `/etc/my.cnf` bearbeiten
* Fügen Sie im Abschnitt `[mysqld]` die folgende Zeile hinzu:
   `lower_case_table_names = 1`

### UTF8-Zeichensatz {#utf-character-set}

Um eine bessere mehrsprachige Unterstützung zu bieten, muss der UTF8-Zeichensatz verwendet werden.

Ändern Sie MySQL so, dass UTF8 als Zeichensatz verwendet wird:
* mysql> SET NAMES &#39;utf8&#39;;

Ändern Sie die MySQL-Datenbank in UTF8:
* Datei `/etc/my.cnf` bearbeiten
* Fügen Sie im Abschnitt `[client]` die folgende Zeile hinzu:
   `default-character-set=utf8`
* Fügen Sie im Abschnitt `[mysqld]` die folgende Zeile hinzu:
   `character-set-server=utf8`

## MySQL Workbench {#installing-mysql-workbench} installieren

MySQL Workbench bietet eine Benutzeroberfläche zum Ausführen von SQL-Skripten, die das Schema und die Ausgangsdaten installieren.

MySQL Workbench sollte gemäß den Anweisungen für das Zielgruppe OS heruntergeladen und installiert werden.

## Aktivierungsverbindung {#enablement-connection}

Wenn MySQL Workbench zum ersten Mal gestartet wird, werden, sofern sie nicht bereits für andere Zwecke verwendet werden, noch keine Verbindungen angezeigt:

![chlimage_1-327](assets/chlimage_1-327.png)

### Neue Verbindungseinstellungen {#new-connection-settings}

1. Klicken Sie auf das Symbol &quot;+&quot;rechts neben `MySQL Connections`.
1. Geben Sie im Dialogfeld `Setup New Connection` Werte ein, die für Ihre Plattform zu Demonstrationszwecken geeignet sind, wobei sich die Autorinstanz AEM MySQL auf demselben Server befinden:
   * Verbindungsname: `Enablement`
   * Verbindungsmethode: `Standard (TCP/IP)`
   * Hostname: `127.0.0.1`
   * Benutzername: `root`
   * Passwort: `no password by default`
   * Standard-Schema: `leave blank`
1. Wählen Sie `Test Connection`, um die Verbindung zum ausgeführten MySQL-Dienst zu überprüfen

**Hinweise**:

* Der Standardanschluss ist `3306`
* Das ausgewählte `Connection Name` wird als Name `datasource` in [JDBC OSGi-Konfiguration](#configure-jdbc-connections) eingegeben

#### Erfolgreiche Verbindung {#successful-connection}

![chlimage_1-328](assets/chlimage_1-328.png)

#### Neue Aktivierungsverbindung {#new-enablement-connection}

![chlimage_1-329](assets/chlimage_1-329.png)

## Datenbank-Setup {#database-setup}

Beachten Sie beim Öffnen der neuen Aktivierungsverbindung, dass ein Test-Schema und Standardbenutzerkonten vorhanden sind.

![chlimage_1-330](assets/chlimage_1-330.png)

### Abrufen von SQL-Skripten {#obtain-sql-scripts}

Die SQL-Skripten werden mithilfe der CRXDE Lite der Autoreninstanz abgerufen. Das [SCORM-Paket](deploy-communities.md#scorm) muss installiert sein:

1. Zur CRXDE Lite navigieren
   * Beispiel: [http://localhost:4502/crx/de](http://localhost:4502/crx/de)
1. Erweitern Sie den Ordner `/libs/social/config/scorm/`
1. Download `database_scormengine.sql`
1. `database_scorm_integration.sql` herunterladen

![chlimage_1-331](assets/chlimage_1-331.png)

Eine Möglichkeit zum Herunterladen des Schemas besteht darin,

* Wählen Sie den Knoten `jcr:content`für die SQL-Datei aus
* Beachten Sie, dass der Wert für die `jcr:data`Eigenschaft ein Link zur Ansicht ist.
* Wählen Sie den Link &quot;Ansicht&quot;, um die Daten in einer lokalen Datei zu speichern

### SCORM-Datenbank erstellen {#create-scorm-database}

Die zu erstellende SCORM-Datenbank für die Aktivierung lautet:

* name: `ScormEngineDB`
* erstellt aus Skripten:
   * Schema: `database_scormengine.sql`
   * data: `database_scorm_integration.sql`
Gehen Sie wie folgt vor (
[open](#step-open-sql-file),  [execute](#step-execute-sql-script)), um jedes  [SQL-Skript](#obtain-sql-scripts)  zu installieren. [Wenn erforderlich, ](#refresh) aktualisieren Sie die Ergebnisse der Skriptausführung.

Installieren Sie das Schema, bevor Sie die Daten installieren.

>[!CAUTION]
>
>Wenn der Datenbankname geändert wird, stellen Sie sicher, dass Sie ihn in
>
>* [JDBC-Konfiguration](#configure-jdbc-connections)
>* [SCORM-Konfiguration](#configure-scorm)

>



#### Schritt 1: Öffnen Sie die SQL-Datei {#step-open-sql-file}

In der MySQL-Workbench

* Über das Pulldown-Menü Datei
* Wählen Sie nun eine der folgenden Optionen aus `Open SQL Script ...`
* Wählen Sie in dieser Reihenfolge eine der folgenden Optionen aus:
   1. `database_scormengine.sql`
   1. `database_scorm_integration.sql`

![chlimage_1-332](assets/chlimage_1-332.png)

#### Schritt 2: execute SQL Script {#step-execute-sql-script}

Wählen Sie im Fenster Workbench für die in Schritt 1 geöffnete Datei das `lightening (flash) icon` aus, um das Skript auszuführen.

Beachten Sie, dass die Ausführung des Skripts `database_scormengine.sql` zum Erstellen der SCORM-Datenbank möglicherweise eine Minute in Anspruch nehmen kann.

![chlimage_1-333](assets/chlimage_1-333.png)

#### Aktualisieren {#refresh}

Nachdem die Skripten ausgeführt wurden, müssen Sie den Abschnitt `SCHEMAS`von `Navigator` aktualisieren, damit die neue Datenbank angezeigt wird. Verwenden Sie das Aktualisierungssymbol rechts neben &quot;SCHEMAS&quot;:

![chlimage_1-334](assets/chlimage_1-334.png)

#### Ergebnis: scormenginedb {#result-scormenginedb}

Nach der Installation und Aktualisierung von SCHEMAS ist **`scormenginedb`** sichtbar.

![chlimage_1-335](assets/chlimage_1-335.png)

## JDBC-Verbindungen konfigurieren {#configure-jdbc-connections}

Die OSGi-Konfiguration für **Day Commons JDBC Connections Pool** konfiguriert den MySQL JDBC-Treiber.

Alle Veröffentlichungs- und Autoreninstanzen sollten auf denselben MySQL-Server verweisen AEM.

Wenn MySQL auf einem Server ausgeführt wird, der sich von AEM unterscheidet, muss der Hostname des Servers anstelle von &quot;localhost&quot;im JDBC-Connector angegeben werden (der die [ScormEngine](#configurescormengineservice)-Konfiguration ausfüllt).

* Auf jeder Instanz im Autorenmodus und AEM veröffentlichen
* Mit Administratorrechten angemeldet
* Zugriff auf die [Webkonsole](../../help/sites-deploying/configuring-osgi.md)
   * Beispiel: [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)
* Suchen Sie nach `Day Commons JDBC Connections Pool`
* Klicken Sie auf das Symbol `+`, um eine neue Konfiguration zu erstellen.

![chlimage_1-336](assets/chlimage_1-336.png)

* Geben Sie die folgenden Werte ein:
   * **[!UICONTROL JDBC-Treiberklasse]**: `com.mysql.jdbc.Driver`
   * **DBC-Verbindung URIJ**:  `jdbc:mysql://localhost:3306/aem63reporting` Server anstelle von localhost angeben, wenn der MySQL-Server nicht identisch mit dem &quot;this&quot;-AEM ist
   * **[!UICONTROL Benutzername]**: Stamm-Node oder geben Sie den konfigurierten Benutzernamen für den MySQL-Server ein, wenn nicht &quot;root&quot;
   * **[!UICONTROL Kennwort]**: Löschen Sie dieses Feld, wenn für MySQL kein Kennwort festgelegt wurde. Geben Sie andernfalls das konfigurierte Kennwort für den MySQL-Benutzernamen ein.
   * **[!UICONTROL Name]** der Datenquelle: Für die  [MySQL-Verbindung](#new-connection-settings) eingegebener Name, z. B. &quot;Aktivierung&quot;
* Wählen Sie **[!UICONTROL Speichern]** aus

## Scorm konfigurieren {#configure-scorm}

### AEM Communities ScormEngine Service {#aem-communities-scormengine-service}

Die OSGi-Konfiguration für **AEM Communities ScormEngine Service** konfiguriert SCORM für die Verwendung des MySQL-Servers durch eine Aktivierungsgemeinschaft.

Diese Konfiguration ist vorhanden, wenn das [SCORM-Paket](deploy-communities.md#scorm-package) installiert ist.

Alle Veröffentlichungs- und Autoreninstanzen verweisen auf denselben MySQL-Server.

Wenn MySQL auf einem Server ausgeführt wird, der sich von AEM unterscheidet, muss der Hostname des Servers anstelle von &quot;localhost&quot;im ScormEngine-Dienst angegeben werden, der normalerweise aus der [JDBC Connection](#configure-jdbc-connections)-Konfiguration gefüllt wird.

* Auf jeder Instanz im Autorenmodus und AEM veröffentlichen
* Mit Administratorrechten angemeldet
* Zugriff auf die [Webkonsole](../../help/sites-deploying/configuring-osgi.md)
   * Beispiel: [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)
* Suchen Sie nach `AEM Communities ScormEngine Service`
* Wählen Sie das Bearbeitungssymbol
   ![chlimage_1-337](assets/chlimage_1-337.png)
* Überprüfen Sie, ob die folgenden Parameterwerte mit der [JDBC Connection](#configurejdbcconnectionspool)-Konfiguration übereinstimmen:
   * **[!UICONTROL JDBC-Verbindungs-URI]**:  `jdbc:mysql://localhost:3306/ScormEngineDB` ** ScormEngineDBist der standardmäßige Datenbankname in den SQL-Skripten
   * **[!UICONTROL Benutzername]**: Stamm-Node oder geben Sie den konfigurierten Benutzernamen für den MySQL-Server ein, wenn nicht &quot;root&quot;
   * **[!UICONTROL Kennwort]**: Löschen Sie dieses Feld, wenn für MySQL kein Kennwort festgelegt wurde. Geben Sie andernfalls das konfigurierte Kennwort für den MySQL-Benutzernamen ein.
* Zum folgenden Parameter:
   * **[!UICONTROL Scorm-Benutzerkennwort]**: NICHT BEARBEITEN

      Nur zur internen Verwendung. Es ist für einen Spezialdienstbenutzer, der von AEM Communities verwendet wird, um mit der Scorm Engine zu kommunizieren.
* Wählen Sie **[!UICONTROL Speichern]** aus

### Adobe Granite CSRF Filter {#adobe-granite-csrf-filter}

Um sicherzustellen, dass Aktivierungskurse in allen Browsern korrekt funktionieren, müssen Sie Mozilla als Benutzeragent hinzufügen, der nicht vom CSRF-Filter überprüft wird.

* Auf jeder AEM
* Mit Administratorrechten angemeldet
* Zugriff auf die [Webkonsole](../../help/sites-deploying/configuring-osgi.md)
   * Beispiel: [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)
* Suchen Sie nach `Adobe Granite CSRF Filter`
* Wählen Sie das Bearbeitungssymbol
   ![chlimage_1-338](assets/chlimage_1-338.png)
* Klicken Sie auf das Symbol `[+]`, um einen sicheren Benutzeragent hinzuzufügen.
* Geben Sie Folgendes ein `Mozilla/*`
* Wählen Sie **[!UICONTROL Speichern]** aus

