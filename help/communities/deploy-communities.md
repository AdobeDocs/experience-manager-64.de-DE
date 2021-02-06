---
title: Bereitstellen von Communities
seo-title: Bereitstellen von Communities
description: Bereitstellung von AEM Communities
seo-description: Bereitstellung von AEM Communities
uuid: 1f7faf1a-a339-4eaa-b728-b9110cb350a8
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
content-type: reference
topic-tags: deploying
discoiquuid: d0249609-2a9c-4d3b-92ee-dbc5fbdeaac6
translation-type: tm+mt
source-git-commit: 1375282df15b1a1a1ab5ed760190af8d6288970e
workflow-type: tm+mt
source-wordcount: '2138'
ht-degree: 5%

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

**Für die  [AEM](../../help/sites-deploying/deploy.md#what-is-aem)**

* Installieren Sie die neuesten [AEM 6.4 Updates](#aem-updates)

* Wenn Sie die Standardanschlüsse nicht verwenden (4502, 4503), dann [konfigurieren Sie Replizierungsagenten](#replication-agents-on-author)
* [Verschlüsselungsschlüssel replizieren](#replicate-the-crypto-key)
* Bei Unterstützung der Globalisierung können Sie [die automatisierte Übersetzung ](../../help/sites-administering/translation.md) einrichten.

   (Beispiel-Setup wird für die Entwicklung bereitgestellt)

**Fähigkeit &quot; [Communities&quot;](overview.md)**

* Bei der Bereitstellung einer [Veröffentlichungsfarm](../../help/sites-deploying/recommended-deploys.md#tarmk-farm) [müssen Sie den primären Herausgeber ](#primary-publisher) identifizieren.

* [Aktivieren des Tunneldienstes](#tunnel-service-on-author)
* [Aktivieren der Social-Anmeldung](social-login.md#adobe-granite-oauth-authentication-handler)
* [Konfigurieren Sie Analytics](analytics.md)
* Einrichten eines [Standard-E-Mail-Diensts](email.md)
* Bestimmen Sie die Auswahl für [freigegebene UGC-Datenspeicherung](working-with-srp.md) (**SRP**)

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
         * UGC nur sichtbar auf AEM Instanz oder Cluster, in dem sie eingegeben wurde
      * Standard ist JSRP

   Für die **[Aktivierungsfunktion](overview.md#enablement-community)**

   * [FFmpeg installieren und konfigurieren](ffmpeg.md)
   * [JDBC-Treiber für MySQL installieren](#jdbc-driver-for-mysql)
   * [AEM Communities SCORM-Engine installieren](#scorm-package)
   * [MySQL für die Aktivierung installieren und konfigurieren](mysql.md)






## Neueste Versionen {#latest-releases}

AEM 6.4 Communities GA beinhaltet Communities-Paket. Informationen zu Aktualisierungen von AEM 6.4 [Communities](/help/release-notes/release-notes.md#experience-manager-communities) finden Sie unter [AEM 6.4 Versionshinweise](/help/release-notes/release-notes.md#release-information).

### AEM 6.4 Updates {#aem-updates}

Ab AEM 6.3 werden Updates an Communities als Teil AEM Cumulative Fix Packs und Service Packs bereitgestellt.

Die neuesten Updates für AEM 6.4 finden Sie unter [Adobe Experience Manager 6.4 Cumulative Fix Packs and Service Packs](https://helpx.adobe.com/experience-manager/aem-releases-updates.html).

### Versionsverlauf {#version-history}

Wie bei AEM 6.4 und höher sind AEM Communities-Funktionen und Hotfixes Teil der AEM Communities-Pakete für kumulative Fixpacks und Service Packs. Es gibt daher keine separaten Feature Packs.

### JDBC-Treiber für MySQL {#jdbc-driver-for-mysql}

Zwei Communities-Funktionen verwenden eine MySQL-Datenbank:

* Für [Aktivierung](enablement.md): Aufzeichnung von SCORM-Aktivitäten und -Lernenden
* Für [DSRP](dsrp.md): Speichern benutzergenerierter Inhalte (UGC)

Der MySQL-Connector muss separat bezogen und installiert werden.

Die erforderlichen Schritte sind:

1. ZIP-Archiv von [https://dev.mysql.com/downloads/connector/j/](https://dev.mysql.com/downloads/connector/j/) herunterladen

   * Version muss >= 5.1.38 sein

1. Extrahieren Sie mysql-connector-java-&lt;version>-bin.jar (bundle) aus dem Archiv

1. Verwenden Sie die Web-Konsole, um das Bundle zu installieren und Beginn:

   * Beispiel: http://localhost:4502/system/console/bundles
   * Wählen Sie nun eine der folgenden Optionen aus **`Install/Update`**
   * Durchsuchen... zum Auswählen des aus dem heruntergeladenen ZIP-Archiv extrahierten Bundles
   * Überprüfen Sie, ob der JDBC-Treiber der Oracle Corporation für MySQLcom.mysql.jdbc *aktiv ist, und, falls nicht, Beginn (oder überprüfen Sie die Protokolle)*

1. Wenn Sie nach der Konfiguration von JDBC in einer vorhandenen Bereitstellung installieren, binden Sie JDBC erneut an den neuen Connector, indem Sie die JDBC-Konfiguration aus der Webkonsole erneut binden:

   * Beispiel: http://localhost:4502/system/console/configMgr
   * Suchen Sie nach `Day Commons JDBC Connections Pool`-Konfiguration
   * Zum Öffnen auswählen
   * Wählen Sie nun eine der folgenden Optionen aus `Save`

1. Wiederholen Sie die Schritte 3 und 4 für alle Autoren- und Veröffentlichungsinstanzen.

Weitere Informationen zum Installieren von Bundles finden Sie auf der Seite [Web-Konsole](/help/sites-deploying/web-console.md#bundles).

#### Beispiel: Installiertes MySQL Connector-Bundle {#example-installed-mysql-connector-bundle}

![chlimage_1-410](assets/chlimage_1-410.png)

### SCORM-Paket {#scorm-package}

Das Shareable Content Object Reference Model (SCORM) ist eine Sammlung von Standards und Spezifikationen für eLearning. SCORM definiert auch, wie Inhalte in eine übertragbare ZIP-Datei verpackt werden können.

Die AEM Communities SCORM-Engine ist für die Funktion [enable](overview.md#enablement-community) erforderlich. Die auf AEM Communities 6.4 unterstützten Scorm-Pakete sind:

* **[cq -social- scorm -package, Version 1.2.11](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/scorm/cq-social-scorm-pkg)**. Dieses SCORM-Paket wird von allen AEM 6.4 Communities-Versionen unterstützt.

* **[cq -social- scorm -package, Version 2.2.2 ](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/scorm/cq-social-scorm-2017-pkg)** enthält die  [SCORM 2017.1](https://rusticisoftware.com/blog/scorm-engine-2017-released/) Engine. Dieses SCORM-Paket wird ab AEM 6.4.2.x Communities unterstützt.

Für eine neue Installation der SCORM-Engine sollte das Paket verwendet werden, das [SCORM 2017.1](https://rusticisoftware.com/blog/scorm-engine-2017-released/) enthält (das [ cq -social- scorm -package, Version 2.2.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/scorm/cq-social-scorm-2017-pkg)). Damit Sie Lernressourcen spielen können, die von SCORM 2017 unterstützt werden.

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### So installieren Sie ein SCORM-Paket zum ersten Mal

1. Installieren Sie das **[cq-social-scorm-package, Version 2.2.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/scorm/cq-social-scorm-2017-pkg).**
1. Laden Sie **`/libs/social/config/scorm/database_scormengine_data.sql`** von der cq-Instanz herunter und führen Sie es auf dem mysql-Server aus, um ein aktualisiertes scormEngineDB-Schema zu erstellen.
1. hinzufügen `/content/communities/scorm/RecordResults` in der Eigenschaft &quot;Ausgeschlossene Pfade&quot;im CSRF-Filter von `https://<hostname>;:<port>/system/console/configMgr` bei Herausgebern.

Bestehende SCORM-Installationen können auf [**cq-social-scorm-package, Version 2.2**](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/scorm/cq-social-scorm-2017-pkg) (die [SCORM 2017.1](https://rusticisoftware.com/blog/scorm-engine-2017-released/) verwendet) aktualisiert werden, wenn für den erstellten Kursinhalt SCORM 2017.1 erforderlich ist.

>[!NOTE]
>
>Die Aktualisierung auf das SCORM 2017.1-Paket erfordert die Migration der vorhandenen Datenbank (wie weiter erläutert).

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### So aktualisieren Sie die Version der SCORM-Engine

1. Sichern Sie sich das ScormEngineDB-Schema.
1. Installieren Sie das **[cq-social-scorm-package, Version 2.2.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/scorm/cq-social-scorm-2017-pkg).**
1. Laden Sie das Paket von `/libs/social/config/scorm/ScormEngine.zip` herunter und extrahieren Sie dasselbe.
1. Wechseln Sie zum Ordner **Installer** des extrahierten Ordners.
1. Aktualisieren Sie `SystemDatabaseConnectionString` mit `scorm db connection url` in der Datei **[!UICONTROL EngineInstall.xml]**.
1. Führen Sie das Aktualisierungstool für das mysql-Schema im Installationsordner mit folgendem Befehl aus:

   `java -Dlogback.configurationFile=logback.xml -cp "lib/*" RusticiSoftware.ScormContentPlayer.Logic.Upgrade.ConsoleApp EngineInstall.xml`
1. Überwachen Sie die `engine_upgrade.log`-Datei auf alle Fehler- und Schema-Aktualisierungsstatus.
1. hinzufügen `/content/communities/scorm/RecordResults` in **[!UICONTROL Ausgeschlossene Pfade]**-Eigenschaft im CSRF-Filter von `https://<hostname>:<port>/system/console/configMgr` bei Herausgebern.

### SCORM-Protokollierung {#scorm-logging}

Nach der Installation wird die gesamte Aktivität zur Aktivierung ausführlich an die Systemkonsole protokolliert.

Bei Bedarf kann die Protokollebene für das `RusticiSoftware.*`-Paket auf WARN eingestellt werden.

Informationen zum Arbeiten mit Protokollen finden Sie unter [Arbeiten mit Audit-Aufzeichnungen und Protokolldateien](../../help/sites-deploying/monitoring-and-maintaining.md#working-with-audit-records-and-log-files).

### AEM Advanced MLS {#aem-advanced-mls}

Damit die SRP-Sammlung (MSRP oder DSRP) die erweiterte mehrsprachige Suche (MLS) unterstützen kann, sind zusätzlich zu einer benutzerdefinierten Schema- und Solr-Konfiguration neue Solr-Plug-ins erforderlich. Alle erforderlichen Elemente werden in einer herunterladbaren ZIP-Datei zusammengefasst.

Der erweiterte MLS-Download (auch &quot;phasetwo&quot;genannt) ist im Repository der Adobe verfügbar:

* [AEM-SOLR-MLS-phasetwo](https://repo.adobe.com/nexus/content/repositories/releases/com/adobe/tat/AEM-SOLR-MLS-phasetwo/1.2.40/)

   * Version 1.2.40, 6. April 2016
   * AEM-SOLR-MLS-phasetwo-1.2.40.zip herunterladen

Weitere Informationen und Installationsinformationen finden Sie unter [Solr-Konfiguration](solr.md) für SRP.

### Links zu Package Share {#about-links-to-package-share}

**In Adobe AEM Cloud sichtbare Pakete**

Die Links zu Paketen auf dieser Seite erfordern keine laufende Instanz von AEM, da sie Paketfreigabe auf `adobeaemcloud.com` erfordern. Während die Pakete angezeigt werden können, dient die `Install`Schaltfläche zum Installieren der Pakete auf einer Adobe gehosteten Site. Wenn Sie beabsichtigen, eine Installation auf einer lokalen AEM durchzuführen, führt die Auswahl von `Install`zu einem Fehler.

**Installation auf einer lokalen AEM-Instanz**

Um die in `adobeaemcloud.com` sichtbaren Pakete auf einer lokalen AEM zu installieren, muss das Paket zunächst auf eine lokale Festplatte heruntergeladen werden:

* Wählen Sie die Registerkarte **[!UICONTROL Assets]**
* Wählen Sie **[!UICONTROL Auf Datenträger herunterladen]**

Verwenden Sie auf der lokalen AEM den Paketmanager (z. B. [http://localhost:4502/crx/packmgr/](http://localhost:4502/crx/packmgr/)), um das Paket-Repository in AEM lokalen Repository hochzuladen.

Alternativ dazu wird beim Zugriff auf das Paket mit Package Share von der lokalen AEM Instanz aus (z. B. [http://localhost:4502/crx/packageshare/](http://localhost:4502/crx/packageshare/)) die Schaltfläche `Download`zum Paket-Repository der lokalen AEM Instanz heruntergeladen.

Sobald Sie sich im Paket-Repository der lokalen AEM-Instanz befinden, installieren Sie das Paket mit Package Manager.

Weitere Informationen finden Sie unter [So arbeiten Sie mit Paketen](../../help/sites-administering/package-manager.md#package-share).

## Empfohlene Bereitstellungen {#recommended-deployments}

In AEM Communities wird ein gemeinsamer Speicher zum Speichern benutzergenerierter Inhalte (UGC) verwendet und häufig als [Datenspeicherung Resource Provider (SRP)](working-with-srp.md) bezeichnet. Die empfohlene Bereitstellung konzentriert sich auf die Auswahl einer SRP-Option für den gemeinsamen Speicher.

Der gemeinsame Speicher unterstützt die Moderation und Analyse von UGC in der Veröffentlichungs-Umgebung, wobei gleichzeitig die [Replikation](sync.md) von UGC entfällt.

* [Community Content Store](working-with-srp.md): beschreibt die Optionen für die SRP-Datenspeicherung für AEM Communities

* [Empfohlene Topologien](topologies.md): die je nach Anwendungsfall und SRP-Auswahl zu verwendende Topologie

## Aktualisieren {#upgrading}

Bei der Aktualisierung auf die AEM 6.4-Plattform von früheren Versionen von AEM ist es wichtig, die Aktualisierung auf AEM 6.4 zu lesen.

Lesen Sie zum Aktualisieren der Plattform [Aktualisieren auf AEM Communities 6.4](upgrade.md), um mehr über Änderungen in Communities zu erfahren.

## Konfigurationen {#configurations}

### Primär Publisher {#primary-publisher}

Wenn die gewählte Bereitstellung eine [Veröffentlichungsfarm](topologies.md#tarmk-publish-farm) ist, muss eine AEM Veröffentlichungsinstanz für Aktivitäten, die nicht auf allen Instanzen auftreten sollten, als **`primary publisher`** identifiziert werden, z. B. für Funktionen, die auf **Benachrichtigungen** oder **Adobe Analytics** basieren.

Standardmäßig wird die OSGi-Konfiguration mit dem Kontrollkästchen **`Primary Publisher`** konfiguriert, sodass alle Veröffentlichungsinstanzen in einer Veröffentlichungsfarm sich selbst als Primär identifizieren.`AEM Communities Publisher Configuration`

Daher müssen Sie die Konfiguration für alle sekundären Veröffentlichungsinstanzen **bearbeiten, um das Kontrollkästchen **`Primary Publisher`**zu deaktivieren.**

![chlimage_1-411](assets/chlimage_1-411.png)

Für alle anderen (sekundären) Instanzen im Veröffentlichungsmodus:

* Anmelden mit Administratorberechtigungen
* Zugriff auf die [Webkonsole](../../help/sites-deploying/configuring-osgi.md)

   * Beispiel: [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Suchen Sie nach `AEM Communities Publisher Configuration`
* Wählen Sie das Bearbeitungssymbol
* Deaktivieren Sie das Kontrollkästchen **[!UICONTROL Primär Publisher]**
* Wählen Sie **[!UICONTROL Speichern]** aus

### Replizierungsagenten bei Autor {#replication-agents-on-author}

Die Replikation wird für Site-Inhalte verwendet, die in der Veröffentlichungsgruppe erstellt wurden, wie z. B. Community-Gruppen, sowie für die Verwaltung von Mitgliedern und Mitgliedsgruppen aus der Autorenversion mithilfe des [Tunneldienstes](#tunnel-service-on-author)-Umgebung.

Stellen Sie für den primären Herausgeber sicher, dass [Replication Agent Config](../../help/sites-deploying/replication.md) den Veröffentlichungsserver und den autorisierten Benutzer richtig identifiziert. Der standardmäßig autorisierte Benutzer `admin,` verfügt bereits über die entsprechenden Berechtigungen (ist Mitglied von `Communities Administrators`).

Damit andere Benutzer über die entsprechenden Berechtigungen verfügen, müssen sie als Mitglied der Benutzergruppe `administrators` hinzugefügt werden (auch Mitglied von `Communities Administrators`).

Es gibt zwei Replizierungsagenten in der Authoring-Umgebung, für die die Transportkonfiguration korrekt konfiguriert werden muss.

* Zugriff auf die Replikationskonsole beim Autor

   * Aus globaler Navigation: **[!UICONTROL Tools > Bereitstellung > Replikation > Agenten bei Autor]**

* Für beide Wirkstoffe gilt das gleiche Verfahren:

   * **Standardagent (veröffentlichen)**
   * **Agenten für Rückwärtsreplikation (Rückwärtsveröffentlichen)**

      1. Agent auswählen
      1. Wählen Sie **[!UICONTROL edit]**
      1. Wählen Sie die Registerkarte **[!UICONTROL Transport]**
      1. Wenn kein Anschluss `4503` vorhanden ist, bearbeiten Sie den **[!UICONTROL URI]**, um den richtigen Anschluss anzugeben.
      1. Wenn kein Benutzer `admin`, bearbeiten Sie die **[!UICONTROL Benutzer]** und **[!UICONTROL Kennwort]**, um ein Mitglied der `administrators` Benutzergruppe anzugeben.

Die folgenden Abbildungen zeigen die Ergebnisse einer Änderung des Anschlusses von 4503 auf 6103 durch:

#### Standardagent (publish) {#default-agent-publish}

![chlimage_1-412](assets/chlimage_1-412.png)

#### Replizierungsagenten umkehren (Umkehren veröffentlichen) {#reverse-replication-agent-publish-reverse}

![chlimage_1-413](assets/chlimage_1-413.png)

### Tunnel-Dienst bei Autor {#tunnel-service-on-author}

Wenn Sie die Umgebung zum Erstellen von Sites](sites-console.md), [zum Ändern von Site-Eigenschaften](sites-console.md#modifying-site-properties) oder [Verwalten von Community-Mitgliedern](members.md) verwenden, müssen Sie auf in der Umgebung zum Veröffentlichen registrierte Mitglieder (Benutzer) zugreifen, nicht auf Benutzer, die beim Autor registriert sind.[

Der Tunneldienst bietet diesen Zugriff mithilfe des Replizierungsagenten beim Autor.

So aktivieren Sie den Tunneldienst:

* Unter **author**
* Anmelden mit Administratorrechten
* Wenn der Herausgeber nicht localhost:4503 ist oder der Transportbenutzer nicht `admin` ist,

   Konfigurieren Sie dann [den Replizierungsagenten](#replication-agents-on-author)

* Zugriff auf die [Webkonsole](../../help/sites-deploying/configuring-osgi.md)

   * Beispiel: [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)

* Suchen Sie nach `AEM Communities Publish Tunnel Service`
* Wählen Sie das Bearbeitungssymbol
* Aktivieren Sie das Kontrollkästchen **[!UICONTROL enable]**
* Wählen Sie **[!UICONTROL Speichern]** aus

![chlimage_1-414](assets/chlimage_1-414.png)

### Crypto-Schlüssel {#replicate-the-crypto-key} replizieren

Es gibt zwei Funktionen von AEM Communities, bei denen alle AEM Serverinstanzen dieselben Verschlüsselungsschlüssel verwenden müssen. Dazu gehören [Analytics](analytics.md) und [ASRP](asrp.md).

Ab AEM 6.3 wird das Schlüsselmaterial im Dateisystem und nicht mehr im Repository gespeichert.

Um das Schlüsselmaterial vom Autor in alle anderen Instanzen zu kopieren, müssen Sie:

* Greifen Sie auf die AEM Instanz zu, in der es sich normalerweise um eine Autoreninstanz handelt, die das zu kopierende Schlüsselmaterial enthält

   * Suchen Sie das Bundle `com.adobe.granite.crypto.file` im lokalen Dateisystem

      Beispiel:

      * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21`
      * Die `bundle.info`-Datei identifiziert das Bundle
   * In den Datenordner navigieren

      Beispiel:

      * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`
   * Kopieren Sie die Dateien für den hmac- und den primären Knoten



* Für jede Zielgruppe AEM Instanz

   * In den Datenordner navigieren

      Beispiel:

      * `<publish-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`
   * Einfügen der zuvor kopierten zwei Dateien
   * Es ist erforderlich, das Granite Crypto Bundle](#refresh-the-granite-crypto-bundle) zu aktualisieren, wenn die Zielgruppe AEM Instanz derzeit ausgeführt wird.[


>[!CAUTION]
>
>Wenn bereits eine andere Sicherheitsfunktion konfiguriert wurde, die auf den Verschlüsselungsschlüsseln basiert, könnte die Replizierung der Verschlüsselungsschlüssel die Konfiguration beschädigen. Wenden Sie sich zwecks Hilfe an den Kundendienst.[](https://helpx.adobe.com/de/marketing-cloud/contact-support.html)

#### Repository-Replikation {#repository-replication}

Die Speicherung des Schlüsselmaterials im Repository kann, wie bei AEM 6.2 und früher, beibehalten werden, indem beim ersten Start jeder AEM Instanz (die das anfängliche Repository erstellt) die folgende Systemeigenschaft angegeben wird:

* `-Dcom.adobe.granite.crypto.file.disable=true`

>[!NOTE]
>
>Es ist wichtig zu überprüfen, ob der [Replizierungsagenten unter author](#replication-agents-on-author) richtig konfiguriert ist.

Wenn das Schlüsselmaterial im Repository gespeichert ist, erfolgt die Replizierung des Verschlüsselungsschlüssels vom Autor zu anderen Instanzen wie folgt:

Verwenden von [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Gehen Sie zu [https://&lt;server>:&lt;port>/crx/de](http://localhost:4502/crx/de)
* auswählen `/etc/key`
* Register öffnen `Replication`
* auswählen `Replicate`

* [Granite Crypto-Bundle aktualisieren](#refresh-the-granite-crypto-bundle)

![chlimage_1-415](assets/chlimage_1-415.png)

#### Granite Crypto-Bundle aktualisieren{#refresh-the-granite-crypto-bundle}

* Rufen Sie in jeder Veröffentlichungsinstanz die [Webkonsole](../../help/sites-deploying/configuring-osgi.md) auf

   * Beispiel: [https://&lt;server>:&lt;port>/system/console/bundles](http://localhost:4503/system/console/bundles)

* Suchen Sie nach `Adobe Granite Crypto Support` bundle (com.adobe.granite.crypto)
* Wählen Sie **[!UICONTROL Aktualisieren]**

![chlimage_1-416](assets/chlimage_1-416.png)

* Nach einem Augenblick sollte ein Dialogfeld **Erfolg** angezeigt werden:

   `Operation completed successfully.`

### Apache HTTP Server {#apache-http-server}

Wenn Sie den Apache HTTP-Server verwenden, stellen Sie sicher, dass Sie den richtigen Servernamen für alle relevanten Einträge verwenden.

Achten Sie insbesondere darauf, den korrekten Servernamen, nicht `localhost`, in `RedirectMatch` zu verwenden.

#### httpd.conf sample {#httpd-conf-sample}

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

* AEM [Dokumentation zu Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html)
* [Installieren des Dispatchers](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-install.html)
* [Konfigurieren von Dispatcher für Communities](dispatcher.md)
* [Bekannte Probleme](troubleshooting.md#dispatcher-refetch-fails)

## Communities-Dokumentation zu ähnlichen Themen {#related-communities-documentation}

* Unter [Communities-Sites verwalten](administer-landing.md) erfahren Sie mehr darüber, wie Sie Community-Sites erstellen, Community-Site-Vorlagen bearbeiten, Community-Inhalte moderieren, Mitglieder verwalten und Messaging-Systeme konfigurieren können.

* Besuchen Sie [Developing Communities](communities.md), um mehr über das Social-Komponenten-Framework (SCF) zu erfahren und Communities-Komponenten und -Funktionen anzupassen.

* Unter [Komponenten für Authoring-Communities](author-communities.md) erfahren Sie, wie Sie mit Communities-Komponenten erstellen und konfigurieren.

