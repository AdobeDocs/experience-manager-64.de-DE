---
title: Digitale Assets mit AEM Assets verwalten
description: Erfahren Sie mehr über verschiedene Asset-Management- und -Bearbeitungsaufgaben, die Sie mithilfe der Touch-optimierten Benutzeroberfläche von AEM Assets durchführen können
contentOwner: AG
mini-toc-levels: 1
feature: Asset Management,Search,Renditions,Collaboration
role: Business Practitioner
exl-id: aa1a702b-18dd-496b-a6e0-aa593af6e57c
translation-type: tm+mt
source-git-commit: fd79ac0694d5b7af0422c546cc4a94fdf2326d37
workflow-type: tm+mt
source-wordcount: '10083'
ht-degree: 65%

---

# Digitale Assets {#managing-assets-with-the-touch-optimized-ui} verwalten

Erfahren Sie mehr über verschiedene Asset-Management- und -Bearbeitungsaufgaben, die Sie mithilfe der Touch-optimierten Benutzeroberfläche von AEM Assets durchführen können.

In diesem Artikel wird beschrieben, wie Sie Assets mithilfe der Adobe Experience Manager (AEM) Touch-optimierten Benutzeroberfläche verwalten und bearbeiten. Weitere Informationen zur Benutzeroberfläche finden Sie unter [Grundlegende Handhabung der Touch-Benutzeroberfläche](/help/sites-authoring/basic-handling.md). Informationen zum Verwalten von Inhaltsfragmenten finden Sie unter [Verwalten von Inhaltsfragmenten](content-fragments-managing.md)-Assets.

## Erstellen von Ordnern {#create-folders}

Wenn Sie eine Sammlung von Assets organisieren, etwa alle `Nature`-Aufnahmen, können Sie Ordner erstellen, um diese zu gruppieren. Mit Ordnern können Sie Assets kategorisieren und organisieren. Bei AEM Assets müssen Sie Assets nicht in Ordner organisieren, um besser zu arbeiten.

>[!NOTE]
>
>* Das Freigeben eines Assets-Ordners des Typs `sling:OrderedFolder` wird beim Freigeben auf Marketing Cloud nicht unterstützt. Wenn Sie einen Ordner freigeben möchten, wählen Sie beim Erstellen eines Ordners nicht „Geordnet“ aus.
>* In Experience Manager ist die Verwendung von `subassets` als Ordnername nicht zulässig. Dies ist ein Keyword, das für Knoten reserviert ist, die Teil-Assets für ebenenübergreifende Assets enthalten..


1. Navigieren Sie zu dem Ort in Ihrem Ordner „Digitale Assets“, an dem Sie einen neuen Ordner erstellen möchten.
1. Klicken Sie im Menü auf **[!UICONTROL Erstellen]**. Wählen Sie **[!UICONTROL Neuer Ordner]** aus.
1. Geben Sie in das Feld **[!UICONTROL Titel]** einen Ordnernamen an. DAM verwendet standardmäßig den Titel, den Sie als Ordnernamen angegeben haben. Wenn der Ordner erstellt wurde, können Sie die Standardeinstellung außer Kraft setzen und einen anderen Ordnernamen angeben.
1. Klicken Sie auf **[!UICONTROL Erstellen]**. Ihr Ordner wird im Ordner „Digitale Assets“ angezeigt.

Die folgenden Zeichen (in der Liste durch Leerzeichen getrennt) werden nicht unterstützt:

* Der Asset-Dateiname darf nicht enthalten: `* / : [ \ \ ] | # % { } ? &`
* Der Asset-Ordnername darf nicht enthalten: `* / : [ \ \ ] | # % { } ? \" . ^ ; + & \t`

## Hochladen von Assets {#uploading-assets}

Sie können verschiedene Arten von Assets (z. B. Bilder, PDF-Dateien, Raw-Dateien usw.) von Ihrem lokalen Ordner oder Netzlaufwerk in AEM Assets hochladen.

>[!NOTE]
>
>Im Dynamic Media Scene 7-Modus können Sie nur Assets mit einer Dateigröße von maximal 2 GB hochladen.

Sie können Assets in Ordnern mit oder ohne zugewiesenem Verarbeitungsprofil hochladen.

Für Ordner mit zugewiesenem Verarbeitungsprofil wird der Profilname in der Miniaturansicht der Kartenansicht angezeigt. In der Listenansicht wird der Profilname in der Spalte **[!UICONTROL Verarbeitungsprofil]** angezeigt. Siehe [Verarbeitungsprofile](processing-profiles.md).

Stellen Sie vor dem Hochladen eines Assets sicher, dass es im Format [unterstützt](assets-formats.md) vorliegt.

**So laden Sie Assets** hoch:

1. Navigieren Sie in der Weboberfläche &quot;Assets&quot;zu dem Speicherort, an dem Sie digitale Assets hinzufügen möchten.
1. Führen Sie einen der folgenden Schritte aus, um die Assets hochzuladen:

   * Tippen Sie in der Symbolleiste auf das Symbol **[!UICONTROL Erstellen]**. Tippen Sie dann im Menü auf **[!UICONTROL Dateien]**. Sie können die Datei im angezeigten Dialogfeld bei Bedarf umbenennen.
   * Ziehen Sie die Assets in einem Browser, der HTML5 unterstützt, direkt auf die Oberfläche. Das Dialogfeld zum Umbenennen der Datei wird nicht angezeigt.

   ![create_menu](assets/create_menu.png)

   Wenn Sie die Assets im Dialogfeld für die Dateiauswahl bei gedrückter Strg-/Befehlstaste markieren, können Sie mehrere Dateien auswählen. Auf einem iPad können Sie jeweils nur eine Datei auswählen.

   Sie können das Hochladen von großen Assets (größer als 500 MB) anhalten und später von der gleichen Seite aus fortsetzen. Tippen Sie auf das Symbol **[!UICONTROL Pause]** neben dem bei Uploadbeginn eingeblendeten Fortschrittsbalken.

   ![chlimage_1-5](assets/chlimage_1-5.png)

   Die Größe, ab der ein Asset als großes Asset gilt, lässt sich konfigurieren. Sie können das System beispielsweise so konfigurieren, dass Assets über 1000 MB (anstatt 500 MB) als große Assets angesehen werden. In diesem Fall wird die Schaltfläche **[!UICONTROL Pause]** im Fortschrittsbalken angezeigt, wenn Assets hochgeladen werden, die größer als 1000 MB sind.

   Die Schaltfläche **[!UICONTROL Pause]** zeigt nicht an, wenn eine Datei größer als 1000 MB mit einer Datei kleiner als 1000 MB hochgeladen wird. Wenn Sie jedoch den Upload der Datei abbrechen, die kleiner ist als 1000 MB, wird die Schaltfläche **[!UICONTROL Pause]** angezeigt.

   Um die Größenbeschränkung zu ändern, konfigurieren Sie die `chunkUploadMinFileSize`-Eigenschaft des `fileupload`Knotens im CRX-Repository.

   Wenn Sie auf das Symbol **[!UICONTROL Pause]** klicken, wird es zum Symbol **[!UICONTROL Wiedergabe]**. Um das Hochladen fortzusetzen, klicken Sie auf das Symbol **[!UICONTROL Wiedergabe.]**

   ![chlimage_1-6](assets/chlimage_1-6.png)

   Um einen laufenden Upload-Vorgang abzubrechen, klicken Sie auf die Schaltfläche `X` neben der Fortschrittsleiste. Wenn Sie den Upload abbrechen, löscht AEM Assets den teilweise hochgeladenen Teil des Assets.

   Den Upload fortsetzen zu können, ist besonders hilfreich bei geringer Bandbreite und Netzwerkfehlern, bei denen der Upload großer Assets lange dauern kann. Sie können den Uploadvorgang anhalten und später fortsetzen, wenn die Bedingungen besser sind. Beim Fortsetzen beginnt der Upload an dem Punkt, an dem Sie pausiert haben.

   Während des Uploads speichert AEM die Teile des hochgeladenen Assets als Datenblöcke im CRX-Repository. Wenn der Upload abgeschlossen ist, konsolidiert AEM diese Blöcke in einem einzelnen Datenblock im Repository.

   Um die Bereinigungs-Aufgabe für nicht fertig gestellte Stapelupload-Aufträge zu konfigurieren, gehen Sie zu `https://[aem_server]:[port]/system/console/configMgr/org.apache.sling.servlets.post.impl.helper.ChunkCleanUpTask`.

   Wenn Sie ein Asset unter einem Namen hochladen, der bereits für ein Asset verwendet wird, das sich am Zielort befindet, wird eine Warnmeldung angezeigt.

   Sie können festlegen, ob ein vorhandenes Asset ersetzt, eine neue Version erstellt oder beide Assets beibehalten werden sollen, indem Sie das neue hochgeladene Asset umbenennen. Wenn Sie ein vorhandenes Asset ersetzen, werden die Metadaten für das Asset sowie alle früheren Änderungen und Verlaufsdaten (z. B. Anmerkungen, Ernten usw.) gelöscht. Wenn Sie beide Assets beibehalten möchten, wird das neue Asset umbenannt.

   ![chlimage_1-7](assets/chlimage_1-7.png)

   >[!NOTE]
   >
   >Wenn Sie **[!UICONTROL Ersetzen]** im Dialogfeld **[!UICONTROL Namenskonflikt]** auswählen, wird die Asset-ID für das neue Asset neu generiert. Diese ID unterscheidet sich von der ID des vorherigen Assets.
   >
   >Wenn **[!UICONTROL Asset Insights]** aktiviert ist, um Impressionen/Klicks mit Adobe Analytics zu verfolgen, macht diese neu generierte Asset-ID die für das Asset auf Adobe Analytics erfassten Daten ungültig.

   Wenn das hochgeladene Asset in AEM Assets vorhanden ist, wird im Dialogfeld **[!UICONTROL Erkannte Duplikat]** gewarnt, dass Sie versuchen, ein Duplikat-Asset hochzuladen. Das Dialogfeld wird nur angezeigt, wenn der SHA-1-Prüfsummenwert der Binärdatei des bestehenden Assets dem des Assets entspricht, das Sie gerade hochladen. In diesem Fall sind die Namen der Assets unerheblich. Das bedeutet, dass das Dialogfeld auch für Assets mit unterschiedlichen Namen angezeigt werden kann, wenn die SHA 1-Werte für ihre Binärdateien identisch sind.

   >[!NOTE]
   >
   >Das Dialogfeld **[!UICONTROL Duplikat erkannt]** wird nur angezeigt, wenn die Funktion **[!UICONTROL Duplikat-Erkennung]** aktiviert ist. Informationen zum Aktivieren der Funktion **[!UICONTROL Duplikat-Erkennung]** finden Sie unter [Aktivieren der Duplikat-Erkennung](duplicate-detection.md).

   ![chlimage_1-8](assets/chlimage_1-8.png)

   Tippen Sie auf **[!UICONTROL Behalten Sie]**, um das Duplikat-Asset in AEM Assets beizubehalten. Tippen Sie auf **[!UICONTROL Löschen]**, um das hochgeladene Duplikat-Asset zu löschen.

   AEM Assets verhindert, dass Sie Assets hochladen, deren Dateinamen unzulässige Zeichen enthalten. Wenn Sie versuchen, ein Asset hochzuladen, das die unzulässigen Zeichen enthält, zeigt AEM Assets eine Warnmeldung an, dass der Dateiname verbotene Zeichen enthält, und stoppt den Upload, bis Sie diese Zeichen entfernen oder mit einem zulässigen Namen hochladen.

   Um den spezifischen Dateibenennungsregeln für Ihr Unternehmen zu entsprechen, können Sie im Dialogfeld **[!UICONTROL Assets hochladen]** lange Namen für die hochgeladenen Dateien angeben.

   ![chlimage_1-9](assets/chlimage_1-9.png)

   Allerdings werden die folgenden Zeichen (in der Liste durch Leerzeichen getrennt) nicht unterstützt:
   * Der Asset-Dateiname darf nicht enthalten: `* / : [ \ \ ] | # % { } ? &`
   * Der Asset-Ordnername darf nicht enthalten: `* / : [ \ \ ] | # % { } ? \" . ^ ; + & \t`

   Darüber hinaus zeigt die Assets-Oberfläche das neueste Asset an, das Sie hochladen, oder den Ordner, den Sie zuerst in allen Ansichten erstellen (**[!UICONTROL Card-Ansicht]**, **[!UICONTROL Liste-Ansicht]** und **[!UICONTROL Spalten-Ansicht]**).

   Beim gleichzeitigen Hochladen großer Assets oder mehrerer Assets können Sie anhand visueller Indikatoren den Fortschritt häufig bewerten. Das Dialogfeld **[!UICONTROL Upload-Fortschritt]** zeigt die Anzahl der erfolgreich hochgeladenen Dateien und die Dateien an, die nicht hochgeladen wurden.

   ![chlimage_1-10](assets/chlimage_1-10.png)

   Wenn Sie den Upload abbrechen, bevor die Dateien hochgeladen sind, unterbricht AEM Assets den Upload der aktuellen Datei und aktualisiert den Inhalt. Dateien, die bereits hochgeladen wurden, werden jedoch nicht gelöscht.

### Serielle Uploads {#serial-uploads}

