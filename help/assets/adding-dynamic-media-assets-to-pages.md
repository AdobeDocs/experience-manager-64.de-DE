---
title: Hinzufügen von Dynamic Media-Assets zu Seiten
seo-title: Hinzufügen von Dynamic Media-Assets zu Seiten
description: Erfahren Sie, wie Sie in AEM einer Seite Komponenten für dynamische Medien hinzufügen können.
seo-description: Erfahren Sie, wie Sie in AEM einer Seite Komponenten für dynamische Medien hinzufügen können.
uuid: 77abcb87-2df7-449b-be52-540d749890b6
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: d1f45751-1761-4d6b-b17d-110b2f1117ea
translation-type: tm+mt
source-git-commit: 501a6c470113d249646f4424a19ee215a82b032d
workflow-type: tm+mt
source-wordcount: '2830'
ht-degree: 62%

---


# Hinzufügen von Dynamic Media-Assets zu Seiten {#adding-dynamic-media-assets-to-pages}

To add the dynamic media functionality to assets you use on your websites, you can add the **Dynamic Media** or **Interactive Media** component directly on the page. Wechseln Sie dazu in den Layoutmodus und aktivieren Sie die Komponenten vom Typ „Dynamische Medien“. Anschließend können Sie der Seite diese Komponenten und der Komponente Assets hinzufügen. „Dynamische Medien“ und „Interaktive Medien“ sind intelligente Komponenten, die erkennen, ob Sie ein Bild oder ein Video hinzufügen. Die verfügbaren Optionen werden entsprechend angepasst.

Sie können dynamische Medienelemente direkt zur Seite hinzufügen, wenn Sie AEM als WCM verwenden. Wenn Sie einen Drittanbieter für Ihr WCM verwenden, [verknüpfen](linking-urls-to-yourwebapplication.md) Sie Ihre Assets oder [betten](embed-code.md) Sie sie ein. Eine responsive Website von Drittanbietern finden Sie unter [Bereitstellen optimierter Bilder für eine responsive Site](responsive-site.md).

>[!NOTE]
>
>Sie müssen Assets veröffentlichen, um sie Seiten in AEM hinzufügen zu können. Siehe [Veröffentlichen von Dynamic Media-Assets ](publishing-dynamicmedia-assets.md).

## Hinzufügen einer Dynamic Media-Komponente zu einer Seite       {#adding-a-dynamic-media-component-to-a-page}

Das Hinzufügen einer Seitenkomponente zu einer Dynamic Media ist dasselbe wie das Hinzufügen einer  zu einer beliebigen Seite. Die Dynamic Media-Komponenten werden in den folgenden Abschnitten ausführlich beschrieben.

>[!NOTE]
>
>Wenn eine Dynamic Media-Komponente auf einer Webseite vorhanden ist, auf die ein Benutzer mit schreibgeschützten Berechtigungen zugreift, werden die Seitenumbrüche und die Komponenten nicht korrekt dargestellt. Der Grund dafür ist, dass die Seite rekonstruiert wurde, um sicherzustellen, dass die Eigenschaften der Komponenten gut sind und alle referenzierten Assets und Konfigurationen verfügbar sind. Die Seite wird dann erneut gerendert und die Komponenten werden umgebrochen. Der entsprechende Komponentencode auf der Seite kann aufgrund des schreibgeschützten Zugriffs des Benutzers nicht erneut gerendert werden.
>  
>Um dieses Problem zu vermeiden, müssen Sie sicherstellen, dass die Benutzer über die erforderlichen Berechtigungen zum Zugriff auf die Assets verfügen.

