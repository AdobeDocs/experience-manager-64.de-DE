---
title: Texte in interaktiver Kommunikation
seo-title: Text in Interactive Communications
description: Erstellen und Bearbeiten von Textdokumentfragmenten zur Verwendung in interaktiver Kommunikation - Text ist einer der vier Arten von Dokumentfragmenten, die zum Erstellen interaktiver Kommunikation verwendet werden. Die anderen drei sind Bedingungen, Listen und Layout-Fragmente.
seo-description: Creating and editing text document fragments to be used in Interactive Communications
uuid: b2188d34-14f9-4c4e-bbe0-a2e763ed2958
topic-tags: interactive-communications
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 7677327a-cc56-413b-b2e3-7b10d0d0319d
feature: Interactive Communication
exl-id: a689aead-7b39-4d66-8922-ae8910c5e9ef
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2269'
ht-degree: 54%

---

# Texte in interaktiver Kommunikation {#texts-in-interactive-communications}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Erstellen und Bearbeiten von Textdokumentfragmenten zur Verwendung in interaktiver Kommunikation - Text ist einer der vier Arten von Dokumentfragmenten, die zum Erstellen interaktiver Kommunikation verwendet werden. Die anderen drei sind Bedingungen, Listen und Layout-Fragmente.

## Übersicht {#overview}

Ein Textdokumentfragment besteht aus einem oder mehreren Textabsätzen. Ein Absatz kann statisch oder dynamisch sein. Ein dynamischer Absatz kann Formulardatenmodelleigenschaften und -variablen enthalten. Sie können Regeln auch anwenden und innerhalb eines Textdokumentfragments wiederholen. So könnte beispielsweise der Kundenname in einer Grußformel eine Formulardatenmodell (FDM)-Eigenschaft sein, dessen Wert zur Laufzeit bereitgestellt wird. Durch Änderung dieser Werte können Sie dieselbe interaktive Kommunikation verwenden, um die interaktive Kommunikation für die verschiedenen Kunden mit der Benutzung der Benutzeroberfläche für Agenten vorzubereiten.

Das Textdokumentfragment in der interaktiven Kommunikation unterstützt den folgenden Typ dynamischer Daten:

* **Datenmodellobjekte**: Die Dateneigenschaften verwenden eine Back-End-Datenquelle.
* **Regelbasierter Inhalt**: Teile des Inhalts in einem Text, die basierend auf einer Regel angezeigt oder ausgeblendet werden. Eine Regel könnte auch auf den Eigenschaften und Variablen des Formulardatenmodells basieren.
* **Variablen**: Im Textdokumentfragment sind Variablen nicht an eine Backend-Datenquelle gebunden. Der Agent füllt/wählt Werte in Variablen oder bindet die Variablen an Datenquellen während der Vorbereitung der interaktiven Kommunikation zum Senden an einen Nachbearbeitungsprozess.
* **Wiederholen**: Sie haben eventuell dynamische Informationen in Ihrer interaktiven Kommunikation, z. B. Transaktionen in einem Kreditkartenauszug, deren Anzahl sich mit jeder generierten interaktiven Kommunikation ändern kann. Wenn Sie die Wiederholen-Funktion verwenden, können Sie solche dynamischen Daten formatieren und strukturieren. Weitere Informationen finden Sie unter [Inline-Zustand und Wiederholung](cm-inline-condition.md).

## Text erstellen {#createtext}

