---
title: Asynchrone Übermittlung von adaptiven Formularen
seo-title: Asynchronous submission of adaptive forms
description: Erfahren Sie, wie Sie die asynchrone Übermittlung für adaptive Formulare konfigurieren.
seo-description: Learn to configure asynchronous submission for adaptive forms.
uuid: 3b8aeac8-cb38-4a2b-8375-556b2736d58b
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 6e4e3af5-4260-4f38-9b29-0818e92bc182
feature: Adaptive Forms
exl-id: 1ca492e9-9832-4e5d-8020-2690ac4f5505
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '691'
ht-degree: 40%

---

# Asynchrone Übermittlung von adaptiven Formularen {#asynchronous-submission-of-adaptive-forms}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Web-Formulare werden herkömmlicherweise für die synchrone Übermittlung konfiguriert. Wenn Benutzer ein Formular senden, werden sie zu einer Bestätigungsseite oder, falls die Übermittlung fehlschlägt, zu einer Fehlerseite umgeleitet. Allerdings sind moderne Web-Abläufe wie Einzelseitenanwendungen zunehmend beliebt. Dabei bleibt die Web-Seite unverändert, während die Client-Server-Interaktion im Hintergrund abläuft. Sie können diese Erfahrung jetzt in adaptiven Formularen bieten, indem Sie die asynchrone Übermittlung konfigurieren. In diesem Fall verhält sich ein adaptives Formular wie eine Einzelseitenanwendung, da das Formular nicht neu geladen wird oder sich seine URL nicht ändert, wenn die gesendeten Formulardaten auf dem Server validiert werden.

Weitere Informationen zur asynchronen Übermittlung in adaptiven Formularen finden Sie im Abschnitt .

## Asynchrone Übermittlung konfigurieren {#configure}

So konfigurieren Sie die asynchrone Übermittlung für ein adaptives Formular:

1. Wählen Sie im Authoring-Modus des adaptiven Formulars den Formular-Container aus und tippen Sie auf ![cmppr1](assets/cmppr1.png), um dessen Eigenschaften anzuzeigen.
1. Aktivieren Sie im Eigenschaftenbereich **[!UICONTROL Übermittlung]** die Option **[!UICONTROL Asynchrone Übermittlung verwenden]**.
1. Im **[!UICONTROL Beim Senden]** wählen Sie eine der folgenden Optionen aus, die bei erfolgreicher Formularübermittlung ausgeführt werden sollen.

   * **[!UICONTROL Zu URL umleiten]**: Leitet beim Senden des Formulars zur angegebenen URL oder Seite um. Sie können eine URL angeben oder mit der Funktion zum Durchsuchen den Pfad zu einer Seite im Feld **[!UICONTROL Umleitungs-URL/Pfad]** wählen.
   * **[!UICONTROL Nachricht anzeigen]**: Zeigt eine Meldung beim Senden des Formulars an. Sie können eine Nachricht in das Textfeld unterhalb der Option Nachricht anzeigen eingeben. Das Textfeld unterstützt Rich-Text-Formatierung.

1. Tippen Sie auf ![check-button1](assets/check-button1.png), um die Eigenschaften zu speichern.

## Funktionsweise der asynchronen Übermittlung {#how-asynchronous-submission-works}

AEM Forms bietet vordefinierte Erfolgs- und Fehler-Handler für die Formularübermittlung. Handler sind clientseitige Funktionen, die basierend auf der Serverantwort ausgeführt werden. Wenn ein Formular gesendet wird, werden die Daten zur Validierung an den Server übermittelt, der eine Antwort mit Informationen zum Erfolgs- oder Fehlerereignis für die Übermittlung an den Client zurückgibt. Die Informationen werden als Parameter an den relevanten Handler übergeben, um die Funktion auszuführen.

