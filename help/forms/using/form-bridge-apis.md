---
title: Form Bridge APIs für HTML5-Formulare
seo-title: Form Bridge APIs for HTML5 forms
description: Externe Anwendungen verwenden die FormBridge-APIs, um eine Verbindung mit dem XFA Mobile Form herzustellen. Die API löst ein FormBridgeInitialized-Ereignis auf dem übergeordneten Fenster aus.
seo-description: External applications use the FormBridge API to connect to the XFA Mobile Form. The API dispatches a FormBridgeInitialized event on the parent window.
uuid: 0db22649-522b-4857-9ffd-826c52381d15
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: developer-reference
discoiquuid: c05c9911-7c49-4342-89de-61b8b9953c83
exl-id: ad669f3b-2bda-4c41-8032-cf25a192ce12
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '939'
ht-degree: 40%

---

# Form Bridge APIs für HTML5-Formulare {#form-bridge-apis-for-html-forms}

Sie können die Form Bridge-APIs verwenden, um einen Kommunikationskanal zwischen XFA-basierten HTML5-Formularen und Ihren Anwendungen zu öffnen. Die Form Bridge-APIs bieten eine **connect** API zum Erstellen der Verbindung.

Die **Verbindungs**-API akzeptiert einen Handler als ein Argument. Nachdem eine erfolgreiche Verbindung zwischen XFA-basiertem HTML5-Formular und Form Bridge erstellt wurde, wird der Handle aufgerufen.

Sie können den folgenden Beispielcode verwenden, um die Verbindung zu erstellen.

```
// Example showing how to connect to FormBridge
window.addEventListener("FormBridgeInitialized",
                                function(event) {
                                    var fb = event.detail.formBridge;
                                    fb.connect(function() {
                                           //use form bridge functions 
                         })
                            })
```

>[!NOTE]
>
>Stellen Sie sicher, dass Sie eine Verbindung erstellen, bevor Sie die formRuntime.jsp-Datei einbeziehen.

## Verfügbare Form Bridge-API  {#available-form-bridge-api-nbsp}

**getBridgeVersion()**

Gibt die Versionsnummer der Skriptbibliothek zurück.

* **Eingabe:** keine
* **Ausgabe**: Versionsnummer der Skriptbibliothek
* **Fehler:** keine

**isConnected()** Prüft, ob der Formularstatus initialisiert wurde

* **Eingabe:** keine
* **Ausgabe**: **True** , wenn der XFA-Formularstatus initialisiert wurde

* **Fehler:** keine

**connect(handler, context)** Stellt eine Verbindung zu FormBridge her und führt die Funktion aus, nachdem die Verbindung hergestellt und der Formularstatus initialisiert wurde.

* **Eingabe**:

   * **handler:** Funktion, die ausgeführt wird, wenn Form Bridge verbunden ist.
   * **context**: Das Objekt, auf das der Kontext (dies) der *handler *function festgelegt wird.

* **Ausgabe:** keine
* **Fehler:** keine

**getDataXML(options)** Gibt die aktuellen Formulardaten im XML-Format aus

* **Eingabe:**

   * **options:** JavaScript-Objekt, das die folgenden Eigenschaften enthält:

      * **Error:** Fehlerhandler-Funktion
      * **success:** Erfolgshandler-Funktion. Diese Funktion wird an ein Objekt übergeben, das XML in der *data*-Eigenschaft enthält.
      * **context:** Das Objekt, auf das der Kontext (dies) der *success*-Funktion festgelegt wird.
      * **validationChecker**: Funktion zum Aufrufen, um Überprüfungsfehler zu überprüfen, die vom Server empfangen wurden. Der Überprüfungsfunktion wird ein Array von Fehlerstrings übergeben.
      * **formState**: Der JSON-Status des XFA-Formulars, für das Daten-XML zurückgegeben werden muss. Wenn nicht anders angegeben, wird Daten-XML für das aktuell gerenderte Formular zurückgegeben.

* **Ausgabe:** keine
* **Fehler:** keine

