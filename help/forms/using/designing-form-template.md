---
title: Entwerfen von Formularvorlagen für HTML5-Formulare
seo-title: Designing form templates for HTML5 forms
description: AEM Forms ermöglicht die Wiedergabe von XFA-Formularvorlagen im HTML5-Format. Formularentwickler können Formularvorlagen mit Designer entwerfen und die HTML5-Render-Funktion nutzen.
seo-description: AEM Forms offers rendering XFA form template to HTML5 format. Form designers can design form templates using Designer and use the HTML5 rendition capability.
uuid: 41a00ec5-d7f9-4717-a961-00d20d8e7b2a
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: e135fa01-fede-4285-b4dd-2d23acbb4d26
feature: Mobile Forms
exl-id: 248e56c7-51b7-41d3-8bc9-a5d737bf178b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 62%

---

# Entwerfen von Formularvorlagen für HTML5-Formulare {#designing-form-templates-for-html-forms}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Die HTML5 forms-Komponente in AEM bietet die Wiedergabe der XFA-Formularvorlage im HTML5-Format. Formularentwickler können Formularvorlagen mit [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63_de) entwerfen und die HTML5-Renderfunktion nutzen. Diese Formularvorlagen können sich zusammen mit ihren Assets in AEM Repository oder Dateisystem befinden oder über HTTP verfügbar gemacht werden. Wenn Sie beabsichtigen, Ihre Formulare mithilfe von Forms Manager zu verwalten, müssen sich die Vorlagen und Assets im AEM-Repository befinden.

Obwohl das Verhalten von HTML5-Formularen und PDF-Formularen sich stark ähnelt, gibt es mehrere Funktionen in beiden Formaten, die nicht im anderen Format verfügbar sind. Beispielsweise ist die Anwendung von Barcodes auf einem PDF-Formular in Adobe Reader und auf einem Formular für Mobilgeräte unterschiedlich, ebenso wie es bei digitalen Signaturen Unterschiede gibt. Weitere Informationen zu diesen Unterschieden finden Sie unter [Funktionsunterschiede zwischen HTML5- und PDF-Formularen](/help/forms/using/feature-differentiation-html5-forms-pdf-forms.md).

Allgemeine XFA-Funktionen finden Sie in den folgenden Best Practices und Richtlinien zum Entwerfen eines Formulars, das in beiden Formaten funktioniert.

## Funktionen in AEM Forms Designer für HTML5-Formulare {#capabilities-in-aem-forms-designer-for-html-forms}

### Vorschau von HTML {#preview-html}

Die Registerkarte Vorschau-HTML wird im Designmodus hinzugefügt, damit Formularentwickler während des Entwurfsprozesses eine Vorschau der Formulare im HTML5-Format anzeigen können. Weitere Informationen zum Aktivieren und Konfigurieren dieser Funktion in AEM Forms Designer finden Sie unter [Vorschau von HTML](/help/forms/using/preview-xdp-forms-html.md).

### Scribble-Signatur {#scribble-signature}

Das Hauptziel für HTML5-Formulare sind Touch-Geräte. Daher wird ein neues Scribble-Signatur-Steuerelement in AEM Forms Designer hinzugefügt. Sie können das Scribble-Signatur-Steuerelement anklicken oder per Drag-und-Drop auf Ihre Formularvorlage ziehen und konfigurieren. Es wird in der HTML5-Darstellung als Scribble-Feld gerendert und kann für Scribble-Signaturen auf Touch-Geräten verwendet werden. Auf Desktop-Rechnern kann es per Maussteuerung als Scribble-Feld verwendet werden. Weitere Informationen dazu, wie Sie diese Funktion nutzen, finden Sie unter [XFA-Scribble-Feld](/help/forms/using/scribble-signature.md).

![4](assets/4.png)
