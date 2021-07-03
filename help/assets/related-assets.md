---
title: Zugehörige Assets
description: Erfahren Sie, wie Sie Assets mit bestimmten gemeinsamen Attributen verknüpfen. Mit der Funktion können Sie außerdem Quellbeziehungen/abgeleitete Beziehungen zwischen Assets erstellen.
contentOwner: AG
feature: Asset-Management, Zusammenarbeit
role: User
exl-id: d19544c4-c8e7-4a39-9c86-15a46dca848e
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 99%

---

# Zugehörige Assets {#related-assets}

Mit Adobe Experience Manager (AEM) Assets können Sie Assets manuell entsprechend den Anforderungen Ihres Unternehmens zuordnen. Verwenden Sie hierfür die Funktion „Zugehörige Assets“. Beispielsweise können Sie einem Asset oder einem Bild/Video eine Lizenzdatei zu einem ähnlichen Thema zuordnen. Sie können Assets zuordnen, die bestimmte gängige Attribute teilen. Mit der Funktion können Sie außerdem Quellbeziehungen/abgeleitete Beziehungen zwischen Assets erstellen. Beispielsweise können Sie PDF-Dateien, die aus einer INDD-Datei generiert wurden, der INDD-Quelldatei zuordnen.

Auf diese Weise haben Sie die Flexibilität, Dateien mit niedriger Auflösung (z. B. PDF/JPG) mit Mitarbeitern/Agenturen zu teilen und die Datei mit hoher Auflösung (z. B. INDD) nur auf Anfrage zur Verfügung zu stellen.

## Zugehörige Assets {#relating-assets}

1. Öffnen Sie in der Benutzeroberfläche von Assets die Eigenschaftenseite für ein Asset, das Sie zuordnen möchten.

   ![chlimage_1-272](assets/chlimage_1-272.png)

   Wählen Sie alternativ das gewünschte Asset in der Liste aus.

   ![chlimage_1-273](assets/chlimage_1-273.png)

   Sie können das Asset auch aus einer Sammlung auswählen.

   ![chlimage_1-274](assets/chlimage_1-274.png)

1. Um dem ausgewählten Asset ein anderes Asset zuzuordnen, klicken/tippen Sie in der Symbolleiste auf das Symbol für **[!UICONTROL Zuordnen]**.

   ![chlimage_1-275](assets/chlimage_1-275.png)

1. Führen Sie einen der folgenden Schritte aus:

   * Um die Quelldatei des Elements zuzuordnen, wählen Sie **[!UICONTROL Quelle]** aus der Liste aus.
   * Um eine abgeleitete Datei zuzuordnen, wählen Sie **[!UICONTROL Abgeleitet]** aus der Liste aus.
   * Um eine Zweiwege-Beziehung zwischen den Assets zu erstellen, wählen Sie **[!UICONTROL Andere]** aus der Liste aus.

   ![chlimage_1-276](assets/chlimage_1-276.png)

1. Navigieren Sie im Bildschirm **[!UICONTROL Assets auswählen]** zum Speicherort des Elements, das Sie zuordnen möchten, und wählen Sie es aus.

   ![chlimage_1-277](assets/chlimage_1-277.png)

1. Klicken/tippen Sie auf das Symbol **[!UICONTROL Bestätigen]**.
1. Klicken/tippen Sie auf **[!UICONTROL OK]**, um das Dialogfeld zu schließen. Je nach Auswahl der Beziehung in Schritt 3 wird das zugeordnete Asset unter einer entsprechenden Kategorie im Abschnitt **[!UICONTROL Zugehörig]** aufgeführt. Beispiel: Wenn das zugeordnete Asset die Quelldatei des aktuellen Elements ist, wird es unter **[!UICONTROL Quelle]** aufgeführt.

   ![chlimage_1-278](assets/chlimage_1-278.png)

1. Um die Zuordnung eines Elements aufzuheben, klicken/tippen Sie in der Symbolleiste auf das Symbol **[!UICONTROL Bezug aufheben]**.

   ![chlimage_1-279](assets/chlimage_1-279.png)

1. Wählen Sie die Assets aus, deren Bezug zum Dialogfeld **[!UICONTROL Beziehungen entfernen]** Sie aufheben möchten, und klicken/tippen Sie auf **[!UICONTROL Bezug aufheben]**.

   ![chlimage_1-280](assets/chlimage_1-280.png)

1. Klicken/tippen Sie auf **[!UICONTROL OK]**, um das Dialogfeld zu schließen. Die Assets, für die Sie Verbindungen entfernt haben, werden aus der Liste der zugeordneten Assets im Abschnitt **[!UICONTROL Zugehörig]** gelöscht.

## Übersetzen von zugehörigen Assets {#translating-related-assets}

Für die Übersetzungs-Workflows ist die Erstellung von Quellbeziehungen/abgeleiteten Beziehungen zwischen Assets mit der Funktion „Zugehörige Assets“ nützlich. Wenn Sie für ein abgeleitetes Asset einen Übersetzungs-Workflow ausführen, ruft AEM Assets automatisch beliebige Assets ab, die von der Quelldatei referenziert werden, und nimmt sie in die Übersetzung auf. Auf diese Weise wird das vom Quell-Asset referenzierte Asset zusammen mit dem Quell-Asset und den abgeleiteten Assets übersetzt. Beispiel: In einem Szenario enthält die Kopie in englischer Sprache ein abgeleitetes Asset und die entsprechende Quelldatei wie gezeigt.

![chlimage_1-281](assets/chlimage_1-281.png)

Ist die Quelldatei mit einem anderen Asset verknüpft, ruft AEM Assets das referenzierte Asset ab und nimmt es in die Übersetzung auf.

![chlimage_1-282](assets/chlimage_1-282.png)

1. Übersetzen Sie die Assets im Quellordner für eine Zielsprache, indem Sie die Schritte unter [Neues Übersetzungsprojekt erstellen](translation-projects.md#create-a-new-translation-project) befolgen. Übersetzen Sie in diesem Fall zum Beispiel Ihre Assets ins Französische.
1. Öffnen Sie auf der Seite „Projekte“ den Übersetzungsordner.

   ![chlimage_1-283](assets/chlimage_1-283.png)

1. Klicken/tippen Sie auf die Projektkachel, um die Seite mit den Details zu öffnen.

   ![chlimage_1-284](assets/chlimage_1-284.png)

1. Klicken/tippen Sie auf die Auslassungszeichen unter der Karte „Übersetzungsauftrag“, um den Übersetzungsstatus anzuzeigen.

   ![chlimage_1-285](assets/chlimage_1-285.png)

1. Wählen Sie das Asset aus und tippen/klicken Sie in der Symbolleiste auf **[!UICONTROL In Assets einblenden]**, um den Übersetzungsstatus für das Asset anzuzeigen.

   ![chlimage_1-286](assets/chlimage_1-286.png)

1. Um sicherzustellen, dass die der Quelle zugeordneten Assets übersetzt wurden, klicken/tippen Sie auf das Quellelement.

   ![chlimage_1-287](assets/chlimage_1-287.png)

1. Wählen Sie das mit der Quelle verknüpfte Element aus und klicken/tippen Sie auf **[!UICONTROL In Assets einblenden]**. Das übersetzte zugehörige Asset wird angezeigt.

   ![chlimage_1-288](assets/chlimage_1-288.png)
