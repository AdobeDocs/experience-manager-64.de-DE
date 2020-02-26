---
title: 'Verwalten von zusammengesetzten Assets und '
description: Hier erfahren Sie, wie Sie Verweise auf AEM-Assets aus InDesign-, Adobe Illustrator- und Fotoshop-Dateien erstellen. Darüber hinaus erfahren Sie, wie Sie mit der Funktion „Seitenanzeige“ einzelne Seiten mehrseitiger Dateien, darunter PDF, INDD, PPT, PPTX und Ai-Dateien, anzeigen können.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 28ebd6c7648e4f32203e20dbc8a7d7f205acb740

---


# Verwalten von zusammengesetzten Assets mit Teilassets {#managing-compound-assets}

Adobe Experience Manager (AEM) Assets kann erkennen, ob eine hochgeladene Datei Referenzen zu Assets enthält, die bereits im Repository vorhanden sind. Diese Funktion ist nur für unterstützte Dateiformate verfügbar. Wenn das hochgeladene Asset Referenzen zu AEM-Assets enthält, wird eine bidirektionale Verknüpfung zwischen dem hochgeladenen Asset und den referenzierten Assets erstellt.

Durch die Referenzierung von AEM-Assets in Adobe Creative Cloud-Anwendungen wird Redundanz beseitigt und die Zusammenarbeit verbessert. Außerdem werden die Effizienz und Produktivität der Benutzer gesteigert.

AEM Assets supports **bidirectional referencing**. Referenzierte Assets finden Sie auf der Asset-Detailseite der hochgeladenen Datei. Darüber hinaus finden Sie die referenzierenden Dateien für AEM-Assets auf der Asset-Detailseite des referenzierten Assets.

Referenzen werden auf der Grundlage von Pfad, Dokument-ID und Instanz-ID der referenzierten Assets aufgelöst.

## Hinzufügen von AEM-Assets als Referenzen in Adobe Illustrator {#refai}

Sie können vorhandene AEM-Assets aus einer Adobe Illustrator-Datei referenzieren.

