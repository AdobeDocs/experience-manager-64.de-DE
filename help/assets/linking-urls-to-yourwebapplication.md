---
title: Verknüpfen von URLs mit einer Web-Anwendung
seo-title: Linking URLs to your Web Application
description: Verknüpfen von URLs mit einer Web-Anwendung in Dynamic Media
seo-description: How to link URLs to your web application in dynamic media
uuid: cf599e66-b1f9-40c0-b572-cea19f2e6793
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: d12e6ea3-aaf4-4672-9679-3c16c76d7d5b
exl-id: e076349d-8b1a-487f-b982-9440d7de13b9
feature: Configuration
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1308'
ht-degree: 91%

---

# Verknüpfen von URLs mit einer Web-Anwendung {#linking-urls-to-your-web-application}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Ihre Websites und Programme greifen über URL-Aufrufe auf Dynamic Media-Services zu. Wenn Sie ein Asset veröffentlichen, wird eine URL-Zeichenfolge, die auf das Asset verweist, von „Dynamic Media“ aktiviert. Sie können diese URLs zum Testen in einen Webbrowser einfügen.

Sie verknüpfen nur dann zu URLs, wenn Sie AEM *nicht* als Ihren WCM verwenden. Die Verknüpfung (im Gegensatz zur Einbettung) wird verwendet, wenn Sie einen Video-Player als Popup oder modales Fenster übermitteln möchten. Wenn Sie AEM als Ihren WCM verwenden, [fügen Sie die Assets direkt zu Ihrer Seite hinzu](adding-dynamic-media-assets-to-pages.md).

Um diese URL-Zeichenfolgen auf Ihren Web-Seiten und in Ihren Programmen zu platzieren, müssen Sie sie aus Dynamic Media kopieren.

>[!NOTE]
>
>URL-Zeichenfolgen sind nur für dynamische Ausgabedarstellungen von Assets verfügbar. Sie sind derzeit nicht für statische Assets verfügbar, die in DAM und nicht im Server für Dynamic Media aufbewahrt werden. Für statische Ausgabedarstellungen wird die URL-Schaltfläche nicht angezeigt.

Siehe auch [Einbetten des Video- oder Bild-Viewers auf einer Web-Seite.](embed-code.md)

Siehe auch [Verknüpfen von YouTube-URLs mit einer Web-Anwendung](video.md).

Siehe auch [Bereitstellen von optimierten Bildern für eine responsive Site.](responsive-site.md)

