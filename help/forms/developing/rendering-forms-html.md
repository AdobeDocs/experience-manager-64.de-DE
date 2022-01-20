---
title: Rendern von Forms als HTML
seo-title: Rendering Forms as HTML
description: Verwenden Sie den Forms-Dienst, um Formulare als HTML aufgrund einer HTTP-Anforderung eines Webbrowsers wiederzugeben. Sie können die Java-API und die Web Service-API verwenden, um Formulare als HTML wiederzugeben.
seo-description: Use the Forms service to render forms as HTML in response to an HTTP request from a web browser. You can use the Java API and Web Service API to render forms as HTML.
uuid: bd8edb6f-333b-4ceb-9877-618f5377f56f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 669ede46-ea55-444b-a23f-23a86e5aff8e
role: Developer
exl-id: 2e8bcdf8-ae57-4ccd-945a-8f3fda4aa3c2
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '4137'
ht-degree: 1%

---

# Rendern von Forms als HTML {#rendering-forms-as-html}

Der Forms-Dienst rendert Formulare als HTML aufgrund einer HTTP-Anforderung eines Webbrowsers. Ein Vorteil der Wiedergabe eines Formulars als HTML besteht darin, dass der Computer, auf dem sich der Client-Webbrowser befindet, keine Adobe Reader, Acrobat oder Flash Player benötigt (für Formular-Guides (nicht mehr unterstützt)).

Um ein Formular als HTML wiederzugeben, muss der Formularentwurf als XDP-Datei gespeichert werden. Ein Formularentwurf, der als PDF-Datei gespeichert wird, kann nicht als HTML gerendert werden. Beachten Sie bei der Entwicklung eines Formularentwurfs in Designer, der als HTML wiedergegeben wird, die folgenden Kriterien:

* Verwenden Sie keine Objektbegrenzungseigenschaften, um Linien, Felder oder Raster auf dem Formular zu zeichnen. In einigen Browsern werden die Ränder möglicherweise nicht genau so angeordnet, wie sie in der Vorschau angezeigt werden. Die Objekte erscheinen eventuell übereinander oder schieben andere Objekte von ihren vorgesehenen Positionen.
* Sie können Linien, Rechtecke und Kreise verwenden, um den Hintergrund zu definieren.
* Zeichnen Sie Text etwas größer als das, was erforderlich zu sein scheint, um den Text aufzunehmen. In einigen Webbrowsern wird der Text nicht leserlich angezeigt.

>[!NOTE]
>
>Beim Rendern eines Formulars, das TIFF-Bilder enthält, mithilfe der `FormServiceClient` -Objekt `(Deprecated) renderHTMLForm` und `renderHTMLForm2` -Methoden verwenden, sind die TIFF-Bilder nicht im wiedergegebenen HTML-Formular sichtbar, das in Internet Explorer oder Mozilla Firefox angezeigt wird. Diese Browser bieten keine native Unterstützung für TIFF-Images.

## HTML-Seiten {#html-pages}

Wenn ein Formularentwurf als HTML-Formular wiedergegeben wird, wird jedes Teilformular der zweiten Ebene als HTML-Seite (Bedienfeld) wiedergegeben. Sie können die Hierarchie eines Teilformulars in Designer anzeigen. Untergeordnete Teilformulare, die zum Stammteilformular gehören (der Standardname eines Stammteilformulars ist &quot;form1&quot;), sind die Teilformulare des Bedienfelds. Das folgende Beispiel zeigt die Teilformulare eines Formularentwurfs.

```as3
     form1 
         Master Pages 
         PanelSubform1 
             NestedDynamicSubform 
                 TextEdit1 
         PanelSubform2 
             TextEdit1 
         PanelSubform3 
             TextEdit1 
         PanelSubform4 
             TextEdit1
```

Wenn Formularentwürfe als HTML-Formulare wiedergegeben werden, sind die Bedienfelder nicht auf eine bestimmte Seitengröße beschränkt. Wenn Sie über dynamische Teilformulare verfügen, sollten diese im Teilformular des Bedienfelds verschachtelt sein. Dynamische Teilformulare können auf eine unendliche Anzahl von HTML-Seiten erweitert werden.

Wenn ein Formular als HTML-Formular wiedergegeben wird, haben Seitengrößen (erforderlich für die Paginierung von Formularen, die als PDF wiedergegeben werden) keine Bedeutung. Da ein Formular mit flexiblem Layout auf eine unendliche Anzahl von HTML-Seiten erweitert werden kann, ist es wichtig, Fußzeilen auf der Übergeordneten Seite zu vermeiden. Eine Fußzeile unter dem Inhaltsbereich auf einer Übergeordneten Seite kann HTML-Inhalte überschreiben, die über eine Seitengrenze hinausfließen.

Sie müssen explizit von Bedienfeld zu Bedienfeld wechseln, indem Sie die `xfa.host.pageUp` und `xfa.host.pageDown` -Methoden. Sie ändern die Seiten, indem Sie ein Formular an den Forms-Dienst senden und den Forms-Dienst das Formular auf das Clientgerät zurückgeben lassen, normalerweise einen Webbrowser.

