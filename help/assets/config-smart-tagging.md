---
title: Konfigurieren Sie Asset-Tagging mit dem Smart Content Service.
description: Erfahren Sie, wie Sie Smart-Tagging und verbessertes Smart-Tagging konfigurieren in [!DNL Adobe Experience Manager], mithilfe des Smart Content Service.
contentOwner: AG
feature: Smart Tags,Tagging
role: Admin
exl-id: 11c5dd92-f824-41d2-9ab2-b32bdeae01b6
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '1212'
ht-degree: 49%

---

# Konfigurieren von Asset-Tags mit dem Smart Content Service {#configure-asset-tagging-using-the-smart-content-service}

Sie können [!DNL Adobe Experience Manager] mit dem Smart Content Service mit [!DNL Adobe Developer Console]. Verwenden Sie diese Konfiguration, um von aus auf den Smart Content Service zuzugreifen [!DNL Experience Manager].

Der Artikel beschreibt die folgenden Hauptaufgaben, die zum Konfigurieren des Smart Content Service erforderlich sind. Am Backend wird die [!DNL Experience Manager] -Server authentifiziert Ihre Dienstanmeldeinformationen mit dem [!DNL Adobe Developer Console] Gateway vor der Weiterleitung Ihrer Anforderung an den Smart Content Service.

