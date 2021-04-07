---
title: Konfigurieren von Dynamic Media – Scene7-Modus
description: Erfahren Sie, wie Sie den Dynamic Media - Scene7-Modus konfigurieren.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
exl-id: b0f0c6e4-77c8-40db-a9f4-699d1a633571
feature: Konfiguration, Scene7-Modus
role: Administrator,Business Practitioner,Developer
translation-type: tm+mt
source-git-commit: 13eb1d64677f6940332a2eeb4d3aba2915ac7bba
workflow-type: tm+mt
source-wordcount: '5593'
ht-degree: 54%

---

# Konfigurieren von Dynamic Media – Scene7-Modus {#configuring-dynamic-media-scene-mode}

Wenn Sie Adobe Experience Manager für verschiedene Umgebung wie Entwicklung, Staging und Live-Produktion verwenden, müssen Sie Dynamic Media-Cloud Services für jede Umgebung konfigurieren.

## Architekturgrafik von Dynamic Media – Scene7-Modus {#architecture-diagram-of-dynamic-media-scene-mode}

Die folgende Architekturgrafik beschreibt die Funktionsweise von Dynamic Media – Scene7-Modus.

Mit der neuen Architektur ist Experience Manager für Übergeordnet-Assets und Synchronisierungen mit Dynamic Media für die Verarbeitung und Veröffentlichung von Assets verantwortlich:

1. Wenn das Übergeordnet-Asset in Experience Manager hochgeladen wird, wird es in Dynamic Media repliziert. Ab diesem Punkt übernimmt Dynamic Media die gesamte Asset-Verarbeitung und Ausgabenerstellung, z. B. Videokodierung und dynamische Varianten eines Bilds.
1. Nachdem die Darstellungen generiert wurden, kann Experience Manager sicher auf die Dynamic Media-Remote-Darstellungen zugreifen und diese Vorschau durchführen (es werden keine Binärdateien an die Experience Manager-Instanz zurückgesendet).
1. Nachdem der Inhalt bereit zur Genehmigung und Veröffentlichung ist, wird der Dynamic Media-Service ausgelöst und pusht Inhalt an Bereitstellungs-Server und Cache-Inhalt in das CDN.

![chlimage_1](assets/chlimage_1.png)

## Aktivieren von Dynamic Media im Scene7-Modus {#enabling-dynamic-media-in-scene-mode}

