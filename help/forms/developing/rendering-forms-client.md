---
title: Rendern von Forms auf dem Client
seo-title: Rendering Forms at the Client
description: Optimieren Sie die Bereitstellung von PDF-Inhalten und verbessern Sie die Fähigkeit des Forms-Dienstes, die Netzwerklast mithilfe der clientseitigen Rendering-Funktion von Acrobat oder Adobe Reader zu bewältigen.
seo-description: Optimize the delivery of PDF content and improve the Forms service’s ability to handle network load by using the client-side rendering capability of Acrobat or Adobe Reader.
uuid: 09bcc23d-28b0-473a-87f1-bc17e87620f4
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 08d36e9f-cafc-478e-9781-8fc29ac6262e
role: Developer
exl-id: 641452e6-bf7e-4af4-a4f9-6e5627db9fca
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1684'
ht-degree: 2%

---

# Rendern von Forms auf dem Client {#rendering-forms-at-the-client}

## Rendern von Forms auf dem Client {#rendering-forms-at-the-client-inner}

Sie können die Bereitstellung von PDF-Inhalten optimieren und die Fähigkeit des Forms-Dienstes, die Netzwerklast zu bewältigen, verbessern, indem Sie die clientseitige Rendering-Funktion von Acrobat oder Adobe Reader verwenden. Dieser Prozess wird als Wiedergabe eines Formulars auf dem Client bezeichnet. Um ein Formular auf dem Client wiederzugeben, muss das Client-Gerät (normalerweise ein Webbrowser) Acrobat 7.0 oder Adobe Reader 7.0 oder höher verwenden.

