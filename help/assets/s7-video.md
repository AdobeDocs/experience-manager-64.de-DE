---
title: Video
description: Erfahren Sie mehr über die zentralisierte Verwaltung von Video-Assets, bei der Sie Videos für Experience Manager Assets zur automatischen Kodierung in Dynamic Media Classic hochladen können. Sie können auch direkt über Experience Manager Assets auf Dynamic Media Classic-Videos zugreifen. Durch die Dynamic Media Classic-Videointegration wird die Reichweite optimierter Videos auf alle Bildschirme mit automatischer Geräte- und Bandbreitenerkennung erweitert.
contentOwner: rbrough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: managing-assets
content-type: reference
exl-id: 081e7db0-95cc-4260-8f08-318cd7d9d5b4
feature: Video
role: User
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '1603'
ht-degree: 66%

---

# Video  {#video}

Assets bieten eine zentralisierte Verwaltung von Video-Assets, mit der Sie Videos direkt in Assets hochladen können, um sie automatisch in Dynamic Media Classic zu kodieren. Sie können auch direkt aus Assets auf Dynamic Media Classic-Videos für die Seitenbearbeitung zugreifen.

Die Dynamic Media Classic-Videointegration erweitert die Reichweite optimierter Videos auf alle Bildschirme (automatische Geräteanpassung und Bandbreitenerkennung).

Die Komponente **[!UICONTROL Scene7-Video]** führt automatisch eine Geräte- und Bandbreitenerkennung durch, damit Videos auf Desktop-, Tablet- und Mobilgeräten im richtigen Format und in einer geeigneten Qualität wiedergegeben werden.

Sie können adaptive Videosets anstelle nur einzelner Video-Assets einschließen. Ein adaptives Videoset ist ein Container für alle Videoausgabedarstellungen, die für die nahtlose Wiedergabe des Videos über mehrere Bildschirme hinweg erforderlich sind. Ein adaptives Videoset gruppiert Versionen desselben Videos, die mit unterschiedlichen Bitraten und Formaten kodiert wurden. Beispiel: 400 kBit/s, 800 kBit/s und 1000 kBit/s. Sie verwenden ein adaptives Videoset zusammen mit der S7-Videokomponente für adaptives Video-Streaming über mehrere Bildschirmtypen hinweg. Beispielsweise Desktop-, iOS-, Android-, BlackBerry- und Windows-Mobilgeräte.

