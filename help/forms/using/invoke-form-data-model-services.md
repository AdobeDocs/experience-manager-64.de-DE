---
title: API zum Aufrufen des Formulardatenmodell-Service aus adaptiven Formularen
seo-title: API to invoke form data model service from adaptive forms
description: Erläutert die invokeWebServices-API, mit der Sie Webdienste aufrufen können, die in WSDL von einem Feld in einem adaptiven Formular aus geschrieben wurden.
seo-description: Explains the invokeWebServices API that you can use to invoke web services written in WSDL from within an adaptive form field.
uuid: 40561086-e69d-4e6a-9543-1eb2f54cd836
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: aa3e50f1-8f5a-489d-a42e-a928e437ab79
feature: Adaptive Forms
exl-id: 0653b0e4-a697-472a-8093-5ed48ede3c75
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 55%

---

# API zum Aufrufen von Formulardatenmodelldiensten aus adaptiven Formularen {#api-to-invoke-form-data-model-service-from-adaptive-forms}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Übersicht {#overview}

AEM Forms ermöglicht es Formularautoren, das Ausfüllen von Formularen weiter zu vereinfachen und zu verbessern, indem sie Dienste aufrufen, die in einem Formulardatenmodell innerhalb eines adaptiven Formularfelds konfiguriert sind. Um einen Datenmodell-Service aufzurufen, können Sie entweder eine Regel im visuellen Editor anlegen oder ein JavaScript mit der `guidelib.dataIntegrationUtils.executeOperation`-API im Code-Editor des [Regeleditors](/help/forms/using/rule-editor.md) angeben.

In diesem Dokument wird das Schreiben von JavaScript in der `guidelib.dataIntegrationUtils.executeOperation`-API für den Aufruf eines Service beschrieben.

## Verwenden der API {#using-the-api}

Die `guidelib.dataIntegrationUtils.executeOperation`-API ruft einen Service über ein Feld in einem adaptiven Formular auf. Für die API gilt folgende Syntax:

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
   <td>Geben Sie den Repository-Pfad zum Formulardatenmodell einschließlich dessen Namen an</td> 
  </tr> 
  <tr> 
   <td><code>operationName</code></td> 
   <td>Geben Sie den Namen des auszuführenden Dienstvorgangs an</td> 
  </tr> 
  <tr> 
   <td><code>input</code></td> 
   <td>Ordnen Sie den Eingabeargumenten für den Dienstvorgang mindestens ein Formularobjekt zu</td> 
  </tr> 
  <tr> 
   <td>Ausgabe</td> 
   <td>Ordnen Sie ein oder mehrere Formularobjekte Ausgabewerten aus dem Dienstvorgang zu, um Formularfelder auszufüllen<br /> </td> 
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
