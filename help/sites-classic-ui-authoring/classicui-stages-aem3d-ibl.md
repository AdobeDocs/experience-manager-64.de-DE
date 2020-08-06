---
title: Arbeiten mit IBL-Bühnen
seo-title: Arbeiten mit IBL-Bühnen
description: AEM 3D unterstützt die bildbasierte Beleuchtung (IBL) für die interaktive Anzeige und das Rendern mit dem integrierten Rapid Refine-Renderer von Adobe sowie mit Renderern von Drittanbietern. Sie können IBL-Bühnen mit herkömmlichen Authoring-Programmen wie Autodesk Maya oder Autodesk 3ds Max erstellen.
seo-description: AEM 3D unterstützt die bildbasierte Beleuchtung (IBL) für die interaktive Anzeige und das Rendern mit dem integrierten Rapid Refine-Renderer von Adobe sowie mit Renderern von Drittanbietern. Sie können IBL-Bühnen mit herkömmlichen Authoring-Programmen wie Autodesk Maya oder Autodesk 3ds Max erstellen.
uuid: 6598fb8a-65b0-4b84-8063-fdc94f6ea935
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: f9291151-851a-4aff-a50e-a24330ee0c13
translation-type: tm+mt
source-git-commit: e0ce860380a28a9dcaa6f8ce94ad278cdbe49fad
workflow-type: tm+mt
source-wordcount: '742'
ht-degree: 78%

---


# Arbeiten mit IBL-Bühnen{#about-working-with-ibl-stages}

AEM 3D unterstützt die bildbasierte Beleuchtung (IBL) für die interaktive Anzeige und für das Rendern mit dem integrierten Adobe Rapid Refine™ Renderer und den Renderern von Drittanbietern. Sie können IBL-Bühnen mit gängigen Authoring-Werkzeugen wie Autodesk® Maya® oder Autodesk® 3ds Max® erstellen.

## Bilder für IBL {#images-for-ibl}

Bilder, die für bildbasierte Beleuchtung verwendet werden, sollten über HDR (High Dynamic Range) verfügen, um optimale Ergebnisse zu erzielen. Sie müssen ein Länge/Breite-Format aufweisen. Dabei bietet die sphärische Zuordnung eine vollständige Abdeckung der Umgebung.

Derzeit unterstützt AEM 3D nur 32-Bit-TIFF-Dateien. Verwenden Sie gegebenenfalls Adobe Photoshop oder ein ähnliches Tool, mit dem das HDR-Bild in ein TIFF-Format konvertiert werden kann. Verwenden Sie dafür die folgenden Einstellungen im Dialogfeld „Adobe Photoshop TIFF-Export“:

* **[!UICONTROL Bittiefe]** - 32-Bit (Float)
* **[!UICONTROL Pixelreihenfolge]** - Interleaved (RGBRGB)
* **[!UICONTROL Bildkomprimierung]** - LZW
* **[!UICONTROL Byte Order]** - IBM PC

Häufig ist ein einziges HDR-Bild für IBL-Bühnen ausreichend. AEM 3D lässt jedoch bis zu drei separate Bilder zu und bietet so zusätzliche Steuerungsmöglichkeiten der IBL-Effekte:

* **[!UICONTROL Bild in einer Umgebung mit diffuser Beleuchtung]**: Dieser Bildtyp sollte ein HDR-Bild sein. Das Bild kann jedoch relativ klein sein, weil es vor seiner Verwendung für diffuse Beleuchtung stark gefiltert wird.
* **[!UICONTROL Bild in einer Umgebung mit Spiegelung]**: Dieser Bildtyp wird verwendet, um Reflexionen auf Objektoberflächen zu erstellen. Es kann sich um ein Standard-8-Bit-RGB-Bild handeln. Größe und Auflösung sind geeignet, um die Anforderungen an Qualität und Schärfe der Reflexionen zu erfüllen. Bei Angabe eines HDR-Bildes wandelt AEM 3D das Bild in 8-Bit-RGB um, bevor ein proprietärer Algorithmus verwendet wird.
* **[!UICONTROL Bild mit Hintergrund der Umgebung]**: Dieser Bildtyp wird als Hintergrund verwendet. Es kann sich um ein standardmäßiges 8-Bit-RGB-Bild handeln, das die gewünschte Größe/Auflösung/Detailebene für den Bühnenhintergrund aufweist. Wenn ein HDR-Bild angegeben ist, konvertiert AEM 3D dieses mithilfe eines proprietären Algorithmus in ein 8-Bit-RGB-Bild.

