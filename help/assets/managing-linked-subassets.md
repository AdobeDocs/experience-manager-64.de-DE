---
title: Verwalten Sie zusammengesetzte Assets und erstellen Sie Teilassets.
description: Erfahren Sie, wie Sie Verweise auf AEM Assets aus InDesign-, Adobe Illustrator- und Photoshop-Dateien erstellen. Darüber hinaus erfahren Sie, wie Sie mit der Funktion „Seitenanzeige“ einzelne Seiten mehrseitiger Dateien, darunter PDF-, INDD-, PPT-, PPTX- und AI-Dateien, anzeigen können.
contentOwner: AG
feature: Asset Management
role: Business Practitioner,Administrator
translation-type: tm+mt
source-git-commit: e46a27a1ba11b4a5973eb1ece02c8594b2ae0fc9
workflow-type: tm+mt
source-wordcount: '1415'
ht-degree: 47%

---


# Verwalten von zusammengesetzten Assets mit Teilassets {#managing-compound-assets}

Adobe Experience Manager (AEM) Assets kann erkennen, ob eine hochgeladene Datei Referenzen zu Assets enthält, die bereits im Repository vorhanden sind. Diese Funktion ist nur für unterstützte Dateiformate verfügbar. Wenn das hochgeladene Asset Referenzen zu AEM-Assets enthält, wird eine bidirektionale Verknüpfung zwischen dem hochgeladenen Asset und den referenzierten Assets erstellt.

Durch die Referenzierung von AEM-Assets in Adobe Creative Cloud-Anwendungen wird Redundanz beseitigt und die Zusammenarbeit verbessert. Außerdem werden die Effizienz und Produktivität der Benutzer gesteigert.

AEM Assets unterstützt die **bidirektionale Referenzierung**. Referenzierte Assets finden Sie auf der Asset-Detailseite der hochgeladenen Datei. Darüber hinaus finden Sie die referenzierenden Dateien für AEM-Assets auf der Asset-Detailseite des referenzierten Assets.

Referenzen werden auf der Grundlage von Pfad, Dokument-ID und Instanz-ID der referenzierten Assets aufgelöst.

## Adobe Illustrator: hinzufügen von Assets als Verweise {#refai}

Sie können vorhandene AEM-Assets aus einer Adobe Illustrator-Datei referenzieren.

