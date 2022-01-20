---
title: Rendern von HTML Forms mit benutzerdefinierten CSS-Dateien
seo-title: Rendering HTML Forms Using Custom CSS Files
description: Verwenden Sie den Forms-Dienst, um auf benutzerdefinierte CSS-Dateien zu verweisen, um HTML-Formulare als Reaktion auf eine HTTP-Anforderung eines Webbrowsers wiederzugeben. Sie können ein HTML-Formular rendern, das eine CSS-Datei verwendet, indem Sie die Java-API und die Web Service-API verwenden.
seo-description: Use the Forms service to refer to custom CSS files to render HTML forms in response to an HTTP request from a web browser. You can render an HTML form that uses a CSS file using the Java API and Web Service API.
uuid: a44e96f1-001d-48a2-8c96-15cb9d0c71b3
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 8fe7c072-7df0-44b7-92d0-bf39dc1e688a
role: Developer
exl-id: d10cbb97-1cec-4b1b-9104-48063e75a2cd
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1674'
ht-degree: 2%

---

# Rendern von HTML Forms mit benutzerdefinierten CSS-Dateien {#rendering-html-forms-using-custom-css-files}

Der Forms-Dienst rendert HTML-Formulare als Reaktion auf eine HTTP-Anforderung eines Webbrowsers. Beim Rendern eines HTML-Formulars kann der Forms-Dienst auf eine benutzerdefinierte CSS-Datei verweisen. Sie können eine benutzerdefinierte CSS-Datei erstellen, um Ihre Geschäftsanforderungen zu erfüllen und auf diese CSS-Datei zu verweisen, wenn Sie den Forms-Dienst zum Rendern von HTML-Formularen verwenden.

Der Forms-Dienst analysiert die benutzerdefinierte CSS-Datei im Hintergrund. Das heißt, der Forms-Dienst meldet keine Fehler, die auftreten können, wenn die benutzerdefinierte CSS-Datei nicht den CSS-Standards entspricht. In diesem Fall ignoriert der Forms-Dienst den Stil und fährt mit den übrigen Stilen fort, die sich in der CSS-Datei befinden.

Die folgende Liste enthält Stile, die in einer benutzerdefinierten CSS-Datei unterstützt werden:

* **Selektorstil-Paare auf Klassenebene**: Wenn in einer benutzerdefinierten CSS-Datei vorhanden, werden Selektoren verwendet, die im HTML-Formular als Klassenstile verwendet werden. Nicht verwendete Klassenstile werden ignoriert.
* **Selektorstil-Paare auf Identifizierungsebene**: Alle Identifizierungsstile werden verwendet, wenn sie im HTML-Formular verwendet werden.
* **Selektor-Stil-Paare auf Elementebene**: Alle Elementstile werden verwendet, wenn sie im HTML-Formular verwendet werden.
* **Stilpriorität**: Stilpriorität (wie wichtig) wird unterstützt und kann in einer benutzerdefinierten CSS-Datei verwendet werden.
* **Medientyp**: Ein oder mehrere Selektorstil-Paare können in den @media-Stil eingeschlossen werden, um den Medientyp zu definieren. Der Forms-Dienst überprüft nicht, ob der angegebene Medientyp unterstützt wird. Der in der benutzerdefinierten CSS-Datei angegebene Medientyp wird im HTML-Formular zusammengeführt.

Sie können eine CSS-Beispieldatei mit der FormsIVS-Anwendung abrufen. Laden Sie das Formular hoch, wählen Sie es auf der Seite &quot;Formularentwurf testen&quot;aus und klicken Sie auf &quot;CSS generieren&quot;. Es ist nicht erforderlich, den HTML-Transformationstyp festzulegen, bevor Sie auf die Schaltfläche klicken. Wählen Sie dann Speichern aus. Sie können diese CSS-Datei bearbeiten, um Ihre Geschäftsanforderungen zu erfüllen.

