---
title: Imaging Transcoding Library
description: Erfahren Sie, wie Sie die Imaging Transcoding Library von Adobe konfigurieren und verwenden, eine Bildverarbeitungslösung, die die wichtigsten Bildbearbeitungsfunktionen wie Kodierung, Transcodierung, Bildneubearbeitung und Bildgröße durchführen kann.
contentOwner: AG
feature: Renditions,Developer Tools,Asset Processing
role: Admin
exl-id: 0314626d-e846-4f10-950e-6c1ceb7f4c06
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '994'
ht-degree: 69%

---

# Imaging Transcoding Library {#imaging-transcoding-library}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Die Imaging Transcoding Library von Adobe ist eine proprietäre Bildverarbeitungslösung, die zentrale Bildbearbeitungsfunktionen durchführen kann, darunter:

* Kodierung
* Transkodierung (Konvertieren unterstützter Formate)
* Bildneubearbeitung mit PS- und Intel IPP-Algorithmen
* Beibehaltung der Bittiefe und des Farbprofils
* JPEG-Qualitätskomprimierung
* Ändern der Bildgröße

Die Imaging Transcoding Library bietet CMYK-Unterstützung und vollständige Alpha-Unterstützung, außer CMYK-Alpha.

Neben der Unterstützung einer Vielzahl von Dateiformaten und Profilen bietet die Imaging Transcoding Library signifikante Vorteile im Vergleich zu anderen Lösungen von Drittanbietern hinsichtlich Leistung, Skalierbarkeit und Qualität. Hier nur einige Vorteile der Verwendung der Imaging Transcoding Library:

* **Skaliert mit zunehmender Dateigröße oder Auflösung**: Die Skalierung wird hauptsächlich durch die patentierte Fähigkeit der Imaging Transcoding Library erreicht, die Größe beim Dekodieren von Dateien zu ändern. Diese Funktion stellt sicher, dass die Speicherauslastung der Laufzeitumgebung immer optimal ist und keine quadratische Funktion zur Erhöhung der Dateigröße oder der Auflösung von Megapixeln ist. Die Imaging Transcoding Library kann größere und hochauflösende Dateien (mit höheren Megapixeln) verarbeiten. Drittanbieter-Tools wie ImageMagick können große Dateien nicht verarbeiten und stürzen bei der Verarbeitung solcher Dateien ab.
* **Algorithmen zur Qualitätskomprimierung und Größenanpassung von Photoshop**: Konsistenz mit dem Branchenstandard hinsichtlich der Qualität der Downsampling (glatt, scharf und automatisch bikubisch) und der Komprimierungsqualität. Die Imaging Transcoding Library ermittelt außerdem den Qualitätsfaktor des Eingabebildes und setzt für das Ausgabebild intelligent Optimierungstabellen und Qualitätseinstellungen ein. Dies erzeugt Dateien in optimaler Größe, ohne Abstriche bei der visuellen Qualität.
* **Hoher Durchsatz:** Die Antwortzeit ist kürzer und der Durchsatz ist durchgängig höher als bei ImageMagick. Daher verringern sich mit der Imaging Transcoding Library die Wartezeiten für Benutzerinnen und Benutzer und die Kosten für das Hosting.
* **Bessere Skalierung bei gleichzeitiger Last:** Die Imaging Transcoding Library liefert optimale Leistung bei gleichzeitiger Last. Sie bietet hohen Durchsatz mit optimaler CPU-Leistung, Speichernutzung und niedriger Antwortzeit, was die Kosten für das Hosting verringert.

## Unterstützte Plattformen {#supported-platforms}

Die Imaging Transcoding Library ist nur für RHEL 7- und CentOS 7-Distributionen verfügbar.

>[!NOTE]
>
>Mac OS und andere *nix-Distributionen (z. B. Debian und Ubuntu) werden nicht unterstützt.

## Nutzung {#usage}

Die Befehlszeilenargumente für die Imaging Transcoding Library können Folgendes umfassen:

```shell
 -destMime PNG/JPEG: Mime type of output rendition
 -BitDepth 8/16: Preserves Bit Depth. Bitdepth ‘4’ is automatically converted to ‘8’
 -preserveBitDepth: Downscales Bit Depth (No upscaling)
 -preserveCMYK: Preserves CMYK color space
 -jpegQuality: Provides jpeg quality parameter (0-12 , corresponding to Photoshop qualities)
 -ResamplingMethod BiCubic/Lanczos/PSBicubic: Provides resampling methods. PSBicubic is a Photoshop quality resampling method.
 -resize
```

