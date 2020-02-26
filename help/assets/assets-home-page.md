---
title: AEM Assets-Startseitenerlebnis
description: Passen Sie die AEM Assets-Startseite an, um Benutzern ein ansprechendes Erlebnis auf dem Willkommensbildschirm zu bieten, einschließlich einer Übersicht der letzten Aktivitäten rund um Assets.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1

---


# AEM Assets-Startseitenerlebnis {#aem-assets-home-page-experience}

Passen Sie die AEM Assets-Startseite an, um Benutzern ein ansprechendes Erlebnis auf dem Willkommensbildschirm zu bieten, einschließlich einer Übersicht der letzten Aktivitäten rund um Assets.

Die Adobe Experience Manager (AEM) Assets-Startseite bietet ein ansprechendes und personalisiertes Willkommenserlebnis, einschließlich einer Übersicht der letzten Aktivitäten, wie z. B. kürzlich angezeigte oder hochgeladene Assets.

Die Assets-Startseite ist standardmäßig deaktiviert. Gehen Sie wie folgt vor, um sie zu aktivieren:

1. Um auf AEM Configuration Manager zuzugreifen, klicken Sie auf **[!UICONTROL Werkzeuge > Vorgang > Web-Konsole]**.
1. Open the **Day CQ DAM Event Recorder** service.
1. Select the **[!UICONTROL Enable this service]** to enable activity recording.

   ![chlimage_1-250](assets/chlimage_1-250.png)

1. From the **Event Types** list, select the events to be recorded and save the changes.

   >[!CAUTION]
   >
   >Die Aktivierung der Optionen „Angezeigte Assets“, „Angezeigte Projekte“ und „Angezeigte Sammlungen“ erhöht die Anzahl der aufgezeichneten Ereignisse erheblich.

1. Open the **[!UICONTROL DAM Asset Home Page Feature Flag]** service from Configuration Manager `https://[AEM_server]:[port]/system/console/configMgr`.
1. Select the **[!UICONTROL isEnabled.name]** option to enable the Assets Home page feature. Speichern Sie die Änderungen.

   ![chlimage_1-251](assets/chlimage_1-251.png)

1. Open the **[!UICONTROL User Preferences]** dialog, and select **[!UICONTROL Enable Assets Home Page]**. Speichern Sie die Änderungen.

   ![user_preferences](assets/user_preferences.png)

Nachdem Sie die Seite &quot;Assets-Homepage&quot;aktiviert haben, navigieren Sie zur Benutzeroberfläche &quot;Assets&quot;auf der Navigationsseite.

![home_page](assets/home_page.png)

Tap/click the **[!UICONTROL Click here to configure your experience link]** to add your username, background image, and profile image.

Die Assets-Startseite enthält die folgenden Abschnitte:

* Begrüßungsabschnitt
* Widget-Abschnitt

**Begrüßungsabschnitt** 

Wenn Ihr Profil vorhanden ist, wird im Begrüßungsabschnitt eine Begrüßungsnachricht für Sie angezeigt. Außerdem zeigt es Ihr Profilbild und ein Begrüßungsbild an (falls bereits konfiguriert).

Wenn Ihr Profil unvollständig ist, zeigt der Begrüßungsabschnitt eine generische Begrüßungsnachricht und einen Platzhalter für Ihr Profilbild an.

**Widget-Abschnitt** 

Dieser Abschnitt wird unter dem Begrüßungsabschnitt angezeigt und bietet fertige Widgets unter den folgenden Abschnitten:

* Aktivität
* Aktuell
* Entdecken

**Aktivität**: Unter diesem Abschnitt zeigt das Widget &quot; **Meine Aktivität** &quot;die zuletzt vom angemeldeten Benutzer durchgeführten Aktivitäten mit Assets (einschließlich Assets ohne Ausgabeformate) an, z. B. Assets hochladen, Downloads, Asset-Erstellung, Bearbeitungen, Kommentare, Anmerkungen und &quot;Teilen&quot;-Klicks.

**Zuletzt**: Das **kürzlich angezeigte** Widget unter diesem Abschnitt zeigt kürzlich aufgerufene Entitäten des angemeldeten Benutzers an, einschließlich Ordner, Sammlungen und Projekte.

**Discover**: Das **neue** Widget unter diesem Abschnitt zeigt die Assets und Darstellungen an, die kürzlich in die AEM Assets-Instanz hochgeladen wurden.

To enable purging of user activity data, enable the **DAM Event Purge Service** from Configuration Manager. Nachdem Sie den Dienst aktiviert haben, werden die Aktivitäten des angemeldeten Benutzers, die eine bestimmte Anzahl überschreiten, vom System gelöscht.

Der Begrüßungsbildschirm enthält einfache Navigationshilfen, z. B. Symbole in der Symbolleiste für das Zugreifen auf Ordner, Sammlungen und Kataloge.

>[!NOTE]
>
>Die Aktivierung der Day CQ DAM Event Recorder- und DAM Event Purge-Dienste erhöht die Schreibvorgänge in JCR und die Suchindizierung, wodurch die Belastung des AEM-Servers erheblich erhöht wird. Die zusätzliche Last auf dem AEM-Server kann dessen Leistung beeinträchtigen.

>[!CAUTION]
>
>Das Erfassen, Filtern und Bereinigen von Benutzeraktivitäten für die Asset-Homepage erfordert Mehraufwand. Daher sollten Administratoren die Homepage für Zielbenutzer effektiv konfigurieren.
>
>Adobe empfiehlt Administratoren und Benutzern, die mit großen Datenmengen arbeiten, die Verwendung der Asset-Homepage-Funktion zu vermeiden, um einen Anstieg der Benutzeraktivitäten zu verhindern. Außerdem können Administratoren Aufzeichnungsaktivitäten von bestimmten Benutzern unterbinden, indem sie den **Day CQ DAM Event Recorder** vom Configuration Manager aus konfigurieren.
>
>Wenn Sie die Funktion verwenden, empfiehlt Adobe, dass Sie die Bereinigungsfrequenz auf der Grundlage der Serverlast planen.
