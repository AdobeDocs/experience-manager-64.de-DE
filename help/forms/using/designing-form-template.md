---
title: Entwerfen von Formularvorlagen für HTML5-Formulare
seo-title: Entwerfen von Formularvorlagen für HTML5-Formulare
description: 'AEM Forms ermöglicht die Wiedergabe von XFA-Formularvorlagen im HTML5-Format. Formularentwickler können Formularvorlagen mit Designer entwerfen und die HTML5-Renderfunktion nutzen. '
seo-description: 'AEM Forms ermöglicht die Wiedergabe von XFA-Formularvorlagen im HTML5-Format. Formularentwickler können Formularvorlagen mit Designer entwerfen und die HTML5-Renderfunktion nutzen. '
uuid: 41a00ec5-d7f9-4717-a961-00d20d8e7b2a
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: e135fa01-fede-4285-b4dd-2d23acbb4d26
feature: Mobile Forms
exl-id: 248e56c7-51b7-41d3-8bc9-a5d737bf178b
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 65%

---

# Entwerfen von Formularvorlagen für HTML5-Formulare {#designing-form-templates-for-html-forms}

Die HTML5-Formularkomponente in AEM ermöglicht, XFA-Formularvorlagen im HTML5-Format zu rendern. Formularentwickler können Formularvorlagen mit [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63) entwerfen und die HTML5-Renderfunktion nutzen. Diese Formularvorlagen können sich zusammen mit ihren Assets im AEM Repository-Dateisystem befinden oder über HTTP bereitgestellt werden. Wenn Sie Ihre Formulare jedoch mit Forms Manager verwalten möchten, sollten sich die Vorlagen und Assets im AEM Repository befinden.

Obwohl das Verhalten von HTML5-Formularen und PDF-Formularen sich stark ähnelt, gibt es mehrere Funktionen in beiden Formaten, die nicht im anderen Format verfügbar sind. Beispielsweise variiert die Anwendung von Barcodes auf ein PDF-Formular in Adobe Reader von einem Mobile-Formular aus oder die digitale Unterzeichnung eines Formulars variiert auch zwischen den Formaten. Weitere Informationen zu diesen Varianten finden Sie unter [Funktionsunterschiede zwischen HTML5-Formularen und PDF forms](/help/forms/using/feature-differentiation-html5-forms-pdf-forms.md).

Allgemeine XFA-Funktionen finden Sie in den folgenden empfohlenen Verfahrensweisen und Richtlinien zum Entwerfen eines Formulars, das in beiden Formaten funktioniert.

## Funktionen in AEM Forms Designer für HTML5 Forms {#capabilities-in-aem-forms-designer-for-html-forms}

### HTML-Vorschau {#preview-html}

Die HTML-Vorschau-Registerkarte wurde im Designmodus für Formularentwickler hinzugefügt, um eine Vorschau von Formularen im HTML5-Format während des Entwurfsprozesses zu ermöglichen. Weitere Informationen dazu, wie Sie diese Funktion in AEM Forms Designer aktivieren und konfigurieren, finden Sie unter [HTML-Vorschau](/help/forms/using/preview-xdp-forms-html.md).

### Scribble-Signatur {#scribble-signature}

Das Hauptziel für HTML5-Formulare sind Touch-Geräte. Daher wurde ein neues Scribble-Signatur-Steuerelement in AEM Forms Designer hinzugefügt. Sie können auf das Scribble-Signatur-Steuerelement klicken oder es per Drag-and-Drop auf Ihre Formularvorlage ziehen und konfigurieren. Sie wird in der HTML5-Ausgabe als Scribble-Feld gerendert und kann für die Scribble-Signatur auf Touch-Geräten verwendet werden. Auf Desktop-Rechnern kann es per Maussteuerung als Scribble-Feld verwendet werden. Weitere Informationen zur Verwendung dieser Funktion finden Sie unter [XFA Scribble Field](/help/forms/using/scribble-signature.md).

![4](assets/4.png)
