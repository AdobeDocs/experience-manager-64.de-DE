---
title: Optimieren von HTML5-Formularen
seo-title: Optimizing HTML5 forms
description: Sie können die Ausgabegröße der HTML5-Formulare optimieren.
seo-description: You can optimize the output size of the HTML5 forms.
uuid: 959f0b6a-9e4d-478a-afa8-4c39011fdf7a
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: bdb9edc2-6a37-4d3f-97d5-0fc5664316be
feature: Mobile Forms
exl-id: 8d2b5294-9763-4348-b927-706ebac90b95
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 24%

---

# Optimieren von HTML5-Formularen {#optimizing-html-forms}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

HTML5 forms rendert Formulare im HTML5-Format. Die resultierende Ausgabe kann abhängig von Faktoren wie der Formulargröße und den Bildern im Formular groß sein. Um die Datenübertragung zu optimieren, wird empfohlen, die HTML-Antwort mit dem Webserver zu komprimieren, von dem aus die Anforderung bereitgestellt wird. Dieser Ansatz reduziert die Antwortgröße, den Netzwerk-Traffic und die zum Streamen von Daten zwischen dem Server und den Clientgeräten erforderliche Zeit.

In diesem Artikel werden die Schritte beschrieben, die zum Aktivieren der Komprimierung für den 32-Bit-Apache-Webserver 2.0 mit JBoss erforderlich sind.

*Hinweis: Die folgenden Anweisungen gelten nicht für andere Server als Apache Web Server 2.0 32 Bit.*

Installieren Sie die Apache-Webserver-Software für Ihr Betriebssystem:

* Für Windows laden Sie den Apache-Webserver von der Apache HTTP Server Project-Site herunter.
* Für Solaris 64 Bit laden Sie den Apache-Webserver von der Sunfreeware for Solaris-Website herunter.
* Für Linux ist der Apache-Webserver auf einem Linux-System vorinstalliert.

Apache kann mit JBoss über HTTP oder das AJP-Protokoll kommunizieren.

1. Entfernen Sie den Kommentar für folgende Modulkonfigurationen in der Datei *APACHE_HOME/conf/httpd.conf*.

   ```java
   LoadModule proxy_balancer_module modules/mod_proxy.so
   LoadModule proxy_balancer_module modules/mod_proxy_http.so
   LoadModule deflate_module modules/mod_deflate.so
   ```

   >[!NOTE]
   >
   >Für Linux ist der Standardordner APACHE_HOME /etc/httpd/.

1. Konfigurieren Sie den Proxy auf Port 8080 von JBoss.

   Fügen Sie in die Datei *APACHE_HOME/conf/httpd.conf* folgende Konfiguration ein.

   ```java
   ProxyPass / https://<server_Name>:8080/
   ProxyPassReverse / https://<server_Name>:8080/
   ```

   >[!NOTE]
   >
   >Wenn Sie einen Proxy verwenden, sind die folgenden Konfigurationsänderungen erforderlich:
   > 
   >* Zugriff: *https://&lt;server>:&lt;port>/system/console/configMgr*
   * Bearbeiten Sie die Konfiguration für den Apache Sling Referrer Filter
   * Fügen Sie unter &quot;Hosts zulassen&quot;den Eintrag für den Proxyserver hinzu.


1. Aktivieren Sie die Komprimierung.

   Fügen Sie in die Konfigurationsdatei *APACHE_HOME/conf/httpd.conf* folgende Konfiguration ein.

   ```java
   <Location /content/xfaforms>
     <IfModule mod_deflate.c>
        SetOutputFilter DEFLATE
        # Don’t compress
        SetEnvIfNoCase Request_URI \.(?:gif|jpe?g|png)$ no-gzip dont-vary
        SetEnvIfNoCase Request_URI \.(?:exe|t?gz|zip|bz2|sit|rar)$ no-gzip dont-vary
       #Dealing with proxy servers
   
        <IfModule mod_headers.c>
           Header append Vary User-Agent
        </IfModule>
     </IfModule>
   </Location>
   ```

1. Um auf den AEM-Server zuzugreifen, verwenden Sie https://[Apache_server]:80.