**registerConfig(configName, config)** Registriert Benutzer-/Portal-spezifische Konfigurationen mit FormBridge. Diese Konfigurationen überschreiben die Standardkonfigurationen. Die unterstützten Konfigurationen sind im Abschnitt „config“ angegeben.

* **Eingabe:**

   * **configName:** Name der zu überschreibenden Konfiguration

      * **widgetConfig:** Ermöglicht dem Benutzer, die Standard-Widgets im Formular mit benutzerdefinierten Widgets zu überschreiben. Die Konfiguration wird überschrieben wie folgt:

         formBridge.registerConfig(&quot;widgetConfig&quot;:{/&amp;ast;configuration&amp;ast;/})

      * **pagingConfig:** Ermöglicht dem Benutzer, das Standardverhalten zu überschreiben, bei dem nur die erste Seite gerendert wird. Die Konfiguration wird überschrieben wie folgt:

         window.formBridge.registerConfig(&quot;pagingConfig&quot;:{pagingDisabled: &lt;true | false>, shrinkPageDisabled: &lt;true | false> }).

      * **LoggingConfig:** Ermöglicht dem Benutzer, die Protokollierungsstufe zu überschreiben, die Protokollierung für eine Kategorie zu deaktivieren oder festzulegen, ob die Protokollkonsole angezeigt oder an den Server gesendet werden soll. Die Konfiguration kann überschrieben werden wie folgt:

      ```css
      formBridge.registerConfig{  
        "LoggerConfig" : {  
      {  
      "on":`<true *| *false>`,  
      "category":`<array of categories>`,  
      "level":`<level of categories>`, "  
      type":`<"console"/"server"/"both">`  
          }  
        }
      ```

      * **SubmitServiceProxyConfig:** Erlauben Sie Benutzern, die Proxy-Dienste für Übermittlung und Protokollierung zu registrieren.

         ```css
         window.formBridge.registerConfig("submitServiceProxyConfig",  
         {  
         "submitServiceProxy" : "`<submitServiceProxy>`",  
         "logServiceProxy": "`<logServiceProxy>`",  
         "submitUrl" : "`<submitUrl>`"  
         });
         ```
   * **config:** Wert der Konfiguration



* **Ausgabe:** Objekt, das den ursprünglichen Wert der Konfiguration in der *data*-Eigenschaft enthält.

* **Fehler:** keine

**hideFields(fieldArray)** Blendet die Felder aus, deren SOM-Ausdrücke im fieldArray bereitgestellt werden. Setzt diepresence-Eigenschaft der angegebenen Felder auf invisible

* **Eingabe:**

   * **fieldArray:** Array von SOM-Ausdrücken für die auszublendenden Felder

* **Ausgabe:** keine
* **Fehler:** keine

**showFields(fieldArray)** Zeigt die Felder an, deren SOM-Ausdrücke im fieldArray bereitgestellt werden. Setzt diepresence-Eigenschaft der angegebenen Felder auf visible

* **Eingabe:**

   * **fieldArray:** Array von SOM-Ausdrücken für die anzuzeigenden Felder

* **Ausgabe:** keine
* **Fehler:** keine

**hideSubmitButtons()** Blendet alle Senden-Schaltflächen im Formular aus

* **Eingabe:** keine
* **Ausgabe:** keine
* **Fehler:** Gibt einen Ausnahmefehler aus, wenn Formularstatus nicht initialisiert wurde.

**getFormState()** Gibt die JSON-Datei aus, die den Formularstatus darstellt

* **Eingabe:** keine
* **Ausgabe:** Objekt, das JSON enthält, das den aktuellen Formularstatus in *data* -Eigenschaft.

* **Fehler:** keine

**restoreFormState(options)** Stellt den Formularstatus im bereitgestellten JSON-Status im Optionsobjekt wieder her. Der Status wird angewendet und Erfolgs- oder Fehlerhandler werden aufgerufen, nachdem der Vorgang ist abgeschlossen ist.