Das Hochladen zahlreicher Assets in großen Mengen erfordert erhebliche Systemressourcen, was sich negativ auf die Leistung Ihrer AEM auswirken kann. Mögliche Engpässe sind Ihre Internetverbindung, Lese- und Schreibvorgänge auf der Festplatte, Einschränkungen des Webbrowsers bei der Anzahl der POST-Anfragen beim gleichzeitigen Hochladen von Assets. Der Vorgang zum Hochladen von Massen kann fehlschlagen oder vorzeitig beendet werden. Dabei kann es vorkommen, dass in AEM Assets bei der Erfassung großer Dateienmengen einige Dateien verloren gehen oder der Erfassungsvorgang insgesamt nicht ausgeführt werden kann.

Um diese Situation zu vermeiden, gibt es die Möglichkeit, Ladevorgänge im Stapelmodus seriell durchzuführen. Dabei werden in AEM Assets die Assets nicht gleichzeitig, sondern einzeln nacheinander erfasst.

Der serielle Upload von Assets ist standardmäßig aktiviert. Um die Funktion zu deaktivieren und das gleichzeitige Hochladen zuzulassen, überlagern Sie den Knoten `fileupload` in CRXDe und legen Sie den Wert der Eigenschaft `parallelUploads` auf `true` fest.

### Hochladen von Assets mit FTP {#uploading-assets-using-ftp}

Dynamic Media ermöglicht das Batch-Hochladen von Assets über den FTP-Server. Wenn Sie große Assets (über 1 GB) oder ganze Ordner und Unterordner hochladen möchten, sollten Sie FTP verwenden. Sie können das Hochladen per FTP auch einrichten, um Uploads regelmäßig und nach Plan durchzuführen.

>[!NOTE]
>
>Im Dynamic Media Scene 7-Modus können Sie nur Assets mit einer Dateigröße von maximal 2 GB hochladen.

>[!NOTE]
>
>Um Assets per FTP in Dynamic Media - Scene7-Modus zu laden, installieren Sie Feature Pack (FP) 18912 auf AEM Autor. Wenden Sie sich an den Kundendienst der Adobe, um Zugriff auf das FP-18912 zu erhalten und die Einrichtung Ihres FTP-Kontos abzuschließen. Weitere Informationen finden Sie unter [Installieren von Feature Pack 18912 für Massenmigration von Assets](/help/assets/bulk-ingest-migrate.md).
>
>Die in AEM angegebenen Upload-Einstellungen werden ignoriert, wenn Sie FTP zum Hochladen von Assets verwenden. Stattdessen werden Dateiverarbeitungsregeln, wie in Dynamic Media Classic definiert, verwendet.    

**So laden Sie Assets per FTP hoch**

