---
title: Einbetten des Dynamic Media-Video- oder Bild-Viewers auf einer Web-Seite
seo-title: Embedding the Dynamic Media Video or Image viewer on a web page
description: Erfahren Sie, wie Sie Dynamic Media-Videos oder -Bilder auf einer Web-Seite einbetten.
seo-description: Learn how to embed Dynamic media video or images on a web page
uuid: 6f786521-eb6c-4c80-8c15-9bf97b56818f
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 4ae76d8a-208f-4099-9f17-a94df424685e
exl-id: bff564a8-e982-4e1a-a9b5-05e44e3e4d46
feature: Components
role: User
source-git-commit: cc9b6d147a93688e5f96620d50f8fc8b002e2d0d
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 95%

---

# Einbetten des Dynamic Media-Video- oder Bild-Viewers auf einer Web-Seite {#embedding-the-video-or-image-viewer-on-a-web-page}

Verwenden Sie die Funktion **[!UICONTROL Einbettungs-Code]**, wenn Sie ein Video wiedergeben oder ein Asset anzeigen möchten, das auf einer Web-Seite eingebettet wurde. Kopieren Sie den Einbettungs-Code in die Zwischenablage, damit Sie ihn in die Web-Seiten einfügen können. Der Code kann im Dialogfeld **[!UICONTROL Einbettungs-Code]** nicht bearbeitet werden.

Betten Sie URLs nur dann ein, wenn Sie _nicht_ als Ihr WCM verwenden. [!DNL Experience Manager] Wenn Sie [!DNL Experience Manager] als WCM verwenden, [Sie fügen die Assets direkt auf Ihrer Seite hinzu.](adding-dynamic-media-assets-to-pages.md)

Siehe [Verknüpfen von URLs mit einer Web-Anwendung](linking-urls-to-yourwebapplication.md).

Siehe [Bereitstellen von optimierten Bildern für eine responsive Site](responsive-site.md).

>[!NOTE]
>
>Der eingebettete Code kann erst kopiert werden, nachdem Sie das ausgewählte Asset veröffentlicht haben. Darüber hinaus müssen Sie die Viewer-Vorgabe oder die Bildvorgabe veröffentlichen.
>
>Siehe [Veröffentlichen von Assets](publishing-dynamicmedia-assets.md).
>
>Siehe [Veröffentlichen von Viewer-Vorgaben](managing-viewer-presets.md#publishing-viewer-presets).
>
>Siehe [Veröffentlichen von Bildvorgaben](managing-image-presets.md#publishing-image-presets).

**So betten Sie den Dynamic Media-Video- oder Bild-Viewer auf einer Web-Seite ein**:

1. Navigieren Sie zum *veröffentlichten* Video- oder Bild-Asset, dessen Einbettungs-Code Sie kopieren möchten.

   Denken Sie daran, dass der Einbettungscode nur *nach* der ersten *Veröffentlichung* der Assets kopiert werden können. Darüber hinaus müssen die Viewer-Vorgabe oder die Bildvorgabe ebenfalls veröffentlicht werden.

   Siehe [Veröffentlichen von Assets](publishing-dynamicmedia-assets.md).

   Siehe [Veröffentlichen von Viewer-Vorgaben](managing-viewer-presets.md#publishing-viewer-presets).

   Siehe [Veröffentlichen von Bildvorgaben](managing-image-presets.md#publishing-image-presets).

1. Wählen Sie in der linken Leiste das Dropdown-Menü aus und tippen Sie auf **[!UICONTROL Viewer]**.
1. Tippen Sie auf der linken Schiene auf den Namen einer Viewer-Vorgabe. Die Viewer-Vorgabe wird auf das Asset angewendet.
1. Tippen Sie auf **[!UICONTROL Einbetten]**.
1. Kopieren Sie im Dialogfeld **[!UICONTROL Einbettungs-Code]** den gesamten Code in die Zwischenablage und tippen Sie dann auf **[!UICONTROL Schließen]**.
1. Fügen Sie den Integrations-Code in die Web-Seiten ein.

## Verwenden von HTTP/2 zur Bereitstellung von Dynamic Media-Assets   {#using-http-to-deliver-your-dynamic-media-assets}

HTTP/2 ist das neue, aktualisierte Web-Protokoll, das die Kommunikation zwischen Browser und Servern verbessert. Es beschleunigt die Übertragung von Informationen und reduziert die erforderliche Prozessorleistung. Es ist jetzt möglich, Dynamic Media-Assets über HTTP/2 bereitzustellen, das schnellere Reaktions- und Ladezeiten bietet.

Vollständige Informationen zu den ersten Schritten mit HTTP/2 und Ihrem Dynamic Media-Konto finden Sie unter [Bereitstellung von Inhalt über HTTP/2](http2.md).