>[!NOTE]
>
>Der Prozess des Versands eines Formulars an den Forms-Dienst und des anschließenden Wiedergabevorgangs des Formulars durch den Forms-Dienst an das Client-Gerät wird als &quot;Round-Tripping-Daten&quot;an den Server bezeichnet.

>[!NOTE]
>
>Wenn Sie das Erscheinungsbild der HTML Digital Signature-Schaltfläche in einem HTML-Formular anpassen möchten, müssen Sie die folgenden Eigenschaften in der Datei fscdigsig.css ändern (in der Datei adobe-forms-ds.ear > adobe-forms-ds.war ):

**.fsc-ds-ssb**: Dieses Stylesheet gilt für Felder mit Leerzeichen.

**.fsc-ds-ssv**: Dieses Stylesheet gilt für ein gültiges Zeichenfeld.

**.fsc-ds-ssc**: Dieses Stylesheet gilt für ein gültiges Zeichenfeld, die Daten wurden jedoch geändert.

**.fsc-ds-ssi**: Dieses Stylesheet gilt für ungültige Zeichenfelder.

**.fsc-ds-popup-bg**: Diese Stylesheet-Eigenschaft wird nicht verwendet.

**.fsc-ds-popup-btn**: Diese Stylesheet-Eigenschaft wird nicht verwendet.

## Scripts ausführen {#running-scripts}

Ein Formularautor gibt an, ob ein Skript auf dem Server oder Client ausgeführt wird. Der Forms-Dienst erstellt eine verteilte, Ereignis-Verarbeitungsumgebung für die Ausführung der Formular-Intelligence, die mithilfe der `runAt` -Attribut. Weitere Informationen zu diesem Attribut oder zum Erstellen von Skripten in Formularentwürfen finden Sie unter [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63)

Der Forms-Dienst kann Skripten ausführen, während das Formular wiedergegeben wird. Daher können Sie ein Formular mit Daten vorab ausfüllen, indem Sie eine Verbindung zu einer Datenbank oder zu Webdiensten herstellen, die auf dem Client möglicherweise nicht verfügbar sind. Sie können auch die `Click` -Ereignis auf dem Server ausgeführt werden, damit der Client die Reisedaten an den Server umrundet. Dadurch kann der Client Skripte ausführen, die möglicherweise Serverressourcen erfordern, z. B. eine Unternehmensdatenbank, während ein Benutzer mit einem Formular interagiert. Bei HTML-Formularen können formcalc-Skripte nur auf dem Server ausgeführt werden. Daher müssen Sie diese Skripte markieren, damit sie unter `server` oder `both`.

Sie können Formulare entwerfen, die zwischen Seiten (Bedienfeldern) wechseln, indem Sie `xfa.host.pageUp` und `xfa.host.pageDown` -Methoden. Dieses Skript wird im `Click` und `runAt` -Attribut auf `Both`. Der Grund, den Sie auswählen `Both` ist so eingestellt, dass Adobe Reader oder Acrobat (für Formulare, die als PDF wiedergegeben werden) Seiten ändern können, ohne zum Server zu wechseln, und dass HTML-Formulare Seiten ändern können, indem Daten zum Umblättern an den Server gesendet werden. Das heißt, ein Formular wird an den Forms-Dienst gesendet und ein Formular wird als HTML wiedergegeben, wobei die neue Seite angezeigt wird.

Es wird empfohlen, Skriptvariablen und Formularfelder nicht mit den gleichen Namen wie Elemente zu versehen. In einigen Webbrowsern wie Internet Explorer wird eine Variable möglicherweise nicht mit demselben Namen wie ein Formularfeld initialisiert, was zu einem Skriptfehler führt. Es empfiehlt sich, Formularfelder und Skriptvariablen unterschiedliche Namen zu geben.

Achten Sie beim Rendern von HTML-Formularen, die sowohl Seitennavigationsfunktionen als auch Formularskripte enthalten (z. B. wenn ein Skript Felddaten jedes Mal aus einer Datenbank abruft, wenn das Formular wiedergegeben wird) darauf, dass sich das Formularskript im form:calculate -Ereignis und nicht im form:readyevent befindet.

Formularskripte, die sich im form:ready -Ereignis befinden, werden nur einmal während der ersten Wiedergabe des Formulars ausgeführt und nicht für nachfolgende Seitenabrufe. Im Gegensatz dazu wird das form:calculate -Ereignis für jede Seitennavigation ausgeführt, in der das Formular wiedergegeben wird.

>[!NOTE]
In einem mehrseitigen Formular werden Änderungen, die von JavaScript an einer Seite vorgenommen werden, nicht beibehalten, wenn Sie zu einer anderen Seite wechseln.

