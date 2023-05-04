---
title: Hinzufügen von Dynamic Media-Assets zu Seiten
seo-title: Adding Dynamic Media assets to pages
description: Um die Funktion für dynamische Medien zu Assets hinzuzufügen, die Sie auf Ihren Websites verwenden, können Sie die Komponente Dynamic Media oder Interaktive Medien direkt auf der Seite hinzufügen.
seo-description: To add the dynamic media functionality to assets you use on your websites, you can add the Dynamic Media or Interactive Media component directly on the page.
uuid: 650d0867-a079-4936-a466-55b7a30803a2
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 331f4980-5193-4546-a22e-f27e38bb8250
exl-id: b498d54e-ff34-49a1-bfad-c6efbb6f75f4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1721'
ht-degree: 56%

---

# Hinzufügen von Dynamic Media-Assets zu Seiten{#adding-dynamic-media-assets-to-pages}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Zum Hinzufügen der Funktion „Dynamic Media“ zu auf Websites verwendeten Assets können Sie die Komponente **[!UICONTROL Dynamic Media]** oder **[!UICONTROL Interaktive Medien]** direkt auf der Seite hinzufügen. Geben Sie dazu [!UICONTROL Design] und die Aktivierung der Komponenten für dynamische Medien. Anschließend können Sie der Seite diese Komponenten und der Komponente Assets hinzufügen. Die Komponenten für dynamische Medien und interaktive Medien sind intelligent. Sie wissen, ob Sie ein Bild oder Video hinzufügen. Die verfügbaren Optionen ändern sich entsprechend.

Sie fügen Dynamic Media-Assets direkt zur Seite hinzu, wenn Sie AEM als WCM verwenden.

>[!NOTE]
>
>Imagemaps sind für Karussellbanner umgehend verfügbar.

## Hinzufügen einer Dynamic Media-Komponente zu einer Seite {#adding-a-dynamic-media-component-to-a-page}

Das Hinzufügen einer Komponente vom Typ [!UICONTROL Dynamic Media] oder [!UICONTROL Interaktive Medien] entspricht dem Hinzufügen einer Komponente zu einer Seite. Die Komponenten vom Typ [!UICONTROL Dynamic Media] oder [!UICONTROL Interaktive Medien] werden in den folgenden Abschnitten ausführlicher beschrieben.

So fügen Sie einer Seite eine Komponente bzw. einen Viewer vom Typ „Dynamic Media“ hinzu:

1. Öffnen Sie in AEM die Seite, auf der Sie die Dynamic Media-Komponente hinzufügen möchten.
1. Wenn keine Dynamic Media-Komponente verfügbar ist, klicken Sie auf das Lineal im [!UICONTROL Sidekick] eingeben **[!UICONTROL Design]** mode, click **[!UICONTROL Bearbeiten]** parsys und wählen Sie **[!UICONTROL Dynamic Media]** , um die Dynamic Media-Komponenten verfügbar zu machen.

   >[!NOTE]
   >
   >Weitere Informationen finden Sie unter [Konfigurieren von Komponenten im Design-Modus](/help/sites-authoring/default-components-designmode.md).

