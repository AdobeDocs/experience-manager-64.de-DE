---
title: Tabellen in adaptiven Formularen
seo-title: Tables in adaptive forms
description: 'Mit der Komponente „Tabelle“ in AEM Forms können Sie Tabellen in adaptiven Formularen erstellen, die auf mobile Layouts reagieren und den Einsatz von XDP-Tabellenkomponenten zulassen. '
seo-description: The Table component in AEM Forms lets you create tables in adaptive forms that are responsive to mobile layouts, and also allows using XDP table components.
uuid: 604cd51f-2a47-4410-b414-9cb13fe63713
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: e7d53127-3a0f-4c74-a656-25d9cf969f98
feature: Adaptive Forms
exl-id: 3269aab9-ac39-4adc-9a6b-9fe9f4276b29
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '2140'
ht-degree: 96%

---

# Tabellen in adaptiven Formularen {#tables-in-adaptive-forms}

Der Einsatz von Tabellen ist eine effektive, vereinfachte und geordnete Möglichkeit zur Darstellung komplexer Daten. Sie helfen Benutzern beim Identifizieren der Daten, die in Zeilen und Spalten angeordnet sind. Die meisten Formulare aus Finanzdienstleistungen und Behörden erfordern große Datentabellen zum Anzeigen von Zahlen und Durchführen von Berechnungen.

AEM Forms bietet eine Tabellenkomponente im Komponenten-Browser in der Seitenleiste, mit der Sie Tabellen in adaptiven Formularen erstellen können. Unter anderem sind folgende wichtige Funktionen verfügbar:

* Responsive Layout für Mobilgeräte
* Konfigurierbare Zeilen und Spalten
* Dynamisches Hinzufügen und Löschen von Zeilen zur Laufzeit
* Kombinieren oder Zusammenführen und Teilen von Zellen
* Unterstützung von Bildschirmlesehilfen
* Benutzerdefiniertes Layout mit CSS
* Kompatibel und zugeordnet mit der XDP-Tabellenkomponente
* Unterstützung für das Hinzufügen von Zeilen oder Zellen mit komplexen XSD-Typelementen
* Zusammenführen von Daten aus einer XML-Datei

## Erstellen einer Tabelle {#create-a-table}

Um eine Tabelle zu erstellen, ziehen Sie per Drag &amp; Drop die Tabellenkomponente vom Komponenten-Browser im Sidekick in das adaptive Formular. Standardmäßig enthält die Tabelle zwei Spalten und drei Zeilen, einschließlich der Zeile mit der Kopfzeile.

![Komponente „Tabelle“ in AEM-Seitenleiste](assets/sidebar-tables.png)

### Info zu Kopfzeilen- und Textzellen {#about-header-and-body-cells}

Die Kopfzeilenzellen sind Textfelder. Zum Ändern der Beschriftung einer Überschriftenzelle klicken Sie mit der rechten Maustaste auf die Überschriftenzelle und wählen Sie im Kontextmenü die Option **Bearbeiten**. Aktualisieren Sie im Dialogfeld „Statischen Text bearbeiten“ die Beschriftung im Feld **Wert** und klicken Sie auf **OK**.

Die Textzellen sind standardmäßig Textfelder. Sie können eine Textzelle durch eine beliebige andere, in Sidekick verfügbare adaptive Formularkomponente ersetzen (z. B. Ziffernfeld, Datumsauswahl oder Dropdownliste).

Beispiel: Die erste Textzeile in der folgenden Tabelle enthält ein Textfeld, eine Datumsauswahl und eine Dropdown-Liste.

![row-cell-types](assets/row-cell-types.png)

Sie können zwei oder mehr Textzellen zusammenführen, indem Sie die gewünschten Zellen auswählen, mit der rechten Maustaste klicken, und im Kontextmenü die Option **Zusammenführen** wählen. Außerdem können Sie eine zusammengeführte Zelle teilen, indem Sie mit der rechten Maustaste darauf klicken und im Kontextmenü die Option **Zellen teilen** wählen.

### Hinzufügen, Löschen und Verschieben von Zeilen und Spalten {#add-delete-move-rows-and-columns}

Sie können eine Zeile oder Spalte hinzufügen bzw. löschen sowie eine Zeile in einer Tabelle nach oben bzw. nach unten verschieben.

Um eine Zeile bzw. Spalte hinzuzufügen oder zu löschen oder eine Zeile zu verschieben, klicken Sie auf eine beliebige Zelle in der Zeile bzw. Spalte. Eine Dropdown-Liste wird jeweils am oberen Rand der Spalte und links neben der Zeile angezeigt. Die obere Liste enthält Optionen zum Hinzufügen bzw. Löschen der Spalte, die Liste links Optionen zum Hinzufügen, Löschen und Verschieben der Zeile.

