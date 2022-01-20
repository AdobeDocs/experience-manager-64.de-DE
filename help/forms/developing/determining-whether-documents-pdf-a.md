---
title: Bestimmen, ob Dokumente PDF/A-konform sind
seo-title: Determining Whether Documents Are PDF/A-Compliant
description: Verwenden Sie den Assembler-Dienst, um mithilfe der Java-API und der Web Service-API zu ermitteln, ob ein PDF-Dokument PDF/A-kompatibel ist.
seo-description: Use the Assembler service to determine if a PDF document is PDF/A-compliant using the Java API and Web Service API.
uuid: 4e9d8c8f-2153-411b-9c4b-2d14b3c8f4bb
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: c429d6e1-7847-43c8-bf75-cb0078dbb9d5
role: Developer
exl-id: fa9d0720-f4bf-4933-ae63-c24bb835cc60
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '2082'
ht-degree: 4%

---

# Bestimmen, ob Dokumente PDF/A-konform sind {#determining-whether-documents-are-pdf-a-compliant}

Mithilfe des Assembler-Dienstes können Sie feststellen, ob ein PDF-Dokument PDF/A-kompatibel ist. Ein PDF/A-Dokument existiert als Archivformat, das für die Langzeitarchivierung des Dokumentinhalts vorgesehen ist. Die Schriftarten werden im Dokument eingebettet und die Datei bleibt unkomprimiert. PDF/A-Dokumente sind daher in der Regel größer als normale PDF-Dokumente. Außerdem enthalten PDF/A-Dokumente keine Audio- und Videoinhalte.

Die PDF/A-1-Spezifikation besteht aus zwei Konformitätsstufen, nämlich A und B. Der Hauptunterschied zwischen den beiden Ebenen ist die logische Strukturunterstützung (Barrierefreiheit), die nicht für Konformitätsstufe B erforderlich ist. Unabhängig von der Konformitätsstufe bestimmt PDF/A-1, dass alle Schriftarten in das generierte PDF/A-Dokument eingebettet sind. Derzeit wird nur PDF/A-1b bei der Validierung (und Konvertierung) unterstützt.

Angenommen, für diese Diskussion wird das folgende DDX-Dokument verwendet.

```as3
 <?xml version="1.0" encoding="UTF-8"?> 
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/"> 
         <DocumentInformation source="Loan.pdf" result="Loan_result.xml"> 
         <PDFAValidation compliance="PDF/A-1b" resultLevel="Detailed"                       ignoreUnusedResources="true" allowCertificationSignatures="true" /> 
     </DocumentInformation> 
 </DDX>
```

In diesem DDX-Dokument wird die `DocumentInformation` -Element weist den Assembler-Dienst an, Informationen zum PDF-Eingabedokument zurückzugeben. Innerhalb der `DocumentInformation` -Element, das `PDFAValidation` -Element weist den Assembler-Dienst an, anzugeben, ob das PDF-Eingabedokument PDF/A-kompatibel ist.

Der Assembler-Dienst gibt Informationen zurück, die angeben, ob das PDF-Eingabedokument in einem XML-Dokument, das ein `PDFAConformance` -Element. Wenn das PDF-Eingabedokument PDF/A-kompatibel ist, wird der Wert der `PDFAConformance` -Element `isCompliant` Attribut ist `true`. Wenn das PDF-Dokument nicht PDF/A-kompatibel ist, wird der Wert der `PDFAConformance` -Element `isCompliant` Attribut ist `false`.

>[!NOTE]
>
>Da das in diesem Abschnitt angegebene DDX-Dokument eine `DocumentInformation` -Element gibt der Assembler-Dienst XML-Daten anstelle eines PDF-Dokuments zurück. Das heißt, der Assembler-Dienst stellt kein PDF-Dokument zusammen oder zerlegt es. Es werden Informationen zum Eingabe-PDF-Dokument in einem XML-Dokument zurückgegeben.

