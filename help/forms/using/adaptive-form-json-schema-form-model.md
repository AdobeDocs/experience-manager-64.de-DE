---
title: Erstellen adaptiver Formulare mithilfe des JSON-Schemas
seo-title: Creating adaptive forms using JSON Schema
description: Adaptive Formulare können ein JSON-Schema als Formularmodell verwenden, sodass Sie vorhandene JSON-Vorlagen nutzen können, um adaptive Formulare zu erstellen.
seo-description: Adaptive forms can use JSON schema as form model, allowing you to leverage existing JSON schemas to create adaptive forms.
uuid: e73b4b4c-6ad7-4400-b776-5892549970c3
topic-tags: develop
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: bcda96ff-6c7d-46c4-a9e8-7e0fb245cde9
feature: Adaptive Forms
exl-id: 42c41625-7441-479c-bd07-7e96e867cc0a
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1207'
ht-degree: 86%

---

# Erstellen adaptiver Formulare mithilfe des JSON-Schemas {#creating-adaptive-forms-using-json-schema}

## Voraussetzungen {#prerequisites}

Für das Authoring eines adaptiven Formulars mit einem JSON-Schema als Formularmodell sind grundlegende Kenntnisse zu JSON-Schemas erforderlich. Es wird empfohlen, den folgenden Inhalt vor diesem Artikel durchzulesen.

