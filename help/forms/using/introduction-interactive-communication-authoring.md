---
title: Einführung in die Benutzeroberfläche für interaktive Kommunikationserstellung
seo-title: Eine Einführung in die verschiedenen Elemente der Benutzeroberfläche, mit denen Sie interaktive Kommunikation erstellen können
description: Eine Einführung in die verschiedenen Elemente der Benutzeroberfläche, mit denen Sie interaktive Kommunikation erstellen können
seo-description: Eine Einführung in die verschiedenen Elemente der Benutzeroberfläche, mit denen Sie interaktive Kommunikation erstellen können
uuid: 4e301b9a-76a1-4beb-9d67-dbd0a3bdd2e4
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: interactive-communications
discoiquuid: 565bfb42-6099-49f4-83ba-b1f0c129aab7
translation-type: tm+mt
source-git-commit: de440f57091d814a0a7ff48e9a0383c5415a0a5b
workflow-type: tm+mt
source-wordcount: '1315'
ht-degree: 55%

---


# Einführung in die Benutzeroberfläche für interaktive Kommunikationserstellung {#introduction-to-interactive-communication-authoring-ui}

Eine Einführung in die verschiedenen Elemente der Benutzeroberfläche, mit denen Sie interaktive Kommunikation erstellen können

The user interface for authoring [Interactive Communication](/help/forms/using/interactive-communications-overview.md) is intuitive and provides the following for authoring print and web channel of the Interactive Communication:

* WYSIWYG Drag-and-Drop-Dokumenteditor
* Integriertes Repository für Assets - Die auf den Server hochgeladenen und erstellten Assets sind im Asset-Browser der Authoring-Oberfläche für interaktive Kommunikation verfügbar

Wenn Sie eine [neue interaktive Kommunikation](/help/forms/using/create-interactive-communication.md) erstellen oder eine vorhandene bearbeiten, verwenden Sie die folgenden Elemente der Benutzeroberfläche:

