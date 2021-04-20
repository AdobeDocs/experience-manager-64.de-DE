---
title: Verarbeiten Sie Assets, um Geschäftsprozesse durchzuführen, Prüfungen durchzuführen, Compliance zu erzielen und die Grundanforderungen zu erfüllen.
description: Asset-Verarbeitung zum Konvertieren von Formaten, Erstellen von Darstellungen, Verwalten von Assets, Überprüfen von Assets und Ausführen von Workflows.
contentOwner: AG
feature: Workflow,Renditions
role: Business Practitioner,Administrator
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '1052'
ht-degree: 28%

---


# Digitale Assets verarbeiten {#process-assets}

[!DNL Adobe Experience Manager Assets] ermöglicht Ihnen, Ihre digitalen Assets auf vielfältige Weise zu bearbeiten, um eine robuste Asset-Verarbeitung zu ermöglichen. Sie können die verfügbaren Verarbeitungsmethoden verwenden oder die Methoden erweitern, um den Abschluss von End-to-End-Geschäftsprozessen mithilfe von Audits und Compliance, Erkennung und Verteilung von digitalen Assets und grundlegender Zuverlässigkeit zu gewährleisten. Sie können dies alles tun und dabei die erforderliche Größe und Anpassung erreichen.

## Verstehen Sie Workflows {#understand-workflows}

Bei der Asset-Verarbeitung verwendet [!DNL Experience Manager] Workflows. Workflows helfen bei der Automatisierung der Geschäftslogik oder der Aktivitäten. Granuläre Schritte zum Ausführen bestimmter Aufgaben werden standardmäßig bereitgestellt, und Entwickler können eigene benutzerdefinierte Schritte erstellen. Diese Schritte können in einer logischen Reihenfolge kombiniert werden, um Workflows zu erstellen. Ein Workflow kann beispielsweise automatisch Wasserzeichen auf hochgeladene Bilder anwenden, die auf bestimmten Kriterien basieren, wie z. B. in das Bild eingebettete Metadaten, hochgeladene Ordner, Auflösung des Bildes usw. Ein weiteres Beispiel ist ein Workflow, der so konfiguriert wurde, dass er Wasserzeichenbilder auf eine Weise und gleichzeitig auf mehrere Asset-Management-Anforderungen abzielt, z. B. das Hinzufügen von Metadaten, das Erstellen von Darstellungen, das Hinzufügen intelligenter Tags zur Asset-Erkennung, das Veröffentlichen in einem Datenspeicher, das Festlegen von Zugriffsberechtigungen für Benutzer usw.

## Workflows in Experience Manager {#default-workflows} verfügbar

Standardmäßig werden alle hochgeladenen Assets mit dem Arbeitsablauf [!UICONTROL DAM Update Asset] verarbeitet. Der Arbeitsablauf wird für jedes hochgeladene Asset ausgeführt und führt grundlegende Aufgaben zur Asset-Verwaltung durch, wie z. B. Generierung von Ausgabeformaten, Schreibback von Metadaten, Extraktion von Seiten, Extraktion von Medien und Transkodierung.

Die verschiedenen Workflow-Modelle, die standardmäßig verfügbar sind, finden Sie unter [!UICONTROL Werkzeuge > Workflow > Modelle] in [!DNL Experience Manager].

![Einige der standardmäßigen Arbeitsabläufe](assets/aem-default-workflows.png)

*Abbildung: Einige der standardmäßigen Arbeitsabläufe sind in verfügbar  [!DNL Experience Manager].*

## Anwenden von Workflows auf Assets {#applying-workflows-to-assets}

Das Anwenden von Workflows auf digitale Assets entspricht dem Vorgehen bei den Seiten einer Website. Eine vollständige Anleitung zum Erstellen und Verwenden von Workflows finden Sie unter [Beginn Workflows](/help/sites-authoring/workflows-participating.md).

Nutzen Sie Workflows in digitalen Assets, um das Asset zu aktivieren oder Wasserzeichen zu erstellen. Viele Workflows für Assets werden automatisch aktiviert. Beispielsweise wird der Workflow, mit dem nach der Bearbeitung eines Bildes automatisch ein Ausgabeformat erstellt wird, automatisch aktiviert.

