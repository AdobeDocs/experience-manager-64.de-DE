---
title: Erweiterte Konfigurationseinstellungen
seo-title: Erweiterte Konfigurationseinstellungen
description: Erfahren Sie mehr über erweiterte Konfigurationseinstellungen, die für die Integration von AEM 3D für sowohl Maya- als auch Nicht-Maya-Bereitstellungen gelten.
seo-description: Erfahren Sie mehr über erweiterte Konfigurationseinstellungen, die für die Integration von AEM 3D für sowohl Maya- als auch Nicht-Maya-Bereitstellungen gelten.
uuid: 016e7745-e3c3-4d77-b95a-c0e671d719e2
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: e43fd002-2954-4ef1-ac2b-e8d45afa75be
exl-id: fdc82bca-e676-4052-b3e9-a198c685df96
feature: 3D-Assets
role: Administrator,Business Practitioner
translation-type: tm+mt
source-git-commit: 13eb1d64677f6940332a2eeb4d3aba2915ac7bba
workflow-type: tm+mt
source-wordcount: '1385'
ht-degree: 61%

---

# Erweiterte Konfigurationseinstellungen {#advanced-configuration-settings}

Während die Standardkonfigurationseinstellungen für typische Einsatzmöglichkeiten verwendet werden, sind in manchen Fällen möglicherweise Änderungen vorzunehmen.

Die folgenden erweiterten Konfigurationseinstellungen gelten für die Integration von AEM 3D für sowohl Maya- als auch Nicht-Maya-Bereitstellungen.

Auf alle Einstellungen wird mithilfe von **CRXDE Lite** in AEM (**[!UICONTROL Tools > Allgemein > CRXDE Lite]**) zugegriffen.

>[!NOTE]
>
>Wenn Sie das Paket neu installieren, werden alle Einstellungen auf die Standardwerte zurückgesetzt.

>[!CAUTION]
>
>Die Bearbeitung von Einstellungen, die nicht in der folgenden Tabelle aufgeführt sind, kann zu unerwartetem oder unerwünschtem Programmverhalten führen.

## Assettypen – Konfiguration {#asset-types-configuration}

Greifen Sie in **CRXDE Lite** in AEM (**[!UICONTROL Tools > Allgemein > CRXDE Lite]**) auf die folgenden Konfigurationen zu:

| Pfad | Beschreibung |
|---|---|
| `/libs/settings/dam/v3D/assetTypes/*/Conversion` | Legt den Dateityp des während der Aufnahme erstellten 3D-Zwischenformats fest. Muss bei den Dateiformaten „fbx“ und „obj“ leer sein oder bei durch Maya aktivierten Formaten „fbx“. |
| `/libs/settings/dam/v3D/assetTypes/*/Enabled` | Auf &quot;true&quot;oder &quot;false&quot;setzen, um diesen Eintrag in der Liste **[!UICONTROL assetTypes]** zu aktivieren oder zu deaktivieren. |
| `/libs/settings/dam/v3D/assetTypes/*/Extension` | Legen Sie eine oder mehrere durch Kommas getrennte Dateiendungen oder Dateierweiterungen fest, die diesem Assettyp zugewiesen werden. |
| `/libs/settings/dam/v3D/assetTypes/*/IngestRegime` | Muss für FBX- und OBJ-Dateiformate `native` und für Formate, die von Maya aktiviert werden, `maya` sein. |
| `/libs/settings/dam/v3D/assetTypes/*/MimeType` | Gibt den Mime-Typ für diesen Elementtyp an. Bei Formaten, die von Maya aktiviert werden, wird empfohlen, `application/x-ext` zu verwenden, wobei `ext` die als `Extension`-Wert angegebene Zeichenfolge ist. |

## Aufnahmekonfiguration {#ingestion-configuration}

