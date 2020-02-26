---
title: Anwenden von Workflows zur Verarbeitung digitaler Assets
description: Erfahren Sie, wie Sie Workflows auf Assets, Ordner und Sammlungen in AEM Assets anwenden, um Ihre digitalen Assets zu verarbeiten.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1

---


# Arbeitsabläufe auf Assets anwenden {#applying-workflows-to-assets}

Das Anwenden von Workflows auf digitale Assets entspricht dem Vorgehen bei den Seiten einer Website. Eine vollständige Anleitung zum Erstellen und Verwenden von Workflows in AEM finden Sie unter [Starten von Workflows](../sites-authoring/workflows-participating.md).

Nutzen Sie Workflows in digitalen Assets, um das Asset zu aktivieren oder Wasserzeichen zu erstellen. Viele Workflows für Assets werden automatisch aktiviert. Beispielsweise wird der Workflow, mit dem nach der Bearbeitung eines Bildes automatisch ein Ausgabeformat erstellt wird, automatisch aktiviert.

Wenn ein Workflow in der klassischen Benutzeroberfläche verfügbar ist, aber nicht in der Touch-optimierten Benutzeroberfläche, wie zum Beispiel „Aktivierungsanfrage“ und „Deaktivierungsanfrage“, finden Sie weitere Informationen hierzu unter [Bereitstellen von Workflow-Modellen in der Touch-optimierten Benutzeroberfläche](../sites-developing/workflows-models.md#make-workflow-models-available-in-touchui).

## Anwenden eines Workflows auf ein AEM-Asset {#applying-a-workflow-to-an-aem-asset}

Weitere Informationen zum Anwenden eines Workflows auf ein AEM-Asset finden Sie unter [Starten eines Workflows für ein Asset](managing-assets-touch-ui.md#starting-a-workflow-on-an-asset).

## Anwenden eines Workflows auf mehrere Assets {#applying-a-workflow-to-multiple-assets}

1. Navigieren Sie in der Assets-Konsole zum Verzeichnis der Assets, für die Sie einen Workflow starten möchten, und wählen Sie die Assets aus.
1. Click the GlobalNav icon, and the choose **[!UICONTROL Timeline]** from the menu to display the timeline.

   ![chlimage_1-136](assets/chlimage_1-136.png)

1. Click the **[!UICONTROL Actions]** (arrow) icon at the bottom.

   ![chlimage_1-137](assets/chlimage_1-137.png)

1. Klicken Sie auf **[!UICONTROL Arbeitsablauf starten]**.
1. Wählen Sie im Dialogfeld **[!UICONTROL Workflow beginnen]** ein Workflow-Modell aus der Liste.

   ![chlimage_1-138](assets/chlimage_1-138.png)

1. (Optional) Geben Sie einen Titel für den Workflow an, der für den Verweis auf die Workflow-Instanz verwendet werden kann.
1. Klicken Sie auf **[!UICONTROL Launch]** und dann im Dialogfeld auf **[!UICONTROL Bestätigen]**. Der Workflow wird für alle Assets ausgeführt, die Sie ausgewählt haben.

## Anwenden eines Workflows auf mehrere Ordner {#applying-a-workflow-to-multiple-folders}

Die Vorgehensweise zum Anwenden eines Workflows auf mehrere Ordner ähnelt der Vorgehensweise beim Anwenden eines Workflows auf mehrere Assets. Wählen Sie die Ordner in der Assets-Konsole aus und führen Sie die Schritte 2 bis 7 des Verfahrens [Anwenden eines Workflows auf mehrere Assets](assets-workflow.md#applying-a-workflow-to-multiple-assets) aus.

## Anwenden eines Workflows auf eine Sammlung {#applying-a-workflow-to-a-collection}

For details of applying a workflow to a collection, see [Running a workflow on a collection](managing-collections-touch-ui.md#running-a-workflow-on-a-collection).
