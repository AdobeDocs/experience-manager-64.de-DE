---
title: Grundlagen der Ordnerstruktur
seo-title: Grundlagen der Ordnerstruktur
description: Grundlegendes zur Ordnerstruktur von AEM Forms Workspace-Quellcode zur Anpassung.
seo-description: Grundlegendes zur Ordnerstruktur von AEM Forms Workspace-Quellcode zur Anpassung.
uuid: ee844f89-887e-4f07-9db3-389859baa374
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 7427858d-8eec-423d-a0a9-444140420620
exl-id: 192c436d-a507-4883-bd68-a6863a6664e0
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 66%

---

# Grundlagen der Ordnerstruktur  {#understanding-the-folder-structure}

AEM Forms Workspace-Komponenten basieren auf einer MVC-Architektur mit Backbone. Jede Komponente verfügt über eine Datei für:

* Das Modell, das die Geschäftslogik enthält.
* Die Vorlage als HTML-Datei mit Steuerelementen der Benutzeroberfläche.
* Die Ansicht, die als Steuerungklasse für die Vorlage fungiert.

Die Elemente für alle Komponenten werden in der unten beschriebenen Ordnerstruktur gespeichert. Um auf die Assets zuzugreifen, melden Sie sich bei CRXDE Lite an und navigieren Sie zu `/libs/ws/js/runtime/`.

**** modelsEnthält Backbone-Modelle.

**** viewsEnthält Backbone-Ansichten.

**** templatesEnthält nur die HTML-Vorlagen für die Komponenten.

**** routesEnthält universelle Routen. Der Ordner „templates“ unter „routes“ enthält den HTML-Code und die Verweise auf die Komponenten.

**** servicesEnthält die Dienstschnittstelle zum Aufrufen von Adobe Experience Manager-Server-APIs am REST-Endpunkt.

**** utilEnthält allgemeine Dienstprogramme, die von mehreren Komponenten verwendet werden können.
