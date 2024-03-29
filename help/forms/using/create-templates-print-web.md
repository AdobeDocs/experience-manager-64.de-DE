---
title: "Tutorial: Erstellen Sie Vorlagen"
seo-title: Create Print and Web templates for Interactive Communication
description: Erstellen Sie Druck- und Webvorlagen für die interaktive Kommunikation
seo-description: Create Print and Web templates for Interactive Communication
uuid: d7b0d9a5-f5f0-4c21-a6f8-622bf94f4491
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 40c0a17b-6894-44cc-b1f7-490913061532
feature: Interactive Communication
exl-id: 5822145f-d317-4807-a3f0-1d2aea0a779b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1852'
ht-degree: 55%

---

# Tutorial: Erstellen Sie Vorlagen {#tutorial-create-templates}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Erstellen Sie Druck- und Webvorlagen für die interaktive Kommunikation

![07-apply-rules-to-adaptive-form_small](assets/07-apply-rules-to-adaptive-form_small.png)

Dieses Tutorial ist ein Schritt in der Reihe [Erstellen Sie Ihre erste interaktive Kommunikation](/help/forms/using/create-your-first-interactive-communication.md). Es wird empfohlen, der Reihe in chronologischer Reihenfolge zu folgen, um den vollständigen Anwendungsfall des Tutorials zu verstehen, auszuführen und zu demonstrieren.

Um eine interaktive Kommunikation zu erstellen, müssen auf dem AEM-Server Vorlagen für Druck- und Webkanäle verfügbar sein.

Die Vorlagen für den Druckkanal werden in Adobe Forms Designer erstellt und auf den AEM hochgeladen. Diese Vorlagen können dann beim Erstellen einer interaktiven Kommunikation verwendet werden.

Die Vorlagen für den Webkanal werden in AEM erstellt. Vorlagenautoren und -administratoren können Webvorlagen erstellen, bearbeiten und aktivieren. Nach der Erstellung und Aktivierung sind diese Vorlagen zur Verwendung beim Erstellen einer interaktiven Kommunikation verfügbar.

Dieses Tutorial führt Sie durch die Schritte zum Erstellen von Vorlagen für Druck- und Webkanäle, damit diese zur Erstellung interaktiver Kommunikation zur Verfügung stehen. Am Ende dieses Tutorials können Sie Folgendes:

* Erstellen von XDP-Vorlagen für den Druckkanal mit Adobe Forms Designer
* Hochladen der XDP-Vorlagen auf den AEM Forms-Server
* Erstellen und Aktivieren von Vorlagen für den Webkanal

## Vorlage für Druckkanal erstellen {#create-template-for-print-channel}

Erstellen und verwalten Sie Vorlagen für den Druckkanal der interaktiven Kommunikation mit folgenden Aufgaben:

* [Erstellen Sie eine XDP-Vorlage mit dem Forms Designer](/help/forms/using/create-templates-print-web.md#create-xdp-template-using-forms-designer)
* [Laden Sie die XDP-Vorlagen auf den AEM Forms Server hoch](/help/forms/using/create-templates-print-web.md#upload-xdp-template-to-the-aem-forms-server)
* [XDP-Vorlage für Layoutfragmente erstellen](/help/forms/using/create-templates-print-web.md#create-xdp-template-for-layout-fragments)

### Erstellen Sie eine XDP-Vorlage mit dem Forms Designer {#create-xdp-template-using-forms-designer}

Basierend auf dem [Anwendungsfall](/help/forms/using/create-your-first-interactive-communication.md) und der [Anatomie](/help/forms/using/planning-interactive-communications.md), erstellen Sie die folgenden Teilformulare in der XDP-Vorlage:

* Rechnungsdetails: Enthält ein Dokumentfragment
* Kundendetails: Enthält ein Dokumentfragment
* Rechnungszusammenfassung: Enthält ein Dokumentfragment
* Zusammenfassung: Enthält ein Dokumentfragment (Teilformular „Gebühren“) und ein Diagramm (Teilformular „Diagramme“).
* Aufrufe: Enthält eine Tabelle (Layout-Fragment)
* Jetzt bezahlen: Enthält ein Bild
* Mehrwert-Services: Enthält ein Bild

![create_print_template](assets/create_print_template.gif)

Diese Teilformulare werden nach dem Hochladen der XDP-Datei auf den Forms-Server als Zielbereiche in der Druckvorlage angezeigt. Alle Entitäten wie Dokumentfragmente, Diagramme, Layout-Fragmente und Bilder werden beim Erstellen der interaktiven Kommunikation den Zielbereichen hinzugefügt.

Führen Sie die folgenden Schritte aus, um eine XDP-Vorlage für den Druckkanal zu erstellen:

1. Öffnen Sie den Forms Designer, wählen Sie **Datei** > **Neu** > **Verwenden Sie ein leeres Formular**,  tippen Sie auf **Weiter** und anschließend auf **Fertig stellen**, um das Formular für die Vorlagenerstellung zu öffnen.

   Stellen Sie sicher, dass die **Objektbibliothek** und die Option **Objekt** im Menü **Fenster** ausgewählt werden.

1. Ziehen Sie die Komponente **Teilformular** aus der **Objektbibliothek** in das Formular.
1. Wählen Sie das Teilformular aus, um die Optionen für das Teilformular im Fenster **Objekt** im rechten Bereich anzuzeigen.
1. Wählen Sie die Registerkarte **Teilformular** und wählen Sie **Textfluss** aus der Dropdown-Liste **Inhalt** aus. Ziehen Sie den linken Endpunkt des Teilformulars, um die Länge anzupassen.
1. Führen Sie auf der Registerkarte **Bindungen** folgende Schritte aus:

   1. Geben Sie **BillDetails** in das Feld **Name** ein.
   1. Wählen Sie **Keine Datenbindung** aus der Dropdown-Liste **Datenbindung**.

   ![forms_designer_subform](assets/forms_designer_subform.png)

1. Wählen Sie das Teilformular „Stamm“, dann die Registerkarte **Teilformular** und dann **Textfluss** aus der Dropdown-Liste **Inhalt** aus. Führen Sie auf der Registerkarte **Bindungen** folgende Schritte aus:

   1. Geben Sie **TelecaBill** in das Feld **Name** ein.
   1. Wählen Sie **Keine Datenbindung** aus der Dropdown-Liste **Datenbindung**.

   ![root_subform_print_template](assets/root_subform_print_template.png)

1. Wiederholen Sie die Schritte 2 bis 5, um die folgenden Teilformulare zu erstellen:

   * BillDetails
   * CustomerDetails
   * BillSummary
   * Zusammenfassung – Wählen Sie die Registerkarte **Teilformular** und wählen Sie für dieses Teilformular **Positioniert** aus der Dropdown-Liste **Inhalt**. Fügen Sie die folgenden Teilformulare in das Teilformular **Zusammenfassung** ein.

      * Gebühren
      * Diagramme
   * itemsCalls
   * PayNow
   * ValueAddedServices

   Um Zeit zu sparen, können Sie auch vorhandene Teilformulare kopieren und einfügen, um neue Teilformulare zu erstellen.

   Um das Teilformular **Diagramme** rechts neben das Teilformular „Gebühren“ zu verschieben, wählen Sie das Teilformular **Diagramme** im linken Bereich aus, wählen Sie die Registerkarte **Layout** und geben Sie einen Wert für das Feld **AnkerX** an. Der Wert muss größer als der Wert für das Feld **Breite** für das Teilformular **Gebühren** sein. Wählen Sie das Teilformular **Gebühren** und wählen Sie die Registerkarte **Layout**, um den Wert des Felds **Breite** anzuzeigen.

1. Ziehen Sie das Objekt **Text** aus der **Objektbibliothek** in das Formular, und geben Sie den Text **XXXX zum Abonnieren wählen** in das Feld ein.
1. Klicken Sie mit der rechten Maustaste auf das Textobjekt im linken Bereich, wählen Sie **Objekt umbenennen**, und geben Sie den Namen des Textobjekts als **Abonnieren** ein.

   ![print_xdp_template_subform](assets/print_xdp_template_subform.png)

1. Wählen Sie **Datei** > **Speichern unter**, um die Datei im lokalen Dateisystem zu speichern:

   1. Navigieren Sie zum Speicherort der Datei und geben Sie den Namen **create_first_ic_print_template** ein.
   1. Auswählen **.xdp** von **Dateityp** Dropdown-Liste.
   1. Tippen Sie auf **Speichern**.

### Hochladen einer XDP-Vorlage auf den AEM Forms-Server {#upload-xdp-template-to-the-aem-forms-server}

Nachdem Sie eine XDP-Vorlage mit Forms Designer erstellt haben, müssen Sie sie auf den AEM Forms-Server hochladen, damit die Vorlage beim Erstellen der interaktiven Kommunikation verwendet werden kann.

1. Wählen Sie **[!UICONTROL Formulare]** > **[!UICONTROL Formulare &amp; Dokumente]**.
1. Tippen Sie auf **Erstellen** > **Datei hochladen**.

   Navigieren Sie zur Vorlage **create_first_ic_print_template** (XDP) und wählen Sie sie aus. Tippen Sie auf **Öffnen**, um die XDP-Vorlage auf den AEM Forms-Server zu importieren.

### Erstellen einer XDP-Vorlage für Layout-Fragmente {#create-xdp-template-for-layout-fragments}

Um ein Layout-Fragment für den Druckkanal der interaktiven Kommunikation zu erstellen, erstellen Sie eine XDP mit Forms Designer und laden Sie sie auf den AEM Forms-Server hoch.

1. Öffnen Sie den Formular-Designer, wählen Sie **Datei** > **Neu** > **Leeres Formular verwenden**, und tippen Sie auf **Weiter**, und danach auf **Fertig stellen**, um das Formular für die Vorlagenerstellung zu öffnen.

   Stellen Sie sicher, dass die **Objektbibliothek** und die Option **Objekt** im Menü **Fenster** ausgewählt werden.

1. Ziehen Sie die Komponente **Tabelle** per Drag-and-Drop aus der **Objektbibliothek** auf das Formular.
1. Im Dialogfeld „Tabelle einfügen“:

   1. Geben Sie die Anzahl der Spalten als **5**.
   1. Geben Sie die Anzahl der Textzeilen als **1**.
   1. Wählen Sie die **Kopfzeile in Tabelle einschließen** aktivieren.
   1. Registerkarte **OK**.

1. Tippen **+** im linken Bereich neben **Verzeichnis** 1 und Rechtsklick **Cell1** und wählen Sie **Objekt umbenennen** nach **Datum**.

   Benennen Sie **Zelle2**, **Zelle3**, **Zelle4** und **Zelle5** in **Zeit**, **Anzahl**, **Dauer** und **Kosten** um.

1. Klicken Sie in der **Designer-Ansicht** auf die Textfelder „Kopfzeile“ und benennen Sie sie in **Zeit**, **Anzahl**, **Dauer** und **Kosten** um.

   ![layout_fragment_print](assets/layout_fragment_print.png)

1. Wählen Sie **Zeile 1** aus dem linken Bereich und wählen Sie **Objekt** > **Bindung** > **Zeile für jedes Datenelement wiederholen**.

   ![layout_fragment_print_repeat](assets/layout_fragment_print_repeat.png)

1. Ziehen Sie die Komponente **Textfeld** per Drag-and-Drop aus der **Objektbibliothek** in die **Designer-Ansicht**.

   ![layout_fragment_print_text_field](assets/layout_fragment_print_text_field.png)

   Ziehen Sie die Komponente **Textfeld** in die Zeilen **Zeit**, **Anzahl**, **Dauer** und **Kosten**.

1. Wählen Sie **Datei** > **Speichern unter**, um die Datei im lokalen Dateisystem zu speichern:

   1. Navigieren Sie zum Speicherort der Datei und geben Sie den Namen **table_lf** ein.
   1. Auswählen **.xdp** von **Dateityp** Dropdown-Liste.
   1. Tippen Sie auf **Speichern**.

   Nachdem Sie eine XDP-Vorlage mit dem Forms-Designer erstellt haben, müssen Sie sie auf den AEM Forms-Server [hochladen](/help/forms/using/create-templates-print-web.md#upload-xdp-template-to-the-aem-forms-server), damit die Vorlage beim Erstellen der von Layout-Fragmenten verwendet werden kann.

## Vorlage für Webkanal erstellen {#create-template-for-web-channel}

Erstellen und verwalten Sie Vorlagen für den Webkanal der interaktiven Kommunikation mit folgenden Aufgaben:

* [Ordner für Vorlagen erstellen](/help/forms/using/create-templates-print-web.md#create-folder-for-templates)
* [Vorlage erstellen](/help/forms/using/create-templates-print-web.md#create-the-template)
* [Vorlage aktivieren](/help/forms/using/create-templates-print-web.md#enable-the-template)
* [Aktivieren von Schaltflächen in interaktiven Kommunikationen](/help/forms/using/create-templates-print-web.md#enabling-buttons-in-interactive-communications)

### Erstellen eines Ordners für Vorlagen {#create-folder-for-templates}

Um eine Webkanalvorlage zu erstellen, definieren Sie einen Ordner, in dem Sie die erstellten Vorlagen speichern können. Nachdem Sie eine Vorlage in diesem Ordner erstellt haben, aktivieren Sie die Vorlage, damit die Formularbenutzer den Webkanal einer interaktiven Kommunikation basierend auf der Vorlage erstellen können.

Führen Sie die folgenden Schritte aus, um einen Ordner für die bearbeitbaren Vorlagen zu erstellen:

1. Tippen **Instrumente** ![Instrumente](assets/tools-icon.svg) > **Konfigurationsbrowser**.
   * Weitere Informationen finden Sie in der Dokumentation zum [Konfigurations-Browser.](/help/sites-administering/configurations.md)
1. Tippen Sie auf der Seite „Konfigurationsbrowser“ auf **Erstellen**.
1. Legen Sie im Dialogfeld **Konfiguration erstellen** **Create_First_IC_templates** als den Titel für den Ordner fest, aktivieren Sie **Bearbeitbare Vorlagen** und tippen Sie auf **Erstellen**.

   ![create_first_ic_web_template](assets/create_first_ic_web_template.png)

   Der Ordner **Create_First_IC_templates** wird auf der Seite **Konfigurations-Browser** erstellt und aufgeführt.

### Vorlage erstellen {#create-the-template}

Basierend auf dem [Anwendungsfall](/help/forms/using/create-your-first-interactive-communication.md) und der [Anatomie](/help/forms/using/planning-interactive-communications.md), erstellen Sie die folgenden Bereiche in der Webvorlage:

* Rechnungsdetails: Enthält ein Dokumentfragment
* Kundendetails: Enthält ein Dokumentfragment
* Rechnungszusammenfassung: Enthält ein Dokumentfragment
* Kostenübersicht: Enthält ein Dokumentfragment und ein Diagramm (zweispaltiges Layout)
* Einzeln aufgeführte Anrufe: Enthält eine Tabelle
* Jetzt bezahlen: Enthält die Schaltfläche **Jetzt bezahlen** und ein Bild
* Mehrwert-Services: Enthält ein Bild und die Schaltfläche **Abonnieren**.

![create_web_template](assets/create_web_template.gif)

Alle Entitäten wie Dokumentfragmente, Diagramme, Tabellen, Bilder und Schaltflächen werden beim Erstellen der interaktiven Kommunikation hinzugefügt.

Führen Sie die folgenden Schritte aus, um eine Vorlage für den Webkanal im **Create_First_IC_templates** Ordner:

1. Navigieren Sie zum entsprechenden Vorlagenordner durch Auswahl von **Tools** > **Vorlagen** > **Create_First_IC_templates**.
1. Tippen Sie auf **Erstellen**.
1. Wählen Sie im Konfigurationsassistenten **Vorlagentyp wählen** den Typ **Interaktive Kommunikation - Webkanal** und tippen Sie auf **Weiter**.
1. Geben Sie im Konfigurationsassistenten **Vorlagendetails** **Create_First_IC_Web_Template** als Vorlagentitel ein. Geben Sie eine optionale Beschreibung ein und tippen Sie auf **Erstellen**.

   Eine Bestätigungsmeldung, dass **Create_First_IC_Web_Template** angezeigt wird.

1. Tippen **Öffnen** , um die Vorlage im Vorlageneditor zu öffnen.
1. Auswählen **Anfänglicher Inhalt** aus der Dropdown-Liste neben dem **Vorschau** -Option.

   ![template_editor_initial_content](assets/template_editor_initial_content.png)

1. Tippen Sie auf **Stammbereich** und dann auf **+**, um die Liste der Komponenten anzuzeigen, die Sie der Vorlage hinzufügen können.
1. Auswählen **Bedienfeld** aus der Liste, um ein Bedienfeld über dem **Stammbereich**.
1. Wählen Sie die **Inhalt** im linken Bereich. Das neue Bedienfeld, das in Schritt 8 hinzugefügt wurde, wird unter dem **Stammbereich** in der Inhaltsstruktur.

   ![content_tree_root_panel](assets/content_tree_root_panel.png)

1. Wählen Sie die Tabelle aus und tippen Sie auf ![configure_icon](assets/configure_icon.png) (Konfigurieren).
1. Im Bereich Eigenschaften :

   1. Angeben **billdetails** im Feld &quot;Name&quot;ein.
   1. Angeben **Rechnungsdetails** im Feld Titel .
   1. Auswählen **1** von **Spaltenanzahl** Dropdown-Liste.
   1. Tippen Sie auf das ![Symbol „Fertig“](assets/done_icon.png), um die Eigenschaften zu speichern.

   Der Name des Bedienfelds wird aktualisiert auf **Rechnungsdetails** in der Inhaltsstruktur.

1. Wiederholen Sie die Schritte 7 bis 11, um der Vorlage Bedienfelder mit den folgenden Eigenschaften hinzuzufügen:

   | Name | Titel | Anzahl der Spalten |
   |---|---|---|
   | customerdetails | Kundendetails | 1 |
   | billsummary | Rechnungszusammenfassung | 1 |
   | Zusammenfassende Gebühren | Zusammenfassung der Gebühren | 2 |
   | itemisedcalls | Aufrufe | 1 |
   | paynow | Jetzt bezahlen | 2 |
   | vas | Mehrwertdienste | 1 |

   Die folgende Abbildung zeigt die Inhaltsstruktur, nachdem alle Bedienfelder zur Vorlage hinzugefügt wurden:

   ![content_tee_all_panels](assets/content_tee_all_panels.png)

### Aktivieren der Vorlage {#enable-the-template}

Nachdem Sie die Webvorlage erstellt haben, müssen Sie sie aktivieren, um die Vorlage beim Erstellen der interaktiven Kommunikation zu verwenden.

Führen Sie die folgenden Schritte aus, um die Webvorlage zu aktivieren:

1. Tippen **Instrumente** ![Instrumente](assets/tools-icon.svg) > **Vorlagen**.
1. Navigieren Sie zur Vorlage **Create_First_IC_Web_Template**, wählen Sie sie aus und tippen Sie auf **Aktivieren**.
1. Registerkarte **Aktivieren** erneut zu bestätigen.

   Die Vorlage ist aktiviert und ihr Status wird als Aktiviert angezeigt. Sie können diese Vorlage beim Erstellen der interaktiven Kommunikation für den Webkanal verwenden.

### Aktivieren von Schaltflächen in interaktiven Kommunikationen {#enabling-buttons-in-interactive-communications}

Je nach Anwendungsfall müssen Sie die Variable **Jetzt bezahlen** und **Abonnieren** Schaltflächen (adaptive Formularkomponenten) in der interaktiven Kommunikation. Führen Sie die folgenden Schritte aus, um die Verwendung dieser Schaltflächen in der interaktiven Kommunikation zu aktivieren:

1. Wählen Sie **Struktur** aus der Dropdown-Liste neben der Option **Vorschau**.
1. Wählen Sie im Stammbereich **Dokument-Container** mit der Inhaltsstruktur und tippen Sie auf **Richtlinie**, um die Komponenten auszuwählen, die für die Verwendung in der interaktiven Kommunikation erlaubt sind.

   ![structure_configure_policy](assets/structure_configure_policy.png)

1. Wählen Sie auf der Registerkarte **Zugelassene Komponenten** im Abschnitt **Eigenschaften** die Option **Schaltfläche** aus den Komponenten **Adaptives Formular**.

   ![allowed_components_af](assets/allowed_components_af.png)

1. Tippen Sie auf das ![Symbol „Fertig“](assets/done_icon.png), um die Eigenschaften zu speichern.
