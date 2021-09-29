---
title: Veröffentlichen von Ordnern in Brand Portal
description: Es wird beschrieben, wie Sie Ordner in Brand Portal veröffentlichen und die Veröffentlichung aufheben.
contentOwner: VG
feature: Brand Portal
role: User
exl-id: f41ab750-5780-42ae-a131-5bc748280215
source-git-commit: de5632ff0ee87a4ded88e792b57e818baf4c01a3
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 45%

---

# Veröffentlichen von Ordnern in Brand Portal {#publish-folders-to-brand-portal}

Als Adobe Experience Manager Assets-Administrator können Sie Assets und Ordner für Ihr Unternehmen in der [!DNL Experience Manager Assets Brand Portal]-Instanz veröffentlichen (oder den Veröffentlichungs-Workflow für einen späteren Zeitpunkt planen). Sie müssen jedoch zunächst [!DNL Experience Manager Assets] mit [!DNL Brand Portal] integrieren. Weitere Informationen finden Sie unter [Konfigurieren [!DNL Experience Manager Assets] mit Brand Portal](configure-aem-assets-with-brand-portal.md).

Nachdem Sie ein Asset oder einen Ordner veröffentlicht haben, ist es für Benutzer in Brand Portal verfügbar.

Wenn Sie nachfolgende Änderungen am ursprünglichen Asset oder Ordner in [!DNL Assets] vornehmen, werden die Änderungen erst dann in Brand Portal übernommen, wenn Sie das Asset oder den Ordner erneut veröffentlichen. Mit dieser Funktion wird sichergestellt, dass Änderungen im Rahmen der laufenden Bearbeitung nicht in Brand Portal verfügbar sind. Nur genehmigte, von einem Administrator veröffentlichte Änderungen sind in Brand Portal verfügbar.

## Veröffentlichen von Ordnern in Brand Portal {#publish-folders-to-brand-portal-1}

1. Bewegen Sie in der [!DNL Assets]-Benutzeroberfläche den Mauszeiger über den gewünschten Ordner und wählen Sie in den Schnellaktionen die Option **[!UICONTROL Veröffentlichen]** aus.

   Alternativ können Sie den gewünschten Ordner auswählen und den weiteren Schritten folgen.

   ![publish2bp](assets/publish2bp.png)

2. **Ordner jetzt veröffentlichen**

   Um die ausgewählten Ordner in Brand Portal zu veröffentlichen, führen Sie einen der folgenden Schritte aus:

   * Wählen Sie in der Symbolleiste **[!UICONTROL Quick Publish]** aus. Wählen Sie dann im Menü **[!UICONTROL In Brand Portal veröffentlichen]** aus.
   * Wählen Sie in der Symbolleiste **[!UICONTROL Veröffentlichung verwalten]** aus.

3. Wählen Sie dann **[!UICONTROL Aktion]** **[!UICONTROL Auf Brand Portal veröffentlichen]** aus und wählen Sie **[!UICONTROL Planung]** **[!UICONTROL Jetzt]** aus. Tippen Sie auf **[!UICONTROL Weiter].**
4. Bestätigen Sie Ihre Auswahl in **[!UICONTROL Umfang]** und tippen Sie auf **[!UICONTROL In Brand Portal veröffentlichen]**.

   Eine Meldung erscheint, die besagt, dass der Ordner zur Veröffentlichung in Brand Portal in die Warteschlange gestellt wurde. Melden Sie sich bei der Brand Portal-Benutzeroberfläche an, um den veröffentlichten Ordner zu sehen.

   **Ordner später veröffentlichen**

   So planen Sie die Veröffentlichung von Asset-Ordnern in Brand Portal auf einen späteren Zeitpunkt:

   1. Nachdem Sie die zu veröffentlichenden Assets/Ordner ausgewählt haben, wählen Sie oben in der Symbolleiste **[!UICONTROL Veröffentlichung verwalten]** aus.
   2. Wählen Sie auf der Seite **[!UICONTROL Veröffentlichung verwalten]** die Option **[!UICONTROL In Brand Portal veröffentlichen]** aus **[!UICONTROL Aktion]** und wählen Sie **[!UICONTROL Später]** aus **[!UICONTROL Planung]**.

      ![publishlaterbp](assets/publishlaterbp.png)

   3. Wählen Sie ein **[!UICONTROL Aktivierungsdatum]** aus und geben Sie die Zeit an. Tippen Sie auf **[!UICONTROL Weiter]**.
   4. Bestätigen Sie Ihre Auswahl unter **[!UICONTROL Umfang]**. Tippen Sie auf **[!UICONTROL Weiter]**.
   5. Geben Sie einen Workflow-Titel unter **[!UICONTROL Workflows]** an. Tippen Sie auf **[!UICONTROL Später veröffentlichen]**.

      ![manageschedulepub](assets/manageschedulepub.png)