>[!NOTE]
>Der Umwandlungsalgorithmus kann bei bestimmten IBL-Bildern Probleme bereiten. Diese Probleme können dazu führen, dass Hintergrundbilder in der Vorschau oder beim Rendern mit Rapid Refine zu hell oder zu stark gesättigt sind. In solchen Fällen empfiehlt Adobe die Verwendung von Photoshop oder einem vergleichbaren Tool zur manuellen Umwandlung des IBL-Bildes in ein 8-Bit-RGB-Bild. Laden Sie dieses Bild separat hoch und fügen Sie es der Bühne als Hintergrundumgebungsbild hinzu. Die Umgebungsbilder für diffuse Beleuchtung und Reflexion müssen immer TIFF-Dateien von 32-Bit sein.


## Anpassen des Erscheinungsbildes der IBL-Bühnen {#adjusting-the-ibl-stage-appearance}

Sie können das Erscheinungsbild der IBL-Bühne mithilfe der folgenden Eigenschaften festlegen:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Eigenschaft</strong><br /> </td> 
   <td><strong>Beschreibung</strong></td> 
  </tr> 
  <tr> 
   <td>IBL-Sun-Details</td> 
   <td><p>Hiermit können Sie die Richtung und Stärke der zusätzlichen Lichtquelle einstellen, die die Sonne simuliert. <span class="diff-html-added">Diese Lichtquelle erhöht die Helligkeit der Beleuchtung und sorgt für einen Schlagschatten auf der Ausgangsebene. Der Schattenwurf wird beim Rendern mit Rapid Refine und in der Vorschau mit Google Chrome unterstützt. Von anderen Browsern wird er derzeit nicht unterstützt.</span></p> 
    <ul> 
     <li><strong>lat</strong> - Die vertikale Position der Lichtquelle (<code>0.0</code>-<code>1.0</code>).<br /> eine Einstellung von <code>0.0</code> ist am Horizont (vertikaler Mittelpunkt des Bilds für die diffuse Umgebung); <code>1.0</code> befindet sich am höchsten Punkt (obere Kante der Umgebung "Diffuse Lighting").</li> 
     <li><strong>long</strong> - Die horizontale Position der Lichtquelle (<code>0.0</code>-<code>1.0</code>).<br /> Die Einstellung 0,0 steht für die linke Ecke, 1,0 für die rechte Ecke des Umgebungsbildes für diffuse Beleuchtung.<br /> </li> 
     <li><strong>hell</strong> - Die Helligkeit der Sonnenlichtquelle. Erhöhen Sie diesen Wert, um die Sonnenlichtquelle aufzuhellen. Verringern Sie den Wert, um sie zu verdunkeln. <br /> Bei einer Einstellung werden zusätzliche Beleuchtung <code>0</code> deaktiviert und Schatten deaktiviert. Der Parameter wirkt sich nicht auf die Umgebungsreflexionen aus.<br /> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>IBL-Kamerahöhe</td> 
   <td>Wenn der IBL-Hintergrund in der Nähe des Horizonts verzerrt angezeigt wird, ist es möglich, die Verzerrung durch Anpassen dieser Eigenschaft zu reduzieren oder zu beseitigen. <br /> </td> 
  </tr> 
  <tr> 
   <td>Umgebung-Beleuchtung</td> 
   <td><p><span class="diff-html-added">Hiermit können Sie die diffuse Beleuchtung steuern. Wenn das Bild mit diffuser Beleuchtungsumgebung ungewöhnlich hell oder dunkel ist (beispielsweise Nachtszenen), müssen Sie diese Eigenschaft manuell korrigieren.</span></p> 
    <ul> 
     <li><strong>r, g, b</strong> - Derzeit nicht verwendet.</li> 
     <li><strong>hell</strong> - <span class="diff-html-added">Helligkeitsmultiplikator. Über diesen Wert können Sie die Gesamtlichtintensität (die grundlegende IBL-Beleuchtung und die Helligkeit der Sonnenlichtquelle) erhöhen und reduzieren.</span></li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

