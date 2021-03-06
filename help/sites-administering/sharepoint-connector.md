---
title: SharePoint-Connector
seo-title: SharePoint Connector
description: Day JCR Connector for Microsoft Sharepoint 2010 und Microsoft SharePoint 2013, Version 4.0.
seo-description: Learn about the Sharepoint Connector in AEM.
uuid: 2f3b90f9-ec6b-4808-bbd4-20e67b6a7573
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: e3f2dc5a-ef5e-432c-be07-b3dedbd6549b
exl-id: cdb45bec-81d7-4356-ac55-5b6a40b35433
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1601'
ht-degree: 73%

---

# SharePoint-Connector{#sharepoint-connector}

Day JCR Connector for Microsoft Sharepoint 2010 und Microsoft SharePoint 2013, Version 4.0.

Dieser Artikel enthält Details zur Adobe JCR Connector für Microsoft SharePoint 2010 und Microsoft SharePoint 2013, Version 4.0.

Der SharePoint-Connector unterstützt folgende grundlegenden Funktionen:

* Lesen von Inhalten und Metadaten aus SharePoint
* Berücksichtigung von SharePoint-Sicherheitseinstellungen für aufgerufene Inhalte mittels Anwendung nativer SharePoint-Authentifizierung und -Autorisierung
* Inhaltsintegration mithilfe der Inhaltssuche
* Anzeige von SharePoint-Bildern und -Videos unter Verwendung von AEM-Komponenten (beispielsweise externe Ressource)
* Synchronisierung von SharePoint mit AEM Assets

Bei der Implementierung aller Funktionen werden die nativen SharePoint-Webdienste als Schnittstelle für SharePoint-Inhalte und -Dienste verwendet.

