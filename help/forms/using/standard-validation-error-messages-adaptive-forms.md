---
title: Standardmäßige Validierungsfehlermeldungen für adaptive Formulare
seo-title: Standard validation error messages for adaptive forms
description: Konvertieren der Überprüfungsfehlermeldungen für adaptive Formulare in das Standardformat mithilfe von benutzerdefinierten Fehler-Handlern
seo-description: Transform the validation error messages for adaptive forms into standard format using custom error handlers
uuid: 0d1f9835-3e28-41d3-a3b1-e36d95384328
contentOwner: anujkapo
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_managing_domains
discoiquuid: ec062567-1c6b-497b-a1e7-1dbac2d60852
feature: Adaptive Forms
exl-id: 864e6b0d-178b-4b91-85d3-34b90e999ee3
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1108'
ht-degree: 10%

---

# Standardmäßige Validierungsfehlermeldungen für adaptive Formulare {#standard-validation-error-messages}

Adaptive Formulare validieren die Eingaben, die Sie in Feldern bereitstellen, basierend auf vordefinierten Validierungskriterien. Die Validierungskriterien beziehen sich auf die zulässigen Eingabewerte für Felder in einem adaptiven Formular. Sie können die Validierungskriterien auf Grundlage der Datenquelle festlegen, die Sie mit dem adaptiven Formular verwenden. Wenn Sie beispielsweise RESTful-Webdienste als Datenquelle verwenden, können Sie die Validierungskriterien in einer Swagger-Definitionsdatei definieren.

Wenn die Eingabewerte die Validierungskriterien erfüllen, werden die Werte an die Datenquelle gesendet. Andernfalls zeigt das adaptive Formular eine Fehlermeldung an.

Ähnlich wie dieser Ansatz können adaptive Formulare jetzt in benutzerdefinierte Dienste integriert werden, um Datenvalidierungen durchzuführen. Wenn die eingegebenen Werte die Validierungskriterien nicht erfüllen und die vom Server zurückgegebene Validierungsfehlermeldung im standardmäßigen Nachrichtenformat vorliegt, werden die Fehlermeldungen auf Feldebene im Formular angezeigt.

Wenn die Eingabewerte die Validierungskriterien nicht erfüllen und die Fehlermeldung bei der Servervalidierung nicht im standardmäßigen Nachrichtenformat vorliegt, bieten die adaptiven Formulare einen Mechanismus, um die Validierungsfehlermeldungen in ein Standardformat umzuwandeln, sodass sie auf Feldebene im Formular angezeigt werden. Sie können die Fehlermeldung mit einer der beiden folgenden Methoden in das Standardformat umwandeln:

* Hinzufügen eines benutzerdefinierten Fehler-Handlers bei der Übermittlung des adaptiven Formulars
* Fügen Sie mithilfe des Regeleditors einen benutzerdefinierten Handler zur Aktion &quot;Dienst aufrufen&quot;hinzu

In diesem Artikel werden das Standardformat für die Validierungsfehlermeldungen und die Anweisungen zum Konvertieren der Fehlermeldungen von einer benutzerdefinierten in das Standardformat beschrieben.

## Standardmäßige Validierungsfehlermeldung {#standard-validation-message-format}

Die adaptiven Formulare zeigen die Fehler auf Feldebene an, wenn die Fehlermeldungen bei der Servervalidierung im folgenden Standardformat vorliegen:

```javascript
   {
    errorCausedBy : "SERVER_SIDE_VALIDATION/SERVICE_INVOCATION_FAILURE"
    errors : [
        {
             somExpression  : <somexpr>
             errorMessage / errorMessages : <validationMsg> / [<validationMsg>, <validationMsg>]

        }
    ]
    originCode : <target error Code>
    originMessage : <unstructured error message returned by service>
}
```

Dabei gilt:

* `errorCausedBy` beschreibt den Grund für das Fehlschlagen
* `errors` den SOM-Ausdruck der Felder, die die Validierungskriterien nicht erfüllt haben, zusammen mit der Validierungsfehlermeldung erwähnen
* `originCode` enthält den vom externen Dienst zurückgegebenen Fehlercode
* `originMessage` enthält die vom externen Dienst zurückgegebenen rohen Fehlerdaten

## Konfigurieren der Übermittlung adaptiver Formulare zum Hinzufügen benutzerdefinierter Handler {#configure-adaptive-form-submission}

Wenn die Fehlermeldung zur Servervalidierung nicht im Standardformat angezeigt wird, können Sie die asynchrone Übermittlung aktivieren und einen benutzerdefinierten Fehler-Handler bei der Übermittlung des adaptiven Formulars hinzufügen, um die Nachricht in ein Standardformat zu konvertieren.

### Konfigurieren der asynchronen Übermittlung adaptiver Formulare {#configure-asynchronous-adaptive-form-submission}

