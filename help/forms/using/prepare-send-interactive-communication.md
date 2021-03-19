---
title: Interaktive Kommunikation mithilfe der Benutzeroberfläche für Agenten vorbereiten und senden
seo-title: Interaktive Kommunikation mithilfe der Benutzeroberfläche für Agenten vorbereiten und senden
description: 'Über die Benutzeroberfläche der Agenten können die Agenten die interaktive Kommunikation vorbereiten und an den Nachbearbeitungsprozess senden. Der Agent nimmt die erforderlichen Änderungen vor und übergibt die interaktive Kommunikation an einen Nachbearbeitungsprozess, z. B. E-Mail oder Druck. '
seo-description: Interaktive Kommunikation mithilfe der Benutzeroberfläche für Agenten vorbereiten und senden
uuid: d1a19b83-f630-4648-9ad2-a22374e31aa9
topic-tags: interactive-communications
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 110c86ea-9bd8-4018-bfcc-ca33e6b3f3ba
feature: Interaktive Kommunikation
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '1360'
ht-degree: 55%

---


# Interaktive Kommunikation mithilfe der Benutzeroberfläche für Agenten vorbereiten und senden {#prepare-and-send-interactive-communication-using-the-agent-ui}

Über die Benutzeroberfläche der Agenten können die Agenten die interaktive Kommunikation vorbereiten und an den Nachbearbeitungsprozess senden. Der Agent nimmt die erforderlichen Änderungen vor und übergibt die interaktive Kommunikation an einen Nachbearbeitungsprozess, z. B. E-Mail oder Druck.

## Überblick {#overview}

Nachdem eine interaktive Kommunikation erstellt wurde, kann der Agent die Interaktive Kommunikation in der Agent-Benutzeroberfläche öffnen und eine Empfänger-spezifische Kopie erstellen, indem er Daten eingibt und Inhalte und Anlagen verwaltet. Schließlich kann der Agent die interaktive Kommunikation an einen Nachbearbeitungsprozess senden.

Während der Vorbereitung der interaktiven Kommunikation mithilfe der Agent-Benutzeroberfläche verwaltet der Agent die folgenden Aspekte der interaktiven Kommunikation in der Agent-Benutzeroberfläche, bevor er sie an einen Nachbearbeitungsprozess übermittelt:

* **Daten**: Die Registerkarte „Daten“ der Benutzeroberfläche für Agenten zeigt alle vom Agenten bearbeitbaren Variablen und entsperrten Datenmodelleigenschaften in der interaktiven Kommunikation an. Diese Variablen/Eigenschaften werden beim Bearbeiten oder Erstellen von Dokumentfragmenten in der interaktiven Kommunikation erstellt. Die Registerkarte „Daten“ enthält auch alle Felder, die in der XDP/Druckkanalvorlage erstellt wurden. Die Registerkarte &quot;Daten&quot;wird nur angezeigt, wenn Variablen, Formulardatenmodelleigenschaften oder Felder in der interaktiven Kommunikation vorhanden sind, die vom Agenten bearbeitet werden können.
* **Inhalt**: Auf der Registerkarte „Inhalt“ verwalten Sie den Inhalt, z. B. Dokumentfragmente und die Inhaltsvariablen in der interaktiven Kommunikation. Der Agent kann die Änderungen im Dokument-Fragment wie zulässig vornehmen, während die Interaktive Kommunikation in den Eigenschaften dieser Dokument-Fragmente erstellt wird. Der Agent kann auch ein Dokumentfragment neu anordnen, hinzufügen/entfernen und Seitenumbrüche hinzufügen, sofern dies zulässig ist.
* **Anlagen**: Die Registerkarte &quot;Anlagen&quot;wird in der Benutzeroberfläche des Agenten nur angezeigt, wenn die interaktive Kommunikation über Anlagen verfügt oder der Agent über Bibliothekszugriff verfügt. Der Agent darf die Anlagen ändern oder bearbeiten.

## Vorbereitung der interaktiven Kommunikation mithilfe der Agent-Benutzeroberfläche {#prepare-interactive-communication-using-the-agent-ui}

