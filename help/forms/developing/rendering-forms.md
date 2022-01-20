---
title: Rendern von Forms
seo-title: Rendering Forms
description: Verwenden Sie den Forms-Dienst zum Erstellen interaktiver Clientanwendungen zur Datenerfassung, die normalerweise in Designer erstellte Formulare validieren, verarbeiten, transformieren und bereitstellen. Formularverfasser können einen einzelnen Formularentwurf entwickeln, den der Forms-Dienst in verschiedenen Browserumgebungen im PDF, SWF oder HTML rendert.
seo-description: Use the Forms service to create interactive data capture client applications that validate, process, transform, and deliver forms typically created in Designer. Form authors can develop a single form design that the Forms service renders in PDF, SWF, or HTML in various browser environments.
uuid: 68d7b7bc-7730-4a83-b7b9-ebe2a29d6c51
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/performing_service_operations_using_apis
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: f8749793-e53f-4812-a093-8278f480e6a8
role: Developer
exl-id: 61d63c89-26e8-4a50-b6a3-1bcf1a1b4c54
source-git-commit: e608249c3f95f44fdc14b100910fa11ffff5ee32
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 0%

---

# Rendern von Forms {#rendering-forms}

**Über den Forms-Dienst**

Mit dem Forms-Dienst können Sie interaktive Clientanwendungen zur Datenerfassung erstellen, mit denen typischerweise in Designer erstellte Formulare validiert, verarbeitet, transformiert und bereitgestellt werden. Formularverfasser können einen einzelnen Formularentwurf entwickeln, den der Forms-Dienst in verschiedenen Browserumgebungen im PDF, SWF oder HTML rendert.

Wenn ein Endbenutzer ein Formular anfordert, sendet eine Clientanwendung die Anforderung an den Forms-Dienst, der das Formular in einem entsprechenden Format zurückgibt. Sobald der Forms-Dienst eine Anforderung erhält, werden die Daten mit einem Formularentwurf zusammengeführt und das Formular im gewünschten Format bereitgestellt. Die Formulardienstausgabe ist ein interaktives Formular, normalerweise ein PDF-Dokument. Mit einem interaktiven Formular können Benutzer Felder im Formular ausfüllen.

Je nach Typ der Clientanwendung können Sie das Formular in einen Client-Webbrowser schreiben oder es als PDF-Datei speichern. Eine webbasierte Anwendung kann das Formular in einen Webbrowser schreiben. Ein Desktop-Programm kann das Formular als PDF-Datei speichern. Um zu demonstrieren, wie Sie an einen Webbrowser und eine PDF-Datei schreiben, beginnt der Schnellstart im *Rendern von Forms* -Abschnitte sind wie folgt organisiert:

* Beispiele für Java-API mit starker Typisierung (SOAP-Modus) sind ein Java-Servlet.
* Beispiele für den Webdienst (Java Base64) sind ein Java-Servlet.
* Bei den Webdienstbeispielen (MTOM) handelt es sich um eine Konsolenanwendung (nicht bei allen Schnellstarts wird ein MTOM-Beispiel verwendet).

   >[!NOTE]
   >
   >Informationen zum Erstellen einer Webanwendung, die Java-Servlets zum Aufrufen des Forms-Dienstes verwendet, finden Sie unter [Erstellen von Webanwendungen, die Forms rendern](/help/forms/developing/creating-web-applications-renders-forms.md).

   Sie können einen Formularentwurf (eine XDP-Datei) oder ein PDF-Dokument auf zwei Arten an den Forms-Dienst übergeben:

* Sie können den Formularentwurf mithilfe eines URL-Werts referenzieren. Dieser Ansatz beinhaltet die Verwendung von `URLSpec` -Objekt. Der Inhaltsstamm wird mithilfe der `URLSpec` -Objekt `setContentRootURI` -Methode. Der Name des Formularentwurfs ( `formQuery`) wird als separater Parameter übergeben. Die beiden Werte werden verkettet, um den absoluten Verweis auf den Formularentwurf zu erhalten. (Die meisten Schnellstarts befinden sich im *Rendern von Forms* -Abschnitt verwenden diesen Ansatz.)
* Sie können eine `com.adobe.idp.Document` , der den Formularentwurf für den Forms-Dienst enthält. Zwei neue Methoden namens `renderPDFForm2` und `renderHTMLForm2` akzeptieren `com.adobe.idp.Document` -Objekt, das einen Formularentwurf enthält. (Siehe [Übergeben von Dokumenten an den Forms-Dienst](/help/forms/developing/passing-documents-forms-service.md)

Sie können diese Aufgaben mithilfe des Forms-Dienstes ausführen:

* Interaktive PDF forms rendern (Siehe [Rendern interaktiver PDF forms](/help/forms/developing/rendering-interactive-pdf-forms.md).
* Wiedergabe von Formularen auf dem Client (Siehe [Rendern von Forms auf dem Client](/help/forms/developing/rendering-forms-client.md).
* Wiedergabe von Formularen basierend auf Fragmenten (Siehe [Rendern von Forms basierend auf Fragmenten](/help/forms/developing/rendering-forms-based-fragments.md).
* Für Rechte aktivierte Formulare wiedergeben. (Siehe [Rendern von Rights-aktiviertem Forms](/help/forms/developing/rendering-rights-enabled-forms.md).
* Rendern von Formularen als HTML (Siehe [Rendern von Forms als HTML](/help/forms/developing/rendering-forms-html.md).
* Rendern von HTML Forms mit benutzerdefinierten CSS-Dateien ([Rendern von HTML Forms mit benutzerdefinierten CSS-Dateien](/help/forms/developing/rendering-html-forms-using-custom.md).
* Verarbeiten gesendeter Formulare. (Siehe [Umgang mit übermittelten Forms](/help/forms/developing/handling-submitted-forms.md).
* Erstellen von PDF-Dokumenten mit gesendeten XML-Daten. (Siehe [Erstellen von PDF-Dokumenten mit gesendeten XML-Daten](/help/forms/developing/creating-pdf-documents-submitted-xml.md).
* Formulare im Voraus ausfüllen. (Siehe [Vorausfüllen von Forms mit flexiblen Layouts](/help/forms/developing/prepopulating-forms-flowable-layouts.md).
* Übergeben von Dokumenten. (Siehe [Übergeben von Dokumenten an den Forms-Dienst](/help/forms/developing/passing-documents-forms-service.md)
* Formulardaten berechnen. (Siehe [Formulardaten berechnen](/help/forms/developing/calculating-form-data.md).
* Optimieren einer Anwendung. (Siehe [Leistungsoptimierung des Forms-Dienstes](/help/forms/developing/optimizing-performance-forms-service.md).

