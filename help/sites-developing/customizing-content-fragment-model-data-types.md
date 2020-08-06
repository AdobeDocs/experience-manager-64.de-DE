---
title: NICHT VERÖFFENTLICHEN, SONDERN KEIN DELETE ZUM Anpassen der Datentypen für Inhaltsfragmentmodelle
seo-title: Anpassen von Datentypen für Inhaltsfragmentmodelle
description: Datentypen, die in Inhaltsfragmentmodellen verwendet werden, können angepasst werden.
seo-description: Datentypen, die in Inhaltsfragmentmodellen verwendet werden, können angepasst werden.
page-status-flag: de-activated
uuid: d8215dbf-2dbe-43cb-a5c1-dc1cb412a204
contentOwner: aheimoz
discoiquuid: a8b8155c-852c-4d16-b59b-7e19527c2bd4
noindex: true
translation-type: tm+mt
source-git-commit: 3bdff366a0d455b405c1f9de371ced98d25ae2e2
workflow-type: tm+mt
source-wordcount: '1642'
ht-degree: 2%

---


# NICHT VERÖFFENTLICHEN, SONDERN KEIN DELETE ZUM Anpassen der Datentypen für Inhaltsfragmentmodelle{#do-not-publish-but-do-not-delete-customizing-data-types-for-content-fragment-models}