* [Randleiste](#sidebar)
* [Seitensymbolleiste](#page-toolbar)

* [Komponenten-Symbolleiste](#component-toolbar)
* Inhaltsbereich

![Benutzeroberfläche der interaktiven Kommunikation](assets/form-editor.png)

**A.** Seitenleiste **B.** Seitensymbolleiste **C.** Inhaltsbereich

## Randleiste {#sidebar}

![Randleiste](assets/sidebar-comps.png)

[Zum Vergrößern hier klicken](assets/sidebar-comps-1.png)

**A.** Kanal Browser **B.** Inhaltsbrowser **C.** Eigenschaftenbrowser **D.** Asset Browser **E.** Komponenten-Browser **F.** Datenquellen-Browser - Datenmodell **G.** Data Sources-Browser - Übergeordnet Content

Die Seitenleiste beinhaltet Folgendes:

* **Kanalbrowser**

   Mit dem Kanalbrowser können Sie zwischen den Druck- und Internetkanälen der interaktiven Kommunikation wechseln. Je nach dem Kanal, den Sie im Kanalbrowser ausgewählt haben, zeigen die Browser, z. B. Inhalts- und Komponentenbrowser, die Optionen an.

* **Inhaltsbrowser**

   Im Inhaltsbrowser können Sie die Objekthierarchie des Dokuments für den ausgewählten Kanal sehen. Der Autor kann zu bestimmten Formularkomponenten navigieren, indem er auf das entsprechende Element in der Dokumentobjektstruktur tippt. Der Autor kann Objekte im Webkanal suchen und in dieser Struktur neu anordnen. 

* **Eigenschaftenbrowser**

   Hiermit können Sie die Eigenschaften einer Komponente bearbeiten. Die Eigenschaften sind je nach Komponente verschieden. So zeigen Sie beispielsweise die Eigenschaften des Dokument-Containers an:

   Wählen Sie eine Komponente aus, tippen Sie dann auf ![Feldebene](assets/field-level.png) > **Dokument-Container** und dann auf ![cmppr](assets/cmppr.png).

* **Assets-Browser**

   Trennt verschiedene Arten von Inhalten wie Layout-Fragmente, Bilder, Dokumente, Seiten, Videos. Der Autor kann Assets in die interaktive Kommunikation ziehen und ablegen.

* **Komponentenbrowser**

   Umfasst Komponenten, die Sie zum Erstellen der Druck- und Web-Kanäle eines Dokuments verwenden können. Sie können Komponenten in die interaktive Kommunikation ziehen, um Elemente hinzuzufügen und hinzugefügte Elemente gemäß den Anforderungen zu konfigurieren. In der folgenden Tabelle werden die im Komponentenbrowser aufgelisteten Komponenten für Druck- und Webkanäle beschrieben. 

| **Komponente** | **Druckkanal** | **Webkanal** | **Funktion** |
|---|---|---|---|
| Diagramm | ✓ | ✓ | Fügt ein Diagramm hinzu, das Sie in interaktiver Kommunikation zur visuellen Darstellung von zweidimensionalen Daten verwenden können, die aus einem FDM-Sammlungselement abgerufen werden. |
| Dokumentfragment | ✓ | ✓ | Ermöglicht das Hinzufügen einer wiederverwendbaren Komponente, eines Textes, einer Liste oder einer Bedingung zu einer interaktiven Kommunikation. Die wiederverwendbare Komponente, die Sie einer interaktiven Kommunikation hinzufügen, kann entweder auf Formulardatenmodellen oder ohne Formulardatenmodell basieren. |
| Bild | ✓ | ✓ | Ermöglicht es Ihnen, ein Bild einzufügen. |
| Fenster | - | ✓ | Die Bereichskomponente ist ein Platzhalter zum Gruppieren anderer Komponenten und steuert, wie eine Gruppe von Komponenten in einer interaktiven Kommunikation angeordnet wird. Mit einer Bereichskomponente können Sie auch eine Gruppe von Komponenten für den Endbenutzer wiederholbar machen, z. B. mehrere Einträge zum Ausfüllen von Bildungsnachweisen. Es empfiehlt sich außerdem, ein Bedienfeld für jede Registerkarte einer interaktiven Kommunikation mit mehreren Registerkarten zu verwenden. |
| Tabelle | &amp;ast; | ✓ | Fügt eine Tabelle hinzu, mit der Sie Daten in Zeilen und Spalten organisieren können. |
| Zielbereich | &amp;ast;&amp;ast; | ✓ | Fügt einen Zielbereich in einen Webkanal ein, um die webkanalspezifischen Komponenten zu organisieren. |
| Text | - | ✓ | Fügt dem Webkanal einer interaktiven Kommunikation Text hinzu. Text kann Formulardatenmodellobjekte verwenden, um den Inhalt dynamisch zu gestalten. |

&amp;ast; Verwenden Sie Layout-Fragmente im Kanal &quot;Drucken&quot;, um Tabellen hinzuzufügen.

&amp;ast;&amp;ast; Im Kanal &quot;Drucken&quot;sind die Bereiche der Zielgruppe in der XDP-/Druckvorlage vordefiniert. Sie können keine neuen Zielbereiche mithilfe der Autorenoberfläche für die interaktive Kommunikation hinzufügen.

* **Datenquellen-Browser**

   Der Datenquellen-Browser zeigt die verfügbaren Datenquellen im Formulardatenmodell an, das Sie beim Erstellen der interaktiven Kommunikation ausgewählt haben.

### Wichtige Punkte für das Arbeiten mit Komponenten {#key-points-for-working-with-components}

Die wichtigsten Punkte beim Arbeiten mit interaktiven Kommunikationskomponenten sind:

* Jede Komponente verfügt über zugehörige Eigenschaften, die ihre Darstellung und Funktion steuern. To configure the properties of a component, tap the component and tap ![cmppr](assets/cmppr.png) to open the component properties in the Properties browser.
* Eine Komponente wird mit ihrem Elementnamen gekennzeichnet. When you tap ![cmppr](assets/cmppr.png), you can change the name of the component by changing the Element Name field value in the properties browser. Das Feld „Elementname“ akzeptiert nur Buchstaben, Zahlen, Bindestriche (-) und Unterstriche (_). Andere Sonderzeichen sind nicht zulässig. Der Elementname muss mit einem Buchstaben beginnen.
* Sie können die Eigenschaft &quot;Titel&quot;einer interaktiven Kommunikationskomponente inline im Editor ändern, ohne den Eigenschaftenbrowser zu öffnen, solange der Titel in der interaktiven Kommunikation sichtbar ist. Gehen Sie dazu wie folgt vor:

   1. Wählen Sie auf eine Komponente, in der die Eigenschaft Title vorhanden ist und deren Eigenschaft Titel ausblenden deaktiviert ist, aus, indem Sie darauf tippen.
   1. Tippen Sie auf ![aem_6_3_edit](assets/aem_6_3_edit.png) , um den Titel bearbeitbar zu machen.
   1. Ändern Sie den Titel und tippen Sie auf die Return-Taste oder tippen Sie auf eine beliebige Stelle außerhalb der Komponente, um die Änderungen zu speichern. Tippen Sie auf die Esc-Taste, um die Änderungen zu verwerfen.

## Komponenten-Symbolleiste {#component-toolbar}

![](do-not-localize/toolbar.png)

Wenn Sie eine Komponente auswählen, sehen Sie eine Symbolleiste, die folgende Funktionen bietet. Sie erhalten Optionen zum Ausschneiden, Einfügen, Verschieben und Festlegen von Eigenschaften der Komponenten. Ihre Optionen sind:

A.**Konfigurieren**: Wenn Sie auf **Konfigurieren** tippen, werden in der Seitenleiste Komponenteneingenschaften sichtbar.

B. **Edit Rules**: When you tap Edit Rules, Rule Editor appears in which you can edit and create rules for the selected component. Im Regeleditor können Sie auch andere Formularobjekte (Komponenten) auswählen und Regeln für diese Formularobjekte bearbeiten/erstellen.

C. **Kopieren**: Sie können die Kopieroption verwenden, um eine Komponente zu kopieren und an andere Positionen im Formular einzufügen.

D. **Cut**: You can use the cut option to move a component from one place to another in the Interactive Communication.

E. **Delete**: Lets you delete the component from the Interactive Communication.

F. **Insert Component**: Lets you insert a component above the selected component.

G. **Paste**: Lets you paste the component you cut or copied using the options described above.

H. **Gruppieren**: Mit dieser Funktion können Sie mehrere Komponenten auswählen, um sie zusammen auszuschneiden, zu kopieren oder einzufügen.

I. **Übergeordnet**: Hier können Sie das übergeordnete Element einer Komponente auswählen.

J. **More**: Provides more options to work with the selected component.

* SOM-Ausdruck anzeigen (nur für Bereiche)
* Gruppenobjekte im Bereich (nur für Bereiche)
* Fragment bearbeiten (nur für Fragmente)
* Bereich als Fragment speichern (nur für Bereiche)
* Untergeordneten Bereich hinzufügen (nur für Bereiche)
* Bereichssymbolleiste hinzufügen (nur für Bereiche)
* Ersetzen (nicht für Bereiche)

## Seitensymbolleiste {#page-toolbar}

Die Seitensymbolleiste oben bietet Optionen, mit denen Sie die interaktive Kommunikation Vorschau und ihre Eigenschaften ändern können. Sie können die interaktive Kommunikation beim Erstellen einer Vorschau erstellen und entsprechende Änderungen vornehmen. In der Seitensymbolleiste wird Folgendes angezeigt:

* Toggle Side Panel ![toggle-side-panel](assets/toggle-side-panel.png): Lets you show or hide Sidebar.
* Page information ![pageinformationad](assets/pageinformationad.png): Lets you view page properties.
* Emulator ![ruler](assets/ruler.png): Lets you emulate the look of your Interactive Communication for different display sizes such as tablets and phones.
* Bearbeiten: Hiermit können Sie andere Modi auswählen, wie etwa: Bearbeiten, Stil, Entwickler und Design.

   * Bearbeiten: Ermöglicht die Bearbeitung der Eigenschaften der interaktiven Kommunikation und ihrer Komponenten. Dies tun Sie, indem Sie beispielsweise eine Komponente hinzufügen, ein Bild ablegen oder obligatorische Felder festlegen.
   * Stil: Hiermit können Sie das Erscheinungsbild von Komponenten der interaktiven Kommunikation stilistisch anpassen. Im Stilmodus können Sie beispielsweise einen Bereich auswählen und dessen Hintergrundfarbe festlegen.
   * Entwickler: Ermöglicht Entwicklern Folgendes:

      * Entdecken Sie, woraus interaktive Kommunikation besteht.
      * Debugging der am Formular durchgeführten Aktionen zur Behebung von Fehlern.
   * Zielgruppe: Ermöglicht die Aktivierung oder Deaktivierung benutzerdefinierter Komponenten oder von vordefinierten Komponenten, die nicht in der Seitenleiste aufgeführt sind.


* Vorschau: Ermöglicht die Vorschau, wie die interaktive Kommunikation aussieht, wenn Sie sie veröffentlichen.

