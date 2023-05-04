---
title: Installieren und Konfigurieren von interaktiven Kommunikationen
seo-title: Install and configure Interactive Communications
description: Installieren und konfigurieren Sie interaktive Kommunikationen in AEM Forms, um Geschäftskorrespondenzen, Dokumente, Kontoauszüge, Mitteilungen über finanzielle Leistungen, Marketing-E-Mails, Rechnungen und Willkommens-Kits zu erstellen.
seo-description: Install and configure AEM Forms Interactive Communications to create business correspondences, documents, statements, benefit notices, marketing mails, bills, and welcome kits.
uuid: c09b5743-3cbc-49ff-977a-b6b3eb81b160
topic-tags: installing
discoiquuid: 674c6b68-8a04-4cd3-a63e-9968ca686948
role: Admin
exl-id: c7aaa81d-d140-44d9-9144-0cbf6ec5d650
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1420'
ht-degree: 66%

---

# Installieren und konfigurieren Sie Interaktive Kommunikationen {#install-and-configure-interactive-communications}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Einführung {#introduction}

Mit AEM Form lässt sich die Generierung, Zusammenstellung, Verwaltung und Lieferung von sicheren und interaktiven Dokumenten wie Geschäftskorrespondenzen, Dokumenten, Kontoauszügen, Mitteilungen über finanzielle Leistungen, Marketing-Mails, Rechnungen und Willkommenspaketen zentralisieren. Diese Funktion wird als interaktive Kommunikation bezeichnet. Die Funktion ist im Add-on-Paket zu AEM Forms enthalten. Das Add-On-Paket wird auf einer Autoren- oder Veröffentlichungsinstanz von AEM bereitgestellt.

Sie können die interaktive Kommunikationsfunktion verwenden, um Kommunikation in mehreren Formaten zu erstellen. Zum Beispiel Web und PDF. Sie können die interaktive Kommunikation mit AEM Workflow integrieren, um die assemblierte Kommunikation zu verarbeiten und an die Kunden auf dem Kanal ihrer Wahl zu liefern. Beispielsweise das Senden einer Kommunikation an den Endbenutzer per E-Mail.

