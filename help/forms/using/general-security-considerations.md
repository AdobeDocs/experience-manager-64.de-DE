---
title: Allgemeine Überlegungen zur Sicherheit von AEM Forms on JEE
seo-title: General Security Considerations for AEM Forms on JEE
description: Erfahren Sie, wie Sie sich auf die Härtung der AEM Forms on JEE-Umgebung vorbereiten.
seo-description: Learn how to prepare for hardening your AEM Forms on JEE environment.
uuid: c5f6ffc7-b987-4541-ab60-e97b4ff5b2a4
content-type: reference
topic-tags: Security
products: SG_EXPERIENCEMANAGER/6.4
discoiquuid: 38132225-ecae-4887-8f3d-0b3845059130
role: Admin
exl-id: cde40670-ce9d-4b96-92d3-9e56cb15bdce
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1127'
ht-degree: 59%

---

# Allgemeine Überlegungen zur Sicherheit von AEM Forms on JEE {#general-security-considerations-for-aem-forms-on-jee}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Erfahren Sie, wie Sie sich auf die Härtung der AEM Forms on JEE-Umgebung vorbereiten.

Dieser Artikel enthält einleitende Informationen, die Sie bei der Vorbereitung auf die Härtung Ihrer AEM Forms-Umgebung unterstützen. Dazu gehören Informationen zu AEM Forms on JEE, zum Betriebssystem, zum Anwendungsserver und zur Datenbanksicherheit. Sie sollten diese Informationen lesen, bevor Sie Ihre Umgebung sperren.

## Anbieterspezifische Sicherheitsinformationen {#vendor-specific-security-information}

Dieser Abschnitt enthält sicherheitsbezogene Informationen zu Betriebssystemen, Anwendungsservern und Datenbanken, die in Ihre AEM Forms on JEE-Lösung integriert sind.

Verwenden Sie die Links in diesem Abschnitt, um herstellerspezifische Sicherheitsinformationen für Ihr Betriebssystem, Ihre Datenbank und Ihren Anwendungsserver zu finden.

### Informationen zur Betriebssystemsicherheit {#operating-system-security-information}

Berücksichtigen Sie bei der Absicherung Ihres Betriebssystems sorgfältig die vom Hersteller Ihres Betriebssystems beschriebenen Maßnahmen, einschließlich der folgenden:

* Definieren und Steuern von Benutzern, Rollen und Berechtigungen
* Überwachungsprotokolle und Prüfprotokolle
* Entfernen unnötiger Dienste und Anwendungen
* Sichern von Dateien

Sicherheitsinformationen zu von AEM Forms on JEE unterstützten Betriebssystemen finden Sie in der nachfolgenden Tabelle:

<table> 
 <thead> 
  <tr> 
   <th><p>Betriebssystem</p> </th> 
   <th><p>Sicherheitsressource</p> </th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>IBM® AIX® 7.2</p> </td> 
   <td><p><a href="https://www.ibm.com/support/knowledgecenter/ssw_aix_72/com.ibm.aix.security/security-kickoff.htm" target="_blank">IBM AIX-Sicherheitsvorteile</a></p> </td> 
  </tr> 
  <tr> 
   <td><p>Microsoft Windows Server 2012 </p> </td> 
   <td><p><a href="https://blogs.technet.com/b/secguide/archive/2014/08/13/security-baselines-for-windows-8-1-windows-server-2012-r2-and-internet-explorer-11-final.aspx" target="_blank">Windows Server 2012 Security Guide</a></p> </td> 
  </tr> 
  <tr> 
   <td><p>Microsoft Windows Server 2016 </p> </td> 
   <td><p><a href="https://cloudblogs.microsoft.com/windowsserver/2017/08/22/now-available-windows-server-2016-security-guide/">Windows Server 2016 Security Guide</a></p> </td> 
  </tr> 
  <tr> 
   <td><p>Red Hat® Linux® AP oder ES</p> </td> 
   <td><p><a href="https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/pdf/security_guide/Red_Hat_Enterprise_Linux-7-Security_Guide-en-US.pdf" target="_blank">Red Hat Enterprise Linux Security Guide</a></p> </td> 
  </tr> 
  <tr> 
   <td><p>Sun Solaris 11</p> </td> 
   <td><p><a href="https://docs.oracle.com/cd/E53394_01/html/E54807/index.html" target="_blank">Richtlinien zur Sicherheit und Härtung</a></p> </td> 
  </tr> 
  <tr> 
   <td>Oracle Linux® 7 Update 3</td> 
   <td><a href="https://docs.oracle.com/cd/E52668_01/E54670/E54670.pdf" target="_blank">Security Guide for Release 7</a><br /> </td> 
  </tr> 
  <tr> 
   <td>CentOS 7<sup> </sup></td> 
   <td><a href="https://wiki.centos.org/HowTos/OS_Protection" target="_blank">Protection documentation</a></td> 
  </tr> 
 </tbody> 
