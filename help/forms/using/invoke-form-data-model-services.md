---
title: API zum Aufrufen von Formulardatenmodelldiensten aus adaptiven Formularen
seo-title: API to invoke form data model service from adaptive forms
description: 'Hier wird die invokeWebServices-API beschrieben, mit deren Hilfe Sie Webdienste aufrufen können, die in einem Feld eines adaptiven Formulars in WSDL geschrieben wurden. '
seo-description: Explains the invokeWebServices API that you can use to invoke web services written in WSDL from within an adaptive form field.
uuid: 40561086-e69d-4e6a-9543-1eb2f54cd836
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: aa3e50f1-8f5a-489d-a42e-a928e437ab79
feature: Adaptive Forms
exl-id: 0653b0e4-a697-472a-8093-5ed48ede3c75
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 88%

---

# API zum Aufrufen von Formulardatenmodelldiensten aus adaptiven Formularen {#api-to-invoke-form-data-model-service-from-adaptive-forms}

## Übersicht {#overview}

AEM Forms ermöglicht es Formularautoren, das Ausfüllen von Formularen weiter zu vereinfachen und zu verbessern, indem sie Dienste, die in einem Formulardatenmodell konfiguriert sind, aus einem adaptiven Formularfeld heraus aufrufen. Um einen Datenmodell-Service aufzurufen, können Sie entweder eine Regel im visuellen Editor anlegen oder ein JavaScript mit der `guidelib.dataIntegrationUtils.executeOperation`-API im Code-Editor des [Regeleditors](/help/forms/using/rule-editor.md) angeben.

In diesem Dokument wird das Schreiben von JavaScript in der `guidelib.dataIntegrationUtils.executeOperation`-API für den Aufruf eines Service beschrieben.

## Verwenden der API {#using-the-api}

Die `guidelib.dataIntegrationUtils.executeOperation` API ruft einen Dienst aus einem Feld in einem adaptiven Formular auf. Für die API gilt folgende Syntax:

```
guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs)
```

Für die API sind die folgenden Parameter erforderlich.

| Parameter | Beschreibung |
|---|---|
| `operationInfo` | Struktur zur Angabe von Formulardatenmodellkennung, Operationstitel und Operationsname |
| `inputs` | Struktur zum Angeben von Formularobjekten, deren Werte in den Dienstvorgang eingegeben werden |
| `outputs` | Struktur zum Angeben von Formularobjekten, die mit den vom Dienstvorgang zurückgegebenen Werten gefüllt werden |

Die Struktur der `guidelib.dataIntegrationUtils.executeOperation`-API gibt Details zum Service-Vorgang an. Die Struktur weist die folgende Syntax auf.

```
var operationInfo = {
formDataModelId,
operationTitle,
operationName
};
var inputs = {
inputField1,
inputFieldN
};
var outputs = {
outputField1,
outputFieldN
}
```

Die API-Struktur gibt folgende Informationen zum Service-Vorgang an.

<table> 
 <tbody> 
  <tr> 
   <th>Parameter</th> 
   <th>Beschreibung</th> 
  </tr> 
  <tr> 
   <td><code>forDataModelId</code></td> 
   <td>Geben Sie den Repository-Pfad zum Formulardatenmodell an, einschließlich Name</td> 
  </tr> 
  <tr> 
   <td><code>operationName</code></td> 
   <td>Geben Sie den Namen des Dienstvorgangs an, um</td> 
  </tr> 
  <tr> 
   <td><code>input</code></td> 
   <td>Ordnen Sie ein oder mehrere Formularobjekte den Eingabeargumenten für den Dienstvorgang zu.</td> 
  </tr> 
  <tr> 
   <td>Ausgabe</td> 
   <td>Ordnen Sie ein oder mehrere Formularobjekte Ausgabewerte aus dem Dienstvorgang zu, um Formularfelder zu füllen.<br />  </td> 
  </tr> 
 </tbody> 
</table>

## Beispielskript zum Aufrufen eines Service {#sample-script-to-invoke-a-service}

Folgendes Beispielskript verwendet die `guidelib.dataIntegrationUtils.executeOperation`-API, um den `getAccountById`-Service-Vorgang aufzurufen, der im Formulardatenmodell `employeeAccount` konfiguriert ist.

Der Vorgang `getAccountById` nimmt den Wert im Formularfeld `employeeID` als Eingabe für das Argument `empId` und gibt den Mitarbeiternamen, die Kontonummer und den Kontostand für den entsprechenden Mitarbeiter zurück. Die Ausgabewerte werden in den angegebenen Formularfeldern befüllt. Beispielsweise wird der Wert im Argument `name` im Formularelement `fullName` befüllt und der Wert für das Argument `accountNumber` im Formularelement `account`.

```
var operationInfo = {
"formDataModelId": "/content/dam/formsanddocuments-fdm/employeeAccount",
"operationName": "getAccountDetails"
};
var inputs = {
"empid" : employeeID
};
var outputs = {
"name" : fullName,
"accountNumber" : account,
"balance" : balance
};
guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs);
```
