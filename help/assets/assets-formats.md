---
title: In AEM Assets unterstützte Dateiformate
description: Liste der von AEM Assets unterstützten Dateiformate und MIME-Typen sowie der für jedes Format unterstützten Funktionen.
contentOwner: AG
feature: Asset-Management,Ausgabeformate
role: User,Admin
exl-id: ee25fe8f-36fb-42b3-9f90-0ea77bc02e2f
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '1651'
ht-degree: 64%

---

# Unterstützte Dateiformate in AEM Assets {#assets-supported-formats}

AEM Assets unterstützt eine breite Palette von Dateiformaten und jede Funktionalität bietet unterschiedliche Unterstützung für verschiedene MIME-Typen.

Um AEM Assets mit anderen standardkonformen DAM-Lösungen (Digital Asset Management) und Desktop-Software-Anwendungen zu integrieren, verwenden Sie die Extensible Metadata Platform (XMP) von Adobe.

Die Legende gibt den Grad der Unterstützung an.

| Unterstützungsebene | Beschreibung |
|:---:|---|
| ✓ | Unterstützt |
| * | Mit Funktionen von Zusatzmodulen unterstützt |
| - | Nicht zutreffend |

## Raster-Bildformate {#supported-raster-image-formats}

Folgende Rasterbildformate werden für Asset-Management-Funktionen unterstützt:

