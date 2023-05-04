---
title: Erstellen adaptiver Formulare mithilfe des JSON-Schemas
seo-title: Creating adaptive forms using JSON Schema
description: Adaptive Formulare können das JSON-Schema als Formularmodell verwenden, sodass Sie vorhandene JSON-Schemas nutzen können, um adaptive Formulare zu erstellen.
seo-description: Adaptive forms can use JSON schema as form model, allowing you to leverage existing JSON schemas to create adaptive forms.
uuid: e73b4b4c-6ad7-4400-b776-5892549970c3
topic-tags: develop
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: bcda96ff-6c7d-46c4-a9e8-7e0fb245cde9
feature: Adaptive Forms
exl-id: 42c41625-7441-479c-bd07-7e96e867cc0a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1243'
ht-degree: 33%

---

# Erstellen adaptiver Formulare mithilfe des JSON-Schemas {#creating-adaptive-forms-using-json-schema}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Voraussetzungen {#prerequisites}

Das Authoring eines adaptiven Formulars mit einem JSON-Schema als Formularmodell erfordert grundlegende Kenntnisse des JSON-Schemas. Es wird empfohlen, den folgenden Inhalt vor diesem Artikel durchzulesen.

* [Erstellen eines adaptiven Formulars](/help/forms/using/creating-adaptive-form.md)
* [JSON-Schema](https://json-schema.org/)

## Verwenden eines JSON-Schemas als Formularmodell  {#using-a-json-schema-as-form-model}

AEM Forms unterstützt die Erstellung eines adaptiven Formulars mithilfe eines vorhandenen JSON-Schemas als Formularmodell. Dieses JSON-Schema stellt die Struktur dar, in der Daten vom Back-End-System in Ihrem Unternehmen produziert oder genutzt werden. Das JSON-Schema, das Sie verwenden, sollte mit den [Spezifikationen der Version 4](https://json-schema.org/draft-04/schema) konform sein.

Die wichtigsten Funktionen bei der Verwendung eines JSON-Schemas sind:

* Die Struktur der JSON-Datei wird im Authoring-Modus für ein adaptives Formular auf der Registerkarte Inhaltssuche als Baumstruktur angezeigt. Sie können Elemente aus der JSON-Hierarchie in das adaptive Formular ziehen und hinzufügen.
* Sie können das Formular mit JSON im Voraus ausfüllen, das mit dem zugehörigen Schema konform ist.
* Bei der Übermittlung werden die vom Benutzer eingegebenen Daten als JSON gesendet, das dem zugehörigen Schema entspricht.

Ein JSON-Schema besteht aus einfachen und komplexen Elementtypen. Die Elemente weisen Attribute auf, die dem Element Regeln hinzufügen. Wenn diese Elemente und Attribute in ein adaptives Formular gezogen werden, werden sie automatisch der entsprechenden Komponente des adaptiven Formulars zugeordnet.

Diese Zuordnung von JSON-Elementen zu adaptiven Formularkomponenten lautet wie folgt:

<table> 
 <tbody> 
  <tr> 
   <th><strong>JSON-Element, -Eigenschaften oder -Attribute</strong></th> 
   <th><strong>Komponente des adaptiven Formulars</strong></th> 
  </tr> 
  <tr> 
   <td><p>Zeichenfolgen-Eigenschaften mit enum- und enumNames-Beschränkung.</p> <p>Syntax,</p> <p> <code>{</code></p> <p><code>"type" : "string",</code></p> <p><code>"enum" : ["M", "F"]</code></p> <p><code>"enumNames" : ["Male", "Female"]</code></p> <p><code>}</code></p> <p> </p> </td> 
   <td><p>Dropdown-Komponente:</p> 
    <ul> 
     <li>Die in enumNames aufgeführten Werte werden in der Dropbox angezeigt.</li> 
     <li>Die in der Aufzählung aufgeführten Werte werden zur Berechnung verwendet.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>Zeichenfolgeneigenschaft mit Formateinschränkung. Beispielsweise E-Mail und Datum.</p> <p>Syntax,</p> <p><code>{</code></p> <p><code>"type" : "string",</code></p> <p><code>"format" : "email"</code></p> <p><code>}</code></p> <p> </p> </td> 
   <td> 
    <ul> 
     <li>Die E-Mail-Komponente wird zugeordnet, wenn der Typ Zeichenfolge und das Format E-Mail ist.</li> 
     <li>Textbox-Komponente mit Validierung wird zugeordnet, wenn der Typ Zeichenfolge ist und das Format der Hostname ist.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>{</p> <p>"type" : "string",</p> <p>}</p> </td> 
   <td><br /> <br /> Textfeld<br /> <br /> <br /> </td> 
  </tr> 
  <tr> 
   <td>number-Eigenschaft<br /> </td> 
   <td>Numerisches Feld mit Untertyp auf Gleitkommazahl eingestellt<br /> </td> 
  </tr> 
  <tr> 
   <td>Ganzzahl-Eigenschaft<br /> </td> 
   <td>Numerisches Feld mit Untertyp "integer"<br /> </td> 
  </tr> 
  <tr> 
   <td>Boolesche Eigenschaft<br /> </td> 
   <td>Schalter<br /> </td> 
  </tr> 
  <tr> 
   <td>Objekteigenschaft<br /> </td> 
   <td>Bedienfeld<br /> </td> 
  </tr> 
  <tr> 
   <td>Array-Eigenschaft</td> 
   <td>Wiederholbares Bedienfeld mit Mindest- und Höchstwert gleich "minItems"bzw. "maxItems". Nur homogene Arrays werden unterstützt. Daher muss die Elementbeschränkung ein Objekt sein, kein Array.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Allgemeine Schema-Eigenschaften {#common-schema-properties}

Das adaptive Formular verwendet die im JSON-Schema verfügbaren Informationen, um jedes generierte Feld zuzuordnen. Führen Sie insbesondere die folgenden Aufgaben aus:

* Die Eigenschaft title dient als Beschriftung für die Komponenten des adaptiven Formulars.
* Die Eigenschaft &quot;description&quot;wird als lange Beschreibung für eine Komponente eines adaptiven Formulars festgelegt.
* Die Standardeigenschaft dient als Anfangswert eines adaptiven Formularfelds.
* Die Eigenschaft maxLength wird als Attribut maxLength der Textfeldkomponente festgelegt.
* Die Eigenschaften &quot;minimum&quot;, &quot;maximum&quot;, &quot;exclusiveMinimum&quot;und &quot;exclusiveMaximum&quot;werden für die Komponente &quot;Numeric box&quot;verwendet.
* Um den Bereich für die DatePicker-Komponente zu unterstützen, werden zusätzliche JSON-Schema-Eigenschaften minDate und maxDate bereitgestellt.
* Mit den Eigenschaften minItems und maxItems wird die Anzahl der Elemente/Felder beschränkt, die zu einer Bedienfeldkomponente hinzugefügt oder daraus entfernt werden können.
* Die Eigenschaft readOnly legt das schreibgeschützte Attribut einer adaptiven Formularkomponente fest.
* Die erforderliche Eigenschaft markiert das Feld im adaptiven Formular als obligatorisch, während im Falle eines Bedienfelds (wobei der Typ &quot;Objekt&quot;ist) die endgültigen gesendeten JSON-Daten Felder mit leerem Wert aufweisen, die diesem Objekt entsprechen.
* Die pattern-Eigenschaft wird als Überprüfungsmuster (regulärer Ausdruck) im adaptiven Formular festgelegt.
* Die Erweiterung der JSON-Schema-Datei „.schema.json“ muss beibehalten werden. Beispiel: &lt;filename>.schema.json.

## Beispiel für ein JSON-Schema {#sample-json-schema}

Hier ist ein Beispiel für ein JSON-Schema.

```
{
 "$schema": "https://json-schema.org/draft-04/schema#",
 "definitions": {
  "employee": {
   "type": "object",
   "properties": {
    "userName": {
     "type": "string"
    },
    "dateOfBirth": {
     "type": "string",
     "format": "date"
    },
    "email": {
     "type": "string",
     "format": "email"
    },
    "language": {
     "type": "string"
    },
    "personalDetails": {
     "$ref": "#/definitions/personalDetails"
    },
    "projectDetails": {
     "$ref": "#/definitions/projectDetails"
    }
   },
   "required": [
    "userName",
    "dateOfBirth",
    "language"
   ]
  },
  "personalDetails": {
   "type": "object",
   "properties": {
    "GeneralDetails": {
     "$ref": "#/definitions/GeneralDetails"
    },
    "Family": {
     "$ref": "#/definitions/Family"
    },
    "Income": {
     "$ref": "#/definitions/Income"
    }
   }
  },
  "projectDetails": {
   "type": "array",
   "items": {
    "properties": {
     "name": {
      "type": "string"
     },
     "age": {
      "type": "number"
     },
     "projects": {
      "$ref": "#/definitions/projects"
     }
    }
   },
   "minItems": 1,
   "maxItems": 4
  },
  "projects": {
   "type": "array",
   "items": {
    "properties": {
     "name": {
      "type": "string"
     },
     "age": {
      "type": "number"
     },
     "projectsAdditional": {
      "$ref": "#/definitions/projectsAdditional"
     }
    }
   },
   "minItems": 1,
   "maxItems": 4
  },
  "projectsAdditional": {
   "type": "array",
   "items": {
    "properties": {
     "Additional_name": {
      "type": "string"
     },
     "Additional_areacode": {
      "type": "number"
     }
    }
   },
   "minItems": 1,
   "maxItems": 4
  },
  "GeneralDetails": {
   "type": "object",
   "properties": {
    "age": {
     "type": "number"
    },
    "married": {
     "type": "boolean"
    },
    "phone": {
     "type": "number",
     "aem:afProperties": {
      "sling:resourceType": "/libs/fd/af/components/guidetelephone",
      "guideNodeClass": "guideTelephone"
     }
    },
    "address": {
     "type": "string"
    }
   }
  },
  "Family": {
   "type": "object",
   "properties": {
    "spouse": {
     "$ref": "#/definitions/spouse"
    },
    "kids": {
     "$ref": "#/definitions/kids"
    }
   }
  },
  "Income": {
   "type": "object",
   "properties": {
    "monthly": {
     "type": "number"
    },
    "yearly": {
     "type": "number"
    }
   }
  },
  "spouse": {
   "type": "object",
   "properties": {
    "name": {
     "type": "string"
    },
    "Income": {
     "$ref": "#/definitions/Income"
    }
   }
  },
  "kids": {
   "type": "array",
   "items": {
    "properties": {
     "name": {
      "type": "string"
     },
     "age": {
      "type": "number"
     }
    }
   },
   "minItems": 1,
   "maxItems": 4
  }
 },
 "type": "object",
 "properties": {
  "employee": {
   "$ref": "#/definitions/employee"
  }
 }
}
```

### Wiederverwendbare Schemadefinitionen {#reusable-schema-definitions}

Definitionsschlüssel kennzeichnen wiederverwendbare Schemas. Die wiederverwendbaren Schemadefinitionen werden verwendet, um Fragmente zu erstellen. Sie ähnelt der Identifizierung komplexer Typen in XSD. Ein JSON-Beispielschema mit Definitionen wird unten angezeigt:

```
{
  "$schema": "https://json-schema.org/draft-04/schema#",
 
  "definitions": {
    "address": {
      "type": "object",
      "properties": {
        "street_address": { "type": "string" },
        "city":           { "type": "string" },
        "state":          { "type": "string" }
      },
      "required": ["street_address", "city", "state"]
    }
  },
 
  "type": "object",
 
  "properties": {
    "billing_address": { "$ref": "#/definitions/address" },
    "shipping_address": { "$ref": "#/definitions/address" }
  }
}
```

Im obigen Beispiel wird ein Kundendatensatz definiert, in dem jeder Kunde über eine Versand- und eine Rechnungsadresse verfügt. Die Struktur beider Adressen ist identisch - Adressen haben eine Straße, eine Stadt und einen Bundesstaat - daher ist es empfehlenswert, die Adressen nicht zu duplizieren. Außerdem wird das Hinzufügen und Löschen von Feldern für künftige Änderungen vereinfacht.

## Vorkonfigurieren von Feldern in JSON-Schemadefinitionen {#pre-configuring-fields-in-json-schema-definition}

Mit der Eigenschaft **aem:afProperties** können Sie ein JSON-Schemafeld so vorkonfigurieren, dass es einer benutzerdefinierten Komponente des adaptiven Formulars zugeordnet wird. Ein Beispiel wird unten angezeigt:

```
{
    "properties": {
        "sizeInMB": {
            "type": "integer",
            "minimum": 16,
            "maximum": 512,
            "aem:afProperties" : {
                 "sling:resourceType" : "/apps/fd/af/components/guideTextBox",
                 "guideNodeClass" : "guideTextBox"
             }
        }
    },
    "required": [ "sizeInMB" ],
    "additionalProperties": false
}
```

## Einschränken der gültigen Werte für eine Komponente eines adaptiven Formulars {#limit-acceptable-values-for-an-adaptive-form-component}

Sie können die folgenden Einschränkungen zu JSON-Schemaelementen hinzufügen, um die Werte zu beschränken, die für eine Komponente eines adaptiven Formulars gültig sind:

<table> 
 <tbody> 
  <tr> 
   <td><p><strong> Schemaeigenschaft</strong></p> </td> 
   <td><p><strong>Datentyp</strong></p> </td> 
   <td><p><strong>Beschreibung</strong></p> </td> 
   <td><p><strong>Komponente</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p><code>maximum</code></p> </td> 
   <td><p>Zeichenfolge</p> </td> 
   <td><p>Gibt die Obergrenze für numerische Werte und Daten an. Standardmäßig ist der Maximalwert enthalten.</p> </td> 
   <td> 
    <ul> 
     <li>Numerisches Feld</li> 
     <li>Numerische Schritte<br /> </li> 
     <li>Datumsauswahl</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p><code>minimum</code></p> </td> 
   <td><p>Zeichenfolge</p> </td> 
   <td><p>Gibt die Untergrenze für numerische Werte und Daten an. Standardmäßig ist der Mindestwert enthalten.</p> </td> 
   <td> 
    <ul> 
     <li>Numerisches Feld</li> 
     <li>Numerische Schritte</li> 
     <li>Datumsauswahl</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p><code>exclusiveMaximum</code></p> </td> 
   <td><p>Boolesch</p> </td> 
   <td><p>Wenn "true", muss der numerische Wert oder das Datum, der bzw. das in der Komponente des Formulars angegeben wird, kleiner als der numerische Wert oder das Datum sein, der bzw. das für die Eigenschaft "maximum"angegeben ist.</p> <p>Bei "false"muss der numerische Wert oder das Datum, der bzw. das in der Komponente des Formulars angegeben wird, kleiner oder gleich dem numerischen Wert oder Datum sein, der bzw. das für die Eigenschaft "maximum"angegeben ist.</p> </td> 
   <td> 
    <ul> 
     <li>Numerisches Feld</li> 
     <li>Numerische Schritte</li> 
     <li>Datumsauswahl</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p><code>exclusiveMinimum</code></p> </td> 
   <td><p>Boolesch</p> </td> 
   <td><p>Wenn "true", muss der in der Komponente des Formulars angegebene numerische Wert oder das Datum größer sein als der numerische Wert oder das Datum, der bzw. das für die Eigenschaft "minimum"angegeben wurde.</p> <p>Bei "false"muss der in der Komponente des Formulars angegebene numerische Wert oder das Datum größer oder gleich dem numerischen Wert oder Datum sein, der bzw. das für die Eigenschaft "minimum"angegeben wurde.</p> </td> 
   <td> 
    <ul> 
     <li>Numerisches Feld</li> 
     <li>Numerische Schritte</li> 
     <li>Datumsauswahl</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p><code>minLength</code></p> </td> 
   <td><p>Zeichenfolge</p> </td> 
   <td><p>Gibt die Mindestanzahl von Zeichen an, die in einer Komponente zulässig sind. Die minimale Länge muss größer oder gleich null sein.</p> </td> 
   <td> 
    <ul> 
     <li>Textfeld</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><code>maxLength</code></td> 
   <td>Zeichenfolge</td> 
   <td>Gibt die maximal zulässige Anzahl von Zeichen in einer Komponente an. Die maximale Länge muss größer oder gleich null sein.</td> 
   <td> 
    <ul> 
     <li>Textfeld</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p><code>pattern</code></p> </td> 
   <td><p>Zeichenfolge</p> </td> 
   <td><p>Gibt die Reihenfolge der Zeichen an. Eine Komponente akzeptiert die Zeichen, wenn die Zeichen dem angegebenen Muster entsprechen.</p> <p>Die pattern-Eigenschaft wird dem Überprüfungsmuster der entsprechenden adaptiven Formularkomponente zugeordnet.</p> </td> 
   <td> 
    <ul> 
     <li>Alle adaptiven Formulare, die einem XSD-Schema zugeordnet sind </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>maxItems</td> 
   <td>Zeichenfolge</td> 
   <td>Gibt die maximale Anzahl von Elementen in einem Array an. Die maximale Anzahl von Elementen muss größer oder gleich null sein.</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>minItems</td> 
   <td>Zeichenfolge</td> 
   <td>Gibt die Mindestanzahl von Elementen in einem Array an. Die Mindestanzahl von Elementen muss größer oder gleich null sein.</td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

## Nicht unterstützte Konstrukte  {#non-supported-constructs}

Adaptive Formulare unterstützen die folgenden JSON-Schema-Konstrukte nicht:

* Null-Typ
* Unionstypen, z. B. und
* OneOf, AnyOf, AllOf und NOT
* Nur homogene Arrays werden unterstützt. Die Elementbegrenzung muss also ein Objekt und kein Array sein.

## Häufig gestellte Fragen {#frequently-asked-questions}

**Warum kann ich nicht einzelne Elemente eines Teilformulars (Struktur aus einem komplexen Typ generiert) für wiederholbare Teilformulare ziehen (Wert von „minOccurs“ oder „maxOccurs“ ist größer als 1)?**

In einem wiederholbaren Teilformular müssen Sie das vollständige Teilformular verwenden. Wenn Sie nur einzelne Felder nutzen möchten, verwenden Sie die gesamte Struktur und löschen Sie unerwünschte Felder.

**Ich habe eine lange komplexe Struktur in der Inhaltssuche. Wie finde ich ein bestimmtes Element?**

Sie haben zwei Optionen:

* Scrollen Sie durch die Baumstruktur
* Verwenden Sie das Suchfeld, um ein Element zu finden