Sie können benutzerdefinierte Skripte vor dem Senden eines Formulars aufrufen. Diese Funktion funktioniert in allen verfügbaren Browsern. Es kann jedoch nur verwendet werden, wenn Benutzer das HTML-Formular rendern, das über seine `Output Type` Eigenschaft auf `Form Body`. Es funktioniert nicht, wenn die Variable `Output Type` is `Full HTML`. Anweisungen zum Konfigurieren dieser Funktion finden Sie in der Administration-Hilfe unter Konfigurieren von Formularen .

Sie müssen zunächst eine Rückruffunktion definieren, die vor dem Senden des Formulars aufgerufen wird, wobei der Name der Funktion `_user_onsubmit`. Es wird davon ausgegangen, dass die Funktion keine Ausnahme ausgibt. Andernfalls wird die Ausnahme ignoriert. Es wird empfohlen, die JavaScript-Funktion im Kopfabschnitt des HTML-Codes zu platzieren. Sie können sie jedoch an einer beliebigen Stelle vor dem Ende der Skript-Tags deklarieren, die Folgendes enthalten: `xfasubset.js`.

Wenn der Formularserver eine XDP-Datei rendert, die eine Dropdown-Liste enthält, werden neben der Erstellung der Dropdown-Liste auch zwei ausgeblendete Textfelder erstellt. Diese Textfelder speichern die Daten der Dropdown-Liste (eines speichert den Anzeigenamen der Optionen, das andere speichert den Wert für die Optionen). Daher werden jedes Mal, wenn ein Benutzer das Formular sendet, alle Daten der Dropdown-Liste gesendet. Wenn Sie nicht jedes Mal so viele Daten senden möchten, können Sie ein benutzerdefiniertes Skript schreiben, um dies zu deaktivieren. Beispiel: Der Name der Dropdown-Liste lautet `drpOrderedByStateProv` und wird in die Kopfzeile des Teilformulars eingeschlossen. Der Name des HTML-Eingabeelements lautet `header[0].drpOrderedByStateProv[0]`. Der Name der ausgeblendeten Felder, die die Daten der Dropdown-Liste speichern und senden, hat die folgenden Namen: `header[0].drpOrderedByStateProv_DISPLAYITEMS_[0] header[0].drpOrderedByStateProv_VALUEITEMS_[0]`

Sie können diese Eingabeelemente wie folgt deaktivieren, wenn Sie die Daten nicht posten möchten. `var __CUSTOM_SCRIPTS_VERSION = 1; //enabling the feature function _user_onsubmit() { var elems = document.getElementsByName("header[0].drpOrderedByStateProv_DISPLAYITEMS_[0]"); elems[0].disabled = true; elems = document.getElementsByName("header[0].drpOrderedByStateProv_VALUEITEMS_[0]"); elems[0].disabled = true; }`

```as3
header[0].drpOrderedByStateProv_DISPLAYITEMS_[0] header[0].drpOrderedByStateProv_VALUEITEMS_[0]
```

```as3
var __CUSTOM_SCRIPTS_VERSION = 1; //enabling the feature 
    function _user_onsubmit() { 
    var elems = document.getElementsByName("header[0].drpOrderedByStateProv_DISPLAYITEMS_[0]"); 
    elems[0].disabled = true; 
    elems = document.getElementsByName("header[0].drpOrderedByStateProv_VALUEITEMS_[0]"); 
    elems[0].disabled = true; 
    }
```

## XFA-Teilmengen {#xfa-subsets}

Beim Erstellen von Formularentwürfen, die als HTML gerendert werden sollen, müssen Sie die Skripterstellung auf die XFA-Untergruppe für Skripte in JavaScript beschränken.

Skripte, die auf dem Client ausgeführt werden oder sowohl auf dem Client als auch auf dem Server ausgeführt werden, müssen in die XFA-Untergruppe geschrieben werden. Skripte, die auf dem Server ausgeführt werden, können das vollständige XFA-Skriptmodell verwenden und auch FormCalc verwenden. Informationen zur Verwendung von JavaScript finden Sie unter [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63).

Beim Ausführen von Skripten auf dem Client kann nur das aktuelle Bedienfeld, das angezeigt wird, das Skript verwenden. Sie können beispielsweise kein Skript für Felder erstellen, die sich im Bereich A befinden, wenn Bereich B angezeigt wird. Beim Ausführen von Skripten auf dem Server können alle Bedienfelder aufgerufen werden.

Außerdem müssen Sie bei der Verwendung von SOM-Ausdrücken (Scripting Object Model) in Skripten, die auf dem Client ausgeführt werden, vorsichtig sein. Nur eine vereinfachte Untergruppe von SOM-Ausdrücken wird von Skripten unterstützt, die auf dem Client ausgeführt werden.

## Ereigniszeitpunkt {#event-timing}

