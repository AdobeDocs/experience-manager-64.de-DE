---
title: Unterstützte Plattformen für AEM Forms on JEE
seo-title: Supported Platforms for AEM Forms on JEE
description: Liste der für die Installation von AEM Forms on JEE erforderlichen und unterstützten Infrastrukturkomponenten
seo-description: List of infrastructure components required and supported for installing AEM Forms on JEE
uuid: 22f05fd4-f9fc-423e-8a86-1e75df4b2b44
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: 1b9f8d98-e7e8-4b9b-a0df-52ccba324da3
role: Admin
exl-id: 6609c625-0591-42fd-910b-c7c65d52c5f1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3367'
ht-degree: 52%

---

# Unterstützte Plattformen für AEM Forms on JEE {#supported-platforms-for-aem-forms-on-jee}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Unterstützte Plattformen {#supported-platforms}

### Unterstützungsebenen {#support-levels}

AEM Forms on JEE-Server kann mit einer beliebigen Kombination von unterstützten Betriebssystemen, Anwendungsservern, Datenbanken, Datenbanktreibern, JDK-, LDAP-Servern und E-Mail-Servern eingerichtet werden.

In diesem Dokument werden die unterstützten Client- und Serverplattformen für AEM Forms on JEE aufgeführt. Adobe bietet verschiedene Unterstützungsebenen an, die für empfohlene und andere Konfigurationen gelten. Das Dokument listet auch andere unterstützte Software und deren Versionen, Ausnahmen, Patch-Definitionen und Richtlinien zur Unterstützung von Software-Patches von Drittanbietern auf.

