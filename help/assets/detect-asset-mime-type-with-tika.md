---
title: Verwenden von Apache Tika zur Erkennung des MIME-Typs digitaler Assets
description: Aktivieren Sie Apache Tika, damit AEM Assets beim Upload-Vorgang den MIME-Typ von Assets aus dem Inhalts-Stream anstelle der Dateierweiterung erkennen kann.
contentOwner: AG
feature: Metadaten,Entwicklertools,Asset-Management
role: Administrator,Architect
exl-id: 6c9e53e9-5e54-4816-9431-41e796340d1e
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 36%

---

# Verwenden Sie Apache Tika, um den MIME-Typ digitaler Assets zu erkennen {#detecting-mime-type-of-assets-using-apache-tika}

Normalerweise erkennt Adobe Experience Manager (AEM) Assets den MIME-Typ der Assets, die Sie von ihrer Dateierweiterung hochladen. Wenn Sie Apache Tika verwenden, um Assets hochzuladen, erkennt AEM Assets deren MIME-Typ durch den Content Stream während des Uploadvorgangs statt durch die Dateierweiterung. 

Diese Funktion ist standardmäßig deaktiviert.  Um die Funktion zu aktivieren, konfigurieren Sie den Dienst **Day CQ DAM Mime Type** aus Configuration Manager.

>[!NOTE]
>
>Die MIME-Typerkennung mit der Apache Tika-Bibliothek ist ein ressourcenintensiver Vorgang.

1. Navigieren Sie zu `https://[AEM_server]:[port]/system/console/configMgr` , um die Web-Konsole &quot;Configuration Manager&quot;zu öffnen.
1. Suchen Sie in der Liste der Dienste **[!UICONTROL Day CQ DAM Mime Type Service]** und tippen/klicken Sie auf das Symbol **[!UICONTROL Bearbeiten]** daneben, um ihn im Bearbeitungsmodus zu öffnen.

1. Wählen Sie die Option **[!UICONTROL MIME aus Inhalt erkennen]** aus, um das Parsen hochgeladener Assets zu aktivieren, um ihren MIME-Typ zu bestimmen, während Dateierweiterungen ignoriert werden. Standardmäßig ist diese Option deaktiviert. 

   ![chlimage_1-333](assets/chlimage_1-333.png)

1. Klicken oder tippen Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern.