Bevor Sie einen benutzerdefinierten Handler hinzufügen, müssen Sie das adaptive Formular für die asynchrone Übermittlung konfigurieren. Führen Sie die folgenden Schritte aus:

1. Wählen Sie im Authoring-Modus des adaptiven Formulars das Formularcontainer-Objekt aus und tippen Sie auf ![Eigenschaften adaptiver Formulare](assets/configure_icon.png) , um seine Eigenschaften zu öffnen.
1. Aktivieren Sie im Eigenschaftenbereich **[!UICONTROL Übermittlung]** die Option **[!UICONTROL Asynchrone Übermittlung verwenden]**.
1. Auswählen **[!UICONTROL Auf dem Server erneut überprüfen]** , um die Eingabefeldwerte auf dem Server vor der Übermittlung zu überprüfen.
1. Wählen Sie die Sendeaktion aus:

   * Auswählen **[!UICONTROL Senden mit Formulardatenmodell]** und wählen Sie das entsprechende Datenmodell aus, wenn Sie RESTful-Webdienst-basiert verwenden [Formulardatenmodell](work-with-form-data-model.md) als Datenquelle.
   * Auswählen **[!UICONTROL An REST-Endpunkt übermitteln]** und geben Sie die **[!UICONTROL Umleitungs-URL/Pfad]**, wenn Sie RESTful-Webdienste als Datenquelle verwenden.

   ![Eigenschaften für die Übermittlung adaptiver Formulare](assets/af_submission_properties.png)

1. Tippen Sie auf ![Speichern](assets/save_icon.png), um die Eigenschaften zu speichern.

### Hinzufügen eines benutzerdefinierten Fehler-Handlers bei der Übermittlung des adaptiven Formulars {#add-custom-error-handler-af-submission}

AEM Forms bietet standardmäßig Handler zur Verarbeitung von erfolgreichen und fehlgeschlagenen Formularübermittlungen an. Handler sind clientseitige Funktionen, die anhand der Serverantwort ausgeführt werden. Wenn ein Formular übermittelt wird, werden die Daten zur Validierung an den Server gesendet, der eine Antwort mit Informationen über den Erfolg oder das Fehlschlagen der Übermittlung an den Client zurücksendet. Die Informationen werden als Parameter an den relevanten Handler übergeben, um die Funktion auszuführen.

Führen Sie die folgenden Schritte aus, um beim Senden des adaptiven Formulars einen benutzerdefinierten Fehler-Handler hinzuzufügen:

1. Öffnen Sie das adaptive Formular im Authoring-Modus, wählen Sie ein beliebiges Formularobjekt aus und tippen Sie auf <!--![Rule Editor](assets/af_edit_rules.png)--> , um den Regeleditor zu öffnen.
1. Wählen Sie **[!UICONTROL Formular]** in der Struktur „Formularobjekte“ und tippen Sie auf **[!UICONTROL Erstellen]**.
1. Auswählen **[!UICONTROL Fehler bei Übermittlung]** aus der Dropdown-Liste Ereignis aus.
1. Erstellen Sie eine Regel, um die benutzerdefinierte Fehlerstruktur in die Standardfehlerstruktur zu konvertieren, und tippen Sie auf **[!UICONTROL Fertig]** , um die Regel zu speichern.

Im Folgenden finden Sie einen Beispielcode zum Konvertieren einer benutzerdefinierten Fehlerstruktur in die standardmäßige Fehlerstruktur:

```javascript
var data = $event.data;
var som_map = {
    "id": "guide[0].guide1[0].guideRootPanel[0].Pet[0].id_1[0]",
    "name": "guide[0].guide1[0].guideRootPanel[0].Pet[0].name_2[0]",
    "status": "guide[0].guide1[0].guideRootPanel[0].Pet[0].status[0]"
};

var errorJson = {};
errorJson.errors = [];

if (data) {
    if (data.originMessage) {
        var errorData;
        try {
            errorData = JSON.parse(data.originMessage);
        } catch (err) {
            // not in json format
        }

        if (errorData) {
            Object.keys(errorData).forEach(function(key) {
                var som_key = som_map[key];
                if (som_key) {
                    var error = {};
                    error.somExpression = som_key;
                    error.errorMessage = errorData[key];
                    errorJson.errors.push(error);
                }
            });
        }
        window.guideBridge.handleServerValidationError(errorJson);
    } else {
        window.guideBridge.handleServerValidationError(data);
    }
}
```

Die `var som_map` listet den SOM-Ausdruck der adaptiven Formularfelder auf, die in das Standardformat umgewandelt werden sollen. Sie können den SOM-Ausdruck eines beliebigen Felds in einem adaptiven Formular anzeigen, indem Sie auf das Feld tippen und **[!UICONTROL SOM-Ausdruck anzeigen]**.

Mit diesem benutzerdefinierten Fehler-Handler konvertiert das adaptive Formular die in `var som_map` zum standardmäßigen Fehlermeldungsformat. Daher werden die Überprüfungsfehlermeldungen auf Feldebene im adaptiven Formular angezeigt.

