---
title: Best Practices für Dateiformate in Assets
description: Best Practices für die Dateiunterstützung in AEM Assets.
contentOwner: AG
feature: Asset Management,Entwicklertools
role: Administrator
exl-id: ff739a17-188e-4779-8820-9e4d9b7031d0
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 91%

---

# Best Practices für Dateiformate in Assets {#assets-file-format-best-practices}

AEM Assets unterstützt viele proprietäre und Drittanbieter-Dateiformatbibliotheken, um benutzerseitigen Bedarf an Dateiunterstützung zu decken. Zu den unterstützten Adobe-Bibliotheken zählen Adobe Camera Raw, Gibson, Adobe PDF Rasterizer und Adobe InDesign Server. Außerdem unterstützt AEM Assets Drittanbieterbibliotheken, darunter ImageMagick, TwelveMonkeys usw.

Eine vollständige Liste der unterstützten Dateiformate finden Sie unter [Von Assets unterstützte Formate](assets-formats.md).

## Adobe Camera Raw-Bibliothek  {#adobe-camera-raw-library}

Für optimale Leistung empfiehlt Adobe die Verwendung der Adobe Camera Raw-Bibliothek für:

* RAW
* DNG

Die Adobe Camera Raw-Bibliothek unterstützt das CMYK-Farbprofil als Eingabe. Sie generiert die Ausgabe jedoch im RGB-Farbraum und unterstützt nur Darstellungen im JPEG-Format. Sie behält nicht den Quelldatei-Farbraum (z. B. CMYK) in den Miniaturen bei.

Weitere Informationen finden Sie unter [Camera Raw-Unterstützung](camera-raw.md) in AEM Assets.

## Adobe PDF Rasterizer-Bibliothek {#adobe-pdf-rasterizer-library}

Um optimale Ergebnisse zu erzielen, sollte die Adobe PDF Rasterizer-Bibliothek für folgende Dateien verwendet werden:

* Große PDF-Dateien mit viel Inhalt
* AI-Dateien mit nicht standardmäßig generierten Miniaturbildern
* Für AI-Dateien mit SPOT (PMS)-Farben

Die Miniaturbilder und Vorschauen, die mit PDF-Rasterizer generiert werden, haben eine bessere Qualität als die standardmäßige Rasterausgabe. Die Adobe PDF Rasterizer-Bibliothek unterstützt keine Farbraumkonvertierung. Ungeachtet des Farbraums der Quell-PDF-Datei generiert Adobe PDF Rasterizer nur eine RGB-Ausgabe.

## Adobe InDesign Server  {#adobe-indesign-cc-server}

Adobe empfiehlt, InDesign Server zu verwenden, um die InDesign-spezifischen Ausgaben von Adobe, darunter IDML und HTML, zu extrahieren. Weitere Informationen finden Sie unter [Hinzufügen AEM Assets als Referenzen in Adobe InDesign](managing-linked-subassets.md#add-aem-assets-as-references-in-adobe-indesign).

## Dynamic Media  {#dynamic-media}

Dynamic Media generiert und stellt mehrere Varianten von anspruchsvollem Inhalt über sein globales, skalierbares und leistungsoptimiertes Netzwerk bereit. Es dient der Bereitstellung interaktiver Erlebnisse und optimiert die Verwaltung digitaler Kampagnen. Weitere Informationen zur Aktivierung von Dynamic Media finden Sie unter [Konfigurieren von Dynamic Media](config-dynamic.md).

Derzeit unterstützt Dynamic Media Videos mit bis zu 15 GB Inhalt pro Datei.

## ImageMagick-Bibliothek {#imagemagick-library}

Adobe empfiehlt, die ImageMagick-Bibliothek für folgende Zwecke zu verwenden:

* Generieren von Miniaturausgabeformaten für EPS-Dateien
* Beibehaltung von Bildprofilinformationen
* Beibehaltung von Transparenz
* Verarbeitung von PSD- und PSB-Dateien

Informationen zum Einrichten der ImageMagic-Bibliothek in AEM finden Sie unter [Verwenden von ImageMagick](media-handlers.md#an-example-using-imagemagick). Hinweise zur optimalen Verwendung finden Sie unter [Best Practices zur Konfiguration von ImageMagick](best-practices-for-imagemagick.md).

## Imaging Transcoding Library  {#image-transcoding-library}

Bei der Adobe Imaging Transcoding Library handelt es sich um eine Lösung zur Bildverarbeitung, die essenzielle Bildfunktionen übernimmt, darunter Bildkodierung, -transkodierung, -Resampling, Größenanpassung usw.

Die Imaging Transcoding Library unterstützt folgende MIME-Typen:

* JPG/JPEG
* PNG (8 und 16 Bit)
* GIF
* BMP
* TIFF/Komprimiertes TIFF (außer 32-Bit-Tiff und PTiff).
* ICO
* ICN

Weitere Informationen finden Sie unter [Imaging Transcoding Library](imaging-transcoding-library.md).
