---
title: Arbeiten mit Barcoded Forms
seo-title: Working with barcoded forms
description: Dekodieren Sie Daten aus einem PDF-Formular oder einem Bild, das einen Barcode enthält, mithilfe der Java-API und der Web Service-API.
seo-description: Decode data from a PDF form or an image that contains a barcode using the Java API and Web Service API.
uuid: e56c3c94-384d-401f-b418-dd34cdc57eda
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: eb28ac30-265c-4611-8247-1f4bc826f254
role: Developer
exl-id: 9d459939-a311-4770-84db-f2a4b7869072
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1906'
ht-degree: 2%

---

# Arbeiten mit Barcoded Forms {#working-with-barcoded-forms}

## Über den Barcoded Forms-Dienst {#about-the-barcoded-forms-service}

Der Barcoded Forms-Dienst automatisiert die Erfassung von Daten aus Ausfüllungs- und Druckformularen und integriert erfasste Informationen in die IT-Kernsysteme eines Unternehmens.

Mit dem Barcoded Forms-Dienst können Sie interaktiven PDF forms eindimensionale und zweidimensionale Barcodes hinzufügen. Sie können die mit Strichcode versehenen Formulare dann auf einer Website veröffentlichen oder per E-Mail oder CD verteilen. Wenn ein Benutzer ein mit Strichcode versehenes Formular mit Adobe Reader, Acrobat Professional oder Acrobat Standard ausfüllt, wird der Barcode automatisch aktualisiert, um die vom Benutzer eingegebenen Formulardaten zu kodieren. Der Benutzer kann das Formular elektronisch einreichen oder auf Papier drucken und per Post, Fax oder Hand versenden. Sie können die vom Benutzer eingegebenen Daten später im Rahmen eines automatisierten Workflows extrahieren und die Daten zwischen Genehmigungsprozessen und Geschäftssystemen weiterleiten.

