---
title: Unterstützung der Picture-Klausel für HTML5-Formulare
seo-title: Picture clause support for HTML5 forms
description: HTML5-Formulare unterstützen die XFA-Picture-Klausel für Anzeigewerte und formatierte Werte für Datumsangaben, Text und numerische Symbole.
seo-description: HTML5 forms supports XFA Picture clause for display value and formatted value for date, text, and numeric symbols.
uuid: ca5074ce-8219-4f27-a37c-b1f0dca4ce03
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: 5e344be7-46cd-4e1f-ae3a-1f89c645cffe
feature: Mobile Forms
exl-id: b63758f1-b375-4c05-bd53-69e0346733c6
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '648'
ht-degree: 19%

---

# Unterstützung der Picture-Klausel für HTML5-Formulare {#picture-clause-support-for-html-forms}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

HTML5-Formulare unterstützen die XFA-Picture-Klausel für Anzeigewerte und formatierte Werte für Datumsangaben, Text und numerische Symbole. Folgende Ausdrücke der Picture-Klausel werden unterstützt:

* category(locale){picture-clause} | category(locale){picture-clause} | category(locale){picture-clause}
* category.subcategory{}

>[!NOTE]
>
>Mobile Forms unterstützt derzeit keine Edit Picture-Klausel. Außerdem werden die Klauselsymbole DateTime und Time Picture nicht unterstützt.

## Unterstützte Datumsfeldsymbole {#supported-date-field-symbols}

Unterstützter Ausdruck für Datums-Picture-Klausel:

* date.long{}
* date.short{}
* date.medium{}
* date.full{}
* date.short{}
* date{date Picture Clause symbols}

>[!NOTE]
>
>Das Standardmuster der Picture-Klausel ist das Muster {MMM D, YYYY}. Wenn kein Muster angewendet wird, wird das Standardmuster verwendet.

<table> 
 <tbody>
  <tr>
   <th><strong>Symbol</strong></th> 
   <th>Interpretation</th> 
  </tr>
  <tr>
   <td>D</td> 
   <td>1- oder 2-stelliger (1-31) Tag des Monats</td> 
  </tr>
  <tr>
   <td>DD</td> 
   <td>Mit 0 aufgefüllter zweistelliger (01-31) Tag des Monats.<br /> </td> 
  </tr>
  <tr>
   <td>M</td> 
   <td>1- oder 2-stelliger (1-12) Monat des Jahres.<br /> </td> 
  </tr>
  <tr>
   <td>MM</td> 
   <td>Mit 0 aufgefüllter zweistelliger (01-12) Monat des Jahres.<br /> </td> 
  </tr>
  <tr>
   <td>MMM</td> 
   <td>Abgekürzter Monatsname des aktuellen Gebietsschemas<br /> </td> 
  </tr>
  <tr>
   <td>MMMM</td> 
   <td>Vollständiger Monatsname des aktuellen Gebietsschemas<br /> </td> 
  </tr>
  <tr>
   <td>EEE</td> 
   <td>Abgekürzter Wochentag des aktuellen Gebietsschemas<br /> </td> 
  </tr>
  <tr>
   <td>EEEE</td> 
   <td>Vollständiger Wochentag des aktuellen Gebietsschemas<br /> </td> 
  </tr>
  <tr>
   <td>YY</td> 
   <td>2-stellige Jahreszahl, wobei 00 = 2000, 29 = 2029, 30 = 1930 und 99 = 1999<br /> </td> 
  </tr>
  <tr>
   <td>YYYY</td> 
   <td>4-stellige Jahreszahl<br /> </td> 
  </tr>
 </tbody>
</table>

## Numerische Picture-Klausel {#numeric-picture-clause}

HTML5-Formulare unterstützen numerische Picture-Symbole. Es gibt jedoch Unterschiede bei der Unterstützung von PDF forms und HTML Forms.

In **PDF forms**, wird eine Zahl unabhängig von der Anzahl der Symbole in der Picture-Klausel formatiert.

In **HTML Forms**, wird eine Zahl nur formatiert, wenn die Zahl weniger Ziffern enthält als die Anzahl der Symbole in der Picture-Klausel.

**Beispiel**: Beachten Sie eine Picture-Klausel: num{zzz,zzz,zz9}.

Die Zahl **10000** ist formatiert als **10.000** HTML und PDF forms.

Die Zahl 1000000 ist in PDF forms als 1.000.000 formatiert. In HTML Forms ist die Zahl jedoch nicht als 1000000 formatiert.

