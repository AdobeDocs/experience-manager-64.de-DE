---
title: Arbeiten mit Workflows
seo-title: Working with Workflows
description: AEM Workflows ermöglichen die Automatisierung einer Reihe von Schritten, die auf einer Seite oder einem Asset ausgeführt werden. Beispielsweise muss beim Veröffentlichen ein Editor den Inhalt überprüfen, bevor eine oder ein Site-Admindie Seite aktiviert. Ein Workflow, der dieses Beispiel automatisiert, benachrichtigt jeden Teilnehmer, wenn es Zeit ist, die erforderlichen Arbeiten auszuführen.
seo-description: AEM Workflows allows you to automate a series of steps that are performed on a page or asset. For example, when publishing, an editor has to review the content - before a site administrator activates the page. A workflow that automates this example notifies each participant when it is time to perform their required work.
uuid: 3eb6e790-6589-414a-8e51-33c358f47a73
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: b11f0e4c-4dec-4b66-9f54-a0aa13ac77b9
exl-id: 843cf933-d8a1-407d-9468-1a6409110f81
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 44%

---

# Arbeiten mit Workflows{#working-with-workflows}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

AEM Workflows ermöglichen die Automatisierung einer Reihe von Schritten, die auf einer Seite oder einem Asset ausgeführt werden. Beispielsweise muss beim Veröffentlichen ein Editor den Inhalt überprüfen, bevor eine oder ein Site-Admindie Seite aktiviert. Ein Workflow, der dieses Beispiel automatisiert, benachrichtigt jeden Teilnehmer, wenn es Zeit ist, die erforderlichen Arbeiten auszuführen:

1. Der Autor wendet den Workflow auf die Seite an.
1. Der Editor erhält ein Arbeitselement, das angibt, dass er den Seiteninhalt überprüfen muss. Wenn sie fertig sind, geben sie an, dass ihr Arbeitselement abgeschlossen ist.
1. Der Site-Administrator erhält dann ein Arbeitselement, das die Aktivierung der Seite anfordert. Wenn sie fertig sind, geben sie an, dass ihr Arbeitselement abgeschlossen ist.

In der Regel:

* Inhaltsautoren wenden Workflows auf Seiten an und nehmen an Workflows teil.
* Die von Ihnen verwendeten Workflows sind spezifisch für die Geschäftsprozesse Ihres Unternehmens.

Die folgenden Seiten behandeln:

* [Anwenden von Workflows auf Seiten](/help/sites-classic-ui-authoring/classic-workflows-applying.md)
* [Teilnehmen an Workflows](/help/sites-classic-ui-authoring/classic-workflows-participating.md)