Wenn Sie ein Upgrade von einer früheren Version durchführen und bereits in die Korrespondenzverwaltung investiert haben, können Sie das [Kompatibilitätspaket](/help/forms/using/installing-configuring-intreactive-communication-correspondence-management.md#install-compatibility-package) installieren, um die Korrespondenzverwaltung weiterhin zu verwenden. Informationen zu den Unterschieden zwischen interaktiver Kommunikation und Korrespondenzverwaltung finden Sie unter [Übersicht über interaktive Kommunikation](/help/forms/using/interactive-communications-overview.md#interactive-communications-vs-correspondence-management).

AEM Forms ist eine leistungsstarke Plattform der Unternehmensklasse. Interaktive Kommunikation ist nur eine der Funktionen von AEM Forms. Eine vollständige Liste der Funktionen finden Sie unter [Einführung in AEM Forms](/help/forms/using/introduction-aem-forms.md).

## Bereitstellungstopologie {#deployment-topology}

Das AEM Forms Add-On-Paket ist eine Anwendung, die auf AEM bereitgestellt wird. Sie benötigen nur mindestens eine AEM-Autoren- und Verarbeitungsinstanz, um die interaktive Kommunikationsfunktion auszuführen. Die folgende Topologie ist eine indikative Topologie für die Ausführung von AEM Forms Interactive Communications, Correspondence Management, AEM Forms-Datenerfassung und Forms-zentrierten Workflows für OSGi-Funktionen. Detaillierte Informationen zu Topologien finden Sie unter [Architektur und Bereitstellungstopologien für AEM Forms](/help/forms/using/aem-forms-architecture-deployment.md).

![recommended-topology](assets/recommended-topology.png)

AEM Forms Interactive Communications führt Administrations-, Authoring- und Agentenbenutzeroberflächen auf den Autoreninstanzen von AEM Forms aus. Die Veröffentlichungsinstanzen hosten die endgültige Version der interaktiven Kommunikation, die für Endbenutzer nutzbar ist.

## Systemanforderungen {#system-requirements}

Bevor Sie mit der Installation und Konfiguration interaktiver Kommunikations- und Korrespondenzverwaltungsfunktionen von AEM Forms beginnen, stellen Sie Folgendes sicher:

* Hardware- und Software-Infrastruktur ist eingerichtet. Eine detaillierte Liste der unterstützten Hardware und Software finden Sie unter [Technische Anforderungen](/help/sites-deploying/technical-requirements.md).

* Der Installationspfad der AEM-Instanz enthält keine Leerzeichen.
* Eine AEM Instanz läuft. In der AEM-Terminologie entspricht eine „Instanz“ einer Kopie von AEM, die auf einem Server im Autor- oder Veröffentlichungsmodus ausgeführt wird. Sie benötigen mindestens eine AEM-Instanz (Autor oder Verarbeitung), um die interaktiven Kommunikations- und Korrespondenzverwaltungsfunktionen von AEM Forms ausführen zu können:

   * **Autor**: Eine zum Erstellen, Hochladen und Bearbeiten von Inhalten sowie zum Verwalten der Website verwendete AEM-Instanz. Sobald der Inhalt für die Veröffentlichung bereit ist, wird er an die Veröffentlichungsinstanz repliziert.
   * **Verarbeitung:** Eine Verarbeitungsinstanz ist [gehärtete AEM-Autoreninstanz](/help/forms/using/hardening-securing-aem-forms-environment.md) -Instanz. Nach der Installation können Sie eine Autoreninstanz festlegen und absichern. 
   * **Veröffentlichen**: Eine AEM Instanz, die die veröffentlichten Inhalte über das Internet oder ein internes Netzwerk öffentlich zugänglich macht.

* Die Speicheranforderungen sind erfüllt. Für das Add-on-Paket für AEM Forms ist Folgendes erforderlich:

   * 15 GB temporärer Speicherplatz für Windows-basierte Installationen von Microsoft.
   * 6 GB temporärer Speicherplatz für UNIX-basierte Installationen.

* Zusätzliche Anforderungen für UNIX-basierte Systeme: Wenn Sie das UNIX-basierte Betriebssystem verwenden, installieren Sie die folgenden Pakete aus den Installationsmedien des jeweiligen Betriebssystems.

<table> 
 <tbody> 
  <tr> 
   <td>expat</td> 
   <td>libxcb</td> 
   <td>freetype</td> 
   <td>libXau</td> 
  </tr> 
  <tr> 
   <td>libSM</td> 
   <td>zlib</td> 
   <td>libICE</td> 
   <td>libuuid</td> 
  </tr> 
  <tr> 
   <td>glibc</td> 
   <td>libXext</td> 
   <td><p>nss-softokn-freebl</p> </td> 
   <td>fontconfig</td> 
  </tr> 
  <tr> 
   <td>libX11</td> 
   <td>libXrender</td> 
   <td>libXrandr</td> 
   <td>libXinerama</td> 
  </tr> 
 </tbody> 
</table>

## Installieren des AEM Forms-Add-on-Pakets {#install-aem-forms-add-on-package}

Das AEM Forms Add-On-Paket ist eine Anwendung, die auf AEM bereitgestellt wird. Das Paket enthält Funktionen für AEM Forms, darunter für interaktive Kommunikation, Korrespondenz-Management und weitere. Führen Sie die folgenden Schritte aus, um das Add-On-Paket zu installieren:

1. Öffnen Sie [Software Distribution](https://experience.adobe.com/downloads). Zum Anmelden bei Software Distribution benötigen Sie eine Adobe ID.
1. Tippen Sie im Kopfzeilenmenü auf **[!UICONTROL Adobe Experience Manager]**.
1. Im **[!UICONTROL Filter]** Abschnitt:
   1. Auswählen **[!UICONTROL Forms]** von **[!UICONTROL Lösung]** Dropdown-Liste.
   2. Wählen Sie die Version aus und geben Sie für das Paket ein. Sie können auch die Option **[!UICONTROL Downloads durchsuchen]** verwenden, um die Ergebnisse zu filtern.
1. Tippen Sie auf den für Ihr Betriebssystem zutreffenden Paketnamen, wählen Sie **[!UICONTROL EULA-Bedingungen akzeptieren]** und tippen Sie auf **[!UICONTROL Herunterladen]**.
1. Öffnen Sie [Package Manager](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=de) und klicken Sie auf **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen.
1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

   Sie können das Paket auch über den direkten Link herunterladen, der im Artikel [AEM Forms-Versionen](https://helpx.adobe.com/de/aem-forms/kb/aem-forms-releases.html) aufgeführt ist.

1. Sobald das Paket installiert ist, werden Sie aufgefordert, die AEM-Instanz neu zu starten. **Starten Sie den Server nicht sofort neu.** Warten Sie vor dem Anhalten des AEM Forms-Servers, bis die Meldungen „ServiceEvent REGISTERED“ und „ServiceEvent UNREGISTERED“ nicht mehr in der Datei „[AEM-Installationsverzeichnis]/crx-quickstart/logs/error.log“ angezeigt werden und das Protokoll stabil ist.
1. Wiederholen Sie Schritten 1-7 für alle Autor- und Veröffentlichungsinstanzen. 

## Auf die Installation folgende Konfigurationen {#post-installation-configurations}

AEM Forms verfügt über einige obligatorische und optionale Konfigurationen. Zu den obligatorischen Konfigurationen gehören die Konfiguration von BouncyCastle-Bibliotheken und Serialisierungsagenten. Zu den optionalen Konfigurationen gehören die Konfiguration von Dispatcher und Adobe Target.

### Obligatorische Konfigurationen nach der Installation {#mandatory-post-installation-configurations}

#### Konfigurieren von RSA- und BouncyCastle-Bibliotheken  {#configure-rsa-and-bouncycastle-libraries}

Führen Sie sowohl auf der Autor- als auch auf der Veröffentlichungsinstanz folgende Schritte zum Boot-Delegate der Bibliotheken aus:

1. Beenden Sie die zugrunde liegenden AEM-Instanz.
1. Öffnen Sie die Datei „[AEM-Installationsverzeichnis]\crx-quickstart\conf\sling.properties“ zur Bearbeitung.

   Wenn Sie AEM mit „[AEM-Installationsverzeichnis]\crx-quickstart\bin\start.bat“ gestartet haben, bearbeiten Sie die Datei „sling.properties“ unter [AEM_root]\crx-quickstart\.

1. Fügen Sie die folgenden Eigenschaften der sling.properties-Datei hinzu:

   ```
   sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*
   sling.bootdelegation.class.org.bouncycastle.jce.provider.BouncyCastleProvider=org.bouncycastle.*
   ```

1. (Nur AIX) Fügen Sie die folgenden Eigenschaften zur Datei „sling.properties“ hinzu:

   ```
   sling.bootdelegation.xerces=org.apache.xerces.*
   ```

1. Speichern und schließen Sie die Datei und starten Sie die AEM-Instanz.
1. Wiederholen Sie Schritten 1-4 für alle Autor- und Veröffentlichungsinstanzen. 

#### Konfigurieren Sie den Serialisierungsagenten {#configure-the-serialization-agent}

Führen Sie auf allen Autoren- und Veröffentlichungsinstanzen folgende Schritte aus, um das Paket zur Zulassungsliste hinzuzufügen:

1. Öffnen Sie AEM Configuration Manager in einem Browserfenster. Die Standardeinstellung ist `https://[server]:[port]/system/console/configMgr`.
1. Suchen und öffnen Sie die **Deserialisierungs-Firewallkonfiguration**.
1. Fügen Sie das Paket **sun.util.calendar** zum Feld **Zulassungsliste** hinzu. Klicken Sie auf Speichern.
1. Wiederholen Sie Schritten 1-3 für alle Autor- und Veröffentlichungsinstanzen. 

### Optionale Konfigurationen nach der Installation {#optional-post-installation-configurations}

#### Installieren des Kompatibilitäts-Pakets {#install-compatibility-package}

Interaktive Kommunikation ist der Standard und empfohlene Ansatz, um Kundenkommunikation in AEM 6.4 Forms zu erstellen. Wenn Sie ein Upgrade oder eine Migration von einer früheren Version durchgeführt haben und weiterhin Briefe (Correspondence Management) verwenden möchten, installieren Sie das [AEMFD-Kompatibilitätspaket](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de).

Mit dem AEMFD-Kompatibilitätspaket können Sie die folgenden Assets aus AEM 6.3 Forms und AEM 6.2 Forms auf AEM 6.4 Forms verwenden:

* Dokumentfragmente
* Briefe
* Datenwörterbücher
* Veraltete Vorlagen und Seiten für adaptive Formulare

#### Konfiguration des Dispatchers {#configure-dispatcher}

Dispatcher ist ein Tool zum Zwischenspeichern und für den Lastenausgleich für AEM. AEM Dispatcher hilft auch, AEM Server vor Angriffen zu schützen. Somit können Sie die Sicherheit Ihrer AEM-Instanz verbessern, indem Sie den Dispatcher in Verbindung mit einem Webserver der Unternehmensklasse verwenden. Wenn Sie [Dispatcher](https://helpx.adobe.com/de/experience-manager/dispatcher/using/dispatcher-configuration.html) verwenden, führen Sie die folgenden Konfigurationen für AEM Forms durch:

1. Konfigurieren des Zugriffs für AEM Forms:

   Öffnen Sie die Datei &quot;dispatcher.any&quot;zur Bearbeitung. Navigieren Sie zum Filterabschnitt und fügen Sie dem Filterabschnitt den folgenden Filter hinzu:

   `/0025 { /type "allow" /glob "* /bin/xfaforms/submitaction*" } # to enable AEM Forms submission`

   Speichern und schließen Sie die Datei. Detaillierte Informationen zu Filtern finden Sie unter [Dispatcher-Dokumentation](https://helpx.adobe.com/de/experience-manager/dispatcher/using/dispatcher-configuration.html).

1. Konfigurieren Sie den Referrer-Filterdienst:

   Melden Sie sich beim Apache Felix Configuration Manager als Administrator an. Die Standard-URL für den Configuration Manager lautet `https://[server]:[port_number]/system/console/configMgr`. Wählen Sie im Menü **Configurations** die Option **Apache Sling Referrer Filter.** Geben Sie im Feld „Hosts zulassen“ den Hostnamen des Dispatchers ein, um ihn als Referrer zuzulassen, und klicken Sie auf **Speichern**. Das Format des Eintrags ist `https://[server]:[port]`.

#### Adobe Target integrieren {#integrate-adobe-target}

Ihre Kunden werden interaktive Kommunikation wahrscheinlich verlassen, wenn sie nicht davon angesprochen fühlen. Für die Kunden ist dies ein frustrierendes Erlebnis. Für Ihr Unternehmen kann es zusätzlichen Supportaufwand und Mehrkosten bedeuten. Das Kundenerlebnis optimal zu gestalten und dadurch eine höhere Konvertierungsrate zu erzielen, ist absolut unverzichtbar und stellt zugleich eine große Herausforderung dar. AEM Formulare sind der Schlüssel zu diesem Problem.

AEM forms kann mit der Adobe Marketing Cloud-Lösung Adobe Target integriert werden, um den Kunden ein personalisiertes und ansprechendes Erlebnis über verschiedene digitale Kanäle zu bieten. Um Adobe Target zur Personalisierung einer interaktiven Kommunikation zu verwenden, [integrieren Sie Adobe Target in AEM Forms](/help/forms/using/ab-testing-adaptive-forms.md#setupandintegratetargetinaemforms).

#### Konfigurieren der SSL-Kommunikation für das Formulardatenmodell  {#configure-ssl-communcation-for-form-data-model}

Sie können die SSL-Kommunikation für das Formulardatenmodell aktivieren. Um die SSL-Kommunikation für das Formulardatenmodell zu aktivieren, fügen Sie vor dem Starten einer AEM Forms-Instanz Zertifikate zum Java Trust Store aller Instanzen hinzu. Sie können den folgenden Befehl ausführen, um die Zertifikate hinzuzufügen:

`keytool -import -alias <alias-name> -file <pathTo .cer certificate file> -keystore <<pathToJRE>\lib\security\cacerts>`

## Nächste Schritte {#next-steps}

Sie haben eine Umgebung konfiguriert, in der Funktionen für interaktive Kommunikation und Korrespondenz-Management verwendet werden können. Die nächsten Schritte zur Verwendung der Funktionen, sind Folgende:

* [Überblick über Correspondence Management](/help/forms/using/interactive-communications-overview.md)

* [Interaktive Kommunikation erstellen](/help/forms/using/create-interactive-communication.md)

* [Erstellen eines Correspondence Management-Briefs](/help/forms/using/create-letter.md)
