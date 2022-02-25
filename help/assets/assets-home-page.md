---
title: '"[!DNL Experience Manager Assets] Homepage-Erlebnis"'
description: Passen Sie die Assets-Startseite an, um Benutzern ein ansprechendes Erlebnis auf dem Willkommensbildschirm zu bieten, einschließlich einer Übersicht der letzten Aktivitäten rund um Assets.
contentOwner: AG
feature: Developer Tools,Asset Management
role: Admin,User
exl-id: f47c6da7-aa21-4f49-9c66-2a8091e19561
source-git-commit: d9cfb5376210234b3b05877509c273c52d9cecf3
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 45%

---

# [!DNL Adobe Experience Manager Assets] Startseiten-Erlebnis {#aem-assets-home-page-experience}

Personalisieren Sie die [!DNL Experience Manager Assets] Startseite für ein umfangreiches Begrüßungsbildschirm-Erlebnis, einschließlich einer Momentaufnahme der letzten Aktivitäten rund um Assets.

Die [!DNL Adobe Experience Manager Assets] Die Startseite bietet ein umfangreiches und personalisiertes Begrüßungsbildschirm-Erlebnis, das eine Momentaufnahme der letzten Aktivitäten enthält, z. B. der kürzlich angezeigten oder hochgeladenen Assets.

Die Assets-Startseite ist standardmäßig deaktiviert. Gehen Sie wie folgt vor, um sie zu aktivieren:

1. So greifen Sie auf [!DNL Experience Manager] Configuration Manager, klicken Sie auf **[!UICONTROL Tools > Vorgang > Web-Konsole]**.
1. Öffnen Sie die **Day CQ DAM Event Recorder** Dienst.
1. Wählen Sie die **[!UICONTROL Aktivieren dieses Dienstes]** zur Aktivierung der Aktivitätsaufzeichnung.

   ![chlimage_1-250](assets/chlimage_1-250.png)

1. Aus dem **Ereignistypen** , wählen Sie die Ereignisse aus, die aufgezeichnet werden sollen, und speichern Sie die Änderungen.

   >[!CAUTION]
   >
   >Die Aktivierung der Optionen „Angezeigte Assets“, „Angezeigte Projekte“ und „Angezeigte Sammlungen“ erhöht die Anzahl der aufgezeichneten Ereignisse erheblich.

1. Öffnen Sie die **[!UICONTROL Feature Flag &quot;DAM Asset Home Page&quot;]** Dienst von Configuration Manager `https://[AEM_server]:[port]/system/console/configMgr`.
1. Wählen Sie die **[!UICONTROL isEnabled.name]** -Option, um die Funktion &quot;Assets-Startseite&quot;zu aktivieren. Speichern Sie die Änderungen.

   ![chlimage_1-251](assets/chlimage_1-251.png)

1. Öffnen Sie die **[!UICONTROL Benutzereinstellungen]** und wählen Sie **[!UICONTROL Asset-Homepage aktivieren]**. Speichern Sie die Änderungen.

   ![user_Preferences](assets/user_preferences.png)

Navigieren Sie nach Aktivierung der Assets-Startseite von der Navigationsseite zur Assets-Benutzeroberfläche.

![home_page](assets/home_page.png)

Tippen/klicken Sie auf **[!UICONTROL Klicken Sie hier , um Ihren Erlebnislink zu konfigurieren.]** um Ihren Benutzernamen, Ihr Hintergrundbild und Ihr Profilbild hinzuzufügen.

Die Assets-Startseite enthält die folgenden Abschnitte:

* Begrüßungsabschnitt
* Widget-Abschnitt

**Begrüßungsabschnitt** 

Wenn Ihr Profil vorhanden ist, wird im Begrüßungsabschnitt eine Begrüßungsnachricht für Sie angezeigt. Darüber hinaus werden Ihr Profilbild und ein Willkommensbild angezeigt (sofern bereits konfiguriert).

Wenn Ihr Profil unvollständig ist, zeigt der Begrüßungsabschnitt eine generische Begrüßungsnachricht und einen Platzhalter für Ihr Profilbild an.

**Widget-Abschnitt** 

Dieser Abschnitt wird unter dem Begrüßungsabschnitt angezeigt und bietet fertige Widgets unter den folgenden Abschnitten:

* Aktivität
* Aktuell
* Entdecken

**Aktivität**: Unter diesem Abschnitt wird die **Meine Aktivität** Widget zeigt die letzten Aktivitäten an, die der angemeldete Benutzer mit Assets ausgeführt hat (einschließlich Assets ohne Ausgabedarstellungen), z. B. Asset-Uploads, -Downloads, Asset-Erstellung, Bearbeitungen, Kommentare, Anmerkungen und Teilen-Vorgänge.

**Zuletzt**: Die **Kürzlich angezeigt** -Widget unter diesem Abschnitt zeigt die kürzlich vom angemeldeten Benutzer aufgerufenen Entitäten an, darunter Ordner, Sammlungen und Projekte.

**Discover**: Die **Neu** Widget unter diesem Abschnitt zeigt die Assets und Ausgabedarstellungen an, die kürzlich in die [!DNL Assets] -Instanz.

Um die Bereinigung der Benutzeraktivitätsdaten zu ermöglichen, aktivieren Sie die **DAM-Ereignisbereinigungsdienst** von Configuration Manager aus. Nachdem Sie den Dienst aktiviert haben, werden die Aktivitäten des angemeldeten Benutzers, die eine bestimmte Anzahl überschreiten, vom System gelöscht.

Der Begrüßungsbildschirm enthält einfache Navigationshilfen, z. B. Symbole in der Symbolleiste für das Zugreifen auf Ordner, Sammlungen und Kataloge.

>[!NOTE]
>
>Durch die Aktivierung der Day CQ DAM Event Recorder- und DAM Event Purge-Dienste werden Schreibvorgänge in JCR und die Suchindizierung erhöht, was die Belastung der [!DNL Experience Manager] Server. Die zusätzliche Belastung der [!DNL Experience Manager] -Server kann sich auf seine Leistung auswirken.

>[!CAUTION]
>
>Das Erfassen, Filtern und Bereinigen von Benutzeraktivitäten für die Asset-Homepage erfordert Mehraufwand. Daher sollten Administratoren die Homepage für Zielbenutzer effektiv konfigurieren.
>
>Adobe empfiehlt Administratoren und Benutzern, die mit großen Datenmengen arbeiten, die Verwendung der Asset-Homepage-Funktion zu vermeiden, um einen Anstieg der Benutzeraktivitäten zu verhindern. Außerdem können Administratoren Aufzeichnungsaktivitäten von bestimmten Benutzern unterbinden, indem sie den **Day CQ DAM Event Recorder** vom Configuration Manager aus konfigurieren.
>
>Wenn Sie die Funktion verwenden, empfiehlt Adobe, dass Sie die Bereinigungsfrequenz auf der Grundlage der Serverlast planen.