| Format | Speicherung | Metadatenverwaltung | Metadatenextraktion | Generierung von Miniaturansichten | Interaktive Bearbeitung | Metadaten-Writeback | Insights |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| PNG | verwalten | verwalten | verwalten | verwalten | verwalten | verwalten | verwalten |
| GIF | verwalten | verwalten | verwalten | verwalten | verwalten |  | verwalten |
| TIFF | verwalten | verwalten | verwalten | verwalten |  | verwalten | verwalten |
| JPEG | verwalten | verwalten | verwalten | verwalten | verwalten | verwalten | verwalten |
| BMP | verwalten | verwalten | verwalten | verwalten | verwalten |  | verwalten |
| PNM | verwalten | verwalten |  |  |  |  | verwalten |
| PGM | verwalten | verwalten |  |  |  |  | verwalten |
| PBM | verwalten | verwalten |  |  |  |  | verwalten |
| PPM | verwalten | verwalten |  |  |  |  | verwalten |
| PSD **‡** | verwalten | verwalten | verwalten | verwalten |  |  | verwalten |
| [EPS](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | verwalten | verwalten | verwalten | verwalten |  | verwalten |  |
| PICT |  |  |  |  |  |  | verwalten |
| PSB | verwalten | verwalten | verwalten | verwalten |  |  |  |

**‡** Das zusammengeführte Bild wird aus der PSD-Datei extrahiert. Dabei handelt es sich um ein von Adobe Photoshop generiertes Bild, das in der PSD enthalten ist. Je nach den Einstellungen kann dieses Bild das eigentliche Bild sein oder nicht.

Folgende Rasterbildformate werden für Dynamic Media-Funktionen unterstützt:

| Format | Upload<br> (Eingabeformat) | Erstellen<br> image<br> preset<br> (Ausgabeformat) | Vorschau<br> dynamische<br> Ausgabedarstellung | Bereitstellung<br> dynamischer<br> Ausgabedarstellung | Download<br> dynamische<br> Ausgabedarstellung |
|---|:---:|:---:|:---:|:---:|:---:|
| PNG | verwalten | verwalten | verwalten | verwalten | verwalten |
| GIF | verwalten | verwalten | verwalten | verwalten | verwalten |
| TIFF | verwalten | verwalten | verwalten | verwalten | verwalten |
| JPEG | verwalten | verwalten | verwalten | verwalten | verwalten |
| BMP | verwalten |  |  |  |  |
| PNM |  |  |  |  |  |
| PGM |  |  |  |  |  |
| PBM |  |  |  |  |  |
| PPM |  |  |  |  |  |
| PSD **‡** | verwalten |  |  |  |  |
| [EPS](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | verwalten | verwalten | verwalten | verwalten | verwalten |
| PICT | verwalten |  |  |  |  |
| PSB |  |  |  |  |  |

**‡** Das zusammengeführte Bild wird aus der PSD-Datei extrahiert. Dabei handelt es sich um ein von Adobe Photoshop generiertes Bild, das in der PSD enthalten ist. Je nach den Einstellungen kann dieses Bild das eigentliche Bild sein oder nicht.

Berücksichtigen Sie zusätzlich zu den oben genannten Informationen Folgendes:

* Die Unterstützung für EPS-Dateien gilt nur für Rasterbilder. Zum Beispiel wird die Erstellung von Miniaturansichten für Vektorbilder im EPS-Format nicht standardmäßig unterstützt. Um die Unterstützung hinzuzufügen, [konfigurieren Sie ImageMagick](best-practices-for-imagemagick.md). Informationen zur Integration von Drittanbieter-Tools zur Aktivierung zusätzlicher Funktionen finden Sie unter [Befehlszeilenbasierter Medien-Handler](media-handlers.md#command-line-based-media-handler).

* Metadaten-Writeback funktioniert für das PSB-Dateiformat, wenn es zum Handler `NComm` hinzugefügt wird.

* Um mithilfe von Dynamic Media dynamische Ausgaben für EPS-Dateien in der Vorschau anzuzeigen und zu generieren, informieren Sie sich unter [Dateiformate Adobe Illustrator (AI), Postscript (EPS) und PDF](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats).

* Metadaten-Writeback für EPS-Dateien wird ab Version 3.0 von PostScript Document Structuring Convention (PS-Adobe) unterstützt.

## Nicht unterstützte Rasterbildformate in Dynamic Media {#unsupported-image-formats-dynamic-media}

In der folgenden Liste werden die Untertypen der Rasterbilddateiformate beschrieben, die in Dynamic Media nicht von *a1/> unterstützt werden.*

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

Die Adobe Camera Raw-Bibliothek aktiviert AEM Assets für die Aufnahme von Rohbildern. Siehe [Camera Raw Unterstützung](camera-raw.md).

## Dokumentenformate {#supported-document-formats}

Folgende Dokumentenformate werden für Asset-Management-Funktionen unterstützt:

| Format | Speicherung | Verwaltung von Metadaten<br> | Volltext<br> Extraktion | Extraktion von Metadaten<br> | Generierung von Miniaturansichten<br> | Extraktion von Subasset<br> | Metadaten<br> Writeback |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| [AI](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | verwalten | verwalten |  | verwalten | verwalten | verwalten | verwalten |
| DOC | verwalten | verwalten | verwalten | verwalten |  |  |  |
| DOCX | verwalten | verwalten | verwalten | verwalten |  |  |  |
| ODT | verwalten | verwalten | verwalten |  |  |  |  |
| [PDF](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | verwalten | verwalten | verwalten | verwalten | verwalten | verwalten | verwalten |
| HTML | verwalten | verwalten | verwalten |  |  |  |  |
| RTF | verwalten | verwalten | verwalten |  |  |  |  |
| TXT | verwalten | verwalten | verwalten |  |  |  |  |
| XLS | verwalten | verwalten | verwalten |  |  |  |  |
| XLSX | verwalten | verwalten | verwalten | verwalten |  |  |  |
| ODS | verwalten | verwalten | verwalten |  |  |  |  |
| PPT | verwalten | verwalten | verwalten | verwalten | verwalten | verwalten |  |
| PPTX | verwalten | verwalten | verwalten | verwalten | verwalten | verwalten |  |
| ODP | verwalten | verwalten | verwalten |  |  |  |  |
| [INDD](managing-image-presets.md#indesign-indd-file-format) | verwalten | verwalten |  | verwalten | verwalten | verwalten | verwalten |
| PS | verwalten | verwalten |  |  |  |  |  |
| QXP | verwalten | verwalten |  |  |  |  |  |
| EPUB | verwalten | verwalten |  | verwalten | verwalten |  |  |

Folgende Dokumentenformate werden für Dynamic Media-Funktionen unterstützt:

| Format | Upload<br> (Eingabeformat) | Erstellen<br> image<br> preset<br> (Ausgabeformat) | Vorschau<br> dynamische<br> Ausgabedarstellung | Bereitstellung<br> dynamischer<br> Ausgabedarstellung | Download<br> dynamische<br> Ausgabedarstellung |
|---|:---:|:---:|:---:|:---:|:---:|
| [KI](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | verwalten |  |  |  |  |
| DOC |  |  |  |  |  |
| DOCX |  |  |  |  |  |
| ODT |  |  |  |  |  |
| [PDF](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | verwalten | verwalten | verwalten | verwalten | verwalten |
| HTML |  |  |  |  |  |
| RTF |  |  |  |  |  |
| TXT |  |  |  |  |  |
| XLS |  |  |  |  |  |
| XLSX |  |  |  |  |  |
| ODS |  |  |  |  |  |
| PPT |  |  |  |  |  |
| PPTX |  |  |  |  |  |
| ODP |  |  |  |  |  |
| [INDD](managing-image-presets.md#indesign-indd-file-format) | verwalten |  |  |  |  |
| PS |  |  |  |  |  |
| QXP |  |  |  |  |  |
| EPUB |  |  |  |  |  |

Berücksichtigen Sie zusätzlich zu den oben genannten Funktionen Folgendes:

* Um mithilfe von Dynamic Media dynamische Ausgaben für PDF-Dateien zu generieren, informieren Sie sich unter [Adobe Illustrator (AI)-, PostScript (EPS)- und PDF-Dateiformate.](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)

* Um mithilfe von Dynamic Media dynamische Ausgaben für AI-Dateien in der Vorschau anzuzeigen und zu generieren, informieren Sie sich unter [Adobe Illustrator (AI)-, PostScript (EPS)- und PDF-Dateiformate.](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) 

* Informationen zum Generieren dynamischer Ausgabeformate für INDD-Dateien mit Dynamic Media finden Sie unter [InDesign (INDD)-Dateiformat](../assets/managing-image-presets.md#indesign-indd-file-format).

## Multimediaformate {#supported-multimedia-formats}

| Format | Speicherung | Metadatenverwaltung | Metadatenextraktion | Generierung von Miniaturansichten | FFMPEG-Transkodierung |
|:---|:---:|:---:|:---:|:---:|:---:|
| AAC | verwalten | verwalten |  | - | * |
| MIDI | verwalten | verwalten |  | - | * |
| 3GP | verwalten | verwalten |  | - | * |
| MP3 | verwalten | verwalten | verwalten | - | * |
| MPG | verwalten | verwalten |  | - | * |
| OGA | verwalten | verwalten |  | - | * |
| OGG | verwalten | verwalten |  | - | * |
| RA | verwalten | verwalten |  | - | * |
| WAV | verwalten | verwalten |  | - | * |
| WMA | verwalten | verwalten |  | - | * |
| DVI | verwalten | verwalten |  | * | * |
| FLV | verwalten | verwalten |  | * | * |
| M4V | verwalten | verwalten |  | * | * |
| MPEG | verwalten | verwalten |  | * | * |
| OGV | verwalten | verwalten |  | * | * |
| MOV | verwalten | verwalten |  | * | * |
| WMV | verwalten | verwalten |  | * | * |
| SWF | verwalten | verwalten |  |  |  |

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
| TGZ | verwalten | verwalten | verwalten | verwalten | verwalten |  |
| JAR | verwalten | verwalten | verwalten | verwalten | verwalten |  |
| RAR | verwalten | verwalten | verwalten | verwalten | verwalten |  |
| TAR | verwalten | verwalten | verwalten | verwalten | verwalten |  |
| ZIP **†** | verwalten | verwalten | verwalten | verwalten | verwalten | verwalten |

**†** Das zusammengeführte Bild wird aus der PSD-Datei extrahiert. Dabei handelt es sich um ein von Adobe Photoshop generiertes Bild, das in der PSD enthalten ist. Je nach den Einstellungen kann dieses Bild das eigentliche Bild sein oder nicht. Die ZIP-Archive, die unter Verwendung des `Deflate64`-Algorithmus erstellt werden, werden in AEM nur begrenzt unterstützt. Archivierungs- und Archivierungsvorgänge werden nicht unterstützt. Jedoch werden Operationen wie das Laden, Navigieren und Herunterladen unterstützt.

## Weitere unterstützte Formate {#other-supported-formats}

Die Anwendbarkeit allgemeiner DAM-Workflows für einige weitere Dateiformate wird in der folgenden Tabelle beschrieben.

| Format | Speicherung | Versionierung | Workflow | Veröffentlichung | Zugriffssteuerung | Bereitstellung dynamischer Medien |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| **#** | verwalten | verwalten | verwalten | verwalten | verwalten |  |
| SVG | verwalten | verwalten | verwalten | verwalten | verwalten |  |
| CSS | verwalten | verwalten | verwalten | verwalten | verwalten | verwalten |
| VTT | verwalten | verwalten | verwalten | verwalten | verwalten | verwalten |
| XML | verwalten | verwalten | verwalten | verwalten | verwalten | verwalten |
| Javascript (wenn mit eigener Bereitstellungsdomäne konfiguriert) |  |  |  |  |  | verwalten |

**#** Die anderen Formate werden in DAM für Speicher, Versionierung, ACL, Workflow, Veröffentlichung und Metadatenverwaltung unterstützt.

## Unterstützte MIME-Typen {#supported-mime-types}

Standardmäßig erkennt AEM den Dateityp mithilfe der Dateierweiterung. AEM kann es aus dem Inhalt der Dateien erkennen. Wählen Sie für letztere die Option [!UICONTROL MIME aus dem Inhalt erkennen] in [!UICONTROL Day CQ DAM Mime Type Service] in der AEM Web Console.

Eine Liste der unterstützten MIME-Typen ist in CRXDE Lite unter `/conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes` verfügbar.

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
>* [Aktivieren Sie die Unterstützung](/help/sites-administering/scene7.md#enabling-mime-type-based-assets-scene-upload-job-parameter-support) von MIME-typbasierten Assets/Dynamic Media Classic-Upload-Auftragsparametern.
>* [Konfigurieren Sie die Unterstützung](config-dynamic.md) von MIME-typbasierten Upload-Auftragsparametern.

