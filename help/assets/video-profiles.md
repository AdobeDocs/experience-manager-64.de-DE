---
title: Videoprofile für dynamische Medien
seo-title: Videoprofile für dynamische Medien
description: 'Dynamic Media enthält bereits das vordefinierte Profil „Adaptive Videoverschlüsselung“. Die Einstellungen in diesem vordefinierten Profil sind optimiert, um Ihren Kunden Ansichten in bestmöglicher Qualität bieten zu können. '
seo-description: 'Dynamic Media enthält bereits das vordefinierte Profil „Adaptive Videoverschlüsselung“. Die Einstellungen in diesem vordefinierten Profil sind optimiert, um Ihren Kunden Ansichten in bestmöglicher Qualität bieten zu können. '
uuid: cfb498f8-44a0-4d94-99b0-fed7c27f575b
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: administering
content-type: reference
discoiquuid: b893f366-279a-4872-9413-77626d3387ea
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939

---


# Dynamic Media video profiles {#video-profiles}

Dynamic Media enthält bereits das vordefinierte Profil „Adaptive Videoverschlüsselung“. Die Einstellungen in diesem vordefinierten Profil sind optimiert, um Ihren Kunden Ansichten in bestmöglicher Qualität bieten zu können. Beim Kodieren von Mastervideos mithilfe des Profils „Adaptive Videoverschlüsselung“ passt der Videoplayer während der Wiedergabe automatisch die Qualität des Videostreams auf Grundlage der Internetverbindungsgeschwindigkeit Ihrer Kunden an. Dies wird als adaptives Streaming bezeichnet.

Die folgenden weiteren Faktoren wirken sich auf die Qualität Ihrer Videos aus:

* **Auflösung des hochgeladenen Mastervideos**

   Wenn das MP4-Video mit einer niedrigeren Auflösung (z. B. 240p oder 360p) aufgezeichnet wurde, kann es nicht in hoher Auflösung gestreamt werden.

* **Videoplayer-Größe**

   By default, the **[!UICONTROL Width]** in the Adaptive Video Encoding profile is set to **[!UICONTROL Auto]**. Wie erwähnt wird je nach Größe des Players bei der Wiedergabe die bestmögliche Qualität verwendet.

