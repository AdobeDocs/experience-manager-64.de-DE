---
title: Verwenden Sie Apache Tika, um den MIME-Typ digitaler Assets zu erkennen
description: Aktivieren Sie Apache Tika, damit AEM Assets beim Upload-Vorgang den MIME-Typ von Assets aus dem Inhalts-Stream anstelle der Dateierweiterung erkennen kann.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 37%

---


# Verwenden Sie Apache Tika, um den MIME-Typ digitaler Assets zu erkennen {#detecting-mime-type-of-assets-using-apache-tika}

Normalerweise erkennt Adobe Experience Manager (AEM) Assets den MIME-Typ von Assets, die Sie von ihrer Dateierweiterung hochladen. Wenn Sie Apache Tika verwenden, um Assets hochzuladen, erkennt AEM Assets deren MIME-Typ durch den Content Stream während des Uploadvorgangs statt durch die Dateierweiterung. 

Diese Funktion ist standardmäßig deaktiviert.  To enable the feature, configure the **Day CQ DAM Mime Type** service from Configuration Manager.

>[!NOTE]
>
>Die MIME-Typerkennung mit der Apache Tika-Bibliothek ist ein ressourcenintensiver Vorgang.

1. Go to `https://[AEM_server]:[port]/system/console/configMgr` to open the Configuration Manager web console.
1. From the list of services, locate **[!UICONTROL Day CQ DAM Mime Type Service]** and tap/click the **[!UICONTROL Edit]** icon beside it to open it in Edit mode.

1. Select the **[!UICONTROL Detect MIME from content]** option to enable the parsing of uploaded assets to determine their MIME type while ignoring file extensions. Standardmäßig ist diese Option deaktiviert. 

   ![chlimage_1-333](assets/chlimage_1-333.png)

1. Klicken oder tippen Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern.
