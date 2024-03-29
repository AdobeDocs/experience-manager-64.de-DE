---
title: Microsoft Dynamics OData-Konfiguration
seo-title: Microsoft Dynamics ODtata configuration
description: Erfahren Sie, wie Sie mithilfe des Formulardatenmodells die Integration und die Arbeit mit Online- und lokalen Microsoft Dynamics-Services nutzen können.
seo-description: Learn how to leverage integrate and work with online and on-premises Microsoft Dynamics services through form data model.
uuid: c9b2764f-9127-4a99-a469-b6ebcdee8fdf
topic-tags: integration
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 62f9d1de-c397-46b5-964e-19777ddd130c
feature: Form Data Model
exl-id: 18df57b6-789a-4b61-9418-fa12294b226f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1253'
ht-degree: 60%

---

# Microsoft Dynamics OData-Konfiguration {#microsoft-dynamics-odata-configuration}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Erfahren Sie, wie Sie mithilfe des Formulardatenmodells die Integration und die Arbeit mit Online- und lokalen Microsoft Dynamics-Services nutzen können.

![data-integeration](assets/data-integeration.png)

Microsoft Dynamics ist eine Software für Customer Relationship Management (CRM) und Enterprise Resource Planning (ERP), die Unternehmenslösungen für die Erstellung und Verwaltung von Kundenkonten, Kontakten, Leads, Chancen und Fällen bietet. [AEM Forms-Datenintegration](/help/forms/using/data-integration.md) bietet eine OData-Cloud-Service-Konfiguration zur Integration von Forms in Online- und On-Premise-Microsoft Dynamics-Server. Damit können Sie ein Formulardatenmodell erstellen, das auf den im Microsoft Dynamics-Dienst definierten Entitäten, Attributen und Diensten basiert. Das Formulardatenmodell kann verwendet werden, um adaptive Formulare zu erstellen, die mit Microsoft Dynamics Server interagieren, um Geschäfts-Workflows zu ermöglichen. Beispiel:

* Abfragen des Microsoft Dynamics-Servers nach Daten und Vorausfüllen der adaptiven Formulare
* Schreiben von Daten in Microsoft Dynamics bei der Sendung von adaptiven Formularen
* Schreiben von Daten in Microsoft Dynamics durch benutzerdefinierte Entitäten, die im Formulardatenmodell definiert sind und umgekehrt

AEM Forms beinhaltet auch ein Add-on-Paket für die OData-Referenzkonfiguration, mit der Sie Microsoft Dynamics schnell in AEM Forms integrieren können.

Wenn das Paket installiert ist, sind die folgenden Entitäten und Dienste in Ihrer AEM Forms-Instanz verfügbar:

* MS Dynamics OData-Cloud Service (OData-Dienst)
* Formulardatenmodell mit vorkonfigurierten Microsoft Dynamics-Entitäten und -Services.

Der OData-Cloud Service und das Formulardatenmodell mit vorkonfigurierten Microsoft Dynamics-Entitäten und -Diensten sind nur dann in Ihrer AEM Forms-Instanz verfügbar, wenn der Ausführungsmodus für die AEM Instanz auf `samplecontent`(Standard). Weitere Informationen zum Konfigurieren von Ausführungsmodi für eine AEM-Instanz finden Sie unter [Ausführungsmodi](/help/sites-deploying/configure-runmodes.md).

## Voraussetzungen {#prerequisites}

Bevor Sie mit der Einrichtung und Konfiguration von Microsoft Dynamics beginnen, stellen Sie Folgendes sicher:

