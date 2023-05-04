---
title: Leistungsoptimierung für AEM Forms-Server
seo-title: Performance tuning of AEM Forms server
description: Damit AEM Forms optimal funktioniert, können Sie die Cacheeinstellungen und JVM-Parameter anpassen. Außerdem kann die Verwendung eines Webservers die Leistung der AEM Forms-Bereitstellung verbessern.
seo-description: For AEM Forms to perform optimally, you can fine-tune the cache settings and JVM parameters. Also, using a web server can enhance the performance of AEM Forms deployment.
uuid: 77eaeecc-ca52-4d3d-92e6-1ab4d91b9edd
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: 5d672b56-00c4-46a0-974b-e174fbdf07d6
role: Admin
exl-id: bc750571-08a5-414c-aed5-4e839f6695ae
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '902'
ht-degree: 29%

---

# Leistungsoptimierung für AEM Forms-Server {#performance-tuning-of-aem-forms-server}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

In diesem Artikel werden Strategien und Best Practices besprochen, die Sie implementieren können, um Engpässe zu reduzieren und die Leistung Ihrer AEM Forms-Implementierung zu optimieren.

## Cacheeinstellungen {#cache-settings}

Sie können die Cachestrategie für AEM Forms mithilfe der **Mobile Forms-Konfigurationen** Komponente in AEM Web Configuration Console unter:

* (AEM Forms on OSGi) `https://[server]:[port]/system/console/configMgr`
* (AEM Forms unter JEE) `https://[server]:[port]/lc/system/console/configMgr`

Die verfügbaren Optionen für die Zwischenspeicherung lauten wie folgt:

* **Keines**: Erzwingt, dass kein Artefakt zwischengespeichert wird. Dies verlangsamt in der Praxis die Leistung und erfordert aufgrund des Fehlens von Cache eine hohe Speicherverfügbarkeit.
* **Konservativ**: Dient dazu, nur jene Zwischenartefakte zwischenzuspeichern, die vor dem Rendern des Formulars generiert werden, z. B. eine Vorlage mit Inline-Fragmenten und Bildern.
* **Aggressiv**: Erzwingt das Zwischenspeichern von fast allem, was zwischengespeichert werden kann, einschließlich des gerenderten HTML-Inhalts neben allen Artefakten aus der Cachestufe &quot;Konservativ&quot;. Dies führt zur besten Leistung, verbraucht aber auch mehr Speicher zum Speichern zwischengespeicherter Artefakte. Aggressive Cachestrategie bedeutet, dass Sie beim Rendern eines Formulars eine konstante Zeitleistung erhalten, da der gerenderte Inhalt zwischengespeichert wird.

Die standardmäßigen Cacheeinstellungen für AEM Forms erweisen sich für eine optimale Leistung möglicherweise als unzureichend. Daher wird die Verwendung der folgenden Einstellungen empfohlen:

* **Cachestrategie**: Aggressiv
* **Cachegröße** (in Bezug auf Anzahl von Formularen): Bei Bedarf
* **Max Objektgröße**: Bei Bedarf

![Mobile Forms-Konfigurationen](assets/snap.png)

>[!NOTE]
>
>Wenn Sie AEM Dispatcher verwenden, um adaptive Formulare zwischenzuspeichern, werden auch adaptive Formulare zwischengespeichert, die Formulare mit vorausgefüllten Daten enthalten. Wenn solche Formulare aus AEM Dispatcher-Cache bereitgestellt werden, kann dies dazu führen, dass vorausgefüllte oder veraltete Daten für die Benutzer bereitgestellt werden. Verwenden Sie AEM Dispatcher also, um adaptive Formulare zwischenzuspeichern, die keine vorausgefüllten Daten verwenden. Außerdem werden zwischengespeicherte Fragmente nicht durch einen Dispatcher-Cache automatisch invalidiert. Verwenden Sie sie also nicht zum Zwischenspeichern von Formularfragmenten. Verwenden Sie für solche Formulare und Fragmente [Cache für adaptive Formulare](/help/forms/using/configure-adaptive-forms-cache.md).

