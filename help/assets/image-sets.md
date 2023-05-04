---
title: Bildsets
seo-title: Image Sets
description: Erfahren Sie, wie Sie mit Bildsets in Dynamic Media arbeiten.
seo-description: Learn how to work with image sets in dynamic media
uuid: 16008278-f59f-4fa8-90e9-19c78f132439
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: e00e7cc9-b777-4f9e-906d-824bcb2bbd41
exl-id: af3f95aa-a162-4212-a20a-68b5a0e72d6d
feature: Image Sets
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2182'
ht-degree: 68%

---

# Bildsets {#image-sets}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Über Bildsets erhalten Benutzer ein integriertes Anzeigeerlebnis, bei dem sie unterschiedliche Ansichten eines Elements durch Klicken auf eine Miniatur anzeigen können. Mit Bildsets können Sie alternative Ansichten eines Elements darstellen. Dabei enthält der Viewer Zoomtools, mit denen Bilder genauer betrachtet werden können.

Bildsets werden durch ein Banner mit dem Wort gekennzeichnet **[!UICONTROL IMAGESET]**. Darüber hinaus wird bei veröffentlichten Bildsets das Veröffentlichungsdatum (durch das **[!UICONTROL Welt]**-Symbol gekennzeichnet) zusammen mit dem Datum der letzten Änderung (durch das **[!UICONTROL Bleistift]**-Symbol gekennzeichnet) im Banner angezeigt.

![chlimage_1-339](assets/chlimage_1-339.png)

Innerhalb des Bildsets können Sie auch Muster erstellen, indem Sie ein Bildset erstellen und Miniaturansichten hinzufügen.

Diese Anwendung ist besonders nützlich, wenn Sie ein Element in einer anderen Farbe, einem anderen Muster oder einer anderen Oberfläche anzeigen möchten. Um ein Bildset mit Farbmustern zu erstellen, benötigen Sie ein Bild für alle Farben, Muster oder Endverarbeitungen, die den Benutzern dargestellt werden sollen. Sie benötigen außerdem ein Farb-, Muster- oder Finish-Muster für jede Farbe, jedes Muster oder jede Oberfläche.

Angenommen, Sie möchten Bilder von Begrenzungen mit unterschiedlichen Farbbildern präsentieren. die Rechnungen sind rot, grün und blau. In diesem Fall benötigen Sie drei Aufnahmen derselben Mütze. Man braucht einen Schuss mit einem roten, einen mit einem grünen und einen mit einem blauen Schein. Außerdem benötigen Sie ein rotes, grünes und blaues Farbmuster. Die Farbmuster dienen als Miniaturen, auf die Benutzer im Musterset-Viewer klicken, um die Kappe mit rotem, grünem oder blauem Schirm anzuzeigen.

>[!NOTE]
>
>Weitere Informationen zur Assets-Benutzeroberfläche finden Sie unter [Verwalten von Assets mit der Touch-Benutzeroberfläche](managing-assets-touch-ui.md).

Beim Erstellen eines Bildsets empfiehlt Adobe die folgenden Best Practices und erzwingt die folgenden Beschränkungen:

| Begrenzungstyp | Best Practice | Grenzwert |
| --- | --- | --- |
| Anzahl der doppelten Assets pro Satz | Keine Duplikate | 20 |
| Maximale Anzahl an Bildern pro Set | 5–10 Bilder pro Set | 1000 |

Siehe auch [Grenzwerte für Dynamic Media](/help/assets/limitations.md).

## Schnellstart: Bildsets {#quick-start-image-sets}

So schaffen Sie einen schnellen Einstieg:

1. [Laden Sie die Primärbilder für mehrere Ansichten hoch.](#uploading-assets-in-image-sets)

   Laden Sie zunächst die Bilder für die Bildsets hoch. Berücksichtigen Sie den Zoom bei der Auswahl von Bildern, da Benutzer Bilder im Bildset-Viewer einzoomen können. Achten Sie darauf, dass die längste Seite der Bilder mindestens 2.000 Pixel hat, um optimale Zoom-Details zu erzielen. Mit Dynamic Media können Bilder mit einer Auflösung von jeweils bis zu 25 Megapixel gerendert werden. Sie können beispielsweise ein Bild mit 5000 x 5000 Megapixel oder eine beliebige andere Größenkombination mit bis zu 25 Megapixel verwenden.

   AEM Assets unterstützt viele Bilddateiformate. Es werden jedoch verlustfreie TIFF-, PNG- und EPS-Bilder empfohlen.

1. [Erstellen Sie Bildsets.](#creating-image-sets)

   In Bildsets klicken Benutzer im Bildset-Viewer auf Miniaturen.

   Um ein Bildset in Assets zu erstellen, tippen Sie auf **[!UICONTROL Erstellen > Bildsets]**. Fügen Sie dann Bilder hinzu und tippen Sie auf **[!UICONTROL Speichern]**.

   Sie können Bildsets auch automatisch über [Stapelsatzvorgaben](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets) erstellen.

   **Wichtig** — Stapelsätze werden vom IPS (Image Production System) bei der Asset-Erfassung erstellt und sind nur im Dynamic Media-Scene7-Modus verfügbar.

   Siehe [Vorbereiten von Bildset-Assets auf das Hochladen und Hochladen von Dateien](#uploading-assets-in-image-sets).

   Siehe [Arbeiten mit Selektoren](working-with-selectors.md).

1. Fügen Sie nach Bedarf [Bildset-Viewer-Vorgaben](managing-viewer-presets.md) hinzu.

   Administratoren können Bilder erstellen oder ändern **[!UICONTROL Festlegen von Viewer-Vorgaben]**. Wählen Sie zum Anzeigen Ihres Bildsets mit einer Viewer-Vorgabe das Bildset und links in der Leiste in der Dropdown-Liste die Option **[!UICONTROL Viewer]**.

   Um Viewer-Vorgaben zu erstellen oder zu bearbeiten, wählen Sie **[!UICONTROL Tools > Assets > Viewer-Vorgaben]**.

1. (Optional) [Anzeigen von Bildsets](image-sets.md#viewing-image-sets), die mit Stapelsatzvorgaben erstellt wurden.
1. [Zeigen Sie Bildsets in einer Vorschau an.](previewing-assets.md)

   Wählen Sie das Bildset aus, um dessen Vorschau anzuzeigen. Tippen Sie auf die Miniaturansichtssymbole, um das Bildset im ausgewählten Viewer zu untersuchen. Sie können verschiedene Viewer aus dem Menü **[!UICONTROL Viewer]** wählen, das Sie links in der Leiste über die Dropdown-Liste aufrufen können.

1. [Veröffentlichen Sie Bildsets.](publishing-dynamicmedia-assets.md)

   Beim Veröffentlichen eines Bildsets wird die URL- und Einbettungszeichenfolge aktiviert. Darüber hinaus müssen Sie alle [benutzerdefinierten Viewer-Vorgaben veröffentlichen](managing-viewer-presets.md), die Sie erstellt haben. Standardmäßig vorhandene Viewer-Vorgaben sind bereits veröffentlicht.

1. [Verknüpfen Sie URLs mit einer Web-Anwendung](linking-urls-to-yourwebapplication.md) oder [betten Sie den Video- oder Bild-Viewer ein](embed-code.md).

   AEM Assets erstellt URL-Aufrufe für Bildsets und aktiviert diese, nachdem Sie die Bildsets veröffentlicht haben. Sie können diese URLs während der Asset-Vorschau kopieren. Alternativ können Sie sie auf Ihrer Website einbetten.

   Wählen Sie das Bildset und dann im Dropdown-Menü links die Option **[!UICONTROL Viewer]**.

   Siehe [Verknüpfen von Bildsets mit Web-Seiten](linking-urls-to-yourwebapplication.md) und [Einbetten des Video- oder Bild-Viewers](embed-code.md).

Informationen zum Bearbeiten von Bildsets finden Sie unter [Bearbeiten von Bildsets](#editing-image-sets). Darüber hinaus können Sie [Eigenschaften von Bildsets](managing-assets-touch-ui.md#editing-properties) anzeigen und bearbeiten.

Wenn Sie beim Erstellen von Sets Probleme haben, lesen Sie den Abschnitt zu Bildern und Sets unter [Problembehandlung in Dynamic Media – Scene7-Modus](troubleshoot-dms7.md#images-and-sets).

## Hochladen von Assets in Bildsets {#uploading-assets-in-image-sets}

Laden Sie zunächst die Bilder für die Bildsets hoch. Berücksichtigen Sie den Zoom bei der Auswahl von Bildern, da Benutzer Bilder im Bildset-Viewer einzoomen können. Achten Sie darauf, dass die längste Seite der Bilder mindestens 2.000 Pixel hat. Bildsets unterstützen zahlreiche Bilddateiformate, empfohlen werden aber verlustfreie TIFF-, PNG- und EPS-Bilder.

Sie laden Bilder für Bild­Sets genauso wie [alle anderen Assets in Assets](managing-assets-touch-ui.md#uploading-assets) hoch.

### Vorbereiten von Bildset-Assets auf das Hochladen {#preparing-image-set-assets-for-upload}

Bevor Sie Bildsets erstellen, achten Sie darauf, dass die Bilder die richtige Größe und das richtige Format aufweisen.

Um ein Bildset mit mehreren Ansichten zu erstellen, benötigen Sie Bilder, die einen Artikel aus unterschiedlichen Blickwinkeln zeigen oder unterschiedliche Aspekte desselben Artikels darstellen. Das Ziel besteht darin, die wichtigen Funktionen eines Elements hervorzuheben, damit die Betrachter ein vollständiges Bild davon erhalten, wie es aussieht oder funktioniert.

Stellen Sie sicher, dass die Bilder in Bildsets mindestens 2.000 Pixel in der größten Abmessung aufweisen, da Benutzer sie einzoomen können. Assets unterstützt zahlreiche Bilddateiformate, empfohlen werden aber verlustfreie TIFF-, PNG- und EPS-Bilder.

>[!NOTE]
>
>Wenn Sie außerdem Miniaturansichten verwenden, um Produktmuster anzugeben, müssen Sie Folgendes tun:
>
>Sie benötigen Vignetten oder andere Aufnahmen desselben Bildes, die es in verschiedenen Farben, Mustern oder Endverarbeitungen zeigen. Außerdem benötigen Sie Miniaturdateien, die den verschiedenen Farben, Mustern oder Endverarbeitungen entsprechen. Um beispielsweise Miniaturen in einem Bildset zu präsentieren, die eine Jacke in Schwarz, Braun und Grün anzeigen, benötigen Sie:
>
>* Ein schwarzer, brauner und grüner Schuss derselben Jacke.
>* eine schwarze, braune und grüne Miniatur
>


## Erstellen von Bildsets {#creating-image-sets}

Sie können Bildsets über die Benutzeroberfläche oder die API erstellen. In diesem Abschnitt wird beschrieben, wie Sie Bildsets in der Benutzeroberfläche erstellen.

>[!NOTE]
>
>Sie können Bildsets auch automatisch über [Stapelsatzvorgaben](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets) erstellen.

**Wichtig**: Stapelsätze werden vom IPS (Image Production System) im Rahmen der Asset-Aufnahme erstellt und sind nur im Scene7-Modus von Dynamic Media verfügbar.

Assets, die Sie Ihrem Set hinzufügen, werden automatisch in alphanumerischer Reihenfolge hinzugefügt. Sie können die Assets manuell neu anordnen oder sortieren, nachdem sie hinzugefügt wurden.

>[!NOTE]
>
>Bildsets werden für Assets mit `,` (Komma) im Dateinamen.

Beim Erstellen eines Bildsets empfiehlt Adobe die folgenden Best Practices und erzwingt die folgenden Beschränkungen:

| Begrenzungstyp | Best Practice | Grenzwert |
| --- | --- | --- |
| Anzahl der doppelten Assets pro Satz | Keine Duplikate | 20 |
| Maximale Anzahl an Bildern pro Set | 5–10 Bilder pro Set | 1000 |

Siehe auch [Dynamic Media-Beschränkungen](/help/assets/limitations.md).

**So erstellen Sie ein Bildset**:

1. In **Assets**, navigieren Sie zu der Stelle, an der Sie ein Bildset erstellen möchten, tippen Sie auf **[!UICONTROL Erstellen]** und wählen Sie **[!UICONTROL Bildset]**. Sie können das Set auch in einem Ordner erstellen, der die gewünschten Assets enthält.

   ![chlimage_1-340](assets/chlimage_1-340.png)

1. Auf der Seite &quot;Bildset-Editor&quot;im **[!UICONTROL Titel]** ein, geben Sie einen Namen für das Bildset ein. Der Name wird im Banner über dem Bildset angezeigt. Geben Sie optional eine Beschreibung ein.

   ![chlimage_1-341](assets/chlimage_1-341.png)

   >[!NOTE]
   >
   >Beim Erstellen des Bildsets können Sie die Miniaturansicht des Bildsets ändern oder zulassen, dass AEM die Miniaturansicht anhand der Assets im Bildset automatisch auswählt. Um eine Miniaturansicht auszuwählen, tippen Sie auf **[!UICONTROL Miniaturansicht ändern]** und wählen Sie ein beliebiges Bild aus (Sie können auch zu anderen Ordnern navigieren, um nach Bildern zu suchen). Wenn Sie eine Miniaturansicht ausgewählt haben und dann festlegen möchten, dass AEM eine aus dem Bildset generiert, **[!UICONTROL wählen Sie  Zu automatischer Miniatur wechseln]**.

1. Führen Sie eine der folgenden Aktionen aus:

   * In der linken oberen Ecke des **[!UICONTROL Bildset-Editor]** Seite, tippen Sie auf **[!UICONTROL Asset hinzufügen]**.
   * In der Mitte des **[!UICONTROL Bildset-Editor]** Seite, tippen Sie auf **[!UICONTROL Tippen, um den Asset-Selektor zu öffnen]**.

   Tippen Sie, um Assets auszuwählen, die Sie in das Bildset aufnehmen möchten. Die ausgewählten Assets sind mit einem Häkchen versehen. Wenn Sie fertig sind, tippen Sie oben rechts auf der Seite auf **[!UICONTROL Auswählen]**.

   Mit dem Asset-Selektor können Sie nach Assets suchen, indem Sie ein Keyword eingeben und auf **[!UICONTROL Eingabe]** tippen. Sie können auch Filter anwenden, um Ihre Suchergebnisse genauer abzustimmen. Sie können nach Pfad, Sammlung, Dateityp und Tag filtern. Wählen Sie den Filter und tippen Sie in der Symbolleiste auf das Symbol **[!UICONTROL Filter]**. Ändern Sie die Ansicht, indem Sie auf die **[!UICONTROL Ansicht]** Symbol und Auswahl **[!UICONTROL Spaltenansicht]**, **[!UICONTROL Kartenansicht]** oder **[!UICONTROL Listenansicht]**.

   Siehe [Arbeiten mit Selektoren](working-with-selectors.md).

   ![chlimage_1-342](assets/chlimage_1-342.png)

1. Assets, die Sie Ihrem Set hinzufügen, werden automatisch in alphanumerischer Reihenfolge hinzugefügt. Sie können Assets nach dem Hinzufügen manuell neu anordnen oder sortieren.

   Ziehen Sie bei Bedarf die **[!UICONTROL Neu anordnen]** rechts neben dem Dateinamen des Assets, um Bilder in der Setliste nach oben oder unten anzuordnen.

   ![spin_set_assets](assets/spin_set_assets.png)

   Wenn Sie eine Miniaturansicht oder ein Muster ändern möchten, tippen Sie auf die **[!UICONTROL Miniatur]** neben dem Bild und navigieren Sie zur gewünschten Miniaturansicht bzw. zum gewünschten Muster. Wenn Sie alle Bilder ausgewählt haben, tippen Sie auf **[!UICONTROL Speichern]**.

1. (Optional) Führen Sie einen der folgenden Schritte aus:

   * Um ein Bild zu löschen, wählen Sie das Bild aus und tippen Sie auf **[!UICONTROL Asset löschen]**.
   * Wenn Sie eine Vorgabe anwenden möchten, tippen Sie oben rechts auf **[!UICONTROL Voreingestellt]**. Wählen Sie anschließend eine Vorgabe aus, um sie auf alle Elemente gleichzeitig anzuwenden.

1. Tippen Sie auf **[!UICONTROL Speichern]**. Das neu erstellte Bildset wird in dem Ordner angezeigt, in dem es erstellt wurde.

## Anzeigen von Bildsets {#viewing-image-sets}

Sie können Bildsets entweder in der Benutzeroberfläche oder automatisch über [Stapelsatzvorgaben](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets) erstellen.

**Wichtig** — Stapelsätze werden vom IPS erstellt. [Image Production System] als Teil der Asset-Erfassung und nur im Modus Dynamic Media - Scene7 verfügbar sind.)

Mit Stapelsatzvorgaben erstellte Sets werden jedoch *nicht* in der Benutzeroberfläche angezeigt. Sie können diese Sets auf drei verschiedene Arten anzeigen. (Diese Methoden sind auch verfügbar, wenn Sie die Bildsets in der Benutzeroberfläche erstellt haben.)

* Beim Öffnen der Eigenschaften eines einzelnen Assets. Die Eigenschaften zeigen an, zu welchen Sets das ausgewählte Asset gehört (unter **[!UICONTROL Mitglied von Sets]**). Tippen Sie auf den Namen des Sets, um den gesamten Satz anzuzeigen.

   ![chlimage_1-343](assets/chlimage_1-343.png)

* Von einem zugehörigen Bild eines beliebigen Sets. Wählen Sie das Menü **[!UICONTROL Sets]** aus, um die Sets anzuzeigen, denen das Asset angehört.

   ![chlimage_1-344](assets/chlimage_1-344.png)

* Über die Suche können Sie **[!UICONTROL Filter]**, dann erweitern **[!UICONTROL Dynamic Media]** und wählen Sie **[!UICONTROL Sets]**.

   Die Suche gibt als Ergebnis Sets zurück, die in der Benutzeroberfläche manuell oder mit Stapelsatzvorgaben automatisch erstellt wurden. Bei automatisierten Sets wird die Suchabfrage mithilfe der Suchkriterien &quot;Beginnt mit&quot;durchgeführt, die sich von AEM Suche unterscheidet, die auf der Verwendung von Suchkriterien &quot;Enthält&quot;basiert. Automatisierte Sets können nur durchsucht werden, wenn der Filter auf **[!UICONTROL Sets]** eingestellt ist.

   ![chlimage_1-345](assets/chlimage_1-345.png)

>[!NOTE]
>
>Sets können über die Benutzeroberfläche angezeigt werden, wie unter [Bearbeiten von Bildsets](#editing-image-sets) beschrieben.

## Bearbeiten von Bildsets {#editing-image-sets}

Sie können mehrere Bearbeitungsaufgaben für Bildsets ausführen, z. B. die folgenden:

* Fügen Sie dem Bildset Bilder hinzu.
* Ordnen Sie Bilder im Bildset neu an.
* Löschen Sie Assets im Bildset.
* Wenden Sie Viewer-Vorgaben an.
* Löschen Sie das Bildset.

**So bearbeiten Sie Bildsets**:

1. Führen Sie einen der folgenden Schritte aus:

   * Zeigen Sie mit der Maus auf ein Bildset-Asset und tippen Sie auf **[!UICONTROL Bearbeiten]** (Bleistiftsymbol).
   * Zeigen Sie mit der Maus auf ein Bildset-Asset und tippen Sie auf **[!UICONTROL Auswählen]** (Häkchensymbol) und dann auf **[!UICONTROL Bearbeiten]** in der Symbolleiste.
   * Tippen Sie auf ein Bildset-Asset und dann auf **[!UICONTROL Bearbeiten]** (Bleistiftsymbol) in der Symbolleiste.

1. Führen Sie eine der folgenden Aktionen aus, um die Bilder im Bildset zu bearbeiten:

   * Um Assets neu anzuordnen, ziehen Sie ein Bild an eine neue Position (wählen Sie das Symbol für die Neuanordnung aus, um Elemente zu verschieben).
   * Um Elemente in auf- oder absteigender Reihenfolge zu sortieren, tippen Sie auf die Spaltenüberschrift.
   * Um ein Asset hinzuzufügen oder ein vorhandenes Asset zu aktualisieren, tippen Sie auf **[!UICONTROL Asset hinzufügen]**. Navigieren Sie zu einem Asset, wählen Sie es aus und tippen Sie oben rechts auf **[!UICONTROL Auswählen]**.

   >[!NOTE]
   >Wenn Sie das in AEM als Miniaturansicht verwendete Bild löschen und durch ein anderes ersetzen, wird das Original-Asset weiterhin angezeigt.

   * Um ein Asset zu löschen, wählen Sie es aus und tippen Sie auf **[!UICONTROL Asset löschen]**.
   * Um eine Vorgabe anzuwenden, tippen Sie oben rechts auf der Seite auf **[!UICONTROL Vorgabe]** und wählen Sie eine Viewer-Vorgabe aus.
   * Um eine Miniatur hinzuzufügen oder zu ändern, wählen Sie die Miniatur rechts neben dem Asset. Navigieren Sie zur neuen Miniaturansicht oder zum neuen Musterasset, wählen Sie es aus und tippen Sie dann auf **[!UICONTROL Auswählen]**.
   * Um ein ganzes Bildset zu löschen, navigieren Sie zum Bildset, wählen Sie es aus und klicken Sie auf **[!UICONTROL Löschen]**.

   >[!NOTE]
   >
   >Sie können die Bilder in einem Bildset bearbeiten, indem Sie zu diesem Set navigieren, in der linken Seitenleiste auf **[!UICONTROL Mitglieder des Sets]** tippen und dann auf das Bleistiftsymbol eines einzelnen Assets tippen, um das Bearbeitungsfenster zu öffnen.****

1. Tippen Sie auf **[!UICONTROL Speichern]**, wenn Sie die Bearbeitung abgeschlossen haben.

## Anzeigen von Bildsets in einer Vorschau {#previewing-image-sets}

Weitere Informationen finden Sie im Abschnitt [Asset-Vorschau](previewing-assets.md).

## Veröffentlichen von Bildsets {#publishing-image-sets}

Siehe [Veröffentlichen von Assets](publishing-dynamicmedia-assets.md).