Für den Parameter `-resize` können folgende Optionen konfiguriert werden:

* `X`: `Works similar to AEM. For example -resize 319.`

* `WxH`: `Aspect Ratio will not be maintained, For example -resize 319X319.`

* `Wx`: `Fixes the width and calculates the height maintaining the aspect ratio. For example -resize 319x.`

* `xH`: `Fixes the height and calculates the width maintaining the aspect ratio. For example -resize x319.`

```shell
 -AllowUpsampling (Resizes smaller images)
 -input <fileName>
 -output <fileName>
```

## Konfigurieren der Imaging Transcoding Library {#configuring-imaging-transcoding-library}

Erstellen Sie zum Konfigurieren der ITL-Verarbeitung eine Konfigurationsdatei und aktualisieren Sie den Workflow, um sie auszuführen.

### Erstellen einer Konfigurationsdatei für das extrahierte Bundle {#create-conf-file}

Um die Bibliothek zu konfigurieren, erstellen Sie eine .conf-Datei, um die Bibliotheken mithilfe der folgenden Schritte anzugeben. Sie benötigen Admin- oder Root-Berechtigungen.

1. Laden Sie das Paket mit der [Imaging Transcoding Library von Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/aem630/product/assets/aem-assets-imaging-transcoding-library-pkg) herunter und installieren Sie es mit dem Paket-Manager. Das Paket ist kompatibel mit [!DNL Experience Manager] 6.5.

1. So kennen Sie die Bundle-ID für `com.day.cq.dam.cq-dam-switchengine`, melden Sie sich bei der Web-Konsole an und tippen Sie auf **[!UICONTROL OSGi > Bundles]**. Alternativ können Sie zum Öffnen der Bundles-Konsole die URL `https://[aem_server:[port]/system/console/bundles/` aufrufen. Suchen Sie das Bundle `com.day.cq.dam.cq-dam-switchengine` und seine ID.

1. Stellen Sie sicher, dass alle erforderlichen Bibliotheken extrahiert werden, indem Sie den Ordner mit dem Befehl `ls -la /aem64/author/crx-quickstart/launchpad/felix/bundle<id>/data/binaries/` überprüfen, wobei der Ordnername die Bundle-ID enthält. Beispielsweise lautet der Befehl `ls -la /aem64/author/crx-quickstart/launchpad/felix/bundle588/data/binaries/`, wenn die Bundle-ID `588` ist.

1. Erstellen Sie eine Datei `SWitchEngineLibs.conf`, die mit der Bibliothek verknüpft wird.

   ```shell
   cd `/etc/ld.so.conf.d`
   touch SWitchEngineLibs.conf
   vi SWitchEngineLibs.conf
   ```

1. Fügen Sie den Pfad `/aem64/author/crx-quickstart/launchpad/felix/bundle<id>/data/binaries/` mit dem Befehl `cat SWitchEngineLibs.conf` der conf-Datei hinzu.

1. Führen Sie den Befehl `ldconfig` aus, um die erforderlichen Links und den Cache zu erstellen.

1. Bearbeiten Sie in dem Konto, das zum Starten von AEM verwendet wird `.bash_profile` -Datei. Fügen Sie `LD_LIBRARY_PATH` hinzu, indem Sie Folgendes hinzufügen.

   ```shell
   LD_LIBRARY_PATH=.
   export LD_LIBRARY_PATH
   ```

1. Stellen Sie sicher, dass der Wert des Pfads auf `.` festgelegt ist, indem Sie den Befehl `echo $LD_LIBRARY_PATH` verwenden. Die Ausgabe sollte nur `.` sein. Wenn der Wert nicht auf `.` festgelegt ist, starten Sie die Sitzung neu.

### Konfigurieren Sie den Workflow DAM-Update-Asset. {#configure-dam-asset-update-workflow}

Aktualisieren Sie den Workflow [!UICONTROL DAM-Update-Asset], um die Bibliothek zur Verarbeitung von Bildern zu verwenden.

1. Tippen/klicken Sie auf [!DNL Experience Manager] -Logo und navigieren Sie zu **[!UICONTROL Tools > Workflow > Modelle]**.

1. Öffnen Sie auf der Seite **[!UICONTROL Workflow-Modelle]** den Workflow **[!UICONTROL DAM-Update-Asset]** im Bearbeitungsmodus.