Weitere Informationen finden Sie in der [Dynamic Media Classic-Dokumentation zu adaptiven Videosets](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/dynamicmedia/video-profiles.html#dynamicmedia).

## Über FFMPEG und Dynamic Media Classic {#about-ffmpeg-and-scene}

Die Grundlage des standardmäßigen Videokodierungsprozesses ist die Verwendung der FFMPEG-basierten Integration mit Videoprofilen. Aus diesem Grund enthält der Standard-Aufnahme-Workflow von DAM die folgenden ffmpeg-basierten Workflow-Schritte:

* FFMPEG-Miniaturen
* FFMPEG-Kodierung

Durch Aktivierung und Konfiguration der Dynamic Media Classic-Integration werden diese beiden Workflow-Schritte im standardmäßigen Aufnahme-Workflow von DAM nicht automatisch entfernt oder deaktiviert. Wenn Sie die FFMPEG-basierte Videokodierung in Experience Manager bereits nutzen, ist es wahrscheinlich, dass FFMPEG in Ihren Authoring-Umgebungen bereits installiert ist. In diesem Fall würde ein Video, das über DAM aufgenommen wurde, zweimal kodiert werden: einmal durch den FFMPEG-Kodierer und einmal durch die Dynamic Media Classic-Integration.

Wenn Sie die FFMPEG-basierte Videokodierung in AEM konfiguriert und FFMPEG installiert haben, können Sie die beiden FFMPEG-Workflows aus Ihren DAM-Aufnahme-Workflows entfernen.

## Unterstützte Formate {#supported-formats}

Die folgenden Formate werden für die Scene7-Videokomponente unterstützt:

* F4V H.264
* H.264 (.mp4)

## Festlegen eines Speicherorts für hochgeladene Videos {#deciding-where-to-upload-your-video}

Der Speicherort für hochgeladene Videos hängt von folgenden Faktoren ab:

* Benötigen Sie für das Video-Asset einen Workflow?
* Benötigen Sie für das Video-Asset eine Versionskontrolle?

Falls Sie eine der Fragen mit „ja“ beantworten können, laden Sie Ihr Video direkt in Adobe DAM hoch. Lautet die Antwort auf beide Fragen „nein“, sollten Sie Ihr Video direkt in Dynamic Media Classic hochladen. Der Workflow für jedes Szenario wird in den nächsten Abschnitten beschrieben.

### Wenn Sie Ihr Video direkt in Adobe DAM hochladen {#if-you-are-uploading-your-video-directly-to-adobe-dam}

Wenn Sie einen Workflow oder eine Versionierung für Ihre Assets benötigen, laden Sie sie zuerst in Adobe DAM hoch. Der folgende Workflow wird empfohlen:

1. Laden Sie das Video-Asset in Adobe DAM hoch. Es findet eine automatische Kodierung und Veröffentlichung in Dynamic Media Classic statt.
1. Öffnen Sie Experience Manager und greifen Sie in WCM auf der Registerkarte **[!UICONTROL Filme]** des Content Finders auf Video-Assets zu.
1. Verwenden Sie die **[!UICONTROL Scene7]**- oder **[!UICONTROL Foundation]**-Videokomponente.

### Wenn Sie Ihr Video in Scene7 hochladen {#if-you-are-uploading-your-video-to-scene}

Wenn Sie keinen Workflow und keine Versionierung für Ihre Assets benötigen, laden Sie sie in Scene7 hoch. Der folgende Workflow wird empfohlen:

1. [Planen Sie in Dynamic Media Classic einen FTP-Upload und eine Kodierung für Scene7 (System automatisiert)](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/upload-publish/uploading-files.html#preparing-your-assets-and-folders-for-uploading).
1. Greifen Sie in Experience Manager in WCM auf der Registerkarte **[!UICONTROL Scene7]** des Content Finders auf Video-Assets zu.
1. Verwenden Sie die Komponente **[!UICONTROL Scene7-Video]**.

## Konfigurieren der Integration mit Scene7-Videos {#configuring-integration-with-scene-video}

So konfigurieren Sie universelle Vorlagen:

1. Navigieren Sie in **[!UICONTROL Cloud-Services]** zu Ihrer **[!UICONTROL Scene7]**-Konfiguration und klicken Sie auf **[!UICONTROL Bearbeiten]**.
1. Wählen Sie die Registerkarte **[!UICONTROL Video]** aus.

   ![chlimage_1-363](assets/chlimage_1-363.png)

   >[!NOTE]
   >
   >Die Registerkarte **[!UICONTROL Video]** wird nicht angezeigt, wenn die Seite keine Cloud-Konfiguration hat.

1. Wählen Sie das Profil für adaptive Videokodierung, ein Standardprofil für die Kodierung einzelner Videos, oder ein benutzerdefiniertes Videokodierungsprofil aus.

   >[!NOTE]
   >
   >Weitere Informationen dazu, was die Videovorgaben bedeuten, finden Sie in der [Dynamic Media Classic-Dokumentation](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/setup/application-setup.html?lang=de#video-presets-for-encoding-video-files).
   >
   >Adobe empfiehlt, entweder beide adaptive Videosets bei der Konfiguration der universellen Vorgaben oder die Option **[!UICONTROL Adaptive Videokodierung]** auszuwählen.

1. Die ausgewählten Kodierungsprofile werden automatisch auf alle Videos angewendet, die in den CQ DAM-Zielordner, den Sie für diese Scene7-Cloud-Konfiguration einrichten, hochgeladen werden. Sie können mehrere Scene7-Cloud-Konfigurationen mit verschiedenen Zielordnern einrichten, um nach Bedarf verschiedene Kodierungsprofile anzuwenden.

## Aktualisieren von Viewer- und Kodierungsvorlagen {#updating-viewer-and-encoding-presets}

Es ist erforderlich, die Viewer- und Kodierungsvorgaben für Videos in Experience Manager zu aktualisieren, wenn die Vorgaben in Scene7 aktualisiert wurden. Navigieren Sie in diesen Fällen zur Scene7-Konfiguration in der Cloud-Konfiguration und klicken Sie auf **[!UICONTROL Aktualisieren von Viewer- und Kodierungsvorgaben]**.

![chlimage_1-364](assets/chlimage_1-364.png)

## Hochladen Ihres Übergeordneten Videos von Adobe DAM auf Scene7 {#uploading-your-master-video}

1. Navigieren Sie zum CQ DAM-Zielordner, in dem Sie Ihre Cloud-Konfiguration mit Scene7-Kodierungsprofilen eingerichtet haben.
1. Klicken Sie auf **[!UICONTROL Hochladen]**, um das Mastervideo hochzuladen. Hochladen und Kodieren von Videos sind abgeschlossen, nachdem der Workflow &quot;DAM-Update-Asset&quot;abgeschlossen ist und **[!UICONTROL In Scene7 veröffentlichen]** hat ein Häkchen.

   >[!NOTE]
   >
   >Es dauert einige Zeit, bis die Videominiaturen generiert werden.

   Durch Ziehen des Übergeordneten DAM-Videos auf die Videokomponente wird auf zugegriffen. *all* die Scene7-kodierten Proxy-Ausgabeformate für die Bereitstellung.

## Foundation-Videokomponente im Vergleich zur Scene7-Videokomponente {#foundation-video-component-versus-scene-video-component}

Wenn Sie Experience Manager nutzen, haben Sie auf die Videokomponente, die in Sites verfügbar ist, und auf die Scene7-Videokomponente Zugriff. Diese Komponenten sind nicht austauschbar.

Die Scene7-Videokomponente funktioniert nur für Scene7-Videos. Die Foundation-Komponente funktioniert mit Videos, die in Experience Manager (mit FFMPEG) gespeichert wurden, und Scene7-Videos.

Die folgende Matrix verdeutlicht, wann welche Komponente verwendet wird:

![chlimage_1-365](assets/chlimage_1-365.png)

>[!NOTE]
>
>Standardmäßig verwendet die S7-Videokomponente das universelle Videoprofil. Sie können jedoch den HTML5-basierten Videoplayer in Experience Manager abrufen. Kopieren Sie einfach den Einbettungscode des vordefinierten HTML5-Videoplayers und fügen Sie ihn in Ihre Experience Manager-Seite ein.

## Experience Manager-Videokomponente {#aem-video-component}

Selbst wenn die Verwendung der Scene7-Videokomponente für die Anzeige von Scene7-Videos empfohlen wird, sollten Sie Scene7-Videos mit der Foundation-Videokomponente verwenden, um die Vollständigkeit zu gewährleisten.

### Vergleich von Experience Manager-Videos und Scene7-Videos {#aem-video-and-scene-video-comparison}

In der folgenden Tabelle finden Sie einen Vergleich der unterstützen Funktionen der Experience Manager-Foundation-Videokomponente und der Scene7-Videokomponente:

|  | Experience Manager-Foundation-Video | Scene7 Video |
|---|---|---|
| Ansatz | HTML5 hat Priorität. Flash dient nur zum Ausweichen bei Nicht-HTML5-Inhalten. | Flash auf den meisten Desktopgeräten HTML5 kommt auf Mobilgeräten und Tablets zum Einsatz. |
| Bereitstellung | Progressiv | Adaptives Streaming |
| Nachverfolgung | Ja | Ja |
| Erweiterbarkeit | Ja | Ja (mit [Dokumentation zur HTML 5 Viewer SDK-API](https://s7d1.scene7.com/s7sdk/3.10/docs/jsdoc/index.html)) |
| Mobile Videos | Ja | Ja |

### Einrichtung {#setting-up}

#### Erstellen von Videoprofilen {#creating-video-profiles}

Die verschiedenen Videokodierungen werden entsprechend den in der Scene7-Cloud-Konfiguration ausgewählten Scene7-Kodierungsvorgaben erstellt. Damit die Foundation-Videokomponente sie verwendet, muss für jede ausgewählte Scene7-Kodierungsvorgabe ein Videoprofil erstellt werden. Mit dieser Methode kann die Videokomponente die DAM-Ausgabedarstellungen entsprechend auswählen.

>[!NOTE]
>
>Neue Videoprofile und Änderungen daran müssen für eine Veröffentlichung aktiviert werden.

1. Tippen Sie in Experience Manager auf **[!UICONTROL Instrumente] > [!UICONTROL Konfigurationskonsole]**.
1. Aus dem **[!UICONTROL Konfigurationskonsole]** navigieren zu **[!UICONTROL Tools > DAM > Videoprofile]** in der Navigationsstruktur.
1. Erstellen Sie ein Scene7-Videoprofil. Im **[!UICONTROL Neu...]** Dropdown-Liste auswählen **[!UICONTROL Seite erstellen]** und wählen Sie dann die Vorlage Scene7-Videoprofil aus. Geben Sie der neuen Videoprofilseite einen Namen und klicken Sie auf **[!UICONTROL Erstellen]**.

   ![chlimage_1-366](assets/chlimage_1-366.png)

1. Bearbeiten Sie das neue Videoprofil. Wählen Sie zuerst die Cloud-Konfiguration aus. Wählen Sie anschließend dieselbe Kodierungsvorlage aus, die Sie bereits in der Cloud-Konfiguration ausgewählt haben.

   ![chlimage_1-367](assets/chlimage_1-367.png)

   | Eigenschaft | Beschreibung |
   |---|---|
   | Scene7-Cloud-Konfiguration | Die Cloud-Konfiguration, die für die Kodierungsvorlagen verwendet werden soll |
   | Scene7-Kodierungsvorlage | Die Kodierungsvorlage, die diesem Videoprofil zugeordnet werden soll |
   | HTML5-Videotyp | Mit dieser Eigenschaft können Sie den Wert der Typeigenschaft des HTML5-Videoquellelements festlegen. Diese Information wird nicht von den S7-Kodierungsvorlagen bereitgestellt, sie ist jedoch erforderlich, um die Videos anhand des HTML5-Videoelements richtig zu rendern. Eine Liste für gängige Formate wird bereitgestellt, kann jedoch für andere Formate überschrieben werden. |

   Wiederholen Sie diesen Schritt für alle in der Cloud-Konfiguration ausgewählten Kodierungsvorgaben, die Sie in der Videokomponente verwenden möchten.

#### Design konfigurieren {#configuring-design}

Die **[!UICONTROL Foundation-Video]** -Komponente muss wissen, welche Videoprofile zum Erstellen der Videoquellenliste verwendet werden sollen. Öffnen Sie das Dialogfeld für das Design von Videokomponenten und konfigurieren Sie das Design der Komponenten für die Nutzung der neuen Videoprofile.

>[!NOTE]
>
>Wenn Sie die **[!UICONTROL Foundation]**-Videokomponente auf einer Mobilseite verwenden, wiederholen Sie diese Schritte für das Design der Mobilseite.

>[!NOTE]
>
>Änderungen am Design erfordern die Aktivierung des Designs, damit sie bei der Veröffentlichung wirksam werden können.

1. Öffnen Sie das Dialogfeld für das Design der **[!UICONTROL Foundation]**-Videokomponente und wechseln Sie auf die Registerkarte **[!UICONTROL Profile]**. Löschen Sie anschließend die vordefinierten Profile und fügen Sie die neuen S7-Videoprofile hinzu. Die Reihenfolge der Profilliste im Design-Dialogfeld definiert die Reihenfolge des Videoquellenelements beim Rendern.
1. Bei Browsern, die kein HTML5 unterstützen, ermöglicht die Videokomponente ein Ausweichen auf Flash. Öffnen Sie das Dialogfeld für das Design der Videokomponenten und wechseln Sie auf die Registerkarte **[!UICONTROL Flash]**. Konfigurieren Sie die Flash Player-Einstellungen und weisen Sie dem Flash Player ein Fallback-Profil zu.

#### Checkliste {#checklist}

1. Erstellen Sie eine S7-Cloud-Konfiguration. Vergewissern Sie sich, dass die Videokodierungsvorgaben festgelegt sind und das Importprogramm ausgeführt wird.
1. Erstellen Sie ein S7-Videoprofil für jede in der Cloud-Konfiguration ausgewählte Videokodierungsvorlage.
1. Die Videoprofile müssen aktiviert sein.
1. Konfigurieren Sie das Design der **[!UICONTROL Foundation]**-Videokomponente auf Ihrer Seite.
1. Aktivieren Sie das Design, sobald Sie mit Ihren Design-Änderungen fertig sind.
