---
title: Verwenden von Apache Tika zur Erkennung des MIME-Typs digitaler Assets
description: Aktivieren Sie Apache Tika, um zu helfen [!DNL Experience Manager] Assets erkennen den MIME-Typ von Assets aus dem Inhalts-Stream während des Upload-Vorgangs anstelle der Dateierweiterung.
contentOwner: AG
feature: Metadata,Developer Tools,Asset Management
role: Admin,Architect
exl-id: 6c9e53e9-5e54-4816-9431-41e796340d1e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 28%

---

# Verwenden von Apache Tika zur Erkennung des MIME-Typs digitaler Assets {#detecting-mime-type-of-assets-using-apache-tika}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

In der Regel erkennt Adobe Experience Manager Assets den MIME-Typ der Assets, die Sie von ihrer Dateierweiterung hochladen. Wenn Sie Assets mit Apache Tika hochladen, [!DNL Experience Manager] Assets erkennt ihren MIME-Typ während des Upload-Vorgangs aus dem Inhalts-Stream anstelle der Dateierweiterung.

Diese Funktion ist standardmäßig deaktiviert.  Um die Funktion zu aktivieren, konfigurieren Sie in Configuration Manager den Dienst **Day CQ DAM Mime Type**.

>[!NOTE]
>
>Die MIME-Typerkennung mit der Apache Tika-Bibliothek ist ein ressourcenintensiver Vorgang.

1. Navigieren Sie zu `https://[AEM_server]:[port]/system/console/configMgr` , um die Web-Konsole &quot;Configuration Manager&quot;zu öffnen.
1. Suchen Sie in der Liste der Dienste nach **[!UICONTROL Day CQ DAM Mime Type Service]** und tippen/klicken Sie auf **[!UICONTROL Bearbeiten]** daneben klicken, um sie im Bearbeitungsmodus zu öffnen.

1. Aktivieren Sie die Option **[!UICONTROL Detect MIME from content]**, um das Analysieren hochgeladener Assets zu aktivieren und so den zugehörigen MIME-Typ ohne Beachtung der Dateierweiterungen zu bestimmen. Standardmäßig ist diese Option deaktiviert. 

   ![chlimage_1-333](assets/chlimage_1-333.png)

1. Klicken oder tippen Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern.
