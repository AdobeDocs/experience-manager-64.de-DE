---
title: Technische Anforderungen
seo-title: Technical Requirements
description: Eine Liste der unterstützten Client- und Server-Plattformen für AEM.
seo-description: A list of the supported client and server platforms for AEM.
uuid: d5bdcd41-3585-41f7-860d-8068a2931a72
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: platform
discoiquuid: 4d3c4650-3e2a-43b1-ad2d-8d0ae2254ca9
exl-id: 21c10b39-ca37-4085-86f8-063c30a180ed
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3295'
ht-degree: 69%

---

# Technische Anforderungen {#technical-requirements}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Adobe unterstützt Adobe Experience Manager (AEM) auf den Plattformen, wie in den folgenden Informationen in diesem Dokument beschrieben.

Wenden Sie sich bei Problemen, die speziell mit der Plattform selbst in Verbindung stehen, direkt an den Plattformanbieter.

>[!NOTE]
>
>Je nach Plattform, auf der Sie AEM installieren, kann es verschiedene Anforderungen für die Benutzerverwaltung geben.

## Voraussetzungen {#prerequisites}

Mindestanforderungen für die Ausführung von Adobe Experience Manager:

* Installierte Java-Plattform, Standard Edition JDK oder andere unterstützte [Java Virtual Machines](#java-virtual-machines)
* Experience Manager-Schnellstartdatei (eigenständige JAR-Datei oder Bereitstellungs-WAR-Datei für Webanwendungen)

### Mindestgrößenanforderungen {#minimum-sizing-requirements}

Mindestanforderungen für die Ausführung von Adobe Experience Manager:

* 5 GB freier Speicherplatz im Installationsverzeichnis
* 2 GB Arbeitsspeicher

>[!NOTE]
>
>* Anwendungsfälle für digitale Assets benötigen mehr Arbeitsspeicher. Siehe [Bereitstellung und Wartung](/help/sites-deploying/deploy.md#default-local-install) für mehr Details.
>* Das [AEM Forms Add-on-Paket](/help/forms/using/installing-configuring-aem-forms-osgi.md) benötigt 15 GB temporären Speicherplatz.
>


Siehe [Richtlinien zur Hardware-Skalierung](/help/managing/hardware-sizing-guidelines.md) für weitere Informationen.

### Unterstützungsebenen {#support-levels}

In diesem Dokument werden die unterstützten Client- und Server-Plattformen für Adobe Experience Manager aufgeführt. Adobe bietet verschiedene Unterstützungsebenen an, die für empfohlene und andere Konfigurationen gelten.

### Unterstützte Konfigurationen {#supported-configurations}

Adobe empfiehlt diese Konfigurationen und bietet im Zuge der standardmäßigen Vereinbarung für die Software-Wartung vollständige Unterstützung.

<table> 
 <tbody> 
  <tr> 
   <td>Unterstützungsebene</td> 
   <td>Beschreibung<br /> </td> 
  </tr> 
  <tr> 
   <td><strong>A: Unterstützt</strong></td> 
   <td>Adobe bietet vollständige Unterstützung und Wartung für diese Konfiguration. Diese Konfiguration wird über den Qualitätssicherungsvorgang von Adobe abgedeckt.</td> 
  </tr> 
  <tr> 
   <td><strong>R: Eingeschränkte Unterstützung </strong></td> 
   <td>Um den Projekterfolg unserer Kundinnen und Kunden sicherzustellen, bietet Adobe im Rahmen eines eingeschränkten Support-Programms volle Unterstützung an, was erfordert, dass bestimmte Bedingungen erfüllt werden. Der Support auf R-Ebene erfordert eine formelle Kundenanfrage und eine Bestätigung durch Adobe. Weitere Informationen erhalten Sie bei der Kundenunterstützung von Adobe.</td> 
  </tr> 
 </tbody> 
</table>

### Nicht unterstützte Konfigurationen {#unsupported-configurations}

| Unterstützungsebene | Beschreibung |
|---|---|
| **Z: Nicht unterstützt** | Die Konfiguration wird nicht unterstützt. Adobe macht keine Angaben dazu, ob die Konfiguration funktioniert, und unterstützt sie nicht. |

## Unterstützte Plattformen {#supported-platforms}

### Java Virtual Machines {#java-virtual-machines}

Für die Anwendung ist eine Java Virtual Machine erforderlich, die durch die Java Development Kit (JDK)-Verteilung bereitgestellt wird.

Adobe Experience Manager funktioniert mit den folgenden Versionen von Java Virtual Machine:

>[!CAUTION]
>
>Es wird empfohlen, die Sicherheitsbulletins vom Java-Anbieter zu verfolgen, um den Schutz und die Sicherheit von Produktionsumgebungen sicherzustellen und die neuesten Java-Aktualisierungen zu installieren.

<table> 
 <tbody> 
  <tr> 
   <td>Plattform</td> 
   <td>Unterstützungsebene<br /> </td> 
  </tr> 
  <tr> 
   <td>Oracle Java SE 11 JDK [1]</td> 
   <td>Z: Nicht unterstützt </td> 
  </tr> 
  <tr> 
   <td>Oracle Java SE 10 JDK [1]</td> 
   <td>Z: Nicht unterstützt </td> 
  </tr> 
  <tr> 
   <td>Oracle Java SE 9 JDK [1]</td> 
   <td>Z: Nicht unterstützt</td> 
  </tr> 
  <tr> 
   <td><strong>Oracle Java SE 8 JDK – 64 Bit</strong></td> 
   <td>A: Unterstützt [3]<br /> </td> 
  </tr> 
  <tr> 
   <td>IBM J9 VM - Build 2.9, JRE 1.8.0 [2]</td> 
   <td>A: Unterstützt</td> 
  </tr> 
  <tr> 
   <td>IBM J9 VM - Build 2.8, JRE 1.8.0 [2]</td> 
   <td>A: Unterstützt</td> 
  </tr> 
 </tbody> 
</table>

1. Oracle ist auf ein LTS-Modell (Long Term Support) für Oracle Java SE-Produkte umgestiegen. Java 9 und 10 sind Nicht-LTS-Versionen von Oracle (siehe [Oracle Java SE-Support-Roadmap](https://www.oracle.com/technetwork/java/eol-135779.html)). Adobe bietet nur Unterstützung für LTS-Versionen von Java, um AEM in der Produktion auszuführen.

1. IBM JRE wird nur in Verbindung mit WebSphere Application Server unterstützt.
1. Der Support und die Bereitstellung von Oracle Java SE, einschließlich aller Wartungsupdates von LTS-Versionen, werden von Adobe direkt für alle AEM-Kunden unterstützt, die die Oracle Java SE-Technologie nutzen. Siehe [Oracle Java-Unterstützung für Adobe Experience Manager - Fragen und Antworten](assets/adobe-oracle-java-license-agreement.pdf) für weitere Informationen.

### Speicherung und Persistenz {#storage-persistence}

Es gibt verschiedene Optionen zum Bereitstellen des Repositorys von Adobe Experience Manager. In der folgenden Liste finden Sie unterstützte Technologien und Speicheroptionen.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Plattform</strong></td> 
   <td><strong>Beschreibung</strong></td> 
   <td><strong>Unterstützungsebene</strong></td> 
  </tr> 
  <tr> 
   <td><strong>Dateisystem mit TAR-Dateien [1]</strong></td> 
   <td>Repository</td> 
   <td>A: Unterstützt</td> 
  </tr> 
  <tr> 
   <td><strong>Dateisystem mit Datenspeicher [1]</strong></td> 
   <td>Binärdateien</td> 
   <td>A: Unterstützt</td> 
  </tr> 
  <tr> 
   <td>Speichern von Binärdateien in TAR-Dateien im Dateisystem [1]</td> 
   <td>Binärdateien</td> 
   <td>Z: Wird nicht für die Produktion unterstützt</td> 
  </tr> 
  <tr> 
   <td>Amazon S3</td> 
   <td>Binärdateien</td> 
   <td>A: Unterstützt</td> 
  </tr> 
  <tr> 
   <td>Microsoft Azure Blob Storage</td> 
   <td>Binärdateien</td> 
   <td>A: Unterstützt</td> 
  </tr> 
  <tr> 
   <td>MongoDB Enterprise 3.6 [5, 6]</td> 
   <td>Repository</td> 
   <td>A: Unterstützt mit Einschränkungen</td> 
  </tr> 
  <tr> 
   <td>MongoDB Enterprise 3.4 [2, 3, 6]</td> 
   <td>Repository</td> 
   <td>A: Unterstützt mit Einschränkungen</td> 
  </tr> 
  <tr> 
   <td>MySQL 5.7</td> 
   <td>Forms-Datenbank</td> 
   <td>A: Unterstützt</td> 
  </tr> 
  <tr> 
   <td>IBM DB2 11.1<br /> </td> 
   <td>Forms-Datenbank</td> 
   <td>A: Unterstützt</td> 
  </tr> 
  <tr> 
   <td>IBM DB2 10.5</td> 
   <td>Repository und Forms-Datenbank</td> 
   <td>R: Eingeschränkte Unterstützung  (4)</td> 
  </tr> 
  <tr> 
   <td>Oracle Database 12c (12.1.x)</td> 
   <td>Repository und Forms-Datenbank</td> 
   <td>R: Eingeschränkte Unterstützung </td> 
  </tr> 
  <tr> 
   <td>Microsoft SQL Server 2017</td> 
   <td>Forms-Datenbank</td> 
   <td>Z: Nicht unterstützt (4)</td> 
  </tr> 
  <tr> 
   <td>Microsoft SQL Server 2016</td> 
   <td>Forms-Datenbank</td> 
   <td>A: Unterstützt</td> 
  </tr> 
  <tr> 
   <td>Microsoft SQL Server 2014</td> 
   <td>Forms-Datenbank</td> 
   <td>R: Eingeschränkte Unterstützung (4)</td> 
  </tr> 
  <tr> 
   <td><strong>Apache Lucene (Schnellstart integriert)</strong></td> 
   <td>Suchdienst</td> 
   <td>A: Unterstützt</td> 
  </tr> 
  <tr> 
   <td>Apache Solr</td> 
   <td>Suchdienst</td> 
   <td>A: Unterstützt</td> 
  </tr> 
 </tbody> 
</table>

1. „Dateisystem“ umfasst den POSIX-konformen Blockspeicher. Dazu gehört auch die Netzwerkspeichertechnologie. Beachten Sie, dass die Leistung des Dateisystems variieren und die Gesamtleistung beeinflussen kann. Es wird empfohlen, AEM in Kombination mit dem Netzwerk-/Remote-Dateisystem zu laden und zu testen.
1. MongoDB Sharding wird in AEM nicht unterstützt.
1. Nur MongoDB Storage Engine WiredTiger wird unterstützt.
1. Wird für AEM Forms nicht unterstützt.
1. MongoDB Enterprise 3.6 wird ab AEM Version 6.4.2.0 unterstützt.
1. Die Unterstützung für MongoDB 3.4 hat das Ende des Lebenszyklus (End of Life, EOL) erreicht, während MongoDB 3.6 voraussichtlich am 30. April 2021 die EOL erreichen wird. Bitte beachten Sie, dass Adobe künftig nur noch AEM produktbezogenen Fragen unterstützt.

>[!NOTE]
>
>Weitere Informationen zur Funktion von AEM Communities finden Sie unter [Bereitstellen von Communities](/help/communities/deploy-communities.md).

>[!NOTE]
>
>MongoDB ist eine Drittanbietersoftware und nicht im AEM-Lizenzierungspaket enthalten. Weitere Informationen finden Sie auf der Seite zur [MongoDB-Lizenzierungsrichtlinie](https://www.mongodb.org/about/licensing/).
>
>Um Ihre AEM-Bereitstellung mit MongoDB optimal nutzen zu können, empfiehlt Adobe die Lizenzierung der MongoDB Enterprise-Version, um professionellen Support zu erhalten. Weitere Informationen finden Sie unter [Empfohlene Implementierungen](/help/sites-deploying/recommended-deploys.md#prerequisites-and-recommendations-when-deploying-aem-with-mongomk).
>
>Die Lizenz umfasst eine standardmäßige Replikatgruppe. Diese besteht aus einer primären und zwei sekundären Instanzen, die für die Autoren- oder Veröffentlichungsbereitstellungen verwendet werden können.
>
>Wenn Sie sowohl Autor als auch Veröffentlichung auf MongoDB ausführen möchten, müssen zwei separate Lizenzen erworben werden.
>
>Die Adobe-Kundenunterstützung unterstützt Sie bei bestimmten Problemen, die mit der Verwendung von MongoDB mit AEM in Zusammenhang stehen.
>
>Weitere Informationen finden Sie auf der Seite für [MongoDB für Adobe Experience Manager](https://www.mongodb.com/lp/contact/mongodb-adobe-experience-manager).

>[!NOTE]
>
>Unterstützte relationale Datenbanken wie oben aufgeführt sind Software von Drittanbietern und sind nicht im AEM-Lizenzierungspaket enthalten.
>
>Um AEM 6.4 mit einer unterstützten relationalen Datenbank ausführen zu können, ist ein separater Supportvertrag mit einem Datenbankanbieter erforderlich. Die Adobe-Kundenunterstützung unterstützt Sie beim Qualifizieren von Problemen, die mit der Verwendung von relationalen Datenbanken mit AEM 6.4 in Zusammenhang stehen.
>
>**Bitte beachten Sie, dass die meisten relationalen Datenbanken derzeit in Level-R auf AEM 6.4 unterstützt werden, was mit Supportkriterien und einem Supportprogramm, wie in der Beschreibung zu Level-R angegeben, einhergeht.**

### Servlet-Engines/Anwendungs-Server {#servlet-engines-application-servers}

Adobe Experience Manager kann entweder als eigenständiger Server (die Schnellstart-JAR-Datei) oder als Webanwendung auf einem Drittanbieter-Anwendungsserver (die WAR-Datei) ausgeführt werden.

Die erforderliche Mindestversion der Servlet-API ist Servlet 3.1, jedoch unter Servlet 4.0.

| Plattform | Unterstützungsebene |
|---|---|
| **Integrierte Schnellstart-Servlet-Engine (Jetty 9.3)** | A: Unterstützt |
| Oracle WebLogic Server 12.2 (12cR2) | A: Unterstützt |
| Continuous Delivery für IBM WebSphere Application Server (LibertyProfile) mit Web Profile 7.0 und IBM JRE 1.8 | A: Unterstützt |
| IBM WebSphere Application Server 9.0 | A: Unterstützt |
| Apache Tomcat 8.5.x | A: Unterstützt |
| JBoss EAP 7.1.0 mit JBoss Application Server | A: Unterstützt (1) |
| JBoss EAP 7.0.0 mit JBoss Application Server | A: Unterstützt |

1. Wird für AEM Forms nicht unterstützt.

### Server-Betriebssysteme {#server-operating-systems}

Adobe Experience Manager funktioniert mit den folgenden Serverplattformen:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Plattform</strong></td> 
   <td><strong>Unterstützungsebene</strong></td> 
  </tr> 
  <tr> 
   <td><strong>Linux, basierend auf der Red Hat-Distribution</strong></td> 
   <td>A: Unterstützt (1)</td> 
  </tr> 
  <tr> 
   <td>Linux, auf Basis der Debian-Distribution einschl. Ubuntu</td> 
   <td>A: Unterstützt (4)</td> 
  </tr> 
  <tr> 
   <td>Linux, auf Basis der SUSE-Distribution</td> 
   <td>A: Unterstützt</td> 
  </tr> 
  <tr> 
   <td>Microsoft Windows Server 2016</td> 
   <td>A: Unterstützt</td> 
  </tr> 
  <tr> 
   <td>Microsoft Windows Server 2012 R2</td> 
   <td>A: Unterstützt</td> 
  </tr> 
  <tr> 
   <td>Oracle Solaris 11</td> 
   <td>A: Unterstützt mit Einschränkungen (3,5,7)<br /> R: Eingeschränkte Unterstützung für neue Verträge</td> 
  </tr> 
  <tr> 
   <td>IBM AIX 7.2</td> 
   <td>A: Unterstützt mit Einschränkungen (2,5,7)<br /> R: Eingeschränkte Unterstützung für neue Verträge</td> 
  </tr> 
 </tbody> 
</table>

1. Die Linux-Kernel 2.6, 3.x und 4.x umfassen Ableitungen aus Red Hat, einschließlich Red Hat Enterprise Linux, CentOS, Oracle Linux und Amazon Linux. AEM Forms-Add-On-Funktionen werden nur auf CentOS 7 und Red Hat Enterprise Linux 7 unterstützt.
1. AEM Assets: Siehe Abschnitt . [Unterstützung für XMP Zurückschreiben von Metadaten](#requirements-for-aem-assets-xmp-metadata-write-back)
1. AEM Assets: Dynamic Media Imaging wird nicht unterstützt. Dynamic Media Video wird unterstützt.
1. AEM Forms wird nur auf Ubuntu 16.04 LTS unterstützt.
1. AEM Assets: Keine Unterstützung für [Rohdateiumwandlung](/help/assets/camera-raw.md)
1. AEM Forms: Keine Unterstützung für Produktionsumgebungen
1. AEM Assets: Keine Unterstützung für [Enhanced PDF Rasterizer](/help/assets/aem-pdf-rasterizer.md)
1. AEM Forms: Nicht unterstützt

### Virtuelle und Cloud-Computing-Umgebungen {#virtual-cloud-computing-environments}

Adobe Experience Manager wird in einer virtuellen Maschine in Cloud-Computing-Umgebungen wie Microsoft Azure und Amazon Web Services (AWS) unterstützt, wobei die auf dieser Seite aufgeführten technischen Anforderungen sowie die standardmäßigen Supportbedingungen von Adobe eingehalten werden.

Adobe empfiehlt die Verwendung von Adobe Managed Services zur Bereitstellung von AEM auf Azure oder AWS. Adobe Managed Services liefert die Erfahrung und Kenntnisse, die Experten zur Bereitstellung und Ausführung von AEM in diesen Cloud-Computing-Umgebungen benötigen. Sehen Sie sich bitte unsere [Zusätzliche Dokumentation zu Adobe Managed Services](https://www.adobe.com/marketing-cloud/enterprise-content-management/managed-services-cloud-platform.html?aemClk=t).

In allen anderen Fällen der Bereitstellung von AEM auf Azure oder AWS oder einer anderen Cloud-Computing-Umgebung beschränkt sich Unterstützung von Adobe auf die virtuelle Rechenumgebung in Übereinstimmung mit den auf dieser Seite aufgeführten technischen Spezifikationen. Jedes gemeldete Problem, das im Zusammenhang mit der AEM in einer dieser Cloud-Umgebungen auftritt, muss unabhängig von jedem Cloud-Service reproduzierbar sein, der für die Cloud-Computing-Umgebung spezifisch ist, es sei denn, der Cloud-Service wird speziell im Rahmen der auf dieser Seite aufgelisteten technischen Anforderungen unterstützt, z. B. Azure Blob Storage oder AWS S3.

Für Empfehlungen zur Bereitstellung von AEM auf Azure oder AWS außerhalb von Adobe Managed Services empfehlen wir dringend, direkt mit dem Cloud-Anbieter oder Adobe-Partnern zusammenzuarbeiten, die die Implementierung von AEM in der von Ihnen ausgewählten Cloud-Umgebung unterstützen. Der ausgewählte Cloud-Anbieter oder -Partner ist für die Größenspezifikationen, das Design und die Implementierung der Architektur verantwortlich, um Ihre spezifischen Anforderungen an Leistung, Auslastung, Skalierbarkeit und Sicherheit zu erfüllen.

### Dispatcher-Plattformen (Web-Server) {#dispatcher-platforms-web-servers}

Beim Dispatcher handelt es sich um eine Zwischenspeicherungs- und Lastenausgleichskomponente. [Laden Sie die neueste Dispatcher-Version herunter](https://helpx.adobe.com/experience-manager/dispatcher/release-notes.html). Für Experience Manager 6.4 ist die Dispatcher-Version 4.3.1 oder höher erforderlich.

Die folgenden Web-Server werden für die Verwendung mit der Dispatcher-Version 4.3.1 unterstützt:

| Plattform | Unterstützungsebene |
|---|---|
| **Apache httpd 2.4.x** (siehe auch 1,2 unten) | A: Unterstützt |
| Microsoft IIS 10 (Internet Information Server) | A: Unterstützt |
| Microsoft IIS 8.5 (Internet Information Server) | A: Unterstützt |

1. Auf Grundlage des Apache-httpd-Quell-Codes erstellte Webserver verfügen über dieselbe Unterstützungsebene wie die Version von httpd, auf der sie basiert. Im Zweifelsfall bitten Sie um Adobe zur Bestätigung der Unterstützungsebene für das jeweilige Serverprodukt. Folgende Fälle:

   1. Der HTTP-Server wurde nur mit offiziellen Apache-Quellverteilungen erstellt, oder
   1. Der HTTP-Server wurde als Teil des Betriebssystems bereitgestellt, auf dem er ausgeführt wird. Beispiele: IBM HTTP Server, Oracle HTTP Server

1. Der Dispatcher ist nicht für Apache 2.4.x für Windows-Betriebssysteme verfügbar.

## Unterstützte Client-Plattformen {#supported-client-platforms}

### Unterstützte Browser für die Authoring-Benutzeroberfläche {#supported-browsers-for-authoring-user-interface}

Die Adobe Experience Manager-Benutzeroberfläche funktioniert mit den folgenden Client-Plattformen. Alle Browser werden mit dem Standardsatz von Plug-ins und Add-ons getestet.

Die AEM-Benutzeroberfläche ist für größere Bildschirme (normalerweise Notebooks und Desktop-Computer) und den Tablet-Formfaktor (z. B. Apple iPad oder Microsoft Surface) optimiert. Der Telefon-Formfaktor wird nicht unterstützt.

>[!NOTE]
>
>**Unterstützung für Browser mit schnellen Versionszyklen:**
>
>Die Versionen von Mozilla Firefox, Google Chrome und Microsoft Edge werden alle paar Monate aktualisiert. Adobe setzt sich dafür ein, Aktualisierungen für Adobe Experience Manager bereitzustellen, um die unten beschriebene Unterstützungsebene mit den kommenden Versionen dieser Browser beizubehalten.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Browser</strong></td> 
   <td><strong>Unterstützung für Benutzeroberfläche<br /> </strong></td> 
   <td><strong>Unterstützung für klassische Benutzeroberfläche</strong></td> 
  </tr> 
  <tr> 
   <td><strong>Google Chrome (Evergreen)</strong></td> 
   <td>A: Unterstützt</td> 
   <td>A: Unterstützt</td> 
  </tr> 
  <tr> 
   <td>Microsoft Edge (Evergreen)</td> 
   <td>A: Unterstützt</td> 
   <td>A: Unterstützt</td> 
  </tr> 
  <tr> 
   <td>Microsoft Internet Explorer 11</td> 
   <td>A: Unterstützt</td> 
   <td>A: Unterstützt</td> 
  </tr> 
  <tr> 
   <td>Mozilla Firefox (Evergreen)</td> 
   <td>A: Unterstützt</td> 
   <td>A: Unterstützt</td> 
  </tr> 
  <tr> 
   <td>Letztes ESR von Mozilla Firefox [1]</td> 
   <td>A: Unterstützt</td> 
   <td>A: Unterstützt</td> 
  </tr> 
  <tr> 
   <td>Apple Safari 12.x auf macOS</td> 
   <td>A: Unterstützt</td> 
   <td>A: Unterstützt</td> 
  </tr> 
  <tr> 
   <td>Apple Safari 11.x auf macOS</td> 
   <td>A: Unterstützt</td> 
   <td>A: Unterstützt</td> 
  </tr> 
  <tr> 
   <td>Apple Safari 10.x auf macOS</td> 
   <td>A: Unterstützt</td> 
   <td>A: Unterstützt</td> 
  </tr> 
  <tr> 
   <td>Apple Safari auf iOS 12.x</td> 
   <td>A: Unterstützt [2]</td> 
   <td>Z: Nicht unterstützt</td> 
  </tr> 
  <tr> 
   <td>Apple Safari auf iOS 11.x</td> 
   <td>A: Unterstützt [2]</td> 
   <td>Z: Nicht unterstützt</td> 
  </tr> 
  <tr> 
   <td>Apple Safari auf iOS 10.3</td> 
   <td>A: Unterstützt [2]</td> 
   <td>Z: Nicht unterstützt</td> 
  </tr> 
 </tbody> 
</table>

1. Version mit erweiterter Unterstützung von Firefox [Weitere Informationen dazu finden Sie auf mozilla.org](https://www.mozilla.org/de-DE/firefox/organizations/faq/)
1. Unterstützung für Apple iPad

### Unterstützte Browser für Websites {#supported-browsers-for-websites}

Im Allgemeinen hängt die Browser-Unterstützung für von AEM Sites gerenderte Websites von der Implementierung von Seitenvorlagen, Designs und der Komponentenausgabe von AEM ab und unterliegt daher der Kontrolle der Seite, die diese Teile implementiert.

### WebDAV-Clients {#webdav-clients}

**Microsoft Windows 7+**

Um eine erfolgreiche Verbindung mit Microsoft Windows 7+ zu einer AEM-Instanz herzustellen, die nicht mit SSL gesichert ist, muss unter Windows die grundlegende Authentifizierung über ein ungesichertes Netzwerk aktiviert sein. Dies erfordert eine Änderung in der Windows-Registrierung des WebClient:

1. Suchen Sie den Registrierungsunterschlüssel:

   * HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WebClient\Parameters

1. Fügen Sie diesem Unterschlüssel den Registrierungseintrag „BasicAuthLevel“ mit dem Wert 2 oder mehr hinzu.

Siehe [Microsoft-Support KB 841215](https://support.microsoft.com/default.aspx/kb/841215).

Informationen zur Verbesserung der Reaktionsfähigkeit des WebDav-Clients unter Windows finden Sie unter [Microsoft-Support KB 2445570](https://support.microsoft.com/kb/2445570)

## Zusätzliche Hinweise zu Platform {#additional-platform-notes}

Dieser Abschnitt enthält spezielle Hinweise und detailliertere Informationen zum Ausführen von Adobe Experience Manager und seinen Add-ons.

### IPv4 und IPv6 {#ipv-and-ipv}

Alle Elemente von Adobe Experience Manager (Instance, Dispatcher) können sowohl in IPv4- als auch in IPv6-Netzwerken installiert werden.

Der Betrieb ist nahtlos, da keine spezielle Konfiguration erforderlich ist. Sie können bei Bedarf einfach eine IP-Adresse in dem für Ihren Netzwerktyp geeigneten Format angeben.

Wenn eine IP-Adresse angegeben werden muss, können Sie (je nach Bedarf) aus den folgenden Optionen auswählen:

* eine IPv6-Adresse

   zum Beispiel `https://[ab12::34c5:6d7:8e90:1234]:4502`

* eine IPv4-Adresse

   zum Beispiel `https://123.1.1.4:4502`

* einen Server-Namen

   zum Beispiel `https://www.yourserver.com:4502`

* der Standardfall von `localhost` wird für IPv4- und IPv6-Netzwerkinstallationen interpretiert

   zum Beispiel `http://localhost:4502`

### Voraussetzungen für das AEM Dynamic Media-Add-on {#requirements-for-aem-dynamic-media-add-on}

AEM Dynamic Media ist standardmäßig deaktiviert. Siehe [Aktivieren von Dynamic Media](/help/assets/config-dynamic.md#enabling-dynamic-media).

Wenn Dynamic Media aktiviert ist, gelten die folgenden zusätzlichen Systemanforderungen:
>[!NOTE]
>
>Die folgenden Systemanforderungen gelten **_only_** wenn Sie den Hybridmodus von Dynamic Media verwenden; Der Hybridmodus von Dynamic Media verfügt über einen eingebetteten Bildserver, der nur für bestimmte Betriebssysteme zertifiziert ist.
>
>Für Dynamic Media-Kunden, die den Modus „Dynamic Media - Scene7“ ausführen (d. h. Ausführungsmodus **dynamicmedia_scene7**) gelten keine weiteren Systemanforderungen. Es gelten dieselben Systemanforderungen wie für AEM. Die Architektur des Dynamic Media-Scene7-Modus verwendet den Cloud-basierten Bilddienst, nicht den in AEM eingebetteten Dienst.

#### Hardware {#hardware}

Die folgenden Hardwareanforderungen gelten für Linux- und Windows-Betriebssysteme:

* Intel Xeon- oder AMD Opteron-CPU mit mindestens 4 Kernen
* Mindestens 16 GB RAM

#### Linux {#linux}

Die Verwendung von Dynamic Media unter Linux erfordert die folgenden Voraussetzungen:

* RedHat Enterprise 7 oder CentOS 7 und höher mit den neuesten Fix-Patches
* 64-Bit-Betriebssystem
* Swapping deaktiviert (empfohlen)
* SELinux deaktiviert (siehe folgenden Hinweis)

>[!NOTE]
>
>Wenn das Gebietsschema so festgelegt ist, dass LC_CTYPE nicht gleich en_US.UTF-8 ist, funktioniert das dynamische Medium nicht. Geben Sie bei der Eingabeaufforderung den Wert „locale“ ein, um den Wert zu ermitteln. Wenn er nicht darauf festgelegt ist, legen Sie die Umgebungsvariable LC_CTYPE auf die leere Zeichenfolge fest, indem Sie „export LC_CTYPE=“ eingeben, bevor Sie AEM ausführen.

>[!NOTE]
>
>**Deaktivieren von SELinux**: Die Bereitstellung von Bildern funktioniert nicht, wenn SELinux aktiviert ist. Diese Option ist standardmäßig aktiviert. Um dieses Problem zu beheben, bearbeiten Sie die Datei **/etc/selinux/config** und ändern Sie den SELinux-Wert von:
>
>`SELINUX=enforcing` in  `SELINUX=disabled`

>[!NOTE]
>
>**NUMA-Architektur:** Systeme mit Prozessoren mit AMD64 und Intel EM64T sind normalerweise als NUMA-Plattformen (Non-Uniform Memory Architecture) konfiguriert, was bedeutet, dass der Kernel beim Starten mehrere Speicherknoten erstellt, anstatt einen einzelnen Speicherknoten zu erstellen.
>
>Das Konstrukt mit mehreren Knoten kann zu einer Speichererschöpfung auf einem oder mehreren Knoten führen, bevor andere Knoten erschöpft sind. Wenn die Speichererschöpfung eintritt, kann der Kernel Prozesse beenden (z. B. den Bild- oder Platform-Server), selbst wenn verfügbarer Speicher vorhanden ist.
>
>Daher empfiehlt Adobe, dass Sie NUMA bei der Ausführung eines solchen Systems mit der Boot-Option **numa=off** ausschalten, um zu vermeiden, dass der Kernel diese Prozesse beendet.

>[!NOTE]
>
>**Hostname des Servers muss auflösbar sein:** Stellen Sie sicher, dass der Hostname des Servers in eine IP-Adresse aufgelöst werden kann. Wenn dies nicht möglich ist, fügen Sie den vollständig qualifizierten Hostnamen und die IP-Adresse zu **/etc/hosts**:
>
>`<ip address> <fully qualified hostname>`

#### Windows {#windows}

* Microsoft Windows Server 2016
* Swap-Speicherplatz, der mindestens der doppelten Menge des physischen Speichers (RAM) entspricht

Um Dynamic Media unter Windows zu verwenden, müssen die Redistributables von Microsoft Visual Studio 2010, 2013 und 2015 für x64 und x86 installiert sein.

x64

* Die Redistributable Microsoft Visual Studio 2010 finden Sie unter [https://www.microsoft.com/en-us/download/details.aspx?id=13523](https://www.microsoft.com/de-de/download/details.aspx?id=13523)
* Die Redistributable Microsoft Visual Studio 2013 finden Sie unter [https://www.microsoft.com/en-us/download/details.aspx?id=40784](https://www.microsoft.com/de-de/download/details.aspx?id=40784)
* Verteilbare Microsoft Visual Studio 2015-Dateien finden Sie unter [https://www.microsoft.com/en-us/download/details.aspx?id=48145](https://www.microsoft.com/de-de/download/details.aspx?id=48145)

x86

* Die Redistributable Microsoft Visual Studio 2010 finden Sie unter [https://www.microsoft.com/en-in/download/details.aspx?id=5555](https://www.microsoft.com/en-in/download/details.aspx?id=5555)
* Die Redistributable Microsoft Visual Studio 2013 finden Sie unter [https://www.microsoft.com/en-in/download/details.aspx?id=40769](https://www.microsoft.com/en-in/download/details.aspx?id=40769)
* Verteilbare Microsoft Visual Studio 2015-Dateien finden Sie unter [https://www.microsoft.com/en-us/download/details.aspx?id=52685](https://www.microsoft.com/de-de/download/details.aspx?id=52685)

#### macOS {#macos}

* 10.9.x und höher
* Wird nur für Test- und Demozwecke unterstützt

### Anforderungen für AEM Forms PDF Generator {#requirements-for-aem-forms-pdf-generator}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>Produkt</strong></p> </th> 
   <th><p><strong>Unterstützte Formate für die Konvertierung ins PDF-Format </strong></p> </th> 
  </tr> 
  <tr> 
   <td><p><a href="https://helpx.adobe.com/de/acrobat/release-note/release-notes-acrobat-reader.html">Acrobat 2017 Classic Track</a></p> </td> 
   <td><p>XPS, Bildformate (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPF, JPX, JP2, J2K, J2C, JPC), HTML, HTM, DWG, DXF und DWF</p> </td> 
  </tr> 
  <tr> 
   <td>Microsoft® Project 2016</td> 
   <td>MPP</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Publisher 2016</td> 
   <td>PUB</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Office Visio 2016</td> 
   <td>VSD</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Office 2016</td> 
   <td>DOC, DOCX, XLS, XLSX, PPT, PPTX, RTF und TXT</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Office 2013</td> 
   <td>DOC, DOCX, XLS, XLSX, PPT, PPTX, RTF und TXT</td> 
  </tr> 
  <tr> 
   <td>Corel WordPerfect X7</td> 
   <td>WP, WPD<br /> </td> 
  </tr> 
  <tr> 
   <td>OpenOffice 4.1.2</td> 
   <td>ODT, ODP, ODS, ODG, ODF, SXW, SXI, SXC, SXD, XLS, XLSX, DOC, DOCX, PPT, PPTX, Bildformate (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPF, JPX, JP2, J2K, J2C, JPC), HTML, HTM, RTF und TXT</td> 
  </tr> 
  <tr> 
   <td><p>OpenOffice 3.4</p> </td> 
   <td><p>ODT, ODP, ODS, ODG, ODF, SXW, SXI, SXC, SXD, XLS, XLSX, DOC, DOCX, PPT, PPTX, Bildformate (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPF, JPX, JP2, J2K, J2C, JPC), HTML, HTM, RTF und TXT</p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>PDF Generator unterstützt nur englische, französische, deutsche und japanische Versionen der unterstützten Betriebssysteme und Anwendungen.
>
>Zusätzlich gilt Folgendes:
>
>* PDF Generator erfordert [Acrobat 2017 Klassische Track-Version 17.011.30078 oder höher](https://helpx.adobe.com/de/acrobat/release-note/release-notes-acrobat-reader.html) , um die Konvertierung durchzuführen.
>* AEM Forms unterstützt nur 32-Bit-Editionen der unterstützten Software.
>* Die OCR-PDF- (durchsuchbare PDF), Optimize PDF- und Export PDF-Funktionen werden nur unter Microsoft Windows unterstützt.
>* Der HTML2PDF-Dienst wird unter AIX nicht mehr unterstützt.
>* PDF Generator-Konvertierungen für OpenOffice werden nur unter Windows, Linux und Solaris unterstützt.
>* Die Funktionen von OCR PDF, PDF optimieren und PDF erstellen werden nur unter Windows unterstützt.
>* Eine Version von Acrobat ist im Lieferumfang von AEM Forms enthalten, um die PDF Generator-Funktionalität zu aktivieren. Die gebündelte Version sollte während der Laufzeit der AEM Forms-Lizenz zur Verwendung mit AEM Forms PDF Generator nur programmatisch mit AEM Forms zugänglich sein. Weitere Informationen finden Sie in der AEM Forms-Produktbeschreibung für Ihre Bereitstellung ([On-Premise](https://helpx.adobe.com/de/legal/product-descriptions/adobe-experience-manager-on-premise.html) oder [Managed Services](https://helpx.adobe.com/de/legal/product-descriptions/adobe-experience-manager-managed-services.html))”
>


### Anforderungen für AEM Forms Designer {#requirements-for-aem-forms-designer}

* Microsoft® Windows® 2012 Server R2, Microsoft® Windows® 2016 Server, Microsoft® Windows® 2019 Server, Microsoft® Windows® 10
* Prozessor mit 1 GHz oder höher mit Unterstützung für PAE, NX und SSE2.
* 1 GB RAM für 32-Bit-Betriebssysteme oder 2 GB RAM für 64-Bit-Betriebssysteme
* 16 GB Speicherplatz für 32-Bit-Betriebssysteme oder 20 GB Speicherplatz für 64-Bit-Betriebssysteme
* Grafikspeicher – 128 MB GPU (256 MB empfohlen)
* 2,35 GB verfügbarer Festplattenspeicher
* Bildschirmauflösung 1024 x 768 Pixel oder höher
* Beschleuniger für Video-Hardware (optional)
* Acrobat Pro DC, Acrobat Standard DC oder Adobe Acrobat Reader DC
* Administratorrechte für die Installation von Designer

### Anforderungen für das Zurückschreiben von XMP-Metadaten der AEM Assets {#requirements-for-aem-assets-xmp-metadata-write-back}

Das Zurückschreiben von XMP-Daten wird für die folgenden Plattformen und Dateiformate unterstützt und aktiviert:

**Betriebssysteme**

* Linux (32-Bit, 32-Bit-Anwendungsunterstützung auf 64-Bit-Systemen erforderlich). Schrittweise Anleitungen zur Installation von 32-Bit-Clientbibliotheken finden Sie unter [Aktivieren von XMP-Extraktion und -Writeback unter RedHat Linux (64 Bit)](https://helpx.adobe.com/de/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html).

* Windows Server
* Oracle Solaris
* macOS X (64 Bit)

**Dateiformate**

* JPEG
* PNG
* TIFF
* PDF
* INDD
* AI
* EPS

### Voraussetzungen für AEM Screens Player {#requirements-for-aem-screens-player}

AEM Screens Player Version 3.3.x unterstützt folgende Betriebssysteme:

* Microsoft Windows 10 Enterprise LTSB
* Google Chrome OS 62+
* Google Android 5.1.1 mit aktualisierter Android System WebView Version 52+
* Apple iOS 10.3+
* Apple macOS 10.12+
