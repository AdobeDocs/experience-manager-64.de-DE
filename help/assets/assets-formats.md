---
title: Unterstützte Dateiformate in [!DNL Experience Manager] Assets
description: Liste der von Assets unterstützten Dateiformate und MIME-Typen sowie der für jedes Format unterstützten Funktionen.
contentOwner: AG
feature: Asset Management,Renditions
role: User,Admin
exl-id: ee25fe8f-36fb-42b3-9f90-0ea77bc02e2f
source-git-commit: cc47644419f7b7f4f1f00bb848050aa4a98efa09
workflow-type: tm+mt
source-wordcount: '1645'
ht-degree: 62%

---

# Unterstützte Dateiformate in [!DNL Adobe Experience Manager Assets] {#assets-supported-formats}

[!DNL Experience Manager Assets] unterstützt eine breite Palette von Dateiformaten und jede Funktionalität bietet unterschiedliche Unterstützung für verschiedene MIME-Typen.

Integration [!DNL Assets] Verwenden Sie zusammen mit anderen standardkonformen DAM-Lösungen (Digital Asset Management) und Desktop-Software die Extensible Metadata Platform (XMP) von Adobe.

Die Legende gibt den Grad der Unterstützung an.

| Unterstützungsebene | Beschreibung |
|:---:|---|
| ✓ | Unterstützt |
| &#42; | Mit Funktionen von Zusatzmodulen unterstützt |
| − | Nicht zutreffend |

## Raster-Bildformate {#supported-raster-image-formats}

Folgende Rasterbildformate werden für Asset-Management-Funktionen unterstützt:

