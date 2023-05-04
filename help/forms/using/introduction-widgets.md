---
title: Framework des Erscheinungsbilds für adaptive und HTML5-Formulare
seo-title: Appearance framework for adaptive and HTML5 forms
description: Mobile Forms rendert Formularvorlagen als HTML5-Formulare. Diese Formulare verwenden die Dateien "jQuery", "Backbone.js"und "Underscore.js", um das Erscheinungsbild zu verbessern und Skripterstellung zu aktivieren.
seo-description: Mobile Forms render Form Templates as HTML5 forms. These forms use jQuery, Backbone.js and Underscore.js files for the appearance and to enable scripting.
uuid: 183b8d71-44fc-47bf-8cb2-1cf920ffd23a
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: customization
discoiquuid: 3c2a44a7-24e7-49ee-bf18-eab0e44efa42
exl-id: 272d3ec1-7f92-4f4a-9e98-954136b20b27
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1206'
ht-degree: 34%

---

# Framework des Erscheinungsbilds für adaptive und HTML5-Formulare {#appearance-framework-for-adaptive-and-html-forms}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Formulare (adaptive Formulare und HTML5-Formulare) verwenden [jQuery](https://jquery.com/)-, [Backbone.js](https://backbonejs.org/)- und [Underscore.js](https://underscorejs.org/)-Bibliotheken für das Erscheinungsbild und die Skripterstellung. Die Formulare verwenden auch die Architektur von [jQuery UI](https://jqueryui.com/)-**Widgets** für alle interaktiven Elemente (beispielsweise Felder und Schaltflächen) im Formular. Diese Architektur ermöglicht es dem Formularentwickler, einen umfangreichen Satz verfügbarer jQuery-Widgets und -Plug-ins in Forms zu verwenden. Sie können ebenfalls formularspezifische Logik beim Erfassen von Benutzerdaten implementieren, wie etwa „leadDigits/trailDigits“-Einschränkungen, oder Bildklassen implementieren. Formularentwickler können benutzerdefinierte Erscheinungsbilder erstellen und verwenden, um die Datenerfassung zu verbessern und sie benutzerfreundlicher zu gestalten.

Dieser Artikel richtet sich an Entwickler mit ausreichenden Kenntnissen von jQuery- und jQuery-Widgets. Es bietet Einblicke in das Erscheinungsbild-Framework und ermöglicht es Entwicklern, ein alternatives Erscheinungsbild für ein Formularfeld zu erstellen.

Das Erscheinungsbild-Framework nutzt verschiedene Optionen, Ereignisse (Trigger) und Funktionen zum Erfassen von Benutzerinteraktionen mit dem Formular und reagiert auf Modelländerungen, um den Endbenutzer zu informieren. Zusätzlich gilt Folgendes:

* Das Framework bietet eine Reihe von Optionen für das Erscheinungsbild eines Felds. Diese Optionen sind Schlüssel-Wert-Paare und in zwei Kategorien unterteilt: allgemeine Optionen und feldtypspezifische Optionen.
* Das Erscheinungsbild Trigger als Teil des Vertrags eine Reihe von Ereignissen wie &quot;enter&quot;und &quot;exit&quot;.
* Das Erscheinungsbild ist erforderlich, um eine Reihe von Funktionen zu implementieren. Einige Funktionen sind häufig, während andere für Feldfunktionen spezifisch sind.

## Allgemeine Optionen {#common-options}

Im Folgenden finden Sie die globalen Optionen. Diese Optionen stehen für jedes Feld zur Verfügung.

