---
title: Verwalten von ebenenübergreifenden Assets und Generieren von Unter-Assets.
description: Erfahren Sie, wie Sie Verweise auf [!DNL Experience Manager] Assets aus InDesign-, Adobe Illustrator- und Photoshop-Dateien erstellen. Erfahren Sie außerdem, wie Sie mit der Funktion "Seitenanzeige"einzelne Seiten mehrseitiger Dateien anzeigen können.
contentOwner: AG
feature: Asset Management
role: User,Admin
exl-id: 9fa44b26-76f7-48e2-a9df-4fd1c0074158
source-git-commit: 937c9425e276f67486fba1d4563799fe68d35cc7
workflow-type: tm+mt
source-wordcount: '1377'
ht-degree: 29%

---

# Verwalten von ebenenübergreifenden Assets mit Unter-Assets {#managing-compound-assets}

Adobe Experience Manager Assets kann erkennen, ob eine hochgeladene Datei Verweise auf Assets enthält, die bereits im Repository vorhanden sind. Diese Funktion ist nur für unterstützte Dateiformate verfügbar. Wenn das hochgeladene Asset Verweise auf [!DNL Experience Manager]-Assets enthält, wird eine bidirektionale Verknüpfung zwischen den hochgeladenen und den referenzierten Assets erstellt.

Die Referenzierung von [!DNL Experience Manager]-Assets in Adobe Creative Cloud-Anwendungen sorgt nicht nur für Redundanz, sondern verbessert auch die Zusammenarbeit und erhöht die Effizienz und Produktivität der Benutzer.

[!DNL Experience Manager] Assets unterstützt  **bidirektionale Referenzierung**. Referenzierte Assets finden Sie auf der Asset-Detailseite der hochgeladenen Datei. Darüber hinaus können Sie die referenzierenden Dateien für [!DNL Experience Manager]-Assets auf der Asset-Detailseite des referenzierten Assets anzeigen.

Referenzen werden auf der Grundlage von Pfad, Dokument-ID und Instanz-ID der referenzierten Assets aufgelöst.

## Adobe Illustrator: Hinzufügen von Assets als Referenzen {#refai}

Sie können vorhandene [!DNL Experience Manager]-Assets aus einer Adobe Illustrator-Datei referenzieren.