## Hinzufügen eines benutzerdefinierten Handlers mit der Aktion &quot;Dienst aufrufen&quot;

Führen Sie die folgenden Schritte aus, um einen Fehler-Handler hinzuzufügen, um eine benutzerdefinierte Fehlerstruktur in die Standardfehlerstruktur zu konvertieren, indem Sie [Regel-Editor](rule-editor.md) Dienstaktion aufrufen:

1. Öffnen Sie das adaptive Formular im Authoring-Modus, wählen Sie ein beliebiges Formularobjekt aus und tippen Sie auf ![Regeleditor](assets/rule_editor_icon.png) , um den Regeleditor zu öffnen.
1. Tippen Sie auf **[!UICONTROL Erstellen]**.
1. Erstellen Sie eine Bedingung im **[!UICONTROL Wann]** -Abschnitt der Regel. Beispiel: Wenn[Feldname] geändert. Auswählen **[!UICONTROL geändert]** von **[!UICONTROL Status auswählen]** Dropdown-Liste, um diese Bedingung zu erfüllen.
1. Im Abschnitt **[!UICONTROL Dann]** wählen Sie **[!UICONTROL Dienst aufrufen]** aus der Dropdown-Liste **[!UICONTROL Aktion auswählen.]**
1. Wählen Sie einen Post-Dienst und die zugehörigen Datenbindungen aus dem **[!UICONTROL Eingabe]** Abschnitt. Wenn Sie beispielsweise **Name**, **ID** und **Status** -Felder im adaptiven Formular, wählen Sie einen Post-Dienst (Tier) aus und wählen Sie &quot;pet.name&quot;, &quot;pet.id&quot;und &quot;pet.status&quot;im **[!UICONTROL Eingabe]** Abschnitt.

Die aus dieser Regel resultierenden Werte, für die Sie **Name**, **ID** und **Status** werden validiert, sobald das in Schritt 2 definierte Feld geändert wird und Sie das Feld im Formular verlassen.

1. Auswählen **[!UICONTROL Code-Editor]** aus der Dropdown-Liste der Modusauswahl.
1. Tippen **[!UICONTROL Code bearbeiten]**.
1. Löschen Sie die folgende Zeile aus dem vorhandenen Code:

   ```javascript
   guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs);
   ```

1. Erstellen Sie eine Regel, um die benutzerdefinierte Fehlerstruktur in die Standardfehlerstruktur zu konvertieren, und tippen Sie auf **[!UICONTROL Fertig]** , um die Regel zu speichern.
Fügen Sie beispielsweise den folgenden Beispielcode am Ende hinzu, um eine benutzerdefinierte Fehlerstruktur in die standardmäßige Fehlerstruktur zu konvertieren:

   ```javascript
   var errorHandler = function(jqXHR, data) {
   var som_map = {
       "id": "guide[0].guide1[0].guideRootPanel[0].Pet[0].id_1[0]",
       "name": "guide[0].guide1[0].guideRootPanel[0].Pet[0].name_2[0]",
       "status": "guide[0].guide1[0].guideRootPanel[0].Pet[0].status[0]"
   };
   
   
   var errorJson = {};
   errorJson.errors = [];
   
   if (data) {
       if (data.originMessage) {
           var errorData;
           try {
               errorData = JSON.parse(data.originMessage);
           } catch (err) {
               // not in json format
           }
   
           if (errorData) {
               Object.keys(errorData).forEach(function(key) {
                   var som_key = som_map[key];
                   if (som_key) {
                       var error = {};
                       error.somExpression = som_key;
                       error.errorMessage = errorData[key];
                       errorJson.errors.push(error);
                   }
               });
           }
           window.guideBridge.handleServerValidationError(errorJson);
       } else {
           window.guideBridge.handleServerValidationError(data);
       }
     }
   };
   
   guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs, null, errorHandler);
   ```

   Die `var som_map` listet den SOM-Ausdruck der adaptiven Formularfelder auf, die in das Standardformat umgewandelt werden sollen. Sie können den SOM-Ausdruck eines beliebigen Felds in einem adaptiven Formular anzeigen, indem Sie auf das Feld tippen und **[!UICONTROL SOM-Ausdruck anzeigen]** von **[!UICONTROL Weitere Optionen]** (...).

   Stellen Sie sicher, dass Sie die folgende Zeile des Beispielcodes in den benutzerdefinierten Fehler-Handler kopieren:

   ```javascript
   guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs, null, errorHandler);
   ```

   Die executeOperation-API enthält die `null` und `errorHandler` Parameter basierend auf dem neuen benutzerdefinierten Fehler-Handler.

   Mit diesem benutzerdefinierten Fehler-Handler konvertiert das adaptive Formular die in `var som_map` zum standardmäßigen Fehlermeldungsformat. Daher werden die Überprüfungsfehlermeldungen auf Feldebene im adaptiven Formular angezeigt.
