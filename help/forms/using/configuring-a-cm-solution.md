---
title: Konfigurieren einer Correspondence Management-Lösung
seo-title: Configuring a Correspondence Management solution
description: Erfahren Sie, wie Sie eine URL der Autoreninstanz für die Wiederherstellung der Autoreninstanz-Version definieren und die URL der Veröffentlichungsinstanz für den Aktivierungsmanager der öffentlichen Instanz definieren.
seo-description: Learn how to define an author instance URL for the author instance version restore and define the Publish instance URL for public instance activation manager.
uuid: 76b25004-fe47-44d7-9bed-7c0fd963306b
topic-tags: correspondence-management
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
discoiquuid: 186ca75c-638b-4057-826e-cd5d56aa0397
feature: Correspondence Management
exl-id: a062957d-a526-4c4b-bbc5-0cda8ab007a3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 40%

---

# Konfigurieren einer Correspondence Management-Lösung {#configuring-a-correspondence-management-solution}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Definieren der URL der Autoreninstanz für VersionRestoreManagerImpl {#defining-author-instance-url-for-versionrestoremanagerimpl}

Führen Sie die folgenden Schritte aus, um eine URL der Autoreninstanz für die Wiederherstellung der Autoreninstanz zu definieren:

1. Navigieren Sie zu *https://:&lt;PublishHost>:&lt;PublishPort>/lc/system/console/configMgr*. Melden Sie sich mit den Anmeldedaten der OSGi Management Console an. Standardmäßig lauten die Anmeldedaten: admin/admin.
1. Klicken Sie auf **[!UICONTROL Bearbeiten]** neben der Einstellung **[!UICONTROL com.adobe.livecycle.content.activate.impl.VersionRestoreManagerImpl.name]**.
1. Geben Sie im Feld **[!UICONTROL VersionRestoreManager Author-URL]** die URL der Autoreninstanz von VersionRestoreManager an.

   **URL-Zeichenfolge**:

   `https://<hostname>:<port>:/libs/fd/fdm/content/crud/lc.content.remote.activate.VersionRestoreManager`

   >[!NOTE]
   >
   >Wenn mehrere Instanzen im Autorenmodus (in Cluster) mit einem vorgeschalteten Lastenausgleich vorhanden sind, geben Sie die URL für den Lastenausgleich im Feld **[!UICONTROL Autor-URL von VersionRestoreManager]** an.

1. Klicken Sie auf **[!UICONTROL Speichern]**.

## Definieren der URL der Instanz im Veröffentlichungsmodus für ActivationManagerImpl (Aktivierungsmanager der öffentlichen Instanz) {#defining-the-publish-instance-url-for-activationmanagerimpl-public-instance-activation-manager}

Führen Sie die folgenden Schritte aus, um die URL der Veröffentlichungsinstanz für den Aktivierungsmanager der öffentlichen Instanz zu definieren:

1. Navigieren Sie zu *https://:&lt;authorHost>:&lt;authorPort>/lc/system/console/configMgr*. Melden Sie sich mit den Anmeldedaten der OSGi Management Console an. Standardmäßig lauten die Anmeldedaten: admin/admin.
1. Suchen und klicken Sie auf **[!UICONTROL Bearbeiten]** Symbol neben **[!UICONTROL com.adobe.livecycle.content.activate.impl.ActivationManagerImpl.name]** -Einstellung.
1. Geben Sie im Feld für die **[!UICONTROL Veröffentlichungs-URL von ActivationManager]** die URL für den Zugriff auf die Instanz im Veröffentlichungsmodus in ActivationManager an. Sie können die folgenden URLs angeben.

   * **Lastenausgleichs-URL (empfohlen)**: Geben Sie die Lastenausgleichs-URL an, wenn Sie einen Webserver haben, der vor der Veröffentlichungsfarm (mehreren nicht geclusterten Veröffentlichungsinstanzen) als Lastenausgleich fungiert.
   * **URL der Veröffentlichungsinstanz**: Geben Sie eine Veröffentlichungsinstanz-URL an, wenn Sie über eine einzelne Veröffentlichungsinstanz verfügen oder der Webserver, der der Veröffentlichungsfarm vorgeschaltet ist, aufgrund von Einschränkungen nicht über die Autorenumgebung zugänglich ist. Wenn die angegebene Veröffentlichungsinstanz ausfällt, gibt es einen Ausweichmechanismus, der auf der Autorenseite verarbeitet werden kann.
   * **URL-Zeichenfolge**:

      `https://<hostname>:<port>:/libs/fd/fdm/content/crud/lc.content.remote.activate.activationManager`

1. Klicken Sie auf **[!UICONTROL Speichern]**.

Weitere Informationen zum Konfigurieren von Correspondence Management finden Sie unter [Konfigurationseigenschaften von Correspondence Management](https://helpx.adobe.com/de/aem-forms/6-2/aem-forms-architecture-deployment.html).