1. Wählen Sie **[!UICONTROL Formulare]** > **[!UICONTROL Formulare &amp; Dokumente]**.
1. Wählen Sie die entsprechende interaktive Kommunikation aus und tippen Sie auf **[!UICONTROL Benutzeroberfläche des offenen Agenten]**.

   >[!NOTE]
   >
   >Die Benutzeroberfläche des Agenten funktioniert nur, wenn die ausgewählte Interaktive Kommunikation über einen Kanal zum Drucken verfügt.

   ![openagentiui](assets/openagentiui.png)

   Basierend auf dem Inhalt und den Eigenschaften der interaktiven Kommunikation wird die Benutzeroberfläche für Agenten mit den folgenden drei Registerkarten angezeigt: Daten, Inhalt und Anlage.

   ![agentuitabs](assets/agentuitabs.png)

   Fahren Sie mit der Dateneingabe, der Verwaltung des Inhalts und der Verwaltung der Anlagen fort.

### Daten eingeben {#enter-data}

1. Geben Sie auf der Registerkarte „Daten“ die erforderlichen Daten für Variablen, Formulardatenmodelleigenschaften und Druckvorlagenfelder (XDP) ein. Füllen Sie alle erforderlichen Felder mit einem Sternchen (&amp;ast;) aus, um die Schaltfläche **Senden** zu aktivieren.

   Tippen Sie auf einen Datenfeldwert in der Vorschau Interaktive Kommunikation, um das entsprechende Datenfeld auf der Registerkarte &quot;Daten&quot;zu markieren oder umgekehrt.

### Inhalt verwalten {#manage-content}

Verwalten Sie auf der Registerkarte „Inhalt“ den Inhalt, z. B. Dokumentfragmente und die Inhaltsvariablen in der interaktiven Kommunikation.

1. Wählen Sie **[!UICONTROL Inhalt]**. Die Registerkarte &quot;Inhalt&quot;der interaktiven Kommunikation wird angezeigt.

   ![agentuicontenttab](assets/agentuicontenttab.png)

