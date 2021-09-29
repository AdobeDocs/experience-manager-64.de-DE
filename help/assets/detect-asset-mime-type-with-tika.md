---
title: Verwenden von Apache Tika zur Erkennung des MIME-Typs digitaler Assets
description: Aktivieren Sie Apache Tika, um [!DNL Experience Manager] Assets beim Hochladen zu helfen, den MIME-Typ von Assets aus dem Inhalts-Stream anstelle der Dateierweiterung zu erkennen.
contentOwner: AG
feature: Metadata,Developer Tools,Asset Management
role: Admin,Architect
exl-id: 6c9e53e9-5e54-4816-9431-41e796340d1e
source-git-commit: 8948bca63f1f5ec9d94ede2fb845ed01b4e23333
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 10%

---

# Verwenden von Apache Tika zur Erkennung des MIME-Typs digitaler Assets {#detecting-mime-type-of-assets-using-apache-tika}

In der Regel erkennt Adobe Experience Manager Assets den MIME-Typ der Assets, die Sie von ihrer Dateierweiterung hochladen. Wenn Sie Assets mit Apache Tika hochladen, erkennt [!DNL Experience Manager] Assets während des Upload-Vorgangs den MIME-Typ vom Inhalts-Stream anstelle der Dateierweiterung.

Diese Funktion ist standardmäßig deaktiviert.  Um die Funktion zu aktivieren, konfigurieren Sie den Dienst **Day CQ DAM Mime Type** aus Configuration Manager.

>[!NOTE]
>
>Die MIME-Typerkennung mit der Apache Tika-Bibliothek ist ein ressourcenintensiver Vorgang.

1. Navigieren Sie zu `https://[AEM_server]:[port]/system/console/configMgr` , um die Web-Konsole &quot;Configuration Manager&quot;zu öffnen.
1. Suchen Sie in der Liste der Dienste **[!UICONTROL Day CQ DAM Mime Type Service]** und tippen/klicken Sie auf das Symbol **[!UICONTROL Bearbeiten]** daneben, um ihn im Bearbeitungsmodus zu öffnen.

1. Wählen Sie die Option **[!UICONTROL MIME aus Inhalt erkennen]** aus, um das Parsen hochgeladener Assets zu aktivieren, um ihren MIME-Typ zu bestimmen, während Dateierweiterungen ignoriert werden. Standardmäßig ist diese Option deaktiviert. 

   ![chlimage_1-333](assets/chlimage_1-333.png)

1. Klicken oder tippen Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern.
