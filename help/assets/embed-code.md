---
title: Einbetten des Video- oder Bild-Viewers für dynamische Medien in eine Webseite
seo-title: Einbetten des Video- oder Bild-Viewers für dynamische Medien in eine Webseite
description: Erfahren Sie, wie Sie Videos oder Bilder mit dynamischen Medien auf einer Webseite einbetten
seo-description: Erfahren Sie, wie Sie Videos oder Bilder mit dynamischen Medien auf einer Webseite einbetten
uuid: 6f786521-eb6c-4c80-8c15-9bf97b56818f
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 4ae76d8a-208f-4099-9f17-a94df424685e
translation-type: tm+mt
source-git-commit: 15d933a2e71a44e84cdcc9ae28f60c67b43bd8f4

---


# Embedding the Dynamic Media Video or Image viewer on a web page {#embedding-the-video-or-image-viewer-on-a-web-page}

Verwenden Sie die Funktion **[!UICONTROL Einbettungscode]**, wenn Sie das Video abspielen oder ein auf einer Webseite eingebettetes Asset anzeigen möchten. Kopieren Sie den Einbettungscode in die Zwischenablage, damit Sie ihn in Ihre Webseiten einfügen können. Die Bearbeitung des Codes ist im Dialogfeld **[!UICONTROL Einbettungscode]** nicht zulässig.

You embed URLs only if you are _not_ using AEM as your WCM. Wenn Sie AEM als Ihren WCM verwenden, [fügen Sie die Assets direkt zu Ihrer Seite hinzu](adding-dynamic-media-assets-to-pages.md).

See [Linking URLs to your Web Application.](linking-urls-to-yourwebapplication.md)

See [Delivering Optimized Images for a Responsive Site.](responsive-site.md)

>[!NOTE]
>
>Der eingebettete Code kann erst kopiert werden, nachdem Sie das ausgewählte Asset veröffentlicht haben. Darüber hinaus müssen Sie die Viewer-Vorgabe oder die Bildvorgabe veröffentlichen.
>
>Siehe [Veröffentlichen von Assets](publishing-dynamicmedia-assets.md).
>
>Siehe [Veröffentlichen von Viewer-Vorgaben](managing-viewer-presets.md#publishing-viewer-presets).
>
>Siehe [Veröffentlichen von Bildvorgaben](managing-image-presets.md#publishing-image-presets).

**So betten Sie den Video- oder Bild-Viewer für dynamische Medien auf einer Webseite** ein:

1. Navigate to the *published* video or image asset whose embed code you want to copy.

   Denken Sie daran, dass der Einbettungscode nur *nach* der ersten *Veröffentlichung* der Assets kopiert werden können. Darüber hinaus muss die Viewer- oder Bildvoreinstellung auch veröffentlicht werden.

   Siehe [Veröffentlichen von Assets](publishing-dynamicmedia-assets.md).

   Siehe [Veröffentlichen von Viewer-Vorgaben](managing-viewer-presets.md#publishing-viewer-presets).

   Siehe [Veröffentlichen von Bildvorgaben](managing-image-presets.md#publishing-image-presets).

1. In the left rail, select the drop-down menu and tap **[!UICONTROL Viewers]**.
1. Tippen Sie auf der linken Schiene auf einen Viewer-Vorgabennamen. Die Viewer-Vorgabe wird auf das Asset angewendet.
1. Tippen Sie auf **[!UICONTROL Einbetten]**.
1. In the **[!UICONTROL Embed Code]** dialog box, copy the entire code to the clipboard, and then tap **[!UICONTROL Close]**.
1. Fügen Sie den Integrationscode in die Webseiten ein.

## Verwendung von HTTP/2 zur Bereitstellung von Dynamic Media-Assets {#using-http-to-deliver-your-dynamic-media-assets}

HTTP/2 ist das neue, aktualisierte Webprotokoll, das die Kommunikation zwischen Browser und Servern verbessert. Es beschleunigt die Übertragung von Informationen und reduziert die erforderliche Prozessorleistung. Es ist jetzt möglich, Dynamic Media-Assets über HTTP/2 bereitzustellen, das schnellere Reaktions- und Ladezeiten bietet.

Vollständige Informationen zu den ersten Schritten mit HTTP/2 und Ihrem Dynamic Media-Konto finden Sie unter [Bereitstellung von Inhalt über HTTP/2](http2.md).