[Inhaltsfragmente](/help/assets/content-fragments.md) basieren auf [Inhaltsfragmentmodellen](/help/assets/content-fragments-models.md). Diese Modelle basieren auf [Elementen](/help/assets/content-fragments.md#constituent-parts-of-a-content-fragment) unterschiedlicher Datentypen.

Es stehen verschiedene Datentypen zur Verfügung, darunter einzeiliger Text, mehrzeiliger Rich-Text, numerische Felder, boolesche Selektoren, Dropdown-Menüoptionen, Datum und Uhrzeit usw. AEM Benutzer können Datentypen auf der Grundlage der redaktionellen Absicht der entsprechenden Fragmente auswählen. Auf diese Weise können Sie einfache Textmodelle bis hin zu komplexen Modellen mit verschiedenen Inhaltsarten und dem damit verbundenen Erlebnis zum Erstellen von Fragmenten abdecken.

Datentypen werden durch eine [Kombination von Knoteneigenschaften](#properties) definiert, die an [bestimmten Positionen im Repository](#locations-in-the-repository)gespeichert werden. Sie können auch eigene [Datentypen](#creating-your-data-type) und [fieldProperties](#creating-your-own-fieldproperties-property)erstellen.

<!-- Please uncomment when files are used>
>[!NOTE]
>
>See also [Customizing Content Fragment Models](/help/sites-developing/customizing-content-fragment-models.md).
-->

## Speicherorte im Repository {#locations-in-the-repository}

Alle vordefinierten Datentypen werden wie folgt deklariert:

`/libs/settings`

Sie können neue Datentypen hinzufügen, indem Sie die Knotenstruktur wie folgt überlagern `/apps`:

`/apps/settings/dam/cfm/models/formbuilderconfig/datatypes/items`

>[!CAUTION]
>
>Sie dürfen keinerlei Änderungen im Pfad `/libs` vornehmen.
>
>Alles, was dort vorhanden ist, kann sich beim nächsten Upgrade oder bei der Installation eines Service oder Fix Packs ändern.

## Eigenschaften {#properties}

Knoteneigenschaften werden zur Definition der Datentypen verwendet:

* [Datentypeigenschaften](#data-type-properties)
* und innerhalb dieser [fieldProperties](#fieldproperties)

### Datentypeigenschaften {#data-type-properties}

Alle Datentypen werden in einer Knotenstruktur wie folgt dargestellt:

`/libs/settings/dam/cfm/models/formbuilderconfig/datatypes/items`

Jede Node unter `/items` verfügt über Eigenschaften, die definieren, wie dieser Datentyp im Modelleditor dargestellt werden soll.

Alle folgenden Eigenschaften müssen vorhanden sein, damit der Datentyp im Modelleditor vorhanden ist:

* `fieldIcon`

   [CoralUI-Symbol](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/coral-ui/coralui3/Coral.Icon.html#availableicons) zur Darstellung des Datentyps in der Benutzeroberfläche des Modelleditors.

* ` [fieldProperties](#fieldproperties)`

   Ein Array, das die Konfigurationseigenschaften für jeden Datentyp darstellt.

* `fieldResourceType`

   Der Sling-Ressourcentyp, der zum Rendern des Datentyps in einem Inhaltsfragment verwendet wird. Bei Datentypen, die auf unterschiedliche Weise wiedergegeben werden können (z. B. einfache Texteingabe und/oder mehrzeilige Texteingabe), muss diese Eigenschaft als Array erstellt werden, das alle Ressourcentypen enthält. Die `renderasfield` Eigenschaft wird automatisch hinzugefügt, `fieldProperties` damit der Benutzer den Ressourcentyp auswählen kann, den er dem Modell hinzufügen muss.

* `fieldPropResourceType`

   Der Sling-Ressourcentyp, der zum Rendern der Standardeigenschaft für den Datentyp verwendet wird.

   Beispiel für den Datentyp:

   * Einzelzeilentext `fieldPropResourceType` wäre eine `textfield` Komponente
   * Boolescher Wert, `fieldPropResourceType` der eine `checkbox` Komponente ist

* `fieldViewResourceType`

   Der Sling-Ressourcentyp, der zum Rendern des Datentyps in der Vorschau beim Erstellen des Modells verwendet wird. Wenn der Benutzer den Datentyp auf die linke Seite des Modelleditors zieht, stellt die `fieldViewResourceType` Eigenschaft die Komponente dar, die dort wiedergegeben wird. Dies wird für Fälle verwendet, in denen Sie nicht die vollständige Komponente wiedergeben möchten, sondern nur einen Ersatz, der den Aufwand für den Modelleditor minimiert.

* `fieldTitle`

   Eigenschaft, die den Titel dieses Datentyps definiert. Beispiel: **Einzeiliger Text** für eine `textfield` Komponente, **Mehrzeiliger Text** für eine Komponente mit mehreren Feldern.

* `valueType`

   Dies ist der Werttyp, den der Datentyp zurückgibt, wenn er intern gespeichert wird. Siehe [Zuordnungen](#mappings).

* `renderType`

   Dies ist eine interne Darstellung des Datentyps. Es verbindet die Komponente `valueType` mit einer UI-Komponente. Siehe [Zuordnungen](#mappings).

* `listOrder`

   Jeder Datentyp benötigt einen Wert, der seine Reihenfolge in der Liste darstellt. Dadurch wird beim Speichern des Modelleditors die richtige Reihenfolge der verschiedenen Felder gewährleistet (per Drag &amp; Drop hinzugefügt/verschoben). Dieser Wert muss eine Ganzzahl sein, und es wird empfohlen, die Zahl in aufsteigender Reihenfolge zuzuweisen. Beim Erstellen eines neuen Datentyps ist es am besten, den Wert basierend auf dem letzten Datentyp in der Liste zuzuweisen (dem höchsten in den Datentypen vorhandenen `listOrder` Wertwert).

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
   <td>Anzahl (Dublette/Fließkomma)</td> 
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
   <td>Auflistung</td> 
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
>Einige Typen (z. B. `string``long`u. a.) können mit mehreren Werten versehen sein. In diesem Fall wird die Komponente, die zum Rendern und Bearbeiten verwendet wird, normalerweise durch eine Multifield-Komponente ( `granite/ui/components/coral/foundation/form/multifield`) umschlossen. Die Ausnahme sind Tags, bei denen die Bearbeitungskomponente für die korrekte Wiedergabe verantwortlich ist.

### fieldProperties {#fieldproperties}

Die Konfigurationseigenschaften für jeden Datentyp. Werte für `fieldProperties`:

* `base`

   Dies ist die Grundlage für alle `fieldProperties` Komponenten. Die Definition liegt unter `/libs/dam/cfm/models/editor/components/datatypeproperties/base`.

   Es enthält die Variable `fieldRoot`, die anschließend beim Erstellen von Eingaben zum Abrufen des richtigen Pfads verwendet werden `fieldProperties` kann.

   Beispiel: Um den richtigen Pfad für eine **Feldbeschriftung** zu erhalten, müssen Sie die Komponente, zu der diese gehört, mit der Eingabetaste für dieses Feld `fieldRoot` + `<*fieldLabel*>`

* `checkboxfields`

   Diese Komponente fügt das Kontrollkästchen &quot;Standard&quot;für den `Boolean` Datentyp sowie die Sling-Parameter `checked@Delete` und -Parameter hinzu `checked@TypeHint`.

* `datepickerfields`

   Komponente, die die ausgeblendeten Eingaben hinzufügt, die für die Funktion der Datumsauswahl-Komponente erforderlich sind. Umfasst das Erstellen der Eigenschaften `defaultDateField`, `displayedFormat`, `emptyText`, `valueFormat`und `minDate` `maxDate`.

* `datetimepickerfields`

   Dadurch wird ein Auswahlfeld für den `Date&Time` Datentyp hinzugefügt, um zwischen `Date` und `Date&Time` Optionen zu unterscheiden.

* `datevaluefield`

   Dadurch wird den Eigenschaften ein Datumsbereich hinzugefügt, sodass ein Benutzer einen Standarddatentyp für den `Date&Time` Datentyp auswählen kann.

* `descriptionfield`

   Diese Komponente fügt ein mehrzeiliges Textfeld hinzu, das die Beschreibung der derzeit ausgewählten Komponente im mehrzeiligen Editor darstellt. Er wird automatisch vom Modelleditor-Renderer am Ende der einzelnen Datentypeigenschaften hinzugefügt.

* `labelfield`

   Komponente, die eine `textfield` Eingabe hinzufügt, mit der die Feldbeschriftung für einen Datentyp hinzugefügt wird, der Feldbeschriftungen enthalten kann.

* `maptopropertyfield`

   Diese Komponente fügt das `Name` Feld in den Eigenschaften hinzu und gibt der ausgewählten Komponente eines Datentyps einen Bezeichner. Es sollte in allen Datentypen vorhanden sein.

* `maxlengthfield`

   Sie wird verwendet, um die `maxLength` Eigenschaft für die Verwendung mit Datentypen hinzuzufügen, die diese Eigenschaft akzeptieren. Beispiel: **Einzelzeilentext**, **Nummer** usw.

* `multieditorfield`

   Dadurch wird das gesamte verborgene Feld hinzugefügt, das für die Arbeit des mehrzeiligen Editors erforderlich ist, der vom Datentyp **Mehrzeiliger Text** dargestellt wird.

* `mvfields`

   Komponente, die alle ausgeblendeten Felder hinzufügt, die für die Arbeit mit einer Multifield-Komponente erforderlich sind. Beispielsweise für die zweite Option eines **einzeiligen Texttyps** . Dies sollte für jede Komponente hinzugefügt werden, die als Multifeld gerendert wird.

* `numbertypefield`

   Wählen Sie die Option für den Datentyp &quot; **Zahl** &quot;, der für den Datentyp &quot; **Zahl** &quot;zwischen **Integer** oder **Fraction** ausgewählt wird.

* `numbervaluefield`

   Eine `numberfield` Standardwertauswahl für die **Zahl** `type.options` Hiermit werden die Optionseingaben für den Datentyp &quot; **Auflistung** &quot;hinzugefügt, mit dem die Werte für die Komponente &quot;Auswahlfeld&quot;bestimmt werden.

* `placeholderfield`

   Dies ist ein Textfeld, das als Eingabe für die `emptyText` Eigenschaft einer Komponente dient. Dies sollte von allen Datentypen verwendet werden, die einen Platzhalter akzeptieren (was nicht sehr kompliziert ist). z. B. **Einzelzeilentext**, **Nummer** usw.).

* `renderasfield`

   Dies ist die Komponente, die automatisch wiedergegeben wird, wenn mehrere Komponenten in der Eigenschaft des Datentypknotens vorhanden `fieldResourceTypes` sind.

* `requiredfield`

   Dieses Kontrollkästchen stellt die `required` Eigenschaft einer Komponente dar. Da die meisten Komponenten das `required` Feld akzeptieren, kann dieses Feld für die meisten Datentypen verwendet werden.

* `tagsfields`

   Komponenten, die die für die Wiedergabe einer `tagfield` Komponente erforderlichen Eingaben hinzufügen, die vom Datentyp &quot; **Tags** &quot;verwendet werden.

* `tagsroot`

   Eine Pfadauswahl, die vom **Tags** -Datentyp verwendet wird, um den Stammpfad für die `tagsfield` Komponente festzulegen.

* `textfield`

   Wird vom `Boolean` Datentyp verwendet, um die Feldbeschriftung des von diesem Datentyp definierten Kontrollkästchens einzustellen.

* `textvaluefield`

   Die Standardwerteigenschaft für den Datentyp &quot; **Einzelzeilentext** &quot;.

## Datentyp erstellen {#creating-your-data-type}

Um einen eigenen Datentyp zu erstellen, müssen Sie:

* [Knotenstruktur erstellen](#creating-the-node-structure)
* [Definieren der Eigenschaften für Ihren Datentyp](#defining-the-properties-for-your-data-type)

Anschließend können Sie Ihren Datentyp [verwenden](#using-your-data-type).

You can also [create your own `fieldProperties`](#creating-your-own-fieldproperties-property).

### Creating the Node Structure {#creating-the-node-structure}

Die Knotenstruktur muss unter erstellt werden, `/apps` um die Datentypen zu überlagern. Wenn es nicht bereits vorhanden ist, müssen Sie Folgendes erstellen:

1. Wenn es nicht bereits vorhanden ist, müssen Sie Folgendes erstellen:

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
   >`/apps/settings/dam` sollte bereits existieren.
   >
   >`/cfm/models/formbuilderconfig/datatypes/items` möglicherweise mit den angegebenen Nodetypen erstellt werden.

1. Unter können `/items` Sie neue Nodes hinzufügen, um Ihre neuen Datentypen zu repräsentieren:

   * Node Type: `nt:unstructured`
   * &quot;Eigenschaften: siehe [Definieren der Eigenschaften für Ihren Datentyp](#defining-the-properties-for-your-data-type)

### Definieren der Eigenschaften für Ihren Datentyp {#defining-the-properties-for-your-data-type}

1. Legen Sie Werte für die folgenden [Datentypeigenschaften](#data-type-properties) fest, die für Ihren Datentyp erforderlich sind:

   * `fieldResourceType`
   * `fieldPropResourceType`
   * `fieldViewResourceType`

   Diese legen fest, wie die Komponenten für Ihren Datentyp wiedergegeben werden. Sie können beliebige Komponenten sein. einschließlich Ihrer eigenen benutzerdefinierten Komponenten (benötigen Sie einen passenden Satz ` [fieldProperties](#fieldproperties)`).

   Definieren Sie diese Eigenschaften mit den entsprechenden Werten auf der Node für Ihren Datentyp.

1. Bestimmen Sie die ` [fieldProperties](#fieldproperties)` zu verwendende. Dies hängt von den Attributen oder Eigenschaften ab, die Sie `fieldResourceType` benötigen.

   Beispielsweise `granite/ui/components/coral/foundation/form/textfield`sollte ein Objekt über einen **Beschriftungsnamen**, eine **maximale Länge**, einen Platzhaltertext **und eine Eigenschaft** Standardwert **** verfügen.

   Sie können aus den vordefinierten [fieldProperties](#fieldproperties)wählen oder eigene Eigenschaften [erstellen](#creating-your-own-fieldproperties-property).

   Definieren Sie diese Eigenschaften mit den entsprechenden Werten auf der Node für Ihren Datentyp.

1. Legen Sie Werte für die folgenden [Datentypeigenschaften](#data-type-properties)fest:

   * `fieldIcon`
   * `fieldTitle`
   * `renderType`
   * `valueType`
   * `listOrder`

   Definieren Sie diese Eigenschaften mit den entsprechenden Werten auf der Node für Ihren Datentyp.

### Verwenden des Datentyps {#using-your-data-type}

Nachdem Sie diese Knotenstruktur mit allen angewendeten Eigenschaften gespeichert haben, können Sie jedes Modell mit dem Modelleditor öffnen und Ihren neuen Datentyp anzeigen und verwenden.

## Erstellen einer eigenen fieldProperties-Eigenschaft {#creating-your-own-fieldproperties-property}

Sie können aus den vordefinierten [fieldProperties](#fieldproperties)wählen oder eigene erstellen:

1. Komponente erstellen unter:

   `/apps/dam/cfm/models/editor/components/datatypeproperties/`

   Wenn der Pfad nicht vorhanden ist, können Sie ihn mithilfe von `nt:folder` Knoten erstellen.

   1. Um Zugriff auf die Variablen zu haben, sollte diese Komponente wie folgt erweitert werden:

      `/libs/dam/cfm/models/editor/components/datatypeproperties/base`* *

   1. Die Komponente sollte in folgenden Bereichen enthalten sein können:

      `sling:include`

   1. Diese Komponente sollte entweder ein Feld (wenn ein Benutzer Daten eingeben muss) oder eine ausgeblendete Eingabe mit den für den Datentyp erforderlichen Eigenschaften rendern. Eine Multifield-Komponente benötigt beispielsweise einen untergeordneten Knoten mit dem Feldtyp, den sie Duplikat haben soll. Daher sollte eine Eingabe vorhanden sein, die (durch Sling-POST-Mechanik) einen untergeordneten Knoten eines bestimmten Typs erstellen kann.

1. Der Basisname dieser Komponente sollte hinzugefügt werden `fieldProperties`.
1. Wiederholen Sie diese Schritte für alle gewünschten Eigenschaften.

