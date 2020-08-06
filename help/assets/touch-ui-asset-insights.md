---
title: Verwenden Sie die Funktion "Asset Insight", um die Nutzung Ihrer Bilder zu verfolgen
description: Mit der Asset Insights-Funktion können Sie Benutzerbewertungen und Nutzungsstatistiken von Bildern verfolgen, die auf Websites von Drittanbietern, in Marketing-Kampagnen und in kreativen Lösungen der Adobe verwendet werden.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0e0e2aa693c30c8e1ef1033b936b82d83e5b348e
workflow-type: tm+mt
source-wordcount: '773'
ht-degree: 86%

---


# Asset Insights {#asset-insights}

Erfahren Sie, wie Sie mit der Funktion „Asset Insights“ Benutzerbewertungen und Nutzungsstatistiken von Assets nachverfolgen können, die auf Drittanbieter-Websites, in Marketingkampagnen und den Kreativlösungen von Adobe verwendet werden. 

Mit der Funktion „Asset Insights“ können Sie Benutzerbewertungen und Nutzungsstatistiken von Assets nachverfolgen, die auf Drittanbieter-Websites, in Marketingkampagnen sowie in den Kreativlösungen von Adobe verwendet werden, um Einblicke in Performance und Beliebtheit zu gewinnen.

Asset Insights erfasst Details zur Benutzeraktivität, wie z. B. die Anzahl der Asset-Bewertungen und -Aufrufe sowie der Impressionen (also wie oft das Asset auf der Website geladen wird). Basierend auf diesen Statistiken wird Assets eine Bewertung zugewiesen. Sie können die Bewertungen und Leistungs-Statistiken verwenden, um beliebte Assets für die Berücksichtigung in Katalogen, Marketing-Kampagnen usw. auszuwählen. Sie können sogar Archiv- und Lizenzerneuerungsrichtlinien für Assets auf Grundlage dieser Statistiken formulieren.

Damit Asset Insights Nutzungsstatistiken für Assets von einer Website erfasst, müssen Sie Code für die Assets im Website-Code einbetten.

Damit Asset Insights Nutzungsstatistiken für Assets anzeigen kann, konfigurieren Sie zunächst die Funktion für den Abruf von Berichtsdaten aus [!DNL Adobe Analytics]. Weitere Details finden Sie unter [Asset Insights konfigurieren](touch-ui-configuring-asset-insights.md).

>[!NOTE]
>
>Einblicke werden nur für Bilder unterstützt und bereitgestellt.

## View statistics for an asset {#viewing-statistics-for-an-asset}

Sie können die Asset Insights-Bewertungen über die Metadatenseite anzeigen.

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
   >Da die Asset Insights-Funktion in der Regel die Lösungsdaten regelmäßig von Adobe Analytics abruft, werden im Abschnitt &quot;Lösungen&quot;möglicherweise nicht die neuesten Daten angezeigt. Der Zeitraum, für den die Daten angezeigt werden, hängt vom Zeitplan des Abholvorgangs ab, mit dem Asset Insights ausgeführt wird, um Daten aus Analytics abzurufen.

1. Um Leistungsstatistiken für das Asset für einen bestimmten Zeitraum grafisch anzuzeigen, wählen Sie den gewünschten Zeitraum im Abschnitt **[!UICONTROL Leistungsstatistiken]** aus. Details wie Klicks und Impressions werden als Trend-Linien eines Diagramms angezeigt.

   ![chlimage_1-3](assets/chlimage_1-3.jpeg)

   >[!NOTE]
   >
   >Im Gegensatz zu den Daten im Abschnitt „Lösungen“ zeigt der Abschnitt „Leistungsstatistiken“ die neuesten Daten an.

1. Um den Einbettungs-Code für das Asset zu erhalten, das Sie zu Websites hinzufügen, um Leistungsdaten zu gewinnen, tippen oder klicken Sie unter der Asset-Miniaturansicht auf **[!UICONTROL Einbettungs-Code abrufen]**. For more information on how to include your Embed code in third-party web pages, see [Using Page Tracker and Embed code in web pages](touch-ui-using-page-tracker.md).

   ![chlimage_1-303](assets/chlimage_1-303.png)

## View aggregate statistics for assets {#viewing-aggregate-statistics-for-assets}

Mit der **[!UICONTROL Insights-Ansicht]** können Sie Bewertungen aller Assets in einem Ordner gleichzeitig anzeigen.

1. Navigieren Sie in der Assets-Benutzeroberfläche zum Ordner, in dem die Assets enthalten sind, für die Sie Statistiken anzeigen möchten.
1. Tippen oder klicken Sie auf das Layout-Symbol und wählen Sie **[!UICONTROL Insight-Ansicht]** aus.
1. Die Seite zeigt die Nutzungsbewertungen für die Assets an. Vergleichen Sie die Bewertungen der verschiedenen Assets und ziehen Sie Ihre Erkenntnisse daraus.

## Planen von Hintergrundaufträgen {#scheduling-background-job}

Asset Insights ruft regelmäßig Nutzungsdaten für Assets aus den Adobe Analytics-Report Suites ab. Standardmäßig führt Asset Insights alle 24 Stunden um 2 Uhr Hintergrundjobs aus, um Daten abzurufen. Sie können jedoch die Häufigkeit und die Zeit ändern, indem Sie den Dienst **[!UICONTROL Adobe CQ DAM Asset Performance Report Sync Job]** von der Web-Konsole aus konfigurieren.

1. Tippen Sie auf das AEM-Logo und navigieren Sie anschließend zu **[!UICONTROL Tools > Vorgänge > Web-Konsole]**.
1. Öffnen Sie die Service-Konfiguration **[!UICONTROL Adobe CQ DAM Asset Performance Report Sync Job]**.

   ![chlimage_1-304](assets/chlimage_1-304.png)

1. Geben Sie die gewünschte Terminplaner-Häufigkeit und Startzeit für den Auftrag im Eigenschaftsplanerausdruck ein. Speichern Sie die Änderungen.
