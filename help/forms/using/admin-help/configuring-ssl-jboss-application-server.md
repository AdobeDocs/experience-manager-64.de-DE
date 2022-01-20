---
title: SSL für JBoss Application Server konfigurieren
seo-title: Configuring SSL for JBoss Application Server
description: Erfahren Sie, wie Sie SSL für JBoss Application Server konfigurieren.
seo-description: Learn how to configure SSL for JBoss Application Server.
uuid: 7c13cf00-ea89-4894-a4fc-aaeec7ae9f66
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: c187daa4-41b7-47dc-9669-d7120850cafd
exl-id: 1888b8c7-d077-4e54-b442-5df0ba557513
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '908'
ht-degree: 51%

---

# SSL für JBoss Application Server konfigurieren {#configuring-ssl-for-jboss-application-server}

Zum Konfigurieren von SSL unter JBoss Application Server benötigen Sie eine SSL-Berechtigung für die Authentifizierung. Sie können das Java-Keytool zum Erstellen einer Berechtigung oder zum Anfordern und Importieren einer Berechtigung von einer Zertifizierungsstelle verwenden. Anschließend müssen Sie SSL unter JBoss aktivieren.

Sie können das Keytool mit einem einzelnen Befehl ausführen, der alle zum Erstellen des Keystore erforderlichen Informationen enthält.

In diesem Verfahren gilt:

* `[appserver root]` ist der Basisordner des Anwendungsservers, auf dem AEM Formulare ausgeführt werden.
* `[type]` ist ein Ordnername, der je nach Art der von Ihnen ausgeführten Installation variiert.

## SSL-Berechtigung erstellen {#create-an-ssl-credential}

1. Wechseln Sie an einer Eingabeaufforderung zum *[JAVA HOME]*/bin und geben Sie den folgenden Befehl ein, um die Berechtigung und den Keystore zu erstellen:

   `keytool -genkey -dname "CN=`*Hostname* `, OU=`*Gruppenname* `, O=`*Firmenname* `,L=`*Ortsname* `, S=`*state* `, C=`Ländercode&quot; `-alias "AEMForms Cert"` `-keyalg RSA -keypass`*key_password* `-keystore`*keystorename* `.keystore`

   >[!NOTE]
   >
   >Ersetzen `[JAVA_HOME]` durch den Ordner, in dem das JDK installiert ist, und ersetzen Sie kursiv den Text durch die Werte, die Ihrer Umgebung entsprechen. Der Hostname ist der voll qualifizierte Domänenname des Anwendungsservers.

1. Geben Sie die `keystore_password` bei Aufforderung zur Eingabe eines Kennworts. Das Kennwort für den Keystore und der Schlüssel müssen identisch sein.

   >[!NOTE]
   >
   >Die `keystore_password` *in diesen Schritt eingegeben wird, kann dasselbe Kennwort (key_password) sein, das Sie in Schritt 1 eingegeben haben, oder es kann anders sein.*

1. Kopieren Sie die *keystorename*.keystore zum `[appserver root]/server/[type]/conf` Verzeichnis durch Eingabe eines der folgenden Befehle:

   * (Windows-Einzelserver) `copy` `keystorename.keystore[appserver root]\standalone\configuration`
   * (Windows Server Cluster) copy `keystorename.keystore[appserver root]\domain\configuration`
   * (Linux-Einzelserver) `cp keystorename.keystore [appserver root]/standalone/configuration`
   * (Linux-Servercluster) `cp <em>keystorename</em>.keystore<em>[appserver root]</em>/domain/configuration`


1. Exportieren Sie die Zertifikatdatei durch Eingabe des folgenden Befehls:

   * (Einzelserver) `keytool -export -alias "AEMForms Cert" -file AEMForms_cert.cer -keystore [appserver root]/standalone/configuration/keystorename.keystore`
   * (Servercluster) `keytool -export -alias "AEMForms Cert" -file AEMForms_cert.cer -keystore [appserver root]/domain/configuration/keystorename.keystore`

1. Geben Sie das *keystore_Kennwort* ein, wenn Sie zur Eingabe eines Kennworts aufgefordert werden.
1. Kopieren Sie die Datei AEMForms_cert.cer in die *[Anwendungsserver-Stammordner] \conf* Verzeichnis durch Eingabe des folgenden Befehls:

   * (Windows-Einzelserver) `copy AEMForms_cert.cer [appserver root]\standalone\configuration`
   * (Windows Server-Cluster) `copy AEMForms_cert.cer [appserver root]\domain\configuration`
   * (Linux-Einzelserver) `cp AEMForms _cert.cer [appserver root]\standalone\configuration`
   * (Linux-Servercluster) `cp AEMForms _cert.cer [appserver root]\domain\configuration`

