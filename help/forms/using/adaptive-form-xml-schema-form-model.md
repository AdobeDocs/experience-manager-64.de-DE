---
title: Adaptive Formulare mithilfe des XML-Schemas erstellen
seo-title: Creating adaptive forms using XML Schema
description: Adaptive Formulare können das XML-Schema als Formularmodell verwenden, sodass Sie vorhandene XSD-Vorlagen nutzen können, um adaptive Formulare zu erstellen. Sie können Schemaelemente per Drag & Drop aus XSD in Ihr adaptives Formular ziehen.
seo-description: Adaptive forms can use XML schema as form model, allowing you to leverage existing XSD templates to create adaptive forms. You can drag-and-drop schema elements from XSD onto your adaptive form.
uuid: a5f5d423-9b83-47e8-b0fa-88210d0d18d9
content-type: reference
topic-tags: adaptive_forms, develop
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: a1070d9e-fb7c-4134-b6d5-ffa2d3e9718d
feature: Adaptive Forms
exl-id: 5f6d23b2-ab8b-48fd-b853-eea7d6c9d651
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1080'
ht-degree: 36%

---

# Adaptive Formulare mithilfe des XML-Schemas erstellen {#creating-adaptive-forms-using-xml-schema}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Voraussetzungen {#prerequisites}

Die Erstellung eines adaptiven Formulars mit einem XML-Schema als Formularmodell erfordert grundlegende Kenntnisse zu XML-Schemata. Außerdem wird empfohlen, folgenden Inhalt vor diesem Artikel durchzulesen.

