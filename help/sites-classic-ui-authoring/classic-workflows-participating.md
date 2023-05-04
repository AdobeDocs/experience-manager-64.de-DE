---
title: Teilnehmen an Workflows
seo-title: Participating in Workflows
description: Workflows enthalten normalerweise Schritte, bei denen eine Person eine Aktivität auf einer Seite oder in einem Asset ausführen muss. Der Workflow wählt einen Benutzer oder eine Gruppe aus, um die Aktivität auszuführen, und weist dieser Person oder Gruppe ein Arbeitselement zu.
seo-description: Workflows typically include steps that require a person to perform an activity on a page or asset. The workflow selects a user or group to perform the activity and assigns a work item to that person or group.
uuid: 04dcc8f2-dc11-430f-b0ae-47ef2cb069a2
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 1d7a4889-82c5-4096-8567-8f66215a8458
exl-id: a4f0f0c4-3050-4348-8d51-2ca91839208c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 49%

---

# Teilnehmen an Workflows{#participating-in-workflows}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Workflows enthalten normalerweise Schritte, bei denen eine Person eine Aktivität auf einer Seite oder in einem Asset ausführen muss. Der Workflow wählt einen Benutzer oder eine Gruppe aus, um die Aktivität auszuführen, und weist dieser Person oder Gruppe ein Arbeitselement zu.

## Bearbeiten von Arbeitselementen {#processing-your-work-items}

Sie können die folgenden Aktionen ausführen, um ein Arbeitselement zu verarbeiten:

* **Fertig stellen**

   Sie können ein Element abschließen, damit der Workflow mit dem nächsten Schritt fortfahren kann.

* **Delegieren**

   Wenn Ihnen ein Schritt zugewiesen wurde, Sie jedoch aus irgendeinem Grund keine Aktion ausführen können, können Sie den Schritt an einen anderen Benutzer oder eine andere Gruppe delegieren.

   Die Benutzer, die für die Zuweisung verfügbar sind, hängen davon ab, wem das Arbeitselement zugewiesen wurde:

   * Wenn das Arbeitselement einer Gruppe zugewiesen wurde, sind die Gruppenmitglieder verfügbar.
   * Wenn das Arbeitselement einer Gruppe zugewiesen und dann an einen Benutzer delegiert wurde, sind die Gruppenmitglieder und die Gruppe verfügbar.
   * Wenn das Arbeitselement einem einzelnen Benutzer zugewiesen wurde, kann es nicht delegiert werden.

* **Schritt zurück**

   Wenn Sie erkennen, dass ein Schritt oder eine Reihe von Schritten wiederholt werden muss, können Sie zu einem vorherigen Schritt zurückkehren. Auf diese Weise können Sie einen früheren Schritt im Workflow zur erneuten Verarbeitung auswählen. Der Workflow kehrt zu dem von Ihnen angegebenen Schritt zurück und fährt dann von dort fort.

## Teilnehmen an einem Workflow {#participating-in-a-workflow}

### Benachrichtigungen über zugewiesene Workflow-Aktionen {#notifications-of-assigned-workflow-actions}

Wenn Ihnen ein Arbeitselement zugewiesen wird (z. B. **Inhalte genehmigen**), werden verschiedene Warnungen und/oder Benachrichtigungen angezeigt:

* Die **Status** -Spalte der Websites-Konsole gibt an, wann sich eine Seite in einem Workflow befindet:

   ![workflowstatus-1](assets/workflowstatus-1.png)

* Wenn Ihnen oder einer Gruppe, der Sie angehören, ein Arbeitselement im Rahmen eines Workflows zugewiesen wird, wird das Arbeitselement in Ihrem AEM-Workflow-Posteingang angezeigt.

   ![workflowinbox](assets/workflowinbox.png)

### Fertigstellen eines Teilnehmerschritts {#completing-a-participant-step}

Nachdem Sie die angegebene Aktion abgeschlossen haben, können Sie das Arbeitselement fertig stellen, damit der Workflow fortgesetzt wird. Führen Sie die folgenden Schritte aus, um das Arbeitselement abzuschließen.

1. Wählen Sie den Workflow-Schritt aus und klicken Sie auf die Schaltfläche **Fertig** in der oberen Navigationsleiste.
1. Wählen Sie im angezeigten Dialogfeld die Option **Nächster Schritt** aus. Damit ist der Schritt gemeint, der als nächster ausgeführt werden soll. Eine Dropdown-Liste zeigt alle entsprechenden Ziele an. A **Kommentar** kann auch eingegeben werden.

   ![workflowcomplete](assets/workflowcomplete.png)

   Die Anzahl der aufgeführten Schritte hängt vom Design des Workflow-Modells ab.

1. Klicken Sie auf **OK**, um die Aktion zu bestätigen.

### Delegieren eines Teilnehmerschritts {#delegating-a-participant-step}

Gehen Sie wie folgt vor, um ein Arbeitselement zu delegieren.

1. Klicken Sie auf **Delegieren** in der oberen Navigationsleiste.
1. Wählen Sie im Dialogfeld mithilfe der Dropdown-Liste die **Benutzer** , um das Arbeitselement zu delegieren. Sie können auch eine **Kommentar**.

   ![workflowdelegate](assets/workflowdelegate.png)

1. Klicken Sie auf **OK**, um die Aktion zu bestätigen.

### Wechseln zu einem vorherigen Teilnehmerschritt {#performing-step-back-on-a-participant-step}

Gehen Sie wie folgt vor, um zurückzutreten.

1. Klicken Sie in der oberen Navigationsleiste auf die Schaltfläche Schritt zurück .
1. Wählen Sie im angezeigten Dialogfeld einen Schritt unter „Vorheriger Schritt“ aus. Dies ist der Schritt, der als nächster ausgeführt werden soll (wobei es sich natürlich um einen Schritt handelt, der weiter vorne im Workflow steht). Eine Dropdown-Liste zeigt alle entsprechenden Ziele an.

   ![screen_shot_2018-08-10at155325](assets/screen_shot_2018-08-10at155325.jpg)

1. Klicken Sie auf „OK“, um die Aktion zu bestätigen.
