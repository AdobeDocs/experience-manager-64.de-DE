---
title: "[!DNL Experience Manager Assets] Homepage-Erlebnis"
description: Personalisieren Sie die Assets-Startseite für ein umfangreiches Begrüßungsbildschirm-Erlebnis, einschließlich einer Momentaufnahme der letzten Aktivitäten rund um Assets.
contentOwner: AG
feature: Developer Tools,Asset Management
role: Admin,User
exl-id: f47c6da7-aa21-4f49-9c66-2a8091e19561
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '593'
ht-degree: 53%

---

# [!DNL Adobe Experience Manager Assets]-Startseiten-Erlebnis {#aem-assets-home-page-experience}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Personalisieren Sie die [!DNL Experience Manager Assets]-Startseite, um Benutzenden ein ansprechendes Erlebnis auf dem Willkommensbildschirm zu bieten, einschließlich einer Übersicht der letzten Aktivitäten rund um Assets.

Die [!DNL Adobe Experience Manager Assets] Die Startseite bietet ein umfangreiches und personalisiertes Begrüßungsbildschirm-Erlebnis, das eine Momentaufnahme der letzten Aktivitäten enthält, z. B. der kürzlich angezeigten oder hochgeladenen Assets.

Die Assets-Startseite ist standardmäßig deaktiviert. Gehen Sie wie folgt vor, um sie zu aktivieren:

1. So greifen Sie auf [!DNL Experience Manager] Configuration Manager, klicken Sie auf **[!UICONTROL Tools > Vorgang > Web-Konsole]**.
1. Öffnen Sie den Dienst **Day CQ DAM Event Recorder**.
1. Wählen Sie **[!UICONTROL Diesen Dienst aktivieren]** aus, um die Aktivitätsaufzeichnung zu aktivieren.

   ![chlimage_1-250](assets/chlimage_1-250.png)

1. Wählen Sie aus der Liste **Ereignistypen** die Ereignisse aus, die aufgezeichnet werden sollen, und speichern Sie die Änderungen.

   >[!CAUTION]
   >
   >Die Aktivierung der Optionen „Angezeigte Assets“, „Angezeigte Projekte“ und „Angezeigte Sammlungen“ erhöht die Anzahl der aufgezeichneten Ereignisse erheblich.

1. Öffnen Sie den Dienst **[!UICONTROL DAM Assets-Startseitenfunktion-Flag]** von Configuration Manager aus `https://[AEM_server]:[port]/system/console/configMgr`.
1. Wählen Sie die **[!UICONTROL isEnabled.name]** -Option, um die Funktion &quot;Assets-Startseite&quot;zu aktivieren. Speichern Sie die Änderungen.

   ![chlimage_1-251](assets/chlimage_1-251.png)

1. Öffnen Sie das Dialogfeld **[!UICONTROL Benutzereinstellungen]** und wählen Sie **[!UICONTROL Assets-Startseite aktivieren]** aus. Speichern Sie die Änderungen.

   ![user_Preferences](assets/user_preferences.png)

Navigieren Sie nach Aktivierung der Assets-Startseite von der Navigationsseite zur Assets-Benutzeroberfläche.

![home_page](assets/home_page.png)

Tippen/klicken Sie auf **[!UICONTROL Klicken Sie hier , um Ihren Erlebnislink zu konfigurieren.]** um Ihren Benutzernamen, Ihr Hintergrundbild und Ihr Profilbild hinzuzufügen.

Die Assets-Startseite enthält die folgenden Abschnitte:

* Begrüßungsabschnitt
* Widget-Bereich

**Begrüßungsabschnitt**

Wenn Ihr Profil vorhanden ist, wird im Begrüßungsabschnitt eine Begrüßungsnachricht für Sie angezeigt. Darüber hinaus werden Ihr Profilbild und ein Begrüßungsbild angezeigt (wenn bereits konfiguriert).

Wenn Ihr Profil unvollständig ist, werden im Bereich &quot;Willkommen&quot;eine allgemeine Willkommensnachricht und ein Platzhalter für Ihr Profilbild angezeigt.

**Widget-Bereich**

Dieser Abschnitt wird unter dem Begrüßungsabschnitt angezeigt und zeigt native Widgets unter den folgenden Abschnitten an:

* Aktivität
* Aktuell
* Entdecken

**Aktivität**: Unter diesem Abschnitt zeigt das Widget **Meine Aktivität** die aktuellsten Aktivitäten an, die angemeldete Benutzende mit Assets durchgeführt haben (einschließlich Assets ohne Ausgabedarstellungen), z. B. Asset-Uploads, -Downloads, Asset-Erstellung, Bearbeitungen, Kommentare, Anmerkungen und Freigaben.

**Aktuell**: Das Widget **Vor kurzem angezeigt** unter diesem Abschnitt zeigt vor kurzem durch angemeldete Benutzende aufgerufene Entitäten an, z. B. Ordner, Sammlungen und Projekte.

**Discover**: Die **Neu** Widget unter diesem Abschnitt zeigt die Assets und Ausgabedarstellungen an, die kürzlich in die [!DNL Assets] -Instanz.

Um das Löschen von Benutzeraktivitätsdaten zu aktivieren, aktivieren Sie den **DAM Event Purge-Dienst** vom Configuration Manager aus. Nachdem Sie diesen Dienst aktiviert haben, werden Aktivitäten des angemeldeten Benutzers, die eine bestimmte Anzahl überschreiten, vom System gelöscht.

Der Begrüßungsbildschirm bietet einfache Navigationshilfen, z. B. Symbole in der Symbolleiste für den Zugriff auf Ordner, Sammlungen und Kataloge.

>[!NOTE]
>
>Die Dienste Day CQ DAM Event Recorder und DAM Event Purge erhöhen die Zahl der JCR-Schreibvorgänge und die Suchindizierung, was die Last auf dem [!DNL Experience Manager]-Server erheblich erhöht. Die zusätzliche Last auf dem [!DNL Experience Manager]-Server kann dessen Leistung beeinträchtigen.

>[!CAUTION]
>
>Die Erfassung, Filterung und Bereinigung von Benutzeraktivitäten, die für die Asset-Startseite erforderlich sind, bringt einen Mehraufwand für die Leistung mit sich. Daher sollten Administratoren die Startseite für Zielbenutzer effektiv konfigurieren.
>
>Adobe empfiehlt Administratoren und Benutzern, die mit großen Datenmengen arbeiten, die Verwendung der Asset-Homepage-Funktion zu vermeiden, um einen Anstieg der Benutzeraktivitäten zu verhindern. Außerdem können Admins Aufzeichnungsaktivitäten von bestimmten Benutzenden unterbinden, indem sie den **Day CQ DAM Event Recorder** vom Configuration Manager aus konfigurieren.
>
>Wenn Sie die Funktion verwenden, empfiehlt Adobe, dass Sie die Bereinigungsfrequenz auf der Grundlage der Serverlast planen.
