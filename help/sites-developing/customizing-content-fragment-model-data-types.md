---
title: NICHT VERÖFFENTLICHEN, ABER KEIN DELETE ZUM Anpassen von Datentypen für Inhaltsfragmentmodelle
seo-title: Anpassen von Datentypen für Inhaltsfragmentmodelle
description: In Inhaltsfragmentmodellen verwendete Datentypen können angepasst werden.
seo-description: In Inhaltsfragmentmodellen verwendete Datentypen können angepasst werden.
page-status-flag: de-activated
uuid: d8215dbf-2dbe-43cb-a5c1-dc1cb412a204
contentOwner: aheimoz
discoiquuid: a8b8155c-852c-4d16-b59b-7e19527c2bd4
noindex: true
source-git-commit: 3bdff366a0d455b405c1f9de371ced98d25ae2e2
workflow-type: tm+mt
source-wordcount: '1642'
ht-degree: 2%

---


# NICHT VERÖFFENTLICHEN, ABER KEIN DELETE ZUM Anpassen von Datentypen für Inhaltsfragmentmodelle{#do-not-publish-but-do-not-delete-customizing-data-types-for-content-fragment-models}

[Inhaltsfragmente ](/help/assets/content-fragments.md) basieren auf  [Inhaltsfragmentmodellen](/help/assets/content-fragments-models.md). Diese Modelle werden aus [Elementen](/help/assets/content-fragments.md#constituent-parts-of-a-content-fragment) verschiedener Datentypen erstellt.

Standardmäßig sind verschiedene Datentypen verfügbar, darunter einzeiliger Text, mehrzeiliger Rich-Text, numerische Felder, boolesche Selektoren, Dropdown-Menüoptionen, Datum und Uhrzeit und andere. AEM Benutzer können Datentypen basierend auf der redaktionellen Absicht der entsprechenden Fragmente auswählen. Auf diese Weise können Sie einfache Textmodelle bis hin zu komplexen Modellen mit verschiedenen Arten von Inhalten und dem zugehörigen Authoring-Erlebnis für Fragmente bearbeiten.

Datentypen werden durch eine [Kombination von Knoteneigenschaften](#properties) definiert, die sich an [bestimmten Stellen im Repository](#locations-in-the-repository) befinden. Sie können auch eigene [Datentypen](#creating-your-data-type) und [fieldProperties](#creating-your-own-fieldproperties-property) erstellen.

<!-- Please uncomment when files are used>
>[!NOTE]
>
>See also [Customizing Content Fragment Models](/help/sites-developing/customizing-content-fragment-models.md).
-->

## Speicherorte im Repository {#locations-in-the-repository}

Alle nativen Datentypen werden unter folgender Adresse deklariert:

`/libs/settings`

Sie können neue Datentypen hinzufügen, indem Sie die Knotenstruktur wie folgt unter `/apps` überlagern:

`/apps/settings/dam/cfm/models/formbuilderconfig/datatypes/items`

>[!CAUTION]
>
>Sie dürfen keinerlei Änderungen im Pfad `/libs` vornehmen.
>
>Alles, was dort vorhanden ist, kann sich beim nächsten Upgrade oder bei der Installation eines Service oder Fix Packs ändern.

## Eigenschaften {#properties}

Knoteneigenschaften werden verwendet, um die Datentypen zu definieren:

* [Datentypeigenschaften](#data-type-properties)
* und innerhalb dieser [fieldProperties](#fieldproperties)

### Datentypeigenschaften {#data-type-properties}

Alle Datentypen werden in einer Knotenstruktur wie folgt dargestellt:

`/libs/settings/dam/cfm/models/formbuilderconfig/datatypes/items`

Jeder Knoten unter `/items` verfügt über Eigenschaften, die definieren, wie dieser Datentyp im Modell-Editor dargestellt werden soll.

Alle folgenden Eigenschaften müssen vorhanden sein, damit der Datentyp im Modell-Editor vorhanden ist:

* `fieldIcon`

   [CoralUI-](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/coral-ui/coralui3/Coral.Icon.html#availableicons) Symbol, das den Datentyp in der Benutzeroberfläche des Modell-Editors darstellt.

* ` [fieldProperties](#fieldproperties)`

   Ein Array, das die Konfigurationseigenschaften für jeden Datentyp darstellt.

* `fieldResourceType`

   Der Sling-Ressourcentyp, der zum Rendern des Datentyps in einem Inhaltsfragment verwendet wird. Bei Datentypen, die auf unterschiedliche Weise gerendert werden können (z. B. als einfache Texteingabe und/oder mehrzeilige Texteingabe), muss diese Eigenschaft als Array erstellt werden, das alle Ressourcentypen enthält. Die Eigenschaft `renderasfield` wird automatisch zu `fieldProperties` hinzugefügt, damit der Benutzer den Ressourcentyp auswählen kann, den er zum Modell hinzufügen muss.

* `fieldPropResourceType`

   Der Sling-Ressourcentyp, der zum Rendern der Standardeigenschaft für den Datentyp verwendet wird.

   Für den Datentyp beispielsweise:

   * Einzelzeilentext `fieldPropResourceType` wäre eine `textfield`-Komponente
   * Boolesch, die `fieldPropResourceType` wäre eine `checkbox`-Komponente

* `fieldViewResourceType`

   Der Sling-Ressourcentyp, der beim Erstellen des Modells zum Rendern des Datentyps in der Vorschau verwendet wird. Wenn der Benutzer den Datentyp auf die linke Seite des Modell-Editors zieht, stellt die Eigenschaft `fieldViewResourceType` die Komponente dar, die dort gerendert wird. Dies wird für Fälle verwendet, in denen Sie nicht die vollständige Komponente rendern möchten, sondern nur einen Ersatz rendern möchten, der den Mehraufwand für den Modell-Editor minimiert.

* `fieldTitle`

   Eigenschaft, die den Titel dieses Datentyps definiert. Beispiel: **Einzelzeilentext** für eine `textfield`-Komponente, **Mehrzeiliger Text** für eine Multifield-Komponente.

* `valueType`

   Dies ist der Typ des Werts, den der Datentyp zurückgibt, wenn er intern gespeichert wird. Siehe [Zuordnungen](#mappings).

* `renderType`

   Dies ist eine interne Darstellung des Datentyps. Dadurch wird `valueType` mit einer UI-Komponente verbunden. Siehe [Zuordnungen](#mappings).

* `listOrder`

   Jeder Datentyp benötigt einen Wert, der seine Reihenfolge in der Liste darstellt. Dies wird verwendet, um beim Speichern des Modell-Editors die richtige Reihenfolge der verschiedenen Felder sicherzustellen (durch Drag &amp; Drop hinzugefügt/verschoben). Dieser Wert muss eine Ganzzahl sein. Es wird empfohlen, die Zahl aufsteigend und geordnet zuzuweisen. Bei der Erstellung eines neuen Datentyps ist es am besten, den Wert basierend auf dem letzten Datentyp in der Liste zuzuweisen (der höchste in den Datentypen vorhandene Wert von `listOrder`).

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
   <td>Zeichenfolge</td> 
   <td>text-single</td> 
  </tr> 
  <tr> 
   <td>Mehrzeilentext</td> 
   <td>Zeichenfolge mit Inhaltstyp<br /> </td> 
   <td>text-multi</td> 
  </tr> 
  <tr> 
   <td>Zahl (Ganzzahl/lang)<br /> </td> 
   <td>long</td> 
   <td>number</td> 
  </tr> 
  <tr> 
   <td>Zahl (double/float)</td> 
   <td>double</td> 
   <td>number</td> 
  </tr> 
  <tr> 
   <td>Boolesch</td> 
   <td>Boolesch</td> 
   <td>Boolesch</td> 
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
   <td>Zeichenfolge</td> 
   <td>tags</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Einige Typen (z. B. `string`, `long`) können mehrere Werte aufweisen. In diesem Fall wird die Komponente, die für das Rendern und Bearbeiten verwendet wird, normalerweise von einer Multifield-Komponente ( `granite/ui/components/coral/foundation/form/multifield`) umschlossen. Die Ausnahme sind Tags, bei denen die Bearbeitungskomponente für die korrekte Wiedergabe verantwortlich ist.

### fieldProperties {#fieldproperties}

Die Konfigurationseigenschaften für jeden Datentyp. Werte für `fieldProperties`:

* `base`

   Dies ist die Grundlage für alle `fieldProperties` -Komponenten. Die Definition befindet sich unter `/libs/dam/cfm/models/editor/components/datatypeproperties/base`.

   Sie enthält die Variable `fieldRoot`, die nachfolgende `fieldProperties` beim Erstellen von Eingaben verwenden kann, um den richtigen Pfad abzurufen.

   Beispiel: Um den richtigen Pfad für eine **Feldbezeichnung** zu erhalten, müssen Sie den Schlüssel zur Identifizierung der Komponente verwenden, zu der diese gehört. Die Eingabe für dieses Feld sollte `fieldRoot` + `<*fieldLabel*>` lauten.

* `checkboxfields`

   Diese Komponente fügt das standardmäßige Kontrollkästchen für den Datentyp `Boolean` sowie die Sling-Parameter `checked@Delete` und `checked@TypeHint` hinzu.

* `datepickerfields`

   Komponente, die die ausgeblendeten Eingaben hinzufügt, die für die Funktion der Datumsauswahl-Komponente erforderlich sind. Enthält das Erstellen der Eigenschaften `defaultDateField`, `displayedFormat`, `emptyText`, `valueFormat`, `minDate` und `maxDate`.

* `datetimepickerfields`

   Dadurch wird ein Auswahlfeld für den Datentyp `Date&Time` hinzugefügt, um zwischen den Optionen `Date` und `Date&Time` zu unterscheiden.

* `datevaluefield`

   Dadurch wird den Eigenschaften eine Datumsauswahl hinzugefügt, sodass ein Benutzer einen Standardwert für den Datentyp `Date&Time` auswählen kann.

* `descriptionfield`

   Diese Komponente fügt ein mehrzeiliges Textfeld hinzu, das die Beschreibung der aktuell ausgewählten Komponente im mehrzeiligen Editor darstellt. Sie wird automatisch vom Modell-Editor-Renderer am Ende jeder Datentypeigenschaft hinzugefügt.

* `labelfield`

   Komponente, die eine `textfield`-Eingabe hinzufügt, die die Feldbeschriftung für einen Datentyp hinzufügt, der Feldbeschriftungen enthalten kann.

* `maptopropertyfield`

   Diese Komponente fügt das Feld `Name` in den Eigenschaften hinzu und gibt der ausgewählten Komponente eines Datentyps eine Kennung. Sie sollte in allen Datentypen vorhanden sein.

* `maxlengthfield`

   Sie wird verwendet, um die `maxLength`-Eigenschaft für die Verwendung mit Datentypen hinzuzufügen, die diese Eigenschaft akzeptieren. Beispielsweise mit **Einzelzeilentext**, **Zahl** usw.

* `multieditorfield`

   Dadurch wird das gesamte ausgeblendete Feld hinzugefügt, das für die Verwendung des mehrzeiligen Editors erforderlich ist. Dieser wird durch den Datentyp **Mehrzeiliger Text** dargestellt.

* `mvfields`

   Komponente, die alle ausgeblendeten Felder hinzufügt, die für die Funktionsweise einer Multifield-Komponente erforderlich sind. Beispielsweise für die zweite Option eines Datentyps **Einzelzeilentext**. Dies sollte für jede Komponente hinzugefügt werden, die als Multifeld gerendert wird.

* `numbertypefield`

   Wählen Sie eine Option für den Datentyp **Zahl** aus, der zwischen **Integer** oder **Fraction** für den Datentyp **Zahl** auswählt.

* `numbervaluefield`

   Eine `numberfield`-Standardwertauswahl für den **Number** `type.options` Hierdurch werden die Optionseingaben für den Datentyp **Enumeration** hinzugefügt, mit dem die Werte für die Komponente &quot;Auswahlfeld&quot;bestimmt werden.

* `placeholderfield`

   Dies ist ein Textfeld, das als Eingabe für die Eigenschaft `emptyText` einer Komponente dient. Dies sollte von allen Datentypen verwendet werden, die einen Platzhalter akzeptieren (was nicht sehr kompliziert ist). z. B. **Einzelzeilentext**, **Zahl** usw.).

* `renderasfield`

   Dies ist die Komponente, die automatisch gerendert wird, wenn mehrere `fieldResourceTypes` in der Eigenschaft des Datentypknotens vorhanden sind.

* `requiredfield`

   Dies ist ein Kontrollkästchen, das die `required` -Eigenschaft für eine Komponente darstellt. Da die meisten Komponenten das Feld `required` akzeptieren, kann dieses Feld für die meisten Datentypen verwendet werden.

* `tagsfields`

   Komponenten, die die Eingaben hinzufügen, die für die Wiedergabe einer `tagfield`-Komponente erforderlich sind, und vom Datentyp **Tags** verwendet werden.

* `tagsroot`

   Eine Pfadauswahl, die vom Datentyp **Tags** verwendet wird, um den Stammpfad für die Komponente `tagsfield` festzulegen.

* `textfield`

   Wird vom Datentyp `Boolean` verwendet, um die Feldbezeichnung des durch diesen Datentyp definierten Kontrollkästchens festzulegen.

* `textvaluefield`

   Die Standardwerteigenschaft für den Datentyp **Einzelzeilentext**.

## Erstellen des Datentyps {#creating-your-data-type}

Um einen eigenen Datentyp zu erstellen, gehen Sie folgendermaßen vor:

* [Erstellen der Knotenstruktur](#creating-the-node-structure)
* [Definieren der Eigenschaften für Ihren Datentyp](#defining-the-properties-for-your-data-type)

Sie können dann [Ihren Datentyp ](#using-your-data-type) verwenden.

Sie können auch [Ihre eigene `fieldProperties`](#creating-your-own-fieldproperties-property) erstellen.

### Erstellen der Knotenstruktur {#creating-the-node-structure}

Die Knotenstruktur muss unter `/apps` erstellt werden, um die Datentypen zu überlagern. Wenn sie noch nicht vorhanden ist, müssen Sie Folgendes erstellen:

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

1. Unter `/items` können Sie neue Knoten hinzufügen, die Ihre neuen Datentypen darstellen:

   * Knotentyp: `nt:unstructured`
   * &quot;Eigenschaften: Siehe [Definieren der Eigenschaften für Ihren Datentyp](#defining-the-properties-for-your-data-type)

### Definieren der Eigenschaften für Ihren Datentyp {#defining-the-properties-for-your-data-type}

1. Legen Sie Werte für die folgenden [Datentypeigenschaften](#data-type-properties) fest, die für Ihren Datentyp erforderlich sind:

   * `fieldResourceType`
   * `fieldPropResourceType`
   * `fieldViewResourceType`

   Diese definieren, wie die Komponenten für Ihren Datentyp gerendert werden. Sie können jede beliebige Komponente sein. einschließlich Ihrer eigenen benutzerdefinierten Komponenten (erfordert einen passenden Satz von ` [fieldProperties](#fieldproperties)`).

   Definieren Sie diese Eigenschaften mit den entsprechenden Werten auf dem Knoten für Ihren Datentyp.

1. Bestimmen Sie die zu verwendende ` [fieldProperties](#fieldproperties)`. Dies hängt von den Attributen oder Eigenschaften ab, die Ihr `fieldResourceType` benötigt.

   Beispielsweise sollte ein `granite/ui/components/coral/foundation/form/textfield`einen **Beschriftungsnamen**, eine **Maximale Länge**, einen **Platzhaltertext** und eine **Standardwert**-Eigenschaft haben.

   Sie können aus den vordefinierten [fieldProperties](#fieldproperties) wählen oder [Ihre eigenen Eigenschaften](#creating-your-own-fieldproperties-property) erstellen.

   Definieren Sie diese Eigenschaften mit den entsprechenden Werten auf dem Knoten für Ihren Datentyp.

1. Legen Sie Werte für die folgenden [Datentypeigenschaften](#data-type-properties) fest:

   * `fieldIcon`
   * `fieldTitle`
   * `renderType`
   * `valueType`
   * `listOrder`

   Definieren Sie diese Eigenschaften mit den entsprechenden Werten auf dem Knoten für Ihren Datentyp.

### Verwenden des Datentyps {#using-your-data-type}

Nachdem Sie diese Knotenstruktur mit allen angewendeten Eigenschaften gespeichert haben, können Sie jedes Modell mit dem Modell-Editor öffnen und Ihren neuen Datentyp anzeigen und verwenden.

## Erstellen Ihrer eigenen fieldProperties-Eigenschaft {#creating-your-own-fieldproperties-property}

Sie können aus dem vordefinierten [fieldProperties](#fieldproperties) auswählen oder eine eigene erstellen:

1. Erstellen Sie eine Komponente unter:

   `/apps/dam/cfm/models/editor/components/datatypeproperties/`

   Wenn der Pfad nicht vorhanden ist, können Sie ihn mit `nt:folder` -Knoten erstellen.

   1. Um Zugriff auf die Variablen zu erhalten, sollte diese Komponente Folgendes erweitern:

      `/libs/dam/cfm/models/editor/components/datatypeproperties/base`* * *

   1. Die Komponente sollte wie folgt eingeschlossen werden können:

      `sling:include`

   1. Diese Komponente sollte entweder ein Feld (wenn ein Benutzer Daten einführen muss) oder eine ausgeblendete Eingabe mit den Eigenschaften rendern, die für Ihren Datentyp erforderlich sind. Beispielsweise erfordert eine Multifield-Komponente einen untergeordneten Knoten mit dem Feldtyp, den sie duplizieren soll. Daher sollte es eine Eingabe geben, die (durch Sling-POST-Mechanismus) einen untergeordneten Knoten eines bestimmten Typs erstellen kann.

1. Der Basisname dieser Komponente sollte `fieldProperties` hinzugefügt werden.
1. Wiederholen Sie diesen Vorgang für alle benötigten Eigenschaften.

