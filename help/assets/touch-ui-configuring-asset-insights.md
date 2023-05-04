---
title: Konfigurieren von Asset Insights
description: Erfahren Sie, wie Sie Assets Insights konfigurieren in [!DNL Experience Manager] Assets.
contentOwner: AG
feature: Asset Insights,Asset Reports
role: User,Admin
exl-id: b0d62dd3-1868-4d73-95f7-3d6c3ff474d9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 39%

---

# Konfigurieren von Asset Insights {#configuring-asset-insights}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Adobe Experience Manager Assets ruft Nutzungsdaten ab [!DNL Experience Manager] Assets, die von Websites von Drittanbietern aus Adobe Analytics verwendet werden. Damit Assets Insights diese Daten abrufen und Einblicke generieren kann, konfigurieren Sie zunächst die Funktion zur Integration in Adobe Analytics.

>[!NOTE]
>
>Insights werden nur für Bilder unterstützt und bereitgestellt.

1. Klicken Sie in AEM auf **[!UICONTROL Tools > Assets]**.

   ![chlimage_1-210](assets/chlimage_1-210.png)

1. Klicken Sie auf die Karte **[!UICONTROL Insights-Konfiguration]**.
1. Wählen Sie im Assistenten ein Rechenzentrum aus und geben Sie Ihre Anmeldeinformationen ein, einschließlich des Namens Ihres Unternehmens, des Benutzernamens und des Kennworts.

   ![chlimage_1-211](assets/insights_config2.png)

1. Klicken/tippen Sie auf **[!UICONTROL Authentifizieren]**.
1. Nachdem [!DNL Experience Manager] Ihre Anmeldedaten authentifiziert hat, wählen Sie aus der Liste **[!UICONTROL Report Suite]** eine Adobe Analytics-Report Suite aus, aus der Asset Insights Daten abrufen soll. Klicken Sie auf **[!UICONTROL Hinzufügen]**.
1. Nachher [!DNL Experience Manager] Report Suite einrichten, klicken/tippen Sie auf **[!UICONTROL Fertig]**.

## Seitenverfolgung {#page-tracker}

Nachdem Sie Ihr Analytics-Konto konfiguriert haben, wird der Seitenverfolgungs-Code für Sie erzeugt. Um Asset Insights zur Verfolgung von [!DNL Experience Manager]-Assets in Websites von Drittanbietern zu aktivieren, schließen Sie den Seitenverfolgungs-Code in den Website-Code ein. Verwenden Sie das Seitenverfolgungs-Dienstprogramm in [!DNL Experience Manager] Assets zum Generieren des Seitenverfolgungs-Codes. Weitere Informationen dazu, wie Sie Ihren Seitenverfolgungs-Code in Webseiten von Drittanbietern einbeziehen, finden Sie unter [Verwenden von Seitenverfolgung und Einbettungscode in Webseiten](touch-ui-using-page-tracker.md).

1. Klicken Sie AEM auf die **[!UICONTROL Tools > Assets]**.

   ![chlimage_1-214](assets/chlimage_1-214.png)

1. Klicken Sie in der **[!UICONTROL Navigationsseite]** auf die Karte **[!UICONTROL Insights-Seitenverfolgung]**.
1. Klicken Sie auf **[!UICONTROL Download]** zum Herunterladen des Seitenverfolgungs-Codes.
