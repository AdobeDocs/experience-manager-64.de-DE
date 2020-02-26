---
title: AI-basiertes Tagging mit dem Smart Content Service konfigurieren
description: Erfahren Sie, wie Sie Smart-Tagging und optimierte Smart-Tags in AEM mit dem Smart Content Service konfigurieren.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 90d39315207129aa4fc616e6fffb4bad5c450a7b

---


# Configure asset tagging using the Smart Content Service {#configure-asset-tagging-using-the-smart-content-service}

Erfahren Sie, wie Sie Smart-Tagging und optimierte Smart-Tags in AEM mit dem Smart Content Service konfigurieren.

Sie können Adobe Experience Manager (AEM) in den Dienst für intelligente Inhalte integrieren. Verwenden Sie diese Konfiguration, um von AEM aus auf den Smart Content Service zuzugreifen und Ihre Bilder automatisch mit Tags zu versehen.

Der Artikel beschreibt die folgenden Hauptaufgaben, die zum Konfigurieren des Smart Content Service erforderlich sind. Am Back-End authentifiziert der AEM-Server Ihre Service-Anmeldeinformationen beim Adobe IO-Gateway, bevor Ihre Anfrage an den Smart Content Service weitergeleitet wird.

1. Erstellen Sie in AEM eine Konfiguration für den Smart Content Service, um einen öffentlichen Schlüssel zu erstellen. Erhalten Sie ein öffentliches Zertifikat für die OAuth-Integration.
1. Erstellen Sie eine Integration in Adobe I/O und laden Sie den generierten öffentlichen Schlüssel hoch.
1. Konfigurieren Sie die AEM-Instanz mithilfe des API-Schlüssels und anderen Anmeldeinformationen aus Adobe I/O.
1. Aktivieren Sie optional das automatische Tagging beim Hochladen eines Assets.

## Voraussetzungen {#prerequisites}

Stellen Sie vor der Verwendung des Smart Content Service Folgendes sicher, um eine Integration in Adobe I/O zu erstellen:

* Es ist ein Adobe ID-Konto mit Administratorrechten für die Organisation vorhanden.
* Der Smart Content Service ist für Ihre Organisation aktiviert.