Die XFA-Untergruppe definiert die XFA-Ereignisse, die HTML-Ereignissen zugeordnet sind. Es gibt einen geringfügigen Unterschied im Verhalten hinsichtlich des Timings von calculate- und validate-Ereignissen. In einem Webbrowser wird beim Beenden eines Felds ein vollständiges calculate -Ereignis ausgeführt. Berechnete Ereignisse werden nicht automatisch ausgeführt, wenn Sie einen Feldwert ändern. Sie können ein calculate -Ereignis erzwingen, indem Sie die `xfa.form.execCalculate` -Methode.

In einem Webbrowser werden Validierungs-Ereignisse nur ausgeführt, wenn ein Feld beendet oder ein Formular gesendet wird. Sie können ein validate -Ereignis erzwingen, indem Sie die `xfa.form.execValidate` -Methode.

Forms, das in einem Webbrowser angezeigt wird (im Gegensatz zu Adobe Reader oder Acrobat), entspricht dem XFA-Null-Test (Fehler oder Warnungen) für Pflichtfelder.

* Wenn der Null-Test einen Fehler erzeugt und Sie ein Feld verlassen, ohne einen Wert anzugeben, wird ein Meldungsfeld angezeigt und Sie werden nach dem Klicken auf OK zum Feld neu positioniert.
* Wenn ein Null-Test eine Warnung erzeugt und Sie ein Feld verlassen, ohne einen Wert anzugeben, werden Sie aufgefordert, entweder auf OK oder auf Abbrechen zu klicken. Dort haben Sie die Möglichkeit, den Vorgang fortzusetzen, ohne einen Wert anzugeben, oder zum Feld zurückzukehren, um einen Wert einzugeben.

Weitere Informationen zu einem Null-Test finden Sie unter [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63).

## Formularschaltflächen {#form-buttons}

Wenn Sie auf eine Senden-Schaltfläche klicken, werden Formulardaten an den Forms-Dienst gesendet und stellen das Ende der Formularverarbeitung dar. Die `preSubmit` -Ereignis auf dem Client oder Server ausgeführt werden. Die `preSubmit` -Ereignis vor der Formularübermittlung ausgeführt werden, wenn es für die Ausführung auf dem Client konfiguriert ist. Andernfalls wird die `preSubmit` -Ereignis wird während der Formularübermittlung auf dem Server ausgeführt. Weitere Informationen zum `preSubmit` -Ereignis, siehe [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63).

Wenn einer Schaltfläche kein clientseitiges Skript zugeordnet ist, werden die Daten an den Server übermittelt, die Berechnungen werden auf dem Server durchgeführt und das HTML-Formular wird neu generiert. Wenn eine Schaltfläche ein clientseitiges Skript enthält, werden keine Daten an den Server gesendet und das clientseitige Skript wird im Webbrowser ausgeführt.

## HTML 4.0-Webbrowser {#html-4-0-web-browser}

Ein Webbrowser, der nur HTML 4.0 unterstützt, kann das clientseitige Skriptmodell der XFA-Untergruppe nicht unterstützen. Beim Erstellen eines Formularentwurfs für die Verwendung sowohl in HTML 4.0 als auch in MSDHTML oder CSS2HTML wird ein Skript, das für die Ausführung auf dem Client markiert ist, tatsächlich auf dem Server ausgeführt. Angenommen, ein Benutzer klickt auf eine Schaltfläche in einem Formular, das in einem Webbrowser von HTML 4.0 angezeigt wird. In diesem Fall werden die Formulardaten an den Server gesendet, auf dem das clientseitige Skript ausgeführt wird.

Es wird empfohlen, die Formularlogik in calculate -Ereignissen zu platzieren, die auf dem Server in HTML 4.0 und auf dem Client für MSDHTML oder CSS2HTML ausgeführt werden.

## Unterbreitungsänderungen beibehalten {#maintaining-presentation-changes}

Wenn Sie zwischen HTML-Seiten (Bedienfeldern) wechseln, wird nur der Status der Daten beibehalten. Einstellungen wie die Hintergrundfarbe oder die obligatorischen Feldeinstellungen werden nicht beibehalten (wenn sie sich von den ursprünglichen Einstellungen unterscheiden). Um den Präsentationsstatus beizubehalten, müssen Sie Felder (normalerweise ausgeblendet) erstellen, die den Präsentationsstatus von Feldern darstellen. Wenn Sie ein Skript zum `Calculate` -Ereignis, das die Darstellung basierend auf versteckten Feldwerten ändert, können Sie den Präsentationsstatus beibehalten, wenn Sie zwischen HTML-Seiten (Bedienfeldern) hin- und herwechseln.

Das folgende Skript behält die `fillColor` eines auf dem Wert von `hiddenField`. Angenommen, dieses Skript befindet sich im `Calculate` -Ereignis.

```as3
     If (hiddenField.rawValue == 1) 
         this.fillColor = "255,0,0" 
     else 
         this.fillColor = "0,255,0"
```

