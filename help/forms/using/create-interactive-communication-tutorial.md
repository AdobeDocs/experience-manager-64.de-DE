---
title: "Tutorial: Erstellen einer interaktiven Kommunikation "
seo-title: Create an Interactive Communication for Print and Web
description: Erstellen Sie eine interaktive Kommunikation mit allen Bausteinen
seo-description: Create an Interactive Communication using all building blocks
uuid: 91702f41-5c19-4840-a3b5-59d69003fd67
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 39262cb1-1447-469a-9c01-886f66eeec74
feature: Interactive Communication
exl-id: b4ec8004-d100-4bcb-b2d8-0928e0955d3f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2049'
ht-degree: 59%

---

# Tutorial: Erstellen einer interaktiven Kommunikation {#tutorial-create-interactive-communication}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Erstellen Sie eine interaktive Kommunikation mit allen Bausteinen

![Interaktive Kommunikation gestalten](assets/styleaf.png)

Dieses Tutorial ist ein Schritt in der Reihe [Erstellen Sie Ihre erste interaktive Kommunikation](/help/forms/using/create-your-first-interactive-communication.md). Es wird empfohlen, der Reihe in chronologischer Reihenfolge zu folgen, um den vollständigen Anwendungsfall des Tutorials zu verstehen, auszuführen und zu demonstrieren.

Nachdem Sie alle Bausteine wie Formulardatenmodell, Dokumentfragmente, Vorlagen und Designs für die Webversion erstellt haben, können Sie mit der Erstellung einer interaktiven Kommunikation beginnen.

Interaktive Kommunikation kann über zwei Kanäle bereitgestellt werden: Druck und Web. Sie können auch eine interaktive Kommunikation mit dem Druckkanal als Übergeordnet erstellen. Die Option &quot;Als Übergeordnet drucken&quot;für den Webkanal stellt sicher, dass der Inhalt, die Vererbung und die Datenbindung des Webkanals vom Druckkanal abgeleitet werden. Außerdem wird sichergestellt, dass die im Druckkanal vorgenommenen Änderungen im Webkanal synchronisiert werden. Die Autoren der interaktiven Kommunikation dürfen jedoch die Vererbung für bestimmte Komponenten im Webkanal unterbrechen.

Dieses Tutorial führt Sie durch die Schritte zum Erstellen interaktiver Kommunikation für Druck- und Webkanäle. Am Ende dieses Tutorials können Sie Folgendes:

* Erstellen der interaktiven Kommunikation für den Druckkanal
* Erstellen der interaktiven Kommunikation für den Webkanal
* Erstellen Sie Print- und Web-interaktive Kommunikation mit Druck als Übergeordnet

## Erstellen interaktiver Kommunikation für Druck und Web ohne Synchronisierung {#create-interactive-communications-for-print-and-web-with-no-synchronization}

### Erstellen einer interaktiven Kommunikation für den Druckkanal {#create-interactive-communication-for-print-channel}

Im Folgenden finden Sie eine Liste der Ressourcen, die bereits in diesem Tutorial erstellt wurden und beim Erstellen der interaktiven Kommunikation für den Druckkanal benötigt werden:

**Druckvorlage:** [create_first_ic_print_template](/help/forms/using/create-templates-print-web.md)

**Formulardatenmodell:** [FDM_Create_First_IC](create-form-data-model-tutorial.md)

**Dokumentfragmente:** [bill_details_first_ic, customer_details_first_ic, bill_summary_first_ic, summary_charges_first_ic](/help/forms/using/create-document-fragments.md)

**Layout-Fragmente:** [table_lf](/help/forms/using/create-templates-print-web.md)

**Bilder:** PayNow und ValueAddedServices

1. Melden Sie sich bei Ihrer AEM-Autoreninstanz an und navigieren Sie zu **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]**.
1. Tippen Sie auf **Erstellen** und wählen Sie **Interaktive Kommunikation** aus. Der Assistent **Erstellen einer interaktiven Kommunikation** wird angezeigt.
1. Geben Sie **create_first_ic** im Feld **Titel** und im Feld **Name** an. Wählen Sie **FDM_Create_First_IC** als Formulardatenmodell und tippen Sie auf **Weiter**.
1. Im Assistenten **Kanäle**:

   1. Geben Sie **create_first_ic_print_template** als Druckvorlage an und tippen Sie auf **Auswählen**. Stellen Sie sicher, dass das Kontrollkästchen **Druck als Master für Webkanal verwenden** nicht aktiviert ist.
   1. Geben Sie den Ordner **Create_First_IC_templates** > **Create_First_IC_Web_Template** als Web-Vorlage an und tippen Sie auf **Auswählen**.
   1. Tippen Sie auf **Erstellen**.

   Es wird eine Bestätigungsmeldung angezeigt, dass die interaktive Kommunikation erfolgreich erstellt wurde.

