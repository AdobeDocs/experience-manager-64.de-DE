---
title: Grundlagen der Ordnerstruktur
seo-title: Understanding the folder structure
description: Grundlegendes zur Ordnerstruktur des AEM Forms Workspace-Quellcodes zur Anpassung.
seo-description: How to understand the folder structure of AEM Forms workspace source code to customize.
uuid: ee844f89-887e-4f07-9db3-389859baa374
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 7427858d-8eec-423d-a0a9-444140420620
exl-id: 192c436d-a507-4883-bd68-a6863a6664e0
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 46%

---

# Grundlagen der Ordnerstruktur {#understanding-the-folder-structure}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

AEM Forms Workspace-Komponenten basieren auf der MVC-Architektur mit Backbone. Jede Komponente verfügt über eine Datei für:

* Modell, das Geschäftslogik enthält.
* Vorlage: Dies ist eine HTML-Datei, die Steuerelemente für die Benutzeroberfläche enthält.
* Ansicht, die als Controller-Klasse für Vorlage fungiert.

Die Assets für alle Komponenten werden in der unten beschriebenen Ordnerstruktur platziert. Um auf die Elemente zuzugreifen, melden Sie sich bei CRXDE Lite an und navigieren Sie zu `/libs/ws/js/runtime/`.

**models** Enthält Backbone-Modelle.

**views** Enthält Backbone-Ansichten.

**templates** Enthält nur die HTML-Vorlagen für die Komponenten.

**routes** Enthält universelle Routen. Der Ordner „templates“ unter „routes“ enthält den HTML-Code und die Verweise auf die Komponenten.

**services** Enthält die Serviceschnittstelle zum Aufrufen von Adobe Experience Manager-Server-APIs am REST-Endpunkt.

**util** Enthält generische Serviceprogramme, die von mehreren Komponenten verwendet werden können.