1. Verwenden Sie das [AEM-Desktop-Programm](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=de), um das AEM Asset-Repository als Laufwerk auf Ihrem lokalen Rechner einzubinden. Navigieren Sie im bereitgestellten Laufwerk zum Speicherort des Assets, das Sie referenzieren möchten.
1. Ziehen Sie das Asset vom bereitgestellten Laufwerk auf die Illustrator-Datei.
1. Speichern Sie die Illustrator-Datei im bereitgestellten Laufwerk oder [laden](managing-assets-touch-ui.md#uploading-assets) Sie sie in das AEM-Repository hoch.
1. Nachdem der Workflow abgeschlossen ist, navigieren Sie zur Detailseite für das Asset. Die Referenzen zu vorhandenen AEM-Assets werden unter **[!UICONTROL Abhängigkeiten]** in der Spalte **[!UICONTROL Verweise]** aufgeführt.

   ![chlimage_1-258](assets/chlimage_1-258.png)

1. Es ist auch möglich, dass andere Dateien als die aktuelle Datei auf die referenzierten Assets verweisen, die unter **[!UICONTROL Abhängigkeiten]** angezeigt werden. Um eine Liste der referenzierenden Dateien für ein Asset anzuzeigen, klicken Sie unter **[!UICONTROL Abhängigkeiten]** auf das Asset.

   ![chlimage_1-259](assets/chlimage_1-259.png)

1. Klicken Sie in der Symbolleiste auf das Symbol **[!UICONTROL Eigenschaften anzeigen]**. Auf der Seite „Eigenschaften“ wird die Liste der Dateien, die das aktuelle Asset referenzieren, auf der Registerkarte **[!UICONTROL Allgemein]** unter der Spalte **[!UICONTROL Verweise]** angezeigt.

   ![chlimage_1-260](assets/chlimage_1-260.png)

## Adobe InDesign: hinzufügen von Assets als Verweise {#add-aem-assets-as-references-in-adobe-indesign}

Um AEM-Assets aus einer InDesign-Datei zu referenzieren, ziehen Sie die AEM-Assets auf die InDesign-Datei oder exportieren Sie die InDesign-Datei als ZIP-Datei.

Referenzierte Assets sind bereits in AEM Assets enthalten. Sie können Teilassets nach [configure InDesign server](indesign.md) extrahieren. Eingebettete Assets in einer InDesign-Datei werden als Teil-Assets extrahiert.

>[!NOTE]
>
>Wenn der InDesign-Server als Proxyserver dient, wird die Vorschau der InDesign-Dateien innerhalb der XMP-Metadaten eingebettet. In diesem Fall ist die Extraktion von Miniaturen nicht explizit erforderlich. Wenn der InDesign-Server nicht als Proxyserver fungiert, müssen Miniaturen für InDesign-Dateien explizit extrahiert werden.

Beim Hochladen einer INDD-Datei werden die Verweise abgerufen, indem Assets mit der Eigenschaft `xmpMM:InstanceID` und `xmpMM:DocumentID` im Repository abgefragt werden.

### Erstellen von Verweisen durch Ziehen von Assets {#create-references-by-dragging-aem-assets}

Dieses Verfahren ist ähnlich wie [Hinzufügen Assets als Referenzen in Adobe Illustrator](#refai).

### Erstellen von Referenzen zu Assets durch Exportieren einer ZIP-Datei {#create-references-to-aem-assets-by-exporting-a-zip-file}

1. Führen Sie die Schritte unter [Erstellen von Workflow-Modellen](/help/sites-developing/workflows-models.md) aus, um einen neuen Workflow zu erstellen.
1. Verwenden Sie die Paketfunktion von Adobe InDesign](https://helpx.adobe.com/indesign/how-to/indesign-package-files-for-handoff.html), um das Dokument zu exportieren. Adobe InDesign kann ein Dokument und die verknüpften Assets als Paket exportieren. [ In diesem Fall enthält der exportierte Ordner den Ordner `Links`, der Unterelemente in der InDesign-Datei enthält. Der Ordner `Links` befindet sich im selben Ordner wie die INDD-Datei.
1. Erstellen Sie eine ZIP-Datei und laden Sie sie in das AEM-Repository hoch.
1. Starten Sie den Unarchiver-Workflow.
1. Wenn der Workflow abgeschlossen ist, werden die Referenzen im Link-Ordner automatisch als Teil-Assets referenziert. Um eine Liste der referenzierten Assets anzuzeigen, navigieren Sie zur Asset-Detailseite des InDesign-Assets und schließen Sie die [Leiste](/help/sites-authoring/basic-handling.md#rail-selector).

## Adobe Photoshop: hinzufügen von Assets als Verweise {#refps}

1. Mit einem WebDAV-Client installieren Sie AEM Assets als Laufwerk.
1. Um Referenzen zu AEM-Assets in einer Photoshop-Datei zu erstellen, navigieren Sie im bereitgestellten Laufwerk zu den entsprechenden Assets mit der Funktion „Verknüpftes Smartobjekt platzieren“ in Photoshop.

   ![chlimage_1-261](assets/chlimage_1-261.png)

1. Speichern Sie die Datei in Photoshop auf dem gemounteten Laufwerk oder [upload](managing-assets-touch-ui.md#uploading-assets) in das AEM Repository.
1. Nach Abschluss des Workflows werden die Referenzen zu vorhandenen AEM-Assets auf der Asset-Detailseite aufgeführt.

   Rufen Sie die referenzierten Assets auf, indem Sie die [Leiste](/help/sites-authoring/basic-handling.md#rail-selector) auf der Asset-Detailseite schließen.

1. Die referenzierten Assets enthalten auch die Liste der Assets, auf die sie verwiesen werden. Um eine Liste referenzierter Assets Ansicht, navigieren Sie zur Seite mit den Asset-Details und schließen Sie die Leiste [Leiste](/help/sites-authoring/basic-handling.md#rail-selector).

>[!NOTE]
>
>Die Assets innerhalb der ebenenübergreifenden Assets können ebenfalls basierend auf ihrer Dokument-ID und ihrer Instanz-ID referenziert werden. Diese Funktion ist nur in Adobe Illustrator und Adobe Photoshop verfügbar. Bei anderen Versionen erfolgt die Referenzierung basierend auf dem relativen Pfad von verknüpften Assets im ebenenübergreifenden Haupt-Asset, wie das auch bei früheren Versionen von AEM der Fall ist.

## Erstellen von Teilassets {#generate-subassets}

Für die unterstützten Assets mit mehrseitigen Formaten — PDF-Dateien, AI-Dateien, Microsoft PowerPoint- und Apple Keynote-Dateien und Adobe InDesign-Dateien — AEM können Teilassets generieren, die den einzelnen Seiten des ursprünglichen Assets entsprechen. Diese Teilassets sind mit dem Element *parent* verknüpft und erleichtern die mehrseitige Ansicht. Für alle anderen Zwecke werden die Teilassachen in AEM wie normale Vermögenswerte behandelt.

Die Erstellung von Unter-Assets ist standardmäßig deaktiviert. Gehen Sie wie folgt vor, um die Erzeugung von Teilassets zu aktivieren:

1. Melden Sie sich bei Experience Manager als Administrator an. Öffnen Sie **[!UICONTROL Werkzeuge > Workflow > Modelle]**.
1. Wählen Sie den Workflow **[!UICONTROL DAM-Update-Asset]** und klicken Sie auf **[!UICONTROL Bearbeiten]**.
1. Klicken Sie auf **[!UICONTROL Seitliches Bedienfeld]** ein/aus und suchen Sie den Schritt **[!UICONTROL Unterasset]** erstellen. hinzufügen den Schritt zum Workflow. Klicken Sie auf **[!UICONTROL Synchronisieren]**.

Führen Sie zum Generieren der Teilassets einen der folgenden Schritte aus:

* Neue Assets: Der Workflow [!UICONTROL DAM Update Assets] wird für jedes neue Asset ausgeführt, das in AEM hochgeladen wird. Teilassets werden automatisch für neue mehrseitige Assets generiert.
* Vorhandene mehrseitige Assets: Führen Sie den Workflow [!UICONTROL DAM Update Assets] manuell aus, indem Sie einen der folgenden Schritte ausführen:

   * Wählen Sie ein Asset aus und klicken Sie auf [!UICONTROL Zeitschiene], um das linke Bedienfeld zu öffnen. Verwenden Sie alternativ den Tastaturbefehl `alt + 3`. Klicken Sie auf [!UICONTROL Beginn-Workflow], wählen Sie [!UICONTROL DAM-Update-Asset], klicken Sie auf [!UICONTROL Beginn] und klicken Sie auf [!UICONTROL Fortfahren].
   * Wählen Sie ein Asset aus und klicken Sie in der Symbolleiste auf [!UICONTROL Erstellen > Workflow]. Wählen Sie im Popup-Dialogfeld [!UICONTROL DAM-Update-Asset]-Arbeitsablauf, klicken Sie auf [!UICONTROL Beginn] und klicken Sie auf [!UICONTROL Fortfahren].

Führen Sie insbesondere für Microsoft Word-Dokumente den Arbeitsablauf **[!UICONTROL DAM Parse Word-Dokumente]** aus. Es wird eine `cq:Page`-Komponente aus dem Inhalt des Microsoft Word-Dokuments generiert. Die `cq:Page`-Komponente verweist auf die aus dem Dokument extrahierten Bilder. Diese Bilder werden auch dann extrahiert, wenn die Erstellung von Unter-Assets deaktiviert ist.

## Anzeigen von Unter-Assets {#viewing-subassets}

Die Teilassets werden nur angezeigt, wenn die Teilassets generiert wurden und für das ausgewählte mehrseitige Asset verfügbar sind. Um die generierten Teilassets Ansicht, öffnen Sie das mehrseitige Asset. Klicken Sie im oberen linken Seitenbereich auf das Symbol ![Linke Leiste](assets/do-not-localize/aem_leftrail_contentonly.png) und klicken Sie in der Liste auf **[!UICONTROL Teilassets]**. Wenn Sie **[!UICONTROL Subassets]** aus der Liste auswählen. Verwenden Sie alternativ den Tastaturbefehl `alt + 5`.

![Ansichten-Teilassets für ein mehrseitiges Asset](assets/view_subassets_simulation.gif)

## Anzeigen von Seiten einer mehrseitigen Datei  {#view-pages-of-a-multi-page-file}

Sie können eine mehrseitige Datei, wie z. B. PDF, INDD, PPT, PPTX und AI, mit der Seitenanzeigefunktion von AEM Assets Ansicht werden. Öffnen Sie ein mehrseitiges Asset und klicken Sie auf **[!UICONTROL Ansichten]** oben links auf der Seite. Der daraufhin geöffnete Seiten-Viewer zeigt die Seiten des Assets und die Steuerelemente zum Durchsuchen und Zoomen der einzelnen Seiten an.

![Ansicht und Anzeige von Seiten eines mehrseitigen Assets](assets/view_multipage_asset_fmr.gif)

In InDesign können Sie Seiten mithilfe des InDesign-Servers extrahieren. Wenn die Vorschau von Seiten bei der Erstellung einer InDesign-Datei gespeichert wird, ist der InDesign-Server nicht für die Seitenextraktion erforderlich.

Die folgenden Optionen stehen in der Symbolleiste, in der linken Leiste und in den Seiten-Viewer-Steuerelementen zur Verfügung:

* **[!UICONTROL Desktop-]** Aktionen zum Öffnen oder Einblenden eines bestimmten Teilassets mit AEM Desktop-App. Erfahren Sie, wie Sie mit AEM Desktop-App Desktop-Aktionen konfigurieren können.[](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=en#desktopactions-v2)

* **[!UICONTROL Mit]** der Option &quot;Eigenschaften&quot;wird die Seite &quot;  Eigenschaften&quot;des jeweiligen Unterassets geöffnet.

* **[!UICONTROL Mit der]** Option &quot;Annotator&quot;können Sie das spezifische Unterelement kommentieren. Die Anmerkungen, die Sie in separaten Teilassets verwenden, werden zusammen erfasst und angezeigt, wenn das übergeordnete Asset zur Ansicht geöffnet wird.

* **[!UICONTROL Die Option &quot;Seitenübersicht&quot;]** zeigt alle Teilassets gleichzeitig an.

* **[!UICONTROL Die]** Option &quot;Zeitablauf&quot;in der linken Leiste nach dem Klicken auf das Symbol für die  ![linke Leiste ](assets/do-not-localize/aem_leftrail_contentonly.png) zeigt den Dateistream an.

## Bewährte Verfahren und Einschränkungen {#best-practice-limitation-tips}

* Die Erzeugung von Teilassets kann bei jeder Bereitstellung von Experience Managern sehr ressourcenintensiv sein. Wenn Sie beim Hochladen komplexer Assets Teilassets generieren, fügen Sie den Schritt im DAM-Arbeitsablauf zum Aktualisieren von Assets hinzu. Wenn Sie bei Bedarf Teilassets erstellen, erstellen Sie einen separaten Workflow, um Teilassets zu generieren. Ein dedizierter Arbeitsablauf ermöglicht es Ihnen, die anderen Schritte im DAM Update Asset-Arbeitsablauf zu überspringen und Rechenressourcen zu speichern.

>[!MORELIKETHIS]
>
>* [Verwenden des Adobe Experience Manager-Desktop-Programms](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=de)