1. Tippen **Bearbeiten** , um die interaktive Kommunikation im rechten Bereich zu öffnen.
1. Wechseln Sie zur Registerkarte **Assets** und wenden Sie den Filter an, um nur die Dokumentfragmente im linken Bereich anzuzeigen.
1. Ziehen Sie die folgenden Dokumentfragmente per Drag-and-Drop in die Zielbereiche der interaktiven Kommunikation:

   | Dokumentfragment | Zielbereich |
   |---|---|
   | bill_details_first_ic | BillDetails |
   | customer_details_first_ic | CustomerDetails |
   | bill_summary_first_ic | BillSummary |
   | summary_charges_first_interactive_communication | Gebühren |

   ![create_first_ic_doc_fragments](assets/create_first_ic_doc_fragments.png)

1. Tippen Sie auf den Zielbereich **Diagramme** und anschließend auf **+**, um eine Komponente **Diagramm** hinzuzufügen.
1. Tippen Sie auf die Diagrammkomponente und wählen Sie ![configure_icon](assets/configure_icon.png) (Konfigurieren) aus. Die Diagrammeigenschaften werden im linken Bereich angezeigt:

   1. Geben Sie einen Namen für das Diagramm an.
   1. Wählen Sie **Kreis** aus der Dropdownliste **Diagrammtyp**.
   1. Wählen Sie die Eigenschaft **calltype** aus dem Datenmodellobjekt **calls** im Abschnitt **X-Achse** Tippen Sie auf ![done_icon](assets/done_icon.png).
   1. Wählen Sie **Frequenz** aus der Dropdown-Liste **Funktion**.
   1. Wählen Sie die Eigenschaft **calltype** aus dem Datenmodellobjekt **calls** im Abschnitt **Y-Achse** aus. Tippen Sie auf ![done_icon](assets/done_icon.png).
   1. Durch das Tippen auf ![done_icon](assets/done_icon.png) werden die Diagrammeigenschaften gespeichert.

1. Wechseln Sie zur Registerkarte **Elemente** und wenden Sie den Filter an, um nur die Layout-Fragmente im linken Bereich anzuzeigen. Ziehen Sie das Layout **table_lf** per Drag-and-Drop in den Zielbereich **Einzeln aufgeführte Anrufe**.
1. Wählen Sie das Textfeld in der Spalte **Datum** aus und tippen Sie auf ![configure_icon](assets/configure_icon.png) (Konfigurieren).
1. Wählen Sie **Datenmodellobjekt** aus der Dropdown-Liste **Bindungstyp** und wählen Sie **calls** > **calldate**. Zum Speichern der Eigenschaften tippen Sie zweimal auf ![done_icon](assets/done_icon.png).

   Erstellen Sie eine Bindung mit **calltime**, **callnumber**, **callduration** und **callcharges** für Textfelder in den Spalten **Zeit**, **Anzahl**, **Dauer** und **Kosten**.

1. Um eine **Bild**-Komponente hinzuzufügen, tippen Sie auf den Zielbereich **PayNow** und anschließend auf **+**.
1. Tippen Sie auf die Bildkomponente und wählen Sie ![configure_icon](assets/configure_icon.png) (Konfigurieren) aus. Die Bildeigenschaften werden im linken Bereich angezeigt:

   1. Angeben **PayNow** als Name des Bildes im **Name** -Feld.
   1. Tippen Sie auf **Hochladen**, wählen Sie das im lokalen Dateisystem gespeicherte Bild aus und tippen Sie auf **Öffnen**.
   1. Zum Speichern der Bildeigenschaften tippen Sie auf ![done_icon](assets/done_icon.png).

1. Um das Bild **ValueAddedServices** dem Zielbereich **ValueAddedServices** hinzuzufügen, wiederholen Sie die Schritte 13 und 14.

### Interaktive Kommunikation für Webkanal erstellen {#create-interactive-communication-for-web-channel}

Im Folgenden finden Sie eine Liste der Ressourcen, die bereits in diesem Tutorial erstellt wurden und beim Erstellen der interaktiven Kommunikation für den Webkanal benötigt werden:

**Webvorlage:** [Create_First_IC_Web_Template](/help/forms/using/create-templates-print-web.md)