Siehe auch [Best Practices zur Videokodierung](video.md#best-practices-for-encoding-videos).

>[!NOTE]
>
>Um die Metadaten eines Videos und die zugehörigen Videobild-Miniaturansichten zu generieren, muss das Video selbst den Kodierungsprozess in dynamischen Medien durchlaufen. In AEM kodiert der Workflow für die **[!UICONTROL Videokodierung mit dynamischen Medien]** Videos, wenn Sie dynamische Medien aktiviert und Video-Cloud Services eingerichtet haben. Dieser Workflow erfasst den Workflow-Prozess und Informationen zu Fehlern.
>
>Siehe [Überwachen der Videokodierung und des YouTube Publishing-Fortschritts](video.md#monitoring-video-encoding-and-youtube-publishing-progress). If you have enabled Dynamic Media and set up video cloud services, the **[!UICONTROL Dynamic Media Encode Video]** workflow automatically takes effect when you upload a video. (Wenn Sie keine dynamischen Medien verwenden, wird der Workflow **[!UICONTROL DAM Update Asset]** wirksam.)
>
>Metadaten sind nützlich, wenn Sie nach Assets suchen. Bei den Miniaturbildern handelt es sich um statische Videobilder, die während der Kodierung generiert werden. They are required by the AEM system and used in the user interface to help you visually identify videos in the **[!UICONTROL Cards View]**, **[!UICONTROL Search Results]** view, and the **[!UICONTROL Asset List]** view. You can see the generated thumbnails when you tap the **[!UICONTROL Renditions]** icon (a painter&#39;s palette) of an encoded video.

Nach dem Erstellen des Videoprofils wenden Sie es auf einen Ordner oder mehrere Ordner an. See [Applying a video profile to folders.](#applying-a-video-profile-to-folders)

Informationen zur Definition von erweiterten Verarbeitungsparametern für andere Asset-Typen finden Sie unter [Konfigurieren der Asset-Verarbeitung](config-dms7.md#configuring-asset-processing).

## Vorgaben für adaptive Videoverschlüsselung {#adaptive-video-encoding-presets}

In der folgenden Tabelle werden die empfohlenen Kodierungsprofile für das adaptive Video-Streaming auf Smartphones und Tablets sowie Desktop-Computern angegeben. Sie können diese Vorgaben für Videos mit jedem Seitenverhältnis verwenden.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Videoformat-Codec</strong></td> 
   <td><strong>Videogröße – Breite (px) </strong></td> 
   <td><strong>Videogröße – Höhe (px)</strong></td> 
   <td><strong>Seitenverhältnis beibehalten?</strong></td> 
   <td><strong>Video-Bitrate (kBit/s)</strong></td> 
   <td><strong>Video-Framerate (fps)</strong></td> 
   <td><strong>Audio-Codec</strong></td> 
   <td><strong>Audiobitrate (Kbit/s)</strong></td> 
  </tr> 
  <tr> 
   <td><p>MP4 H.264 (mp4)</p> </td> 
   <td>auto</td> 
   <td>360</td> 
   <td>Ja</td> 
   <td>730</td> 
   <td>30</td> 
   <td>Dolby HE-AAC</td> 
   <td>128</td> 
  </tr> 
  <tr> 
   <td><p>MP4 H.264 (mp4)</p> </td> 
   <td>auto</td> 
   <td>540</td> 
   <td>Ja</td> 
   <td>2000<br /> </td> 
   <td>30</td> 
   <td>Dolby HE-AAC</td> 
   <td>128</td> 
  </tr> 
  <tr> 
   <td><p>MP4 H.264 (mp4)</p> </td> 
   <td>auto</td> 
   <td>720<br /> </td> 
   <td>Ja</td> 
   <td>3000<br /> </td> 
   <td>30</td> 
   <td>Dolby HE-AAC</td> 
   <td>128</td> 
  </tr> 
 </tbody> 
</table>

## Creating a Dynamic Media video encoding profile for adaptive streaming {#creating-a-video-encoding-profile-for-adaptive-streaming}

Dynamic Media umfasst standardmäßig das vordefinierte Profil „Adaptive Videokodierung“ (eine Gruppe mit Videoupload-Einstellungen für MP4 H.264), das für das beste Anzeigeerlebnis optimiert ist. Sie können dieses Profil beim Hochladen von Videos verwenden.

Wenn dieses vordefinierte Profil Ihre Anforderungen jedoch nicht erfüllt, können Sie ein eigenes Profil für die adaptive Videoverschlüsselung erstellen. When you use the setting **[!UICONTROL Encode for adaptive streaming]**–*a best practice*– all encoding presets that you add to the profile are validated to ensure that all videos have the same aspect ratio. Darüber hinaus werden die kodierten Videos als Multi-Bitrate-Set für das Streaming behandelt.

Beim Erstellen des Videokodierungsprofils sehen Sie, dass die meisten Kodierungsoptionen mit empfohlenen Standardeinstellungen gefüllt sind, um Ihnen die Arbeit zu erleichtern. Wenn Sie allerdings einen anderen Wert als den empfohlenen Standard auswählen, müssen Sie bedenken, dass dies zu schlechter Videoqualität bei der Wiedergabe und zu anderen Leistungsproblemen führen kann.

Für alle MP4 H.264-Videokodierungsvorgaben im Profil werden also die folgenden Werte validiert, um sicherzustellen, dass diese über individuelle Kodierungsvorgaben hinweg identisch sind. Dadurch wird das adaptive Streaming ermöglicht:

* Videoformat-Codec – MP4 H.264 (.mp4)
* Audio-Codec
* Audiobitrate
* Seitenverhältnis beibehalten
* Kodierung mit zwei Durchgängen
* Konstante Bitrate
* H264-Profil
* Audio-Samplingrate

Wenn die Werte nicht identisch sind, können Sie das Profil durchaus im Istzustand erstellen. Denken Sie aber daran, dass das adaptive Streaming dann nicht möglich ist. Stattdessen wird das Einzel-Bitraten-Streaming durchgeführt. Es wird empfohlen, dass Sie die Kodierungseinstellungen so bearbeiten, dass dieselben Werte über individuelle Kodierungsvorgaben hinweg im Profil verwendet werden. (Note that the video profile/preset editor should enforce parity of the adaptive video encoding settings if **[!UICONTROL Encode for adaptive streaming]** is enabled.)

Siehe auch [Erstellen eines Videokodierungsprofils für progressives Streaming](#creating-a-video-encoding-profile-for-progressive-streaming).

Siehe auch [Best Practices für Videokodierung](video.md#best-practices-for-encoding-videos).

Informationen zur Definition von erweiterten Verarbeitungsparametern für andere Asset-Typen finden Sie unter [Konfigurieren der Asset-Verarbeitung](config-dms7.md#configuring-asset-processing).

Nach dem Erstellen des Videoprofils wenden Sie es auf einen oder mehrere Ordner an.

**So erstellen Sie ein Videokodierungsprofil für dynamische Medien für adaptives Streaming**:

1. Tap or click the AEM logo and navigate to **[!UICONTROL Tools > Assets > Video Profiles]**.
1. Tap **[!UICONTROL Create]** to add a new video profile.

1. Geben Sie einen Namen und eine Beschreibung für das Profil ein.
1. Stellen Sie sicher, dass **[!UICONTROL Für adaptives Streaming kodieren]** aktiviert ist (Standard).
1. Tippen Sie auf **[!UICONTROL Videokodierungsvorgabe hinzufügen]**.
1. Legen Sie auf der Registerkarte **[!UICONTROL Allgemein]** die Video- und Audiooptionen fest.

   Tippen Sie auf das Informationssymbol neben den einzelnen Optionen, um zusätzliche Beschreibungen oder empfohlene Einstellungen auf Grundlage des ausgewählten Videoformat-Codecs anzuzeigen.

1. Stellen Sie unter der Überschrift „Videogröße“ sicher, dass **[!UICONTROL Seitenverhältnis beibehalten]** aktiviert ist.
1. Legen Sie die Videoframe-Auflösung in Pixeln fest. Verwenden Sie den Wert **[!UICONTROL Auto]**, um das Seitenverhältnis der Quelle anzupassen (Verhältnis von Breite zu Höhe).  Beispielsweise „Auto x 480“ oder „640 x Auto“.

   Führen Sie einen der folgenden Schritte aus:

   * Geben Sie im Feld **[!UICONTROL Breite]** die Option **[!UICONTROL auto]** ein. Geben Sie im Feld **[!UICONTROL Höhe]** einen Wert in Pixeln ein.
   * To help you visualize the size of the video, tap the **[!UICONTROL Information]** icon (i) to the right of **[!UICONTROL Height]** to open the **[!UICONTROL Size Calculator]** page. Legen Sie mit der **[!UICONTROL Größenberechnung]** die gewünschten Abmessungen des Videos fest (durch das blaue Feld dargestellt). Tippen Sie oben rechts auf **[!UICONTROL X]**, wenn Sie fertig sind.

1. (Optional) Tap the **[!UICONTROL Advanced]** tab and ensure the **[!UICONTROL Use Default Values]** check box is selected (recommended). Alternativ können Sie erweiterte Video- und Audioeinstellungen anpassen.
1. Tippen Sie oben rechts auf der Seite auf **[!UICONTROL Speichern]**, um die Vorgabe zu speichern.
1. Führen Sie einen der folgenden Schritte aus:

   * Wiederholen Sie Schritt 5 bis 10, um weitere Kodierungsvorgaben zu erstellen. (Das adaptive Videostreaming erfordert mehrere Videovorgaben.)
   * Tippen Sie oben rechts auf der Seite erneut auf **[!UICONTROL Speichern]**, um das Profil zu speichern.

## Überwachen des Fortschritts eines Kodierungsauftrags {#monitoring-the-progress-of-an-encoding-job}

Eine Verarbeitungsanzeige (oder eine Statusleiste) wird angezeigt, damit Sie den Fortschritt eines Videokodierungsauftrags visuell überwachen können.

You can also view the `error.log` file to monitor the progress of an encoding job, to see if encoding is finished, or to see any job errors. The `error.log` is found in the `logs` folder where your instance of AEM is installed.

## Creating a Dynamic Media video encoding profile for progressive streaming {#creating-a-video-encoding-profile-for-progressive-streaming}

Wenn Sie die Option **[!UICONTROL Kodieren für adaptives Streaming]** nicht verwenden möchten, beachten Sie, dass alle Kodierungsvoreinstellungen, die Sie dem Profil hinzufügen, als einzelne Videoausgabedarstellungen für Single-Bitrate-Streaming oder progressive Videowiedergabe behandelt werden. Außerdem gibt es keine Validierung, um sicherzustellen, dass alle Videowiedergaben dasselbe Seitenverhältnis aufweisen.

Je nachdem, welchen Modus Sie ausführen, werden die folgenden Videoformat-Codecs unterstützt:

* Dynamischer Media-Scene7-Modus: H.264 (.mp4)
* Dynamischer Media-Hybrid-Modus: H.264 (.mp4), WebM

Siehe auch [Erstellen eines Videokodierungsprofils für adaptives Streaming](#creating-a-video-encoding-profile-for-adaptive-streaming).

Siehe auch [Best Practices für Videokodierung](video.md#best-practices-for-encoding-videos).

Informationen zur Definition von erweiterten Verarbeitungsparametern für andere Asset-Typen finden Sie unter [Konfigurieren der Asset-Verarbeitung](config-dms7.md#configuring-asset-processing).

Nach dem Erstellen des Videoprofils wenden Sie es auf einen oder mehrere Ordner an.

**So erstellen Sie ein Videokodierungsprofil für dynamische Medien für progressives Streaming:**

1. Tippen Sie auf das AEM-Logo und navigieren Sie zu **[!UICONTROL Werkzeuge > Assets > Videoprofile]**.
1. Tap **[!UICONTROL Create]** to add a new video profile.
1. Geben Sie einen Namen und eine Beschreibung für das Profil ein.
1. Clear the **[!UICONTROL Encode for adaptive streaming]** check box.
1. Tippen Sie auf **[!UICONTROL Videokodierungsvorgabe hinzufügen]**.
1. Legen Sie auf der Registerkarte **[!UICONTROL Allgemein]** die Video- und Audiooptionen fest.

   Tap the **[!UICONTROL Information]** icon next to each option for additional descriptions or recommended settings based on the selected video format codec.

1. (Optional) Under the **Video Size** heading, uncheck **[!UICONTROL Keep aspect ratio]**.
1. In the **[!UICONTROL Width]** field, enter **[!UICONTROL auto]**; to the right of the **[!UICONTROL Height]** field, tap the **[!UICONTROL Information]** icon. Passen Sie die Größe des Videos auf der Seite **[!UICONTROL Größenberechnung]** wunschgemäß weiter an. Tippen Sie auf **[!UICONTROL X]**, wenn Sie fertig sind.
1. (Optional) Führen Sie einen der folgenden Schritte aus:

   * Tap the **[!UICONTROL Advanced]** tab, and make sure the **[!UICONTROL Use Default Values]** check box is selected (recommended).
   * Clear the **[!UICONTROL Use Default Values]** check box and specify the video settings and audio settings you want.

      Tap the **[!UICONTROL Information]** icon next to each option for additional descriptions or recommended settings based on the selected video format codec.

1. Tippen Sie oben rechts auf der Seite auf **[!UICONTROL Speichern]**, um die Vorgabe zu speichern.
1. Führen Sie einen der folgenden Schritte aus:

   * Wiederholen Sie Schritt 5 bis 10, um weitere Kodierungsvorgaben zu erstellen.
   * Tippen Sie oben rechts auf der Seite auf **[!UICONTROL Speichern]**, um das Profil zu speichern.

## Verwenden von benutzerdefinierten Videokodierungsparametern {#using-custom-added-video-encoding-parameters}

Sie können vorhandene Videokodierungsprofile bearbeiten, um von erweiterten Parametern zur Videokodierung zu profitieren, die beim Erstellen oder Bearbeiten eines Videoprofils in AEM nicht in der Benutzeroberfläche vorhanden sind. You custom add one or more advanced parameters—such as **[!UICONTROL minBitrate]** and **[!UICONTROL maxBitrate]**—to your existing profile.

**So verwenden Sie benutzerdefinierte Videokodierungsparameter**:

1. Tippen Sie auf das AEM-Logo und navigieren Sie dann zu **[!UICONTROL Werkzeuge > Allgemein > CRXDE Lite]**.
1. From the **[!UICONTROL CRXDE Lite]** page, in the **[!UICONTROL Explorer]** panel on the left, navigate to the following:

   `/conf/global/settings/dam/dm/presets/video/*name_of_video_encoding_profile_to_edit*`

1. In the panel on the lower-right side of the page, from the **[!UICONTROL Properties]** tab, specify the **[!UICONTROL Name]**, **[!UICONTROL Type]**, and **[!UICONTROL Value]** of the parameter you want to use.

   Die folgenden erweiterten Parameter sind verfügbar:

   <table> 
    <tbody> 
    <tr> 
    <td><strong>Name</strong></td> 
    <td><strong>Beschreibung</strong><br /> </td> 
    <td><strong>Typ</strong><br /> </td> 
    <td><strong>Wert</strong></td> 
    </tr> 
    <tr> 
    <td><code>h264Level</code></td> 
    <td>H.264-Level für die Kodierung. Normalerweise wird dieser Parameter basierend auf den Kodierungseinstellungen automatisch bestimmt.</td> 
    <td><code>String</code></td> 
    <td><p>Stufe 10 * h264</p> <p>Beispiel: 3.0 = 30, 1.3 = 13)</p> <p>Kein Standardwert.</p> </td> 
    </tr> 
    <tr> 
    <td><code>keyframe</code></td> 
    <td>Die Zielanzahl der Frames zwischen Keyframes. Berechnen Sie diesen Wert, um alle 2–10 Sekunden einen Keyframe zu generieren. Bei 30 Frames pro Sekunde sollte das Keyframe-Intervall zwischen 60 und 300 liegen.<br /> <br /> Niedrigere Keyframe-Intervalle verbessern das Verhalten bei Stream-Suche und Stream-Wechsel für adaptive Videokodierungen und können auch die Qualität bei Videos mit viel Bewegung verbessern. Da die Keyframes die Größe einer Datei erhöhen, bewirkt ein niedrigeres Keyframe-Intervall in der Regel eine niedrigere Videogesamtqualität bei einer bestimmten Bitrate.</td> 
    <td><code>String</code></td> 
    <td><p>Positive Zahl.</p> <p>Der Standardwert ist 300.</p> <p>Der empfohlene Wert für HLS (HTTP Live Streaming) ist 60–90.</p> </td> 
    </tr> 
    <tr> 
    <td><code>minBitrate</code></td> 
    <td><p>Minimale Bitrate, um Kodierungen mit variabler Bitrate in Kbit/s (Kilobit pro Sekunde) zu ermöglichen.</p> <p>This parameter only applies when<strong> Use Constant Bitrate</strong> is deselected in the Advanced tab when you create or edit a video encoding profile.</p> <p>Siehe auch <a href="/help/assets/video.md#bitrate">Bitrate</a>.</p> </td> 
    <td><code>String</code></td> 
    <td><p>Positive Zahl in Kbit/s.</p> <p>Kein Standardwert.</p> </td> 
    </tr> 
    <tr> 
    <td><code>maxBitrate</code></td> 
    <td><p>Maximale Bitrate, um Kodierungen mit variabler Bitrate in Kbit/s zu ermöglichen.</p> <p>This parameter only applies when<strong> Use Constant Bitrate</strong> is deselected in the Advanced tab when you create or edit a video encoding profile.</p> <p>Siehe auch <a href="/help/assets/video.md#bitrate">Bitrate</a>.</p> </td> 
    <td><code>String</code></td> 
    <td><p>Positive Zahl in Kbit/s.</p> <p>Kein Standardwert. Der empfohlene Wert entspricht jedoch bis zum Zweifachen der Kodierungsbitrate.</p> </td> 
    </tr> 
    <tr> 
    <td><code>audioBitrateCustom</code></td> 
    <td>Legen Sie einen Wert fest, <code>true</code> um eine konstante Bitrate für den Audiostream zu erzwingen, sofern dieser vom Audio-Codec unterstützt wird.</td> 
    <td><code>String</code></td> 
    <td><p><code>true</code>/<code>false</code></p> <p>Der Standardwert ist <code>false</code>.</p> <p>Recommended value for HLS (HTTP Live Streaming) is <code>false</code>.</p> <p> </p> </td> 
    </tr> 
    </tbody> 
   </table>

   ![chlimage_1-516](assets/chlimage_1-516.png)

1. Tippen Sie in der rechten unteren Ecke der Seite auf **[!UICONTROL Hinzufügen]**.
1. Führen Sie einen der folgenden Schritte aus:

   * Wiederholen Sie die Schritte 3 und 4, um Ihrem Videokodierungsprofil einen weiteren Parameter hinzuzufügen.
   * Tippen Sie in der oberen linken Ecke der Seite auf **[!UICONTROL Alle speichern]**.

1. In the upper-left corner of the **[!UICONTROL CRXDE Lite]** page, tap the **[!UICONTROL Back Home]** icon to return to AEM.

### Bearbeiten eines Videokodierungsprofils für dynamische Medien {#editing-a-video-encoding-profile}

Sie können die Videokodierungsprofile bearbeiten, die Sie erstellt haben, um die in diesen Profilen enthaltenen Videovorgaben hinzuzufügen, zu bearbeiten oder zu löschen.

Die Bearbeitung des bereits in Dynamic Media integrierten Profils **[!UICONTROL Adaptive Videokodierung]** ist standardmäßig deaktiviert. Sie können das Profil einfach kopieren und dann unter einem neuen Namen speichern. Dann können Sie die gewünschten Vorgaben im kopierten Profil bearbeiten.

Siehe auch [Best Practices für Videokodierung](video.md#best-practices-for-encoding-videos).

Informationen zur Definition von erweiterten Verarbeitungsparametern für andere Asset-Typen finden Sie unter [Konfigurieren der Asset-Verarbeitung](config-dms7.md#configuring-asset-processing).

**So bearbeiten Sie ein Videokodierungsprofil** für dynamische Medien:

1. Tippen Sie auf das AEM-Logo und navigieren Sie zu **[!UICONTROL Werkzeuge > Assets > Videoprofile]**.
1. On the **[!UICONTROL Video Profiles]** page, check one video profile name.
1. Tippen Sie in der Symbolleiste auf **[!UICONTROL Bearbeiten]**.
1. On the **[!UICONTROL Video Encoding Profile]** page, edit the name and description, as desired.
1. Als Best Practice sollten Sie sicherstellen, dass das Kontrollkästchen **[!UICONTROL Kodierung für adaptives Streaming]** aktiviert ist.

   Tippen Sie auf das Informationssymbol, um eine Beschreibung für adaptives Streaming zu erhalten. (Wenn Sie ein progressives Videoprofil nicht bearbeiten möchten, aktivieren Sie dieses Kontrollkästchen nicht.)

1. Under the **[!UICONTROL Video Encoding Presets]** heading, add, edit, or delete video encoding presets that make up the profile.

   Tap the **[!UICONTROL Information]** icon next to each option on the **[!UICONTROL Basic]** and **[!UICONTROL Advanced]** tabs for additional descriptions or recommended settings based on the selected video format codec.

1. Tippen Sie oben rechts auf der Seite auf **[!UICONTROL Speichern]**.

### Kopieren eines Videokodierungsprofils für dynamische Medien {#copying-a-video-encoding-profile}

1. Tippen Sie auf das AEM-Logo und navigieren Sie zu **[!UICONTROL Werkzeuge > Assets > Videoprofile]**.
1. On the **[!UICONTROL Video Profiles]** page, check one video profile name.
1. On the toolbar, tap **[!UICONTROL Copy]**.
1. On the **[!UICONTROL Video Encoding Profile]** page, enter a new name for the profile.
1. Als Best Practice sollten Sie sicherstellen, dass das Kontrollkästchen **[!UICONTROL Kodierung für adaptives Streaming]** aktiviert ist. Tippen Sie auf das Informationssymbol, um eine Beschreibung für adaptives Streaming zu erhalten. (Wenn Sie ein progressives Videoprofil kopieren, aktivieren Sie das Kontrollkästchen nicht.)

   Wenn im Hybridmodus von Dynamic Video eine WebM-Videovoreinstellung Teil des Videoprofils ist, dann ist die Option **[!UICONTROL Für adaptives Streaming kodieren]** nicht möglich, da alle Vorgaben das MP4-Format aufweisen müssen.
1. Under the **[!UICONTROL Video Encoding Presets]** heading, add, edit, or delete video encoding presets that make up the profile.

   Tap the **[!UICONTROL Information]** icon next to each option on the **[!UICONTROL Basic]** and **[!UICONTROL Advanced]** tabs for recommended settings and descriptions.

1. Tippen Sie oben rechts auf der Seite auf **[!UICONTROL Speichern]**.

### Löschen eines Videokodierungsprofils für dynamische Medien {#deleting-a-video-encoding-profile}

1. Tippen Sie auf das AEM-Logo und navigieren Sie zu **[!UICONTROL Werkzeuge > Assets > Videoprofile]**.
1. On the **[!UICONTROL Video Profiles]** page, check one or more video profile names.
1. Tippen Sie in der Symbolleiste auf **[!UICONTROL Löschen]**.
1. Tippen Sie auf **[!UICONTROL OK]**.

## Anwenden eines Videoprofils für dynamische Medien auf Ordner {#applying-a-video-profile-to-folders}

Wenn Sie ein Videoprofil einem Ordner zuweisen, erben automatisch alle Unterordner das Profil vom übergeordneten Ordner. Demzufolge können Sie einem Ordner nur ein Videoprofil zuweisen. Daher sollten Sie die Ordnerstruktur sorgfältig planen, in der Sie Assets hochladen, speichern, verwenden und archivieren.

Wenn Sie einem Ordner ein anderes Videoprofil zugewiesen haben, überschreibt das neue das vorherige Profil. Die zuvor vorhandenen Ordner-Assets verbleiben unverändert. Das neue Profil wird auf die Assets angewendet, die dem Ordner später hinzugefügt werden.

Ordner, denen ein Profil zugewiesen wurde, werden in der Benutzeroberfläche durch den Namen des Profils angegeben, der im Kartennamen angezeigt wird.

![chlimage_1-517](assets/chlimage_1-517.png)

Sie können Videoprofile auf bestimmte Ordner oder global auf alle Assets anwenden.

### Anwenden von Videoprofilen auf bestimmte Ordner {#applying-video-profiles-to-specific-folders}

Sie können ein Videoprofil über das Menü **[!UICONTROL Werkzeuge]** oder, falls Sie sich im Ordner befinden, über **[!UICONTROL Eigenschaften]** auf einen Ordner anwenden. In diesem Abschnitt wird beschrieben, wie Sie Videoprofile auf beide Arten auf Ordner anwenden.

Ordner, denen bereits ein Profil zugewiesen ist, werden durch die Anzeige des Profilnamens direkt unter dem Ordnernamen gekennzeichnet.

#### Applying Dynamic Media video profiles to folders from Profiles user interface {#applying-video-profiles-to-folders-from-profiles-user-interface}

1. Tippen Sie auf das AEM-Logo und navigieren Sie zu **[!UICONTROL Werkzeuge > Assets > Videoprofile]**.
1. Wählen Sie ein Videoprofil aus, das Sie auf einen oder mehrere Ordner anwenden möchten.
1. Tippen Sie auf **[!UICONTROL Profil auf Ordner anwenden]**, wählen Sie den Ordner oder mehrere Ordner aus, die Sie zum Empfangen der neu hochgeladenen Assets verwenden möchten, und klicken Sie auf **[!UICONTROL Übernehmen]**. Ordner, denen bereits ein Profil zugewiesen ist, werden durch die Anzeige des Profilnamens direkt unter dem Ordnernamen gekennzeichnet.

#### Applying Dynamic Media video profiles to folders from Properties {#applying-video-profiles-to-folders-from-properties}

1. Tap the AEM logo and navigate to **[!UICONTROL Assets]** and then to the folder that you want to apply a video profile to.
1. On the folder, tap the check mark to select it and then tap **[!UICONTROL Properties]**.
1. Select the **[!UICONTROL Video Profiles]** tab and select the profile from the drop-down menu and tap **[!UICONTROL Save &amp; Close]**. Ordner, denen bereits ein Profil zugewiesen ist, werden durch die Anzeige des Profilnamens direkt unter dem Ordnernamen gekennzeichnet.

   ![chlimage_1-518](assets/chlimage_1-518.png)

### Globales Anwenden eines Videoprofils für dynamische Medien {#applying-a-video-profile-globally}

Profile können nicht nur auf einzelne Ordner, sondern auch global angewendet werden. Dann wird allen Inhalten, die Sie in AEM-Assets in beliebigen Ordnern hochladen, das ausgewählte Profil zugeordnet.

**So wenden Sie ein dynamisches Medienvideoprofil global** an

1. Navigate to CRXDE Lite to the following node: `/content/dam/jcr:content`.
1. Fügen Sie die Eigenschaft **[!UICONTROL videoProfile]** hinzu: `/etc/dam/video/dynamicmedia/<name_of_video_encoding_profile>`
1. Tippen Sie auf **[!UICONTROL Alle speichern]**.

![chlimage_1-519](assets/chlimage_1-519.png)

## Entfernen eines Videoprofils für dynamische Medien aus Ordnern {#removing-a-video-profile-from-folders}

Wenn Sie ein Videoprofil aus einem Ordner entfernen, übernehmen alle Unterordner automatisch die Entfernung des Profils vom übergeordneten Ordner. Die Verarbeitung der Dateien, die in den Ordnern stattgefunden hat, verbleibt jedoch intakt.

Sie können ein Videoprofil über das Menü **[!UICONTROL Werkzeuge]** oder, falls Sie sich im Ordner befinden, über **[!UICONTROL Eigenschaften]** aus einem Ordner entfernen. In diesem Abschnitt wird beschrieben, wie Sie Videoprofile auf beide Arten aus Ordnern entfernen.

### Removing Dynamic Media video profiles from folders by way of Profiles user interface {#removing-video-profiles-from-folders-via-profiles-user-interface}

1. Tippen Sie auf das AEM-Logo und navigieren Sie zu **[!UICONTROL Werkzeuge > Assets > Videoprofile]**.
1. Wählen Sie das Videoprofil, das Sie aus einem oder mehreren Ordnern entfernen möchten.
1. Tap **[!UICONTROL Remove Profile from Folder(s)]** and select the folder or multiple folders you want use to remove the profile from and tap **[!UICONTROL Remove]**.

   Sie können bestätigen, dass das Videoprofil nicht länger auf einen Ordner angewendet wird, da der Name in diesem Fall nicht mehr unter dem Ordner angezeigt wird.

### Removing Dynamic Media video profiles from folders by way of Properties {#removing-video-profiles-from-folders-via-properties}

1. Tap the AEM logo and navigate to **[!UICONTROL Assets]** and then to the folder that you want to remove a video profile from.
1. On the folder, tap the check mark to select it, then tap **[!UICONTROL Properties]**.
1. Select the **[!UICONTROL Video Profiles]** tab and select **[!UICONTROL None]** from the drop-down menu and tap **[!UICONTROL Save &amp; Close]**. Ordner, denen bereits ein Profil zugewiesen ist, werden durch die Anzeige des Profilnamens direkt unter dem Ordnernamen gekennzeichnet.