1. Zeigen Sie den Inhalt des Zertifikats durch Eingabe des folgenden Befehls an:

   * `keytool -printcert -v -file [appserver root]\standalone\configuration\AEMForms_cert.cer`
   * `keytool -printcert -v -file [appserver root]\domain\configuration\AEMForms_cert.cer`

1. So gewähren Sie Schreibzugriff auf die Datei &quot;cacerts&quot;in `[JAVA_HOME]\jre\lib\security`Führen Sie bei Bedarf die folgende Aufgabe aus:

   * (Windows) Klicken Sie mit der rechten Maustaste auf die Datei „cacerts“, wählen Sie „Eigenschaften“ und deaktivieren Sie das Attribut „Schreibgeschützt“.
   * (Linux) Typ `chmod 777 cacerts`

1. Importieren Sie das Zertifikat durch Eingabe des folgenden Befehls:

   `keytool -import -alias “AEMForms Cert” -file`*AEMForms_cert* `.cer -keystore`*JAVA_HOME* `\jre\lib\security\cacerts`

1. Typ `changeit` als Kennwort. Dieses Kennwort ist das Standardkennwort für Java-Installationen. Eventuell wurde es von Ihrem Systemadministrator geändert.
1. Wenn Sie dazu aufgefordert werden `Trust this certificate? [no]`:, type `yes`. Daraufhin wird die Bestätigung „Certificate was added to keystore“ angezeigt.
1. Wenn Sie die Verbindung über SSL von Workbench aus herstellen, müssen Sie das Zertifikat auf dem Workbench-Computer installieren.
1. Öffnen Sie in einem Texteditor die folgende Dateien zur Bearbeitung:

   * Einzelserver - `[appserver root]`/standalone/configuration/lc_&lt;dbname turnkey=&quot;&quot;>.xml

   * Servercluster - `[appserver root]`/domain/configuration/host.xml

   * Servercluster - `[appserver root]`/domain/configuration/domain_&lt;dbname>.xml

1. 
   * **Für Einzelserver** Fügen Sie in der Datei „lc_&lt;dbaname/tunkey>.xml“ Folgendes nach dem Abschnitt „&lt;security-realms>“ ein:

   ```as3
   <security-realm name="SSLRealm">
   <server-identities>
   <ssl>
   <keystore path="C:/Adobe/Adobe_Experience_Manager_Forms/jboss/standalone/configuration/aemformses.keystore" keystore-password="changeit" alias="AEMformsCert" key-password="changeit"/>
   </ssl>
   </server-identities>
   </security-realm>
   ```

   Suchen Sie die `<server>` -Abschnitt nach dem folgenden Code vorhanden ist:

   `<http-listener name="default" socket-binding="http" redirect-socket="https" max-post-size="104857600"/>`

   Fügen Sie Folgendes dem &lt;server>-Abschnitt hinzu, der nach dem obigen Code steht:

   ```
   <https-listener name="default-secure" socket-binding="https" security-realm="SSLRealm"/>
   ```

   * **Bei Serverclustern:** im [Anwendungsserver-Stammordner]\domain\configuration\host.xml auf allen Knoten fügen Sie Folgendes hinzu, nachdem &lt;security-realms> Abschnitt:

   ```as3
   <security-realm name="SSLRealm">
   <server-identities>
   <ssl>
   <keystore path="C:/Adobe/Adobe_Experience_Manager_Forms/jboss/standalone/configuration/aemformses.keystore" keystore-password="changeit" alias="AEMForms Cert" key-password="changeit"/>
   </ssl>
   </server-identities>
   </security-realm>
   ```

   Auf dem primären Knoten des Serverclusters im [Anwendungsserver-Stammordner]\domain\configuration\domain_&lt;dbname>.xml, suchen Sie die &lt;server> -Abschnitt nach dem folgenden Code vorhanden ist:

   `<http-listener name="default" socket-binding="http" redirect-socket="https" max-post-size="104857600"/>`

   Fügen Sie Folgendes dem &lt;server>-Abschnitt hinzu, der nach dem obigen Code steht:

   ```
   <https-listener name="default-secure" socket-binding="https" security-realm="SSLRealm"/>
   ```

