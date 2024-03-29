---
title: Grundlegende Konfigurationskonzepte
seo-title: Basic Configuration Concepts
description: Erfahren Sie, wie Sie AEM konfigurieren.
seo-description: Learn how to configure AEM.
uuid: edcdd4bd-5917-417e-8913-40d488383ea9
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: configuring
content-type: reference
discoiquuid: 2673ea92-1651-4b1b-9aac-f4ba8b36782e
feature: Configuring
exl-id: 758ef6d2-2eba-44ef-8e65-18258c4e9123
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2180'
ht-degree: 38%

---

# Grundlegende Konfigurationskonzepte{#basic-configuration-concepts}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Alle Parameter von Adobe Experience Manager (AEM) weisen bei der Installation Standardeinstellungen auf. Dadurch ist die Software sofort einsatzbereit. Sie können AEM jedoch für Ihre eigenen spezifischen Anforderungen konfigurieren.

Es gibt viele Aspekte von AEM, die konfiguriert werden können:

* Einige sind [für jede Projektinstallation konfiguriert](#primary-configuration-considerations) und müssen überprüft werden, um festzustellen, ob sie für Ihr Projekt relevant sind oder nicht.
* [Weitere Konfigurationen](#further-configuration-considerations) können häufig, jedoch nicht zwingend sein; im Zusammenhang mit Funktionen oder Systemleistung und -stabilität.
* Andere sind nur für bestimmte optionale Funktionen von AEM erforderlich (diese werden zusammen mit der entsprechenden Funktion dokumentiert).

Abhängig von der spezifischen Konfiguration können diese Änderungen mithilfe der folgenden Methoden vorgenommen werden:

* **Adobe CQ Web-Konsole**

   Dies ist ein Standardspeicherort für die Konfiguration von OSGi-Bundles und -Services.

   Weitere Informationen und empfohlene Vorgehensweisen finden Sie unter [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md).

* **Repository**

   Manche OSGi-Konfigurationen sind im Repository verfügbar. Dadurch wird sichergestellt, dass beim Kopieren oder Replizieren von Repository-Inhalten identische Konfigurationen neu erstellt werden. Sie können auch Ihre eigenen Konfigurationen, abhängig vom Ausführungsmodus, zum Repository hinzufügen.

   Weitere Informationen finden Sie unter [OSGi-Konfiguration im Repository](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository), insbesondere unter [Hinzufügen einer neuen Konfiguration zum Repository](/help/sites-deploying/configuring-osgi.md#adding-a-new-configuration-to-the-repository).

* **Dateisystem**

   Einige wenige Konfigurationsdateien befinden sich im Dateisystem.

* **AEM-WCM**

   Diverse Aspekte können auch im AEM-WCM selbst konfiguriert werden. Häufig wird hierfür die [Tools](/help/sites-administering/tools-consoles.md)-Konsole verwendet, z. B. Replikationsagenten.

>[!NOTE]
>
>Bei der Arbeit mit Adobe Experience Manager gibt es verschiedene Methoden zum Verwalten der Konfigurationseinstellungen für OSGi-Dienste (Konsolen- oder Repository-Knoten).
>
>Siehe [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md) für ausführliche Informationen.

>[!NOTE]
>
>Die Konfiguration von AEM ist unkompliziert, Sie müssen jedoch Folgendes beachten:
>
>Bestimmte Änderungen können erhebliche Auswirkungen auf die Anwendung(en) haben. Stellen Sie daher sicher, dass Sie über das erforderliche Erlebnis und Wissen verfügen, bevor Sie mit der Konfiguration von AEM beginnen, und nehmen Sie nur die Änderungen vor, von denen Sie wissen, dass sie erforderlich sind. Alle Änderungen, die über die OSGi-Konsole vorgenommen werden, sind **sofort** auf das laufende System angewendet werden (kein Neustart erforderlich).

## Überlegungen zur Primären Konfiguration {#primary-configuration-considerations}

Diese Liste beschreibt die Hauptbereiche, die normalerweise für jedes neue Projekt konfiguriert werden. Nicht alle sind erforderlich, aber die Liste muss gelesen und überprüft werden, um zu sehen, was auf Ihr Projekt zutrifft.

Die Liste bietet einen kurzen Überblick über die einzelnen Konfigurationsaspekte sowie Links zu den Seiten, die vollständige Details enthalten.

### Sicherheitscheckliste {#security-checklist}

Einige wichtige Konfigurationsprobleme werden im Abschnitt [Sicherheitscheckliste](/help/sites-administering/security-checklist.md). Lesen Sie sich die Liste durch und ergreifen Sie die für Ihre Installation nötigen Maßnahmen. 

### Konfigurieren der Standard-Benutzeroberfläche - Touch-optimiert oder Classic {#configuring-the-default-ui-touch-optimized-or-classic}

Es gibt zwei Benutzeroberflächen, die in AEM verwendet werden können:

* Die Touch-optimierte Benutzeroberfläche
* Klassische Benutzeroberfläche

Sie können die von Ihnen benötigte Benutzeroberfläche mithilfe von [Root Mapping](/help/sites-deploying/osgi-configuration-settings.md) konfigurieren.

>[!NOTE]
>
>Weitere Informationen zur Auswahl der Benutzeroberflächen finden Sie unter [Auswählen der Benutzeroberfläche](/help/sites-authoring/select-ui.md).

### IPv4 und IPv6 {#ipv-and-ipv}

Alle Elemente der AEM (z. B. Repository, Dispatcher usw.) können sowohl in IPv4- als auch in IPv6-Netzwerken installiert werden.

Der Betrieb ist nahtlos, da keine spezielle Konfiguration erforderlich ist. Bei Bedarf können Sie einfach eine IP-Adresse in dem Ihrem Netzwerktyp entsprechenden Format angeben.

Wenn eine IP-Adresse angegeben werden muss, können Sie (je nach Bedarf) aus den folgenden Optionen auswählen:

* eine IPv6-Adresse

   zum Beispiel `https://[ab12::34c5:6d7:8e90:1234]:4502`

* eine IPv4-Adresse

   zum Beispiel `https://123.1.1.4:4502`

* einen Server-Namen

   zum Beispiel `https://www.yourserver.com:4502`

* der Standardfall von `localhost` wird für IPv4- und IPv6-Netzwerkinstallationen interpretiert

   zum Beispiel `http://localhost:4502`

### Versionsbereinigung {#version-purging}

In einer Standardinstallation erstellt AEM eine neue Version einer Seite oder eines Knotens, sobald Sie eine Seite aktivieren (nach der Aktualisierung des Inhalts). Sie können auf Anfrage auch zusätzliche Versionen erstellen, indem Sie die **Versionierung** Registerkarte des Sidekicks. Alle diese Versionen werden im Repository gespeichert und können bei Bedarf wiederhergestellt werden.

Diese Versionen werden nie gelöscht, sodass die Repository-Größe mit der Zeit zunimmt und daher verwaltet werden muss.

Weitere Informationen hierzu finden Sie unter [Bereinigen der Version](/help/sites-deploying/version-purging.md), insbesondere unter [Versions-Manager](/help/sites-deploying/version-purging.md#version-manager). Hier wird erläutert, wie Sie AEM konfigurieren müssen, um ältere Versionen zu bereinigen, wenn eine neue Version erstellt wird.

### Protokollierung {#logging}

AEM bietet Ihnen die Möglichkeit, Folgendes zu konfigurieren:

* globale Parameter für den zentralen Protokollierungsdienst
* Anforderungsdatenprotokollierung; eine spezielle Protokollierungskonfiguration für Anfrageinformationen
* Spezifische Einstellungen für die einzelnen Dienste; zum Beispiel eine einzelne Protokolldatei und das Format für die Protokollmeldungen

Weitere Informationen finden Sie unter [Protokollierung](/help/sites-deploying/configure-logging.md). 

### Ausführungsmodi {#run-modes}

Mit Ausführungsmodi können Sie Ihre AEM für einen bestimmten Zweck anpassen. z. B. Autor oder Veröffentlichung, Test, Entwicklung oder Intranet usw.

Dies geschieht durch Definition von Kollektionen von Konfigurationsparametern für jeden Ausführungsmodus. Ein Grundbestand an Konfigurationsparametern wird auf alle Ausführungsmodi angewendet. Sie können dann zusätzliche Parameter entsprechend den Anforderungen Ihrer spezifischen Umgebung einstellen. Diese werden dann nach Bedarf angewendet.

Alle Konfigurationseinstellungen werden in einem Repository gespeichert und durch Festlegen der **Ausführungsmodus**.

Siehe [Ausführungsmodi](/help/sites-deploying/configure-runmodes.md) für ausführliche Informationen.

### Single Sign-On {#single-sign-on}

Mithilfe von Single Sign-On (SSO) können Sie durch die einmalige Eingabe Ihrer Zugangsdaten (z. B. Ihres Benutzernamens und Passworts) auf mehrere Systeme zugreifen. Ein separates System (auch als vertrauenswürdiger Authentifizierer bezeichnet) führt die Authentifizierung durch und stellt den Experience Manager die Benutzeranmeldeinformationen zur Verfügung. Experience Manager überprüft und erzwingt die Zugriffsberechtigungen für den Benutzer (d. h. legt fest, auf welche Ressourcen der Benutzer zugreifen darf).

Siehe [Single Sign-On](/help/sites-deploying/single-sign-on.md) für weitere Informationen.

### Ressourcenzuordnung {#resource-mapping}

Die Ressourcenzuordnung wird verwendet, um Umleitungen, Vanity-URLs und virtuelle Hosts für AEM zu definieren.

Diese Zuordnungen können Sie beispielsweise verwenden, um:

* Allen Anfragen das Präfix `/content` voranzustellen, sodass die interne Struktur für Besucher Ihrer Website ausgeblendet wird.
* Eine Umleitung zu definieren, sodass alle Anfragen an die Seite `/content/en/gateway` Ihrer Website zu `https://gbiv.com/` umgeleitet werden.

Siehe [Ressourcenzuordnung](/help/sites-deploying/resource-mapping.md) für weitere Informationen.

### Replikation, Rückwärtsreplikation und Replikationsagenten {#replication-reverse-replication-and-replication-agents}

Replikationsagenten sind von zentraler Bedeutung für AEM als Mechanismus, der verwendet wird, um:

* [Veröffentlichen (aktivieren)](/help/sites-authoring/publishing-pages.md) Inhalt von einem Autor in eine Veröffentlichungsumgebung.
* Explizites Leeren von Inhalten aus dem Dispatcher-Cache.
* Gibt Benutzereingaben (z. B. Formulareingaben) aus der Veröffentlichungsumgebung an die Autorenumgebung zurück (unter Kontrolle der Autorenumgebung).

Weitere Informationen finden Sie unter [Replikation](/help/sites-deploying/replication.md)

### OSGi-Konfigurationseinstellungen {#osgi-configuration-settings}

[OSGi](https://www.osgi.org/) ist ein wesentlicher Bestandteil der Technologien von AEM. Es wird zur Steuerung der zusammengesetzten AEM-Bundles und ihrer Konfiguration verwendet.

Siehe [OSGi-Konfigurationseinstellungen](/help/sites-deploying/osgi-configuration-settings.md) für eine Liste der verschiedenen Bundles, die für die Projektimplementierung relevant sind (aufgelistet nach Bundle). Nicht alle aufgeführten Einstellungen müssen angepasst werden. Einige werden hier nur zum besseren Verständnis von AEM erwähnt.

Bei AEM können Sie die Konfigurationseinstellungen für Dienste dieser Art auf unterschiedliche Weise vornehmen. Informationen zur empfohlenen Vorgehensweise finden Sie unter [Konfigurieren von OSGi.](/help/sites-deploying/configuring-osgi.md).

### LDAP konfigurieren {#configuring-ldap}

Die LDAP-Authentifizierung ist erforderlich, um Benutzer zu authentifizieren, die in einem (zentralen) LDAP-Ordner wie Active Directory gespeichert sind. Dies reduziert den Aufwand für die Verwaltung von Benutzerkonten.

Die LDAP-Authentifizierung erfolgt auf Repository-Ebene, sie wird also direkt vom Repository durchgeführt. Weitere Informationen finden Sie unter [Konfigurieren von LDAP mit AEM](/help/sites-administering/ldap-config.md).

Informationen zur Benutzerverwaltung in AEM (einschließlich der Zuweisung von Zugriffsrechten) finden Sie unter [Benutzerverwaltung und Sicherheit](/help/sites-administering/security.md).

### Konfigurieren des Dispatchers {#configuring-the-dispatcher}

Der Dispatcher ist das Caching- und/oder Lastenausgleichstool der Adobe. Die Verwendung des Dispatchers hilft auch, Ihren AEM-Server vor Angriffen zu schützen. Daher können Sie die Sicherheit Ihrer AEM-Instanz erhöhen, indem Sie den Dispatcher in Verbindung mit einem Webserver der Unternehmensklasse verwenden.

Weitere Informationen zur Konfiguration finden Sie unter [Dispatcher](https://helpx.adobe.com/de/experience-manager/dispatcher/using/dispatcher.html), insbesondere unter [Konfigurieren des Dispatchers](https://helpx.adobe.com/de/experience-manager/dispatcher/using/dispatcher-configuration.html).

### Konfigurieren von AEM LiveCycle Connector {#configuring-aem-livecycle-connector}

Mit der Veröffentlichung von AEM Doc Services und AEM Doc Security haben wir jetzt die Möglichkeit, mithilfe der LiveCycle Doc Services ein XFA-Formular zu erstellen, ein Dokument in das PDF-Format umzuwandeln und ein Dokument durch eine Richtlinie zu schützen. Weitere Informationen hierzu finden Sie unter [AEM LiveCycle Connector](https://helpx.adobe.com/de/livecycle/help/aem/aem-livecycle-connector.html).

### Auftragsabladung und Topologieverwaltung {#job-offloading-and-topology-administration}

[Abladung](/help/sites-deploying/offloading.md) verteilt Verarbeitungsaufgaben auf Experience Manager-Instanzen in einer Topologie. Mit der Abladung können Sie bestimmte Experience Manager-Instanzen zur Durchführung bestimmter Verarbeitungsarten verwenden. Durch eine spezialisierte Verarbeitung können Sie die Nutzung der verfügbaren Serverressourcen maximieren.

Topologien sind lose verknüpfte Experience Manager-Cluster, die an der Abladung beteiligt sind. Ein Cluster besteht aus einer oder mehreren Experience Manager-Serverinstanzen (eine Instanz gilt als Cluster).

Weitere Informationen zum Anzeigen oder Ändern der Topologiemitgliedschaft finden Sie unter [Verwalten von Topologien](/help/sites-deploying/offloading.md#administering-topologies) Abschnitt.

### Konfigurieren der Begrüßungskonsole {#configuring-the-welcome-console}

Die Begrüßungskonsole der klassischen Benutzeroberfläche bietet eine Liste von Links zu den verschiedenen Konsolen und Funktionen in AEM.

Es ist möglich, die sichtbaren Links zu konfigurieren, siehe [Konfigurieren der Begrüßungskonsole](/help/sites-developing/customizing-the-welcome-console.md) für weitere Informationen.

### Konfigurieren zur Leistungsoptimierung {#configuring-for-performance}

[Leistung](/help/sites-deploying/configuring-performance.md) ist der Schlüssel zu Ihrem Projekt. Bestimmte Aspekte von AEM (bzw. des zugrunde liegenden Repositorys) können so konfiguriert werden, dass die Leistung optimiert wird.

Siehe [Konfiguration für Leistung](/help/sites-deploying/configuring-performance.md#configuring-for-performance) für weitere Informationen.

<!--delete ### Scaling {#scaling}

Scaling a CQ installation correctly depends greatly on the details of your particular use case. A detailed discussion of solution patterns for various situations can be found in [Scaling CQ](/help/sites-deploying/scaling.md).-->

### Freigegebener Datenspeicher {#shared-data-store}

Der Datenspeicher des Repositorys wird verwendet, um gespeicherte Daten großer Binärdateien aus dem Repository in einen separaten Bereich abzuladen. Dadurch werden mehrere Instanzen derselben Binärdatei (z. B. eines Bildes) innerhalb der Repository-Struktur nur einmal gespeichert.

Diese Funktion &quot;einmal speichern, mehrmals referenzieren&quot;kann erweitert werden, um nicht nur eine einzige Repository-Struktur, sondern vollständig separate Repositorys bereitzustellen, indem der Datenspeicher jedes Repositorys so konfiguriert wird, dass er auf denselben Speicherort des freigegebenen Dateisystems verweist.

Ein solcher Datenspeicher kann zwischen verschiedenen Knoten im selben Cluster, verschiedenen Veröffentlichungs- und/oder Autoreninstanzen in derselben Installation oder sogar völlig separaten Instanzen in verschiedenen Installationen freigegeben werden.

Weitere Informationen finden Sie unter [Konfigurieren von Datenspeichern und Knotenspeichern](/help/sites-deploying/data-store-config.md).

## Weitere Konfigurationsaspekte {#further-configuration-considerations}

### Aktivieren von HTTP über SSL {#enabling-http-over-ssl}

Sie können HTTP über SSL aktivieren, um sicherere Verbindungen zu Ihren Servern herzustellen.

Siehe [Aktivieren von HTTP über SSL](/help/sites-administering/ssl-by-default.md) für weitere Informationen.

### AEM-Portale und Portlets {#aem-portals-and-portlets}

Ein Portal ist eine Webanwendung, die Personalisierung, Single Sign-On und Inhaltsintegration aus unterschiedlichen Quellen ermöglicht und die Präsentationsschicht von Informationssystemen hostet. Mit der Portlet-Komponente können Sie auch ein Portlet auf der Seite einbetten. Um auf von CQ5 WCM bereitgestellte Inhalte zuzugreifen, kann der Portalserver mit dem Director Portlet CQ5 Portal ausgestattet werden. Dazu installieren, konfigurieren und fügen Sie das Portlet zur Portalseite hinzu.

Weitere Einzelheiten finden Sie unter [Portal und Portlets](/help/sites-administering/aem-as-portal.md).

### Ablauf der Gültigkeit statischer Objekte {#expiration-of-static-objects}

Statische Objekte (z. B. Symbole) ändern sich nicht. Daher sollte das System so konfiguriert werden, dass sie (für einen angemessenen Zeitraum) nicht ablaufen und so unnötigen Traffic reduzieren.

Siehe [Ablauf statischer Objekte](/help/sites-deploying/expiration-static-objects.md) für weitere Informationen.

### Geöffnete Dateien im Java-Prozess {#open-files-in-the-java-process}

Jeder Java-Prozess kann auf Dateien zugreifen - dies erfordert Systemressourcen. Aus diesem Grund wird ein oberes Limit definiert, das angibt, auf wie viele Dateien in jedem Prozess gleichzeitig zugegriffen werden darf. Wenn dieser Wert überschritten wird, kann ein Ausnahmefehler auftreten.

Wenn der AEM-Prozess dieses obere Limit überschreitet, wird die Nachricht „`too many open files`“ in `error.log` angezeigt.

Um solche Ausnahmen zu vermeiden, müssen Sie:

1. Überprüfen Sie, wie viele geöffnete Dateien Ihr AEM verwendet.

   Wie Sie diese Prüfung durchführen, hängt davon ab, auf welcher Plattform Ihre Instanz ausgeführt wird. Hilfsprogramme wie lsof (Unix) oder Process Explorer (Windows) können verwendet werden.

   Dieser Wert sollte bei der Entwicklung und bei Tests aus folgenden Gründen überwacht werden:

   * Zur Bestätigung, dass Dateien ordnungsgemäß geschlossen werden 
   * zur Bestimmung des erforderlichen Maximalwerts (unter verschiedenen Umständen).

1. Legen Sie das zulässige Maximum fest.

   Der neue Wert sollte sowohl für die aktuellen Anforderungen als auch für etwaige künftige Spitzen ausreichend sein. Deshalb ist es ratsam, den Wert für die aktuellen Anforderungen zu verdoppeln.

   Standardmäßig konfiguriert `serverctl` `CQ_MAX_OPEN_FILES` mit `8192`. Dies sollte für die meisten Szenarien ausreichend sein.

### Konfigurieren des Rich-Text-Editors {#configuring-the-rich-text-editor}

Die **Rich-Text-Editor** (**RTE**) bietet Autoren eine Vielzahl von [Funktion](/help/sites-authoring/rich-text-editor.md) zur Bearbeitung des Textinhalts; Bereitstellung von Symbolen, Auswahlfeldern und Menüs für ein WYSIWYG-Erlebnis.

Siehe [Konfigurieren des Rich-Text-Editors](/help/sites-administering/rich-text-editor.md) für weitere Informationen.

### Konfigurieren von Rückgängig-Vorgängen zur Seitenbearbeitung {#configuring-undo-for-page-editing}

Es gibt mehrere Eigenschaften, mit denen das Verhalten der Befehle „Rückgängig machen“ und „Wiederholen“ zur Bearbeitung von Seiten gesteuert werden kann. Diese können konfiguriert werden, siehe [Konfigurieren von Rückgängig für die Seitenbearbeitung](/help/sites-administering/config-undo.md) für weitere Informationen.

### Konfigurieren der Videokomponente {#configuring-the-video-component}

Die [Videokomponente](/help/sites-authoring/default-components-foundation.md#video) ermöglicht es Ihnen, ein vordefiniertes, vordefiniertes Videoelement auf Ihrer Seite zu platzieren.

Damit eine korrekte Transkodierung erfolgt, muss Ihr Administrator [Installieren von FFmpeg](/help/sites-administering/config-video.md#install-ffmpeg) getrennt. Sie können auch [Videoprofile konfigurieren](/help/sites-administering/config-video.md#configure-video-profiles) zur Verwendung mit HTML5-Elementen.

### Konfigurieren und Anpassen von Berichten {#configuring-and-customizing-reports}

Um Ihnen bei der Überwachung und Analyse des Status Ihrer Instanz zu helfen, bietet CQ eine Auswahl von Standardberichten, die für Ihre individuellen Anforderungen konfiguriert werden können:

Siehe [Grundlagen der Berichtsanpassung](/help/sites-administering/reporting.md#the-basics-of-report-customization) für weitere Informationen.

### Konfigurieren von E-Mail-Benachrichtigungen {#configuring-email-notification}

CQ sendet E-Mail-Benachrichtigungen an Benutzer, die:

* Seitenereignisse wie Änderungen oder Replikationen abonniert haben.
* Forumsveranstaltungen abonniert haben.
* Führen Sie einen Schritt in einem Workflow aus.

Siehe [Konfigurieren von E-Mail-Benachrichtigungen](/help/sites-administering/notification.md) für weitere Informationen.

### Aktivieren von Seitenimpressionen {#enabling-page-impressions}

Seitenimpressionen werden im **Impressionen** -Spalte der Siteadmin-Konsole der klassischen Benutzeroberfläche. Um die Erfassung von Seitenimpressionen zu aktivieren, müssen Sie Folgendes konfigurieren:

* In der Veröffentlichungsinstanz:

   * [Day CQ WCM-Seitenstatistiken](/help/sites-deploying/osgi-configuration-settings.md)

* In der Autoreninstanz:

   * [Adobe Page Impressions Tracker](/help/sites-deploying/osgi-configuration-settings.md)

>[!CAUTION]
>
>Die Konfiguration von Adobe Page Impressions Tracker in der Autorenumgebung ermöglicht anonyme Anfragen an den Tracking-Service.