To enable Enhanced Smart Tags, in addition to the above, also install the latest [AEM service pack](https://helpx.adobe.com/experience-manager/aem-releases-updates.html).

## Erhalten eines öffentlichen Zertifikats {#obtain-public-certificate}

Ein öffentliches Zertifikat ermöglicht Ihnen die Authentifizierung Ihres Profils in Adobe I/O.

1. Tippen Sie in der AEM-Benutzeroberfläche auf das AEM-Logo und öffnen Sie **[!UICONTROL Tools]** > **[!UICONTROL Cloud-Services]** > **[!UICONTROL Legacy-Cloud-Services]**.

1. Tippen/Klicken Sie auf der Seite „Cloud Services“ unter **[!UICONTROL Assets Smart Tags]** auf **[!UICONTROL Jetzt konfigurieren]**.
1. Geben Sie im Dialogfeld **[!UICONTROL Konfiguration erstellen]** einen Titel und einen Namen für die Smart-Tags-Konfiguration ein. Tippen/klicken Sie auf **[!UICONTROL Erstellen]**.
1. Verwenden Sie im Dialogfeld **[!UICONTROL AEM Smart Content Service]** die folgenden Werte:

   **[!UICONTROL Dienst-URL]**: `https://mc.adobe.io/marketingcloud/smartcontent`

   **[!UICONTROL Autorisierungsserver]**: `https://ims-na1.adobelogin.com`

   Lassen Sie die anderen Felder vorerst leer (Werte werden später bereitgestellt). Tippen/klicken Sie auf **[!UICONTROL OK]**.

   ![Dialogfeld von AEM Smart Content Service zum Bereitstellen der Content Service-URL](assets/aem_scs.png)

   >[!NOTE]
   >
   >The URL provided as [!UICONTROL Service URL] is not accessible via browser and generates a 404 error. Die Konfiguration funktioniert mit demselben Wert des Parameters [!UICONTROL Service URL] . Informationen zum Gesamtstatus und Wartungszeitplan für Adobe I/O finden Sie unter [https://status.adobe.com](https://status.adobe.com).

1. Tippen/klicken Sie auf **[!UICONTROL Öffentliches Zertifikat für OAuth-Integration herunterladen]** und laden Sie die öffentliche Zertifikatdatei `AEM-SmartTags.crt` herunter.

   ![Darstellung der für den Smart-Tagging-Service erstellten Einstellungen](assets/download_link.png)

## Adobe I/O-Integration erstellen {#create-adobe-i-o-integration}

Um Smart Content Service-APIs zu verwenden, erstellen Sie eine Integration in Adobe I/O zur Generierung von API-Schlüssel, ID des technischen Kontos, Organisations-ID und Client-Geheimnis.

1. Greifen Sie auf [https://console.adobe.io](https://console.adobe.io/) zu.
1. Wählen Sie auf der Seite **[!UICONTROL Integrationen]** Ihre Organisation aus.
1. Tippen/klicken Sie auf **[!UICONTROL Neue Integration]**.
1. Wählen Sie auf der Seite **[!UICONTROL Neue Integration erstellen]** die Option **[!UICONTROL Auf eine API zugreifen]** aus. Tippen/Klicken Sie auf **[!UICONTROL Weiter]**.
1. Wählen Sie unter **[!UICONTROL Experience Cloud]** die Option **[!UICONTROL Smart Content]**. Tippen/Klicken Sie auf **[!UICONTROL Weiter]**.

   ![Auswählen der Option „Smart Content“ unter „Experience Cloud“ aus den verfügbaren Optionen beim Erstellen einer neuen Integration](assets/smart_content.png)

1. Wählen Sie auf der nächsten Seite **[!UICONTROL Neue Integration]** aus. Tippen/Klicken Sie auf **[!UICONTROL Weiter]**.
1. Geben Sie auf der Seite **[!UICONTROL Integrationsdetails]** einen Namen für das Integrations-Gateway ein und fügen Sie eine Beschreibung hinzu.
1. Laden Sie in den **[!UICONTROL Zertifikaten zu öffentlichen Schlüsseln]** die Datei `AEM-SmartTags.crt` hoch, die Sie weiter oben heruntergeladen haben.
1. Tippen/klicken Sie auf **[!UICONTROL Integration erstellen]**.
1. Tippen/klicken Sie auf **[!UICONTROL Mit Integrationsdetails fortfahren]**, um die Integrationsinformationen anzuzeigen.

   ![Auf der Registerkarte „Übersicht“ können Sie die für die Integration bereitgestellten Informationen überprüfen.](assets/integration_details.png)

## Konfigurieren des Smart Content Service {#configure-smart-content-service}

Verwenden Sie zum Konfigurieren der Integration die Werte der Felder „ID des technischen Kontos“, „Organisations-ID“, „Client-Geheimnis“, „Autorisierungsserver“ und „API-Schlüssel“ aus der Adobe I/O-Integration. Das Erstellen einer Smart-Tags-Cloud-Konfiguration ermöglicht die Authentifizierung von API-Anfragen von der AEM-Instanz.

1. Tippen/klicken Sie in der AEM-Benutzeroberfläche auf das AEM-Logo. Navigieren Sie zu **[!UICONTROL Tools > Cloud-Service > Legacy-Cloud-Services]**, um die Cloud-Services-Konsole zu öffnen.
1. Öffnen Sie unter den **[!UICONTROL Smart-Tags für Assets]** die oben erstellte Konfiguration. Klicken Sie auf der Seite mit den Serviceeinstellungen auf **[!UICONTROL Bearbeiten]**.
1. Verwenden Sie im Dialogfeld **[!UICONTROL AEM Smart Content Service]** die vorausgefüllten Werte für die Felder **[!UICONTROL Service-URL]** und **[!UICONTROL Autorisierungsserver]**.
1. Verwenden Sie für die Felder API-Schlüssel, Technische Konto-ID, Organisations-ID und Geheimer Clientschlüssel die oben generierten Werte.

## Überprüfen der Konfiguration {#validate-the-configuration}

Nachdem Sie die Konfiguration abgeschlossen haben, können Sie die Konfiguration mit einem JMX MBean überprüfen. Führen Sie zum Überprüfen die folgenden Schritte aus.

1. Um in AEM OSGi zu öffnen, klicken Sie auf **[!UICONTROL Werkzeuge > Vorgänge > Web-Konsole]**. Klicken Sie auf **[!UICONTROL Haupt > JMX]**.
1. Klicken Sie auf **[!UICONTROL com.day.cq.dam.similaritysearch.internal.impl]**. Die Seite **[!UICONTROL SimilaritySearch Miscellaneous Tasks]** wird geöffnet
1. Klicken Sie auf **[!UICONTROL validateConfigs()]**. In the **[!UICONTROL Validate Configurations]** dialog, click **[!UICONTROL Invoke]**.

   Das Überprüfungsergebnis wird im selben Dialogfeld angezeigt.

## Enable smart tagging in the DAM Update Asset workflow (Optional) {#enable-smart-tagging-in-the-update-asset-workflow-optional}

1. Tippen Sie in der AEM-Benutzeroberfläche auf das AEM-Logo und öffnen Sie **[!UICONTROL Tools > Workflow > Modelle]**.
1. Wählen Sie auf der Seite **[!UICONTROL Workflowmodelle]** das **[!UICONTROL DAM Update Asset]**-Workflowmodell.
1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Bearbeiten]**. .
1. Erweitern Sie das Seitenbedienfeld, um die Schritte anzuzeigen. Ziehen Sie den Schritt **[!UICONTROL Smart Tag-Asset]**, der im Abschnitt „DAM-Workflow“ verfügbar ist, und platzieren Sie ihn nach dem Schritt **[!UICONTROL Prozessminiaturansichten]**.

   ![Schritt zum Hinzufügen von Smart Tag Assets nach dem Schritt „Miniaturansichten verarbeiten“ im Workflow „DAM-Update-Asset“](assets/chlimage_1-105.png)

1. Öffnen Sie den Schritt im Bearbeitungsmodus. Stellen Sie unter **[!UICONTROL Erweiterte Einstellungen]** sicher, dass die Option **[!UICONTROL Handler-Erweiterung]** ausgewählt ist.

   ![chlimage_1-106](assets/chlimage_1-106.png)

1. Wählen Sie auf der Registerkarte **[!UICONTROL Argumente]** die Option **[!UICONTROL Fehler ignorieren]**, wenn der Workflow auch dann abgeschlossen werden soll, falls der automatische Tag-Schritt fehlschlägt.

   ![chlimage_1-107](assets/chlimage_1-107.png)

   Um Assets unabhängig davon mit Tags zu versehen, ob die Smart-Tagging-Funktion für Ordner aktiviert ist, wählen Sie **[!UICONTROL Smart-Tag-Flag ignorieren]** aus.

   ![chlimage_1-108](assets/chlimage_1-108.png)

1. Tippen/klicken Sie auf **[!UICONTROL OK]**, um den Prozessschritt zu schließen, und speichern Sie dann den Workflow.

>[!MORELIKETHIS]
>
>* [Intelligente Tags in AEM Assets](https://helpx.adobe.com/experience-manager/kt/assets/using/smart-tags-feature-video-understand.html)
>* [Verwenden intelligenter Tags mit AEM Assets](https://helpx.adobe.com/experience-manager/kt/assets/using/smart-tags-feature-video-use.html)
>* [Erweiterte Smart-Tags mit AEM Assets verwenden](https://helpx.adobe.com/experience-manager/kt/assets/using/enhanced-smart-tags-feature-video-use.html)
>* [Einrichten erweiterter Smart-Tags in AEM Assets](https://helpx.adobe.com/experience-manager/kt/assets/using/enhanced-smart-tags-technical-video-setup.html)

