---
title: Verwenden von Diagrammen mit interaktiver Kommunikation
seo-title: Chart component in Interactive Communications
description: Mithilfe von Diagrammen in einer interaktiven Kommunikation können Sie große Mengen von Informationen zu einem einfach zu analysierenden und verständlichen visuellen Format zusammenfassen
seo-description: AEM Forms provides a chart component that you can use to create charts in your Interactive Communication. This document explains basic and agent configurations of the chart component.
uuid: dedd670c-030b-4497-bbcb-3ad935cebcda
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: interactive-communications
discoiquuid: 16c7e698-258d-4e63-9828-f538dc7d3294
feature: Interactive Communication
exl-id: 99077042-cba9-4429-b1e0-830739de5939
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2426'
ht-degree: 22%

---

# Verwenden von Diagrammen mit interaktiver Kommunikation {#using-charts-in-interactive-communications}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Mithilfe von Diagrammen in einer interaktiven Kommunikation können Sie große Mengen von Informationen zu einem einfach zu analysierenden und verständlichen visuellen Format zusammenfassen

Ein Diagramm oder Diagramm ist eine visuelle Darstellung von Daten. Sie fasst große Mengen von Informationen in ein leicht verständliches visuelles Format zusammen, sodass die Empfänger der interaktiven Kommunikation komplexe Daten besser visualisieren, interpretieren und analysieren können.

Beim Erstellen einer interaktiven Kommunikation können Sie Diagramme hinzufügen, um zweidimensionale Daten vom Formulardatenmodell der Vorlage für die interaktive Kommunikation visuell darzustellen. Mit der Diagrammkomponente können Sie die folgenden Arten von Diagrammen hinzufügen und konfigurieren:

* Kreisdiagramm
* Spalte
* Donut
* Balken (nur Webkanal)
* Line
* Linie und Punkt
* Punkt
* Bereich

## Hinzufügen und Konfigurieren eines Diagramms in einer interaktiven Kommunikation {#add-and-configure-chart-in-an-interactive-communication}

Führen Sie die folgenden Schritte aus, um einer interaktiven Kommunikation ein Diagramm hinzuzufügen:

1. Ziehen Sie die Diagrammkomponente aus den Komponenten in der AEM Seitenleiste in einen der folgenden Druck- oder Webkanäle einer interaktiven Kommunikation:

   * Druckkanal: Zielbereich und Bildfeld
   * Webkanal: Bereich und Zielbereich

   Die abgelegte Diagrammkomponente erstellt einen Platzhalter für ein Diagramm.

1. Tippen Sie auf die Diagrammkomponente im Editor für interaktive Kommunikation und wählen Sie in der Komponenten-Symbolleiste die Option **[!UICONTROL Konfigurieren (]** ![configure_icon](assets/configure_icon.png)).

   Die Seitenleiste Eigenschaften wird mit den grundlegenden Eigenschaften des Diagramms angezeigt.

   ![Grundlegende Eigenschaften eines Zeilentypdiagramms im Druckkanal](assets/chart_basicproperties.png)
   **Abbildung:** *Grundlegende Eigenschaften eines Liniendiagramms im Druckkanal*

   ![Grundlegende Eigenschaften eines Zeilentypdiagramms im Webkanal](assets/basicpropertieswebchannel.png)
   **Abbildung:** *Grundlegende Eigenschaften eines Linientypdiagramms im Webkanal*

