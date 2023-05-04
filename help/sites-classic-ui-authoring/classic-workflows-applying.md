---
title: Anwenden von Workflows auf Seiten
seo-title: Applying Workflows to Pages
description: Workflows können entweder über die Websites-Konsole oder beim Bearbeiten einer Seite über den Sidekick gestartet werden.
seo-description: Workflows can be started from either the Websites console or, when editing a page, from Sidekick.
uuid: 55f6f1d7-da54-4732-b9ff-b7479622db51
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 22712b73-90f2-4329-b32f-dbb7ce802d1d
exl-id: f10680e5-e8ae-49a0-ae52-3aa1f22b2d3e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 44%

---

# Anwenden von Workflows auf Seiten{#applying-workflows-to-pages}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Wenn Sie den Workflow anwenden, geben Sie die folgenden Informationen an:

* Der anzuwendende Workflow.

   Sie können jeden beliebigen Workflow anwenden (auf den Sie Zugriff haben, wie von Ihrem AEM-Administrator zugewiesen).
* Optional:

   * Ein Kommentar, der Informationen zum Starten des Workflows enthält.
   * Ein Titel, der dabei hilft, die Workflow-Instanz im Posteingang eines Benutzers zu identifizieren.

>[!NOTE]
>
>AEM Administratoren können Workflows mit [mehrere andere Methoden](/help/sites-administering/workflows-starting.md).

## Anwenden von Workflows {#applying-workflows}

Workflows können entweder über die Websites-Konsole oder beim Bearbeiten einer Seite über den Sidekick gestartet werden.

Die Spalte **Status** in der **Websites**-Konsole gibt an, ob ein Workflow auf eine Seite angewendet wurde:

![workflowstatus](assets/workflowstatus.png)

### Starten eines Workflows aus der Websites-Konsole {#starting-a-workflow-from-the-websites-console}

1. Öffnen Sie die Websites-Konsole. ([http://localhost:4502/siteadmin](http://localhost:4502/siteadmin))
1. Wählen Sie in der Website-Struktur das übergeordnete Element der Seite aus, auf die Sie den Workflow anwenden möchten.
1. Wählen Sie in der Seitenliste die Seite aus und klicken Sie auf &quot;Workflow&quot;.
1. Wählen Sie im Dialogfeld Workflow starten den anzuwendenden Workflow aus. Geben Sie optional einen Kommentar und einen Titel ein. Klicken Sie dann auf Start.

### Starten eines Workflows mit dem Sidekick {#starting-a-workflow-using-sidekick}

1. Öffnen Sie die Websites-Konsole.
1. Öffnen Sie die gewünschte Seite.
1. Wählen Sie im Sidekick die Registerkarte Workflow aus.
1. Erweitern Sie das Dialogfeld **Workflow**, um den **Workflow** auszuwählen, und geben Sie optional einen **Workflow-Titel** und einen **Kommentar** ein.

   ![workflowstartsidekick](assets/workflowstartsidekick.png)

1. Klicken Sie auf **Workflow starten**, um eine neue Workflow-Instanz mit den Eigenschaften zu starten, die Sie konfiguriert haben, und mit der aktuellen Seite als Payload. Jetzt wird der Workflow ausgeführt.