* Der Vorgang „Hinzufügen“ fügt eine Zeile unterhalb bzw. eine Spalte rechts von der ausgewählten Zeile bzw. Spalte hinzu.
* Der Vorgang „Löschen“ löscht die ausgewählte Zeile bzw. Spalte.
* Der Vorgang „Nach oben“ bzw. „Nach unten“ verschiebt die ausgewählte Zeile nach oben bzw. nach unten.

Die Dropdown-Liste für die Zeile enthält auch die Option „Bearbeiten“ zum Bearbeiten von Zeileneigenschaften, Einstellungen und Stiloptionen.

![add-delete-move-row-column](assets/add-delete-move-row-column.png)

>[!NOTE]
>
>Sie können zwar eine beliebige Anzahl von Zeilen einer Tabelle hinzufügen, aber nur maximal sechs Spalten. Die Überschriftzeile der Tabelle kann nicht gelöscht werden.

### Die Spaltenbreite einer Tabelle einstellen {#set-column-width}

Führen Sie die folgenden Schritte aus, um die Spaltenbreite für eine Tabelle festzulegen:

1. Tippen Sie auf der **[!UICONTROL Inhalt]**-Registerkarte auf die Komponente **[!UICONTROL Tabelle]** und tippen Sie auf das Konfigurieren-Symbol (![Konfigurieren](assets/configure-icon.svg)).

1. Um die proportionale Breite der einzelnen Spalten der Tabelle festzulegen, geben Sie die jeweiligen Werte als kommagetrennte Liste in das **[!UICONTROL Spaltenbreite]**-Feld ein. Beispiel: Für eine Tabelle mit 3 Spalten führt die Eingabe des Werts „2,4,6“ in das **[!UICONTROL Spaltenbreite]**-Feld dazu, dass die Spaltenbreite für die erste Spalte auf 2/12, für die zweite auf 4/12 und für die dritte auf 6/12 eingestellt wird. 2/12 als Spaltenbreite für die erste Spalte entspricht einem Sechstel der Tabellenbreite. Parallel dazu wird mit dem Wert 4/12 die Breite der zweiten Spalte auf ein Drittel der Tabellenbreite und mit 6/12 die Breite der dritten Spalte auf die Hälfte der Tabellenbreite eingestellt.

### Hinzufügen einer Tabellenbeschreibung {#add-table-description}

Sie können der Tabelle eine Beschreibung hinzufügen, die erklärt, wie die Daten aufgebaut sind, damit sie von Bildschirmlesehilfen interpretiert und ausgelesen werden können. Hinzufügen der Beschreibung:

1. Wählen Sie die Tabelle aus und tippen Sie auf ![cmppr](assets/cmppr.png), damit ihre Eigenschaften in der Seitenleiste angezeigt werden.
1. Geben Sie auf der Registerkarte „Ein-/Ausgabehilfe“ die Zusammenfassung ein.
1. Klicken Sie auf **Fertig**.

## Konfigurieren des Tabellenstils {#configure}

Sie können den Stil für eine Tabelle definieren, indem Sie den Stilmodus in der Seitensymbolleiste verwenden. Führen Sie die folgenden Schritte aus, um zum Stilmodus zu wechseln und den Stil der Tabelle zu bearbeiten:

1. Tippen Sie in der Symbolleiste „Seite“ vor „Vorschau“ auf ![canvas-drop-down](assets/canvas-drop-down.png) > **Stil**.

1. Wählen Sie in der Seitenleiste die Tabelle aus und tippen Sie auf die Schaltfläche zum Bearbeiten ![edit_button](assets/edit-button.png).

   Die Stileigenschaften werden in der Seitenleiste angezeigt.

![Anpassen der Stileigenschaften einer Tabelle](assets/style-table.png)

>[!NOTE]
>
>Sie können das Farbschema für Kopf- und Textzeilen ändern, indem Sie die Werte der LESS-Variablen ändern. Weitere Informationen finden Sie unter [Designs in AEM Forms](/help/forms/using/themes.md)..

## Dynamisches Hinzufügen oder Löschen einer Zeile {#add-or-delete-a-row-dynamically}

Tabellen unterstützen standardmäßig das dynamische Hinzufügen oder Löschen von Zeilen zur Laufzeit.

