---
title: Varianten – Erstellen von Fragmentinhalten
seo-title: Variations - Authoring Fragment Content
description: Varianten ermöglichen es Ihnen, Inhalte für das Fragment zu erstellen und dann Varianten des Inhalts entsprechend dem Zweck zu erstellen (falls erforderlich).
seo-description: Variations allow you to author content for the fragment, then create variations of that content according to purpose (if required).
uuid: affccda0-be5f-47d2-85b6-8701b77ac932
contentOwner: AEM Docs
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: content-fragments
content-type: reference
discoiquuid: 1cdb2dfc-623b-44cf-9a7b-98cfabbb1d0c
exl-id: 15a5fdc9-2878-4f95-83ee-02a2899aeb43
feature: Content Fragments
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1774'
ht-degree: 70%

---

# Varianten – Erstellen von Fragmentinhalten {#variations-authoring-fragment-content}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

>[!CAUTION]
>
>Einige Inhaltsfragmentfunktionen erfordern die Anwendung von [AEM 6.4 Service Pack 2 (6.4.2.0 oder höher)](../release-notes/sp-release-notes.md).

[Varianten](content-fragments.md#constituent-parts-of-a-content-fragment) sind eine wichtige Funktion für Inhaltsfragmente, da sie Ihnen die Möglichkeit bieten, Kopien des primären Inhalts zu erstellen und zu bearbeiten und diese für bestimmte Kanäle und/oder Szenarien zu verwenden.

Aus dem **Varianten** können Sie Folgendes tun:

* [Inhalt eingeben](#authoring-your-content) für Ihr Fragment
* [Erstellen und Verwalten von Varianten](#managing-variations) des **primären** Inhalts

Führen Sie je nach bearbeitetem Datentyp eine Reihe weiterer Aktionen durch. Beispiel:

* [Einfügen von visuellen Assets in Ihr Fragment](#inserting-assets-into-your-fragment) (Bilder)
* Wählen Sie zwischen [Rich-Text](#rich-text), [Nur Text](#plain-text) und [Markdown](#markdown) zur Bearbeitung

* [Inhalt hochladen](#uploading-content)

* [Anzeigen von Schlüsselstatistiken](#viewing-key-statistics) (über mehrzeiligen Text)
* [Zusammenfassen von Text](#summarizing-text)

* [Synchronisieren von Varianten mit dem primären Inhalt](#synchronizing-with-master)

>[!CAUTION]
>
>Nachdem ein Fragment veröffentlicht und/oder referenziert wurde, zeigt AEM eine Warnmeldung an, wenn ein Autor das Fragment erneut zur Bearbeitung öffnet. Dies dient als Hinweis darauf, dass am Fragment vorgenommene Änderungen sich auch auf die referenzierten Seiten auswirken.

## Verfassen Ihres Inhalts {#authoring-your-content}

Wenn Sie das Inhaltsfragment zur Bearbeitung öffnen, wird die **Varianten** ist standardmäßig geöffnet. Hier können Sie den Inhalt bearbeiten, und zwar den der primären Version sowie sämtlicher Varianten. Sie haben folgende Möglichkeiten:

* Nehmen Sie Ihre Änderungen direkt in der Registerkarte **Varianten** vor
* Öffnen Sie die [Vollbild-Editor](#full-screen-editor) an:

   * das [Format](#formats) auszuwählen
   * weitere Bearbeitungsoptionen anzuzeigen ([Rich-Text](#rich-text)-Format)
   * auf eine Reihe von [Aktionen](#actions)zuzugreifen

Beispiel:

* Bearbeiten eines einfachen Fragments

   Ein einfaches Fragment besteht aus einem mehrzeiligen Textfeld (visuelle Assets können über den Vollbild-Editor hinzugefügt werden).

   ![cfm-6420-21](assets/cfm-6420-21.png)

* Bearbeiten eines Fragments mit strukturiertem Inhalt

   Ein strukturiertes Fragment enthält verschiedene Felder verschiedener Datentypen, die im Inhaltsmodell definiert wurden. Für mehrzeilige Felder muss die Variable [Vollbild-Editor](#full-screen-editor) ist verfügbar.

   ![cfm-6420-16](assets/cfm-6420-16.png)

### Vollbild-Editor {#full-screen-editor}

Beim Bearbeiten eines mehrzeiligen Textfelds können Sie den Vollbild-Editor öffnen:

![cf-fullscreeneditor-icon](assets/cf-fullscreeneditor-icon.png)

Der Vollbild-Editor bietet Folgendes:

* Zugriff auf verschiedene [Aktionen](#actions)
* Je nach [format](#formats), zusätzliche Formatierungsoptionen ([Rich-Text](#rich-text))

### Aktionen {#actions}

Die folgenden Aktionen sind ebenfalls verfügbar (für sämtliche [Formate](#formats)), wenn der Vollbild-Editor (d. h. mehrzeiliger Text) geöffnet ist:

* Wählen Sie die [format](#formats) ([Rich-Text](#rich-text), [Nur Text](#plain-text), [Markdown](#markdown))
* [Textstatistiken anzeigen](#viewing-key-statistics)
* [Inhalt hochladen](#uploading-content)
* [Mit primärer Version synchronisieren](#synchronizing-with-master) (beim Bearbeiten einer Variante)
* [Zusammenfassen von Text](#summarizing-text)
* [Text kommentieren](content-fragments-variations.md#annotating-a-content-fragment)

* [Einfügen von visuellen Assets in Ihr Fragment](#inserting-assets-into-your-fragment) (Bilder)

### Formate {#formats}

Die Optionen für das Bearbeiten von mehrzeiligem Text hängen vom ausgewählten Format ab:

* [Rich-Text](#rich-text)
* [Nur Text](#plain-text)
* [Markdown](#markdown)

Das Format kann im Vollbild-Editor ausgewählt werden.

### Rich-Text {#rich-text}

Mit der Rich-Text-Bearbeitung können Sie Folgendes formatieren:

* Fett
* Kursiv
* Unterstrichen
* Ausrichtung: links, zentriert, rechts
* Aufzählungsliste
* Nummerierte Liste
* Einzug: erhöhen, verringern
* Hyperlinks erstellen/unterbrechen
* Öffnen Sie den Vollbild-Editor, in dem die folgenden Formatierungsoptionen zur Verfügung stehen:

   * Text/aus Word einfügen
   * Tabelle einfügen
   * Absatzstil: Absatz 1 Überschrift 1/2/3
   * [Einfügen visueller Assets](#inserting-assets-into-your-fragment)
   * Suchen
   * Suchen/Ersetzen
   * Rechtschreibprüfung
   * [Anmerkungen](content-fragments-variations.md#annotating-a-content-fragment)

Die [Aktionen](#actions) sind ebenfalls über den Vollbild-Editor verfügbar.

### Nur Text {#plain-text}

Nur Text ermöglicht die schnelle Eingabe von Inhalt ohne Formatierungs- oder Markdown-Informationen. Für weitere [Aktionen](#actions) können Sie auch den Vollbild-Editor öffnen.

>[!CAUTION]
>
>Wenn Sie **Nur Text** auswählen, gehen möglicherweise alle Formatierungen, Markierungen und/oder Assets verloren, die Sie in **Rich-Text** oder **Markdown** eingefügt haben.

### Markdown {#markdown}

>[!NOTE]
>
>Umfassende Informationen finden Sie unter [Markdown](content-fragments-markdown.md) Dokumentation.

Auf diese Weise können Sie Ihren Text mithilfe von Markdown formatieren. Sie können Folgendes definieren:

* Überschriften
* Absätze und Zeilenumbrüche
* Links
* Bilder
* Blockzitate
* Listen
* Hervorhebungen
* Code-Blöcke
* Umgekehrter Schrägstrich - Escape

Für weitere [Aktionen](#actions) können Sie auch den Vollbild-Editor öffnen.

>[!CAUTION]
>
>Wenn Sie zwischen **Rich-Text** und **Markdown** umschalten, treten möglicherweise unerwartete Effekte mit Blockzitaten und Code-Blöcken auf, da diese beiden Formate unterschiedlich verarbeitet werden.

### Anzeigen von wichtigen Statistiken {#viewing-key-statistics}

Wenn der Vollbild-Editor geöffnet ist, zeigt die Aktion **Textstatistik** eine Reihe von Informationen über den Text an. Beispiel:

![cfx-6420-22](assets/cfx-6420-22.png)

### Hochladen von Inhalt {#uploading-content}

Um die Erstellung von Inhaltsfragmenten zu vereinfachen, können Sie Text hochladen, der in einem externen Editor vorbereitet wurde, und ihn direkt in das Fragment einfügen.

### Zusammenfassung von Text {#summarizing-text}

Mithilfe der Zusammenfassung von Text können Benutzer die Länge des Textes auf eine vordefinierte Anzahl von Wörtern verringern, während die wichtigen Punkte und die allgemeine Bedeutung beibehalten werden.

>[!NOTE]
>
>Auf einer technischeren Stufe behält das System die Sätze bei, die in Übereinstimmung mit bestimmten Algorithmen das *beste Verhältnis von Informationsdichte und Eindeutigkeit* bieten.

>[!CAUTION]
>
>Das Inhaltsfragment muss einen gültigen Sprachordner als Vorgänger aufweisen. wird verwendet, um das zu verwendende Sprachmodell zu bestimmen.
>
>Beispiel: `en/` wie im folgenden Pfad:
>
>`/content/dam/my-brand/en/path-down/my-content-fragment`

>[!CAUTION]
>
>Englisch ist standardmäßig verfügbar.
>
>Andere Sprachen sind als Sprachmodellpakete von Software Distribution verfügbar:
>
>* [Französisch (fr) von Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?lang=de?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-fr)
>* [Deutsch (de) von Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?lang=de?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-de)
>* [Italienisch (it) von Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?lang=de?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-it)
>* [Spanisch (es) von Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?lang=de?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-es)
>


1. Wählen Sie **[!UICONTROL Primäre Version]** oder die erforderliche Variante aus.
1. Öffnen Sie den Vollbild-Editor.

1. Wählen Sie in der Symbolleiste die Option **[!UICONTROL Text zusammenfassen]** aus.

   ![cf-17](assets/cf-17.png)

1. Geben Sie den Zielwert der Wörter an und wählen Sie **[!UICONTROL Starten]**:
1. Der ursprüngliche Text wird nebeneinander mit der vorgeschlagenen Zusammenfassung angezeigt:

   * Alle zu beseitigenden Sätze werden rot hervorgehoben und durchgestrichen.
   * Klicken Sie auf einen markierten Satz, um ihn im zusammengefassten Inhalt zu behalten.
   * Klicken Sie auf einen nicht hervorgehobenen Satz, um ihn zu eliminieren.

   ![cfm-6420-23](assets/cfm-6420-23.png)

1. Wählen Sie **[!UICONTROL Zusammenfassen]** aus, um die Änderungen zu bestätigen.

### Anmerkungen zu Inhaltsfragmenten {#annotating-a-content-fragment}

So kommentieren Sie ein Fragment:

1. Wählen Sie **[!UICONTROL Primäre Version]** oder die erforderliche Variante aus.
1. Öffnen Sie den Vollbild-Editor.
1. Wählen Sie Text aus. Das Symbol **[!UICONTROL Anmerken]** wird verfügbar.

   ![cfm-6420-24](assets/cfm-6420-24.png)

1. Ein Dialogfeld wird geöffnet. Hier können Sie Ihre Anmerkungen eingeben.

1. Schließen Sie den Editor im Vollbildmodus und **[!UICONTROL speichern]** Sie das Fragment.

### Anzeigen, Bearbeiten und Löschen von Anmerkungen {#viewing-editing-deleting-annotations}

Anmerkungen:

* Sie werden durch die Markierung auf dem Text sowohl im Vollbildmodus als auch im normalen Modus des Editors angezeigt. Vollständige Details einer Anmerkung können angezeigt, bearbeitet und/oder gelöscht werden, indem Sie auf den markierten Text klicken, der das Dialogfeld erneut öffnet.

   >[!NOTE]
   >
   >Eine Dropdown-Liste wird angezeigt, wenn mehrere Anmerkungen auf einen Textausschnitt angewendet wurden.

* Wenn Sie den gesamten Text löschen, auf den die Anmerkung angewendet wurde, wird der Kommentar ebenfalls gelöscht.

* Kann durch das Auswählen der Registerkarte **[!UICONTROL Anmerkungen]** im Fragment-Editor aufgeführt und gelöscht werden.

   ![cfm-6420-25](assets/cfm-6420-25.png)

* Kann in der [Zeitleiste](https://helpx.adobe.com/experience-manager/6-3/assets/using/content-fragments-managing.html#timeline-for-content-fragments) für das ausgewählte Fragment angezeigt und gelöscht werden.

### Einfügen von Assets in das Fragment {#inserting-assets-into-your-fragment}

Um die Erstellung von Inhaltsfragmenten zu vereinfachen, können Sie [Assets](managing-assets-touch-ui.md) (Bilder) direkt zum Fragment hinzufügen.

Sie werden der Absatzsequenz des Fragments ohne Formatierung hinzugefügt. Formatierung kann durchgeführt werden, wenn die [Fragment wird auf einer Seite verwendet/referenziert](/help/sites-authoring/content-fragments.md).

>[!CAUTION]
>
>Diese Assets können auf einer referenzierenden Seite nicht verschoben oder gelöscht werden, sondern nur im Fragment-Editor.
>
>Die Formatierung des Assets (z. B. Größe) muss jedoch im [Seiteneditor](/help/sites-authoring/content-fragments.md). Die Darstellung des Assets im Fragment-Editor dient lediglich der Erstellung des Inhaltsflusses.

>[!NOTE]
>
>Es gibt verschiedene Methoden, um [Bilder](content-fragments.md#fragments-with-visual-assets) zu einem Fragment und/oder einer Seite hinzuzufügen.

1. Positionieren Sie den Cursor über der Position, an der Sie das Bild hinzufügen möchten.
1. Öffnen Sie das Suchdialogfeld mithilfe der Schaltfläche **[!UICONTROL Asset einfügen]**.

   ![cf-insertasset-icon](assets/cf-insertasset-icon.png)

1. In diesem Dialogfeld haben Sie folgende Möglichkeiten:

   * Navigieren zum erforderlichen Asset in DAM
   * Suchen nach dem Asset in DAM

   Nachdem Sie das gewünschte Asset gefunden haben, wählen Sie es aus, indem Sie auf die Miniatur klicken.

1. Verwenden Sie **[!UICONTROL Auswahl]**, um das Asset dem Absatzsystem Ihres Inhaltsfragments am aktuellen Speicherort hinzuzufügen.

   >[!CAUTION]
   >
   >Wenn Sie nach dem Hinzufügen eines Assets das Format ändern in:
   >
   >* **Klartext:** Das Asset geht im Fragment vollständig verloren.
   >* **Markdown:** Das Asset wird nicht angezeigt, ist aber immer noch vorhanden, wenn Sie zu **Rich Text** zurückkehren.


## Verwalten von Varianten  {#managing-variations}

### Erstellen einer Variante {#creating-a-variation}

Varianten ermöglichen die Abänderung von **primärem** Inhalt für einen bestimmten Zweck (sofern notwendig).

So erstellen Sie eine neue Variante:

1. Öffnen Sie das Fragment und stellen Sie sicher, dass der Seitenbereich sichtbar ist.
1. Wählen Sie im seitlichen Bedienfeld in der Symbolleiste die Option **[!UICONTROL Varianten]** aus.
1. Auswählen **[!UICONTROL Variante erstellen]**.
1. Daraufhin wird ein Dialogfeld geöffnet, in dem der **[!UICONTROL Titel]** und die **[!UICONTROL Beschreibung]** für die neue Variante angegeben werden.
1. Wählen Sie **[!UICONTROL Hinzufügen]** aus. Das Fragment **[!UICONTROL Primäre Version]** wird in die neue Variante kopiert, die nun zur [Bearbeitung](#editing-a-variation) geöffnet ist.

   >[!NOTE]
   >
   >Wenn eine neue Variante erstellt wird, wird immer die **Primäre Version** kopiert, nicht die gerade geöffnete Variante.

### Bearbeiten einer Variante {#editing-a-variation}

Sie können Änderungen am Varianteninhalt vornehmen, nachdem Sie entweder:

* [Variante erstellen](#creating-a-variation).
* Öffnen Sie ein vorhandenes Fragment und wählen Sie dann die gewünschte Variante aus dem Seitenbereich aus.

![cfm-6420-26](assets/cfm-6420-26.png)

### Umbenennen einer Variante {#renaming-a-variation}

So benennen Sie eine vorhandene Variante um:

1. Öffnen Sie das Fragment und wählen Sie über den Seitenbereich die Option **[!UICONTROL Varianten]** aus.
1. Wählen Sie die gewünschte Variante aus.
1. Wählen Sie im Dropdown-Menü **[!UICONTROL Aktionen]** die Option **[!UICONTROL Umbenennen]** aus.

1. Geben Sie im Dialogfeld den neuen **[!UICONTROL Titel]** und/oder die **[!UICONTROL Beschreibung]** ein.

1. Bestätigen Sie die **[!UICONTROL Umbenennen]** Aktion.

>[!NOTE]
>
>Dies betrifft nur die Variante **Titel**.

### Löschen einer Variante {#deleting-a-variation}

So löschen Sie eine vorhandene Variante:

1. Öffnen Sie das Fragment und wählen Sie über den Seitenbereich die Option **[!UICONTROL Varianten]** aus.
1. Wählen Sie die gewünschte Variante aus.
1. Wählen Sie im Dropdown-Menü **[!UICONTROL Aktionen]** die Option **[!UICONTROL Löschen]** aus.

1. Bestätigen Sie im Dialogfeld die Aktion **[!UICONTROL Löschen]**.

>[!NOTE]
>
>**Primäre Version** kann nicht gelöscht werden.

### Mit primärer Version synchronisieren {#synchronizing-with-master}

**Primäre Version** ist ein wesentlicher Bestandteil eines Inhaltsfragments und enthält die primäre Version des Inhalts, während die Varianten einzelne aktualisierte und maßgeschneiderten Versionen des Inhalts enthalten. Wenn die primäre Version aktualisiert wird, können diese Änderungen auch für die Varianten relevant sein und müssen daher auf diese übertragen werden.

Beim Bearbeiten einer Variante haben Sie Zugriff auf die Aktion zur Synchronisierung des aktuellen Elements der Variante mit der primären Version. Dadurch können Sie an der primären Version vorgenommene Änderungen automatisch in die entsprechende Variante kopieren.

>[!CAUTION]
>
>Die Synchronisierung ist nur verfügbar, um Änderungen *von der **primären Version**in die Variante* zu kopieren.
>
>Nur das aktuelle Element der Variante wird synchronisiert.
>
>Die Synchronisierung funktioniert nur mit Datentypen mit **mehrzeiligem Text**.
>
>Es ist nicht möglich, Änderungen *von einer Variante auf die **primäre Version*** zu übertragen.

1. Öffnen Sie das Inhaltsfragment im Fragment-Editor. Stellen Sie sicher, dass die **primäre Version** bearbeitet wurde.
2. Wählen Sie eine bestimmte Variante und dann die entsprechende Synchronisierungsaktion aus:

   * über den Dropdown-Selektor **Aktionen** – **Aktuelles Element mit primärer Version synchronisieren**
   * über die Symbolleiste des Vollbild-Editors – **Mit Master synchronisieren**

3. Master und Variante werden nebeneinander angezeigt:

   * Grün zeigt an, dass Inhalt (zur Variante) hinzugefügt wurde
   * Rot zeigt an, dass Inhalt entfernt wurde (aus der Variante)

   ![cfm-6420-27](assets/cfm-6420-27.png)

4. Wählen Sie **[!UICONTROL Synchronisieren]**. Die Variante wird dann aktualisiert und angezeigt.
