---
title: AEM DS-Einstellungen konfigurieren
seo-title: AEM DS-Einstellungen konfigurieren
description: Sie müssen die Verarbeitungsserver-URL angeben, bevor Sie ein Formular senden.
seo-description: Sie müssen die Verarbeitungsserver-URL angeben, bevor Sie ein Formular senden.
uuid: 2b415c99-275b-4b67-bb8e-35329514ecbb
contentOwner: amgoyal
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: fbb9044a-a737-45f6-8062-0ef5424a92f8
role: Admin
exl-id: f60beaae-4082-4165-8a37-9d9c94e360b2
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 70%

---

# AEM DS-Einstellungen konfigurieren {#configuring-aem-ds-settings}

Dieser Artikel beschreibt, wie Sie den **AEM DS-Einstellungen-Dienst** konfigurieren. Diese Einstellung kann in mehreren Szenarien verwendet werden, zum Beispiel:

* In Correspondence Management

   * Für die Konfiguration des AEM Forms-Workflow
   * Achten Sie bei der Verwendung von Formularportals für Remote-Verwendung, darauf, dass Sie Entwurf/der Übermittlung speichern

* In den adaptiven Formularen für Fälle, bei denen ein adaptives Formular von der Veröffentlichungsinstanz gesendet wird

Führen Sie die folgenden Schritte aus, um die **[!UICONTROL AEM DS-Einstellungen]** zu konfigurieren:

1. Öffnen Sie Configuration Manager mithilfe der URL auf der Veröffentlichungsinstanz:

   *http://localhost:port/system/console/configMgr*.

   ![aem_web_configuration_console](assets/aem_web_configuration_console.png)

1. Suchen Sie im Fenster **[!UICONTROL Adobe Experience Manager Web Console Configuration]** die Option **[!UICONTROL AEM DS Settings]** und klicken Sie darauf.

   ![ds_settings](assets/ds_settings.png)

1. Das Fenster **[!UICONTROL AEM DS-Einstellungendienst]** zeigt die allgemeinen Konfigurationseinstellungen für AEM DS-Komponenten.

   ![ds_settings_1](assets/ds_settings_1.png)

1. Fügen Sie die folgenden Informationen in die entsprechenden Felder ein:

   **[!UICONTROL Verarbeitungsserver-URL]**: Der Verarbeitungsserver ist der Server, auf dem der Forms- oder AEM-Workflow ausgelöst werden muss. Dies kann mit der URL der AEM-Autoreninstanz oder der anderen Server-URL übereinstimmen (d. h. http://localhost:port/).

   **[!UICONTROL Verarbeitungsserver-Benutzername]**: Benutzername des Workflow-Benutzers  [basierend auf der verwendeten Server-URL]

   **[!UICONTROL Verarbeitungs-Serverkennwort]**: Das Kennwort des Workflow-Benutzers

   >[!NOTE]
   >
   >* Bei der Verwendung von Formularen oder AEM-Workflows ist es notwendig, den DS-Einstellungendienst zu konfigurieren, bevor Sie eine Übertragung vom Veröffentlichungsserver vornehmen. Andernfalls schlägt die Übermittlung eines Formulars fehlgeschlagen.

