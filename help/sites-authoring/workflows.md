---
title: Arbeiten mit Workflows
seo-title: Working with Workflows
description: Mit Workflows in AEM können Sie eine Reihe von Schritten automatisieren, die auf einer Seite oder einem Asset ausgeführt werden.
seo-description: Workflows in AEM allow you to automate a series of steps that are performed on a page or asset.
uuid: c4442d2a-c6b0-49d4-a1ce-384017c45bf0
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 7cb99618-d903-4cfb-b0d9-b23d189f6e78
exl-id: 8d318fd5-3d8f-4144-95c8-d90685378a91
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 34%

---

# Arbeiten mit Workflows{#working-with-workflows}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

AEM Workflows ermöglichen die Automatisierung einer Reihe von Schritten, die auf (einer oder mehreren) Seiten und/oder Assets ausgeführt werden.

Beispielsweise muss beim Veröffentlichen ein Editor den Inhalt überprüfen, bevor eine oder ein Site-Admindie Seite aktiviert. Ein Workflow, der dieses Beispiel automatisiert, benachrichtigt jeden Teilnehmer, wenn es Zeit ist, die erforderlichen Arbeiten auszuführen:

1. Der Autor wendet den Workflow auf die Seite an.
1. Der Editor erhält ein Arbeitselement, das angibt, dass er den Seiteninhalt überprüfen muss. Wenn sie fertig sind, geben sie an, dass ihr Arbeitselement abgeschlossen ist.
1. Der Site-Administrator erhält dann ein Arbeitselement, das die Aktivierung der Seite anfordert. Wenn sie fertig sind, geben sie an, dass ihr Arbeitselement abgeschlossen ist.

In der Regel:

* Inhaltsautoren wenden Workflows auf Seiten an und nehmen an Workflows teil.
* Die von Ihnen verwendeten Workflows sind spezifisch für die Geschäftsprozesse Ihres Unternehmens.

Die folgenden Seiten behandeln:

* [Anwenden von Workflows auf Seiten](/help/sites-authoring/workflows-applying.md)
* [Teilnehmen an Workflows](/help/sites-authoring/workflows-participating.md)
