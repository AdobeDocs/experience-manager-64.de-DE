---
title: Rendern von Rights-aktiviertem Forms
seo-title: Rendering Rights-Enabled Forms
description: Verwenden Sie den Forms-Dienst zum Rendern von Formularen, für die Verwendungsrechte angewendet wurden. Sie können Formulare mit aktivierten Rechten mithilfe der Java-API und der Web Service-API rendern.
seo-description: Use the Forms service to render forms that have usage rights applied to them. You can render rights-enabled forms using the Java API and Web Service API.
uuid: ce5e4be6-d9b0-4989-a0e1-a8c3b98aed77
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: d4c2b2f0-613a-409d-b39b-8e37fdb96eea
role: Developer
exl-id: 0cee94ba-1a72-4021-b606-8fa945312483
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1463'
ht-degree: 5%

---

# Rendern von Rights-aktiviertem Forms {#rendering-rights-enabled-forms}

Der Forms-Dienst kann Formulare wiedergeben, auf die Verwendungsrechte angewendet wurden. Verwendungsrechte gelten für Funktionen, die standardmäßig in Acrobat, nicht jedoch in Adobe Reader zur Verfügung stehen, wie etwa die Möglichkeit, Kommentare zu einem Formular hinzuzufügen oder Formularfelder auszufüllen und das Formular zu speichern. Forms, auf die Verwendungsrechte angewendet wurden, werden als Formulare mit aktivierten Verwendungsrechten bezeichnet. Ein Benutzer, der ein Formular mit aktivierten Benutzerrechten in Adobe Reader öffnet, kann Vorgänge durchführen, die für dieses Formular aktiviert sind.

