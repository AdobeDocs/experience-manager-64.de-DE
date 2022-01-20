---
title: Rendern von Forms nach Wert
seo-title: Rendering Forms By Value
description: Verwenden Sie die Forms-API (Java), um ein Formular mit Werten mithilfe der Java-API und der Web Service-API zu rendern.
seo-description: Use the Forms API (Java) to render a form by value using the Java API and Web Service API.
uuid: b932cc54-662f-40ae-94e0-20ac82845f3b
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: ddbb2b82-4c57-4845-a5be-2435902d312b
role: Developer
exl-id: 50c34781-45e3-4255-a997-44f694527c92
source-git-commit: e608249c3f95f44fdc14b100910fa11ffff5ee32
workflow-type: tm+mt
source-wordcount: '1821'
ht-degree: 3%

---

# Rendern von Forms nach Wert {#rendering-forms-by-value}

In der Regel wird ein in Designer erstellter Formularentwurf durch Verweis auf den Forms-Dienst übergeben. Formularentwürfe können groß sein und daher ist es effizienter, sie anhand von Verweisen zu übergeben, um zu vermeiden, dass Formularentwurfssbyte nach Wert sortiert werden müssen. Der Forms-Dienst kann den Formularentwurf auch zwischenzuspeichern, sodass er den Formularentwurf beim Zwischenspeichern nicht kontinuierlich lesen muss.

Wenn ein Formularentwurf ein UUID-Attribut enthält, wird er zwischengespeichert. Der UUID-Wert ist für alle Formularentwürfe eindeutig und dient zur eindeutigen Identifizierung eines Formulars. Beim Wiedergeben eines Formulars nach Wert sollte das Formular nur zwischengespeichert werden, wenn es wiederholt verwendet wird. Wenn das Formular jedoch nicht wiederholt verwendet wird und eindeutig sein muss, können Sie das Zwischenspeichern des Formulars mithilfe von Zwischenspeicherungsoptionen vermeiden, die mithilfe der AEM Forms-API festgelegt werden.

Der Forms-Dienst kann auch den Speicherort verknüpfter Inhalte im Formularentwurf auflösen. Beispielsweise sind verknüpfte Bilder, auf die im Formularentwurf verwiesen wird, relative URLs. Verknüpfte Inhalte werden immer als relativ zum Speicherort des Formularentwurfs betrachtet. Daher muss der Speicherort des verknüpften Inhalts durch Anwenden des relativen Pfads auf den absoluten Speicherort des Formularentwurfs bestimmt werden.

Anstatt einen Formularentwurf als Referenz zu übergeben, können Sie einen Formularentwurf als Wert übergeben. Die Übergabe eines Formularentwurfs anhand eines Werts ist effizient, wenn ein Formularentwurf dynamisch erstellt wird. das heißt, wenn eine Client-Anwendung die XML generiert, die während der Laufzeit einen Formularentwurf erstellt. In diesem Fall wird ein Formularentwurf nicht in einem physischen Repository gespeichert, da er im Speicher gespeichert ist. Wenn Sie einen Formularentwurf zur Laufzeit dynamisch erstellen und nach Wert übergeben, können Sie das Formular zwischenspeichern und die Leistung des Forms-Dienstes verbessern.

**Einschränkungen für die Übergabe eines Formulars nach Wert**

Die folgenden Einschränkungen gelten, wenn ein Formularentwurf vom Wert übergeben wird:

* Relativer verknüpfter Inhalt kann nicht im Formularentwurf enthalten sein. Alle Bilder und Fragmente müssen in den Formularentwurf eingebettet oder auf den unbedingt verwiesen werden.
* Serverseitige Berechnungen können nach der Wiedergabe des Formulars nicht mehr ausgeführt werden. Wenn das Formular an den Forms-Dienst zurückgesendet wird, werden die Daten extrahiert und ohne serverseitige Berechnungen zurückgegeben.
* Da HTML nur verknüpfte Bilder zur Laufzeit verwenden kann, ist es nicht möglich, HTML mit eingebetteten Bildern zu generieren. Dies liegt daran, dass der Forms-Dienst eingebettete Bilder mit HTML unterstützt, indem er die Bilder von einem referenzierten Formularentwurf abruft. Da ein Formularentwurf, der vom Wert übergeben wird, keinen referenzierten Speicherort hat, können eingebettete Bilder nicht extrahiert werden, wenn die HTML-Seite angezeigt wird. Daher müssen Bildverweise absolute Pfade sein, die im HTML gerendert werden sollen.

>[!NOTE]
>
>Sie können zwar unterschiedliche Formulartypen nach Wert rendern (z. B. HTML-Formulare oder Formulare mit Verwendungsrechten), in diesem Abschnitt wird jedoch die Wiedergabe interaktiver PDF forms beschrieben.