>[!NOTE]
>
>Weitere Informationen zum Assembler-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Weitere Informationen zu einem DDX-Dokument finden Sie unter [Assembler-Dienst und DDX-Referenz](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Zusammenfassung der Schritte {#summary-of-steps}

Um festzustellen, ob ein PDF-Dokument PDF/A-kompatibel ist, führen Sie die folgenden Schritte aus:

1. Projektdateien einschließen.
1. Erstellen Sie einen PDF Assembler-Client.
1. Referenzieren Sie ein vorhandenes DDX-Dokument.
1. Referenzieren Sie ein PDF-Dokument, das zur Bestimmung der PDF/A-Kompatibilität verwendet wird.
1. Legen Sie Laufzeitoptionen fest.
1. Rufen Sie Informationen zum PDF-Dokument ab.
1. Speichern Sie das zurückgegebene XML-Dokument.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Wenn AEM Forms auf einem anderen unterstützten J2EE-Anwendungsserver als JBoss bereitgestellt wird, müssen Sie die Dateien &quot;adobe-utilities.jar&quot;und &quot;jbossall-client.jar&quot;durch JAR-Dateien ersetzen, die für den J2EE-Anwendungsserver spezifisch sind, auf dem AEM Forms bereitgestellt wird. Informationen zum Speicherort aller AEM Forms-JAR-Dateien finden Sie unter [Einschließen von AEM Forms-Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**PDF Assembler-Client erstellen**

Bevor Sie einen Assembler-Vorgang programmgesteuert ausführen können, müssen Sie einen Assembler-Dienst-Client erstellen.

**Vorhandenes DDX-Dokument referenzieren**

Es muss auf ein DDX-Dokument verwiesen werden, um einen Assembler-Dienstvorgang durchzuführen. Um festzustellen, ob ein PDF-Eingabedokument PDF/A-kompatibel ist, stellen Sie sicher, dass das DDX-Dokument die `PDFAValidation` -Element in einer `DocumentInformation` -Element. Die `PDFAValidation` -Element weist den Assembler-Dienst an, ein XML-Dokument zurückzugeben, das angibt, ob das PDF-Eingabedokument PDF/A-kompatibel ist.

**Referenzieren eines PDF-Dokuments zur Bestimmung der PDF/A-Kompatibilität**

Ein PDF-Dokument muss referenziert und an den Assembler-Dienst übergeben werden, um festzustellen, ob das PDF-Dokument PDF/A-kompatibel ist.

**Laufzeitoptionen festlegen**

Sie können Laufzeitoptionen festlegen, die das Verhalten des Assembler-Dienstes während der Ausführung eines Auftrags steuern. Sie können beispielsweise eine Option festlegen, mit der der Assembler-Dienst angewiesen wird, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt. Informationen zu den Laufzeitoptionen, die Sie festlegen können, finden Sie unter `AssemblerOptionSpec` Klassenreferenz in [AEM Forms API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Informationen zum PDF-Dokument abrufen**

Nachdem Sie den Assembler-Dienst-Client erstellt haben, auf das DDX-Dokument verweisen, auf ein interaktives PDF-Dokument verweisen und Laufzeitoptionen festlegen, können Sie die `invokeDDX` Vorgang. Da das DDX-Dokument die `DocumentInformation` -Element gibt der Assembler-Dienst XML-Daten anstelle eines PDF-Dokuments zurück.

**Das zurückgegebene XML-Dokument speichern**

Das vom Assembler-Dienst zurückgegebene XML-Dokument gibt an, ob das PDF-Eingabedokument PDF/A-kompatibel ist. Wenn das PDF-Eingabedokument beispielsweise nicht PDF/A-kompatibel ist, gibt der Assembler-Dienst ein XML--Dokument zurück, das das folgende Element enthält:

```as3
 <PDFAConformance isCompliant="false" compliance="PDF/A-1b" resultLevel="Detailed" ignoreUnusedResources="true" allowCertificationSignatures="true">
```

Speichern Sie das XML-Dokument als XML-Datei, damit Sie die Datei öffnen und die Ergebnisse anzeigen können.

**Siehe auch**

[Bestimmen Sie mithilfe der Java-API, ob ein Dokument mit PDF/A kompatibel ist.](/help/forms/developing/determining-whether-documents-pdf-a.md#determine-whether-a-document-is-pdf-a-compliant-using-the-java-api)

[Ermitteln Sie mithilfe der Webdienst-API, ob ein Dokument PDF/A-kompatibel ist.](/help/forms/developing/determining-whether-documents-pdf-a.md#determine-whether-a-document-is-pdf-a-compliant-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Programmgesteuertes Zusammenstellen von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Bestimmen Sie mithilfe der Java-API, ob ein Dokument mit PDF/A kompatibel ist. {#determine-whether-a-document-is-pdf-a-compliant-using-the-java-api}

Stellen Sie mithilfe der Assembler-Dienst-API (Java) fest, ob ein PDF-Dokument PDF/A-kompatibel ist:

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-assembler-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie eine `AssemblerServiceClient` -Objekt durch Verwendung seines Konstruktors und Übergabe des `ServiceClientFactory` -Objekt.

1. Referenzieren Sie ein vorhandenes DDX-Dokument.

   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, das das DDX-Dokument darstellt, indem es seinen Konstruktor verwendet und einen string -Wert übergibt, der den Speicherort der DDX-Datei angibt. Um festzustellen, ob das PDF-Dokument PDF/A-kompatibel ist, stellen Sie sicher, dass das DDX-Dokument die `PDFAValidation` -Element, das in einer `DocumentInformation` -Element.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Referenzieren Sie ein PDF-Dokument, das zur Bestimmung der PDF/A-Kompatibilität verwendet wird.

   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, indem Sie seinen Konstruktor verwenden und den Speicherort eines PDF-Dokuments übergeben, das zum Ermitteln der PDF/A-Kompatibilität verwendet wird.
   * Erstellen Sie eine `com.adobe.idp.Document` -Objekt durch Verwendung seines Konstruktors und Übergabe des `java.io.FileInputStream` -Objekt, das das PDF-Dokument enthält.
   * Erstellen Sie eine `java.util.Map` -Objekt, das zum Speichern des Eingabe-PDF-Dokuments mithilfe eines `HashMap` -Konstruktor.
   * Fügen Sie dem `java.util.Map` -Objekt durch Aufrufen seiner `put` -Methode verwenden und die folgenden Argumente übergeben:

      * Ein string -Wert, der den Schlüsselnamen darstellt. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen Quellelements übereinstimmen. Beispielsweise lautet der Wert des Quellelements im DDX-Dokument, das in diesem Abschnitt eingeführt wird, Loan.pdf.
      * A `com.adobe.idp.Document` -Objekt, das das PDF-Eingabedokument enthält.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie eine `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen mithilfe seines Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie eine Methode aufrufen, die zum `AssemblerOptionSpec` -Objekt. Um beispielsweise den Assembler-Dienst anzuweisen, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt, rufen Sie die `AssemblerOptionSpec` -Objekt `setFailOnError` -Methode und -übergabe `false`.

1. Rufen Sie Informationen zum PDF-Dokument ab.

   Rufen Sie die `AssemblerServiceClient` -Objekt `invokeDDX` -Methode verwenden und die folgenden erforderlichen Werte übergeben:

   * A `com.adobe.idp.Document` -Objekt, das das zu verwendende DDX-Dokument darstellt
   * A `java.util.Map` -Objekt, das die Eingabedatei enthält, mit der die PDF/A-Kompatibilität ermittelt wird.
   * A `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` -Objekt, das die Laufzeitoptionen angibt

   Die `invokeDDX` -Methode gibt eine `com.adobe.livecycle.assembler.client.AssemblerResult` -Objekt, das XML-Daten enthält, die angeben, ob das PDF-Eingabedokument PDF/A-kompatibel ist.

1. Speichern Sie das zurückgegebene XML-Dokument.

   So rufen Sie XML-Daten ab, die angeben, ob das Eingabedokument ein PDF/A-PDF-Dokument ist:

   * Rufen Sie die `AssemblerResult` -Objekt `getDocuments` -Methode. Dadurch wird eine `java.util.Map` -Objekt.
   * Iteration durch die `java.util.Map` -Objekt, bis Sie das Ergebnis finden `com.adobe.idp.Document` -Objekt.
   * Rufen Sie die `com.adobe.idp.Document` -Objekt `copyToFile` -Methode, um das XML-Dokument zu extrahieren. Stellen Sie sicher, dass Sie die XML-Daten als XML-Datei speichern.

**Siehe auch**

[Schnellstart (SOAP-Modus): Bestimmen, ob ein Dokument mit der Java-API mit PDF/A kompatibel ist](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-determining-whether-a-document-is-pdf-a-compliant-using-the-java-api) (SOAP-Modus)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Ermitteln Sie mithilfe der Webdienst-API, ob ein Dokument PDF/A-kompatibel ist. {#determine-whether-a-document-is-pdf-a-compliant-using-the-web-service-api}

Stellen Sie mithilfe der Assembler-Dienst-API (Webdienst) fest, ob ein PDF-Dokument PDF/A-kompatibel ist:

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie eine `AssemblerServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie eine `AssemblerServiceClient.Endpoint.Address` -Objekt mithilfe der `System.ServiceModel.EndpointAddress` -Konstruktor. Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/AssemblerService?blob=mtom`). Sie müssen die `lc_version` -Attribut. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie eine `System.ServiceModel.BasicHttpBinding` -Objekt durch Abrufen des Werts der `AssemblerServiceClient.Endpoint.Binding` -Feld. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den Benutzernamen AEM Formulare zu `AssemblerServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `AssemblerServiceClient.ClientCredentials.UserName.Password`.
      * Konstantenwert zuweisen `HttpClientCredentialType.Basic` zum Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Konstantenwert zuweisen `BasicHttpSecurityMode.TransportCredentialOnly` zum Feld `BasicHttpBindingSecurity.Security.Mode`.

1. Referenzieren Sie ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Die `BLOB` -Objekt wird zum Speichern des DDX-Dokuments verwendet.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des DDX-Dokuments und den Modus zum Öffnen der Datei darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie die `BLOB` Objekt durch Zuweisen seiner `MTOM` -Feld mit dem Inhalt des Byte-Arrays.

1. Referenzieren Sie ein PDF-Dokument, das zur Bestimmung der PDF/A-Kompatibilität verwendet wird.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Die `BLOB` -Objekt wird zum Speichern des PDF-Eingabedokuments verwendet.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt durch Aufrufen des Konstruktors und Übergeben eines Zeichenfolgenwerts, der den Dateispeicherort des Eingabedokuments und den PDF-Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie die `BLOB` Objekt durch Zuweisen seiner `MTOM` -Eigenschaft mit dem Inhalt des Byte-Arrays.
   * Erstellen Sie eine `MyMapOf_xsd_string_To_xsd_anyType` -Objekt. Dieses Collection-Objekt wird zum Speichern des PDF-Dokuments verwendet.
   * Erstellen Sie eine `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objekt.
   * Weisen Sie dem `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objekt `key` -Feld. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen PDF-Quellelements übereinstimmen.
   * Zuweisen der `BLOB` -Objekt, das das PDF-Dokument im `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objekt `value` -Feld.
   * Fügen Sie die `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objekt `MyMapOf_xsd_string_To_xsd_anyType` -Objekt. Rufen Sie die `MyMapOf_xsd_string_To_xsd_anyType` object&#39; `Add` -Methode und übergeben Sie die `MyMapOf_xsd_string_To_xsd_anyType` -Objekt.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie eine `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen mithilfe seines Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie einem Datenelement einen Wert zuweisen, der zum `AssemblerOptionSpec` -Objekt. Um beispielsweise den Assembler-Dienst anzuweisen, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt, weisen Sie `false` der `AssemblerOptionSpec` -Objekt `failOnError` Datenelement.

1. Rufen Sie Informationen zum PDF-Dokument ab.

   Rufen Sie die `AssemblerServiceService` -Objekt `invoke` -Methode verwenden und die folgenden Werte übergeben:

   * A `BLOB` -Objekt, das das DDX-Dokument darstellt.
   * Die `MyMapOf_xsd_string_To_xsd_anyType` -Objekt, das das PDF-Eingabedokument enthält. Die Schlüssel müssen mit den Namen der PDF-Quelldateien übereinstimmen, und ihre Werte müssen die `BLOB` -Objekt, das der PDF-Eingabedatei entspricht.
   * Ein `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen angibt.

   Die `invoke` -Methode gibt eine `AssemblerResult` -Objekt, das XML-Daten enthält, die angeben, ob das PDF-Eingabedokument ein PDF/A-Dokument ist.

1. Speichern Sie das zurückgegebene XML-Dokument.

   So rufen Sie XML-Daten ab, die angeben, ob das Eingabedokument ein PDF/A-PDF-Dokument ist:

   * Zugriff auf `AssemblerResult` -Objekt `documents` -Feld, das ein `Map` -Objekt, das die XML-Daten enthält, die angeben, ob das PDF-Eingabedokument ein PDF/A-Dokument ist.
   * Iteration durch die `Map` -Objekt, um jedes Zieldokument abzurufen. Dann den Wert dieses Array-Mitglieds in eine `BLOB`.
   * Extrahieren Sie die Binärdaten, die die XML-Daten darstellen, indem Sie auf ihre `BLOB` -Objekt `MTOM` -Feld. Dieses Feld speichert ein Array von Bytes, in die Sie als XML-Datei schreiben können.

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
