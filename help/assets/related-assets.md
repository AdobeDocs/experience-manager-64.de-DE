---
title: Zugehörige Assets
description: Erfahren Sie, wie Sie Assets verknüpfen, die bestimmte gemeinsame Attribute aufweisen. Sie können die Funktion auch verwenden, um Quell-/abgeleitete Beziehungen zwischen Assets zu erstellen.
contentOwner: AG
feature: Asset Management,Collaboration
role: User
exl-id: d19544c4-c8e7-4a39-9c86-15a46dca848e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '646'
ht-degree: 38%

---

# Zugehörige Assets {#related-assets}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Mit Adobe Experience Manager Assets können Sie Assets mithilfe der Funktion &quot;Zugehörige Assets&quot;manuell basierend auf den Anforderungen Ihres Unternehmens zuordnen. Beispielsweise können Sie einem Asset oder einem Bild/Video mit einer Lizenzdatei zu einem ähnlichen Thema verknüpfen. Sie können Assets verknüpfen, die bestimmte Attribute gemeinsam haben. Sie können die Funktion auch verwenden, um Quell-/abgeleitete Beziehungen zwischen Assets zu erstellen. Beispielsweise können Sie PDF-Dateien, die aus einer INDD-Datei generiert wurden, mit der INDD-Quelldatei verknüpfen.

Auf diese Weise können Sie eine Datei mit niedriger Auflösung (z. B. PDF/JPG) für Anbieter/Agenturen freigeben und die hochauflösende Datei (z. B. INDD) nur auf Anfrage zur Verfügung stellen.

## Zuordnen von Assets {#relating-assets}

1. Öffnen Sie in der Benutzeroberfläche von Assets die Eigenschaftenseite für ein Asset, das Sie zuordnen möchten.

   ![chlimage_1-272](assets/chlimage_1-272.png)

   Wählen Sie alternativ das gewünschte Asset in der Listenansicht aus.

   ![chlimage_1-273](assets/chlimage_1-273.png)

   Sie können das Asset auch aus einer Sammlung auswählen.

   ![chlimage_1-274](assets/chlimage_1-274.png)

1. Um ein anderes Asset mit dem ausgewählten Asset zu verknüpfen, klicken/tippen Sie auf das **[!UICONTROL Relation]** in der Symbolleiste.

   ![chlimage_1-275](assets/chlimage_1-275.png)

1. Führen Sie einen der folgenden Schritte aus:

   * Um die Quelldatei für das Asset zuzuordnen, wählen Sie **[!UICONTROL Quelle]** aus der Liste.
   * Um eine abgeleitete Datei zuzuordnen, wählen Sie **[!UICONTROL Abgeleitet]** aus der Liste aus.
   * Um eine bidirektionale Beziehung zwischen den Assets zu erstellen, wählen Sie **[!UICONTROL sonstige]** aus der Liste.

   ![chlimage_1-276](assets/chlimage_1-276.png)

1. Aus dem **[!UICONTROL Asset auswählen]** navigieren Sie zum Speicherort des Assets, das Sie zuordnen möchten, und wählen Sie es aus.

   ![chlimage_1-277](assets/chlimage_1-277.png)

1. Klicken/tippen Sie auf **[!UICONTROL Bestätigen]** Symbol.
1. Klicken/tippen Sie auf **[!UICONTROL OK]**, um das Dialogfeld zu schließen. Je nach Auswahl der Beziehung in Schritt 3 wird das verknüpfte Asset unter einer entsprechenden Kategorie im Abschnitt **[!UICONTROL Verknüpft]** aufgeführt. Beispiel: Wenn das verknüpfte Asset die Quelldatei des aktuellen Elements ist, wird es unter **[!UICONTROL Quelle]** aufgeführt.

   ![chlimage_1-278](assets/chlimage_1-278.png)

1. Um die Zuordnung eines Assets aufzuheben, klicken/tippen Sie auf die **[!UICONTROL Nicht zuordnen]** in der Symbolleiste.

   ![chlimage_1-279](assets/chlimage_1-279.png)

1. Wählen Sie die Assets aus, deren Bezug zum Dialogfeld **[!UICONTROL Beziehungen entfernen]** Sie aufheben möchten, und klicken/tippen Sie auf **[!UICONTROL Bezug aufheben]**.

   ![chlimage_1-280](assets/chlimage_1-280.png)

1. Klicken/Tippen **[!UICONTROL OK]** , um das Dialogfeld zu schließen. Die Assets, für die Sie Verknüpfungen entfernt haben, werden aus der Liste der verknüpften Assets im Abschnitt **[!UICONTROL Verknüpft]** gelöscht.

## Übersetzen verwandter Assets {#translating-related-assets}

Das Erstellen von Quell-/abgeleiteten Beziehungen zwischen Assets mithilfe der Funktion &quot;Zugehörige Assets&quot;ist auch in Übersetzungs-Workflows hilfreich. Wenn Sie einen Übersetzungs-Workflow für ein abgeleitetes Asset ausführen, [!DNL Experience Manager] Assets ruft automatisch alle Assets ab, auf die die Quelldatei verweist, und schließt sie zur Übersetzung ein. Auf diese Weise wird das vom Quell-Asset referenzierte Asset zusammen mit der Quelle und den abgeleiteten Assets übersetzt. Angenommen, Ihre englischsprachige Kopie enthält ein abgeleitetes Asset und dessen Quelldatei wie gezeigt.

![chlimage_1-281](assets/chlimage_1-281.png)

Wenn die Quelldatei mit einem anderen Asset verknüpft ist, [!DNL Experience Manager] Assets ruft das referenzierte Asset ab und fügt es zur Übersetzung hinzu.

![chlimage_1-282](assets/chlimage_1-282.png)

1. Übersetzen Sie die Assets im Quellordner in eine Zielsprache, indem Sie die Schritte unter [Neues Übersetzungsprojekt erstellen](translation-projects.md#create-a-new-translation-project). Übersetzen Sie in diesem Fall beispielsweise Ihre Assets auf Französisch.
1. Öffnen Sie auf der Seite Projekte den Übersetzungsordner.

   ![chlimage_1-283](assets/chlimage_1-283.png)

1. Klicken/tippen Sie auf die Projektkachel, um die Detailseite zu öffnen.

   ![chlimage_1-284](assets/chlimage_1-284.png)

1. Klicken/tippen Sie auf die Auslassungszeichen unter der Karte Übersetzungsauftrag , um den Übersetzungsstatus anzuzeigen.

   ![chlimage_1-285](assets/chlimage_1-285.png)

1. Wählen Sie das Asset aus und klicken/tippen Sie dann auf **[!UICONTROL In Assets einblenden]** in der Symbolleiste, um den Übersetzungsstatus für das Asset anzuzeigen.

   ![chlimage_1-286](assets/chlimage_1-286.png)

1. Um zu überprüfen, ob die mit der Quelle verknüpften Assets übersetzt wurden, klicken/tippen Sie auf das Quell-Asset.

   ![chlimage_1-287](assets/chlimage_1-287.png)

1. Wählen Sie das mit der Quelle verknüpfte Element aus und klicken/tippen Sie auf **[!UICONTROL In Assets einblenden]**. Das übersetzte zugehörige Asset wird angezeigt.

   ![chlimage_1-288](assets/chlimage_1-288.png)