>[!NOTE]
>
>Weitere Informationen zum Forms-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Zusammenfassung der Schritte {#summary-of-steps}

Um ein Formular nach Wert wiederzugeben, führen Sie die folgenden Schritte aus:

1. Projektdateien einschließen.
1. Erstellen Sie ein Forms Client-API-Objekt.
1. Referenzieren Sie den Formularentwurf.
1. Wiedergabe eines Formulars nach Wert.
1. Schreiben Sie den Formular-Datenstrom in den Client-Webbrowser.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Forms Client-API-Objekts**

Bevor Sie Daten programmgesteuert in eine PDF Form Client API importieren können, müssen Sie einen Client für den Datenintegrationsdienst erstellen. Beim Erstellen eines Service-Clients definieren Sie Verbindungseinstellungen, die zum Aufrufen eines Dienstes erforderlich sind.

**Referenzieren des Formularentwurfs**

Beim Rendern eines Formulars nach Wert müssen Sie eine `com.adobe.idp.Document` -Objekt, das den wiederzugebenden Formularentwurf enthält. Sie können auf eine vorhandene XDP-Datei verweisen oder einen Formularentwurf zur Laufzeit dynamisch erstellen und eine `com.adobe.idp.Document` mit diesen Daten.

>[!NOTE]
>
>Dieser Abschnitt und der entsprechende Schnellstart verweisen auf eine vorhandene XDP-Datei.

**Formular nach Wert rendern**

Übergeben Sie eine `com.adobe.idp.Document` -Instanz, die den Formularentwurf für die Render-Methode enthält `inDataDoc` -Parameter (kann einer der `FormsServiceClient` Rendermethoden des Objekts, z. B. `renderPDFForm`, `(Deprecated) renderHTMLForm`usw.). Dieser Parameterwert ist normalerweise für Daten reserviert, die mit dem Formular zusammengeführt werden. Übergeben Sie einen leeren Zeichenfolgenwert an die `formQuery` Parameter. Normalerweise erfordert dieser Parameter einen Zeichenfolgenwert, der den Namen des Formularentwurfs angibt.

>[!NOTE]
>
>Wenn Sie Daten im Formular anzeigen möchten, müssen diese im `xfa:datasets` -Element. Informationen zur XFA-Architektur finden Sie unter [https://www.pdfa.org/norm-refs/XFA-3_3.pdf](https://www.pdfa.org/norm-refs/XFA-3_3.pdf).

**Schreiben Sie den Formulardaten-Stream in den Client-Webbrowser**

Wenn der Forms-Dienst ein Formular anhand des Werts wiedergibt, wird ein Formulardatenstream zurückgegeben, den Sie in den Client-Webbrowser schreiben müssen. Beim Schreiben in den Client-Webbrowser ist das Formular für den Benutzer sichtbar.

**Siehe auch**

[Wiedergabe eines Formulars nach Wert mithilfe der Java-API](#render-a-form-by-value-using-the-java-api)

[Wiedergabe eines Formulars nach Wert mithilfe der Webdienst-API](#render-a-form-by-value-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Forms Service-API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Übergeben von Dokumenten an den Forms-Dienst](/help/forms/developing/passing-documents-forms-service.md)

[Erstellen von Webanwendungen, die Forms rendern](/help/forms/developing/creating-web-applications-renders-forms.md)

## Wiedergabe eines Formulars nach Wert mithilfe der Java-API {#render-a-form-by-value-using-the-java-api}

Wiedergabe eines Formulars nach Wert mithilfe der Forms-API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-forms-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Forms Client-API-Objekts

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie eine `FormsServiceClient` -Objekt durch Verwendung seines Konstruktors und Übergabe des `ServiceClientFactory` -Objekt.

1. Referenzieren des Formularentwurfs

   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, das den Formularentwurf darstellt, der mithilfe des Konstruktors wiedergegeben werden soll, und einen Zeichenfolgenwert übergibt, der den Speicherort der XDP-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Formular nach Wert rendern

   Rufen Sie die `FormsServiceClient` -Objekt `renderPDFForm` -Methode verwenden und die folgenden Werte übergeben:

   * Ein leerer Zeichenfolgenwert. (Normalerweise erfordert dieser Parameter einen Zeichenfolgenwert, der den Namen des Formularentwurfs angibt.)
   * A `com.adobe.idp.Document` -Objekt, das den Formularentwurf enthält. Normalerweise ist dieser Parameterwert für Daten reserviert, die mit dem Formular zusammengeführt werden.
   * A `PDFFormRenderSpec` -Objekt, das Laufzeitoptionen speichert. Dies ist ein optionaler Parameter, den Sie `null` , wenn Sie keine Laufzeitoptionen festlegen möchten.
   * A `URLSpec` -Objekt, das URI-Werte enthält, die für den Forms-Dienst erforderlich sind.
   * A `java.util.HashMap` -Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter, den Sie `null` , wenn Sie keine Dateien an das Formular anhängen möchten.

   Die `renderPDFForm` -Methode gibt eine `FormsResult` -Objekt, das einen Formulardatenstrom enthält, der in den Client-Webbrowser geschrieben werden kann.

1. Schreiben Sie den Formulardaten-Stream in den Client-Webbrowser

   * Erstellen Sie eine `com.adobe.idp.Document` -Objekt durch Aufrufen der `FormsResult` object ‘s `getOutputContent` -Methode.
   * Abrufen des Inhaltstyps der `com.adobe.idp.Document` -Objekt durch Aufrufen seiner `getContentType` -Methode.
   * Legen Sie die `javax.servlet.http.HttpServletResponse` Inhaltstyp des Objekts durch Aufrufen seiner `setContentType` -Methode und Übergabe des Inhaltstyps der `com.adobe.idp.Document` -Objekt.
   * Erstellen Sie eine `javax.servlet.ServletOutputStream` -Objekt, das zum Schreiben des Formulardaten-Streams in den Client-Webbrowser durch Aufrufen der `javax.servlet.http.HttpServletResponse` -Objekt `getOutputStream` -Methode.
   * Erstellen Sie eine `java.io.InputStream` -Objekt durch Aufrufen der `com.adobe.idp.Document` -Objekt `getInputStream` -Methode.
   * Erstellen Sie ein Byte-Array und weisen Sie die Größe der `InputStream` -Objekt. Rufen Sie die `InputStream` -Objekt `available` -Methode, um die Größe der `InputStream` -Objekt.
   * Füllen Sie das Byte-Array mit dem Formulardatenstream, indem Sie die `InputStream` -Objekt `read`-Methode verwenden und das Byte-Array als Argument übergeben.
   * Rufen Sie die `javax.servlet.ServletOutputStream` -Objekt `write` -Methode zum Senden des Formulardaten-Streams an den Client-Webbrowser. Übergeben Sie das Byte-Array an die `write` -Methode.

**Siehe auch**

[Rendern von Forms nach Wert](/help/forms/developing/rendering-forms.md)

[Schnellstart (SOAP-Modus): Rendern nach Wert mit der Java-API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-by-value-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Wiedergabe eines Formulars nach Wert mithilfe der Webdienst-API {#render-a-form-by-value-using-the-web-service-api}

Wiedergabe eines Formulars nach Wert mithilfe der Forms-API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie Java-Proxyklassen, die die Forms-Dienst-WSDL verwenden.
   * Schließen Sie die Java-Proxy-Klassen in Ihren Klassenpfad ein.

1. Erstellen eines Forms Client-API-Objekts

   Erstellen Sie eine `FormsService` Objekt und legen Sie Authentifizierungswerte fest.

1. Referenzieren des Formularentwurfs

   * Erstellen Sie ein Objekt `java.io.FileInputStream`, indem Sie den Konstruktor verwenden. Übergeben Sie einen string -Wert, der den Speicherort der XDP-Datei angibt.
   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Die `BLOB` -Objekt wird verwendet, um ein mit einem Kennwort verschlüsseltes PDF-Dokument zu speichern.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `java.io.FileInputStream` -Objekt. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `java.io.FileInputStream` Größe des Objekts anhand seiner `available` -Methode.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `java.io.FileInputStream` -Objekt `read` -Methode verwenden und das Byte-Array übergeben.
   * Füllen Sie die `BLOB` -Objekt durch Aufrufen seiner `setBinaryData` -Methode verwenden und das Byte-Array übergeben.

1. Formular nach Wert rendern

   Rufen Sie die `FormsService` -Objekt `renderPDFForm` -Methode verwenden und die folgenden Werte übergeben:

   * Ein leerer Zeichenfolgenwert. (Normalerweise erfordert dieser Parameter einen Zeichenfolgenwert, der den Namen des Formularentwurfs angibt.)
   * A `BLOB` -Objekt, das den Formularentwurf enthält. Normalerweise ist dieser Parameterwert für Daten reserviert, die mit dem Formular zusammengeführt werden.
   * A `PDFFormRenderSpec` -Objekt, das Laufzeitoptionen speichert. Dies ist ein optionaler Parameter, den Sie `null` , wenn Sie keine Laufzeitoptionen festlegen möchten.
   * A `URLSpec` -Objekt, das URI-Werte enthält, die für den Forms-Dienst erforderlich sind.
   * A `java.util.HashMap` -Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter, den Sie `null` , wenn Sie keine Dateien an das Formular anhängen möchten.
   * Ein leeres `com.adobe.idp.services.holders.BLOBHolder` -Objekt, das von der -Methode aufgefüllt wird. Damit wird das wiedergegebene PDF-Formular gespeichert.
   * Ein leeres `javax.xml.rpc.holders.LongHolder` -Objekt, das von der -Methode aufgefüllt wird. (Dieses Argument speichert die Anzahl der Seiten im Formular.)
   * Ein leeres `javax.xml.rpc.holders.StringHolder` -Objekt, das von der -Methode aufgefüllt wird. (Dieses Argument speichert den Gebietsschemawert.)
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

[Rendern von Forms nach Wert](#rendering-forms-by-value)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
