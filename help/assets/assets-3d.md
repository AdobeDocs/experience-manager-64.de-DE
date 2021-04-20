---
title: Arbeiten mit AEM 3D-Assets
description: Erfahren Sie, wie Sie in AEM 3D mit 3D-Assets arbeiten.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: introduction
content-type: reference
exl-id: 3cee9b4f-c4be-4ffc-970c-5680c8ebba47
feature: 3D Assets
role: Administrator,Business Practitioner
translation-type: tm+mt
source-git-commit: 13eb1d64677f6940332a2eeb4d3aba2915ac7bba
workflow-type: tm+mt
source-wordcount: '1177'
ht-degree: 74%

---

# Arbeiten mit AEM 3D-Assets {#working-with-d-assets}

>[!IMPORTANT]
>
>AEM 3D in AEM 6.4 wird nicht mehr unterstützt. Adobe empfiehlt, die Funktion für 3D-Elemente in [AEM als Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/dynamicmedia/assets-3d.html) oder [AEM 6.5.3 oder höher zu verwenden.](https://experienceleague.adobe.com/docs/experience-manager-65/assets/dynamic/assets-3d.html#dynamic)

Mit AEM 3D (Adobe Experience Manager 3D) können Sie 3D-Inhalte hochladen, verwalten, anzeigen und rendern. Die Unterstützung für das Anzeigen und Rendern ist für einzelne Objekte optimiert.

Siehe auch [Versionshinweise zu AEM 3D](/help/release-notes/aem3d-release-notes.md).

Siehe auch [Installieren und Konfigurieren von AEM 3D](install-config-3d.md).

## Modelle und Bühnen in AEM 3D {#about-models-and-stages-in-aem-d}

Mit AEM 3D können Sie statische, eigenständige 3D-Modelle hoher Qualität in vordefinierten Umgebungen anzeigen und rendern, die als „Bühnen“ (Englisch: Stages) bezeichnet werden. Eine Bühne bildet die Grundlage („Beleuchtung“) für die 3D-Szene und stellt die Einstellungen für das Rendern in einer nativen Anwendung bereit, z. B. Autodesk® Maya® oder Autodesk 3ds Max®. Darüber hinaus kann die Bühne optional vordefinierte Kameras, Hintergründe sowie eine Grundebenengeometrie enthalten.

Hochgeladene 3D-Dateien, die „Beleuchtungselemente“ enthalten, werden als Bühne angesehen. Sie können diese Assets zurück in einfache 3D-Objekte verwandeln, indem Sie das Asset auf der Seite mit den Asset-Details öffnen. Tippen Sie auf **[!UICONTROL Eigenschaften anzeigen]** und dann auf die Registerkarte **[!UICONTROL Allgemein]**. Wählen Sie unter der Überschrift „Metadaten“ in der Dropdown-Liste „Asset-Klasse“ die Option **[!UICONTROL 3D-Objekt]**.

Beachten Sie Folgendes, wenn Sie 3D-Modelle für die Verwendung in AEM 3D erstellen:

* Ihre 3D-Modelldateien sollten nur ein Objekt und keine Hintergründe, Grundebenen, Szenenbeleuchtungen oder Kameras enthalten.
* Platzieren Sie das Modell auf der Grundebene. Diese Positionierung ist besonders wichtig, wenn Sie das Anzeigen oder Rendern mit Bühnen durchführen, die über eine Grundebene verfügen. Es ist eine Konfigurationseinstellung verfügbar (standardmäßig aktiviert), mit der das Objekt über der Grundebene bewegt wird, wenn Sie Rapid Refine für das Anzeigen als Vorschau oder das Rendern verwenden. Diese Einstellung hat keine Auswirkung auf das Rendern mit Renderern von Drittanbietern (z. B. per Maya), sodass Objekte, die nicht oberhalb der Grundebene angeordnet sind, ggf. teilweise ausgeblendet werden.
* Positionieren Sie das Modell so, dass es in passender Weise seitlich in der Nähe des Koordinatensystemursprungs (0,0,0) zentriert ist. Auf diese Weise erzielen Sie ein gutes Ergebnis in Bezug auf die interaktive Anzeige.
* Neben Texturmaps werden auch externe Dateiverweise unterstützt. Aus diesem Grund ist es erforderlich, dass Sie alle referenzierten Inhalte in die primäre Modelldatei einbetten, bevor Sie sie in AEM hochladen.

   Siehe [Informationen zum Hochladen und Verarbeiten von 3D-Assets in AEM](upload-processing-3d-assets.md).

* Die allgemeine Beleuchtung der Szene wird von der Bühne bereitgestellt. Daher wird von Adobe nicht empfohlen, Beleuchtungselemente in 3D-Modelldateien einzubinden. Sie können Beleuchtungselemente in das Modell einfügen. Diese müssen aber spezifisch für das Modell gelten. Beispielsweise kann es erforderlich sein, zusätzliche Beleuchtung einzubinden, um einen Teil des Objekts aufzuhellen, der von anderen Teilen verdunkelt wird. Allein mit den Beleuchtungselementen der Bühne wäre keine ausreichende Sichtbarkeit gegeben.

## Unterstützte Dateien in AEM 3D {#supported-files-in-aem-d}

Ein typisches 3D-Asset verfügt über eine primäre Modelldatei und ggf. referenzierte Dateien. Zu den referenzierten Dateien gehören beispielsweise Texturmaps oder **IBL (Image-Based Lighting)**-Bilder.

### Informationen zur primären 3D-Modelldatei {#about-the-primary-d-model-file}

Die primäre 3D-Modelldatei enthält die eigentliche 3D-Modellgeometrie und Definitionen für die (standardmäßigen) Materialien, die auf die Modelloberflächen angewendet werden. AEM 3D unterstützt für primäre 3D-Modelldateien die folgenden Formate:

* Wavefront-OBJ-Dateiformat (`.obj`)

   Das OBJ-Format erfordert eine oder mehrere separate, externe MTL-Dateien (Materialvorlagenbibliothek) (`.mtl`).

* Autodesk FBX (Filmbox)-Dateiformat (`.fbx`)

   das Format für den Austausch von 3D-Dateien von Autodesk; sowohl binäre als auch ASCII-Formate.

   Für die Erstellung von FBX-Dateien in Drittanbieteranwendungen empfiehlt Adobe die folgenden Konfigurationseinstellungen (siehe Tabelle unten). Mit diesen Einstellungen können Sie die besten Ergebnisse für 3D-Dateien erzielen, die Sie in AEM nutzen möchten. Die Namen der Optionen werden aus dem Dialogfeld **[!UICONTROL Autodesk Maya FBX Exportoptionen]** entnommen.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Option im Dialogfeld "Autodesk Maya FBX Export"</strong></td> 
   <td><strong>Beschreibung</strong></td> 
  </tr> 
  <tr> 
   <td>Verweise beibehalten<br /> </td> 
   <td><p>Auswahl aufheben.</p> <p>Für AEM 3D werden derzeit keine externen Verweise unterstützt.</p> </td> 
  </tr> 
  <tr> 
   <td>Glattes Mesh<br /> </td> 
   <td>Wählen Sie nun eine der folgenden Optionen aus.</td> 
  </tr> 
  <tr> 
   <td>Konvertieren von NURBS-Oberflächen in</td> 
   <td><strong>Software Render Mesh</strong></td> 
  </tr> 
  <tr> 
   <td>Animation</td> 
   <td><p>Auswählen oder Aufheben der Auswahl.</p> <p>Wenn Sie diese Option aktivieren, werden die Animationsinformationen in der Datei von AEM 3D ignoriert.</p> </td> 
  </tr> 
  <tr> 
   <td>Kameras</td> 
   <td><p>Wählen Sie für <strong>3D-Stufen</strong>.</p> <p>Deaktivieren Sie die Option für 3D-Modelle.</p> </td> 
  </tr> 
  <tr> 
   <td>Lichter</td> 
   <td><p>Wählen Sie für <strong>3D-Stufen</strong>.</p> <p>Deaktivieren Sie die Option für <strong>3D-Modelle</strong>.</p> </td> 
  </tr> 
  <tr> 
   <td>Einheiten - Automatisch</td> 
   <td>Wählen Sie nun eine der folgenden Optionen aus. AEM 3D führt die Konvertierung während des Imports durch.</td> 
  </tr> 
  <tr> 
   <td>Achsenumrechnung - Up-Achse</td> 
   <td><p><strong>Y-up</strong></p> <p>Y-up liefert konsistente Ergebnisse beim Export aus Maya und ist das bevorzugte Koordinatensystem für FBX-Dateien in dieser AEM 3D-Version.</p> </td> 
  </tr> 
  <tr> 
   <td>Medien einbetten</td> 
   <td>Beide Optionen werden unterstützt. Wenn "Eingebettet"ausgewählt ist, extrahiert AEM 3D die eingebetteten Medien in einen angrenzenden Ordner, der denselben Namen wie die Modelldatei hat, an die <code>.fbm</code> angehängt wurde.</td> 
  </tr> 
  <tr> 
   <td>FBX-Dateiformat - Typ</td> 
   <td>Sowohl <strong>Binary </strong>als auch <strong>ASCII </strong>werden unterstützt.</td> 
  </tr> 
  <tr> 
   <td>FBX-Dateiformat - Version</td> 
   <td>FBX 2014/2015 wird empfohlen. Andere Versionen funktionieren ggf. auch.</td> 
  </tr> 
 </tbody> 
</table>

Die folgenden zusätzlichen Dateiformate werden unterstützt, wenn Autodesk Maya auf AEM-Erstellungsservern installiert und konfiguriert ist:

* Autodesk Maya

   Sowohl ASCII `.ma`- als auch binäre `.mb`-Formate.

* `Jupiter Tesselation (ISO 14306-1).jt`.

   Ein branchenübliches CAD-Format für Datenaustausch, Zusammenarbeit und Produktvisualisierung.

### Unterstützung von Texturmap-Dateien {#support-for-texture-map-files}

Materialdefinitionen in 3D-Modelldateien können Verweise auf externe Bilddateien enthalten, über die Texturmaps bereitgestellt werden. AEM 3D unterstützt die folgenden Arten von Texturmap-Dateien:

* Diffuse Farbtexturen
* Spiegelnde Farbtexturen
* Umgebungsfarbtexturen
* Verschiebungsmatrizen (auch als Bump-Maps bezeichnet)
* Normale Maps
* Opazitäts-Maps
* Rauheits-Maps (auch als Gloss-, Reflectivity- oder Cosine Power-Maps bezeichnet)

Materialien in der primären 3D-Modelldatei können auf andere Arten von Karten verweisen, die von AEM 3D ignoriert werden.

### IBL-Bilder (Image-Based Lighting) {#ibl-image-based-lighting-images}

In einer 3D-Modelldatei, mit der eine Bühne definiert wird, kann jeweils auf ein IBL-Umgebungsbild verwiesen werden. Derzeit unterstützt AEM 3D für diffuses IBL und für Spiegelungen nur 32-Bit-TIFF-Bilder im Breitengrad/Längengrad-Format. Für einen kugelförmigen Szenenhintergrund werden auch 8-Bit-RGB-Bilder unterstützt.

Weitere Informationen finden Sie unter [Arbeiten mit IBL-Bühnen](working-with-ibl-stages.md).

>[!NOTE]
>
>Dateiverweise (mit Ausnahme der oben beschriebenen), die in der primären 3D-Modelldatei enthalten sind, werden derzeit ignoriert. AEM 3D unterstützt keine Verweise auf sekundäre 3D-Modelldateien.
Y-up ist das bevorzugte Koordinatensystem für FBX-Dateien in dieser Version.

## Materialschattierungen in einer primären 3D-Modelldatei {#material-shading-in-a-primary-d-model-file}

Die ursprüngliche native Modelldatei kann Materialdefinitionen enthalten, die mit Shadern, z. B. Blinn oder Lambert, oder mit vorgangsorientierten Shadern verwendet werden. Diese potenziell komplexen Materialien werden nur unterstützt, wenn Sie das Rendern mit der entsprechenden nativen Anwendung (z. B. Autodesk Maya) durchführen.

Zu Anzeigezwecken oder beim Rendern mit dem standardmäßigen Rapid Refine™-Renderer werden alle Materialien entweder vereinfacht, ausgetauscht oder beides, damit sie mit einem Phong-ähnlichen Shader verwendet werden können. Dieser Shader unterstützt einen begrenzten Satz von Attributen. Andere Attribute der Materialdefinition werden ignoriert.

Weitere Informationen finden Sie unter [Anzeigen von 3D-Assets](viewing-3d-assets.md)

Weitere Informationen finden Sie unter [Rendern von 3D-Assets](rendering-3d-assets.md).

## Benennen von Materialien in einer primären 3D-Modelldatei {#naming-materials-in-a-primary-d-model-file}

Eine *Oberfläche* ist als der Oberflächenbereich eines 3D-Modells definiert, der von demselben Material bedeckt ist. Dieses Material gibt der Oberfläche auch ihren Namen. Daher empfiehlt Adobe, die in primären 3D-Modelldateien enthaltenen Materialien entsprechend zu benennen. Beispielsweise wird die Verwendung bestimmter Namen wie &quot;Körper&quot;, &quot;Windows&quot;, &quot;Reifen&quot;oder &quot;Rims&quot;der Verwendung vager Namen wie &quot;Rot&quot;, &quot;Glas&quot;, &quot;Gummi&quot;oder &quot;Aluminium&quot;vorgezogen.
