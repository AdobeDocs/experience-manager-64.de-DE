---
title: Best Practices für Dateiformate in Assets
description: Best Practices für die Dateiunterstützung in [!DNL Experience Manager] Assets.
contentOwner: AG
feature: Asset Management,Developer Tools
role: Admin
exl-id: ff739a17-188e-4779-8820-9e4d9b7031d0
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 25%

---

# Best Practices für Dateiformate in Assets {#assets-file-format-best-practices}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

[!DNL Experience Manager Assets] unterstützt viele proprietäre und Drittanbieter-Dateiformatbibliotheken, um benutzerseitigen Bedarf an Dateiunterstützung zu decken. Zu den unterstützten Adobe-Bibliotheken gehören Adobe Camera Raw, Gibson, Adobe PDF Rasterizer und Adobe InDesign Server. Darüber hinaus [!DNL Assets] unterstützt Bibliotheken von Drittanbietern, einschließlich ImageMagick, TformerMonkeys usw.

Eine vollständige Liste der unterstützten Dateiformate finden Sie unter [Von Assets unterstützte Formate](assets-formats.md).

## Adobe Camera Raw-Bibliothek {#adobe-camera-raw-library}

Für optimale Leistung empfiehlt Adobe die Verwendung der Adobe Camera Raw-Bibliothek für:

* RAW
* DNG

Die Adobe Camera Raw-Bibliothek unterstützt das CMYK-Farbprofil als Eingabe. Es erzeugt jedoch die Ausgabe im RGB-Farbraum und unterstützt nur die Ausgabe im JPEG-Format. Der Farbraum der Quelldatei (z. B. CMYK) wird nicht in den Miniaturansichten beibehalten.

Weitere Informationen finden Sie unter [Camera Raw Unterstützung](camera-raw.md) in [!DNL Assets].

## Adobe PDF Rasterizer-Bibliothek {#adobe-pdf-rasterizer-library}

Die besten Ergebnisse erzielen Sie, wenn Adobe empfiehlt, die Adobe PDF Rasterizer-Bibliothek für die folgenden Dateien zu verwenden:

* Hohe, inhaltsintensive PDF-Dateien
* AI-Dateien mit nicht nativen Miniaturansichten
* Für AI-Dateien mit SPOT-Farben (PMS)

Die Miniaturbilder und Vorschauen, die mit PDF-Rasterizer generiert werden, haben eine bessere Qualität als die standardmäßige Rasterausgabe. Die Adobe PDF Rasterizer-Bibliothek unterstützt keine Farbraumkonvertierung. Unabhängig vom Farbraum der Quelldatei erzeugt Adobe PDF Rasterizer nur eine RGB-PDF-Ausgabe.

## Adobe InDesign-Server {#adobe-indesign-cc-server}

Adobe empfiehlt, den Adobe InDesign-Server zu verwenden, um Adobe InDesign-spezifische Ausgabeformate wie IDML und HTML zu extrahieren. Weitere Informationen finden Sie unter [Hinzufügen [!DNL Experience Manager] Assets als Referenzen in Adobe InDesign](managing-linked-subassets.md#add-aem-assets-as-references-in-adobe-indesign).

## Dynamic Media  {#dynamic-media}

Dynamic Media generiert und liefert mehrere Varianten ansprechender Inhalte in Echtzeit über sein globales, skalierbares und leistungsoptimiertes Netzwerk. Es dient der Bereitstellung interaktiver Erlebnisse und optimiert die Verwaltung digitaler Kampagnen. Weitere Informationen zur Aktivierung von Dynamic Media finden Sie unter [Konfigurieren von Dynamic Media](config-dynamic.md).

Derzeit kann Dynamic Media Videos mit bis zu 15 GB Inhalt pro Datei unterstützen.

## ImageMagick-Bibliothek {#imagemagick-library}

Adobe empfiehlt die Verwendung der ImageMagick-Bibliothek in den folgenden Szenarien:

* So generieren Sie Miniaturansichten für EPS-Dateien
* Beibehaltung von Bildprofilinformationen
* Beibehaltung von Transparenz
* Verarbeitung von PSD- und PSB-Dateien

Informationen zum Einrichten der ImageMagic-Bibliothek in [!DNL Experience Manager], siehe [Verwenden von ImageMagick](media-handlers.md#an-example-using-imagemagick). Informationen zur optimalen Verwendung finden Sie unter [Best Practices für die Konfiguration von ImageMagick](best-practices-for-imagemagick.md).

## Bildtranskodierungsbibliothek {#image-transcoding-library}

Die Adobe Imaging Transcoding Library ist eine Bildverarbeitungslösung, die zentrale Bildbearbeitungsfunktionen wie Bildkodierung, -transkodierung, -Resampling, Größenanpassung usw. durchführt.

Die Imaging Transcoding Library unterstützt die folgenden MIME-Typen:

* JPG/JPEG
* PNG (8 Bit und 16 Bit)
* GIF
* BMP
* TIFF/Komprimiertes TIFF (außer 32-Bit-Tiff und PTiff).
* ICO
* ICN

Weitere Informationen finden Sie unter [Imaging Transcoding Library](imaging-transcoding-library.md).