Änderungen an einem Formular, die aus der serverseitigen Skriptausführung resultieren, werden nicht in einem Formular übernommen, das auf dem Client wiedergegeben wird, es sei denn, das Stammteilformular enthält die `restoreState` -Attribut, das auf `auto`. Weitere Informationen zu diesem Attribut finden Sie unter [Forms Designer.](https://www.adobe.com/go/learn_aemforms_designer_63)

>[!NOTE]
>
>Weitere Informationen zum Forms-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

Führen Sie die folgenden Aufgaben aus, um ein Formular auf dem Client wiederzugeben:

1. Projektdateien einschließen.
1. Erstellen Sie ein Forms Client-API-Objekt.
1. Legen Sie Laufzeitoptionen für Client-Rendering fest.
1. Wiedergabe eines Formulars auf dem Client
1. Schreiben Sie das Formular in den Client-Webbrowser.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Forms Client-API-Objekts**

Bevor Sie einen Client-API-Vorgang für den Forms-Dienst programmgesteuert ausführen können, müssen Sie einen Forms-Dienstclient erstellen. Wenn Sie die Java-API verwenden, erstellen Sie eine `FormsServiceClient` -Objekt. Wenn Sie die Forms-Webdienst-API verwenden, erstellen Sie eine `FormsService` -Objekt.

**Festlegen von Laufzeitoptionen für Client-Rendering**

Sie müssen die Laufzeitoption zum Rendern eines Formulars auf dem Client festlegen, indem Sie die `RenderAtClient` Laufzeitoption zu `true`. Dadurch wird das Formular an das Client-Gerät gesendet, auf dem es wiedergegeben wird. Wenn `RenderAtClient` is `auto` (Standardwert) bestimmt der Formularentwurf, ob das Formular auf dem Client wiedergegeben wird. Der Formularentwurf muss ein Formularentwurf mit flexiblem Layout sein.

Eine optionale Laufzeitoption, die Sie festlegen können, ist die `SeedPDF` -Option. Die `SeedPDF` -Option kombiniert den PDF-Container (Seed-PDF-Dokument) mit dem Formularentwurf und den XML-Daten. Sowohl der Formularentwurf als auch die XML-Daten werden an Acrobat oder Adobe Reader übermittelt, wo das Formular wiedergegeben wird. Die `SeedPDF` kann verwendet werden, wenn der Clientcomputer über keine Schriften verfügt, die im Formular verwendet werden, z. B. wenn ein Endbenutzer nicht für die Verwendung einer Schrift lizenziert ist, die der Formularinhaber verwenden darf.

Sie können Designer verwenden, um eine einfache dynamische PDF-Datei zu erstellen, die als Seed-PDF-Datei verwendet werden kann. Die folgenden Schritte sind erforderlich, um diese Aufgabe durchzuführen:

1. Bestimmen Sie, ob Sie Schriftarten in die Seed-PDF-Datei einbetten müssen. Die Seed-PDF-Datei muss zusätzliche Schriftarten enthalten, die für das wiedergegebene Formular erforderlich sind. Stellen Sie beim Einbetten von Schriftarten in die Seed-PDF-Datei sicher, dass Sie keine Schriftartlizenzvereinbarungen verletzen. In Designer können Sie festlegen, ob Sie Schriftarten rechtmäßig einbetten können. Wenn Schriftarten gespeichert werden, die nicht in das Formular eingebettet werden können, zeigt Designer eine Meldung an, in der die Schriftarten aufgeführt werden, die nicht eingebettet werden können. Diese Meldung wird in Designer bei statischen PDF-Dokumenten nicht angezeigt.
1. Wenn Sie die Seed-PDF-Datei in Designer erstellen, wird empfohlen, mindestens ein Textfeld mit einer Meldung hinzuzufügen. Die Meldung sollte an Benutzer früherer Versionen von Adobe Reader gerichtet werden, die darauf hinweisen, dass sie Acrobat 7.0 oder höher oder Adobe Reader 7.0 oder höher benötigen, um das Dokument anzuzeigen.
1. Speichern Sie die Seed-PDF-Datei als dynamische PDF-Datei mit der PDF-Dateinamenerweiterung.

>[!NOTE]
>
>Sie müssen die Laufzeitoption Testadressen-PDF nicht definieren, um ein Formular auf dem Client wiederzugeben. Wenn Sie keine Seed-PDF angeben, erstellt der Forms-Dienst ein Shell-PDF-Dokument, das keine COS-Objekte enthält, jedoch einen PDF-Wrapper mit dem eigentlichen XDP-Inhalt enthält, der in eingebettet ist. Die Schritte in diesem Abschnitt legen die Laufzeitoption zum Testen der PDF nicht fest. Informationen zu COS-Objekten finden Sie im Adobe PDF-Referenzhandbuch.

**Formular auf dem Client wiedergeben**

Um ein Formular auf dem Client wiederzugeben, müssen Sie sicherstellen, dass die Client-Rendering-Laufzeitoptionen in Ihrer Anwendungslogik enthalten sind, um ein Formular wiederzugeben.

**Schreiben Sie den Formulardaten-Stream in den Client-Webbrowser**

Der Forms-Dienst erstellt einen Formulardatenstream, den Sie in den Client-Webbrowser schreiben müssen. Wenn das Formular in den Client-Webbrowser geschrieben wird, wird es von Acrobat 7.0 oder Adobe Reader 7.0 oder höher wiedergegeben und ist für den Benutzer sichtbar.

**Siehe auch**

[Wiedergabe eines Formulars auf dem Client mithilfe der Java-API](#render-a-form-at-the-client-using-the-java-api)

[Wiedergabe eines Formulars auf dem Client mithilfe der Webdienst-API](#render-a-form-at-the-client-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Forms Service-API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Übergeben von Dokumenten an den Forms-Dienst](/help/forms/developing/passing-documents-forms-service.md)

[Erstellen von Webanwendungen, die Forms rendern](/help/forms/developing/creating-web-applications-renders-forms.md)

### Wiedergabe eines Formulars auf dem Client mithilfe der Java-API {#render-a-form-at-the-client-using-the-java-api}

Wiedergabe eines Formulars auf dem Client mithilfe der Forms API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-forms-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Forms Client-API-Objekts

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie eine `FormsServiceClient` -Objekt durch Verwendung seines Konstruktors und Übergabe des `ServiceClientFactory` -Objekt.

1. Festlegen von Laufzeitoptionen für Client-Rendering

   * Erstellen Sie ein Objekt `PDFFormRenderSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die `RenderAtClient` Laufzeitoption durch Aufrufen der `PDFFormRenderSpec` -Objekt `setRenderAtClient` Methode und Übergabe des Enum-Werts `RenderAtClient.Yes`.

1. Formular auf dem Client wiedergeben

   Rufen Sie die `FormsServiceClient` -Objekt `renderPDFForm` -Methode verwenden und die folgenden Werte übergeben:

   * Ein string -Wert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil einer AEM Forms-Anwendung ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * A `com.adobe.idp.Document` -Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie einen leeren `com.adobe.idp.Document` -Objekt.
   * A `PDFFormRenderSpec` -Objekt, das Laufzeitoptionen speichert, die zum Rendern eines Formulars auf dem Client erforderlich sind.
   * A `URLSpec` -Objekt, das URI-Werte enthält, die der Forms-Dienst zum Rendern eines Formulars benötigt.
   * A `java.util.HashMap` -Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter, den Sie `null` , wenn Sie keine Dateien an das Formular anhängen möchten.

   Die `renderPDFForm` -Methode gibt eine `FormsResult` -Objekt, das einen Formulardatenstrom enthält, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben Sie den Formulardaten-Stream in den Client-Webbrowser

   * Erstellen Sie eine `com.adobe.idp.Document` -Objekt durch Aufrufen der `FormsResult` object ‘s `getOutputContent` -Methode.
   * Abrufen des Inhaltstyps der `com.adobe.idp.Document` -Objekt durch Aufrufen seiner `getContentType` -Methode.
   * Legen Sie die `javax.servlet.http.HttpServletResponse` Inhaltstyp des Objekts durch Aufrufen seiner `setContentType` -Methode und Übergabe des Inhaltstyps der `com.adobe.idp.Document` -Objekt.
   * Erstellen Sie eine `javax.servlet.ServletOutputStream` -Objekt, das zum Schreiben des Formulardaten-Streams in den Client-Webbrowser durch Aufrufen der `javax.servlet.http.HttpServletResponse` -Objekt `getOutputStream` -Methode.
   * Erstellen Sie eine `java.io.InputStream` -Objekt durch Aufrufen der `com.adobe.idp.Document` -Objekt `getInputStream` -Methode.
   * Erstellen Sie ein Byte-Array und füllen Sie es mit dem Formulardatenstream, indem Sie die `InputStream` -Objekt `read` -Methode verwenden und das Byte-Array als Argument übergeben.
   * Rufen Sie die `javax.servlet.ServletOutputStream` -Objekt `write` -Methode zum Senden des Formulardaten-Streams an den Client-Webbrowser. Übergeben Sie das Byte-Array an die `write` -Methode.

**Siehe auch**

[Schnellstart (SOAP-Modus): Wiedergabe eines Formulars auf dem Client mithilfe der Java-API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-a-form-at-the-client-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Wiedergabe eines Formulars auf dem Client mithilfe der Webdienst-API {#render-a-form-at-the-client-using-the-web-service-api}

Wiedergabe eines Formulars auf dem Client mithilfe der Forms-API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie Java-Proxyklassen, die die Forms-Dienst-WSDL verwenden.
   * Schließen Sie die Java-Proxy-Klassen in Ihren Klassenpfad ein.

1. Erstellen eines Forms Client-API-Objekts

   Erstellen Sie eine `FormsService` Objekt und legen Sie Authentifizierungswerte fest.

1. Festlegen von Laufzeitoptionen für Client-Rendering

   * Erstellen Sie ein Objekt `PDFFormRenderSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die `RenderAtClient` Laufzeitoption durch Aufrufen der `PDFFormRenderSpec` -Objekt `setRenderAtClient` -Methode und Übergeben des Zeichenfolgenwerts `RenderAtClient.Yes`.

1. Formular auf dem Client wiedergeben

   Rufen Sie die `FormsService` -Objekt `renderPDFForm` -Methode verwenden und die folgenden Werte übergeben:

   * Ein string -Wert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil einer Forms-Anwendung ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * A `BLOB` -Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie `null`. (Siehe [Vorausfüllen von Forms mit flexiblen Layouts](/help/forms/developing/prepopulating-forms-flowable-layouts.md).
   * A `PDFFormRenderSpec` -Objekt, das Laufzeitoptionen speichert, die zum Rendern eines Formulars auf dem Client erforderlich sind.
   * A `URLSpec` -Objekt, das URI-Werte enthält, die für den Forms-Dienst erforderlich sind.
   * A `java.util.HashMap` -Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter, den Sie `null` , wenn Sie keine Dateien an das Formular anhängen möchten.
   * Ein leeres `com.adobe.idp.services.holders.BLOBHolder` -Objekt, das von der -Methode aufgefüllt wird. Dieser Parameter wird zum Speichern des wiedergegebenen PDF-Formulars verwendet.
   * Ein leeres `javax.xml.rpc.holders.LongHolder` -Objekt, das von der -Methode aufgefüllt wird. (Dieses Argument speichert die Anzahl der Seiten im Formular).
   * Ein leeres `javax.xml.rpc.holders.StringHolder` -Objekt, das von der -Methode aufgefüllt wird. (Dieses Argument speichert den Gebietsschemawert).
   * Ein leeres `com.adobe.idp.services.holders.FormsResultHolder` -Objekt, das die Ergebnisse dieses Vorgangs enthält.

   Die `renderPDFForm` -Methode füllt die `com.adobe.idp.services.holders.FormsResultHolder` -Objekt, das als letzter Argumentwert mit einem Formulardatenstream übergeben wird, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben Sie den Formulardaten-Stream in den Client-Webbrowser

   * Erstellen Sie eine `FormResult` -Objekt durch Abrufen des Werts der `com.adobe.idp.services.holders.FormsResultHolder` -Objekt `value` Datenelement.
   * Erstellen Sie eine `BLOB` -Objekt, das Formulardaten enthält, durch Aufrufen der `FormsResult` -Objekt `getOutputContent` -Methode.
   * Abrufen des Inhaltstyps der `BLOB` -Objekt durch Aufrufen seiner `getContentType` -Methode.
   * Legen Sie die `javax.servlet.http.HttpServletResponse` Inhaltstyp des Objekts durch Aufrufen seiner `setContentType` -Methode und Übergabe des Inhaltstyps der `BLOB` -Objekt.
   * Erstellen Sie eine `javax.servlet.ServletOutputStream` -Objekt, das zum Schreiben des Formulardaten-Streams in den Client-Webbrowser durch Aufrufen der `javax.servlet.http.HttpServletResponse` -Objekt `getOutputStream` -Methode.
   * Erstellen Sie ein Byte-Array und füllen Sie es durch Aufrufen der `BLOB` -Objekt `getBinaryData` -Methode. Diese Aufgabe weist den Inhalt des `FormsResult` -Objekt zum Byte-Array hinzu.
   * Rufen Sie die `javax.servlet.http.HttpServletResponse` -Objekt `write` -Methode zum Senden des Formulardaten-Streams an den Client-Webbrowser. Übergeben Sie das Byte-Array an die `write` -Methode.

**Siehe auch**

[Rendern von Forms auf dem Client](#rendering-forms-at-the-client)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
