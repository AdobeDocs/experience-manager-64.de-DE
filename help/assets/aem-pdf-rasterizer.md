---
title: PDF-Rasterfunktion verwenden
description: Erstellen Sie hochwertige Miniaturansichten und Darstellungen mit der Adobe PDF Raster-Bibliothek.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1

---


# Verwenden von PDF Rasterizer {#using-pdf-rasterizer}

Wenn große, inhaltslastige PDF- oder AI-Dateien in Adobe Experience Manager (AEM) Assets hochgeladen werden, erstellt die Standardbibliothek u. U. manchmal keine genaue Ausgabe. In solchen Fällen kann die Adobe PDF Rasterizer-Bibliothek zuverlässigere und präzisere Ausgaben erstellen als Standardbibliotheken.

Adobe empfiehlt die Verwendung der PDF Rasterizer-Bibliothek für folgende Dateien:

* Starke, inhaltsintensive AI- oder PDF-Dateien.
* AI- oder PDF-Dateien mit nicht standardmäßig generierten Miniaturbildern.
* AI-Dateien mit PMS-Farben (Pantone Matching System)

Mit PDF Rasterizer erstellte Miniaturansichten und Vorschauen weisen im Vergleich mit der standardmäßigen Ausgabe eine bessere Qualität auf und bieten daher eine konsistente Darstellung auf allen Geräten. Die Adobe PDF Rasterizer-Bibliothek unterstützt keine Farbraumkonvertierung. Die Ausgabe erfolgt unabhängig vom Farbraum der Quelldatei immer in RGB.

1. Installieren Sie das PDF Rasterizer-Paket aus [Package Share](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/product/assets/aem-assets-pdf-rasterizer-pkg) auf Ihrer AEM-Instanz.

   >[!NOTE]
   >
   >Die PDF Rasterizer-Bibliothek ist nur für Windows und Linux verfügbar.

1. Greifen Sie von `https://[AEM_server]:[port]/workflow`aus auf die AEM Assets Workflow-Konsole zu.
1. Open the **[!UICONTROL DAM Update Asset]** workflow page.
1. Konfigurieren Sie Folgendes, um die standardmäßige Miniaturansicht- und Webwiedergabegenerierung für PDF- und AI-Dateien zu überspringen:

   * Öffnen Sie den Schritt **[!UICONTROL Miniaturansicht-Prozess]** und fügen Sie `application/pdf` bzw. `application/postscript` im Feld &quot; **[!UICONTROL Mime-Typen]** überspringen&quot;hinzu.
   ![skip_mime_types-2](assets/skip_mime_types-2.png)

   * In the **[!UICONTROL Web Enabled Image]** tab, add `application/pdf` or `application/postscript` under **[!UICONTROL Skip List]** depending upon your requirements.
   ![web_enabled_imageskiplist](assets/web_enabled_imageskiplist.png)

1. Open the **[!UICONTROL Rasterize PDF/AI Image Preview Rendition]** step, and remove the MIME type for which you want to skip the default generation of preview image renditions. For example, remove the MIME type *application/pdf*, *application/postscript,* or *application/illustrator* from the **[!UICONTROL MIME Types]** list.

   ![process_arguments](assets/process_arguments.png)

