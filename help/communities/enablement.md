---
title: Konfiguration von Aktivierungsfunktionen
seo-title: Konfiguration von Aktivierungsfunktionen
description: Aktivierungsfunktionen in Communities konfigurieren
seo-description: Aktivierungsfunktionen in Communities konfigurieren
uuid: 27be3128-1a7d-412e-99a9-6e3b3b0aec1c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 765a3d9b-4552-403e-872c-fdf684ac271d
role: Admin
exl-id: 01cfc774-8ae1-48c0-a7e3-5836c4b39bff
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 9%

---

# Konfiguration von Aktivierungsfunktionen {#configuring-enablement-features}

## Übersicht {#overview}

Die Aktivierungsfunktionen bieten die Möglichkeit, [Aktivierungsgruppen](overview.md#enablement-community) zu erstellen.

* Diese Funktion erfordert zusätzliche Lizenzen für die Verwendung in einer Produktionsumgebung.

Die Verwendung der Aktivierungsfunktionen erfordert Folgendes:

Installation von:

* ****
SCORMSharable Content Object Reference Model (SCORM) ist eine Sammlung von Standards und Spezifikationen für E-Learning. SCORM definiert auch, wie Inhalte in eine übertragbare ZIP-Datei gepackt werden können.

* ****
MySQLMySQL ist eine relationale Datenbank, die hauptsächlich für SCORM-Tracking- und Reporting-Daten zur Aktivierung sowie Tabellen zur Verfolgung des Videofortschritts verwendet wird. Für das SCORM zur Aktivierung des Feature Packs ist der MySQL JDBC-Treiber erforderlich.

* ****
FFmpegFFmpeg ist eine Lösung zum Konvertieren und Streaming von Audio und Video und wird, wenn sie installiert ist, für die ordnungsgemäße Transkodierung von  [Video-Assets](../../help/sites-authoring/default-components-foundation.md#video) verwendet. Für Aktivierungs-Communities wird sie in der Autorenumgebung verwendet, um Metadaten für hochgeladene Ressourcen abzurufen und eine Miniaturansicht zu generieren, die bei der Auflistung der Ressource angezeigt wird.

Einrichtung von:

* **Community-**
ManagerFür Aktivierungsgemeinschaften, nur Mitglieder der 
`Community Enablement Managers` Benutzergruppen kann die Rolle von zugewiesen werden,  `*Community Site* Enablement Manager`deren Berechtigungen die Erstellung von Inhalten, Zuweisungen und Mitgliederverwaltung in der Veröffentlichungsumgebung umfassen können.

Optionale Konfiguration von:

* **Adobe**
Analytics-Integration mit Adobe Analytics bietet umfassende Berichterstellungsfunktionen und unterstützt die Video Heartbeat-Erweiterung zu Analytics.

* **Dispatcher**

## Konfigurationsschritte {#configuration-steps}

Im Folgenden werden die Schritte beschrieben, die für die Aktivierung von Communities erforderlich sind.

Jeder Schritt verlinkt zu einer Dokumentation, die die erforderlichen Details enthält.

**In allen Autoren-/Veröffentlichungsinstanzen:**

1. **[Installieren Sie den JDBC-Treiber für](deploy-communities.md#jdbc-driver-for-mysql)**
MySQLUse Web Console (Bundles): Installieren Sie  *http://localhost:4502/system/console/*
bundlesInstallieren Sie  ** vor der Installation des SCORM-Pakets.

1. **[SCORM-](deploy-communities.md#scorm-package)**
Paket installieren Verwenden Sie Package Manager: 
*http://localhost:4502/crx/packmgr/*

**Auf jedem Server:**

1. **[MySQL, MySQL Workbench installieren](mysql.md)**

1. **[Installieren von MySQL-](mysql.md#database-setup)**
DatenbankenAusführen von SQL-Skripten, die von der Autoreninstanz heruntergeladen wurden
\
   MySQL Workbench verwenden

**Auf derselben Server-Hosting-Autoreninstanz:**

1. **[install FFmpeg](ffmpeg.md)**

**In allen Autoren-/Veröffentlichungsinstanzen:**

1. **[Konfigurieren von JDBC-Verbindungen](mysql.md#configure-jdbc-connections)**
poolUse Web Console (configMgr): 
*http://localhost:4502/system/console/configMgr*

1. **[Konfigurieren des SCORM-Engine-](mysql.md#aem-communities-scormengine-service)**
ServiceVerwenden der Web-Konsole (configMgr): 
*http://localhost:4502/system/console/configMgr*

1. **[CSRF-](mysql.md#adobe-granite-csrf-filter)**
Filter konfigurierenWebkonsole verwenden (configMgr): 
*http://localhost:4502/system/console/configMgr*

**In der Autoreninstanz:**

1. (*optional*) **[Konfigurieren des Analytics-Dienstes](analytics.md)**
Verwenden Sie Tools, Bereitstellung, Cloud Services-Konsole: 
*http://localhost:4502/etc/cloudservices/sitecatalyst.html*

1. **[Konfigurieren der](ffmpeg.md#configure-ffmpeg-transcoding-service)**
FFmpegVerwenden der Konsole &quot;Workflow/Modelle&quot;

1. **[Aktivieren Sie Tunnel](deploy-communities.md#tunnel-service-on-author)**
ServiceVerwenden Sie die Web-Konsole (configMgr): 
*http://localhost:4502/system/console/configMgr*

1. **[Erstellen von Community-](users.md#creating-community-members)** AdministratorenVerwenden Sie für die Autorenumgebung die Sicherheitskonsole der klassischen Benutzeroberfläche:  *http://localhost:4502/*
useradmincreate user(s) with path = /home/users/community

   * Fügen Sie den folgenden Gruppen Mitglieder hinzu:

      * Community-Aktivierungsmanager
      * Communities-Administratoren

## Dispatcher {#dispatcher}

Wenn die Bereitstellung [AEM Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html) enthält, müssen die Abschnitte `clientheader`und `filter`geändert werden, damit die Aktivierungsfunktionen ordnungsgemäß funktionieren. Siehe [Konfigurieren des Dispatchers für Communities](dispatcher.md#enablement).
