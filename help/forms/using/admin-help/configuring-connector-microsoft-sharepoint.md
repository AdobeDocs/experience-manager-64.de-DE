---
title: Konfigurieren des Connectors für Microsoft SharePoint
seo-title: Configuring Connector for Microsoft SharePoint
description: Konfigurieren Sie Connector für Microsoft SharePoint, um die Kommunikation zwischen AEM Formularen und Microsoft SharePoint zu aktivieren.
seo-description: Configure Connector for Microsoft SharePoint to enable communication between AEM forms and Microsoft SharePoint.
uuid: f1561b41-da20-4220-b13a-e78472a9449f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/connecting_to_a_content_management_system
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 0ec881c9-8dcc-4847-9edf-24d9e6c4a7ea
exl-id: 9bd396a3-5da9-4355-ad76-e7132ac8aed8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 57%

---

# Connector für Microsoft SharePoint konfigurieren {#configuring-connector-for-microsoft-sharepoint}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Connector für Microsoft SharePoint ermöglicht die Kommunikation zwischen AEM Formularen und Microsoft SharePoint. Weitere Hintergrundinformationen finden Sie unter &quot;Connectors for ECM&quot;in [Dienstreferenz](https://www.adobe.com/go/learn_aemforms_services_63).

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Connector für Microsoft SharePoint&quot;.
1. Geben Sie die folgenden Einstellungen für Ihren SharePoint-Server an:

   **Hostname des SharePoint-Servers:** Die Hostnamen-Anschlussnummer der Webanwendung auf dem SharePoint-Server im Format `[hostname]:[port]`.

   **Benutzername:** Das Benutzerkonto, das zum Herstellen einer Verbindung mit dem SharePoint-Server verwendet wird.

   **Kennwort:** Das Kennwort für das Benutzerkonto, das zum Herstellen einer Verbindung mit dem SharePoint-Server verwendet wird.

   **Domain-Name:** Die Domain, in der sich der SharePoint-Server befindet.

1. Klicken Sie auf Speichern.

## Microsoft SharePoint-Konfigurationsdienst {#microsoft-sharepoint-configuration-service}

Mit dem Microsoft SharePoint-Konfigurations-Service (`(MSSharePointConfigService)`) können Sie Anmeldedaten für den AEM Forms-Benutzer angeben, der über die Berechtigung zum Identitätswechsel verfügt. Weitere Informationen zu Berechtigungen zum Identitätswechsel finden Sie unter [Connector für Microsoft SharePoint konfigurieren](https://help.adobe.com/de_DE/AEMForms/6.1/SharePointConfig/index.html). Führen Sie folgende Schritte aus, um die Einstellungen für `MSSharePointConfigService` anzugeben:

1. Klicken Sie in Administration Console auf „Dienste“ > „Anwendungen und Dienste“ > „Dienstverwaltung“.
1. Durchlaufen Sie die Liste der Dienste und klicken Sie auf `MSSharePointConfigService`.
1. Geben Sie auf der Seite &quot;Konfiguration&quot;die folgenden Einstellungen an:

   * Benutzername für einen Benutzer mit Berechtigungen zum Identitätswechsel
   * Kennwort für den obigen Benutzer

1. Klicken Sie auf Speichern.