>[!NOTE]
Statische Objekte werden nicht in einem wiedergegebenen HTML-Formular angezeigt, wenn sie in einer Tabellenzelle verschachtelt sind. Beispielsweise werden ein in einer Tabellenzelle verschachtelter Kreis und Rechteck nicht in einem Render-HTML-Formular angezeigt. Dieselben statischen Objekte werden jedoch korrekt angezeigt, wenn sie sich außerhalb der Tabelle befinden.

## HTML-Formulare digital signieren {#digitally-signing-html-forms}

Sie können kein HTML-Formular signieren, das ein digitales Signaturfeld enthält, wenn das Formular als eine der folgenden HTML-Transformationen wiedergegeben wird:

* AHTML
* HTML4
* StaticHTML
* NoScriptXHTML

Informationen zum digitalen Signieren eines Dokuments finden Sie unter [Digitales Signieren und Zertifizieren von Dokumenten](/help/forms/developing/digitally-signing-certifying-documents.md)

## Rendern eines barrierefreien, richtlinienkonformen XHTML-Formulars {#rendering-an-accessibility-guidelines-compliant-xhtml-form}

Sie können ein vollständiges HTML-Formular wiedergeben, das den Richtlinien für Barrierefreiheit entspricht. Das heißt, das Formular wird innerhalb vollständiger HTML-Tags wiedergegeben, anstatt dass das HTML-Formular innerhalb von body-Tags wiedergegeben wird (keine vollständige HTML-Seite).

## Validieren von Formulardaten {#validating-form-data}

Es wird empfohlen, die Verwendung von Validierungsregeln für Formularfelder bei der Wiedergabe des Formulars als HTML-Formular zu beschränken. Einige Validierungsregeln werden für HTML-Formulare möglicherweise nicht unterstützt. Wenn beispielsweise ein Überprüfungsmuster von MM-TT-JJJJ auf eine `Date/Time` -Feld in einem Formularentwurf, der als HTML-Formular wiedergegeben wird, nicht ordnungsgemäß funktioniert, selbst wenn das Datum richtig eingegeben wurde. Dieses Überprüfungsmuster funktioniert jedoch ordnungsgemäß für Formulare, die als PDF wiedergegeben werden.

