---
title: AEM 3D – Versionshinweise
seo-title: AEM 3D – Versionshinweise
description: Spezifische Versionshinweise für 3D-Inhalt in Adobe Experience Manager Assets.
seo-description: Spezifische Versionshinweise für 3D-Inhalt in Adobe Experience Manager Assets.
uuid: 6675951f-86f0-4ec5-97e4-d247f6faf913
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
content-type: reference
topic-tags: 3D
discoiquuid: 9789d031-fb7e-415a-a9c3-8b8fde978238
translation-type: tm+mt
source-git-commit: f8ba597c62379ba413309303c2ad066ab7afce1e
workflow-type: tm+mt
source-wordcount: '1933'
ht-degree: 46%

---


# AEM 3D – Versionshinweise {#aem-d-release-notes}

AEM-6.4-DynamicMedia-3D Version 3.1.0 (10. Oktober 2018)

Das AEM 3D Feature Pack ermöglicht die Unterstützung von 3D-Inhalten in AEM Assets. Es bietet Funktionen zum Hochladen, Verwalten und Wiedergeben sowie zur Vorschau von 3D-Assets. Die Unterstützung für Anzeige und Wiedergabe ist für einzelne Objekte optimiert (und nicht für komplexe Szenen mit mehreren Objekten).

AEM 3D unterstützt die Asset-Typen Adobe Dimension (Dn) und glTF. Die Implementierung für diese Asset-Typen unterscheidet sich wesentlich von der für herkömmliche 3D-Typen, die in dieser Dokumentation beschrieben werden. Siehe [Arbeiten mit Adobe Dimension-Assets](/help/assets/working-dimension-assets.md).

Dazu gehören auch serverseitige Integrationen mit Autodesk® Maya® (nur Windows). Wenn Sie Maya auf demselben Server installieren und konfigurieren wie AEM, aktivieren Sie die Unterstützung für native Maya-Dateiformate, darunter die hochwertige Wiedergabe mit dem NVIDIA® Mental Ray Standalone Plug-in für Maya. Die Installation und Konfiguration von 3ds Max auf dem Server ermöglicht die Unterstützung des nativen .max-Dateiformats.

Weitere Informationen finden Sie unter [Integration in Autodesk Maya](/help/assets/integrate-maya-with-3d.md).

Siehe auch [Installieren und Konfigurieren von AEM 3D Assets](/help/assets/install-config-3d.md) und [Erweiterte Konfigurationseinstellungen](/help/assets/advanced-config-3d.md).

Siehe auch [Arbeiten mit 3D-Assets](/help/assets/assets-3d.md).

## Systemanforderungen {#system-requirements}

**Voraussetzungen**

* AEM 6.4.2 (AEM 6.4 mit Service Pack 2)
* Autodesk® FBX® SDK 2016.1.2

**Unterstützte Betriebssysteme**

* Microsoft Windows 2012 Server oder höher
* Apple OS X El Capitan 10.6 oder höher
* RedHat Enterprise Linux 7.3

**Unterstützte Webbrowser für AEM Assets**

* Google Chrome 53 oder höher (empfohlen)
* Apple Safari 9.1 oder höher
* Firefox 48 oder höher
* Microsoft Edge 25.10586 oder höher

Andere Browser unterstützen möglicherweise keine interaktive Anzeige von 3D-Inhalten in AEM. Nur Google Chrome unterstützt die Option „Wirft Schatten“ in der Vorschau.

**Hardwareanforderungen und -empfehlungen**

* CPU – 3D-Verarbeitung und -Rendering nimmt die CPU eines Computers stark in Anspruch. Entsprechend wird ein moderner Server mit mindestens acht CPU-Kernen empfohlen.
* Speicher – Empfohlen werden mindestens 32 GB.
* Massenspeicherung – Empfohlen wird ein SSD-Speicher mit hoher Bandbreite.

   Beim Hochladen werden 3D-Assets in ein proprietäres Format umgewandelt, um eine schnelle, interaktive Anzeige zu ermöglichen. Je nach Art des 3D-Assets ist eine Speicherkapazität erforderlich, die 2- bis 3-mal so groß ist wie das hochgeladene 3D-Asset.