<table> 
 <tbody>
  <tr>
   <th>Eigenschaft </th> 
   <th>Beschreibung</th> 
  </tr>
  <tr>
   <td>name</td> 
   <td>Ein Bezeichner, mit dem dieses Objekt oder Ereignis in Skriptausdrücken angegeben wird. Diese Eigenschaft gibt beispielsweise den Namen der Host-Anwendung an.</td> 
  </tr>
  <tr>
   <td>value</td> 
   <td>Tatsächlicher Wert des Felds. </td> 
  </tr>
  <tr>
   <td>displayValue</td> 
   <td>Der Wert des Felds wird angezeigt. </td> 
  </tr>
  <tr>
   <td>screenReaderText</td> 
   <td>Reader des Bildschirms verwenden diesen Wert, um Informationen über das Feld zu beschreiben. Das Formular gibt den Wert an. Sie können diesen Wert überschreiben.<br /> </td> 
  </tr>
  <tr>
   <td>tabIndex</td> 
   <td>Die Position des Felds in der Tab-Abfolge des Formulars. Überschreiben Sie den tabIndex nur, wenn Sie die Standardreihenfolge der Registerkarten im Formular ändern möchten.</td> 
  </tr>
  <tr>
   <td>role</td> 
   <td>Rolle des Elements, z. B. Überschrift oder Tabelle.</td> 
  </tr>
  <tr>
   <td>Höhe</td> 
   <td>Die Höhe des Widgets. Sie wird in Pixel angegeben. </td> 
  </tr>
  <tr>
   <td>width</td> 
   <td>Die Breite des Widgets. Sie wird in Pixel angegeben.</td> 
  </tr>
  <tr>
   <td>access</td> 
   <td>Steuerelemente für den Zugriff auf den Inhalt eines Containers, z. B. eines Teilformulars.</td> 
  </tr>
  <tr>
   <td>paraStyles</td> 
   <td>Die para -Eigenschaft eines XFA-Elements für das Widget.</td> 
  </tr>
  <tr>
   <td>dir</td> 
   <td>Die Richtung des Textes. Mögliche Werte sind "ltr"(von links nach rechts) und "rtl"(von rechts nach links).</td> 
  </tr>
 </tbody>
</table>

Zusätzlich zu diesen Optionen stellt das Framework einige andere Optionen bereit, die je nach Typ des Felds variieren. Die Details zu den feldspezifischen Optionen sind unten aufgeführt.

### Interaktion mit Formularframework {#interaction-with-forms-framework}

Um mit dem Formularframework zu interagieren, löst ein Widget einige Ereignisse aus, die das Formularskript aktivieren. Wenn das Widget diese Ereignisse nicht ausgibt, funktionieren einige Skripte nicht, die im Formular für dieses Feld geschrieben wurden.

#### Vom Widget ausgelöste Ereignisse {#events-triggered-by-widget}

<table> 
 <tbody>
  <tr>
   <th>Ereignis </th> 
   <th>Beschreibung</th> 
  </tr>
  <tr>
   <td>XFA_ENTER_EVENT</td> 
   <td>Das Ereignis wird ausgelöst, wenn das Feld im Fokus ist. Dadurch kann das Skript "enter"auf dem Feld ausgeführt werden. Die Syntax zum Auslösen des Ereignisses lautet<br /> (Widget)._trigger(xfalib.ut.XfaUtil.prototype.XFA_ENTER_EVENT)<br /> </td> 
  </tr>
  <tr>
   <td>XFA_EXIT_EVENT</td> 
   <td>Dieses Ereignis wird ausgelöst, wenn der Benutzer das Feld verlässt. Dadurch kann die Engine den Wert des Felds festlegen und ihr "exit"-Skript ausführen. Die Syntax zum Auslösen des Ereignisses lautet<br /> (Widget)._trigger(xfalib.ut.XfaUtil.prototype.XFA_EXIT_EVENT)<br /> </td> 
  </tr>
  <tr>
   <td>XFA_CHANGE_EVENT</td> 
   <td>Dieses Ereignis wird ausgelöst, damit die Engine das "change"-Skript ausführen kann, das in das Feld geschrieben wurde. Die Syntax zum Auslösen des Ereignisses lautet<br /> (Widget)._trigger(xfalib.ut.XfaUtil.prototype.XFA_CHANGE_EVENT)<br /> </td> 
  </tr>
  <tr>
   <td>XFA_CLICK_EVENT</td> 
   <td>Das Ereignis wird ausgelöst, wenn das Feld angeklickt wird. Dadurch kann die Engine das "click"-Skript ausführen, das in das Feld geschrieben wurde. Die Syntax zum Auslösen des Ereignisses lautet<br /> (Widget)._trigger(xfalib.ut.XfaUtil.prototype.XFA_CLICK_EVENT)<br /> </td> 
  </tr>
 </tbody>