1. Using [AEM desktop app](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html), mount AEM Assets repository as a drive on your local machine. Navigieren Sie im bereitgestellten Laufwerk zum Speicherort des Assets, das Sie referenzieren möchten.
1. Ziehen Sie das Asset vom bereitgestellten Laufwerk auf die Illustrator-Datei.
1. Save the Illustrator file to the mounted drive, or [upload](managing-assets-touch-ui.md#uploading-assets) to the AEM repository.
1. Wenn der Workflow abgeschlossen ist, navigieren Sie zur Detailseite für das Asset. Die Referenzen zu vorhandenen AEM-Assets werden unter **[!UICONTROL Abhängigkeiten]** in der Spalte **[!UICONTROL Verweise]** aufgeführt.

   ![chlimage_1-258](assets/chlimage_1-258.png)

1. The referenced assets that appear under **[!UICONTROL Dependencies]** can also be referenced by files other than the current one. Um eine Liste der referenzierenden Dateien für ein Asset anzuzeigen, klicken Sie unter **[!UICONTROL Abhängigkeiten]** auf das Asset.

   ![chlimage_1-259](assets/chlimage_1-259.png)

1. Click the **[!UICONTROL View Properties]** icon from the toolbar. Auf der Seite „Eigenschaften“ wird die Liste der Dateien, die das aktuelle Asset referenzieren, auf der Registerkarte **[!UICONTROL Allgemein]** unter der Spalte **[!UICONTROL Verweise]** angezeigt.

   ![chlimage_1-260](assets/chlimage_1-260.png)

## Hinzufügen von AEM-Assets als Referenzen in Adobe InDesign {#add-aem-assets-as-references-in-adobe-indesign}

Um auf AEM-Assets aus einer InDesign-Datei zu verweisen, ziehen Sie entweder AEM-Assets in die InDesign-Datei oder exportieren Sie die InDesign-Datei als ZIP-Datei.

Referenzierte Assets sind bereits in AEM Assets enthalten. You can extract subassets by [configure InDesign server](indesign.md). Eingebettete Assets in einer InDesign-Datei werden als Teilassets extrahiert.

>[!NOTE]
>
>Wenn der InDesign-Server als Proxyserver dient, wird die Vorschau der InDesign-Dateien innerhalb der XMP-Metadaten eingebettet. In diesem Fall ist die Extraktion von Miniaturen nicht explizit erforderlich. Wenn der InDesign-Server nicht als Proxyserver fungiert, müssen Miniaturen für InDesign-Dateien explizit extrahiert werden.

### Erstellen von Referenzen durch Ziehen von AEM-Assets {#create-references-by-dragging-aem-assets}

Dieses Verfahren weist Ähnlichkeiten zur in [Hinzufügen von AEM-Assets als Referenzen in Adobe Illustrator](#refai) beschriebenen Prozedur auf.

### Erstellen von Referenzen zu AEM-Assets durch Exportieren einer ZIP-Datei {#create-references-to-aem-assets-by-exporting-a-zip-file}

1. Perform the steps in [Creating Workflow Models](/help/sites-developing/workflows-models.md) to create a new workflow.
1. Verwenden Sie die Paketfunktion von Adobe InDesign, um das Dokument zu exportieren.Adobe InDesign kann ein Dokument und die verknüpften Assets als Paket exportieren. In diesem Fall enthält der exportierte Ordner den Ordner &quot;Links&quot;, der in der InDesign-Datei enthaltene Teilassets enthält.
1. Erstellen Sie eine ZIP-Datei und laden Sie sie in das AEM-Repository hoch.
1. Starten Sie den Unarchiver-Workflow.
1. When the workflow completes, the references in the Links folder are automatically referenced as subassets. To view a list of referred assets, navigate to the asset details page of the InDesign asset and close the [Rail](/help/sites-authoring/basic-handling.md#rail-selector).

## Hinzufügen von AEM-Assets als Referenzen in Adobe Photoshop {#refps}

1. Mit einem WebDAV-Client installieren Sie AEM Assets als Laufwerk.
1. Um Referenzen zu AEM-Assets in einer Photoshop-Datei zu erstellen, navigieren Sie im bereitgestellten Laufwerk zu den entsprechenden Assets mit der Funktion „Verknüpftes Smartobjekt platzieren“ in Photoshop.

   ![chlimage_1-261](assets/chlimage_1-261.png)

1. Save in Photoshop file to the mounted drive or or [upload](managing-assets-touch-ui.md#uploading-assets) to the AEM repository.
1. Nach Abschluss des Workflows werden die Verweise auf vorhandene AEM-Assets auf der Seite mit den Asset-Details aufgeführt.

   To view the referenced assets, close the [Rail](/help/sites-authoring/basic-handling.md#rail-selector) in the asset details page.

1. The referenced assets also contain the list of assets they are referenced from. To view a list of referenced assets, navigate to the asset details page and close the [rail](/help/sites-authoring/basic-handling.md#rail-selector).

>[!NOTE]
>
>Auf die Assets in zusammengesetzten Assets kann auch anhand ihrer Dokument-ID und Instanz-ID verwiesen werden. Diese Funktion ist nur in Adobe Illustrator und Adobe Photoshop verfügbar. Bei anderen Versionen erfolgt die Referenzierung basierend auf dem relativen Pfad von verknüpften Assets im ebenenübergreifenden Haupt-Asset, wie das auch bei früheren Versionen von AEM der Fall ist.

## Erstellen von Teilassets {#generate-subassets}

Für die unterstützten Assets mit mehrseitigen Formaten — PDF-Dateien, AI-Dateien, Microsoft PowerPoint- und Apple Keynote-Dateien und Adobe InDesign-Dateien — AEM kann Teilassets generieren, die jeder einzelnen Seite des ursprünglichen Assets entsprechen. Diese Teilassets sind mit dem *übergeordneten* Asset verknüpft und ermöglichen eine mehrseitige Ansicht. Für alle anderen Zwecke werden die Teilassets in AEM wie normale Assets behandelt.

Die Erstellung von Unter-Assets ist standardmäßig deaktiviert. Gehen Sie wie folgt vor, um die Erzeugung von Teilassets zu aktivieren:

1. Melden Sie sich bei Experience Manager als Administrator an. Access **[!UICONTROL Tools > Workflow > Models]**.
1. Wählen Sie **[!UICONTROL DAM Update Asset]** Workflow und klicken Sie auf **[!UICONTROL Bearbeiten]**.
1. Klicken Sie auf **[!UICONTROL Seitenbedienfeld]** umschalten und suchen Sie den Schritt &quot;Unterelement **[!UICONTROL erstellen&quot;]** . Fügen Sie den Schritt zum Workflow hinzu. Klicken Sie auf **[!UICONTROL Synchronisieren]**.

Führen Sie zum Generieren der Teilassets einen der folgenden Schritte aus:

* Neue Assets: Der Arbeitsablauf [!UICONTROL DAM-Aktualisierung für Assets] wird für jedes neue Asset ausgeführt, das auf AEM hochgeladen wird. Teilassets werden automatisch für neue mehrseitige Assets generiert.
* Vorhandene mehrseitige Assets: Führen Sie den Arbeitsablauf [!UICONTROL DAM Update Assets] manuell aus, wie folgt:

   * Wählen Sie ein Asset aus und klicken Sie auf [!UICONTROL Zeitschiene] , um das linke Bedienfeld zu öffnen. Verwenden Sie alternativ den Tastaturbefehl `alt + 3`. Klicken Sie auf Arbeitsablauf [!UICONTROL starten], wählen Sie [!UICONTROL DAM-Update-Asset], klicken Sie auf [!UICONTROL Start]und dann auf [!UICONTROL Fortfahren].
   * Wählen Sie ein Asset aus und klicken Sie in der Symbolleiste auf [!UICONTROL Erstellen > Workflow] . Wählen Sie im Popup-Dialogfeld [!UICONTROL DAM Update Asset] Workflow, klicken Sie auf [!UICONTROL Start]und dann auf [!UICONTROL Fortfahren].

Führen Sie insbesondere für Microsoft Word-Dokumente den Arbeitsablauf **[!UICONTROL DAM Parse Word Documents]** aus. Es wird eine `cq:Page` Komponente aus dem Inhalt des Microsoft Word-Dokuments generiert. The images extracted from the document are referenced from the `cq:Page` component. Diese Bilder werden auch dann extrahiert, wenn die Erstellung von Unter-Assets deaktiviert ist.

## View subassets {#viewing-subassets}

Die Teilassets werden nur angezeigt, wenn die Teilassets generiert wurden und für das ausgewählte mehrseitige Asset verfügbar sind. Um die generierten Teilassets anzuzeigen, öffnen Sie das mehrseitige Asset. Klicken Sie im oberen linken Bereich der Seite auf das Symbol![ für die ](assets/do-not-localize/aem_leftrail_contentonly.png)linke Leiste und klicken Sie in der Liste auf **[!UICONTROL Teilassets]** . Wenn Sie **[!UICONTROL Teilassets]** aus der Liste auswählen. Verwenden Sie alternativ den Tastaturbefehl `alt + 5`.

![Anzeigen von Teilassets für ein mehrseitiges Asset](assets/view_subassets_simulation.gif)

## Anzeigen von Seiten einer mehrseitigen Datei {#view-pages-of-a-multi-page-file}

Sie können eine mehrseitige Datei wie PDF-, INDD-, PPT-, PPTX- und AI-Datei mit der Funktion &quot;Seiten-Viewer&quot;von AEM Assets anzeigen. Öffnen Sie ein mehrseitiges Asset und klicken Sie in der oberen linken Ecke der Seite auf Seiten **[!UICONTROL anzeigen]** . Der daraufhin geöffnete Seiten-Viewer zeigt die Seiten des Assets und die Steuerelemente zum Durchsuchen und Zoomen der einzelnen Seiten an.

![Anzeigen und Anzeigen von Seiten eines mehrseitigen Assets](assets/view_multipage_asset_fmr.gif)

In InDesign können Sie Seiten mithilfe des InDesign-Servers extrahieren. Wenn die Vorschau von Seiten bei der Erstellung einer InDesign-Datei gespeichert wird, ist der InDesign-Server nicht für die Seitenextraktion erforderlich.

Die folgenden Optionen stehen in der Symbolleiste, in der linken Leiste und in den Seiten-Viewer-Steuerelementen zur Verfügung:

* **[!UICONTROL Desktop-Aktionen]** zum Öffnen oder Einblenden eines bestimmten Unterassets mit der AEM-Desktop-App. Erfahren Sie, wie Sie Desktop-Aktionen[ ](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html#desktopactions-v2)konfigurieren, wenn Sie die AEM-Desktop-App verwenden.

* **[!UICONTROL Mit der Option &quot;Eigenschaften]** &quot;wird die Seite &quot; [!UICONTROL Eigenschaften] &quot;des jeweiligen Unterassets geöffnet.

* **[!UICONTROL Mit der Option &quot;Anmerkung]** &quot;können Sie das spezifische Unterelement kommentieren. Die Anmerkungen, die Sie in separaten Teilassets verwenden, werden zusammen erfasst und angezeigt, wenn das übergeordnete Asset zur Ansicht geöffnet wird.

* **[!UICONTROL Die Option &quot;Seitenübersicht]** &quot;zeigt alle Teilassets gleichzeitig an.

* **[!UICONTROL Die Option Zeitschiene]** in der linken Leiste, nachdem auf das Symbol für die ![](assets/do-not-localize/aem_leftrail_contentonly.png) linke Leiste geklickt wurde, zeigt den Aktivitätsstream für die Datei an.