Greifen Sie in **CRXDE Lite** in AEM (**[!UICONTROL Tools > Allgemein > CRXDE Lite]**) auf die folgenden Konfigurationen zu:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Pfad</strong></td> 
   <td><strong>Beschreibung</strong></td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/addGroundPlaneImageOnIngest</td> 
   <td>Aktiviert die Generation eines Ambient Occlusion-Schlagschattens beim Anzeigen oder Rendern mit einer IBL-Bühne. Gilt für die Vorschau und das Rendern mit RapidRefine</td> 
  </tr> 
  <tr> 
   <td><p>/libs/settings/dam/v3D/settings/cleanupRenderWorkDir</p> </td> 
   <td>Legen Sie den Parameter auf <strong>false</strong> fest, damit temporäre Dateien nach der Konversion und dem Rendern im MayaWork-Ordner bleiben. Kann beim Debuggen nützlich sein, wenn Sie Probleme bei der Maya-Konvertierung und dem Rendering haben.</td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/invokeAnimationOnIngest</td> 
   <td><p>Wenn die Option aktiviert ist, wird ImageMagick auf dem Server installiert und magickPath wird konfiguriert. Rapid Refine wird verwendet, um eine einfache Animation für 3D-Objekte zu erstellen, die als Miniaturbild in der Kartenansicht und in anderen Ansichten verwendet werden.</p> <p>Das Erstellen von Animationen verbraucht bedeutende CPU-Ressourcen während des Aufnahmeprozesses.</p> </td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/invokeLightMapsOnIngest</td> 
   <td>Aktiviert das automatische Erstellen von Licht-Maps bei der Aufnahme. Wird auf <strong>false</strong> gesetzt, um die automatische Erstellung von Light-Maps zu deaktivieren. Dadurch kann der CPU-Verbrauch erheblich gesenkt werden, allerdings zu Lasten der Qualität der Vorschau und des Renderns mit Rapid Refine. Hat keine Auswirkungen auf das Rendern mit Maya.</td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/gPlaneZero</td> 
   <td><p>Bei Festlegung auf <strong>true</strong> (Standard) werden Objekte ggf. vertikal verschoben, um sicherzustellen, dass sich alle Teile des Objekts über der Bodenebene befinden (y=0).</p> <p>Bei Festlegung auf <strong>false</strong> (Standard) werden Objekte nicht neu positioniert und können teilweise durch die Bodenebene einer Bühne ausgeblendet werden. (Gilt nur für Vorschau und Rendering mit Rapid Refine.) Wirkt sich jedoch nicht auf das Rendern mit Maya aus. Bei Festlegung auf <strong>true</strong> kann die vertikale Position von Objekten in Maya anders sein als in der Vorschau oder beim Rendering mit Rapid Refine.</p> </td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/Paths/magickPath</td> 
   <td>Der Pfad und der Name zum ImageMagick-Konversionsprogramm. Ein absoluter Pfad ist erforderlich, wenn die animierte Miniaturbilderstellung aktiviert ist.</td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/MaxCpuPercentage</td> 
   <td><p>Legt fest, wie viele CPUs maximal für die Aufnahmeverarbeitung von 3D-Objekten verwendet werden.</p> <p>Höhere Werte beschleunigen die Aufnahmen, können aber dazu führen, dass AEM insgesamt langsamer reagiert. Diese Einstellung ist approximativ. Das heißt, die Genauigkeit steigt mit der Anzahl von verfügbaren CPU-Kernen.</p> </td> 
  </tr> 
 </tbody> 
</table>

## Konfigurationseinstellungen für Cloud Services {#cloud-services-configuration-settings}

Die Werte für die folgenden Einstellungen werden von Ihrem Kundenbetreuer, Bereitstellungsexperten oder Supportmitarbeiter bereitgestellt.

| **Pfad** | **Beschreibung** |
|---|---|
| `/libs/settings/dam/v3D/services/aws/accountId` | Die Konto-ID des Adobe AWS-Kontos. |
| `/libs/settings/dam/v3D/services/aws/bucketName` | Name des S3-Übertragungsbehältnisses; normalerweise `aem3d`. |
| `/libs/settings/dam/v3D/services/aws/customerId` | Die eindeutige ID, die Ihrer Organisation durch Adobe zugewiesen wird. Wird als AWS-Kognito-Benutzer-ID verwendet. |
| `/libs/settings/dam/v3D/services/aws/encryptedPassword` | Das mit dieser customerId verknüpfte Kennwort. Wird als AWS-Kognito-Kennwort verwendet. |
| `/libs/settings/dam/v3D/services/aws/region` | Die AWS-Region, in der die Cloud-Dienste bereitgestellt werden. |
| `/libs/settings/dam/v3D/services/aws/userPoolId` | Die entsprechende AWS-Kognito-Benutzer-Pool-ID. |
| `/libs/settings/dam/v3D/services/dncr/clientId` | Die AWS-Cognito-Client-ID für den CDN-Konvertierungsdienst. |

