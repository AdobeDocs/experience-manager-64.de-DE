---
title: Bereitstellen von Communities
seo-title: Bereitstellen von Communities
description: Bereitstellen von AEM Communities
seo-description: Bereitstellen von AEM Communities
uuid: 1f7faf1a-a339-4eaa-b728-b9110cb350a8
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
content-type: reference
topic-tags: deploying
discoiquuid: d0249609-2a9c-4d3b-92ee-dbc5fbdeaac6
translation-type: tm+mt
source-git-commit: 9d03a3988b2c8e34b9009d80a53d8b8508b5f0aa

---


# Bereitstellen von Communities {#deploying-communities}

## Voraussetzungen {#prerequisites}

* [AEM 6.4-Plattform](../../help/sites-deploying/deploy.md)

* AEM Communities-Lizenz

* Optionale Lizenzen für:

   * [Funktionen von Adobe Analytics für Communities](analytics.md)
   * [MongoDB für MSRP](msrp.md)
   * [Adobe Cloud für ASRP](asrp.md)

## Checkliste für die Installation {#installation-checklist}

**Für die[AEM-Plattform](../../help/sites-deploying/deploy.md#what-is-aem)**

* Neueste [AEM 6.4-Updates installieren](#aem-updates)

* Wenn Sie nicht die Standardanschlüsse (4502, 4503) verwenden, [konfigurieren Sie Replizierungsagenten](#replication-agents-on-author)
* [Verschlüsselungsschlüssel replizieren](#replicate-the-crypto-key)
* Bei Unterstützung der Globalisierung [richten Sie die automatisierte Übersetzung ein](../../help/sites-administering/translation.md)

   (Beispiel-Setup wird für die Entwicklung bereitgestellt)

**Fähigkeit &quot;[Communities&quot;](overview.md)**

* Wenn Sie eine [Veröffentlichungsfarm](../../help/sites-deploying/recommended-deploys.md#tarmk-farm)bereitstellen, [müssen Sie den primären Herausgeber](#primary-publisher)

* [Aktivieren des Tunneldienstes](#tunnel-service-on-author)
* [Aktivieren der Social-Anmeldung](social-login.md#adobe-granite-oauth-authentication-handler)
* [Konfigurieren Sie Analytics](analytics.md)
* Einrichten eines [Standard-E-Mail-Dienstes](email.md)
* Identifizieren Sie die Wahl für [freigegebenen UGC-Speicher](working-with-srp.md) (**SRP**).

   * Wenn MongoDB SRP [(MSRP)](msrp.md)

      * [MongoDB installieren und konfigurieren](msrp.md#mongodb-configuration)
      * [Solr konfigurieren](solr.md)
      * [MSRP auswählen](srp-config.md)
   * Bei relationaler Datenbank SRP [(DSRP)](dsrp.md)

      * [JDBC-Treiber für MySQL installieren](#jdbc-driver-for-mysql)
      * [MySQL für DSRP installieren und konfigurieren](dsrp-mysql.md)
      * [Solr konfigurieren](solr.md)
      * [DSRP auswählen](srp-config.md)
   * Wenn Adobe SRP [(ASRP)](asrp.md)

      * Wenden Sie sich zwecks Bereitstellung an Ihren Kundenbetreuer
      * [ASRP auswählen](srp-config.md)
   * Wenn JCR SRP [(JSRP)](jsrp.md)

      * Kein freigegebener UGC-Store:

         * UGC wird nie repliziert
         * UGC ist nur auf der AEM-Instanz oder dem AEM-Cluster sichtbar, in dem sie eingegeben wurde
      * Standard ist JSRP
   Für die **[Aktivierungsfunktion](overview.md#enablement-community)**

   * [FFmpeg installieren und konfigurieren](ffmpeg.md)
   * [JDBC-Treiber für MySQL installieren](#jdbc-driver-for-mysql)
   * [Installieren der AEM Communities SCORM-Engine](#scorm-package)
   * [MySQL für die Aktivierung installieren und konfigurieren](mysql.md)






## Neueste Versionen {#latest-releases}

AEM 6.4 Communities GA wird mit Communities-Paketen geliefert. Informationen zu Updates für AEM 6.4 [Communities](/help/release-notes/release-notes.md#experience-manager-communities)finden Sie in den [Versionshinweisen](/help/release-notes/release-notes.md#release-information)zu AEM 6.4.

### AEM 6.4 Updates {#aem-updates}

Ab AEM 6.3 werden Updates für Communities als Teil von AEM Cumulative Fix Packs und Service Packs bereitgestellt.

Die neuesten Updates für AEM 6.4 finden Sie in [Adobe Experience Manager 6.4 Cumulative Fix Packs and Service Packs](https://helpx.adobe.com/experience-manager/aem-releases-updates.html).

### Version History {#version-history}

Wie bei AEM 6.4 und höher sind AEM Communities-Funktionen und Hotfixes Teil der kumulativen Fix Packs und Service Packs von AEM Communities. Es gibt daher keine separaten Feature Packs.

### JDBC-Treiber für MySQL {#jdbc-driver-for-mysql}

Zwei Communities-Funktionen verwenden eine MySQL-Datenbank:

* Für [Aktivierung](enablement.md): Aufzeichnung von SCORM-Aktivitäten und -Lernenden
* Für [DSRP](dsrp.md): Speichern benutzergenerierter Inhalte (UGC)

Der MySQL-Connector muss separat bezogen und installiert werden.

Die erforderlichen Schritte sind:

1. ZIP-Archiv von [https://dev.mysql.com/downloads/connector/j/ herunterladen](https://dev.mysql.com/downloads/connector/j/)

   * Version muss >= 5.1.38 sein

1. Extrahieren Sie mysql-connector-java-&lt;version>-bin.jar (bundle) aus dem Archiv

1. Verwenden Sie die Webkonsole, um das Bundle zu installieren und zu starten:

   * Beispiel: http://localhost:4502/system/console/bundles
   * Wählen Sie nun eine der folgenden Optionen aus **`Install/Update`**
   * Durchsuchen... zum Auswählen des aus dem heruntergeladenen ZIP-Archiv extrahierten Bundles
   * Überprüfen Sie, ob der JDBC-Treiber der *Oracle Corporation für MySQLcom.mysql.jdbc* aktiv ist, und starten Sie ihn gegebenenfalls (oder überprüfen Sie die Protokolle)

1. Wenn Sie nach der Konfiguration von JDBC in einer vorhandenen Bereitstellung installieren, binden Sie JDBC erneut an den neuen Connector, indem Sie die JDBC-Konfiguration aus der Webkonsole erneut binden:

   * Beispiel: http://localhost:4502/system/console/configMgr
   * Suchen `Day Commons JDBC Connections Pool` der Konfiguration
   * Zum Öffnen auswählen
   * Wählen Sie nun eine der folgenden Optionen aus `Save`

1. Wiederholen Sie die Schritte 3 und 4 für alle Autoren- und Veröffentlichungsinstanzen.

Weitere Informationen zum Installieren von Bundles finden Sie auf der Seite [Web-Konsole](/help/sites-deploying/web-console.md#bundles) .

#### Beispiel: Installiertes MySQL Connector-Bundle {#example-installed-mysql-connector-bundle}

![chlimage_1-410](assets/chlimage_1-410.png)

### SCORM-Paket {#scorm-package}

Das Shareable Content Object Reference Model (SCORM) ist eine Sammlung von Standards und Spezifikationen für eLearning. SCORM definiert auch, wie Inhalte in eine übertragbare ZIP-Datei verpackt werden können.

Die AEM Communities SCORM-Engine ist für die [Aktivierungsfunktion](overview.md#enablement-community) erforderlich. Für AEM Communities 6.4 werden folgende Scorm-Pakete unterstützt:

* **[cq -social- scorm -package, Version 1.2.11](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/scorm/cq-social-scorm-pkg)**. Dieses SCORM-Paket wird von allen Versionen von AEM 6.4 Communities unterstützt.

* **[cq -social- scorm -package, Version 2.2.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/scorm/cq-social-scorm-2017-pkg)**enthält die[SCORM 2017.1](https://rusticisoftware.com/blog/scorm-engine-2017-released/)Engine. Dieses SCORM-Paket wird ab AEM 6.4.2.x Communities unterstützt.

Für eine Neuinstallation der SCORM Engine sollte das Paket verwendet werden, das [SCORM 2017.1](https://rusticisoftware.com/blog/scorm-engine-2017-released/) enthält (was [ cq -social- scorm -package, Version 2.2.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/scorm/cq-social-scorm-2017-pkg)ist). Damit Sie Lernressourcen spielen können, die von SCORM 2017 unterstützt werden.

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### So installieren Sie ein SCORM-Paket zum ersten Mal

1. Installieren Sie das **[cq-social-scorm-package, Version 2.2.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/scorm/cq-social-scorm-2017-pkg).**
1. Laden Sie **`/libs/social/config/scorm/database_scormengine_data.sql`** von der cq-Instanz herunter und führen Sie sie auf dem mysql-Server aus, um ein aktualisiertes scormEngineDB-Schema zu erstellen.
1. Fügen Sie `/content/communities/scorm/RecordResults` die Eigenschaft Ausgeschlossene Pfade im CSRF-Filter von Herausgebern `https://<hostname>;:<port>/system/console/configMgr` hinzu.

Bestehende SCORM-Installationen können auf [**cq-social-scorm-package, Version 2.2.2 **](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/scorm/cq-social-scorm-2017-pkg)(die[SCORM 2017.1](https://rusticisoftware.com/blog/scorm-engine-2017-released/)verwendet) aktualisiert werden, wenn für die erstellten Kursinhalte SCORM 2017.1 erforderlich ist.

>[!NOTE]
>
>Die Aktualisierung auf das SCORM 2017.1-Paket erfordert die Migration der vorhandenen Datenbank (wie weiter erläutert).

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### So aktualisieren Sie die Version der SCORM-Engine

1. Erstellen Sie eine Sicherungskopie des ScormEngineDB-Schemas.
1. Installieren Sie das **[cq-social-scorm-package, Version 2.2.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/scorm/cq-social-scorm-2017-pkg).**
1. Laden Sie das Paket herunter `/libs/social/config/scorm/ScormEngine.zip` und extrahieren Sie es.
1. Wechseln Sie zum Ordner **Installer** des extrahierten Ordners.
1. Aktualisieren Sie `SystemDatabaseConnectionString` mit Ihrer `scorm db connection url` Datei **[!UICONTROL EngineInstall.xml]**.
1. Führen Sie das Aktualisierungstool für das mysql-Schema im Installationsordner mit folgendem Befehl aus:

   `java -Dlogback.configurationFile=logback.xml -cp "lib/*" RusticiSoftware.ScormContentPlayer.Logic.Upgrade.ConsoleApp EngineInstall.xml`
1. Überwachen Sie die `engine_upgrade.log` Datei auf alle Fehler- und Schemaaktualisierungsstatus.
1. Fügen Sie `/content/communities/scorm/RecordResults` die Eigenschaft &quot; **[!UICONTROL Ausgeschlossene Pfade]** &quot;im CSRF-Filter von Herausgebern `https://<hostname>:<port>/system/console/configMgr` hinzu.

### SCORM-Protokollierung {#scorm-logging}

Nach der Installation werden alle Aktivierungsaktivitäten ausführlich an die Systemkonsole protokolliert.

Bei Bedarf kann die Protokollebene für das `RusticiSoftware.*` Paket auf WARN eingestellt werden.

Informationen zum Arbeiten mit Protokollen finden Sie unter [Arbeiten mit Audit-Aufzeichnungen und Protokolldateien](../../help/sites-deploying/monitoring-and-maintaining.md#working-with-audit-records-and-log-files).

### AEM Advanced MLS {#aem-advanced-mls}

Damit die SRP-Sammlung (MSRP oder DSRP) die erweiterte mehrsprachige Suche (MLS) unterstützen kann, sind zusätzlich zu einer benutzerdefinierten Schema- und Solr-Konfiguration neue Solr-Plug-Ins erforderlich. Alle erforderlichen Elemente werden in einer herunterladbaren ZIP-Datei zusammengefasst.

Der erweiterte MLS-Download (auch &quot;phasetwo&quot;genannt) ist im Adobe-Repository verfügbar:

* [AEM-SOLR-MLS-phasetwo](https://repo.adobe.com/nexus/content/repositories/releases/com/adobe/tat/AEM-SOLR-MLS-phasetwo/1.2.40/)

   * Version 1.2.40, 6. April 2016
   * Herunterladen von AEM-SOLR-MLS-phasetwo-1.2.40.zip

Weitere Informationen und Installationsinformationen finden Sie unter [Solr-Konfiguration](solr.md) für SRP.

### Über Links zur Paketfreigabe {#about-links-to-package-share}

**In Adobe AEM Cloud sichtbare Pakete**

Die Links zu Paketen auf dieser Seite erfordern keine laufende Instanz von AEM, da sie für die Paketfreigabe vorgesehen sind `adobeaemcloud.com`. Während die Pakete angezeigt werden können, wird die `Install`Schaltfläche zum Installieren der Pakete auf einer von Adobe gehosteten Site verwendet. Wenn Sie beabsichtigen, eine Installation auf einer lokalen AEM-Instanz durchzuführen, `Install`führt die Auswahl zu einem Fehler.

**Installation auf lokaler AEM-Instanz**

Um die Pakete zu installieren, die in `adobeaemcloud.com` einer lokalen AEM-Instanz sichtbar sind, muss das Paket zunächst auf eine lokale Festplatte heruntergeladen werden:

* Select the **[!UICONTROL Assets]** tab
* Select **[!UICONTROL download to disk]**

Verwenden Sie auf der lokalen AEM-Instanz Package Manager (z. B. [http://localhost:4502/crx/packmgr/](http://localhost:4502/crx/packmgr/)), um das Paket-Repository von AEM in das lokale AEM-Repository hochzuladen.

Alternativ können Sie über Package Share von der lokalen AEM-Instanz aus (z. B. [http://localhost:4502/crx/packageshare/](http://localhost:4502/crx/packageshare/)) auf das Paket zugreifen. Die `Download`Schaltfläche wird dann in das Paket-Repository der lokalen AEM-Instanz heruntergeladen.

Sobald Sie sich im Paket-Repository der lokalen AEM-Instanz befinden, installieren Sie das Paket mit Package Manager.

Weitere Informationen finden Sie unter [Arbeiten mit Paketen](../../help/sites-administering/package-manager.md#package-share).

## Empfohlene Bereitstellungen {#recommended-deployments}

In AEM Communities wird ein gemeinsamer Speicher zum Speichern benutzergenerierter Inhalte (UGC) verwendet und häufig als [Speicherressourcenanbieter (SRP)](working-with-srp.md)bezeichnet. Die empfohlene Bereitstellung konzentriert sich auf die Auswahl einer SRP-Option für den gemeinsamen Speicher.

Der gemeinsame Speicher unterstützt die Moderation und Analyse von UGC in der Veröffentlichungsumgebung, während gleichzeitig keine [Replikation](sync.md) von UGC erforderlich ist.

* [Community Content Store](working-with-srp.md): beschreibt die SRP-Speicheroptionen für AEM Communities

* [Empfohlene Topologien](topologies.md): die je nach Anwendungsfall und SRP-Auswahl zu verwendende Topologie

## Aktualisieren {#upgrading}

Bei der Aktualisierung von früheren Versionen von AEM auf die AEM 6.4-Plattform ist es wichtig, dass Sie unter Aktualisierung auf AEM 6.4 lesen.

Lesen Sie neben der Aktualisierung der Plattform auch [Aktualisieren auf AEM Communities 6.4](upgrade.md) , um mehr über Änderungen in Communities zu erfahren.

## Konfigurationen {#configurations}

### Herausgeber {#primary-publisher}

Wenn es sich bei der gewählten Bereitstellung um eine [Veröffentlichungsfarm](topologies.md#tarmk-publish-farm)handelt, muss eine AEM-Veröffentlichungsinstanz als die **`primary publisher`** für Aktivitäten identifiziert werden, die nicht in allen Instanzen auftreten sollten, z. B. Funktionen, die auf **Benachrichtigungen** oder **Adobe Analytics** basieren.

Standardmäßig wird die `AEM Communities Publisher Configuration` OSGi-Konfiguration mit dem Kontrollkästchen **`Primary Publisher`** konfiguriert, sodass alle Instanzen im Veröffentlichungsmodus in einer Veröffentlichungsfarm sich selbst als Primär identifizieren.

Daher müssen Sie die Konfiguration für alle sekundären Veröffentlichungsinstanzen **bearbeiten, um das Kontrollkästchen zu deaktivieren** . **`Primary Publisher`**

![chlimage_1-411](assets/chlimage_1-411.png)

Für alle anderen (sekundären) Instanzen im Veröffentlichungsmodus:

* Anmelden mit Administratorberechtigungen
* Access the [web console](../../help/sites-deploying/configuring-osgi.md)

   * For example, [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Suchen Sie die `AEM Communities Publisher Configuration`
* Wählen Sie das Bearbeitungssymbol
* Deaktivieren Sie das Kontrollkästchen **[!UICONTROL Primärherausgeber]** .
* Wählen Sie **[!UICONTROL Speichern]**

### Replizierungsagenten beim Autor {#replication-agents-on-author}

Die Replikation wird für Site-Inhalte verwendet, die in der Veröffentlichungsumgebung erstellt wurden, z. B. Community-Gruppen, sowie für die Verwaltung von Mitgliedern und Mitgliedsgruppen aus der Autorenumgebung mithilfe des [Tunneldienstes](#tunnel-service-on-author).

Stellen Sie für den primären Herausgeber sicher, dass die [Replication Agent-Konfiguration](../../help/sites-deploying/replication.md) den Veröffentlichungsserver und den autorisierten Benutzer richtig identifiziert. Der standardmäßig autorisierte Benutzer hat `admin,` bereits die entsprechenden Berechtigungen (ist Mitglied von `Communities Administrators`).

Damit andere Benutzer über die entsprechenden Berechtigungen verfügen können, müssen sie als Mitglied der `administrators` Benutzergruppe (auch Mitglied von `Communities Administrators`) hinzugefügt werden.

Es gibt zwei Replizierungsagenten in der Autorenumgebung, für die die Transportkonfiguration richtig konfiguriert werden muss.

* Zugriff auf die Replikationskonsole beim Autor

   * Aus globaler Navigation: **[!UICONTROL Werkzeuge > Bereitstellung > Replikation > Agenten beim Autor]**

* Für beide Wirkstoffe gilt das gleiche Verfahren:

   * **Standardagent (veröffentlichen)**
   * **Agenten für Rückwärtsreplikation (Rückwärtsveröffentlichen)**

      1. Agent auswählen
      1. Select **[!UICONTROL edit]**
      1. Select the **[!UICONTROL Transport]** tab
      1. Wenn kein Anschluss vorhanden `4503`ist, bearbeiten Sie den **[!UICONTROL URI]** , um den richtigen Anschluss anzugeben.
      1. Falls kein Benutzer `admin`, bearbeiten Sie **[!UICONTROL Benutzer]** und **[!UICONTROL Kennwort]** , um ein Mitglied der `administrators` Benutzergruppe anzugeben.

Die folgenden Abbildungen zeigen die Ergebnisse einer Änderung des Anschlusses von 4503 auf 6103 durch:

#### Standardagent (veröffentlichen) {#default-agent-publish}

![chlimage_1-412](assets/chlimage_1-412.png)

#### Agenten für Rückwärtsreplikation (Rückwärtsveröffentlichen) {#reverse-replication-agent-publish-reverse}

![chlimage_1-413](assets/chlimage_1-413.png)

### Tunneldienst beim Autor {#tunnel-service-on-author}

Wenn Sie die Autorenumgebung zum [Erstellen von Sites](sites-console.md), zum [Ändern von Site-Eigenschaften](sites-console.md#modifying-site-properties) oder zum [Verwalten von Community-Mitgliedern](members.md)verwenden, müssen Sie auf Mitglieder (Benutzer) zugreifen, die in der Veröffentlichungsumgebung registriert sind, nicht auf Benutzer, die beim Autor registriert sind.

Der Tunneldienst bietet diesen Zugriff mithilfe des Replizierungsagenten beim Autor.

So aktivieren Sie den Tunneldienst:

* On **author**
* Anmelden mit Administratorrechten
* Wenn der Herausgeber nicht localhost:4503 ist oder der Transportbenutzer nicht `admin`,

   Then [configure the replication agent](#replication-agents-on-author)

* Access the [Web Console](../../help/sites-deploying/configuring-osgi.md)

   * For example, [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)

* Suchen Sie die `AEM Communities Publish Tunnel Service`
* Wählen Sie das Bearbeitungssymbol
* Aktivieren Sie das **[!UICONTROL Kontrollkästchen &quot;Aktivieren]** &quot;
* Wählen Sie **[!UICONTROL Speichern]**

![chlimage_1-414](assets/chlimage_1-414.png)

### Crypto-Schlüssel replizieren {#replicate-the-crypto-key}

Es gibt zwei Funktionen von AEM Communities, bei denen alle AEM-Serverinstanzen dieselben Verschlüsselungsschlüssel verwenden müssen. Dies sind [Analytics](analytics.md) und [ASRP](asrp.md).

Ab AEM 6.3 wird das Schlüsselmaterial im Dateisystem und nicht mehr im Repository gespeichert.

Um das Schlüsselmaterial vom Autor in alle anderen Instanzen zu kopieren, müssen Sie:

* Greifen Sie auf die AEM-Instanz zu, normalerweise eine Autoreninstanz, die das zu kopierende Schlüsselmaterial enthält

   * Locate the `com.adobe.granite.crypto.file` bundle in the local file system

      Beispiel:

      * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21`
      * Die `bundle.info` Datei identifiziert das Bundle
   * In den Datenordner navigieren

      Beispiel:

      * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`
   * Kopieren Sie die hmac- und master-Dateien



* Für jede AEM-Zielinstanz

   * In den Datenordner navigieren

      Beispiel:

      * `<publish-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`
   * Einfügen der zuvor kopierten zwei Dateien
   * Das Granite Crypto-Bundle muss [aktualisiert werden, wenn die AEM-Zielinstanz derzeit ausgeführt wird](#refresh-the-granite-crypto-bundle) .


>[!CAUTION]
>
>Wenn bereits eine andere Sicherheitsfunktion konfiguriert wurde, die auf den Verschlüsselungsschlüsseln basiert, könnte die Replizierung der Verschlüsselungsschlüssel die Konfiguration beschädigen. Wenden Sie sich zwecks Hilfe [an die Kundenunterstützung](https://helpx.adobe.com/marketing-cloud/contact-support.html).

#### Repository-Replikation {#repository-replication}

Die Speicherung des Schlüsselmaterials im Repository ist wie bei AEM 6.2 und früher möglich, indem Sie beim ersten Start jeder AEM-Instanz (die das anfängliche Repository erstellt) die folgende Systemeigenschaft angeben:

* `-Dcom.adobe.granite.crypto.file.disable=true`

>[!NOTE]
>
>Es ist wichtig zu überprüfen, ob der [Replizierungsagenten beim Autor](#replication-agents-on-author) richtig konfiguriert ist.

Wenn das Schlüsselmaterial im Repository gespeichert ist, erfolgt die Replizierung des Verschlüsselungsschlüssels vom Autor zu anderen Instanzen wie folgt:

Using [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Navigieren Sie zu [https://&lt;server>:&lt;port>/crx/de](http://localhost:4502/crx/de)
* auswählen `/etc/key`
* Register öffnen `Replication`
* auswählen `Replicate`

* [Granite Crypto-Bundle aktualisieren](#refresh-the-granite-crypto-bundle)

![chlimage_1-415](assets/chlimage_1-415.png)

#### Granite Crypto-Bundle aktualisieren {#refresh-the-granite-crypto-bundle}

* Greifen Sie auf jeder Instanz im Veröffentlichungsmodus auf die [Web-Konsole zu](../../help/sites-deploying/configuring-osgi.md)

   * Beispiel: [https://&lt;server>:&lt;port>/system/console/bundles](http://localhost:4503/system/console/bundles)

* Suchen Sie nach `Adobe Granite Crypto Support` Bundle (com.adobe.granite.crypto)
* Wählen Sie **[!UICONTROL Aktualisieren]**

![chlimage_1-416](assets/chlimage_1-416.png)

* Nach einem Augenblick sollte ein **Erfolgsdialogfeld** angezeigt werden:

   `Operation completed successfully.`

### Apache HTTP Server {#apache-http-server}

Wenn Sie den Apache HTTP-Server verwenden, stellen Sie sicher, dass Sie den richtigen Servernamen für alle relevanten Einträge verwenden.

Achten Sie insbesondere darauf, den richtigen Servernamen zu verwenden, nicht `localhost`in der `RedirectMatch`.

#### httpd.conf-Beispiel {#httpd-conf-sample}

```shell
<IfModule alias_module>
     # XAMPP does not have a favicon; this prevents any 404 errors which may arise.
     Redirect 404 /favicon.ico
     <Location /favicon.ico>
         ErrorDocument 404 "No favicon"
     </Location>

    # Return from "Sign Out" generates response header directing you to "/", generating a 404 error
    # The RedirectMatch resolves it correctly when modified for the target Community Site:
    RedirectMatch ^/$ https://[server name]/content/sites/engage/en.html
 ...
 </IfModule>
```

### Dispatcher {#dispatcher}

Informationen zum Verwenden eines Dispatchers finden Sie unter:

* Dokumentation zu AEM [Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html)
* [Installieren des Dispatchers](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-install.html)
* [Konfigurieren von Dispatcher für Communities](dispatcher.md)
* [Bekannte Probleme](troubleshooting.md#dispatcher-refetch-fails)

## Communities-Dokumentation zu ähnlichen Themen {#related-communities-documentation}

* Unter [Communities-Sites verwalten](administer-landing.md) erfahren Sie mehr darüber, wie Sie Community-Sites erstellen, Community-Site-Vorlagen bearbeiten, Community-Inhalte moderieren, Mitglieder verwalten und Messaging-Systeme konfigurieren können.

* Visit [Developing Communities](communities.md) to learn about the social component framework (SCF) and customizing Communities components and features.

* Unter [Authoring Communities-Komponenten](author-communities.md) erfahren Sie, wie Sie Communities-Komponenten erstellen und konfigurieren.