Um Verwendungsrechte auf ein Formular anzuwenden, muss der Acrobat Reader DC Extensions-Dienst Teil Ihrer AEM Forms-Installation sein. Außerdem müssen Sie über gültige Berechtigungen verfügen, mit denen Sie Verwendungsrechte auf PDF-Dokumente anwenden können. Das heißt, Sie müssen den Acrobat Reader DC Extensions-Dienst ordnungsgemäß konfigurieren, bevor Sie ein Formular mit aktivierten Rechten wiedergeben können. (Siehe [Informationen zum Acrobat Reader DC Extensions-Dienst](/help/forms/developing/assigning-usage-rights.md#about-the-acrobat-reader-dc-extensions-service).

>[!NOTE]
>
>Um ein Formular wiederzugeben, das Verwendungsrechte enthält, müssen Sie eine XDP-Datei als Eingabe und keine PDF-Datei verwenden. Wenn Sie eine PDF-Datei als Eingabe verwenden, wird das Formular weiterhin wiedergegeben. Es handelt sich jedoch nicht um ein Formular mit aktivierten Rechten.

>[!NOTE]
>
>Sie können ein Formular nicht mit XML-Daten vorab ausfüllen, wenn Sie die folgenden Verwendungsrechte angeben: `enableComments`, `enableCommentsOnline`, `enableEmbeddedFiles`oder `enableDigitalSignatures`. (Siehe [Vorausfüllen von Forms mit flexiblen Layouts](/help/forms/developing/prepopulating-forms-flowable-layouts.md).

>[!NOTE]
>
>Weitere Informationen zum Forms-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Zusammenfassung der Schritte {#summary-of-steps}

Um ein Formular mit aktivierten Rechten wiederzugeben, führen Sie die folgenden Aufgaben aus:

1. Projektdateien einschließen.
1. Erstellen Sie ein Forms Client-API-Objekt.
1. Legen Sie Laufzeitoptionen für Nutzungsrechte fest.
1. Wiedergabe eines Formulars mit aktivierten Verwendungsrechten.
1. Schreiben Sie das Formular mit aktivierten Berechtigungen in den Client-Webbrowser.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Forms Client-API-Objekts**

Bevor Sie einen Client-API-Vorgang für den Forms-Dienst programmgesteuert ausführen können, müssen Sie einen Forms-Dienstclient erstellen.

**Laufzeitoptionen für Verwendungsrechte festlegen**

Sie müssen Laufzeitoptionen für Nutzungsrechte festlegen, um ein Formular mit aktivierten Verwendungsrechten wiederzugeben. Sie müssen auch den Alias der Berechtigung angeben, die zum Anwenden von Verwendungsrechten auf ein Formular verwendet wird. Nachdem Sie den Alias-Wert angegeben haben, geben Sie jedes Nutzungsrecht an, das auf das Formular angewendet werden soll.

**Wiedergabe eines Formulars mit aktivierten Verwendungsrechten**

Um ein Formular mit aktivierten Benutzerrechten wiederzugeben, verwenden Sie dieselbe Anwendungslogik wie die Wiedergabe eines Formulars ohne Verwendungsrechte. Der einzige Unterschied besteht darin, dass Sie sicherstellen müssen, dass die Laufzeitoptionen für Nutzungsrechte in Ihrer Anwendungslogik enthalten sind.

>[!NOTE]
>
>Bei der Wiedergabe eines Formulars mit aktivierten Rechten mithilfe der Forms-Webdienst-API können Sie keine Dateien an das Formular anhängen.

**Schreiben Sie den Formulardaten-Stream in den Client-Webbrowser**

Wenn der Forms-Dienst ein Formular mit aktivierten Benutzerrechten rendert, wird ein Formulardatenstream zurückgegeben, den Sie in den Client-Webbrowser schreiben müssen. Nach dem Schreiben in den Client-Webbrowser ist das Formular für den Benutzer sichtbar. Ein Benutzer, der das Formular mit aktivierten Rechten in Adobe Reader anzeigt, kann Vorgänge ausführen, die für dieses Formular aktiviert sind.

**Siehe auch**

[Rendern von Formularen mit aktivierten Rechten mithilfe der Java-API](#render-rights-enabled-forms-using-the-java-api)

[Rendern von Formularen mit aktivierten Verwendungsrechten mithilfe der Webdienst-API](#render-rights-enabled-forms-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Forms Service-API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Rendern interaktiver PDF forms](/help/forms/developing/rendering-interactive-pdf-forms.md)

[Erstellen von Webanwendungen, die Forms rendern](/help/forms/developing/creating-web-applications-renders-forms.md)

### Rendern von Formularen mit aktivierten Rechten mithilfe der Java-API {#render-rights-enabled-forms-using-the-java-api}

Rendern Sie ein Formular mit aktivierten Rechten mithilfe der Forms API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-forms-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Forms Client-API-Objekts

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie eine `FormsServiceClient` -Objekt durch Verwendung seines Konstruktors und Übergabe des `ServiceClientFactory` -Objekt.

1. Laufzeitoptionen für Verwendungsrechte festlegen

   * Erstellen Sie ein Objekt `ReaderExtensionSpec`, indem Sie den Konstruktor verwenden.
   * Geben Sie den Alias der Berechtigung an, indem Sie die `ReaderExtensionSpec` -Objekt `setReCredentialAlias` -Methode und geben Sie einen Zeichenfolgenwert an, der den Alias-Wert darstellt.
   * Legen Sie die einzelnen Verwendungsrechte fest, indem Sie die entsprechende Methode aufrufen, die zum `ReaderExtensionSpec` -Objekt. Sie können jedoch nur dann ein Verwendungsrecht festlegen, wenn die von Ihnen referenzierte Berechtigung dies zulässt. Das heißt, Sie können keine Verwendungsrechte festlegen, wenn die Berechtigung es Ihnen nicht erlaubt, sie festzulegen. Beispiel. Um die Verwendungsrechte festzulegen, mit denen ein Benutzer Formularfelder ausfüllen und das Formular speichern kann, rufen Sie die `ReaderExtensionSpec` -Objekt `setReFillIn` -Methode und -übergabe `true`.

   >[!NOTE]
   >
   >Es ist nicht erforderlich, die `ReaderExtensionSpec` -Objekt `setReCredentialPassword`* Methode. Diese Methode wird vom Forms-Dienst nicht verwendet. *

1. Wiedergabe eines Formulars mit aktivierten Verwendungsrechten

   Rufen Sie die `FormsServiceClient` -Objekt `renderPDFFormWithUsageRights` -Methode verwenden und die folgenden Werte übergeben:

   * Ein string -Wert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil einer Forms-Anwendung ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * A `com.adobe.idp.Document` -Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie einen leeren `com.adobe.idp.Document` -Objekt.
   * A `PDFFormRenderSpec` -Objekt, das Laufzeitoptionen speichert.
   * A `ReaderExtensionSpec` -Objekt, das Laufzeitoptionen für Nutzungsrechte speichert.
   * A `URLSpec` -Objekt, das URI-Werte enthält, die für den Forms-Dienst erforderlich sind.

   Die `renderPDFFormWithUsageRights` -Methode gibt eine `FormsResult` -Objekt, das einen Formulardatenstrom enthält, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben Sie den Formulardaten-Stream in den Client-Webbrowser

   * Erstellen Sie eine `com.adobe.idp.Document` -Objekt durch Aufrufen der `FormsResult` object ‘s `getOutputContent` -Methode.
   * Abrufen des Inhaltstyps der `com.adobe.idp.Document` -Objekt durch Aufrufen seiner `getContentType` -Methode.
   * Legen Sie die `javax.servlet.http.HttpServletResponse` Inhaltstyp des Objekts durch Aufrufen seiner `setContentType` -Methode und Übergabe des Inhaltstyps der `com.adobe.idp.Document` -Objekt.
   * Erstellen Sie eine `javax.servlet.ServletOutputStream` -Objekt, das zum Schreiben des Formulardaten-Streams in den Client-Webbrowser durch Aufrufen der `javax.servlet.http.HttpServletResponse` -Objekt `getOutputStream` -Methode.
   * Erstellen Sie eine `java.io.InputStream` -Objekt durch Aufrufen der `com.adobe.idp.Document` -Objekt `getInputStream` -Methode.
   * Erstellen Sie ein Byte-Array, das mit dem Formulardatenstream gefüllt wird, indem Sie die `InputStream` -Objekt `read` -Methode verwenden und das Byte-Array als Argument übergeben.
   * Rufen Sie die `javax.servlet.ServletOutputStream` -Objekt `write` -Methode zum Senden des Formulardaten-Streams an den Client-Webbrowser. Übergeben Sie das Byte-Array an die `write` -Methode.

**Siehe auch**

[Schnellstart (SOAP-Modus): Rendern eines Formulars mit aktivierten Rechten mithilfe der Java-API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-a-rights-enabled-form-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Rendern von Formularen mit aktivierten Verwendungsrechten mithilfe der Webdienst-API {#render-rights-enabled-forms-using-the-web-service-api}

Rendern Sie ein Formular mit aktivierten Rechten mithilfe der Forms-API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie Java-Proxyklassen, die die Forms-Dienst-WSDL verwenden.
   * Schließen Sie die Java-Proxy-Klassen in Ihren Klassenpfad ein.

1. Erstellen eines Forms Client-API-Objekts

   Erstellen Sie eine `FormsService` Objekt und legen Sie Authentifizierungswerte fest.

1. Laufzeitoptionen für Verwendungsrechte festlegen

   * Erstellen Sie ein Objekt `ReaderExtensionSpec`, indem Sie den Konstruktor verwenden.
   * Geben Sie den Alias der Berechtigung an, indem Sie die `ReaderExtensionSpec` -Objekt `setReCredentialAlias` -Methode und geben Sie einen Zeichenfolgenwert an, der den Alias-Wert darstellt.
   * Legen Sie die einzelnen Verwendungsrechte fest, indem Sie die entsprechende Methode aufrufen, die zum `ReaderExtensionSpec` -Objekt. Sie können jedoch nur dann ein Verwendungsrecht festlegen, wenn die von Ihnen referenzierte Berechtigung dies zulässt. Das heißt, Sie können keine Verwendungsrechte festlegen, wenn die Berechtigung es Ihnen nicht erlaubt, sie festzulegen. Um die Verwendungsrechte festzulegen, mit denen ein Benutzer Formularfelder ausfüllen und das Formular speichern kann, rufen Sie die `ReaderExtensionSpec` -Objekt `setReFillIn` -Methode und -übergabe `true`.

1. Wiedergabe eines Formulars mit aktivierten Verwendungsrechten

   Rufen Sie die `FormsService` -Objekt `renderPDFFormWithUsageRights` -Methode verwenden und die folgenden Werte übergeben:

   * Ein string -Wert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil einer Forms-Anwendung ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * A `BLOB` -Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten mit dem Formular zusammenführen möchten, müssen Sie eine `BLOB` -Objekt, das auf einer leeren XML-Datenquelle basiert. Sie können keine `BLOB` Objekt, das null ist; Andernfalls wird eine Ausnahme ausgelöst.
   * A `PDFFormRenderSpec` -Objekt, das Laufzeitoptionen speichert.
   * A `ReaderExtensionSpec` -Objekt, das Laufzeitoptionen für Nutzungsrechte speichert.
   * A `URLSpec` -Objekt, das URI-Werte enthält, die für den Forms-Dienst erforderlich sind.

   Die `renderPDFFormWithUsageRights` -Methode gibt eine `FormsResult` -Objekt, das einen Formulardatenstrom enthält, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben Sie den Formulardaten-Stream in den Client-Webbrowser

   * Erstellen Sie eine `BLOB` -Objekt, das Formulardaten enthält, durch Aufrufen der `FormsResult` -Objekt `getOutputContent` -Methode.
   * Abrufen des Inhaltstyps der `BLOB` -Objekt durch Aufrufen seiner `getContentType` -Methode.
   * Legen Sie die `javax.servlet.http.HttpServletResponse` Inhaltstyp des Objekts durch Aufrufen seiner `setContentType` -Methode und Übergabe des Inhaltstyps der `BLOB` -Objekt.
   * Erstellen Sie eine `javax.servlet.ServletOutputStream` -Objekt, das zum Schreiben des Formulardaten-Streams in den Client-Webbrowser durch Aufrufen der `javax.servlet.http.HttpServletResponse` -Objekt `getOutputStream` -Methode.
   * Erstellen Sie ein Byte-Array und füllen Sie es durch Aufrufen der `BLOB` -Objekt `getBinaryData` -Methode. Diese Aufgabe weist den Inhalt des `FormsResult` -Objekt zum Byte-Array hinzu.
   * Rufen Sie die `javax.servlet.http.HttpServletResponse` -Objekt `write` -Methode zum Senden des Formulardaten-Streams an den Client-Webbrowser. Übergeben Sie das Byte-Array an die `write` -Methode.

**Siehe auch**

[Rendern von Rights-aktiviertem Forms](#rendering-rights-enabled-forms)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