1. Stellen Sie mithilfe des [[!DNL Experience Manager] Desktop-Programms](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=de) das [!DNL Experience Manager]-Asset-Repository als Laufwerk auf Ihrem lokalen Computer bereit. Navigieren Sie im bereitgestellten Laufwerk zum Speicherort des Assets, das Sie referenzieren möchten.
1. Ziehen Sie das Asset vom bereitgestellten Laufwerk auf die Illustrator-Datei.
1. Speichern Sie die Illustrator-Datei auf dem bereitgestellten Laufwerk oder [laden Sie](managing-assets-touch-ui.md#uploading-assets) in das [!DNL Experience Manager]-Repository hoch.
1. Nachdem der Workflow abgeschlossen ist, navigieren Sie zur Detailseite für das Asset. Die Verweise auf vorhandene [!DNL Experience Manager]-Assets werden unter **[!UICONTROL Abhängigkeiten]** in der Spalte **[!UICONTROL Verweise]** aufgeführt.

   ![chlimage_1-258](assets/chlimage_1-258.png)

1. Es ist auch möglich, dass andere Dateien als die aktuelle Datei auf die referenzierten Assets verweisen, die unter **[!UICONTROL Abhängigkeiten]** angezeigt werden. Um eine Liste der referenzierenden Dateien für ein Asset anzuzeigen, klicken Sie unter **[!UICONTROL Abhängigkeiten]** auf das Asset.

   ![chlimage_1-259](assets/chlimage_1-259.png)

1. Klicken Sie in der Symbolleiste auf das Symbol **[!UICONTROL Eigenschaften anzeigen]**. Auf der Seite „Eigenschaften“ wird die Liste der Dateien, die das aktuelle Asset referenzieren, auf der Registerkarte **[!UICONTROL Allgemein]** unter der Spalte **[!UICONTROL Verweise]** angezeigt.

   ![chlimage_1-260](assets/chlimage_1-260.png)

## Adobe InDesign: Hinzufügen von Assets als Referenzen {#add-aem-assets-as-references-in-adobe-indesign}

Um auf [!DNL Experience Manager]-Assets aus einer InDesign-Datei zu verweisen, ziehen Sie entweder [!DNL Experience Manager]-Assets in die InDesign-Datei oder exportieren Sie die InDesign-Datei als ZIP-Datei.

Referenzierte Assets sind bereits in [!DNL Experience Manager] Assets vorhanden. Sie können Unter-Assets nach [Konfigurieren des InDesign-Servers](indesign.md) extrahieren. Eingebettete Assets in einer InDesign-Datei werden als Teil-Assets extrahiert.

>[!NOTE]
>
>Wenn der InDesign-Server als Proxyserver dient, wird die Vorschau der InDesign-Dateien innerhalb der XMP-Metadaten eingebettet. In diesem Fall ist die Extraktion von Miniaturen nicht explizit erforderlich. Wenn der InDesign-Server nicht als Proxyserver fungiert, müssen Miniaturen für InDesign-Dateien explizit extrahiert werden.

Wenn eine INDD-Datei hochgeladen wird, werden die Verweise abgerufen, indem Assets mit der Eigenschaft `xmpMM:InstanceID` und `xmpMM:DocumentID` im Repository abgefragt werden.

### Erstellen von Referenzen durch Ziehen von Assets {#create-references-by-dragging-aem-assets}

Dieses Verfahren ähnelt [Hinzufügen von Assets als Referenzen in Adobe Illustrator](#refai).

### Erstellen von Referenzen zu Assets durch Exportieren einer ZIP-Datei {#create-references-to-aem-assets-by-exporting-a-zip-file}

1. Führen Sie die Schritte unter [Erstellen von Workflow-Modellen](/help/sites-developing/workflows-models.md) aus, um einen neuen Workflow zu erstellen.
1. Verwenden Sie die Paketfunktion von Adobe InDesign](https://helpx.adobe.com/indesign/how-to/indesign-package-files-for-handoff.html), um das Dokument zu exportieren. Adobe InDesign kann ein Dokument und die verknüpften Assets als Paket exportieren. [ In diesem Fall enthält der exportierte Ordner einen Ordner `Links`, der Teil-Assets in der InDesign-Datei enthält. Der Ordner `Links` befindet sich im selben Ordner wie die INDD-Datei.
1. Erstellen Sie eine ZIP-Datei und laden Sie sie in das [!DNL Experience Manager]-Repository hoch.
1. Starten Sie den Unarchiver-Workflow.
1. Wenn der Workflow abgeschlossen ist, werden die Referenzen im Link-Ordner automatisch als Teil-Assets referenziert. Um eine Liste der referenzierten Assets anzuzeigen, navigieren Sie zur Asset-Detailseite des InDesign-Assets und schließen Sie die [Leiste](/help/sites-authoring/basic-handling.md#rail-selector).

## Adobe Photoshop: Hinzufügen von Assets als Referenzen {#refps}

1. Stellen Sie mithilfe eines WebDav-Clients [!DNL Experience Manager] Assets als Laufwerk bereit.
1. Um Verweise auf [!DNL Experience Manager]-Assets in einer Photoshop-Datei zu erstellen, navigieren Sie mithilfe der Funktion Verknüpftes platzieren in Photoshop zu den entsprechenden Assets im bereitgestellten Laufwerk.

   ![chlimage_1-261](assets/chlimage_1-261.png)

1. Speichern Sie die Datei in Photoshop auf dem bereitgestellten Laufwerk oder [laden Sie](managing-assets-touch-ui.md#uploading-assets) in das [!DNL Experience Manager]-Repository hoch.
1. Nach Abschluss des Workflows werden die Verweise auf vorhandene [!DNL Experience Manager]-Assets auf der Asset-Detailseite aufgelistet.

   Rufen Sie die referenzierten Assets auf, indem Sie die [Leiste](/help/sites-authoring/basic-handling.md#rail-selector) auf der Asset-Detailseite schließen.

1. Die referenzierten Assets enthalten auch die Liste der Assets, von denen sie referenziert werden. Um eine Liste der referenzierten Assets anzuzeigen, navigieren Sie zur Asset-Detailseite und schließen Sie die Leiste [Leiste](/help/sites-authoring/basic-handling.md#rail-selector).

>[!NOTE]
>
>Die Assets innerhalb der ebenenübergreifenden Assets können ebenfalls basierend auf ihrer Dokument-ID und ihrer Instanz-ID referenziert werden. Diese Funktion ist nur in Adobe Illustrator und Adobe Photoshop verfügbar. Bei anderen Versionen erfolgt die Referenzierung basierend auf dem relativen Pfad von verknüpften Assets im ebenenübergreifenden Haupt-Asset, wie das auch bei früheren Versionen von AEM der Fall ist.

## Erstellen von Unter-Assets {#generate-subassets}

Für die unterstützten Assets mit mehrseitigen Formaten - PDF-Dateien, AI-Dateien, Microsoft PowerPoint- und Apple Keynote-Dateien und Adobe InDesign-Dateien - kann [!DNL Experience Manager] Teil-Assets generieren, die jeder einzelnen Seite des ursprünglichen Assets entsprechen. Diese Teil-Assets sind mit dem *übergeordneten*-Asset verknüpft und erleichtern die mehrseitige Ansicht. Für alle anderen Zwecke werden die Unter-Assets wie normale Assets in AEM behandelt.

Die Erstellung von Unter-Assets ist standardmäßig deaktiviert. Gehen Sie wie folgt vor, um die Erstellung von Unter-Assets zu aktivieren:

1. Melden Sie sich bei Experience Manager als Administrator an. Rufen Sie **[!UICONTROL Tools > Workflow > Modelle]** auf.
1. Wählen Sie den Workflow **[!UICONTROL DAM Update Asset]** aus und klicken Sie auf **[!UICONTROL Bearbeiten]**.
1. Klicken Sie auf **[!UICONTROL Seitliches Bedienfeld ein/aus]** und suchen Sie den Schritt **[!UICONTROL Untergeordnetes Asset erstellen]** . Fügen Sie den Schritt zum Workflow hinzu. Klicken Sie auf **[!UICONTROL Synchronisieren]**.

Führen Sie einen der folgenden Schritte aus, um die Unter-Assets zu generieren:

* Neue Assets: Der Workflow [!UICONTROL DAM-Update-Assets] wird für jedes neue Asset ausgeführt, das in AEM hochgeladen wird. Teil-Assets werden automatisch für neue mehrseitige Assets generiert.
* Vorhandene mehrseitige Assets: Führen Sie den Workflow [!UICONTROL DAM Update Assets] manuell aus, indem Sie einen der folgenden Schritte ausführen:

   * Wählen Sie ein Asset aus und klicken Sie auf [!UICONTROL Timeline] , um das linke Bedienfeld zu öffnen. Verwenden Sie alternativ den Tastaturbefehl `alt + 3`. Klicken Sie auf [!UICONTROL Workflow starten], wählen Sie [!UICONTROL DAM Update Asset], klicken Sie auf [!UICONTROL Start] und klicken Sie auf [!UICONTROL Weiter].
   * Wählen Sie ein Asset aus und klicken Sie in der Symbolleiste auf [!UICONTROL Erstellen > Workflow] . Wählen Sie im Popup-Dialogfeld den Workflow [!UICONTROL DAM Update Asset] aus, klicken Sie auf [!UICONTROL Start] und klicken Sie auf [!UICONTROL Weiter].

Führen Sie insbesondere für Microsoft Word-Dokumente den Workflow **[!UICONTROL DAM Parse Word Documents]** aus. Es wird eine `cq:Page`-Komponente aus dem Inhalt des Microsoft Word-Dokuments generiert. Die `cq:Page`-Komponente verweist auf die aus dem Dokument extrahierten Bilder. Diese Bilder werden auch dann extrahiert, wenn die Erstellung von Unter-Assets deaktiviert ist.

## Anzeigen von Unter-Assets {#viewing-subassets}

Die Teil-Assets werden nur angezeigt, wenn die Teil-Assets generiert wurden und für das ausgewählte mehrseitige Asset verfügbar sind. Um die generierten Teil-Assets anzuzeigen, öffnen Sie das mehrseitige Asset. Klicken Sie oben links auf der Seite auf das Symbol ![Linke Leiste](assets/do-not-localize/aem_leftrail_contentonly.png) und klicken Sie in der Liste auf **[!UICONTROL Unter-Assets]** . Wenn Sie **[!UICONTROL Unter-Assets]** aus der Liste auswählen. Verwenden Sie alternativ den Tastaturbefehl `alt + 5`.

![Anzeigen von Unter-Assets für ein mehrseitiges Asset](assets/view_subassets_simulation.gif)

## Anzeigen von Seiten einer mehrseitigen Datei  {#view-pages-of-a-multi-page-file}

Sie können eine mehrseitige Datei, z. B. PDF, INDD, PPT, PPTX und AI-Datei, mit der Funktion &quot;Seiten-Viewer&quot;von [!DNL Experience Manager] Assets anzeigen. Öffnen Sie ein mehrseitiges Asset und klicken Sie oben links auf der Seite auf **[!UICONTROL Seiten anzeigen]** . Der daraufhin geöffnete Seiten-Viewer zeigt die Seiten des Assets und die Steuerelemente zum Durchsuchen und Zoomen der einzelnen Seiten an.

![Anzeigen und Anzeigen von Seiten eines mehrseitigen Assets](assets/view_multipage_asset_fmr.gif)

In InDesign können Sie Seiten mithilfe des InDesign-Servers extrahieren. Wenn die Vorschau von Seiten bei der Erstellung einer InDesign-Datei gespeichert wird, ist der InDesign-Server nicht für die Seitenextraktion erforderlich.

Die folgenden Optionen sind in der Symbolleiste, in der linken Leiste und in den Steuerelementen des Seiten-Viewers verfügbar:

* **[!UICONTROL Desktop-]** Aktionen zum Öffnen oder Anzeigen eines bestimmten Unter-Assets mithilfe des  [!DNL Experience Manager] Desktop-Programms. Erfahren Sie, wie Sie [Desktop-Aktionen](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=de#desktopactions-v2) konfigurieren, wenn Sie das [!DNL Experience Manager]-Desktop-Programm verwenden.

* **** Eigenschaften-Option öffnet die   Eigenschaftsseite des jeweiligen Unter-Assets.

* **** Mit der Option &quot;Anmerken&quot;können Sie das spezifische Unter-Asset kommentieren. Die Anmerkungen, die Sie für separate Unter-Assets verwenden, werden erfasst und zusammen angezeigt, wenn das übergeordnete Asset zur Anzeige geöffnet wird.

* **[!UICONTROL Die Option]** &quot;Seitenübersicht&quot;zeigt alle Teil-Assets gleichzeitig an.

* **** Die Zeitleistenoption in der linken Leiste nach dem Klicken auf die  ![linke Leiste ](assets/do-not-localize/aem_leftrail_contentonly.png) zeigt den Aktivitäts-Stream für die Datei an.

## Best Practices und Einschränkungen {#best-practice-limitation-tips}

* Die Erstellung von Unter-Assets kann bei jeder Experience Manager-Bereitstellung sehr ressourcenintensiv sein. Wenn Sie Teil-Assets generieren, wenn komplexe Assets hochgeladen werden, fügen Sie den Schritt im Workflow DAM-Update-Asset hinzu. Wenn Sie Teil-Assets On-Demand generieren, erstellen Sie einen separaten Workflow zum Generieren von Teil-Assets. Mit einem speziellen Workflow können Sie die anderen Schritte im Workflow DAM-Update-Asset überspringen und Rechenressourcen speichern.

>[!MORELIKETHIS]
>
>* [Verwenden des Adobe Experience Manager-Desktop-Programms](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=de)

