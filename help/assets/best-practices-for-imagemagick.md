---
title: Installieren und Konfigurieren von ImageMagick für die Verwendung mit [!DNL Experience Manager] Assets
description: Erfahren Sie mehr über die ImageMagick-Software, wie Sie diese installieren, den Befehlszeilenprozessschritt einrichten und damit Miniaturansichten von Bildern bearbeiten, zusammenstellen und generieren können.
contentOwner: AG
feature: Renditions,Developer Tools
role: Admin
exl-id: 9aeda88a-fd66-4fad-b496-3352a6ecab81
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '800'
ht-degree: 53%

---

# Installieren und konfigurieren Sie ImageMagick, um mit [!DNL Experience Manager Assets] arbeiten zu können. {#install-and-configure-imagemagick-to-work-with-aem-assets}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

ImageMagick-Software ist ein Software-Plug-in zum Erstellen, Bearbeiten, Zusammenzusetzen oder Konvertieren von Bitmap-Bildern. Es kann Bilder in über 200 Formaten lesen und schreiben, darunter PNG, JPEG, JPEG-2000, GIF, TIFF, DPX, EXR, WebP, Postscript, PDF und SVG. Verwenden Sie ImageMagick, um die Größe, das Spiegeln, Spiegeln, Drehen, Verzerren, Verscheren und Transformieren von Bildern zu ändern. Mit ImageMagick können Sie auch Bildfarben anpassen, verschiedene Spezialeffekte anwenden oder Text, Linien, Polygone, Ellipsen und Kurven zeichnen.

Verwenden Sie den Adobe Experience Manager-Medien-Handler über die Befehlszeile, um Bilder über ImageMagick zu verarbeiten. Informationen zum Arbeiten mit verschiedenen Dateiformaten mit ImageMagick finden Sie unter [Best Practices für Asset-Dateiformate](assets-file-format-best-practices.md). Weitere Informationen zu allen unterstützten Dateiformaten finden Sie unter [Von Assets unterstützte Formate](assets-formats.md).

Um große Dateien mit ImageMagick zu verarbeiten, sollten Sie höhere Speicheranforderungen als gewöhnlich berücksichtigen, mögliche Änderungen an IM-Richtlinien und die Gesamtauswirkungen auf die Leistung berücksichtigen. Die Speicheranforderungen hängen von verschiedenen Faktoren wie Auflösung, Bittiefe, Farbprofil und Dateiformat ab. Wenn Sie sehr große Dateien mit ImageMagick verarbeiten möchten, müssen Sie ein ordnungsgemäßes [!DNL Experience Manager]-Server-Benchmark durchführen. Einige hilfreiche Ressourcen finden Sie weiter unten.

>[!NOTE]
>
>Wenn Sie [!DNL Experience Manager] in Adobe Managed Services (AMS) verwenden, wenden Sie sich an den Adobe Support, wenn Sie viele große PSD- oder PSB-Dateien verarbeiten möchten. Experience Manager verarbeitet möglicherweise keine PSB-Dateien mit sehr hoher Auflösung, die mehr als 30000 x 23000 Pixel umfassen.

## Installieren von ImageMagick {#installing-imagemagick}

Für verschiedene Betriebssysteme stehen mehrere Versionen von ImageMagic-Installationsdateien zur Verfügung. Verwenden Sie die entsprechende Version für Ihr Betriebssystem.

