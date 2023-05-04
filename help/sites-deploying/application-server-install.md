---
title: Installation des Anwendungs-Servers
seo-title: Application Server Install
description: Erfahren Sie, wie Sie AEM mit einem Anwendungsserver installieren.
seo-description: Learn how to install AEM with an application server.
uuid: c9571f80-6ed1-46fe-b7c3-946658dfc3f4
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: deploying
discoiquuid: 6fdce35d-2709-41cc-87fb-27a4b867e960
exl-id: 65346618-e5a6-43d0-a2b3-698268d3cf64
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1199'
ht-degree: 66%

---

# Installation des Anwendungs-Servers{#application-server-install}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

>[!NOTE]
>
>`JAR` und `WAR` sind die Dateitypen, in denen AEM veröffentlicht wird. Diese Formate unterliegen einer Qualitätssicherung, mit der die von Adobe zugesicherten Supportstufen sichergestellt werden.

In diesem Abschnitt erfahren Sie, wie Sie Adobe Experience Manager (AEM) mit einem Anwendungsserver installieren. Lesen Sie den Abschnitt [Unterstützte Plattformen](/help/sites-deploying/technical-requirements.md#servlet-engines-application-servers), um die spezifischen Unterstützungsebenen anzuzeigen, die für die einzelnen Anwendungsserver bereitgestellt werden.

Es werden die Installationsschritte der folgenden Anwendungsserver beschrieben:

* [WebSphere 8.5](#websphere)
* [JBoss EAP 6.3.0/6.4.0](#jboss-eap)
* [Oracle WebLogic 12.1.3/12.2](#oracle-weblogic)
* [Tomcat 8/8.5](#tomcat)

Lesen Sie die entsprechende Anwendungsserverdokumentation, um weitere Informationen über das Installieren von Webanwendungen, Serverkonfigurationen und darüber zu erhalten, wie der Server gestartet und angehalten wird.

>[!NOTE]
>
>Wenn Sie Dynamic Media in einer WAR-Bereitstellung verwenden, lesen Sie den Abschnitt [Dokumentation zu dynamischen Medien](/help/assets/config-dynamic.md#enabling-dynamic-media).

## Allgemeine Beschreibung {#general-description}

### Standardverhalten beim Installieren von AEM auf einem Anwendungsserver {#default-behaviour-when-installing-aem-in-an-application-server}

AEM wird als einzelne WAR-Datei bereitgestellt.

Bei Bereitstellung geschieht standardmäßig Folgendes:

* Der Ausführungsmodus lautet `author`.
* Die Instanz (Repository, Felix OSGi-Umgebung, Bundles usw.) wird in `${user.dir}/crx-quickstart` installiert, wobei `${user.dir}` das aktuelle Arbeitsverzeichnis ist. Dieser Pfad zu crx-quickstart wird als `sling.home` bezeichnet.

* Der Kontextstamm ist der Name der WAR-Datei, z. B.: `aem-6`.

#### Konfiguration {#configuration}

Sie können das Standardverhalten wie folgt ändern:

* Ausführungsmodus: Konfigurieren Sie den Parameter `sling.run.modes` in der Datei `WEB-INF/web.xml` der AEM-WAR-Datei vor der Bereitstellung.

* sling.home: Konfigurieren Sie den Parameter `sling.home` in der Datei `WEB-INF/web.xml` der AEM-WAR-Datei vor der Bereitstellung.

* Kontextstamm: Benennen Sie die AEM-WAR-Datei um.

#### Installationsveröffentlichung {#publish-installation}

Um eine Veröffentlichungsinstanz bereitzustellen, müssen Sie den Ausführungsmodus auf „publish“ (veröffentlichen) festlegen:

* Entpacken Sie WEB-INF/web.xml aus der WAR-Datei AEM
* Ändern Sie den Parameter „sling.run.modes“ in „publish“ (veröffentlichen).
* Datei &quot;web.xml&quot;in AEM WAR-Datei replizieren
* Stellen Sie die AEM-WAR-Datei bereit.

#### Installationsprüfung {#installation-check}

Um zu überprüfen, ob alle installiert sind, können Sie Folgendes tun:

* Untersuchen der Datei `error.log`, um anzuzeigen, ob der gesamte Inhalt installiert ist.
* Überprüfen in `/system/console`, ob alle Bundles installiert sind

#### Zwei Instanzen auf demselben Anwendungsserver {#two-instances-on-the-same-application-server}

Zu Demonstrationszwecken kann es sinnvoll sein, die Autoren- und Veröffentlichungsinstanz auf einem Anwendungsserver zu installieren. Gehen Sie dazu wie folgt vor:

1. Ändern Sie die Variablen „sling.home“ und „sling.run.modes“ der Veröffentlichungsinstanz.
1. Entpacken Sie die Datei „WEB-INF/web.xml“ aus der AEM-WAR-Datei.
1. Ändern Sie den Parameter „sling.home“ in einen anderen Pfad (absolute und relative Pfade sind möglich).
1. Ändern Sie „sling.run.modes“ für die Veröffentlichungsinstanz in „publish“ (veröffentlichen).
1. Packen Sie die Datei „web.xml“ erneut.
1. Benennen Sie die WAR-Dateien um, sodass sie unterschiedliche Namen aufweisen. So können Sie eine beispielsweise in „aemauthor.war“ und die andere in „aempublish.war“ umbenennen.
1. Verwenden Sie höhere Speichereinstellungen, etwa -Xmx3072m für standardmäßige AEM-Instanzen.
1. Stellen Sie die beiden Webanwendungen bereit.
1. Halten Sie nach der Bereitstellung die beiden Webanwendungen an.
1. Stellen Sie in den Erstellungs- und Veröffentlichungsinstanzen sicher, dass in den „sling.properties“-Dateien die Eigenschaft „felix.service.urlhandlers=false“ auf „false“ festgelegt ist (standardmäßig ist der Wert auf „true“ gesetzt).
1. Starten Sie die beiden Webanwendungen erneut.

## Installationsverfahren für Anwendungsserver {#application-servers-installation-procedures}

### WebSphere 8.5 {#websphere}

Lesen Sie oben [Allgemeine Beschreibung](#general-description), bevor Sie eine Bereitstellung vornehmen.

**Servervorbereitung**

* Lassen Sie einfache Auth-Header durchgehen:

   * Eine Möglichkeit, AEM Benutzer authentifizieren zu können, besteht darin, die globale Verwaltungssicherheit des WebSphere-Servers zu deaktivieren: Wechseln Sie zu Sicherheit > Globale Sicherheit und deaktivieren Sie das Kontrollkästchen Enable administrative security , speichern und starten Sie den Server neu.

* set `"JAVA_OPTS= -Xmx2048m"`
* Wenn Sie AEM mithilfe des Kontextstamms =/ installieren möchten, müssen Sie zunächst den Kontextstamm der vorhandenen standardmäßigen Webanwendung ändern.

**Bereitstellung der AEM-Webanwendung**

* Laden Sie die AEM-WAR-Datei herunter.
* Nehmen Sie bei Bedarf Konfigurationen in web.xml vor (siehe oben in der allgemeinen Beschreibung).

   * Entpacken Sie die Datei „WEB-INF/web.xml“.
   * Ändern Sie den Parameter „sling.run.modes“ in „publish“ (veröffentlichen).
   * Entfernen Sie die Kommentarzeichen für den ursprünglichen Parameter „sling.home“ und legen Sie diesen Pfad nach Bedarf fest.
   * Packen Sie die Datei „web.xml“ erneut.

* Bereitstellen der AEM-WAR-Datei

   * Wählen Sie einen Kontextstamm aus. (Wenn Sie die Sling-Ausführungsmodi festlegen möchten, müssen Sie die detaillierten Schritte des Bereitstellungsassistenten auswählen und dann in Schritt 6 des Assistenten angeben.)

* AEM Webanwendung starten

#### JBoss EAP 6.3.0/6.4.0 {#jboss-eap}

Lesen Sie oben [Allgemeine Beschreibung](#general-description), bevor Sie eine Bereitstellung vornehmen.

**JBoss-Servervorbereitung**

Legen Sie die „Memory“-Argumente in Ihrer Konfigurationsdatei (z. B. `standalone.conf`) fest.

* JAVA_OPTS=&quot;-Xms64m -Xmx2048m&quot;

Wenn Sie die Bereitstellungsüberprüfung für die Installation der AEM-Webanwendung verwenden, empfiehlt es sich möglicherweise, den Wert für `deployment-timeout,` zu erhöhen. Legen Sie dafür das Attribut `deployment-timeout` in der XML-Datei Ihrer Instanz (z. B. `configuration/standalone.xml)`) fest:

```xml
<subsystem xmlns="urn:jboss:domain:deployment-scanner:1.1">
            <deployment-scanner path="deployments" relative-to="jboss.server.base.dir" scan-interval="5000" deployment-timeout="1000"/>
</subsystem>
```

**Bereitstellung der AEM-Webanwendung**

* Laden Sie die AEM-Webanwendung in Ihre JBoss-Verwaltungskonsole hoch.

* Aktivieren Sie die AEM-Webanwendung.

#### Oracle WebLogic 12.1.3/12.2 {#oracle-weblogic}

Lesen Sie oben [Allgemeine Beschreibung](#general-description), bevor Sie eine Bereitstellung vornehmen.

Hierbei wird ein einfaches Server-Layout mit nur einem Admin-Server verwendet.

**WebLogic Server-Vorbereitung**

* Fügen Sie in `${myDomain}/config/config.xml` Folgendes zum Abschnitt „security-configuration“ hinzu:

   * `<enforce-valid-basic-auth-credentials>false</enforce-valid-basic-auth-credentials>` – auf [https://xmlns.oracle.com/weblogic/domain/1.0/domain.xsd](https://xmlns.oracle.com/weblogic/domain/1.0/domain.xsd) finden Sie die richtige Position (standardmäßig ist es in Ordnung, die Positionierung am Ende des Abschnitts vorzunehmen).

* Erhöhen Sie den für die virtuelle Maschine eingestellten Arbeitsspeicherwert:

   * Öffnen Sie `${myDomain}/bin/setDomainEnv.cmd` (bzw. .sh). Suchen Sie nach WLS_MEM_ARGS, legen Sie z. B. `WLS_MEM_ARGS_64BIT=-Xms256m -Xmx2048m` fest.
   * Starten Sie WebLogic Server neu.

* Erstellen Sie unter `${myDomain}` einen Ordner „packages“ und darin einen Ordner „cq“ mit einem Ordner „Plan“.

**Bereitstellung der AEM-Webanwendung**

* Laden Sie die AEM-WAR-Datei herunter.
* Legen Sie die AEM-WAR-Datei im Ordner „${myDomain}/packages/cq“ ab.
* Nehmen Sie bei Bedarf Konfigurationen in `WEB-INF/web.xml` vor (siehe oben unter „Allgemeine Beschreibung“).

   * Entpacken Sie die Datei `WEB-INF/web.xml`.
   * Ändern Sie den Parameter „sling.run.modes“ in „publish“ (veröffentlichen).
   * Entfernen Sie die Kommentarzeichen für den anfänglichen Parameter „sling.home“ und legen Sie diesen Pfad nach Bedarf fest (siehe „Allgemeine Beschreibung“).
   * Packen Sie die Datei „web.xml“ erneut.

* Bereitstellen der AEM-WAR-Datei als Anwendung (für die anderen Einstellungen verwenden Sie die Standardeinstellungen)
* Die Installation kann einige Zeit dauern...
* Vergewissern Sie sich, dass die Installation wie oben in der allgemeinen Beschreibung beschrieben abgeschlossen ist (z. B. Aufrufen des error.log).
* Sie können den Kontextstamm auf der Konfigurationsregisterkarte der Webanwendung in der WebLogic-`/console` ändern.

#### Tomcat 8/8.5 {#tomcat}

Lesen Sie oben [Allgemeine Beschreibung](#general-description), bevor Sie eine Bereitstellung vornehmen.

* **Tomcat-Servervorbereitung**

   * Erhöhen Sie den für die virtuelle Maschine eingestellten Arbeitsspeicherwert:

      * Fügen Sie in `bin/catalina.bat` (bzw. `catalina.sh` unter Unix) die folgende Einstellung hinzu:
      * `set "JAVA_OPTS= -Xmx2048m`
   * Tomcat ermöglicht weder der bzw. dem Admin noch der Managerin bzw. dem Manager bei der Installation den Zugriff. Daher müssen Sie `tomcat-users.xml` manuell bearbeiten, um den Zugriff für diese Konten zuzulassen:

      * Bearbeiten Sie `tomcat-users.xml`, um den Zugriff für Admin und Managerin bzw. Manager einzuschließen. Die Konfiguration sollte dem folgenden Beispiel ähneln:

      ```xml
        <?xml version='1.0' encoding='utf-8'?>
         <tomcat-users>
         <role rolename="manager"/>
         <role rolename="tomcat"/>
         <role rolename="admin"/>
         <role rolename="role1"/>
         <role rolename="manager-gui"/>
         <user username="both" password="tomcat" roles="tomcat,role1"/>
         <user username="tomcat" password="tomcat" roles="tomcat"/>
         <user username="admin" password="admin" roles="admin,manager-gui"/>
         <user username="role1" password="tomcat" roles="role1"/>
         </tomcat-users>
      ```

   * Wenn Sie AEM mit dem Kontextstamm &quot;/&quot;bereitstellen möchten, müssen Sie den Kontextstamm der vorhandenen ROOT-Webanwendung ändern:

      * Stoppen und Aufheben der Bereitstellung der ROOT-Webapp
      * Umbenennen des Ordners &quot;ROOT.war&quot;im Ordner &quot;webapps&quot;von Tomcat
      * Webapp erneut starten
   * Wenn Sie die AEM-Web-Anwendung mithilfe der manager-gui installieren, müssen Sie die maximale Größe einer hochgeladenen Datei erhöhen, da die Standardeinstellung nur eine Upload-Größe von 50 MB zulässt. Öffnen Sie dafür die Datei „web.xml“ der Manager-Webanwendung

      `webapps/manager/WEB-INF/web.xml`

      und erhöhen Sie „max-file-size“ und „max-request-size“ auf mindestens „500 MB“. Im folgenden `multipart-config`-Beispiel finden Sie eine derartige `web.xml`-Datei:

      ```
      <multipart-config>
       <!-- 500MB max -->
       <max-file-size>524288000</max-file-size>
       <max-request-size>524288000</max-request-size>
       <file-size-threshold>0</file-size-threshold>
       </multipart-config>
      ```




* **Bereitstellung der AEM-Webanwendung**

   * Laden Sie die AEM-WAR-Datei herunter.
   * Nehmen Sie bei Bedarf Konfigurationen in web.xml vor (siehe oben in der allgemeinen Beschreibung).

      * Entpacken Sie die Datei „WEB-INF/web.xml“.
      * Ändern Sie den Parameter „sling.run.modes“ in „publish“ (veröffentlichen).
      * Entfernen Sie die Kommentarzeichen für den ursprünglichen Parameter „sling.home“ und legen Sie diesen Pfad nach Bedarf fest.
      * Packen Sie die Datei „web.xml“ erneut.
   * Benennen Sie AEM WAR-Datei in ROOT.war um, wenn Sie sie als Root-Webapp bereitstellen möchten, benennen Sie sie z. B. in aemauthor.war um, wenn Sie aemauthor als Kontextstamm verwenden möchten.
   * Kopieren Sie es in den Ordner webapps von Tomcat.
   * warten, bis AEM installiert ist


## Fehlerbehebung {#troubleshooting}

Informationen zum Umgang mit Problemen, die während der Installation auftreten können, finden Sie unter:

* [Fehlerbehebung](/help/sites-deploying/troubleshooting.md)
