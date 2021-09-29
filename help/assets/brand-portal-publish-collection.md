---
title: Veröffentlichen von Sammlungen in Brand Portal
description: Erfahren Sie, wie Sie Sammlungen in Brand Portal veröffentlichen und Veröffentlichungen rückgängig machen können.
contentOwner: VG
feature: Brand Portal
role: User
exl-id: c2c6759e-f763-405e-9e45-5a90b9d32df2
source-git-commit: de5632ff0ee87a4ded88e792b57e818baf4c01a3
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 41%

---

# Veröffentlichen von Sammlungen in Brand Portal {#publish-collections-to-brand-portal}

Als Adobe Experience Manager Assets-Administrator können Sie Sammlungen in der [!DNL Experience Manager Assets Brand Portal]-Instanz für Ihr Unternehmen veröffentlichen. Allerdings müssen Sie zunächst Assets mit Brand Portal integrieren. Weitere Informationen finden Sie unter [Konfigurieren der von  Assets mit Brand Portal](configure-aem-assets-with-brand-portal.md).

Wenn Sie nachfolgende Änderungen an der ursprünglichen Sammlung in Assets vornehmen, werden die Änderungen erst dann in Brand Portal übernommen, wenn Sie die Sammlung erneut veröffentlichen. Diese Eigenschaft stellt sicher, dass laufende Änderungen in Brand Portal nicht verfügbar sind. Nur genehmigte, von einem Administrator veröffentlichte Änderungen sind in Brand Portal verfügbar.

>[!NOTE]
>
>Inhaltsfragmente können nicht in Brand Portal veröffentlicht werden. Wenn Sie daher Inhaltsfragmente in der [!DNL Experience Manager] -Autoreninstanz auswählen, ist die Aktion **[In Brand Portal veröffentlichen]** nicht verfügbar.
>
>Wenn Sammlungen, die Inhaltsfragmente enthalten, aus dem Ordner [!DNL Experience Manager] Autor in Brand Portal veröffentlicht werden, werden alle Inhalte des Ordners mit Ausnahme der Inhaltsfragmente auf der Brand Portal-Benutzeroberfläche repliziert.

## Veröffentlichen einer Sammlung in Brand Portal {#publish-a-collection-to-brand-portal}

1. Tippen/klicken Sie in der Assets-Benutzeroberfläche auf das [!DNL Experience Manager]-Logo. Wechseln Sie dann zu **[!UICONTROL Assets > Sammlungen]** auf der Seite **[!UICONTROL Navigation]**.
2. Wählen Sie in der Konsole &quot;Sammlungen&quot;die Sammlung aus, die Sie in Brand Portal veröffentlichen möchten.

   ![Sammlung auswählen](assets/select_collection.png)

3. Tippen/klicken Sie in der Symbolleiste auf **[!UICONTROL In Brand Portal veröffentlichen]**.

   ![publish_to_bp_icon](assets/publish_to_bp_icon.png)

4. Klicken/tippen Sie im Bestätigungsdialog auf **[!UICONTROL Veröffentlichen]**.
5. Schließen Sie die Bestätigungsmeldung.
6. Melden Sie sich bei Brand Portal als Administrator an. Die veröffentlichte Sammlung steht in der Konsole „Sammlungen“ zur Verfügung.

   ![publish_collection](assets/published_collection.png)

## Veröffentlichung von Sammlungen aufheben {#unpublish-collections}

Sie können die Veröffentlichung von Sammlungen, die Sie aus Assets in Brand Portal veröffentlichen, rückgängig machen. Nachdem Sie die Veröffentlichung der ursprünglichen Sammlung rückgängig gemacht haben, ist die Kopie nicht mehr für Brand Portal-Benutzer verfügbar.

1. Wählen Sie in der Konsole &quot;Sammlungen&quot;Ihrer [!DNL Assets]-Instanz die Sammlung aus, deren Veröffentlichung Sie rückgängig machen möchten.

   ![select_collection-1](assets/select_collection-1.png)

2. Tippen oder klicken Sie in der Symbolleiste auf das Symbol **[!UICONTROL Aus Brand Portal entfernen]** .

   ![remove_from_bp_icon](assets/remove_from_bp_icon.png)

3. Klicken/tippen Sie im Dialog auf **[!UICONTROL Veröffentlichung rückgängig machen]**.
4. Schließen Sie die Bestätigungsmeldung. Die Sammlung wird aus der Brand Portal-Oberfläche entfernt.
