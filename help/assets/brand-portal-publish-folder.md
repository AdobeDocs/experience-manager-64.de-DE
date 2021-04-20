---
title: Veröffentlichen von Ordnern in Brand Portal
description: Es wird beschrieben, wie Sie Ordner in Brand Portal veröffentlichen und die Veröffentlichung aufheben.
contentOwner: VG
feature: Brand Portal
role: Business Practitioner
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '575'
ht-degree: 58%

---


# Veröffentlichen von Ordnern in Brand Portal {#publish-folders-to-brand-portal}

Als Adobe Experience Manager (AEM) Assets-Administrator können Sie für Ihre Organisation Assets und Ordner in der AEM Assets Brand Portal-Instanz veröffentlichen (oder den Veröffentlichungs-Workflow für einen späteren Zeitpunkt planen). Allerdings müssen Sie zunächst AEM Assets mit Brand Portal integrieren. Weitere Informationen finden Sie unter [Konfigurieren der von AEM Assets mit Brand Portal](configure-aem-assets-with-brand-portal.md).

Nachdem Sie ein Asset oder einen Ordner veröffentlicht haben, steht es Benutzern im Markenportal zur Verfügung.

Wenn Sie nachfolgende Änderungen am ursprünglichen Asset oder Ordner in AEM Assets vornehmen, werden die Änderungen erst dann im Markenportal übernommen, wenn Sie das Asset oder den Ordner erneut veröffentlichen. Mit dieser Funktion wird sichergestellt, dass Änderungen im Rahmen der laufenden Bearbeitung nicht in Brand Portal verfügbar sind. Nur genehmigte, von einem Administrator veröffentlichte Änderungen sind in Brand Portal verfügbar.

## Veröffentlichen von Ordnern in Brand Portal {#publish-folders-to-brand-portal-1}

1. Bewegen Sie den Mauszeiger in der AEM Assets-Oberfläche über den gewünschten Ordner und wählen Sie in den Schnellaktionen die Option **[!UICONTROL Veröffentlichen]**.

   Alternativ können Sie den gewünschten Ordner auswählen und den weiteren Schritten folgen.

   ![publish2bp](assets/publish2bp.png)

2. **Ordner jetzt veröffentlichen** 

   Um die ausgewählten Ordner in Brand Portal zu veröffentlichen, führen Sie einen der folgenden Schritte aus:

   * Wählen Sie in der Symbolleiste **[!UICONTROL Quick Publish]** aus. Wählen Sie dann im Menü **[!UICONTROL In Markenportal veröffentlichen]**.
   * Wählen Sie in der Symbolleiste **[!UICONTROL Veröffentlichung verwalten]** aus.

3. Wählen Sie dann unter **[!UICONTROL Aktion]** **[!UICONTROL In Markenportal veröffentlichen]** und unter **[!UICONTROL Einplanen]** **[!UICONTROL Jetzt]**. Tippen Sie auf **[!UICONTROL Weiter].**
4. Bestätigen Sie in **[!UICONTROL Scope]** Ihre Auswahl und tippen Sie auf **[!UICONTROL In Markenportal veröffentlichen]**.

   Eine Meldung erscheint, die besagt, dass der Ordner zur Veröffentlichung in Brand Portal in die Warteschlange gestellt wurde. Melden Sie sich bei der Brand Portal-Benutzeroberfläche an, um den veröffentlichten Ordner zu sehen.

   **Ordner später veröffentlichen**

   So planen Sie die Veröffentlichung von Asset-Ordnern im Brand Portal auf ein späteres Datum oder eine spätere Uhrzeit:

   1. Nachdem Sie die zu veröffentlichenden Assets/Ordner ausgewählt haben, wählen Sie in der Symbolleiste oben **[!UICONTROL Veröffentlichung verwalten]** aus.
   2. Wählen Sie auf der Seite **[!UICONTROL Veröffentlichung verwalten]** die Option **[!UICONTROL In Markenportal veröffentlichen]** aus **[!UICONTROL Aktion]** und wählen Sie **[!UICONTROL Später]** aus **[!UICONTROL Einplanen]**.

      ![publishlaterbp](assets/publishlaterbp.png)

   3. Wählen Sie ein **[!UICONTROL Aktivierungsdatum]** aus und geben Sie die Zeit an. Tippen Sie auf **[!UICONTROL Weiter]**.
   4. Bestätigen Sie Ihre Auswahl unter **[!UICONTROL Umfang]**. Tippen Sie auf **[!UICONTROL Weiter]**.
   5. Geben Sie einen Workflow-Titel unter **[!UICONTROL Workflows]** an. Tippen Sie auf **[!UICONTROL Später veröffentlichen]**.

      ![manageschedulepub](assets/manageschedulepub.png)

