---
title: AEM Assets-Startseitenerlebnis
description: Passen Sie die AEM Assets-Startseite an, um Benutzern ein ansprechendes Erlebnis auf dem Willkommensbildschirm zu bieten, einschließlich einer Übersicht der letzten Aktivitäten rund um Assets.
contentOwner: AG
feature: Developer Tools,Asset Management
role: Administrator,Business Practitioner
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 56%

---


# AEM Assets-Startseitenerlebnis {#aem-assets-home-page-experience}

Passen Sie die AEM Assets-Startseite an, um Benutzern ein ansprechendes Erlebnis auf dem Willkommensbildschirm zu bieten, einschließlich einer Übersicht der letzten Aktivitäten rund um Assets.

Die Adobe Experience Manager (AEM) Assets-Startseite bietet ein ansprechendes und personalisiertes Willkommenserlebnis, einschließlich einer Übersicht der letzten Aktivitäten, wie z. B. kürzlich angezeigte oder hochgeladene Assets.

Die Assets-Startseite ist standardmäßig deaktiviert. Gehen Sie wie folgt vor, um sie zu aktivieren:

1. Um auf AEM Configuration Manager zuzugreifen, klicken Sie auf **[!UICONTROL Tools > Vorgang > Web-Konsole]**.
1. Öffnen Sie den Dienst **Day CQ DAM Ereignis Recorder**.
1. Wählen Sie **[!UICONTROL Aktivieren Sie diesen Dienst]**, um die Aufzeichnung der Aktivität zu aktivieren.

   ![chlimage_1-250](assets/chlimage_1-250.png)

1. Wählen Sie in der Liste **Ereignistyp** die aufzuzeichnenden Ereignis aus und speichern Sie die Änderungen.

   >[!CAUTION]
   >
   >Die Aktivierung der Optionen „Angezeigte Assets“, „Angezeigte Projekte“ und „Angezeigte Sammlungen“ erhöht die Anzahl der aufgezeichneten Ereignisse erheblich.

1. Öffnen Sie den Dienst **[!UICONTROL DAM Asset Startseite Feature Flag]** in Configuration Manager `https://[AEM_server]:[port]/system/console/configMgr`.
1. Wählen Sie die Option **[!UICONTROL isEnabled.name]**, um die Funktion &quot;Asset-Startseite&quot;zu aktivieren. Speichern Sie die Änderungen.

   ![chlimage_1-251](assets/chlimage_1-251.png)

1. Öffnen Sie das Dialogfeld **[!UICONTROL Benutzereinstellungen]** und wählen Sie **[!UICONTROL Startseite &quot;Elemente aktivieren]**&quot;aus. Speichern Sie die Änderungen.

   ![user_preferences](assets/user_preferences.png)

Nachdem Sie die Assets-Startseite aktiviert haben, navigieren Sie auf der Navigationsseite zur Benutzeroberfläche &quot;Assets&quot;.

![home_page](assets/home_page.png)

Tippen/klicken Sie auf **[!UICONTROL Klicken Sie hier, um Ihren Erlebnislink]** zu konfigurieren, um Ihren Benutzernamen, Ihr Hintergrundbild und Ihr Profil hinzuzufügen.

Die Assets-Startseite enthält die folgenden Abschnitte:

* Begrüßungsabschnitt
* Widget-Abschnitt

**Begrüßungsabschnitt** 

Wenn Ihr Profil vorhanden ist, wird im Begrüßungsabschnitt eine Begrüßungsnachricht für Sie angezeigt. Außerdem werden Ihr Profil und ein Begrüßungsbild angezeigt (falls bereits konfiguriert).

Wenn Ihr Profil unvollständig ist, zeigt der Begrüßungsabschnitt eine generische Begrüßungsnachricht und einen Platzhalter für Ihr Profilbild an.

**Widget-Abschnitt** 

Dieser Abschnitt wird unter dem Begrüßungsabschnitt angezeigt und bietet fertige Widgets unter den folgenden Abschnitten:

* Aktivität
* Aktuell
* Entdecken

**Aktivität**: Unter diesem Abschnitt zeigt das  **My** Activity Widget die letzten Aktivitäten an, die der angemeldete Benutzer mit Assets (einschließlich Assets ohne Ausgabeformate) durchgeführt hat, z. B. Asset-Uploads, Downloads, Asset-Erstellung, Bearbeitungen, Kommentare, Anmerkungen und Teilen-Vorgänge.

**Zuletzt**: Das  **Widget &quot;Zuletzt** angezeigt&quot;unter diesem Abschnitt zeigt kürzlich aufgerufene Entitäten des angemeldeten Benutzers an, einschließlich Ordner, Sammlungen und Projekte.

**Discover**: Das  **** Widget unter diesem Abschnitt zeigt die Assets und Darstellungen an, die kürzlich in die AEM Assets-Instanz hochgeladen wurden.

Um das Bereinigen von Benutzerdaten zu aktivieren, aktivieren Sie den Dienst **DAM Ereignis Purge Service** in Configuration Manager. Nachdem Sie den Dienst aktiviert haben, werden die Aktivitäten des angemeldeten Benutzers, die eine bestimmte Anzahl überschreiten, vom System gelöscht.

Der Begrüßungsbildschirm enthält einfache Navigationshilfen, z. B. Symbole in der Symbolleiste für das Zugreifen auf Ordner, Sammlungen und Kataloge.

>[!NOTE]
>
>Die Aktivierung der Day CQ DAM Ereignis Recorder- und DAM Ereignis Purge-Dienste erhöht die Schreibvorgänge in JCR und die Suchindizierung, wodurch die Belastung auf dem AEM erheblich erhöht wird. Die zusätzliche Last auf dem AEM-Server kann dessen Leistung beeinträchtigen.

>[!CAUTION]
>
>Das Erfassen, Filtern und Bereinigen von Benutzeraktivitäten für die Asset-Homepage erfordert Mehraufwand. Daher sollten Administratoren die Homepage für Zielbenutzer effektiv konfigurieren.
>
>Adobe empfiehlt Administratoren und Benutzern, die mit großen Datenmengen arbeiten, die Verwendung der Asset-Homepage-Funktion zu vermeiden, um einen Anstieg der Benutzeraktivitäten zu verhindern. Außerdem können Administratoren Aufzeichnungsaktivitäten von bestimmten Benutzern unterbinden, indem sie den **Day CQ DAM Event Recorder** vom Configuration Manager aus konfigurieren.
>
>Wenn Sie die Funktion verwenden, empfiehlt Adobe, dass Sie die Bereinigungsfrequenz auf der Grundlage der Serverlast planen.