Siehe auch [Arbeiten mit 3D-Assets](/help/assets/assets-3d.md).

## Installieren und Konfigurieren von AEM 3D {#installing-and-configuring-aem-d}

Siehe [Installieren und Konfigurieren von AEM 3D](/help/assets/install-config-3d.md).

Siehe auch [Integration von AEM 3D mit Autodesk Maya](/help/assets/integrate-maya-with-3d.md) und [Integration von AEM 3D mit Autodesk 3ds Max](/help/assets/integrating-aem-3d-with-autodesk-3ds-max.md).

## Unterstützte 3D-Dateiformate {#supported-d-file-formats}

| Format | Beschreibung | Plattformen | Hinweise |
|--- |--- |--- |--- |
| DN | Adobe Dimension | Alle | Erfordert Zugriff auf einen Cloud-basierten Konvertierungsdienst. |
| GLTZ | Zip gITF | Alle |  |
| GLB | BinärgITF | Alle | Nur Download (GLB-Darstellungen werden für DN-Elemente erstellt). |
| OBJ | Wavefront OBJ 3D | Alle |  |
| FBX | Autodesk FBX (Kaydara Filmbox) | Alle | Das Autodesk FBX SDK muss auf dem Autorknoten installiert sein. |
| MA, MB | Native Autodesk Maya-Dateien | Nur Windows | Autodesk Maya ist auf dem Autorknoten erforderlich, um diese Dateiformate zu aktivieren. Siehe [Integration von AEM 3D mit Autodesk Maya](/help/assets/integrate-maya-with-3d.md). |
| JT | Open CAD-Dateien von Siemens PLM | Nur Windows | Autodesk Maya ist auf dem Autorknoten erforderlich, um diese Dateiformate zu aktivieren. Siehe [Integration von AEM 3D mit Autodesk Maya](/help/assets/integrate-maya-with-3d.md). |
| * | Es können zusätzliche, von Autodesk Maya unterstützte 3D-Eingabeformate aktiviert werden. See [Enabling Additional Formats Supported by Maya](/help/assets/integrate-maya-with-3d.md#enabling-additional-formats-supported-by-maya). | Nur Windows | Autodesk Maya ist auf dem Autorknoten erforderlich, um diese Dateiformate zu aktivieren. Siehe [Integration von AEM 3D mit Autodesk Maya](/help/assets/integrate-maya-with-3d.md). |
| MAX | Native Autodesk 3ds Max | Nur Windows | Autodesk 3ds Max ist auf dem Autorenknoten erforderlich, um dieses Dateiformat zu aktivieren. Siehe [Integration von AEM 3D mit Autodesk 3ds Max](/help/assets/integrating-aem-3d-with-autodesk-3ds-max.md). |

## Verbesserungen und neue Funktionen {#enhancements-and-new-features}

Version 3.0

* Unterstützung für Autodesk 3ds Max natives Dateiformat.
* Verschiedene Änderungen und Fehlerkorrekturen zur Verbesserung von Stabilität, Qualität und Benutzerfreundlichkeit.
* Konfigurationseinstellungen verschoben auf `/libs/settings/dam/v3d/`

Version 3.1

* Eingeschränkte Unterstützung für das native Adobe Dimension-Dateiformat (.dn).
* Ein neuer 3D-Viewer für glTF-Assets.
* Eine neue Schnittstelle zu einem Cloud-basierten, von Adoben verwalteten Konvertierungsdienst, der in Amazon AWS gehostet wird. Zuerst konvertiert dieser Dienst nur vom Dn- in das glTF-Format.

## Einschränkungen und bekannte Probleme {#restrictions-and-known-issues}

### Adobe Dimension-Support {#adobe-dimension-support}

* Diese Version von AEM3D bietet eingeschränkte Unterstützung für .dn-Dateien, die mit Adobe Dimension erstellt wurden.
* Während der Upload-Verarbeitung AEM einen Cloud-basierten Konvertierungsdienst, der von der Adobe gehostet wird, nutzen, um eine glTF-Darstellung aus der nativen .dn-Datei zu erstellen. Der Zugriff auf den Konvertierungsdienst und die Auswahl der Amazon AWS-Endpunkte sind erforderlich.
* Es wird ein neuer glTF-Viewer bereitgestellt, der die Anzeige von Dn-Assets in AEM Assets und in Sites/Bildschirmen unterstützt. Die Unterstützung für Phasen im Viewer ist noch nicht verfügbar.
* Dn-Modelle können IBL-Lichter und -Hintergründe einbetten, die angezeigt werden, sofern vorhanden. Alternativ dazu wendet der Viewer eine Standardbeleuchtung oder eine standardmäßige Hintergrundfarbe oder beides an.
* Das hochwertige Rendering für DN-Assets ist noch nicht verfügbar.
* Abhängigkeiten wie Texturmaps werden in DN-Assets eingebettet und können nicht explizit in AEM verwaltet werden.

### Kompatibilität {#compatibility}

* **Das Ausführen als Windows-Dienst wird nicht unterstützt (nur Windows)** – Ggf. funktioniert dies, es wurde jedoch nicht getestet.
* **Dynamic Media** ( `dynamicmedia-scene7` Modus) - Die Kompatibilität von AEM3D mit der neuen Dynamic Media-Lösung, die mit AEM 6.4 veröffentlicht wurde, wurde noch nicht vollständig überprüft. Wenn Dynamic Media und AEM3D zusammen bereitgestellt werden, sollten Sie 3D-Elemente und deren Abhängigkeiten nur in einem Bereich des AEM Assets-Repositorys platzieren, der nicht Dynamic Media zugewiesen ist. Diese Empfehlung ist besonders wichtig für 32-Bit-TIFF-Dateien, die für 3D-Phasen erforderlich sind, aber von Dynamic Media nicht unterstützt werden.

### Allgemein {#general}

* **Verknüpfung „Abhängigkeiten auflösen“** – Diese Verknüpfung ist in der Kartenansicht der 3D-Assets verfügbar. Asset-Karten in der Kartenansicht werden im Banner „Nicht aufgelöste Abhängigkeiten“ angezeigt. Über die Verknüpfung wird die Registerkarte **Allgemeine Eigenschaften** anstelle der Registerkarte **Abhängigkeiten** geöffnet. Problemumgehung: Navigieren Sie manuell zur Registerkarte „Abhängigkeiten“.

* **Bühnenauswahl nicht verfügbar** – 3D-Assets, die Lichter beinhalten, werden von AEM automatisch mit Tags als 3D-Bühnen gekennzeichnet. In der Detailansicht ist keine Bühnenauswahl verfügbar. Um ein 3D-Asset als 3D-Objekt zu markieren, navigieren Sie zu **Allgemeine Eigenschaften**, ändern Sie **Asset-Klasse** in **3D-Objekt** und klicken Sie auf **Speichern**.

* **3D-Assets mit abhängigen Elementen und Darstellungen herunterladen** – Beim Herunterladen von 3D-Assets von AEM mit aktivierten Optionen **Abhängigkeiten** und **Darstellungen** enthält der Download nicht nur die Ausgaben des primären 3D-Assets, sondern auch die Ausgaben aller abhängigen Elemente.

* **Autodesk 3ds Max. Integration** - Rendering mit 3ds Max wird derzeit nicht unterstützt.

### Dateitypbeschränkungen {#file-type-restrictions}

* **Mathematica-Dateien (.ma)** – Mathematica-Dateien verwenden dieselbe Dateiendung wie native Maya-Dateien. Wenn Feature Pack installiert und das Maya .ma-Dateiformat aktiviert ist, versucht AEM3D Mathematica-Dateien zu erfassen, wenn Maya-Dateien fehlschlagen. Solche Assets zeigen ein Fehlerbanner in der Ansicht &quot;Karte&quot;an.

* **Targa-Bilddateien (.tga)** – Ältere 3D-Modelldateien enthalten möglicherweise Verweise auf TGA-Dateien. Dieses Format wird nicht von AEM unterstützt. Adobe empfiehlt, dass Sie diese Dateien in ein anderes Format konvertieren, bevor Sie die 3D-Elemente in AEM hochladen.
* **HDR-Bilder** – HDR-Bilder werden für Bühnen mit Image-based Lighting (IBL) verwendet. Derzeit werden nur 32-Bit-TIFF-Bilder zu diesem Zweck unterstützt.
* **32-Bit-TIFF-Bilder** – 32-Bit-TIFF-Bilder werden für Bühnen mit Image-based Lighting (IBL) verwendet. AEM unterstützt nicht die Erstellung von Darstellungen für diese Assets, was zu leeren Miniaturbildern führt. Eine Vorschau ist nicht möglich. Das Asset funktioniert dennoch ordnungsgemäß, wenn es mit einer IBL-Bühne verwendet wird.
* **Autodesk 3ds Max (.max)-Dateien** - Wenn Autodesk 3ds Max auf den Autorknoten installiert und konfiguriert ist, unterstützt AEM die Erfassung und Konvertierung von .max-Dateien. Die Verwendung von .max-Dateien als Phasen wird derzeit nicht unterstützt.

### Automatische Auflösung der Abhängigkeiten {#automatic-dependency-resolution}

* **Nicht aufgelöste Dateiabhängigkeiten beim Hochladen** – Wenn 3D-Assets und ihre abhängigen Elemente im selben Upload-Vorgang hochgeladen werden, ist es möglich, dass einige abhängige Elemente nicht automatisch behoben werden. Dieses Problem kann auftreten, wenn es sich um große abhängige Dateien handelt. Um dieses Problem zu beheben, greifen Sie auf die **Eigenschaften-/Abhängigkeitsseite** des Assets zu, auf der die nicht aufgelösten abhängigen Elemente nach dem Hochladen angezeigt werden. Die zuvor nicht aufgelösten abhängigen Elemente sollten jetzt angezeigt werden. Klicken Sie auf **Speichern**, um das Asset fertigzustellen. Um dieses Problem in Zukunft zu vermeiden, können Sie vor dem Hochladen der 3D-Objekte alle abhängigen Elemente in einer separaten Transaktion hochladen.

* **Groß-/Kleinschreibung** – Bei der automatischen Auflösung der Abhängigkeiten wird versucht, die Dateinamen unter Berücksichtigung der Groß-/Kleinschreibung zuzuordnen. For example, if the original dependency found in the 3D asset is `image.jpg`, the dependency resolves to an asset named `Image.jpg`, `image.JPG`, or any other case variation.

### 3D-Bühnen {#d-stages}

* **Miniaturansichten für Phasen** - Die automatisch generierten Miniaturansichten für Phasen stellen die Bühne möglicherweise nicht genau dar.
* **Bühnengeometrie für Bühnen mit anderer Beleuchtung als IBL** – Der Rapid Refine Renderer rendert die Geometrie von Bühnen mit einer anderen Beleuchtung als IBL nicht – auch nicht die der Hintergründe und Bodenflächen. Diese Geometrie wird in der Asset-Detail-Ansicht (3D-Vorschau) weiterhin angemessen angezeigt.

* **FBX-Bühnen mit IBL** – Sie können FBX-Bühnen mit IBL hochladen. Allerdings gibt es beim FBX-Format keine Vorkehrungen zum Übertragen des IBL-Bildnamens. Daher schlägt die Auflösung der Dateiabhängigkeiten fehl. Das IBL-Bild muss der Bühne nach dem Hochladen manuell zugewiesen werden. You can assign the same 32-bit TIFF image to the three dependencies which are **Diffuse Lighting Environment Image**, **Reflection Environment Image**, and **Background Environment Image**, or different images may be assigned.

* **Hintergrund von IBL-Stadien** – Bei manchen IBL-Szenen ist das Hintergrundbild ggf. von schlechter Qualität, also zum Beispiel zu hell oder zu verschwommen. Um die visuelle Qualität des Bildhintergrunds von IBL-Bühnen zu maximieren, empfiehlt Adobe, dass Sie ein separates 8-Bit-JPEG-Bild vorbereiten und der IBL-Bühne als **Bild mit dem Hintergrund der Umgebung hinzufügen**.

* **Schwarzes Bild beim Rendern mit Maya mithilfe einer IBL-Bühne** – Dieses Problem wird wahrscheinlich durch Maya verursacht, das die IBL-Bildabhängigkeit nicht findet, da das durch die Bühne referenzierte IBL-Originalbild durch ein Bild mit einem anderen Namen ersetzt wurde. Um dieses Problem zu vermeiden, stellen Sie sicher, dass mindestens eine der drei Abhängigkeiten, auf die im Maya IBL-Stadium verwiesen wird, denselben Namen wie die ursprüngliche IBL-Dateireferenz in der Maya-Datei hat.
* **Reservierter Hintergrund für IBL-Bühne** – Die Bilder zu IBL-Bühnen werden absichtlich horizontal gespiegelt, um dem Verhalten des NVIDIA Mental Ray Renderers zu entsprechen, der mit Autodesk Maya bereitgestellt wird. Problemumgehung: Spiegeln Sie die für IBL-Bühnen in Photoshop verwendeten Bilder, bevor Sie sie hochladen.
* **Helligkeit von IBL-Bühnen** – Die automatische Analyse des IBL-Bildes kann zu einer Szene führen, die zu dunkel oder zu hell ist. To adjust the lighting brightness of IBL stages, navigate to **Basic Properties** and adjust the **bright** value of **Environment Lighting** as needed.

### AEM Sites-3D-Komponente {#aem-sites-d-component}

* **Eine 3D-Komponente pro Seite** - Derzeit ist auf jeder Webseite nur eine Instanz der 3D-Komponente zulässig. Wenn mehr als eine 3D-Komponente zur gleichen Seite hinzugefügt wird, funktioniert keine der 3D-Komponenten korrekt.
* **3D-Ansicht fehlt bei der Vorschau in Sites** - Wenn Sie die **Vorschau** in Sites verwenden, muss die Seite im Browser neu geladen werden, damit der 3D-Viewer vollständig initialisiert werden kann. Dies ist kein Problem, wenn Sie die Webseite direkt (d. h., wenn sie aus dem Pfad entfernt `edit.html` wird) auf den Knoten &quot;Autor&quot;oder &quot;Veröffentlichen&quot;Ansicht haben.

* **Vollbildmodus auf iOS-Geräten** nicht verfügbar - Die Vollbildschaltfläche ist auf iOS-Geräten unabhängig vom verwendeten Browser nicht verfügbar.

### Veröffentlichen von 3D-Inhalten {#publishing-d-content}

* **Konfiguration** der 3D-Komponenten: Sie müssen das 3D-Feature Pack auf allen aktiven Veröffentlichungsknoten installieren und jeder Knoten muss mit **CRXDE Lite** zu den gleichen Konfigurationsoptionen am `/libs/settings/dam/v3D/WebGLSites`.

* **Fehlende Texturen, Hintergrund oder Beleuchtung nach der Veröffentlichung** - Der **Veröffentlichungsmechanismus** in AEM Sites veröffentlicht automatisch die primären Abhängigkeiten der Seite, einschließlich des 3D-Modells und der 3D-Phase, auf die die 3D-Komponente verweist. 3D-Bühnen und 3D-Modelle sind üblicherweise auf sekundäre Assets für IBL-Bilder und Texturzuodnungen angewiesen, die der Veröffentlichungsmechanismus von Sites nicht automatisch veröffentlicht. Problemumgehung: alle 3D-Assets aus Assets veröffentlichen, bevor die Webseite von Sites veröffentlicht wird. Dadurch wird sichergestellt, dass alle Abhängigkeiten für 3D-Assets auf den Veröffentlichungsknoten verfügbar sind.
