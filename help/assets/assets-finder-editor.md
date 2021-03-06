---
title: Erstellen und Konfigurieren von Asset-Editor-Seiten
description: Erfahren Sie, wie Sie benutzerdefinierte Asset-Editor-Seiten erstellen und mehrere Assets gleichzeitig bearbeiten können.
contentOwner: AG
feature: Developer Tools,Asset Management
role: User,Admin
exl-id: 12899f61-9ceb-4bde-a501-6c50c93e3276
source-git-commit: 1679bbab6390808a1988cb6fe9b7692c3db31ae4
workflow-type: tm+mt
source-wordcount: '3300'
ht-degree: 76%

---

# Erstellen und Konfigurieren von Asset-Editor-Seiten {#creating-and-configuring-asset-editor-pages}

Dieses Dokument beschäftigt sich mit den folgenden Fragestellungen:

* Was spricht für die Erstellung angepasster Asset-Editor-Seiten?
* Wie werden Asset-Editor-Seiten erstellt und angepasst? (Hierbei handelt es sich um WCM-Seiten, mit denen Sie Metadaten anzeigen und bearbeiten sowie Aktionen für ein Asset ausführen können.)
* Wie werden mehrere Assets gleichzeitig bearbeitet?

>[!NOTE]
>
>Asset-Freigabe ist als Open-Source-Refrerenzimplementierung verfügbar. Siehe [Asset-Freigabe](https://adobe-marketing-cloud.github.io/asset-share-commons/). Wird nicht offiziell unterstützt.

## Was spricht für das Erstellen und Konfigurieren von Asset-Editor-Seiten? {#why-create-and-configure-asset-editor-pages}

Digital Asset Management wird in einer immer größeren Anzahl von Szenarien eingesetzt. Wenn Sie von einer kleinen Lösung für eine kleine Benutzergruppe professionell ausgebildeter Benutzer - wie Fotografen oder Taxonomen - zu größeren und vielfältigeren Benutzergruppen - wie z. B. Geschäftsbenutzer, WCM-Autoren, Journalisten usw. - zur leistungsstarken Benutzeroberfläche von [!DNL Adobe Experience Manager Assets] für professionelle Benutzer zu viele Informationen bereitstellen können und Interessengruppen beginnen, bestimmte Benutzeroberflächen oder Anwendungen für den Zugriff auf die digitalen Assets anzufordern, die für sie relevant sind.

Bei diesen Asset-orientierten Anwendungen kann es sich um einfache Fotogalerien im Internet handeln, über die Mitarbeiter Fotos von Messebesuchen hochladen können, oder um Pressezentren öffentlicher Websites, wie etwa hier im Geometrixx-Beispiel zu sehen. Asset-orientierte Anwendungen können sich auch auf Komplettlösungen, einschließlich Warenkorb, Kassen- und Prüfprozessen, erstrecken.

Eine Asset-orientierte Anwendung zu erstellen, wird so in erster Linie zu einem Konfigurationsvorgang, der keinerlei Kodierung erfordert. Sie müssen lediglich mit den Benutzergruppen, deren Bedürfnissen und den verwendeten Metadaten vertraut sein. Asset-orientierte Anwendungen, die mit [!DNL Assets] sind erweiterbar: Mit moderatem Kodierungsaufwand können wiederverwendbare Komponenten für die Suche, Anzeige und Änderung von Assets erstellt werden.

Eine Asset-orientierte Anwendung in [!DNL Experience Manager] besteht aus einer Asset-Editor-Seite, die verwendet werden kann, um eine detaillierte Ansicht eines bestimmten Assets zu erhalten. Über eine Asset-Editor-Seite können zudem Metadaten bearbeitet werden, sofern der Benutzer, der auf das Asset zugreift, über die erforderlichen Berechtigungen verfügt.

## Erstellen und Konfigurieren einer Asset-Freigabe-Seite {#creating-and-configuring-an-asset-share-page}

Sie können die DAM Finder-Funktionsweise anpassen und Seiten mit allen benötigten Funktionen erstellen. Diese Seiten werden als Asset-Freigabe-Seiten bezeichnet. Um eine neue Asset-Freigabe-Seite zu erstellen, fügen Sie zunächst die Seite mithilfe der Vorlage „Geometrixx-Asset-Freigabe“ hinzu. Sie können dann die von den Benutzern ausführbaren Aktionen anpassen, bestimmen, wie Assets dargestellt werden, und festlegen, wie Benutzer ihre Abfragen erstellen können.

Einige Anwendungsbeispiele zum Erstellen einer angepassten Asset-Freigabe-Seite:

* Pressezentrum für Journalisten
* Bildsuchmaschine für interne Geschäftsbenutzer
* Bilddatenbank für Website-Benutzer
* Medien-Tagging-Benutzeroberfläche für Metadaten-Editoren

### Erstellen einer Asset-Freigabe-Seite {#creating-an-asset-share-page}

Neue Asset-Freigabe-Seiten können entweder beim Arbeiten auf Websites oder über den Digital Asset Manager erstellt werden.

>[!NOTE]
>
>Standardmäßig werden beim Erstellen einer Asset-Freigabe-Seite über die Option **Neu** im Digital Asset Manager ein Asset-Viewer und ein Asset-Editor automatisch für Sie erstellt.

So erstellen Sie eine neue Asset-Freigabe-Seite in der **Websites-Konsole**:

1. Navigieren Sie auf der Registerkarte **[!UICONTROL Websites]** an die Stelle, an der eine Asset-Freigabe-Seite erstellt werden soll, und klicken Sie auf **[!UICONTROL Neu]**.

1. Wählen Sie die **[!UICONTROL Asset-Freigabe]** Seite und klicken Sie auf **[!UICONTROL Erstellen]**. Die neue Seite wird erstellt und die Asset-Freigabe-Seite wird auf der Registerkarte **[!UICONTROL Websites]** aufgeführt.

![dam8](assets/dam8.png)

Die mit der Geometrixx-DAM-Asset-Freigabe-Vorlage erstellte Standardseite sieht wie folgt aus:

![screen_shot_2012-04-18at115456am](assets/screen_shot_2012-04-18at115456am.png)

Die Asset-Freigabe-Seite kann über die Elemente aus dem Sidekick angepasst werden. Dabei können Sie auch die Query-Builder-Eigenschaften bearbeiten. Die Seite **[!UICONTROL Geometrixx Pressezentrum]** ist eine auf dieser Vorlage basierende angepasste Version einer Seite:

![screen_shot_2012-04-19at123048pm](assets/screen_shot_2012-04-19at123048pm.png)

So erstellen Sie eine neue Asset-Freigabe-Seite mit dem Digital Asset Manager:

1. Wählen Sie im Digital Asset Manager unter **[!UICONTROL Neu]** die Option **[!UICONTROL Neue Asset-Freigabe]**.
1. Geben Sie in das Feld **[!UICONTROL Titel]** den Namen der Asset-Freigabe-Seite ein. Geben Sie ggf. einen Namen für die URL ein.

   ![screen_shot_2012-04-19at23626pm](assets/screen_shot_2012-04-19at23626pm.png)

1. Doppelklicken Sie auf die Asset-Freigabe-Seite, um die Seite zu öffnen und zu konfigurieren.

   ![screen_shot_2012-04-19at24114pm](assets/screen_shot_2012-04-19at24114pm.png)

   Standardmäßig werden beim Erstellen einer Asset-Freigabe-Seite über die Option **[!UICONTROL Neu]** ein Asset-Viewer und ein Asset-Editor automatisch für Sie erstellt.

#### Aktionen anpassen {#customizing-actions}

Sie können anhand einer Auswahl vordefinierter Aktionen festlegen, welche Aktionen Benutzer für ausgewählte digitale Assets ausführen können.

So fügen Sie der Asset-Freigabe-Seite Aktionen hinzu:

1. Klicken Sie auf der anzupassenden Asset-Freigabe-Seite im Sidekick auf **[!UICONTROL Aktionen.]**

   Die folgenden Aktionen sind verfügbar:
   ![assetshare2](assets/assetshare2.bmp)

| Aktion | Beschreibung |
|---|---|
| [!UICONTROL Löschen-Aktion] | Benutzer können die ausgewählten Assets löschen. |
| [!UICONTROL Download-Aktion] | Ermöglicht Benutzern das Herunterladen ausgewählter Assets auf ihren Computern. |
| [!UICONTROL Lightbox-Aktion] | Speichert Assets in einer &quot;Lightbox&quot;, in der Sie andere Aktionen durchführen können. Dies ist praktisch, wenn über mehrere Seiten hinweg an Assets gearbeitet wird. Die Lightbox kann ebenfalls als Warenkorb für Assets verwendet werden. |
| [!UICONTROL Verschieben-Aktion] | Benutzer können das Asset an einen anderen Speicherort verschieben |
| [!UICONTROL Tags-Aktion] | Ermöglicht Benutzern das Hinzufügen von Tags zu ausgewählten Assets |
| [!UICONTROL Asset-Aktion anzeigen] | Öffnet das Asset im Asset-Editor zur Bearbeitung durch Benutzer. |

1. Ziehen Sie die entsprechende Aktion in den Bereich **Aktionen** auf der Seite. Hierdurch wird eine Schaltfläche zum Ausführen dieser Aktion erstellt.

   ![chlimage_1-387](assets/chlimage_1-387.png)

#### Ermitteln, wie Suchergebnisse angezeigt werden {#determining-how-search-results-are-presented}

Sie können über eine vordefinierte Liste von Linsen bestimmen, wie Ergebnisse gezeigt werden.

So ändern Sie die Anzeige von Suchergebnissen:

1. Klicken Sie auf der anzupassenden Asset-Freigabe-Seite auf **[!UICONTROL Suchen]**.

   ![chlimage_1](assets/chlimage_1.bmp)

1. Ziehen Sie die entsprechende Linse in den oberen Seitenbereich. Im Pressezentrum sind die Linsen bereits verfügbar. Durch Auswahl des entsprechenden Linsensymbols können Benutzer die Suchergebnisse wie gewünscht anzeigen.

Folgende Linsen sind verfügbar:

| Objektiv | Beschreibung |
|---|---|
| **[!UICONTROL Listenlinse]** | Stellt die Assets in Listenform mit Details dar. |
| **[!UICONTROL Mosaik-Linse]** | Stellt Assets in Mosaik dar. |

#### Mosaik-Linse {#mosaic-lens}

![chlimage_1-388](assets/chlimage_1-388.png)

#### Listenlinse {#list-lens}

![chlimage_1-389](assets/chlimage_1-389.png)

#### Query Builder anpassen {#customizing-the-query-builder}

Über den Query Builder können Sie Suchbegriffe eingeben und Inhalt für die Asset-Freigabe-Seite erstellen. Wenn Sie den Query Builder bearbeiten, können Sie auch festlegen, wie viele Suchergebnisse pro Seite angezeigt werden und welcher Asset-Editor beim Doppelklicken auf ein Asset geöffnet wird. Außerdem können Sie den Pfad bestimmen, der über die Abfrage durchsucht wird, und wie Knotentypen angepasst werden.

So passen Sie den Query Builder an:

1. Klicken Sie auf der anzupassenden Asset-Freigabe-Seite im Query Builder auf **[!UICONTROL Bearbeiten]**. Standardmäßig wird die Registerkarte **[!UICONTROL Allgemein]** geöffnet.

1. Wählen Sie die Anzahl der Ergebnisse pro Seite, den Pfad des Asset-Editors (im Falle eines angepassten Asset-Editors) und den Aktionstitel aus.

   ![screen_shot_2012-04-23at15055pm](assets/screen_shot_2012-04-23at15055pm.png)

1. Klicken Sie auf die Registerkarte **[!UICONTROL Pfade]**. Geben Sie einen Pfad oder mehrere Pfade zum Ausführen des Suchvorgangs ein. Diese Pfade werden überschrieben, wenn der Benutzer die Pfad-Eigenschaft verwendet.

   ![screen_shot_2012-04-23at15150pm](assets/screen_shot_2012-04-23at15150pm.png)

1. Geben Sie ggf. einen weiteren Knotentyp ein.

1. Im Feld **[!UICONTROL Query-Builder-URL]** können Sie den Query Builder überschreiben oder umschließen und neue Servlet-URLs mit dem vorhandenen Query Builder eingeben. Im Feld **[!UICONTROL Feed-URL]** können Sie zudem die Feed-URL überschreiben.

   ![screen_shot_2012-04-23at15313pm](assets/screen_shot_2012-04-23at15313pm.png)

1. In das Feld **[!UICONTROL Text]** können Sie den für die Ergebnisse anzuzeigenden Text und die Seitenzahlen der Ergebnisse eingeben. Klicken Sie auf **[!UICONTROL OK]**, wenn Sie keine weiteren Änderungen vornehmen möchten.

   ![screen_shot_2012-04-23at15300pm](assets/screen_shot_2012-04-23at15300pm.png)

#### Hinzufügen von Prädikaten {#adding-predicates}

[!DNL Experience Manager Assets] beinhaltet eine Reihe von Eigenschaften, die Sie der Asset-Freigabe-Seite hinzufügen können. So können Benutzer Suchvorgänge weiter eingrenzen. Mitunter können sie auch einen Query-Builder-Parameter (etwa den Pfad-Parameter) überschreiben.

So fügen Sie Eigenschaften hinzu:

1. Klicken Sie auf der anzupassenden Asset-Freigabe-Seite auf **[!UICONTROL Suchen]**.

   ![assetshare3](assets/assetshare3.bmp)

1. Ziehen Sie die entsprechenden Eigenschaften auf die Asset-Freigabe-Seite unterhalb des Query Builders. Hierdurch werden die entsprechenden Felder erstellt.

   ![assetshare4](assets/assetshare4.bmp)

   Die folgenden Eigenschaften sind verfügbar:

| Prädikat | Beschreibung |
|---|---|
| **[!UICONTROL Datumseigenschaft]** | Ermöglicht Benutzern die Suche nach Assets, die vor und nach bestimmten Daten geändert wurden. |
| **[!UICONTROL Options-Eigenschaft]** | Der Site-Eigentümer kann eine Eigenschaft angeben, nach der gesucht werden soll (wie im Eigenschaftsprädikat, z. B. cq:tags), und eine Inhaltsstruktur, aus der die Optionen gefüllt werden sollen (z. B. die Tag-Struktur). Hierdurch wird eine Liste von Optionen generiert, aus der der Benutzer die gewünschten Werte (Tags) für die ausgewählte Eigenschaft (Tag-Eigenschaft) auswählen kann. Über diese Eigenschaft können Sie Steuerungen wie eine Tag-Liste, Dateitypen, Bildausrichtungen usw. erstellen – ideal geeignet für einen festen Satz an Optionen. |
| **[!UICONTROL Pfad-Eigenschaft]** | Ermöglicht Benutzern, bei Bedarf den Pfad und die Unterordner zu definieren. |
| **[!UICONTROL Eigenschaftsprädikat]** | Der Site-Eigentümer gibt eine Eigenschaft an, nach der gesucht werden soll, z. B. tiff:ImageLength, und der Benutzer kann dann einen Wert eingeben, z. B. 800. Dadurch werden alle Bilder zurückgegeben, die 800 Pixel hoch sind. Dies ist nützlich, wenn eine Eigenschaft beliebige Werte aufweisen darf. |

Weitere Informationen finden Sie in den [Predicate Javadocs](https://helpx.adobe.com/de/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/search/eval/package-summary.html).

1. Um die Eigenschaft weiter zu konfigurieren, doppelklicken Sie darauf. Wenn Sie beispielsweise die Pfad-Eigenschaft öffnen, müssen Sie den Stammpfad zuweisen.

   ![screen_shot_2012-04-23at15640pm](assets/screen_shot_2012-04-23at15640pm.png)

## Erstellen und Konfigurieren einer Asset-Editor-Seite {#creating-and-configuring-an-asset-editor-page}

Durch Anpassen des Asset-Editors können Sie bestimmen, wie Benutzer digitale Assets anzeigen und bearbeiten können. Hierzu erstellen Sie eine neue Asset-Editor-Seite und passen dann die Ansichten und die Aktionen, die der Benutzer ausführen kann, auf dieser Seite an.

>[!NOTE]
>
>Wenn Sie benutzerdefinierte Felder zum DAM-Asset-Editor hinzufügen möchten, fügen Sie neue cq:Widget-Knoten zu `/apps/dam/content/asseteditors.`

### Erstellen der Asset-Editor-Seite {#creating-the-asset-editor-page}

Beim Erstellen von Asset-Editor-Seiten hat es sich bewährt, die Seite direkt unter der Asset-Freigabe-Seite anzulegen.

So erstellen Sie eine Asset-Editor-Seite:

1. Navigieren Sie auf der Registerkarte **[!UICONTROL Websites]** an die Stelle, an der eine Asset-Editor-Seite erstellt werden soll, und klicken Sie auf **[!UICONTROL Neu]**.

1. Wählen Sie **[!UICONTROL Geometrixx-Asset-Editor]** und klicken Sie auf **[!UICONTROL Erstellen]**. Die neue Seite wird erstellt und auf der Registerkarte **[!UICONTROL Websites]** aufgeführt.

![screen_shot_2012-04-23at15858pm](assets/screen_shot_2012-04-23at15858pm.png)

Die mit der Vorlage „Geometrixx-Asset-Editor“ erstellte Standardseite sieht wie folgt aus:

![assetshare5](assets/assetshare5.bmp)

Anpassen können Sie die Asset-Editor-Seite mithilfe der Elemente aus dem Sidekick. Die Asset-Editor-Seite, auf die über die **[!UICONTROL Geometrixx Pressezentrum]** ist eine auf dieser Vorlage basierende angepasste Version einer Seite:

![assetshare6](assets/assetshare6.bmp)

#### Festlegen, welcher Asset-Editor von einer Asset-Freigabe-Seite aus geöffnet wird {#setting-which-asset-editor-opens-from-an-asset-share-page}

Nachdem Sie die angepasste Asset-Editor-Seite erstellt haben, müssen Sie sicherstellen, dass beim Doppelklicken auf Assets über die von Ihnen erstellte angepasste Asset-Freigabe die Assets auf der angepassten Editorseite geöffnet werden.

So stellen Sie die Asset-Editor-Seite ein:

1. Klicken Sie auf der Asset-Freigabe-Seite neben dem Query Builder auf **[!UICONTROL Bearbeiten]**.

   ![screen_shot_2012-04-23at20123pm](assets/screen_shot_2012-04-23at20123pm.png)

1. Klicken Sie auf die Registerkarte **[!UICONTROL Allgemein]**, sofern diese nicht bereits ausgewählt ist.

1. Geben Sie in das Feld **[!UICONTROL Pfad des Asset-Editors]** den Pfad zu dem Asset-Editor ein, in dem die Asset-Freigabe-Seite Assets öffnen soll, und klicken Sie auf **[!UICONTROL OK]**.

   ![screen_shot_2012-04-23at21653pm](assets/screen_shot_2012-04-23at21653pm.png)

#### Hinzufügen von Asset Editor-Komponenten {#adding-asset-editor-components}

Sie können bestimmen, welche Funktionen ein Asset-Editor besitzt, indem Sie der Seite Komponenten hinzufügen.

So fügen Sie Asset-Editor-Komponenten hinzu:

1. Klicken Sie auf der anzupassenden Asset-Editor-Seite im Sidekick auf **[!UICONTROL Asset-Editor]**. Alle verfügbaren Asset-Editor-Komponenten werden angezeigt.

   >[!NOTE]
   >
   >Was angepasst werden kann, hängt von den verfügbaren Komponenten ab. Zum Aktivieren von Komponenten wechseln Sie in den Designmodus und wählen Sie die zu aktivierenden Komponenten aus.

1. Ziehen Sie die Komponenten aus dem Sidekick in den Asset-Editor und nehmen Sie Änderungen in den Komponentendialogen vor. Die Komponenten werden in der folgenden Tabelle kurz und in den darauffolgenden Anweisungen ausführlicher beschrieben.

   >[!NOTE]
   >
   >Beim Entwerfen der Asset-Editor-Seite können Sie Komponenten erstellen, die entweder schreibgeschützt oder bearbeitbar sind. Benutzer wissen, dass ein Feld bearbeitet werden kann, wenn ein Bleistiftsymbol in einer Komponente angezeigt wird. Standardmäßig sind die meisten Komponenten mit Schreibschutz eingerichtet.

   | Komponente | Beschreibung |
   |---|---|
   | **[!UICONTROL Metadatenformular] und [!UICONTROL Metadaten-Textfeld]** | Ermöglicht das Hinzufügen zusätzlicher Metadaten zu einem Asset und das Ausführen einer Aktion (z. B. Senden) für dieses Asset. |
   | **[!UICONTROL Unter-Assets]** | Ermöglicht die Anpassung von Unter-Assets. |
   | **Tags** | Ermöglicht Benutzern, Tags auszuwählen und zu einem Asset hinzuzufügen. |
   | **[!UICONTROL Miniatur]** | Zeigt eine Miniaturansicht des Assets und dessen Dateinamen an und ermöglicht das Hinzufügen eines alternativen Textes. Hierüber können Sie zudem Asset-Editor-Aktionen hinzufügen. |
   | **[!UICONTROL Titel]** | Zeigt den Asset-Titel an, der angepasst werden kann. |

   ![screen_shot_2012-04-23at22743pm](assets/screen_shot_2012-04-23at22743pm.png)

#### Metadatenformular und Textfeld – Konfigurieren der Komponente für die Metadatenanzeige {#metadata-form-and-text-field-configuring-the-view-metadata-component}

Das Metadatenformular ist ein Formular mit Start- und Endaktion. Dazwischen nehmen Sie Eingaben in die **[!UICONTROL Textfelder]** vor. Weitere Informationen über das Arbeiten mit Formularen finden Sie unter [Formulare](../sites-authoring/default-components.md).

1. Erstellen Sie eine Startaktion, indem Sie im Startbereich des Formulars auf **[!UICONTROL Bearbeiten]** klicken. Sie können einen Box-Titel eingeben, sofern gewünscht. Standardmäßig lautet der Box-Titel **[!UICONTROL Metadaten]**. Aktivieren Sie das Kontrollkästchen „Client-Validierung“, wenn JavaScript-Clientcode zwecks Validierung generiert werden soll.

   ![screen_shot_2012-04-23at22911pm](assets/screen_shot_2012-04-23at22911pm.png)

1. Erstellen Sie eine Endaktion, indem Sie im Endbereich des Formulars auf **[!UICONTROL Bearbeiten]** klicken. Beispielsweise können Sie eine Schaltfläche **[!UICONTROL Absenden]** erstellen, damit Benutzer geänderte Metadaten übermitteln können. Sie können auch eine Schaltfläche **[!UICONTROL Zurücksetzen]** hinzufügen, um den ursprünglichen Status der Metadaten wiederherzustellen.

   ![screen_shot_2012-04-23at23138pm](assets/screen_shot_2012-04-23at23138pm.png)

1. Ziehen Sie zwischen **[!UICONTROL Formular-Start]** und **Formular-Ende** die Metadaten-Textfelder in das Formular. Benutzer füllen diese Textfelder mit Metadaten auf, die übermittelt werden können oder für die eine weitere Aktion ausgeführt werden kann.

1. Doppelklicken Sie auf den Feldnamen, z. B. **Titel**, um das Metadatenfeld zu öffnen und Änderungen vorzunehmen. Auf der Registerkarte **[!UICONTROL Allgemein]** des Fensters[!UICONTROL  Komponente bearbeiten] definieren Sie den Namespace und die Feldbezeichnung sowie den Typ, z. B. `dc:title`.


   ![screen_shot_2012-04-23at23305pm](assets/screen_shot_2012-04-23at23305pm.png)

   Siehe [Anpassen und Erweitern [!DNL Assets]](extending-assets.md) für Informationen zum Ändern der im Metadatenformular verfügbaren Namespaces.

1. Klicken Sie auf die Registerkarte **[!UICONTROL Beschränkungen]**. Hier können Sie festlegen, ob ein Feld erforderlich ist, und ggf. weitere Beschränkungen hinzufügen.

   ![screen_shot_2012-04-23at23435pm](assets/screen_shot_2012-04-23at23435pm.png)

1. Klicken Sie auf die Registerkarte **[!UICONTROL Anzeigen]**. Hier können Sie einen neuen Breitenwert und die Anzahl der Zeilen für das Metadatenfeld eingeben. Aktivieren Sie das Kontrollkästchen **Feld ist schreibgeschützt**, damit Benutzer die Metadaten bearbeiten können.

   ![screen_shot_2012-04-23at23446pm](assets/screen_shot_2012-04-23at23446pm.png)

   Es folgt ein Beispiel für ein Metadatenformular mit verschiedenen Feldern:

   ![chlimage_1-390](assets/chlimage_1-390.png)

Auf der Asset-Editor-Seite können Benutzer dann Werte in die Metadatenfelder eingeben (sofern diese bearbeitbar sind) und die Endaktion ausführen (etwa Änderungen übermitteln).

#### Unter-Assets {#sub-assets}

Über die Komponente „Unter-Assets“ können Sie Unter-Assets anzeigen und auswählen. Sie können festlegen, welche Namen unter dem [Haupt-Asset](assets.md#what-are-digital-assets) und den Unter-Assets angezeigt werden.

![screen_shot_2012-04-23at24025pm](assets/screen_shot_2012-04-23at24025pm.png)

Doppelklicken Sie auf die Komponente „Unter-Assets“, um das gleichnamige Dialogfeld zu öffnen, in dem Sie die Titel für das Haupt-Asset und etwaige Unter-Assets ändern können. Die Standardwerte werden unter dem entsprechenden Feld angezeigt.

![screen_shot_2012-04-23at23907pm](assets/screen_shot_2012-04-23at23907pm.png)

Es folgt ein Beispiel für eine ausgefüllte Komponente „Unter-Assets“:

![screen_shot_2012-04-23at24442pm](assets/screen_shot_2012-04-23at24442pm.png)

Achten Sie z. B. bei Auswahl eines Unter-Assets darauf, wie die Komponente die entsprechende Seite anzeigt und sich der Box-Titel von „Unter-Assets“ zu „Gleichgeordnete“ ändert.

![screen_shot_2012-04-23at24552pm](assets/screen_shot_2012-04-23at24552pm.png)

#### Tags {#tags}

Mit der Komponente „Tags“ können Benutzer einem Asset vorhandene Tags zuweisen, was sich später bei Organisation und Abruf als hilfreich erweist. Sie können diese Komponente mit Schreibschutz versehen, sodass Benutzer Tags zwar anzeigen, aber nicht hinzufügen können.

![screen_shot_2012-04-23at25031pm](assets/screen_shot_2012-04-23at25031pm.png)

Doppelklicken Sie auf die Komponente „Tags“, um das gleichnamige Dialogfeld zu öffnen, in dem Sie den Titel „Tags“ ggf. ändern und die zugewiesenen Namespaces auswählen können. Damit dieses Feld bearbeitet werden kann, deaktivieren Sie das Kontrollkästchen **Bearbeitungsschaltfläche** ausblenden. Standardmäßig können Tags bearbeitet werden.

![screen_shot_2012-04-23at24731pm](assets/screen_shot_2012-04-23at24731pm.png)

Wenn Benutzer Tags bearbeiten können, können sie auf das Bleistiftsymbol klicken, um Tags durch Auswahl aus dem Dropdownmenü hinzuzufügen.

![screen_shot_2012-04-23at25150pm](assets/screen_shot_2012-04-23at25150pm.png)

Es folgt ein Beispiel für eine ausgefüllte Komponente „Tags“:

![screen_shot_2012-04-23at25244pm](assets/screen_shot_2012-04-23at25244pm.png)

#### Miniatur {#thumbnail}

In der Komponente „Miniatur“ zeigt das Asset die ausgewählte Miniatur an (für eine Vielzahl der Formate wird die Miniatur automatisch extrahiert). Außerdem präsentiert die Komponente den Dateinamen und [von Ihnen veränderbare Aktionen](assets-finder-editor.md#adding-asset-editor-actions).

![screen_shot_2012-04-23at25452pm](assets/screen_shot_2012-04-23at25452pm.png)

Doppelklicken Sie auf die Komponente „Miniatur“, um den gleichnamigen Dialog zum Ändern des ALT-Texts zu öffnen. Der Alt-Text der Miniaturansicht standardmäßig auf **[!UICONTROL Zum Herunterladen klicken]** Asset.

![screen_shot_2012-04-23at25604pm](assets/screen_shot_2012-04-23at25604pm.png)

Es folgt ein Beispiel für eine ausgefüllte Komponente „Miniatur“:

![screen_shot_2012-04-23at34815pm](assets/screen_shot_2012-04-23at34815pm.png)

#### Titel {#title}

Über die Komponente „Titel“ werden der Titel des Assets sowie eine Beschreibung angezeigt.

![chlimage_1-391](assets/chlimage_1-391.png)

Standardmäßig liegt die Komponente im schreibgeschützten Modus vor, um eine Bearbeitung durch Benutzer zu verhindern. Damit sie bearbeitet werden kann, doppelklicken Sie auf die Komponente und deaktivieren Sie das Kontrollkästchen **Bearbeitungsschaltfläche ausblenden**. Geben Sie außerdem einen Titel für mehrere Assets ein.

![screen_shot_2012-04-23at35100pm](assets/screen_shot_2012-04-23at35100pm.png)

Wenn der Titel bearbeitbar ist, können Sie einen Titel und eine Beschreibung hinzufügen, indem Sie auf das Bleistiftsymbol klicken und so das Fenster **Asset-Eigenschaften** öffnen. Darüber hinaus ist es möglich, das Asset durch Auswahl von Datum und Uhrzeit zu aktiveren bzw. zu deaktivieren.

Wenn Benutzer den Titel durch Klicken auf das Bleistiftsymbol bearbeiten, können Sie den **Titel** und die **Beschreibung** ändern und die **Einschaltzeit** sowie die **Ausschaltzeit** zum Aktivieren und Deaktivieren des Assets eingeben.

![screen_shot_2012-04-23at35241pm](assets/screen_shot_2012-04-23at35241pm.png)

Es folgt ein Beispiel für eine ausgefüllte Komponente „Titel“:

![chlimage_1-392](assets/chlimage_1-392.png)

#### Hinzufügen von Asset Editor-Aktionen {#adding-asset-editor-actions}

Sie können anhand einer Auswahl vordefinierter Aktionen festlegen, welche Aktionen Benutzer für ausgewählte digitale Assets ausführen können.

So fügen Sie der Asset-Editor-Seite Aktionen hinzu:

1. Klicken Sie auf der anzupassenden Asset-Editor-Seite auf **[!UICONTROL Asset-Editor]** im Sidekick.<br>

   ![Asset-Editor im Sidekick auswählen](assets/screen_shot_2012-04-23at35515pm.png)

   Die folgenden Aktionen sind verfügbar:

   | Aktion | Beschreibung |
   |---|---|
   | [!UICONTROL Download] | Ermöglicht Benutzern das Herunterladen ausgewählter Assets auf ihren Computern. |
   | [!UICONTROL Editoren] | Ermöglicht Benutzern die Bearbeitung eines Bildes (interaktive Bearbeitung) |
   | [!UICONTROL Lightbox] | Speichert Assets in einer &quot;Lightbox&quot;, in der Sie andere Aktionen durchführen können. Dies ist praktisch, wenn über mehrere Seiten hinweg an Assets gearbeitet wird. |
   | [!UICONTROL Sperren] | Benutzer können ein Asset sperren. Diese Funktion ist nicht standardmäßig aktiviert und muss in der Liste der Komponenten aktiviert werden. |
   | [!UICONTROL Verweise] | Klicken Sie auf diese Option, um anzuzeigen, auf welchen Seiten das Asset verwendet wird. |
   | [!UICONTROL Versionierung] | Ermöglicht das Erstellen und Wiederherstellen von Versionen eines Assets. |

1. Ziehen Sie die entsprechende Aktion in den Bereich **Aktionen** auf der Seite. Hierdurch wird eine Schaltfläche zum Ausführen dieser Aktion erstellt.

![chlimage_1-393](assets/chlimage_1-393.png)

## Bearbeiten mehrerer Assets mit der Asset-Editor-Seite {#multi-editing-assets-with-the-asset-editor-page}

Mit [!DNL Assets] Sie können Änderungen an mehreren Assets gleichzeitig vornehmen. Nach Auswahl der Assets können Sie bei diesen gleichzeitig Folgendes ändern:

* Tags
* Metadaten

So führen Sie eine Mehrfachbearbeitung von Assets mit der Asset-Editor-Seite durch:

1. Öffnen Sie die Geometrixx **[!UICONTROL Pressezentrum]** page at `http://localhost:4502/content/geometrixx/en/company/press.html`.
1. Wählen Sie die Assets aus:

   * unter Windows: `Ctrl + click` jedes Asset.
   * auf Mac: `Cmd + click` jedes Asset.

   So wählen Sie einen Asset-Bereich aus: Klicken Sie auf das erste Asset und dann auf `Shift + click` das letzte Asset.

1. Klicken Sie im Feld **[!UICONTROL Aktionen]** auf **Metadaten bearbeiten** (linker Seitenbereich).

1. Die Geometrixx-Seite mit dem **[!UICONTROL Pressezentrum-Asset-Editor]** wird auf einer neuen Registerkarte geöffnet. Die Metadaten der Assets werden wie folgt angezeigt:

   * Ein Tag, das nicht für alle Assets gilt, sondern nur für einige wenige, wird kursiv dargestellt.
   * Ein Tag, das für alle Assets gilt, wird mit einer normalen Schriftart angezeigt.
   * Andere Metadaten als Tags: Der Wert des Felds wird nur angezeigt, wenn dieser für alle ausgewählten Assets identisch ist.

1. Klicken **[!UICONTROL Download]** , um eine ZIP-Datei mit den Original-Ausgabeformaten der Assets herunterzuladen.
1. Klicken Sie auf das Bleistiftsymbol neben dem Feld **[!UICONTROL Tags]**, um die Tags zu bearbeiten:

   * Ein Tag, das nicht für alle Assets gilt, sondern nur für einige wenige, hat einen grauen Hintergrund.
   * Ein Tag, das für alle Assets gilt, hat einen weißen Hintergrund.

   Sie haben folgende Möglichkeiten:

   * Klicken Sie auf das Symbol `x`, um das Tag für alle Assets zu entfernen.
   * Klicken Sie auf `+` -Symbol, um das Tag zu allen Assets hinzuzufügen.
   * Klicken Sie auf `arrow` und wählen Sie ein Tag aus, um allen Assets ein neues Tag hinzuzufügen.

   Klicken Sie auf **[!UICONTROL OK]**, um die Änderungen in das Formular zu schreiben. Das Kästchen neben dem Feld **Tags** wird automatisch aktiviert.

1. Bearbeiten Sie das Feld Beschreibung . Setzen Sie sie beispielsweise auf: `This is a common description`. Wenn ein Feld bearbeitet wird, überschreibt sein Wert die vorhandenen Werte der ausgewählten Assets, wenn das Formular gesendet wird. Das Kästchen neben dem Feld wird automatisch aktiviert, wenn das Feld bearbeitet wird.

   `This is a common description`

   Wenn ein Feld bearbeitet wird, überschreibt sein Wert die vorhandenen Werte der ausgewählten Assets, wenn das Formular gesendet wird.

   Hinweis: Das Kästchen neben dem Feld wird automatisch aktiviert, wenn das Feld bearbeitet wird.

1. Klicken Sie auf **[!UICONTROL Metadaten aktualisieren]**, um das Formular abzusenden und die Änderungen für alle Assets zu speichern. Nur die aktivierten Metadaten werden geändert.
