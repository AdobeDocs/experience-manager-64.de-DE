---
title: Bereitstellen von Communities
seo-title: Deploying Communities
description: Bereitstellen von AEM Communities
seo-description: How to deploy AEM Communities
uuid: 1f7faf1a-a339-4eaa-b728-b9110cb350a8
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
content-type: reference
topic-tags: deploying
discoiquuid: d0249609-2a9c-4d3b-92ee-dbc5fbdeaac6
exl-id: 0b7496f0-0b3c-4d12-a659-d95744157f14
source-git-commit: a70f874ad7fcae59ee4c6ec20e23ffb2e339590b
workflow-type: tm+mt
source-wordcount: '2180'
ht-degree: 5%

---

# Bereitstellen von Communities {#deploying-communities}

## Voraussetzungen {#prerequisites}

* [AEM 6.4 Platform](../../help/sites-deploying/deploy.md)

* AEM Communities-Lizenz

* Optionale Lizenzen für:

   * [Adobe Analytics für Communities-Funktionen](analytics.md)
   * [MongoDB für MSRP](msrp.md)
   * [Adobe Cloud für ASRP](asrp.md)

## Checkliste für die Installation {#installation-checklist}

**Für [AEM](../../help/sites-deploying/deploy.md#what-is-aem)**

* Installieren Sie die neueste Version [AEM 6.4 Updates](#aem-updates)

* Wenn Sie die Standardanschlüsse nicht verwenden (4502, 4503), wird [Konfigurieren von Replikationsagenten](#replication-agents-on-author)
* [Replizieren des Verschlüsselungsschlüssels](#replicate-the-crypto-key)
* Wenn die Globalisierung unterstützt wird, [Einrichten der automatisierten Übersetzung](../../help/sites-administering/translation.md)

   (Beispiel-Setup wird für die Entwicklung bereitgestellt)

**Für [Communities-Funktionen](overview.md)**

* Bei Bereitstellung eines [Veröffentlichungsfarm](../../help/sites-deploying/recommended-deploys.md#tarmk-farm), [den primären Herausgeber identifizieren](#primary-publisher)

* [Tunneldienst aktivieren](#tunnel-service-on-author)
* [Social-Anmeldung aktivieren](social-login.md#adobe-granite-oauth-authentication-handler)
* [Konfigurieren von Adobe Analytics](analytics.md)
* Einrichten einer [Standard-E-Mail-Dienst](email.md)
* Auswahl für [freigegebener UGC-Speicher](working-with-srp.md) (**SRP**)

   * Wenn MongoDB SRP [(MSRP)](msrp.md)

      * [MongoDB installieren und konfigurieren](msrp.md#mongodb-configuration)
      * [Solr konfigurieren](solr.md)
      * [MSRP auswählen](srp-config.md)
   * Wenn relationale Datenbank SRP [(DSRP)](dsrp.md)

      * [JDBC-Treiber für MySQL installieren](#jdbc-driver-for-mysql)
      * [MySQL für DSRP installieren und konfigurieren](dsrp-mysql.md)
      * [Solr konfigurieren](solr.md)
      * [DSRP auswählen](srp-config.md)
   * Wenn Adobe SRP [(ASRP)](asrp.md)

      * Wenden Sie sich zur Bereitstellung an Ihren Kundenbetreuer
      * [ASRP auswählen](srp-config.md)
   * Wenn JCR SRP [(JSRP)](jsrp.md)

      * Kein freigegebener benutzergenerierter Speicher:

         * UGC wird nie repliziert
         * UGC ist nur in AEM Instanz oder Cluster sichtbar, in dem sie eingegeben wurde
      * Der Standardwert ist JSRP

   Für **[Aktivierungsfunktion](overview.md#enablement-community)**

   * [Installieren und Konfigurieren von FFmpeg](ffmpeg.md)
   * [JDBC-Treiber für MySQL installieren](#jdbc-driver-for-mysql)
   * [AEM Communities SCORM-Engine installieren](#scorm-package)
   * [MySQL zur Aktivierung installieren und konfigurieren](mysql.md)






## Neueste Versionen {#latest-releases}

AEM 6.4 Communities GA umfasst das Communities-Package. Informationen zu Updates auf AEM 6.4 [Communities](/help/release-notes/release-notes.md#experience-manager-communities), siehe [AEM 6.4 - Versionshinweise](/help/release-notes/release-notes.md#release-information).

### AEM 6.4 Updates {#aem-updates}

Ab AEM 6.3 werden Aktualisierungen an Communities als Teil von AEM Cumulative Fix Packs und Service Packs bereitgestellt.

Die neuesten Updates zu AEM 6.4 finden Sie unter [Adobe Experience Manager 6.4 Cumulative Fix Packs und Service Packs](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/aem-releases-updates.html?lang=de).

### Versionsverlauf {#version-history}

Wie AEM 6.4 und höher sind AEM Communities-Funktionen und Hotfixes Teil von AEM Communities Cumulative Fix Packs und Service Packs. Es gibt daher keine separaten Feature Packs.

### JDBC-Treiber für MySQL {#jdbc-driver-for-mysql}

Zwei Communities-Funktionen verwenden eine MySQL-Datenbank:

* Für [Aktivierung](enablement.md): Aufzeichnen von SCORM-Aktivitäten und -Lernenden
* Für [DSRP](dsrp.md): Speichern benutzergenerierter Inhalte (UGC)

Der MySQL-Connector muss separat abgerufen und installiert werden.

Die erforderlichen Schritte sind:

1. Laden Sie das ZIP-Archiv herunter von [https://dev.mysql.com/downloads/connector/j/](https://dev.mysql.com/downloads/connector/j/)

   * Version muss >= 5.1.38 sein.

1. Extrahieren Sie mysql-connector-java-&lt;version>-bin.jar (Bundle) aus dem Archiv

1. Verwenden Sie die Web-Konsole, um das Bundle zu installieren und zu starten:

   * Beispiel: http://localhost:4502/system/console/bundles
   * Wählen Sie nun eine der folgenden Optionen aus **`Install/Update`**
   * Durchsuchen... , um das aus dem heruntergeladenen ZIP-Archiv extrahierte Bundle auszuwählen.
   * Vergewissern Sie sich, dass *JDBC-Treiber der oracle Corporation für MySQLcom.mysql.jdbc* aktiv ist, und starten Sie es, falls nicht (oder überprüfen Sie die Protokolle)

1. Wenn Sie nach der Konfiguration von JDBC in einer vorhandenen Bereitstellung installieren, binden Sie JDBC erneut an den neuen Connector, indem Sie die JDBC-Konfiguration von der Web-Konsole aus erneut speichern:

   * Beispiel: http://localhost:4502/system/console/configMgr
   * Suchen `Day Commons JDBC Connections Pool` Konfiguration
   * Zum Öffnen auswählen
   * Wählen Sie nun eine der folgenden Optionen aus `Save`

1. Wiederholen Sie die Schritte 3 und 4 für alle Autoren- und Veröffentlichungsinstanzen.

Weitere Informationen zur Installation von Bundles finden Sie auf der [Web-Konsole](/help/sites-deploying/web-console.md#bundles) Seite.

#### Beispiel: MySQL Connector Bundle installiert {#example-installed-mysql-connector-bundle}

![chlimage_1-410](assets/chlimage_1-410.png)

### SCORM-Paket {#scorm-package}

Das Shareable Content Object Reference Model (SCORM) ist eine Sammlung von Standards und Spezifikationen für E-Learning. SCORM definiert auch, wie Inhalte in eine übertragbare ZIP-Datei gepackt werden können.

Die AEM Communities SCORM-Engine ist für die [Aktivierung](overview.md#enablement-community) Funktion. Von AEM Communities 6.4 unterstützte Scorm-Pakete sind:

* **[cq -social- scorm -package, Version 1.2.11](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq640%2Fsocial%2Fscorm%2Fcq-social-scorm-pkg)**. Dieses SCORM-Paket wird von allen AEM 6.4 Communities-Versionen unterstützt.

* **[cq -social- scorm -package, Version 2.2.2](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq640%2Fsocial%2Fscorm%2Fcq-social-scorm-2017-pkg)** include [SCORM 2017.1](https://rusticisoftware.com/blog/scorm-engine-2017-released/) Motor. Dieses SCORM-Paket wird ab 6.4.2.x Communities AEM.

Bei einer Neuinstallation des SCORM-Moduls enthält das Paket [SCORM 2017.1](https://rusticisoftware.com/blog/scorm-engine-2017-released/) , [  cq -social- scorm -package, Version 2.2.2](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq640%2Fsocial%2Fscorm%2Fcq-social-scorm-2017-pkg)) verwendet werden. Damit Sie Lernressourcen spielen können, die von SCORM 2017 unterstützt werden.

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### So installieren Sie ein SCORM-Paket zum ersten Mal

1. Installieren Sie die **[cq-social-scorm-package, Version 2.2.2](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq640%2Fsocial%2Fscorm%2Fcq-social-scorm-2017-pkg).**
1. Download **`/libs/social/config/scorm/database_scormengine_data.sql`** aus der cq-Instanz und führen Sie sie auf dem mysql-Server aus, um ein aktualisiertes scormEngineDB-Schema zu erstellen.
1. Hinzufügen `/content/communities/scorm/RecordResults` in der Eigenschaft &quot;Excluded Paths&quot;im CSRF-Filter von `https://<hostname>;:<port>/system/console/configMgr` auf Herausgebern.

Bestehende SCORM-Installationen können auf [**cq-social-scorm-package, Version 2.2.2**](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq640%2Fsocial%2Fscorm%2Fcq-social-scorm-2017-pkg) , die [SCORM 2017.1](https://rusticisoftware.com/blog/scorm-engine-2017-released/)), wenn für den erstellten Kursinhalt SCORM 2017.1 erforderlich ist.

>[!NOTE]
>
>Die Aktualisierung auf das SCORM 2017.1-Paket erfordert die Migration der vorhandenen Datenbank (wie weiter erläutert).

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### Aktualisierung der Version Ihrer SCORM-Engine

1. Erstellen Sie eine Sicherungskopie des ScormEngineDB-Schemas.
1. Installieren Sie die **[cq-social-scorm-package, Version 2.2.2](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq640%2Fsocial%2Fscorm%2Fcq-social-scorm-2017-pkg).**
1. Laden Sie das Paket herunter von `/libs/social/config/scorm/ScormEngine.zip` und extrahieren Sie dasselbe.
1. Navigieren Sie zu **Installationsprogramm** Ordner des extrahierten Ordners.
1. Aktualisieren `SystemDatabaseConnectionString` mit `scorm db connection url` in Datei **[!UICONTROL EngineInstall.xml]**.
1. Führen Sie das mysql-Schema-Upgrade-Tool im Installationsordner mit dem Befehl aus:

   `java -Dlogback.configurationFile=logback.xml -cp "lib/*" RusticiSoftware.ScormContentPlayer.Logic.Upgrade.ConsoleApp EngineInstall.xml`
1. Überwachen `engine_upgrade.log` -Datei für jeden Fehler- und Schema-Upgrade-Status.
1. Hinzufügen `/content/communities/scorm/RecordResults` in **[!UICONTROL Ausgeschlossene Pfade]** Eigenschaft in CSRF-Filter von `https://<hostname>:<port>/system/console/configMgr` auf Herausgebern.

### SCORM-Protokollierung {#scorm-logging}

Wie installiert, werden alle Aktivierungsaktivitäten ausführlich in der Systemkonsole protokolliert.

Bei Bedarf kann die Protokollebene für die `RusticiSoftware.*` Paket.

Informationen zum Arbeiten mit Protokollen finden Sie unter [Arbeiten mit Auditdatensätzen und Protokolldateien](../../help/sites-deploying/monitoring-and-maintaining.md#working-with-audit-records-and-log-files).

### AEM erweiterte MLS {#aem-advanced-mls}

Damit die SRP-Sammlung (MSRP oder DSRP) erweiterte mehrsprachige Suche (MLS) unterstützen kann, sind zusätzlich zu einem benutzerdefinierten Schema und einer Solr-Konfiguration neue Solr-Plug-ins erforderlich. Alle erforderlichen Elemente werden in einer herunterladbaren ZIP-Datei zusammengefasst.

Der erweiterte MLS-Download (auch als &quot;Phasetwo&quot;bezeichnet) ist im Adobe-Repository verfügbar:

* AEM-SOLR-MLS-phasetwo

   Informationen zum Abrufen des erweiterten MLS-Pakets finden Sie unter [AEM erweiterte MLS](deploy-communities.md#aem-advanced-mls) im Abschnitt &quot;Bereitstellung&quot;der Dokumentation.

   * Version 1.2.40, 6. April 2016
   * AEM-SOLR-MLS-phasetwo-1.2.40.zip herunterladen

Weitere Informationen und Installationsinformationen finden Sie unter [Solr-Konfiguration](solr.md) für SRP.

### Über Links zur Paketfreigabe {#about-links-to-package-share}

**In Adobe AEM Cloud sichtbare Pakete**

Die Links zu Paketen auf dieser Seite erfordern keine laufende Instanz von AEM, da sie für die Paketfreigabe auf `adobeaemcloud.com`. Während die Pakete sichtbar sind, wird die `Install`-Schaltfläche ist für die Installation der Pakete auf einer Adobe gehosteten Site. Wenn Sie eine Installation auf einer lokalen AEM durchführen möchten, wählen Sie `Install`führt zu einem Fehler.

**Installieren auf einer lokalen AEM-Instanz**

So installieren Sie die Pakete, die in `adobeaemcloud.com` auf einer lokalen AEM-Instanz muss das Paket zuerst auf eine lokale Festplatte heruntergeladen werden:

* Wählen Sie die **[!UICONTROL Assets]** tab
* Auswählen **[!UICONTROL Herunterladen auf Festplatte]**

Verwenden Sie auf der lokalen AEM-Instanz den Package Manager (z. B. [http://localhost:4502/crx/packmgr/](http://localhost:4502/crx/packmgr/)), um in das lokale AEM-Package-Repository hochzuladen.

Alternativ können Sie über Package Share über die lokale AEM-Instanz auf das Paket zugreifen (z. B. [http://localhost:4502/crx/packageshare/](http://localhost:4502/crx/packageshare/)), die `Download`-Schaltfläche in das Package-Repository der lokalen AEM-Instanz heruntergeladen.

Sobald Sie sich im Package-Repository der lokalen AEM-Instanz befinden, installieren Sie das Package mit Package Manager.

Weitere Informationen finden Sie unter [Arbeiten mit Paketen](../../help/sites-administering/package-manager.md#package-share).

## Empfohlene Bereitstellungen {#recommended-deployments}

In AEM Communities wird ein gemeinsamer Speicher zum Speichern benutzergenerierter Inhalte verwendet, die häufig als [Storage Resource Provider (SRP)](working-with-srp.md). Die empfohlene Implementierung konzentriert sich auf die Auswahl einer SRP-Option für den gemeinsamen Speicher.

Der gemeinsame Speicher unterstützt die Moderation von und die Analyse von benutzergenerierten Inhalten in der Veröffentlichungsumgebung, während die Notwendigkeit für [Replikation](sync.md) von UGC.

* [Community-Inhaltsspeicher](working-with-srp.md): beschreibt die SRP-Speicheroptionen für AEM Communities

* [Empfohlene Topologien](topologies.md): beschreibt die je nach Anwendungsfall und SRP-Auswahl zu verwendende Topologie

## Aktualisieren {#upgrading}

Wenn Sie von früheren Versionen von AEM auf die AEM 6.4-Plattform aktualisieren, ist es wichtig, die Informationen unter Upgrade auf AEM 6.4 zu lesen.

Lesen Sie neben der Aktualisierung der Plattform auch [Upgrade auf AEM Communities 6.4](upgrade.md) , um mehr über Communities-Änderungen zu erfahren.

## Konfigurationen {#configurations}

### Primärer Herausgeber {#primary-publisher}

Wenn es sich bei der ausgewählten Bereitstellung um eine [Veröffentlichungsfarm](topologies.md#tarmk-publish-farm), muss eine AEM Veröffentlichungsinstanz als **`primary publisher`** für Aktivitäten, die nicht in allen Instanzen auftreten sollten, z. B. Funktionen, auf die **Benachrichtigungen** oder **Adobe Analytics**.

Standardmäßig wird die `AEM Communities Publisher Configuration` Die OSGi-Konfiguration wird mit der **`Primary Publisher`** -Kontrollkästchen aktiviert, sodass sich alle Veröffentlichungsinstanzen in einer Veröffentlichungsfarm selbst als primär identifizieren.

Daher ist es notwendig, **Bearbeiten Sie die Konfiguration auf allen sekundären Veröffentlichungsinstanzen.** , um die **`Primary Publisher`** aktivieren.

![chlimage_1-411](assets/chlimage_1-411.png)

Für alle anderen (sekundären) Veröffentlichungsinstanzen in einer Veröffentlichungsfarm:

* Anmelden mit Administratorrechten
* Zugriff auf [Webkonsole](../../help/sites-deploying/configuring-osgi.md)

   * Beispiel: [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Suchen Sie die `AEM Communities Publisher Configuration`
* Bearbeiten-Symbol auswählen
* Deaktivieren Sie die **[!UICONTROL Primärer Herausgeber]** box
* Wählen Sie **[!UICONTROL Speichern]** aus

### Replikationsagenten auf der Autoreninstanz {#replication-agents-on-author}

Die Replikation wird für Site-Inhalte verwendet, die in der Veröffentlichungsumgebung erstellt werden, z. B. Community-Gruppen, sowie für die Verwaltung von Mitgliedern und Mitgliedergruppen aus der Autorenumgebung mithilfe der [Tunneldienst](#tunnel-service-on-author).

Stellen Sie für den primären Herausgeber sicher, dass die [Konfiguration des Replikationsagenten](../../help/sites-deploying/replication.md) den Veröffentlichungsserver und den autorisierten Benutzer korrekt identifiziert. Der standardmäßig autorisierte Benutzer `admin,` verfügt bereits über die entsprechenden Berechtigungen (ist Mitglied von `Communities Administrators`).

Damit andere Benutzer über die entsprechenden Berechtigungen verfügen können, müssen sie als Mitglied der `administrators` Benutzergruppe (ebenfalls Mitglied von `Communities Administrators`).

Es gibt zwei Replikationsagenten in der Autorenumgebung, für die die Transportkonfiguration korrekt konfiguriert werden muss.

* Zugriff auf die Replikationskonsole auf der Autoreninstanz

   * Über die globale Navigation: **[!UICONTROL Tools > Bereitstellung > Replikation > Agenten für Autor]**

* Gehen Sie für beide Agenten genauso vor:

   * **Standardagent (publish)**
   * **Agenten für Rückwärtsreplikation (Rückwärts veröffentlichen)**

      1. Wählen Sie den Agenten aus
      1. Auswählen **[!UICONTROL edit]**
      1. Wählen Sie die **[!UICONTROL Verkehr]** tab
      1. Wenn nicht Port `4503`, bearbeiten Sie die **[!UICONTROL URI]** zum Angeben des richtigen Ports
      1. Wenn kein Benutzer `admin`, bearbeiten Sie die **[!UICONTROL Benutzer]** und **[!UICONTROL Passwort]** , um ein Mitglied der `administrators` Benutzergruppe

Die folgenden Abbildungen zeigen die Ergebnisse einer Änderung des Ports von 4503 auf 6103 durch:

#### Standardagent (publish) {#default-agent-publish}

![chlimage_1-412](assets/chlimage_1-412.png)

#### Agenten für Rückwärtsreplikation (Rückwärts veröffentlichen) {#reverse-replication-agent-publish-reverse}

![chlimage_1-413](assets/chlimage_1-413.png)

### Tunnel-Dienst auf Autoreninstanz {#tunnel-service-on-author}

Bei Verwendung der Autorenumgebung zu [Erstellen von Sites](sites-console.md), [Ändern von Site-Eigenschaften](sites-console.md#modifying-site-properties) oder [Verwalten von Community-Mitgliedern](members.md), ist es erforderlich, auf Mitglieder (Benutzer) zuzugreifen, die in der Veröffentlichungsumgebung registriert sind, nicht auf Benutzer, die in der Autoreninstanz registriert sind.

Der Tunneldienst stellt diesen Zugriff mithilfe des Replikationsagenten auf der Autoreninstanz bereit.

So aktivieren Sie den Tunneldienst:

* on **author**
* Anmelden mit Administratorrechten
* Wenn der Herausgeber nicht localhost:4503 ist oder der Transportbenutzer nicht `admin`,

   Dann [Konfigurieren des Replikationsagenten](#replication-agents-on-author)

* Zugriff auf [Web-Konsole](../../help/sites-deploying/configuring-osgi.md)

   * Beispiel: [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)

* Suchen Sie die `AEM Communities Publish Tunnel Service`
* Bearbeiten-Symbol auswählen
* Überprüfen Sie die **[!UICONTROL enable]** box
* Wählen Sie **[!UICONTROL Speichern]** aus

![chlimage_1-414](assets/chlimage_1-414.png)

### Replizieren des Crypto-Schlüssels {#replicate-the-crypto-key}

Es gibt zwei Funktionen von AEM Communities, für die alle AEM Serverinstanzen dieselben Verschlüsselungsschlüssel verwenden müssen. Diese [Analytics](analytics.md) und [ASRP](asrp.md).

Ab AEM 6.3 wird das Schlüsselmaterial im Dateisystem und nicht mehr im Repository gespeichert.

Um das Schlüsselmaterial vom Autor in alle anderen Instanzen zu kopieren, müssen Sie Folgendes tun:

* Greifen Sie auf die AEM-Instanz zu, normalerweise eine Autoreninstanz, die das zu kopierende Schlüsselmaterial enthält

   * Suchen Sie die `com.adobe.granite.crypto.file` Bundle im lokalen Dateisystem

      Beispiel:

      * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21`
      * Die `bundle.info` -Datei identifiziert das Bundle
   * Navigieren zum Datenordner

      Beispiel:

      * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`
   * Kopieren Sie die Dateien hmac und primary .



* Für jede AEM-Instanz

   * Navigieren zum Datenordner

      Beispiel:

      * `<publish-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`
   * Fügen Sie die beiden zuvor kopierten Dateien ein.
   * Es ist erforderlich, [Aktualisieren des Granite Crypto-Bundles](#refresh-the-granite-crypto-bundle) , wenn die Ziel-AEM-Instanz derzeit ausgeführt wird


>[!CAUTION]
>
>Wenn bereits eine andere Sicherheitsfunktion konfiguriert wurde, die auf den Verschlüsselungsschlüsseln basiert, kann die Replikation der Verschlüsselungsschlüssel die Konfiguration beschädigen. Hilfe: [Kundenunterstützung kontaktieren](https://helpx.adobe.com/de/marketing-cloud/contact-support.html).

#### Repository-Replikation {#repository-replication}

Das Schlüsselmaterial, das wie bei AEM 6.2 und früher im Repository gespeichert ist, kann beibehalten werden, indem beim ersten Start jeder AEM Instanz (durch die das anfängliche Repository erstellt wird) die folgende Systemeigenschaft angegeben wird:

* `-Dcom.adobe.granite.crypto.file.disable=true`

>[!NOTE]
>
>Es ist wichtig zu überprüfen, dass die Variable [Replikationsagent auf Autoreninstanz](#replication-agents-on-author) korrekt konfiguriert ist.

Mit dem im Repository gespeicherten Schlüsselmaterial wird der Crypto-Schlüssel vom Autor auf andere Instanzen wie folgt repliziert:

Verwenden [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Durchsuchen nach [https://&lt;server>:&lt;port>/crx/de](http://localhost:4502/crx/de)
* auswählen `/etc/key`
* open `Replication` tab
* auswählen `Replicate`

* [Aktualisieren des Granite Crypto-Bundles](#refresh-the-granite-crypto-bundle)

![chlimage_1-415](assets/chlimage_1-415.png)

#### Aktualisieren des Granite Crypto-Bundles {#refresh-the-granite-crypto-bundle}

* Rufen Sie in jeder Veröffentlichungsinstanz die [Web-Konsole](../../help/sites-deploying/configuring-osgi.md)

   * Beispiel: [https://&lt;server>:&lt;port>/system/console/bundles](http://localhost:4503/system/console/bundles)

* Suchen `Adobe Granite Crypto Support` Bundle (com.adobe.granite.crypto)
* Auswählen **[!UICONTROL Aktualisieren]**

![chlimage_1-416](assets/chlimage_1-416.png)

* Nach einem Moment **Erfolg** sollte angezeigt werden:

   `Operation completed successfully.`

### Apache HTTP Server {#apache-http-server}

Stellen Sie bei Verwendung des Apache HTTP-Servers sicher, dass Sie den richtigen Servernamen für alle relevanten Einträge verwenden.

Achten Sie insbesondere darauf, den richtigen Servernamen zu verwenden, nicht `localhost`in der `RedirectMatch`.

#### Beispiel für httpd.conf {#httpd-conf-sample}

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

Informationen zur Verwendung eines Dispatchers finden Sie unter:

* AEM [Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html) Dokumentation
* [Installieren des Dispatchers](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-install.html)
* [Konfigurieren des Dispatchers für Communities](dispatcher.md)
* [Bekannte Probleme](troubleshooting.md#dispatcher-refetch-fails)

## Communities-Dokumentation zu ähnlichen Themen {#related-communities-documentation}

* Unter [Communities-Sites verwalten](administer-landing.md) erfahren Sie mehr darüber, wie Sie Community-Sites erstellen, Community-Site-Vorlagen bearbeiten, Community-Inhalte moderieren, Mitglieder verwalten und Messaging-Systeme konfigurieren können.

* Besuch [Entwickeln von Communities](communities.md) , um mehr über das Social-Komponenten-Framework (SCF) zu erfahren und Communities-Komponenten und -Funktionen anzupassen.

* Besuch [Erstellen von Communities-Komponenten](author-communities.md) , um zu erfahren, wie Sie Communities-Komponenten erstellen und konfigurieren.