## Allgemeine Verarbeitungseinstellungen {#common-processing-settings}

Greifen Sie in **CRXDE Lite** in AEM (**[!UICONTROL Tools > Allgemein > CRXDE Lite]**) auf die folgenden Konfigurationen zu:

| **Pfad** | **Beschreibung** |
|---|---|
| `/libs/settings/dam/v3D/Paths/mayaWorkPath` | Der Name und der Speicherort des Arbeitsordners für Umwandlung und Rendering mit Maya. Der Ordner wird automatisch erstellt, wenn er nicht vorhanden ist. |
| `/libs/settings/dam/v3D/Paths/maxWorkPath` | Name und Speicherort des Arbeitsordners für die maximale Konvertierung von 3ds. Der Ordner wird automatisch erstellt, wenn er nicht vorhanden ist. |
| `/libs/settings/dam/v3D/settings/debugNative` | Auf **[!UICONTROL true]** gesetzt, um das Erstellen von Debugging-Informationen während der Formatkonversion und dem Rendering mit dem RapidRefine-Renderer zu aktivieren. |

## Renderer-Konfiguration {#renderer-configuration}

Greifen Sie in **CRXDE Lite** in AEM (**[!UICONTROL Tools > Allgemein > CRXDE Lite]**) auf die folgenden Konfigurationen zu:

| **Pfad** | **Beschreibung** |
|---|---|
| `/libs/settings/dam/v3D/settings/dynamicIBL` | Wenn auf **[!UICONTROL true]** gesetzt und wenn keine vorgenerierten Licht-Maps verfügbar sind (d. h. invokeLightMapsOnIngest=false), erstellt der Rapid Refine-Renderer während des Renderns Licht-Maps, um die Rendering-Qualität zu verbessern. Diese Einstellung kann die Rendering-Zeit wesentlich verlängern. Wenn auf **[!UICONTROL false]** gesetzt, wird die CPU-Auslastung in solchen Fällen minimiert, aber die Rendering-Qualität kann schlechter werden. |
| `/libs/settings/dam/v3D/renderers/*/Enabled` | Auf **[!UICONTROL true]** oder **[!UICONTROL false]** festgelegt, um einen Renderer zu aktivieren bzw. zu deaktivieren. |
| `/libs/settings/dam/v3D/renderers/*/Display` | Erlaubt Ihnen, die Zeichenfolge zu ändern, die im Rendering-Feld in der Renderer-Auswahl für einen aktivierten Renderer angezeigt wird. |
| `/libs/settings/dam/v3D/renderers/*/MaxCpuPercentage` | Legt fest, wie viele CPUs maximal für das Rendern von 3D-Szenen verwendet werden. Höhere Werte beschleunigen das Rendern, können aber dazu führen, dass AEM insgesamt langsamer reagiert. Diese Einstellung ist approximativ. Das heißt, die Genauigkeit steigt mit der Anzahl von verfügbaren CPU-Kernen. |

## Einstellungen für die 3D-Asset-Vorschau {#d-asset-preview-settings}

Greifen Sie in **CRXDE Lite** in AEM (**[!UICONTROL Tools > Allgemein > CRXDE Lite]**) auf die folgenden Konfigurationen zu:

