---
title: Einchecken und Auschecken digitaler Assets zur Bearbeitung
description: Erfahren Sie, wie Sie Assets zur Bearbeitung auschecken und nach Abschluss der Änderungen wieder einchecken können.
contentOwner: AG
feature: Asset Management
role: User
exl-id: 0c79ed42-0acd-426e-8e14-412bb4117585
source-git-commit: 8948bca63f1f5ec9d94ede2fb845ed01b4e23333
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 66%

---

# Ein- und Auschecken von Dateien in Assets {#check-in-and-check-out-files-in-assets}

Mit Adobe Experience Manager Assets können Sie Assets zur Bearbeitung auschecken und wieder einchecken, nachdem Sie die Änderungen vorgenommen haben. Nachdem Sie ein Asset ausgecheckt haben, können nur Sie es bearbeiten, kommentieren, veröffentlichen, verschieben oder löschen. Beim Auschecken eines Assets wird das Asset gesperrt. Andere Benutzer können diese Vorgänge erst dann für das Asset ausführen, wenn Sie das Asset wieder in [!DNL Experience Manager] Assets. Allerdings können Sie nach wie vor die Metadaten für das gesperrte Asset ändern.

Um Assets ein- oder auschecken zu können, benötigen Sie Schreibzugriff auf sie.

Mithilfe dieser Funktion können Sie verhindern, dass Benutzer die von einem Autor vorgenommenen Änderungen überschreiben, wenn mehrere Benutzer Team-übergreifend im Rahmen von Bearbeitungs-Workflows zusammenarbeiten.

## Auschecken von Assets {#checking-out-assets}

1. Wählen Sie in der Assets-Benutzeroberfläche das Asset aus, das Sie auschecken möchten. Sie können auch mehrere Assets zum Auschecken auswählen.

   ![chlimage_1-468](assets/chlimage_1-468.png)

1. Klicken Sie in der Symbolleiste auf das Symbol **[!UICONTROL Auschecken]**.

   ![chlimage_1-469](assets/chlimage_1-469.png)

   Das Symbol **[!UICONTROL Auschecken]** verändert sich zum Symbol **[!UICONTROL Einchecken]** mit geöffnetem Schloss.

   ![chlimage_1-470](assets/chlimage_1-470.png)

   Um zu überprüfen, ob andere Benutzer das von Ihnen ausgecheckte Asset bearbeiten können, melden Sie sich unter einem anderen Benutzernamen an. Ein Schlosssymbol wird auf der Miniatur des Assets angezeigt, das Sie ausgecheckt haben.

   ![chlimage_1-471](assets/chlimage_1-471.png)

   Wählen Sie das Asset aus. In der Symbolleiste werden keine Optionen zum Bearbeiten, Kommentieren, Veröffentlichen oder Löschen des Assets angezeigt.

   ![chlimage_1-472](assets/chlimage_1-472.png)

   Sie können jedoch auf das Symbol **[!UICONTROL Eigenschaften anzeigen]** klicken/tippen, um die Metadaten für das gesperrte Asset zu bearbeiten.

1. Klicken/tippen Sie auf das Symbol „Bearbeiten“, um das Asset im Bearbeitungsmodus zu öffnen.

   ![chlimage_1-473](assets/chlimage_1-473.png)

1. Bearbeiten Sie das Asset und speichern Sie die Änderungen. Schneiden Sie beispielsweise das Bild zu und speichern Sie es.

   ![chlimage_1-474](assets/chlimage_1-474.png)

   Sie können das Asset auch mit Anmerkungen versehen oder es veröffentlichen.

1. Wählen Sie das bearbeitete Asset in der Assets-Benutzeroberfläche aus und klicken Sie auf das Symbol **[!UICONTROL Checkin]** in der Symbolleiste.

   ![chlimage_1-475](assets/chlimage_1-475.png)

   Das geänderte Asset wird in [!DNL Assets] eingecheckt und steht anderen Benutzern zur Bearbeitung zur Verfügung.

## Erzwungenes Einchecken {#forced-check-in}

Administratoren können Assets einchecken, die von anderen Benutzern ausgecheckt wurden.

1. Melden Sie sich bei [!DNL Assets] als Admin an.
1. Wählen Sie in der Assets-Benutzeroberfläche ein bzw. mehrere Assets, das bzw. die von anderen Benutzern ausgecheckt wurde(n).

   ![chlimage_1-476](assets/chlimage_1-476.png)

1. Klicken/tippen Sie in der Symbolleiste auf das Symbol **[!UICONTROL Sperre lösen]**. Das Asset wird wieder eingecheckt und steht anderen Benutzern zur Bearbeitung zur Verfügung.

   ![chlimage_1-477](assets/chlimage_1-477.png)