1. Wählen Sie eine Tabellenzeile aus und tippen Sie auf ![cmppr](assets/cmppr.png).
1. Geben Sie auf der Registerkarte „Wiederholungseinstellungen“ die Mindest- und Höchstanzahl der Zeilen in der Tabelle an.
1. Klicken Sie auf **Fertig**.

Zur Laufzeit sehen Sie **`+`** und *`-`* -Schaltflächen zum Hinzufügen oder Löschen einer Zeile.

![add-delete-rows-dynamic](assets/add-delete-rows-dynamically.png)

>[!NOTE]
>
>Das dynamische Hinzufügen und Löschen einer Zeile wird im Mobile-Layout „Kopfzeilen links“ nicht unterstützt.

## Ausdrücke in einer Tabelle {#expressions-in-a-table}

Mit Tabellen in adaptiven Formularen können Sie Ausdrücke in JavaScript schreiben, um Funktionen (z. B. das Ein- bzw. Ausblenden einer Tabelle oder Zeile, das Addieren aller Zahlen und das Anzeigen der Summe in einer Zelle, das Aktivieren bzw. Deaktivieren einer Zelle, das Überprüfen der Benutzereingabe usw.) bereitzustellen. Diese Ausdrücke nutzen Skriptmodell-APIs für adaptive Formulare.

Während Tabellen und Zeilen nur Ausdrücke zum Steuern ihrer Sichtbarkeit unterstützen, unterstützen Zellen folgende Ausdrücke:

* **Initialisierungsskript**: Zum Ausführen einer Aktion nach der Initialsierung eines Felds.
* **Skript zum Bestätigen von Werten**: Zum Ändern der Komponenten eines Formulars, nachdem der Wert eines Felds geändert wurde.

>[!NOTE]
>
>Wenn das XFA-Änderungs-/Exit-Skript auch auf dasselbe Feld angewendet wird, wird das XFA-Änderungs-/Exit-Skript vor dem Skript zum Bestätigen von Werten ausgeführt.

* **Ausdrücke für die Berechnung**: Zum automatischen Berechnen des Werts eines Felds.
* **Überprüfungsausdrücke**: Zum Überprüfen eines Felds.
* **Ausdrücke für den Zugriff**: Zum Aktivieren/Deaktivieren eines Felds.
* **Ausdruck für die Sichtbarkeit**: Zum Steuern der Sichtbarkeit eines Felds oder Bereichs.

Der Sichtbarkeitsausdruck für eine Tabelle oder Zeile kann im entsprechenden Dialogfeld „Eigenschaften bearbeiten“ auf der Registerkarte „Bereichseigenschaften“ definiert werden. Die Ausdrücke für eine Zelle können im entsprechenden Dialogfeld „Eigenschaften bearbeiten“ auf der Registerkarte „Skript“ definiert werden.