Weitere Informationen zum Barcoded Forms-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Dekodieren von Barcoded Form Data {#decoding-barcoded-form-data}

Sie können die Barcoded Forms-Dienst-API verwenden, um Daten aus einem PDF-Formular oder einem Bild mit einem Barcode zu dekodieren. Das Dekodieren von Formulardaten bedeutet das Extrahieren von Daten, die sich im Barcode befinden. Bevor Daten aus einem PDF-Formular (oder Bild) dekodiert werden können, muss ein Benutzer das Formular mit Daten ausfüllen.

>[!NOTE]
>
>Weitere Informationen zum Barcoded Forms-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

So dekodieren Sie Daten aus einem PDF-Formular:

1. Projektdateien einschließen.
1. Erstellen Sie ein Barcoded formsClient-API-Objekt.
1. Rufen Sie ein PDF-Formular mit Barcodedaten ab.
1. Dekodieren Sie die Daten aus dem PDF-Formular.
1. Konvertieren Sie die Daten in eine XML-Datenquelle.
1. Verarbeiten Sie die dekodierten Daten.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-barcodedforms-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* xercesImpl.jar (unter &lt;install directory=&quot;&quot;>/Adobe/Adobe_Experience_Manager_forms/sdk/client-libs\thirdparty)

Wenn AEM Forms auf einem unterstützten J2EE-Anwendungsserver bereitgestellt wird, der nicht JBOSS ist, müssen Sie adobe-utilities.jar und jbossall-client.jar durch JAR-Dateien ersetzen, die spezifisch für den J2EE-Anwendungsserver sind, auf dem AEM Forms bereitgestellt wird. Informationen zum Speicherort aller AEM Forms-JAR-Dateien finden Sie unter [Einschließen von AEM Forms-Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Client-API-Objekt für Barcoded forms erstellen**

Bevor Sie programmgesteuert einen Barcoded Forms-Dienstvorgang durchführen können, müssen Sie einen Barcoded Forms-Dienstclient erstellen. Wenn Sie die Java-API verwenden, erstellen Sie eine `BarcodedFormsServiceClient` -Objekt. Wenn Sie die Barcoded Forms-Webdienst-API verwenden, erstellen Sie eine `BarcodedFormsServiceService` -Objekt.

**Abrufen eines PDF-Formulars mit Barcode-Daten**

Sie müssen ein PDF-Formular mit einem Barcode abrufen, der mit Benutzerdaten ausgefüllt wurde.

**Daten aus dem PDF-Formular dekodieren**

Nachdem Sie ein PDF-Formular (oder ein Bild) mit einem Barcode erhalten haben, können Sie Daten dekodieren. Der Barcoded Forms-Dienst unterstützt die folgenden Barcodetypen:

* PDF417 Barcodes.
* Datenmatrix-Barcodes.
* QR-Code-Barcodes.
* Codabar-Barcodes.
* Code 128-Barcodes.
* Code 39-Barcodes.
* EAN-13-Barcodes.
* EAN-8-Barcodes.

Die als Hexadezimalwert in der Dekodierungs-API eingegebene Zeichensatzeingabe bedeutet, dass der Barcode-Inhalt als hexadezimale Zeichenfolge kodiert wird. Wenn beispielsweise UTF-8 als Zeichenkodierung im Formular angegeben und im Dekodierungsvorgang &quot;Hex&quot;angegeben ist, wird der Barcode-Inhalt als Hex-Zeichenfolge im &lt; `xb:content`> -Element in der dekodierten Ausgabe. Sie können diesen Hex-Wert konvertieren, um den ursprünglichen Inhalt zu erhalten, indem Sie eine Anwendungslogik in Ihrer Client-Anwendung erstellen.

**Daten in eine XML-Datenquelle konvertieren**

Nachdem Sie Formulardaten dekodiert haben, können Sie sie in XDP- oder XFDF-Daten konvertieren. Angenommen, Sie möchten die Daten in ein anderes Formular importieren. Um die Daten in ein XFA-Formular zu importieren, müssen Sie die Daten in XDP-Daten konvertieren. Weitere Informationen finden Sie unter [Importieren von Formulardaten](/help/forms/developing/importing-exporting-data.md#importing-form-data).

**Dekodierte Daten verarbeiten**

Sie können die konvertierten Daten verarbeiten, um Ihre Geschäftsanforderungen zu erfüllen. Nachdem Sie beispielsweise die Daten dekodiert und konvertiert haben, können Sie sie in einer Datei speichern, in einer Unternehmensdatenbank speichern, ein anderes Formular ausfüllen usw. In diesem Abschnitt wird beschrieben, wie Sie die konvertierten Daten als XML-Datei speichern.

>[!NOTE]
>
>Der Barcoded Forms-Dienst kann Strichcodedaten nicht dekodieren, wenn die Parameter für das Trennzeichen für Zeilen und Felder denselben Wert haben

**Siehe auch**

[Dekodieren von mit Strichcode versehenen Formulardaten mit der Java-API](barcoded-forms.md#decode-barcoded-form-data-using-the-java-api)

[Dekodieren von mit Strichcode versehenen Formulardaten mithilfe der Webdienst-API](barcoded-forms.md#decode-barcoded-form-data-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Dekodieren von mit Strichcode versehenen Formulardaten mit der Java-API {#decode-barcoded-form-data-using-the-java-api}

Dekodieren Sie Formulardaten mithilfe der Barcoded Forms API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien in den Klassenpfad Ihres Java-Projekts ein.

1. Client-API-Objekt für Barcoded forms erstellen

   Erstellen Sie eine `BarcodedFormsServiceClient` -Objekt mithilfe des -Konstruktors und Übergeben eines `ServiceClientFactory` -Objekt, das Verbindungseigenschaften enthält.

1. Abrufen eines PDF-Formulars mit Barcode-Daten

   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, das das PDF-Formular darstellt, das Barcoded-Daten enthält, indem es seinen Konstruktor verwendet und einen Zeichenfolgenwert übergibt, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Daten aus dem PDF-Formular dekodieren

   Dekodieren Sie die Formulardaten, indem Sie die `BarcodedFormsServiceClient` -Objekt `decode` -Methode verwenden und die folgenden Werte übergeben:

   * Die `com.adobe.idp.Document` -Objekt, das das PDF-Formular enthält.
   * A `java.lang.Boolean` -Objekt, das angibt, ob ein PDF417-Barcode dekodiert werden soll.
   * A `java.lang.Boolean` -Objekt, das angibt, ob ein Datenmatrix-Barcode dekodiert werden soll.
   * A `java.lang.Boolean` -Objekt, das angibt, ob ein QR-Code-Barcode dekodiert werden soll.
   * A `java.lang.Boolean` -Objekt, das angibt, ob ein Codabar-Barcode dekodiert werden soll.
   * A `java.lang.Boolean` -Objekt, das angibt, ob ein Code-128-Barcode dekodiert werden soll.
   * A `java.lang.Boolean` -Objekt, das angibt, ob ein Code-39-Barcode dekodiert werden soll.
   * A `java.lang.Boolean` -Objekt, das angibt, ob ein EAN-13-Barcode dekodiert werden soll.
   * A `java.lang.Boolean` -Objekt, das angibt, ob ein EAN-8-Barcode dekodiert werden soll.
   * A `com.adobe.livecycle.barcodedforms.CharSet` enumeration -Wert, der den im Barcode verwendeten Kodierungswert für Zeichensätze angibt.

   Die `decode` -Methode gibt eine `org.w3c.dom.Document` -Objekt, das dekodierte Formulardaten enthält.

1. Daten in eine XML-Datenquelle konvertieren

   Konvertieren Sie die dekodierten Daten durch Aufrufen der `BarcodedFormsServiceClient` -Objekt `extractToXML` -Methode verwenden und die folgenden Werte übergeben:

   * Die `org.w3c.dom.Document` -Objekt, das dekodierte Daten enthält (stellen Sie sicher, dass Sie die `decode` Rückgabewert der Methode).
   * A `com.adobe.livecycle.barcodedforms.Delimiter` Auflistungswert, der das Trennzeichen für die Zeile angibt. Es wird empfohlen, `Delimiter.Carriage_Return`.
   * A `com.adobe.livecycle.barcodedforms.Delimiter` Auflistungswert, der das Feldtrennzeichen angibt. Geben Sie beispielsweise `Delimiter.Tab`.
   * A `com.adobe.livecycle.barcodedforms.XMLFormat` enumeration -Wert, der angibt, ob die Barcodedaten in XDP- oder XFDF-XML-Daten konvertiert werden sollen. Geben Sie beispielsweise `XMLFormat.XDP` , um die Daten in XDP-Daten zu konvertieren.

   >[!NOTE]
   >
   >Geben Sie nicht dieselben Werte für die Parameter &quot;Zeilentrennzeichen&quot;und &quot;Feldtrennzeichen&quot;an.

   Die `extractToXML` -Methode gibt eine `java.util.List` -Objekt, bei dem jedes Element `org.w3c.dom.Document` -Objekt. Für jeden Barcode im Formular gibt es ein eigenes Element. Das heißt, wenn das Formular vier Barcodes enthält, sind vier Elemente in der zurückgegebenen `java.util.List` -Objekt.

1. Dekodierte Daten verarbeiten

   * Iteration durch die `java.util.List` Objekt zum Abrufen `org.w3c.dom.Document` -Objekt, das sich in der Liste befindet.
   * Konvertieren Sie für jedes Element in der Liste die Variable `org.w3c.dom.Document` -Objekt `com.adobe.idp.Document` -Objekt. (Die Anwendungslogik, die eine `org.w3c.dom.Document` Objekt in ein `com.adobe.idp.Document` -Objekt wird im Beispiel Dekodieren von mit Strichcode versehenen Formulardaten mithilfe der Java-API angezeigt).
   * Speichern Sie die XML-Daten als XML-Datei, indem Sie die `com.adobe.idp.Document` -Objekt `copyToFile`und übergeben Sie ein File -Objekt, das die XML-Datei darstellt.

**Siehe auch**

[Schnellstart (SOAP-Modus): Dekodieren von mit Strichcode versehenen Formulardaten mit der Java-API](/help/forms/developing/barcoded-forms-service-java-api.md#quick-start-soap-mode-decoding-barcoded-form-data-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Dekodieren von mit Strichcode versehenen Formulardaten mithilfe der Webdienst-API {#decode-barcoded-form-data-using-the-web-service-api}

Dekodieren Sie Formulardaten mithilfe der Barcoded Forms API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die Barcoded Forms-Dienst-WSDL verwendet. Weitere Informationen finden Sie unter [Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding).
   * Verweisen Sie auf die Microsoft .NET-Clientassembly. Weitere Informationen finden Sie unter &quot;Referenzieren der .NET-Clientassembly&quot;in [Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding).

1. Client-API-Objekt für Barcoded forms erstellen

   Erstellen Sie mithilfe der Microsoft .NET-Client-Assembly, die die WSDL des Barcoded Forms-Dienstes verwendet, eine `BarcodedFormsServiceService` -Objekt durch Aufrufen des Standardkonstruktors.

1. Abrufen eines PDF-Formulars mit Barcode-Daten

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Die `BLOB` -Objekt wird zum Speichern eines PDF-Dokuments verwendet, das einen Barcode enthält.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie die `BLOB` Objekt durch Zuweisen seiner `binaryData` -Eigenschaft mit dem Inhalt des Byte-Arrays.

1. Daten aus dem PDF-Formular dekodieren

   Dekodieren Sie die Formulardaten, indem Sie die `BarcodedFormsServiceService` -Objekt `decode` -Methode verwenden und die folgenden Werte übergeben:

   * Die `BLOB` -Objekt, das das PDF-Formular enthält.
   * A `Boolean` -Objekt, das angibt, ob ein PDF417-Barcode dekodiert werden soll.
   * A `Boolean` -Objekt, das angibt, ob ein Datenmatrix-Barcode dekodiert werden soll.
   * A `Boolean` -Objekt, das angibt, ob ein QR-Code-Barcode dekodiert werden soll.
   * A `Boolean` -Objekt, das angibt, ob ein Codabar-Barcode dekodiert werden soll.
   * A `Boolean` -Objekt, das angibt, ob ein Code-128-Barcode dekodiert werden soll.
   * A `Bolean` -Objekt, das angibt, ob ein Code-39-Barcode dekodiert werden soll.
   * A `Boolean` -Objekt, das angibt, ob ein EAN-13-Barcode dekodiert werden soll.
   * A `Boolean` -Objekt, das angibt, ob ein EAN-8-Barcode dekodiert werden soll.
   * A `CharSet` enumeration -Wert, der den im Barcode verwendeten Kodierungswert für Zeichensätze angibt.

   Die `decode` -Methode gibt einen Zeichenfolgenwert zurück, der dekodierte Formulardaten enthält.

1. Daten in eine XML-Datenquelle konvertieren

   Konvertieren Sie die dekodierten Daten durch Aufrufen der `BarcodedFormsServiceService` -Objekt `extractToXML` -Methode verwenden und die folgenden Werte übergeben:

   * Ein string -Wert, der dekodierte Daten enthält (stellen Sie sicher, dass Sie die `decode` Rückgabewert der Methode).
   * A `Delimiter` Auflistungswert, der das Trennzeichen für die Zeile angibt. Es wird empfohlen, `Delimiter.Carriage_Return`.
   * A `Delimiter` Auflistungswert, der das Feldtrennzeichen angibt. Geben Sie beispielsweise `Delimiter.Tab`.
   * A `XMLFormat` enumeration -Wert, der angibt, ob die Barcodedaten in XDP- oder XFDF-XML-Daten konvertiert werden sollen. Geben Sie beispielsweise `XMLFormat.XDP` , um die Daten in XDP-Daten zu konvertieren.

   >[!NOTE]
   >
   >Geben Sie nicht dieselben Werte für die Parameter &quot;Zeilentrennzeichen&quot;und &quot;Feldtrennzeichen&quot;an.

   Die `extractToXML` -Methode gibt eine `Object` Array, wobei jedes Element `BLOB` -Instanz. Für jeden Barcode im Formular gibt es ein eigenes Element. Das heißt, wenn das Formular vier Barcodes enthält, sind vier Elemente in der zurückgegebenen `Object` Array.

1. Dekodierte Daten verarbeiten

   * Erstellen Sie eine `System.IO.FileStream` -Objekt durch Aufrufen des Konstruktors und Übergeben eines Zeichenfolgenwerts, der den Dateispeicherort des gesicherten PDF-Dokuments darstellt.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt der `BLOB` -Objekt, das von der `encryptPDFUsingPassword` -Methode. Füllen Sie das Byte-Array, indem Sie den Wert der `BLOB` -Objekt `binaryData` Datenelement.
   * Erstellen Sie eine `System.IO.BinaryWriter` -Objekt durch Aufrufen des Konstruktors und Übergeben des `System.IO.FileStream` -Objekt.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `System.IO.BinaryWriter` -Objekt `Write` -Methode verwenden und das Byte-Array übergeben.

**Siehe auch**

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
