---
title: Architektur von AEM Forms Workspace
seo-title: AEM Forms Workspace Architecture
description: Grundlegende Informationen und Überblick über die Architektur von LiveCycle AEM Forms Workspace.
seo-description: Conceptual information and overview of the architecture of LiveCycle AEM Forms workspace.
uuid: e1a48452-ed44-4ea7-ba38-d961c8faafa5
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: c3a312fb-f684-477d-916d-2d3c99aa7607
exl-id: 30bde8d6-7959-4e4b-a6f4-faf52444e67a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 29%

---

# Architektur von AEM Forms Workspace {#aem-forms-workspace-architecture}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

AEM Forms Workspace ist eine Webanwendung, die auf CRX™ gehostet wird. Wenn Workspace in einem Browser geöffnet wird, wird auf eine CRX-Ressource zugegriffen und die Anwendung wird im Browser als HTML-Seite gerendert.

Das Programm greift auf den AEM Forms-Server an REST-Endpunkten zu, um Folgendes zu tun:

* Abrufen von Benutzeraufgaben, Verarbeiten von Startpunkten, Prozessverlauf und Benutzerinformationen
* Ausführen von Aktionen für Aufgaben
* Abfragen in der Datenbank
* Aktualisieren von Benutzereinstellungen und mehr

Der AEM Forms-Server greift über JDBC auf die AEM Forms-Datenbank zu. Die Datenbank enthält Aufgaben, Prozesse und ihre Instanzen, Benutzer und zugehörige Informationen.

AEM Forms Workspace ist aus modularen JavaScript™-Komponenten aufgebaut, die in anderen Web-Anwendungen individuell angepasst und wiederverwendet werden können. Die Komponenten basieren auf BackBone, einer JavaScript-Bibliothek, die Webanwendungen strukturiert. Ein detaillierter Artikel, der die Interaktion von Komponenten mit BackBone beschreibt, ist [here](/help/forms/using/backbone-interaction.md). Die Organisation der Komponenten in der CRX-Ordnerstruktur wird im Abschnitt [this](/help/forms/using/folder-structure.md) Artikel.

Für AEM Forms Workspace bereitgestellte Pakete:

* `adobe-lc-workspace-pkg-<version>.zip`: Dies ist ein CRX-Paket, das heißt, es kann mithilfe des Package Manager in CRX bereitgestellt werden.
* `adobe-lc-workspace-<version>-src.zip`: Dies ist ein Archiv, das den vollständigen Code von AEM Forms Workspace und Skripte enthält, um die Bereitstellungspakete (Lieferpaket, Debugging-Paket und Entwicklungspaket) zu erstellen.