1. Laden Sie die entsprechenden [ImageMagick-Installationsdateien](https://www.imagemagick.org/script/download.php) für Ihr Betriebssystem herunter.
1. Um ImageMagick auf der Festplatte zu installieren, auf der der [!DNL Experience Manager]-Server gehostet wird, starten Sie die Installationsdatei.

1. Legen Sie die Path-Umgebungsvariable auf das ImageMagick-Installationsverzeichnis fest.
1. Um zu überprüfen, ob die Installation erfolgreich war, führen Sie den Befehl `identify -version` aus.

## Einrichten des Befehlszeilen-Prozessschritts {#set-up-the-command-line-process-step}

Sie können den Befehlszeilenprozessschritt für Ihren jeweiligen Anwendungsfall einrichten. Führen Sie diese Schritte aus, um jedes Mal eine gespiegelte Version von Bildern und Miniaturansichten (140x100, 48x48, 319x319 und 1280x1280) zu erstellen, wenn Sie eine JPEG-Bilddatei zum Verzeichnis `/content/dam` auf dem [!DNL Experience Manager]-Server hinzufügen:

1. Wechseln Sie auf dem [!DNL Experience Manager]-Server zur Workflow-Konsole (`https://[aem_server]:[Port]/workflow`) und öffnen Sie das Workflow-Modell **[!UICONTROL DAM-Update-Asset]**.
1. Öffnen Sie über das Workflow-Modell **[!UICONTROL DAM-Update-Asset]** den Schritt **[!UICONTROL EPS-Miniaturansichten (unterstützt von ImageMagick)]**.
1. Fügen Sie in der **[!UICONTROL Registerkarte „Argumente“]** `image/jpeg` zur Liste **[!UICONTROL MIME-Typen]** hinzu.

   ![mime_types_jpeg](assets/mime_types_jpeg.png)

1. Geben Sie im Feld **[!UICONTROL Befehle]** folgenden Befehl ein:

   `convert ./${filename} -flip ./${basename}.flipped.jpg`

1. Aktivieren Sie die Flags **[!UICONTROL Erzeugte Ausgabedarstellung löschen]** und **[!UICONTROL Webausgabe erstellen]**.

   ![select_flags](assets/select_flags.png)

1. Legen Sie auf der Registerkarte **[!UICONTROL Webfähiges Bild]** die Details für die Ausgabedarstellung mit 1280x1280 Pixel fest. Geben Sie außerdem i *image/jpeg* im **[!UICONTROL Mimetype]** ankreuzen.

   ![web_enabled_image](assets/web_enabled_image.png)

1. Tippen/klicken **[!UICONTROL OK]** , um die Änderungen zu speichern.

   >[!NOTE]
   >
   >In manchen Versionen von Windows (z. B. Windows SE) kann der Befehl `convert` fehlschlagen, da er in Konflikt mit dem nativen Dienstprogramm `convert` steht, das Teil der Windows-Installation ist. Geben Sie in diesem Fall den vollständigen Pfad für das ImageMagick-Dienstprogramm an. Geben Sie beispielsweise
   >
   >`"C:\Program Files\ImageMagick-6.8.9-Q16\convert.exe" -define jpeg:size=319x319 ./${filename} -thumbnail 319x319 cq5dam.thumbnail.319.319.png`

1. Öffnen Sie den Schritt **[!UICONTROL Miniaturansichten verarbeiten]** und fügen Sie den MIME-Typ `image/jpeg` unter **[!UICONTROL MIME-Typen überspringen]** hinzu.

   ![skip_mime_types](assets/skip_mime_types.png)

1. Fügen Sie in der Registerkarte **[!UICONTROL Webfähiges Bild]** den MIME-Typ `image/jpeg` unter **[!UICONTROL Liste zum Überspringen]** hinzu. Tippen/klicken **[!UICONTROL OK]** , um die Änderungen zu speichern.

   ![web_enabled](assets/web_enabled.png)

1. Speichern Sie den Workflow.
1. Um zu überprüfen, ob ImageMagic Bilder ordnungsgemäß verarbeiten kann, laden Sie ein JPG-Bild in [!DNL Assets]. Überprüfen Sie, ob ein gespiegeltes Bild und die Ausgabeformate dafür generiert werden.

## Minderung von Sicherheitslücken {#mitigating-security-vulnerabilities}

Die Verwendung von ImageMagick zur Verarbeitung von Bildern weist mehrere Sicherheitslücken auf. Beispielsweise birgt die Verarbeitung von vom Benutzer übermittelten Bildern das Risiko der Ausführung von Remote-Code (RCE).

Darüber hinaus hängen verschiedene Bildverarbeitungs-Plug-ins von der ImageMagick-Bibliothek ab, darunter der imagick von PHP, Rmagick und Paperclip von Ruby und Node.js imagemagick.

Wenn Sie ImageMagick oder eine betroffene Bibliothek verwenden, empfiehlt Adobe, die bekannten Sicherheitslücken zu minimieren, indem Sie mindestens eine der folgenden Aufgaben ausführen (vorzugsweise beide):

1. Vergewissern Sie sich, dass alle Bilddateien in Übereinstimmung mit den von Ihnen unterstützten Bilddateitypen mit den erwarteten [„magischen Bytes“](https://en.wikipedia.org/wiki/List_of_file_signatures) beginnen, bevor Sie sie zur Verarbeitung an ImageMagick senden.
1. Verwenden Sie eine Richtliniendatei, um die anfälligen ImageMagick-Codierer zu deaktivieren. Die globale Richtlinie für ImageMagick ist in `/etc/ImageMagick` zu finden.

>[!MORELIKETHIS]
>
>* [Best Practices für die Verarbeitung verschiedener Dateiformate mithilfe von [!DNL Assets]](assets-file-format-best-practices.md)
>* [Befehlszeilenoptionen für ImageMagick](https://www.imagemagick.org/script/command-line-options.php)
>* [Grundlegende und erweiterte Beispiele für die Verwendung von ImageMagick](https://www.imagemagick.org/Usage/)
>* [Asset-Leistungsoptimierung für ImageMagick](performance-tuning-guidelines.md)
>* [Vollständige Liste der von [!DNL Assets]](assets-formats.md)
>* [Grundlegendes zu Dateiformaten und Speicherkosten von Bildern](https://www.scantips.com/basics1d.html)