Informationen hierzu finden Sie auch unter [Hochladen von Assets.](managing-assets-touch-ui.md#uploading-assets)

## Abrufen einer URL für ein Asset     {#obtaining-a-url-for-an-asset}

Sie können eine URL-Zeichenfolge abrufen, die von einer Bildvorgabe oder einer Viewer-Vorgabe generiert wird. Wenn Sie die URL kopieren, wird sie in der Zwischenablage abgelegt, sodass Sie sie nach Bedarf in Seiten einer Website oder einem Programm einfügen können.

>[!NOTE]
>
>Die URL kann erst kopiert werden, wenn Sie das gewählte Asset veröffentlicht haben. Darüber hinaus müssen Sie die Viewer-Vorgabe oder die Bildvorgabe veröffentlichen.
>
>Siehe [Veröffentlichen von Assets](publishing-dynamicmedia-assets.md).
>
>Siehe [Veröffentlichen von Viewer-Vorgaben](managing-viewer-presets.md#publishing-viewer-presets).
>
>Siehe [Veröffentlichen von Bildvorgaben](managing-image-presets.md#publishing-image-presets).

Es gibt mehrere Möglichkeiten, eine URL-Zeichenfolge zu erhalten. Die folgenden Schritte zeigen Ihnen jedoch nur eine der Methoden, die Sie verwenden können.

**So rufen Sie eine URL für ein Asset ab**:

1. Navigieren Sie zum *veröffentlichten* Asset, dessen Bildvorgaben-URL oder Viewer-Vorgaben-URL Sie kopieren möchten, und tippen Sie auf das Asset, um es zu öffnen.

   Denken Sie daran, dass URLs erst kopiert werden können, *nachdem* Sie die Assets *veröffentlicht* haben. Darüber hinaus müssen die Viewer-Vorgabe oder die Bildvorgabe ebenfalls veröffentlicht werden.

   Siehe [Veröffentlichen von Assets](publishing-dynamicmedia-assets.md).

   Siehe [Veröffentlichen von Viewer-Vorgaben](managing-viewer-presets.md#publishing-viewer-presets).

   Siehe [Veröffentlichen von Bildvorgaben](managing-image-presets.md#publishing-image-presets).

1. Führen Sie je nach gewähltem Asset eine der folgenden Aktionen aus:

   * Wenn Sie ein Bild im Dropdown-Menü ausgewählt haben, tippen Sie auf **[!UICONTROL Ausgabedarstellungen]**.

      Tippen Sie unter der Überschrift **[!UICONTROL Dynamisch]** auf einen Vorgabennamen, um die zugehörige Ausgabedarstellung im rechten Rahmen anzuzeigen. Möglicherweise müssen Sie in der Liste der Ausgabedarstellungen einen Bildlauf durchführen, um die Überschrift „Dynamisch“ anzuzeigen.

      Tippen Sie unten in der linken Seitenleiste auf **[!UICONTROL URL]**.

      ![chlimage_1-270](assets/chlimage_1-270.png)

   * Wenn Sie ein Rotationsset, Bildset, Karussellset oder Video ausgewählt haben, tippen Sie im Dropdown-Menü auf **[!UICONTROL Viewer]**.

      Tippen Sie auf der linken Schiene auf den Namen einer Viewer-Vorgabe. Eine Vorschau des Sets oder Videos wird auf einer separaten Seite geöffnet.

      Tippen Sie auf der linken Leiste unten auf **[!UICONTROL URL]**.

      ![chlimage_1-271](assets/chlimage_1-271.png)

1. Markieren Sie den Text und kopieren Sie ihn in den Webbrowser, um eine Vorschau des Assets anzuzeigen oder es der Web-Inhaltsseite hinzuzufügen.

   Um das URL-Fenster zu verlassen, tippen Sie auf das **[!UICONTROL X]** oder auf **[!UICONTROL Schließen]**.

## Abrufen einer URL für ein statisches Asset {#obtaining-a-url-for-a-static-asset}

Dynamic Media unterstützt die Bereitstellung von statischen Assets, bei denen es sich um weitere Assets als nur Bilder und Videos handelt. Folgende unterstützte Formate von statischen Assets sind für die Bereitstellung verfügbar:

* Animiertes GIF
* Audiodateien
* CSS
* JavaScript (wenn das Unternehmen mit einer eigenen Domain konfiguriert wurde)
* PDF
* SVG
* XML
* ZIP

**So rufen Sie eine URL für ein statisches Asset ab**:

1. Navigieren Sie zum *veröffentlichten *statischen Asset, dessen URL Sie kopieren möchten, und tippen Sie auf das Asset, um es zu öffnen.

   Beachten Sie, dass URLs erst kopiert werden können, *nachdem* Sie das statische Asset *veröffentlicht* haben.

   Siehe [Veröffentlichen von Assets](publishing-dynamicmedia-assets.md).

1. Verwenden Sie eine der folgenden Methoden, um die URL für das veröffentlichte statische Asset abzurufen:

   * `The URL of the published static is the following:`

      * `https://*<server_name>*/is/content/*<company_name>*/*<static_asset_filename>*.*<extension>*`

         Beispiel: `https://aem.com/is/content/adobe/image.gif`.
   * Klicken Sie auf **[!UICONTROL Asset > Dynamische Ausgabeformate]** und tippen Sie dann auf ein dynamisches Ausgabeformat des statischen Assets und kopieren Sie die URL.

      Ändern Sie die kopierte URL, um `is/content` anstelle von `is/image/` im Pfad zu verwenden.


## Abrufen einer Video-URL für eine veröffentlichtes Videoausgabedarstellung {#obtaining-a-video-url-for-a-published-video-rendition}

1. Navigieren Sie in AEM zu **[!UICONTROL Tools > Bereitstellung > Cloud > Cloud Services]**.
1. Scrollen Sie auf der Seite **[!UICONTROL Cloud Services]** nach unten zur Überschrift **[!UICONTROL Dynamic Media Cloud Services]** und tippen Sie dann auf **[!UICONTROL Konfigurationen anzeigen]**.
1. Tippen Sie unter **[!UICONTROL Verfügbare Konfigurationen]** auf den Namen der gewünschten Konfiguration.

1. Kopieren Sie auf der Seite **[!UICONTROL Cloud-Einstellungen für Dynamic Media]** unter **[!UICONTROL Videodienst-URL]** den gesamten URL-Pfad. Sie benötigen den kopierten URL-Pfad später in den Schritten.

   Der URL-Pfad kann zum Beispiel folgendermaßen aussehen:

   `https://s7athens.macromedia.com:9090/DMGateway/`

   (Der oben angegebene Pfad dient nur zur Veranschaulichung. Es handelt sich nicht um den Pfad, den Sie kopieren.)

1. Kopieren Sie unter **[!UICONTROL Registrierungs-ID]** den Kundennamen im letzten Teil der ID.

   Beispiel: Für die Registrierungs-ID `87654321|MyCompany` lautet der Name des Kunden `MyCompany`.

1. Tippen Sie oben links auf der Seite auf **[!UICONTROL Cloud Service]s**, tippen Sie auf das AEM und navigieren Sie zu **[!UICONTROL Allgemein > CRXDE Lite]**.
1. Kopieren Sie den gesamten Pfad für die Videoausgabedarstellung aus dem JCR (Java Content Repository).

   Der Pfad für die Videoausgabedarstellung kann zum Beispiel folgendermaßen aussehen:

   `/_renditions_/0bd/0bd28743-a616-4fe6-92aa-6eae7c2112f/avs/Momentum_1080-0x720-2600k.mp4`

   (Der oben angegebene Pfad dient nur zur Veranschaulichung. Es handelt sich nicht um den Pfad, den Sie kopieren.)

1. Ordnen Sie die kopierten Informationen in der folgenden Reihenfolge an, um einen vollständigen URL-Pfad zu erstellen:

   `<Video_Service_URL>/public/<Customer_name_from_Registration_ID>/<Video_rendition_path>`

   Wenn Sie den Beispielpfad und den Beispiel-Kundennamen der vorherigen Schritte verwenden, sieht der vollständige Pfad folgendermaßen aus:

   `https://s7athens.macromedia.com:9090/DMGateway/public/MyCompany/_renditions_/0bd/0bd28743-a616-4fe6-92aa-6eae7c2112ff/avs/Momentum_1080-0x720-2600k.mp4`

   Dies ist die vollständige Video-URL für eine veröffentlichte Videoausgabedarstellung.

## Abrufen einer Video-URL für adaptives Streaming (HLS)  {#obtaining-a-video-url-for-adaptive-streaming-hls}

1. Navigieren Sie in AEM zu **[!UICONTROL Tools > Bereitstellung > Cloud > Cloud Services]**.
1. Scrollen Sie auf der Seite **[!UICONTROL Cloud Services]** nach unten zur Überschrift **[!UICONTROL Dynamic Media Cloud Services]** und tippen Sie dann auf **[!UICONTROL Konfigurationen anzeigen]**.
1. Tippen Sie unter **[!UICONTROL Verfügbare Konfigurationen]** auf den Namen der gewünschten Konfiguration.
1. Gehen Sie auf der Seite **[!UICONTROL Cloud Services-Einstellungen für Dynamic Media]** wie folgt vor:

   * Unter **[!UICONTROL Videodienst-URL]** kopieren Sie den gesamten URL-Pfad. Sie benötigen den kopierten URL-Pfad später in diesen Schritten. Der URL-Pfad kann zum Beispiel folgendermaßen aussehen:

   `https://gateway-na.assetsadobe.com/DMGateway/`

   (Der oben angegebene Pfad dient nur zur Veranschaulichung. Es handelt sich nicht um den Pfad, den Sie kopieren.)

   * Kopieren Sie unter **[!UICONTROL Registrierungs-ID]** den Kundennamen im letzten Teil der ID. Sie benötigen den kopierten Kundennamen später bei diesen Schritten.

      Beispiel: Für die Registrierungs-ID `87654321|demoCo` lautet der Name des Kunden, den Sie kopieren, `demoCo`.


1. Je nachdem, welches Videobereitstellungsprotokoll Sie verwenden möchten, kopieren Sie den entsprechenden Protokollselektor. Sie benötigen den kopierten Protokollselektor später in diesen Schritten.

   | Von Ihnen verwendetes Videobereitstellungsprotokoll | Zu verwendender Protokollselektor |
   |---|---|
   | HTTP   <br> Wenn Sie HTTP (unsichere Videobereitstellung) verwenden, müssen Sie in der Videodienst-URL, die Sie zuvor kopiert haben, „https“ in „http“ ändern. | `public/` |
   | HTTPS | `public-ssl/` |

1. Kopieren Sie den vollständigen Video-Asset-Pfad in AEM, wie mit Dynamic Media verarbeitet. Sie benötigen diesen kopierten Video-Asset-Pfad später in diesen Schritten.

   Beispiel:

   `/content/dam/marketing/MyVideo.mp4`

1. Kombinieren Sie alle Teile, die Sie zuvor kopiert haben, um eine Zeichenfolge in der folgenden Reihenfolge zu erstellen:

   &lt; `video service URL`>&lt; `protocol selector`>&lt; `customer name`>&lt; `video asset path`>

   Unter Verwendung der kopierten Informationen aus den obigen Beispielen würde die Zeichenfolge wie folgt aussehen:

   `https://gateway-na.assetsadobe.com/DMGateway/public-ssl/demoCo/content/dam/marketing/MyVideo.mp4`

1. Vervollständigen Sie die URL, indem Sie am Ende der Zeichenfolge `.m3u8` anhängen. Wenn beispielsweise `.m3u8` aus dem vorherigen Schritt an die Zeichenfolge angehängt wird, würde der vollständige URL-Pfad wie folgt aussehen:

   `https://gateway-na.assetsadobe.com/DMGateway/public-ssl/demoCo/content/dam/marketing/MyVideo.mp4.m3u8`

## Verwenden von HTTP/2 zur Bereitstellung von Dynamic Media-Assets   {#using-http-to-deliver-your-dynamic-media-assets}

HTTP/2 ist das neue, aktualisierte Web-Protokoll, das die Kommunikation zwischen Browser und Servern verbessert. Es beschleunigt die Übertragung von Informationen und reduziert die erforderliche Prozessorleistung. Die Bereitstellung von Dynamic Media-Assets kann über HTTP/2 erfolgen, das schnellere Antwort- und Ladezeiten bietet.

Siehe [Bereitstellung von Inhalt über HTTP/2](http2.md), um ausführliche Informationen zu den ersten Schritten mit HTTP/2 mit Ihrem Dynamic Media-Konto zu erhalten.
