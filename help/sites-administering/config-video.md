---
title: Konfigurieren der Videokomponente
seo-title: Configure the Video component
description: Erfahren Sie, wie Sie die Videokomponente konfigurieren.
seo-description: Learn how to configure the Video Component.
uuid: f4755a13-08ea-4096-a951-46a590f8d766
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: a1efef3c-0e4b-4a17-bcad-e3cc17adbbf7
exl-id: 46d0765d-fb77-4332-8fbb-5bd2abcd6806
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 41%

---

# Konfigurieren der Videokomponente {#configure-the-video-component}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Die [Videokomponente](/help/sites-authoring/default-components-foundation.md#video) können Sie ein vordefiniertes OOTB-Videoelement (vordefiniertes) auf Ihrer Seite platzieren.

Damit eine korrekte Transkodierung erfolgt, muss Ihr Administrator [Installieren Sie FFmpeg und konfigurieren Sie AEM](#install-ffmpeg) getrennt. Sie können auch [Videoprofile konfigurieren](#configure-video-profiles) zur Verwendung mit HTML5-Elementen.

>[!CAUTION]
>
>Es wird nicht mehr erwartet, dass diese Komponente ohne umfassende Anpassungen auf Projektebene vorkonfiguriert funktioniert.

## Videoprofile konfigurieren {#configure-video-profiles}

Sie können Videoprofile definieren, die für HTML5-Elemente verwendet werden sollen. Die hier gewählten werden der Reihe nach verwendet. Um zuzugreifen, verwenden Sie [Design-Modus](/help/sites-authoring/default-components-designmode.md) (nur in der klassischen Benutzeroberfläche) und wählen Sie die Registerkarte **[!UICONTROL Profile]** aus:

![chlimage_1-317](assets/chlimage_1-317.png)

Sie können auch das Design der Videokomponenten und -parameter für [!UICONTROL Wiedergabe], [!UICONTROL Flash]und [!UICONTROL Erweitert].

## Installieren von FFmpeg und Konfigurieren von AEM {#install-ffmpeg}

Die Videokomponente nutzt das Open-Source-Produkt FFmpeg eines Drittanbieters für die ordnungsgemäße Transkodierung von Videos, die heruntergeladen werden können von [https://ffmpeg.org/](https://ffmpeg.org/). Nach der Installation von FFmpeg müssen Sie AEM konfigurieren, um einen bestimmten Audio-Codec und bestimmte Laufzeitoptionen zu verwenden.

**So installieren Sie FFmpeg für Ihre Plattform**:

* **Unter Windows:**

   1. Laden Sie die kompilierte Binärdatei als `ffmpeg.zip`
   1. Entpacken Sie die Datei in einen Ordner.
   1. Systemumgebungsvariable festlegen `PATH` nach `<*your-ffmpeg-locatio*n>\bin`
   1. Starten Sie AEM neu.

* **Unter Mac OS X:**

   1. Installieren Sie Xcode ([https://developer.apple.com/technologies/tools/xcode.html](https://developer.apple.com/technologies/tools/xcode.html))
   1. Installieren Sie XQuartz/X11.
   1. Installieren Sie MacPorts ([https://www.macports.org/](https://www.macports.org/))
   1. Führen Sie in der Konsole den folgenden Befehl aus und befolgen Sie die Anweisungen:

      `sudo port install ffmpeg`

      `FFmpeg` muss in `PATH` , damit AEM ihn über die Befehlszeile abrufen können.

* **Verwenden der vorkompilierten Version für OS X 10.6:**

   1. Laden Sie die vorkompilierte Version herunter.
   1. Extrahieren Sie sie in die `/usr/local` Verzeichnis.
   1. Führen Sie vom Terminal aus Folgendes aus:

      `sudo ln -s /usr/local/Cellar/ffmpeg/0.6/bin/ffmpeg /usr/bin/ffmpeg`

**So konfigurieren Sie AEM**:

1. Öffnen Sie [!UICONTROL CRXDE Lite] in einem Webbrowser. ([http://localhost:4502/crx/de](http://localhost:4502/crx/de))
1. Wählen Sie den Knoten `/libs/settings/dam/video/format_aac/jcr:content` aus und stellen Sie sicher, dass die Knoteneigenschaften wie folgt lauten:

   * audioCodec:

      ```
       aac
      ```

   * customArgs:

      ```
       -flags +loop -me_method umh -g 250 -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -bf 16 -b_strategy 1 -i_qfactor 0.71 -cmp chroma -subq 8 -me_range 16 -coder 1 -sc_threshold 40 -b-pyramid normal -wpredp 2 -mixed-refs 1 -8x8dct 1 -fast-pskip 1 -keyint_min 25 -refs 4 -trellis 1 -direct-pred 3 -partitions i8x8,i4x4,p8x8,b8x8
      ```

1. Um die Konfiguration anzupassen, erstellen Sie eine Überlagerung im Knoten `/apps/settings/` und verschieben Sie dieselbe Struktur unter den Knoten `/conf/global/settings/`. Sie kann nicht im Knoten `/libs` bearbeitet werden. Um zum Beispiel den Pfad `/libs/settings/dam/video/fullhd-bp` zu überlagern, erstellen Sie ihn bei `/conf/global/settings/dam/video/fullhd-bp`.

   >[!NOTE]
   >
   >Überlagern und bearbeiten Sie den gesamten Profilknoten und nicht nur die Eigenschaft, die geändert werden muss. Solche Ressourcen werden nicht über SlingResourceMerger aufgelöst.

1. Haben Sie eine der Eigenschaften geändert, klicken Sie auf **[!UICONTROL Alle speichern]**.

>[!NOTE]
>
>OOTB-Workflow-Modelle werden beim Upgrade Ihrer AEM-Instanz nicht beibehalten. Adobe empfiehlt, OOTB-Workflow-Modelle zu kopieren, bevor Sie sie bearbeiten. Kopieren Sie beispielsweise das vorkonfigirierte Modell DAM Update Asset, bevor Sie den FFmpeg-Transkodierungsschritt im Modell DAM Update Asset ändern, um bereits vor dem Upgrade vorhandene Videoprofilnamen auszuwählen. Sie können dann den Knoten `/apps` überlagern, damit AEM die benutzerdefinierten Änderungen am vorkonfigurierten Modell abrufen kann.
