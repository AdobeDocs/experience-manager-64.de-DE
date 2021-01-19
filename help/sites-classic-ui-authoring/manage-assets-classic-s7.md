---
title: Hinzufügen von Dynamic Media Classic-Funktionen zu einer Seite
seo-title: Hinzufügen von Dynamic Media Classic-Funktionen zu einer Seite
description: Adobe Dynamic Media Classic ist eine gehostete Lösung zum Verwalten, Erweitern, Veröffentlichen und Bereitstellen von Rich-Media-Assets für Web-, Mobil-, E-Mail- und Internetanzeigen und -drucke.
seo-description: Adobe Dynamic Media Classic ist eine gehostete Lösung zum Verwalten, Erweitern, Veröffentlichen und Bereitstellen von Rich-Media-Assets für Web-, Mobil-, E-Mail- und Internetanzeigen und -drucke.
uuid: 66b9c150-c482-4a41-9772-fa39c135802c
contentOwner: Alva Ware-Bevacqui
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 9ba95dce-a801-4a36-8798-45d295371b1b
translation-type: tm+mt
source-git-commit: 28e552f065d38225226d757c0af00d86d9ed8e07
workflow-type: tm+mt
source-wordcount: '3428'
ht-degree: 33%

---


# Hinzufügen von Dynamic Media Classic-Funktionen zu Ihrer Seite{#adding-scene-features-to-your-page}

