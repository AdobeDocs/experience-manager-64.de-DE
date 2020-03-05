---
title: Veröffentlichen von Ordnern in Brand Portal
description: Erfahren Sie, wie Sie Assets im Markenportal veröffentlichen und die Veröffentlichung rückgängig machen.
contentOwner: VG
translation-type: tm+mt
source-git-commit: f09853921dec6602952f369982a1563c7e4a9727

---


# Veröffentlichen von Assets in Brand Portal {#publish-assets-to-brand-portal}

Als Administrator für Adobe Experience Manager (AEM) Assets können Sie Assets für Ihr Unternehmen in der AEM Assets Brand Portal-Instanz veröffentlichen (oder den Veröffentlichungsarbeitsablauf auf ein späteres Datum/eine spätere Uhrzeit planen). Sie müssen jedoch zuerst AEM Assets mit dem Markenportal konfigurieren. For details, see [Configure AEM Assets with Brand Portal](configure-aem-assets-with-brand-portal.md).

Nachdem Sie ein Asset veröffentlicht haben, steht es Benutzern im Markenportal zur Verfügung.

Wenn Sie nachfolgende Änderungen am ursprünglichen Asset in AEM Assets vornehmen, werden die Änderungen erst dann im Markenportal übernommen, wenn Sie das Asset erneut veröffentlichen. Mit dieser Funktion wird sichergestellt, dass derzeit vorgenommene Änderungen nicht im Markenportal verfügbar sind. Nur genehmigte Änderungen, die von einem Administrator veröffentlicht werden, sind im Markenportal verfügbar.

Nach erfolgreicher Replikation können Sie Assets, Ordner und Sammlungen in Brand Portal veröffentlichen. Gehen Sie wie folgt vor, um Assets in Brand Portal zu veröffentlichen:

>[!NOTE]
>
>Adobe empfiehlt eine gestaffelte Veröffentlichung, vorzugsweise außerhalb der Spitzenzeiten, sodass die AEM-Autoreninstanz keine übermäßigen Ressourcen belegt.

1. Bewegen Sie in der Assets-Konsole den Mauszeiger auf die gewünschten Assets und wählen Sie aus den Schnellaktionen die Option **[!UICONTROL Veröffentlichen]** aus.

   Alternativ können Sie auch die Assets auswählen, die Sie in Brand Portal veröffentlichen möchten.

   ![publish2bp-2](assets/publish2bp-2.png)

2. Um die Assets im Markenportal zu veröffentlichen, stehen die folgenden zwei Optionen zur Verfügung:
   * [Assets sofort veröffentlichen](#publish-now)
   * [Assets später veröffentlichen](#publish-later)

## Assets jetzt veröffentlichen {#publish-now}

Um die ausgewählten Assets in Brand Portal zu veröffentlichen, führen Sie einen der folgenden Schritte aus:

* From the toolbar, select **[!UICONTROL Quick Publish]**. Then from the menu, select **[!UICONTROL Publish to Brand Portal]**.

* From the toolbar, select **[!UICONTROL Manage Publication]**.

   1. Then from the **[!UICONTROL Action]** select **[!UICONTROL Publish to Brand Portal]**, and from **[!UICONTROL Scheduling]** select **[!UICONTROL Now]**. Klicken oder tippen Sie auf **[!UICONTROL Weiter].**

   2. Within **[!UICONTROL Scope]**, confirm your selection and tap/ click **[!UICONTROL Publish to Brand Portal]**.

Eine Meldung erscheint, die besagt, dass die Assets zur Veröffentlichung in Brand Portal in die Warteschlange gestellt wurden. Melden Sie sich bei der Brand Portal-Benutzeroberfläche an, um die veröffentlichten Assets zu sehen.

## Assets später veröffentlichen {#publish-later}

So planen Sie die Veröffentlichung der Assets in Brand Portal zu einem späteren Zeitpunkt:

1. Once you have selected assets/ folders to publish, select **[!UICONTROL Manage Publication]** from the tool bar at the top.
2. On **[!UICONTROL Manage Publication]** page, select **[!UICONTROL Publish to Brand Portal]** from **[!UICONTROL Action]** and select **[!UICONTROL Later]** from **[!UICONTROL Scheduling]**.

   ![publishlatbp-1](assets/publishlaterbp-1.png)

3. Select an **[!UICONTROL Activation date]** and specify time. Klicken oder tippen Sie auf **[!UICONTROL Weiter]**.
4. Select an **[!UICONTROL Activation date]** and specify time. Klicken oder tippen Sie auf **[!UICONTROL Weiter]**.
5. Specify a Workflow title under **[!UICONTROL Workflows]**. Tap/ click **[!UICONTROL Publish Later]**.

   ![publishworkflow](assets/publishworkflow.png)

Melden Sie sich jetzt beim Markenportal an, um zu sehen, ob die veröffentlichten Assets auf der Benutzeroberfläche des Markenportals verfügbar sind.

![bp_631_landing_page](assets/bp_landing_page.png)
