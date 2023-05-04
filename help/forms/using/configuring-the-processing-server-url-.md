---
title: Konfigurieren der AEM DS-Einstellungen
seo-title: Configuring AEM DS settings
description: Sie müssen die URL des Verarbeitungsservers angeben, bevor Sie ein Formular senden.
seo-description: You need to specify the processing server URL before you submit a form.
uuid: 2b415c99-275b-4b67-bb8e-35329514ecbb
contentOwner: amgoyal
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: fbb9044a-a737-45f6-8062-0ef5424a92f8
role: Admin
exl-id: f60beaae-4082-4165-8a37-9d9c94e360b2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 37%

---

# AEM DS-Einstellungen konfigurieren {#configuring-aem-ds-settings}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

In diesem Artikel wird beschrieben, wie Sie **AEM DS Settings Service**. Diese Einstellung kann in mehreren Szenarien verwendet werden, z. B.:

* In Correspondence Management

   * Konfigurieren des AEM Forms-Workflows
   * Beim Verwenden des Formularportals zum Remote-Speichern von Entwürfen/Übermittlungen

* In adaptiven Formularen für Fälle, in denen das adaptive Formular von der Veröffentlichungsinstanz gesendet wird

Im Folgenden werden die Schritte zum Konfigurieren der **[!UICONTROL AEM DS-Einstellungen]**:

1. Öffnen Sie den Konfigurations-Manager unter der Veröffentlichungsinstanz mit der URL:

   *http://localhost:port/system/console/configMgr*.

   ![aem_web_configuration_console](assets/aem_web_configuration_console.png)

1. Klicken Sie im Fenster **[!UICONTROL Adobe Experience Manager Web-Konsolenkonfiguration]** auf die Option **[!UICONTROL AEM DS-Einstellungen]**.

   ![ds_settings](assets/ds_settings.png)

1. Das Fenster **[!UICONTROL AEM DS-Einstellungendienst]** zeigt die allgemeinen Konfigurationseinstellungen für AEM DS-Komponenten.

   ![ds_settings_1](assets/ds_settings_1.png)

1. Fügen Sie die folgenden Informationen in die entsprechenden Felder ein:

   **[!UICONTROL Verarbeitungs-Server-URL]**: Der Verarbeitungs-Server ist der Server, auf dem der Forms- oder AEM-Workflow ausgelöst werden muss. Dies kann mit der URL der AEM Autoreninstanz oder der anderen Server-URL (d. h. http:// localhost:port/) übereinstimmen.

   **[!UICONTROL Verarbeitungs-Server-Benutzername]**: Benutzername des Workflow-Benutzers [basiert auf der verwendeten Server-URL]

   **[!UICONTROL Verarbeitungsserver-Kennwort]**: Kennwort des Workflow-Benutzers

   >[!NOTE]
   >
   >* Bei Verwendung von Forms- oder AEM-Workflows ist es vor der Übermittlung durch den Veröffentlichungsserver erforderlich, den DS-Einstellungsdienst zu konfigurieren. Andernfalls schlägt die Übermittlung des Formulars fehl.

