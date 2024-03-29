---
title: Bereitstellen und Verwalten
seo-title: Deploying and Maintaining
description: Erfahren Sie, wie Sie mit der AEM-Installation beginnen.
seo-description: Learn how to get started with the AEM installation.
uuid: 552a41a1-a8b3-4c5a-bfb3-718bcb612752
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: deploying
discoiquuid: 6696c325-d188-41c8-a39f-c8ae7f339fe8
exl-id: 9a779cde-dfdf-4d70-a452-5e7d12bf3f28
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1855'
ht-degree: 88%

---

# Bereitstellen und Verwalten {#deploying-and-maintaining}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Inhalt dieser Seite:

* [Grundlegende Konzepte](#basic-concepts)

   * [Was ist AEM?](#what-is-aem)
   * [Typische Bereitstellungen](#typical-deployment-scenarios)

      * [On-Premise](#on-premise)
      * [Managed Services mit Cloud Manager](#managed-services-using-cloud-manager)

* [Erste Schritte](#getting-started)

   * [Voraussetzungen](#prerequisites)
   * [Abrufen der Software](#getting-the-software)
   * [Standardmäßige lokale Installation](#default-local-install)
   * [Installation von Erstellungs- und Veröffentlichungsinstanzen](#author-and-publish-installs)
   * [Entpacktes Installationsverzeichnis](#unpacked-install-directory)
   * [Starten und Anhalten](#starting-and-stopping)

Nachdem Sie sich mit diesen Grundlagen vertraut gemacht haben, finden Sie auf den folgenden Unterseiten komplexere und ausführlichere Informationen:

* [Technische Anforderungen](/help/sites-deploying/technical-requirements.md)
* [Empfohlene Bereitstellungen](/help/sites-deploying/recommended-deploys.md)
* [Benutzerdefinierte Standalone-Installation](/help/sites-deploying/custom-standalone-install.md)
* [Anwendungsserver-Installation](/help/sites-deploying/application-server-install.md)
* [Fehlerbehebung](/help/sites-deploying/troubleshooting.md)
* [Start und Stopp über die Befehlszeile](/help/sites-deploying/command-line-start-and-stop.md)
* [Konfiguration](/help/sites-deploying/configuring.md)
* [Aktualisieren auf AEM 6.4](/help/sites-deploying/upgrade.md)
* [E-Commerce](/help/sites-deploying/ecommerce.md)
* [Artikel mit Anleitungen für die Konfiguration](/help/sites-deploying/ht-deploy.md)
* [Web-Konsole](/help/sites-deploying/web-console.md)
* [Fehlerbehebung bei Replikationsproblemen](/help/sites-deploying/troubleshoot-rep.md)
* [Best Practices](/help/sites-deploying/best-practices.md)
* [Bereitstellen von Communities](/help/communities/deploy-communities.md)
* [Einführung in die AEM-Plattform](/help/sites-deploying/platform.md)
* [Leistungsrichtlinien](/help/sites-deploying/performance-guidelines.md)
* [Erste Schritte mit AEM Mobile](/help/mobile/getting-started-aem-mobile.md)
* [Was ist AEM Screens? ](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/aem-screens-introduction.html?lang=de)

## Grundlegende Konzepte {#basic-concepts}

### Was ist AEM? {#what-is-aem}

Adobe Experience Manager ist ein Web-basiertes Client-Server-System für das Erstellen, Verwalten und Bereitstellen von kommerziellen Websites und zugehörigen Services. Es kombiniert einige Funktionen auf Infrastrukturebene und Anwendungsebene in einem einzelnen integrierten Paket.

Auf Infrastrukturebene bietet AEM Folgendes:

* **Webanwendungsserver**: AEM können im eigenständigen Modus (einschließlich eines integrierten Jetty-Webservers) oder als Webanwendung auf einem Drittanbieter-Anwendungsserver (WebLogic, WebSphere usw.) bereitgestellt werden.
* **Web-Anwendungs-Framework**: AEM beinhaltet das Sling-Web-Anwendungs-Framework, das das Schreiben von RESTful-Web-Anwendungen vereinfacht.
* **Content-Repository**: AEM enthält ein Java Content Repository (JCR), einen Typ hierarchischer Datenbank, der speziell für unstrukturierte und teilstrukturierte Daten entwickelt wurde. Das Repository speichert nicht nur den für die Benutzenden sichtbaren Inhalt, sondern auch den gesamten Code, die Vorlagen und die internen Daten, die von der Anwendung verwendet werden.

Auf dieser Grundlage bietet AEM außerdem eine Reihe von Funktionen auf Anwendungsebene für die Verwaltung von:

* **Websites**
* **Mobile Apps**
* **Digitalen Veröffentlichungen**
* **Formulare**
* **Digitale Assets**
* **Communities**
* **Online-Commerce**

Schließlich können Kunden diese Bausteine auf Infrastruktur- und Anwendungsebene verwenden, um benutzerdefinierte Lösungen zu erstellen, indem sie eigene Anwendungen erstellen.

Der AEM-Server ist **Java-basiert** und kann auf den meisten Betriebssystemen ausgeführt werden, die diese Plattform unterstützen. Die gesamte Client-Interaktion mit AEM erfolgt über einen **Webbrowser**.

### Typische Implementierungsszenarien {#typical-deployment-scenarios}

In der Terminologie von AEM entspricht eine „Instanz“ einer Kopie von AEM, die auf einem Server ausgeführt wird. AEM-Installationen betreffen in der Regel mindestens zwei Instanzen, die normalerweise auf separaten Computern ausgeführt werden:

* **Author**: Eine zum Erstellen, Hochladen und Bearbeiten von Inhalten sowie zum Verwalten der Website verwendete AEM-Instanz. Sobald der Inhalt für die Veröffentlichung bereit ist, wird er an die Veröffentlichungsinstanz repliziert.
* **Publish**: Eine AEM-Instanz, die den Inhalt veröffentlicht.

Diese Instanzen sind hinsichtlich der installierten Software identisch. Sie unterscheiden sich nur in Bezug auf ihre Konfiguration. Darüber hinaus verwenden die meisten Installationen einen Dispatcher:

* **Dispatcher**: Ein statischer Webserver (Apache httpd, Microsoft IIS usw.), der um das AEM Dispatcher-Modul erweitert wurde. Er speichert durch die Veröffentlichungsinstanz generierte Web-Seiten zwischen, um die Leistung zu verbessern.

Es gibt viele erweiterte Optionen und Ausarbeitungen dieses Setups, aber das grundlegende Muster von Author, Publish und Dispatcher bildet den Kern der meisten Implementierungen. Zunächst konzentrieren wir uns auf ein relativ einfaches Setup. Die Erläuterung erweiterter Bereitstellungsoptionen folgt.

In den folgenden Abschnitten werden beide Szenarien beschrieben:

* **On-Premise**: AEM in Ihrer Unternehmensumgebung bereitgestellt und verwaltet.

* **Managed Services – Cloud-Manager für Adobe Experience Manager**: AEM von Adobe Managed Services bereitgestellt und verwaltet.

### On-Premise {#on-premise}

Sie können AEM auf Servern in Ihrer Unternehmensumgebung installieren. Typische Installationsinstanzen umfassen: Bereitstellungs-, Test- und Veröffentlichungsumgebungen. Nähere Informationen finden Sie im Abschnitt [Erste Schritte](/help/sites-deploying/deploy.md#getting-started). Dort erhalten Sie grundlegende Informationen darüber, wie Sie die AEM-Software erhalten, um sie lokal zu installieren.

Weitere Informationen zu typischen On-Premise-Bereitstellungen finden Sie unter [Empfohlene Bereitstellungen](/help/sites-deploying/recommended-deploys.md).

### Managed Services mit Cloud Manager {#managed-services-using-cloud-manager}

AEM Managed Services ist eine Komplettlösung für das Management digitaler Erlebnisse. Sie bietet die Vorteile einer Lösung zur Erlebnisbereitstellung in der Cloud unter Beibehaltung aller Vorteile hinsichtlich Kontrolle, Sicherheit und Personalisierung einer On-Premise-Bereitstellung. AEM Managed Services ermöglicht Kunden schnellere Launches, indem sie in der Cloud bereitstellen und dabei auf die Best Practices und die Unterstützung von Adobe vertrauen können. Unternehmen und Anwenderinnen bzw. Anwender im Geschäftsbereich können Kundinnen und Kunden in kürzester Zeit ansprechen, Marktanteile steigern und sich auf die Erstellung innovativer Marketing-Kampagnen konzentrieren, während die IT-Abteilung entlastet wird.

Mit AEM Managed Services können Kundinnen und Kunden die folgenden Vorteile erzielen:

**Schnellere Markteinführungszeiten:** Dank flexibler Cloud-Infrastruktur von Adobe Managed Services können Organisationen erfolgreiche digitale Erlebnisse schnell planen, starten und optimieren. Adobe verwaltet die Cloud-Architektur ohne zusätzliches Kapital, keine Hardware oder Software, und die Customer Success Engineers der Adobe unterstützen Sie bei AEM Architektur, Bereitstellung, Anpassung für die Verbindung mit Back-End-Apps und Best Practices für die Live-Schaltung.

**Höhere Leistung:** Bietet zuverlässige digitale Erlebnisse für Ihr Unternehmen mit vier Service-Verfügbarkeitsoptionen, 99,5 %, 99,9 %, 99,95 % und 99,99 %. Zusätzlich ermöglicht es eine automatische Sicherung und Modelle zur Notfallwiederherstellung und hilft so, Sicherheit und kontinuierliche Verwaltung sicherzustellen.

**Optimierte IT-Kosten:** Proaktive Unterstützung und Know-how helfen Unternehmen, über neue Entwicklungen von AEM auf dem Laufenden zu bleiben. Adobe Platinum Maintenance und Support ist bei neuen Bereitstellungen von AMS Enterprise/Basic automatisch enthalten und bietet technisches Know-how und operative Erfahrung, um Unternehmen bei der Verwaltung ihrer unternehmenskritischen Applikationen zu helfen. Kostenlose grundlegende Analytics- oder Target-Funktionen bieten zusätzlichen Mehrwert für mittelständische Unternehmen mit begrenztem Bedarf hinsichtlich Analysen und Personalisierung.

**Oberste Sicherheit:** Stellt physische, Netzwerk- und Datensicherheit auf Unternehmensniveau sicher, indem Kunden-Applikationen in einer Einrichtung mit beschränktem Zugang, hinter Firewall-Systemen oder in einer virtuellen, privaten Cloud, gehostet werden. Es beinhaltet virtuelle Maschinen für Einzelmandanten mit robuster Datenspeicherverschlüsselung, Virenschutz und Datenisolierung.

**Cloud Manager**: Cloud Manager, Teil von Adobe Experience Manager Managed Services, bietet ein Selbstbedienungsportal, das es Organisationen besser ermöglicht, Adobe Experience Manager in der Cloud selbst zu verwalten. Es enthält eine moderne kontinuierliche Integration und eine kontinuierliche Bereitstellungs-Pipeline (CI/CD), die IT-Teams und Implementierungspartner dazu nutzen können, die Geschwindigkeit der Lieferung von Personalisierungen oder Aktualisierungen zu erhöhen, ohne bei der Leistung oder Sicherheit Abstriche zu machen. Cloud Manager ist nur für Kundinnen und Kunden von Adobe Managed Services verfügbar.

Weitere Informationen zu Cloud Manager und seinen Ressourcen finden Sie unter [**Cloud Manager-Benutzerhandbuch**](https://helpx.adobe.com/experience-manager/cloud-manager/user-guide.html).

## Erste Schritte {#getting-started}

### Voraussetzungen {#prerequisites}

Während Produktionsinstanzen für gewöhnlich auf dedizierten Computern ausgeführt werden, auf denen wiederum offiziell unterstützte Betriebssysteme ausgeführt werden (siehe [Technische Anforderungen](/help/sites-deploying/technical-requirements.md)), kann der Experience Manager-Server tatsächlich auf jedem System ausgeführt werden, das [**Java Standard Edition 8**](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) unterstützt.

Um sich mit AEM vertraut zu machen bzw. um die Entwicklung auf AEM vorzunehmen, wird häufig eine auf Ihrem lokalen Computer installierte Instanz verwendet, auf der Apple OS X oder Desktopcomputerversionen von Microsoft Windows oder Linux ausgeführt werden.

Auf der Clientseite funktioniert AEM mit allen modernen Browsern (**Microsoft Edge**, **Internet Explorer** 11, **Chrome** 51+ , **Firefox** 47+, **Safari** 8+) auf Desktop- und Tablet-Betriebssystemen. Details finden Sie unter [Unterstützte Clientplattformen](/help/sites-deploying/technical-requirements.md#supported-client-platforms).

### Abrufen der Software {#getting-the-software}

Kunden mit einem gültigen Wartungs- und Supportvertrag sollten eine E-Mail-Benachrichtigung mit einem Code erhalten haben und in der Lage sein, AEM über die [**Adobe-Lizenzierungswebsite**](https://licensing.adobe.com/) herunterzuladen. Geschäftspartner können den Downloadzugriff über [**spphelp@adobe.com**](mailto:spphelp@adobe.com) anfordern.

Das AEM-Softwarepaket steht in zwei Formen zur Verfügung:

* **cq-quickstart-6.4.0.jar:** Eine eigenständige ausführbare *JAR*-Datei, die alles für die Einrichtung und Ausführung enthält.

* **cq-quickstart-6.4.0.war:** Eine *WAR*-Datei für die Bereitstellung auf dem Anwendungsserver eines Drittanbieters.

Im folgenden Abschnitt wird die **eigenständige Installation** beschrieben. Weitere Informationen zum Installieren von AEM auf einem Anwendungs-Server finden Sie unter [Anwendungs-Server-Installation](/help/sites-deploying/application-server-install.md).

### Standardmäßige lokale Installation {#default-local-install}

1. Erstellen Sie auf Ihrem lokalen Computer ein Installationsverzeichnis. Beispiel:

   UNIX-Installationsspeicherort: **/opt/aem**

   Windows-Installationsspeicherort: **`C:\Program Files\aem`**

   Ebenso ist es üblich, Beispielinstanzen in einem Ordner direkt auf dem Desktop zu installieren. In jedem Fall werden wir diesen Speicherort im Allgemeinen wie folgt bezeichnen:

   `<aem-install>`

   *Beachten Sie, dass der Pfad des Dateiverzeichnisses nur aus US-ASCII-Zeichen bestehen darf.*

1. Legen Sie die Dateien **jar** und **license** in dieses Verzeichnis:

   ```shell
   <aem-install>/
       cq-quickstart-6.4.0.jar
       license.properties
   ```

   Wenn Sie keine `license.properties`-Datei bereitstellen, leitet AEM Ihren Browser beim Start zu einem **Begrüßungsbildschirm** um, wo Sie Ihren Lizenzschlüssel eingeben können. Sie müssen einen gültigen Lizenzschlüssel von Adobe anfordern, wenn Sie noch nicht über einen verfügen.

1. Doppelklicken Sie zum Starten der Instanz in einer GUI-Umgebung einfach auf die Datei **`cq-quickstart-6.4.0.jar`**.

   Alternativ können Sie AEM über die Befehlszeile starten. Geben Sie für eine 32-Bit-Java-VM Folgendes ein:

   ```shell
       java -Xmx1024M -jar cq-quickstart-6.4.0.jar
   ```

   Geben Sie für eine 64-Bit-VM Folgendes ein:

   ```shell
       java -XX:MaxPermSize=256m -Xmx1024M -jar cq-quickstart-6.4.0.jar
   ```

AEM braucht ein paar Minuten, um die JAR-Datei zu entpacken, sich selbst zu installieren und zu starten. Das obige Verfahren führt zu:

* einer **AEM author**-Instanz,
* die auf **localhost**
* auf Port **4502** ausgeführt wird

Navigieren Sie für den Zugriff auf den Instanzpunkt zu:

**`http://localhost:4502`**

Das Ergebnis in der Erstellungsinstanz wird automatisch so konfiguriert, dass eine Verbindung zu einer **Veröffentlichungsinstanz** auf **`localhost:4503`** hergestellt wird.

### Installation von Erstellungs- und Veröffentlichungsinstanzen {#author-and-publish-installs}

Die Standardinstallation (eine **author**-Instanz auf **`localhost:4502`**) kann einfach durch das Umbenennen der `jar`-Datei geändert werden, bevor sie das erste Mal gestartet wird. Das Benennungsmuster lautet:

**`cq-<instance-type>-p<port-number>.jar`**

So führt beispielsweise das Umbenennen der Datei zu

**`cq-author-p4502.jar`**

und das Starten dieser Datei zu einer „author“-Instanz, die auf **`localhost:4502`** ausgeführt wird.

Ähnlich verhält es sich beim Umbenennen und Starten der Datei

**`cq-publish-p4503.jar`**

Dies führt zu einer „publish“-Instanz, die auf **`localhost:4503`** ausgeführt wird.

Diese zwei Instanzen würden Sie beispielsweise installieren in:

`<aem-install>/author`und

**`<aem-install>/publish`**

Weitere Informationen über das Anpassen Ihrer Installation finden Sie unter:

* [Benutzerdefinierte Standalone-Installation](/help/sites-deploying/custom-standalone-install.md)
* [Ausführungsmodi](/help/sites-deploying/configure-runmodes.md)

### Entpacktes Installationsverzeichnis {#unpacked-install-directory}

Wenn die JAR-Datei für den Schnellstart erstmals gestartet wird, entpackt sie sich selbst im selben Verzeichnis unter einem neuen Unterverzeichnis mit dem Namen `crx-quickstart`. Sie sollten Folgendes erhalten:

```xml
<aem-install>/
    license.properties
    cq-quickstart-6.4.0.jar
    crx-quickstart/
        app/
        bin/
        conf/
        launchpad/
        logs/
        metrics/        
        monitoring/
        opt/
        repository/
        threaddumps/
        eula-de_DE.html
        eula-en_US.html
        eula-fr_FR.html
        eula-ja_JP.html
        readme.txt
```

Wenn die Instanz über die Benutzeroberfläche installiert wurde, wird automatisch ein Browser-Fenster geöffnet und ein Desktop-Programm-Fenster wird geöffnet, in dem der Host und Port der Instanz sowie ein Ein-/Aus-Schalter angezeigt werden:

![screen_shot_2018-04-05at91504am1](assets/screen_shot_2018-04-05at91504am1.png)

>[!NOTE]
>
>Wenn Sie Symlinks verwenden, sehen Sie sich den Artikel [Probleme mit Symlink](https://helpx.adobe.com/de/experience-manager/kb/changing-symlink.html) an.

### Starten und Anhalten {#starting-and-stopping}

Nachdem AEM sich selbst entpackt und zum ersten Mal gestartet hat, wird durch einen Doppelklick auf die JAR-Datei im Installationsverzeichnis einfach die Instanz gestartet, sie wird nicht erneut installiert.

Um die Instanz über die grafische Benutzeroberfläche zu stoppen, klicken Sie einfach auf den **Ein-/Aus**-Schalter im Fenster des Desktopprogramms.

Sie können AEM auch über die Befehlszeile anhalten und starten. Angenommen, Sie haben die Instanz bereits erstmals installiert, dann befinden sich die **Befehlszeilenskripts** hier:

**`<aem-install>/crx-quickstart/bin/`**

Dieser Ordner enthält die folgenden Unix-Bash-Shell-Skripts:

* **`start`**: Startet die Instanz
* `stop`: Hält die Instanz an
* **`status`**: Meldet den Status der Instanz
* **`quickstart`**: Wird bei Bedarf zum Konfigurieren der Startinformationen verwendet

Es stehen auch entsprechende **`bat`**-Dateien für Windows zur Verfügung. Detaillierte Informationen finden Sie in:

* [Start und Stopp über die Befehlszeile](/help/sites-deploying/command-line-start-and-stop.md)

AEM startet und leitet Ihren Webbrowser automatisch zur entsprechenden Seite um. Für gewöhnlich handelt es sich um die Anmeldeseite, beispielsweise:

`http://localhost:4502/`

![screen_shot_2018-04-03at15317pm1](assets/screen_shot_2018-04-03at15317pm1.png)

Nach der Anmeldung haben Sie Zugriff auf AEM. Für weitere Informationen je nach Ihrer Rolle siehe Folgendes:

* [Authoring](/help/sites-authoring/home.md)
* [Verwalten](/help/sites-administering/home.md)
* [Entwickeln](/help/sites-developing/home.md)
* [Verwaltung](/help/managing/best-practices.md)

## Erweiterte Implementierung {#advanced-deployment}

Der obige Abschnitt sollte Ihnen ein gutes Verständnis der Grundlagen zur AEM-Installation vermitteln. Die Installation eines vollständigen Produktionssystems von AEM kann jedoch erheblich komplexer sein. In den folgenden Unterseiten wird die erweiterte Installation vollständig abgedeckt:

* [Technische Anforderungen](/help/sites-deploying/technical-requirements.md)
* [Empfohlene Bereitstellungen](/help/sites-deploying/recommended-deploys.md)
* [Benutzerdefinierte Standalone-Installation](/help/sites-deploying/custom-standalone-install.md)
* [Anwendungsserver-Installation](/help/sites-deploying/application-server-install.md)
* [Fehlerbehebung](/help/sites-deploying/troubleshooting.md)
* [Start und Stopp über die Befehlszeile](/help/sites-deploying/command-line-start-and-stop.md)
* [Konfiguration](/help/sites-deploying/configuring.md)
* [Aktualisieren auf AEM 6.4](/help/sites-deploying/upgrade.md)
* [E-Commerce](/help/sites-deploying/ecommerce.md)
* [Artikel mit Anleitungen für die Konfiguration](/help/sites-deploying/ht-deploy.md)
* [Web-Konsole](/help/sites-deploying/web-console.md)
* [Fehlerbehebung bei Replikationsproblemen](/help/sites-deploying/troubleshoot-rep.md)
* [Best Practices](/help/sites-deploying/best-practices.md)
* [Bereitstellen von Communities](/help/communities/deploy-communities.md)
* [Einführung in die AEM-Plattform](/help/sites-deploying/platform.md)
* [Leistungsrichtlinien](/help/sites-deploying/performance-guidelines.md)
* [Erste Schritte mit AEM Mobile](/help/mobile/getting-started-aem-mobile.md)
* [Was ist AEM Screens? ](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/aem-screens-introduction.html?lang=de)