1. [Erstellen Sie in eine Konfiguration für den Smart Content Service, um einen öffentlichen Schlüssel zu erstellen. ](#obtain-public-certificate)[!DNL Experience Manager] [Erlangen Sie ein öffentliches Zertifikat](#obtain-public-certificate) für die OAuth-Integration.

1. [Erstellen Sie eine Integration in der Adobe Developer Console](#create-adobe-i-o-integration) und laden Sie den generierten öffentlichen Schlüssel hoch.

1. [Implementierung konfigurieren](#configure-smart-content-service) Verwendung des API-Schlüssels und anderer Anmeldeinformationen von [!DNL Adobe Developer Console].

1. [Testen Sie die Konfiguration](#validate-the-configuration).

1. Optional, [Aktivieren des automatischen Tagging beim Hochladen von Assets](#enable-smart-tagging-in-the-update-asset-workflow-optional).

## Voraussetzungen {#prerequisites}

Bevor Sie den Smart Content Service verwenden, stellen Sie Folgendes sicher, um eine Integration in [!DNL Adobe Developer Console]:

* Es ist ein Adobe ID-Konto mit Administratorrechten für die Organisation vorhanden.

* Der Smart Content ist für Ihre Organisation aktiviert.

Um optimierte Smart-Tags zu aktivieren, installieren Sie zusätzlich zu den oben genannten auch die neuesten [Experience Manager Service Pack](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/aem-releases-updates.html?lang=de).

## Erstellen der Konfiguration des Smart Content Service zum Abrufen eines öffentlichen Zertifikats {#obtain-public-certificate}

Mit einem öffentlichen Zertifikat können Sie Ihr Profil bei [!DNL Adobe Developer Console].

1. Im [!DNL Experience Manager] Benutzeroberfläche, Zugriff **[!UICONTROL Instrumente]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Ältere Cloud Services]**.

1. Klicken Sie auf der Seite &quot;Cloud Services&quot;auf **[!UICONTROL Jetzt konfigurieren]** under **[!UICONTROL Smart-Tags für Assets]**.

1. Geben Sie im Dialogfeld **[!UICONTROL Konfiguration erstellen]** einen Titel und einen Namen für die Smart-Tags-Konfiguration ein. Klicken Sie auf **[!UICONTROL Erstellen]**.

1. Verwenden Sie im Dialogfeld **[!UICONTROL AEM Smart Content Service]** die folgenden Werte:

   **[!UICONTROL Service-URL]**: `https://mc.adobe.io/marketingcloud/smartcontent`

   **[!UICONTROL Autorisierungsserver]**: `https://ims-na1.adobelogin.com`

   Lassen Sie die anderen Felder vorerst leer (Werte werden später bereitgestellt). Klicken Sie auf **[!UICONTROL OK]**.

   ![Dialogfeld &quot;Experience Manager Smart Content Service&quot;zur Bereitstellung der Inhaltsdienst-URL](assets/aem_scs.png)


   *Abbildung: Dialogfeld &quot;Smart Content Service&quot;zur Bereitstellung der Content Service-URL*

   >[!NOTE]
   >
   >Die als [!UICONTROL Dienst-URL] ist nicht über den Browser zugänglich und erzeugt einen 404-Fehler. Die Konfiguration funktioniert mit demselben Wert für [!UICONTROL Dienst-URL] Parameter. Informationen zum Gesamtbetriebsstatus und Wartungszeitplan finden Sie unter [https://status.adobe.com](https://status.adobe.com).

1. Klicken **[!UICONTROL Öffentliches Zertifikat für OAuth-Integration herunterladen]** und laden Sie die öffentliche Zertifikatdatei herunter `AEM-SmartTags.crt`.

   ![Darstellung der für den Smart-Tagging-Service erstellten Einstellungen](assets/smart-tags-download-public-cert.png)


   *Abbildung: Einstellungen für den Smart-Tagging-Dienst*

### Neu konfigurieren, wenn ein Zertifikat abläuft {#certrenew}

Nachdem ein Zertifikat abgelaufen ist, wird es nicht mehr als vertrauenswürdig eingestuft. Sie können ein abgelaufenes Zertifikat nicht verlängern. Um ein neues Zertifikat hinzuzufügen, führen Sie diese Schritte aus.

1. Melden Sie sich bei Ihrer [!DNL Experience Manager]-Implementierung als Administrator an. Klicken Sie auf **[!UICONTROL Tools]** > **[!UICONTROL Sicherheit]** > **[!UICONTROL Benutzer]**.

1. Suchen und finden Sie **[!UICONTROL dam-update-service]**-Benutzer und klicken Sie darauf. Klicken Sie auf die Registerkarte **[!UICONTROL Keystore]**.

1. Löschen Sie den vorhandenen **[!UICONTROL similaritysearch]**-Keystore mit dem abgelaufenen Zertifikat. Klicken Sie auf **[!UICONTROL Speichern und schließen]**.

   ![Löschen Sie den vorhandenen Eintrag similaritysearch in Keystore, um ein neues Sicherheitszertifikat hinzuzufügen.](assets/smarttags_delete_similaritysearch_keystore.png)

   *Abbildung: Löschen des vorhandenen Eintrags `similaritysearch` in Keystore, um ein neues Sicherheitszertifikat hinzuzufügen.*

1. Navigieren Sie zu **[!UICONTROL Werkzeuge]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Legacy-Cloud Services]**. Klicken Sie auf **[!UICONTROL Asset-Smart-Tags]** > **[!UICONTROL Konfiguration anzeigen]** > **[!UICONTROL Verfügbare Konfigurationen]**. Klicken Sie auf die gewünschte Konfiguration.

1. Um ein öffentliches Zertifikat herunterzuladen, klicken Sie auf **[!UICONTROL Öffentliches Zertifikat für OAuth-Integration herunterladen]**.

1. Rufen Sie [https://console.adobe.io](https://console.adobe.io) auf und navigieren Sie zu den vorhandenen Smart Content Services auf der Seite **[!UICONTROL Integrationen]**. Laden Sie das neue Zertifikat hoch. Weitere Informationen finden Sie in den Anweisungen unter [Integration der Adobe Developer Console erstellen](#create-adobe-i-o-integration).

## Integration der Adobe Developer Console erstellen {#create-adobe-i-o-integration}

Um Smart Content Service-APIs zu verwenden, erstellen Sie eine Integration in der Adobe Developer Console, um [!UICONTROL API-Schlüssel] (generiert in [!UICONTROL CLIENT-ID] Adobe Developer Console-Integration), [!UICONTROL TECHNISCHE KONTO-ID], [!UICONTROL ORGANISATIONS-ID]und [!UICONTROL CLIENT SECRET] für [!UICONTROL Einstellungen für den Smart-Tagging-Dienst für Assets] der Cloud-Konfiguration in [!DNL Experience Manager].

1. Rufen Sie [https://console.adobe.io](https://console.adobe.io/) in einem Browser auf. Wählen Sie das entsprechende Konto aus und vergewissern Sie sich, dass die zugehörige Organisationsrolle „Systemadministrator“ ist.

1. Erstellen Sie ein Projekt mit einem beliebigen Namen. Klicken Sie auf **[!UICONTROL API hinzufügen]**.

1. Wählen Sie auf der Seite **[!UICONTROL API hinzufügen]** die Option **[!UICONTROL Experience Cloud]** und dann **[!UICONTROL Smart Content]** aus. Klicken Sie auf **[!UICONTROL Weiter]**.

1. Wählen Sie **[!UICONTROL Öffentlichen Schlüssel hochladen]** aus. Stellen Sie die von [!DNL Experience Manager] heruntergeladenen Zertifikatdatei bereit. Die Meldung [!UICONTROL Öffentliche(r) Schlüssel erfolgreich hochgeladen] wird angezeigt. Klicken Sie auf **[!UICONTROL Weiter]**.

   Die Seite [!UICONTROL Neue Dienstkonto (JWT)-Anmeldedaten erstellen] zeigt den öffentlichen Schlusselle für das Dienstkonto an, das Sie gerade konfiguriert haben.

1. Klicken Sie auf **[!UICONTROL Weiter]**.

1. Wählen Sie auf der Seite **[!UICONTROL Produktprofile auswählen]** die Option **[!UICONTROL Smart Content Services]** aus. Klicken Sie auf **[!UICONTROL Konfigurierte API speichern]**.

   Auf einer Seite werden weitere Informationen zur Konfiguration angezeigt. Lassen Sie diese Seite zum Kopieren geöffnet und fügen Sie diese Werte hinzu in [!UICONTROL Einstellungen für den Smart-Tagging-Dienst für Assets] der Cloud-Konfiguration in [!DNL Experience Manager] , um Smart-Tags zu konfigurieren.

   ![Auf der Registerkarte „Übersicht“ können Sie die für die Integration bereitgestellten Informationen überprüfen.](assets/integration_details.png)

   *Abbildung: Integrationsdetails in der Adobe Developer Console*

## Konfigurieren des Smart Content Service {#configure-smart-content-service}

Verwenden Sie zum Konfigurieren der Integration die Werte von [!UICONTROL TECHNISCHE KONTO-ID], [!UICONTROL ORGANISATIONS-ID], [!UICONTROL CLIENT SECRET]und [!UICONTROL CLIENT-ID] -Felder aus der Adobe Developer Console-Integration. Das Erstellen einer Smart-Tags-Cloud-Konfiguration ermöglicht die Authentifizierung von API-Anfragen aus dem [!DNL Experience Manager] Implementierung.

1. In [!DNL Experience Manager], navigieren Sie zu **[!UICONTROL Tools > Cloud Service > Legacy-Cloud Services]** , um [!UICONTROL Cloud Services] Konsole.

1. Öffnen Sie unter den **[!UICONTROL Smart-Tags für Assets]** die oben erstellte Konfiguration. Klicken Sie auf der Seite mit den Serviceeinstellungen auf **[!UICONTROL Bearbeiten]**.

1. Verwenden Sie im Dialogfeld **[!UICONTROL AEM Smart Content Service]** die vorausgefüllten Werte für die Felder **[!UICONTROL Service-URL]** und **[!UICONTROL Autorisierungsserver]**.

1. Für die Felder [!UICONTROL API-Schlüssel], [!UICONTROL Technische Konto-ID], [!UICONTROL Organisations-ID]und [!UICONTROL Client Secret], kopieren und verwenden Sie die folgenden Werte, die in generiert wurden: [Integration der Adobe Developer Console](#create-adobe-i-o-integration).

   | [!UICONTROL Diensteinstellungen für Smart-Tagging in Assets] | [!DNL Adobe Developer Console] Integrationsfelder |
   |--- |--- |
   | [!UICONTROL API-Schlüssel] | [!UICONTROL CLIENT-ID] |
   | [!UICONTROL ID des technischen Kontos] | [!UICONTROL TECHNISCHE KONTO-ID] |
   | [!UICONTROL Unternehmens-ID] | [!UICONTROL ORGANISATIONS-ID] |
   | [!UICONTROL Client-Geheimnis] | [!UICONTROL CLIENT SECRET] |

## Überprüfen der Konfiguration {#validate-the-configuration}

Nachdem Sie die Konfiguration abgeschlossen haben, verwenden Sie ein JMX MBean, um die Konfiguration zu validieren. Führen Sie zum Überprüfen die folgenden Schritte aus.

1. Zugriff auf [!DNL Experience Manager] Server unter `https://[aem_server]:[port]`.

1. Öffnen Sie unter **[!UICONTROL Tools > Vorgänge > Web-Konsole]** die OSGi-Konsole. Klicken Sie auf **[!UICONTROL Haupt > JMX]**.

1. Klicken Sie auf **[!UICONTROL com.day.cq.dam.similaritysearch.internal.impl]**. Wird geöffnet **[!UICONTROL ÄhnlichkeitSearch - Verschiedene Aufgaben]**.

1. Klicken Sie auf **[!UICONTROL validateConfigs()]**. Im **[!UICONTROL Konfigurationen überprüfen]** dialog, klicken Sie **[!UICONTROL Aufrufen]**.

   Die Überprüfungsergebnisse werden im selben Dialogfeld angezeigt.

## Aktivieren Sie Smart-Tagging im Workflow &quot;DAM-Update-Asset&quot;(optional) {#enable-smart-tagging-in-the-update-asset-workflow-optional}

1. In [!DNL Experience Manager], gehen Sie zu **[!UICONTROL Instrumente]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]**.

1. Wählen Sie auf der Seite **[!UICONTROL Workflow-Modelle]** das Workflow-Modell **[!UICONTROL DAM Update Asset]** aus.

1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Bearbeiten]**.

1. Erweitern Sie das Seitenbedienfeld, um die Schritte anzuzeigen. Ziehen Sie den Schritt **[!UICONTROL Asset intelligent taggen]**, der im Abschnitt „DAM-Workflow“ verfügbar ist, und platzieren Sie ihn nach dem Schritt **[!UICONTROL Prozessminiaturansichten]**.

   ![Schritt zum Hinzufügen von Smart-Tag-Assets nach dem Schritt „Miniaturansichten verarbeiten“ im Workflow „DAM-Update-Asset“](assets/smart-tag-in-dam-update-asset-workflow.png)

   *Abbildung: Schritt zum Hinzufügen von Smart-Tag-Assets nach dem Schritt „Miniaturansichten verarbeiten“ im Workflow „DAM-Update-Asset“.*

1. Öffnen Sie den Schritt im Bearbeitungsmodus. Stellen Sie unter **[!UICONTROL Erweiterte Einstellungen]** sicher, dass die Option **[!UICONTROL Handler-Erweiterung]** ausgewählt ist.

   ![Konfigurieren des Workflows &quot;DAM-Update-Asset&quot;und Hinzufügen des Schritts &quot;Smart-Tag&quot;](assets/smart-tag-step-properties-workflow1.png)


   *Abbildung: Konfigurieren des Workflows &quot;DAM-Update-Asset&quot;und Hinzufügen des Schritts &quot;Smart-Tag&quot;*

1. Wählen Sie auf der Registerkarte **[!UICONTROL Argumente]** die Option **[!UICONTROL Fehler ignorieren]**, wenn der Workflow auch dann abgeschlossen werden soll, falls der automatische Tag-Schritt fehlschlägt.

   ![Konfigurieren Sie den Workflow DAM-Update-Asset , um den Schritt &quot;Smart-Tag&quot;hinzuzufügen und den Handler-Modus auszuwählen.](assets/smart-tag-step-properties-workflow2.png)


   *Abbildung: Konfigurieren Sie den Workflow DAM-Update-Asset , um den Schritt &quot;Smart-Tag&quot;hinzuzufügen und den Handler-Modus auszuwählen.*

   Um Assets unabhängig davon mit Tags zu versehen, ob die Smart-Tagging-Funktion für Ordner aktiviert ist, wählen Sie **[!UICONTROL Smart-Tag-Markierung ignorieren]** aus.

   ![Konfigurieren Sie den Workflow DAM-Update-Asset , um den Schritt &quot;Smart-Tag&quot;hinzuzufügen und das Flag &quot;Smart-Tag ignorieren&quot;auszuwählen.](assets/smart-tag-step-properties-workflow3.png)


   *Abbildung: Konfigurieren Sie den Workflow DAM-Update-Asset , um den Schritt &quot;Smart-Tag&quot;hinzuzufügen und das Flag &quot;Smart-Tag ignorieren&quot;auszuwählen.*

1. Klicken Sie auf **[!UICONTROL OK]**, um den Prozessschritt zu schließen, und speichern Sie dann den Workflow.

>[!MORELIKETHIS]
>
>* [Verwalten von Smart-Tags](managing-smart-tags.md)
>* [Überblick und Schulung von Smart-Tags](enhanced-smart-tags.md)
>* [Richtlinien und Regeln zum Trainieren des Smart Content Service](smart-tags-training-guidelines.md)

