---
title: AEM Assets-Integration mit Experience Cloud konfigurieren
description: Erfahren Sie, wie Sie die AEM Assets-Integration mit Experience Cloud konfigurieren.
feature: Asset Management
role: User, Architect, Admin
exl-id: f8629c30-1901-4b6e-b5a6-e46ee3c72fba
source-git-commit: 63a4304a1a10f868261eadce74a81148026390b6
workflow-type: tm+mt
source-wordcount: '1017'
ht-degree: 43%

---

# AEM Assets-Integration mit Experience Cloud konfigurieren {#configure-aem-assets-integration-with-experience-cloud-and-creative-cloud}

Wenn Sie Adobe Experience Cloud-Kunde sind, können Sie Ihre Assets in Adobe Experience Manager Assets mit Adobe Creative Cloud synchronisieren und umgekehrt. Sie können Ihre Assets auch mit Experience Cloud synchronisieren und umgekehrt. Sie können diese Synchronisation einrichten durch [!DNL Adobe I/O]. Der aktualisierte Name von [!DNL Adobe Marketing Cloud] is [!DNL Adobe Experience Cloud].

Der Workflow zur Einrichtung dieser Integration ist:

1. Erstellen Sie eine Authentifizierung in [!DNL Adobe I/O] über ein öffentliches Gateway und eine Anwendungs-ID abrufen.
1. Erstellen Sie ein Profil in Ihrer AEM Assets-Instanz mithilfe der Anwendungs-ID.
1. Verwenden Sie diese Konfiguration, um Ihre Assets zu synchronisieren.

Am Backend authentifiziert der AEM-Server Ihr Profil gegenüber dem Gateway und synchronisiert dann die Daten zwischen Assets und Experience Cloud.

