---
title: Freigeben privater Ordner
description: Erfahren Sie, wie Sie in Adobe Experience Manager (AEM) Assets einen privaten Ordner erstellen, ihn mit anderen Benutzern teilen und ihnen verschiedene Berechtigungen zuweisen können.
contentOwner: AG
feature: Collaboration
role: Business Practitioner
translation-type: tm+mt
source-git-commit: 4acf159ae1b9923a9c93fa15faa38c7f4bc9f759
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 100%

---


# Freigeben privater Ordner {#private-folder-sharing}

Sie können einen privaten Ordner in der Adobe Experience Manager (AEM) Assets-Benutzeroberfläche erstellen, der nur für Sie verfügbar ist. Sie können diesen privaten Ordner auch für andere Benutzer freigeben und diesen Benutzern verschiedene Berechtigungen zuweisen. Je nach der zugewiesenen Berechtigungsstufe können Benutzer verschiedene Aufgaben mit dem Ordner ausführen, wie das Anzeigen oder Bearbeiten von Assets im Ordner.

1. Klicken oder tippen Sie in der Konsole „Assets“ von der Symbolleiste aus auf **[!UICONTROL Erstellen]** und wählen Sie dann **[!UICONTROL Ordner]** aus dem Menü aus.

   ![chlimage_1-411](assets/chlimage_1-411.png)

1. Geben Sie in das Dialogfeld **[!UICONTROL Ordner hinzufügen]** einen Titel und einen Namen (optional) für den Ordner ein und wählen Sie **[!UICONTROL Privat]** aus.

   ![chlimage_1-412](assets/chlimage_1-412.png)

1. Tippen oder klicken Sie auf **[!UICONTROL Erstellen]**. Ein privater Ordner wird auf der Assets-Benutzeroberfläche erstellt.

   ![chlimage_1-413](assets/chlimage_1-413.png)

1. Um den Ordner für andere Benutzer freizugeben und ihnen Berechtigungen zuzuweisen, wählen Sie den Ordner aus und tippen/klicken Sie auf das Symbol **[!UICONTROL Eigenschaften]** in der Symbolleiste.

   ![chlimage_1-414](assets/chlimage_1-414.png)

   >[!NOTE]
   >
   >Der Ordner wird erst dann für andere Benutzer sichtbar, wenn Sie ihn freigeben.

1. Wählen Sie auf der Seite „Ordnereigenschaften“ einen Benutzer in der Liste **[!UICONTROL Benutzer hinzufügen]** aus, weisen Sie dem Benutzer eine Rolle für den privaten Ordner zu und klicken Sie auf **[!UICONTROL Hinzufügen]**.

   ![chlimage_1-415](assets/chlimage_1-415.png)

   >[!NOTE]
   >
   >Sie können dem Benutzer, für den Sie den Ordner freigeben, verschiedene Rollen zuweisen, wie Bearbeiter, Eigentümer oder Betrachter. Wenn Sie dem Benutzer eine Eigentümerrolle zuweisen, hat der Benutzer Editor-Berechtigungen für den Ordner. Darüber hinaus kann der Benutzer den Ordner für andere freigeben. Wenn Sie die Rolle „Editor“ zuweisen, kann der Benutzer die Assets in Ihrem privaten Ordner bearbeiten. Wenn Sie die Rolle „Betrachter“ zuweisen, kann der Benutzer die Assets im privaten Ordner lediglich anzeigen.

1. Klicken Sie auf **[!UICONTROL Speichern]**. Je nach der zugewiesenen Rolle erhält der Benutzer einen Satz Berechtigungen für den privaten Ordner, wenn er sich bei AEM Assets anmeldet.
1. Klicken Sie auf **[!UICONTROL OK]** zum Schließen der Bestätigungsmeldung.
1. Der Benutzer, für den Sie den Ordner freigeben, erhält eine Freigabebenachrichtigung. Melden Sie sich bei AEM Assets mit den Anmeldedaten des Benutzers an, um die Benachrichtigungen anzuzeigen.

   ![chlimage_1-416](assets/chlimage_1-416.png)

1. Tippen/klicken Sie auf das Symbol „Benachrichtigungen“, um eine Liste der Benachrichtigungen zu öffnen.

   ![chlimage_1-417](assets/chlimage_1-417.png)

1. Klicken oder tippen Sie auf den Eintrag für den privaten Ordner, der vom Administrator freigegeben wurde, um den Ordner zu öffnen.

>[!NOTE]
>
>Um einen privaten Ordner zu erstellen, benötigen Sie die Berechtigungen „Lesen“ und „ACL bearbeiten“ für den übergeordneten Ordner, unter dem Sie einen privaten Ordner erstellen möchten. Wenn Sie kein Administrator sind, werden diese Berechtigungen auf */content/dam* nicht standardmäßig für Sie aktiviert. In diesem Fall müssen Sie zunächst diese Berechtigungen für Ihre Benutzer-ID/Gruppe erhalten, bevor Sie versuchen, private Ordner zu erstellen oder Ordnereinstellungen anzuzeigen.