1. Bearbeiten Sie auf der Registerkarte „Inhalt“ ggf. die Dokumentfragmente. Um den Fokus auf das relevante Fragment in der Inhaltshierarchie zu legen, können Sie entweder auf die entsprechende Zeile oder den entsprechenden Absatz in der Vorschau Interaktive Kommunikation tippen oder direkt in der Inhaltshierarchie auf das Fragment tippen.

   Beispielsweise wird das Dokumentfragment mit der Zeile „Jetzt online bezahlen ...“ in der Vorschau in der untenstehenden Grafik ausgewählt und das gleiche Dokumentfragment wurde auf der Registerkarte „Inhalt“ ausgewählt.

   ![contentmodulefocus](assets/contentmodulefocus.png)

   Wenn Sie auf der Registerkarte &quot;Inhalt&quot;oder &quot;Daten&quot;links oben auf der Vorschau auf &quot;Ausgewählte Module im Inhalt markieren&quot;( ![highlightsselectedModuleIncontentccr](assets/highlightselectedmodulesincontentccr.png)) tippen, können Sie die Funktion deaktivieren oder aktivieren, um zum Dokument-Fragment zu wechseln, wenn auf den entsprechenden Text, Absatz oder das Datenfeld in der Vorschau getippt/ausgewählt wird.

   Die Fragmente, die vom Agenten beim Erstellen der interaktiven Kommunikation bearbeitet werden dürfen, haben das Symbol Ausgewählten Inhalt bearbeiten ( ![iconeditselectedcontent](assets/iconeditselectedcontent.png)). Tippen Sie auf das Symbol „Ausgewählten Inhalt bearbeiten“, um das Fragment im Bearbeitungsmodus zu starten und Änderungen daran vorzunehmen. Verwenden Sie die folgenden Optionen zum Formatieren und Verwalten von Text:

   * [Formatierungsoptionen](#formattingtext)

      * [Formatierten Text aus anderen Anwendungen kopieren/einfügen](#pasteformattedtext)
      * [Teile des Textes markieren](#highlightemphasize)
   * [Sonderzeichen](#specialcharacters)
   * [Tastaturbefehle](/help/forms/using/keyboard-shortcuts.md)

   Weitere Informationen zu den Aktionen, die für verschiedene Fragmente des Dokuments in der Agent-Benutzeroberfläche verfügbar sind, finden Sie unter [Aktionen und Informationen in der Agent-Benutzeroberfläche](#actionsagentui).

1. Um der Druckausgabe der interaktiven Kommunikation einen Seitenumbruch hinzuzufügen, platzieren Sie den Cursor an der Stelle, an der Sie einen Seitenumbruch einfügen möchten, und wählen Sie &quot;Seitenumbruch vor&quot;oder &quot;Seitenumbruch nach&quot;( ![pagebreakVorher](assets/pagebreakbeforeafter.png)).

   Ein Platzhalter für einen expliziten Seitenumbruch wird in der interaktiven Kommunikation eingefügt. Sie können in der Druckvorschau anzeigen, wie sich ein expliziter Seitenumbruch auf die interaktive Kommunikation auswirkt.

   ![explicitpagebreak](assets/explicitpagebreak.png)

   Fahren Sie mit der Verwaltung der Anlagen der interaktiven Kommunikation fort.

### Anlagen verwalten {#manage-attachments}

1. Wählen Sie **[!UICONTROL Anlage]**. Die Benutzeroberfläche für Agenten zeigt die verfügbaren Anlagen so an, wie sie beim Erstellen der interaktiven Kommunikation eingerichtet wurden.

   Sie können festlegen, dass keine Anlage zusammen mit der interaktiven Kommunikation gesendet werden soll, indem Sie auf das Symbol &quot;Ansicht&quot;tippen, und Sie können auf das Kreuz in der Anlage tippen, um sie zu löschen (wenn der Agent die Anlage löschen oder ausblenden darf). Für die Anhänge, die beim Erstellen der interaktiven Kommunikation als obligatorisch festgelegt wurden, sind die Symbole „Anzeigen“ und „Löschen“ deaktiviert.

   ![attachmentsagentui](assets/attachmentsagentui.png)

1. Tippen Sie auf das Symbol &quot;Bibliothekszugriff&quot;( ![Bibliothekszugriff](assets/libraryaccess.png)), um auf die Inhaltsbibliothek zuzugreifen und DAM-Assets als Anlagen einzufügen.

   >[!NOTE]
   >
   >Das Symbol &quot;Bibliothekszugriff&quot;ist nur verfügbar, wenn beim Erstellen der Interaktiven Kommunikation der Bibliothekszugriff aktiviert wurde (in den Eigenschaften des Dokument-Containers des Kanals &quot;Drucken&quot;).

1. Wenn die Reihenfolge der Anhänge beim Erstellen der interaktiven Kommunikation nicht gesperrt war, können Sie die Reihenfolge der Anhänge neu anordnen, indem Sie einen Anhang auswählen und auf die Pfeile nach unten oder nach oben tippen.
1. Verwenden Sie Webvorschau und Druckvorschau, um zu sehen, ob die beiden Ausgaben Ihren Anforderungen entsprechen.

   Wenn die Vorschauen zufriedenstellend sind, tippen Sie auf **[!UICONTROL Senden]**, um die interaktive Kommunikation an einen Nachbearbeitungsprozess zu senden/zu senden. Um Änderungen vorzunehmen, beenden Sie die Vorschau, um zu den vorzunehmenden Änderungen zurückzukehren.

## Text formatieren {#formattingtext}

Beim Bearbeiten eines Textfragments in der Benutzeroberfläche für Agenten ändert sich die Symbolleiste abhängig vom Typ der von Ihnen vorgenommenen Änderungen: Schriftart, Absatz oder Liste:

![](assets/typeofformattingtoolbar.png) ![typeofformattingtoolbarFont, Symbolleiste](do-not-localize/fonttoolbar.png)

Schriftart-Symbolleiste

![Absatz-Symbolleiste](do-not-localize/paragraphtoolbar.png)

Absatz-Symbolleiste

![Liste-Symbolleiste](do-not-localize/listtoolbar.png)

Liste-Symbolleiste

### Teile des Textes markieren/hervorheben  {#highlightemphasize}

Um Teile eines Textes in einem bearbeitbaren Fragment hervorzuheben, wählen Sie den Text aus und tippen Sie auf „Hervorhebungsfarbe“.

![highlighttextagentui](assets/highlighttextagentui.png)

### Formatierten Text einfügen {#pasteformattedtext}

![pastedtext](assets/pastedtext.png)

### Sonderzeichen in Text einfügen {#specialcharacters}

Die Benutzeroberfläche für Agenten enthält integrierte Unterstützung für 210 Sonderzeichen. Der Administrator kann [Unterstützung für mehr/benutzerdefinierte Sonderzeichen durch Anpassung](/help/forms/using/custom-special-characters.md) hinzufügen.

#### Anlagenübermittlung {#attachmentdelivery}

* Wenn die interaktive Kommunikation mit serverseitigen APIs als interaktive oder nicht interaktive PDF gerendert wird, enthält die gerenderte PDF-Datei Anlagen als PDF-Anlagen.
* Wenn ein mit einer interaktiven Kommunikation verknüpfter Nachbearbeitungsprozess als Teil der Benutzeroberfläche &quot;Mit Agent senden&quot;geladen wird, werden Anlagen als Parameter &quot;Liste&lt;com.adobe.idp.Dokument> inAttachmentDocs&quot;übergeben.
* Vordefinierte Übermittlungsmechanismen, wie z. B. E-Mail und Drucken, übermitteln auch Anlagen zusammen mit einer PDF-Datei der interaktiven Kommunikation.

## Aktionen und Informationen, die auf der Benutzeroberfläche für Agenten verfügbar sind  {#actionsagentui}

### Dokumentfragmente {#document-fragments}

![](do-not-localize/contentoptionsdocfragments.png)

* **Pfeile nach oben bzw. nach unten**: Pfeile zum Verschieben von Dokumentenfragmenten nach unten oder oben in der interaktiven Kommunikation.
* **Löschen**: Wenn zulässig, löschen Sie das Dokumentfragment aus der interaktiven Kommunikation.
* **Seitenumbruch vor** (anwendbar für untergeordnete Fragmente des Zielbereichs): Fügt Seitenumbruch vor dem Dokumentfragment ein.
* **Einzug:** Einzug eines Dokumentenfragments vergrößern oder verkleinern.
* **Seitenumbruch nach**  (gilt für untergeordnete Fragmente des Bereichs Zielgruppe): Fügt nach dem Fragment des Dokuments einen Seitenumbruch ein.

![docfragoptions](assets/docfragoptions.png)

* Bearbeiten (nur Textfragmente): Öffnen Sie den Rich-Text-Editor zum Bearbeiten des Textdokumentfragments. Weitere Informationen finden Sie unter [Text formatieren](#formattingtext).

* Auswahl (Augensymbol): Schließt Dokumentfragmente in die interaktive Kommunikation ein/schließt sie daraus aus.
* Nicht ausgefüllte Werte (Info): Gibt die Anzahl der nicht ausgefüllten Variablen im Dokumentfragment an.

### Listendokumentfragmente  {#list-document-fragments}

![listoptions](assets/listoptions.png)

* Leere Linie einfügen: Fügt eine neue leere Linie ein.
* Auswahl (Augensymbol): Schließt Dokumentfragmente in die interaktive Kommunikation ein/schließt sie daraus aus.
* Aufzählungszeichen/Nummerierungen überspringen: Aktivieren Sie „Aufzählungszeichen/Nummerierungen überspringen“ im Listendokumentfragment.
* Nicht ausgefüllte Werte (Info): Gibt die Anzahl der nicht ausgefüllten Variablen im Dokumentfragment an.

