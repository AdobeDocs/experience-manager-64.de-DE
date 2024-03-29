---
title: XFA-Unterstützung in XDP-basierten adaptiven Formularen
seo-title: XFA support in XDP-based adaptive forms
description: Listet unterstützte XFA-Ereignisse, Eigenschaften, Skripte und Überprüfungen in adaptiven Formularen auf.
seo-description: Lists supported XFA events, properties, scripts, and validation in adaptive forms.
uuid: 2f976de3-2cdf-4bbb-acd1-048a498930f0
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: eaf60421-097e-4feb-b661-433a512470ab
feature: Adaptive Forms
exl-id: 86596819-8108-409e-af14-4634e8a1959d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '719'
ht-degree: 62%

---

# XFA-Unterstützung in XDP-basierten adaptiven Formularen {#xfa-support-in-xdp-based-adaptive-forms}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Einführung {#introduction}

Adaptive Formulare bieten Unterstützung für verschiedene XFA-Ereignisse, Eigenschaften, Skripte und Überprüfungen, die in einer XDP-Datei definiert sind, einschließlich:

* Ausführung von Skripten, die für Ereignisse in der XDP-Datei definiert wurden.
* Erfassen von Standardwerten und Verhaltenseigenschaften für Felder in der XDP-Datei.
* Ausführung von Überprüfungsskripten, die in der XDP-Datei definiert sind.

Wenn ein adaptives Formular basierend auf einer XDP-Datei erstellt wird, werden die Eigenschaften, Ereignisse und Überprüfungen automatisch in die Benutzeroberfläche zum Erstellen von Formularen eingefügt. Allerdings können Formularautoren einige dieser Elemente überschreiben, um ein anderes Erlebnis bereitzustellen.

In diesem Artikel werden unterstützte XFA-Ereignisse, Eigenschaften und Überprüfungen aufgelistet, die in adaptiven Formularen berücksichtigt werden, und erläutert, wie sie in adaptiven Formularen überschrieben werden.

## Unterstützte XFA-Elemente und deren Zuordnung in adaptiven Formularen {#supported-xfa-elements-and-their-mapping-in-adaptive-forms-br}

### Felder {#fields}

Wenn ein adaptives Formular mit einer XDP-Datei erstellt wird, können Sie ein XFA-Feld per Drag-and-Drop in das adaptive Formular ziehen. In der folgenden Tabelle ist aufgeführt, wie XFA-Felder adaptiven Formularfeldern zugeordnet werden.

<table> 
 <tbody>
  <tr>
   <td><p><strong>XFA-Feld oder Container</strong></p> </td> 
   <td><p><strong>Entsprechende Komponente des adaptiven Formulars</strong></p> </td> 
  </tr>
  <tr>
   <td><p>Schaltfläche </p> </td> 
   <td><p>Schaltfläche</p> </td> 
  </tr>
  <tr>
   <td><p>Kontrollkästchen </p> </td> 
   <td><p>Kontrollkästchen</p> </td> 
  </tr>
  <tr>
   <td><p>Listenfeld </p> </td> 
   <td><p>Dropdownliste</p> </td> 
  </tr>
  <tr>
   <td><p>Datum-/Uhrzeitfeld </p> </td> 
   <td><p>Datumsauswahl</p> </td> 
  </tr>
  <tr>
   <td><p>Unterschrift freihändig</p> </td> 
   <td><p>Freihändige Unterschrift</p> </td> 
  </tr>
  <tr>
   <td><p>Numerisches Feld </p> </td> 
   <td><p>Numerisches Feld</p> </td> 
  </tr>
  <tr>
   <td><p>Dezimalfeld</p> </td> 
   <td><p>Numerisches Feld</p> </td> 
  </tr>
  <tr>
   <td><p>Textfeld </p> </td> 
   <td><p>Textfeld</p> </td> 
  </tr>
  <tr>
   <td><p>Kennwortfeld </p> </td> 
   <td><p>Kennwortfeld</p> </td> 
  </tr>
  <tr>
   <td><p>Bild</p> </td> 
   <td><p>Bild</p> </td> 
  </tr>
  <tr>
   <td><p>Text</p> </td> 
   <td><p>Text</p> </td> 
  </tr>
  <tr>
   <td><p>Teilformular </p> </td> 
   <td><p>Bereich</p> </td> 
  </tr>
  <tr>
   <td><p>Bereich (Gruppe)</p> </td> 
   <td><p>Bereich</p> </td> 
  </tr>
  <tr>
   <td><p>Teilformularsatz </p> </td> 
   <td><p>Bereich</p> </td> 
  </tr>
 </tbody>