## Veröffentlichung von Ordnern in Brand Portal rückgängig machen {#unpublish-folders-from-brand-portal}

Sie können alle in Brand Portal veröffentliche Assets/Ordner entfernen, indem Sie die Veröffentlichung über die AEM-Autoreninstanz rückgängig machen. Nachdem Sie die Veröffentlichung des ursprünglichen Ordners aufgehoben haben, ist dessen Kopie nicht mehr für Brand Portal-Benutzer verfügbar.

Sie können die Veröffentlichung der Ordner in Brand Portal sofort rückgängig machen oder diesen Vorgang für einen späteren Zeitpunkt planen. So machen Sie die Veröffentlichung von Assets/Ordnern in Brand Portal rückgängig:

1. Wählen Sie in der AEM Assets-Benutzeroberfläche in der AEM-Autoreninstanz den Ordner aus, dessen Veröffentlichung Sie rückgängig machen möchten.

   ![publish2bp-1](assets/publish2bp-1.png)

2. Tippen/klicken Sie in der Symbolleiste auf **[!UICONTROL Veröffentlichung verwalten]**. 

3. **Veröffentlichung in Brand Portal jetzt rückgängig machen**

   So können Sie die Veröffentlichung des gewünschten Ordners in Brand Portal schnell rückgängig machen:

   1. Wählen Sie auf der Seite **[!UICONTROL Veröffentlichung verwalten]** von **[!UICONTROL Aktion]** **[!UICONTROL Veröffentlichung rückgängig machen]** und **[!UICONTROL Planen]** **[!UICONTROL Jetzt]** aus.
   2. Klicken oder tippen Sie auf **[!UICONTROL Weiter].**
   3. Bestätigen Sie in **[!UICONTROL Scope]** Ihre Auswahl und tippen Sie auf **[!UICONTROL Veröffentlichung im Markenportal rückgängig machen]**.

   ![confirm-unpublish](assets/confirm-unpublish.png)

   **Rückgängigmachen der Veröffentlichung aus dem Markenportal**

   So können Sie die Veröffentlichung eines Ordners in Brand Portal zu einem späteren Zeitpunkt rückgängig machen:

   1. Wählen Sie auf der Seite **[!UICONTROL Veröffentlichung verwalten]** von **[!UICONTROL Aktion]** **[!UICONTROL Rückgängigmachen der Veröffentlichung aus dem Markenportal]** und **[!UICONTROL Einplanen]** **[!UICONTROL Später].**.
   2. Wählen Sie ein **[!UICONTROL Aktivierungsdatum]** aus und geben Sie die Zeit an. Tippen Sie auf **[!UICONTROL Weiter]**.
   3. Bestätigen Sie innerhalb von **[!UICONTROL Scope]** Ihre Auswahl und tippen Sie auf **[!UICONTROL Weiter]**.
   4. Geben Sie einen **[!UICONTROL Workflow-Titel]** unter **[!UICONTROL Workflows]** an. Tippen Sie auf **[!UICONTROL Veröffentlichung später rückgängig machen].**

      ![unpublishworkflows](assets/unpublishworkflows.png)


>[!NOTE]
>
>Das Verfahren zum Veröffentlichen/Rückgängigmachen der Veröffentlichung eines Assets im/vom Markenportal ist dem entsprechenden Vorgang für einen Ordner ähnlich.
