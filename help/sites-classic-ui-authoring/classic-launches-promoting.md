---
title: Weiterleiten von Launches
seo-title: Promoting Launches
description: Sie müssen Launch-Seiten weiterleiten, damit der Inhalt vor der Veröffentlichung wieder in die Quelle (Produktion) verschoben wird. Beim Weiterleiten einer Launch-Seite wird die entsprechende Seite der Quellseiten mit dem Inhalt der weitergeleiteten Seite aktualisiert.
seo-description: You need to promote launch pages to move the content back into the source (production) before publishing. When a launch page is promoted, the corresponding page of the source pages is replaced with the content of the promoted page.
uuid: 91f1c6ac-8c4e-4459-aaab-feaa32befc45
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 8d38c6f7-8fea-4d27-992d-03b604b9541f
legacypath: /content/docs/en/aem/6-0/author/site-page-features/launches
exl-id: 793c44fa-9dd1-45f2-b1ab-219b436fcb54
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 95%

---

# Weiterleiten von Launches{#promoting-launches}

Sie müssen Launch-Seiten weiterleiten, damit der Inhalt vor der Veröffentlichung wieder in die Quelle (Produktion) verschoben wird. Beim Weiterleiten einer Launch-Seite wird die entsprechende Seite der Quellseiten mit dem Inhalt der weitergeleiteten Seite aktualisiert. Die folgenden Optionen sind beim Weiterleiten einer Launch-Seite verfügbar:

* Soll nur die aktuelle Seite weitergeleitet werden oder der gesamte Launch?
* Sollen die untergeordneten Seiten der aktuellen Seite weitergeleitet werden?
* Soll der vollständige Launch weitergeleitet werden oder die nur Seiten, die geändert wurden?

## Weiterleiten von Launch-Seiten {#promoting-launch-pages}

Führen Sie beim Bearbeiten der weiterzuleitenden Launch-Seite die folgenden Schritte aus, um Seiten weiterzuleiten:

1. Klicken Sie im Sidekick auf der Registerkarte **Seite** auf **Launch bewerben**.
1. Geben Sie die Seiten an, die weitergeleitet werden sollen:

   * (Standard) Um nur die aktuelle Seite weiterzuleiten, wählen Sie **Weiterleiten von Seitenänderungen an die Produktionsversion**.
   * Um auch die untergeordneten Seiten der aktuellen Seite weiterzuleiten, wählen Sie **Unterseiten einschließen**.
   * Um alle Seiten im Launch weiterzuleiten, wählen Sie **Vollständigen Launch in Produktionsversion weiterleiten**.

1. Um die Produktionsseiten einem Workflow-Paket hinzuzufügen, wählen Sie zunächst **Zu Workflow-Paket hinzufügen** und wählen Sie dann das Workflow-Paket.
1. Klicken Sie auf **Bewerben**.

## Bearbeiten weitergeleiteter Seiten mit einem AEM-Workflow {#processing-promoted-pages-using-aem-workflow}

Verwenden Sie Workflow-Modelle, um eine Stapelverarbeitung weitergeleiteter Launch-Seiten durchzuführen:

1. Erstellen Sie ein Workflow-Paket.
1. Wenn Autoren Launch-Seiten weiterleiten, speichern sie sie in einem Workflow-Paket.
1. Starten Sie ein Workflow-Modell mit dem Paket als Payload.

Um einen Workflow automatisch zu starten, wenn Seiten weitergeleitet werden, [konfigurieren Sie einen Workflow-Starter](/help/sites-administering/workflows-starting.md#workflows-launchers) für den Paketknoten.

Sie können z. B. automatisch Seitenaktivierungsanfragen generieren, wenn Autoren Launches-Seiten weiterleiten. Konfigurieren Sie einen Workflow-Starter, um den Workflow zur Anfrageaktivierung zu starten, wenn der Paketknoten geändert wird.

![chlimage_1-136](assets/chlimage_1-136.png)