Unterstützte Ausdrücke für die numerische Picture-Klausel in **HTML-Formularen** sind:

* num.integer{}
* num.decimal{}
* num.currency{}
* num.percent{}
* num{Numeric Picture Clause Symbols}

<table> 
 <tbody>
  <tr>
   <th><strong>Symbol</strong></th> 
   <th><strong>Interpretation</strong></th> 
   <th>Eingabeanalyse</th> 
  </tr>
  <tr>
   <td>9</td> 
   <td><strong>Ausgabeformat</strong>: eine einstellige Zahl. Oder für die Ziffer Null, wenn die Eingabedaten leer sind oder sich ein Leerzeichen an der entsprechenden Position befindet.<br /> </td> 
   <td>Einstellige Zahl</td> 
  </tr>
  <tr>
   <td>Z</td> 
   <td><strong>Ausgabeformat</strong>: eine einstellige Zahl. Oder ein Leerzeichen, wenn die Eingabedaten leer sind, ein Leerzeichen oder die Ziffer Null an der entsprechenden Position.<br /> </td> 
   <td>Einstellige Zahl oder Leerzeichen</td> 
  </tr>
  <tr>
   <td>z</td> 
   <td><strong>Ausgabeformat</strong>: eine einstellige Zahl. Oder nichts, wenn die Eingabedaten leer sind, ein Leerzeichen oder die Null-Ziffer an der entsprechenden Position.<br /> </td> 
   <td>Einstellige Zahl oder nichts</td> 
  </tr>
  <tr>
   <td>E</td> 
   <td><strong>Ausgabeformat</strong>: der Exponent eines Gleitkommazahls, der aus dem Exponentialsymbol (E) besteht. Danach ein optionales Plus- oder Minuszeichen. gefolgt vom Exponentenwert.<br /> </td> 
   <td>Wie bei der Ausgabeformatierung</td> 
  </tr>
  <tr>
   <td>CR oder cr<br /> </td> 
   <td>Kreditsymbol (CR), wenn die Zahl negativ ist. Sonst nichts.</td> 
   <td><br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>S oder s<br /> </td> 
   <td>Ausgabeformatierung: ein Minuszeichen, wenn die Zahl negativ ist. Andernfalls Leerzeichen.<br /> </td> 
   <td>Minuszeichen, wenn die Zahl negativ ist. Pluszeichen, wenn die Zahl positiv ist</td> 
  </tr>
  <tr>
   <td>V</td> 
   <td>Dezimalwurzel des maßgeblichen Gebietsschemas. Einbeziehen der Dezimalwurzel in die Eingabeanalyse.</td> 
   <td><br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>v</td> 
   <td>Dezimalwurzel des maßgeblichen Gebietsschemas. Einbeziehen der Dezimalwurzel in die Eingabe- und Ausgabeformatierung.</td> 
   <td><br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>.</td> 
   <td>Dezimalwurzel des maßgeblichen Gebietsschemas.</td> 
   <td><br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>, (U+FF0C)</td> 
   <td>Gruppierungstrennzeichen des maßgeblichen Gebietsschemas</td> 
   <td><br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>$ (U+FF04)</td> 
   <td>Währungssymbol des maßgeblichen Gebietsschemas.</td> 
   <td><br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>% (U+FF05)</td> 
   <td>Prozentsymbol des maßgeblichen Gebietsschemas.</td> 
   <td><br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>( (U+FF08)</td> 
   <td>Linke Klammer, wenn die Zahl negativ ist. Andernfalls Leerzeichen.</td> 
   <td><br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>) (U+FF09)</td> 
   <td>Rechte Klammer, wenn die Zahl negativ ist. Andernfalls Leerzeichen.</td> 
   <td><br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>t</td> 
   <td>Tabulatorzeichen</td> 
   <td><br type="_moz" /> </td> 
  </tr>
 </tbody>
</table>

## Text-Picture-Klausel {#text-picture-clause}

HTML5-Formulare unterstützen die folgenden Text-Picture-Klausel-Ausdrücke:

* text{text Picture clause symbols}

| **Symbol** | **Interpretation** |
|---|---|
| A | Einzelnes alphabetisches Zeichen. |
| X | Einzelnes Zeichen. |
| O | Einzelnes alphanumerisches Zeichen. |
| 0 (null) | Einzelnes alphanumerisches Zeichen. |
| 9 | Einstellige Zahl. |