</table>

### Eigenschaften {#properties}

Die folgende Tabelle erfasst, wie sich verschiedene XFA-Skripte, die in den XDP-Dateien definiert sind, in adaptiven Formularen verhalten.

<table> 
 <tbody>
  <tr>
   <td><p><strong>XFA-Komponenteneigenschaften</strong></p> </td> 
   <td><p><strong>Entsprechendes Verhalten in adaptiven Formularen</strong></p> </td> 
  </tr>
  <tr>
   <td><p>somExpression </p> </td> 
   <td><p>Der Eigenschaft der Verbindungsreferenz (bindRef) im adaptiven Formular zugeordnet.</p> </td> 
  </tr>
  <tr>
   <td><p>presence </p> </td> 
   <td><p>Der visible-Eigenschaft im adaptiven Formular zugeordnet. Sie können sie mit dem Sichtbarkeitsausdruck überschreiben.</p> </td> 
  </tr>
  <tr>
   <td><p>access </p> </td> 
   <td><p>Der enabled-Eigenschaft im adaptiven Formular zugeordnet. Sie können sie mit dem Zugriffsausdruck überschreiben.</p> </td> 
  </tr>
  <tr>
   <td><p>Barrierefreiheit: role </p> </td> 
   <td><p>Der role-Eigenschaft im adaptiven Formular zugeordnet.</p> </td> 
  </tr>
  <tr>
   <td><p>Barrierefreiheit: speakPriority </p> </td> 
   <td><p>Der speakPriority-Eigenschaft im adaptiven Formular zugeordnet.</p> </td> 
  </tr>
  <tr>
   <td><p>Barrierefreiheit: speakText</p> </td> 
   <td><p>Dem benutzerdefinierten barrierefreien Text im adaptiven Formular zugeordnet.</p> </td> 
  </tr>
  <tr>
   <td><p>Barrierefreiheit: toolTip </p> </td> 
   <td><p>Der short-description-Eigenschaft im adaptiven Formular zugeordnet.</p> </td> 
  </tr>
  <tr>
   <td><p>caption<em> (alle Feldtypen)</em></p> </td> 
   <td><p>Der Title-Eigenschaft im adaptiven Formular zugeordnet.</p> </td> 
  </tr>
  <tr>
   <td><p>displayFormat<em> (alle Feldtypen)</em></p> </td> 
   <td><p>Dem Anzeigemuster im adaptiven Formular zugeordnet.</p> </td> 
  </tr>
  <tr>
   <td><p>rawValue<em> (alle Feldtypen)</em></p> </td> 
   <td><p>Der value-Eigenschaft im adaptiven Formular zugeordnet.</p> </td> 
  </tr>
  <tr>
   <td><p>items<em> (Listenfeld, Kontrollkästchen)</em></p> </td> 
   <td><p>Der options-Eigenschaft im adaptiven Formular zugeordnet. Mit dem Optionsausdruck überschreibbar.</p> </td> 
  </tr>
  <tr>
   <td><p>maxChar<em> (Textfeld)</em></p> </td> 
   <td><p>Der Maximum characters allowed-Eigenschaft im adaptiven Formular zugeordnet.</p> </td> 
  </tr>
  <tr>
   <td><p>multiline<em> (Textfeld)</em></p> </td> 
   <td><p>Der Allow multiple lines-Eigenschaft im adaptiven Formular zugeordnet.</p> </td> 
  </tr>
  <tr>
   <td><p>fracDigit<em> (numerisches Feld, Dezimalfeld)</em></p> </td> 
   <td><p>Der Frac digits-Eigenschaft im adaptiven Formular zugeordnet.</p> </td> 
  </tr>
  <tr>
   <td><p>leadDigit<em> (numerisches Feld, Dezimalfeld)</em></p> </td> 
   <td><p>Der Lead digits-Eigenschaft im adaptiven Formular zugeordnet.</p> </td> 
  </tr>
  <tr>
   <td><p>multiSelect<em> (Listenfeld)</em></p> </td> 
   <td><p>Der Allows multiple selection-Eigenschaft im adaptiven Formular zugeordnet.</p> </td> 
  </tr>
 </tbody>
