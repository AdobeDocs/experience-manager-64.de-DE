---
title: Bereitstellen von optimierten Bildern für eine responsive Site
seo-title: Bereitstellen von optimierten Bildern für eine responsive Site
description: Anleitung zur Bereitstellung optimierter Bilder mit der responsiven Codefunktion
seo-description: Anleitung zur Bereitstellung optimierter Bilder mit der responsiven Codefunktion
uuid: 7c6baef5-7513-4644-94ed-2383e8724c17
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 5edcc765-c374-4368-a0d9-e02a713a24f2
translation-type: tm+mt
source-git-commit: 8c6fdcea0def7720062edfc564c536f8d47e8402

---


# Bereitstellen von optimierten Bildern für eine responsive Website {#delivering-optimized-images-for-a-responsive-site}

Verwenden Sie die Funktion für responsiven Code, wenn Sie den Code für responsive Verarbeitung für den Webentwickler freigeben möchten. You copy the responsive (**[!UICONTROL RESS]**) code to the clipboard so you can share it with the web developer.

Verwenden Sie diese Funktion, wenn sich Ihre Website auf einem Drittanbieter-WCM befindet. Wenn sich Ihre Website jedoch auf AEM befindet, rendert ein Offsite-Image-Server das Bild und stellt es der Webseite bereit.

Informationen hierzu finden Sie unter [Einbetten des Video-Viewers auf einer Webseite](embed-code.md).

Siehe auch [Verknüpfen von URLs mit einer Webanwendung](linking-urls-to-yourwebapplication.md).

**So stellen Sie optimierte Bilder für eine responsive Site bereit**:

1. Navigate to the image you want supply responsive code for and in the drop-down menu, tap **[!UICONTROL Renditions]**.

   ![chlimage_1-408](assets/chlimage_1-408.png)

1. Wählen Sie eine Voreinstellung für interaktive Bilder aus. Die Schaltflächen **[!UICONTROL URL]** und **[!UICONTROL RESS]** werden angezeigt.

   ![chlimage_1-409](assets/chlimage_1-409.png)

   >[!NOTE]
   >
   >Das ausgewählte Asset *und* die ausgewählte Bildvoreinstellung bzw. Viewer-Voreinstellung müssen veröffentlicht werden, damit die Schaltflächen **[!UICONTROL URL]** oder **[!UICONTROL RESS]** verfügbar sind.
   >
   >Dynamische Medien - Im Hybridmodus müssen Sie Bildvorgaben veröffentlichen. Dynamische Medien - Im Scene7-Modus werden Bildvorgaben automatisch veröffentlicht.

1. Tippen Sie auf **[!UICONTROL Energiespeichersystem]**.

   ![chlimage_1-410](assets/chlimage_1-410.png)

1. Wählen Sie im Dialogfeld &quot;Responsive Bilder **[!UICONTROL einbetten]** &quot;den interaktiven Code-Text aus und kopieren Sie ihn in Ihre Website, um auf das interaktive Asset zuzugreifen.
1. Bearbeiten Sie die Standard-Breakpoints im Integrationscode, damit sie denen der responsiven Website direkt im Code entsprechen. Testen Sie außerdem die verschiedenen Bildauflösungen bei verschiedenen Seiten-Breakpoints.

## Bereitstellen von Dynamic Media-Assets mit HTTP/2 {#using-http-to-delivery-your-dynamic-media-assets}

HTTP/2 ist das neue, aktualisierte Webprotokoll, das die Kommunikation zwischen Browser und Servern verbessert. Es beschleunigt die Übertragung von Informationen und reduziert die erforderliche Prozessorleistung. Die Bereitstellung von Dynamic Media Assets kann über HTTP/2 erfolgen, das schnellere Antwort- und Ladezeiten bietet.

Vollständige Informationen zu den ersten Schritten mit HTTP/2 und Ihrem Dynamic Media-Konto finden Sie unter [Bereitstellung von Inhalt über HTTP/2](http2.md).