</table>

### Informationen zur Sicherheit des Anwendungs-Servers {#application-server-security-information}

Berücksichtigen Sie bei der Sicherung Ihres Anwendungs-Servers sorgfältig die von Ihrem Serveranbieter beschriebenen Maßnahmen, einschließlich der folgenden:

* Verwenden eines nicht offensichtlichen Benutzernamens für Administratoren
* Deaktivieren unnötiger Dienste
* Schützen des Konsolenmanagers
* Aktivieren sicherer Cookies
* Schließen nicht benötigter Ports
* Einschränken von Clients nach IP-Adressen oder Domänen
* Verwenden von Java™ Security Manager zum programmgesteuerten Einschränken von Berechtigungen

Sicherheitsinformationen zu von AEM Forms on JEE unterstützten Anwendungsservern finden Sie in den nachfolgend aufgeführten Ressourcen.

<table> 
 <thead> 
  <tr> 
   <th><p>Anwendungs-Server</p> </th> 
   <th><p>Sicherheitsressource</p> </th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>Oracle WebLogic®</p> </td> 
   <td><p>Suchen Sie unter <a href="https://download.oracle.com/docs/">https://download.oracle.com/docs/</a> nach „Understanding WebLogic Security“.</p> </td> 
  </tr> 
  <tr> 
   <td><p>IBM WebSphere®</p> </td> 
   <td><p><a href="https://www.ibm.com/developerworks/websphere/zones/was/security/" target="_blank">Anwendungen und ihre Umgebung sichern</a></p> </td> 
  </tr> 
  <tr> 
   <td><p>Red Hat® JBoss®</p> </td> 
   <td><p><a href="https://docs.jboss.org/author/display/AS7/Security+subsystem+configuration">Konfiguration des Sicherheitssystems</a></p> </td> 
  </tr> 
 </tbody> 
</table>

### Informationen zur Datenbanksicherheit {#database-security-information}

Berücksichtigen Sie bei der Sicherung Ihrer Datenbank die von Ihrem Datenbankanbieter beschriebenen Maßnahmen, einschließlich der folgenden:

* Einschränken von Vorgängen mit Zugriffssteuerungslisten (ACLs)
* Verwendung nicht standardmäßiger Anschlüsse
* Datenbank hinter einer Firewall ausblenden
* Verschlüsseln sensibler Daten vor dem Schreiben in die Datenbank (siehe die Dokumentation des Datenbankherstellers)

Sicherheitsinformationen zu von AEM Forms on JEE unterstützten Datenbanken finden Sie in den nachfolgend aufgeführten Ressourcen.