Darüber hinaus können Formularautoren und -entwickler formularspezifische Regeln schreiben, die die Standard-Handler überschreiben. Weitere Informationen finden Sie unter [Standard-Handler mithilfe von Regeln überschreiben](#custom).

Lassen Sie uns zunächst die Serverantwort auf Erfolgs- und Fehlerereignisse überprüfen.

### Server-Antwort für Erfolgsereignis bei Übermittlung {#server-response-for-submission-success-event}

Die Server-Antwort für Erfolgsereignis bei Übermittlung weist folgende Struktur auf:

```
{
  contentType : "<xmlschema or jsonschema>", 
  data : "<dataXML or dataJson>" , 
  thankYouOption : <page/message>, 
  thankYouContent : "<thank you page url/thank you message>"
}
```

Die Serverantwort im Falle einer erfolgreichen Formularübermittlung umfasst Folgendes:

* Form data format type: XML oder JSON
* Formulardaten im XML- oder JSON-Format
* Ausgewählte Option, um zu einer Seite umzuleiten oder eine Nachricht wie im Formular konfiguriert anzuzeigen
* Seiten-URL oder Nachrichteninhalt, wie im Formular konfiguriert

Der Erfolgshandler liest die Serverantwort und leitet entsprechend zur konfigurierten Seiten-URL weiter oder zeigt eine Nachricht an.

### Serverantwort für Fehlerereignis bei Übermittlung {#server-response-for-submission-error-event}

Die Struktur der Serverantwort für das Ereignis bei Übertragungsfehlern sieht wie folgt aus:

```
{
   errorCausedBy : "<CAPTCHA_VALIDATION or SERVER_SIDE_VALIDATION>",

   errors : [
               { "somExpression" : "<SOM Expression>",
                 "errorMessage"  : "<Error Message>"
               },
               ...
             ]
 }
```

Die Serverantwort im Fall eines Fehlers bei der Formularübermittlung umfasst Folgendes:

* Grund für den Fehler, falsche Antwort in CAPTCHA oder fehlgeschlagene Server-seitige Validierung
* Liste der Fehlerobjekte, einschließlich des SOM-Ausdrucks des Felds, bei dem die Validierung fehlgeschlagen ist, und der entsprechenden Fehlermeldung

Der Fehler-Handler liest die Serverantwort und zeigt dementsprechend die Fehlermeldung im Formular an.

## Standard-Handler mithilfe von Regeln außer Kraft setzen {#custom}

Formularentwickler und -autoren können im Code-Editor auf Formularebene Regeln schreiben, um Standard-Handler zu überschreiben. Die Antwort des Servers bei Erfolgs- und Fehlerereignissen wird auf Formularebene bereitgestellt, auf die Entwickler mithilfe von `$event.data` in Regeln zugreifen können.

Führen Sie die folgenden Schritte aus, um im Codeeditor Regeln zu schreiben, um die Erfolgs- und Fehlerereignisse zu verarbeiten.

1. Öffnen Sie das adaptive Formular im Authoring-Modus, wählen Sie ein Formularobjekt aus und tippen Sie auf ![edit-rules1](assets/edit-rules1.png), um den Regeleditor zu öffnen.
1. Wählen Sie **[!UICONTROL Formular]** in der Struktur „Formularobjekte“ und tippen Sie auf **[!UICONTROL Erstellen]**.
1. Auswählen **[!UICONTROL Code-Editor]** aus der Dropdown-Liste der Modusauswahl.
1. Tippen Sie im Codeeditor auf **[!UICONTROL Code bearbeiten]**. Tippen **[!UICONTROL Bearbeiten]** im Bestätigungsdialogfeld angezeigt.
1. Auswählen **[!UICONTROL Erfolgreiche Übermittlung]** oder **[!UICONTROL Fehler bei Übermittlung]** von **[!UICONTROL Ereignis]** Dropdown-Liste.
1. Eine Regel für das ausgewählte Ereignis schreiben und auf tippen **[!UICONTROL Fertig]** , um die Regel zu speichern.