>[!NOTE]
>
>Diese Funktion wird in AEM Assets nicht mehr unterstützt. Suchen von Ersetzungen in [Best Practices für die Integration von AEM und Creative Clouden](/help/assets/aem-cc-integration-best-practices.md). Bei Abfragen: [Adobe-Support kontaktieren](https://www.adobe.com/account/sign-in.supportportal.html).

<!-- Hiding this for now via cqdoc-16834.
![Flow of data when AEM Assets and Creative Cloud are integrated](assets/chlimage_1-287.png)

>[!NOTE]
>
>Sharing assets between Adobe Experience Cloud and Adobe Creative Cloud requires administrator privileges on the AEM instance.
-->

## Erstellen einer Anwendung {#create-an-application}

1. Greifen Sie auf die Adobe Developer Gateway-Schnittstelle zu, indem Sie sich unter [https://legacy-oauth.cloud.adobe.io](https://legacy-oauth.cloud.adobe.io/) einloggen.

   >[!NOTE]
   >
   >Sie benötigen Administratorrechte, um eine Anwendungs-ID zu erstellen.

1. Navigieren Sie im linken Bereich zu **[!UICONTROL Entwicklertools]** > **[!UICONTROL Anwendungen]** um eine Liste der Anwendungen anzuzeigen.
1. Klicken **[!UICONTROL Hinzufügen]** ![aem_assets_addcircle_icon](assets/aem_assets_addcircle_icon.png) , um eine Anwendung zu erstellen.
1. Wählen Sie aus der Liste **[!UICONTROL Client-Anmeldeinformationen]** die Option **[!UICONTROL Dienstkonto (JWT-Assertion)]** aus. Dies ist ein Server-zu-Server-Kommunikationsdienst für die Serverauthentifizierung.

   ![chlimage_1-288](assets/chlimage_1-288.png)

1. Geben Sie einen Namen für die Anwendung und eine optionale Beschreibung an.
1. Wählen Sie aus der Liste **[!UICONTROL Organisation]** die Organisation aus, für die Sie die Assets synchronisieren möchten.
1. Aus dem **[!UICONTROL Anwendungsbereich]** Liste auswählen **[!UICONTROL dam-read]**, **[!UICONTROL dam-sync]**, **[!UICONTROL dam-write]** und **[!UICONTROL cc-share]**.
1. Klicken Sie auf **[!UICONTROL Erstellen]**. Eine Meldung informiert Sie darüber, dass die Anwendung erstellt wurde.

   ![Benachrichtigung über die erfolgreiche Erstellung der Anwendung zur Integration von AEM Assets in Adobe Creative Cloud](assets/chlimage_1-289.png)

1. Kopieren Sie die **[!UICONTROL Anwendungs-ID]**, die für die neue Anwendung generiert wird.

   >[!CAUTION]
   >
   >Achten Sie darauf, dass Sie nicht versehentlich das **[!UICONTROL Anwendungsgeheimnis]** anstelle der **[!UICONTROL Anwendungs-ID]** kopieren.

## Hinzufügen einer neuen Konfiguration zu Experience Cloud {#add-a-new-configuration}

1. Klicken Sie auf das AEM-Logo in der Benutzeroberfläche in Ihrer lokalen AEM Assets-Instanz und navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Cloud-Services]** > **[!UICONTROL Legacy-Cloud-Services]**.

1. Suchen Sie die **[!UICONTROL Adobe Experience Cloud]** Dienst. Wenn keine Konfigurationen vorhanden sind, klicken Sie auf **[!UICONTROL Jetzt konfigurieren]**. Wenn Konfigurationen vorhanden sind, klicken Sie auf **[!UICONTROL Konfigurationen anzeigen]** und klicken Sie auf `+` , um eine neue Konfiguration hinzuzufügen.

   >[!NOTE]
   >
   >Verwenden Sie ein Adobe ID-Konto mit Administratorrechten für die entsprechende Organisation.

1. Geben Sie im Dialogfeld **[!UICONTROL Konfiguration erstellen]** einen Titel und einen Namen für die neue Konfiguration an und klicken Sie auf **[!UICONTROL Erstellen]**.

   ![Benennen neuer Konfigurationen für die Integration mit AEM Assets und Creative Cloud](assets/cloudservices_configure_mc.png)

1. Geben Sie im Feld **[!UICONTROL Mandanten-URL]** die URL für AEM Assets ein. Wenn die URL in der Vergangenheit als `https://<tenant_id>.marketing.adobe.com`ändern Sie sie in `https://<tenant_id>.experiencecloud.adobe.com`.

   1. Navigieren Sie zu **Werkzeuge > Cloud Services > Legacy-Cloud Services**. Klicken Sie unter Adobe Experience Cloud auf **Konfigurationen anzeigen**.
   1. Wählen Sie die zu bearbeitende vorhandene Konfiguration aus. Bearbeiten Sie die Konfiguration und ersetzen Sie `marketing.adobe.com` nach `experiencecloud.adobe.com`.
   1. Speichern Sie die Konfiguration. Testen Sie die MAC-synchronisierten Replikationsagenten.

1. Im **[!UICONTROL Client-ID]** -Feld die Anwendungs-ID einzufügen, die Sie am Ende des Verfahrens kopiert haben [Anwendung erstellen](#create-an-application).

   ![Angeben der erforderlichen Anwendungs-ID-Werte für die Integration von AEM Assets und Creative Cloud](assets/cloudservices_tenant_info.png)

1. Wählen Sie unter **[!UICONTROL Synchronisierung]** die Option **[!UICONTROL Aktiviert]** aus, um die Synchronisierung zu aktivieren, und klicken Sie auf **[!UICONTROL OK]**. Wenn Sie **disabled**, funktioniert die Synchronisation in eine einzige Richtung.

1. Klicken Sie auf der Konfigurationsseite auf **[!UICONTROL Öffentlichen Schlüssel anzeigen]**, um den für Ihre Instanz generierten öffentlichen Schlüssel anzuzeigen. Klicken Sie alternativ auf **[!UICONTROL Öffentlichen Schlüssel für OAuth-Gateway herunterladen]** , um die Datei mit dem öffentlichen Schlüssel herunterzuladen. Öffnen Sie dann die Datei, um den öffentlichen Schlüssel anzuzeigen.

## Aktivieren der Synchronisierung {#enable-synchronization}

1. Anzeigen des öffentlichen Schlüssels mit einer der folgenden Methoden, die im letzten Schritt des Verfahrens erwähnt wurden [Hinzufügen einer neuen Konfiguration zu Experience Cloud](#add-a-new-configuration). Klicken Sie auf **[!UICONTROL Öffentlichen Schlüssel anzeigen]**.

1. Kopieren Sie den öffentlichen Schlüssel und fügen Sie ihn in den **[!UICONTROL Öffentlicher Schlüssel]** Feld der Konfigurationsoberfläche der Anwendung, die Sie in der [Anwendung erstellen](#create-an-application).

   ![chlimage_1-293](assets/chlimage_1-293.png)

1. Klicken Sie auf **[!UICONTROL Aktualisieren]**. Synchronisieren Sie Ihre Assets jetzt mit der AEM Assets-Instanz.

## Testen der Synchronisierung {#test-the-synchronization}

1. Klicken Sie auf das AEM in der Benutzeroberfläche Ihrer lokalen AEM Assets-Instanz und navigieren Sie zu **[!UICONTROL Instrumente]**> **[!UICONTROL Implementierung]**> **[!UICONTROL Replikation]**um die für die Synchronisierung erstellten Replikationsprofile zu finden.
1. Im **[!UICONTROL Replikation]** Seite, klicken Sie auf **[!UICONTROL Agenten für Autor]**.
1. Klicken Sie in der Liste der Profile auf das Standardreplikationsprofil zu Ihrer Organisation, um es zu öffnen.
1. Klicken Sie im Dialogfeld auf **[!UICONTROL Verbindung testen]**.

   ![Testen der Verbindung und Festlegen des Standardreplikationsprofils zu Ihrer Organisation](assets/chlimage_1-294.png)

1. Sehen Sie sich den unteren Bereich der Testergebnisse an, um zu prüfen, ob die Replikation erfolgreich war.

## Benutzer zu Experience Cloud hinzufügen {#add-users-to-experience-cloud}

1. Melden Sie sich mit Administratorberechtigungen bei Experience Cloud an.
1. Gehen Sie von den Schienen nach **[!UICONTROL Administration]** und klicken Sie anschließend auf **[!UICONTROL Enterprise Dashboard starten]**.
1. Klicken Sie in der Leiste auf **[!UICONTROL Benutzer]**, um die Seite **[!UICONTROL Benutzerverwaltung]** zu öffnen.
1. Klicken Sie in der Symbolleiste auf **Hinzufügen** ![aem_assets_add_icon](assets/aem_assets_add_icon.png).
1. Fügen Sie einen oder mehr Benutzer hinzu, denen Sie die Möglichkeit zur Freigabe von Assets für Creative Cloud bereitstellen möchten.

   >[!NOTE]
   >
   >Nur Benutzer, die Sie zu Experience Cloud hinzufügen, können Assets von AEM Assets für Creative Cloud freigeben.

## Austausch von Assets zwischen AEM Assets und Experience Cloud {#exchange-assets-between-aem-and-experience-cloud}

1. Melden Sie sich bei AEM Assets an.
1. Erstellen Sie in der Assets-Konsole einen Ordner und laden Sie einige Assets dort hoch. Erstellen Sie zum Beispiel einen Ordner **mc-demo** und laden Sie ein Asset dort hoch.
1. Wählen Sie den Ordner aus und klicken Sie auf **Freigeben** ![assets_share](assets/assets_share.png).
1. Wählen Sie im Menü die Option **[!UICONTROL Adobe Experience Cloud]** und klicken Sie auf **[!UICONTROL Freigeben]**. Eine Meldung informiert Sie, dass der Ordner für Experience Cloud freigegeben wurde.

   ![chlimage_1-295](assets/chlimage_1-295.png)

   >[!NOTE]
   >
   >Freigeben eines Assets-Ordners vom Typ `sling:OrderedFolder`, wird im Kontext der Freigabe in Adobe Experience Cloud nicht unterstützt. Wenn Sie einen Ordner bei seiner Erstellung in AEM Assets freigeben möchten, wählen Sie nicht die Option **[!UICONTROL Geordnet]** aus.

1. Aktualisieren Sie die AEM Assets-Benutzeroberfläche. Der Ordner, den Sie in der Assets-Konsole Ihrer lokalen AEM Assets-Instanz erstellt haben, wird in die Experience Cloud-Benutzeroberfläche kopiert. Das Asset, das Sie in den Ordner in AEM Assets hochladen, wird in der Ordnerkopie in Experience Cloud angezeigt, nachdem es vom AEM verarbeitet wurde.
1. Sie können auch ein Asset in die replizierte Kopie des Ordners in Experience Cloud hochladen. Nach der Verarbeitung wird das Asset im freigegebenen Ordner in AEM Assets angezeigt.

<!-- Removing as per PM guidance via https://jira.corp.adobe.com/browse/CQDOC-16834?focusedCommentId=22881523&page=com.atlassian.jira.plugin.system.issuetabpanels:comment-tabpanel#comment-22881523.
## Exchange assets between AEM Assets and Creative Cloud {#exchange-assets-between-aem-assets-and-creative-cloud}

AEM Assets lets you share folders containing assets with Adobe Creative Cloud users.

1. In the Assets console, select the folder to share with Creative Cloud.
1. From the toolbar, click **[!UICONTROL Share]** ![assets_share](assets/assets_share.png).
1. From the list, select the **[!UICONTROL Adobe Creative Cloud]** option.

   >[!NOTE]
   >
   >The options are available for users with read permissions on the root. Users must have the required permission to access the replication agent information of Marketing Cloud.

1. In the **[!UICONTROL Creative Cloud Sharing]** page, add the user to share the folder with and choose a role for the user. Click **[!UICONTROL Save]** and click **[!UICONTROL OK]**.

1. Log on to Creative Cloud with the credentials of the user you shared the folder with. The shared folder is available in Creative Cloud.

The AEM Assets-Marketing Cloud synchronization is designed in a way that the user machine instance from where the asset is uploaded retains the right to modify the asset. Only these changes are propagated to the other instance.

For example, if an asset is uploaded from an AEM Assets (on premises) instance, the changes to the asset from this instance are propagated to the Marketing Cloud instance. However, the changes done from the Marketing Cloud instance to the same asset aren’t propagated to the AEM instance and vice versa for asset uploaded from Marketing Cloud.
-->

>[!MORELIKETHIS]
>
>* [Best Practices für die Integration von Assets und Creative Clouden](/help/assets/aem-cc-integration-best-practices.md)
>* [Best Practices für die Ordnerfreigabe von Assets in Creative Cloud](/help/assets/aem-cc-folder-sharing-best-practices.md)

