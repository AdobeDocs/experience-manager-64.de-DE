---
title: Weiterleiten von Launches
seo-title: Weiterleiten von Launches
description: 'Sie müssen Launch-Seiten weiterleiten (bewerben), damit der Inhalt vor der Veröffentlichung wieder in die Quelle (Produktion) verschoben wird. '
seo-description: 'Sie müssen Launch-Seiten weiterleiten (bewerben), damit der Inhalt vor der Veröffentlichung wieder in die Quelle (Produktion) verschoben wird. '
uuid: 56483f8f-d66e-4677-a7bd-3b1425625b2b
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 977a3dda-4292-4bd2-bfa5-af4d789d9ef9
legacypath: /content/docs/en/aem/6-0/author/site-page-features/launches
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Weiterleiten von Launches{#promoting-launches}

Sie müssen Launch-Seiten weiterleiten (bewerben), damit der Inhalt vor der Veröffentlichung wieder in die Quelle (Produktion) verschoben wird. Beim Weiterleiten einer Launch-Seite wird die entsprechende Seite der Quellseiten mit dem Inhalt der weitergeleiteten Seite aktualisiert. Die folgenden Optionen sind beim Weiterleiten einer Launch-Seite verfügbar:

* Soll nur die aktuelle Seite weitergeleitet werden oder der gesamte Launch?
* Sollen die untergeordneten Seiten der aktuellen Seite weitergeleitet werden?
* Soll der vollständige Launch weitergeleitet werden oder die nur Seiten, die geändert wurden?

>[!NOTE]
>
>Wenn Sie die Launch-Seiten an das Ziel (**Produktion**) weitergeleitet haben, können Sie die **Produktionsseiten** als Entität aktivieren (um den Vorgang zu beschleunigen). Fügen Sie die Seiten einem Workflow-Paket hinzu und verwenden Sie es als Payload für einen Workflow, der ein Paket mit Seiten aktiviert. Sie müssen das Workflow-Paket erstellen, bevor Sie den Launch weiterleiten. Siehe [Bearbeiten weitergeleiteter Seiten mit einem AEM-Workflow](#processing-promoted-pages-using-aem-workflow).

>[!CAUTION]
>
>Es ist nicht möglich, einen einzelnen Launch gleichzeitig mehrfach weiterzuleiten. This means that two promote actions on the same launch at the same time can result in an error - `Launch could not be promoted` (together with conflict errors in the log).

>[!CAUTION]
>
>Bei Promotions von Launches für *geänderte* Seiten werden Anpassungen sowohl im Quell- als auch im Launch-Zweig berücksichtigt.

## Weiterleiten von Launch-Seiten {#promoting-launch-pages}

>[!NOTE]
>
>Informationen zur manuellen Weiterleitung von Launch-Seiten, wenn es nur eine Launch-Ebene gibt. Siehe:
>
>* [Weiterleiten eines verschachtelten Launches](#promoting-a-nested-launch), wenn die Struktur mehrere Launches enthält.
>* [Der Ablauf eines Launches](/help/sites-authoring/launches.md#launches-the-order-of-events) für weitere Informationen zur automatischen Weiterleitung und Veröffentlichung.
>



Sie können Launches entweder über die Konsole **Sites** oder die Konsole **Launches** weiterleiten:

1. Öffnen Sie:

   * die Konsole **Sites**:

      1. Open the [references rail](/help/sites-authoring/author-environment-tools.md#references) and select the required source page using [selection mode](/help/sites-authoring/basic-handling.md) (or select and open the references rail, the order is not important). Alle Verweise werden angezeigt.

      1. Wählen Sie **Launches** aus (z. B. „Launches (1)“), um eine Liste der Launches anzuzeigen.
      1. Wählen Sie den gewünschten Launch aus, damit die verfügbaren Aktionen angezeigt werden.
      1. Wählen Sie **Launch bewerben** aus, um den Assistenten zu öffnen.
   * die Konsole **Launches**:

      1. Wählen Sie den Launch aus (indem Sie auf die Miniatur tippen/klicken).
      1. Wählen Sie **Bewerben**.


1. Im ersten Schritt können Sie folgende Optionen festlegen:

   * **Vollständigen Launch bewerben**
   * **Geänderte Seiten bewerben**
   * **Aktuelle Seite bewerben**
   * **Aktuelle Seite und Unterseiten bewerben**
   Wenn beispielsweise nur geänderte Seiten weitergeleitet werden sollen: 

   ![chlimage_1](assets/chlimage_1.png)

   >[!NOTE]
   >
   >Hier wird ein individueller Launch beschrieben. Informationen zu verschachtelten Launches finden Sie unter [Weiterleiten eines verschachtelten Launches](#promoting-a-nested-launch).

1. Klicken Sie auf **Weiter**, um den Vorgang fortzusetzen.
1. Sie können die weiterzuleitenden Seiten überprüfen. Diese Überprüfung hängt vom ausgewählten Seitenbereich ab: 

   ![chlimage_1-1](assets/chlimage_1-1.png)

1. Wählen Sie **Bewerben**.

## Weiterleiten von Launch-Seiten bei der Bearbeitung {#promoting-launch-pages-when-editing}

Wenn Sie eine Launch-Seite bearbeiten, steht die Aktion **Launch bewerben** auch im Bereich **Seiteninformationen** zur Verfügung. Dadurch wird der Assistent geöffnet, um die benötigten Informationen zusammenzustellen. 

![chlimage_1-2](assets/chlimage_1-2.png)

>[!NOTE]
>
>Diese Option steht für einzelne und [verschachtelte Launches](#promoting-a-nested-launch) zur Verfügung.

## Weiterleiten eines verschachtelten Launches {#promoting-a-nested-launch}

Wenn Sie einen verschachtelten Launch erstellt haben, können Sie ihn wieder an jede der Quellen weiterleiten, auch an die Stammquelle (Produktion).

![chlimage_1-3](assets/chlimage_1-3.png)

1. Wie beim [Erstellen eines verschachtelten Starts](/help/sites-authoring/launches-creating.md#creating-a-nested-launch) navigieren Sie entweder über die Konsole **Launches** oder die Leiste **Verweise** zum gewünschten Launch und wählen diesen aus.
1. Wählen Sie **Launch bewerben** aus, um den Assistenten zu öffnen.

1. Geben Sie die erforderlichen Details ein:

   * **Ziel der Promotion**

      Sie können für eine beliebige Quelle werben.

   * **Bereich** Hier können Sie auswählen, ob der gesamte Launch weitergeleitet werden soll oder nur die Seiten, die bearbeitet wurden. Im zweiten Fall können Sie dann auswählen, welche Unterseiten einbezogen bzw. ausgeschlossen werden. In der Standardkonfiguration werden nur Seitenänderungen für die aktuelle Seite weitergeleitet:

      * **Vollständigen Launch bewerben**
      * **Geänderte Seiten bewerben**
      * **Aktuelle Seite bewerben**
      * **Aktuelle Seite und Unterseiten bewerben**
   ![chlimage_1-4](assets/chlimage_1-4.png)

1. Wählen Sie **Weiter**.
1. Überprüfen Sie die Details, bevor Sie **Bewerben** auswählen: 

   ![chlimage_1-5](assets/chlimage_1-5.png)

   >[!NOTE]
   >
   >Welche Seiten angezeigt werden, hängt vom festgelegten **Bereich** und möglicherweise auch von den Seiten ab, die tatsächlich bearbeitet wurden.

1. Die Änderungen werden weitergeleitet und in der Konsole **Launches** dargestellt:

   ![chlimage_1-6](assets/chlimage_1-6.png)

## Verarbeiten von promoteten Seiten mit AEM Workflow {#processing-promoted-pages-using-aem-workflow}

Verwenden Sie Workflow-Modelle, um eine Stapelverarbeitung weitergeleiteter Launch-Seiten durchzuführen:

1. Erstellen Sie ein Workflow-Paket.
1. Wenn Autoren Launch-Seiten weiterleiten, speichern sie sie in einem Workflow-Paket.
1. Starten Sie ein Workflow-Modell mit dem Paket als Payload.

Um einen Workflow automatisch zu starten, wenn Seiten weitergeleitet werden, [konfigurieren Sie einen Workflow-Starter](/help/sites-administering/workflows-starting.md#workflows-launchers) für den Paketknoten.

Sie können z. B. automatisch Seitenaktivierungsanfragen generieren, wenn Autoren Launches-Seiten weiterleiten. Konfigurieren Sie einen Workflow-Starter, um den Workflow zur Anfrageaktivierung zu starten, wenn der Paketknoten geändert wird.

![chlimage_1-7](assets/chlimage_1-7.png)