## JVM-Parameter  {#jvm-parameters}

Zur optimal Leistung wird die Verwendung der folgenden JVM-`init`-Argumenten empfohlen, um `Java heap` und `PermGen` zu konfigurieren.

```java
set CQ_JVM_OPTS=%CQ_JVM_OPTS% -Xms8192m
set CQ_JVM_OPTS=%CQ_JVM_OPTS% -Xmx8192m
set CQ_JVM_OPTS=%CQ_JVM_OPTS% -XX:PermSize=256m
set CQ_JVM_OPTS=%CQ_JVM_OPTS% -XX:MaxPermSize=1024m
```

>[!NOTE]
>
>Die empfohlenen Einstellungen gelten für Windows 2008 R2 8 Core und Oracle HotSpot 1.7 (64-bit) JDK und sollten gemäß Ihrer Systemkonfiguration angepasst werden.

## Webserver verwenden {#using-a-web-server}

Adaptive Formulare und HTML5-Formulare werden im HTML5-Format wiedergegeben. Die resultierende Ausgabe kann abhängig von Faktoren wie der Formulargröße und den Bildern im Formular groß sein. Um die Datenübertragung zu optimieren, wird empfohlen, die HTML-Antwort mit dem Webserver zu komprimieren, von dem aus die Anforderung bereitgestellt wird. Dieser Ansatz reduziert die Antwortgröße, den Netzwerk-Traffic und die zum Streamen von Daten zwischen Server- und Client-Computern erforderliche Zeit.

Führen Sie beispielsweise die folgenden Schritte aus, um die Komprimierung auf Apache Web Server 2.0 32-Bit mit JBoss zu aktivieren:

>[!NOTE]
>
>Die folgenden Anweisungen gelten für keine anderen Server als Apache Web Server 2.0 32 Bit.  Informationen über spezielle Schritte für andere Server finden Sie in der entsprechenden Produktdokumentation.

Die folgenden Schritte zeigen die Änderungen, die erforderlich sind, um die Komprimierung mit Apache Web Server zu aktivieren

**Installieren Sie die Apache-Webserver-Software für Ihr Betriebssystem.**

* Windows: Laden Sie den Apache-Webserver von der Apache HTTP Server Project-Site herunter.
* Solaris 64-Bit: Laden Sie den Apache-Webserver von der Sunfreeware for Solaris-Website herunter.
* Linux: der Apache-Webserver ist auf einem Linux-System vorinstalliert.

Apache kann mit CRX über das HTTP-Protokoll kommunizieren. Die Konfigurationen dienen der Optimierung mithilfe von HTTP.

1. Entfernen Sie den Kommentar für folgende Modulkonfigurationen in der Datei `APACHE_HOME/conf/httpd.conf`.

   ```java
   LoadModule proxy_balancer_module modules/mod_proxy.so
   LoadModule proxy_balancer_module modules/mod_proxy_http.so
   LoadModule deflate_module modules/mod_deflate.so
   ```

   >[!NOTE]
   >
   >Für Linux lautet der Standard für `APACHE_HOME` `/etc/httpd/`.

1. Konfigurieren Sie das Proxys auf Port 4502 von crx.

   Fügen Sie in die `APACHE_HOME/conf/httpd.conf`-Konfigurationsdatei folgende Konfiguration ein.

   ```java
   ProxyPass / https://<server>:4502/
   ProxyPassReverse / https://<server>:4502/
   ```