* Installiert die [AEM 6.4 Forms Add-On-Paket](https://helpx.adobe.com//experience-manager/6-4/forms/using/installing-configuring-aem-forms-osgi.html)
* Microsoft Dynamics 365 online konfiguriert oder eine Instanz einer der folgenden Microsoft Dynamics-Versionen installiert:

   * Microsoft Dynamics 365 vor Ort
   * Microsoft Dynamics 2016 vor Ort

* [Das Programm wurde für den Microsoft Dynamics-Online-Service bei Microsoft Azure Active Directory registriert](https://docs.microsoft.com/de-de/dynamics365/customer-engagement/developer/walkthrough-register-dynamics-365-app-azure-active-directory). Notieren Sie sich die Werte für die Client-ID (die auch als Anwendungs-ID bezeichnet wird) und den geheimen Clientschlüssel für den registrierten Service. Diese Werte werden verwendet, während [Konfigurieren des Cloud-Dienstes für Ihren Microsoft Dynamics-Dienst](/help/forms/using/ms-dynamics-odata-configuration.md#configure-cloud-service-for-your-microsoft-dynamics-service).

## Festlegen der Antwort-URL für registrierte Microsoft Dynamics-Anwendung {#set-reply-url-for-registered-microsoft-dynamics-application}

Führen Sie die folgenden Schritte aus, um die Antwort-URL für die registrierte Microsoft Dynamics-Anwendung festzulegen:

>[!NOTE]
>
>Verwenden Sie dieses Verfahren nur bei der Integration von AEM Forms mit dem Online-Microsoft Dynamics-Server.

1. Wechseln Sie zu einem Microsoft Azure Active Directory-Konto und fügen Sie in den Einstellungen für **[!UICONTROL Antwort-URLs]** für Ihre registrierte Anwendung die folgende Cloud-Service-Konfigurations-URL hinzu:

   `https://[server]:[port]/libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices.html`

   ![azure_directory](assets/azure_directory.png)

1. Speichern Sie die Konfiguration.

## Microsoft Dynamics für IFD konfigurieren {#configure-microsoft-dynamics-for-ifd}

Microsoft Dynamics verwendet eine auf Ansprüchen basierende Authentifizierung, um externen Benutzern Zugriff auf Daten auf dem Microsoft Dynamics CRM-Server zu gewähren. Um dies zu aktivieren, führen Sie die folgenden Schritte aus, um Microsoft Dynamics für eine Internet-orientierte Bereitstellung (IFD) zu konfigurieren und Schadenseinstellungen zu konfigurieren.

>[!NOTE]
>
>Verwenden Sie dieses Verfahren nur bei der Integration von AEM Forms mit dem lokalen Microsoft Dynamics-Server.

1. Konfigurieren Sie die lokale Microsoft Dynamics-Instanz für IFD, wie in [Konfigurieren von IFD für Microsoft Dynamics](https://technet.microsoft.com/de-de/library/dn609803.aspx) beschrieben.
1. Führen Sie die folgenden Befehle mit Windows PowerShell aus, um die Anspruchseinstellungen für IFD-aktiviertes Microsoft Dynamics zu konfigurieren:

   ```
   Add-PSSnapin Microsoft.Crm.PowerShell 
    $ClaimsSettings = Get-CrmSetting -SettingType OAuthClaimsSettings 
    $ClaimsSettings.Enabled = $true 
    Set-CrmSetting -Setting $ClaimsSettings
   ```

   Weitere Informationen finden Sie unter [App-Registrierung für CRM lokal (IFD)](https://msdn.microsoft.com/de-de/library/dn531010(v=crm.7).aspx#bkmk_ifd).

## Konfigurieren des OAuth-Clients auf einem AD FS-Computer {#configure-oauth-client-on-ad-fs-machine}

Führen Sie die folgenden Schritte aus, um einen OAuth-Client auf einem AD FS (Active Directory Federation Services)-Computer zu registrieren und Zugriff auf den AD FS-Computer zu erteilen:

>[!NOTE]
>
>Verwenden Sie dieses Verfahren nur bei der Integration von AEM Forms mit dem lokalen Microsoft Dynamics-Server.

1. Führen Sie den folgenden Befehl aus:

   `Add-AdfsClient -ClientId “<Client-ID>” -Name "<name>" -RedirectUri "<redirect-uri>" -GenerateClientSecret`

   Dabei ist:

   * `Client-ID` eine Client-ID, die Sie mit einem beliebigen GUID-Generator generieren können.
   * `redirect-uri` ist die URL zum Microsoft Dynamics OData Cloud-Dienst auf AEM Forms. Der mit dem AEM Forms-Paket installierte standardmäßige Cloud-Service wird unter der folgenden URL bereitgestellt:

      ```
      http://[server]:[port]/libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices.html
      ```

1. Führen Sie den folgenden Befehl aus, um Zugriff auf den AD FS-Computer zu gewähren:

   `Grant-AdfsApplicationPermission -ClientRoleIdentifier “<Client-ID>” -ServerRoleIdentifier <resource> -ScopeNames openid`

   Dabei ist:

   * `resource` ist die Microsoft Dynamics-Organisations-URL.

1. Microsoft Dynamics verwendet das HTTPS-Protokoll. Um AD FS-Endpunkte über den Forms-Server aufzurufen, installieren Sie das Microsoft Dynamics-Websitezertifikat mithilfe des Befehls `keytool` auf dem Computer, auf dem AEM Forms ausgeführt wird, im Java-Zertifikatspeicher.

## Konfigurieren Sie den Cloud-Dienst für Ihren Microsoft Dynamics-Dienst {#configure-cloud-service-for-your-microsoft-dynamics-service}

Die Konfiguration **MS Dynamics OData Cloud Service (OData Service)** wird mit der Standard-OData-Konfiguration geliefert. Gehen Sie wie folgt vor, um ihn für die Verbindung mit Ihrem Microsoft Dynamics -Dienst zu konfigurieren.

1. Navigieren Sie zu **[!UICONTROL Tools > Cloud-Services > Datenquellen]** und tippen Sie auf den Konfigurationsordner `global`.
1. Auswählen **[!UICONTROL MS Dynamics OData-Cloud Service (OData-Dienst)]** Konfiguration und tippen Sie auf **[!UICONTROL Eigenschaften]**. Das Dialogfeld &quot;Cloud Service-Konfigurationseigenschaft&quot;wird geöffnet.

   Auf der Registerkarte **[!UICONTROL Authentifizierungseinstellungen]**:

   1. Geben Sie den Wert für das Feld **[!UICONTROL Service-Stamm]** ein. Wechseln Sie zur Dynamics-Instanz und navigieren Sie zu **[!UICONTROL Entwickler-Ressourcen]**, um den Wert für das Feld „Service-Stamm“ anzuzeigen. Beispiel: https://&lt;tenant-name>/api/data/v9.1/
   1. Ersetzen Sie die Standardwerte in der **[!UICONTROL Client ID]** (auch als **[!UICONTROL Application ID]** bezeichnet), die Felder **[!UICONTROL Client Secret]**, **[!UICONTROL OAuth URL]**, **[!UICONTROL Refresh Token URL]**, **[!UICONTROL Access Token URL]** und **[!UICONTROL Resource]** mit Werten aus Ihrer Microsoft Dynamics-Dienstkonfiguration. Sie müssen die Dynamics-Instanz-URL im Feld **[!UICONTROL Ressource]** angeben, um Microsoft Dynamics mit einem Formulardatenmodell zu konfigurieren. Verwenden Sie die Service-Stamm-URL, um die URL der Dynamics-Instanz abzuleiten. Beispiel: [https://org.crm.dynamics.com](https://org.crm.dynamics.com/).
   1. Geben Sie die **[!UICONTROL openid]** im Feld **[!UICONTROL Autorisierungsumfang]** für den Autorisierungsprozess auf Microsoft Dynamics an.

   ![dynamics_authentication_settings](assets/dynamics_authentication_settings.png)

1. Klicken Sie auf **[!UICONTROL Verbindung zu OAuth herstellen]**. Sie werden zur Anmeldungsseite von Microsoft Dynamics umgeleitet.
1. Melden Sie sich mit Ihren Microsoft Dynamics-Anmeldeinformationen an und lassen Sie zu, dass die Cloud-Service-Konfiguration eine Verbindung zum Microsoft Dynamics-Service herstellen kann. Es ist eine einmalige Aufgabe, eine Verbindung zwischen dem Cloud-Service und dem Dienst herzustellen.

   Anschließend werden Sie zur Cloud-Service-Konfigurationsseite weitergeleitet, auf der eine Meldung angezeigt wird, dass die OData-Konfiguration erfolgreich gespeichert wurde.

Der MS Dynamics OData-Cloud Service (OData Service) ist konfiguriert und mit Ihrem Dynamics-Service verbunden.

## Erstellen des Formulardatenmodells {#create-form-data-model}

Wenn Sie das AEM Forms-Paket installieren, wird ein Formulardatenmodell, **Microsoft Dynamics FDM**, in Ihrer AEM-Instanz bereitgestellt. Standardmäßig verwendet das Formulardatenmodell den Microsoft Dynamics-Service, der im MS Dynamics ODaten-Cloud-Service (ODaten-Service) konfiguriert ist, als Datenquelle.

Beim erstmaligen Öffnen des Formulardatenmodells stellt es eine Verbindung zum konfigurierten Microsoft Dynamics-Dienst her und ruft Entitäten von Ihrer Microsoft Dynamics-Instanz ab. Die Entitäten &quot;contact&quot;und &quot;lead&quot;aus Microsoft Dynamics wurden bereits im Formulardatenmodell hinzugefügt.

Um das Formulardatenmodell zu überprüfen, navigieren Sie zu **[!UICONTROL Formulare > Datenintegrationen]**. Auswählen **[!UICONTROL Microsoft Dynamics FDM]** und klicken Sie auf **[!UICONTROL Bearbeiten]** , um das Formulardatenmodell im Bearbeitungsmodus zu öffnen. Alternativ können Sie das Formulardatenmodell direkt über die folgende URL öffnen:

`https://[*server*]:[*port*]/aem/fdm/editor.html/content/dam/formsanddocuments-fdm/ms-dynamics-fdm`

![default-fdm-1](assets/default-fdm-1.png)

Anschließend können Sie ein adaptives Formular auf der Grundlage des Formulardatenmodells erstellen und es in verschiedenen Anwendungsfällen für adaptive Formulare verwenden, wie z. B.:

* Adaptives Formulars durch Abfrage von Informationen aus Microsoft Dynamics-Entitäten und Dienste befüllen
* Aufrufen von Microsoft Dynamics-Server-Prozessen, die in einem Formulardatenmodell definiert sind, unter Verwendung adaptiver Formularregeln
* Gesendete Formulardaten in Microsoft Dynamics-Entitäten schreiben

Es wird empfohlen, eine Kopie des mit dem AEM Forms-Package bereitgestellten Formulardatenmodells zu erstellen und Datenmodelle und -dienste entsprechend Ihren Anforderungen zu konfigurieren. Dadurch wird sichergestellt, dass zukünftige Aktualisierungen des Pakets Ihr Formulardatenmodell nicht überschreiben.

Weitere Informationen zur Erstellung und Verwendung des Formulardatenmodells in Business Workflows finden Sie unter [Datenintegration](/help/forms/using/data-integration.md).
