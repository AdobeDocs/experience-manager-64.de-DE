---
title: Arbeiten mit PDF/A-Dokumenten
seo-title: Working with PDF/A Documents
description: Verwenden Sie den DocConverter-Dienst, um zu ermitteln, ob ein PDF-Dokument ein PDF/A-Dokument ist, und um PDF-Dokumente in PDF/A-Dokumente zu konvertieren.
seo-description: Use the  DocConverter service to determine if a PDF document is a PDF/A document and convert PDF documents to PDF/A documents.
uuid: c258d253-068a-4412-955a-21d8a4792d6f
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 1e6cc554-aef1-463c-906b-634b80a27917
role: Developer
exl-id: fbf6c225-5351-4589-97d3-9faf9c5939bc
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '2358'
ht-degree: 7%

---

# Arbeiten mit PDF/A-Dokumenten {#working-with-pdf-a-documents}

**Über den DocConverter-Dienst**

Der DocConverter-Dienst kann PDF-Dokumente in PDA/A-Dokumente konvertieren. Sie können diese Aufgaben mit diesem Dienst ausführen:

* Konvertieren Sie PDF-Dokumente in PDF/A-Dokumente. (Siehe [Konvertieren von Dokumenten in PDF/A-Dokumente](pdf-a-documents.md#converting-documents-to-pdf-a-documents).
* Stellen Sie fest, ob PDF-Dokumente PDF/A-Dokumente sind. (Siehe [Programmatische Bestimmung der PDF/A-Kompatibilität](pdf-a-documents.md#programmatically-determining-pdf-a-compliancy).

>[!NOTE]
>
>Weitere Informationen zum DocConverter-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Konvertieren von Dokumenten in PDF/A-Dokumente {#converting-documents-to-pdf-a-documents}

Sie können den DocConverter-Dienst verwenden, um ein PDF-Dokument in ein PDF/A-Dokument zu konvertieren. Da PDF/A ein Archivierungsformat für die langfristige Beibehaltung des Dokumentinhalts ist, werden alle Schriftarten eingebettet und die Datei unkomprimiert. PDF/A-Dokumente sind daher in der Regel größer als normale PDF-Dokumente. Außerdem enthalten PDF/A-Dokumente keine Audio- und Videoinhalte. Bevor Sie ein PDF-Dokument in ein PDF/A-Dokument konvertieren, stellen Sie sicher, dass das PDF-Dokument kein PDF/A-Dokument ist.

Die PDF/A-1-Spezifikation besteht aus zwei Konformitätsstufen, nämlich A und B. Der Hauptunterschied zwischen den beiden besteht in Bezug auf die Unterstützung der logischen Struktur (Barrierefreiheit), die nicht für Konformitätsstufe B erforderlich ist. Unabhängig von der Konformitätsstufe bestimmt PDF/A-1, dass alle Schriftarten in das generierte PDF/A-Dokument eingebettet sind. Derzeit wird nur PDF/A-1b bei der Validierung (und Konvertierung) unterstützt.

PDF/A ist zwar der Standard für die Archivierung von PDF-Dokumenten, es ist jedoch nicht erforderlich, dass PDF/A zur Archivierung verwendet wird, wenn ein Standarddokument für die PDF den Anforderungen Ihres Unternehmens entspricht. Der PDF/A-Standard dient der Erstellung einer PDF-Datei, die für die langfristige Archivierung und Dokumentenerhaltung bestimmt ist.

>[!NOTE]
>
>Weitere Informationen zum DocConverter-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

Gehen Sie wie folgt vor, um ein PDF-Dokument in ein PDF/A-Dokument zu konvertieren:

1. Projektdateien einschließen.
1. Erstellen eines DocConvert-Clients
1. Referenzieren Sie ein PDF-Dokument, das in ein PDF/A-Dokument konvertiert werden soll.
1. Festlegen von Tracking-Informationen.
1. Konvertieren Sie das Dokument.
1. Speichern Sie das PDF/A-Dokument.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-docconverter-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

Informationen zum Speicherort dieser JAR-Dateien finden Sie unter [Einschließen von AEM Forms-Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines DocConvert-Clients**

Bevor Sie einen DocConverter-Vorgang programmgesteuert ausführen können, müssen Sie einen DocConverter-Client erstellen. Wenn Sie die Java-API verwenden, erstellen Sie eine `DocConverterServiceClient` -Objekt. Wenn Sie die DocConverter-Webdienst-API verwenden, erstellen Sie eine `DocConverterServiceService` -Objekt.

**Referenzieren eines PDF-Dokuments zur Konvertierung in ein PDF/A-Dokument**

Rufen Sie ein PDF-Dokument ab, das in ein PDF/A-Dokument konvertiert werden soll. Wenn Sie versuchen, ein PDF-Dokument, z. B. ein Acrobat-Formular, in ein PDF/A-Dokument zu konvertieren, wird eine Ausnahme verursacht.

**Tracking-Informationen festlegen**

Sie können eine Laufzeitoption festlegen, die bestimmt, wie viele Informationen während des Konvertierungsprozesses verfolgt werden. Das heißt, Sie können neun verschiedene Ebenen festlegen, die angeben, wie viele Informationen der DocConverter-Dienst verfolgt, wenn ein PDF-Dokument in ein PDF/A-Dokument konvertiert wird.

**Dokument konvertieren**

Nachdem Sie den DocConverter-Dienst-Client erstellt haben, referenzieren Sie das PDF-Dokument zum Konvertieren und legen Sie die Laufzeitoption fest, die angibt, wie viele Informationen verfolgt werden, und konvertieren Sie das PDF-Dokument in ein PDF/A-Dokument.

**PDF/A-Dokument speichern**

Sie können das PDF/A-Dokument als PDF-Datei speichern.

**Siehe auch**

[Konvertieren von Dokumenten in PDF/A-Dokumente mithilfe der Java-API](pdf-a-documents.md#convert-documents-to-pdf-a-documents-using-the-java-api)

[Konvertieren von Dokumenten in PDF/A-Dokumente mithilfe der Webdienst-API](pdf-a-documents.md#convert-documents-to-pdf-a-documents-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Programmatische Bestimmung der PDF/A-Kompatibilität](pdf-a-documents.md#programmatically-determining-pdf-a-compliancy)

### Konvertieren von Dokumenten in PDF/A-Dokumente mithilfe der Java-API {#convert-documents-to-pdf-a-documents-using-the-java-api}

Konvertieren Sie ein PDF-Dokument mithilfe der Java-API in ein PDF/A-Dokument:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-docConverter-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines DocConvert-Clients

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `DocConverterServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Referenzieren eines PDF-Dokuments zur Konvertierung in ein PDF/A-Dokument

   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, das das zu konvertierende PDF-Dokument mithilfe des Konstruktors darstellt und einen Zeichenfolgenwert übergibt, der den Speicherort der PDF-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Tracking-Informationen festlegen

   * Erstellen Sie ein Objekt `PDFAConversionOptionSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Tracking-Ebene für Informationen fest, indem Sie die `PDFAConversionOptionSpec` -Objekt `setLogLevel` -Methode verwenden und einen string -Wert übergeben, der die Tracking-Ebene angibt. Übergeben Sie beispielsweise den Wert `FINE`. Weitere Informationen zu den verschiedenen Werten finden Sie unter `setLogLevel` -Methode [AEM Forms API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

1. Dokument konvertieren

   Konvertieren Sie das PDF-Dokument in ein PDF/A-Dokument, indem Sie die `DocConverterServiceClient` -Objekt `toPDFA` -Methode verwenden und die folgenden Werte übergeben:

   * Die `com.adobe.idp.Document` -Objekt, das das zu konvertierende PDF-Dokument enthält
   * Die `PDFAConversionOptionSpec` Objekt, das Tracking-Informationen angibt

   Die `toPDFA` -Methode gibt eine `PDFAConversionResult` -Objekt, das das PDF/A-Dokument enthält.

1. PDF/A-Dokument speichern

   * Rufen Sie das PDF/A-Dokument ab, indem Sie die `PDFAConversionResult` -Objekt `getPDFA` -Methode. Diese Methode gibt eine `com.adobe.idp.Document` -Objekt, das das PDF/A-Dokument darstellt.
   * Erstellen Sie eine `java.io.File` -Objekt, das die PDF/A-Datei darstellt. Stellen Sie sicher, dass die Dateinamenerweiterung .pdf lautet.
   * Füllen Sie die Datei mit PDF/A-Daten, indem Sie die `com.adobe.idp.Document` -Objekt `copyToFile` -Methode und Übergabe der `java.io.File` -Objekt.

**Siehe auch**

[Arbeiten mit PDF/A-Dokumenten](pdf-a-documents.md#working-with-pdf-a-documents)

[Schnellstart (SOAP-Modus): Konvertieren eines Dokuments in ein PDF/A-Dokument mithilfe der Java-API](/help/forms/developing/docconverter-service-java-api-quick.md#quick-start-soap-mode-converting-a-document-to-a-pdf-a-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Konvertieren von Dokumenten in PDF/A-Dokumente mithilfe der Webdienst-API {#convert-documents-to-pdf-a-documents-using-the-web-service-api}

Konvertieren Sie ein PDF-Dokument mithilfe der DocConverter-API (Webdienst) in ein PDF/A-Dokument:

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die DocConverter-WSDL verwendet.
   * Verweisen Sie auf die Microsoft .NET-Clientassembly.

1. Erstellen eines DocConvert-Clients

   * Erstellen Sie mithilfe der Microsoft .NET-Client-Assembly eine `DocConverterServiceService` -Objekt durch Aufrufen des Standardkonstruktors.
   * Legen Sie die `DocConverterServiceService` -Objekt `Credentials` Datenelement mit `System.Net.NetworkCredential` -Wert, der den Benutzernamen und den Kennwortwert angibt.

1. Referenzieren eines PDF-Dokuments zur Konvertierung in ein PDF/A-Dokument

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Die `BLOB` -Objekt wird zum Speichern des PDF-Dokuments verwendet, das in ein PDF/A-Dokument konvertiert wird.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt durch Aufrufen des Konstruktors und Übergeben eines Zeichenfolgenwerts, der den Dateispeicherort des PDF-Dokuments und den Modus zum Öffnen der Datei darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie die `BLOB` Objekt durch Zuweisen seiner `binaryData` -Eigenschaft mit dem Inhalt des Byte-Arrays.

1. Tracking-Informationen festlegen

   * Erstellen Sie ein Objekt `PDFAConversionOptionSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Tracking-Ebene für Informationen fest, indem Sie einen Wert zuweisen, der die Tracking-Ebene der `PDFAConversionOptionSpec` -Objekt `logLevel` Datenelement. Weisen Sie beispielsweise den Wert zu `FINE` zu diesem Datenelement hinzu.

1. Dokument konvertieren

   Konvertieren Sie das PDF-Dokument in ein PDF/A-Dokument, indem Sie die `DocConverterServiceService` -Objekt `toPDFA` -Methode verwenden und die folgenden Werte übergeben:

   * Die `BLOB` -Objekt, das das zu konvertierende PDF-Dokument enthält
   * Die `PDFAConversionOptionSpec` Objekt, das Tracking-Informationen angibt

   Die `toPDFA` -Methode gibt eine `PDFAConversionResult` -Objekt, das das PDF/A-Dokument enthält.

1. PDF/A-Dokument speichern

   * Erstellen Sie eine `BLOB` -Objekt, das das PDF/A-Dokument speichert, indem der Wert des `PDFAConversionResult` -Objekt `PDFADocument` Datenelement.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `BLOB` -Objekt, das mithilfe der `PDFAConversionResult` -Objekt. Füllen Sie das Byte-Array, indem Sie den Wert der `BLOB` -Objekt `binaryData` Datenelement.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt durch Aufrufen des Konstruktors und Übergeben eines Zeichenfolgenwerts, der den Dateispeicherort des PDF/A-Dokuments darstellt.
   * Erstellen Sie eine `System.IO.BinaryWriter` -Objekt durch Aufrufen des Konstruktors und Übergeben des `System.IO.FileStream` -Objekt.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `System.IO.BinaryWriter` -Objekt `Write` -Methode verwenden und das Byte-Array übergeben.

**Siehe auch**

[Arbeiten mit PDF/A-Dokumenten](pdf-a-documents.md#working-with-pdf-a-documents)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Erstellen einer .NET-Client-Assembly, die die Base64-Kodierung verwendet](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)

## Programmatische Bestimmung der PDF/A-Kompatibilität {#programmatically-determining-pdf-a-compliancy}

Mit dem DocConverter-Dienst können Sie ermitteln, ob ein PDF-Dokument PDF/A-konform ist. Informationen zu einem PDF/A-Dokument und zum Konvertieren eines PDF-Dokuments in ein PDF/A-Dokument finden Sie unter [Konvertieren von Dokumenten in PDF/A-Dokumente](pdf-a-documents.md#converting-documents-to-pdf-a-documents).

>[!NOTE]
>
>Weitere Informationen zum DocConverter-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-1}

Um die PDF/A-Kompatibilität zu ermitteln, führen Sie die folgenden Schritte aus:

1. Projektdateien einschließen.
1. Erstellen eines DocConvert-Clients
1. Referenzieren Sie ein PDF-Dokument, das zur Bestimmung der PDF/A-Kompatibilität verwendet wird.
1. Legen Sie Laufzeitoptionen fest.
1. Rufen Sie Informationen zum PDF-Dokument ab.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-docconverter-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

Informationen zum Speicherort dieser JAR-Dateien finden Sie unter [Einschließen von AEM Forms-Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines DocConvert-Clients**

Bevor Sie einen DocConverter-Vorgang programmgesteuert ausführen können, müssen Sie einen DocConverter-Client erstellen. Wenn Sie die Java-API verwenden, erstellen Sie eine `DocConverterServiceClient` -Objekt. Wenn Sie die DocConverter-Webdienst-API verwenden, erstellen Sie eine `DocConverterServiceService` -Objekt.

**Referenzieren eines PDF-Dokuments zur Bestimmung der PDF/A-Kompatibilität**

Ein PDF-Dokument muss referenziert und an den DocConverter-Dienst übergeben werden, um festzustellen, ob das PDF-Dokument PDF/A-kompatibel ist.

**Laufzeitoptionen festlegen**

Sie können eine Laufzeitoption festlegen, die bestimmt, wie viele Informationen während des Konvertierungsprozesses verfolgt werden. Das heißt, Sie können neun verschiedene Ebenen festlegen, die angeben, wie viele Informationen der DocConverter-Dienst beim Konvertieren eines PDF-Dokuments in ein PDF/A-Dokument verfolgt.

**Informationen zum PDF-Dokument abrufen**

Nachdem Sie den DocConverter-Dienstclient erstellt, auf das PDF-Dokument verwiesen und die Laufzeitoptionen festgelegt haben, können Sie bestimmen, ob das PDF-Dokument ein PDF/A-kompatibles Dokument ist.

**Siehe auch**

[PDF/A-Kompatibilität mithilfe der Java-API ermitteln](pdf-a-documents.md#determine-pdf-a-compliancy-using-the-java-api)

[PDF/A-Kompatibilität mithilfe der Webdienst-API ermitteln](pdf-a-documents.md#determine-pdf-a-compliancy-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### PDF/A-Kompatibilität mithilfe der Java-API ermitteln {#determine-pdf-a-compliancy-using-the-java-api}

Bestimmen Sie mithilfe der Java-API die Kompatibilität von PDF/A:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-docConverter-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines DocConvert-Clients

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `DocConverterServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Referenzieren eines PDF-Dokuments zur Bestimmung der PDF/A-Kompatibilität

   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, das das zu konvertierende PDF-Dokument mithilfe des Konstruktors darstellt und einen Zeichenfolgenwert übergibt, der den Speicherort der PDF-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Laufzeitoptionen festlegen

   * Erstellen Sie ein Objekt `PDFAValidationOptionSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Konformitätsstufe fest, indem Sie die `PDFAValidationOptionSpec` -Objekt `setCompliance` Methode und Übergabe `PDFAValidationOptionSpec.Compliance.PDFA_1B`.
   * Legen Sie die Tracking-Ebene für Informationen fest, indem Sie die `PDFAValidationOptionSpec` -Objekt `setLogLevel` -Methode verwenden und einen string -Wert übergeben, der die Tracking-Ebene angibt. Übergeben Sie beispielsweise den Wert `FINE`. Weitere Informationen zu den verschiedenen Werten finden Sie unter `setLogLevel` -Methode [AEM Forms API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

1. Informationen zum PDF-Dokument abrufen

   PDF/A-Kompatibilität durch Aufrufen der `DocConverterServiceClient` -Objekt `isPDFA` -Methode verwenden und die folgenden Werte übergeben:

   * Die `com.adobe.idp.Document` -Objekt, das das PDF-Dokument enthält.
   * Die `PDFAValidationOptionSpec` -Objekt, das Laufzeitoptionen angibt.

   Die `isPDFA` -Methode gibt eine `PDFAValidationResult` -Objekt, das die Ergebnisse dieses Vorgangs enthält.

**Siehe auch**

[Arbeiten mit PDF/A-Dokumenten](pdf-a-documents.md#working-with-pdf-a-documents)

[Schnellstart (SOAP-Modus): Bestimmen der PDF/A-Kompatibilität mithilfe der Java-API](/help/forms/developing/docconverter-service-java-api-quick.md#quick-start-soap-mode-determining-pdf-a-compliancy-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### PDF/A-Kompatibilität mithilfe der Webdienst-API ermitteln {#determine-pdf-a-compliancy-using-the-web-service-api}

Bestimmen Sie mithilfe der Webdienst-API die Kompatibilität von PDF/A:

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die DocConverter-WSDL verwendet.
   * Verweisen Sie auf die Microsoft .NET-Clientassembly.

1. Erstellen eines DocConvert-Clients

   * Erstellen Sie mithilfe der Microsoft .NET-Client-Assembly eine `DocConverterServiceService` -Objekt durch Aufrufen des Standardkonstruktors.
   * Legen Sie die `DocConverterServiceService` -Objekt `Credentials` Datenelement mit `System.Net.NetworkCredential` -Wert, der den Benutzernamen und den Kennwortwert angibt.

1. Referenzieren eines PDF-Dokuments zur Bestimmung der PDF/A-Kompatibilität

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Die `BLOB` -Objekt wird zum Speichern des PDF-Dokuments verwendet, das in ein PDF/A-Dokument konvertiert wird.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt durch Aufrufen des Konstruktors und Übergeben eines Zeichenfolgenwerts, der den Dateispeicherort des PDF-Dokuments und den Modus zum Öffnen der Datei darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie die `BLOB` Objekt durch Zuweisen seiner `binaryData` -Eigenschaft mit dem Inhalt des Byte-Arrays.

1. Laufzeitoptionen festlegen

   * Erstellen Sie ein Objekt `PDFAValidationOptionSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Konformitätsstufe fest, indem Sie die `PDFAValidationOptionSpec` -Objekt `compliance` Datenelement mit dem Wert `PDFAConversionOptionSpec_Compliance.PDFA_1B`.
   * Legen Sie die Tracking-Ebene für Informationen fest, indem Sie die `PDFAValidationOptionSpec` -Objekt `resultLevel` Datenelement mit dem Wert `PDFAValidationOptionSpec_ResultLevel.DETAILED`.

1. Informationen zum PDF-Dokument abrufen

   PDF/A-Kompatibilität durch Aufrufen der `DocConverterServiceService` -Objekt `isPDFA` -Methode verwenden und die folgenden Werte übergeben:

   * Die `BLOB` -Objekt, das das PDF-Dokument enthält.
   * Die `PDFAValidationOptionSpec` -Objekt, das Laufzeitoptionen enthält.

   Die `isPDFA` -Methode gibt eine `PDFAValidationResult` -Objekt, das die Ergebnisse dieses Vorgangs enthält.

**Siehe auch**

[Arbeiten mit PDF/A-Dokumenten](pdf-a-documents.md#working-with-pdf-a-documents)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Erstellen einer .NET-Client-Assembly, die die Base64-Kodierung verwendet](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)
