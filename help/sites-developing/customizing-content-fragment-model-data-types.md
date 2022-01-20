---
title: NICHT VERÖFFENTLICHEN, ABER KEIN DELETE ZUM Anpassen von Datentypen für Inhaltsfragmentmodelle
seo-title: Customizing Data Types for Content Fragment Models
description: In Inhaltsfragmentmodellen verwendete Datentypen können angepasst werden.
seo-description: Data types used in Content Fragment Models can be customized.
page-status-flag: de-activated
uuid: d8215dbf-2dbe-43cb-a5c1-dc1cb412a204
contentOwner: aheimoz
discoiquuid: a8b8155c-852c-4d16-b59b-7e19527c2bd4
noindex: true
source-git-commit: 3bdff366a0d455b405c1f9de371ced98d25ae2e2
workflow-type: tm+mt
source-wordcount: '1625'
ht-degree: 2%

---


# NICHT VERÖFFENTLICHEN, ABER KEIN DELETE ZUM Anpassen von Datentypen für Inhaltsfragmentmodelle{#do-not-publish-but-do-not-delete-customizing-data-types-for-content-fragment-models}

[Inhaltsfragmente](/help/assets/content-fragments.md) basieren auf [Inhaltsfragmentmodelle](/help/assets/content-fragments-models.md). Diese Modelle werden aus [elements](/help/assets/content-fragments.md#constituent-parts-of-a-content-fragment) von verschiedenen Datentypen.

Standardmäßig sind verschiedene Datentypen verfügbar, darunter einzeiliger Text, mehrzeiliger Rich-Text, numerische Felder, boolesche Selektoren, Dropdown-Menüoptionen, Datum und Uhrzeit und andere. AEM Benutzer können Datentypen basierend auf der redaktionellen Absicht der entsprechenden Fragmente auswählen. Auf diese Weise können Sie einfache Textmodelle bis hin zu komplexen Modellen mit verschiedenen Arten von Inhalten und dem zugehörigen Authoring-Erlebnis für Fragmente bearbeiten.

Datentypen werden durch eine [Kombination von Knoteneigenschaften](#properties) in [spezifische Speicherorte im Repository](#locations-in-the-repository). Sie können auch Ihre eigenen [Datentypen](#creating-your-data-type) und [fieldProperties](#creating-your-own-fieldproperties-property).

<!-- Please uncomment when files are used>
>[!NOTE]
>
>See also [Customizing Content Fragment Models](/help/sites-developing/customizing-content-fragment-models.md).
-->

## Speicherorte im Repository {#locations-in-the-repository}

Alle nativen Datentypen werden unter folgender Adresse deklariert:

`/libs/settings`

Sie können neue Datentypen hinzufügen, indem Sie die Knotenstruktur wie folgt überschreiben: `/apps`:

`/apps/settings/dam/cfm/models/formbuilderconfig/datatypes/items`

>[!CAUTION]
>
>Sie dürfen keinerlei Änderungen im Pfad `/libs` vornehmen.
>
>Alles, was dort vorhanden ist, kann sich beim nächsten Upgrade oder bei der Installation eines Service oder Fix Packs ändern.

## Eigenschaften {#properties}

Knoteneigenschaften werden verwendet, um die Datentypen zu definieren:

* [Datentypeigenschaften](#data-type-properties)
* und [fieldProperties](#fieldproperties)

### Datentypeigenschaften {#data-type-properties}

Alle Datentypen werden in einer Knotenstruktur wie folgt dargestellt:

`/libs/settings/dam/cfm/models/formbuilderconfig/datatypes/items`

Jeder Knoten unter `/items` verfügt über Eigenschaften, die definieren, wie dieser Datentyp im Modell-Editor dargestellt werden soll.

Alle folgenden Eigenschaften müssen vorhanden sein, damit der Datentyp im Modell-Editor vorhanden ist:

* `fieldIcon`

   [CoralUI-Symbol](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/coral-ui/coralui3/Coral.Icon.html#availableicons) , um den Datentyp in der Benutzeroberfläche des Modell-Editors darzustellen.

* ` [fieldProperties](#fieldproperties)`

   Ein Array, das die Konfigurationseigenschaften für jeden Datentyp darstellt.

* `fieldResourceType`

   Der Sling-Ressourcentyp, der zum Rendern des Datentyps in einem Inhaltsfragment verwendet wird. Bei Datentypen, die auf unterschiedliche Weise gerendert werden können (z. B. als einfache Texteingabe und/oder mehrzeilige Texteingabe), muss diese Eigenschaft als Array erstellt werden, das alle Ressourcentypen enthält. Die `renderasfield` -Eigenschaft wird automatisch zu `fieldProperties` , damit der Benutzer den Ressourcentyp auswählen kann, den er zum Modell hinzufügen muss,

* `fieldPropResourceType`

   Der Sling-Ressourcentyp, der zum Rendern der Standardeigenschaft für den Datentyp verwendet wird.

   Für den Datentyp beispielsweise:

   * Einzelzeilentext, die `fieldPropResourceType` wäre ein `textfield` component
   * Boolesch, die `fieldPropResourceType` wäre ein `checkbox` component

* `fieldViewResourceType`

   Der Sling-Ressourcentyp, der beim Erstellen des Modells zum Rendern des Datentyps in der Vorschau verwendet wird. Wenn der Benutzer den Datentyp auf die linke Seite des Modell-Editors zieht, wird der `fieldViewResourceType` -Eigenschaft stellt die Komponente dar, die dort gerendert wird. Dies wird für Fälle verwendet, in denen Sie nicht die vollständige Komponente rendern möchten, sondern nur einen Ersatz rendern möchten, der den Mehraufwand für den Modell-Editor minimiert.

* `fieldTitle`

   Eigenschaft, die den Titel dieses Datentyps definiert. Beispiel: **Einzelzeilentext** für `textfield` Komponente, **Mehrzeiliger Text** für eine Komponente mit mehreren Feldern.

* `valueType`

   Dies ist der Typ des Werts, den der Datentyp zurückgibt, wenn er intern gespeichert wird. Siehe [Zuordnungen](#mappings).

* `renderType`

   Dies ist eine interne Darstellung des Datentyps. Es verbindet die `valueType` zu einer UI-Komponente. Siehe [Zuordnungen](#mappings).

* `listOrder`

   Jeder Datentyp benötigt einen Wert, der seine Reihenfolge in der Liste darstellt. Dies wird verwendet, um beim Speichern des Modell-Editors die richtige Reihenfolge der verschiedenen Felder sicherzustellen (durch Drag &amp; Drop hinzugefügt/verschoben). Dieser Wert muss eine Ganzzahl sein. Es wird empfohlen, die Zahl aufsteigend und geordnet zuzuweisen. Beim Erstellen eines neuen Datentyps ist es am besten, den Wert auf Grundlage des letzten Datentyps in der Liste zuzuweisen (der höchste Wert von `listOrder` -Wert, der in den Datentypen vorhanden ist).

#### Zuweisungen {#mappings}

<table> 
 <tbody> 
  <tr> 
   <td>Datentyp<br /> </td> 
   <td>Werttyp<br /> </td> 
   <td>Render Type (Rendertyp)</td> 
  </tr> 
  <tr> 
   <td>Einzeilentext</td> 
   <td>String (Zeichenfolge)</td> 
   <td>text-single</td> 
  </tr> 
  <tr> 
   <td>Mehrzeilentext</td> 
   <td>Zeichenfolge mit Content-Typ<br /> </td> 
   <td>text-multi</td> 
  </tr> 
  <tr> 
   <td>Zahl (Integer/lang)<br /> </td> 
   <td>long</td> 
   <td>Number (Zahl)</td> 
  </tr> 
  <tr> 
   <td>Zahl (double/float)</td> 
   <td>double</td> 
   <td>Number (Zahl)</td> 
  </tr> 
  <tr> 
   <td>Boolesch</td> 
   <td>Boolean (Boolesch)</td> 
   <td>Boolean (Boolesch)</td> 
  </tr> 
  <tr> 
   <td>Datum und Uhrzeit</td> 
   <td>calendar</td> 
   <td>Zeit </td> 
  </tr> 
  <tr> 
   <td>Aufzählung</td> 
   <td>string/long</td> 
   <td>enumeration</td> 
  </tr> 
  <tr> 
   <td>Tags</td> 
   <td>String (Zeichenfolge)</td> 
   <td>tags</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Einige Typen (z. B. `string`, `long`, können mehrere Werte aufweisen. In diesem Fall wird die für die Wiedergabe und Bearbeitung verwendete Komponente normalerweise von einer Multifield-Komponente umschlossen ( `granite/ui/components/coral/foundation/form/multifield`). Die Ausnahme sind Tags, bei denen die Bearbeitungskomponente für die korrekte Wiedergabe verantwortlich ist.

### fieldProperties {#fieldproperties}

Die Konfigurationseigenschaften für jeden Datentyp. Werte für `fieldProperties`:

* `base`

   Dies ist die Grundlage für alle `fieldProperties` Komponenten. Die Definition befindet sich unter `/libs/dam/cfm/models/editor/components/datatypeproperties/base`.

   Sie enthält die Variable `fieldRoot`, der folgenden `fieldProperties` kann beim Erstellen von Eingaben verwenden, um den richtigen Pfad abzurufen.

   Beispiel: , um den richtigen Pfad für eine **Feldbezeichnung** Wenn Sie den Schlüssel benötigen, um die Komponente zu identifizieren, zu der diese gehört, sollte die Eingabe für dieses Feld `fieldRoot` + `<*fieldLabel*>`

* `checkboxfields`

   Diese Komponente fügt das standardmäßige Kontrollkästchen für die `Boolean` Datentyp sowie die Sling-Parameter `checked@Delete` und `checked@TypeHint`.

* `datepickerfields`

   Komponente, die die ausgeblendeten Eingaben hinzufügt, die für die Funktion der Datumsauswahl-Komponente erforderlich sind. Einschließlich der Erstellung der Eigenschaften `defaultDateField`, `displayedFormat`, `emptyText`, `valueFormat`, `minDate` und `maxDate`.

* `datetimepickerfields`

   Dadurch wird ein Auswahlfeld für `Date&Time` Datentyp zur Unterscheidung zwischen `Date` und `Date&Time` Optionen.

* `datevaluefield`

   Dadurch wird den Eigenschaften eine Datumsauswahl hinzugefügt, sodass ein Benutzer eine Standardeinstellung für die `Date&Time` Datentyp.

* `descriptionfield`

   Diese Komponente fügt ein mehrzeiliges Textfeld hinzu, das die Beschreibung der aktuell ausgewählten Komponente im mehrzeiligen Editor darstellt. Sie wird automatisch vom Modell-Editor-Renderer am Ende jeder Datentypeigenschaft hinzugefügt.

* `labelfield`

   Komponente, die eine `textfield` -Eingabe, die die Feldbeschriftung für einen Datentyp hinzufügt, der Feldbeschriftungen enthalten kann.

* `maptopropertyfield`

   Diese Komponente fügt die `Name` -Feld in den Eigenschaften, das der ausgewählten Komponente eines Datentyps eine Kennung angibt. Sie sollte in allen Datentypen vorhanden sein.

* `maxlengthfield`

   Sie wird verwendet, um die `maxLength` -Eigenschaft für die Verwendung mit Datentypen, die diese Eigenschaft akzeptieren. Beispiel: mit **Einzelzeilentext**, **Zahl**, usw.

* `multieditorfield`

   Dadurch wird das gesamte ausgeblendete Feld hinzugefügt, das erforderlich ist, damit der mehrzeilige Editor funktioniert, der durch die **Mehrzeiliger Text** Datentyp.

* `mvfields`

   Komponente, die alle ausgeblendeten Felder hinzufügt, die für die Funktionsweise einer Multifield-Komponente erforderlich sind. Beispielsweise für die zweite Option eines **Einzelzeilentext** Datentyp. Dies sollte für jede Komponente hinzugefügt werden, die als Multifeld gerendert wird.

* `numbertypefield`

   Wählen Sie die Option für **Zahl** Datentyp, der zwischen **Ganzzahl** oder **Fragment** für **Zahl** Datentyp.

* `numbervaluefield`

   A `numberfield` Standardwertauswahl für **Zahl** `type.options` Dadurch werden die Optionseingaben für die **Auflistung** Datentyp, mit dem die Werte für die Komponente &quot;Auswahlfeld&quot;bestimmt werden.

* `placeholderfield`

   Dies ist ein Textfeld, das als Eingabe für die `emptyText` -Eigenschaft einer Komponente. Dies sollte von allen Datentypen verwendet werden, die einen Platzhalter akzeptieren (was nicht sehr kompliziert ist). z. B. **Einzelzeilentext**, **Zahl** usw.).

* `renderasfield`

   Dies ist die Komponente, die automatisch gerendert wird, wenn mehrere `fieldResourceTypes` sind in der Eigenschaft des Datentypknotens vorhanden.

* `requiredfield`

   Dies ist ein Kontrollkästchen, das die `required` -Eigenschaft für eine Komponente. Da die meisten Komponenten die `required` festgelegt ist, kann dieses Feld für die meisten Datentypen verwendet werden.

* `tagsfields`

   Komponenten, die die für eine `tagfield` Komponente, die gerendert werden soll, verwendet von der **Tags** Datentyp.

* `tagsroot`

   Eine von der **Tags** Datentyp zum Festlegen des Stammpfads für `tagsfield` -Komponente.

* `textfield`

   Wird von der `Boolean` Datentyp , um die Feldbezeichnung des durch diesen Datentyp definierten Kontrollkästchens festzulegen.

* `textvaluefield`

   Die Eigenschaft Standardwert für **Einzelzeilentext** Datentyp.

## Erstellen des Datentyps {#creating-your-data-type}

Um einen eigenen Datentyp zu erstellen, gehen Sie folgendermaßen vor:

* [Erstellen der Knotenstruktur](#creating-the-node-structure)
* [Definieren der Eigenschaften für Ihren Datentyp](#defining-the-properties-for-your-data-type)

Sie können dann [Datentyp verwenden](#using-your-data-type).

Sie können auch [Erstellen eigener `fieldProperties`](#creating-your-own-fieldproperties-property).

### Erstellen der Knotenstruktur {#creating-the-node-structure}

Die Knotenstruktur muss unter `/apps` um die Datentypen zu überlagern. Wenn sie noch nicht vorhanden ist, müssen Sie Folgendes erstellen:

1. Wenn sie noch nicht vorhanden ist, müssen Sie Folgendes erstellen:

   ```
   + apps 
     + settings
       + dam 
         + cfm (cq:Page) 
           + models (nt:folder)
             + formbuilderconfig (sling:folder)
               + datatypes (nt:unstructured)
                 + items (nt:unstructured)
   ```

   >[!NOTE]
   >
   >`/apps/settings/dam` bereits existieren.
   >
   >`/cfm/models/formbuilderconfig/datatypes/items` möglicherweise mit den angegebenen Knotentypen erstellt werden.

1. under `/items` Sie können neue Knoten hinzufügen, die Ihre neuen Datentypen repräsentieren:

   * Knotentyp: `nt:unstructured`
   * &quot;Eigenschaften: see [Definieren der Eigenschaften für Ihren Datentyp](#defining-the-properties-for-your-data-type)

### Definieren der Eigenschaften für Ihren Datentyp {#defining-the-properties-for-your-data-type}

1. Werte für Folgendes bestimmen [Datentypeigenschaften](#data-type-properties) die für Ihren Datentyp erforderlich sind:

   * `fieldResourceType`
   * `fieldPropResourceType`
   * `fieldViewResourceType`

   Diese definieren, wie die Komponenten für Ihren Datentyp gerendert werden. Sie können jede beliebige Komponente sein. einschließlich Ihrer eigenen benutzerdefinierten Komponenten (benötigen Sie einen entsprechenden Satz von ` [fieldProperties](#fieldproperties)`).

   Definieren Sie diese Eigenschaften mit den entsprechenden Werten auf dem Knoten für Ihren Datentyp.

1. Bestimmen Sie die ` [fieldProperties](#fieldproperties)` verwendet werden. Dies hängt von den Attributen oder Eigenschaften ab, die Ihre `fieldResourceType` benötigt.

   Beispiel: eine `granite/ui/components/coral/foundation/form/textfield`sollte **Beschriftungsname**, **Maximale Länge**, **Platzhaltertext** und **Standardwert** -Eigenschaft.

   Sie können aus den vordefinierten [fieldProperties](#fieldproperties)oder [eigene Eigenschaften erstellen](#creating-your-own-fieldproperties-property).

   Definieren Sie diese Eigenschaften mit den entsprechenden Werten auf dem Knoten für Ihren Datentyp.

1. Werte für Folgendes bestimmen [Datentypeigenschaften](#data-type-properties):

   * `fieldIcon`
   * `fieldTitle`
   * `renderType`
   * `valueType`
   * `listOrder`

   Definieren Sie diese Eigenschaften mit den entsprechenden Werten auf dem Knoten für Ihren Datentyp.

### Verwenden des Datentyps {#using-your-data-type}

Nachdem Sie diese Knotenstruktur mit allen angewendeten Eigenschaften gespeichert haben, können Sie jedes Modell mit dem Modell-Editor öffnen und Ihren neuen Datentyp anzeigen und verwenden.

## Erstellen einer eigenen fieldProperties-Eigenschaft {#creating-your-own-fieldproperties-property}

Sie können aus den vordefinierten [fieldProperties](#fieldproperties)oder erstellen Sie Ihre eigene:

1. Erstellen Sie eine Komponente unter:

   `/apps/dam/cfm/models/editor/components/datatypeproperties/`

   Wenn der Pfad nicht vorhanden ist, können Sie ihn mit `nt:folder` Knoten.

   1. Um Zugriff auf die Variablen zu erhalten, sollte diese Komponente Folgendes erweitern:

      `/libs/dam/cfm/models/editor/components/datatypeproperties/base`* *

   1. Die Komponente sollte wie folgt eingeschlossen werden können:

      `sling:include`

   1. Diese Komponente sollte entweder ein Feld (wenn ein Benutzer Daten einführen muss) oder eine ausgeblendete Eingabe mit den Eigenschaften rendern, die für Ihren Datentyp erforderlich sind. Beispielsweise erfordert eine Multifield-Komponente einen untergeordneten Knoten mit dem Feldtyp, den sie duplizieren soll. Daher sollte es eine Eingabe geben, die (durch Sling-POST-Mechanismus) einen untergeordneten Knoten eines bestimmten Typs erstellen kann.

1. Der Basisname dieser Komponente sollte zu `fieldProperties`.
1. Wiederholen Sie diesen Vorgang für alle benötigten Eigenschaften.