1. Öffnen Sie in AEM die Seite, auf der Sie die Dynamic Media-Komponente hinzufügen möchten.
1. Klicken Sie im Bedienfeld auf der linken Seite der Seite (möglicherweise müssen Sie die Anzeige des Seitenbedienfelds umschalten) auf das Symbol &quot; **[!UICONTROL Komponenten]** &quot;.
1. Wählen Sie unter der Überschrift **[!UICONTROL Komponenten]** in der Dropdown-Liste **[!UICONTROL Dynamic Media]** aus. Wenn keine Liste der Dynamic Media-Komponenten verfügbar ist, müssen Sie wahrscheinlich die zu verwendenden Dynamic Media-Komponenten aktivieren. Informationen hierzu finden Sie unter [Aktivieren von Dynamic Media-Komponenten](#enabling-dynamic-media-components).

   ![chlimage_1-537](assets/chlimage_1-537.png)

1. Ziehen Sie eine Dynamic Media-Komponente, die Sie verwenden möchten, an die gewünschte Position auf der Seite.
1. Bewegen Sie den Mauszeiger direkt über die Komponente. Wenn die Komponente blau hervorgehoben wird, tippen Sie einmal darauf, um die Symbolleiste der Komponente anzuzeigen. Tippen Sie auf das Symbol **** Konfiguration (Schraubenschlüssel).
1. [Bearbeiten Sie die Komponenten](#dynamic-media-components) nach Bedarf und klicken Sie auf das Häkchen, um die Änderungen zu speichern.

### Aktivieren von Dynamic Media-Komponenten {#enabling-dynamic-media-components}

Wenn keine Dynamic Media-Komponenten zum Hinzufügen zu einer Seite verfügbar sind, bedeutet dies wahrscheinlich, dass Sie zunächst die zu verwendenden Komponenten aktivieren müssen.

1. Öffnen Sie in AEM die Seite, auf der Sie die Dynamic Media-Komponente hinzufügen möchten.
1. Tippen Sie links oben auf der Seite in der Symbolleiste auf das Symbol „Seiteninformationen“ und dann in der Dropdown-Liste auf **[!UICONTROL Vorlage bearbeiten]**.

   ![edit-template](/help/assets/assets-dm/edit-template.png)

1. Tippen Sie oben rechts auf der Seite in der Symbolleiste in der Dropdown-Liste auf **[!UICONTROL Struktur]**.

   ![Richtlinie](/help/assets/assets-dm/structure-mode.png)

1. Tippen Sie unten auf der Seite auf **[!UICONTROL Layout-Container]**, um die Symbolleiste zu öffnen. Tippen Sie anschließend auf das Symbol „Richtlinie“.
1. Stellen Sie auf der Seite **[!UICONTROL Layout-Container]** unter der Überschrift **[!UICONTROL Eigenschaften]** sicher, dass die Registerkarte **[!UICONTROL Zulässige Komponenten]** ausgewählt ist.

   ![Zugelassene Komponenten](/help/assets/assets-dm/allowed-components.png)

1. Scrollen Sie nach unten, bis **[!UICONTROL Dynamic Media]** angezeigt wird.
1. Tippen Sie links neben **[!UICONTROL Dynamic Media]** auf „>“, um die Liste zu erweitern, und wählen Sie die Dynamic Media-Komponenten aus, die Sie aktivieren möchten.

   ![Liste der Dynamic Media-Komponenten](/help/assets/assets-dm/dm-components-select.png)

1. Tippen Sie rechts oben auf der Seite **[!UICONTROL Layout-Container]** auf das Symbol „Fertig“ (Häkchen).

1. Tippen Sie oben rechts auf der Seite in der Symbolleiste in der Dropdown-Liste auf **[!UICONTROL Anfänglicher Inhalt]** und [fügen Sie dann wie gewohnt eine Dynamic Media-Komponente zu einer Seite hinzu](#adding-a-dynamic-media-component-to-a-page).

## Localizing Dynamic Media components {#localizing-dynamic-media-components}

Zum Lokalisieren von Dynamic Media-Komponenten stehen Ihnen zwei Möglichkeiten zur Verfügung:

* Öffnen Sie auf einer Web-Seite unter „Sites“ die Option **[!UICONTROL Eigenschaften]** und wählen Sie die Registerkarte **[!UICONTROL Erweitert]** aus. Wählen Sie die gewünschte Sprache für die Lokalisierung aus.

   ![chlimage_1-538](assets/chlimage_1-538.png)

* Wählen Sie über den Site-Selector die gewünschte Seite oder Seitengruppe aus. Tippen Sie auf **[!UICONTROL Eigenschaften]** und wählen Sie die Registerkarte **[!UICONTROL Erweitert]** aus. Wählen Sie die gewünschte Sprache für die Lokalisierung aus.

   >[!NOTE]
   >
   >Nicht allen im Menü **[!UICONTROL Sprache]** verfügbaren Sprachen sind derzeit Tokens zugewiesen.

## Dynamic Media components {#dynamic-media-components}

Dynamic Media and Interactive Media are available under the [!UICONTROL Dynamic Media] tab in [!UICONTROL Components]. Verwenden Sie die Komponente [!UICONTROL Interaktive Medien] für beliebige interaktive Assets wie interaktive Videos, interaktive Bilder oder Karussell-Sets. Verwenden Sie für alle anderen Komponenten vom Typ „Dynamische Medien“ die Komponente Dynamische Medien.

>[!NOTE]
>
>Diese Komponenten sind nicht standardmäßig verfügbar und müssen zunächst über den Vorlagen-Editor bereitgestellt werden. [Nachdem sie im Vorlageneditor zur Verfügung gestellt wurden, können Sie die Komponenten wie jede andere AEM-Komponente Ihrer Seite hinzufügen.](/help/sites-authoring/templates.md#editing-templates-template-authors)

![chlimage_1-539](assets/chlimage_1-539.png)

### Komponente „Dynamische Medien“{#dynamic-media-component}

Die Komponente &quot;Dynamic Media&quot;ist intelligent. Je nachdem, ob Sie ein Bild oder ein Video hinzufügen, stehen Ihnen verschiedene Optionen zur Verfügung. Die Komponente unterstützt Bildvorgaben, bildbasierte Viewer wie Bildsets sowie Rotationssets, gemischte Mediensets und Videos. Darüber hinaus reagiert der Viewer. Das heißt, die Bildschirmgröße ändert sich automatisch je nach Bildschirmgröße. Bei allen Viewern handelt es sich um HTML5-Viewer.

>[!NOTE]
>
>Wenn es eine Komponente für Dynamic Media, eine Komponente für interaktive Medien oder beides auf einer Webseite gibt, auf die ein Benutzer mit schreibgeschützten Berechtigungen zugreift, werden die Seitenumbrüche und die Komponenten nicht korrekt dargestellt. Der Grund dafür ist, dass die Seite rekonstruiert wurde, um sicherzustellen, dass die Eigenschaften der Komponenten gut sind und alle referenzierten Assets und Konfigurationen verfügbar sind. Die Seite wird dann erneut gerendert und die Komponenten werden umgebrochen. Der entsprechende Komponentencode auf der Seite kann aufgrund des schreibgeschützten Zugriffs des Benutzers nicht erneut gerendert werden.
>  
>Um dieses Problem zu vermeiden, müssen Sie sicherstellen, dass die Benutzer über die erforderlichen Berechtigungen zum Zugriff auf die Assets verfügen.

>[!NOTE]
>
>Wenn Sie die Dynamic Media-Komponente hinzufügen und **[!UICONTROL Einstellungen für dynamische Medien]** leer ist, ist es nicht möglich, ein Asset ordnungsgemäß hinzuzufügen. Überprüfen Sie Folgendes:
>
>* Sie [Dynamic Media aktiviert](config-dynamic.md) haben. Dynamic Media ist standardmäßig deaktiviert.
>* das Bild eine Pyramid TIFF-Datei aufweist. Bilder, die vor der Aktivierung von dynamischen Medien importiert wurden, verfügen nicht über eine Pyramid TIFF-Datei.

>



#### Arbeiten mit Bildern       {#when-working-with-images}

Mit der Komponente „Dynamische Medien“ können Sie dynamische Bilder, einschließlich Bildsets, Rotationssets und Sets für gemischte Medien, hinzufügen. Sie können Vergrößerungen sowie Verkleinerungen vornehmen und (sofern zutreffend) ein Bild in einem Rotationsset drehen oder ein Bild aus einem anderen Set auswählen.

Sie können zudem die Viewer-Vorgabe, Bildvorgabe oder das Bildformat direkt in der Komponente konfigurieren. Um ein Bild dynamisch zu machen, können Sie die Haltepunkte festlegen oder eine dynamische Bildvorgabe anwenden.

You must edit the following Dynamic Media Settings by clicking the **[!UICONTROL Edit]** icon in the component and then **[!UICONTROL Dynamic Media Settings]**.

![dm-settings-image-preset](assets/dm-settings-image-preset.png)

>[!NOTE]
>
>Standardmäßig ist die Bildkomponente für dynamische Medien adaptiv. If you want to make it a fixed size, set it in the component in the **[!UICONTROL Advanced]** tab with the **[!UICONTROL Width]** and **[!UICONTROL Height]** settings.

* **[!UICONTROL Viewer-Vorgabe]**Wählen Sie eine vorhandene Viewer-Vorgabe aus dem Dropdown-Menü. Wenn die gewünschte Viewer-Vorgabe nicht sichtbar ist, müssen Sie sie möglicherweise sichtbar machen. Siehe „Verwalten von Viewer-Vorgaben“. Es ist nicht möglich, eine Viewer-Vorgabe auszuwählen, wenn Sie eine Bildvorgabe verwenden, und umgekehrt.
Dies ist die einzig verfügbare Option beim Anzeigen von Bildsets, Rotationssets oder Sets für gemischte Medien. Die angezeigten Viewer-Vorgaben sind ebenfalls intelligent – es werden nur relevante Viewer-Vorgaben angezeigt.

* **[!UICONTROL Viewer-Modifikatoren]**-Viewer-Modifikatoren haben die Form eines &quot;name=value&quot;-Paars mit einem &amp;-Trennzeichen und ermöglichen das Ändern von Viewern, wie im Viewer-Referenzhandbuch beschrieben. Ein Beispiel für einen Viewer-Modifikator ist posterimage=img.jpg&amp;caption=text.vtt,1, der ein anderes Bild für die Videominiatur festlegt und eine Untertiteldatei mit dem Video verknüpft.

* **[!UICONTROL Bildvorgabe]**Wählen Sie eine vorhandene Bildvorgabe aus dem Dropdown-Menü. Wenn die gewünschte Bildvorgabe nicht sichtbar ist, müssen Sie sie möglicherweise sichtbar machen. Siehe „Verwalten von Bildvorgaben“. Es ist nicht möglich, eine Viewer-Vorgabe auszuwählen, wenn Sie eine Bildvorgabe verwenden, und umgekehrt.
Diese Option ist beim Anzeigen von Bildsets, Rotationssets oder Sets für gemischte Medien nicht verfügbar.

* **[!UICONTROL Bildmodifikatoren]**Sie können Bildeffekte anwenden, indem Sie zusätzliche Bildbefehle bereitstellen. Diese werden unter „Bildvorgaben“ und in der Referenz zum Image-Serving-Befehl beschrieben.
Diese Option ist beim Anzeigen von Bildsets, Rotationssets oder Sets für gemischte Medien nicht verfügbar.

* **[!UICONTROL Haltepunkte]**Wenn Sie dieses Asset auf einer responsiven Site verwenden, müssen Sie die Bild-Haltepunkte hinzufügen. Bildhaltepunkte müssen durch Kommas (,) voneinander getrennt werden. Diese Option kann verwendet werden, wenn in einer Bildvorgabe keine Höhe oder Breite festgelegt ist.
Diese Option ist beim Anzeigen von Bildsets, Rotationssets oder Sets für gemischte Medien nicht verfügbar.
Sie können die folgenden erweiterten Einstellungen bearbeiten, indem Sie in der Komponente auf **[!UICONTROL Bearbeiten]** klicken.

* **[!UICONTROL Titel]**&#x200B;Ändern Sie den Titel des Bilds.

* **[!UICONTROL Alt-Text]**Hinzufügen einen Titel für das Bild für Benutzer, die Grafiken deaktiviert haben.
Diese Option ist beim Anzeigen von Bildsets, Rotationssets oder Sets für gemischte Medien nicht verfügbar.

* **[!UICONTROL URL, In]**Öffnen Sie ein Asset, um einen Link zu öffnen. Legen Sie die URL fest. Geben Sie in „Öffnen in“ an, ob der Link im selben oder einem neuen Fenster geöffnet werden soll.
Diese Option ist beim Anzeigen von Bildsets, Rotationssets oder Sets für gemischte Medien nicht verfügbar.

* **[!UICONTROL Breite]** und **[!UICONTROL Höhe]** Geben Sie den Wert in Pixel ein, wenn das Bild eine feste Größe haben soll. Wenn die Werte leer gelassen werden, ist das Asset adaptiv.

#### Arbeiten mit Videos {#when-working-with-video}

Verwenden Sie die Dynamic Media-Komponente, um Ihren Web-Seiten dynamische Videos hinzuzufügen. Beim Bearbeiten der Komponente können Sie eine vordefinierte Video-Viewer-Vorgabe für das Wiedergeben des Videos auf der Seite verwenden.

![chlimage_1-540](assets/chlimage_1-540.png)

You must edit the following Dynamic Media Settings by clicking **[!UICONTROL Edit]** in the component.

>[!NOTE]
>
>Die Videokomponente für Dynamic Media ist standardmäßig adaptiv. Wenn sie eine feste Größe aufweisen soll, müssen Sie dies in der Komponente auf der Registerkarte **[!UICONTROL Erweitert]** mit **[!UICONTROL Breite]** und [!UICONTROL Höhe] festlegen.

* **[!UICONTROL Viewer-Vorgabe]** Wählen Sie eine vorhandene Video-Viewer-Vorgabe aus dem Dropdown-Menü. Wenn die gewünschte Viewer-Vorgabe nicht sichtbar ist, müssen Sie sie möglicherweise sichtbar machen. Siehe „Verwalten von Viewer-Vorgaben“.

* **[!UICONTROL Viewer-Modifikatoren]**-Viewer-Modifikatoren haben die Form eines &quot;name=value&quot;-Paars mit einem &amp;-Trennzeichen und ermöglichen das Ändern von Viewern, wie im Adobe Viewer-Referenzhandbuch beschrieben. Ein Beispiel für einen Viewer-Modifikator ist posterimage=img.jpg&amp;caption=text.vtt,1.

   Mit Viewer-Modifikatoren können Sie beispielsweise Folgendes ausführen:

   * Associate a caption file with a video [caption](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-caption.html)
   * Associate a navigation file with a video [navigation](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-navigation.html)

You can edit the following [!UICONTROL Advanced Settings] by clicking **[!UICONTROL Edit]** in the component.

* **[!UICONTROL Titel]**&#x200B;Ändern Sie den Titel des Videos.

* **[!UICONTROL Breite]** und **[!UICONTROL Höhe]** Geben Sie den Wert in Pixel ein, wenn das Video eine feste Größe haben soll. Wenn die Werte leer gelassen werden, wird es adaptiv.

#### Bei der Arbeit mit smartem Zuschneiden {#when-working-with-smart-crop}

Verwenden Sie die Dynamic Media-Komponente, um Bild-Assets für smartes Zuschneiden zu Ihren Web-Seiten hinzuzufügen. Beim Bearbeiten der Komponente können Sie eine vordefinierte Video-Viewer-Vorgabe für das Wiedergeben des Videos auf der Seite verwenden.

Weitere Informationen finden Sie unter [Bildprofile](image-profiles.md).

![dm-settings-smart-cut](assets/dm-settings-smart-crop.png)

You can edit the following [!UICONTROL Dynamic Media Settings] by clicking **[!UICONTROL Edit]** in the component.

>[!NOTE]
>
>Standardmäßig ist die Bildkomponente für dynamische Medien adaptiv. Wenn Sie eine feste Größe einrichten möchten, legen Sie sie auf der Registerkarte [!UICONTROL Erweitert] in der Komponente mit der **[!UICONTROL Breite]** und **[!UICONTROL Höhe]** fest.

* **[!UICONTROL Bildmodifikatoren]**Sie können Bildeffekte anwenden, indem Sie zusätzliche Bildbefehle bereitstellen. Diese werden unter „Bildvorgaben“ und in der Referenz zum Image-Serving-Befehl beschrieben.
Diese Option ist beim Anzeigen von Bildsets, Rotationssets oder Sets für gemischte Medien nicht verfügbar.

You can edit the following **[!UICONTROL Advanced]** settings by clicking **[!UICONTROL Edit]** in the component.

* **[!UICONTROL Titel]**&#x200B;Ändern Sie den Titel des Smart-Schnittbilds.

* **[!UICONTROL Alt-Text]**Hinzufügen einen Titel für das intelligente Beschneidungsbild für Benutzer, die Grafiken deaktiviert haben.
Diese Option ist beim Anzeigen von Bildsets, Rotationssets oder Sets für gemischte Medien nicht verfügbar.

* **[!UICONTROL URL, In]**Öffnen Sie ein Asset, um einen Link zu öffnen. Legen Sie die URL fest. Geben Sie in „Öffnen in“ an, ob der Link im selben oder einem neuen Fenster geöffnet werden soll.
Diese Option ist beim Anzeigen von Bildsets, Rotationssets oder Sets für gemischte Medien nicht verfügbar.

* **[!UICONTROL Height** and **[!UICONTROL Width]** Geben Sie den Wert in Pixel ein, wenn das Smart-Schnittbild eine feste Größe haben soll. Wenn die Werte leer gelassen werden, wird es adaptiv.

### Interactive Media component {#interactive-media-component}

Die Komponente „Interaktive Medien“ ist für Assets mit interaktiven Elementen wie Hotspots oder Imagemaps vorgesehen. Verwenden Sie bei interaktiven Bildern, interaktiven Videos oder Karussellbannern die Komponente Interaktive Medien.

Die Komponente &quot;Interaktive Medien&quot;ist intelligent. Je nachdem, ob Sie ein Bild oder ein Video hinzufügen, stehen Ihnen verschiedene Optionen zur Verfügung. Zudem ist der Viewer dynamisch. Die Größe des Bildschirms ändert sich demnach automatisch auf Grundlage der Bildschirmgröße. Bei allen Viewern handelt es sich um HTML5-Viewer.

>[!NOTE]
>
>Wenn es eine Komponente für Dynamic Media, eine Komponente für interaktive Medien oder beides auf einer Webseite gibt, auf die ein Benutzer mit schreibgeschützten Berechtigungen zugreift, werden die Seitenumbrüche und die Komponenten nicht korrekt dargestellt. Der Grund dafür ist, dass die Seite rekonstruiert wurde, um sicherzustellen, dass die Eigenschaften der Komponenten gut sind und alle referenzierten Assets und Konfigurationen verfügbar sind. Die Seite wird dann erneut gerendert und die Komponenten werden umgebrochen. Der entsprechende Komponentencode auf der Seite kann aufgrund des schreibgeschützten Zugriffs des Benutzers nicht erneut gerendert werden.
> 
>Um dieses Problem zu vermeiden, müssen Sie sicherstellen, dass die Benutzer über die erforderlichen Berechtigungen zum Zugriff auf die Assets verfügen.

![chlimage_1-541](assets/chlimage_1-541.png)

Sie können die folgenden allgemeinen Einstellungen **** bearbeiten, indem Sie in der Komponente auf **[!UICONTROL Bearbeiten]** klicken.

* **[!UICONTROL Viewer-Vorgabe]** Wählen Sie eine vorhandene Viewer-Vorgabe aus dem Dropdown-Menü. Wenn die gewünschte Viewer-Vorgabe nicht sichtbar ist, müssen Sie sie möglicherweise sichtbar machen. Viewer-Vorgaben müssen veröffentlicht werden, bevor sie verwendet werden können. Siehe „Verwalten von Viewer-Vorgaben“.

* **[!UICONTROL Titel]**&#x200B;Ändern Sie den Titel des Videos.

* **[!UICONTROL Breite]** und **[!UICONTROL Höhe]** Geben Sie den Wert in Pixel ein, wenn das Video eine feste Größe haben soll. Wenn die Werte leer gelassen werden, wird es adaptiv.

Sie können die folgenden Einstellungen von **[!UICONTROL Zu Warenkorb hinzufügen]** bearbeiten, indem Sie in der Komponente auf **[!UICONTROL Bearbeiten]** klicken.

* **[!UICONTROL Produkt-Asset]** anzeigen Standardmäßig ist dieser Wert ausgewählt. Das Produkt-Asset zeigt ein Bild des Produkts, wie im Commerce-Modul definiert. Deaktivieren Sie das Kontrollkästchen, um das Produkt-Asset nicht anzuzeigen.

* **[!UICONTROL Produktpreis]** anzeigen Standardmäßig ist dieser Wert ausgewählt. Der Produktpreis gibt den Preis des Artikels an, wie im Commerce-Modul definiert. Deaktivieren Sie das Kontrollkästchen, um den Produktpreis nicht anzuzeigen.

* **[!UICONTROL Produktformular]** anzeigen Standardmäßig ist dieser Wert nicht ausgewählt. Das Produktformular beinhaltet jegliche Produktvarianten, etwa hinsichtlich der Größe und der Farbe. Deaktivieren Sie das Kontrollkästchen, um die Produktvarianten nicht anzuzeigen.

### Panoramic Media component {#panoramic-media-component}

Die Panoramamedienkomponente bezieht sich auf Kugelpanoramen. Solche Bilder bieten ein 360°-Zuschauererlebnis eines Raums, einer Immobile, eines Ortes oder einer Landschaft. Damit ein Bild als Kugelpanorama gilt, muss MINDESTENS eine der beiden folgenden Eigenschaften zutreffen:

* Ein Seitenverhältnis von 2:1.
* Mit den Keywords „equirectangular“ oder („spherical“ und „panorama“) oder („spherical“ und „panoramic“) als Tags versehen. Weitere Informationen finden Sie unter [Verwenden von Tags](/help/sites-authoring/tags.md).

Die Kriterien für das Seitenverhältnis sowie die Keywords gelten für Panorama-Assets für die Asset-Detailseite und die WCM-Komponente „Panoramamedien“.

![panoramic-media-viewer-preset](assets/panoramic-media-viewer-preset.png)

Sie können die folgenden erweiterten Einstellungen bearbeiten, indem Sie in der Komponente auf **[!UICONTROL Konfigurieren]** tippen.

* **[!UICONTROL Viewer-Vorgabe]** Wählen Sie einen vorhandenen Viewer aus dem Dropdown-Menü &quot;Viewer-Vorgabe&quot;aus.

Wenn die gesuchte Viewer-Vorgabe nicht angezeigt wird, stellen Sie sicher, dass sie veröffentlicht wurde. Sie müssen Viewer-Vorgaben veröffentlichen, bevor Sie sie verwenden können. Siehe [Verwalten von Viewer-Vorgaben](managing-viewer-presets.md).

### Bereitstellen von Dynamic Media-Assets mit HTTP/2 {#using-http-to-delivery-dynamic-media-assets}

HTTP/2 ist das neue, aktualisierte Webprotokoll, das die Kommunikation zwischen Browser und Servern verbessert. Es beschleunigt die Übertragung von Informationen und reduziert die erforderliche Prozessorleistung. Es ist jetzt möglich, Dynamic Media-Assets über HTTP/2 bereitzustellen, das schnellere Reaktions- und Ladezeiten bietet.

Vollständige Informationen zu den ersten Schritten mit HTTP/2 und Ihrem Dynamic Media-Konto finden Sie unter [Bereitstellung von Inhalt über HTTP/2](http2.md).

>[!MORELIKETHIS]
>
>* [Farb-Management mit AEM Dynamic Media](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-color-management-technical-video-setup.html)
>* [Verwenden der benutzerdefinierten Videominiatur mit AEM Dynamic Media](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-video-thumbnails-feature-video-use.html)
>* [Verwenden des Asset-Viewers mit AEM Dynamic Media](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-viewer-feature-video-understand.html)
>* [Verwenden von interaktiven Videos mit AEM Dynamic Media](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-interactive-video-feature-video-use.html)
>* [Verwenden des Video-Players in AEM Dynamic Media](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-video-player-feature-video-use.html)
>* [Verwenden des Scharfzeichnens von Bildern mit AEM Dynamic Media](https://helpx.adobe.com/experience-manager/6-4/assets/using/best-practices-for-optimizing-the-quality-of-your-images.html)

