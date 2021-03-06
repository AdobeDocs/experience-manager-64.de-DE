---
title: AEM Forms Workspace-Architektur
seo-title: AEM Forms Workspace Architecture
description: Grundlegende Informationen und Überblick über die Architektur von LiveCycle AEM Forms workspace.
seo-description: Conceptual information and overview of the architecture of LiveCycle AEM Forms workspace.
uuid: e1a48452-ed44-4ea7-ba38-d961c8faafa5
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: c3a312fb-f684-477d-916d-2d3c99aa7607
exl-id: 30bde8d6-7959-4e4b-a6f4-faf52444e67a
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 79%

---

# AEM Forms Workspace-Architektur {#aem-forms-workspace-architecture}

AEM Forms Workspace ist eine Webanwendung, die auf CRX™ gehostet wird. Wenn Workspace in einem Browser geöffnet wird, wird auf eine CRX-Ressource zugegriffen und die Anwendung als HTML-Seite im Browser angezeigt.

Die Anwendung greift auf den AEM Forms-Server an den REST-Endpunkten zu, um folgende Aktionen auszuführen:

* Abrufen von Benutzeraufgaben, Verarbeiten von Startpunkten, Verlauf und Benutzerinformationen
* Ausführen von Aktionen für die Aufgaben
* Abfrage von Aufgaben in der Datenbank
* Aktualisieren von Benutzereinstellungen und mehr

Der AEM Forms Server greift auf die AEM Forms-Datenbank über JDBC zu. Die Datenbank erfasst Aufgaben, Prozesse und deren Instanzen, Benutzer und zugehörige Informationen.

Der AEM Forms-Arbeitsbereich ist aus modularen JavaScript™-Komponenten aufgebaut, die einzeln angepasst und in anderen Webanwendungen wiederverwendet werden können. Die Komponenten basieren auf Backbone, einer JavaScript-Bibliothek, die eine Struktur für Webanwendungen zur Verfügung stellt. Einen ausführlicher Artikel, der die Interaktion von Komponenten mit Backbone beschreibt, finden Sie [hier](/help/forms/using/backbone-interaction.md). Die Organisation der Komponenten in der CRX-Ordnerstruktur wird in [diesem](/help/forms/using/folder-structure.md) Artikel behandelt.

Pakete, die für AEM Forms Workspace gesendet werden:

* `adobe-lc-workspace-pkg-<version>.zip`: Dies ist ein CRX-Paket, das heißt, es kann mithilfe des Package Manager in CRX bereitgestellt werden.
* `adobe-lc-workspace-<version>-src.zip`: Es ist ein Archiv, das den vollständigen Code von AEM Forms Workspace und Skripten zum Erstellen der Bereitstellungspakete (Lieferpakete, Debug- und Entwicklungspakete) enthält.