1. Auswählen **`[!UICONTROL Forms]`** > **[!UICONTROL Dokumentfragmente]**.
1. Auswählen **`[!UICONTROL Create]`** > **[!UICONTROL Text]**.
1. Geben Sie die folgenden Daten an:

   * **[!UICONTROL Titel]**: (Optional) Geben Sie den Titel für das Textdokumentfragment ein. Titel müssen nicht eindeutig sein und dürfen Sonderzeichen und nichtenglische Zeichen enthalten. Texte werden durch ihren Titel (falls verfügbar) wie etwa in Miniaturen und Eigenschaften referenziert.
   * **[!UICONTROL Name]**: Der eindeutige Name des Texts, in einem Ordner. Es ist nicht möglich, dass zwei Dokumentfragmente (Text, Bedingung oder Liste) mit demselben Namen vorhanden sind, ungeachtet ihres jeweiligen Status. Im Feld Name können Sie nur englische Sprachzeichen, Zahlen und Bindestriche eingeben. Das Feld Name wird automatisch auf der Grundlage des Felds Titel ausgefüllt. Die Sonderzeichen, Leerzeichen, Zahlen und die nichtenglischen Zeichen im Feld „Titel“ werden im Feld „Name“ durch Bindestriche ersetzt. Obwohl der Wert im Feld „Titel“ automatisch in das Feld „Name“ kopiert wird, können Sie den Wert bearbeiten.
   * **[!UICONTROL Beschreibung]**: Geben Sie eine Beschreibung des Textes ein.
   * **[!UICONTROL Formulardatenmodell]**: Wählen Sie optional das Optionsfeld Formulardatenmodell aus, um den Text basierend auf einem Formulardatenmodell zu erstellen. Wenn Sie das Optionsfeld &quot;Formulardatenmodell&quot;auswählen, **[!UICONTROL Formulardatenmodell*]** angezeigt. Suchen Sie nach einem Formulardatenmodell und wählen Sie es aus. Stellen Sie beim Erstellen von Text und Bedingungen für eine interaktive Kommunikation sicher, dass Sie dasselbe Datenmodell verwenden, das Sie in der interaktiven Kommunikation verwenden möchten. Weitere Informationen zum Formulardatenmodell finden Sie unter [Datenintegration](/help/forms/using/data-integration.md).
   * **[!UICONTROL Tags]**: Um optional einen benutzerdefinierten Tag zu erstellen, geben Sie einen Wert in das Textfeld ein und drücken Sie die Eingabetaste. Wenn Sie diesen Text speichern, werden die neu hinzugefügten Tags erstellt.

1. Tippen Sie auf **[!UICONTROL Weiter]**.

   Die Seite Text erstellen wird angezeigt. Wenn Sie sich dafür entschieden haben, einen auf einem Formulardatenmodell basierenden Text zu erstellen, werden die Eigenschaften des Formulardatenmodells im linken Bereich angezeigt.

