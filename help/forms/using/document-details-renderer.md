---
title: Dokumentdetails für den Renderer
seo-title: Document details for renderer
description: Grundlegende Informationen dazu, wie die Wiedergabe in AEM Forms Workspace funktioniert, um die verschiedenen unterstützten Formular- und Dateitypen wiederzugeben.
seo-description: Conceptual information on how renders work in AEM Forms workspace to render the various supported form and file types.
uuid: ae3f0585-9105-4ca7-a490-ffdefd3ac8cd
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: b6e88080-6ffc-4796-98c7-d7462bca454e
exl-id: 192ba4c4-a133-4e16-9882-98005f25ba7f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '691'
ht-degree: 52%

---

# Dokumentdetails für den Renderer {#document-details-for-renderer}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Einführung {#introduction}

In AEM Forms Workspace werden mehrere Formulartypen nahtlos unterstützt. Dazu gehören:

* PDF forms (XDP/Acroform/Flache PDF)
* Neue HTML-Formulare
* Bilder
* Drittanbieteranwendungen (z. B. Correspondence Management)

In diesem Dokument wird die Arbeit dieser Renderer aus der Perspektive der semantischen Anpassung/Komponentenwiederverwendung erläutert, sodass die Kundenanforderungen erfüllt werden, ohne dass die Ausgabedarstellung unterbrochen wird. Obwohl der Arbeitsbereich von AEM Forms beliebige Änderungen der Benutzeroberfläche oder der Bedeutung zulässt, wird empfohlen, die Rendering-Logik von verschiedenen Formulartypen nicht zu ändern. Andernfalls können die Ergebnisse unvorhersehbar sein. Dieses Dokument dient als Anleitung bzw. als Anleitung für das Rendern desselben Formulars mit denselben Workspace-Komponenten in verschiedenen Portalen und nicht zum Ändern der Renderlogik selbst.

## PDF forms {#pdf-forms}

PDF-Formulare werden von `PdfTaskForm View` gerendert.

Wenn ein XDP-Formular als PDF-Datei gerendert wird, wird vom FormsAugmenter-Service ein `FormBridge`-JavaScript™ hinzugefügt. Dieses JavaScript™ (innerhalb des PDF-Formulars) hilft bei Aktionen wie dem Senden und Speichern von Formularen oder dem Offline-Schalten des Formulars.

Im Arbeitsbereich von AEM Forms kommuniziert die Ansicht „PDFTaskForm“ über einen HTML-Zwischen-Code, der unter `/lc/libs/ws/libs/ws/pdf.html` gespeichert ist, mit dem `FormBridge`-Javascript. Der Fluss ist:

**PDFTaskForm-Ansicht - pdf.html**

Kommunikation über `window.postMessage`/`window.attachEvent('message')`

Diese Methode ist die Standardkommunikation zwischen einem übergeordneten Frame und einem iframe. Die vorhandenen Ereignis-Listener aus zuvor geöffneten PDF forms werden entfernt, bevor ein neuer hinzugefügt wird. Bei dieser Bereinigung wird auch der Wechsel zwischen Formular-Registerkarte und Verlaufs-Registerkarte in der Aufgabendetailansicht berücksichtigt.

**pdf.html – `FormBridge`-Javascript innerhalb der gerenderten PDF-Datei**

Kommunikation über `pdfObject.postMessage`/`pdfObject.messageHandler`

Diese Methode ist die Standardkommunikation mit einem PDF-JavaScript von einer HTML. Die PdfTaskForm-Ansicht kümmert sich auch um flaches PDF und rendert es einfach.

>[!NOTE]
>
>Es wird nicht empfohlen, den Inhalt der PdfTaskForm-Ansicht &quot;pdf.html&quot;zu ändern.

## Neue HTML Forms {#new-html-forms}

Neue HTML-Formulare werden von der NewHTMLTaskForm-Ansicht wiedergegeben.