>[!NOTE]
>
>Wenn in der Touch-aktivierten Benutzeroberfläche kein Workflow verfügbar ist, wie [!UICONTROL Anfrage zur Aktivierung] und [!UICONTROL Anfrage zur Deaktivierung], finden Sie unter [Workflow-Modelle erstellen](/help/sites-developing/workflows-models.md#make-workflow-models-available-in-touchui) weitere Informationen.

## Anwenden eines Workflows auf ein AEM-Asset {#apply-a-workflow-to-an-aem-asset}

<!-- 
TBD: Add animated GIF for these steps instead of all these screenshots.
-->

Gehen Sie wie folgt vor, um einen Workflow auf ein Asset anzuwenden:

1. Navigieren Sie zum Speicherort des Assets, für das Sie einen Workflow erstellen möchten, und klicken Sie auf das Asset, um die Asset-Seite zu öffnen.

1. Navigieren Sie zum Speicherort des Assets, für das Sie einen Workflow erstellen möchten, und klicken Sie auf das Asset, um die Asset-Seite zu öffnen. Wählen Sie **[!UICONTROL Zeitschiene]** aus dem Menü, um die Zeitschiene anzuzeigen.

   ![timeline-2](assets/timeline-2.png)

1. Klicken Sie unten auf **[!UICONTROL Aktionen]**, um die Liste der für das Asset verfügbaren Aktionen zu öffnen.

1. Klicken Sie in der Liste auf **[!UICONTROL Beginn-Workflow]**.

1. Wählen Sie im Dialogfeld **[!UICONTROL Beginn-Workflow]** ein Workflow-Modell aus der Liste.

   ![chlimage_1-50](assets/chlimage_1-50.png)

1. (Optional) Geben Sie einen Titel für den Workflow an, der für den Verweis auf die Workflow-Instanz verwendet werden kann.

   ![chlimage_1-51](assets/chlimage_1-51.png)

1. Klicken Sie auf **[!UICONTROL Beginn]** und dann auf **[!UICONTROL Fortfahren]** im Dialogfeld, um dies zu bestätigen. Jeder Schritt des Workflows wird in der Zeitleiste als ein Ereignis angezeigt.

   ![chlimage_1-52](assets/chlimage_1-52.png)

## Anwenden eines Workflows auf mehrere Assets {#applying-a-workflow-to-multiple-assets}

1. Navigieren Sie in der Assets-Konsole zum Verzeichnis der Assets, für die Sie einen Workflow starten möchten, und wählen Sie die Assets aus. Wählen Sie **[!UICONTROL Zeitschiene]** aus dem Menü, um die Zeitschiene anzuzeigen.

   ![chlimage_1-136](assets/chlimage_1-136.png)

1. Klicken Sie unten auf **[!UICONTROL Aktionen]**.

1. Klicken Sie auf **[!UICONTROL Workflow starten]**. Wählen Sie im Dialogfeld **[!UICONTROL Workflow starten]** ein Workflow-Modell aus der Liste.

   ![chlimage_1-138](assets/chlimage_1-138.png)

1. (Optional) Geben Sie einen Titel für den Workflow an, der für den Verweis auf die Workflow-Instanz verwendet werden kann.

1. Klicken Sie auf **[!UICONTROL Starten]** und anschließend im Dialogfeld auf **[!UICONTROL Bestätigen]**. Der Workflow wird für alle Assets ausgeführt, die Sie ausgewählt haben.

## Anwenden eines Workflows auf mehrere Ordner {#applying-a-workflow-to-multiple-folders}

Die Vorgehensweise zum Anwenden eines Workflows auf mehrere Ordner ähnelt der Vorgehensweise beim Anwenden eines Workflows auf mehrere Assets. Wählen Sie die Ordner in der Assets-Konsole aus und führen Sie die Schritte 2-7 des Verfahrens [Einen Workflow auf mehrere Assets anwenden](assets-workflow.md#applying-a-workflow-to-multiple-assets) aus.

## Anwenden eines Workflows auf eine Sammlung {#applying-a-workflow-to-a-collection}

Weitere Informationen zum Anwenden eines Workflows auf eine Sammlung finden Sie unter [Anwenden eines Workflows auf eine Sammlung](managing-collections-touch-ui.md#running-a-workflow-on-a-collection).

## Automatisches Beginn eines Workflows zur bedingten Verarbeitung von Assets{#auto-execute-workflow-on-some-assets}

Administratoren können Arbeitsabläufe so konfigurieren, dass Assets auf der Grundlage vordefinierter Bedingungen automatisch ausgeführt und verarbeitet werden. Diese Funktion ist beispielsweise nützlich für Benutzer und Marketingfachleute, um einen benutzerdefinierten Workflow für bestimmte Ordner zu erstellen. Angenommen, alle Assets aus dem Foto einer Agentur können mit einem Wasserzeichen versehen oder alle von einem freiberuflichen Anbieter hochgeladenen Assets können verarbeitet werden, um bestimmte Darstellungen zu erstellen.

Für ein Workflow-Modell können Benutzer einen Workflow-Starter erstellen, der es ausführt. Ein Workflow-Starter überwacht Änderungen im Inhalts-Repository und führt den Workflow aus, wenn die vordefinierten Bedingungen erfüllt sind. Administratoren können Marketingexperten Zugriff gewähren, um die Workflows zu erstellen und den Starter zu konfigurieren. Benutzer können den standardmäßigen Arbeitsablauf [!UICONTROL DAM Update Asset] ändern, um die zusätzlichen Schritte hinzuzufügen, die zur Verarbeitung bestimmter Assets erforderlich sind. Der Workflow wird für alle neu hochgeladenen Assets ausgeführt. Verwenden Sie einen der folgenden Ansätze, um die Ausführung der zusätzlichen Schritte für bestimmte Assets zu beschränken:

* Erstellen Sie eine Kopie des Workflows [!UICONTROL DAM Update Asset] und ändern Sie ihn, um es in einer bestimmten Ordnerhierarchie auszuführen. Dieser Ansatz ist für einige Ordner nützlich.
* Die zusätzlichen Verarbeitungsschritte können mit einem [OR split](/help/sites-developing/workflows-step-ref.md#or-split) hinzugefügt werden, sofern dies bedingt für so viele Ordner wie erforderlich gilt.

## Best Practices und Einschränkungen {#best-practices-limitations-tips}

* Berücksichtigen Sie beim Entwickeln von Workflows Ihre Anforderungen für alle Arten von Ausgabedarstellungen. Wenn Sie der Meinung sind, dass eine Ausgabedarstellung in Zukunft nicht erforderlich sein wird, entfernen Sie den Erstellungsschritt aus dem Workflow. Ausgabedarstellungen können später nicht mehr stapelweise gelöscht werden. Unerwünschte Ausgabedarstellungen können nach längerer Nutzung von [!DNL Experience Manager] viel Speicherplatz beanspruchen. Bei einzelnen Assets können Sie Ausgabedarstellungen manuell aus der Benutzeroberfläche entfernen. Bei mehreren Assets können Sie [!DNL Experience Manager] so anpassen, dass entweder bestimmte Ausgabedarstellungen gelöscht oder die Assets gelöscht und die gelöschten Assets erneut hochgeladen werden.
* Der Arbeitsablauf für [!UICONTROL DAM-Aktualisierung von Asset] umfasst standardmäßig einige Schritte zum Erstellen von Miniaturbildern und Webdarstellungen. Wenn Standarddarstellungen aus dem Workflow entfernt werden, wird die Benutzeroberfläche von [!DNL Assets] nicht richtig dargestellt.

>[!MORELIKETHIS]
>
>* [Workflows](/help/sites-authoring/workflows.md)
>* [Erstellen von Workflow-Modellen und Erweitern der Workflow-Funktionalität](/help/sites-developing/workflows.md)
>* [Methoden zum Ausführen Workflows](/help/sites-administering/workflows-starting.md)
>* [Best Practices für Arbeitsabläufe](/help/sites-developing/workflows-best-practices.md)
>* [Community-Artikel zum Ändern von Assets mithilfe des Workflows](https://helpx.adobe.com/experience-manager/using/modify_asset_workflow.html)

