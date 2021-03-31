---
title: Einschränkungen beim Hochladen von Assets konfigurieren
description: Erfahren Sie mehr darüber, wie Sie Adobe Experience Manager (AEM) Assets so konfigurieren können, dass der von den Benutzern hochladbare Typ von Assets (Dateien) eingeschränkt ist.
contentOwner: AG
feature: Entwickler
role: Administrator, Architekt
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 91%

---


# Beschränkungen für das Hochladen von Assets konfigurieren {#configuring-asset-upload-restrictions}

Sie können Adobe Experience Manager (AEM) Assets so konfigurieren, dass der von den Benutzern hochladbare Typ von Assets (Dateien) eingeschränkt ist. Mit dieser Funktion können Sie verhindern, dass Benutzer Assets in einem unerwünschten Format oder schädliche Dateien hochladen. Der Dienst `Day CQ DAM Asset Upload Restriction` ermöglicht es Ihnen, den Typ von Dateien, die Benutzer hochladen können, zu steuern. Standardmäßig lässt es AEM Assets zu, dass Benutzer Assets aller MIME-Typen hochladen. Sie können jedoch den Dienst so konfigurieren, dass Benutzer auf den Upload von Dateien bestimmter MIME-Typen beschränkt werden.

1. Um die Configuration Manager-Webkonsole zu öffnen, rufen Sie `https://[AEM_server]:[port]/system/console/configMgr` auf.
1. Öffnen Sie den Dienst **[!UICONTROL Day CQ DAM Asset Upload Restriction]** im Bearbeitungsmodus. Standardmäßig ist die Option **Alle MIME-Typen zulassen** aktiviert, sodass Benutzer Dateien aller MIME-Typen hochladen können.

   ![chlimage_1-378](assets/chlimage_1-378.png)

1. Um Benutzer auf den Upload von Dateien bestimmter MIME-Typen zu beschränken, deaktivieren Sie die Option **[!UICONTROL Alle MIME-Typen zulassen]** und legen Sie die zulässigen MIME-Typen mithilfe regulärer Ausdrücke im Feld **[!UICONTROL Zulässige Asset-MIME-Typen (regex)]** an.

   ![chlimage_1-379](assets/chlimage_1-379.png)

1. Klicken oder tippen Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern. Wenn Sie MIME-Zeichenfolgen für zulässige MIME-Typen angeben, schlägt der Upload-Vorgang für alle Assets fehl, deren MIME-Typ nicht den in diesen Feldern konfigurierten MIME-Zeichenfolgen entspricht.