</table>

#### Vom Widget implementierte APIs {#apis-implemented-by-widget}

Die Erscheinungsbild-Framework ruft einige Funktionen des Widgets auf, die in den benutzerdefinierten Widgets implementiert sind. Das Widget muss die folgenden Funktionen implementieren:

<table> 
 <tbody>
  <tr>
   <th>Funktion</th> 
   <th>Beschreibung</th> 
  </tr>
  <tr>
   <td>focus: function()</td> 
   <td>Fokus wird auf das Feld gelegt.</td> 
  </tr>
  <tr>
   <td>click: function()</td> 
   <td>Setzt den Fokus auf das Feld und ruft XFA_CLICK_EVENT auf.</td> 
  </tr>
  <tr>
   <td><p>markError:function(errorMessage, errorType)<br /> <br /> <em>errorMessage: string </em>steht für den Fehler<br /> <em>errorType: string (“warning”/”error”)</em></p> <p><strong>Hinweis</strong>: Gilt nur für HTML5-Formulare.</p> </td> 
   <td>Sendet Fehlermeldung und Fehlertyp an das Widget. Das Widget zeigt den Fehler an.</td> 
  </tr>
  <tr>
   <td><p>clearError: function()</p> <p><strong>Hinweis</strong>: Gilt nur für HTML5-Formulare.</p> </td> 
   <td>Wird aufgerufen, wenn die Fehler im Feld behoben sind. Das Widget blendet den Fehler aus.</td> 
  </tr>
 </tbody>
</table>

## Optionen je nach Feldtyp {#options-specific-to-type-of-field}

Alle benutzerdefinierten Widgets sollten mit den oben genannten Spezifikationen übereinstimmen. Um die Funktionen von verschiedenen Feldern zu nutzen, muss das Widget den Richtlinien des jeweiligen Felds entsprechen.

### TextEdit: Textfeld {#textedit-text-field}

<table> 
 <tbody>
  <tr>
   <th>Option</th> 
   <th>Beschreibung</th> 
  </tr>
  <tr>
   <td>multiline</td> 
   <td>True , wenn das Feld die Eingabe eines Zeilenumbruchzeichens unterstützt, andernfalls false.</td> 
  </tr>
  <tr>
   <td>maxChars</td> 
   <td>Maximale Zeichenanzahl, die in das Feld eingegeben werden kann.</td> 
  </tr>
  <tr>
   <td><p>limitLengthToVisibleArea</p> <p><strong>Hinweis</strong>: Gilt nur für HTML5-Formulare</p> </td> 
   <td>Gibt das Verhalten des Textfelds an, wenn die Textbreite die Breite des Widgets überschreitet.</td> 
  </tr>
 </tbody>
</table>

### ChoiceList: DropDownList, ListBox {#choicelist-dropdownlist-listbox}

