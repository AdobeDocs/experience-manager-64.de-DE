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
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 71%

---

# Konfigurieren einer Correspondence Management-Lösung {#configuring-a-correspondence-management-solution}

## Definieren einer URL der Autorinstanz für VersionRestoreManagerImpl {#defining-author-instance-url-for-versionrestoremanagerimpl}

Führen Sie die folgenden Schritte aus, um eine URL der Autorinstanz zur Wiederherstellung der Autorinstanzversion:

1. Navigieren Sie zu *https://:&lt;publishhost>:&lt;publishport>/lc/system/console/configMgr*. Melden Sie sich mit den Anmeldedaten der OSGi Management Console an. Standardmäßig lauten die Anmeldedaten: admin/admin.
1. Klicken Sie auf **[!UICONTROL Bearbeiten]** neben der Einstellung **[!UICONTROL com.adobe.livecycle.content.activate.impl.VersionRestoreManagerImpl.name]**.
1. Im **[!UICONTROL Autoren-URL für VersionRestoreManager]** Geben Sie die URL der Autoreninstanz von VersionRestoreManager an.

   **URL-Zeichenfolge**:

   `https://<hostname>:<port>:/libs/fd/fdm/content/crud/lc.content.remote.activate.VersionRestoreManager`

   >[!NOTE]
   >
   >Wenn mehrere Autoreninstanzen (geclustert) mit einem Frontend für einen Lastenausgleich vorhanden sind, geben Sie die URL für den Lastenausgleich im **[!UICONTROL Autoren-URL für VersionRestoreManager]** -Feld.

1. Klicken Sie auf **[!UICONTROL Speichern]**.

## URL der Instanz im Veröffentlichungsmodus für ActivationManagerImpl festlegen (Aktivierungsmanager der öffentlichen Instanz) {#defining-the-publish-instance-url-for-activationmanagerimpl-public-instance-activation-manager}

Folgen Sie diesen Schritten, um die „URL-Instanz veröffentlichen“ für den Aktivierungsmanager der Veröffentlichungsinstanz zu definieren:

1. Navigieren Sie zu *https://:&lt;authorhost>:&lt;authorport>/lc/system/console/configMgr*. Melden Sie sich mit den Anmeldedaten der OSGi Management Console an. Standardmäßig lauten die Anmeldedaten: admin/admin.
1. Klicken Sie auf das **[!UICONTROL Bearbeitungs]** symbol neben der Einstellung **[!UICONTROL com.adobe.livecycle.content.activate.impl.ActivationManagerImpl.name]**.
1. Geben Sie im Feld für die **[!UICONTROL Veröffentlichungs-URL von ActivationManage]** r die URL für den Zugriff auf die Instanz im Veröffentlichungsmodus in ActivationManager an. Sie können die folgenden URLs angeben.

   * **Lastenausgleichs-URL (empfohlen)**: Geben Sie die Lastenausgleichs-URL an, wenn Sie einen Webserver haben, der gegenüber der Veröffentlichungsfarm (mehrere nicht geclusterte Instanzen im Veröffentlichungsmodus) als Lastenausgleich fungiert.
   * **URL der Instanz im Veröffentlichungsmodus**: Geben Sie die URL einer beliebigen Instanz im Veröffentlichungsmodus an, wenn Sie nur eine Instanz im Veröffentlichungsmodus haben oder ein Zugriff auf den der Veröffentlichungsfarm vorgeschalteten Webserver von der Autorumgebung aus aufgrund von gegebenen falls vorhandenen Beschränkungen nicht möglich ist. Wenn die angegebene Instanz im Veröffentlichungsmodus nicht bereit ist, gibt es einen Fallback-Mechanismus, damit autorseitig etwas zur Behebung unternommen werden kann.
   * **URL-Zeichenfolge**:

      `https://<hostname>:<port>:/libs/fd/fdm/content/crud/lc.content.remote.activate.activationManager`

1. Klicken Sie auf **[!UICONTROL Speichern]**.

Weitere Informationen zum Konfigurieren von Correspondence Management finden Sie unter [Correspondence Management Configuration-Eigenschaften](https://helpx.adobe.com/aem-forms/6-2/cm-configuration-properties.html).