1. Konfigurieren Sie die grundlegenden Eigenschaften des Diagramms für den Druckkanal und den Webkanal. Neben den allgemeinen Eigenschaften gibt es Eigenschaften, die spezifisch für den Druck- und Webkanal und den Diagrammtyp sind.

   * **[!UICONTROL Name]**: Name des Diagrammobjekts. Der Name des Diagramms, das Sie hier angeben, erscheint nicht in der Diagrammausgabe, sondern wird in Regeln verwendet, um auf das Diagramm zu verweisen.
   * **[!UICONTROL Diagrammtyp]**: Geben Sie den Diagrammtyp an: Kreis-, Spalten-, Ring-, Linien-, Linien- und Punkt-, Punkt- oder Bereichsdiagramm.
   * **[!UICONTROL Objekt ausblenden]**: Wählen Sie diese Option aus, um die Grafik in der endgültigen Ausgabe auszublenden.
   * Geben Sie Folgendes an für **[!UICONTROL x-Achse]** und **[!UICONTROL y-Achse]**:

      * **[!UICONTROL Titel]**: Geben Sie die Titel für die X- und Y-Achse an, die in der interaktiven Kommunikation angezeigt werden sollen.
      * **[!UICONTROL Datenmodellobjekt *]**: Suchen Sie nach Datenmodellobjekten für die X- und Y-Achse des Diagramms und wählen Sie sie aus dem Formulardatenmodell aus, das beim Erstellen der interaktiven Kommunikation angegeben wurde. Wählen Sie zwei Sammlungs-/Array-Typ-Eigenschaften desselben übergeordneten Datenmodellobjekts aus, die im Verhältnis zueinander aussagekräftig sind, um sie auf der X- und Y-Achse eines Diagramms darzustellen.
      * **[!UICONTROL Funktion]**: Um die Werte auf der Achse mithilfe statistischer Funktionen zu berechnen, wählen Sie Funktion für die X/Y-Achse. Weitere Informationen zu Funktionen finden Sie unter [Funktionen im Diagramm verwenden](#usefunction) und [Beispiel 2: Anwendung der Summen- und Mittelfunktionen in einem Liniendiagramm](#applicationsumfrequency).

   >[!NOTE]
   >
   >Für den Druckkanal sollte das Datenmodellobjekt, das Sie binden, auf der X-Achse vom Typ Zahl, Zeichenfolge oder Datum sein. Auf der Y-Achse sollte das Datenmodellobjekt, das Sie binden, vom Typ Zahl sein. Es wird empfohlen, die rechte Legende im Druckkanal zu verwenden.

   Weitere Informationen zu Diagrammeigenschaften finden Sie unter [Grundlegende Eigenschaften in Diagrammen](#basicpropertiescharts).

1. (Nur Druckkanal) Geben Sie in den Agenteneinstellungen an, ob es für den Agenten obligatorisch ist, dieses Diagramm zu verwenden. Wenn i **[!UICONTROL Es ist erforderlich, dass der Agent dieses Diagramm verwendet]** nicht ausgewählt ist, kann der Agent auf das Augensymbol für das Diagramm auf der Registerkarte Inhalt der Benutzeroberfläche des Agenten tippen, um das Diagramm ein-/auszublenden.

   ![chart_agentproperties](assets/chart_agentproperties.png)

1. Tippen Sie in der Seitenleiste &quot;Eigenschaften&quot;auf ![done_icon](assets/done_icon.png).

   Vorschau, um das Erscheinungsbild und die Daten des Diagramms anzuzeigen. Kehren Sie bei Bedarf zurück, um die Eigenschaften des Diagramms neu zu konfigurieren.

1. Kehren Sie zu anderen Änderungen in der interaktiven Kommunikation zurück.

## Beispiel 1: Diagrammausgabe in Druck und Web {#chartoutputprintweb}

Auf der Registerkarte Allgemein definieren Sie den Diagrammtyp, die Eigenschaften des Datenmodells des Quellformulars, die Daten enthalten, die Beschriftungen, die auf der X- und Y-Achse des Diagramms dargestellt werden sollen, und optional die statistische Funktion, um die Werte für die grafische Darstellung im Diagramm zu berechnen.

Anhand eines Kreditkartenauszugs, der mit einer interaktiven Kommunikation generiert wurde, werden wir die erforderlichen Informationen in den grundlegenden Eigenschaften im Detail verstehen. Angenommen, Sie möchten ein Diagramm erstellen, in dem die Höhe der verschiedenen Ausgaben in der Anweisung dargestellt wird. Sie möchten verschiedene Arten von Diagrammen für die Druck- und Webausgabe der interaktiven Kommunikation verwenden.

Dazu müssen Sie Folgendes angeben:

* **[!UICONTROL Diagrammtyp]** - in diesem Beispiel Spalte für den Druckkanal und Ringdiagramm für den Webkanal
* **[!UICONTROL Datenmodellobjekte]** als Quelle für die X- und Y-Achse des Diagramms - in diesem Beispiel Transaktionsbetrag für die X-Achse und Ausgabenname für die Y-Achse.
* **[!UICONTROL Titel]** für die X- und Y-Achse (für das Säulentypdiagramm im Druckkanal nur in diesem Beispiel) - in diesem Beispiel Betrag ($) für die X-Achse und Kosten für die Y-Achse.
* **[!UICONTROL Beschriftungsrichtung]** (nur für das Diagramm vom Typ Spalte im Druckkanal in diesem Beispiel) - in diesem Beispiel `Tilt Left`

* **[!UICONTROL QuickInfo]** zur Anzeige bei der Maus über eine Ausgabe (nur Webkanal) - in diesem Beispiel `${x}: $ ${y}`, das als `[Expense Label: $ Amount]` (Beispiel: Besuch des Themenparks: $ 315)

![Spaltendiagramm in der Druckausgabe einer interaktiven Kommunikation](assets/chartprintchannel.png)
**Abbildung:** *Spaltendiagramm in der Druckausgabe einer interaktiven Kommunikation*

**A.** Y-Achse - Aus der Eigenschaft des Formulardatenmodells abgerufener Betrag und die Eigenschaft Titel auf Betrag ($) **B.** Beschriftungsrichtung der X-Achse auf Linksbündig eingestellt **C.** X-Achse - Ausgabenbeschreibung, die aus der Eigenschaft des Formulardatenmodells und der Eigenschaft Titel abgerufen wird, die auf &quot;Spesenkonto&quot;eingestellt ist

![Ringdiagramm in der Webausgabe einer interaktiven Kommunikation](assets/chartwebchannel.png)
**Abbildung:** *Ringdiagramm in der Webausgabe einer interaktiven Kommunikation*

**A.** Die Eigenschaft &quot;Innerer Radius&quot;des Donuts ist festgelegt. **B.** Die Eigenschaft &quot;Legende anzeigen&quot;ist ausgewählt und die Eigenschaft &quot;Legendenposition&quot;ist auf &quot;Rechts&quot;festgelegt. **C.** QuickInfo zeigt die Details des Elements beim Bewegen der Maus an - QuickInfo ist auf ${x} festgelegt: $ ${y}

## Beispiel 2: Anwendung von Summen- und Häufigkeitsfunktionen in einem Liniendiagramm {#applicationsumfrequency}

Durch Anwenden von Funktionen in einem Diagramm können Sie Daten darstellen, die nicht direkt vom Formulardatenmodell bereitgestellt werden. In diesem Beispiel verwenden wir ein Kreditkartenabrechnungsbeispiel, um zu verstehen, wie Summen- und Häufigkeitsfunktionen auf das Diagramm angewendet werden können.

![Liniendiagramm ohne Funktion mit drei &quot;Bed and Breakfast&quot;-Transaktionen](assets/creditcarddatalinechartcopy.png)
**Abbildung:** *Liniendiagramm ohne Funktion mit drei &quot;Bed and Breakfast&quot;-Transaktionen*

### Sum-Funktion {#sum-function}

Sie können die Funktion sum anwenden, um Werte mehrerer Instanzen derselben Dateneigenschaft hinzuzufügen und sie nur einmal anzuzeigen. Im folgenden Diagramm wird beispielsweise die Summenfunktion auf die Y-Achse angewendet, um den Betrag der drei Bed and Breakfast-Transaktionen ($99.45, $78 und $12) zu addieren und nur eine Transaktion ($189.45) anzuzeigen.

Die Summenfunktion kann Diagramme nützlicher machen, wenn Sie die Summe für viele Instanzen derselben Dateneigenschaft sortieren und anzeigen möchten.

![creditcardchartsumfunctionCopy](assets/creditcardchartsumfunctioncopy.png)

### Häufigkeitsfunktion {#frequency-function}

Die Funktion Frequenz gibt die Anzahl der Werte auf der X- oder Y-Achse für einen bestimmten Wert auf der anderen Achse zurück. Mit der Anwendung der Frequenzfunktion auf der y-Achse (Amount/TransAmount) zeigt das Diagramm an, dass es drei Vorkommen von Bed and Breakfast-Transaktionen und ein Vorkommen von restlichen Transaktionen gegeben hat.

![creditcardchartfrequencyfunktionsCopy](assets/creditcardchartfrequencyfunctioncopy.png)

## Grundlegende Eigenschaften in Diagrammen {#basicpropertiescharts}

Auf der Registerkarte Allgemein können Sie die folgenden Eigenschaften konfigurieren:

**Name** Eine Kennung für das Diagrammelement. Der Name ist nicht im Diagramm sichtbar, aber hilfreich, wenn von anderen Komponenten, Skripten und SOM-Ausdrücken auf das Element verwiesen wird.

**Titel (nur Druckkanal)** Gibt den Titel des Diagramms an.

**Diagrammtyp** Gibt den Typ des Diagramms an, das Sie generieren möchten. Die verfügbaren Optionen sind Kreis, Spalte, Ringdiagramm, Balken (nur Webkanal), Linie, Linie und Punkt, Punkt und Bereich. Weitere Informationen finden Sie unter Beispiel 1: Diagrammausgabe in Druck und Web.

**X-Achse > Titel** Gibt den Titel für die X-Achse an.

**X-Achse > Datenmodellobjekt &amp;ast;** Geben Sie den Namen des Formulardatenmodellsammlungselements an, das auf der X-Achse dargestellt werden soll.

**X-Achse > Funktion** Gibt die statistische/benutzerdefinierte Funktion an, die für die Berechnung der Werte auf der X-Achse verwendet werden soll. Weitere Informationen zu Funktionen finden Sie unter Verwenden von Funktionen in Grafik und Beispiel 2: Anwendung der Summen- und Mittelfunktionen in einem Liniendiagramm.

**X-Achse > Beschriftungsrichtung** Richtung des Titels auf dem Diagramm im Druckkanal. Wenn Sie die Richtung der Beschriftung als &quot;Benutzerdefinierte Drehung&quot;wählen, wird das Feld &quot;Benutzerdefinierter Drehwinkel (Grad)&quot;angezeigt. Im Feld Benutzerdefinierter Drehwinkel (Grad) können Sie den Drehwinkel in Schritten von 15 Grad wählen.

**Y-Achse > Titel** Gibt den Titel für die Y-Achse an.

**Y-Achse > Datenmodellobjekt &amp;ast;** Gibt das Formulardatenmodellsammlungselement an, das auf der y-Achse dargestellt werden soll. Im Druckkanal sollte das Datenmodellobjekt für die Y-Achse vom Typ Zahl sein.

**Y-Achse > Funktion** Gibt die statistische/benutzerdefinierte Funktion an, die für die Berechnung der Werte auf der Y-Achse verwendet werden soll. Weitere Informationen zu Funktionen finden Sie unter Verwenden von Funktionen in Grafik und Beispiel 2: Anwendung der Summen- und Mittelfunktionen in einem Liniendiagramm.

**Legende anzeigen** Zeigt eine Legende für das Torten- oder Ringdiagramm an, wenn diese Option aktiviert ist.

**Legendenposition** Gibt die Position der Legende in Bezug auf das Diagramm an. Die verfügbaren Optionen sind rechts, links, oben und unten.

**Höhe (nur Druckkanal)** Höhe des Diagramms in Pixel.

**Breite (nur Druckkanal)** Breite des Diagramms in Pixel.

>[!NOTE]
>
>Sie können die Breite des Diagramms im Webkanal mithilfe der Stil-Ebene oder durch Anwenden eines Designs steuern.

**QuickInfo (nur Webkanal)** Gibt das Format an, in dem die QuickInfo beim Bewegen des Mauszeigers auf einem Datenpunkt im Diagramm im Webkanal angezeigt wird. Der Standardwert ist \${x}(\${y}). Je nach Diagrammtyp werden die Variablen \${x} und \${y} dynamisch durch die entsprechenden Werte auf der X-Achse und Y-Achse ersetzt und in der QuickInfo angezeigt, wenn Sie den Mauszeiger auf einen Punkt, ein Balken oder einen Ausschnitt im Diagramm bewegen.

Wenn Sie QuickInfo deaktivieren möchten, lassen Sie das Feld Quickinfo leer. Diese Option ist nicht auf Linien- und Bereichsdiagramme anwendbar. Beispiel: [Beispiel 1: Diagrammausgabe in Druck und Web](#chartoutputprintweb).

**CSS-Klasse (nur Webkanal)** Geben Sie den Namen einer CSS-Klasse im CSS-Klassenfeld an, um benutzerdefinierte Stile auf das Diagramm anzuwenden.

**Obligatorischer Seitenumbruch vor (nur Druckkanal)** Wählen Sie diese Option aus, um vor dem Diagramm einen obligatorischen Seitenumbruch hinzuzufügen und das Diagramm auf eine neue Seite zu setzen.

**Obligatorischer Seitenumbruch nach (nur Druckkanal)** Wählen Sie diese Option aus, um dem Diagramm einen obligatorischen Seitenumbruch hinzuzufügen und den Inhalt dem Diagramm auf einer neuen Seite anzuzeigen.

**Einzug (nur Druckkanal)** Geben Sie den Einzug des Diagramms links auf der Seite an.

**Diagrammspezifische Konfigurationen** Zusätzlich zu den allgemeinen Konfigurationen ist die folgende Diagrammkonfiguration verfügbar:

* **Innerer Radius**: Für Ringdiagramme verfügbar, um den Radius (in Pixel) des inneren Kreises im Diagramm anzugeben.
* **Linienfarbe**: für Linien-, Linien- und Punkt- sowie Flächendiagramme verfügbar sind, um den hexadezimalen Farbwert für die Linie im Diagramm anzugeben.
* **Punktfarbe**: für Punkt- und Linien- und Punktdiagramme verfügbar sind, um den hexadezimalen Farbwert für die Punkte im Diagramm anzugeben.

* **Bereichsfarbe**: für Bereichsdiagramme verfügbar sind, um den hexadezimalen Farbwert für den Bereich unter der Linie im Diagramm anzugeben.

## Funktionen im Diagramm verwenden {#usefunction}

Sie können ein Diagramm so konfigurieren, dass es mithilfe statistischer Funktionen Werte aus den Quelldaten für die Darstellung im Diagramm berechnet. Durch Anwenden von Funktionen in einem Diagramm können Sie Daten grafisch darstellen, die nicht direkt vom Formulardatenmodell bereitgestellt werden.

Während die Diagrammkomponente einige integrierte Funktionen enthält, können Sie eigene Funktionen schreiben und sie für die Verwendung in der Diagrammkonfiguration im Webkanal zur Verfügung stellen.

![Funktionsplan](assets/functionchart.png)

>[!NOTE]
>
>Sie können Funktionen verwenden, um Werte für die X- oder Y-Achse in einem Diagramm zu berechnen.

### Standardfunktionen {#default-functions}

Die folgenden Funktionen sind standardmäßig in der Diagrammkomponente verfügbar:

**Mittelwert (Durchschnitt)** Gibt den Durchschnitt der Werte auf der X- oder Y-Achse für einen bestimmten Wert auf der anderen Achse zurück.

**Summe** Gibt die Summe aller Werte auf der X- oder Y-Achse für einen bestimmten Wert auf der anderen Achse zurück.

**Maximum** Gibt das Maximum der Werte auf der X- oder Y-Achse für einen bestimmten Wert auf der anderen Achse zurück.

**Häufigkeit** Gibt die Anzahl der Werte auf der X- oder Y-Achse für einen bestimmten Wert auf der anderen Achse zurück.

**Bereich** Gibt die Differenz zwischen dem Maximum und dem Minimum der Werte auf der X- oder Y-Achse für einen bestimmten Wert auf der anderen Achse zurück.

**Median** Gibt den Wert zurück, der höhere und niedrigere Werte auf der X- oder Y-Achse bei einem bestimmten Wert auf der anderen Achse in der Mitte trennt.

**Minimum** Gibt das Minimum der Werte auf der X- oder Y-Achse für einen bestimmten Wert auf der anderen Achse zurück.

**Modus** Gibt den Wert mit den meisten Vorkommnissen auf der X- oder Y-Achse für einen bestimmten Wert auf der anderen Achse zurück

### Benutzerdefinierte Funktionen im Web-Kanal {#custom-functions-in-web-channel}

Neben den Standardfunktionen in Diagrammen können Sie auch benutzerdefinierte Funktionen in JavaScript™ schreiben und in der Funktionsliste der Diagrammkomponente für den Webkanal verfügbar machen.

Eine Funktion akzeptiert ein Array oder Werte und einen Kategorienamen als Eingaben und gibt einen Wert zurück. Beispiel:

```
Multiply(valueArray, category) {
 var val = 1;
 _.each(valueArray, function(value) {
 val = val * value;
 });
 return val;
}
```

Nachdem Sie eine benutzerdefinierte Funktion geschrieben haben, führen Sie die folgenden Schritte aus, um sie für die Verwendung in der Diagrammkonfiguration verfügbar zu machen:

1. Fügen Sie die benutzerdefinierte Funktion in der Client-Bibliothek hinzu, die mit der relevanten interaktiven Kommunikation verknüpft ist. Weitere Informationen finden Sie unter [Konfigurieren der Sendeaktion](/help/forms/using/configuring-submit-actions.md) und [Verwenden von Client-seitigen Bibliotheken](/help/sites-developing/clientlibs.md).

1. Um die benutzerdefinierte Funktion in der Dropdownliste „Funktion“ anzuzeigen, erstellen Sie in CRXDe Lite einen `nt:unstructured`-Knoten im Apps-Ordener mit den folgenden Eigenschaften:

   * Fügen Sie die Eigenschaft `guideComponentType` mit einem Wert wie `fd/af/reducer` hinzu. (mandatory)
   * Fügen Sie die Eigenschaft `value` zu einem vollständig qualifizierten Namen der benutzerdefinierten JavaScript™-Funktion hinzu. (obligatorisch) und setzen Sie den Wert auf den Namen der benutzerdefinierten Funktion, z. B. Multiplizieren, fest.
   * Fügen Sie die Eigenschaft `jcr:description` mit dem Wert hinzu, den Sie als Name der benutzerdefinierten Funktion anzeigen möchten, die in der Dropdown-Liste „Funktion“ angezeigt wird. Beispiel:**Multiplizieren**. 
   * Fügen Sie die Eigenschaft `qtip` mit einem Wert hinzu, der eine kurze Beschreibung der benutzerdefinierten Funktion darstellt. Es wird als QuickInfo angezeigt, wenn der Mauszeiger über den Funktionsnamen in der Dropdown-Liste **Funktion** bewegt wird.

1. Klicken **Alle speichern** , um die Konfiguration zu speichern.

Die Funktion ist jetzt für die Verwendung im Diagramm verfügbar.