<table> 
 <tbody>
  <tr>
   <th>Option</th> 
   <th>Beschreibung</th> 
  </tr>
  <tr>
   <td>Wert<br /> </td> 
   <td>Array der ausgewählten Werte.<br /> </td> 
  </tr>
  <tr>
   <td>Elemente<br /> </td> 
   <td>Array von Objekten, die als Optionen angezeigt werden sollen. Jedes Objekt enthält zwei Eigenschaften:<br /> save: Wert zum Speichern, anzeigen: anzuzeigenden Wert.<br /> <br /> </td> 
  </tr>
  <tr>
   <td><p>standardmäßig als bearbeitbar</p> <p><strong>Hinweis</strong>: Gilt nur für HTML5-Formulare.<br /> </p> </td> 
   <td>Wenn der Wert "true"ist, wird der benutzerdefinierte Texteintrag im Widget aktiviert.<br /> </td> 
  </tr>
  <tr>
   <td>displayValue<br /> </td> 
   <td>Array von anzuzeigenden Werten.<br /> </td> 
  </tr>
  <tr>
   <td>multiselect<br /> </td> 
   <td>"True", wenn mehrere Auswahlen zulässig sind, andernfalls "false".<br /> </td> 
  </tr>
 </tbody>
</table>

#### API {#api}

<table> 
 <tbody>
  <tr>
   <th>Funktion</th> 
   <th>Beschreibung</th> 
  </tr>
  <tr>
   <td><p>addItem:<em> function(itemValues)<br /> itemValues: Objekt, das den Wert "display"und "save"enthält <br /> {sDisplayVal: &lt;displayvalue&gt;, sSaveVal: &lt;save value=""&gt;}</em></p> </td> 
   <td>Fügt der Liste ein Element hinzu.</td> 
  </tr>
  <tr>
   <td>deleteItem<em>: function(nIndex)<br /> nIndex: Index des Elements, das aus der Liste entfernt werden soll<br /> </em><br /> <br /> </td> 
   <td>Löscht eine Option aus der Liste.</td> 
  </tr>
  <tr>
   <td>clearItems:<code> function()</code></td> 
   <td>Löscht alle Optionen aus der Liste.</td> 
  </tr>
 </tbody>
</table>

### NumericEdit: NumericField, DecimalField {#numericedit-numericfield-decimalfield}

| Optionen | Beschreibung |
|---|---|
| dataType | Zeichenfolge, die den Datentyp des Felds darstellt (Ganzzahl/Dezimalzahl). |
| leadDigits | Maximale führende Stellen in der Dezimalzahl. |
| fracDigits | Maximale Bruchzahlen in der Dezimalzahl. |
| zero | Zeichenfolgendarstellung von null im Gebietsschema des Felds. |
| decimal | Zeichenfolgendarstellung der Dezimalzahl im Gebietsschema des Felds. |

### CheckButton: RadioButton, CheckBox {#checkbutton-radiobutton-checkbox}

<table> 
 <tbody>
  <tr>
   <th>Optionen</th> 
   <th>Beschreibung</th> 
  </tr>
  <tr>
   <td>values</td> 
   <td><p>Array von Werten (ein/aus/neutral).</p> <p>Es handelt sich um ein Array von Werten für die verschiedenen Status von checkButton. values[0] ist der Wert, wenn der Status EIN ist, value[1] der Wert, wenn der Status AUS ist;<br /> value[2] ist der Wert, wenn der Status NEUTRAL ist. Die Länge des Werte-Arrays entspricht dem Wert der Statusoption.<br /> </p> </td> 
  </tr>
  <tr>
   <td>states</td> 
   <td><p>Anzahl der zulässigen Status. </p> <p>Zwei für adaptive Formulare (Ein, Aus) und drei für HTML5-Formulare (Ein, Aus, Neutral).</p> </td> 
  </tr>
  <tr>
   <td>state</td> 
   <td><p>Aktueller Status des Elements.</p> <p>Zwei für adaptive Formulare (Ein, Aus) und drei für HTML5-Formulare (Ein, Aus, Neutral).</p> </td> 
  </tr>
 </tbody>
</table>

### DateTimeEdit: (DateField) {#datetimeedit-datefield}

| Option | Beschreibung |
|---|---|
| Tage | Lokalisierte Tagesnamen für dieses Feld. |
| Monate | Lokalisierte Monatsnamen für dieses Feld. |
| zero | Der lokalisierte Text für die Zahl 0. |
| clearText | Der lokalisierte Text für die Schaltfläche &quot;Löschen&quot;. |