1. Ändern Sie die Werte für die Attribute `keystoreFile` und `keystorePass` in das Keystore-Kennwort, das Sie beim Erstellen des Keystore festgelegt haben.
1. Starten Sie den Anwendungsserver neu.

   * Für Turnkey-Installationen:

      * Klicken Sie in der Windows-Systemsteuerung auf Verwaltung und dann auf Dienste.
      * Wählen Sie JBoss für Adobe Experience Manager Forms.
      * Wählen Sie Aktion > Anhalten.
      * Warten Sie, bis als Status des Dienstes „Angehalten“ angezeigt wird.
      * Wählen Sie Aktion > Starten.
   * Für von Adobe vorkonfigurierte oder manuell konfigurierte JBoss-Installationen:

      * Wechseln Sie an einer Eingabeaufforderung zum *`[appserver root]`*/bin.
      * Beenden Sie den Server durch Eingabe des folgenden Befehls:

         * (Windows) `shutdown.bat -S`
         * (Linux) `./shutdown.sh -S`
      * Warten Sie, bis der JBoss-Prozess vollständig heruntergefahren wurde. (Dies ist der Fall, wenn der JBoss-Prozess die Kontrolle wieder an das Terminal übergibt, in dem er gestartet wurde.)
      * Starten Sie den Server durch Eingabe des folgenden Befehls:

         * (Windows) `run.bat -c <profile>`
         * (Linux) `./run.sh -c <profile>`



1. Um mithilfe von SSL auf Administration Console zuzugreifen, geben Sie `https://[host name]:[port]/adminui` in einem Webbrowser:

   Der SSL-Standardanschluss für JBoss ist 8443. Geben Sie von hier an beim Zugriff auf AEM Forms diesen Anschluss an.

## Berechtigung von einer Zertifizierungsstelle anfordern {#request-a-credential-from-a-ca}

1. Wechseln Sie an einer Eingabeaufforderung zum *[JAVA HOME]*/bin und geben Sie den folgenden Befehl ein, um den Keystore und den Schlüssel zu erstellen:

   `keytool -genkey -dname "CN=`*Hostname* `, OU=`*Gruppenname* `, O=`*Firmenname* `, L=`*Ortsname* `, S=`*state* `, C=`*Ländercode*&quot; `-alias "AEMForms Cert"` `-keyalg RSA -keypass`-*key_password* `-keystore`*keystorename* `.keystore`

   >[!NOTE]
   >
   >Ersetzen *`[JAVA_HOME]`* durch den Ordner, in dem das JDK installiert ist, und ersetzen Sie kursiv den Text durch die Werte, die Ihrer Umgebung entsprechen.

1. Geben Sie den folgenden Befehl ein, um eine Zertifikatanforderung an die Zertifizierungsstelle zu erzeugen:

   `keytool -certreq -alias` &quot;AEMForms Cert&quot; `-keystore`*keystorename* `.keystore -file`*AEMFormscertRequest.csr*

1. Wenn Ihre Anforderung einer Zertifikatdatei erfüllt wurde, führen Sie die Schritte im nächsten Verfahren durch.

## Berechtigung von einer Zertifizierungsstelle zum Aktivieren von SSL verwenden {#use-a-credential-obtained-from-a-ca-to-enable-ssl}

1. Wechseln Sie an einer Eingabeaufforderung zum *`[JAVA HOME]`*/bin und geben Sie den folgenden Befehl ein, um das Stammzertifikat der Zertifizierungsstelle zu importieren, mit der die CSR signiert wurde:

   `keytool -import -trustcacerts -file` rootcert.pem -keystore` keystorename.keystore -alias root`

   Wenn sich das Stammzertifikat nicht im Browser befindet, importieren Sie es ebenfalls dorthin.

   >[!NOTE]
   >
   >Ersetzen *`[JAVA_HOME]`durch den Ordner, in dem das JDK installiert ist, und ersetzen Sie kursiv den Text durch die Werte, die Ihrer Umgebung entsprechen.*

1. Wechseln Sie an einer Eingabeaufforderung zum *`[JAVA HOME]`*/bin und geben Sie den folgenden Befehl ein, um die Berechtigung in den Keystore zu importieren:

   `keytool -import -trustcacerts -file`*CACertificateName* `.crt -keystore`*keystorename* `.keystore`

   >[!NOTE]
   >
   >* Ersetzen `[JAVA_HOME]` durch den Ordner, in dem das JDK installiert ist, und ersetzen Sie kursiv den Text durch die Werte, die Ihrer Umgebung entsprechen.
   >* Das importierte, von der Zertifizierungsstelle signierte Zertifikat ersetzt ein selbst signiertes Zertifikat (sofern vorhanden).


1. Führen Sie die Schritte 13 bis 18 im Abschnitt „SSL-Berechtigung erstellen“ durch.