**Formulardatenmodell:** [FDM_Create_First_IC](create-form-data-model-tutorial.md)

**Dokumentfragmente:** [bill_details_first_ic, customer_details_first_ic, bill_summary_first_ic, summary_charges_first_ic](/help/forms/using/create-document-fragments.md)

**Bilder:** PayNowWeb und ValueAddedServicesWeb

1. Melden Sie sich bei Ihrer AEM-Autoreninstanz an und navigieren Sie zu **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]**.
1. Tippen Sie auf **Erstellen** und wählen Sie **Interaktive Kommunikation** aus. Der Assistent **Erstellen einer interaktiven Kommunikation** wird angezeigt.
1. Geben Sie **create_first_ic** im Feld **Titel** und im Feld **Name** an. Wählen Sie **FDM_Create_First_IC** als Formulardatenmodell und tippen Sie auf **Weiter**.
1. Im Assistenten **Kanäle**:

   1. Geben Sie **create_first_ic_print_template** als Druckvorlage an und tippen Sie auf **Auswählen**. Stellen Sie sicher, dass das Kontrollkästchen **Druck als Master für Webkanal verwenden** nicht aktiviert ist.
   1. Geben Sie den Ordner **Create_First_IC_templates** > **Create_First_IC_Web_Template** als Web-Vorlage an und tippen Sie auf **Auswählen**.
   1. Tippen Sie auf **Erstellen**.

   Es wird eine Bestätigungsmeldung angezeigt, dass die interaktive Kommunikation erfolgreich erstellt wurde.

1. Tippen **Bearbeiten** , um die interaktive Kommunikation im rechten Bereich zu öffnen.
1. Tippen Sie auf die Registerkarte **Kanäle** im linken Bereich, und tippen Sie auf **Web**.
1. Wechseln Sie zur Registerkarte **Elemente** und wenden Sie den Filter an, um nur die Dokumentfragmente im linken Bereich anzuzeigen.
1. Ziehen Sie die folgenden Dokumentfragmente per Drag-and-Drop in die Zielbereiche der interaktiven Kommunikation:

   | Dokumentfragment | Zielbereich |
   |---|---|
   | bill_details_first_ic | BillDetails |
   | customer_details_first_ic | CustomerDetails |
   | bill_summary_first_ic | BillSummary |
   | summary_charges_first_interactive_communication | Gebühren |

1. Tippen Sie auf den Zielbereich **Zusammenfassung der Gebühren** und anschließend auf **+**, um eine Komponente **Diagramm** hinzuzufügen.
1. Tippen Sie auf die Diagrammkomponente und wählen Sie ![configure_icon](assets/configure_icon.png) (Konfigurieren) aus. Die Diagrammeigenschaften werden im linken Bereich angezeigt:

   1. Geben Sie einen Namen für das Diagramm an.
   1. Wählen Sie **Kreis** aus der Dropdownliste **Diagrammtyp**.
   1. Wählen Sie die Eigenschaft **calltype** aus dem Datenmodellobjekt **calls** im Abschnitt **X-Achse** Tippen Sie auf ![done_icon](assets/done_icon.png).
   1. Wählen Sie **Frequenz** aus der Dropdown-Liste **Funktion**.
   1. Wählen Sie die Eigenschaft **calltype** aus dem Datenmodellobjekt **calls** im Abschnitt **Y-Achse** aus. Tippen Sie auf ![done_icon](assets/done_icon.png).
   1. Tippen Sie auf ![done_icon](assets/done_icon.png), um die Diagrammeigenschaften zu speichern.

1. Wählen Sie die Registerkarte **Datenquellen** aus dem linken Bereich und ziehen Sie das Datenmodellobjekt **calls** in den Zielbereich **Einzeln aufgeführte Anrufe**. Alle Eigenschaften im Datenmodellobjekt **calls** werden als Tabellenspalten im Zielbereich **Einzeln aufgeführte Anrufe** im rechten Bereich angezeigt.

   Basierend auf dem Anwendungsfall benötigen Sie die Spalten „Anrufdatum“, „Anrufzeit“, „Rufnummer“, „Anrufdauer“ und „Anrufkosten“ in der Tabelle.

   ![table_ic_web](assets/table_ic_web.png)