</table>

### Skripte {#scripts}

Die folgende Tabelle erfasst, wie verschiedene XFA-Skripten, die in der XDP-Datei definiert sind, sich in adaptiven Formularen verhalten.

<table> 
 <tbody>
  <tr>
   <td><p><strong>XFA-Skriptereignisse</strong></p> </td> 
   <td><p><strong>Entsprechendes Verhalten in adaptiven Formularen</strong></p> </td> 
  </tr>
  <tr>
   <td><p>initialize </p> </td> 
   <td><p>Dieses Skript wird zur Laufzeit ausgeführt und kann im adaptiven Formular nicht außer Kraft gesetzt werden.</p> </td> 
  </tr>
  <tr>
   <td><p>calculate</p> </td> 
   <td><p>Dem Ausdruck für die Berechnung im adaptiven Formular zugeordnet.</p> </td> 
  </tr>
  <tr>
   <td><p>validate </p> </td> 
   <td><p>Dem Überprüfungsausdruck im adaptiven Formular zugeordnet.</p> </td> 
  </tr>
  <tr>
   <td><p>ValidationState </p> </td> 
   <td><p>Dieses Skript wird zur Laufzeit ausgeführt und kann im adaptiven Formular nicht außer Kraft gesetzt werden.<br /> </p> </td> 
  </tr>
  <tr>
   <td><p>exit </p> </td> 
   <td><p>Dieses Skript wird zur Laufzeit ausgeführt und kann im adaptiven Formular nicht außer Kraft gesetzt werden.</p> </td> 
  </tr>
  <tr>
   <td><p>click (Schaltflächen)</p> </td> 
   <td><p>Dem Klick-Ausdruck der Schaltfläche zugeordnet.</p> </td> 
  </tr>
  <tr>
   <td><p>Unterstützung für Server-seitiges Skript</p> </td> 
   <td><p>Dieses Skript wird zur Laufzeit ausgeführt und kann im adaptiven Formular nicht außer Kraft gesetzt werden.</p> </td> 
  </tr>
  <tr>
   <td><p>Unterstützung für Web-Dienste</p> </td> 
   <td><p>Dieses Skript wird zur Laufzeit ausgeführt und kann im adaptiven Formular nicht außer Kraft gesetzt werden.</p> </td> 
  </tr>
  <tr>
   <td><p>Change (Scribble-Feld, Optionsschalter, Kontrollkästchen)</p> </td> 
   <td><p>Dieses Skript wird zur Laufzeit ausgeführt und kann im adaptiven Formular nicht außer Kraft gesetzt werden.</p> </td> 
  </tr>
 </tbody>
</table>

### Validierungen {#validations}

Die folgende Tabelle erfasst, wie XFA-Überprüfungen den Überprüfungen in adaptiven Formularen zugeordnet sind.

<table> 
 <tbody>
  <tr>
   <td><p><strong>XFA-Validierung</strong></p> </td> 
   <td><p><strong>Entsprechende Überprüfungen im adaptiven Formular</strong></p> </td> 
  </tr>
  <tr>
   <td><p>Validierungsmuster (formatTest)</p> </td> 
   <td><p>validatePictureClause</p> </td> 
  </tr>
  <tr>
   <td><p>Validierungsmuster-Meldung (formatTestMessage)</p> </td> 
   <td><p>validatePictureMessage</p> </td> 
  </tr>
  <tr>
   <td><p>Erforderlich (nullTest)</p> </td> 
   <td><p>mandatory </p> </td> 
  </tr>
  <tr>
   <td><p>Meldung bei leerem Feld (nullTestMessage) </p> </td> 
   <td><p>mandatoryMessage</p> </td> 
  </tr>
  <tr>
   <td><p>Skript validieren (scriptTest)</p> </td> 
   <td><p>validateExp</p> </td> 
  </tr>
  <tr>
   <td><p>Überprüfungsskript-Meldung (scriptTestMessage)</p> </td> 
   <td><p>validateMessage</p> </td> 
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Sie können die obligatorische Eigenschaft für Optionsfelder und Kontrollkästchengruppen im adaptiven Formular, die an XFA-Kontrollkästchen gebunden sind, nicht überschreiben.
