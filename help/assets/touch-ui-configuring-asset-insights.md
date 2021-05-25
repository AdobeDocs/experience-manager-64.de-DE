---
title: Konfigurieren von Asset Insights
description: Erfahren Sie, wie Sie Assets Insights in AEM Assets konfigurieren.
contentOwner: AG
feature: Asset Insights,Asset-Berichte
role: Business Practitioner,Administrator
exl-id: b0d62dd3-1868-4d73-95f7-3d6c3ff474d9
source-git-commit: edba9586711ee5c0e5549dbe374226e878803178
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 70%

---

# Konfigurieren von Assets Insights {#configuring-asset-insights}

Adobe Experience Manager (AEM) Assets ruft Nutzungsdaten rund um AEM-Assets von Websites von Drittanbietern aus Adobe Analytics ab. Damit Assets Insights diese Daten abrufen und Einblicke generieren kann, konfigurieren Sie zunächst die Funktion zur Integration in Adobe Analytics.

>[!NOTE]
>
>Insights werden nur für Bilder unterstützt und bereitgestellt.

1. Klicken Sie in AEM auf **[!UICONTROL Tools > Assets]**.

   ![chlimage_1-210](assets/chlimage_1-210.png)

1. Klicken Sie auf die Karte **[!UICONTROL Insights-Konfiguration]**.
1. Wählen Sie im Assistenten ein Datencenter aus und geben Sie Ihre Anmeldeinformationen an, z. B. den Namen Ihres Unternehmens, Benutzernamen und Kennwort.

   ![chlimage_1-211](assets/insights_config2.png)

1. Klicken/tippen Sie auf **[!UICONTROL Authentifizieren]**.
1. Nachdem AEM Ihre Anmeldedaten authentifiziert hat, wählen Sie in der Liste **[!UICONTROL Report Suite]** eine Adobe Analytics Report Suite aus, aus der Assets Insights Daten abrufen soll. Klicken Sie auf **[!UICONTROL Hinzufügen]**.
1. Nach der Report Suite-Einrichtung durch AEM klicken/tippen Sie auf **[!UICONTROL Fertig]**.

## Seitenverfolgung {#page-tracker}

Nachdem Sie Ihr Analytics-Konto konfiguriert haben, wird der Seitenverfolgungs-Code für Sie erzeugt. Um Asset Insights zur Verfolgung von AEM-Assets in Websites von Drittanbietern zu aktivieren, beziehen Sie den Seitenverfolgungscode in den Website-Code ein. Verwenden Sie das Seitenverfolgungs-Dienstprogramm in AEM Assets, um den Seitenverfolgungscode zu erzeugen. Weitere Informationen dazu, wie Sie Ihren Seitenverfolgungscode in Webseiten von Drittanbietern einbeziehen, finden Sie unter [Verwenden von Seitenverfolgung und Einbettungscode in Webseiten](touch-ui-using-page-tracker.md).

1. Klicken Sie in AEM auf **[!UICONTROL Tools > Assets]**.

   ![chlimage_1-214](assets/chlimage_1-214.png)

1. Klicken Sie in der **[!UICONTROL Navigationsseite]** auf die Karte **[!UICONTROL Insights-Seitenverfolgung]**.
1. Klicken Sie auf das Symbol **[!UICONTROL Herunterladen]**, um den Seitenverfolgungscode herunterzuladen.