1. Wählen Sie die Tabellenspaltenüberschrift **Mobilenum** und dann **Weitere Optionen** > **Spalte löschen** aus. Löschen Sie auf ähnliche Weise die Spalte **Anruftyp**.
1. Wählen Sie die Tabellenspaltenüberschrift **Calldate** aus und tippen Sie auf ![Bearbeiten](assets/edit.png) (Bearbeiten), um den Text in **Anrufdatum** umzubenennen. Benennen Sie auf ähnliche Weise andere Spaltenüberschriften in der Tabelle um.
1. Fügen Sie je nach Anwendungsfall eine **Jetzt bezahlen** in der interaktiven Kommunikation, die dem Benutzer die Möglichkeit bietet, die Zahlung durch Klicken auf die Schaltfläche vorzunehmen. Führen Sie die folgenden Schritte aus, um die Schaltfläche einzufügen:

   1. Tippen Sie auf den Zielbereich **Jetzt bezahlen** und anschließend auf **+**, um eine Komponente **Text** hinzuzufügen.
   1. Tippen Sie auf die Textkomponente und anschließend auf ![Bearbeiten](assets/edit.png) (Bearbeiten).
   1. Benennen Sie den Text in **Jetzt bezahlen**.
   1. Wählen Sie den Text aus und tippen Sie auf das Symbol Hyperlink .
   1. Geben Sie die Zahlungs-URL im **Pfad** -Feld.
   1. Auswählen **Neue Registerkarte** von **Target** Dropdown-Liste.
   1. Tippen Sie auf ![done_icon](assets/done_icon.png), um die Hyperlink-Eigenschaften zu speichern.

1. Wählen Sie **Style** aus der Dropdown-Liste neben der Option **Vorschau**.

   ![select_style_ic_web](assets/select_style_ic_web.png)

1. Gestalten Sie den Hyperlink-Text so, dass er als Schaltfläche in der interaktiven Kommunikation angezeigt wird. Gehen Sie dazu wie folgt vor:

   1. Tippen Sie auf die Textkomponente und wählen Sie ![Bearbeiten](assets/edit.png) (Bearbeiten) aus.
   1. Geben Sie im Abschnitt **Rahmen** **1.5px** als **Rahmenbreite** ein, wählen Sie **Durchgehend** als **Rahmenstil** ein und geben Sie **46px** als **Rahmenradius** ein.
   1. Wählen Sie Rot als Hintergrundfarbe für die Schaltfläche aus dem **Hintergrund** Abschnitt.
   1. Im **Marge** -Feld für **Dimensionen und Position** Tippen Sie auf **Gleichzeitig bearbeiten** und legen Sie die **Right** margin as **450 px**. Die Felder Oben, Unten und Links werden leer gelassen.

   ![ic_web_hyperlink](assets/ic_web_hyperlink.png)

1. Tippen Sie auf den Zielbereich **Jetzt bezahlen** und anschließend auf **+**, um eine Komponente **Bild** hinzuzufügen.
1. Tippen Sie auf die Bildkomponente und wählen Sie ![configure_icon](assets/configure_icon.png) (Konfigurieren) aus. Die Bildeigenschaften werden im linken Bereich angezeigt:

   1. Angeben **PayNow** als Name des Bildes im **Name** -Feld.
   1. Tippen Sie auf **Hochladen**, wählen Sie das im lokalen Dateisystem gespeicherte Bild **PayNowWeb** aus und tippen Sie auf **Öffnen**.
   1. Tippen Sie auf ![done_icon](assets/done_icon.png), um die Bildeigenschaften zu speichern.

1. Fügen Sie je nach Anwendungsfall die Schaltfläche **Abonnieren** in die interaktive Kommunikation ein, die dem Benutzer die Option bietet, den Mehrwert-Service durch Klicken auf die Schaltfläche zu abonnieren.

   Wiederholen Sie die Schritte 13 bis 17, um eine Schaltfläche **Abonnieren** zum Zielbereich **Mehrwert - Service** hinzuzufügen und das Bild **ValueAddedServicesWeb** hinzufügen.

## Erstellen interaktiver Kommunikation für Druck und Web mit automatischer Synchronisierung {#create-interactive-communications-for-print-and-web-with-auto-synchronization}

Sie können auch eine interaktive Kommunikation erstellen, indem Sie die automatische Synchronisierung zwischen Druck- und Webkanälen aktivieren. Um die automatische Synchronisierung zu aktivieren, wählen Sie beim Erstellen der interaktiven Kommunikation die Option Als Übergeordnet drucken aus. Durch Auswahl der Option Als Übergeordnet drucken wird sichergestellt, dass der Inhalt, die Vererbung und die Datenbindung des Webkanals vom Druckkanal abgeleitet werden. Außerdem wird sichergestellt, dass die im Druckkanal vorgenommenen Änderungen im Webkanal übernommen werden.

