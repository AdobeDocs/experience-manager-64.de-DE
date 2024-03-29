---
title: Rendern von Formularen
seo-title: Rendering Forms
description: Verwenden Sie den Forms-Service, um interaktive Client-Programme zur Datenerfassung zu erstellen, die Formulare, welche üblicherweise in Designer erstellt werden, validieren, verarbeiten, transformieren und bereitstellen. Formularverfasser können einen einzelnen Formularentwurf entwickeln, den der Forms-Service in verschiedenen Browser-Umgebungen als PDF, SWF oder HTML wiedergibt.
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
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '593'
ht-degree: 95%

---

# Rendern von Formularen {#rendering-forms}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

**Über den Forms-Service**

Der Forms-Service ermöglicht das Erstellen interaktiver Client-Programme zur Datenerfassung, die Formulare, welche üblicherweise in Designer erstellt werden, validieren, verarbeiten, transformieren und bereitstellen. Formularverfasser können einen einzelnen Formularentwurf entwickeln, den der Forms-Service in verschiedenen Browser-Umgebungen als PDF, SWF oder HTML wiedergibt.

Wenn ein Endbenutzer ein Formular anfordert, sendet ein Client-Programm die Anforderung an den Forms-Service, der das Formular in einem entsprechenden Format zurückgibt. Sobald der Forms-Service eine Anforderung erhält, werden die Daten mit einem Formularentwurf zusammengeführt und das Formular im gewünschten Format bereitgestellt. Die Ausgabe des Forms-Services ist ein interaktives Formular, in der Regel ein PDF-Dokument. Mit einem interaktiven Formular können Benutzer Felder im Formular ausfüllen.

Je nach Typ des Client-Programms können Sie das Formular in einen Client-Webbrowser schreiben oder es als PDF-Datei speichern. Ein Web-basiertes Programm kann das Formular in einen Webbrowser schreiben. Ein Desktop-Programm kann das Formular als PDF-Datei speichern. Um zu demonstrieren, wie die Ausgabe in einen Webbrowser und in eine PDF-Datei erfolgt, sind die Kurzanleitungen im Abschnitt *Wiedergeben von Formularen* wie folgt aufgebaut:

* Die Beispiele für Java-API mit starker Typisierung (SOAP-Modus) sind ein Java-Servlet.
* Die Beispiele für den Webservice (Java Base64) sind ein Java-Servlet.
* Bei den Webservice-Beispielen (MTOM) handelt es sich um ein Konsolenprogramm (nicht bei allen Kurzanleitungen wird ein MTOM-Beispiel verwendet).

   >[!NOTE]
   >
   >Weitere Informationen zum Erstellen eines Web-Programms, das Java-Servlets zum Aufrufen des Forms-Services verwendet, finden Sie unter [Erstellen von Web-Programmen zum Wiedergeben von Formularen](/help/forms/developing/creating-web-applications-renders-forms.md).

   Sie können einen Formularentwurf (eine XDP-Datei) oder ein PDF-Dokument auf zwei Arten an den Forms-Service übergeben:

* Sie können den Formularentwurf mithilfe eines URL-Werts referenzieren. Dieser Ansatz beinhaltet die Verwendung eines `URLSpec`-Objekts. Der Inhaltsstamm wird mit der Methode `setContentRootURI` des `URLSpec`-Objekts an den Forms-Service übergeben. Der Name des Formularentwurfs (`formQuery`) wird als separater Parameter übergeben. Die beiden Werte werden verkettet, um den absoluten Verweis auf den Formularentwurf zu bilden. (Die meisten der Kurzanleitungen im Abschnitt *Wiedergeben von Formularen* verwenden diesen Ansatz.)
* Sie können ein `com.adobe.idp.Document`, das den Formularentwurf enthält, an den Forms-Service übergeben. Zwei neue Methoden namens `renderPDFForm2` und `renderHTMLForm2` akzeptieren `com.adobe.idp.Document`-Objekt, das einen Formularentwurf enthält. (Siehe [Übergeben von Dokumenten an den Forms-Service](/help/forms/developing/passing-documents-forms-service.md)

Sie können diese Aufgaben mithilfe des Forms-Services ausführen:

* Interaktive PDF-Formulare wiedergeben. (Siehe [Wiedergeben von interaktiven PDF-Formularen](/help/forms/developing/rendering-interactive-pdf-forms.md).)
* Wiedergeben von Formularen auf dem Client. (Siehe [Wiedergeben von Formularen auf dem Client](/help/forms/developing/rendering-forms-client.md).)
* Wiedergabe von Formularen basierend auf Fragmenten. (Siehe [Wiedergeben von Formularen, die auf Fragmenten basieren](/help/forms/developing/rendering-forms-based-fragments.md).)
* Berechtigungsaktivierte Formulare wiedergeben. (Siehe [Wiedergeben von berechtigungsaktivierten Formularen](/help/forms/developing/rendering-rights-enabled-forms.md).)
* Formulare als HTML wiedergeben. (Siehe [Wiedergeben von Formularen als HTML](/help/forms/developing/rendering-forms-html.md).)
* Wiedergeben von HTML-Formularen mithilfe von benutzerdefinierten CSS-Dateien ([Wiedergeben von HTML-Formularen mithilfe von benutzerdefinierten CSS-Dateien](/help/forms/developing/rendering-html-forms-using-custom.md))
* Übermittelte Formulare verarbeiten. (Siehe [Verarbeiten von übermittelten Formularen](/help/forms/developing/handling-submitted-forms.md).)
* PDF-Dokumente mit übermittelten XML-Daten erstellen. (Siehe [Erstellen von PDF-Dokumenten mit übermittelten XML-Daten](/help/forms/developing/creating-pdf-documents-submitted-xml.md).)
* Formulare im Voraus ausfüllen. (Siehe [Vorausfüllen von Formularen mit flexiblen Layouts](/help/forms/developing/prepopulating-forms-flowable-layouts.md).)
* Dokumente übergeben. (Siehe [Übergeben von Dokumenten an den Forms-Service](/help/forms/developing/passing-documents-forms-service.md).)
* Formulardaten berechnen. (Siehe [Berechnen von Formulardaten](/help/forms/developing/calculating-form-data.md).)
* Optimieren eines Programms. (Siehe [Leistungsoptimierung des Forms-Services](/help/forms/developing/optimizing-performance-forms-service.md).)