1. Ziehen Sie den Schritt **[!UICONTROL PDF Rasterizer-Handler]** aus dem Seitenbereich unter den Schritt **[!UICONTROL Miniaturansichten verarbeiten]**.
1. Configure the following arguments for the **[!UICONTROL PDF Rasterizer Handler]** step:

   * Mime Types: *application/pdf* or *application/postscript*
   * Befehle: `PDFRasterizer -d -p 1 -s 1280 -t PNG -i ${file}`
   * Fügen Sie Größen für Miniaturansichten hinzu: 319:319, 140:100, 48:48. Fügen Sie ggf. eine benutzerdefinierte Konfiguration für Miniaturansichten hinzu.
   Die Befehlszeilenargumente für den `PDFRasterizer`-Befehl können Folgendes enthalten:

   **-d**: Flag zum Ermöglichen einer reibungslosen Darstellung von Text, Vektorgrafiken und Bildern. Erstellt Bilder mit besserer Qualität. Die Verwendung dieses Parameters führt allerdings zu einer langsamen Ausführung des Befehls und zu größeren Bildern.

   `-p`: Seitenzahl. Der Standardwert ist „Alle Seiten“. „*“ steht für „Alle Seiten“.

   **-s**: Maximale Bildabmessung (Höhe oder Breite). Dieser Wert wird für jede Seite in DPI umgewandelt. Bei Seiten mit unterschiedlichen Größen wird u. U. jede Seite mit einem anderen Wert skaliert. Der Standardwert ist die tatsächliche Seitengröße.

   **-t**: Typ des Ausgabeabbilds. Gültige Formate sind JPEG, PNG, GIF und BMP. Das Standardformat ist JPEG.

   **-i**: Pfad für die Eingabe-PDF. Dieser Parameter ist erforderlich.

   `-h`: Hilfe

1. Um Zwischenausgabeformate zu löschen, wählen Sie **[!UICONTROL Erzeugte Ausgabe löschen]**.
1. Um Webausgabeformate von PDF Rasterizer generieren zu lassen, wählen Sie **[!UICONTROL Webausgabe erstellen]**.

   ![generate_web_renditions1](assets/generate_web_renditions1.png)

1. Specify the settings in the **[!UICONTROL Web Enabled Image]** tab.

   ![web_enabled_image1](assets/web_enabled_image1.png)

1. Speichern Sie den Workflow.
1. To enable PDF Rasterizer to process PDF pages with PDF libraries, open the **[!UICONTROL DAM Process Subasset]** model from the Workflow console.
1. From the side panel, drag the PDF Rasterizer Handler step under the **[!UICONTROL Create Web-Enabled Image Rendition]** step.
1. Configure the following arguments for the **[!UICONTROL PDF Rasterizer Handler]** step:

   * Mime-Typen: `application/pdf` oder `application/postscript`
   * Befehle: `PDFRasterizer -d -p 1 -s 1280 -t PNG -i ${file}`
   * Fügen Sie Größen für Miniaturansichten hinzu: 319:319, 140:100, 48:48. Fügen Sie ggf. eine benutzerdefinierte Konfiguration für Miniaturansichten hinzu.
   Die Befehlszeilenargumente für den PDFRasterizer-Befehl können Folgendes enthalten:

   **-d**: Flag zum Ermöglichen einer reibungslosen Darstellung von Text, Vektorgrafiken und Bildern. Erstellt Bilder mit besserer Qualität. Die Verwendung dieses Parameters führt allerdings zu einer langsamen Ausführung des Befehls und zu größeren Bildern.

   **-p**: Seitenzahl. Der Standardwert ist „Alle Seiten“. Ein Sternchen `*` bezeichnet alle Seiten.

   **-s**: Maximale Bildabmessung (Höhe oder Breite). Dieser Wert wird für jede Seite in DPI umgewandelt. Bei Seiten mit unterschiedlichen Größen wird u. U. jede Seite mit einem anderen Wert skaliert. Der Standardwert ist die tatsächliche Seitengröße.

   **-t**: Typ des Ausgabeabbilds. Gültige Formate sind JPEG, PNG, GIF und BMP. Das Standardformat ist JPEG.

   **-i**: Pfad für die Eingabe-PDF. Dieser Parameter ist erforderlich.

   **-h**: Hilfe

1. Um Zwischenausgabeformate zu löschen, wählen Sie **[!UICONTROL Erzeugte Ausgabe löschen]**.
1. Um Webausgabeformate von PDF Rasterizer generieren zu lassen, wählen Sie **[!UICONTROL Webausgabe erstellen]**.

   ![generate_web_renditions](assets/generate_web_renditions.png)

1. Specify the settings in the **[!UICONTROL Web Enabled Image tab]**.

   ![web_enabled_image-1](assets/web_enabled_image-1.png)

1. Speichern Sie den Workflow.
1. Laden Sie eine PDF- oder AI-Datei in AEM Assets hoch. PDF Rasterizer erstellt die Miniaturansichten und Webausgaben für die Datei.