>[!NOTE]
>
>* Eine vollständige Liste der Ausnahmen für unterstützte Serverplattformen finden Sie unter [Ausnahmen für unterstützte Serverplattformen](#exceptions-to-supported-server-platforms).
>* AEM Forms on JEE unterstützt nur englische, französische, deutsche und japanische Versionen der unterstützten Betriebssysteme und Anwendungen.
>


### Empfohlene Konfigurationen {#recommendedconfigurations}

Adobe empfiehlt diese Konfigurationen und bietet vollständige oder eingeschränkte Unterstützung im Rahmen des Standard-Software-Wartungsvertrags:

<table> 
 <tbody> 
  <tr> 
   <th>Unterstützungsebene</th> 
   <th>Beschreibung</th> 
  </tr> 
  <tr> 
   <td>A: Unterstützt<br /> </td> 
   <td>Adobe bietet vollständige Unterstützung und Wartung für diese Konfiguration. Diese Konfiguration wird über den Qualitätssicherungsvorgang von Adobe abgedeckt.</td> 
  </tr> 
  <tr> 
   <td>R: Eingeschränkte Unterstützung </td> 
   <td>Adobe unterstützt diese Konfiguration vollständig, wenn bestimmte Voraussetzungen erfüllt sind. Wenden Sie sich an den Support von Adobe Enterprise, um mehr über die Voraussetzungen zu erfahren und um Support anzufordern.</td> 
  </tr> 
  <tr> 
   <td>L: Eingeschränkte Unterstützung</td> 
   <td>Adobe bietet vollständige Unterstützung und Wartung für diese Konfigurationen, sofern bestimmte Voraussetzungen erfüllt sind. Nicht alle Funktionen sind in der Konfiguration verfügbar. Wenden Sie sich an den Support von Adobe Enterprise, um mehr über die Voraussetzungen zu erfahren und um Support anzufordern.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Nicht unterstützte Konfigurationen {#unsupported-configurations}

| Unterstützungsebene | Beschreibung |
|---|---|
| E: Funktionsfähigkeit wird erwartet | Es wird erwartet, dass die Konfiguration funktioniert, und es wird nichts Gegenteiliges berichtet. |
| Z: Nicht unterstützt | Die Konfiguration wird nicht unterstützt. Adobe macht keine Angaben dazu, ob die Konfiguration funktioniert, und unterstützt sie nicht. |

### Java Virtual Machines (JVM) {#java-virtual-machines-jvm}

Adobe Experience Manager Forms erfordert eine Java Virtual Machine, die von der Java Development Kit-Distribution (JDK) bereitgestellt wird. Adobe Experience Manager funktioniert mit den folgenden Versionen von Java Virtual Machine:

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>Plattform</strong></p> </th> 
   <th><p><strong>Unterstützungsebene</strong></p> </th> 
   <th><p><strong>Unterstützte Patch-Definitionen</strong></p> </th> 
  </tr> 
  <tr> 
   <td><p>Oracle Java™ SE 8 (64 Bit)</p> </td> 
   <td><p>A: Unterstützt</p> </td> 
   <td><p>Nebenversionen und Updates</p> </td> 
  </tr> 
  <tr> 
   <td>IBM® J9 Virtual Machine (Build 2.8, JRE 1.8.0)</td> 
   <td>A: Unterstützt</td> 
   <td>Nebenversionen und Updates</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>* AEM Forms on JEE wird nur von 64-Bit-JVMs für Produktionsumgebungen unterstützt.
>* Es wird empfohlen, die Sicherheitsbulletins vom Java-Anbieter zu verfolgen, um den Schutz und die Sicherheit von Produktionsumgebungen sicherzustellen und die neuesten Java-Aktualisierungen zu installieren.
>


### Datenbanken und CRX-Persistenz {#databases-and-crx-persistence}

#### AEM Persistenzunterstützung {#aem-persistence-support}

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Plattform</strong></p> </td> 
   <td><p><strong> Beschreibung</strong></p> </td> 
   <td><p><strong>Unterstützungsebene</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Dateisystem</p> </td> 
   <td><p>Repository Microkernel (TAR MK-Dateien)</p> </td> 
   <td><p>Unterstützt</p> </td> 
  </tr> 
  <tr> 
   <td><p>MongoDB Enterprise 3.4</p> </td> 
   <td><p>Repository-Mikrokernel</p> </td> 
   <td><p>Unterstützt</p> </td> 
  </tr> 
  <tr> 
   <td>IBM DB2 11.1</td> 
   <td>Repository-Mikrokernel</td> 
   <td>Unterstützt</td> 
  </tr> 
  <tr> 
   <td><p>Oracle-Datenbank 12c Version 1</p> </td> 
   <td><p>Repository-Mikrokernel</p> </td> 
   <td><p>Unterstützt</p> </td> 
  </tr> 
  <tr> 
   <td><p>Microsoft SQL Server 2016</p> </td> 
   <td><p>Repository-Mikrokernel</p> </td> 
   <td><p>Unterstützt</p> </td> 
  </tr> 
 </tbody> 
</table>

* MongoDB ist eine Drittanbietersoftware und nicht im AEM-Lizenzierungspaket enthalten. Weitere Informationen finden Sie auf der Seite zur [MongoDB-Lizenzierungsrichtlinie](https://www.mongodb.org/about/licensing/).

* Um das Beste aus Ihrer AEM-Bereitstellung zu erhalten, empfiehlt Adobe die Lizenzierung der MongoDB Enterprise-Version, um professionellen Support zu erhalten.
* Die Adobe-Kundenunterstützung unterstützt Sie bei bestimmten Problemen, die mit der Verwendung von MongoDB mit AEM in Zusammenhang stehen. Weitere Informationen finden Sie auf der Seite für [MongoDB für Adobe Experience Manager](https://www.mongodb.com/lp/contact/mongodb-adobe-experience-manager).
* „Dateisystem“ umfasst den POSIX-konformen Blockspeicher. Dazu gehört auch die Netzwerkspeichertechnologie. Beachten Sie, dass die Leistung des Dateisystems variieren und die Gesamtleistung beeinflussen kann. Es wird empfohlen, AEM in Kombination mit dem Netzwerk-/Remote-Dateisystem zu laden und zu testen.
* Nur MongoDB Storage Engine WiredTiger wird unterstützt.
* MongoDB Sharding wird in AEM nicht unterstützt.
* AEM Forms on JEE unterstützt keine MySQL für RDBMK-Persistenz.
* Das Document Security-Modul verwendet kein Content Repository. Dies bedeutet, dass Sie, wenn Sie nur Document Security verwenden und nicht HTML Workspace, HTML5-Formulare oder adaptive Formulare verwenden möchten, Content Repository nicht installieren.
* AEM Forms on JEE unterstützt die Oracle-Multitenant-Architektur.

#### Unterstützung von DATENBANKEN {#database-support}

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Plattform</strong></p> </td> 
   <td><p><strong> Beschreibung</strong></p> </td> 
   <td><p><strong>Unterstützungsebene AEM 6.4</strong></p> </td> 
   <td><p><strong>Unterstützungsebene für AEM Forms 6.4 on JEE</strong></p> </td> 
  </tr> 
  <tr> 
   <td>IBM DB2 11.1</td> 
   <td>Repository-Mikrokernel</td> 
   <td>Unterstützt</td> 
   <td>Unterstützt</td> 
  </tr> 
  <tr> 
   <td><p>Oracle-Datenbank 12c Version 1</p> </td> 
   <td><p>Repository-Mikrokernel</p> </td> 
   <td><p>Unterstützt</p> </td> 
   <td><p>Unterstützt </p> </td> 
  </tr> 
  <tr> 
   <td><p>MySQL 5.7.19<br /> </p> </td> 
   <td><p>Repository-Mikro-Kernel</p> </td> 
   <td><p>Funktionieren erwartet</p> </td> 
   <td><p>Unterstützt</p> </td> 
  </tr> 
  <tr> 
   <td><p>Microsoft SQL Server 2016</p> </td> 
   <td><p>Repository-Mikrokernel</p> </td> 
   <td><p>Funktionieren erwartet</p> </td> 
   <td><p>Unterstützt</p> </td> 
  </tr> 
 </tbody> 
</table>

### Datenbanktreiber {#database-drivers}

<table> 
 <tbody> 
  <tr> 
   <th>Datenbank </th> 
   <th><p><strong>Plattform</strong></p> </th> 
   <th><p><strong>Unterstützte Patch-Definitionen</strong></p> </th> 
  </tr> 
  <tr> 
   <td>MySQL</td> 
   <td><p>MySQL Connector/J 5.7</p> <p>mysql-connector-java-5.1.44-bin.jar (Version 5.1.44)</p> </td> 
   <td><p>AEM Forms on JEE-Installation im Paket enthalten</p> </td> 
  </tr> 
  <tr> 
   <td>Microsoft SQL Server<br /> </td> 
   <td><p>Microsoft® SQL Server JDBC-Treiber 6.2.1.0 (veraltet) <br /> </p> <p>sqljdbc6.jar</p> </td> 
   <td><p>AEM Forms on JEE-Installation im Paket enthalten.</p> </td> 
  </tr> 
  <tr> 
   <td>Microsoft SQL Server<br /> </td> 
   <td><p>Microsoft® SQL Server JDBC-Treiber 6.2.2.0<br /> </p> <p>sqljdbc6.jar</p> </td> 
   <td><p>Laden Sie dies von der Microsoft-Website herunter.</p> </td> 
  </tr> 
  <tr> 
   <td>Oracle</td> 
   <td><p>Oracle Database 12.1.0.2.0 JDBC-Treiber</p> <p>ojdbc7.jar (Version 12.1.0.2.0)<br /> </p> </td> 
   <td><p>AEM Forms on JEE-Installation im Paket enthalten.</p> </td> 
  </tr> 
  <tr> 
   <td>IBM DB2</td> 
   <td><p>IBM® DB2 Universal JDBC-Treiber 4.16.53 (db2jcc4.jar)</p> </td> 
   <td><p>Laden Sie den Treiber von herunter. <a href="https://www-01.ibm.com/support/docview.wss?uid=swg21363866" target="_blank">IBM-Website</a></p> </td> 
  </tr> 
 </tbody> 
</table>

### Anwendungsserver {#application-servers}

<table> 
 <tbody> 
  <tr> 
   <td><p><strong> Plattform</strong></p> </td> 
   <td><p><strong>Unterstützungsebene</strong></p> </td> 
   <td><p><strong>Unterstützte Patch-Definitionen</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Oracle WebLogic Server 12.2.1 (12c R2) <sup>[1] [2] [4] [8]</sup></p> </td> 
   <td><p>A: Unterstützt</p> </td> 
   <td><p>Service Pack und wichtige Updates</p> </td> 
  </tr> 
  <tr> 
   <td>IBM® WebSphere® Application Server 9.0 <sup>[2] [6]</sup><br /> </td> 
   <td>A: Unterstützt</td> 
   <td>Service Pack und wichtige Updates</td> 
  </tr> 
  <tr> 
   <td><p>JBoss® Enterprise Application Platform (EAP) 7.0.6 <sup>[1] [4] [5] [7] [8][11]</sup></p> </td> 
   <td><p>A: Unterstützt</p> </td> 
   <td><p>Patches und kumulative Patches  für die unterstützte EAP-Version<br /> </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>IBM® WebSphere®-Cluster werden nur in Network Deployment-Editionen unterstützt.

### Serverbetriebssysteme {#server-operating-systems}

#### Produktionsumgebungen {#production-environments}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong> Plattform</strong></p> </th> 
   <th><p><strong>Unterstützungsebene</strong></p> </th> 
   <th><p><strong>Unterstützte Patch-Definitionen</strong></p> </th> 
  </tr> 
  <tr> 
   <td>Microsoft Windows Server 2016</td> 
   <td>A: Unterstützt</td> 
   <td>Service Packs und wichtige Updates</td> 
  </tr> 
  <tr> 
   <td><p>Microsoft Windows Server 2012 R2 V6.3</p> </td> 
   <td><p>A: Unterstützt</p> </td> 
   <td><p>Service Packs und wichtige Updates</p> </td> 
  </tr> 
  <tr> 
   <td><p>Oracle Solaris™ 11 - V5.11<sup> [3] [10]</sup></p> </td> 
   <td><p>L: Limited</p> </td> 
   <td><p>Aktualisierungen und Patches</p> </td> 
  </tr> 
  <tr> 
   <td><p>Red Hat Enterprise Linux 7 (Kernel 3.x)</br><b>Hinweis:</b> <a href="https://access.redhat.com/articles/4665701">Red Hat Enterprise Linux 6</a> erreicht das Ende der Wartungsphase und wechselt zur Phase der erweiterten Unterstützung für den Lebenszyklus am 30. November 2020. Adobe empfiehlt Red Hat Enterprise Linux 7 für Upgrades und neue Installationen. Bestehende Installationen können Red Hat Enterprise Linux 6 während der Erweiterten Life Cycle Support-Phase verwenden.</p> </td> 
   <td><p>A: Unterstützt</p> </td> 
   <td><p>Nebenversionen, kumulative Updates und wichtige Updates</p> </td> 
  </tr> 
  <tr> 
   <td><p>SUSE® Linux® Enterprise Server 12</p> </td> 
   <td><p>A: Unterstützt</p> </td> 
   <td><p>Service Packs, kumulative Patches und wichtige Sicherheitsupdates</p> </td> 
  </tr> 
  <tr> 
   <td>Oracle Linux® 7 Update 3 </td> 
   <td>A: Unterstützt</td> 
   <td>Service Packs, kumulative Patches und wichtige Sicherheitsupdates</td> 
  </tr> 
  <tr> 
   <td>CentOS 7<sup> [9]</sup></td> 
   <td>A: Unterstützt</td> 
   <td>Service Packs, kumulative Patches und wichtige Sicherheitsupdates</td> 
  </tr> 
  <tr> 
   <td>IBM AIX 7.2 [10]</td> 
   <td>A: Eingeschränkte Unterstützung</td> 
   <td>Service Packs, kumulative Patches und wichtige Sicherheitsupdates</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>AEM Forms on JEE unterstützt nur 64-Bit-Betriebssysteme.

#### Virtualisierte Umgebung {#virtualized-environment}

Sie können AEM Forms on JEE auf einem physischen Computer oder in einer virtuellen Umgebung ausführen. Wenn Sie jedoch auf ein Problem mit AEM Forms in einer virtuellen Umgebung stoßen, versuchen Sie, das Problem auf einem physischen Computer zu replizieren. Wenn das Problem auf dem physischen Computer weiterhin besteht, wenden Sie sich in Hinblick auf Unterstützung an den Adobe-Support. Wenden Sie sich bei Problemen, die nicht auf dem physischen Computer repliziert werden, an Ihren Anbieter für virtuelle Umgebungen.

#### Entwicklungsumgebungen {#development-environments}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>Plattform (Basisversion)</strong></p> </th> 
   <th>Unterstützungsebene</th> 
   <th><p><strong>Unterstützte Patch-Definitionen</strong></p> </th> 
  </tr> 
  <tr> 
   <td><p>Microsoft® Windows® 10</p> </td> 
   <td>E: Funktionsfähigkeit wird erwartet</td> 
   <td><p>Service Pack und wichtige Updates</p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>* AEM Forms on JEE unterstützt nur 64-Bit-Betriebssysteme.
>* Der PDF Generator-Dienst wird unter Windows 10 nicht unterstützt.
>


### Ausnahmen für unterstützte Serverplattformen {#exceptions-to-supported-server-platforms}

Beachten Sie beim Auswählen einer Plattform für die Einrichtung Ihres AEM Forms on JEE-Servers die folgenden Ausnahmen.

1. AEM Forms on JEE unterstützt Oracle WebLogic und JBoss® nicht unter IBM® AIX®.
1. AEM Forms on JEE unterstützt Oracle WebLogic und IBM® WebSphere® mit MySQL nicht.
1. AEM Forms on JEE unterstützt nicht Oracle Solaris™ mit Intel® Architektur (nur SPARC® wird unterstützt).
1. AEM Forms on JEE unterstützt Oracle WebLogic und JBoss nicht unter SUSE Linux Enterprise Server 12. Nur IBM WebSphere wird auf SUSE Linux Enterprise Server 12 unterstützt.
1. AEM Forms on JEE unterstützt kein anderes JDK mit JBoss® als Oracle Java™ SE.
1. AEM Forms on JEE unterstützt kein anderes JDK mit IBM® WebSphere® als IBM® JDK.
1. AEM Forms on JEE unterstützt IBM® DB2 mit JBoss® nicht.
1. CRX-Repository unterstützt Persistenz des Typs TarMK, MongoDB und relationale Datenbanken (RDBMK). Sie dürfen nicht zwei verschiedene Datenbanksysteme zwischen dem Anwendungsserver und dem CRX-Repository haben. In einer AEM Forms on JEE-Umgebung können Sie MongoMK jedoch mit dem CRX-Repository und einer unterstützten relationalen Datenbank mit Anwendungsserver verwenden.
1. AEM Forms on JEE unterstützt keinen WebSphere-Anwendungsserver unter CentOS.
1. AIX- und Solaris-Betriebssysteme sind nur für Upgrade-Kunden verfügbar.
1. AEM Forms on JEE unterstützt keine rollenbasierte JBoss-Zugriffskontrolle (RBAC).

Beachten Sie außerdem die folgenden Punkte bei der Auswahl der Software für Adobe AEM Forms on JEE-Implementierungen:

* AEM Forms on JEE unterstützt Updates, Patches und Fix Packs zusätzlich zu der angegebenen Haupt- oder Nebenversion der unterstützten Software. Die Aktualisierung auf die nächste Haupt- oder Nebenversion wird jedoch nicht unterstützt, sofern nichts anderes angegeben ist.
* Clusterbasierte Installationen unterstützen keine TarMK-Persistenz. Informationen zur unterstützten Persistenz finden Sie unter [Persistenztyp für eine AEM Forms-Installation auswählen](/help/forms/using/choosing-persistence-type-for-aem-forms.md).
* AEM Forms on JEE unterstützt verschiedene Software von Drittanbietern gemäß unserer [Richtlinie zur Unterstützung von Software von Drittanbietern](#third-party-patch-support-policy).
* AEM Forms on JEE unterstützt Plattformen in Abhängigkeit der Unterstützung durch Drittanbieter. Einige Kombinationen sind möglicherweise von Drittanbietern nicht zulässig. Beispielsweise haben viele Anbieter ihre Anwendungsserver nicht für IBM® DB2 zertifiziert. Daher unterstützt AEM Forms on JEE diese Kombinationen ebenfalls nicht. Um sicherzugehen, dass Sie die unterstützten Softwareversionen auswählen, sollten Sie auch die Supportmatrix dieser Drittanbieter überprüfen.
* AEM Forms on JEE unterstützt keine TarMK Cold Standby.
* AEM Forms on JEE unterstützt kein vertikales Clustering.
* AEM Forms on JEE unterstützt keine MySQL-Datenbank in einer Clusterumgebung.
* RDBMK funktioniert nicht mit DB2-, MYSQL-, MS SQL- und Oracle-Datenbanken, wenn die Package JDBC-Module für Weblogic konfiguriert sind.

### LDAP-Server (optional) {#ldap-servers-optional}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>Produkt (Basisversion)</strong></p> </th> 
   <th><p><strong>Unterstützte Patch-Definitionen</strong></p> </th> 
  </tr> 
  <tr> 
   <td>Oracle Unified Directory (OUD) 11g Version 2</td> 
   <td>Service Packs</td> 
  </tr> 
  <tr> 
   <td>Microsoft Active Directory 2016</td> 
   <td>Maintenance Release und Fix Packs</td> 
  </tr> 
  <tr> 
   <td><p>Microsoft® Active Directory 2012</p> </td> 
   <td><p>Updates mit dem Betriebssystem</p> </td> 
  </tr> 
  <tr> 
   <td><p>Microsoft Active Directory Lightweight Directory Services 2012</p> </td> 
   <td><p>Updates mit dem Betriebssystem</p> </td> 
  </tr> 
  <tr> 
   <td><p>IBM® Tivoli Directory Server 6.4</p> </td> 
   <td><p>Feature Packs und Interim Fixes</p> </td> 
  </tr> 
  <tr> 
   <td>IBM Lotus Domino 8.5.0</td> 
   <td>Maintenance Release und Fix Packs</td> 
  </tr> 
  <tr> 
   <td>Novell eDirectory 8.8.7</td> 
   <td>Produktaktualisierungen</td> 
  </tr> 
 </tbody> 
</table>

### E-Mail-Server (optional) {#email-servers-optional}

* IBM Lotus Domino 9.0
* Microsoft Exchange 2013
* Microsoft Office 365

### Content Manager und entsprechende Connectoren {#content-managers-and-corresponding-connectors}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Produkt<br /> </strong></td> 
   <td><strong>Version</strong></td> 
  </tr> 
  <tr> 
   <td>IBM Content Manager Server</td> 
   <td>8.5 Fixpack 2<br /> </td> 
  </tr> 
  <tr> 
   <td>IBM Content Manager Client</td> 
   <td><p>Version 8.5<strong> </strong>wird unterstützt</p> </td> 
  </tr> 
  <tr> 
   <td>EMC Documentum</td> 
   <td>7.0 und 7.3</td> 
  </tr> 
  <tr> 
   <td>IBM Filenet</td> 
   <td>5.2</td> 
  </tr> 
  <tr> 
   <td>Microsoft Sharepoint</td> 
   <td>2013 und 2016<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Unterstützung für Cordova {#support-for-cordova}

AEM Forms App unterstützt jetzt Apache Cordova. Die folgenden plattformspezifischen Versionen von Cordova werden unterstützt:

* Apache Cordova 6.4.0
* Cordova iOS 4.3.0
* Cordova Android 6.0.0
* Cordova Windows 4.4.3

### Software-Support für PDF Generator {#software-support-for-pdf-generator}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>Produkt</strong></p> </th> 
   <th><p><strong>Unterstützte Formate für die Konvertierung ins PDF-Format </strong></p> </th> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/de/acrobat/release-note/release-notes-acrobat-reader.html">Acrobat 2017 Classic Track</a></td> 
   <td>XPS, Bildformate (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPF, JPX, JP2, J2K, J2C, JPC), HTML, HTM, DWG, DXF und DWF</td> 
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
   <td>WordPerfect X7</td> 
   <td>WP, WPD</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Office Visio 2013</td> 
   <td>VSD, VSDX</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Office Visio 2016</td> 
   <td>VSD, VSDX</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Publisher 2013</td> 
   <td>PUB</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Publisher 2016</td> 
   <td>PUB</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Project 2013</td> 
   <td>MPP</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Project 2016</td> 
   <td>MPP</td> 
  </tr> 
  <tr> 
   <td>OpenOffice 4.1.2</td> 
   <td>ODT, ODP, ODS, ODG, ODF, SXW, SXI, SXC, SXD, XLS, XLSX, DOC, DOCX, PPT, PPTX, Bildformate (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPF, JPX, JP2, J2K, J2C, JPC), HTML, HTM, RTF und TXT</td> 
  </tr> 
  <tr> 
   <td>OpenOffice 3.4</td> 
   <td>ODT, ODP, ODS, ODG, ODF, SXW, SXI, SXC, SXD, XLS, XLSX, DOC, DOCX, PPT, PPTX, Bildformate (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPF, JPX, JP2, J2K, J2C, JPC), HTML, HTM, RTF und TXT</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>PDF Generator unterstützt nur englische, französische, deutsche und japanische Versionen der unterstützten Betriebssysteme und Anwendungen.
>
>Zusätzlich gilt Folgendes:
>
>* Für PDF Generator ist die 32-Bit-Version der [klassischen Acrobat 2017-Version 17.011.30078 oder höher](https://helpx.adobe.com/de/acrobat/release-note/release-notes-acrobat-reader.html) für die Konvertierung erforderlich.
>* PDF Generator unterstützt nur die 32-Bit-Einzelhandelsversion von Microsoft Office Professional Plus und andere für die Konvertierung erforderliche Software.
>* PDF Generator unterstützt nicht Microsoft Office 365.
>* PDF Generator-Konvertierungen für OpenOffice werden nur unter Windows, Linux und Solaris unterstützt.
>* Der HTML2PDF-Dienst wird unter AIX nicht mehr unterstützt.
>* Die Funktionen von OCR PDF, PDF optimieren und PDF erstellen werden nur unter Windows unterstützt.
>* Eine Version von Acrobat ist im Lieferumfang von AEM Forms enthalten, um die PDF Generator-Funktionalität zu aktivieren. Die gebündelte Version sollte während der Laufzeit der AEM Forms-Lizenz zur Verwendung mit AEM Forms PDF Generator nur programmatisch mit AEM Forms zugänglich sein. Weitere Informationen finden Sie in der AEM Forms-Produktbeschreibung für Ihre Bereitstellung ([On-Premise](https://helpx.adobe.com/de/legal/product-descriptions/adobe-experience-manager-on-premise.html) oder [Managed Services](https://helpx.adobe.com/de/legal/product-descriptions/adobe-experience-manager-managed-services.html))”
>


### Ausnahmen der Barrierefreiheit {#exceptions-to-accessibility-support}

Die folgenden Teilsysteme von AEM Forms sind nicht [508](https://www.section508.gov/) kompatibel:

* Adaptive Forms Authoring-Benutzeroberfläche
* Forms Manager Authoring-Benutzeroberfläche
* Benutzeroberfläche für Correspondence Management Authoring
* Administrator-Benutzeroberfläche (Benutzeroberfläche der Administration Console)

## Systemanforderungen für AEM Forms on JEE {#system-requirements-for-aem-forms-on-jee}

### Mindestanforderungen an die Hardware {#minimum-hardware-requirements}

<table> 
 <tbody> 
  <tr> 
   <td>Plattform</td> 
   <td>Mindestanforderungen an die Hardware</td> 
  </tr> 
  <tr> 
   <td>Microsoft Windows Server </td> 
   <td>Intel® Xeon® E5-2680, 2,4 GHz Prozessor oder gleichwertiger Prozessor<br /> VMWare ESX 5.1 oder höher<br /> RAM: 6 GB (64-Bit-Betriebssystem mit 64-Bit-JVM)<br /> Freier Speicherplatz: 15 GB temporärer Speicherplatz plus 22 GB<br /> für AEM Forms on JEE</td> 
  </tr> 
  <tr> 
   <td>Sun Solaris</td> 
   <td>UltraSPARC® IIIi, 1,5-GHz-Prozessor<br /> Partitionierung von Solaris-Containern (Zonen)<br /> RAM: 6 GB (64-Bit-Betriebssystem mit 64-Bit-JVM)<br /> Freier Speicherplatz: 6 GB temporärer Speicherplatz plus 22 GB<br /> für AEM Forms on JEE</td> 
  </tr> 
  <tr> 
   <td>IBM AIX</td> 
   <td>P6 pSeries 520 (Modell 52A) 9131-52A, 1,8 GHz-Prozessor<br /> LPAR-Partitionierung<br /> RAM: 6 GB (64-Bit-Betriebssystem mit 64-Bit-JVM)<br /> Freier Speicherplatz: 6 GB temporärer Speicherplatz plus 22 GB<br /> für AEM Forms on JEE</td> 
  </tr> 
  <tr> 
   <td>SUSE Linux Enterprise Server</td> 
   <td>Intel Xeon E5-2670v2, 1 vCPU, 2,5 GHz-Prozessor<br /> AWS m3.medium (3 ECU)<br /> RAM: 6 GB (64-Bit-Betriebssystem mit 64-Bit-JVM)<br /> Freier Speicherplatz: 6 GB temporärer Speicherplatz plus 22 GB<br /> für AEM Forms on JEE</td> 
  </tr> 
  <tr> 
   <td>Red Hat Enterprise Linux</td> 
   <td>Intel Xeon E5-2670v2, 1 vCPU, 2,5 GHz-Prozessor <br /> AWS m3.medium (3 ECUs)<br /> RAM: 6 GB (64 Bit OS mit 64 Bit JVM)<br /> Freier Speicherplatz: 6 GB temporärer  Leertaste plus 22 GB<br /> für AEM Forms on JEE<br /> </td> 
  </tr> 
  <tr> 
   <td>Hardwareanforderungen für eine kleine Produktionsumgebung</td> 
   <td> 
    <ul> 
     <li><strong>Intel-gestützte Umgebung</strong>: Intel® Xeon® E5-2680, 2,4 GHz oder höher. Durch die Verwendung eines Dualcore-Prozessors wird die Leistung weiter verbessert</li> 
     <li><strong>Sun SPARC-gestützte Umgebung:</strong> UltraSPARC V oder höher</li> 
     <li><strong>IBM AIX-gestützte Umgebung:</strong> Power6 oder höher<br /> </li> 
     <li><strong>Speicher: </strong>4 GB <br /> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

Weitere Anforderungen finden Sie unter:

* [Systemanforderungen für eine Bereitstellung von AEM Forms on JEE auf einem Einzelserver](https://www.adobe.com/go/learn_aemforms_sysreq_single_64_de)
* [Systemanforderungen für eine Clusterbereitstellung von AEM Forms on JEE](https://www.adobe.com/go/learn_aemforms_sysreq_cluster_64_de)

## Unterstützte Clients für AEM Forms on JEE {#supported-clients-for-aem-forms-on-jee}

### Workbench {#workbench}

>[!NOTE]
>
>Es werden sowohl 32-Bit- als auch 64-Bit-Betriebssysteme unterstützt.

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>Plattform</strong></p> </th> 
   <th><p><strong>Unterstützte Patch-Definitionen</strong></p> </th> 
  </tr> 
  <tr> 
   <td><p>Microsoft® Windows® 10</p> <p>(Enterprise, Pro, Basic)</p> </td> 
   <td>Service Packs und wichtige Updates</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Windows® 2012 Server R2</td> 
   <td>Service Packs und wichtige Updates</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Windows® 2016 Server</td> 
   <td>Service Packs und wichtige Updates</td> 
  </tr> 
 </tbody> 
</table>

* Erforderlicher Speicherplatz auf der Festplatte: 1,7 GB nur für Workbench, 2,7 GB auf einem einzelnen Laufwerk für eine vollständige Installation von Workbench, Designer und der Assembly mit den Beispielen, 400 MB für temporäre Installationsordner: 200 MB im Ordner „temp“ des Benutzers und 200 MB im temporären Ordner von Windows

>[!NOTE]
>
>Wenn sich all diese Speicherorte auf einem einzigen Laufwerk befinden, muss während der Installation 1,5 GB Speicherplatz verfügbar sein. Die Dateien, die in die temporären Ordner kopiert werden, werden nach Abschluss der Installation gelöscht.

* Speicher für Ausführung von Workbench: 2 GB RAM
* Hardware-Anforderung: Intel® Pentium® 4 oder gleichwertiger AMD-Prozessor, 1 GHz
* Minimale Bildschirmauflösung 1024 x 768 Pixel oder höher mit 16-Bit-Farbtiefe oder höher
* TCP/IPv4- oder TCP/IPv6-Netzwerkverbindung zum AEM Forms on JEE-Server

>[!NOTE]
>
>Sie müssen über Administratorrechte verfügen, um Workbench unter Windows installieren zu können. Wenn Sie die Installation mit einem Konto ohne Administratorrechte durchführen, werden Sie vom Installationsprogramm zur Eingabe der Anmeldeinformationen für ein entsprechendes Konto aufgefordert.

### Designer {#designer}

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

### Adobe Acrobat und Adobe Reader {#adobe-acrobat-and-adobe-reader}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>Acrobat und Adobe Reader (Basisversion)</strong></p> </th> 
   <th><p><strong>Unterstützte Patch-Definitionen</strong></p> </th> 
  </tr> 
  <tr> 
   <td>Acrobat 2017 (Classic)</td> 
   <td>Version 17.011.30078 oder neuer<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Die Acrobat DC-Produktfamilie führt zwei Spuren für Acrobat und Reader ein, die im Wesentlichen zwei verschiedene Produkte sind: „Klassik“ und „Fortlaufend“. Details und einen Vergleich der beiden Modi finden Sie unter [https://www.adobe.com/go/acrobatdctracks_de](https://www.adobe.com/go/acrobatdctracks_de).

### Browser {#browsers}

#### Desktops {#desktops}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>Browser (Basisversion)</strong></p> </th> 
   <th><p><strong>Unterstützungsebene</strong></p> </th> 
   <th><p><strong>Unterstützte Patch-Definitionen</strong></p> </th> 
  </tr> 
  <tr> 
   <td><p>Microsoft Edge</p> </td> 
   <td><p>A: Unterstützt</p> </td> 
   <td><p>Service Packs und Updates</p> </td> 
  </tr> 
  <tr> 
   <td><p>Mozilla Firefox 45.x</p> </td> 
   <td><p>A: Unterstützt</p> </td> 
   <td><p>Alle Updates</p> </td> 
  </tr> 
  <tr> 
   <td><p>Google Chrome 46+</p> </td> 
   <td><p>A: Unterstützt</p> </td> 
   <td><p>Alle Updates</p> </td> 
  </tr> 
  <tr> 
   <td>Apple Safari 11.x</td> 
   <td>A: Unterstützt</td> 
   <td>Alle Updates</td> 
  </tr> 
  <tr> 
   <td><p>Google Chrome und Firefox unter Mac OS X</p> </td> 
   <td><p>A: Unterstützt</p> </td> 
   <td><p>Alle Updates</p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Einige browserbezogene Ausnahmen für Desktops lauten wie folgt:
>
>* Die meisten modernen Browser unterstützen keine NPAPI-basierten Plug-Ins mehr. Informationen darüber, wie sich dies auf AEM Forms-Programme und -Workflows auswirkt, finden Sie unter [Einstellung von NPAPI-Browser-Plug-ins und ihre Auswirkungen](https://helpx.adobe.com/de/aem-forms/kb/discontinuation-of-npapi-plugins-impact-on-aem-forms.html).
>* Safari wird nur unter Mac OS X unterstützt.


#### Mobile Clients {#mobile-clients}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>Browser (Basisversion)</strong></p> </th> 
   <th><p><strong>Unterstützte Patch-Definitionen</strong></p> </th> 
  </tr> 
  <tr> 
   <td><p>Chrome unter Android™ 4.1.2 und höher</p> </td> 
   <td><p>Alle Updates</p> </td> 
  </tr> 
  <tr> 
   <td>Safari unter iOS 15.1 und höher</td> 
   <td>Alle Updates</td> 
  </tr> 
  <tr> 
   <td>Internet Explorer unter Windows 10</td> 
   <td>Alle Updates</td> 
  </tr> 
  <tr> 
   <td>Microsoft Edge<br /> </td> 
   <td>Alle Updates<br /> </td> 
  </tr> 
  <tr> 
   <td>Nativer Android-Browser  on Android™ 4.4 und höher</td> 
   <td>Alle Updates</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>* Forms Portal wird nur auf einem iPad nur in Safari unterstützt.
>


### AEM Forms-App {#aem-forms-workspace-app}

#### Mobilgeräteunterstützung {#mobile-device-support}

Das AEM Forms-Programm ist auf den folgenden Plattformen verfügbar:

| **Plattform** | **Unterstützte Geräte** |
|---|---|
| Apple iOS | Apple iPhone, iPad, iPad Air und iPad mini mit iOS 15.1 und höher. |
| Google Android | Android 4.4 (Android Kit Kat) und höher *[API-Ebene 19 und höher]*. Die AEM Forms-App ist für Samsung Galaxy-Tablets (7 und 10 Zoll) und Google Nexus-Tablets (7 Zoll) sowie beliebte Smartphones zertifiziert. |
| Microsoft Windows | Microsoft Surface-Geräte, Tablets, Laptops und Desktops mit Microsoft Windows 10. |

### Adobe Flash Player {#adobe-flash-player}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>Flash Player (Basisversion)</strong></p> </th> 
   <th><p><strong>Unterstützte Patch-Definitionen</strong></p> </th> 
  </tr> 
  <tr> 
   <td><p>Neueste Version des Flash Players</p> </td> 
   <td><p>Nebenversionen und Updates</p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Adobe hat [Ende 2020 die Aktualisierung und Verteilung von Flash Player eingestellt](https://theblog.adobe.com/adobe-flash-update/).

### Adobe Document Security Extension for Microsoft Office {#adobe-rights-management-extension-for-microsoft-office}

Klicken Sie [hier](https://www.adobe.com/de/products/livecycle/rightsmanagement/extension/downloads.html), um die Systemanforderungen für Adobe Document Security Extension for Microsoft® Office anzuzeigen.

### Ausnahmen der Clientunterstützung {#exceptions-to-client-support}

Microsoft® Windows® 2012 wird nicht für alle angegebenen clientseitigen Software mit Ausnahme von Reader und Acrobat unterstützt.

Außerdem unterstützt AEM Forms on JEE Updates, Patches und Fix Packs zusätzlich zur angegebenen Haupt- und Nebenversion der unterstützten Software. Die Aktualisierung auf die nächste Haupt- oder Nebenversion wird jedoch nicht unterstützt, sofern nichts anderes angegeben ist.

## Richtlinie zur Unterstützung von Patches von Drittanbietern {#third-party-patch-support-policy}

Die Anforderungen an Drittpartei-Software für AEM Forms on JEE werden im Abschnitt „Systemanforderungen“ der jeweiligen Produktdokumente erläutert. Die gesamte Dokumentation ist unter [https://adobe.com/go/learn_aemforms_documentation_64_de](https://adobe.com/go/learn_aemforms_documentation_64_de) verfügbar. 

Die für AEM Forms on JEE verwendeten Referenzplattformen von Drittanbietern stellen ein spezifisches Patchlevel für die Infrastruktur von Drittanbietern dar, das während der Entwicklung und Veröffentlichung der jeweiligen Versionen von AEM Forms on JEE aktuell war, und bilden das Mindest-Patchlevel oder Service Pack-Level der Infrastruktur, die von dieser Version von AEM Forms on JEE unterstützt wird.

Adobe unterstützt dringende oder empfohlene Patches von Drittanbietern und geht bei deren Veröffentlichung davon aus, dass Drittanbieter die Abwärtskompatibilität mit den Versionen gewährleisten, die AEM Forms on JEE unterstützt. Adobe unterstützt nur Patches, die nach dem in der AEM Forms on JEE-Dokumentation angegebenen Mindest-Patch-Level veröffentlicht wurden.

In einigen Fällen unterstützt Adobe keine Updates von Drittanbietern, die Hauptfunktionen verändern und dadurch keine vollständige Abwärtskompatibilität gewährleisten. Einzelheiten zu den unterstützten Updates finden Sie unter [Unterstützte Patch-Definitionen](https://helpx.adobe.com/de/aem-forms/aem-forms-third-party-software-patch.html) für bestimmte Herstellerprodukte und die von Adobe unterstützten Arten von Patches.

Unter Umständen, auf die Adobe keinen Einfluss hat, können sich Patches von Drittanbietern, die Abwärtskompatibilität beanspruchen, negativ auf die Adobe-Produkte oder Kundenumgebungen auswirken. In solchen Fällen empfiehlt die Adobe, dass die Kunden die Auswirkungen eines dringenden Patches von einem Dritten bewerten, bevor diese auf kritische Systeme angewendet werden. Die Adobe wird mit Dritten zusammenarbeiten, indem sie vernünftige geschäftliche Anstrengungen unternimmt, um solche Probleme zu lösen, entweder durch reguläre Unterstützungsprogramme für Adoben oder durch Dritte, die das Problem in ihrem Patch beheben. Dies garantiert nicht, dass ein neu veröffentlichtes Drittanbieter-Patch, das von Adobe unterstützt wird, wie in der Dokumentation des Anbieters oder mit AEM Forms on JEE funktioniert.

Adobe behält sich das Recht vor, die von einer AEM Forms on JEE-Version unterstützten Referenzplattformen von Drittanbietern und deren unterstützte Patch-Definitionen jederzeit zu ändern.

Weitere Informationen zu Patches von Drittanbietern finden Sie auch auf der Adobe Enterprise Support-Site in Knowledgebase-Artikeln, die sich auf Ihr Produkt beziehen.

[**Support kontaktieren**](https://www.adobe.com/account/sign-in.supportportal.html)

## Revisionsverlauf {#revision-history}


* 10. Oktober 2021

   * Die unterstützte Version von iOS für die Mobile App von AEM Forms wurde in iOS 15.1 geändert. Die vorherige Version war iOS 12.