[Dynamic Media ist standardmäßig deaktiviert. ](https://www.adobe.com/de/solutions/web-experience-management/dynamic-media.html) Um dynamische Medienfunktionen nutzen zu können, müssen Sie diese aktivieren.

>[!NOTE]
>
>Dynamic Media - Der Scene7-Modus ist nur für die Autoreninstanz des Experience Managers verfügbar. Daher müssen Sie `runmode=dynamicmedia_scene7`auf der Autoreninstanz des Experience Managers konfigurieren, nicht auf der Veröffentlichungsinstanz des Experience Managers.

Um Dynamic Media zu aktivieren, müssen Sie den Experience Manager mit dem Ausführungsmodus `dynamicmedia_scene7` über die Befehlszeile starten, indem Sie Folgendes in ein Terminalfenster eingeben (Beispiel: Anschluss 4502):

```shell
java -Xms4096m -Xmx4096m -Doak.queryLimitInMemory=500000 -Doak.queryLimitReads=500000 -jar cq-quickstart-6.4.0.jar -gui -r author,dynamicmedia_scene7 -p 4502
```

## (Optional) Migration von Dynamic Media-Vorgaben und -Konfigurationen von 6.3 zu 6.4 ohne Ausfallzeit {#optional-migrating-dynamic-media-presets-and-configurations-from-to-zero-downtime}

Wenn Sie Experience Manager Dynamic Media von 6.3 auf 6.4 aktualisieren (einschließlich der Möglichkeit, keine Ausfallzeiten bereitzustellen), führen Sie den folgenden Befehl &quot;curl&quot;aus, um alle Ihre Vorgaben und Konfigurationen in der CRXDE Lite von `/etc` auf `/conf` zu migrieren.

>[!NOTE]
>
>Wenn Sie Ihre Experience Manager-Instanz im Kompatibilitätsmodus ausführen - d. h. die Kompatibilität ist verpackt - müssen Sie diese Befehle nicht ausführen.

Um Ihre benutzerdefinierten Vorgaben und Konfigurationen von `/etc` auf `/conf` zu migrieren, führen Sie den folgenden Linux®-Befehl &quot;curl&quot;aus:

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets.migratedmcontent.json`

Bei allen Upgrades, ob mit oder ohne Kompatibilitätspaket, können Sie mit dem folgenden Befehl die standardmäßigen Benutzer-Vorgaben kopieren:

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

## (Optional) Installieren von Feature Pack 18912 für Massenmigration von Assets{#installing-feature-pack}

Mit Feature Pack 18912 können Sie Assets per FTP stapelweise erfassen oder Assets von Dynamic Media - Hybrid-Modus oder Dynamic Media Classic auf dem Experience Manager in den Dynamic Media - Scene7-Modus migrieren. Es ist in Adobe Professional Services erhältlich.

Weitere Informationen finden Sie unter [Feature Pack 18912 installieren für Massenmigration von Assets](bulk-ingest-migrate.md).

## Konfigurieren von Dynamic Media Cloud Services {#configuring-dynamic-media-cloud-services}

Ändern Sie das Kennwort, bevor Sie Dynamic Media-Cloud Services konfigurieren. Nachdem Sie Ihre Bereitstellungs-E-Mail mit Dynamic Media-Anmeldeinformationen erhalten haben, müssen Sie sich [bei der Dynamic Media Classic-Desktopanwendung anmelden, um Ihr Kennwort zu ändern. ](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/intro/dynamic-media-classic-desktop-app.html?lang=en#system-requirements-dmc-app) Das Kennwort aus der Bereitstellungs-E-Mail wird systemseitig erstellt und ist nur als temporäres Kennwort vorgesehen. Sie müssen das Kennwort aktualisieren, damit Dynamic Media Cloud Service mit den richtigen Anmeldedaten eingerichtet wird.

>[!NOTE]
>
>Standardmäßig ist der Konfigurationspfad für Cloud Services `/content/dam`. Jeder andere Konfigurationspfad wird vom Dynamic Media - Scene7-Modus nicht unterstützt.

So konfigurieren Sie Dynamic Media-Cloud Services:

1. Tippen Sie in Experience Manager auf das Logo des Experience Managers, um auf die globale Navigationskonsole zuzugreifen, und dann auf das Symbol Tools und dann auf **[!UICONTROL Cloud Services > Dynamic Media Configuration]**.
1. Tippen Sie auf der Seite &quot;Dynamic Media Configuration Browser&quot;im linken Bereich auf **[!UICONTROL global]** und dann auf **[!UICONTROL Create]**. Tippen oder wählen Sie nicht das Ordnersymbol links neben [!UICONTROL global].
1. Geben Sie auf der Seite [!UICONTROL Dynamic Media-Konfiguration erstellen] einen Titel, die E-Mail-Adresse des Dynamic Media-Kontos und das Kennwort ein. Wählen Sie Ihre Region aus. Diese Informationen werden Ihnen per Adobe in Ihrer Bereitstellungs-E-Mail bereitgestellt. Wenden Sie sich an den Kundendienst der Adobe, wenn Sie die E-Mail nicht erhalten haben.

   Tippen Sie auf **[!UICONTROL Verbindung zu Dynamic Media]** herstellen.

   >[!NOTE]
   >
   >Nachdem Sie Ihre Bereitstellungs-E-Mail mit Dynamic Media-Anmeldeinformationen erhalten haben, öffnen Sie die Desktopanwendung [Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html?lang=de#getting-started) und melden Sie sich dann bei Ihrem Firmen-Konto an, um Ihr Kennwort zu ändern. Das Kennwort aus der Bereitstellungs-E-Mail wird systemseitig erstellt und ist nur als temporäres Kennwort vorgesehen. Es ist wichtig, dass Sie das Kennwort aktualisieren, damit der Dynamic Media-Cloud Service mit den richtigen Anmeldeinformationen eingerichtet wird.

1. Wenn die Verbindung hergestellt wurde, können Sie auch folgende Einstellungen festlegen:

   * **[!UICONTROL Unternehmen]** – der Name des Dynamic Media-Kontos. Es ist möglich, mehrere Dynamic Media-Konten für verschiedene Untermarken, Geschäftsbereiche oder unterschiedliche Staging-/Produktionsgruppen-Umgebung zu haben.
   * **[!UICONTROL Firmen-Root-Ordnerpfad]**
   * **[!UICONTROL Veröffentlichung von Assets]** – Die Option **[!UICONTROL Sofort]** bedeutet, dass das System hochgeladene Assets aufnimmt und umgehend die URL/den Link zur Einbettung bereitstellt. Zum Veröffentlichen von Assets ist kein Benutzereingriff erforderlich. Die Option **[!UICONTROL Bei Aktivierung]** bedeutet, dass Sie das Asset explizit veröffentlichen müssen, bevor ein URL-/Einbettungslink bereitgestellt wird.
   * **[!UICONTROL Sicherer Vorschau-Server]** – bietet Ihnen die Möglichkeit, den URL-Pfad zu Ihrem Vorschau-Server für sichere Ausgaben anzugeben. Das heißt, nach der Generierung von Darstellungen kann Experience Manager sicher auf die Dynamic Media-Remote-Darstellungen zugreifen und diese Vorschau durchführen (es werden keine Binärdateien an die Experience Manager-Instanz zurückgesendet).

      Sofern Sie keine spezielle Vereinbarung zur Verwendung des Servers Ihrer eigenen Firma oder eines Spezialservers haben, empfiehlt Adobe die Verwendung der Standardeinstellung.
   >[!NOTE]
   >
   >Die Versionierung wird in DMS7 nicht unterstützt. Eine verzögerte Aktivierung gilt nur, wenn auf der Seite „Konfiguration von Dynamic Media bearbeiten“ die Option **[!UICONTROL Assets veröffentlichen]** auf **[!UICONTROL Bei Aktivierung]** eingestellt ist, und erst dann, wenn das Asset zum ersten Mal aktiviert wird.
   >
   >Wenn ein Asset aktiviert wurde, werden alle Aktualisierungen automatisch live in der S7-Bereitstellung übernommen.

   ![dynamicmediaconfiguration2updated](assets/dynamicmediaconfiguration2updated.png)

1. Tippen Sie auf **[!UICONTROL Speichern]**.
1. Damit Dynamic Media-Inhalte vor der Veröffentlichung sicher Vorschau werden können, müssen Sie die Instanz im Experience Manager &quot;Autor&quot;so konfigurieren, dass eine Verbindung zu Dynamic Media hergestellt wird.

   * Öffnen Sie das [Dynamic Media Classic-Desktop-Programm](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started) und melden Sie sich bei Ihrem Konto an. Ihre Benutzer- und Anmeldedaten haben Sie zum Zeitpunkt der Bereitstellung von Adobe erhalten. Wenn Ihnen die Informationen nicht vorliegen, wenden Sie sich an den technischen Support.
   * Tippen Sie in der Navigationsleiste oben rechts auf der Seite auf **[!UICONTROL Einstellungen > Anwendungseinstellungen > Veröffentlichungseinstellungen > Image-Server]**.
   * Wählen Sie auf der Seite „Veröffentlichung zum Image-Server“ in der Dropdown-Liste „Veröffentlichungskontext“ die Option **[!UICONTROL Image-Serving testen]**.
   * Tippen Sie für den Client-Adressfilter auf **[!UICONTROL Hinzufügen]**.
   * Aktivieren Sie das Kontrollkästchen, um die Adresse zu aktivieren (einschalten). Geben Sie die IP-Adresse der Autoreninstanz des Experience Managers (nicht Dispatcher-IP) ein.
   * Tippen Sie auf **[!UICONTROL Speichern]**.

Sie haben nun die Grundkonfiguration abgeschlossen und können Dynamic Media im Scene7-Modus verwenden.

Wenn Sie Ihre Konfiguration weiter anpassen möchten, können Sie auch eine der Aufgaben unter [(Optional) Konfigurieren der erweiterten Einstellungen in Dynamic Media – Scene7-Modus](#optional-configuring-advanced-settings-in-dynamic-media-scene-mode) abschließen.

## (Optional) Konfigurieren der erweiterten Einstellungen in Dynamic Media – Scene7-Modus {#optional-configuring-advanced-settings-in-dynamic-media-scene-mode}

Wenn Sie die Konfiguration weiter anpassen und Dynamic Media – Scene7-Modus einrichten oder die Leistung optimieren möchten, können Sie eine oder mehrere der folgenden optionalen Aufgaben durchführen:

* [(Optional) Einrichtung und Konfiguration der Einstellungen von Dynamic Media – Scene7-Modus](#optional-setup-and-configuration-of-dynamic-media-scene-mode-settings-p)

* [(Optional) Steigern der Leistung von Dynamic Media – Scene7-Modus](#optional-tuning-the-performance-of-dynamic-media-scene-mode) 
* [(Optional) Filtern von Assets für die Replizierung](#optional-filtering-assets-for-replication)

### (Optional) Einrichtung und Konfiguration der Einstellungen von Dynamic Media – Scene7-Modus</p> {#optional-setup-and-configuration-of-dynamic-media-scene-mode-settings-p}

Wenn Sie sich im Ausführungsmodus **dynamicmedia_scene7** befinden, verwenden Sie die Dynamic Media Classic-Benutzeroberfläche, um Ihre Dynamic Media-Einstellungen zu ändern.

Bei einigen der oben genannten Aufgaben müssen Sie das [Dynamic Media Classic-Desktop-Programm](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started) öffnen und sich dann bei Ihrem Konto anmelden.

Die Aufgaben für die Einrichtung und Konfiguration sind:

* [Veröffentlichungseinstellungen für Image-Server](#publishing-setup-for-image-server)
* [Konfigurieren der allgemeinen Programmeinstellungen](#configuring-application-general-settings)
* [Konfigurieren des Farb-Managements](#configuring-color-management)
* [Bearbeiten von MIME-Typen für unterstützte Formate](#editing-mime-types-for-supported-formats)
* [Hinzufügen von MIME-Typen für nicht unterstützte Formate](#adding-mime-types-for-unsupported-formats)
* [Erstellen von Stapelsatzvorgaben zum automatischen Erzeugen von Bild- und Rotationssets](#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets)

#### Veröffentlichungseinstellungen für Image-Server  {#publishing-setup-for-image-server}

Mit den Veröffentlichungseinstellungen wird festgelegt, wie Assets standardmäßig von Dynamic Media bereitgestellt werden. Wenn keine Einstellung festgelegt wird, stellt Dynamic Media ein Asset gemäß den Standardeinstellungen unter „Veröffentlichungseinstellungen“ bereit. Beispiel: Bei der Anfrage, ein Bild bereitzustellen, das kein Auflösungsattribut enthält, wird ein Bild mit der Einstellung „Standardobjektauflösung“ bereitgestellt.

So konfigurieren Sie die Veröffentlichungseinstellungen: Tippen Sie in Dynamic Media Classic auf **[!UICONTROL Einstellungen > Anwendungseinstellungen > Veröffentlichungseinstellungen > Image-Server]**.

Auf dem Bildschirm „Image-Server“ werden Standardeinstellungen für das Bereitstellen von Bildern festgelegt. Eine Beschreibung der einzelnen Einstellungen finden Sie in der Benutzeroberfläche.

* **[!UICONTROL Anfrage-Attribute]**: Mit diesen Einstellungen werden Einschränkungen für die Bilder festgelegt, die über den Server bereitgestellt werden können.
* **[!UICONTROL Standardattribute für Anfragen]**: Diese Einstellungen beziehen sich auf die standardmäßige Darstellung von Bildern.
* **[!UICONTROL Allgemeine Attribute für Miniaturansichten]**: Diese Einstellungen beziehen sich auf die standardmäßige Darstellung von Miniaturbildern.
* **[!UICONTROL Standardeinstellungen für Katalogfelder]**: Diese Einstellungen beziehen sich auf die Auflösung und den Standardtyp für Miniaturansichten von Bildern.
* **[!UICONTROL Farbverwaltungsattribute]**: Mit diesen Einstellungen wird festgelegt, welche ICC-Farbprofile verwendet werden.
* **[!UICONTROL Kompatibilitätsattribute]**: Diese Einstellung ermöglicht die Behandlung von Anfangs- und Endabsätzen in Textebenen wie in Version 3.6, um die Abwärtskompatibilität zu gewährleisten.
* **[!UICONTROL Lokalisierungsunterstützung]**: Mit diesen Einstellungen können mehrere Gebietsschemaattribute verwaltet werden. Außerdem kann damit eine Zeichenfolge der Gebietsschemakarte angegeben werden, damit Sie festlegen können, welche Sprachen für die verschiedenen QuickInfos in Viewern unterstützt werden sollen. Weitere Informationen zum Einrichten der Lokale Anpassung-Unterstützung finden Sie unter [Wichtige Überlegungen bei der Implementierung der lokale Anpassung](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/setup/publish-setup.html#image-server).

#### Konfigurieren der allgemeinen Programmeinstellungen {#configuring-application-general-settings}

Um die Seite [!UICONTROL Allgemeine Programmeinstellungen] zu öffnen, tippen Sie in der Dynamic Media Classic-Navigationsleiste auf **[!UICONTROL Einstellungen > Anwendungseinstellungen > Allgemeine Einstellungen]**.

**[!UICONTROL Server]**: Bei der Kontobereitstellung stellt Dynamic Media automatisch die zugeordneten Server für Ihr Unternehmen bereit. Diese Server werden verwendet, um URL-Zeichenfolgen für Ihre Website und Programme zu erstellen. Diese URL-Aufrufe gelten spezifisch für Ihr Konto. Ändern Sie keine Servernamen, es sei denn, Sie werden von der Unterstützung des Experience Managers ausdrücklich dazu aufgefordert.

**[!UICONTROL Bilder überschreiben]**: Dynamic Media lässt zwei Dateien mit denselben Namen nicht zu. Die URL-ID (Dateiname ohne Erweiterung) eines Elements muss jeweils eindeutig sein. Diese Optionen legen fest, wie Ersatz-Assets hochgeladen werden, d. h. ob sie das Original ersetzen oder doppelt vorhanden sind. Duplizierte Assets werden durch Anhängen von „-1“ umbenannt („chair.tif“ wird beispielsweise zu „chair-1.tif“). Diese Optionen gelten für Assets, die in einen anderen Ordner als das Original hochgeladen werden, oder Assets mit einer anderen Dateinamenerweiterung als das Original (z. B. JPG, TIF oder PNG).

* **[!UICONTROL Im aktuellen Ordner Bilder mit demselben Namen und derselben Erweiterung überschreiben]**: Diese Option stellt die strengste Ersetzungsregel dar. Das Ersatzbild muss in den Ordner des Originalbilds hochgeladen werden und dieselbe Dateierweiterung haben wie das Originalbild. Werden diese Anforderungen nicht erfüllt, wird ein Duplikat geschaffen.

>[!NOTE]
>
>Um die Konsistenz mit Experience Manager zu wahren, wählen Sie **[!UICONTROL Im aktuellen Ordner überschreiben, Name/Erweiterung des Basisbilds]**.

* **[!UICONTROL In einem beliebigen Ordner überschreiben, Name/Erweiterung]**  des Basisassets - Erfordert, dass das Ersatzbild dieselbe Dateinamenerweiterung wie das Originalbild hat (z. B.  `chair.jpg` ersetzt  `chair.jpg` und nicht  `chair.tif`). Sie können das Ersatzbild jedoch in einen anderen Ordner hochladen als den, in dem sich das Original befindet. Das hochgeladene Bild bleibt dann im neuen Ordner; die Datei befindet sich also nicht mehr am ursprünglichen Speicherort..
* **[!UICONTROL In belieb. Ordner Assets mit ident. Namen unabh. von Erweit. überschreiben]**: Diese Option stellt die am wenigsten einschränkende Ersetzungsregel dar. Sie können ein Ersatzbild in einen anderen Ordner hochladen als den, in dem sich das Originalbild befindet, und eine Datei mit einer anderen Dateierweiterung verwenden, um die Originaldatei zu ersetzen. Wenn sich die Originaldatei in einem anderen Ordner befindet, bleibt das Ersatzbild in dem neuen Ordner, in den es hochgeladen wurde.

**[!UICONTROL Standardfarbprofile]**: Zusätzliche Informationen finden Sie unter [Konfigurieren des Farb-Managements](#configuring-color-management).

>[!NOTE]
>
>Standardmäßig zeigt das System 15 Ausgabedarstellungen an, wenn Sie **[!UICONTROL Ausgabedarstellungen]** auswählen, und 15 Viewer-Voreinstellungen, wenn Sie in der Detailansicht des Assets **[!UICONTROL Viewer]** auswählen. Sie können diese Grenze erhöhen. Siehe [Erhöhung der Anzahl der Bildvorgaben, die angezeigt werden,](managing-image-presets.md#increasing-or-decreasing-the-number-of-image-presets-that-display) oder [Erhöhung der Anzahl der Viewer-Vorgaben, die](managing-viewer-presets.md#increasing-the-number-of-viewer-presets-that-display) anzeigen.

#### Konfigurieren des Farb-Managements {#configuring-color-management}

Beim Farb-Management für Dynamic Media können Sie die Farben von Assets korrigieren. Bei der Farbkorrektur behalten übernommene Assets ihren Farbraum (RGB, CMYK, Grau) und das eingebettete Farbprofil bei. Wenn Sie eine dynamische Ausgabedarstellung anfordern, wird die Bildfarbe gemäß dem Zielfarbraum korrigiert, indem eine CMYK-, RGB- oder Grau-Ausgabe verwendet wird. Siehe [Konfigurieren von Bildvorgaben](managing-image-presets.md).

So konfigurieren Sie die Standardfarbeigenschaften, damit die Farbkorrektur beim Anfordern von Bildern aktiviert ist:

1. Öffnen Sie das [Dynamic Media Classic-Desktop-Programm](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started) und melden Sie sich mit den Anmeldedaten, die Sie zum Zeitpunkt der Bereitstellung erhalten haben, bei Ihrem Konto an. Navigieren Sie zu **[!UICONTROL Einrichtung > Anwendungseinstellungen]**.
1. Erweitern Sie den Bereich **[!UICONTROL Veröffentlichungseinstellungen]** und wählen Sie **[!UICONTROL Image-Server]**. Legen Sie **[!UICONTROL Veröffentlichungskontext]** beim Festlegen von Standardwerten für Veröffentlichungsinstanzen auf **[!UICONTROL Image Serving]** fest.
1. Blättern Sie zu der Eigenschaft, die Sie ändern müssen. Beispiel: Eine Eigenschaft im Bereich **[!UICONTROL Farbmanagementattribute]**.

   Sie können die folgenden Farbkorrektureigenschaften festlegen:

   * [!UICONTROL CMYK-Standardfarbraum]: Name des standardmäßigen CMYK-Farbprofils
   * [!UICONTROL Graustufen-Standardfarbraum]: Name des standardmäßigen Grau-Farbprofils
   * [!UICONTROL RGB-Standardfarbraum]: Name des standardmäßigen RGB-Farbprofils
   * [!UICONTROL Rendering Intent für Farbumwandlung]: Gibt die Render-Priorität an. Die zulässigen Werte sind `perceptual`, `relative` `colometric`, `saturation` und `absolute colometric`. Adobe empfiehlt `relative` als Standard.

1. Tippen Sie auf **[!UICONTROL Speichern]**.

So können Sie beispielsweise den **[!UICONTROL RGB-Standardfarbraum]** auf `sRGB` und den **[!UICONTROL CMYK-Standardfarbraum]** auf `WebCoated` festlegen.

Dies hat folgende Auswirkungen:

* Die Farbkorrektur für RGB- und CMYK-Bilder wird aktiviert.
* RGB-Profile ohne Farbraum werden als im Farbraum `sRGB` angezeigt.
* CMYK-Profile ohne Farbraum werden als Farbräume `WebCoated` angenommen.
* Dynamische Darstellungen, die RGB-Ausgabe zurückgeben, geben sie im Farbraum `sRGB` zurück.
* Dynamische Darstellungen, die CMYK-Ausgabe zurückgeben, geben sie im Farbraum `WebCoated` zurück.

#### Bearbeiten von MIME-Typen für unterstützte Formate {#editing-mime-types-for-supported-formats}

Sie können festlegen, welche Asset-Typen von Dynamic Media verarbeitet werden, und erweiterte Asset-Verarbeitungsparameter anpassen. Beispielsweise können Sie Asset-Verarbeitungsparameter für folgende Aktionen festlegen:

* Konvertieren eines Adobe PDF-Dokuments in ein E-Katalog-Asset
* Konvertieren eines Adobe Photoshop-Dokuments (.PSD) in ein Bannervorlagen-Asset für Personalisierung
* Rastern Sie eine Adobe Illustrator-Datei (.AI) oder eine Adobe Photoshop Encapsulated PostScript® file (.EPS).
* [Videoprofile](/help/assets/video-profiles.md) und [Bilddarstellungsprofile](/help/assets/image-profiles.md) können jeweils zum Definieren der Verarbeitung von Videos und Bildern verwendet werden.

Informationen hierzu finden Sie unter [Hochladen von Assets](managing-assets-touch-ui.md#uploading-assets).

**So bearbeiten Sie MIME-Typen für unterstützte Formate**

1. Tippen Sie in Experience Manager auf das Logo des Experience Managers, um auf die globale Navigationskonsole zuzugreifen, dann auf das Symbol **[!UICONTROL Tools]** (Hammer) und navigieren Sie zu **[!UICONTROL Allgemein > CRXDE Lite]**.
1. Navigieren Sie in der linken Leiste zu:

   `/conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`

   ![mimetypes](assets/mimetypes.png)

1. Wählen Sie unter dem Ordner `mimeTypes` einen Mime-Typ aus.
1. Im rechten unteren Bereich der Seite „CRXDE Lite“:

   * Doppelklicken Sie auf das Feld **[!UICONTROL Aktiviert]**. Standardmäßig sind alle Asset-Mime-Typen aktiviert (auf **[!UICONTROL true]** eingestellt). Das bedeutet, dass die Assets zur Verarbeitung mit Dynamic Media synchronisiert werden. Wenn Sie diesen Asset-MIME-Typ von der Verarbeitung ausschließen möchten, ändern Sie diese Einstellung in **[!UICONTROL false]**.
   * Doppelklicken Sie auf **[!UICONTROL jobParam]**, um das zugehörige Textfeld zu öffnen. Unter [Unterstützte MIME-Typen](assets-formats.md#supported-mime-types) finden Sie eine Liste mit zulässigen Werten für Verarbeitungsparameter, die Sie für einen bestimmten MIME-Typ verwenden können.

1. Führen Sie einen der folgenden Schritte aus:

   * Wiederholen Sie die Schritte 3 bis 4, um weitere Mime-Typen zu bearbeiten.
   * Tippen Sie in der Menüleiste der Seite &quot;CRXDE Lite&quot;auf **[!UICONTROL Alle speichern]**.

1. Tippen Sie oben links auf der Seite auf **[!UICONTROL CRXDE Lite]**, um zum Experience Manager zurückzukehren.

#### Hinzufügen benutzerdefinierter MIME-Typen für nicht unterstützte Formate {#adding-custom-mime-types-for-unsupported-formats}

Sie können benutzerdefinierte MIME-Typen für nicht unterstützte Formate in Experience Manager Assets hinzufügen. Um sicherzustellen, dass alle neuen Knoten, die Sie in CRXDE Lite hinzufügen, nicht von Experience Manager gelöscht werden, verschieben Sie den MIME-Typ vor **[!UICONTROL image_]** und der aktivierte Wert auf **[!UICONTROL false]**.

**So fügen Sie benutzerspezifische MIME-Typen für nicht unterstützte Formate hinzu**

1. Klicken Sie in Experience Manager auf **[!UICONTROL Tools > Vorgänge > Web-Konsole]**.

   ![Web-Konsole](assets/2019-08-02_16-13-14.png)

1. Auf der Seite **[!UICONTROL Adobe Experience Manager-Web-Konsolen-Konfiguration]** wird eine neue Browser-Registerkarte geöffnet.

   ![Experience Manager Web Console-Konfiguration](assets/2019-08-02_16-17-29.png)

1. Blättern Sie auf der Seite nach unten zum Namen **[!UICONTROL Adobe CQ Scene7 Asset MIME type Service]**. Tippen Sie rechts neben dem Namen auf **[!UICONTROL Konfigurationswerte bearbeiten]** (Stiftsymbol).

   ![Bearbeiten Sie die Konfigurationswerte](assets/2019-08-02_16-44-56.png)

1. Klicken Sie auf der Seite **[!UICONTROL Adobe CQ Scene7 Asset MIME type Service]** auf ein beliebiges Pluszeichen `+`. Die Position in der Tabelle, an der Sie auf das Pluszeichen klicken, um den neuen MIME-Typ hinzuzufügen, ist unerheblich.

   ![Plus-Zeichen-Symbol](assets/2019-08-02_16-27-27.png)

1. Geben Sie `DWG=image/vnd.dwg` in das leere Textfeld ein, das Sie soeben hinzugefügt haben.

   Das Beispiel `DWG=image/vnd.dwg` dient nur zur Veranschaulichung. Der hier hinzugefügte MIME-Typ kann ein beliebiges anderes nicht unterstütztes Format sein.

   ![Beispiel für einen MIME-Typ](assets/2019-08-02_16-36-36.png)

1. Klicken Sie in der rechten unteren Ecke der Seite auf **[!UICONTROL Speichern]**.

   An dieser Stelle können Sie die Registerkarte des Browsers schließen, auf der die Seite „Adobe Experience Manager-Web-Konsolen-Konfiguration“ geöffnet ist.

1. Kehren Sie zur Browserregisterkarte zurück, auf der sich Ihre geöffnete Experience Manager-Konsole befindet.

1. Klicken Sie in Experience Manager auf **[!UICONTROL Tools > Allgemein > CRXDE Lite]**.

   ![CRXDE Lite](assets/2019-08-02_16-55-41.png)

1. Navigieren Sie in der linken Leiste zu:

   `conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`

1. Ziehen Sie den Mime-Typ `image_vnd.dwg` und legen Sie ihn direkt über `image_` in der Struktur ab.

   ![Mime-Typ ziehen](assets/CRXDELite_CQDOC-14627.png)

1. Wenn der MIME-Typ `image_vnd.dwg` noch in der Struktur ausgewählt ist, auf der Registerkarte **[!UICONTROL Eigenschaften]** in der Zeile **[!UICONTROL enabled]** unter der Spaltenüberschrift **[!UICONTROL value]**, klicken Sie bei gedrückter Dublette auf den Wert, um die Dropdown-Liste **[!UICONTROL value]** zu öffnen.

1. Geben Sie `false` in das Feld ein (oder wählen Sie `false` aus der Dropdown-Liste).

   ![False-Wert](assets/2019-08-02_16_60_30.png)

1. Klicken Sie in der oberen linken Ecke der Seite „CRXDE Lite“ auf **[!UICONTROL Alle speichern]**.

#### Erstellen von Stapelsatzvorgaben zum automatischen Erzeugen von Bild- und Rotationssets {#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets}

Verwenden Sie Stapelsatzvorgaben, um die Erstellung von Bildsätzen oder Rotationssets während des Hochladens von Assets in Dynamic Media zu automatisieren.

Definieren Sie zunächst die Benennungskonvention für die Gruppierung von Assets in einem Satz. Anschließend können Sie eine Stapelsatzvorgabe erstellen. Dabei handelt es sich um einen eindeutig benannten, in sich abgeschlossenen Satz von Anweisungen, der festlegt, wie der Satz unter Verwendung von Bildern erstellt wird, die den im Vorgabenrezept definierten Benennungsregeln entsprechen.

Wenn Sie Dateien hochladen, erstellt Dynamic Media automatisch einen Satz mit allen Dateien, die den definierten Benennungsregeln in den aktiven Vorgaben entsprechen.

**Konfigurieren der Standardbenennung**

Erstellen Sie eine Standardbenennungskonvention zur Verwendung in einem beliebigen Stapelsatzvorgaben-Rezept. Die in der Stapelsatzvorgabendefinition ausgewählte Standardbenennungsregel ist wahrscheinlich alles, was Ihre Firma zum Erstellen von Stapelsätzen benötigt. Eine Stapelsatzvorgabe wird erstellt, damit die von Ihnen definierte Standardbenennungskonvention verwendet wird. Sie können so viele Stapelsatzvorgaben mit alternativen, benutzerdefinierten Benennungskonventionen erstellen, wie für einen bestimmten Satz von Inhalten notwendig sind, sofern eine Ausnahme für die unternehmensspezifische Standardbenennung vorhanden ist.

Die Einrichtung einer Standardbenennungsregel ist für die Verwendung der Funktionen von Stapelsatzvorgaben nicht erforderlich, Sie können sie jedoch verwenden, um so viele Elemente Ihrer Benennungsregel zu definieren, die Sie in einem Satz gruppieren möchten. Dadurch wird die Erstellung von Stapelsätzen optimiert.

Alternativ können Sie **[!UICONTROL Ansichten-Code]** ohne verfügbare Formularfelder verwenden. Auf diese Ansicht erstellen Sie Ihre Benennungskonventionen ausschließlich mit regulären Ausdrücken.

Es stehen zwei Elemente zur Definition zur Verfügung: **[!UICONTROL Match]** und **[!UICONTROL Basisname]**. Mit diesen Feldern können Sie alle Elemente einer Benennungskonvention definieren und den Teil der Konvention identifizieren, der zum Benennen des Satzes verwendet wird, der diese Elemente enthält. Die Benennungsregel einer Firma kann für jedes dieser Elemente eine oder mehrere Definitionszeilen verwenden. Verwenden Sie so viele Zeilen für Ihre eindeutige Definition und gruppieren Sie sie in unterschiedliche Elemente. Beispiel: &quot;Hauptbild&quot;, &quot;Farbelement&quot;, &quot;Alternative Ansicht&quot;und &quot;Muster&quot;.

**So konfigurieren Sie die Standardbenennung:**

1. Öffnen Sie das [Dynamic Media Classic-Desktop-Programm](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started) und melden Sie sich bei Ihrem Konto an.

   Ihre Benutzer- und Anmeldedaten haben Sie zum Zeitpunkt der Bereitstellung von Adobe erhalten. Wenn Ihnen die Informationen nicht vorliegen, wenden Sie sich an den technischen Support.

1. Tippen Sie in der Navigationsleiste im oberen Seitenbereich auf **[!UICONTROL Einrichtung > Anwendungseinstellungen > Stapelsatzvorgaben > Standardbenennung].**
1. Wählen Sie **[!UICONTROL Formular anzeigen]** oder **[!UICONTROL Code anzeigen]**, um die gewünschte Ansicht festzulegen, und geben Sie Informationen zu den einzelnen Elementen ein.

   Sie können das Kontrollkästchen **[!UICONTROL Code anzeigen]** aktivieren, um die Erstellung des regelmäßigen Ausdruckswerts neben Ihren Formularauswahlen anzuzeigen. Sie können diese Werte nach Bedarf eingeben oder ändern. Dies hilft Ihnen bei der Definition der Elemente der Benennungsdefinition, falls Sie aus irgendeinem Grund durch die Formularansicht eingeschränkt werden. Falls Ihre Werte in der Formularansicht nicht analysiert werden können, werden die Formularfelder inaktiv.

   >[!NOTE]
   >
   >Bei deaktivierten Formularfeldern erfolgt keine Überprüfung, ob Ihre regelmäßigen Ausdrücke korrekt sind. Ergebnisse des regelmäßigen Ausdrucks, den Sie für jedes Element erstellen, werden nach der Zeile „Ergebnis“ angezeigt. Der vollständige regelmäßige Ausdruck wird am unteren Seitenrand angezeigt.

1. Erweitern Sie die Elemente bei Bedarf und geben Sie die zu verwendenden Benennungsregeln ein.
1. Führen Sie ggf. einen der folgenden Schritte aus:

   * Tippen Sie auf **[!UICONTROL Hinzufügen]**, um eine weitere Benennungsregel für ein Element hinzuzufügen.
   * Tippen Sie auf **[!UICONTROL Entfernen]**, um eine Benennungsregel für ein Element zu löschen.

1. Führen Sie einen der folgenden Schritte aus:

   * Tippen Sie auf **[!UICONTROL Speichern unter]** und geben Sie einen Namen für die Vorgabe ein.
   * Wenn Sie eine vorhandene Vorgabe bearbeiten, tippen Sie auf **[!UICONTROL Speichern]**.

**Erstellen einer Stapelsatzvorgabe**

Dynamic Media verwendet Stapelsatzvorgaben, um Assets für die Anzeige in Viewern in Bildsätzen (alternative Bilder, Farboptionen, 360°-Drehung) zu organisieren. Die Stapelsatzvorgaben werden automatisch parallel zu den Asset-Uploadprozessen in Dynamic Media ausgeführt.

Sie können Ihre Stapelsatzvorgaben erstellen, bearbeiten und verwalten. Es gibt zwei Formen von Stapelsatzvorgabendefinitionen: eine für eine von Ihnen eingerichtete Standardbenennungsregel und eine für benutzerdefinierte Benennungsregeln, die Sie spontan erstellen.

Sie können zum Definieren einer Stapelsatzvorgabe entweder die Formularfeldmethode oder die Codemethode verwenden, die Ihnen die Verwendung regelmäßiger Ausdrücke ermöglicht. Wie bei der Standardbenennung können Sie [!UICONTROL Ansichten-Code] gleichzeitig in der [!UICONTROL Form-Ansicht] definieren und Ihre Definitionen mit regulären Ausdrücken erstellen. Als Alternative können Sie eine der Ansichten deaktivieren, um die andere ausschließlich zu verwenden.

**So erstellen Sie eine Stapelsatzvorgabe:**

1. Öffnen Sie das [Dynamic Media Classic-Desktop-Programm](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started) und melden Sie sich bei Ihrem Konto an.

   Ihre Benutzer- und Anmeldedaten haben Sie zum Zeitpunkt der Bereitstellung von Adobe erhalten. Wenn Ihnen die Informationen nicht vorliegen, wenden Sie sich an den technischen Support.

1. Tippen Sie in der Navigationsleiste im oberen Seitenbereich auf **[!UICONTROL Einrichtung > Anwendungseinstellungen > Stapelsatzvorgaben > Stapelsatzvorgabe].**

   [!UICONTROL Ansicht Form], wie in der rechten oberen Ecke der   Detailseite eingestellt, ist die Standardeinstellung für die Ansicht.

1. Tippen Sie im Bedienfeld &quot;Liste der Vorgabe&quot;auf **[!UICONTROL Hinzufügen]**, um die Definitionsfelder im Bedienfeld **[!UICONTROL Details]** auf der rechten Seite des Bildschirms zu aktivieren.
1. Geben Sie im Bereich **[!UICONTROL Details]** im Feld **[!UICONTROL Vorgabenname]** einen Namen für die Vorgabe ein.
1. Wählen Sie im Dropdownmenü **[!UICONTROL Stapelsatztyp]** einen Vorgabentyp aus.
1. Führen Sie einen der folgenden Schritte aus:

   * Wenn Sie eine standardmäßige Benennungskonvention verwenden, die Sie zuvor unter **[!UICONTROL Anwendungseinstellungen > Stapelsatzvorgaben > Standardbenennung]** eingerichtet haben, erweitern Sie **[!UICONTROL Asset-Benennungsregeln]****** und klicken Sie anschließend in der Dropdown-Liste auf **[!UICONTROL Standard]**.
   * Um beim Einrichten der Vorgabe eine neue Benennungskonvention zu definieren, klicken Sie auf **[!UICONTROL Konventionen für die Asset-Benennung]** und klicken Sie dann in der Dropdown-Liste **[!UICONTROL Dateibenennung]** auf **[!UICONTROL Benutzerdefiniert]**.

1. Definieren Sie für [!UICONTROL Sequenzreihenfolge] die Reihenfolge, in der Bilder angezeigt werden, nachdem der Satz in Dynamic Media gruppiert wurde.

   Die Assets werden standardmäßig in alphanumerischer Reihenfolge angeordnet. Sie können jedoch auch eine durch Kommas getrennte Liste mit regulären Ausdrücken verwenden, um die Reihenfolge anzupassen.

1. Geben Sie für **[!UICONTROL Benennen]** und **[!UICONTROL Erstellungskonvention]** das Suffix oder Präfix an den Basisnamen an, den Sie in der **[!UICONTROL Asset-Benennungskonvention]** definiert haben. Definieren Sie außerdem, wo der Satz in der Dynamic Media-Ordnerstruktur erstellt wird.

   Wenn Sie eine große Anzahl von Sätzen definieren, sollten Sie diese getrennt von den Ordnern halten, die die Assets selbst enthalten. Erstellen Sie beispielsweise einen Ordner &quot;Bildsätze&quot;und legen Sie hier die generierten Bildsätze ab.

1. Tippen Sie im Bedienfeld **[!UICONTROL Details]** auf **[!UICONTROL Speichern]**.
1. Tippen Sie neben dem neuen Vorgabenamen auf **[!UICONTROL Aktiv]**.

   Durch das Aktivieren dieser Vorgabe wird sichergestellt, dass beim Hochladen von Assets in Dynamic Media die Stapelsatzvorgabe zur Erstellung des Satzes angewendet wird.

**Erstellen einer Stapelsatzvorgabe für die automatische Erstellung eines 2D-Rotationssets**

Sie können den Stapelsatztyp **[!UICONTROL Multiachsen-Rotationsset]** verwenden, um ein „Rezept“ zu erstellen, das die Erstellung von 2D-Rotations-Sets automatisiert. Für die Gruppierung von Bildern werden die regulären Ausdrücke „Zeile“ und „Spalte“ verwendet, sodass die Bild-Assets im multidimensionalen Array korrekt an der entsprechenden Position ausgerichtet werden. Es gibt keine Mindest- oder Maximalzahl an Reihen und Spalten, die in einem Multiachsen-Rotationsset vorhanden sein müssen.

Beispiel: Sie möchten ein Multiachsen-Rotationsset mit dem Namen `spin-2dspin` erstellen. Sie haben einen Satz von Rotationsset-Bildern, die drei Zeilen mit 12 Bildern pro Zeile enthalten. Die Bilder haben die folgenden Namen:

```
spin-01-01 
 spin-01-02 
 … 
 spin-01-12 
 spin-02-01 
 … 
 spin-03-12
```

Mit diesen Informationen kann Ihr [!UICONTROL Stapelsatztyp]-Rezept wie folgt erstellt werden:

![chlimage_1-1](assets/chlimage_1-1.png)

Die Gruppierung für den Teil des gemeinsamen Asset-Namens des Rotationssets wird dem Feld **[!UICONTROL Übereinstimmung]** hinzugefügt (wie hervorgehoben). Der variable Teil des Asset-Namens, der die Zeile und Spalte enthält, wird den Feldern **[!UICONTROL Zeile]** bzw. **[!UICONTROL Spalte]** hinzugefügt.

Wenn das Rotationsset hochgeladen und veröffentlicht wird, aktivieren Sie den Namen des 2D-Rotationssets-Rezepts, das unter **[!UICONTROL Stapelsatzvorgaben]** im Dialogfeld **[!UICONTROL Upload-Auftragsoptionen]** aufgeführt ist.

**So erstellen Sie eine Stapelsatzvorgabe für die automatische Erstellung eines 2D-Rotations-Sets:**

1. Öffnen Sie das [Dynamic Media Classic-Desktop-Programm](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started) und melden Sie sich bei Ihrem Konto an.

   Ihre Benutzer- und Anmeldedaten haben Sie zum Zeitpunkt der Bereitstellung von Adobe erhalten. Wenn Ihnen die Informationen nicht vorliegen, wenden Sie sich an den technischen Support.

1. Tippen Sie in der Navigationsleiste im oberen Seitenbereich auf **[!UICONTROL Einrichtung > Anwendungseinstellungen > Stapelsatzvorgaben > Stapelsatzvorgabe]**.

   [!UICONTROL Ansicht Form], wie in der rechten oberen Ecke der   Detailseite eingestellt, ist die Standardeinstellung für die Ansicht.

1. Tippen Sie im Bedienfeld **[!UICONTROL Vorgabe-Liste]** auf **[!UICONTROL Hinzufügen]**, um die Definitionsfelder im Bedienfeld **[!UICONTROL Details]** auf der rechten Seite des Bildschirms zu aktivieren.
1. Geben Sie im Bereich **[!UICONTROL Details]** im Feld [!UICONTROL Vorgabenname] einen Namen für die Vorgabe ein.
1. Wählen Sie im Dropdownmenü **[!UICONTROL Stapelsatztyp]** **[!UICONTROL Asset-Set]**.
1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Untertyp]** **[!UICONTROL Multiachsen-Rotationsset]**.
1. Erweitern Sie **[!UICONTROL Asset-Benennungsregeln]** und klicken Sie dann in der Dropdown-Liste **[!UICONTROL Dateibenennung]** auf **[!UICONTROL Benutzerdefiniert]**.
1. Verwenden Sie die Attribute **[!UICONTROL Übereinstimmung]** und optional **[!UICONTROL Basisname]**, um einen regulären Ausdruck für die Benennung von Bild-Assets zu definieren, aus denen die Gruppierung besteht.

   So könnte der reguläre Ausdruck &quot;Literal Übereinstimmung&quot;z. B. wie folgt aussehen:

   `(w+)-w+-w+`

1. Erweitern Sie **[!UICONTROL Zeilen-/Spaltenposition]** und definieren Sie anschließend den Namen des Formats für die Position des Bild-Assets innerhalb des 2D-Rotationsset-Arrays.

   Setzen Sie die Zeilen- oder Spaltenposition im Dateinamen in Klammern.

   So könnte der reguläre Ausdruck Ihrer Zeile z. B. wie folgt aussehen:

   `\w+-R([0-9]+)-\w+`

   oder

   `\w+-(\d+)-\w+`

   Der reguläre Ausdruck Ihrer Spalte könnte wie folgt aussehen:

   `\w+-\w+-C([0-9]+)`

   oder

   `\w+-\w+-C(\d+)`

   Beachten Sie, dass diese Ausdrücke nur zu Veranschaulichungszwecken dienen. Sie können reguläre Ausdrücke Ihren Bedürfnissen entsprechend erstellen.

   >[!NOTE]
   >
   >Wenn die Kombination aus regulären Ausdrücken für Zeilen und Spalten die Position des Assets im multidimensionalen Rotationsset-Array nicht bestimmen kann, wird dieses Asset nicht dem Satz hinzugefügt und ein Fehler wird protokolliert.

1. Geben Sie für **[!UICONTROL Benennen]** und **[!UICONTROL Erstellungskonvention]** das Suffix oder Präfix an den Basisnamen an, den Sie in der **[!UICONTROL Asset-Benennungskonvention]** definiert haben.

   Definieren Sie außerdem, wo das Rotationsset in der Dynamic Media Classic-Ordnerstruktur erstellt wird.

   Wenn Sie eine große Anzahl von Sätzen definieren, sollten Sie diese getrennt von den Ordnern halten, die die Assets selbst enthalten. Dazu erstellen Sie beispielsweise einen Ordner namens „Rotationssets“ und weisen die Anwendung an, generierte Sätze hier abzulegen.

1. Tippen Sie im Bedienfeld **[!UICONTROL Details]** auf **[!UICONTROL Speichern]**.
1. Tippen Sie neben dem neuen Vorgabenamen auf **[!UICONTROL Aktiv]**.

   Durch das Aktivieren dieser Vorgabe wird sichergestellt, dass beim Hochladen von Assets in Dynamic Media die Stapelsatzvorgabe zur Erstellung des Satzes angewendet wird.

### (Optional) Steigern der Leistung von Dynamic Media – Scene7-Modus  {#optional-tuning-the-performance-of-dynamic-media-scene-mode}

Damit der Dynamic Media - Scene7-Modus reibungslos ausgeführt werden kann, empfiehlt Adobe die folgenden Tipps zur Synchronisierungsleistung/Skalierbarkeit:

* Aktualisieren der vordefinierten Auftragsparameter zur Verarbeitung verschiedener Dateiformate.
* Aktualisieren der vordefinierten Warteschlangen-Workerthreads des Granite-Workflows (Video-Assets).
* Aktualisieren der vordefinierten Warteschlangen-Workerthreads des Granite-Verlaufs-Workflows (Bilder und Nicht-Video-Assets).
* Aktualisieren der maximalen Upload-Verbindungen mit dem Dynamic Media Classic-Server.

#### Aktualisieren der vordefinierten Auftragsparameter zur Verarbeitung verschiedener Dateiformate.

Beim Hochladen von Dateien können Sie die Auftragsparameter für eine schnellere Verarbeitung anpassen. Wenn Sie beispielsweise PSD-Dateien hochladen, diese aber nicht als Vorlagen verarbeiten möchten, können Sie die Ebenendatei auf &quot;false&quot;(Aus) setzen. In diesem Fall wird der Parameter für den angepassten Auftrag wie folgt angezeigt: `process=None&createTemplate=false`.

Wenn Sie die Vorlagenerstellung aktivieren möchten, verwenden Sie die folgenden Parameter: `process=MaintainLayers&layerNaming=AppendName&createTemplate=true`.

<!-- REMOVED BASED ON CQDOC-17657 You can tune job parameters for faster processing when you upload files. For example, if you are uploading PSD files, but do not want to process them as templates, you can set layer extraction to false (off). In such case, the tuned job parameter would appear as `process=None&createTemplate=false`. -->

Adobe empfiehlt die Verwendung der folgenden &quot;angepassten&quot;Auftragsparameter für PDF-, PostScript®- und PSD-Dateien:

<!-- OLD PDF JOB PARAMETERS `pdfprocess=Rasterize&resolution=150&colorspace=Auto&pdfbrochure=false&keywords=false&links=false` -->

<!-- OLD POSTSCRIPT JOB PARAMETERS `psprocess=Rasterize&psresolution=150&pscolorspace=Auto&psalpha=false&psextractsearchwords=false&aiprocess=Rasterize&airesolution=150&aicolorspace=Auto&aialpha=false` -->

| Dateityp | Empfohlene Auftragsparameter |
| ---| ---|
| PDF | `pdfprocess=Thumbnail&resolution=150&colorspace=Auto&pdfbrochure=false&keywords=false&links=false` |
| PostScript® | `psprocess=Rasterize&psresolution=150&pscolorspace=Auto&psalpha=false&psextractsearchwords=false&aiprocess=Thumbnail&airesolution=150&aicolorspace=Auto&aialpha=false` |
| PSD | `process=None&layerNaming=AppendName&anchor=Center&createTemplate=false&extractText=false&extendLayers=false` |

<!-- CQDOC-17657 for PSD entry in table above -->

Um einen dieser Parameter zu aktualisieren, führen Sie die Schritte unter [Unterstützung von MIME-typbasierten Assets/Dynamic Media Classic-Upload-Auftragsparametern](/help/sites-administering/scene7.md#enabling-mime-type-based-assets-scene-upload-job-parameter-support) aus.

#### Aktualisieren der Verlaufs-Workflow-Warteschlange von Granite {#updating-the-granite-transient-workflow-queue}

Die Transit-Workflow-Warteschlange von Granite wird für den Workflow **[!UICONTROL DAM-Update-Asset]** verwendet. In Dynamic Media wird sie für die Bildaufnahme und -verarbeitung genutzt.

**So aktualisieren Sie die Verlaufs-Workflow-Warteschlange von Granite**

1. Navigieren Sie zu [https://&lt;Server>/system/console/configMgr](http://localhost:4502/system/console/configMgr) und suchen Sie nach **[!UICONTROL Warteschlange: Warteschlange für die Granite-Übergangs-Workflows]**.

   >[!NOTE]
   >
   >Anstelle einer direkten URL ist eine Textsuche erforderlich, da die OSGi-PID dynamisch generiert wird.

1. Ändern Sie im Feld **[!UICONTROL Maximale Anzahl an parallelen Aufträgen]** die Zahl in den gewünschten Wert.

   Sie können **[!UICONTROL Maximale Anzahl an parallelen Aufträgen]** erhöhen, um das Hochladen von Dateien zu Dynamic Media angemessen zu unterstützen. Der genaue Wert hängt von der Hardwarekapazität ab. In bestimmten Szenarien, z. B. einer ersten Migration oder einem einmaligen Massen-Upload, können Sie einen großen Wert verwenden. Beachten Sie jedoch, dass die Verwendung eines hohen Werts (z. B. die zweifache Anzahl der Kerne) negative Auswirkungen auf andere gleichzeitige Aktivitäten haben kann. Testen Sie daher den Wert und passen Sie ihn je nach Anwendungsfall an.

<!--    By default, the maximum number of parallel jobs depends on the number of available CPU cores. For example, on a 4-core server, it assigns 2 worker threads. (A value between 0.0 and 1.0 is ratio based, or any numbers greater than 1 will assign the number of worker threads.)

   Adobe recommends that 32 **[!UICONTROL Maximum Parallel Jobs]** be configured to adequately support heavy upload of files to Dynamic Media Classic. -->

![chlimage_1](assets/chlimage_1.jpeg)

1. Tippen Sie auf **[!UICONTROL Speichern]**.

#### Aktualisieren der Granite-Workflow-Warteschlange {#updating-the-granite-workflow-queue}

Die Granite-Workflow-Warteschlange wird für Workflows ohne Verlauf verwendet. In Dynamic Media wurden Videos mit dem Arbeitsablauf **[!UICONTROL Dynamic Media Encode Video]** verarbeitet.

**So aktualisieren Sie die Granite-Workflow-Warteschlange:**

1. Navigieren Sie zu `https://<server>/system/console/configMgr` und suchen Sie nach **[!UICONTROL Warteschlange: Granite-Workflow-Warteschlange]**.

   >[!NOTE]
   >
   >Anstelle einer direkten URL ist eine Textsuche erforderlich, da die OSGi-PID dynamisch generiert wird.

1. Ändern Sie im Feld **[!UICONTROL Maximale Anzahl an parallelen Aufträgen]** die Zahl in den gewünschten Wert.

   Die maximale Anzahl der parallelen Aufträge hängt standardmäßig von der Anzahl der verfügbaren CPU-Kerne ab. Auf einem 4-Core-Server werden beispielsweise zwei Arbeitsthreads zugewiesen. (Ein Wert zwischen 0,0 und 1,0 basiert auf einem Quotienten oder eine Zahl größer als 1 weist die Anzahl der Arbeitsthreads zu.)

   In den meisten Fällen ist die Standardeinstellung 0,5 ausreichend.

   ![chlimage_1-1](assets/chlimage_1-1.jpeg)

1. Tippen Sie auf **[!UICONTROL Speichern]**.

#### Aktualisieren der Scene7-Upload-Verbindung {#updating-the-scene-upload-connection}

Die Einstellung &quot;Scene7-Upload-Verbindung&quot;synchronisiert Experience Manager-Assets mit Dynamic Media Classic-Servern.

**So aktualisieren Sie die Scene7-Upload-Verbindung:**

1. Navigieren Sie zu `https://<server>/system/console/configMgr/com.day.cq.dam.scene7.impl.Scene7UploadServiceImpl`
1. Ändern Sie im Feld [!UICONTROL Anzahl der Verbindungen] und/oder im Feld [!UICONTROL Zeitüberschreitung bei aktiven Aufträgen] den Wert in die gewünschte Anzahl.

   Die Einstellung **[!UICONTROL Anzahl der Verbindungen]** steuert die maximale Anzahl an HTTP-Verbindungen, die für den Experience Manager zum Hochladen von Dynamic Media zulässig sind. In der Regel ist der vordefinierte Wert von zehn Verbindungen ausreichend.

   Die Einstellung **[!UICONTROL Zeitüberschreitung bei aktiven Aufträgen]** legt die Wartezeit für hochgeladene Dynamic Media-Assets bis zur Veröffentlichung auf dem Übermittlungs-Server fest. Dieser Wert beträgt standardmäßig 2.100 Sekunden oder 35 Minuten.

   In den meisten Fällen ist die Einstellung „2100“ausreichend.

   ![chlimage_1-2](assets/chlimage_1-2.jpeg)

1. Tippen Sie auf **[!UICONTROL Speichern]**.

### (Optional) Filtern von Assets für die Replizierung {#optional-filtering-assets-for-replication}

In Nicht-Dynamic Media-Bereitstellungen replizieren Sie *alle*-Elemente (sowohl Bilder als auch Videos) aus Ihrer Experience Manager-Author-Umgebung in den Veröffentlichungsknoten des Experience Managers. Dieser Arbeitsablauf ist erforderlich, da die Experience Manager-Veröffentlichungsserver auch die Assets bereitstellen.

Da Assets jedoch über den Cloud Service bereitgestellt werden, müssen diese Assets in Dynamic Media-Bereitstellungen nicht an Experience Manager Publish-Knoten repliziert werden. Ein solcher Arbeitsablauf für &quot;Hybrid-Veröffentlichung&quot;vermeidet zusätzliche Kosten für die Datenspeicherung und längere Verarbeitungszeiten für die Replizierung von Assets. Andere Inhalte, wie z. B. Site-Seiten, werden weiterhin von den Veröffentlichungsknoten des Experience Managers bereitgestellt.

Die Filter bieten Ihnen die Möglichkeit, *Assets von der Replizierung auf den Veröffentlichungsknoten des Experience Managers auszuschließen.*

#### Verwenden von Asset-Standardfiltern für die Replikation {#using-default-asset-filters-for-replication}

Wenn Sie Dynamic Media für die Bildbearbeitung, Videomaterial oder beides verwenden, können Sie die standardmäßigen Filter verwenden, die die Adobe bereitstellt. Folgende Filter sind standardmäßig aktiviert:

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td><strong>Filter</strong></td> 
   <td><strong>Mimetype</strong></td> 
   <td><strong>Ausgabeformate</strong></td> 
  </tr> 
  <tr> 
   <td>Dynamic Media Image Versand</td> 
   <td><p>filter-images</p> <p>filter-sets</p> <p> </p> </td> 
   <td><p>Beginn mit <strong>image/</strong></p> <p>Enthält <strong>application/</strong> und endet mit <strong>set</strong>.</p> </td> 
   <td>Die vordefinierten "Filterbilder"(gilt für Einzelbilder, einschließlich interaktiver Bilder) und "Filtersätze"(gilt für Rotationssets, Bildsätze, gemischte Mediensets und Karussell-Sets) werden wie folgt ausgeführt: 
    <ul> 
     <li>Das Originalbild und statische Bildausgabeformate werden von der Replikation ausgeschlossen.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Dynamic Media Video Versand</td> 
   <td>filter-video</td> 
   <td>Beginn mit <strong>video/</strong></td> 
   <td>Das vordefinierte "filter-video" wird: 
    <ul> 
     <li>Von der Replikation ausschließen Sie die ursprünglichen Video- und statischen Miniaturdarstellungen. <br /> <br /> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Filter gelten für MIME-Typen und können nicht pfadspezifisch sein.

#### Anpassen von Asset-Filtern für die Replikation {#customizing-asset-filters-for-replication}

1. Tippen Sie in Experience Manager auf das Logo des Experience Managers, um auf die globale Navigationskonsole zuzugreifen, und dann auf das Symbol **[!UICONTROL Tools]** und navigieren Sie zu **[!UICONTROL Allgemein > CRXDE Lite]**.
1. Navigieren Sie im linken Ordnerbaum zu `/etc/replication/agents.author/publish/jcr:content/damRenditionFilters`, um die Filter zu überprüfen.

   ![chlimage_1-2](assets/chlimage_1-2.png)

1. Zum Definieren des MIME-Typs für den Filter können Sie den MIME-Typ wie folgt ermitteln:

   Erweitern Sie in der linken Leiste **[!UICONTROL content > dam > &lt;`locate_your_asset` > jcr:content > metadata]** und suchen Sie in der Tabelle **[!UICONTROL dc:format]**.

   Die folgende Grafik ist ein Beispiel für den Pfad eines Assets zu „dc:format“.

   ![chlimage_1-3](assets/chlimage_1-3.png)

   Beachten Sie, dass `dc:format` für das Asset `Fiji Red.jpg` `image/jpeg`  lautet.

   Damit dieser Filter für alle Bilder unabhängig von ihrem Format gilt, setzen Sie den Wert auf `image/*`, wobei `*` ein regulärer Ausdruck ist, der auf alle Bilder eines beliebigen Formats angewendet wird.

   Damit der Filter nur auf Bilder vom Typ JPEG angewendet werden kann, geben Sie den Wert `image/jpeg` ein.

1. Definieren Sie, welche Darstellungen Sie von der Replizierung ausschließen möchten.

   Sie können die folgenden Zeichen verwenden, um einen Filtervorgang für die Replikation durchzuführen:

   <table> 
    <tbody> 
    <tr> 
    <td><strong>Zu verwendendes Zeichen</strong></td> 
    <td><strong>So werden Assets für die Replizierung Filter</strong></td> 
    </tr> 
    <tr> 
    <td>*</td> 
    <td>Platzhalterzeichen<br /> </td> 
    </tr> 
    <tr> 
    <td>+</td> 
    <td>Umfasst Elemente für die Replikation.</td> 
    </tr> 
    <tr> 
    <td>-</td> 
    <td>Schließt Assets von der Replikation aus.</td> 
    </tr> 
    </tbody> 
   </table>

   Navigieren Sie zu **content/dam/&lt;`locate your asset`/jcr:content/renditions**.

   Die folgende Grafik ist ein Beispiel für die Wiedergabeformate eines Assets.

   ![chlimage_1-4](assets/chlimage_1-4.png)

   Wenn Sie nur das Original replizieren möchten, geben Sie `+original` ein.