* [Erstellen eines adaptiven Formulars](/help/forms/using/creating-adaptive-form.md)
* [JSON-Schema](https://json-schema.org/)

## Verwenden eines JSON-Schemas als Formularmodell  {#using-a-json-schema-as-form-model}

AEM Forms unterstützt die Erstellung eines adaptiven Formulars mit einem vorhandenen JSON-Schema als Formularmodell. Dieses JSON-Schema stellt die Struktur dar, in der Daten vom Back-End-System in Ihrem Unternehmen produziert oder genutzt werden. Das JSON-Schema, das Sie verwenden, sollte mit den [Spezifikationen der Version 4](https://json-schema.org/draft-04/schema) konform sein.

Die Haupteigenschaften bei der Verwendung eines JSON-Schemas sind wie folgt:

* Die Struktur der JSON wird als Baumstruktur in der Registerkarte für die Inhaltssuche im Authoring-Modus für ein adaptives Formular angezeigt. Sie können Elemente aus der JSON-Hierarchie in das adaptive Formular ziehen.
* Sie können das Formular mit JSON, das mit dem zugehörigen Schema konform ist, vorausfüllen.
* Bei der Übermittlung werden die vom Benutzer eingegebenen Daten in einem JSON-Format gesendet, das dem zugehörigen Schema entspricht.

Ein JSON-Schema besteht aus einfachen und komplexen Elementtypen. Die Elemente weisen Attribute auf, die dem Element Regeln hinzufügen. Wenn diese Elemente und Attribute in ein adaptives Formular gezogen werden, werden sie automatisch der entsprechenden Komponente des adaptiven Formulars zugeordnet.

Diese Zuordnung von JSON-Elementen zu Komponenten adaptiver Formulare ist wie folgt:

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
     <li>Die in enumNames aufgeführten Werte werden im Dropdown-Feld angezeigt.</li> 
     <li>Die in enum aufgeführten Werte werden für die Berechnung verwendet.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>Zeichenfolgen-Eigenschaft mit Formatbeschränkung. Z. B. E-Mail oder Datum.</p> <p>Syntax,</p> <p><code>{</code></p> <p><code>"type" : "string",</code></p> <p><code>"format" : "email"</code></p> <p><code>}</code></p> <p> </p> </td> 
   <td> 
    <ul> 
     <li>E-Mail-Komponente wird zugeordnet, wenn der Typ „Zeichenfolge“ lautet und das Format „E-Mail“.</li> 
     <li>Textfeld-Komponente mit Validierung wird zugeordnet, wenn der Typ „Zeichenfolge“ lautet und das Format „Hostname“.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>{</p> <p>"type" : "string",</p> <p>}</p> </td> 
   <td><br /> <br /> Textfeld<br /> <br /> <br /> </td> 
  </tr> 
  <tr> 
   <td>Nummern-Eigenschaft<br /> </td> 
   <td>Numerisches Feld, Untertyp auf „nicht verankert“ eingestellt<br /> </td> 
  </tr> 
  <tr> 
   <td>Ganzzahl-Eigenschaft<br /> </td> 
   <td>Numerisches Feld, Untertyp auf „Ganzzahl“ eingestellt<br /> </td> 
  </tr> 
  <tr> 
   <td>Boolesche Eigenschaft<br /> </td> 
   <td>Schalter<br /> </td> 
  </tr> 
  <tr> 
   <td>Objekt-Eigenschaft<br /> </td> 
   <td>Bedienfeld<br /> </td> 
  </tr> 
  <tr> 
   <td>Array-Eigenschaft</td> 
   <td>Wiederholbares Bedienfeld mit „min.“ und „max.“ gleich „minItems“ und „maxItems“. Nur homogene Arrays werden unterstützt. Daher muss die Elementbeschränkung ein Objekt sein, kein Array.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Allgemeine Schema-Eigenschaften {#common-schema-properties}

Bei einem adaptiven Formular werden jedem generierten Feld im JSON-Schema verfügbare Informationen zugeordnet. Führen Sie insbesondere die folgenden Aufgaben aus:

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

Im Folgenden finden Sie ein Beispiel eines JSON-Schemas.

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

Definitionsschlüssel kennzeichnen wiederverwendbare Schemas. Die wiederverwendbaren Schemadefinitionen werden verwendet, um Fragmente zu erstellen. Dies geschieht ähnlich wie beim Identifizieren komplexer Typen in XSD. Ein JSON-Beispielschema mit Definitionen wird unten angezeigt:

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

Das obige Beispiel definiert einen Kundendatensatz, bei dem jeder Kunde über eine Versand- und eine Rechnungsadresse verfügt. Die Struktur der beiden Adressen ist gleich: Straße, Stadt und Land. Daher sollten Sie die Adressen nicht duplizieren. Das erleichtert auch das Hinzufügen und Löschen von Feldern, wodurch zukünftige Änderungen einfach sind.

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
   <td><p>Gibt die Obergrenze für numerische Werte und Daten an. Standardmäßig ist der Höchstwert enthalten.</p> </td> 
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
   <td><p>Wenn „true“, muss der numerische Wert oder das Datum, der/das in der Komponente des Formulars festgelegt ist, kleiner sein als der numerische Wert oder das Datum, der/das für die Eigenschaft „maximum“ angegeben ist.</p> <p>Wenn „false“, muss der numerische Wert oder das Datum, der/das in der Komponente des Formulars festgelegt ist, kleiner oder gleich dem numerischen Wert oder Datum sein, der/das für die Eigenschaft „maximum“ angegeben ist.</p> </td> 
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
   <td><p>Wenn „true“, muss der numerische Wert oder das Datum, der/das in der Komponente des Formulars festgelegt ist, größer sein als der numerische Wert oder das Datum, der/das für die Eigenschaft „minimum“ angegeben ist.</p> <p>Wenn „false“, muss der numerische Wert oder das Datum, der/das in der Komponente des Formulars festgelegt ist, größer oder gleich dem numerischen Wert oder Datum sein, der/das für die Eigenschaft „minimum“ angegeben ist.</p> </td> 
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
   <td><p>Legt die zulässige Mindestanzahl von Zeichen in einer Komponente fest. Die minimale Länge muss größer oder gleich null sein.</p> </td> 
   <td> 
    <ul> 
     <li>Textfeld</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><code>maxLength</code></td> 
   <td>Zeichenfolge</td> 
   <td>Legt die zulässige Höchstzahl von Zeichen in einer Komponente fest. Die maximale Länge muss größer oder gleich null sein.</td> 
   <td> 
    <ul> 
     <li>Textfeld</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p><code>pattern</code></p> </td> 
   <td><p>Zeichenfolge</p> </td> 
   <td><p>Legt die Reihenfolge der Zeichen fest. Eine Komponente akzeptiert die Zeichen, wenn sie dem angegebenen Muster entsprechen.</p> <p>Die Eigenschaft „pattern“ ist dem Überprüfungsmuster der entsprechenden Komponente des adaptiven Formulars zugeordnet.</p> </td> 
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

Adaptive Formulare bieten keine Unterstützung für die folgenden JSON-Schemakonstrukte:

* Null-Typ
* Union-Typen wie „any“, „and“
* OneOf, AnyOf, AllOf und NOT
* Nur homogene Arrays werden unterstützt. Daher muss die Elementbeschränkung ein Array sein, kein Objekt.

## Häufig gestellte Fragen {#frequently-asked-questions}

**Warum kann ich nicht einzelne Elemente eines Teilformulars (Struktur aus einem komplexen Typ generiert) für wiederholbare Teilformulare ziehen (Wert von „minOccurs“ oder „maxOccurs“ ist größer als 1)?**

In einem wiederholbaren Teilformular müssen Sie das gesamte Teilformular verwenden. Wenn Sie nur einzelne Felder nutzen möchten, verwenden Sie die gesamte Struktur und löschen Sie unerwünschte Felder.

**Ich habe eine lange komplexe Struktur in der Inhaltssuche. Wie kann ich ein bestimmtes Element suchen?**

Es gibt zwei Optionen:

* Scrollen Sie durch die Baumstruktur
* Verwenden Sie das Suchfeld, um ein Element zu finden