1. Kehren Sie zum Modus **[!UICONTROL Bearbeiten]** zurück, indem Sie auf das Stiftsymbol im [!UICONTROL Sidekick] klicken.
1. Ziehen Sie die Komponente **[!UICONTROL Dynamic Media]** oder **[!UICONTROL Interaktive Medien]** aus der Gruppe **[!UICONTROL Sonstige]** im Sidekick an die gewünschte Stelle auf der Seite.
1. Klicken **[!UICONTROL Bearbeiten]** , um die Komponente zu öffnen.
1. [Bearbeiten der Komponente](#dynamic-media-component) klicken Sie bei Bedarf auf **[!UICONTROL OK]** , um Änderungen zu speichern.

## Komponenten vom Typ „Dynamic Media“ {#dynamic-media-components}

[!UICONTROL Dynamic Media] und [!UICONTROL Interaktive Medien] sind im [!UICONTROL Sidekick] unter **[!UICONTROL Dynamic Media]** verfügbar. Verwenden Sie die Komponente **[!UICONTROL Interaktive Medien]** für beliebige interaktive Assets wie interaktive Videos, interaktive Bilder oder Karussellsets. Verwenden Sie für alle anderen Dynamic Media-Komponenten den **[!UICONTROL Dynamic Media]** -Komponente.

![chlimage_1-71](assets/chlimage_1-71.png)

>[!NOTE]
>
>Diese Komponenten sind standardmäßig nicht verfügbar und müssen vor der Verwendung im Designmodus ausgewählt werden. [Nachdem sie im Designmodus verfügbar gemacht wurden](/help/sites-authoring/default-components-designmode.md)können Sie die Komponenten Ihrer Seite wie jede andere AEM hinzufügen.

### Komponente „Dynamic Media“ {#dynamic-media-component}

Die Komponente „Dynamic Media“ ist intelligent. In Abhängigkeit davon, ob Sie ein Bild oder Video hinzufügen, haben Sie verschiedene Optionen. Die Komponente unterstützt Bildvorgaben, bildbasierte Viewer wie Bildsets sowie Rotationssets, Sets für gemischte Medien und Videos. Darüber hinaus ist der Viewer responsiv. Das heißt, die Größe des Bildschirms ändert sich automatisch entsprechend der Bildschirmgröße. Bei allen Viewern handelt es sich um HTML5-Viewer.

>[!NOTE]
>
>Wenn Sie die Komponente [!UICONTROL Dynamic Media] hinzufügen und **[!UICONTROL Einstellungen für Dynamic Media]** leer ist oder es nicht möglich ist, ein Asset ordnungsgemäß hinzuzufügen, überprüfen Sie Folgendes:
>
>* Sie haben [Dynamic Media aktiviert](/help/assets/config-dynamic.md). Dynamic Media ist standardmäßig deaktiviert.
>* Das Bild weißt eine Pyramid TIFF-Datei auf. Bilder, die vor der Aktivierung von Dynamic Media importiert wurden, verfügen nicht über eine Pyramid TIFF-Datei.
>


#### Arbeiten mit Bildern {#when-working-with-images}

Mit der Komponente [!UICONTROL Dynamic Media] können Sie dynamische Bilder, einschließlich Bildsets, Rotationssets und Sets für gemischte Medien, hinzufügen. Sie können Vergrößerungen sowie Verkleinerungen vornehmen und (sofern zutreffend) ein Bild in einem Rotationsset drehen oder ein Bild aus einem anderen Set auswählen.

Sie können zudem die Viewer-Vorgabe, Bildvorgabe oder das Bildformat direkt in der Komponente konfigurieren. Um ein Bild responsiv zu gestalten, können Sie entweder die Haltepunkte festlegen oder eine responsive Bildvorgabe anwenden.

![chlimage_1-72](assets/chlimage_1-72.png)

Sie können die folgenden Einstellungen für Dynamic Media bearbeiten, indem Sie in der Komponente auf **[!UICONTROL Bearbeiten]** und dann auf die Registerkarte **[!UICONTROL Einstellungen für Dynamic Media]** klicken.

![chlimage_1-73](assets/chlimage_1-73.png)

>[!NOTE]
>
>Standardmäßig ist die Bildkomponente für Dynamic Media adaptiv. Wenn Sie eine feste Größe einrichten möchten, legen Sie sie in der Komponente auf der Registerkarte **[!UICONTROL Erweitert]** mit den Eigenschaften **[!UICONTROL Breite]** und **[!UICONTROL Höhe]** fest.

**[!UICONTROL Viewer-Vorgabe]** - Wählen Sie eine vorhandene Viewer-Vorgabe aus dem Dropdown-Menü aus. Wenn die gewünschte Viewer-Vorgabe nicht sichtbar ist, müssen Sie sie möglicherweise sichtbar machen. Siehe [Verwalten von Viewer-Vorgaben](/help/assets/managing-viewer-presets.md). Sie können keine Viewer-Vorgabe auswählen, wenn Sie eine Bildvorgabe verwenden und umgekehrt.

Dies ist die einzig verfügbare Option beim Anzeigen von Bildsets, Rotationssets oder Sets für gemischte Medien. Die angezeigten Viewer-Vorgaben sind ebenfalls intelligent. Es werden nur relevante Viewer-Vorgaben angezeigt.

**[!UICONTROL Bildvorgabe]** - Wählen Sie eine vorhandene Bildvorgabe aus dem Dropdown-Menü aus. Wenn die gewünschte Bildvorgabe nicht sichtbar ist, müssen Sie sie möglicherweise sichtbar machen. Siehe [Verwalten von Bildvorgaben](/help/assets/managing-image-presets.md). Sie können keine Viewer-Vorgabe auswählen, wenn Sie eine Bildvorgabe verwenden und umgekehrt.

Diese Option ist beim Anzeigen von Bildsets, Rotationssets oder Sets für gemischte Medien nicht verfügbar.

**[!UICONTROL Bild-Modifikatoren]** - Sie können Bildeffekte ändern, indem Sie zusätzliche Bildbefehle bereitstellen. Diese werden unter [Verwalten von Bildvorgaben](/help/assets/managing-viewer-presets.md) und [Befehlsreferenz](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference.html?lang=de).

Diese Option ist beim Anzeigen von Bildsets, Rotationssets oder Sets für gemischte Medien nicht verfügbar.

**[!UICONTROL Haltepunkte]** - Wenn Sie dieses Asset auf einer responsiven Site verwenden, müssen Sie die Seitenhaltepunkte hinzufügen. Bildhaltepunkte müssen durch Kommas (,) getrennt werden. Diese Option kann verwendet werden, wenn in einer Bildvorgabe keine Höhe oder Breite festgelegt ist.

Diese Option ist beim Anzeigen von Bildsets, Rotationssets oder Sets für gemischte Medien nicht verfügbar.

Sie können die folgenden [!UICONTROL erweiterten Einstellungen] bearbeiten, indem Sie in der Komponente auf **[!UICONTROL Bearbeiten]** klicken.

**[!UICONTROL Titel]** - Ändern Sie den Titel des Bildes.

**[!UICONTROL Alternativtext]** - Fügen Sie dem Bild einen Titel für die Benutzer hinzu, deren Grafiken deaktiviert sind.

Diese Option ist beim Anzeigen von Bildsets, Rotationssets oder Sets für gemischte Medien nicht verfügbar.

**[!UICONTROL URL, Öffnen in]** - Sie können ein Asset in festlegen, um einen Link zu öffnen. Legen Sie die **[!UICONTROL URL]** und **[!UICONTROL Öffnen in]** fest, um anzugeben, ob die Seite im selben Fenster oder in einem neuen Fenster geöffnet werden soll.

Diese Option ist beim Anzeigen von Bildsets, Rotationssets oder Sets für gemischte Medien nicht verfügbar.

**[!UICONTROL Breite und Höhe]** - Geben Sie einen Wert in Pixel an, wenn das Bild eine feste Größe aufweisen soll. Wenn die Werte leer gelassen werden, ist das Asset adaptiv.

#### Arbeiten mit Videos {#when-working-with-video}

Verwenden Sie die Komponente [!UICONTROL Dynamic Media], um Ihren Web-Seiten dynamische Videos hinzuzufügen. Beim Bearbeiten der Komponente können Sie eine vordefinierte Video-Viewer-Vorgabe für das Wiedergeben des Videos auf der Seite verwenden.

![chlimage_1-74](assets/chlimage_1-74.png)

Sie können die folgenden [!UICONTROL Einstellungen für Dynamic Media] bearbeiten, indem Sie in der Komponente auf **[!UICONTROL Bearbeiten]** klicken.

>[!NOTE]
>
>Die Videokomponente für Dynamic Media ist standardmäßig adaptiv. Wenn sie eine feste Größe aufweisen soll, müssen Sie dies in der Komponente auf der Registerkarte **[!UICONTROL Erweitert]** mit **[!UICONTROL Breite]** und **[!UICONTROL Höhe]** festlegen.

**[!UICONTROL Viewer-Vorgabe]** - Wählen Sie eine vorhandene Video-Viewer-Vorgabe aus dem Dropdown-Menü aus. Wenn die gewünschte Viewer-Vorgabe nicht sichtbar ist, müssen Sie sie möglicherweise sichtbar machen. Siehe [Verwalten von Viewer-Vorgaben](/help/assets/managing-viewer-presets.md).

Sie können die folgenden [!UICONTROL erweiterten] Einstellungen bearbeiten, indem Sie in der Komponente auf **[!UICONTROL Bearbeiten]** klicken.

**[!UICONTROL Titel]** - Ändern Sie den Titel des Videos.

**[!UICONTROL Breite und Höhe]** - Geben Sie einen Wert in Pixel an, wenn das Video eine feste Größe aufweisen soll. Wenn die Werte leer gelassen werden, wird es adaptiv.

#### Sicheres Video bereitstellen {#how-to-delivery-secure-video}

In AEM 6.2 bei der Installation [FP-13480](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq620/featurepack/cq-6.2.0-featurepack-13480)können Sie steuern, ob ein Video über eine sichere SSL-Verbindung (HTTPS) oder eine unsichere Verbindung (HTTP) bereitgestellt wird. Standardmäßig wird das Videobereitstellungsprotokoll automatisch vom Protokoll der eingebetteten Webseite übernommen. Wenn die Webseite über HTTPS geladen wird, wird das Video ebenfalls über HTTPS wiedergegeben. Umgekehrt wird das Video über HTTP bereitgestellt, wenn sich die Webseite auf HTTP befindet. In den meisten Fällen ist dieses Standardverhalten korrekt und es müssen keine Konfigurationsänderungen vorgenommen werden. Sie können dieses Standardverhalten jedoch außer Kraft setzen, indem Sie `VideoPlayer.ssl=on` an das Ende eines URL-Pfads oder an die Liste anderer Viewer-Konfigurationsparameter in einem Einbettungscode-Snippet, um eine sichere Videobereitstellung zu erzwingen.

Weitere Informationen zur sicheren Videowiedergabe sowie zur Verwendung des Konfigurationsattributs `VideoPlayer.ssl` in Ihrem URL-Pfad finden Sie im Referenzhandbuch zu den Viewern unter [Sichere Videowiedergabe](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/c-html5-video-viewer-20-securevideodelivery.html?lang=de). Neben dem Video-Viewer ist die sichere Videowiedergabe auch für den Viewer für gemischte Medien und den Viewer für interaktive Videos verfügbar.

### Interaktive Medienkomponente {#interactive-media-component}

Die interaktive Medienkomponente eignet sich für Assets, die interaktiv sind, wie Hotspots oder Imagemaps. Wenn Sie über ein interaktives Bild, interaktives Video oder Karussellbanner verfügen, verwenden Sie die **[!UICONTROL Interaktive Medien]** -Komponente.

Die Komponente [!UICONTROL Interaktive Medien] ist eine intelligente Komponente. Je nachdem, ob Sie ein Bild oder Video hinzufügen, werden Ihnen unterschiedliche Optionen zur Verfügung gestellt. Darüber hinaus ist der Viewer responsiv. Das heißt, die Größe des Bildschirms ändert sich automatisch entsprechend der Bildschirmgröße. Bei allen Viewern handelt es sich um HTML5-Viewer.

![chlimage_1-75](assets/chlimage_1-75.png)

Sie können die folgenden **[!UICONTROL allgemeinen]** Einstellungen bearbeiten, indem Sie in der Komponente auf **[!UICONTROL Bearbeiten]** klicken.

**[!UICONTROL Viewer-Vorgabe]** - Wählen Sie eine vorhandene Viewer-Vorgabe aus dem Dropdown-Menü aus. Wenn die gewünschte Viewer-Vorgabe nicht sichtbar ist, müssen Sie sie möglicherweise sichtbar machen. Viewer-Vorgaben müssen veröffentlicht werden, bevor sie verwendet werden können. Siehe „Verwalten von Viewer-Vorgaben“.

**[!UICONTROL Titel]** - Ändern Sie den Titel des Videos.

**[!UICONTROL Breite und Höhe]** - Geben Sie einen Wert in Pixel an, wenn das Video eine feste Größe aufweisen soll. Wenn die Werte leer gelassen werden, wird es adaptiv.

Sie können die folgenden Einstellungen von **[!UICONTROL Zu Warenkorb hinzufügen]** bearbeiten, indem Sie in der Komponente auf **[!UICONTROL Bearbeiten]** klicken.

**[!UICONTROL Produkt-Asset anzeigen]** - Standardmäßig ist dieser Wert ausgewählt. Das Produkt-Asset zeigt ein Bild des Produkts an, wie im Commerce-Modul definiert. Deaktivieren Sie das Kontrollkästchen, um das Produkt-Asset nicht anzuzeigen.

**[!UICONTROL Produktpreis anzeigen]** - Standardmäßig ist dieser Wert ausgewählt. Der Produktpreis zeigt den Preis des Artikels entsprechend der Definition im Commerce-Modul an. Deaktivieren Sie das Kontrollkästchen, um den Produktpreis nicht anzuzeigen.

**[!UICONTROL Produktformular anzeigen]** - Standardmäßig ist dieser Wert nicht ausgewählt. Das Produktformular enthält alle Produktvarianten wie Größe und Farbe. Deaktivieren Sie das Kontrollkästchen, um die Produktvarianten nicht anzuzeigen.
