---
title: Veröffentlichen von Ordnern in Brand Portal
description: Erfahren Sie, wie Sie Assets im Markenportal veröffentlichen und die Veröffentlichung rückgängig machen.
contentOwner: VG
feature: Brand Portal
role: Business Practitioner
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 52%

---


# Veröffentlichen von Assets in Brand Portal {#publish-assets-to-brand-portal}

Als Adobe Experience Manager (AEM) Asset-Administrator können Sie Assets für Ihr Unternehmen in der AEM Assets Brand Portal-Instanz veröffentlichen (oder den Veröffentlichungs-Workflow auf ein späteres Datum/eine spätere Uhrzeit planen). Zunächst müssen Sie AEM Assets jedoch mit Brand Portal konfigurieren. Weitere Informationen finden Sie unter [Konfigurieren der von AEM Assets mit Brand Portal](configure-aem-assets-with-brand-portal.md).

Nachdem Sie ein Asset veröffentlicht haben, steht es Benutzern im Markenportal zur Verfügung.

Wenn Sie nachfolgende Änderungen am ursprünglichen Asset in AEM Assets vornehmen, werden die Änderungen erst dann im Markenportal übernommen, wenn Sie das Asset erneut veröffentlichen. Mit dieser Funktion wird sichergestellt, dass Änderungen im Rahmen der laufenden Bearbeitung nicht in Brand Portal verfügbar sind. Nur genehmigte, von einem Administrator veröffentlichte Änderungen sind in Brand Portal verfügbar.

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

## Sofortiges Veröffentlichen von Assets {#publish-now}

Um die ausgewählten Assets in Brand Portal zu veröffentlichen, führen Sie einen der folgenden Schritte aus:

* Wählen Sie in der Symbolleiste **[!UICONTROL Quick Publish]** aus. Wählen Sie dann im Menü **[!UICONTROL In Markenportal veröffentlichen]**.

* Wählen Sie in der Symbolleiste **[!UICONTROL Veröffentlichung verwalten]** aus.

   1. Wählen Sie dann unter **[!UICONTROL Aktion]** **[!UICONTROL In Markenportal veröffentlichen]** und unter **[!UICONTROL Einplanen]** **[!UICONTROL Jetzt]**. Klicken oder tippen Sie auf **[!UICONTROL Weiter].**

   2. Bestätigen Sie in **[!UICONTROL Scope]** Ihre Auswahl und tippen/klicken Sie auf **[!UICONTROL In Markenportal veröffentlichen]**.

Eine Meldung erscheint, die besagt, dass die Assets zur Veröffentlichung in Brand Portal in die Warteschlange gestellt wurden. Melden Sie sich bei der Brand Portal-Benutzeroberfläche an, um die veröffentlichten Assets zu sehen.

## Assets später veröffentlichen {#publish-later}

So planen Sie die Veröffentlichung der Assets in Brand Portal zu einem späteren Zeitpunkt:

1. Nachdem Sie die zu veröffentlichenden Assets/Ordner ausgewählt haben, wählen Sie in der Symbolleiste oben die Option **[!UICONTROL Veröffentlichung verwalten]**.
2. Wählen Sie auf der Seite **[!UICONTROL Veröffentlichung verwalten]** die Option **[!UICONTROL In Markenportal veröffentlichen]** aus **[!UICONTROL Aktion]** und wählen Sie **[!UICONTROL Später]** aus **[!UICONTROL Einplanen]**.

   ![publishlaterbp-1](assets/publishlaterbp-1.png)

3. Wählen Sie ein **[!UICONTROL Aktivierungsdatum]** aus und geben Sie die Zeit an. Klicken oder tippen Sie auf **[!UICONTROL Weiter]**.
4. Wählen Sie ein **[!UICONTROL Aktivierungsdatum]** aus und geben Sie die Zeit an. Klicken oder tippen Sie auf **[!UICONTROL Weiter]**.
5. Geben Sie einen Workflow-Titel unter **[!UICONTROL Workflows]** an. Tippen/klicken Sie auf **[!UICONTROL Später veröffentlichen]**.

   ![publishworkflow](assets/publishworkflow.png)

Melden Sie sich jetzt beim Markenportal an, um zu sehen, ob die veröffentlichten Assets auf der Benutzeroberfläche des Markenportals verfügbar sind.

![bp_631_landing_page](assets/bp_landing_page.png)