1. Aktivieren Sie die Komprimierung. Fügen Sie in die `APACHE_HOME/conf/httpd.conf`-Konfigurationsdatei folgende Konfiguration ein.

   **Für HTML5-Formulare**

   ```java
   <Location /content/xfaforms>
       <IfModule mod_deflate.c>
           SetOutputFilter DEFLATE
           #Don’t compress
           SetEnvIfNoCase Request_URI \.(?:gif|jpe?g|png)$ no-gzip dont-vary
           SetEnvIfNoCase Request_URI \.(?:exe|t?gz|zip|bz2|sit|rar)$ no-gzip dont-vary
           #Dealing with proxy servers
               <IfModule mod_headers.c>
                   Header append Vary User-Agent
               </IfModule>
       </IfModule>
   </Location>
   ```

   **Für adaptive Formulare**

   ```java
   <Location /content/forms/af>
       <IfModule mod_deflate.c>
           SetOutputFilter DEFLATE
           #Don’t compress
           SetEnvIfNoCase Request_URI \.(?:gif|jpe?g|png)$ no-gzip dont-vary
           SetEnvIfNoCase Request_URI \.(?:exe|t?gz|zip|bz2|sit|rar)$ no-gzip dont-vary
           #Dealing with proxy servers
               <IfModule mod_headers.c>
                   Header append Vary User-Agent
               </IfModule>
       </IfModule>
   </Location>
   ```

   Verwenden Sie für den Zugriff auf den CRX-Server `https://[server]:80`, wobei `server` für den Namen des Servers steht, auf dem der Apache-Server ausgeführt wird.

## Verwenden eines Antivirenprogramms auf dem Server, auf dem AEM Forms ausgeführt wird {#using-an-antivirus-on-server-running-aem-forms}

Auf Servern, auf denen eine Antivirensoftware ausgeführt wird, kann die Leistung beeinträchtigt werden. Eine immer auf Antivirensoftware (On-Access Scan) scannt alle Dateien eines Systems. Dies kann den Server verlangsamen und die Leistung der AEM Forms wird beeinträchtigt.

Um die Leistung zu verbessern, können Sie die Antivirus-Software anweisen, die folgenden AEM Forms-Dateien und -Ordner von der (On-Access-)Prüfung auszuschließen:

* AEM Installationsverzeichnis. Wenn es nicht möglich ist, das vollständige Verzeichnis auszuschließen, schließen Sie Folgendes aus:

   * [AEM-Installationsverzeichnis]\crx-repository\temp
   * [AEM-Installationsverzeichnis]\crx-repository\repository
   * [AEM-Installationsverzeichnis]\crx-repository\launchpad

* Temporärer Ordner des Anwendungsservers. Der Standardspeicherort lautet:

   * (Jboss) [AEM-Installationsverzeichnis]\jboss\standalone\tmp
   * (Weblogic) \Oracle\Middleware\user_projects\domains\LCDomain\servers\LCServer1\tmp
   * (Websphere) \Program Files\IBM\WebSphere\AppServer\profiles\AppSrv01\temp

* **(Nur AEM Forms on JEE)** Ordner des globalen Dokumentenspeichers (GDS). Der Standardspeicherort lautet:

   * (JBoss) `[appserver root]/server/[server]/svcnative/DocumentStorage`
   * (WebLogic) `[appserverdomain]/[server]/adobe/LiveCycleServer/DocumentStorage`
   * (WebSphere) `[appserver root]/installedApps/adobe/[server]/DocumentStorage`

* **(Nur AEM Forms unter JEE),** AEM Forms-Serverprotokolle und temporäres Verzeichnis. Der Standardspeicherort lautet:

   * Serverprotokolle - `[AEM Forms installation directory]\Adobe\AEM forms\[app-server]\server\all\logs`
   * Temporäres Verzeichnis: [AEM Forms-Installationsverzeichnis]\temp

>[!NOTE]
>
>* Wenn Sie einen anderen Speicherort für den globalen Dokumentenspeicher und den temporären Ordner verwenden, öffnen Sie die AdminUI unter `https://[server]:[port]/adminui)`, navigieren Sie zu **Startseite > Einstellungen > Core-Systemeinstellungen > Core-Konfigurationen** zur Bestätigung des verwendeten Standorts.
* Wenn der AEM Forms-Server auch nach dem Ausschließen der vorgeschlagenen Ordner langsam arbeitet, schließen Sie die ausführbare Java-Datei (java.exe) ebenfalls aus. 
>