1. Öffnen Sie den Workflow-Prozessschritt **[!UICONTROL Miniaturansichten verarbeiten]**. Fügen Sie auf der Registerkarte **[!UICONTROL Miniaturansichten]** die MIME-Typen, bei denen Sie den Standardprozess zum Generieren von Miniaturansichten überspringen möchten, zur Liste **[!UICONTROL MIME-Typen überspringen]** hinzu.
Wenn Sie z. B. Miniaturansichten für ein TIFF-Bild mit der Imaging Transcoding Library erstellen möchten, geben Sie in das Feld `image/tiff`MIME-Typen überspringen **[!UICONTROL den Text]** ein.

1. Fügen Sie auf der Registerkarte **[!UICONTROL Webfähiges Bild]** die MIME-Typen zur **[!UICONTROL Liste zum Überspringen]** hinzu, bei denen Sie den Standardprozess zum Generieren von Web-Ausgaben überspringen möchten. Wenn Sie z. B. im vorherigen Schritt den MIME-Typ `image/tiff` übersprungen haben, fügen Sie der Liste zum Überspringen `image/tiff` hinzu.

1. Öffnen Sie den Schritt **[!UICONTROL EPS-Miniaturen (unterstützt von ImageMagick)]** und navigieren Sie zur Registerkarte **[!UICONTROL Argumente]**. Fügen Sie der Liste **[!UICONTROL MIME-Typen]** die MIME-Typen hinzu, die die Imaging Transcoding Library verarbeiten soll. Wenn Sie z. B. im vorherigen Schritt den MIME-Typ `image/tiff` übersprungen haben, fügen Sie `image/jpeg` zur Liste **[!UICONTROL MIME-Typen]** hinzu.

1. Entfernen Sie die Standardbefehle, falls vorhanden.

1. Blenden Sie das seitliche Bedienfeld ein und fügen Sie aus der Liste der Schritte **[!UICONTROL SwitchEngine Handler]** hinzu.

1. Fügen Sie basierend auf Ihren benutzerdefinierten Anforderungen Befehle zu [!UICONTROL SwitchEngine Handler] hinzu. Passen Sie die Parameter der Befehle an, die Sie für Ihre Anforderungen angeben. Wenn Sie z. B. das Farbprofil Ihres JPEG-Bildes beibehalten möchten, fügen Sie die folgenden Befehle zur Liste **[!UICONTROL Befehle]** hinzu:

   * `SWitchEngine -input ${file} -destMime PNG -resize 48 -output ${directory}cq5dam.thumbnail.48.48.png`
   * `SWitchEngine -input ${file} -destMime PNG -resize 140x100 -output ${directory}cq5dam.thumbnail.140.100.png`
   * `SWitchEngine -input ${file} -destMime PNG -resize 319 -output ${directory}cq5dam.thumbnail.319.319.png`
   * `SWitchEngine -input ${file} -destMime JPEG -resize 1280 -preserveCMYK -output ${directory}cq5dam.web.1280.1280.jpeg`

   ![chlimage](assets/chlimage_1-199.png)

1. (Optional) Generieren Sie mit einem einzelnen Befehl Miniaturansichten aus einer Zwischenausgabe. Die Zwischenausgabe dient als Quelle, um statische und Web-Ausgaben zu generieren. Diese Methode ist schneller als die frühere Methode. Mit dieser Methode können Sie jedoch keine benutzerdefinierten Parameter auf Miniaturansichten anwenden.

   ![chlimage](assets/chlimage_1-200.png)

1. Um Web-Ausgaben zu generieren, konfigurieren Sie Parameter auf der Registerkarte **[!UICONTROL Webfähiges Bild]**.

1. Synchronisieren Sie das aktualisierte Workflow-Modell [!UICONTROL DAM-Update-Asset]. Speichern Sie den Workflow.

Überprüfen Sie die Konfiguration, laden Sie ein TIFF-Bild hoch und überwachen Sie die Datei error.log. Ihnen werden `INFO`-Nachrichten auffallen, in denen `SwitchEngineHandlingProcess execute: executing command line` vorkommt. In den Protokollen werden die generierten Ausgabedarstellungen genannt. Nach Abschluss des Workflows können Sie die neuen Ausgabedarstellungen in AEM anzeigen.

>[!MORELIKETHIS]
>
>* [Artikel zu unterstützten MIME-Typen](assets-formats.md#supported-image-transcoding-library)