>[!NOTE]
>
>Bevor Sie ein HTML-Formular rendern, das eine benutzerdefinierte CSS-Datei verwendet, müssen Sie über fundierte Kenntnisse im Rendern von HTML-Formularen verfügen. (Siehe [Rendern von Forms als HTML](/help/forms/developing/rendering-forms-html.md).

>[!NOTE]
>
>Weitere Informationen zum Forms-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Zusammenfassung der Schritte {#summary-of-steps}

Um ein HTML-Formular wiederzugeben, das eine CSS-Datei verwendet, führen Sie die folgenden Schritte aus:

1. Projektdateien einschließen.
1. Erstellen Sie ein Forms Java API-Objekt.
1. Verweisen Sie auf die CSS-Datei.
1. Rendern Sie ein HTML-Formular.
1. Schreiben Sie den Formular-Datenstrom in den Client-Webbrowser.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Forms Java API-Objekts**

Bevor Sie einen vom Forms-Dienst unterstützten Vorgang programmgesteuert ausführen können, müssen Sie ein Forms-Client-Objekt erstellen.

**Verweisen auf die CSS-Datei**

Um ein HTML-Formular wiederzugeben, das eine benutzerdefinierte CSS-Datei verwendet, stellen Sie sicher, dass Sie auf eine vorhandene CSS-Datei verweisen.

**Rendern eines HTML-Formulars**

Um ein HTML-Formular wiederzugeben, müssen Sie einen Formularentwurf angeben, der in Designer erstellt und als XDP-Datei gespeichert wurde. Sie müssen auch einen HTML-Transformationstyp auswählen. Sie können beispielsweise den Transformationstyp HTML angeben, der eine dynamische HTML für Internet Explorer 5.0 oder höher rendert.

Für die Wiedergabe eines HTML-Formulars sind auch Werte erforderlich, z. B. URI-Werte, die zum Rendern anderer Formulartypen erforderlich sind.

**Schreiben Sie den Formulardaten-Stream in den Client-Webbrowser**

Wenn der Forms-Dienst ein HTML-Formular rendert, wird ein Formulardatenstream zurückgegeben, den Sie in den Client-Webbrowser schreiben müssen, damit das HTML-Formular für den Benutzer sichtbar wird.

**Siehe auch**

[Rendern eines HTML-Formulars, das eine CSS-Datei mit der Java-API verwendet](#render-an-html-form-that-uses-a-css-file-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Forms Service-API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Rendern interaktiver PDF forms](/help/forms/developing/rendering-interactive-pdf-forms.md)

[Rendern von Forms als HTML](/help/forms/developing/rendering-forms-html.md)

[Erstellen von Webanwendungen, die Forms rendern](/help/forms/developing/creating-web-applications-renders-forms.md)

## Rendern eines HTML-Formulars, das eine CSS-Datei mit der Java-API verwendet {#render-an-html-form-that-uses-a-css-file-using-the-java-api}

Rendern Sie ein HTML-Formular, das eine benutzerdefinierte CSS-Datei mithilfe der Forms-API (Java) verwendet:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-forms-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Forms Java API-Objekts

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `FormsServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Verweisen auf die CSS-Datei

   * Erstellen Sie eine `HTMLRenderSpec` -Objekt durch Verwendung seines -Konstruktors.
   * Rufen Sie zum Rendern des HTML-Formulars, das eine benutzerdefinierte CSS-Datei verwendet, die `HTMLRenderSpec` -Objekt `setCustomCSSURI` -Methode verwenden und einen string -Wert übergeben, der den Speicherort und den Namen der CSS-Datei angibt.

1. Rendern eines HTML-Formulars

   Rufen Sie die `FormsServiceClient` -Objekt `(Deprecated) (Deprecated) renderHTMLForm` -Methode verwenden und die folgenden Werte übergeben:

   * Ein string -Wert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil einer Forms-Anwendung ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * A `TransformTo` enum -Wert, der den Präferenztyp für HTML angibt. Um beispielsweise ein HTML-Formular wiederzugeben, das mit dynamischem HTML für Internet Explorer 5.0 oder höher kompatibel ist, geben Sie `TransformTo.MSDHTML`.
   * A `com.adobe.idp.Document` -Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie einen leeren `com.adobe.idp.Document` -Objekt.
   * Die `HTMLRenderSpec` -Objekt, das HTML-Laufzeitoptionen speichert.
   * Ein string -Wert, der die `HTTP_USER_AGENT` Kopfzeilenwert, z. B. `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`.
   * A `URLSpec` -Objekt, das URI-Werte speichert, die zum Rendern eines HTML-Formulars erforderlich sind.
   * A `java.util.HashMap` -Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter, den Sie `null` , wenn Sie keine Dateien an das Formular anhängen möchten.

   Die `(Deprecated) renderHTMLForm` -Methode gibt eine `FormsResult` -Objekt, das einen Formulardatenstrom enthält, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben Sie den Formulardaten-Stream in den Client-Webbrowser

   * Erstellen Sie eine `com.adobe.idp.Document` -Objekt durch Aufrufen der `FormsResult` object ‘s `getOutputContent` -Methode.
   * Abrufen des Inhaltstyps der `com.adobe.idp.Document` -Objekt durch Aufrufen seiner `getContentType` -Methode.
   * Legen Sie die `javax.servlet.http.HttpServletResponse` Inhaltstyp des Objekts durch Aufrufen seiner `setContentType` -Methode und Übergabe des Inhaltstyps der `com.adobe.idp.Document` -Objekt.
   * Erstellen Sie eine `javax.servlet.ServletOutputStream` -Objekt, das zum Schreiben des Formulardaten-Streams in den Client-Webbrowser durch Aufrufen der `javax.servlet.h\ttp.HttpServletResponse` -Objekt `getOutputStream` -Methode.
   * Erstellen Sie eine `java.io.InputStream` -Objekt durch Aufrufen der `com.adobe.idp.Document` -Objekt `getInputStream` -Methode.
   * Erstellen Sie ein Byte-Array und füllen Sie es mit dem Formulardatenstream, indem Sie die `InputStream` -Objekt `read` -Methode verwenden und das Byte-Array als Argument übergeben.
   * Rufen Sie die `javax.servlet.ServletOutputStream` -Objekt `write` -Methode zum Senden des Formulardaten-Streams an den Client-Webbrowser. Übergeben Sie das Byte-Array an die `write` -Methode.

**Siehe auch**

[Rendern von HTML Forms mit benutzerdefinierten CSS-Dateien](#rendering-html-forms-using-custom-css-files)

[Schnellstart (SOAP-Modus): Rendern eines HTML-Formulars, das eine CSS-Datei mit der Java-API verwendet](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-an-html-form-that-uses-a-css-file-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Rendern eines HTML-Formulars, das eine CSS-Datei mit der Webdienst-API verwendet {#render-an-html-form-that-uses-a-css-file-using-the-web-service-api}

Rendern Sie ein HTML-Formular, das eine benutzerdefinierte CSS-Datei verwendet, mithilfe der Forms-API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie Java-Proxyklassen, die die Forms-Dienst-WSDL verwenden.
   * Schließen Sie die Java-Proxy-Klassen in Ihren Klassenpfad ein.

1. Erstellen eines Forms Java API-Objekts

   Erstellen Sie eine `FormsService` Objekt und legen Sie Authentifizierungswerte fest.

1. Verweisen auf die CSS-Datei

   * Erstellen Sie eine `HTMLRenderSpec` -Objekt durch Verwendung seines -Konstruktors.
   * Rufen Sie zum Rendern des HTML-Formulars, das eine benutzerdefinierte CSS-Datei verwendet, die `HTMLRenderSpec` -Objekt `setCustomCSSURI` -Methode verwenden und einen string -Wert übergeben, der den Speicherort und den Namen der CSS-Datei angibt.

1. Rendern eines HTML-Formulars

   Rufen Sie die `FormsService` -Objekt `(Deprecated) renderHTMLForm` -Methode verwenden und die folgenden Werte übergeben:

   * Ein string -Wert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil einer Forms-Anwendung ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * A `TransformTo` enum -Wert, der den Präferenztyp für HTML angibt. Um beispielsweise ein HTML-Formular wiederzugeben, das mit dynamischem HTML für Internet Explorer 5.0 oder höher kompatibel ist, geben Sie `TransformTo.MSDHTML`.
   * A `BLOB` -Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie `null`. (Siehe [Vorausfüllen von Forms mit flexiblen Layouts](/help/forms/developing/prepopulating-forms-flowable-layouts.md).
   * Die `HTMLRenderSpec` -Objekt, das HTML-Laufzeitoptionen speichert.
   * Ein string -Wert, der die `HTTP_USER_AGENT` Kopfzeilenwert, z. B. `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`. Wenn Sie diesen Wert nicht festlegen möchten, können Sie eine leere Zeichenfolge übergeben.
   * A `URLSpec` -Objekt, das URI-Werte speichert, die zum Rendern eines HTML-Formulars erforderlich sind.
   * A `java.util.HashMap` -Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter, den Sie `null` , wenn Sie keine Dateien an das Formular anhängen möchten.
   * Ein leeres `com.adobe.idp.services.holders.BLOBHolder` -Objekt, das von der `(Deprecated) renderHTMLForm` -Methode. Dieser Parameterwert speichert das wiedergegebene Formular.
   * Ein leeres `com.adobe.idp.services.holders.BLOBHolder` -Objekt, das von der `(Deprecated) renderHTMLForm` -Methode. Dieser Parameter speichert die XML-Ausgabedaten.
   * Ein leeres `javax.xml.rpc.holders.LongHolder` -Objekt, das von der `(Deprecated) renderHTMLForm` -Methode. Dieses Argument speichert die Anzahl der Seiten im Formular.
   * Ein leeres `javax.xml.rpc.holders.StringHolder` -Objekt, das von der `(Deprecated) renderHTMLForm` -Methode. Dieses Argument speichert den Gebietsschemawert.
   * Ein leeres `javax.xml.rpc.holders.StringHolder` -Objekt, das von der `(Deprecated) renderHTMLForm` -Methode. Dieses Argument speichert den verwendeten HTML-Rendering-Wert.
   * Ein leeres `com.adobe.idp.services.holders.FormsResultHolder` -Objekt, das die Ergebnisse dieses Vorgangs enthält.

   Die `(Deprecated) renderHTMLForm` -Methode füllt die `com.adobe.idp.services.holders.FormsResultHolder` -Objekt, das als letzter Argumentwert mit einem Formulardatenstream übergeben wird, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben Sie den Formulardaten-Stream in den Client-Webbrowser

   * Erstellen Sie eine `FormResult` -Objekt durch Abrufen des Werts der `com.adobe.idp.services.holders.FormsResultHolder` -Objekt `value` Datenelement.
   * Erstellen Sie eine `BLOB` -Objekt, das Formulardaten enthält, durch Aufrufen der `FormsResult` -Objekt `getOutputContent` -Methode.
   * Abrufen des Inhaltstyps der `BLOB` -Objekt durch Aufrufen seiner `getContentType` -Methode.
   * Legen Sie die `javax.servlet.http.HttpServletResponse` Inhaltstyp des Objekts durch Aufrufen seiner `setContentType` -Methode und Übergabe des Inhaltstyps der `BLOB` -Objekt.
   * Erstellen Sie eine `javax.servlet.ServletOutputStream` -Objekt, das zum Schreiben des Formulardaten-Streams in den Client-Webbrowser durch Aufrufen der `javax.servlet.http.HttpServletResponse` -Objekt `getOutputStream` -Methode.
   * Erstellen Sie ein Byte-Array und füllen Sie es durch Aufrufen der `BLOB` -Objekt `getBinaryData` -Methode. Diese Aufgabe weist den Inhalt des `FormsResult` -Objekt zum Byte-Array hinzu.
   * Rufen Sie die `javax.servlet.http.HttpServletResponse` -Objekt `write` -Methode zum Senden des Formulardaten-Streams an den Client-Webbrowser. Übergeben Sie das Byte-Array an die `write` -Methode.

**Siehe auch**

[Rendern von HTML Forms mit benutzerdefinierten CSS-Dateien](#rendering-html-forms-using-custom-css-files)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
