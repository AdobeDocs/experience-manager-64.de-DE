---
title: Hinzufügen von Dynamic Media Classic-Funktionen zu Ihrer Seite
seo-title: Hinzufügen von Dynamic Media Classic-Funktionen zu Ihrer Seite
description: Adobe Dynamic Media Classic ist eine gehostete Lösung für die Verwaltung, Erweiterung, Veröffentlichung und Bereitstellung von Rich-Media-Assets für Web-, Mobile-, E-Mail- und Internet-verbundene Anzeigen und Drucken.
seo-description: Adobe Dynamic Media Classic ist eine gehostete Lösung für die Verwaltung, Erweiterung, Veröffentlichung und Bereitstellung von Rich-Media-Assets für Web-, Mobile-, E-Mail- und Internet-verbundene Anzeigen und Drucken.
uuid: 66b9c150-c482-4a41-9772-fa39c135802c
contentOwner: Alva Ware-Bevacqui
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 9ba95dce-a801-4a36-8798-45d295371b1b
exl-id: 93921d23-a2bf-43b6-b002-58a7482b22b0
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '3381'
ht-degree: 32%

---

# Hinzufügen von Dynamic Media Classic-Funktionen zu Ihrer Seite{#adding-scene-features-to-your-page}

Adobe Dynamic Media Classic ist eine gehostete Lösung für die Verwaltung, Erweiterung, Veröffentlichung und Bereitstellung von Rich-Media-Assets für Web-, Mobile-, E-Mail- und Internet-verbundene Anzeigen und Drucken.

Sie können AEM Assets anzeigen, die in Dynamic Media Classic in verschiedenen Viewern veröffentlicht wurden:

* Zoom
* Flyout
* Video
* Bildvorlage
* Bild

Sie können digitale Assets direkt aus AEM in Dynamic Media Classic veröffentlichen und digitale Assets aus Dynamic Media Classic in AEM veröffentlichen.

In diesem Abschnitt wird beschrieben, wie Sie digitale Assets von AEM in Dynamic Media Classic veröffentlichen und umgekehrt. Die Viewer werden auch detailliert beschrieben. Informationen zum Konfigurieren von AEM für Dynamic Media Classic finden Sie unter [Integrieren von Dynamic Media Classic mit AEM](/help/sites-administering/scene7.md).

Siehe auch [Hinzufügen von Imagemaps](/help/assets/image-maps.md).

Weitere Informationen über die Arbeit mit Videokomponenten mit AEM finden Sie unter:

* [Video](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md)