1. Geben Sie den Text ein und verwenden Sie die folgenden Optionen zum Formatieren, Konditionalisieren und Einfügen von Formulardatenmodelleigenschaften und -variablen in Ihren Text:

   * [Formulardatenmodell](#formdatamodel)
   * [Variablen](#variables)
   * [Regeleditor](#rules)
   * [Formatierungsoptionen](#formatting)

      * [Formatierten Text aus anderen Anwendungen kopieren/einfügen](#paste)
      * [Teile des Textes markieren](#highlight)
   * [Wiederholen](/help/forms/using/cm-inline-condition.md)
   * [Sonderzeichen](#special)
   * [Text suchen und ersetzen](#search-features)
   * [Tastaturbefehle](/help/forms/using/keyboard-shortcuts.md)


1. Tippen Sie auf **[!UICONTROL Speichern]**.

   Der Text wird erstellt. Jetzt können Sie den Text als Baustein beim Erstellen einer interaktiven Kommunikation verwenden.

## Text bearbeiten {#edittext}

Sie können ein vorhandenes Textdokumentfragment wie folgt bearbeiten: Sie können auch ein Textdokumentfragment innerhalb eines interaktiven Kommunikationseditor bearbeiten.

1. Auswählen **`[!UICONTROL Forms]`** > **[!UICONTROL Dokumentfragmente]**.
1. Navigieren Sie zu einem Textdokumentfragment und wählen Sie es aus.
1. Tippen Sie auf **[!UICONTROL Bearbeiten]**.
1. Nehmen Sie die erforderlichen Änderungen vor. Weitere Informationen zu Optionen im Text finden Sie unter [Text erstellen](#createtext).
1. Tippen Sie auf **[!UICONTROL Speichern]** und dann auf **[!UICONTROL Schließen]**.

## Personalisieren eines Textdokumentfragments mithilfe von Formulardatenmodelleigenschaften {#formdatamodel}

Sie können Textdokumentfragmente personalisieren, indem Sie die Eigenschaften des Formulardatenmodells einfügen. Wenn Sie die Eigenschaften der Formulardaten in Text einfügen, können Sie empfängerspezifische Daten aus der Datenquelle für die Vorschau einer interaktiven Kommunikation abrufen und befüllen. Weitere Informationen zum Formulardatenmodell finden Sie unter [Datenintegration für AEM Forms](/help/forms/using/data-integration.md).

Wenn Sie beim Erstellen eines Texts ein Formulardatenmodell angegeben haben, werden die Eigenschaften im Formulardatenmodell im linken Bereich des Texteditors angezeigt. Das angegebene Formulardatenmodell sollte für das Textdokumentfragment sowie für die interaktive Kommunikation, die es enthält, identisch sein.

![insertfdmelementtext](assets/insertfdmelementtext.png)

* Um eine FDM-Eigenschaft in Text einzufügen, platzieren Sie den Cursor an die Stelle, an der Sie die Eigenschaft einfügen möchten, und wählen Sie dann die **`[A]`** Eigenschaft im linken Bereich durch Tippen darauf und tippen Sie auf **`[B]`** **[!UICONTROL Auswahl hinzufügen]**. Sie können auch einfach doppelt auf die Eigenschaft tippen, um sie an der Cursor-Position **`[C]`** einzufügen. Die Eigenschaften des Formulardatenmodells werden in einer bräunlichen Hintergrundfarbe hervorgehoben.

* So können die Agenten den Wert einer FDM-Eigenschaft in der Agenten-Benutzeroberfläche bearbeiten, während [Interaktive Kommunikation vorbereiten und senden](/help/forms/using/prepare-send-interactive-communication.md) Tippen Sie mithilfe der Benutzeroberfläche für Agenten auf die **`[D]`** Sperrsymbol für diese Eigenschaft und stellen Sie sicher, dass sie sich in einem entsperrten Status befindet. Der Standardstatus der Eigenschaft ist gesperrt und ein Agent kann die Eigenschaft in der Benutzeroberfläche für Agenten nicht bearbeiten.

Sie können auch Eigenschaften des Formulardatenmodells verwenden, um Regeln zum Anzeigen oder Ausblenden von Inhaltsbereichen zu erstellen. Weitere Informationen finden Sie unter [Regeln im Text erstellen](#rules).

## Erstellen und Verwenden von Variablen in einem Textdokumentfragment {#variables}

Variablen sind Platzhalter, die beim Erstellen einer interaktiven Kommunikation gebunden werden können. Variablen können an eine Formulardatenmodelleigenschaft oder ein Textfragment gebunden werden. Variablen können auch für den Agenten zum Ausfüllen übrig bleiben.

Sie können Variablen anstelle von Formulardatenmodelleigenschaften verwenden, wenn:

* Ein Textdokumentfragment wird in mehreren interaktiven Kommunikationen verwendet, wobei die Bindung für verschiedene interaktive Kommunikation unterschiedlich sein muss.
* Textdokumentfragmente verfügen zum Zeitpunkt ihrer Erstellung über kein Formulardatenmodell. Sie können Variablen einfügen und später zum Zeitpunkt der Erstellung der interaktiven Kommunikation an die Eigenschaften des Formulardatenmodells binden.
* Sie müssen Text aus einem Textdokumentfragment binden und abrufen. Nur diese Textdokumentfragmente können an Variablen gebunden werden, die keine Variablen enthalten dürfen.

Beim Erstellen oder Bearbeiten eines Textdokumentfragments können Sie Variablen erstellen und einfügen. Die von Ihnen erstellten Variablen werden auf der Registerkarte Daten der Benutzeroberfläche für Agenten angezeigt. Der Agent gibt die Werte für die Variablen an, während [Vorbereiten und Senden der interaktiven Kommunikation über die Benutzeroberfläche des Agenten](/help/forms/using/prepare-send-interactive-communication.md) läuft.

### Variablen erstellen {#create-variables}

1. Tippen Sie im linken Bereich auf **[!UICONTROL Variablen]**.

   Der Variablenbereich wird angezeigt.

   ![variablespanel](assets/variablespane.png)

1. Tippen Sie auf **[!UICONTROL Erstellen]**.

   Der Bereich Variablen erstellen wird angezeigt.

1. Geben Sie die folgenden Informationen ein und tippen Sie auf **[!UICONTROL Erstellen]**:

   * **[!UICONTROL Name*]**: Name der Variablen.
   * **[!UICONTROL Beschreibung]**: Geben Sie optional eine Beschreibung der Variablen ein.
   * **[!UICONTROL Typ*]**: Wählen Sie einen Variablentyp aus: Zeichenfolge, Zahl, Boolescher Wert oder Datum.
   * **[!UICONTROL Nur bestimmte Werte zulassen]**: Bei Zeichenfolge- und Zahl-Variablen können Sie sicherstellen, dass der Agent aus einem bestimmten Satz von Werten für einen Platzhalter in der Agent-UI auswählt. Um den Wertesatz anzugeben, wählen Sie diese Option aus und geben Sie dann im Feld **[!UICONTROL Werte]** durch Komma getrennte Werte an, die zulässig sind.

1. Tippen Sie auf **[!UICONTROL Erstellen]**.

   Die Variable wird erstellt und im Bereich „Variablen“ aufgelistet.

1. Um eine Variable in den Text einzufügen, platzieren Sie den Cursor an der entsprechenden Stelle, wählen Sie die Variable aus und tippen Sie auf **[!UICONTROL Ausgewählte hinzufügen]**.

   ![variableinserted](assets/variableinserted.png)

   Variablen werden in hellblauer Hintergrundfarbe hervorgehoben, während Formulardatenmodelleigenschaften in einer bräunlichen Farbe hervorgehoben werden.

1. Tippen Sie auf **[!UICONTROL Speichern]**.

## Regeln im Text erstellen {#rules}

Mit dem Regeleditor in einem Text können Sie Regeln erstellen, um Textzeichenfolgen oder Inhaltselemente, die auf **voreingestellte Bedingungen**. Diese Bedingungen können wie folgt konfiguriert werden:

* Zeichenfolgen
* Zahlen
* Mathematischer Ausdruck
* Datum
* Eigenschaften des zugehörigen Formulardatenmodells
* Alle Variablen, die Sie möglicherweise im Text erstellt haben

### Regeln im Text erstellen {#create-rules-in-text}

1. Wählen Sie beim Erstellen oder Bearbeiten eines Textes die Textzeichenfolge, den Absatz oder den Inhalt aus, die bzw. den Sie mithilfe der Regel konditionalisieren möchten.

   ![selectcontentapplyrule](assets/selectcontentapplyrule.png)

1. Tippen Sie auf **[!UICONTROL Regel erstellen]**.

   Das Dialogfeld „Regel erstellen“ wird angezeigt. Zusätzlich zu Zeichenfolge, Zahl, mathematischem Ausdruck und Datum stehen im Regeleditor auch folgende Elemente zum Erstellen von Anweisungen der Regeln zur Verfügung:

   * Eigenschaften des zugehörigen Formulardatenmodells
   * Eventuell von Ihnen erstellte Variablen

   Wählen Sie die geeignete Option aus, die ausgewertet werden soll.

   ![ruleeditor](assets/ruleeditor.png)

   ![ruleeditorfdm](assets/ruleeditorfdm.png)

   >[!NOTE]
   >
   >Die Sammlungseigenschaft wird nicht zum Erstellen von Regeln unterstützt, mit denen Text angezeigt wird und Bedingungen festgelegt werden.

1. Wählen Sie den entsprechenden Operator aus, um die Regel auszuwerten, z. B. Gleich ist, Enthält und Beginnt mit.

   ![ruleeditorfdm-1](assets/ruleeditorfdm-1.png)

1. Fügen Sie den auswertenden Ausdruck, den Wert, die Datenmodelleigenschaft oder die Variable ein.

   ![Regel, um den ausgewählten Text anzuzeigen, wenn der Standort des Empfängers gemäß den Quelldaten von FDM US ist](assets/ruleeditorfdm-1-1.png)

   Regel, um den ausgewählten Text anzuzeigen, wenn der Standort des Empfängers gemäß den Quelldaten von FDM US ist

   * Beim Erstellen oder Bearbeiten einer Regel können Sie auch auf ![icon_resize](assets/icon_resize.png) (Größe ändern) tippen, um das Dialogfeld „Regel erstellen/Regel bearbeiten“ zu erweitern. Der erweiterte Vollbildansichtsdialog ermöglicht Ihnen, Eigenschaften des Formulardatenmodells und Variablen mithilfe der Drag &amp; Drop-Funktion zu ziehen und einzufügen, um Regeln zu erstellen. Tippen Sie erneut auf „Größe ändern“, um zum Dialogfeld „Regel erstellen“ zurückzukehren.
   * Sie können auch mehrere Bedingungen in einer Regel erstellen.
   * Sie können auch überlappende Regeln erstellen, in denen eine Regel auf einen Teil eines Inhalts angewendet wird, auf den bereits eine Regel angewendet wurde.

1. Tippen Sie auf **[!UICONTROL Fertig]**.

   Die Regel wird angewendet. Der Text oder Inhalt, auf den die Regel angewendet wird, wird grün hervorgehoben. Wenn Sie den Mauszeiger über den linken Ziehpunkt der Hervorhebung bewegen, wird die angewendete Regel angezeigt.

   ![appliedruletext](assets/appliedruletext.png)

   Wenn Sie auf den linken Handler der angewendeten Regel klicken, erhalten Sie die Optionen zum Bearbeiten oder Entfernen der Regel.

## Text formatieren {#formatting}

Beim Erstellen oder Bearbeiten von Text ändert sich die Symbolleiste je nach Art der Änderungen, die Sie vornehmen: Absatz, Ausrichtung oder Auflistung:

Wählen Sie den Typ der Symbolleiste aus: Absatz, Ausrichtung oder Auflistung

![Symbolleiste zum Bearbeiten der Schriftart](do-not-localize/paragraphtoolbar-1.png)

Symbolleiste zum Bearbeiten der Schriftart

![Ausrichtungs-Symbolleiste](assets/alignmenttoolbar.png)

Ausrichtungs-Symbolleiste

![Auflistungs-Symbolleiste](do-not-localize/listingtoolbar.png)

Auflistungs-Symbolleiste

### Teile von Text hervorheben/hervorheben {#highlight}

Um Textteile in einem bearbeitbaren Dokumentfragment hervorzuheben oder hervorzuheben, wählen Sie den Text aus und tippen Sie auf Farbe hervorheben.

![textbackgroundcolorapplied-1](assets/textbackgroundcolorapplied-1.png)

Sie können entweder direkt auf eine Grundfarbe **`[A]`** in der Grundfarbenpalette tippen oder auf **Auswählen** tippen, nachdem Sie den Schieberegler **`[B]`** verwendet haben, um den entsprechenden Farbton der Farbe auszuwählen.

Optional können Sie auch auf der Registerkarte „Erweitert“ die gewünschten Werte für Farbton, Helligkeit und Sättigung **`[C]`** auswählen, um die genaue Farbe zu erstellen, und dann auf „Auswählen“ **`[D]`** tippen, um die Farbe zum Hervorheben des Textes anzuwenden.

![textbackgroundcolor-2](assets/textbackgroundcolor-2.png)

### Einfügen von formatiertem Text {#paste}

Um einen oder mehrere Textabsätze wiederzuverwenden, die in einer anderen Anwendung vorhanden sind, z. B. von Microsoft® Word- oder HTML-Seiten, kopieren Sie den Text und fügen Sie ihn in den Texteditor ein. Die Formatierung des kopierten Texts wird im Texteditor beibehalten.

Sie können einen oder mehrere Textabsätze in ein bearbeitbares Textdokumentfragment kopieren und einfügen. Sie können beispielsweise ein Microsoft® Word-Dokument mit einer Liste mit Aufzählungszeichen für zulässige Aufenthaltsnachweise wie folgt erstellen:

![pastetextmsword-2](assets/pastetextmsword-2.png)

Sie können den Text direkt aus dem Microsoft® Word-Dokument in ein bearbeitbares Textdokumentfragment kopieren und einfügen. Die Formatierung wie Liste mit Aufzählungszeichen, Schriftart und Textfarbe wird im Textdokumentfragment beibehalten.

![pastetexteditablemodule-1](assets/pastetexteditablemodule-1.png)

>[!NOTE]
>
>Die Formatierung des eingefügten Textes hat jedoch einige[ Einschränkungen](https://helpx.adobe.com/de/aem-forms/kb/cm-copy-paste-text-limitations.html).

## Sonderzeichen in Text einfügen {#special}

Fügen Sie ggf. Sonderzeichen in das Dokumentfragment ein. Beispielsweise können Sie über die Sonderzeichenpalette die folgenden Zeichen einfügen:

* Währungssymbole wie €,￥ und £
* Mathematische Symbole wie ∑, √, ∂ und ^
* Satzzeichen wie „ und “

![specialcharacters-2](assets/specialcharacters-2.png)

Texteditor enthält integrierte Unterstützung für 210 Sonderzeichen. Der Administrator kann die [Unterstützung für mehr/benutzerdefinierte Sonderzeichen durch Anpassung hinzufügen](/help/forms/using/custom-special-characters.md).

## Text suchen und ersetzen {#search-features}

Bei der Arbeit mit Textdokumentfragmenten, die eine große Menge an Text enthalten, müssen Sie nach einer bestimmten Textzeichenfolge suchen. Möglicherweise müssen Sie auch eine bestimmte Textfolge durch eine alternative Zeichenfolge ersetzen.

Mit der Funktion &quot;Suchen und Ersetzen&quot;können Sie nach einer beliebigen Textzeichenfolge in einem Textdokumentfragment suchen (und diese ersetzen). Die Funktion umfasst außerdem eine leistungsstarke Suche nach regulären Ausdrücken.

1. Öffnen Sie ein Textdokumentenfragment zur [Bearbeitung](#edittext).
1. Tippen Sie auf **[!UICONTROL Suchen und Ersetzen]**.

1. Geben Sie den zu suchenden Text in das Textfeld **[!UICONTROL Suchen]** und den neuen Text (Ersatztext) in das Textfeld **[!UICONTROL Ersetzen]** ein und tippen Sie auf **[!UICONTROL Ersetzen]**.

1. Wenn der gesuchte Text gefunden wird, wird der Text durch den Ersatztext ersetzt.

   * Wenn eine andere Instanz des Suchtextes gefunden wird, wird diese Instanz im Textdokumentfragment hervorgehoben. Wenn Sie auf **[!UICONTROL Ersetzen]** erneut wird die hervorgehobene Instanz ersetzt und der Cursor bewegt sich weiter, wenn eine dritte Instanz gefunden wird.
   * Wenn keine andere Instanz gefunden wird, wird im Dialogfeld Suchen und Ersetzen eine Meldung angezeigt: Ende des Moduls erreicht.

   Sie können auch auf Alle ersetzen tippen, um alle Übereinstimmungen in einem Schritt zu ersetzen.

   Die Funktion umfasst außerdem eine leistungsstarke Suche nach regulären Ausdrücken. Um Regex in Ihrer Suche zu verwenden, wählen Sie **[!UICONTROL Regex]** und tippen dann auf **[!UICONTROL Suchen]** oder **[!UICONTROL Ersetzen]**.
