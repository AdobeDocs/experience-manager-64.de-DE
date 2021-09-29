---
title: Konfigurieren von Asset-Upload-Beschränkungen
description: Erfahren Sie, wie Sie Adobe Experience Manager Assets konfigurieren, um den Typ der Assets (Dateien) zu beschränken, die Benutzer hochladen können.
contentOwner: AG
feature: Upload,Asset Ingestion,Asset Management
role: Admin,Architect
exl-id: 0d817cfa-ae06-442a-ad89-5fe619bb2eff
source-git-commit: 8948bca63f1f5ec9d94ede2fb845ed01b4e23333
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 69%

---

# Konfigurieren von Asset-Upload-Beschränkungen {#configuring-asset-upload-restrictions}

Sie können Adobe Experience Manager Assets so konfigurieren, dass der Typ der Assets (Dateien), die Benutzer hochladen können, eingeschränkt wird. Mit dieser Funktion können Sie verhindern, dass Benutzer Assets in einem unerwünschten Format oder schädliche Dateien hochladen. Der Dienst `Day CQ DAM Asset Upload Restriction` ermöglicht es Ihnen, den Typ von Dateien, die Benutzer hochladen können, zu steuern. Standardmäßig ermöglicht [!DNL Experience Manager] Assets Benutzern das Hochladen von Assets aller MIME-Typen. Sie können jedoch den Dienst so konfigurieren, dass Benutzer auf den Upload von Dateien bestimmter MIME-Typen beschränkt werden.

1. Um die Web-Konsole &quot;Configuration Manager&quot;zu öffnen, greifen Sie auf `https://[AEM_server]:[port]/system/console/configMgr` zu.
1. Öffnen Sie den Dienst **[!UICONTROL Day CQ DAM Asset Upload Restriction]** im Bearbeitungsmodus. Standardmäßig ist die Option **Alle MIME-Typen zulassen** aktiviert, sodass Benutzer Dateien aller MIME-Typen hochladen können.

   ![chlimage_1-378](assets/chlimage_1-378.png)

1. Um Benutzer auf den Upload von Dateien bestimmter MIME-Typen zu beschränken, deaktivieren Sie die Option **[!UICONTROL Alle MIME-Typen zulassen]** und legen Sie die zulässigen MIME-Typen mithilfe regulärer Ausdrücke im Feld **[!UICONTROL Zulässige Asset-MIME-Typen (regex)]** an.

   ![chlimage_1-379](assets/chlimage_1-379.png)

1. Klicken oder tippen Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern. Wenn Sie MIME-Zeichenfolgen für zulässige MIME-Typen angeben, schlägt der Upload-Vorgang für alle Assets fehl, deren MIME-Typ nicht den in diesen Feldern konfigurierten MIME-Zeichenfolgen entspricht.