| Pfad | Beschreibung |
|---|---|
| `/libs/settings/dam/v3D/WebGLSites/autoSpin` | Setzen Sie diese auf **[!UICONTROL true]** oder **[!UICONTROL false]**, um die automatische Rotation (automatische Camera-Umlaufbahn) beim Laden der Seite zu aktivieren oder zu deaktivieren. |
| `/libs/settings/dam/v3D/WebGLSites/autoSpinAfterReset` | Auf **[!UICONTROL true]** setzen, um die automatische Rotation nach dem Drücken von **[!UICONTROL Zurücksetzen]** neu zu starten. Wird ignoriert, wenn die automatische Rotation deaktiviert ist. |
| `/libs/settings/dam/v3D/WebGLSites/autoSpinSpeed` | Legt die Geschwindigkeit (Umdrehungen pro Minute) und Richtung der automatischen Rotation fest. Dabei stehen negative Werte für das Drehen von rechts nach links und positive Werte für das Drehen von links nach rechts. |
| `/libs/settings/dam/v3D/WebGL/continueRotate` | Auf **[!UICONTROL false]** setzen, um die Fortsetzung mit einem allmählichen Ausblenden der Viewer-Antworten auf Berührungs- und Mausgesten zu deaktivieren. |
| `/libs/settings/dam/v3D/WebGL/curtainColor` | Legt die Farbe des Ladevorhangs fest, der den Viewport der 3D-Asset-Vorschau beim Laden und der Initialisierung optional bedecken kann. RGB-Wert, wobei sich die einzelnen Farbkomponenten im Bereich von 0 bis 255 befinden. |
| `/libs/settings/dam/v3D/WebGL/fadeCurtains` | Bei Festlegung auf **[!UICONTROL true]** wird der Load-Vorhang während der letzten Schritte der Viewer-Initialisierung allmählich ausgeblendet. Bei Festlegung auf **[!UICONTROL false]** bleibt der Vorhang undurchsichtig, bis das Laden und die Initialisierung abgeschlossen sind. |
| `/libs/settings/dam/v3D/WebGL/showCurtains` | Auf **[!UICONTROL true]** oder **[!UICONTROL false]** setzen, um den Ladevorhang für die 3D-Asset-Vorschau zu aktivieren oder zu deaktivieren. |
| `/libs/settings/dam/v3D/WebGL/spinHeight` | Wenn die automatische Rotation aktiviert wurde, wird die vertikale Position der Kamera automatisch relativ zur Höhe des 3D-Objekts angepasst. Wenn dieser Wert auf 0,5 gesetzt wird, wird die Kamera auf halber Höhe vertikal zum Objekt platziert. Dadurch wird der Horizont vertikal zum Viewport zentriert. Höhere Werte führen dazu, dass die Kamera auf das Objekt herabblickt und der gerenderte Horizont angehoben wird. Niedrigere Werte hingegen führen dazu, dass die Kamera zum Objekt aufblickt und der Horizont gesenkt wird. |

## Einstellungen der Komponente &quot;3D-Sites&quot; {#d-sites-component-settings}

Greifen Sie in **CRXDE Lite** in AEM (**[!UICONTROL Tools > Allgemein > CRXDE Lite]**) auf die folgenden Konfigurationen zu:

| Pfad | Beschreibung |
|---|---|
| `/libs/settings/dam/v3D/WebGLSites/autoSpinAfterReset` | Auf **[!UICONTROL true]** setzen, um die automatische Rotation (automatische Kameradorbit) zu reaktivieren, nachdem die Startseite gedrückt wurde. Wird ignoriert, wenn die automatische Rotation deaktiviert ist. |
| `/libs/settings/dam/v3D/WebGLSites/continueRotate` | Auf **[!UICONTROL false]** setzen, um die Fortsetzung mit einem allmählichen Ausblenden der Viewer-Antworten auf Berührungs- und Mausgesten zu deaktivieren. |
| `/libs/settings/dam/v3D/WebGLSites/curtainColor` | Legt die Farbe des Ladevorhangs fest, der den Viewport der 3D-Sites-Komponente beim Laden optional bedecken kann. RGB-Wert, wobei sich die einzelnen Farbkomponenten im Bereich von 0 bis 255 befinden. |
| `/libs/settings/dam/v3D/WebGLSites/fadeCurtains` | Bei Festlegung auf **[!UICONTROL true]** wird der Ladeluftvorhang während der letzten Ladevorgänge und Initialisierungen allmählich ausgeblendet. Bei Festlegung auf **[!UICONTROL false]** bleibt der Vorhang undurchsichtig, bis das Laden und die Initialisierung abgeschlossen sind. |
| `/libs/settings/dam/v3D/WebGLSites/showCurtains` | Auf **[!UICONTROL true]** oder **[!UICONTROL false]** setzen, um den Ladevorhang für die Komponente &quot;3D-Sites&quot;zu aktivieren oder zu deaktivieren. |
| `/libs/settings/dam/v3D/WebGLSites/spinHeight` | Wenn die automatische Rotation aktiviert wurde, wird die vertikale Position der Kamera automatisch relativ zur Höhe des 3D-Objekts angepasst. Wenn dieser Wert auf 0,5 gesetzt wird, wird die Kamera auf halber Höhe vertikal zum Objekt platziert. Dadurch wird der Horizont vertikal zum Viewport zentriert. Höhere Werte führen dazu, dass die Kamera auf das Objekt herabblickt und der gerenderte Horizont angehoben wird. Niedrigere Werte hingegen führen dazu, dass die Kamera zum Objekt aufblickt und der Horizont gesenkt wird. |