<table> 
 <thead> 
  <tr> 
   <th><p>Datenbank</p> </th> 
   <th><p>Sicherheitsressource</p> </th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>IBM DB2 11.1</p> </td> 
   <td><p><a href="https://www-01.ibm.com/software/data/db2/library/">DB2 Product Family Library</a></p> </td> 
  </tr> 
  <tr> 
   <td><p>Microsoft SQL Server 2016</p> </td> 
   <td>Suchen Sie im Web nach „SQL Server 2016: Sicherheit“</td> 
  </tr> 
  <tr> 
   <td><p>MySQL 5</p> </td> 
   <td><p><a href="https://dev.mysql.com/doc/refman/5.0/en/security.html">MySQL 5.0 Allgemeine Sicherheitsprobleme</a></p> <p><a href="https://dev.mysql.com/doc/refman/5.1/en/security.html">MySQL 5.1 Allgemeine Sicherheitsprobleme</a></p> </td> 
  </tr> 
  <tr> 
   <td><p>Oracle 12c</p> </td> 
   <td><p>Weitere Informationen finden Sie im Kapitel „Sicherheit“ in der <a href="https://docs.oracle.com/database/121/TDPSG/GUID-6E2F4E53-5D87-4FCD-9C9C-6792217D7014.htm#TDPSG94426" target="_blank">Oracle 12g Dokumentation</a></p> </td> 
  </tr> 
 </tbody> 
</table>

In dieser Tabelle werden die Standardanschlüsse beschrieben, die während des AEM Forms on JEE-Konfigurationsprozesses geöffnet sein müssen. Wenn Sie die Verbindung über HTTPS herstellen, passen Sie Ihre Anschlussinformationen und IP-Adressen entsprechend an. Weitere Informationen zum Konfigurieren von Anschlüssen finden Sie im Dokument *Installieren und Bereitstellen von AEM Forms on JEE* für Ihren Anwendungsserver.

<table> 
 <thead> 
  <tr> 
   <th><p>Produkt oder Dienst</p> </th> 
   <th><p>Port-Nummer</p> </th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>JBoss</p> </td> 
   <td><p>8080</p> </td> 
  </tr> 
  <tr> 
   <td><p>WebLogic</p> </td> 
   <td><p>7001</p> </td> 
  </tr> 
  <tr> 
   <td><p>WebLogic Managed Server</p> </td> 
   <td><p>Wird vom Administrator während der Konfiguration festgelegt</p> </td> 
  </tr> 
  <tr> 
   <td><p>WebSphere</p> </td> 
   <td><p>9060, wenn Global Security aktiviert ist, lautet der standardmäßige SSL-Anschlusswert 9043.</p> <p>9080</p> </td> 
  </tr> 
  <tr> 
   <td><p>BAM-Server</p> </td> 
   <td><p>7001</p> </td> 
  </tr> 
  <tr> 
   <td><p>SOAP</p> </td> 
   <td><p>8880</p> </td> 
  </tr> 
  <tr> 
   <td><p>MySQL</p> </td> 
   <td><p>3306</p> </td> 
  </tr> 
  <tr> 
   <td><p>Oracle</p> </td> 
   <td><p>1521</p> </td> 
  </tr> 
  <tr> 
   <td><p>DB2</p> </td> 
   <td><p>50000</p> </td> 
  </tr> 
  <tr> 
   <td><p>SQL Server</p> </td> 
   <td><p>1433</p> </td> 
  </tr> 
  <tr> 
   <td><p>LDAP</p> </td> 
   <td><p>Der Anschluss, an dem der LDAP-Server ausgeführt wird. Der Standardanschluss ist in der Regel 389. Wenn Sie jedoch die SSL-Option auswählen, ist der Standardanschluss in der Regel 636. Erkundigen Sie sich beim LDAP-Administrator, welchen Anschluss Sie angeben müssen.</p> </td> 
  </tr> 
 </tbody> 
</table>

### JBoss für die Verwendung eines nicht standardmäßigen HTTP-Ports konfigurieren {#configuring-jboss-to-use-a-non-default-http-port}

JBoss Application Server verwendet 8080 als standardmäßigen HTTP-Port. JBoss verfügt außerdem über die vorkonfigurierten Anschlüsse 8180, 8280 und 8380, die in der Datei „jboss-service.xml“ auskommentiert sind. Wenn Sie auf Ihrem Computer über eine Anwendung verfügen, die bereits diesen Anschluss verwendet, ändern Sie den von AEM Forms on JEE verwendeten Anschluss, indem Sie die folgenden Schritte ausführen:

