---
title: Verwenden der Funktion "Assets Insights", um die Nutzung Ihrer Bilder zu verfolgen
description: Mit der Funktion "Asset Insights"können Sie Benutzerbewertungen und Nutzungsstatistiken von Bildern verfolgen, die auf Drittanbieter-Websites, in Marketingkampagnen und den Kreativlösungen der Adobe verwendet werden.
contentOwner: AG
feature: Asset Insights,Asset-Berichte
role: Business Practitioner,Administrator
exl-id: a9604b09-1c83-4c1e-aff7-13107b898cb3
source-git-commit: af2d14f92efb88143ccefe7fe29f83ae515e5981
workflow-type: tm+mt
source-wordcount: '798'
ht-degree: 59%

---

# Assets Insights {#asset-insights}

Erfahren Sie, wie Sie mit der Funktion Assets Insights Benutzerbewertungen und Nutzungsstatistiken von Assets nachverfolgen können, die auf Drittanbieter-Websites, in Marketingkampagnen und in den Kreativlösungen der Adobe verwendet werden.

Mit der Funktion &quot;Asset Insights&quot;können Sie Benutzerbewertungen und Nutzungsstatistiken von Assets verfolgen, die auf Drittanbieter-Websites, in Marketingkampagnen und den Kreativlösungen der Adobe verwendet werden, um Einblicke in ihre Leistung und Beliebtheit zu erhalten.

Asset Insights erfasst Details zur Benutzeraktivität, wie z. B. die Anzahl der Asset-Bewertungen und -Aufrufe sowie der Impressionen (also wie oft das Asset auf der Website geladen wird). Basierend auf diesen Statistiken wird Assets eine Bewertung zugewiesen. Sie können die Bewertungen und Leistungs-Statistiken verwenden, um beliebte Assets für die Berücksichtigung in Katalogen, Marketing-Kampagnen usw. auszuwählen. Sie können sogar Archiv- und Lizenzerneuerungsrichtlinien für Assets auf Grundlage dieser Statistiken formulieren.

Damit Asset Insights Nutzungsstatistiken für Assets von einer Website erfasst, müssen Sie Code für die Assets im Website-Code einbetten.

Damit Assets Insights Nutzungsstatistiken für Assets anzeigen kann, konfigurieren Sie zunächst die Funktion, um Berichtsdaten von [!DNL Adobe Analytics] abzurufen. Weitere Informationen finden Sie unter [Konfigurieren von Assets Insights](touch-ui-configuring-asset-insights.md). Um diese Funktion in einer On-Premise-Installation zu verwenden, erwerben Sie die Lizenz [!DNL Adobe Analytics] separat. Kunden mit [!DNL Managed Services] erhalten die [!DNL Analytics] -Lizenz im Paket mit [!DNL Experience Manager]. Siehe [Managed Services-Produktbeschreibung](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html).

>[!NOTE]
>
>Einblicke werden nur für Bilder unterstützt und bereitgestellt.

## Anzeigen von Statistiken für ein Asset {#viewing-statistics-for-an-asset}

Sie können die Asset Insights-Bewertungen auf der Metadatenseite anzeigen.

1. Wählen Sie in der Assets-Benutzeroberfläche das Asset aus und tippen oder klicken Sie anschließend in der Symbolleiste auf das Symbol **[!UICONTROL Eigenschaften]**.
1. Tippen oder klicken Sie auf der Seite „Eigenschaften“ auf die Registerkarte **[!UICONTROL Statistiken]**.
1. Überprüfen Sie die Nutzungsdetails für das Asset auf der Registerkarte **[!UICONTROL Insights]**. Der Abschnitt **[!UICONTROL Bewertung]** beschreibt die gesamte Asset-Nutzung und die Leistungsbewertungen eines Assets.

   Die Nutzungsbewertung beschreibt, wie oft ein Asset in verschiedenen Lösungen verwendet wird.

   Die Bewertung **[!UICONTROL Impressionen]** beschreibt, wie oft das Asset auf der Website geladen wurde. Die unter **[!UICONTROL Klicks]** angezeigte Zahl beschreibt, wie oft Benutzer auf das Asset geklickt haben.