## Veröffentlichung von Ordnern in Brand Portal rückgängig machen {#unpublish-folders-from-brand-portal}

Sie können alle in Brand Portal veröffentlichten Asset-Ordner entfernen, indem Sie die Veröffentlichung in der [!DNL Experience Manager] -Autoreninstanz rückgängig machen. Nachdem Sie die Veröffentlichung des ursprünglichen Ordners aufgehoben haben, ist dessen Kopie nicht mehr für Brand Portal-Benutzer verfügbar.

Sie können die Veröffentlichung der Ordner in Brand Portal sofort rückgängig machen oder diesen Vorgang für einen späteren Zeitpunkt planen. So machen Sie die Veröffentlichung von Assets/Ordnern in Brand Portal rückgängig:

1. Wählen Sie in der [!DNL Assets] -Benutzeroberfläche in der [!DNL Experience Manager] -Autoreninstanz den Ordner aus, dessen Veröffentlichung Sie rückgängig machen möchten.

   ![publish2bp-1](assets/publish2bp-1.png)

2. Tippen/klicken Sie in der Symbolleiste auf **[!UICONTROL Veröffentlichung verwalten]**. 

3. **Veröffentlichung in Brand Portal jetzt rückgängig machen**

   So können Sie die Veröffentlichung des gewünschten Ordners in Brand Portal schnell rückgängig machen:

   1. Wählen Sie auf der Seite **[!UICONTROL Veröffentlichung verwalten]** unter **[!UICONTROL Aktion]** die Option **[!UICONTROL Veröffentlichung in Brand Portal rückgängig machen]** und unter **[!UICONTROL Planung]** die Option **[!UICONTROL Jetzt]**.
   2. Klicken oder tippen Sie auf **[!UICONTROL Weiter].**
   3. Bestätigen Sie Ihre Auswahl in **[!UICONTROL Umfang]** und tippen Sie auf **[!UICONTROL Veröffentlichung in Brand Portal rückgängig machen]**.

   ![confirm-unpublish](assets/confirm-unpublish.png)

   **Veröffentlichung später in Brand Portal rückgängig machen**

   So können Sie die Veröffentlichung eines Ordners in Brand Portal zu einem späteren Zeitpunkt rückgängig machen:

   1. Wählen Sie auf der Seite **[!UICONTROL Veröffentlichung verwalten]** unter **[!UICONTROL Aktion]** die Option **[!UICONTROL Veröffentlichung in Brand Portal rückgängig machen]** und unter **[!UICONTROL Planung]** die Option **[!UICONTROL Später].**.
   2. Wählen Sie ein **[!UICONTROL Aktivierungsdatum]** aus und geben Sie die Zeit an. Tippen Sie auf **[!UICONTROL Weiter]**.
   3. Bestätigen Sie Ihre Auswahl in **[!UICONTROL Perimeter]** und tippen Sie auf **[!UICONTROL Weiter]**.
   4. Geben Sie einen **[!UICONTROL Workflow-Titel]** unter **[!UICONTROL Workflows]** an. Tippen Sie auf **[!UICONTROL Veröffentlichung später rückgängig machen].**

      ![unpublishworkflows](assets/unpublishworkflows.png)


>[!NOTE]
>
>Das Veröffentlichen/Rückgängigmachen der Veröffentlichung eines Assets in/von Brand Portal ähnelt dem entsprechenden Verfahren für einen Ordner.
