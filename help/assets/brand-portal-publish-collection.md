---
title: Veröffentlichen von Sammlungen in Brand Portal
description: Erfahren Sie, wie Sie Sammlungen in Brand Portal veröffentlichen und deren Veröffentlichung rückgängig machen können.
contentOwner: VG
feature: Brand Portal
role: User
exl-id: c2c6759e-f763-405e-9e45-5a90b9d32df2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 47%

---

# Veröffentlichen von Sammlungen in Brand Portal {#publish-collections-to-brand-portal}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Als Adobe Experience Manager Assets-Administrator können Sie Sammlungen in der [!DNL Experience Manager Assets Brand Portal] -Instanz für Ihr Unternehmen. Allerdings müssen Sie zunächst Assets mit Brand Portal integrieren. Weitere Informationen finden Sie unter [Konfigurieren von  Assets mit Brand Portal](configure-aem-assets-with-brand-portal.md).

Spätere Änderungen an der ursprünglichen Sammlung in Assets spiegeln sich erst bei erneuter Veröffentlichung der Sammlung in Brand Portal wider. Auf diese Weise wird sichergestellt, dass laufende Änderungen (Work-in-Progress, WIP) nicht in Brand Portal verfügbar sind. Nur genehmigte, von einem Admin veröffentlichte Änderungen sind in Brand Portal verfügbar.

>[!NOTE]
>
>Inhaltsfragmente können nicht in Brand Portal veröffentlicht werden. Wenn Sie daher Inhaltsfragmente auf [!DNL Experience Manager] Autor, dann **[In Brand Portal veröffentlichen]** -Aktion nicht verfügbar ist.
>
>Wenn Sammlungen, die Inhaltsfragmente enthalten, aus veröffentlicht werden [!DNL Experience Manager] Erstellen Sie Brand Portal und dann werden alle Inhalte des Ordners mit Ausnahme der Inhaltsfragmente auf die Brand Portal-Benutzeroberfläche repliziert.

## Veröffentlichen einer Sammlung in Brand Portal {#publish-a-collection-to-brand-portal}

1. Tippen/klicken Sie in der Assets-Benutzeroberfläche auf die [!DNL Experience Manager] Logo. Gehen Sie dann zu **[!UICONTROL Assets > Sammlungen]** von **[!UICONTROL Navigation]** Seite.
2. Wählen Sie in der Konsole &quot;Sammlungen&quot;die Sammlung aus, die Sie in Brand Portal veröffentlichen möchten.

   ![Sammlung auswählen](assets/select_collection.png)

3. Tippen/klicken Sie in der Symbolleiste auf **[!UICONTROL In Brand Portal veröffentlichen]**.

   ![publish_to_bp_icon](assets/publish_to_bp_icon.png)

4. Tippen/klicken Sie im Bestätigungsdialogfeld auf **[!UICONTROL Veröffentlichen]**.
5. Schließen Sie die Bestätigungsmeldung.
6. Melden Sie sich bei Brand Portal als Admin an. Die veröffentlichte Sammlung steht in der Konsole „Sammlungen“ zur Verfügung.

   ![publish_collection](assets/published_collection.png)

## Veröffentlichung von Sammlungen aufheben {#unpublish-collections}

Sie können die Veröffentlichung von Sammlungen, die über Assets in Brand Portal erfolgt sind, rückgängig machen. Nachdem Sie die Veröffentlichung der ursprünglichen Sammlung rückgängig gemacht haben, ist die zugehörige Kopie nicht länger für Brand Portal-Benutzer verfügbar.

1. In der Konsole &quot;Sammlungen&quot;Ihrer [!DNL Assets] und wählen Sie die Sammlung aus, deren Veröffentlichung Sie rückgängig machen möchten.

   ![select_collection-1](assets/select_collection-1.png)

2. Tippen/klicken Sie in der Symbolleiste auf die **[!UICONTROL Aus Brand Portal entfernen]** Symbol.

   ![remove_from_bp_icon](assets/remove_from_bp_icon.png)

3. Tippen/klicken Sie im Dialogfeld auf **[!UICONTROL Veröffentlichung rückgängig machen]**.
4. Schließen Sie die Bestätigungsmeldung. Die Sammlung wird aus der Brand Portal-Oberfläche entfernt.
