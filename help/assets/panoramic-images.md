---
title: Panoramabilder
description: Erfahren Sie mehr über das Arbeiten mit interaktiven Bildern in Dynamic Media.
contentOwner: Rick Brough
topic-tags: dynamic-media
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
exl-id: 51150d51-865e-4b8e-9990-ca755e4c7778
feature: Panoramic Images
role: User
source-git-commit: 0120fe1303aa3b7f5aa7db39eaf40ff127f2e338
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 39%

---

# Panoramabilder {#panoramic-images}

In diesem Abschnitt wird beschrieben, wie Sie mit dem Viewer für Panoramabilder Kugelpanoramen für ein intensives 360°-Betrachtungserlebnis eines Zimmers, einer Immobilie, eines Ortes oder einer Landschaft ausgeben können.

Informationen hierzu finden Sie unter [Verwalten von Viewer-Vorgaben](managing-viewer-presets.md).

![panoramic-image2](assets/panoramic-image2.png)

## Hochladen von Assets für die Verwendung mit dem Viewer für Panoramabilder {#uploading-assets-for-use-with-the-panoramic-image-viewer}

Damit hochgeladene Assets als Kreispanoramen gelten und mit dem Viewer für Panoramabilder verwendet werden können, muss mindestens eine der beiden folgenden Eigenschaften zutreffen:

* Ein Seitenverhältnis von 2.

   Sie können die standardmäßige Seitenverhältniseinstellung von 2 in **[!UICONTROL CRXDE Lite]** unter:

   `/conf/global/settings/cloudconfigs/dmscene7/jcr:content`

* Mit den Keywords `equirectangular` oder `spherical` und `panorama` oder `spherical` und `panoramic` als Tags versehen. Weitere Informationen finden Sie unter [Verwenden von Tags](/help/sites-authoring/tags.md).

Die Kriterien für das Seitenverhältnis und die Keywords gelten für Panorama-Assets für die Asset-Detailseite und die **[!UICONTROL Panoramamedien]** -Komponente.

Weitere Informationen über den Upload von Assets für die Verwendung mit dem Viewer für Panoramabilder finden Sie unter [Hochladen von Assets](managing-assets-touch-ui.md#uploading-assets).

## Konfigurieren von Dynamic Media Classic {#configuring-dynamic-media-classic-scene}

Damit der Viewer für Panoramabilder in AEM ordnungsgemäß funktioniert, müssen Sie die Viewer-Vorgaben für Panoramabilder mit Dynamic Media Classic und Dynamic Media Classic-spezifischen Metadaten synchronisieren, damit die Viewer-Vorgaben im JCR aktualisiert werden. Konfigurieren Sie dazu Dynamic Media Classic wie folgt:

1. [Bei Ihrer Dynamic Media Classic-Desktop-Applikation anmelden](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/intro/dynamic-media-classic-desktop-app.html#system-requirements-dmc-app) für jedes Unternehmenskonto.

1. Klicken Sie oben rechts auf der Seite auf **[!UICONTROL Einstellungen > Anwendungseinstellungen > Veröffentlichungseinrichtung > Image-Server]**.
1. Im **[!UICONTROL Veröffentlichung zum Image-Server]** von der Seite **[!UICONTROL Veröffentlichungskontext]** Dropdown-Menü oben auswählen **[!UICONTROL Image Serving]**.

1. Im selben **[!UICONTROL Veröffentlichung zum Image-Server]** Seite, suchen Sie die Überschrift **[!UICONTROL Anforderungsattribute]**.
1. Unter dem **[!UICONTROL Anforderungsattribute]** Überschrift, suchen **[!UICONTROL Maximale Antwortbildgröße]**. Dann in der zugehörigen **[!UICONTROL Breite]** und **[!UICONTROL Höhe]** erhöhen Sie die maximal zulässige Bildgröße für Panoramabilder.

   Dynamic Media Classic ist auf 25.000.000 Pixel begrenzt. Die maximal zulässige Größe für Bilder mit einem Seitenverhältnis von 2:1 beträgt 7000 x 3500. In der Regel ist für Desktopbildschirme jedoch eine Größe von 4096 x 2048 Pixel ausreichend.

   >[!NOTE]
   >
   >Es werden nur Bilder innerhalb der zulässigen Maximalgröße unterstützt. Anfragen zu Bildern oberhalb der Obergrenze geben einen „403“-Fehler zurück.

1. Unter dem **[Anforderungsattribute]** -Überschrift, führen Sie folgende Schritte aus:

   * Satz **[!UICONTROL Verschleierungsmodus für Anfragen]** nach **[!UICONTROL Behinderte]**.
   * Satz **[!UICONTROL Sperrmodus für Anfragen]** nach **[!UICONTROL Behinderte]**.

   Diese Einstellungen sind für die Verwendung der **[!UICONTROL Panoramamedien]** -Komponente in AEM.

1. Am unteren Rand des **[!UICONTROL Veröffentlichung zum Image-Server]** Seite auf der linken Seite tippen Sie auf **[!UICONTROL Speichern]**.

1. Tippen Sie unten rechts auf **[!UICONTROL Schließen]**.

### Fehlerbehebung für die Komponente &quot;Panoramamedien&quot; {#troubleshooting-the-panoramic-media-wcm-component}

Wenn Sie ein Bild in der **[!UICONTROL Panoramamedien]** -Komponente in Ihrem WCM und der Komponenten-Platzhalter ausgeblendet sind, sollten Sie eine Fehlerbehebung für Folgendes durchführen:

* Wenn Ihnen ein 403-Fehler (Forbidden) angezeigt wird, liegt es möglicherweise daran, dass die angefragte Bildgröße den Grenzwert überschreitet. Überprüfen Sie die *Maximale Antwortbildgröße* Einstellungen in [Konfigurieren von Dynamic Media Classic](#configuring-dynamic-media-classic-scene).

* Für *Ungültige Sperre* im Asset oder *Parsing-Fehler* auf der Seite angezeigt werden, prüfen Sie **[!UICONTROL Verschleierungsmodus für Anfragen]** und **[!UICONTROL Sperrmodus für Anfragen]** , um sicherzustellen, dass sie deaktiviert sind.
* Richten Sie für einen Fehler mit einer beschädigten Arbeitsfläche einen **[!UICONTROL Pfad der Regeldefinitionsdatei und ungültige CTN]** für die vorherigen Anforderungen für das Bild-Asset.
* Wenn die Bildqualität infolge einer Bildanforderung mit einer Größe, die den unterstützten Bereich überschreitet, sehr gering wird, stellen Sie sicher, dass die Einstellung **[!UICONTROL JPEG-Codierungsattribute > Qualität]** nicht leer ist. Eine typische Einstellung für das Feld **[!UICONTROL Qualität]** ist `95`. Sie finden die Einstellung auf der **[!UICONTROL Veröffentlichung zum Image-Server]** Seite. Informationen zum Zugriff auf die Seite finden Sie unter [Konfigurieren von Dynamic Media Classic](#configuring-dynamic-media-classic-scene).

## Anzeigen einer Vorschau für Panoramabilder {#previewing-panoramic-images}

Weitere Informationen finden Sie im Abschnitt [Asset-Vorschau](previewing-assets.md).

## Veröffentlichen von Panoramabildern {#publishing-panoramic-images}

Siehe [Veröffentlichen von Assets](publishing-dynamicmedia-assets.md).
