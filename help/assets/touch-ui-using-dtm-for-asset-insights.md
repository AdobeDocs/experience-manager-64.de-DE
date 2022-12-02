---
title: Aktivieren von Assets Insights über DTM
description: Erfahren Sie, wie Sie Asset Insights mit Adobe Dynamic Tag Management (DTM) aktivieren können.
contentOwner: AG
feature: Asset Insights,Asset Reports
role: User,Admin
exl-id: d19cea4d-5395-479d-b303-4529ae2c0bf2
source-git-commit: 1679bbab6390808a1988cb6fe9b7692c3db31ae4
workflow-type: tm+mt
source-wordcount: '674'
ht-degree: 61%

---

# Aktivieren von Assets Insights über DTM {#enabling-asset-insights-through-dtm}

Adobe Dynamic Tag Management ist ein Tool, mit dem Sie Ihre digitalen Marketing-Tools aktivieren können. Es wird Adobe Analytics-Kunden kostenlos bereitgestellt. Sie können entweder Ihren Tracking-Code anpassen, damit CMS-Lösungen von Drittanbietern Assets Insights nutzen können, oder Sie können DTM verwenden, um Assets Insights-Tags einzufügen. Insights werden nur für Bilder unterstützt und bereitgestellt.

>[!CAUTION]
>
>Adobe DTM ist zugunsten von [!DNL Adobe Experience Platform] veraltet und wird bald das [Ende seiner Lebensdauer](https://medium.com/launch-by-adobe/dtm-plans-for-a-sunset-3c6aab003a6f) erreichen. Adobe empfiehlt, dass Sie [ [!DNL Adobe Experience Platform] für Assets Insights verwenden](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/advanced/asset-insights-launch-tutorial.html?lang=de).

Führen Sie diese Schritte durch, um Asset Insights über DTM zu aktivieren:

1. Tippen/klicken Sie auf [!DNL Experience Manager] -Logo und navigieren Sie zu **[!UICONTROL Instrumente]** > **[!UICONTROL Assets]** > **[!UICONTROL Insights-Konfiguration]**.
1. [Konfigurieren [!DNL Experience Manager] Instanz mit DTM-Cloud Service](../sites-administering/dtm.md)

   Das API-Token sollte verfügbar sein, sobald Sie sich bei [https://dtm.adobe.com](https://dtm.adobe.com/) und Besuch **[!UICONTROL Kontoeinstellungen]** über das Symbol Profil . Dieser Schritt ist aus der Sicht von Assets Insights nicht erforderlich, da die Integration von [!DNL Experience Manager Sites] mit Assets Insights ist noch in Arbeit.

1. Melden Sie sich bei [https://dtm.adobe.com](https://dtm.adobe.com/) an und wählen Sie ggf. ein Unternehmen aus.
1. Erstellen/Öffnen einer vorhandenen Webeigenschaft

   * Wählen Sie die **[!UICONTROL Webeigenschaften]** und tippen/klicken Sie dann auf **[!UICONTROL Eigenschaft hinzufügen]**.
   * Aktualisieren Sie die Felder entsprechend und tippen/klicken Sie auf **[!UICONTROL Eigenschaft erstellen]** (siehe [Dokumentation](https://helpx.adobe.com/de/experience-manager/using/dtm.html)).

   ![chlimage_1-193](assets/chlimage_1-193.png)

1. Im **[!UICONTROL Regeln]** Registerkarte, wählen Sie **[!UICONTROL Seitenladeregeln]** Tippen/klicken Sie im Navigationsfenster auf **[!UICONTROL Neue Regel erstellen]**.

   ![chlimage_1-194](assets/chlimage_1-194.png)

1. Erweitern **[!UICONTROL JavaScript/Drittanbieter-Tags]**. Tippen/klicken Sie dann auf **[!UICONTROL Neues Skript hinzufügen]** im **[!UICONTROL Sequenzielles HTML]** -Registerkarte, um das Dialogfeld &quot;Skript&quot;zu öffnen.

   ![chlimage_1-195](assets/chlimage_1-195.png)

1. Tippen/klicken Sie auf [!DNL Experience Manager] -Logo und navigieren Sie zu **[!UICONTROL Tools > Assets]**.
1. Tippen/klicken **[!UICONTROL Insights-Seitenverfolgung]**, kopieren Sie den Tracker-Code und fügen Sie ihn dann in das Dialogfeld &quot;Skript&quot;ein, das Sie in Schritt 6 geöffnet haben. Speichern Sie die Änderungen.

   >[!NOTE]
   >
   >* `AppMeasurement.js` wurde entfernt. Es wird erwartet, dass es über das Adobe Analytics-Tool von DTM verfügbar ist.
   >* Der Aufruf an `assetAnalytics.dispatcher.init()` wird entfernt. Es wird erwartet, dass die Funktion erneut aufgerufen wird, sobald das Adobe Analytics-Tool von DTM vollständig geladen ist.
   >* Je nachdem, wo der Asset Insights-Seitenverfolgung gehostet wird (z. B. AEM, CDN usw.), muss der Ursprung der Skriptquelle möglicherweise geändert werden.
   >* Bei AEM gehosteten Seitenverfolgung sollte die Quelle mit dem Hostnamen der Dispatcher-Instanz auf eine Veröffentlichungsinstanz verweisen.


1. Öffnen Sie [https://dtm.adobe.com](https://dtm.adobe.com). Klicken Sie in der Web-Eigenschaft auf Übersicht und dann auf Tool hinzufügen oder öffnen Sie ein vorhandenes Adobe Analytics-Tool. Beim Erstellen des Tools können Sie die Konfigurationsmethode auf Automatisch festlegen.

   ![chlimage_1-196](assets/chlimage_1-196.png)

   Wählen Sie die Report Suites „Bereitstellung/Produktion“ nach Bedarf.

1. Erweitern Sie **[!UICONTROL Bibliotheksverwaltung]** und stellen Sie sicher, dass **[!UICONTROL Bibliothek laden unter]** auf **[!UICONTROL Seitenanfang]** eingestellt ist.

   ![chlimage_1-197](assets/chlimage_1-197.png)

1. Erweitern **[!UICONTROL Seiten-Code anpassen]** und klicken oder tippen Sie auf **[!UICONTROL Editor öffnen]**.

   ![chlimage_1-198](assets/chlimage_1-198.png)

1. Fügen Sie den folgenden Code in das Fenster ein:

   ```java
   var sObj;
   
   if (arguments.length > 0) {
     sObj = arguments[0];
   } else {
     sObj = _satellite.getToolsByType('sc')[0].getS();
   }
   _satellite.notify('in assetAnalytics customInit');
   (function initializeAssetAnalytics() {
     if ((!!window.assetAnalytics) && (!!assetAnalytics.dispatcher)) {
       _satellite.notify('assetAnalytics ready');
       /** NOTE:
           Copy over the call to 'assetAnalytics.dispatcher.init()' from Assets Pagetracker
           Be mindful about changing the AppMeasurement object as retrieved above.
       */
       assetAnalytics.dispatcher.init(
             "",  /** RSID to send tracking-call to */
             "",  /** Tracking Server to send tracking-call to */
             "",  /** Visitor Namespace to send tracking-call to */
             "",  /** listVar to put comma-separated-list of Asset IDs for Asset Impression Events in tracking-call, e.g. 'listVar1' */
             "",  /** eVar to put Asset ID for Asset Click Events in, e.g. 'eVar3' */
             "",  /** event to include in tracking-calls for Asset Impression Events, e.g. 'event8' */
             "",  /** event to include in tracking-calls for Asset Click Events, e.g. 'event7' */
             sObj  /** [OPTIONAL] if the webpage already has an AppMeasurement object, please include the object here. If unspecified, Pagetracker Core shall create its own AppMeasurement object */
             );
       sObj.usePlugins = true;
       sObj.doPlugins = assetAnalytics.core.updateContextData;
       assetAnalytics.core.optimizedAssetInsights();
     }
     else {
       _satellite.notify('assetAnalytics not available. Consider updating the Custom Page Code', 4);
     }
   })();
   ```

   * Die Seitenladeregel in DTM enthält nur den Code &quot;pagetracker.js&quot;. Alle `assetAnalytics`-Felder überschreiben die Standardwerte. Sie sind nicht standardmäßig erforderlich.
   * Der Code ruft `assetAnalytics.dispatcher.init()` auf, nachdem sichergestellt wurde, dass `_satellite.getToolsByType('sc')[0].getS()` initialisiert und `assetAnalytics,dispatcher.init` verfügbar ist. Daher müssen Sie sie in Schritt 11 nicht notwendigerweise hinzufügen.
   * Wie in den Kommentaren innerhalb des Insights-Seitenverfolgungs-Codes (**[!UICONTROL Tools > Assets > Insights-Seitenverfolgung]**) angegeben, sind, wenn die Seitenverfolgung kein `AppMeasurement`-Objekt erstellt, die ersten drei Argumente (RSID, Tracking-Server und Besucher-Namespace) irrelevant. Leere Zeichenfolgen werden stattdessen übergeben, um dies hervorzuheben.

      Die restlichen Argumente entsprechen dem, was in der Statistiken-Konfigurationsseite konfiguriert ist (**[!UICONTROL Tools > Assets > Statistiken-Konfiguration]**).

   * Das AppMeasurement-Objekt wird abgerufen, indem `satelliteLib` für alle verfügbaren SiteCatalyst-Engines abgefragt wird. Wenn mehrere Tags konfiguriert sind, ändern Sie den Index des Array-Selektors entsprechend. Einträge im Array werden gemäß der SiteCatalyst-Tools geordnet, die in der DTM-Benutzeroberfläche verfügbar sind.

1. Speichern und schließen Sie das Code-Editor-Fenster und speichern Sie dann die Änderungen in der Tool-Konfiguration.
1. Genehmigen Sie auf der Registerkarte **[!UICONTROL Genehmigungen]** die beiden ausstehenden Genehmigungen. Das DTM-Tag ist für das Einfügen auf Ihrer Webseite bereit. Weitere Informationen zum Einfügen von DTM-Tags in Webseiten finden Sie auf der archivierten Seite zu [Integrieren von DTM in benutzerdefinierten Seitenvorlagen](https://web.archive.org/web/20180816221834/https://blogs.adobe.com/experiencedelivers/experience-management/integrating-dtm-custom-aem6-page-template).