* **Eingabe:**

   * **Optionen:** JavaScript-Objekt, das die folgenden Eigenschaften enthält:

      * **Error:** Fehlerhandler-Funktion
      * **success:** Erfolgshandler-Funktion
      * **context**: Das Objekt, dem der Kontext (dies) des *success* -Funktion festgelegt
      * **formState:** JSON-Status des Formulars. Das Formular wird im JSON-Status wiederhergestellt.

* **Ausgabe:** keine
* **Fehler:** keine

**setFocus (som)** Legt den Fokus auf das im SOM-Ausdruck angegebene Feld

* **Eingabe:** SOM-Ausdruck des Felds, auf das der Fokus gesetzt werden soll
* **Ausgabe:** keine
* **Fehler:** Gibt im Fall eines falschen SOM-Ausdrucks einen Ausnahmefehler aus.

**setFieldValue (som, value)** Legt den Wert der Felder für die angegebenen SOM-Ausdrücke fest

* **Eingabe:**

   * **som:** Array, das SOM-Ausdrücke des Felds enthält. Der SOM-Ausdruck, der den Wert der Felder festlegt.
   * **Wert:** Array mit Werten, die den in einer **som** Array. Wenn der Datentyp des Werts nicht mit fieldType übereinstimmt, wird der Wert nicht geändert.

* **Ausgabe:** keine
* **Fehler:** Löst im Fall eines falschen SOM-Ausdrucks eine Ausnahme aus

**getFieldValue (som)** Gibt den Wert der Felder für die angegebenen SOM-Ausdrücke aus

* **Eingabe:** Array mit SOM-Ausdrücken der Felder, deren Wert abgerufen werden soll
* **Ausgabe:** Objekt, das das Ergebnis als Array in **data** -Eigenschaft.

* **Fehler:** keine

### Beispiel für API „getFieldValue()“ {#example-of-nbsp-getfieldvalue-api}

```JavaScript
var a =  formBridge.getFieldValue(“xfa.form.form1.Subform1.TextField”);
if(a.errors) {
    var err;
     while((err = a.getNextMessage()) != null)
               alert(a.message)
} else {
   alert(a.data[0]) 
}
```

**getFieldProperties(som, property)** Rufen Sie die Liste der Werte für die angegebene Eigenschaft der in SOM-Ausdrücken angegebenen Felder ab.

* **Eingabe:**

   * **som:** Array, das SOM-Ausdrücke für die Felder enthält.
   * **property:** Name der Eigenschaft, deren Wert erforderlich ist.

* **Ausgabe:** Objekt, das das Ergebnis als Array in *data *property enthält

* **Fehler:** keine

**setFieldProperties(som, property, values)** Legt den Wert der angegebenen Eigenschaft für alle in den SOM-Ausdrücken angegebenen Felder fest

* **Eingabe:**

   * **som:** Array mit SOM-Ausdrücken der Felder, deren Wert festgelegt werden muss
   * **property:** Eigenschaft, deren Wert festgelegt werden soll.
   * **Wert:** Array, das die Werte der angegebenen Eigenschaft für die in SOM-Ausdrücken angegebenen Felder enthält

* **Ausgabe:** keine
* **Fehler:** keine

## Beispielverwendung der Form Bridge-API: {#sample-usage-of-form-bridge-api}

```JavaScript
// Example 1: FormBridge.restoreFormState
  function loadFormState() {
    var suc = function(obj) {
             //success
            }
    var err = function(obj) {
           while(var t = obj.getNextMessage()) {
         $("#errorDiv").append("<div>"+t.message+"</div>");
           }
           }
        var _formState = // load form state from storage
    formBridge.restoreFormState({success:suc,error:err,formState:_formState}); // not passing a context means that this will be formBridge itself. Validation errors will be checked.
  }

//--------------------------------------------------------------------------------------------------

//Example 2: FormBridge.submitForm
  function SubmitForm() {
    var suc = function(obj) {
             var data = obj.data;
         // submit the data to a url;
            }
    var err = function(obj) {
           while(var t = obj.getNextMessage()) {
         $("#errorDiv").append("<div>"+t.message+"</div>");
           }
           }
    formBridge.submitForm({success:suc,error:err}); // not passing a context means that this will be formBridge itself. Validation errors will be checked.
  }
```