Wenn ein XDP-Formular mithilfe des in CRX bereitgestellten Mobile Forms-Pakets als HTML gerendert wird, werden auch zusätzliche `FormBridge` JavaScript auf das Formular verweist, das verschiedene Methoden zum Speichern und Senden von Formulardaten verfügbar macht.

Dieses JavaScript unterscheidet sich von dem oben in PDF forms genannten, erfüllt jedoch einen ähnlichen Zweck.

>[!NOTE]
>
>Es wird nicht empfohlen, den Inhalt der NewHTMLTaskForm-Ansicht zu ändern.

## Flex Forms und Handbücher {#flex-forms-and-guides}

Flex Forms wird von SwfTaskForm gerendert und Guides werden von HtmlTaskForm-Ansichten gerendert.

Im Arbeitsbereich von AEM Forms kommunizieren diese Ansichten mit dem tatsächlichen SWF, aus dem das Flex-Formular bzw. der Form/Guide besteht, über einen Zwischen-SWF-Code, der in `/lc/libs/ws/libs/ws/WSNextAdapter.swf` gespeichert ist.

Die Kommunikation erfolgt mithilfe von `swfObject.postMessage`/`window.flexMessageHandler`.

Dieses Protokoll wird durch `WsNextAdapter.swf` definiert. Die vorhandenen `flexMessageHandlers` im window-Objekt von zuvor geöffneten SWF-Formularen werden entfernt, bevor ein neuer hinzugefügt wird. Bei dieser Logik wird auch der Wechsel zwischen Formular-Registerkarte und Verlaufs-Registerkarte in der Aufgabendetailansicht berücksichtigt. `WsNextAdapter.swf` wird zum Ausführen verschiedener Formularaktionen wie Speichern oder Senden verwendet.

>[!NOTE]
>
>Es wird nicht empfohlen, `WSNextAdapter.swf` oder den Inhalt der Ansichten SwfTaskForm bzw. HtmlTaskForm zu ändern.

## Drittanbieteranwendungen (z. B. Correspondence Management) {#third-party-applications-for-example-correspondence-management}

Drittanbieteranwendungen werden mithilfe der ExtAppTaskForm-Ansicht gerendert.

**Kommunikation zwischen Drittanbieterprogrammen und dem Arbeitsbereich von AEM Forms**

Der Arbeitsbereich von AEM Forms ruft von `window.global.postMessage([Message],[Payload])` ab.

[Nachricht] kann eine in `runtimeMap` als `SubmitMessage`| `CancelMessage`| `ErrorMessage`| `actionEnabledMessage` angegebene Zeichenfolge sein. Drittanbieterprogramme müssen diese Schnittstelle verwenden, um den Arbeitsbereich von AEM Forms bei Bedarf zu benachrichtigen. Die Verwendung dieser Schnittstelle ist obligatorisch, da der Arbeitsbereich von AEM Forms wissen muss, wann die Aufgabe gesendet wird, damit das Aufgabefenster bereinigt werden kann.

**Kommunikation zwischen dem Arbeitsbereich von AEM Forms und Drittanbieterprogrammen**

Wenn die direkten Aktionsschaltflächen des Arbeitsbereichs von AEM Forms sichtbar sind, wird `window.[External-App-Name].getMessage([Action])` aufgerufen, wobei `[Action]` aus `routeActionMap` gelesen wird. Das Drittanbieterprogramm muss von dieser Schnittstelle abrufen und dann den Arbeitsbereich von AEM Forms über die API `postMessage ()` benachrichtigen.

Beispielsweise kann ein Flex-Programm `ExternalInterface.addCallback('getMessage', listener)` definieren, um diese Kommunikation zu unterstützen. Wenn im Drittanbieterprogramm das Senden von Formularen über eigene Schaltflächen behandelt wird, sollten Sie `hideDirectActions = true() in the runtimeMap` angeben, und Sie können diesen Listener überspringen. Daher ist dieses Konstrukt optional.

Weitere Informationen zur Integration von Drittanbieteranwendungen mit Correspondence Management finden Sie unter [Integrieren von Correspondence Management in AEM Forms Workspace](/help/forms/using/integrating-correspondence-management-html-workspace.md).