| Format | Speicherung | Metadatenverwaltung | Metadatenextraktion | Generierung von Miniaturen | Interaktive Bearbeitung | Metadaten-Writeback | Insights |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| PNG | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| GIF | ✓ | ✓ | ✓ | ✓ | ✓ |  | ✓ |
| TIFF | ✓ | ✓ | ✓ | ✓ |  | ✓ | ✓ |
| JPEG | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| BMP | ✓ | ✓ | ✓ | ✓ | ✓ |  | ✓ |
| PNM | ✓ | ✓ |  |  |  |  | ✓ |
| PGM | ✓ | ✓ |  |  |  |  | ✓ |
| PBM | ✓ | ✓ |  |  |  |  | ✓ |
| PPM | ✓ | ✓ |  |  |  |  | ✓ |
| PSD **‡** | ✓ | ✓ | ✓ | ✓ |  |  | ✓ |
| [EPS](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ | ✓ | ✓ | ✓ |  | ✓ |  |
| PICT |  |  |  |  |  |  | ✓ |
| PSB | ✓ | ✓ | ✓ | ✓ |  |  |  |

**‡** Das zusammengeführte Bild wird aus der PSD-Datei extrahiert. Dabei handelt es sich um ein von Adobe Photoshop generiertes Bild, das in der PSD enthalten ist. Je nach den Einstellungen kann dieses Bild das eigentliche Bild sein oder nicht.

Folgende Rasterbildformate werden für Dynamic Media-Funktionen unterstützt:

| Format | Hochladen<br> (Eingabeformat) | Erstellen<br> image<br> preset<br> (Ausgabeformat) | Vorschau<br> dynamisch<br> Ausgabedarstellung | Versand<br> dynamisch<br> Ausgabedarstellung | Download<br> dynamisch<br> Ausgabedarstellung |
|---|:---:|:---:|:---:|:---:|:---:|
| PNG | ✓ | ✓ | ✓ | ✓ | ✓ |
| GIF | ✓ | ✓ | ✓ | ✓ | ✓ |
| TIFF | ✓ | ✓ | ✓ | ✓ | ✓ |
| JPEG | ✓ | ✓ | ✓ | ✓ | ✓ |
| BMP | ✓ |  |  |  |  |
| PNM |  |  |  |  |  |
| PGM |  |  |  |  |  |
| PBM |  |  |  |  |  |
| PPM |  |  |  |  |  |
| PSD **‡** | ✓ |  |  |  |  |
| [EPS](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ | ✓ | ✓ | ✓ | ✓ |
| PICT | ✓ |  |  |  |  |
| PSB |  |  |  |  |  |

**‡** Das zusammengeführte Bild wird aus der PSD-Datei extrahiert. Dabei handelt es sich um ein von Adobe Photoshop generiertes Bild, das in der PSD enthalten ist. Je nach den Einstellungen kann dieses Bild das eigentliche Bild sein oder nicht.

Berücksichtigen Sie zusätzlich zu den oben genannten Informationen Folgendes:

* Die Unterstützung für EPS-Dateien gilt nur für Rasterbilder. Zum Beispiel wird die Erstellung von Miniaturansichten für Vektorbilder im EPS-Format nicht standardmäßig unterstützt. Um die Unterstützung hinzuzufügen, [konfigurieren Sie ImageMagick](best-practices-for-imagemagick.md). Informationen zur Integration von Drittanbieter-Tools zur Aktivierung zusätzlicher Funktionen finden Sie unter [Befehlszeilenbasierter Medien-Handler](media-handlers.md#command-line-based-media-handler).

* Metadaten-Writeback funktioniert für das PSB-Dateiformat, wenn es zum `NComm` Handler.

* Um mithilfe von Dynamic Media dynamische Ausgaben für EPS-Dateien in der Vorschau anzuzeigen und zu generieren, informieren Sie sich unter [Dateiformate Adobe Illustrator (AI), Postscript (EPS) und PDF](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats).

* Metadaten-Writeback für EPS-Dateien wird ab Version 3.0 von PostScript Document Structuring Convention (PS-Adobe) unterstützt.

## Nicht unterstützte Rasterbildformate in Dynamic Media {#unsupported-image-formats-dynamic-media}

In der folgenden Liste werden die Untertypen von Rasterbilddateiformaten beschrieben, die *not* unterstützt in Dynamic Media.

Siehe auch [Erkennung nicht unterstützter Dateiformate für Dynamic Media](https://helpx.adobe.com/experience-manager/kb/detect-unsupported-assets-for-dynamic-media.html).

* PNG-Dateien mit einer IDAT-Blockgröße größer als 100 MB.
* PSB-Dateien.
* PSD-Dateien mit einem anderen Farbraum als CMYK, RGB, Graustufen oder Bitmap werden nicht unterstützt. DuoTone-, Lab- und indizierte Farbräume werden nicht unterstützt.
* PSD-Dateien mit einer Bittiefe größer als 16.
* TIFF-Dateien mit Gleitkommadaten.
* TIFF-Dateien mit Lab-Farbraum.

## PDF Rasterizer-Bibliothek {#supported-pdf-rasterizer-library}

Die Adobe PDF Rasterizer-Bibliothek generiert hochwertige Miniaturansichten und Vorschauen für große und ressourcenintensive Adobe Illustrator- und PDF-Dateien. Adobe empfiehlt die Verwendung der PDF Rasterizer-Bibliothek für folgende Dateien:

* Inhaltsintensive KI-/PDF-Dateien, die ressourcenintensiv verarbeitet werden können.
* AI-/PDF-Dateien, für die standardmäßig keine Miniaturansichten generiert werden.
* AI-Dateien mit PMS-Farben (Pantone Matching System)

Siehe [Verwenden von PDF Rasterizer](aem-pdf-rasterizer.md).

## Imaging Transcoding Library {#supported-image-transcoding-library}

Die Adobe Imaging Transcoding Library ist eine Bildverarbeitungslösung, die zentrale Bildbearbeitungsfunktionen wie Kodierung, Transkodierung, Neuberechnung und Größenanpassung durchführt.

Die Imaging Transcoding Library unterstützt die Typen JPG/JPEG, PNG (8-Bit und 16-Bit), GIF, BMP, TIFF/Komprimiertes TIFF (außer 32-Bit-TIFF-Dateien und PTIFF-Dateien), ICO und ICN MIME.

Siehe [Imaging Transcoding Library](imaging-transcoding-library.md).

## Camera Raw {#supported-camera-raw}

Die Adobe Camera Raw-Bibliothek aktiviert [!DNL Assets] , um Rohbilder aufzunehmen. Siehe [Camera Raw Unterstützung](camera-raw.md).

## Dokumentenformate {#supported-document-formats}

Folgende Dokumentenformate werden für Asset-Management-Funktionen unterstützt:

| Format | Speicherung | Metadaten<br> management | Volltext<br> Extraktion | Metadaten<br> Extraktion | Miniatur<br> generation | Teil-Asset<br> Extraktion | Metadaten<br> Writeback |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| [AI](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ | ✓ |  | ✓ | ✓ | ✓ | ✓ |
| DOC | ✓ | ✓ | ✓ | ✓ |  |  |  |
| DOCX | ✓ | ✓ | ✓ | ✓ |  |  |  |
| ODT | ✓ | ✓ | ✓ |  |  |  |  |
| [PDF](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| HTML | ✓ | ✓ | ✓ |  |  |  |  |
| RTF | ✓ | ✓ | ✓ |  |  |  |  |
| TXT | ✓ | ✓ | ✓ |  |  |  |  |
| XLS | ✓ | ✓ | ✓ |  |  |  |  |
| XLSX | ✓ | ✓ | ✓ | ✓ |  |  |  |
| ODS | ✓ | ✓ | ✓ |  |  |  |  |
| PPT | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| PPTX | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| ODP | ✓ | ✓ | ✓ |  |  |  |  |
| [INDD](managing-image-presets.md#indesign-indd-file-format) | ✓ | ✓ |  | ✓ | ✓ | ✓ | ✓ |
| PS | ✓ | ✓ |  |  |  |  |  |
| QXP | ✓ | ✓ |  |  |  |  |  |
| EPUB | ✓ | ✓ |  | ✓ | ✓ |  |  |

Folgende Dokumentenformate werden für Dynamic Media-Funktionen unterstützt:

| Format | Hochladen<br> (Eingabeformat) | Erstellen<br> image<br> preset<br> (Ausgabeformat) | Vorschau<br> dynamisch<br> Ausgabedarstellung | Versand<br> dynamisch<br> Ausgabedarstellung | Download<br> dynamisch<br> Ausgabedarstellung |
|---|:---:|:---:|:---:|:---:|:---:|
| [KI](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ |  |  |  |  |
| DOC |  |  |  |  |  |
| DOCX |  |  |  |  |  |
| ODT |  |  |  |  |  |
| [PDF](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) (Siehe Hinweis unten) | ✓ | ✓ | ✓ | ✓ | ✓ |
| HTML |  |  |  |  |  |
| RTF |  |  |  |  |  |
| TXT |  |  |  |  |  |
| XLS |  |  |  |  |  |
| XLSX |  |  |  |  |  |
| ODS |  |  |  |  |  |
| PPT |  |  |  |  |  |
| PPTX |  |  |  |  |  |
| ODP |  |  |  |  |  |
| [INDD](managing-image-presets.md#indesign-indd-file-format) | ✓ |  |  |  |  |
| PS |  |  |  |  |  |
| QXP |  |  |  |  |  |
| ePub |  |  |  |  |  |

>[!NOTE]
>
>Bei sicheren PDF wird nur das Hochladen unterstützt.

Berücksichtigen Sie zusätzlich zu den oben genannten Funktionen Folgendes:

* Um mithilfe von Dynamic Media dynamische Ausgaben für PDF-Dateien zu generieren, informieren Sie sich unter [Adobe Illustrator (AI)-, PostScript (EPS)- und PDF-Dateiformate.](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)

* Um mithilfe von Dynamic Media dynamische Ausgaben für AI-Dateien in der Vorschau anzuzeigen und zu generieren, informieren Sie sich unter [Adobe Illustrator (AI)-, PostScript (EPS)- und PDF-Dateiformate.](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) 

* Informationen zum Generieren dynamischer Ausgabeformate für INDD-Dateien mit Dynamic Media finden Sie unter [Dateiformat InDesign (INDD)](../assets/managing-image-presets.md#indesign-indd-file-format).

## Multimediaformate {#supported-multimedia-formats}

| Format | Speicherung | Metadatenverwaltung | Metadatenextraktion | Generierung von Miniaturen | FFMPEG-Transkodierung |
|:---|:---:|:---:|:---:|:---:|:---:|
| AAC | ✓ | ✓ |  | - | &#42; |
| MIDI | ✓ | ✓ |  | - | &#42; |
| 3GP | ✓ | ✓ |  | - | &#42; |
| MP3 | ✓ | ✓ | ✓ | - | &#42; |
| MPG | ✓ | ✓ |  | - | &#42; |
| OGA | ✓ | ✓ |  | - | &#42; |
| OGG | ✓ | ✓ |  | - | &#42; |
| RA | ✓ | ✓ |  | - | &#42; |
| WAV | ✓ | ✓ |  | - | &#42; |
| WMA | ✓ | ✓ |  | - | &#42; |
| DVI | ✓ | ✓ |  | &#42; | &#42; |
| FLV | ✓ | ✓ |  | &#42; | &#42; |
| M4V | ✓ | ✓ |  | &#42; | &#42; |
| MPEG | ✓ | ✓ |  | &#42; | &#42; |
| OGV | ✓ | ✓ |  | &#42; | &#42; |
| MOV | ✓ | ✓ |  | &#42; | &#42; |
| WMV | ✓ | ✓ |  | &#42; | &#42; |
| SWF | ✓ | ✓ |  |  |  |

## Eingabevideoformate für die Dynamic Media-Transkodierung {#supported-input-video-formats-for-dynamic-media-transcoding}

| Videodateierweiterung | Container | Empfohlene Video-Codecs | Nicht unterstützte Video-Codecs |
|---|---|---|---|
| MP4 | MPEG-4 | H264/AVC (alle Profile) |  |
| MOV, QT | Apple QuickTime | H264/AVC, Apple ProRes422 &amp; HQ, Sony XDCAM, Sony DVCAM, HDV, Panasonic DVCPro, Apple DV (DV25), Apple PhotoJPEG, Sorenson, Avid DNxHD, Avid AVR | Apple Intermediate, Apple Animation |
| FLV, F4V | Adobe Flash | H264/AVC, Flix VP6, H263, Sorenson | SWF (Vektoranimationsdateien) |
| WMV | Windows Media 9 | WMV3 (v9), WMV2 (v8), WMV1 (v7), GoToMeeting (G2M2, G2M3, G2M4) | Microsoft Screen (MSS2), Microsoft Photo Story (WVP2) |
| MPG, VOB, M2V, MP2 | MPEG-2 | MPEG-2 |  |
| M4V | Apple iTunes | H264/AVC |  |
| AVI | A/V Interleave | XVID, DIVX, HDV, MiniDV (DV25), Techsmith Camtasia, Huffyuv, Fraps, Panasonic DVCPro | Indeo3 (IV30), MJPEG, Microsoft Video 1 (MS-CRAM) |
| WebM | WebM | Google VP8 |  |
| OGV, OGG | Ogg | Theora, VP3, Dirac |  |
| MXF | MXF | Sony XDCAM, MPEG-2, MPEG-4, Panasonic DVCPro |  |
| MTS | AVCHD | H264/AVC |  |
| MKV | Matroska | H264/AVC |  |
| R3D, RM | Red Raw Video | MJPEG 2000 |  |
| RAM, RM | RealVideo | Nicht unterstützt | Real G2 (RV20), Real 8 (RV30), Real 10 (RV40) |
| FLAC | Native Flac | Free Lossless Audio Codec |  |
| MJ2 | Motion JPEG2000 | Motion JPEG 2000 Codec |  |

## Archivformate {#supported-archive-formats}

Die unterstützten Archivformate und die Anwendbarkeit gemeinsamer DAM-Workflows werden in der folgenden Tabelle behandelt.

| Format | Speicherung | Versionierung | Workflow | Veröffentlichung | Zugriffssteuerung | Bereitstellung dynamischer Medien |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| TGZ | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| JAR | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| RAR | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| TAR | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| ZIP **†** | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |

**†** Das zusammengeführte Bild wird aus der PSD-Datei extrahiert. Dabei handelt es sich um ein von Adobe Photoshop generiertes Bild, das in der PSD enthalten ist. Je nach den Einstellungen kann dieses Bild das eigentliche Bild sein oder nicht. Die ZIP-Archive, die unter Verwendung des `Deflate64`-Algorithmus erstellt werden, werden in AEM nur begrenzt unterstützt. Archivierungs- und Archivierungsvorgänge werden nicht unterstützt. Jedoch werden Operationen wie das Laden, Navigieren und Herunterladen unterstützt.

## Weitere unterstützte Formate {#other-supported-formats}

Die Anwendbarkeit allgemeiner DAM-Workflows für einige weitere Dateiformate wird in der folgenden Tabelle beschrieben.

| Format | Speicherung | Versionierung | Workflow | Veröffentlichung | Zugriffssteuerung | Bereitstellung dynamischer Medien |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| **#** | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| SVG | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| CSS | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| VTT | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| XML | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| Javascript (wenn mit eigener Bereitstellungsdomäne konfiguriert) |  |  |  |  |  | ✓ |

**#** Die anderen Formate werden in DAM für Speicher, Versionierung, ACL, Workflow, Veröffentlichung und Metadatenverwaltung unterstützt.

## Unterstützte MIME-Typen {#supported-mime-types}

Standardmäßig [!DNL Experience Manager] erkennt den Dateityp mithilfe der Dateierweiterung. [!DNL Experience Manager] kann es aus dem Inhalt der Dateien erkennen. Wählen Sie für letztere die Option [!UICONTROL MIME aus Inhalt erkennen] Option in [!UICONTROL Day CQ DAM Mime Type Service] im [!DNL Experience Manager] Web-Konsole.

Eine Liste der unterstützten MIME-Typen finden Sie in CRXDE Lite unter `/conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`.

| Dateierweiterung | MIME-Typ/Internetmedientyp | Standardmäßiger jobParam-Wert | Zulässiger jobParam-Wert |
|---|---|---|---|
| Bild | image/s7asset | `usmAmount=1.75&usmRadius=0.2`<br>`&usmThreshold=2&usmMonochrome=0&` | Der standardmäßige jobParam-Wert gilt für alle Assets mit Bild-MIME-Typ.<ul><li>[knockoutBackgroundOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-knockout-background-options.html)</li><li>[manualCropOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-manual-crop-options.html)</li><li>[autoColorCropOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-auto-color-crop-options.html)</li><li>[autoTransparentCropOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-auto-transparent-crop-options.html)</li><li>[colorManagementOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-color-management-options.html)</li><li>[autoSetCreationOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-auto-set-creation-options.html)</li><li>[emailSetting](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/sting-constants/r-email-settings.html)</li><li>[xmpKeywords](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-xmp-keywords.html)</li><li>[unsharpMaskOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-unsharp-mask-options.html)</li></ul> |
| 3G2 | video/3gpp2 |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| 3GP | video/3gpp |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| AAC | audio/x-aac |  |  |
| AFM | application/x-font-type1 |  |  |
| AI | application/postscript | `aiprocess=Rasterize&airesolution=150`<br>`&aicolorspace=Auto&aialpha=false` | <ul><li>[postScriptOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-post-script-options.html)</li><li> [illustratorOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-illustrator-options.html)</li></ul> |
| AIFF | audio/x-aiff |  |  |
| AVI | video/x-msvideo |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| BMP | image/bmp |  |  |
| CSS | text/css |  |  |
| DOC | application/msword |  |  |
| EPS | <ul><li>application/postscript</li><li>application/eps</li><li>application/x-eps</li><li>image/eps</li><li>image/x-eps</li> |  |  |
| F4V | video/x-f4v |  | ExcludeMasterVideoFromAVS |
| FLA | application/x-shockwave-flash |  |  |
| FLV | video/x-flv |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| FPX | image/vnd.fpx |  |  |
| GIF | image/gif |  |  |
| ICC | application/vnd.iccprofile |  |  |
| ICM | application/vnd.iccprofile |  |  |
| INDD | application/x-indesign |  |  |
| JPEG | image/jpeg |  |  |
| JPG | image/jpeg |  |  |
| M2V | video/mpeg |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| M4V | video/x-m4v |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MOV | video/quicktime |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MP3 | audio/mpeg |  |  |
| MP4 | video/mp4 |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MPEG | video/mpeg |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MPG | video/mpeg |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MTS | model/vnd.mts |  |  |
| OGV | video/ogg |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| OTF | application/x-font-otf |  |  |
| PDF | application/pdf | `pdfprocess=Rasterize&resolution=150`<br>`&colorspace=Auto&pdfbrochure=false`<br>`&keywords=false&links=false` | [pdfOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-photoshop-options.html) |
| PFB | application/x-font-type1 |  |  |
| PFM | application/x-font-type1 |  |  |
| PICT | image/x-pict |  |  |
| PNG | image/png |  |  |
| PPT | application/vnd.ms-powerpoint |  |  |
| PS | application/postscript | `psprocess=Rasterize&psresolution=150`<br>`&pscolorspace=Auto&psalpha=false`<br>`&psextractsearchwords=false`<br>`&aiprocess=Rasterize&airesolution=150`<br>`&aicolorspace=Auto&aialpha=false` | <ul><li>[postScriptOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-post-script-options.html)</li><li>[illustratorOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-illustrator-options.html)</li></ul> |
| PSD | image/vnd.adobe.photoshop | `process=None&layerNaming=Layername`<br>`&anchor=Center&createTemplate=false`<br>`&extractText=false&extendLayers=false` | <ul><li>[photoshopOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-photoshop-options.html)</li><li>[photoshopLayerOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-photoshop-layer-options.html)</li></ul> |
| RTF | application/rtf |  |  |
| SVG | image/svg+xml |  |  |
| SWF | application/x-shockwave-flash |  |  |
| TAR | application/x-tar |  |  |
| TIF/TIFF | image/tiff |  |  |
| TTC | application/x-font-ttf |  |  |
| TTF | application/x-font-ttf |  |  |
| VOB | video/dvd |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| VTT | text/vtt |  |  |
| WAV | audio/x-wav |  |  |
| WEBM | video/webm |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| WMA | audio/x-ms-wma |  |  |
| WMV | video/x-ms-wmv |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| XLS | application/vnd.ms-excel |  |  |
| ZIP | application/zip |  |  |

>[!MORELIKETHIS]
>
>* [Unterstützung von MIME-typbasierten Assets/Dynamic Media Classic-Upload-Auftragsparametern aktivieren](/help/sites-administering/scene7.md#enabling-mime-type-based-assets-scene-upload-job-parameter-support).
>* [Konfigurieren der Unterstützung von MIME-Typen für Upload-Auftragsparametern](config-dynamic.md).