* [Erstellen eines adaptiven Formulars](/help/forms/using/creating-adaptive-form.md)
* [XML-Schema](https://www.w3.org/TR/xmlschema-2/)

## Verwenden eines XML-Schemas als Formularmodell {#using-an-xml-schema-as-form-model}

AEM Forms unterstützt die Erstellung eines adaptiven Formulars mithilfe eines vorhandenen XML-Schemas als Formularmodell. Dieses XML-Schema stellt die Struktur dar, in der Daten vom Back-End-System in Ihrem Unternehmen produziert oder genutzt werden.

Die wichtigsten Funktionen bei der Verwendung eines XML-Schemas sind:

* Die Struktur der XSD wird als Struktur auf der Registerkarte &quot;Content Finder&quot;im Authoring-Modus für ein adaptives Formular angezeigt. Sie können Elemente aus der XSD-Hierarchie in das adaptive Formular ziehen und hinzufügen.
* Sie können das Formular mit XML vorab ausfüllen, das mit dem zugehörigen Schema konform ist.
* Bei der Übermittlung werden die vom Benutzer eingegebenen Daten als XML gesendet, die dem zugehörigen Schema entspricht.

Ein XML-Schema besteht aus einfachen und komplexen Elementtypen. Die Elemente weisen Attribute auf, die dem Element Regeln hinzufügen. Wenn diese Elemente und Attribute in ein adaptives Formular gezogen werden, werden sie automatisch der entsprechenden Komponente des adaptiven Formulars zugeordnet.

Diese Zuordnung von XML-Elementen zu adaptiven Formularkomponenten lautet wie folgt:

<table> 
 <tbody> 
  <tr> 
   <th><strong>XML-Element oder -Attribut </strong></th> 
   <th><strong>Komponente des adaptiven Formulars</strong></th> 
  </tr> 
  <tr> 
   <td><code>xs:string</code></td> 
   <td>Textfeld</td> 
  </tr> 
  <tr> 
   <td><code>xs:boolean</code></td> 
   <td>Kontrollkästchen</td> 
  </tr> 
  <tr> 
   <td> 
    <ul> 
     <li><code>xs:unsignedInt</code></li> 
     <li><code>xs:xs:int</code></li> 
     <li><code class="code">xs:decimal 
        </code></li> 
     <li>Alle Typen numerischer Werte</li> 
    </ul> </td> 
   <td>Numerisches Feld</td> 
  </tr> 
  <tr> 
   <td><code>xs:date</code></td> 
   <td>Datumsauswahl</td> 
  </tr> 
  <tr> 
   <td><code class="code">xs:enumeration
      </code></td> 
   <td>Dropdown</td> 
  </tr> 
  <tr> 
   <td>Jedes Element vom Typ "Komplex"</td> 
   <td>Bedienfeld</td> 
  </tr> 
 </tbody> 
</table>

## Beispiel-XML-Schema {#sample-xml-schema}

Hier ist ein Beispiel für ein XML-Schema.

```xml
<?xml version="1.0" encoding="utf-8" ?> 
    <xs:schema targetNamespace="https://adobe.com/sample.xsd"
                    xmlns="https://adobe.com/sample.xsd"
                    xmlns:xs="https://www.w3.org/2001/XMLSchema"
                >

        <xs:element name="sample" type="SampleType"/>
        
        <xs:complexType name="SampleType">
            <xs:sequence>
                <xs:element name="leaderName" type="xs:string" default="Enter Name"/>
                <xs:element name="assignmentStartBirth" type="xs:date"/>
                <xs:element name="gender" type="GenderEnum"/>
                <xs:element name="noOfProjectsAssigned" type="IntType"/>
                <xs:element name="assignmentDetails" type="AssignmentDetails" 
                                            minOccurs="0" maxOccurs="10"/>
            </xs:sequence>
        </xs:complexType>

        <xs:complexType name="AssignmentDetails">
            <xs:attribute name="name" type="xs:string" use="required"/>
            <xs:attribute name="durationOfAssignment" type="xs:unsignedInt" use="required"/>
            <xs:attribute name="numberOfMentees" type="xs:unsignedInt" use="required"/>
             <xs:attribute name="descriptionOfAssignment" type="xs:string" use="required"/>
             <xs:attribute name="financeRelatedProject" type="xs:boolean"/>
       </xs:complexType>
  <xs:simpleType name="IntType">
            <xs:restriction base="xs:int">
            </xs:restriction>
        </xs:simpleType>
  <xs:simpleType name="GenderEnum">
            <xs:restriction base="xs:string">
                <xs:enumeration value="Female"/>
                <xs:enumeration value="Male"/>
            </xs:restriction>
        </xs:simpleType>
    </xs:schema>
```

>[!NOTE]
>
>Stellen Sie sicher, dass Ihr XML-Schema nur ein Stammelement enthält. Ein XML-Schema mit mehr als einem Stammelement wird nicht unterstützt.

## Hinzufügen spezieller Eigenschaften zu Feldern mithilfe eines XML-Schemas {#adding-special-properties-to-fields-using-xml-schema}

Sie können die folgenden Attribute zu XML-Schemaelementen hinzufügen, um spezielle Eigenschaften zu den Feldern des zugehörigen adaptiven Formulars hinzuzufügen.

<table> 
 <tbody> 
  <tr> 
   <th><strong>Schemaeigenschaft</strong></th> 
   <th><strong>Verwendung im adaptiven Formular</strong></th> 
   <th><strong>Unterstützt in </strong></th> 
  </tr> 
  <tr> 
   <td><code>use=required </code></td> 
   <td>Markiert ein Feld als Pflichtfeld<br /> </td> 
   <td>Attribut</td> 
  </tr> 
  <tr> 
   <td><code>default="default value"</code></td> 
   <td>Fügt einen Standardwert hinzu</td> 
   <td>Element und Attribut</td> 
  </tr> 
  <tr> 
   <td><code>minOccurs="3"</code></td> 
   <td><p>Gibt minimale Vorkommen an</p> <p>(Für wiederholbare Teilformulare (komplexe Typen))</p> </td> 
   <td>Element (komplexer Typ)</td> 
  </tr> 
  <tr> 
   <td><code class="code">maxOccurs="10"
      </code></td> 
   <td><p>Gibt maximale Vorkommen an</p> <p>(Für wiederholbare Teilformulare (komplexe Typen))</p> </td> 
   <td>Element (komplexer Typ)</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Wenn Sie ein Schemaelement in ein adaptives Formular ziehen, wird eine Standardbeschriftung wie folgt generiert:
>
>* Großschreibung des ersten Zeichens des Elementnamens
>* Einfügen von Leerzeichen bei Binnenmajuskeln.
>
>Wenn Sie beispielsweise das Schemaelement `userFirstName` hinzufügen, wird `User First Name` als Beschriftung im adaptiven Formular erstellt.

## Einschränken der gültigen Werte für eine Komponente eines adaptiven Formulars {#limit-acceptable-values-for-an-adaptive-form-component}

Sie können die folgenden Einschränkungen zu XML-Schemaelementen hinzufügen, um die Werte zu beschränken, die für eine Komponente eines adaptiven Formulars gültig sind:

<table> 
 <tbody> 
  <tr> 
   <td><p><strong> Schemaeigenschaft</strong></p> </td> 
   <td><p><strong>Datentyp</strong></p> </td> 
   <td><p><strong>Beschreibung</strong></p> </td> 
   <td><p><strong>Komponente</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p><code>totalDigits</code></p> </td> 
   <td><p>Zeichenfolge</p> </td> 
   <td><p>Gibt die maximal zulässige Anzahl von Stellen in einer Komponente an. Die angegebene Anzahl von Ziffern muss größer als null sein.</p> </td> 
   <td> 
    <ul> 
     <li>Numerisches Feld</li> 
     <li>Numerische Schritte</li> 
    </ul> </td> 
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
   <td><p><code>maxLength</code></p> </td> 
   <td><p>Zeichenfolge</p> </td> 
   <td><p>Gibt die maximal zulässige Anzahl von Zeichen in einer Komponente an. Die maximale Länge muss größer als null sein.</p> </td> 
   <td> 
    <ul> 
     <li>Textfeld</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p><code>length</code></p> </td> 
   <td><p>Zeichenfolge</p> </td> 
   <td><p>Gibt die genaue Anzahl der Zeichen an, die in einer Komponente zulässig sind. Die Länge muss größer oder gleich null sein.</p> </td> 
   <td> 
    <ul> 
     <li>Textfeld</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p><code>fractionDigits</code></p> </td> 
   <td><p>Zeichenfolge</p> </td> 
   <td><p>Gibt die maximal zulässige Anzahl von Dezimalstellen in einer Komponente an. Die fractionDigits müssen größer/gleich null sein.</p> </td> 
   <td> 
    <ul> 
     <li> Numerisches Feld mit Datentyp „Gleitkomma“ oder „Dezimal“.</li> 
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
 </tbody> 
</table>

## Häufig gestellte Fragen  {#frequently-asked-questions}

**Woher weiß ich, welches Element im Baum mit welchem XML-Element verknüpft ist?**

Wenn Sie in der Inhaltssuche auf ein Element doppelklicken, wird in einem Popup-Fenster ein Feldname und eine Eigenschaft mit dem Namen `bindRef`. Diese Eigenschaft ordnet das Baumstrukturelement dem Element oder Attribut im Schema zu.

![Ein bindref-Feld eines XML-Schemaelements](assets/dblclick.png)

Das Feld bindRef</code> zeigt die Verknüpfung zwischen einem Element der Baumstruktur und einem Element oder Attribut in einem Schema an.

>[!NOTE]
>
>Attribute weisen ein `@`-Symbol in ihrem `bindRef`-Wert auf, wodurch sie von Elementen unterschieden werden können. Beispiel: `/config/projectDetails/@duration`.

**Warum kann ich nicht einzelne Elemente eines Teilformulars (Struktur aus einem komplexen Typ generiert) für wiederholbare Teilformulare ziehen (Wert von „minOccurs“ oder „maxOccurs“ ist größer als 1)?**

In einem wiederholbaren Teilformular müssen Sie das vollständige Teilformular verwenden. Wenn Sie nur einzelne Felder nutzen möchten, verwenden Sie die gesamte Struktur und löschen Sie unerwünschte Felder.

**Ich habe eine lange komplexe Struktur in der Inhaltssuche. Wie finde ich ein bestimmtes Element?**

Sie haben zwei Optionen:

* Scrollen Sie durch die Baumstruktur
* Verwenden Sie das Suchfeld, um ein Element zu finden

**Was ist bindRef?**

`bindRef` ist die Verbindung zwischen einer Komponente eines adaptiven Formulars und einem Schemaelement oder -attribut. Dieses Element gibt den `XPath` vor, in dem der Wert, der von dieser Komponente oder diesem Feld erfasst wird, in der Ausgabe-XML verfügbar ist. Ein `bindRef`wird auch verwendet, wenn ein Feldwert aus (vorausgefüllter) XML im Voraus gefüllt wird.