Eine vollständige Liste der Klassen, Ereignisse, Objekte und öffentlichen APIs für adaptive Formulare finden Sie unter [JavaScript Library API-Referenz für adaptive Formulare](https://helpx.adobe.com/aem-forms/6/javascript-api/index.html).

## Layouts für Mobilgeräte {#mobile-layouts}

Tabellen in adaptiven Formularen eignen sich hervorragend für Mobilgeräte aufgrund ihres formbaren und responsiven Layouts. AEM Forms stellt zwei Tabellenlayouts für Mobilgeräte zur Verfügung: „Kopfzeilen links“ und „Reduzierbare Spalten“.

Sie können ein Tabellenlayout für Mobilgeräte auf der Registerkarte „Stil“ im Dialogfeld „Komponente bearbeiten“ einer Tabelle konfigurieren.

### Kopfzeilen links {#headers-on-left}

Im Layout „Kopfzeilen links“ werden die Spaltenüberschriften der Tabelle auf der linken Seite angeordnet und nur eine Zelle steht neben der Kopfzeile. Jede Zeile in diesem Layout ist ein eigenständiger Abschnitt. In den folgenden Abbildungen wird eine Tabelle auf einem Desktop mit derselben auf einem Mobilgerät verglichen.

![Desktop](assets/desktopview.png)
**Abbildung:** *Desktop-Ansicht einer Tabelle mit Layout &quot;Kopfzeile links&quot;*

![headersontheleft](assets/headersontheleft.png)
**Abbildung:** *Mobile Ansicht einer Tabelle mit Layout &quot;Kopfzeile links&quot;*

### Layout „Reduzierbare Spalten“  {#collapsible-columns-layout}

Im Layout „Reduzierbare Spalten“ werden die Spalten der Tabelle so reduziert, dass je nach Gerätegröße eine oder zwei Spalten angezeigt wird, während andere Spalten reduziert werden. Klicken Sie zum Anzeigen der anderen Spalten in der Tabelle auf das Symbol „Reduzieren/Erweitern“.

>[!NOTE]
>
>Das Layout „Reduzierbare Spalten“ ist zwar für Mobilgeräte optimiert, funktioniert aber auch auf Desktops, wenn die Breite nicht ausreicht, um alle Spalten in einer Tabelle anzuzeigen.

In den folgenden Abbildungen wird gezeigt, wie eine Tabelle mit reduzierten und erweiterten Spalten auf einem Mobilgerät aussieht.

![collapsed-column](assets/collapsed-column.png)
**Abbildung:** *Reduzierte Spalten einer Tabelle mit nur zwei Spalten, die auf einem Mobilgerät angezeigt werden*

![collapse_column](assets/collapsible_column.png)
**Abbildung:** *Erweiterte Spalte einer Tabelle auf einem Mobilgerät*

## Zusammenführen von Daten in einer Tabelle {#merge-data-in-a-table}

Sie können Tabellen in adaptiven Formularen zur Laufzeit mithilfe von Daten aus einer XML-Datei füllen. Die XML-Datendatei kann sich im lokalen Dateisystem des Computers, auf dem der AEM Forms-Server ausgeführt wird, oder im CRX-Repository befinden.

Beispiel: Eine Tabelle mit einer Zusammenfassung von Banktransaktionen, die mit Daten aus einer XML-Datei gefüllt werden soll.

![data-merge-table](assets/data-merge-table.png)

In diesem Beispiel ist die Elementnameneigenschaft für:

* die Zeile: **Row1**
* die Textzelle unter „Transaction“: **tableItem1**
* die Textzelle unter „Desription“ ist **tableItem2**
* die Textzelle unter „Transaction type“ **type**
* die Textzelle unter „Amount in USD“ **tableItem3**

Die XML-Datei, die Daten im folgenden Format enthält:

```xml
<?xml version="1.0" encoding="UTF-8"?><afData>
  <afUnboundData>
    <data>
 <typeSelect>0</typeSelect>
 <Row1>
      <tableItem1>2015-01-08</tableItem1>
      <tableItem2>Purchase laptop</tableItem2>
      <type>0</type>
      <tableItem3>12000</tableItem3>
 </Row1>
 <Row1>
      <tableItem1>2015-01-05</tableItem1>
      <tableItem2>Transport expense</tableItem2>
      <type>0</type>
      <tableItem3>120</tableItem3>
 </Row1>
 <Row1>
      <tableItem1>2014-01-08</tableItem1>
      <tableItem2>Laser printer</tableItem2>
      <type>0</type>
      <tableItem3>500</tableItem3>
 </Row1>
 <Row1>
      <tableItem1>2014-12-08</tableItem1>
      <tableItem2>Credit card payment</tableItem2>
      <type>0</type>
      <tableItem3>300</tableItem3>
 </Row1>
 <Row1>
      <tableItem1>2015-01-06</tableItem1>
      <tableItem2>Interest earnings</tableItem2>
      <type>1</type>
      <tableItem3>12000</tableItem3>
 </Row1>
 <Row1>
      <tableItem1>2015-01-05</tableItem1>
      <tableItem2>Payment from a client</tableItem2>
      <type>1</type>
      <tableItem3>500</tableItem3>
 </Row1>
 <Row1>
      <tableItem1>2015-01-08</tableItem1>
      <tableItem2>Food expense</tableItem2>
      <type>0</type>
      <tableItem3>120</tableItem3>
 </Row1>
 </data>
  </afUnboundData>
  <afBoundData>
    <data/>
  </afBoundData>
  <afBoundData/>
</afData>
```

In der XML-Beispieldatei werden die Daten für eine Zeile durch die `<Row1>`-Tags definiert, die den Elementnamen für die Zeile in der Tabelle festlegen. Innerhalb des `<Row1>`-Tags werden die Daten für die einzelnen Zellen innerhalb des Tags für dessen Elementnamen definiert (z. B. `<tableItem1>`, `<tableItem2>`, `<tableItem3>` und `<type>`).

Um diese Daten mit der Tabelle zur Laufzeit zusammenzuführen, muss das adaptive Formular, das die Tabelle enthält, auf den absoluten Pfad der XML-Datei zeigen. Dabei muss „wcmmode“ aktiviert sein. Beispiel: Wenn sich das adaptive Formular unter *http://localhost:4502/myForms/bankTransaction.html* und die XML-Datendatei unter *C:/myTransactions/bankSummary.xml* befindet, können Sie die Tabellen mit Daten unter folgender URL abrufen:

*http://localhost:4502/myForms/bankTransaction.html?dataRef=file:/// C:/myTransactions/bankSummary.xml?wcmmode=disabled*

![data-merged-table](assets/data-merged-table.png)

## Verwenden von XDP-Komponenten und komplexen XSD-Typen {#use-xdp-components-and-xsd-complex-types}

Wenn Sie ein adaptives Formular anhand einer XFA-Formularvorlage erstellt haben, sind die XFA-Elemente in der AEM Inhaltssuche auf der Registerkarte „Datenmodell“ verfügbar. Sie können diese XFA-Elemente, einschließlich Tabellen, in das adaptive Formular ziehen.

Das XFA-Tabellenelement wird der Tabellenkomponente zugeordnet und funktioniert standardmäßig in adaptiven Formularen. Alle Eigenschaften und Funktionen der XDP-Tabelle werden beibehalten, wenn sie in ein adaptives Formular verschoben werden, und Sie können beliebige Vorgänge darauf ausführen, wie auch auf native adaptive Formulare. Beispiel: Wenn eine Zeile in einer XDP-Tabelle als wiederholbar gekennzeichnet ist, wird sie auch wiederholt, wenn sie in adaptiven Formularen eingefügt wird.

Darüber hinaus können Sie XDP-Teilformulare, die in einem Teilformular enthalten sind, ziehen, um der Tabelle eine neue Zeile hinzuzufügen. Beachten Sie jedoch, dass verschachtelte Teilformulare nicht eingefügt werden können.

>[!NOTE]
>
>Eine XDP-Tabelle ohne Kopfzeile wird nicht der Tabellenkomponente des adaptiven Formulars zugeordnet. Stattdessen wird sie der Bereichskomponente des adaptiven Formulars mit unformatiertem Layout zugeordnet. Wenn Sie eine verschachtelte Tabelle aus einer XDP einem adaptiven Formular hinzufügen, wird die äußere Tabelle in einen Bereich konvertiert und die inneren Tabelle bleibt erhalten.

Darüber hinaus können Sie eine Gruppe von komplexen XSD-Typelementen ablegen, um eine Tabellenzeile zu erstellen. Eine neue Zeile wird direkt unterhalb der Zeile erstellt, in der die Elemente abgelegt wurden. Die Zellen, die mit komplexen XSD-Typelementen erstellt wurden, behalten eine Bindungsreferenz zur XSD bei. Sie können auch eine Textzelle mit einem komplexen XSD-Typelement ersetzen, indem Sie das Element in der Zelle ablegen.

>[!NOTE]
>
>Die Anzahl der Elemente in einer XDP-Tabellenkomponente, einem Teilformular oder in einem komplexen XSD-Typ kann die Anzahl der Zellen in einer Zeile nicht überschreiten. Beispielsweise können Sie nicht vier Elemente in einer Zeile ablegen, die nur drei Zellen hat. Dies führt zu einem Fehler.
>
>Wenn die Anzahl der Elemente kleiner als die Anzahl der Zellen in einer Zeile ist, fügt die neue Zeile zunächst die Elementzellen zu. Anschließend werden die verbleibenden Zellen in der Zeile mit Standardzellen ausgefüllt. Beispiel: Wenn Sie eine Gruppe von drei Elementen in einer Zeile ablegen, die aus vier Zellen besteht, dann basieren die ersten drei Zellen auf den abgelegten Elementen und die verbleibende Zelle ist eine Standardtabellenzelle.

## Wichtige Aspekte {#key-considerations}

* Wenn Sie beim Erstellen einer XSD-Tabelle Zeilen nach oben bzw. unten verschieben, gehen Daten aus der XML-Datei verloren, die beim Versenden des Formulars erstellt wurden.
* Jeder Textzelle in einer Standardtabelle ist ein vordefinierter Elementnamen zugeordnet. Wenn Sie eine andere Tabelle im adaptiven Formular hinzufügen, haben die Standardtextzellen in der neuen Tabelle denselben Elementnamen wie in der ersten Tabelle. In solch einem Fall beinhalten die Daten, die beim Senden des Formulars generiert wurden, die Daten in den Standardtextzellen einer der Tabellen. Stellen Sie daher sicher, dass Sie die Elementnamen für Standardtextzellen umbenennen, damit sie in den Tabellen eindeutig sind und Datenverluste vermieden werden.

   Beachten Sie, dass dies lediglich für die standardmäßigen Textzellen gilt. Wenn Sie einer Tabelle weitere Zeilen oder Spalten hinzufügen, werden automatisch eindeutige Elementnamen für nicht standardmäßige Textzellen generiert.