>[!NOTE]
Weitere Informationen zum Forms-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Zusammenfassung der Schritte {#summary-of-steps}

Um ein HTML-Formular wiederzugeben, führen Sie die folgenden Schritte aus:

1. Projektdateien einschließen.
1. Erstellen Sie ein Forms Client-API-Objekt.
1. Festlegen von HTML-Laufzeitoptionen.
1. Rendern Sie ein HTML-Formular.
1. Schreiben Sie den Formular-Datenstrom in den Client-Webbrowser.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Forms Client-API-Objekts**

Bevor Sie Daten programmgesteuert in eine PDF formClient-API importieren können, müssen Sie einen Client für den Formulardatenintegrationsdienst erstellen. Beim Erstellen eines Service-Clients definieren Sie Verbindungseinstellungen, die zum Aufrufen eines Dienstes erforderlich sind.

**Festlegen von HTML-Laufzeitoptionen**

Sie legen beim Rendern eines HTML-Formulars HTML-Laufzeitoptionen fest. Beispielsweise können Sie einem HTML-Formular eine Symbolleiste hinzufügen, um Benutzern zu ermöglichen, Dateianhänge auszuwählen, die sich auf dem Clientcomputer befinden, oder Dateianlagen abzurufen, die mit dem HTML-Formular wiedergegeben werden. Standardmäßig ist eine HTML-Symbolleiste deaktiviert. Um einem HTML-Formular eine Symbolleiste hinzuzufügen, müssen Sie programmgesteuert Laufzeitoptionen festlegen. Standardmäßig besteht eine HTML-Symbolleiste aus den folgenden Schaltflächen:

* `Home`: Stellt einen Link zum Webstamm der Anwendung bereit.
* `Upload`: Bietet eine Benutzeroberfläche zum Auswählen von Dateien, die an das aktuelle Formular angehängt werden sollen.
* `Download`: Bietet eine Benutzeroberfläche zum Anzeigen der angehängten Dateien.

Wenn eine HTML-Symbolleiste auf einem HTML-Formular angezeigt wird, kann ein Benutzer maximal zehn Dateien auswählen, die zusammen mit Formulardaten gesendet werden sollen. Nachdem die Dateien übermittelt wurden, kann der Forms-Dienst die Dateien abrufen.

Beim Rendern eines Formulars als HTML können Sie einen Wert &quot;user-agent&quot;angeben. Ein Wert &quot;user-agent&quot;liefert Browser- und Systeminformationen. Dies ist ein optionaler Wert, und Sie können einen leeren Zeichenfolgenwert übergeben. Der Schnellstart zum Rendern eines HTML-Formulars mit der Java-API zeigt, wie ein Benutzeragentenwert abgerufen und zum Rendern eines Formulars als HTML verwendet wird.

HTTP-URLs, an die Formulardaten gesendet werden, können durch Festlegen der Ziel-URL mithilfe der Forms Service Client-API angegeben werden oder in der im XDP-Formularentwurf enthaltenen Senden-Schaltfläche angegeben werden. Wenn die Ziel-URL im Formularentwurf angegeben ist, legen Sie keinen Wert mithilfe der Forms Service Client-API fest.

>[!NOTE]
Die Wiedergabe eines HTML-Formulars mit einer Symbolleiste ist optional.

>[!NOTE]
Wenn Sie ein AHTML-Formular wiedergeben, wird empfohlen, keine Symbolleiste zum Formular hinzuzufügen.

**Rendern eines HTML-Formulars**

Um ein HTML-Formular wiederzugeben, müssen Sie einen Formularentwurf angeben, der in Designer erstellt und als XDP-Datei gespeichert wurde. Sie müssen auch einen HTML-Transformationstyp auswählen. Sie können beispielsweise den Transformationstyp HTML angeben, der eine dynamische HTML für Internet Explorer 5.0 oder höher rendert.

Für die Wiedergabe eines HTML-Formulars sind auch Werte erforderlich, z. B. URI-Werte, die zum Rendern anderer Formulartypen erforderlich sind.

**Schreiben Sie den Formulardaten-Stream in den Client-Webbrowser**

Wenn der Forms-Dienst ein HTML-Formular rendert, wird ein Formulardatenstream zurückgegeben, den Sie in den Client-Webbrowser schreiben müssen. Beim Schreiben in den Client-Webbrowser ist das HTML-Formular für den Benutzer sichtbar.

**Siehe auch**

[Wiedergabe eines Formulars als HTML mithilfe der Java-API](#render-a-form-as-html-using-the-java-api)

[Wiedergabe eines Formulars als HTML mithilfe der Webdienst-API](#render-a-form-as-html-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Forms Service-API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Rendern interaktiver PDF forms](/help/forms/developing/rendering-interactive-pdf-forms.md)

[Rendern von HTML Forms mit benutzerdefinierten Symbolleisten](/help/forms/developing/rendering-html-forms-custom-toolbars.md)

[Erstellen von Webanwendungen, die Forms rendern](/help/forms/developing/creating-web-applications-renders-forms.md)

## Wiedergabe eines Formulars als HTML mithilfe der Java-API {#render-a-form-as-html-using-the-java-api}

Rendern Sie ein HTML-Formular mithilfe der Forms-API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-forms-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Forms Client-API-Objekts

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie eine `FormsServiceClient` -Objekt durch Verwendung seines Konstruktors und Übergabe des `ServiceClientFactory` -Objekt.

1. Festlegen von HTML-Laufzeitoptionen

   * Erstellen Sie eine `HTMLRenderSpec` -Objekt durch Verwendung seines -Konstruktors.
   * Um ein HTML-Formular mit einer Symbolleiste wiederzugeben, rufen Sie die `HTMLRenderSpec` -Objekt `setHTMLToolbar` -Methode und übergeben Sie eine `HTMLToolbar` enum -Wert. Um beispielsweise eine vertikale HTML-Symbolleiste anzuzeigen, übergeben Sie `HTMLToolbar.Vertical`.
   * Um den Gebietsschemawert für das HTML-Formular festzulegen, rufen Sie die `HTMLRenderSpec` -Objekt `setLocale` -Methode verwenden und einen string -Wert übergeben, der den Gebietsschema-Wert angibt. (Dies ist eine optionale Einstellung.)
   * Um das HTML-Formular mit vollständigen HTML-Tags wiederzugeben, rufen Sie die `HTMLRenderSpec` -Objekt `setOutputType` -Methode und -übergabe `OutputType.FullHTMLTags`. (Dies ist eine optionale Einstellung.)

   >[!NOTE]
   Forms wird beim HTML nicht erfolgreich gerendert, wenn die `StandAlone` Option ist `true` und `ApplicationWebRoot` verweist auf einen anderen Server als den J2EE-Anwendungsserver, der als Host für AEM Forms dient (die `ApplicationWebRoot` -Wert wird mithilfe der `URLSpec` -Objekt, das an die `FormsServiceClient` -Objekt `(Deprecated) renderHTMLForm` -Methode). Wenn die `ApplicationWebRoot`* ein anderer Server ist, der als Host für AEM Forms dient, muss der Wert des Webstamm-URI in der Administration Console als URI-Wert für die Webanwendung des Formulars festgelegt werden. Dazu können Sie sich bei Administration Console anmelden, auf Dienste > Forms klicken und den Web-Stamm-URI auf https://server-name:port/FormServer setzen. Speichern Sie dann Ihre Einstellungen.*

1. Rendern eines HTML-Formulars

   Rufen Sie die `FormsServiceClient` -Objekt `(Deprecated) renderHTMLForm` -Methode verwenden und die folgenden Werte übergeben:

   * Ein string -Wert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil einer Forms-Anwendung ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * A `TransformTo` enum -Wert, der den Präferenztyp für HTML angibt. Um beispielsweise ein HTML-Formular wiederzugeben, das mit dynamischem HTML für Internet Explorer 5.0 oder höher kompatibel ist, geben Sie `TransformTo.MSDHTML`.
   * A `com.adobe.idp.Document` -Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie einen leeren `com.adobe.idp.Document` -Objekt.
   * Die `HTMLRenderSpec` -Objekt, das HTML-Laufzeitoptionen speichert.
   * Ein string -Wert, der die `HTTP_USER_AGENT` Header-Wert; Beispiel: `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`.
   * A `URLSpec` -Objekt, das URI-Werte speichert, die zum Rendern eines HTML-Formulars erforderlich sind.
   * A `java.util.HashMap` -Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter, den Sie `null` , wenn Sie keine Dateien an das Formular anhängen möchten.

   Die `(Deprecated) renderHTMLForm` -Methode gibt eine `FormsResult` -Objekt, das einen Formulardatenstrom enthält, der in den Client-Webbrowser geschrieben werden kann.

1. Schreiben Sie den Formulardaten-Stream in den Client-Webbrowser

   * Erstellen Sie eine `com.adobe.idp.Document` -Objekt durch Aufrufen der `FormsResult` object ‘s `getOutputContent` -Methode.
   * Abrufen des Inhaltstyps der `com.adobe.idp.Document` -Objekt durch Aufrufen seiner `getContentType` -Methode.
   * Legen Sie die `javax.servlet.http.HttpServletResponse` Inhaltstyp des Objekts durch Aufrufen seiner `setContentType` -Methode und Übergabe des Inhaltstyps der `com.adobe.idp.Document` -Objekt.
   * Erstellen Sie eine `javax.servlet.ServletOutputStream` -Objekt, das zum Schreiben des Formulardaten-Streams in den Client-Webbrowser durch Aufrufen der `javax.servlet.http.HttpServletResponse` -Objekt `getOutputStream` -Methode.
   * Erstellen Sie eine `java.io.InputStream` -Objekt durch Aufrufen der `com.adobe.idp.Document` -Objekt `getInputStream` -Methode.
   * Erstellen Sie ein Byte-Array und füllen Sie es mit dem Formulardatenstream, indem Sie die `InputStream` -Objekt `read` -Methode verwenden und das Byte-Array als Argument übergeben.
   * Rufen Sie die `javax.servlet.ServletOutputStream` -Objekt `write` -Methode zum Senden des Formulardaten-Streams an den Client-Webbrowser. Übergeben Sie das Byte-Array an die `write` -Methode.

**Siehe auch**

[Rendern von Forms als HTML](#rendering-forms-as-html)

[Schnellstart (SOAP-Modus): Rendern eines HTML-Formulars mit der Java-API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-an-html-form-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Wiedergabe eines Formulars als HTML mithilfe der Webdienst-API {#render-a-form-as-html-using-the-web-service-api}

Rendern Sie ein HTML-Formular mithilfe der Forms-API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie Java-Proxyklassen, die die Forms-Dienst-WSDL verwenden.
   * Schließen Sie die Java-Proxy-Klassen in Ihren Klassenpfad ein.

1. Erstellen eines Forms Client-API-Objekts

   Erstellen Sie eine `FormsService` Objekt und legen Sie Authentifizierungswerte fest.

1. Festlegen von HTML-Laufzeitoptionen

   * Erstellen Sie eine `HTMLRenderSpec` -Objekt durch Verwendung seines -Konstruktors.
   * Um ein HTML-Formular mit einer Symbolleiste wiederzugeben, rufen Sie die `HTMLRenderSpec` -Objekt `setHTMLToolbar` -Methode und übergeben Sie eine `HTMLToolbar` enum -Wert. Um beispielsweise eine vertikale HTML-Symbolleiste anzuzeigen, übergeben Sie `HTMLToolbar.Vertical`.
   * Um den Gebietsschemawert für das HTML-Formular festzulegen, rufen Sie die `HTMLRenderSpec` -Objekt `setLocale` -Methode verwenden und einen string -Wert übergeben, der den Gebietsschema-Wert angibt. Weitere Informationen finden Sie unter [AEM Forms API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).
   * Um das HTML-Formular mit vollständigen HTML-Tags wiederzugeben, rufen Sie die `HTMLRenderSpec` -Objekt `setOutputType` -Methode und -übergabe `OutputType.FullHTMLTags`.

   >[!NOTE]
   Forms wird beim HTML nicht erfolgreich gerendert, wenn die `StandAlone` Option ist `true` und `ApplicationWebRoot` verweist auf einen anderen Server als den J2EE-Anwendungsserver, der als Host für AEM Forms dient (die `ApplicationWebRoot` -Wert wird mithilfe der `URLSpec` -Objekt, das an die `FormsServiceClient` -Objekt `(Deprecated) renderHTMLForm` -Methode). Wenn die `ApplicationWebRoot`* ein anderer Server ist, der als Host für AEM Forms dient, muss der Wert des Webstamm-URI in der Administration Console als URI-Wert für die Webanwendung des Formulars festgelegt werden. Dazu können Sie sich bei Administration Console anmelden, auf Dienste > Forms klicken und den Web-Stamm-URI auf https://server-name:port/FormServer setzen. Speichern Sie dann Ihre Einstellungen. *

1. Rendern eines HTML-Formulars

   Rufen Sie die `FormsService` -Objekt `(Deprecated) renderHTMLForm` -Methode verwenden und die folgenden Werte übergeben:

   * Ein string -Wert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil einer Forms-Anwendung ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * A `TransformTo` enum -Wert, der den Präferenztyp für HTML angibt. Um beispielsweise ein HTML-Formular wiederzugeben, das mit dynamischem HTML für Internet Explorer 5.0 oder höher kompatibel ist, geben Sie `TransformTo.MSDHTML`.
   * A `BLOB` -Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie `null`. (Siehe [Vorausfüllen von Forms mit flexiblen Layouts](/help/forms/developing/prepopulating-forms-flowable-layouts.md#prepopulating-forms-with-flowable-layouts).
   * Die `HTMLRenderSpec` -Objekt, das HTML-Laufzeitoptionen speichert.
   * Ein string -Wert, der die `HTTP_USER_AGENT` Header-Wert; Beispiel: `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`. Wenn Sie diesen Wert nicht festlegen möchten, können Sie eine leere Zeichenfolge übergeben.
   * A `URLSpec` -Objekt, das URI-Werte speichert, die zum Rendern eines HTML-Formulars erforderlich sind. (Siehe [URI-Werte angeben](/help/forms/developing/rendering-interactive-pdf-forms.md).
   * A `java.util.HashMap` -Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter, den Sie `null` , wenn Sie keine Dateien an das Formular anhängen möchten. (Siehe [Anhängen von Dateien an das Formular](/help/forms/developing/rendering-interactive-pdf-forms.md).
   * Ein leeres `com.adobe.idp.services.holders.BLOBHolder` -Objekt, das von der -Methode aufgefüllt wird. Dieser Parameterwert speichert das wiedergegebene Formular.
   * Ein leeres `com.adobe.idp.services.holders.BLOBHolder` -Objekt, das von der -Methode aufgefüllt wird. Dieser Parameter speichert die XML-Ausgabedaten.
   * Ein leeres `javax.xml.rpc.holders.LongHolder` -Objekt, das von der -Methode aufgefüllt wird. Dieses Argument speichert die Anzahl der Seiten im Formular.
   * Ein leeres `javax.xml.rpc.holders.StringHolder` -Objekt, das von der -Methode aufgefüllt wird. Dieses Argument speichert den Gebietsschemawert.
   * Ein leeres `javax.xml.rpc.holders.StringHolder` -Objekt, das von der -Methode aufgefüllt wird. Dieses Argument speichert den verwendeten HTML-Rendering-Wert.
   * Ein leeres `com.adobe.idp.services.holders.FormsResultHolder` -Objekt, das die Ergebnisse dieses Vorgangs enthält.

   Die `(Deprecated) renderHTMLForm` -Methode füllt die `com.adobe.idp.services.holders.FormsResultHolder` -Objekt, das als letzter Argumentwert mit einem Formulardatenstream übergeben wird, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben Sie den Formulardaten-Stream in den Client-Webbrowser

   * Erstellen Sie eine `FormResult` -Objekt durch Abrufen des Werts der `com.adobe.idp.services.holders.FormsResultHolder` -Objekt `value` Datenelement.
   * Erstellen Sie eine `BLOB` -Objekt, das Formulardaten enthält, durch Aufrufen der `FormsResult` -Objekt `getOutputContent` -Methode.
   * Abrufen des Inhaltstyps der `BLOB` -Objekt durch Aufrufen seiner `getContentType` -Methode.
   * Legen Sie die `javax.servlet.http.HttpServletResponse` Inhaltstyp des Objekts durch Aufrufen seiner `setContentType` -Methode und Übergabe des Inhaltstyps der `BLOB` -Objekt.
   * Erstellen Sie eine `javax.servlet.ServletOutputStream` -Objekt, das zum Schreiben des Formulardaten-Streams in den Client-Webbrowser durch Aufrufen der `javax.servlet.http.HttpServletResponse` -Objekt `getOutputStream` -Methode.
   * Erstellen Sie ein Byte-Array und füllen Sie es durch Aufrufen der `BLOB` -Objekt `getBinaryData` -Methode. Diese Aufgabe weist den Inhalt des `FormsResult` -Objekt zum Byte-Array hinzu.
   * Rufen Sie die `javax.servlet.http.HttpServletResponse` -Objekt `write` -Methode zum Senden des Formulardaten-Streams an den Client-Webbrowser. Übergeben Sie das Byte-Array an die `write` -Methode.

**Siehe auch**

[Rendern von Forms als HTML](#rendering-forms-as-html)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
