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
role: Administrator
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 9%

---


# Konfiguration von Aktivierungsfunktionen {#configuring-enablement-features}

## Überblick {#overview}

Die Aktivierungsfunktionen bieten die Möglichkeit, [Aktivierungsgemeinschaften](overview.md#enablement-community) zu erstellen.

* Für diese Funktion sind zusätzliche Lizenzen für die Verwendung in einer Produktions-Umgebung erforderlich.

Die Verwendung der Aktivierungsfunktionen erfordert Folgendes:

Installation von:

* **Das**
SCORMSharable Content Object Reference Model (SCORM) ist eine Sammlung von Standards und Spezifikationen für e-Learning. SCORM definiert auch, wie Inhalte in eine übertragbare ZIP-Datei verpackt werden können.

* ****
MySQLMySQL ist eine relationale Datenbank, die in erster Linie für die SCORM-Verfolgung und die Berichte-Daten für die Aktivierung sowie Tabellen zur Verfolgung des Videofortschritts verwendet wird. Für das SCORM for enable feature pack ist der JDBC-Treiber für MySQL erforderlich.

* **FFmpegFFmpeg**
ist eine Lösung zum Konvertieren und Streaming von Audio und Video und wird, falls installiert, für die ordnungsgemäße Transkodierung von  [Video-Assets](../../help/sites-authoring/default-components-foundation.md#video) verwendet. Bei Aktivierungs-Communities wird sie in der Autorenressource verwendet, um Metadaten für hochgeladene Umgebung abzurufen und eine Miniaturansicht zu generieren, die bei der Auflistung der Ressource angezeigt werden soll.

Einrichtung von:

* **Community-**
ManagerFür Communities, die für die Aktivierung gedacht sind, nur Mitglieder der 
`Community Enablement Managers` Benutzergruppen kann die Rolle zugewiesen werden, zu  `*Community Site* Enablement Manager`deren Berechtigungen die Inhaltserstellung, Zuweisungen und Mitgliederverwaltung in der Umgebung &quot;Veröffentlichen&quot;gehören können.

Optionale Konfiguration von:

* **Adobe**
AnalyticsIntegration mit Adobe Analytics bietet umfassende Funktionen für Berichte und unterstützt die Video Heartbeat-Ergänzung zu Analytics.

* **Dispatcher**

## Konfigurationsschritte {#configuration-steps}

Im Folgenden werden die Schritte beschrieben, die für die Aktivierung von Communities erforderlich sind.

Jeder Schritt ist mit der Dokumentation verknüpft, die die erforderlichen Details enthält.

**In allen Autoren-/Veröffentlichungsinstanzen:**

1. **[JDBC-Treiber für](deploy-communities.md#jdbc-driver-for-mysql)**
MySQLUse Web Console (Pakete) installieren: Installieren Sie  *http://localhost:4502/system/console/*
von PaketenInstallieren Sie  ** vor der Installation des SCORM-Pakets

1. **[SCORM-](deploy-communities.md#scorm-package)**
Paket installierenPackage Manager verwenden: 
*http://localhost:4502/crx/packmgr/*

**Auf jedem Server:**

1. **[MySQL, MySQL Workbench installieren](mysql.md)**

1. **[MySQL-](mysql.md#database-setup)**
Datenbanken installierenSQL-Skripten ausführen, die von der Autoreninstanz heruntergeladen wurden
\
   MySQL Workbench verwenden

**Auf demselben Server, auf dem die Autoreninstanz gehostet wird:**

1. **[install FFmpeg](ffmpeg.md)**

**In allen Autoren-/Veröffentlichungsinstanzen:**

1. **[JDBC Connections](mysql.md#configure-jdbc-connections)**
poolVerwenden Sie Web Console (configMgr): 
*http://localhost:4502/system/console/configMgr*

1. **[SCORM-Engine-](mysql.md#aem-communities-scormengine-service)**
Dienst konfigurierenWeb-Konsole verwenden (configMgr): 
*http://localhost:4502/system/console/configMgr*

1. **[CSRF-](mysql.md#adobe-granite-csrf-filter)**
Filter konfigurierenWeb-Konsole verwenden (configMgr): 
*http://localhost:4502/system/console/configMgr*

**Auf Autoreninstanz:**

1. (*optional*) **[Konfigurieren des Analytics-Dienstes](analytics.md)**
Verwenden Sie Tools, Bereitstellung, Cloud Services-Konsole: 
*http://localhost:4502/etc/cloudservices/sitecatalyst.html*

1. **[configure](ffmpeg.md#configure-ffmpeg-transcoding-service)**
FFmpegVerwenden der Konsole &quot;Arbeitsablauf/Modelle&quot;

1. **[Tunnel-](deploy-communities.md#tunnel-service-on-author)**
DienstWeb-Konsole verwenden (configMgr): 
*http://localhost:4502/system/console/configMgr*

1. **[Community-](users.md#creating-community-members)** Administratoren erstellenFür die Authoring-Umgebung verwenden Sie die Classic-UI-Sicherheitskonsole:  *http://localhost:4502/*
useradmincreate-Benutzer mit Pfad = /home/users/community

   * hinzufügen Mitglieder zu folgenden Gruppen:

      * Community-Aktivierungsmanager
      * Communities Administratoren

## Dispatcher {#dispatcher}

Wenn die Bereitstellung [AEM Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html) enthält, müssen die Abschnitte `clientheader`und `filter`geändert werden, damit die Aktivierungsfunktionen ordnungsgemäß funktionieren. Siehe [Konfigurieren von Dispatcher für Communities](dispatcher.md#enablement).