Führen Sie die folgenden Schritte aus, um den Webkanalinhalt mithilfe des Druckkanals abzuleiten:

1. Melden Sie sich bei Ihrer AEM-Autoreninstanz an und navigieren Sie zu **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]**.
1. Tippen Sie auf **Erstellen** und wählen Sie **Interaktive Kommunikation** aus. Der Assistent **Erstellen einer interaktiven Kommunikation** wird angezeigt.
1. Geben Sie **create_first_ic** im Feld **Titel** und im Feld **Name** an. Wählen Sie **FDM_Create_First_IC** als Formulardatenmodell und tippen Sie auf **Weiter**.
1. Im Assistenten **Kanäle**:

   1. Geben Sie **create_first_ic_print_template** als Druckvorlage an und tippen Sie auf **Auswählen**.
   1. Aktivieren Sie das Kontrollkästchen **Druck als Master für Webkanal verwenden**.
   1. Geben Sie den Ordner **Create_First_IC_templates** > **Create_First_IC_Web_Template** als Webvorlage ein und tippen Sie auf **Auswählen**.
   1. Tippen Sie auf **Erstellen**.

   Es wird eine Bestätigungsmeldung angezeigt, dass die interaktive Kommunikation erfolgreich erstellt wurde.

1. Tippen **Bearbeiten** , um die interaktive Kommunikation im rechten Bereich zu öffnen.
1. Führen Sie die Schritte 6–15 des Abschnitts [Erstellen einer interaktiven Kommunikation für den Druckkanal](#create-interactive-communication-for-print-channel) aus.
1. Tippen Sie auf die Registerkarte **Kanäle** im linken Bereich und tippen Sie auf **Web**, um automatisch generieren Inhalte für den Webkanal aus dem Druckkanal zu generieren.
1. Da Sie in Schritt 4 das Kontrollkästchen **Druck als Master für Webkanal verwenden** aktiviert haben, werden Inhalt und Bindungen für den Webkanal automatisch aus dem Druckkanal generiert.

   Der Inhalt des Druckkanals wird unter dem Inhalt der Webkanal-Vorlage eingefügt. Um den Webkanalinhalt zu ändern, der automatisch vom Druckkanal generiert wurde, können Sie die Vererbung für einen beliebigen Zielbereich abbrechen.

   Bewegen Sie den Mauszeiger über den entsprechenden Zielbereich im Webkanal und wählen Sie ![cancelinheritance](assets/cancelinheritance.png) (Vererbung abbrechen), tippen Sie dann im Dialogfeld **Vererbung abbrechen** auf **Ja**.

   ![cancel_inheritance_web_channel](assets/cancel_inheritance_web_channel.png)

   Wenn Sie die Vererbung einer Komponente abgebrochen haben, können Sie sie erneut aktivieren. Um die Vererbung wieder zu aktivieren, bewegen Sie die Maus über die Grenze des relevanten Zielbereichs, der die Komponente enthält, und tippen Sie auf ![reenableinheritance](assets/reenableinheritance.png).

1. Wählen Sie die **Inhalt** im linken Bereich.
1. Ziehen Sie den automatisch generierten Webkanalinhalt per Drag-and-Drop in die vorhandenen Bedienfelder in der Webvorlage unter Verwendung der Inhaltsstruktur. Im Folgenden finden Sie eine Liste der Komponenten, die neu angeordnet werden müssen:

   * Komponente &quot;Rechnungsdetails&quot;im Bedienfeld &quot;Rechnungsdetails&quot;
   * Komponente &quot;Kundendetails&quot;im Bereich &quot;Kundendetails&quot;
   * Komponente &quot;Rechnungszusammenfassung&quot;im Bedienfeld &quot;Rechnungszusammenfassung&quot;
   * Komponente &quot;Zusammenfassung der Gebühren&quot;im Bedienfeld &quot;Zusammenfassung der Gebühren&quot;
   * Layout-Fragment (Tabelle) in das Bedienfeld &quot;Auflistungen&quot;

   ![ic_web_content_tree](assets/ic_web_content_tree.png)

1. Wiederholen Sie die Schritte 13 - 18 von [Interaktive Kommunikation für Webkanal erstellen](#create-interactive-communication-for-web-channel), um die Hyperlinks **Jetzt bezahlen** und **Abonnieren** in den Webkanal der interaktiven Kommunikation einzufügen.