[Adobe Dynamic Media ](https://help.adobe.com/en_US/scene7/using/WS26AB0D9A-F51C-464e-88C8-580A5A82F810.html) Classicis ist eine gehostete Lösung zum Verwalten, Erweitern, Veröffentlichen und Bereitstellen von Rich-Media-Assets für Web-, Mobil-, E-Mail- und Internetanzeigen und Drucken.

In Dynamic Media Classic veröffentlichte Assets können in verschiedenen Viewern Ansicht AEM werden:

* Zoom
* Flyout
* Video
* Bildvorlage
* Bild

Sie können digitale Assets direkt von AEM nach Dynamic Media Classic veröffentlichen und digitale Assets von Dynamic Media Classic nach AEM veröffentlichen.

In diesem Abschnitt wird beschrieben, wie digitale Assets von AEM nach Dynamic Media Classic und umgekehrt veröffentlicht werden. Die Viewer werden auch detailliert beschrieben. Informationen zum Konfigurieren von AEM für Dynamic Media Classic finden Sie unter [Integrieren von Dynamic Media Classic mit AEM](/help/sites-administering/scene7.md).

Siehe auch [Hinzufügen von Imagemaps](/help/assets/image-maps.md).

Weitere Informationen über die Arbeit mit Videokomponenten mit AEM finden Sie unter:

* [Video](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md)

>[!NOTE]
>
>Wenn Dynamic Media Classic-Assets nicht korrekt angezeigt werden, stellen Sie sicher, dass das dynamische Medium [deaktiviert](/help/assets/config-dynamic.md#disabling-dynamic-media) ist, und aktualisieren Sie dann die Seite.

## Manuelles Veröffentlichen in Dynamic Media Classic über Assets {#manually-publishing-to-scene-from-assets}

Sie können digitale Assets in Dynamic Media Classic entweder über die Asset-Konsole in der klassischen Benutzeroberfläche oder direkt vom Asset veröffentlichen.

>[!NOTE]
>
>AEM veröffentlicht asynchron in Dynamic Media Classic. Nach dem Klicken auf **[!UICONTROL Veröffentlichen]** kann es mehrere Sekunden dauern, bis Ihr Asset in Dynamic Media Classic veröffentlicht wird.


### Veröffentlichen über die Asset-Konsole {#publishing-from-the-assets-console}

So veröffentlichen Sie in der Asset-Konsole in Dynamic Media Classic, wenn sich die Assets in einem Dynamic Media Classic-Zielgruppen-Ordner befinden:

1. Klicken Sie in der klassischen Benutzeroberfläche von AEM auf **[!UICONTROL Digitale Assets]**, um auf den digitalen Asset-Manager zuzugreifen.

1. Wählen Sie das Asset (oder die Assets) bzw. den Ordner aus dem Ordner &quot;Zielgruppe&quot;, den Sie in Dynamic Media Classic veröffentlichen möchten, und klicken Sie mit der rechten Maustaste und wählen Sie **[!UICONTROL In Dynamic Media Classic veröffentlichen]**. Alternativ können Sie im Menü **[!UICONTROL Tools]** die Option **[!UICONTROL In Dynamic Media Classic veröffentlichen]** auswählen.

   ![chlimage_1-76](assets/chlimage_1-76.png)

1. Gehen Sie zu Dynamic Media Classic und bestätigen Sie, dass die Assets verfügbar sind.

   >[!NOTE]
   >
   >Wenn sich die Assets nicht in einem synchronisierten Dynamic Media Classic-Ordner befinden, ist **[!UICONTROL In Dynamic Media Classic veröffentlichen]** in beiden Menüs sichtbar, aber deaktiviert.

### Veröffentlichen über ein Asset {#publishing-from-an-asset}

Sie können ein Asset manuell veröffentlichen, solange sich dieses Asset im synchronisierten Dynamic Media Classic-Ordner befindet.

>[!NOTE]
>
>Wenn sich das Asset nicht im synchronisierten Ordner von Dynamic Media Classic befindet, ist der Link zu **[!UICONTROL Auf Dynamic Media Classic veröffentlichen]** nicht verfügbar.

**So veröffentlichen Sie in Dynamic Media Classic direkt über ein digitales Asset**:

1. Klicken Sie in AEM auf **[!UICONTROL Digitale Assets]**, um auf den Digital Asset Manager zuzugreifen.

1. Doppelklicken Sie, um ein Asset zu öffnen.

1. Wählen Sie im Bereich &quot;Asset-Details&quot;die Option **[!UICONTROL In Dynamic Media Classic veröffentlichen]**.

   ![screen_shot_2012-02-22at34828pm](assets/screen_shot_2012-02-22at34828pm.png)

1. Der Link ändert sich zu **[!UICONTROL Wird veröffentlicht ...]** und dann zu **[!UICONTROL Veröffentlicht]**. Gehen Sie zu Dynamic Media Classic und bestätigen Sie, dass das Asset verfügbar ist.

   >[!NOTE]
   >
   >Wenn das Asset nicht ordnungsgemäß in Dynamic Media Classic veröffentlicht wird, ändert sich der Link in **[!UICONTROL Veröffentlichung fehlgeschlagen]**. Wenn das Asset bereits in Dynamic Media Classic veröffentlicht wurde, lautet der Link **[!UICONTROL Nach Dynamic Media Classic erneut veröffentlichen]**. Durch die Veröffentlichung können Sie Änderungen an einem Asset in AEM vornehmen und erneut veröffentlichen.

### Veröffentlichen von Assets von außerhalb des CQ-Zielgruppe-Ordners {#publishing-assets-from-outside-the-cq-target-folder}

Adobe empfiehlt, dass Sie Assets in Dynamic Media Classic nur aus Assets im Ordner &quot;Dynamic Media Classic Zielgruppe&quot;veröffentlichen. Wenn Sie jedoch Assets aus einem Ordner außerhalb des Ordners &quot;Zielgruppe&quot;hochladen müssen, können Sie dies dennoch tun, indem Sie sie in den Ordner *ad-hoc* unter Dynamic Media Classic hochladen.

Hierzu konfigurieren Sie die Cloud-Konfiguration für die Seite, auf der das Asset angezeigt werden soll. Anschließend fügen Sie der Seite eine Dynamic Media Classic-Komponente hinzu und ziehen ein Asset per Drag &amp; Drop in die Komponente. Nachdem die Seiteneigenschaften für diese Seite festgelegt wurden, wird ein Link **[!UICONTROL In Dynamic Media Classic veröffentlichen]** angezeigt, der beim Hochladen in Dynamic Media Classic durch ausgewählte Trigger angezeigt wird.

>[!NOTE]
>
>Assets, die sich im Ad-hoc-Ordner befinden, werden nicht im Dynamic Media Classic-Inhaltsbrowser angezeigt.

**So veröffentlichen Sie außerhalb des CQ-Zielordners befindliche Assets**:

1. Klicken Sie in der klassischen Benutzeroberfläche AEM auf **[!UICONTROL Websites]** und navigieren Sie zu der Webseite, der Sie ein digitales Asset hinzufügen möchten, das noch nicht in Dynamic Media Classic veröffentlicht wurde. (Es gelten normale Seitenübernahmeregeln.)

1. Klicken Sie im Sidekick auf das Symbol **[!UICONTROL Seite]** und dann auf **[!UICONTROL Seiteneigenschaften]**.

1. Klicken Sie auf **[!UICONTROL Cloud Services] > [!UICONTROL Hinzufügen Dienste] > [!UICONTROL Dynamic Media Classic (Scene7)]**.
1. Wählen Sie in der Dropdown-Liste Adobe Dynamic Media Classic die gewünschte Konfiguration und klicken Sie dann auf **[!UICONTROL OK]**.

   ![chlimage_1-77](assets/chlimage_1-77.png)

1. Fügen Sie auf der Webseite der gewünschten Position auf der Seite eine Dynamic Media Classic-Komponente (Scene7) hinzu.
1. Ziehen Sie in der Inhaltssuche ein digitales Asset zur Komponente. Es wird ein Link zu **[!UICONTROL Überprüfen Sie den Dynamic Media Classic-Veröffentlichungsstatus]** angezeigt.

   >[!NOTE]
   >
   >Wenn sich das digitale Asset im Ordner &quot;CQ-Zielgruppe&quot;befindet, wird kein Link zu **[!UICONTROL Dynamic Media Classic-Veröffentlichungsstatus überprüfen]** angezeigt. Die Assets werden einfach in der Komponente platziert.

   ![chlimage_1-78](assets/chlimage_1-78.png)

1. Klicken Sie auf **[!UICONTROL Überprüfen Sie den Dynamic Media Classic-Veröffentlichungsstatus]**. Wenn das Asset nicht veröffentlicht wird, veröffentlicht AEM das Asset in Dynamic Media Classic. Nach dem Upload befindet sich das Asset im Ad-hoc-Ordner. Der Ad-hoc-Ordner befindet sich standardmäßig im Ordner `name_of_the_company/CQ5_adhoc`. Sie können dies [bei Bedarf konfigurieren](#configuringtheadhocfolder).

   >[!NOTE]
   >
   >Wenn sich das Asset nicht in einem synchronisierten Dynamic Media Classic-Ordner befindet und keine Dynamic Media Classic-Cloud-Konfiguration mit der aktuellen Seite verknüpft ist, schlägt der Upload fehl.

## Dynamic Media Classic (Scene7)-Komponenten {#scene-components}

Die folgenden Dynamic Media Classic-Komponenten sind in AEM verfügbar:

* Zoom
* Flyout (Zoom)
* Bildvorlage
* Bild
* Video

>[!NOTE]
>
>Diese Komponenten sind nicht standardmäßig verfügbar und müssen vor der Verwendung im **[!UICONTROL Design]**-Modus ausgewählt werden.

Nachdem sie im **[!UICONTROL Design]**-Modus verfügbar gemacht wurden, können Sie die Komponenten wie jede andere AEM Ihrer Seite hinzufügen. Assets, die noch nicht in Dynamic Media Classic veröffentlicht wurden, werden in Dynamic Media Classic veröffentlicht, wenn sie sich in einem synchronisierten Ordner, auf einer Seite oder in einer Dynamic Media Classic-Cloud-Konfiguration befinden.

### Hinweis zum Lebenszyklusende von Flash-Viewern {#flash-viewers-end-of-life-notice}

Ab dem 31. Januar 2017 hat Adobe Dynamic Media Classic offiziell die Unterstützung für die Flash-Viewer-Plattform eingestellt.

Weitere Informationen zu dieser wichtigen Änderung finden Sie unter [FAQs zum Ende der Lebensdauer des Flashs](https://docs.adobe.com/content/docs/en/aem/6-1/administer/integration/marketing-cloud/scene7/flash-eol.html).

### Hinzufügen einer Dynamic Media Classic-Komponente zu einer Seite {#adding-a-scene-component-to-a-page}

Das Hinzufügen einer Dynamic Media Classic-Komponente zu einer Seite entspricht dem Hinzufügen einer Komponente zu einer beliebigen Seite. Die Komponenten von Dynamic Media Classic werden in den folgenden Abschnitten ausführlich beschrieben.

**So fügen Sie einer Seite der klassischen Benutzeroberfläche** eine Dynamic Media Classic-Komponente/einen Viewer hinzu:

1. Öffnen Sie in AEM die Seite, auf der Sie die Dynamic Media Classic-Komponente hinzufügen möchten.

1. Wenn keine Dynamic Media Classic-Komponenten verfügbar sind, klicken Sie auf das Lineal im Sidekick, um in den Modus **[!UICONTROL Design]** zu wechseln, klicken Sie auf **[!UICONTROL Bearbeiten]**-Parsys und wählen Sie alle Komponenten **[!UICONTROL Dynamic Media Classic]** aus, um sie verfügbar zu machen.

1. Kehren Sie zum Modus **[!UICONTROL Bearbeiten]** zurück, indem Sie auf den Stift im Sidekick klicken.

1. Ziehen Sie eine Komponente aus der Gruppe **[!UICONTROL Dynamic Media Classic]** im Sidekick auf die Seite an der gewünschten Position.

1. Klicken Sie auf **[!UICONTROL Bearbeiten]**, um die Komponente zu öffnen.

1. Bearbeiten Sie die Komponente bei Bedarf und klicken Sie auf **[!UICONTROL OK]**, um die Änderungen zu speichern.

### Hinzufügen von interaktiven Anzeigeerlebnissen zu einer dynamischen Website {#adding-interactive-viewing-experiences-to-a-responsive-website}

Dynamisches Design für Ihre Assets bedeutet, dass Ihre Assets in Abhängigkeit ihrer Anzeigeposition angepasst werden. Bei reaktionsfähigem Design werden dieselben Assets effektiv auf mehreren Geräten angezeigt.

**So fügen Sie ein interaktives Anzeigeerlebnis zu einer dynamischen Website auf der klassischen Benutzeroberfläche hinzu**:

1. Melden Sie sich bei AEM an und stellen Sie sicher, dass Sie über [konfigurierte Adobe Dynamic Media Classic-Cloud Services](/help/sites-administering/scene7.md#configuring-scene-integration) verfügen und dass Dynamic Media Classic-Komponenten verfügbar sind.

   >[!NOTE]
   >
   >Wenn die WCM-Komponenten von Dynamic Media Classic nicht verfügbar sind, stellen Sie sicher, dass Sie sie im Modus **[!UICONTROL Design] aktivieren.

1. Ziehen Sie auf einer Website mit aktivierten Dynamic Media Classic-Komponenten einen **[!UICONTROL Image]**-Viewer auf die Seite.
1. Bearbeiten Sie die Komponente und passen Sie die Haltepunkte auf der Registerkarte **[!UICONTROL Dynamic Media Classic Settings]** an.

   ![chlimage_1-79](assets/chlimage_1-79.png)

1. Bestätigen Sie, dass die Größe der Viewer dynamisch geändert wird und dass alle Interaktionen für Desktopcomputer, Tablets und Mobilgeräte optimiert sind.

### Allgemeine Einstellungen für alle Dynamic Media Classic-Komponenten {#settings-common-to-all-scene-components}

Obwohl die Konfigurationsoptionen unterschiedlich sind, gelten für alle Dynamic Media Classic-Komponenten folgende gemeinsame Optionen:

* **[!UICONTROL Dateiverweis]**: Navigieren Sie zu einer Datei, die Sie referenzieren möchten. Der Dateiverweis zeigt die Asset-URL und nicht unbedingt die vollständige Dynamic Media Classic-URL einschließlich der URL-Befehle und -Parameter. Sie können in diesem Feld keine Dynamic Media Classic-URL-Befehle und -Parameter hinzufügen. Sie müssen über die entsprechende Funktionalität in der Komponente hinzugefügt werden.
* **[!UICONTROL Breite]**: Hiermit kann die Breite angepasst werden.
* **[!UICONTROL Höhe]**: Hiermit kann die Höhe angepasst werden.

Sie legen diese Konfigurationsoptionen fest, indem Sie Dublette auf eine Dynamic Media Classic-Komponente klicken, z. B. wenn Sie eine **[!UICONTROL Zoom]**-Komponente öffnen:

![chlimage_1-80](assets/chlimage_1-80.png)

### Zoom {#zoom}

Die HTML5 Zoom-Komponente zeigt ein größeres Bild an, wenn Sie die Taste „+“ drücken.

Das Asset verfügt unten über Zoomwerkzeuge. Klicken Sie auf **[!UICONTROL +]** zum Vergrößern. Klicken Sie auf **[!UICONTROL -]** zum Verkleinern. Durch Klicken auf **[!UICONTROL x]** oder den Zurücksetzen-Zoom-Pfeil wird das Bild wieder in die ursprüngliche Größe des importierten Bildes zurückgesetzt. Klicken Sie auf die diagonalen Pfeile, um es im Vollbild anzuzeigen. Klicken Sie auf **[!UICONTROL Bearbeiten]**, um die Komponente zu konfigurieren. Mit dieser Komponente können Sie [Einstellungen konfigurieren, die allen Dynamic Media Classic-Komponenten gemein sind](#settings-common-to-all-scene-components).

![](do-not-localize/chlimage_1-5.png)

### Flyout {#flyout}

In der HTML5 Flyout-Komponente wird das Asset als geteilter Bildschirm angezeigt. Links wird das Asset in der angegebenen Größe angezeigt, rechts wird der Zoomteil angezeigt. Klicken Sie auf **[!UICONTROL Bearbeiten]**, um die Komponente zu konfigurieren. Mit dieser Komponente können Sie [Einstellungen konfigurieren, die allen Dynamic Media Classic-Komponenten gemein sind](/help/sites-administering/scene7.md#settingscommontoalldynamicmediaclassiccomponents).

>[!NOTE]
>
>Wenn die Flyout-Komponente eine benutzerdefinierte Größe aufweist, wird diese benutzerdefinierte Größe verwendet und die dynamische Einrichtung der Komponente ist deaktiviert.
>
>Wenn Ihre Flyout-Komponente die Standardgröße verwendet, wie in der Ansicht [!UICONTROL Design] festgelegt, wird die Standardgröße verwendet und die Komponente wird entsprechend der Seitenlayoutgröße mit aktiviertem responsiven Setup der Komponente angepasst. Beachten Sie jedoch, dass es eine Beschränkung für das reaktionsfähige Setup der Komponente gibt. Beim Verwenden der Flyout-Komponente mit dynamischer Einrichtung sollten Sie sie nicht mit vollständiger Seitendehnung verwenden. Andernfalls kann der Flyout über den rechten Rand der Seite hinausgehen.

![chlimage_1-81](assets/chlimage_1-81.png)

### Bild {#image}

Mit der Komponente &quot;Dynamic Media Classic Image&quot;können Sie Ihren Bildern Dynamic Media Classic-Funktionen hinzufügen, z. B. Dynamic Media Classic-Modifikatoren, Bild- oder Viewer-Vorgaben und Scharfzeichnen. Die Dynamic Media Classic-Bildkomponente ähnelt anderen Bildkomponenten in AEM mit speziellen Dynamic Media Classic-Funktionen. In diesem Beispiel wurde auf das Bild der URL-Modifikator Dynamic Media Classic angewendet, `&op_invert=1`.

![](do-not-localize/chlimage_1-6.png)

**[!UICONTROL Titel, Alt-Text]**  - Fügen Sie auf der Registerkarte &quot;  Erweitert&quot;dem Bild einen Titel und alternativem Text für Benutzer hinzu, die Grafiken deaktiviert haben.

**[!UICONTROL URL, Öffnen in]** : Sie können ein Asset vom zum Öffnen eines Links festlegen. Legen Sie die Optionen **[!UICONTROL URL]** und **[!UICONTROL In]** öffnen fest, um anzugeben, ob die Datei im selben Fenster oder in einem neuen Fenster geöffnet werden soll.

![chlimage_1-82](assets/chlimage_1-82.png)

**[!UICONTROL Viewer-Vorgabe]** : Wählen Sie im Dropdown-Menü eine vorhandene Viewer-Vorgabe aus. Wenn die gewünschte Viewer-Vorgabe nicht sichtbar ist, müssen Sie sie möglicherweise sichtbar machen. Siehe [Verwalten von Viewer-Vorgaben](/help/assets/managing-viewer-presets.md). Es ist nicht möglich, eine Viewer-Vorgabe auszuwählen, wenn Sie eine Bildvorgabe verwenden, und umgekehrt.

**[!UICONTROL Dynamic Media Classic-Konfiguration]** : Wählen Sie die Dynamic Media Classic-Konfiguration aus, die Sie zum Abrufen aktiver Bildvorgaben aus dem Scene7 Publishing System verwenden möchten.

**[!UICONTROL Bildvorgabe]** : Wählen Sie eine vorhandene Bildvorgabe aus dem Dropdown-Menü. Wenn die gewünschte Bildvorgabe nicht sichtbar ist, müssen Sie sie möglicherweise sichtbar machen. Siehe [Verwalten von Bildvorgaben](/help/assets/managing-image-presets.md). Es ist nicht möglich, eine Viewer-Vorgabe auszuwählen, wenn Sie eine Bildvorgabe verwenden, und umgekehrt.

**[!UICONTROL Ausgabeformat]** : Wählen Sie das Ausgabeformat des Bilds, z. B. jpeg, aus. In Abhängigkeit des von Ihnen ausgewählten Ausgabeformats stehen Ihnen möglicherweise zusätzliche Konfigurationsoptionen zur Verfügung. Siehe [Verwalten von Bildvorgaben](/help/assets/managing-image-presets.md).

**[!UICONTROL Scharfzeichnen]** : Wählen Sie aus, wie das Bild scharfgezeichnet werden soll. Das Scharfzeichnen wird unter [*Adobe Dynamic Media Classic Image Quality and Sharpening Best Practices*](/help/assets/assets/sharpening_images.pdf) ausführlich erläutert.

**[!UICONTROL URL-Modifikatoren]** : Sie können Bildeffekte ändern, indem Sie zusätzliche Dynamic Media Classic-Bildbefehle bereitstellen. Diese werden unter [Verwalten von Bildvorgaben](/help/assets/managing-image-presets.md) und [Befehlsreferenz](https://docs.adobe.com/content/help/de-DE/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference.html) beschrieben.

**[!UICONTROL Haltepunkte]** : Wenn Ihre Website responsiv ist, sollten Sie die Haltepunkte anpassen. Haltepunkte müssen durch Kommas `,` getrennt werden.

### Bildvorlage {#image-template}

[Dynamic Media Classic-](https://help.adobe.com/en_US/scene7/using/WS60B68844-9054-4099-BF69-3DC998A04D3C.html) Bildvorlagen sind Photoshop-Inhalte mit Ebenen, die in Dynamic Media Classic importiert wurden, wobei Inhalt und Eigenschaften auf Variabilität parametrisiert wurden. Mit der Komponente **[!UICONTROL Bildvorlage]** können Sie Bilder importieren und den Text in AEM dynamisch ändern. Zusätzlich können Sie die Komponente **[!UICONTROL Bildvorlage]** dahingehend konfigurieren, dass sie Werte aus dem Clientkontext übernimmt, damit das Bild jedem Benutzer personalisiert angezeigt wird.

Klicken Sie auf **[!UICONTROL Bearbeiten]**, um die Komponente zu konfigurieren. Sie können [Einstellungen konfigurieren, die allen Dynamic Media Classic-Komponenten gemeinsam sind](/help/sites-administering/scene7.md#settingscommontoalldynamicmediaclassicscomponents) sowie andere in diesem Abschnitt beschriebene Einstellungen.

![chlimage_1-83](assets/chlimage_1-83.png)

**[!UICONTROL Dateiverweis, Breite, Höhe]**  - Siehe Einstellungen, die allen Dynamic Media Classic-Komponenten gemeinsam sind.

>[!NOTE]
>
>Dynamic Media Classic-URL-Befehle und -Parameter können der Dateiverweis-URL nicht direkt hinzugefügt werden. Sie können nur auf der Komponenten-Benutzeroberfläche im Bedienfeld **[!UICONTROL Parameter]** definiert werden.

**[!UICONTROL Titel, Alt-]** TextFügen Sie in der  [!UICONTROL Dynamic Media Classic-] Bildvorlage dem Bild und dem Alternativtext einen Titel für Benutzer hinzu, die Grafiken deaktiviert haben.

**[!UICONTROL URL, Öffnen]** inSie können ein Asset so einstellen, dass ein Link geöffnet wird. Legen Sie die **[!UICONTROL URL]** fest. Geben Sie in **[!UICONTROL Öffnen in]** an, ob der Link im selben oder einem neuen Fenster geöffnet werden soll.

![chlimage_1-84](assets/chlimage_1-84.png)

**[!UICONTROL Parameter]** PanelBeim Importieren eines Bilds werden die Parameter mit Informationen aus dem Bild vorausgefüllt. Wenn kein Inhalt vorhanden ist, der dynamisch geändert werden kann, ist dieses Fenster leer.

![chlimage_1-85](assets/chlimage_1-85.png)

#### Dynamisches Ändern von Text {#changing-text-dynamically}

Geben Sie zum dynamischen Ändern des Texts neuen Text in die Felder ein und klicken Sie auf **[!UICONTROL OK]**. In diesem Beispiel lautet der **[!UICONTROL Preis]** 50 $ und der Versand kostet 0,99 $.

![chlimage_1-86](assets/chlimage_1-86.png)

Der Text im Bild ändert sich. Sie können den Text auf den ursprünglichen Wert zurücksetzen, indem Sie neben dem Feld auf **[!UICONTROL Zurücksetzen]** klicken.

![chlimage_1-87](assets/chlimage_1-87.png)

#### Ändern von Text zum Berücksichtigen des Werts eines Clientkontextwerts {#changing-text-to-reflect-the-value-of-a-client-context-value}

Um ein Feld mit einem Clientkontextwert zu verknüpfen, klicken Sie auf **[!UICONTROL Wählen Sie]**, um das Client-Kontextmenü zu öffnen, wählen Sie den Clientkontext aus und klicken Sie auf **[!UICONTROL OK]**. In diesem Beispiel ändert sich der Name auf Grundlage der Verknüpfung des Namens mit dem formatierten Namen im Profil.

![chlimage_1-88](assets/chlimage_1-88.png)

Der Text berücksichtigt den Namen des aktuell angemeldeten Benutzers. Sie können den Text auf den ursprünglichen Wert zurücksetzen, indem Sie neben dem Feld auf **[!UICONTROL Zurücksetzen]** klicken.

![chlimage_1-89](assets/chlimage_1-89.png)

#### Erstellen einer Dynamic Media Classic-Bildvorlage als Link {#making-the-scene-image-template-a-link}

**So erstellen Sie eine Verknüpfung** mit der Dynamic Media Classic-Bildvorlage:

1. Klicken Sie auf der Seite mit der Dynamic Media Classic-Bildvorlagenkomponente auf **[!UICONTROL Bearbeiten]**.
1. Geben Sie im Feld **[!UICONTROL URL]** die URL ein, zu der Benutzer wechseln, wenn sie auf das Bild klicken. Wählen Sie im Feld **[!UICONTROL Öffnen in]** aus, ob das Ziel (in einem neuen oder im selben Fenster) geöffnet werden soll.

   ![chlimage_1-90](assets/chlimage_1-90.png)

1. Klicken Sie auf **[!UICONTROL OK]**.

### Komponente „Video“{#video-component}

Die Komponente Dynamic Media Classic **[!UICONTROL Video]** (verfügbar im Abschnitt &quot;Dynamic Media Classic&quot;des Sidekick) verwendet Geräte- und Bandbreitenerkennung, um das richtige Video für jeden Bildschirm bereitzustellen. Bei dieser Komponente handelt es sich um einen HTML5-Video-Player. Es ist ein einzelner Viewer, der kanalübergreifend verwendet werden kann.

Er kann für adaptive Videosets, ein einzelnes MP4-Video oder ein einzelnes F4V-Video verwendet werden.

Weitere Informationen zur Funktionsweise von Videos bei der Dynamic Media Classic-Integration finden Sie unter [Video](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md). Sehen Sie außerdem, wie die Komponente [Dynamic Media Classic video **mit der Komponente** video **](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md) verglichen wird.**

![chlimage_1-91](assets/chlimage_1-91.png)

### Bekannte Einschränkungen für die Videokomponente {#known-limitations-for-the-video-component}

Adobe DAM und WCM zeigen, ob ein Mastervideo hochgeladen wurde. Sie zeigen diese Proxy-Assets nicht an:

* Dynamic Media Classic-kodierte Darstellungen
* Adaptive Dynamic Media Classic-Videosets

Wenn Sie ein adaptives Videoset mit der Dynamic Media Classic-Videokomponente verwenden, müssen Sie die Größe der Komponente an die Abmessungen des Videos anpassen.

## Dynamic Media Classic Content Browser {#scene-content-browser}

Mit dem Dynamic Media Classic-Inhaltsbrowser können Sie Inhalte aus Dynamic Media Classic direkt in AEM Ansicht verwenden. Um auf den Inhaltsbrowser zuzugreifen, wählen Sie in der Inhaltssuche in der touchoptimierten Benutzeroberfläche die Option **[!UICONTROL Dynamic Media Classic]** oder in der klassischen Benutzeroberfläche das Symbol **[!UICONTROL S7]** aus. Die Funktionalität ist zwischen den beiden Benutzeroberflächen identisch.

Wenn Sie über mehrere Konfigurationen verfügen, zeigt AEM standardmäßig die [Standardkonfiguration](/help/sites-administering/scene7.md#configuring-a-default-configuration) an. Sie können verschiedene Konfigurationen direkt im Dynamic Media Classic-Inhaltsbrowser im Dropdown-Menü auswählen.

>[!NOTE]
>
>* Assets, die sich im Ad-hoc-Ordner befinden, werden nicht im Dynamic Media Classic-Inhaltsbrowser angezeigt.
>* Wenn [Sichere Vorschau aktiviert ist, werden veröffentlichte und unveröffentlichte Assets in Dynamic Media Classic im Dynamic Media Classic-Inhaltsbrowser angezeigt.](/help/sites-administering/scene7.md#configuring-the-state-published-unpublished-of-assets-pushed-to-scene)
>* Wenn Sie im Inhaltsbrowser weder das Symbol **[!UICONTROL Dynamic Media Classic]** noch das Symbol **[!UICONTROL S7]** als Option sehen, müssen Sie [Dynamic Media Classic für die Verwendung mit AEM](/help/sites-administering/scene7.md) konfigurieren.

   >
   >
* Für Videos unterstützt der Dynamic Media Classic-Inhaltsbrowser:
   >
   >
* Adaptive Videosets: Container von allen für die bildschirmübergreifende optimierte Wiedergabe erforderlichen Videoausgabeformaten
>* Einzelnes MP4-Video
>* Einzelnes F4V-Video


### Durchsuchen von Inhalt auf der klassischen Benutzeroberfläche {#browsing-content-in-the-classic-ui}

Durchsuchen Sie Inhalte in Dynamic Media Classic, indem Sie auf die Registerkarte **[!UICONTROL S7]** klicken.

Sie können die Konfiguration, auf die Sie zugreifen, ändern, indem Sie die Konfiguration auswählen. Die Ordner ändern sich je nach ausgewählter Konfiguration.

![chlimage_1-92](assets/chlimage_1-92.png)

Wie mit der Inhaltssuche für Assets können Sie nach Assets suchen und Ergebnisse filtern. Im Gegensatz zur Asset-Suche **[!UICONTROL beginnt]** der Dateiname jedoch beim Eingeben eines Keywords auf der Registerkarte *S7* mit dem von Ihnen eingegebenen String, anstatt dass das Keyword im Dateinamen *enthalten* ist.

Standardmäßig werden Assets nach Dateiname angezeigt. Sie können Ergebnisse auch nach Asset-Typ filtern.

>[!NOTE]
>
>Für Videos unterstützt der Dynamic Media Classic Content Browser von WCM Folgendes:
>
>* Adaptive Videosets: Container von allen für die bildschirmübergreifende optimierte Wiedergabe erforderlichen Videoausgabeformaten
>* Einzelnes MP4-Video
>* Einzelnes F4V-Video

>



### Suchen nach Dynamic Media Classic-Assets mit dem Inhaltsbrowser {#searching-for-scene-assets-with-the-content-browser}

Die Suche nach Dynamic Media Classic-Assets funktioniert ähnlich wie die Suche nach AEM Assets. Bei der Suche sehen Sie jedoch eine Remote-Ansicht der Assets im Dynamic Media Classic-System, anstatt sie direkt in AEM zu importieren.

Sie können die klassische oder Touch-optimierte Benutzeroberfläche verwenden, um Assets anzuzeigen und nach ihnen zu suchen. In Abhängigkeit von der Oberfläche unterscheidet sich die Art und Weise der Suche etwas.

Wenn Sie auf einer der Benutzeroberflächen suchen, können Sie nach den folgenden Kriterien filtern (wird hier in der Touch-optimierten Benutzeroberfläche gezeigt):

**[!UICONTROL Suchbegriffe]**  eingeben - Sie können Assets nach Namen suchen. Bei der Suche entsprechen die von Ihnen eingegebenen Keywords dem Beginn des Dateinamens. Zum Beispiel führt die Eingabe des Worts „schwimmen“ dazu, dass nach Asset-Dateinamen gesucht wird, die mit diesen Buchstaben in dieser Reihenfolge beginnen. Drücken Sie die Eingabetaste, nachdem Sie den Begriff eingegeben haben, um nach dem Asset zu suchen.

![chlimage_1-93](assets/chlimage_1-93.png)

**[!UICONTROL Ordner/Pfad]**  - Der Name des angezeigten Ordners hängt von der ausgewählten Konfiguration ab. Sie können niedrigere Ebenen anzeigen, indem Sie auf das Ordnersymbol klicken, einen Unterordner auswählen und dann auf das Häkchen klicken, um ihn auszuwählen.

Wenn Sie ein Keyword eingeben und einen Ordner auswählen, durchsucht AEM diesen Ordner und die zugehörigen Unterordner. Wenn Sie jedoch bei der Suche keine Keywords eingeben, wird durch die Auswahl des Ordners das Asset nur in diesem Ordner angezeigt und nicht in Unterordnern.

Standardmäßig durchsucht AEM den ausgewählten Ordner und alle Unterordner.

![chlimage_1-94](assets/chlimage_1-94.png)

**[!UICONTROL Typ des]** AssetsWählen Sie Dynamic Media Classic aus, um Dynamic Media Classic-Inhalte zu durchsuchen. Diese Option ist nur verfügbar, wenn Sie Dynamic Media Classic bereits konfiguriert haben.

![chlimage_1-95](assets/chlimage_1-95.png)

**** ConfigurationWenn Sie mehr als eine Dynamic Media Classic-Konfiguration in  [!UICONTROL Cloud Services] definiert haben, können Sie diese hier auswählen. Der Ordner ändert sich anhand der von Ihnen ausgewählten Konfiguration.

![chlimage_1-96](assets/chlimage_1-96.png)

**[!UICONTROL Asset-]** TypIm Dynamic Media Classic-Browser können Sie die Ergebnisse filtern, um Folgendes einzuschließen: Bilder, Vorlagen, Videos und adaptive Videosets. Wenn Sie keinen Asset-Typ auswählen, durchsucht AEM standardmäßig alle Asset-Typen.

![chlimage_1-97](assets/chlimage_1-97.png)

>[!NOTE]
>
>* Beim Durchsuchen eines Videos suchen Sie nach einem einzelnen Ausgabeformat. Die Ergebnisse geben die ursprüngliche Darstellung (nur &amp;ast;.mp4) und die kodierte Darstellung zurück.
>* Beim Durchsuchen eines adaptiven Videosets suchen Sie den Ordner und alle Unterordner, allerdings nur, wenn Sie der Suche einen Suchbegriff hinzugefügt haben. Wenn Sie kein Keyword hinzugefügt haben, durchsucht AEM nicht die Unterordner.

>



**[!UICONTROL Veröffentlichungsstatus]** Sie können nach Assets basierend auf dem Veröffentlichungsstatus filtern:  [!UICONTROL Veröffentlichung ] oder  [!UICONTROL Veröffentlichung rückgängig gemacht]. Wenn Sie keinen [!UICONTROL Veröffentlichungsstatus] auswählen, durchsucht AEM standardmäßig alle Veröffentlichungsstatus.

![chlimage_1-98](assets/chlimage_1-98.png)

