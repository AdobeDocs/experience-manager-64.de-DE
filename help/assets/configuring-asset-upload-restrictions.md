---
title: Konfigurieren von Einschränkungen beim Hochladen von Assets
description: Erfahren Sie, wie Sie Adobe Experience Manager Assets konfigurieren, um den Typ der Assets (Dateien) zu beschränken, die Benutzer hochladen können.
contentOwner: AG
feature: Upload,Asset Ingestion,Asset Management
role: Admin,Architect
exl-id: 0d817cfa-ae06-442a-ad89-5fe619bb2eff
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 61%

---

# Konfigurieren von Einschränkungen beim Hochladen von Assets {#configuring-asset-upload-restrictions}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Sie können Adobe Experience Manager Assets so konfigurieren, dass der Typ der Assets (Dateien), die Benutzer hochladen können, eingeschränkt wird. Mit dieser Funktion können Sie verhindern, dass Benutzer Assets in einem unerwünschten Format hochladen oder schädliche Dateien hochladen. Der Dienst `Day CQ DAM Asset Upload Restriction` ermöglicht es Ihnen, den Typ von Dateien, die Benutzer hochladen können, zu steuern. Standardmäßig [!DNL Experience Manager] Mit Assets können Benutzer Assets aller MIME-Typen hochladen. Sie können jedoch den Dienst so konfigurieren, dass Benutzer auf den Upload von Dateien bestimmter MIME-Typen beschränkt werden.

1. Um die Web-Konsole „Configuration Manager“ zu öffnen, verwenden Sie `https://[AEM_server]:[port]/system/console/configMgr`.
1. Öffnen Sie den Dienst **[!UICONTROL Day CQ DAM Asset Upload Restriction]** im Bearbeitungsmodus. Standardmäßig ist die Option **Alle MIME-Typen zulassen** aktiviert, sodass Benutzer Dateien aller MIME-Typen hochladen können.

   ![chlimage_1-378](assets/chlimage_1-378.png)

1. Um Benutzer auf den Upload von Dateien bestimmter MIME-Typen zu beschränken, deaktivieren Sie die Option **[!UICONTROL Alle MIME-Typen zulassen]** und legen Sie die zulässigen MIME-Typen mithilfe regulärer Ausdrücke im Feld **[!UICONTROL Zulässige Asset-MIME-Typen (regex)]** an.

   ![chlimage_1-379](assets/chlimage_1-379.png)

1. Klicken oder tippen Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern. Wenn Sie MIME-Zeichenfolgen für zulässige MIME-Typen angeben, schlägt der Upload-Vorgang für alle Assets fehl, deren MIME-Typ nicht den in diesen Feldern konfigurierten MIME-Zeichenfolgen entspricht.
