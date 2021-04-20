---
title: Verwenden Sie Apache Tika, um den MIME-Typ digitaler Assets zu erkennen
description: Aktivieren Sie Apache Tika, damit AEM Assets beim Upload-Vorgang den MIME-Typ von Assets aus dem Inhalts-Stream anstelle der Dateierweiterung erkennen kann.
contentOwner: AG
feature: Metadata,Developer Tools,Asset Management
role: Administrator,Architect
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 35%

---


# Verwenden Sie Apache Tika, um den MIME-Typ digitaler Elemente {#detecting-mime-type-of-assets-using-apache-tika} zu erkennen

Normalerweise erkennt Adobe Experience Manager (AEM) Assets den MIME-Typ von Assets, die Sie von ihrer Dateierweiterung hochladen. Wenn Sie Apache Tika verwenden, um Assets hochzuladen, erkennt AEM Assets deren MIME-Typ durch den Content Stream während des Uploadvorgangs statt durch die Dateierweiterung. 

Diese Funktion ist standardmäßig deaktiviert.  Um die Funktion zu aktivieren, konfigurieren Sie den Dienst **Day CQ DAM Mime Type** in Configuration Manager.

>[!NOTE]
>
>Die MIME-Typerkennung mit der Apache Tika-Bibliothek ist ein ressourcenintensiver Vorgang.

1. Wechseln Sie zu `https://[AEM_server]:[port]/system/console/configMgr`, um die Configuration Manager-Webkonsole zu öffnen.
1. Suchen Sie in der Liste der Dienste nach **[!UICONTROL Day CQ DAM Mime Type Service]** und tippen/klicken Sie auf das Symbol **[!UICONTROL Bearbeiten]**, um es im Bearbeitungsmodus zu öffnen.

1. Wählen Sie die Option **[!UICONTROL MIME aus Inhalt erkennen]**, um die Analyse hochgeladener Assets zu aktivieren, um deren MIME-Typ zu bestimmen, während Sie Dateierweiterungen ignorieren. Standardmäßig ist diese Option deaktiviert. 

   ![chlimage_1-333](assets/chlimage_1-333.png)

1. Klicken oder tippen Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern.