1. Im Abschnitt **[!UICONTROL Nutzungsstatistiken]** können Sie ermitteln, in welchen Elementen das Asset enthalten war und in welchen Kreativlösungen es vor Kurzem verwendet wurde. Je höher die Nutzung, desto größer ist die Wahrscheinlichkeit, dass das Asset bei Benutzern beliebt ist. Nutzungsdaten werden unter den folgenden Überschriften angezeigt:

   * **[!UICONTROL Asset]**: Wie oft war das Asset Teil einer Sammlung oder eines zusammengesetzten Assets
   * **[!UICONTROL Web und Mobile]**: Wie oft wurde das Asset in Websites und Apps verwendet
   * **[!UICONTROL Social]**: Wie oft wurde das Asset in Lösungen wie Adobe Social und Adobe Campaign verwendet
   * **[!UICONTROL E-Mail]**: Wie oft wurde das Asset in E-Mail-Kampagnen verwendet

   ![Nutzungsstatistiken](assets/usage_statistics.png)

   >[!NOTE]
   >
   >Die Funktion &quot;Assets Insights&quot;ruft die Lösungsdaten regelmäßig von [!DNL Adobe Analytics] ab. Im Abschnitt &quot;Lösungen&quot;werden möglicherweise nicht die neuesten Daten angezeigt. Der Zeitraum, für den die Daten angezeigt werden, hängt vom Zeitplan des Abrufvorgangs ab, den Assets Insights zum Abrufen von [!DNL Analytics]-Daten ausführt.

1. Um Leistungsstatistiken für das Asset für einen bestimmten Zeitraum grafisch anzuzeigen, wählen Sie den gewünschten Zeitraum im Abschnitt **[!UICONTROL Leistungsstatistiken]** aus. Details wie Klicks und Impressions werden als Trend-Linien eines Diagramms angezeigt.

   ![chlimage_1-3](assets/chlimage_1-3.jpeg)

   >[!NOTE]
   >
   >Im Gegensatz zu den Daten im Abschnitt &quot;Lösungen&quot;werden im Abschnitt &quot;Leistungsstatistiken&quot;die neuesten Daten angezeigt.

1. Um den Einbettungscode für das Asset zu erhalten, das Sie in Websites zum Abrufen von Leistungsdaten einschließen, klicken Sie unter der Asset-Miniaturansicht auf **[!UICONTROL Einbettungscode abrufen]** . Weitere Informationen dazu, wie Sie Ihren Einbettungscode in Webseiten von Drittanbietern einbeziehen, finden Sie unter [Verwenden von Seitenverfolgung und Einbettungscode in Webseiten](touch-ui-using-page-tracker.md).

   ![chlimage_1-303](assets/chlimage_1-303.png)

## Anzeigen von Aggregat-Statistiken für Assets {#viewing-aggregate-statistics-for-assets}

Mit der **[!UICONTROL Insights-Ansicht]** können Sie Bewertungen aller Assets in einem Ordner gleichzeitig anzeigen.

1. Navigieren Sie in der Assets-Benutzeroberfläche zum Ordner, in dem die Assets enthalten sind, für die Sie Statistiken anzeigen möchten.
1. Tippen oder klicken Sie auf das Layout-Symbol und wählen Sie **[!UICONTROL Insight-Ansicht]** aus.
1. Die Seite zeigt die Nutzungsbewertungen für die Assets an. Vergleichen Sie die Bewertungen der verschiedenen Assets und ziehen Sie Ihre Erkenntnisse daraus.

## Planen von Hintergrundaufträgen {#scheduling-background-job}

Assets Insights ruft regelmäßig Nutzungsdaten für Assets aus Adobe Analytics Report Suites ab. Standardmäßig führt Assets Insights alle 24 Stunden um 2 Uhr einen Hintergrundauftrag aus, um die Daten abzurufen. Sie können jedoch die Häufigkeit und die Zeit ändern, indem Sie den Dienst **[!UICONTROL Adobe CQ DAM Asset Performance Report Sync Job]** von der Web-Konsole aus konfigurieren.

1. Tippen Sie auf das AEM-Logo und navigieren Sie anschließend zu **[!UICONTROL Tools > Vorgänge > Web-Konsole]**.
1. Öffnen Sie die Service-Konfiguration **[!UICONTROL Adobe CQ DAM Asset Performance Report Sync Job]**.

   ![chlimage_1-304](assets/chlimage_1-304.png)

1. Geben Sie die gewünschte Terminplaner-Häufigkeit und Startzeit für den Auftrag im Eigenschaftsplanerausdruck ein. Speichern Sie die Änderungen.