>[!NOTE]
>
>Wenn Dynamic Media Classic-Assets nicht ordnungsgemäß angezeigt werden, stellen Sie sicher, dass Dynamic Media [disabled](/help/assets/config-dynamic.md#disabling-dynamic-media) ist, und aktualisieren Sie dann die Seite.

## Manuelles Veröffentlichen in Dynamic Media Classic über Assets {#manually-publishing-to-scene-from-assets}

Sie können digitale Assets in Dynamic Media Classic entweder über die Konsole &quot;Assets&quot;in der klassischen Benutzeroberfläche oder direkt über das Asset veröffentlichen.

>[!NOTE]
>
>AEM veröffentlicht asynchron in Dynamic Media Classic. Wenn Sie auf **[!UICONTROL Publish]** klicken, kann es mehrere Sekunden dauern, bis Ihr Asset in Dynamic Media Classic veröffentlicht wird.


### Veröffentlichen über die Asset-Konsole {#publishing-from-the-assets-console}

So veröffentlichen Sie in Dynamic Media Classic über die Konsole &quot;Assets&quot;, wenn sich die Assets in einem Dynamic Media Classic-Zielordner befinden:

1. Klicken Sie in der AEM klassischen Benutzeroberfläche auf **[!UICONTROL Digitale Assets]** , um auf den Digital Asset Manager zuzugreifen.

1. Wählen Sie das Asset (oder die Assets) oder den Ordner aus dem Zielordner aus, den Sie in Dynamic Media Classic veröffentlichen möchten, klicken Sie mit der rechten Maustaste darauf und wählen Sie **[!UICONTROL In Dynamic Media Classic veröffentlichen]** aus. Alternativ können Sie **[!UICONTROL In Dynamic Media Classic veröffentlichen]** aus dem Menü **[!UICONTROL Tools]** auswählen.

   ![chlimage_1-76](assets/chlimage_1-76.png)

1. Gehen Sie zu Dynamic Media Classic und überprüfen Sie, ob die Assets verfügbar sind.

   >[!NOTE]
   >
   >Wenn sich die Assets nicht in einem synchronisierten Ordner von Dynamic Media Classic befinden, ist **[!UICONTROL In Dynamic Media Classic veröffentlichen]** in beiden Menüs sichtbar, aber deaktiviert.

### Veröffentlichen über ein Asset {#publishing-from-an-asset}

Sie können ein Asset manuell veröffentlichen, solange sich dieses Asset im synchronisierten Ordner von Dynamic Media Classic befindet.

>[!NOTE]
>
>Wenn sich das Asset nicht im synchronisierten Ordner von Dynamic Media Classic befindet, ist der Link zu **[!UICONTROL In Dynamic Media Classic veröffentlichen]** nicht verfügbar.

**So veröffentlichen Sie direkt über ein digitales Asset** in Dynamic Media Classic:

1. Klicken Sie in AEM auf **[!UICONTROL Digitale Assets]**, um auf den Digital Asset Manager zuzugreifen.

1. Doppelklicken Sie, um ein Asset zu öffnen.

1. Wählen Sie im Asset-Detailbereich **[!UICONTROL In Dynamic Media Classic veröffentlichen]** aus.

   ![screen_shot_2012-02-22at34828pm](assets/screen_shot_2012-02-22at34828pm.png)

1. Der Link ändert sich zu **[!UICONTROL Wird veröffentlicht ...]** und dann zu **[!UICONTROL Veröffentlicht]**. Gehen Sie zu Dynamic Media Classic und überprüfen Sie, ob das Asset verfügbar ist.

   >[!NOTE]
   >
   >Wenn das Asset nicht ordnungsgemäß in Dynamic Media Classic veröffentlicht wird, ändert sich der Link in **[!UICONTROL Veröffentlichung fehlgeschlagen]**. Wenn das Asset bereits in Dynamic Media Classic veröffentlicht wurde, lautet der Link **[!UICONTROL In Dynamic Media Classic erneut veröffentlichen]**. Durch das erneute Veröffentlichen können Sie Änderungen an einem Asset in AEM vornehmen und es erneut veröffentlichen.

### Veröffentlichen von Assets außerhalb des CQ-Zielordners {#publishing-assets-from-outside-the-cq-target-folder}

Adobe empfiehlt, Assets nur aus Assets im Dynamic Media Classic-Zielordner in Dynamic Media Classic zu veröffentlichen. Wenn Sie jedoch Assets aus einem Ordner außerhalb des Zielordners hochladen müssen, können Sie dies dennoch tun, indem Sie sie in einen Ordner *Ad-hoc* unter Dynamic Media Classic hochladen.

Konfigurieren Sie dazu die Cloud-Konfiguration für die Seite, auf der das Asset angezeigt wird. Anschließend fügen Sie der Seite eine Dynamic Media Classic-Komponente hinzu und ziehen ein Asset per Drag-and-Drop auf die Komponente. Nachdem die Seiteneigenschaften für diese Seite festgelegt wurden, wird ein Link **[!UICONTROL In Dynamic Media Classic veröffentlichen]** angezeigt, der beim Hochladen ausgewählter Trigger in Dynamic Media Classic erscheint.

>[!NOTE]
>
>Assets, die sich im Ad-hoc-Ordner befinden, werden nicht im Inhaltsbrowser von Dynamic Media Classic angezeigt.

**So veröffentlichen Sie außerhalb des CQ-Zielordners befindliche Assets**:

1. Klicken Sie in AEM klassischen Benutzeroberfläche auf **[!UICONTROL Websites]** und navigieren Sie zur Webseite, der Sie ein digitales Asset hinzufügen möchten, das noch nicht in Dynamic Media Classic veröffentlicht wurde. (Es gelten normale Seitenübernahmeregeln.)

1. Klicken Sie im Sidekick auf das Symbol **[!UICONTROL Seite]** und dann auf **[!UICONTROL Seiteneigenschaften]**.

1. Klicken Sie auf **[!UICONTROL Cloud Services] > [!UICONTROL Dienste hinzufügen] > [!UICONTROL Dynamic Media Classic (Scene7)]**.
1. Wählen Sie in der Dropdownliste Adobe Dynamic Media Classic die gewünschte Konfiguration aus und klicken Sie dann auf **[!UICONTROL OK]**.

   ![chlimage_1-77](assets/chlimage_1-77.png)

1. Fügen Sie auf der Webseite eine Dynamic Media Classic (Scene7)-Komponente an der gewünschten Stelle auf der Seite hinzu.
1. Ziehen Sie in der Inhaltssuche ein digitales Asset zur Komponente. Es wird ein Link zu **[!UICONTROL Überprüfen des Dynamic Media Classic-Veröffentlichungsstatus]** angezeigt.

   >[!NOTE]
   >
   >Wenn sich das digitale Asset im CQ-Zielordner befindet, wird kein Link zu **[!UICONTROL Überprüfen des Dynamic Media Classic-Veröffentlichungsstatus]** angezeigt. Die Assets werden einfach in der Komponente platziert.

   ![chlimage_1-78](assets/chlimage_1-78.png)

1. Klicken Sie auf **[!UICONTROL Überprüfen Sie den Dynamic Media Classic-Veröffentlichungsstatus]**. Wenn das Asset nicht veröffentlicht wurde, veröffentlicht AEM das Asset in Dynamic Media Classic. Nach dem Upload befindet sich das Asset im Ad-hoc-Ordner. Standardmäßig befindet sich der Ad-hoc-Ordner im Ordner `name_of_the_company/CQ5_adhoc`. Sie können dies [bei Bedarf konfigurieren](#configuringtheadhocfolder).

   >[!NOTE]
   >
   >Wenn sich das Asset nicht in einem synchronisierten Ordner von Dynamic Media Classic befindet und keine Dynamic Media Classic-Cloud-Konfiguration mit der aktuellen Seite verknüpft ist, schlägt der Upload fehl.

## Dynamic Media Classic (Scene7)-Komponenten {#scene-components}

Die folgenden Dynamic Media Classic-Komponenten sind in AEM verfügbar:

* Zoom
* Flyout (Zoom)
* Bildvorlage
* Bild
* Video

>[!NOTE]
>
>Diese Komponenten sind standardmäßig nicht verfügbar und müssen vor der Verwendung im Modus **[!UICONTROL Design]** ausgewählt werden.

Nachdem sie im Modus **[!UICONTROL Design]** verfügbar gemacht wurden, können Sie die Komponenten wie jede andere AEM Ihrer Seite hinzufügen. Assets, die noch nicht in Dynamic Media Classic veröffentlicht wurden, werden in Dynamic Media Classic veröffentlicht, wenn sie sich in einem synchronisierten Ordner, auf einer Seite oder mit einer Dynamic Media Classic-Cloud-Konfiguration befinden.

### Hinweis zum Ende der Lebensdauer von Flash-Viewern {#flash-viewers-end-of-life-notice}

Ab dem 31. Januar 2017 hat Adobe Dynamic Media Classic offiziell die Unterstützung für die Flash-Viewer-Plattform eingestellt.

### Hinzufügen einer Dynamic Media Classic-Komponente zu einer Seite {#adding-a-scene-component-to-a-page}

Das Hinzufügen einer Dynamic Media Classic-Komponente zu einer Seite entspricht dem Hinzufügen einer Komponente zu einer beliebigen Seite. Dynamic Media Classic-Komponenten werden in den folgenden Abschnitten ausführlich beschrieben.

**So fügen Sie einer Seite in der klassischen Benutzeroberfläche** eine Dynamic Media Classic-Komponente/einen Viewer hinzu:

1. Öffnen Sie in AEM die Seite, auf der Sie die Dynamic Media Classic-Komponente hinzufügen möchten.

1. Wenn keine Dynamic Media Classic-Komponenten verfügbar sind, klicken Sie auf das Lineal im Sidekick, um in den Modus **[!UICONTROL Design]** zu wechseln. Klicken Sie auf **[!UICONTROL Bearbeiten]** parsys und wählen Sie alle Komponenten **[!UICONTROL Dynamic Media Classic]** aus, um sie verfügbar zu machen.

1. Kehren Sie zum Modus **[!UICONTROL Bearbeiten]** zurück, indem Sie im Sidekick auf das Stiftsymbol klicken.

1. Ziehen Sie eine Komponente aus der Gruppe **[!UICONTROL Dynamic Media Classic]** im Sidekick auf die Seite an der gewünschten Position.

1. Klicken Sie auf **[!UICONTROL Bearbeiten]**, um die Komponente zu öffnen.

1. Bearbeiten Sie die Komponente bei Bedarf und klicken Sie auf **[!UICONTROL OK]**, um die Änderungen zu speichern.

### Hinzufügen von interaktiven Anzeigeerlebnissen zu einer dynamischen Website  {#adding-interactive-viewing-experiences-to-a-responsive-website}

Dynamisches Design für Ihre Assets bedeutet, dass Ihre Assets in Abhängigkeit ihrer Anzeigeposition angepasst werden. Responsives Design ermöglicht die effektive Anzeige derselben Assets auf mehreren Geräten.

**So fügen Sie ein interaktives Anzeigeerlebnis zu einer dynamischen Website auf der klassischen Benutzeroberfläche hinzu**:

1. Melden Sie sich bei AEM an und stellen Sie sicher, dass Sie über [konfigurierte Dynamic Media Classic-Cloud Services](/help/sites-administering/scene7.md#configuring-scene-integration) verfügen und dass Dynamic Media Classic-Komponenten verfügbar sind.

   >[!NOTE]
   >
   >Wenn die WCM-Komponenten von Dynamic Media Classic nicht verfügbar sind, stellen Sie sicher, dass Sie sie im Modus **[!UICONTROL Design] aktivieren.

1. Ziehen Sie auf einer Website mit aktivierten Dynamic Media Classic-Komponenten einen Viewer **[!UICONTROL Bild]** auf die Seite.
1. Bearbeiten Sie die Komponente und passen Sie die Haltepunkte auf der Registerkarte **[!UICONTROL Dynamic Media Classic Settings]** an.

   ![chlimage_1-79](assets/chlimage_1-79.png)

1. Bestätigen Sie, dass die Größe der Viewer dynamisch geändert wird und dass alle Interaktionen für Desktopcomputer, Tablets und Mobilgeräte optimiert sind.

### Für alle Dynamic Media Classic-Komponenten gemeinsame Einstellungen {#settings-common-to-all-scene-components}

Obwohl die Konfigurationsoptionen variieren, gelten für alle Dynamic Media Classic-Komponenten folgende gemeinsame Optionen:

* **[!UICONTROL Dateiverweis]**: Navigieren Sie zu einer Datei, die Sie referenzieren möchten. Der Dateiverweis zeigt die Asset-URL und nicht notwendigerweise die vollständige Dynamic Media Classic-URL, einschließlich der URL-Befehle und -Parameter. In diesem Feld können Sie keine Dynamic Media Classic-URL-Befehle und -Parameter hinzufügen. Sie müssen über die entsprechende Funktionalität in der Komponente hinzugefügt werden.
* **[!UICONTROL Breite]**: Hiermit kann die Breite angepasst werden.
* **[!UICONTROL Höhe]**: Hiermit kann die Höhe angepasst werden.

Sie legen diese Konfigurationsoptionen fest, indem Sie auf eine Dynamic Media Classic-Komponente doppelklicken, z. B. beim Öffnen einer Komponente **[!UICONTROL Zoom]**:

![chlimage_1-80](assets/chlimage_1-80.png)

### Zoom {#zoom}

Die HTML5 Zoom-Komponente zeigt ein größeres Bild an, wenn Sie die Taste „+“ drücken.

Das Asset verfügt unten über Zoomwerkzeuge. Klicken Sie auf **[!UICONTROL +]** zum Vergrößern. Klicken Sie auf **[!UICONTROL -]** zum Verkleinern. Wenn Sie auf **[!UICONTROL x]** oder den Pfeil zum Zurücksetzen des Zooms klicken, wird das Bild wieder in die Originalgröße des importierten Bildes versetzt. Klicken Sie auf die diagonalen Pfeile, um es im Vollbild anzuzeigen. Klicken Sie auf **[!UICONTROL Bearbeiten]**, um die Komponente zu konfigurieren. Mit dieser Komponente können Sie [Einstellungen konfigurieren, die für alle Dynamic Media Classic-Komponenten](#settings-common-to-all-scene-components) gelten.

![](do-not-localize/chlimage_1-5.png)

### Flyout {#flyout}

In der HTML5 Flyout-Komponente wird das Asset als geteilter Bildschirm angezeigt. Links wird das Asset in der angegebenen Größe angezeigt, rechts wird der Zoomteil angezeigt. Klicken Sie auf **[!UICONTROL Bearbeiten]**, um die Komponente zu konfigurieren. Mit dieser Komponente können Sie [Einstellungen konfigurieren, die für alle Dynamic Media Classic-Komponenten](/help/sites-administering/scene7.md#settingscommontoalldynamicmediaclassiccomponents) gelten.

>[!NOTE]
>
>Wenn die Flyout-Komponente eine benutzerdefinierte Größe aufweist, wird diese benutzerdefinierte Größe verwendet und die dynamische Einrichtung der Komponente ist deaktiviert.
>
>Wenn Ihre Flyout-Komponente die Standardgröße verwendet, wie in der [!UICONTROL Design]-Ansicht festgelegt, wird die Standardgröße verwendet und die Komponente erstreckt sich, um die Seitenlayoutgröße mit der responsiven Einrichtung der Komponente anzupassen. Beachten Sie jedoch, dass die responsive Einrichtung der Komponente eingeschränkt ist. Beim Verwenden der Flyout-Komponente mit dynamischer Einrichtung sollten Sie sie nicht mit vollständiger Seitendehnung verwenden. Andernfalls kann das Flyout über den rechten Rand der Seite hinausgehen.

![chlimage_1-81](assets/chlimage_1-81.png)

### Bild {#image}

Mit der Dynamic Media Classic-Bildkomponente können Sie Ihren Bildern Dynamic Media Classic-Funktionen hinzufügen, z. B. Dynamic Media Classic-Modifikatoren, Bild- oder Viewer-Vorgaben und Scharfzeichnen. Die Dynamic Media Classic-Bildkomponente ähnelt anderen Bildkomponenten in AEM mit speziellen Dynamic Media Classic-Funktionen. In diesem Beispiel wird auf das Bild der Dynamic Media Classic-URL-Modifikator `&op_invert=1` angewendet.

![](do-not-localize/chlimage_1-6.png)

**[!UICONTROL Titel, ALT-Text]**  - Fügen Sie auf der Registerkarte &quot;  Erweitert&quot;einen Titel zum Bild und alternativen Text für die Benutzer hinzu, deren Grafiken deaktiviert sind.

**[!UICONTROL URL, Öffnen in]**  - Sie können ein Asset von festlegen, um einen Link zu öffnen. Legen Sie die **[!UICONTROL URL]** und **[!UICONTROL Öffnen in]** fest, um anzugeben, ob Sie sie im selben oder in einem neuen Fenster öffnen möchten.

![chlimage_1-82](assets/chlimage_1-82.png)

**[!UICONTROL Viewer-Vorgabe]** : Wählen Sie eine vorhandene Viewer-Vorgabe aus dem Dropdown-Menü aus. Wenn die gewünschte Viewer-Vorgabe nicht sichtbar ist, müssen Sie sie möglicherweise sichtbar machen. Siehe [Verwalten von Viewer-Vorgaben](/help/assets/managing-viewer-presets.md). Es ist nicht möglich, eine Viewer-Vorgabe auszuwählen, wenn Sie eine Bildvorgabe verwenden, und umgekehrt.

**[!UICONTROL Dynamic Media Classic-Konfiguration]**  - Wählen Sie die Dynamic Media Classic-Konfiguration aus, die Sie zum Abrufen aktiver Bildvorgaben aus dem Scene7 Publishing System verwenden möchten.

**[!UICONTROL Bildvorgabe]** : Wählen Sie eine vorhandene Bildvorgabe aus dem Dropdown-Menü aus. Wenn die gewünschte Bildvorgabe nicht sichtbar ist, müssen Sie sie möglicherweise sichtbar machen. Siehe [Verwalten von Bildvorgaben](/help/assets/managing-image-presets.md). Es ist nicht möglich, eine Viewer-Vorgabe auszuwählen, wenn Sie eine Bildvorgabe verwenden, und umgekehrt.

**[!UICONTROL Ausgabeformat]**  - Wählen Sie das Ausgabeformat des Bildes aus, z. B. jpeg. In Abhängigkeit des von Ihnen ausgewählten Ausgabeformats stehen Ihnen möglicherweise zusätzliche Konfigurationsoptionen zur Verfügung. Siehe [Verwalten von Bildvorgaben](/help/assets/managing-image-presets.md).

**[!UICONTROL Scharfzeichnen]**  - Wählen Sie aus, wie das Bild scharfgezeichnet werden soll. Das Scharfzeichnen wird unter [*Adobe Dynamic Media Classic - Bildqualität und Scharfzeichnen - Best Practices*](/help/assets/assets/sharpening_images.pdf) ausführlich erläutert.

**[!UICONTROL URL-Modifikatoren]** : Sie können Bildeffekte ändern, indem Sie zusätzliche Dynamic Media Classic-Bildbefehle bereitstellen. Diese werden unter [Verwalten von Bildvorgaben](/help/assets/managing-image-presets.md) und [Befehlsreferenz](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference.html) beschrieben.

**[!UICONTROL Haltepunkte]**  - Wenn Ihre Website responsiv ist, möchten Sie die Haltepunkte anpassen. Haltepunkte müssen durch Kommas `,` getrennt werden.

### Bildvorlage {#image-template}

[Dynamic Media Classic-](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/template-basics/quick-start-template-basics.html#template-basics) Bildvorlagen sind Photoshop-Inhalte mit Ebenen, die in Dynamic Media Classic importiert wurden und in denen Inhalte und Eigenschaften für Variabilität parametrisiert wurden. Mit der Komponente **[!UICONTROL Bildvorlage]** können Sie Bilder importieren und den Text in AEM dynamisch ändern. Zusätzlich können Sie die Komponente **[!UICONTROL Bildvorlage]** dahingehend konfigurieren, dass sie Werte aus dem Clientkontext übernimmt, damit das Bild jedem Benutzer personalisiert angezeigt wird.

Klicken Sie auf **[!UICONTROL Bearbeiten]**, um die Komponente zu konfigurieren. Sie können [Einstellungen konfigurieren, die für alle Dynamic Media Classic-Komponenten](/help/sites-administering/scene7.md#settingscommontoalldynamicmediaclassicscomponents) sowie andere in diesem Abschnitt beschriebene Einstellungen gelten.

![chlimage_1-83](assets/chlimage_1-83.png)

**[!UICONTROL Dateiverweis, Breite, Höhe]**  - Siehe für alle Dynamic Media Classic-Komponenten gemeinsame Einstellungen.

>[!NOTE]
>
>Dynamic Media Classic-URL-Befehle und -Parameter können der Dateiverweis-URL nicht direkt hinzugefügt werden. Sie können nur auf der Komponenten-Benutzeroberfläche im Bedienfeld **[!UICONTROL Parameter]** definiert werden.

**[!UICONTROL Titel, Alt]** TextFügen Sie in der  [!UICONTROL Dynamic Media Classic-] Bildvorlage einen Titel zum Bild und Alternativtext für Benutzer hinzu, die Grafiken deaktiviert haben.

**[!UICONTROL URL, Öffnen]** in: Sie können ein Asset von festlegen, um einen Link zu öffnen. Legen Sie die **[!UICONTROL URL]** fest. Geben Sie in **[!UICONTROL Öffnen in]** an, ob der Link im selben oder einem neuen Fenster geöffnet werden soll.

![chlimage_1-84](assets/chlimage_1-84.png)

**[!UICONTROL Parameter]** PanelBeim Importieren eines Bildes werden die Parameter vorab mit Informationen aus dem Bild gefüllt. Wenn kein Inhalt vorhanden ist, der dynamisch geändert werden kann, ist dieses Fenster leer.

![chlimage_1-85](assets/chlimage_1-85.png)

#### Dynamisches Ändern von Text {#changing-text-dynamically}

Geben Sie zum dynamischen Ändern des Texts neuen Text in die Felder ein und klicken Sie auf **[!UICONTROL OK]**. In diesem Beispiel lautet der **[!UICONTROL Preis]** 50 $ und der Versand kostet 0,99 $.

![chlimage_1-86](assets/chlimage_1-86.png)

Der Text im Bild ändert sich. Sie können den Text auf den ursprünglichen Wert zurücksetzen, indem Sie neben dem Feld auf **[!UICONTROL Zurücksetzen]** klicken.

![chlimage_1-87](assets/chlimage_1-87.png)

#### Ändern von Text zum Berücksichtigen des Werts eines Clientkontextwerts {#changing-text-to-reflect-the-value-of-a-client-context-value}

Um ein Feld mit einem Client-Kontextwert zu verknüpfen, klicken Sie auf **[!UICONTROL Auswählen]**, um das Client-Kontextmenü zu öffnen, wählen Sie den Client-Kontext aus und klicken Sie auf **[!UICONTROL OK]**. In diesem Beispiel ändert sich der Name auf Grundlage der Verknüpfung des Namens mit dem formatierten Namen im Profil.

![chlimage_1-88](assets/chlimage_1-88.png)

Der Text berücksichtigt den Namen des aktuell angemeldeten Benutzers. Sie können den Text auf den ursprünglichen Wert zurücksetzen, indem Sie neben dem Feld auf **[!UICONTROL Zurücksetzen]** klicken.

![chlimage_1-89](assets/chlimage_1-89.png)

#### Erstellen einer Dynamic Media Classic-Bildvorlage als Link {#making-the-scene-image-template-a-link}

**So erstellen Sie eine Verknüpfung** aus der Dynamic Media Classic-Bildvorlage:

1. Klicken Sie auf der Seite mit der Bildvorlagenkomponente von Dynamic Media Classic auf **[!UICONTROL Bearbeiten]**.
1. Geben Sie im Feld **[!UICONTROL URL]** die URL ein, zu der Benutzer wechseln, wenn sie auf das Bild klicken. Wählen Sie im Feld **[!UICONTROL Öffnen in]** aus, ob das Ziel (in einem neuen oder im selben Fenster) geöffnet werden soll.

   ![chlimage_1-90](assets/chlimage_1-90.png)

1. Klicken Sie auf **[!UICONTROL OK]**.

### Komponente „Video“{#video-component}

Die Komponente Dynamic Media Classic **[!UICONTROL Video]** (verfügbar im Dynamic Media Classic-Abschnitt des Sidekicks) verwendet die Geräte- und Bandbreitenerkennung, um jedem Bildschirm das richtige Video bereitzustellen. Bei dieser Komponente handelt es sich um einen HTML5-Video-Player. Es ist ein einzelner Viewer, der kanalübergreifend verwendet werden kann.

Er kann für adaptive Videosets, ein einzelnes MP4-Video oder ein einzelnes F4V-Video verwendet werden.

Weitere Informationen zur Verwendung von Videos mit der Dynamic Media Classic-Integration finden Sie unter [Video](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md) . Sehen Sie sich außerdem an, wie die [Dynamic Media Classic-Videokomponente **mit der Foundation-Komponente** video **verglichen wird](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md).**

![chlimage_1-91](assets/chlimage_1-91.png)

### Bekannte Einschränkungen für die Videokomponente {#known-limitations-for-the-video-component}

Adobe DAM und WCM zeigen, ob ein Mastervideo hochgeladen wurde. Sie zeigen diese Proxy-Assets nicht an:

* Dynamic Media Classic-kodierte Ausgabeformate
* Adaptive Dynamic Media Classic-Videosets

Wenn Sie ein adaptives Videoset mit der Dynamic Media Classic-Videokomponente verwenden, müssen Sie die Größe der Komponente ändern, um die Abmessungen des Videos anzupassen.

## Dynamic Media Classic-Inhaltsbrowser {#scene-content-browser}

Mit dem Dynamic Media Classic-Inhaltsbrowser können Sie Inhalte aus Dynamic Media Classic direkt in AEM anzeigen. Um auf den Inhaltsbrowser zuzugreifen, wählen Sie in der Inhaltssuche **[!UICONTROL Dynamic Media Classic]** in der Touch-optimierten Benutzeroberfläche oder in der klassischen Benutzeroberfläche das Symbol **[!UICONTROL S7]** aus. Die Funktionalität ist zwischen den beiden Benutzeroberflächen identisch.

Wenn Sie über mehrere Konfigurationen verfügen, zeigt AEM standardmäßig die [Standardkonfiguration](/help/sites-administering/scene7.md#configuring-a-default-configuration) an. Sie können verschiedene Konfigurationen direkt im Inhaltsbrowser von Dynamic Media Classic im Dropdown-Menü auswählen.

>[!NOTE]
>
>* Im Ad-hoc-Ordner befindliche Assets werden nicht im Inhaltsbrowser von Dynamic Media Classic angezeigt.
>* Wenn [Sichere Vorschau aktiviert ist](/help/sites-administering/scene7.md#configuring-the-state-published-unpublished-of-assets-pushed-to-scene), werden veröffentlichte und nicht veröffentlichte Assets in Dynamic Media Classic im Inhaltsbrowser von Dynamic Media Classic angezeigt.
>* Wenn **[!UICONTROL Dynamic Media Classic]** oder das Symbol **[!UICONTROL S7]** nicht als Option im Inhaltsbrowser angezeigt wird, müssen Sie [Dynamic Media Classic für die Verwendung mit AEM](/help/sites-administering/scene7.md) konfigurieren.

   >
   >
* Für Videos unterstützt der Inhaltsbrowser von Dynamic Media Classic Folgendes:
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
>Für Videos unterstützt der Dynamic Media Classic-Inhaltsbrowser von WCM Folgendes:
>
>* Adaptive Videosets: Container von allen für die bildschirmübergreifende optimierte Wiedergabe erforderlichen Videoausgabeformaten
>* Einzelnes MP4-Video
>* Einzelnes F4V-Video

>



### Suchen nach Dynamic Media Classic-Assets mit dem Inhaltsbrowser {#searching-for-scene-assets-with-the-content-browser}

Die Suche nach Dynamic Media Classic-Assets verläuft ähnlich wie die Suche nach AEM Assets. Bei der Suche wird Ihnen jedoch eine Remote-Ansicht der Assets im Dynamic Media Classic-System angezeigt, anstatt sie direkt in AEM zu importieren.

Sie können die klassische oder Touch-optimierte Benutzeroberfläche verwenden, um Assets anzuzeigen und nach ihnen zu suchen. In Abhängigkeit von der Oberfläche unterscheidet sich die Art und Weise der Suche etwas.

Wenn Sie auf einer der Benutzeroberflächen suchen, können Sie nach den folgenden Kriterien filtern (wird hier in der Touch-optimierten Benutzeroberfläche gezeigt):

**[!UICONTROL Keywords]**  - Sie können Assets nach Namen suchen. Bei der Suche entsprechen die von Ihnen eingegebenen Keywords dem Beginn des Dateinamens. Zum Beispiel führt die Eingabe des Worts „schwimmen“ dazu, dass nach Asset-Dateinamen gesucht wird, die mit diesen Buchstaben in dieser Reihenfolge beginnen. Drücken Sie die Eingabetaste, nachdem Sie den Begriff eingegeben haben, um nach dem Asset zu suchen.

![chlimage_1-93](assets/chlimage_1-93.png)

**[!UICONTROL Ordner/Pfad]**  - Der Name des angezeigten Ordners basiert auf der von Ihnen ausgewählten Konfiguration. Sie können niedrigere Ebenen anzeigen, indem Sie auf das Ordnersymbol klicken, einen Unterordner auswählen und dann auf das Häkchen klicken, um ihn auszuwählen.

Wenn Sie ein Keyword eingeben und einen Ordner auswählen, durchsucht AEM diesen Ordner und die zugehörigen Unterordner. Wenn Sie jedoch bei der Suche keine Keywords eingeben, wird durch die Auswahl des Ordners das Asset nur in diesem Ordner angezeigt und nicht in Unterordnern.

Standardmäßig durchsucht AEM den ausgewählten Ordner und alle Unterordner.

![chlimage_1-94](assets/chlimage_1-94.png)

**[!UICONTROL Typ von]** AssetWählen Sie Dynamic Media Classic aus, um Dynamic Media Classic-Inhalte zu durchsuchen. Diese Option ist nur verfügbar, wenn Sie Dynamic Media Classic bereits konfiguriert haben.

![chlimage_1-95](assets/chlimage_1-95.png)

**** KonfigurationWenn Sie in  [!UICONTROL Cloud Services] mehr als eine Dynamic Media Classic-Konfiguration definiert haben, können Sie sie hier auswählen. Der Ordner ändert sich anhand der von Ihnen ausgewählten Konfiguration.

![chlimage_1-96](assets/chlimage_1-96.png)

**[!UICONTROL Asset-]** Typ Im Dynamic Media Classic-Browser können Sie die Ergebnisse filtern, um Folgendes einzuschließen: Bilder, Vorlagen, Videos und adaptive Videosets. Wenn Sie keinen Asset-Typ auswählen, durchsucht AEM standardmäßig alle Asset-Typen.

![chlimage_1-97](assets/chlimage_1-97.png)

>[!NOTE]
>
>* Beim Durchsuchen eines Videos suchen Sie nach einem einzelnen Ausgabeformat. Die Ergebnisse geben die ursprüngliche Ausgabedarstellung (nur &amp;ast;.mp4) und die kodierte Ausgabedarstellung zurück.
>* Bei der Suche nach einem adaptiven Videoset durchsuchen Sie den Ordner und alle Unterordner, jedoch nur, wenn Sie der Suche ein Keyword hinzugefügt haben. Wenn Sie kein Keyword hinzugefügt haben, durchsucht AEM nicht die Unterordner.

>



**[!UICONTROL Veröffentlichungsstatus]** Sie können nach Assets basierend auf dem Veröffentlichungsstatus filtern:   Veröffentlichung oder  [!UICONTROL Veröffentlichung rückgängig gemacht]. Wenn Sie keinen [!UICONTROL Veröffentlichungsstatus] auswählen, durchsucht AEM standardmäßig alle Veröffentlichungsstatus.

![chlimage_1-98](assets/chlimage_1-98.png)