1. Verwenden Sie den FTP-Client Ihrer Wahl und melden Sie sich beim FTP-Server mit dem FTP-Benutzernamen und -Kennwort aus der Bereitstellungs-E-Mail an. Laden Sie die Dateien und/oder Ordner über den FTP-Client auf den FTP-Server hoch.
1. Öffnen Sie die Desktopanwendung [Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html?lang=de#getting-started) und melden Sie sich dann mit den Anmeldeinformationen an, die Sie aus der Bereitstellungs-E-Mail erhalten haben.
1. Tippen oder klicken Sie in der Leiste „Globale Navigation“ auf **[!UICONTROL Hochladen]**.
1. Tippen Sie auf der Seite **[!UICONTROL Upload]** in der oberen linken Ecke auf die Registerkarte **[!UICONTROL Über FTP]**.
1. Wählen Sie im linken Bereich der Seite einen FTP-Ordner aus, aus dem Sie Dateien hochladen. Auf der rechten Seite der Seite wählen Sie einen Zielordner aus.
1. Tippen Sie in der rechten unteren Ecke der Seite auf **[!UICONTROL Auftragsoptionen]** und legen Sie dann die gewünschten Optionen basierend auf den Assets im ausgewählten Ordner fest.

   Siehe [Upload-Auftragsoptionen](#upload-job-options).

   >[!NOTE]
   >
   >Wenn Sie Assets über FTP hochladen, haben die in Dynamic Media Classic festgelegten Upload-Auftragsoptionen Vorrang vor den in AEM festgelegten Asset-Verarbeitungsparametern.

1. Tippen Sie in der rechten unteren Ecke des Dialogfelds **[!UICONTROL Upload-Auftragsoptionen]** auf **[!UICONTROL Speichern]**.
1. Tippen Sie in der rechten unteren Ecke der Seite **[!UICONTROL Hochladen]** auf **[!UICONTROL Hochladen senden]**.

   Um den Upload-Fortschritt anzuzeigen, tippen Sie in der Leiste „Globale Navigation“ auf **[!UICONTROL Aufträge]**. Die Seite **[!UICONTROL Aufträge]** zeigt den Fortschritt des Hochladevorgangs an. Sie können mit der Arbeit in AEM fortfahren und jederzeit wieder in Dynamic Media Classic zur Seite „Aufträge“ zurückkehren, um einen gerade verarbeiteten Auftrag zu überprüfen.

   Um die laufende Verarbeitung eines Upload-Auftrags abzubrechen, tippen oder klicken Sie neben der Information „Dauer“ auf die Schaltfläche **[!UICONTROL Abbrechen]****[!UICONTROL .]**

#### Upload-Auftragsoptionen {#upload-job-options}

| Upload-Optionen | Unteroption | Beschreibung |
|---|---|---|
| Auftragsname |  | Der Name, der standardmäßig in diesem Feld erstellt wird, enthält den vom Benutzer eingegebenen Teil des Namens und einen Zeitstempel samt Datum. Für diesen Upload-Auftrag können Sie den Standardnamen oder einen von Ihnen selbst erstellten Namen verwenden. <br>Der Auftrag und andere Upload- und Veröffentlichungsaufträge werden auf der Seite „Aufträge“ aufgezeichnet, wo Sie den Status der Aufträge prüfen können. |
| Nach dem Hochladen veröffentlichen |  | Veröffentlicht Assets automatisch nach dem Hochladen. |
| In belieb. Ordner Assets mit ident. Namen unabh. von Erweit. überschreiben |  | Wählen Sie diese Option aus, wenn hochgeladene Dateien vorhandene Dateien mit denselben Namen ersetzen sollen. Der Name dieser Option kann möglicherweise anders lauten, je nach den Einstellungen in **[!UICONTROL Anwendungseinstellungen]** > **[!UICONTROL Allgemeine Einstellungen]** > **[!UICONTROL Zur Anwendung hochladen]** > **[!UICONTROL Bilder überschreiben]**. |
| Dekomprimieren von ZIP- oder TAR-Dateien beim Hochladen |  |  |
| Auftragsoptionen |  | Tippen/klicken Sie auf **[!UICONTROL Auftragsoptionen]**, um das Dialogfeld [!UICONTROL Upload-Auftragsoptionen] zu öffnen und Optionen auszuwählen, die sich auf den gesamten Upload-Auftrag auswirken. Diese Optionen sind für alle Dateitypen gleich.<br>Sie können über die Seite „Allgemeine Programmeinstellungen“ Standardoptionen für das Hochladen von Dateien auswählen. Um diese Seite zu öffnen, wählen Sie **[!UICONTROL Einstellung]** > **[!UICONTROL Anwendungseinstellungen]**. Tippen Sie auf die Schaltfläche **[!UICONTROL Standardmäßige Upload-Optionen]**, um das Dialogfeld [!UICONTROL Upload-Auftragsoptionen] zu öffnen. |
|  | Wenn | Wählen Sie „Einmalig“ oder „Wiederkehrend“ aus. Zum Einrichten eines wiederkehrenden Auftrags wählen Sie eine Wiederholungsoption („Täglich“, „Wöchentlich“, „Monatlich“ oder „Benutzerdefiniert“), um anzugeben, wie oft der FTP-Upload-Auftrag wiederholt werden soll. Dann geben Sie nach Bedarf die Planungsoptionen an. |
|  | Unterordner einschließen | Laden Sie alle Unterordner im hochzuladenden Ordner hoch. Der Name des hochgeladenen Ordners und die Namen der darin enthaltenen Unterordner werden automatisch in AEM Assets erfasst. |
|  | Optionen für das Zuschneiden | Um die Seiten eines Bildes manuell zu beschneiden, wählen Sie im Menü „Beschneiden“ die Option „Manuell“ aus. Dann geben Sie die Anzahl von Pixeln ein, die an einer oder jeder Seite des Bildes abgeschnitten werden sollen. Um wie viel das Bild beschnitten wird, hängt von der ppi-Einstellung (Pixel per Inch; Pixel pro Zoll) in der Bilddatei ab. Beispiel: Wenn das Bild 150 ppi aufweist und Sie 75 in die Textfelder für oben, rechts, unten und links eingeben, wird ein halber Zoll von jeder Seite abgeschnitten.<br> Zum automatischen Beschneiden der Leerraumpixel eines Bildes öffnen Sie das Menü „Beschneiden“, wählen Sie „Manuell“ und geben Sie zum Beschneiden der Seiten die Pixelwerte in die Felder „Oben“, „Rechts“, „Unten“ und „Links“ ein. Sie können im Menü „Beschneiden“ auch „Zuschneiden“ und anschließend folgende Optionen auswählen:<br> **Beschneiden basierend auf** <ul><li>**Farbe** : Wählen Sie die Option &quot;Farbe&quot;. Wählen Sie anschließend im Menü „Ecke“ die Bildecke mit der Farbe aus, die am besten der Leerraumfarbe entspricht, die Sie entfernen möchten.</li><li>**** Transparenz – Wählen Sie die Option „Transparenz“.<br> **Toleranz** : Ziehen Sie den Schieberegler, um eine Toleranz von 0 bis 1 festzulegen. Beim Beschneiden basierend auf Farbe geben Sie 0 an, damit Pixel nur abgeschnitten werden, wenn sie exakt der Farbe entsprechen, die Sie in der Bildecke ausgewählt haben. Werte, die näher an 1 liegen, lassen eine größere Farbdifferenz zu.<br>Für das Zuschneiden auf der Grundlage der Transparenz geben Sie den Wert 0 an, damit Pixel nur dann abgeschnitten werden, wenn sie transparent sind. Werte, die näher an 1 liegen, lassen eine größere Transparenz zu.</li></ul><br>Beachten Sie, dass diese Optionen für das Beschneiden zerstörungsfrei sind. |
|  | Farbprofiloptionen | Wählen Sie beim Erstellen optimierter Dateien eine Farbkonversion aus, die für die Bereitstellung verwendet wird:<ul><li>Beibehaltung der Standardfarbe: Behält die Farben des Quellbildes bei, wenn die Bilder Farbrauminformationen enthalten. Es findet keine Farbkonversion statt. Heutzutage ist in fast allen Bildern das entsprechende Farbprofil eingebettet. Wenn jedoch ein CMYK-Quellbild kein eingebettetes Farbprofil enthält, werden die Farben in den Farbraum sRGB (standardmäßiges Rot Grün Blau) konvertiert. sRGB ist der empfohlene Farbraum zum Anzeigen von Bildern auf Webseiten.</li><li>Ursprünglichen Farbraum beibehalten: Behält die ursprünglichen Farben bei, ohne dass an der betreffenden Stelle eine Farbkonversion stattfindet. Bei Bildern ohne eingebettetes Farbprofil wird jede Farbkonversion mit den in den Veröffentlichungseinstellungen konfigurierten Standardfarbprofilen durchgeführt. Die Farbprofile stimmen möglicherweise nicht mit der Farbe in den Dateien überein, die mit dieser Option erstellt wurden. Deshalb empfiehlt es sich, die Option „Beibehaltung der Standardfarbe“ zu verwenden.</li><li>Benutzerdefinierte Einstellung von > in:<br> Öffnet Menüs, damit Sie einen „Konvertieren von“- und einen „Konvertieren in“-Farbraum auswählen können. Diese erweiterte Option überschreibt alle Farbinformationen, die in die Quelldatei eingebettet sind. Wählen Sie diese Option aus, wenn alle Bilder, die Sie senden, falsche oder fehlende Farbprofildaten enthalten.</li></ul> |
|  | Bildbearbeitungsoptionen | Sie können die Beschneidungsmasken in Bildern beibehalten und ein Farbprofil auswählen.<br> Siehe [Festlegen von Bildbearbeitungsoptionen beim Hochladen](#setting-image-editing-options-at-upload). |
|  | PostScript-Optionen | Sie können PostScript®-Dateien rastern, Dateien beschneiden, transparente Hintergründe beibehalten sowie eine Auflösung und einen Farbraum auswählen.<br> Siehe [Festlegen von PostScript- und Illustrator-Uploadoptionen](#setting-postscript-and-illustrator-upload-options). |
|  | Photoshop-Optionen | Sie können Vorlagen aus Adobe® Photoshop®-Dateien erstellen, Ebenen beibehalten, Ebenennamen angeben, Text extrahieren und angeben, wie Bilder in Vorlagen verankert sind.<br> Beachten Sie, dass in AEM Vorlagen nicht unterstützt werden.<br> Siehe [Festlegen von Photoshop-Uploadoptionen](#setting-photoshop-upload-options). |
|  | PDF-Optionen | Sie können die Dateien rastern, Suchbegriffe und -links extrahieren, automatisch einen E-Katalog erstellen, die Auflösung einstellen und einen Farbraum auswählen.<br> Beachten Sie, dass in AEM E-Kataloge nicht unterstützt werden. <br> Siehe [Festlegen von PDF-Uploadoptionen](#setting-pdf-upload-options). |
|  | Illustrator-Optionen | Sie können Adobe Illustrator®-Dateien rastern, transparente Hintergründe beibehalten sowie eine Auflösung und einen Farbraum auswählen.<br> Siehe [Festlegen von PostScript- und Illustrator-Uploadoptionen](#setting-postscript-and-illustrator-upload-options). |
|  | eVideo-Optionen | Sie können eine Videodatei durch Auswahl einer Videovorgabe transkodieren.<br> Siehe [Festlegen von eVideo-Uploadoptionen](#setting-evideo-upload-options). |
|  | Stapelsatzvorgaben | Um ein Bild- oder Rotationsset aus den hochgeladenen Dateien zu erstellen, klicken Sie auf die Spalte „Aktiv“ der Vorgabe, die Sie verwenden möchten. Sie können mehrere Vorgaben auswählen. Die Vorgaben erstellen Sie auf der Seite „Anwendungseinstellungen/Stapelsatzvorgaben“ von Dynamic Media Classic.<br> Weitere Informationen zur Erstellung von Stapelsatzvorgaben finden Sie unter [Konfigurieren von Stapelsatzvorgaben zum automatischen Erstellen von Bild- und Rotationssets](config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets).<br> Siehe [Festlegen von Stapelsatzvorgaben beim Hochladen](#setting-batch-set-presets-at-upload). |

#### Festlegen von Bildbearbeitungsoptionen beim Hochladen {#setting-image-editing-options-at-upload}

Beim Hochladen von Bilddateien, einschließlich AI-, EPS- und PSD-Dateien, können Sie die folgenden Bearbeitungsaktionen im Dialogfeld **[!UICONTROL Upload-Auftragsoptionen]** ausführen:

* Beschneiden von Leerzeichen am Rand von Bildern (siehe Beschreibung in Tabelle oben).
* Ränder von Bildern manuell beschneiden (siehe Beschreibung in der oben stehenden Tabelle)
* Ein Farbprofil auswählen (siehe Optionsbeschreibung in der oben stehenden Tabelle)
* Eine Maske aus einem Beschneidungspfad erstellen
* Bilder scharfzeichnen mit Optionen für „Unscharf maskieren“
* Hintergrund aussparen

| Option | Unteroption | Beschreibung |
|---|---|---|
| Maske aus Beschneidungspfad erstellen |  | Erstellt basierend auf den Beschneidungspfad-Informationen eine Maske für das Bild. Diese Option ist auf Bilder anwendbar, die mit Bildbearbeitungsanwendungen erstellt wurden, in denen ein Beschneidungspfad erstellt wurde. |
| Unschärfemaske |  | Ermöglicht Ihnen die Feineinstellung eines Schärfefiltereffekts im finalen Downsampling-Bild. So können Sie die Intensität und den Radius des Effekts (in Pixel) sowie einen Schwellenwert für ignorierten Kontrast angeben.<br> Bei diesem Effekt werden dieselben Optionen wie im Filter „Unschärfemaske“ von Photoshop verwendet. Im Gegensatz zu dem, was der Name besagt, ist die Unschärfemaske ein Scharfzeichnungsfilter. Wählen Sie unter „Unschärfemaske“ die gewünschten Optionen aus. Im Folgenden finden Sie Beschreibungen der Einstellungsoptionen: |
|  | Stärke | Steuert den auf die Kantenpixel angewendeten Kontrastwert.<br> Betrachten Sie diese Unteroption als Intensität des Effekts. Der Hauptunterschied zwischen den Werten von „Unschärfemaske“ in Dynamic Media und den Werten in Adobe Photoshop ist, dass Adobe Photoshop einen Wertebereich verwendet, der von 1 % bis 500 % reicht. In Dynamic Media hingegen reichen die Werte von 0,0 bis 5,0. Der Wert 5,0 entspricht ungefähr 500 % in Photoshop, der Wert 0,9 ungefähr 90 % usw. |
|  | Radius | Steuert den Radius des Effekts. Der Wertebereich reicht von 0 bis 250.<br> Der Effekt wird auf alle Pixel in einem Bild angewendet und verbreitet sich in alle Richtungen. Der Radius wird in Pixel gemessen. Um beispielsweise einen ähnlichen Scharfzeichnungseffekt für ein Bild mit 2000 x 2000 Pixel und ein Bild mit 500 x 500 Pixel zu erhalten, können Sie einen Radius von zwei Pixel für das Bild mit 2000 x 2000 Pixel und einen Radius von einem Pixel für das Bild mit 500 x 500 Pixel festlegen. Ein größerer Wert wird für ein Bild mit mehr Pixel verwendet. |
|  | Schwelle | Beschreibt den Kontrastbereich, der beim Anwenden der Unschärfemaske ignoriert wird. Das ist wichtig, damit kein Bildrauschen entsteht, wenn dieser Filter verwendet wird. Der Wertebereich reicht von 0 bis 255. Diese Werte stehen für die Anzahl der Helligkeitsschritte in einem Graustufenbild. 0 = Schwarz, 128 = 50 % Grau und 255 = Weiß.<br> Ein Schwellenwert von 12 ignoriert beispielsweise leichte Variationen der Hauttonhelligkeit, um Rauschen zu vermeiden, fügt aber trotzdem Kantenkontrast zu kontrastreichen Bereichen hinzu, wie z. B. wo Wimpern auf die Haut treffen.<br> Wenn Sie z. B. ein Foto des Gesichts einer Person haben, wirkt sich die &quot;Unscharf maskieren&quot;auf die kontrastreichen Teile des Bildes aus, z. B. wo Wimpern und Haut aufeinander treffen, um einen offensichtlichen Kontrastbereich zu schaffen, und auf die glatte Haut selbst. Selbst die glatteste Haut weist geringfügige Änderungen der Helligkeitswerte auf. Wenn Sie keinen Schwellenwert verwenden, akzentuiert der Filter diese geringfügigen Änderungen in den Hautpixel. Dadurch entsteht ein verrauschter und unerwünschter Effekt, während der Kontrast an den Wimpern verstärkt und die Schärfe intensiviert wird.<br> Zur Vermeidung dieses Problems wird ein Schwellenwert verwendet, der den Filter anweist, die Pixel zu ignorieren, die den Kontrast nicht wesentlich ändern, beispielsweise bei glatter Haut.<br> Beachten Sie in der weiter oben gezeigten Reißverschlussgrafik die Textur neben dem Reißverschluss. Hier ist Bildrauschen erkennbar, weil die Schwellenwerte zu niedrig waren, als dass sie das Bildrauschen unterdrücken könnten. |
|  | Monochrom | Wählen Sie diese Option aus, um die Unschärfemaske auf die Bildhelligkeit anzuwenden (Intensität).<br> Deaktivieren Sie diese Unteroption, um die Unschärfemaske auf jede Farbkomponente einzeln anzuwenden. |
| Hintergrund aussparen |  | Entfernt beim Hochladen automatisch den Hintergrund eines Bildes. Mit dieser Technik ist es möglich, die Aufmerksamkeit auf ein bestimmtes Objekt zu lenken und es von einem belebten Hintergrund abzuheben. Wählen Sie diese Option aus, um die Funktion „Hintergrund aussparen“ und die folgenden Optionen zu aktivieren: |
|  | Ecke | Erforderlich.<br> Die Ecke des Bildes, mit der die auszusparende Hintergrundfarbe definiert wird.<br> Sie können aus **Oben links**, **Unten links**, **Oben rechts** und **Unten rechts** wählen. |
|  | Füllmethode | Erforderlich.<br> Zur Steuerung der Pixeltransparenz ausgehend von der Ecke, die Sie gewählt haben.<br> Sie können aus folgenden Füllmethoden wählen: <ul><li>**Großflächig füllen** – Macht alle Pixel transparent, die mit der von Ihnen angegebenen Ecke übereinstimmen und mit ihr verbunden sind.</li><li>**Pixel abgleichen** – Macht alle entsprechenden Pixel transparent, unabhängig von ihrer Position auf dem Bild.</li></ul> |
|  | Toleranz | Optional.<br> Steuert die zulässige Abweichung der Pixelfarbe ausgehend von der Ecke, die Sie festgelegt haben.<br> Verwenden Sie den Wert 0,0, um die Pixelfarben genau anzugleichen, oder verwenden Sie den Wert 1,0, um die größtmögliche Abweichung zuzulassen. |

#### Festlegen der Upload-Optionen für PostScript und Illustrator {#setting-postscript-and-illustrator-upload-options}

Wenn Sie PostScript (EPS)- oder Illustrator (AI)-Bilddateien hochladen, können Sie diese auf verschiedene Arten formatieren. Sie können die Dateien rastern, den transparenten Hintergrund beibehalten sowie eine Auflösung und einen Farbraum auswählen. Optionen zum Formatieren von PostScript- und Illustrator-Dateien stehen im Dialogfeld „Upload-Auftragsoptionen“ unter PostScript- und Illustrator-Optionen zur Verfügung.

| Option | Unteroption | Beschreibung |
|---|---|---|
| Verarbeitung |  | Wählen Sie **[!UICONTROL Rastern]**, um Vektorgrafiken in der Datei in das Bitmap-Format zu konvertieren. |
| Transparenten Hintergrund in gerendertem Bild beibehalten |  | Zur Beibehaltung der Hintergrundtransparenz der Datei. |
| Auflösung |  | Zur Einstellung der Auflösung. Mit dieser Einstellung wird bestimmt, wie viele Pixel pro Zoll in der Datei angezeigt werden. |
| Farbraum |  | Klicken Sie auf das Menü „Farbraum“ und wählen Sie unter den folgenden Farbraumoptionen: |
|  | Automatisch erkennen | Der Farbraum der Datei wird beibehalten. |
|  | Immer RGB | Zur Konvertierung in den RGB-Farbraum. |
|  | Immer CMYK | Zur Konvertierung in den CMYK-Farbraum. |
|  | Immer Graustufen | Zur Konvertierung in den Graustufenfarbraum. |

#### Festlegen der Photoshop-Upload-Optionen {#setting-photoshop-upload-options}

PSD (Photoshop)-Dateien werden meist zum Erstellen von Bildvorlagen verwendet. Wenn Sie eine PSD-Datei hochladen, können Sie daraus automatisch eine Bildvorlage erstellen (aktivieren Sie auf dem Uploadbildschirm die Option „Vorlage erstellen“). 

Dynamic Media erstellt mehrere Bilder aus einer PSD-Datei mit Ebenen, wenn Sie die Datei zum Erstellen einer Vorlage verwenden. Für jede Ebene wird ein Bild erstellt.

Verwenden Sie die oben beschriebenen Optionen **[!UICONTROL Beschneidungsoptionen]** und **[!UICONTROL Profil-Farboptionen]** mit Photoshop-Upload-Optionen.

>[!NOTE]
>
>Vorlagen werden nicht in AEM unterstützt.

| Option | Unteroption | Beschreibung |
|---|---|---|
| Ebenen beibehalten |  | Teilt die Ebenen in der PSD-Datei ggf. in einzelne Assets auf. Die Asset-Ebenen bleiben der PSD-Datei zugeordnet. Sie können sie anzeigen, indem Sie die PSD-Datei in der Detailansicht öffnen und das Ebenenfenster auswählen. |
| Vorlage erstellen |  | Erstellt eine Vorlage aus den Ebenen der PSD-Datei. |
| Text extrahieren |  | Extrahiert den Text, damit Benutzer im Viewer den Text durchsuchen können. |
| Ebenen auf Hintergrundgröße ausdehnen |  | Erweitert die Größe aufgeteilter Bildebenen auf die Größe der Hintergrundebene. |
| Ebenenbenennung |  | Ebenen in der PSD-Datei werden als separate Bilder hochgeladen. |
|  | Ebenenname | Benennt die Bilder nach ihren Ebenennamen in der PSD-Datei. Wenn eine Ebene in der Original-PSD-Datei beispielsweise „Preisschild“ heißt, wird auch das zugehörige Bild „Preisschild“ genannt. Wenn es sich bei den Ebenennamen in der PSD-Datei jedoch um standardmäßige Photoshop-Ebenennamen handelt (Hintergrund, Ebene 1, Ebene 2 usw.), werden die Bilder nicht nach den Standardebenennamen, sondern nach den zugehörigen Ebenennummern in der PSD-Datei benannt. |
|  | Photoshop- und Ebenennummer | Benennt die Bilder nach ihren Ebenennummern in der PSD-Datei und ignoriert die ursprünglichen Ebenennamen. Bilder werden mit dem Photoshop-Dateinamen und einer angefügten Ebenennummer benannt. Zum Beispiel erhält die zweite Ebene der Datei Frühjahrsannonce.psd den Namen Frühjahrsannonce_2, auch wenn sie in Photoshop einen nicht standardmäßigen Namen hatte. |
|  | Photoshop- und Ebenenname | Benennt die Bilder nach der PSD-Datei, gefolgt vom Ebenennamen oder der -nummer. Die Ebenennummer wird verwendet, wenn es sich bei den Ebenennamen in der PSD-Datei um standardmäßige Photoshop-Ebenennamen handelt. Zum Beispiel erhält eine Ebene mit dem Namen „Preisschild“ in einer PSD-Datei mit dem Namen „Frühjahrsannonce“ den Namen „Frühjahrsannonce_Preisschild“. Eine Ebene mit dem standardmäßigen Namen „Ebene 2“ erhält den Namen „Frühjahrsannonce_2“. |
| Anker |  | Geben Sie an, wie Bilder in Vorlagen, die aus der Zusammenstellung der Ebenen aus der PSD-Datei erstellt werden, verankert werden. Der Anker ist standardmäßig zentriert. Ein zentrierter Anker eignet sich am besten zum Auffüllen desselben Raums mit Ersatzbildern, unabhängig vom Seitenverhältnis der Ersatzbilder. Bilder mit einem anderen Seitenverhältnis, die dieses Bild ersetzen, nehmen effektiv denselben Raum ein, wenn auf die Vorlage verwiesen und die Parameterersetzung durchgeführt wird. Wählen Sie eine andere Einstellung, wenn es für Ihre Anwendung erforderlich ist, dass die Ersatzbilder den zugeordneten Raum in der Vorlage ausfüllen. |

#### Festlegen von PDF-Upload-Optionen {#setting-pdf-upload-options}

Wenn Sie eine PDF-Datei hochladen, können Sie diese auf verschiedene Arten formatieren. Sie können ihre Seiten zuschneiden, Suchbegriffe extrahieren, eine ppi (Pixel pro Zoll)-Auflösung eingeben und einen Farbraum auswählen. PDF-Dateien enthalten oft einen Beschnittrand, Schnittmarken, Registrierungsmarken und andere Druckermarken. Sie können diese Marken von den Seitenrändern aus zuschneiden, wenn Sie eine PDF-Datei hochladen.

>[!NOTE]
>
>E-Kataloge werden nicht in AEM unterstützt.

Wählen Sie unter folgenden Optionen:

| Option | Unteroption | Beschreibung |
|---|---|---|
| Verarbeitung | Rastern | (Standard) Zum Extrahieren der Seiten aus der PDF-Datei und zum Konvertieren von Vektorgrafiken in Bitmap-Bilder. Wählen Sie diese Option, um einen E-Katalog zu erstellen. |
| Extrahieren | Suchbegriffe | Zum Extrahieren von Wörtern aus der PDF-Datei, damit die Datei in einem E-Katalog-Viewer mit einem Schlüsselwort durchsucht werden kann. |
|  | Links | Zum Extrahieren von Links aus den PDF-Dateien und zum Konvertieren der PDF-Dateien in Imagemaps, die in einem E-Katalog-Viewer verwendet werden. |
| E-Katalog aus mehrseitiger PDF automatisch erstellen |  | Zum automatischen Erstellen eines E-Katalogs aus der PDF-Datei. Der E-Katalog wird nach der von Ihnen hochgeladenen PDF-Datei benannt. (Diese Option ist nur dann verfügbar, wenn Sie die PDF-Datei beim Hochladen rastern.) |
| Auflösung |  | Zum Festlegen der Auflösung: Mit dieser Einstellung wird bestimmt, wie viele Pixel pro Zoll in der PDF-Datei angezeigt werden. Standard: 150. |
| Farbraum |  | Wählen Sie das Farbraummenü und einen Farbraum für die PDF-Datei aus. Die meisten PDF-Dateien enthalten sowohl RGB- als auch CMYK-Farbbilder. Der RGB-Farbraum eignet sich besonders gut, um Dateien online anzuzeigen. |
|  | Automatisch erkennen | Der Farbraum der PDF-Datei wird beibehalten. |
|  | Immer RGB | Zur Konvertierung in den RGB-Farbraum. |
|  | Immer CMYK | Zur Konvertierung in den CMYK-Farbraum. |
|  | Immer Graustufen | Zur Konvertierung in den Graustufenfarbraum. |

#### Einstellen der eVideo-Upload-Optionen {#setting-evideo-upload-options}

Sie können eine Videodatei neu kodieren, indem Sie aus einer Vielzahl von Videovorgaben auswählen.

| Option | Unteroption | Beschreibung |
|---|---|---|
| Adaptives Video |  | Eine einzelne Kodierungsvorgabe, die mit jedem Seitenverhältnis verwendet werden kann, um Videos für Versand zu Mobilgeräten, Tablets und Desktops zu erstellen. Hochgeladene Quellvideos, die mit dieser Vorgabe kodiert wurden, weisen eine feste Höhe auf. Die Breite wird jedoch automatisch skaliert, um das Seitenverhältnis des Videos beizubehalten. <br>Die beste Vorgehensweise ist die Verwendung der adaptiven Videokodierung. |
| Einzelne Kodierungsvorgaben | Kodierungsvorgaben sortieren | Wählen Sie &quot;Name&quot;oder &quot;Größe&quot;, um die unter &quot;Desktop&quot;, &quot;Mobil&quot;und &quot;Tablet&quot;aufgelisteten Kodierungsvorgaben nach Name oder Auflösung zu sortieren. |
|  | Desktop | Erstellen Sie eine MP4-Datei zur Bereitstellung eines Streaming- oder progressiven Videoerlebnisses auf Desktop-Computern.Wählen Sie ein oder mehrere Seitenverhältnisse mit der gewünschten Auflösung und Datenrate für die Zielgruppe aus. |
|  | Mobilgerät | Erstellen Sie eine MP4-Datei für den Versand auf iPhone- oder Android-Mobilgeräten.Wählen Sie ein oder mehrere Seitenverhältnisse mit der gewünschten Auflösung und Zielgruppe für die Datenrate aus. |
|  | Tablet | Erstellen Sie eine MP4-Datei für den Versand auf iPad- oder Android-Tablet-Geräten.Wählen Sie ein oder mehrere Seitenverhältnisse mit der gewünschten Auflösung und Datenrate für die Zielgruppe aus. |

#### Stapelsatzvorgaben beim Hochladen festlegen {#setting-batch-set-presets-at-upload}

Wenn Sie aus hochgeladenen Bildern automatisch einen Bildsatz oder ein Rotationsset erstellen möchten, klicken Sie für die gewünschte Vorgabe auf die Spalte **[!UICONTROL Aktiv]**. Sie können mehrere Vorgaben auswählen. 

Weitere Informationen zur Erstellung von Stapelsatzvorgaben finden Sie unter [Konfigurieren von Stapelsatzvorgaben zum automatischen Erstellen von Bild- und Rotationssets](config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets).

### Gestreamte Uploads {#streamed-uploads}

Wenn Sie viele Assets hochladen, steigt die Zahl der I/O-Aufrufe, die an den AEM-Server gesendet werden, drastisch an, wodurch die Upload-Effizienz verringert wird und sogar eine Zeitüberschreitung auftreten kann. AEM Assets unterstützt gestreamte Uploads von Assets. Gestreamte Uploads sorgen für eine Datenträger-I/O-Reduzierung beim Hochladen, da die Speicherung von Assets in einem temporären Ordner auf dem Server vermieden wird, bevor Assets in das Repository kopiert werden. Stattdessen werden die Daten direkt an das Repository übertragen. Auf diese Weise wird die Zeit für das Hochladen von Assets und die Möglichkeit von Zeitüberschreitungen verringert. Das gestreamte Hochladen ist in AEM Assets standardmäßig aktiviert.

Die Funktion „Streaming-Upload“ ist für den Betrieb von AEM auf JEE-Servern mit Servlet-API. Version unter 3.1 deaktiviert.

### ZIP-Archiv mit Assets extrahieren {#extract-zip-archive-containing-assets}

Sie können ZIP-Archive wie jedes andere unterstützte Asset hochladen. Für ZIP-Dateien gelten dieselben Regeln für Dateinamen. Mit AEM können Sie ein ZIP-Archiv in einen DAM-Speicherort extrahieren.

Wählen Sie jeweils ein ZIP-Archiv aus, klicken Sie auf **[!UICONTROL Archiv extrahieren]** und wählen Sie einen Zielordner aus. Wählen Sie eine Option für den Umgang mit eventuellen Konflikten. Wenn die Assets in der ZIP-Datei bereits im Zielordner vorhanden sind, können Sie eine der folgenden Optionen auswählen: Extrahieren überspringen, vorhandene Dateien ersetzen, beide Assets durch Umbenennen behalten oder neue Version erstellen.

Nach Abschluss des Extrahierungsvorgangs erhalten Sie von AEM eine Benachrichtigung im Benachrichtigungsbereich. Während AEM das ZIP-Archiv extrahiert, können Sie ohne Unterbrechung des Extrahierungsvorgangs mit Ihrer Arbeit fortfahren.

![Meldung der Postleitzahl-Extraktion](assets/zip_extract_notification.png)

Die Funktion hat einige Einschränkungen:

* Wenn sich ein gleichnamiger Ordner am Ziel befindet, werden die Assets aus der ZIP-Datei in diesen extrahiert.

* Wenn Sie die Extrahierung abbrechen, werden die bereits extrahierten Assets nicht gelöscht.

* Sie können nicht gleichzeitig zwei ZIP-Dateien auswählen und extrahieren. Sie können jeweils nur ein ZIP-Archiv extrahieren.

## Anzeigen einer Vorschau für Assets {#previewing-assets}

**So zeigen Sie die Asset-Vorschau an**:

1. Navigieren Sie in der Benutzeroberfläche &quot;Assets&quot;zum Speicherort des Assets, das Sie Vorschau haben möchten.
1. Tippen Sie auf das gewünschte Asset, um es zu öffnen.

1. Im Vorschaumodus ist eine Zoom-Funktion für [unterstützte Bildtypen](assets-formats.md#supported-raster-image-formats) verfügbar (mit interaktiver Bearbeitung).

   Um ein Asset zu vergrößern, tippen Sie auf **[!UICONTROL +]** (oder tippen Sie auf die Lupe des Assets). Um die Ansicht zu verkleinern, tippen Sie auf **[!UICONTROL -]**. Beim Heranzoomen können Sie beliebige Bildbereiche durch Schwenken genauer untersuchen. Mit dem Pfeil **[!UICONTROL Zoom zurücksetzen]** gelangen Sie zurück zur Originalansicht.

   ![uploadicon](assets/uploadicon.png)

   Tippen Sie auf die Schaltfläche **[!UICONTROL Zurücksetzen]**, um die Originalgröße der Ansicht wiederherzustellen.

   ![chlimage_1-11](assets/chlimage_1-11.png)

>[!MORELIKETHIS]
>
>* [Vorschau Dynamic Media Assets](/help/assets/previewing-assets.md).
>* [Anzeigen von Unter-Assets](managing-linked-subassets.md#viewing-subassets).


## Eigenschaften bearbeiten {#editing-properties}

1. Navigieren Sie zum Speicherort des Assets, dessen Metadaten Sie bearbeiten möchten.

1. Wählen Sie das Asset aus und tippen Sie in der Symbolleiste auf **[!UICONTROL Eigenschaften]**, um die Asset-Eigenschaften Ansicht. Wählen Sie alternativ die Schnellaktion **[!UICONTROL Eigenschaften]** auf der Asset-Karte aus.

   ![properties_quickaction](assets/properties_quickaction.png)

1. Bearbeiten Sie auf der Registerkarte **[!UICONTROL Eigenschaften]** die Metadateneigenschaften auf den verschiedenen Registerkarten. Zum Beispiel bearbeiten Sie auf der Registerkarte **[!UICONTROL Allgemein]** den Titel, die Beschreibung usw.

   Das Layout der Seite **[!UICONTROL Eigenschaften]** und die verfügbaren Metadaten sind vom zugrunde liegenden Metadatenschema abhängig. Informationen dazu, wie Sie das Layout der Seite **[!UICONTROL Eigenschaften]** ändern können, finden Sie unter [Metadatenschemata](metadata-schemas.md).

1. Um ein bestimmtes Datum/eine Zeit für die Aktivierung der Assets einzustellen, verwenden Sie die Datumsauswahl neben dem Feld **[!UICONTROL Einschaltzeit]**.

   ![Zeit &quot;On&quot;für Assets festlegen, damit Assets für einen bestimmten Zeitraum zwischen Ein- und Auszeit verfügbar gemacht werden](assets/chlimage_1-12.png)

1. Um das Asset nach einer bestimmten Dauer zu deaktivieren, wählen Sie das Deaktivierungsdatum und die Uhrzeit aus der Datumsauswahl neben dem Feld **[!UICONTROL Off Time]**.

   Das Deaktivierungsdatum sollte nach dem Aktivierungsdatum für ein Asset liegen. Nach der [!UICONTROL Ausschaltzeit] sind ein Asset und seine Ausgabedarstellungen weder über die Assets-Web-Oberfläche noch über die HTTP-API verfügbar.

   ![Zeit einstellen, damit Assets nach einem bestimmten Zeitraum nicht mehr verfügbar sind](assets/chlimage_1-13.png)

1. Wählen Sie im Feld **[!UICONTROL Tags]** ein oder mehrere Tags aus. Um ein benutzerdefiniertes Tag hinzuzufügen, geben Sie den Namen des Tags in das Feld ein und drücken Sie **[!UICONTROL die Eingabetaste]**. Das neue Tag wird in AEM gespeichert.

   YouTube erfordert Tags, um zu veröffentlichen und einen Link zu YouTube (wenn ein geeigneter Link gefunden werden kann).
Zum Erstellen von Tags benötigen Sie Schreibberechtigung für `/content/cq:tags/default` im CRX-Repository.

1. Um eine Bewertung für das Asset bereitzustellen, tippen Sie auf die Registerkarte **[!UICONTROL Erweitert]** und dann auf den Stern an der entsprechenden Position, um die gewünschte Bewertung zuzuweisen.

   ![Bewertungen](assets/ratings.png)

   Die Bewertungsnote, die Sie dem Asset zuweisen, wird unter **[!UICONTROL Ihre Bewertungen]** angezeigt. Die durchschnittliche Bewertungsnote, die das Asset von Benutzern erhält, wird unter **[!UICONTROL Bewertung]** angezeigt. Darüber hinaus wird die Aufschlüsselung der Bewertungen, die zur durchschnittlichen Bewertungsnote beitragen, unter **[!UICONTROL Bewertungsübersicht]** angezeigt. Sie können Assets basierend auf der durchschnittlichen Bewertungsnote durchsuchen.

1. Um Nutzungsstatistiken für das Asset zu erhalten, tippen Sie auf die Registerkarte **[!UICONTROL Insights]**.

   Nutzungsstatistiken umfassen folgende Metriken:

   * Anzahl der Aufrufe oder Downloads des Assets.
   * Kanäle/Geräte, über die das Asset genutzt wurde.
   * Kreativlösungen, in denen das Asset kürzlich verwendet wurde.

   Weitere Informationen finden Sie unter [Asset Insights](touch-ui-asset-insights.md).

1. Tippen Sie auf **[!UICONTROL Speichern und Schließen]**.
1. Navigieren Sie zur Assets-Benutzeroberfläche. Die bearbeiteten Metadateneigenschaften, einschließlich Titel, Beschreibung, Bewertungen usw., werden auf der Asset-Ansicht in der Karten-Ansicht und unter den entsprechenden Spalten in der Liste angezeigt.

## Kopieren von Assets {#copying-assets}

Beim Kopieren eines Assets oder eines Ordners wird das gesamte Asset bzw. der Ordner mitsamt seiner Inhaltsstruktur kopiert. Ein kopiertes Asset oder ein kopierter Ordner wird am Zielspeicherort dupliziert. Das Asset am Quellspeicherort bleibt unverändert.

Einige wenige, für eine bestimmte Kopie eines Assets eindeutige Attribute werden nicht übertragen. Beispiele:

* Asset-ID, Erstellungsdatum und -zeitpunkt sowie Versionen und Versionsverlauf. Einige dieser Eigenschaften sind an den Eigenschaften `jcr:uuid`, `jcr:created` und `cq:name` zu erkennen.

* Der Erstellungszeitpunkt und referenzierte Pfade sind für jedes Asset und jede seiner Ausgabedarstellungen eindeutig.

Die übrigen Eigenschaften und Metadateninformationen werden beibehalten. Eine Teilkopie wird beim Kopieren eines Assets nicht erstellt.

1. Wählen Sie in der Benutzeroberfläche &quot;Assets&quot;einen oder mehrere Assets aus und tippen Sie dann in der Symbolleiste auf das Symbol **[!UICONTROL Kopieren]**. Alternativ können Sie die Schnellaktion **[!UICONTROL Kopieren]** aus der Asset-Karte wählen.

   ![copy_icon](assets/copy_icon.png)

   >[!NOTE]
   >
   >Wenn Sie die Schnellaktion **[!UICONTROL Kopieren]** verwenden, können Sie immer nur ein Asset gleichzeitig kopieren.

1. Navigieren Sie zum Speicherort, an den Sie die Assets kopieren möchten.

   >[!NOTE]
   >
   >Wenn Sie ein Asset in denselben Speicherort kopieren, generiert AEM automatisch eine Variation des Namens. Beispiel: Wenn Sie ein Asset mit dem Namen „Quadrat“ kopieren, generiert AEM automatisch den Namen „Quadrat1“ für die Kopie.

1. Tippen Sie in der Symbolleiste auf das Asset-Symbol **[!UICONTROL Einfügen]**:

   ![chlimage_1-14](assets/chlimage_1-14.png)

   Die Assets werden in diesen Speicherort kopiert.

   >[!NOTE]
   >
   >Das Symbol **[!UICONTROL Einfügen]** ist in der Symbolleiste verfügbar, bis das Einfügen abgeschlossen ist.

## Verschieben und Umbenennen von Assets {#moving-or-renaming-assets}

Wenn Sie Assets (oder Ordner) an einen anderen Speicherort verschieben, werden die Assets (oder Ordner) nicht dupliziert, anders als beim Kopieren des Assets. Die Assets (oder die Ordner) werden am Speicherort der Zielgruppe platziert und vom Quellspeicherort entfernt. Sie können das Asset auch umbenennen, wenn Sie es an den neuen Speicherort verschieben. Wenn Sie ein veröffentlichtes Asset an einen anderen Speicherort verschieben, haben Sie die Möglichkeit, das Asset erneut zu veröffentlichen. Standardmäßig wird beim Verschieben eines veröffentlichten Assets die Veröffentlichung automatisch rückgängig gemacht. Verschiebte Assets werden erneut veröffentlicht, wenn der Autor beim Verschieben des Assets die Option [!UICONTROL Neu veröffentlichen] auswählt.

![Sie können bereits veröffentlichte Assets beim Verschieben erneut veröffentlichen](assets/republish-on-move.png)

So verschieben Sie Assets oder Ordner:

1. Navigieren Sie zum Speicherort des Assets, das Sie verschieben möchten.

![Sie können bereits veröffentlichte Assets beim Verschieben erneut veröffentlichen](assets/republish-on-move.png)

So verschieben Sie Assets oder Ordner:

1. Navigieren Sie zum Speicherort des Assets, das Sie verschieben möchten.

1. Wählen Sie das Asset aus und klicken Sie in der Symbolleiste auf die Option **[!UICONTROL Verschieben]**.
   ![Option &quot;Verschieben&quot;in der Assets-Symbolleiste](assets/do-not-localize/move_icon.png)

1. Führen Sie im Assistenten [!UICONTROL Assets verschieben] einen der folgenden Schritte aus:

   * Geben Sie nach dem Verschieben den Namen für das Asset an. Klicken Sie dann auf **[!UICONTROL Weiter]**, um fortzufahren.

   * Klicken Sie auf **[!UICONTROL Abbrechen]**, um den Prozess zu beenden.
   >[!NOTE]
   >
   >* Sie können denselben Namen für das Asset angeben, wenn sich am neuen Speicherort kein Asset mit diesem Namen befindet. Sie sollten jedoch einen anderen Namen verwenden, wenn Sie das Asset an einen Speichertort verschieben, an dem bereits ein Asset mit demselben Namen vorhanden ist. Wenn Sie denselben Namen verwenden, generiert das System automatisch eine Variante dieses Namens. Wenn Sie beispielsweise ein Asset mit dem Namen „Quadrat“ kopieren, generiert das System den Namen „Quadrat1“ für die Kopie.
   >* Beim Umbenennen sind keine Leerzeichen in Dateinamen zulässig.


1. Führen Sie im Dialogfeld **[!UICONTROL Ziel auswählen]** eine der folgenden Aktionen aus:

   * Navigieren Sie zum neuen Speicherort für die Assets und klicken Sie dann auf **[!UICONTROL Weiter]**, um fortzufahren.

   * Klicken Sie auf **[!UICONTROL Zurück]**, um zum Bildschirm **[!UICONTROL Umbenennen]** zurückzukehren.

1. Wenn die verschobenen Assets verweisende Seiten, Assets oder Sammlungen umfassen, wird die Registerkarte **[!UICONTROL Verweise anpassen]** neben der Registerkarte **[!UICONTROL Ziel auswählen]** angezeigt.

   Führen Sie im Bildschirm **[!UICONTROL Verweise anpassen]** einen der folgenden Schritte aus:

   * Geben Sie die Verweise an, die basierend auf den neuen Details angepasst werden sollen, und klicken Sie dann auf **[!UICONTROL Verschieben]**, um fortzufahren.

   * Aktivieren/deaktivieren Sie in der Spalte **[!UICONTROL Anpassen]** Verweise auf die Assets.
   * Klicken Sie auf **[!UICONTROL Zurück]**, um zum Bildschirm **[!UICONTROL Ziel auswählen]** zurückzukehren.

   * Klicken Sie auf **[!UICONTROL Abbrechen]**, um den Verschieben-Vorgang zu beenden.

   Wenn Sie die Verweise nicht aktualisieren, verweisen sie weiterhin auf den alten Asset-Pfad. Wenn Sie die Verweise aktualisieren, werden sie an den neuen Asset-Pfad angepasst.

### Verschieben von Assets mithilfe des Ziehvorgangs {#move-using-drag}

Sie können Assets (oder Ordner) in einen Ordner verschieben, indem Sie sie an den Speicherort der Zielgruppe ziehen, anstatt die Option [!UICONTROL Verschieben] in der Benutzeroberfläche zu verwenden. Dieser Vorgang ist jedoch nur in der Ansicht der Liste möglich.

Wenn Sie Assets durch Ziehen verschieben, wird der Assistent [!UICONTROL Asset verschieben] nicht geöffnet. Daher erhalten Sie beim Verschieben keine Option zum Umbenennen der Assets. Darüber hinaus werden die bereits veröffentlichten Assets beim Verschieben durch Ziehen erneut veröffentlicht, ohne dass die Zustimmung des Benutzers zur erneuten Veröffentlichung eingeholt werden muss.

![Verschieben von Assets in gleichgeordnete Ordner durch Ziehen von Assets](assets/move-by-drag.gif)

## Verwalten von Ausgabedarstellungen {#managing-renditions}

1. Sie können Ausgabedarstellungen für ein Asset hinzufügen oder entfernen, mit Ausnahme des Originals. Navigieren Sie zum Speicherort des Assets, für das Sie Ausgabedarstellungen hinzufügen oder entfernen möchten.

1. Tippen Sie auf das Asset, um seine Asset-Seite zu öffnen.

   ![chlimage_1-15](assets/chlimage_1-15.png)

1. Tippen Sie auf das Symbol **[!UICONTROL Globale Navigation]** und wählen Sie **[!UICONTROL Darstellungen]** aus der Liste.

   ![renditions_menu](assets/renditions_menu.png)

1. Im Bereich **[!UICONTROL Ausgabedarstellungen]** wird die Liste der für das Asset generierten Ausgabedarstellungen angezeigt.

   ![renditions_panel](assets/renditions_panel.png)

   >[!NOTE]
   >
   >Standardmäßig zeigt AEM Assets im Vorschaumodus nicht die ursprüngliche Ausgabedarstellung des Assets an. Wenn Sie ein Administrator sind, können Sie Überlagerungen verwenden, um AEM Assets so zu konfigurieren, dass ursprüngliche Ausgabedarstellungen im Vorschaumodus angezeigt werden.

1. Wählen Sie eine Ausgabedarstellung aus, um sie anzuzeigen oder zu löschen.

   **Eine Darstellung löschen**

   Wählen Sie eine Darstellung aus dem Bedienfeld **[!UICONTROL Ausgabeformate]** und tippen Sie dann auf das Symbol **[!UICONTROL Ausgabeformat]** aus der [Symbolleiste](/help/sites-authoring/basic-handling.md). Ausgabedarstellungen können nach Abschluss der Asset-Verarbeitung nicht mehr stapelweise gelöscht werden. Bei einzelnen Assets können Sie Ausgabedarstellungen manuell aus der Benutzeroberfläche entfernen. Bei mehreren Assets können Sie Experience Manager anpassen, um bestimmte Darstellungen zu löschen oder die Assets zu löschen und die gelöschten Assets erneut hochzuladen.

   ![delete_renditionicon](assets/delete_renditionicon.png)

   **Eine neue Darstellung hochladen**

   Navigieren Sie zur Seite mit den Asset-Details und klicken Sie auf das Symbol **[!UICONTROL Hinzufügen Darstellung]** in der Symbolleiste, um eine neue Darstellung für das Asset hochzuladen.

   ![chlimage_1-16](assets/chlimage_1-16.png)

   >[!NOTE]
   >
   >Wenn Sie eine Ausgabedarstellung im Bedienfeld **[!UICONTROL Ausgabedarstellungen]** auswählen, wird der Kontext der Symbolleiste geändert, sodass nur die für die Ausgabedarstellung relevanten Aktionen angezeigt werden. Optionen wie das Symbol **[!UICONTROL Darstellung hochladen]** werden nicht angezeigt. Um diese Optionen in der Symbolleiste anzuzeigen, navigieren Sie zur Detailseite für das Asset.

   Sie können die Dimensionen für die anzuzeigende Ausgabedarstellung auf der Detailseite des entsprechenden Bild- oder Video-Assets konfigurieren. AEM Assets zeigt anhand der von Ihnen angegebenen Abmessungen die Ausgabedarstellung mit den genauen oder möglichst genauen Abmessungen an.

   Um die Darstellungsdimensionen eines Bildes auf der Ebene der Asset-Details zu konfigurieren, überlagern Sie den Knoten **[!UICONTROL renditionpicker]** `libs/dam/gui/content/assets/assetpage/jcr:content/body/content/content/items/assetdetail/items/col1/items/assetview/renditionpicker` und konfigurieren Sie den Wert der Eigenschaft width. Konfigurieren Sie die Eigenschaft **[!UICONTROL size (Long) in KB]** anstelle von „width“, um die Ausgabedarstellung auf der Asset-Detailseite auf Grundlage der Bildgröße anzupassen. Bei größenbasierter Anpassung gibt die Eigenschaft **[!UICONTROL preferOriginal]** der Originalgröße den Vorzug, wenn das angepasste Wiedergabeformat größer ist als das Original.

   Ebenso können Sie das Seitenbild **[!UICONTROL Anmerkung]** anpassen, indem Sie `libs/dam/gui/content/assets/annotate/jcr:content/body/content/content/items/content/renditionpicker` überlagern.

   ![chlimage_1-17](assets/chlimage_1-17.png)

   Um die Darstellungsdimensionen für ein Video-Asset zu konfigurieren, navigieren Sie zum Knoten **[!UICONTROL videopicker]** im CRX-Repository am Speicherort `/libs/dam/gui/content/assets/assetpage/jcr:content/body/content/content/items/assetdetail/items/col1/items/assetview/videopicker`, überlagern Sie den Knoten und bearbeiten Sie dann die entsprechende Eigenschaft.

   >[!NOTE]
   >
   >Videoanmerkungen werden nur bei Browsern mit HTML5-kompatiblen Videoformaten unterstützt. Darüber hinaus werden je nach Browser unterschiedliche Videoformate unterstützt.

Weitere Informationen zu Teilassets finden Sie unter [Teilassets verwalten](managing-linked-subassets.md).

## Löschen von Assets {#deleting-assets}

Um die eingehenden Verweise von anderen Seiten aufzulösen oder zu entfernen, aktualisieren Sie die entsprechenden Verweise, bevor Sie ein Asset löschen.

Deaktivieren Sie außerdem die Schaltfläche „Löschen erzwingen“ mithilfe einer Überlagerung, um zu verhindern, dass Benutzer referenzierte Assets löschen und fehlerhafte Links hinterlassen.

Sie benötigen eine Löschberechtigung für DAM/Asset, um ein Asset löschen zu können. Wenn Sie nur eine Änderungsberechtigung haben, haben Sie nur die Möglichkeit, die Asset-Metadaten zu bearbeiten und Notizen zum Asset hinzuzufügen. Sie können jedoch das Asset oder dessen Metadaten nicht löschen.

**So löschen Sie Assets**:

1. Navigieren Sie zum Speicherort der Assets, die Sie löschen möchten.

1. Wählen Sie das Asset aus und tippen Sie in der Symbolleiste auf das Symbol **[!UICONTROL Löschen]**.

   ![delete_icon](assets/delete_icon.png)

1. Tippen Sie im Bestätigungsdialogfeld auf:

   * **[!UICONTROL Abbrechen]**, um die Aktion abzubrechen.
   * **[!UICONTROL Löschen Sie]** die Aktion auf der Grundlage der folgenden Punkte:

      * Wenn das Asset keine Referenzen aufweist, wird es gelöscht.
      * Wenn das Asset Referenzen enthält, werden Sie durch eine Fehlermeldung darüber informiert, dass **[!UICONTROL auf eines oder mehrere Assets verwiesen wird. Sie können**[!UICONTROL  Löschen erzwingen ]**oder**[!UICONTROL  Abbrechen ]**auswählen.]**

   >[!NOTE]
   >
   >Um die eingehenden Verweise von anderen Seiten aufzulösen oder zu entfernen, aktualisieren Sie die entsprechenden Verweise, bevor Sie ein Asset löschen.
   >
   >Deaktivieren Sie außerdem die Schaltfläche **[!UICONTROL Löschen]** erzwingen, indem Sie eine Überlagerung verwenden, um Benutzer daran zu hindern, referenzierte Assets zu löschen und fehlerhafte Links zu belassen.

## Herunterladen von Assets {#downloading-assets}

Siehe [Herunterladen von Assets aus AEM](download-assets-from-aem.md)

## Veröffentlichen und Rückgängigmachen der Veröffentlichung von Assets {#publish-assets}

Nach dem Hochladen, Verarbeiten oder Bearbeiten Ihrer Assets auf dem [!DNL Experience Manager]-Autor veröffentlichen Sie das Asset auf dem Veröffentlichungsserver. Durch Veröffentlichen wird das Asset öffentlich verfügbar gemacht. Beim Rückgängigmachen der Veröffentlichung wurde das Asset vom Veröffentlichungsserver, jedoch nicht vom Authoring-Server entfernt.

Spezifische Informationen zu [!DNL Dynamic Media] finden Sie unter [publishing [!DNL Dynamic Media] assets](publishing-dynamicmedia-assets.md).

1. Navigieren Sie zum Speicherort des Assets oder Asset-Ordners, den Sie veröffentlichen möchten oder den Sie aus der Umgebung &quot;Veröffentlichung rückgängig machen&quot;entfernen möchten.

1. Wählen Sie das Asset oder den Ordner aus, dessen Veröffentlichung rückgängig gemacht werden soll, und klicken Sie in der Symbolleiste auf die Option **[!UICONTROL Veröffentlichung verwalten]** ![Veröffentlichungsoption verwalten](assets/do-not-localize/globe-publication.png). Um eine schnelle Veröffentlichung zu ermöglichen, wählen Sie in der Symbolleiste die Option **[!UICONTROL Schnellveröffentlichung]**. Wenn der Ordner, den Sie veröffentlichen möchten, einen leeren Ordner enthält, wird der leere Ordner nicht veröffentlicht.

1. Wählen Sie nach Bedarf die Option **[!UICONTROL Veröffentlichen]** oder **[!UICONTROL Veröffentlichung rückgängig machen]**.

   ![Aktion rückgängig machen](assets/unpublish_action.png)
   *Abbildung: Optionen zum Veröffentlichen und Rückgängigmachen der Veröffentlichung und die Planungsoption.*

1. Wählen Sie **[!UICONTROL Jetzt]** aus, um sofort auf das Asset zu reagieren, oder wählen Sie **[!UICONTROL Später]**, um die Aktion zu planen. Wählen Sie ein Datum und eine Uhrzeit aus, wenn Sie die Option **[!UICONTROL Später]** wählen. Klicken Sie auf **[!UICONTROL Weiter]**.

1. Wenn beim Veröffentlichen ein Asset auf andere Assets verweist, werden seine Verweise im Assistenten aufgeführt. Es werden nur die Verweise angezeigt, die seit der letzten Veröffentlichung nicht veröffentlicht oder geändert wurden. Wählen Sie die Verweise aus, die Sie veröffentlichen möchten.

1. Wenn Sie die Veröffentlichung rückgängig machen und ein Asset auf andere Assets verweist, wählen Sie die Referenzen aus, deren Veröffentlichung Sie rückgängig machen möchten. Klicken Sie auf **[!UICONTROL Veröffentlichung rückgängig machen]**. Klicken Sie im Bestätigungsdialogfeld auf **[!UICONTROL Abbrechen]**, um die Aktion zu beenden, oder klicken Sie auf **[!UICONTROL Veröffentlichung rückgängig machen]**, um zu bestätigen, dass die Veröffentlichung der Assets zum angegebenen Datum rückgängig gemacht werden soll.

Verstehen Sie die folgenden Einschränkungen und Tipps zum Veröffentlichen oder Rückgängigmachen der Veröffentlichung von Assets oder Ordnern:

* Die Option [!UICONTROL Veröffentlichung verwalten] steht nur für Benutzerkonten mit Replizierungsberechtigungen zur Verfügung.
* Wenn Sie die Veröffentlichung eines komplexen Assets rückgängig machen, machen Sie die Veröffentlichung nur des Assets rückgängig. Vermeiden Sie es, die Veröffentlichung der Verweise rückgängig zu machen, da diese möglicherweise von anderen veröffentlichten Assets referenziert werden.
* Leere Ordner werden nicht veröffentlicht.
* Wenn Sie ein Asset veröffentlichen, das momentan verarbeitet wird, wird nur der ursprüngliche Inhalt veröffentlicht. Die Ausgabedarstellungen fehlen. Warten Sie entweder, bis die Verarbeitung abgeschlossen ist, und veröffentlichen Sie das Asset erst dann, oder veröffentlichen Sie es erneut, wenn die Verarbeitung abgeschlossen ist.

## Eine geschlossene Benutzergruppe {#closed-user-group} erstellen

Ein CUG (Closed User Group) wird verwendet, um den Zugriff auf bestimmte Asset-Ordner zu beschränken, die über AEM veröffentlicht wurden. Wenn Sie eine CUG für einen Ordner erstellen, wird der Zugriff auf diesen Ordner (einschließlich Ordner-Assets und Unterordnern) auf zugewiesene Mitglieder und Gruppen beschränkt. Um auf einen Ordner zuzugreifen, müssen Benutzer mit ihren Sicherheitsanmeldedaten angemeldet sein.

CUG bietet eine zusätzliche Möglichkeit, den Zugriff auf Ihre Assets zu beschränken. Sie können auch eine Anmeldeseite für den Ordner konfigurieren.

**So erstellen Sie eine geschlossene Benutzergruppe**:

1. Wählen Sie in der Benutzeroberfläche &quot;Assets&quot;einen Ordner aus und tippen Sie auf das Symbol **[!UICONTROL Eigenschaften]** in der Symbolleiste, um die Eigenschaftsseite anzuzeigen.
1. Fügen Sie auf der Registerkarte **[!UICONTROL Berechtigungen]** unter **[!UICONTROL Geschlossene Benutzergruppe]** Mitglieder oder Gruppen hinzu.

   ![add_user](assets/add_user.png)

1. Um einen Anmeldebildschirm anzuzeigen, wenn Benutzer auf den Ordner zugreifen, wählen Sie die Option **[!UICONTROL Aktivieren]** aus. Wählen Sie anschließend den Pfad zur Anmeldeseite in AEM aus und speichern Sie die Änderungen.

   ![login_page](assets/login_page.png)

   Wenn Sie den Pfad zur Anmeldeseite nicht angeben, zeigt AEM die standardmäßige Anmeldeseite in der Veröffentlichungsinstanz an.

1. Veröffentlichen Sie den Ordner und versuchen Sie, über die Veröffentlichungsinstanz darauf zuzugreifen. Es wird ein Anmeldebildschirm angezeigt.
1. Wenn Sie Mitglied der CUG sind, geben Sie Ihre Anmeldedaten ein. Nachdem Sie von AEM authentifiziert wurden, wird der Ordner angezeigt.

## Suchen von Assets  {#searching-assets}

Die grundlegende Suche wird im Abschnitt über das [Suchen und Filtern](/help/sites-authoring/search.md#search-and-filter) detailliert beschrieben. Verwenden Sie das Bedienfeld **[!UICONTROL Suche]**, um nach Assets, Tags und Metadaten zu suchen. Mithilfe des Platzhaltersternchens können Sie nach Teilen einer Zeichenfolge suchen. Darüber hinaus können Sie das Bedienfeld **[!UICONTROL Suche]** mithilfe von [Suchfacetten](search-facets.md) anpassen.

![Filters_panel](assets/filters_panel.png)

Bei kürzlich hochgeladenen Assets stehen die Metadaten (einschließlich Titel, Tags usw.) nicht sofort in der Liste der Vorschläge zur Verfügung, die beim Eingeben in das Feld &quot;Omniture Search&quot;angezeigt werden.

Das liegt daran, dass AEM Assets erst nach dem Ablauf eines Timeout-Zeitraums (standardmäßig 1 Stunde) im Hintergrund einen Index der Metadaten für alle neu hochgeladenen/aktualisierten Assets erstellt und sie der Liste der Vorschläge hinzufügt.

## Schnellaktionen {#quick-actions} verwenden

Schnellaktion-Symbole sind jeweils nur für ein Asset verfügbar. Führen Sie je nach Gerät folgende Aktionen durch, um die Symbole der Schnellaktionen anzuzeigen:

* Touch-Geräte: Tippen und halten. Mit einem Touch-Gerät, wie z. B. einem iPad, können Sie länger auf ein Asset tippen, damit die Schnellaktionen angezeigt werden.
* Nicht-Touch-Geräte: Mit Mauszeiger darüberfahren. Auf einem Desktop-Gerät wird beispielsweise eine Schnellzugriffsleiste angezeigt, wenn Sie mit dem Mauszeiger über die Miniaturansicht des Assets fahren.

### Navigieren Sie zu Assets {#navigating-and-selecting-assets} und wählen Sie sie aus.

Mit dem Symbol **[!UICONTROL Auswählen]** können Sie Assets mit einer der verfügbaren Ansichten (Liste, ) Ansicht, durch sie navigieren und auswählen. **[!UICONTROL Auswahl]** wird als Schnellaktion in der Ansicht angezeigt.

![select_quick_action](assets/select_quick_action.png)

In der Ansicht &quot;Liste&quot;wird **[!UICONTROL Select]** angezeigt, wenn Sie den Mauszeiger über die Miniaturansicht vor den Namen der Assets/Ordner in der Liste bewegen.

![select_quick_in_listview](assets/select_quick_in_listview.png)

Ähnlich wie bei der Ansicht &quot;Liste&quot;wird **[!UICONTROL Select]** angezeigt, wenn Sie den Mauszeiger über die Miniaturansicht bewegen, bevor die Assets oder Ordner in der Ansicht der Spalte benannt werden.

![select_quick_in_columnView](assets/select_quick_in_columnview.png)

Weitere Informationen finden Sie unter [Anzeigen und Auswählen Ihrer Ressourcen](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).

## Bearbeiten von Bildern {#editing-images}

Mit den Bearbeitungswerkzeugen in der Oberfläche von AEM Assets können Sie kleine Bearbeitungsaktionen in Bild-Assets durchführen. Sie können Bilder beschneiden, drehen, spiegeln und auf andere Arten bearbeiten. Sie können auch Imagemaps zu den Assets hinzufügen.

Die Bildbearbeitung wird für Dateien mit den folgenden Formaten unterstützt:

* BMP
* GIF
* PNG
* JPEG

Für einige Komponenten stehen im Modus **[!UICONTROL Vollbild]** zusätzliche Optionen zur Verfügung.

Um eine TXT-Datei zu bearbeiten, legen Sie **[!UICONTROL Day CQ Link Externalizer]** in Configuration Manager fest.

Sie können auch Imagemaps mit dem Bild-Editor hinzufügen. Einzelheiten dazu finden Sie in [Hinzufügen von Imagemaps](image-maps.md).

**So bearbeiten Sie Bilder**:

1. Führen Sie einen der folgenden Schritte aus, um ein Element im Bearbeitungsmodus zu öffnen:

   * Wählen Sie das Asset aus und klicken Sie dann in der Symbolleiste auf das Symbol **[!UICONTROL Bearbeiten]**.
   * Tippen Sie auf die Option **[!UICONTROL Bearbeiten]**, die auf einem Asset in der Ansicht angezeigt wird.
   * Tippen Sie auf der Asset-Seite in der Symbolleiste auf das Symbol **[!UICONTROL Bearbeiten]**.

   ![edit_icon](assets/edit_icon.png)

1. Um das Bild zu beschneiden, tippen Sie auf **[!UICONTROL Beschneiden]**.

   ![chlimage_1-22](assets/chlimage_1-22.png)

1. Wählen Sie die gewünschte Option aus der Liste aus. Der Zuschneidebereich wird auf dem Bild je nach gewählter Option angezeigt. Mit der Option **[!UICONTROL Freihand]** können Sie das Bild ohne Einschränkungen des Seitenverhältnisses zuschneiden.

   ![chlimage_1-23](assets/chlimage_1-23.png)

1. Wählen Sie den Bereich aus, der beschnitten werden soll, und passen Sie die Größe oder Position des Bereichs auf dem Bild an.
1. Verwenden Sie die Option **[!UICONTROL Fertig stellen]** in der oberen rechten Ecke, um das Bild zu beschneiden. Durch Tippen auf **[!UICONTROL Fertig stellen]** wird auch die Wiederherstellung von Darstellungen Trigger.

   ![chlimage_1-24](assets/chlimage_1-24.png)

1. Verwenden Sie die Symbole **[!UICONTROL Rückgängig]** und **[!UICONTROL Wiederholen]** oben rechts, um zum nicht zugeschnittenen Bild zurückzukehren oder das zugeschnittene Bild beizubehalten.

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. Tippen Sie auf das entsprechende Symbol **[!UICONTROL Drehen]**, um das Bild im Uhrzeigersinn oder gegen den Uhrzeigersinn zu drehen.

   ![chlimage_1-26](assets/chlimage_1-26.png)

1. Tippen Sie auf das entsprechende Symbol **[!UICONTROL Spiegeln]**, um das Bild horizontal oder vertikal zu spiegeln.

   ![chlimage_1-27](assets/chlimage_1-27.png)

1. Tippen Sie auf das Symbol **[!UICONTROL Fertigstellen]**, um die Änderungen zu speichern.

   ![chlimage_1-28](assets/chlimage_1-28.png)

## Verwenden Sie die Zeitleiste {#timeline}

Mit der Zeitleiste **[!UICONTROL können Sie verschiedene Ereignis für ein bestimmtes Element, z. B. aktive Workflows für ein Asset, Kommentare, Anmerkungen, Aktivitäten und Versionen, Ansicht werden.]**

In der [Konsole für Sammlungen](managing-collections-touch-ui.md#navigating-the-collections-console) bietet die Liste **[!UICONTROL Alle anzeigen]** Optionen, um nur Kommentare und Workflows anzuzeigen. Darüber hinaus wird die Zeitleiste nur für Sammlungen auf der höchsten Ebene angezeigt, die in der Konsole aufgelistet sind. Sie wird nicht angezeigt, wenn Sie in einer der Sammlungen navigieren.

**** Zeitleiste enthält mehrere  [Optionen, die spezifisch für Inhaltsfragmente](content-fragments-managing.md#timeline-for-content-fragments) sind. Diese Funktion erfordert  [AEM 6.4 Service Pack 2 (6.4.2.0)](/help/release-notes/sp-release-notes.md)  oder höher.

**So verwenden Sie die Zeitschiene**:

1. Öffnen Sie die Asset-Seite für ein Asset oder wählen Sie es in der Assets-Benutzeroberfläche aus.
1. Tippen Sie auf das Symbol **[!UICONTROL Globale Navigation]** und wählen Sie **[Zeitschiene]** aus der Liste.

   ![Zeitleiste](assets/timeline.png)

1. Verwenden Sie in der angezeigten Liste die Liste **[!UICONTROL Alle anzeigen]**, um die Ergebnisse anhand der Kommentare, Versionen, Workflows und Aktivitäten zu filtern.

   ![timeline_options](assets/timeline_options.png)

## Anmerkungen hinzufügen {#annotating}

Anmerkungen sind Kommentare oder erläuternde Hinweise, die Bildern oder Videos hinzugefügt werden. Anmerkungen bieten Marketern die Möglichkeit, zusammenzuarbeiten und Feedback zu Assets bereitzustellen.

Videoanmerkungen werden nur bei Browsern mit HTML5-kompatiblen Videoformaten unterstützt. Von AEM Assets unterstützte Videoformate sind vom jeweiligen Browser abhängig.

Bei Inhaltsfragmenten werden [Anmerkungen im Editor](content-fragments-variations.md#annotating-a-content-fragment) erstellt. Diese Funktion erfordert [AEM 6.4 Service Pack 2 (6.4.2.0)](/help/release-notes/sp-release-notes.md) oder höher.

Sie können mehrere Anmerkungen hinzufügen, bevor Sie diese speichern.

Sie können Video-Assets Anmerkungen hinzufügen. Während Videos mit Anmerkungen versehen werden, wird der Player angehalten, damit Sie einem Frame eine Anmerkung hinzufügen können. Details finden Sie unter [Verwalten von Video-Assets](managing-video-assets.md).

Sie können auch Anmerkungen zu einer Sammlung hinzufügen. Wenn eine Sammlung jedoch untergeordnete Sammlungen enthält, können Sie der übergeordneten Sammlung nur Anmerkungen oder Kommentare hinzufügen. Die Option **[!UICONTROL Anmerken]** ist für untergeordnete Sammlungen nicht verfügbar.

**Hinzufügen von Anmerkungen**:

1. Navigieren Sie zum Speicherort des Assets, dem Sie Anmerkungen hinzufügen möchten.
1. Tippen Sie auf das Symbol **[!UICONTROL Annotate]** aus einem der folgenden Elemente:

   * [Schnellaktionen](managing-assets-touch-ui.md#quick-actions)
   * In der Symbolleiste, nachdem Sie das Asset ausgewählt haben  oder zur Asset-Seite navigiert sind

   ![chlimage_1-29](assets/chlimage_1-29.png)

1. Fügen Sie im Feld **[!UICONTROL Kommentar]** am unteren Rand der Zeitleiste einen Kommentar hinzu. Alternativ können Sie einen Bildbereich markieren und im Dialogfeld **[!UICONTROL Hinzufügen Anmerkung]** eine Anmerkung hinzufügen.

   ![chlimage_1-30](assets/chlimage_1-30.png)

1. Um einen Benutzer über eine Anmerkung zu benachrichtigen, geben Sie die E-Mail-Adresse des Benutzers an und fügen Sie den Kommentar hinzu. Um Aaron McDonald beispielsweise über eine Anmerkung zu benachrichtigen, geben Sie @aa ein. Vorschläge für alle übereinstimmenden Benutzer werden in einer Liste angezeigt. Wählen Sie Aarons E-Mail-Adresse aus der Liste, um ihn mit dem Kommentar zu versehen. Sie können auch weitere Benutzer innerhalb, vor oder nach der Anmerkung taggen.

   >[!NOTE]
   >
   >Für einen Benutzer ohne Administratorberechtigung sind Vorschläge nur dann sichtbar, wenn er über eine Leseberechtigung in `/home` in CRXDE verfügt.

   ![chlimage_1-31](assets/chlimage_1-31.png)

1. Nachdem Sie die Anmerkung hinzugefügt haben, tippen Sie auf **[!UICONTROL Hinzufügen]**, um sie zu speichern. Eine Benachrichtigung über die Anmerkung wird an Aaron gesendet.

   ![chlimage_1-32](assets/chlimage_1-32.png)

1. Tippen Sie auf **[!UICONTROL Schließen]**, um den Modus **[!UICONTROL Anmerkung]** zu verlassen.
1. Um die Benachrichtigung Ansicht, melden Sie sich mit den Anmeldedaten von Aaron MacDonald bei AEM Assets an und tippen Sie auf das Symbol **[!UICONTROL Benachrichtigungen]**, um die Benachrichtigung Ansicht.

1. Um eine andere Farbe auszuwählen, damit Sie zwischen Benutzern unterscheiden können, tippen Sie auf das Symbol **[!UICONTROL Profil]** und dann auf **[!UICONTROL Meine Voreinstellungen]**.

   ![chlimage_1-33](assets/chlimage_1-33.png)

1. Geben Sie die gewünschte Farbe in das Feld **[!UICONTROL Anmerkungsfarbe]** ein und tippen Sie dann auf **[!UICONTROL Akzeptieren]**.

   ![chlimage_1-34](assets/chlimage_1-34.png)

### Anzeigen gespeicherter Anmerkungen {#viewing-saved-annotations}

1. Um die gespeicherten Anmerkungen zu einem Asset anzuzeigen, navigieren Sie zum Speicherort des Assets und öffnen Sie die Asset-Seite für dieses Asset.

1. Tippen Sie auf das Symbol **[!UICONTROL Globale Navigation]** und tippen Sie in der Liste auf **[!UICONTROL Zeitschiene]**.

   ![chlimage_1-35](assets/chlimage_1-35.png)

1. Wählen Sie in der Liste **[!UICONTROL Alle anzeigen]** in der Zeitleiste **[!UICONTROL Kommentare]** aus, um die Ergebnisse anhand von Anmerkungen zu filtern.

   ![chlimage_1-36](assets/chlimage_1-36.png)

1. Tippen Sie auf einen Kommentar im Bereich **[!UICONTROL Zeitschiene]**, um die entsprechende Anmerkung auf dem Bild Ansicht.

   ![chlimage_1-37](assets/chlimage_1-37.png)

1. Tippen Sie auf **[!UICONTROL Löschen]**, um einen bestimmten Kommentar zu entfernen.

### Drucken von Anmerkungen {#printing-annotations}

Wenn ein Asset Anmerkungen aufweist oder einem Prüfungs-Workflow unterzogen wurde, können Sie das Asset einschließlich der Anmerkungen und des Prüfungsstatus für die Offline-Prüfung als PDF-Datei drucken.

Sie können auch nur die Anmerkungen oder nur den Prüfungsstatus drucken.

Längere Anmerkungen werden in der PDF-Datei möglicherweise nicht richtig gerendert. Für optimales Rendering wird empfohlen, Anmerkungen auf 50 Wörter zu begrenzen.

Um die Anmerkungen und den Überprüfungsstatus zu drucken, tippen Sie auf das Symbol **[!UICONTROL Drucken]** und befolgen Sie die Anweisungen im Assistenten. Das Symbol **[!UICONTROL Drucken]** erscheint nur dann in der Symbolleiste, wenn dem Asset mindestens eine Anmerkung oder ein Prüfungsstatus zugewiesen ist.

1. Öffnen Sie von der Assets-Benutzeroberfläche aus die Vorschauseite für ein Asset.
1. Führen Sie einen der folgenden Schritte aus:

   * Um alle Anmerkungen und den Überprüfungsstatus zu drucken, fahren Sie mit Schritt 4 fort.
   * Um bestimmte Anmerkungen und den Überprüfungsstatus zu drucken, öffnen Sie die [Zeitschiene](managing-assets-touch-ui.md#timeline) und fahren Sie dann mit Schritt 3 fort.

1. Um bestimmte Anmerkungen zu drucken, wählen Sie die Anmerkungen in der **[!UICONTROL Zeitleiste]** aus.

   ![chlimage_1-38](assets/chlimage_1-38.png)

   Um nur den Überprüfungsstatus zu drucken, wählen Sie ihn in der **[!UICONTROL Zeitleiste]** aus.

   ![chlimage_1-39](assets/chlimage_1-39.png)

1. Tippen Sie in der Symbolleiste auf das Symbol **[!UICONTROL Drucken]**.

   ![chlimage_1-40](assets/chlimage_1-40.png)

1. Wählen Sie im Dialogfeld **[!UICONTROL Drucken]** die Position, an der die Anmerkungen oder der Überprüfungsstatus im PDF-Dokument angezeigt werden sollen. Wenn beispielsweise die Anmerkungen oder der Status oben rechts auf der Seite mit dem gedruckten Bild gedruckt werden sollen, verwenden Sie die Einstellung **[!UICONTROL Oben links]** (Standard).

   ![chlimage_1-41](assets/chlimage_1-41.png)

   Sie können je nach Position, an der die Anmerkungen oder der Status in der gedruckten PDF-Datei angezeigt werden sollen, andere Einstellungen auswählen. Wenn die Anmerkungen oder der Status auf einer Seite angezeigt werden sollen, die vom gedruckten Asset getrennt ist, wählen Sie **[!UICONTROL Nächste Seite]**.

1. Tippen Sie auf **[!UICONTROL Drucken]**. Je nach der in Schritt 2 gewählten Option zeigt die erstellte PDF-Datei die Anmerkungen oder den Status an der angegebenen Position an. Beispiel: Wenn Sie beide Anmerkungen und den Prüfungsstatus mithilfe der Einstellung **[!UICONTROL Oben links]** drucken, ähnelt die erstellte Ausgabe der hier dargestellten PDF-Datei.

   ![chlimage_1-42](assets/chlimage_1-42.png)

1. Laden Sie die PDF-Datei herunter oder drucken Sie sie mithilfe der Optionen in der rechten oberen Ecke.

   ![chlimage_1-43](assets/chlimage_1-43.png)

   >[!NOTE]
   >
   >Wenn das Asset Unter-Assets enthält, können Sie alle Unter-Assets zusammen mit ihren jeweiligen seitenweisen Anmerkungen drucken.

   Um das Erscheinungsbild der gerenderten PDF-Datei zu ändern, z. B. Schriftfarbe, -größe und -stil, Hintergrundfarbe der Kommentare und Status, öffnen Sie die **[!UICONTROL PDF-Konfiguration für Anmerkungen]** von **[!UICONTROL Configuration Manager]** und ändern Sie die gewünschten Optionen. Um beispielsweise die Anzeigefarbe des Status „Bestätigt“ zu ändern, modifizieren Sie im entsprechenden Feld den Farb-Code. Informationen zum Ändern der Schriftfarbe von Anmerkungen finden Sie unter [Anmerken](managing-assets-touch-ui.md#annotating).

   ![chlimage_1-44](assets/chlimage_1-44.png)

   Kehren Sie zu der gerenderten PDF-Datei zurück und aktualisieren Sie sie. Der aktualisierte PDF-Datei spiegelt die von Ihnen vorgenommenen Änderungen wider.

**So drucken Sie Anmerkungen in Fremdsprachen**: Wenn ein Asset Anmerkungen in Fremdsprachen (insbesondere in Nicht-lateinischen Sprachen) enthält, müssen Sie zunächst den CQ-DAM-Handler-Gibson Font Manager Service auf dem AEM Server konfigurieren, um diese Anmerkungen drucken zu können. Beim Konfigurieren des CQ-DAM-Handler-Gibson Font Manager Service geben Sie den Pfad an, über den auf die gewünschten Sprachen zugegriffen werden kann.

1. Öffnen Sie die Konfigurationsseite **[!UICONTROL CQ-DAM-Handler-Gibson Font Manager Service]** unter der URL [https://&lt;server>:&lt;port>/system/console/configMgr/com.day.cq.dam.handler.gibson.fontmanager.impl.FontManagerServiceImpl](http://localhost:4502/system/console/configMgr/com.day.cq.dam.handler.gibson.fontmanager.impl.FontManagerServiceImpl).
1. Um **[!UICONTROL CQ-DAM-Handler-Gibson Font Manager Service]** zu konfigurieren, führen Sie einen der folgenden Schritte aus:

   * Geben Sie in der Ordneroption **[!UICONTROL Systemschriftarten]** den vollständigen Pfad zum Schriftartenverzeichnis auf Ihrem System an. Wenn Sie z. B. Mac-Benutzer sind, können Sie den Pfad in der Ordneroption **[!UICONTROL Systemschriftarten]** als `/Library/Fonts` angeben. AEM ruft die Schriftarten aus diesem Verzeichnis ab.
   * Erstellen Sie im Ordner **crx-quickstart** ein Verzeichnis mit dem Namen **[!UICONTROL fonts]**. **[!UICONTROL CQ-DAM-Handler-Gibson Font Manager]** Services ruft die Schriftarten automatisch am Speicherort ab  `crx-quickstart/fonts`. Sie können diesen Standardpfad in der Ordneroption **[!UICONTROL Adobe Server Fonts]** überschreiben.
   * Erstellen Sie einen neuen Ordner für Schriftarten in Ihrem System und speichern Sie in diesem Ordner die gewünschten Schriftarten. Geben Sie dann den vollständigen Pfad zu diesem Ordner in der Ordneroption **[!UICONTROL Kundenschriftarten]** an.

1. Greifen Sie über die URL [https://&lt;server>:&lt;port>/system/console/configMgr/com.day.cq.dam.core.impl.annotation.pdf.AnnotationPdfConfig](http://localhost:4502/system/console/configMgr/com.day.cq.dam.core.impl.annotation.pdf.AnnotationPdfConfig) auf die Konfiguration **[!UICONTROL Annotation PDF]** zu.
1. Konfigurieren Sie die PDF-Datei **[!UICONTROL Anmerkung]** mit dem richtigen Satz der Schriftfamilie wie folgt:

   * Schließen Sie die Zeichenfolge `<font_family_name_of_custom_font, sans-serif>` in der Schriftartoption ein. Wenn Sie z. B. Anmerkungen in CJK (Chinesisch, Japanisch und Koreanisch) drucken möchten, schließen Sie die Zeichenfolge `Arial Unicode MS, Noto Sans, Noto Sans CJK JP, sans-serif` in die Schriftartoption ein. Wenn Sie Anmerkungen in Hindi drucken möchten, laden Sie die entsprechende Schriftart herunter. Anschließend konfigurieren Sie die Schriftart als Arial Unicode MS, Noto Sans, Noto Sans CJK JP, Noto Sans Devanagari, Sans-Serif.

1. Starten Sie die AEM-Instanz neu.

Das folgende Beispiel zeigt, wie Sie AEM zum Drucken von Anmerkungen in CJK (Chinesisch, Japanisch und Koreanisch) konfigurieren:

1. Laden Sie die Google Noto CJK-Schriftarten über die folgenden Links herunter und speichern Sie sie im Schriftartenverzeichnis, das in Font Manager Service konfiguriert ist.

   * Schriftart All In One Super CJK: [https://www.google.com/get/noto/help/cjk/](https://www.google.com/get/noto/help/cjk/)
   * Noto Sans (für europäische Sprachen): [https://www.google.com/get/noto/](https://www.google.com/get/noto/)
   * Noto-Schriftarten für eine Sprache Ihrer Wahl: [https://www.google.com/get/noto/](https://www.google.com/get/noto/)

1. Konfigurieren Sie die PDF-Datei, die Anmerkungen enthält, indem Sie den Schriftartparameter auf `Arial Unicode MS, Noto Sans, Noto Sans CJK JP, sans-serif` setzen. Diese Konfiguration ist standardmäßig verfügbar und funktioniert bei allen europäischen und CJK-Sprachen.
1. Wenn sich die Sprache Ihrer Wahl von den Sprachen unterscheidet, die in Schritt 2 erwähnt werden, fügen Sie der Standardschriftart einen entsprechenden (kommagetrennten) Eintrag hinzu.

## Erstellen der Asset-Version {#asset-versioning}

Bei der Versionierung wird eine Momentaufnahme von digitalen Assets zu einem bestimmten Zeitpunkt aufgezeichnet. Sie hilft Ihnen bei der späteren Wiederherstellung eines vorherigen Asset-Zustands. Wenn Sie etwa eine Änderung an einem Asset rückgängig machen wollen, stellen Sie die unbearbeitete Version des Assets wieder her.

In folgenden Szenarien werden Versionen erstellt:

* Sie ändern ein Bild in einer anderen Anwendung und laden es in AEM Assets hoch. Es wird eine Version des Bildes erstellt, damit das Original nicht überschrieben wird.
* Sie können die Metadaten eines Assets bearbeiten.
* Sie verwenden das AEM-Desktop-Programm, um ein vorhandenes Asset auszuchecken und Ihre Änderungen zu speichern. Bei jedem Speichern des Assets wird eine neue Version erstellt.

Sie können mithilfe eines Workflows die automatische Versionierung aktivieren. Wenn Sie eine Version für ein Asset erstellen, werden die Metadaten und Ausgabedarstellungen gemeinsam mit der Version gespeichert. Ausgabedarstellungen sind gerenderte Alternativen für dieselben Bilder, z. B. eine PNG-Ausgabedarstellung einer hochgeladenen JPEG-Datei.

Die Versionierungsfunktion bietet folgende Möglichkeiten:

* Erstellen einer Version eines Assets
* Anzeigen der aktuellen Version eines Assets
* Zurücksetzen des Assets auf eine frühere Version

**So erstellen Sie die Asset-Versionierung**:

1. Navigieren Sie zum Speicherort des Assets, für das Sie eine Version erstellen möchten, und klicken Sie darauf, um die Asset-Seite zu öffnen.

1. Klicken Sie auf das Symbol **[!UICONTROL Globale Navigation]** und wählen Sie **[!UICONTROL Zeitschiene]** aus dem Menü.

   ![timeline-1](assets/timeline-1.png)

1. Klicken Sie unten auf **[!UICONTROL Aktionen]**, um die verfügbaren Aktionen für das Asset Ansicht.

1. Klicken Sie auf **[!UICONTROL Als Version speichern]**, um eine Version für das Asset zu erstellen.

   ![chlimage_1-46](assets/chlimage_1-46.png)

1. Fügen Sie eine Beschriftung und Kommentare hinzu und klicken Sie auf **[!UICONTROL Erstellen]**, um eine Version zu erstellen. Alternativ können Sie auf **[!UICONTROL Abbrechen]** tippen, um den Vorgang zu beenden.

   ![chlimage_1-47](assets/chlimage_1-47.png)

1. Um die neue Version Ansicht, öffnen Sie die Liste **[!UICONTROL Alle anzeigen]** in der Zeitleiste auf der Seite mit den Asset-Details oder auf der [!DNL Assets]-Oberfläche und wählen Sie **[!UICONTROL Versionen]**.

   ![versions_option](assets/versions_option.png)

1. Wählen Sie eine bestimmte Version für das Asset aus, um sie in der Vorschau anzuzeigen, oder aktivieren Sie sie, damit sie in der Assets-Benutzeroberfläche angezeigt wird.

   ![select_version](assets/select_version.png)

   >[!NOTE]
   >
   >Sie können das Asset auch aus der Ansicht [Liste](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources) oder aus der Ansicht [Spalte](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources) auswählen.

1. Fügen Sie eine Beschriftung und Kommentare für die Version hinzu, um in der Assets-Benutzeroberfläche auf diese bestimmte Version zurückzusetzen.

   ![save_version](assets/save_version.png)

1. Klicken Sie zum Generieren einer Vorschau für die Vorschau auf **[!UICONTROL Version]**.
1. Um diese Version in der Assets-Benutzeroberfläche anzuzeigen, wählen Sie **[!UICONTROL Auf diese Version zurücksetzen]**.
1. Um zwischen zwei Versionen zu vergleichen, gehen Sie zur Asset-Seite und klicken Sie auf die Version, die Sie mit der aktuellen Version vergleichen möchten.

   ![Wählen Sie eine frühere Version des Assets aus, die mit der aktuellen Version verglichen werden soll](assets/select_version_tocompare.png)

1. Wählen Sie in der Zeitleiste die Version aus, die Sie vergleichen wollen, und ziehen Sie den Schieberegler nach links, um diese Version über die aktuelle Version zu setzen.

   ![compare_versions](assets/compare_versions.png)

### Beginn eines Workflows für ein Asset {#starting-a-workflow-on-an-asset}

Siehe [Einen Workflow auf ein AEM Asset anwenden](/help/assets/assets-workflow.md#apply-a-workflow-to-an-aem-asset).

## Sammlungen {#collections}

Bei einer Sammlung handelt es sich um eine sortierte Gruppe von Assets. Anhand von Sammlungen können Assets von mehreren Benutzern gemeinsam verwendet werden.

* Eine Sammlung kann Assets aus verschiedenen Speicherorten enthalten, da sie nur Verweise zu diesen Assets aufweisen. Jede Sammlung hält die referenzielle Integrität von Assets aufrecht.
* Sie können Sammlungen für mehrere Benutzer mit unterschiedlichen Berechtigungsstufen wie Bearbeiten, Anzeigen usw. freigeben.

Ein Benutzer kann über Zugriff auf mehrere Sammlungen verfügen. Sammlungen sind von den folgenden Typen, und zwar auf Grundlage, wie sie Assets sortieren:

* Eine Liste mit einer **statischen Referenz** aus Assets, Ordnern und anderen Sammlungen.

* Eine Sammlung, die ein **Suchkriterium** verwendet und Elemente basierend auf den Kriterien dynamisch füllt. Dies wird als **intelligente Sammlung** bezeichnet.

Weitere Informationen zur Sammlungsverwaltung finden Sie unter [Sammlungen verwalten](managing-collections-touch-ui.md).

>[!NOTE]
>
>Sie benötigen die entsprechenden Zugriffsrechte für Ihr Konto, um Assets zu erstellen oder zu bearbeiten.
