---
title: Optimieren der Leistung des Forms-Dienstes
seo-title: Optimizing the Performance of theForms Service
description: Legen Sie Laufzeitoptionen beim Rendern eines Formulars fest und speichern Sie XDP-Dateien im Repository, um die Leistung des Forms-Dienstes zu optimieren.
seo-description: Set run-time options when rendering a form and store XDP files in the repository to optimize the performance of the Forms service.
uuid: 9040c09a-e5d0-432b-b1c5-ad46ab57c4fc
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 9f883483-b81e-42c6-a4a1-eb499dd112e7
role: Developer
exl-id: a6d468cd-2b70-4332-8277-15f8b9fc1329
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1417'
ht-degree: 7%

---

# Leistungsoptimierung des Forms-Dienstes {#optimizing-the-performance-of-theforms-service}

## Leistungsoptimierung des Forms-Dienstes {#optimizing-the-performance-of-the-forms-service}

Beim Rendern eines Formulars können Sie Laufzeitoptionen festlegen, die die Leistung des Forms-Dienstes optimieren. Eine weitere Aufgabe, die Sie zur Verbesserung der Leistung des Forms-Dienstes ausführen können, ist das Speichern von XDP-Dateien im Repository. In diesem Abschnitt wird jedoch nicht beschrieben, wie diese Aufgabe ausgeführt wird. (Siehe [Aufrufen eines Dienstes mithilfe einer Java-Client-Bibliothek](/help/forms/developing/invoking-aem-forms-using-java.md#invoking-a-service-using-a-java-client-library).

>[!NOTE]
>
>Weitere Informationen zum Forms-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

Führen Sie die folgenden Aufgaben aus, um die Leistung des Forms-Dienstes beim Rendern eines Formulars zu optimieren:

1. Projektdateien einschließen.
1. Erstellen Sie ein Forms Client-API-Objekt.
1. Festlegen von Leistungslaufzeitoptionen.
1. Rendern Sie das Formular.
1. Schreiben Sie den Formular-Datenstrom in den Client-Webbrowser.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Forms Client-API-Objekts**

Bevor Sie einen Client-API-Vorgang für den Forms-Dienst programmgesteuert ausführen können, müssen Sie einen Forms-Dienstclient erstellen. Wenn Sie die Java-API verwenden, erstellen Sie eine `FormsServiceClient` -Objekt. Wenn Sie die Forms-Webdienst-API verwenden, erstellen Sie eine `FormsService` -Objekt.

**Festlegen von Leistungslaufzeitoptionen**

Sie können die folgenden Leistungslaufzeitoptionen festlegen, um die Leistung des Forms-Dienstes zu verbessern:

* **Formular-Zwischenspeicherung**: Sie können ein Formular zwischenspeichern, das im Servercache als PDF wiedergegeben wird. Jedes Formular wird zwischengespeichert, nachdem es zum ersten Mal generiert wurde. Wenn bei einem nachfolgenden Render-Vorgang das zwischengespeicherte Formular neuer ist als der Zeitstempel des Formularentwurfs, wird das Formular aus dem Cache abgerufen. Durch das Zwischenspeichern von Formularen verbessern Sie die Leistung des Forms-Dienstes, da der Formularentwurf nicht aus einem Repository abgerufen werden muss.
* Die Wiedergabe von Formularleitfäden (nicht mehr unterstützt) kann länger dauern als die Wiedergabe anderer Transformationstypen. Es wird empfohlen, Formular-Guides (nicht mehr unterstützt) zwischenzuspeichern, um die Leistung zu verbessern.
* **Eigenständige Option**: Wenn der Forms-Dienst keine serverseitigen Berechnungen durchführen muss, können Sie die Eigenschaftsoption auf `true`, wodurch Formulare ohne Statusinformationen wiedergegeben werden. Statusinformationen sind erforderlich, wenn Sie ein interaktives Formular an einen Endbenutzer rendern möchten, der dann Informationen in das Formular eingibt und das Formular an den Forms-Dienst zurücksendet. Der Forms-Dienst führt anschließend eine Berechnung durch und gibt das Formular mit im Formular angezeigten Ergebnissen an den Benutzer zurück. Wenn ein Formular ohne Statusinformationen an den Forms-Dienst zurückgesendet wird, sind nur die XML-Daten verfügbar und serverseitige Berechnungen werden nicht durchgeführt.
* **Linearized PDF**: Eine linearisierte PDF-Datei ist organisiert, um einen effizienten inkrementellen Zugriff in einer Netzwerkumgebung zu ermöglichen. Die PDF-Datei ist in jeder Hinsicht gültig PDF und mit allen vorhandenen Viewern und anderen PDF-Applikationen kompatibel. Das heißt, eine linearisierte PDF kann angezeigt werden, während sie noch heruntergeladen wird.
* Diese Option verbessert nicht die Leistung, wenn ein PDF-Formular auf dem Client wiedergegeben wird.
* **GuideRSL-Option**: Aktiviert die Erstellung des Formular-Guides (veraltet) mithilfe von freigegebenen Laufzeitbibliotheken. Das bedeutet, dass die erste Anfrage eine kleinere SWF-Datei sowie größere gemeinsame Bibliotheken herunterlädt, die im Browsercache gespeichert sind. Weitere Informationen finden Sie unter RSL in der Flex-Dokumentation.
* Sie können auch die Leistung des Forms-Dienstes verbessern, indem Sie ein Formular auf dem Client wiedergeben. (Siehe [Rendern von Forms auf dem Client](/help/forms/developing/rendering-forms-client.md).

**Formular wiedergeben**

Um das Formular nach dem Festlegen von Leistungsoptionen wiederzugeben, verwenden Sie dieselbe Anwendungslogik wie die Wiedergabe eines Formulars ohne Leistungsoptionen.

**Schreiben Sie den Formulardaten-Stream in den Client-Webbrowser**

Nachdem der Forms-Dienst ein Formular wiedergegeben hat, wird ein Formulardatenstream zurückgegeben, den Sie in den Client-Webbrowser schreiben müssen. Beim Schreiben in den Client-Webbrowser ist das Formular für den Benutzer sichtbar.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Forms Service-API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Rendern interaktiver PDF forms](/help/forms/developing/rendering-interactive-pdf-forms.md)

[Rendern von Forms als HTML](/help/forms/developing/rendering-forms-html.md)

[Erstellen von Webanwendungen, die Forms rendern](/help/forms/developing/creating-web-applications-renders-forms.md)

### Leistung mithilfe der Java-API optimieren {#optimize-the-performance-using-the-java-api}

Wiedergabe eines Formulars mit optimierter Leistung mithilfe der Forms API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-forms-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Forms Client-API-Objekts

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie eine `FormsServiceClient` -Objekt durch Verwendung seines Konstruktors und Übergabe des `ServiceClientFactory` -Objekt.

1. Festlegen von Leistungslaufzeitoptionen

   * Erstellen Sie ein Objekt `PDFFormRenderSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Option für den Formular-Cache fest, indem Sie die `PDFFormRenderSpec` -Objekt `setCacheEnabled` Methode und Übergabe `true`.
   * Festlegen der Option &quot;Linearisiert&quot;, indem Sie die `PDFFormRenderSpec` -Objekt `setLinearizedPDF` Methode und Übergabe `true.`

1. Formular wiedergeben

   Rufen Sie die `FormsServiceClient` -Objekt `renderPDFForm` -Methode verwenden und die folgenden Werte übergeben:

   * Ein string -Wert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt.
   * A `com.adobe.idp.Document` -Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie einen leeren `com.adobe.idp.Document` -Objekt.
   * A `PDFFormRenderSpec` -Objekt, das Laufzeitoptionen speichert, um die Leistung zu verbessern.
   * A `URLSpec` -Objekt, das URI-Werte enthält, die für den Forms-Dienst erforderlich sind.
   * A `java.util.HashMap` -Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter, den Sie `null` , wenn Sie keine Dateien an das Formular anhängen möchten.

   Die `renderPDFForm` -Methode gibt eine `FormsResult` -Objekt, das einen Formulardatenstrom enthält, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben Sie den Formulardaten-Stream in den Client-Webbrowser

   * Erstellen Sie eine `javax.servlet.ServletOutputStream` -Objekt, das zum Senden eines Formulardaten-Streams an den Client-Webbrowser verwendet wird.
   * Erstellen Sie eine `com.adobe.idp.Document` -Objekt durch Aufrufen der `FormsResult` object ‘s `getOutputContent` -Methode.
   * Erstellen Sie eine `java.io.InputStream` -Objekt durch Aufrufen der `com.adobe.idp.Document` -Objekt `getInputStream` -Methode.
   * Erstellen Sie ein Byte-Array und füllen Sie es mit dem Formulardatenstream, indem Sie die `InputStream` -Objekt `read`-Methode verwenden und das Byte-Array als Argument übergeben.
   * Rufen Sie die `javax.servlet.ServletOutputStream` -Objekt `write` -Methode zum Senden des Formulardaten-Streams an den Client-Webbrowser. Übergeben Sie das Byte-Array an die `write` -Methode.

**Siehe auch**

[Schnellstart (SOAP-Modus): Leistungsoptimierung mit der Java-API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-optimizing-performance-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Leistung mithilfe der Webdienst-API optimieren {#optimize-the-performance-using-the-web-service-api}

Wiedergabe eines Formulars mit optimierter Leistung mithilfe der Forms-API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie Java-Proxyklassen, die die Forms-Dienst-WSDL verwenden.
   * Schließen Sie die Java-Proxy-Klassen in Ihren Klassenpfad ein.

1. Erstellen eines Forms Client-API-Objekts

   Erstellen Sie eine `FormsService` Objekt und legen Sie Authentifizierungswerte fest.

1. Festlegen von Leistungslaufzeitoptionen

   * Erstellen Sie ein Objekt `PDFFormRenderSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Option für den Formular-Cache fest, indem Sie die `PDFFormRenderSpec` -Objekt `setCacheEnabled` Methode und Übergabe von &quot;true&quot;übergeben.
   * Legen Sie die eigenständige Option fest, indem Sie die `PDFFormRenderSpec` -Objekt `setStandAlone` Methode und Übergabe von &quot;true&quot;übergeben.
   * Festlegen der Option &quot;Linearisiert&quot;, indem Sie die `PDFFormRenderSpec` -Objekt `setLinearizedPDF` Methode und Übergabe von &quot;true&quot;übergeben.

1. Formular wiedergeben

   Rufen Sie die `FormsService` -Objekt `renderPDFForm` -Methode verwenden und die folgenden Werte übergeben:

   * Ein string -Wert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt.
   * A `BLOB` -Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie `null`.
   * A `PDFFormRenderSpecc` -Objekt, das Laufzeitoptionen speichert.
   * A `URLSpec` -Objekt, das URI-Werte enthält, die für den Forms-Dienst erforderlich sind.
   * A `java.util.HashMap` -Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter, den Sie `null` , wenn Sie keine Dateien an das Formular anhängen möchten.
   * Ein leeres `com.adobe.idp.services.holders.BLOBHolder` -Objekt, das von der -Methode aufgefüllt wird. Damit wird das wiedergegebene PDF-Formular gespeichert.
   * Ein leeres `javax.xml.rpc.holders.LongHolder` -Objekt, das von der -Methode aufgefüllt wird. (Dieses Argument speichert die Anzahl der Seiten im Formular).
   * Ein leeres `javax.xml.rpc.holders.StringHolder` -Objekt, das von der -Methode aufgefüllt wird. (Dieses Argument speichert den Gebietsschemawert).
   * Ein leeres `com.adobe.idp.services.holders.FormsResultHolder` -Objekt, das die Ergebnisse dieses Vorgangs enthält.

   Die `renderPDFForm` -Methode füllt die `com.adobe.idp.services.holders.FormsResultHolder` -Objekt, das als letzter Argumentwert mit einem Formulardatenstream übergeben wird, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben Sie den Formulardaten-Stream in den Client-Webbrowser

   * Erstellen Sie eine `FormResult` -Objekt durch Abrufen des Werts der `com.adobe.idp.services.holders.FormsResultHolder` -Objekt `value` Datenelement.
   * Erstellen Sie eine `javax.servlet.ServletOutputStream` -Objekt, das zum Senden eines Formulardaten-Streams an den Client-Webbrowser verwendet wird.
   * Erstellen Sie eine `BLOB` -Objekt, das Formulardaten enthält, durch Aufrufen der `FormsResult` -Objekt `getOutputContent` -Methode.
   * Erstellen Sie ein Byte-Array und füllen Sie es durch Aufrufen der `BLOB` -Objekt `getBinaryData` -Methode. Diese Aufgabe weist den Inhalt des `FormsResult` -Objekt zum Byte-Array hinzu.
   * Rufen Sie die `javax.servlet.http.HttpServletResponse` -Objekt `write` -Methode zum Senden des Formulardaten-Streams an den Client-Webbrowser. Übergeben Sie das Byte-Array an die `write` -Methode.

**Siehe auch**

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