1. Öffnen Sie die folgende Datei zum Bearbeiten:

   Einzelserverinstallation: [JBoss-Stamm]/standalone/configuration/standalone.xml

   Cluster-Installationen: [JBoss-Stamm]/domain/configuration/domain.xml

1. Ändern Sie den Wert des Attributs **port** im Tag **&lt;socket-binding>** in eine benutzerdefinierte Port-Nummer. Im Folgenden wird beispielsweise Port 8090 verwendet:

   &lt;socket-binding name=&quot;http&quot; port=&quot;8090&quot;/>

1. Speichern und schließen Sie die Datei.
1. Starten Sie den JBoss Anwendungs-Server neu.

## Überlegungen zur Sicherheit von AEM Forms on JEE {#aem-forms-on-jee-security-considerations}

In diesem Abschnitt werden einige AEM Forms on JEE-spezifische Sicherheitsprobleme beschrieben, die Sie kennen sollten.

### In der Datenbank nicht verschlüsselte E-Mail-Anmeldeinformationen {#email-credentials-not-encrypted-in-database}

Die von Anwendungen gespeicherten E-Mail-Anmeldeinformationen werden nicht verschlüsselt, bevor sie in der AEM Forms on JEE-Datenbank gespeichert werden. Wenn Sie einen Dienstendpunkt für die Verwendung von E-Mails konfigurieren, werden Kennwortinformationen, die im Rahmen dieser Endpunktkonfiguration verwendet werden, nicht verschlüsselt, wenn sie in der Datenbank gespeichert werden.

### Sensitive Inhalte für Rights Management in der Datenbank {#sensitive-content-for-rights-management-in-the-database}

AEM Forms on JEE verwendet die AEM Forms on JEE-Datenbank, um vertrauliche Informationen über Dokumentschlüssel und anderes kryptographisches Material zu speichern, das für Richtliniendokumente verwendet wird. Wenn Sie die Datenbank gegen unberechtigten Zugriff schützen, erhöht dies den Schutz dieser sensiblen Informationen.

### Kennwort in unverschlüsseltem Textformular {#password-in-clear-text-format-in-adobe-ds-xml}

Der zum Ausführen von AEM Forms on JEE verwendete Anwendungs-Server muss eigens konfiguriert werden, um über eine auf dem Anwendungs-Server konfigurierte Datenquelle auf Ihre Datenbank zuzugreifen. Stellen Sie sicher, dass der Anwendungs-Server Ihr Datenbankkennwort in seiner Datenquellenkonfigurationsdatei nicht in unverschlüsseltem Textformat offen legt.

Die Datei lc_[Datenbank].xml sollte kein Kennwort in unverschlüsseltem Textformat enthalten. Fragen Sie beim Hersteller des Anwendungs-Servers nach, wie Sie diese Kennwörter für Ihren Anwendungs-Server verschlüsseln sollen.

>[!NOTE]
>
>Das AEM Forms on JEE JBoss Turnkey-Installationsprogramm verschlüsselt das Datenbankkennwort.

Bei IBM® WebSphere Application Server und Oracle WebLogic Server werden Datenquellenkennwörter eventuell standardmäßig verschlüsselt. Schlagen Sie in der Dokumentation zu Ihrem Anwendungs-Server nach, um sicherzustellen, dass eine Verschlüsselung erfolgt.

### Schutz des in Trust Store gespeicherten privaten Schlüssels {#protecting-the-private-key-stored-in-trust-store}

Die privaten Schlüssel oder Berechtigungen, die in Trust Store importiert wurden, werden in der AEM Forms on JEE-Datenbank gespeichert. Sie müssen entsprechende Sicherheitsmaßnahmen treffen, um die Datenbank zu schützen und den Zugriff auf benannte Administratoren zu beschränken.