>[!NOTE]
>
>Der SharePoint-Connector wird auch mit AEM 6.1 Service Pack 2 unterstützt. Die Einbindung virtueller Repositorys wird vom Connector nicht mehr unterstützt, weshalb keine Einbindung möglich ist. Wenn Sie mithilfe von Java-APIs auf das Sharepoint-Repository zugreifen möchten, verwenden Sie die JCR-Repository-Implementierung des SharePoint-Connectors in Ihrem Projekt.
>
>Installation, Konfiguration, Verwaltung und IT-Vorgänge der SharePoint Server-Instanz und der dazugehörigen IT-Infrastruktur werden in diesem Dokument nicht behandelt. Siehe Dokumentation zu Anbietern [SharePoint](https://www.microsoft.com/sharepoint) für Informationen zu diesen Themen. Diese Infrastrukturkomponenten müssen ordnungsgemäß installiert, konfiguriert und betrieben werden, damit der Connector verwendet werden kann.

## Erste Schritte {#getting-started}

Gehen Sie zur Vorbereitung der Connector-Verwendung wie folgt vor:

* Vergewissern Sie sich, dass bei Ihnen mindestens Java 7 installiert ist.
* Laden Sie die Paketverteilungsdatei für den Connector von Package Share herunter.
* Kopieren Sie eine gültige Datei vom Typ *license.properties* in das Verzeichnis, das die Datei *cq-quickstart-6.4.0.jar* enthält.

* Doppelklicken/-tippen Sie auf die JAR-Datei, um AEM zu starten, oder starten Sie AEM über die Befehlszeile.
* Installieren Sie das Connector-Paket über Package Manager.
* Konfigurieren Sie die Connector-Optionen.

## Installieren des SharePoint-Connectors {#installing-sharepoint-connector}

Der Connector liegt als Inhaltspaket vor und lässt sich ganz einfach installieren. Installieren Sie das Paket mithilfe von Package Manager und legen Sie dann die SharePoint-Server-URL fest.\
und anderen Konfigurationsoptionen. Der SharePoint-Inhalt steht im AEM-Repository zur Verfügung.

### Installationsanforderungen {#installation-requirements}

Für den Connector ist Folgendes erforderlich:

* Java Runtime Environment 1.7 oder höher
* SharePoint-Webdienste (verfügbar über das Netzwerk)
* SharePoint Server-URL
* Benutzeranmeldeinformationen und -berechtigungen für CRX- und SharePoint-Repositorys
* [Unterstützte Plattformen](#supported-platforms)

Der SharePoint-Connector kann über heruntergeladen werden. [packageshare](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq630/featurepack/cq-6.3.0-featurepack-17673).

### Unterstützte Plattformen {#supported-platforms}

Der Connector unterstützt Folgendes:

* AEM-Versionen:

   * AEM 6.4, 6.3

* Microsoft SharePoint-Versionen:

   * Microsoft Office SharePoint Server (MOSS) 2010
   * Microsoft Office SharePoint Server (MOSS) 2013

* Wenn Sie Unterstützung für benutzerdefinierte Implementierungen des Connectors (OEM, besondere Anforderungen, angepasste Authentifizierungsmethoden) benötigen, wenden Sie sich die Adobe-Niederlassung für Ihre Region.

>[!NOTE]
>
>Der Connector unterstützt nur Konfigurationen, die offiziell von Microsoft unterstützt werden. Weitere Informationen finden Sie in den Systemanforderungen für [MOSS 2010](https://technet.microsoft.com/en-us/library/cc262485(office.14).aspx) und [MOSS 2013](https://technet.microsoft.com/en-us/library/cc262485.aspx).

### Standardinstallation {#standard-installation}

Produktfeatures, Beispiele und Hotfixes werden über AEM Package Share verteilt. Weitere Informationen finden Sie unter [Package Share-Dokumentation](/help/sites-administering/package-manager.md#package-share).

Um auf die Paketfreigabe auf der AEM Begrüßungsseite zuzugreifen, tippen/klicken Sie auf **Instrumente** und wählen Sie **Package Share**. Sie benötigen einen gültigen Adobe ID, der Ihre Unternehmens-E-Mail-Adresse enthält. Nach der Anmeldung bei Ihrem Konto müssen Sie außerdem Zugriff auf Package Share anfordern.

#### Integrieren mit AEM {#integrating-with-aem}

Gehen Sie zum Installieren des Connector-Inhaltspakets wie folgt vor:

1. Erstellen Sie ein Adobe-Supportticket, um das Connector-Featurepaket anzufordern.
1. Laden Sie das Paket herunter, wenn es verfügbar ist, und öffnen Sie Package Manager für Ihre AEM-Instanz.
1. Tippen/klicken **Installieren** von der Paketbeschreibungsseite aus.
1. Aus dem **Installationspaket** dialog, tippen/klicken **Installieren**.

   **Hinweis:** Vergewissern Sie sich, dass Sie als Administrator angemeldet sind.

1. Tippen/klicken Sie bei der Installation des Pakets auf **Schließen**.

## Konfigurieren des SharePoint-Connectors {#configuring-sharepoint-connector}

Konfigurieren Sie nach der Installation des SharePoint-Connectors die Anwendung und die SharePoint-Ebenen für den Connector.

Legen Sie die SharePoint Server-URL fest, um Ihr SharePoint-Repository JCR-konform zu machen. Sie können weitere Parameter festlegen, um die Verbindung mit der SharePoint Server-Instanz zu konfigurieren. Konfigurieren Sie außerdem die Authentifizierung mit dem SharePoint-Connector.

### Konfigurieren der Verbindung mit der SharePoint Server-Instanz {#configuring-the-connection-with-the-sharepoint-server}

Führen Sie die folgenden Schritte aus, um die URL der SharePoint Server-Instanz sowie erweiterte Optionen festzulegen:

1. Navigieren Sie zur OSGi-Verwaltungskonsole: [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr).
1. Suchen Sie nach **Day JCR Connector für Microsoft Sharepoint** Bundle.
1. Bearbeiten Sie die Konfigurationswerte.
1. Legen Sie den Wert von **Workspaces** auf die SharePoint Server-URL fest.
1. Tippen/Klicken Sie auf **Speichern**.

![chlimage_1-81](assets/chlimage_1-81.png)

Parameter „Workspaces“ und „Name des Standard-Workspace“:

Standardmäßig macht der Connector einen einzelnen JCR-Workspace verfügbar. Die SharePoint Server-Instanz, die durch diesen Workspace verfügbar gemacht wird, wird mithilfe des Konfigurationsparameters „SharePoint Server-URL“ festgelegt.

Der Connector kann auch für mehrere Workspaces konfiguriert werden. In diesem Fall werden die einzelnen Workspaces jeweils der URL der SharePoint Server-Instanz zugeordnet, die über den Workspace verfügbar gemacht wird. Einen Workspace können Sie hinzufügen, indem Sie dem Parameter „Workspaces“ eine Workspace-Definition hinzufügen. Eine Workspace-Definition weist folgendes Format auf:\
`<name>`= `<url>` Hierbei gilt\
`<name>` ist der Name des JCR-Arbeitsbereichs und\
`<url>` ist die URL des SharePoint-Servers für diesen Arbeitsbereich.

Führen Sie in AEM neben den obigen Konfigurationsschritten noch einen weiteren Schritt aus. Zulassungsliste der **com.day.cq.dam.cq-dam-jcr-connectors**&quot; Bundle.

Führen Sie die folgenden Schritte aus, um Bundles in AEM Zulassungsliste:

1. Navigieren Sie zur OSGi-Verwaltungskonsole: http://localhost:4502/system/console/configMgr

1. Suchen Sie nach dem Dienst &quot;Apache Sling Login Admin Whitelist&quot;.

1. Aktivieren Sie das Kontrollkästchen zur Umgehung der Whitelist.

1. Hinzufügen von **com.day.cq.dam.cq-dam-jcr-connectors**&quot;in Whitelist Bundles Standard

1. Klicken Sie auf Speichern.

![chlimage_1-82](assets/chlimage_1-82.png)

>[!NOTE]
>
>Wenn Sie mehrere Workspaces konfigurieren, geben Sie im Parameter „Name des Standard-Workspace“ den Namen des Standard-Workspace an.

Weitere Informationen zu authentifizierungsbezogenen Parametern finden Sie unter [Authentifizierung](/help/sites-administering/sharepoint-connector.md#configuring-authentication).

### Überprüfen der SharePoint-Einrichtung {#verifying-the-sharepoint-setup}

Vergewissern Sie sich nach dem Konfigurieren des Connectors, dass Folgendes erfüllt ist:

* Die SharePoint Server-Instanz wird ausgeführt und die Connector-Instanz hat Zugriff auf die Webdienste.
* Die SharePoint-Benutzeranmeldeinformationen sind gültig und der Benutzer verfügt über die erforderlichen SharePoint-Berechtigungen.
* Der Connector ist installiert und ordnungsgemäß konfiguriert.

### Konfigurieren der DAM-Synchronisierung mit der SharePoint Server-Instanz {#configuring-dam-sync-with-the-sharepoint-server}

Gehen Sie wie folgt vor, um die SharePoint-Assets mit AEM zu synchronisieren:

1. Navigieren Sie zur OSGi-Verwaltungskonsole: [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr).
1. Suchen Sie nach dem Dienst „Default DAMAssetSynchronization“.
1. Bearbeiten Sie die Konfigurationswerte.
1. Legen Sie den Benutzernamen und das dazugehörige Kennwort des Benutzers fest, der Zugriff auf die SharePoint-Website hat.
1. Klicken Sie auf Speichern.

Aktivieren des standardmäßig deaktivierten DAM-Synchronisierungsdiensts:

1. Navigieren Sie zu den OSGi Web Console-Komponenten: [http://localhost:4502/system/console/components](http://localhost:4502/system/console/components)
1. Suchen Sie nach „com.day.cq.dam.jcrconnectors.impl.AssetSynchronizationService“.
1. Klicken Sie auf „Aktivieren“.

Optional: Sie können auch die Synchronisierungsverzögerung zwischen verschiedenen Synchronisierungszyklen konfigurieren:

1. Navigieren Sie zur OSGi-Verwaltungskonsole: [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)
1. Suchen Sie nach „DAY CQ DAM JCR Connector Asset Synchronization Service“.
1. Bearbeiten Sie die Konfigurationswerte.
1. Legen Sie den Wert des Synchronisierungszeitraums (in Sekunden) fest.
1. Klicken Sie auf Speichern.

### Konfigurieren der Authentifizierung {#configuring-authentication}

SharePoint beinhaltet die klassische und die anspruchsbasierte Authentifizierungsmethode, die jeweils folgende Authentifizierungsarten unterstützen:

* Einfach
* Formularbasiert

Somit stehen folgende Authentifizierungsarten zur Verfügung:

* Klassisch/Standard
* Klassisch/formularbasiert
* Anspruchsbasiert/Standard
* Anspruchs-/formularbasiert

Der AEM JCR Connector für Microsoft SharePoint 2010 und Microsoft SharePoint 2013, Version 4.0. unterstützt eine anspruchsbasierte Authentifizierung (die von Microsoft empfohlen wird), die in folgenden Modi ausgeführt wird:

* **Standard-/NTLM-Authentifizierung:** Der Connector versucht zunächst, unter Verwendung der Standardauthentifizierung eine Verbindung herzustellen. Steht diese Option nicht zur Verfügung, wird die NTLM-basierte Authentifizierung verwendet.
* **Forms-basierte Authentifizierung**: Sharepoint überprüft Benutzer anhand von Anmeldeinformationen, die Benutzer in ein Anmeldeformular eingeben (normalerweise eine Webseite). Das System gibt für authentifizierte Anforderungen ein Token aus, das einen Schlüssel zur Identitätsfeststellung bei Folgeanforderungen enthält.

**Konfigurieren der formularbasierten Authentifizierung**

Gehen Sie zu: [http://localhost:4502/system/console/bundles](http://localhost:4502/system/console/bundles)

1. Klicken Sie auf „OSGi“ > „Konfiguration“.
1. Suchen Sie nach „Day JCR Connector for Microsoft Sharepoint“.
1. Klicken Sie auf „Konfigurationswerte bearbeiten“.
1. Legen Sie den Wert von „SharePoint-Verbindungsfactory“ auf „com.day.crx.spi.sharepoint.security.FormsBasedAuthenticationConnectionFactory“ fest.
1. Klicken Sie auf **Speichern**.

**Konfigurieren der einfachen Authentifizierung (Windows)**

1. [Deaktivieren Sie die Tokenauthentifizierung.](#disable-token-authentication)
1. Navigieren Sie zu [http://localhost:4502/system/console/bundles](http://localhost:4502/system/console/bundles).
1. Klicken Sie auf „OSGi“ > „Konfiguration“.
1. Suchen Sie nach **Day JCR Connector for Microsoft Sharepoint**.
1. Klicken Sie auf `Edit the configuration values`.
1. Legen Sie den Wert für die SharePoint-Verbindungsfactory auf `com.day.crx.spi.sharepoint.security.WindowsAuthenticationConnectionFactory` fest.
1. Klicken Sie auf **Speichern**.

Nur Benutzer, die sowohl in AEM als auch in SharePoint authentifiziert sind, können über den Connector auf den SharePoint-Inhalt zugreifen.

Sie können auch die Connector-Erweiterung zur Authentifizierung verwenden, um ein benutzerdefiniertes Authentifizierungsmodul zu erstellen, das beispielsweise den Zugriff durch AEM-Benutzer bestimmten SharePoint-Benutzern zuordnet. Erstellen Sie AEM-Benutzer, die SharePoint-Benutzern entsprechen (Übereinstimmung von Benutzername und Kennwort), um SharePoint-Inhalt anzeigen zu können, der der Connector-Instanz zugeordnet ist.

So erstellen Sie einen Benutzer in AEM:

1. Melden Sie sich unter http://localhost:9502/ als Administratorbenutzer an.
1. Klicken Sie auf „Tools“.
1. Klicken Sie auf „Sicherheit“.
1. Klicken Sie auf „Benutzer“.
1. Klicken Sie auf **Benutzer erstellen**
1. Geben Sie die Benutzer-ID ein (Benutzername, der Zugriff auf SharePoint hat).
1. Geben Sie das entsprechende Kennwort an.
1. Klicken Sie auf das grüne Häkchen, um den Benutzer zu erstellen.

So fügen Sie den Benutzer der Administratorgruppe hinzu:

1. Navigieren Sie zur Gruppenverwaltung.
1. Klicken Sie auf den Knoten &quot;a&quot;
1. Klicken Sie auf „Administratoren“.
1. Geben Sie die oben erstellte Benutzer-ID in das Textfeld ein, bevor Sie **Durchsuchen** button
1. Klicken Sie auf das grüne Häkchen, um den Benutzer der Administratorgruppe hinzuzufügen.

### Deaktivieren der Tokenauthentifizierung {#disable-token-authentication}

1. Herunterladen und Installieren des Pakets `basic auth`. `zip` von Package Share aus.

1. Schließen Sie den Schnellstart.
1. Öffnen Sie die Datei *\crx-quickstart\repository\repository.xml*.
1. Tag suchen `<LoginModule class="com.day.crx.core.CRXLoginModule"> ... </LoginModule>.`
1. Tag einfügen `<param name="disableTokenAuth" value="true"/>` innerhalb des in Schritt 4 erwähnten Tags.
1. Speichern und schließen Sie die XML-Datei.
1. Starten Sie QuickStart neu und melden Sie sich mit Ihren Anmeldedaten an.

#### Unterstützen verschiedener Authentifizierungsmethoden der SharePoint Server-Instanz {#supporting-different-authentication-methods-of-the-sharepoint-server}

In der Standardversion unterstützt der Connector die **Windows**-IIS-Standardauthentifizierung sowie die formularbasierte Authentifizierung (tokenbasiert). Die [anderen Authentifizierungsmethoden](https://technet.microsoft.com/en-us/library/cc262350.aspx#section2) können über den Erweiterbarkeitsmechanismus unterstützt werden.

Die folgenden Schritte bieten Richtlinien für die Erweiterung der Standardauthentifizierung, um verschiedene Authentifizierungsmethoden der SharePoint Server-Instanz zu unterstützen:

1. Implementieren Sie `com.day.crx.spi.sharepoint.security.SharepointConnectionFactory` für die Clientseite Ihres spezifischen Authentifizierungsprozesses.
1. Installieren Sie die `SharepointConnectionFactory` Implementierung als Fragment-Bundle mit Fragmenthost `com.day.crx.spi.crx2sharepoint-bundle`.

   Passen Sie bei Verwendung von Maven die folgende Konfiguration von `maven-bundle-plugin` an die Anforderungen Ihres Projekts an:

   ```xml
              <plugin>
                  <groupId>org.apache.felix</groupId>
                  <artifactId>maven-bundle-plugin</artifactId>
                  <extensions>true</extensions>
                  <configuration>
                      <instructions>
                          <Export-Package />
                          <Private-Package>
                              <!-- your private package here -->
                          </Private-Package>
                          <Fragment-Host>
                              com.day.crx.spi.crx2sharepoint-bundle
                          </Fragment-Host>
                       </instructions>
                  </configuration>
              </plugin>
   ```

1. Registrieren Sie die Implementierung `SharepointConnectionFactory` in der Connector-Konfiguration. Klicken Sie im Konfigurationsfenster des Connectors auf **Erweiterte Optionen**. Im für **SharePoint-Verbindungsfactory** -Feld den Namen der Implementierung angeben `com.day.crx.spi.sharepoint.auth.CustomConnectionFactory`.

1. Starten Sie den Connector neu.
